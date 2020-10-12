---
title: Surface Pro X の展開、管理、メンテナンス
description: この記事では、Surface Pro X の展開、管理、およびメンテナンスに関する重要な考慮事項の概要を示します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: high
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/09/2020
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 202818488f19c82ba9d08cfcbfcd091e3e8b7bf6
ms.sourcegitcommit: 7d5b0a7948eb540d6849a0e2c70a1058584cc5f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "11105842"
---
# <span data-ttu-id="80aa1-103">Surface Pro X の展開、管理、メンテナンス</span><span class="sxs-lookup"><span data-stu-id="80aa1-103">Deploying, managing, and servicing Surface Pro X</span></span>

## <span data-ttu-id="80aa1-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="80aa1-104">Introduction</span></span>

<span data-ttu-id="80aa1-105">Surface Pro X は、クラスで最も強力なプロセッサである Microsoft SQ1 および Microsoft SQ1 ARM チップセットを組み込むことにより新境地を開拓し、商用環境での高パフォーマンス要件を処理できるように構築されています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-105">Built to handle high performance commercial requirements, Surface Pro X breaks new ground by incorporating the most powerful processors in its class, the Microsoft SQ1 and Microsoft SQ1 ARM chipsets.</span></span>

<span data-ttu-id="80aa1-106">Surface Pro X では 3GHz CPU と 2.1 テラフロップ GPU を搭載し、完全な Windows エクスペリエンスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-106">Powered by a 3GHz CPU and a 2.1 teraflop GPU, Surface Pro X provides a full Windows experience.</span></span> <span data-ttu-id="80aa1-107">15 時間のバッテリー寿命を内蔵した Gigabit LTE と、タッチ、ペン、タブレット、ラップトップの多様性により、金融、法務、医療の分野のモバイル ファーストライン ワーカーおよびプロフェッショナルをはじめ、長いバッテリ寿命と継続的な接続性を必要とするあらゆる業務のユーザーに最適に機能します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-107">Its 15-hour battery life built-in Gigabit LTE and the versatility of touch, pen, tablet, and laptop make it ideally suited for mobile first-line workers and professionals across the financial, legal, and medical fields or any role demanding extended battery life and continuous connectivity capabilities.</span></span>

<span data-ttu-id="80aa1-108">Surface Pro X は、最新のクラウドベース環境専用に設計されており、Microsoft 365、Intune、および Windows Autopilot と組み合わせると最適に機能します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-108">Surface Pro X is designed almost exclusively for a modern, cloud-based environment and works best when paired with Microsoft 365, Intune and Windows Autopilot.</span></span> <span data-ttu-id="80aa1-109">この記事では、Surface Pro X の概要を示し、展開、管理、およびメンテナンスに関する主な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-109">This article highlights what that looks like and outlines key considerations for deploying, managing, and servicing Surface Pro X.</span></span>

## <span data-ttu-id="80aa1-110">Surface Pro X の展開</span><span class="sxs-lookup"><span data-stu-id="80aa1-110">Deploying Surface Pro X</span></span>

<span data-ttu-id="80aa1-111">最適なエクスペリエンスを得るには、Windows Autopilot で Surface Pro X を展開します。このとき、補助ツールとして Microsoft クラウド ソリューション プロバイダーを使用するか、Autopilot 展開プロファイルおよび関連機能によるセルフプロビジョニングを行います。</span><span class="sxs-lookup"><span data-stu-id="80aa1-111">For the best experience, deploy Surface Pro X using Windows Autopilot either with the assistance of a Microsoft Cloud Solution Provider or self-provisioned using Autopilot deployment profiles and related features.</span></span> <span data-ttu-id="80aa1-112">詳しくは、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-112">For more information, refer to:</span></span>

- [<span data-ttu-id="80aa1-113">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="80aa1-113">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md)
- [<span data-ttu-id="80aa1-114">Windows Autopilot の概要</span><span class="sxs-lookup"><span data-stu-id="80aa1-114">Overview of Windows Autopilot</span></span>](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)

<span data-ttu-id="80aa1-115">Autopilot による展開には、いくつかの利点があります。ゼロタッチ展開用に合理化された、工場でプロビジョニング済みのオペレーティング システムを使用して、Office Pro Plus のプレインストールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-115">Autopilot deployment has several advantages: It allows you to use the factory provisioned operating system, streamlined for zero-touch deployment, to include pre-installation of Office Pro Plus.</span></span>

