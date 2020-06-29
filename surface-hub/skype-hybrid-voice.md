---
title: Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開 (Surface Hub)
description: このトピックでは、クラウド コネクタ エディションまたは Skype for Business 2015 のプールを使ったオンプレミス PSTN 接続によって、Skype for Business のクラウド PBX を有効にする方法について説明します。
keywords: ハイブリッド展開, Skype Hybrid Voice
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 08349a7d2decb4d4b053cb03fc95808b49d4f2f0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836430"
---
# <span data-ttu-id="dd7ef-104">Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="dd7ef-104">Online or hybrid deployment using Skype Hybrid Voice environment  (Surface Hub)</span></span>

<span data-ttu-id="dd7ef-105">このトピックでは、クラウド コネクタ エディションまたは Skype for Business 2015 のプールを使ったオンプレミスの公衆交換電話網 (PSTN) 接続によって、Skype for Business のクラウド PBX を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-105">This topic explains how to enable Skype for Business Cloud PBX with on-premises Public Switched Telephone Network (PSTN) connectivity via Cloud Connector Edition or Skype for Business 2015 pool.</span></span> <span data-ttu-id="dd7ef-106">このオプションでは、</span><span class="sxs-lookup"><span data-stu-id="dd7ef-106">In this option.</span></span> <span data-ttu-id="dd7ef-107">クラウド上に Skype for Business のホーム プールと Exchange サーバーがあり、それらが Skype for Business 2015 またはクラウド コネクタ エディションを実行するオンプレミス プールを使って PSTN で接続されています。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-107">your Skype for Business home pools and Exchange servers are in the cloud, and are connected by PSTN via an on-premises pool running Skype for Business 2015 or Cloud Connector edition.</span></span> <span data-ttu-id="dd7ef-108">詳しくは、[さまざまなクラウド PBX オプション](https://technet.microsoft.com/library/mt612869.aspx)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-108">[Learn more about different Cloud PBX options](https://technet.microsoft.com/library/mt612869.aspx).</span></span>  

<span data-ttu-id="dd7ef-109">Skype for Business のクラウド PBX をいずれかのハイブリッド音声オプションで展開している場合は、次の手順に従って、Surface Hub のルーム アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-109">If you deployed Skype for Business Cloud PBX with one of the hybrid voice options, follow the steps below to enable the room account for Surface Hub.</span></span> <span data-ttu-id="dd7ef-110">最初に通常のユーザー アカウントを作成し、すべてのハイブリッド音声オプションおよび電話番号を割り当ててから、アカウントをルーム アカウントに変換することが重要です。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-110">It is important to create a regular user account first, assign all hybrid voice options and phone numbers, and then convert the account to a room account.</span></span> <span data-ttu-id="dd7ef-111">この順序に従わない場合、ハイブリッド電話番号を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-111">If you do not follow this order, you will not be able to assign a hybrid phone number.</span></span>  

>[!WARNING]
><span data-ttu-id="dd7ef-112">Hybrid Voice の構成前にアカウントを作成した場合 (Enable-CSMeetingRoom コマンドを実行)、必要なハイブリッド音声パラメーターを構成できません。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-112">If you create an account before configuration of Hybrid voice (you run Enable-CSMeetingRoom command), you will not be able to configure required hybrid voice parameters.</span></span> <span data-ttu-id="dd7ef-113">以前に構成されたアカウントのハイブリッド音声パラメーターを構成するか、または電話番号を再構成するには、E5 または E3 + クラウド PBX アドオン ライセンスを削除し、次の手順に従います (手順 3 から)。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-113">In order to configure hybrid voice parameters for a previously configured account or to reconfigure a phone number, delete the E5 or E3  + Cloud PBX add-on license, and then follow the steps below, starting at step 3.</span></span>

1. <span data-ttu-id="dd7ef-114">Surface Hub の新しいユーザー アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-114">Create a new user account for Surface Hub.</span></span> <span data-ttu-id="dd7ef-115">この例で <strong> は </strong> 、surfacehub2@adatum.com を使います。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-115">This example uses <strong>surfacehub2@adatum.com</strong>.</span></span> <span data-ttu-id="dd7ef-116">アカウントはローカル Active Directory で作成し、クラウドに同期するか、クラウドで直接作成することができます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-116">The account can be created in local Active Directory and synchronized to the cloud, or created directly in the cloud.</span></span> 

    ![新しいオブジェクト - ユーザー](images/new-user-hybrid-voice.png)

2. <span data-ttu-id="dd7ef-118">**[パスワードを無期限にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-118">Select **Password Never Expires**.</span></span> <span data-ttu-id="dd7ef-119">これは、Surface Hub デバイスにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-119">This is important for a Surface Hub device.</span></span>

   ![パスワードを無期限にする](images/new-user-password-hybrid-voice.png)

3. <span data-ttu-id="dd7ef-121">Office 365 では、**E5** ライセンスまたは **E3 および Cloud PBX** アドオンを、ルーム用に作成したユーザー アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-121">In Office 365, add **E5** license or **E3 and Cloud PBX** add-on to the user account created for the room.</span></span> <span data-ttu-id="dd7ef-122">これは、Hybrid Voice が機能するために必要です。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-122">This is required for Hybrid Voice to work.</span></span>

   ![製品ライセンスの追加](images/product-license-hybrid-voice.png)

4. <span data-ttu-id="dd7ef-124">ルームのユーザー アカウントが Skype for Business Online に表示されるまで、約 15 分間待ちます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-124">Wait approximately 15 minutes until the user account for the room appears in Skype for Business Online.</span></span>

5. <span data-ttu-id="dd7ef-125">Skype for Business Online でルームのユーザー アカウントが作成されたら、次のコマンドレットを実行して、Skype for Business のリモート PowerShell での Hybrid Voice に対してアカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-125">After the user account for room is created in Skype for Business Online, enable it for Hybrid Voice in Skype for Business Remote PowerShell by running the following cmdlet:</span></span>

   ```
   Set-csuser surfacehub2@adatum.com EnterpriseVoiceEnabled $true -HostedVoiceMail $true -onpremlineuri tel:+15005000102
   ```
    
6. <span data-ttu-id="dd7ef-126">Surface Hub からテスト通話を行って、Hybrid Voice の呼び出しフローを検証します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-126">Validate Hybrid Voice call flow by placing test calls from the Surface Hub.</span></span>

7. <span data-ttu-id="dd7ef-127">PC でリモート PowerShell セッションを開始し、次のコマンドレットを実行して Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-127">Start a remote PowerShell session on a PC and connect to Exchange by running the following cmdlets.</span></span>

   ```
   Set-ExecutionPolicy Unrestricted
   $cred=Get-Credential -Message "Please use your Office 365 admin credentials"
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/ps1-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```
    
8. <span data-ttu-id="dd7ef-128">セッションを確立した後、次のコマンドレットを実行してルームのユーザー アカウントを変更し、**RoomMailboxAccount** として有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-128">After establishing a session, modify the user account for the room to enable it as a **RoomMailboxAccount** by running the following cmdlets.</span></span> <span data-ttu-id="dd7ef-129">これにより、アカウントが Surface Hub で認証できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-129">This allows the account to authenticate with Surface Hub.</span></span>

   ```
   Set-Mailbox surfacehub2@adatum.com -Type Room
   Set-Mailbox surfacehub2@adatum.com -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
    
9. <span data-ttu-id="dd7ef-130">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-130">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="dd7ef-131">Surface Hub は、**PasswordEnabled** プロパティが **False** に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-131">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to **False**.</span></span> <span data-ttu-id="dd7ef-132">このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-132">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>
    
   <span data-ttu-id="dd7ef-133">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します (このコマンドレットは、"Surface Hubs" というポリシーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-133">If you haven’t created a compatible policy yet, use the following cmdlet (this one creates a policy called "Surface Hubs").</span></span> <span data-ttu-id="dd7ef-134">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-134">After it’s created, you can apply the same policy to other device accounts.</span></span>

   ```
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false
   ```
    
   <span data-ttu-id="dd7ef-135">互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-135">After you have a compatible policy, then you will need to apply the policy to the device account.</span></span> <span data-ttu-id="dd7ef-136">ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-136">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="dd7ef-137">次のコマンドレットを実行して、メールボックスを変換して種類をユーザーにし、ポリシーを適用してから、変換でメールボックスに戻す必要があります (アカウントを有効に戻し、パスワードをもう一度設定することが必要になる場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-137">Run the following cmdlets to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox (you may need to re-enable the account and set the password again).</span></span>
    
   ```
   Set-Mailbox surfacehub2@adatum.com -Type Regular
   Set-CASMailbox surfacehub2@adatum.com -ActiveSyncMailboxPolicy $easPolicy.id
   Set-Mailbox surfacehub2@adatum.com -Type Room
   $credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
   Set-Mailbox surfacehub2@adatum.com -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```
    
10. <span data-ttu-id="dd7ef-138">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-138">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="dd7ef-139">設定できるプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-139">You can see which properties can be set in [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md).</span></span> <span data-ttu-id="dd7ef-140">次のコマンドレットは、Exchange プロパティを設定する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-140">The following cmdlets provide an example of setting Exchange properties.</span></span>

    ```
    Set-CalendarProcessing surfacehub2@adatum.com -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing surfacehub2@adatum.com -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

11. <span data-ttu-id="dd7ef-141">Skype for Business Online で、メールボックスを会議デバイスとして有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-141">Enable the mailbox as a meeting device in Skype for Business Online.</span></span> <span data-ttu-id="dd7ef-142">アカウントを会議デバイスとして有効にする、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-142">Run the following cmdlet which enables the account as a meeting device.</span></span> 

    ```
    Get-CsTenant | select registrarpool
    Enable-CsMeetingRoom surfacehub2@adatum.com -RegistrarPool  'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
    ```
    
    <span data-ttu-id="dd7ef-143">このコマンドレットを実行すると、次の図に示すように、ユーザーは会議室にいるかどうかを尋ねられます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-143">As a result of running this cmdlet, users will be asked if they are in a meeting room, as shown in the following image.</span></span> <span data-ttu-id="dd7ef-144">**[はい]** を選択すると、マイクとスピーカーがミュートされます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-144">**Yes** will mute the microphone and speaker.</span></span>

    ![](images/adjust-room-audio.png)


    
<span data-ttu-id="dd7ef-145">この時点で、Hybrid Voice を含めてルーム アカウントが完全に構成されます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-145">At this moment the room account is fully configured, including Hybrid Voice.</span></span> <span data-ttu-id="dd7ef-146">Skype をオンプレミスで使用する場合は、説明や位置情報などの追加の属性をオンプレミスで構成できます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-146">If you use Skype on-premises, you can configure additional attributes, like description, location, etc., on-premises.</span></span> <span data-ttu-id="dd7ef-147">Skype Online でルームを作成する場合は、これらのパラメーターをオンラインで設定できます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-147">If you create a room in Skype Online, these parameters can be set online.</span></span> 

<span data-ttu-id="dd7ef-148">デバイスは、次の図のようにユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd7ef-148">In the following image, you can see how the device appears to users.</span></span>


![](images/select-room-hybrid-voice.png)
