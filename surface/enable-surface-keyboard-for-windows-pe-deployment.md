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
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: d7ae6fc434f77cad86e73f111243968493de4ff2
ms.sourcegitcommit: e6224f81f8efb6ac862afec0e60e3ddb182e9e6f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "11247309"
---
# <span data-ttu-id="70546-104">MDT の展開中に Surface Laptop キーボードを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="70546-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="70546-105">この記事では、Microsoft Deployment Toolkit (MDT) を使用する展開方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70546-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="70546-106">この情報は、他の展開方法にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="70546-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="70546-107">ほとんどの種類の Surface デバイスでは、ライト タッチ インストール (LTI) 中にキーボードが動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70546-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="70546-108">ただし、Surface Laptop では、キーボードを有効にするために追加のドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="70546-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="70546-109">Surface Laptop (第 1 世代) デバイスと Surface Laptop 2 デバイスでは、LTI の Windows プレインストール環境 (Windows PE) フェーズで使用するキーボード ドライバーを指定できるフォルダー構造と選択プロファイルを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70546-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="70546-110">このフォルダー構造の詳細については、「MDT を使った [Windows 10 イメージの展開: 手順 5:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)ドライバー リポジトリを準備する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70546-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>


> [!IMPORTANT]
> <span data-ttu-id="70546-111">Windows 10 (S モード) がプレインストールされている Surface Laptop に Windows 10 イメージを展開する場合は、KB [4032347](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)を参照してください。S モードでプレインストールされた Windows 10 を使用して Surface デバイスに Windows を展開する際の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="70546-111">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="70546-112">キーボード ドライバーを選択プロファイルに追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="70546-112">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="70546-113">適切な場所から最新の Surface Laptop MSI ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="70546-113">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="70546-114">Surface Laptop (第 1 世代) のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="70546-114">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="70546-115">Surface Laptop 2 のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="70546-115">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="70546-116">Intel プロセッサ ドライバーとファームウェアを搭載した Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="70546-116">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="70546-117">Surface Laptop MSI ファイルの内容を、見つけやすいフォルダー (c:\surface_laptop_drivers など) に抽出します。</span><span class="sxs-lookup"><span data-stu-id="70546-117">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="70546-118">内容を抽出するには、管理者特権のコマンド プロンプト ウィンドウを開き、次の例からコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="70546-118">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="70546-119">Deployment Workbench を開き **、[Deployment Shares]** ノードと展開共有を展開し **、WindowsPEX64 フォルダーに移動** します。</span><span class="sxs-lookup"><span data-stu-id="70546-119">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![Deployment Workbench 内の WindowsPEX64 フォルダーの場所を示す画像](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="70546-121">**WindowsPEX64 フォルダーを右クリック**し、[Import **Drivers] (ドライバーのインポート) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="70546-121">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>
5. <span data-ttu-id="70546-122">ドライバーのインポート ウィザードの指示に従って、ドライバー フォルダーを WindowsPEX64 フォルダーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-122">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

> [!NOTE]
>  <span data-ttu-id="70546-123">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="70546-123">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="70546-124">ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。</span><span class="sxs-lookup"><span data-stu-id="70546-124">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

<span data-ttu-id="70546-125">Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-125">To support Surface Laptop (1st Gen), import the following folders:</span></span>

 - <span data-ttu-id="70546-126">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="70546-126">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="70546-127">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-127">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
 - <span data-ttu-id="70546-128">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-128">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="70546-129">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="70546-129">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="70546-130">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70546-130">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="70546-131">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-131">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="70546-132">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-132">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
- <span data-ttu-id="70546-133">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-133">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
- <span data-ttu-id="70546-134">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-134">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="70546-135">Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-135">To support Surface Laptop 2, import the following folders:</span></span>

 - <span data-ttu-id="70546-136">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="70546-136">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="70546-137">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-137">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
 - <span data-ttu-id="70546-138">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-138">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="70546-139">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="70546-139">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
 - <span data-ttu-id="70546-140">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="70546-140">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
 - <span data-ttu-id="70546-141">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="70546-141">SurfacePlatformInstaller\Drivers\System\UART</span></span>
 - <span data-ttu-id="70546-142">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="70546-142">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="70546-143">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70546-143">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="70546-144">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-144">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="70546-145">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="70546-145">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="70546-146">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="70546-146">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="70546-147">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="70546-147">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="70546-148">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="70546-148">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="70546-149">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="70546-149">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="70546-150">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-150">SurfaceUpdate\Itouch</span></span>

 
<span data-ttu-id="70546-151">Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-151">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

- <span data-ttu-id="70546-152">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-152">SurfaceUpdate\IclSerialIOGPIO</span></span>
- <span data-ttu-id="70546-153">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="70546-153">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="70546-154">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="70546-154">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="70546-155">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="70546-155">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="70546-156">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="70546-156">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="70546-157">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="70546-157">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="70546-158">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="70546-158">SurfaceUpdate\SurfaceHotPlug</span></span>
- <span data-ttu-id="70546-159">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-159">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="70546-160">次のフォルダーをインポートすると、Surface Laptop 3 の PE でキーボード、トラックパッド、タッチの完全な機能を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="70546-160">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

- <span data-ttu-id="70546-161">IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-161">IclSerialIOGPIO</span></span>
- <span data-ttu-id="70546-162">IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="70546-162">IclSerialIOI2C</span></span>
- <span data-ttu-id="70546-163">IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="70546-163">IclSerialIOSPI</span></span>
- <span data-ttu-id="70546-164">IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="70546-164">IclSerialIOUART</span></span>
- <span data-ttu-id="70546-165">itouch</span><span class="sxs-lookup"><span data-stu-id="70546-165">itouch</span></span>
- <span data-ttu-id="70546-166">IclChipset</span><span class="sxs-lookup"><span data-stu-id="70546-166">IclChipset</span></span>
- <span data-ttu-id="70546-167">IclChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="70546-167">IclChipsetLPSS</span></span>
- <span data-ttu-id="70546-168">IclChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="70546-168">IclChipsetNorthpeak</span></span>
- <span data-ttu-id="70546-169">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="70546-169">ManagementEngine</span></span>
- <span data-ttu-id="70546-170">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="70546-170">SurfaceAcpiNotify</span></span>
- <span data-ttu-id="70546-171">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="70546-171">SurfaceBattery</span></span>
- <span data-ttu-id="70546-172">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="70546-172">SurfaceDockIntegration</span></span>
- <span data-ttu-id="70546-173">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="70546-173">SurfaceHidMini</span></span>
- <span data-ttu-id="70546-174">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="70546-174">SurfaceHotPlug</span></span>
- <span data-ttu-id="70546-175">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="70546-175">SurfaceIntegration</span></span>
- <span data-ttu-id="70546-176">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="70546-176">SurfaceSerialHub</span></span>
- <span data-ttu-id="70546-177">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="70546-177">SurfaceService</span></span>
- <span data-ttu-id="70546-178">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="70546-178">SurfaceStorageFwUpdate</span></span>


    > [!NOTE]
    >  <span data-ttu-id="70546-179">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="70546-179">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="70546-180">ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。</span><span class="sxs-lookup"><span data-stu-id="70546-180">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="70546-181">Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-181">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="70546-182">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="70546-182">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="70546-183">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-183">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="70546-184">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-184">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="70546-185">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="70546-185">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="70546-186">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70546-186">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="70546-187">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-187">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="70546-188">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-188">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="70546-189">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-189">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="70546-190">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-190">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="70546-191">Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-191">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="70546-192">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="70546-192">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="70546-193">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="70546-193">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="70546-194">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="70546-194">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="70546-195">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="70546-195">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="70546-196">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="70546-196">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="70546-197">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="70546-197">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="70546-198">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="70546-198">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="70546-199">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70546-199">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="70546-200">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-200">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="70546-201">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="70546-201">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="70546-202">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="70546-202">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="70546-203">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="70546-203">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="70546-204">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="70546-204">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="70546-205">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="70546-205">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="70546-206">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-206">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="70546-207">Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70546-207">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="70546-208">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="70546-208">SurfaceUpdate\IclSerialIOGPIO</span></span>
    - <span data-ttu-id="70546-209">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="70546-209">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="70546-210">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="70546-210">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="70546-211">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="70546-211">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="70546-212">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="70546-212">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="70546-213">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="70546-213">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="70546-214">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="70546-214">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="70546-215">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="70546-215">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="70546-216">Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。</span><span class="sxs-lookup"><span data-stu-id="70546-216">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="70546-217">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="70546-217">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="70546-218">WindowsPEX64 フォルダーにインポートされたドライバーが含まれているのを確認します。</span><span class="sxs-lookup"><span data-stu-id="70546-218">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="70546-219">フォルダーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="70546-219">The folder should resemble the following:</span></span>  

   ![Deployment Workbench の WindowsPEX64 フォルダーに新しくインポートされたドライバーを示す画像](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="70546-221">WindowsPEX64 フォルダーを使用する選択プロファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="70546-221">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="70546-222">選択プロファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="70546-222">The selection profile should resemble the following:</span></span>  

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="70546-224">次のように、新しい選択プロファイルを使う MDT 展開共有の Windows PE プロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="70546-224">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="70546-225">プラットフォーム **の場合**は **、x64 を選択します**。</span><span class="sxs-lookup"><span data-stu-id="70546-225">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="70546-226">[ **選択プロファイル] で**、新しいプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="70546-226">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="70546-227">[ **選択プロファイルからすべてのドライバーを含める] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="70546-227">Select **Include all drivers from the selection profile**.</span></span>
   
   ![MDT 展開共有の Windows PE プロパティを示す画像](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="70546-229">選択プロファイルまたは **DriverGroup001** 変数を使って、残りの Surface Laptop ドライバーが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="70546-229">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="70546-230">Surface Laptop (第 1 世代) の場合、モデルは **Surface Laptop です**。</span><span class="sxs-lookup"><span data-stu-id="70546-230">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="70546-231">残りの Surface Laptop ドライバーは、次の図に示すように、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="70546-231">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="70546-232">Surface Laptop 2 の場合、モデルは **Surface Laptop 2 です**。</span><span class="sxs-lookup"><span data-stu-id="70546-232">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="70546-233">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="70546-233">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="70546-234">Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。</span><span class="sxs-lookup"><span data-stu-id="70546-234">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="70546-235">残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="70546-235">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![Deployment Workbench の Surface Laptop フォルダーにある通常の Surface Laptop (第 1 世代) ドライバーを示す画像](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="70546-237">新しい選択プロファイルと関連する設定を使って MDT 展開共有を構成した後、「MDT を使った Windows 10 イメージの展開 [: 手順 6:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)展開タスク シーケンスを作成する」の説明に従って展開プロセスを続行します。</span><span class="sxs-lookup"><span data-stu-id="70546-237">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>
