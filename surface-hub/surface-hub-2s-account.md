---
title: Surface Hub 2S デバイス アカウントの作成
description: このページでは、Surface Hub 2S device アカウントを作成する手順について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 6d8c41872481d86316d8985871fe74823e005ed8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836381"
---
# <span data-ttu-id="837bc-104">Surface Hub 2S デバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="837bc-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="837bc-105">Surface Hub デバイスアカウント (Room メールボックスとも呼ばれます) を作成すると、Surface Hub 2 で、Microsoft Teams または Skype for Business を使用して会議出席依頼を受信、承認、または拒否し、会議に参加することができます。</span><span class="sxs-lookup"><span data-stu-id="837bc-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings using either Microsoft Teams or Skype for Business.</span></span> <span data-ttu-id="837bc-106">Box (OOBE) セットアップ中にデバイスアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="837bc-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="837bc-107">必要に応じて、後で変更することができます (OOBE セットアップを開始する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="837bc-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="837bc-108">既定では無効になっている標準的な会議用メールボックスとは異なり、Surface Hub の 2S device アカウントを有効にして、Microsoft Teams と Skype for Business にサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="837bc-108">Unlike standard Room mailboxes that remain disabled by default, you need to enable the Surface Hub 2S device account to sign on to Microsoft Teams and Skype for Business.</span></span> <span data-ttu-id="837bc-109">Surface Hub 2S は Exchange ActiveSync に依存します。これには、デバイスアカウントに ActiveSync メールボックスポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="837bc-109">Surface Hub 2S relies on Exchange ActiveSync, which requires an ActiveSync mailbox policy on the device account.</span></span> <span data-ttu-id="837bc-110">Exchange Online に付属の既定の ActiveSync メールボックスポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="837bc-110">Apply the default ActiveSync mailbox policy that comes with Exchange Online.</span></span>

<span data-ttu-id="837bc-111">Microsoft 365 管理センターを使用するか、PowerShell を使用して、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="837bc-111">Create the account by using the Microsoft 365 admin center or by using PowerShell.</span></span> <span data-ttu-id="837bc-112">Exchange Online PowerShell を使用して、次のような特定の機能を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="837bc-112">You can use Exchange Online PowerShell to configure specific features including:</span></span>

- <span data-ttu-id="837bc-113">すべての Surface Hub デバイスアカウントの予定表処理</span><span class="sxs-lookup"><span data-stu-id="837bc-113">Calendar processing for every Surface Hub device account.</span></span>
- <span data-ttu-id="837bc-114">スケジュール要求に対するユーザー設定の自動応答</span><span class="sxs-lookup"><span data-stu-id="837bc-114">Custom auto replies to scheduling requests.</span></span>
- <span data-ttu-id="837bc-115">既定の ActiveSync メールボックスポリシーが、他のユーザーまたは別のプロセスによって既に変更されている場合は、新しい ActiveSync メールボックスポリシーを作成して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="837bc-115">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!NOTE]  
> <span data-ttu-id="837bc-116">Surface Hub デバイスアカウントは、サードパーティフェデレーション Id プロバイダー (FIPs) をサポートしておらず、標準の Active Directory アカウントまたは Azure Active Directory アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="837bc-116">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <span data-ttu-id="837bc-117">Microsoft 365 管理センターを使用してアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="837bc-117">Create account using Microsoft 365 admin center</span></span>

