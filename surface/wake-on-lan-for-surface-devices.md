---
title: Surface devices 用の Wake on LAN (Surface)
description: デバイスに電源が入っていない場合でも、Wake on LAN を使用して、管理またはメンテナンスタスクを実行したり、管理ソリューションを自動的に有効にしたりする方法について説明します。
keywords: update、deploy、driver、wol、wake on-lan
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
ms.openlocfilehash: 760ba75ea7b36238d6de722d38e44a3854073112
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835510"
---
# <span data-ttu-id="1168c-104">Surface デバイス での Wake On LAN の使用</span><span class="sxs-lookup"><span data-stu-id="1168c-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="1168c-105">Windows 10、バージョン 1607 (Windows 10 記念日更新とも呼ばれます) 以降を実行している surface デバイスで、Surface Ethernet アダプターを使って有線ネットワークに接続し、接続されたスタンバイからの Wake On LAN (WOL) 機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1168c-105">Surface devices that run Windows 10, version 1607 (also known as Windows 10 Anniversary Update) or later and use a Surface Ethernet adapter to connect to a wired network, are capable of Wake On LAN (WOL) from Connected Standby.</span></span> <span data-ttu-id="1168c-106">WOL を使用すると、デバイスをリモートでスリープ解除して管理またはメンテナンスタスクを実行したり、管理ソリューション (Microsoft Endpoint Configuration Manager など) を自動的に有効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1168c-106">With WOL, you can remotely wake up devices to perform management or maintenance tasks or enable management solutions (such as Microsoft Endpoint Configuration Manager) automatically.</span></span> <span data-ttu-id="1168c-107">たとえば、Surface Dock または Surface Pro 3 のドッキングステーションと共にドッキングされた Surface デバイスにアプリケーションを展開するには、office が空になっているときに、夜間中央のウィンドウで Microsoft Endpoint Configuration Manager を使用します。</span><span class="sxs-lookup"><span data-stu-id="1168c-107">For example, you can deploy applications to Surface devices left docked with a Surface Dock or Surface Pro 3 Docking Station by using Microsoft Endpoint Configuration Manager during a window in the middle of the night, when the office is empty.</span></span>

>[!NOTE]
><span data-ttu-id="1168c-108">WOL をサポートするには、Surface デバイスが AC 電源に接続され、接続されたスタンバイ (スリープ) に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1168c-108">Surface devices must be connected to AC power and in Connected Standby (Sleep) to support WOL.</span></span> <span data-ttu-id="1168c-109">休止状態または電源がオフになっているデバイスから WOL は使用できません。</span><span class="sxs-lookup"><span data-stu-id="1168c-109">WOL is not possible from devices that are in hibernation or powered off.</span></span>

## <span data-ttu-id="1168c-110">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="1168c-110">Supported devices</span></span>

<span data-ttu-id="1168c-111">WOL では、次のデバイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1168c-111">The following devices are supported for WOL:</span></span>

* <span data-ttu-id="1168c-112">Surface Ethernet アダプター</span><span class="sxs-lookup"><span data-stu-id="1168c-112">Surface Ethernet adapter</span></span>
* <span data-ttu-id="1168c-113">Surface USB-C ~ Ethernet および USB アダプター</span><span class="sxs-lookup"><span data-stu-id="1168c-113">Surface USB-C to Ethernet and USB Adapter</span></span>
* <span data-ttu-id="1168c-114">Surface ドック</span><span class="sxs-lookup"><span data-stu-id="1168c-114">Surface Dock</span></span>
* <span data-ttu-id="1168c-115">Surface Pro 3 用 surface ドッキングステーション</span><span class="sxs-lookup"><span data-stu-id="1168c-115">Surface Docking Station for Surface Pro 3</span></span>
* <span data-ttu-id="1168c-116">Surface 3</span><span class="sxs-lookup"><span data-stu-id="1168c-116">Surface 3</span></span>
* <span data-ttu-id="1168c-117">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="1168c-117">Surface Pro 3</span></span>
* <span data-ttu-id="1168c-118">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="1168c-118">Surface Pro 4</span></span>
* <span data-ttu-id="1168c-119">Surface Pro (第5世代)</span><span class="sxs-lookup"><span data-stu-id="1168c-119">Surface Pro (5th Gen)</span></span>
* <span data-ttu-id="1168c-120">LTE アドバンスト付き Surface Pro (第5世代)</span><span class="sxs-lookup"><span data-stu-id="1168c-120">Surface Pro (5th Gen) with LTE Advanced</span></span>
* <span data-ttu-id="1168c-121">Surface Book</span><span class="sxs-lookup"><span data-stu-id="1168c-121">Surface Book</span></span>
* <span data-ttu-id="1168c-122">Surface ラップトップ (第1世代)</span><span class="sxs-lookup"><span data-stu-id="1168c-122">Surface Laptop (1st Gen)</span></span>
* <span data-ttu-id="1168c-123">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="1168c-123">Surface Pro 6</span></span>
* <span data-ttu-id="1168c-124">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="1168c-124">Surface Book 2</span></span>
* <span data-ttu-id="1168c-125">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="1168c-125">Surface Laptop 2</span></span>
* <span data-ttu-id="1168c-126">Surface Go</span><span class="sxs-lookup"><span data-stu-id="1168c-126">Surface Go</span></span>
* <span data-ttu-id="1168c-127">Surface Go LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="1168c-127">Surface Go with LTE Advanced</span></span>
* <span data-ttu-id="1168c-128">Surface Studio 2 (以下の「Surface Studio 2 の手順」を参照)</span><span class="sxs-lookup"><span data-stu-id="1168c-128">Surface Studio 2 (see Surface Studio 2 instructions below)</span></span>
* <span data-ttu-id="1168c-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="1168c-129">Surface Pro 7</span></span>
* <span data-ttu-id="1168c-130">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="1168c-130">Surface Laptop 3</span></span>

