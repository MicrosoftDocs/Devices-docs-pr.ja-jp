---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: Surface Hub 2 の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
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
ms.openlocfilehash: d7ecee2ca66640b054efc106191d12c1844b90a1
ms.sourcegitcommit: 1bc22f7343af9b1b1b8b375d540adee2af68e693
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2021
ms.locfileid: "11297640"
---
# <span data-ttu-id="98d4a-104">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="98d4a-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

- [<span data-ttu-id="98d4a-105">記事のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="98d4a-105">Article version history</span></span>](#version-history)

<span data-ttu-id="98d4a-106">Surface Hub 2S には、Windows 10 Team がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="98d4a-106">Surface Hub 2S comes with Windows 10 Team installed.</span></span> <span data-ttu-id="98d4a-107">このカスタマイズされた Windows 10 エディションは、会議室環境でのコラボレーションを容易にします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-107">This customized edition of Windows 10 facilitates collaboration in meeting-room environments.</span></span> <span data-ttu-id="98d4a-108">代わりに、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub 2S を使用できます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-108">You can now instead run Windows 10 Pro or Enterprise to use your Surface Hub 2S much like any other PC.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98d4a-109">この移行プロセスでは、この記事で説明されている特定の手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-109">This migration process requires you to follow the specific procedure that's described in this article.</span></span> <span data-ttu-id="98d4a-110">続行する前に、ソリューション[コンポーネントと移行とインストール](#solution-components)[のワークフローを参照してください](#migration-and-installation-workflow-summary)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-110">Before you continue, read [Solution components](#solution-components) and [Migration and installation workflow](#migration-and-installation-workflow-summary).</span></span>

> [!NOTE]
> <span data-ttu-id="98d4a-111">Windows 10 Pro または Enterprise をインストールする場合は、既存の Windows 10 Team ライセンスとは別の新しいライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="98d4a-111">When you install Windows 10 Pro or Enterprise, you need a new licence that's separate from your existing Windows 10 Team license.</span></span>

<span data-ttu-id="98d4a-112">別の PC とダウンロード可能な *Surface UEFI* 構成ツールを使って、Windows 10 Team からの移行を開始します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-112">Start the migration from Windows 10 Team by using a separate PC and the downloadable *Surface UEFI Configurator* tool.</span></span> <span data-ttu-id="98d4a-113">このツールは、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-113">The tool creates a package that contains a new UEFI setting that you apply to the Surface Hub 2S.</span></span>  

<span data-ttu-id="98d4a-114">Surface UEFI コンフィエーターは、Surface Enterprise 管理モード (SEMM) へのインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-114">Surface UEFI Configurator works as an interface into Surface Enterprise Management Mode (SEMM).</span></span> <span data-ttu-id="98d4a-115">企業環境の Surface デバイスでファームウェア設定を一元的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-115">It enables centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="98d4a-116">詳しくは [、Microsoft Surface Enterprise 管理モードに関するページをご覧ください](https://docs.microsoft.com/surface/surface-enterprise-management-mode)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-116">For more information, see [Microsoft Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 
## <span data-ttu-id="98d4a-117">ソリューション コンポーネント</span><span class="sxs-lookup"><span data-stu-id="98d4a-117">Solution components</span></span>

- <span data-ttu-id="98d4a-118">Windows 10 Team を実行している Surface Hub 2S デバイス</span><span class="sxs-lookup"><span data-stu-id="98d4a-118">Surface Hub 2S device running Windows 10 Team</span></span>
- <span data-ttu-id="98d4a-119">Windows 10 を実行している個別のデバイス</span><span class="sxs-lookup"><span data-stu-id="98d4a-119">Separate device running Windows 10</span></span>
- <span data-ttu-id="98d4a-120">SEMM パッケージを作成する Surface UEFI 構成ツール</span><span class="sxs-lookup"><span data-stu-id="98d4a-120">Surface UEFI Configurator tool to create the SEMM package</span></span>
- <span data-ttu-id="98d4a-121">Windows 10 Pro または Enterprise OS イメージ バージョン 1903 以降</span><span class="sxs-lookup"><span data-stu-id="98d4a-121">Windows 10 Pro or Enterprise OS image, version 1903 or later</span></span>
- <span data-ttu-id="98d4a-122">16 GB のストレージ、FAT32 形式の 2 つの USB ドライブ</span><span class="sxs-lookup"><span data-stu-id="98d4a-122">Two USB drives that have 16 GB of storage, FAT32 format</span></span>
- <span data-ttu-id="98d4a-123">Surface Hub 2 Microsoft Windows インストーラー (MSI) ファイルの Windows 10 Pro および Enterprise のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="98d4a-123">The drivers and firmware for Windows 10 Pro and Enterprise in a Surface Hub 2 Microsoft Windows Installer (MSI) file</span></span>
- <span data-ttu-id="98d4a-124">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="98d4a-124">Internet connection</span></span>
- <span data-ttu-id="98d4a-125">イメージング ソリューション (オプション)</span><span class="sxs-lookup"><span data-stu-id="98d4a-125">Imaging solution (optional)</span></span>
 
## <span data-ttu-id="98d4a-126">移行とインストールのワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="98d4a-126">Migration and installation workflow summary</span></span>

| <span data-ttu-id="98d4a-127">ステップ</span><span class="sxs-lookup"><span data-stu-id="98d4a-127">Step</span></span>  | <span data-ttu-id="98d4a-128">操作</span><span class="sxs-lookup"><span data-stu-id="98d4a-128">Action</span></span>                                                                                                 | <span data-ttu-id="98d4a-129">要約</span><span class="sxs-lookup"><span data-stu-id="98d4a-129">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="98d4a-130">1</span><span class="sxs-lookup"><span data-stu-id="98d4a-130">1</span></span> | <span data-ttu-id="98d4a-131">[Surface Hub 2S で UEFI バージョンを確認します](#verify-the-uefi-version-on-surface-hub-2s)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-131">[Verify the UEFI version on the Surface Hub 2S](#verify-the-uefi-version-on-surface-hub-2s).</span></span>                                  | <span data-ttu-id="98d4a-132">UEFI バージョンはバージョン *694.2938.768.0 以降である* 必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-132">The UEFI version must be version *694.2938.768.0* or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="98d4a-133">2</span><span class="sxs-lookup"><span data-stu-id="98d4a-133">2</span></span> | [<span data-ttu-id="98d4a-134">Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-134">Download Surface UEFI Configurator and the Surface Hub 2 drivers and firmware.</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="98d4a-135">[Surface **[Tools for IT] ページで、[](https://www.microsoft.com/download/details.aspx?id=46703)** </a> ダウンロード] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-135">On the **[Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703)** page</a>, select **Download**.</span></span> <span data-ttu-id="98d4a-136">次に **、Surface UEFI Configurator MSI**ファイルを選択してダウンロードし、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-136">Then select and download the **Surface UEFI Configurator MSI file**, and install it on a separate PC.</span></span> <span data-ttu-id="98d4a-137">[また、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェアをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-137">Also download the [Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span></a> <span data-ttu-id="98d4a-138">手順 5 で使用するためにこのパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-138">Save this package for use in step 5.</span></span> |
| <span data-ttu-id="98d4a-139">3</span><span class="sxs-lookup"><span data-stu-id="98d4a-139">3</span></span> | [<span data-ttu-id="98d4a-140">SEMM 証明書を準備します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-140">Prepare the SEMM certificate.</span></span>](#prepare-the-semm-certificate)                                                                          | <span data-ttu-id="98d4a-141">Surface UEFI コンフィエーターを実行するために必要な証明書を準備するか、現在の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-141">Prepare the certificate that's required to run Surface UEFI Configurator, or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="98d4a-142">4</span><span class="sxs-lookup"><span data-stu-id="98d4a-142">4</span></span> | [<span data-ttu-id="98d4a-143">SEMM パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-143">Create a SEMM package.</span></span>](#create-a-semm-package)                                                                               | <span data-ttu-id="98d4a-144">Surface UEFI コンフィエーターを起動して、USB ドライブに SEMM パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-144">Start Surface UEFI Configurator to create a SEMM package on a USB drive.</span></span> <span data-ttu-id="98d4a-145">このパッケージには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-145">This package will contain the configuration files you need to apply on Surface Hub 2S.</span></span> <span data-ttu-id="98d4a-146">これらの SEMM パッケージ ファイルを PC 上のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-146">Copy these SEMM package files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="98d4a-147">5</span><span class="sxs-lookup"><span data-stu-id="98d4a-147">5</span></span> | [<span data-ttu-id="98d4a-148">Windows 10 イメージ、SEMM パッケージ、ドライバーとファームウェアを含む USB フラッシュ ドライブを読み込む。</span><span class="sxs-lookup"><span data-stu-id="98d4a-148">Load a USB flash drive with Windows 10 image, the SEMM package, and drivers and firmware.</span></span>](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="98d4a-149">Windows 10 イメージを含む USB ドライブを作成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-149">Create a USB drive that contains a Windows 10 image.</span></span> <span data-ttu-id="98d4a-150">この例では、ドライブの名前は *BOOTME です*。</span><span class="sxs-lookup"><span data-stu-id="98d4a-150">In this example, the drive is named *BOOTME*.</span></span> <span data-ttu-id="98d4a-151">Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (手順 2 から) と SEMM パッケージ ファイル (手順 4 から) を *BOOTME* ドライブに追加します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-151">Add the drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (from step 2) and the SEMM package files (from step 4) to the *BOOTME* drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="98d4a-152">6</span><span class="sxs-lookup"><span data-stu-id="98d4a-152">6</span></span> | [<span data-ttu-id="98d4a-153">Surface Hub 2S の UEFI を更新して、OS の移行を有効にします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-153">Update the UEFI on the Surface Hub 2S to enable OS migration.</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="98d4a-154">*BOOTME ドライブを使*って Surface Hub 2S を UEFI メニューで起動し、SEMM パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-154">Use the *BOOTME* drive to boot the Surface Hub 2S to the UEFI menu and install the SEMM package.</span></span>|
| <span data-ttu-id="98d4a-155">7</span><span class="sxs-lookup"><span data-stu-id="98d4a-155">7</span></span> | [<span data-ttu-id="98d4a-156">Windows 10 Pro または Enterprise をインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-156">Install Windows 10 Pro or Enterprise.</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="98d4a-157">*BOOTME ドライブを使*って、Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-157">Use the *BOOTME* drive to install Windows 10 Pro or Enterprise version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="98d4a-158">8</span><span class="sxs-lookup"><span data-stu-id="98d4a-158">8</span></span> | [<span data-ttu-id="98d4a-159">Windows 10 Pro と Enterprise のドライバーとファームウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-159">Install drivers and firmware for Windows 10 Pro and Enterprise.</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="98d4a-160">デバイスに最新の更新プログラムとドライバーがインストールされている必要がある場合は、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェアをインストール <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-160">To ensure that your device has all the latest updates and drivers, install the <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span></a>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="98d4a-161">9</span><span class="sxs-lookup"><span data-stu-id="98d4a-161">9</span></span> | [<span data-ttu-id="98d4a-162">Surface Hub 2S を個人の生産性向上デバイスとして構成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-162">Configure Surface Hub 2S as a personal productivity device.</span></span>](#configure-recommended-settings)                                        |  <span data-ttu-id="98d4a-163">推奨される設定とアプリケーションを有効にして、個人の生産性デバイスとして Surface Hub 2S を最適化します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-163">Enable the recommended settings and applications to optimize Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="98d4a-164">Surface Hub 2S で UEFI バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="98d4a-164">Verify the UEFI version on Surface Hub 2S</span></span>

<span data-ttu-id="98d4a-165">Surface Hub を Windows 10 Team から Windows 10 Desktop に移行する前に *、UEFI バージョン 694.2938.768.0* 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="98d4a-165">Before you migrate Surface Hub from Windows 10 Team to Windows 10 Desktop, you need UEFI version *694.2938.768.0* or later.</span></span>
 
**<span data-ttu-id="98d4a-166">システムで UEFI バージョンを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-166">To verify the UEFI version on your system:</span></span>**

1. <span data-ttu-id="98d4a-167">Surface Hub 2S ホーム ページで、[スタート]**を選択し**、Surface アプリ (すべてのアプリの Surface)**を開**  >  **きます**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-167">On the Surface Hub 2S home page, select **Start**, and then open the Surface app (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="98d4a-168">Surface **を選び** 、デバイス上の現在の UEFI バージョンを含む Surface Hub に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-168">Select **Your Surface** to display information about Surface Hub, including the current UEFI version on the device.</span></span> 
   - <span data-ttu-id="98d4a-169">次の図に示すように *、UEFI バージョンが 694.2938.768.0* 以降の場合は、SEMM パッケージを作成して OS の移行を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-169">If the UEFI version is *694.2938.768.0* or later, as the following image shows, you can create the SEMM package to enable OS migration.</span></span>

       ![Screenshot shows the "Your Surface" page in the Surface app.](images/shm-fig1.png)
 
   - <span data-ttu-id="98d4a-171">UEFI バージョンが *バージョン 694.2938.768.0*より前の場合は、次のいずれかの方法を使用して新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-171">If the UEFI version is earlier than version *694.2938.768.0*, use one of the following methods to get a newer version</span></span>
   
#### <span data-ttu-id="98d4a-172">Windows Update による UEFI の更新</span><span class="sxs-lookup"><span data-stu-id="98d4a-172">Update UEFI via Windows Update</span></span>

1. <span data-ttu-id="98d4a-173">Surface Hub 2S で、管理者としてサインイン **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-173">On your Surface Hub 2S, sign in as **Admin**.</span></span>

    >[!Note]
    > <span data-ttu-id="98d4a-174">ユーザー名または管理者パスワードが分からない場合は、デバイスをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-174">If you don't know your user name or admin password, you'll need to reset the device.</span></span> <span data-ttu-id="98d4a-175">詳しくは [、「Surface Hub 2S のリセットと回復」をご覧ください](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-175">For more information, see [Reset and recovery for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span></span>

1. <span data-ttu-id="98d4a-176">[すべてのアプリ**の設定の**  >  **更新と**  >  **セキュリティ**  >  **の Windows Update] に移動し**、すべての更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-176">Go to **All apps** > **Settings** > **Update and Security** > **Windows Update**, and install all updates.</span></span>
1. <span data-ttu-id="98d4a-177">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-177">Restart the device.</span></span>
1. <span data-ttu-id="98d4a-178">Surface アプリを使って UEFI バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-178">Verify the UEFI version by using the Surface app.</span></span> <span data-ttu-id="98d4a-179">UEFI バージョンが *バージョン 694.2938.768.0* 以降ではない場合は、これらの手順を繰り返します。または、次の手順を使用して最新の UEFI バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-179">If the UEFI version isn't version *694.2938.768.0* or later, repeat these steps, or use the following procedure to get the latest UEFI version.</span></span>

#### <span data-ttu-id="98d4a-180">ベア メタル回復 (BMR) イメージを使用して UEFI を更新する</span><span class="sxs-lookup"><span data-stu-id="98d4a-180">Update the UEFI via bare metal recovery (BMR) image</span></span>

1.  <span data-ttu-id="98d4a-181">Surface の回復サイト [に移動し、Surface](https://support.microsoft.com/surfacerecoveryimage) **Hub 2S を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-181">Go to the [Surface recovery site](https://support.microsoft.com/surfacerecoveryimage) and select **Surface Hub 2S**.</span></span>
3.  <span data-ttu-id="98d4a-182">ハブのシリアル番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-182">Enter your Hub serial number.</span></span> <span data-ttu-id="98d4a-183">電源接続の横のハブの背面に位置します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-183">It's located on the back of the Hub next to the power connection.</span></span>
4.  <span data-ttu-id="98d4a-184">指示に従って、Windows 10 Team 2020 Update をインストールして、フォーマットされた USB ドライブにイメージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-184">Follow the directions to download the image onto a formatted USB drive by installing the Windows 10 Team 2020 Update.</span></span>
5.  <span data-ttu-id="98d4a-185">更新後、デバイスは Out-Of-Box-Experience (OOBE) セットアップに入った。</span><span class="sxs-lookup"><span data-stu-id="98d4a-185">After the update, the device enters out-of-box-experience (OOBE) setup.</span></span> <span data-ttu-id="98d4a-186">セットアップを完了する必要はない。</span><span class="sxs-lookup"><span data-stu-id="98d4a-186">You don't need to complete setup.</span></span> <span data-ttu-id="98d4a-187">UEFI バージョンは既に更新されています。</span><span class="sxs-lookup"><span data-stu-id="98d4a-187">The UEFI version is already updated.</span></span> <span data-ttu-id="98d4a-188">代わりに、画面がオフになるまで電源ボタンを押し続け、デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-188">Instead power down the device by holding the power button until the screen turns off.</span></span>

### <span data-ttu-id="98d4a-189">Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="98d4a-189">Download Surface UEFI Configurator and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="98d4a-190">別の PC で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-190">On a separate PC, follow these steps:</span></span>

1. <span data-ttu-id="98d4a-191">[Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Tools for IT] ページで、[ </a> ダウンロード] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-191">On the <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Surface Tools for IT page</a>, select **Download**.</span></span>  
1. <span data-ttu-id="98d4a-192">Surface UEFI Configurator MSI ファイルを選択してダウンロードし、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-192">Select and download the Surface UEFI Configurator MSI file, and install it on a separate PC.</span></span> <span data-ttu-id="98d4a-193">Windows 10 Team エディションのインストール中は、Surface Hub 2S で Surface UEFI コンフィエーター ツールを実行できない。</span><span class="sxs-lookup"><span data-stu-id="98d4a-193">The Surface UEFI Configurator tool can't be run on a Surface Hub 2S while Windows 10 Team edition is installed.</span></span>

1. <span data-ttu-id="98d4a-194">Surface [Hub 2 のドライバーとファームウェアの Windows インストーラー MSI ファイルをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-194">Download the [Surface Hub 2 drivers and firmware Windows Installer MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span> <span data-ttu-id="98d4a-195">このファイルは、新しいオペレーティング システムをインストールするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-195">You'll use this file when you install the new operating system.</span></span>

### <span data-ttu-id="98d4a-196">SEMM 証明書を準備する</span><span class="sxs-lookup"><span data-stu-id="98d4a-196">Prepare the SEMM certificate</span></span>

<span data-ttu-id="98d4a-197">Surface UEFI コンフィエーターを使用したことがない場合は、証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-197">If you haven't used Surface UEFI Configurator before, you need to prepare a certificate.</span></span> <span data-ttu-id="98d4a-198">この証明書により、デバイスを SEMM に登録した後で、承認された証明書で作成されたパッケージを使用する場合にのみ UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-198">This certificate ensures that after a device is enrolled in SEMM, you can modify UEFI settings only by using packages that are created with the approved certificate.</span></span>

<span data-ttu-id="98d4a-199">証明書を取得する方法は、組織の規模や複雑さによって異なります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-199">How you get a certificate depends on the size or complexity of your organization:</span></span>

- <span data-ttu-id="98d4a-200">通常、エンタープライズ組織は、標準のセキュリティプラクティスに従って証明書を生成するための独自のインフラストラクチャを維持しています。</span><span class="sxs-lookup"><span data-stu-id="98d4a-200">Enterprise organizations typically maintain their own infrastructure to generate certificates according to standard security practices.</span></span>

- <span data-ttu-id="98d4a-201">中規模企業や他の企業は、多くの場合、パートナー プロバイダーから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-201">Medium-sized businesses and others often choose to get certificates from partner providers.</span></span> <span data-ttu-id="98d4a-202">このオプションは、IT の専門知識があまりない組織や、専用の IT セキュリティ チームがいない組織に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-202">This option is recommended for organizations that don't have as much IT expertise or lack a dedicated IT security team.</span></span>

- <span data-ttu-id="98d4a-203">または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-203">Alternatively, you can generate a self-signed certificate by using a PowerShell script.</span></span> <span data-ttu-id="98d4a-204">詳しくは [、Surface Enterprise 管理モードの証明書要件に関するページをご覧ください](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-204">For more information, see the [Surface Enterprise Management Mode certificate requirements](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span> <span data-ttu-id="98d4a-205">または、PowerShell を使用して独自の証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-205">Or you can use PowerShell to create your own certificate.</span></span> <span data-ttu-id="98d4a-206">詳細については [、New-SelfSignedCertificate ドキュメントを参照](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-206">For more information, see the [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) documentation.</span></span>

<span data-ttu-id="98d4a-207">Surface UEFI コンフィフィエーターが作成する SEMM パッケージは、証明書で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-207">The SEMM package that Surface UEFI Configurator creates must be secured with a certificate.</span></span> <span data-ttu-id="98d4a-208">証明書は、UEFI 設定を適用する前に構成ファイルの署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-208">The certificate verifies the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="98d4a-209">詳細については [、SEMM ドキュメントを参照](https://docs.microsoft.com/surface/surface-enterprise-management-mode) してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-209">For more information, see the [SEMM](https://docs.microsoft.com/surface/surface-enterprise-management-mode) documentation.</span></span>
 
### <span data-ttu-id="98d4a-210">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="98d4a-210">Create a SEMM package</span></span>

1. <span data-ttu-id="98d4a-211">別の PC に、前にダウンロードした Surface UEFI コンフィエーター ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-211">On a separate PC, install the Surface UEFI Configurator tool that you downloaded earlier.</span></span>

1. <span data-ttu-id="98d4a-212">Surface UEFI コンフィエーターを開き、[スタート] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-212">Open Surface UEFI Configurator, and then select **Start**.</span></span>

   ![Surface UEFI コンフィエーターのスタート画面。](images/shm-fig2.png)
   
1. <span data-ttu-id="98d4a-214">**[Surface デバイス] を選択し**、[次へ] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-214">Select **Surface Devices**, and then select **Next**.</span></span>

   ![スクリーン ショットは、選択されている Surface Devices オプションを示しています。](images/shm-fig3.png)
  
1. <span data-ttu-id="98d4a-216">構成パッケージ **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-216">Select **Configuration Package**.</span></span>

   ![Screenshot shows "Select Configuration Package" selected.](images/shm-fig4.png)
  
1. <span data-ttu-id="98d4a-218">[証明書 **の保護] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-218">Select **Certificate Protection**.</span></span>

   ![Screenshot shows were to choose "Select Certificate Protection".](images/shm-fig5.png)

   <span data-ttu-id="98d4a-220">証明書 .pfx ファイルを追加するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-220">You'll be prompted to add your certificate .pfx file.</span></span>

   ![スクリーンショットは、証明書ファイルを追加する場所を示しています。](images/shm-fig6.png)
   
1. <span data-ttu-id="98d4a-222">証明書のパスワードを入力し **、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-222">Enter your certificate password, and then select **OK**.</span></span>

   ![Screenshot shows fields to enter and confirm your certificate password.](images/shm-fig7.png)

1. <span data-ttu-id="98d4a-224">パスワード **保護を選** び、Surface UEFI にパスワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-224">Select **Password Protection** to add a password to the Surface UEFI.</span></span> <span data-ttu-id="98d4a-225">UEFI を起動するたびに、このパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="98d4a-225">You'll need this password whenever you boot to the UEFI.</span></span> *<span data-ttu-id="98d4a-226">Surface Hub 2S で使用する UEFI パスワードを設定することを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-226">We strongly recommend that you set a UEFI password that you'll use on Surface Hub 2S.</span></span>*

   ![Screenshot shows where to select Password Protection.](images/shm-fig8.png)
   
1. <span data-ttu-id="98d4a-228">UEFI パスワードを設定し **、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-228">Set a UEFI password, and then select **OK**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="98d4a-229">パスワードは、Surface Hub を管理する IT 管理者がアクセスできる安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-229">Save the password in a secure location that's accessible to your IT admins who manage Surface Hub.</span></span> *<span data-ttu-id="98d4a-230">このパスワードが失われた場合は、復元できません。</span><span class="sxs-lookup"><span data-stu-id="98d4a-230">If this password is lost, it can't be recovered.</span></span>*

   ![Screenshot shows where you set the UEFI password.](images/shm-fig9.png)

1. <span data-ttu-id="98d4a-232">**[Surface Hub 2S] を選択し、[次**へ] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-232">Select **Surface Hub 2S**, and then select **Next**.</span></span>

    ![Screenshot shows where to select Surface Hub 2S.](images/shm-fig10.png)
   
1. <span data-ttu-id="98d4a-234">もう一 **度 [次へ] を選択** します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-234">Select **Next** again.</span></span>

    ![Screenshot shows to select Next under "Choose which components".](images/shm-fig10a.png)

1. <span data-ttu-id="98d4a-236">Windows 10 Pro または Enterprise のインストールを許可するには **、EnableOsMigration**を有効にし、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-236">To allow installation of Windows 10 Pro or Enterprise, turn on **EnableOsMigration**, and then select **Next**.</span></span>

    ![Screenshot shows where to select Enable O S Migration.](images/shm-fig11.png)
    
    ![Screenshot shows where to set Enable OS Migration to on.](images/shm-fig12.png)

### <span data-ttu-id="98d4a-239">SEMM 登録を管理する</span><span class="sxs-lookup"><span data-stu-id="98d4a-239">Manage SEMM enrollment</span></span>

<span data-ttu-id="98d4a-240">SEMM へのデバイスの登録は、デバイスの管理方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-240">Enrolling a device into SEMM affects how you can manage it.</span></span> <span data-ttu-id="98d4a-241">たとえば、SEMM パッケージを適用すると、デバイスの UEFI メニューですべての UEFI 設定が使用できなくなった (ロックされます)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-241">For example, after you apply a SEMM package, all UEFI settings are unavailable (locked) in the device's UEFI menu.</span></span> <span data-ttu-id="98d4a-242">PXE ブートの **IPv6 などのその他の設定の** 既定値も使用できません。</span><span class="sxs-lookup"><span data-stu-id="98d4a-242">Default values for other settings such as **IPv6 for PXE Boot** are also unavailable.</span></span>

<span data-ttu-id="98d4a-243">移行後に UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-243">To change UEFI settings after you finish the migration, apply another SEMM package or unenroll the device from SEMM.</span></span> <span data-ttu-id="98d4a-244">別の SEMM パッケージを適用して UEFI 設定を変更する場合は、新しい SEMM パッケージをビルドするときに元の証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-244">If you apply another SEMM package to change the UEFI settings, you must use the original certificate when you build the new SEMM package.</span></span> <span data-ttu-id="98d4a-245">UEFI コンフィグレータ ツールを使用し **、EnableOSMigration**を*オフのままにします*(元の移行手順ではオンではありません)。 \*\*</span><span class="sxs-lookup"><span data-stu-id="98d4a-245">Use the UEFI Configurator tool and leave **EnableOSMigration** *off* (not *on* as in the original migration steps).</span></span>

#### <span data-ttu-id="98d4a-246">パートナーと連携する場合</span><span class="sxs-lookup"><span data-stu-id="98d4a-246">If you work with partners</span></span>

<span data-ttu-id="98d4a-247">会社が Surface Hub 2 の Windows 10 Pro または Enterprise への移行をアウトソーシングしている場合は、パートナーに SEMM 証明書、SEMM パッケージ、UEFI パスワードを転送する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-247">If your company outsources the Surface Hub 2 migration to Windows 10 Pro or Enterprise, you may want to have the partner transfer the SEMM certificate, SEMM package, and UEFI password to you.</span></span> <span data-ttu-id="98d4a-248">または、ハブを移行した後、SEMM からすぐに登録を解除できます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-248">Or, after you migrate the Hub, you can immediately unenroll it from SEMM.</span></span> <span data-ttu-id="98d4a-249">この手順では、UEFI のローカル管理とデバイスの別のパーティへの転送を有効にします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-249">This step enables local administration of UEFI and transfer of the device to another party.</span></span> <span data-ttu-id="98d4a-250">ただし、移行後に構成できる UEFI パスワードを使用することを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-250">But we still strongly recommend that you use a UEFI password, which can be configured after migration.</span></span> <span data-ttu-id="98d4a-251">詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://docs.microsoft.com/surface/manage-surface-uefi-settings)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-251">To learn more, see [Manage Surface UEFI settings](https://docs.microsoft.com/surface/manage-surface-uefi-settings).</span></span> 

#### <span data-ttu-id="98d4a-252">Windows 10 Team にロールバックする</span><span class="sxs-lookup"><span data-stu-id="98d4a-252">To roll back to Windows 10 Team</span></span>

<span data-ttu-id="98d4a-253">この記事で後述するように、移行後にデバイスを Windows 10 Team に復元する場合は、まず SEMM から Hub を登録解除することをお勧めします。 [](#to-roll-back-to-windows-10-team)</span><span class="sxs-lookup"><span data-stu-id="98d4a-253">If you choose to restore your device to Windows 10 Team after the migration [as described later in this article](#to-roll-back-to-windows-10-team), we recommend that you first unenroll Hub from SEMM.</span></span> <span data-ttu-id="98d4a-254">詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-254">To learn more, see [Unenroll Surface devices from SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).</span></span>

#### <span data-ttu-id="98d4a-255">SEMM パッケージを USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="98d4a-255">Save the SEMM package to a USB drive</span></span>

1. <span data-ttu-id="98d4a-256">USB ドライブを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-256">Connect a USB drive to your PC.</span></span>
1. <span data-ttu-id="98d4a-257">[ **ハブ 2S] を選択し、[** 次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-257">Choose **Hub 2S**, and then select **Next**.</span></span>

   ![Screenshot shows where to select Hub 2S](images/shm-fig13.png)

   > [!WARNING]
   > <span data-ttu-id="98d4a-259">SEMM パッケージをビルドすると、USB ドライブ上のすべての既存のデータが消去されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-259">All existing data on the USB drive will be erased when the SEMM package is built.</span></span> <span data-ttu-id="98d4a-260">SEMM パッケージをビルドする前に、USB ドライブから必要なファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-260">Before you build the SEMM package, remove any files that you need from the USB drive.</span></span>
   
1. <span data-ttu-id="98d4a-261">[ビルド **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-261">Select **Build**.</span></span>

   ![Screenshot shows where to select Build.](images/shm-fig14.png)

1. <span data-ttu-id="98d4a-263">このページのスクリーンショットをキャプチャし、[終了] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-263">Capture a screenshot of this page, and then select **End**.</span></span> <span data-ttu-id="98d4a-264">SEMM パッケージの準備ができました。</span><span class="sxs-lookup"><span data-stu-id="98d4a-264">Your SEMM package is now ready.</span></span> <span data-ttu-id="98d4a-265">このファイルには、SEMM パッケージ *DfciUpdate.dfi* と、証明書の拇印の最後の 2 文字である *SEMM*拇印を含むテキスト ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-265">It contains the SEMM package *DfciUpdate.dfi* and a text file that includes the SEMM *thumbprint*, which is the last two characters of the certificate's thumbprint.</span></span>

   ![Screenshot shows where to select End.](images/shm-fig15.png)
   
4. <span data-ttu-id="98d4a-267">証明書の拇印の最後の 2 文字を保存します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-267">Save the certificate thumbprint's last two characters.</span></span> <span data-ttu-id="98d4a-268">Surface Hub 2S でパッケージを適用するときに SEMM をアクティブ化するには、これらの文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="98d4a-268">You'll need these characters to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="98d4a-269">Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 のドライバーとファームウェアを使って USB フラッシュ ドライブを読み込む</span><span class="sxs-lookup"><span data-stu-id="98d4a-269">Load a USB flash drive with a Windows 10 image, SEMM package, and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="98d4a-270">Windows 10 Pro または Enterprise イメージ (バージョン *1903* 以降) をインストールするには、次のいずれかのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-270">You can install a Windows 10 Pro or Enterprise image (version *1903* or later) by using one of the following options:</span></span>

- <span data-ttu-id="98d4a-271">現在のイメージング ソリューション。</span><span class="sxs-lookup"><span data-stu-id="98d4a-271">Your current imaging solution.</span></span>

- <span data-ttu-id="98d4a-272">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator).</span><span class="sxs-lookup"><span data-stu-id="98d4a-272">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator).</span></span> <span data-ttu-id="98d4a-273">このツールを使って、起動可能な Windows 10 イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-273">Use this tool to create a bootable Windows 10 image.</span></span> <span data-ttu-id="98d4a-274">イメージには、現在のすべての Windows 10 更新プログラム、Microsoft Office、その他のアプリ、および必要なドライバーとファームウェアを含めできます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-274">The image can include all current Windows 10 updates, Microsoft Office, other apps, and the required drivers and firmware.</span></span>

- <span data-ttu-id="98d4a-275">Windows 10 Pro または Enterprise イメージを含む USB フラッシュ ドライブ。</span><span class="sxs-lookup"><span data-stu-id="98d4a-275">A USB flash drive that contains a Windows 10 Pro or Enterprise image.</span></span> <span data-ttu-id="98d4a-276">次に、Surface Hub 2 に [Windows 10 Pro と Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) のドライバーとファームウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-276">Then install [drivers and firmware for Windows 10 Pro and Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) on Surface Hub 2.</span></span>
 
<span data-ttu-id="98d4a-277">次の手順は、インストール メディアから USB フラッシュ ドライブを作成し、SEMM パッケージ ファイル、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 MSI ファイルに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98d4a-277">The following steps show how to create a USB flash drive from installation media and then add the SEMM package files and the drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span> <span data-ttu-id="98d4a-278">別の展開方法を使用する場合は [、Surface Hub 2S](#update-uefi-on-surface-hub-2s-to-enable-os-migration) の Update UEFI に移動して、この記事の OS 移行セクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-278">If you use another deployment method, go to the [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="98d4a-279">インストールが完了したら、既存の Windows 10 Team ライセンスとは別に、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="98d4a-279">After you finish the installation, you'll need a valid license for Windows 10 Pro or Windows 10 Enterprise that's separate from your existing Windows 10 Team license.</span></span>

1. <span data-ttu-id="98d4a-280">Windows 10 Pro インストールを作成するには、Windows 10 のダウンロードでメディア作成ツールをダウンロードする手順 [に従います](https://www.microsoft.com/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-280">To create a Windows 10 Pro installation, follow the instructions to download the media creation tool at [Download Windows 10](https://www.microsoft.com/software-download/windows10).</span></span> <span data-ttu-id="98d4a-281">Windows 10 Enterprise をダウンロードするには、Microsoft ボリューム ライセンス サービス センター [にアクセスします](https://www.microsoft.com/licensing/servicecenter/default.aspx)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-281">To download Windows 10 Enterprise, go to the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).</span></span>

1. <span data-ttu-id="98d4a-282">新しい USB ストレージ ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-282">Insert a new USB storage drive.</span></span>
1. <span data-ttu-id="98d4a-283">メディア作成ツールを開き、[インストール メディアの作成] **を**選択し、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-283">Open the media creation tool, select **Create installation media**, and then select **Next**.</span></span>

   ![スクリーンショットは、インストール メディアを作成するオプションを示しています。](images/shm-fig16.png)
   
3. <span data-ttu-id="98d4a-285">言語を選択し **、Windows 10 と 64** ビット **(x64) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-285">Select a language, and then select **Windows 10** and **64-bit (x64)**.</span></span> <span data-ttu-id="98d4a-286">次に、[次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-286">Then select **Next**.</span></span>

   ![Screenshot shows where you select the language, O S edition, and architecture type.](images/shm-fig17.png)
   
4. <span data-ttu-id="98d4a-288">USB **フラッシュ ドライブを選択し、[** 次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-288">Select **USB flash drive**, and then select **Next**.</span></span>

   ![Screenshot shows where to select U S B flash drive.](images/shm-fig18.png)
   
5. <span data-ttu-id="98d4a-290">ダウンロードが完了したら、[完了] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-290">When the download finishes, select **Finish**.</span></span>

   ![画面は、U S B ドライブの準備が完了したと報告し、[完了] ボタンが含まれています。](images/shm-fig19.png)
   
6. <span data-ttu-id="98d4a-292">SURFACE Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS の SEMM パッケージ ファイルとドライバーとファームウェアを、Windows 10 イメージを含む USB フラッシュ ドライブ *(BOOTME)* のルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-292">Copy the SEMM package files and the drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (the MSI file) to the root of the USB flash drive (*BOOTME*) that contains your Windows 10 image.</span></span> <span data-ttu-id="98d4a-293">BOOTME USB ドライブには、次の情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-293">The BOOTME USB drive will contain:</span></span>

    - <span data-ttu-id="98d4a-294">Windows 10 の起動可能なイメージ。</span><span class="sxs-lookup"><span data-stu-id="98d4a-294">Your Windows 10 bootable image.</span></span>
    
    - <span data-ttu-id="98d4a-295">SEMM パッケージ ファイル。USB ドライブのルートにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-295">The SEMM package files, copied to the root of the USB drive:</span></span>
    
      - <span data-ttu-id="98d4a-296">*DfciUpdate.dfi*.</span><span class="sxs-lookup"><span data-stu-id="98d4a-296">*DfciUpdate.dfi*.</span></span>
      - <span data-ttu-id="98d4a-297">SEMM 拇印を含むテキスト ファイル。</span><span class="sxs-lookup"><span data-stu-id="98d4a-297">A text file that includes the SEMM thumbprint.</span></span> <span data-ttu-id="98d4a-298">(この例では、ファイルは次 *SurfaceUEFI_2020Aug25_1058.txt*です)。自動的に生成される日付とタイム スタンプは、Surface UEFI コンフィエーターを使用してファイルを作成した日付に対応します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-298">(In this example, the file is *SurfaceUEFI_2020Aug25_1058.txt*.) The automatically generated date-time stamp corresponds to the date that you created the file by using Surface UEFI Configurator.</span></span>

   - <span data-ttu-id="98d4a-299">Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-299">The drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi).</span></span> <span data-ttu-id="98d4a-300">このファイルを USB ドライブのルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-300">Copy this file to the root of the USB drive.</span></span>

### <span data-ttu-id="98d4a-301">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="98d4a-301">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

1. <span data-ttu-id="98d4a-302">BOOTME ドライブを Surface Hub 2S の USB-A ポートに挿入します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-302">Insert your BOOTME drive into the USB-A port on the Surface Hub 2S.</span></span> <span data-ttu-id="98d4a-303">必要なコンテンツの一覧については、前のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-303">For a list of its required contents, see the previous section.</span></span>

1. <span data-ttu-id="98d4a-304">UEFI を起動するには:</span><span class="sxs-lookup"><span data-stu-id="98d4a-304">To boot into UEFI:</span></span>

   1. <span data-ttu-id="98d4a-305">Surface Hub 2S をオフ (シャットダウン) します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-305">Turn off (shut down) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="98d4a-306">音量 + を **長押**しし、電源ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-306">Press and hold **Volume +**, and then press and release the power button.</span></span> <span data-ttu-id="98d4a-307">UEFI メニュー **が表示されるまで** 、Volume + を保持し続ける。</span><span class="sxs-lookup"><span data-stu-id="98d4a-307">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![図面には、音量ボタンと電源ボタンが表示されます。](images/shm-fig20.png)
      
3. <span data-ttu-id="98d4a-309">デバイスが再起動したら、前に作成した UEFI パスワードを入力します (該当する場合は推奨)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-309">When the device restarts, enter the UEFI password that you created earlier, if applicable (recommended).</span></span>

   ![システム パスワード画面。](images/shm-fig22.png)
   
4. <span data-ttu-id="98d4a-311">UEFI メニューから [管理] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-311">From the UEFI menu, select **Management**.</span></span> <span data-ttu-id="98d4a-312">次に  **、[USB からインストール] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-312">Then select  **Install from USB**.</span></span>

   ![Screenshot shows where to select Management and then "Install from U S B".](images/shm-fig21.png)
   
5. <span data-ttu-id="98d4a-314">次 **の図に示すように**、[今すぐ再起動] を選択します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-314">Select **Restart now**, as the following image shows.</span></span> <span data-ttu-id="98d4a-315">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-315">The device will restart.</span></span> <span data-ttu-id="98d4a-316">ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-316">It will display a white Microsoft logo in the middle of the window and then shut down.</span></span>

   ![Screenshot shows a message prompting you to restart.](images/shm-fig25.png)
   
6. <span data-ttu-id="98d4a-318">電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-318">Press and release the power button.</span></span> <span data-ttu-id="98d4a-319">表示される赤いダイアログ ボックスで、Surface Enterprise 管理モードのアクティブ化を選択します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-319">In the red dialog box that appears, choose to activate Surface Enterprise Management Mode.</span></span>

7. <span data-ttu-id="98d4a-320">2 文字の証明書の拇印と UEFI 設定パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-320">Enter your two-character certificate thumbprint and your UEFI settings password.</span></span> <span data-ttu-id="98d4a-321">**[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="98d4a-321">Then select **OK**.</span></span>

   ![Screenshot shows the confirm-activation dialog box where you enter your two-character certificate thumbprint and your UEFI settings password.](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="98d4a-323">デバイスで SEMM をアクティブ化すると、新しい UEFI 設定 **EnableOSMigration が** 適用されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-323">After you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="98d4a-324">Windows 10 Team にアクセスできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="98d4a-324">You can no longer access Windows 10 Team.</span></span> <span data-ttu-id="98d4a-325">代わりに、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98d4a-325">Instead, you must continue to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span>

   <span data-ttu-id="98d4a-326">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-326">The device reboots.</span></span> <span data-ttu-id="98d4a-327">画面の中央に白いロゴが表示され、もう一度シャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-327">It displays the white logo in the middle of the screen and then shuts down again.</span></span>

### <span data-ttu-id="98d4a-328">Windows 10 Pro または Enterprise のインストール</span><span class="sxs-lookup"><span data-stu-id="98d4a-328">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="98d4a-329">起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-A ポートにまだ存在しない場合は、ここで挿入します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-329">If your bootable Windows 10 Pro or Enterprise drive isn't already in the Surface Hub 2 USB-A port, insert it now.</span></span> <span data-ttu-id="98d4a-330">次に、電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-330">Then press and release the power button.</span></span>

    <span data-ttu-id="98d4a-331">デバイスが起動すると、画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-331">When the device starts, you'll see the white logo in the middle of the screen.</span></span> <span data-ttu-id="98d4a-332">次に、回転する円が白いロゴの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-332">Then a spinning circle appears below the white logo.</span></span>

3. <span data-ttu-id="98d4a-333">Surface デバイスが自動的に USB ドライブを起動しない場合は、デバイスの電源を切ります (電源コードを取り外してから、もう一方の電源を差し込む)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-333">If the Surface device doesn't automatically boot to the USB drive, power off the device (unplug the power cord and then plug it back in).</span></span> <span data-ttu-id="98d4a-334">電源コードを再度接続すると、数秒後にデバイスが起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-334">After you plug in the power cord again, the device should boot after a few seconds.</span></span> <span data-ttu-id="98d4a-335">次に、画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-335">Then you'll see the white logo in the middle of screen.</span></span>

    <span data-ttu-id="98d4a-336">デバイスが有効でなかった場合は、電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-336">If the device doesn't turn on, press and release the power button.</span></span> <span data-ttu-id="98d4a-337">画面の中央にロゴが表示された直後に、白いロゴの下に回転する円が表示されるまでボリューム ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-337">Immediately after you see the logo in the middle of the screen, press and hold the volume button until you see the spinning circle below the white logo.</span></span>
 
   ![音量ボタンと電源ボタンの画像。](images/shm-fig26.png)
   
4. <span data-ttu-id="98d4a-339">Out-Of-Box Experience (OOBE) のセットアップが開始したら、指示に従って Windows 10 Pro または Enterprise (バージョン 1903 以降) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-339">When the out-of-box experience (OOBE) setup starts, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="98d4a-340">Surface Hub 2 のドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="98d4a-340">Install Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="98d4a-341">Surface Hub 2 を最新の情報に更新するには [、Windows 10 Pro](https://www.microsoft.com/download/details.aspx?id=101974)と Enterprise のドライバーとファームウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="98d4a-341">To ensure that your Surface Hub 2 is up to date, install [drivers and firmware for Windows 10 Pro and Enterprise](https://www.microsoft.com/download/details.aspx?id=101974).</span></span> <span data-ttu-id="98d4a-342">その後、デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-342">Then reboot the device.</span></span> <span data-ttu-id="98d4a-343">Surface を 1 時間有効にし、再起動します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-343">Keep the Surface turned on for an hour, and then reboot it again.</span></span> <span data-ttu-id="98d4a-344">2 回目の再起動を求めるメッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="98d4a-344">You won't be prompted for the second reboot.</span></span> <span data-ttu-id="98d4a-345">この一時停止と追加の再起動により、ファームウェアが完全に更新されます。</span><span class="sxs-lookup"><span data-stu-id="98d4a-345">This pause and extra reboot ensures that the firmware has been fully updated.</span></span>
 
## <span data-ttu-id="98d4a-346">推奨設定を構成する</span><span class="sxs-lookup"><span data-stu-id="98d4a-346">Configure recommended settings</span></span>

<span data-ttu-id="98d4a-347">個人の生産性向上デバイスとして Surface Hub 2S を構成するには [、「Surface Hub 2 で Windows 10 Pro または Enterprise](surface-hub-2-post-install.md)を構成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-347">To configure Surface Hub 2S as a personal productivity device, see [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).</span></span>

> [!NOTE]
><span data-ttu-id="98d4a-348">この記事で説明されている手順に従って、デバイスを Windows 10 Pro または Enterprise for Surface Hub 2 に正常に移行できない場合は [、Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)サポートにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-348">If you can't successfully migrate your device to Windows 10 Pro or Enterprise for Surface Hub 2 by following the steps outlined in this article, contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="98d4a-349">Windows 10 Team にロールバックする</span><span class="sxs-lookup"><span data-stu-id="98d4a-349">To roll back to Windows 10 Team</span></span>

<span data-ttu-id="98d4a-350">デバイスを Windows 10 Team に復元する場合は [、「Surface Hub 2S](surface-hub-2s-recover-reset.md)のリセットと回復」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-350">If you want to restore your device to Windows 10 Team, see [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span>

> [!NOTE]
> <span data-ttu-id="98d4a-351">Windows 10 Team にロールバックする前に、まず SEMM から Surface Hub を登録解除してください。</span><span class="sxs-lookup"><span data-stu-id="98d4a-351">Before you roll back to Windows 10 Team, we recommended that you first unenroll the Surface Hub from SEMM.</span></span> <span data-ttu-id="98d4a-352">詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-352">To learn more, see [Unenroll Surface devices from SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).</span></span>

## <span data-ttu-id="98d4a-353">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="98d4a-353">Version history</span></span>

<span data-ttu-id="98d4a-354">次の表に、この記事の変更点を示します。</span><span class="sxs-lookup"><span data-stu-id="98d4a-354">The following table summarizes changes to this article.</span></span>

| <span data-ttu-id="98d4a-355">バージョン</span><span class="sxs-lookup"><span data-stu-id="98d4a-355">Version</span></span> | <span data-ttu-id="98d4a-356">日付</span><span class="sxs-lookup"><span data-stu-id="98d4a-356">Date</span></span>               | <span data-ttu-id="98d4a-357">説明</span><span class="sxs-lookup"><span data-stu-id="98d4a-357">Description</span></span>                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="98d4a-358">v.</span><span class="sxs-lookup"><span data-stu-id="98d4a-358">v.</span></span> <span data-ttu-id="98d4a-359">1.4</span><span class="sxs-lookup"><span data-stu-id="98d4a-359">1.4</span></span>  | <span data-ttu-id="98d4a-360">2020 年 12 月 14 日</span><span class="sxs-lookup"><span data-stu-id="98d4a-360">December 14, 2020</span></span> | <span data-ttu-id="98d4a-361">「Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア」用の MSI ファイルのインストールに関する詳細な情報を提供します。システムの状態によっては、2 回目の再起動が必要になる場合があります。 [](#install-surface-hub-2-drivers-and-firmware)</span><span class="sxs-lookup"><span data-stu-id="98d4a-361">Provides [further info](#install-surface-hub-2-drivers-and-firmware) about installing the MSI file for "Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2," advising that a second reboot may be necessary depending on the state of your system.</span></span>                                                          |
| <span data-ttu-id="98d4a-362">v.</span><span class="sxs-lookup"><span data-stu-id="98d4a-362">v.</span></span> <span data-ttu-id="98d4a-363">1.3</span><span class="sxs-lookup"><span data-stu-id="98d4a-363">1.3</span></span>  | <span data-ttu-id="98d4a-364">2020 年 12 月 3 日</span><span class="sxs-lookup"><span data-stu-id="98d4a-364">December 3, 2020</span></span> | <span data-ttu-id="98d4a-365">SEMM 登録の管理 [に関するガイダンスを更新しました](#manage-semm-enrollment)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-365">Updated with guidance about [managing SEMM enrollment](#manage-semm-enrollment).</span></span>                                                       |
| <span data-ttu-id="98d4a-366">v.</span><span class="sxs-lookup"><span data-stu-id="98d4a-366">v.</span></span> <span data-ttu-id="98d4a-367">1.2</span><span class="sxs-lookup"><span data-stu-id="98d4a-367">1.2</span></span>  | <span data-ttu-id="98d4a-368">2020 年 9 月 29 日</span><span class="sxs-lookup"><span data-stu-id="98d4a-368">September 29, 2020</span></span> | <span data-ttu-id="98d4a-369">使いやすさのフィードバックに対処するその他の更新プログラム。</span><span class="sxs-lookup"><span data-stu-id="98d4a-369">Miscellaneous updates that address usability feedback.</span></span>                                                        |
| <span data-ttu-id="98d4a-370">v.</span><span class="sxs-lookup"><span data-stu-id="98d4a-370">v.</span></span> <span data-ttu-id="98d4a-371">1.1</span><span class="sxs-lookup"><span data-stu-id="98d4a-371">1.1</span></span>  | <span data-ttu-id="98d4a-372">2020 年 9 月 15 日</span><span class="sxs-lookup"><span data-stu-id="98d4a-372">September 15, 2020</span></span> | <span data-ttu-id="98d4a-373">新しい OS をインストールする場合のライセンス要件を明確に示す追加のメモを紹介に追加しました。</span><span class="sxs-lookup"><span data-stu-id="98d4a-373">Placed an additional note in the introduction that clarifies licensing requirements for installing a new OS.</span></span> |
| <span data-ttu-id="98d4a-374">v.</span><span class="sxs-lookup"><span data-stu-id="98d4a-374">v.</span></span> <span data-ttu-id="98d4a-375">1.0</span><span class="sxs-lookup"><span data-stu-id="98d4a-375">1.0</span></span>  | <span data-ttu-id="98d4a-376">2020 年 9 月 1 日</span><span class="sxs-lookup"><span data-stu-id="98d4a-376">September 1, 2020</span></span>  | <span data-ttu-id="98d4a-377">新しい記事。</span><span class="sxs-lookup"><span data-stu-id="98d4a-377">New article.</span></span>                                                                                           |
