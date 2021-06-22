---
title: Surface デバイス での Wake On LAN の使用
description: Wake On LAN を使用してデバイスをリモートで起動して管理タスクを自動的に実行する方法について説明します。
keywords: 更新、展開、ドライバー、wol、wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.date: 6/04/2021
ms.openlocfilehash: 83989461ca557d27740252149418056688774d3f
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613803"
---
# <a name="wake-on-lan-for-surface-devices"></a><span data-ttu-id="cb912-104">Surface デバイス での Wake On LAN の使用</span><span class="sxs-lookup"><span data-stu-id="cb912-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="cb912-105">デバイスを完全に最新の状態に保つために、IT 管理者は、通常は夜間のメンテナンス期間中に、使用していないデバイスを管理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb912-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="cb912-106">Wake on LAN (WOL) を使用すると、管理者はデバイスをリモートで起動し、Microsoft エンドポイント マネージャーまたはサード パーティ製のソリューションを使用して管理タスクを自動的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb912-106">Wake on LAN (WOL) enables admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or third-party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb912-107">要件</span><span class="sxs-lookup"><span data-stu-id="cb912-107">Requirements</span></span>

<span data-ttu-id="cb912-108">デバイスは AC 電源に接続され、次のいずれかの互換性のあるイーサネット アダプターとの有線接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb912-108">Devices must be connected to AC power and have a wired connection with one of the following compatible Ethernet adapters:</span></span>

- <span data-ttu-id="cb912-109">Surface USB 3.0 ギガビット イーサネット アダプター</span><span class="sxs-lookup"><span data-stu-id="cb912-109">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>
- <span data-ttu-id="cb912-110">Surface Ethernet Adapter</span><span class="sxs-lookup"><span data-stu-id="cb912-110">Surface Ethernet Adapter</span></span>
- <span data-ttu-id="cb912-111">Surface USB-C からイーサネットおよび USB アダプター</span><span class="sxs-lookup"><span data-stu-id="cb912-111">Surface USB-C to Ethernet and USB Adapter</span></span>
- <span data-ttu-id="cb912-112">Microsoft USB-C トラベル アダプター ハブ</span><span class="sxs-lookup"><span data-stu-id="cb912-112">Microsoft USB-C Travel Adapter Hub</span></span>
- <span data-ttu-id="cb912-113">Surface ドック</span><span class="sxs-lookup"><span data-stu-id="cb912-113">Surface Dock</span></span>
- <span data-ttu-id="cb912-114">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="cb912-114">Surface Dock 2</span></span>

> [!NOTE]
> <span data-ttu-id="cb912-115">Surface Dock 2 は、追加の IT 構成を必要とせずに Wake on LAN を最高のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb912-115">Surface Dock 2 provides the best support for Wake on LAN without the need for any additional IT configuration.</span></span> <span data-ttu-id="cb912-116">詳細については [、「Wake on LAN for Surface Dock 2」を参照してください。](wake-on-lan-surface-dock2.md)</span><span class="sxs-lookup"><span data-stu-id="cb912-116">To learn more, see [Wake on LAN for Surface Dock 2](wake-on-lan-surface-dock2.md)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="cb912-117">動作のしくみ</span><span class="sxs-lookup"><span data-stu-id="cb912-117">How it works</span></span>

<span data-ttu-id="cb912-118">使用しない場合、Surface デバイスは、モダン スタンバイまたは接続スタンバイと呼ばれるアイドル状態の低電力状態になります。</span><span class="sxs-lookup"><span data-stu-id="cb912-118">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="cb912-119">IT 管理者は、対象の Surface デバイスのメディア アクセス制御 (MAC) アドレスを含むウェイク 要求 (マジック パケット) を使用してデバイスをリモートでトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="cb912-119">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="cb912-120">WOL の組み込Microsoft Endpoint Configuration Managerサポートを提供する Microsoft Storeサードパーティ製アプリなど、多くの管理ソリューション。</span><span class="sxs-lookup"><span data-stu-id="cb912-120">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span> <span data-ttu-id="cb912-121">エンドポイント構成マネージャーを使用してデバイスを起動する方法の詳細については [、「Configure Wake on LAN - Configuration Manager」を参照してください](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)。</span><span class="sxs-lookup"><span data-stu-id="cb912-121">To learn more about waking devices with Endpoint Configuration Manager, see [Configure Wake on LAN - Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan).</span></span>

