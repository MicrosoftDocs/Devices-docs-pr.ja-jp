---
title: Surface Enterprise 管理モード (Surface)
description: Surface UEFI を使った Surface デバイスのこの機能によって、組織内のファームウェア設定をセキュリティで保護および管理する方法について説明します。
keywords: uefi, 構成, ファームウェア, セキュア, semm
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
ms.date: 01/15/2021
ms.openlocfilehash: e6f81639253c646f5d3956243a80f4d61c91028a
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271421"
---
# <span data-ttu-id="9c92f-104">Microsoft Surface Enterprise 管理モード</span><span class="sxs-lookup"><span data-stu-id="9c92f-104">Microsoft Surface Enterprise Management Mode</span></span>

<span data-ttu-id="9c92f-105">Microsoft Surface Enterprise Management Mode (SEMM) は、Surface UEFI を備える Surface デバイスの機能で、組織内のファームウェア設定をセキュリティで保護および管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-105">Microsoft Surface Enterprise Management Mode (SEMM) is a feature of Surface devices with Surface UEFI that allows you to secure and manage firmware settings within your organization.</span></span> <span data-ttu-id="9c92f-106">SEMM を使用すると、IT 担当者は UEFI 設定の構成を準備し、Surface デバイスにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-106">With SEMM, IT professionals can prepare configurations of UEFI settings and install them on a Surface device.</span></span> <span data-ttu-id="9c92f-107">SEMM では、UEFI 設定を構成する機能に加えて、証明書を使用して、不正な改ざんや削除から構成を保護します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-107">In addition to the ability to configure UEFI settings, SEMM also uses a certificate to protect the configuration from unauthorized tampering or removal.</span></span> <span data-ttu-id="9c92f-108">SEMM は、Surface Hub 2S を Windows 10 Pro および Enterprise に移行できる要件です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-108">SEMM is a requirement to be able to migrate a Surface Hub 2S to Windows 10 Pro and Enterprise.</span></span>

>[!NOTE]
><span data-ttu-id="9c92f-109">SEMM は、Surface UEFI ファームウェアを持つデバイスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-109">SEMM is only available on devices with Surface UEFI firmware.</span></span> <span data-ttu-id="9c92f-110">これは、Intel プロセッサを搭載した Surface Pro 7+、Surface Pro X、Surface Hub 2S、Surface Laptop 3 の商用 SKU、Surface Laptop Go など、他のほとんどの Surface デバイスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-110">This comprises most other Surface devices including Surface Pro 7+, Surface Pro X, Surface Hub 2S, and Surface Laptop 3 commercial SKUs with an Intel processor, and Surface Laptop Go.</span></span> <span data-ttu-id="9c92f-111">SEMM は、AMD プロセッサを搭載した 15" Surface Laptop 3 SKU ではサポートされていません (製品 SKU としてのみ利用可能)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-111">SEMM is not supported on the 15" Surface Laptop 3 SKU with AMD processor (only available as a retail SKU).</span></span> 

<span data-ttu-id="9c92f-112">Surface デバイスは SEMM によって構成され、SEMM 証明書で保護されている場合、SEMM *に登録されたと* 見なされます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-112">When Surface devices are configured by SEMM and secured with the SEMM certificate, they are considered *enrolled* in SEMM.</span></span> <span data-ttu-id="9c92f-113">SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM で登録解除されたと見なされます。 \*\*</span><span class="sxs-lookup"><span data-stu-id="9c92f-113">When the SEMM certificate is removed and control of UEFI settings is returned to the user of the device, the Surface device is considered *unenrolled* in SEMM.</span></span>

<span data-ttu-id="9c92f-114">SEMM の管理と Surface デバイスの登録に使用できる管理オプションには、スタンドアロン ツールと Microsoft Endpoint Configuration Manager との統合の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-114">There are two administrative options you can use to manage SEMM and enroll Surface devices – a standalone tool or integration with Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="9c92f-115">この記事では、SEMM スタンドアロン ツール (Microsoft Surface UEFI Configurator と呼ばれる) について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-115">The SEMM standalone tool, called the Microsoft Surface UEFI Configurator, is described in this article.</span></span> <span data-ttu-id="9c92f-116">Microsoft Endpoint Configuration Manager で SEMM を管理する方法の詳細については [、「Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)を使用して SEMM を使用してデバイスを管理する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c92f-116">For more information about how to manage SEMM with Microsoft Endpoint Configuration Manager, see [Use Microsoft Endpoint Configuration Manager to manage devices with SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).</span></span>


## <span data-ttu-id="9c92f-117">Microsoft Surface UEFI コンフィエーター</span><span class="sxs-lookup"><span data-stu-id="9c92f-117">Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="9c92f-118">図 1 に示すように、SEMM のプライマリ ワークスペースは Microsoft Surface UEFI コンフィエーターです。</span><span class="sxs-lookup"><span data-stu-id="9c92f-118">The primary workspace of SEMM is Microsoft Surface UEFI Configurator, as shown in Figure 1.</span></span> <span data-ttu-id="9c92f-119">Microsoft Surface UEFI コンフィグレータは、Surface デバイスでの SEMM の登録、構成、および登録解除に使用される Windows インストーラー (.msi) パッケージまたは WinPE イメージを作成するために使用されるツールです。</span><span class="sxs-lookup"><span data-stu-id="9c92f-119">Microsoft Surface UEFI Configurator is a tool used to create Windows Installer (.msi) packages or WinPE images used to enroll, configure, and unenroll SEMM on a Surface device.</span></span> <span data-ttu-id="9c92f-120">これらのパッケージには、UEFI の設定が指定された構成ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c92f-120">These packages contain a configuration file where the settings for UEFI are specified.</span></span> <span data-ttu-id="9c92f-121">SEMM パッケージには、ファームウェアにインストールおよび保存され、UEFI 設定を適用する前に構成ファイルの署名を確認するために使用される証明書も含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c92f-121">SEMM packages also contain a certificate, which is installed and stored in firmware and used to verify the signature of configuration files before UEFI settings are applied.</span></span>

>[!NOTE]
><span data-ttu-id="9c92f-122">Surface UEFI コンフィエーターと SEMM を使用して、Surface ドック 2 のポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-122">You can now use Surface UEFI Configurator and SEMM to manage ports on Surface Dock 2.</span></span> <span data-ttu-id="9c92f-123">詳細については [、「SEMM によるセキュア Surface Dock 2 ポート」を参照してください](secure-surface-dock-ports-semm.md)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-123">To learn more, see [Secure Surface Dock 2 ports with SEMM](secure-surface-dock-ports-semm.md).</span></span>

