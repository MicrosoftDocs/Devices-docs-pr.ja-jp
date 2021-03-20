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
ms.date: 3/19/2021
ms.openlocfilehash: 1fbbf899876d154469d48fa75a179196697205c1
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442167"
---
# <a name="wake-on-lan-for-surface-devices"></a><span data-ttu-id="ac30d-104">Surface デバイス での Wake On LAN の使用</span><span class="sxs-lookup"><span data-stu-id="ac30d-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="ac30d-105">Surface Ethernet アダプターを使用して有線ネットワークに接続する Surface デバイスは、コネクト スタンバイから Wake On LAN (WOL) を利用できます。</span><span class="sxs-lookup"><span data-stu-id="ac30d-105">Surface devices that use a Surface Ethernet adapter to connect to a wired network can take advantage of Wake On LAN (WOL) from Connected Standby.</span></span> <span data-ttu-id="ac30d-106">WOL を使用すると、デバイスをリモートで起動し、Microsoft Endpoint Manager/Microsoft Intune などの管理ソリューションを使用して管理タスクを自動的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ac30d-106">With WOL, you can remotely wake up devices and automatically perform management tasks using management solutions such as Microsoft Endpoint Manager/Microsoft Intune.</span></span>

## <a name="wol-supported-devices"></a><span data-ttu-id="ac30d-107">WOL がサポートするデバイス</span><span class="sxs-lookup"><span data-stu-id="ac30d-107">WOL-supported devices</span></span>

- <span data-ttu-id="ac30d-108">Surface Ethernet アダプター</span><span class="sxs-lookup"><span data-stu-id="ac30d-108">Surface Ethernet adapter</span></span>
- <span data-ttu-id="ac30d-109">Surface USB-C からイーサネットおよび USB アダプター</span><span class="sxs-lookup"><span data-stu-id="ac30d-109">Surface USB-C to Ethernet and USB Adapter</span></span>
- <span data-ttu-id="ac30d-110">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="ac30d-110">Surface Dock 2</span></span>
- <span data-ttu-id="ac30d-111">Surface Pro 6 以降</span><span class="sxs-lookup"><span data-stu-id="ac30d-111">Surface Pro 6 and later</span></span>
- <span data-ttu-id="ac30d-112">Surface Book (すべての世代)</span><span class="sxs-lookup"><span data-stu-id="ac30d-112">Surface Book (all generations)</span></span>
- <span data-ttu-id="ac30d-113">Surface Laptop (すべての世代)</span><span class="sxs-lookup"><span data-stu-id="ac30d-113">Surface Laptop (all generations)</span></span>
- <span data-ttu-id="ac30d-114">Surface Go (すべての世代)</span><span class="sxs-lookup"><span data-stu-id="ac30d-114">Surface Go (all generations)</span></span>
- <span data-ttu-id="ac30d-115">Surface Studio 2 (付録を参照)</span><span class="sxs-lookup"><span data-stu-id="ac30d-115">Surface Studio 2 (see Appendix)</span></span>


## <a name="using-surface-wol"></a><span data-ttu-id="ac30d-116">Surface WOL の使用</span><span class="sxs-lookup"><span data-stu-id="ac30d-116">Using Surface WOL</span></span>

<span data-ttu-id="ac30d-117">IT 管理者は、対象のコンピューターの MAC アドレスを含むウェイク オン LAN 要求 (マジック パケット) を使用してデバイスをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="ac30d-117">IT admins can trigger devices using a wake on LAN request (magic packet) that contains the target computer’s MAC address.</span></span> <span data-ttu-id="ac30d-118">WOL を使用してマジック パケットを送信し、デバイスをスリープ解除するには、ターゲット デバイスとイーサネット アダプターの MAC アドレスを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac30d-118">To send a magic packet and wake up a device by using WOL, you must know the MAC address of the target device and Ethernet adapter.</span></span> <span data-ttu-id="ac30d-119">マジック パケットは IP ネットワーク プロトコルを使用しないので、デバイスの IP アドレスまたは DNS 名を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ac30d-119">Because the magic packet does not use the IP network protocol, it is not possible to use the IP address or DNS name of the device.</span></span>

<span data-ttu-id="ac30d-120">Microsoft Endpoint Configuration Manager やサード パーティの Microsoft Store アプリなどの多くの管理ソリューションは、WOL の組み込みのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="ac30d-120">Many management solutions, such as Microsoft Endpoint Configuration Manager and third party Microsoft Store apps provide built-in support for WOL.</span></span> <span data-ttu-id="ac30d-121">デバイスは、接続スタンバイ (スリープ) モードで AC 電源に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac30d-121">Note that devices need to be in Connected Standby (Sleep) mode and connected to AC power.</span></span> <span data-ttu-id="ac30d-122">エンドポイント構成マネージャーを使用してデバイスを起動する方法の詳細については [、「Configure Wake on LAN - Configuration Manager」を参照してください](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan)。</span><span class="sxs-lookup"><span data-stu-id="ac30d-122">To learn more about waking devices with Endpoint Configuration Manager, see [Configure Wake on LAN - Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan).</span></span>


## <a name="to-check-wol-is-enabled-on-your-device"></a><span data-ttu-id="ac30d-123">デバイスで WOL が有効になっているのを確認するには</span><span class="sxs-lookup"><span data-stu-id="ac30d-123">To check WOL is enabled on your device</span></span>

1. <span data-ttu-id="ac30d-124">イーサネット接続デバイスで、ネットワーク アダプターを選択し、[プロパティ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="ac30d-124">On your Ethernet connected device, select your network adapter, and then select **Properties**.</span></span>

   > [!div class="mx-imgBorder"]
   > ![Surface Ethernet Adapter](images/surface-ethernet.png)

2. <span data-ttu-id="ac30d-126">[詳細設定**の構成]**  >  **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ac30d-126">Select **Configure** > **Advanced**.</span></span>
3. <span data-ttu-id="ac30d-127">[最新の **スタンバイ WoL マジック パケット] までスクロールし、[** 有効 **] が** 選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac30d-127">Scroll to **Modern Standby WoL Magic Packet** and ensure **Enabled** is selected.</span></span>

     ![デバイスで WOL が有効になっているか確認する](images/ethernet-wol-setting.png)

## <a name="appendix-surface-studio-2"></a><span data-ttu-id="ac30d-129">付録: Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="ac30d-129">Appendix: Surface Studio 2</span></span>

<span data-ttu-id="ac30d-130">Surface Studio 2 で WOL を有効にするには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac30d-130">To enable WOL on Surface Studio 2, use the following procedure.</span></span>

1. <span data-ttu-id="ac30d-131">次のレジストリ キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac30d-131">Create the following registry keys:</span></span>

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. <span data-ttu-id="ac30d-132">次のコマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="ac30d-132">Run the following command</span></span>

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```


## <a name="learn-more"></a><span data-ttu-id="ac30d-133">詳細情報</span><span class="sxs-lookup"><span data-stu-id="ac30d-133">Learn more</span></span>

- [<span data-ttu-id="ac30d-134">Microsoft Surface USB-C からイーサネットおよび USB アダプター</span><span class="sxs-lookup"><span data-stu-id="ac30d-134">Microsoft Surface USB-C to Ethernet and USB Adapter</span></span>](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)

- [<span data-ttu-id="ac30d-135">Surface USB 3.0 ギガビット イーサネット アダプター</span><span class="sxs-lookup"><span data-stu-id="ac30d-135">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)
