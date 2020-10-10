---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成する方法と、ターゲットサーフェスデバイスのファームウェア設定を管理する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/09/2020
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
ms.openlocfilehash: 20d1b187a565f210eedc632be1addeac5dd714ba
ms.sourcegitcommit: 7d5b0a7948eb540d6849a0e2c70a1058584cc5f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "11105862"
---
# <span data-ttu-id="de7df-103">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="de7df-103">Intune management of Surface UEFI settings</span></span>

## <span data-ttu-id="de7df-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="de7df-104">Introduction</span></span>

<span data-ttu-id="de7df-105">クラウドからデバイスを管理する機能によって、ライフサイクル全体の IT 展開とプロビジョニングが大幅に簡略化されました。</span><span class="sxs-lookup"><span data-stu-id="de7df-105">The ability to manage devices from the cloud has dramatically simplified IT deployment and provisioning across the lifecycle.</span></span> <span data-ttu-id="de7df-106">Microsoft Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると ( [パブリックプレビュー](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)で利用できるようになりました)、Surface uefi 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-106">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in [public preview](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="de7df-107">DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-107">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="de7df-108">よく寄せられる質問に対する回答については、「 [Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理のアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-108">For answers to frequently asked questions, see [Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

### <span data-ttu-id="de7df-109">Background</span><span class="sxs-lookup"><span data-stu-id="de7df-109">Background</span></span>

<span data-ttu-id="de7df-110">Windows 10 を実行しているコンピューターと同様に、Surface デバイスは、ハードドライブ、ディスプレイデバイス、USB ポート、その他のデバイスとのインターフェイスを可能にする SoC に保存されているコードに依存します。</span><span class="sxs-lookup"><span data-stu-id="de7df-110">Like any computer running Windows 10, Surface devices rely on code stored in the SoC that enables the CPU to interface with hard drives, display devices, USB ports, and other devices.</span></span> <span data-ttu-id="de7df-111">この読み取り専用メモリ (ROM) に保存されているプログラムは、ファームウェアと呼ばれます (動的メディアに保存されているプログラムはソフトウェアと呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="de7df-111">The programs stored in this read-only memory (ROM) are known as firmware (while programs stored in dynamic media are known as software).</span></span>

<span data-ttu-id="de7df-112">現在市場で利用できる他の Windows 10 デバイスとは対照的に、Surface は、豊富な UEFI 構成設定を使用してファームウェアを構成および管理する機能を IT 管理者に提供します。</span><span class="sxs-lookup"><span data-stu-id="de7df-112">In contrast to other Windows 10 devices available in the market today, Surface provides IT admins with the ability to configure and manage firmware through a rich set of UEFI configuration settings.</span></span> <span data-ttu-id="de7df-113">これにより、モバイルデバイス管理 (MDM) ポリシー、構成マネージャー、またはグループポリシーによって実装された、ソフトウェアベースのポリシー管理の上にある、ハードウェアコントロールのレイヤーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-113">This provides a layer of hardware control on top of software-based policy management as implemented via mobile device management (MDM) policies, Configuration Manager or Group Policy.</span></span> <span data-ttu-id="de7df-114">たとえば、機密情報が含まれるセキュリティの高い領域にデバイスを展開する組織では、ハードウェアレベルで機能を削除することにより、カメラの使用を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-114">For example, organizations deploying devices in highly secure areas with sensitive information can prevent camera use by removing functionality at the hardware level.</span></span> <span data-ttu-id="de7df-115">デバイスの観点から見ると、ファームウェア設定を使用してカメラをオフにすることは、カメラを物理的に取り外すことと同じです。</span><span class="sxs-lookup"><span data-stu-id="de7df-115">From a device standpoint, turning the camera off via a firmware setting is equivalent to physically removing the camera.</span></span> <span data-ttu-id="de7df-116">ファームウェアレベルでの管理の追加セキュリティと比較して、オペレーティングシステムソフトウェアの設定のみに依存するようにします。</span><span class="sxs-lookup"><span data-stu-id="de7df-116">Compare the added security of managing at the firmware level to relying only on operating system software settings.</span></span> <span data-ttu-id="de7df-117">たとえば、ドメイン環境のポリシー設定を使用して Windows audio サービスを無効にした場合、ローカル管理者は引き続きサービスを再び有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-117">For example, if you disable the Windows audio service via a policy setting in a domain environment, a local admin could still re-enable the service.</span></span>

### <span data-ttu-id="de7df-118">DFCI と SEMM</span><span class="sxs-lookup"><span data-stu-id="de7df-118">DFCI versus SEMM</span></span>

<span data-ttu-id="de7df-119">この時点では、ファームウェアの管理には、手動での IT 集約的なタスクのオーバーヘッドにより、デバイスを Surface Enterprise 管理モード (SEMM) に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-119">Until now, managing firmware required enrolling devices into Surface Enterprise Management Mode (SEMM) with the overhead of ongoing manual IT-intensive tasks.</span></span> <span data-ttu-id="de7df-120">例として、SEMM は、IT スタッフが各 PC に物理的にアクセスして、証明書管理プロセスの一部として2桁の pin を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-120">As an example, SEMM requires IT staff to physically access each PC to enter a two-digit pin as part of the certificate management process.</span></span> <span data-ttu-id="de7df-121">SEMM は、厳格なオンプレミス環境における組織向けの優れたソリューションですが、複雑さと IT 集約的な要件によって使用コストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="de7df-121">Although SEMM remains a good solution for organizations in a strictly on-premises environment, its complexity and IT-intensive requirements make it costly to use.</span></span>

<span data-ttu-id="de7df-122">Microsoft Intune で新しく統合された UEFI ファームウェア管理機能を使用すると、ハードウェアのロックダウン機能が簡素化され、1つのコンソールでのプロビジョニング、セキュリティ、効率化された更新のための新しい機能で簡単に使用できるようになりました。 [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)として統合されました。</span><span class="sxs-lookup"><span data-stu-id="de7df-122">Now with newly integrated UEFI firmware management capabilities in Microsoft Intune, the ability to lock down hardware is simplified and easier to use with new features for provisioning, security, and streamlined updating all in a single console, now unified as [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager).</span></span> <span data-ttu-id="de7df-123">次の図は、デバイスに直接表示されている UEFI の設定を示しています (左側)。また、エンドポイントマネージャー本体 (右) に表示されています。</span><span class="sxs-lookup"><span data-stu-id="de7df-123">The following figure shows UEFI settings viewed directly on the device (left) and viewed in the Endpoint Manager console (right).</span></span>

![デバイス (左側) とエンドポイントマネージャーコンソール (右) に表示される UEFI の設定](images/uefidfci.png)

<span data-ttu-id="de7df-125">Crucially を使用すると、IT 管理者による手動の操作が不要になって、ゼロのタッチ管理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="de7df-125">Crucially, DFCI enables zero touch management, eliminating the need for manual interaction by IT admins.</span></span> <span data-ttu-id="de7df-126">DFCI は、Intune のデバイスプロファイル機能を使用して、Windows 自動操縦を介して展開されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-126">DFCI is deployed via Windows Autopilot using the device profiles capability in Intune.</span></span> <span data-ttu-id="de7df-127">デバイスプロファイルを使用すると、設定の追加と構成を行うことができます。これは、組織内の管理に登録されたデバイスに展開することができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-127">A device profile allows you to add and configure settings which can then be deployed to devices enrolled in management within your organization.</span></span> <span data-ttu-id="de7df-128">デバイスがデバイスプロファイルを受信すると、その機能と設定が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-128">Once the device receives the device profile, the features and settings are applied automatically.</span></span> <span data-ttu-id="de7df-129">一般的なデバイスプロファイルの例には、メール、デバイスの制限、VPN、Wi-fi、管理用テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="de7df-129">Examples of common device profiles include Email, Device restrictions, VPN, Wi-Fi, and Administrative templates.</span></span> <span data-ttu-id="de7df-130">DFCI は、オンプレミスのインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できる追加のデバイスプロファイルです。</span><span class="sxs-lookup"><span data-stu-id="de7df-130">DFCI is simply an additional device profile that enables you to manage UEFI configuration settings from the cloud without having to maintain on-premises infrastructure.</span></span>  

## <span data-ttu-id="de7df-131">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="de7df-131">Supported devices</span></span>

<span data-ttu-id="de7df-132">DFCI は、次のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="de7df-132">DFCI is supported in the following devices:</span></span>

- <span data-ttu-id="de7df-133">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="de7df-133">Surface Pro 7</span></span>
- <span data-ttu-id="de7df-134">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="de7df-134">Surface Pro X</span></span>
- <span data-ttu-id="de7df-135">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="de7df-135">Surface Laptop 3</span></span>
- <span data-ttu-id="de7df-136">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="de7df-136">Surface Book 3</span></span>
- <span data-ttu-id="de7df-137">Surface のノート Pc の移動</span><span class="sxs-lookup"><span data-stu-id="de7df-137">Surface Laptop Go</span></span>

> [!NOTE]
> <span data-ttu-id="de7df-138">Surface Pro X では、組み込みのカメラ、オーディオ、Wi-fi/Bluetooth 用の DFCI 設定管理はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="de7df-138">Surface Pro X does not support DFCI settings management for built-in camera, audio, and Wi-Fi/Bluetooth.</span></span>

## <span data-ttu-id="de7df-139">前提条件</span><span class="sxs-lookup"><span data-stu-id="de7df-139">Prerequisites</span></span>

- <span data-ttu-id="de7df-140">デバイスは、 [Microsoft クラウドソリューションプロバイダー (CSP) パートナー](https://partner.microsoft.com/membership/cloud-solution-provider) または OEM ディストリビューターによって Windows 自動操縦に登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-140">Devices must be registered with Windows Autopilot by a [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/membership/cloud-solution-provider) or OEM distributor.</span></span>

- <span data-ttu-id="de7df-141">Surface 用の DFCI を構成する前に、  [Microsoft Intune](https://docs.microsoft.com/intune/) と [azure Active DIRECTORY](https://docs.microsoft.com/azure/active-directory/) (azure AD) での自動操縦の構成要件について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-141">Before configuring DFCI for Surface, you should be familiar with Autopilot configuration requirements in  [Microsoft Intune](https://docs.microsoft.com/intune/) and [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD).</span></span>

## <span data-ttu-id="de7df-142">始める前に</span><span class="sxs-lookup"><span data-stu-id="de7df-142">Before you begin</span></span>

<span data-ttu-id="de7df-143">ターゲット Surface デバイスを Azure AD セキュリティグループに追加します。</span><span class="sxs-lookup"><span data-stu-id="de7df-143">Add your target Surface devices to an Azure AD security group.</span></span> <span data-ttu-id="de7df-144">セキュリティグループの作成と管理の詳細については、「 [Intune ドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-144">For more information about creating and managing security groups, refer to [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups).</span></span>

## <span data-ttu-id="de7df-145">Surface デバイス用の DFCI 管理を構成する</span><span class="sxs-lookup"><span data-stu-id="de7df-145">Configure DFCI management for Surface devices</span></span>

<span data-ttu-id="de7df-146">DFCI 環境では、登録済みデバイスに設定を適用するために、設定と自動操縦プロファイルを含む DFCI プロファイルを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-146">A DFCI environment requires setting up a DFCI profile that contains  the settings and an Autopilot profile to apply the settings to registered devices.</span></span> <span data-ttu-id="de7df-147">また、ユーザーがデバイスを初めて起動したときに、OOBE のセットアップ中に設定をプッシュダウンすることを確認するために、登録ステータスプロファイルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="de7df-147">An enrollment status profile is also recommended to ensure settings are pushed down during OOBE setup when users first start the device.</span></span> <span data-ttu-id="de7df-148">このガイドでは、DFCI 環境を構成し、ターゲット Surface デバイスの UEFI 構成設定を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de7df-148">This guide explains how to configure the DFCI environment and manage UEFI configuration settings for targeted Surface devices.</span></span>

## <span data-ttu-id="de7df-149">DFCI プロフィールの作成</span><span class="sxs-lookup"><span data-stu-id="de7df-149">Create DFCI profile</span></span>

<span data-ttu-id="de7df-150">DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲットデバイスを含む Azure AD セキュリティグループに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-150">Before configuring DFCI policy settings, first create a DFCI profile and assign it to the Azure AD security group that contains your target devices.</span></span>

1. <span data-ttu-id="de7df-151">Devicemanagement.microsoft.com でテナントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="de7df-151">Sign into your tenant at  devicemanagement.microsoft.com.</span></span>
2. <span data-ttu-id="de7df-152">Microsoft Endpoint Manager 管理センターで、[ **デバイス] > 構成プロファイル** ] の [プロファイルの作成] > 名前を入力します。たとえば、 **Dfci 構成ポリシーなどです。**</span><span class="sxs-lookup"><span data-stu-id="de7df-152">In the Microsoft Endpoint Manager Admin Center, select **Devices > Configuration profiles > Create profile** and enter a name; for example, **DFCI Configuration Policy.**</span></span>
3. <span data-ttu-id="de7df-153">プラットフォームの種類については **、[Windows 10** 以降] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-153">Select **Windows 10 and later** for platform type.</span></span>
4. <span data-ttu-id="de7df-154">[Profile type] ドロップダウンリストで、[ **Device ファームウェア構成インターフェイス** ] を選択して、利用可能なすべてのポリシー設定が含まれている dfci ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="de7df-154">In the Profile type drop down list, select **Device Firmware Configuration Interface** to open the DFCI blade containing all available policy settings.</span></span> <span data-ttu-id="de7df-155">DFCI の設定の詳細については、このページまたは [Intune のドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)の表1を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-155">For information on DFCI settings, refer to Table 1 on this page or the [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span> <span data-ttu-id="de7df-156">Dfci プロファイルを編集することにより、初期セットアッププロセスまたは後で DFCI 設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="de7df-156">You can configure DFCI settings during the initial setup process or later by editing the DFCI profile.</span></span>

    ![DFCI プロフィールの作成](images/df1.png)

5. <span data-ttu-id="de7df-158">[ **OK]** をクリックし、[ **作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-158">Click **OK** and then select **Create**.</span></span>
6. <span data-ttu-id="de7df-159">[ **割り当て** ] を選択し、次の図に示すよう **に** 、ターゲットデバイスを含む Azure AD セキュリティグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-159">Select **Assignments** and under **Select groups to include** select the Azure AD security group that contains your target devices, as shown in the following figure.</span></span> <span data-ttu-id="de7df-160">**[Save]** (保存) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de7df-160">Click **Save**.</span></span>

    ![セキュリティグループの割り当て](images/df2a.png)

## <span data-ttu-id="de7df-162">自動操縦プロファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="de7df-162">Create Autopilot profile</span></span>

1. <span data-ttu-id="de7df-163">Devicemanagement.microsoft.com のエンドポイントマネージャーで、[ **Windows 登録 > デバイス** ] を選択し、[ **展開プロファイル**] まで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="de7df-163">In Endpoint Manager at  devicemanagement.microsoft.com, select **devices > Windows enrollment** and scroll down to **Deployment profiles**.</span></span>
2. <span data-ttu-id="de7df-164">[ **プロファイルの作成** ] を選択し、名前を入力します。たとえば、 **[自動操縦プロファイル**] を選び、[ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-164">Select **Create profile** and enter a name; for example, **My Autopilot profile**, and select **Next**.</span></span>
3. <span data-ttu-id="de7df-165">次の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-165">Select the following settings:</span></span>

    - <span data-ttu-id="de7df-166">展開モード: **ユーザー主導型**。</span><span class="sxs-lookup"><span data-stu-id="de7df-166">Deployment mode: **User-Driven**.</span></span>
    - <span data-ttu-id="de7df-167">参加の種類: Azure **AD が結合**されました。</span><span class="sxs-lookup"><span data-stu-id="de7df-167">Join type: Azure **AD joined**.</span></span>

4. <span data-ttu-id="de7df-168">その他の既定の設定はそのままにして、次の図に示すように [ **次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-168">Leave the remaining default settings unchanged and select **Next**, as shown in the following figure.</span></span>

    ![自動操縦プロファイルを作成する](images/df3b.png)

5. <span data-ttu-id="de7df-170">[割り当て] ページで、[ **グループの選択** ] を選んで、Azure AD セキュリティグループを追加してクリックします。</span><span class="sxs-lookup"><span data-stu-id="de7df-170">On the Assignments page, choose **Select groups to include** and click your Azure AD security group.</span></span> <span data-ttu-id="de7df-171">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-171">Select **Next**.</span></span>
6. <span data-ttu-id="de7df-172">概要を承諾し、[ **作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-172">Accept the summary and then select **Create**.</span></span> <span data-ttu-id="de7df-173">自動操縦プロファイルが作成され、グループに割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="de7df-173">The Autopilot profile is now created and assigned to the group.</span></span>

## <span data-ttu-id="de7df-174">登録状態のページを構成する</span><span class="sxs-lookup"><span data-stu-id="de7df-174">Configure Enrollment Status Page</span></span>

<span data-ttu-id="de7df-175">ユーザーがサインインする前に、デバイスで OOBE 中に DFCI 構成が適用されるようにするには、登録の状態を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-175">To ensure that devices apply the DFCI configuration during OOBE before users sign in, you need to configure enrollment status.</span></span>

<span data-ttu-id="de7df-176">詳細については、「 [登録の状態を設定](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)する」ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-176">For more information, refer to [Set up an enrollment status page](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status).</span></span>


## <span data-ttu-id="de7df-177">Surface デバイスで DFCI 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="de7df-177">Configure DFCI settings on Surface devices</span></span>

<span data-ttu-id="de7df-178">DFCI には、ハードウェアレベルでデバイスをロックダウンすることによって、より高度なセキュリティを提供する、合理的な一連の UEFI 構成ポリシーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="de7df-178">DFCI includes a streamlined set of UEFI configuration policies that provide an extra level of security by locking down devices at the hardware level.</span></span> <span data-ttu-id="de7df-179">DFCI は、ソフトウェアレベルでモバイルデバイス管理設定と連携して使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="de7df-179">DFCI is designed to be used in conjunction with mobile device management settings at the software level.</span></span> <span data-ttu-id="de7df-180">DFCI 設定は、Surface デバイスに組み込まれているハードウェアコンポーネントにのみ影響します。 USB web カメラなどの添付された周辺機器に拡張されることはありません。</span><span class="sxs-lookup"><span data-stu-id="de7df-180">Note that DFCI settings only affect hardware components built into Surface devices and do not extend to attached peripherals such as USB webcams.</span></span> <span data-ttu-id="de7df-181">(ただし、Intune のデバイス制限ポリシーを使用して、添付されている周辺機器へのアクセスをソフトウェアレベルでオフにすることができます)。</span><span class="sxs-lookup"><span data-stu-id="de7df-181">(However, you can use Device restriction policies in Intune to turn off access to attached peripherals at the software level).</span></span>

<span data-ttu-id="de7df-182">次の図に示すように、[エンドポイントマネージャー] から DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="de7df-182">You configure DFCI policy settings by editing the DFCI profile from Endpoint Manager, as shown in the figure below.</span></span> 

- <span data-ttu-id="de7df-183">Devicemanagement.microsoft.com のエンドポイントマネージャーで、[ **デバイス > Windows > 構成プロファイル] > "DFCI profile name" > Properties > Settings**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-183">In Endpoint Manager at  devicemanagement.microsoft.com, select **Devices > Windows > Configuration Profiles > “DFCI profile name” > Properties > Settings**.</span></span>

    ![DFCI 設定を構成する](images/dfciconfig.png)

### <span data-ttu-id="de7df-185">ユーザーによる UEFI 設定へのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="de7df-185">Block user access to UEFI settings</span></span>

<span data-ttu-id="de7df-186">多くのお客様は、ユーザーが UEFI 設定を変更できないようにする機能は非常に重要であり、DFCI を使用する主な理由です。</span><span class="sxs-lookup"><span data-stu-id="de7df-186">For many customers, the ability to block users from changing UEFI settings is critically important and a primary reason to use DFCI.</span></span> <span data-ttu-id="de7df-187">表1で示したように、これは [ **ローカルユーザーによる UEFI 設定の変更を許可**する] 設定によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-187">As listed in Table 1, this is managed via the setting **Allow local user to change UEFI settings**.</span></span> <span data-ttu-id="de7df-188">この設定を編集または構成しない場合、ローカルユーザーは Intune で管理されていない UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="de7df-188">If you do not edit or configure this setting, local users will be able to change any UEFI setting not managed by Intune.</span></span> <span data-ttu-id="de7df-189">そのため、**ローカルユーザーによる UEFI 設定の変更を許可**しないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="de7df-189">Therefore, it’s highly recommended to disable **Allow local user to change UEFI settings.**</span></span>
<span data-ttu-id="de7df-190">DFCI 設定の残りの部分では、ユーザーが使用できる機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-190">The rest of the DFCI settings enable you to turn off functionality that would otherwise be available to users.</span></span> <span data-ttu-id="de7df-191">たとえば、安全性の高い領域の機密情報を保護する必要がある場合は、カメラを無効にすることができます。また、ユーザーが USB ドライブから起動したくない場合は、無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="de7df-191">For example, if you need to protect sensitive information in highly secure areas, you can disable the camera, and if you don’t want users booting from USB drives, you can disable that also.</span></span>

### <span data-ttu-id="de7df-192">表 1.</span><span class="sxs-lookup"><span data-stu-id="de7df-192">Table 1.</span></span> <span data-ttu-id="de7df-193">DFCI のシナリオ</span><span class="sxs-lookup"><span data-stu-id="de7df-193">DFCI scenarios</span></span>

| <span data-ttu-id="de7df-194">デバイス管理の目標</span><span class="sxs-lookup"><span data-stu-id="de7df-194">Device management goal</span></span>                        | <span data-ttu-id="de7df-195">構成の手順</span><span class="sxs-lookup"><span data-stu-id="de7df-195">Configuration steps</span></span>                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="de7df-196">ローカルユーザーが UEFI 設定を変更できないようにブロックする</span><span class="sxs-lookup"><span data-stu-id="de7df-196">Block local users from changing UEFI settings</span></span> | <span data-ttu-id="de7df-197">[ **セキュリティ機能 > ローカルユーザーによる UEFI の設定の変更を許可する**] で、[ **なし**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-197">Under **Security Features > Allow local user to change UEFI settings**, select **None**.</span></span>              |
| <span data-ttu-id="de7df-198">カメラを無効にする</span><span class="sxs-lookup"><span data-stu-id="de7df-198">Disable cameras</span></span>                               | <span data-ttu-id="de7df-199">[ **内蔵ハードウェア > カメラ**] で [ **無効**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-199">Under **Built in Hardware > Cameras**, select **Disabled**.</span></span>                                       |
| <span data-ttu-id="de7df-200">マイクとスピーカーを無効にする</span><span class="sxs-lookup"><span data-stu-id="de7df-200">Disable Microphones and speakers</span></span>              | <span data-ttu-id="de7df-201">[ **内蔵ハードウェア > マイクとスピーカー**] で、[ **無効**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-201">Under **Built in Hardware > Microphones and speakers**, select **Disabled**.</span></span>                      |
| <span data-ttu-id="de7df-202">無線を無効にする (Bluetooth、Wi-fi)</span><span class="sxs-lookup"><span data-stu-id="de7df-202">Disable radios (Bluetooth, Wi-Fi)</span></span>             | <span data-ttu-id="de7df-203">[ **内蔵ハードウェア > 無線 (Bluetooth、wi-fi など)**] で [ **無効**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-203">Under **Built in Hardware > Radios (Bluetooth, Wi-Fi, etc…)**, select **Disabled**.</span></span>                   |
| <span data-ttu-id="de7df-204">外部メディアからの起動を無効にする (USB、SD)</span><span class="sxs-lookup"><span data-stu-id="de7df-204">Disable Boot from external media (USB, SD)</span></span>    | <span data-ttu-id="de7df-205">[ **内蔵ハードウェア > ブートオプション > 外部メディア (USB、SD) から起動**する] で [ **無効**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-205">Under **Built in Hardware > Boot Options > Boot from external media (USB, SD)**, select **Disabled**.</span></span> |

> [!CAUTION]
> <span data-ttu-id="de7df-206">[ **無線を無効にする (Bluetooth、wi-fi)** ] 設定は、有線イーサネット接続を備えたデバイスでのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-206">The **Disable radios (Bluetooth, Wi-Fi)** setting should only be used on devices that have a wired Ethernet connection.</span></span>
 
> [!NOTE]
>  <span data-ttu-id="de7df-207">Intune の DFCI には、現在 Surface デバイスに適用されていない2つの設定が含まれています: (1) CPU および IO の仮想化と (2) ネットワークアダプターからの起動を無効にします。</span><span class="sxs-lookup"><span data-stu-id="de7df-207">DFCI in Intune includes two settings that do not currently apply to Surface devices: (1) CPU and IO virtualization and (2) Disable Boot from network adapters.</span></span>
 
<span data-ttu-id="de7df-208">Intune には、管理者権限と適用ルールを委任してデバイスの種類を管理するためのスコープタグが用意されています。</span><span class="sxs-lookup"><span data-stu-id="de7df-208">Intune provides Scope tags to delegate administrative rights and Applicability Rules to manage device types.</span></span> <span data-ttu-id="de7df-209">ポリシー管理のサポートとすべての DFCI 設定の詳細については、 [Microsoft Intune のドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-209">For more information about policy management support and full details on all DFCI settings, refer to [Microsoft Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span>

## <span data-ttu-id="de7df-210">自動操縦でデバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="de7df-210">Register devices in Autopilot</span></span>

<span data-ttu-id="de7df-211">上で説明したように、DFCI を適用できるのは、再販業者またはディストリビューターによって Windows 自動操縦に登録されているデバイスに限られます。この時点では、Surface Pro 7、Surface Pro X、Surface ノート Pc 3 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="de7df-211">As stated above, DFCI can only be applied on devices registered in Windows Autopilot by your reseller or distributor and is only supported, at this time, on Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="de7df-212">セキュリティ上の理由から、デバイスを自動操縦に "セルフプロビジョニング" することはできません。</span><span class="sxs-lookup"><span data-stu-id="de7df-212">For security reasons, it’s not possible to “self-provision” your devices into Autopilot.</span></span>

## <span data-ttu-id="de7df-213">自動操縦機器を手動で同期する</span><span class="sxs-lookup"><span data-stu-id="de7df-213">Manually Sync Autopilot devices</span></span>

<span data-ttu-id="de7df-214">Intune ポリシー設定は通常、ほぼ即座に適用されますが、ターゲットデバイスで設定が有効になるまで10分ほど時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-214">Although Intune policy settings typically get applied almost immediately, there may be a delay of 10 minutes before the settings take effect on targeted devices.</span></span> <span data-ttu-id="de7df-215">まれな状況では、最大8時間の遅延が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-215">In rare circumstances, delays of up to 8 hours are possible.</span></span> <span data-ttu-id="de7df-216">設定ができるだけ早く適用されるようにする (テストシナリオなど) には、ターゲットデバイスを手動で同期することができます。</span><span class="sxs-lookup"><span data-stu-id="de7df-216">To ensure settings apply as soon as possible, (such as in test scenarios), you can manually sync the target devices.</span></span>

- <span data-ttu-id="de7df-217">Devicemanagement.microsoft.com のエンドポイントマネージャーで、[デバイス **> デバイスの登録 > windows enrollment > Windows 自動操縦デバイス** ] に移動し、[ **同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-217">In Endpoint Manager at  devicemanagement.microsoft.com, go to **Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.</span></span>

 <span data-ttu-id="de7df-218">詳細については、「 [Windows デバイスを手動で同期](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-218">For more information, refer to [Sync your Windows device manually](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).</span></span>

> [!NOTE]
> <span data-ttu-id="de7df-219">UEFI で直接設定を調整する場合は、デバイスが標準の Windows ログインに完全に再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-219">When adjusting settings directly in UEFI, you need to ensure the device fully restarts to the standard Windows login.</span></span>

## <span data-ttu-id="de7df-220">DFCI で管理されているデバイスで UEFI 設定を確認する</span><span class="sxs-lookup"><span data-stu-id="de7df-220">Verifying UEFI settings on DFCI-managed devices</span></span>

<span data-ttu-id="de7df-221">テスト環境では、Surface UEFI インターフェイスで設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="de7df-221">In a test environment, you can verify settings in the Surface UEFI interface.</span></span>

1. <span data-ttu-id="de7df-222">[Surface UEFI] を開きます。これには、 **ボリューム** と **電源** ボタンを同時に押す必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7df-222">Open Surface UEFI, which involves pressing the **Volume +** and **Power** buttons at the same time.</span></span>
2. <span data-ttu-id="de7df-223">[ **デバイス**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-223">Select **Devices**.</span></span> <span data-ttu-id="de7df-224">次の図に示すように、[UEFI] メニューには、構成済みの設定が反映されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-224">The UEFI menu will reflect configured settings, as shown in the following figure.</span></span>

    ![Surface UEFI](images/df3.png)

    <span data-ttu-id="de7df-226">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-226">Note how:</span></span>

      - <span data-ttu-id="de7df-227">[ **ローカルユーザーによる UEFI の変更を許可** する] 設定が [なし] に設定されているため、設定が灰色表示されています。</span><span class="sxs-lookup"><span data-stu-id="de7df-227">The settings are greyed out because **Allow local user to change UEFI setting** is set to None.</span></span>
      - <span data-ttu-id="de7df-228">**マイクとスピーカー**が**無効**に設定されているため、オーディオはオフに設定されます。</span><span class="sxs-lookup"><span data-stu-id="de7df-228">Audio is set to off because **Microphones and speakers** are set to **Disabled**.</span></span>

## <span data-ttu-id="de7df-229">DFCI ポリシー設定の削除</span><span class="sxs-lookup"><span data-stu-id="de7df-229">Removing DFCI policy settings</span></span>

<span data-ttu-id="de7df-230">DFCI プロファイルを作成すると、構成されているすべての設定は、プロファイルの管理範囲内のすべてのデバイスで引き続き有効になります。</span><span class="sxs-lookup"><span data-stu-id="de7df-230">When you create a DFCI profile, all configured settings will remain in effect across all devices within the profile’s scope of management.</span></span> <span data-ttu-id="de7df-231">Dfci のポリシー設定は、DFCI プロファイルを直接編集することによってのみ削除できます。</span><span class="sxs-lookup"><span data-stu-id="de7df-231">You can only remove DFCI policy settings by editing the DFCI profile directly.</span></span>

<span data-ttu-id="de7df-232">元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="de7df-232">If the original DFCI profile has been deleted, you can remove policy settings by creating a new profile and then editing the settings, as appropriate.</span></span>

## <span data-ttu-id="de7df-233">DFCI 管理の削除</span><span class="sxs-lookup"><span data-stu-id="de7df-233">Removing DFCI management</span></span>

**<span data-ttu-id="de7df-234">DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻すには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="de7df-234">To remove DFCI management and return device to factory new state:</span></span>**

1. <span data-ttu-id="de7df-235">Intune からデバイスを削除する:</span><span class="sxs-lookup"><span data-stu-id="de7df-235">Retire the device from Intune:</span></span>
    1. <span data-ttu-id="de7df-236">Devicemanagement.microsoft.com のエンドポイントマネージャーで、[ **グループ > すべてのデバイス**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-236">In Endpoint Manager at  devicemanagement.microsoft.com, choose **Groups > All Devices**.</span></span> <span data-ttu-id="de7df-237">削除するデバイスを選択し、[インベントリから削除] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="de7df-237">Select the devices you want to retire, and then choose **Retire/Wipe.**</span></span> <span data-ttu-id="de7df-238">詳細について [は、「ワイプを使用してデバイスを削除する」または「手動でデバイスを登録解除](https://docs.microsoft.com/intune/remote-actions/devices-wipe)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7df-238">To learn more refer to [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/remote-actions/devices-wipe).</span></span> 
2. <span data-ttu-id="de7df-239">自動操縦登録を Intune から削除します。</span><span class="sxs-lookup"><span data-stu-id="de7df-239">Delete the Autopilot registration from Intune:</span></span>
    1.  <span data-ttu-id="de7df-240">[ **デバイス登録 > Windows 登録 > デバイス**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="de7df-240">Choose **Device enrollment > Windows enrollment > Devices**.</span></span>
    2. <span data-ttu-id="de7df-241">[Windows 自動操縦デバイス] で、削除するデバイスを選択し、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de7df-241">Under Windows Autopilot devices, choose the devices you want to delete, and then choose **Delete**.</span></span>
3. <span data-ttu-id="de7df-242">Surface 製のイーサネットアダプターを使って、デバイスを有線インターネットに接続します。</span><span class="sxs-lookup"><span data-stu-id="de7df-242">Connect device to wired internet with Surface-branded ethernet adapter.</span></span> <span data-ttu-id="de7df-243">デバイスを再起動して、[UEFI] メニューを開きます (音量を上げるボタンを押したままにして、電源ボタンを押しながら離します)。</span><span class="sxs-lookup"><span data-stu-id="de7df-243">Restart device and open the UEFI menu (press and hold the volume-up button while also pressing and releasing the power button).</span></span>
4. <span data-ttu-id="de7df-244">[ **管理 > ネットワークからの更新 > 構成** ] を選択し、[停止] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="de7df-244">Select **Management > Configure > Refresh from Network** and then choose **Opt-out.**</span></span>

<span data-ttu-id="de7df-245">Intune でデバイスを引き続き管理しますが、DFCI 管理がない場合は、デバイスを自動操縦に登録して、Intune に登録します。</span><span class="sxs-lookup"><span data-stu-id="de7df-245">To keep managing the device with Intune, but without DFCI management, self-register the device to Autopilot and enroll it to Intune.</span></span> <span data-ttu-id="de7df-246">DFCI は、自己登録デバイスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="de7df-246">DFCI will not be applied to self-registered devices.</span></span>

## <span data-ttu-id="de7df-247">詳細情報</span><span class="sxs-lookup"><span data-stu-id="de7df-247">Learn more</span></span>
- <span data-ttu-id="de7df-248">[Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理のアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windows 自動操縦](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span><span class="sxs-lookup"><span data-stu-id="de7df-248">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span></span>
- [<span data-ttu-id="de7df-249">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="de7df-249">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md) 
- [<span data-ttu-id="de7df-250">Microsoft Intune の Windows デバイスで DFCI プロファイルを使用する</span><span class="sxs-lookup"><span data-stu-id="de7df-250">Use DFCI profiles on Windows devices in Microsoft Intune</span></span>](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
