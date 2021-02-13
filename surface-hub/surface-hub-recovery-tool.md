---
title: Surface Hub の回復ツールの使用
description: Surface Hub 回復ツールを使って SSD を再イメージ化する方法について説明します。
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/11/2020
ms.localizationpriority: medium
ms.openlocfilehash: 34a05eeabd284e0ad43317577b8e7ff9348ffe21
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327341"
---
# Surface Hub の回復ツールの使用

[Microsoft Surface Hub 回復](https://www.microsoft.com/download/details.aspx?id=52210)ツールは、サポートを呼び出したり SSD を交換したりすることなく、Windows 10 デスクトップ デバイスを使って Surface Hub Solid State Drive (SSD) のイメージを再イメージ化するのに役立ちます。 このツールを使用すると、不明な管理者パスワードを持つ SSD、ブート エラー、クラウド回復を完了できなかった SSD、またはオペレーティング システムの古いバージョンを持つデバイスのイメージを再作成できます。 物理的に破損した SSD は修正されません。

回復ツールを使って Surface Hub SSD を再イメージ化するには、Surface Hub から SSD を取り外し、ドライブを USB から SATA ケーブルに接続し、回復ツールがインストールされているデスクトップ PC にケーブルを接続する必要があります。 Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。

> [!IMPORTANT]
> デバイスをスリープ状態にしたり、イメージ ファイルのダウンロードを中断したりしない。

ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。

## 前提条件

### Mandatory

- 64 ビット バージョンの Windows 10 バージョン 1607 以上を実行しているホスト PC。
- インターネット アクセス
- USB 2.0 以上のポートを開く
- USB から SATA ケーブル
- ホスト コンピューター上の 10 GB の空きディスク領域
- 代替としてサポートによって提供される Surface Hub または SSD に付属する SSD。 Microsoft から提供されていない SSD はサポートされていません。

### 推奨

- 高速インターネット接続
- USB 3.0 ポートを開く
- USB 3.0 以上の USB- SATA ケーブル
- イメージング ツールは、次のケーブルの作成とモデルでテストされました。
    - Startech USB312SAT3CB
    - サギス RCUC16001
    - Ugreen 20231

## Surface Hub 回復ツールのダウンロード

Surface Hub 回復ツールは[、Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)からファイル名の下でダウンロード**SurfaceHub_Recovery_v2.7.139.0.msi。 **

> [!IMPORTANT]
> 2021 年 2 月 11 日にリリースされたこのバージョンは、機能しなくなった以前のビルドに置き換わるものになります。 このツールを以前にダウンロードした場合は、現在のバージョンを破棄して使用してください。

ダウンロードを開始するには、[ダウンロード] を **クリック**し、一覧から **SurfaceHub_Recovery_v2.7.139.0.msi**  を選択して、[次へ] をクリック **します**。 ポップアップから、次のいずれかを選択します。

- [ **ファイル名を指定** して実行] をクリックして、インストールをすぐに開始します。
- [ **保存]** をクリックして、後でインストールするためにダウンロードをコンピューターにコピーします。

ホスト PC に Surface Hub 回復ツールをインストールします。

## Surface Hub 回復ツールを実行する

1. ホスト PC で、[スタート****] ボタンを選択し、左側のアルファベット順の一覧をスクロールして、回復ツールのショートカットを選択します。

    ![Microsoft Surface Hub 回復ツールのショートカット](images/shrt-shortcut.png)

2. **[開始]** をクリックします。

    ![回復ツールの [スタート] ボタン](images/shrt-start.png)


3. [ガイダンス] **ウィンドウで** 、[次へ] を **クリックします**。

    ![コンピューターをスリープ状態にしない](images/shrt-guidance.png)

4. [イメージの選択] ウィンドウで **、RS2**または後続の**20H2**をクリックし、[続行] を選択して、[イメージのダウンロード]**を選択します。** ****

     ![回復ツール イメージの選択 ](images/shrt-select-image.png) ![ 回復ツールのダウンロード イメージ](images/shrt-download-image.png)

5. 回復イメージをダウンロードする時間は、インターネット接続の速度に依存します。 平均的な企業接続では、8 GB の画像ファイルをダウンロードするために最大 1 時間かかる場合があります。

    ![イメージのダウンロード](images/shrt-download.png)



5. ダウンロードが完了すると、SSD ドライブを接続するように指示されます。 ツールが接続されているドライブを見つからない場合は、使用されているケーブルが SSD の名前を Windows に報告していない可能性があります。  イメージング ツールは、続行する前にドライブの名前を "LITEON L CH-128V2S USB デバイス" として見つける必要があります。  Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。

    ![SSD の接続](images/shrt-drive.png)

6. ドライブが認識されると、[スタート] を **クリック** して再イメージング プロセスを開始します。 ドライブ上のすべてのデータが消去されるという警告で **、[OK]** をクリックします。



    ドライブにシステム イメージを適用する前に、SSD が再パーティション化され、フォーマットされます。 システム バイナリのコピーには約 30 分かかりますが、USB バスの速度、使用しているケーブル、システムにインストールされているウイルス対策ソフトウェアによっては、時間がかかる場合があります。



## トラブルシューティングと一般的な問題

問題 | 備考
--- | ---
SSD のイメージ作成に失敗する | 出荷時の SSD とテスト済みケーブルのいずれかを使用してください。
再作プロセスが停止/固定された状態で表示される | SSD に影響を与え、Surface Hub 回復ツールを閉じて再起動しても安全です。
ドライブがツールによって認識されない | Surface Hub SSD が"LITEON L CH-128V2S USB デバイスLite-Onドライブとして列挙されている必要があります。  ドライブが別の名前付きデバイスとして認識される場合、現在のケーブルは互換性がありません。 別のケーブルまたは上記のテスト済みケーブルのいずれかを試してください。
エラー: -2147024809 | ディスク マネージャーを開き、Surface Hub ドライブ上のパーティションを削除します。  ドライブを切断し、ホスト コンピューターに再接続します。 イメージング ツールを再度再起動します。

ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。

## バージョン履歴


### バージョン v2.7.139.0

*リリース日: 2021 年 2 月 11 日*<br>
このバージョンの Surface Hub 回復ツールでは、次のサポートが追加されています。

- セキュリティに関する更新


### バージョン v2.0.139.0

> [!IMPORTANT]
> このバージョンは機能しなくなりました。 上記の現在のバージョンをダウンロードしてください。 

*リリース日: 2020 年 12 月 18 日*<br>
このバージョンの Surface Hub 回復ツールでは、次のサポートが追加されています。
- Windows 10 Team 2020 Update (20H2) をサポートする更新プログラム
- ユーザー エクスペリエンスの向上
- アーキテクチャの変更
- 利用統計情報の追加

