---
title: Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある
description: 自動更新に関する Surface Hub のトラブルシューティング情報
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub、メンテナンスウィンドウ、更新プログラム
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 117c18cfce6dfb84b4fe2156ea98198f96da2abf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836405"
---
# <span data-ttu-id="819c1-104">Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある</span><span class="sxs-lookup"><span data-stu-id="819c1-104">Surface Hub may install updates and restart outside maintenance hours</span></span>

<span data-ttu-id="819c1-105">特定の状況では、Surface Hub は通常のメンテナンスウィンドウではなく、業務時間中に更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="819c1-105">Under specific circumstances, Surface Hub installs updates during business hours instead of during the regular maintenance window.</span></span> <span data-ttu-id="819c1-106">必要に応じて、デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="819c1-106">The device then restarts if it is necessary.</span></span> <span data-ttu-id="819c1-107">プロセスが完了するまでは、デバイスを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="819c1-107">You cannot use the device until the process is completed.</span></span>

> [!NOTE]  
> <span data-ttu-id="819c1-108">これは、メンテナンスウィンドウが見つからない場合の予期しない動作です。</span><span class="sxs-lookup"><span data-stu-id="819c1-108">This isn't expected behavior for missing a maintenance window.</span></span> <span data-ttu-id="819c1-109">これは、デバイスの日付が長いときにのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="819c1-109">It occurs only if the device is out-of-date for a long time.</span></span>

## <span data-ttu-id="819c1-110">原因</span><span class="sxs-lookup"><span data-stu-id="819c1-110">Cause</span></span>
<span data-ttu-id="819c1-111">Surface Hub を業務時間中も使用できるようにするために、ハブは設定で定義されているメンテナンスウィンドウで管理機能を実行するように構成されています (以下の「参照」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="819c1-111">To ensure that Surface Hub remains available for use during business hours, the Hub is configured to perform administrative functions during a maintenance window that is defined in Settings (see "References," below).</span></span> <span data-ttu-id="819c1-112">このメンテナンス期間中、ハブは Windows Update または Windows Server Update Service (WSUS) を通じて、利用可能な更新プログラムを自動的にインストールします。</span><span class="sxs-lookup"><span data-stu-id="819c1-112">During this maintenance period, the Hub automatically installs any available updates through Windows Update or Windows Server Update Service (WSUS).</span></span> <span data-ttu-id="819c1-113">更新が完了すると、ハブが再起動されることがあります。</span><span class="sxs-lookup"><span data-stu-id="819c1-113">Once updates are complete, the Hub may restart.</span></span>

<span data-ttu-id="819c1-114">更新プログラムは、Surface Hub がオンになっているが、使用されていない場合、または予約されている場合にのみ、メンテナンスウィンドウでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="819c1-114">Updates can be installed during the maintenance window only if the Surface Hub is turned on but not in use or reserved.</span></span> <span data-ttu-id="819c1-115">たとえば、24時間継続する会議のために Surface Hub がスケジュールされている場合、インストールがスケジュールされている更新は、次のメンテナンスウィンドウでハブが利用可能になるまで延期されます。</span><span class="sxs-lookup"><span data-stu-id="819c1-115">For example, if the Surface Hub is scheduled for a meeting that lasts 24 hours, any updates that are scheduled to be installed will be deferred until the Hub is available during the next maintenance window.</span></span> <span data-ttu-id="819c1-116">ハブがビジー状態で、複数のメンテナンスウィンドウが見つからない場合、ハブは最終的に更新プログラムのインストールとダウンロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="819c1-116">If the Hub continues to be busy and misses multiple maintenance windows, the Hub will eventually begin to install and download updates.</span></span> <span data-ttu-id="819c1-117">これは、メンテナンスウィンドウの途中または外部で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="819c1-117">This can occur during or outside the maintenance window.</span></span> <span data-ttu-id="819c1-118">ダウンロードとインストールが開始されると、デバイスが再起動されることがあります。</span><span class="sxs-lookup"><span data-stu-id="819c1-118">Once the download and installation has begun, the device may restart.</span></span>

## <span data-ttu-id="819c1-119">この問題を回避するには</span><span class="sxs-lookup"><span data-stu-id="819c1-119">To avoid this issue</span></span>

<span data-ttu-id="819c1-120">管理機能を実行するには、Surface Hub のメンテナンス時間を確保することが重要です。</span><span class="sxs-lookup"><span data-stu-id="819c1-120">It's important that you set aside maintenance time for Surface Hub to perform administrative functions.</span></span> <span data-ttu-id="819c1-121">24時間間隔で Surface Hub を予約するか、メンテナンスウィンドウ中にデバイスを使用すると、更新プログラムのインストールが遅延します。</span><span class="sxs-lookup"><span data-stu-id="819c1-121">Reserving the Surface Hub for 24 hour intervals or using the device during the maintenance window delays installing updates.</span></span> <span data-ttu-id="819c1-122">スケジュールされているメンテナンス期間中はハブを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="819c1-122">We recommend that you not use or reserve the Hub during scheduled maintenance period.</span></span> <span data-ttu-id="819c1-123">2時間のウィンドウは更新のために予約されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="819c1-123">A two-hour window should be reserved for updating.</span></span>

<span data-ttu-id="819c1-124">更新プログラムの可用性を制御するために使用できるオプションの1つは、Windows Server Update Service (WSUS) です。</span><span class="sxs-lookup"><span data-stu-id="819c1-124">One option that you can use to control the availability of updates is Windows Server Update Service (WSUS).</span></span> <span data-ttu-id="819c1-125">WSUS は、どの更新プログラムがインストールされているかを制御します。</span><span class="sxs-lookup"><span data-stu-id="819c1-125">WSUS provides control over what updates are installed and when.</span></span>

## <span data-ttu-id="819c1-126">参考文献</span><span class="sxs-lookup"><span data-stu-id="819c1-126">References</span></span> 
 
[<span data-ttu-id="819c1-127">Surface Hub の更新</span><span class="sxs-lookup"><span data-stu-id="819c1-127">Update the Surface Hub</span></span>](first-run-program-surface-hub.md#update-the-surface-hub) 

[<span data-ttu-id="819c1-128">メンテナンス期間</span><span class="sxs-lookup"><span data-stu-id="819c1-128">Maintenance window</span></span>](manage-windows-updates-for-surface-hub.md#maintenance-window) 

[<span data-ttu-id="819c1-129">Windows Server Update Services (WSUS) を使った Windows 10 更新プログラムの展開</span><span class="sxs-lookup"><span data-stu-id="819c1-129">Deploy Windows 10 updates using Windows Server Update Services (WSUS)</span></span>](/windows/deployment/update/waas-manage-updates-wsus) 