![Microsoft Surface UEFI コンフィエーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*<span data-ttu-id="9c92f-125">図 1. </span><span class="sxs-lookup"><span data-stu-id="9c92f-125">Figure 1.</span></span> <span data-ttu-id="9c92f-126">Microsoft Surface UEFI コンフィエーター</span><span class="sxs-lookup"><span data-stu-id="9c92f-126">Microsoft Surface UEFI Configurator</span></span>*


<span data-ttu-id="9c92f-127">Microsoft Surface UEFI コンフィエーター ツールは、次の 3 つのモードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-127">You can use the Microsoft Surface UEFI Configurator tool in three modes:</span></span>

* <span data-ttu-id="9c92f-128">[Surface UEFI 構成パッケージ](#configuration-package)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-128">[Surface UEFI Configuration Package](#configuration-package).</span></span> <span data-ttu-id="9c92f-129">このモードを使って Surface UEFI 構成パッケージを作成し、SURFACE デバイスを SEMM に登録し、登録済みデバイスで UEFI 設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-129">Use this mode to create a Surface UEFI configuration package to enroll a Surface device in SEMM and to configure UEFI settings on enrolled devices.</span></span>
* <span data-ttu-id="9c92f-130">[Surface UEFI リセット パッケージ](#reset-package)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-130">[Surface UEFI Reset Package](#reset-package).</span></span> <span data-ttu-id="9c92f-131">SEMM から Surface デバイスを登録解除するには、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-131">Use this mode to unenroll a Surface device from SEMM.</span></span>
* <span data-ttu-id="9c92f-132">[Surface UEFI 回復要求](#recovery-request)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-132">[Surface UEFI Recovery Request](#recovery-request).</span></span> <span data-ttu-id="9c92f-133">このモードを使用して、パッケージのリセット操作が失敗した SEMM から Surface デバイスを登録解除する回復要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-133">Use this mode to respond to a recovery request to unenroll a Surface device from SEMM where a Reset Package operation is not successful.</span></span>


#### <span data-ttu-id="9c92f-134">Microsoft Surface UEFI コンフィエーターのダウンロード</span><span class="sxs-lookup"><span data-stu-id="9c92f-134">Download Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="9c92f-135">Microsoft Surface UEFI コンフィエーターは [、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703) ダウンロード センターの Surface Tools for IT ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-135">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

### <span data-ttu-id="9c92f-136">構成パッケージ</span><span class="sxs-lookup"><span data-stu-id="9c92f-136">Configuration package</span></span>

<span data-ttu-id="9c92f-137">Surface UEFI 構成パッケージは、Surface デバイスに SEMM を実装および管理するための主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="9c92f-137">Surface UEFI configuration packages are the primary mechanism to implement and manage SEMM on Surface devices.</span></span> <span data-ttu-id="9c92f-138">これらのパッケージには、図 2 に示すように、Microsoft Surface UEFI Configurator でのパッケージの作成時に指定された UEFI 設定の構成ファイルと証明書ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c92f-138">These packages contain a configuration file of UEFI settings specified during creation of the package in Microsoft Surface UEFI Configurator and a certificate file, as shown in Figure 2.</span></span> <span data-ttu-id="9c92f-139">SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアに証明書ファイルがプロビジョニングされ、デバイスが SEMM に登録されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-139">When a configuration package is run for the first time on a Surface device that is not already enrolled in SEMM, it provisions the certificate file in the device’s firmware and enrolls the device in SEMM.</span></span> <span data-ttu-id="9c92f-140">SEMM にデバイスを登録するときに、証明書ファイルを保存して登録を完了する前に、SEMM 証明書の拇印の最後の 2 桁を指定して操作の確認を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-140">When enrolling a device in SEMM, you will be prompted to confirm the operation by providing the last two digits of the SEMM certificate thumbprint before the certificate file is stored and the enrollment can complete.</span></span> <span data-ttu-id="9c92f-141">この確認では、登録時にユーザーがデバイスに物理的に存在し、確認を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-141">This confirmation requires a user be physically present at the device at the time of enrollment to perform the confirmation.</span></span>

![証明書を使用して SEMM 構成パッケージをセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*<span data-ttu-id="9c92f-143">図 2. </span><span class="sxs-lookup"><span data-stu-id="9c92f-143">Figure 2.</span></span> <span data-ttu-id="9c92f-144">証明書を使用して SEMM 構成パッケージをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="9c92f-144">Secure a SEMM configuration package with a certificate</span></span>*

<span data-ttu-id="9c92f-145">SEMM [証明書の要件の詳細については](#surface-enterprise-management-mode-certificate-requirements) 、この記事の「Surface Enterprise 管理モード証明書の要件」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c92f-145">See the [Surface Enterprise Management Mode certificate requirements](#surface-enterprise-management-mode-certificate-requirements) section of this article for more information about the requirements for the SEMM certificate.</span></span>

>[!NOTE]
><span data-ttu-id="9c92f-146">SURFACE UEFI の [セキュリティ]、[デバイス]、[ブート構成]、または\*\*\*\*[エンタープライズ管理\*\*\*\*] ページを表示するために必要な SEMM で UEFI パスワードを指定することもできます。 \*\*\*\* \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9c92f-146">You can also specify a UEFI password with SEMM that is required to view the **Security**, **Devices**, **Boot Configuration**, or **Enterprise Management** pages of Surface UEFI.</span></span>

<span data-ttu-id="9c92f-147">デバイスを SEMM に登録すると、構成ファイルが読み取り、ファイルで指定された設定が UEFI に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-147">After a device is enrolled in SEMM, the configuration file is read and the settings specified in the file are applied to UEFI.</span></span> <span data-ttu-id="9c92f-148">SEMM に既に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名が、デバイスのファームウェアに格納されている証明書と対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-148">When you run a configuration package on a device that is already enrolled in SEMM, the signature of the configuration file is checked against the certificate that is stored in the device firmware.</span></span> <span data-ttu-id="9c92f-149">署名が一致しない場合、変更はデバイスに適用されません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-149">If the signature does not match, no changes are applied to the device.</span></span>

### <span data-ttu-id="9c92f-150">SEMM による Surface UEFI のデバイスの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="9c92f-150">Enable or disable devices in Surface UEFI with SEMM</span></span>

<span data-ttu-id="9c92f-151">以下に、SEMM で管理できるすべての利用可能なデバイスを示します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-151">The following list shows all the available devices you can manage in SEMM:</span></span>

* <span data-ttu-id="9c92f-152">USB ポートのドッキング</span><span class="sxs-lookup"><span data-stu-id="9c92f-152">Docking USB Port</span></span>
* <span data-ttu-id="9c92f-153">オンボード オーディオ</span><span class="sxs-lookup"><span data-stu-id="9c92f-153">On-board Audio</span></span>
* <span data-ttu-id="9c92f-154">DGPU</span><span class="sxs-lookup"><span data-stu-id="9c92f-154">DGPU</span></span>
* <span data-ttu-id="9c92f-155">タイプ カバー</span><span class="sxs-lookup"><span data-stu-id="9c92f-155">Type Cover</span></span>
* <span data-ttu-id="9c92f-156">Micro SD カード</span><span class="sxs-lookup"><span data-stu-id="9c92f-156">Micro SD Card</span></span>
* <span data-ttu-id="9c92f-157">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="9c92f-157">Front Camera</span></span>
* <span data-ttu-id="9c92f-158">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="9c92f-158">Rear Camera</span></span>
* <span data-ttu-id="9c92f-159">Windows Hello 用の赤外線カメラ</span><span class="sxs-lookup"><span data-stu-id="9c92f-159">Infrared Camera, for Windows Hello</span></span>
* <span data-ttu-id="9c92f-160">Bluetoothのみ</span><span class="sxs-lookup"><span data-stu-id="9c92f-160">Bluetooth Only</span></span>
* <span data-ttu-id="9c92f-161">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="9c92f-161">Wi-Fi and Bluetooth</span></span>
* <span data-ttu-id="9c92f-162">             LTE           </span><span class="sxs-lookup"><span data-stu-id="9c92f-162">LTE</span></span>

 >[!NOTE]
><span data-ttu-id="9c92f-163">[UEFI デバイス] ページに表示される組み込みデバイスは、デバイスまたは企業の環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-163">The built-in devices that appear in the UEFI Devices page may vary depending on your device or corporate environment.</span></span> <span data-ttu-id="9c92f-164">たとえば、UEFI デバイス ページは Surface Pro X ではサポートされていません。LTE は LTE 搭載デバイスでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-164">For example, the UEFI Devices page is not supported on Surface Pro X; LTE only appears on LTE-equipped devices.</span></span> 
### <span data-ttu-id="9c92f-165">SEMM を使用して詳細設定を構成する</span><span class="sxs-lookup"><span data-stu-id="9c92f-165">Configure advanced settings with SEMM</span></span>
**<span data-ttu-id="9c92f-166">表 1.</span><span class="sxs-lookup"><span data-stu-id="9c92f-166">Table 1.</span></span> <span data-ttu-id="9c92f-167">詳細設定</span><span class="sxs-lookup"><span data-stu-id="9c92f-167">Advanced settings</span></span>**

| <span data-ttu-id="9c92f-168">設定</span><span class="sxs-lookup"><span data-stu-id="9c92f-168">Setting</span></span>                            | <span data-ttu-id="9c92f-169">説明</span><span class="sxs-lookup"><span data-stu-id="9c92f-169">Description</span></span>                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="9c92f-170">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="9c92f-170">IPv6 for PXE Boot</span></span>                  | <span data-ttu-id="9c92f-171">PXE ブートの IPv6 サポートを管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-171">Allows you to manage IPv6 support for PXE boot.</span></span> <span data-ttu-id="9c92f-172">この設定を構成しない場合、PXE ブートの IPv6 サポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-172">If you do not configure this setting, IPv6 support for PXE boot is disabled.</span></span>                                                                               |
| <span data-ttu-id="9c92f-173">代替ブート</span><span class="sxs-lookup"><span data-stu-id="9c92f-173">Alternate Boot</span></span>                     | <span data-ttu-id="9c92f-174">ブート中にボリューム ダウン ボタンと電源ボタンの両方を押すことで、代替ブート順序の使用を管理して USB デバイスまたはイーサネット デバイスで直接起動できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-174">Allows you to manage use of an Alternate boot order to boot directly to a USB or Ethernet device by pressing both the Volume Down button and Power button during boot.</span></span> <span data-ttu-id="9c92f-175">この設定を構成しない場合は、代替ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-175">If you do not configure this setting, Alternate boot is enabled.</span></span> |
| <span data-ttu-id="9c92f-176">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="9c92f-176">Boot Order Lock</span></span>                    | <span data-ttu-id="9c92f-177">変更を防ぐためにブート順序をロックできます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-177">Allows you to lock the boot order to prevent changes.</span></span> <span data-ttu-id="9c92f-178">この設定を構成しない場合、ブート 順序ロックは無効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-178">If you do not configure this setting, Boot Order Lock is disabled.</span></span>                                                                                                        |
| <span data-ttu-id="9c92f-179">USB ブート</span><span class="sxs-lookup"><span data-stu-id="9c92f-179">USB Boot</span></span>                           | <span data-ttu-id="9c92f-180">USB デバイスの起動を管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-180">Allows you to manage booting to USB devices.</span></span> <span data-ttu-id="9c92f-181">この設定を構成しない場合は、USB ブートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-181">If you do not configure this setting, USB Boot is enabled.</span></span>                                                                                                                 |
| <span data-ttu-id="9c92f-182">ネットワーク スタック</span><span class="sxs-lookup"><span data-stu-id="9c92f-182">Network Stack</span></span>                      | <span data-ttu-id="9c92f-183">ネットワーク スタックのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-183">Allows you to manage Network Stack boot settings.</span></span> <span data-ttu-id="9c92f-184">この設定を構成しない場合、ネットワーク スタックのブート設定を管理する機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-184">If you do not configure this setting,  the ability to manage Network Stack boot settings is disabled.</span></span>                                                                                                           |
| <span data-ttu-id="9c92f-185">自動電源オン</span><span class="sxs-lookup"><span data-stu-id="9c92f-185">Auto Power On</span></span>                      | <span data-ttu-id="9c92f-186">自動電源オンのブート設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-186">Allows you to manage Auto Power On boot settings.</span></span> <span data-ttu-id="9c92f-187">この設定を構成しない場合は、自動電源が有効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-187">If you do not configure this setting, Auto Power on is enabled.</span></span>                                                                                                        |
| <span data-ttu-id="9c92f-188">同時マルチスレッド (SMT)</span><span class="sxs-lookup"><span data-stu-id="9c92f-188">Simultaneous Multi-Threading (SMT)</span></span> | <span data-ttu-id="9c92f-189">同時マルチスレッド (SMT) を管理して、ハイパースレッジを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-189">Allows you to manage Simultaneous Multi-Threading (SMT) to enable or disable hyperthreading.</span></span> <span data-ttu-id="9c92f-190">この設定を構成しない場合は、SMT が有効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-190">If you do not configure this setting, SMT is enabled.</span></span>                                                  |
|<span data-ttu-id="9c92f-191">バッテリ制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="9c92f-191">Enable Battery limit</span></span>| <span data-ttu-id="9c92f-192">バッテリー制限機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-192">Allows you to manage Battery limit functionality.</span></span> <span data-ttu-id="9c92f-193">この設定を構成しない場合、バッテリ制限が有効になります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-193">If you do not configure this setting, Battery limit is enabled</span></span> |
| <span data-ttu-id="9c92f-194">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9c92f-194">Security</span></span>                           | <span data-ttu-id="9c92f-195">Surface UEFI セキュリティ ページ **を表示** します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-195">Displays the Surface UEFI **Security** page.</span></span> <span data-ttu-id="9c92f-196">この設定を構成しない場合は、[セキュリティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-196">If you do not configure this setting, the Security page is displayed.</span></span>                                                                                                                 |
| <span data-ttu-id="9c92f-197">デバイス</span><span class="sxs-lookup"><span data-stu-id="9c92f-197">Devices</span></span>                            | <span data-ttu-id="9c92f-198">[Surface UEFI デバイス] ページ **を表示** します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-198">Displays the Surface UEFI **Devices** page.</span></span> <span data-ttu-id="9c92f-199">この設定を構成しない場合は、[デバイス] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-199">If you do not configure this setting,  the Devices page is displayed.</span></span>                                                                                                                     |
| <span data-ttu-id="9c92f-200">Boot</span><span class="sxs-lookup"><span data-stu-id="9c92f-200">Boot</span></span>                               | <span data-ttu-id="9c92f-201">Surface UEFI ブート ページ **を表示** します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-201">Displays the Surface UEFI **Boot** page.</span></span> <span data-ttu-id="9c92f-202">この設定を構成しない場合は、ブート ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-202">If you do not configure this setting, the Boot page is displayed.</span></span>                                                                                                                                                            |
| <span data-ttu-id="9c92f-203">DateTime</span><span class="sxs-lookup"><span data-stu-id="9c92f-203">DateTime</span></span>                           | <span data-ttu-id="9c92f-204">Surface UEFI **の DateTime ページを表示** します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-204">Displays the Surface UEFI **DateTime** page.</span></span> <span data-ttu-id="9c92f-205">この設定を構成しない場合は、[DateTime] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-205">If you do not configure this setting, the DateTime page is displayed.</span></span>                                                                                                                |
| <span data-ttu-id="9c92f-206">EnableOSMigration</span><span class="sxs-lookup"><span data-stu-id="9c92f-206">EnableOSMigration</span></span>                          | <span data-ttu-id="9c92f-207">Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-207">Allows you to migrate Surface Hub 2 from Windows 10 Team to Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="9c92f-208">この設定を構成しない場合、Surface Hub 2 デバイスで実行できるのは Windows 10 Team OS のみです。</span><span class="sxs-lookup"><span data-stu-id="9c92f-208">If you do not configure this setting, Surface Hub 2 devices can only run Windows 10 Team OS.</span></span>   <span data-ttu-id="9c92f-209">注: Windows 10 Team と Windows 10 Pro/Enterprise の間のデュアル ブートは、Surface Hub 2 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-209">Note: Dual booting between Windows 10 Team and Windows 10 Pro/Enterprise  is not available on Surface Hub 2.</span></span>                                                                                                           |


>[!NOTE]
><span data-ttu-id="9c92f-210">図 3 に示すように、SEMM 構成パッケージを\*\*\*\* 作成すると、[成功] ページに 2 文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-210">When you create a SEMM configuration package, two characters are shown on the **Successful** page, as shown in Figure 3.</span></span>

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*<span data-ttu-id="9c92f-212">図 3. </span><span class="sxs-lookup"><span data-stu-id="9c92f-212">Figure 3.</span></span> <span data-ttu-id="9c92f-213">[成功] ページでの証明書の拇印の最後の 2 文字の表示</span><span class="sxs-lookup"><span data-stu-id="9c92f-213">Display of the last two characters of the certificate thumbprint on the Successful page</span></span>*

<span data-ttu-id="9c92f-214">これらの文字は証明書の拇印の最後の 2 文字であり、書き込むか記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-214">These characters are the last two characters of the certificate thumbprint and should be written down or recorded.</span></span> <span data-ttu-id="9c92f-215">図 4 に示すように、文字は Surface デバイスの SEMM への登録を確認するために必要です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-215">The characters are required to confirm enrollment in SEMM on a Surface device, as shown in Figure 4.</span></span>

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*<span data-ttu-id="9c92f-217">図 4: </span><span class="sxs-lookup"><span data-stu-id="9c92f-217">Figure 4.</span></span> <span data-ttu-id="9c92f-218">SEMM 証明書の拇印を使用した SEMM での登録確認</span><span class="sxs-lookup"><span data-stu-id="9c92f-218">Enrollment confirmation in SEMM with the SEMM certificate thumbprint</span></span>*

>[!NOTE]
><span data-ttu-id="9c92f-219">証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開いて、いつでも拇印を読み取る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-219">Administrators with access to the certificate file (.pfx) can read the thumbprint at any time by opening the .pfx file in CertMgr.</span></span> <span data-ttu-id="9c92f-220">CertMgr で拇印を表示するには、次のプロセスに従います。</span><span class="sxs-lookup"><span data-stu-id="9c92f-220">To view the thumbprint with CertMgr, follow this process:</span></span>
>1. <span data-ttu-id="9c92f-221">.pfx ファイルを右クリックし、[開く] をクリック **します**。</span><span class="sxs-lookup"><span data-stu-id="9c92f-221">Right-click the .pfx file, and then click **Open**.</span></span>
>2. <span data-ttu-id="9c92f-222">ナビゲーション ウィンドウでフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-222">Expand the folder in the navigation pane.</span></span>
>3. <span data-ttu-id="9c92f-223">**[証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c92f-223">Click **Certificates**.</span></span>
>4. <span data-ttu-id="9c92f-224">メイン ウィンドウで証明書を右クリックし、[開く] をクリック **します**。</span><span class="sxs-lookup"><span data-stu-id="9c92f-224">Right-click your certificate in the main pane, and then click **Open**.</span></span>
>5. <span data-ttu-id="9c92f-225">[詳細] **タブをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-225">Click the **Details** tab.</span></span>
>6. <span data-ttu-id="9c92f-226">**[** 表示 **] ドロップダウン メニュー** で [すべて] または [プロパティ **のみ]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-226">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
>7. <span data-ttu-id="9c92f-227">フィールド **Thumbprint を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9c92f-227">Select the field **Thumbprint**.</span></span>

<span data-ttu-id="9c92f-228">SEMM に Surface デバイスを登録したり、構成パッケージから UEFI 構成を適用したりするには、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-228">To enroll a Surface device in SEMM or to apply the UEFI configuration from a configuration package, all you need to do is run the .msi file with administrative privileges on the intended Surface device.</span></span> <span data-ttu-id="9c92f-229">アプリケーション展開または Microsoft [Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) や Microsoft Deployment Toolkit などのオペレーティング システム展開テクノロジ [を使用できます](https://technet.microsoft.com/windows/dn475741)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-229">You can use application deployment or operating system deployment technologies such as [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) or the [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741).</span></span> <span data-ttu-id="9c92f-230">SEMM にデバイスを登録する場合は、デバイスへの登録を確認するために物理的に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-230">When you enroll a device in SEMM you must be physically present to confirm the enrollment on the device.</span></span> <span data-ttu-id="9c92f-231">SEMM に既に登録されているデバイスに構成を適用する場合、ユーザーの操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-231">User interaction is not required when you apply a configuration to devices that are already enrolled in SEMM.</span></span>

<span data-ttu-id="9c92f-232">SEMM で Surface デバイスを登録する方法、または SEMM で Surface UEFI 構成を適用する方法の詳しいチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)を使用して Surface デバイスを登録および構成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c92f-232">For a step-by-step walkthrough of how to enroll a Surface device in SEMM or apply a Surface UEFI configuration with SEMM, see [Enroll and configure Surface devices with SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).</span></span>

### <span data-ttu-id="9c92f-233">パッケージをリセットする</span><span class="sxs-lookup"><span data-stu-id="9c92f-233">Reset package</span></span>

<span data-ttu-id="9c92f-234">Surface UEFI リセット パッケージは、SEMM から Surface デバイスを登録解除するために、1 つのタスクのみを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-234">A Surface UEFI reset package is used to perform only one task — to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="9c92f-235">リセット パッケージには、デバイスのファームウェアから SEMM 証明書を削除し、UEFI 設定を出荷時の既定値にリセットする署名済み手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c92f-235">The reset package contains signed instructions to remove the SEMM certificate from the device’s firmware and to reset UEFI settings to factory default.</span></span> <span data-ttu-id="9c92f-236">Surface UEFI 構成パッケージと同様に、リセット パッケージは、Surface デバイスでプロビジョニングされたのと同じ SEMM 証明書で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-236">Like a Surface UEFI configuration package, a reset package must be signed with the same SEMM certificate that is provisioned on the Surface device.</span></span> <span data-ttu-id="9c92f-237">SEMM リセット パッケージを作成する場合は、リセットする Surface デバイスのシリアル番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-237">When you create a SEMM reset package, you are required to supply the serial number of the Surface device you intend to reset.</span></span> <span data-ttu-id="9c92f-238">SEMM リセット パッケージはユニバーサルではなく、1 つのデバイスに固有です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-238">SEMM reset packages are not universal and are specific to one device.</span></span>

### <span data-ttu-id="9c92f-239">回復要求</span><span class="sxs-lookup"><span data-stu-id="9c92f-239">Recovery request</span></span>

<span data-ttu-id="9c92f-240">シナリオによっては、Surface UEFI リセット パッケージを使えない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-240">In some scenarios, it may be impossible to use a Surface UEFI reset package.</span></span> <span data-ttu-id="9c92f-241">(たとえば、Surface デバイスで Windows が使用できなくなる場合など)。これらのシナリオでは、回復要求操作を使用して、Surface UEFI\*\*\*\* の [エンタープライズ管理] ページ (図 5 を参照) を介して SEMM から Surface デバイスを登録解除できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-241">(For example, if Windows becomes unusable on the Surface device.) In these scenarios you can unenroll the Surface device from SEMM through the **Enterprise Management** page of Surface UEFI (shown in Figure 5) with a Recovery Request operation.</span></span>

![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*<span data-ttu-id="9c92f-243">図 5: </span><span class="sxs-lookup"><span data-stu-id="9c92f-243">Figure 5.</span></span> <span data-ttu-id="9c92f-244">[エンタープライズ管理] ページで SEMM 回復要求を開始する</span><span class="sxs-lookup"><span data-stu-id="9c92f-244">Initiate a SEMM recovery request on the Enterprise Management page</span></span>*

<span data-ttu-id="9c92f-245">[エンタープライズ管理] ページの\*\*\*\* プロセスを使用して Surface デバイスで SEMM をリセットすると、リセット要求が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-245">When you use the process on the **Enterprise Management** page to reset SEMM on a Surface device, you are provided with a Reset Request.</span></span> <span data-ttu-id="9c92f-246">このリセット要求は、ファイルとして USB ドライブに保存したり、テキストとしてコピーしたり、モバイル デバイスで QR コードとして読み取って、簡単にメールやメッセージを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-246">This Reset Request can be saved as a file to a USB drive, copied as text, or read as a QR Code with a mobile device to be easily emailed or messaged.</span></span> <span data-ttu-id="9c92f-247">Microsoft Surface UEFI コンフィエーターのリセット要求オプションを使用して、リセット要求ファイルを読み込むか、要求のリセット テキストまたは QR コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-247">Use the Microsoft Surface UEFI Configurator Reset Request option to load a Reset Request file or enter the Reset Request text or QR Code.</span></span> <span data-ttu-id="9c92f-248">Microsoft Surface UEFI Configurator は、Surface デバイスで入力できる検証コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-248">Microsoft Surface UEFI Configurator will generate a verification code that can be entered on the Surface device.</span></span> <span data-ttu-id="9c92f-249">Surface デバイスでコードを入力して **[Restart]** をクリックすると、デバイスは SEMM から登録解除されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-249">If you enter the code on the Surface device and click **Restart**, the device will be unenrolled from SEMM.</span></span> 

>[!NOTE]
><span data-ttu-id="9c92f-250">リセット要求は、作成後 2 時間で期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-250">A Reset Request expires two hours after it is created.</span></span>

<span data-ttu-id="9c92f-251">SEMM から Surface デバイスを登録解除する方法の詳しいチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)から Surface デバイスを登録解除する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c92f-251">For a step-by-step walkthrough of how to unenroll Surface devices from SEMM, see [Unenroll Surface devices from SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).</span></span>

## <span data-ttu-id="9c92f-252">Surface Enterprise 管理モードの証明書の要件</span><span class="sxs-lookup"><span data-stu-id="9c92f-252">Surface Enterprise Management Mode certificate requirements</span></span>
<span data-ttu-id="9c92f-253">SEMM を Microsoft Surface UEFI コンフィグレータと一緒に使用するには、UEFI 設定を適用する前に、構成ファイルの署名を検証する証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-253">Using SEMM with Microsoft Surface UEFI Configurator requires a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="9c92f-254">この証明書を使用すると、デバイスを SEMM に登録した後で、UEFI の設定を変更するために、承認された証明書で作成されたパッケージのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-254">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span>

>[!NOTE]
><span data-ttu-id="9c92f-255">SEMM 証明書は、登録済み Surface デバイスで SEMM または Surface UEFI の設定に対する変更を実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-255">The SEMM certificate is required to perform any modification to SEMM or Surface UEFI settings on enrolled Surface devices.</span></span> <span data-ttu-id="9c92f-256">SEMM 証明書が破損または失われた場合、SEMM を削除またはリセットすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-256">If the SEMM certificate is corrupted or lost, SEMM cannot be removed or reset.</span></span> <span data-ttu-id="9c92f-257">バックアップと復元に適したソリューションを使用して、SEMM 証明書を適切に管理します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-257">Manage your SEMM certificate accordingly with an appropriate solution for backup and recovery.</span></span>

<span data-ttu-id="9c92f-258">Microsoft Surface UEFI Configurator ツールで作成されたパッケージは、証明書で署名されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-258">Packages created with the Microsoft Surface UEFI Configurator tool are signed with a certificate.</span></span> <span data-ttu-id="9c92f-259">この証明書を使用すると、デバイスを SEMM に登録した後で、UEFI の設定を変更するために、承認された証明書で作成されたパッケージのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-259">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify the settings of UEFI.</span></span> 
### <span data-ttu-id="9c92f-260">推奨される証明書の設定</span><span class="sxs-lookup"><span data-stu-id="9c92f-260">Recommended certificate settings</span></span>
<span data-ttu-id="9c92f-261">SEMM 証明書には次の設定が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-261">The following settings are recommended for the SEMM certificate:</span></span>

* <span data-ttu-id="9c92f-262">**キー アルゴリズム** – RSA</span><span class="sxs-lookup"><span data-stu-id="9c92f-262">**Key Algorithm** – RSA</span></span> 
* <span data-ttu-id="9c92f-263">**キーの長** さ - 2048</span><span class="sxs-lookup"><span data-stu-id="9c92f-263">**Key Length** – 2048</span></span>
* <span data-ttu-id="9c92f-264">**ハッシュ アルゴリズム** – SHA-256</span><span class="sxs-lookup"><span data-stu-id="9c92f-264">**Hash Algorithm** – SHA-256</span></span>
* <span data-ttu-id="9c92f-265">**種類** – SSL サーバー認証</span><span class="sxs-lookup"><span data-stu-id="9c92f-265">**Type** – SSL Server Authentication</span></span>
* <span data-ttu-id="9c92f-266">**キー使用法** – デジタル署名、キー暗号化</span><span class="sxs-lookup"><span data-stu-id="9c92f-266">**Key Usage** – Digital signature, Key Encipherment</span></span>
* <span data-ttu-id="9c92f-267">**プロバイダー** – Microsoft Enhanced RSA and AES Cryptographic Provider</span><span class="sxs-lookup"><span data-stu-id="9c92f-267">**Provider** – Microsoft Enhanced RSA and AES Cryptographic Provider</span></span>
* <span data-ttu-id="9c92f-268">**有効期限 –** 証明書の作成から 15 か月</span><span class="sxs-lookup"><span data-stu-id="9c92f-268">**Expiration Date** – 15 Months from certificate creation</span></span>
* <span data-ttu-id="9c92f-269">**キーのエクスポート ポリシー** - エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="9c92f-269">**Key Export Policy** – Exportable</span></span>

<span data-ttu-id="9c92f-270">また、中間証明機関 (CA) が SEMM 専用である 2 層公開キー基盤 (PKI) アーキテクチャで SEMM 証明書を認証し、証明書の失効を可能にしてください。</span><span class="sxs-lookup"><span data-stu-id="9c92f-270">It is also recommended that the SEMM certificate be authenticated in a two-tier public key infrastructure (PKI) architecture where the intermediate certification authority (CA) is dedicated to SEMM, enabling certificate revocation.</span></span> <span data-ttu-id="9c92f-271">2 層 PKI 構成の詳細については、「テスト ラボ ガイド: AD CS および PKI 階層Two-Tier [参照してください](https://technet.microsoft.com/library/hh831348)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-271">For more information about a two-tier PKI configuration, see [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://technet.microsoft.com/library/hh831348).</span></span>

### <span data-ttu-id="9c92f-272">自己署名証明書</span><span class="sxs-lookup"><span data-stu-id="9c92f-272">Self-signed certificate</span></span> 
<span data-ttu-id="9c92f-273">次の PowerShell スクリプトの例を使用して、概念実証シナリオで使用する自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-273">You can use the following example PowerShell script to create a self-signed certificate for use in proof-of-concept scenarios.</span></span>
<span data-ttu-id="9c92f-274">このスクリプトを使用するには、次のテキストをメモ帳にコピーし、PowerShell スクリプト (.ps1) としてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-274">To use this script, copy the following text into Notepad and save the file as a PowerShell script (.ps1).</span></span> 

> [!NOTE]
> <span data-ttu-id="9c92f-275">このスクリプトは、次のパスワードを持つ証明書を作成します `12345678` 。このスクリプトによって生成される証明書は、実稼働環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-275">This script creates a certificate with a password of `12345678`.The certificate generated by this script is not recommended for production environments.</span></span>
  
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
><span data-ttu-id="9c92f-276">SEMM および Microsoft Surface UEFI コンフィエーターで使用するには、証明書をプライベート キーとパスワード保護を使用してエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-276">For use with SEMM and Microsoft Surface UEFI Configurator, the certificate must be exported with the private key and with password protection.</span></span> <span data-ttu-id="9c92f-277">必要に応じて、SemM 証明書ファイル (.pfx) と証明書パスワードを選択するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-277">Microsoft Surface UEFI Configurator will prompt you to select the SEMM certificate file (.pfx) and certificate password when it is required.</span></span>

1.  <span data-ttu-id="9c92f-278">スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM などです。</span><span class="sxs-lookup"><span data-stu-id="9c92f-278">Create a folder on your C: drive where you will save the script; for example, C:\SEMM.</span></span>
2.  <span data-ttu-id="9c92f-279">サンプル スクリプトをメモ帳または同等のテキスト エディターにコピーし、PowerShell スクリプト (.ps1) としてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-279">Copy the example script into Notepad or equivalent text editor and save the file as a PowerShell script (.ps1).</span></span>
3.  <span data-ttu-id="9c92f-280">管理者の資格情報で PC にサインインし、管理者特権の PowerShell セッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-280">Sign into your PC with administrator credentials and open an elevated PowerShell session.</span></span>
4.  <span data-ttu-id="9c92f-281">スクリプトの実行を許可するアクセス許可が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-281">Ensure your permissions are set to allow scripts to run.</span></span> <span data-ttu-id="9c92f-282">既定では、実行ポリシーを変更しない限り、スクリプトの実行はブロックされます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-282">By default, scripts are blocked from running unless you modify the execution policy.</span></span> <span data-ttu-id="9c92f-283">詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-283">To learn more, see [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>
5.  <span data-ttu-id="9c92f-284">コマンド プロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-284">At the command prompt, enter the full path of the script and then press Enter.</span></span> <span data-ttu-id="9c92f-285">このスクリプトは、TempOwner.pfx という名前のデモ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c92f-285">The script creates a Demo Certificate named TempOwner.pfx.</span></span>

<span data-ttu-id="9c92f-286">または、PowerShell を使用して独自の自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-286">Alternatively, you can create your own self-signed certificate using PowerShell.</span></span> <span data-ttu-id="9c92f-287">詳細については、PowerShell のドキュメント [New-SelfSignedCertificate を参照してください](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。</span><span class="sxs-lookup"><span data-stu-id="9c92f-287">For more information, see the following PowerShell documentation: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).</span></span>




>[!NOTE]
><span data-ttu-id="9c92f-288">PKI インフラストラクチャでオフライン ルートを使用する組織の場合、SEMM 証明書を認証するには、ルート CA に接続された環境で Microsoft Surface UEFI コンフィフィケーターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-288">For organizations that use an offline root in their PKI infrastructure, Microsoft Surface UEFI Configurator must be run in an environment connected to the root CA to authenticate the SEMM certificate.</span></span> <span data-ttu-id="9c92f-289">Microsoft Surface UEFI Configurator によって生成されたパッケージはファイルとして転送されるため、USB スティックなどのリムーバブル記憶域を使用してオフライン ネットワーク環境の外部に転送できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-289">The packages generated by Microsoft Surface UEFI Configurator can be transferred as files and therefore can be transferred outside the offline network environment with removable storage, such as a USB stick.</span></span>

### <span data-ttu-id="9c92f-290">証明書の管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="9c92f-290">Managing certificates FAQ</span></span>

<span data-ttu-id="9c92f-291">推奨される *最小の* 長さは 15 か月です。</span><span class="sxs-lookup"><span data-stu-id="9c92f-291">The recommended *minimum* length is 15 months.</span></span> <span data-ttu-id="9c92f-292">有効期限が 15 か月未満の証明書を使用するか、15 か月より長く有効期限が切れた証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-292">You can use a certificate that expires in less than 15 months or use a certificate that expires in longer than 15 months.</span></span>

>[!NOTE] 
><span data-ttu-id="9c92f-293">証明書の有効期限が切れると、証明書は自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-293">When a certificate expires, it does not automatically renew.</span></span> 


**<span data-ttu-id="9c92f-294">有効期限が切れた証明書は SEMM に登録されたデバイスの機能に影響しますか?</span><span class="sxs-lookup"><span data-stu-id="9c92f-294">Will an expired certificate affect the functionality of SEMM-enrolled devices?</span></span>**<br><br>
<span data-ttu-id="9c92f-295">いいえ。証明書は SEMM の IT 管理者管理タスクにのみ影響し、有効期限が切れるとデバイスの機能には影響しません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-295">No, a certificate only impacts IT admin management tasks in SEMM and has no effect on device functionality when it expires.</span></span>


**<span data-ttu-id="9c92f-296">SEMM パッケージと証明書があるすべてのコンピューターで SEMM パッケージと証明書を更新する必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="9c92f-296">Will the SEMM package and certificate need to be updated on all machines that have it?</span></span>**

<span data-ttu-id="9c92f-297">SEMM のリセットまたは回復を機能するには、証明書が有効であり、有効期限が切れていない必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c92f-297">If you want SEMM reset or recovery to work, the certificate needs to be valid and not expired.</span></span> 

**<span data-ttu-id="9c92f-298">注文するサーフェスごとにパッケージを一括リセットできますか?</span><span class="sxs-lookup"><span data-stu-id="9c92f-298">Can bulk reset packages be created for each surface that we order?</span></span> <span data-ttu-id="9c92f-299">環境内のすべてのコンピューターをリセットするビルドは可能ですか?</span><span class="sxs-lookup"><span data-stu-id="9c92f-299">Can one be built that resets all machines in our environment?</span></span>**

<span data-ttu-id="9c92f-300">特定のデバイスの種類の構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセット パッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-300">The PowerShell samples that create a config package for a specific device type can also be used to create a reset package that is serial-number independent.</span></span> <span data-ttu-id="9c92f-301">証明書がまだ有効な場合は、PowerShell を使用して SEMM をリセットするリセット パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-301">If the certificate is still valid, you can create a reset package using PowerShell to reset SEMM.</span></span>

## <span data-ttu-id="9c92f-302">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="9c92f-302">Version History</span></span>

### <span data-ttu-id="9c92f-303">バージョン 2.79.139.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-303">Version 2.79.139.0</span></span>

<span data-ttu-id="9c92f-304">このバージョンの SEMM には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-304">This version of SEMM includes:</span></span>
- <span data-ttu-id="9c92f-305">Surface Pro 7+ のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-305">Support for Surface Pro 7+</span></span>
- <span data-ttu-id="9c92f-306">ユーザー エクスペリエンスの向上</span><span class="sxs-lookup"><span data-stu-id="9c92f-306">User experience improvements</span></span>


### <span data-ttu-id="9c92f-307">バージョン 2.78.139.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-307">Version 2.78.139.0</span></span>

<span data-ttu-id="9c92f-308">このバージョンの SEMM には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-308">This version of SEMM includes:</span></span>

- <span data-ttu-id="9c92f-309">Surface Laptop Go と Surface Pro X のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-309">Support for Surface Laptop Go and Surface Pro X</span></span>
- <span data-ttu-id="9c92f-310">新しいバージョン リリースの通知</span><span class="sxs-lookup"><span data-stu-id="9c92f-310">Notifications for new version release</span></span>
- <span data-ttu-id="9c92f-311">所有権を変更するカスタム パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="9c92f-311">Ability to create custom packages to change ownership</span></span>
- <span data-ttu-id="9c92f-312">バグ修正</span><span class="sxs-lookup"><span data-stu-id="9c92f-312">Bug fixes</span></span>

### <span data-ttu-id="9c92f-313">バージョン 2.73.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-313">Version 2.73.136.0</span></span>

<span data-ttu-id="9c92f-314">このバージョンの SEMM には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-314">This version of SEMM includes:</span></span>

- <span data-ttu-id="9c92f-315">SEMM を使用して Surface Hub2S でオーディオを無効にできる</span><span class="sxs-lookup"><span data-stu-id="9c92f-315">Audio can now be disabled on Surface Hub2S using SEMM</span></span>
- <span data-ttu-id="9c92f-316">Surface Pro X for Dock 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-316">Support to Surface Pro X for Dock 2</span></span>
- <span data-ttu-id="9c92f-317">ドック 2 関連操作の UEFI マネージャーのサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-317">Support to UEFI Manager for Dock 2 related operations</span></span>
- <span data-ttu-id="9c92f-318">Surface Go リセット パッケージのバグ修正</span><span class="sxs-lookup"><span data-stu-id="9c92f-318">Surface Go reset package bug fix</span></span>
- <span data-ttu-id="9c92f-319">Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行のサポート。</span><span class="sxs-lookup"><span data-stu-id="9c92f-319">Support for migrating Surface Hub 2 devices from Windows 10 Team OS to Windows 10 Pro or Enterprise.</span></span>

### <span data-ttu-id="9c92f-320">バージョン 2.71.139.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-320">Version 2.71.139.0</span></span>

<span data-ttu-id="9c92f-321">このバージョンの SEMM では、Surface Book 3、Surface Laptop 3、Surface Pro 7 の Surface ドック 2 管理機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9c92f-321">This version of SEMM adds support for Surface Dock 2 management features  for Surface Book 3, Surface Laptop 3, and Surface Pro 7 including:</span></span>

- <span data-ttu-id="9c92f-322">オーディオの有効化 (ロック/ロック解除)、イーサネット ポートと USB ポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-322">Enabling audio (locking/unlocking), Ethernet and USB ports</span></span>
- <span data-ttu-id="9c92f-323">認証されたホストと認証されていないホストの両方のドック パッケージを作成する機能</span><span class="sxs-lookup"><span data-stu-id="9c92f-323">Ability to create dock packages for both authenticated and unauthenticated hosts</span></span>

### <span data-ttu-id="9c92f-324">バージョン 2.70.130.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-324">Version 2.70.130.0</span></span>

<span data-ttu-id="9c92f-325">このバージョンの SEMM には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-325">This version of SEMM includes:</span></span>

- <span data-ttu-id="9c92f-326">Surface Go 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-326">Support for Surface Go 2</span></span>
- <span data-ttu-id="9c92f-327">Surface Book 3 のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-327">Support for Surface Book 3</span></span>
- <span data-ttu-id="9c92f-328">バグ修正</span><span class="sxs-lookup"><span data-stu-id="9c92f-328">Bug fixes</span></span>


### <span data-ttu-id="9c92f-329">バージョン 2.59.139.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-329">Version 2.59.139.0</span></span>

* <span data-ttu-id="9c92f-330">Intel プロセッサを搭載した Surface Pro 7、Surface Pro X、Surface Laptop 3 13.5" および 15" モデルのサポート。</span><span class="sxs-lookup"><span data-stu-id="9c92f-330">Support for Surface Pro 7, Surface Pro X,  and Surface Laptop 3 13.5" and 15" models with Intel processor.</span></span> <span data-ttu-id="9c92f-331">注: Surface Laptop 3 15" AMD プロセッサはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9c92f-331">Note:  Surface Laptop 3 15" AMD processor is not supported.</span></span>

- <span data-ttu-id="9c92f-332">電源でのスリープ解除機能のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-332">Support for Wake on Power feature</span></span>

### <span data-ttu-id="9c92f-333">バージョン 2.54.139.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-333">Version 2.54.139.0</span></span>
* <span data-ttu-id="9c92f-334">Surface Hub 2S のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-334">Support to Surface Hub 2S</span></span>
* <span data-ttu-id="9c92f-335">バグ修正</span><span class="sxs-lookup"><span data-stu-id="9c92f-335">Bug fixes</span></span>

### <span data-ttu-id="9c92f-336">バージョン 2.43.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-336">Version 2.43.136.0</span></span>
* <span data-ttu-id="9c92f-337">マルチマルチサーティングの有効化/無効化のサポート</span><span class="sxs-lookup"><span data-stu-id="9c92f-337">Support to enable/disable simulatenous multithreating</span></span> 
* <span data-ttu-id="9c92f-338">一部のデバイスでは、WiFi とBluetoothオプションを個別に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c92f-338">Separate options for WiFi and Bluetooth for some devices</span></span> 
* <span data-ttu-id="9c92f-339">Surface Studio のバッテリー制限の削除</span><span class="sxs-lookup"><span data-stu-id="9c92f-339">Battery Limit removed for Surface Studio</span></span> 

### <span data-ttu-id="9c92f-340">バージョン 2.26.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-340">Version 2.26.136.0</span></span>
* <span data-ttu-id="9c92f-341">Surface Studio 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-341">Add support to Surface Studio 2</span></span>
* <span data-ttu-id="9c92f-342">バッテリー制限機能</span><span class="sxs-lookup"><span data-stu-id="9c92f-342">Battery Limit feature</span></span>

### <span data-ttu-id="9c92f-343">バージョン 2.21.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-343">Version 2.21.136.0</span></span>
* <span data-ttu-id="9c92f-344">Surface Pro 6 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-344">Add support to Surface Pro 6</span></span>
* <span data-ttu-id="9c92f-345">Surface Laptop 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-345">Add support to Surface Laptop 2</span></span>

### <span data-ttu-id="9c92f-346">バージョン 2.14.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-346">Version 2.14.136.0</span></span>
* <span data-ttu-id="9c92f-347">Surface Go へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-347">Add support to Surface Go</span></span>

### <span data-ttu-id="9c92f-348">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-348">Version 2.9.136.0</span></span>
* <span data-ttu-id="9c92f-349">Surface Book 2 へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-349">Add support to Surface Book 2</span></span>
* <span data-ttu-id="9c92f-350">Surface Pro LTE へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-350">Add support to Surface Pro LTE</span></span>
* <span data-ttu-id="9c92f-351">アクセシビリティの強化</span><span class="sxs-lookup"><span data-stu-id="9c92f-351">Accessibility improvements</span></span>

### <span data-ttu-id="9c92f-352">バージョン 1.0.74.0</span><span class="sxs-lookup"><span data-stu-id="9c92f-352">Version 1.0.74.0</span></span>
* <span data-ttu-id="9c92f-353">Surface Laptop へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-353">Add support to Surface Laptop</span></span>
* <span data-ttu-id="9c92f-354">Surface Pro へのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="9c92f-354">Add support to Surface Pro</span></span>
* <span data-ttu-id="9c92f-355">バグ修正と一般的な改善</span><span class="sxs-lookup"><span data-stu-id="9c92f-355">Bug fixes and general improvement</span></span>

## <span data-ttu-id="9c92f-356">関連トピック</span><span class="sxs-lookup"><span data-stu-id="9c92f-356">Related topics</span></span>

- [<span data-ttu-id="9c92f-357">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="9c92f-357">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)
- [<span data-ttu-id="9c92f-358">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="9c92f-358">Unenroll Surface devices from SEMM</span></span>](unenroll-surface-devices-from-semm.md)
- [<span data-ttu-id="9c92f-359">SEMM を使用して Surface Dock 2 ポートを保護する</span><span class="sxs-lookup"><span data-stu-id="9c92f-359">Secure Surface Dock 2 ports with SEMM</span></span>](secure-surface-dock-ports-semm.md)
