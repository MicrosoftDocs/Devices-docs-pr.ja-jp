---
title: Windows 10 Team 2020 の更新プログラムをインストールする
description: Surface Hub オペレーティング システムの Windows 10 Team 2020 Update の最新の更新プログラムを取得します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/17/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 4d68f751bd15ef6529bcd16a6305d8c682970747
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470415"
---
# <a name="install-windows-10-team-2020-update"></a><span data-ttu-id="e79b3-104">Windows 10 Team 2020 の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="e79b3-104">Install Windows 10 Team 2020 Update</span></span> 

<span data-ttu-id="e79b3-105">新しい Surface Hub オペレーティング システム **である Windows 10 Team 2020 Update は、Windows 10**バージョン 20H2 に基づいて、Surface Hub 2S と元の Surface Hub (v1) で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e79b3-105">The new Surface Hub operating system, **Windows 10 Team 2020 Update**, based on Windows 10 version 20H2, is now available for Surface Hub 2S and the original Surface Hub (v1).</span></span> 

- <span data-ttu-id="e79b3-106">「既知の [問題: Windows 10 Team 2020 Update」も参照してください。](surface-hub-2020-team-update-known-issues.md)</span><span class="sxs-lookup"><span data-stu-id="e79b3-106">See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-team-update-known-issues.md)</span></span>

## <a name="distribution"></a><span data-ttu-id="e79b3-107">[Distribution] (配布)</span><span class="sxs-lookup"><span data-stu-id="e79b3-107">Distribution</span></span>

<span data-ttu-id="e79b3-108">Windows 2020 Update は、次のいずれかの方法で取得できます。</span><span class="sxs-lookup"><span data-stu-id="e79b3-108">You can obtain Windows 2020 Update using one of the following methods:</span></span>

