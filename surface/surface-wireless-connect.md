---
title: Surface デバイスでの Wi-Fi 接続の最適化
description: このトピックでは、ネットワークの輻輳環境とモバイルシナリオで、Surface デバイスが確実に接続されるようにするために推奨される Wi-fi 設定について説明します。
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
ms.openlocfilehash: 2fb64f86e3c1da0e4ba3834877548898e98fd893
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835549"
---
# <span data-ttu-id="2db49-103">Surface デバイスでの Wi-Fi 接続の最適化</span><span class="sxs-lookup"><span data-stu-id="2db49-103">Optimize Wi-Fi connectivity for Surface devices</span></span>


<span data-ttu-id="2db49-104">稼働状態を維持するために、Surface デバイスは、パフォーマンスと省電力のバランスを取るワイヤレス接続設定を実装しています。</span><span class="sxs-lookup"><span data-stu-id="2db49-104">To stay connected with all-day battery life, Surface devices implement wireless connectivity settings that balance performance and power conservation.</span></span> <span data-ttu-id="2db49-105">最も要求の多いモバイルシナリオ以外に、ユーザーは、既定のネットワークアダプターや関連設定を変更せずに、十分なワイヤレス接続を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-105">Outside of the most demanding mobility scenarios, users can maintain sufficient wireless connectivity without modifying default network adapter or related settings.</span></span> 

<span data-ttu-id="2db49-106">輻輳ネットワーク環境では、組織は、複数のネットワークアクセスポイント間で専用のワイヤレスプロトコルを実装することで、ローミングを容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-106">In congested network environments, organizations can implement purpose-built wireless protocols across multiple network access points to facilitate roaming.</span></span> <span data-ttu-id="2db49-107">このページでは、Surface Pro 3 以降、Surface Book、Surface Pc、Surface Go を利用しているモバイルシナリオの主要なワイヤレス接続の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="2db49-107">This page highlights key wireless connectivity considerations in mobile scenarios utilizing Surface Pro 3 and later, Surface Book, Surface Laptop, and Surface Go.</span></span>

## <span data-ttu-id="2db49-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="2db49-108">Prerequisites</span></span>

<span data-ttu-id="2db49-109">このドキュメントでは、主要な機器ベンダーからのベストプラクティスに従って、802.11 n (Wi-fi 4) 以降をサポートするワイヤレスネットワークを正常に展開したことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2db49-109">This document assumes you have successfully deployed a wireless network that supports 802.11n (Wi-Fi 4) or later in accordance with best practice recommendations from leading equipment vendors.</span></span>

## <span data-ttu-id="2db49-110">最適なローミング機能のためのアクセスポイントの構成</span><span class="sxs-lookup"><span data-stu-id="2db49-110">Configuring access points for optimal roaming capabilities</span></span>

