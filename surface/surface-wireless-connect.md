---
title: Surface デバイスでの Wi-Fi 接続の最適化
description: このトピックでは、混雑したネットワークWi-Fiモバイル シナリオで Surface デバイスを確実に接続するための推奨される設定について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.audience: itpro
ms.localizationpriority: medium
ms.author: greglin
ms.topic: article
ms.reviewer: tokatz
manager: laurawi
ms.date: 01/15/2021
ms.openlocfilehash: 69ca7bc7383a122dfd4f069135319b92ff7edfb0
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271381"
---
# <span data-ttu-id="c55e4-103">Surface デバイスでの Wi-Fi 接続の最適化</span><span class="sxs-lookup"><span data-stu-id="c55e4-103">Optimize Wi-Fi connectivity for Surface devices</span></span>


<span data-ttu-id="c55e4-104">Surface デバイスは、1 日のバッテリー残量を保つには、パフォーマンスと消費電力のバランスを取るワイヤレス接続設定を実装しています。</span><span class="sxs-lookup"><span data-stu-id="c55e4-104">To stay connected with all-day battery life, Surface devices implement wireless connectivity settings that balance performance and power conservation.</span></span> <span data-ttu-id="c55e4-105">最も要求の厳しいモビリティ シナリオの外部では、ユーザーは、既定のネットワーク アダプターや関連する設定を変更することなく、十分なワイヤレス接続を維持できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-105">Outside of the most demanding mobility scenarios, users can maintain sufficient wireless connectivity without modifying default network adapter or related settings.</span></span> <span data-ttu-id="c55e4-106">このページでは、Surface Pro 7+、Surface Laptop Go、Surface Go 2、Surface Pro X、Surface Laptop 3、Surface Book 3、Surface Pro 7 などの最新の Surface デバイスを使用するモバイル シナリオでのワイヤレス接続に関する重要な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-106">This page highlights key wireless connectivity considerations in mobile scenarios using the latest Surface devices including Surface Pro 7+, Surface Laptop Go, Surface Go 2, Surface Pro X, Surface Laptop 3, Surface Book 3, and Surface Pro 7.</span></span>

## <span data-ttu-id="c55e4-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="c55e4-107">Prerequisites</span></span>

<span data-ttu-id="c55e4-108">このドキュメントでは、主要な機器ベンダーからのベスト プラクティスの推奨事項に従って、802.11n (Wi-Fi 4) 以降をサポートするワイヤレス ネットワークが正常に展開されたことを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="c55e4-108">This document assumes you have successfully deployed a wireless network that supports 802.11n (Wi-Fi 4) or later in accordance with best practice recommendations from leading equipment vendors.</span></span>

## <span data-ttu-id="c55e4-109">最適なローミング機能のためのアクセス ポイントの構成</span><span class="sxs-lookup"><span data-stu-id="c55e4-109">Configuring access points for optimal roaming capabilities</span></span>

<span data-ttu-id="c55e4-110">通常、さまざまな種類のクライアント デバイスからアクセスされるワイヤレス ネットワークを管理している場合は [、「802.11k、802.11v、802.11r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r)での高速ローミング」で説明するように、WLAN のアクセス ポイント (AP) で特定のプロトコルを有効にするようにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c55e4-110">If you’re managing a wireless network that’s typically accessed by many different types of client devices, it’s recommended to enable specific protocols on access points (APs) in your WLAN, as described in [Fast Roaming with 802.11k, 802.11v, and 802.11r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r).</span></span> <span data-ttu-id="c55e4-111">Surface デバイスでは、次のワイヤレス プロトコルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-111">Surface devices can take advantage of the following wireless protocols:</span></span>

