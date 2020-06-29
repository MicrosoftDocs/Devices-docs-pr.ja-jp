---
title: 既存のワイヤレス ネットワークまたは LAN での Miracast
description: Windows 10 では、ローカル ネットワーク経由で Miracast ストリームを送信することができます。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/24/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d63b3de0f76cb70fe86fff246d82cbe166278461
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836977"
---
# <span data-ttu-id="dd459-103">インフラストラクチャ経由の Miracast</span><span class="sxs-lookup"><span data-stu-id="dd459-103">Miracast over infrastructure</span></span>

<span data-ttu-id="dd459-104">Windows 10 Version 1703 では、Microsoft はダイレクト ワイヤレス リンク経由ではなく、ローカル ネットワーク経由で Miracast ストリームを送信できるように機能を拡張しました。</span><span class="sxs-lookup"><span data-stu-id="dd459-104">In the Windows 10, version 1703, Microsoft has extended the ability to send a Miracast stream over a local network rather than over a direct wireless link.</span></span> <span data-ttu-id="dd459-105">この機能は [Miracast over Infrastructure Connection Establishment Protocol (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dd459-105">This functionality is based on the [Miracast over Infrastructure Connection Establishment Protocol (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx).</span></span>

<span data-ttu-id="dd459-106">Miracast over Infrastructure は多くのメリットを提供します。</span><span class="sxs-lookup"><span data-stu-id="dd459-106">Miracast over Infrastructure offers a number of benefits:</span></span>

- <span data-ttu-id="dd459-107">Windows では、このパスでのビデオ ストリームの送信が適用可能であることを自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="dd459-107">Windows automatically detects when sending the video stream over this path is applicable.</span></span>
- <span data-ttu-id="dd459-108">Windows では、イーサネット ネットワークまたはセキュリティで保護された Wi-Fi ネットワークを介して接続されている場合にのみ、このルートを選択します。</span><span class="sxs-lookup"><span data-stu-id="dd459-108">Windows will only choose this route if the connection is over Ethernet or a secure Wi-Fi network.</span></span>
- <span data-ttu-id="dd459-109">ユーザーは、Miracast レシーバーに接続する方法を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dd459-109">Users do not have to change how they connect to a Miracast receiver.</span></span> <span data-ttu-id="dd459-110">標準の Miracast 接続の場合と同じ UX を使用します。</span><span class="sxs-lookup"><span data-stu-id="dd459-110">They use the same UX as for standard Miracast connections.</span></span>
- <span data-ttu-id="dd459-111">現在のワイヤレス ドライバーまたは PC のハードウェアを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dd459-111">No changes to current wireless drivers or PC hardware are required.</span></span>
- <span data-ttu-id="dd459-112">Miracast over Wi-Fi Direct 用に最適化されていない以前のワイヤレス ハードウェアで正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="dd459-112">It works well with older wireless hardware that is not optimized for Miracast over Wi-Fi Direct.</span></span>
- <span data-ttu-id="dd459-113">接続にかかる時間を短縮し、非常に安定してストリームを提供する既存の接続を活用します。</span><span class="sxs-lookup"><span data-stu-id="dd459-113">It leverages an existing connection which both reduces the time to connect and provides a very stable stream.</span></span>


## <span data-ttu-id="dd459-114">動作のしくみ</span><span class="sxs-lookup"><span data-stu-id="dd459-114">How it works</span></span>

<span data-ttu-id="dd459-115">ユーザーは、以前と同じように、Wi-fi アダプターを介して Miracast レシーバーに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="dd459-115">Users attempt to connect to a Miracast receiver through their Wi-Fi adapter as they did previously.</span></span> <span data-ttu-id="dd459-116">Miracast レシーバーの一覧が作成されると、Windows 10 はレシーバーがインフラストラクチャ経由での接続をサポートできるかどうかを識別します。</span><span class="sxs-lookup"><span data-stu-id="dd459-116">When the list of Miracast receivers is populated, Windows 10 will identify that the receiver is capable of supporting a connection over the infrastructure.</span></span> <span data-ttu-id="dd459-117">ユーザーが Miracast レシーバーを選択すると、Windows 10 は標準的な DNS、およびマルチキャスト DNS (mDNS) によってデバイスのホスト名を解決しようとします。</span><span class="sxs-lookup"><span data-stu-id="dd459-117">When the user selects a Miracast receiver, Windows 10 will attempt to resolve the device's hostname via standard DNS, as well as via multicast DNS (mDNS).</span></span> <span data-ttu-id="dd459-118">名前が DNS のいずれかの方法で解決できない場合、Windows 10 は、標準的な Wi-Fi Direct 接続を使用した Miracast セッションの確立にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="dd459-118">If the name is not resolvable via either DNS method, Windows 10 will fall back to establishing the Miracast session using the standard Wi-Fi direct connection.</span></span>

> [!NOTE]
> <span data-ttu-id="dd459-119">接続ネゴシエーションの順序について詳しくは、「[インフラストラクチャ接続確立プロトコル (ms-dtc)](https://msdn.microsoft.com/library/mt796768.aspx) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd459-119">For more information on the connection negotiation sequence, see [Miracast over Infrastructure Connection Establishment Protocol (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx)</span></span>




## <span data-ttu-id="dd459-120">Miracast over Infrastructure の有効化</span><span class="sxs-lookup"><span data-stu-id="dd459-120">Enabling Miracast over Infrastructure</span></span> 

<span data-ttu-id="dd459-121">Windows 10 Version 1703 に更新済みの Surface Hub やその他の Windows 10 デバイスがある場合、自動的にこの新しい機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dd459-121">If you have a Surface Hub or other Windows 10 device that has been updated to Windows 10, version 1703, then you automatically have this new feature.</span></span> <span data-ttu-id="dd459-122">お客様の環境内で最大限に活用するには、展開環境で次の条件が満たされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-122">To take advantage of it in your environment, you need to ensure the following is true within your deployment:</span></span>

- <span data-ttu-id="dd459-123">Surface Hub やデバイス (Windows PC またはスマートフォン) では、Windows 10 Version 1703 が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-123">The Surface Hub or device (Windows PC or phone) needs to be running Windows 10, version 1703.</span></span>
- <span data-ttu-id="dd459-124">[TCP port: **7250**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="dd459-124">Open TCP port: **7250**.</span></span>
- <span data-ttu-id="dd459-125">Surface Hub や Windows PC は、Miracast over Infrastructure *レシーバー*として使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd459-125">A Surface Hub or Windows PC can act as a Miracast over Infrastructure *receiver*.</span></span> <span data-ttu-id="dd459-126">Windows PC やスマートフォンは、Miracast over Infrastructure *ソース*として使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd459-126">A Windows PC or phone can act as a Miracast over Infrastructure *source*.</span></span>
    - <span data-ttu-id="dd459-127">Miracast レシーバーとして、Surface Hub やデバイスは、イーサネットまたはセキュリティで保護された Wi-Fi 接続 (WPA2-PSK と WPA2-Enterprise セキュリティのいずれかを使用して) で企業ネットワークに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-127">As a Miracast receiver, the Surface Hub or device must be connected to your enterprise network via either Ethernet or a secure Wi-Fi connection (e.g. using either WPA2-PSK or WPA2-Enterprise security).</span></span> <span data-ttu-id="dd459-128">Surface Hub またはデバイスが開いている Wi-fi 接続に接続されている場合、インフラストラクチャ経由で Miracast が無効になります。</span><span class="sxs-lookup"><span data-stu-id="dd459-128">If the Surface Hub or device is connected to an open Wi-Fi connection, Miracast over Infrastructure will disable itself.</span></span>
    - <span data-ttu-id="dd459-129">Miracast ソースとして、Windows PC またはスマートフォンはイーサネットまたはセキュリティで保護された Wi‑Fi 接続で同じ企業ネットワークに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-129">As a Miracast source, the Windows PC or phone must be connected to the same enterprise network via Ethernet or a secure Wi-Fi connection.</span></span>
- <span data-ttu-id="dd459-130">Surface Hub またはデバイスの DNS Hostname (デバイス名) は、DNS サーバー経由で解決できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-130">The DNS Hostname (device name) of the Surface Hub or device needs to be resolvable via your DNS servers.</span></span> <span data-ttu-id="dd459-131">これを実現するには、Surface Hub が動的 DNS によって自動的に登録することを許可するか、Surface Hub のホスト名の A または AAAA レコードを手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="dd459-131">You can achieve this by either allowing your Surface Hub to register automatically via Dynamic DNS, or by manually creating an A or AAAA record for the Surface Hub's hostname.</span></span> 
- <span data-ttu-id="dd459-132">Windows 10 PC はイーサネットまたはセキュリティで保護された Wi‑Fi 接続で同じ企業ネットワークに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-132">Windows 10 PCs must be connected to the same enterprise network via Ethernet or a secure Wi-Fi connection.</span></span> 
-   <span data-ttu-id="dd459-133">Windows 10 Pc では、**この PC 機能へのプロジェクション**は、システム設定で有効にしておく必要があります。また、wi-fi アダプターでのみ実行される証拠開示要求に応答するには、デバイスで wi-fi インターフェイスが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-133">On Windows 10 PCs, the **Projecting to this PC** feature must be enabled in System Settings, and the device must have a Wi-Fi interface enabled in order to respond to discovery requests that only occur through the Wi-Fi adapter.</span></span>


<span data-ttu-id="dd459-134">Miracast over Infrastructure は標準の Miracast の代わりにではないことに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd459-134">It is important to note that Miracast over Infrastructure is not a replacement for standard Miracast.</span></span> <span data-ttu-id="dd459-135">代わりに、この機能は補完的であり、企業ネットワークに接続しているユーザーにメリットをもたらします。</span><span class="sxs-lookup"><span data-stu-id="dd459-135">Instead, the functionality is complementary, and provides an advantage to users who are part of the enterprise network.</span></span> <span data-ttu-id="dd459-136">特定の場所でゲストである場合や、企業ネットワークへのアクセス権がない場合は、引き続き Wi-Fi Direct の接続方法を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="dd459-136">Users who are guests to a particular location and don’t have access to the enterprise network will continue to connect using the Wi-Fi Direct connection method.</span></span>

<span data-ttu-id="dd459-137">[SurfaceHub 構成サービス プロバイダー (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) の **InBoxApps/WirelessProjection/PinRequired** 設定は、Miracast over Infrastructure では必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dd459-137">The **InBoxApps/WirelessProjection/PinRequired** setting in the [SurfaceHub configuration service provider (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) is not required for Miracast over Infrastructure.</span></span> <span data-ttu-id="dd459-138">Miracast over Infrastructure は両方のデバイスが同じ企業ネットワークに接続されている場合のみ動作するためです。</span><span class="sxs-lookup"><span data-stu-id="dd459-138">This is because Miracast over Infrastructure only works when both devices are connected to the same enterprise network.</span></span> <span data-ttu-id="dd459-139">これにより、以前にはなかったセキュリティの制限が Miracast から削除されます。</span><span class="sxs-lookup"><span data-stu-id="dd459-139">This removes the security restriction that was previously missing from Miracast.</span></span> <span data-ttu-id="dd459-140">(以前に使用していた場合) 引き続きこの設定を使用することをお勧めします。インフラストラクチャ接続が機能しない場合、Miracast は通常の Miracast にフォールバックするためです。</span><span class="sxs-lookup"><span data-stu-id="dd459-140">We recommend that you continue using this setting (if you used it previously) as Miracast will fall back to regular Miracast if the infrastructure connection does not work.</span></span> 

## <span data-ttu-id="dd459-141">FAQ</span><span class="sxs-lookup"><span data-stu-id="dd459-141">FAQ</span></span>
**<span data-ttu-id="dd459-142">インフラストラクチャで Miracast を使用するために Wi-fi がまだ必要なのはなぜですか?</span><span class="sxs-lookup"><span data-stu-id="dd459-142">Why do I still need Wi-Fi to use Miracast over infrastructure?</span></span>**<br>
<span data-ttu-id="dd459-143">Miracast レシーバーを特定する証拠開示要求は、Wi-fi アダプター経由でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="dd459-143">Discovery requests to identify Miracast receivers can only occur through the Wi-Fi adapter.</span></span> <span data-ttu-id="dd459-144">受信者が識別されると、Windows 10 はネットワークへの接続を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="dd459-144">Once the receivers have been identified, Windows 10 can then attempt the connection to the network.</span></span>
