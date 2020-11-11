---
title: Surface Pro 3 向けの UEFI の高度なセキュリティ機能 (Surface)
description: この記事では、UEFI の更新プログラム v3.11.760.0 をインストールし、Surface Pro 3 デバイス向けの追加のセキュリティ オプションを有効にするように構成する方法について説明します。
ms.assetid: 90F790C0-E5FC-4482-AD71-60589E3C9C93
ms.reviewer: ''
manager: laurawi
keywords: セキュリティ, 機能, 構成, ハードウェア, デバイス, カスタム, スクリプト, 更新プログラム, security, features, configure, hardware, device, custom, script, update
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 6a5c53c3e161bd4c49069a0665896762ce587618
ms.sourcegitcommit: e9190a6fe68b8a7cd9b024aea4be9f885f0de388
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "11163181"
---
# <span data-ttu-id="a6490-104">Surface Pro 3 向けの UEFI の高度なセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="a6490-104">Advanced UEFI security features for Surface Pro 3</span></span>


<span data-ttu-id="a6490-105">この記事では、UEFI の更新プログラム v3.11.760.0 をインストールし、Surface Pro 3 デバイス向けの追加のセキュリティ オプションを有効にするように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6490-105">This article describes how to install and configure the v3.11.760.0 UEFI update to enable additional security options for Surface Pro 3 devices.</span></span>

<span data-ttu-id="a6490-106">UEFI の更新プログラム v3.11.760.0 では、Surface デバイスのセキュリティをさらに細かく制御できるように、特定のハードウェア デバイスを無効にしたり、それらのデバイスからの起動を防止したりできる追加のセキュリティ オプションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a6490-106">To address more granular control over the security of Surface devices, the v3.11.760.0 UEFI update provides additional security options that allow you to disable specific hardware devices or to prevent starting from those devices.</span></span> <span data-ttu-id="a6490-107">UEFI の更新プログラムをデバイスにインストールした後、プログラムを手動で構成することも、スクリプトを実行して自動で構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6490-107">After the UEFI update is installed on a device, you can configure it manually or automatically by running a script.</span></span>

## <span data-ttu-id="a6490-108">UEFI の更新プログラムを手動でインストールする</span><span class="sxs-lookup"><span data-stu-id="a6490-108">Manually install the UEFI update</span></span>