- **<span data-ttu-id="c55e4-112">802.11r.</span><span class="sxs-lookup"><span data-stu-id="c55e4-112">802.11r.</span></span>** <span data-ttu-id="c55e4-113">"Fast**BSS Transition"** は、デバイスを動き回る際にデバイスが別の AP にアクセスする前に必要なフレーム数を減らすことで、新しいワイヤレス アクセス ポイントへの接続を加速します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-113">“**Fast BSS Transition”** accelerates connecting to new wireless access points by reducing the number of frames required before your device can access another AP as you move around with your device.</span></span> <span data-ttu-id="c55e4-114">2019 年からリリースされた新しい世代の Surface デバイスでは、エンド ユーザーがデバイスのローミングの積極的な設定にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-114">In the new generation of Surface devices released since 2019, end users may gain access to roaming aggressiveness settings on their device.</span></span> <span data-ttu-id="c55e4-115">既定の設定の変更は推奨されませんが、ユーザーはこの機能を認識し、特定の設定が接続を維持する能力に与える影響を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-115">Although modifying default settings is not recommended, users should be aware of this capability and understand how specific settings can impact their ability to remain connected.</span></span>
- **<span data-ttu-id="c55e4-116">802.11k。</span><span class="sxs-lookup"><span data-stu-id="c55e4-116">802.11k.</span></span>** <span data-ttu-id="c55e4-117">**"近隣レポート" は** 、隣接するアクセス ポイントの現在の状態に関する情報をデバイスに提供します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-117">**“Neighbor Reports”** provides devices with information on current conditions at neighboring access points.</span></span> <span data-ttu-id="c55e4-118">これは、AP 使用率などの信号強度以外の条件を使用して、Surface デバイスが最適な AP を選択するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-118">It can help your Surface device choose the best AP using criteria other than signal strength such as AP utilization.</span></span>

<span data-ttu-id="c55e4-119">特定の Surface デバイスでは、802.11v の "BSS 移行管理フレーム" も使用できます。これは、近くの候補 AP に関する情報を 802.11k と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-119">Specific Surface devices can also use 802.11v “BSS Transition Management Frames,” which functions much like 802.11k in providing information on nearby candidate APs.</span></span> <span data-ttu-id="c55e4-120">これには、Surface Pro 7+、Surface Go、Surface Go 2、Surface Pro 7、Surface Pro X、Surface Laptop 3 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-120">These include Surface Pro 7+, Surface Go, Surface Go 2, Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> 

## <span data-ttu-id="c55e4-121">ユーザー設定の管理</span><span class="sxs-lookup"><span data-stu-id="c55e4-121">Managing user settings</span></span>

<span data-ttu-id="c55e4-122">すべてのアクセス ポイントで 802.11r と 802.11k をサポートする、十分に設計されたネットワークを通じて最適なローミング機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-122">You can achieve optimal roaming capabilities through a well-designed network that supports  802.11r and 802.11k across all access points.</span></span> <span data-ttu-id="c55e4-123">最適なワイヤレス エクスペリエンスをユーザーに提供するようにネットワークが適切に構成されていることを確認する方法は、個々のデバイスでユーザー設定を管理する方法と比較して推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="c55e4-123">Ensuring that your network is properly configured to provide users with the best wireless experience is the recommended approach versus attempting to manage user settings on individual devices.</span></span> 

### <span data-ttu-id="c55e4-124">推奨されるユーザー設定とベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c55e4-124">Recommended user settings and best practices</span></span>

<span data-ttu-id="c55e4-125">状況によっては、Surface デバイスに組み込んだ高度なネットワーク アダプター設定を変更すると、より信頼性の高い接続が容易になります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-125">In certain situations, modifying advanced network adapter settings built into Surface devices may facilitate a more reliable connection.</span></span> <span data-ttu-id="c55e4-126">ただし、アクセス ポイントの問題、ネットワーク設計の欠陥、環境サイトの問題により、ワイヤレス リソースに接続できない方が頻繁に発生する点に気を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-126">Keep in mind however that an inability to connect to wireless resources is more often due to an access point issue, networking design flaw, or environmental site issue.</span></span>

> [!NOTE]
> <span data-ttu-id="c55e4-127">Surface Pro または Surface Go を保持する方法は、信号の強さにも影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-127">How you hold your Surface Pro or Surface Go can also affect signal strength.</span></span> <span data-ttu-id="c55e4-128">帯域幅の損失が発生した場合は、ディスプレイの上部 (Wi-Fi 無線レシーバーがある場所) を保持していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-128">If you’re experiencing a loss of bandwidth, check that you’re not holding the top of the display, where the Wi-Fi radio receiver is located.</span></span> <span data-ttu-id="c55e4-129">ディスプレイの上部を保持してもワイヤレス信号はブロックされませんが、デバイス ドライバーをトリガーして接続を減らす変更を開始できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-129">Although holding the top of the display does not block wireless signals, it can trigger the device driver to initiate changes that reduce connectivity.</span></span>

