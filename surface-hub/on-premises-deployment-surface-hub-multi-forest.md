---
title: 複数フォレスト環境でのオンプレミス展開 (Surface Hub)
description: このトピックでは、複数フォレスト環境のオンプレミス展開を使っている場合に Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。
keywords: 複数フォレスト展開, オンプレミス展開, デバイス アカウント, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 48fe874175a2c55b7e95ba0974cefe29f710c134
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836134"
---
# <span data-ttu-id="d77b9-104">複数フォレスト環境での Surface Hub のオンプレミス展開</span><span class="sxs-lookup"><span data-stu-id="d77b9-104">On-premises deployment for Surface Hub in a multi-forest environment</span></span>


<span data-ttu-id="d77b9-105">このトピックでは、複数フォレスト環境のオンプレミス展開を使っている場合に Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-105">This topic explains how you add a device account for your Microsoft Surface Hub when you have a multi-forest, on-premises deployment.</span></span>

<span data-ttu-id="d77b9-106">Microsoft Exchange 2013 以降と Skype for Business 2013 以降を搭載した複数フォレストのオンプレミス展開を使っている場合は、[提供されている PowerShell スクリプトを使用](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts)してデバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-106">If you have a multi-forest on-premises deployment with Microsoft Exchange 2013 or later and Skype for Business 2013 or later, then you can [use the provided PowerShell scripts](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) to create device accounts.</span></span> <span data-ttu-id="d77b9-107">単一フォレスト展開を使っている場合は、「[単一フォレスト環境での Surface Hub のオンプレミス展開](on-premises-deployment-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77b9-107">If you’re using a single-forest deployment, see [On-premises deployment for Surface Hub in a single-forest environment](on-premises-deployment-surface-hub-device-accounts.md).</span></span>

1.  <span data-ttu-id="d77b9-108">PC でリモート PowerShell セッションを開始し、Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-108">Start a remote PowerShell session from a PC and connect to Exchange.</span></span>

    <span data-ttu-id="d77b9-109">関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-109">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

    <span data-ttu-id="d77b9-110">ここで `$strExchangeServer` は Exchange サーバーの完全修飾ドメイン名 (FQDN) であり、`$strLyncFQDN` は Skype for Business サーバーの FQDN です。</span><span class="sxs-lookup"><span data-stu-id="d77b9-110">Note here that `$strExchangeServer` is the fully qualified domain name (FQDN) of your Exchange server, and `$strLyncFQDN` is the FQDN of your Skype for Business server.</span></span>

    ```PowerShell
    Set-ExecutionPolicy Unrestricted
    $org='contoso.microsoft.com'
    $cred=Get-Credential $admin@$org
    $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $cred -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
    $sessLync = New-PSSession -Credential $cred -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
    Import-PSSession $sessExchange
    Import-PSSession $sessLync
    ```

2.  <span data-ttu-id="d77b9-111">セッションの確立後、リソース フォレストに新しいメールボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-111">After establishing a session, create a new mailbox in the Resource Forest.</span></span> <span data-ttu-id="d77b9-112">これにより、アカウントを Surface Hub に対して認証できます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-112">This will allow the account to authenticate into the Surface Hub.</span></span>

    <span data-ttu-id="d77b9-113">既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-113">If you're changing an existing resource mailbox:</span></span>

    ```PowerShell
    New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01"
    ```

3.  <span data-ttu-id="d77b9-114">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-114">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

    <span data-ttu-id="d77b9-115">Surface Hub は、**PasswordEnabled** プロパティが **False** に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-115">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to **False**.</span></span> <span data-ttu-id="d77b9-116">このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。</span><span class="sxs-lookup"><span data-stu-id="d77b9-116">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

    <span data-ttu-id="d77b9-117">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-117">If you haven’t created a compatible policy yet, use the following cmdlet-—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="d77b9-118">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-118">Once it’s created, you can apply the same policy to other device accounts.</span></span>

    ```PowerShell
    $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
    ```

    <span data-ttu-id="d77b9-119">互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-119">Once you have a compatible policy, then you will need to apply the policy to the device account.</span></span> 

    ```PowerShell
    Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy -ActiveSyncEnabled $true
    Set-Mailbox $acctUpn -Type Room
    ```

