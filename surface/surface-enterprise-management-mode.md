---
title: Surface Enterprise Management Mode (Surface)
description: Surface UEFI を使用した Surface デバイスのこの機能が、組織内のファームウェア設定のセキュリティ保護と管理に役立つ方法について説明します。
keywords: uefi、構成、ファームウェア、セキュア、semm
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
audience: itpro
ms.date: 03/18/2021
ms.openlocfilehash: 011f4d0270c47b976e10dbece2adb70559222b79
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442185"
---
# <a name="microsoft-surface-enterprise-management-mode"></a><span data-ttu-id="83bd0-104">Microsoft Surface Enterprise 管理モード</span><span class="sxs-lookup"><span data-stu-id="83bd0-104">Microsoft Surface Enterprise Management Mode</span></span>

<span data-ttu-id="83bd0-105">Microsoft Surface Enterprise Management Mode (SEMM) は、Surface UEFI を備える Surface デバイスの機能で、組織内のファームウェア設定をセキュリティで保護および管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-105">Microsoft Surface Enterprise Management Mode (SEMM) is a feature of Surface devices with Surface UEFI that allows you to secure and manage firmware settings within your organization.</span></span> <span data-ttu-id="83bd0-106">SEMM を使用すると、IT 担当者は UEFI 設定の構成を準備し、Surface デバイスにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-106">With SEMM, IT professionals can prepare configurations of UEFI settings and install them on a Surface device.</span></span> <span data-ttu-id="83bd0-107">UEFI 設定を構成する機能に加えて、SEMM は証明書を使用して、承認されていない改ざんや削除から構成を保護します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-107">In addition to the ability to configure UEFI settings, SEMM also uses a certificate to protect the configuration from unauthorized tampering or removal.</span></span> <span data-ttu-id="83bd0-108">SEMM は、Surface Hub 2S を Windows 10 Pro および Enterprise に移行できる要件です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-108">SEMM is a requirement to be able to migrate a Surface Hub 2S to Windows 10 Pro and Enterprise.</span></span>

>[!NOTE]
><span data-ttu-id="83bd0-109">SEMM は Surface UEFI ファームウェアを持つデバイスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-109">SEMM is only available on devices with Surface UEFI firmware.</span></span> <span data-ttu-id="83bd0-110">これには、Surface Pro 7+、Surface Pro 7、Surface Pro X、Surface Hub 2S、Intel プロセッサを搭載した Surface Laptop 3 商用 SKU、Surface Laptop Go などのほとんどの Surface デバイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-110">This includes most Surface devices including Surface Pro 7+, Surface Pro 7, Surface Pro X, Surface Hub 2S, Surface Laptop 3 commercial SKUs with an Intel processor, and Surface Laptop Go.</span></span> <span data-ttu-id="83bd0-111">SEMM は、AMD プロセッサ付き 15" Surface Laptop 3 SKU ではサポートされていません (小売 SKU としてのみ利用可能)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-111">SEMM is not supported on the 15" Surface Laptop 3 SKU with AMD processor (only available as a retail SKU).</span></span> 

<span data-ttu-id="83bd0-112">Surface デバイスが SEMM によって構成され、SEMM 証明書で保護されている場合、デバイスは SEMM *に登録されたと* 見なされます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-112">When Surface devices are configured by SEMM and secured with the SEMM certificate, they are considered *enrolled* in SEMM.</span></span> <span data-ttu-id="83bd0-113">SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM で登録されていない *と* 見なされます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-113">When the SEMM certificate is removed and control of UEFI settings is returned to the user of the device, the Surface device is considered *unenrolled* in SEMM.</span></span>

