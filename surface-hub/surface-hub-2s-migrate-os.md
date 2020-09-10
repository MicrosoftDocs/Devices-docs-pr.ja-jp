---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 上の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行するプロセスについて説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e47ee735c0ba1cc0782c892b64d50f7e9d09f355
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004489"
---
# <span data-ttu-id="17a22-104">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="17a22-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

## <span data-ttu-id="17a22-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="17a22-105">Introduction</span></span>

<span data-ttu-id="17a22-106">Surface Hub 2S は、Windows 10 チームでプレインストールされています。カスタマイズされた Windows 10 は、会議室環境での共同作業が容易になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="17a22-106">Surface Hub 2S comes pre-installed with Windows 10 Team, a customized edition of Windows 10 designed to facilitate easy collaboration in meeting room environments.</span></span> <span data-ttu-id="17a22-107">これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub の2S を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="17a22-107">Now you have the option of running Windows 10 Pro or Enterprise to use Surface Hub 2S much like any other PC.</span></span> 

> [!IMPORTANT]
><span data-ttu-id="17a22-108">通常のアップグレードや移行とは異なり、このプロセスでは、このページの説明に従って、規範となる手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-108">Unlike a typical upgrade or migration, this process requires you to follow a prescriptive procedure, as described on this page.</span></span> <span data-ttu-id="17a22-109">続行する前に、 [ソリューションのコンポーネント](#solution-components) と [移行ワークフロー](#migration-workflow-summary) を確認します。</span><span class="sxs-lookup"><span data-stu-id="17a22-109">Review the [Solution components](#solution-components) and [Migration workflow](#migration-workflow-summary) before proceeding.</span></span>