### <span data-ttu-id="c55e4-130">デュアル帯域幅機能の既定の自動設定を維持する</span><span class="sxs-lookup"><span data-stu-id="c55e4-130">Keep default Auto setting for dual bandwidth capability</span></span>

<span data-ttu-id="c55e4-131">ほとんどの Surface デバイスでは、5 GHz 以上のワイヤレス AP にのみ接続するか、2.4 GHz 以上で接続するか、オペレーティング システムが最適なオプション (既定の自動設定) を選択できるよう、クライアント ネットワーク アダプター設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-131">On most Surface devices, you can configure client network adapter settings to only connect to wireless APs over 5 gigahertz (GHz), only connect over 2.4 GHz, or let the operating system choose the best option (default Auto setting).</span></span>

**<span data-ttu-id="c55e4-132">ネットワーク アダプターの設定にアクセスするには、次の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-132">To access network adapter settings go to:</span></span>**

- <span data-ttu-id="c55e4-133">**Start**  > **コントロール パネル**  > **ネットワークと共有センター**  > **Wi-Fi アダプター**  > **プロパティ**  > **構成**  > **高度です**。</span><span class="sxs-lookup"><span data-stu-id="c55e4-133">**Start** > **Control panel** > **Network and Sharing Center** > **your Wi-Fi adapter** > **Properties** > **Configure** > **Advanced**.</span></span>

![\* wifi-band settings\*](images/wifi-band.png) <br>

<span data-ttu-id="c55e4-135">2.4 GHz には、5 GHz よりもいくつかの利点があります。壁や他の実物を通じてさらに広がり、より容易に侵入します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-135">Keep in mind that 2.4 GHz has some advantages over 5 GHz: It extends further and more easily penetrates through walls or other solid objects.</span></span> <span data-ttu-id="c55e4-136">5 GHz への接続を保証する明確な使用事例がない限り、悪影響を及ぼす可能性を回避するために、Band 設定を既定の状態のままにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c55e4-136">Unless you have a clear use case that warrants connecting to 5 GHz, it’s recommended to leave the Band setting in the default state to avoid possible adverse consequences.</span></span> <span data-ttu-id="c55e4-137">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-137">For example:</span></span>


- <span data-ttu-id="c55e4-138">ホテル、喫茶店、空港で見つかった多くのホットスポットでは、依然として 2.4 GHz しか使用されません。バンドが 5 GHz のみに設定されている場合、デバイスへのアクセスは事実上ブロックされます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-138">Many hotspots found in hotels, coffee shops, and airports still only use 2.4 GHz, effectively blocking access to devices if Band is set to 5 GHz Only.</span></span>
- <span data-ttu-id="c55e4-139">Miracast ワイヤレスディスプレイ接続では、最初のハンドシェイクを 2.4 GHz チャネルで完了する必要があります。デバイスは 5 GHz でのみ接続できません。</span><span class="sxs-lookup"><span data-stu-id="c55e4-139">Since Miracast wireless display connections require the initial handshake to be completed over 2.4 GHz channels, devices won’t be able to connect at 5 GHz Only.</span></span>

> [!NOTE]
> <span data-ttu-id="c55e4-140">既定では、Surface デバイスでは、利用可能な場合は 5 GHz への接続が優先されます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-140">By default Surface devices will prefer connecting to 5 GHz if available.</span></span> <span data-ttu-id="c55e4-141">ただし、低バッテリ状態で電力を維持するために、Surface は最初に 2.4 GHz 接続を探します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-141">However, to preserve power  in a low battery state, Surface will first look for a 2.4 GHz connection.</span></span>

<span data-ttu-id="c55e4-142">必要に応じて、環境に合わせてバンド設定を切り替えできます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-142">You can also toggle the band setting as needed to suit your environment.</span></span> <span data-ttu-id="c55e4-143">たとえば、複数の Wi-Fi ホットスポットを備えた密度の高いアパートメントビルに住んでいるユーザーは、2.4 GHz 経由ですべてのブロードキャストを行うコンシューマー デバイスの存在を示します。Surface デバイスを 5 GHz でのみ接続し、必要に応じて自動に戻すという利点があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-143">For example, users living in high density apartment buildings with multiple Wi-Fi hotspots  —  amid the presence of consumer devices all broadcasting via 2.4 GHz  —  will likely benefit by setting their Surface device to connect on 5 GHz only and then revert to Auto when needed.</span></span>