<span data-ttu-id="cb912-122">Wake on LAN のサポートは、スリープ状態 (接続スタンバイまたは休止状態 (S4 電源状態) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cb912-122">Support for Wake on LAN varies depending on sleep state:  Connected Standby or Hibernation (S4 power state).</span></span>

## <a name="connected-standby"></a><span data-ttu-id="cb912-123">接続スタンバイ</span><span class="sxs-lookup"><span data-stu-id="cb912-123">Connected Standby</span></span>

<span data-ttu-id="cb912-124">既定では、Windows 10スタンバイの Surface デバイスの Wake on LAN がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cb912-124">By default, Windows 10 supports Wake on LAN for Surface devices in Connected Standby.</span></span>

### <a name="supported-surface-devices---connected-standby"></a><span data-ttu-id="cb912-125">サポートされている Surface デバイス - 接続スタンバイ</span><span class="sxs-lookup"><span data-stu-id="cb912-125">Supported Surface devices - Connected Standby</span></span>

- <span data-ttu-id="cb912-126">Surface Laptop 4 (Intel プロセッサのみ)</span><span class="sxs-lookup"><span data-stu-id="cb912-126">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="cb912-127">Surface Laptop 3 (Intel プロセッサのみ)</span><span class="sxs-lookup"><span data-stu-id="cb912-127">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="cb912-128">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="cb912-128">Surface Pro 7+</span></span>
- <span data-ttu-id="cb912-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="cb912-129">Surface Pro 7</span></span>
- <span data-ttu-id="cb912-130">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="cb912-130">Surface Pro X</span></span>
- <span data-ttu-id="cb912-131">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="cb912-131">Surface Go 2</span></span>
- <span data-ttu-id="cb912-132">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="cb912-132">Surface Laptop Go</span></span>
- <span data-ttu-id="cb912-133">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="cb912-133">Surface Book 3</span></span>

## <a name="hibernation"></a><span data-ttu-id="cb912-134">休止状態</span><span class="sxs-lookup"><span data-stu-id="cb912-134">Hibernation</span></span>

<span data-ttu-id="cb912-135">デバイスを休止状態から解除するには[、Surface Enterprise](surface-enterprise-management-mode.md)管理モード (SEMM) を介して UEFI ポリシー設定を有効にする必要があります (Surface ドック 2 に接続されているデバイスでは必要ありません)。</span><span class="sxs-lookup"><span data-stu-id="cb912-135">To wake devices out of Hibernation requires enabling a UEFI policy setting via [Surface Enterprise Management Mode](surface-enterprise-management-mode.md) (SEMM) (not required for devices connected to Surface Dock 2).</span></span>

### <a name="supported-surface-devices---hibernation"></a><span data-ttu-id="cb912-136">サポートされている Surface デバイス - 休止状態</span><span class="sxs-lookup"><span data-stu-id="cb912-136">Supported Surface devices - Hibernation</span></span>

- <span data-ttu-id="cb912-137">Surface Laptop 4 (Intel プロセッサのみ)</span><span class="sxs-lookup"><span data-stu-id="cb912-137">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="cb912-138">Surface Laptop 3 (Intel プロセッサのみ)</span><span class="sxs-lookup"><span data-stu-id="cb912-138">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="cb912-139">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="cb912-139">Surface Pro 7+</span></span>
- <span data-ttu-id="cb912-140">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="cb912-140">Surface Pro 7</span></span>
- <span data-ttu-id="cb912-141">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="cb912-141">Surface Laptop Go</span></span>
- <span data-ttu-id="cb912-142">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="cb912-142">Surface Book 3</span></span>

### <a name="to-enable-wake-on-lan-uefi-setting"></a><span data-ttu-id="cb912-143">Wake on LAN UEFI の設定を有効にするには</span><span class="sxs-lookup"><span data-stu-id="cb912-143">To enable Wake on LAN UEFI setting</span></span>

<span data-ttu-id="cb912-144">Wake on LAN UEFI 設定を有効にするには、ターゲット デバイスを SEMM に登録し、構成パッケージを作成し、デバイスにパッケージを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb912-144">To enable the Wake on LAN UEFI setting you need to enroll target devices into SEMM, create a configuration package, and apply the package to the devices.</span></span> <span data-ttu-id="cb912-145">詳しくは、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb912-145">For more information, refer to:</span></span>

- [<span data-ttu-id="cb912-146">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="cb912-146">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="cb912-147">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="cb912-147">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)

1. <span data-ttu-id="cb912-148">[**Surface UEFI コンフィギュレーターをダウンロードしてインストールします**](https://www.microsoft.com/download/details.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="cb912-148">Download and install [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
2. <span data-ttu-id="cb912-149">[構成**パッケージ**  >  **の作成と**  >  **証明書の**  > **保護の開始] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="cb912-149">Select **Start** > **Configuration Package** > **Create** >**+ Certificate Protection**.</span></span>
3. <span data-ttu-id="cb912-150">[詳細設定]**に移動し\*\*\*\*、[Wake on LAN] を [オン]** に**切り替えます**。</span><span class="sxs-lookup"><span data-stu-id="cb912-150">Go to **Advanced settings** and switch **Wake on LAN** to **On**.</span></span>
4. <span data-ttu-id="cb912-151">パッケージをターゲット デバイスに適用します。</span><span class="sxs-lookup"><span data-stu-id="cb912-151">Apply the package to target devices.</span></span>

    > [!div class="mx-imgBorder"]
    > ![[LAN UEFI のスリープ解除] ポリシー設定を有効にする](images/wol-uefi.png)

## <a name="learn-more"></a><span data-ttu-id="cb912-153">詳細情報</span><span class="sxs-lookup"><span data-stu-id="cb912-153">Learn more</span></span>

- [<span data-ttu-id="cb912-154">Surface Dock 2 の WAKE on LAN</span><span class="sxs-lookup"><span data-stu-id="cb912-154">Wake on LAN for Surface Dock 2</span></span>](wake-on-lan-surface-dock2.md)
- [<span data-ttu-id="cb912-155">Microsoft Surface USB-C からイーサネットおよび USB アダプター</span><span class="sxs-lookup"><span data-stu-id="cb912-155">Microsoft Surface USB-C to Ethernet and USB Adapter</span></span>](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)
- [<span data-ttu-id="cb912-156">Surface USB 3.0 ギガビット イーサネット アダプター</span><span class="sxs-lookup"><span data-stu-id="cb912-156">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)
