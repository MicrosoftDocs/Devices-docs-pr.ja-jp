---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成し、対象となる Surface デバイスのファームウェア設定を管理する方法について説明します。
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
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
ms.openlocfilehash: dde34126c726ec0ac8093a665804c4fb0f639e3e
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271571"
---
# <span data-ttu-id="358bd-103">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="358bd-103">Intune management of Surface UEFI settings</span></span>

## <span data-ttu-id="358bd-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="358bd-104">Introduction</span></span>

<span data-ttu-id="358bd-105">クラウドからデバイスを管理する機能により、ライフサイクル全体にわたって IT の展開とプロビジョニングが大幅に簡素化されました。</span><span class="sxs-lookup"><span data-stu-id="358bd-105">The ability to manage devices from the cloud has dramatically simplified IT deployment and provisioning across the lifecycle.</span></span> <span data-ttu-id="358bd-106">[Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)に組み込みのデバイス ファームウェア構成インターフェイス (DFCI) プロファイルにより、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。</span><span class="sxs-lookup"><span data-stu-id="358bd-106">With Device Firmware Configuration Interface (DFCI) profiles built into [Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="358bd-107">DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を構築します。</span><span class="sxs-lookup"><span data-stu-id="358bd-107">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="358bd-108">よく寄せられる質問への回答については [、「Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358bd-108">For answers to frequently asked questions, see [Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

### <span data-ttu-id="358bd-109">Background</span><span class="sxs-lookup"><span data-stu-id="358bd-109">Background</span></span>

<span data-ttu-id="358bd-110">Windows 10 を実行している他のコンピューターと同様に、Surface デバイスは SoC に格納されているコードを利用して、CPU がハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスできます。</span><span class="sxs-lookup"><span data-stu-id="358bd-110">Like any computer running Windows 10, Surface devices rely on code stored in the SoC that enables the CPU to interface with hard drives, display devices, USB ports, and other devices.</span></span> <span data-ttu-id="358bd-111">この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに保存されているプログラムはソフトウェアと呼ばれています)。</span><span class="sxs-lookup"><span data-stu-id="358bd-111">The programs stored in this read-only memory (ROM) are known as firmware (while programs stored in dynamic media are known as software).</span></span>

<span data-ttu-id="358bd-112">現在、市場で利用可能な他の Windows 10 デバイスとは対照的に、Surface は、豊富な UEFI 構成設定を通じてファームウェアを構成および管理する機能を IT 管理者に提供します。</span><span class="sxs-lookup"><span data-stu-id="358bd-112">In contrast to other Windows 10 devices available in the market today, Surface provides IT admins with the ability to configure and manage firmware through a rich set of UEFI configuration settings.</span></span> <span data-ttu-id="358bd-113">これにより、モバイル デバイス管理 (MDM) ポリシー、Configuration Manager、またはグループ ポリシーを通じて実装されるソフトウェア ベースのポリシー管理の上にハードウェア制御のレイヤーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-113">This provides a layer of hardware control on top of software-based policy management as implemented via mobile device management (MDM) policies, Configuration Manager or Group Policy.</span></span> <span data-ttu-id="358bd-114">たとえば、機密性の高い情報を持つ高度なセキュリティ領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することでカメラの使用を防止できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-114">For example, organizations deploying devices in highly secure areas with sensitive information can prevent camera use by removing functionality at the hardware level.</span></span> <span data-ttu-id="358bd-115">デバイスの観点から、ファームウェア設定でカメラをオフにした場合は、カメラを物理的に取り外すのと同じです。</span><span class="sxs-lookup"><span data-stu-id="358bd-115">From a device standpoint, turning the camera off via a firmware setting is equivalent to physically removing the camera.</span></span> <span data-ttu-id="358bd-116">ファームウェア レベルでの管理に関する追加のセキュリティと、オペレーティング システムのソフトウェア設定にのみ依存するセキュリティを比較します。</span><span class="sxs-lookup"><span data-stu-id="358bd-116">Compare the added security of managing at the firmware level to relying only on operating system software settings.</span></span> <span data-ttu-id="358bd-117">たとえば、ドメイン環境のポリシー設定を使用して Windows オーディオ サービスを無効にした場合でも、ローカル管理者はサービスを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="358bd-117">For example, if you disable the Windows audio service via a policy setting in a domain environment, a local admin could still re-enable the service.</span></span>

### <span data-ttu-id="358bd-118">DFCI と SEMM の比較</span><span class="sxs-lookup"><span data-stu-id="358bd-118">DFCI versus SEMM</span></span>

<span data-ttu-id="358bd-119">以前は、ファームウェアを管理するには、進行中の手動 IT 集中型タスクのオーバーヘッドを利用して、デバイスを Surface Enterprise Management Mode (SEMM) に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-119">Previously, managing firmware required enrolling devices into Surface Enterprise Management Mode (SEMM) with the overhead of ongoing manual IT-intensive tasks.</span></span> <span data-ttu-id="358bd-120">たとえば、SEMM では、証明書管理プロセスの一環として、IT スタッフが各 PC に物理的にアクセスして 2 桁のピンを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-120">As an example, SEMM requires IT staff to physically access each PC to enter a two-digit pin as part of the certificate management process.</span></span> <span data-ttu-id="358bd-121">SEMM は厳密にオンプレミス環境の組織に対する優れたソリューションであり続けますが、複雑性と IT 負荷の高い要件により、使用にコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="358bd-121">Although SEMM remains a good solution for organizations in a strictly on-premises environment, its complexity and IT-intensive requirements make it costly to use.</span></span>

 <span data-ttu-id="358bd-122">Microsoft Intune に統合された UEFI ファームウェア管理機能により、ハードウェアをロックダウンする機能が簡素化され、プロビジョニング、セキュリティ、および合理化された更新のための新機能を 1 つのコンソールで簡単に使用できます。Microsoft [Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)として統合されました。</span><span class="sxs-lookup"><span data-stu-id="358bd-122">With integrated UEFI firmware management capabilities in Microsoft Intune, the ability to lock down hardware is simplified and easier to use with new features for provisioning, security, and streamlined updating all in a single console, now unified as [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager).</span></span> <span data-ttu-id="358bd-123">次の図は、デバイスで直接表示され (左)、エンドポイント マネージャー コンソール (右) で表示される UEFI 設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="358bd-123">The following figure shows UEFI settings viewed directly on the device (left) and viewed in the Endpoint Manager console (right).</span></span>

![デバイス (左側) とエンドポイント マネージャー コンソール (右) に表示される UEFI 設定](images/uefidfci.png)

<span data-ttu-id="358bd-125">非常に重要な点として、DFCI ではタッチ管理が不要で、IT 管理者による手動操作の必要性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="358bd-125">Crucially, DFCI enables zero touch management, eliminating the need for manual interaction by IT admins.</span></span> <span data-ttu-id="358bd-126">DFCI は、Intune のデバイス プロファイル機能を使用して Windows Autopilot 経由で展開されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-126">DFCI is deployed via Windows Autopilot using the device profiles capability in Intune.</span></span> <span data-ttu-id="358bd-127">デバイス プロファイルを使用すると、組織内の管理に登録されているデバイスに展開できる設定を追加および構成できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-127">A device profile allows you to add and configure settings which can then be deployed to devices enrolled in management within your organization.</span></span> <span data-ttu-id="358bd-128">デバイスがデバイス プロファイルを受信すると、機能と設定が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-128">Once the device receives the device profile, the features and settings are applied automatically.</span></span> <span data-ttu-id="358bd-129">一般的なデバイス プロファイルの例には、メール、デバイスの制限、VPN、Wi-Fi、管理用テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="358bd-129">Examples of common device profiles include Email, Device restrictions, VPN, Wi-Fi, and Administrative templates.</span></span> <span data-ttu-id="358bd-130">DFCI は、単に追加のデバイス プロファイルで、オンプレミスのインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-130">DFCI is simply an additional device profile that enables you to manage UEFI configuration settings from the cloud without having to maintain on-premises infrastructure.</span></span>  

## <span data-ttu-id="358bd-131">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="358bd-131">Supported devices</span></span>

<span data-ttu-id="358bd-132">DFCI は、次のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="358bd-132">DFCI is supported in the following devices:</span></span>

- <span data-ttu-id="358bd-133">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="358bd-133">Surface Pro 7+</span></span>
- <span data-ttu-id="358bd-134">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="358bd-134">Surface Pro 7</span></span>
- <span data-ttu-id="358bd-135">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="358bd-135">Surface Pro X</span></span>
- <span data-ttu-id="358bd-136">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="358bd-136">Surface Laptop 3</span></span>
- <span data-ttu-id="358bd-137">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="358bd-137">Surface Book 3</span></span>
- <span data-ttu-id="358bd-138">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="358bd-138">Surface Laptop Go</span></span>

> [!NOTE]
> <span data-ttu-id="358bd-139">Surface Pro X は、組み込みのカメラ、オーディオ、Wi-Fi/Bluetooth の DFCI 設定管理をサポートBluetooth。</span><span class="sxs-lookup"><span data-stu-id="358bd-139">Surface Pro X does not support DFCI settings management for built-in camera, audio, and Wi-Fi/Bluetooth.</span></span>

## <span data-ttu-id="358bd-140">前提条件</span><span class="sxs-lookup"><span data-stu-id="358bd-140">Prerequisites</span></span>

- <span data-ttu-id="358bd-141">デバイスは、Microsoft クラウド ソリューション プロバイダー [(CSP)](https://partner.microsoft.com/membership/cloud-solution-provider) パートナーまたは OEM ディストリビューターによって Windows Autopilot に登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-141">Devices must be registered with Windows Autopilot by a [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/membership/cloud-solution-provider) or OEM distributor.</span></span>

- <span data-ttu-id="358bd-142">Surface の DFCI を構成する前に  [、Microsoft Intune](https://docs.microsoft.com/intune/) および Azure Active [Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD) の Autopilot 構成要件を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-142">Before configuring DFCI for Surface, you should be familiar with Autopilot configuration requirements in  [Microsoft Intune](https://docs.microsoft.com/intune/) and [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD).</span></span>

## <span data-ttu-id="358bd-143">始める前に</span><span class="sxs-lookup"><span data-stu-id="358bd-143">Before you begin</span></span>

<span data-ttu-id="358bd-144">ターゲット Surface デバイスを Azure AD セキュリティ グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="358bd-144">Add your target Surface devices to an Azure AD security group.</span></span> <span data-ttu-id="358bd-145">セキュリティ グループの作成と管理の詳細については、Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。</span><span class="sxs-lookup"><span data-stu-id="358bd-145">For more information about creating and managing security groups, refer to [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups).</span></span>

## <span data-ttu-id="358bd-146">Surface デバイスの DFCI 管理を構成する</span><span class="sxs-lookup"><span data-stu-id="358bd-146">Configure DFCI management for Surface devices</span></span>

<span data-ttu-id="358bd-147">DFCI 環境では、設定を含む DFCI プロファイルを設定し、登録されたデバイスに設定を適用する Autopilot プロファイルを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-147">A DFCI environment requires setting up a DFCI profile that contains  the settings and an Autopilot profile to apply the settings to registered devices.</span></span> <span data-ttu-id="358bd-148">登録状態プロファイルは、ユーザーが初めてデバイスを起動するときに、OOBE のセットアップ中に設定がプッシュダウンされるのを確認するためにも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-148">An enrollment status profile is also recommended to ensure settings are pushed down during OOBE setup when users first start the device.</span></span> <span data-ttu-id="358bd-149">このガイドでは、DFCI 環境を構成し、対象となる Surface デバイスの UEFI 構成設定を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="358bd-149">This guide explains how to configure the DFCI environment and manage UEFI configuration settings for targeted Surface devices.</span></span>

## <span data-ttu-id="358bd-150">DFCI プロファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="358bd-150">Create DFCI profile</span></span>

<span data-ttu-id="358bd-151">DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-151">Before configuring DFCI policy settings, first create a DFCI profile and assign it to the Azure AD security group that contains your target devices.</span></span>

1. <span data-ttu-id="358bd-152">サインイン時にテナントにdevicemanagement.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="358bd-152">Sign into your tenant at  devicemanagement.microsoft.com.</span></span>
2. <span data-ttu-id="358bd-153">Microsoft Endpoint Manager 管理センターで、[デバイスと構成>を選択>プロファイルを作成 **し** 、名前を入力します。たとえば **、DFCI 構成ポリシーです。**</span><span class="sxs-lookup"><span data-stu-id="358bd-153">In the Microsoft Endpoint Manager Admin Center, select **Devices > Configuration profiles > Create profile** and enter a name; for example, **DFCI Configuration Policy.**</span></span>
3. <span data-ttu-id="358bd-154">プラットフォーム **の種類として Windows 10 以降** を選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-154">Select **Windows 10 and later** for platform type.</span></span>
4. <span data-ttu-id="358bd-155">[プロファイルの種類] ドロップダウン リストで、[ **デバイス** ファームウェア構成インターフェイス] を選択し、使用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="358bd-155">In the Profile type drop down list, select **Device Firmware Configuration Interface** to open the DFCI blade containing all available policy settings.</span></span> <span data-ttu-id="358bd-156">DFCI 設定の詳細については、このページの表 1 または Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。</span><span class="sxs-lookup"><span data-stu-id="358bd-156">For information on DFCI settings, refer to Table 1 on this page or the [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span> <span data-ttu-id="358bd-157">初期セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-157">You can configure DFCI settings during the initial setup process or later by editing the DFCI profile.</span></span>

    ![DFCI プロファイルを作成する](images/df1.png)

5. <span data-ttu-id="358bd-159">**[OK] を**クリックし、[作成] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-159">Click **OK** and then select **Create**.</span></span>
6. <span data-ttu-id="358bd-160">次**の図に**示\*\*\*\* すように、[割り当て] を選択し、[グループの選択] でターゲット デバイスを含む Azure AD セキュリティ グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-160">Select **Assignments** and under **Select groups to include** select the Azure AD security group that contains your target devices, as shown in the following figure.</span></span> <span data-ttu-id="358bd-161">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="358bd-161">Click **Save**.</span></span>

    ![セキュリティ グループを割り当てる](images/df2a.png)

## <span data-ttu-id="358bd-163">Autopilot プロファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="358bd-163">Create Autopilot profile</span></span>

1. <span data-ttu-id="358bd-164">In Endpoint Manager at devicemanagement.microsoft.com, select **devices > windows enrollment** and scroll down to Deployment **profiles**.</span><span class="sxs-lookup"><span data-stu-id="358bd-164">In Endpoint Manager at  devicemanagement.microsoft.com, select **devices > Windows enrollment** and scroll down to **Deployment profiles**.</span></span>
2. <span data-ttu-id="358bd-165">[プロファイル **の作成] を** 選択し、名前を入力します。For example, **My Autopilot profile,** and select **Next**.</span><span class="sxs-lookup"><span data-stu-id="358bd-165">Select **Create profile** and enter a name; for example, **My Autopilot profile**, and select **Next**.</span></span>
3. <span data-ttu-id="358bd-166">次の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-166">Select the following settings:</span></span>

    - <span data-ttu-id="358bd-167">展開モード: **ユーザー駆動型**。</span><span class="sxs-lookup"><span data-stu-id="358bd-167">Deployment mode: **User-Driven**.</span></span>
    - <span data-ttu-id="358bd-168">参加の種類: Azure **AD参加しています**。</span><span class="sxs-lookup"><span data-stu-id="358bd-168">Join type: Azure **AD joined**.</span></span>

4. <span data-ttu-id="358bd-169">次の図に示すように、残りの\*\*\*\* 既定の設定は変更されず、[次へ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-169">Leave the remaining default settings unchanged and select **Next**, as shown in the following figure.</span></span>

    ![Autopilot プロファイルを作成する](images/df3b.png)

5. <span data-ttu-id="358bd-171">[割り当て]\*\*\*\* ページで、[含めるグループの選択] を選択し、Azure AD セキュリティ グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="358bd-171">On the Assignments page, choose **Select groups to include** and click your Azure AD security group.</span></span> <span data-ttu-id="358bd-172">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-172">Select **Next**.</span></span>
6. <span data-ttu-id="358bd-173">概要を受け入れ、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-173">Accept the summary and then select **Create**.</span></span> <span data-ttu-id="358bd-174">これで、Autopilot プロファイルが作成され、グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="358bd-174">The Autopilot profile is now created and assigned to the group.</span></span>

## <span data-ttu-id="358bd-175">[登録状態の構成] ページ</span><span class="sxs-lookup"><span data-stu-id="358bd-175">Configure Enrollment Status Page</span></span>

<span data-ttu-id="358bd-176">ユーザーがサインインする前に OOBE 中にデバイスが DFCI 構成を適用するには、登録状態を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-176">To ensure that devices apply the DFCI configuration during OOBE before users sign in, you need to configure enrollment status.</span></span>

<span data-ttu-id="358bd-177">詳細については、「登録状態の [設定」ページを参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。</span><span class="sxs-lookup"><span data-stu-id="358bd-177">For more information, refer to [Set up an enrollment status page](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status).</span></span>


## <span data-ttu-id="358bd-178">Surface デバイスで DFCI 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="358bd-178">Configure DFCI settings on Surface devices</span></span>

<span data-ttu-id="358bd-179">DFCI には、ハードウェア レベルでデバイスをロックダウンすることで、より高いレベルのセキュリティを提供する UEFI 構成ポリシーの合理化されたセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="358bd-179">DFCI includes a streamlined set of UEFI configuration policies that provide an extra level of security by locking down devices at the hardware level.</span></span> <span data-ttu-id="358bd-180">DFCI は、ソフトウェア レベルでのモバイル デバイス管理設定と組み合わせて使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="358bd-180">DFCI is designed to be used in conjunction with mobile device management settings at the software level.</span></span> <span data-ttu-id="358bd-181">DFCI 設定は Surface デバイスに組み込みのハードウェア コンポーネントにのみ影響し、USB Web カメラなどの接続された周辺機器には適用されません。</span><span class="sxs-lookup"><span data-stu-id="358bd-181">Note that DFCI settings only affect hardware components built into Surface devices and do not extend to attached peripherals such as USB webcams.</span></span> <span data-ttu-id="358bd-182">(ただし、Intune のデバイス制限ポリシーを使用して、ソフトウェア レベルで接続された周辺機器へのアクセスをオフにできます)。</span><span class="sxs-lookup"><span data-stu-id="358bd-182">(However, you can use Device restriction policies in Intune to turn off access to attached peripherals at the software level).</span></span>

<span data-ttu-id="358bd-183">以下の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="358bd-183">You configure DFCI policy settings by editing the DFCI profile from Endpoint Manager, as shown in the figure below.</span></span> 

- <span data-ttu-id="358bd-184">エンドポイント マネージャーの devicemanagement.microsoft.comで、Windows > > Configuration Profiles > **"DFCI profile name"**> Properties > Settings ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="358bd-184">In Endpoint Manager at  devicemanagement.microsoft.com, select **Devices > Windows > Configuration Profiles > “DFCI profile name” > Properties > Settings**.</span></span>

    ![DFCI 設定を構成する](images/dfciconfig.png)

### <span data-ttu-id="358bd-186">UEFI 設定へのユーザー アクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="358bd-186">Block user access to UEFI settings</span></span>

<span data-ttu-id="358bd-187">多くのお客様にとって、ユーザーが UEFI 設定を変更することをブロックする機能は非常に重要であり、DFCI を使用する主な理由です。</span><span class="sxs-lookup"><span data-stu-id="358bd-187">For many customers, the ability to block users from changing UEFI settings is critically important and a primary reason to use DFCI.</span></span> <span data-ttu-id="358bd-188">表 1 に示す通り、これはローカル ユーザーによる UEFI 設定の変更を許可する設定 **によって管理されます**。</span><span class="sxs-lookup"><span data-stu-id="358bd-188">As listed in Table 1, this is managed via the setting **Allow local user to change UEFI settings**.</span></span> <span data-ttu-id="358bd-189">この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-189">If you do not edit or configure this setting, local users will be able to change any UEFI setting not managed by Intune.</span></span> <span data-ttu-id="358bd-190">そのため、ローカル ユーザーによる UEFI 設定の変更を許可することを無効に **することを強くお勧めします。**</span><span class="sxs-lookup"><span data-stu-id="358bd-190">Therefore, it’s highly recommended to disable **Allow local user to change UEFI settings.**</span></span>
<span data-ttu-id="358bd-191">残りの DFCI 設定では、ユーザーが使用できない機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="358bd-191">The rest of the DFCI settings enable you to turn off functionality that would otherwise be available to users.</span></span> <span data-ttu-id="358bd-192">たとえば、セキュリティが高い領域で機密情報を保護する必要がある場合は、カメラを無効にし、ユーザーが USB ドライブから起動したくない場合は、無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="358bd-192">For example, if you need to protect sensitive information in highly secure areas, you can disable the camera, and if you don’t want users booting from USB drives, you can disable that also.</span></span>

### <span data-ttu-id="358bd-193">表 1.</span><span class="sxs-lookup"><span data-stu-id="358bd-193">Table 1.</span></span> <span data-ttu-id="358bd-194">DFCI シナリオ</span><span class="sxs-lookup"><span data-stu-id="358bd-194">DFCI scenarios</span></span>

| <span data-ttu-id="358bd-195">デバイス管理の目標</span><span class="sxs-lookup"><span data-stu-id="358bd-195">Device management goal</span></span>                        | <span data-ttu-id="358bd-196">構成手順</span><span class="sxs-lookup"><span data-stu-id="358bd-196">Configuration steps</span></span>                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="358bd-197">ローカル ユーザーが UEFI 設定を変更することをブロックする</span><span class="sxs-lookup"><span data-stu-id="358bd-197">Block local users from changing UEFI settings</span></span> | <span data-ttu-id="358bd-198">[ **セキュリティ機能] >ローカル ユーザーによる UEFI**設定の変更を許可する] で、[なし] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-198">Under **Security Features > Allow local user to change UEFI settings**, select **None**.</span></span>              |
| <span data-ttu-id="358bd-199">カメラを無効にする</span><span class="sxs-lookup"><span data-stu-id="358bd-199">Disable cameras</span></span>                               | <span data-ttu-id="358bd-200">[ **組み込みのハードウェア > カメラ**] で、[無効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-200">Under **Built in Hardware > Cameras**, select **Disabled**.</span></span>                                       |
| <span data-ttu-id="358bd-201">マイクとスピーカーを無効にする</span><span class="sxs-lookup"><span data-stu-id="358bd-201">Disable Microphones and speakers</span></span>              | <span data-ttu-id="358bd-202">[Built **in Hardware > Microphones and speakers]** で、[無効] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-202">Under **Built in Hardware > Microphones and speakers**, select **Disabled**.</span></span>                      |
| <span data-ttu-id="358bd-203">無線を無効にする (Bluetooth、Wi-Fi)</span><span class="sxs-lookup"><span data-stu-id="358bd-203">Disable radios (Bluetooth, Wi-Fi)</span></span>             | <span data-ttu-id="358bd-204">[Built **in Hardware > Radios (Bluetooth, Wi-Fi など)]** で、[無効] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-204">Under **Built in Hardware > Radios (Bluetooth, Wi-Fi, etc…)**, select **Disabled**.</span></span>                   |
| <span data-ttu-id="358bd-205">外部メディア (USB、SD) からのブートを無効にする</span><span class="sxs-lookup"><span data-stu-id="358bd-205">Disable Boot from external media (USB, SD)</span></span>    | <span data-ttu-id="358bd-206">[Built **in Hardware > Boot Options > Boot from external media (USB, SD)**] で、[無効] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-206">Under **Built in Hardware > Boot Options > Boot from external media (USB, SD)**, select **Disabled**.</span></span> |

> [!CAUTION]
> <span data-ttu-id="358bd-207">Disable **radios (Bluetooth, Wi-Fi)** 設定は、ワイヤード (有線) イーサネット接続を備えるデバイスでのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="358bd-207">The **Disable radios (Bluetooth, Wi-Fi)** setting should only be used on devices that have a wired Ethernet connection.</span></span>
 
> [!NOTE]
>  <span data-ttu-id="358bd-208">Intune の DFCI には、現在 Surface デバイスには適用されない 2 つの設定が含まれています。(1) CPU と IO の仮想化と (2) ネットワーク アダプターからのブートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="358bd-208">DFCI in Intune includes two settings that do not currently apply to Surface devices: (1) CPU and IO virtualization and (2) Disable Boot from network adapters.</span></span>
 
<span data-ttu-id="358bd-209">Intune には、管理権限を委任するためのスコープ タグと、デバイスの種類を管理するための適用性ルールが提供されています。</span><span class="sxs-lookup"><span data-stu-id="358bd-209">Intune provides Scope tags to delegate administrative rights and Applicability Rules to manage device types.</span></span> <span data-ttu-id="358bd-210">ポリシー管理のサポートとすべての DFCI 設定の詳細については、Microsoft Intune のドキュメント [を参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。</span><span class="sxs-lookup"><span data-stu-id="358bd-210">For more information about policy management support and full details on all DFCI settings, refer to [Microsoft Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span>

## <span data-ttu-id="358bd-211">Autopilot でデバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="358bd-211">Register devices in Autopilot</span></span>

<span data-ttu-id="358bd-212">上記のように、DFCI は、リセラーまたはディストリビューターによって Windows Autopilot に登録されているデバイスにのみ適用できます。また、Surface Pro 7+、Surface Laptop Go、Surface Pro 7、Surface Pro X、Surface Laptop 3 でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="358bd-212">As stated above, DFCI can only be applied on devices registered in Windows Autopilot by your reseller or distributor and is only supported on Surface Pro 7+, Surface Laptop Go, Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="358bd-213">セキュリティ上の理由から、デバイスを Autopilot に "セルフ プロビジョニング" できません。</span><span class="sxs-lookup"><span data-stu-id="358bd-213">For security reasons, it’s not possible to “self-provision” your devices into Autopilot.</span></span> <span data-ttu-id="358bd-214">詳しくは、Windows Autopilot の Surface [登録サポートに関するページをご覧ください](surface-autopilot-registration-support.md)。</span><span class="sxs-lookup"><span data-stu-id="358bd-214">To learn more, see Surface [Registration Support for Windows Autopilot](surface-autopilot-registration-support.md).</span></span> 

## <span data-ttu-id="358bd-215">Autopilot デバイスを手動で同期する</span><span class="sxs-lookup"><span data-stu-id="358bd-215">Manually Sync Autopilot devices</span></span>

<span data-ttu-id="358bd-216">Intune ポリシー設定は通常、ほぼ即座に適用されます。ただし、設定が対象デバイスに適用される前に、10 分の遅延が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-216">Although Intune policy settings typically get applied almost immediately, there may be a delay of 10 minutes before the settings take effect on targeted devices.</span></span> <span data-ttu-id="358bd-217">まれな状況では、最大 8 時間の遅延が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-217">In rare circumstances, delays of up to 8 hours are possible.</span></span> <span data-ttu-id="358bd-218">(テスト シナリオなど) 設定をできるだけ早く適用するには、ターゲット デバイスを手動で同期できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-218">To ensure settings apply as soon as possible, (such as in test scenarios), you can manually sync the target devices.</span></span>

- <span data-ttu-id="358bd-219">In Endpoint Manager at devicemanagement.microsoft.com, go **to Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.</span><span class="sxs-lookup"><span data-stu-id="358bd-219">In Endpoint Manager at  devicemanagement.microsoft.com, go to **Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.</span></span>

 <span data-ttu-id="358bd-220">詳しくは、「Windows デバイスを手動 [で同期する」をご覧ください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。</span><span class="sxs-lookup"><span data-stu-id="358bd-220">For more information, refer to [Sync your Windows device manually](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).</span></span>

> [!NOTE]
> <span data-ttu-id="358bd-221">UEFI で直接設定を調整する場合は、デバイスが標準の Windows ログインに完全に再起動することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-221">When adjusting settings directly in UEFI, you need to ensure the device fully restarts to the standard Windows login.</span></span>

## <span data-ttu-id="358bd-222">DFCI で管理されるデバイスでの UEFI 設定の確認</span><span class="sxs-lookup"><span data-stu-id="358bd-222">Verifying UEFI settings on DFCI-managed devices</span></span>

<span data-ttu-id="358bd-223">テスト環境では、Surface UEFI インターフェイスの設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-223">In a test environment, you can verify settings in the Surface UEFI interface.</span></span>

1. <span data-ttu-id="358bd-224">Surface UEFI を開きます。ボリューム**ボタンと\*\*\*\*電源**ボタンを同時に押す必要があります。</span><span class="sxs-lookup"><span data-stu-id="358bd-224">Open Surface UEFI, which involves pressing the **Volume +** and **Power** buttons at the same time.</span></span>
2. <span data-ttu-id="358bd-225">[デバイス **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-225">Select **Devices**.</span></span> <span data-ttu-id="358bd-226">次の図に示すように、UEFI メニューには構成済みの設定が反映されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-226">The UEFI menu will reflect configured settings, as shown in the following figure.</span></span>

    ![Surface UEFI](images/df3.png)

    <span data-ttu-id="358bd-228">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="358bd-228">Note how:</span></span>

      - <span data-ttu-id="358bd-229">ローカル ユーザーによる **UEFI** 設定の変更を許可する設定が [なし] に設定されている場合、設定は灰色表示されます。</span><span class="sxs-lookup"><span data-stu-id="358bd-229">The settings are greyed out because **Allow local user to change UEFI setting** is set to None.</span></span>
      - <span data-ttu-id="358bd-230">マイクとスピーカーが無効に設定されているので、 **オーディオがオフ** に設定 **されています**。</span><span class="sxs-lookup"><span data-stu-id="358bd-230">Audio is set to off because **Microphones and speakers** are set to **Disabled**.</span></span>

## <span data-ttu-id="358bd-231">DFCI ポリシー設定の削除</span><span class="sxs-lookup"><span data-stu-id="358bd-231">Removing DFCI policy settings</span></span>

<span data-ttu-id="358bd-232">DFCI プロファイルを作成する場合、構成済みのすべての設定は、プロファイルの管理範囲内のすべてのデバイスで有効なままです。</span><span class="sxs-lookup"><span data-stu-id="358bd-232">When you create a DFCI profile, all configured settings will remain in effect across all devices within the profile’s scope of management.</span></span> <span data-ttu-id="358bd-233">DFCI ポリシー設定は、DFCI プロファイルを直接編集することでのみ削除できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-233">You can only remove DFCI policy settings by editing the DFCI profile directly.</span></span>

<span data-ttu-id="358bd-234">元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="358bd-234">If the original DFCI profile has been deleted, you can remove policy settings by creating a new profile and then editing the settings, as appropriate.</span></span>

## <span data-ttu-id="358bd-235">DFCI 管理の削除</span><span class="sxs-lookup"><span data-stu-id="358bd-235">Removing DFCI management</span></span>

**<span data-ttu-id="358bd-236">DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻す方法:</span><span class="sxs-lookup"><span data-stu-id="358bd-236">To remove DFCI management and return device to factory new state:</span></span>**

1. <span data-ttu-id="358bd-237">Intune からデバイスをリタイアします。</span><span class="sxs-lookup"><span data-stu-id="358bd-237">Retire the device from Intune:</span></span>
    1. <span data-ttu-id="358bd-238">In Endpoint Manager at devicemanagement.microsoft.com, choose **Groups > All Devices**.</span><span class="sxs-lookup"><span data-stu-id="358bd-238">In Endpoint Manager at  devicemanagement.microsoft.com, choose **Groups > All Devices**.</span></span> <span data-ttu-id="358bd-239">リタイアするデバイスを選択し、[リタイア/ワイプ **] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="358bd-239">Select the devices you want to retire, and then choose **Retire/Wipe.**</span></span> <span data-ttu-id="358bd-240">詳細については、「ワイプ、リタイア、または手動でのデバイスの登録解除を使用してデバイスを削除する」 [を参照してください](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。</span><span class="sxs-lookup"><span data-stu-id="358bd-240">To learn more refer to [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/remote-actions/devices-wipe).</span></span> 
2. <span data-ttu-id="358bd-241">Intune から Autopilot 登録を削除します。</span><span class="sxs-lookup"><span data-stu-id="358bd-241">Delete the Autopilot registration from Intune:</span></span>
    1.  <span data-ttu-id="358bd-242">Choose **Device enrollment > Windows enrollment > Devices**.</span><span class="sxs-lookup"><span data-stu-id="358bd-242">Choose **Device enrollment > Windows enrollment > Devices**.</span></span>
    2. <span data-ttu-id="358bd-243">[Windows Autopilot デバイス] で、削除するデバイスを選択し、[削除] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="358bd-243">Under Windows Autopilot devices, choose the devices you want to delete, and then choose **Delete**.</span></span>
3. <span data-ttu-id="358bd-244">Surface ブランドのイーサネット アダプターを使用して、デバイスを有線インターネットに接続します。</span><span class="sxs-lookup"><span data-stu-id="358bd-244">Connect device to wired internet with Surface-branded ethernet adapter.</span></span> <span data-ttu-id="358bd-245">デバイスを再起動し、UEFI メニューを開きます (音量を上げながら電源ボタンを長押しします)。</span><span class="sxs-lookup"><span data-stu-id="358bd-245">Restart device and open the UEFI menu (press and hold the volume-up button while also pressing and releasing the power button).</span></span>
4. <span data-ttu-id="358bd-246">[ **管理] >構成>ネットワーク** から更新] を選択し、[オプトアウト] **を選択します。**</span><span class="sxs-lookup"><span data-stu-id="358bd-246">Select **Management > Configure > Refresh from Network** and then choose **Opt-out.**</span></span>

<span data-ttu-id="358bd-247">Intune を使用してデバイスを管理し続けるが、DFCI 管理を使用しない場合は、デバイスを Autopilot に自己登録し、Intune に登録します。</span><span class="sxs-lookup"><span data-stu-id="358bd-247">To keep managing the device with Intune, but without DFCI management, self-register the device to Autopilot and enroll it to Intune.</span></span> <span data-ttu-id="358bd-248">DFCI は、自己登録デバイスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="358bd-248">DFCI will not be applied to self-registered devices.</span></span>

## <span data-ttu-id="358bd-249">詳細情報</span><span class="sxs-lookup"><span data-stu-id="358bd-249">Learn more</span></span>
- <span data-ttu-id="358bd-250">[Ignite 2019: Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)からの Surface UEFI 設定のリモート管理の発表 
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span><span class="sxs-lookup"><span data-stu-id="358bd-250">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span></span>
- [<span data-ttu-id="358bd-251">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="358bd-251">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md) 
- [<span data-ttu-id="358bd-252">Microsoft Intune の Windows デバイスで DFCI プロファイルを使用する</span><span class="sxs-lookup"><span data-stu-id="358bd-252">Use DFCI profiles on Windows devices in Microsoft Intune</span></span>](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
