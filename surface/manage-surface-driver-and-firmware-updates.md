---
title: Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する
description: この記事では、Surface デバイスのファームウェアとドライバーの更新プログラムを管理および展開するために使用できるオプションについて説明します。
ms.assetid: CD1219BA-8EDE-4BC8-BEEF-99B50C211D73
ms.reviewer: ''
manager: laurawi
keywords: Surface, Surface Pro 3, ファームウェア, 更新プログラム, デバイス, 管理, 展開, ドライバー, USB, Surface, Surface Pro 3, firmware, update, device, manage, deploy, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 91cde5fdf4a7745d491bd2eb928baca75955b90d
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835085"
---
# <span data-ttu-id="701b5-104">Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する</span><span class="sxs-lookup"><span data-stu-id="701b5-104">Manage and deploy Surface driver and firmware updates</span></span>

<span data-ttu-id="701b5-105">Surface ドライバーとファームウェア更新プログラムの管理方法は、環境や組織の要件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="701b5-105">How you manage Surface driver and firmware updates varies depending on your environment and organizational requirements.</span></span> <span data-ttu-id="701b5-106">Surface デバイスでは、ファームウェアはドライバーとしてオペレーティングシステムに公開され、デバイスマネージャーに表示されるため、Windows Update または Windows Update を使用して、デバイスのファームウェアとドライバーを自動的に更新することができます。</span><span class="sxs-lookup"><span data-stu-id="701b5-106">On Surface devices, firmware is exposed to the operating system as a driver and is visible in Device Manager, enabling device firmware and drivers to be automatically updated using Windows Update or Windows Update for Business.</span></span> <span data-ttu-id="701b5-107">この簡素化されたアプローチは、新興企業や中小企業にとって実現可能な場合もありますが、大規模な組織では通常、更新プログラムを社内で配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="701b5-107">Although this simplified approach may be feasible for startups and small or medium-sized businesses, larger organizations typically need IT admins to distribute updates internally.</span></span> <span data-ttu-id="701b5-108">これには、ネットワーク全体での最終的な承認と配布前に、包括的な計画、アプリケーションの互換性テスト、試験的な更新、検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="701b5-108">This may involve comprehensive planning, application compatibility testing, piloting and validating updates, before final approval and distribution across the network.</span></span>

