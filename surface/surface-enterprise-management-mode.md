---
title: Surface Enterprise管理モード (Surface)
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
ms.date: 04/16/2021
ms.openlocfilehash: 3c7eea524daa3210a329c41536f4c47a2c012bcf
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576587"
---
# <a name="microsoft-surface-enterprise-management-mode"></a><span data-ttu-id="48857-104">Microsoft Surface Enterprise管理モード</span><span class="sxs-lookup"><span data-stu-id="48857-104">Microsoft Surface Enterprise Management Mode</span></span>

<span data-ttu-id="48857-105">Microsoft Surface Enterprise管理モード (SEMM) は、Surface Unified 拡張可能ファームウェア インターフェイス (UEFI) を備えた Surface デバイスの機能です。</span><span class="sxs-lookup"><span data-stu-id="48857-105">Microsoft Surface Enterprise Management Mode (SEMM) is a feature of Surface devices with Surface Unified Extensible Firmware Interface (UEFI).</span></span> <span data-ttu-id="48857-106">SEMM を使用すると、次の場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="48857-106">You can use SEMM to:</span></span>

- <span data-ttu-id="48857-107">組織内のファームウェア設定をセキュリティで保護し、管理します。</span><span class="sxs-lookup"><span data-stu-id="48857-107">Secure and manage firmware settings in your organization.</span></span>
- <span data-ttu-id="48857-108">UEFI 設定の構成を準備し、Surface デバイスにインストールします。</span><span class="sxs-lookup"><span data-stu-id="48857-108">Prepare UEFI settings configurations and install them on a Surface device.</span></span> 

<span data-ttu-id="48857-109">また、SEMM は証明書を使用して、承認されていない改ざんや削除から構成を保護します。</span><span class="sxs-lookup"><span data-stu-id="48857-109">SEMM also uses a certificate to protect the configuration from unauthorized tampering or removal.</span></span> <span data-ttu-id="48857-110">2S を 2S Surface HubまたはWindows 10 ProにWindows Enterpriseするには、SEMM が必要です。</span><span class="sxs-lookup"><span data-stu-id="48857-110">To migrate a Surface Hub 2S to Windows 10 Pro or Windows Enterprise, SEMM is required.</span></span>

>[!NOTE]
><span data-ttu-id="48857-111">SEMM は Surface UEFI ファームウェアを持つデバイスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="48857-111">SEMM is only available on devices with Surface UEFI firmware.</span></span> <span data-ttu-id="48857-112">これには、intel プロセッサを搭載した Surface Pro 7+、Surface Pro X、Surface Hub 2S、Surface Laptop 4 商用 SKU、AMD プロセッサを搭載した Surface Laptop 4 の商用 SKU、Intel プロセッサを搭載した Surface Laptop 3 の商用 SKU、Surface Laptop Go など、他のほとんどの Surface デバイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-112">This includes most other Surface devices including Surface Pro 7+, Surface Pro X, Surface Hub 2S, Surface Laptop 4 commercial SKUs with an Intel processor, Surface Laptop 4 commercial SKUs with AMD processor, Surface Laptop 3 commercial SKUs with an Intel processor, and Surface Laptop Go.</span></span> <span data-ttu-id="48857-113">SEMM は、AMD プロセッサを使用した 15" Surface Laptop 3 SKU ではサポートされていません (小売 SKU としてのみ利用可能)。</span><span class="sxs-lookup"><span data-stu-id="48857-113">SEMM is not supported on the 15" Surface Laptop 3 SKU with AMD processor (available only as a retail SKU).</span></span> 

<span data-ttu-id="48857-114">Surface デバイスが SEMM によって構成され、SEMM 証明書で保護されている場合、デバイスは SEMM *に登録されたと* 見なされます。</span><span class="sxs-lookup"><span data-stu-id="48857-114">When Surface devices are configured by SEMM and secured with the SEMM certificate, they're considered *enrolled* in SEMM.</span></span> <span data-ttu-id="48857-115">SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM で登録されていない *と* 見なされます。</span><span class="sxs-lookup"><span data-stu-id="48857-115">When the SEMM certificate is removed and control of UEFI settings is returned to the user of the device, the Surface device is considered *unenrolled* in SEMM.</span></span>

<span data-ttu-id="48857-116">SEMM の管理と Surface デバイスの登録には、次の 2 つの管理オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="48857-116">There are two administrative options that you can use to manage SEMM and enroll Surface devices:</span></span>

- <span data-ttu-id="48857-117">SEMM スタンドアロン ツールである Microsoft Surface UEFI コンフィギュレーターについて、この記事で説明します。</span><span class="sxs-lookup"><span data-stu-id="48857-117">SEMM standalone tool, Microsoft Surface UEFI Configurator, is described in this article.</span></span> 

- <span data-ttu-id="48857-118">ユーザーとのMicrosoft Endpoint Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="48857-118">Integration with Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="48857-119">詳細については、「デバイスを[SEMM で管理Microsoft Endpoint Configuration Managerを使用する」を参照してください](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)。</span><span class="sxs-lookup"><span data-stu-id="48857-119">For information, see [Use Microsoft Endpoint Configuration Manager to manage devices with SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).</span></span>