## <span data-ttu-id="1168c-131">WOL ドライバー</span><span class="sxs-lookup"><span data-stu-id="1168c-131">WOL driver</span></span>

<span data-ttu-id="1168c-132">Surface デバイスで WOL サポートを有効にするには、Surface Ethernet アダプター用の特定のドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="1168c-132">To enable WOL support on Surface devices, a specific driver for the Surface Ethernet adapter is required.</span></span> <span data-ttu-id="1168c-133">このドライバーは、Surface デバイス用の標準ドライバーとファームウェアパックに含まれていません。別途ダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1168c-133">This driver is not included in the standard driver and firmware pack for Surface devices – you must download and install it separately.</span></span> <span data-ttu-id="1168c-134">Surface WOL ドライバー (SurfaceWOL.msi) は、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1168c-134">You can download the Surface WOL driver (SurfaceWOL.msi) from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

<span data-ttu-id="1168c-135">Surface デバイスでこの Microsoft Windows インストーラー (.msi) ファイルを実行して Surface WOL ドライバーをインストールしたり、Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して Surface デバイスに配布したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1168c-135">You can run this Microsoft Windows Installer (.msi) file on a Surface device to install the Surface WOL driver, or you can distribute it to Surface devices with an application deployment solution, such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="1168c-136">展開時に Surface WOL ドライバーを含めるには、展開プロセス中に .msi ファイルをアプリケーションとしてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="1168c-136">To include the Surface WOL driver during deployment, you can install the .msi file as an application during the deployment process.</span></span> <span data-ttu-id="1168c-137">Surface WOL ドライバーファイルを抽出して展開プロセスに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="1168c-137">You can also extract the Surface WOL driver files to include them in the deployment process.</span></span> <span data-ttu-id="1168c-138">たとえば、Microsoft 展開ツールキット (MDT) 展開共有にそれらを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1168c-138">For example, you can include them in your Microsoft Deployment Toolkit (MDT) deployment share.</span></span> <span data-ttu-id="1168c-139">MDT での Surface の展開の詳細については、「 [Windows 10 を surface デバイスに展開して Microsoft 展開ツールキットを使用](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1168c-139">You can read more about Surface deployment with MDT in [Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt).</span></span>

> [!NOTE]
> <span data-ttu-id="1168c-140">SurfaceWOL.msi のインストール中に、次のレジストリキーが1の値に設定されます。これにより、WOL ドライバーがインストールされているシステムを簡単に識別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1168c-140">During the installation of SurfaceWOL.msi, the following registry key is set to a value of 1, which allows easy identification of systems where the WOL driver has been installed.</span></span> <span data-ttu-id="1168c-141">展開時にこれらのドライバーを個別に抽出してインストールする場合は、このレジストリキーは構成されず、手動で、またはスクリプトを使って構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1168c-141">If you chose to extract and install these drivers separately during deployment, this registry key will not be configured and must be configured manually or with a script.</span></span>
> 
> **<span data-ttu-id="1168c-142">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span><span class="sxs-lookup"><span data-stu-id="1168c-142">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span></span>** 

<span data-ttu-id="1168c-143">SurfaceWOL.msi の内容を抽出するには、次の例に示すように MSIExec 管理インストールオプション (**/a**) を使用して、コンテンツを C:\WOL\ フォルダーに抽出します。</span><span class="sxs-lookup"><span data-stu-id="1168c-143">To extract the contents of SurfaceWOL.msi, use the MSIExec administrative installation option (**/a**), as shown in the following example, to extract the contents to the C:\WOL\ folder:</span></span>

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## <span data-ttu-id="1168c-144">Surface Studio 2 の手順</span><span class="sxs-lookup"><span data-stu-id="1168c-144">Surface Studio 2 instructions</span></span>

<span data-ttu-id="1168c-145">Surface Studio 2 で WOL を有効にするには、次の手順を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1168c-145">To enable WOL on Surface Studio 2, you must use the following procedure</span></span>

1. <span data-ttu-id="1168c-146">次のレジストリキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1168c-146">Create the following registry keys:</span></span>

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. <span data-ttu-id="1168c-147">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1168c-147">Run the following command</span></span>

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```

## <span data-ttu-id="1168c-148">Surface WOL の使用</span><span class="sxs-lookup"><span data-stu-id="1168c-148">Using Surface WOL</span></span>

<span data-ttu-id="1168c-149">Surface WOL ドライバーは、WOL 標準に準拠しているため、デバイスはマジックパケットと呼ばれる特殊なネットワーク通信によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1168c-149">The Surface WOL driver conforms to the WOL standard, whereby the device is woken by a special network communication known as a magic packet.</span></span> <span data-ttu-id="1168c-150">Magic packet は、6バイトの 255 (または16進数の FF) で構成され、その後にターゲットコンピューターの MAC アドレスが16回繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="1168c-150">The magic packet consists of 6 bytes of 255 (or FF in hexadecimal) followed by 16 repetitions of the target computer’s MAC address.</span></span> <span data-ttu-id="1168c-151">この magic packet と[ウィキペディア](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet)の WOL 標準の詳細については、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1168c-151">You can read more about the magic packet and the WOL standard on [Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet).</span></span>

>[!NOTE]
><span data-ttu-id="1168c-152">WOL を使って magic packet を送信し、デバイスをウェイクアップするには、ターゲットデバイスとイーサネットアダプターの MAC アドレスがわかっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1168c-152">To send a magic packet and wake up a device by using WOL, you must know the MAC address of the target device and Ethernet adapter.</span></span> <span data-ttu-id="1168c-153">Magic packet では IP ネットワークプロトコルを使用していないため、デバイスの IP アドレスまたは DNS 名を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="1168c-153">Because the magic packet does not use the IP network protocol, it is not possible to use the IP address or DNS name of the device.</span></span>

<span data-ttu-id="1168c-154">Configuration Manager などの多くの管理ソリューションは、WOL の組み込みサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="1168c-154">Many management solutions, such as Configuration Manager, provide built-in support for WOL.</span></span> <span data-ttu-id="1168c-155">Microsoft ストアアプリ、PowerShell モジュール、サードパーティ製のアプリケーション、サードパーティ製の管理ソリューションなど、デバイスをスリープ状態にするための magic packet を送信できるソリューションも数多くあります。</span><span class="sxs-lookup"><span data-stu-id="1168c-155">There are also many solutions, including Microsoft Store apps, PowerShell modules, third-party applications, and third-party management solutions that allow you to send a magic packet to wake up a device.</span></span> <span data-ttu-id="1168c-156">たとえば、TechNet スクリプトセンターで[Wake ON LAN PowerShell モジュール](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4)を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1168c-156">For example, you can use the [Wake On LAN PowerShell module](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) from the TechNet Script Center.</span></span> 

>[!NOTE]
><span data-ttu-id="1168c-157">デバイスが magic packet で起動された後、アプリケーションがシステムのスリープを積極的に妨害していない場合、または AllowSystemRequiredPowerRequests レジストリキーが1に設定されていない場合は、デバイスはスリープ状態に戻ります。これにより、アプリケーションはスリープを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="1168c-157">After a device has been woken up with a magic packet, the device will return to sleep if an application is not actively preventing sleep on the system or if the AllowSystemRequiredPowerRequests registry key is not configured to 1, which allows applications to prevent sleep.</span></span> <span data-ttu-id="1168c-158">このレジストリキーの詳細については、この記事の「 [WOL ドライバー](#wol-driver) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1168c-158">See the [WOL driver](#wol-driver) section of this article for more information about this registry key.</span></span>
