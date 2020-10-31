---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 上の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行するプロセスについて説明します。
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
ms.openlocfilehash: 12742cc887ba495f8f7cbded8bd84dc4fd63b6f6
ms.sourcegitcommit: 5448f775d3fe177806fce6cbaf0b2b091ed8b7d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2020
ms.locfileid: "11145972"
---
# <span data-ttu-id="f8151-104">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="f8151-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

## <span data-ttu-id="f8151-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="f8151-105">Introduction</span></span>

<span data-ttu-id="f8151-106">Surface Hub 2S は、Windows 10 チームでプレインストールされています。カスタマイズされた Windows 10 は、会議室環境での共同作業が容易になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="f8151-106">Surface Hub 2S comes pre-installed with Windows 10 Team, a customized edition of Windows 10 designed to facilitate easy collaboration in meeting room environments.</span></span> <span data-ttu-id="f8151-107">これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub の2S を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f8151-107">Now you have the option of running Windows 10 Pro or Enterprise to use Surface Hub 2S much like any other PC.</span></span> 

> [!IMPORTANT]
><span data-ttu-id="f8151-108">通常のアップグレードや移行とは異なり、このプロセスでは、このページの説明に従って、規範となる手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-108">Unlike a typical upgrade or migration, this process requires you to follow a prescriptive procedure, as described on this page.</span></span> <span data-ttu-id="f8151-109">続行する前に、 [ソリューションのコンポーネント](#solution-components) と [移行とインストールのワークフロー](#migration-and-installation-workflow-summary) を確認します。</span><span class="sxs-lookup"><span data-stu-id="f8151-109">Review the [Solution components](#solution-components) and [Migration and installation workflow](#migration-and-installation-workflow-summary) before proceeding.</span></span>


> [!NOTE]
> <span data-ttu-id="f8151-110">Windows 10 Pro または Enterprise をインストールする場合は、既存の Windows 10 チームライセンスとは別の新しいライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8151-110">When you install Windows 10 Pro or Enterprise, you will need a new licence separate from your existing Windows 10 Team license.</span></span> 