> [!NOTE]
> <span data-ttu-id="701b5-109">この記事は、テクニカルサポート担当者と IT プロフェッショナルを対象としています。 Surface デバイスにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="701b5-109">This article is intended for technical support agents and IT professionals and applies to Surface devices only.</span></span> <span data-ttu-id="701b5-110">Surface の更新プログラムまたはファームウェアをホームデバイスにインストールする方法については、「 [surface ファームウェアと Windows 10 を更新](https://support.microsoft.com/help/4023505)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-110">If you're looking for help to install Surface updates or firmware on a home device, see [Update Surface firmware and Windows 10](https://support.microsoft.com/help/4023505).</span></span>

<span data-ttu-id="701b5-111">エンタープライズグレードのソフトウェア配布ソリューションは進化し続けていますが、更新プログラムを一元管理するためのビジネスの根拠は変わりません。 Surface デバイスのセキュリティを維持し、最新のオペレーティングシステムと機能の改善によって更新された状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="701b5-111">While enterprise-grade software distribution solutions continue to evolve, the business rationale for centrally managing  updates remains the same: Maintain the security of Surface devices and keep them updated with the latest operating system and feature improvements.</span></span> <span data-ttu-id="701b5-112">これは、安定した運用環境を維持し、ユーザーが生産性をブロックされないようにするために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="701b5-112">This is essential for sustaining a stable production environment and ensuring users aren't blocked from being productive.</span></span> <span data-ttu-id="701b5-113">この記事では、大規模な組織がこれらの目標を達成するための推奨ツールとプロセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="701b5-113">This article provides an overview of recommended tools and processes for larger organizations to accomplish these goals.</span></span>

## <span data-ttu-id="701b5-114">商用環境での一元的な更新管理</span><span class="sxs-lookup"><span data-stu-id="701b5-114">Central update management in commercial environments</span></span>

<span data-ttu-id="701b5-115">Microsoft には、ドライバーやファームウェアの更新プログラムなど、デバイスを管理するための合理化されたツールが用意されています。これには、devicemanagement.microsoft.com からアクセスされる[Microsoft Endpoint Manager 管理センター](https://devicemanagement.microsoft.com/)という単一の統合されたエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="701b5-115">Microsoft has streamlined tools for managing devices – including driver and firmware updates -- into a single unified experience called [Microsoft Endpoint Manager admin center](https://devicemanagement.microsoft.com/) accessed from devicemanagement.microsoft.com.</span></span>

### <span data-ttu-id="701b5-116">Configuration Manager と Intune を使用して更新プログラムを管理する</span><span class="sxs-lookup"><span data-stu-id="701b5-116">Manage updates with Configuration Manager and Intune</span></span>

<span data-ttu-id="701b5-117">Microsoft Endpoint Configuration Manager を使用すると、Configuration Manager クライアントを使用して、Surface ファームウェアとドライバー更新プログラムの同期と展開を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="701b5-117">Microsoft Endpoint Configuration Manager allows you to synchronize and deploy Surface firmware and driver updates with the Configuration Manager client.</span></span> <span data-ttu-id="701b5-118">Microsoft Intune との統合により、管理対象、共同管理、パートナーが管理するすべてのデバイスを1か所で確認できます。</span><span class="sxs-lookup"><span data-stu-id="701b5-118">Integration with Microsoft Intune lets you see all your managed, co-managed, and partner-managed devices in one place.</span></span> <span data-ttu-id="701b5-119">これは、大規模な組織が Surface の更新を管理するために推奨されるソリューションです。</span><span class="sxs-lookup"><span data-stu-id="701b5-119">This is the recommended solution for large organizations to manage Surface updates.</span></span>

<span data-ttu-id="701b5-120">詳細な手順については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-120">For detailed steps, see the following resources:</span></span>

- [<span data-ttu-id="701b5-121">Configuration Manager で Surface driver の更新プログラムを管理する方法</span><span class="sxs-lookup"><span data-stu-id="701b5-121">How to manage Surface driver updates in Configuration Manager</span></span>](https://docs.microsoft.com/surface/manage-surface-driver-updates-configuration-manager)
- [<span data-ttu-id="701b5-122">Configuration Manager を使用してアプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="701b5-122">Deploy applications with Configuration Manager</span></span>](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [<span data-ttu-id="701b5-123">エンドポイント構成マネージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="701b5-123">Endpoint Configuration Manager documentation</span></span>](https://docs.microsoft.com/configmgr/)

### <span data-ttu-id="701b5-124">Microsoft 展開ツールキットを使用して更新プログラムを管理する</span><span class="sxs-lookup"><span data-stu-id="701b5-124">Manage updates with Microsoft Deployment Toolkit</span></span>

<span data-ttu-id="701b5-125">エンドポイント構成マネージャーに含まれている Microsoft 展開ツールキット (MDT) には、環境に応じて使用する必要があるオプションの展開ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="701b5-125">Included in Endpoint Configuration Manager, the Microsoft Deployment Toolkit (MDT) contains optional deployment tools that you may wish to use depending on your environment.</span></span> <span data-ttu-id="701b5-126">これには、windows の評価と展開キット (Windows ADK)、Windows システムイメージマネージャー (Windows SIM)、展開イメージのサービスと管理 (DISM)、ユーザー状態移行ツール (USMT) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="701b5-126">These include the Windows Assessment and Deployment Kit (Windows ADK), Windows System Image Manager (Windows SIM), Deployment Image Servicing and Management (DISM), and User State Migration Tool (USMT).</span></span> <span data-ttu-id="701b5-127">最新バージョンの MDT は、 [Microsoft 展開ツールキットのダウンロードページ](https://www.microsoft.com/download/details.aspx?id=54259)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="701b5-127">You can download the latest version of MDT from the [Microsoft Deployment Toolkit download page](https://www.microsoft.com/download/details.aspx?id=54259).</span></span>

<span data-ttu-id="701b5-128">詳細な手順については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-128">For detailed steps, see the following resources:</span></span>

- [<span data-ttu-id="701b5-129">Microsoft 展開ツールキットのドキュメント</span><span class="sxs-lookup"><span data-stu-id="701b5-129">Microsoft Deployment Toolkit documentation</span></span>](https://docs.microsoft.com/configmgr/mdt/)
- [<span data-ttu-id="701b5-130">Microsoft Deployment Toolkit による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="701b5-130">Deploy Windows 10 with the Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [<span data-ttu-id="701b5-131">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="701b5-131">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)

<span data-ttu-id="701b5-132">Surface ドライバーとファームウェアの更新プログラムは、Windows Installer (\* .msi) ファイルとしてパッケージ化されています。</span><span class="sxs-lookup"><span data-stu-id="701b5-132">Surface driver and firmware updates are packaged as Windows Installer (\*.msi) files.</span></span> <span data-ttu-id="701b5-133">これらの Windows インストーラーパッケージを展開するには、エンドポイント構成マネージャーまたは MDT を使用できます。</span><span class="sxs-lookup"><span data-stu-id="701b5-133">To deploy these Windows Installer packages, you can use Endpoint Configuration Manager or MDT.</span></span> <span data-ttu-id="701b5-134">デバイスとオペレーティングシステムに適切な .msi ファイルを選択する方法については、次のガイダンスを参照してください。 .msi ファイルのダウンロードについての説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-134">For information about selecting the correct .msi file for a device and operating system, refer to the guidance below about downloading .msi files.</span></span>

<span data-ttu-id="701b5-135">エンドポイント構成マネージャーを使用して更新プログラムを展開する方法については、「 [Configuration manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)を使用してアプリケーションを展開する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-135">For instructions on how to deploy updates by using Endpoint Configuration Manager refer to [Deploy applications with Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications).</span></span> <span data-ttu-id="701b5-136">MDT を使用して更新プログラムを展開する方法については、「 [mdt を使用した Windows 10 イメージの展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-136">For instructions on how to deploy updates by using MDT, see [Deploy a Windows 10 image using MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).</span></span>

**<span data-ttu-id="701b5-137">WindowsPE および Surface ファームウェアとドライバー</span><span class="sxs-lookup"><span data-stu-id="701b5-137">WindowsPE and Surface firmware and drivers</span></span>**

<span data-ttu-id="701b5-138">エンドポイント構成マネージャーと MDT では、展開プロセス中に Windows Preinstallation Environment (WindowsPE) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="701b5-138">Endpoint Configuration Manager and MDT both use the Windows Preinstallation Environment (WindowsPE) during the deployment process.</span></span> <span data-ttu-id="701b5-139">WindowsPE は、ネットワークアダプターや記憶域コントローラーなどの一部の基本的なドライバーのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="701b5-139">WindowsPE only supports a limited set of basic drivers such as those for network adapters and storage controllers.</span></span> <span data-ttu-id="701b5-140">WindowsPE の一部ではない Windows コンポーネントのドライバーは、エラーを発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="701b5-140">Drivers for Windows components that are not part of WindowsPE might produce errors.</span></span> <span data-ttu-id="701b5-141">最善の方法として、このようなエラーを回避するには、WindowsPE フェーズ中に必要なドライバーのみを使用するように展開プロセスを構成します。</span><span class="sxs-lookup"><span data-stu-id="701b5-141">As a best practice, you can prevent such errors by configuring the deployment process to use only the required drivers during the WindowsPE phase.</span></span>

### <span data-ttu-id="701b5-142">Endpoint Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="701b5-142">Endpoint Configuration Manager</span></span>

<span data-ttu-id="701b5-143">エンドポイント構成マネージャーから開始すると、Configuration Manager クライアントを使用して、Microsoft Surface ファームウェアとドライバーの更新プログラムを同期して展開することができます。</span><span class="sxs-lookup"><span data-stu-id="701b5-143">Starting in Endpoint Configuration Manager, you can synchronize and deploy Microsoft Surface firmware and driver updates by using the Configuration Manager client.</span></span> <span data-ttu-id="701b5-144">詳細については、「KB 4098906、[構成マネージャーで Surface driver の更新プログラムを管理する方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-144">For additional information, see KB 4098906, [How to manage Surface driver updates in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager).</span></span>

## <span data-ttu-id="701b5-145">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="701b5-145">Supported devices</span></span>

<span data-ttu-id="701b5-146">Surface Pro 2 以降では、ダウンロード可能な .msi ファイルを Surface デバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="701b5-146">Downloadable .msi files are available for Surface devices from Surface Pro 2 and later.</span></span> <span data-ttu-id="701b5-147">Surface Pro 7、Surface Pro X、Surface Pc 3 などの最新の Surface デバイスの .msi ファイルに関する情報は、リリース時にこのページから入手できます。</span><span class="sxs-lookup"><span data-stu-id="701b5-147">Information about .msi files for the newest Surface devices such as Surface Pro 7, Surface Pro X, and Surface Laptop 3 will be available from this page upon release.</span></span>

## <span data-ttu-id="701b5-148">DFCI でのファームウェアの管理</span><span class="sxs-lookup"><span data-stu-id="701b5-148">Managing firmware with DFCI</span></span>

<span data-ttu-id="701b5-149">Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると ([パブリックプレビュー](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)で利用できるようになりました)、Surface uefi 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="701b5-149">With Device Firmware Configuration Interface (DFCI) profiles built into Intune (now available in [public preview](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="701b5-150">DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。</span><span class="sxs-lookup"><span data-stu-id="701b5-150">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="701b5-151">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-151">For more information, see:</span></span>

- [<span data-ttu-id="701b5-152">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="701b5-152">Intune management of Surface UEFI settings</span></span>](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- <span data-ttu-id="701b5-153">[Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。</span><span class="sxs-lookup"><span data-stu-id="701b5-153">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

## <span data-ttu-id="701b5-154">更新プログラムの展開プロセスのためのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="701b5-154">Best practices for update deployment processes</span></span>

<span data-ttu-id="701b5-155">安定した環境を維持するには、最新バージョンの Windows 10 でパリティを維持することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="701b5-155">To maintain a stable environment, it's strongly recommended to maintain parity with the most recent version of Windows 10.</span></span>  <span data-ttu-id="701b5-156">ベストプラクティスの推奨事項については、「 [Windows 10 の更新プログラムの展開リングを作成する](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-156">For best practice recommendations, see [Build deployment rings for Windows 10 updates](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates).</span></span>

## <span data-ttu-id="701b5-157">ダウンロード可能な Surface 更新パッケージ</span><span class="sxs-lookup"><span data-stu-id="701b5-157">Downloadable Surface update packages</span></span>

<span data-ttu-id="701b5-158">Windows 10 の特定のバージョンには個別の .msi ファイルがあり、各ファイルには、Surface デバイスのために必要な累積ドライバーとファームウェア更新プログラムがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="701b5-158">Specific versions of Windows 10 have separate .msi files, each containing all required cumulative driver and firmware updates for Surface devices.</span></span> <span data-ttu-id="701b5-159">更新プログラムパッケージには、次のコンポーネントの一部またはすべてが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="701b5-159">Update packages may include some or all of the following components:</span></span>

- <span data-ttu-id="701b5-160">Wi-fi および LTE</span><span class="sxs-lookup"><span data-stu-id="701b5-160">Wi-Fi and LTE</span></span>
- <span data-ttu-id="701b5-161">ビデオ</span><span class="sxs-lookup"><span data-stu-id="701b5-161">Video</span></span>
- <span data-ttu-id="701b5-162">ソリッドステートドライブ</span><span class="sxs-lookup"><span data-stu-id="701b5-162">Solid state drive</span></span>
- <span data-ttu-id="701b5-163">システムアグリゲーターモジュール (SAM)</span><span class="sxs-lookup"><span data-stu-id="701b5-163">System aggregator module (SAM)</span></span>
- <span data-ttu-id="701b5-164">バッテリー</span><span class="sxs-lookup"><span data-stu-id="701b5-164">Battery</span></span>
- <span data-ttu-id="701b5-165">キーボードコントローラー</span><span class="sxs-lookup"><span data-stu-id="701b5-165">Keyboard controller</span></span>
- <span data-ttu-id="701b5-166">埋め込みコントローラー (EC)</span><span class="sxs-lookup"><span data-stu-id="701b5-166">Embedded controller (EC)</span></span>
- <span data-ttu-id="701b5-167">管理エンジン (ME)</span><span class="sxs-lookup"><span data-stu-id="701b5-167">Management engine (ME)</span></span>
- <span data-ttu-id="701b5-168">統合された拡張ファームウェアインターフェイス (UEFI)</span><span class="sxs-lookup"><span data-stu-id="701b5-168">Unified extensible firmware interface (UEFI)</span></span>

### <span data-ttu-id="701b5-169">.Msi ファイルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="701b5-169">Downloading .msi files</span></span>

1. <span data-ttu-id="701b5-170">Microsoft ダウンロードセンターで、 [Surface のドライバーとファームウェアのダウンロード](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701b5-170">Browse to [Download drivers and firmware for Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware) on the Microsoft Download Center.</span></span>
2. <span data-ttu-id="701b5-171">Windows のサーフェスモデルとバージョンと一致する .msi ファイル名を選びます。</span><span class="sxs-lookup"><span data-stu-id="701b5-171">Select the .msi file name that matches the Surface model and version of Windows.</span></span> <span data-ttu-id="701b5-172">.Msi ファイル名には、ドライバーとファームウェアをインストールするためにサポートされている最小の Windows ビルド番号が含まれています。</span><span class="sxs-lookup"><span data-stu-id="701b5-172">The .msi file name includes the minimum supported Windows build number required to install the drivers and firmware.</span></span> <span data-ttu-id="701b5-173">たとえば、次の図に示すように、Windows 10 のビルド18362で Surface Book 2 を更新するには、[SurfaceBook2_Win10_18362_19.101.13994.msi] を選び**ます。**</span><span class="sxs-lookup"><span data-stu-id="701b5-173">For example, as shown in the following figure, to update a Surface Book 2 with build 18362 of Windows 10, choose **SurfaceBook2_Win10_18362_19.101.13994.msi.**</span></span> <span data-ttu-id="701b5-174">Windows 10 のビルド16299で Surface Book 2 を使用している場合は、[ **SurfaceBook2_Win10_16299_1803509_3.msi**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="701b5-174">For a Surface Book 2 with build 16299 of Windows 10, choose **SurfaceBook2_Win10_16299_1803509_3.msi**.</span></span>

    ![図 1. ](images/fig1-downloads-msi.png)

    *<span data-ttu-id="701b5-177">図 1. </span><span class="sxs-lookup"><span data-stu-id="701b5-177">Figure 1.</span></span> <span data-ttu-id="701b5-178">サーフェスの更新プログラムのダウンロード</span><span class="sxs-lookup"><span data-stu-id="701b5-178">Downloading Surface updates</span></span>*

### <span data-ttu-id="701b5-179">Surface の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="701b5-179">Surface .msi naming convention</span></span>

<span data-ttu-id="701b5-180">2019年8月の .msi ファイルでは、次の名前付け規則が使われています。</span><span class="sxs-lookup"><span data-stu-id="701b5-180">Since August 2019, .msi files have used the following naming convention:</span></span>

- <span data-ttu-id="701b5-181">*Product*_*windows release*_*windows ビルド番号*_*バージョン*_*番号 (通常はゼロ) の*バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="701b5-181">*Product*_*Windows release*_*Windows build number*_*Version number*_*Revision of version number (typically zero)*.</span></span>

**<span data-ttu-id="701b5-182">例</span><span class="sxs-lookup"><span data-stu-id="701b5-182">Example</span></span>**

- <span data-ttu-id="701b5-183">SurfacePro6_Win10_18362_19.073.44195_0.msi</span><span class="sxs-lookup"><span data-stu-id="701b5-183">SurfacePro6_Win10_18362_19.073.44195_0.msi</span></span>

<span data-ttu-id="701b5-184">このファイル名には、次の情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="701b5-184">This file name provides the following information:</span></span>

- <span data-ttu-id="701b5-185">**製品:** SurfacePro6</span><span class="sxs-lookup"><span data-stu-id="701b5-185">**Product:** SurfacePro6</span></span>
- <span data-ttu-id="701b5-186">**Windows リリース:** Win10</span><span class="sxs-lookup"><span data-stu-id="701b5-186">**Windows release:** Win10</span></span>
- <span data-ttu-id="701b5-187">**ビルド:** 18362</span><span class="sxs-lookup"><span data-stu-id="701b5-187">**Build:** 18362</span></span>
- <span data-ttu-id="701b5-188">[**バージョン]:** 19.073.44195 –ファイルが作成された日付と時刻が、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="701b5-188">**Version:** 19.073.44195 – This shows the date and time that the file was created, as follows:</span></span>
  - <span data-ttu-id="701b5-189">**年:** 19 (2019)</span><span class="sxs-lookup"><span data-stu-id="701b5-189">**Year:** 19 (2019)</span></span>
  - <span data-ttu-id="701b5-190">**Month and week:** 073 (7 月3日)</span><span class="sxs-lookup"><span data-stu-id="701b5-190">**Month and week:** 073 (third week of July)</span></span>
  - <span data-ttu-id="701b5-191">**月の分:** 44195</span><span class="sxs-lookup"><span data-stu-id="701b5-191">**Minute of the month:** 44195</span></span>
- <span data-ttu-id="701b5-192">**バージョンのリビジョン:** 0 (このバージョンの最初のリリース)</span><span class="sxs-lookup"><span data-stu-id="701b5-192">**Revision of version:** 0 (first release of this version)</span></span>

### <span data-ttu-id="701b5-193">以前の Surface の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="701b5-193">Legacy Surface .msi naming convention</span></span>

<span data-ttu-id="701b5-194">従来の .msi ファイル (2019 年8月より前にビルドされたファイル) には、全体的な名前付けの数式と同じものがありましたが、別の方法でバージョン番号を派生させています。</span><span class="sxs-lookup"><span data-stu-id="701b5-194">Legacy .msi files (files built before August 2019) followed the same overall naming formula but used a different method to derive the version number.</span></span>

**<span data-ttu-id="701b5-195">例</span><span class="sxs-lookup"><span data-stu-id="701b5-195">Example</span></span>**

- <span data-ttu-id="701b5-196">SurfacePro6_Win10_16299_1900307_0.msi</span><span class="sxs-lookup"><span data-stu-id="701b5-196">SurfacePro6_Win10_16299_1900307_0.msi</span></span>

<span data-ttu-id="701b5-197">このファイル名には、次の情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="701b5-197">This file name provides the following information:</span></span>

- <span data-ttu-id="701b5-198">**製品:** SurfacePro6</span><span class="sxs-lookup"><span data-stu-id="701b5-198">**Product:** SurfacePro6</span></span>
- <span data-ttu-id="701b5-199">**Windows リリース:** Win10</span><span class="sxs-lookup"><span data-stu-id="701b5-199">**Windows release:** Win10</span></span>
- <span data-ttu-id="701b5-200">**ビルド:** 16299</span><span class="sxs-lookup"><span data-stu-id="701b5-200">**Build:** 16299</span></span>
- <span data-ttu-id="701b5-201">**バージョン:** 1900307 –次のように、ファイルが作成された日付と、リリースシーケンスでの位置を示します。</span><span class="sxs-lookup"><span data-stu-id="701b5-201">**Version:** 1900307 – This shows the date that the file was created and its position in the release sequence, as follows:</span></span>
  - <span data-ttu-id="701b5-202">**年:** 19 (2019)</span><span class="sxs-lookup"><span data-stu-id="701b5-202">**Year:** 19 (2019)</span></span>
  - <span data-ttu-id="701b5-203">**リリース数:** 003 (年の第3リリース)</span><span class="sxs-lookup"><span data-stu-id="701b5-203">**Number of release:** 003 (third release of the year)</span></span>
  - <span data-ttu-id="701b5-204">**製品バージョン番号:** 07 (surface pro 6 は正式には、surface pro の7番目のバージョンです)</span><span class="sxs-lookup"><span data-stu-id="701b5-204">**Product version number:** 07 (Surface Pro 6 is officially the seventh version of Surface Pro)</span></span>
- <span data-ttu-id="701b5-205">**バージョンのリビジョン:** 0 (このバージョンの最初のリリース)</span><span class="sxs-lookup"><span data-stu-id="701b5-205">**Revision of version:** 0 (first release of this version)</span></span>

## <span data-ttu-id="701b5-206">詳細情報</span><span class="sxs-lookup"><span data-stu-id="701b5-206">Learn more</span></span>

- [<span data-ttu-id="701b5-207">Surface 用のドライバーとファームウェアをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="701b5-207">Download drivers and firmware for Surface</span></span>](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)
- [<span data-ttu-id="701b5-208">Configuration Manager で Surface driver の更新プログラムを管理する方法</span><span class="sxs-lookup"><span data-stu-id="701b5-208">How to manage Surface driver updates in Configuration Manager</span></span>](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [<span data-ttu-id="701b5-209">Configuration Manager を使用してアプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="701b5-209">Deploy applications with Configuration Manager</span></span>](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [<span data-ttu-id="701b5-210">エンドポイント構成マネージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="701b5-210">Endpoint Configuration Manager documentation</span></span>](https://docs.microsoft.com/configmgr/)
- [<span data-ttu-id="701b5-211">Microsoft 展開ツールキットのドキュメント</span><span class="sxs-lookup"><span data-stu-id="701b5-211">Microsoft Deployment Toolkit documentation</span></span>](https://docs.microsoft.com/configmgr/mdt/)
- [<span data-ttu-id="701b5-212">Microsoft Deployment Toolkit による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="701b5-212">Deploy Windows 10 with the Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [<span data-ttu-id="701b5-213">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="701b5-213">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)  
- [<span data-ttu-id="701b5-214">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="701b5-214">Intune management of Surface UEFI settings</span></span>](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- <span data-ttu-id="701b5-215">[Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。</span><span class="sxs-lookup"><span data-stu-id="701b5-215">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>
- [<span data-ttu-id="701b5-216">Windows 10 更新プログラムの展開リングの構築</span><span class="sxs-lookup"><span data-stu-id="701b5-216">Build deployment rings for Windows 10 updates</span></span>](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)
