---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
keywords: Surface Hub デスクトップ、Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: c2851505b3595ea768217de443676b45cc01a9ae
ms.sourcegitcommit: efc38524f81238e0c36371f462eb57123e46d09b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "11228558"
---
# <span data-ttu-id="9dfb6-104">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

- [<span data-ttu-id="9dfb6-105">記事のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="9dfb6-105">Article version history</span></span>](#version-history)

<span data-ttu-id="9dfb6-106">Surface Hub 2S には、Windows 10 Team がプレインストールされています。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-106">Surface Hub 2S comes preinstalled with Windows 10 Team.</span></span> <span data-ttu-id="9dfb6-107">このカスタマイズされた Windows 10 エディションは、会議室環境でのコラボレーションを容易にするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-107">This customized edition of Windows 10 is designed to facilitate collaboration in meeting room environments.</span></span> <span data-ttu-id="9dfb6-108">これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub 2S を使用するオプションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-108">Now you have the option of running Windows 10 Pro or Enterprise to use Surface Hub 2S much like any other PC.</span></span> 

> [!IMPORTANT]
><span data-ttu-id="9dfb6-109">一般的なアップグレードや移行とは異なり、このプロセスでは、この記事で説明するように、標準的な手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-109">Unlike a typical upgrade or migration, this process requires you to follow a prescriptive procedure, as described in this article.</span></span> <span data-ttu-id="9dfb6-110">続行する[前に、ソリューション コンポーネントと](#solution-components)[移行とインストールのワークフロー](#migration-and-installation-workflow-summary)を確認します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-110">Review the [Solution components](#solution-components) and [Migration and installation workflow](#migration-and-installation-workflow-summary) before you continue.</span></span>


> [!NOTE]
> <span data-ttu-id="9dfb6-111">Windows 10 Pro または Enterprise をインストールする場合は、既存の Windows 10 Team ライセンスとは別の新しいライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-111">When you install Windows 10 Pro or Enterprise, you need a new licence that's separate from your existing Windows 10 Team license.</span></span> 


<span data-ttu-id="9dfb6-112">別の PC とダウンロード可能なツール Surface UEFI コンフィケーターを使って、Windows 10 Team からの移行 *を開始します*。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-112">Start the migration from Windows 10 Team by using a separate PC and the downloadable tool *Surface UEFI Configurator*.</span></span> <span data-ttu-id="9dfb6-113">このツールを使って、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-113">Use the tool  to create a package that contains a new UEFI setting that you apply to Surface Hub 2S.</span></span>  

<span data-ttu-id="9dfb6-114">Surface UEFI コンフィエーターは、Surface Enterprise 管理モード (SEMM) へのインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-114">Surface UEFI Configurator works as an interface into Surface Enterprise Management Mode (SEMM).</span></span> <span data-ttu-id="9dfb6-115">企業環境の Surface デバイスでファームウェア設定の一元管理を容易にするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-115">It's designed to facilitate centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="9dfb6-116">詳細については <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> 、Microsoft SEMM ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-116">For more information, see the <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank">Microsoft SEMM documentation</span></span></a>
 

## <span data-ttu-id="9dfb6-117">ソリューション コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9dfb6-117">Solution components</span></span>

- <span data-ttu-id="9dfb6-118">Windows 10 Team オペレーティング システムを実行している Surface Hub 2S デバイス</span><span class="sxs-lookup"><span data-stu-id="9dfb6-118">Surface Hub 2S device running the Windows 10 Team operating system</span></span>
- <span data-ttu-id="9dfb6-119">Windows 10 を実行している個別のデバイス</span><span class="sxs-lookup"><span data-stu-id="9dfb6-119">Separate device running Windows 10</span></span>
- <span data-ttu-id="9dfb6-120">SEMM パッケージを作成する Surface UEFI 構成ツール</span><span class="sxs-lookup"><span data-stu-id="9dfb6-120">Surface UEFI Configurator tool to create the SEMM package</span></span>
- <span data-ttu-id="9dfb6-121">Windows 10 Pro または Enterprise OS イメージ バージョン 1903 以降</span><span class="sxs-lookup"><span data-stu-id="9dfb6-121">Windows 10 Pro or Enterprise OS image, version 1903 or later</span></span>
- <span data-ttu-id="9dfb6-122">16 GB のストレージ、FAT32 形式の 2 つの USB ドライブ</span><span class="sxs-lookup"><span data-stu-id="9dfb6-122">Two USB drives that have 16 GB of storage, FAT32 format</span></span>
- <span data-ttu-id="9dfb6-123">Surface Hub 2 Microsoft Windows インストーラー (MSI) ファイル上の Windows 10 Pro および Enterprise OS のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="9dfb6-123">The Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 Microsoft Windows Installer (MSI) file</span></span>
- <span data-ttu-id="9dfb6-124">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="9dfb6-124">Internet connection</span></span>
- <span data-ttu-id="9dfb6-125">イメージング ソリューション (オプション)</span><span class="sxs-lookup"><span data-stu-id="9dfb6-125">Imaging solution (optional)</span></span>

 
## <span data-ttu-id="9dfb6-126">移行とインストールのワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="9dfb6-126">Migration and installation workflow summary</span></span>

| <span data-ttu-id="9dfb6-127">ステップ</span><span class="sxs-lookup"><span data-stu-id="9dfb6-127">Step</span></span>  | <span data-ttu-id="9dfb6-128">操作</span><span class="sxs-lookup"><span data-stu-id="9dfb6-128">Action</span></span>                                                                                                 | <span data-ttu-id="9dfb6-129">まとめ</span><span class="sxs-lookup"><span data-stu-id="9dfb6-129">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="9dfb6-130">1</span><span class="sxs-lookup"><span data-stu-id="9dfb6-130">1</span></span> | [<span data-ttu-id="9dfb6-131">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-131">Verify that the UEFI version on Surface Hub 2S meets minimum requirements.</span></span>](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | <span data-ttu-id="9dfb6-132">UEFI バージョンが 694.2938.768.0 以降である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-132">Ensure the UEFI version is 694.2938.768.0 or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="9dfb6-133">2</span><span class="sxs-lookup"><span data-stu-id="9dfb6-133">2</span></span> | [<span data-ttu-id="9dfb6-134">Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-134">Download Surface UEFI Configurator and Surface Hub 2 drivers and firmware.</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="9dfb6-135">[Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> **Tools for IT] ページで、[** </a> ダウンロード] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-135">On the <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank">**Surface Tools for IT** page</a>, select **Download**.</span></span> <span data-ttu-id="9dfb6-136">次に **、Surface UEFI コンフィエーターを選択してダウンロードします。MSI ファイルを** 作成し、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-136">Then select and download the **Surface UEFI Configurator .MSI file** and install it on a separate PC.</span></span> <span data-ttu-id="9dfb6-137">Surface Hub 2 MSI ファイルに <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Windows 10 Pro および Enterprise OS のドライバーとファームウェアをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-137">Download the <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span></a> <span data-ttu-id="9dfb6-138">手順 5 で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-138">Save it for use in step 5.</span></span> |
| <span data-ttu-id="9dfb6-139">3</span><span class="sxs-lookup"><span data-stu-id="9dfb6-139">3</span></span> | [<span data-ttu-id="9dfb6-140">SEMM 証明書を準備します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-140">Prepare SEMM certificate.</span></span>](#prepare-the-semm-certificate)                                                                          | <span data-ttu-id="9dfb6-141">Surface UEFI コンフィエーターを実行するために必要な証明書を準備します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-141">Prepare the certificate that's required to run Surface UEFI Configurator.</span></span> <span data-ttu-id="9dfb6-142">または、現在の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-142">Or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="9dfb6-143">4</span><span class="sxs-lookup"><span data-stu-id="9dfb6-143">4</span></span> | [<span data-ttu-id="9dfb6-144">SEMM パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-144">Create SEMM package.</span></span>](#create-a-semm-package)                                                                               | <span data-ttu-id="9dfb6-145">Surface UEFI コンフィエーターを起動して、USB ドライブに SEMM パッケージを作成します。このパッケージには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-145">Start Surface UEFI Configurator to create a SEMM package on a USB drive, which will contain the configuration files you need to apply on Surface Hub 2S.</span></span> <span data-ttu-id="9dfb6-146">これらの SEMM パッケージ ファイルを PC 上のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-146">Copy these SEMM package files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="9dfb6-147">5</span><span class="sxs-lookup"><span data-stu-id="9dfb6-147">5</span></span> | [<span data-ttu-id="9dfb6-148">Surface Hub 2 で Windows 10 Pro および Enterprise OS 用の Windows 10 イメージ、SEMM パッケージ、ドライバーとファームウェアを含む USB フラッシュ ドライブを準備します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-148">Prepare USB flash drive that contains Windows 10 image, SEMM package, and drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2.</span></span>](#prepare-a-usb-flash-drive-that-contains-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="9dfb6-149">Windows 10 イメージを含む単一の USB ドライブを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-149">Create a single USB drive that contains a Windows 10 image.</span></span> <span data-ttu-id="9dfb6-150">この例では、ドライブの名前は *BOOTME です*。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-150">In this example, the drive is named *BOOTME*.</span></span> <span data-ttu-id="9dfb6-151">Surface Hub 2 (手順 2) と SEMM パッケージ ファイル (手順 4) で Windows 10 Pro および Enterprise OS のドライバーとファームウェアを *BOOTME* ドライブに追加します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-151">Add your drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (step 2) and SEMM package files (step 4) to the *BOOTME* drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="9dfb6-152">6</span><span class="sxs-lookup"><span data-stu-id="9dfb6-152">6</span></span> | [<span data-ttu-id="9dfb6-153">Surface Hub 2S で UEFI を更新して、OS の移行を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-153">Update UEFI on Surface Hub 2S to enable OS migration.</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="9dfb6-154">*BOOTME ドライブを使*って Surface Hub 2S を UEFI メニューで起動し、SEMM パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-154">Use the *BOOTME* drive to boot Surface Hub 2S to the UEFI menu and install the SEMM package.</span></span>|
| <span data-ttu-id="9dfb6-155">7</span><span class="sxs-lookup"><span data-stu-id="9dfb6-155">7</span></span> | [<span data-ttu-id="9dfb6-156">Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-156">Install Windows 10 Pro or Enterprise version 1903 or later.</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="9dfb6-157">*BOOTME ドライブを使*って、Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-157">Use the *BOOTME* drive to install Windows 10 Pro or Enterprise version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="9dfb6-158">8</span><span class="sxs-lookup"><span data-stu-id="9dfb6-158">8</span></span> | [<span data-ttu-id="9dfb6-159">Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 にインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-159">Install drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2.</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="9dfb6-160">デバイスに最新の更新プログラムとドライバーがインストールされている必要がある場合は、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェア <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-160">To ensure your device has all the latest updates and drivers, install the <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span></a>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="9dfb6-161">9</span><span class="sxs-lookup"><span data-stu-id="9dfb6-161">9</span></span> | [<span data-ttu-id="9dfb6-162">Surface Hub 2S を個人用生産性デバイスとして完全に構成します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-162">Fully configure Surface Hub 2S as a personal productivity device.</span></span>](#configure-recommended-settings)                                        |  <span data-ttu-id="9dfb6-163">推奨設定とアプリケーションを有効にして、個人用生産性デバイスとして Surface Hub 2S を最適化します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-163">Enable recommended settings and applications to optimize Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="9dfb6-164">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-164">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>

<span data-ttu-id="9dfb6-165">Surface Hub を Windows 10 Team から Windows 10 Desktop に移行する前に *、694.2938.768.0*以上の UEFI バージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-165">Before you migrate Surface Hub from Windows 10 Team to Windows 10 Desktop, you need a UEFI version that's at least *694.2938.768.0*.</span></span>
 
**<span data-ttu-id="9dfb6-166">システムで UEFI バージョンを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-166">To verify the UEFI version on your system:</span></span>**

1. <span data-ttu-id="9dfb6-167">Surface Hub 2S ホーム ページで、[スタート]**を選択し**、Surface アプリ (すべてのアプリの Surface)**を開**  >  **きます**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-167">On the Surface Hub 2S home page, select **Start**, and then open the Surface app (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="9dfb6-168">Surface **を選び** 、デバイス上の現在の UEFI バージョンを含む Surface Hub に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-168">Select **Your Surface** to display information about Surface Hub, including the current UEFI version on the device.</span></span> 
   - <span data-ttu-id="9dfb6-169">次の図に示すように *、UEFI バージョンが 694.2938.768.0* 以降の場合は、SEMM パッケージを作成して OS の移行を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-169">If the UEFI version is *694.2938.768.0* or later, as the following image shows, you can create the SEMM package to enable OS migration.</span></span>

       ![Surface アプリの [Your Surface] ページを示すスクリーンショット。](images/shm-fig1.png)
 
   - <span data-ttu-id="9dfb6-171">UEFI バージョンがバージョン 694.2938.768.0 より前の場合は、Window 10 Team 2020 Update Bare Metal Recovery (BMR) イメージをインストールするか、Windows Update を使用して、現在のバージョンを入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-171">If the UEFI version is earlier than version 694.2938.768.0, you will need to obtain a current version by either installing the Window 10 Team 2020 Update Bare Metal Recovery (BMR) image, or by using Windows Update.</span></span>
   
**<span data-ttu-id="9dfb6-172">Windows Update を使って UEFI を更新するには:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-172">To update UEFI via Windows Update:</span></span>**

1. <span data-ttu-id="9dfb6-173">Surface Hub 2S で、管理者としてサインイン **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-173">On your Surface Hub 2S, sign in as **Admin**.</span></span> 
    >[!Note]
    > <span data-ttu-id="9dfb6-174">ユーザー名または管理者パスワードが分からない場合は、デバイスをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-174">If you don't know your username or admin password, you'll need to reset the device.</span></span> <span data-ttu-id="9dfb6-175">詳しくは <a href="https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset" target="_blank"> 、「Surface Hub 2S のリセットと回復」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-175">For more information, see <a href="https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset" target="_blank">Reset and recovery for Surface Hub 2S.</span></span></a>

1. <span data-ttu-id="9dfb6-176">[すべてのアプリ**の設定の**  >  **更新と**  >  **セキュリティ**  >  **] Windows Update に移動し**、すべての更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-176">Go to **All apps** > **Settings** > **Update and Security** > **Windows Update**, and then install all updates.</span></span> 
1. <span data-ttu-id="9dfb6-177">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-177">Restart the device.</span></span> 
1. <span data-ttu-id="9dfb6-178">Surface アプリを使って UEFI バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-178">Verify the UEFI version by using the Surface app.</span></span> 
1. <span data-ttu-id="9dfb6-179">この時点で、UEFI バージョンがまだバージョン 694.2938.768.0 以降ではない場合は、上記の手順を繰り返し実行するか、Windows 10 Team 2020 Update Bare Metal Recovery (BMR) イメージをインストールして最新の UEFI を取得できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-179">At this point, if the UEFI version is not yet version  694.2938.768.0 or later, you can either repeat the above steps, or you can get the latest UEFI by installing the Windows 10 Team 2020 Update Bare Metal Recovery (BMR) image.</span></span>

**<span data-ttu-id="9dfb6-180">ベア メタル回復 (BMR) イメージを使用して UEFI を更新するには:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-180">To update UEFI via Bare Metal Recovery (BMR) image:</span></span>**

1.  <span data-ttu-id="9dfb6-181">Surface の回復サイト [に移動し、[Surface](https://support.microsoft.com/surfacerecoveryimage) **Hub 2S] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="9dfb6-181">Go to the [Surface recovery site](https://support.microsoft.com/surfacerecoveryimage) and select **Surface Hub 2S**</span></span>
3.  <span data-ttu-id="9dfb6-182">ハブのシリアル番号を入力します (電源接続の横のハブの背面にあります)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-182">Enter your Hub Serial Number (located on the rear side of the Hub next to the power connection.)</span></span>
4.  <span data-ttu-id="9dfb6-183">指示に従って、Windows 10 Team 2020 Update をインストールして、フォーマットされた USB ドライブにイメージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-183">Follow the directions to download the image onto a formatted USB drive through installing the Windows 10 Team 2020 Update.</span></span>
5.  <span data-ttu-id="9dfb6-184">更新が完了し、デバイスが初めて OOBE に入った後は、OOBE を完了する必要はなんか、UEFI バージョンが更新されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-184">After the update has completed and the device enters the OOBE first time setup, you do not need to complete OOBE, the UEFI version will be updated.</span></span> <span data-ttu-id="9dfb6-185">代わりに、画面がオフになるまで電源ボタンを押し続け、デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-185">Instead power down the device by holding the power button until the screen turns off.</span></span> 

### <span data-ttu-id="9dfb6-186">Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9dfb6-186">Download Surface UEFI Configurator and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="9dfb6-187">別の PC の場合:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-187">On a separate PC:</span></span>

1. <span data-ttu-id="9dfb6-188">[Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Tools for IT] ページで、[ </a> ダウンロード] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-188">On the <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Surface Tools for IT page</a>, select **Download**.</span></span>  
1. <span data-ttu-id="9dfb6-189">Surface UEFI Configurator MSI ファイルを選択してダウンロードし、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-189">Select and download the Surface UEFI Configurator MSI file and install it on a separate PC.</span></span> <span data-ttu-id="9dfb6-190">Windows 10 Team エディションがインストールされている間、Surface Hub 2S で Surface UEFI コンフィエーター ツールを実行できない。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-190">The Surface UEFI Configurator tool can't be run on a Surface Hub 2S while the Windows 10 Team edition is installed.</span></span>

1. <span data-ttu-id="9dfb6-191">Surface <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Hub 2 Drivers and Firmware Windows Installer MSI ファイルをダウンロードします </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-191">Download the <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Surface Hub 2 Drivers and Firmware Windows Installer MSI file</a>.</span></span> <span data-ttu-id="9dfb6-192">このファイルは、新しいオペレーティング システムをインストールするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-192">You'll use this file when you install the new operating system.</span></span>

### <span data-ttu-id="9dfb6-193">SEMM 証明書を準備する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-193">Prepare the SEMM certificate</span></span>

<span data-ttu-id="9dfb6-194">Surface UEFI コンフィエーターを使用したことがない場合は、証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-194">If you haven't used Surface UEFI Configurator before, you need to prepare a certificate.</span></span> <span data-ttu-id="9dfb6-195">この証明書により、デバイスを SEMM に登録した後で、承認された証明書で作成されたパッケージを使用する場合にのみ UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-195">This certificate ensures that after a device is enrolled in SEMM, you can modify UEFI settings only by using packages that are created with the approved certificate.</span></span> 

<span data-ttu-id="9dfb6-196">証明書を取得する方法は、組織の規模や複雑さによって異なります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-196">How you get a certificate depends on the size or complexity of your organization:</span></span>

- <span data-ttu-id="9dfb6-197">通常、エンタープライズ組織は、標準のセキュリティプラクティスに従って証明書を生成するための独自のインフラストラクチャを維持しています。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-197">Enterprise organizations typically maintain their own infrastructure to generate certificates according to standard security practices.</span></span>

- <span data-ttu-id="9dfb6-198">中規模企業などでは、パートナー プロバイダーから証明書を取得する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-198">Medium-sized businesses and others might choose to get certificates from partner providers.</span></span> <span data-ttu-id="9dfb6-199">このオプションは、十分な IT 専門知識や専用の IT セキュリティ チームがいない組織に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-199">This option is recommended for organizations that don't have sufficient IT expertise or a dedicated IT security team.</span></span>

- <span data-ttu-id="9dfb6-200">または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-200">Alternatively, you can generate a self-signed certificate by using a PowerShell script.</span></span> <span data-ttu-id="9dfb6-201">詳しくは <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements" target="_blank"> 、Surface Enterprise 管理モードの証明書要件に関するページをご覧ください </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-201">For more information, see the <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements" target="_blank">Surface Enterprise Management Mode certificate requirements </a>.</span></span> <span data-ttu-id="9dfb6-202">または、PowerShell を使用して独自の証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-202">Or you can use PowerShell to create your own certificate.</span></span> <span data-ttu-id="9dfb6-203">詳細については <a href="https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate" target="_blank"> 、New-SelfSignedCertificate ドキュメントを参照 </a> してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-203">For more information, see the <a href="https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate" target="_blank"> New-SelfSignedCertificate</a> documentation.</span></span>

<span data-ttu-id="9dfb6-204">Surface UEFI コンフィフィエーターが作成する SEMM パッケージは、証明書で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-204">The SEMM package that Surface UEFI Configurator creates must be secured with a certificate.</span></span> <span data-ttu-id="9dfb6-205">証明書は、UEFI 設定を適用する前に構成ファイルの署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-205">The certificate verifies the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="9dfb6-206">詳細については <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> 、SEMM ドキュメントを参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-206">For more information, see the <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> SEMM documentation</a>.</span></span>
 
 
### <span data-ttu-id="9dfb6-207">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-207">Create a SEMM package</span></span>

1. <span data-ttu-id="9dfb6-208">別の PC に、前にダウンロードした Surface UEFI コンフィエーター ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-208">On a separate PC, install the Surface UEFI Configurator tool that you downloaded earlier.</span></span> 

2. <span data-ttu-id="9dfb6-209">Surface UEFI コンフィエーターを開き、[スタート] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-209">Open Surface UEFI Configurator, and then select **Start**.</span></span>

   ![Surface UEFI コンフィエーターを開きます。](images/shm-fig2.png)
   
3. <span data-ttu-id="9dfb6-211">**[Surface デバイス] を選択し**、[次へ] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-211">Select **Surface Devices**, and then select **Next**.</span></span>

   ![[Surface デバイス] を選択します。](images/shm-fig3.png)
  
4. <span data-ttu-id="9dfb6-213">構成パッケージ **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-213">Select **Configuration Package**.</span></span>

   ![[構成パッケージ] を選択します。](images/shm-fig4.png)
  
5. <span data-ttu-id="9dfb6-215">[証明書 **の保護] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-215">Select **Certificate Protection**.</span></span>

   ![[証明書の保護] を選択します。](images/shm-fig5.png)

   <span data-ttu-id="9dfb6-217">証明書 .pfx ファイルを追加するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-217">You're prompted to add your certificate .pfx file.</span></span>

   ![証明書を追加します。](images/shm-fig6.png)
   
7. <span data-ttu-id="9dfb6-219">証明書のパスワードを入力し **、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-219">Enter your certificate password, and then select **OK**.</span></span>

   ![証明書のパスワードを入力し、[OK] を選択します。](images/shm-fig7.png)

8. <span data-ttu-id="9dfb6-221">パスワード **保護を選** び、Surface UEFI にパスワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-221">Select **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="9dfb6-222">UEFI を起動するたびに、このパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-222">You'll need this password whenever you boot to UEFI.</span></span> <span data-ttu-id="9dfb6-223">Surface \*\* Hub 2S で使用する UEFI パスワードを設定することを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-223">We *strongly recommend* that you set a UEFI password that you'll use on Surface Hub 2S.</span></span>

   ![[パスワード保護] を選択します。](images/shm-fig8.png)
   
9. <span data-ttu-id="9dfb6-225">UEFI パスワードを設定し **、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-225">Set a UEFI password, and then select **OK**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="9dfb6-226">パスワードは、Surface Hub を管理する IT 管理者がアクセスできる安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-226">Save the password in a secure location that's accessible to your IT admins who manage Surface Hub.</span></span> <span data-ttu-id="9dfb6-227">パスワードが失われた場合は、復元できません。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-227">If the password is lost, it can't be recovered.</span></span> 

   ![UEFI パスワードを入力します。](images/shm-fig9.png)

10. <span data-ttu-id="9dfb6-229">**[Surface Hub 2S] を選択し、[次**へ] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-229">Select **Surface Hub 2S**, and then select **Next**.</span></span>

    ![[Surface Hub 2S] を選択します。](images/shm-fig10.png)
   
11. <span data-ttu-id="9dfb6-231">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-231">Select **Next**.</span></span>

    ![[次へ] を選択します。](images/shm-fig10a.png)

12. <span data-ttu-id="9dfb6-233">Windows 10 Pro または Enterprise のインストールを許可するには **、EnableOsMigration**を有効にし、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-233">To allow installation of Windows 10 Pro or Enterprise, turn on **EnableOsMigration**, and then select **Next**.</span></span>

    ![[O S 移行を有効にする] を選択します。](images/shm-fig11.png)
    
    ![[OS 移行を有効にする] を [オン] に設定します。](images/shm-fig12.png)

### <span data-ttu-id="9dfb6-236">SEMM 登録の管理</span><span class="sxs-lookup"><span data-stu-id="9dfb6-236">Managing SEMM enrollment</span></span>

<span data-ttu-id="9dfb6-237">SEMM へのデバイスの登録は、今後のデバイスの管理方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-237">Enrolling devices into SEMM affects how you can manage the device going forward.</span></span> <span data-ttu-id="9dfb6-238">たとえば、SEMM パッケージを適用した後、デバイスの UEFI メニューで、すべての UEFI 設定を使用できません (ロックされています)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-238">For example, after you apply a SEMM package, in the device's UEFI menu, all UEFI settings are unavailable (locked).</span></span> <span data-ttu-id="9dfb6-239">PXE ブートの **IPv6 などのその他の設定の** 既定値も使用できません。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-239">Default values for other settings such as **IPv6 for PXE Boot** are also unavailable.</span></span> 

<span data-ttu-id="9dfb6-240">移行後に UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-240">To change UEFI settings after you finish the migration, apply another SEMM package or unenroll the device from SEMM.</span></span> <span data-ttu-id="9dfb6-241">別の SEMM パッケージを適用して UEFI 設定を変更する場合は、新しい SEMM パッケージをビルドするときに元の証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-241">If you apply another SEMM package to change the UEFI settings, you must use the original certificate when you build the new SEMM package.</span></span> <span data-ttu-id="9dfb6-242">UEFI コンフィグレータ ツールを使用し **、EnableOSMigration** をオフのままにします (元の移行手順に示すようにオンではありません)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-242">Use the UEFI Configurator tool and leave **EnableOSMigration** off (not on, as shown in the original migration steps).</span></span>

#### <span data-ttu-id="9dfb6-243">パートナーとの連携</span><span class="sxs-lookup"><span data-stu-id="9dfb6-243">Working with partners</span></span>

<span data-ttu-id="9dfb6-244">会社が Surface Hub 2 の Windows 10 Pro または Enterprise への移行をアウトソーシングしている場合は、パートナーに SEMM 証明書、SEMM パッケージ、および UEFI パスワードを転送する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-244">If your company is outsourcing the migration to Windows 10 Pro or Enterprise on Surface Hub 2, you may want to have the partner transfer the SEMM certificate, SEMM package, and UEFI password to you.</span></span>  <span data-ttu-id="9dfb6-245">または、ハブを移行した後、SEMM からすぐに登録を解除できます。この場合、UEFI のローカル管理とデバイスの別のパーティへの転送が可能になります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-245">Alternatively, after migrating the Hub, you can immediately un-enroll it from SEMM, which will allow local administration of UEFI and transfer of the device to another party.</span></span> <span data-ttu-id="9dfb6-246">それでも、移行後に構成できる UEFI パスワードを使用することを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-246">Nevertheless, it's still strongly recommended to use a UEFI password, which can be configured after migration.</span></span> <span data-ttu-id="9dfb6-247">詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://docs.microsoft.com/surface/manage-surface-uefi-settings)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-247">To learn more, see [Manage Surface UEFI settings](https://docs.microsoft.com/surface/manage-surface-uefi-settings).</span></span> 

#### <span data-ttu-id="9dfb6-248">Windows 10 Team へのロールバック</span><span class="sxs-lookup"><span data-stu-id="9dfb6-248">Rolling back to Windows 10 Team</span></span>

<span data-ttu-id="9dfb6-249">移行後に、後述するようにデバイスを Windows 10 Team[](#roll-back-to-windows-10-team)に復元する場合は、まず SEMM から Hub を登録解除してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-249">If after migrating you choose to restore your device to Windows 10 Team, [as described below](#roll-back-to-windows-10-team), it's recommended to first unenroll Hub from SEMM.</span></span> <span data-ttu-id="9dfb6-250">詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-250">To learn more, see [Unenroll Surface devices from SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).</span></span>


#### <span data-ttu-id="9dfb6-251">SEMM パッケージを USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-251">Save the SEMM package to a USB drive</span></span>

1. <span data-ttu-id="9dfb6-252">USB ドライブを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-252">Connect a USB drive to your PC.</span></span> 
1. <span data-ttu-id="9dfb6-253">[ **ハブ 2S] を選択し、[** 次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-253">Choose **Hub 2S**, and then select **Next**.</span></span>

   ![USB の選択](images/shm-fig13.png)

   > [!WARNING]
   > <span data-ttu-id="9dfb6-255">SEMM パッケージをビルドすると、USB ドライブ上のすべての既存のデータが消去されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-255">All existing data on the USB drive is erased when the SEMM package is built.</span></span> <span data-ttu-id="9dfb6-256">SEMM パッケージを作成する前に、保存する USB ドライブからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-256">Before building the SEMM package, remove any files from the USB drive that you want to save.</span></span>
   
2. <span data-ttu-id="9dfb6-257">[ビルド **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-257">Select **Build**.</span></span>

   ![[ビルド] を選択します。](images/shm-fig14.png)

3. <span data-ttu-id="9dfb6-259">このページのスクリーンショットをキャプチャし、[終了] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-259">Capture a screenshot of this page, and then select **End**.</span></span> <span data-ttu-id="9dfb6-260">SEMM パッケージの準備ができました。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-260">Your SEMM package is now ready.</span></span> <span data-ttu-id="9dfb6-261">このファイルには、SEMM パッケージ *DfciUpdate.dfi* と、SEMM 拇印 (証明書の拇印の最後の 2 文字) を含むテキスト ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-261">It contains the SEMM package *DfciUpdate.dfi* and a text file that includes the SEMM thumbprint (the last two characters of the certificate's thumbprint).</span></span>

   ![[終了] を選択します。](images/shm-fig15.png)
   
4. <span data-ttu-id="9dfb6-263">証明書の拇印の最後の 2 文字を保存します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-263">Save the certificate thumbprint's last two characters.</span></span> <span data-ttu-id="9dfb6-264">Surface Hub 2S でパッケージを適用するときに SEMM をアクティブ化するには、これらの文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-264">You'll need these characters to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="9dfb6-265">Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 のドライバーとファームウェアを含む USB フラッシュ ドライブを準備する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-265">Prepare a USB flash drive that contains a Windows 10 image, SEMM package, and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="9dfb6-266">Windows 10 Pro または Enterprise イメージ (バージョン 1903 以降) をインストールするには、次のいずれかのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-266">You can install a Windows 10 Pro or Enterprise image (version 1903 or later) by using one of the following options:</span></span>

- <span data-ttu-id="9dfb6-267">現在のイメージング ソリューション。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-267">Your current imaging solution.</span></span>

- <a href="https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator" target="_blank"> <span data-ttu-id="9dfb6-268">Surface Deployment Accelerator </a> .</span><span class="sxs-lookup"><span data-stu-id="9dfb6-268">Surface Deployment Accelerator</a>.</span></span> <span data-ttu-id="9dfb6-269">このツールを使って、起動可能な Windows 10 イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-269">Use this tool to create a bootable Windows 10 image.</span></span> <span data-ttu-id="9dfb6-270">イメージには、現在のすべての Windows 10 更新プログラム、Office、選択した他のアプリ、必要なドライバーとファームウェアを含めできます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-270">The image can include all current Windows 10 updates, Office, other apps that you choose, and the required drivers and firmware.</span></span> 

- <span data-ttu-id="9dfb6-271">Windows 10 Pro または Enterprise イメージを含む USB フラッシュ ドライブ。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-271">USB flash drive that contains a Windows 10 Pro or Enterprise image.</span></span> <span data-ttu-id="9dfb6-272">次に <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> 、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 にインストールします </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-272">Then install <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2</a>.</span></span>
 
<span data-ttu-id="9dfb6-273">次の手順では、インストール メディアから USB フラッシュ ドライブを作成し、SEMM パッケージ ファイルと Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 MSI ファイルに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-273">The following procedure describes how to create a USB flash drive from installation media, and then add the SEMM package files and the Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span> <span data-ttu-id="9dfb6-274">他の展開方法を使用している場合は [、Surface Hub 2S](#update-uefi-on-surface-hub-2s-to-enable-os-migration) の Update UEFI に移動して、この記事の OS 移行セクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-274">If you're using other deployment methods, go to the [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration) section in this article.</span></span>

> [!NOTE]
> <span data-ttu-id="9dfb6-275">インストールが完了したら、既存の Windows 10 Team ライセンスとは別に、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-275">After you finish the installation, you'll need a valid license for Windows 10 Pro or Windows 10 Enterprise that's separate from your existing Windows 10 Team license.</span></span>

1. <span data-ttu-id="9dfb6-276">Windows 10 Pro インストールを作成するには、Windows 10 のダウンロード ページで、指示に従ってメディア作成ツール <a href="https://www.microsoft.com/software-download/windows10" target="_blank"> </a> をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-276">To create a Windows 10 Pro installation, on the<a href="https://www.microsoft.com/software-download/windows10" target="_blank"> Download Windows 10</a> page, follow the instructions to download the media creation tool.</span></span> <span data-ttu-id="9dfb6-277">Windows 10 Enterprise をダウンロードするには、Microsoft ボリューム ライセンス サービス センター <a href="https://www.microsoft.com/licensing/servicecenter/default.aspx" target="_blank"> にアクセスします </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-277">To download Windows 10 Enterprise, go to the <a href="https://www.microsoft.com/licensing/servicecenter/default.aspx" target="_blank"> Microsoft Volume Licensing Service Center</a>.</span></span>

2. <span data-ttu-id="9dfb6-278">新しい USB ストレージ ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-278">Insert a new USB storage drive.</span></span> 
1. <span data-ttu-id="9dfb6-279">メディア作成ツールを開き、[インストール メディアの作成] **を**選択し、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-279">Open the media creation tool, select **Create installation media**, and then select **Next**.</span></span>

   ![インストール メディアを作成します。](images/shm-fig16.png)
   
3. <span data-ttu-id="9dfb6-281">言語を選択し **、Windows 10 と 64** ビット **(x64) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-281">Select a language, and then choose **Windows 10** and **64-bit (x64)**.</span></span> <span data-ttu-id="9dfb6-282">次に、[次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-282">Then select **Next**.</span></span>

   ![言語を選択し、Windows 10 と 64 ビットを選択します。](images/shm-fig17.png)
   
4. <span data-ttu-id="9dfb6-285">USB **フラッシュ ドライブを選択し、[** 次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-285">Select **USB flash drive**, and then select **Next**.</span></span>

   ![[U S B フラッシュ ドライブ] を選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. <span data-ttu-id="9dfb6-287">ダウンロードが完了したら、[完了] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-287">When the download finishes, select **Finish**.</span></span>

   ![[完了] を選択します。](images/shm-fig19.png)
   
6. <span data-ttu-id="9dfb6-289">SURFACE Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS の SEMM パッケージ ファイルとドライバーとファームウェアを、Windows 10 イメージを含む USB フラッシュ ドライブ *(BOOTME)* のルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-289">Copy the SEMM package files and the drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (the MSI file) to the root of the USB flash drive (*BOOTME*) that contains your Windows 10 image.</span></span> <span data-ttu-id="9dfb6-290">BOOTME USB ドライブには次が含まれる。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-290">The BOOTME USB drive contains:</span></span>

    - <span data-ttu-id="9dfb6-291">Windows 10 の起動可能なイメージ。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-291">Your Windows 10 bootable image.</span></span>
    
    - <span data-ttu-id="9dfb6-292">SEMM パッケージ ファイル (USB ドライブのルートにコピー)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-292">SEMM package files (copied to the root of the USB drive).</span></span>
    
      - <span data-ttu-id="9dfb6-293">*DfciUpdate.dfi*.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-293">*DfciUpdate.dfi*.</span></span>
      - <span data-ttu-id="9dfb6-294">SEMM 拇印を含むテキスト ファイル。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-294">Text file that includes the SEMM thumbprint.</span></span> <span data-ttu-id="9dfb6-295">(この例では、ファイルは次 *SurfaceUEFI_2020Aug25_1058.txt*です)。自動的に生成される日付のタイム スタンプは、Surface UEFI コンフィエーターを使用してファイルを作成した日付に対応します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-295">(In this example, the file is *SurfaceUEFI_2020Aug25_1058.txt*.) The automatically generated date time stamp corresponds to the date that you created the file by using Surface UEFI Configurator.</span></span>

   - <span data-ttu-id="9dfb6-296">Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-296">Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi).</span></span> <span data-ttu-id="9dfb6-297">このファイルを USB ドライブのルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-297">Copy this file to the root of the USB drive.</span></span>

### <span data-ttu-id="9dfb6-298">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="9dfb6-298">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

1. <span data-ttu-id="9dfb6-299">BOOTME ドライブを Surface Hub 2S の USB-A ポートに挿入します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-299">Insert your BOOTME drive into the USB-A port on Surface Hub 2S.</span></span> <span data-ttu-id="9dfb6-300">必要なファイルの一覧については、前のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-300">For a list of required files, see the previous section.</span></span>

2. <span data-ttu-id="9dfb6-301">UEFI を起動するには:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-301">To boot into UEFI:</span></span>

   1. <span data-ttu-id="9dfb6-302">Surface Hub 2S をオフ (シャットダウン) します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-302">Turn off (shut down) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="9dfb6-303">音量 + を **長押**しし、電源ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-303">Press and hold **Volume +**, and then press and release the power button.</span></span>
   1. <span data-ttu-id="9dfb6-304">UEFI メニュー **が表示されるまで** 、Volume + を保持し続ける。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-304">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![UEFI メニューが表示されるまで、音量を上げボタンを長押しします。](images/shm-fig20.png)
      
3. <span data-ttu-id="9dfb6-306">デバイスが再起動したら、前に作成した UEFI パスワードを入力します (該当する場合は、強く推奨)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-306">When the device restarts, enter the UEFI password that you created earlier, if applicable (strongly recommended).</span></span>

   ![UEFI パスワードを入力します。](images/shm-fig22.png)
   
4. <span data-ttu-id="9dfb6-308">UEFI メニューで、USB から **[管理**  >  **インストール] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-308">In the UEFI menu, select **Management** > **Install from USB**.</span></span>

   ![[管理] を選択し、[U S B] から [インストール] を選択します。](images/shm-fig21.png)
   
5. <span data-ttu-id="9dfb6-310">次 **の図に示すように**、[今すぐ再起動] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-310">Select **Restart now**, as the following image shows.</span></span> <span data-ttu-id="9dfb6-311">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-311">The device reboots.</span></span> <span data-ttu-id="9dfb6-312">ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-312">It displays a white Microsoft logo in the middle of the window and then shuts down.</span></span>

   ![[今すぐ再起動] を選択します。](images/shm-fig25.png)
   
6. <span data-ttu-id="9dfb6-314">電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-314">Press and release the power button.</span></span> <span data-ttu-id="9dfb6-315">表示される赤いウィンドウで、Surface Enterprise 管理モードをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-315">In the red window that appears, activate Surface Enterprise Management Mode.</span></span> 

7. <span data-ttu-id="9dfb6-316">2 文字の証明書の拇印と UEFI 設定パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-316">Enter your two-character certificate thumbprint and your UEFI settings password.</span></span> <span data-ttu-id="9dfb6-317">**[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-317">Then select **OK**.</span></span>

   ![2 文字の証明書の拇印と UEFI 設定パスワードを入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="9dfb6-319">デバイスで SEMM をアクティブ化すると、新しい UEFI 設定 **EnableOSMigration が** 適用されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-319">After you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="9dfb6-320">Windows 10 Team にアクセスできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-320">You'll no longer be able to access Windows 10 Team.</span></span> <span data-ttu-id="9dfb6-321">代わりに、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-321">Instead, you must continue to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span> 

   <span data-ttu-id="9dfb6-322">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-322">The device reboots.</span></span> <span data-ttu-id="9dfb6-323">画面の中央に白いロゴが表示され、もう一度シャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-323">It displays the white logo in the middle of the screen and then shuts down again.</span></span>

### <span data-ttu-id="9dfb6-324">Windows 10 Pro または Enterprise のインストール</span><span class="sxs-lookup"><span data-stu-id="9dfb6-324">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="9dfb6-325">起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-A ポートにまだ存在しない場合は、ここで挿入します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-325">If your bootable Windows 10 Pro or Enterprise drive isn't already in the Surface Hub 2 USB-A port, insert it now.</span></span> <span data-ttu-id="9dfb6-326">次に、電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-326">Then press and release the power button.</span></span> 

    <span data-ttu-id="9dfb6-327">デバイスが起動すると、画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-327">When the device starts, you see the white logo in the middle of the screen.</span></span> <span data-ttu-id="9dfb6-328">次に、白いロゴの下に回転する円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-328">Then you see a spinning circle below the white logo.</span></span>

3. <span data-ttu-id="9dfb6-329">デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切ります (電源コードを取り外してから、もう一方の電源を差し込む)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-329">If the device doesn't automatically boot to the USB drive, power off the device (unplug the power cord and then plug it back in).</span></span> <span data-ttu-id="9dfb6-330">電源コードを再度接続すると、数秒後にデバイスが起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-330">After you plug the power cord in again, the device should boot after a few seconds.</span></span> <span data-ttu-id="9dfb6-331">次に、画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-331">Then you'll see the white logo in the middle of screen.</span></span> 

    <span data-ttu-id="9dfb6-332">デバイスが有効でなかった場合は、電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-332">If the device doesn't turn on, press and release the power button.</span></span> <span data-ttu-id="9dfb6-333">画面の中央にロゴが表示された直後に、白いロゴの下に回転する円が表示されるまでボリューム ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-333">Immediately after you see the logo in the middle of the screen, press and hold the volume button until you see the spinning circle below the white logo.</span></span>
 
   ![U S B ドライブから Windows 10 を起動します。](images/shm-fig26.png)
   
4. <span data-ttu-id="9dfb6-335">Out-Of-Box Experience (OOBE) のセットアップが開始したら、指示に従って Windows 10 Pro または Enterprise (バージョン 1903 以降) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-335">When the out-of-box experience (OOBE) setup starts, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="9dfb6-336">Surface Hub 2 のドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="9dfb6-336">Install Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="9dfb6-337">デバイスに最新の更新プログラムとドライバーが含まれていますので、Surface Hub 2 に Windows 10 Pro および Enterprise OS のドライバーとファームウェアを <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> インストールします </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-337">To ensure your device has all the latest updates and drivers, install <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2</a>.</span></span> <span data-ttu-id="9dfb6-338">ドライバーとファームウェア MSI のインストール後、デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-338">After installation of the drivers and firmware MSI, reboot the device.</span></span> <span data-ttu-id="9dfb6-339">次に、ハブの電源を再び入れ、PC の電源を 1 時間保持し、デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-339">Then, after powering the Hub back on, keep the PC power on for an hour and reboot the device again.</span></span> <span data-ttu-id="9dfb6-340">2 回目の再起動を求めるメッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-340">You will not be prompted for the second reboot.</span></span> <span data-ttu-id="9dfb6-341">Windows 10 Pro または Enterprise に移行する前のコンピューターの状態によっては、すべてのファームウェアが更新された状態を確認するために、この 2 番目の手順が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-341">Depending on the state of your machine prior to migrating to Windows 10 Pro or Enterprise, this second step may be needed to ensure all of the firmware has been updated.</span></span>
 
## <span data-ttu-id="9dfb6-342">推奨設定を構成する</span><span class="sxs-lookup"><span data-stu-id="9dfb6-342">Configure recommended settings</span></span>

<span data-ttu-id="9dfb6-343">個人の生産性向上デバイスとして Surface Hub 2S を完全に構成するには、「Surface Hub 2 で Windows 10 Pro または Enterprise を構成する」を参照 <a href="surface-hub-2-post-install.md" target="_blank"> してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-343">To fully configure Surface Hub 2S as a personal productivity device, see <a href="surface-hub-2-post-install.md" target="_blank">Configure Windows 10 Pro or Enterprise on Surface Hub 2</a>.</span></span>

> [!NOTE]
><span data-ttu-id="9dfb6-344">この記事で説明されている手順で、デバイスを Windows 10 Pro または Enterprise for Surface Hub 2 に正常に移行できない場合は、Surface Hub サポートにお問い <a href="https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support" target="_blank"> 合わせください </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-344">If the steps outlined in this article don't successfully migrate your device to Windows 10 Pro or Enterprise for Surface Hub 2, contact <a href="https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support" target="_blank"> Surface Hub Support</a>.</span></span>

## <span data-ttu-id="9dfb6-345">Windows 10 Team にロールバックする</span><span class="sxs-lookup"><span data-stu-id="9dfb6-345">Roll back to Windows 10 Team</span></span>

<span data-ttu-id="9dfb6-346">デバイスを Windows 10 Team に復元する場合は、「Surface Hub 2S のリセットと回復」 <a href="surface-hub-2s-recover-reset.md" target="_blank"> を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-346">If you want to restore your device to Windows 10 Team, see <a href="surface-hub-2s-recover-reset.md" target="_blank"> Reset and recovery for Surface Hub 2S</a>.</span></span>

> [!NOTE]
> <span data-ttu-id="9dfb6-347">Windows 10 Team にロールバックする前に、まず SEMM から Hub を登録解除してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-347">Before rolling back to Windows 10 Team, it's recommended to first unenroll Hub from SEMM.</span></span> <span data-ttu-id="9dfb6-348">詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-348">To learn more, see [Unenroll Surface devices from SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).</span></span>

## <span data-ttu-id="9dfb6-349">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="9dfb6-349">Version history</span></span>

<span data-ttu-id="9dfb6-350">次の表に、この記事の変更点を示します。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-350">The following table summarizes changes to this article.</span></span>

| <span data-ttu-id="9dfb6-351">バージョン</span><span class="sxs-lookup"><span data-stu-id="9dfb6-351">Version</span></span> | <span data-ttu-id="9dfb6-352">日付</span><span class="sxs-lookup"><span data-stu-id="9dfb6-352">Date</span></span>               | <span data-ttu-id="9dfb6-353">説明</span><span class="sxs-lookup"><span data-stu-id="9dfb6-353">Description</span></span>                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="9dfb6-354">v.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-354">v.</span></span> <span data-ttu-id="9dfb6-355">1.4</span><span class="sxs-lookup"><span data-stu-id="9dfb6-355">1.4</span></span>  | <span data-ttu-id="9dfb6-356">2020 年 12 月 14 日</span><span class="sxs-lookup"><span data-stu-id="9dfb6-356">December 14, 2020</span></span> | <span data-ttu-id="9dfb6-357">「Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア」用の MSI ファイルのインストールに関する詳細な情報を提供します。システムの状態によっては、2 回目の再起動が必要になる場合があります。 [](#install-surface-hub-2-drivers-and-firmware)</span><span class="sxs-lookup"><span data-stu-id="9dfb6-357">Provides [further info](#install-surface-hub-2-drivers-and-firmware) about installing the MSI file for "Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2," advising that a second reboot may be necessary depending on the state of your system.</span></span>                                                          |
| <span data-ttu-id="9dfb6-358">v.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-358">v.</span></span> <span data-ttu-id="9dfb6-359">1.3</span><span class="sxs-lookup"><span data-stu-id="9dfb6-359">1.3</span></span>  | <span data-ttu-id="9dfb6-360">2020 年 12 月 3 日</span><span class="sxs-lookup"><span data-stu-id="9dfb6-360">December 3, 2020</span></span> | <span data-ttu-id="9dfb6-361">SEMM 登録の管理 [に関するガイダンスを更新しました](#managing-semm-enrollment)。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-361">Updated with guidance about [managing SEMM enrollment](#managing-semm-enrollment).</span></span>                                                       |
| <span data-ttu-id="9dfb6-362">v.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-362">v.</span></span> <span data-ttu-id="9dfb6-363">1.2</span><span class="sxs-lookup"><span data-stu-id="9dfb6-363">1.2</span></span>  | <span data-ttu-id="9dfb6-364">2020 年 9 月 29 日</span><span class="sxs-lookup"><span data-stu-id="9dfb6-364">September 29, 2020</span></span> | <span data-ttu-id="9dfb6-365">使いやすさのフィードバックに対処するその他の更新プログラム。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-365">Miscellaneous updates that address usability feedback.</span></span>                                                        |
| <span data-ttu-id="9dfb6-366">v.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-366">v.</span></span> <span data-ttu-id="9dfb6-367">1.1</span><span class="sxs-lookup"><span data-stu-id="9dfb6-367">1.1</span></span>  | <span data-ttu-id="9dfb6-368">2020 年 9 月 15 日</span><span class="sxs-lookup"><span data-stu-id="9dfb6-368">September 15, 2020</span></span> | <span data-ttu-id="9dfb6-369">新しい OS をインストールする場合のライセンス要件を明確に示す追加のメモを紹介に追加しました。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-369">Placed an additional note in the introduction that clarifies licensing requirements for installing a new OS.</span></span> |
| <span data-ttu-id="9dfb6-370">v.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-370">v.</span></span> <span data-ttu-id="9dfb6-371">1.0</span><span class="sxs-lookup"><span data-stu-id="9dfb6-371">1.0</span></span>  | <span data-ttu-id="9dfb6-372">2020 年 9 月 1 日</span><span class="sxs-lookup"><span data-stu-id="9dfb6-372">September 1, 2020</span></span>  | <span data-ttu-id="9dfb6-373">新しい記事。</span><span class="sxs-lookup"><span data-stu-id="9dfb6-373">New article.</span></span>                                                                                           |
