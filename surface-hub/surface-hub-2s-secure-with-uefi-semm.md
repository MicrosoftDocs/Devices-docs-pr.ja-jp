---
title: SEMM で Surface Hub の2S をセキュリティで保護し、管理する
description: 詳細については、「SEMM による Surface Hub のセキュリティ保護」を参照してください。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 03ce1dfa48ade8aade545c63818ca5ae8947e6b7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835270"
---
# SEMM と UEFI による Surface Hub 2S のセキュリティ保護と管理

Surface Hub 2S の新機種では、SEMM を使ってデバイスの UEFI 設定を管理できます。
Microsoft Surface UEFI コンフィギュレーターを使用して、次のコンポーネントを制御します。

- ワイヤード (有線) LAN
- カメラ
- Bluetooth
- Wi-Fi
- 占有センサー

Microsoft Surface UEFI コンフィギュレーターを使用して、次の UEFI 設定のオンとオフを切り替えます。

- Boot

    - PXE ブート用 IPv6
    - 代替ブート
    - ブート順序ロック
    - USB ブート
- UEFI の先頭ページ

    - デバイス
    - Boot
    - 日付/時刻

## UEFI 構成のイメージを作成する

他の Surface デバイスとは異なり、MSI ファイルまたは Win PE イメージを使って Surface Hub 2S でこれらの設定を適用することはできません。 代わりに、デバイスに読み込む USB イメージを作成する必要があります。 Surface Hub 2S UEFI 構成イメージを作成するには、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページから、最新バージョンの MICROSOFT Surface uefi コンフィギュレーターをダウンロードしてインストールします。 UEFI と SEMM の使い方について詳しくは、「 [Microsoft Surface Enterprise Management モード](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」をご覧ください。

## Surface Hub 2S で UEFI を構成するには

1. UEFI コンフィギュレーターを起動し、最初の画面で [**構成パッケージ**] を選びます。<br><br>
![* UEFI コンフィギュレーターを開始し、「構成パッケージ」を選択します。](images/sh2-uefi1.png) <br> <br>
2. パッケージに証明書を追加するには、パッケージを署名して保護するために、秘密キーに関する有効な証明書を .pfx ファイル形式で指定する必要があります。 [ **+ 証明書による保護**] を選択します。 <br>
![* 選択 + 証明書の保護 *](images/sh2-uefi2.png) <br><br>
3. 証明書の秘密キーのパスワードを入力します。<br>
![* 証明書の秘密キーのパスワードを入力 *](images/sh2-uefi3.png) <br><br>
4. 秘密キーをインポートしたら、続けてパッケージの作成を行います。<br>
![* パッケージの作成を続けます *](images/sh2-uefi4.png) <br><br>
5. UEFI 構成パッケージのターゲットとして、[ **hub**および**Surface hub 2s** ] を選びます。<br>
![* UEFI 構成パッケージのターゲットとしてハブおよび Surface Hub 2S を選ぶ *](images/sh2-uefi5.png) <br><br>
6. Surface Hub 2S でアクティブ化または非アクティブ化するコンポーネントと設定を選びます。<br>
![* アクティブ化または非アクティブ化するコンポーネントと設定を選択してください *](images/sh2-uefi6.png) <br><br>
7. [USB] オプションを使用して、ファイルをエクスポートします。<br>
![* USB オプションを使用してファイルをエクスポート *](images/sh2-uefi8.png) <br><br>
8. このパッケージに使用する USB ドライブを挿入して選択します。 USB ドライブの書式が設定され、お持ちの情報が失われます。<br>
![* パッケージ用の USB ドライブを挿入して選択します *](images/sh2-uefi9.png) <br><br>
9. パッケージの作成が正常に完了すると、証明書の拇印の最後の2文字が表示されます。 Surface Hub 2S に構成をインポートするときは、これらの文字が必要です。<br>
![* パッケージの正常な構成 *](images/sh2-uefi10.png) <br>

## UEFI を起動するには

Surface Hub 2S をオフにします。 **音量を上げる**ボタンを長押しして、**電源**ボタンを押します。 [UEFI] メニューが表示されるまで、[音量を上げる] ボタンを押したままにします。
