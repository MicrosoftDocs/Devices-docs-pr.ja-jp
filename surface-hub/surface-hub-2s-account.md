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
ms.date: 12/07/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e171d7c2db8a0d69594ca8d5f3a54f33ecebc9ae
ms.sourcegitcommit: dc08a2096a1fe955eb67e736e2a4453f75e926be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "11196730"
---
# <span data-ttu-id="a6922-104">Surface Hub 2S デバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="a6922-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="a6922-105">Surface Hub デバイスアカウント (Room メールボックスとも呼ばれます) を作成すると、Surface Hub 2 で、Microsoft Teams または Skype for Business を使用して会議出席依頼を受信、承認、または拒否し、会議に参加することができます。</span><span class="sxs-lookup"><span data-stu-id="a6922-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings using either Microsoft Teams or Skype for Business.</span></span> <span data-ttu-id="a6922-106">Box (OOBE) セットアップ中にデバイスアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="a6922-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="a6922-107">必要に応じて、後で変更することができます (OOBE セットアップを開始する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="a6922-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="a6922-108">既定では無効になっている標準的な会議用メールボックスとは異なり、Surface Hub の 2S device アカウントを有効にして、Microsoft Teams と Skype for Business にサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6922-108">Unlike standard Room mailboxes that remain disabled by default, you need to enable the Surface Hub 2S device account to sign on to Microsoft Teams and Skype for Business.</span></span> <span data-ttu-id="a6922-109">Surface Hub 2S は Exchange ActiveSync に依存します。これには、デバイスアカウントに ActiveSync メールボックスポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a6922-109">Surface Hub 2S relies on Exchange ActiveSync, which requires an ActiveSync mailbox policy on the device account.</span></span> <span data-ttu-id="a6922-110">Exchange Online に付属の既定の ActiveSync メールボックスポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="a6922-110">Apply the default ActiveSync mailbox policy that comes with Exchange Online.</span></span>

<span data-ttu-id="a6922-111">Microsoft 365 管理センターを使用するか、PowerShell を使用して、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="a6922-111">Create the account by using the Microsoft 365 admin center or by using PowerShell.</span></span> <span data-ttu-id="a6922-112">Exchange Online PowerShell を使用して、次のような特定の機能を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="a6922-112">You can use Exchange Online PowerShell to configure specific features including:</span></span>

- <span data-ttu-id="a6922-113">すべての Surface Hub デバイスアカウントの予定表処理</span><span class="sxs-lookup"><span data-stu-id="a6922-113">Calendar processing for every Surface Hub device account.</span></span>
- <span data-ttu-id="a6922-114">スケジュール要求に対するユーザー設定の自動応答</span><span class="sxs-lookup"><span data-stu-id="a6922-114">Custom auto replies to scheduling requests.</span></span>
- <span data-ttu-id="a6922-115">既定の ActiveSync メールボックスポリシーが、他のユーザーまたは別のプロセスによって既に変更されている場合は、新しい ActiveSync メールボックスポリシーを作成して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6922-115">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!NOTE]  
> <span data-ttu-id="a6922-116">Surface Hub デバイスアカウントは、サードパーティフェデレーション Id プロバイダー (FIPs) をサポートしておらず、標準の Active Directory アカウントまたは Azure Active Directory アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6922-116">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <span data-ttu-id="a6922-117">Microsoft 365 管理センターを使用してアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="a6922-117">Create account using Microsoft 365 admin center</span></span>

1. <span data-ttu-id="a6922-118">Microsoft 365 管理センターで、[ **リソース** ] に移動し、[ **会議 & 室** ] を選択して、[ **+ Room**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6922-118">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Room**.</span></span>

2. <span data-ttu-id="a6922-119">デバイスアカウントの名前とメールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="a6922-119">Provide a name and email address for the device account.</span></span> <span data-ttu-id="a6922-120">残りの設定は既定の状態のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="a6922-120">Leave remaining settings unchanged in the default state.</span></span>

   ![名前とメールアドレスを入力する](images/sh2-account2.png)

   ![その他の設定は既定の状態のままにします。](images/sh2-account3.png)

3. <span data-ttu-id="a6922-123">デバイスアカウントのパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6922-123">Set the password for the device account.</span></span> <span data-ttu-id="a6922-124">パスワードを設定するには、[ **ユーザー** ]、[ **アクティブなユーザー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a6922-124">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="a6922-125">新しく作成されたユーザーを検索して、パスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6922-125">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="a6922-126">[**このユーザーが最初にサインインしたときにパスワードの変更を行う**] オプションを選択して**いない**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a6922-126">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![デバイスアカウントのパスワードを設定する](images/sh2-account4.png)

4. <span data-ttu-id="a6922-128">Office 365 ライセンスを持つ会議室を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a6922-128">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="a6922-129">Skype for Business Online および Microsoft Teams のアカウントを自動的に有効にする新しいオプションとして、Office 365 **会議室** ライセンスを割り当てることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6922-129">It’s recommended to assign the Office 365 **Meeting Room** license, a new option that automatically enables the account for Skype for Business Online and Microsoft Teams.</span></span>

   ![Office 365 ライセンスを割り当てる](images/sh2-account5.png)

### <span data-ttu-id="a6922-131">PowerShell を使用してセットアップを完了する</span><span class="sxs-lookup"><span data-stu-id="a6922-131">Finalize setup via PowerShell</span></span>

- <span data-ttu-id="a6922-132">**Microsoft Teams と Skype For business の予定表:** このアカウントの [**カレンダー自動処理**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) を設定します。</span><span class="sxs-lookup"><span data-stu-id="a6922-132">**Microsoft Teams and Skype for Business Calendar:** Set [**Calendar Auto processing**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) for this account.</span></span>

## <span data-ttu-id="a6922-133">PowerShell を使用してアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="a6922-133">Create account using PowerShell</span></span>

<span data-ttu-id="a6922-134">Microsoft 管理センターポータルを使用する代わりに、PowerShell を使用してアカウントを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a6922-134">Instead of using the Microsoft Admin Center portal, you can create the account using PowerShell.</span></span>

### <span data-ttu-id="a6922-135">Exchange Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="a6922-135">Connect to Exchange Online PowerShell</span></span>

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### <span data-ttu-id="a6922-136">メールボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="a6922-136">Create mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### <span data-ttu-id="a6922-137">予定表の自動処理を設定する</span><span class="sxs-lookup"><span data-stu-id="a6922-137">Set Calendar auto-processing</span></span>

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### <span data-ttu-id="a6922-138">メールアプリを使用する必要がある場合は、ActiveSync を有効にする</span><span class="sxs-lookup"><span data-stu-id="a6922-138">Enable ActiveSync if use of email app is required</span></span>

 <span data-ttu-id="a6922-139">既定の ActiveSync ポリシーは、解除された場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="a6922-139">The default ActiveSync Policy will work if unchnaged.</span></span> <span data-ttu-id="a6922-140">または、新しいポリシーを作成して割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a6922-140">Otherwise create a new Policy and assign.</span></span>

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```
### <span data-ttu-id="a6922-141">Azure AD への接続</span><span class="sxs-lookup"><span data-stu-id="a6922-141">Connect to Azure AD</span></span>

```powershell
Connect-AzureAD
```

### <span data-ttu-id="a6922-142">ライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a6922-142">Assign a license</span></span>

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### <span data-ttu-id="a6922-143">利用可能なライセンスを確認する</span><span class="sxs-lookup"><span data-stu-id="a6922-143">Check for available licenses</span></span>

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```