<span data-ttu-id="83bd0-114">SEMM を管理し、Surface デバイスを登録するために使用できる管理オプションには、スタンドアロン ツールまたは Microsoft Endpoint Configuration Manager との統合の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-114">There are two administrative options you can use to manage SEMM and enroll Surface devices – a standalone tool or integration with Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="83bd0-115">この記事では、Microsoft Surface UEFI コンフィギュレーターと呼ばれる SEMM スタンドアロン ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-115">The SEMM standalone tool, called the Microsoft Surface UEFI Configurator, is described in this article.</span></span> <span data-ttu-id="83bd0-116">Microsoft Endpoint Configuration Manager を使用して SEMM を管理する方法の詳細については、「Use Microsoft Endpoint Configuration Manager を使用して SEMM を使用してデバイスを管理する」 [を参照してください](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-116">For more information about how to manage SEMM with Microsoft Endpoint Configuration Manager, see [Use Microsoft Endpoint Configuration Manager to manage devices with SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).</span></span>

> [!NOTE]
> <span data-ttu-id="83bd0-117">SEMM は、UEFI マネージャーを介して Surface Pro X でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-117">SEMM is supported on Surface Pro X via the UEFI Manager only.</span></span> <span data-ttu-id="83bd0-118">IT 向け Surface Tools から UEFI [マネージャーをダウンロードできます](https://www.microsoft.com/download/details.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-118">You can download UEFI Manager from [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> <span data-ttu-id="83bd0-119">詳細については [、「Surface Pro X の展開、管理、およびサービス」を参照してください](surface-pro-arm-app-management.md)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-119">For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>


## <a name="microsoft-surface-uefi-configurator"></a><span data-ttu-id="83bd0-120">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="83bd0-120">Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="83bd0-121">図 1 に示すように、SEMM のプライマリ ワークスペースは Microsoft Surface UEFI コンフィギュレーターです。</span><span class="sxs-lookup"><span data-stu-id="83bd0-121">The primary workspace of SEMM is Microsoft Surface UEFI Configurator, as shown in Figure 1.</span></span> <span data-ttu-id="83bd0-122">Microsoft Surface UEFI Configureator は、Surface デバイスでの SEMM の登録、構成、および登録解除に使用される Windows インストーラー (.msi) パッケージまたは WinPE イメージの作成に使用されるツールです。</span><span class="sxs-lookup"><span data-stu-id="83bd0-122">Microsoft Surface UEFI Configurator is a tool used to create Windows Installer (.msi) packages or WinPE images used to enroll, configure, and unenroll SEMM on a Surface device.</span></span> <span data-ttu-id="83bd0-123">これらのパッケージには、UEFI の設定を指定する構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="83bd0-123">These packages contain a configuration file where the settings for UEFI are specified.</span></span> <span data-ttu-id="83bd0-124">SEMM パッケージには証明書も含まれています。この証明書はファームウェアにインストールおよび保存され、UEFI 設定を適用する前に構成ファイルの署名を確認するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-124">SEMM packages also contain a certificate, which is installed and stored in firmware and used to verify the signature of configuration files before UEFI settings are applied.</span></span>

>[!TIP]
><span data-ttu-id="83bd0-125">Surface UEFI コンフィギュレーターと SEMM を使用して、Surface ドック 2 のポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-125">You can now use Surface UEFI Configurator and SEMM to manage ports on Surface Dock 2.</span></span> <span data-ttu-id="83bd0-126">詳細については [、「Secure Surface Dock 2 ports with SEMM」を参照してください](secure-surface-dock-ports-semm.md)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-126">To learn more, see [Secure Surface Dock 2 ports with SEMM](secure-surface-dock-ports-semm.md).</span></span>

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*<span data-ttu-id="83bd0-128">図 1. </span><span class="sxs-lookup"><span data-stu-id="83bd0-128">Figure 1.</span></span> <span data-ttu-id="83bd0-129">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="83bd0-129">Microsoft Surface UEFI Configurator</span></span>*


<span data-ttu-id="83bd0-130">Microsoft Surface UEFI コンフィギュレーター ツールは、次の 3 つのモードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-130">You can use the Microsoft Surface UEFI Configurator tool in three modes:</span></span>

* <span data-ttu-id="83bd0-131">[Surface UEFI 構成パッケージ](#configuration-package)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-131">[Surface UEFI Configuration Package](#configuration-package).</span></span> <span data-ttu-id="83bd0-132">このモードを使用して、Surface UEFI 構成パッケージを作成して、Surface デバイスを SEMM に登録し、登録済みデバイスで UEFI 設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-132">Use this mode to create a Surface UEFI configuration package to enroll a Surface device in SEMM and to configure UEFI settings on enrolled devices.</span></span>
* <span data-ttu-id="83bd0-133">[Surface UEFI リセット パッケージ](#reset-package)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-133">[Surface UEFI Reset Package](#reset-package).</span></span> <span data-ttu-id="83bd0-134">SEMM から Surface デバイスの登録を解除するには、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-134">Use this mode to unenroll a Surface device from SEMM.</span></span>
* <span data-ttu-id="83bd0-135">[Surface UEFI 回復要求](#recovery-request)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-135">[Surface UEFI Recovery Request](#recovery-request).</span></span> <span data-ttu-id="83bd0-136">このモードを使用して、回復要求に応答して、パッケージのリセット操作が成功しない SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-136">Use this mode to respond to a recovery request to unenroll a Surface device from SEMM where a Reset Package operation is not successful.</span></span>


#### <a name="download-microsoft-surface-uefi-configurator"></a><span data-ttu-id="83bd0-137">Microsoft Surface UEFI コンフィギュレーターをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="83bd0-137">Download Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="83bd0-138">Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロード センターの [[Surface Tools for IT]](https://www.microsoft.com/download/details.aspx?id=46703) ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-138">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

### <a name="configuration-package"></a><span data-ttu-id="83bd0-139">構成パッケージ</span><span class="sxs-lookup"><span data-stu-id="83bd0-139">Configuration package</span></span>

<span data-ttu-id="83bd0-140">Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装および管理するための主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="83bd0-140">Surface UEFI configuration packages are the primary mechanism to implement and manage SEMM on Surface devices.</span></span> <span data-ttu-id="83bd0-141">これらのパッケージには、図 2 に示すように、Microsoft Surface UEFI Configurationator でのパッケージの作成時に指定された UEFI 設定の構成ファイルと証明書ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="83bd0-141">These packages contain a configuration file of UEFI settings specified during creation of the package in Microsoft Surface UEFI Configurator and a certificate file, as shown in Figure 2.</span></span> <span data-ttu-id="83bd0-142">SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアに証明書ファイルが準備され、SEMM にデバイスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-142">When a configuration package is run for the first time on a Surface device that is not already enrolled in SEMM, it provisions the certificate file in the device’s firmware and enrolls the device in SEMM.</span></span> <span data-ttu-id="83bd0-143">SEMM にデバイスを登録するときに、証明書ファイルが保存され、登録が完了する前に、SEMM 証明書の拇印の最後の 2 桁を指定して操作を確認するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-143">When enrolling a device in SEMM, you will be prompted to confirm the operation by providing the last two digits of the SEMM certificate thumbprint before the certificate file is stored and the enrollment can complete.</span></span> <span data-ttu-id="83bd0-144">この確認では、確認を実行するには、登録時にユーザーがデバイスに物理的に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-144">This confirmation requires a user be physically present at the device at the time of enrollment to perform the confirmation.</span></span>

![証明書を使用して SEMM 構成パッケージをセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*<span data-ttu-id="83bd0-146">図 2. </span><span class="sxs-lookup"><span data-stu-id="83bd0-146">Figure 2.</span></span> <span data-ttu-id="83bd0-147">証明書を使用して SEMM 構成パッケージをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="83bd0-147">Secure a SEMM configuration package with a certificate</span></span>*

<span data-ttu-id="83bd0-148">SEMM [証明書の要件の](#surface-enterprise-management-mode-certificate-requirements) 詳細については、この記事の「Surface Enterprise Management Mode 証明書要件」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="83bd0-148">See the [Surface Enterprise Management Mode certificate requirements](#surface-enterprise-management-mode-certificate-requirements) section of this article for more information about the requirements for the SEMM certificate.</span></span>

>[!TIP]
><span data-ttu-id="83bd0-149">Surface UEFI のセキュリティ、デバイス、ブート構成、またはエンタープライズ管理ページを表示\*\*\*\* するために必要な SEMM\*\*\*\* を使用して UEFI パスワードを指定することもできます。 \*\*\*\* \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="83bd0-149">You can also specify a UEFI password with SEMM that is required to view the **Security**, **Devices**, **Boot Configuration**, or **Enterprise Management** pages of Surface UEFI.</span></span>

<span data-ttu-id="83bd0-150">デバイスが SEMM に登録されると、構成ファイルが読み取り、ファイルで指定された設定が UEFI に適用されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-150">After a device is enrolled in SEMM, the configuration file is read and the settings specified in the file are applied to UEFI.</span></span> <span data-ttu-id="83bd0-151">SEMM に既に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名がデバイス ファームウェアに保存されている証明書に対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-151">When you run a configuration package on a device that is already enrolled in SEMM, the signature of the configuration file is checked against the certificate that is stored in the device firmware.</span></span> <span data-ttu-id="83bd0-152">署名が一致しない場合、デバイスに変更は適用されません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-152">If the signature does not match, no changes are applied to the device.</span></span>

### <a name="enable-or-disable-devices-in-surface-uefi-with-semm"></a><span data-ttu-id="83bd0-153">SEMM を使用して Surface UEFI でデバイスを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="83bd0-153">Enable or disable devices in Surface UEFI with SEMM</span></span>

<span data-ttu-id="83bd0-154">次の一覧は、SEMM で管理できる利用可能なすべてのデバイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="83bd0-154">The following list shows all the available devices you can manage in SEMM:</span></span>

* <span data-ttu-id="83bd0-155">USB ポートのドッキング</span><span class="sxs-lookup"><span data-stu-id="83bd0-155">Docking USB Port</span></span>
* <span data-ttu-id="83bd0-156">ボード上のオーディオ</span><span class="sxs-lookup"><span data-stu-id="83bd0-156">On-board Audio</span></span>
* <span data-ttu-id="83bd0-157">DGPU</span><span class="sxs-lookup"><span data-stu-id="83bd0-157">DGPU</span></span>
* <span data-ttu-id="83bd0-158">タイプ カバー</span><span class="sxs-lookup"><span data-stu-id="83bd0-158">Type Cover</span></span>
* <span data-ttu-id="83bd0-159">Micro SD カード</span><span class="sxs-lookup"><span data-stu-id="83bd0-159">Micro SD Card</span></span>
* <span data-ttu-id="83bd0-160">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="83bd0-160">Front Camera</span></span>
* <span data-ttu-id="83bd0-161">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="83bd0-161">Rear Camera</span></span>
* <span data-ttu-id="83bd0-162">Windows Hello 用赤外線カメラ</span><span class="sxs-lookup"><span data-stu-id="83bd0-162">Infrared Camera, for Windows Hello</span></span>
* <span data-ttu-id="83bd0-163">Bluetoothのみ</span><span class="sxs-lookup"><span data-stu-id="83bd0-163">Bluetooth Only</span></span>
* <span data-ttu-id="83bd0-164">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="83bd0-164">Wi-Fi and Bluetooth</span></span>
* <span data-ttu-id="83bd0-165">             LTE           </span><span class="sxs-lookup"><span data-stu-id="83bd0-165">LTE</span></span>

 >[!NOTE]
><span data-ttu-id="83bd0-166">UEFI デバイス ページに表示される組み込みのデバイスは、デバイスまたは企業環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-166">The built-in devices that appear in the UEFI Devices page may vary depending on your device or corporate environment.</span></span> <span data-ttu-id="83bd0-167">たとえば、[UEFI デバイス] ページは Surface Pro X ではサポートされていません。LTE は、LTE 搭載デバイスにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-167">For example, the UEFI Devices page is not supported on Surface Pro X; LTE only appears on LTE-equipped devices.</span></span> 
### <a name="configure-advanced-settings-with-semm"></a><span data-ttu-id="83bd0-168">SEMM を使用して詳細設定を構成する</span><span class="sxs-lookup"><span data-stu-id="83bd0-168">Configure advanced settings with SEMM</span></span>
**<span data-ttu-id="83bd0-169">表 1.</span><span class="sxs-lookup"><span data-stu-id="83bd0-169">Table 1.</span></span> <span data-ttu-id="83bd0-170">詳細設定</span><span class="sxs-lookup"><span data-stu-id="83bd0-170">Advanced settings</span></span>**

| <span data-ttu-id="83bd0-171">設定</span><span class="sxs-lookup"><span data-stu-id="83bd0-171">Setting</span></span>                            | <span data-ttu-id="83bd0-172">説明</span><span class="sxs-lookup"><span data-stu-id="83bd0-172">Description</span></span>                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="83bd0-173">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="83bd0-173">IPv6 for PXE Boot</span></span>                  | <span data-ttu-id="83bd0-174">PXE ブートの IPv6 サポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-174">Allows you to manage IPv6 support for PXE boot.</span></span> <span data-ttu-id="83bd0-175">この設定を構成しない場合、PXE ブートの IPv6 サポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-175">If you do not configure this setting, IPv6 support for PXE boot is disabled.</span></span>                                                                               |
| <span data-ttu-id="83bd0-176">代替ブート</span><span class="sxs-lookup"><span data-stu-id="83bd0-176">Alternate Boot</span></span>                     | <span data-ttu-id="83bd0-177">ブート中に [ボリューム ダウン] ボタンと [電源] ボタンの両方を押して、USB またはイーサネット デバイスに直接起動する代替ブート順序の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-177">Allows you to manage use of an Alternate boot order to boot directly to a USB or Ethernet device by pressing both the Volume Down button and Power button during boot.</span></span> <span data-ttu-id="83bd0-178">この設定を構成しない場合は、代替ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-178">If you do not configure this setting, Alternate boot is enabled.</span></span> |
| <span data-ttu-id="83bd0-179">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="83bd0-179">Boot Order Lock</span></span>                    | <span data-ttu-id="83bd0-180">変更を防ぐためにブート順序をロックできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-180">Allows you to lock the boot order to prevent changes.</span></span> <span data-ttu-id="83bd0-181">この設定を構成しない場合、ブート順序ロックは無効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-181">If you do not configure this setting, Boot Order Lock is disabled.</span></span>                                                                                                        |
| <span data-ttu-id="83bd0-182">USB ブート</span><span class="sxs-lookup"><span data-stu-id="83bd0-182">USB Boot</span></span>                           | <span data-ttu-id="83bd0-183">USB デバイスの起動を管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-183">Allows you to manage booting to USB devices.</span></span> <span data-ttu-id="83bd0-184">この設定を構成しない場合は、USB ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-184">If you do not configure this setting, USB Boot is enabled.</span></span>                                                                                                                 |
| <span data-ttu-id="83bd0-185">ネットワーク スタック</span><span class="sxs-lookup"><span data-stu-id="83bd0-185">Network Stack</span></span>                      | <span data-ttu-id="83bd0-186">ネットワーク スタックのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-186">Allows you to manage Network Stack boot settings.</span></span> <span data-ttu-id="83bd0-187">この設定を構成しない場合、ネットワーク スタックのブート設定を管理する機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-187">If you do not configure this setting,  the ability to manage Network Stack boot settings is disabled.</span></span>                                                                                                           |
| <span data-ttu-id="83bd0-188">自動電源オン</span><span class="sxs-lookup"><span data-stu-id="83bd0-188">Auto Power On</span></span>                      | <span data-ttu-id="83bd0-189">自動電源オンのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-189">Allows you to manage Auto Power On boot settings.</span></span> <span data-ttu-id="83bd0-190">この設定を構成しない場合は、自動電源オンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-190">If you do not configure this setting, Auto Power on is enabled.</span></span>                                                                                                        |
| <span data-ttu-id="83bd0-191">同時マルチスレッド (SMT)</span><span class="sxs-lookup"><span data-stu-id="83bd0-191">Simultaneous Multi-Threading (SMT)</span></span> | <span data-ttu-id="83bd0-192">同時マルチスレッド (SMT) を管理して、ハイパースレッジを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-192">Allows you to manage Simultaneous Multi-Threading (SMT) to enable or disable hyperthreading.</span></span> <span data-ttu-id="83bd0-193">この設定を構成しない場合は、SMT が有効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-193">If you do not configure this setting, SMT is enabled.</span></span>                                                  |
|<span data-ttu-id="83bd0-194">バッテリーの制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="83bd0-194">Enable Battery limit</span></span>| <span data-ttu-id="83bd0-195">バッテリー制限機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-195">Allows you to manage Battery limit functionality.</span></span> <span data-ttu-id="83bd0-196">この設定を構成しない場合は、バッテリーの制限が有効になります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-196">If you do not configure this setting, Battery limit is enabled</span></span> |
| <span data-ttu-id="83bd0-197">Security</span><span class="sxs-lookup"><span data-stu-id="83bd0-197">Security</span></span>                           | <span data-ttu-id="83bd0-198">[Surface UEFI セキュリティ] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-198">Displays the Surface UEFI **Security** page.</span></span> <span data-ttu-id="83bd0-199">この設定を構成しない場合は、[セキュリティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-199">If you do not configure this setting, the Security page is displayed.</span></span>                                                                                                                 |
| <span data-ttu-id="83bd0-200">デバイス</span><span class="sxs-lookup"><span data-stu-id="83bd0-200">Devices</span></span>                            | <span data-ttu-id="83bd0-201">[Surface UEFI デバイス] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-201">Displays the Surface UEFI **Devices** page.</span></span> <span data-ttu-id="83bd0-202">この設定を構成しない場合は、[デバイス] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-202">If you do not configure this setting,  the Devices page is displayed.</span></span>                                                                                                                     |
| <span data-ttu-id="83bd0-203">Boot</span><span class="sxs-lookup"><span data-stu-id="83bd0-203">Boot</span></span>                               | <span data-ttu-id="83bd0-204">[Surface UEFI ブート] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-204">Displays the Surface UEFI **Boot** page.</span></span> <span data-ttu-id="83bd0-205">この設定を構成しない場合は、[ブート] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-205">If you do not configure this setting, the Boot page is displayed.</span></span>                                                                                                                                                            |
| <span data-ttu-id="83bd0-206">DateTime</span><span class="sxs-lookup"><span data-stu-id="83bd0-206">DateTime</span></span>                           | <span data-ttu-id="83bd0-207">Surface UEFI **DateTime ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-207">Displays the Surface UEFI **DateTime** page.</span></span> <span data-ttu-id="83bd0-208">この設定を構成しない場合は、[DateTime] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-208">If you do not configure this setting, the DateTime page is displayed.</span></span>                                                                                                                |
| <span data-ttu-id="83bd0-209">EnableOSMigration</span><span class="sxs-lookup"><span data-stu-id="83bd0-209">EnableOSMigration</span></span>                          | <span data-ttu-id="83bd0-210">Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-210">Allows you to migrate Surface Hub 2 from Windows 10 Team to Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="83bd0-211">この設定を構成しない場合、Surface Hub 2 デバイスは Windows 10 Team OS のみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-211">If you do not configure this setting, Surface Hub 2 devices can only run Windows 10 Team OS.</span></span>   <span data-ttu-id="83bd0-212">注: Windows 10 Team と Windows 10 Pro/Enterprise のデュアル ブートは Surface Hub 2 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-212">Note: Dual booting between Windows 10 Team and Windows 10 Pro/Enterprise  is not available on Surface Hub 2.</span></span>                                                                                                           |


>[!NOTE]
><span data-ttu-id="83bd0-213">SEMM 構成パッケージを作成すると、図 3 に\*\*\*\* 示すように、成功ページに 2 文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-213">When you create a SEMM configuration package, two characters are shown on the **Successful** page, as shown in Figure 3.</span></span>

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*<span data-ttu-id="83bd0-215">図 3. </span><span class="sxs-lookup"><span data-stu-id="83bd0-215">Figure 3.</span></span> <span data-ttu-id="83bd0-216">[成功] ページに証明書の拇印の最後の 2 文字を表示する</span><span class="sxs-lookup"><span data-stu-id="83bd0-216">Display of the last two characters of the certificate thumbprint on the Successful page</span></span>*

<span data-ttu-id="83bd0-217">これらの文字は、証明書の拇印の最後の 2 文字であり、書き込みまたは記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-217">These characters are the last two characters of the certificate thumbprint and should be written down or recorded.</span></span> <span data-ttu-id="83bd0-218">図 4 に示すように、Surface デバイスの SEMM での登録を確認するには、文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-218">The characters are required to confirm enrollment in SEMM on a Surface device, as shown in Figure 4.</span></span>

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*<span data-ttu-id="83bd0-220">図 4: </span><span class="sxs-lookup"><span data-stu-id="83bd0-220">Figure 4.</span></span> <span data-ttu-id="83bd0-221">SEMM 証明書の拇印を使用した SEMM での登録確認</span><span class="sxs-lookup"><span data-stu-id="83bd0-221">Enrollment confirmation in SEMM with the SEMM certificate thumbprint</span></span>*

>[!NOTE]
><span data-ttu-id="83bd0-222">証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開いて、いつでも拇印を読み取りできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-222">Administrators with access to the certificate file (.pfx) can read the thumbprint at any time by opening the .pfx file in CertMgr.</span></span> <span data-ttu-id="83bd0-223">CertMgr を使用して拇印を表示するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="83bd0-223">To view the thumbprint with CertMgr:</span></span> 
>1. <span data-ttu-id="83bd0-224">.pfx ファイルを右クリックし、[開く] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="83bd0-224">Right-click the .pfx file, and then click **Open**.</span></span>
>2. <span data-ttu-id="83bd0-225">ナビゲーション ウィンドウでフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-225">Expand the folder in the navigation pane.</span></span>
>3. <span data-ttu-id="83bd0-226">**[証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83bd0-226">Click **Certificates**.</span></span>
>4. <span data-ttu-id="83bd0-227">メイン ウィンドウで証明書を右クリックし、[開く] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="83bd0-227">Right-click your certificate in the main pane, and then click **Open**.</span></span>
>5. <span data-ttu-id="83bd0-228">[詳細] **タブをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-228">Click the **Details** tab.</span></span>
>6. <span data-ttu-id="83bd0-229">**[表示** ] **ドロップダウン メニュー** で [すべて] または [ **プロパティのみ]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-229">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
>7. <span data-ttu-id="83bd0-230">[拇印] フィールド **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="83bd0-230">Select the field **Thumbprint**.</span></span>

<span data-ttu-id="83bd0-231">SURFACE デバイスを SEMM に登録するか、構成パッケージから UEFI 構成を適用するには、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-231">To enroll a Surface device in SEMM or to apply the UEFI configuration from a configuration package, all you need to do is run the .msi file with administrative privileges on the intended Surface device.</span></span> <span data-ttu-id="83bd0-232">アプリケーション展開またはオペレーティング システム展開テクノロジ[(Microsoft Endpoint Configuration Manager、Microsoft Deployment configuration Manager](https://technet.microsoft.com/library/mt346023)など) を使用[Toolkit。](https://technet.microsoft.com/windows/dn475741)</span><span class="sxs-lookup"><span data-stu-id="83bd0-232">You can use application deployment or operating system deployment technologies such as [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) or the [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741).</span></span> <span data-ttu-id="83bd0-233">SEMM にデバイスを登録する場合は、デバイスの登録を確認するために物理的に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-233">When you enroll a device in SEMM you must be physically present to confirm the enrollment on the device.</span></span> <span data-ttu-id="83bd0-234">SEMM に既に登録されているデバイスに構成を適用する場合、ユーザーの操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-234">User interaction is not required when you apply a configuration to devices that are already enrolled in SEMM.</span></span>

<span data-ttu-id="83bd0-235">SURFACE デバイスを [SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)に登録する方法、または SEMM を使用して Surface UEFI 構成を適用する方法の詳細なチュートリアルについては、「SEMM を使用して Surface デバイスを登録して構成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83bd0-235">For a step-by-step walkthrough of how to enroll a Surface device in SEMM or apply a Surface UEFI configuration with SEMM, see [Enroll and configure Surface devices with SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).</span></span>

### <a name="reset-package"></a><span data-ttu-id="83bd0-236">パッケージのリセット</span><span class="sxs-lookup"><span data-stu-id="83bd0-236">Reset package</span></span>

<span data-ttu-id="83bd0-237">Surface UEFI リセット パッケージは、SEMM から Surface デバイスの登録を解除するために、1 つのタスクのみを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-237">A Surface UEFI reset package is used to perform only one task — to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="83bd0-238">リセット パッケージには、デバイスのファームウェアから SEMM 証明書を削除し、UEFI 設定を出荷時の既定にリセットする署名済み手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="83bd0-238">The reset package contains signed instructions to remove the SEMM certificate from the device’s firmware and to reset UEFI settings to factory default.</span></span> <span data-ttu-id="83bd0-239">Surface UEFI 構成パッケージと同様に、Surface デバイスでプロビジョニングされたのと同じ SEMM 証明書でリセット パッケージに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-239">Like a Surface UEFI configuration package, a reset package must be signed with the same SEMM certificate that is provisioned on the Surface device.</span></span> <span data-ttu-id="83bd0-240">SEMM リセット パッケージを作成する場合は、リセットする Surface デバイスのシリアル番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-240">When you create a SEMM reset package, you are required to supply the serial number of the Surface device you intend to reset.</span></span> <span data-ttu-id="83bd0-241">SEMM リセット パッケージは汎用的ではなく、1 つのデバイスに固有です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-241">SEMM reset packages are not universal and are specific to one device.</span></span>

### <a name="recovery-request"></a><span data-ttu-id="83bd0-242">回復要求</span><span class="sxs-lookup"><span data-stu-id="83bd0-242">Recovery request</span></span>

<span data-ttu-id="83bd0-243">一部のシナリオでは、Surface UEFI リセット パッケージを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-243">In some scenarios, it may be impossible to use a Surface UEFI reset package.</span></span> <span data-ttu-id="83bd0-244">(たとえば、Windows が Surface デバイスで使用できなくなった場合など)。これらのシナリオでは、回復要求操作を使用して、Surface UEFI \*\*\*\* (図 5 に示す) のエンタープライズ管理ページを介して SEMM から Surface デバイスの登録を解除できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-244">(For example, if Windows becomes unusable on the Surface device.) In these scenarios you can unenroll the Surface device from SEMM through the **Enterprise Management** page of Surface UEFI (shown in Figure 5) with a Recovery Request operation.</span></span>

> [!div class="mx-imgBorder"]
> ![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*<span data-ttu-id="83bd0-246">図 5: </span><span class="sxs-lookup"><span data-stu-id="83bd0-246">Figure 5.</span></span> <span data-ttu-id="83bd0-247">[エンタープライズ管理] ページで SEMM 回復要求を開始する</span><span class="sxs-lookup"><span data-stu-id="83bd0-247">Initiate a SEMM recovery request on the Enterprise Management page</span></span>*

<span data-ttu-id="83bd0-248">[エンタープライズ管理] ページの **プロセスを** 使用して Surface デバイスの SEMM をリセットすると、リセット要求が提供されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-248">When you use the process on the **Enterprise Management** page to reset SEMM on a Surface device, you are provided with a Reset Request.</span></span> <span data-ttu-id="83bd0-249">このリセット要求は、ファイルとして USB ドライブに保存したり、テキストとしてコピーしたり、モバイル デバイスを使用して QR コードとして読み取って、電子メールやメッセージを簡単に送信できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-249">This Reset Request can be saved as a file to a USB drive, copied as text, or read as a QR Code with a mobile device to be easily emailed or messaged.</span></span> <span data-ttu-id="83bd0-250">Microsoft Surface UEFI Configurator Reset Request オプションを使用して、要求のリセット ファイルを読み込むか、要求のリセット テキストまたは QR コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-250">Use the Microsoft Surface UEFI Configurator Reset Request option to load a Reset Request file or enter the Reset Request text or QR Code.</span></span> <span data-ttu-id="83bd0-251">Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスで入力できる検証コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-251">Microsoft Surface UEFI Configurator will generate a verification code that can be entered on the Surface device.</span></span> <span data-ttu-id="83bd0-252">Surface デバイスでコードを入力し、[再起動] を **クリック**すると、デバイスは SEMM から登録解除されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-252">If you enter the code on the Surface device and click **Restart**, the device will be unenrolled from SEMM.</span></span> 

>[!NOTE]
><span data-ttu-id="83bd0-253">リセット要求の有効期限は、作成後 2 時間です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-253">A Reset Request expires two hours after it is created.</span></span>

<span data-ttu-id="83bd0-254">SEMM から Surface デバイスの登録を解除する方法の詳細なチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)からの Surface デバイスの登録を解除する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83bd0-254">For a step-by-step walkthrough of how to unenroll Surface devices from SEMM, see [Unenroll Surface devices from SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).</span></span>

## <a name="surface-enterprise-management-mode-certificate-requirements"></a><span data-ttu-id="83bd0-255">Surface Enterprise Management Mode 証明書の要件</span><span class="sxs-lookup"><span data-stu-id="83bd0-255">Surface Enterprise Management Mode certificate requirements</span></span>
<span data-ttu-id="83bd0-256">MICROSOFT Surface UEFI コンフィギュレーターで SEMM を使用するには、UEFI 設定を適用する前に、構成ファイルの署名を確認するための証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-256">Using SEMM with Microsoft Surface UEFI Configurator requires a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="83bd0-257">この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-257">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span>

>[!NOTE]
><span data-ttu-id="83bd0-258">SEMM 証明書は、登録済み Surface デバイスで SEMM または Surface UEFI の設定に対する変更を実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-258">The SEMM certificate is required to perform any modification to SEMM or Surface UEFI settings on enrolled Surface devices.</span></span> <span data-ttu-id="83bd0-259">SEMM 証明書が破損または紛失した場合、SEMM を削除またはリセットすることはできません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-259">If the SEMM certificate is corrupted or lost, SEMM cannot be removed or reset.</span></span> <span data-ttu-id="83bd0-260">バックアップと回復に適したソリューションを使用して、SEMM 証明書を適切に管理します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-260">Manage your SEMM certificate accordingly with an appropriate solution for backup and recovery.</span></span>

<span data-ttu-id="83bd0-261">Microsoft Surface UEFI コンフィギュレーター ツールで作成されたパッケージは、証明書で署名されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-261">Packages created with the Microsoft Surface UEFI Configurator tool are signed with a certificate.</span></span> <span data-ttu-id="83bd0-262">この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-262">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span> 
### <a name="recommended-certificate-settings"></a><span data-ttu-id="83bd0-263">推奨される証明書の設定</span><span class="sxs-lookup"><span data-stu-id="83bd0-263">Recommended certificate settings</span></span>
<span data-ttu-id="83bd0-264">SEMM 証明書には、次の設定が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-264">The following settings are recommended for the SEMM certificate:</span></span>

* <span data-ttu-id="83bd0-265">**キー アルゴリズム** – RSA</span><span class="sxs-lookup"><span data-stu-id="83bd0-265">**Key Algorithm** – RSA</span></span> 
* <span data-ttu-id="83bd0-266">**キーの長** さ – 2048</span><span class="sxs-lookup"><span data-stu-id="83bd0-266">**Key Length** – 2048</span></span>
* <span data-ttu-id="83bd0-267">**ハッシュ アルゴリズム** – SHA-256</span><span class="sxs-lookup"><span data-stu-id="83bd0-267">**Hash Algorithm** – SHA-256</span></span>
* <span data-ttu-id="83bd0-268">**種類** – SSL サーバー認証</span><span class="sxs-lookup"><span data-stu-id="83bd0-268">**Type** – SSL Server Authentication</span></span>
* <span data-ttu-id="83bd0-269">**キー使用法** – デジタル署名、キーエンシファーメント</span><span class="sxs-lookup"><span data-stu-id="83bd0-269">**Key Usage** – Digital signature, Key Encipherment</span></span>
* <span data-ttu-id="83bd0-270">**プロバイダー** – Microsoft Enhanced RSA および AES 暗号化プロバイダー</span><span class="sxs-lookup"><span data-stu-id="83bd0-270">**Provider** – Microsoft Enhanced RSA and AES Cryptographic Provider</span></span>
* <span data-ttu-id="83bd0-271">**有効期限 –** 証明書の作成から 15 か月</span><span class="sxs-lookup"><span data-stu-id="83bd0-271">**Expiration Date** – 15 Months from certificate creation</span></span>
* <span data-ttu-id="83bd0-272">**キーのエクスポート ポリシー** – エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="83bd0-272">**Key Export Policy** – Exportable</span></span>

<span data-ttu-id="83bd0-273">また、中間証明機関 (CA) が SEMM 専用である 2 層公開キー基盤 (PKI) アーキテクチャで SEMM 証明書を認証し、証明書の失効を有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="83bd0-273">It is also recommended that the SEMM certificate be authenticated in a two-tier public key infrastructure (PKI) architecture where the intermediate certification authority (CA) is dedicated to SEMM, enabling certificate revocation.</span></span> <span data-ttu-id="83bd0-274">2 層 PKI 構成の詳細については、「Test Lab Guide: Deploying a AD [CS Two-Tier」を参照してください](https://technet.microsoft.com/library/hh831348)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-274">For more information about a two-tier PKI configuration, see [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://technet.microsoft.com/library/hh831348).</span></span>

### <a name="self-signed-certificate"></a><span data-ttu-id="83bd0-275">自己署名証明書</span><span class="sxs-lookup"><span data-stu-id="83bd0-275">Self-signed certificate</span></span> 
<span data-ttu-id="83bd0-276">次の PowerShell スクリプトの例を使用して、概念実証シナリオで使用する自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-276">You can use the following example PowerShell script to create a self-signed certificate for use in proof-of-concept scenarios.</span></span>
<span data-ttu-id="83bd0-277">このスクリプトを使用するには、次のテキストをメモ帳にコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-277">To use this script, copy the following text into Notepad and save the file as a PowerShell script (.ps1).</span></span> 

> [!NOTE]
> <span data-ttu-id="83bd0-278">このスクリプトは、 のパスワードを持つ証明書を作成します `12345678` 。このスクリプトによって生成される証明書は、実稼働環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-278">This script creates a certificate with a password of `12345678`.The certificate generated by this script is not recommended for production environments.</span></span>
  
```powershell
if (-not (Test-Path "Demo Certificate"))  { New-Item -ItemType Directory -Force -Path "Demo Certificate" }
if (Test-Path "Demo Certificate\TempOwner.pfx") { Remove-Item "Demo Certificate\TempOwner.pfx" }

# Generate the Ownership private signing key with password 12345678
$pw = ConvertTo-SecureString "12345678" -AsPlainText -Force

$TestUefiV2 = New-SelfSignedCertificate `
  -Subject "CN=Surface Demo Kit, O=Contoso Corporation, C=US" `
  -Type SSLServerAuthentication `
  -HashAlgorithm sha256 `
  -KeyAlgorithm RSA `
  -KeyLength 2048 `
  -KeyUsage KeyEncipherment `
  -KeyUsageProperty All `
  -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
  -NotAfter (Get-Date).AddYears(25) `
  -TextExtension @("2.5.29.37={text}1.2.840.113549.1.1.1") `
  -KeyExportPolicy Exportable

$TestUefiV2 | Export-PfxCertificate -Password $pw -FilePath "Demo Certificate\TempOwner.pfx"
```

>[!IMPORTANT]
><span data-ttu-id="83bd0-279">SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書をプライベート キーとパスワード保護でエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-279">For use with SEMM and Microsoft Surface UEFI Configurator, the certificate must be exported with the private key and with password protection.</span></span> <span data-ttu-id="83bd0-280">必要に応じて、SEMM 証明書ファイル (.pfx) と証明書パスワードを選択するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-280">Microsoft Surface UEFI Configurator will prompt you to select the SEMM certificate file (.pfx) and certificate password when it is required.</span></span>

1.  <span data-ttu-id="83bd0-281">スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM。</span><span class="sxs-lookup"><span data-stu-id="83bd0-281">Create a folder on your C: drive where you will save the script; for example, C:\SEMM.</span></span>
2.  <span data-ttu-id="83bd0-282">サンプル スクリプトをメモ帳または同等のテキスト エディターにコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-282">Copy the example script into Notepad or equivalent text editor and save the file as a PowerShell script (.ps1).</span></span>
3.  <span data-ttu-id="83bd0-283">管理者資格情報を使用して PC にサインインし、管理者特権の PowerShell セッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-283">Sign into your PC with administrator credentials and open an elevated PowerShell session.</span></span>
4.  <span data-ttu-id="83bd0-284">スクリプトの実行を許可するアクセス許可が設定されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-284">Ensure your permissions are set to allow scripts to run.</span></span> <span data-ttu-id="83bd0-285">既定では、実行ポリシーを変更しない限り、スクリプトの実行がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-285">By default, scripts are blocked from running unless you modify the execution policy.</span></span> <span data-ttu-id="83bd0-286">詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-286">To learn more, see [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>
5.  <span data-ttu-id="83bd0-287">コマンド プロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-287">At the command prompt, enter the full path of the script and then press Enter.</span></span> <span data-ttu-id="83bd0-288">このスクリプトは、TempOwner.pfx という名前のデモ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="83bd0-288">The script creates a Demo Certificate named TempOwner.pfx.</span></span>

<span data-ttu-id="83bd0-289">または、PowerShell を使用して独自の自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-289">Alternatively, you can create your own self-signed certificate using PowerShell.</span></span> <span data-ttu-id="83bd0-290">詳細については [、「New-SelfSignedCertificate」の PowerShell ドキュメントを参照してください](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。</span><span class="sxs-lookup"><span data-stu-id="83bd0-290">For more information, see the following PowerShell documentation: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).</span></span>




>[!NOTE]
><span data-ttu-id="83bd0-291">PKI インフラストラクチャでオフライン ルートを使用する組織の場合、SEMM 証明書を認証するには、ルート CA に接続された環境で Microsoft Surface UEFI コンフィギュレーターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-291">For organizations that use an offline root in their PKI infrastructure, Microsoft Surface UEFI Configurator must be run in an environment connected to the root CA to authenticate the SEMM certificate.</span></span> <span data-ttu-id="83bd0-292">Microsoft Surface UEFI Configurator によって生成されたパッケージはファイルとして転送されるため、USB スティックなどのリムーバブル ストレージを使用してオフライン ネットワーク環境の外部に転送できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-292">The packages generated by Microsoft Surface UEFI Configurator can be transferred as files and therefore can be transferred outside the offline network environment with removable storage, such as a USB stick.</span></span>

### <a name="managing-certificates-faq"></a><span data-ttu-id="83bd0-293">証明書の管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="83bd0-293">Managing certificates FAQ</span></span>

<span data-ttu-id="83bd0-294">推奨される *最小長* は 15 か月です。</span><span class="sxs-lookup"><span data-stu-id="83bd0-294">The recommended *minimum* length is 15 months.</span></span> <span data-ttu-id="83bd0-295">有効期限が 15 か月未満の証明書を使用するか、15 か月以上経過した証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-295">You can use a certificate that expires in less than 15 months or use a certificate that expires in longer than 15 months.</span></span>

>[!NOTE] 
><span data-ttu-id="83bd0-296">証明書の有効期限が切れると、証明書は自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-296">When a certificate expires, it does not automatically renew.</span></span> 


**<span data-ttu-id="83bd0-297">有効期限が切れた証明書は、SEMM 登録デバイスの機能に影響しますか?</span><span class="sxs-lookup"><span data-stu-id="83bd0-297">Will an expired certificate affect the functionality of SEMM-enrolled devices?</span></span>**<br><br>
<span data-ttu-id="83bd0-298">いいえ、証明書は SEMM の IT 管理者管理タスクにのみ影響し、有効期限が切れるとデバイス機能には影響しません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-298">No, a certificate only impacts IT admin management tasks in SEMM and has no effect on device functionality when it expires.</span></span>


**<span data-ttu-id="83bd0-299">SEMM パッケージと証明書を持つすべてのコンピューターで更新する必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="83bd0-299">Will the SEMM package and certificate need to be updated on all machines that have it?</span></span>**

<span data-ttu-id="83bd0-300">SEMM のリセットまたは回復を機能するには、証明書が有効で有効期限が切れていない必要があります。</span><span class="sxs-lookup"><span data-stu-id="83bd0-300">If you want SEMM reset or recovery to work, the certificate needs to be valid and not expired.</span></span> 

**<span data-ttu-id="83bd0-301">注文したサーフェスごとにパッケージを一括リセットできますか?</span><span class="sxs-lookup"><span data-stu-id="83bd0-301">Can bulk reset packages be created for each surface that we order?</span></span> <span data-ttu-id="83bd0-302">環境内のすべてのコンピューターをリセットするビルドは可能ですか?</span><span class="sxs-lookup"><span data-stu-id="83bd0-302">Can one be built that resets all machines in our environment?</span></span>**

<span data-ttu-id="83bd0-303">特定のデバイスの種類の構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセット パッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-303">The PowerShell samples that create a config package for a specific device type can also be used to create a reset package that is serial-number independent.</span></span> <span data-ttu-id="83bd0-304">証明書がまだ有効な場合は、PowerShell を使用してリセット パッケージを作成して SEMM をリセットできます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-304">If the certificate is still valid, you can create a reset package using PowerShell to reset SEMM.</span></span>

## <a name="version-history"></a><span data-ttu-id="83bd0-305">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="83bd0-305">Version History</span></span>

### <a name="version-2791390"></a><span data-ttu-id="83bd0-306">バージョン 2.79.139.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-306">Version 2.79.139.0</span></span>

<span data-ttu-id="83bd0-307">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-307">This version of SEMM includes:</span></span>
- <span data-ttu-id="83bd0-308">Surface Pro 7+ のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-308">Support for Surface Pro 7+</span></span>
- <span data-ttu-id="83bd0-309">ユーザー エクスペリエンスの向上</span><span class="sxs-lookup"><span data-stu-id="83bd0-309">User experience improvements</span></span>


### <a name="version-2781390"></a><span data-ttu-id="83bd0-310">バージョン 2.78.139.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-310">Version 2.78.139.0</span></span>

<span data-ttu-id="83bd0-311">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-311">This version of SEMM includes:</span></span>

- <span data-ttu-id="83bd0-312">Surface Laptop Go と Surface Pro X のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-312">Support for Surface Laptop Go and Surface Pro X</span></span>
- <span data-ttu-id="83bd0-313">新しいバージョン リリースの通知</span><span class="sxs-lookup"><span data-stu-id="83bd0-313">Notifications for new version release</span></span>
- <span data-ttu-id="83bd0-314">所有権を変更するカスタム パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="83bd0-314">Ability to create custom packages to change ownership</span></span>
- <span data-ttu-id="83bd0-315">バグ修正</span><span class="sxs-lookup"><span data-stu-id="83bd0-315">Bug fixes</span></span>

### <a name="version-2731360"></a><span data-ttu-id="83bd0-316">バージョン 2.73.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-316">Version 2.73.136.0</span></span>

<span data-ttu-id="83bd0-317">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-317">This version of SEMM includes:</span></span>

- <span data-ttu-id="83bd0-318">SEMM を使用して Surface Hub2S でオーディオを無効にできる</span><span class="sxs-lookup"><span data-stu-id="83bd0-318">Audio can now be disabled on Surface Hub2S using SEMM</span></span>
- <span data-ttu-id="83bd0-319">Surface Pro X for Dock 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-319">Support to Surface Pro X for Dock 2</span></span>
- <span data-ttu-id="83bd0-320">ドック 2 関連操作の UEFI マネージャーのサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-320">Support to UEFI Manager for Dock 2 related operations</span></span>
- <span data-ttu-id="83bd0-321">Surface Go リセット パッケージのバグ修正</span><span class="sxs-lookup"><span data-stu-id="83bd0-321">Surface Go reset package bug fix</span></span>
- <span data-ttu-id="83bd0-322">Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行のサポート。</span><span class="sxs-lookup"><span data-stu-id="83bd0-322">Support for migrating Surface Hub 2 devices from Windows 10 Team OS to Windows 10 Pro or Enterprise.</span></span>

### <a name="version-2711390"></a><span data-ttu-id="83bd0-323">バージョン 2.71.139.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-323">Version 2.71.139.0</span></span>

<span data-ttu-id="83bd0-324">このバージョンの SEMM では、Surface Book 3、Surface Laptop 3、Surface Pro 7 の Surface ドック 2 管理機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="83bd0-324">This version of SEMM adds support for Surface Dock 2 management features  for Surface Book 3, Surface Laptop 3, and Surface Pro 7 including:</span></span>

- <span data-ttu-id="83bd0-325">オーディオ (ロック/ロック解除)、イーサネット ポート、USB ポートの有効化</span><span class="sxs-lookup"><span data-stu-id="83bd0-325">Enabling audio (locking/unlocking), Ethernet and USB ports</span></span>
- <span data-ttu-id="83bd0-326">認証済みホストと認証されていないホストの両方にドック パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="83bd0-326">Ability to create dock packages for both authenticated and unauthenticated hosts</span></span>

### <a name="version-2701300"></a><span data-ttu-id="83bd0-327">バージョン 2.70.130.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-327">Version 2.70.130.0</span></span>

<span data-ttu-id="83bd0-328">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83bd0-328">This version of SEMM includes:</span></span>

- <span data-ttu-id="83bd0-329">Surface Go 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-329">Support for Surface Go 2</span></span>
- <span data-ttu-id="83bd0-330">Surface Book 3 のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-330">Support for Surface Book 3</span></span>
- <span data-ttu-id="83bd0-331">バグ修正</span><span class="sxs-lookup"><span data-stu-id="83bd0-331">Bug fixes</span></span>


### <a name="version-2591390"></a><span data-ttu-id="83bd0-332">バージョン 2.59.139.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-332">Version 2.59.139.0</span></span>

* <span data-ttu-id="83bd0-333">Surface Pro 7、Surface Pro X、Surface Laptop 3 13.5" および 15" モデルと Intel プロセッサのサポート。</span><span class="sxs-lookup"><span data-stu-id="83bd0-333">Support for Surface Pro 7, Surface Pro X,  and Surface Laptop 3 13.5" and 15" models with Intel processor.</span></span>

  > [!NOTE]
  > <span data-ttu-id="83bd0-334">Surface Laptop 3 15" AMD プロセッサはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="83bd0-334">Surface Laptop 3 15" AMD processor is not supported.</span></span>

- <span data-ttu-id="83bd0-335">Wake on Power 機能のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-335">Support for Wake on Power feature</span></span>

### <a name="version-2541390"></a><span data-ttu-id="83bd0-336">バージョン 2.54.139.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-336">Version 2.54.139.0</span></span>
* <span data-ttu-id="83bd0-337">Surface Hub 2S のサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-337">Support to Surface Hub 2S</span></span>
* <span data-ttu-id="83bd0-338">バグ修正</span><span class="sxs-lookup"><span data-stu-id="83bd0-338">Bug fixes</span></span>

### <a name="version-2431360"></a><span data-ttu-id="83bd0-339">バージョン 2.43.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-339">Version 2.43.136.0</span></span>
* <span data-ttu-id="83bd0-340">マルチスレティングのシミュレーションを有効/無効にするサポート</span><span class="sxs-lookup"><span data-stu-id="83bd0-340">Support to enable/disable simulatenous multithreating</span></span> 
* <span data-ttu-id="83bd0-341">一部のデバイスで WiFi と Bluetoothのオプションを分離する</span><span class="sxs-lookup"><span data-stu-id="83bd0-341">Separate options for WiFi and Bluetooth for some devices</span></span> 
* <span data-ttu-id="83bd0-342">Surface Studio のバッテリー制限が削除されました</span><span class="sxs-lookup"><span data-stu-id="83bd0-342">Battery Limit removed for Surface Studio</span></span> 

### <a name="version-2261360"></a><span data-ttu-id="83bd0-343">バージョン 2.26.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-343">Version 2.26.136.0</span></span>
* <span data-ttu-id="83bd0-344">Surface Studio 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-344">Add support to Surface Studio 2</span></span>
* <span data-ttu-id="83bd0-345">バッテリー制限機能</span><span class="sxs-lookup"><span data-stu-id="83bd0-345">Battery Limit feature</span></span>

### <a name="version-2211360"></a><span data-ttu-id="83bd0-346">バージョン 2.21.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-346">Version 2.21.136.0</span></span>
* <span data-ttu-id="83bd0-347">Surface Pro 6 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-347">Add support to Surface Pro 6</span></span>
* <span data-ttu-id="83bd0-348">Surface Laptop 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-348">Add support to Surface Laptop 2</span></span>

### <a name="version-2141360"></a><span data-ttu-id="83bd0-349">バージョン 2.14.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-349">Version 2.14.136.0</span></span>
* <span data-ttu-id="83bd0-350">Surface Go へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-350">Add support to Surface Go</span></span>

### <a name="version-291360"></a><span data-ttu-id="83bd0-351">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-351">Version 2.9.136.0</span></span>
* <span data-ttu-id="83bd0-352">Surface Book 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-352">Add support to Surface Book 2</span></span>
* <span data-ttu-id="83bd0-353">Surface Pro LTE へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-353">Add support to Surface Pro LTE</span></span>
* <span data-ttu-id="83bd0-354">アクセシビリティの改善</span><span class="sxs-lookup"><span data-stu-id="83bd0-354">Accessibility improvements</span></span>

### <a name="version-10740"></a><span data-ttu-id="83bd0-355">バージョン 1.0.74.0</span><span class="sxs-lookup"><span data-stu-id="83bd0-355">Version 1.0.74.0</span></span>
* <span data-ttu-id="83bd0-356">Surface Laptop へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-356">Add support to Surface Laptop</span></span>
* <span data-ttu-id="83bd0-357">Surface Pro へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="83bd0-357">Add support to Surface Pro</span></span>
* <span data-ttu-id="83bd0-358">バグ修正と一般的な改善</span><span class="sxs-lookup"><span data-stu-id="83bd0-358">Bug fixes and general improvement</span></span>

## <a name="related-topics"></a><span data-ttu-id="83bd0-359">関連トピック</span><span class="sxs-lookup"><span data-stu-id="83bd0-359">Related topics</span></span>

- [<span data-ttu-id="83bd0-360">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="83bd0-360">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)
- [<span data-ttu-id="83bd0-361">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="83bd0-361">Unenroll Surface devices from SEMM</span></span>](unenroll-surface-devices-from-semm.md)
- [<span data-ttu-id="83bd0-362">SEMM を使用して Surface Dock 2 ポートを保護する</span><span class="sxs-lookup"><span data-stu-id="83bd0-362">Secure Surface Dock 2 ports with SEMM</span></span>](secure-surface-dock-ports-semm.md)