### <span data-ttu-id="c55e4-144">Intel アダプターを搭載した Surface デバイスでのローミングの積極的な設定</span><span class="sxs-lookup"><span data-stu-id="c55e4-144">Roaming aggressiveness settings on Surface devices with Intel adapters</span></span> 

<span data-ttu-id="c55e4-145">ユーザーは、信号が低下した場合に新しいアクセス ポイントを検索するようにデバイスに求める信号の強さのしきい値を選択する場合があります (ローミングの攻撃)。</span><span class="sxs-lookup"><span data-stu-id="c55e4-145">Users may wish to select a signal strength threshold that prompts the device to search for a new access point when the signal drops (roaming aggressiveness).</span></span> <span data-ttu-id="c55e4-146">既定では、Intel アダプターを搭載した Surface デバイスは、信号強度が **中** 程度 (信号強度 72%) を下回ると、新しいアクセス ポイントへのローミングを試みます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-146">By default, Surface devices with Intel adapters attempt to roam to a new access point if the signal strength drops below **Medium** (72 percent signal strength).</span></span> <span data-ttu-id="c55e4-147">また、組織は、このページで既に説明したように、混雑したネットワーク環境のローミングを容易にするために、複数のネットワーク アクセス ポイントを通じて専用のワイヤレス プロトコルを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-147">Note also that organizations can implement purpose-built wireless protocols across multiple network access points to facilitate roaming congested network environments, as explained earlier on this page.</span></span> 

<span data-ttu-id="c55e4-148">**中**程度を超えるローミングの積極度を増やすと、混雑の大きなオフィスや環境では接続性が向上する可能性があります。一方で、これらの環境の外側をステップ実行すると接続性が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-148">While increasing roaming aggressiveness above **Medium** may yield improved connectivity in highly congested office or residential environments, it can result in degraded connectivity when stepping outside of these environments.</span></span> 

<span data-ttu-id="c55e4-149">電話会議中に音声とビデオの接続を維持しながら環境サイトの検査を実施するなどの特定のモバイル シナリオで接続の問題が発生しない限り、ローミングの積極的な設定を既定の状態のままにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c55e4-149">It’s recommended to leave the roaming aggressiveness setting in the default state unless you’re encountering connectivity issues in specific mobile scenarios such as conducting environmental site inspections while also maintaining voice and video connectivity during a conference meeting.</span></span> <span data-ttu-id="c55e4-150">改善点に気付かない場合は、既定の Medium 状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-150">If you don’t notice any improvement, revert to the default Medium state.</span></span> <span data-ttu-id="c55e4-151">ローミングの積極的性を高める場合は、バッテリーの電力消費も加速します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-151">Note that if you increase roaming aggressiveness, you also accelerate battery power consumption.</span></span> 

**<span data-ttu-id="c55e4-152">Surface でローミングの積極的性を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="c55e4-152">To enable roaming aggressiveness on Surface:</span></span>**

1. <span data-ttu-id="c55e4-153">[デバイス マネージャー**の**  >  **起動] に移動します**。</span><span class="sxs-lookup"><span data-stu-id="c55e4-153">Go to **Start** > **Device Manager**.</span></span>
2. <span data-ttu-id="c55e4-154">[ **ネットワーク アダプター] で** **Intel Wi-Fi 6** を選択し、[プロパティ] を右クリック **します**。</span><span class="sxs-lookup"><span data-stu-id="c55e4-154">Under **Network adapters** select **Intel Wi-Fi 6** and then right click **Properties**.</span></span>
3. <span data-ttu-id="c55e4-155">[詳細設定] **タブを選択** します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-155">Select the **Advanced** tab.</span></span>
4. <span data-ttu-id="c55e4-156">[Roaming **Aggressiveness] を** 選択し、ドロップダウン メニューから目的の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-156">Select **Roaming Aggressiveness** and choose your preferred value from the drop-down menu.</span></span>

![\* ローミングの積極的な設定 - Intel \*](images/wifi-roaming-int.png) <br>

### <span data-ttu-id="c55e4-158">Surface Go と Surface Pro X でのローミングの積極的な設定</span><span class="sxs-lookup"><span data-stu-id="c55e4-158">Roaming aggressiveness settings on Surface Go and Surface Pro X</span></span>