- <span data-ttu-id="e79b3-109">**Windows Update for Business**.</span><span class="sxs-lookup"><span data-stu-id="e79b3-109">**Windows Update for Business**.</span></span>
- <span data-ttu-id="e79b3-110">**ベア メタル回復 (BMR) イメージ**。</span><span class="sxs-lookup"><span data-stu-id="e79b3-110">**Bare metal recovery (BMR) image**.</span></span> <span data-ttu-id="e79b3-111">デバイスを Azure Active Directory に参加したり、デバイスがインターネットから更新プログラムを受け取るのを許可しない場合に推奨されるオプションです。</span><span class="sxs-lookup"><span data-stu-id="e79b3-111">Recommended option for customers who join their devices to Azure Active Directory or don’t allow their devices to receive updates from the internet.</span></span> <span data-ttu-id="e79b3-112">開始するには [、「Surface の回復イメージをダウンロードする」を参照してください](https://support.microsoft.com/surfacerecoveryimage)。</span><span class="sxs-lookup"><span data-stu-id="e79b3-112">To get started, see [Download a recovery image for your Surface](https://support.microsoft.com/surfacerecoveryimage).</span></span>
- **<span data-ttu-id="e79b3-113">Windows Update。</span><span class="sxs-lookup"><span data-stu-id="e79b3-113">Windows Update.</span></span>** <span data-ttu-id="e79b3-114">可用性は、次の表に示す地域/国によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e79b3-114">Availability varies by region/country, as noted in the following table:</span></span>

| <span data-ttu-id="e79b3-115">フェーズ</span><span class="sxs-lookup"><span data-stu-id="e79b3-115">Phase</span></span> | <span data-ttu-id="e79b3-116">国/地域</span><span class="sxs-lookup"><span data-stu-id="e79b3-116">Country/Region</span></span>                         | <span data-ttu-id="e79b3-117">開始</span><span class="sxs-lookup"><span data-stu-id="e79b3-117">Starting</span></span>          |
| ----- | -------------------------------------- | ----------------- |
| <span data-ttu-id="e79b3-118">1</span><span class="sxs-lookup"><span data-stu-id="e79b3-118">1</span></span>     | <span data-ttu-id="e79b3-119">NZ, オーストラリア, カナダ, ベルギー, メキシコ</span><span class="sxs-lookup"><span data-stu-id="e79b3-119">NZ, Australia, Canada, Belgium, Mexico</span></span> | <span data-ttu-id="e79b3-120">2020 年 10 月</span><span class="sxs-lookup"><span data-stu-id="e79b3-120">October 2020</span></span>  |
| <span data-ttu-id="e79b3-121">2</span><span class="sxs-lookup"><span data-stu-id="e79b3-121">2</span></span>     | <span data-ttu-id="e79b3-122">英国、日本、スイス、イタリア</span><span class="sxs-lookup"><span data-stu-id="e79b3-122">UK, Japan, Switzerland, Italy</span></span>          | <span data-ttu-id="e79b3-123">2020 年 11 月</span><span class="sxs-lookup"><span data-stu-id="e79b3-123">November 2020</span></span> |
| <span data-ttu-id="e79b3-124">3</span><span class="sxs-lookup"><span data-stu-id="e79b3-124">3</span></span>     | <span data-ttu-id="e79b3-125">ドイツ、オランダ</span><span class="sxs-lookup"><span data-stu-id="e79b3-125">Germany, Netherlands</span></span>                   | <span data-ttu-id="e79b3-126">2021 年 2 月下旬</span><span class="sxs-lookup"><span data-stu-id="e79b3-126">Late February 2021</span></span> |
| <span data-ttu-id="e79b3-127">4</span><span class="sxs-lookup"><span data-stu-id="e79b3-127">4</span></span>     | <span data-ttu-id="e79b3-128">グローバル</span><span class="sxs-lookup"><span data-stu-id="e79b3-128">Global</span></span>                                 | <span data-ttu-id="e79b3-129">2021 年 3 月上旬</span><span class="sxs-lookup"><span data-stu-id="e79b3-129">Early March 2021</span></span> |

## <a name="servicing-surface-hubs-with-windows-10-team-edition-version-1703"></a><span data-ttu-id="e79b3-130">Windows 10 Team Edition バージョン 1703 での Surface Hubs のサービス</span><span class="sxs-lookup"><span data-stu-id="e79b3-130">Servicing Surface Hubs with Windows 10 Team Edition version 1703</span></span> 

<span data-ttu-id="e79b3-131">[Windows 10 Team Edition バージョン 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f)のフル サービス サポートは、2021 年 3 月 16 日まで継続する予定です。</span><span class="sxs-lookup"><span data-stu-id="e79b3-131">Full servicing support for [Windows 10 Team Edition version 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f) is scheduled to continue until March 16, 2021.</span></span>

### <a name="2s-devices"></a><span data-ttu-id="e79b3-132">2S デバイス</span><span class="sxs-lookup"><span data-stu-id="e79b3-132">2S devices</span></span> 

<span data-ttu-id="e79b3-133">すべての地域のお客様は、「Surface Hub [2S](surface-hub-2s-recover-reset.md)のリセットと回復」で説明したように、Surface Hub 2S デバイスを Windows Update、Windows Update for Business、またはベア メタル回復 (BMR) イメージを使用して 2020 Update に更新できます。</span><span class="sxs-lookup"><span data-stu-id="e79b3-133">Customers in all regions can update their Surface Hub 2S devices to the 2020 Update through Windows Update, Windows Update for Business or by using the bare metal recovery (BMR) image, as explained in [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span>

### <a name="v1-devices"></a><span data-ttu-id="e79b3-134">V1 デバイス</span><span class="sxs-lookup"><span data-stu-id="e79b3-134">V1 devices</span></span> 

<span data-ttu-id="e79b3-135">すべての地域のお客様は、Windows Update、Windows Update for Business、または Surface Hub 回復ツールを使用して、Surface Hub v1 デバイスを 2020 Update に [更新できます](surface-hub-recovery-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="e79b3-135">Customers in all regions can update their Surface Hub v1 devices to the 2020 Update through Windows Update, Windows Update for Business, or by [using the Surface Hub Recovery Tool](surface-hub-recovery-tool.md).</span></span> <span data-ttu-id="e79b3-136">更新プログラムを受信するには、KB5000749 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79b3-136">KB5000749 must be installed in order to receive the update over-the-air.</span></span> <span data-ttu-id="e79b3-137">詳細については [、「Surface IT Pro ブログ」を参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-hub-v1-status/ba-p/2118371)。</span><span class="sxs-lookup"><span data-stu-id="e79b3-137">To learn more, see [Surface IT Pro Blog](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-hub-v1-status/ba-p/2118371).</span></span>
 
## <a name="whats-new"></a><span data-ttu-id="e79b3-138">新機能</span><span class="sxs-lookup"><span data-stu-id="e79b3-138">What’s new</span></span>

<span data-ttu-id="e79b3-139">Windows 10 Team 2020 Update は、最新の Windows 10 機能と共に、デバイスの展開と管理性に大きな改善を提供します。</span><span class="sxs-lookup"><span data-stu-id="e79b3-139">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="e79b3-140">詳細については [、「Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e79b3-140">To learn more, see [What's new in Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md).</span></span>
 
## <a name="before-you-begin"></a><span data-ttu-id="e79b3-141">始める前に</span><span class="sxs-lookup"><span data-stu-id="e79b3-141">Before you begin</span></span>

<span data-ttu-id="e79b3-142">Windows 10 Team 2020 Update をインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。</span><span class="sxs-lookup"><span data-stu-id="e79b3-142">Prior to installing Windows 10 Team 2020 Update, make sure you save the BitLocker key associated with your device.</span></span> 

**<span data-ttu-id="e79b3-143">BitLocker キーを手動で保存するには</span><span class="sxs-lookup"><span data-stu-id="e79b3-143">To manually save your BitLocker key</span></span>**

1. <span data-ttu-id="e79b3-144">Surface Hub に USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="e79b3-144">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="e79b3-145">Surface Hub で [設定] を **開** き、プロンプトが表示されたら管理者資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="e79b3-145">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="e79b3-146">[セキュリティ回復の**更新&に**  >  **移動します**。</span><span class="sxs-lookup"><span data-stu-id="e79b3-146">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="e79b3-147">**[BitLocker] で**、[保存]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="e79b3-147">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="e79b3-148">BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e79b3-148">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="e79b3-149">詳細については [、「Save your BitLocker key 」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="e79b3-149">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="e79b3-150">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e79b3-150">Learn more</span></span>

- [<span data-ttu-id="e79b3-151">Windows 10 Team 2020 更新プログラムの新機能</span><span class="sxs-lookup"><span data-stu-id="e79b3-151">What's new in Windows 10 Team 2020 Update</span></span>](surface-hub-2020-update-whats-new.md)
- [<span data-ttu-id="e79b3-152">Windows 10 Team のロールアウトに関する更新プログラム</span><span class="sxs-lookup"><span data-stu-id="e79b3-152">Update to the Windows 10 Team rollout</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-february-status/ba-p/2118369)
