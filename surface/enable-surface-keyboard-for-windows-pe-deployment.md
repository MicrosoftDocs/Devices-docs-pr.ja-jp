---
title: MDT の展開中に Surface Laptop キーボードを有効にする方法
description: MDT を使って Windows 10 を Surface ノート PC に展開する場合は、Windows PE 環境で使うキーボード ドライバーをインポートする必要があります。
keywords: Windows 10 surface, 自動化, カスタマイズ, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
ms.reviewer: scottmca
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
ms.date: 02/02/2021
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: fb51dd3785882e74c90d8b2717e4cc499d492d6f
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312063"
---
# <span data-ttu-id="8c46a-104">MDT の展開中に Surface Laptop キーボードを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="8c46a-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="8c46a-105">この記事では、Microsoft Deployment Toolkit (MDT) を使用する展開方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="8c46a-106">この情報は、他の展開方法にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="8c46a-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="8c46a-107">ほとんどの種類の Surface デバイスでは、ライト タッチ インストール (LTI) 中にキーボードが動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="8c46a-108">ただし、Surface Laptop では、キーボードを有効にするために追加のドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="8c46a-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="8c46a-109">Surface Laptop (第 1 世代) デバイスと Surface Laptop 2 デバイスでは、LTI の Windows プレインストール環境 (Windows PE) フェーズで使用するキーボード ドライバーを指定できるフォルダー構造と選択プロファイルを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="8c46a-110">このフォルダー構造の詳細については、「MDT を使った [Windows 10 イメージの展開: 手順 5:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)ドライバー リポジトリを準備する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c46a-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>

> [!TIP]    
> <span data-ttu-id="8c46a-111">同じ Windows PE ブート インスタンスで Surface Laptop 2 と Surface Laptop 3 のキーボード ドライバーを使う場合、キーボードまたはタッチパッドが Windows PE で動作しない場合は、ファームウェアを手動でリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-111">When using keyboard drivers for Surface Laptop 2 and Surface Laptop 3 in the same Windows PE boot instance, you may need to manually reset the firmware if the keyboard or touchpad don’t work in Windows PE:</span></span>
>
> - <span data-ttu-id="8c46a-112">電源ボタンを 30 秒間長押しします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-112">Press and hold the Power button for 30 seconds.</span></span> <span data-ttu-id="8c46a-113">電源ユニット (PSU) に接続している場合は、電源ボタンを長押しして、PSU コードの最後にあるライトが少しオフになるまで押し続け、電源をオンに戻します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-113">If you are connected to a power supply unit (PSU), press and hold the Power button until you see the light at the end of the PSU cord briefly turn off before turning back on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c46a-114">Windows 10 (S モード) がプレインストールされている Surface Laptop に Windows 10 イメージを展開する場合は、KB [4032347](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)を参照してください。S モードでプレインストールされた Windows 10 を使用して Surface デバイスに Windows を展開する際の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-114">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="8c46a-115">キーボード ドライバーを選択プロファイルに追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-115">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="8c46a-116">適切な場所から最新の Surface Laptop MSI ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-116">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="8c46a-117">Surface Laptop (第 1 世代) のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="8c46a-117">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="8c46a-118">Surface Laptop 2 のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="8c46a-118">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="8c46a-119">Intel プロセッサ ドライバーとファームウェアを搭載した Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="8c46a-119">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="8c46a-120">Surface Laptop MSI ファイルの内容を、見つけやすいフォルダー (c:\surface_laptop_drivers など) に抽出します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-120">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="8c46a-121">内容を抽出するには、管理者特権のコマンド プロンプト ウィンドウを開き、次の例からコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-121">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="8c46a-122">Deployment Workbench を開き **、[Deployment Shares]** ノードと展開共有を展開し **、WindowsPEX64 フォルダーに移動** します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-122">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![Deployment Workbench 内の WindowsPEX64 フォルダーの場所を示す画像](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="8c46a-124">**WindowsPEX64 フォルダーを右クリック**し、[Import **Drivers] (ドライバーのインポート) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="8c46a-124">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>