<span data-ttu-id="2db49-111">多くの種類のクライアントデバイスによってアクセスされるワイヤレスネットワークを管理する場合は、WLAN のアクセスポイント (APs) で特定のプロトコルを有効にすることをお勧めします。詳細については、「802.11 [k、802.11 v、802.11 r を使用した高速ローミング](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2db49-111">If you’re managing a wireless network that’s typically accessed by many different types of client devices, it’s recommended to enable specific protocols on access points (APs) in your WLAN, as described in [Fast Roaming with 802.11k, 802.11v, and 802.11r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r).</span></span> <span data-ttu-id="2db49-112">Surface デバイスは、次のワイヤレスプロトコルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="2db49-112">Surface devices can take advantage of the following wireless protocols:</span></span>

- **<span data-ttu-id="2db49-113">802.11 r。</span><span class="sxs-lookup"><span data-stu-id="2db49-113">802.11r.</span></span>** <span data-ttu-id="2db49-114">"**高速 BSS の切り替え"** を使うと、デバイスで移動するときに、デバイスから別の AP にアクセスする前に必要なフレーム数を減らすことで、新しいワイヤレスアクセスポイントへの接続が高速化されます。</span><span class="sxs-lookup"><span data-stu-id="2db49-114">“**Fast BSS Transition”** accelerates connecting to new wireless access points by reducing the number of frames required before your device can access another AP as you move around with your device.</span></span>
- **<span data-ttu-id="2db49-115">802.11 k。</span><span class="sxs-lookup"><span data-stu-id="2db49-115">802.11k.</span></span>** <span data-ttu-id="2db49-116">**"近隣レポート"** は、近隣のアクセスポイントで現在の条件に関する情報を提供するデバイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2db49-116">**“Neighbor Reports”** provides devices with information on current conditions at neighboring access points.</span></span> <span data-ttu-id="2db49-117">これにより、Surface デバイスは、AP の使用率などの信号強度以外の条件を使用して最適な AP を選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-117">It can help your Surface device choose the best AP using criteria other than signal strength such as AP utilization.</span></span>

<span data-ttu-id="2db49-118">特定の Surface デバイスでは、802.11 v の "BSS Transition 管理フレーム" を使うこともできます。802.11 の候補としては、802.11 の候補 Ap に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2db49-118">Specific Surface devices can also use 802.11v “BSS Transition Management Frames,” which functions much like 802.11k in providing information on nearby candidate APs.</span></span> <span data-ttu-id="2db49-119">これには、Surface Go、Surface Pro 7、Surface Pro X、Surface Pc 3 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2db49-119">These include Surface Go, Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> 

## <span data-ttu-id="2db49-120">ユーザー設定を管理する</span><span class="sxs-lookup"><span data-stu-id="2db49-120">Managing user settings</span></span>

<span data-ttu-id="2db49-121">すべてのアクセスポイントで 802.11 r と 802.11 k をサポートする、適切に設計されたネットワークを通じて最適なローミング機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="2db49-121">You can achieve optimal roaming capabilities through a well-designed network that supports  802.11r and 802.11k across all access points.</span></span> <span data-ttu-id="2db49-122">最適なワイヤレスエクスペリエンスをユーザーに提供するようにネットワークが適切に構成されていることを確認するには、個々のデバイスでユーザー設定を管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2db49-122">Ensuring that your network is properly configured to provide users with the best wireless experience is the recommended approach versus attempting to manage user settings on individual devices.</span></span> <span data-ttu-id="2db49-123">さらに、多くの企業環境では、デバイスユーザーは、明示的な権限またはローカルの管理者権限がなくても、アドバンストネットワークアダプターの設定にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="2db49-123">Moreover, in many corporate environments Surface device users won’t be able to access advanced network adapter settings without explicit permissions or local admin rights.</span></span> <span data-ttu-id="2db49-124">その他の管理されていないネットワークでは、特定の設定が接続を維持する機能にどのように影響するかを把握することにより、ユーザーはメリットを享受できます</span><span class="sxs-lookup"><span data-stu-id="2db49-124">In other lightly managed networks, users can benefit by knowing how specific settings can impact their ability to remain connected.</span></span>

### <span data-ttu-id="2db49-125">推奨されるユーザー設定とベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="2db49-125">Recommended user settings and best practices</span></span>

<span data-ttu-id="2db49-126">一部の状況では、Surface デバイスに組み込まれている advanced network adapter の設定を変更すると、より信頼性の高い接続を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-126">In certain situations, modifying advanced network adapter settings built into Surface devices may facilitate a more reliable connection.</span></span> <span data-ttu-id="2db49-127">ただし、ワイヤレスリソースに接続できない場合は、アクセスポイントの問題、ネットワーク設計の問題、または環境サイトの問題が原因である場合が多いことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2db49-127">Keep in mind however that an inability to connect to wireless resources is more often due to an access point issue, networking design flaw, or environmental site issue.</span></span>

> [!NOTE]
> <span data-ttu-id="2db49-128">Surface Pro または Surface Go の保持方法は、信号強度にも影響します。</span><span class="sxs-lookup"><span data-stu-id="2db49-128">How you hold your Surface Pro or Surface Go can also affect signal strength.</span></span> <span data-ttu-id="2db49-129">帯域幅が失われている場合は、Wi-fi 無線受信機が配置されている画面の上部が表示されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2db49-129">If you’re experiencing a loss of bandwidth, check that you’re not holding the top of the display, where the Wi-Fi radio receiver is located.</span></span> <span data-ttu-id="2db49-130">ディスプレイの一番上にマウスを置いても、ワイヤレス信号はブロックされませんが、デバイスドライバーをトリガーして、接続を減らすための変更を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-130">Although holding the top of the display does not block wireless signals, it can trigger the device driver to initiate changes that reduce connectivity.</span></span>

### <span data-ttu-id="2db49-131">既定の自動設定を保持してデュアル帯域幅機能を使用する</span><span class="sxs-lookup"><span data-stu-id="2db49-131">Keep default Auto setting for dual bandwidth capability</span></span>
<span data-ttu-id="2db49-132">ほとんどの Surface デバイスでは、5ギガヘルツ (GHz) 以上のワイヤレス Ap にのみ接続するようにクライアントのネットワークアダプターの設定を構成できます。また、2.4 GHz 以上で接続するか、オペレーティングシステムで最適なオプション (既定の自動設定) を選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-132">On most Surface devices, you can configure client network adapter settings to only connect to wireless APs over 5 gigahertz (GHz), only connect over 2.4 GHz, or let the operating system choose the best option (default Auto setting).</span></span>

**<span data-ttu-id="2db49-133">ネットワークアダプターの設定にアクセスするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2db49-133">To access network adapter settings go to:</span></span>**

- <span data-ttu-id="2db49-134">**開始**  > **コントロールパネル**  > **ネットワークと共有センター**  > **wi-fi アダプター**  > **プロパティ**  > **構成**  > **[詳細設定**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2db49-134">**Start** > **Control panel** > **Network and Sharing Center** > **your Wi-Fi adapter** > **Properties** > **Configure** > **Advanced**.</span></span>

![\* wifi-バンド設定 \*](images/wifi-band.png) <br>

<span data-ttu-id="2db49-136">2.4 GHz には 5 GHz 以上の利点があることに注意してください。これにより、壁やその他のソリッドオブジェクトをさらに penetrates することができます。</span><span class="sxs-lookup"><span data-stu-id="2db49-136">Keep in mind that 2.4 GHz has some advantages over 5 GHz: It extends further and more easily penetrates through walls or other solid objects.</span></span> <span data-ttu-id="2db49-137">5 GHz への接続を想定している明確なユースケースを使用していない場合は、悪影響を及ぼす可能性を回避するためにバンド設定を既定の状態のままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2db49-137">Unless you have a clear use case that warrants connecting to 5 GHz, it’s recommended to leave the Band setting in the default state to avoid possible adverse consequences.</span></span> <span data-ttu-id="2db49-138">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2db49-138">For example:</span></span>


- <span data-ttu-id="2db49-139">ホテル、コーヒーショップ、空港の多くのホットスポットは、依然として 2.4 GHz のみを使用しており、バンドが 5 GHz のみに設定されている場合は、デバイスへのアクセスを効果的にブロックします。</span><span class="sxs-lookup"><span data-stu-id="2db49-139">Many hotspots found in hotels, coffee shops, and airports still only use 2.4 GHz, effectively blocking access to devices if Band is set to 5 GHz Only.</span></span>
- <span data-ttu-id="2db49-140">Miracast ワイヤレスディスプレイ接続では、最初のハンドシェイクを 2.4 GHz チャネル経由で完了する必要があるため、デバイスは 5 GHz のみで接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="2db49-140">Since Miracast wireless display connections require the initial handshake to be completed over 2.4 GHz channels, devices won’t be able to connect at 5 GHz Only.</span></span>

> [!NOTE]
> <span data-ttu-id="2db49-141">既定では、Surface デバイスは、可能であれば 5 GHz に接続することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2db49-141">By default Surface devices will prefer connecting to 5 GHz if available.</span></span> <span data-ttu-id="2db49-142">ただし、バッテリー残量を節約するために、Surface はまず 2.4 GHz 接続を探します。</span><span class="sxs-lookup"><span data-stu-id="2db49-142">However, to preserve power  in a low battery state, Surface will first look for a 2.4 GHz connection.</span></span>

<span data-ttu-id="2db49-143">必要に応じて、環境に合わせてバンド設定を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="2db49-143">You can also toggle the band setting as needed to suit your environment.</span></span> <span data-ttu-id="2db49-144">たとえば、複数の Wi-fi ホットスポットを備えた高密度のアパートメント建物に居住しているユーザー (たとえば、2.4 GHz 経由でのすべてのブロードキャスティング) では、Surface デバイスを 5 GHz のみに接続し、必要に応じて自動に戻すことでメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="2db49-144">For example, users living in high density apartment buildings with multiple Wi-Fi hotspots  —  amid the presence of consumer devices all broadcasting via 2.4 GHz  —  will likely benefit by setting their Surface device to connect on 5 GHz only and then revert to Auto when needed.</span></span>

### <span data-ttu-id="2db49-145">Surface Go のローミング aggressiveness 設定</span><span class="sxs-lookup"><span data-stu-id="2db49-145">Roaming aggressiveness settings on Surface Go</span></span>

<span data-ttu-id="2db49-146">Surface Go を使っているフロントラインワーカーは、シグナルの強さがなくなったときに、デバイスが新しいアクセスポイントを検索することを要求するシグナル強度のしきい値を選ぶことができます (ローミング aggressiveness)。</span><span class="sxs-lookup"><span data-stu-id="2db49-146">Front-line workers using Surface Go may wish to select a signal strength threshold that prompts the device to search for a new access point when signal strength drops (roaming aggressiveness).</span></span> <span data-ttu-id="2db49-147">既定では、シグナルの強さが**Medium** (50 パーセントの信号強度) を下回ると、Surface デバイスは新しいアクセスポイントへのローミングを試みます。</span><span class="sxs-lookup"><span data-stu-id="2db49-147">By default, Surface devices attempt to roam to a new access point if the signal strength drops below **Medium** (50 percent signal strength).</span></span> <span data-ttu-id="2db49-148">ローミング aggressiveness を増加させるたびに、バッテリー消費量を加速することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2db49-148">Note that whenever you increase roaming aggressiveness, you accelerate battery power consumption.</span></span>

<span data-ttu-id="2db49-149">環境設定のサイト検査などの特定のモバイルシナリオで接続の問題が発生した場合、または会議中に音声とビデオの接続性を維持している場合を除き、[ローミングの aggressiveness] 設定は既定の状態のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="2db49-149">Leave the roaming aggressiveness setting in the default state unless you’re encountering connectivity issues in specific mobile scenarios such as conducting environmental site inspections while also maintaining voice and video connectivity during a conference meeting.</span></span> <span data-ttu-id="2db49-150">改善された機能がない場合は、既定の**メディア**の状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="2db49-150">If you don’t notice any improvement revert to the default **Medium** state.</span></span>

**<span data-ttu-id="2db49-151">Surface Go でローミング aggressiveness を有効にするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2db49-151">To enable roaming aggressiveness on Surface Go:</span></span>**

1. <span data-ttu-id="2db49-152">[**スタート > コントロールパネル**の [  >  **ネットワークとインターネット**ネットワークと共有センター] に移動し  >  **ます。**</span><span class="sxs-lookup"><span data-stu-id="2db49-152">Go to **Start > Control Panel** > **Network and Internet** > **Network and Sharing Center.**</span></span>
2. <span data-ttu-id="2db49-153">[**接続**] で [ **wi-fi** ] を選択し、[プロパティ] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="2db49-153">Under **Connections** select **Wi-Fi** and then select **Properties.**</span></span>
3. <span data-ttu-id="2db49-154">[ **Microsoft ネットワーククライアント**] を選択し、[**構成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2db49-154">Select **Client for Microsoft Networks** and then select **Configure**</span></span>
4. <span data-ttu-id="2db49-155">[ **Advanced**  >  **ローミング Aggressiveness** ] を選択し、ドロップダウンメニューから希望の値を選びます。</span><span class="sxs-lookup"><span data-stu-id="2db49-155">Select **Advanced** > **Roaming Aggressiveness** and choose your preferred value from the drop-down menu.</span></span>

![\* ローミング aggressiveness の設定 \*](images/wifi-roaming.png) <br>

## <span data-ttu-id="2db49-157">まとめ</span><span class="sxs-lookup"><span data-stu-id="2db49-157">Conclusion</span></span>

<span data-ttu-id="2db49-158">Surface デバイスは、バッテリ寿命の維持と共に、最適なワイヤレス接続を実現するための既定の設定で設計されています。</span><span class="sxs-lookup"><span data-stu-id="2db49-158">Surface devices are designed with default settings for optimal wireless connectivity balanced alongside the need to preserve battery life.</span></span> <span data-ttu-id="2db49-159">Surface デバイスで信頼性の高い接続を実現する最も効果的な方法は、802.11 r と 802.11 k をサポートする、適切に設計されたネットワークです。</span><span class="sxs-lookup"><span data-stu-id="2db49-159">The most effective way of enabling reliable connectivity for Surface devices is through a well-designed network that supports 802.11r and 802.11k.</span></span> <span data-ttu-id="2db49-160">ユーザーは、ネットワークアダプターの設定またはローミングの aggressiveness を調整できますが、顕著な改善がない場合にのみ、特定の環境要因に応じて既定の状態に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2db49-160">Users can adjust network adapter settings or roaming aggressiveness but should only do so in response to specific environmental factors and revert to default state if there’s no noticeable improvement.</span></span>
