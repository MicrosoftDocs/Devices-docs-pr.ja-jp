---
title: バッテリー制限の設定 (Surface)
description: バッテリー制限は、Surface デバイスのバッテリーの充電方法を変更し、その寿命を延ばす可能性がある UEFI 設定です。
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.reviewer: jesko
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
manager: laurawi
audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 8ce1dcfc621a547aca9ca1db322f3ed2ce082728
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271144"
---
# <span data-ttu-id="c56c8-103">バッテリーの制限の設定</span><span class="sxs-lookup"><span data-stu-id="c56c8-103">Battery Limit setting</span></span>

<span data-ttu-id="c56c8-104">バッテリー制限オプションは、Surface デバイスのバッテリーの充電方法を変更し、その寿命を延ばす可能性がある UEFI 設定です。</span><span class="sxs-lookup"><span data-stu-id="c56c8-104">Battery Limit option is a UEFI setting that changes how the Surface device battery is charged and may prolong its longevity.</span></span> <span data-ttu-id="c56c8-105">デバイスがキオスク ソリューションに統合されている場合など、デバイスが継続的に電源に接続されている場合は、この設定をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c56c8-105">This setting is recommended in  cases  in which the device is continuously connected to power, for example when devices are integrated into kiosk solutions.</span></span>  

## <span data-ttu-id="c56c8-106">バッテリー制限のしくみ</span><span class="sxs-lookup"><span data-stu-id="c56c8-106">How Battery Limit works</span></span>

<span data-ttu-id="c56c8-107">[バッテリー制限] でデバイスを設定すると、デバイスのバッテリーを充電するプロトコルが変更されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-107">Setting the device on Battery Limit changes the protocol for charging the device battery.</span></span> <span data-ttu-id="c56c8-108">バッテリー制限を有効にすると、バッテリ残量は最大容量の 50% に制限されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-108">When Battery Limit is enabled, the battery charge will be limited to 50% of its maximum capacity.</span></span> <span data-ttu-id="c56c8-109">Windows で報告される課金レベルには、この制限が反映されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-109">The charge level reported in Windows will reflect this limit.</span></span> <span data-ttu-id="c56c8-110">したがって、バッテリーは最大 50% 充電され、この制限を超えて充電されません。</span><span class="sxs-lookup"><span data-stu-id="c56c8-110">Therefore, it will show that the battery is charged up to 50% and will not charge beyond  this limit.</span></span> <span data-ttu-id="c56c8-111">デバイスの充電量が 50% を超えた状態でバッテリー制限を有効にした場合、バッテリー アイコンには、デバイスが接続されているが、デバイスが最大充電容量の 50% に達するまで充電中であることが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-111">If you enable Battery Limit while the device is above 50% charge, the Battery icon will show that the device is plugged in but discharging until the device reaches 50% of its maximum charge capacity.</span></span>  

## <span data-ttu-id="c56c8-112">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="c56c8-112">Supported devices</span></span>