<span data-ttu-id="f8151-111">別個の PC とダウンロード可能なツールを使用して、Windows 10 チームから移行を開始します。 surface **UEFI コンフィギュレーター** --Surface Hub 2s に適用する新しい UEFI 設定を含むパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8151-111">You start the migration from Windows 10 Team using a separate PC and downloadable tool -- **Surface UEFI Configurator** --  to create a package containing a new UEFI setting that you apply to Surface Hub 2S.</span></span>  <span data-ttu-id="f8151-112">Surface Enterprise Management Mode (SEMM) へのインターフェイスとしての surface の構成機能。これは、企業環境の Surface デバイスでのファームウェア設定の一元管理を容易にするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="f8151-112">Surface UEFI Configurator functions as an interface into Surface Enterprise Management Mode (SEMM), designed to facilitate centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="f8151-113">SEMM の詳細については、「 [Microsoft Surface Enterprise 管理モードのドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8151-113">To learn more about SEMM, see [Microsoft Surface Enterprise Management Mode documentation](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 

## <span data-ttu-id="f8151-114">ソリューションのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="f8151-114">Solution Components</span></span>

- <span data-ttu-id="f8151-115">Windows 10 Team オペレーティングシステムを実行している Surface Hub 2S デバイス。</span><span class="sxs-lookup"><span data-stu-id="f8151-115">Surface Hub 2S device running Windows 10 Team operating system.</span></span>
- <span data-ttu-id="f8151-116">Windows 10 を実行している別のデバイス。</span><span class="sxs-lookup"><span data-stu-id="f8151-116">Separate device running Windows 10.</span></span>
- <span data-ttu-id="f8151-117">SEMM パッケージを作成するための Surface UEFI コンフィギュレーターツール。</span><span class="sxs-lookup"><span data-stu-id="f8151-117">Surface UEFI Configurator tool to create the SEMM package.</span></span>
- <span data-ttu-id="f8151-118">Windows 10 Pro または Enterprise OS イメージ、バージョン1903またはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="f8151-118">Windows 10 Pro or Enterprise OS image, version 1903 or greater.</span></span>
- <span data-ttu-id="f8151-119">2 GB の記憶域、FAT32 形式の USB ドライブ。</span><span class="sxs-lookup"><span data-stu-id="f8151-119">Two USB drives with 16GB of storage, FAT32 format.</span></span>
- <span data-ttu-id="f8151-120">Surface Hub 2、Windows インストーラーの Windows 10 Pro および Enterprise OS 用のドライバーとファームウェア。MSI ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8151-120">Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2, Windows Installer .MSI file.</span></span>
- <span data-ttu-id="f8151-121">インターネット接続。</span><span class="sxs-lookup"><span data-stu-id="f8151-121">Internet connection.</span></span>
- <span data-ttu-id="f8151-122">イメージングソリューション (オプション)。</span><span class="sxs-lookup"><span data-stu-id="f8151-122">Imaging solution (optional).</span></span>

 
## <span data-ttu-id="f8151-123">移行とインストールワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="f8151-123">Migration and installation workflow summary</span></span>

| <span data-ttu-id="f8151-124">ステップ</span><span class="sxs-lookup"><span data-stu-id="f8151-124">Step</span></span>  | <span data-ttu-id="f8151-125">操作</span><span class="sxs-lookup"><span data-stu-id="f8151-125">Action</span></span>                                                                                                 | <span data-ttu-id="f8151-126">まとめ</span><span class="sxs-lookup"><span data-stu-id="f8151-126">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8151-127">件</span><span class="sxs-lookup"><span data-stu-id="f8151-127">1</span></span> | [<span data-ttu-id="f8151-128">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="f8151-128">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | <span data-ttu-id="f8151-129">UEFI バージョンが **694.2938.768.0** 以降であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8151-129">Ensure the UEFI version is **694.2938.768.0** or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="f8151-130">両面</span><span class="sxs-lookup"><span data-stu-id="f8151-130">2</span></span> | [<span data-ttu-id="f8151-131">ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="f8151-131">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="f8151-132">[ [Surface Tools FOR IT](https://www.microsoft.com/download/details.aspx?id=46703) ] ページで [ダウンロード] ボタンを選択し、Surface UEFI コンフィギュレーターを選択してダウンロードし **ます。MSI ファイル** を別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-132">Select the Download button on the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page, select and download the **Surface UEFI Configurator .MSI file** and install it on a separate PC.</span></span> <span data-ttu-id="f8151-133">[Surface Hub 2 の Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをダウンロードします。MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)を保存して、手順5で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="f8151-133">Download [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) and save it for use in Step 5.</span></span> |
| <span data-ttu-id="f8151-134">-</span><span class="sxs-lookup"><span data-stu-id="f8151-134">3</span></span> | [<span data-ttu-id="f8151-135">SEMM 証明書の準備</span><span class="sxs-lookup"><span data-stu-id="f8151-135">Prepare SEMM certificate</span></span>](#prepare-semm-certificate)                                                                          | <span data-ttu-id="f8151-136">Surface UEFI コンフィギュレーターの実行に必要な証明書を準備するか、現在の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8151-136">Prepare required certificate for running Surface UEFI Configurator or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="f8151-137">4d</span><span class="sxs-lookup"><span data-stu-id="f8151-137">4</span></span> | [<span data-ttu-id="f8151-138">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="f8151-138">Create SEMM package</span></span>](#create-semm-package)                                                                               | <span data-ttu-id="f8151-139">Surface UEFI コンフィギュレーターを起動して、USB ドライブ上に SEMM パッケージを作成します。これには、Surface Hub 2S に適用する必要な構成ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8151-139">Launch Surface UEFI Configurator to create a SEMM package on a USB drive, which will contain the required configuration files to apply on Surface Hub 2S.</span></span> <span data-ttu-id="f8151-140">これらの SEMM パッケージファイルを PC 上のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f8151-140">Copy these SEMM package  files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="f8151-141">個</span><span class="sxs-lookup"><span data-stu-id="f8151-141">5</span></span> | [<span data-ttu-id="f8151-142">Windows 10 のイメージ、SEMM パッケージ、および Windows 10 Pro と Enterprise OS for Surface Hub 2 のドライバーとファームウェアを含む USB フラッシュドライブを準備する</span><span class="sxs-lookup"><span data-stu-id="f8151-142">Prepare USB flash drive containing Windows 10 image, SEMM package, and Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2</span></span>](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="f8151-143">Windows 10 イメージを含む USB ドライブ (この例では **Bootme** という名前) を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8151-143">Create a single USB drive (named **BOOTME** in this example) containing a Windows 10 image.</span></span> <span data-ttu-id="f8151-144">Surface Hub 2 (手順 2) と SEMM パッケージファイル (手順 4) に Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアを **Bootme** ドライブに追加します。</span><span class="sxs-lookup"><span data-stu-id="f8151-144">Add your Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (Step 2) and SEMM package files (Step 4) to the **BOOTME** drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="f8151-145">=</span><span class="sxs-lookup"><span data-stu-id="f8151-145">6</span></span> | [<span data-ttu-id="f8151-146">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="f8151-146">Update UEFI on Surface Hub 2S to enable OS migration</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="f8151-147">**Bootme**ドライブを使って、[UEFI] メニューに Surface Hub 2s を起動し、semm パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-147">Use the **BOOTME** drive to boot Surface Hub 2S to the UEFI menu and install SEMM package.</span></span>|
| <span data-ttu-id="f8151-148">日</span><span class="sxs-lookup"><span data-stu-id="f8151-148">7</span></span> | [<span data-ttu-id="f8151-149">Windows 10 Pro または Enterprise バージョン1903以降をインストールする</span><span class="sxs-lookup"><span data-stu-id="f8151-149">Install Windows 10 Pro or Enterprise version 1903 or later</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="f8151-150">**Bootme**ドライブを使用して、 **Windows 10 Pro または Enterprise**バージョン1903以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-150">Use the **BOOTME** drive to Install **Windows 10 Pro or Enterprise** version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="f8151-151">個</span><span class="sxs-lookup"><span data-stu-id="f8151-151">8</span></span> | [<span data-ttu-id="f8151-152">Surface Hub 2 の Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="f8151-152">Install Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="f8151-153">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをインストールします。MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)。</span><span class="sxs-lookup"><span data-stu-id="f8151-153">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="f8151-154">ファイブ</span><span class="sxs-lookup"><span data-stu-id="f8151-154">9</span></span> | [<span data-ttu-id="f8151-155">パーソナル生産性デバイスとして Surface Hub 2S を完全に構成する</span><span class="sxs-lookup"><span data-stu-id="f8151-155">Fully configure Surface Hub 2S as a personal productivity device</span></span>](#next-steps)                                        |  <span data-ttu-id="f8151-156">推奨される設定とアプリケーションを有効にして、個人用生産性デバイスとして Surface Hub 2S の使用を最適化します。</span><span class="sxs-lookup"><span data-stu-id="f8151-156">Enable recommended settings and applications to optimize use of Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="f8151-157">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="f8151-157">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>

<span data-ttu-id="f8151-158">Surface Hub を Windows 10 Team から Windows 10 デスクトップに移行する前に、 **694.2938.768.0**の最小 UEFI バージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8151-158">The minimum UEFI version required prior to migrating the Surface Hub from Windows 10 Team to Windows 10 Desktop is **694.2938.768.0**.</span></span>
 
**<span data-ttu-id="f8151-159">システムの現在の UEFI バージョンを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f8151-159">To verify the current UEFI version on your system:</span></span>**

1. <span data-ttu-id="f8151-160">Surface Hub 2s ホーム画面で、[**開始**] を選択し、 **SurfaceApp** (**すべてのアプリ**の  >  **サーフェス**) を開きます。</span><span class="sxs-lookup"><span data-stu-id="f8151-160">On Surface Hub 2S home screen, select **Start** and open the **SurfaceApp** (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="f8151-161">Surface Hub に関する情報を表示する **サーフェス** を選択します。これには、デバイス上の現在の UEFI バージョンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8151-161">Select **Your Surface** to display information about the Surface Hub, including the current UEFI version on the device.</span></span> <span data-ttu-id="f8151-162">以下に示すように、UEFI バージョンが **694.2938.768.0** 以降の場合、uefi は、OS の移行を有効にするための semm パッケージの作成に適しています。</span><span class="sxs-lookup"><span data-stu-id="f8151-162">If the UEFI version is **694.2938.768.0** or later as shown below, the UEFI is eligible for you to create the SEMM package to enable OS migration.</span></span>

    ![Surface アプリを開く & Surface を選択します。](images/shm-fig1.png)
 
3. <span data-ttu-id="f8151-164">UEFI バージョンがバージョン **694.2938.768.0**よりも古い場合は、Windows Update を使用して現在のバージョンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-164">If the UEFI version is earlier than version **694.2938.768.0**, you will need to obtain a current version using Windows Update.</span></span>

**<span data-ttu-id="f8151-165">Windows Update から UEFI を更新するには:</span><span class="sxs-lookup"><span data-stu-id="f8151-165">To update UEFI from Windows Update:</span></span>**

1. <span data-ttu-id="f8151-166">Surface Hub 2s の場合は、**管理者**としてサインインし、[**すべてのアプリ**の設定]、[  >  **Settings**  >  **セキュリティ**  >  **Windows Update** ] の順に移動して、すべての更新プログラムをインストールしてから、デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f8151-166">On your Surface Hub 2S, sign in as an **Admin**, go to **All apps** > **Settings** > **Update and Security** > **Windows Update** and install all updates, then restart the device.</span></span> <span data-ttu-id="f8151-167">Surface アプリを使用して、UEFI バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8151-167">Verify the UEFI version using the Surface App.</span></span> <span data-ttu-id="f8151-168">**注:** ユーザー名または管理者のパスワードがわからない場合は、デバイスをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-168">**Note:** If you do not know your username or admin password, you will need to reset the device.</span></span> <span data-ttu-id="f8151-169">詳細については、「 [Surface Hub 2s のリセットと回復](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8151-169">To learn more, see [Reset and recovery for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span></span>

2. <span data-ttu-id="f8151-170">UEFI バージョンが **694.2938.768.0** 以降になるまで、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f8151-170">Repeat these steps until the UEFI version is **694.2938.768.0** or later.</span></span>

3. <span data-ttu-id="f8151-171">まだ更新されている UEFI が何回も表示されない場合は、 **更新履歴** を確認して、失敗したファームウェアインストールのインスタンスを探します。</span><span class="sxs-lookup"><span data-stu-id="f8151-171">If you still do not see the updated UEFI after multiple attempts, check **Update History** and look for any instances of failed firmware installations.</span></span> <span data-ttu-id="f8151-172">デバイスをリセットする必要がある場合があります (**設定**  >  **更新 & セキュリティ**  >  **リセットデバイス**)。</span><span class="sxs-lookup"><span data-stu-id="f8151-172">You may need to reset your device (**Settings** > **Update & security** > **Reset device**).</span></span>

### <span data-ttu-id="f8151-173">ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="f8151-173">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="f8151-174">別の PC では、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f8151-174">On a separate PC:</span></span>

- <span data-ttu-id="f8151-175">[ [Surface Tools FOR IT] ページ](https://www.microsoft.com/download/details.aspx?id=46703)で [ダウンロード] ボタンを選択し、Surface UEFI コンフィギュレーターを選択してダウンロードします。MSI ファイルを別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-175">Select the Download button on the [Surface Tools for IT page](https://www.microsoft.com/download/details.aspx?id=46703), select and download the Surface UEFI Configurator .MSI file and install it on a separate PC.</span></span> <span data-ttu-id="f8151-176">Surface UEFI コンフィギュレーターツールは、Windows 10 Team edition がインストールされている Surface Hub 2S では実行できません。</span><span class="sxs-lookup"><span data-stu-id="f8151-176">The Surface UEFI Configurator tool cannot be run on a Surface Hub 2S while Windows 10 Team edition is installed.</span></span>

- <span data-ttu-id="f8151-177">[Surface Hub 2 ドライバーとファームウェア Windows インストーラーをダウンロードします。](https://www.microsoft.com/download/details.aspx?id=101974)新しいオペレーティングシステムをインストールするときに適用される MSI ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8151-177">Download [Surface Hub 2 Drivers and Firmware Windows Installer .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) to be applied when installing the new operating system.</span></span>

### <span data-ttu-id="f8151-178">SEMM 証明書の準備</span><span class="sxs-lookup"><span data-stu-id="f8151-178">Prepare SEMM certificate</span></span>

<span data-ttu-id="f8151-179">Surface UEFI コンフィギュレーターを初めて使用する場合は、証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-179">If this is your first time using Surface UEFI Configurator, you’ll need to prepare a certificate.</span></span> <span data-ttu-id="f8151-180">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI 設定を変更できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="f8151-180">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify UEFI settings.</span></span> <span data-ttu-id="f8151-181">証明書を取得する方法は、組織の規模または複雑さによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-181">How you acquire a certificate may vary depending on the size or complexity of your organization:</span></span>

- <span data-ttu-id="f8151-182">大規模なエンタープライズ組織では、通常、標準セキュリティの慣行ごとに証明書を生成する独自の証明書インフラストラクチャを維持しています。</span><span class="sxs-lookup"><span data-stu-id="f8151-182">Large enterprise organizations typically maintain their own certificate infrastructure to generate certificates per standard security practices.</span></span>

- <span data-ttu-id="f8151-183">中規模企業やその他のユーザーが、サードパーティプロバイダーから証明書を取得することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f8151-183">Medium-sized businesses and others may choose to obtain a certificate from third party providers.</span></span> <span data-ttu-id="f8151-184">これは、十分な IT 専門知識のない組織または専用の IT セキュリティチーム向けの推奨オプションです。</span><span class="sxs-lookup"><span data-stu-id="f8151-184">This is the recommended option for organizations without sufficient IT expertise or a dedicated IT security team.</span></span>

- <span data-ttu-id="f8151-185">または、次のドキュメントに記載されている PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 [Surface Enterprise 管理モードの証明書の要件](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。</span><span class="sxs-lookup"><span data-stu-id="f8151-185">Alternatively, you can generate a self-signed certificate with a PowerShell script per the following documentation: [Surface Enterprise Management Mode certificate requirements](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span> <span data-ttu-id="f8151-186">または、PowerShell を使用して、次のドキュメントに従って独自の証明書を作成します。[新正書法 certificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)</span><span class="sxs-lookup"><span data-stu-id="f8151-186">Or use PowerShell to create your own certificate per the following documentation: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).</span></span>

<span data-ttu-id="f8151-187">Surface UEFI コンフィギュレーターツールを使用して作成された SEMM パッケージは、UEFI 設定を適用する前に、構成ファイルの署名を確認するために証明書を使用して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-187">The SEMM package created by using the Surface UEFI Configurator tool must be secured with a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="f8151-188">詳細については、「 [Surface Enterprise 管理モード](https://docs.microsoft.com/surface/surface-enterprise-management-mode) のドキュメント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8151-188">To learn more, see [Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode) documentation.</span></span>
 
 
### <span data-ttu-id="f8151-189">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="f8151-189">Create SEMM package</span></span>

1. <span data-ttu-id="f8151-190">前にダウンロードした **SURFACE UEFI コンフィギュレーター** ツールを別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-190">Install the **Surface UEFI Configurator** tool, as downloaded earlier, to a separate PC.</span></span> 

2. <span data-ttu-id="f8151-191">**SURFACE UEFI コンフィギュレーター**を開き、[**開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-191">Open **Surface UEFI Configurator** and select **Start**.</span></span>

   ![Open Surface UEFI コンフィギュレーター](images/shm-fig2.png)
   
3. <span data-ttu-id="f8151-193">[ **Surface デバイス** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-193">Select **Surface Devices** and then select **Next**.</span></span>

   ![Surface デバイスの選択](images/shm-fig3.png)
  
4. <span data-ttu-id="f8151-195">[ **構成パッケージ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-195">Select **Configuration Package**.</span></span>

   ![構成パッケージを選ぶ](images/shm-fig4.png)
  
5. <span data-ttu-id="f8151-197">[ **証明書の保護**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-197">Select **Certificate Protection**.</span></span>

   ![証明書の保護を選ぶ](images/shm-fig5.png)

6. <span data-ttu-id="f8151-199">証明書 .pfx ファイルを追加するように求められます。</span><span class="sxs-lookup"><span data-stu-id="f8151-199">You will be prompted to add your certificate .pfx file.</span></span>

   ![証明書を追加するように求められます。](images/shm-fig6.png)
   
7. <span data-ttu-id="f8151-201">**証明書のパスワード**を入力して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-201">Enter your **Certificate password** and select **OK**.</span></span>

   ![証明書のパスワードを入力して、[OK] を選択します。](images/shm-fig7.png)

8. <span data-ttu-id="f8151-203">Surface UEFI にパスワードを追加するには、[ **パスワードによる保護** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-203">Select **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="f8151-204">このパスワードは、UEFI を起動するたびに必要になります。</span><span class="sxs-lookup"><span data-stu-id="f8151-204">This password will be required whenever you boot to UEFI.</span></span> <span data-ttu-id="f8151-205">Surface Hub 2S で使用する UEFI パスワードを設定する **ことを強くお勧め** します。</span><span class="sxs-lookup"><span data-stu-id="f8151-205">It is **strongly recommended** to set a UEFI password you will use on Surface Hub 2S.</span></span>

   ![[パスワードによる保護] をクリック](images/shm-fig8.png)
   
9. <span data-ttu-id="f8151-207">**UEFI パスワード**を設定して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-207">Set a **UEFI password** and select **OK**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="f8151-208">Surface Hub の管理を担当する組織の IT 管理者がアクセスできる安全な場所にパスワードを保存します。</span><span class="sxs-lookup"><span data-stu-id="f8151-208">Save the password in a secure location accessible to IT admins in your organization responsible for managing Surface Hubs.</span></span> <span data-ttu-id="f8151-209">パスワードが失われた場合は、回復処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="f8151-209">If the password is lost, there is no recovery process.</span></span> 

   ![UEFI パスワードを入力する](images/shm-fig9.png)

10. <span data-ttu-id="f8151-211">[ **Surface Hub 2s** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-211">Select **Surface Hub 2S** and then select **Next**.</span></span>

    ![Surface Hub 2S の選択](images/shm-fig10.png)
   
11. <span data-ttu-id="f8151-213">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-213">Select **Next**.</span></span>

    ![[次へ] を選ぶ](images/shm-fig10a.png)

12. <span data-ttu-id="f8151-215">Windows 10 Pro または Enterprise のインストールを許可するには、[EnableOsMigration] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="f8151-215">To allow installation of Windows 10 Pro or Enterprise, select **EnableOsMigration.**</span></span>

    ![[OS の移行を有効にする] を選ぶ](images/shm-fig11.png)
    
13. <span data-ttu-id="f8151-217">**EnableOSMigration**を **[オン**] に設定して、[**次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-217">Set **EnableOSMigration** to **On** and select **Next**.</span></span>

    ![[OS 移行の有効化] を [オン] に設定する](images/shm-fig12.png)

> [!NOTE]
> <span data-ttu-id="f8151-219">SEMM パッケージを適用した後は、デバイスの UEFI メニューですべての UEFI 設定が灰色表示になります (ロックされています)。</span><span class="sxs-lookup"><span data-stu-id="f8151-219">After you apply a SEMM package, all UEFI settings will display as grayed out (locked) in the UEFI menu on the device.</span></span> <span data-ttu-id="f8151-220">これには、PXE ブート用 IPv6 など、他の設定の既定値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8151-220">This includes default values for other settings such as IPv6 for PXE Boot.</span></span> <span data-ttu-id="f8151-221">移行を完了した後で UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-221">To modify UEFI settings after completing the migration, you will need to apply another SEMM package or unenroll the device from SEMM.</span></span> <span data-ttu-id="f8151-222">別の SEMM パッケージを適用して UEFI の設定を変更する場合は、UEFI コンフィギュレーターツールを使って新しい SEMM パッケージを作成するときに元の証明書を使用し、"EnableOSMigration" をオフにしておきます (元の移行手順で示されています)。</span><span class="sxs-lookup"><span data-stu-id="f8151-222">If you apply another SEMM package to modify the UEFI settings, you must use the original Certificate when building the new SEMM package using the UEFI Configurator tool and leave the "EnableOSMigration" OFF (and not "on" as shown in the original migration steps).</span></span>

#### <span data-ttu-id="f8151-223">SEMM パッケージを USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="f8151-223">Save SEMM package to USB drive</span></span>

1. <span data-ttu-id="f8151-224">USB ドライブを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="f8151-224">Connect a USB Drive to your PC.</span></span> <span data-ttu-id="f8151-225">[ **Hub 2s** ] を選び、[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-225">Choose **Hub 2S** and then select **Next**.</span></span>

   ![USB を選ぶ](images/shm-fig13.png)

> [!WARNING]
> <span data-ttu-id="f8151-227">SEMM パッケージをビルドすると、USB ドライブ上の既存のデータはすべて消去されます。</span><span class="sxs-lookup"><span data-stu-id="f8151-227">All existing data on the USB drive is erased when building the SEMM package.</span></span> <span data-ttu-id="f8151-228">SEMM パッケージを作成する前に、保存したい USB ドライブからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="f8151-228">Before building the SEMM package, remove any files from the USB drive that you wish to save.</span></span>
   
2. <span data-ttu-id="f8151-229">[ **ビルド**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-229">Select **Build**.</span></span>

   ![[ビルド] を選ぶ](images/shm-fig14.png)

3. <span data-ttu-id="f8151-231">このページのスクリーンショットをキャプチャして、[ **終了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-231">Capture a screenshot of this page and then select **End**.</span></span> <span data-ttu-id="f8151-232">SEMM パッケージは現在準備が整っており、semm パッケージ **Dfciupdate** と、semm 拇印 (証明書の拇印の最後の2文字) を含むテキストファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8151-232">Your SEMM package is now ready and contains the SEMM package **DfciUpdate.dfi** and a text file with the SEMM thumbprint (the last two characters of the certificate’s thumbprint).</span></span>

   ![[終了] を選ぶ](images/shm-fig15.png)
   
4. <span data-ttu-id="f8151-234">Surface Hub 2S でパッケージを適用するときに、SEMM をアクティブ化するために必要な証明書の拇印の最後の2文字を保存します。</span><span class="sxs-lookup"><span data-stu-id="f8151-234">Save the certificate thumbprint’s last 2 characters, which is required to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="f8151-235">Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 ドライバーとファームウェアを含む USB フラッシュドライブを準備する</span><span class="sxs-lookup"><span data-stu-id="f8151-235">Prepare USB flash drive containing Windows 10 image, SEMM package, and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="f8151-236">次のいずれかのオプションを使用して、Windows 10 Pro または Enterprise のイメージ (バージョン1903以降) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f8151-236">You can install a Windows 10 Pro or Enterprise image (version 1903 or later) using one of the following options:</span></span>

- <span data-ttu-id="f8151-237">現在のイメージングソリューション。</span><span class="sxs-lookup"><span data-stu-id="f8151-237">Your current imaging solution.</span></span>

- <span data-ttu-id="f8151-238">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) を使用すると、現在のすべての windows 10 の更新プログラム、Office、その他のアプリ、および必要なドライバーとファームウェアを含む、起動可能な windows 10 イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f8151-238">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) lets you create a bootable Windows 10 image which can include all current Windows 10 updates, Office, other apps of your choice, as well as the required drivers and firmware.</span></span> 

- <span data-ttu-id="f8151-239">Windows 10 Pro または Enterprise のイメージが搭載された USB フラッシュドライブ。その後、  [Surface Hub 2 で windows 10 pro と ENTERPRISE OS 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-239">USB flash drive with Windows 10 Pro or Enterprise image, followed by installing  [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
<span data-ttu-id="f8151-240">この手順では、インストールメディアから USB フラッシュドライブを作成して、Surface Hub 2 の Windows 10 Pro と Enterprise OS 用の SEMM パッケージファイルとドライバーおよびファームウェアを追加する方法について説明します。MSI ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8151-240">This procedure describes creating a USB flash drive from installation media and then adding the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 .MSI file.</span></span> <span data-ttu-id="f8151-241">他の展開方法を使用している場合は、 [Surface Hub 2s の [UEFI の更新] に進み、OS の移行を有効に](#update-uefi-on-surface-hub-2s-to-enable-os-migration)します。</span><span class="sxs-lookup"><span data-stu-id="f8151-241">If you’re using other deployment methods, proceed to the section [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration).</span></span>

> [!NOTE]
> <span data-ttu-id="f8151-242">インストールが完了したら、既存の Windows 10 Team ライセンスとは別の Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8151-242">Once installed, you will need a valid license for Windows 10 Pro or Windows 10 Enterprise that is separate from your existing Windows 10 Team license.</span></span>

1. <span data-ttu-id="f8151-243">Windows 10 Pro のインストールを作成するには、「 [windows 10 のダウンロード](https://www.microsoft.com/software-download/windows10) 」ページの手順に従って、 **メディア作成** ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8151-243">To create a Windows 10 Pro installation, follow the instructions on the [Download Windows 10](https://www.microsoft.com/software-download/windows10) page for using the **Media Creation** tool.</span></span> <span data-ttu-id="f8151-244">Windows 10 Enterprise をダウンロードするには、 [Microsoft ボリュームライセンスサービスセンター](https://www.microsoft.com/licensing/servicecenter/default.aspx)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="f8151-244">To download Windows 10 Enterprise, go to the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).</span></span>

2. <span data-ttu-id="f8151-245">新しい **USB ストレージ** ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="f8151-245">Insert a new **USB storage** drive.</span></span> <span data-ttu-id="f8151-246">**メディア作成**ツールを起動し、[**インストールメディアの作成**] を選択して、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-246">Launch the **Media Creation** tool, select **Create installation media** and then select **Next**.</span></span>

   ![インストールメディアを作成する](images/shm-fig16.png)
   
3. <span data-ttu-id="f8151-248">[言語]、[Windows 10]、[64 ビット (x64)] の順に選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-248">Select language, Windows 10, and 64-bit (x64) and then select **Next**.</span></span>

   ![[言語]、[Windows 10]、[64 ビット] の & 選択し、[次へ] を選択します。](images/shm-fig17.png)
   
4. <span data-ttu-id="f8151-250">[ **USB フラッシュドライブ** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-250">Select **USB flash drive** and select **Next**.</span></span>

   ![USB フラッシュドライブを選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. <span data-ttu-id="f8151-252">ダウンロードが完了したら、[ **完了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-252">When the download completes, select **Finish**.</span></span>

   ![[完了] を選ぶ](images/shm-fig19.png)
   
6. <span data-ttu-id="f8151-254">Surface Hub 2 の Windows 10 Pro と Enterprise OS 用の SEMM パッケージファイルとドライバーおよびファームウェアをコピーします (.MSI ファイル) を、Windows 10 イメージを含む USB フラッシュドライブ (**Bootme**) のルートに保存します。</span><span class="sxs-lookup"><span data-stu-id="f8151-254">Copy the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (.MSI file) to the ROOT of the USB flash drive (**BOOTME**) containing your Windows 10 image.</span></span> <span data-ttu-id="f8151-255">BOOTME USB ドライブの内容:</span><span class="sxs-lookup"><span data-stu-id="f8151-255">BOOTME USB drive contains:</span></span>

    - <span data-ttu-id="f8151-256">Windows 10 の起動可能なイメージ。</span><span class="sxs-lookup"><span data-stu-id="f8151-256">Your Windows 10 bootable image.</span></span>
    
    - <span data-ttu-id="f8151-257">SEMM パッケージファイル (USB ドライブのルートにコピーされます)</span><span class="sxs-lookup"><span data-stu-id="f8151-257">SEMM package files (copied to the root of the USB drive)</span></span>
    
      - <span data-ttu-id="f8151-258">Dfi をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f8151-258">DfciUpdate.dfi.</span></span>
      - <span data-ttu-id="f8151-259">SEMM 拇印のテキストファイル。</span><span class="sxs-lookup"><span data-stu-id="f8151-259">Text file with the SEMM thumbprint.</span></span> <span data-ttu-id="f8151-260">(この例では、SurfaceUEFI_2020Aug25_1058.txt)自動生成された日付のタイムスタンプは、Surface UEFI コンフィギュレーターを使用してファイルを作成した日付に対応します。</span><span class="sxs-lookup"><span data-stu-id="f8151-260">(In this example: SurfaceUEFI_2020Aug25_1058.txt.) The auto-generated date timestamp corresponds to the date that you created the file using Surface UEFI Configurator.</span></span>

   - <span data-ttu-id="f8151-261">Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) 上の Windows 10 Pro および Enterprise OS 用のドライバーとファームウェアは、USB ドライブのルートにもコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f8151-261">Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi), also copied to the root of the USB drive.</span></span>

### <span data-ttu-id="f8151-262">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="f8151-262">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

1. <span data-ttu-id="f8151-263">**Boot me**ドライブを USB に挿入します。 Surface Hub 2S の A ポート。</span><span class="sxs-lookup"><span data-stu-id="f8151-263">Insert your **BOOTME** drive into the USB-A port on Surface Hub 2S.</span></span> <span data-ttu-id="f8151-264">(必要なファイルのリストについては、前のセクションを参照してください。)</span><span class="sxs-lookup"><span data-stu-id="f8151-264">(See the previous section for the list of required files.)</span></span>

2. <span data-ttu-id="f8151-265">UEFI を起動するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f8151-265">To boot into UEFI:</span></span>

   1. <span data-ttu-id="f8151-266">Surface Hub 2S の電源をオフにします (シャットダウンします)。</span><span class="sxs-lookup"><span data-stu-id="f8151-266">Power off (shutdown) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="f8151-267">**ボリューム +** を押しながら、**電源**ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="f8151-267">Press and hold **Volume +** and then press and release the **Power** button.</span></span>
   1. <span data-ttu-id="f8151-268">[UEFI] メニューが表示さ **れるまで、[保持]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="f8151-268">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![[UEFI] メニューが表示されるまで、holdling 音量を維持する](images/shm-fig20.png)
      
3. <span data-ttu-id="f8151-270">デバイスが再起動したら、前に作成した UEFI パスワード (該当する場合) を入力します (強くお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="f8151-270">When the device restarts, enter the UEFI password you created earlier, if applicable (strongly recommended).</span></span>

   ![デバイスが再起動したら、UEFI の paassword を入力します。](images/shm-fig22.png)
   
4. <span data-ttu-id="f8151-272">[UEFI] メニューで、[**管理**インストール (USB)] を選択し  >  **Install from USB**ます。</span><span class="sxs-lookup"><span data-stu-id="f8151-272">In the UEFI menu, select **Management** > **Install from USB**.</span></span>

   ![[管理 & [USB からインストール] を選ぶ](images/shm-fig21.png)
   
5. <span data-ttu-id="f8151-274">次に示すように、[ **今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-274">Select **Restart now**, as shown below.</span></span> <span data-ttu-id="f8151-275">デバイスが再起動し、画面の中央に白い4乗のロゴが表示され、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="f8151-275">The device will reboot and display the white 4-square logo in the middle of screen and then shut down.</span></span>

   ![[今すぐ再起動] を選択する](images/shm-fig25.png)
   
6. <span data-ttu-id="f8151-277">Power button を押して離すと、Surface Enterprise 管理モードのライセンス認証を求めるメッセージが赤い画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8151-277">Press and release the power button, a red screen will display prompting you to activate Surface Enterprise Management Mode.</span></span> 

7. <span data-ttu-id="f8151-278">2文字の **証明書の拇印**と、 **UEFI 設定のパスワード** を入力して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8151-278">Enter your two-character **certificate thumbprint**, your **UEFI settings password** and then select **OK**.</span></span>

   ![2文字の証明書の拇印を入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="f8151-280">デバイスで SEMM のライセンス認証を行うと、新しい UEFI 設定 **EnableOSMigration** が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8151-280">Once you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="f8151-281">Windows 10 チームにはアクセスできなくなり、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8151-281">You will no longer be able to access Windows 10 Team and must proceed to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span> 

8. <span data-ttu-id="f8151-282">デバイスが再起動し、白い4マスのロゴが画面中央に表示されます。その後、もう一度終了します。</span><span class="sxs-lookup"><span data-stu-id="f8151-282">The device will reboot, display the white 4-square logo in the middle of the screen, and then it will shut down again.</span></span>

### <span data-ttu-id="f8151-283">Windows 10 Pro または Enterprise をインストールする</span><span class="sxs-lookup"><span data-stu-id="f8151-283">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="f8151-284">起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-ポートにまだ入っていない場合は、ここで挿入して、電源ボタンを押してから離します。</span><span class="sxs-lookup"><span data-stu-id="f8151-284">If your bootable Windows 10 Pro or Enterprise drive is not already in the Surface Hub 2 USB-A port, insert it now and then press and release the power button.</span></span>

2. <span data-ttu-id="f8151-285">デバイスが起動し、画面の中央に白い4乗が表示され、白い4乗のロゴの下にスピンした円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8151-285">The device will start, you will see the white 4-square in the middle of the screen, and then you will see a spinning circle below the white four-square logo.</span></span>

3. <span data-ttu-id="f8151-286">デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切ってください (電源コードを外して、もう一度接続します)。</span><span class="sxs-lookup"><span data-stu-id="f8151-286">If the device does not automatically boot to the USB drive, power off the device (unplug the power cord and plug it back in).</span></span> <span data-ttu-id="f8151-287">電源コードをもう一度接続すると、デバイスは画面中央の白い4乗ロゴに数秒経ってから起動します。または、電源ボタンを押して離すと、デバイスの電源を入れ直すことができます。</span><span class="sxs-lookup"><span data-stu-id="f8151-287">After plugging the power cord back in, the device should boot after a few seconds to the white 4-square logo in the middle of screen, or you can press and release the power button to turn the device back on.</span></span> <span data-ttu-id="f8151-288">画面の中央に4乗のロゴが表示されたらすぐに、[音量を下げる] ボタンを長押しして、白い4乗ロゴの下にスピンした円が表示されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="f8151-288">Immediately after you see the 4-square logo in the middle of the screen, press and hold the volume down button until you see the spinning circle below the white four-square logo.</span></span>
 
   ![USB から Windows 10 への起動](images/shm-fig26.png)
   
4. <span data-ttu-id="f8151-290">既定のエクスペリエンス (OOBE) セットアップが起動したら、指示に従って Windows 10 Pro または Enterprise (バージョン1903以降) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-290">When the out-of-box experience (OOBE) setup launches, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="f8151-291">Surface Hub 2 ドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="f8151-291">Install Surface Hub 2 drivers and firmware</span></span>

 - <span data-ttu-id="f8151-292">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8151-292">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise OS on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
### <span data-ttu-id="f8151-293">次のステップ</span><span class="sxs-lookup"><span data-stu-id="f8151-293">Next steps</span></span>

<span data-ttu-id="f8151-294">Surface Hub をパーソナルの生産性デバイスとして完全に構成する方法については、「 [Surface hub 2 で Windows 10 Pro または Enterprise を構成](surface-hub-2-post-install.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8151-294">To fully configure Surface Hub 2S as a personal productivity device, see [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).</span></span>

> [!NOTE]
><span data-ttu-id="f8151-295">このドキュメントで説明されている手順を実行しても、Surface Hub 2 のデバイスを Windows 10 Pro または Enterprise に移行できなかった場合は、 [Surface hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="f8151-295">If following the steps outlined in this document is unsuccessful in migrating your device to Windows 10 Pro or Enterprise for Surface Hub 2, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

### <span data-ttu-id="f8151-296">Windows 10 チームへのロールバック</span><span class="sxs-lookup"><span data-stu-id="f8151-296">Rolling back to Windows 10 Team</span></span>

<span data-ttu-id="f8151-297">デバイスを Windows 10 チームに復元する場合は、「 [Surface Hub 2s のリセットと回復](surface-hub-2s-recover-reset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8151-297">If you would Like to restore your device to Windows 10 Team, refer to [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span>

## <span data-ttu-id="f8151-298">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="f8151-298">Version history</span></span>

| <span data-ttu-id="f8151-299">バージョン</span><span class="sxs-lookup"><span data-stu-id="f8151-299">Version</span></span> | <span data-ttu-id="f8151-300">日付</span><span class="sxs-lookup"><span data-stu-id="f8151-300">Date</span></span>               | <span data-ttu-id="f8151-301">説明</span><span class="sxs-lookup"><span data-stu-id="f8151-301">Description</span></span>                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8151-302">部.</span><span class="sxs-lookup"><span data-stu-id="f8151-302">v.</span></span> <span data-ttu-id="f8151-303">1.2</span><span class="sxs-lookup"><span data-stu-id="f8151-303">1.2</span></span>  | <span data-ttu-id="f8151-304">2020年9月29日</span><span class="sxs-lookup"><span data-stu-id="f8151-304">September 29, 2020</span></span> | <span data-ttu-id="f8151-305">ユーザビリティのフィードバックごとのその他の更新。</span><span class="sxs-lookup"><span data-stu-id="f8151-305">Miscellaneous updates per usability feedback.</span></span>                                                        |
| <span data-ttu-id="f8151-306">部.</span><span class="sxs-lookup"><span data-stu-id="f8151-306">v.</span></span> <span data-ttu-id="f8151-307">1.1</span><span class="sxs-lookup"><span data-stu-id="f8151-307">1.1</span></span>  | <span data-ttu-id="f8151-308">2020年9月15日</span><span class="sxs-lookup"><span data-stu-id="f8151-308">September 15, 2020</span></span> | <span data-ttu-id="f8151-309">「概要」で追加のメモを追加して、新しい OS をインストールするためのライセンス要件を明確にします。</span><span class="sxs-lookup"><span data-stu-id="f8151-309">Placed additional note in the Introduction clarifying licensing requirements for installing a new OS.</span></span> |
| <span data-ttu-id="f8151-310">部.</span><span class="sxs-lookup"><span data-stu-id="f8151-310">v.</span></span> <span data-ttu-id="f8151-311">1.0</span><span class="sxs-lookup"><span data-stu-id="f8151-311">1.0</span></span>  | <span data-ttu-id="f8151-312">2020年9月1日</span><span class="sxs-lookup"><span data-stu-id="f8151-312">September 1, 2020</span></span>  | <span data-ttu-id="f8151-313">新しい記事。</span><span class="sxs-lookup"><span data-stu-id="f8151-313">New article.</span></span>                                                                                           |
