---
title: Microsoft Surface Data Eraser (Surface)
description: Surface デバイスからデータを安全に消去するうえで Microsoft Surface Data Eraser ツールがどのように役立つかを紹介します。
ms.assetid: 8DD3F9FE-5458-4467-BE26-E9200341CF10
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: ツール, USB, データ, 消去, tool, USB, data, erase
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
audience: itpro
ms.date: 10/12/2020
ms.openlocfilehash: 8b201ce45533c28740a7c6bdfcb56688ada25718
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114705"
---
# Microsoft Surface Data Eraser


Surface デバイスからデータを安全に消去するうえで Microsoft Surface Data Eraser ツールがどのように役立つかを紹介します。

[Microsoft Surface Data Eraser](https://www.microsoft.com/download/details.aspx?id=46703) は、USB スティックから起動して、互換性のある Surface デバイスからすべてのデータのセキュア ワイプを実行できるツールです。 Microsoft Surface Data Eraser USB スティックの要件は、USB から起動できることだけです。 この USB スティックは、用意されているウィザード (Microsoft Surface Data Eraser Wrapper) を使って簡単に作成でき、単純なグラフィカル インターフェイスで簡単に使うことができます (コマンド ラインを使う必要はありません)。 Microsoft が Surface のサービス プロセスで使うデータ消去機能とプラクティスについて詳しくは、「[Surface を修理に出す場合にデータを保護する](https://www.microsoft.com/surface/support/security-sign-in-and-accounts/data-wiping-policy)」をご覧ください。

>[!IMPORTANT]
>Microsoft Surface Data Eraser は NVM Express (NVMe) format コマンドを使って、「[NIST 特別刊行物 800-88 改訂 1](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf)」で承認されているように、データを消去します。 

互換性のある Surface デバイスは次のとおりです。

- Surface Book (すべてのエディション)
- Surface Go (すべてのエディション)
- Surface Pro X (すべてのエディション)
- Surface のノート Pc (すべてのエディション)
- Surface のノート Pc の移動
- Surface Studio (すべてのエディション)
- Surface Pro 2 以降
- Surface Hub 2 の Windows 10 Pro と Enterprise

Microsoft Surface Data Eraser が役立つシナリオには次のようなものがあります。

-   修理に出す Surface デバイスを準備する

-   企業または組織で使わなくなった Surface デバイスを使用停止にする

-   新しい部門で使うため、または新規ユーザーによる使用のために Surface デバイスを再利用する

-   重要なデータで使われていたデバイスの再イメージ化を実行するときの標準的な手法

>[!NOTE]
>サード パーティのデバイス、Windows RT を実行している Surface デバイス (Surface や Surface 2 など)、Surface Pro は、Microsoft Surface Data Eraser と互換性がありません。

>[!NOTE]
>Microsoft Surface Data Eraser を実行するには USB から起動できる必要があるため、デバイスが USB から起動するように構成されていない場合や、デバイスのブートまたは POST が正常に行われない場合は、Microsoft Surface Data Eraser ツールは機能しません。

>[!NOTE]
>Surface Studio および Surface Studio 2 の Surface Data Eraser は、ディスクの消去が発生する前に WinPE で起動するのに最大 6 分かかる場合があります。


## Microsoft Surface Data Eraser USB スティックの作成方法


Microsoft Surface Data Eraser USB スティックを作成するには、まず、この記事の冒頭にあるリンクを使って、Microsoft ダウンロード センターから Microsoft Surface Data Eraser セットアップ ツールをインストールします。 USB スティックを*作成*するのに Surface デバイスは必要ありません。 お使いのコンピューターにインストール ファイルをダウンロードした後、次の手順に従って Microsoft Surface Data Eraser 作成ツールをインストールします。

1.  Run the DataEraserSetup.msi installation file that you downloaded from the [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=46703)からダウンロードした DataEraserSetup.msi インストール ファイルを実行します。

2.  チェック ボックスをオンにして使用許諾契約の条項に同意し、**[Install]** をクリックします。

3.  **[Finish]** をクリックして、Microsoft Surface Data Eraser セットアップ ウィンドウを閉じます。

作成ツールをインストールした後、次の手順に従って Microsoft Surface Data Eraser USB スティックを作成します。 次の手順を開始する前に、4 GB 以上の USB 3.0 スティックがコンピューターに接続されていることを確認してください。

1. [スタート] メニューまたはスタート画面から Microsoft Surface Data Eraser を起動します。

2. **[Build]** をクリックして、Microsoft Surface Data Eraser USB 作成プロセスを開始します。 

3. 図 1 に示すように、**[Start]** をクリックして、4 GB 以上の USB スティックが接続されていることを確認します。

   ![Microsoft Surface Data Eraser ツールの起動](images/dataeraser-start-tool.png "Start the Microsoft Surface Data Eraser tool")

   *図 1.  Microsoft Surface Data Eraser ツールの起動*
4.  図 2 に示すように、[**アーキテクチャの選択**] ページから、ほとんどの Surface デバイスでは **x64** を選択し、Surface Pro X では **ARM64** を選択します。 **[続行]** を選びます。

    ![アーキテクチャの選択](images/dataeraser-arch.png "Architecture Selection")<br>
       *図 2.  デバイスのアーキテクチャを選択する*
    

4. 図 3 に示すように、[**USBドライブの選択**] ページで目的の USB ドライブを選択し、[**開始**] をクリックして USB の作成プロセスを開始します。 選んだドライブがフォーマットされて、そのドライブ上の既存のデータは失われます。

   >[!NOTE]
   >[Start] ボタンが無効になっている場合は、リムーバブル ドライブの合計容量が 4 GB 以上であることを確認してください。
  
   ![USBドライブの選択](images/dataeraser-usb-selection.png "USB thumb drive selection")

   *図 3.  USBドライブの選択*

5. 作成プロセスが完了すると、USB ドライブがフォーマットされて、すべてのバイナリが USB ドライブにコピーされます。 **[Success]** をクリックします。

6. **[Congratulations]** 画面が表示されたら、サム ドライブを取り外すことができます。 これで、このサム ドライブを Surface デバイスに挿入し、そこからデバイスを起動して、デバイス上のすべてのデータを消去する準備ができました。 図 4 に示すように、[**完了**] をクリックして USB の作成プロセスを完了します。

   ![Surface Data Eraser USB 作成プロセス](images/dataeraser-complete-process.png "Surface Data Eraser USB creation process")

   *図 4:  Microsoft Surface Data Eraser USB 作成プロセスの完了*

7. **[X]** をクリックして Microsoft Surface Data Eraser を閉じます。

## Microsoft Surface Data Eraser USB スティックの使用方法


Microsoft Surface Data Eraser USB スティックを作成したら、次の手順に従って、サポートされている Surface デバイスを USB スティックから起動することができます。

1. サポートされている Surface デバイスに、起動可能な Microsoft Surface Data Eraser USB スティックを挿入します。

2. Microsoft Surface Data Eraser USB スティックから Surface デバイスを起動します。 USB スティックからデバイスを起動するには、次の手順を実行します。

   a.  Surface デバイスの電源を切ります。

   b.  **[音量を下げる]** ボタンを長押しします。

   c.  **電源**ボタンを押して離します。

   d.  **[音量を下げる]** ボタンを離します。
    
   >[!NOTE]
   >この手順を使っても、デバイスが USB から起動しない場合は、Surface UEFI で **[Enable Alternate Boot Sequence]** (代替ブート シーケンスを有効にする) オプションをオンにする必要があります。 Surface UEFI のブート構成について詳しくは、「[Surface UEFI の設定を管理する](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)」をご覧ください。

3. Surface デバイスが起動すると、**SoftwareLicenseTerms** テキスト ファイルが表示されます (図 5 を参照)。

   ![Microsoft Surface Data Eraser USB スティックの起動](images/data-eraser-3.png "Booting the Microsoft Surface Data Eraser USB stick")

   *図 5:  Microsoft Surface Data Eraser USB スティックの起動*

4. ソフトウェア ライセンス条項を読み、メモ帳ファイルを閉じます。

5. 「**Accept**」または「**Decline**」と入力して、ソフトウェア ライセンス条項を承諾または拒否します。 続行するには、ライセンス条項に同意する必要があります。

6. Microsoft Surface Data Eraser スクリプトによって、Surface デバイスに存在するストレージ デバイスが検出され、ネイティブなストレージ デバイスの詳細が表示されます。 続行するには、**Y** キー (Microsoft Surface Data Eraser を実行して、ストレージ デバイスからすべてのデータを削除する場合) を押すか、**N** キー (データを削除せずにデバイスをシャット ダウンする場合) を押します。

   >[!NOTE]
   >Microsoft Surface Data Eraser ツールによって、デバイスの起動に必要な Windows オペレーティング システム ファイルを含むすべてのデータが、安全かつ回復不可能な方法で削除されます。 Microsoft Surface Data Eraser によってワイプされた Surface デバイスを起動するには、まず Windows オペレーティング システムを再インストールする必要があります。 Windows オペレーティング システムを削除せずに Surface デバイスからデータを削除するには、**[PC を初期状態に戻す]** 機能を使用します。 ただし、この場合、フォレンジック機能またはデータ回復機能を使ったデータ回復を防止できません。 詳しくは、「[Windows 10 の回復オプション](https://support.microsoft.com/help/12415/windows-10-recovery-options)」をご覧ください。

   ![消去されるパーティションが表示されます。](images/sda-fig5-erase.png "Partition to be erased is displayed")
  
   *図 6.  消去されるパーティションが Microsoft Surface Data Eraser に表示される*

7. 手順 6. で **Y** キーを押した場合、データを消去するプロセスの破棄を伴う特性により、選択内容を確認する追加のダイアログ ボックスが表示されます。

8. **[Yes]** ボタンをクリックして、Surface デバイス上のデータの消去を続行します。

   >[!NOTE]
   >Surface Data Eraser USB ドライブで Surface Data Eraser を実行すると、**SurfaceDataEraserLogs** フォルダーにログ ファイルが生成されます。

## 変更と更新

Microsoft Surface Data Eraser は、Microsoft によって定期的に更新されます。 新しい各バージョンで提供される変更について詳しくは、以下をご覧ください。

### 3.33.139
*リリース日: 2020 年9月9日*

このバージョンの Surface データの消しゴムには、バグ修正が含まれており、次のサポートが追加されています。 

- アーキテクチャの再設計により、新製品のリリースによる更新の必要性を軽減
- 新しいツールの更新に使用できる通知
- テレメトリの追加
- Surface Hub 2 の Windows 10 Pro と Enterprise


### 3.30.139
*リリース日: 2020 年 5 月 11 日*

このバージョンの Surface Data Eraser では、次のサポートが追加されています。 
- Surface Book 3
- Surface Go 2
- Surface Go の新しい SSD

### 3.28.137
*リリース日: 2019 年 11 月 11 日* このバージョンの Surface Data Eraser:

- バグ修正を含む

### バージョン 3.21.137
*リリース日: 2019 年 10 月 21 日* このバージョンの Surface Data Eraser は x86 向けにコンパイルされており、次のデバイスのサポートが追加されています。

- Surface Pro 7、Surface Pro X、Surface Laptop 3 がサポートされています

### バージョン 3.2.78.0
*リリース日: 2018 年 12 月 4 日*

このバージョンの Surface Data Eraser:

- バグ修正を含む


### バージョン 3.2.75.0
*リリース日: 2018 年 11 月 12 日*

このバージョンの Surface Data Eraser:

- Surface Studio 2 のサポートを追加
- SD カードの問題を修正

### バージョン 3.2.69.0
*リリース日: 2018 年 10 月 12 日*

このバージョンの Surface Data Eraser では、次のサポートが追加されています。

- Surface Pro 6
- Surface Laptop 2

### バージョン 3.2.68.0
このバージョンの Microsoft Surface Data Eraser では、以下のサポートが追加されています。

- Surface Go


### バージョン 3.2.58.0
このバージョンの Microsoft Surface Data Eraser では、以下のサポートが追加されています。

- Surface Pro および Surface Laptop デバイス用の追加ストレージ デバイス (ドライブ)


### バージョン 3.2.46.0
このバージョンの Microsoft Surface Data Eraser では、以下のサポートが追加されています。

- Surface Pro LTE Advanced


### バージョン 3.2.45.0

このバージョンの Microsoft Surface Data Eraser では、以下のサポートが追加されています。

- Surface Book 2

- Surface Pro 1TB

   >[!NOTE]
   >Surface Data Eraser v3.2.45.0 以降を使用すると、デバイスに 2 つの個別の 512 GB ボリュームが表示される場合、または Windows 10 の展開またはインストール時にエラーが発生した場合に、1 TB ストレージ オプションで Surface Pro または Surface Laptop デバイスを復元できます 詳しくは、「[Surface Pro モデル 1796 と Surface Laptop 1 TB が 2 台のドライブを表示する](https://support.microsoft.com/help/4046105/surface-pro-model-1796-and-surface-laptop-1tb-display-two-drives)」をご覧ください。


### バージョン 3.2.36.0

このバージョンの Microsoft Surface Data Eraser では、以下のサポートが追加されています。

- Surface Pro

- Surface Laptop

>[!NOTE]
>Microsoft Surface Data Eraser USB ドライブ作成ツールは、Windows 10 S では実行できません。Windows 10 S を実行している Surface Laptop をワイプするには、まず Windows 10 Pro または Windows 10 Enterprise を実行する別のコンピューターで Microsoft Surface Data Eraser USB ドライブを作成する必要があります。
