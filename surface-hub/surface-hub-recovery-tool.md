---
title: Surface Hub の回復ツールの使用
description: Surface Hub の回復ツールを使用して、SSD を再イメージする方法について説明します。
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/22/2018
ms.localizationpriority: medium
ms.openlocfilehash: 1988a6ed59525d7dc77872e532247dbc50f01bdf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836897"
---
# Surface Hub の回復ツールの使用

[Microsoft Surface hub の回復ツール](https://www.microsoft.com/download/details.aspx?id=52210)では、Windows 10 デスクトップデバイスを使用して Surface Hub のソリッドステートドライブ (ssd) を再イメージすることができます。これには、サポートに問い合わせるか、ssd を交換する必要があります。 このツールを使用すると、管理者パスワードが不明な SSD、ブートエラー、クラウドの回復を完了できなかったデバイス、または以前のバージョンのオペレーティングシステムを搭載しているデバイスの SSD を再作成することができます。 このツールでは、物理的に破損した Ssd は解決されません。

回復ツールを使用して Surface Hub SSD を再イメージするには、Surface Hub から SSD を取り外す必要があります。ドライブを USB 対 SATA ケーブルに接続して、回復ツールがインストールされているデスクトップ PC にケーブルを接続します。 Surface Hub から既存のドライブを削除する方法について詳しくは、「 [Surface HUB SSD の交換](surface-hub-ssd-replacement.md)」をご覧ください。

> [!IMPORTANT]
> デバイスがスリープ状態になったり、イメージファイルのダウンロードが中断されたりしないようにします。

このツールでドライブの再作成に失敗した場合は、 [Surface Hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。

## 前提条件

### Mandatory

- 64ビット版の Windows 10 バージョン1607以降を実行しているホスト PC。
- インターネット アクセス
- USB 2.0 以上のポートを開く
- USB 対 SATA ケーブル
- ホストコンピューター上の 10 GB の空きディスク領域
- SSDs は Surface Hub に同梱されています。また、交換としてサポートによって提供される SSD。 Microsoft によって提供されていない Ssd はサポートされていません。

### 推奨

- 高速インターネット接続
- USB 3.0 ポートを開く
- Usb 3.0 以上の USB ケーブル
- イメージングツールは、次のようなケーブルのメーカーとモデルを使ってテストされています。
    - Startech USB312SAT3CB
    - Rosewill
    - Ugreen 20231

## Surface Hub 回復ツールをダウンロードする

Surface hub 回復ツールは、[ファイル名**SurfaceHub_Recovery_v1.14.137.0.msi**の下[にある surface hub ツール](https://www.microsoft.com/download/details.aspx?id=52210)からダウンロードできます。

ダウンロードを開始するには、[**ダウンロード**] をクリックし、一覧から [ **SurfaceHub_Recovery_v1.14.137.0.msi** ] を選択して、[**次へ**] をクリックします。 ポップアップで、次のいずれかのオプションを選びます。

- [**実行**] をクリックして、すぐにインストールを開始します。
- [**保存**] をクリックして、後でインストールするためにダウンロードしたファイルをコンピューターにコピーします。

Surface Hub 回復ツールをホスト PC にインストールします。

## Surface Hub 回復ツールを実行する

1. ホスト PC で、[**スタート**] ボタンを選択し、左側のアルファベット順の一覧をスクロールして、回復ツールのショートカットを選択します。

    ![Microsoft Surface Hub 回復ツールのショートカット](images/shrt-shortcut.png)

2. **[開始]** をクリックします。

    ![回復ツールの [スタート] ボタン](images/shrt-start.png)

3. [**ガイダンス**] ウィンドウで、[**次へ**] をクリックします。

    ![マシンがスリープガイダンスに移動しないようにする](images/shrt-guidance.png)

4. 画像をダウンロードするには、[**はい]** をクリックします。 回復イメージのダウンロードにかかる時間は、インターネット接続の速度によって異なります。 企業の平均的な接続では、8GB の画像ファイルをダウンロードするまでに最長で1時間かかることがあります。

    ![画像をダウンロードしますか?](images/shrt-download.png)

5. ダウンロードが完了すると、SSD ドライブへの接続を指示するツールが表示されます。 このツールで接続されているドライブが見つからない場合は、使用されているケーブルで SSD の名前が Windows に報告されていない可能性があります。  イメージングツールは、続行する前に、ドライブの名前を "LITEON L CH-128V2S USB デバイス" として探す必要があります。  Surface Hub から既存のドライブを削除する方法について詳しくは、「 [Surface HUB SSD の交換](surface-hub-ssd-replacement.md)」をご覧ください。

    ![SSD の接続](images/shrt-drive.png)

6. ドライブが認識されたら、[**開始**] をクリックして再イメージングプロセスを開始します。 ドライブ上のすべてのデータが消去されるという警告が表示されたら、[ **OK**] をクリックします。

    ![SSD の再イメージングを開始する](images/shrt-drive-start.png)

    システムイメージをドライブに適用する前に、SSD は repartitioned および書式設定されています。 システムバイナリのコピーには約30分かかりますが、USB バスの速度、使用されているケーブル、またはシステムにインストールされているウイルス対策ソフトウェアによって、より長い時間がかかることがあります。

    ![コピーが完了しました](images/shrt-done.png)

    ![イメージの完成](images/shrt-complete.png)

## トラブルシューティングと一般的な問題

問題 | 備考
--- | ---
このツールでは、SSD の画像に失敗します | 工場で供給されている SSD とテストしたケーブルのいずれかを使用していることを確認してください。
再イメージのプロセスが停止またはフリーズする | SSD に悪影響を及ぼすことなく Surface Hub の回復ツールを終了して再起動することは安全です。
ドライブがツールによって認識されない | Surface Hub SSD がライトツードライブとして列挙されていることを確認します ("LITEON L CH-128V2S USB デバイス")。  ドライブが別の名前付きデバイスとして認識された場合、現在のケーブルには互換性がありません。 別のケーブルを試すか、上に記載されているテスト済みケーブルのいずれかを試してみてください。
エラー:-2147024809 | ディスクマネージャーを開き、Surface Hub ドライブのパーティションを削除します。  ドライブを切断し、ホストコンピューターに再接続します。 もう一度イメージングツールを再起動します。

このツールでドライブの再作成に失敗した場合は、 [Surface Hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。
