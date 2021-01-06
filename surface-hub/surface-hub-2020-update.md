---
title: Windows 10 Team 2020 の更新プログラムをインストールする
description: Surface Hub オペレーティング システムの最新の更新プログラムである Windows 10 Team 2020 Update を取得します。
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
ms.openlocfilehash: b3f1f0884273728abc8b4f6e8662190dacdaf2b2
ms.sourcegitcommit: 8c75e57dc32eaf7c11cb9badea74809fd3877ffc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "11253966"
---
# <span data-ttu-id="509e7-104">Windows 10 Team 2020 の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="509e7-104">Install Windows 10 Team 2020 Update</span></span> 

<span data-ttu-id="509e7-105">Windows **10 バージョン 20H2**に基づく新しい Surface Hub オペレーティング システムである Windows 10 Team 2020 Update が、すべての Surface Hub 2S デバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="509e7-105">The new Surface Hub operating system, **Windows 10 Team 2020 Update**, based on Windows 10 version 20H2, is now available for all Surface Hub 2S devices.</span></span>  

- <span data-ttu-id="509e7-106">See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-update.md)</span><span class="sxs-lookup"><span data-stu-id="509e7-106">See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-update.md)</span></span>

## <span data-ttu-id="509e7-107">[Distribution] (配布)</span><span class="sxs-lookup"><span data-stu-id="509e7-107">Distribution</span></span>

<span data-ttu-id="509e7-108">Windows 2020 Update は、次のいずれかの方法で入手できます。</span><span class="sxs-lookup"><span data-stu-id="509e7-108">You can obtain Windows 2020 Update using one of the following methods:</span></span>

