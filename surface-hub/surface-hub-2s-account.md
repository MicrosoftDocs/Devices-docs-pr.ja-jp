---
title: Surface Hub 2S デバイス アカウントの作成
description: このページでは、Surface Hub 2S デバイス アカウントを作成する手順について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 76ac960be2ab30a30b4e29618f350a13a284f52a
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312023"
---
# <span data-ttu-id="f72d5-104">Surface Hub 2S デバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="f72d5-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="f72d5-105">Surface Hub デバイス アカウント (会議室メールボックスとも呼ばれる) を作成すると、Surface Hub 2S は会議出席依頼を受信、承認、または辞退し、会議に参加できます。</span><span class="sxs-lookup"><span data-stu-id="f72d5-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings.</span></span> <span data-ttu-id="f72d5-106">Out-of-Box Experience (OOBE) のセットアップ中にデバイス アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="f72d5-107">必要に応じて、後で変更できます (OOBE セットアップは行わずに行います)。</span><span class="sxs-lookup"><span data-stu-id="f72d5-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="f72d5-108">Microsoft 365 管理センターからアカウントを作成するには、次の方法Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f72d5-108">You can create the account from  Microsoft 365 Admin center in combination with Windows PowerShell:</span></span> 

- <span data-ttu-id="f72d5-109">**管理センターからアカウントを作成します**。</span><span class="sxs-lookup"><span data-stu-id="f72d5-109">**Create account via Admin center**.</span></span> <span data-ttu-id="f72d5-110">最小要件を満たすために、アカウントに必要なすべてを [Microsoft 365 管理センターから直接構成できます](https://admin.microsoft.com/AdminPortal)。</span><span class="sxs-lookup"><span data-stu-id="f72d5-110">To meet minimum requirements, you can configure everything you need for the account directly from the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal).</span></span> <span data-ttu-id="f72d5-111">ホワイトボード アプリからホワイトボードを直接共有する場合など、一部の機能では PowerShell を使用して ActiveSync を構成する必要があります。この [ページでメール アプリの使用が必要な場合は、「ActiveSync](#enable-activesync-if-use-of-email-app-is-required) を有効にする」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f72d5-111">Some features like sharing whiteboards directly from the whiteboard app require using PowerShell to configure ActiveSync; see [Enable ActiveSync if use of email app is required](#enable-activesync-if-use-of-email-app-is-required) on this page.</span></span>

- <span data-ttu-id="f72d5-112">**PowerShell を使用してアカウントを作成します**。</span><span class="sxs-lookup"><span data-stu-id="f72d5-112">**Create account via PowerShell**.</span></span> <span data-ttu-id="f72d5-113">PowerShell スクリプトを使用すると、複数のデバイス アカウントの作成を容易にし、次に示す特定の機能をすばやく構成できます。</span><span class="sxs-lookup"><span data-stu-id="f72d5-113">You can use PowerShell scripts to facilitate creation of multiple device accounts and quickly configure specific features including:</span></span>
    - <span data-ttu-id="f72d5-114">すべての Surface Hub デバイス アカウントの予定表の処理。</span><span class="sxs-lookup"><span data-stu-id="f72d5-114">Calendar processing for every Surface Hub device account.</span></span>
    - <span data-ttu-id="f72d5-115">スケジュール設定要求へのカスタム自動返信。</span><span class="sxs-lookup"><span data-stu-id="f72d5-115">Custom auto replies to scheduling requests.</span></span>
    - <span data-ttu-id="f72d5-116">既定の ActiveSync メールボックス ポリシーが他のユーザーまたは別のプロセスによって既に変更されている場合は、新しい ActiveSync メールボックス ポリシーを作成して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f72d5-116">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!TIP]
> <span data-ttu-id="f72d5-117">アカウントのセットアップを確認するには、以下のアカウント検証 [スクリプトを実行](#account-verification-script) します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-117">You can check account setup by running the [Account verification script](#account-verification-script) below.</span></span>

> [!NOTE]  
> <span data-ttu-id="f72d5-118">Surface Hub デバイス アカウントは、サード パーティのフェデレーション ID プロバイダー (FIP) をサポートしず、標準の Active Directory または Azure Active Directory アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f72d5-118">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <span data-ttu-id="f72d5-119">管理センターからアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="f72d5-119">Create account via admin center</span></span>

1. <span data-ttu-id="f72d5-120">Microsoft 365 管理センターで、[リソース\*\*\*\*] に移動し、[会議室&**備品**] を選択し、[+ リソースの追加]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="f72d5-120">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Add resource**.</span></span>

2. <span data-ttu-id="f72d5-121">デバイス アカウントの名前と電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-121">Provide a name and email address for the device account.</span></span> <span data-ttu-id="f72d5-122">残りの設定は既定の状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="f72d5-122">Leave remaining settings unchanged in the default state.</span></span>

   ![名前とメール アドレスを入力する](images/sh2-account2.png)

   ![残りの設定は既定の状態のままにする](images/sh2-account3.png)

3. <span data-ttu-id="f72d5-125">デバイス アカウントのパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-125">Set the password for the device account.</span></span> <span data-ttu-id="f72d5-126">パスワードを設定するには、[ユーザー] を選択 **し** 、[アクティブなユーザー] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="f72d5-126">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="f72d5-127">新しく作成したユーザーを検索してパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-127">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="f72d5-128">[このユーザー **が初** めてサインインするときにパスワードを変更する] オプション **を選択していないことを確認します。**</span><span class="sxs-lookup"><span data-stu-id="f72d5-128">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![デバイス アカウントのパスワードを設定する](images/sh2-account4.png)

4. <span data-ttu-id="f72d5-130">365 ライセンスを持つOffice割り当てる。</span><span class="sxs-lookup"><span data-stu-id="f72d5-130">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="f72d5-131">Office 365 Meeting **Room** ライセンスを割り当て、Microsoft Teams と Skype for Business のアカウントを自動的に有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="f72d5-131">It’s recommended to assign the Office 365 **Meeting Room** license, which automatically enables the account for Microsoft Teams and Skype for Business.</span></span>

   ![365 Officeを割り当てる](images/sh2-account5.png)


> [!NOTE]  
> <span data-ttu-id="f72d5-133">Skype for Business を使用している場合は、PowerShell を使用してセットアップを完了する必要があります -- Skype for Business カレンダー: [このアカウント](#set-calendar-auto-processing-skype-for-business-only) の予定表の自動処理を設定します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-133">If using Skype for Business, you will need to finalize setup via PowerShell -- Skype for Business Calendar: Set [Calendar Autoprocessing](#set-calendar-auto-processing-skype-for-business-only) for this account.</span></span> 

## <span data-ttu-id="f72d5-134">PowerShell を使用してアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="f72d5-134">Create account via PowerShell</span></span>

 <span data-ttu-id="f72d5-135">PowerShell を使用して Surface Hub のタスクを迅速に自動化しても、必ずしも PowerShell の専門知識が必要であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f72d5-135">Using PowerShell to rapidly automate tasks on Surface Hub does not necessarily require PowerShell expertise.</span></span> <span data-ttu-id="f72d5-136">このページで適切なスクリプトを使用する前に、セットアップの前提条件が完了していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-136">Ensure you have completed the setup prerequisites before using the appropriate scripts on this page.</span></span>

### <span data-ttu-id="f72d5-137">PowerShell を使用して Surface Hub を管理するための前提条件</span><span class="sxs-lookup"><span data-stu-id="f72d5-137">Prerequisites for using PowerShell to manage Surface Hub</span></span> 

1. <span data-ttu-id="f72d5-138">管理者特権 (管理者として**実行)** で PowerShell を起動し、PowerShell スクリプトを実行するようにシステムが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-138">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="f72d5-139">詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)。</span><span class="sxs-lookup"><span data-stu-id="f72d5-139">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="f72d5-140">[Azure PowerShell モジュールをインストールします](https://docs.microsoft.com/powershell/azure/install-az-ps)。</span><span class="sxs-lookup"><span data-stu-id="f72d5-140">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>


### <span data-ttu-id="f72d5-141">Exchange Online PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="f72d5-141">Connect to Exchange Online PowerShell</span></span>

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### <span data-ttu-id="f72d5-142">メールボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="f72d5-142">Create mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### <span data-ttu-id="f72d5-143">予定表の自動処理を設定する (Skype for Business のみ)</span><span class="sxs-lookup"><span data-stu-id="f72d5-143">Set Calendar auto-processing (Skype for Business only)</span></span>

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### <span data-ttu-id="f72d5-144">メール アプリの使用が必要な場合は ActiveSync を有効にする</span><span class="sxs-lookup"><span data-stu-id="f72d5-144">Enable ActiveSync if use of email app is required</span></span>

 <span data-ttu-id="f72d5-145">既定の ActiveSync ポリシーは、変更されていない場合に機能します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-145">The default ActiveSync Policy will work if unchanged.</span></span> <span data-ttu-id="f72d5-146">それ以外の場合は、新しいポリシーを作成して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f72d5-146">Otherwise createStupid a new Policy and assign.</span></span>

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```

### <span data-ttu-id="f72d5-147">Azure AD への接続</span><span class="sxs-lookup"><span data-stu-id="f72d5-147">Connect to Azure AD</span></span>

```powershell
Connect-AzureAD
```

### <span data-ttu-id="f72d5-148">ライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f72d5-148">Assign a license</span></span>

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### <span data-ttu-id="f72d5-149">利用可能なライセンスを確認する</span><span class="sxs-lookup"><span data-stu-id="f72d5-149">Check for available licenses</span></span>

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```

## <span data-ttu-id="f72d5-150">アカウント検証スクリプト</span><span class="sxs-lookup"><span data-stu-id="f72d5-150">Account verification script</span></span>

<span data-ttu-id="f72d5-151">デバイス アカウントを作成した後、次の検証スクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f72d5-151">After creating the device account, you can run the following verification script.</span></span> <span data-ttu-id="f72d5-152">このスクリプトは、以前に作成されたデバイス アカウントを検証し、概要レポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-152">This script validates a previously-created device account and produces a summary report.</span></span> <span data-ttu-id="f72d5-153">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="f72d5-153">For example:</span></span>

``` syntax
15 tests executed
0 failures
2 warnings
15 passed
```

<span data-ttu-id="f72d5-154">具体的な設定の詳細は表示されません。</span><span class="sxs-lookup"><span data-stu-id="f72d5-154">Details of specific settings will not be shown.</span></span>

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
```

## <span data-ttu-id="f72d5-155">詳細情報</span><span class="sxs-lookup"><span data-stu-id="f72d5-155">Learn more</span></span>

- [<span data-ttu-id="f72d5-156">PowerShell を使用して Surface Hub 2S オンプレミス アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="f72d5-156">Create Surface Hub 2S on-premises accounts with PowerShell</span></span>](surface-hub-2s-onprem-powershell.md)