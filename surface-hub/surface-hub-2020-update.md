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
ms.openlocfilehash: 043c7ed49dafab7e0f3d042f5b98d527ffe0610f
ms.sourcegitcommit: 6252903b28f0c410065eb2515c746f5e9920c652
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "11237217"
---
# <span data-ttu-id="98426-104">Windows 10 Team 2020 の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="98426-104">Install Windows 10 Team 2020 Update</span></span> 

<span data-ttu-id="98426-105">Windows **10 バージョン 20H2**に基づく新しい Surface Hub オペレーティング システムである Windows 10 Team 2020 Update が、すべての Surface Hub 2S デバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="98426-105">The new Surface Hub operating system, **Windows 10 Team 2020 Update**, based on Windows 10 version 20H2, is now available for all Surface Hub 2S devices.</span></span>  

- <span data-ttu-id="98426-106">See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-update.md)</span><span class="sxs-lookup"><span data-stu-id="98426-106">See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-update.md)</span></span>

## <span data-ttu-id="98426-107">[Distribution] (配布)</span><span class="sxs-lookup"><span data-stu-id="98426-107">Distribution</span></span>

<span data-ttu-id="98426-108">Windows 2020 Update は、次のいずれかの方法で入手できます。</span><span class="sxs-lookup"><span data-stu-id="98426-108">You can obtain Windows 2020 Update using one of the following methods:</span></span>