4.  <span data-ttu-id="d77b9-120">ユーザーの会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-120">Various Exchange properties can be set on the device account to improve the meeting experience for people.</span></span> <span data-ttu-id="d77b9-121">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77b9-121">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ```PowerShell
    Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  <span data-ttu-id="d77b9-122">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-122">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="d77b9-123">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77b9-123">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span> <span data-ttu-id="d77b9-124">これは、ユーザー フォレストで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-124">This should be set in the User Forest.</span></span>

    ```PowerShell
    Set-AdUser $acctUpn -PasswordNeverExpires $true
    ```

6.  <span data-ttu-id="d77b9-125">Active Directory のアカウントが Surface Hub に認証されるように、アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d77b9-125">Enable the account in Active Directory so it will authenticate to the Surface Hub.</span></span> <span data-ttu-id="d77b9-126">これは、ユーザー フォレストで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-126">This should be set in the User Forest.</span></span>

    ```PowerShell
    Set-AdUser $acctUpn -Enabled $true
    ```

6. <span data-ttu-id="d77b9-127">ここで会議室メールボックスをリンクされたメールボックスに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-127">You now need to change the room mailbox to a linked mailbox:</span></span>

    ```PowerShell
    $cred=Get-Credential AuthForest\ADAdmin
    Set-mailbox -Alias LinkedRoomTest1 -LinkedMasterAccount AuthForest\LinkedRoomTest1 -LinkedDomainController AuthForest-4939.AuthForest.extest.contoso.com -Name LinkedRoomTest1 -LinkedCredential $cred -Identity LinkedRoomTest1
    ```

7.  <span data-ttu-id="d77b9-128">Skype for Business Server プールの Surface Hub AD アカウントを有効にして、デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="d77b9-128">Enable the device account with Skype for Business by enabling your Surface Hub AD account on a Skype for Business Server pool:</span></span>

    ```PowerShell
    Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
     -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
     -Identity HUB01
    ```

    <span data-ttu-id="d77b9-129">Surface Hub のセッション開始プロトコル (SIP) アドレスとドメイン コントローラーに加えて、専用の Skype for Business Server プール ID とユーザー ID を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-129">You'll need to use the Session Initiation Protocol (SIP) address and domain controller for the Surface Hub, along with your own Skype for Business Server pool identifier and user identity.</span></span>


## <span data-ttu-id="d77b9-130">匿名のメールと IM を無効にする</span><span class="sxs-lookup"><span data-stu-id="d77b9-130">Disable anonymous email and IM</span></span>



<span data-ttu-id="d77b9-131">Surface Hub は、デバイスアカウントを使用して、メールおよびコラボレーションサービス (IM、ビデオ、音声) を提供します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-131">Surface Hub uses a device account to provide email and collaboration services (IM, video, voice).</span></span> <span data-ttu-id="d77b9-132">このデバイスアカウントは、メール、IM、通話の発信時に、送信元の身元 ("差出人") として使用されます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-132">This device account is used as the originating identity (the “from” party) when sending email, IM, and placing calls.</span></span> <span data-ttu-id="d77b9-133">このアカウントは個人の識別可能なユーザーからのものではないため、Surface Hub のデバイスアカウントから送信されたため、"匿名" と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d77b9-133">As this account is not coming from an individual, identifiable user, it is deemed “anonymous” because it originated from the Surface Hub's device account.</span></span>  

<span data-ttu-id="d77b9-134">Id が**SurfaceHubPolicy**の各会議室デバイスに、ユーザーごとのクライアントポリシーが割り当てられているものとします。</span><span class="sxs-lookup"><span data-stu-id="d77b9-134">Assume you have a per-user client policy assigned to each meeting room device with an identity of **SurfaceHubPolicy**.</span></span> <span data-ttu-id="d77b9-135">匿名のメールとメッセージングを無効にするには、次のコマンドを使用して、このクライアントポリシーに clientPolicyEntry を追加します。</span><span class="sxs-lookup"><span data-stu-id="d77b9-135">To disable anonymous email and messaging, you add a clientPolicyEntry to this client policy by using the following commands.</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $false
$clientPolicy = Get-CsClientPolicy -Identity SurfaceHubPolicy
$clientPolicy.PolicyEntry.Add($policyEntry)
Set-CsClientPolicy -Instance $clientPolicy
```

<span data-ttu-id="d77b9-136">ポリシーが設定されていることを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d77b9-136">To verify that the policy has been set:</span></span>

```
Select-Object -InputObject $clientPolicy -Property PolicyEntry
```

<span data-ttu-id="d77b9-137">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d77b9-137">The output should be:</span></span>

```
PolicyEntry
-----------
{Name=AllowResourceAccountSendMessage;Value=False}
```
    
    
<span data-ttu-id="d77b9-138">ポリシーエントリを変更するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d77b9-138">To change the policy entry:</span></span>

```
$policyEntry =  New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Replace = $policyEntry}
``` 
    
<span data-ttu-id="d77b9-139">ポリシーのエントリを削除するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d77b9-139">To remove the policy entry:</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Remove = $policyEntry}
```
 