<span data-ttu-id="17a22-110">別個の PC とダウンロード可能なツールを使用して、Windows 10 チームから移行を開始します。 surface **UEFI コンフィギュレーター** --Surface Hub 2s に適用する新しい UEFI 設定を含むパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="17a22-110">You start the migration from Windows 10 Team using a separate PC and downloadable tool -- **Surface UEFI Configurator** --  to create a package containing a new UEFI setting that you apply to Surface Hub 2S.</span></span>  <span data-ttu-id="17a22-111">Surface Enterprise Management Mode (SEMM) へのインターフェイスとしての surface の構成機能。これは、企業環境の Surface デバイスでのファームウェア設定の一元管理を容易にするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="17a22-111">Surface UEFI Configurator functions as an interface into Surface Enterprise Management Mode (SEMM), designed to facilitate centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="17a22-112">SEMM の詳細については、「 [Microsoft Surface Enterprise 管理モードのドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17a22-112">To learn more about SEMM, see [Microsoft Surface Enterprise Management Mode documentation](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 

## <span data-ttu-id="17a22-113">ソリューションのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="17a22-113">Solution Components</span></span>

- <span data-ttu-id="17a22-114">Windows 10 Team オペレーティングシステムを実行している Surface Hub 2S デバイス</span><span class="sxs-lookup"><span data-stu-id="17a22-114">Surface Hub 2S device running Windows 10 Team operating system</span></span>
- <span data-ttu-id="17a22-115">Windows 10 を実行している別のデバイス</span><span class="sxs-lookup"><span data-stu-id="17a22-115">Separate device running Windows 10</span></span>
- <span data-ttu-id="17a22-116">Surface UEFI コンフィギュレーターツール</span><span class="sxs-lookup"><span data-stu-id="17a22-116">Surface UEFI Configurator tool</span></span>
- <span data-ttu-id="17a22-117">Windows 10 Pro または Enterprise OS イメージ、バージョン1903以上</span><span class="sxs-lookup"><span data-stu-id="17a22-117">Windows 10 Pro or Enterprise OS image, version 1903 or greater</span></span>
- <span data-ttu-id="17a22-118">2 GB の記憶域を持つ2つの USB ドライブ、FAT32 形式</span><span class="sxs-lookup"><span data-stu-id="17a22-118">Two USB drives with 16GB of storage, FAT32 format</span></span>
- <span data-ttu-id="17a22-119">Windows 10 Pro および Enterprise のドライバーとファームウェアは Surface Hub 2、Windows Installer で使用できます。MSI ファイル</span><span class="sxs-lookup"><span data-stu-id="17a22-119">Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2, Windows Installer .MSI file</span></span>
- <span data-ttu-id="17a22-120">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="17a22-120">Internet connection</span></span>
- <span data-ttu-id="17a22-121">イメージングソリューション (オプション)</span><span class="sxs-lookup"><span data-stu-id="17a22-121">Imaging solution (optional)</span></span>

 
## <span data-ttu-id="17a22-122">移行ワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="17a22-122">Migration workflow summary</span></span>

| <span data-ttu-id="17a22-123">ステップ</span><span class="sxs-lookup"><span data-stu-id="17a22-123">Step</span></span>  | <span data-ttu-id="17a22-124">操作</span><span class="sxs-lookup"><span data-stu-id="17a22-124">Action</span></span>                                                                                                 | <span data-ttu-id="17a22-125">まとめ</span><span class="sxs-lookup"><span data-stu-id="17a22-125">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="17a22-126">件</span><span class="sxs-lookup"><span data-stu-id="17a22-126">1</span></span> | [<span data-ttu-id="17a22-127">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="17a22-127">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | <span data-ttu-id="17a22-128">UEFI バージョンが694.2938.768.0 以降であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="17a22-128">Ensure the UEFI version is 694.2938.768.0 or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="17a22-129">両面</span><span class="sxs-lookup"><span data-stu-id="17a22-129">2</span></span> | [<span data-ttu-id="17a22-130">ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="17a22-130">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="17a22-131">Surface Tools から [surface](https://www.microsoft.com/download/details.aspx?id=46703) をダウンロードして、別の PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-131">Download [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) from Surface Tools for IT and install it on a separate PC.</span></span> <span data-ttu-id="17a22-132">[Surface Hub 2 で Windows 10 Pro と Enterprise のドライバーとファームウェアをダウンロードします。MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)を保存して、手順5で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="17a22-132">Download [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) and save it for use in Step 5.</span></span> |
| <span data-ttu-id="17a22-133">-</span><span class="sxs-lookup"><span data-stu-id="17a22-133">3</span></span> | [<span data-ttu-id="17a22-134">SEMM 証明書の準備</span><span class="sxs-lookup"><span data-stu-id="17a22-134">Prepare SEMM certificate</span></span>](#prepare-semm-certificate)                                                                          | <span data-ttu-id="17a22-135">Surface UEFI コンフィギュレーターの実行に必要な証明書を準備するか、現在の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="17a22-135">Prepare required certificate for running Surface UEFI Configurator or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="17a22-136">4d</span><span class="sxs-lookup"><span data-stu-id="17a22-136">4</span></span> | [<span data-ttu-id="17a22-137">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="17a22-137">Create SEMM package</span></span>](#create-semm-package)                                                                               | <span data-ttu-id="17a22-138">Surface UEFI コンフィギュレーターを起動して USB ドライブ上に SEMM パッケージを作成します。これには、Surface Hub 2S に適用する必要な構成ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="17a22-138">Launch Surface UEFI Configurator to create a SEMM package on a USB drive which will contain the required configuration files to apply on Surface Hub 2S.</span></span> <span data-ttu-id="17a22-139">これらの SEMM パッケージファイルを PC 上のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="17a22-139">Copy these SEMM package  files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="17a22-140">個</span><span class="sxs-lookup"><span data-stu-id="17a22-140">5</span></span> | [<span data-ttu-id="17a22-141">Windows 10 イメージ、SEMM パッケージ、および Windows 10 Pro とドライバーとファームウェアを含む USB フラッシュドライブを Surface Hub 2 で準備する</span><span class="sxs-lookup"><span data-stu-id="17a22-141">Prepare USB flash drive containing Windows 10 image, SEMM package, and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2</span></span>](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="17a22-142">Windows 10 イメージを含む USB ドライブ (この例では **Bootme** という名前) を作成します。</span><span class="sxs-lookup"><span data-stu-id="17a22-142">Create a single USB drive (named **BOOTME** in this example) containing a Windows 10 image.</span></span> <span data-ttu-id="17a22-143">Windows 10 Pro と Enterprise 用のドライバーとファームウェアを Surface Hub 2 (手順 2) と SEMM パッケージファイル (手順 4) に追加して、 **Bootme** ドライブに追加します。</span><span class="sxs-lookup"><span data-stu-id="17a22-143">Add your Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 (Step 2) and SEMM package files (Step 4) to the **BOOTME** drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="17a22-144">=</span><span class="sxs-lookup"><span data-stu-id="17a22-144">6</span></span> | [<span data-ttu-id="17a22-145">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="17a22-145">Update UEFI on Surface Hub 2S to enable OS migration</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="17a22-146">**Bootme**ドライブを使って、[UEFI] メニューに Surface Hub 2s を起動し、semm パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-146">Use the **BOOTME** drive to boot Surface Hub 2S to the UEFI menu and install SEMM package.</span></span>|
| <span data-ttu-id="17a22-147">日</span><span class="sxs-lookup"><span data-stu-id="17a22-147">7</span></span> | [<span data-ttu-id="17a22-148">Windows 10 Pro または Enterprise バージョン1903以降をインストールする</span><span class="sxs-lookup"><span data-stu-id="17a22-148">Install Windows 10 Pro or Enterprise version 1903 or later</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="17a22-149">**Bootme**ドライブを使用して、 **Windows 10 Pro または Enterprise**バージョン1903以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-149">Use the **BOOTME** drive to Install **Windows 10 Pro or Enterprise** version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="17a22-150">個</span><span class="sxs-lookup"><span data-stu-id="17a22-150">8</span></span> | [<span data-ttu-id="17a22-151">Surface Hub 2 の Windows 10 Pro と Enterprise 用のドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="17a22-151">Install Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="17a22-152">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と Enterprise 用のドライバーとファームウェアをインストールします。MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)</span><span class="sxs-lookup"><span data-stu-id="17a22-152">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974)</span></span>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="17a22-153">ファイブ</span><span class="sxs-lookup"><span data-stu-id="17a22-153">9</span></span> | [<span data-ttu-id="17a22-154">パーソナル生産性デバイスとして Surface Hub 2S を完全に構成する</span><span class="sxs-lookup"><span data-stu-id="17a22-154">Fully configure Surface Hub 2S as a personal productivity device</span></span>](#next-steps)                                        |  <span data-ttu-id="17a22-155">推奨される設定とアプリケーションのセットを有効にして、個人用生産性デバイスとして Surface Hub 2S の使用を最適化します。</span><span class="sxs-lookup"><span data-stu-id="17a22-155">Enable the set of recommended settings and applications to optimize use of Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="17a22-156">Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する</span><span class="sxs-lookup"><span data-stu-id="17a22-156">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>

<span data-ttu-id="17a22-157">Surface Hub を Windows 10 Team から Windows 10 デスクトップに移行する前に、 **694.2938.768.0**の最小 UEFI バージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="17a22-157">The minimum UEFI version required prior to migrating the Surface Hub from Windows 10 Team to Windows 10 Desktop is **694.2938.768.0**.</span></span>
 
**<span data-ttu-id="17a22-158">システムの現在の UEFI バージョンを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="17a22-158">To verify the current UEFI version on your system:</span></span>**

1. <span data-ttu-id="17a22-159">Surface Hub 2s ホーム画面で、[**開始**] を選択し、 **SurfaceApp** (**すべてのアプリ**の  >  **サーフェス**) を開きます。</span><span class="sxs-lookup"><span data-stu-id="17a22-159">On Surface Hub 2S home screen, select **Start** and open the **SurfaceApp** (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="17a22-160">**Surface**を選択して、surface Hub に関する情報を表示します。これには、デバイス上の UEFI の最新バージョンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="17a22-160">Select **Your Surface** to display information about the Surface Hub, including the current version of the UEFI on the device.</span></span> <span data-ttu-id="17a22-161">以下に示すように、UEFI バージョンが **694.2938.768.0** 以降の場合、uefi は、OS の移行を有効にするための semm パッケージの作成に適しています。</span><span class="sxs-lookup"><span data-stu-id="17a22-161">If the UEFI version is **694.2938.768.0** or later as shown below, the UEFI is eligible for you to create the SEMM package to enable OS migration.</span></span>

    ![Surface アプリを開く & Surface を選択します。](images/shm-fig1.png)
 
3. <span data-ttu-id="17a22-163">UEFI バージョンがバージョン **694.2938.768.0**よりも古い場合は、Windows Update を使用して現在のバージョンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-163">If the UEFI version is earlier than version **694.2938.768.0**, you will need to obtain a current version using Windows Update.</span></span>

**<span data-ttu-id="17a22-164">Windows Update から UEFI を更新するには:</span><span class="sxs-lookup"><span data-stu-id="17a22-164">To update UEFI from Windows Update:</span></span>**
1. <span data-ttu-id="17a22-165">Surface Hub 2s の場合は、**管理者**としてサインインし、[**すべてのアプリ**の設定]、[  >  **Settings** >  **セキュリティ**  >  **Windows Update** ] の順に移動して、すべての更新プログラムをインストールしてから、デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="17a22-165">On your Surface Hub 2S, sign in as an **Admin**, go to **All apps** > **Settings**> **Update and Security** > **Windows Update** and install all updates, then restart the device.</span></span> <span data-ttu-id="17a22-166">Surface アプリを使用して、UEFI バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="17a22-166">Verify the UEFI version using the Surface App.</span></span> <span data-ttu-id="17a22-167">注: ユーザー名または管理者のパスワードがわからない場合は、デバイスをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-167">Note: If you do not know your username or admin password, you will need to reset the device.</span></span> <span data-ttu-id="17a22-168">詳細については、「 [Surface Hub 2s のリセットと回復](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17a22-168">To learn more, see [Reset and recovery for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span></span>

2. <span data-ttu-id="17a22-169">UEFI バージョンが **694.2938.768.0** 以降になるまで、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="17a22-169">Repeat these steps until the UEFI version is **694.2938.768.0** or later.</span></span>

3. <span data-ttu-id="17a22-170">まだ更新されている UEFI が何回も表示されない場合は、 **更新履歴** を確認して、失敗したファームウェアインストールのインスタンスを探します。</span><span class="sxs-lookup"><span data-stu-id="17a22-170">If you still do not see the updated UEFI after multiple attempts, check **Update History** and look for any instances of failed firmware installations.</span></span> <span data-ttu-id="17a22-171">デバイスをリセットする必要がある場合があります (**設定**  >  **更新 & セキュリティ**  >  **リセットデバイス**)。</span><span class="sxs-lookup"><span data-stu-id="17a22-171">You may need to reset your device (**Settings** > **Update & security** > **Reset device**).</span></span>

### <span data-ttu-id="17a22-172">ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="17a22-172">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="17a22-173">別の PC では、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="17a22-173">On a separate PC:</span></span>

- <span data-ttu-id="17a22-174">Surface Tools から Microsoft [SURFACE UEFI コンフィギュレーター](https://www.microsoft.com/download/details.aspx?id=46703) をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-174">Download and install Microsoft [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) from Surface Tools for IT.</span></span> <span data-ttu-id="17a22-175">Surface UEFI コンフィギュレーターは Surface Hub 2S では実行できませんが、Windows 10 Team はインストールされています。</span><span class="sxs-lookup"><span data-stu-id="17a22-175">Surface UEFI Configurator cannot be run on Surface Hub 2S, while Windows 10 Team is installed.</span></span>

- <span data-ttu-id="17a22-176">[Surface Hub 2 ドライバーとファームウェア Windows インストーラーをダウンロードします。](https://www.microsoft.com/download/details.aspx?id=101974)新しいオペレーティングシステムをインストールするときに適用される MSI ファイル。</span><span class="sxs-lookup"><span data-stu-id="17a22-176">Download [Surface Hub 2 Drivers and Firmware Windows Installer .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) to be applied when installing the new operating system.</span></span>

### <span data-ttu-id="17a22-177">SEMM 証明書の準備</span><span class="sxs-lookup"><span data-stu-id="17a22-177">Prepare SEMM certificate</span></span>

<span data-ttu-id="17a22-178">Surface UEFI コンフィギュレーターを初めて使用する場合は、証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-178">If this is your first time using Surface UEFI Configurator, you’ll need to prepare a certificate.</span></span> <span data-ttu-id="17a22-179">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI 設定を変更できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="17a22-179">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify UEFI settings.</span></span> <span data-ttu-id="17a22-180">証明書を取得する方法は、組織の規模または複雑さによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-180">How you acquire a certificate may vary depending on the size or complexity of your organization:</span></span>

- <span data-ttu-id="17a22-181">大規模なエンタープライズ組織では、通常、標準セキュリティの慣行ごとに証明書を生成する独自の証明書インフラストラクチャを維持しています。</span><span class="sxs-lookup"><span data-stu-id="17a22-181">Large enterprise organizations typically maintain their own certificate infrastructure to generate certificates per standard security practices.</span></span>

- <span data-ttu-id="17a22-182">中規模企業やその他のユーザーが、サードパーティプロバイダーから証明書を取得することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="17a22-182">Medium-sized businesses and others may choose to obtain a certificate from third party providers.</span></span> <span data-ttu-id="17a22-183">これは、十分な IT 専門知識または専任の IT セキュリティチームを持たない組織向けの推奨オプションです。</span><span class="sxs-lookup"><span data-stu-id="17a22-183">This is the recommended option for organizations without sufficient IT expertise or dedicated IT security team.</span></span>

- <span data-ttu-id="17a22-184">または、次のドキュメントに記載されている PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 [Surface Enterprise 管理モードの証明書の要件](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。</span><span class="sxs-lookup"><span data-stu-id="17a22-184">Alternatively, you can generate a self-signed certificate with a PowerShell script per the following documentation: [Surface Enterprise Management Mode certificate requirements](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span> <span data-ttu-id="17a22-185">または、PowerShell を使用して、次のドキュメントに従って独自の証明書を作成します。[新正書法 certificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps)</span><span class="sxs-lookup"><span data-stu-id="17a22-185">Or use PowerShell to create your own certificate per the following documentation: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps).</span></span>

<span data-ttu-id="17a22-186">UEFI 設定を適用する前に、構成ファイルの署名を確認するために、SEMM パッケージを証明書を使用して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-186">The SEMM package must be secured with a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="17a22-187">詳細については、「 [Surface Enterprise 管理モード](https://docs.microsoft.com/surface/surface-enterprise-management-mode) のドキュメント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17a22-187">To learn more, see [Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode) documentation.</span></span>
 
 
### <span data-ttu-id="17a22-188">SEMM パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="17a22-188">Create SEMM package</span></span>

1. <span data-ttu-id="17a22-189">**SURFACE UEFI コンフィギュレーター**を開き、[**開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-189">Open **Surface UEFI Configurator** and select **Start**.</span></span>

   ![Open Surface UEFI コンフィギュレーター](images/shm-fig2.png)
   
2. <span data-ttu-id="17a22-191">[ **Surface デバイス** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-191">Select **Surface Devices** and then select **Next**.</span></span>

   ![Surface デバイスの選択](images/shm-fig3.png)
  
3. <span data-ttu-id="17a22-193">[ **構成パッケージ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-193">Select **Configuration Package**.</span></span>

   ![構成パッケージを選ぶ](images/shm-fig4.png)
  
4. <span data-ttu-id="17a22-195">[ **証明書の保護**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-195">Select **Certificate Protection**.</span></span>

   ![証明書の保護を選ぶ](images/shm-fig5.png)

5. <span data-ttu-id="17a22-197">証明書 .pfx ファイルを追加するように求められます。</span><span class="sxs-lookup"><span data-stu-id="17a22-197">You will be prompted to add your certificate .pfx file.</span></span>

   ![証明書を追加するように求められます。](images/shm-fig6.png)
   
6. <span data-ttu-id="17a22-199">**証明書のパスワード**を入力して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-199">Enter your **Certificate password** and select **OK**.</span></span>

   ![証明書のパスワードを入力して、[OK] を選択します。](images/shm-fig7.png)

7. <span data-ttu-id="17a22-201">Surface UEFI にパスワードを追加するには、[ **パスワードによる保護** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-201">Select **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="17a22-202">このパスワードは、UEFI を起動するたびに必要になります。</span><span class="sxs-lookup"><span data-stu-id="17a22-202">This password will be required whenever you boot to UEFI.</span></span> <span data-ttu-id="17a22-203">Surface Hub 2S で使用する UEFI パスワードを設定する **ことを強くお勧め** します。</span><span class="sxs-lookup"><span data-stu-id="17a22-203">It is **strongly recommended** to set a UEFI password you will use on Surface Hub 2S.</span></span>

   ![[パスワードによる保護] をクリック](images/shm-fig8.png)
   
8. <span data-ttu-id="17a22-205">**UEFI パスワード**を設定して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-205">Set a **UEFI password** and select **OK**.</span></span>

   ![UEFI パスワードを入力する](images/shm-fig9.png)

   > [!IMPORTANT]
   > <span data-ttu-id="17a22-207">パスワードをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="17a22-207">Make a note of your password.</span></span> <span data-ttu-id="17a22-208">パスワードを忘れた場合、または紛失した場合は、回復処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="17a22-208">If you forget or lose your password, there is no recovery process.</span></span> 

9. <span data-ttu-id="17a22-209">[ **Surface Hub 2s** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-209">Select **Surface Hub 2S** and then select **Next**.</span></span>

   ![Surface Hub 2S の選択](images/shm-fig10.png)
   
10. <span data-ttu-id="17a22-211">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-211">Select **Next**.</span></span>

    ![[次へ] を選ぶ](images/shm-fig10a.png)

11. <span data-ttu-id="17a22-213">Windows 10 Pro または Enterprise のインストールを許可するには、[EnableOsMigration] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="17a22-213">To allow installation of Windows 10 Pro or Enterprise, select **EnableOsMigration.**</span></span>

    ![[OS の移行を有効にする] を選ぶ](images/shm-fig11.png)
    
12. <span data-ttu-id="17a22-215">**EnableOSMigration**を **[オン**] に設定して、[**次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-215">Set **EnableOSMigration** to **On** and select **Next**.</span></span>

    ![[OS 移行の有効化] を [オン] に設定する](images/shm-fig12.png)

> [!NOTE]
> <span data-ttu-id="17a22-217">SEMM パッケージを適用した後は、デバイスの UEFI メニューですべての UEFI 設定が灰色表示になります (ロックされています)。</span><span class="sxs-lookup"><span data-stu-id="17a22-217">After you apply a SEMM package, all UEFI settings will display as grayed out (locked) in the UEFI menu on the device.</span></span> <span data-ttu-id="17a22-218">これには、PXE ブート用 IPv6 など、他の設定の既定値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17a22-218">This includes default values for other settings such as IPv6 for PXE Boot.</span></span> <span data-ttu-id="17a22-219">UEFI の設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-219">To modify UEFI settings, you will need to apply another SEMM package or unenroll the device from SEMM.</span></span>

#### <span data-ttu-id="17a22-220">SEMM パッケージを USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="17a22-220">Save SEMM package to USB drive</span></span>

1. <span data-ttu-id="17a22-221">USB ドライブを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="17a22-221">Connect a USB Drive to your PC.</span></span> <span data-ttu-id="17a22-222">[ **Hub 2s** ] を選び、[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-222">Choose **Hub 2S** and then select **Next**.</span></span>

   ![USB を選ぶ](images/shm-fig13.png)
   
2. <span data-ttu-id="17a22-224">[ **ビルド**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-224">Select **Build**.</span></span>

   ![[ビルド] を選ぶ](images/shm-fig14.png)

3. <span data-ttu-id="17a22-226">このページのスクリーンショットをキャプチャして、[ **終了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-226">Capture a screenshot of this page and then select **End**.</span></span> <span data-ttu-id="17a22-227">SEMM パッケージは現在準備が整っており、semm パッケージ **Dfciupdate** と、semm 拇印 (証明書の拇印の最後の2文字) を含むテキストファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="17a22-227">Your SEMM package is now ready and contains the SEMM package **DfciUpdate.dfi** and a text file with the SEMM thumbprint (the last two characters of the certificate’s thumbprint).</span></span>

   ![[終了] を選ぶ](images/shm-fig15.png)
   
4. <span data-ttu-id="17a22-229">Surface Hub 2S でパッケージを適用するときに、SEMM をアクティブ化するために必要な証明書の拇印の最後の2文字を保存します。</span><span class="sxs-lookup"><span data-stu-id="17a22-229">Save the certificate thumbprint’s last 2 characters, which is required to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="17a22-230">Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 ドライバーとファームウェアを含む USB フラッシュドライブを準備する</span><span class="sxs-lookup"><span data-stu-id="17a22-230">Prepare USB flash drive containing Windows 10 image, SEMM package, and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="17a22-231">次のいずれかのオプションを使用して、Windows 10 Pro または Enterprise のイメージ (バージョン1903以降) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="17a22-231">You can install a Windows 10 Pro or Enterprise image (version 1903 or later) using one of the following options:</span></span>

- <span data-ttu-id="17a22-232">現在のイメージングソリューション。</span><span class="sxs-lookup"><span data-stu-id="17a22-232">Your current imaging solution.</span></span>

- <span data-ttu-id="17a22-233">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) では、現在使用しているすべての windows 10 の更新プログラム、Office、その他のアプリ、および必要なドライバーとファームウェアを含めることができる起動可能な windows 10 イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="17a22-233">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) lets you create a bootable Windows 10 image which can include all of the current Windows 10 updates, Office, other apps of your choice, as well as the required drivers and firmware.</span></span> 

- <span data-ttu-id="17a22-234">Windows 10 Pro または Enterprise のイメージが搭載された USB フラッシュドライブ。その後、  [Surface Hub 2 で windows 10 pro と enterprise 用のドライバーとファームウェアを](https://www.microsoft.com/download/details.aspx?id=101974)インストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-234">USB flash drive with Windows 10 Pro or Enterprise image, followed by installing  [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 

<span data-ttu-id="17a22-235">この手順では、インストールメディアから USB フラッシュドライブを作成して、Windows 10 Pro とドライバーとファームウェアを Surface Hub 2 で追加します。MSI ファイル。</span><span class="sxs-lookup"><span data-stu-id="17a22-235">This procedure describes creating a USB flash drive from installation media and then adding the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file.</span></span> <span data-ttu-id="17a22-236">他の展開方法を使用している場合は、次のセクション「 [Surface Hub 2s で UEFI を更新して OS の移行を有効](#update-uefi-on-surface-hub-2s-to-enable-os-migration)にする」に進みます。</span><span class="sxs-lookup"><span data-stu-id="17a22-236">If you’re using other deployment methods, proceed to the following section: [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration).</span></span>

> [!NOTE]
> <span data-ttu-id="17a22-237">インストールが完了したら、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="17a22-237">Once installed, you will need a valid license for Windows 10 Pro or Windows 10 Enterprise.</span></span>

1. <span data-ttu-id="17a22-238">Windows 10 Pro のインストールを作成するには、「 [windows 10 のダウンロード](https://www.microsoft.com/software-download/windows10) 」ページの手順に従って、 **メディア作成** ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="17a22-238">To create a Windows 10 Pro installation, follow the instructions on the [Download Windows 10](https://www.microsoft.com/software-download/windows10) page for using the **Media Creation** tool.</span></span> <span data-ttu-id="17a22-239">Windows 10 Enterprise をダウンロードするには、 [Microsoft ボリュームライセンスサービスセンター](https://www.microsoft.com/licensing/servicecenter/default.aspx)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="17a22-239">To download Windows 10 Enterprise, go to the [Microsoft Volume Licensing Service Center.](https://www.microsoft.com/licensing/servicecenter/default.aspx).</span></span>

2. <span data-ttu-id="17a22-240">新しい **USB ストレージ** ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="17a22-240">Insert a new **USB storage** drive.</span></span> <span data-ttu-id="17a22-241">**メディア作成**ツールを起動し、[**インストールメディアの作成**] を選択して、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-241">Launch the **Media Creation** tool, select **Create installation media** and then select **Next**.</span></span>

   ![インストールメディアを作成する](images/shm-fig16.png)
   
3. <span data-ttu-id="17a22-243">[言語]、[Windows 10]、[64 ビット (x64)] の順に選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-243">Select language, Windows 10, and 64-bit (x64) and then select **Next**.</span></span>

   ![[言語]、[Windows 10]、[64 ビット] の & 選択し、[次へ] を選択します。](images/shm-fig17.png)
   
4. <span data-ttu-id="17a22-245">[ **USB フラッシュドライブ** ] を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-245">Select **USB flash drive** and select **Next**.</span></span>

   ![USB フラッシュドライブを選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. <span data-ttu-id="17a22-247">ダウンロードが完了したら、[ **完了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-247">When the download completes, select **Finish**.</span></span>

   ![[完了] を選ぶ](images/shm-fig19.png)
   
6. <span data-ttu-id="17a22-249">Surface Hub 2 の Windows 10 Pro および Enterprise 用の SEMM パッケージファイルとドライバーおよびファームウェアをコピーします。Windows 10 イメージを含む USB フラッシュドライブ (**Bootme**) への MSI。</span><span class="sxs-lookup"><span data-stu-id="17a22-249">Copy the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI to the USB flash drive (**BOOTME**) containing your Windows 10 image:</span></span>

    - <span data-ttu-id="17a22-250">DfciUpdate</span><span class="sxs-lookup"><span data-stu-id="17a22-250">DfciUpdate.dfi</span></span>
    - <span data-ttu-id="17a22-251">SEMM 拇印のテキストファイル。</span><span class="sxs-lookup"><span data-stu-id="17a22-251">Text file with the SEMM thumbprint.</span></span> <span data-ttu-id="17a22-252">(この例では、SurfaceUEFI_2020Aug25_1058.txt)</span><span class="sxs-lookup"><span data-stu-id="17a22-252">(In this example: SurfaceUEFI_2020Aug25_1058.txt)</span></span>
    - <span data-ttu-id="17a22-253">Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) での Windows 10 Pro と Enterprise のドライバーとファームウェア</span><span class="sxs-lookup"><span data-stu-id="17a22-253">Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)</span></span>

### <span data-ttu-id="17a22-254">Surface Hub 2S で UEFI を更新して OS の移行を有効にする</span><span class="sxs-lookup"><span data-stu-id="17a22-254">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

<span data-ttu-id="17a22-255">**Bootme**ドライブを使って、semm パッケージファイルをインストールし、UEFI を更新して、Windows 10 Pro または Enterprise を実行できるように Surface Hub を有効にします。</span><span class="sxs-lookup"><span data-stu-id="17a22-255">Use your **BOOTME** drive to install the SEMM package files and update the UEFI, enabling Surface Hub to run Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="17a22-256">次に、 **Bootme** ドライブから起動して、Windows 10 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-256">Then boot from the **BOOTME** drive to install Windows 10.</span></span>

1. <span data-ttu-id="17a22-257">SEMM パッケージファイル、Windows 10 Pro 用のドライバーとファームウェアを含む **Bootme** ドライブを Surface Hub 2 に挿入します。MSI、Windows 10 では、ファイルが USB にインストールされます。 Surface Hub 2S のポート。</span><span class="sxs-lookup"><span data-stu-id="17a22-257">Insert your **BOOTME** drive containing SEMM package files, Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI, and Windows 10 install files into the USB-A port on Surface Hub 2S.</span></span>  

2. <span data-ttu-id="17a22-258">UEFI を起動するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="17a22-258">To boot into UEFI:</span></span>

   1. <span data-ttu-id="17a22-259">Surface Hub 2S の最初の電源オフ (シャットダウン)。</span><span class="sxs-lookup"><span data-stu-id="17a22-259">First power off (shutdown) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="17a22-260">**ボリューム +** を押しながら、**電源**ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="17a22-260">Press and hold **Volume +** and then press and release the **Power** button.</span></span>
   1. <span data-ttu-id="17a22-261">[UEFI] メニューが表示さ **れるまで、[保持]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="17a22-261">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![[UEFI] メニューが表示されるまで、holdling 音量を維持する](images/shm-fig20.png)
      
3. <span data-ttu-id="17a22-263">デバイスが再起動したら、前に作成した UEFI パスワード (該当する場合) を入力します (強くお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="17a22-263">When the device restarts, enter the UEFI password you created earlier, if applicable (strongly recommended).</span></span>

   ![デバイスが再起動したら、UEFI の paassword を入力します。](images/shm-fig22.png)
   
4. <span data-ttu-id="17a22-265">[UEFI] メニューで、[**管理**インストール (USB)] を選択し  >  **Install from USB**ます。</span><span class="sxs-lookup"><span data-stu-id="17a22-265">In the UEFI menu, select **Management** > **Install from USB**.</span></span>

   ![[管理 & [USB からインストール] を選ぶ](images/shm-fig21.png)
   
5. <span data-ttu-id="17a22-267">次に示すように、[ **今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-267">Select **Restart now**, as shown below.</span></span> <span data-ttu-id="17a22-268">デバイスがシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="17a22-268">The device will shut down.</span></span>

   ![[今すぐ再起動] を選択する](images/shm-fig25.png)
   
6. <span data-ttu-id="17a22-270">Power button を押して離すと、Surface Enterprise 管理モードのライセンス認証を求めるメッセージが赤い画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="17a22-270">Press and release the power button, a red screen will display prompting you to activate Surface Enterprise Management Mode.</span></span> 

7. <span data-ttu-id="17a22-271">2文字の **証明書の拇印**と、 **UEFI 設定のパスワード** を入力して、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17a22-271">Enter your two-character **certificate thumbprint**, your **UEFI settings password** and then select **OK**.</span></span>

   ![2文字の証明書の拇印を入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="17a22-273">デバイスで SEMM のライセンス認証を行うと、新しい UEFI 設定 **EnableOSMigration** が適用されます。</span><span class="sxs-lookup"><span data-stu-id="17a22-273">Once you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="17a22-274">Windows 10 チームにはアクセスできなくなり、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17a22-274">You will no longer be able to access Windows 10 Team and must proceed to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span> 

8. <span data-ttu-id="17a22-275">デバイスが再起動し、画面中央に白い4乗が表示されたら、もう一度オフにします。</span><span class="sxs-lookup"><span data-stu-id="17a22-275">The device will reboot, display the white 4-square in the middle of the screen, and then again turn off.</span></span>

### <span data-ttu-id="17a22-276">Windows 10 Pro または Enterprise をインストールする</span><span class="sxs-lookup"><span data-stu-id="17a22-276">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="17a22-277">起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-ポートにまだ入っていない場合は、ここで挿入して、電源ボタンを押してから離します。</span><span class="sxs-lookup"><span data-stu-id="17a22-277">If your bootable Windows 10 Pro or Enterprise drive is not already in the Surface Hub 2 USB-A port, insert it now and then press and release the power button.</span></span>

2. <span data-ttu-id="17a22-278">デバイスが起動し、画面の中央に白い4乗が表示され、白い4乗のロゴの下にスピンした円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17a22-278">The device will start, you will see the white 4-square in the middle of the screen, and then you will see a spinning circle below the white four-square logo.</span></span>

3. <span data-ttu-id="17a22-279">デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切って (電源コードを外してもう一度接続します)、電源ボタンを押してから離し、白の4乗のロゴの下にスピンしている円が表示されるまで、[音量を下げる] ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="17a22-279">If the device does not automatically boot to the USB drive, power off the device (unplug the power cord and plug it back in),  press and release the power button and then press and hold the volume down button until you see the spinning circle below the white four-square logo.</span></span>
 
   ![USB から Windows 10 への起動](images/shm-fig26.png)
   
4. <span data-ttu-id="17a22-281">不在時のエクスペリエンス (OOBE) セットアップが起動したら、指示に従って Windows 10 Pro または Enterprise (バージョン1903以降) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-281">When the out of box experience (OOBE) setup launches, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="17a22-282">Surface Hub 2 ドライバーとファームウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="17a22-282">Install Surface Hub 2 drivers and firmware</span></span>

 - <span data-ttu-id="17a22-283">デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と Enterprise 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="17a22-283">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
### <span data-ttu-id="17a22-284">次のステップ</span><span class="sxs-lookup"><span data-stu-id="17a22-284">Next steps</span></span>

<span data-ttu-id="17a22-285">Surface Hub をパーソナルの生産性デバイスとして完全に構成する方法については、「 [Surface hub 2 で Windows 10 Pro または Enterprise を構成](surface-hub-2-post-install.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17a22-285">To fully configure Surface Hub 2S as a personal productivity device, see [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).</span></span>

> [!NOTE]
><span data-ttu-id="17a22-286">このドキュメントで説明されている手順を実行しても、Surface Hub 2 のデバイスを Windows 10 Pro または Enterprise に移行できなかった場合は、 [Surface hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="17a22-286">If following the steps outlined in this document is unsuccessful in migrating your device to Windows 10 Pro or Enterprise for Surface Hub 2, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