- <span data-ttu-id="98426-109">**Windows Update for Business**.</span><span class="sxs-lookup"><span data-stu-id="98426-109">**Windows Update for Business**.</span></span>
- <span data-ttu-id="98426-110">**ベア メタル回復 (BMR) イメージ**。</span><span class="sxs-lookup"><span data-stu-id="98426-110">**Bare metal recovery (BMR) image**.</span></span> <span data-ttu-id="98426-111">デバイスを Azure Active Directory に参加しているお客様、またはデバイスがインターネットから更新プログラムを受信できないお客様に推奨されるオプションです。</span><span class="sxs-lookup"><span data-stu-id="98426-111">Recommended option for customers who join their devices to Azure Active Directory or don’t allow their devices to receive updates from the internet.</span></span> <span data-ttu-id="98426-112">開始するには、「Surface の回復 [イメージをダウンロードする」を参照してください](https://support.microsoft.com/surfacerecoveryimage)。</span><span class="sxs-lookup"><span data-stu-id="98426-112">To get started, see [Download a recovery image for your Surface](https://support.microsoft.com/surfacerecoveryimage).</span></span>
- **<span data-ttu-id="98426-113">Windows Update。</span><span class="sxs-lookup"><span data-stu-id="98426-113">Windows Update.</span></span>** <span data-ttu-id="98426-114">可用性は、次の表に示す地域/国によって異なります。</span><span class="sxs-lookup"><span data-stu-id="98426-114">Availability varies by region/country, as noted in the following table:</span></span>

| <span data-ttu-id="98426-115">フェーズ</span><span class="sxs-lookup"><span data-stu-id="98426-115">Phase</span></span> | <span data-ttu-id="98426-116">国/地域</span><span class="sxs-lookup"><span data-stu-id="98426-116">Country/Region</span></span>                         | <span data-ttu-id="98426-117">開始</span><span class="sxs-lookup"><span data-stu-id="98426-117">Starting</span></span>          |
| ----- | -------------------------------------- | ----------------- |
| <span data-ttu-id="98426-118">1</span><span class="sxs-lookup"><span data-stu-id="98426-118">1</span></span>     | <span data-ttu-id="98426-119">NZ、オーストラリア、カナダ、ベルギー、メキシコ</span><span class="sxs-lookup"><span data-stu-id="98426-119">NZ, Australia, Canada, Belgium, Mexico</span></span> | <span data-ttu-id="98426-120">2020 年 10 月 27 日</span><span class="sxs-lookup"><span data-stu-id="98426-120">October 27, 2020</span></span>  |
| <span data-ttu-id="98426-121">2</span><span class="sxs-lookup"><span data-stu-id="98426-121">2</span></span>     | <span data-ttu-id="98426-122">英国、日本、スイス、イタリア</span><span class="sxs-lookup"><span data-stu-id="98426-122">UK, Japan, Switzerland, Italy</span></span>          | <span data-ttu-id="98426-123">2020 年 11 月 10 日</span><span class="sxs-lookup"><span data-stu-id="98426-123">November 10, 2020</span></span> |
| <span data-ttu-id="98426-124">3</span><span class="sxs-lookup"><span data-stu-id="98426-124">3</span></span>     | <span data-ttu-id="98426-125">米国、ドイツ</span><span class="sxs-lookup"><span data-stu-id="98426-125">US, Germany</span></span>                            | <span data-ttu-id="98426-126">TBD</span><span class="sxs-lookup"><span data-stu-id="98426-126">TBD</span></span> |
| <span data-ttu-id="98426-127">4</span><span class="sxs-lookup"><span data-stu-id="98426-127">4</span></span>     | <span data-ttu-id="98426-128">グローバル</span><span class="sxs-lookup"><span data-stu-id="98426-128">Global</span></span>                                 | <span data-ttu-id="98426-129">TBD</span><span class="sxs-lookup"><span data-stu-id="98426-129">TBD</span></span>  |

## <span data-ttu-id="98426-130">Windows 10 Team Edition v1703 による Surface Hub 2S のサービス</span><span class="sxs-lookup"><span data-stu-id="98426-130">Servicing Surface Hub 2S with Windows 10 Team Edition v1703</span></span> 

<span data-ttu-id="98426-131">すべての地域のお客様は、「Surface Hub 2S のリセットと回復」で説明したように、引き続き Windows Update for Business を使用するか、ベア メタル回復 (BMR) イメージを使用して Surface [Hub 2S](surface-hub-2s-recover-reset.md)デバイスを更新できます。</span><span class="sxs-lookup"><span data-stu-id="98426-131">Customers in all regions can continue to update their Surface Hub 2S devices using Windows Update for Business or using a bare metal recovery (BMR) image, as explained in [Reset and recovery for Surface Hub 2S](surface-hub-2s-recover-reset.md).</span></span> <span data-ttu-id="98426-132">Windows 10 Team Edition バージョン 1703 の完全なサービス サポートは、2021 年 3 月 16 日まで継続する予定です。</span><span class="sxs-lookup"><span data-stu-id="98426-132">Full servicing support for Windows 10 Team Edition version 1703 is scheduled to continue until March 16, 2021.</span></span>


## <span data-ttu-id="98426-133">V1 デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="98426-133">V1 device support</span></span> 

<span data-ttu-id="98426-134">Surface Hub 2S デバイス用に最初にリリースされた Windows Windows 10 Team 2020 Update は、間もなく Surface Hub v1 デバイスで利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="98426-134">Initially released for Surface Hub 2S devices, Windows Windows 10 Team 2020 Update will soon be available for Surface Hub v1 devices.</span></span> <span data-ttu-id="98426-135">詳細については [、Surface IT Pro ブログを参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-available-october-27/ba-p/1810739)。</span><span class="sxs-lookup"><span data-stu-id="98426-135">To learn more, see [Surface IT Pro Blog](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-available-october-27/ba-p/1810739).</span></span>
 
## <span data-ttu-id="98426-136">新機能</span><span class="sxs-lookup"><span data-stu-id="98426-136">What’s new</span></span>

<span data-ttu-id="98426-137">Windows 10 Team 2020 Update では、最新の Windows 10 機能と共に、デバイスの展開と管理性が大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="98426-137">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="98426-138">詳しくは [、Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="98426-138">To learn more, see [What's new in Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md).</span></span>
 
## <span data-ttu-id="98426-139">始める前に</span><span class="sxs-lookup"><span data-stu-id="98426-139">Before you begin</span></span>

<span data-ttu-id="98426-140">Windows 10 Team 2020 更新プログラムをインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。</span><span class="sxs-lookup"><span data-stu-id="98426-140">Prior to installing Windows 10 team 2020 update, make sure you save the BitLocker key associated with your device.</span></span> 

**<span data-ttu-id="98426-141">BitLocker キーを手動で保存するには</span><span class="sxs-lookup"><span data-stu-id="98426-141">To manually save your BitLocker key</span></span>**

1. <span data-ttu-id="98426-142">Surface Hub に USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="98426-142">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="98426-143">Surface Hub で[設定] を **開** き、メッセージが表示されたら管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="98426-143">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="98426-144">[更新とセキュリティ**の回復&に**  >  **移動します**。</span><span class="sxs-lookup"><span data-stu-id="98426-144">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="98426-145">**[BitLocker] で、[** 保存] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="98426-145">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="98426-146">BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="98426-146">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="98426-147">詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="98426-147">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

## <span data-ttu-id="98426-148">詳細情報</span><span class="sxs-lookup"><span data-stu-id="98426-148">Learn more</span></span>

- [<span data-ttu-id="98426-149">既知の問題: Windows 10 Team 2020 Update</span><span class="sxs-lookup"><span data-stu-id="98426-149">Known issues: Windows 10 Team 2020 Update</span></span>](surface-hub-2020-update.md)
- [<span data-ttu-id="98426-150">Surface Hub Windows 10 Team 2020 Update の重要な更新プログラム</span><span class="sxs-lookup"><span data-stu-id="98426-150">Important Updates on the Surface Hub Windows 10 Team 2020 Update</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/important-updates-on-the-surface-hub-windows-10-team-2020-update/ba-p/1960897)
