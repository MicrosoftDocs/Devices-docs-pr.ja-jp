---
title: MDT の展開時に Surface ラップトップキーボードを有効にする方法
description: MDT を使用して Windows 10 を Surface のノート pc に展開する場合は、Windows PE 環境で使うキーボードドライバーをインポートする必要があります。
keywords: windows 10 surface、オートメーション、カスタマイズ、mdt
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
ms.openlocfilehash: 5d4e4b46c109d9fe24fe75151c9eb1e0a8b702c0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834717"
---
# <span data-ttu-id="88539-104">MDT の展開時に Surface ラップトップキーボードを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="88539-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="88539-105">この記事では、Microsoft 展開ツールキット (MDT) を使用する展開方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88539-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="88539-106">この情報は、その他の展開方法論にも適用することができます。</span><span class="sxs-lookup"><span data-stu-id="88539-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="88539-107">ほとんどの種類の Surface デバイスでは、キーボードは、ライトタッチインストール (LTI) で動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88539-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="88539-108">ただし、Surface ノートパソコンでキーボードを有効にするには、追加のドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="88539-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="88539-109">Surface Pc (第1世代) および Surface ノートブック2台の場合、LTI の Windows Preinstallation Environment (Windows PE) フェーズで使用するキーボードドライバーを指定できるようにするには、フォルダー構造と選択プロファイルを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88539-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="88539-110">このフォルダー構造の詳細については、「 [MDT を使用した Windows 10 イメージの展開: 手順 5: ドライバーリポジトリを準備する](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88539-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>

