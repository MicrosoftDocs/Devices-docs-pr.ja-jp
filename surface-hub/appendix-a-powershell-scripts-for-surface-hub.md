---
title: Surface Hub 用 PowerShell (Surface Hub)
description: Microsoft Surface Hub の設定と管理に役立つ PowerShell スクリプトです。
ms.assetid: 3EF48F63-8E4C-4D74-ACD5-461F1C653784
ms.reviewer: ''
manager: laurawi
keywords: PowerShell, Surface Hub のセットアップ, Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/10/2018
ms.localizationpriority: medium
ms.openlocfilehash: 92b42139020db13251fa6c5f8439d7084a61a132
ms.sourcegitcommit: 5d02cca9ca8c0a252798c2fc0a89dbda81911c44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "11195382"
---
# <span data-ttu-id="6b623-104">Surface Hub 用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b623-104">PowerShell for Surface Hub</span></span>

<span data-ttu-id="6b623-105">Microsoft Surface Hub の設定と管理に役立つ PowerShell スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="6b623-105">PowerShell scripts to help set up and manage your Microsoft Surface Hub.</span></span>

-   [<span data-ttu-id="6b623-106">Surface Hub 管理者向けの PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="6b623-106">PowerShell scripts for Surface Hub admins</span></span>](#scripts-for-admins)
    -   [<span data-ttu-id="6b623-107">オンプレミスアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="6b623-107">Create an on-premises account</span></span>](#create-on-premises-ps-scripts)
    -   [<span data-ttu-id="6b623-108">Office 365 を使ったデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="6b623-108">Create a device account using Office 365</span></span>](#create-os356-ps-scripts)
    -   [<span data-ttu-id="6b623-109">アカウント検証スクリプト</span><span class="sxs-lookup"><span data-stu-id="6b623-109">Account verification script</span></span>](#acct-verification-ps-scripts)
    -   [<span data-ttu-id="6b623-110">Skype for Business の有効化 (EnableSfb.ps1)</span><span class="sxs-lookup"><span data-stu-id="6b623-110">Enable Skype for Business (EnableSfb.ps1)</span></span>](#enable-sfb-ps-scripts)
-   [<span data-ttu-id="6b623-111">便利なコマンドレット</span><span class="sxs-lookup"><span data-stu-id="6b623-111">Useful cmdlets</span></span>](#useful-cmdlets)
    -   [<span data-ttu-id="6b623-112">Surface Hub と互換性のある Exchange ActiveSync ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="6b623-112">Creating a Surface Hub-compatible Exchange ActiveSync policy</span></span>](#create-compatible-as-policy)
    -   [<span data-ttu-id="6b623-113">ActiveSync に対するデバイス ID の許可</span><span class="sxs-lookup"><span data-stu-id="6b623-113">Allowing device IDs for ActiveSync</span></span>](#whitelisting-device-ids-cmdlet)
    -   [<span data-ttu-id="6b623-114">会議出席依頼の自動的な承諾と辞退</span><span class="sxs-lookup"><span data-stu-id="6b623-114">Auto-accepting and declining meeting requests</span></span>](#auto-accept-meetings-cmdlet)
    -   [<span data-ttu-id="6b623-115">外部会議出席依頼の承諾</span><span class="sxs-lookup"><span data-stu-id="6b623-115">Accepting external meeting requests</span></span>](#accept-ext-meetings-cmdlet)
    
 > [!NOTE]
 > <span data-ttu-id="6b623-116">「[モダン Auth」および「Exchange Online PowerShell V2 の無人スクリプト](https://techcommunity.microsoft.com/t5/exchange-team-blog/modern-auth-and-unattended-scripts-in-exchange-online-powershell/ba-p/1497387)」もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6b623-116">See also [Modern Auth and Unattended Scripts in Exchange Online PowerShell V2](https://techcommunity.microsoft.com/t5/exchange-team-blog/modern-auth-and-unattended-scripts-in-exchange-online-powershell/ba-p/1497387)</span></span>

## <span data-ttu-id="6b623-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="6b623-117">Prerequisites</span></span>

<span data-ttu-id="6b623-118">これらの PowerShell スクリプトを正常に実行するには、次の前提条件をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-118">To successfully execute these PowerShell scripts, you will need to install the following prerequisites:</span></span>

- [<span data-ttu-id="6b623-119">IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW</span><span class="sxs-lookup"><span data-stu-id="6b623-119">Microsoft Online Services Sign-in Assistant for IT Professionals RTW</span></span>](https://www.microsoft.com/download/details.aspx?id=41950)
- [<span data-ttu-id="6b623-120">Windows PowerShell 用 Microsoft Azure Active Directory モジュール (64 ビット版)</span><span class="sxs-lookup"><span data-stu-id="6b623-120">Microsoft Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://www.powershellgallery.com/packages/MSOnline/1.1.183.17)
- [<span data-ttu-id="6b623-121">Windows PowerShell Module for Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="6b623-121">Windows PowerShell Module for Skype for Business Online</span></span>](https://www.microsoft.com/download/details.aspx?id=39366)

## <a href="" id="scripts-for-admins"></a><span data-ttu-id="6b623-122">Surface Hub 管理者向けの PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="6b623-122">PowerShell scripts for Surface Hub administrators</span></span>

<span data-ttu-id="6b623-123">スクリプトには、次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-123">What do the scripts do?</span></span>

-   <span data-ttu-id="6b623-124">純粋な単一フォレストの社内 (Microsoft Exchange および Skype 2013 以降のみ) またはオンライン (Microsoft Office 365) を使って、セットアップ用にデバイス アカウントを作成します。作成したアカウントはお使いの Surface Hub 向けに正しく構成されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-124">Create device accounts for setups using pure single-forest on-premises (Microsoft Exchange and Skype 2013 and later only) or online (Microsoft Office 365), that are configured correctly for your Surface Hub.</span></span>
-   <span data-ttu-id="6b623-125">任意のセットアップ (オンプレミスまたはオンライン) 用の既存のデバイス アカウントを検証して、アカウントに Surface Hub と互換性があることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="6b623-125">Validate existing device accounts for any setup (on-premises or online) to make sure they're compatible with Surface Hub.</span></span>
-   <span data-ttu-id="6b623-126">独自のデバイス アカウント作成スクリプトや検証スクリプトを作成するすべてのユーザーに、基本となるテンプレートを提供します。</span><span class="sxs-lookup"><span data-stu-id="6b623-126">Provide a base template for anyone wanting to create their own device account creation or validation scripts.</span></span>

<span data-ttu-id="6b623-127">スクリプトを実行するための要件は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b623-127">What do you need in order to run the scripts?</span></span>

-   <span data-ttu-id="6b623-128">組織のドメインまたはテナント、Exchange サーバー、および Skype for Business サーバーへのリモートの PowerShell アクセス</span><span class="sxs-lookup"><span data-stu-id="6b623-128">Remote PowerShell access to your organization's domain or tenant, Exchange servers, and Skype for Business servers.</span></span>
-   <span data-ttu-id="6b623-129">組織のドメインまたはテナント、Exchange サーバー、および Skype for Business サーバーに対する管理者の資格情報</span><span class="sxs-lookup"><span data-stu-id="6b623-129">Admin credentials for your organization's domain or tenant, Exchange servers, and Skype for Business servers.</span></span>

> [!NOTE]
> <span data-ttu-id="6b623-130">新しいアカウントを作成する場合でも、既存のアカウントを変更する場合でも、検証スクリプトを実行すると、デバイス アカウントが正しく構成されていることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-130">Whether you’re creating a new account or modifying an already-existing account, the validation script will verify that your device account is configured correctly.</span></span> <span data-ttu-id="6b623-131">デバイス アカウントを Surface Hub に追加する前には、必ず検証スクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-131">You should always run the validation script before adding a device account to Surface Hub.</span></span>

## <span data-ttu-id="6b623-132">スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="6b623-132">Running the scripts</span></span>

<span data-ttu-id="6b623-133">アカウント作成スクリプトでは、次の処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-133">The account creation scripts will:</span></span>

-   <span data-ttu-id="6b623-134">管理者の資格情報を要求する。</span><span class="sxs-lookup"><span data-stu-id="6b623-134">Ask for administrator credentials</span></span>
-   <span data-ttu-id="6b623-135">ドメイン/テナントにデバイス アカウントを作成する。</span><span class="sxs-lookup"><span data-stu-id="6b623-135">Create device accounts in your domain/tenant</span></span>
-   <span data-ttu-id="6b623-136">Surface Hub と互換性のある ActiveSync ポリシーを作成する、またはこのようなポリシーをデバイス アカウントに割り当てる。</span><span class="sxs-lookup"><span data-stu-id="6b623-136">Create or assign a Surface Hub-compatible ActiveSync policy to the device account(s)</span></span>
-   <span data-ttu-id="6b623-137">Exchange と Skype for Business で、作成されたアカウントに関するさまざまな属性を設定する。</span><span class="sxs-lookup"><span data-stu-id="6b623-137">Set various attributes for the created account(s) in Exchange and Skype for Business.</span></span>
-   <span data-ttu-id="6b623-138">作成されたアカウントに、ライセンスとアクセス許可を割り当てる。</span><span class="sxs-lookup"><span data-stu-id="6b623-138">Assign licenses and permissions to the created account(s)</span></span>

<span data-ttu-id="6b623-139">スクリプトによって設定される属性は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b623-139">These are the attributes that are set by the scripts:</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6b623-140">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="6b623-140">Cmdlet</span></span></th>
<th align="left"><span data-ttu-id="6b623-141">属性</span><span class="sxs-lookup"><span data-stu-id="6b623-141">Attribute</span></span></th>
<th align="left"><span data-ttu-id="6b623-142">値</span><span class="sxs-lookup"><span data-stu-id="6b623-142">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="6b623-143">Set-Mailbox</span><span class="sxs-lookup"><span data-stu-id="6b623-143">Set-Mailbox</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-144">RoomMailboxPassword</span><span class="sxs-lookup"><span data-stu-id="6b623-144">RoomMailboxPassword</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-145">ユーザー指定</span><span class="sxs-lookup"><span data-stu-id="6b623-145">User-provided</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-146">EnableRoomMailboxAccount</span><span class="sxs-lookup"><span data-stu-id="6b623-146">EnableRoomMailboxAccount</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-147">True</span><span class="sxs-lookup"><span data-stu-id="6b623-147">True</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-148">Type</span><span class="sxs-lookup"><span data-stu-id="6b623-148">Type</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-149">Room</span><span class="sxs-lookup"><span data-stu-id="6b623-149">Room</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="6b623-150">Set-CalendarProcessing</span><span class="sxs-lookup"><span data-stu-id="6b623-150">Set-CalendarProcessing</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-151">AutomateProcessing</span><span class="sxs-lookup"><span data-stu-id="6b623-151">AutomateProcessing</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-152">AutoAccept</span><span class="sxs-lookup"><span data-stu-id="6b623-152">AutoAccept</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-153">RemovePrivateProperty</span><span class="sxs-lookup"><span data-stu-id="6b623-153">RemovePrivateProperty</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-154">False</span><span class="sxs-lookup"><span data-stu-id="6b623-154">False</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-155">DeleteSubject</span><span class="sxs-lookup"><span data-stu-id="6b623-155">DeleteSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-156">False</span><span class="sxs-lookup"><span data-stu-id="6b623-156">False</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-157">DeleteComments</span><span class="sxs-lookup"><span data-stu-id="6b623-157">DeleteComments</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-158">False</span><span class="sxs-lookup"><span data-stu-id="6b623-158">False</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-159">AddOrganizerToSubject</span><span class="sxs-lookup"><span data-stu-id="6b623-159">AddOrganizerToSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-160">False</span><span class="sxs-lookup"><span data-stu-id="6b623-160">False</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-161">AddAdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="6b623-161">AddAdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-162">True</span><span class="sxs-lookup"><span data-stu-id="6b623-162">True</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-163">AdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="6b623-163">AdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-164">&quot;This is a Surface Hub room!&quot;</span><span class="sxs-lookup"><span data-stu-id="6b623-164">&quot;This is a Surface Hub room!&quot;</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="6b623-165">New-MobileDeviceMailboxPolicy</span><span class="sxs-lookup"><span data-stu-id="6b623-165">New-MobileDeviceMailboxPolicy</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-166">PasswordEnabled</span><span class="sxs-lookup"><span data-stu-id="6b623-166">PasswordEnabled</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-167">False</span><span class="sxs-lookup"><span data-stu-id="6b623-167">False</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-168">AllowNonProvisionableDevices</span><span class="sxs-lookup"><span data-stu-id="6b623-168">AllowNonProvisionableDevices</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-169">True</span><span class="sxs-lookup"><span data-stu-id="6b623-169">True</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="6b623-170">Enable-CSMeetingRoom</span><span class="sxs-lookup"><span data-stu-id="6b623-170">Enable-CSMeetingRoom</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-171">RegistrarPool</span><span class="sxs-lookup"><span data-stu-id="6b623-171">RegistrarPool</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-172">ユーザー指定</span><span class="sxs-lookup"><span data-stu-id="6b623-172">User-provided</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p><span data-ttu-id="6b623-173">SipAddress</span><span class="sxs-lookup"><span data-stu-id="6b623-173">SipAddress</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-174">デバイス アカウントのユーザー プリンシパル名 (UPN) に設定</span><span class="sxs-lookup"><span data-stu-id="6b623-174">Set to the User Principal Name (UPN) of the device account</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="6b623-175">Set-MsolUserLicense (O365 のみ)</span><span class="sxs-lookup"><span data-stu-id="6b623-175">Set-MsolUserLicense (O365 only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-176">AddLicenses</span><span class="sxs-lookup"><span data-stu-id="6b623-176">AddLicenses</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-177">ユーザー指定</span><span class="sxs-lookup"><span data-stu-id="6b623-177">User-provided</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="6b623-178">Set-MsolUser (O365 のみ)</span><span class="sxs-lookup"><span data-stu-id="6b623-178">Set-MsolUser (O365 only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-179">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="6b623-179">PasswordNeverExpires</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-180">True</span><span class="sxs-lookup"><span data-stu-id="6b623-180">True</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="6b623-181">Set-AdUser (社内のみ)</span><span class="sxs-lookup"><span data-stu-id="6b623-181">Set-AdUser (On-prem only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-182">Enabled</span><span class="sxs-lookup"><span data-stu-id="6b623-182">Enabled</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-183">True</span><span class="sxs-lookup"><span data-stu-id="6b623-183">True</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="6b623-184">Set-AdUser (社内のみ)</span><span class="sxs-lookup"><span data-stu-id="6b623-184">Set-AdUser (On-prem only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-185">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="6b623-185">PasswordNeverExpires</span></span></p></td>
<td align="left"><p><span data-ttu-id="6b623-186">True</span><span class="sxs-lookup"><span data-stu-id="6b623-186">True</span></span></p></td>
</tr>
</tbody>
</table>

## <span data-ttu-id="6b623-187">アカウント作成スクリプト</span><span class="sxs-lookup"><span data-stu-id="6b623-187">Account creation scripts</span></span>

<span data-ttu-id="6b623-188">これらのスクリプトを実行すると、デバイス アカウントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-188">These scripts will create a device account for you.</span></span> <span data-ttu-id="6b623-189">正しく実行されたことを確かめるには、[アカウント検証スクリプト](#acct-verification-ps-scripts)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b623-189">You can use the [Account verification script](#acct-verification-ps-scripts) to make sure they ran correctly.</span></span>

<span data-ttu-id="6b623-190">アカウント作成スクリプトで既存のアカウントを変更することはできませんが、アカウント作成スクリプトを使うと、既存のアカウントを正しく構成するにはどのコマンドレットを実行する必要があるかを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6b623-190">The account creation scripts cannot modify an already existing account, but can be used to help you understand which cmdlets need to be run to configure the existing account correctly.</span></span>

### <a href="" id="create-on-premises-ps-scripts"></a><span data-ttu-id="6b623-191">オンプレミスアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="6b623-191">Create an on-premises account</span></span>

<span data-ttu-id="6b623-192">「[社内展開](on-premises-deployment-surface-hub-device-accounts.md)」で説明しているとおりに、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b623-192">Creates an account as described in [On-premises deployment](on-premises-deployment-surface-hub-device-accounts.md).</span></span>

```PowerShell
# SHAccountCreateOnPrem.ps1

$Error.Clear()
$ErrorActionPreference = "Stop"
$status = @{}

# Cleans up set state such as remote powershell sessions
function Cleanup()
{
    if ($sessExchange)
    {
        Remove-PSSession $sessExchange
    }
    if ($sessCS)
    {
        Remove-PSSession $sessCS
    }
}

function PrintError($strMsg)
{
    Write-Host $strMsg -foregroundcolor Red
}

function PrintSuccess($strMsg)
{
    Write-Host $strMsg -foregroundcolor Green
}

function PrintAction($strMsg)
{
    Write-Host $strMsg -ForegroundColor Cyan
}


# Cleans up and prints an error message
function CleanupAndFail($strMsg)
{
    if ($strMsg)
    {
        PrintError($strMsg);
    }
    Cleanup
    exit 1
}

# Exits if there is an error set and prints the given message
function ExitIfError($strMsg)
{
    if ($Error)
    {
        CleanupAndFail($strMsg);
    }
}

## Collect account data ##
$credNewAccount = (Get-Credential -Message "Enter the desired UPN and password for this new account")
$strUpn = $credNewAccount.UserName
$strDisplayName = Read-Host "Please enter the display name you would like to use for $strUpn"
if (!$credNewAccount -Or [System.String]::IsNullOrEmpty($strDisplayName) -Or [System.String]::IsNullOrEmpty($credNewAccount.UserName) -Or $credNewAccount.Password.Length -le 0)
{
    CleanupAndFail "Please enter all of the requested data to continue."
    exit 1
}

## Sign in to remote powershell for exchange and lync online ##

$credExchange = $null
$credExchange=Get-Credential -Message "Enter credentials of an Exchange user with mailbox creation rights"
if (!$credExchange)
{
    CleanupAndFail("Valid credentials are required to create and prepare the account.");
}
$strExchangeServer = Read-Host "Please enter the FQDN of your exchange server (e.g. exch.contoso.com)"

# Lync info
$credLync = Get-Credential -Message "Enter credentials of a Skype for Business admin (or cancel if they are the same as Exchange)"
if (!$credLync)
{
    $credLync = $credExchange
}
$strLyncFQDN = Read-Host "Please enter the FQDN of your Lync server (e.g. lync.contoso.com) or enter to use [$strExchangeServer]"
if ([System.String]::IsNullOrEmpty($strLyncFQDN))
{
    $strLyncFQDN = $strExchangeServer
}


PrintAction "Connecting to remote sessions. This can occasionally take a while - please do not enter input..."
try
{
    $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $credExchange -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
}
catch
{
    CleanupAndFail("Failed to connect to exchange. Please check your credentials and try again. If this continues to fail, you may not have permission for remote powershell - if not, please perform the setup manually. Error message: $_")
}
PrintSuccess "Connected to Remote Exchange Shell"

try
{
    $sessLync = New-PSSession -Credential $credLync -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
}
catch
{
    CleanupAndFail("Failed to connect to Lync. Please check your credentials and try again. Error message: $_")
}
PrintSuccess "Connected to Lync Server Remote PowerShell"


Import-PSSession $sessExchange -AllowClobber -WarningAction SilentlyContinue
Import-PSSession $sessLync -AllowClobber -WarningAction SilentlyContinue

## Create the Exchange mailbox ##
> [!Note]
> These exchange commandlets do not always throw their errors as exceptions

# Because Get-Mailbox will throw an error if the mailbox is not found
$Error.Clear()
PrintAction "Creating a new account..."
try
{
    $mailbox = $null
    $mailbox = (New-Mailbox -UserPrincipalName $credNewAccount.UserName -Alias $credNewAccount.UserName.substring(0,$credNewAccount.UserName.indexOf('@')) -room -Name $strDisplayName -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true)
} catch { }
ExitIfError "Failed to create a new mailbox on exchange.";
$status["Mailbox Setup"] = "Successfully created a mailbox for the new account"


$strEmail = $mailbox.WindowsEmailAddress
PrintSuccess "The following mailbox has been created for this room: $strEmail"

## Create or retrieve a policy that will be applied to surface hub devices ##
# The policy disables requiring a device password so that the SurfaceHub does not need to be lockable to use Active Sync
$strPolicy = Read-Host 'Please enter the name for a new Surface Hub ActiveSync policy that will be created and applied to this account.
We will configure that policy to be compatible with Surface Hub devices.
If this script has been used before, please enter the name of the existing policy.'

$easpolicy = $null
try {
    $easpolicy = Get-MobileDeviceMailboxPolicy $strPolicy
}
catch {}

if ($easpolicy)
{
    if (!$easpolicy.PasswordEnabled -and ($easpolicy.AllowNonProvisionableDevices -eq $null -or $easpolicy.AllowNonProvisionableDevices ))
    {
        PrintSuccess "An existing policy has been found and will be applied to this account."
    }
    else
    {
        PrintError "The policy you provided is incompatible with the surface hub."
        $easpolicy = $null
        $status["Device Password Policy"] = "Failed to apply the EAS policy to the account because the policy was invalid."
    }
}
else
{
    $Error.Clear()
    PrintAction "Creating policy..."
    $easpolicy = New-MobileDeviceMailboxPolicy -Name $strPolicy -PasswordEnabled $false -AllowNonProvisionableDevices $true
    if ($easpolicy)
    {
        PrintSuccess "A new device policy has been created; you can use this same policy for all future Surface Hub device accounts."
    }
    else
    {
        PrintError "Could not create $strPolicy"
    }
}

if ($easpolicy)
{
    # Convert mailbox to user type so we can apply the policy (necessary)
    # Sometimes it takes a while for this change to take affect so we have some nasty retry loops
    $Error.Clear();
    try
    {
        Set-Mailbox $credNewAccount.UserName -Type Regular
    } catch {}
    if ($Error)
    {
        $Error.Clear()
        $status["Device Password Policy"] = "Failed to apply the EAS policy to the account."
    }
    else
    {
        # Loop until resource type goes away, up to 5 times
        for ($i = 0; $i -lt 5 -And (Get-Mailbox $credNewAccount.UserName).ResourceType; $i++)
        {
            Start-Sleep -s 5
        }
        # If the mailbox is still a Room we cannot apply the policy
        if (!((Get-Mailbox $credNewAccount.UserName).ResourceType))
        {
            $Error.Clear()
            # Set policy for account
            Set-CASMailbox $credNewAccount.UserName -ActiveSyncMailboxPolicy $strPolicy
            if (!$Error)
            {
                $status["ActiveSync Policy"] = "Successfully applied $strPolicy to the account"
            }
            else
            {
                $status["ActiveSync Policy"] = "Failed to apply the EAS policy to the account."
            }
            $Error.Clear()

            # Convert back to room mailbox
            Set-Mailbox $credNewAccount.UserName -Type Room
            # Loop until resource type goes back to room
            for ($i = 0; ($i -lt 5) -And ((Get-Mailbox $credNewAccount.UserName).ResourceType -ne "Room"); $i++)
            {
                Start-Sleep -s 5
            }
            if ((Get-Mailbox $credNewAccount.UserName).ResourceType -ne "Room")
            {
                # A failure to convert the mailbox back to a room is unfortunate but means the mailbox is unusable.
                $status["Mailbox Setup"] = "A mailbox was created but we could not set it to a room resource type."
            }
            else
            {
                try
                {
                    Set-Mailbox $credNewAccount.UserName -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
                } catch { }
                if ($Error)
                {
                    $status["Mailbox Setup"] = "A room mailbox was created but we could not set its password."
                }
                $Error.Clear()
            }

        }
    }
}
PrintSuccess "Account creation completed."

PrintAction "Setting calendar processing rules..."

$Error.Clear();
## Prepare the calendar for automatic meeting responses ##
try {
    Set-CalendarProcessing -Identity $credNewAccount.UserName -AutomateProcessing AutoAccept
} catch { }
if ($Error)
{
    $status["Calendar Acceptance"] = "Failed to configure the account to automatically accept/decline meeting requests"
}
else
{
    $status["Calendar Acceptance"] = "Successfully configured the account to automatically accept/decline meeting requests"
}


$Error.Clear()
try {
    Set-CalendarProcessing -Identity $credNewAccount.UserName -RemovePrivateProperty $false -AddOrganizerToSubject $false -AddAdditionalResponse $true -DeleteSubject $false -DeleteComments $false -AdditionalResponse "This is a Surface Hub room!"
} catch { }
if ($Error)
{
    $status["Calendar Response Configuration"] = "Failed to configure the account's response properties"
}
else
{
    $status["Calendar Response Configuration"] = "Successfully configured the account's response properties"
}

$Error.Clear()
## Configure the Account to not expire ##
PrintAction "Configuring password not to expire..."
Start-Sleep -s 20
try
{
    Set-AdUser $mailbox.UserPrincipalName -PasswordNeverExpires $true -Enabled $true
}
catch
{

}

if ($Error)
{
    $status["Password Expiration Policy"] = "Failed to set the password to never expire"
}
else
{
    $status["Password Expiration Policy"] = "Successfully set the password to never expire"
}

PrintSuccess "Completed Exchange configuration"

## Setup Skype for Business. This is somewhat optional and if it fails we SfbEnable can be used later ##
PrintAction "Configuring account for Skype for Business."

# Getting registrar pool
$strRegPool = $strLyncFQDN
$Error.Clear()
$strRegPoolEntry = Read-Host "Enter a Skype for Business Registrar Pool, or leave blank to use [$strRegPool]"
if (![System.String]::IsNullOrEmpty($strRegPoolEntry))
{
    $strRegPool = $strRegPoolEntry
}

# Try to SfB-enable the account. Note that it may not work right away as the account needs to propagate to active directory
PrintAction "Enabling Skype for Business..."
Start-Sleep -s 10
$Error.Clear()
try {
    Enable-CsMeetingRoom -Identity $credNewAccount.UserName -RegistrarPool $strRegPool -SipAddressType EmailAddress
}
catch { }

if ($Error)
{
    $status["Skype for Business Account Setup"] = "Failed to setup the Skype for Business meeting room - you can run EnableSfb.ps1 to try again."
    $Error.Clear();
}
else
{
    $status["Skype for Business Account Setup"] = "Successfully enabled account as a Skype for Business meeting room"
}

Write-Host

## Cleanup and print results ##
Cleanup
$strDisplay = $mailbox.DisplayName
$strUsr = $credNewAccount.UserName
PrintAction "Summary for creation of $strUsr ($strDisplay)"
if ($status.Count -gt 0)
{
    ForEach($k in $status.Keys)
    {
        $v = $status[$k]
        $color = "yellow"
        if ($v[0] -eq "S") { $color = "green" }
        elseif ($v[0] -eq "F")
        {
            $color = "red"
            $v += " Go to https://aka.ms/shubtshoot"
        }

        Write-Host -NoNewline $k -ForegroundColor $color
        Write-Host -NoNewline ": "
        Write-Host $v
    }
}
else
{
    PrintError "The account could not be created"
}
```

### <a href="" id="create-os356-ps-scripts"></a><span data-ttu-id="6b623-193">Office 365 を使ったデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="6b623-193">Create a device account using Office 365</span></span>

<span data-ttu-id="6b623-194">「[Office 365 を使ったデバイス アカウントの作成](create-a-device-account-using-office-365.md)」で説明しているとおりに、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b623-194">Creates an account as described in [Create a device account using Office 365](create-a-device-account-using-office-365.md)</span></span>

```PowerShell
# SHAccountCreateO365.ps1

$Error.Clear()
$ErrorActionPreference = "Stop"
$status = @{}

# Cleans up set state such as remote powershell sessions
function Cleanup()
{
    if ($sessExchange)
    {
        Remove-PSSession $sessExchange
    }
    if ($sessCS)
    {
        Remove-PSSession $sessCS
    }
}

function PrintError($strMsg)
{
    Write-Host $strMsg -foregroundcolor Red
}

function PrintSuccess($strMsg)
{
    Write-Host $strMsg -foregroundcolor Green
}

function PrintAction($strMsg)
{
    Write-Host $strMsg -ForegroundColor Cyan
}


# Cleans up and prints an error message
function CleanupAndFail($strMsg)
{
    if ($strMsg)
    {
        PrintError($strMsg);
    }
    Cleanup
    exit 1
}

# Exits if there is an error set and prints the given message
function ExitIfError($strMsg)
{
    if ($Error)
    {
        CleanupAndFail($strMsg);
    }
}


## Check dependencies ##
try {
    Import-Module SkypeOnlineConnector
    Import-Module MSOnline
}
catch
{
    PrintError "Some dependencies are missing"
    PrintError "Please install the Windows PowerShell Module for Lync Online. For more information go to https://www.microsoft.com/download/details.aspx?id=39366"
    PrintError "Please install the Azure Active Directory module for PowerShell from https://go.microsoft.com/fwlink/p/?linkid=236297"
    CleanupAndFail
}



## Collect account data ##
$credNewAccount = (Get-Credential -Message "Enter the desired UPN and password for this new account")
$strUpn = $credNewAccount.UserName
$strDisplayName = Read-Host "Please enter the display name you would like to use for $strUpn"
if (!$credNewAccount -Or [System.String]::IsNullOrEmpty($strDisplayName) -Or [System.String]::IsNullOrEmpty($credNewAccount.UserName) -Or $credNewAccount.Password.Length -le 0)
{
    CleanupAndFail "Please enter all of the requested data to continue."
    exit 1
}


## Sign in to remote powershell for exchange and lync online ##
$credAdmin = $null
$credAdmin=Get-Credential -Message "Enter credentials of an Exchange and Skype for Business admin"
if (!$credadmin)
{
    CleanupAndFail "Valid admin credentials are required to create and prepare the account."
}
PrintAction "Connecting to remote sessions. This can occasionally take a while - please do not enter input..."
try
{
    $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $credAdmin -AllowRedirection -Authentication basic -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -WarningAction SilentlyContinue
}
catch
{
    CleanupAndFail "Failed to connect to exchange. Please check your credentials and try again. Error message: $_"
}

try
{
    $sessCS = New-CsOnlineSession -Credential $credAdmin
}
catch
{
    CleanupAndFail "Failed to connect to Skype for Business Online Datacenter. Please check your credentials and try again. Error message: $_"
}

try
{
    Connect-MsolService -Credential $credAdmin
}
catch
{
    CleanupAndFail "Failed to connect to Azure Active Directory. Please check your credentials and try again. Error message: $_"
}

Import-PSSession $sessExchange -AllowClobber -WarningAction SilentlyContinue
Import-PSSession $sessCS -AllowClobber -WarningAction SilentlyContinue

## Create the Exchange mailbox ##
> [!Note]
> These exchange commandlets do not always throw their errors as exceptions

# Because Get-Mailbox will throw an error if the mailbox is not found
$Error.Clear()
PrintAction "Creating a new account..."
try
{
    $mailbox = $null
    $mailbox = (New-Mailbox -MicrosoftOnlineServicesID $credNewAccount.UserName -room -Name $strDisplayName -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true)
} catch { }
ExitIfError "Failed to create a new mailbox on exchange.";
$status["Mailbox Setup"] = "Successfully created a mailbox for the new account"


$strEmail = $mailbox.WindowsEmailAddress
PrintSuccess "The following mailbox has been created for this room: $strEmail"


## Create or retrieve a policy that will be applied to surface hub devices ##
# The policy disables requiring a device password so that the SurfaceHub does not need to be lockable to use Active Sync
$strPolicy = Read-Host 'Please enter the name for a new Surface Hub ActiveSync policy that will be created and applied to this account.
We will configure that policy to be compatible with Surface Hub devices.
If this script has been used before, please enter the name of the existing policy.'

$easpolicy = $null
try {
    $easpolicy = Get-MobileDeviceMailboxPolicy $strPolicy
}
catch {}

if ($easpolicy)
{
    if (!$easpolicy.PasswordEnabled -and ($easpolicy.AllowNonProvisionableDevices -eq $null -or $easpolicy.AllowNonProvisionableDevices ))
    {
        PrintSuccess "An existing policy has been found and will be applied to this account."
    }
    else
    {
        PrintError "The policy you provided is incompatible with the surface hub."
        $easpolicy = $null
        $status["ActiveSync Policy"] = "Failed to apply the EAS policy to the account because the policy was invalid."
    }
}
else
{
    $Error.Clear()
    PrintAction "Creating policy..."
    $easpolicy = New-MobileDeviceMailboxPolicy -Name $strPolicy -PasswordEnabled $false -AllowNonProvisionableDevices $true
    if ($easpolicy)
    {
        PrintSuccess "A new device policy has been created; you can use this same policy for all future Surface Hub device accounts."
    }
    else
    {
        PrintError "Could not create $strPolicy"
    }
}

if ($easpolicy)
{
    # Convert mailbox to user type so we can apply the policy (necessary)
    # Sometimes it takes a while for this change to take affect so we have some nasty retry loops
    $Error.Clear();
    try
    {
        Set-Mailbox $credNewAccount.UserName -Type Regular
    } catch {}
    if ($Error)
    {
        $Error.Clear()
        $status["Device Password Policy"] = "Failed to apply the EAS policy to the account."
        PrintError "Failed to convert to regular account"
    }
    else
    {
        # Loop until resource type goes away, up to 5 times
        for ($i = 0; $i -lt 5 -And (Get-Mailbox $credNewAccount.UserName).ResourceType; $i++)
        {
            Start-Sleep -s 5
        }
        # If the mailbox is still a Room we cannot apply the policy
        if (!((Get-Mailbox $credNewAccount.UserName).ResourceType))
        {
            $Error.Clear()
            # Set policy for account
            Set-CASMailbox $credNewAccount.UserName -ActiveSyncMailboxPolicy $strPolicy
            if (!$Error)
            {
                $status["Device Password Policy"] = "Successfully applied $strPolicy to the account"
            }
            else
            {
                $status["Device Password Policy"] = "Failed to apply the EAS policy to the account."
                PrintError "Failed to apply policy"
            }
            $Error.Clear()

            # Convert back to room mailbox
            Set-Mailbox $credNewAccount.UserName -Type Room
            # Loop until resource type goes back to room
            for ($i = 0; ($i -lt 5) -And ((Get-Mailbox $credNewAccount.UserName).ResourceType -ne "Room"); $i++)
            {
                Start-Sleep -s 5
            }
            if ((Get-Mailbox $credNewAccount.UserName).ResourceType -ne "Room")
            {
                # A failure to convert the mailbox back to a room is unfortunate but means the mailbox is unusable.
                $status["Mailbox Setup"] = "A mailbox was created but we could not set it to a room resource type."
            }
            else
            {
                Set-Mailbox $credNewAccount.UserName -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
                if ($Error)
                {
                    $status["Mailbox Setup"] = "A room mailbox was created but we could not set its password."
                }
                $Error.Clear()
            }

        }
    }
}
else
{
    $status["Device Password Policy"] = "Failed to apply the EAS policy to the account."
    PrintError "Failed to obtain policy"
}
PrintSuccess "Account creation completed."

PrintAction "Setting calendar processing rules..."

$Error.Clear();
## Prepare the calendar for automatic meeting responses ##
try {
    Set-CalendarProcessing -Identity $credNewAccount.UserName -AutomateProcessing AutoAccept
} catch { }
if ($Error)
{
    $status["Calendar Acceptance"] = "Failed to configure the account to automatically accept/decline meeting requests"
}
else
{
    $status["Calendar Acceptance"] = "Successfully configured the account to automatically accept/decline meeting requests"
}


$Error.Clear()
try {
    Set-CalendarProcessing -Identity $credNewAccount.UserName -RemovePrivateProperty $false -AddOrganizerToSubject $false -AddAdditionalResponse $true -DeleteSubject $false -DeleteComments $false -AdditionalResponse "This is a Surface Hub room!"
} catch { }
if ($Error)
{
    $status["Calendar Response Configuration"] = "Failed to configure the account's response properties"
}
else
{
    $status["Calendar Response Configuration"] = "Successfully configured the account's response properties"
}

$Error.Clear()
## Configure the Account to not expire ##
PrintAction "Configuring password not to expire..."
try
{
    Set-MsolUser -UserPrincipalName $credNewAccount.UserName -PasswordNeverExpires $true
}
catch
{

}

if ($Error)
{
    $status["Password Expiration Policy"] = "Failed to set the password to never expire"
}
else
{
    $status["Password Expiration Policy"] = "Successfully set the password to never expire"
}

PrintSuccess "Completed Exchange configuration"

## Setup Skype for Business. This is somewhat optional and if it fails we SfbEnable can be used later ##
PrintAction "Configuring account for Skype for Business."

# Getting registrar pool
$strRegPool = $null
try {
    $strRegPool = (Get-CsTenant).TenantPoolExtension
}
catch {}
$Error.Clear()
if (![System.String]::IsNullOrEmpty($strRegPool))
{
    $strRegPool = $strRegPool.Substring($strRegPool[0].IndexOf(':') + 1)
}
<#
$strRegPoolEntry = Read-Host "Enter a Skype for Business Registrar Pool, or leave blank to use [$strRegPool]"
if (![System.String]::IsNullOrEmpty($strRegPoolEntry))
{
    $strRegPool = $strRegPoolEntry
}
#>

# Try to SfB-enable the account. Note that it may not work right away as the account needs to propagate to active directory
PrintAction "Enabling Skype for Business on $strRegPool"
Start-Sleep -s 10
$Error.Clear()
try {
    Enable-CsMeetingRoom -Identity $credNewAccount.UserName -RegistrarPool $strRegPool -SipAddressType EmailAddress
}
catch { }

if ($Error)
{
    $status["Skype for Business Account Setup"] = "Failed to setup the Skype for Business meeting room - you can run EnableSfb.ps1 to try again."
    $Error.Clear();
}
else
{
    $status["Skype for Business Account Setup"] = "Successfully enabled account as a Skype for Business meeting room"
}

## Now we need to assign a Skype for Business license to the account ##
# Assign a license to thes
$countryCode = (Get-CsTenant).CountryAbbreviation
$loc = Read-Host "Please enter the usage location for this device account (where the account is being used). This is a 2-character code that is used to assign licenses (e.g. $countryCode)"
try {
    $Error.Clear()
    Set-MsolUser -UserPrincipalName $credNewAccount.UserName -UsageLocation $loc
}
catch{}
if ($Error)
{
    $status["Office 365 License"] = "Failed to assign an Office 365 license to the account"
    $Error.Clear()
}
else
{
    PrintAction "We found the following licenses available for your tenant:"
    $skus = (Get-MsolAccountSku | Where-Object { !$_.AccountSkuID.Contains("INTUNE"); })
    $i = 1
    $skus | % {
     Write-Host -NoNewline $i
     Write-Host -NoNewLine ": AccountSKUID: "
     Write-Host -NoNewLine $_.AccountSkuid
     Write-Host -NoNewLine " Active Units: "
     Write-Host -NoNewLine $_.ActiveUnits
     Write-Host -NoNewLine " Consumed Units: "
     Write-Host $_.ConsumedUnits
     $i++
    }
    $iLicenseIndex = 0;
    do
    {
        $iLicenseIndex = Read-Host 'Choose the number for the SKU you want to pick'
    } while ($iLicenseIndex -lt 1 -or $iLicenseIndex -gt $skus.Length)
    $strLicenses = $skus[$iLicenseIndex - 1].AccountSkuId

    if (![System.String]::IsNullOrEmpty($strLicenses))
    {
        try
        {
            $Error.Clear()
            Set-MsolUserLicense -UserPrincipalName $credNewAccount.UserName -AddLicenses $strLicenses
        }
        catch
        {

        }
        if ($Error)
        {
            $Error.Clear()
            $status["Office 365 License"] = "Failed to add a license to the account. Make sure you have remaining licenses."
        }
        else
        {
            $status["Office 365 License"] = "Successfully added license to the account"
        }
    }
    else
    {
        $status["Office 365 License"] = "You opted not to install a license on this account"
    }
}


Write-Host

## Cleanup and print results ##
Cleanup
$strDisplay = $mailbox.DisplayName
$strUsr = $credNewAccount.UserName
PrintAction "Summary for creation of $strUsr ($strDisplay)"
if ($status.Count -gt 0)
{
    ForEach($k in $status.Keys)
    {
        $v = $status[$k]
        $color = "yellow"
        if ($v[0] -eq "S") { $color = "green" }
        elseif ($v[0] -eq "F")
        {
            $color = "red"
            $v += " Go to https://aka.ms/shubtshoot for help"
        }

        Write-Host -NoNewline $k -ForegroundColor $color
        Write-Host -NoNewline ": "
        Write-Host $v
    }
}
else
{
    PrintError "The account could not be created"
}
```

## <a href="" id="acct-verification-ps-scripts"></a><span data-ttu-id="6b623-195">アカウント検証スクリプト</span><span class="sxs-lookup"><span data-stu-id="6b623-195">Account verification script</span></span>

<span data-ttu-id="6b623-196">このスクリプトを実行すると、以前に作成した Surface Hub のデバイス アカウントが、作成時に使った方法に関係なく検証されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-196">This script will validate the previously-created device account on a Surface Hub, no matter which method was used to create it.</span></span> <span data-ttu-id="6b623-197">このスクリプトは、基本的に合格/不合格方式です。</span><span class="sxs-lookup"><span data-stu-id="6b623-197">This script is basically pass/fail.</span></span> <span data-ttu-id="6b623-198">いずれかのテスト エラーが発生すると詳細なエラー メッセージが表示されますが、すべてのテストに合格すると、最終的な結果は要約レポートになります。</span><span class="sxs-lookup"><span data-stu-id="6b623-198">If one of the test errors out, it will show a detailed error message, but if all tests pass, the end result will be a summary report.</span></span> <span data-ttu-id="6b623-199">たとえば、次のような結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-199">For example, you might see:</span></span>

``` syntax
15 tests executed
0 failures
2 warnings
15 passed
```

<span data-ttu-id="6b623-200">具体的な設定の詳細は表示されません。</span><span class="sxs-lookup"><span data-stu-id="6b623-200">Details of specific settings will not be shown.</span></span>

```PowerShell
# SHAccountValidate.ps1

$Error.Clear()
$ErrorActionPreference = "Stop"


# Cleans up set state such as remote powershell sessions
function Cleanup()
{
    if ($sessEx)
    {
        Remove-PSSession $sessEx
    }
    if ($sessSfb)
    {
        Remove-PSSession $sessSfb
    }
}

function PrintError($strMsg)
{
    Write-Host $strMsg -foregroundcolor "red"
}

function PrintSuccess($strMsg)
{
    Write-Host $strMsg -foregroundcolor "green"
}

function PrintAction($strMsg)
{
    Write-Host $strMsg -ForegroundColor Cyan
}


# Cleans up and prints an error message
function CleanupAndFail($strMsg)
{
    if ($strMsg)
    {
        PrintError($strMsg);
    }
    Cleanup
    exit 1
}

# Exits if there is an error set and prints the given message
function ExitIfError($strMsg)
{
    if ($Error)
    {
        CleanupAndFail($strMsg);
    }
}

$strUpn = Read-Host "What is the email address of the account you wish to validate?"
if (!$strUpn.Contains('@'))
{
    CleanupAndFail "$strUpn is not a valid email address"
}
$strExServer = Read-Host "What is your exchange server? (leave blank for online tenants)"
if ($strExServer.Equals(""))
{
    $fExIsOnline = $true
}
else
{
    $fExIsOnline = $false
}
$credEx = Get-Credential -Message "Please provide exchange user credentials"

$strRegistrarPool = Read-Host ("What is the Skype for Business registrar pool for $strUpn" + "? (leave blank for online tenants)")
$fSfbIsOnline = $strRegistrarPool.Equals("")

$fHasOnPrem = $true
if ($fSfbIsOnline -and $fExIsOnline)
{
    do
    {
        $strHasOnPrem = (Read-Host "Do you have an on-premises Active Directory (Y/N) (No if your domain services are hosted entirely online)").ToUpper()
    } while ($strHasOnPrem -ne "Y" -and $strHasOnPrem -ne "N")
    $fHasOnPrem = $strHasOnPrem.Equals("Y")
}

$fHasOnline = $false
if ($fSfbIsOnline -or $fExIsOnline)
{
    $fHasOnline = $true
}

if ($fSfbIsOnline)
{
    try {
        Import-Module SkypeOnlineConnector
    }
    catch
    {
        CleanupAndFail "To verify Skype for Business in online tenants you need the Lync Online Connector module from https://www.microsoft.com/download/details.aspx?id=39366"
    }
}
else
{
    $credSfb = (Get-Credential -Message "Please enter Skype for Business admin credentials")
}

if ($fHasOnline)
{
    $credSfb = $credEx
    try {
        Import-Module MSOnline
    }
    catch
    {
        CleanupAndFail "To verify accounts in online tenants you need the Azure Active Directory module for PowerShell from https://go.microsoft.com/fwlink/p/?linkid=236297"
    }
}

PrintAction "Connecting to Exchange Powershell Session..."
[System.Management.Automation.Runspaces.AuthenticationMechanism] $authType = [System.Management.Automation.Runspaces.AuthenticationMechanism]::Kerberos
if ($fExIsOnline)
{
    $authType = [System.Management.Automation.Runspaces.AuthenticationMechanism]::Basic
}
try
{
    $sessEx = $null
    if ($fExIsOnline)
    {
        $sessEx = New-PSSession -ConfigurationName microsoft.exchange -Credential $credEx -AllowRedirection -Authentication $authType -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -WarningAction SilentlyContinue
    }
    else
    {
        $sessEx = New-PSSession -ConfigurationName microsoft.exchange -Credential $credEx -AllowRedirection -Authentication $authType -ConnectionUri https://$strExServer/powershell -WarningAction SilentlyContinue
    }
}
catch
{
}

if (!$sessEx)
{
    CleanupAndFail "Connecting to Exchange Powershell failed, please validate your server is accessible and credentials are correct"
}

PrintSuccess "Connected to Exchange Powershell Session"

PrintAction "Connecting to Skype for Business Powershell Session..."

if ($fSfbIsOnline)
{
    $sessSfb = New-CsOnlineSession -Credential $credSfb
}
else
{
    $sessSfb = New-PSSession -Credential $credSfb -ConnectionURI "https://$strRegistrarPool/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
}

if (!$sessSfb)
{
    CleanupAndFail "Connecting to Skype for Business Powershell failed, please validate your server is accessible and credentials are correct"
}

PrintSuccess "Connected to Skype for Business Powershell"

if ($fHasOnline)
{
    $credMsol = $null
    if ($fExIsOnline)
    {
        $credMsol = $credEx
    }
    elseif ($fSfbIsOnline)
    {
        $credMsol = $credSfb
    }
    else
    {
        CleanupAndFail "Internal error - could not determine MS Online credentials"
    }
    try
    {
        PrintAction "Connecting to Azure Active Directory Services..."
        Connect-MsolService -Credential $credMsol
        PrintSuccess "Connected to Azure Active Directory Services"
    }
    catch
    {
        # This really shouldn't happen unless there is a network error
        CleanupAndFail "Failed to connect to MSOnline"
    }
}


PrintAction "Importing remote sessions into the local session..."
try
{
    $importEx = Import-PSSession $sessEx -AllowClobber -WarningAction SilentlyContinue -DisableNameChecking
    $importSfb = Import-PSSession $sessSfb -AllowClobber -WarningAction SilentlyContinue -DisableNameChecking
}
catch
{
}
if (!$importEx -or !$importSfb)
{
    CleanupAndFail "Import failed"
}
PrintSuccess "Import successful"


$mailbox = $null
try
{
    $mailbox = Get-Mailbox -Identity $strUpn
}
catch
{
}

if (!$mailbox)
{
    CleanupAndFail "Account exists check failed. Unable to find the mailbox for $strUpn - please make sure the Exchange account exists on $strExServer"
}

$exchange = $null
if (!$fExIsOnline)
{
    $exchange = Get-ExchangeServer
    if (!$exchange -or !$exchange.IsE14OrLater)
    {
        CleanupAndFail "A compatible exchange server version was not found. Please use at least exchange 2010."
    }
}


$strAlias = $mailbox.UserPrincipalName
$strDisplayName = $mailbox.DisplayName

$strLinkedAccount = $strLinkedDomain = $strLinkedUser = $strLinkedServer = $null
$credLinkedDomain = $Null
if (!$fExIsOnline -and ![System.String]::IsNullOrEmpty($mailbox.LinkedMasterAccount) -and !$mailbox.LinkedMasterAccount.EndsWith("\SELF"))
{
    $strLinkedAccount = $mailbox.LinkedMasterAccount
    $strLinkedDomain = $strLinkedAccount.substring(0,$strLinkedAccount.IndexOf('\'))
    $strLinkedUser = $strLinkedAccount.substring($strLinkedAccount.IndexOf('\') + 1)
    $strLinkedServer = Read-Host "What is the domain controller for the $strLinkedDomain"
    $credLinkedDomain = (Get-Credential -Message "Please provide credentials for $strLinkedDomain")
}







Write-Host
Write-Host
Write-Host
PrintAction "Performing verification checks on $strDisplayName..."
$Global:iTotalFailures = 0
$global:iTotalWarnings = 0
$Global:iTotalPasses = 0

function Validate()
{
    Param(
        [string]$Test,
        [bool]  $Condition,
        [string]$FailureMsg,
        [switch]$WarningOnly
    )

    Write-Host -NoNewline -ForegroundColor White $Test.PadRight(100,'.')
    if ($Condition)
    {
        Write-Host -ForegroundColor Green "Passed"
        $global:iTotalPasses++
    }
    else
    {
        if ($WarningOnly)
        {
            Write-Host -ForegroundColor Yellow ("Warning: "+$FailureMsg)
            $global:iTotalWarnings++
        }
        else
        {
            Write-Host -ForegroundColor Red ("Failed: "+$FailureMsg)
            $global:iTotalFailures++
        }
    }
}

## Exchange ##

Validate -WarningOnly -Test "The mailbox $strUpn is enabled as a room account" -Condition ($mailbox.RoomMailboxAccountEnabled -eq $True) -FailureMsg "RoomMailboxEnabled - without a device account, the Surface Hub will not be able to use various key features."
$calendarProcessing = Get-CalendarProcessing -Identity $strUpn -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
Validate -Test "The mailbox $strUpn is configured to accept meeting requests" -Condition ($calendarProcessing -ne $null -and $calendarProcessing.AutomateProcessing -eq 'AutoAccept') -FailureMsg "AutomateProcessing - the Surface Hub will not be able to send mail or sync its calendar."
Validate -WarningOnly -Test "The mailbox $strUpn will not delete meeting comments" -Condition ($calendarProcessing -ne $null -and !$calendarProcessing.DeleteComments) -FailureMsg "DeleteComments - the Surface Hub may be missing some meeting information on the welcome screen and Skype."
Validate -WarningOnly -Test "The mailbox $strUpn keeps private meetings private" -Condition ($calendarProcessing -ne $null -and !$calendarProcessing.RemovePrivateProperty) -FailureMsg "RemovePrivateProperty - the Surface Hub will make show private meetings."
Validate -Test "The mailbox $strUpn keeps meeting subjects" -Condition ($calendarProcessing -ne $null -and !$calendarProcessing.DeleteSubject) -FailureMsg "DeleteSubject - the Surface Hub will not keep meeting subject information."
Validate -WarningOnly -Test "The mailbox $strUpn does not prepend meeting organizers to subjects" -Condition ($calendarProcessing -ne $null -and !$calendarProcessing.AddOrganizerToSubject) -FailureMsg "AddOrganizerToSubject - the Surface Hub will not display meeting subjects as intended."

if ($fExIsOnline)
{
    #No online specifics
}
else
{
    #No onprem specifics
}

#ActiveSync
$casMailbox = Get-Casmailbox $strUpn -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
Validate -Test "The mailbox $strUpn has a mailbox policy" -Condition ($casMailbox -ne $null) -FailureMsg "PasswordEnabled - unable to find policy - the Surface Hub will not be able to send mail or sync its calendar."
if ($casMailbox)
{
    $policy = $null
    if ($fExIsOnline -or $exchange.IsE15OrLater)
    {
        $strPolicy = $casMailbox.ActiveSyncMailboxPolicy
        $policy = Get-MobileDeviceMailboxPolicy -Identity $strPolicy -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
        Validate -Test "The policy $strPolicy does not require a device password" -Condition ($policy.PasswordEnabled -ne $True) -FailureMsg "PasswordEnabled - policy requires a device password - the Surface Hub will not be able to send mail or sync its calendar."
    }
    else
    {
        $strPolicy = $casMailbox.ActiveSyncMailboxPolicy
        $policy = Get-ActiveSyncMailboxPolicy -Identity $strPolicy -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
        Validate -Test "The policy $strPolicy does not require a device password" -Condition ($policy.PasswordEnabled -ne $True) -FailureMsg "PasswordEnabled - policy requires a device password - the Surface Hub will not be able to send mail or sync its calendar."
    }

    if ($policy -ne $null)
    {
        Validate -Test "The policy $strPolicy allows non-provisionable devices" -Condition ($policy.AllowNonProvisionableDevices -eq $null -or $policy.AllowNonProvisionableDevices -eq $true) -FailureMsg "AllowNonProvisionableDevices - policy will not allow the SurfaceHub to sync"
    }

}


# Check the default access level
$orgSettings = Get-ActiveSyncOrganizationSettings
$strDefaultAccessLevel = $orgSettings.DefaultAccessLevel
Validate -Test "ActiveSync devices are allowed" -Condition ($strDefaultAccessLevel -eq 'Allow') -FailureMsg "DeviceType Windows Mail is accessible - devices are not allowed by default - the surface hub will not be able to send mail or sync its calendar."

# Check if there exists a device access rule that bans the device type Windows Mail
$blockingRules = Get-ActiveSyncDeviceAccessRule | where {($_.AccessLevel -eq 'Block' -or $_.AccessLevel -eq 'Quarantine') -and $_.Characteristic -eq 'DeviceType'-and $_.QueryString -eq 'WindowsMail'}
Validate -Test "Windows mail devices are not blocked or quarantined" -Condition ($blockingRules -eq $null -or $blockingRules.Length -eq 0) -FailureMsg "DeviceType Windows Mail is accessible - devices are blocked or quarantined - the surface hub will not be able to send mail or sync its calendar."

## End Exchange ##



## SfB ##
$strLyncIdentity = $null
if ($fSfbIsOnline)
{
    $strLyncIdentity = $strUpn
}
else
{
    $strLyncIdentity = $strAlias
}

$lyncAccount = $null
try {
    $lyncAccount = Get-CsMeetingRoom -Identity $strLyncIdentity -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
} catch {
    try {
        $lyncAccount = Get-CsUser -Identity $strLyncIdentity -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
    } catch { }
}
Validate -Test "There is a Lync or Skype for Business account for $strLyncIdentity" -Condition ($lyncAccount -ne $null -and $lyncAccount.Enabled) -FailureMsg "SfB Enabled - there is no Skype for Business account - meetings will not support Skype for Business"
if ($lyncAccount)
{
    Validate -Test "The meeting room has a SIP address" -Condition (![System.String]::IsNullOrEmpty($lyncAccount.SipAddress)) -FailureMsg "SfB Enabled - there is no SIP Address - the device account cannot be used to sign into Skype for Business."
}
## End SFB ##


if ($fHasOnline)
{
    #License validation and password expiry
    $accountOnline = Get-MsolUser -UserPrincipalName $strUpn -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
    Validate -Test "There is an online user account for $strUpn" -Condition ($accountOnline -ne $null) -FailureMsg "Could not find a Microsoft Online account for this user even though some services are online"
    if ($accountOnline)
    {
        Validate -Test "The password for $strUpn will not expire" -Condition ($accountOnline.PasswordNeverExpires -eq $True) -FailureMsg "PasswordNeverExpires - the admin will need to update the device account's password on the Surface Hub when it expires."
        if ($fIsSfbOnline -and !$fIsExOnline)
        {
            $strLicenseFailureMsg = "Has O365 license - The devices will not be able to use Skype for Business services."
        }
        elseif ($fIsExOnline -and !$fIsSfbOnline)
        {
            $strLicenseFailureMsg = "Has O365 license - The devices will not be able to use Exchange Online services."
        }
        else
        {
            $strLicenseFailureMsg = "Has O365 license - The devices will not be able to use Skype for Business or Exchange Online services."
        }
        Validate -Test "$strUpn is licensed" -Condition ($accountOnline.IsLicensed -eq $True) -FailureMsg $strLicenseFailureMsg

        Validate -Test "$strUpn is allowed to sign in" -Condition ($accountOnline.BlockCredential -ne $True) -FailureMsg "BlockCredential - This user is not allowed to sign in."
    }
}

#If there is an on-prem component, we can get the authoritative AD user from mailbox
if ($fHasOnPrem)
{
    $accountOnPrem = $null
    if ($strLinkedAccount)
    {
        $accountOnPrem = Get-AdUser $strLinkedUser -server $strLinkedServer -credential $credLinkedDomain -properties PasswordNeverExpires -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
    }
    else
    {
        #AD User enabled validation
        $accountOnPrem = Get-AdUser $mailbox.UserPrincipalName -properties PasswordNeverExpires -WarningAction SilentlyContinue -ErrorAction SilentlyContinue
    }
    $strOnPremUpn = $accountOnPrem.UserPrincipalName
    Validate -Test "There is a user account for $strOnPremUpn" -Condition ($accountOnprem -ne $null) -FailureMsg "Could not find an Active Directory account for this user"
    if ($accountOnPrem)
    {
        Validate -WarningOnly -Test "The password for $strOnPremUpn will not expire" -Condition ($accountOnprem.PasswordNeverExpires -eq $True) -FailureMsg "PasswordNeverExpires - the admin will need to update the device account's password on the Surface Hub when it expires."
        Validate -Test "$strOnPremUpn is enabled" -Condition $accountOnPrem.Enabled -FailureMsg "AccountEnabled - this device account will not sign in"
    }
}


$global:iTotalTests = ($global:iTotalFailures + $global:iTotalPasses + $global:iTotalWarnings)

Write-Host -NoNewline $global:iTotalTests "tests executed: "
Write-Host -NoNewline -ForegroundColor Red $Global:iTotalFailures "failures "
Write-Host -NoNewline -ForegroundColor Yellow $Global:iTotalWarnings "warnings "
Write-Host -ForegroundColor Green $Global:iTotalPasses "passes "

Cleanup
```

## <a href="" id="enable-sfb-ps-scripts"></a><span data-ttu-id="6b623-201">Skype for Business の有効化</span><span class="sxs-lookup"><span data-stu-id="6b623-201">Enable Skype for Business</span></span>

<span data-ttu-id="6b623-202">このスクリプトを実行すると、デバイス アカウントで Skype for Business が有効になります。</span><span class="sxs-lookup"><span data-stu-id="6b623-202">This script will enable Skype for Business on a device account.</span></span> <span data-ttu-id="6b623-203">アカウントの作成時にまだ Skype for Business が有効になっていなかった場合にのみ、このスクリプトを使います。</span><span class="sxs-lookup"><span data-stu-id="6b623-203">Use it only if Skype for Business wasn't previously enabled during account creation.</span></span>

```PowerShell
## This script performs only the Enable for Skype for Business step on an account. It should only be run if this step failed in SHAccountCreate and the other steps have been completed ##
# EnableSfb.ps1

$Error.Clear()
$ErrorActionPreference = "Stop"

# Cleans up set state such as remote powershell sessions
function Cleanup()
{
    if ($sessCS)
    {
        Remove-PSSession $sessCS
    }
}

function PrintError($strMsg)
{
    Write-Host $strMsg -foregroundcolor "red"
}

function PrintSuccess($strMsg)
{
    Write-Host $strMsg -foregroundcolor "green"
}

# Cleans up and prints an error message
function CleanupAndFail($strMsg)
{
    if ($strMsg)
    {
        PrintError($strMsg);
    }
    Cleanup
    exit 1
}

# Exits if there is an error set and prints the given message
function ExitIfError($strMsg)
{
    if ($Error)
    {
        CleanupAndFail($strMsg);
    }
}

## Check dependencies ##

$input = Read-Host "Is the account you wish to enable part of an online environment (enter O) or on-premises environment (enter P)"
if ($input -eq "P")
{
    $online = $false
}
elseif ($input -eq "O")
{
    $online = $true
}
else
{
    CleanupAndFail "Invalid selection"
}
if ($online)
{
    try {
        Import-Module SkypeOnlineConnector
    }
    catch
    {
        PrintError "Some dependencies are missing"
        PrintError "Please install the Windows PowerShell Module for Lync Online. For more information go to https://www.microsoft.com/download/details.aspx?id=39366"
        PrintError "Please install the Azure Active Directory module for PowerShell from https://go.microsoft.com/fwlink/p/?linkid=236297"
        CleanupAndFail
    }
}
else
{
    $strRegPool = Read-Host "Enter the FQDN of your Skype for Business Registrar Pool"
}


## Collect account data ##
Write-Host "-----------  Enter info for the account to enable  -----------." -foregroundcolor "magenta"
$strRoomUri=Read-Host 'Please enter the UPN of the account you are enabling (e.g. confroom@surfacehub.microsoft.com)'

if ([System.String]::IsNullOrEmpty($strRoomUri))
{
    CleanupAndFail "Please enter all of the requested data to continue."
    exit 1
}
Write-Host "--------------------------------------------------------------." -foregroundcolor "magenta"



## Sign in to remote powershell for exchange and lync online ##
Write-Host "`n------------------  Establishing connection  -----------------." -foregroundcolor "magenta"
$credAdmin=Get-Credential -Message "Enter credentials of a Skype for Business admin"
if (!$credadmin)
{
    CleanupAndFail("Valid admin credentials are required to create and prepare the account.");
}
Write-Host "Connecting to remote sessions. This can occasionally take a while - please do not enter input..."

try
{
    if ($online)
    {
        $sessCS = New-CsOnlineSession -Credential $credAdmin
    }
    else
    {
        $sessCS = New-PSSession -Credential $credAdmin -ConnectionURI "https://$strRegPool/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
    }
}
catch
{
    CleanupAndFail("Failed to connect to Skype for Business server. Please check your credentials and try again. Error message: $_")
}

Import-PSSession $sessCS -AllowClobber


Write-Host "--------------------------------------------------------------." -foregroundcolor "magenta"

# Getting registrar pool
if ($online)
{
    try {
        $strRegPool = $null;
        $strRegPool = (Get-CsTenant).RegistrarPool
    } catch {}
    if ($Error)
    {
        $Error.Clear();
        $strRegPool = "";
        Write-Host "We failed to lookup your Skype for Business Registrar Pool, but you can still enter it manually"
    }
    else
    {
        $strRegPool = $strRegPool[0].Substring($strRegPool[0].IndexOf(':') + 1)
    }
}


$Error.Clear()
try {
    Enable-CsMeetingRoom -Identity $strRoomUri -RegistrarPool $strRegPool -SipAddressType EmailAddress
}
catch {}

ExitIfError("Failed to setup Skype for Business meeting room")

PrintSuccess "Successfully enabled $strRoomUri as a Skype for Business meeting room"

Cleanup
```

## <span data-ttu-id="6b623-204">便利なコマンドレット</span><span class="sxs-lookup"><span data-stu-id="6b623-204">Useful cmdlets</span></span>

### <a href="" id="create-compatible-as-policy"></a><span data-ttu-id="6b623-205">Surface Hub と互換性のある ActiveSync ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="6b623-205">Creating a Surface Hub-compatible ActiveSync policy</span></span>

<span data-ttu-id="6b623-206">Surface Hub で Exchange サービスを使うには、互換性のある ActiveSync ポリシーで構成したデバイス アカウントを、デバイスにプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-206">For Surface Hub to use Exchange services, a device account configured with a compatible ActiveSync policy must be provisioned on the device.</span></span> <span data-ttu-id="6b623-207">このポリシーには、</span><span class="sxs-lookup"><span data-stu-id="6b623-207">This policy has the following requirements:</span></span>

``` syntax
PasswordEnabled == 0
```

<span data-ttu-id="6b623-208">次のコマンドレットでは、 `$strPolicy` は ActiveSync ポリシーの名前であり、 `$strRoomUpn` は、ポリシーを適用するデバイス アカウントの UPN です。</span><span class="sxs-lookup"><span data-stu-id="6b623-208">In the following cmdlets, `$strPolicy` is the name of the ActiveSync policy, and `$strRoomUpn` is the UPN of the device account you want to apply the policy to.</span></span>

<span data-ttu-id="6b623-209">コマンドレットを実行するには、リモート PowerShell セッションを確立し、次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-209">Note that in order to run the cmdlets, you need to set up a remote PowerShell session and:</span></span>

-   <span data-ttu-id="6b623-210">管理者アカウントがリモート PowerShell に対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-210">Your admin account must be remote-PowerShell-enabled.</span></span> <span data-ttu-id="6b623-211">これにより、スクリプトに必要な PowerShell コマンドレットを管理者が使用できます </span><span class="sxs-lookup"><span data-stu-id="6b623-211">This allows the admin to use the PowerShell cmdlets that are needed by the script.</span></span> <span data-ttu-id="6b623-212">(このアクセス許可を設定するには `set-user $admin -RemotePowerShellEnabled $true` を使用できます)。</span><span class="sxs-lookup"><span data-stu-id="6b623-212">(This permission can be set using `set-user $admin -RemotePowerShellEnabled $true`)</span></span>
-   <span data-ttu-id="6b623-213">作成スクリプトの実行を計画している場合は、管理者アカウントに "Reset Password/パスワードのリセット" 役割が必要です。</span><span class="sxs-lookup"><span data-stu-id="6b623-213">Your admin account must have the "Reset Password" role if you plan to run the creation scripts.</span></span> <span data-ttu-id="6b623-214">これにより、管理者がアカウントのパスワードを変更できます。この操作はスクリプトに必要です。</span><span class="sxs-lookup"><span data-stu-id="6b623-214">This allows the admin to change the password of the account, which is needed for the script.</span></span> <span data-ttu-id="6b623-215">"Reset Password/パスワードのリセット" 役割を有効にするには、Exchange 管理センターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b623-215">The Reset Password Role can be enabled using the Exchange Admin Center.</span></span>

<span data-ttu-id="6b623-216">ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b623-216">Create the policy.</span></span>

```PowerShell
# Create new policy with PasswordEnabled == false
New-MobileDeviceMailboxPolicy -Name $strPolicy -PasswordEnabled $false –AllowNonProvisionableDevices $true
```

<span data-ttu-id="6b623-217">ポリシーを適用するには、メールボックスの種類を会議室にすることはできないため、最初にメールボックスをユーザーに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-217">To apply the policy, the mailbox cannot be a room type, so it has to be converted into a user first.</span></span>

```PowerShell
# Convert user to regular type
Set-Mailbox $strRoomUpn -Type Regular
# Set policy for account
Set-CASMailbox $strRoomUpn -ActiveSyncMailboxPolicy $strPolicy
```

<span data-ttu-id="6b623-218">これで、必要な作業は、デバイス アカウントを変換して種類を会議室に戻すことだけになります。</span><span class="sxs-lookup"><span data-stu-id="6b623-218">Now the device account just needs to be converted back into a room type.</span></span>

```PowerShell
# Convert back to room mailbox
Set-Mailbox $strRoomUpn -Type Room
```

### <a href="" id="whitelisting-device-ids-cmdlet"></a><span data-ttu-id="6b623-219">ActiveSync に対するデバイス ID の許可</span><span class="sxs-lookup"><span data-stu-id="6b623-219">Allowing device IDs for ActiveSync</span></span>

<span data-ttu-id="6b623-220">アカウント `$strRoomUpn` を許可するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6b623-220">To allow an account `$strRoomUpn`, run the following command:</span></span>

```PowerShell
Set-CASMailbox –Identity $strRoomUpn –ActiveSyncAllowedDeviceIDs “<ID>”
```

<span data-ttu-id="6b623-221">デバイスの ID を検索するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6b623-221">To find a device's ID, run:</span></span>

```PowerShell
Get-ActiveSyncDevice -Mailbox $strRoomUpn
```

<span data-ttu-id="6b623-222">このコマンドを実行すると、`DeviceId` プロパティなど、アカウントのプロビジョニング先となっているすべてのデバイスのデバイス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-222">This retrieves device information for every device that the account has been provisioned on, Including the `DeviceId` property.</span></span>

### <a href="" id="auto-accept-meetings-cmdlet"></a><span data-ttu-id="6b623-223">会議出席依頼の自動的な承諾と辞退</span><span class="sxs-lookup"><span data-stu-id="6b623-223">Auto-accepting and declining meeting requests</span></span>

<span data-ttu-id="6b623-224">デバイス アカウントで、空き時間に基づいて会議出席依頼を自動的に承諾または辞退するには、**AutomateProcessing** 属性を **AutoAccept** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-224">For a device account to automatically accept or decline meeting requests based on its availability, the **AutomateProcessing** attribute must be set to **AutoAccept**.</span></span> <span data-ttu-id="6b623-225">これは、会議の重複を防ぐために推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="6b623-225">This is recommended as to prevent overlapping meetings.</span></span>

```PowerShell
Set-CalendarProcessing $strRoomUpn -AutomateProcessing AutoAccept
```

### <a href="" id="accept-ext-meetings-cmdlet"></a><span data-ttu-id="6b623-226">外部会議出席依頼の承諾</span><span class="sxs-lookup"><span data-stu-id="6b623-226">Accepting external meeting requests</span></span>

<span data-ttu-id="6b623-227">デバイス アカウントで外部会議出席依頼 (同じテナント/ドメイン名にないアカウントからの会議出席依頼) を承諾するには、そのデバイス アカウントが、外部会議出席依頼の処理を許可するように設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b623-227">For a device account to accept external meeting requests (a meeting request from an account not in the same tenant/domain), the device account must be set to allow processing of external meeting requests.</span></span> <span data-ttu-id="6b623-228">設定すると、外部アカウントからの会議出席依頼とローカル アカウントからの会議出席依頼が、デバイス アカウントで自動的に承諾または辞退されます。</span><span class="sxs-lookup"><span data-stu-id="6b623-228">Once set, the device account will automatically accept or decline meeting requests from external accounts as well as local accounts.</span></span>

> [!Note]
> <span data-ttu-id="6b623-229">**オートマトン Eprocessing**属性が**autoaccept**に設定されていない場合、この設定を行っても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="6b623-229">If the **AutomateProcessing** attribute is not set to **AutoAccept**, then setting this will have no effect.</span></span>

```PowerShell
Set-CalendarProcessing $strRoomUpn -ProcessExternalMeetingMessages $true
```
