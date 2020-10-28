---
title: Surface デバイスでの Wi-Fi 接続の最適化
description: このトピックでは、混雑したネットワーク環境とモバイルシナリオで、Surface デバイスが確実に接続されるようにするために推奨される Wi-Fi 設定について説明します。
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
ms.date: 10/26/2020
ms.openlocfilehash: d211ceea20b89824d45e433cf9670abe137130a0
ms.sourcegitcommit: 07ac65bf70c8c6efcda28eecc3013983fc386e0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "11136148"
---
# <span data-ttu-id="ed081-103">Surface デバイスでの Wi-Fi 接続の最適化</span><span class="sxs-lookup"><span data-stu-id="ed081-103">Optimize Wi-Fi connectivity for Surface devices</span></span>


<span data-ttu-id="ed081-104">稼働状態を維持するために、Surface デバイスは、パフォーマンスと省電力のバランスを取るワイヤレス接続設定を実装しています。</span><span class="sxs-lookup"><span data-stu-id="ed081-104">To stay connected with all-day battery life, Surface devices implement wireless connectivity settings that balance performance and power conservation.</span></span> <span data-ttu-id="ed081-105">最も要求の多いモバイルシナリオ以外に、ユーザーは、既定のネットワークアダプターや関連設定を変更せずに、十分なワイヤレス接続を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-105">Outside of the most demanding mobility scenarios, users can maintain sufficient wireless connectivity without modifying default network adapter or related settings.</span></span> <span data-ttu-id="ed081-106">このページでは、Surface Pro 7、surface Pro X、surface のノート Pc 3、surface Book 3、Surface Go 2、surface Pc の移動など、最新の Surface デバイスを使った、モバイルシナリオでの主要なワイヤレス接続性に関する考慮事項について取り上げます。</span><span class="sxs-lookup"><span data-stu-id="ed081-106">This page highlights key wireless connectivity considerations in mobile scenarios using the latest Surface devices including Surface Pro 7, Surface Pro X, Surface Laptop 3, Surface Book 3,  Surface Go 2, and Surface Laptop Go.</span></span>  

## <span data-ttu-id="ed081-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="ed081-107">Prerequisites</span></span>

<span data-ttu-id="ed081-108">このドキュメントでは、主要な機器ベンダーからのベストプラクティスに従って、802.11 n (Wi-fi 4) 以降をサポートするワイヤレスネットワークを正常に展開したことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="ed081-108">This document assumes you have successfully deployed a wireless network that supports 802.11n (Wi-Fi 4) or later in accordance with best practice recommendations from leading equipment vendors.</span></span>

## <span data-ttu-id="ed081-109">最適なローミング機能のためのアクセスポイントの構成</span><span class="sxs-lookup"><span data-stu-id="ed081-109">Configuring access points for optimal roaming capabilities</span></span>