> [!NOTE]
> <span data-ttu-id="88539-111">ドライバーの競合により、現在のところ、同じ Windows PE ブートインスタンスで Surface ノートブック2と Surface ノートブックの3つのキーボードドライバーを追加することはサポートされていません。代わりに別のインスタンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="88539-111">It is currently not supported to add Surface Laptop 2 and Surface Laptop 3 keyboard drivers in the same Windows PE boot instance due to a driver conflict; use separate instances instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88539-112">Windows 10 イメージを S モードでプレインストールされた Surface ノート Pc に展開している場合は、「windows 10 を[プレインストールしているときに、s モードで](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)windows 10 をインストールすると、KB 4032347、問題が発生する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88539-112">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="88539-113">選択プロファイルにキーボードドライバーを追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="88539-113">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="88539-114">適切な場所から最新の Surface ラップトップ MSI ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="88539-114">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="88539-115">Surface ラップトップ (第1世代) ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="88539-115">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="88539-116">Surface ラップトップ2ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="88539-116">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="88539-117">Intel プロセッサドライバーとファームウェアを搭載した Surface ノートパソコン3</span><span class="sxs-lookup"><span data-stu-id="88539-117">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="88539-118">Surface ラップトップ MSI ファイルの内容を、簡単に見つけることができるフォルダー (c:\ surface_laptop_drivers など) に抽出します。</span><span class="sxs-lookup"><span data-stu-id="88539-118">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="88539-119">コンテンツを抽出するには、管理者特権のコマンドプロンプトウィンドウを開いて、次の例のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="88539-119">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="88539-120">展開ワークベンチを開き **、展開共有ノードと**展開共有を展開して、 **WindowsPEX64**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="88539-120">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![展開ワークベンチでの WindowsPEX64 フォルダーの場所を示す画像](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="88539-122">**WindowsPEX64**フォルダーを右クリックして、[**ドライバーのインポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="88539-122">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>
5. <span data-ttu-id="88539-123">ドライバーのインポートウィザードの指示に従って、WindowsPEX64 フォルダーにドライバーフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-123">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

> [!NOTE]
>  <span data-ttu-id="88539-124">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="88539-124">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="88539-125">MSI がリリースされたタイミングに応じて、ディレクトリ構造は、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) のいずれかで開始されます。</span><span class="sxs-lookup"><span data-stu-id="88539-125">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

<span data-ttu-id="88539-126">Surface Pc (第1世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-126">To support Surface Laptop (1st Gen), import the following folders:</span></span>

 - <span data-ttu-id="88539-127">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="88539-127">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="88539-128">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-128">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
 - <span data-ttu-id="88539-129">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-129">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="88539-130">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="88539-130">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="88539-131">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="88539-131">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="88539-132">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-132">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="88539-133">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-133">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
- <span data-ttu-id="88539-134">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-134">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
- <span data-ttu-id="88539-135">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-135">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="88539-136">Surface ノート Pc 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-136">To support Surface Laptop 2, import the following folders:</span></span>

 - <span data-ttu-id="88539-137">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="88539-137">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="88539-138">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-138">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
 - <span data-ttu-id="88539-139">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-139">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="88539-140">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="88539-140">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
 - <span data-ttu-id="88539-141">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="88539-141">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
 - <span data-ttu-id="88539-142">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="88539-142">SurfacePlatformInstaller\Drivers\System\UART</span></span>
 - <span data-ttu-id="88539-143">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="88539-143">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="88539-144">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="88539-144">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="88539-145">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-145">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="88539-146">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="88539-146">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="88539-147">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="88539-147">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="88539-148">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="88539-148">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="88539-149">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="88539-149">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="88539-150">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="88539-150">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="88539-151">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-151">SurfaceUpdate\Itouch</span></span>

 
<span data-ttu-id="88539-152">Intel プロセッサを搭載した Surface ノート Pc 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-152">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

- <span data-ttu-id="88539-153">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-153">SurfaceUpdate\IclSerialIOGPIO</span></span>
- <span data-ttu-id="88539-154">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="88539-154">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="88539-155">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="88539-155">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="88539-156">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="88539-156">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="88539-157">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="88539-157">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="88539-158">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="88539-158">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="88539-159">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="88539-159">SurfaceUpdate\SurfaceHotPlug</span></span>
- <span data-ttu-id="88539-160">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-160">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="88539-161">次のフォルダーをインポートすると、Surface Pc 3 の PE でのフルキーボード、トラックパッド、タッチ機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="88539-161">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

- <span data-ttu-id="88539-162">IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-162">IclSerialIOGPIO</span></span>
- <span data-ttu-id="88539-163">IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="88539-163">IclSerialIOI2C</span></span>
- <span data-ttu-id="88539-164">Iclて、</span><span class="sxs-lookup"><span data-stu-id="88539-164">IclSerialIOSPI</span></span>
- <span data-ttu-id="88539-165">お絵</span><span class="sxs-lookup"><span data-stu-id="88539-165">IclSerialIOUART</span></span>
- <span data-ttu-id="88539-166">itouch</span><span class="sxs-lookup"><span data-stu-id="88539-166">itouch</span></span>
- <span data-ttu-id="88539-167">IclChipset セット</span><span class="sxs-lookup"><span data-stu-id="88539-167">IclChipset</span></span>
- <span data-ttu-id="88539-168">IclChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="88539-168">IclChipsetLPSS</span></span>
- <span data-ttu-id="88539-169">IclChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="88539-169">IclChipsetNorthpeak</span></span>
- <span data-ttu-id="88539-170">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="88539-170">ManagementEngine</span></span>
- <span data-ttu-id="88539-171">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="88539-171">SurfaceAcpiNotify</span></span>
- <span data-ttu-id="88539-172">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="88539-172">SurfaceBattery</span></span>
- <span data-ttu-id="88539-173">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="88539-173">SurfaceDockIntegration</span></span>
- <span data-ttu-id="88539-174">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="88539-174">SurfaceHidMini</span></span>
- <span data-ttu-id="88539-175">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="88539-175">SurfaceHotPlug</span></span>
- <span data-ttu-id="88539-176">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="88539-176">SurfaceIntegration</span></span>
- <span data-ttu-id="88539-177">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="88539-177">SurfaceSerialHub</span></span>
- <span data-ttu-id="88539-178">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="88539-178">SurfaceService</span></span>
- <span data-ttu-id="88539-179">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="88539-179">SurfaceStorageFwUpdate</span></span>


    > [!NOTE]
    >  <span data-ttu-id="88539-180">ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="88539-180">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="88539-181">MSI がリリースされたタイミングに応じて、ディレクトリ構造は、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) のいずれかで開始されます。</span><span class="sxs-lookup"><span data-stu-id="88539-181">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="88539-182">Surface Pc (第1世代) をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-182">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="88539-183">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="88539-183">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="88539-184">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-184">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="88539-185">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-185">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="88539-186">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="88539-186">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="88539-187">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="88539-187">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="88539-188">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-188">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="88539-189">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-189">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="88539-190">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-190">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="88539-191">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-191">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="88539-192">Surface ノート Pc 2 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-192">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="88539-193">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="88539-193">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="88539-194">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="88539-194">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="88539-195">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="88539-195">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="88539-196">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="88539-196">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="88539-197">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="88539-197">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="88539-198">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="88539-198">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="88539-199">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="88539-199">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="88539-200">または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="88539-200">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="88539-201">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-201">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="88539-202">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="88539-202">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="88539-203">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="88539-203">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="88539-204">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="88539-204">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="88539-205">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="88539-205">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="88539-206">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="88539-206">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="88539-207">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-207">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="88539-208">Intel プロセッサを搭載した Surface ノート Pc 3 をサポートするには、次のフォルダーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="88539-208">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="88539-209">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="88539-209">SurfaceUpdate\IclSerialIOGPIO</span></span>
    - <span data-ttu-id="88539-210">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="88539-210">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="88539-211">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="88539-211">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="88539-212">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="88539-212">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="88539-213">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="88539-213">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="88539-214">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="88539-214">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="88539-215">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="88539-215">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="88539-216">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="88539-216">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="88539-217">Surface Pc 3 (Intel プロセッサ搭載) では、モデルは Surface ノートブック3です。</span><span class="sxs-lookup"><span data-stu-id="88539-217">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="88539-218">残りの Surface のラップトップドライバーは、「\ MDT の展開」という Drivers\Windows10\X64\Surface の [ラップトップの 3] フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="88539-218">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="88539-219">WindowsPEX64 フォルダーに、インポートしたドライバーが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="88539-219">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="88539-220">フォルダーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="88539-220">The folder should resemble the following:</span></span>  

   ![展開ワークベンチの WindowsPEX64 フォルダーに新しくインポートされたドライバーを示す画像](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="88539-222">WindowsPEX64 フォルダーを使う選択プロファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="88539-222">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="88539-223">選択プロファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="88539-223">The selection profile should resemble the following:</span></span>  

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="88539-225">新しい選択プロファイルを使用するために、MDT 展開共有の Windows PE プロパティを構成します。次のようにします。</span><span class="sxs-lookup"><span data-stu-id="88539-225">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="88539-226">**プラットフォーム**の場合は、[ **x64**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="88539-226">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="88539-227">[**選択プロファイル**] で、新しいプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="88539-227">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="88539-228">選択**プロファイルから [すべてのドライバーを含める**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="88539-228">Select **Include all drivers from the selection profile**.</span></span>
   
   ![MDT 展開共有の Windows PE プロパティを示す画像](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="88539-230">選択プロファイルまたは**DriverGroup001**変数のいずれかを使用して、残りの Surface ラップトップドライバーが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="88539-230">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="88539-231">Surface ラップトップ (第1世代) では、モデルは**Surface pc**です。</span><span class="sxs-lookup"><span data-stu-id="88539-231">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="88539-232">残りの Surface のラップトップドライバーは、このリストの後の図に示すように、[/MDT 展開] の [Drivers\Windows10\X64\Surface のラップトップ] フォルダーに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="88539-232">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="88539-233">Surface ノートブック2の場合、モデルは**Surface ノートブック 2**です。</span><span class="sxs-lookup"><span data-stu-id="88539-233">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="88539-234">残りの Surface のラップトップドライバーは、\ MDT の展開用の [Drivers\Windows10\X64\Surface] ボックスに常駐している必要があります。</span><span class="sxs-lookup"><span data-stu-id="88539-234">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="88539-235">Surface Pc 3 (Intel プロセッサ搭載) では、モデルは Surface ノートブック3です。</span><span class="sxs-lookup"><span data-stu-id="88539-235">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="88539-236">残りの Surface のラップトップドライバーは、「\ MDT の展開」という Drivers\Windows10\X64\Surface の [ラップトップの 3] フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="88539-236">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![展開ワークベンチの Surface ラップトップフォルダーの標準 Surface (第1世代) ドライバーを示す画像](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="88539-238">新しい選択プロファイルと関連設定を使用するために MDT 展開共有を構成した後、「 [mdt を使用した Windows 10 イメージの展開: 手順 6: 展開タスクシーケンスを作成](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)する」の説明に従って展開プロセスを続行します。</span><span class="sxs-lookup"><span data-stu-id="88539-238">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>
