---
title: Surface デバイス用のスリープ解除 (LAN) (Surface)
description: Wake On LAN を使ってデバイスをリモートでスリープ解除して管理タスクやメンテナンス タスクを実行する方法、または管理ソリューションを自動的に有効にする方法 (デバイスの電源が切っている場合でも) を参照してください。
keywords: 更新, 展開, ドライバー, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 709286cc0d62bd0b4c1e28e7626529fc4a215ae2
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271124"
---
# <span data-ttu-id="8e5c6-104">Surface デバイス での Wake On LAN の使用</span><span class="sxs-lookup"><span data-stu-id="8e5c6-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="8e5c6-105">Windows 10 バージョン 1607 (Windows 10 Anniversary Update とも呼ばれる) 以降を実行し、Surface イーサネット アダプターを使って有線ネットワークに接続する Surface デバイスは、コネクト スタンバイから Wake On LAN (WOL) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-105">Surface devices that run Windows 10, version 1607 (also known as Windows 10 Anniversary Update) or later and use a Surface Ethernet adapter to connect to a wired network, are capable of Wake On LAN (WOL) from Connected Standby.</span></span> <span data-ttu-id="8e5c6-106">WOL を使用すると、デバイスをリモートで起動して管理タスクやメンテナンス タスクを実行したり、管理ソリューション (Microsoft Endpoint Configuration Manager など) を自動的に有効にできます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-106">With WOL, you can remotely wake up devices to perform management or maintenance tasks or enable management solutions (such as Microsoft Endpoint Configuration Manager) automatically.</span></span> <span data-ttu-id="8e5c6-107">たとえば、オフィスが空の夜間のウィンドウで Microsoft Endpoint Configuration Manager を使用して、Surface ドックまたは Surface Pro 3 ドッキング ステーションにドッキングされた Surface デバイスにアプリケーションを展開できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-107">For example, you can deploy applications to Surface devices left docked with a Surface Dock or Surface Pro 3 Docking Station by using Microsoft Endpoint Configuration Manager during a window in the middle of the night, when the office is empty.</span></span>

>[!NOTE]
><span data-ttu-id="8e5c6-108">WOL をサポートするには、Surface デバイスを AC 電源と接続スタンバイ (スリープ) に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-108">Surface devices must be connected to AC power and in Connected Standby (Sleep) to support WOL.</span></span> <span data-ttu-id="8e5c6-109">休止状態にあるデバイスや電源がオフになっているデバイスでは、WOL を使用できません。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-109">WOL is not possible from devices that are in hibernation or powered off.</span></span>

## <span data-ttu-id="8e5c6-110">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="8e5c6-110">Supported devices</span></span>

<span data-ttu-id="8e5c6-111">WOL では、次のデバイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-111">The following devices are supported for WOL:</span></span>

