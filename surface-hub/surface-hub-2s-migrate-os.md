---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 上の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
keywords: Surface Hub デスクトップ、Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 713bd2e76f144b4dca7c0fad5c584b06ea12b0b5
ms.sourcegitcommit: 3ca1d1bc77452acca914d0af03e252ee260ebf1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "11154136"
---
# <span data-ttu-id="8e3b3-104">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

<span data-ttu-id="8e3b3-105">Surface Hub 2S は、Windows 10 チームにプレインストールされています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-105">Surface Hub 2S comes preinstalled with Windows 10 Team.</span></span> <span data-ttu-id="8e3b3-106">この Windows 10 のカスタマイズされたエディションは、会議室環境での共同作業を容易にするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-106">This customized edition of Windows 10 is designed to facilitate collaboration in meeting room environments.</span></span> <span data-ttu-id="8e3b3-107">これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub の2S を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-107">Now you have the option of running Windows 10 Pro or Enterprise to use Surface Hub 2S much like any other PC.</span></span> 

> [!IMPORTANT]
><span data-ttu-id="8e3b3-108">通常のアップグレードや移行とは異なり、このプロセスでは、この記事で説明するように、規範となる手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-108">Unlike a typical upgrade or migration, this process requires you to follow a prescriptive procedure, as described in this article.</span></span> <span data-ttu-id="8e3b3-109">続行する前に、 [ソリューションのコンポーネント](#solution-components) と [移行とインストールのワークフロー](#migration-and-installation-workflow-summary) を確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-109">Review the [Solution components](#solution-components) and [Migration and installation workflow](#migration-and-installation-workflow-summary) before you continue.</span></span>


> [!NOTE]
> <span data-ttu-id="8e3b3-110">Windows 10 Pro または Enterprise をインストールする場合、既存の Windows 10 チームライセンスとは別の新しいライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-110">When you install Windows 10 Pro or Enterprise, you need a new licence that's separate from your existing Windows 10 Team license.</span></span> 


<span data-ttu-id="8e3b3-111">別の PC とダウンロード可能なツール *SURFACE UEFI コンフィギュレーター*を使用して、Windows 10 チームからの移行を開始します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-111">Start the migration from Windows 10 Team by using a separate PC and the downloadable tool *Surface UEFI Configurator*.</span></span> <span data-ttu-id="8e3b3-112">このツールを使用して、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-112">Use the tool  to create a package that contains a new UEFI setting that you apply to Surface Hub 2S.</span></span>  

<span data-ttu-id="8e3b3-113">Surface UEFI コンフィギュレーターは、Surface Enterprise 管理モード (SEMM) のインターフェイスとして動作します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-113">Surface UEFI Configurator works as an interface into Surface Enterprise Management Mode (SEMM).</span></span> <span data-ttu-id="8e3b3-114">企業環境の Surface デバイスでのファームウェア設定の一元管理を容易にするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-114">It's designed to facilitate centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="8e3b3-115">詳細については、「 [Microsoft SEMM ドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-115">For more information, see the [Microsoft SEMM documentation](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 

## <span data-ttu-id="8e3b3-116">ソリューションのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="8e3b3-116">Solution components</span></span>

- <span data-ttu-id="8e3b3-117">Windows 10 Team オペレーティングシステムを実行している Surface Hub 2S デバイス</span><span class="sxs-lookup"><span data-stu-id="8e3b3-117">Surface Hub 2S device running the Windows 10 Team operating system</span></span>
- <span data-ttu-id="8e3b3-118">Windows 10 を実行している別のデバイス</span><span class="sxs-lookup"><span data-stu-id="8e3b3-118">Separate device running Windows 10</span></span>
- <span data-ttu-id="8e3b3-119">SEMM パッケージを作成するための Surface UEFI コンフィギュレーターツール</span><span class="sxs-lookup"><span data-stu-id="8e3b3-119">Surface UEFI Configurator tool to create the SEMM package</span></span>
- <span data-ttu-id="8e3b3-120">Windows 10 Pro または Enterprise OS イメージ、バージョン1903以降</span><span class="sxs-lookup"><span data-stu-id="8e3b3-120">Windows 10 Pro or Enterprise OS image, version 1903 or later</span></span>
- <span data-ttu-id="8e3b3-121">16 GB の記憶域を持つ2つの USB ドライブ、FAT32 形式</span><span class="sxs-lookup"><span data-stu-id="8e3b3-121">Two USB drives that have 16 GB of storage, FAT32 format</span></span>
- <span data-ttu-id="8e3b3-122">Surface Hub 2 の Microsoft Windows Installer (MSI) ファイル上の Windows 10 Pro および Enterprise OS 用のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="8e3b3-122">The Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 Microsoft Windows Installer (MSI) file</span></span>
- <span data-ttu-id="8e3b3-123">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="8e3b3-123">Internet connection</span></span>
- <span data-ttu-id="8e3b3-124">イメージングソリューション (オプション)</span><span class="sxs-lookup"><span data-stu-id="8e3b3-124">Imaging solution (optional)</span></span>

 
## <span data-ttu-id="8e3b3-125">移行とインストールワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="8e3b3-125">Migration and installation workflow summary</span></span>

| <span data-ttu-id="8e3b3-126">ステップ</span><span class="sxs-lookup"><span data-stu-id="8e3b3-126">Step</span></span>  | <span data-ttu-id="8e3b3-127">操作</span><span class="sxs-lookup"><span data-stu-id="8e3b3-127">Action</span></span>                                                                                                 | <span data-ttu-id="8e3b3-128">まとめ</span><span class="sxs-lookup"><span data-stu-id="8e3b3-128">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8e3b3-129">件</span><span class="sxs-lookup"><span data-stu-id="8e3b3-129">1</span></span> | [<span data-ttu-id="8e3b3-130">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-130">Verify that the UEFI version on Surface Hub 2S meets minimum requirements.</span></span>](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | <span data-ttu-id="8e3b3-131">UEFI バージョンが694.2938.768.0 以降であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-131">Ensure the UEFI version is 694.2938.768.0 or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="8e3b3-132">両面</span><span class="sxs-lookup"><span data-stu-id="8e3b3-132">2</span></span> | [<span data-ttu-id="8e3b3-133">Surface UEFI コンフィギュレーターおよび Surface Hub 2 のドライバーとファームウェアをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-133">Download Surface UEFI Configurator and Surface Hub 2 drivers and firmware.</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="8e3b3-134">[ [**Surface Tools FOR IT**](https://www.microsoft.com/download/details.aspx?id=46703) ] ページで、[ **ダウンロード**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-134">On the [**Surface Tools for IT**](https://www.microsoft.com/download/details.aspx?id=46703) page, select **Download**.</span></span> <span data-ttu-id="8e3b3-135">次に、Surface UEFI コンフィギュレーターを選択してダウンロードし **ます。MSI ファイル** を別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-135">Then select and download the **Surface UEFI Configurator .MSI file** and install it on a separate PC.</span></span> <span data-ttu-id="8e3b3-136">[Surface Hub 2 MSI ファイル上の Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-136">Download the [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span> <span data-ttu-id="8e3b3-137">手順5で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-137">Save it for use in step 5.</span></span> |
| <span data-ttu-id="8e3b3-138">-</span><span class="sxs-lookup"><span data-stu-id="8e3b3-138">3</span></span> | [<span data-ttu-id="8e3b3-139">SEMM 証明書を準備します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-139">Prepare SEMM certificate.</span></span>](#prepare-the-semm-certificate)                                                                          | <span data-ttu-id="8e3b3-140">Surface UEFI コンフィギュレーターの実行に必要な証明書を準備します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-140">Prepare the certificate that's required to run Surface UEFI Configurator.</span></span> <span data-ttu-id="8e3b3-141">または、現在の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-141">Or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="8e3b3-142">4d</span><span class="sxs-lookup"><span data-stu-id="8e3b3-142">4</span></span> | [<span data-ttu-id="8e3b3-143">SEMM パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-143">Create SEMM package.</span></span>](#create-a-semm-package)                                                                               | <span data-ttu-id="8e3b3-144">開始 Surface UEFI コンフィギュレーターを使用して、USB ドライブ上に SEMM パッケージを作成します。これには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-144">Start Surface UEFI Configurator to create a SEMM package on a USB drive, which will contain the configuration files you need to apply on Surface Hub 2S.</span></span> <span data-ttu-id="8e3b3-145">これらの SEMM パッケージファイルを PC 上のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-145">Copy these SEMM package files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="8e3b3-146">個</span><span class="sxs-lookup"><span data-stu-id="8e3b3-146">5</span></span> | [<span data-ttu-id="8e3b3-147">Windows 10 のイメージ、SEMM パッケージ、および Windows 10 Pro とエンタープライズ OS 用の windows 10 Pro およびドライバーとファームウェアを含む USB フラッシュドライブを Surface Hub 2 で準備します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-147">Prepare USB flash drive that contains Windows 10 image, SEMM package, and drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2.</span></span>](#prepare-a-usb-flash-drive-that-contains-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="8e3b3-148">Windows 10 イメージを含む USB ドライブを1つ作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-148">Create a single USB drive that contains a Windows 10 image.</span></span> <span data-ttu-id="8e3b3-149">この例では、ドライブは *Bootme*という名前になっています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-149">In this example, the drive is named *BOOTME*.</span></span> <span data-ttu-id="8e3b3-150">Surface Hub 2 (手順 2) と SEMM パッケージファイル (手順 4) に Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアを *Bootme* ドライブに追加します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-150">Add your drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (step 2) and SEMM package files (step 4) to the *BOOTME* drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="8e3b3-151">=</span><span class="sxs-lookup"><span data-stu-id="8e3b3-151">6</span></span> | [<span data-ttu-id="8e3b3-152">OS の移行を有効にするには、Surface Hub 2S で UEFI を更新します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-152">Update UEFI on Surface Hub 2S to enable OS migration.</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="8e3b3-153">*Bootme*ドライブを使って、[UEFI] メニューに Surface Hub 2s を起動し、semm パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-153">Use the *BOOTME* drive to boot Surface Hub 2S to the UEFI menu and install the SEMM package.</span></span>|
| <span data-ttu-id="8e3b3-154">日</span><span class="sxs-lookup"><span data-stu-id="8e3b3-154">7</span></span> | [<span data-ttu-id="8e3b3-155">Windows 10 Pro または Enterprise バージョン1903以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-155">Install Windows 10 Pro or Enterprise version 1903 or later.</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="8e3b3-156">*Bootme*ドライブを使用して、Windows 10 Pro または Enterprise バージョン1903以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-156">Use the *BOOTME* drive to install Windows 10 Pro or Enterprise version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="8e3b3-157">個</span><span class="sxs-lookup"><span data-stu-id="8e3b3-157">8</span></span> | [<span data-ttu-id="8e3b3-158">Surface Hub 2 で Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-158">Install drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2.</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="8e3b3-159">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 MSI ファイルに Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-159">To ensure your device has all the latest updates and drivers, install the [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="8e3b3-160">ファイブ</span><span class="sxs-lookup"><span data-stu-id="8e3b3-160">9</span></span> | [<span data-ttu-id="8e3b3-161">パーソナルの生産性向上デバイスとして Surface Hub 2S を完全に構成します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-161">Fully configure Surface Hub 2S as a personal productivity device.</span></span>](#configure-recommended-settings)                                        |  <span data-ttu-id="8e3b3-162">推奨される設定とアプリケーションを有効にして、個人用の生産性デバイスとして Surface Hub の2S を最適化します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-162">Enable recommended settings and applications to optimize Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="8e3b3-163">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-163">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>

<span data-ttu-id="8e3b3-164">Surface Hub を Windows 10 Team から Windows 10 デスクトップに移行する前に、少なくとも *694.2938.768.0*の UEFI バージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-164">Before you migrate Surface Hub from Windows 10 Team to Windows 10 Desktop, you need a UEFI version that's at least *694.2938.768.0*.</span></span>
 
<span data-ttu-id="8e3b3-165">システムの UEFI バージョンを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-165">To verify the UEFI version on your system:</span></span>

1. <span data-ttu-id="8e3b3-166">Surface Hub 2s のホームページで、[**開始**] を選び、surface アプリ ([**すべてのアプリ**]  >  **サーフェス**) を開きます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-166">On the Surface Hub 2S home page, select **Start**, and then open the Surface app (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="8e3b3-167">**Surface**を選択して、デバイス上の現在の UEFI バージョンなど、surface Hub に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-167">Select **Your Surface** to display information about Surface Hub, including the current UEFI version on the device.</span></span> 
   - <span data-ttu-id="8e3b3-168">UEFI バージョンが *694.2938.768.0* 以降の場合は、次の図に示すように、semm パッケージを作成して OS の移行を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-168">If the UEFI version is *694.2938.768.0* or later, as the following image shows, you can create the SEMM package to enable OS migration.</span></span>

       ![Surface アプリの Surface ページを示すスクリーンショット。](images/shm-fig1.png)
 
   - <span data-ttu-id="8e3b3-170">UEFI バージョンが *694.2938.768.0*より前のバージョンである場合は、Windows Update を使用して現在のバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-170">If the UEFI version is earlier than *694.2938.768.0*, get a current version by using Windows Update.</span></span>

<span data-ttu-id="8e3b3-171">Windows Update を使用して UEFI を更新するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-171">To update the UEFI by using Windows Update:</span></span>

1. <span data-ttu-id="8e3b3-172">Surface Hub 2S で、 **管理者**としてサインインします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-172">On your Surface Hub 2S, sign in as **Admin**.</span></span> 
    >[!Note]
    > <span data-ttu-id="8e3b3-173">ユーザー名または管理者パスワードがわからない場合は、デバイスをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-173">If you don't know your username or admin password, you'll need to reset the device.</span></span> <span data-ttu-id="8e3b3-174">詳細については、「 [Surface Hub 2s のリセットと回復](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-174">For more information, see [Reset and recovery for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span></span>

1. <span data-ttu-id="8e3b3-175">[**すべてのアプリ**  >  **設定**  >  の**更新とセキュリティ**  >  **Windows Update**] に移動して、すべての更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-175">Go to **All apps** > **Settings** > **Update and Security** > **Windows Update**, and then install all updates.</span></span> 
1. <span data-ttu-id="8e3b3-176">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-176">Restart the device.</span></span> 
1. <span data-ttu-id="8e3b3-177">Surface アプリを使用して、UEFI バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-177">Verify the UEFI version by using the Surface app.</span></span> 
2. <span data-ttu-id="8e3b3-178">UEFI バージョンが *694.2938.768.0* 以降になるまで、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-178">Repeat these steps until the UEFI version is *694.2938.768.0* or later.</span></span>
3. <span data-ttu-id="8e3b3-179">複数回試行しても更新された UEFI が表示されない場合は、 **更新履歴** を確認して、失敗したファームウェアインストールのインスタンスを探してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-179">If you don't see the updated UEFI after multiple attempts, check **Update History** and look for any instances of failed firmware installations.</span></span> <span data-ttu-id="8e3b3-180">デバイスをリセットする必要がある場合があります (**設定**  >  **更新 & セキュリティ**  >  **リセットデバイス**)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-180">You might need to reset your device (**Settings** > **Update & security** > **Reset device**).</span></span>

### <span data-ttu-id="8e3b3-181">ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="8e3b3-181">Download Surface UEFI Configurator and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="8e3b3-182">別の PC では、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-182">On a separate PC:</span></span>

1. <span data-ttu-id="8e3b3-183">[ [Surface Tools FOR IT] ページ](https://www.microsoft.com/download/details.aspx?id=46703)で、[ **ダウンロード**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-183">On the [Surface Tools for IT page](https://www.microsoft.com/download/details.aspx?id=46703), select **Download**.</span></span>  
1. <span data-ttu-id="8e3b3-184">Surface UEFI コンフィギュレーター MSI ファイルを選択してダウンロードし、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-184">Select and download the Surface UEFI Configurator MSI file and install it on a separate PC.</span></span> <span data-ttu-id="8e3b3-185">Surface UEFI コンフィギュレーターツールは、Windows 10 Team edition がインストールされているときに Surface Hub 2S で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-185">The Surface UEFI Configurator tool can't be run on a Surface Hub 2S while the Windows 10 Team edition is installed.</span></span>

1. <span data-ttu-id="8e3b3-186">[Surface Hub 2 ドライバーとファームウェア Windows インストーラー MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-186">Download the [Surface Hub 2 Drivers and Firmware Windows Installer MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span> <span data-ttu-id="8e3b3-187">このファイルは、新しいオペレーティングシステムをインストールするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-187">You'll use this file when you install the new operating system.</span></span>

### <span data-ttu-id="8e3b3-188">SEMM 証明書を準備する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-188">Prepare the SEMM certificate</span></span>

<span data-ttu-id="8e3b3-189">Surface UEFI コンフィギュレーターを以前に使用していない場合は、証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-189">If you haven't used Surface UEFI Configurator before, you need to prepare a certificate.</span></span> <span data-ttu-id="8e3b3-190">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージを使用してのみ UEFI 設定を変更できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-190">This certificate ensures that after a device is enrolled in SEMM, you can modify UEFI settings only by using packages that are created with the approved certificate.</span></span> 

<span data-ttu-id="8e3b3-191">証明書を取得する方法は、組織の規模または複雑さによって異なります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-191">How you get a certificate depends on the size or complexity of your organization:</span></span>

- <span data-ttu-id="8e3b3-192">通常、エンタープライズ組織は、標準セキュリティの慣行に従って証明書を生成するために独自のインフラストラクチャを維持します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-192">Enterprise organizations typically maintain their own infrastructure to generate certificates according to standard security practices.</span></span>

- <span data-ttu-id="8e3b3-193">中規模企業や他のユーザーが、パートナープロバイダーから証明書を取得することを選択する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-193">Medium-sized businesses and others might choose to get certificates from partner providers.</span></span> <span data-ttu-id="8e3b3-194">十分な IT 専門知識を持っていない組織や専用の IT セキュリティチームの場合は、このオプションをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-194">This option is recommended for organizations that don't have sufficient IT expertise or a dedicated IT security team.</span></span>

- <span data-ttu-id="8e3b3-195">または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-195">Alternatively, you can generate a self-signed certificate by using a PowerShell script.</span></span> <span data-ttu-id="8e3b3-196">詳細については、「 [Surface Enterprise 管理モードの証明書の要件](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-196">For more information, see the [Surface Enterprise Management Mode certificate requirements](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span> <span data-ttu-id="8e3b3-197">または、PowerShell を使用して独自の証明書を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-197">Or you can use PowerShell to create your own certificate.</span></span> <span data-ttu-id="8e3b3-198">詳しくは、 [新しい自己 Signedcertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) のドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-198">For more information, see the [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) documentation.</span></span>

<span data-ttu-id="8e3b3-199">Surface UEFI コンフィギュレーターで作成される SEMM パッケージは、証明書を使ってセキュリティで保護されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-199">The SEMM package that Surface UEFI Configurator creates must be secured with a certificate.</span></span> <span data-ttu-id="8e3b3-200">UEFI 設定を適用する前に、証明書によって構成ファイルの署名が確認されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-200">The certificate verifies the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="8e3b3-201">詳細については、「 [Semm ドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-201">For more information, see the [SEMM documentation](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 
 
### <span data-ttu-id="8e3b3-202">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-202">Create a SEMM package</span></span>

1. <span data-ttu-id="8e3b3-203">別の PC で、以前にダウンロードした Surface UEFI コンフィギュレーターツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-203">On a separate PC, install the Surface UEFI Configurator tool that you downloaded earlier.</span></span> 

2. <span data-ttu-id="8e3b3-204">[Surface UEFI コンフィギュレーター] を開き、[ **開始**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-204">Open Surface UEFI Configurator, and then select **Start**.</span></span>

   ![Surface UEFI コンフィギュレーターを開きます。](images/shm-fig2.png)
   
3. <span data-ttu-id="8e3b3-206">[ **Surface Devices**] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-206">Select **Surface Devices**, and then select **Next**.</span></span>

   ![[Surface Devices] を選びます。](images/shm-fig3.png)
  
4. <span data-ttu-id="8e3b3-208">[ **構成パッケージ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-208">Select **Configuration Package**.</span></span>

   ![[構成パッケージ] を選びます。](images/shm-fig4.png)
  
5. <span data-ttu-id="8e3b3-210">[ **証明書の保護**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-210">Select **Certificate Protection**.</span></span>

   ![[証明書の保護] を選びます。](images/shm-fig5.png)

   <span data-ttu-id="8e3b3-212">証明書 .pfx ファイルを追加するように求められます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-212">You're prompted to add your certificate .pfx file.</span></span>

   ![証明書を追加します。](images/shm-fig6.png)
   
7. <span data-ttu-id="8e3b3-214">証明書のパスワードを入力して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-214">Enter your certificate password, and then select **OK**.</span></span>

   ![証明書のパスワードを入力して、[OK] を選択します。](images/shm-fig7.png)

8. <span data-ttu-id="8e3b3-216">Surface UEFI にパスワードを追加するには、[ **パスワードによる保護** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-216">Select **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="8e3b3-217">このパスワードは、UEFI を起動するたびに必要になります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-217">You'll need this password whenever you boot to UEFI.</span></span> <span data-ttu-id="8e3b3-218">Surface Hub 2S で使う UEFI パスワードを設定することを *強くお勧め* します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-218">We *strongly recommend* that you set a UEFI password that you'll use on Surface Hub 2S.</span></span>

   ![[パスワードによる保護] を選びます。](images/shm-fig8.png)
   
9. <span data-ttu-id="8e3b3-220">UEFI パスワードを設定して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-220">Set a UEFI password, and then select **OK**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="8e3b3-221">Surface Hub を管理する IT 管理者がアクセスできる安全な場所にパスワードを保存します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-221">Save the password in a secure location that's accessible to your IT admins who manage Surface Hub.</span></span> <span data-ttu-id="8e3b3-222">パスワードを紛失した場合、復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-222">If the password is lost, it can't be recovered.</span></span> 

   ![UEFI パスワードを入力します。](images/shm-fig9.png)

10. <span data-ttu-id="8e3b3-224">[ **Surface Hub 2s**] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-224">Select **Surface Hub 2S**, and then select **Next**.</span></span>

    ![[Surface Hub 2S] を選びます。](images/shm-fig10.png)
   
11. <span data-ttu-id="8e3b3-226">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-226">Select **Next**.</span></span>

    ![[次へ] を選択します。](images/shm-fig10a.png)

12. <span data-ttu-id="8e3b3-228">Windows 10 Pro または Enterprise のインストールを許可するには、 **EnableOsMigration**を有効にして、[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-228">To allow installation of Windows 10 Pro or Enterprise, turn on **EnableOsMigration**, and then select **Next**.</span></span>

    ![[O S の移行を有効にする] を選択します。](images/shm-fig11.png)
    
    ![[OS 移行の有効化] を [オン] に設定します。](images/shm-fig12.png)

> [!NOTE]
> <span data-ttu-id="8e3b3-231">SEMM パッケージを適用した後、デバイスの UEFI メニューでは、すべての UEFI 設定を使用できなくなります (ロックされています)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-231">After you apply a SEMM package, in the device's UEFI menu, all UEFI settings are unavailable (locked).</span></span> <span data-ttu-id="8e3b3-232">その他の設定については、 **IPv6 の場合、IPv6 の場合** の既定値も使用できません。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-232">Default values for other settings such as **IPv6 for PXE Boot** are also unavailable.</span></span> 
>
><span data-ttu-id="8e3b3-233">移行が完了した後で UEFI の設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-233">To change UEFI settings after you finish the migration, apply another SEMM package or unenroll the device from SEMM.</span></span> <span data-ttu-id="8e3b3-234">別の SEMM パッケージを適用して UEFI の設定を変更する場合は、新しい SEMM パッケージをビルドするときに、元の証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-234">If you apply another SEMM package to change the UEFI settings, you must use the original certificate when you build the new SEMM package.</span></span> <span data-ttu-id="8e3b3-235">UEFI コンフィギュレーターツールを使用して、 **EnableOSMigration** をオフのままにしておきます (元の移行手順で示されています)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-235">Use the UEFI Configurator tool and leave **EnableOSMigration** off (not on, as shown in the original migration steps).</span></span>

#### <span data-ttu-id="8e3b3-236">SEMM パッケージを USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-236">Save the SEMM package to a USB drive</span></span>

1. <span data-ttu-id="8e3b3-237">USB ドライブを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-237">Connect a USB drive to your PC.</span></span> 
1. <span data-ttu-id="8e3b3-238">[ **Hub 2s**] を選び、[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-238">Choose **Hub 2S**, and then select **Next**.</span></span>

   ![USB を選ぶ](images/shm-fig13.png)

   > [!WARNING]
   > <span data-ttu-id="8e3b3-240">SEMM パッケージをビルドすると、USB ドライブ上の既存のデータはすべて消去されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-240">All existing data on the USB drive is erased when the SEMM package is built.</span></span> <span data-ttu-id="8e3b3-241">SEMM パッケージを作成する前に、保存する USB ドライブからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-241">Before building the SEMM package, remove any files from the USB drive that you want to save.</span></span>
   
2. <span data-ttu-id="8e3b3-242">[ **ビルド**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-242">Select **Build**.</span></span>

   ![[ビルド] を選びます。](images/shm-fig14.png)

3. <span data-ttu-id="8e3b3-244">このページのスクリーンショットをキャプチャして、[ **終了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-244">Capture a screenshot of this page, and then select **End**.</span></span> <span data-ttu-id="8e3b3-245">これで、SEMM パッケージの準備ができました。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-245">Your SEMM package is now ready.</span></span> <span data-ttu-id="8e3b3-246">このファイルには、SEMM パッケージ *Dfciupdate* と、semm 拇印 (証明書の拇印の最後の2文字) が含まれているテキストファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-246">It contains the SEMM package *DfciUpdate.dfi* and a text file that includes the SEMM thumbprint (the last two characters of the certificate's thumbprint).</span></span>

   ![[終了] を選びます。](images/shm-fig15.png)
   
4. <span data-ttu-id="8e3b3-248">証明書の拇印の最後の2文字を保存します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-248">Save the certificate thumbprint's last two characters.</span></span> <span data-ttu-id="8e3b3-249">Surface Hub 2S でパッケージを適用するときに、SEMM を有効にするには、これらの文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-249">You'll need these characters to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="8e3b3-250">Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 ドライバーとファームウェアを含む USB フラッシュドライブを準備する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-250">Prepare a USB flash drive that contains a Windows 10 image, SEMM package, and Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="8e3b3-251">次のいずれかのオプションを使用して、Windows 10 Pro または Enterprise のイメージ (バージョン1903以降) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-251">You can install a Windows 10 Pro or Enterprise image (version 1903 or later) by using one of the following options:</span></span>

- <span data-ttu-id="8e3b3-252">現在のイメージングソリューション。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-252">Your current imaging solution.</span></span>

- <span data-ttu-id="8e3b3-253">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-253">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator).</span></span> <span data-ttu-id="8e3b3-254">このツールを使用して、起動可能な Windows 10 イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-254">Use this tool to create a bootable Windows 10 image.</span></span> <span data-ttu-id="8e3b3-255">画像には、現在使用しているすべての Windows 10 の更新プログラム、Office、選択したその他のアプリ、および必要なドライバーとファームウェアが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-255">The image can include all current Windows 10 updates, Office, other apps that you choose, and the required drivers and firmware.</span></span> 

- <span data-ttu-id="8e3b3-256">Windows 10 Pro または Enterprise のイメージが含まれている USB フラッシュドライブ。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-256">USB flash drive that contains a Windows 10 Pro or Enterprise image.</span></span> <span data-ttu-id="8e3b3-257">次 [に、Surface Hub 2 の Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアを](https://www.microsoft.com/download/details.aspx?id=101974)インストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-257">Then install [drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
<span data-ttu-id="8e3b3-258">次の手順では、インストールメディアから USB フラッシュドライブを作成した後、SEMM パッケージファイルと、Surface Hub 2 MSI ファイルの Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-258">The following procedure describes how to create a USB flash drive from installation media, and then add the SEMM package files and the Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 MSI file.</span></span> <span data-ttu-id="8e3b3-259">他の展開方法を使用している場合は、この記事の「 [Surface Hub 2s での更新プログラム](#update-uefi-on-surface-hub-2s-to-enable-os-migration) のインストール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-259">If you're using other deployment methods, go to the [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration) section in this article.</span></span>

> [!NOTE]
> <span data-ttu-id="8e3b3-260">インストールが完了したら、既存の Windows 10 Team ライセンスとは別の Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-260">After you finish the installation, you'll need a valid license for Windows 10 Pro or Windows 10 Enterprise that's separate from your existing Windows 10 Team license.</span></span>

1. <span data-ttu-id="8e3b3-261">Windows 10 Pro のインストールを作成するには、[ [**windows 10 のダウンロード**](https://www.microsoft.com/software-download/windows10) ] ページで指示に従ってメディア作成ツールをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-261">To create a Windows 10 Pro installation, on the [**Download Windows 10**](https://www.microsoft.com/software-download/windows10) page, follow the instructions to download the media creation tool.</span></span> <span data-ttu-id="8e3b3-262">Windows 10 Enterprise をダウンロードするには、 [Microsoft ボリュームライセンスサービスセンター](https://www.microsoft.com/licensing/servicecenter/default.aspx)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-262">To download Windows 10 Enterprise, go to the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).</span></span>

2. <span data-ttu-id="8e3b3-263">新しい USB ストレージドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-263">Insert a new USB storage drive.</span></span> 
1. <span data-ttu-id="8e3b3-264">メディア作成ツールを開き、[ **インストールメディアの作成**] を選択して、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-264">Open the media creation tool, select **Create installation media**, and then select **Next**.</span></span>

   ![インストールメディアを作成します。](images/shm-fig16.png)
   
3. <span data-ttu-id="8e3b3-266">言語を選択し、[ **Windows 10** ] と [ **64 ビット (x64)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-266">Select a language, and then choose **Windows 10** and **64-bit (x64)**.</span></span> <span data-ttu-id="8e3b3-267">[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-267">Then select **Next**.</span></span>

   ![[言語] を選択し、[Windows 10] と [64 ビット] を選択します。](images/shm-fig17.png)
   
4. <span data-ttu-id="8e3b3-270">[ **USB フラッシュドライブ**] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-270">Select **USB flash drive**, and then select **Next**.</span></span>

   ![[U S B フラッシュドライブ] を選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. <span data-ttu-id="8e3b3-272">ダウンロードが完了したら、[ **完了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-272">When the download finishes, select **Finish**.</span></span>

   ![[完了] を選びます。](images/shm-fig19.png)
   
6. <span data-ttu-id="8e3b3-274">Surface Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS のドライバーとファームウェアを、Windows 10 イメージが含まれている USB フラッシュドライブ (*Bootme*) のルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-274">Copy the SEMM package files and the drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (the MSI file) to the root of the USB flash drive (*BOOTME*) that contains your Windows 10 image.</span></span> <span data-ttu-id="8e3b3-275">BOOTME USB ドライブの内容:</span><span class="sxs-lookup"><span data-stu-id="8e3b3-275">The BOOTME USB drive contains:</span></span>

    - <span data-ttu-id="8e3b3-276">Windows 10 の起動可能なイメージ。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-276">Your Windows 10 bootable image.</span></span>
    
    - <span data-ttu-id="8e3b3-277">SEMM パッケージファイル (USB ドライブのルートにコピーされます)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-277">SEMM package files (copied to the root of the USB drive).</span></span>
    
      - <span data-ttu-id="8e3b3-278">*Dfi をダウンロード*します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-278">*DfciUpdate.dfi*.</span></span>
      - <span data-ttu-id="8e3b3-279">SEMM 拇印を含むテキストファイル。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-279">Text file that includes the SEMM thumbprint.</span></span> <span data-ttu-id="8e3b3-280">(この例では、ファイルは *SurfaceUEFI_2020Aug25_1058.txt*ています)。自動的に生成された日付タイムスタンプは、Surface UEFI コンフィギュレーターを使用してファイルを作成した日付に対応します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-280">(In this example, the file is *SurfaceUEFI_2020Aug25_1058.txt*.) The automatically generated date time stamp corresponds to the date that you created the file by using Surface UEFI Configurator.</span></span>

   - <span data-ttu-id="8e3b3-281">Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) での Windows 10 Pro と Enterprise OS のドライバーとファームウェア。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-281">Drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi).</span></span> <span data-ttu-id="8e3b3-282">このファイルを USB ドライブのルートにコピーします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-282">Copy this file to the root of the USB drive.</span></span>

### <span data-ttu-id="8e3b3-283">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="8e3b3-283">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

1. <span data-ttu-id="8e3b3-284">BOOT ME ドライブを USB に挿入します。 Surface Hub 2S の A ポート。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-284">Insert your BOOTME drive into the USB-A port on Surface Hub 2S.</span></span> <span data-ttu-id="8e3b3-285">必要なファイルの一覧については、前のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-285">For a list of required files, see the previous section.</span></span>

2. <span data-ttu-id="8e3b3-286">UEFI を起動するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-286">To boot into UEFI:</span></span>

   1. <span data-ttu-id="8e3b3-287">Surface Hub 2S をオフにします (シャットダウンします)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-287">Turn off (shut down) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="8e3b3-288">**ボリューム +** を押しながら、電源ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-288">Press and hold **Volume +**, and then press and release the power button.</span></span>
   1. <span data-ttu-id="8e3b3-289">[UEFI] メニューが表示さ **れるまで、[保持]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-289">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![[UEFI] メニューが表示されるまで、音量を調節したままにします。](images/shm-fig20.png)
      
3. <span data-ttu-id="8e3b3-291">デバイスが再起動したら、前に作成した UEFI パスワード (該当する場合) を入力します (強くお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-291">When the device restarts, enter the UEFI password that you created earlier, if applicable (strongly recommended).</span></span>

   ![UEFI パスワードを入力します。](images/shm-fig22.png)
   
4. <span data-ttu-id="8e3b3-293">[UEFI] メニューで、[**管理**インストール (USB)] を選択し  >  **Install from USB**ます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-293">In the UEFI menu, select **Management** > **Install from USB**.</span></span>

   ![[管理] を選択し、U S B からインストールします。](images/shm-fig21.png)
   
5. <span data-ttu-id="8e3b3-295">次の図に示すように、[ **今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-295">Select **Restart now**, as the following image shows.</span></span> <span data-ttu-id="8e3b3-296">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-296">The device reboots.</span></span> <span data-ttu-id="8e3b3-297">ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-297">It displays a white Microsoft logo in the middle of the window and then shuts down.</span></span>

   ![[今すぐ再起動] を選択します。](images/shm-fig25.png)
   
6. <span data-ttu-id="8e3b3-299">電源ボタンを押してから離します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-299">Press and release the power button.</span></span> <span data-ttu-id="8e3b3-300">表示される赤いウィンドウで、[Surface Enterprise Management] モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-300">In the red window that appears, activate Surface Enterprise Management Mode.</span></span> 

7. <span data-ttu-id="8e3b3-301">2文字の証明書の拇印と UEFI 設定のパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-301">Enter your two-character certificate thumbprint and your UEFI settings password.</span></span> <span data-ttu-id="8e3b3-302">[ **OK]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-302">Then select **OK**.</span></span>

   ![2文字の証明書の拇印と UEFI 設定のパスワードを入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="8e3b3-304">デバイスで SEMM のライセンス認証を行うと、新しい UEFI 設定 **EnableOSMigration** が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-304">After you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="8e3b3-305">Windows 10 チームにはアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-305">You'll no longer be able to access Windows 10 Team.</span></span> <span data-ttu-id="8e3b3-306">代わりに、次の手順に進んで、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-306">Instead, you must continue to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span> 

   <span data-ttu-id="8e3b3-307">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-307">The device reboots.</span></span> <span data-ttu-id="8e3b3-308">画面の中央に白いロゴが表示され、もう一度停止します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-308">It displays the white logo in the middle of the screen and then shuts down again.</span></span>

### <span data-ttu-id="8e3b3-309">Windows 10 Pro または Enterprise をインストールする</span><span class="sxs-lookup"><span data-stu-id="8e3b3-309">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="8e3b3-310">起動可能な Windows 10 Pro または Enterprise ドライブが、Surface Hub 2 USB-ポートにまだ入っていない場合は、ここで挿入します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-310">If your bootable Windows 10 Pro or Enterprise drive isn't already in the Surface Hub 2 USB-A port, insert it now.</span></span> <span data-ttu-id="8e3b3-311">次に、電源ボタンを押してから離します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-311">Then press and release the power button.</span></span> 

    <span data-ttu-id="8e3b3-312">デバイスが起動すると、画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-312">When the device starts, you see the white logo in the middle of the screen.</span></span> <span data-ttu-id="8e3b3-313">白いロゴの下にスピンしている円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-313">Then you see a spinning circle below the white logo.</span></span>

3. <span data-ttu-id="8e3b3-314">デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切ってください (電源コードを外してから、もう一度接続します)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-314">If the device doesn't automatically boot to the USB drive, power off the device (unplug the power cord and then plug it back in).</span></span> <span data-ttu-id="8e3b3-315">電源コードをもう一度接続すると、数秒経ってもデバイスが起動します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-315">After you plug the power cord in again, the device should boot after a few seconds.</span></span> <span data-ttu-id="8e3b3-316">画面の中央に白いロゴが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-316">Then you'll see the white logo in the middle of screen.</span></span> 

    <span data-ttu-id="8e3b3-317">デバイスの電源がオンになっていない場合は、電源ボタンを押してから離します。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-317">If the device doesn't turn on, press and release the power button.</span></span> <span data-ttu-id="8e3b3-318">画面中央にロゴが表示されたらすぐに、白いロゴの下にスピンしている円が表示されるまで音量ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-318">Immediately after you see the logo in the middle of the screen, press and hold the volume button until you see the spinning circle below the white logo.</span></span>
 
   ![U S B ドライブから Windows 10 に起動します。](images/shm-fig26.png)
   
4. <span data-ttu-id="8e3b3-320">既定のエクスペリエンス (OOBE) セットアップが開始されたら、手順に従って Windows 10 Pro または Enterprise (バージョン1903以降) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-320">When the out-of-box experience (OOBE) setup starts, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="8e3b3-321">Surface Hub 2 ドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="8e3b3-321">Install Surface Hub 2 drivers and firmware</span></span>

<span data-ttu-id="8e3b3-322">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-322">To ensure your device has all the latest updates and drivers, install [drivers and firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
## <span data-ttu-id="8e3b3-323">推奨設定を構成する</span><span class="sxs-lookup"><span data-stu-id="8e3b3-323">Configure recommended settings</span></span>

<span data-ttu-id="8e3b3-324">Surface Hub をパーソナルの生産性デバイスとして完全に構成する方法については、「 [Surface hub 2 で Windows 10 Pro または Enterprise を構成](surface-hub-2-post-install.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-324">To fully configure Surface Hub 2S as a personal productivity device, see [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).</span></span>

> [!NOTE]
><span data-ttu-id="8e3b3-325">この記事に記載されている手順を実行してもデバイスが Windows 10 Pro または Surface Hub 2 のエンタープライズに正常に移行されない場合は、 [Surface hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-325">If the steps outlined in this article don't successfully migrate your device to Windows 10 Pro or Enterprise for Surface Hub 2, contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="8e3b3-326">Windows 10 チームにロールバックする</span><span class="sxs-lookup"><span data-stu-id="8e3b3-326">Roll back to Windows 10 Team</span></span>

<span data-ttu-id="8e3b3-327">デバイスを Windows 10 チームに復元する場合は、「 [Surface Hub 2s のリセットと回復](surface-hub-2s-recover-reset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-327">If you want to restore your device to Windows 10 Team, see [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span>

## <span data-ttu-id="8e3b3-328">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="8e3b3-328">Version history</span></span>

<span data-ttu-id="8e3b3-329">次の表は、この記事に加えられた変更をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-329">The following table summarizes changes to this article.</span></span>

| <span data-ttu-id="8e3b3-330">バージョン</span><span class="sxs-lookup"><span data-stu-id="8e3b3-330">Version</span></span> | <span data-ttu-id="8e3b3-331">日付</span><span class="sxs-lookup"><span data-stu-id="8e3b3-331">Date</span></span>               | <span data-ttu-id="8e3b3-332">説明</span><span class="sxs-lookup"><span data-stu-id="8e3b3-332">Description</span></span>                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8e3b3-333">部.</span><span class="sxs-lookup"><span data-stu-id="8e3b3-333">v.</span></span> <span data-ttu-id="8e3b3-334">1.2</span><span class="sxs-lookup"><span data-stu-id="8e3b3-334">1.2</span></span>  | <span data-ttu-id="8e3b3-335">2020年9月29日</span><span class="sxs-lookup"><span data-stu-id="8e3b3-335">September 29, 2020</span></span> | <span data-ttu-id="8e3b3-336">ユーザビリティのフィードバックに対応するその他の更新プログラム。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-336">Miscellaneous updates that address usability feedback.</span></span>                                                        |
| <span data-ttu-id="8e3b3-337">部.</span><span class="sxs-lookup"><span data-stu-id="8e3b3-337">v.</span></span> <span data-ttu-id="8e3b3-338">1.1</span><span class="sxs-lookup"><span data-stu-id="8e3b3-338">1.1</span></span>  | <span data-ttu-id="8e3b3-339">2020年9月15日</span><span class="sxs-lookup"><span data-stu-id="8e3b3-339">September 15, 2020</span></span> | <span data-ttu-id="8e3b3-340">新しい OS をインストールするためのライセンス要件を明確に示す追加メモを導入しています。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-340">Placed an additional note in the introduction that clarifies licensing requirements for installing a new OS.</span></span> |
| <span data-ttu-id="8e3b3-341">部.</span><span class="sxs-lookup"><span data-stu-id="8e3b3-341">v.</span></span> <span data-ttu-id="8e3b3-342">1.0</span><span class="sxs-lookup"><span data-stu-id="8e3b3-342">1.0</span></span>  | <span data-ttu-id="8e3b3-343">2020年9月1日</span><span class="sxs-lookup"><span data-stu-id="8e3b3-343">September 1, 2020</span></span>  | <span data-ttu-id="8e3b3-344">新しい記事。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-344">New article.</span></span>                                                                                           |
