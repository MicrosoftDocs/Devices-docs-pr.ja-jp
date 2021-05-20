---
title: Surface UEFI の設定の Intune 管理
description: この記事では、ターゲットとなる Surface デバイスのファームウェア設定Microsoft Intune管理するために DFCI 環境を構成する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
- Surface Laptop 4
ms.openlocfilehash: b74aeab45dd2354550f0dff712af5b37b853111c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576517"
---
# <a name="intune-management-of-surface-uefi-settings"></a><span data-ttu-id="704ae-103">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="704ae-103">Intune management of Surface UEFI settings</span></span>

## <a name="introduction"></a><span data-ttu-id="704ae-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="704ae-104">Introduction</span></span>

<span data-ttu-id="704ae-105">クラウドからデバイスを管理する機能により、ライフサイクル全体にわたる IT の展開とプロビジョニングが大幅に簡素化されました。</span><span class="sxs-lookup"><span data-stu-id="704ae-105">The ability to manage devices from the cloud has dramatically simplified IT deployment and provisioning across the lifecycle.</span></span> <span data-ttu-id="704ae-106">デバイス ファームウェア構成インターフェイス (DFCI) プロファイルを[Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)に組み込むと、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。</span><span class="sxs-lookup"><span data-stu-id="704ae-106">With Device Firmware Configuration Interface (DFCI) profiles built into [Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="704ae-107">DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を築きます。</span><span class="sxs-lookup"><span data-stu-id="704ae-107">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="704ae-108">よく寄せられる質問に対する回答については [、「Ignite 2019: Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)から Surface UEFI 設定のリモート管理を発表する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="704ae-108">For answers to frequently asked questions, see [Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

### <a name="background"></a><span data-ttu-id="704ae-109">Background</span><span class="sxs-lookup"><span data-stu-id="704ae-109">Background</span></span>

<span data-ttu-id="704ae-110">Surface デバイスは、Windows 10 を実行しているコンピューターと同様に、SoC に格納されているコードを使用して、CPU がハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスできます。</span><span class="sxs-lookup"><span data-stu-id="704ae-110">Like any computer running Windows 10, Surface devices rely on code stored in the SoC that enables the CPU to interface with hard drives, display devices, USB ports, and other devices.</span></span> <span data-ttu-id="704ae-111">この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに格納されているプログラムはソフトウェアと呼ばれています)。</span><span class="sxs-lookup"><span data-stu-id="704ae-111">The programs stored in this read-only memory (ROM) are known as firmware (while programs stored in dynamic media are known as software).</span></span>

<span data-ttu-id="704ae-112">現在市場でWindows 10されている他のデバイスとは対照的に、Surface は、豊富な UEFI 構成設定を使用してファームウェアを構成および管理する機能を IT 管理者に提供します。</span><span class="sxs-lookup"><span data-stu-id="704ae-112">In contrast to other Windows 10 devices available in the market today, Surface provides IT admins with the ability to configure and manage firmware through a rich set of UEFI configuration settings.</span></span> <span data-ttu-id="704ae-113">これにより、モバイル デバイス管理 (MDM) ポリシー、Configuration Manager、またはグループ ポリシーを介して実装されるソフトウェア ベースのポリシー管理の上に、ハードウェア制御の層が提供されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-113">This provides a layer of hardware control on top of software-based policy management as implemented via mobile device management (MDM) policies, Configuration Manager or Group Policy.</span></span> <span data-ttu-id="704ae-114">たとえば、機密情報を含むセキュリティの高い領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することで、カメラの使用を防止できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-114">For example, organizations deploying devices in highly secure areas with sensitive information can prevent camera use by removing functionality at the hardware level.</span></span> <span data-ttu-id="704ae-115">デバイスの観点から、ファームウェア設定を介してカメラをオフに設定すると、カメラを物理的に取り外すのと同じです。</span><span class="sxs-lookup"><span data-stu-id="704ae-115">From a device standpoint, turning the camera off via a firmware setting is equivalent to physically removing the camera.</span></span> <span data-ttu-id="704ae-116">ファームウェア レベルでの管理に関する追加のセキュリティと、オペレーティング システム のソフトウェア設定にのみ依存するセキュリティを比較します。</span><span class="sxs-lookup"><span data-stu-id="704ae-116">Compare the added security of managing at the firmware level to relying only on operating system software settings.</span></span> <span data-ttu-id="704ae-117">たとえば、ドメイン環境でポリシー設定をWindowsオーディオ サービスを無効にした場合でも、ローカル管理者はサービスを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="704ae-117">For example, if you disable the Windows audio service via a policy setting in a domain environment, a local admin could still re-enable the service.</span></span>

### <a name="dfci-versus-semm"></a><span data-ttu-id="704ae-118">DFCI と SEMM の比較</span><span class="sxs-lookup"><span data-stu-id="704ae-118">DFCI versus SEMM</span></span>

<span data-ttu-id="704ae-119">以前は、ファームウェアを管理するには、継続的な手動 IT 集中タスクのオーバーヘッドを利用して、Surface Enterprise 管理モード (SEMM) にデバイスを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-119">Previously, managing firmware required enrolling devices into Surface Enterprise Management Mode (SEMM) with the overhead of ongoing manual IT-intensive tasks.</span></span> <span data-ttu-id="704ae-120">たとえば、SEMM では、証明書管理プロセスの一環として、IT スタッフが各 PC に物理的にアクセスして 2 桁のピンを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-120">As an example, SEMM requires IT staff to physically access each PC to enter a two-digit pin as part of the certificate management process.</span></span> <span data-ttu-id="704ae-121">SEMM は、厳密にオンプレミス環境の組織に対する優れたソリューションですが、複雑で IT の負荷の高い要件により、使用コストが高い状態になります。</span><span class="sxs-lookup"><span data-stu-id="704ae-121">Although SEMM remains a good solution for organizations in a strictly on-premises environment, its complexity and IT-intensive requirements make it costly to use.</span></span>

 <span data-ttu-id="704ae-122">Microsoft Intune に統合された UEFI ファームウェア管理機能を使用すると、ハードウェアをロックダウンする機能が簡素化され、プロビジョニング、セキュリティ、および合理化された更新のための新機能を 1 つのコンソールで簡単かつ簡単に使用できます。現在は Microsoft エンドポイント マネージャー と[統合](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)されています。</span><span class="sxs-lookup"><span data-stu-id="704ae-122">With integrated UEFI firmware management capabilities in Microsoft Intune, the ability to lock down hardware is simplified and easier to use with new features for provisioning, security, and streamlined updating all in a single console, now unified as [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager).</span></span> <span data-ttu-id="704ae-123">次の図は、デバイス (左) で直接表示され、コンソール (右) で表示される UEFI エンドポイント マネージャー示しています。</span><span class="sxs-lookup"><span data-stu-id="704ae-123">The following figure shows UEFI settings viewed directly on the device (left) and viewed in the Endpoint Manager console (right).</span></span>

![デバイス (左) とコンソール (右) に表示エンドポイント マネージャー UEFI 設定](images/uefidfci.png)

<span data-ttu-id="704ae-125">重要な点として、DFCI はゼロ タッチ管理を可能にし、IT 管理者による手動操作の必要性を排除します。</span><span class="sxs-lookup"><span data-stu-id="704ae-125">Crucially, DFCI enables zero touch management, eliminating the need for manual interaction by IT admins.</span></span> <span data-ttu-id="704ae-126">DFCI は、Intune のWindows機能を使用して、自動パイロットを介して展開されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-126">DFCI is deployed via Windows Autopilot using the device profiles capability in Intune.</span></span> <span data-ttu-id="704ae-127">デバイス プロファイルを使用すると、組織の管理に登録されているデバイスに展開できる設定を追加および構成できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-127">A device profile allows you to add and configure settings which can then be deployed to devices enrolled in management within your organization.</span></span> <span data-ttu-id="704ae-128">デバイスがデバイス プロファイルを受信すると、機能と設定が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-128">Once the device receives the device profile, the features and settings are applied automatically.</span></span> <span data-ttu-id="704ae-129">一般的なデバイス プロファイルの例としては、メール、デバイス制限、VPN、Wi-Fi、管理用テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="704ae-129">Examples of common device profiles include Email, Device restrictions, VPN, Wi-Fi, and Administrative templates.</span></span> <span data-ttu-id="704ae-130">DFCI は、単に追加のデバイス プロファイルで、オンプレミスインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-130">DFCI is simply an additional device profile that enables you to manage UEFI configuration settings from the cloud without having to maintain on-premises infrastructure.</span></span>  

## <a name="supported-devices"></a><span data-ttu-id="704ae-131">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="704ae-131">Supported devices</span></span>

<span data-ttu-id="704ae-132">DFCI は、次のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="704ae-132">DFCI is supported in the following devices:</span></span>

- <span data-ttu-id="704ae-133">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="704ae-133">Surface Pro 7+</span></span>
- <span data-ttu-id="704ae-134">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="704ae-134">Surface Pro 7</span></span>
- <span data-ttu-id="704ae-135">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="704ae-135">Surface Pro X</span></span>
- <span data-ttu-id="704ae-136">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="704ae-136">Surface Laptop 3</span></span>
- <span data-ttu-id="704ae-137">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="704ae-137">Surface Book 3</span></span>
- <span data-ttu-id="704ae-138">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="704ae-138">Surface Laptop Go</span></span>
- <span data-ttu-id="704ae-139">Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="704ae-139">Surface Laptop 4</span></span>

> [!NOTE]
> <span data-ttu-id="704ae-140">Surface ProX は、組み込みのカメラ、オーディオ、および Wi-Fi/Bluetooth の DFCI 設定管理をサポートBluetooth。</span><span class="sxs-lookup"><span data-stu-id="704ae-140">Surface Pro X does not support DFCI settings management for built-in camera, audio, and Wi-Fi/Bluetooth.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="704ae-141">前提条件</span><span class="sxs-lookup"><span data-stu-id="704ae-141">Prerequisites</span></span>

- <span data-ttu-id="704ae-142">デバイスは、CSP (CSP) パートナー Windows OEM ディストリビューターによって[、Microsoft クラウド ソリューション プロバイダー Autopilot](https://partner.microsoft.com/membership/cloud-solution-provider)に登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-142">Devices must be registered with Windows Autopilot by a [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/membership/cloud-solution-provider) or OEM distributor.</span></span>

- <span data-ttu-id="704ae-143">SURFACE 用の DFCI を構成する前に、Microsoft Intune および Azure Active Directory [](https://docs.microsoft.com/intune/) [(Azure](https://docs.microsoft.com/azure/active-directory/) AD) のオートパイロット構成要件に精通している必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-143">Before configuring DFCI for Surface, you should be familiar with Autopilot configuration requirements in  [Microsoft Intune](https://docs.microsoft.com/intune/) and [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="704ae-144">始める前に</span><span class="sxs-lookup"><span data-stu-id="704ae-144">Before you begin</span></span>

<span data-ttu-id="704ae-145">対象の Surface デバイスを Azure ADに追加します。</span><span class="sxs-lookup"><span data-stu-id="704ae-145">Add your target Surface devices to an Azure AD security group.</span></span> <span data-ttu-id="704ae-146">セキュリティ グループの作成と管理の詳細については、「Intune のドキュメント」 [を参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。</span><span class="sxs-lookup"><span data-stu-id="704ae-146">For more information about creating and managing security groups, refer to [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups).</span></span>

## <a name="configure-dfci-management-for-surface-devices"></a><span data-ttu-id="704ae-147">Surface デバイスの DFCI 管理を構成する</span><span class="sxs-lookup"><span data-stu-id="704ae-147">Configure DFCI management for Surface devices</span></span>

<span data-ttu-id="704ae-148">DFCI 環境では、設定を含む DFCI プロファイルと、登録済みデバイスに設定を適用する自動パイロット プロファイルを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-148">A DFCI environment requires setting up a DFCI profile that contains  the settings and an Autopilot profile to apply the settings to registered devices.</span></span> <span data-ttu-id="704ae-149">ユーザーが最初にデバイスを起動するときに、OOBE セットアップ中に設定がプッシュダウンされるのを確認するには、登録状態プロファイルも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-149">An enrollment status profile is also recommended to ensure settings are pushed down during OOBE setup when users first start the device.</span></span> <span data-ttu-id="704ae-150">このガイドでは、DFCI 環境を構成し、対象となる Surface デバイスの UEFI 構成設定を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="704ae-150">This guide explains how to configure the DFCI environment and manage UEFI configuration settings for targeted Surface devices.</span></span>

## <a name="create-dfci-profile"></a><span data-ttu-id="704ae-151">DFCI プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="704ae-151">Create DFCI profile</span></span>

<span data-ttu-id="704ae-152">DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-152">Before configuring DFCI policy settings, first create a DFCI profile and assign it to the Azure AD security group that contains your target devices.</span></span>

1. <span data-ttu-id="704ae-153">テナントにサインイン devicemanagement.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="704ae-153">Sign into your tenant at  devicemanagement.microsoft.com.</span></span>
2. <span data-ttu-id="704ae-154">[管理センター Microsoft エンドポイント マネージャーで、[デバイスと構成プロファイル>プロファイル>作成] を選択し **、名前**を入力します。たとえば **、DFCI 構成ポリシーです。**</span><span class="sxs-lookup"><span data-stu-id="704ae-154">In the Microsoft Endpoint Manager Admin Center, select **Devices > Configuration profiles > Create profile** and enter a name; for example, **DFCI Configuration Policy.**</span></span>
3. <span data-ttu-id="704ae-155">プラットフォームの**Windows 10を選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-155">Select **Windows 10 and later** for platform type.</span></span>
4. <span data-ttu-id="704ae-156">[プロファイルの種類] ドロップダウン リストで、[デバイス ファームウェア **構成** インターフェイス] を選択して、使用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="704ae-156">In the Profile type drop down list, select **Device Firmware Configuration Interface** to open the DFCI blade containing all available policy settings.</span></span> <span data-ttu-id="704ae-157">DFCI 設定の詳細については、このページの表 1 または Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。</span><span class="sxs-lookup"><span data-stu-id="704ae-157">For information on DFCI settings, refer to Table 1 on this page or the [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span> <span data-ttu-id="704ae-158">初期セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-158">You can configure DFCI settings during the initial setup process or later by editing the DFCI profile.</span></span>

    ![DFCI プロファイルの作成](images/df1.png)

5. <span data-ttu-id="704ae-160">**[OK] をクリック**し、[作成]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-160">Click **OK** and then select **Create**.</span></span>
6. <span data-ttu-id="704ae-161">[**割り当て**] を選択し、[グループの選択] で、次の図に示すようにADデバイスを含む Azure AD セキュリティ グループを選択します。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="704ae-161">Select **Assignments** and under **Select groups to include** select the Azure AD security group that contains your target devices, as shown in the following figure.</span></span> <span data-ttu-id="704ae-162">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="704ae-162">Click **Save**.</span></span>

    ![セキュリティ グループの割り当て](images/df2a.png)

## <a name="create-autopilot-profile"></a><span data-ttu-id="704ae-164">自動パイロット プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="704ae-164">Create Autopilot profile</span></span>

1. <span data-ttu-id="704ae-165">[エンドポイント マネージャーで devicemanagement.microsoft.com 登録するデバイス> Windows**選択**し、[展開プロファイル] まで下**にスクロールします**。</span><span class="sxs-lookup"><span data-stu-id="704ae-165">In Endpoint Manager at  devicemanagement.microsoft.com, select **devices > Windows enrollment** and scroll down to **Deployment profiles**.</span></span>
2. <span data-ttu-id="704ae-166">[プロファイル **の作成] を** 選択し、名前を入力します。たとえば、[マイ オート **パイロット プロファイル] を選択し、[** 次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-166">Select **Create profile** and enter a name; for example, **My Autopilot profile**, and select **Next**.</span></span>
3. <span data-ttu-id="704ae-167">次の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="704ae-167">Select the following settings:</span></span>

    - <span data-ttu-id="704ae-168">展開モード: **User-Driven .**</span><span class="sxs-lookup"><span data-stu-id="704ae-168">Deployment mode: **User-Driven**.</span></span>
    - <span data-ttu-id="704ae-169">参加の種類: Azure **AD参加しています**。</span><span class="sxs-lookup"><span data-stu-id="704ae-169">Join type: Azure **AD joined**.</span></span>

4. <span data-ttu-id="704ae-170">次の図に示すように、残りの既定の設定はそのままにし、[ **次**へ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="704ae-170">Leave the remaining default settings unchanged and select **Next**, as shown in the following figure.</span></span>

    ![自動パイロット プロファイルの作成](images/df3b.png)

5. <span data-ttu-id="704ae-172">[割り当て] ページで、[含めるグループの選択] を **選択** し、Azure セキュリティ グループADクリックします。</span><span class="sxs-lookup"><span data-stu-id="704ae-172">On the Assignments page, choose **Select groups to include** and click your Azure AD security group.</span></span> <span data-ttu-id="704ae-173">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="704ae-173">Select **Next**.</span></span>
6. <span data-ttu-id="704ae-174">概要を受け入れ、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-174">Accept the summary and then select **Create**.</span></span> <span data-ttu-id="704ae-175">自動パイロット プロファイルが作成され、グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="704ae-175">The Autopilot profile is now created and assigned to the group.</span></span>

## <a name="configure-enrollment-status-page"></a><span data-ttu-id="704ae-176">[登録状態の構成] ページ</span><span class="sxs-lookup"><span data-stu-id="704ae-176">Configure Enrollment Status Page</span></span>

<span data-ttu-id="704ae-177">ユーザーがサインインする前に、OOBE 中にデバイスが DFCI 構成を適用するには、登録状態を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-177">To ensure that devices apply the DFCI configuration during OOBE before users sign in, you need to configure enrollment status.</span></span>

<span data-ttu-id="704ae-178">詳細については、「登録状態ページの [設定」を参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。</span><span class="sxs-lookup"><span data-stu-id="704ae-178">For more information, refer to [Set up an enrollment status page](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status).</span></span>


## <a name="configure-dfci-settings-on-surface-devices"></a><span data-ttu-id="704ae-179">Surface デバイスで DFCI 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="704ae-179">Configure DFCI settings on Surface devices</span></span>

<span data-ttu-id="704ae-180">DFCI には、ハードウェア レベルでデバイスをロックダウンすることで、より高いレベルのセキュリティを提供する UEFI 構成ポリシーの合理化されたセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="704ae-180">DFCI includes a streamlined set of UEFI configuration policies that provide an extra level of security by locking down devices at the hardware level.</span></span> <span data-ttu-id="704ae-181">DFCI は、ソフトウェア レベルでのモバイル デバイス管理設定と組み合わせて使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="704ae-181">DFCI is designed to be used in conjunction with mobile device management settings at the software level.</span></span> <span data-ttu-id="704ae-182">DFCI 設定は Surface デバイスに組み込みのハードウェア コンポーネントにのみ影響し、USB Web カメラなどの接続された周辺機器には適用されません。</span><span class="sxs-lookup"><span data-stu-id="704ae-182">Note that DFCI settings only affect hardware components built into Surface devices and do not extend to attached peripherals such as USB webcams.</span></span> <span data-ttu-id="704ae-183">(ただし、Intune でデバイス制限ポリシーを使用して、ソフトウェア レベルで接続されている周辺機器へのアクセスをオフにできます)。</span><span class="sxs-lookup"><span data-stu-id="704ae-183">(However, you can use Device restriction policies in Intune to turn off access to attached peripherals at the software level).</span></span>

<span data-ttu-id="704ae-184">DFCI ポリシー設定を構成するには、次の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="704ae-184">You configure DFCI policy settings by editing the DFCI profile from Endpoint Manager, as shown in the figure below.</span></span> 

- <span data-ttu-id="704ae-185">[エンドポイント マネージャー] devicemanagement.microsoft.com で、[デバイス] > Windows >構成プロファイル> **"DFCI**プロファイル名" >を選択> 設定。</span><span class="sxs-lookup"><span data-stu-id="704ae-185">In Endpoint Manager at  devicemanagement.microsoft.com, select **Devices > Windows > Configuration Profiles > “DFCI profile name” > Properties > Settings**.</span></span>

    ![DFCI 設定の構成](images/dfciconfig.png)

### <a name="block-user-access-to-uefi-settings"></a><span data-ttu-id="704ae-187">UEFI 設定へのユーザー アクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="704ae-187">Block user access to UEFI settings</span></span>

<span data-ttu-id="704ae-188">多くのお客様にとって、ユーザーが UEFI 設定を変更することをブロックする機能は非常に重要であり、DFCI を使用する主な理由です。</span><span class="sxs-lookup"><span data-stu-id="704ae-188">For many customers, the ability to block users from changing UEFI settings is critically important and a primary reason to use DFCI.</span></span> <span data-ttu-id="704ae-189">表 1 に示す通り、これは [ローカル ユーザーによる UEFI 設定の変更を許可する] の設定 **を使用して管理されます**。</span><span class="sxs-lookup"><span data-stu-id="704ae-189">As listed in Table 1, this is managed via the setting **Allow local user to change UEFI settings**.</span></span> <span data-ttu-id="704ae-190">この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-190">If you do not edit or configure this setting, local users will be able to change any UEFI setting not managed by Intune.</span></span> <span data-ttu-id="704ae-191">そのため、ローカル ユーザーによる UEFI 設定の変更を許可するを無効 **にすることを強くお勧めします。**</span><span class="sxs-lookup"><span data-stu-id="704ae-191">Therefore, it’s highly recommended to disable **Allow local user to change UEFI settings.**</span></span>
<span data-ttu-id="704ae-192">残りの DFCI 設定を使用すると、ユーザーが利用できる機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="704ae-192">The rest of the DFCI settings enable you to turn off functionality that would otherwise be available to users.</span></span> <span data-ttu-id="704ae-193">たとえば、セキュリティが高い領域で機密情報を保護する必要がある場合は、カメラを無効にし、ユーザーが USB ドライブから起動しない場合は、その情報も無効にできます。</span><span class="sxs-lookup"><span data-stu-id="704ae-193">For example, if you need to protect sensitive information in highly secure areas, you can disable the camera, and if you don’t want users booting from USB drives, you can disable that also.</span></span>

### <a name="table-1-dfci-scenarios"></a><span data-ttu-id="704ae-194">表 1.</span><span class="sxs-lookup"><span data-stu-id="704ae-194">Table 1.</span></span> <span data-ttu-id="704ae-195">DFCI のシナリオ</span><span class="sxs-lookup"><span data-stu-id="704ae-195">DFCI scenarios</span></span>

| <span data-ttu-id="704ae-196">デバイス管理の目標</span><span class="sxs-lookup"><span data-stu-id="704ae-196">Device management goal</span></span>                        | <span data-ttu-id="704ae-197">構成手順</span><span class="sxs-lookup"><span data-stu-id="704ae-197">Configuration steps</span></span>                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="704ae-198">ローカル ユーザーが UEFI 設定を変更することをブロックする</span><span class="sxs-lookup"><span data-stu-id="704ae-198">Block local users from changing UEFI settings</span></span> | <span data-ttu-id="704ae-199">[ **セキュリティ機能] >ローカル**ユーザーによる UEFI 設定の変更を許可する] で、[なし] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-199">Under **Security Features > Allow local user to change UEFI settings**, select **None**.</span></span>              |
| <span data-ttu-id="704ae-200">カメラを無効にする</span><span class="sxs-lookup"><span data-stu-id="704ae-200">Disable cameras</span></span>                               | <span data-ttu-id="704ae-201">[ **ハードウェア カメラに組み込>で、[無効**] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-201">Under **Built in Hardware > Cameras**, select **Disabled**.</span></span>                                       |
| <span data-ttu-id="704ae-202">マイクとスピーカーを無効にする</span><span class="sxs-lookup"><span data-stu-id="704ae-202">Disable Microphones and speakers</span></span>              | <span data-ttu-id="704ae-203">[ **ハードウェアに組み込>マイクとスピーカー]** で、[無効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-203">Under **Built in Hardware > Microphones and speakers**, select **Disabled**.</span></span>                      |
| <span data-ttu-id="704ae-204">無線を無効にする (Bluetooth Wi-Fi)</span><span class="sxs-lookup"><span data-stu-id="704ae-204">Disable radios (Bluetooth, Wi-Fi)</span></span>             | <span data-ttu-id="704ae-205">[**ハードウェア に組み込> (Bluetooth、Wi-Fi**など) で、[無効] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-205">Under **Built in Hardware > Radios (Bluetooth, Wi-Fi, etc…)**, select **Disabled**.</span></span>                   |
| <span data-ttu-id="704ae-206">外部メディアからのブートを無効にする (USB、SD)</span><span class="sxs-lookup"><span data-stu-id="704ae-206">Disable Boot from external media (USB, SD)</span></span>    | <span data-ttu-id="704ae-207">[ **組み込みのハードウェア > ブート オプション>外部メディア (USB、SD)** から起動する] で、[無効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-207">Under **Built in Hardware > Boot Options > Boot from external media (USB, SD)**, select **Disabled**.</span></span> |

> [!CAUTION]
> <span data-ttu-id="704ae-208">無線**を無効にする (Bluetooth Wi-Fi)** 設定は、有線イーサネット接続を持つデバイスでのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-208">The **Disable radios (Bluetooth, Wi-Fi)** setting should only be used on devices that have a wired Ethernet connection.</span></span>
 
> [!NOTE]
>  <span data-ttu-id="704ae-209">Intune の DFCI には、現在 Surface デバイスには適用されない 2 つの設定が含まれています。(1) CPU と IO の仮想化と (2) ネットワーク アダプターからのブートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="704ae-209">DFCI in Intune includes two settings that do not currently apply to Surface devices: (1) CPU and IO virtualization and (2) Disable Boot from network adapters.</span></span>
 
<span data-ttu-id="704ae-210">Intune には、管理権限を委任するためのスコープ タグと、デバイスの種類を管理するための適用ルールが提供されています。</span><span class="sxs-lookup"><span data-stu-id="704ae-210">Intune provides Scope tags to delegate administrative rights and Applicability Rules to manage device types.</span></span> <span data-ttu-id="704ae-211">ポリシー管理のサポートとすべての DFCI 設定の詳細については、次のドキュメント[を](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)参照Microsoft Intuneしてください。</span><span class="sxs-lookup"><span data-stu-id="704ae-211">For more information about policy management support and full details on all DFCI settings, refer to [Microsoft Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span>

## <a name="register-devices-in-autopilot"></a><span data-ttu-id="704ae-212">Autopilot にデバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="704ae-212">Register devices in Autopilot</span></span>

<span data-ttu-id="704ae-213">上記のように、DFCI はリセラーまたはディストリビューターによって Windows Autopilot に登録されているデバイスにのみ適用され、Surface Pro 7+、Surface Laptop Go、Surface Pro 7、Surface Pro X、および Surface Laptop 3 でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="704ae-213">As stated above, DFCI can only be applied on devices registered in Windows Autopilot by your reseller or distributor and is only supported on Surface Pro 7+, Surface Laptop Go, Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="704ae-214">セキュリティ上の理由から、デバイスを自動パイロットに "自己プロビジョニング" できません。</span><span class="sxs-lookup"><span data-stu-id="704ae-214">For security reasons, it’s not possible to “self-provision” your devices into Autopilot.</span></span> <span data-ttu-id="704ae-215">詳細については、「Surface [Registration Support for Windows」を参照してください](surface-autopilot-registration-support.md)。</span><span class="sxs-lookup"><span data-stu-id="704ae-215">To learn more, see Surface [Registration Support for Windows Autopilot](surface-autopilot-registration-support.md).</span></span> 

## <a name="manually-sync-autopilot-devices"></a><span data-ttu-id="704ae-216">自動パイロット デバイスを手動で同期する</span><span class="sxs-lookup"><span data-stu-id="704ae-216">Manually Sync Autopilot devices</span></span>

<span data-ttu-id="704ae-217">Intune ポリシー設定は通常、ほぼ即座に適用されます。対象のデバイスで設定が有効になるまで、10 分の遅延が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-217">Although Intune policy settings typically get applied almost immediately, there may be a delay of 10 minutes before the settings take effect on targeted devices.</span></span> <span data-ttu-id="704ae-218">まれな状況では、最大 8 時間の遅延が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="704ae-218">In rare circumstances, delays of up to 8 hours are possible.</span></span> <span data-ttu-id="704ae-219">設定ができるだけ早く適用される (テスト シナリオなど) には、ターゲット デバイスを手動で同期できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-219">To ensure settings apply as soon as possible, (such as in test scenarios), you can manually sync the target devices.</span></span>

- <span data-ttu-id="704ae-220">[エンドポイント マネージャーで devicemanagement.microsoft.com に移動し、[デバイスの登録\*\*\*\*>自動パイロット デバイス> Windowsに> Windows同期] を選択**します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-220">In Endpoint Manager at  devicemanagement.microsoft.com, go to **Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.</span></span>

 <span data-ttu-id="704ae-221">詳細については、「デバイスを手動で[同期するWindows参照してください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。</span><span class="sxs-lookup"><span data-stu-id="704ae-221">For more information, refer to [Sync your Windows device manually](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).</span></span>

> [!NOTE]
> <span data-ttu-id="704ae-222">UEFI で設定を直接調整する場合は、デバイスが標準のユーザー ログインに完全に再起動Windowsがあります。</span><span class="sxs-lookup"><span data-stu-id="704ae-222">When adjusting settings directly in UEFI, you need to ensure the device fully restarts to the standard Windows login.</span></span>

## <a name="verifying-uefi-settings-on-dfci-managed-devices"></a><span data-ttu-id="704ae-223">DFCI 管理デバイスでの UEFI 設定の確認</span><span class="sxs-lookup"><span data-stu-id="704ae-223">Verifying UEFI settings on DFCI-managed devices</span></span>

<span data-ttu-id="704ae-224">テスト環境では、Surface UEFI インターフェイスで設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-224">In a test environment, you can verify settings in the Surface UEFI interface.</span></span>

1. <span data-ttu-id="704ae-225">Surface UEFI を開きます。ボリューム **+** ボタンと **電源** ボタンを同時に押します。</span><span class="sxs-lookup"><span data-stu-id="704ae-225">Open Surface UEFI, which involves pressing the **Volume +** and **Power** buttons at the same time.</span></span>
2. <span data-ttu-id="704ae-226">[デバイス **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-226">Select **Devices**.</span></span> <span data-ttu-id="704ae-227">次の図に示すように、UEFI メニューには構成済みの設定が反映されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-227">The UEFI menu will reflect configured settings, as shown in the following figure.</span></span>

    ![Surface UEFI](images/df3.png)

    <span data-ttu-id="704ae-229">次の方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="704ae-229">Note how:</span></span>

      - <span data-ttu-id="704ae-230">ローカル ユーザーによる **UEFI** 設定の変更を許可する設定が [なし] に設定されている場合、設定はグレー表示されます。</span><span class="sxs-lookup"><span data-stu-id="704ae-230">The settings are greyed out because **Allow local user to change UEFI setting** is set to None.</span></span>
      - <span data-ttu-id="704ae-231">マイクとスピーカーが [無効] に設定されている場合、オーディオ**はオフに\*\*\*\*設定されます**。</span><span class="sxs-lookup"><span data-stu-id="704ae-231">Audio is set to off because **Microphones and speakers** are set to **Disabled**.</span></span>

## <a name="removing-dfci-policy-settings"></a><span data-ttu-id="704ae-232">DFCI ポリシー設定の削除</span><span class="sxs-lookup"><span data-stu-id="704ae-232">Removing DFCI policy settings</span></span>

<span data-ttu-id="704ae-233">DFCI プロファイルを作成すると、構成された設定はすべて、プロファイルの管理範囲内のすべてのデバイスで有効になります。</span><span class="sxs-lookup"><span data-stu-id="704ae-233">When you create a DFCI profile, all configured settings will remain in effect across all devices within the profile’s scope of management.</span></span> <span data-ttu-id="704ae-234">DFCI ポリシー設定は、DFCI プロファイルを直接編集することでのみ削除できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-234">You can only remove DFCI policy settings by editing the DFCI profile directly.</span></span>

<span data-ttu-id="704ae-235">元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="704ae-235">If the original DFCI profile has been deleted, you can remove policy settings by creating a new profile and then editing the settings, as appropriate.</span></span>

## <a name="removing-dfci-management"></a><span data-ttu-id="704ae-236">DFCI 管理の削除</span><span class="sxs-lookup"><span data-stu-id="704ae-236">Removing DFCI management</span></span>

**<span data-ttu-id="704ae-237">DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻す方法:</span><span class="sxs-lookup"><span data-stu-id="704ae-237">To remove DFCI management and return device to factory new state:</span></span>**

1. <span data-ttu-id="704ae-238">Intune からデバイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="704ae-238">Retire the device from Intune:</span></span>
    1. <span data-ttu-id="704ae-239">[エンドポイント マネージャー] で devicemanagement.microsoft.com[グループ]**を選択>すべてのデバイスを選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-239">In Endpoint Manager at  devicemanagement.microsoft.com, choose **Groups > All Devices**.</span></span> <span data-ttu-id="704ae-240">廃止するデバイスを選択し、[引退/ワイプ **] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="704ae-240">Select the devices you want to retire, and then choose **Retire/Wipe.**</span></span> <span data-ttu-id="704ae-241">詳細については、「デバイスのワイプ、削除、または手動での登録解除を使用してデバイスを削除する」 [を参照してください](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。</span><span class="sxs-lookup"><span data-stu-id="704ae-241">To learn more refer to [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/remote-actions/devices-wipe).</span></span> 
2. <span data-ttu-id="704ae-242">Intune から自動パイロット登録を削除します。</span><span class="sxs-lookup"><span data-stu-id="704ae-242">Delete the Autopilot registration from Intune:</span></span>
    1.  <span data-ttu-id="704ae-243">[**デバイスの登録] > Windows [デバイス>選択します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-243">Choose **Device enrollment > Windows enrollment > Devices**.</span></span>
    2. <span data-ttu-id="704ae-244">[Windows] で、削除するデバイスを選択し、[削除] を選択**します**。</span><span class="sxs-lookup"><span data-stu-id="704ae-244">Under Windows Autopilot devices, choose the devices you want to delete, and then choose **Delete**.</span></span>
3. <span data-ttu-id="704ae-245">Connectブランドのイーサネット アダプターを使用して、デバイスを有線インターネットに接続します。</span><span class="sxs-lookup"><span data-stu-id="704ae-245">Connect device to wired internet with Surface-branded ethernet adapter.</span></span> <span data-ttu-id="704ae-246">デバイスを再起動し、UEFI メニューを開きます (音量アップ ボタンを長押ししながら、電源ボタンを長押しします)。</span><span class="sxs-lookup"><span data-stu-id="704ae-246">Restart device and open the UEFI menu (press and hold the volume-up button while also pressing and releasing the power button).</span></span>
4. <span data-ttu-id="704ae-247">[ **管理] > [ネットワーク>更新の構成] を選択し** 、[オプトアウト] **を選択します。**</span><span class="sxs-lookup"><span data-stu-id="704ae-247">Select **Management > Configure > Refresh from Network** and then choose **Opt-out.**</span></span>

<span data-ttu-id="704ae-248">Intune でデバイスを管理し続けるが、DFCI 管理を行わずに、デバイスを自動パイロットに自己登録し、Intune に登録します。</span><span class="sxs-lookup"><span data-stu-id="704ae-248">To keep managing the device with Intune, but without DFCI management, self-register the device to Autopilot and enroll it to Intune.</span></span> <span data-ttu-id="704ae-249">DFCI は自己登録デバイスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="704ae-249">DFCI will not be applied to self-registered devices.</span></span>

## <a name="learn-more"></a><span data-ttu-id="704ae-250">詳細情報</span><span class="sxs-lookup"><span data-stu-id="704ae-250">Learn more</span></span>
- <span data-ttu-id="704ae-251">[Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発表する](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windowsオートパイロット](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span><span class="sxs-lookup"><span data-stu-id="704ae-251">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span></span>
- [<span data-ttu-id="704ae-252">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="704ae-252">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md) 
- [<span data-ttu-id="704ae-253">デバイス内のデバイスで DFCI プロファイルWindows使用Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="704ae-253">Use DFCI profiles on Windows devices in Microsoft Intune</span></span>](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