1. <span data-ttu-id="837bc-118">Microsoft 365 管理センターで、[**リソース**] に移動し、[**会議 & 室**] を選択して、[ **+ Room**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="837bc-118">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Room**.</span></span>

2. <span data-ttu-id="837bc-119">デバイスアカウントの名前とメールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="837bc-119">Provide a name and email address for the device account.</span></span> <span data-ttu-id="837bc-120">残りの設定は既定の状態のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="837bc-120">Leave remaining settings unchanged in the default state.</span></span>

   ![名前とメールアドレスを入力する](images/sh2-account2.png)

   ![その他の設定は既定の状態のままにします。](images/sh2-account3.png)

3. <span data-ttu-id="837bc-123">デバイスアカウントのパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="837bc-123">Set the password for the device account.</span></span> <span data-ttu-id="837bc-124">パスワードを設定するには、[**ユーザー** ]、[**アクティブなユーザー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="837bc-124">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="837bc-125">新しく作成されたユーザーを検索して、パスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="837bc-125">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="837bc-126">[**このユーザーが最初にサインインしたときにパスワードの変更を行う**] オプションを選択して**いない**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="837bc-126">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![デバイスアカウントのパスワードを設定する](images/sh2-account4.png)

4. <span data-ttu-id="837bc-128">Office 365 ライセンスを持つ会議室を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="837bc-128">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="837bc-129">Skype for Business Online および Microsoft Teams のアカウントを自動的に有効にする新しいオプションとして、Office 365**会議室**ライセンスを割り当てることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="837bc-129">It’s recommended to assign the Office 365 **Meeting Room** license, a new option that automatically enables the account for Skype for Business Online and Microsoft Teams.</span></span>

   ![Office 365 ライセンスを割り当てる](images/sh2-account5.png)

### <span data-ttu-id="837bc-131">PowerShell を使用してセットアップを完了する</span><span class="sxs-lookup"><span data-stu-id="837bc-131">Finalize setup via PowerShell</span></span>

- <span data-ttu-id="837bc-132">**Skype For business:** Skype for Business のみ (オンプレミスまたはオンライン) の場合、Skype for business オブジェクトを有効にするには、[ **enable-Csroom room** ] を実行して、音声およびロビーホールドの会議室のプロンプトなどの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="837bc-132">**Skype for Business:** For Skype for Business only (on-premises or online), you can enable the Skype for Business object by running **Enable-CsMeetingRoom** to enable features such as Meeting room prompt for audio and Lobby hold.</span></span>

- <span data-ttu-id="837bc-133">**Microsoft Teams と Skype For business の予定表:** このアカウントの[**カレンダー自動処理**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing)を設定します。</span><span class="sxs-lookup"><span data-stu-id="837bc-133">**Microsoft Teams and Skype for Business Calendar:** Set [**Calendar Auto processing**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) for this account.</span></span>

## <span data-ttu-id="837bc-134">PowerShell を使用してアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="837bc-134">Create account using PowerShell</span></span>

<span data-ttu-id="837bc-135">Microsoft 管理センターポータルを使用する代わりに、PowerShell を使用してアカウントを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="837bc-135">Instead of using the Microsoft Admin Center portal, you can create the account using PowerShell.</span></span>

### <span data-ttu-id="837bc-136">Exchange Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="837bc-136">Connect to Exchange Online PowerShell</span></span>

```powershell
$365Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential (Get-Credential) -Authentication Basic –AllowRedirection
$ImportResults = Import-PSSession $365Session
```

### <span data-ttu-id="837bc-137">新しい会議室メールボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="837bc-137">Create a new Room mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID account@YourDomain.com -Alias SurfaceHub2S -Name SurfaceHub2S -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString  -String "<Enter Strong Password>" -AsPlainText -Force)
```

### <span data-ttu-id="837bc-138">予定表の自動処理を設定する</span><span class="sxs-lookup"><span data-stu-id="837bc-138">Set Calendar auto-processing</span></span>

```powershell
Set-CalendarProcessing -Identity "account@YourDomain.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

### <span data-ttu-id="837bc-139">ライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="837bc-139">Assign a license</span></span>

```powershell
Connect-MsolService
Set-Msoluser -UserPrincipalName account@YourDomain.com -UsageLocation IE
Set-MsolUserLicense -UserPrincipalName "account@YourDomain.com" -AddLicenses "contoso:MEETING_ROOM"
```

## <span data-ttu-id="837bc-140">PowerShell を使用して Skype for Business Online に接続する</span><span class="sxs-lookup"><span data-stu-id="837bc-140">Connect to Skype for Business Online using PowerShell</span></span>

### <span data-ttu-id="837bc-141">前提条件をインストールする</span><span class="sxs-lookup"><span data-stu-id="837bc-141">Install pre-requisites</span></span>

- [<span data-ttu-id="837bc-142">Visual C++ 2017 再頒布可能</span><span class="sxs-lookup"><span data-stu-id="837bc-142">Visual C++ 2017 Redistributable</span></span>](https://aka.ms/vs/15/release/vc_redist.x64.exe)
- [<span data-ttu-id="837bc-143">Skype for Business Online PowerShell モジュール</span><span class="sxs-lookup"><span data-stu-id="837bc-143">Skype for Business Online PowerShell Module</span></span>](https://www.microsoft.com/download/confirmation.aspx?id=39366)

```powershell
Import-Module LyncOnlineConnector
$SfBSession = New-CsOnlineSession -Credential (Get-Credential)
Import-PSSession $SfBSession -AllowClobber

# Enable the Skype for Business meeting room
Enable-CsMeetingRoom -Identity account@YourDomain.com -RegistrarPool(Get-CsTenant).Registrarpool -SipAddressType EmailAddress
```
