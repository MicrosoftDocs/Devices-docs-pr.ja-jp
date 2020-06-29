---
title: Surface Hub への他のデバイスの接続と表示
description: Surface Hub に他のデバイスを接続して、コンテンツを表示できます。
ms.assetid: 8BB80FA3-D364-4A90-B72B-65F0F0FC1F0D
ms.reviewer: ''
manager: laurawi
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2d8d814d5e33a878fab066321a0d7800ae5104c0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836702"
---
# Surface Hub への他のデバイスの接続と表示


Microsoft Surface Hub に他のデバイスを接続して、コンテンツを表示できます。 このトピックでは、ワイヤード (有線) 接続によって利用できるゲスト モード、代替 PC モード、ビデオ出力機能について説明し、[Bluetooth](#bluetooth-accessories) を使って Surface Hub に接続できるアクセサリも示します。

>[!NOTE]
>Surface Hub は、新しい接続が行われるか、既存の接続が中断されるか、または Connect アプリが閉じられるまで、選択したビデオ入力を使います。

## 推奨される方法

外部のデバイスとディスプレイを Surface Hub 接続する場合、複数のオプションを利用できます。 使用する方法はシナリオとニーズによって異なります。 

| 目的の操作: | 使用する方法: |
| --- | --- |
| Surface Hub の画面を別のデバイスにミラーリングする。 | [ビデオ出力](#video-out) |
| 別のデバイスの画面を Surface Hub の画面に表示し、そのデバイスのコンテンツと、組み込みの Surface Hub エクスペリエンスの両方を操作する。 | [ゲスト モード](#guest-mode) |
| 外部の Windows 10 PC を Surface Hub の動力にして、Surface Hub の内蔵コンピューターをオフにする。 ペンやタッチに加えて、カメラ、マイク、スピーカーなどの周辺機器は外部 PC に送る。 | [代替 PC モード](#replacement-pc-mode) |


## ゲスト モード


ゲスト モードでは、ワイヤード (有線) 接続を使用することで、ユーザーのデバイスのコンテンツを Surface Hub に表示できます。 ソース デバイスが Windows ベースの場合は、そのデバイスで touchback と inkback を使うこともできます。 Surface Hub の内部 PC は、接続されたデバイスからビデオとオーディオを受取り、Surface Hub に表示します。 Surface Hub が高帯域幅デジタルコンテンツ保護 (HDCP) 信号を検出した場合、ソースは黒色の画像として表示されます。 HDCP 要件に違反することなくコンテンツを表示するには、Surface Hub の右側にあるキーパッドを使用して外部ソースを直接選択します。

>[!NOTE]
>HDCP ソースが接続されている場合、サイド キーパッドを使用して、ソースの入力を変更します。

### ポート

ゲスト モードには、以下の Surface Hub のポートを使用します。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>インターフェイス</th>
<th>種類</th>
<th>説明</th>
<th>機能</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ディスプレイ ポート 1.1a</p></td>
<td><p>ビデオ入力</p></td>
<td><p>ゲスト入力 #1</p></td>
<td><ul>
<li><p>ゲスト入力 #2 とゲスト入力 #3 を使用したゲスト入力の同時表示 (一方はフル解像度、もう一方はサムネイル) のサポート</p></li>
<li><p>バイパス モードでの HDCP 準拠</p></li>
<li><p>touchback に対応</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>HDMI 1.4</p></td>
<td><p>ビデオ入力</p></td>
<td><p>ゲスト入力 #2</p></td>
<td><ul>
<li><p>ゲスト入力 #1 とゲスト入力 #3 を使用したゲスト入力の同時表示 (一方はフル解像度、もう一方はサムネイル) のサポート</p></li>
<li><p>バイパス モードでの HDCP 準拠</p></li>
<li><p>touchback に対応</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>VGA</p></td>
<td><p>ビデオ入力</p></td>
<td><p>ゲスト入力 #3</p></td>
<td><ul>
<li><p>ゲスト入力 #1 とゲスト入力 #2 を使用したゲスト入力の同時表示 (一方はフル解像度、もう一方はサムネイル) のサポート</p></li>
<li><p>バイパス モードでの HDCP 準拠</p></li>
<li><p>touchback に対応</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>3.5 mm ジャック</p></td>
<td><p>オーディオ入力</p></td>
<td><p>アナログ オーディオ入力</p></td>
<td><ul>
<li><p>通常は VGA ビデオ入力による、Surface Hub PC への取り込み</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB 2.0 タイプ B</p></td>
<td><p>USB 出力</p></td>
<td><p>touchback</p></td>
<td><ul>
<li><p>HID 入力デバイス (マウス、タッチ、キーボード、スタイラスなど) を利用してゲスト PC を制御できます。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### ポートの場所

以下に、ゲスト モードに使用する 55 インチと 84 インチの Surface Hub のポート接続を示します。

![55 インチの Surface Hub のゲスト ポートを示す画像。](images/sh-55-guest-ports.png)

55 インチの Surface Hub のワイヤード (有線) 接続

![84 インチの Surface Hub のゲスト ポートを示す画像。](images/sh-84-guest-ports.png)

84 インチの Surface Hub のワイヤード (有線) 接続

### ポートの列挙

ワイヤード (有線) 接続 USB ポートを使用して Surface Hub にゲスト コンピューターが接続されると、さまざまな USB デバイスが検出および設定されます。 以下の周辺機器は、touchback と inkback に対応しています。 これらの周辺機器は、デバイス マネージャーで表示できます。 一部のデバイスについては、デバイス マネージャーに名前が重複して表示されます。

**ヒューマン インターフェイス デバイス**

-   HID 準拠コンシューマー制御デバイス

-   HID 準拠ペン

-   HID 準拠ペン (重複する項目)

-   HID 準拠ペン (重複する項目)

-   HID 準拠タッチ スクリーン

-   USB 入力デバイス

-   USB入力デバイス (重複する項目)

**キーボード**

-   標準 PS/2 キーボード

**マウスとそのほかのポインティング デバイス**

-   HID 準拠マウス

**ユニバーサル シリアル バス コントローラー**

-   汎用 USB ハブ

-   USB 複合デバイス

### ゲスト モードの接続

どのビデオ ケーブルを使うかは、ソース入力で利用可能な規格によって決まります。 Surface Hub には、DisplayPort、HDMI、および VGA の 3 種類のビデオ入力があります。 利用可能な解像度については、次の表をご覧ください。

<table style="width:100%;">
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th>信号の種類</th>
<th>解像度</th>
<th>フレーム レート</th>
<th>HDMI - RGB</th>
<th>DisplayPort</th>
<th>VGA</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC</p></td>
<td><p>640 x 480</p></td>
<td><p>59.94/60</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
</tr>
<tr class="even">
<td><p>PC</p></td>
<td><p>720 x 480</p></td>
<td><p>59.94/60</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>PC</p></td>
<td><p>1024 x 768</p></td>
<td><p>60</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
</tr>
<tr class="even">
<td><p>HDTV</p></td>
<td><p>720p</p></td>
<td><p>59.94/60</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
</tr>
<tr class="odd">
<td><p>HDTV</p></td>
<td><p>1080p</p></td>
<td><p>59.94/60</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
<td><p>○</p></td>
</tr>
</tbody>
</table>

 

ソース オーディオは、DisplayPort ケーブルと HDMI ケーブルによって提供されます。 VGA を使う必要がある場合、Surface Hub には 3.5 mm プラグ用のオーディオ入力ポートがあります。 また、Surface Hub では、USB ケーブルを使用して、touchback および inkback 機能対応の Windows 10 デバイスを Surface Hub から操作できます。 USB ケーブルは、既にケーブルで接続されているビデオ入力にも使用できます。

ゲスト モードを使用して PC を接続する場合は、次のいずれかを使用します。

**DisplayPort** -- DisplayPort ケーブルと USB 2.0 ケーブル

**HDMI** -- HDMI ケーブルと USB 2.0 ケーブル

**VGA** -- VGA ケーブル、3.5 mm オーディオ ケーブル、および USB 2.0 ケーブル

ゲスト モードを使用しているコンピューターが、touchback と inkback に対応していない場合は、USB ケーブルは必要ありません。

## 代替 PC モード


代替 PC モードでは、Surface Hub の埋め込みコンピューターをオフにして、外部 PC を Surface Hub に接続します。 代替 PC ポートに接続すると、画面、ペン、タッチ機能など、Surface Hub の主な周辺機器にアクセスできます。 つまり、Surface Hub における Windows チーム エクスペリエンスのメリットはなくなりますが、ユーザー自身の Windows コンピューターを用意して操作できることによる柔軟性がもたらされます。

### ソフトウェア要件

代替 PC モードでは、64 ビット版の Windows 10 Home、Windows 10 Pro、および Windows 10 Enterprise を使用して Surface Hub を実行できます。 [Surface Hub 代替 PC ドライバー パッケージ](https://www.microsoft.com/download/details.aspx?id=52210)は、Microsoft ダウンロード センターからダウンロードできます。 代替 PC として使用することを計画しているコンピューターには、このドライバーをインストールすることをお勧めします。

### ハードウェア要件

Surface Hub は、さまざまなハードウェアと互換性があります。 代替 PC のプロセッサとメモリ構成を選び、使用するプログラムがサポートされるようにします。 代替 PC ハードウェアは、64 ビット版の Windows 10 をサポートする必要があります。

### グラフィックス アダプター

Surface Hub は代替 PC モードでは、DisplayPort 信号を生成するグラフィックス アダプターをサポートします。 Surface Hub の解像度とリフレッシュ レートに対応できるグラフィックス アダプターを使用することで、エクスペリエンスを向上できます。 たとえば、Surface Hub で最適な推奨される代替 PC エクスペリエンスは、120 Hz のビデオ信号です。

**55 インチの Surface Hubs** - 解像度 1080p、リフレッシュレート 120 Hz に対応するグラフィックス カードを使用してください。

**84 インチの Surface Hubs** - 最適なエクスペリエンスを得るには、DisplayPort 1.2 で 4 ストリームを出力し、120Hz で 2160p (垂直リフレッシュ レート 120 Hz で 3840 x 2160) を生成できるグラフィックス アダプターを使用してください。 NVIDIA Quadro K2200、NVIDIA Quadro K4200、NVIDIA Quadro M6000、AMD FirePro W5100、AMD FirePro W7100、AMD FirePro W9100 で動作することを確認しました。 グラフィックス カードはこれ以外にもあり、他のベンダーからも提供されています。 

最新のドライバーについては、直接グラフィックス カード ベンダーのサイトを確認してください。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>グラフィックス ベンダー</th>
<th>ドライバーのダウンロード ページ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NVIDIA</p></td>
<td><p><a href="http://nvidia.com/Download/index.aspx" data-raw-source="[http://nvidia.com/Download/index.aspx](http://nvidia.com/Download/index.aspx)">http://nvidia.com/Download/index.aspx</a></p></td>
</tr>
<tr class="even">
<td><p>AMD</p></td>
<td><p><a href="http://support.amd.com/en-us/download" data-raw-source="[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)">http://support.amd.com/en-us/download</a></p></td>
</tr>
<tr class="odd">
<td><p>Intel</p></td>
<td><p><a href="https://downloadcenter.intel.com/" data-raw-source="[https://downloadcenter.intel.com/](https://downloadcenter.intel.com/)">https://downloadcenter.intel.com/</a></p></td>
</tr>
</tbody>
</table>

 

### ポート

55 インチの Surface Hub の代替 PC ポート。

![55 インチの Surface Hub の代替 PC ポートを示す画像。](images/sh-55-rpc-ports.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>説明</th>
<th>種類</th>
<th>インターフェイス</th>
<th>詳細</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC ビデオ</p></td>
<td><p>ビデオ入力</p></td>
<td><p>DP 1.2</p></td>
<td><ul>
<li><p>120 Hz で 1080 p の全画面表示とオーディオ</p></li>
<li><p>HDCP 準拠</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>内蔵の周辺機器</p></td>
<td><p>USB 出力</p></td>
<td><p>USB 2.0 タイプ B</p></td>
<td><ul>
<li><p>タッチ</p></li>
<li><p>ペン</p></li>
<li><p>スピーカー (複数)</p></li>
<li><p>マイク</p></li>
<li><p>カメラ</p></li>
<li><p>NFC センサー</p></li>
<li><p>環境光センサー</p></li>
<li><p>受動赤外線センサー</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB ハブ</p></td>
<td><p>USB 出力</p></td>
<td><p>USB 2.0 タイプ B</p></td>
<td><ul>
<li><p>USB ポートの下</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

84 インチの Surface Hub の代替 PC ポート。

![84 インチの Surface Hub の代替 PC ポートを示す画像。](images/sh-84-rpc-ports.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>説明</th>
<th>種類</th>
<th>インターフェイス</th>
<th>詳細</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC ビデオ</p></td>
<td><p>ビデオ入力</p></td>
<td><p>DP 1.2 (2x)</p></td>
<td><ul>
<li><p>120 Hz で 2160 p の全画面表示とオーディオ</p></li>
<li><p>HDCP 準拠</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>内蔵の周辺機器</p></td>
<td><p>USB 出力</p></td>
<td><p>USB 2.0 タイプ B</p></td>
<td><ul>
<li><p>タッチ</p></li>
<li><p>ペン</p></li>
<li><p>スピーカー (複数)</p></li>
<li><p>マイク</p></li>
<li><p>カメラ</p></li>
<li><p>NFC センサー</p></li>
<li><p>環境光センサー</p></li>
<li><p>受動赤外線センサー</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB ハブ</p></td>
<td><p>USB 出力</p></td>
<td><p>USB 2.0 タイプ B</p></td>
<td><ul>
<li><p>USB ポートの下</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### 代替 PC のセットアップ手順

**代替 PC モードを使用するには**

1.  [Surface Hub 代替 PC ドライバー パッケージ](https://www.microsoft.com/download/details.aspx?id=52210) をダウンロードして、代替 PC にインストールします。

    >[!NOTE]
    >代替 PC は、使用していないときに Surface Hub によってディスプレイの電源を切れるように、スリープまたは休止状態に設定することをお勧めします。

2.  電源ケーブルの横にある電源スイッチを使用して、Surface Hub の電源を切ります。

3.  Surface Hub の代替 PC ポートから代替 PC にケーブルを接続します。 このポートは、通常、取り外しができるプラスチックのカバーで覆われています。

    55 インチの Surface Hub -- DisplayPort ケーブル 1 本と USB ケーブル 2 本を接続します。

    84 インチの Surface Hub -- DisplayPort ケーブル 2 本と USB ケーブル 2 本を接続します。

4.  モード スイッチを**代替 PC** に切り替えます。 モード スイッチは代替 PC ポートの横にあります。

5.  電源ケーブルの横にある電源スイッチを使用して、Surface Hub の電源を入れます。

6.  Surface Hub の右側にある電源ボタンを押します。

Surface Hub の内蔵の PC を使用するように切り替えることができます。

**内蔵の PC に戻すには**

1.  電源ケーブルの横にある電源スイッチを使用して、Surface Hub の電源を切ります。

2.  モード スイッチを内蔵 PC に切り替えます。 モード スイッチは代替 PC ポートの横にあります。

3.  電源ケーブルの横にある電源スイッチを使用して、Surface Hub の電源を入れます。

 
## ビデオ出力
 
Surface Hub には、Surface Hub から別のディスプレイに視覚的なコンテンツをミラーリングするために、ビデオ出力ポートが搭載されています。

### ポート

55 インチの Surface Hub のビデオ出力ポート

![ビデオ出力ポートの図](images/video-out-55.png)

84 インチの Surface Hub のビデオ出力ポート

![ビデオ出力ポートの図](images/video-out-84.png)

<table>
<thead>
<tr class="header">
<th>説明</th>
<th>種類</th>
<th>インターフェイス</th>
<th>機能</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ビデオ出力のミラー</p></td>
<td><p>ビデオ出力</p></td>
<td><p>ビデオ出力</p></td>
<td><ul>
<li><p>標準的な DisplayPort モニターへの接続をサポート (24bpp で 1080p60 の解像度を表示する x4 リンクのみサポート)</p></li>
<li><p>DisplayPort to HDMI アダプターを使用することで (1080p60 をサポートする) HDMI モニターの使用をサポート</p></li>
</ul></td>
</tr>
</tbody>
</table>

## ケーブル (複数)

55 インチと 84 インチのどちらの Surface Hub デバイスも、認定 DisplayPort および HDMI ケーブルで動作することがテストされています。  ベンダーにより販売されている長いケーブルも Surface Hub で動作する可能性がありますが、Hub で動作することが確認されているのはテスト ラボにより認定されているこれらのケーブルだけです。 たとえば、認定されている DisplayPort ケーブルは最大 3 メートルですが、多くのベンダーが 3 倍の長さのケーブルを販売しています。 長いケーブルが必要な場合は、HDMI を使うことを強くお勧めします。  HDMI には、リピーターの使用など、コスト効率の高い長距離ケーブル用ソリューションが多く用意されています。 ほぼすべての DisplayPort ソースは、HDMI シンクが検出された場合に HDMI 信号に自動的に切り替えます。


## Bluetooth アクセサリ

次のアクセサリは、Bluetooth を使って Surface Hub に接続できます。

- マウス (複数)
- キーボード
- ヘッドセット
- スピーカー

>[!NOTE]
>Bluetooth ヘッドセットまたはスピーカーを接続すると、[既定のマイクとスピーカーの設定](local-management-surface-hub-settings.md)の変更が必要になることがあります。
