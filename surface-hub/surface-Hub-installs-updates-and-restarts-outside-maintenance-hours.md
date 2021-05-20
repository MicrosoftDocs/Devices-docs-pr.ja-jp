---
title: Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある
description: 自動更新に関するSurface Hubトラブルシューティング情報
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub, メンテナンス ウィンドウ, 更新
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.date: 04/15/2021
ms.openlocfilehash: 7df7857258c1baeedf4ff239eda17c66c93a531c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577027"
---
# <a name="surface-hub-may-install-updates-and-restart-outside-maintenance-hours"></a><span data-ttu-id="b1cdf-104">Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある</span><span class="sxs-lookup"><span data-stu-id="b1cdf-104">Surface Hub may install updates and restart outside maintenance hours</span></span>

<span data-ttu-id="b1cdf-105">特定の状況では、Surface Hubメンテナンス期間中ではなく、営業時間内に更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-105">Under specific circumstances, Surface Hub installs updates during business hours instead of during the regular maintenance window.</span></span> <span data-ttu-id="b1cdf-106">必要に応じて、デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-106">The device then restarts if it is necessary.</span></span> <span data-ttu-id="b1cdf-107">プロセスが完了するまで、デバイスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-107">You cannot use the device until the process is completed.</span></span>

> [!NOTE]  
> <span data-ttu-id="b1cdf-108">メンテナンス ウィンドウが見つからない場合、これは予期しない動作です。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-108">This isn't expected behavior for missing a maintenance window.</span></span> <span data-ttu-id="b1cdf-109">これは、デバイスが長時間古い場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-109">It occurs only if the device is out-of-date for a long time.</span></span>

## <a name="cause"></a><span data-ttu-id="b1cdf-110">原因</span><span class="sxs-lookup"><span data-stu-id="b1cdf-110">Cause</span></span>

<span data-ttu-id="b1cdf-111">営業時間内Surface Hub使用できる状態を維持するために、ハブは 設定 で定義されているメンテナンス ウィンドウ中に管理機能を実行するように構成されています (以下の「参照」を参照)。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-111">To ensure that Surface Hub remains available for use during business hours, the Hub is configured to perform administrative functions during a maintenance window that is defined in Settings (see "References," below).</span></span> <span data-ttu-id="b1cdf-112">このメンテナンス期間中、ハブは、ビジネス向け更新プログラム (WUfB) Windows更新プログラムWindowsを使用して、利用可能な更新プログラムを自動的にインストールします。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-112">During this maintenance period, the Hub automatically installs any available updates through Windows Update or Windows Update for Business (WUfB).</span></span> <span data-ttu-id="b1cdf-113">更新が完了すると、ハブが再起動する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-113">Once updates are complete, the Hub may restart.</span></span>

<span data-ttu-id="b1cdf-114">更新プログラムは、更新プログラムが有効になっているが、Surface Hub予約されていない場合にのみ、メンテナンス 期間中にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-114">Updates can be installed during the maintenance window only if the Surface Hub is turned on but not in use or reserved.</span></span> <span data-ttu-id="b1cdf-115">たとえば、Surface Hub が 24 時間続く会議にスケジュールされている場合、インストールがスケジュールされている更新プログラムは、次のメンテナンス 期間中にハブが利用可能になるまで延期されます。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-115">For example, if the Surface Hub is scheduled for a meeting that lasts 24 hours, any updates that are scheduled to be installed will be deferred until the Hub is available during the next maintenance window.</span></span> <span data-ttu-id="b1cdf-116">ハブが引き続きビジー状態で、複数のメンテナンス ウィンドウを逃した場合、ハブは最終的に更新プログラムのインストールとダウンロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-116">If the Hub continues to be busy and misses multiple maintenance windows, the Hub will eventually begin to install and download updates.</span></span> <span data-ttu-id="b1cdf-117">これは、メンテナンス ウィンドウの間または外部で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-117">This can occur during or outside the maintenance window.</span></span> <span data-ttu-id="b1cdf-118">ダウンロードとインストールが開始すると、デバイスが再起動する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-118">Once the download and installation has begun, the device may restart.</span></span>

## <a name="to-avoid-this-issue"></a><span data-ttu-id="b1cdf-119">この問題を回避するには</span><span class="sxs-lookup"><span data-stu-id="b1cdf-119">To avoid this issue</span></span>

<span data-ttu-id="b1cdf-120">管理機能を実行する場合は、Surface Hubを確保することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-120">It's important that you set aside maintenance time for Surface Hub to perform administrative functions.</span></span> <span data-ttu-id="b1cdf-121">24 時間Surface Hub予約するか、メンテナンス ウィンドウで更新プログラムのインストールが遅れる間にデバイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-121">Reserving the Surface Hub for 24 hour intervals or using the device during the maintenance window delays installing updates.</span></span> <span data-ttu-id="b1cdf-122">スケジュールされたメンテナンス期間中は、ハブを使用または予約することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-122">We recommend that you not use or reserve the Hub during scheduled maintenance period.</span></span> <span data-ttu-id="b1cdf-123">更新用に 2 時間のウィンドウを予約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-123">A two-hour window should be reserved for updating.</span></span>

<span data-ttu-id="b1cdf-124">更新プログラムの可用性を制御するために使用できるオプションの 1 つは、「Update for Business Windowsを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-124">One option that you can use to control the availability of updates is Windows Update for Business.</span></span>

## <a name="learn-more"></a><span data-ttu-id="b1cdf-125">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b1cdf-125">Learn more</span></span>
 
- [<span data-ttu-id="b1cdf-126">Surface Hub の更新</span><span class="sxs-lookup"><span data-stu-id="b1cdf-126">Update the Surface Hub</span></span>](first-run-program-surface-hub.md#update-the-surface-hub) 
- [<span data-ttu-id="b1cdf-127">メンテナンス期間</span><span class="sxs-lookup"><span data-stu-id="b1cdf-127">Maintenance window</span></span>](manage-windows-updates-for-surface-hub.md#maintenance-window) 