5. <span data-ttu-id="8c46a-125">ドライバーのインポート ウィザードの指示に従って、ドライバー フォルダーを WindowsPEX64 フォルダーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-125">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8c46a-126">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-126">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="8c46a-127">ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。</span><span class="sxs-lookup"><span data-stu-id="8c46a-127">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="8c46a-128">Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-128">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="8c46a-129">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-129">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="8c46a-130">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-130">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="8c46a-131">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-131">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="8c46a-132">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-132">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="8c46a-133">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-133">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="8c46a-134">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-134">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-135">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-135">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="8c46a-136">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-136">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="8c46a-137">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-137">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="8c46a-138">Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-138">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="8c46a-139">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-139">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="8c46a-140">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-140">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="8c46a-141">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-141">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="8c46a-142">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-142">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="8c46a-143">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-143">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="8c46a-144">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="8c46a-144">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="8c46a-145">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-145">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="8c46a-146">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-146">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="8c46a-147">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-147">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-148">SurfaceUpdate\serialioi2c</span><span class="sxs-lookup"><span data-stu-id="8c46a-148">SurfaceUpdate\serialioi2c</span></span>
    - <span data-ttu-id="8c46a-149">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-149">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="8c46a-150">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="8c46a-150">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="8c46a-151">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="8c46a-151">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="8c46a-152">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="8c46a-152">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="8c46a-153">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-153">SurfaceUpdate\Itouch</span></span>

     
    <span data-ttu-id="8c46a-154">Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-154">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="8c46a-155">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-155">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-156">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-156">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="8c46a-157">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-157">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="8c46a-158">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="8c46a-158">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="8c46a-159">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="8c46a-159">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="8c46a-160">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="8c46a-160">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="8c46a-161">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="8c46a-161">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="8c46a-162">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-162">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="8c46a-163">次のフォルダーをインポートすると、Surface Laptop 3 の PE でキーボード、トラックパッド、タッチの完全な機能を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="8c46a-163">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

    - <span data-ttu-id="8c46a-164">SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-164">SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-165">SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-165">SerialIOI2C</span></span>
    - <span data-ttu-id="8c46a-166">SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-166">SerialIOSPI</span></span>
    - <span data-ttu-id="8c46a-167">SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="8c46a-167">SerialIOUART</span></span>
    - <span data-ttu-id="8c46a-168">itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-168">itouch</span></span>
    - <span data-ttu-id="8c46a-169">チップセット</span><span class="sxs-lookup"><span data-stu-id="8c46a-169">Chipset</span></span>
    - <span data-ttu-id="8c46a-170">ChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="8c46a-170">ChipsetLPSS</span></span>
    - <span data-ttu-id="8c46a-171">ChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="8c46a-171">ChipsetNorthpeak</span></span>
    - <span data-ttu-id="8c46a-172">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="8c46a-172">ManagementEngine</span></span>
    - <span data-ttu-id="8c46a-173">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="8c46a-173">SurfaceAcpiNotify</span></span>
    - <span data-ttu-id="8c46a-174">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="8c46a-174">SurfaceBattery</span></span>
    - <span data-ttu-id="8c46a-175">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="8c46a-175">SurfaceDockIntegration</span></span>
    - <span data-ttu-id="8c46a-176">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="8c46a-176">SurfaceHidMini</span></span>
    - <span data-ttu-id="8c46a-177">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="8c46a-177">SurfaceHotPlug</span></span>
    - <span data-ttu-id="8c46a-178">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="8c46a-178">SurfaceIntegration</span></span>
    - <span data-ttu-id="8c46a-179">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="8c46a-179">SurfaceSerialHub</span></span>
    - <span data-ttu-id="8c46a-180">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="8c46a-180">SurfaceService</span></span>
    - <span data-ttu-id="8c46a-181">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="8c46a-181">SurfaceStorageFwUpdate</span></span>

     > [!NOTE]
     >  <span data-ttu-id="8c46a-182">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-182">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="8c46a-183">ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。</span><span class="sxs-lookup"><span data-stu-id="8c46a-183">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

     <span data-ttu-id="8c46a-184">Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-184">To support Surface Laptop (1st Gen), import the following folders:</span></span>

    - <span data-ttu-id="8c46a-185">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-185">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
    - <span data-ttu-id="8c46a-186">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-186">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="8c46a-187">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-187">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="8c46a-188">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-188">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="8c46a-189">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-189">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="8c46a-190">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-190">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-191">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-191">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="8c46a-192">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-192">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="8c46a-193">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-193">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="8c46a-194">Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-194">To support Surface Laptop 2, import the following folders:</span></span>

    - <span data-ttu-id="8c46a-195">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-195">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
    - <span data-ttu-id="8c46a-196">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-196">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
    - <span data-ttu-id="8c46a-197">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="8c46a-197">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="8c46a-198">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-198">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
    - <span data-ttu-id="8c46a-199">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-199">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
    - <span data-ttu-id="8c46a-200">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="8c46a-200">SurfacePlatformInstaller\Drivers\System\UART</span></span>
    - <span data-ttu-id="8c46a-201">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-201">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="8c46a-202">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-202">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="8c46a-203">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-203">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-204">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-204">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="8c46a-205">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-205">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="8c46a-206">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="8c46a-206">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="8c46a-207">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="8c46a-207">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="8c46a-208">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="8c46a-208">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="8c46a-209">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-209">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="8c46a-210">Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8c46a-210">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="8c46a-211">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="8c46a-211">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="8c46a-212">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="8c46a-212">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="8c46a-213">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="8c46a-213">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="8c46a-214">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="8c46a-214">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="8c46a-215">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="8c46a-215">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="8c46a-216">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="8c46a-216">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="8c46a-217">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="8c46a-217">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="8c46a-218">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="8c46a-218">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c46a-219">Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。</span><span class="sxs-lookup"><span data-stu-id="8c46a-219">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="8c46a-220">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-220">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="8c46a-221">WindowsPEX64 フォルダーにインポートされたドライバーが含まれているのを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-221">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="8c46a-222">フォルダーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-222">The folder should resemble the following:</span></span>  

   ![Deployment Workbench の WindowsPEX64 フォルダーに新しくインポートされたドライバーを示す画像](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="8c46a-224">WindowsPEX64 フォルダーを使用する選択プロファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-224">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="8c46a-225">選択プロファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-225">The selection profile should resemble the following:</span></span>  

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="8c46a-227">次のように、新しい選択プロファイルを使う MDT 展開共有の Windows PE プロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-227">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="8c46a-228">プラットフォーム **の場合**は **、x64 を選択します**。</span><span class="sxs-lookup"><span data-stu-id="8c46a-228">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="8c46a-229">[ **選択プロファイル] で**、新しいプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-229">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="8c46a-230">[ **選択プロファイルからすべてのドライバーを含める] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="8c46a-230">Select **Include all drivers from the selection profile**.</span></span>
   
   ![MDT 展開共有の Windows PE プロパティを示す画像](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="8c46a-232">選択プロファイルまたは **DriverGroup001** 変数を使って、残りの Surface Laptop ドライバーが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-232">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="8c46a-233">Surface Laptop (第 1 世代) の場合、モデルは **Surface Laptop です**。</span><span class="sxs-lookup"><span data-stu-id="8c46a-233">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="8c46a-234">次の図に示すように、残りの Surface Laptop ドライバーは\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-234">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="8c46a-235">Surface Laptop 2 の場合、モデルは **Surface Laptop 2 です**。</span><span class="sxs-lookup"><span data-stu-id="8c46a-235">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="8c46a-236">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-236">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="8c46a-237">Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。</span><span class="sxs-lookup"><span data-stu-id="8c46a-237">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="8c46a-238">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8c46a-238">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![Deployment Workbench の Surface Laptop フォルダーにある通常の Surface Laptop (第 1 世代) ドライバーを示す画像](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="8c46a-240">新しい選択プロファイルと関連する設定を使って MDT 展開共有を構成した後、「MDT を使った Windows 10 イメージの展開 [: 手順 6:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)展開タスク シーケンスを作成する」の説明に従って展開プロセスを続行します。</span><span class="sxs-lookup"><span data-stu-id="8c46a-240">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>
