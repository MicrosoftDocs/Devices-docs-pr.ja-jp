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
ms.date: 09/01/2020
ms.openlocfilehash: a6ea1742ab767a99e7b4868e56d081bf0016785b
ms.sourcegitcommit: 6618e8fe05628aa8b17654584657eff0f784dbfd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "10986329"
---
# <span data-ttu-id="1fbb8-104">Microsoft Surface Enterprise 管理モード</span><span class="sxs-lookup"><span data-stu-id="1fbb8-104">Microsoft Surface Enterprise Management Mode</span></span>

<span data-ttu-id="1fbb8-105">Microsoft Surface Enterprise Management Mode (SEMM) は、組織内のファームウェア設定をセキュリティで保護し、管理できる surface UEFI を備えた Surface デバイスの機能です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-105">Microsoft Surface Enterprise Management Mode (SEMM) is a feature of Surface devices with Surface UEFI that allows you to secure and manage firmware settings within your organization.</span></span> <span data-ttu-id="1fbb8-106">SEMM では、IT プロフェッショナルが UEFI 設定の構成を準備し、それを Surface デバイスにインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-106">With SEMM, IT professionals can prepare configurations of UEFI settings and install them on a Surface device.</span></span> <span data-ttu-id="1fbb8-107">UEFI 設定を構成する機能に加えて、SEMM は証明書を使用して、許可されていない改ざんまたは削除から構成を保護します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-107">In addition to the ability to configure UEFI settings, SEMM also uses a certificate to protect the configuration from unauthorized tampering or removal.</span></span> <span data-ttu-id="1fbb8-108">SEMM は、Surface Hub の2S を Windows 10 Pro と Enterprise に移行できるようにするための要件です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-108">SEMM is a requirement to be able to migrate a Surface Hub 2S to Windows 10 Pro and Enterprise.</span></span>

>[!NOTE]
><span data-ttu-id="1fbb8-109">SEMM は、Surface UEFI ファームウェアを搭載したデバイスでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-109">SEMM is only available on devices with Surface UEFI firmware.</span></span> <span data-ttu-id="1fbb8-110">これは、Surface Pro 7、Surface Pro X、Surface Hub 2S、Surface Pc 3 の市販 Sku など、Intel プロセッサを搭載した、他の多くの Surface デバイスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-110">This comprises most other Surface devices including Surface Pro 7, Surface Pro X, Surface Hub 2S, and Surface Laptop 3 commercial SKUs with an Intel processor.</span></span> <span data-ttu-id="1fbb8-111">SEMM は、(小売 SKU としてのみ利用可能) AMD プロセッサを搭載した15インチ Surface ノートパソコン 3 SKU ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-111">SEMM is not supported on the 15" Surface Laptop 3 SKU with AMD processor (only available as a retail SKU).</span></span> 

<span data-ttu-id="1fbb8-112">Surface デバイスが SEMM によって構成され、SEMM 証明書によって保護されている場合は、SEMM に *登録* されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-112">When Surface devices are configured by SEMM and secured with the SEMM certificate, they are considered *enrolled* in SEMM.</span></span> <span data-ttu-id="1fbb8-113">SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM に *登録* されていないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-113">When the SEMM certificate is removed and control of UEFI settings is returned to the user of the device, the Surface device is considered *unenrolled* in SEMM.</span></span>

