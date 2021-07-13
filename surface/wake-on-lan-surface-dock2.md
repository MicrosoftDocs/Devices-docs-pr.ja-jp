---
title: Surface Dock 2 とWake On LAN
description: Surface Dock 2 では、Wake on LAN (WOL) の最適なサポートが提供され、管理者はデバイスをリモートで起動し、管理タスクを自動的に実行できます。
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
ms.date: 7/02/2021
ms.openlocfilehash: 4a74efb8af776e9805ad3148ea656f0a65d5d09c
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643853"
---
# <a name="wake-on-lan-with-surface-dock-2"></a><span data-ttu-id="cc272-104">Surface Dock 2 とWake On LAN</span><span class="sxs-lookup"><span data-stu-id="cc272-104">Wake On LAN with Surface Dock 2</span></span>

<span data-ttu-id="cc272-105">デバイスを完全に最新の状態に保つために、IT 管理者は、通常は夜間のメンテナンス期間中に、使用していないデバイスを管理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc272-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="cc272-106">Surface Dock 2 では、Wake on LAN (WOL) に最適なサポートが提供され、管理者はデバイスをリモートで起動し、Microsoft エンドポイント マネージャー または他のサード パーティ製ソリューションを使用して管理タスクを自動的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="cc272-106">Surface Dock 2 provides the best support for Wake on LAN (WOL) enabling admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or other third party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc272-107">要件</span><span class="sxs-lookup"><span data-stu-id="cc272-107">Requirements</span></span>

<span data-ttu-id="cc272-108">デバイスは、Surface ドック 2 との有線接続を持ち、AC Power に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc272-108">Devices must have a wired connection with Surface Dock 2 and stay connected to AC Power.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a><span data-ttu-id="cc272-110">サポートされている Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="cc272-110">Supported Surface devices</span></span>

- <span data-ttu-id="cc272-111">Surface Laptop 4 (Intel プロセッサ)</span><span class="sxs-lookup"><span data-stu-id="cc272-111">Surface Laptop 4 (Intel processors)</span></span>
- <span data-ttu-id="cc272-112">Surface Laptop 4 (AMD プロセッサ)</span><span class="sxs-lookup"><span data-stu-id="cc272-112">Surface Laptop 4 (AMD processors)</span></span>
- <span data-ttu-id="cc272-113">Surface Laptop 3 (Intel プロセッサ)</span><span class="sxs-lookup"><span data-stu-id="cc272-113">Surface Laptop 3 (Intel processors)</span></span>
- <span data-ttu-id="cc272-114">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="cc272-114">Surface Pro 7+</span></span>
- <span data-ttu-id="cc272-115">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="cc272-115">Surface Pro 7</span></span>
- <span data-ttu-id="cc272-116">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="cc272-116">Surface Pro X</span></span>
- <span data-ttu-id="cc272-117">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="cc272-117">Surface Go 2</span></span>
- <span data-ttu-id="cc272-118">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="cc272-118">Surface Laptop Go</span></span>
- <span data-ttu-id="cc272-119">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="cc272-119">Surface Book 3</span></span>

<span data-ttu-id="cc272-120">Surface Dock 2 は、次の電源状態のデバイスに WOL サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="cc272-120">Surface Dock 2 provides WOL support for devices in the following power states:</span></span>

- <span data-ttu-id="cc272-121">コネクト スタンバイ</span><span class="sxs-lookup"><span data-stu-id="cc272-121">Connected standby</span></span>
- <span data-ttu-id="cc272-122">休止状態 (S4 電源状態)</span><span class="sxs-lookup"><span data-stu-id="cc272-122">Hibernation (S4 power state)</span></span>
- <span data-ttu-id="cc272-123">シャットダウン (S5 "soft off" 電源状態)</span><span class="sxs-lookup"><span data-stu-id="cc272-123">Shutdown (S5 “soft off” power state)</span></span>

<span data-ttu-id="cc272-124">電源状態の詳細については [、「System Power States」を参照してください](/windows/win32/power/system-power-states)。</span><span class="sxs-lookup"><span data-stu-id="cc272-124">To learn more about power states, see [System Power States](/windows/win32/power/system-power-states).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="cc272-125">動作のしくみ</span><span class="sxs-lookup"><span data-stu-id="cc272-125">How it works</span></span>

<span data-ttu-id="cc272-126">使用しない場合、Surface デバイスは、モダン スタンバイまたは接続スタンバイと呼ばれるアイドル状態の低電力状態になります。</span><span class="sxs-lookup"><span data-stu-id="cc272-126">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="cc272-127">IT 管理者は、対象の Surface デバイスのメディア アクセス制御 (MAC) アドレスを含むウェイク 要求 (マジック パケット) を使用してデバイスをリモートでトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="cc272-127">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="cc272-128">WOL の組み込Microsoft Endpoint Configuration Managerサポートを提供する Microsoft Storeサードパーティ製アプリなど、多くの管理ソリューション。</span><span class="sxs-lookup"><span data-stu-id="cc272-128">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span>

<span data-ttu-id="cc272-129">Surface ドック 2 を使用しないデバイスで WOL を有効にするには [、「Wake on LAN for Surface デバイス」を参照してください](wake-on-lan-for-surface-devices.md)。</span><span class="sxs-lookup"><span data-stu-id="cc272-129">To enable WOL on devices without Surface Dock 2, see [Wake on LAN for Surface devices](wake-on-lan-for-surface-devices.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="cc272-130">詳細情報</span><span class="sxs-lookup"><span data-stu-id="cc272-130">Learn more</span></span>

- [<span data-ttu-id="cc272-131">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="cc272-131">Surface Dock 2</span></span>](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [<span data-ttu-id="cc272-132">Surface デバイス の Wake On LAN</span><span class="sxs-lookup"><span data-stu-id="cc272-132">Wake On LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)
- [<span data-ttu-id="cc272-133">システムの電源状態</span><span class="sxs-lookup"><span data-stu-id="cc272-133">System Power States</span></span>](/windows/win32/power/system-power-states)
- [<span data-ttu-id="cc272-134">Wake on LAN の構成 - Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="cc272-134">Configure Wake on LAN - Configuration Manager</span></span>](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)