<span data-ttu-id="80aa1-116">既に最新の管理、セキュリティ、および生産性ソリューションを使用している組織は、Surface Pro X 独自のパフォーマンス機能を活用できます。最新のビジネス アプリ、Microsoft Store (UWP) アプリ、またはリモート デスクトップ ソリューションを使用しているお客様も有利です。</span><span class="sxs-lookup"><span data-stu-id="80aa1-116">Organizations already using modern management, security, and productivity solutions are well positioned to take advantage of the unique performance features in Surface Pro X. Customers using modernized line of business apps, Microsoft store (UWP) apps, or remote desktop solutions also stand to benefit.</span></span>

## <span data-ttu-id="80aa1-117">イメージ ベースの展開に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="80aa1-117">Image-based deployment considerations</span></span>

<span data-ttu-id="80aa1-118">現在、Microsoft Deployment Toolkit (MDT) および Microsoft Endpoint Configuration Manager (旧称 System Center Configuration Manager) では、Surface Pro X でのオペレーティング システムの展開がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-118">Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager (formerly System Center Configuration Manager) currently do not support Surface Pro X for operating system deployment.</span></span> <span data-ttu-id="80aa1-119">イメージ ベースの展開をご利用のお客様は、最新の展開ソリューションに移行する適切な時期を引き続き評価しつつ、Surface Pro 7 の使用をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-119">Customers relying on image-based deployment should consider Surface Pro 7 while they continue to evaluate the right time to transition to modern deployment solutions.</span></span> 

## <span data-ttu-id="80aa1-120">Surface Pro X デバイスの管理</span><span class="sxs-lookup"><span data-stu-id="80aa1-120">Managing Surface Pro X devices</span></span>

### <span data-ttu-id="80aa1-121">Intune</span><span class="sxs-lookup"><span data-stu-id="80aa1-121">Intune</span></span>

<span data-ttu-id="80aa1-122">Intune は、Microsoft Enterprise Mobility + Security のコンポーネントです。これを Azure Active Directory と統合することで、ID およびアクセスの制御を行い、登録済みの Surface Pro X デバイスをきめ細かく管理できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-122">A component of Microsoft Enterprise Mobility + Security, Intune integrates with Azure Active Directory for identity and access control and provides granular management of enrolled Surface Pro X devices.</span></span> <span data-ttu-id="80aa1-123">Intune モバイル デバイス管理 (MDM) ポリシーには、Windows グループ ポリシーなどの従来のオンプレミス ツールと比較して、多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-123">Intune mobile device management (MDM) policies have a number of advantages over older on-premises tools such as Windows Group Policy.</span></span> <span data-ttu-id="80aa1-124">これには、デバイスのログイン時間の短縮や、合理的なポリシー カタログによる、クラウドからの総合的なデバイス管理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-124">This includes faster device login times and a more streamlined catalog of policies enabling full device management from the cloud.</span></span> <span data-ttu-id="80aa1-125">たとえば、eSIM プロファイルを使用して LTE を管理し、データ通信プランを設定して、アクティブ化コードを複数のデバイスに展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-125">For example, you can manage LTE using eSIM profiles to configure data plans and deploy activation codes to multiple devices.</span></span><br> 