<span data-ttu-id="a6490-109">Surface デバイスの高度なセキュリティ機能を構成する前に、まず UEFI の更新プログラム v3.11.760.0 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6490-109">Before you can configure the advanced security features of your Surface device, you must first install the v3.11.760.0 UEFI update.</span></span> <span data-ttu-id="a6490-110">この更新プログラムを Windows Update から受け取った場合、プログラムは自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a6490-110">This update is installed automatically if you receive your updates from Windows Update.</span></span> <span data-ttu-id="a6490-111">Windows Update を使って自動的に更新されるように Windows を構成する方法について詳しくは、「[Windows での自動更新の構成方法および使用方法](https://support.microsoft.com/kb/306525)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6490-111">For more information about how to configure Windows to update automatically by using Windows Update, see [How to configure and use Automatic Updates in Windows](https://support.microsoft.com/kb/306525).</span></span>

<span data-ttu-id="a6490-112">Surface Pro 3 の UEFI を更新する場合は、Surface UEFI の更新プログラムを Surface Pro 3 ファームウェアおよびドライバー パックの一部としてダウンロードし、インストールできます。</span><span class="sxs-lookup"><span data-stu-id="a6490-112">To update the UEFI on Surface Pro 3, you can download and install the Surface UEFI updates as part of the Surface Pro 3 Firmware and Driver Pack.</span></span> <span data-ttu-id="a6490-113">これらのファームウェアおよびドライバー パックは、Microsoft ダウンロード センターの [Surface Pro 3 のページ](https://www.microsoft.com/download/details.aspx?id=38826)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="a6490-113">These firmware and driver packs are available from the [Surface Pro 3 page](https://www.microsoft.com/download/details.aspx?id=38826) on the Microsoft Download Center.</span></span> <span data-ttu-id="a6490-114">ファームウェアおよびドライバー パックについて詳しくは、「[Surface デバイス用の最新のファームウェアとドライバーをダウンロードする](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6490-114">You can find out more about the firmware and driver packs at [Download the latest firmware and drivers for Surface devices](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices).</span></span> <span data-ttu-id="a6490-115">ファームウェアおよびドライバー パックは、両方自己完結型の Windows インストーラー (.msi) 形式とアーカイブ (.zip) 形式の両方で提供されています。</span><span class="sxs-lookup"><span data-stu-id="a6490-115">The firmware and driver packs are available as both self-contained Windows Installer (.msi) and archive (.zip) formats.</span></span> <span data-ttu-id="a6490-116">これら 2 種類の形式と、それぞれの形式を使用してドライバーを更新する方法について詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6490-116">You can find out more about these two formats and how you can use them to update your drivers at [Manage Surface driver and firmware updates](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates).</span></span>

## <span data-ttu-id="a6490-117">追加のセキュリティ設定を手動で構成する</span><span class="sxs-lookup"><span data-stu-id="a6490-117">Manually configure additional security settings</span></span>


>[!NOTE]
><span data-ttu-id="a6490-118">Surface デバイスのファームウェアのセットアップ画面に入るには、デバイスの電源を切り、**[音量を上げる]** ボタンを長押ししながら **[電源]** ボタンを押し、デバイスの起動が開始されたら **[音量を上げる]** ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="a6490-118">To enter firmware setup on a Surface device, begin with the device powered off, press and hold the **Volume Up** button, then press and release the **Power** button, then release the **Volume Up** button after the device has begun to boot.</span></span>

<span data-ttu-id="a6490-119">Surface デバイスに UEFI の更新プログラム v3.11.760.0 をインストールしたら、**[Advanced Device Security]** と呼ばれる追加の UEFI メニューを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a6490-119">After the v3.11.760.0 UEFI update is installed on a Surface device, an additional UEFI menu named **Advanced Device Security** becomes available.</span></span> <span data-ttu-id="a6490-120">このメニューをクリックすると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6490-120">If you click this menu, the following options are displayed:</span></span>

| <span data-ttu-id="a6490-121">オプション</span><span class="sxs-lookup"><span data-stu-id="a6490-121">Option</span></span>         | <span data-ttu-id="a6490-122">説明</span><span class="sxs-lookup"><span data-stu-id="a6490-122">Description</span></span>                                                                                                                                                                          | <span data-ttu-id="a6490-123">利用可能な設定 (太字は既定値)</span><span class="sxs-lookup"><span data-stu-id="a6490-123">Available settings (default listed in bold)</span></span> |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| <span data-ttu-id="a6490-124">ネットワーク ブート</span><span class="sxs-lookup"><span data-stu-id="a6490-124">Network Boot</span></span>   | <span data-ttu-id="a6490-125">Surface デバイスをネットワークから起動する機能を有効または無効にします (PXE ブートとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="a6490-125">Enables or disables the ability of your Surface device to boot from the network (also known as PXE boot).</span></span>                                                                            | <span data-ttu-id="a6490-126">**有効**、起動不可</span><span class="sxs-lookup"><span data-stu-id="a6490-126">**Enabled**, Not Bootable</span></span>                   |
| <span data-ttu-id="a6490-127">側面 USB</span><span class="sxs-lookup"><span data-stu-id="a6490-127">Side USB</span></span>       | <span data-ttu-id="a6490-128">Surface デバイスの側面にある USB ポートを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-128">Enables or disables the USB port on the side of the Surface device.</span></span> <span data-ttu-id="a6490-129">なお、この USB ポートを有効にすることはできますが、このポートからの起動は許可されません。</span><span class="sxs-lookup"><span data-stu-id="a6490-129">Additionally, the USB port can be enabled, but not allow booting.</span></span>                                                | <span data-ttu-id="a6490-130">**有効**、起動不可、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-130">**Enabled**, Not Bootable, Disabled</span></span>         |
| <span data-ttu-id="a6490-131">ドッキング ポート</span><span class="sxs-lookup"><span data-stu-id="a6490-131">Docking Port</span></span>   | <span data-ttu-id="a6490-132">Surface のドッキング ステーションのポートを有効または無効にします</span><span class="sxs-lookup"><span data-stu-id="a6490-132">Enables or disables the ports on the Surface docking station.</span></span> <span data-ttu-id="a6490-133">なお、ドッキング ポートを有効にすることはできますが、ドッキング ステーションの USB ポートまたはイーサネット ポートからの起動は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="a6490-133">Additionally, the docking port can be enabled, but block booting from any USB or Ethernet port in the docking station.</span></span> | <span data-ttu-id="a6490-134">**有効**、起動不可、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-134">**Enabled**, Not Bootable, Disabled</span></span>         |
| <span data-ttu-id="a6490-135">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="a6490-135">Front Camera</span></span>   | <span data-ttu-id="a6490-136">Surface デバイスの前面のカメラを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-136">Enables or disables the camera on the front of the Surface device.</span></span>                                                                                                                   | <span data-ttu-id="a6490-137">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-137">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="a6490-138">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="a6490-138">Rear Camera</span></span>    | <span data-ttu-id="a6490-139">Surface デバイスの背面のカメラを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-139">Enables or disables the camera on the rear of the Surface device.</span></span>                                                                                                                    | <span data-ttu-id="a6490-140">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-140">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="a6490-141">オンボード オーディオ</span><span class="sxs-lookup"><span data-stu-id="a6490-141">On Board Audio</span></span> | <span data-ttu-id="a6490-142">Surface デバイスのオーディオを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-142">Enables or disables audio on the Surface device.</span></span>                                                                                                                                     | <span data-ttu-id="a6490-143">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-143">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="a6490-144">microSD</span><span class="sxs-lookup"><span data-stu-id="a6490-144">microSD</span></span>        | <span data-ttu-id="a6490-145">Surface デバイスの microSD スロットを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-145">Enables or disables the microSD slot on the Surface device.</span></span>                                                                                                                          | <span data-ttu-id="a6490-146">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-146">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="a6490-147">WiFi</span><span class="sxs-lookup"><span data-stu-id="a6490-147">WiFi</span></span>           | <span data-ttu-id="a6490-148">Surface デバイスに組み込みの Wi-Fi トランシーバーを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-148">Enables or disables the built-in Wi-Fi transceiver in the Surface device.</span></span> <span data-ttu-id="a6490-149">これを無効にすると、Bluetooth も無効になります。</span><span class="sxs-lookup"><span data-stu-id="a6490-149">This also disables Bluetooth.</span></span>                                                                              | <span data-ttu-id="a6490-150">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-150">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="a6490-151">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="a6490-151">Bluetooth</span></span>      | <span data-ttu-id="a6490-152">Surface デバイスに組み込みの Bluetooth トランシーバーを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6490-152">Enables or disables the built-in Bluetooth transceiver in the Surface device.</span></span>                                                                                                        | <span data-ttu-id="a6490-153">**有効**、無効</span><span class="sxs-lookup"><span data-stu-id="a6490-153">**Enabled**, Disabled</span></span>                       |

 

## <span data-ttu-id="a6490-154">追加のセキュリティ設定を自動化する</span><span class="sxs-lookup"><span data-stu-id="a6490-154">Automate additional security settings</span></span>


<span data-ttu-id="a6490-155">管理者権限を持つ IT 担当者は、Microsoft ダウンロード センターから入手できる [Surface Pro 3 Firmware Tools (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) を利用して、UEFI 設定の構成を自動化することができます。</span><span class="sxs-lookup"><span data-stu-id="a6490-155">As an IT professional with administrative privileges, you can automate the configuration of UEFI settings by leveraging [Surface Pro 3 Firmware Tools (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) available from the Microsoft Download Center.</span></span> <span data-ttu-id="a6490-156">これらのツールを利用すると、すべてのカスタム アプリケーションやスクリプトから呼び出すことができる .NET アセンブリがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a6490-156">These tools install a .NET assembly that can be called from any custom application or script.</span></span>

**<span data-ttu-id="a6490-157">前提条件</span><span class="sxs-lookup"><span data-stu-id="a6490-157">Prerequisites</span></span>**

-   <span data-ttu-id="a6490-158">以下に示すサンプル スクリプトでは、前に説明した拡張機能を利用しているため、管理されているデバイスにツールがインストールされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a6490-158">The sample scripts below leverage the previously mentioned extension and therefore assume that the tool has been installed on the device being managed.</span></span>
-   <span data-ttu-id="a6490-159">スクリプトは管理者権限で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6490-159">The scripts must be run with administrative privilege.</span></span>
-   <span data-ttu-id="a6490-160">サンプル スクリプトがデジタル署名されていない場合は、スクリプトを実行する前に Windows PowerShell コマンド [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6490-160">The Windows PowerShell command [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) must be called prior to running sample scripts if they are not digitally signed.</span></span>

**<span data-ttu-id="a6490-161">サンプル スクリプト</span><span class="sxs-lookup"><span data-stu-id="a6490-161">Sample scripts</span></span>**

> [!NOTE]
> <span data-ttu-id="a6490-162">以下のサンプル スクリプトで使用される UEFI パスワードはクリア テキストで表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6490-162">The UEFI password used in the sample scripts below is presented in clear text.</span></span> <span data-ttu-id="a6490-163">スクリプトを保護された場所に保存し、管理された環境で実行することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6490-163">We strongly recommend saving the scripts in a protected location and running them in a controlled environment.</span></span>


<span data-ttu-id="a6490-164">構成可能なオプションをすべて示します。</span><span class="sxs-lookup"><span data-stu-id="a6490-164">Show all configurable options:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
foreach ($uefiOption in $uefiOptions) 
{ 
    Write-Host "Name:" $uefiOption.Name 
    Write-Host " Description =" $uefiOption.Description 
    Write-Host " Current Value =" $uefiOption.CurrentValue 
    Write-Host " Default Value =" $uefiOption.DefaultValue 
    Write-Host " Proposed Value =" $uefiOption.ProposedValue 
     
    # This gives usage and validation information 
    Write-Host " Allowed Values =" $uefiOption.FriendlyRegEx 
    Write-Host " Regular Expression =" $uefiOption.RegEx 
     
    Write-Host 
}
```

<span data-ttu-id="a6490-165">UEFI パスワードを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="a6490-165">Set or change UEFI password:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
$Password = [Microsoft.Surface.FirmwareOption]::Find("Password") 
 
# Set New value to 12345 
$Password.ProposedValue = "12345"
```

<span data-ttu-id="a6490-166">提示された変更の状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="a6490-166">Check status of proposed changes:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Check update status 
$updateStatus = [Microsoft.Surface.FirmwareOption]::UpdateStatus 
$updateIteration = [Microsoft.Surface.FirmwareOption]::UpdateIteration 
Write-Host "Last Update Status =" $updateStatus 
Write-Host "Last Update Iteration =" $updateIteration 
 
# Get the individual results for the last proposed update 
# If the device has never had an update attempt this will be an empty list 
$details = [Microsoft.Surface.FirmwareOption]::UpdateStatusDetails 
Write-Host $details.Count "Settings were proposed" 
if ($details.Count -gt 0) 
{ 
    Write-Host "Result Details" 
    foreach ($detail in $details.GetEnumerator()) 
    { 
        Write-Host " " $detail.Key "=" $detail.Value 
    } 
}
```

<span data-ttu-id="a6490-167">UEFI を既定値に戻します。</span><span class="sxs-lookup"><span data-stu-id="a6490-167">Revert UEFI to default values:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
# Reset all options to the factory default 
foreach ($uefiOption in $uefiOptions) 
{ 
    $uefiOption.ProposedValue = $uefiOption.DefaultValue 
}
```

<span data-ttu-id="a6490-168">状態コードの解釈</span><span class="sxs-lookup"><span data-stu-id="a6490-168">Status code interpretation</span></span>

-   <span data-ttu-id="a6490-169">00 - 提示された更新が成功しました。</span><span class="sxs-lookup"><span data-stu-id="a6490-169">00 - The proposed update was a success</span></span>
-   <span data-ttu-id="a6490-170">02 - 提示された値の 1 つが無効な値でした。</span><span class="sxs-lookup"><span data-stu-id="a6490-170">02 - One of the proposed values had an invalid value</span></span>
-   <span data-ttu-id="a6490-171">03 - 提示された値セットの 1 つが認識されませんでした。</span><span class="sxs-lookup"><span data-stu-id="a6490-171">03 - There was a proposed value set that was not recognized</span></span>
-   <span data-ttu-id="a6490-172">0F - ロック解除パスワードが現在設定されているパスワードと一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="a6490-172">0F - The unlock password did not match currently set password</span></span>

 
