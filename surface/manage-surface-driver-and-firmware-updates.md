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
ms.openlocfilehash: f41974193d62e4c0cbc1e286976105c20534d906
ms.sourcegitcommit: ed4478dd3c6116a25b1e01a3a0f5ff6c1f940013
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "10897065"
---
# <span data-ttu-id="e7ceb-104">Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-104">Manage and deploy Surface driver and firmware updates</span></span>

<span data-ttu-id="e7ceb-105">Surface ドライバーとファームウェア更新プログラムの管理方法は、環境や組織の要件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-105">How you manage Surface driver and firmware updates varies depending on your environment and organizational requirements.</span></span> <span data-ttu-id="e7ceb-106">Surface デバイスでは、ファームウェアはオペレーティングシステムにドライバーとして公開され、デバイスマネージャーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-106">On Surface devices, firmware is exposed to the operating system as a driver and is visible in Device Manager.</span></span> <span data-ttu-id="e7ceb-107">これにより、デバイスのファームウェアとドライバーは、一般法人向け Windows Update または Windows Update を使用して自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-107">This enables device firmware and drivers to be automatically updated using Windows Update or Windows Update for Business.</span></span> <span data-ttu-id="e7ceb-108">この簡素化されたアプローチは、新興企業や中小企業にとって実現可能な場合もありますが、大規模な組織では通常、更新プログラムを社内で配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-108">Although this simplified approach may be feasible for startups and small or medium-sized businesses, larger organizations typically need IT admins to distribute updates internally.</span></span> <span data-ttu-id="e7ceb-109">これには、ネットワーク全体での最終的な承認および配布前に、包括的な計画、アプリケーションの互換性テスト、および更新プログラムの検証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-109">This may involve comprehensive planning, application compatibility testing, and piloting and validating updates before final approval and distribution across the network.</span></span>

> [!NOTE]
> <span data-ttu-id="e7ceb-110">この記事は、テクニカルサポート担当者と IT プロフェッショナルを対象としています。 Surface デバイスにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-110">This article is intended for technical support agents and IT professionals and applies to Surface devices only.</span></span> <span data-ttu-id="e7ceb-111">Surface の更新プログラムまたはファームウェアをホームデバイスにインストールする方法については、「 [surface ファームウェアと Windows 10 を更新](https://support.microsoft.com/help/4023505)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-111">If you're looking for help to install Surface updates or firmware on a home device, see [Update Surface firmware and Windows 10](https://support.microsoft.com/help/4023505).</span></span>

<span data-ttu-id="e7ceb-112">エンタープライズグレードのソフトウェア配布ソリューションは進化し続けていますが、更新プログラムを一元管理するためのビジネスの根拠は変わりません。 Surface デバイスのセキュリティを維持し、最新のオペレーティングシステムと機能の改善によって更新された状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-112">While enterprise-grade software distribution solutions continue to evolve, the business rationale for centrally managing  updates remains the same: Maintain the security of Surface devices and keep them updated with the latest operating system and feature improvements.</span></span> <span data-ttu-id="e7ceb-113">これは、安定した運用環境を維持し、ユーザーが生産性をブロックされないようにするために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-113">This is essential for sustaining a stable production environment and making sure that users aren't blocked from being productive.</span></span> <span data-ttu-id="e7ceb-114">この記事では、大規模な組織がこれらの目標を達成するための推奨ツールとプロセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-114">This article provides an overview of recommended tools and processes for larger organizations to accomplish these goals.</span></span>

## <span data-ttu-id="e7ceb-115">商用環境での一元的な更新管理</span><span class="sxs-lookup"><span data-stu-id="e7ceb-115">Central update management in commercial environments</span></span>

