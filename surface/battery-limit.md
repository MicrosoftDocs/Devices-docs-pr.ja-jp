---
title: バッテリー制限の設定 (等高線)
description: バッテリー制限は、Surface デバイスのバッテリの充電方法を変更する UEFI の設定であり、その寿命を延長する可能性があります。
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
ms.date: 5/06/2020
ms.openlocfilehash: 927f00681bd5756f380025adf00a08a34a3f411f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835989"
---
# <span data-ttu-id="1955c-103">バッテリーの制限の設定</span><span class="sxs-lookup"><span data-stu-id="1955c-103">Battery Limit setting</span></span>

<span data-ttu-id="1955c-104">[バッテリー制限] オプションは、Surface デバイスのバッテリの充電方法を変更する UEFI 設定で、その寿命を延長する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1955c-104">Battery Limit option is a UEFI setting that changes how the Surface device battery is charged and may prolong its longevity.</span></span> <span data-ttu-id="1955c-105">この設定は、デバイスがキオスクのソリューションに統合されている場合など、デバイスが継続的に電源に接続されている場合にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1955c-105">This setting is recommended in  cases  in which the device is continuously connected to power, for example when devices are integrated into kiosk solutions.</span></span>  

## <span data-ttu-id="1955c-106">バッテリの制限のしくみ</span><span class="sxs-lookup"><span data-stu-id="1955c-106">How Battery Limit works</span></span>

<span data-ttu-id="1955c-107">バッテリー制限でデバイスを設定すると、デバイスのバッテリーを充電するためのプロトコルが変更されます。</span><span class="sxs-lookup"><span data-stu-id="1955c-107">Setting the device on Battery Limit changes the protocol for charging the device battery.</span></span> <span data-ttu-id="1955c-108">バッテリの上限を有効にすると、バッテリの充電量が最大容量の50% に制限されます。</span><span class="sxs-lookup"><span data-stu-id="1955c-108">When Battery Limit is enabled, the battery charge will be limited to 50% of its maximum capacity.</span></span> <span data-ttu-id="1955c-109">Windows で報告される充電レベルは、この制限を反映します。</span><span class="sxs-lookup"><span data-stu-id="1955c-109">The charge level reported in Windows will reflect this limit.</span></span> <span data-ttu-id="1955c-110">そのため、バッテリーが50% まで充電され、この制限を超えて充電されないことが示されます。</span><span class="sxs-lookup"><span data-stu-id="1955c-110">Therefore, it will show that the battery is charged up to 50% and will not charge beyond  this limit.</span></span> <span data-ttu-id="1955c-111">デバイスの充電率が50% の場合にバッテリの制限を有効にすると、デバイスが接続されていることを示すバッテリアイコンが表示されますが、デバイスが最大充電容量の50% に到達するまで放電します。</span><span class="sxs-lookup"><span data-stu-id="1955c-111">If you enable Battery Limit while the device is above 50% charge, the Battery icon will show that the device is plugged in but discharging until the device reaches 50% of its maximum charge capacity.</span></span>  