<span data-ttu-id="1fbb8-114">SEMM および登録 Surface デバイスを管理するために使用できる管理オプションは2つあります。スタンドアロンツールとして、または Microsoft Endpoint Configuration Manager との統合です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-114">There are two administrative options you can use to manage SEMM and enroll Surface devices – a standalone tool or integration with Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="1fbb8-115">この記事では、Microsoft Surface UEFI コンフィギュレーターと呼ばれる SEMM 単体ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-115">The SEMM standalone tool, called the Microsoft Surface UEFI Configurator, is described in this article.</span></span> <span data-ttu-id="1fbb8-116">Microsoft Endpoint Configuration Manager を使用して SEMM を管理する方法の詳細については、「 [Microsoft Endpoint Configuration manager を使用して semm でデバイスを管理](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-116">For more information about how to manage SEMM with Microsoft Endpoint Configuration Manager, see [Use Microsoft Endpoint Configuration Manager to manage devices with SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).</span></span>


## <span data-ttu-id="1fbb8-117">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="1fbb8-117">Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="1fbb8-118">SEMM のプライマリワークスペースは、図1のように Microsoft Surface UEFI コンフィギュレーターです。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-118">The primary workspace of SEMM is Microsoft Surface UEFI Configurator, as shown in Figure 1.</span></span> <span data-ttu-id="1fbb8-119">Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスで SEMM を登録、構成、登録解除するために使用される Windows Installer (.msi) パッケージまたは WinPE イメージを作成するために使用されるツールです。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-119">Microsoft Surface UEFI Configurator is a tool used to create Windows Installer (.msi) packages or WinPE images used to enroll, configure, and unenroll SEMM on a Surface device.</span></span> <span data-ttu-id="1fbb8-120">これらのパッケージには、UEFI の設定が指定されている構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-120">These packages contain a configuration file where the settings for UEFI are specified.</span></span> <span data-ttu-id="1fbb8-121">SEMM パッケージには証明書も含まれています。これは、インストールされ、ファームウェアに保存され、UEFI 設定が適用される前に構成ファイルの署名を確認するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-121">SEMM packages also contain a certificate, which is installed and stored in firmware and used to verify the signature of configuration files before UEFI settings are applied.</span></span>

>[!NOTE]
><span data-ttu-id="1fbb8-122">Surface UEFI コンフィギュレーターと SEMM を使って Surface Dock 2 上のポートを管理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-122">You can now use Surface UEFI Configurator and SEMM to manage ports on Surface Dock 2.</span></span> <span data-ttu-id="1fbb8-123">詳細については、「 [SEMM での Secure Surface Dock 2 ポート](secure-surface-dock-ports-semm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-123">To learn more, see [Secure Surface Dock 2 ports with SEMM](secure-surface-dock-ports-semm.md).</span></span>

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*<span data-ttu-id="1fbb8-125">図 1. </span><span class="sxs-lookup"><span data-stu-id="1fbb8-125">Figure 1.</span></span> <span data-ttu-id="1fbb8-126">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="1fbb8-126">Microsoft Surface UEFI Configurator</span></span>*


<span data-ttu-id="1fbb8-127">Microsoft Surface UEFI コンフィギュレーターツールは、次の3つのモードで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-127">You can use the Microsoft Surface UEFI Configurator tool in three modes:</span></span>

* <span data-ttu-id="1fbb8-128">[SURFACE UEFI 構成パッケージ](#configuration-package)。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-128">[Surface UEFI Configuration Package](#configuration-package).</span></span> <span data-ttu-id="1fbb8-129">Surface UEFI 構成パッケージを作成して SEMM に Surface デバイスを登録し、登録済みデバイスで UEFI 設定を構成するには、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-129">Use this mode to create a Surface UEFI configuration package to enroll a Surface device in SEMM and to configure UEFI settings on enrolled devices.</span></span>
* <span data-ttu-id="1fbb8-130">[SURFACE UEFI リセットパッケージ](#reset-package)。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-130">[Surface UEFI Reset Package](#reset-package).</span></span> <span data-ttu-id="1fbb8-131">このモードを使って、SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-131">Use this mode to unenroll a Surface device from SEMM.</span></span>
* <span data-ttu-id="1fbb8-132">[SURFACE UEFI 回復要求](#recovery-request)。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-132">[Surface UEFI Recovery Request](#recovery-request).</span></span> <span data-ttu-id="1fbb8-133">このモードを使って、回復要求に応答して、Reset Package 操作が失敗した場合に、SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-133">Use this mode to respond to a recovery request to unenroll a Surface device from SEMM where a Reset Package operation is not successful.</span></span>


#### <span data-ttu-id="1fbb8-134">Microsoft Surface UEFI コンフィギュレーターをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="1fbb8-134">Download Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="1fbb8-135">Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-135">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

### <span data-ttu-id="1fbb8-136">構成パッケージ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-136">Configuration package</span></span>

<span data-ttu-id="1fbb8-137">Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装して管理するための主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-137">Surface UEFI configuration packages are the primary mechanism to implement and manage SEMM on Surface devices.</span></span> <span data-ttu-id="1fbb8-138">これらのパッケージには、図2に示すように、Microsoft Surface UEFI コンフィギュレーターおよび証明書ファイルでパッケージの作成時に指定した UEFI 設定の構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-138">These packages contain a configuration file of UEFI settings specified during creation of the package in Microsoft Surface UEFI Configurator and a certificate file, as shown in Figure 2.</span></span> <span data-ttu-id="1fbb8-139">まだ SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアで証明書ファイルがプロビジョニングされ、SEMM にデバイスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-139">When a configuration package is run for the first time on a Surface device that is not already enrolled in SEMM, it provisions the certificate file in the device’s firmware and enrolls the device in SEMM.</span></span> <span data-ttu-id="1fbb8-140">SEMM でデバイスを登録すると、証明書ファイルが保存され、登録が完了する前に、SEMM 証明書の拇印の最後の2桁を指定して、操作を確認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-140">When enrolling a device in SEMM, you will be prompted to confirm the operation by providing the last two digits of the SEMM certificate thumbprint before the certificate file is stored and the enrollment can complete.</span></span> <span data-ttu-id="1fbb8-141">この確認を行うには、登録時にユーザーがデバイスに物理的に存在していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-141">This confirmation requires a user be physically present at the device at the time of enrollment to perform the confirmation.</span></span>

![SEMM 構成パッケージと証明書をセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*<span data-ttu-id="1fbb8-143">図 2. </span><span class="sxs-lookup"><span data-stu-id="1fbb8-143">Figure 2.</span></span> <span data-ttu-id="1fbb8-144">SEMM 構成パッケージと証明書をセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-144">Secure a SEMM configuration package with a certificate</span></span>*

<span data-ttu-id="1fbb8-145">SEMM 証明書の要件の詳細については、この記事の「 [Surface Enterprise 管理モード証明書の要件](#surface-enterprise-management-mode-certificate-requirements) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-145">See the [Surface Enterprise Management Mode certificate requirements](#surface-enterprise-management-mode-certificate-requirements) section of this article for more information about the requirements for the SEMM certificate.</span></span>

>[!NOTE]
><span data-ttu-id="1fbb8-146">Surface UEFI の **セキュリティ**、 **デバイス**、 **ブート構成**、または **エンタープライズ管理** ページを表示するために必要となる、semm を使って uefi パスワードを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-146">You can also specify a UEFI password with SEMM that is required to view the **Security**, **Devices**, **Boot Configuration**, or **Enterprise Management** pages of Surface UEFI.</span></span>

<span data-ttu-id="1fbb8-147">デバイスが SEMM に登録されると、構成ファイルが読み込まれ、ファイルで指定された設定が UEFI に適用されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-147">After a device is enrolled in SEMM, the configuration file is read and the settings specified in the file are applied to UEFI.</span></span> <span data-ttu-id="1fbb8-148">既に SEMM に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名が、デバイスファームウェアに保存されている証明書に照らしてチェックされます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-148">When you run a configuration package on a device that is already enrolled in SEMM, the signature of the configuration file is checked against the certificate that is stored in the device firmware.</span></span> <span data-ttu-id="1fbb8-149">署名が一致しない場合、デバイスに変更は適用されません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-149">If the signature does not match, no changes are applied to the device.</span></span>

### <span data-ttu-id="1fbb8-150">SEMM で Surface UEFI のデバイスを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="1fbb8-150">Enable or disable devices in Surface UEFI with SEMM</span></span>

<span data-ttu-id="1fbb8-151">次のリストは、SEMM で管理可能なすべてのデバイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-151">The following list shows all the available devices you can manage in SEMM:</span></span>

* <span data-ttu-id="1fbb8-152">ドッキング USB ポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-152">Docking USB Port</span></span>
* <span data-ttu-id="1fbb8-153">ボードオーディオ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-153">On-board Audio</span></span>
* <span data-ttu-id="1fbb8-154">DGPU</span><span class="sxs-lookup"><span data-stu-id="1fbb8-154">DGPU</span></span>
* <span data-ttu-id="1fbb8-155">タイプ カバー</span><span class="sxs-lookup"><span data-stu-id="1fbb8-155">Type Cover</span></span>
* <span data-ttu-id="1fbb8-156">マイクロ SD カード</span><span class="sxs-lookup"><span data-stu-id="1fbb8-156">Micro SD Card</span></span>
* <span data-ttu-id="1fbb8-157">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-157">Front Camera</span></span>
* <span data-ttu-id="1fbb8-158">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-158">Rear Camera</span></span>
* <span data-ttu-id="1fbb8-159">Windows Hello の赤外線カメラ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-159">Infrared Camera, for Windows Hello</span></span>
* <span data-ttu-id="1fbb8-160">Bluetooth のみ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-160">Bluetooth Only</span></span>
* <span data-ttu-id="1fbb8-161">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="1fbb8-161">Wi-Fi and Bluetooth</span></span>
* <span data-ttu-id="1fbb8-162">             LTE           </span><span class="sxs-lookup"><span data-stu-id="1fbb8-162">LTE</span></span>

 >[!NOTE]
><span data-ttu-id="1fbb8-163">[UEFI デバイス] ページに表示される組み込みデバイスは、お使いのデバイスまたは企業環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-163">The built-in devices that appear in the UEFI Devices page may vary depending on your device or corporate environment.</span></span> <span data-ttu-id="1fbb8-164">たとえば、[UEFI デバイス] ページは Surface Pro X ではサポートされていません。LTE が装備されているデバイスにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-164">For example, the UEFI Devices page is not supported on Surface Pro X; LTE only appears on LTE-equipped devices.</span></span> 
### <span data-ttu-id="1fbb8-165">SEMM で詳細設定を構成する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-165">Configure advanced settings with SEMM</span></span>
**<span data-ttu-id="1fbb8-166">表 1.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-166">Table 1.</span></span> <span data-ttu-id="1fbb8-167">詳細設定</span><span class="sxs-lookup"><span data-stu-id="1fbb8-167">Advanced settings</span></span>**

| <span data-ttu-id="1fbb8-168">設定</span><span class="sxs-lookup"><span data-stu-id="1fbb8-168">Setting</span></span>                            | <span data-ttu-id="1fbb8-169">説明</span><span class="sxs-lookup"><span data-stu-id="1fbb8-169">Description</span></span>                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1fbb8-170">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="1fbb8-170">IPv6 for PXE Boot</span></span>                  | <span data-ttu-id="1fbb8-171">PXE ブートの IPv6 サポートを管理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-171">Allows you to manage IPv6 support for PXE boot.</span></span> <span data-ttu-id="1fbb8-172">この設定を構成しない場合は、IPv6 の PXE ブートのサポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-172">If you do not configure this setting, IPv6 support for PXE boot is disabled.</span></span>                                                                               |
| <span data-ttu-id="1fbb8-173">代替ブート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-173">Alternate Boot</span></span>                     | <span data-ttu-id="1fbb8-174">起動時に音量を下げるボタンと電源ボタンの両方を押して、USB またはイーサネットデバイスを直接起動することで、代替のブート順序の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-174">Allows you to manage use of an Alternate boot order to boot directly to a USB or Ethernet device by pressing both the Volume Down button and Power button during boot.</span></span> <span data-ttu-id="1fbb8-175">この設定を構成しない場合は、代替ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-175">If you do not configure this setting, Alternate boot is enabled.</span></span> |
| <span data-ttu-id="1fbb8-176">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="1fbb8-176">Boot Order Lock</span></span>                    | <span data-ttu-id="1fbb8-177">変更を防止するために、ブート順序をロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-177">Allows you to lock the boot order to prevent changes.</span></span> <span data-ttu-id="1fbb8-178">この設定を構成しないと、起動順序のロックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-178">If you do not configure this setting, Boot Order Lock is disabled.</span></span>                                                                                                        |
| <span data-ttu-id="1fbb8-179">USB ブート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-179">USB Boot</span></span>                           | <span data-ttu-id="1fbb8-180">USB デバイスの起動を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-180">Allows you to manage booting to USB devices.</span></span> <span data-ttu-id="1fbb8-181">この設定を構成しない場合は、USB のブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-181">If you do not configure this setting, USB Boot is enabled.</span></span>                                                                                                                 |
| <span data-ttu-id="1fbb8-182">ネットワークスタック</span><span class="sxs-lookup"><span data-stu-id="1fbb8-182">Network Stack</span></span>                      | <span data-ttu-id="1fbb8-183">ネットワークスタックのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-183">Allows you to manage Network Stack boot settings.</span></span> <span data-ttu-id="1fbb8-184">この設定を構成しない場合、ネットワークスタックのブート設定を管理する機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-184">If you do not configure this setting,  the ability to manage Network Stack boot settings is disabled.</span></span>                                                                                                           |
| <span data-ttu-id="1fbb8-185">自動電源オン</span><span class="sxs-lookup"><span data-stu-id="1fbb8-185">Auto Power On</span></span>                      | <span data-ttu-id="1fbb8-186">自動電源オンのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-186">Allows you to manage Auto Power On boot settings.</span></span> <span data-ttu-id="1fbb8-187">この設定を構成しない場合、自動電源オンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-187">If you do not configure this setting, Auto Power on is enabled.</span></span>                                                                                                        |
| <span data-ttu-id="1fbb8-188">同時マルチスレッド (SMT)</span><span class="sxs-lookup"><span data-stu-id="1fbb8-188">Simultaneous Multi-Threading (SMT)</span></span> | <span data-ttu-id="1fbb8-189">ハイパースレッディングを有効または無効にするために、同時マルチスレッド (SMT) を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-189">Allows you to manage Simultaneous Multi-Threading (SMT) to enable or disable hyperthreading.</span></span> <span data-ttu-id="1fbb8-190">この設定を構成しない場合、SMT は有効になります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-190">If you do not configure this setting, SMT is enabled.</span></span>                                                  |
|<span data-ttu-id="1fbb8-191">バッテリー制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="1fbb8-191">Enable Battery limit</span></span>| <span data-ttu-id="1fbb8-192">バッテリー制限機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-192">Allows you to manage Battery limit functionality.</span></span> <span data-ttu-id="1fbb8-193">この設定を構成しない場合は、バッテリー制限が有効になっています</span><span class="sxs-lookup"><span data-stu-id="1fbb8-193">If you do not configure this setting, Battery limit is enabled</span></span> |
| <span data-ttu-id="1fbb8-194">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-194">Security</span></span>                           | <span data-ttu-id="1fbb8-195">Surface UEFI **セキュリティ** ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-195">Displays the Surface UEFI **Security** page.</span></span> <span data-ttu-id="1fbb8-196">この設定を構成しない場合、[セキュリティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-196">If you do not configure this setting, the Security page is displayed.</span></span>                                                                                                                 |
| <span data-ttu-id="1fbb8-197">デバイス</span><span class="sxs-lookup"><span data-stu-id="1fbb8-197">Devices</span></span>                            | <span data-ttu-id="1fbb8-198">Surface UEFI **デバイス** ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-198">Displays the Surface UEFI **Devices** page.</span></span> <span data-ttu-id="1fbb8-199">この設定を構成しないと、[デバイス] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-199">If you do not configure this setting,  the Devices page is displayed.</span></span>                                                                                                                     |
| <span data-ttu-id="1fbb8-200">Boot</span><span class="sxs-lookup"><span data-stu-id="1fbb8-200">Boot</span></span>                               | <span data-ttu-id="1fbb8-201">Surface UEFI **ブート** ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-201">Displays the Surface UEFI **Boot** page.</span></span> <span data-ttu-id="1fbb8-202">この設定を構成しない場合、[ブート] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-202">If you do not configure this setting, the Boot page is displayed.</span></span>                                                                                                                                                            |
| <span data-ttu-id="1fbb8-203">DateTime</span><span class="sxs-lookup"><span data-stu-id="1fbb8-203">DateTime</span></span>                           | <span data-ttu-id="1fbb8-204">Surface UEFI の [ **DateTime** ] ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-204">Displays the Surface UEFI **DateTime** page.</span></span> <span data-ttu-id="1fbb8-205">この設定を構成しない場合、[DateTime] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-205">If you do not configure this setting, the DateTime page is displayed.</span></span>                                                                                                                |
| <span data-ttu-id="1fbb8-206">EnableOSMigration</span><span class="sxs-lookup"><span data-stu-id="1fbb8-206">EnableOSMigration</span></span>                          | <span data-ttu-id="1fbb8-207">Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-207">Allows you to migrate Surface Hub 2 from Windows 10 Team to Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="1fbb8-208">この設定を構成しない場合、Surface Hub 2 のデバイスでは、Windows 10 Team OS のみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-208">If you do not configure this setting, Surface Hub 2 devices can only run Windows 10 Team OS.</span></span>   <span data-ttu-id="1fbb8-209">注: Windows 10 Team と Windows 10 Pro/Enterprise の間のデュアルブートは Surface Hub 2 では利用できません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-209">Note: Dual booting between Windows 10 Team and Windows 10 Pro/Enterprise  is not available on Surface Hub 2.</span></span>                                                                                                           |


>[!NOTE]
><span data-ttu-id="1fbb8-210">SEMM 構成パッケージを作成すると、図3に示すように、 **成功** したページに2つの文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-210">When you create a SEMM configuration package, two characters are shown on the **Successful** page, as shown in Figure 3.</span></span>

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*<span data-ttu-id="1fbb8-212">図 3. </span><span class="sxs-lookup"><span data-stu-id="1fbb8-212">Figure 3.</span></span> <span data-ttu-id="1fbb8-213">成功したページの証明書の拇印の最後の2文字を表示する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-213">Display of the last two characters of the certificate thumbprint on the Successful page</span></span>*

<span data-ttu-id="1fbb8-214">これらの文字は、証明書の拇印の最後の2文字であり、書き留めたり記録したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-214">These characters are the last two characters of the certificate thumbprint and should be written down or recorded.</span></span> <span data-ttu-id="1fbb8-215">図4に示すように、Surface デバイス上の SEMM での登録を確認するために文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-215">The characters are required to confirm enrollment in SEMM on a Surface device, as shown in Figure 4.</span></span>

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*<span data-ttu-id="1fbb8-217">図 4: </span><span class="sxs-lookup"><span data-stu-id="1fbb8-217">Figure 4.</span></span> <span data-ttu-id="1fbb8-218">Semm 証明書拇印での SEMM の登録確認</span><span class="sxs-lookup"><span data-stu-id="1fbb8-218">Enrollment confirmation in SEMM with the SEMM certificate thumbprint</span></span>*

>[!NOTE]
><span data-ttu-id="1fbb8-219">証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開くと、いつでも拇印を読むことができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-219">Administrators with access to the certificate file (.pfx) can read the thumbprint at any time by opening the .pfx file in CertMgr.</span></span> <span data-ttu-id="1fbb8-220">CertMgr で拇印を表示するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-220">To view the thumbprint with CertMgr, follow this process:</span></span>
>1. <span data-ttu-id="1fbb8-221">.Pfx ファイルを右クリックし、[ **開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-221">Right-click the .pfx file, and then click **Open**.</span></span>
>2. <span data-ttu-id="1fbb8-222">ナビゲーションウィンドウでフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-222">Expand the folder in the navigation pane.</span></span>
>3. <span data-ttu-id="1fbb8-223">**[証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-223">Click **Certificates**.</span></span>
>4. <span data-ttu-id="1fbb8-224">メインウィンドウで証明書を右クリックし、[ **開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-224">Right-click your certificate in the main pane, and then click **Open**.</span></span>
>5. <span data-ttu-id="1fbb8-225">[ **詳細** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-225">Click the **Details** tab.</span></span>
>6. <span data-ttu-id="1fbb8-226">[表示] ドロップダウンメニューで [**すべて**] または [**プロパティ** **]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-226">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
>7. <span data-ttu-id="1fbb8-227">フィールドの **拇印**を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-227">Select the field **Thumbprint**.</span></span>

<span data-ttu-id="1fbb8-228">SEMM で Surface デバイスを登録したり、構成パッケージから UEFI 構成を適用したりするには、必要な操作は、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行することだけです。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-228">To enroll a Surface device in SEMM or to apply the UEFI configuration from a configuration package, all you need to do is run the .msi file with administrative privileges on the intended Surface device.</span></span> <span data-ttu-id="1fbb8-229">[Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023)や[Microsoft 展開ツールキット](https://technet.microsoft.com/windows/dn475741)などの、アプリケーションの展開やオペレーティングシステムの展開テクノロジを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-229">You can use application deployment or operating system deployment technologies such as [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) or the [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741).</span></span> <span data-ttu-id="1fbb8-230">SEMM でデバイスを登録する場合、デバイスでの登録を確認するために物理的に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-230">When you enroll a device in SEMM you must be physically present to confirm the enrollment on the device.</span></span> <span data-ttu-id="1fbb8-231">既に SEMM に登録されているデバイスに構成を適用する場合は、ユーザーの操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-231">User interaction is not required when you apply a configuration to devices that are already enrolled in SEMM.</span></span>

<span data-ttu-id="1fbb8-232">Semm で Surface デバイスを登録する方法、または SEMM を使って surface UEFI 構成を適用する方法の詳しい手順については、「 [semm を使って surface デバイスを登録して構成](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-232">For a step-by-step walkthrough of how to enroll a Surface device in SEMM or apply a Surface UEFI configuration with SEMM, see [Enroll and configure Surface devices with SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).</span></span>

### <span data-ttu-id="1fbb8-233">パッケージのリセット</span><span class="sxs-lookup"><span data-stu-id="1fbb8-233">Reset package</span></span>

<span data-ttu-id="1fbb8-234">Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除するために、1つのタスクを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-234">A Surface UEFI reset package is used to perform only one task — to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="1fbb8-235">リセットパッケージには、デバイスのファームウェアから SEMM 証明書を削除する、または UEFI 設定を出荷時の既定にリセットするための、署名された手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-235">The reset package contains signed instructions to remove the SEMM certificate from the device’s firmware and to reset UEFI settings to factory default.</span></span> <span data-ttu-id="1fbb8-236">Surface UEFI 構成パッケージと同様に、リセットパッケージは Surface デバイスでプロビジョニングされた同じ SEMM 証明書で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-236">Like a Surface UEFI configuration package, a reset package must be signed with the same SEMM certificate that is provisioned on the Surface device.</span></span> <span data-ttu-id="1fbb8-237">SEMM reset パッケージを作成するときは、リセットする Surface デバイスのシリアル番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-237">When you create a SEMM reset package, you are required to supply the serial number of the Surface device you intend to reset.</span></span> <span data-ttu-id="1fbb8-238">SEMM リセットパッケージはユニバーサルではなく、1つのデバイスに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-238">SEMM reset packages are not universal and are specific to one device.</span></span>

### <span data-ttu-id="1fbb8-239">回復要求</span><span class="sxs-lookup"><span data-stu-id="1fbb8-239">Recovery request</span></span>

<span data-ttu-id="1fbb8-240">一部のシナリオでは、Surface UEFI リセットパッケージを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-240">In some scenarios, it may be impossible to use a Surface UEFI reset package.</span></span> <span data-ttu-id="1fbb8-241">(たとえば、Surface デバイスで Windows が使用できなくなった場合など)。このようなシナリオでは、回復要求操作によって、surface デバイスの (図5に表示されている) Surface UEFI の [ **エンタープライズ管理** ] ページを、semm から登録解除できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-241">(For example, if Windows becomes unusable on the Surface device.) In these scenarios you can unenroll the Surface device from SEMM through the **Enterprise Management** page of Surface UEFI (shown in Figure 5) with a Recovery Request operation.</span></span>

![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*<span data-ttu-id="1fbb8-243">図 5: </span><span class="sxs-lookup"><span data-stu-id="1fbb8-243">Figure 5.</span></span> <span data-ttu-id="1fbb8-244">[エンタープライズ管理] ページで SEMM 回復要求を開始する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-244">Initiate a SEMM recovery request on the Enterprise Management page</span></span>*

<span data-ttu-id="1fbb8-245">[ **エンタープライズ管理** ] ページのプロセスを使用して Surface デバイス上の semm をリセットすると、リセット要求が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-245">When you use the process on the **Enterprise Management** page to reset SEMM on a Surface device, you are provided with a Reset Request.</span></span> <span data-ttu-id="1fbb8-246">このリセット要求は、ファイルとして USB ドライブに保存するか、テキストとしてコピーするか、モバイルデバイスを使用して簡単にメールや送信先を送信する QR コードとして読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-246">This Reset Request can be saved as a file to a USB drive, copied as text, or read as a QR Code with a mobile device to be easily emailed or messaged.</span></span> <span data-ttu-id="1fbb8-247">Microsoft Surface UEFI Configurator のリセット要求オプションを使用して、リセット要求ファイルを読み込むか、リセット要求のテキストまたは QR コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-247">Use the Microsoft Surface UEFI Configurator Reset Request option to load a Reset Request file or enter the Reset Request text or QR Code.</span></span> <span data-ttu-id="1fbb8-248">Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスに入力できる確認コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-248">Microsoft Surface UEFI Configurator will generate a verification code that can be entered on the Surface device.</span></span> <span data-ttu-id="1fbb8-249">Surface デバイスにコードを入力し、[ **再起動**] をクリックすると、デバイスは semm からアン登録されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-249">If you enter the code on the Surface device and click **Restart**, the device will be unenrolled from SEMM.</span></span> 

>[!NOTE]
><span data-ttu-id="1fbb8-250">再設定要求は、作成後2時間後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-250">A Reset Request expires two hours after it is created.</span></span>

<span data-ttu-id="1fbb8-251">SEMM から Surface デバイスの登録を解除する方法についての詳しいチュートリアルについては、「 [SEMM からのサーデバイスの](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)登録解除」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-251">For a step-by-step walkthrough of how to unenroll Surface devices from SEMM, see [Unenroll Surface devices from SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).</span></span>

## <span data-ttu-id="1fbb8-252">Surface Enterprise 管理モードの証明書の要件</span><span class="sxs-lookup"><span data-stu-id="1fbb8-252">Surface Enterprise Management Mode certificate requirements</span></span>
<span data-ttu-id="1fbb8-253">Microsoft Surface UEFI コンフィギュレーターで SEMM を使用するには、UEFI 設定を適用する前に、証明書を使って構成ファイルの署名を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-253">Using SEMM with Microsoft Surface UEFI Configurator requires a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="1fbb8-254">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI の設定を変更できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-254">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span>

>[!NOTE]
><span data-ttu-id="1fbb8-255">Semm 証明書は、登録されている Surface デバイスで SEMM または Surface UEFI の設定を変更する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-255">The SEMM certificate is required to perform any modification to SEMM or Surface UEFI settings on enrolled Surface devices.</span></span> <span data-ttu-id="1fbb8-256">SEMM 証明書が破損または紛失した場合、SEMM は削除またはリセットできません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-256">If the SEMM certificate is corrupted or lost, SEMM cannot be removed or reset.</span></span> <span data-ttu-id="1fbb8-257">必要に応じて、バックアップと復元に適したソリューションを使用して、SEMM 証明書を管理します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-257">Manage your SEMM certificate accordingly with an appropriate solution for backup and recovery.</span></span>

<span data-ttu-id="1fbb8-258">Microsoft Surface UEFI コンフィギュレーターツールで作成されたパッケージは、証明書で署名されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-258">Packages created with the Microsoft Surface UEFI Configurator tool are signed with a certificate.</span></span> <span data-ttu-id="1fbb8-259">この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI の設定を変更できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-259">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span> 
### <span data-ttu-id="1fbb8-260">推奨される証明書の設定</span><span class="sxs-lookup"><span data-stu-id="1fbb8-260">Recommended certificate settings</span></span>
<span data-ttu-id="1fbb8-261">SEMM 証明書には、次の設定が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-261">The following settings are recommended for the SEMM certificate:</span></span>

* <span data-ttu-id="1fbb8-262">**キーアルゴリズム** – RSA</span><span class="sxs-lookup"><span data-stu-id="1fbb8-262">**Key Algorithm** – RSA</span></span> 
* <span data-ttu-id="1fbb8-263">**キーの長さ** –2048</span><span class="sxs-lookup"><span data-stu-id="1fbb8-263">**Key Length** – 2048</span></span>
* <span data-ttu-id="1fbb8-264">**ハッシュアルゴリズム** – SHA-256</span><span class="sxs-lookup"><span data-stu-id="1fbb8-264">**Hash Algorithm** – SHA-256</span></span>
* <span data-ttu-id="1fbb8-265">**種類** – SSL サーバー認証</span><span class="sxs-lookup"><span data-stu-id="1fbb8-265">**Type** – SSL Server Authentication</span></span>
* <span data-ttu-id="1fbb8-266">**キー使用法** –デジタル署名、キーの暗号化</span><span class="sxs-lookup"><span data-stu-id="1fbb8-266">**Key Usage** – Digital signature, Key Encipherment</span></span>
* <span data-ttu-id="1fbb8-267">**プロバイダー** – Microsoft エンハンス RSA および AES 暗号化プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1fbb8-267">**Provider** – Microsoft Enhanced RSA and AES Cryptographic Provider</span></span>
* <span data-ttu-id="1fbb8-268">**有効期限** : 証明書の作成から15ヶ月</span><span class="sxs-lookup"><span data-stu-id="1fbb8-268">**Expiration Date** – 15 Months from certificate creation</span></span>
* <span data-ttu-id="1fbb8-269">**キーエクスポートポリシー** –エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="1fbb8-269">**Key Export Policy** – Exportable</span></span>

<span data-ttu-id="1fbb8-270">また、SEMM 証明書は、中間証明機関 (CA) が SEMM 専用であり、証明書の失効を有効にする2階層の公開キー基盤 (PKI) アーキテクチャで認証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-270">It is also recommended that the SEMM certificate be authenticated in a two-tier public key infrastructure (PKI) architecture where the intermediate certification authority (CA) is dedicated to SEMM, enabling certificate revocation.</span></span> <span data-ttu-id="1fbb8-271">2階層の PKI 構成の詳細については、「 [テストラボガイド: AD CS 2 階層の Pki 階層の展開](https://technet.microsoft.com/library/hh831348)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-271">For more information about a two-tier PKI configuration, see [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://technet.microsoft.com/library/hh831348).</span></span>

### <span data-ttu-id="1fbb8-272">自己署名証明書</span><span class="sxs-lookup"><span data-stu-id="1fbb8-272">Self-signed certificate</span></span> 
<span data-ttu-id="1fbb8-273">次の PowerShell スクリプト例では、コンセプトのあるシナリオで使用する自己署名証明書を作成する方法についてご紹介します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-273">You can use the following example PowerShell script to create a self-signed certificate for use in proof-of-concept scenarios.</span></span>
<span data-ttu-id="1fbb8-274">このスクリプトを使用するには、次のテキストをメモ帳にコピーして、ファイルを PowerShell スクリプト (. ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-274">To use this script, copy the following text into Notepad and save the file as a PowerShell script (.ps1).</span></span> <span data-ttu-id="1fbb8-275">注: このスクリプトでは、というパスワードの証明書を作成し `12345678` ます。このスクリプトによって生成された証明書は、運用環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-275">Note: This script creates a certificate with a password of `12345678`.The certificate generated by this script is not recommended for production environments.</span></span>
  
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

>[!IMPORTANT]
><span data-ttu-id="1fbb8-276">SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書を秘密キーでエクスポートし、パスワード保護を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-276">For use with SEMM and Microsoft Surface UEFI Configurator, the certificate must be exported with the private key and with password protection.</span></span> <span data-ttu-id="1fbb8-277">Microsoft Surface UEFI コンフィギュレーターは、必要に応じて SEMM 証明書ファイル (.pfx) と証明書のパスワードを選択するように求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-277">Microsoft Surface UEFI Configurator will prompt you to select the SEMM certificate file (.pfx) and certificate password when it is required.</span></span>

1.  <span data-ttu-id="1fbb8-278">スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-278">Create a folder on your C: drive where you will save the script; for example, C:\SEMM.</span></span>
2.  <span data-ttu-id="1fbb8-279">このサンプルスクリプトをメモ帳または同等のテキストエディターにコピーして、ファイルを PowerShell スクリプト (ps1) として保存します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-279">Copy the example script into Notepad or equivalent text editor and save the file as a PowerShell script (.ps1).</span></span>
3.  <span data-ttu-id="1fbb8-280">管理者の資格情報を使って PC にサインインし、管理者特権の PowerShell セッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-280">Sign into your PC with administrator credentials and open an elevated PowerShell session.</span></span>
4.  <span data-ttu-id="1fbb8-281">スクリプトの実行を許可するようにアクセス許可が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-281">Ensure your permissions are set to allow scripts to run.</span></span> <span data-ttu-id="1fbb8-282">既定では、実行ポリシーを変更しない限り、スクリプトは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-282">By default, scripts are blocked from running unless you modify the execution policy.</span></span> <span data-ttu-id="1fbb8-283">詳細については、「実行ポリシーについて」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-283">To learn more, see About Execution Policies.</span></span>
5.  <span data-ttu-id="1fbb8-284">コマンドプロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-284">At the command prompt, enter the full path of the script and then press Enter.</span></span> <span data-ttu-id="1fbb8-285">このスクリプトでは、TempOwner というデモ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-285">The script creates a Demo Certificate named TempOwner.pfx.</span></span>

<span data-ttu-id="1fbb8-286">または、PowerShell を使用して、独自の自己署名証明書を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-286">Alternatively, you can create your own self-signed certificate using PowerShell.</span></span> <span data-ttu-id="1fbb8-287">詳細については、次の PowerShell ドキュメントを参照してください。 [新-SelfSignedCertificate] (https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)</span><span class="sxs-lookup"><span data-stu-id="1fbb8-287">For more information, see the following PowerShell documentation: [New-SelfSignedCertificate] (https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)</span></span>




>[!NOTE]
><span data-ttu-id="1fbb8-288">PKI インフラストラクチャでオフラインルートを使用している組織の場合、Microsoft Surface UEFI コンフィギュレーターは、ルート CA に接続されている環境で SEMM 証明書を認証するために実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-288">For organizations that use an offline root in their PKI infrastructure, Microsoft Surface UEFI Configurator must be run in an environment connected to the root CA to authenticate the SEMM certificate.</span></span> <span data-ttu-id="1fbb8-289">Microsoft Surface UEFI コンフィギュレーターによって生成されたパッケージは、ファイルとして転送することができます。そのため、USB スティックなどのリムーバブル記憶域を使用して、オフラインネットワーク環境以外の場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-289">The packages generated by Microsoft Surface UEFI Configurator can be transferred as files and therefore can be transferred outside the offline network environment with removable storage, such as a USB stick.</span></span>

### <span data-ttu-id="1fbb8-290">証明書の管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="1fbb8-290">Managing certificates FAQ</span></span>

<span data-ttu-id="1fbb8-291">推奨される *最小* の長さは15か月です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-291">The recommended *minimum* length is 15 months.</span></span> <span data-ttu-id="1fbb8-292">有効期限が15か月以内の証明書を使用するか、有効期限が15か月を超える証明書を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-292">You can use a certificate that expires in less than 15 months or use a certificate that expires in longer than 15 months.</span></span>

>[!NOTE] 
><span data-ttu-id="1fbb8-293">証明書の有効期限が切れた場合は、自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-293">When a certificate expires, it does not automatically renew.</span></span> 


**<span data-ttu-id="1fbb8-294">有効期限が切れた証明書は、SEMM 登録済みデバイスの機能に影響しますか?</span><span class="sxs-lookup"><span data-stu-id="1fbb8-294">Will an expired certificate affect the functionality of SEMM-enrolled devices?</span></span>**<br><br>
<span data-ttu-id="1fbb8-295">いいえ。証明書は、SEMM の IT 管理者の管理タスクにのみ影響し、有効期限が切れたときにデバイスの機能に影響を与えることはありません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-295">No, a certificate only impacts IT admin management tasks in SEMM and has no effect on device functionality when it expires.</span></span>


**<span data-ttu-id="1fbb8-296">SEMM パッケージと証明書は、それがインストールされているすべてのコンピューターで更新する必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="1fbb8-296">Will the SEMM package and certificate need to be updated on all machines that have it?</span></span>**

<span data-ttu-id="1fbb8-297">SEMM のリセットまたは回復機能が必要な場合は、証明書が有効であり、期限切れになっていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-297">If you want SEMM reset or recovery to work, the certificate needs to be valid and not expired.</span></span> 

**<span data-ttu-id="1fbb8-298">注文した各サーフェスに対してパッケージを一括リセットできますか?</span><span class="sxs-lookup"><span data-stu-id="1fbb8-298">Can bulk reset packages be created for each surface that we order?</span></span> <span data-ttu-id="1fbb8-299">環境内のすべてのマシンをリセットするように構築することはできますか?</span><span class="sxs-lookup"><span data-stu-id="1fbb8-299">Can one be built that resets all machines in our environment?</span></span>**

<span data-ttu-id="1fbb8-300">特定のデバイスの種類に対して構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセットパッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-300">The PowerShell samples that create a config package for a specific device type can also be used to create a reset package that is serial-number independent.</span></span> <span data-ttu-id="1fbb8-301">証明書が有効な場合は、PowerShell を使用して、SEMM をリセットすることでリセットパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-301">If the certificate is still valid, you can create a reset package using PowerShell to reset SEMM.</span></span>

## <span data-ttu-id="1fbb8-302">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="1fbb8-302">Version History</span></span>


### <span data-ttu-id="1fbb8-303">バージョン2.73.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-303">Version 2.73.136.0</span></span>

<span data-ttu-id="1fbb8-304">SEMM のこのバージョンには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-304">This version of SEMM includes:</span></span>

- <span data-ttu-id="1fbb8-305">SEMM を使用して、Surface Hub2S でオーディオを無効にできるようになりました</span><span class="sxs-lookup"><span data-stu-id="1fbb8-305">Audio can now be disabled on Surface Hub2S using SEMM</span></span>
- <span data-ttu-id="1fbb8-306">Dock 2 用 Surface Pro X のサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-306">Support to Surface Pro X for Dock 2</span></span>
- <span data-ttu-id="1fbb8-307">Dock 2 関連操作のための UEFI Manager のサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-307">Support to UEFI Manager for Dock 2 related operations</span></span>
- <span data-ttu-id="1fbb8-308">Surface Go リセットパッケージのバグ修正</span><span class="sxs-lookup"><span data-stu-id="1fbb8-308">Surface Go reset package bug fix</span></span>
- <span data-ttu-id="1fbb8-309">Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-309">Support for migrating Surface Hub 2 devices from Windows 10 Team OS to Windows 10 Pro or Enterprise.</span></span>

### <span data-ttu-id="1fbb8-310">バージョン2.71.139.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-310">Version 2.71.139.0</span></span>

<span data-ttu-id="1fbb8-311">このバージョンの SEMM は、surface Dock 3、surface Pc 3、Surface Pro 7 の surface Dock 2 の管理機能のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-311">This version of SEMM adds support for Surface Dock 2 management features  for Surface Book 3, Surface Laptop 3, and Surface Pro 7 including:</span></span>

- <span data-ttu-id="1fbb8-312">オーディオ (ロック/ロック解除)、イーサネットおよび USB ポートを有効にする</span><span class="sxs-lookup"><span data-stu-id="1fbb8-312">Enabling audio (locking/unlocking), Ethernet and USB ports</span></span>
- <span data-ttu-id="1fbb8-313">認証されたホストと認証されていないホストの両方に対して、dock パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="1fbb8-313">Ability to create dock packages for both authenticated and unauthenticated hosts</span></span>

### <span data-ttu-id="1fbb8-314">バージョン2.70.130.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-314">Version 2.70.130.0</span></span>

<span data-ttu-id="1fbb8-315">SEMM のこのバージョンには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-315">This version of SEMM includes:</span></span>

- <span data-ttu-id="1fbb8-316">Surface Go 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-316">Support for Surface Go 2</span></span>
- <span data-ttu-id="1fbb8-317">Surface Book 3 のサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-317">Support for Surface Book 3</span></span>
- <span data-ttu-id="1fbb8-318">バグ修正</span><span class="sxs-lookup"><span data-stu-id="1fbb8-318">Bug fixes</span></span>


### <span data-ttu-id="1fbb8-319">バージョン2.59.139.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-319">Version 2.59.139.0</span></span>

* <span data-ttu-id="1fbb8-320">Surface Pro 7、Surface Pro X、Surface ノート Pc の 3 13.5 "と 15" のモデルを、Intel プロセッサでサポートします。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-320">Support for Surface Pro 7, Surface Pro X,  and Surface Laptop 3 13.5" and 15" models with Intel processor.</span></span> <span data-ttu-id="1fbb8-321">注: Surface ノート Pc 3 15 "AMD processor はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1fbb8-321">Note:  Surface Laptop 3 15" AMD processor is not supported.</span></span>

- <span data-ttu-id="1fbb8-322">Power on on Power 機能のサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-322">Support for Wake on Power feature</span></span>

### <span data-ttu-id="1fbb8-323">バージョン2.54.139.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-323">Version 2.54.139.0</span></span>
* <span data-ttu-id="1fbb8-324">Surface Hub 2S へのサポート</span><span class="sxs-lookup"><span data-stu-id="1fbb8-324">Support to Surface Hub 2S</span></span>
* <span data-ttu-id="1fbb8-325">バグ修正</span><span class="sxs-lookup"><span data-stu-id="1fbb8-325">Bug fixes</span></span>

### <span data-ttu-id="1fbb8-326">バージョン2.43.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-326">Version 2.43.136.0</span></span>
* <span data-ttu-id="1fbb8-327">Simulatenous を有効/無効にするサポート (複数)</span><span class="sxs-lookup"><span data-stu-id="1fbb8-327">Support to enable/disable simulatenous multithreating</span></span> 
* <span data-ttu-id="1fbb8-328">一部のデバイスで WiFi と Bluetooth の個別のオプションを使用する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-328">Separate options for WiFi and Bluetooth for some devices</span></span> 
* <span data-ttu-id="1fbb8-329">Surface Studio のバッテリー制限が削除されました</span><span class="sxs-lookup"><span data-stu-id="1fbb8-329">Battery Limit removed for Surface Studio</span></span> 

### <span data-ttu-id="1fbb8-330">バージョン2.26.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-330">Version 2.26.136.0</span></span>
* <span data-ttu-id="1fbb8-331">Surface Studio 2 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-331">Add support to Surface Studio 2</span></span>
* <span data-ttu-id="1fbb8-332">バッテリー制限機能</span><span class="sxs-lookup"><span data-stu-id="1fbb8-332">Battery Limit feature</span></span>

### <span data-ttu-id="1fbb8-333">バージョン2.21.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-333">Version 2.21.136.0</span></span>
* <span data-ttu-id="1fbb8-334">Surface Pro 6 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-334">Add support to Surface Pro 6</span></span>
* <span data-ttu-id="1fbb8-335">Surface ノート Pc にサポートを追加する2</span><span class="sxs-lookup"><span data-stu-id="1fbb8-335">Add support to Surface Laptop 2</span></span>

### <span data-ttu-id="1fbb8-336">バージョン2.14.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-336">Version 2.14.136.0</span></span>
* <span data-ttu-id="1fbb8-337">Surface Go にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-337">Add support to Surface Go</span></span>

### <span data-ttu-id="1fbb8-338">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-338">Version 2.9.136.0</span></span>
* <span data-ttu-id="1fbb8-339">Surface Book 2 にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-339">Add support to Surface Book 2</span></span>
* <span data-ttu-id="1fbb8-340">Surface Pro LTE にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-340">Add support to Surface Pro LTE</span></span>
* <span data-ttu-id="1fbb8-341">ユーザー補助機能の改善</span><span class="sxs-lookup"><span data-stu-id="1fbb8-341">Accessibility improvements</span></span>

### <span data-ttu-id="1fbb8-342">バージョン1.0.74.0</span><span class="sxs-lookup"><span data-stu-id="1fbb8-342">Version 1.0.74.0</span></span>
* <span data-ttu-id="1fbb8-343">Surface のノート Pc にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-343">Add support to Surface Laptop</span></span>
* <span data-ttu-id="1fbb8-344">Surface Pro にサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-344">Add support to Surface Pro</span></span>
* <span data-ttu-id="1fbb8-345">バグ修正と全般的な改善</span><span class="sxs-lookup"><span data-stu-id="1fbb8-345">Bug fixes and general improvement</span></span>

## <span data-ttu-id="1fbb8-346">関連トピック</span><span class="sxs-lookup"><span data-stu-id="1fbb8-346">Related topics</span></span>

- [<span data-ttu-id="1fbb8-347">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="1fbb8-347">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)
- [<span data-ttu-id="1fbb8-348">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="1fbb8-348">Unenroll Surface devices from SEMM</span></span>](unenroll-surface-devices-from-semm.md)
- [<span data-ttu-id="1fbb8-349">SEMM を使用して Surface Dock 2 ポートを保護する</span><span class="sxs-lookup"><span data-stu-id="1fbb8-349">Secure Surface Dock 2 ports with SEMM</span></span>](secure-surface-dock-ports-semm.md)