<span data-ttu-id="c56c8-113">バッテリー制限 UEFI の設定は、Surface Pro 7+、Surface Pro 7、Surface Laptop 3 などの最新の Surface デバイスに組み込されています。</span><span class="sxs-lookup"><span data-stu-id="c56c8-113">The Battery Limit UEFI setting is built into the latest Surface devices including Surface Pro 7+, Surface Pro 7, and Surface Laptop 3.</span></span> <span data-ttu-id="c56c8-114">以前のデバイスでは [、Windows](manage-surface-driver-and-firmware-updates.md)Update または Surface サポート サイトの MSI ドライバーおよびファームウェア パッケージから利用できる Surface UEFI ファームウェア更新 [プログラムが必要です](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface)。</span><span class="sxs-lookup"><span data-stu-id="c56c8-114">Earlier devices require a [Surface UEFI firmware update](manage-surface-driver-and-firmware-updates.md), available through Windows Update or via the MSI driver and firmware packages on the [Surface Support site](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface).</span></span> <span data-ttu-id="c56c8-115">サポート [されている各デバイス](https://support.microsoft.com/help/4464941) に必要な特定の Surface UEFI バージョンについて、延長期間に接続する必要がある Surface デバイスに対して [バッテリー制限] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c56c8-115">Check [Enable "Battery Limit" for Surface devices that have to be plugged in for extended periods of time](https://support.microsoft.com/help/4464941) for the specific Surface UEFI version required for each supported device.</span></span> 

## <span data-ttu-id="c56c8-116">Surface UEFI でのバッテリー制限の有効化 (Surface Pro 4 以降)</span><span class="sxs-lookup"><span data-stu-id="c56c8-116">Enabling Battery Limit in Surface UEFI (Surface Pro 4 and later)</span></span>

<span data-ttu-id="c56c8-117">Surface UEFI のバッテリー制限の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。**</span><span class="sxs-lookup"><span data-stu-id="c56c8-117">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="c56c8-118">ブート**構成を選択し**、[詳細オプション\*\*\*\*] で [バッテリ制限モードを有効にする] を [オン]**に\*\*\*\*切り替えます**。</span><span class="sxs-lookup"><span data-stu-id="c56c8-118">Choose **boot configuration**, and then, under **Advanced Options**, toggle **Enable Battery Limit Mode** to **On**.</span></span>  

![バッテリー制限の詳細オプション](images/enable-bl.png) 

## <span data-ttu-id="c56c8-120">Surface Go と Surface Go 2 でバッテリー制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="c56c8-120">Enabling battery limit on Surface Go and Surface Go 2</span></span>
<span data-ttu-id="c56c8-121">Surface Battery Limit の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。**</span><span class="sxs-lookup"><span data-stu-id="c56c8-121">The Surface Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="c56c8-122">ブート**構成を選択**し、[キオスク\*\*\*\* モード] でスライダーを右に移動し、[バッテリー制限] を [有効] に設定**します**。</span><span class="sxs-lookup"><span data-stu-id="c56c8-122">Choose **boot configuration**, and then, under **Kiosk Mode**, move the slider to the right to set Battery Limit to **Enabled**.</span></span>  

![Surface Go でのキオスク モードのバッテリー制限](images/go-batterylimit.png) 

## <span data-ttu-id="c56c8-124">Surface UEFI でのバッテリー制限の有効化 (Surface Pro 3)</span><span class="sxs-lookup"><span data-stu-id="c56c8-124">Enabling Battery Limit in Surface UEFI (Surface Pro 3)</span></span>

<span data-ttu-id="c56c8-125">Surface UEFI のバッテリー制限の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。**</span><span class="sxs-lookup"><span data-stu-id="c56c8-125">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="c56c8-126">[ **キオスク モード] を選択**し、[バッテリー制限 **] を**選択して、[有効] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c56c8-126">Choose **Kiosk Mode**, select **Battery Limit**, and then choose **Enabled**.</span></span>

![詳細オプションのスクリーンショット](images/enable-bl-sp3.png) 

![詳細設定オプション](images/enable-bl-sp3-2.png) 

## <span data-ttu-id="c56c8-129">Surface Enterprise 管理モード (SEMM) または Surface Pro 3 ファームウェア PowerShell スクリプトを使用したバッテリ制限の有効化</span><span class="sxs-lookup"><span data-stu-id="c56c8-129">Enabling Battery Limit using Surface Enterprise Management Mode (SEMM) or Surface Pro 3 firmware PowerShell scripts</span></span>

<span data-ttu-id="c56c8-130">Surface UEFI バッテリーの制限は、次の方法で構成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-130">The Surface UEFI battery limit is also available for configuration via the following methods:</span></span>

- <span data-ttu-id="c56c8-131">Surface Pro 4 以降</span><span class="sxs-lookup"><span data-stu-id="c56c8-131">Surface Pro 4 and later</span></span> 
    - [<span data-ttu-id="c56c8-132">Microsoft Surface UEFI コンフィエーター</span><span class="sxs-lookup"><span data-stu-id="c56c8-132">Microsoft Surface UEFI Configurator</span></span>](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - <span data-ttu-id="c56c8-133">Surface Tools [for IT](https://www.microsoft.com/download/details.aspx?id=46703)ダウンロードの Surface UEFI マネージャー Powershell スクリプト (SEMM_Powershell.zip)</span><span class="sxs-lookup"><span data-stu-id="c56c8-133">Surface UEFI Manager Powershell scripts (SEMM_Powershell.zip) in the [Surface Tools for IT downloads](https://www.microsoft.com/download/details.aspx?id=46703)</span></span>
- <span data-ttu-id="c56c8-134">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="c56c8-134">Surface Pro 3</span></span> 
    - [<span data-ttu-id="c56c8-135">SP3_Firmware_Powershell_Scripts.zip</span><span class="sxs-lookup"><span data-stu-id="c56c8-135">SP3_Firmware_Powershell_Scripts.zip</span></span>](https://www.microsoft.com/download/details.aspx?id=46703)

### <span data-ttu-id="c56c8-136">Microsoft Surface UEFI コンフィエーターの使用</span><span class="sxs-lookup"><span data-stu-id="c56c8-136">Using Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="c56c8-137">バッテリー制限モードを構成するには、SEMM (Surface Pro \*\*\*\* 4 以降) の [詳細設定] 構成ページで [キオスクの上書き] 設定を設定します。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c56c8-137">To configure Battery Limit mode, set the **Kiosk Overrides** setting on the **Advanced Settings** configuration page in SEMM (Surface Pro 4 and later).</span></span>

![詳細設定のスクリーンショット](images/semm-bl.png)

### <span data-ttu-id="c56c8-139">Surface UEFI マネージャー PowerShell スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="c56c8-139">Using Surface UEFI Manager PowerShell scripts</span></span>

<span data-ttu-id="c56c8-140">バッテリ制限機能は、次の設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-140">The battery limit feature is controlled via the following setting:</span></span>  

`407 = Battery Profile`

<span data-ttu-id="c56c8-141">**説明**: バッテリ使用パターンのアクティブな管理スキーム</span><span class="sxs-lookup"><span data-stu-id="c56c8-141">**Description**:  Active management scheme for battery usage pattern</span></span>

<span data-ttu-id="c56c8-142">**既定値は次の値です**。</span><span class="sxs-lookup"><span data-stu-id="c56c8-142">**Default**:</span></span>  `0` 

<span data-ttu-id="c56c8-143">バッテリ制限を `1` 有効にするには、これを設定します。</span><span class="sxs-lookup"><span data-stu-id="c56c8-143">Set this to `1` to enable Battery Limit.</span></span>

### <span data-ttu-id="c56c8-144">Surface Pro 3 ファームウェア ツールの使用</span><span class="sxs-lookup"><span data-stu-id="c56c8-144">Using Surface Pro 3 firmware tools</span></span>

<span data-ttu-id="c56c8-145">バッテリ制限機能は、次の設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="c56c8-145">The battery limit feature is controlled via the following setting:</span></span>  

<span data-ttu-id="c56c8-146">**Name**: BatteryLimitEnable</span><span class="sxs-lookup"><span data-stu-id="c56c8-146">**Name**: BatteryLimitEnable</span></span>

<span data-ttu-id="c56c8-147">**説明**: BatteryLimit</span><span class="sxs-lookup"><span data-stu-id="c56c8-147">**Description**:  BatteryLimit</span></span>

<span data-ttu-id="c56c8-148">**現在の値**:</span><span class="sxs-lookup"><span data-stu-id="c56c8-148">**Current Value**:</span></span>  `0` 

<span data-ttu-id="c56c8-149">**既定値**:</span><span class="sxs-lookup"><span data-stu-id="c56c8-149">**Default Value**:</span></span> `0`

<span data-ttu-id="c56c8-150">**提案された値**:</span><span class="sxs-lookup"><span data-stu-id="c56c8-150">**Proposed Value**:</span></span> `0` 

<span data-ttu-id="c56c8-151">バッテリ制限を `1` 有効にするには、これを設定します。</span><span class="sxs-lookup"><span data-stu-id="c56c8-151">Set this to `1` to enable Battery Limit.</span></span>

>[!NOTE]
><span data-ttu-id="c56c8-152">この設定を構成するには、次のコマンドを使用[SP3_Firmware_Powershell_Scripts.zip。 ](https://www.microsoft.com/download/details.aspx?id=46703)</span><span class="sxs-lookup"><span data-stu-id="c56c8-152">To configure this setting, you must use [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> 