## <span data-ttu-id="1955c-112">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="1955c-112">Supported devices</span></span>
<span data-ttu-id="1955c-113">バッテリー制限 UEFI 設定は、Surface Pro 7 と Surface ノート Pc 3 を含む最新の Surface デバイスに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1955c-113">The Battery Limit UEFI setting is built into the latest Surface devices including Surface Pro 7 and Surface Laptop 3.</span></span> <span data-ttu-id="1955c-114">以前のデバイスでは[SURFACE UEFI ファームウェアの更新](manage-surface-driver-and-firmware-updates.md)が必要です。 Windows update または[surface サポートサイト](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface)の MSI ドライバーとファームウェアパッケージを通じて入手できます。</span><span class="sxs-lookup"><span data-stu-id="1955c-114">Earlier devices require a [Surface UEFI firmware update](manage-surface-driver-and-firmware-updates.md), available through Windows Update or via the MSI driver and firmware packages on the [Surface Support site](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface).</span></span> <span data-ttu-id="1955c-115">サポートされている各デバイスに必要な特定の Surface UEFI バージョンのために[長時間接続する必要がある surface デバイスに対して、"バッテリー制限" を有効](https://support.microsoft.com/help/4464941)にすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1955c-115">Check [Enable "Battery Limit" for Surface devices that have to be plugged in for extended periods of time](https://support.microsoft.com/help/4464941) for the specific Surface UEFI version required for each supported device.</span></span> 

## <span data-ttu-id="1955c-116">Surface UEFI でのバッテリー制限の有効化 (Surface Pro 4 以降)</span><span class="sxs-lookup"><span data-stu-id="1955c-116">Enabling Battery Limit in Surface UEFI (Surface Pro 4 and later)</span></span>

<span data-ttu-id="1955c-117">Surface UEFI バッテリ制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。</span><span class="sxs-lookup"><span data-stu-id="1955c-117">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="1955c-118">[**ブート構成**] を選択し、[**詳細オプション**] で [**バッテリー制限モードを有効**にする] を **[オン**] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1955c-118">Choose **boot configuration**, and then, under **Advanced Options**, toggle **Enable Battery Limit Mode** to **On**.</span></span>  

![詳細オプションのスクリーンショット](images/enable-bl.png) 

## <span data-ttu-id="1955c-120">Surface の移動と Surface 移動でのバッテリ制限の有効化2</span><span class="sxs-lookup"><span data-stu-id="1955c-120">Enabling battery limit on Surface Go and Surface Go 2</span></span>
<span data-ttu-id="1955c-121">Surface バッテリー制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。</span><span class="sxs-lookup"><span data-stu-id="1955c-121">The Surface Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="1955c-122">[**ブート構成**] を選択し、[**キオスクモード**] の下にあるスライダーを右に動かして、[バッテリーの上限] を [**有効**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="1955c-122">Choose **boot configuration**, and then, under **Kiosk Mode**, move the slider to the right to set Battery Limit to **Enabled**.</span></span>  

![Surface Go のキオスクモードのバッテリー制限のスクリーンショット](images/go-batterylimit.png) 

## <span data-ttu-id="1955c-124">Surface UEFI でのバッテリー制限の有効化 (Surface Pro 3)</span><span class="sxs-lookup"><span data-stu-id="1955c-124">Enabling Battery Limit in Surface UEFI (Surface Pro 3)</span></span>

<span data-ttu-id="1955c-125">Surface UEFI バッテリ制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。</span><span class="sxs-lookup"><span data-stu-id="1955c-125">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="1955c-126">[**キオスクモード**] を選択し、[**バッテリーの上限**] を選択して、[**有効**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="1955c-126">Choose **Kiosk Mode**, select **Battery Limit**, and then choose **Enabled**.</span></span>

![詳細オプションのスクリーンショット](images/enable-bl-sp3.png) 

![詳細オプションのスクリーンショット](images/enable-bl-sp3-2.png) 

## <span data-ttu-id="1955c-129">Surface Enterprise Management Mode (SEMM) または Surface Pro 3 ファームウェア PowerShell スクリプトを使用してバッテリ制限を有効にする</span><span class="sxs-lookup"><span data-stu-id="1955c-129">Enabling Battery Limit using Surface Enterprise Management Mode (SEMM) or Surface Pro 3 firmware PowerShell scripts</span></span>

<span data-ttu-id="1955c-130">Surface UEFI バッテリ制限は、次の方法で構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1955c-130">The Surface UEFI battery limit is also available for configuration via the following methods:</span></span>

- <span data-ttu-id="1955c-131">Surface Pro 4 以降</span><span class="sxs-lookup"><span data-stu-id="1955c-131">Surface Pro 4 and later</span></span> 
    - [<span data-ttu-id="1955c-132">Microsoft Surface UEFI コンフィギュレーター</span><span class="sxs-lookup"><span data-stu-id="1955c-132">Microsoft Surface UEFI Configurator</span></span>](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - <span data-ttu-id="1955c-133">Surface [Tools FOR IT をダウンロードするため](https://www.microsoft.com/download/details.aspx?id=46703)の Surface UEFI Manager Powershell スクリプト (SEMM_Powershell.zip)</span><span class="sxs-lookup"><span data-stu-id="1955c-133">Surface UEFI Manager Powershell scripts (SEMM_Powershell.zip) in the [Surface Tools for IT downloads](https://www.microsoft.com/download/details.aspx?id=46703)</span></span>
- <span data-ttu-id="1955c-134">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="1955c-134">Surface Pro 3</span></span> 
    - [<span data-ttu-id="1955c-135">SP3_Firmware_Powershell_Scripts.zip</span><span class="sxs-lookup"><span data-stu-id="1955c-135">SP3_Firmware_Powershell_Scripts.zip</span></span>](https://www.microsoft.com/download/details.aspx?id=46703)

### <span data-ttu-id="1955c-136">Microsoft Surface UEFI コンフィギュレーターの使用</span><span class="sxs-lookup"><span data-stu-id="1955c-136">Using Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="1955c-137">バッテリー制限モードを構成するには、SEMM (Surface Pro 4 以降) の **[詳細設定**] 構成ページで [ **Kiosk Overrides** ] 設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="1955c-137">To configure Battery Limit mode, set the **Kiosk Overrides** setting on the **Advanced Settings** configuration page in SEMM (Surface Pro 4 and later).</span></span>

![詳細設定のスクリーンショット](images/semm-bl.png)

### <span data-ttu-id="1955c-139">Surface UEFI Manager PowerShell スクリプトを使用する</span><span class="sxs-lookup"><span data-stu-id="1955c-139">Using Surface UEFI Manager PowerShell scripts</span></span>

<span data-ttu-id="1955c-140">バッテリー制限機能は、次の設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1955c-140">The battery limit feature is controlled via the following setting:</span></span>  

`407 = Battery Profile`

<span data-ttu-id="1955c-141">**説明**: バッテリ使用パターンのアクティブな管理スキーム</span><span class="sxs-lookup"><span data-stu-id="1955c-141">**Description**:  Active management scheme for battery usage pattern</span></span>

<span data-ttu-id="1955c-142">**既定値**:</span><span class="sxs-lookup"><span data-stu-id="1955c-142">**Default**:</span></span>  `0` 

<span data-ttu-id="1955c-143">バッテリの上限を有効にするには、これを設定し `1` ます。</span><span class="sxs-lookup"><span data-stu-id="1955c-143">Set this to `1` to enable Battery Limit.</span></span>

### <span data-ttu-id="1955c-144">Surface Pro 3 のファームウェアツールの使用</span><span class="sxs-lookup"><span data-stu-id="1955c-144">Using Surface Pro 3 firmware tools</span></span>

<span data-ttu-id="1955c-145">バッテリー制限機能は、次の設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1955c-145">The battery limit feature is controlled via the following setting:</span></span>  

<span data-ttu-id="1955c-146">**名前**: BatteryLimitEnable</span><span class="sxs-lookup"><span data-stu-id="1955c-146">**Name**: BatteryLimitEnable</span></span>

<span data-ttu-id="1955c-147">**説明**: BatteryLimit</span><span class="sxs-lookup"><span data-stu-id="1955c-147">**Description**:  BatteryLimit</span></span>

<span data-ttu-id="1955c-148">**現在の値**:</span><span class="sxs-lookup"><span data-stu-id="1955c-148">**Current Value**:</span></span>  `0` 

<span data-ttu-id="1955c-149">**既定値**:</span><span class="sxs-lookup"><span data-stu-id="1955c-149">**Default Value**:</span></span> `0`

<span data-ttu-id="1955c-150">**提案**された値:</span><span class="sxs-lookup"><span data-stu-id="1955c-150">**Proposed Value**:</span></span> `0` 

<span data-ttu-id="1955c-151">バッテリの上限を有効にするには、これを設定し `1` ます。</span><span class="sxs-lookup"><span data-stu-id="1955c-151">Set this to `1` to enable Battery Limit.</span></span>

>[!NOTE]
><span data-ttu-id="1955c-152">この設定を構成するには、 [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1955c-152">To configure this setting, you must use [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> 

