---
title: Surface Enterprise 管理モード (Surface)
description: Surface UEFI を使用した Surface デバイスのこの機能を使って、組織内のファームウェア設定をセキュリティで保護し、管理する方法について説明します。
keywords: uefi、構成、ファームウェア、secure、semm
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
ms.date: 05/26/2020
ms.openlocfilehash: 116aeb6d1d92f387efa34319f7852febda729207
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835606"
---
# <span data-ttu-id="a9ec9-104">Microsoft Surface Enterprise 管理モード</span><span class="sxs-lookup"><span data-stu-id="a9ec9-104">Microsoft Surface Enterprise Management Mode</span></span>

<span data-ttu-id="a9ec9-105">Microsoft Surface Enterprise Management Mode (SEMM) は、組織内のファームウェア設定をセキュリティで保護し、管理できる surface UEFI を備えた Surface デバイスの機能です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-105">Microsoft Surface Enterprise Management Mode (SEMM) is a feature of Surface devices with Surface UEFI that allows you to secure and manage firmware settings within your organization.</span></span> <span data-ttu-id="a9ec9-106">SEMM では、IT プロフェッショナルが UEFI 設定の構成を準備し、それを Surface デバイスにインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-106">With SEMM, IT professionals can prepare configurations of UEFI settings and install them on a Surface device.</span></span> <span data-ttu-id="a9ec9-107">UEFI 設定を構成する機能に加えて、SEMM は証明書を使用して、許可されていない改ざんまたは削除から構成を保護します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-107">In addition to the ability to configure UEFI settings, SEMM also uses a certificate to protect the configuration from unauthorized tampering or removal.</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-108">SEMM は、Surface UEFI ファームウェアを搭載したデバイスでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-108">SEMM is only available on devices with Surface UEFI firmware.</span></span> <span data-ttu-id="a9ec9-109">これには、Surface Pro 7、Surface Pro X、Surface Pc 3 の市販 Sku など、Intel プロセッサを搭載したほとんどの Surface デバイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-109">This includes most Surface devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3 commercial SKUs with an Intel processor.</span></span> <span data-ttu-id="a9ec9-110">SEMM は、(小売 SKU としてのみ利用可能) AMD プロセッサを搭載した15インチ Surface ノートパソコン 3 SKU ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-110">SEMM is not supported on the 15" Surface Laptop 3 SKU with AMD processor (only available as a retail SKU).</span></span> 

<span data-ttu-id="a9ec9-111">Surface デバイスが SEMM によって構成され、SEMM 証明書によって保護されている場合は、SEMM に*登録*されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-111">When Surface devices are configured by SEMM and secured with the SEMM certificate, they are considered *enrolled* in SEMM.</span></span> <span data-ttu-id="a9ec9-112">SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM に*登録*されていないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-112">When the SEMM certificate is removed and control of UEFI settings is returned to the user of the device, the Surface device is considered *unenrolled* in SEMM.</span></span>