<span data-ttu-id="c55e4-159">Surface Go を使用するフロント ライン ワーカーは、信号強度が低下した場合 (ローミングの攻撃性) が低下した場合に、デバイスに新しいアクセス ポイントの検索を求める信号強度しきい値を選択する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-159">Front-line workers using Surface Go may wish to select a signal strength threshold that prompts the device to search for a new access point when signal strength drops (roaming aggressiveness).</span></span> <span data-ttu-id="c55e4-160">既定では、Surface デバイスは、信号の強さが **中** 程度 (信号強度が 50%) を下回ると、新しいアクセス ポイントへのローミングを試みます。</span><span class="sxs-lookup"><span data-stu-id="c55e4-160">By default, Surface devices attempt to roam to a new access point if the signal strength drops below **Medium** (50 percent signal strength).</span></span> <span data-ttu-id="c55e4-161">ローミングの積極的性を高めるたびに、バッテリーの電力消費を加速する点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c55e4-161">Note that whenever you increase roaming aggressiveness, you accelerate battery power consumption.</span></span>

<span data-ttu-id="c55e4-162">会議中に音声とビデオの接続を維持しながら環境サイトの検査を実行するなどの特定のモバイル シナリオで接続の問題が発生しない限り、ローミングの積極的な設定は既定の状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="c55e4-162">Leave the roaming aggressiveness setting in the default state unless you’re encountering connectivity issues in specific mobile scenarios such as conducting environmental site inspections while also maintaining voice and video connectivity during a conference meeting.</span></span> <span data-ttu-id="c55e4-163">改善点が気付かない場合は、既定の中型の状態に **戻** ります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-163">If you don’t notice any improvement revert to the default **Medium** state.</span></span>

**<span data-ttu-id="c55e4-164">Surface Go でローミングの積極的性を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="c55e4-164">To enable roaming aggressiveness on Surface Go:</span></span>**

1. <span data-ttu-id="c55e4-165">スタート>**コントロール パネルネットワーク**  >  **とインターネット ネットワークと**  >  **共有センターに移動します。**</span><span class="sxs-lookup"><span data-stu-id="c55e4-165">Go to **Start > Control Panel** > **Network and Internet** > **Network and Sharing Center.**</span></span>
2. <span data-ttu-id="c55e4-166">[ **接続] で** **Wi-Fi を選択し** 、[プロパティ] を **選択します。**</span><span class="sxs-lookup"><span data-stu-id="c55e4-166">Under **Connections** select **Wi-Fi** and then select **Properties.**</span></span>
3. <span data-ttu-id="c55e4-167">**[Microsoft ネットワークのクライアント] を選択し、[** 構成] を選択**します。**</span><span class="sxs-lookup"><span data-stu-id="c55e4-167">Select **Client for Microsoft Networks** and then select **Configure**</span></span>
4. <span data-ttu-id="c55e4-168">[Advanced \*\*\*\*  >  **Roaming Aggressiveness] を**選択し、ドロップダウン メニューから目的の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c55e4-168">Select **Advanced** > **Roaming Aggressiveness** and choose your preferred value from the drop-down menu.</span></span>

![\* ローミングの積極的な設定 - QualComm \*](images/wifi-roaming.png) <br>


## <span data-ttu-id="c55e4-170">まとめ</span><span class="sxs-lookup"><span data-stu-id="c55e4-170">Conclusion</span></span>

<span data-ttu-id="c55e4-171">Surface デバイスは、バッテリ残量を維持する必要がある場合と一緒に最適なワイヤレス接続のバランスを取る既定の設定で設計されています。</span><span class="sxs-lookup"><span data-stu-id="c55e4-171">Surface devices are designed with default settings for optimal wireless connectivity balanced alongside the need to preserve battery life.</span></span> <span data-ttu-id="c55e4-172">Surface デバイスで信頼性の高い接続を実現する最も効果的な方法は、802.11r と 802.11k をサポートする、十分に設計されたネットワークを介する方法です。</span><span class="sxs-lookup"><span data-stu-id="c55e4-172">The most effective way of enabling reliable connectivity for Surface devices is through a well-designed network that supports 802.11r and 802.11k.</span></span> <span data-ttu-id="c55e4-173">ユーザーはネットワーク アダプターの設定やローミングの積極的さを調整できますが、特定の環境要因に応じて調整を行い、顕著な改善がない場合は既定の状態に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c55e4-173">Users can adjust network adapter settings or roaming aggressiveness but should only do so in response to specific environmental factors and revert to default state if there’s no noticeable improvement.</span></span>
