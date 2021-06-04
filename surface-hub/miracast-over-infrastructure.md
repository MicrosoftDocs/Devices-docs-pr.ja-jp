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
# インフラストラクチャ経由の Miracast

Windows 10 Version 1703 では、Microsoft はダイレクト ワイヤレス リンク経由ではなく、ローカル ネットワーク経由で Miracast ストリームを送信できるように機能を拡張しました。 この機能は [Miracast over Infrastructure Connection Establishment Protocol (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx) に基づいています。

Miracast over Infrastructure は多くのメリットを提供します。

- Windows では、このパスでのビデオ ストリームの送信が適用可能であることを自動的に検出します。
- Windows では、イーサネット ネットワークまたはセキュリティで保護された Wi-Fi ネットワークを介して接続されている場合にのみ、このルートを選択します。
- ユーザーは、Miracast レシーバーに接続する方法を変更する必要はありません。 標準の Miracast 接続の場合と同じ UX を使用します。
- 現在のワイヤレス ドライバーまたは PC のハードウェアを変更する必要はありません。
- Miracast over Wi-Fi Direct 用に最適化されていない以前のワイヤレス ハードウェアで正常に動作します。
- 接続にかかる時間を短縮し、非常に安定してストリームを提供する既存の接続を活用します。


##  <a name="how-it-works"></a>動作のしくみ

ユーザーは、以前と同じように、Wi-fi アダプターを介して Miracast レシーバーに接続しようとします。 Miracast レシーバーの一覧が作成されると、Windows 10 はレシーバーがインフラストラクチャ経由での接続をサポートできるかどうかを識別します。 ユーザーが Miracast レシーバーを選択すると、Windows 10 は標準的な DNS、およびマルチキャスト DNS (mDNS) によってデバイスのホスト名を解決しようとします。 名前が DNS のいずれかの方法で解決できない場合、Windows 10 は、標準的な Wi-Fi Direct 接続を使用した Miracast セッションの確立にフォールバックします。

> [!NOTE]
> 接続ネゴシエーションの順序について詳しくは、「[インフラストラクチャ接続確立プロトコル (ms-dtc)](https://msdn.microsoft.com/library/mt796768.aspx) 」をご覧ください。




##  <a name="enabling-miracast-over-infrastructure-"></a>Miracast over Infrastructure の有効化 

Windows 10 Version 1703 に更新済みの Surface Hub やその他の Windows 10 デバイスがある場合、自動的にこの新しい機能が含まれています。 お客様の環境内で最大限に活用するには、展開環境で次の条件が満たされていることを確認する必要があります。

- Surface Hub やデバイス (Windows PC またはスマートフォン) では、Windows 10 Version 1703 が実行されている必要があります。
- [TCP port: **7250**] を開きます。
- Surface Hub や Windows PC は、Miracast over Infrastructure *レシーバー*として使用できます。 Windows PC やスマートフォンは、Miracast over Infrastructure *ソース*として使用できます。
    - Miracast レシーバーとして、Surface Hub やデバイスは、イーサネットまたはセキュリティで保護された Wi-Fi 接続 (WPA2-PSK と WPA2-Enterprise セキュリティのいずれかを使用して) で企業ネットワークに接続されている必要があります。 Surface Hub またはデバイスが開いている Wi-fi 接続に接続されている場合、インフラストラクチャ経由で Miracast が無効になります。
    - Miracast ソースとして、Windows PC またはスマートフォンはイーサネットまたはセキュリティで保護された Wi‑Fi 接続で同じ企業ネットワークに接続されている必要があります。
- Surface Hub またはデバイスの DNS Hostname (デバイス名) は、DNS サーバー経由で解決できる必要があります。 これを実現するには、Surface Hub が動的 DNS によって自動的に登録することを許可するか、Surface Hub のホスト名の A または AAAA レコードを手動で作成します。 
- Windows 10 PC はイーサネットまたはセキュリティで保護された Wi‑Fi 接続で同じ企業ネットワークに接続されている必要があります。 
-   Windows 10 Pc では、**この PC 機能へのプロジェクション**は、システム設定で有効にしておく必要があります。また、wi-fi アダプターでのみ実行される証拠開示要求に応答するには、デバイスで wi-fi インターフェイスが有効になっている必要があります。


Miracast over Infrastructure は標準の Miracast の代わりにではないことに注意する必要があります。 代わりに、この機能は補完的であり、企業ネットワークに接続しているユーザーにメリットをもたらします。 特定の場所でゲストである場合や、企業ネットワークへのアクセス権がない場合は、引き続き Wi-Fi Direct の接続方法を使用して接続します。

[SurfaceHub 構成サービス プロバイダー (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) の **InBoxApps/WirelessProjection/PinRequired** 設定は、Miracast over Infrastructure では必要ありません。 Miracast over Infrastructure は両方のデバイスが同じ企業ネットワークに接続されている場合のみ動作するためです。 これにより、以前にはなかったセキュリティの制限が Miracast から削除されます。 (以前に使用していた場合) 引き続きこの設定を使用することをお勧めします。インフラストラクチャ接続が機能しない場合、Miracast は通常の Miracast にフォールバックするためです。 

##  <a name="faq"></a>FAQ
**インフラストラクチャで Miracast を使用するために Wi-fi がまだ必要なのはなぜですか?**<br>
Miracast レシーバーを特定する証拠開示要求は、Wi-fi アダプター経由でのみ実行できます。 受信者が識別されると、Windows 10 はネットワークへの接続を試みることができます。
