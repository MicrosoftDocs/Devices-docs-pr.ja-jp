---
title: 単一フォレスト環境でのオンプレミス展開 (Surface Hub)
description: このトピックでは、単一フォレスト環境のオンプレミス展開を使っている場合に、Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。
ms.assetid: 80E12195-A65B-42D1-8B84-ECC3FCBAAFC6
ms.reviewer: ''
manager: laurawi
keywords: 単一フォレスト展開, オンプレミス展開, デバイス アカウント, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.localizationpriority: medium
ms.openlocfilehash: 37b157268769ddcdeaef67b7e19cc7260cd392b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836166"
---
# <span data-ttu-id="2234d-104">単一フォレスト環境での Surface Hub のオンプレミス展開</span><span class="sxs-lookup"><span data-stu-id="2234d-104">On-premises deployment for Surface Hub in a single-forest environment</span></span>


<span data-ttu-id="2234d-105">このトピックでは、単一フォレスト環境のオンプレミス展開を使っている場合に、Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2234d-105">This topic explains how you add a device account for your Microsoft Surface Hub when you have a single-forest, on-premises deployment.</span></span>

<span data-ttu-id="2234d-106">Microsoft Exchange 2013 以降と Skype for Business 2013 以降を搭載した単一フォレスト環境のオンプレミス展開を使っている場合は、[提供されている PowerShell スクリプトを使用](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts)してデバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2234d-106">If you have a single-forest on-premises deployment with Microsoft Exchange 2013 or later and Skype for Business 2013 or later, then you can [use the provided PowerShell scripts](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) to create device accounts.</span></span> <span data-ttu-id="2234d-107">複数フォレスト展開を使っている場合は、「[複数フォレスト環境での Surface Hub のオンプレミス展開](on-premises-deployment-surface-hub-multi-forest.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2234d-107">If you’re using a multi-forest deployment, see [On-premises deployment for Surface Hub in a multi-forest environment](on-premises-deployment-surface-hub-multi-forest.md).</span></span>

1. <span data-ttu-id="2234d-108">PC でリモート PowerShell セッションを開始し、Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="2234d-108">Start a remote PowerShell session from a PC and connect to Exchange.</span></span>

   <span data-ttu-id="2234d-109">関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2234d-109">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

   <span data-ttu-id="2234d-110">ここで `$strExchangeServer` は Exchange サーバーの完全修飾ドメイン名 (FQDN) であり、 `$strLyncFQDN` は Skype for Business サーバーの FQDN です。</span><span class="sxs-lookup"><span data-stu-id="2234d-110">Note here that `$strExchangeServer` is the fully qualified domain name (FQDN) of your Exchange server, and `$strLyncFQDN` is the FQDN of your Skype for Business server.</span></span>

   ```PowerShell
   Set-ExecutionPolicy Unrestricted
   $org='contoso.microsoft.com'
   $cred=Get-Credential $admin@$org
   $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $cred -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
   $sessLync = New-PSSession -Credential $cred -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
   Import-PSSession $sessExchange
   Import-PSSession $sessLync
   ```

2. <span data-ttu-id="2234d-111">セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="2234d-111">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="2234d-112">これにより、アカウントを Surface Hub に対して認証できます。</span><span class="sxs-lookup"><span data-stu-id="2234d-112">This will allow the account to authenticate into the Surface Hub.</span></span>

   <span data-ttu-id="2234d-113">既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="2234d-113">If you're changing an existing resource mailbox:</span></span>

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   <span data-ttu-id="2234d-114">新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="2234d-114">If you’re creating a new resource mailbox:</span></span>

   ```PowerShell
   New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
> [!IMPORTANT] 
> <span data-ttu-id="2234d-115">ActiveSync 仮想ディレクトリの基本認証は、Surface Hub で他の認証方法を使用して認証できないため、有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-115">ActiveSync Virtual Directory Basic Authentication is required to be enabled as the Surface Hub is unable to authenticate using other authentication methods.</span></span>

3. <span data-ttu-id="2234d-116">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-116">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="2234d-117">Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-117">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="2234d-118">このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。</span><span class="sxs-lookup"><span data-stu-id="2234d-118">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

   <span data-ttu-id="2234d-119">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2234d-119">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="2234d-120">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="2234d-120">Once it’s created, you can apply the same policy to other device accounts.</span></span>

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
   ```

   <span data-ttu-id="2234d-121">互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-121">Once you have a compatible policy, then you will need to apply the policy to the device account.</span></span> <span data-ttu-id="2234d-122">ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。</span><span class="sxs-lookup"><span data-stu-id="2234d-122">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="2234d-123">メールボックスを変換して種類をユーザーにし、ポリシーを適用して、変換でメールボックスに戻す必要があります。また、メールボックスを有効に戻してパスワードをもう一度設定することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2234d-123">You need to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox—you may need to re-enable it and set the password again too.</span></span>

   ```PowerShell
   $acctUpn = Get-Mailbox -Identity "<mailbox identity>"
   $credNewAccount.Password = ConvertTo-SecureString -String <room mailbox password> -AsPlainText -Force
   Set-Mailbox $acctUpn -Type Regular
   Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy
   Set-Mailbox $acctUpn -Type Room
   Set-Mailbox $acctUpn -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```