> [!NOTE]
> <span data-ttu-id="48857-120">SEMM は、UEFI マネージャー Surface Pro X でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="48857-120">SEMM is supported on Surface Pro X via the UEFI Manager only.</span></span> <span data-ttu-id="48857-121">IT 向け Surface Tools から UEFI [マネージャーをダウンロードできます](https://www.microsoft.com/download/details.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="48857-121">You can download UEFI Manager from [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> <span data-ttu-id="48857-122">詳細については、「X の展開、管理、およびサービス[Surface Pro参照してください](surface-pro-arm-app-management.md)。</span><span class="sxs-lookup"><span data-stu-id="48857-122">For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>


## <a name="microsoft-surface-uefi-configurator"></a><span data-ttu-id="48857-123">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="48857-123">Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="48857-124">図 1 に示すように、SEMM のプライマリ ワークスペースは Microsoft Surface UEFI コンフィギュレーターです。</span><span class="sxs-lookup"><span data-stu-id="48857-124">The primary workspace of SEMM is Microsoft Surface UEFI Configurator, as shown in Figure 1.</span></span> 

<span data-ttu-id="48857-125">Microsoft Surface UEFI コンフィギュレーターを使用すると、次の手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="48857-125">You can use Microsoft Surface UEFI Configurator to:</span></span>

- <span data-ttu-id="48857-126">インストーラー (Windows) パッケージを.msiします。</span><span class="sxs-lookup"><span data-stu-id="48857-126">Create Windows Installer (.msi) packages.</span></span>
- <span data-ttu-id="48857-127">WinPE イメージを使用して、Surface デバイスに SEMM を登録、構成、および登録解除します。</span><span class="sxs-lookup"><span data-stu-id="48857-127">Use WinPE images to enroll, configure, and unenroll SEMM on a Surface device.</span></span> 

<span data-ttu-id="48857-128">これらのパッケージには、UEFI 設定を指定する構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="48857-128">These packages contain a configuration file that specifies the UEFI settings.</span></span> <span data-ttu-id="48857-129">SEMM パッケージには、ファームウェアにインストールおよび保存されている証明書も含まれています。UEFI 設定を適用する前に構成ファイルの署名を確認するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="48857-129">SEMM packages also contain a certificate that's installed and stored in firmware and is used to verify the signature of configuration files before UEFI settings are applied.</span></span>

>[!TIP]
><span data-ttu-id="48857-130">Surface UEFI コンフィギュレーターと SEMM を使用して、Surface ドック 2 のポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-130">You can now use Surface UEFI Configurator and SEMM to manage ports on Surface Dock 2.</span></span> <span data-ttu-id="48857-131">詳細については [、「Secure Surface Dock 2 ports with SEMM」を参照してください](secure-surface-dock-ports-semm.md)。</span><span class="sxs-lookup"><span data-stu-id="48857-131">To learn more, see [Secure Surface Dock 2 ports with SEMM](secure-surface-dock-ports-semm.md).</span></span>

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*<span data-ttu-id="48857-133">図 1.</span><span class="sxs-lookup"><span data-stu-id="48857-133">Figure 1.</span></span> <span data-ttu-id="48857-134">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="48857-134">Microsoft Surface UEFI Configurator</span></span>*

<span data-ttu-id="48857-135">Microsoft Surface UEFI コンフィギュレーター ツールは、次の 3 つのモードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="48857-135">You can use the Microsoft Surface UEFI Configurator tool in three modes:</span></span>

- <span data-ttu-id="48857-136">[Surface UEFI 構成パッケージ](#configuration-package)。</span><span class="sxs-lookup"><span data-stu-id="48857-136">[Surface UEFI Configuration Package](#configuration-package).</span></span> <span data-ttu-id="48857-137">このモードを使用して、Surface UEFI 構成パッケージを作成して、Surface デバイスを SEMM に登録し、登録済みデバイスで UEFI 設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="48857-137">Use this mode to create a Surface UEFI configuration package to enroll a Surface device in SEMM and to configure UEFI settings on enrolled devices.</span></span>
- <span data-ttu-id="48857-138">[Surface UEFI リセット パッケージ](#reset-package)。</span><span class="sxs-lookup"><span data-stu-id="48857-138">[Surface UEFI Reset Package](#reset-package).</span></span> <span data-ttu-id="48857-139">SEMM から Surface デバイスの登録を解除するには、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="48857-139">Use this mode to unenroll a Surface device from SEMM.</span></span>
- <span data-ttu-id="48857-140">[Surface UEFI 回復要求](#recovery-request)。</span><span class="sxs-lookup"><span data-stu-id="48857-140">[Surface UEFI Recovery Request](#recovery-request).</span></span> <span data-ttu-id="48857-141">このモードを使用して、回復要求に応答して、パッケージのリセット操作が成功しない SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="48857-141">Use this mode to respond to a recovery request to unenroll a Surface device from SEMM where a Reset Package operation is not successful.</span></span>

#### <a name="download-microsoft-surface-uefi-configurator"></a><span data-ttu-id="48857-142">Microsoft Surface UEFI コンフィギュレーターをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="48857-142">Download Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="48857-143">Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロード センターの [[Surface Tools for IT]](https://www.microsoft.com/download/details.aspx?id=46703) ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="48857-143">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

### <a name="configuration-package"></a><span data-ttu-id="48857-144">構成パッケージ</span><span class="sxs-lookup"><span data-stu-id="48857-144">Configuration package</span></span>

<span data-ttu-id="48857-145">Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装および管理するための主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="48857-145">Surface UEFI configuration packages are the primary mechanism to implement and manage SEMM on Surface devices.</span></span> <span data-ttu-id="48857-146">図 2 に示すように、これらのパッケージには構成ファイルと証明書ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="48857-146">These packages contain a configuration file and a certificate file, as shown in Figure 2.</span></span> <span data-ttu-id="48857-147">構成ファイルには、パッケージが Microsoft Surface UEFI Configurationator で作成される際に指定される UEFI 設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="48857-147">The configuration file contains UEFI settings that are specified when the package is created in Microsoft Surface UEFI Configurator.</span></span> <span data-ttu-id="48857-148">SEMM に登録されていない Surface デバイスで構成パッケージが初めて実行されると、デバイスのファームウェアに証明書ファイルがプロビジョニングされ、デバイスが SEMM に登録されます。</span><span class="sxs-lookup"><span data-stu-id="48857-148">When a configuration package runs for the first time on a Surface device that's not already enrolled in SEMM, it provisions the certificate file in the device’s firmware and enrolls the device in SEMM.</span></span> <span data-ttu-id="48857-149">SEMM にデバイスを登録し、証明書が保存され、登録が完了する前に、SEMM 証明書の拇印の最後の 2 桁を指定して操作を確認するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-149">When enrolling a device in SEMM, and before the certificate is stored and the enrollment finishes, you're prompted to confirm the operation by providing the last two digits of the SEMM certificate thumbprint.</span></span> <span data-ttu-id="48857-150">この確認を実行するには、登録中にユーザーがデバイスに物理的に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-150">This confirmation requires a user to be physically present at the device during enrollment to perform the confirmation.</span></span>

![証明書を使用して SEMM 構成パッケージをセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*<span data-ttu-id="48857-152">図 2.</span><span class="sxs-lookup"><span data-stu-id="48857-152">Figure 2.</span></span> <span data-ttu-id="48857-153">証明書を使用して SEMM 構成パッケージをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="48857-153">Secure a SEMM configuration package with a certificate</span></span>*

<span data-ttu-id="48857-154">SEMM 証明書の要件の詳細については、この記事の後半の[「Surface](#surface-enterprise-management-mode-certificate-requirements) Enterprise管理モード証明書の要件」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48857-154">For more information about the requirements for the SEMM certificate, see the [Surface Enterprise Management Mode certificate requirements](#surface-enterprise-management-mode-certificate-requirements) section later in this article.</span></span>

>[!TIP]
><span data-ttu-id="48857-155">SEMM で UEFI パスワードを要求するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="48857-155">You have the option to require a UEFI password with SEMM.</span></span> <span data-ttu-id="48857-156">これを行う場合は、Surface UEFI\*\*\*\* のセキュリティ\*\*\*\*、デバイス\*\*\*\*、ブート構成、および Enterprise**管理**ページを表示するためにパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="48857-156">If you do, the password is required to view the **Security**, **Devices**, **Boot Configuration**, and **Enterprise Management** pages of Surface UEFI.</span></span>

<span data-ttu-id="48857-157">デバイスが SEMM に登録されると、構成ファイルが読み取り、ファイルで指定された設定が UEFI に適用されます。</span><span class="sxs-lookup"><span data-stu-id="48857-157">After a device is enrolled in SEMM, the configuration file is read, and the settings specified in the file are applied to UEFI.</span></span> <span data-ttu-id="48857-158">SEMM に既に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名がデバイス のファームウェアに保存されている証明書に対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="48857-158">When you run a configuration package on a device that's already enrolled in SEMM, the signature of the configuration file is checked against the certificate that's stored in the device firmware.</span></span> <span data-ttu-id="48857-159">署名が一致しない場合、デバイスに変更は適用されません。</span><span class="sxs-lookup"><span data-stu-id="48857-159">If the signature doesn't match, no changes are applied to the device.</span></span>

### <a name="enable-or-disable-devices-in-surface-uefi-with-semm"></a><span data-ttu-id="48857-160">SEMM を使用して Surface UEFI でデバイスを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="48857-160">Enable or disable devices in Surface UEFI with SEMM</span></span>

<span data-ttu-id="48857-161">次の一覧は、SEMM で管理できる利用可能なすべてのデバイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="48857-161">The following list shows all the available devices that you can manage in SEMM:</span></span>

- <span data-ttu-id="48857-162">USB ポートのドッキング</span><span class="sxs-lookup"><span data-stu-id="48857-162">Docking USB port</span></span>
- <span data-ttu-id="48857-163">ボード上のオーディオ</span><span class="sxs-lookup"><span data-stu-id="48857-163">On-board audio</span></span>
- <span data-ttu-id="48857-164">デジタル グラフィックス処理ユニット</span><span class="sxs-lookup"><span data-stu-id="48857-164">Digital graphics processing unit</span></span>
- <span data-ttu-id="48857-165">タイプ カバー</span><span class="sxs-lookup"><span data-stu-id="48857-165">Type cover</span></span>
- <span data-ttu-id="48857-166">Micro SD カード</span><span class="sxs-lookup"><span data-stu-id="48857-166">Micro SD card</span></span>
- <span data-ttu-id="48857-167">フロント カメラ</span><span class="sxs-lookup"><span data-stu-id="48857-167">Front camera</span></span>
- <span data-ttu-id="48857-168">リア カメラ</span><span class="sxs-lookup"><span data-stu-id="48857-168">Rear camera</span></span>
- <span data-ttu-id="48857-169">赤外線カメラ (Windows Hello 用)</span><span class="sxs-lookup"><span data-stu-id="48857-169">Infrared camera (for Windows Hello)</span></span>
- <span data-ttu-id="48857-170">Bluetoothのみ</span><span class="sxs-lookup"><span data-stu-id="48857-170">Bluetooth only</span></span>
- <span data-ttu-id="48857-171">ワイヤレス ネットワークとBluetooth</span><span class="sxs-lookup"><span data-stu-id="48857-171">Wireless network and Bluetooth</span></span>
- <span data-ttu-id="48857-172">長期的な進化 (LTE)</span><span class="sxs-lookup"><span data-stu-id="48857-172">Long-term evolution (LTE)</span></span>

 >[!NOTE]
><span data-ttu-id="48857-173">[UEFI デバイス] ページでは、組み込みのデバイスは、デバイスまたは企業環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="48857-173">On the UEFI Devices page, the built-in devices might vary, depending on your device or corporate environment.</span></span> <span data-ttu-id="48857-174">たとえば、[UEFI デバイス] ページは X ではSurface Proされません。LTE は、LTE 搭載デバイスでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-174">For example, the UEFI Devices page isn't supported on Surface Pro X; LTE appears only on LTE-equipped devices.</span></span> 
### <a name="configure-advanced-settings-with-semm"></a><span data-ttu-id="48857-175">SEMM を使用して詳細設定を構成する</span><span class="sxs-lookup"><span data-stu-id="48857-175">Configure advanced settings with SEMM</span></span>
**<span data-ttu-id="48857-176">表 1.</span><span class="sxs-lookup"><span data-stu-id="48857-176">Table 1.</span></span> <span data-ttu-id="48857-177">詳細設定</span><span class="sxs-lookup"><span data-stu-id="48857-177">Advanced settings</span></span>**

| <span data-ttu-id="48857-178">設定</span><span class="sxs-lookup"><span data-stu-id="48857-178">Setting</span></span>                            | <span data-ttu-id="48857-179">説明</span><span class="sxs-lookup"><span data-stu-id="48857-179">Description</span></span>                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="48857-180">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="48857-180">IPv6 for PXE Boot</span></span>                  | <span data-ttu-id="48857-181">PXE ブートの IPv6 サポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-181">Allows you to manage IPv6 support for PXE boot.</span></span> <span data-ttu-id="48857-182">この設定を構成しない場合、PXE ブートの IPv6 サポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-182">If you don't configure this setting, IPv6 support for PXE boot is disabled.</span></span>                                                                               |
| <span data-ttu-id="48857-183">代替ブート</span><span class="sxs-lookup"><span data-stu-id="48857-183">Alternate Boot</span></span>                     | <span data-ttu-id="48857-184">ブート中に [ボリューム ダウン] ボタンと [電源] ボタンの両方を押して、USB またはイーサネット デバイスに直接起動する代替ブート注文の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-184">Allows you to manage the use of an Alternate boot order to boot directly to a USB or Ethernet device by pressing both the Volume Down button and Power button during boot.</span></span> <span data-ttu-id="48857-185">この設定を構成しない場合は、代替ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-185">If you don't configure this setting, Alternate boot is enabled.</span></span> |
| <span data-ttu-id="48857-186">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="48857-186">Boot Order Lock</span></span>                    | <span data-ttu-id="48857-187">変更を防ぐためにブート順序をロックできます。</span><span class="sxs-lookup"><span data-stu-id="48857-187">Allows you to lock the boot order to prevent changes.</span></span> <span data-ttu-id="48857-188">この設定を構成しない場合、ブート順序ロックは無効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-188">If you don't configure this setting, Boot Order Lock is disabled.</span></span>                                                                                                        |
| <span data-ttu-id="48857-189">USB ブート</span><span class="sxs-lookup"><span data-stu-id="48857-189">USB Boot</span></span>                           | <span data-ttu-id="48857-190">USB デバイスの起動を管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-190">Allows you to manage booting to USB devices.</span></span> <span data-ttu-id="48857-191">この設定を構成しない場合は、USB ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-191">If you don't configure this setting, USB Boot is enabled.</span></span>                                                                                                                 |
| <span data-ttu-id="48857-192">ネットワーク スタック</span><span class="sxs-lookup"><span data-stu-id="48857-192">Network Stack</span></span>                      | <span data-ttu-id="48857-193">ネットワーク スタックのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-193">Allows you to manage Network Stack boot settings.</span></span> <span data-ttu-id="48857-194">この設定を構成しない場合、ネットワーク スタックのブート設定を管理する機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-194">If you don't configure this setting,  the ability to manage Network Stack boot settings is disabled.</span></span>                                                                                                           |
| <span data-ttu-id="48857-195">自動電源オン</span><span class="sxs-lookup"><span data-stu-id="48857-195">Auto Power On</span></span>                      | <span data-ttu-id="48857-196">自動電源オンのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-196">Allows you to manage Auto Power On boot settings.</span></span> <span data-ttu-id="48857-197">この設定を構成しない場合は、自動電源オンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-197">If you don't configure this setting, Auto Power on is enabled.</span></span>                                                                                                        |
| <span data-ttu-id="48857-198">同時マルチスレッド (SMT)</span><span class="sxs-lookup"><span data-stu-id="48857-198">Simultaneous Multi-Threading (SMT)</span></span> | <span data-ttu-id="48857-199">同時マルチスレッド (SMT) を管理して、ハイパースレッジを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="48857-199">Allows you to manage Simultaneous Multi-Threading (SMT) to enable or disable hyperthreading.</span></span> <span data-ttu-id="48857-200">この設定を構成しない場合は、SMT が有効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-200">If you don't configure this setting, SMT is enabled.</span></span>                                                  |
|<span data-ttu-id="48857-201">バッテリーの制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="48857-201">Enable Battery limit</span></span>| <span data-ttu-id="48857-202">バッテリー制限機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="48857-202">Allows you to manage Battery limit functionality.</span></span> <span data-ttu-id="48857-203">この設定を構成しない場合は、バッテリーの制限が有効になります。</span><span class="sxs-lookup"><span data-stu-id="48857-203">If you don't configure this setting, Battery limit is enabled</span></span> |
| <span data-ttu-id="48857-204">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="48857-204">Security</span></span>                           | <span data-ttu-id="48857-205">[Surface UEFI セキュリティ] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="48857-205">Displays the Surface UEFI **Security** page.</span></span> <span data-ttu-id="48857-206">この設定を構成しない場合は、[セキュリティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-206">If you don't configure this setting, the Security page is displayed.</span></span>                                                                                                                 |
| <span data-ttu-id="48857-207">デバイス</span><span class="sxs-lookup"><span data-stu-id="48857-207">Devices</span></span>                            | <span data-ttu-id="48857-208">[Surface UEFI デバイス] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="48857-208">Displays the Surface UEFI **Devices** page.</span></span> <span data-ttu-id="48857-209">この設定を構成しない場合は、[デバイス] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-209">If you don't configure this setting,  the Devices page is displayed.</span></span>                                                                                                                     |
| <span data-ttu-id="48857-210">Boot</span><span class="sxs-lookup"><span data-stu-id="48857-210">Boot</span></span>                               | <span data-ttu-id="48857-211">[Surface UEFI ブート] **ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="48857-211">Displays the Surface UEFI **Boot** page.</span></span> <span data-ttu-id="48857-212">この設定を構成しない場合は、[ブート] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-212">If you don't configure this setting, the Boot page is displayed.</span></span>                                                                                                                                                            |
| <span data-ttu-id="48857-213">DateTime</span><span class="sxs-lookup"><span data-stu-id="48857-213">DateTime</span></span>                           | <span data-ttu-id="48857-214">Surface UEFI **DateTime ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="48857-214">Displays the Surface UEFI **DateTime** page.</span></span> <span data-ttu-id="48857-215">この設定を構成しない場合は、[DateTime] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-215">If you don't configure this setting, the DateTime page is displayed.</span></span>                                                                                                                |
| <span data-ttu-id="48857-216">EnableOSMigration</span><span class="sxs-lookup"><span data-stu-id="48857-216">EnableOSMigration</span></span>                          | <span data-ttu-id="48857-217">2 から 2 にSurface Hubして、Windows 10 TeamまたはWindows 10 ProにEnterprise。</span><span class="sxs-lookup"><span data-stu-id="48857-217">Allows you to migrate Surface Hub 2 from Windows 10 Team to Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="48857-218">この設定を構成しない場合は、Surface Hub 2 台のデバイスで OS Windows 10 Teamできます。</span><span class="sxs-lookup"><span data-stu-id="48857-218">If you don't configure this setting, Surface Hub 2 devices can run only the Windows 10 Team OS.</span></span> <span data-ttu-id="48857-219">注: 2 では、Windows 10 Teamと Windows 10 Pro/Enterpriseのデュアル ブートSurface Hubできません。</span><span class="sxs-lookup"><span data-stu-id="48857-219">Note: Dual booting between Windows 10 Team and Windows 10 Pro/Enterprise isn't available on Surface Hub 2.</span></span>                                                                                                           |


>[!NOTE]
><span data-ttu-id="48857-220">SEMM 構成パッケージを作成すると、図 3 に\*\*\*\* 示すように、成功ページに 2 文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-220">When you create a SEMM configuration package, two characters are shown on the **Successful** page, as shown in Figure 3.</span></span>

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*<span data-ttu-id="48857-222">図 3. </span><span class="sxs-lookup"><span data-stu-id="48857-222">Figure 3.</span></span> <span data-ttu-id="48857-223">[成功] ページに証明書の拇印の最後の 2 文字を表示する</span><span class="sxs-lookup"><span data-stu-id="48857-223">Display of the last two characters of the certificate thumbprint on the Successful page</span></span>*

<span data-ttu-id="48857-224">これらの文字は、証明書の拇印の最後の 2 文字であり、書き込みまたは記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-224">These characters are the last two characters of the certificate thumbprint and should be written down or recorded.</span></span> <span data-ttu-id="48857-225">図 4 に示すように、Surface デバイスの SEMM での登録を確認するには、文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="48857-225">The characters are required to confirm enrollment in SEMM on a Surface device, as shown in Figure 4.</span></span>

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*<span data-ttu-id="48857-227">図 4: </span><span class="sxs-lookup"><span data-stu-id="48857-227">Figure 4.</span></span> <span data-ttu-id="48857-228">SEMM 証明書の拇印を使用した SEMM での登録確認</span><span class="sxs-lookup"><span data-stu-id="48857-228">Enrollment confirmation in SEMM with the SEMM certificate thumbprint</span></span>*

>[!NOTE]
><span data-ttu-id="48857-229">証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開いて、いつでも拇印を読み取りできます。</span><span class="sxs-lookup"><span data-stu-id="48857-229">Administrators with access to the certificate file (.pfx) can read the thumbprint at any time by opening the .pfx file in CertMgr.</span></span> <span data-ttu-id="48857-230">CertMgr を使用して拇印を表示するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="48857-230">To view the thumbprint with CertMgr:</span></span>
>1. <span data-ttu-id="48857-231">.pfx ファイルを選択して保持 (または右クリック) し、[開く] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="48857-231">Select and hold (or right-click) the .pfx file, and then select **Open**.</span></span>
>2. <span data-ttu-id="48857-232">ナビゲーション ウィンドウで、フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="48857-232">In the navigation pane, expand the folder.</span></span>
>3. <span data-ttu-id="48857-233">[証明書 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="48857-233">Select **Certificates**.</span></span>
>4. <span data-ttu-id="48857-234">メイン ウィンドウで、証明書を選択して保持 (または右クリック) し、[開く] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="48857-234">In the main pane, select and hold (or right-click) your certificate, and then select **Open**.</span></span>
>5. <span data-ttu-id="48857-235">[詳細] **タブを選択** します。</span><span class="sxs-lookup"><span data-stu-id="48857-235">Select the **Details** tab.</span></span>
>6. <span data-ttu-id="48857-236">[表示 **] ドロップダウン**メニューで、[**すべて] または [\*\*\*\*プロパティのみ]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-236">In the **Show** drop-down menu, **All** or **Properties Only** must be selected.</span></span>
>7. <span data-ttu-id="48857-237">[拇 **印] フィールドを** 選択します。</span><span class="sxs-lookup"><span data-stu-id="48857-237">Select the **Thumbprint** field.</span></span>

<span data-ttu-id="48857-238">Surface デバイスを SEMM に登録するか、構成パッケージから UEFI 構成を適用するには、目的の Surface デバイスに対する管理特権を持つ .msi ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="48857-238">To enroll a Surface device in SEMM or apply the UEFI configuration from a configuration package, run the .msi file with administrative privileges on the intended Surface device.</span></span> <span data-ttu-id="48857-239">アプリケーションの展開やオペレーティング システムの展開テクノロジ (Microsoft Endpoint Configuration Manager Microsoft Deployment [Toolkit) を使用できます](https://technet.microsoft.com/windows/dn475741)。 [](https://technet.microsoft.com/library/mt346023)</span><span class="sxs-lookup"><span data-stu-id="48857-239">You can use application deployment or operating system deployment technologies, like [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) or the [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741).</span></span> <span data-ttu-id="48857-240">SEMM にデバイスを登録する場合は、デバイスの登録を確認するために物理的に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-240">When you enroll a device in SEMM, you must be physically present to confirm the enrollment on the device.</span></span> <span data-ttu-id="48857-241">SEMM に既に登録されているデバイスに構成を適用する場合、ユーザー操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="48857-241">When you apply a configuration to devices that are already enrolled in SEMM, user interaction isn’t required.</span></span>

<span data-ttu-id="48857-242">SURFACE デバイスを [SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)に登録する方法、または SEMM を使用して Surface UEFI 構成を適用する方法の詳細なチュートリアルについては、「SEMM を使用して Surface デバイスを登録して構成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48857-242">For a step-by-step walkthrough of how to enroll a Surface device in SEMM or apply a Surface UEFI configuration with SEMM, see [Enroll and configure Surface devices with SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).</span></span>

### <a name="reset-package"></a><span data-ttu-id="48857-243">パッケージのリセット</span><span class="sxs-lookup"><span data-stu-id="48857-243">Reset package</span></span>

<span data-ttu-id="48857-244">Surface UEFI リセット パッケージは、SEMM から Surface デバイスの登録を解除するために、1 つのタスクのみを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="48857-244">A Surface UEFI reset package is used to perform only one task — to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="48857-245">リセット パッケージには、デバイスのファームウェアから SEMM 証明書を削除し、UEFI 設定を工場出荷時の既定の設定にリセットする署名済み手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="48857-245">The reset package contains signed instructions to remove the SEMM certificate from the device’s firmware and to reset UEFI settings to the factory default settings.</span></span> <span data-ttu-id="48857-246">Surface UEFI 構成パッケージと同様に、Surface デバイスでプロビジョニングされたのと同じ SEMM 証明書でリセット パッケージに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-246">Like a Surface UEFI configuration package, a reset package must be signed with the same SEMM certificate that’s provisioned on the Surface device.</span></span> <span data-ttu-id="48857-247">SEMM リセット パッケージを作成する場合は、リセットする Surface デバイスのシリアル番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-247">When you create a SEMM reset package, you’re required to supply the serial number of the Surface device that you intend to reset.</span></span> <span data-ttu-id="48857-248">SEMM リセット パッケージは、1 つのデバイスに固有の汎用的なパッケージです。</span><span class="sxs-lookup"><span data-stu-id="48857-248">SEMM reset packages aren’t universal — they’re specific to one device.</span></span>

### <a name="recovery-request"></a><span data-ttu-id="48857-249">回復要求</span><span class="sxs-lookup"><span data-stu-id="48857-249">Recovery request</span></span>

<span data-ttu-id="48857-250">一部のシナリオでは、Surface UEFI リセット パッケージを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="48857-250">In some scenarios, it might be impossible to use a Surface UEFI reset package.</span></span> <span data-ttu-id="48857-251">(たとえば、Surface デバイスWindows使用できなくなった場合など)。これらのシナリオでは、回復要求操作を使用して、Surface UEFI (図 5 に示す) の**Enterprise 管理**ページを介して SEMM から Surface デバイスの登録を解除できます。</span><span class="sxs-lookup"><span data-stu-id="48857-251">(For example, if Windows becomes unusable on the Surface device.) In these scenarios you can unenroll the Surface device from SEMM through the **Enterprise Management** page of Surface UEFI (shown in Figure 5) with a Recovery Request operation.</span></span>

> [!div class="mx-imgBorder"]
> ![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*<span data-ttu-id="48857-253">図 5: </span><span class="sxs-lookup"><span data-stu-id="48857-253">Figure 5.</span></span> <span data-ttu-id="48857-254">[管理] ページで SEMM 回復要求Enterprise開始する</span><span class="sxs-lookup"><span data-stu-id="48857-254">Initiate a SEMM recovery request on the Enterprise Management page</span></span>*

<span data-ttu-id="48857-255">[管理] ページの**Enterpriseを使用して**Surface デバイスの SEMM をリセットすると、リセット要求が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48857-255">When you use the process on the **Enterprise Management** page to reset SEMM on a Surface device, you’re given a Reset Request.</span></span> <span data-ttu-id="48857-256">このリセット要求は、ファイルとして USB ドライブに保存したり、テキストとしてコピーしたり、モバイル デバイスを使用して QR コードとして読み取って、電子メールやメッセージを簡単に送信できます。</span><span class="sxs-lookup"><span data-stu-id="48857-256">This Reset Request can be saved as a file to a USB drive, copied as text, or read as a QR Code with a mobile device to be easily emailed or messaged.</span></span> <span data-ttu-id="48857-257">Microsoft Surface UEFI Configurator Reset Request オプションを使用して、要求のリセット ファイルを読み込むか、または要求のリセット テキストまたは QR コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="48857-257">Use the Microsoft Surface UEFI Configurator Reset Request option to load a Reset Request file or to enter the Reset Request text or QR Code.</span></span> <span data-ttu-id="48857-258">Microsoft Surface UEFI Configurator は、Surface デバイスで入力できる検証コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="48857-258">Microsoft Surface UEFI Configurator generates a verification code that can be entered on the Surface device.</span></span> <span data-ttu-id="48857-259">Surface デバイスでコードを入力し、[再起動]\*\*\*\* を選択すると、デバイスは SEMM から登録解除されます。</span><span class="sxs-lookup"><span data-stu-id="48857-259">If you enter the code on the Surface device and select **Restart**, the device is unenrolled from SEMM.</span></span> 

>[!NOTE]
><span data-ttu-id="48857-260">リセット要求は、作成から 2 時間後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="48857-260">A Reset Request expires two hours after it's created.</span></span>

<span data-ttu-id="48857-261">SEMM から Surface デバイスの登録を解除する方法の詳細なチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)からの Surface デバイスの登録を解除する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48857-261">For a step-by-step walkthrough of how to unenroll Surface devices from SEMM, see [Unenroll Surface devices from SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).</span></span>

## <a name="surface-enterprise-management-mode-certificate-requirements"></a><span data-ttu-id="48857-262">Surface Enterprise管理モード証明書の要件</span><span class="sxs-lookup"><span data-stu-id="48857-262">Surface Enterprise Management Mode certificate requirements</span></span>
<span data-ttu-id="48857-263">SEMM を Microsoft Surface UEFI Configurator と一緒に使用し、UEFI 設定を適用する場合は、構成ファイルの署名を確認するために証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="48857-263">When you use SEMM with Microsoft Surface UEFI Configurator and want to apply UEFI settings, a certificate is required to verify the signature of configuration files.</span></span> <span data-ttu-id="48857-264">この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI 設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="48857-264">This certificate ensures that after a device enrolls in SEMM, only packages created with the approved certificate can be used to modify the UEFI settings.</span></span>

>[!NOTE]
><span data-ttu-id="48857-265">登録済み Surface デバイスで SEMM または Surface UEFI 設定を変更するには、SEMM 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="48857-265">To make any modification to SEMM or Surface UEFI settings on enrolled Surface devices, the SEMM certificate is required.</span></span> <span data-ttu-id="48857-266">SEMM 証明書が破損または紛失した場合、SEMM を削除またはリセットすることはできません。</span><span class="sxs-lookup"><span data-stu-id="48857-266">If the SEMM certificate is corrupt or lost, SEMM can’t be removed or reset.</span></span> <span data-ttu-id="48857-267">バックアップと回復に適したソリューションを使用して、SEMM 証明書を適切に管理する</span><span class="sxs-lookup"><span data-stu-id="48857-267">Manage your SEMM certificate accordingly with an appropriate solution for backup and recovery</span></span>

<span data-ttu-id="48857-268">Microsoft Surface UEFI コンフィギュレーター ツールで作成されたパッケージは、証明書で署名されます。</span><span class="sxs-lookup"><span data-stu-id="48857-268">Packages created with the Microsoft Surface UEFI Configurator tool are signed with a certificate.</span></span> <span data-ttu-id="48857-269">この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="48857-269">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span> 
### <a name="recommended-certificate-settings"></a><span data-ttu-id="48857-270">推奨される証明書の設定</span><span class="sxs-lookup"><span data-stu-id="48857-270">Recommended certificate settings</span></span>
<span data-ttu-id="48857-271">SEMM 証明書には、次の設定が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="48857-271">The following settings are recommended for the SEMM certificate:</span></span>

- <span data-ttu-id="48857-272">**キー アルゴリズム** – RSA</span><span class="sxs-lookup"><span data-stu-id="48857-272">**Key Algorithm** – RSA</span></span> 
- <span data-ttu-id="48857-273">**キーの長** さ – 2048</span><span class="sxs-lookup"><span data-stu-id="48857-273">**Key Length** – 2048</span></span>
- <span data-ttu-id="48857-274">**ハッシュ アルゴリズム** – SHA-256</span><span class="sxs-lookup"><span data-stu-id="48857-274">**Hash Algorithm** – SHA-256</span></span>
- <span data-ttu-id="48857-275">**種類** – SSL サーバー認証</span><span class="sxs-lookup"><span data-stu-id="48857-275">**Type** – SSL Server Authentication</span></span>
- <span data-ttu-id="48857-276">**キー使用法** – デジタル署名、キーエンシファーメント</span><span class="sxs-lookup"><span data-stu-id="48857-276">**Key Usage** – Digital signature, Key Encipherment</span></span>
- <span data-ttu-id="48857-277">**プロバイダー** – Microsoft Enhanced RSA および AES 暗号化プロバイダー</span><span class="sxs-lookup"><span data-stu-id="48857-277">**Provider** – Microsoft Enhanced RSA and AES Cryptographic Provider</span></span>
- <span data-ttu-id="48857-278">**有効期限 –** 証明書の作成から 15 か月</span><span class="sxs-lookup"><span data-stu-id="48857-278">**Expiration Date** – 15 Months from certificate creation</span></span>
- <span data-ttu-id="48857-279">**キーのエクスポート ポリシー** – エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="48857-279">**Key Export Policy** – Exportable</span></span>

<span data-ttu-id="48857-280">また、中間証明機関 (CA) が SEMM 専用である 2 層公開キー基盤 (PKI) アーキテクチャで SEMM 証明書を認証し、証明書の失効を有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="48857-280">It's also recommended that the SEMM certificate be authenticated in a two-tier public key infrastructure (PKI) architecture where the intermediate certification authority (CA) is dedicated to SEMM, enabling certificate revocation.</span></span> <span data-ttu-id="48857-281">2 層 PKI 構成の詳細については、「Test Lab Guide: Deploying a AD [CS Two-Tier」を参照してください](https://technet.microsoft.com/library/hh831348)。</span><span class="sxs-lookup"><span data-stu-id="48857-281">For more information about a two-tier PKI configuration, see [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://technet.microsoft.com/library/hh831348).</span></span>

### <a name="self-signed-certificate"></a><span data-ttu-id="48857-282">自己署名証明書</span><span class="sxs-lookup"><span data-stu-id="48857-282">Self-signed certificate</span></span> 
<span data-ttu-id="48857-283">次の PowerShell スクリプトの例を使用して、概念実証シナリオで使用する自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="48857-283">You can use the following example PowerShell script to create a self-signed certificate for use in proof-of-concept scenarios.</span></span>
<span data-ttu-id="48857-284">このスクリプトを使用するには、次のテキストを メモ帳 にコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="48857-284">To use this script, copy the following text into Notepad, and then save the file as a PowerShell script (.ps1).</span></span> 

> [!NOTE]
> <span data-ttu-id="48857-285">このスクリプトは、 のパスワードを持つ証明書を作成します `12345678` 。</span><span class="sxs-lookup"><span data-stu-id="48857-285">This script creates a certificate with a password of `12345678`.</span></span> <span data-ttu-id="48857-286">このスクリプトによって生成される証明書は、実稼働環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="48857-286">The certificate generated by this script isn't recommended for production environments.</span></span>
  
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
><span data-ttu-id="48857-287">SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書をプライベート キーとパスワード保護でエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-287">For use with SEMM and Microsoft Surface UEFI Configurator, the certificate must be exported with the private key and with password protection.</span></span> <span data-ttu-id="48857-288">Microsoft Surface UEFI コンフィギュレーターは、SEMM 証明書ファイル (.pfx) と証明書パスワードを選択するように求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="48857-288">Microsoft Surface UEFI Configurator prompts you to select the SEMM certificate file (.pfx) and certificate password.</span></span>

<span data-ttu-id="48857-289">自己署名証明書を作成するには、次の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="48857-289">To create a self-signed certificate:</span></span>
1.  <span data-ttu-id="48857-290">C: ドライブで、スクリプトを保存するフォルダーを作成します。たとえば、C:\SEMM。</span><span class="sxs-lookup"><span data-stu-id="48857-290">On your C: drive, create the folder where you'll save the script; for example, C:\SEMM.</span></span>
2.  <span data-ttu-id="48857-291">例のスクリプトを メモ帳 (または同等のテキスト エディター) にコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="48857-291">Copy the example script into Notepad (or equivalent text editor), and then save the file as a PowerShell script (.ps1).</span></span>
3.  <span data-ttu-id="48857-292">管理者の資格情報を使用してコンピューターにサインインし、管理者特権の PowerShell セッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="48857-292">Sign in to your computer with administrator credentials, and then open an elevated PowerShell session.</span></span>
4.  <span data-ttu-id="48857-293">スクリプトの実行を許可するアクセス許可が設定されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="48857-293">Make sure that your permissions are set to allow scripts to run.</span></span> <span data-ttu-id="48857-294">既定では、実行ポリシーを変更しない限り、スクリプトの実行がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="48857-294">By default, scripts are blocked from running unless you modify the execution policy.</span></span> <span data-ttu-id="48857-295">詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="48857-295">To learn more, see [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>
5.  <span data-ttu-id="48857-296">コマンド プロンプトで、スクリプトの完全なパスを入力し、Enter キーを **押します**。</span><span class="sxs-lookup"><span data-stu-id="48857-296">At the command prompt, enter the full path of the script and then press **Enter**.</span></span> <span data-ttu-id="48857-297">このスクリプトは、TempOwner.pfx という名前のデモ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="48857-297">The script creates a Demo Certificate named TempOwner.pfx.</span></span>

<span data-ttu-id="48857-298">または、PowerShell を使用して独自の自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="48857-298">Alternatively, you can create your own self-signed certificate using PowerShell.</span></span> <span data-ttu-id="48857-299">詳細については [、「New-SelfSignedCertificate」を参照してください](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。</span><span class="sxs-lookup"><span data-stu-id="48857-299">For more information, see [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).</span></span>

>[!NOTE]
><span data-ttu-id="48857-300">PKI インフラストラクチャでオフライン ルートを使用する組織の場合、SEMM 証明書を認証するには、ルート CA に接続された環境で Microsoft Surface UEFI コンフィギュレーターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-300">For organizations that use an offline root in their PKI infrastructure, Microsoft Surface UEFI Configurator must be run in an environment connected to the root CA to authenticate the SEMM certificate.</span></span> <span data-ttu-id="48857-301">Microsoft Surface UEFI Configurator によって生成されたパッケージはファイルとして転送できます。そのため、USB スティックなどのリムーバブル ストレージを使用してオフライン ネットワーク環境の外部に転送できます。</span><span class="sxs-lookup"><span data-stu-id="48857-301">The packages generated by Microsoft Surface UEFI Configurator can be transferred as files, so they can be transferred outside the offline network environment with removable storage, such as a USB stick.</span></span>

### <a name="managing-certificates-faq"></a><span data-ttu-id="48857-302">証明書の管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="48857-302">Managing certificates FAQ</span></span>

<span data-ttu-id="48857-303">推奨される *最小長* は 15 か月です。</span><span class="sxs-lookup"><span data-stu-id="48857-303">The recommended *minimum* length is 15 months.</span></span> <span data-ttu-id="48857-304">有効期限が 15 か月未満の証明書を使用するか、15 か月以上経過した証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="48857-304">You can use a certificate that expires in less than 15 months or use a certificate that expires in longer than 15 months.</span></span>

>[!NOTE] 
><span data-ttu-id="48857-305">証明書の有効期限が切れると、証明書は自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="48857-305">When a certificate expires, it doesn't automatically renew.</span></span> 

**<span data-ttu-id="48857-306">有効期限が切れた証明書は、SEMM 登録デバイスの機能に影響しますか?</span><span class="sxs-lookup"><span data-stu-id="48857-306">Will an expired certificate affect the functionality of SEMM-enrolled devices?</span></span>**<br><br>
<span data-ttu-id="48857-307">いいえ、証明書は SEMM の IT 管理者管理タスクにのみ影響し、有効期限が切れるとデバイス機能には影響しません。</span><span class="sxs-lookup"><span data-stu-id="48857-307">No, a certificate only impacts IT admin management tasks in SEMM and has no effect on device functionality when it expires.</span></span>

**<span data-ttu-id="48857-308">SEMM パッケージと証明書を持つすべてのコンピューターで更新する必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="48857-308">Will the SEMM package and certificate need to be updated on all machines that have it?</span></span>**<br><br>
<span data-ttu-id="48857-309">SEMM のリセットまたは回復を機能するには、証明書が有効で有効期限が切れていない必要があります。</span><span class="sxs-lookup"><span data-stu-id="48857-309">If you want SEMM reset or recovery to work, the certificate needs to be valid and not expired.</span></span> 

**<span data-ttu-id="48857-310">注文したサーフェスごとにパッケージを一括リセットできますか?</span><span class="sxs-lookup"><span data-stu-id="48857-310">Can bulk reset packages be created for each surface that we order?</span></span> <span data-ttu-id="48857-311">環境内のすべてのコンピューターをリセットするビルドは可能ですか?</span><span class="sxs-lookup"><span data-stu-id="48857-311">Can one be built that resets all machines in our environment?</span></span>**<br><br>
<span data-ttu-id="48857-312">特定のデバイスの種類の構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセット パッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="48857-312">The PowerShell samples that create a config package for a specific device type can also be used to create a reset package that's serial-number independent.</span></span> <span data-ttu-id="48857-313">証明書がまだ有効な場合は、PowerShell を使用してリセット パッケージを作成して SEMM をリセットできます。</span><span class="sxs-lookup"><span data-stu-id="48857-313">If the certificate is still valid, you can create a reset package using PowerShell to reset SEMM.</span></span>

## <a name="version-history"></a><span data-ttu-id="48857-314">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="48857-314">Version history</span></span>


### <a name="version-2831390"></a><span data-ttu-id="48857-315">バージョン 2.83.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-315">Version 2.83.139.0</span></span>

<span data-ttu-id="48857-316">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-316">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-317">4 のSurface Laptopサポート</span><span class="sxs-lookup"><span data-stu-id="48857-317">Support for Surface Laptop 4</span></span>
- <span data-ttu-id="48857-318">7 の同時マルチスレッド オプションSurface Pro</span><span class="sxs-lookup"><span data-stu-id="48857-318">Support for simultaneous multithreading option for Surface Pro 7</span></span>
- <span data-ttu-id="48857-319">廃止された SEMM 設定の削除</span><span class="sxs-lookup"><span data-stu-id="48857-319">Removal of obsolete SEMM settings</span></span>  
- <span data-ttu-id="48857-320">MSI 署名の強化</span><span class="sxs-lookup"><span data-stu-id="48857-320">Improved MSI signing</span></span> 

### <a name="version-2791390"></a><span data-ttu-id="48857-321">バージョン 2.79.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-321">Version 2.79.139.0</span></span>

<span data-ttu-id="48857-322">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-322">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-323">7 以上Surface Proサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-323">Support for Surface Pro 7+.</span></span>
- <span data-ttu-id="48857-324">ユーザー エクスペリエンスの向上。</span><span class="sxs-lookup"><span data-stu-id="48857-324">User experience improvements.</span></span>

### <a name="version-2781390"></a><span data-ttu-id="48857-325">バージョン 2.78.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-325">Version 2.78.139.0</span></span>

<span data-ttu-id="48857-326">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-326">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-327">Go と Surface Laptop X のSurface Proサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-327">Support for Surface Laptop Go and Surface Pro X.</span></span>
- <span data-ttu-id="48857-328">新しいバージョン リリースの通知。</span><span class="sxs-lookup"><span data-stu-id="48857-328">Notifications for new version releases.</span></span>
- <span data-ttu-id="48857-329">所有権を変更するカスタム パッケージを作成する機能。</span><span class="sxs-lookup"><span data-stu-id="48857-329">The ability to create custom packages to change ownership.</span></span>
- <span data-ttu-id="48857-330">バグ修正。</span><span class="sxs-lookup"><span data-stu-id="48857-330">Bug fixes.</span></span>

### <a name="version-2731360"></a><span data-ttu-id="48857-331">バージョン 2.73.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-331">Version 2.73.136.0</span></span>

<span data-ttu-id="48857-332">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-332">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-333">SEMM を使用して Surface Hub2S でオーディオを無効にする機能。</span><span class="sxs-lookup"><span data-stu-id="48857-333">The ability for audio to be disabled on Surface Hub2S using SEMM.</span></span>
- <span data-ttu-id="48857-334">ドック 2 Surface Pro X のサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-334">Support for Surface Pro X for Dock 2.</span></span>
- <span data-ttu-id="48857-335">ドック 2 関連の操作の UEFI マネージャーのサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-335">Support for UEFI Manager for Dock 2-related operations.</span></span>
- <span data-ttu-id="48857-336">Surface Go リセット パッケージのバグ修正。</span><span class="sxs-lookup"><span data-stu-id="48857-336">A Surface Go reset package bug fix.</span></span>
- <span data-ttu-id="48857-337">2 台のSurface Hub OS から Windows 10 Teamデバイスへの移行Windows 10 ProサポートEnterprise。</span><span class="sxs-lookup"><span data-stu-id="48857-337">Support for migrating Surface Hub 2 devices from Windows 10 Team OS to Windows 10 Pro or Enterprise.</span></span>

### <a name="version-2711390"></a><span data-ttu-id="48857-338">バージョン 2.71.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-338">Version 2.71.139.0</span></span>

<span data-ttu-id="48857-339">このバージョンの SEMM では、3、Surface Book 3、および 7 の Surface Dock 2 管理機能Surface Laptop追加Surface Proされています。</span><span class="sxs-lookup"><span data-stu-id="48857-339">This version of SEMM adds support for Surface Dock 2 management features for Surface Book 3, Surface Laptop 3, and Surface Pro 7.</span></span> <span data-ttu-id="48857-340">内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48857-340">It includes:</span></span>

- <span data-ttu-id="48857-341">オーディオ (ロック/ロック解除) とイーサネットポートと USB ポートを有効にする機能。</span><span class="sxs-lookup"><span data-stu-id="48857-341">The ability to enable audio (lock/unlock), and Ethernet and USB ports.</span></span>
- <span data-ttu-id="48857-342">認証済みホストと認証されていないホストの両方にドック パッケージを作成する機能。</span><span class="sxs-lookup"><span data-stu-id="48857-342">The ability to create dock packages for both authenticated and unauthenticated hosts.</span></span>

### <a name="version-2701300"></a><span data-ttu-id="48857-343">バージョン 2.70.130.0</span><span class="sxs-lookup"><span data-stu-id="48857-343">Version 2.70.130.0</span></span>

<span data-ttu-id="48857-344">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-344">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-345">Surface Go 2 のサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-345">Support for Surface Go 2.</span></span>
- <span data-ttu-id="48857-346">3 のSurface Book。</span><span class="sxs-lookup"><span data-stu-id="48857-346">Support for Surface Book 3.</span></span>
- <span data-ttu-id="48857-347">バグ修正。</span><span class="sxs-lookup"><span data-stu-id="48857-347">Bug fixes.</span></span>

### <a name="version-2591390"></a><span data-ttu-id="48857-348">バージョン 2.59.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-348">Version 2.59.139.0</span></span>

<span data-ttu-id="48857-349">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-349">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-350">Intel プロセッサSurface Pro 7、Surface Pro X、Surface Laptop 3 13.5" および 15" モデルのサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-350">Support for Surface Pro 7, Surface Pro X, and Surface Laptop 3 13.5" and 15" models with Intel processor.</span></span> 
    >[!NOTE]
    ><span data-ttu-id="48857-351">Surface Laptop 3 15" AMD プロセッサはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48857-351">Surface Laptop 3 15" AMD processor isn't supported.</span></span>
- <span data-ttu-id="48857-352">Wake on Power 機能のサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-352">Support for the Wake on Power feature.</span></span>

### <a name="version-2541390"></a><span data-ttu-id="48857-353">バージョン 2.54.139.0</span><span class="sxs-lookup"><span data-stu-id="48857-353">Version 2.54.139.0</span></span>

<span data-ttu-id="48857-354">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-354">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-355">2S Surface Hubサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-355">Support for Surface Hub 2S.</span></span>
- <span data-ttu-id="48857-356">バグ修正。</span><span class="sxs-lookup"><span data-stu-id="48857-356">Bug fixes.</span></span>

### <a name="version-2431360"></a><span data-ttu-id="48857-357">バージョン 2.43.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-357">Version 2.43.136.0</span></span>

<span data-ttu-id="48857-358">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-358">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-359">同時マルチスレッドを有効または無効にするサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-359">Support to enable/disable simultaneous multithreading.</span></span>
- <span data-ttu-id="48857-360">ワイヤレス ネットワークと一部のデバイスのBluetoothオプションを分離します。</span><span class="sxs-lookup"><span data-stu-id="48857-360">Separate options for wireless networking and Bluetooth for some devices.</span></span>
- <span data-ttu-id="48857-361">バッテリーの制限は、Surface Studio。</span><span class="sxs-lookup"><span data-stu-id="48857-361">Battery Limit removed for Surface Studio.</span></span>

### <a name="version-2261360"></a><span data-ttu-id="48857-362">バージョン 2.26.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-362">Version 2.26.136.0</span></span>

<span data-ttu-id="48857-363">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-363">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-364">2 のSurface Studioサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-364">Support for Surface Studio 2.</span></span>
- <span data-ttu-id="48857-365">バッテリー制限機能。</span><span class="sxs-lookup"><span data-stu-id="48857-365">Battery Limit feature.</span></span>

### <a name="version-2211360"></a><span data-ttu-id="48857-366">バージョン 2.21.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-366">Version 2.21.136.0</span></span>

<span data-ttu-id="48857-367">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-367">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-368">6 のSurface Pro。</span><span class="sxs-lookup"><span data-stu-id="48857-368">Support for Surface Pro 6.</span></span>
- <span data-ttu-id="48857-369">2 のSurface Laptop。</span><span class="sxs-lookup"><span data-stu-id="48857-369">Support for Surface Laptop 2.</span></span>

### <a name="version-2141360"></a><span data-ttu-id="48857-370">バージョン 2.14.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-370">Version 2.14.136.0</span></span>

<span data-ttu-id="48857-371">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-371">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-372">Surface Go のサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-372">Support for Surface Go.</span></span>

### <a name="version-291360"></a><span data-ttu-id="48857-373">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="48857-373">Version 2.9.136.0</span></span>

<span data-ttu-id="48857-374">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-374">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-375">2 のSurface Bookサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-375">Support for Surface Book 2.</span></span>
- <span data-ttu-id="48857-376">LTE のSurface Proサポート。</span><span class="sxs-lookup"><span data-stu-id="48857-376">Support for Surface Pro LTE.</span></span>
- <span data-ttu-id="48857-377">アクセシビリティの向上。</span><span class="sxs-lookup"><span data-stu-id="48857-377">Accessibility improvements.</span></span>

### <a name="version-10740"></a><span data-ttu-id="48857-378">バージョン 1.0.74.0</span><span class="sxs-lookup"><span data-stu-id="48857-378">Version 1.0.74.0</span></span>

<span data-ttu-id="48857-379">このバージョンの SEMM には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48857-379">This version of SEMM includes:</span></span>

- <span data-ttu-id="48857-380">データのサポートSurface Laptop。</span><span class="sxs-lookup"><span data-stu-id="48857-380">Support for Surface Laptop.</span></span>
- <span data-ttu-id="48857-381">データのSurface Pro。</span><span class="sxs-lookup"><span data-stu-id="48857-381">Support for Surface Pro.</span></span>
- <span data-ttu-id="48857-382">バグ修正と一般的な改善。</span><span class="sxs-lookup"><span data-stu-id="48857-382">Bug fixes and general improvements.</span></span>

## <a name="related-topics"></a><span data-ttu-id="48857-383">関連トピック</span><span class="sxs-lookup"><span data-stu-id="48857-383">Related topics</span></span>

- [<span data-ttu-id="48857-384">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="48857-384">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)
- [<span data-ttu-id="48857-385">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="48857-385">Unenroll Surface devices from SEMM</span></span>](unenroll-surface-devices-from-semm.md)
- [<span data-ttu-id="48857-386">SEMM を使用して Surface Dock 2 ポートを保護する</span><span class="sxs-lookup"><span data-stu-id="48857-386">Secure Surface Dock 2 ports with SEMM</span></span>](secure-surface-dock-ports-semm.md)