* <span data-ttu-id="8e5c6-112">Surface Ethernet アダプター</span><span class="sxs-lookup"><span data-stu-id="8e5c6-112">Surface Ethernet adapter</span></span>
* <span data-ttu-id="8e5c6-113">Surface USB-C からイーサネットおよび USB アダプター</span><span class="sxs-lookup"><span data-stu-id="8e5c6-113">Surface USB-C to Ethernet and USB Adapter</span></span>
* <span data-ttu-id="8e5c6-114">Surface ドック</span><span class="sxs-lookup"><span data-stu-id="8e5c6-114">Surface Dock</span></span>
* <span data-ttu-id="8e5c6-115">Surface Pro 3 用 Surface ドッキング ステーション</span><span class="sxs-lookup"><span data-stu-id="8e5c6-115">Surface Docking Station for Surface Pro 3</span></span>
* <span data-ttu-id="8e5c6-116">Surface 3</span><span class="sxs-lookup"><span data-stu-id="8e5c6-116">Surface 3</span></span>
* <span data-ttu-id="8e5c6-117">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="8e5c6-117">Surface Pro 3</span></span>
* <span data-ttu-id="8e5c6-118">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="8e5c6-118">Surface Pro 4</span></span>
* <span data-ttu-id="8e5c6-119">Surface Pro (第 5 世代)</span><span class="sxs-lookup"><span data-stu-id="8e5c6-119">Surface Pro (5th Gen)</span></span>
* <span data-ttu-id="8e5c6-120">Surface Pro (第 5 世代) LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="8e5c6-120">Surface Pro (5th Gen) with LTE Advanced</span></span>
* <span data-ttu-id="8e5c6-121">Surface Book</span><span class="sxs-lookup"><span data-stu-id="8e5c6-121">Surface Book</span></span>
* <span data-ttu-id="8e5c6-122">Surface Laptop (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="8e5c6-122">Surface Laptop (1st Gen)</span></span>
* <span data-ttu-id="8e5c6-123">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="8e5c6-123">Surface Pro 6</span></span>
* <span data-ttu-id="8e5c6-124">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="8e5c6-124">Surface Book 2</span></span>
* <span data-ttu-id="8e5c6-125">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="8e5c6-125">Surface Laptop 2</span></span>
* <span data-ttu-id="8e5c6-126">Surface Go</span><span class="sxs-lookup"><span data-stu-id="8e5c6-126">Surface Go</span></span>
* <span data-ttu-id="8e5c6-127">Surface Go LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="8e5c6-127">Surface Go with LTE Advanced</span></span>
* <span data-ttu-id="8e5c6-128">Surface Studio 2 (下記の Surface Studio 2 の手順を参照)</span><span class="sxs-lookup"><span data-stu-id="8e5c6-128">Surface Studio 2 (see Surface Studio 2 instructions below)</span></span>
* <span data-ttu-id="8e5c6-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="8e5c6-129">Surface Pro 7</span></span>
* <span data-ttu-id="8e5c6-130">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="8e5c6-130">Surface Laptop 3</span></span>
* <span data-ttu-id="8e5c6-131">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="8e5c6-131">Surface Laptop Go</span></span>
* <span data-ttu-id="8e5c6-132">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="8e5c6-132">Surface Pro 7+</span></span>

## <span data-ttu-id="8e5c6-133">WOL ドライバー</span><span class="sxs-lookup"><span data-stu-id="8e5c6-133">WOL driver</span></span>

<span data-ttu-id="8e5c6-134">Surface デバイスで WOL サポートを有効にするには、Surface イーサネット アダプター用の特定のドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-134">To enable WOL support on Surface devices, a specific driver for the Surface Ethernet adapter is required.</span></span> <span data-ttu-id="8e5c6-135">このドライバーは、Surface デバイスの標準のドライバーおよびファームウェア パックには含まれていません。別途ダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-135">This driver is not included in the standard driver and firmware pack for Surface devices – you must download and install it separately.</span></span> <span data-ttu-id="8e5c6-136">Surface WOL ドライバー (SurfaceWOL.msi) は、Microsoft ダウンロード センターの [[Surface Tools for IT]](https://www.microsoft.com/download/details.aspx?id=46703) ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-136">You can download the Surface WOL driver (SurfaceWOL.msi) from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

<span data-ttu-id="8e5c6-137">Surface デバイスでこの Microsoft Windows インストーラー (.msi) ファイルを実行して Surface WOL ドライバーをインストールしたり、Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して Surface デバイスに配布することができます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-137">You can run this Microsoft Windows Installer (.msi) file on a Surface device to install the Surface WOL driver, or you can distribute it to Surface devices with an application deployment solution, such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="8e5c6-138">展開中に Surface WOL ドライバーを含めるには、展開プロセス中に .msi ファイルをアプリケーションとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-138">To include the Surface WOL driver during deployment, you can install the .msi file as an application during the deployment process.</span></span> <span data-ttu-id="8e5c6-139">展開プロセスに含める Surface WOL ドライバー ファイルを抽出することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-139">You can also extract the Surface WOL driver files to include them in the deployment process.</span></span> <span data-ttu-id="8e5c6-140">たとえば、Microsoft Deployment Toolkit (MDT) 展開共有に含めできます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-140">For example, you can include them in your Microsoft Deployment Toolkit (MDT) deployment share.</span></span> <span data-ttu-id="8e5c6-141">MDT による Surface の展開の詳細については、「Microsoft Deployment Toolkit を使った Surface デバイスへの [Windows 10 の展開」をご覧ください](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt)。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-141">You can read more about Surface deployment with MDT in [Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt).</span></span>

> [!NOTE]
> <span data-ttu-id="8e5c6-142">SurfaceWOL.msi のインストール時に、次のレジストリ キーの値を 1 に設定すると、WOL ドライバーがインストールされているシステムを簡単に識別できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-142">During the installation of SurfaceWOL.msi, the following registry key is set to a value of 1, which allows easy identification of systems where the WOL driver has been installed.</span></span> <span data-ttu-id="8e5c6-143">展開中にこれらのドライバーを個別に抽出してインストールすることを選択した場合、このレジストリ キーは構成されません。また、手動またはスクリプトを使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-143">If you chose to extract and install these drivers separately during deployment, this registry key will not be configured and must be configured manually or with a script.</span></span>
> 
> **<span data-ttu-id="8e5c6-144">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span><span class="sxs-lookup"><span data-stu-id="8e5c6-144">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span></span>** 

<span data-ttu-id="8e5c6-145">SurfaceWOL.msi の内容を抽出するには、次の例に示すように MSIExec 管理インストール オプション (**/a)** を使用して、コンテンツを C:\WOL\ フォルダーに抽出します。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-145">To extract the contents of SurfaceWOL.msi, use the MSIExec administrative installation option (**/a**), as shown in the following example, to extract the contents to the C:\WOL\ folder:</span></span>

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## <span data-ttu-id="8e5c6-146">Surface Studio 2 の手順</span><span class="sxs-lookup"><span data-stu-id="8e5c6-146">Surface Studio 2 instructions</span></span>

<span data-ttu-id="8e5c6-147">Surface Studio 2 で WOL を有効にするには、次の手順を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-147">To enable WOL on Surface Studio 2, you must use the following procedure</span></span>

1. <span data-ttu-id="8e5c6-148">次のレジストリ キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-148">Create the following registry keys:</span></span>

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. <span data-ttu-id="8e5c6-149">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-149">Run the following command</span></span>

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```

## <span data-ttu-id="8e5c6-150">Surface WOL の使用</span><span class="sxs-lookup"><span data-stu-id="8e5c6-150">Using Surface WOL</span></span>

<span data-ttu-id="8e5c6-151">Surface WOL ドライバーは WOL 標準に準拠しています。この場合、デバイスは、魔法のパケットと呼ばれる特別なネットワーク通信によって発生します。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-151">The Surface WOL driver conforms to the WOL standard, whereby the device is woken by a special network communication known as a magic packet.</span></span> <span data-ttu-id="8e5c6-152">この魔法のパケットは、255 の 6 バイト (または 16 進数の FF) と、ターゲット コンピューターの MAC アドレスの 16 回の繰り返しで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-152">The magic packet consists of 6 bytes of 255 (or FF in hexadecimal) followed by 16 repetitions of the target computer’s MAC address.</span></span> <span data-ttu-id="8e5c6-153">魔法のパケットと WOL 標準の詳細については [、Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-153">You can read more about the magic packet and the WOL standard on [Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet).</span></span>

>[!NOTE]
><span data-ttu-id="8e5c6-154">WOL を使用して魔法のパケットを送信し、デバイスをスリープ解除するには、ターゲット デバイスとイーサネット アダプターの MAC アドレスを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-154">To send a magic packet and wake up a device by using WOL, you must know the MAC address of the target device and Ethernet adapter.</span></span> <span data-ttu-id="8e5c6-155">この魔法のパケットは IP ネットワーク プロトコルを使用しないので、デバイスの IP アドレスまたは DNS 名を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-155">Because the magic packet does not use the IP network protocol, it is not possible to use the IP address or DNS name of the device.</span></span>

<span data-ttu-id="8e5c6-156">Configuration Manager などの多くの管理ソリューションは、WOL の組み込みサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-156">Many management solutions, such as Configuration Manager, provide built-in support for WOL.</span></span> <span data-ttu-id="8e5c6-157">また、Microsoft Store アプリ、PowerShell モジュール、サード パーティ製アプリケーション、サード パーティ製の管理ソリューションなど、多くのソリューションを使用して、デバイスをスリープ解除する魔法のパケットを送信できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-157">There are also many solutions, including Microsoft Store apps, PowerShell modules, third-party applications, and third-party management solutions that allow you to send a magic packet to wake up a device.</span></span> <span data-ttu-id="8e5c6-158">たとえば、TechNet スクリプト センターの [Wake On LAN PowerShell](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) モジュールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-158">For example, you can use the [Wake On LAN PowerShell module](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) from the TechNet Script Center.</span></span> 

>[!NOTE]
><span data-ttu-id="8e5c6-159">デバイスが魔法のパケットで起動された後、アプリケーションがシステム上のスリープをアクティブに妨げない場合、または AllowSystemRequiredPowerRequests レジストリ キーが 1 に構成されていない場合、デバイスはスリープ状態に戻ります。これにより、アプリケーションはスリープ状態を回避できます。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-159">After a device has been woken up with a magic packet, the device will return to sleep if an application is not actively preventing sleep on the system or if the AllowSystemRequiredPowerRequests registry key is not configured to 1, which allows applications to prevent sleep.</span></span> <span data-ttu-id="8e5c6-160">このレジストリ [キーの詳細については](#wol-driver) 、この記事の WOL ドライバーセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e5c6-160">See the [WOL driver](#wol-driver) section of this article for more information about this registry key.</span></span>