<span data-ttu-id="80aa1-126">Intune の使用方法の詳細については、[Intune ドキュメント](https://docs.microsoft.com/intune/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-126">For more information about using Intune, refer to the [Intune documentation](https://docs.microsoft.com/intune/).</span></span>

### <span data-ttu-id="80aa1-127">共同管理</span><span class="sxs-lookup"><span data-stu-id="80aa1-127">Co-management</span></span>

<span data-ttu-id="80aa1-128">Autopilot で展開すると、Surface Pro X デバイスを Azure ADまたはActive Directory (Hybrid Azure AD Join) に参加させて、Intune でデバイスを管理することも、Endpoint Configuration Manager でデバイスを共同管理することもできます (32 ビットの x86 ConfigMgr クライアントがインストールされます)。</span><span class="sxs-lookup"><span data-stu-id="80aa1-128">Once deployed in Autopilot, you can join Surface Pro X devices to Azure AD or Active Directory (Hybrid Azure AD Join) where you will be able to manage the devices with Intune or co-manage them with Endpoint Configuration Manager, which will install the 32-bit x86 ConfigMgr client.</span></span>

### <span data-ttu-id="80aa1-129">サード パーティの MDM ソリューション</span><span class="sxs-lookup"><span data-stu-id="80aa1-129">Third party MDM solutions</span></span>

<span data-ttu-id="80aa1-130">Surface Pro X デバイスの管理に、サード パーティ製 MDM ツールを使用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-130">You may be able to use third-party MDM tools to manage Surface Pro X devices.</span></span> <span data-ttu-id="80aa1-131">詳しくは、MDM プロバイダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-131">For details, contact your MDM provider.</span></span>

### <span data-ttu-id="80aa1-132">ウイルス対策ソフトウェア</span><span class="sxs-lookup"><span data-stu-id="80aa1-132">Antivirus software</span></span>

<span data-ttu-id="80aa1-133">Windows Defender は、Windows 10 デバイスの有効なサポート期間中、ARM ベースの PC での Windows 10 の保護に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-133">Windows Defender will help protect Windows 10 on ARM-based PCs for the supported lifetime of the Windows 10 device.</span></span> 

<span data-ttu-id="80aa1-134">サード パーティ製ウイルス対策ソフトウェアには、ARM ベースのプロセッサで動作する Windows 10 PC にインストールできないものもあります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-134">Some third-party antivirus software cannot be installed on a Windows 10 PC running on an ARM-based processor.</span></span> <span data-ttu-id="80aa1-135">サードパーティ製のウイルス対策ソフトウェア プロバイダーとのコラボレーションは、ARM ベースの PC での AV アプリの準備用に継続されています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-135">Collaboration with third-party antivirus software providers is continuing for AV app readiness on ARM-based PCs.</span></span> <span data-ttu-id="80aa1-136">アプリが利用可能になる時期については、各ウイルス対策ソフトウェア プロバイダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-136">Contact your antivirus software provider to understand when their apps will be available.</span></span>

## <span data-ttu-id="80aa1-137">Surface Pro X のメンテナンス</span><span class="sxs-lookup"><span data-stu-id="80aa1-137">Servicing Surface Pro X</span></span>

<span data-ttu-id="80aa1-138">Surface Pro X は Windows 10 バージョン 2004 に付属しており、Windows 10 バージョン 1903 以降をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-138">Surface Pro X ships with Windows 10 version 2004 and supports Windows 10, version 1903 and later.</span></span> <span data-ttu-id="80aa1-139">ARM ベースのデバイスとして、最新のドライバーとファームウェアを維持するための特定の要件があります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-139">As an ARM-based device, it has specific requirements for maintaining the latest drivers and firmware.</span></span> 

<span data-ttu-id="80aa1-140">Surface Pro X は、ホーム ユーザーと小規模ビジネス ユーザーの両方を対象とし、ドライバーとファームウェアを最新の状態に保つプロセスを Windows Update で簡略化できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-140">Surface Pro X was designed to use Windows Update to simplify the process of keeping drivers and firmware up to date for both home users and small business users.</span></span> <span data-ttu-id="80aa1-141">自動で更新プログラムを受け取るには、既定の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-141">Use the default settings to receive Automatic updates.</span></span>  <span data-ttu-id="80aa1-142">設定を確認するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-142">To verify:</span></span>

1. <span data-ttu-id="80aa1-143">**[スタート]** > **[設定] > [更新とセキュリティ] > [Windows Update]** > **[詳細オプション]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-143">Go to **Start** > **Settings > Update & Security > Windows Update** > **Advanced Options.**</span></span>
2. <span data-ttu-id="80aa1-144">**[更新プログラムのインストール方法を選んでください]** で、**[自動 (推奨)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-144">Under **Choose how updates are installed,** select **Automatic (recommended)**.</span></span>

### <span data-ttu-id="80aa1-145">商用利用のお客様向けの推奨事項</span><span class="sxs-lookup"><span data-stu-id="80aa1-145">Recommendations for commercial customers</span></span>

- <span data-ttu-id="80aa1-146">最新のドライバとファームウェアを維持するには、Windows Update または Windows Update for Business を使用します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-146">Use Windows Update or Windows Update for Business for maintaining the latest drivers and firmware.</span></span> <span data-ttu-id="80aa1-147">詳しくは、「[Windows Update for Business を使った更新プログラムの展開](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-147">For more information, see [Deploy Updates using Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).</span></span>
- <span data-ttu-id="80aa1-148">Surface デバイスでの更新プログラムの展開と管理の詳細については、「[Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する](manage-surface-driver-and-firmware-updates.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-148">For more information about deploying and managing updates on Surface devices, see [Manage and deploy Surface driver and firmware updates](manage-surface-driver-and-firmware-updates.md).</span></span>
- <span data-ttu-id="80aa1-149">Windows Server Update Services (WSUS) では、ドライバーとファームウェアを Surface Pro X に提供する機能がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-149">Note that Windows Server Update Services (WSUS) does not support the ability to deliver drivers and firmware to Surface Pro X.</span></span>

## <span data-ttu-id="80aa1-150">Surface Pro X でのアプリの実行</span><span class="sxs-lookup"><span data-stu-id="80aa1-150">Running apps on Surface Pro X</span></span>

<span data-ttu-id="80aa1-151">一部の例外を除き、ARM ベースの Windows 10 PC では、ほとんどのアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-151">Most apps run on ARM-based Windows 10 PCs with limited exclusions.</span></span>

### <span data-ttu-id="80aa1-152">サポートされているアプリ</span><span class="sxs-lookup"><span data-stu-id="80aa1-152">Supported apps</span></span>

- <span data-ttu-id="80aa1-153">Surface Pro X では、ほとんどの x86 Win32 アプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-153">Most x86 Win32 apps run on Surface Pro X.</span></span>
- <span data-ttu-id="80aa1-154">ネイティブの ARM64 アプリと Microsoft Store UWP アプリは、バッテリの寿命を最適化しながら、ARM ベースのプロセッサのネイティブ速度をフル活用して、優れたユーザー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-154">Native ARM64 and Microsoft Store UWP apps provide an excellent user experience utilizing the full native speed of the ARM-based processor while optimizing battery life.</span></span>
- <span data-ttu-id="80aa1-155">ARM ベースのプロセッサで動作する Windows 10 PC 用に設計されたドライバーを使用するアプリ。</span><span class="sxs-lookup"><span data-stu-id="80aa1-155">Apps that use drivers designed for a Windows 10 PC running on an ARM-based processor.</span></span>

> [!NOTE]
> <span data-ttu-id="80aa1-156">64 ビット エミュレーションが Windows Insider プログラムを介してプレビューで間もなく登場するため、Surface Pro X で 64 ビット (x64) アプリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-156">With 64-bit emulation coming soon in Preview via the Windows Insider program, you'll be able to run 64-bit (x64) apps on Surface Pro X.</span></span>

### <span data-ttu-id="80aa1-157">FastTrack App Assure</span><span class="sxs-lookup"><span data-stu-id="80aa1-157">FastTrack App Assure</span></span> 

<span data-ttu-id="80aa1-158">App Assure プログラムは、ARM 版 Windows 10 を対象とする LOB、ISV、および Microsoft のファーストパーティ アプリの商用のお客様が利用できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-158">The App Assure program is available to commercial customers for their LOB, ISV and Microsoft first-party apps targeting Windows 10 on ARM.</span></span> <span data-ttu-id="80aa1-159">ARM 版 Windows 10 を使用してアプリの互換性の問題が発生した場合、Microsoft は、追加費用なしで、アプリの修正をトラブルシューティングおよび支援するための開発者向けリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-159">If commercial encounter an app compatibility issue using Windows 10 on ARM, Microsoft will provide developer resources to troubleshoot and assist with app remediations, at no additional cost.</span></span> <span data-ttu-id="80aa1-160">詳細については、aka.ms/AppAssure にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-160">To learn more,visit aka.ms/AppAssure</span></span>


<span data-ttu-id="80aa1-161">Surface Pro X でのアプリの実行について詳しくは、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-161">For more information about running apps on Surface Pro X, refer to:</span></span>

- [<span data-ttu-id="80aa1-162">Windows 10 ARM ベースの PC に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="80aa1-162">Windows 10 ARM-based PCs Support FAQ</span></span>](https://support.microsoft.com/help/4521606)
- [<span data-ttu-id="80aa1-163">ARM 版 Windows 10 のドキュメント</span><span class="sxs-lookup"><span data-stu-id="80aa1-163">Windows 10 on ARM documentation</span></span>](https://docs.microsoft.com/windows/arm)

## <span data-ttu-id="80aa1-164">仮想デスクトップ (VDI)</span><span class="sxs-lookup"><span data-stu-id="80aa1-164">Virtual Desktops (VDI)</span></span>

<span data-ttu-id="80aa1-165">Windows Virtual Desktop を使用すると、任意の場所から任意のコンピューティング デバイスまたはプラットフォーム上の Windows デスクトップ、アプリケーション、およびデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-165">Windows Virtual Desktop enables access to Windows desktops,applications, and data on any computing device or platform, from any location.</span></span> <span data-ttu-id="80aa1-166">詳しくは、[Windows Virtual Desktop のサイト](https://aka.ms/wvd)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-166">To learn more, refer to the [Windows Virtual Desktop site](https://aka.ms/wvd).</span></span> 

## <span data-ttu-id="80aa1-167">Surface Pro X で使用できるブラウザー</span><span class="sxs-lookup"><span data-stu-id="80aa1-167">Browsing with Surface Pro X</span></span>

<span data-ttu-id="80aa1-168">Surface Pro X では、一般的な各種のブラウザーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-168">Popular browsers run on Surface Pro X:</span></span>

- <span data-ttu-id="80aa1-169">また、Surface Pro X では、付属の Edge、Firefox、Chrome、Internet Explorer をすべて使用できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-169">In-box Edge, Firefox, Chrome, and Internet Explorer all run on Surface Pro X.</span></span>
- <span data-ttu-id="80aa1-170">Chromium に基づく Firefox と Microsoft Edge はネイティブで動作するため、ARM ベースのプロセッサで動作する Windows 10 PC で、高いパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-170">Firefox and Microsoft Edge based on Chromium run natively and therefore have enhanced performance on a Windows 10 PC on an ARM-based processor.</span></span>

## <span data-ttu-id="80aa1-171">Microsoft Office のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="80aa1-171">Installing and using Microsoft Office</span></span>

- <span data-ttu-id="80aa1-172">ARM ベースのプロセッサで動作する Windows 10 PC で最高のエクスペリエンスを実現する Office 365 をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-172">Use Office 365 for the best experience on a Windows 10 PC on an ARM-based processor.</span></span>
- <span data-ttu-id="80aa1-173">Office 365 の"クイック実行"により、ARM ベースのプロセッサで動作する Windows 10 PC での実行用に最適化された Outlook、Word、Excel、および PowerPoint がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-173">Office 365 "click-to-run" installs Outlook, Word, Excel, and PowerPoint, optimized to run on a Windows 10 PC on an ARM-based processor.</span></span>
- <span data-ttu-id="80aa1-174">Microsoft Teams も、Surface Pro X で快適にご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-174">Microsoft Teams runs great on Surface Pro X.</span></span>
- <span data-ttu-id="80aa1-175">Office 2019 など、Office の "永続バージョン" については、32 ビット バージョンをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-175">For "perpetual versions" of Office such as Office 2019, install the 32-bit version.</span></span>

## <span data-ttu-id="80aa1-176">VPN</span><span class="sxs-lookup"><span data-stu-id="80aa1-176">VPN</span></span>

<span data-ttu-id="80aa1-177">ARM ベースのプロセッサで動作する Windows 10 PC が特定のサード パーティ VPN でサポートされているかどうかを確認するには、VPN プロバイダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-177">To confirm if a specific third-party VPN supports a Windows 10 PC on an ARM-based processor, contact the VPN provider.</span></span>

## <span data-ttu-id="80aa1-178">機能の概要</span><span class="sxs-lookup"><span data-stu-id="80aa1-178">Feature summary</span></span>

<span data-ttu-id="80aa1-179">次の表は、ARM 版 Windows 10 を搭載した Surface Pro X で選択された主要機能の可用性を示しています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-179">The following tables show the availability of selected key features on Surface Pro X with Windows 10 on ARM.</span></span>


**<span data-ttu-id="80aa1-180">展開</span><span class="sxs-lookup"><span data-stu-id="80aa1-180">Deployment</span></span>**

| <span data-ttu-id="80aa1-181">機能</span><span class="sxs-lookup"><span data-stu-id="80aa1-181">Feature</span></span>                                                           | <span data-ttu-id="80aa1-182">Y/N</span><span class="sxs-lookup"><span data-stu-id="80aa1-182">Y/N</span></span> | <span data-ttu-id="80aa1-183">備考</span><span class="sxs-lookup"><span data-stu-id="80aa1-183">Notes</span></span>                                                                                                                             |
| ----------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="80aa1-184">Windows Autopilot</span><span class="sxs-lookup"><span data-stu-id="80aa1-184">Windows Autopilot</span></span>                                                 | <span data-ttu-id="80aa1-185">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-185">Yes</span></span> |                                                                                                                                   |
| <span data-ttu-id="80aa1-186">ネットワーク ブート (PXE) のサポート</span><span class="sxs-lookup"><span data-stu-id="80aa1-186">Support for Network Boot (PXE)</span></span>                                    | <span data-ttu-id="80aa1-187">なし</span><span class="sxs-lookup"><span data-stu-id="80aa1-187">No</span></span>  |                                                                                                                                   |
| <span data-ttu-id="80aa1-188">Windows 構成デザイナー</span><span class="sxs-lookup"><span data-stu-id="80aa1-188">Windows Configuration Designer</span></span>                                    | <span data-ttu-id="80aa1-189">なし</span><span class="sxs-lookup"><span data-stu-id="80aa1-189">No</span></span>  | <span data-ttu-id="80aa1-190">Surface Pro X では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-190">Not recommended for Surface Pro X.</span></span>                                                                                                |
| <span data-ttu-id="80aa1-191">WinPE</span><span class="sxs-lookup"><span data-stu-id="80aa1-191">WinPE</span></span>                                                             | <span data-ttu-id="80aa1-192">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-192">Yes</span></span> | <span data-ttu-id="80aa1-193">Surface Pro X では推奨されていません。Microsoft では、Surface Pro X で WinPE をサポートするために必要な .ISO とドライバーが提供されていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-193">Not recommended for Surface Pro X. Microsoft does not provide the necessary .ISO and drivers to support WinPE with Surface Pro X.</span></span> |
| <span data-ttu-id="80aa1-194">Endpoint Configuration Manager: オペレーティング システムの展開 (OSD)</span><span class="sxs-lookup"><span data-stu-id="80aa1-194">Endpoint Configuration Manager: Operating System Deployment (OSD)</span></span> | <span data-ttu-id="80aa1-195">なし</span><span class="sxs-lookup"><span data-stu-id="80aa1-195">No</span></span>  | <span data-ttu-id="80aa1-196">Surface Pro X ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-196">Not supported on Surface Pro X.</span></span>                                                                                                   |
| <span data-ttu-id="80aa1-197">MDT</span><span class="sxs-lookup"><span data-stu-id="80aa1-197">MDT</span></span>                                                               | <span data-ttu-id="80aa1-198">なし</span><span class="sxs-lookup"><span data-stu-id="80aa1-198">No</span></span>  | <span data-ttu-id="80aa1-199">Surface Pro X ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-199">Not supported on Surface Pro X.</span></span>                                                                                                   |

 
 
 **<span data-ttu-id="80aa1-200">管理</span><span class="sxs-lookup"><span data-stu-id="80aa1-200">Management</span></span>**
 

| <span data-ttu-id="80aa1-201">機能</span><span class="sxs-lookup"><span data-stu-id="80aa1-201">Feature</span></span>                                       | <span data-ttu-id="80aa1-202">Y/N</span><span class="sxs-lookup"><span data-stu-id="80aa1-202">Y/N</span></span>     | <span data-ttu-id="80aa1-203">備考</span><span class="sxs-lookup"><span data-stu-id="80aa1-203">Notes</span></span>                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="80aa1-204">Intune</span><span class="sxs-lookup"><span data-stu-id="80aa1-204">Intune</span></span>                                        | <span data-ttu-id="80aa1-205">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-205">Yes</span></span>     | <span data-ttu-id="80aa1-206">LTE は eSIM プロファイルで管理します。</span><span class="sxs-lookup"><span data-stu-id="80aa1-206">Manage LTE with eSIM profiles.</span></span>                                                        |
| <span data-ttu-id="80aa1-207">Windows Autopilot</span><span class="sxs-lookup"><span data-stu-id="80aa1-207">Windows Autopilot</span></span>                             | <span data-ttu-id="80aa1-208">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-208">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-209">Azure AD (共同管理)</span><span class="sxs-lookup"><span data-stu-id="80aa1-209">Azure AD (co-management)</span></span>                      | <span data-ttu-id="80aa1-210">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-210">Yes</span></span>     | <span data-ttu-id="80aa1-211">Azure AD または Active Directory (Hybrid Azure AD Join) に Surface Pro X を参加させます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-211">Ability to join Surface Pro X to Azure AD or Active Directory (Hybrid Azure AD Join).</span></span> |
| <span data-ttu-id="80aa1-212">Endpoint Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="80aa1-212">Endpoint Configuration Manager</span></span>                | <span data-ttu-id="80aa1-213">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-213">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-214">AC 復元時の電源オン</span><span class="sxs-lookup"><span data-stu-id="80aa1-214">Power on When AC Restore</span></span>                      | <span data-ttu-id="80aa1-215">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-215">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-216">ビジネス向け Surface 診断ツールキット (SDT)</span><span class="sxs-lookup"><span data-stu-id="80aa1-216">Surface Diagnostic Toolkit (SDT) for Business</span></span> | <span data-ttu-id="80aa1-217">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-217">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-218">Surface Asset Tag ツール</span><span class="sxs-lookup"><span data-stu-id="80aa1-218">Surface Asset Tag tool</span></span>                        | <span data-ttu-id="80aa1-219">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-219">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-220">Surface Enterprise Management Mode (SEMM)</span><span class="sxs-lookup"><span data-stu-id="80aa1-220">Surface Enterprise management Mode (SEMM)</span></span>     | <span data-ttu-id="80aa1-221">一部</span><span class="sxs-lookup"><span data-stu-id="80aa1-221">Partial</span></span> | <span data-ttu-id="80aa1-222">Surface Pro X のハードウェアをファームウェア レベルで無効にするオプションはありません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-222">No option to disable hardware on Surface Pro X at the firmware level.</span></span>                 |
| <span data-ttu-id="80aa1-223">Surface UEFI コンフィギュレータ</span><span class="sxs-lookup"><span data-stu-id="80aa1-223">Surface UEFI Configurator</span></span>                     | <span data-ttu-id="80aa1-224">なし</span><span class="sxs-lookup"><span data-stu-id="80aa1-224">No</span></span>      | <span data-ttu-id="80aa1-225">Surface Pro X のハードウェアを</span><span class="sxs-lookup"><span data-stu-id="80aa1-225">No option to disable hardware.</span></span> <span data-ttu-id="80aa1-226">ファームウェア レベルで無効にするオプションはありません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-226">on Surface Pro X at the firmware level.</span></span>                |
| <span data-ttu-id="80aa1-227">Surface UEFI マネージャー</span><span class="sxs-lookup"><span data-stu-id="80aa1-227">Surface UEFI Manager</span></span>                          | <span data-ttu-id="80aa1-228">一部</span><span class="sxs-lookup"><span data-stu-id="80aa1-228">Partial</span></span> | <span data-ttu-id="80aa1-229">Surface Pro X のハードウェアをファームウェア レベルで無効にするオプションはありません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-229">No option to disable hardware on Surface Pro X at the firmware level.</span></span>                 |

 

**<span data-ttu-id="80aa1-230">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="80aa1-230">Security</span></span>**
 

 <span data-ttu-id="80aa1-231">機能</span><span class="sxs-lookup"><span data-stu-id="80aa1-231">Feature</span></span>                                       | <span data-ttu-id="80aa1-232">Y/N</span><span class="sxs-lookup"><span data-stu-id="80aa1-232">Y/N</span></span>     | <span data-ttu-id="80aa1-233">備考</span><span class="sxs-lookup"><span data-stu-id="80aa1-233">Notes</span></span>                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="80aa1-234">BitLocker</span><span class="sxs-lookup"><span data-stu-id="80aa1-234">BitLocker</span></span>                                     | <span data-ttu-id="80aa1-235">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-235">Yes</span></span>     |                                                       |
| <span data-ttu-id="80aa1-236">Windows Defender</span><span class="sxs-lookup"><span data-stu-id="80aa1-236">Windows Defender</span></span>                              | <span data-ttu-id="80aa1-237">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-237">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-238">サード パーティ製ウィルス対策のサポート</span><span class="sxs-lookup"><span data-stu-id="80aa1-238">Support for third-party antivirus</span></span>             | <span data-ttu-id="80aa1-239">「備考」を参照</span><span class="sxs-lookup"><span data-stu-id="80aa1-239">See note</span></span>| <span data-ttu-id="80aa1-240">サード パーティ製ウイルス対策ソフトウェアには、ARM ベースのプロセッサで動作する Windows 10 PC にインストールできないものもあります。</span><span class="sxs-lookup"><span data-stu-id="80aa1-240">Some third-party antivirus software cannot be installed on a Windows 10 PC running on an ARM-based processor.</span></span> <span data-ttu-id="80aa1-241">サードパーティ製のウイルス対策ソフトウェア プロバイダーとのコラボレーションは、ARM ベースの PC での AV アプリの準備用に継続されています。</span><span class="sxs-lookup"><span data-stu-id="80aa1-241">Collaboration with third-party antivirus software providers is continuing for AV app readiness on ARM-based PCs.</span></span> <span data-ttu-id="80aa1-242">アプリが利用可能になる時期については、各ウイルス対策ソフトウェア プロバイダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-242">Contact your antivirus software provider to understand when their apps will be available.</span></span> |
| <span data-ttu-id="80aa1-243">セキュア ブート</span><span class="sxs-lookup"><span data-stu-id="80aa1-243">Secure Boot</span></span>               | <span data-ttu-id="80aa1-244">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-244">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-245">Windows 情報保護</span><span class="sxs-lookup"><span data-stu-id="80aa1-245">Windows Information Protection</span></span>                      | <span data-ttu-id="80aa1-246">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-246">Yes</span></span>     |                                                                                       |
| <span data-ttu-id="80aa1-247">Surface Data Eraser (SDE)</span><span class="sxs-lookup"><span data-stu-id="80aa1-247">Surface Data Eraser (SDE)</span></span>     | <span data-ttu-id="80aa1-248">あり</span><span class="sxs-lookup"><span data-stu-id="80aa1-248">Yes</span></span>     |                                                                                       |




## <span data-ttu-id="80aa1-249">FAQ</span><span class="sxs-lookup"><span data-stu-id="80aa1-249">FAQ</span></span>

### <span data-ttu-id="80aa1-250">MDT または Endpoint Configuration Manager を使用して Surface Pro X を展開できますか?</span><span class="sxs-lookup"><span data-stu-id="80aa1-250">Can I deploy Surface Pro X with MDT or Endpoint Configuration Manager?</span></span>

<span data-ttu-id="80aa1-251">現在、Microsoft Deployment Toolkit (MDT) および Microsoft Endpoint Configuration Manager では、Surface Pro X でのオペレーティング システムの展開がサポートされていません。イメージ ベースの展開をご利用のお客様は、クラウドへの移行に適したタイミングを引き続き評価しつつ、Surface Pro 7 の使用をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-251">The Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager  currently do not support Surface Pro X for operating system deployment.Customers relying on image-based deployment should consider Surface Pro 7 while they continue to evaluate the right time to transition to the cloud.</span></span>

### <span data-ttu-id="80aa1-252">Surface Pro X を展開する方法は?</span><span class="sxs-lookup"><span data-stu-id="80aa1-252">How can I deploy Surface Pro X?</span></span>

<span data-ttu-id="80aa1-253">Surface Pro X は Windows Autopilot を使用して展開できます。</span><span class="sxs-lookup"><span data-stu-id="80aa1-253">Deploy Surface Pro X using Windows Autopilot.</span></span>

### <span data-ttu-id="80aa1-254">BMR は利用できますか?</span><span class="sxs-lookup"><span data-stu-id="80aa1-254">Is a BMR available?</span></span>

<span data-ttu-id="80aa1-255">はい、「[Surface の回復イメージのダウンロード](https://support.microsoft.com/surfacerecoveryimage)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80aa1-255">Yes, refer to [Download a recovery image for your Surface](https://support.microsoft.com/surfacerecoveryimage).</span></span>

### <span data-ttu-id="80aa1-256">Surface Pro X を管理するためには Intune が必要ですか?</span><span class="sxs-lookup"><span data-stu-id="80aa1-256">Is Intune required to manage Surface Pro X?</span></span>

<span data-ttu-id="80aa1-257">Intune をお勧めしますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="80aa1-257">Intune is recommended but not required.</span></span> <span data-ttu-id="80aa1-258">Autopilot で展開すると、Surface Pro X デバイスを Azure ADまたはActive Directory (Hybrid Azure AD Join) に参加させて、Intune でデバイスを管理することも、Endpoint Configuration Manager でデバイスを共同管理することもできます (32 ビットの x86 ConfigMgr クライアントがインストールされます)。</span><span class="sxs-lookup"><span data-stu-id="80aa1-258">Once deployed in Autopilot, you can join Surface Pro X devices to Azure AD or Active Directory (Hybrid Azure AD Join) where you will be able to manage the devices with Intune or co-manage them with Endpoint Configuration Manager, which will install the 32-bit x86 ConfigMgr client.</span></span>
