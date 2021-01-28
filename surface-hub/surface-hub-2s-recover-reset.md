---
title: Surface Hub 2S のリセットと回復
description: Surface Hub 2S を回復してリセットする方法について学習します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/05/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 88f5d912f7505aecaa5bd7ba659acab2d6c4fa1a
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304810"
---
# Surface Hub 2S のリセットと回復

Surface Hub 2S で問題が発生した場合は、デバイスを出荷時の設定にリセットするか、USB ドライブを使用して復元できます。

まず、管理者の資格情報で Surface Hub 2S にサインインし****、設定アプリを**** 開き、[更新とセキュリティ] &を選択して、[回復] を選択**します**。

## デバイスをリセットする

   > [!IMPORTANT]
   > デバイスをリセットする前に、BitLocker キーが利用可能な状態にしてください(後で入力を求めるメッセージが表示されます)。 詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。

1. デバイスをリセットするには、[開始] **を選択します**。

2. When the **Ready to reset this device window** appears, select **Reset**. 
  
   > [!IMPORTANT]
   > ハブが回復パーティションに再起動すると、BitLocker キーの入力を求めるメッセージが表示されます。 このプロンプトをスキップすると、リセットが失敗します。 BitLocker キーを入力すると、Hub は回復パーティションからオペレーティング システムを再インストールします。 完了まで最大 1 時間かかる場合があります。
  
3. デバイスを再構成するには、初回セットアップ プログラムを実行します。

4. Microsoft Intune または別のモバイル デバイス管理ソリューションを使用してデバイスを管理する場合は、前のレコードを廃止して削除してから、新しいデバイスを再登録します。 詳細については、「ワイプ、リタイア、または手動によるデバイスの登録解除を使用してデバイスを削除する」を [参照してください](https://docs.microsoft.com/intune/devices-wipe)。

   > [!div class="mx-imgBorder"]
   > ![*Surface Hub 2S のリセットと回復*](images/sh2-reset.png)
   <br/>*図 1.  Surface Hub 2S のリセットと回復* 

## USB 回復ドライブを使用して Surface Hub 2S を回復する

Surface Hub 2S の新機能として、回復イメージを使用してデバイスを再インストールできます。

### USB ドライブからの回復

Surface Hub 2S を使用すると、回復イメージを使用してデバイスを再インストールできます。 これにより、BitLocker キーを紛失した場合、または設定アプリの管理者資格情報を持たなくなった場合に、デバイスを出荷時の設定に再インストールできます。

>[!NOTE]
>FAT32 としてフォーマットされた 8 GB または 16 GB のストレージを備える USB 3.0 ドライブを使用します。

1. 別の PC から [、Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) Web サイトから .zip ファイルの回復イメージをダウンロードし、次の手順に戻ってください。 

1. ダウンロードしたファイルを USB ドライブのルートに解凍します。  

1. USB ドライブを Surface Hub 2S 上の USB-C ポートまたは USB-A ポートに接続します。

1. デバイスをオフにします。

   1. 音量ボタンを押しながら、電源ボタンを押します。
   1. Windows ロゴが表示されるまで、両方のボタンを押し続けます。
   1. 電源ボタンを離しますが、インストール UI が開始するまで音量を下すボタンを押したままにします。

      ![*ボリューム ダウンボタンと電源ボタンを使用して回復を開始する*](images/sh2-keypad.png)
      <br>*図 2.  音量ボタンと電源ボタン*

1. 言語選択画面で、Surface Hub 2S の表示言語を選択します。

1. Select **Recover from a drive** and **Fully clean the drive,** and then select **Recover**. BitLocker キーの入力を求めるメッセージが表示されたら、[このドライブをスキップする] **を選択します**。 Surface Hub 2S は数回再起動し、回復プロセスが完了するのに約 30 分かかります。

初回セットアップ画面が表示されたら、USB ドライブを取り外します。

## サポートに問い合わせ

質問がある場合やサポートが必要な場合は、サポート [リクエストを作成できます](https://support.microsoft.com/supportforbusiness/productselection)。