<span data-ttu-id="a9ec9-113">SEMM および登録サーフェスデバイスを管理するために使用できる管理オプションは2つあります。スタンドアロンツールとして、または Microsoft Endpoint Configuration Manager との統合です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-113">There are two administrative options you can use to manage SEMM and enrolled Surface devices – a standalone tool or integration with Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="a9ec9-114">この記事では、Microsoft Surface UEFI コンフィギュレーターと呼ばれる SEMM 単体ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-114">The SEMM standalone tool, called the Microsoft Surface UEFI Configurator, is described in this article.</span></span> <span data-ttu-id="a9ec9-115">Microsoft Endpoint Configuration Manager を使用して SEMM を管理する方法の詳細については、「 [Microsoft Endpoint Configuration manager を使用して semm でデバイスを管理](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-115">For more information about how to manage SEMM with Microsoft Endpoint Configuration Manager, see [Use Microsoft Endpoint Configuration Manager to manage devices with SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).</span></span>


## <span data-ttu-id="a9ec9-116">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="a9ec9-116">Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="a9ec9-117">SEMM のプライマリワークスペースは、図1のように Microsoft Surface UEFI コンフィギュレーターです。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-117">The primary workspace of SEMM is Microsoft Surface UEFI Configurator, as shown in Figure 1.</span></span> <span data-ttu-id="a9ec9-118">Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスで SEMM を登録、構成、登録解除するために使用される Windows Installer (.msi) パッケージまたは WinPE イメージを作成するために使用されるツールです。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-118">Microsoft Surface UEFI Configurator is a tool that is used to create Windows Installer (.msi) packages or WinPE images that are used to enroll, configure, and unenroll SEMM on a Surface device.</span></span> <span data-ttu-id="a9ec9-119">これらのパッケージには、UEFI の設定が指定されている構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-119">These packages contain a configuration file where the settings for UEFI are specified.</span></span> <span data-ttu-id="a9ec9-120">SEMM パッケージには、インストールされてファームウェアに保存されている証明書が含まれており、UEFI 設定が適用される前に構成ファイルの署名を確認するために使われます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-120">SEMM packages also contain a certificate that is installed and stored in firmware and used to verify the signature of configuration files before UEFI settings are applied.</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-121">Surface UEFI コンフィギュレーターと SEMM を使って Surface Dock 2 上のポートを管理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-121">You can now use Surface UEFI Configurator and SEMM to manage ports on Surface Dock 2.</span></span> <span data-ttu-id="a9ec9-122">詳細については、「 [SEMM での Secure Surface Dock 2 ポート](secure-surface-dock-ports-semm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-122">To learn more, see [Secure Surface Dock 2 ports with SEMM](secure-surface-dock-ports-semm.md).</span></span>

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*<span data-ttu-id="a9ec9-124">図 1. </span><span class="sxs-lookup"><span data-stu-id="a9ec9-124">Figure 1.</span></span> <span data-ttu-id="a9ec9-125">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="a9ec9-125">Microsoft Surface UEFI Configurator</span></span>*


<span data-ttu-id="a9ec9-126">Microsoft Surface UEFI コンフィギュレーターツールは、次の3つのモードで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-126">You can use the Microsoft Surface UEFI Configurator tool in three modes:</span></span>

* <span data-ttu-id="a9ec9-127">[SURFACE UEFI 構成パッケージ](#configuration-package)。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-127">[Surface UEFI Configuration Package](#configuration-package).</span></span> <span data-ttu-id="a9ec9-128">Surface UEFI 構成パッケージを作成して SEMM に Surface デバイスを登録し、登録済みデバイスで UEFI 設定を構成するには、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-128">Use this mode to create a Surface UEFI configuration package to enroll a Surface device in SEMM and to configure UEFI settings on enrolled devices.</span></span>
* <span data-ttu-id="a9ec9-129">[SURFACE UEFI リセットパッケージ](#reset-package)。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-129">[Surface UEFI Reset Package](#reset-package).</span></span> <span data-ttu-id="a9ec9-130">このモードを使って、SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-130">Use this mode to unenroll a Surface device from SEMM.</span></span>
* <span data-ttu-id="a9ec9-131">[SURFACE UEFI 回復要求](#recovery-request)。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-131">[Surface UEFI Recovery Request](#recovery-request).</span></span> <span data-ttu-id="a9ec9-132">このモードを使って、回復要求に応答して、Reset Package 操作が失敗した場合に、SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-132">Use this mode to respond to a recovery request to unenroll a Surface device from SEMM where a Reset Package operation is not successful.</span></span>


#### <span data-ttu-id="a9ec9-133">Microsoft Surface UEFI コンフィギュレーターをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a9ec9-133">Download Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="a9ec9-134">Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-134">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

### <span data-ttu-id="a9ec9-135">構成パッケージ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-135">Configuration package</span></span>

<span data-ttu-id="a9ec9-136">Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装して管理するための主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-136">Surface UEFI configuration packages are the primary mechanism to implement and manage SEMM on Surface devices.</span></span> <span data-ttu-id="a9ec9-137">これらのパッケージには、図2に示すように、Microsoft Surface UEFI コンフィギュレーターおよび証明書ファイルでパッケージの作成時に指定した UEFI 設定の構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-137">These packages contain a configuration file of UEFI settings specified during creation of the package in Microsoft Surface UEFI Configurator and a certificate file, as shown in Figure 2.</span></span> <span data-ttu-id="a9ec9-138">まだ SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアで証明書ファイルがプロビジョニングされ、SEMM にデバイスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-138">When a configuration package is run for the first time on a Surface device that is not already enrolled in SEMM, it provisions the certificate file in the device’s firmware and enrolls the device in SEMM.</span></span> <span data-ttu-id="a9ec9-139">SEMM でデバイスを登録すると、証明書ファイルが保存され、登録が完了する前に、SEMM 証明書の拇印の最後の2桁を指定して、操作を確認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-139">When enrolling a device in SEMM, you will be prompted to confirm the operation by providing the last two digits of the SEMM certificate thumbprint before the certificate file is stored and the enrollment can complete.</span></span> <span data-ttu-id="a9ec9-140">この確認を行うには、登録時にユーザーがデバイスに存在していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-140">This confirmation requires that a user be present at the device at the time of enrollment to perform the confirmation.</span></span>

![SEMM 構成パッケージと証明書をセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*<span data-ttu-id="a9ec9-142">図 2. </span><span class="sxs-lookup"><span data-stu-id="a9ec9-142">Figure 2.</span></span> <span data-ttu-id="a9ec9-143">SEMM 構成パッケージと証明書をセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-143">Secure a SEMM configuration package with a certificate</span></span>*

<span data-ttu-id="a9ec9-144">SEMM 証明書の要件の詳細については、この記事の「 [Surface Enterprise 管理モード証明書の要件](#surface-enterprise-management-mode-certificate-requirements)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-144">See the [Surface Enterprise Management Mode certificate requirements](#surface-enterprise-management-mode-certificate-requirements) section of this article for more information about the requirements for the SEMM certificate.</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-145">Surface UEFI の**セキュリティ**、**デバイス**、**ブート構成**、または**エンタープライズ管理**ページを表示するために必要となる、semm を使って uefi パスワードを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-145">You can also specify a UEFI password with SEMM that is required to view the **Security**, **Devices**, **Boot Configuration**, or **Enterprise Management** pages of Surface UEFI.</span></span>

<span data-ttu-id="a9ec9-146">デバイスが SEMM に登録されると、構成ファイルが読み込まれ、ファイルで指定された設定が UEFI に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-146">After a device is enrolled in SEMM, the configuration file is read and the settings specified in the file are applied to UEFI.</span></span> <span data-ttu-id="a9ec9-147">既に SEMM に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名が、デバイスファームウェアに保存されている証明書に照らしてチェックされます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-147">When you run a configuration package on a device that is already enrolled in SEMM, the signature of the configuration file is checked against the certificate that is stored in the device firmware.</span></span> <span data-ttu-id="a9ec9-148">署名が一致しない場合、デバイスに変更は適用されません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-148">If the signature does not match, no changes are applied to the device.</span></span>

### <span data-ttu-id="a9ec9-149">SEMM で Surface UEFI のデバイスを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="a9ec9-149">Enable or disable devices in Surface UEFI with SEMM</span></span>

<span data-ttu-id="a9ec9-150">次のリストは、SEMM で管理可能なすべてのデバイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-150">The following list shows all the available devices you can manage in SEMM:</span></span>

* <span data-ttu-id="a9ec9-151">ドッキング USB ポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-151">Docking USB Port</span></span>
* <span data-ttu-id="a9ec9-152">ボードオーディオ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-152">On-board Audio</span></span>
* <span data-ttu-id="a9ec9-153">DGPU</span><span class="sxs-lookup"><span data-stu-id="a9ec9-153">DGPU</span></span>
* <span data-ttu-id="a9ec9-154">タイプ カバー</span><span class="sxs-lookup"><span data-stu-id="a9ec9-154">Type Cover</span></span>
* <span data-ttu-id="a9ec9-155">マイクロ SD カード</span><span class="sxs-lookup"><span data-stu-id="a9ec9-155">Micro SD Card</span></span>
* <span data-ttu-id="a9ec9-156">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-156">Front Camera</span></span>
* <span data-ttu-id="a9ec9-157">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-157">Rear Camera</span></span>
* <span data-ttu-id="a9ec9-158">Windows Hello の赤外線カメラ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-158">Infrared Camera, for Windows Hello</span></span>
* <span data-ttu-id="a9ec9-159">Bluetooth のみ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-159">Bluetooth Only</span></span>
* <span data-ttu-id="a9ec9-160">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="a9ec9-160">Wi-Fi and Bluetooth</span></span>
* <span data-ttu-id="a9ec9-161">             LTE           </span><span class="sxs-lookup"><span data-stu-id="a9ec9-161">LTE</span></span>

 >[!NOTE]
><span data-ttu-id="a9ec9-162">[UEFI デバイス] ページに表示される組み込みデバイスは、お使いのデバイスまたは企業環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-162">The built-in devices that appear in the UEFI Devices page may vary depending on your device or corporate environment.</span></span> <span data-ttu-id="a9ec9-163">たとえば、[UEFI デバイス] ページは Surface Pro X ではサポートされていません。LTE が装備されているデバイスにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-163">For example, the UEFI Devices page is not supported on Surface Pro X; LTE only appears on LTE-equipped devices.</span></span> 
### <span data-ttu-id="a9ec9-164">SEMM で詳細設定を構成する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-164">Configure advanced settings with SEMM</span></span>
**<span data-ttu-id="a9ec9-165">表 1.</span><span class="sxs-lookup"><span data-stu-id="a9ec9-165">Table 1.</span></span> <span data-ttu-id="a9ec9-166">詳細設定</span><span class="sxs-lookup"><span data-stu-id="a9ec9-166">Advanced settings</span></span>**

| <span data-ttu-id="a9ec9-167">設定</span><span class="sxs-lookup"><span data-stu-id="a9ec9-167">Setting</span></span>                            | <span data-ttu-id="a9ec9-168">説明</span><span class="sxs-lookup"><span data-stu-id="a9ec9-168">Description</span></span>                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a9ec9-169">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="a9ec9-169">IPv6 for PXE Boot</span></span>                  | <span data-ttu-id="a9ec9-170">PXE ブートの Ipv6 サポートを管理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-170">Allows you to manage Ipv6 support for PXE boot.</span></span> <span data-ttu-id="a9ec9-171">この設定を構成しない場合は、IPv6 の PXE ブートのサポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-171">If you do not configure this setting, IPv6 support for PXE boot is disabled.</span></span>                                                                               |
| <span data-ttu-id="a9ec9-172">代替ブート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-172">Alternate Boot</span></span>                     | <span data-ttu-id="a9ec9-173">起動時に音量を下げるボタンと電源ボタンの両方を押して、USB またはイーサネットデバイスを直接起動することで、代替のブート順序の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-173">Allows you to manage use of an Alternate boot order to boot directly to a USB or Ethernet device by pressing both the Volume Down button and Power button during boot.</span></span> <span data-ttu-id="a9ec9-174">この設定を構成しない場合は、代替ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-174">If you do not configure this setting, Alternate boot is enabled.</span></span> |
| <span data-ttu-id="a9ec9-175">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="a9ec9-175">Boot Order Lock</span></span>                    | <span data-ttu-id="a9ec9-176">変更を防止するために、ブート順序をロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-176">Allows you to lock the boot order to prevent changes.</span></span> <span data-ttu-id="a9ec9-177">この設定を構成しないと、起動順序のロックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-177">If you do not configure this setting, Boot Order Lock is disabled.</span></span>                                                                                                        |
| <span data-ttu-id="a9ec9-178">USB ブート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-178">USB Boot</span></span>                           | <span data-ttu-id="a9ec9-179">USB デバイスの起動を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-179">Allows you to manage booting to USB devices.</span></span> <span data-ttu-id="a9ec9-180">この設定を構成しない場合は、USB のブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-180">If you do not configure this setting, USB Boot is enabled.</span></span>                                                                                                                 |
| <span data-ttu-id="a9ec9-181">ネットワークスタック</span><span class="sxs-lookup"><span data-stu-id="a9ec9-181">Network Stack</span></span>                      | <span data-ttu-id="a9ec9-182">ネットワークスタックのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-182">Allows you to manage Network Stack boot settings.</span></span> <span data-ttu-id="a9ec9-183">この設定を構成しない場合、ネットワークスタックのブート設定を管理する機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-183">If you do not configure this setting,  the ability to manage Network Stack boot settings is disabled.</span></span>                                                                                                           |
| <span data-ttu-id="a9ec9-184">自動電源オン</span><span class="sxs-lookup"><span data-stu-id="a9ec9-184">Auto Power On</span></span>                      | <span data-ttu-id="a9ec9-185">自動電源オンのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-185">Allows you to manage Auto Power On boot settings.</span></span> <span data-ttu-id="a9ec9-186">この設定を構成しない場合、自動電源オンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-186">If you do not configure this setting, Auto Power on is enabled.</span></span>                                                                                                        |
| <span data-ttu-id="a9ec9-187">同時マルチスレッド (SMT)</span><span class="sxs-lookup"><span data-stu-id="a9ec9-187">Simultaneous Multi-Threading (SMT)</span></span> | <span data-ttu-id="a9ec9-188">ハイパースレッディングを有効または無効にするために、同時マルチスレッド (SMT) を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-188">Allows you to manage Simultaneous Multi-Threading (SMT) to enable or disable hyperthreading.</span></span> <span data-ttu-id="a9ec9-189">この設定を構成しない場合、SMT は有効になります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-189">If you do not configure this setting, SMT is enabled.</span></span>                                                  |
|<span data-ttu-id="a9ec9-190">バッテリー制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="a9ec9-190">Enable Battery limit</span></span>| <span data-ttu-id="a9ec9-191">バッテリー制限機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-191">Allows you to manage Battery limit functionality.</span></span> <span data-ttu-id="a9ec9-192">この設定を構成しない場合は、バッテリー制限が有効になっています</span><span class="sxs-lookup"><span data-stu-id="a9ec9-192">If you do not configure this setting, Battery limit is enabled</span></span> |
| <span data-ttu-id="a9ec9-193">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-193">Security</span></span>                           | <span data-ttu-id="a9ec9-194">Surface UEFI**セキュリティ**ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-194">Displays the Surface UEFI **Security** page.</span></span> <span data-ttu-id="a9ec9-195">この設定を構成しない場合、[セキュリティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-195">If you do not configure this setting, the Security page is displayed.</span></span>                                                                                                                 |
| <span data-ttu-id="a9ec9-196">デバイス</span><span class="sxs-lookup"><span data-stu-id="a9ec9-196">Devices</span></span>                            | <span data-ttu-id="a9ec9-197">Surface UEFI**デバイス**ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-197">Displays the Surface UEFI **Devices** page.</span></span> <span data-ttu-id="a9ec9-198">この設定を構成しないと、[デバイス] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-198">If you do not configure this setting,  the Devices page is displayed.</span></span>                                                                                                                     |
| <span data-ttu-id="a9ec9-199">Boot</span><span class="sxs-lookup"><span data-stu-id="a9ec9-199">Boot</span></span>                               | <span data-ttu-id="a9ec9-200">Surface UEFI**ブート**ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-200">Displays the Surface UEFI **Boot** page.</span></span> <span data-ttu-id="a9ec9-201">この設定を構成しない場合、[ブート] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-201">If you do not configure this setting, the Boot page is displayed.</span></span>                                                                                                                                                            |
| <span data-ttu-id="a9ec9-202">DateTime</span><span class="sxs-lookup"><span data-stu-id="a9ec9-202">DateTime</span></span>                           | <span data-ttu-id="a9ec9-203">Surface UEFI の [ **DateTime** ] ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-203">Displays the Surface UEFI **DateTime** page.</span></span> <span data-ttu-id="a9ec9-204">この設定を構成しない場合、[DateTime] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-204">If you do not configure this setting, the DateTime page is displayed.</span></span>                                                                                                                |



>[!NOTE]
><span data-ttu-id="a9ec9-205">SEMM 構成パッケージを作成すると、図3に示すように、**成功**したページに2つの文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-205">When you create a SEMM configuration package, two characters are shown on the **Successful** page, as shown in Figure 3.</span></span>

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*<span data-ttu-id="a9ec9-207">図 3. </span><span class="sxs-lookup"><span data-stu-id="a9ec9-207">Figure 3.</span></span> <span data-ttu-id="a9ec9-208">成功したページの証明書の拇印の最後の2文字を表示する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-208">Display of the last two characters of the certificate thumbprint on the Successful page</span></span>*

<span data-ttu-id="a9ec9-209">これらの文字は、証明書の拇印の最後の2文字であり、書き留めたり記録したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-209">These characters are the last two characters of the certificate thumbprint and should be written down or recorded.</span></span> <span data-ttu-id="a9ec9-210">図4に示すように、Surface デバイス上の SEMM での登録を確認するために文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-210">The characters are required to confirm enrollment in SEMM on a Surface device, as shown in Figure 4.</span></span>

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*<span data-ttu-id="a9ec9-212">図 4: </span><span class="sxs-lookup"><span data-stu-id="a9ec9-212">Figure 4.</span></span> <span data-ttu-id="a9ec9-213">Semm 証明書拇印での SEMM の登録確認</span><span class="sxs-lookup"><span data-stu-id="a9ec9-213">Enrollment confirmation in SEMM with the SEMM certificate thumbprint</span></span>*

>[!NOTE]
><span data-ttu-id="a9ec9-214">証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開くと、いつでも拇印を読むことができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-214">Administrators with access to the certificate file (.pfx) can read the thumbprint at any time by opening the .pfx file in CertMgr.</span></span> <span data-ttu-id="a9ec9-215">CertMgr で拇印を表示するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-215">To view the thumbprint with CertMgr, follow this process:</span></span>
>1. <span data-ttu-id="a9ec9-216">.Pfx ファイルを右クリックし、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-216">Right-click the .pfx file, and then click **Open**.</span></span>
>2. <span data-ttu-id="a9ec9-217">ナビゲーションウィンドウでフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-217">Expand the folder in the navigation pane.</span></span>
>3. <span data-ttu-id="a9ec9-218">**[証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-218">Click **Certificates**.</span></span>
>4. <span data-ttu-id="a9ec9-219">メインウィンドウで証明書を右クリックし、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-219">Right-click your certificate in the main pane, and then click **Open**.</span></span>
>5. <span data-ttu-id="a9ec9-220">[**詳細**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-220">Click the **Details** tab.</span></span>
>6. <span data-ttu-id="a9ec9-221">[表示] ドロップダウンメニューで [**すべて**] または [**プロパティ** **]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-221">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
>7. <span data-ttu-id="a9ec9-222">フィールドの**拇印**を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-222">Select the field **Thumbprint**.</span></span>

<span data-ttu-id="a9ec9-223">SEMM で Surface デバイスを登録したり、構成パッケージから UEFI 構成を適用したりするには、必要な操作は、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行することだけです。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-223">To enroll a Surface device in SEMM or to apply the UEFI configuration from a configuration package, all you need to do is run the .msi file with administrative privileges on the intended Surface device.</span></span> <span data-ttu-id="a9ec9-224">[Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023)や[Microsoft 展開ツールキット](https://technet.microsoft.com/windows/dn475741)などの、アプリケーションの展開やオペレーティングシステムの展開テクノロジを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-224">You can use application deployment or operating system deployment technologies such as [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) or the [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741).</span></span> <span data-ttu-id="a9ec9-225">SEMM でデバイスを登録する場合、デバイスで登録を確認するために存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-225">When you enroll a device in SEMM you must be present to confirm the enrollment on the device.</span></span> <span data-ttu-id="a9ec9-226">既に SEMM に登録されているデバイスに構成を適用する場合は、ユーザーの操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-226">User interaction is not required when you apply a configuration to devices that are already enrolled in SEMM.</span></span>

<span data-ttu-id="a9ec9-227">Semm で Surface デバイスを登録する方法、または SEMM を使って surface UEFI 構成を適用する方法の詳しい手順については、「 [semm を使って surface デバイスを登録して構成](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-227">For a step-by-step walkthrough of how to enroll a Surface device in SEMM or apply a Surface UEFI configuration with SEMM, see [Enroll and configure Surface devices with SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).</span></span>

### <span data-ttu-id="a9ec9-228">パッケージのリセット</span><span class="sxs-lookup"><span data-stu-id="a9ec9-228">Reset package</span></span>

<span data-ttu-id="a9ec9-229">Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除するために、1つのタスクを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-229">A Surface UEFI reset package is used to perform only one task — to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="a9ec9-230">リセットパッケージには、デバイスのファームウェアから SEMM 証明書を削除する、または UEFI 設定を出荷時の既定にリセットするための、署名された手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-230">The reset package contains signed instructions to remove the SEMM certificate from the device’s firmware and to reset UEFI settings to factory default.</span></span> <span data-ttu-id="a9ec9-231">Surface UEFI 構成パッケージと同様に、リセットパッケージは Surface デバイスでプロビジョニングされた同じ SEMM 証明書で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-231">Like a Surface UEFI configuration package, a reset package must be signed with the same SEMM certificate that is provisioned on the Surface device.</span></span> <span data-ttu-id="a9ec9-232">SEMM reset パッケージを作成するときは、リセットする Surface デバイスのシリアル番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-232">When you create a SEMM reset package, you are required to supply the serial number of the Surface device you intend to reset.</span></span> <span data-ttu-id="a9ec9-233">SEMM リセットパッケージはユニバーサルではなく、1つのデバイスに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-233">SEMM reset packages are not universal and are specific to one device.</span></span>

### <span data-ttu-id="a9ec9-234">回復要求</span><span class="sxs-lookup"><span data-stu-id="a9ec9-234">Recovery request</span></span>

<span data-ttu-id="a9ec9-235">一部のシナリオでは、Surface UEFI リセットパッケージを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-235">In some scenarios, it may be impossible to use a Surface UEFI reset package.</span></span> <span data-ttu-id="a9ec9-236">(たとえば、Surface デバイスで Windows が使用できなくなった場合など)。このようなシナリオでは、回復要求操作によって、surface デバイスの (図5に表示されている) Surface UEFI の [**エンタープライズ管理**] ページを、semm から登録解除できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-236">(For example, if Windows becomes unusable on the Surface device.) In these scenarios you can unenroll the Surface device from SEMM through the **Enterprise Management** page of Surface UEFI (shown in Figure 5) with a Recovery Request operation.</span></span>

![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*<span data-ttu-id="a9ec9-238">図 5: </span><span class="sxs-lookup"><span data-stu-id="a9ec9-238">Figure 5.</span></span> <span data-ttu-id="a9ec9-239">[エンタープライズ管理] ページで SEMM 回復要求を開始する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-239">Initiate a SEMM recovery request on the Enterprise Management page</span></span>*

<span data-ttu-id="a9ec9-240">[**エンタープライズ管理**] ページのプロセスを使用して Surface デバイス上の semm をリセットすると、リセット要求が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-240">When you use the process on the **Enterprise Management** page to reset SEMM on a Surface device, you are provided with a Reset Request.</span></span> <span data-ttu-id="a9ec9-241">このリセット要求は、ファイルとして USB ドライブに保存するか、テキストとしてコピーするか、モバイルデバイスを使用して簡単にメールや送信先を送信する QR コードとして読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-241">This Reset Request can be saved as a file to a USB drive, copied as text, or read as a QR Code with a mobile device to be easily emailed or messaged.</span></span> <span data-ttu-id="a9ec9-242">Microsoft Surface UEFI Configurator のリセット要求オプションを使用して、リセット要求ファイルを読み込むか、リセット要求のテキストまたは QR コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-242">Use the Microsoft Surface UEFI Configurator Reset Request option to load a Reset Request file or enter the Reset Request text or QR Code.</span></span> <span data-ttu-id="a9ec9-243">Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスに入力できる確認コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-243">Microsoft Surface UEFI Configurator will generate a verification code that can be entered on the Surface device.</span></span> <span data-ttu-id="a9ec9-244">Surface デバイスにコードを入力し、[**再起動**] をクリックすると、デバイスは semm からアン登録されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-244">If you enter the code on the Surface device and click **Restart**, the device will be unenrolled from SEMM.</span></span> 

>[!NOTE]
><span data-ttu-id="a9ec9-245">再設定要求は、作成後2時間後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-245">A Reset Request expires two hours after it is created.</span></span>

<span data-ttu-id="a9ec9-246">SEMM から Surface デバイスの登録を解除する方法についての詳しいチュートリアルについては、「 [SEMM からのサーデバイスの](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)登録解除」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-246">For a step-by-step walkthrough of how to unenroll Surface devices from SEMM, see [Unenroll Surface devices from SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).</span></span>

## <span data-ttu-id="a9ec9-247">Surface Enterprise 管理モードの証明書の要件</span><span class="sxs-lookup"><span data-stu-id="a9ec9-247">Surface Enterprise Management Mode certificate requirements</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-248">Semm 証明書は、登録されている Surface デバイスで SEMM または Surface UEFI の設定を変更する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-248">The SEMM certificate is required to perform any modification to SEMM or Surface UEFI settings on enrolled Surface devices.</span></span> <span data-ttu-id="a9ec9-249">SEMM 証明書が破損または紛失した場合、SEMM は削除またはリセットできません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-249">If the SEMM certificate is corrupted or lost, SEMM cannot be removed or reset.</span></span> <span data-ttu-id="a9ec9-250">必要に応じて、バックアップと復元に適したソリューションを使用して、SEMM 証明書を管理します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-250">Manage your SEMM certificate accordingly with an appropriate solution for backup and recovery.</span></span>

<span data-ttu-id="a9ec9-251">Microsoft Surface UEFI コンフィギュレーターツールで作成されたパッケージは、証明書で署名されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-251">Packages created with the Microsoft Surface UEFI Configurator tool are signed with a certificate.</span></span> <span data-ttu-id="a9ec9-252">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI の設定を変更できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-252">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span> <span data-ttu-id="a9ec9-253">SEMM 証明書には、次の設定が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-253">The following settings are recommended for the SEMM certificate:</span></span>

* <span data-ttu-id="a9ec9-254">**キーアルゴリズム**– RSA</span><span class="sxs-lookup"><span data-stu-id="a9ec9-254">**Key Algorithm** – RSA</span></span> 
* <span data-ttu-id="a9ec9-255">**キーの長さ**–2048</span><span class="sxs-lookup"><span data-stu-id="a9ec9-255">**Key Length** – 2048</span></span>
* <span data-ttu-id="a9ec9-256">**ハッシュアルゴリズム**– SHA-256</span><span class="sxs-lookup"><span data-stu-id="a9ec9-256">**Hash Algorithm** – SHA-256</span></span>
* <span data-ttu-id="a9ec9-257">**種類**– SSL サーバー認証</span><span class="sxs-lookup"><span data-stu-id="a9ec9-257">**Type** – SSL Server Authentication</span></span>
* <span data-ttu-id="a9ec9-258">**キー使用法**–デジタル署名、キーの暗号化</span><span class="sxs-lookup"><span data-stu-id="a9ec9-258">**Key Usage** – Digital signature, Key Encipherment</span></span>
* <span data-ttu-id="a9ec9-259">**プロバイダー** – Microsoft エンハンス RSA および AES 暗号化プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a9ec9-259">**Provider** – Microsoft Enhanced RSA and AES Cryptographic Provider</span></span>
* <span data-ttu-id="a9ec9-260">**有効期限**: 証明書の作成から15ヶ月</span><span class="sxs-lookup"><span data-stu-id="a9ec9-260">**Expiration Date** – 15 Months from certificate creation</span></span>
* <span data-ttu-id="a9ec9-261">**キーエクスポートポリシー** –エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="a9ec9-261">**Key Export Policy** – Exportable</span></span>

<span data-ttu-id="a9ec9-262">また、SEMM 証明書は、中間証明機関 (CA) が SEMM 専用であり、証明書の失効を有効にする2階層の公開キー基盤 (PKI) アーキテクチャで認証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-262">It is also recommended that the SEMM certificate be authenticated in a two-tier public key infrastructure (PKI) architecture where the intermediate certification authority (CA) is dedicated to SEMM, enabling certificate revocation.</span></span> <span data-ttu-id="a9ec9-263">2階層の PKI 構成の詳細については、「[テストラボガイド: AD CS 2 階層の Pki 階層の展開](https://technet.microsoft.com/library/hh831348)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-263">For more information about a two-tier PKI configuration, see [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://technet.microsoft.com/library/hh831348).</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-264">次の PowerShell スクリプトを使用して、概念実証のシナリオで使用する自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-264">You can use the following PowerShell script to create a self-signed certificate for use in proof-of-concept scenarios.</span></span>
 > <span data-ttu-id="a9ec9-265">このスクリプトを使用するには、次のテキストをメモ帳にコピーして、ファイルを PowerShell スクリプト (. ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-265">To use this script, copy the following text into Notepad and save the file as a PowerShell script (.ps1).</span></span> <span data-ttu-id="a9ec9-266">このスクリプトは、というパスワードの証明書を作成し `12345678` ます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-266">This script creates a certificate with a password of `12345678`.</span></span><br/><br/><span data-ttu-id="a9ec9-267">このスクリプトによって生成された証明書は、運用環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-267">The certificate generated by this script is not recommended for production environments.</span></span>
  
   ```
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

<span data-ttu-id="a9ec9-268">SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書を秘密キーでエクスポートし、パスワード保護を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-268">For use with SEMM and Microsoft Surface UEFI Configurator, the certificate must be exported with the private key and with password protection.</span></span> <span data-ttu-id="a9ec9-269">Microsoft Surface UEFI コンフィギュレーターは、必要に応じて SEMM 証明書ファイル (.pfx) と証明書のパスワードを選択するように求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-269">Microsoft Surface UEFI Configurator will prompt you to select the SEMM certificate file (.pfx) and certificate password when it is required.</span></span>

>[!NOTE]
><span data-ttu-id="a9ec9-270">PKI インフラストラクチャでオフラインルートを使用している組織の場合、Microsoft Surface UEFI コンフィギュレーターは、ルート CA に接続されている環境で SEMM 証明書を認証するために実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-270">For organizations that use an offline root in their PKI infrastructure, Microsoft Surface UEFI Configurator must be run in an environment connected to the root CA to authenticate the SEMM certificate.</span></span> <span data-ttu-id="a9ec9-271">Microsoft Surface UEFI コンフィギュレーターによって生成されたパッケージは、ファイルとして転送することができます。そのため、USB スティックなどのリムーバブル記憶域を使用して、オフラインネットワーク環境以外の場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-271">The packages generated by Microsoft Surface UEFI Configurator can be transferred as files and therefore can be transferred outside the offline network environment with removable storage, such as a USB stick.</span></span>

### <span data-ttu-id="a9ec9-272">証明書の管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="a9ec9-272">Managing certificates FAQ</span></span>

<span data-ttu-id="a9ec9-273">推奨される*最小*の長さは15か月です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-273">The recommended *minimum* length is 15 months.</span></span> <span data-ttu-id="a9ec9-274">有効期限が15か月以内の証明書を使用するか、有効期限が15か月を超える証明書を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-274">You can use a certificate that expires in less than 15 months or use a certificate that expires in longer than 15 months.</span></span>

>[!NOTE] 
><span data-ttu-id="a9ec9-275">証明書の有効期限が切れた場合は、自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-275">When a certificate expires, it does not automatically renew.</span></span> 

**<span data-ttu-id="a9ec9-276">既存のマシンは15ヶ月後も bios 設定を引き続き適用しますか?</span><span class="sxs-lookup"><span data-stu-id="a9ec9-276">Will existing machines continue to apply the bios settings after 15 months?</span></span>**

<span data-ttu-id="a9ec9-277">○ (ただし、証明書が有効だったときにパッケージ自体に署名された場合)</span><span class="sxs-lookup"><span data-stu-id="a9ec9-277">Yes, but only if the package itself was signed when the certificate was valid.</span></span>

<span data-ttu-id="a9ec9-278">**Will** **Semm パッケージと証明書は、それがインストールされているすべてのコンピューターで更新する必要がありますか?**</span><span class="sxs-lookup"><span data-stu-id="a9ec9-278">**Will** **the SEMM package and certificate need to be updated on all machines that have it?**</span></span>

<span data-ttu-id="a9ec9-279">SEMM のリセットまたは回復機能が必要な場合は、証明書が有効であり、期限切れになっていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-279">If you want SEMM reset or recovery to work, the certificate needs to be valid and not expired.</span></span> 

**<span data-ttu-id="a9ec9-280">注文した各サーフェスに対してパッケージを一括リセットできますか?</span><span class="sxs-lookup"><span data-stu-id="a9ec9-280">Can bulk reset packages be created for each surface that we order?</span></span> <span data-ttu-id="a9ec9-281">環境内のすべてのマシンをリセットするように構築することはできますか?</span><span class="sxs-lookup"><span data-stu-id="a9ec9-281">Can one be built that resets all machines in our environment?</span></span>**

<span data-ttu-id="a9ec9-282">特定のデバイスの種類に対して構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセットパッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-282">The PowerShell samples that create a config package for a specific device type can also be used to create a reset package that is serial-number independent.</span></span> <span data-ttu-id="a9ec9-283">証明書が有効な場合は、PowerShell を使用して、SEMM をリセットすることでリセットパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-283">If the certificate is still valid, you can create a reset package using PowerShell to reset SEMM.</span></span>

## <span data-ttu-id="a9ec9-284">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="a9ec9-284">Version History</span></span>

### <span data-ttu-id="a9ec9-285">バージョン2.71.139.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-285">Version 2.71.139.0</span></span>

<span data-ttu-id="a9ec9-286">このバージョンの SEMM は、surface Dock 3、surface Pc 3、Surface Pro 7 の surface Dock 2 の管理機能のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-286">This version of SEMM adds support for Surface Dock 2 management features  for Surface Book 3, Surface Laptop 3, and Surface Pro 7 including:</span></span>

- <span data-ttu-id="a9ec9-287">オーディオ (ロック/ロック解除)、イーサネットおよび USB ポートを有効にする</span><span class="sxs-lookup"><span data-stu-id="a9ec9-287">Enabling audio (locking/unlocking), Ethernet and USB ports</span></span>
- <span data-ttu-id="a9ec9-288">認証されたホストと認証されていないホストの両方に対して、dock パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="a9ec9-288">Ability to create dock packages for both authenticated and unauthenticated hosts</span></span>

### <span data-ttu-id="a9ec9-289">バージョン2.70.130.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-289">Version 2.70.130.0</span></span>

<span data-ttu-id="a9ec9-290">SEMM のこのバージョンには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-290">This version of SEMM includes:</span></span>

- <span data-ttu-id="a9ec9-291">Surface Go 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-291">Support for Surface Go 2</span></span>
- <span data-ttu-id="a9ec9-292">Surface Book 3 のサポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-292">Support for Surface Book 3</span></span>
- <span data-ttu-id="a9ec9-293">バグ修正</span><span class="sxs-lookup"><span data-stu-id="a9ec9-293">Bug fixes</span></span>


### <span data-ttu-id="a9ec9-294">バージョン2.59.139.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-294">Version 2.59.139.0</span></span>

* <span data-ttu-id="a9ec9-295">Surface Pro 7、Surface Pro X、Surface ノート Pc の 3 13.5 "と 15" のモデルを、Intel プロセッサでサポートします。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-295">Support for Surface Pro 7, Surface Pro X,  and Surface Laptop 3 13.5" and 15" models with Intel processor.</span></span> <span data-ttu-id="a9ec9-296">注: Surface ノート Pc 3 15 "AMD processor はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a9ec9-296">Note:  Surface Laptop 3 15" AMD processor is not supported.</span></span>

- <span data-ttu-id="a9ec9-297">Power on on Power 機能のサポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-297">Support for Wake on Power feature</span></span>

### <span data-ttu-id="a9ec9-298">バージョン2.54.139.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-298">Version 2.54.139.0</span></span>
* <span data-ttu-id="a9ec9-299">Surface Hub 2S へのサポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-299">Support to Surface Hub 2S</span></span>
* <span data-ttu-id="a9ec9-300">バグ修正</span><span class="sxs-lookup"><span data-stu-id="a9ec9-300">Bug fixes</span></span>

### <span data-ttu-id="a9ec9-301">バージョン2.43.136.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-301">Version 2.43.136.0</span></span>
* <span data-ttu-id="a9ec9-302">Simulatenous を有効/無効にするサポート (複数)</span><span class="sxs-lookup"><span data-stu-id="a9ec9-302">Support to enable/disable simulatenous multithreating</span></span> 
* <span data-ttu-id="a9ec9-303">一部のデバイスで WiFi と Bluetooth の個別のオプションを使用する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-303">Separate options for WiFi and Bluetooth for some devices</span></span> 
* <span data-ttu-id="a9ec9-304">Surface Studio のバッテリー制限が削除されました</span><span class="sxs-lookup"><span data-stu-id="a9ec9-304">Battery Limit removed for Surface Studio</span></span> 

### <span data-ttu-id="a9ec9-305">バージョン2.26.136.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-305">Version 2.26.136.0</span></span>
* <span data-ttu-id="a9ec9-306">Surface Studio 2 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-306">Add support to Surface Studio 2</span></span>
* <span data-ttu-id="a9ec9-307">バッテリー制限機能</span><span class="sxs-lookup"><span data-stu-id="a9ec9-307">Battery Limit feature</span></span>

### <span data-ttu-id="a9ec9-308">バージョン2.21.136.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-308">Version 2.21.136.0</span></span>
* <span data-ttu-id="a9ec9-309">Surface Pro 6 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-309">Add support to Surface Pro 6</span></span>
* <span data-ttu-id="a9ec9-310">Surface ノート Pc にサポートを追加する2</span><span class="sxs-lookup"><span data-stu-id="a9ec9-310">Add support to Surface Laptop 2</span></span>

### <span data-ttu-id="a9ec9-311">バージョン2.14.136.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-311">Version 2.14.136.0</span></span>
* <span data-ttu-id="a9ec9-312">Surface Go にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-312">Add support to Surface Go</span></span>

### <span data-ttu-id="a9ec9-313">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-313">Version 2.9.136.0</span></span>
* <span data-ttu-id="a9ec9-314">Surface Book 2 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-314">Add support to Surface Book 2</span></span>
* <span data-ttu-id="a9ec9-315">Surface Pro LTE にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-315">Add support to Surface Pro LTE</span></span>
* <span data-ttu-id="a9ec9-316">ユーザー補助機能の改善</span><span class="sxs-lookup"><span data-stu-id="a9ec9-316">Accessibility improvements</span></span>

### <span data-ttu-id="a9ec9-317">バージョン1.0.74.0</span><span class="sxs-lookup"><span data-stu-id="a9ec9-317">Version 1.0.74.0</span></span>
* <span data-ttu-id="a9ec9-318">Surface のノート Pc にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-318">Add support to Surface Laptop</span></span>
* <span data-ttu-id="a9ec9-319">Surface Pro にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="a9ec9-319">Add support to Surface Pro</span></span>
* <span data-ttu-id="a9ec9-320">バグ修正と全般的な改善</span><span class="sxs-lookup"><span data-stu-id="a9ec9-320">Bug fixes and general improvement</span></span>

## <span data-ttu-id="a9ec9-321">関連トピック</span><span class="sxs-lookup"><span data-stu-id="a9ec9-321">Related topics</span></span>

- [<span data-ttu-id="a9ec9-322">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="a9ec9-322">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)
- [<span data-ttu-id="a9ec9-323">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="a9ec9-323">Unenroll Surface devices from SEMM</span></span>](unenroll-surface-devices-from-semm.md)
- [<span data-ttu-id="a9ec9-324">SEMM での Secure Surface Dock 2 ポート</span><span class="sxs-lookup"><span data-stu-id="a9ec9-324">Secure Surface Dock 2 ports with SEMM</span></span>](secure-surface-dock-ports-semm.md)
