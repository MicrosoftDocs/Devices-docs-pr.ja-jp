---
title: Office 365 を使ったオンライン展開 (Surface Hub)
description: このトピックでは、純粋なオンライン展開がある場合に Microsoft Surface Hub のデバイス アカウントを追加する手順を示します。
ms.assetid: D325CA68-A03F-43DF-8520-EACF7C3EDEC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のデバイス アカウント, オンライン展開, device account for Surface Hub, online deployment
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/21/2018
ms.localizationpriority: medium
ms.openlocfilehash: b38b8eb0ef13c2e945d63821e6e246ac7a59b2d7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836133"
---
# <span data-ttu-id="7f768-104">Office 365 を使ったオンライン展開 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="7f768-104">Online deployment with Office 365 (Surface Hub)</span></span>


<span data-ttu-id="7f768-105">このトピックでは、純粋なオンライン展開がある場合に Microsoft Surface Hub のデバイス アカウントを追加する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="7f768-105">This topic has instructions for adding a device account for your Microsoft Surface Hub when you have a pure, online deployment.</span></span>

<span data-ttu-id="7f768-106">純粋なオンライン (O365) 展開がある場合は、[提供されている PowerShell スクリプトを使用](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts)してデバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-106">If you have a pure, online (O365) deployment, then you can [use the provided PowerShell scripts](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts) to create device accounts.</span></span> 

1. <span data-ttu-id="7f768-107">PC でリモート PowerShell セッションを開始し、Exchange に接続します。</span><span class="sxs-lookup"><span data-stu-id="7f768-107">Start a remote PowerShell session on a PC and connect to Exchange.</span></span>

   <span data-ttu-id="7f768-108">関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7f768-108">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

   ```PowerShell
   Set-ExecutionPolicy RemoteSigned
   $org='contoso.microsoft.com'
   $cred=Get-Credential admin@$org
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```

2. <span data-ttu-id="7f768-109">セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="7f768-109">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="7f768-110">これにより、アカウントを Surface Hub に対して認証できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-110">This will allow the account to authenticate into the Surface Hub.</span></span>

   <span data-ttu-id="7f768-111">既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f768-111">If you're changing an existing resource mailbox:</span></span>

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   <span data-ttu-id="7f768-112">新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f768-112">If you’re creating a new resource mailbox:</span></span>

   ```PowerShell
   New-Mailbox -MicrosoftOnlineServicesID HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. <span data-ttu-id="7f768-113">メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-113">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="7f768-114">Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-114">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="7f768-115">このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。</span><span class="sxs-lookup"><span data-stu-id="7f768-115">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

   <span data-ttu-id="7f768-116">互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f768-116">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="7f768-117">ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-117">Once it’s created, you can apply the same policy to other device accounts.</span></span>

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false -AllowNonProvisionableDevices $True
   ```

   <span data-ttu-id="7f768-118">互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-118">Once you have a compatible policy, then you will need to apply the policy to the device account.</span></span>

   ```PowerShell
   Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.Id
   ```

4. <span data-ttu-id="7f768-119">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-119">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="7f768-120">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7f768-120">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

   ```PowerShell
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. <span data-ttu-id="7f768-121">Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="7f768-121">Connect to Azure AD.</span></span>
    
   <span data-ttu-id="7f768-122">PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-122">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="7f768-123">管理者特権の PowerShell プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f768-123">In an elevated powershell prompt run the following command :</span></span>
    
   ```PowerShell
   Install-Module -Name AzureAD
   ```
   <span data-ttu-id="7f768-124">一部のアカウント設定を適用するには、Azure AD に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-124">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="7f768-125">次のコマンドレットを実行すると接続できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-125">You can run this cmdlet to connect.</span></span>

   ```PowerShell
   Import-Module AzureAD
   Connect-AzureAD -Credential $cred
   ```

6. <span data-ttu-id="7f768-126">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-126">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="7f768-127">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7f768-127">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

   ```PowerShell
   Set-AzureADUser -ObjectId "HUB01@contoso.com" -PasswordPolicies "DisablePasswordExpiration"
   ```

7. <span data-ttu-id="7f768-128">Surface Hub には、Skype for Business 機能のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="7f768-128">Surface Hub requires a license for Skype for Business functionality.</span></span> <span data-ttu-id="7f768-129">Skype for Business を有効にするには、環境が [Skype for Business Online の前提条件](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online)を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-129">In order to enable Skype for Business, your environment will need to meet the [prerequisites for Skype for Business online](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online).</span></span>
   
   <span data-ttu-id="7f768-130">次に、`Get-AzureADSubscribedSku` を使って、O365 テナントで利用可能な SKU の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-130">Next, you can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

   <span data-ttu-id="7f768-131">SKU の一覧を取得したら、`$License.SkuId` 変数に必要な SkuId を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-131">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

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

8. <span data-ttu-id="7f768-132">デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="7f768-132">Enable the device account with Skype for Business.</span></span>
   <span data-ttu-id="7f768-133">Skype for Business の PowerShell モジュールがインストールされていない場合は、[Windows PowerShell Module for Skype for Business Online をダウンロード](https://www.microsoft.com/download/details.aspx?id=39366)します。</span><span class="sxs-lookup"><span data-stu-id="7f768-133">If the Skype for Business PowerShell module is not installed, [download the Skype for Business Online Windows PowerShell Module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 

   - <span data-ttu-id="7f768-134">まず、PC でリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f768-134">Start by creating a remote PowerShell session from a PC.</span></span>

     ```PowerShell
     Import-Module SkypeOnlineConnector  
     $cssess=New-CsOnlineSession -Credential $cred  
     Import-PSSession $cssess -AllowClobber
     ```

   - <span data-ttu-id="7f768-135">次に、環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、このコマンドレット (<em>alice@contoso.com</em> など) を使って、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="7f768-135">Next, if you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet (for example, <em>alice@contoso.com</em>):</span></span>

       ```PowerShell
       Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool
       ```
       <span data-ttu-id="7f768-136">または、次の変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="7f768-136">OR by setting a variable</span></span>
        
       ```PowerShell
    $strRegistrarPool = Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool | out-string
    $strRegistrarPool = $strRegistrarPool.Substring($strRegistrarPool.IndexOf(':') + 2)
       ```
        
   - <span data-ttu-id="7f768-137">次のコマンドレットを使って Surface Hub アカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7f768-137">Enable the Surface Hub account with the following cmdlet:</span></span>
      
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool yourRegistrarPool -SipAddressType EmailAddress
       ```
        
       <span data-ttu-id="7f768-138">または、上のコマンドレットで $strRegistarPool 変数を使います。</span><span class="sxs-lookup"><span data-stu-id="7f768-138">OR using the $strRegistarPool variable from above</span></span>
        
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool $strRegistrarPool -SipAddressType EmailAddress
       ```

<span data-ttu-id="7f768-139">検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f768-139">For validation, you should be able to use any Skype for Business client (PC, Android, etc) to sign in to this account.</span></span>





