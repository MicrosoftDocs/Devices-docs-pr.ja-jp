---
title: ルーム コントロール システムを使う (Surface Hub)
description: Microsoft Surface Hub では、ルーム コントロール システムを使用できます。
ms.assetid: DC365002-6B35-45C5-A2B8-3E1EB0CB8B50
ms.reviewer: ''
manager: laurawi
keywords: ルーム コントロール システム, room control system, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0e3b1706e58edb6e37156eda8d06fb0faefa4c91
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834846"
---
# ルーム コントロール システムを使う (Surface Hub)


Microsoft Surface Hub では、ルーム コントロール システムを使用できます。

Surface Hub でルーム コントロール システムを使用するには、ルーム コントロール ハードウェアを Surface Hub に接続します。通常、接続には Surface Hub の下部にある RJ11 シリアル ポートを使用します。

## 端末の設定

ルーム コントロール システムのコントロール パネルに接続するために、Surface Hub で端末の設定を構成する必要はありません。 PC やノート PC を Surface Hub に接続して Surface Hub からシリアル コマンドを送信する場合は、Tera Term や PuTTY などの端末エミュレーターを使用できます。 

| 設定 | 値 |
| --- | --- |
| ボー レート | 115200 |
| データ ビット | 個 | 
| ストップ ビット | 件 |
| パリティ | なし |
| フロー制御 | なし |
| ライン フィード | すべてのキャリッジ リターン |
 

## 配線図

Surface Hub のシリアル ポートをルーム コントロール システムに接続する際は、標準的な RJ-11 (6P6C) コネクタを使用できます。 これは、推奨されている接続方法です。 RJ-11 4 コンダクター ケーブルを使用することもできますが、この方法は推奨されません。

次の図では、DB9 ケーブルに対する RJ-11 (6P6C) に使用する適切なピンアウトを示します。

![配線図を示す画像。](images/room-control-wiring-diagram.png)

## コマンド セット

ルーム コントロール システムでは、コマンドに関して一般的な会議室シナリオを使用します。 コマンドはルーム コントロール システムで生成され、Surface Hub とのシリアル接続を介して伝達されます。 コマンドは ASCII ベースで、Surface Hub は状態変化の発生を認識します。

以下のコマンド修飾子を使用できます。 コマンドは、改行文字 (\n) に到達すると終了します。 管理ポート コマンドによって直接トリガーされていない状態変化では、応答があらゆる時点で発生する可能性があります。

| 修飾子 | 結果 |
| --- | --- |
| + | 値を増やす |
| - | 値を減らす |
| = | 個別の値を設定する |
| ? | 現在の値を照会する |
 

## 電源

Surface Hub の電力は、以下のいずれかの状態になります。

| 状態 | Energy Star の状態| 説明 |
| --- | --- | --- |
| 0 | S5 | オフ |
| 件 | - | 電源投入 (不確定状態) |
| 両面 | S3 | スリープ |
| 個 | S0 | 準備完了 |


代替 PC モードでは、電源状態は準備完了とオフのみであり、ディスプレイのみを変更します。 管理ポートを使って代替 PC の電源を入れることはできません。 

| 状態 | Energy Star の状態| 説明 |
| --- | --- | --- |
| 0 | S5 | オフ |
| 個 | S0 | 準備完了 |

コントロール デバイスの場合、5/準備完了以外はすべてオフと考える必要があります。 各 PowerOn コマンドは、2つの状態の変更と応答を生成します。 

| コマンド | 状態の変化| 応答 |
| --- | --- | --- |
| PowerOn | デバイスの電源が入ります (ディスプレイ + PC)。</br></br>PC サービスによって、PC の準備ができたことが SMC に通知されます。 |  Power=0</br></br>Power=5 |
| PowerOff | デバイスが環境状態に移行します (PC オン、ディスプレイ暗転)。 |  Power=0 |
| Power? |  SMC は最後にわかっている電源状態を報告します。 |  Power=<#> |



## Brightness

現在の明るさレベルの範囲は、0 ~ 100 です。

明るさレベルの変更は、ルーム コントロール システムなどのシステムによって送信できます。