- <span data-ttu-id="509e7-109">**Windows Update for Business**.</span><span class="sxs-lookup"><span data-stu-id="509e7-109">**Windows Update for Business**.</span></span>
- <span data-ttu-id="509e7-110">**ベア メタル回復 (BMR) イメージ**。</span><span class="sxs-lookup"><span data-stu-id="509e7-110">**Bare metal recovery (BMR) image**.</span></span> <span data-ttu-id="509e7-111">デバイスを Azure Active Directory に参加しているお客様、またはデバイスがインターネットから更新プログラムを受信できないお客様に推奨されるオプションです。</span><span class="sxs-lookup"><span data-stu-id="509e7-111">Recommended option for customers who join their devices to Azure Active Directory or don’t allow their devices to receive updates from the internet.</span></span> <span data-ttu-id="509e7-112">始めるには、「Surface の回復 [イメージをダウンロードする」をご覧ください](https://support.microsoft.com/surfacerecoveryimage)。</span><span class="sxs-lookup"><span data-stu-id="509e7-112">To get started, see [Download a recovery image for your Surface](https://support.microsoft.com/surfacerecoveryimage).</span></span>
- **<span data-ttu-id="509e7-113">Windows Update。</span><span class="sxs-lookup"><span data-stu-id="509e7-113">Windows Update.</span></span>** <span data-ttu-id="509e7-114">可用性は、次の表に示す地域/国によって異なります。</span><span class="sxs-lookup"><span data-stu-id="509e7-114">Availability varies by region/country, as noted in the following table:</span></span>

| <span data-ttu-id="509e7-115">フェーズ</span><span class="sxs-lookup"><span data-stu-id="509e7-115">Phase</span></span> | <span data-ttu-id="509e7-116">国/地域</span><span class="sxs-lookup"><span data-stu-id="509e7-116">Country/Region</span></span>                         | <span data-ttu-id="509e7-117">開始</span><span class="sxs-lookup"><span data-stu-id="509e7-117">Starting</span></span>          |
| ----- | -------------------------------------- | ----------------- |
| <span data-ttu-id="509e7-118">1</span><span class="sxs-lookup"><span data-stu-id="509e7-118">1</span></span>     | <span data-ttu-id="509e7-119">NZ、オーストラリア、カナダ、ベルギー、メキシコ</span><span class="sxs-lookup"><span data-stu-id="509e7-119">NZ, Australia, Canada, Belgium, Mexico</span></span> | <span data-ttu-id="509e7-120">2020 年 10 月 27 日</span><span class="sxs-lookup"><span data-stu-id="509e7-120">October 27, 2020</span></span>  |
| <span data-ttu-id="509e7-121">2</span><span class="sxs-lookup"><span data-stu-id="509e7-121">2</span></span>     | <span data-ttu-id="509e7-122">英国、日本、スイス、イタリア</span><span class="sxs-lookup"><span data-stu-id="509e7-122">UK, Japan, Switzerland, Italy</span></span>          | <span data-ttu-id="509e7-123">2020 年 11 月 10 日</span><span class="sxs-lookup"><span data-stu-id="509e7-123">November 10, 2020</span></span> |
| <span data-ttu-id="509e7-124">3</span><span class="sxs-lookup"><span data-stu-id="509e7-124">3</span></span>     | <span data-ttu-id="509e7-125">米国、ドイツ</span><span class="sxs-lookup"><span data-stu-id="509e7-125">US, Germany</span></span>                            | <span data-ttu-id="509e7-126">TBD</span><span class="sxs-lookup"><span data-stu-id="509e7-126">TBD</span></span> |
| <span data-ttu-id="509e7-127">4</span><span class="sxs-lookup"><span data-stu-id="509e7-127">4</span></span>     | <span data-ttu-id="509e7-128">グローバル</span><span class="sxs-lookup"><span data-stu-id="509e7-128">Global</span></span>                                 | <span data-ttu-id="509e7-129">TBD</span><span class="sxs-lookup"><span data-stu-id="509e7-129">TBD</span></span>  |

## <span data-ttu-id="509e7-130">Windows 10 Team Edition バージョン 1703 での Surface Hub のサービス提供</span><span class="sxs-lookup"><span data-stu-id="509e7-130">Servicing Surface Hubs with Windows 10 Team Edition version 1703</span></span> 

<span data-ttu-id="509e7-131">Windows 10 Team Edition バージョン 1703 の完全なサービス サポートは、2021 年 3 月 16 日まで継続する予定です。</span><span class="sxs-lookup"><span data-stu-id="509e7-131">Full servicing support for Windows 10 Team Edition version 1703 is scheduled to continue until March 16, 2021.</span></span>

### <span data-ttu-id="509e7-132">2S デバイス</span><span class="sxs-lookup"><span data-stu-id="509e7-132">2S devices</span></span> 

<span data-ttu-id="509e7-133">すべての地域のお客様は、「Surface Hub 2S のリセットと回復」で説明したように、Windows Update for Business またはベア メタル回復 (BMR) イメージを使用して、引き続き Surface Hub 2S デバイスを [2020](surface-hub-2s-recover-reset.md)Update に更新できます。</span><span class="sxs-lookup"><span data-stu-id="509e7-133">Customers in all regions can continue to update their Surface Hub 2S devices to the 2020 Update using Windows Update for Business or using a bare metal recovery (BMR) image, as explained in [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span>

### <span data-ttu-id="509e7-134">V1 デバイス</span><span class="sxs-lookup"><span data-stu-id="509e7-134">V1 devices</span></span> 

<span data-ttu-id="509e7-135">すべての地域のお客様は、Surface Hub 回復ツールを使って Surface Hub v1 デバイスを 2020 Update に [更新できます](surface-hub-recovery-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="509e7-135">Customers in all regions can now update their Surface Hub v1 devices to the 2020 Update by [using the Surface Hub Recovery Tool](surface-hub-recovery-tool.md).</span></span> <span data-ttu-id="509e7-136">これらのデバイスを Windows 10 Team 2020 Update に更新する他の方法は、間もなく利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="509e7-136">Other methods to update these devices to the Windows 10 Team 2020 Update will soon be available.</span></span> <span data-ttu-id="509e7-137">詳細については [、Surface IT Pro ブログを参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update/ba-p/2000144)。</span><span class="sxs-lookup"><span data-stu-id="509e7-137">To learn more, see [Surface IT Pro Blog](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update/ba-p/2000144).</span></span>
 
## <span data-ttu-id="509e7-138">新機能</span><span class="sxs-lookup"><span data-stu-id="509e7-138">What’s new</span></span>

<span data-ttu-id="509e7-139">Windows 10 Team 2020 Update では、最新の Windows 10 機能と共に、デバイスの展開と管理性が大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="509e7-139">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="509e7-140">詳しくは [、Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="509e7-140">To learn more, see [What's new in Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md).</span></span>
 
## <span data-ttu-id="509e7-141">始める前に</span><span class="sxs-lookup"><span data-stu-id="509e7-141">Before you begin</span></span>

<span data-ttu-id="509e7-142">Windows 10 Team 2020 Update をインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。</span><span class="sxs-lookup"><span data-stu-id="509e7-142">Prior to installing Windows 10 Team 2020 Update, make sure you save the BitLocker key associated with your device.</span></span> 

**<span data-ttu-id="509e7-143">BitLocker キーを手動で保存するには</span><span class="sxs-lookup"><span data-stu-id="509e7-143">To manually save your BitLocker key</span></span>**

1. <span data-ttu-id="509e7-144">Surface Hub に USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="509e7-144">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="509e7-145">Surface Hub で[設定] を **開** き、メッセージが表示されたら管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="509e7-145">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="509e7-146">[更新とセキュリティの**回復&に**  >  **移動します**。</span><span class="sxs-lookup"><span data-stu-id="509e7-146">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="509e7-147">**[BitLocker] で、[** 保存] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="509e7-147">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="509e7-148">BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="509e7-148">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="509e7-149">詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="509e7-149">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

## <span data-ttu-id="509e7-150">詳細情報</span><span class="sxs-lookup"><span data-stu-id="509e7-150">Learn more</span></span>

- [<span data-ttu-id="509e7-151">既知の問題: Windows 10 Team 2020 Update</span><span class="sxs-lookup"><span data-stu-id="509e7-151">Known issues: Windows 10 Team 2020 Update</span></span>](surface-hub-2020-update.md)
- [<span data-ttu-id="509e7-152">Surface Hub Windows 10 Team 2020 Update の重要な更新プログラム</span><span class="sxs-lookup"><span data-stu-id="509e7-152">Important Updates on the Surface Hub Windows 10 Team 2020 Update</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/important-updates-on-the-surface-hub-windows-10-team-2020-update/ba-p/1960897)
