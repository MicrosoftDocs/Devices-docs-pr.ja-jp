---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成し、対象の Surface デバイスのファームウェア設定を管理する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 08/19/2020
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
ms.openlocfilehash: 9d83fe9b7febf996d2cb314399505ed050a69a92
ms.sourcegitcommit: b94832cba98e01014f7d184c85d79f8339e046c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2020
ms.locfileid: "10941660"
---
# <span data-ttu-id="3a81f-103">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="3a81f-103">Intune management of Surface UEFI settings</span></span>

## <span data-ttu-id="3a81f-104">概要</span><span class="sxs-lookup"><span data-stu-id="3a81f-104">Introduction</span></span>

<span data-ttu-id="3a81f-105">クラウドからデバイスを管理する機能は、IT の展開とライフサイクルにわたってプロビジョニングを行っています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-105">The ability to manage devices from the cloud has dramatically simplified IT deployment and provisioning across the lifecycle.</span></span> <span data-ttu-id="3a81f-106">Microsoft Intune に組み込まれた (パブリック プレビューで利用 [可能にな](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)りました) に組み込まれたデバイス ファームウェア構成インターフェイス (DFCI) プロファイルを使用すると、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルに拡張します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-106">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in [public preview](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="3a81f-107">DFCI は、ゼロタッチ プロビジョニング、BIOS パスワードを消します。ボット オプションと組み込み周期など、セキュリティ設定を制御し、以降の高度なセキュリティ シナリオの基本的なセキュリティ設定を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-107">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="3a81f-108">よく寄せられる質問への回答については [、「Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発信する」を参照してください](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-108">For answers to frequently asked questions, see [Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).</span></span>

### <span data-ttu-id="3a81f-109">Background</span><span class="sxs-lookup"><span data-stu-id="3a81f-109">Background</span></span>

<span data-ttu-id="3a81f-110">Windows 10 を実行しているコンピューターと同様に、Surface デバイスはソートシップに保存されているコードに使用されます。CPU はハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-110">Like any computer running Windows 10, Surface devices rely on code stored in the SoC that enables the CPU to interface with hard drives, display devices, USB ports, and other devices.</span></span> <span data-ttu-id="3a81f-111">この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに保存されているプログラムはソフトウェアと呼ばれています)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-111">The programs stored in this read-only memory (ROM) are known as firmware (while programs stored in dynamic media are known as software).</span></span>

<span data-ttu-id="3a81f-112">現在マーケットで利用できる他の Windows 10 デバイスとは対して、さまざまな UEFI 構成設定を通じてファームウェアを構成および管理できる機能を IT 管理者に提供しています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-112">In contrast to other Windows 10 devices available in the market today, Surface provides IT admins with the ability to configure and manage firmware through a rich set of UEFI configuration settings.</span></span> <span data-ttu-id="3a81f-113">これにより、モバイル デバイス管理 (MDM) ポリシー、構成マネージャー、グループ ポリシーを使用して実装される、ソフトウェア ベースのポリシー管理の上位のハードウェア制御が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-113">This provides a layer of hardware control on top of software-based policy management as implemented via mobile device management (MDM) policies, Configuration Manager or Group Policy.</span></span> <span data-ttu-id="3a81f-114">たとえば、重要な情報を含む、セキュリティで保護された分析領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することでカメラを使用できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-114">For example, organizations deploying devices in highly secure areas with sensitive information can prevent camera use by removing functionality at the hardware level.</span></span> <span data-ttu-id="3a81f-115">デバイスのスタンドポイントから、ファームウェア設定でカメラをオフにすると、カメラを入れるのとよくなります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-115">From a device standpoint, turning the camera off via a firmware setting is equivalent to physically removing the camera.</span></span> <span data-ttu-id="3a81f-116">追加されたセキュリティを、オペレーティング システムソフトウェア設定のみにのみ表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-116">Compare the added security of managing at the firmware level to relying only on operating system software settings.</span></span> <span data-ttu-id="3a81f-117">たとえば、ドメイン環境のポリシー設定を使用して Windows オーディオ サービスを無効にした場合、ローカルの管理者は引き続きサービスを再度有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-117">For example, if you disable the Windows audio service via a policy setting in a domain environment, a local admin could still re-enable the service.</span></span>

### <span data-ttu-id="3a81f-118">DFCI と SEMM</span><span class="sxs-lookup"><span data-stu-id="3a81f-118">DFCI versus SEMM</span></span>

<span data-ttu-id="3a81f-119">これまでは、ファームウェアを Surface Enterprise Management Mode (SEMM) にエントリを管理し、進行中の手動タスクのオーバーヘッドをオーバーヘッドしていました。</span><span class="sxs-lookup"><span data-stu-id="3a81f-119">Until now, managing firmware required enrolling devices into Surface Enterprise Management Mode (SEMM) with the overhead of ongoing manual IT-intensive tasks.</span></span> <span data-ttu-id="3a81f-120">たとえば、SEMM は、Certificate Management プロセスの一部として 2 桁の PC にアクセスするのに IT スタッフを各 PC にてても必要としています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-120">As an example, SEMM requires IT staff to physically access each PC to enter a two-digit pin as part of the certificate management process.</span></span> <span data-ttu-id="3a81f-121">SEMM は、オンプレミス環境の組織にとっても、あまり優れたソリューションですが、複雑さと IT を積が大量に利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-121">Although SEMM remains a good solution for organizations in a strictly on-premises environment, its complexity and IT-intensive requirements make it costly to use.</span></span>

<span data-ttu-id="3a81f-122">Microsoft Intune の新しく統合された UEFI ファームウェア管理機能が新しく統合されました。ハードウェアをロックする機能はシンプルであり、Microsoft エンドポイント マネージャーとして統合されるように [なりました](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-122">Now with newly integrated UEFI firmware management capabilities in Microsoft Intune, the ability to lock down hardware is simplified and easier to use with new features for provisioning, security, and streamlined updating all in a single console, now unified as [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager).</span></span> <span data-ttu-id="3a81f-123">次の図は、デバイスに直接表示され(左側) で表示され、エンドポイント マネージャー コンソール (右) で表示される UEFI 設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-123">The following figure shows UEFI settings viewed directly on the device (left) and viewed in the Endpoint Manager console (right).</span></span>

![デバイス (左側) およびエンドポイント マネージャー コンソール (右) に表示される UEFI 設定](images/uefidfci.png)

<span data-ttu-id="3a81f-125">DFCI により、DFCI によって、IT 管理者による手動操作の必要性をなくすために、正常に動作する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-125">Crucially, DFCI enables zero touch management, eliminating the need for manual interaction by IT admins.</span></span> <span data-ttu-id="3a81f-126">DFCI は、Intune のデバイス プロファイル機能を使用して、Windows AutoPilot を使用して展開されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-126">DFCI is deployed via Windows Autopilot using the device profiles capability in Intune.</span></span> <span data-ttu-id="3a81f-127">デバイス プロファイルを使用すると、組織内の管理に加集されるデバイスに展開できる設定を追加および構成できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-127">A device profile allows you to add and configure settings which can then be deployed to devices enrolled in management within your organization.</span></span> <span data-ttu-id="3a81f-128">デバイスのプロファイルを受信すると、機能と設定が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-128">Once the device receives the device profile, the features and settings are applied automatically.</span></span> <span data-ttu-id="3a81f-129">一般的なデバイス プロファイルの例としては、メール、デバイスの制限、VPN、Wi-Fi、管理用テンプレートなどがあります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-129">Examples of common device profiles include Email, Device restrictions, VPN, Wi-Fi, and Administrative templates.</span></span> <span data-ttu-id="3a81f-130">DFCI は、追加のデバイス プロファイルで、オンプレミス インフラストラクチャを維保持しなくても、クラウドから UEFI 構成設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-130">DFCI is simply an additional device profile that enables you to manage UEFI configuration settings from the cloud without having to maintain on-premises infrastructure.</span></span>  

## <span data-ttu-id="3a81f-131">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="3a81f-131">Supported devices</span></span>

<span data-ttu-id="3a81f-132">DFCI は、次のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-132">DFCI is supported in the following devices:</span></span>

- <span data-ttu-id="3a81f-133">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="3a81f-133">Surface Pro 7</span></span>
- <span data-ttu-id="3a81f-134">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="3a81f-134">Surface Pro X</span></span>
- <span data-ttu-id="3a81f-135">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="3a81f-135">Surface Laptop 3</span></span>
- <span data-ttu-id="3a81f-136">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="3a81f-136">Surface Book 3</span></span>

> [!NOTE]
> <span data-ttu-id="3a81f-137">Surface Pro X では、内部カメラ、オーディオ、Wi-Fi/Bluetooth の DFCI 設定の管理をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3a81f-137">Surface Pro X does not support DFCI settings management for built-in camera, audio, and Wi-Fi/Bluetooth.</span></span>

## <span data-ttu-id="3a81f-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="3a81f-138">Prerequisites</span></span>

- <span data-ttu-id="3a81f-139">デバイスは、Microsoft クラウド ソリューション プロバイダー [(CSP)](https://partner.microsoft.com/membership/cloud-solution-provider) パートナーまたは OEM 配布リストによって Windows AutoPilot に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-139">Devices must be registered with Windows Autopilot by a [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/membership/cloud-solution-provider) or OEM distributor.</span></span>

- <span data-ttu-id="3a81f-140">Surface 用 DFCI を構成する前に  [、Microsoft Intune](https://docs.microsoft.com/intune/) および [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD) での AutoPilot 構成要件について理いる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-140">Before configuring DFCI for Surface, you should be familiar with Autopilot configuration requirements in  [Microsoft Intune](https://docs.microsoft.com/intune/) and [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD).</span></span>

## <span data-ttu-id="3a81f-141">始める前に</span><span class="sxs-lookup"><span data-stu-id="3a81f-141">Before you begin</span></span>

<span data-ttu-id="3a81f-142">Azure セキュリティ グループにターゲットの Surface デバイスADします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-142">Add your target Surface devices to an Azure AD security group.</span></span> <span data-ttu-id="3a81f-143">セキュリティ グループの作成と管理の詳細については [、Intune ドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-143">For more information about creating and managing security groups, refer to [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups).</span></span>

## <span data-ttu-id="3a81f-144">Surface デバイス用の DFCI 管理を構成する</span><span class="sxs-lookup"><span data-stu-id="3a81f-144">Configure DFCI management for Surface devices</span></span>

<span data-ttu-id="3a81f-145">DFCI 環境では、登録済みデバイスに設定を適用する設定と自動パイロット プロファイルを含む DFCI プロファイルを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-145">A DFCI environment requires setting up a DFCI profile that contains  the settings and an Autopilot profile to apply the settings to registered devices.</span></span> <span data-ttu-id="3a81f-146">ユーザーが初めてデバイスを起動したときに、OOBE セットアップ時に設定がプッシュされるようにするには、加わりのステータス プロファイルもあります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-146">An enrollment status profile is also recommended to ensure settings are pushed down during OOBE setup when users first start the device.</span></span> <span data-ttu-id="3a81f-147">このガイドでは、DFCI 環境を構成し、対象の Surface デバイスの UEFI 構成設定を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-147">This guide explains how to configure the DFCI environment and manage UEFI configuration settings for targeted Surface devices.</span></span>

## <span data-ttu-id="3a81f-148">DFCI プロファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="3a81f-148">Create DFCI profile</span></span>

<span data-ttu-id="3a81f-149">DFCI ポリシー設定を構成する前に、最初に DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-149">Before configuring DFCI policy settings, first create a DFCI profile and assign it to the Azure AD security group that contains your target devices.</span></span>

1. <span data-ttu-id="3a81f-150">テナントのテナントdevicemanagement.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="3a81f-150">Sign into your tenant at  devicemanagement.microsoft.com.</span></span>
2. <span data-ttu-id="3a81f-151">Microsoft エンドポイント マネージャ **ー管理センターで、[デバイスの作成] >作成して名前を入力する>選択** します。たとえば **、DFCI 構成ポリシーなどです。**</span><span class="sxs-lookup"><span data-stu-id="3a81f-151">In the Microsoft Endpoint Manager Admin Center, select **Devices > Configuration profiles > Create profile** and enter a name; for example, **DFCI Configuration Policy.**</span></span>
3. <span data-ttu-id="3a81f-152">プ **ラットフォーム タイプに Windows 10** 以降を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-152">Select **Windows 10 and later** for platform type.</span></span>
4. <span data-ttu-id="3a81f-153">[プロファイルの種類] ドロップダウン リストで **、[Device ファームウ** ェア構成インターフェイス] を選択して、利用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-153">In the Profile type drop down list, select **Device Firmware Configuration Interface** to open the DFCI blade containing all available policy settings.</span></span> <span data-ttu-id="3a81f-154">DFCI 設定の詳細については、このページのテーブル 1 または [Intune ドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-154">For information on DFCI settings, refer to Table 1 on this page or the [Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span> <span data-ttu-id="3a81f-155">セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-155">You can configure DFCI settings during the initial setup process or later by editing the DFCI profile.</span></span>

    ![DFCI プロファイルを作成する](images/df1.png)

5. <span data-ttu-id="3a81f-157">**[OK] を**クリックし、[作成] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-157">Click **OK** and then select **Create**.</span></span>
6. <span data-ttu-id="3a81f-158">[ **課題] を選択** し **、[グループの選択] グループ** に、ターゲット デバイスを含む Azure AD セキュリティ グループを選択します。次の図に示すように、ターゲット デバイスを含む Azure セキュリティ グループが選択されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-158">Select **Assignments** and under **Select groups to include** select the Azure AD security group that contains your target devices, as shown in the following figure.</span></span> <span data-ttu-id="3a81f-159">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-159">Click **Save**.</span></span>

    ![セキュリティ グループの割り当て](images/df2a.png)

## <span data-ttu-id="3a81f-161">Autopilot プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="3a81f-161">Create Autopilot profile</span></span>

1. <span data-ttu-id="3a81f-162">devicemanagement.microsoft.com のエンドポイント マネー **ジャーで、Windows の>を選択し、** 下にスクロールして **展開プロファイルに移動します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-162">In Endpoint Manager at  devicemanagement.microsoft.com, select **devices > Windows enrollment** and scroll down to **Deployment profiles**.</span></span>
2. <span data-ttu-id="3a81f-163">[プロ **ファイルの作成** ] を選択して名前を入力します。たとえば、 **自動パイロット プロファイルを選び**、[次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-163">Select **Create profile** and enter a name; for example, **My Autopilot profile**, and select **Next**.</span></span>
3. <span data-ttu-id="3a81f-164">次の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-164">Select the following settings:</span></span>

    - <span data-ttu-id="3a81f-165">展開モード: **ユーザー ドライブ**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-165">Deployment mode: **User-Driven**.</span></span>
    - <span data-ttu-id="3a81f-166">結合の種類: Azure **AD結合されています**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-166">Join type: Azure **AD joined**.</span></span>

4. <span data-ttu-id="3a81f-167">下の図に示すように、残りの既定の設定は変更されていないままにして、[ **次**へ] を選びます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-167">Leave the remaining default settings unchanged and select **Next**, as shown in the following figure.</span></span>

    ![Autopilot プロファイルの作成](images/df3b.png)

5. <span data-ttu-id="3a81f-169">[課題] ページで、[Azure とセキュリティ **グループを** 追加するグループを選択ADクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-169">On the Assignments page, choose **Select groups to include** and click your Azure AD security group.</span></span> <span data-ttu-id="3a81f-170">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-170">Select **Next**.</span></span>
6. <span data-ttu-id="3a81f-171">概要を承諾してから、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-171">Accept the summary and then select **Create**.</span></span> <span data-ttu-id="3a81f-172">これで AutoPilot プロファイルが作成され、グループに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-172">The Autopilot profile is now created and assigned to the group.</span></span>

## <span data-ttu-id="3a81f-173">加集の状態ページを構成する</span><span class="sxs-lookup"><span data-stu-id="3a81f-173">Configure Enrollment Status Page</span></span>

<span data-ttu-id="3a81f-174">ユーザーがサインインする前に OOBE の間に DFCI 構成を適用するには、加注ステータスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-174">To ensure that devices apply the DFCI configuration during OOBE before users sign in, you need to configure enrollment status.</span></span>

<span data-ttu-id="3a81f-175">詳細については、「加えたことを確認する [」のページを参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-175">For more information, refer to [Set up an enrollment status page](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status).</span></span>


## <span data-ttu-id="3a81f-176">Surface デバイスで DFCI 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="3a81f-176">Configure DFCI settings on Surface devices</span></span>

<span data-ttu-id="3a81f-177">DFCI には、ハードウェア レベルでデバイスをロックダウンして、追加のセキュリティ レベルを提供する UEFI 構成ポリシーの効率化されたセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-177">DFCI includes a streamlined set of UEFI configuration policies that provide an extra level of security by locking down devices at the hardware level.</span></span> <span data-ttu-id="3a81f-178">DFCI は、ソフトウェア レベルでモバイル デバイス管理設定とを使用することで使用されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-178">DFCI is designed to be used in conjunction with mobile device management settings at the software level.</span></span> <span data-ttu-id="3a81f-179">DFCI 設定は、Surface デバイスに組み込まれたハードウェア コンポーネントにのみ影響し、USB Web カメラなどのリニシャル接続の選択にも拡張されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3a81f-179">Note that DFCI settings only affect hardware components built into Surface devices and do not extend to attached peripherals such as USB webcams.</span></span> <span data-ttu-id="3a81f-180">ただし、Intune でデバイス制限ポリシーを使用して、ソフトウェア レベルで添付されている機内者へのアクセスをオフにすることができます。)</span><span class="sxs-lookup"><span data-stu-id="3a81f-180">(However, you can use Device restriction policies in Intune to turn off access to attached peripherals at the software level).</span></span>

<span data-ttu-id="3a81f-181">次の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-181">You configure DFCI policy settings by editing the DFCI profile from Endpoint Manager, as shown in the figure below.</span></span> 

- <span data-ttu-id="3a81f-182">devicemanagement.microsoft.com エンドポイント マネージャーで **、Windows >構成プロ >ファイル名> "DFCI プロファイル名" >のプロパティ>選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-182">In Endpoint Manager at  devicemanagement.microsoft.com, select **Devices > Windows > Configuration Profiles > “DFCI profile name” > Properties > Settings**.</span></span>

    ![DFCI 設定を構成する](images/dfciconfig.png)

### <span data-ttu-id="3a81f-184">UEFI 設定へのユーザー アクセスのブロック</span><span class="sxs-lookup"><span data-stu-id="3a81f-184">Block user access to UEFI settings</span></span>

<span data-ttu-id="3a81f-185">多くのお客様にとって、ユーザーが UEFI 設定の変更を禁止する機能は重要であり、DFCI を使用する主な理由は重要です。</span><span class="sxs-lookup"><span data-stu-id="3a81f-185">For many customers, the ability to block users from changing UEFI settings is critically important and a primary reason to use DFCI.</span></span> <span data-ttu-id="3a81f-186">テーブル 1 に示されているように、これはローカル ユーザーに UEFI 設定を変更する設定 **によって管理されます**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-186">As listed in Table 1, this is managed via the setting **Allow local user to change UEFI settings**.</span></span> <span data-ttu-id="3a81f-187">この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-187">If you do not edit or configure this setting, local users will be able to change any UEFI setting not managed by Intune.</span></span> <span data-ttu-id="3a81f-188">そのため、ローカル ユーザーに UEFI 設定の変更を許可することを強 **くお勧めします。**</span><span class="sxs-lookup"><span data-stu-id="3a81f-188">Therefore, it’s highly recommended to disable **Allow local user to change UEFI settings.**</span></span>
<span data-ttu-id="3a81f-189">残りの DFCI 設定では、他の方法では、他の方法ではユーザーが使用できるようにする機能をオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-189">The rest of the DFCI settings enable you to turn off functionality that would otherwise be available to users.</span></span> <span data-ttu-id="3a81f-190">たとえば、高度にセキュリティで保護された領域で機関情報を保護する必要がある場合、カメラを無効にしたり、ユーザーが USB ドライブからブードを起動しないようにしたりする場合は、無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-190">For example, if you need to protect sensitive information in highly secure areas, you can disable the camera, and if you don’t want users booting from USB drives, you can disable that also.</span></span>

### <span data-ttu-id="3a81f-191">表 1.</span><span class="sxs-lookup"><span data-stu-id="3a81f-191">Table 1.</span></span> <span data-ttu-id="3a81f-192">DFCI シナリオ</span><span class="sxs-lookup"><span data-stu-id="3a81f-192">DFCI scenarios</span></span>

| <span data-ttu-id="3a81f-193">デバイス管理の目標</span><span class="sxs-lookup"><span data-stu-id="3a81f-193">Device management goal</span></span>                        | <span data-ttu-id="3a81f-194">構成手順</span><span class="sxs-lookup"><span data-stu-id="3a81f-194">Configuration steps</span></span>                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="3a81f-195">ローカル ユーザーが UEFI 設定を変更できないことを禁止する</span><span class="sxs-lookup"><span data-stu-id="3a81f-195">Block local users from changing UEFI settings</span></span> | <span data-ttu-id="3a81f-196">[**セキュリティ機能] >UEFI 設定の変更を許可する] で [\*\*\*\*なし] を選びます**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-196">Under **Security Features > Allow local user to change UEFI settings**, select **None**.</span></span>              |
| <span data-ttu-id="3a81f-197">カメラを無効にする</span><span class="sxs-lookup"><span data-stu-id="3a81f-197">Disable cameras</span></span>                               | <span data-ttu-id="3a81f-198">ハ **ードウェアの組み込みの>で、[無効**] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-198">Under **Built in Hardware > Cameras**, select **Disabled**.</span></span>                                       |
| <span data-ttu-id="3a81f-199">マイクとスピーカーを無効にする</span><span class="sxs-lookup"><span data-stu-id="3a81f-199">Disable Microphones and speakers</span></span>              | <span data-ttu-id="3a81f-200">ハ **ードウェアの組み込み>マ**イクとスピーカーで、[無効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-200">Under **Built in Hardware > Microphones and speakers**, select **Disabled**.</span></span>                      |
| <span data-ttu-id="3a81f-201">ラジオを無効にBluetooth (Wi-Fi)</span><span class="sxs-lookup"><span data-stu-id="3a81f-201">Disable radios (Bluetooth, Wi-Fi)</span></span>             | <span data-ttu-id="3a81f-202">ハ **ードウェア>ラジオ (Bluetooth Wi-Fi**など) で、[無効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-202">Under **Built in Hardware > Radios (Bluetooth, Wi-Fi, etc…)**, select **Disabled**.</span></span>                   |
| <span data-ttu-id="3a81f-203">外部メディア (USB、SD) からのボットの無効化</span><span class="sxs-lookup"><span data-stu-id="3a81f-203">Disable Boot from external media (USB, SD)</span></span>    | <span data-ttu-id="3a81f-204">ハ **ードウェアの組み込みの> ブート オプション > ブ**ートからボットを表示する) で、[ **無効にする] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-204">Under **Built in Hardware > Boot Options > Boot from external media (USB, SD)**, select **Disabled**.</span></span> |

> [!CAUTION]
> <span data-ttu-id="3a81f-205">無 **線接続のBluetoothデバイスで** のみ、[無効にする] の設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-205">The **Disable radios (Bluetooth, Wi-Fi)** setting should only be used on devices that have a wired Ethernet connection.</span></span>
 
> [!NOTE]
>  <span data-ttu-id="3a81f-206">Intune の DFCI には、現在、Surface デバイスに適用されない 2 つの設定が含まれます。(1) CPU と IO 仮想化、(2) ネットワーク アダプターから Boot を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3a81f-206">DFCI in Intune includes two settings that do not currently apply to Surface devices: (1) CPU and IO virtualization and (2) Disable Boot from network adapters.</span></span>
 
<span data-ttu-id="3a81f-207">Intune では、デバイス タイプを管理する管理権限と適用のルールを代理人にするスコープ タグを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-207">Intune provides Scope tags to delegate administrative rights and Applicability Rules to manage device types.</span></span> <span data-ttu-id="3a81f-208">ポリシー管理サポートとすべての DFCI 設定の詳細については [、Microsoft Intune のドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-208">For more information about policy management support and full details on all DFCI settings, refer to [Microsoft Intune documentation](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).</span></span>

## <span data-ttu-id="3a81f-209">AutoPilot でデバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="3a81f-209">Register devices in Autopilot</span></span>

<span data-ttu-id="3a81f-210">前述のように、DFCI は、再保護者または配布者が Windows Autopilot に登録されているデバイスにのみ適用でき、現在は Surface Pro 7、Surface Pro X、Surface Laptop 3 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3a81f-210">As stated above, DFCI can only be applied on devices registered in Windows Autopilot by your reseller or distributor and is only supported, at this time, on Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="3a81f-211">セキュリティ上の理えから、デバイスを AutoPilot に "セルフプロビジョニング" することはできません。</span><span class="sxs-lookup"><span data-stu-id="3a81f-211">For security reasons, it’s not possible to “self-provision” your devices into Autopilot.</span></span>

## <span data-ttu-id="3a81f-212">自動デバイスを手動で同期する</span><span class="sxs-lookup"><span data-stu-id="3a81f-212">Manually Sync Autopilot devices</span></span>

<span data-ttu-id="3a81f-213">通常、Intune ポリシー設定はほぼすぐに適用されますが、設定が対象デバイスに反映されるまでに 10 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-213">Although Intune policy settings typically get applied almost immediately, there may be a delay of 10 minutes before the settings take effect on targeted devices.</span></span> <span data-ttu-id="3a81f-214">まず、最大 8 時間の遅延が可能です。</span><span class="sxs-lookup"><span data-stu-id="3a81f-214">In rare circumstances, delays of up to 8 hours are possible.</span></span> <span data-ttu-id="3a81f-215">設定が可能な限りすぐに (テスト シナリオなど) を確かめるようにするには、ターゲット デバイスを手動で同期できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-215">To ensure settings apply as soon as possible, (such as in test scenarios), you can manually sync the target devices.</span></span>

- <span data-ttu-id="3a81f-216">devicemanagement.microsoft.com のエンドポイント マ**ネージャー >で、Windows Autopilot デバイス> Windows の加入>Windows の加入>を確認し、[同期] を\*\*\*\*選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-216">In Endpoint Manager at  devicemanagement.microsoft.com, go to **Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.</span></span>

 <span data-ttu-id="3a81f-217">詳細については、「Windows デバイスを [手動で同期する」を参照してください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-217">For more information, refer to [Sync your Windows device manually](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).</span></span>

> [!NOTE]
> <span data-ttu-id="3a81f-218">UEFI で設定を直接調整する場合、デバイスが標準の Windows ログインに完全に再起動されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a81f-218">When adjusting settings directly in UEFI, you need to ensure the device fully restarts to the standard Windows login.</span></span>

## <span data-ttu-id="3a81f-219">DFCI で管理されているデバイスでの UEFI 設定の確認</span><span class="sxs-lookup"><span data-stu-id="3a81f-219">Verifying UEFI settings on DFCI-managed devices</span></span>

<span data-ttu-id="3a81f-220">テスト環境では、Surface UEFI インターフェイスで設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-220">In a test environment, you can verify settings in the Surface UEFI interface.</span></span>

1. <span data-ttu-id="3a81f-221">Surface UEFI を開きます。この場合、ボリューム + ボタンと**電**源**ボ**タンの押下が同時に押されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-221">Open Surface UEFI, which involves pressing the **Volume +** and **Power** buttons at the same time.</span></span>
2. <span data-ttu-id="3a81f-222">[デバイス **] を選びます**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-222">Select **Devices**.</span></span> <span data-ttu-id="3a81f-223">次の図に示すように、構成された設定が UEFI メニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-223">The UEFI menu will reflect configured settings, as shown in the following figure.</span></span>

    ![Surface UEFI](images/df3.png)

    <span data-ttu-id="3a81f-225">方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3a81f-225">Note how:</span></span>

      - <span data-ttu-id="3a81f-226">ローカル ユーザーに **UEFI** 設定の変更を許可する設定が [なし] に設定されているため、設定はグレー表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-226">The settings are greyed out because **Allow local user to change UEFI setting** is set to None.</span></span>
      - <span data-ttu-id="3a81f-227">マイクとスピーカーが無効に設定されているため、**オーディオはオフ\*\*\*\*に設定されています**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-227">Audio is set to off because **Microphones and speakers** are set to **Disabled**.</span></span>

## <span data-ttu-id="3a81f-228">DFCI ポリシー設定の削除</span><span class="sxs-lookup"><span data-stu-id="3a81f-228">Removing DFCI policy settings</span></span>

<span data-ttu-id="3a81f-229">DFCI プロファイルを作成する場合、構成されたすべての設定は、管理のためのプロファイルのスコープ内のすべてのデバイスで有効です。</span><span class="sxs-lookup"><span data-stu-id="3a81f-229">When you create a DFCI profile, all configured settings will remain in effect across all devices within the profile’s scope of management.</span></span> <span data-ttu-id="3a81f-230">DFCI プロファイルを直接編集することで、DFCI ポリシー設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-230">You can only remove DFCI policy settings by editing the DFCI profile directly.</span></span>

<span data-ttu-id="3a81f-231">元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に合って設定を編集することで、ポリシー設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="3a81f-231">If the original DFCI profile has been deleted, you can remove policy settings by creating a new profile and then editing the settings, as appropriate.</span></span>

## <span data-ttu-id="3a81f-232">DFCI 管理の削除</span><span class="sxs-lookup"><span data-stu-id="3a81f-232">Removing DFCI management</span></span>

**<span data-ttu-id="3a81f-233">DFCI 管理を削除してデバイスを出発新状態に戻すには:</span><span class="sxs-lookup"><span data-stu-id="3a81f-233">To remove DFCI management and return device to factory new state:</span></span>**

1. <span data-ttu-id="3a81f-234">Intune からデバイスを廃止します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-234">Retire the device from Intune:</span></span>
    1. <span data-ttu-id="3a81f-235">エンドポイント マネージャdevicemanagement.microsoft.comで、[グループ **>] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-235">In Endpoint Manager at  devicemanagement.microsoft.com, choose **Groups > All Devices**.</span></span> <span data-ttu-id="3a81f-236">回復するデバイスを選択し、[廃 **止/ワイプ] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="3a81f-236">Select the devices you want to retire, and then choose **Retire/Wipe.**</span></span> <span data-ttu-id="3a81f-237">デバイスの追加や手動の解除の詳細については、ワイプ、廃止、またはデバイスの [追加を手動で解除します](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-237">To learn more refer to [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/remote-actions/devices-wipe).</span></span> 
2. <span data-ttu-id="3a81f-238">Intune から自動登録を削除します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-238">Delete the Autopilot registration from Intune:</span></span>
    1.  <span data-ttu-id="3a81f-239">**デバイスの加入>を >選択します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-239">Choose **Device enrollment > Windows enrollment > Devices**.</span></span>
    2. <span data-ttu-id="3a81f-240">Windows Autopilot デバイスで、削除するデバイスを選択し、[削除] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="3a81f-240">Under Windows Autopilot devices, choose the devices you want to delete, and then choose **Delete**.</span></span>
3. <span data-ttu-id="3a81f-241">Surface ブランド イーサネット アダプターで有線インターネットに接続します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-241">Connect device to wired internet with Surface-branded ethernet adapter.</span></span> <span data-ttu-id="3a81f-242">デバイスを再起動し、UEFI メニューを開きます (電源ボタンを押したままにしてから、電源ボタンを押したままにします)。</span><span class="sxs-lookup"><span data-stu-id="3a81f-242">Restart device and open the UEFI menu (press and hold the volume-up button while also pressing and releasing the power button).</span></span>
4. <span data-ttu-id="3a81f-243">[ **管理] >ネットワークからの [>を更新を構成** してから [ **オプトアウト] を選びます。**</span><span class="sxs-lookup"><span data-stu-id="3a81f-243">Select **Management > Configure > Refresh from Network** and then choose **Opt-out.**</span></span>

<span data-ttu-id="3a81f-244">Intune でデバイスを管理し、DFCI 管理がなくても、DFCI 管理がない場合は、デバイスを AutoPilot に登録し、Intune に登録します。</span><span class="sxs-lookup"><span data-stu-id="3a81f-244">To keep managing the device with Intune, but without DFCI management, self-register the device to Autopilot and enroll it to Intune.</span></span> <span data-ttu-id="3a81f-245">自己登録デバイスには DFCI は適用されません。</span><span class="sxs-lookup"><span data-stu-id="3a81f-245">DFCI will not be applied to self-registered devices.</span></span>

## <span data-ttu-id="3a81f-246">詳細情報</span><span class="sxs-lookup"><span data-stu-id="3a81f-246">Learn more</span></span>
- <span data-ttu-id="3a81f-247">[Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発行する](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span><span class="sxs-lookup"><span data-stu-id="3a81f-247">[Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)</span></span>
- [<span data-ttu-id="3a81f-248">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="3a81f-248">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md) 
- [<span data-ttu-id="3a81f-249">Microsoft Intune で Windows デバイスで DFCI プロファイルを使用する</span><span class="sxs-lookup"><span data-stu-id="3a81f-249">Use DFCI profiles on Windows devices in Microsoft Intune</span></span>](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