| コマンド | 状態の変化 |応答 |
| --- | --- | --- |
| Brightness+ | システム管理コントローラー (SMC) が、明るさを上げるコマンドを送信します。</br></br>ルーム コントロール システムの PC サービスによって、新しい明るさレベルが SMC に通知されます。 |  Brightness = 51 |
| Brightness- |  SMC が、明るさを下げるコマンドを送信します。</br></br>PC サービスによって、新しい明るさレベルが SMC に通知されます。 | Brightness = 50 |

##  <a name="volume"></a>Volume

現在の音量レベルの範囲は、0 ~ 100 です。

音量レベルの変更は、ルーム コントロール システムなどのシステムによって送信できます。

>[!NOTE]
>Volume コマンドでは、埋め込みモードまたは代替 PC モードの音量のみが制御され、[ゲストのソース](connect-and-display-with-surface-hub.md)は制御されません。

| コマンド | 状態の変化 | 応答</br>([代替 PC モード](connect-and-display-with-surface-hub.md#replacement-pc-mode) で有効) |
| --- | --- | --- |
| Volume+ |  SMC が音量を上げるコマンドを送信します。</br></br>PC サービスによって、新しい音量レベルが SMC に通知されます。 |  Volume = 51 |
| Volume- |  SMC が音量を下げるコマンドを送信します。</br></br>PC サービスによって、新しい音量レベルが SMC に通知されます。 |  Volume = 50 |


 

## オーディオのミュート

オーディオをミュートすることができます。

| コマンド | 状態の変化 | 応答 |
| --- | --- | --- |
| AudioMute+ |  SMC がオーディオのミュート コマンドを送信します。</br></br>PC サービスによって、オーディオがミュートされていることが SMC に通知されます。 |  なし |


 

## ビデオ ソース

複数の表示ソースを使用できます。

| 状態 | 説明 | 
| --- | --- |
| 0 |  オンボード PC |
| 件 |  DisplayPort |
| 両面 |  HDMI |
| - |  VGA |


 

表示ソースへの変更は、ルーム コントロール システムなどのシステムによって送信できます。

| コマンド | 状態の変化 | 応答 |
| --- | --- | --- |
| Source=# |  SMC によって目的のソースに変更されます。</br></br>PC サービスによって、表示ソースが切り替えられたことが SMC に通知されます。 |  Source=&lt;#&gt; |
| Source+ |  SMC によって次のアクティブな入力ソースに移行されます。</br></br>PC サービスによって、現在の入力ソースが SMC に通知されます。 |  Source=&lt;#&gt; |
| Source- | SMC によって前のアクティブな入力ソースに移行されます。</br></br>PC サービスによって、現在の入力ソースが SMC に通知されます。 |  Source=&lt;#&gt; |
| Source? |  SMC が、PC サービスでアクティブな入力ソースを照会します。</br></br>PC サービスによって、現在の入力ソースが SMC に通知されます。 | Source=&lt;#&gt; |

## Errors

エラーは、次の表の形式に従って返されます。

| エラー | 注意 |
| --- | --- |
| エラー: 不明なコマンド '&lt;入力値&gt;' です。 |  命令に不明な初期コマンドが含まれています。 たとえば、&quot;VOL+&quot; では無効になり、&quot;エラー: 不明なコマンド 'VOL' です&quot; と表示されます。 |
| エラー: 不明な演算子 '&lt;入力値&gt;' です。 |  命令に不明な演算子が含まれています たとえば、&quot;Volume!&quot; では無効となり、&quot;エラー: 不明な演算子 '!' です&quot; が表示されます。 |
| エラー: 不明なパラメーター '&lt;入力値&gt;' です。 |  命令に不明なパラメーターが含まれています。 たとえば、&quot;Volume=abc&quot; では無効となり、&quot;エラー: 不明なパラメーター 'abc' です&quot; と表示されます。 |
| エラー: 電源が切れているときに使用できないコマンド ('&lt;入力値&gt;') です。 |  Surface Hub の電源が切れている場合、Power 以外のコマンドはこのエラーを返します。 たとえば、&quot;Volume+&quot; では無効となり、&quot;エラー: 電源が切れているときに使用できないコマンド 'Volume' です&quot; と表示されます。 |


 

##  <a name="related-topics"></a>関連トピック


[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

 

 





