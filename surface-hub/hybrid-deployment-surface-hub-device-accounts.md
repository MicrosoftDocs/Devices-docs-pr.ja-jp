---
title: ハイブリッド展開 (Surface Hub)
description: ハイブリッド展開では、Microsoft Surface Hub のデバイス アカウントを設定するには特別な手順が必要です。
ms.assetid: 7BFBB7BE-F587-422E-9CE4-C9DDF829E4F1
ms.reviewer: ''
manager: laurawi
keywords: ハイブリッド展開, Surface Hub のデバイス アカウント, 社内でホストされている Exchange, オンラインでホストされている Exchange
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/30/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7444c3f31f7a144200a0b8b89cfa509ef7a7afc4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836205"
---
# <span data-ttu-id="15828-104">ハイブリッド展開 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="15828-104">Hybrid deployment (Surface Hub)</span></span>

<span data-ttu-id="15828-105">ハイブリッド展開では、Microsoft Surface Hub のデバイス アカウントを設定するには特別な手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="15828-105">A hybrid deployment requires special processing to set up a device account for your Microsoft Surface Hub.</span></span> <span data-ttu-id="15828-106">組織に社内でホストされているサービスとオンラインでホストされているサービスが混在しているハイブリッド展開を使っている場合、各サービスがホストされている場所によって構成が異なります。</span><span class="sxs-lookup"><span data-stu-id="15828-106">If you’re using a hybrid deployment, in which your organization has a mix of services, with some hosted on-premises and some hosted online, then your configuration will depend on where each service is hosted.</span></span> <span data-ttu-id="15828-107">このトピックでは、[オンプレミスでホストされている Exchange](#exchange-on-premises)、[オンラインでホストされている Exchange](#exchange-online)、Skype for Business オンプレミス、Skype for Business Online、および Skype for Business ハイブリッドを対象としたハイブリッド展開について説明します。</span><span class="sxs-lookup"><span data-stu-id="15828-107">This topic covers hybrid deployments for [Exchange hosted on-premises](#exchange-on-premises), [Exchange hosted online](#exchange-online), Skype for Business on-premises, Skype for Business online, and Skype for Business hybrid.</span></span> <span data-ttu-id="15828-108">この種類の展開には非常に多くのバリエーションがあるため、すべてのバリエーションについて詳しい手順を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="15828-108">Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them.</span></span> <span data-ttu-id="15828-109">次の手順は、多くの構成に利用できます。</span><span class="sxs-lookup"><span data-stu-id="15828-109">The following process will work for many configurations.</span></span> <span data-ttu-id="15828-110">手順が実際のセットアップに適していない場合は、PowerShell の使用をお勧めします (「[付録: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)」をご覧ください)。PowerShell を使用して、ここでの説明と同じ結果を得ることや、他の展開オプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="15828-110">If the process isn't right for your setup, we recommend that you use PowerShell (see [Appendix: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)) to achieve the same end result as documented here, and for other deployment options.</span></span> <span data-ttu-id="15828-111">その後、提供されている PowerShell スクリプトを使って Surface Hub のセットアップを検証する必要があります </span><span class="sxs-lookup"><span data-stu-id="15828-111">You should then use the provided Powershell script to verify your Surface Hub setup.</span></span> <span data-ttu-id="15828-112">(「[アカウント検証スクリプト](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="15828-112">(See [Account Verification Script](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts).)</span></span>

> [!NOTE]
> <span data-ttu-id="15828-113">Exchange ハイブリッド環境では、 [exchange on-premises](#exchange-on-premises)の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="15828-113">In an Exchange hybrid environment, follow the steps for [Exchange on-premises](#exchange-on-premises).</span></span> <span data-ttu-id="15828-114">Exchange オブジェクトを Office 365 に移動するには、 [MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps)コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="15828-114">To move Exchange objects to Office 365, use the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps) cmdlet.</span></span>

## <span data-ttu-id="15828-115">Exchange On-Premises</span><span class="sxs-lookup"><span data-stu-id="15828-115">Exchange on-premises</span></span>

<span data-ttu-id="15828-116">Exchange On-Premises を使用している場合は、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="15828-116">Use this procedure if you use Exchange on-premises.</span></span>

1. <span data-ttu-id="15828-117">この手順では、AD 管理ツールを使ってオンプレミス ドメイン アカウントのメール アドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="15828-117">For this procedure, you'll be using AD admin tools to add an email address for your on-premises domain account.</span></span> <span data-ttu-id="15828-118">このアカウントは、Office 365 と同期されます。</span><span class="sxs-lookup"><span data-stu-id="15828-118">This account will be synced to Office 365.</span></span>

- <span data-ttu-id="15828-119">**Active Directory ユーザーとコンピューター** AD ツールで、Surface Hub アカウントの作成先となるフォルダーまたは組織単位を右クリックし、**[新規作成]**、**[ユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-119">In **Active Directory Users and Computers** AD tool, right-click on the folder or Organizational Unit that your Surface Hub accounts will be created in, click **New**, and **User**.</span></span>
- <span data-ttu-id="15828-120">前のコマンドレットの表示名を **[フル ネーム]** ボックスに入力し、エイリアスを **[ユーザー ログオン名]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="15828-120">Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box.</span></span> <span data-ttu-id="15828-121">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-121">Click **Next**.</span></span><p>

![Active Directory で新しいユーザーを作成するための [新しいオブジェクト] ダイアログ ボックス。](images/hybriddeployment-01a.png)

- <span data-ttu-id="15828-123">このアカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15828-123">Type the password for this account.</span></span> <span data-ttu-id="15828-124">確認用に再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-124">You'll need to retype it for verification.</span></span> <span data-ttu-id="15828-125">必ず、**[パスワードを無期限にする]** チェック ボックスだけをオンにします。</span><span class="sxs-lookup"><span data-stu-id="15828-125">Make sure the **Password never expires** checkbox is the only option selected.</span></span>

> <span data-ttu-id="15828-126">**重要** **[パスワードを無期限にする]** をオンにすることは、Surface Hub で Skype for Business を使用するための要件です。</span><span class="sxs-lookup"><span data-stu-id="15828-126">**Important** Selecting **Password never expires** is a requirement for Skype for Business on the Surface Hub.</span></span> <span data-ttu-id="15828-127">ドメイン ルールによっては、無期限のパスワードが禁止されています。</span><span class="sxs-lookup"><span data-stu-id="15828-127">Your domain rules may prohibit passwords that don't expire.</span></span> <span data-ttu-id="15828-128">その場合は、Surface Hub デバイス アカウントごとに例外を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-128">If so, you'll need to create an exception for each Surface Hub device account.</span></span>

![パスワードのダイアログ ボックスを示す画像。](images/hybriddeployment-02a.png)

-   <span data-ttu-id="15828-130">**[完了]** をクリックしてアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-130">Click **Finish** to create the account.</span></span>

![新しいユーザーのアカウント名、ログオン名、およびパスワード オプションが表示された画像。](images/hybriddeployment-03a.png)

2. <span data-ttu-id="15828-132">リモート メールボックスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="15828-132">Enable the remote mailbox.</span></span>

<span data-ttu-id="15828-133">オンプレミスの Exchange 管理シェルを管理者のアクセス許可で開き、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-133">Open your on-premises Exchange Management Shell with administrator permissions, and run this cmdlet.</span></span>

```PowerShell
Enable-RemoteMailbox 'HUB01@contoso.com' -RemoteRoutingAddress 'HUB01@contoso.com' -Room
```

> [!NOTE]
> <span data-ttu-id="15828-134">このコマンドレットを実行するオンプレミスの Exchange 環境がない場合は、アカウントの Active Directory オブジェクトに直接同じ変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="15828-134">If you don't have an on-premises Exchange environment to run this cmdlet, you can make the same changes directly to the Active Directory object for the account.</span></span>
>
> <span data-ttu-id="15828-135">msExchRemoteRecipientType = 33</span><span class="sxs-lookup"><span data-stu-id="15828-135">msExchRemoteRecipientType = 33</span></span>
>
> <span data-ttu-id="15828-136">msExchRecipientDisplayType = -2147481850</span><span class="sxs-lookup"><span data-stu-id="15828-136">msExchRecipientDisplayType = -2147481850</span></span>
>
> <span data-ttu-id="15828-137">msExchRecipientTypeDetails = 8589934592</span><span class="sxs-lookup"><span data-stu-id="15828-137">msExchRecipientTypeDetails = 8589934592</span></span>

3. <span data-ttu-id="15828-138">アカウントを作成したら、ディレクトリ同期を実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-138">After you've created the account, run a directory synchronization.</span></span> <span data-ttu-id="15828-139">完了したら、Microsoft 365 管理センターの [ユーザー] ページに移動し、前の手順で作成したアカウントがオンラインに統合されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15828-139">When it's complete, go to the users page in your Microsoft 365 admin center and verify that the account created in the previous steps has merged to online.</span></span>

4. <span data-ttu-id="15828-140">Microsoft Exchange Online に接続し、Office 365 のアカウントのプロパティをいくつか設定します。</span><span class="sxs-lookup"><span data-stu-id="15828-140">Connect to Microsoft Exchange Online and set some properties for the account in Office 365.</span></span>

<span data-ttu-id="15828-141">PC でリモート PowerShell セッションを開始し、Microsoft Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="15828-141">Start a remote PowerShell session on a PC and connect to Microsoft Exchange.</span></span> <span data-ttu-id="15828-142">関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15828-142">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

<span data-ttu-id="15828-143">以降の手順は、Office 365 テナントで実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-143">The next steps will be run on your Office 365 tenant.</span></span>

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri 'https://ps.outlook.com/powershell' -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

5. <span data-ttu-id="15828-144">新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使います。</span><span class="sxs-lookup"><span data-stu-id="15828-144">Create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

<span data-ttu-id="15828-145">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-145">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy or use a compatible existing policy.</span></span>

<span data-ttu-id="15828-146">Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="15828-146">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="15828-147">このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。</span><span class="sxs-lookup"><span data-stu-id="15828-147">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

<span data-ttu-id="15828-148">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-148">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="15828-149">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="15828-149">Once it’s created, you can apply the same policy to other device accounts.</span></span>

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

<span data-ttu-id="15828-150">互換性のあるポリシーを取得したら、デバイスアカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-150">Once you have a compatible policy, you will need to apply the policy to the device account.</span></span> 

```PowerShell
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
```

6. <span data-ttu-id="15828-151">Exchange プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="15828-151">Set Exchange properties.</span></span>

<span data-ttu-id="15828-152">会議エクスペリエンスを向上させるには、Exchange プロパティをデバイス アカウントに設定します。</span><span class="sxs-lookup"><span data-stu-id="15828-152">Setting Exchange properties on the device account to improve the meeting experience.</span></span> <span data-ttu-id="15828-153">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="15828-153">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse 'This is a Surface Hub room!'
```

7. <span data-ttu-id="15828-154">Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="15828-154">Connect to Azure AD.</span></span>

<span data-ttu-id="15828-155">PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-155">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="15828-156">管理者特権の PowerShell プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-156">In an elevated PowerShell prompt, run the following command:</span></span>

```PowerShell
Install-Module -Name AzureAD
```

<span data-ttu-id="15828-157">一部のアカウント設定を適用するには、Azure AD に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-157">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="15828-158">次のコマンドレットを実行すると接続できます。</span><span class="sxs-lookup"><span data-stu-id="15828-158">You can run this cmdlet to connect.</span></span>

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. <span data-ttu-id="15828-159">Office 365 のライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-159">Assign an Office 365 license.</span></span>

<span data-ttu-id="15828-160">デバイス アカウントには、有効な Office 365 (O365) のライセンスが必要です。ライセンスがない場合、Exchange と Skype for Business を利用できません。</span><span class="sxs-lookup"><span data-stu-id="15828-160">The device account needs to have a valid Office 365 (O365) license, or Exchange and Skype for Business will not work.</span></span> <span data-ttu-id="15828-161">ライセンスがある場合は、利用場所をデバイス アカウントに割り当てる必要があります。これにより、アカウントで利用可能なライセンス SKU が決まります。</span><span class="sxs-lookup"><span data-stu-id="15828-161">If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account.</span></span>

<span data-ttu-id="15828-162">`Get-AzureADSubscribedSku` を使って、O365 テナントで利用可能な SKU の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="15828-162">You can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

<span data-ttu-id="15828-163">SKU の一覧を取得したら、`$License.SkuId` 変数に必要な SkuId を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-163">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

<span data-ttu-id="15828-164">次に、[Skype for Business Online](#skype-for-business-online)、[Skype for Business オンプレミス](#skype-for-business-on-premises)、または [Skype for Business ハイブリッド](#skype-for-business-hybrid)でデバイス アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="15828-164">Next, you enable the device account with [Skype for Business Online](#skype-for-business-online), [Skype for Business on-premises](#skype-for-business-on-premises), or [Skype for Business hybrid](#skype-for-business-hybrid).</span></span>

### <span data-ttu-id="15828-165">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="15828-165">Skype for Business Online</span></span>

<span data-ttu-id="15828-166">Skype for Business Online を有効にするには、テナント ユーザーが Exchange メールボックスを持っている必要があります (テナント内に 1 つ以上の Exchange メールボックスが必要です)。</span><span class="sxs-lookup"><span data-stu-id="15828-166">To enable Skype for Business online, your tenant users must have Exchange mailboxes (at least one Exchange mailbox in the tenant is required).</span></span> <span data-ttu-id="15828-167">次の表では、必要なプランや追加のサービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="15828-167">The following table explains which plans or additional services you need.</span></span>

| <span data-ttu-id="15828-168">Skype ルーム システムのシナリオ</span><span class="sxs-lookup"><span data-stu-id="15828-168">Skype room system scenario</span></span> | <span data-ttu-id="15828-169">Office 365 Premium、Microsoft 365 アプリ (enterprise 向け)、または Skype for Business Standalone Plan 2 を使用している場合は、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="15828-169">If you have Office 365 Premium, Microsoft 365 Apps for enterprise, or Skype for Business Standalone Plan 2, you need:</span></span> | <span data-ttu-id="15828-170">エンタープライズ ベースのプランを利用している場合に必要なもの:</span><span class="sxs-lookup"><span data-stu-id="15828-170">If you have an Enterprise-based plan, you need:</span></span> | <span data-ttu-id="15828-171">Skype for Business Server 2015 (オンプレミスまたはハイブリッド) を使用している場合は、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="15828-171">If you have Skype for Business Server 2015 (on-premises or hybrid), you need:</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="15828-172">スケジュールされた会議に参加する</span><span class="sxs-lookup"><span data-stu-id="15828-172">Join a scheduled meeting</span></span> | <span data-ttu-id="15828-173">Skype for Business スタンドアロン プラン 1</span><span class="sxs-lookup"><span data-stu-id="15828-173">Skype for Business Standalone Plan 1</span></span> | <span data-ttu-id="15828-174">E1、3、4、または 5</span><span class="sxs-lookup"><span data-stu-id="15828-174">E1, 3, 4, or 5</span></span> | <span data-ttu-id="15828-175">Skype for Business Server Standard の CAL</span><span class="sxs-lookup"><span data-stu-id="15828-175">Skype for Business Server Standard CAL</span></span> |
| <span data-ttu-id="15828-176">臨時の会議を開始する</span><span class="sxs-lookup"><span data-stu-id="15828-176">Initiate an ad-hoc meeting</span></span> | <span data-ttu-id="15828-177">Skype for Business スタンドアロン プラン 2</span><span class="sxs-lookup"><span data-stu-id="15828-177">Skype for Business Standalone Plan 2</span></span> | <span data-ttu-id="15828-178">E 1、3、4、または 5</span><span class="sxs-lookup"><span data-stu-id="15828-178">E 1, 3, 4, or 5</span></span> | <span data-ttu-id="15828-179">Skype for Business Server Standard の CAL または Enterprise の CAL</span><span class="sxs-lookup"><span data-stu-id="15828-179">Skype for Business Server Standard CAL or Enterprise CAL</span></span> |
| <span data-ttu-id="15828-180">アドホック会議を開始し、会議から電話番号にダイヤルアウトする</span><span class="sxs-lookup"><span data-stu-id="15828-180">Initiate an ad-hoc meeting and dial out from a meeting to phone numbers</span></span> | <span data-ttu-id="15828-181">Skype for Business Standalone Plan 2 (電話会議あり)</span><span class="sxs-lookup"><span data-stu-id="15828-181">Skype for Business Standalone Plan 2 with Audio Conferencing</span></span></br></br><span data-ttu-id="15828-182">**注** PSTN 従量課金はオプションです</span><span class="sxs-lookup"><span data-stu-id="15828-182">**Note** PSTN consumption billing is optional</span></span> | <span data-ttu-id="15828-183">電話会議または E5 付きの E1 または E3</span><span class="sxs-lookup"><span data-stu-id="15828-183">E1 or E3 with Audio Conferencing, or E5</span></span>| <span data-ttu-id="15828-184">Skype for Business Server Standard の CAL または Enterprise の CAL</span><span class="sxs-lookup"><span data-stu-id="15828-184">Skype for Business Server Standard CAL or Enterprise CAL</span></span> |
| <span data-ttu-id="15828-185">ルームに電話番号を提供して、ルームから電話をかけるまたは受ける、電話番号を使用してダイヤルイン会議に参加する</span><span class="sxs-lookup"><span data-stu-id="15828-185">Give the room a phone number and make or receive calls from the room or join a dial-in conference using a phone number</span></span> | <span data-ttu-id="15828-186">Skype for Business Standalone Plan 2 (電話システムと PSTN 音声通話プラン)</span><span class="sxs-lookup"><span data-stu-id="15828-186">Skype for Business Standalone Plan 2 with Phone System and a PSTN Voice Calling plan</span></span> | <span data-ttu-id="15828-187">電話システムと PSTN 音声通話プラン (E5) を使用した E1 または E3</span><span class="sxs-lookup"><span data-stu-id="15828-187">E1 or E3 with Phone System and a PSTN Voice Calling plan, or E5</span></span> | <span data-ttu-id="15828-188">Skype for Business Server Standard の CAL または Plus の CAL</span><span class="sxs-lookup"><span data-stu-id="15828-188">Skype for Business Server Standard CAL or Plus CAL</span></span> |

<span data-ttu-id="15828-189">次の表に、Office 365 のプランと Skype for Business のオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="15828-189">The following table lists the Office 365 plans and Skype for Business options.</span></span>

| <span data-ttu-id="15828-190">Office 365 のプラン</span><span class="sxs-lookup"><span data-stu-id="15828-190">O365 Plan</span></span> | <span data-ttu-id="15828-191">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="15828-191">Skype for Business</span></span> | <span data-ttu-id="15828-192">電話システム</span><span class="sxs-lookup"><span data-stu-id="15828-192">Phone System</span></span> | <span data-ttu-id="15828-193">電話会議</span><span class="sxs-lookup"><span data-stu-id="15828-193">Audio Conferencing</span></span> | <span data-ttu-id="15828-194">通話プラン</span><span class="sxs-lookup"><span data-stu-id="15828-194">Calling Plans</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="15828-195">Office 365 Business Essentials</span><span class="sxs-lookup"><span data-stu-id="15828-195">O365 Business Essentials</span></span> | <span data-ttu-id="15828-196">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-196">Included</span></span> |  |  |  |
| <span data-ttu-id="15828-197">Office 365 Business Premium</span><span class="sxs-lookup"><span data-stu-id="15828-197">O365 Business Premium</span></span> | <span data-ttu-id="15828-198">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-198">Included</span></span> |  |  |  |
| <span data-ttu-id="15828-199">E1</span><span class="sxs-lookup"><span data-stu-id="15828-199">E1</span></span> | <span data-ttu-id="15828-200">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-200">Included</span></span> | <span data-ttu-id="15828-201">アドオン</span><span class="sxs-lookup"><span data-stu-id="15828-201">Add-on</span></span> | <span data-ttu-id="15828-202">アドオン</span><span class="sxs-lookup"><span data-stu-id="15828-202">Add-on</span></span> | <span data-ttu-id="15828-203">アドオン (電話システムアドオンが必要)</span><span class="sxs-lookup"><span data-stu-id="15828-203">Add-on (requires Phone System add-on)</span></span> |
| <span data-ttu-id="15828-204">E3</span><span class="sxs-lookup"><span data-stu-id="15828-204">E3</span></span> | <span data-ttu-id="15828-205">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-205">Included</span></span> | <span data-ttu-id="15828-206">アドオン</span><span class="sxs-lookup"><span data-stu-id="15828-206">Add-on</span></span> | <span data-ttu-id="15828-207">アドオン</span><span class="sxs-lookup"><span data-stu-id="15828-207">Add-on</span></span> | <span data-ttu-id="15828-208">アドオン (電話システムアドオンが必要)</span><span class="sxs-lookup"><span data-stu-id="15828-208">Add-on (requires Phone System add-on)</span></span> |
| <span data-ttu-id="15828-209">E5</span><span class="sxs-lookup"><span data-stu-id="15828-209">E5</span></span> | <span data-ttu-id="15828-210">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-210">Included</span></span> | <span data-ttu-id="15828-211">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-211">Included</span></span> | <span data-ttu-id="15828-212">含まれる</span><span class="sxs-lookup"><span data-stu-id="15828-212">Included</span></span> | <span data-ttu-id="15828-213">アドオン</span><span class="sxs-lookup"><span data-stu-id="15828-213">Add-on</span></span>  |

1. <span data-ttu-id="15828-214">まず PC で、Skype for Business Online 環境に対するリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-214">Start by creating a remote PowerShell session from a PC to the Skype for Business online environment.</span></span>

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. <span data-ttu-id="15828-215">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-215">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool 'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

<span data-ttu-id="15828-216">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="15828-216">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

```PowerShell
Get-CsOnlineUser -Identity ‘HUB01@contoso.com’| fl *registrarpool*
```

3. <span data-ttu-id="15828-217">Skype for Business のライセンスを Surface Hub アカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-217">Assign Skype for Business license to your Surface Hub account.</span></span>

 <span data-ttu-id="15828-218">ここまでの手順を完了して Skype for Business Online で Surface Hub アカウントを有効にしたら、Surface Hub にライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-218">Once you've completed the preceding steps to enable your Surface Hub account in Skype for Business Online, you need to assign a license to the Surface Hub.</span></span> <span data-ttu-id="15828-219">O365 管理ポータルを使用して、デバイスに Skype for Business Online (プラン 2) または Skype for Business Online (Plan 3) ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-219">Using the O365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.</span></span>

- <span data-ttu-id="15828-220">テナント管理者としてログインし、O365 管理ポータルを開いて、"管理者" アプリをクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-220">Login as a tenant administrator, open the O365 Administrative Portal, and click on the Admin app.</span></span>

- <span data-ttu-id="15828-221">**[ユーザーとグループ]**、**[ユーザーの追加、パスワードのリセットなど]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-221">Click on **Users and Groups** and then **Add users, reset passwords, and more**.</span></span>

- <span data-ttu-id="15828-222">Surface Hub アカウントをクリックし、次にペン アイコンをクリックして、アカウント情報を編集します。</span><span class="sxs-lookup"><span data-stu-id="15828-222">Click the Surface Hub account, and then click the pen icon to edit the account information.</span></span>

- <span data-ttu-id="15828-223">**[ライセンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-223">Click **Licenses**.</span></span>

- <span data-ttu-id="15828-224">[**ライセンスの割り当て**] で、ライセンスおよびエンタープライズボイスの要件に応じて、[Skype for Business (プラン 1)] または [Skype for Business (plan 2)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="15828-224">In **Assign licenses**, select Skype for Business (Plan 1) or Skype for Business (Plan 2), depending on your licensing and Enterprise Voice requirements.</span></span> <span data-ttu-id="15828-225">Surface Hub でエンタープライズボイスを使用する場合は、プラン2ライセンスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-225">You'll have to use a Plan 2 license if you want to use Enterprise Voice on your Surface Hub.</span></span>

- <span data-ttu-id="15828-226">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-226">Click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="15828-227">これらのライセンスのいずれかの割り当てに必要なコマンドレットを実行するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールも使用できますが、ここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="15828-227">You can also use the Windows Azure Active Directory Module for Windows Powershell to run the cmdlets needed to assign one of these licenses, but that's not covered here.</span></span>

<span data-ttu-id="15828-228">検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-228">For validation, you should be able to use any Skype for Business client (PC, Android, etc.) to sign in to this account.</span></span>

### <span data-ttu-id="15828-229">Skype for Business オンプレミス</span><span class="sxs-lookup"><span data-stu-id="15828-229">Skype for Business on-premises</span></span>

<span data-ttu-id="15828-230">コマンドレットを実行するには、いずれかの Skype フロントエンドに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-230">To run this cmdlet, you will need to connect to one of the Skype front-ends.</span></span> <span data-ttu-id="15828-231">Skype PowerShell を開き、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-231">Open the Skype PowerShell and run:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### <span data-ttu-id="15828-232">Skype for Business ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="15828-232">Skype for Business hybrid</span></span>

<span data-ttu-id="15828-233">組織で、[Skype for Business Server と Skype for Business Online 間のハイブリッド接続](https://technet.microsoft.com/library/jj205403.aspx)を設定している場合は、アカウントを作成するためのガイダンスは標準的な Surface Hub の展開とは異なります。</span><span class="sxs-lookup"><span data-stu-id="15828-233">If your organization has set up [hybrid connectivity between Skype for Business Server and Skype for Business Online](https://technet.microsoft.com/library/jj205403.aspx), the guidance for creating accounts differs from a standard Surface Hub deployment.</span></span>

<span data-ttu-id="15828-234">Surface Hub では種類が `meetingroom` の Skype アカウントが必要になりますが、一般ユーザーの場合は種類が user の Skype アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="15828-234">The Surface Hub requires a Skype account of the type `meetingroom`, while a normal user would use a user type account in Skype.</span></span> <span data-ttu-id="15828-235">Skype サーバーがハイブリッド用に設定されていて、ローカル Skype サーバーのユーザーと Office 365 でホストされているユーザーが存在する場合、Surface Hub アカウントを作成しようとするといくつかの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15828-235">If your Skype server is set up for hybrid where you might have users on the local Skype server as well as users hosted in Office 365, you might run into a few issues when trying to create a Surface Hub account.</span></span>

<span data-ttu-id="15828-236">Skype for Business Server 2015 ハイブリッド環境では、Skype for business Online で使用するすべてのユーザーは、まずオンプレミス展開で作成し、ユーザーアカウントが Active Directory ドメインサービスで作成されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-236">In Skype for Business Server 2015 hybrid environment, any user that you want in Skype for Business Online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services.</span></span> <span data-ttu-id="15828-237">その後、ユーザーを Skype for Business Online に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="15828-237">You can then move the user to Skype for Business Online.</span></span> <span data-ttu-id="15828-238">オンプレミスからオンラインへのユーザーアカウントの移動は、 [move-csuser](https://technet.microsoft.com/library/gg398528.aspx)コマンドレットによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="15828-238">The move of a user account from on-premises to online is done via the [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) cmdlet.</span></span> <span data-ttu-id="15828-239">Csroom Room オブジェクトを移動するには、 [move-Csroom room](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396)コマンドレットを使います。</span><span class="sxs-lookup"><span data-stu-id="15828-239">To move a Csmeetingroom object, use the [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="15828-240">6.0.9319.281 のムーブルームコマンドレットを使用するには、 [Skype For Business server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)または[Lync server 2013 の2017年7月の累積更新プログラム 5.0.8308.992](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)の2017年5月の累積更新プログラムをインストールしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-240">To use the Move-CsMeetingRoom cmdlet, you must have installed [the May 2017 cumulative update 6.0.9319.281 for Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) or [the July 2017 cumulative update 5.0.8308.992 for Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span></span>


## <span data-ttu-id="15828-241">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="15828-241">Exchange online</span></span>

<span data-ttu-id="15828-242">Exchange Online を使用している場合は、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="15828-242">Use this procedure if you use Exchange online.</span></span>

1. <span data-ttu-id="15828-243">Office 365 のメール アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-243">Create an email account in Office 365.</span></span>

<span data-ttu-id="15828-244">PC でリモート PowerShell セッションを開始し、Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="15828-244">Start a remote PowerShell session on a PC and connect to Exchange.</span></span> <span data-ttu-id="15828-245">関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15828-245">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/PowerShell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2. <span data-ttu-id="15828-246">メールボックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="15828-246">Set up a mailbox.</span></span>

<span data-ttu-id="15828-247">セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="15828-247">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="15828-248">これにより、アカウントを Surface Hub に対して認証できます。</span><span class="sxs-lookup"><span data-stu-id="15828-248">This will allow the account to authenticate into the Surface Hub.</span></span>

<span data-ttu-id="15828-249">既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-249">If you're changing an existing resource mailbox:</span></span>

```PowerShell
Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

<span data-ttu-id="15828-250">新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-250">If you’re creating a new resource mailbox:</span></span>

```PowerShell
New-Mailbox -MicrosoftOnlineServicesID 'HUB01@contoso.com' -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3. <span data-ttu-id="15828-251">Exchange ActiveSync ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-251">Create Exchange ActiveSync policy.</span></span>

<span data-ttu-id="15828-252">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-252">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

<span data-ttu-id="15828-253">Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="15828-253">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="15828-254">正しく設定されていない場合、Surface Hub 上の Exchange サービス (メール、予定表、会議への参加) は有効になりません。</span><span class="sxs-lookup"><span data-stu-id="15828-254">If this isn’t set properly, Exchange services on the Surface Hub (mail, calendar, and joining meetings) will not be enabled.</span></span>

<span data-ttu-id="15828-255">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-255">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="15828-256">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="15828-256">Once it’s created, you can apply the same policy to other device accounts.</span></span>

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

<span data-ttu-id="15828-257">互換性のあるポリシーを取得したら、デバイスアカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-257">Once you have a compatible policy, you will need to apply the policy to the device account.</span></span> <span data-ttu-id="15828-258">ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。</span><span class="sxs-lookup"><span data-stu-id="15828-258">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="15828-259">メールボックスを変換して種類をユーザーにし、ポリシーを適用して、変換でメールボックスに戻す必要があります。また、メールボックスを有効に戻してパスワードをもう一度設定することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="15828-259">You need to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox—you may need to re-enable it and set the password again too.</span></span>

```PowerShell
Set-Mailbox 'HUB01@contoso.com' -Type Regular
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
Set-Mailbox 'HUB01@contoso.com' -Type Room
$credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
Set-Mailbox 'HUB01@contoso.com' -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
```

4. <span data-ttu-id="15828-260">Exchange プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="15828-260">Set Exchange properties.</span></span>

<span data-ttu-id="15828-261">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-261">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="15828-262">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="15828-262">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
```

5. <span data-ttu-id="15828-263">オンプレミスのドメインアカウントのメールアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="15828-263">Add an email address for your on-premises domain account.</span></span>

<span data-ttu-id="15828-264">この手順では、AD 管理ツールを使ってオンプレミス ドメイン アカウントのメール アドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="15828-264">For this procedure, you'll be using AD admin tools to add an email address for your on-premises domain account.</span></span>

- <span data-ttu-id="15828-265">**Active Directory ユーザーとコンピューター** AD ツールで、Surface Hub アカウントの作成先となるフォルダーまたは組織単位を右クリックし、**[新規作成]**、**[ユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-265">In **Active Directory Users and Computers** AD tool, right-click on the folder or Organizational Unit that your Surface Hub accounts will be created in, click **New**, and **User**.</span></span>
- <span data-ttu-id="15828-266">前のコマンドレットの表示名を **[フル ネーム]** ボックスに入力し、エイリアスを **[ユーザー ログオン名]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="15828-266">Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box.</span></span> <span data-ttu-id="15828-267">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-267">Click **Next**.</span></span>

![Active Directory で新しいユーザーを作成するための [新しいオブジェクト] ダイアログ ボックス。](images/hybriddeployment-01a.png)

- <span data-ttu-id="15828-269">このアカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15828-269">Type the password for this account.</span></span> <span data-ttu-id="15828-270">確認用に再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-270">You'll need to retype it for verification.</span></span> <span data-ttu-id="15828-271">必ず、**[パスワードを無期限にする]** チェック ボックスだけをオンにします。</span><span class="sxs-lookup"><span data-stu-id="15828-271">Make sure the **Password never expires** checkbox is the only option selected.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15828-272">[**パスワードを無期限**にする] は、Surface Hub 上の Skype for business の要件です。</span><span class="sxs-lookup"><span data-stu-id="15828-272">Selecting **Password never expires** is a requirement for Skype for Business on the Surface Hub.</span></span> <span data-ttu-id="15828-273">ドメイン ルールによっては、無期限のパスワードが禁止されています。</span><span class="sxs-lookup"><span data-stu-id="15828-273">Your domain rules may prohibit passwords that don't expire.</span></span> <span data-ttu-id="15828-274">その場合は、Surface Hub デバイス アカウントごとに例外を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-274">If so, you'll need to create an exception for each Surface Hub device account.</span></span>

![パスワードのダイアログ ボックスを示す画像。](images/hybriddeployment-02a.png)

- <span data-ttu-id="15828-276">**[完了]** をクリックしてアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-276">Click **Finish** to create the account.</span></span>

![新しいユーザーのアカウント名、ログオン名、およびパスワード オプションが表示された画像。](images/hybriddeployment-03a.png)

6. <span data-ttu-id="15828-278">ディレクトリ同期を実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-278">Run directory synchronization.</span></span>

<span data-ttu-id="15828-279">アカウントを作成したら、ディレクトリ同期を実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-279">After you've created the account, run a directory synchronization.</span></span> <span data-ttu-id="15828-280">完了したら、ユーザー ページに移動して、前の手順で作成した 2 つのアカウントが結合していることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="15828-280">When it's complete, go to the users page and verify that the two accounts created in the previous steps have merged.</span></span>

7. <span data-ttu-id="15828-281">Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="15828-281">Connect to Azure AD.</span></span>

<span data-ttu-id="15828-282">PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-282">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="15828-283">管理者特権の PowerShell プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-283">In an elevated PowerShell prompt, run the following command:</span></span>

```PowerShell
Install-Module -Name AzureAD
```

<span data-ttu-id="15828-284">一部のアカウント設定を適用するには、Azure AD に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-284">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="15828-285">接続するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-285">You can run this cmdlet to connect:</span></span>

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. <span data-ttu-id="15828-286">Office 365 のライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-286">Assign an Office 365 license.</span></span>

<span data-ttu-id="15828-287">デバイス アカウントには、有効な Office 365 (O365) のライセンスが必要です。ライセンスがない場合、Exchange と Skype for Business を利用できません。</span><span class="sxs-lookup"><span data-stu-id="15828-287">The device account needs to have a valid Office 365 (O365) license, or Exchange and Skype for Business will not work.</span></span> <span data-ttu-id="15828-288">ライセンスがある場合は、利用場所をデバイス アカウントに割り当てる必要があります。これにより、アカウントで利用可能なライセンス SKU が決まります。</span><span class="sxs-lookup"><span data-stu-id="15828-288">If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account.</span></span>

<span data-ttu-id="15828-289">次に、`Get-AzureADSubscribedSku` を使って、O365 テナントで利用可能な SKU の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="15828-289">Next, you can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

<span data-ttu-id="15828-290">SKU の一覧を取得したら、`$License.SkuId` 変数に必要な SkuId を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-290">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

<span data-ttu-id="15828-291">次に、[Skype for Business Online](#skype-for-business-online)、[Skype for Business オンプレミス](#skype-for-business-on-premises)、または [Skype for Business ハイブリッド](#skype-for-business-hybrid)でデバイス アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="15828-291">Next, you enable the device account with [Skype for Business Online](#skype-for-business-online), [Skype for Business on-premises](#skype-for-business-on-premises), or [Skype for Business hybrid](#skype-for-business-hybrid).</span></span>

### <span data-ttu-id="15828-292">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="15828-292">Skype for Business Online</span></span>

<span data-ttu-id="15828-293">Skype for Business を有効にするには、環境が [Skype for Business Online の前提条件](#skype-for-business-online)を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-293">In order to enable Skype for Business, your environment will need to meet the [prerequisites for Skype for Business online](#skype-for-business-online).</span></span>

1. <span data-ttu-id="15828-294">まず PC で、Skype for Business Online 環境に対するリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="15828-294">Start by creating a remote PowerShell session to the Skype for Business online environment from a PC.</span></span>

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. <span data-ttu-id="15828-295">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-295">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool  
'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

   <span data-ttu-id="15828-296">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="15828-296">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

```PowerShell
Get-CsOnlineUser -Identity 'HUB01@contoso.com'| fl *registrarpool*
```

10. <span data-ttu-id="15828-297">Skype for Business のライセンスを Surface Hub アカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-297">Assign Skype for Business license to your Surface Hub account</span></span>

<span data-ttu-id="15828-298">ここまでの手順を完了して Skype for Business Online で Surface Hub アカウントを有効にしたら、Surface Hub にライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-298">Once you've completed the preceding steps to enable your Surface Hub account in Skype for Business Online, you need to assign a license to the Surface Hub.</span></span> <span data-ttu-id="15828-299">O365 管理ポータルを使用して、デバイスに Skype for Business Online (プラン 2) または Skype for Business Online (Plan 3) ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15828-299">Using the O365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.</span></span>

- <span data-ttu-id="15828-300">テナント管理者としてサインインし、O365 管理ポータルを開いて、"管理者" アプリをクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-300">Sign in as a tenant administrator, open the O365 Administrative Portal, and click on the Admin app.</span></span>

- <span data-ttu-id="15828-301">**[ユーザーとグループ]**、**[ユーザーの追加、パスワードのリセットなど]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-301">Click on **Users and Groups** and then **Add users, reset passwords, and more**.</span></span>

- <span data-ttu-id="15828-302">Surface Hub アカウントをクリックし、次にペン アイコンをクリックして、アカウント情報を編集します。</span><span class="sxs-lookup"><span data-stu-id="15828-302">Click the Surface Hub account, and then click the pen icon to edit the account information.</span></span>

- <span data-ttu-id="15828-303">**[ライセンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-303">Click **Licenses**.</span></span>

- <span data-ttu-id="15828-304">**[ライセンスの割り当て]** で、ライセンスとエンタープライズ VoIP の要件に応じて、Skype for Business (プラン 2) または Skype for Business (プラン 3) を選択します。</span><span class="sxs-lookup"><span data-stu-id="15828-304">In **Assign licenses**, select Skype for Business (Plan 2) or Skype for Business (Plan 3), depending on your licensing and Enterprise Voice requirements.</span></span> <span data-ttu-id="15828-305">Surface Hub でエンタープライズ VoIP を使用する場合は、プラン 3 のライセンスを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-305">You'll have to use a Plan 3 license if you want to use Enterprise Voice on your Surface Hub.</span></span>

- <span data-ttu-id="15828-306">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15828-306">Click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="15828-307">これらのライセンスのいずれかの割り当てに必要なコマンドレットを実行するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールも使用できますが、ここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="15828-307">You can also use the Windows Azure Active Directory Module for Windows PowerShell to run the cmdlets needed to assign one of these licenses, but that's not covered here.</span></span>

<span data-ttu-id="15828-308">検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-308">For validation, you should be able to use any Skype for Business client (PC, Android, etc) to sign in to this account.</span></span>

### <span data-ttu-id="15828-309">Skype for Business オンプレミス</span><span class="sxs-lookup"><span data-stu-id="15828-309">Skype for Business on-premises</span></span>

<span data-ttu-id="15828-310">コマンドレットを実行するには、いずれかの Skype フロントエンドに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-310">To run this cmdlet, you will need to connect to one of the Skype front-ends.</span></span> <span data-ttu-id="15828-311">Skype PowerShell を開き、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="15828-311">Open the Skype PowerShell and run:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### <span data-ttu-id="15828-312">Skype for Business ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="15828-312">Skype for Business hybrid</span></span>

<span data-ttu-id="15828-313">組織で、[Skype for Business Server と Skype for Business Online 間のハイブリッド接続](https://technet.microsoft.com/library/jj205403.aspx)を設定している場合は、アカウントを作成するためのガイダンスは標準的な Surface Hub の展開とは異なります。</span><span class="sxs-lookup"><span data-stu-id="15828-313">If your organization has set up [hybrid connectivity between Skype for Business Server and Skype for Business Online](https://technet.microsoft.com/library/jj205403.aspx), the guidance for creating accounts differs from a standard Surface Hub deployment.</span></span>

<span data-ttu-id="15828-314">Surface Hub では種類が *meetingroom* の Skype アカウントが必要になりますが、一般ユーザーの場合は種類が *user* の Skype アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="15828-314">The Surface Hub requires a Skype account of the type *meetingroom*, while a normal user would use a *user* type account in Skype.</span></span> <span data-ttu-id="15828-315">Skype サーバーがハイブリッド用に設定されていて、ローカル Skype サーバーのユーザーと Office 365 でホストされているユーザーが存在する場合、Surface Hub アカウントを作成しようとするといくつかの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15828-315">If your Skype server is set up for hybrid where you might have users on the local Skype server as well as users hosted in Office 365, you might run into a few issues when trying to create a Surface Hub account.</span></span>

<span data-ttu-id="15828-316">Skype for Business Server 2015 ハイブリッド環境では、Skype for business Online で使用するすべてのユーザーは、まずオンプレミス展開で作成し、ユーザーアカウントが Active Directory ドメインサービスで作成されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-316">In Skype for Business Server 2015 hybrid environment, any user that you want in Skype for Business Online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services.</span></span> <span data-ttu-id="15828-317">その後、ユーザーを Skype for Business Online に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="15828-317">You can then move the user to Skype for Business Online.</span></span> <span data-ttu-id="15828-318">オンプレミスからオンラインへのユーザーアカウントの移動は、 [move-csuser](https://technet.microsoft.com/library/gg398528.aspx)コマンドレットによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="15828-318">The move of a user account from on-premises to online is done via the [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) cmdlet.</span></span> <span data-ttu-id="15828-319">Csroom Room オブジェクトを移動するには、 [move-Csroom room](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396)コマンドレットを使います。</span><span class="sxs-lookup"><span data-stu-id="15828-319">To move a Csmeetingroom object, use the [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="15828-320">6.0.9319.281 のムーブルームコマンドレットを使用するには、 [Skype For Business server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)または[Lync server 2013 の2017年7月の累積更新プログラム 5.0.8308.992](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)の2017年5月の累積更新プログラムをインストールしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="15828-320">To use the Move-CsMeetingRoom cmdlet, you must have installed [the May 2017 cumulative update 6.0.9319.281 for Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) or [the July 2017 cumulative update 5.0.8308.992 for Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span></span>