4. <span data-ttu-id="2234d-124">ユーザーの会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="2234d-124">Various Exchange properties can be set on the device account to improve the meeting experience for people.</span></span> <span data-ttu-id="2234d-125">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2234d-125">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

   ```PowerShell
   Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. <span data-ttu-id="2234d-126">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="2234d-126">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="2234d-127">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2234d-127">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

   ```PowerShell
   Set-AdUser $acctUpn -PasswordNeverExpires $true
   ```

6. <span data-ttu-id="2234d-128">Active Directory のアカウントが Surface Hub に認証されるように、アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2234d-128">Enable the account in Active Directory so it will authenticate to the Surface Hub.</span></span>

   ```PowerShell
   Set-AdUser $acctUpn -Enabled $true
   ```

7. <span data-ttu-id="2234d-129">Skype for Business Server プールの Surface Hub AD アカウントを有効にして、デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="2234d-129">Enable the device account with Skype for Business by enabling your Surface Hub AD account on a Skype for Business Server pool:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
    -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
    -Identity HUB01
   ```

   <span data-ttu-id="2234d-130">Surface Hub のセッション開始プロトコル (SIP) アドレスとドメイン コントローラーに加えて、専用の Skype for Business Server プール ID とユーザー ID を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-130">You'll need to use the Session Initiation Protocol (SIP) address and domain controller for the Surface Hub, along with your own Skype for Business Server pool identifier and user identity.</span></span>

8. <span data-ttu-id="2234d-131">省略可能: アカウントのエンタープライズ VoIP を有効にして、Surface Hub での公衆交換電話網 (PSTN) 電話の発信と着信を許可することもできます。</span><span class="sxs-lookup"><span data-stu-id="2234d-131">OPTIONAL: You can also allow your Surface Hub to make and receive public switched telephone network (PSTN) phone calls by enabling Enterprise Voice for your account.</span></span> <span data-ttu-id="2234d-132">エンタープライズ VoIP は Surface Hub の要件ではありませんが、Surface Hub クライアントで PSTN ダイヤル機能を使用する場合、実現方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2234d-132">Enterprise Voice isn't a requirement for Surface Hub, but if you want PSTN dialing functionality for the Surface Hub client, here's how to enable it:</span></span>

   ```PowerShell
   Set-CsMeetingRoom  -Identity HUB01 -DomainController DC-ND-001.contoso.com -LineURI "tel:+14255550555;ext=50555"  -EnterpriseVoiceEnabled $true
   ```

   <span data-ttu-id="2234d-133">この場合も、提供されているドメインコントローラーと電話番号の例を独自の情報で置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="2234d-133">Again, you need to replace the provided domain controller and phone number examples with your own information.</span></span> <span data-ttu-id="2234d-134">パラメーターの値 `$true` は変更されません。</span><span class="sxs-lookup"><span data-stu-id="2234d-134">The parameter value `$true` stays the same.</span></span>
    

 ## <span data-ttu-id="2234d-135">匿名のメールと IM を無効にする</span><span class="sxs-lookup"><span data-stu-id="2234d-135">Disable anonymous email and IM</span></span>




<span data-ttu-id="2234d-136">Surface Hub は、デバイスアカウントを使用して、メールおよびコラボレーションサービス (IM、ビデオ、音声) を提供します。</span><span class="sxs-lookup"><span data-stu-id="2234d-136">Surface Hub uses a device account to provide email and collaboration services (IM, video, voice).</span></span> <span data-ttu-id="2234d-137">このデバイスアカウントは、メール、IM、通話の発信時に、送信元の身元 ("差出人") として使用されます。</span><span class="sxs-lookup"><span data-stu-id="2234d-137">This device account is used as the originating identity (the “from” party) when sending email, IM, and placing calls.</span></span> <span data-ttu-id="2234d-138">このアカウントは個人の識別可能なユーザーからのものではないため、Surface Hub のデバイスアカウントから送信されたため、"匿名" と見なされます。</span><span class="sxs-lookup"><span data-stu-id="2234d-138">As this account is not coming from an individual, identifiable user, it is deemed “anonymous” because it originated from the Surface Hub's device account.</span></span>  

<span data-ttu-id="2234d-139">Id が**SurfaceHubPolicy**の各会議室デバイスに、ユーザーごとのクライアントポリシーが割り当てられているものとします。</span><span class="sxs-lookup"><span data-stu-id="2234d-139">Assume you have a per-user client policy assigned to each meeting room device with an identity of **SurfaceHubPolicy**.</span></span> <span data-ttu-id="2234d-140">匿名のメールとメッセージングを無効にするには、次のコマンドを使用して、このクライアントポリシーに clientPolicyEntry を追加します。</span><span class="sxs-lookup"><span data-stu-id="2234d-140">To disable anonymous email and messaging, you add a clientPolicyEntry to this client policy by using the following commands.</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $false
$clientPolicy = Get-CsClientPolicy -Identity SurfaceHubPolicy
$clientPolicy.PolicyEntry.Add($policyEntry)
Set-CsClientPolicy -Instance $clientPolicy
```

<span data-ttu-id="2234d-141">ポリシーが設定されていることを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2234d-141">To verify that the policy has been set:</span></span>

```
Select-Object -InputObject $clientPolicy -Property PolicyEntry
```

<span data-ttu-id="2234d-142">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2234d-142">The output should be:</span></span>

```
PolicyEntry
-----------
{Name=AllowResourceAccountSendMessage;Value=False}
```
    
    
<span data-ttu-id="2234d-143">ポリシーエントリを変更するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2234d-143">To change the policy entry:</span></span>

```
$policyEntry =  New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Replace = $policyEntry}
``` 
    
<span data-ttu-id="2234d-144">ポリシーのエントリを削除するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2234d-144">To remove the policy entry:</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Remove = $policyEntry}
```

 