<span data-ttu-id="e7ceb-116">Microsoft には、ドライバーやファームウェアの更新プログラムなど、デバイスを管理するための合理化されたツールがあります。これは、 [Microsoft Endpoint Manager 管理センター](https://devicemanagement.microsoft.com/)という名前の単一の統合されたエクスペリエンスで、 [devicemanagement.microsoft.com](https://devicemanagement.microsoft.com/#home)からアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-116">Microsoft has streamlined tools for managing devices – including driver and firmware updates -- into a single unified experience that is named [Microsoft Endpoint Manager admin center](https://devicemanagement.microsoft.com/) and is accessed from [devicemanagement.microsoft.com](https://devicemanagement.microsoft.com/#home).</span></span>

### <span data-ttu-id="e7ceb-117">Configuration Manager と Intune を使用して更新プログラムを管理する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-117">Manage updates with Configuration Manager and Intune</span></span>

<span data-ttu-id="e7ceb-118">Microsoft Endpoint Configuration Manager を使用すると、Configuration Manager クライアントを使用して、Surface ファームウェアとドライバー更新プログラムの同期と展開を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-118">Microsoft Endpoint Configuration Manager allows you to synchronize and deploy Surface firmware and driver updates with the Configuration Manager client.</span></span> <span data-ttu-id="e7ceb-119">Microsoft Intune との統合により、管理対象、共同管理、パートナーが管理するすべてのデバイスを1か所で確認できます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-119">Integration with Microsoft Intune lets you see all your managed, co-managed, and partner-managed devices in one place.</span></span> <span data-ttu-id="e7ceb-120">これは、大規模な組織が Surface の更新を管理するために推奨されるソリューションです。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-120">This is the recommended solution for large organizations to manage Surface updates.</span></span>

<span data-ttu-id="e7ceb-121">詳細な手順については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-121">For detailed steps, see the following resources:</span></span>

- [<span data-ttu-id="e7ceb-122">構成マネージャーのドライバーの更新</span><span class="sxs-lookup"><span data-stu-id="e7ceb-122">Manage Surface driver updates in Configuration Manager</span></span>](https://docs.microsoft.com/surface/manage-surface-driver-updates-configuration-manager)
- [<span data-ttu-id="e7ceb-123">Configuration Manager を使用してアプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-123">Deploy applications with Configuration Manager</span></span>](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [<span data-ttu-id="e7ceb-124">エンドポイント構成マネージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="e7ceb-124">Endpoint Configuration Manager documentation</span></span>](https://docs.microsoft.com/configmgr/)

### <span data-ttu-id="e7ceb-125">Microsoft 展開ツールキットを使用して更新プログラムを管理する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-125">Manage updates with Microsoft Deployment Toolkit</span></span>

<span data-ttu-id="e7ceb-126">Microsoft 展開ツールキット (MDT) は、エンドポイント構成マネージャーに含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-126">The Microsoft Deployment Toolkit (MDT) is included in Endpoint Configuration Manager.</span></span> <span data-ttu-id="e7ceb-127">環境によっては、使用する必要があるオプションの展開ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-127">It contains optional deployment tools that you may want to use, depending on your environment.</span></span> <span data-ttu-id="e7ceb-128">これには、windows の評価と展開キット (Windows ADK)、Windows システムイメージマネージャー (Windows SIM)、展開イメージのサービスと管理 (DISM)、ユーザー状態移行ツール (USMT) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-128">These include the Windows Assessment and Deployment Kit (Windows ADK), Windows System Image Manager (Windows SIM), Deployment Image Servicing and Management (DISM), and User State Migration Tool (USMT).</span></span> <span data-ttu-id="e7ceb-129">最新バージョンの MDT は、 [Microsoft 展開ツールキットのダウンロードページ](https://www.microsoft.com/download/details.aspx?id=54259)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-129">You can download the latest version of MDT from the [Microsoft Deployment Toolkit download page](https://www.microsoft.com/download/details.aspx?id=54259).</span></span>

<span data-ttu-id="e7ceb-130">詳細な手順については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-130">For detailed steps, see the following resources:</span></span>

- [<span data-ttu-id="e7ceb-131">Microsoft 展開ツールキットのドキュメント</span><span class="sxs-lookup"><span data-stu-id="e7ceb-131">Microsoft Deployment Toolkit documentation</span></span>](https://docs.microsoft.com/configmgr/mdt/)
- [<span data-ttu-id="e7ceb-132">Microsoft Deployment Toolkit による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="e7ceb-132">Deploy Windows 10 with the Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [<span data-ttu-id="e7ceb-133">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-133">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)

<span data-ttu-id="e7ceb-134">Surface ドライバーとファームウェアの更新プログラムは、Windows Installer (\* .msi) ファイルとしてパッケージ化されています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-134">Surface driver and firmware updates are packaged as Windows Installer (\*.msi) files.</span></span> <span data-ttu-id="e7ceb-135">これらの Windows インストーラーパッケージを展開するには、エンドポイント構成マネージャーまたは MDT を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-135">To deploy these Windows Installer packages, you can use Endpoint Configuration Manager or MDT.</span></span> <span data-ttu-id="e7ceb-136">デバイスとオペレーティングシステムに適切な .msi ファイルを選択する方法については、次のセクションの「.msi ファイルのダウンロードに関するガイドライン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-136">For information about how to select the correct .msi file for a device and operating system, refer to the guidance in the following sections about downloading .msi files.</span></span>

<span data-ttu-id="e7ceb-137">エンドポイント構成マネージャーを使用して更新プログラムを展開する方法については、「 [Configuration manager を](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)使用してアプリケーションを展開する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-137">For instructions about how to deploy updates by using Endpoint Configuration Manager, see [Deploy applications with Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications).</span></span> <span data-ttu-id="e7ceb-138">MDT を使用して更新プログラムを展開する方法については、「 [mdt を使用した Windows 10 イメージの展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-138">For instructions about how to deploy updates by using MDT, see [Deploy a Windows 10 image using MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).</span></span>

**<span data-ttu-id="e7ceb-139">WindowsPE および Surface ファームウェアとドライバー</span><span class="sxs-lookup"><span data-stu-id="e7ceb-139">WindowsPE and Surface firmware and drivers</span></span>**

<span data-ttu-id="e7ceb-140">エンドポイント構成マネージャーと MDT では、展開プロセス中に Windows Preinstallation Environment (WindowsPE) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-140">Endpoint Configuration Manager and MDT both use the Windows Preinstallation Environment (WindowsPE) during the deployment process.</span></span> <span data-ttu-id="e7ceb-141">WindowsPE は、ネットワークアダプターや記憶域コントローラーなどの一部の基本的なドライバーのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-141">WindowsPE supports only a limited set of basic drivers such as those for network adapters and storage controllers.</span></span> <span data-ttu-id="e7ceb-142">WindowsPE の一部ではない Windows コンポーネントのドライバーは、エラーを発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-142">Drivers for Windows components that are not part of WindowsPE might produce errors.</span></span> <span data-ttu-id="e7ceb-143">最善の方法として、このようなエラーを回避するには、WindowsPE フェーズ中に必要なドライバーのみを使用するように展開プロセスを構成します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-143">As a best practice, you can prevent such errors by configuring the deployment process to use only the required drivers during the WindowsPE phase.</span></span>

### <span data-ttu-id="e7ceb-144">Endpoint Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="e7ceb-144">Endpoint Configuration Manager</span></span>

<span data-ttu-id="e7ceb-145">エンドポイント構成マネージャーから開始すると、Configuration Manager クライアントを使用して、Microsoft Surface ファームウェアとドライバーの更新プログラムを同期して展開することができます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-145">Starting in Endpoint Configuration Manager, you can synchronize and deploy Microsoft Surface firmware and driver updates by using the Configuration Manager client.</span></span> <span data-ttu-id="e7ceb-146">詳細については、「KB 4098906、[構成マネージャーで Surface driver の更新プログラムを管理する方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-146">For additional information, see KB 4098906, [How to manage Surface driver updates in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager).</span></span>

## <span data-ttu-id="e7ceb-147">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="e7ceb-147">Supported devices</span></span>

<span data-ttu-id="e7ceb-148">Surface Pro 2 以降のデバイスでは、ダウンロード可能な .msi ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-148">Downloadable .msi files are available for the Surface Pro 2 and later devices.</span></span> <span data-ttu-id="e7ceb-149">Surface Pro 7 や Surface ノートブック3など、最新の Surface デバイスの .msi ファイルに関する情報は、リリース時にこのページから入手できます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-149">Information about .msi files for the newest Surface devices, such as Surface Pro 7 and Surface Laptop 3, will be available from this page upon release.</span></span>

## <span data-ttu-id="e7ceb-150">DFCI でのファームウェアの管理</span><span class="sxs-lookup"><span data-stu-id="e7ceb-150">Managing firmware with DFCI</span></span>

<span data-ttu-id="e7ceb-151">Intune にデバイスファームウェア構成インターフェイス (DFCI) プロファイルを構築することによって ([パブリックプレビュー](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)で利用できるようになりました)、Surface UEFI 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-151">By having Device Firmware Configuration Interface (DFCI) profiles built into Intune (now available in [public preview](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="e7ceb-152">DFCI では、ゼロタッチプロビジョニング、BIOS パスワードの排除、セキュリティ設定の制御 (起動オプションや内蔵の周辺機器を含む)、今後の高度なセキュリティシナリオの基盤を構築しています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-152">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings (including startup options and built-in peripherals), and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="e7ceb-153">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-153">For more information, see the following articles:</span></span>

- [<span data-ttu-id="e7ceb-154">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="e7ceb-154">Intune management of Surface UEFI settings</span></span>](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- <span data-ttu-id="e7ceb-155">[Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-155">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

## <span data-ttu-id="e7ceb-156">更新プログラムの展開プロセスのためのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="e7ceb-156">Best practices for update deployment processes</span></span>

<span data-ttu-id="e7ceb-157">安定した環境を維持するには、最新バージョンの Windows 10 とのパリティを保持することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-157">To maintain a stable environment, we strongly recommend that you maintain parity with the most recent version of Windows 10.</span></span>  <span data-ttu-id="e7ceb-158">ベストプラクティスの推奨事項については、「 [Windows 10 の更新プログラムの展開リングを作成する](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-158">For best practice recommendations, see [Build deployment rings for Windows 10 updates](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates).</span></span>

## <span data-ttu-id="e7ceb-159">ダウンロード可能な Surface 更新パッケージ</span><span class="sxs-lookup"><span data-stu-id="e7ceb-159">Downloadable Surface update packages</span></span>

<span data-ttu-id="e7ceb-160">Windows 10 の特定のバージョンには個別の .msi ファイルがあり、各ファイルには、Surface デバイスのために必要な累積ドライバーとファームウェア更新プログラムがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-160">Specific versions of Windows 10 have separate .msi files, each containing all the required cumulative driver and firmware updates for Surface devices.</span></span> <span data-ttu-id="e7ceb-161">更新プログラムパッケージには、次のコンポーネントの一部またはすべてが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-161">Update packages may include some or all the following components:</span></span>

- <span data-ttu-id="e7ceb-162">Wi-fi および LTE</span><span class="sxs-lookup"><span data-stu-id="e7ceb-162">Wi-Fi and LTE</span></span>
- <span data-ttu-id="e7ceb-163">ビデオ</span><span class="sxs-lookup"><span data-stu-id="e7ceb-163">Video</span></span>
- <span data-ttu-id="e7ceb-164">ソリッドステートドライブ</span><span class="sxs-lookup"><span data-stu-id="e7ceb-164">Solid state drive</span></span>
- <span data-ttu-id="e7ceb-165">システムアグリゲーターモジュール (SAM)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-165">System aggregator module (SAM)</span></span>
- <span data-ttu-id="e7ceb-166">バッテリー</span><span class="sxs-lookup"><span data-stu-id="e7ceb-166">Battery</span></span>
- <span data-ttu-id="e7ceb-167">キーボードコントローラー</span><span class="sxs-lookup"><span data-stu-id="e7ceb-167">Keyboard controller</span></span>
- <span data-ttu-id="e7ceb-168">埋め込みコントローラー (EC)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-168">Embedded controller (EC)</span></span>
- <span data-ttu-id="e7ceb-169">管理エンジン (ME)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-169">Management engine (ME)</span></span>
- <span data-ttu-id="e7ceb-170">統合された拡張ファームウェアインターフェイス (UEFI)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-170">Unified extensible firmware interface (UEFI)</span></span>

### <span data-ttu-id="e7ceb-171">.Msi ファイルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="e7ceb-171">Downloading .msi files</span></span>

1. <span data-ttu-id="e7ceb-172">Microsoft ダウンロードセンターで、 [Surface のドライバーとファームウェアのダウンロード](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-172">Browse to [Download drivers and firmware for Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware) on the Microsoft Download Center.</span></span>
2. <span data-ttu-id="e7ceb-173">Windows のサーフェスモデルとバージョンと一致する .msi ファイル名を選びます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-173">Select the .msi file name that matches the Surface model and version of Windows.</span></span> <span data-ttu-id="e7ceb-174">.Msi ファイル名には、ドライバーとファームウェアをインストールするために必要な最小サポートされる Windows ビルド番号が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-174">The .msi file name includes the minimum supported Windows build number that's required to install the drivers and firmware.</span></span> <span data-ttu-id="e7ceb-175">たとえば、次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-175">For example, refer to the following figure.</span></span> <span data-ttu-id="e7ceb-176">Windows 10 のビルド18362を持つ Surface Book 2 を更新するには、[SurfaceBook2_Win10_18362_19.101.13994.msi] を選び**ます。**</span><span class="sxs-lookup"><span data-stu-id="e7ceb-176">To update a Surface Book 2 that has build 18362 of Windows 10, choose **SurfaceBook2_Win10_18362_19.101.13994.msi.**</span></span> <span data-ttu-id="e7ceb-177">Windows 10 のビルド16299を持つ Surface Book 2 の場合は、[ **SurfaceBook2_Win10_16299_1803509_3.msi**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-177">For a Surface Book 2 that has build 16299 of Windows 10, choose **SurfaceBook2_Win10_16299_1803509_3.msi**.</span></span>

    ![図 1. ](images/fig1-downloads-msi.png)

    *<span data-ttu-id="e7ceb-180">図 1. </span><span class="sxs-lookup"><span data-stu-id="e7ceb-180">Figure 1.</span></span> <span data-ttu-id="e7ceb-181">サーフェスの更新プログラムのダウンロード</span><span class="sxs-lookup"><span data-stu-id="e7ceb-181">Downloading Surface updates</span></span>*

### <span data-ttu-id="e7ceb-182">Surface の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e7ceb-182">Surface .msi naming convention</span></span>

<span data-ttu-id="e7ceb-183">2019年8月の .msi ファイルでは、次の名前付け規則が使用されています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-183">Since August 2019, .msi files are using the following naming convention:</span></span>

- <span data-ttu-id="e7ceb-184">*Product*_*windows release*_*windows ビルド番号*_*バージョン*_*番号 (通常はゼロ) の*バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-184">*Product*_*Windows release*_*Windows build number*_*Version number*_*Revision of version number (typically zero)*.</span></span>

**<span data-ttu-id="e7ceb-185">例</span><span class="sxs-lookup"><span data-stu-id="e7ceb-185">Example</span></span>**

- <span data-ttu-id="e7ceb-186">SurfacePro6_Win10_18362_19.073.44195_0.msi</span><span class="sxs-lookup"><span data-stu-id="e7ceb-186">SurfacePro6_Win10_18362_19.073.44195_0.msi</span></span>

<span data-ttu-id="e7ceb-187">このファイル名には、次の情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-187">This file name provides the following information:</span></span>

- <span data-ttu-id="e7ceb-188">**製品:** SurfacePro6</span><span class="sxs-lookup"><span data-stu-id="e7ceb-188">**Product:** SurfacePro6</span></span>
- <span data-ttu-id="e7ceb-189">**Windows リリース:** Win10</span><span class="sxs-lookup"><span data-stu-id="e7ceb-189">**Windows release:** Win10</span></span>
- <span data-ttu-id="e7ceb-190">**ビルド:** 18362</span><span class="sxs-lookup"><span data-stu-id="e7ceb-190">**Build:** 18362</span></span>
- <span data-ttu-id="e7ceb-191">[**バージョン]:** 19.073.44195 –ファイルが作成された日付と時刻が、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-191">**Version:** 19.073.44195 – This shows the date and time that the file was created, as follows:</span></span>
  - <span data-ttu-id="e7ceb-192">**年:** 19 (2019)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-192">**Year:** 19 (2019)</span></span>
  - <span data-ttu-id="e7ceb-193">**Month and week:** 073 (7 月3日)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-193">**Month and week:** 073 (third week of July)</span></span>
  - <span data-ttu-id="e7ceb-194">**月の分:** 44195</span><span class="sxs-lookup"><span data-stu-id="e7ceb-194">**Minute of the month:** 44195</span></span>
- <span data-ttu-id="e7ceb-195">**バージョンのリビジョン:** 0 (このバージョンの最初のリリース)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-195">**Revision of version:** 0 (first release of this version)</span></span>

### <span data-ttu-id="e7ceb-196">以前の Surface の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e7ceb-196">Legacy Surface .msi naming convention</span></span>

<span data-ttu-id="e7ceb-197">従来の .msi ファイル (2019 年8月より前にビルドされたファイル) は、全体的な名前付けのすべての式に従いますが、別の方法でバージョン番号を派生させます。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-197">Legacy .msi files (files that were built before August 2019) followed the same overall naming formula but used a different method to derive the version number.</span></span>

**<span data-ttu-id="e7ceb-198">例</span><span class="sxs-lookup"><span data-stu-id="e7ceb-198">Example</span></span>**

- <span data-ttu-id="e7ceb-199">SurfacePro6_Win10_16299_1900307_0.msi</span><span class="sxs-lookup"><span data-stu-id="e7ceb-199">SurfacePro6_Win10_16299_1900307_0.msi</span></span>

<span data-ttu-id="e7ceb-200">このファイル名には、次の情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-200">This file name provides the following information:</span></span>

- <span data-ttu-id="e7ceb-201">**製品:** SurfacePro6</span><span class="sxs-lookup"><span data-stu-id="e7ceb-201">**Product:** SurfacePro6</span></span>
- <span data-ttu-id="e7ceb-202">**Windows リリース:** Win10</span><span class="sxs-lookup"><span data-stu-id="e7ceb-202">**Windows release:** Win10</span></span>
- <span data-ttu-id="e7ceb-203">**ビルド:** 16299</span><span class="sxs-lookup"><span data-stu-id="e7ceb-203">**Build:** 16299</span></span>
- <span data-ttu-id="e7ceb-204">**バージョン:** 1900307 –次のように、ファイルが作成された日付と、リリースシーケンスでの位置を示します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-204">**Version:** 1900307 – This shows the date that the file was created and its position in the release sequence, as follows:</span></span>
  - <span data-ttu-id="e7ceb-205">**年:** 19 (2019)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-205">**Year:** 19 (2019)</span></span>
  - <span data-ttu-id="e7ceb-206">**リリース数:** 003 (年の第3リリース)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-206">**Number of release:** 003 (third release of the year)</span></span>
  - <span data-ttu-id="e7ceb-207">**製品バージョン番号:** 07 (surface pro 6 は正式には、surface pro の7番目のバージョンです)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-207">**Product version number:** 07 (Surface Pro 6 is officially the seventh version of Surface Pro)</span></span>
- <span data-ttu-id="e7ceb-208">**バージョンのリビジョン:** 0 (このバージョンの最初のリリース)</span><span class="sxs-lookup"><span data-stu-id="e7ceb-208">**Revision of version:** 0 (first release of this version)</span></span>

## <span data-ttu-id="e7ceb-209">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e7ceb-209">Learn more</span></span>

- [<span data-ttu-id="e7ceb-210">Surface 用のドライバーとファームウェアをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e7ceb-210">Download drivers and firmware for Surface</span></span>](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)
- [<span data-ttu-id="e7ceb-211">Configuration Manager で Surface driver の更新プログラムを管理する方法</span><span class="sxs-lookup"><span data-stu-id="e7ceb-211">How to manage Surface driver updates in Configuration Manager</span></span>](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [<span data-ttu-id="e7ceb-212">Configuration Manager を使用してアプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-212">Deploy applications with Configuration Manager</span></span>](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [<span data-ttu-id="e7ceb-213">エンドポイント構成マネージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="e7ceb-213">Endpoint Configuration Manager documentation</span></span>](https://docs.microsoft.com/configmgr/)
- [<span data-ttu-id="e7ceb-214">Microsoft 展開ツールキットのドキュメント</span><span class="sxs-lookup"><span data-stu-id="e7ceb-214">Microsoft Deployment Toolkit documentation</span></span>](https://docs.microsoft.com/configmgr/mdt/)
- [<span data-ttu-id="e7ceb-215">Microsoft Deployment Toolkit による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="e7ceb-215">Deploy Windows 10 with the Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [<span data-ttu-id="e7ceb-216">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="e7ceb-216">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)  
- [<span data-ttu-id="e7ceb-217">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="e7ceb-217">Intune management of Surface UEFI settings</span></span>](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- <span data-ttu-id="e7ceb-218">[Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。</span><span class="sxs-lookup"><span data-stu-id="e7ceb-218">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>
- [<span data-ttu-id="e7ceb-219">Windows 10 更新プログラムの展開リングの構築</span><span class="sxs-lookup"><span data-stu-id="e7ceb-219">Build deployment rings for Windows 10 updates</span></span>](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)