<span data-ttu-id="ed081-110">多くの種類のクライアントデバイスによってアクセスされるワイヤレスネットワークを管理する場合は、WLAN のアクセスポイント (APs) で特定のプロトコルを有効にすることをお勧めします。詳細については、「802.11 [k、802.11 v、802.11 r を使用した高速ローミング](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed081-110">If you’re managing a wireless network that’s typically accessed by many different types of client devices, it’s recommended to enable specific protocols on access points (APs) in your WLAN, as described in [Fast Roaming with 802.11k, 802.11v, and 802.11r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r).</span></span> <span data-ttu-id="ed081-111">Surface デバイスは、次のワイヤレスプロトコルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="ed081-111">Surface devices can take advantage of the following wireless protocols:</span></span>

- **<span data-ttu-id="ed081-112">802.11 r。</span><span class="sxs-lookup"><span data-stu-id="ed081-112">802.11r.</span></span>** <span data-ttu-id="ed081-113">"**高速 BSS の切り替え"** を使うと、デバイスで移動するときに、デバイスから別の AP にアクセスする前に必要なフレーム数を減らすことで、新しいワイヤレスアクセスポイントへの接続が高速化されます。</span><span class="sxs-lookup"><span data-stu-id="ed081-113">“**Fast BSS Transition”** accelerates connecting to new wireless access points by reducing the number of frames required before your device can access another AP as you move around with your device.</span></span> <span data-ttu-id="ed081-114">2019以降にリリースされた Surface デバイスの新世代では、エンドユーザーがデバイス上のローミング aggressiveness 設定にアクセスできる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed081-114">In the new generation of Surface devices released since 2019, end users may gain access to roaming aggressiveness settings on their device.</span></span> <span data-ttu-id="ed081-115">既定の設定を変更することはお勧めできませんが、ユーザーはこの機能を認識して、特定の設定が接続を維持する機能にどのように影響するかを理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed081-115">Although modifying default settings is not recommended, users should be aware of this capability and understand how specific settings can impact their ability to remain connected.</span></span>
- **<span data-ttu-id="ed081-116">802.11 k。</span><span class="sxs-lookup"><span data-stu-id="ed081-116">802.11k.</span></span>** <span data-ttu-id="ed081-117">**"近隣レポート"** は、近隣のアクセスポイントで現在の条件に関する情報を提供するデバイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed081-117">**“Neighbor Reports”** provides devices with information on current conditions at neighboring access points.</span></span> <span data-ttu-id="ed081-118">これにより、Surface デバイスは、AP の使用率などの信号強度以外の条件を使用して最適な AP を選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-118">It can help your Surface device choose the best AP using criteria other than signal strength such as AP utilization.</span></span>

<span data-ttu-id="ed081-119">特定の Surface デバイスでは、802.11 v の "BSS Transition 管理フレーム" を使うこともできます。802.11 の候補としては、802.11 の候補 Ap に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ed081-119">Specific Surface devices can also use 802.11v “BSS Transition Management Frames,” which functions much like 802.11k in providing information on nearby candidate APs.</span></span> <span data-ttu-id="ed081-120">これには、Surface Go、Surface Pro 7、Surface Pro X、Surface Pc 3 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed081-120">These include Surface Go, Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> 

## <span data-ttu-id="ed081-121">ユーザー設定を管理する</span><span class="sxs-lookup"><span data-stu-id="ed081-121">Managing user settings</span></span>

<span data-ttu-id="ed081-122">すべてのアクセスポイントで 802.11 r と 802.11 k をサポートする、適切に設計されたネットワークを通じて最適なローミング機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="ed081-122">You can achieve optimal roaming capabilities through a well-designed network that supports  802.11r and 802.11k across all access points.</span></span> <span data-ttu-id="ed081-123">最適なワイヤレスエクスペリエンスをユーザーに提供するようにネットワークが適切に構成されていることを確認するには、個々のデバイスでユーザー設定を管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed081-123">Ensuring that your network is properly configured to provide users with the best wireless experience is the recommended approach versus attempting to manage user settings on individual devices.</span></span> 

### <span data-ttu-id="ed081-124">推奨されるユーザー設定とベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="ed081-124">Recommended user settings and best practices</span></span>

<span data-ttu-id="ed081-125">一部の状況では、Surface デバイスに組み込まれている advanced network adapter の設定を変更すると、より信頼性の高い接続を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-125">In certain situations, modifying advanced network adapter settings built into Surface devices may facilitate a more reliable connection.</span></span> <span data-ttu-id="ed081-126">ただし、ワイヤレスリソースに接続できない場合は、アクセスポイントの問題、ネットワーク設計の問題、または環境サイトの問題が原因である場合が多いことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ed081-126">Keep in mind however that an inability to connect to wireless resources is more often due to an access point issue, networking design flaw, or environmental site issue.</span></span>

> [!NOTE]
> <span data-ttu-id="ed081-127">Surface Pro または Surface Go の保持方法は、信号強度にも影響します。</span><span class="sxs-lookup"><span data-stu-id="ed081-127">How you hold your Surface Pro or Surface Go can also affect signal strength.</span></span> <span data-ttu-id="ed081-128">帯域幅が失われている場合は、Wi-Fi 無線受信機が配置されている画面の上部が表示されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed081-128">If you’re experiencing a loss of bandwidth, check that you’re not holding the top of the display, where the Wi-Fi radio receiver is located.</span></span> <span data-ttu-id="ed081-129">ディスプレイの一番上にマウスを置いても、ワイヤレス信号はブロックされませんが、デバイスドライバーをトリガーして、接続を減らすための変更を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-129">Although holding the top of the display does not block wireless signals, it can trigger the device driver to initiate changes that reduce connectivity.</span></span>

### <span data-ttu-id="ed081-130">既定の自動設定を保持してデュアル帯域幅機能を使用する</span><span class="sxs-lookup"><span data-stu-id="ed081-130">Keep default Auto setting for dual bandwidth capability</span></span>

<span data-ttu-id="ed081-131">ほとんどの Surface デバイスでは、5ギガヘルツ (GHz) 以上のワイヤレス Ap にのみ接続するようにクライアントのネットワークアダプターの設定を構成できます。また、2.4 GHz 以上で接続するか、オペレーティングシステムで最適なオプション (既定の自動設定) を選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-131">On most Surface devices, you can configure client network adapter settings to only connect to wireless APs over 5 gigahertz (GHz), only connect over 2.4 GHz, or let the operating system choose the best option (default Auto setting).</span></span>

**<span data-ttu-id="ed081-132">ネットワークアダプターの設定にアクセスするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ed081-132">To access network adapter settings go to:</span></span>**

- <span data-ttu-id="ed081-133">**開始**  > **コントロールパネル**  > **ネットワークと共有センター**  > **Wi-Fi アダプター**  > **プロパティ**  > **構成**  > **[詳細設定**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="ed081-133">**Start** > **Control panel** > **Network and Sharing Center** > **your Wi-Fi adapter** > **Properties** > **Configure** > **Advanced**.</span></span>

![\* wifi-バンド設定 \*](images/wifi-band.png) <br>

<span data-ttu-id="ed081-135">2.4 GHz には 5 GHz 以上の利点があることに注意してください。これにより、壁やその他のソリッドオブジェクトをさらに penetrates することができます。</span><span class="sxs-lookup"><span data-stu-id="ed081-135">Keep in mind that 2.4 GHz has some advantages over 5 GHz: It extends further and more easily penetrates through walls or other solid objects.</span></span> <span data-ttu-id="ed081-136">5 GHz への接続を想定している明確なユースケースを使用していない場合は、悪影響を及ぼす可能性を回避するためにバンド設定を既定の状態のままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed081-136">Unless you have a clear use case that warrants connecting to 5 GHz, it’s recommended to leave the Band setting in the default state to avoid possible adverse consequences.</span></span> <span data-ttu-id="ed081-137">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="ed081-137">For example:</span></span>


- <span data-ttu-id="ed081-138">ホテル、コーヒーショップ、空港の多くのホットスポットは、依然として 2.4 GHz のみを使用しており、バンドが 5 GHz のみに設定されている場合は、デバイスへのアクセスを効果的にブロックします。</span><span class="sxs-lookup"><span data-stu-id="ed081-138">Many hotspots found in hotels, coffee shops, and airports still only use 2.4 GHz, effectively blocking access to devices if Band is set to 5 GHz Only.</span></span>
- <span data-ttu-id="ed081-139">Miracast ワイヤレスディスプレイ接続では、最初のハンドシェイクを 2.4 GHz チャネル経由で完了する必要があるため、デバイスは 5 GHz のみで接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="ed081-139">Since Miracast wireless display connections require the initial handshake to be completed over 2.4 GHz channels, devices won’t be able to connect at 5 GHz Only.</span></span>

> [!NOTE]
> <span data-ttu-id="ed081-140">既定では、Surface デバイスは、可能であれば 5 GHz に接続することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed081-140">By default Surface devices will prefer connecting to 5 GHz if available.</span></span> <span data-ttu-id="ed081-141">ただし、バッテリー残量を節約するために、Surface はまず 2.4 GHz 接続を探します。</span><span class="sxs-lookup"><span data-stu-id="ed081-141">However, to preserve power  in a low battery state, Surface will first look for a 2.4 GHz connection.</span></span>

<span data-ttu-id="ed081-142">必要に応じて、環境に合わせてバンド設定を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="ed081-142">You can also toggle the band setting as needed to suit your environment.</span></span> <span data-ttu-id="ed081-143">たとえば、複数の Wi-Fi ホットスポットを備えた高密度のアパートメント建物 (2.4 GHz 経由でブロードキャストしているコンシューマーデバイスの存在を含む) のユーザーは、Surface デバイスを 5 GHz のみに接続し、必要に応じて自動に戻すことでメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="ed081-143">For example, users living in high density apartment buildings with multiple Wi-Fi hotspots  —  amid the presence of consumer devices all broadcasting via 2.4 GHz  —  will likely benefit by setting their Surface device to connect on 5 GHz only and then revert to Auto when needed.</span></span>

### <span data-ttu-id="ed081-144">Intel アダプターを搭載した Surface デバイスでのローミング aggressiveness の設定</span><span class="sxs-lookup"><span data-stu-id="ed081-144">Roaming aggressiveness settings on Surface devices with Intel adapters</span></span> 

<span data-ttu-id="ed081-145">ユーザーはシグナル強度のしきい値を選択することができます。これにより、デバイスは、シグナルのドロップ時に新しいアクセスポイントを検索するよう求められます (ローミング aggressiveness)。</span><span class="sxs-lookup"><span data-stu-id="ed081-145">Users may wish to select a signal strength threshold that prompts the device to search for a new access point when the signal drops (roaming aggressiveness).</span></span> <span data-ttu-id="ed081-146">既定では、Intel アダプターを使っている Surface デバイスは、シグナルの強さが **Medium** (72 パーセントの信号強度) を下回ると、新しいアクセスポイントにローミングしようとします。</span><span class="sxs-lookup"><span data-stu-id="ed081-146">By default, Surface devices with Intel adapters attempt to roam to a new access point if the signal strength drops below **Medium** (72 percent signal strength).</span></span> <span data-ttu-id="ed081-147">また、このページで既に説明したように、組織が複数のネットワークアクセスポイントを使用して、ローミングの輻輳ネットワーク環境を容易にするために、目的に応じたワイヤレスプロトコルを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed081-147">Note also that organizations can implement purpose-built wireless protocols across multiple network access points to facilitate roaming congested network environments, as explained earlier on this page.</span></span> 

<span data-ttu-id="ed081-148">**メディア**の上にあるローミング aggressiveness の増加により、高輻輳の office や個人環境での接続性が向上することがあります。そのため、これらの環境以外でステップ実行すると、接続性が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed081-148">While increasing roaming aggressiveness above **Medium** may yield improved connectivity in highly congested office or residential environments, it can result in degraded connectivity when stepping outside of these environments.</span></span> 

<span data-ttu-id="ed081-149">特定のモバイルシナリオで接続の問題が発生している場合 (たとえば、電話会議中に音声とビデオの接続性を維持するなど)、接続の問題が発生した場合を除き、[ローミング aggressiveness] 設定は既定の状態のままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed081-149">It’s recommended to leave the roaming aggressiveness setting in the default state unless you’re encountering connectivity issues in specific mobile scenarios such as conducting environmental site inspections while also maintaining voice and video connectivity during a conference meeting.</span></span> <span data-ttu-id="ed081-150">改善されていない場合は、既定のメディアの状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="ed081-150">If you don’t notice any improvement, revert to the default Medium state.</span></span> <span data-ttu-id="ed081-151">ローミング aggressiveness を向上させると、バッテリ消費も加速します。</span><span class="sxs-lookup"><span data-stu-id="ed081-151">Note that if you increase roaming aggressiveness, you also accelerate battery power consumption.</span></span> 

**<span data-ttu-id="ed081-152">Surface でローミング aggressiveness を有効にするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ed081-152">To enable roaming aggressiveness on Surface:</span></span>**

1. <span data-ttu-id="ed081-153">「 **Start**  >  **デバイスマネージャー**の起動」を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed081-153">Go to **Start** > **Device Manager**.</span></span>
2. <span data-ttu-id="ed081-154">[ **ネットワークアダプター** ] で [ **Intel Wi-Fi 6** ] を選び、右クリックして [ **プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed081-154">Under **Network adapters** select **Intel Wi-Fi 6** and then right click **Properties**.</span></span>
3. <span data-ttu-id="ed081-155">[ **詳細設定** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="ed081-155">Select the **Advanced** tab.</span></span>
4. <span data-ttu-id="ed081-156">[ **ローミング Aggressiveness** ] を選択し、ドロップダウンメニューから希望の値を選びます。</span><span class="sxs-lookup"><span data-stu-id="ed081-156">Select **Roaming Aggressiveness** and choose your preferred value from the drop-down menu.</span></span>

![\* ローミング aggressiveness 設定-Intel \*](images/wifi-roaming-int.png) <br>

### <span data-ttu-id="ed081-158">Surface Go および Surface Pro X のローミング aggressiveness 設定</span><span class="sxs-lookup"><span data-stu-id="ed081-158">Roaming aggressiveness settings on Surface Go and Surface Pro X</span></span>

<span data-ttu-id="ed081-159">Surface Go を使っているフロントラインワーカーは、シグナルの強さがなくなったときに、デバイスが新しいアクセスポイントを検索することを要求するシグナル強度のしきい値を選ぶことができます (ローミング aggressiveness)。</span><span class="sxs-lookup"><span data-stu-id="ed081-159">Front-line workers using Surface Go may wish to select a signal strength threshold that prompts the device to search for a new access point when signal strength drops (roaming aggressiveness).</span></span> <span data-ttu-id="ed081-160">既定では、シグナルの強さが **Medium** (50 パーセントの信号強度) を下回ると、Surface デバイスは新しいアクセスポイントへのローミングを試みます。</span><span class="sxs-lookup"><span data-stu-id="ed081-160">By default, Surface devices attempt to roam to a new access point if the signal strength drops below **Medium** (50 percent signal strength).</span></span> <span data-ttu-id="ed081-161">ローミング aggressiveness を増加させるたびに、バッテリー消費量を加速することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ed081-161">Note that whenever you increase roaming aggressiveness, you accelerate battery power consumption.</span></span>

<span data-ttu-id="ed081-162">環境設定のサイト検査などの特定のモバイルシナリオで接続の問題が発生した場合、または会議中に音声とビデオの接続性を維持している場合を除き、[ローミングの aggressiveness] 設定は既定の状態のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="ed081-162">Leave the roaming aggressiveness setting in the default state unless you’re encountering connectivity issues in specific mobile scenarios such as conducting environmental site inspections while also maintaining voice and video connectivity during a conference meeting.</span></span> <span data-ttu-id="ed081-163">改善された機能がない場合は、既定の **メディア** の状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="ed081-163">If you don’t notice any improvement revert to the default **Medium** state.</span></span>

**<span data-ttu-id="ed081-164">Surface Go でローミング aggressiveness を有効にするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ed081-164">To enable roaming aggressiveness on Surface Go:</span></span>**

1. <span data-ttu-id="ed081-165">[**スタート > コントロールパネル**の [  >  **ネットワークとインターネット**ネットワークと共有センター] に移動し  >  **ます。**</span><span class="sxs-lookup"><span data-stu-id="ed081-165">Go to **Start > Control Panel** > **Network and Internet** > **Network and Sharing Center.**</span></span>
2. <span data-ttu-id="ed081-166">[ **接続** ] で [ **wi-fi** ] を選択し、[プロパティ] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="ed081-166">Under **Connections** select **Wi-Fi** and then select **Properties.**</span></span>
3. <span data-ttu-id="ed081-167">[ **Microsoft ネットワーククライアント**] を選択し、[**構成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed081-167">Select **Client for Microsoft Networks** and then select **Configure**</span></span>
4. <span data-ttu-id="ed081-168">[ **Advanced**  >  **ローミング Aggressiveness** ] を選択し、ドロップダウンメニューから希望の値を選びます。</span><span class="sxs-lookup"><span data-stu-id="ed081-168">Select **Advanced** > **Roaming Aggressiveness** and choose your preferred value from the drop-down menu.</span></span>

![\* ローミング aggressiveness 設定-た qualcomm \*](images/wifi-roaming.png) <br>


## <span data-ttu-id="ed081-170">まとめ</span><span class="sxs-lookup"><span data-stu-id="ed081-170">Conclusion</span></span>

<span data-ttu-id="ed081-171">Surface デバイスは、バッテリ寿命の維持と共に、最適なワイヤレス接続を実現するための既定の設定で設計されています。</span><span class="sxs-lookup"><span data-stu-id="ed081-171">Surface devices are designed with default settings for optimal wireless connectivity balanced alongside the need to preserve battery life.</span></span> <span data-ttu-id="ed081-172">Surface デバイスで信頼性の高い接続を実現する最も効果的な方法は、802.11 r と 802.11 k をサポートする、適切に設計されたネットワークです。</span><span class="sxs-lookup"><span data-stu-id="ed081-172">The most effective way of enabling reliable connectivity for Surface devices is through a well-designed network that supports 802.11r and 802.11k.</span></span> <span data-ttu-id="ed081-173">ユーザーは、ネットワークアダプターの設定またはローミングの aggressiveness を調整できますが、顕著な改善がない場合にのみ、特定の環境要因に応じて既定の状態に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed081-173">Users can adjust network adapter settings or roaming aggressiveness but should only do so in response to specific environmental factors and revert to default state if there’s no noticeable improvement.</span></span>
