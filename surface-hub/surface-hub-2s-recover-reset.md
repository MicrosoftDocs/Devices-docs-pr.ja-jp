---
title: Surface Hub 2S のリセットと回復
description: Surface Hub 2S を復元およびリセットする方法について説明します。
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
ms.openlocfilehash: 7d79fab22b62e6ef29832be6241c484e9caf72e0
ms.sourcegitcommit: 537fa38bdd21fcd679af0764e734f4b8efb6a03f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "10959949"
---
# Surface Hub 2S のリセットと回復

Surface Hub 2S で問題が発生した場合は、デバイスを出荷時の設定にリセットするか、USB ドライブを使って復元することができます。

開始するには、管理者の資格情報で Surface Hub 2S にサインインし、[ **設定** ] アプリを開き、[ **更新 & のセキュリティ**] を選択して、[ **回復**] を選びます。

## デバイスをリセットする

1. デバイスをリセットするには、[ **はじめ**に] を選びます。

2. [ **このデバイスをリセットする準備ができ** ました] ウィンドウが表示されたら、[ **リセット**] を選びます。 
  
   > [!NOTE]
   > Surface Hub 2S 回復パーティションからオペレーティングシステムを再インストールします。 完了までに最長で1時間かかることがあります。
  
3. デバイスを再構成するには、1回目のセットアッププログラムを実行します。

4. Microsoft Intune または他のモバイルデバイス管理ソリューションを使用してデバイスを管理している場合は、以前のレコードを削除してから、新しいデバイスを再登録します。 詳細については、「 [デバイスのワイプまたは削除を使用してデバイスを削除する」または「手動でデバイスを登録解除する](https://docs.microsoft.com/intune/devices-wipe)」を参照してください。

> [!div class="mx-imgBorder"]
> ![* Surface Hub 2S のリセットと回復 *](images/sh2-reset.png)
<br/>*図 1.  Surface Hub 2S のリセットと回復* 

## USB 回復ドライブを使用して Surface Hub 2S を回復する

Surface Hub 2S の新機能により、回復イメージを使用してデバイスを再インストールできるようになりました。

### USB ドライブからの回復

Surface Hub 2S を使って、回復イメージを使用してデバイスを再インストールできます。 これにより、BitLocker キーを紛失した場合、または設定アプリの管理者資格情報がなくなった場合に、デバイスを出荷時の設定に再インストールできます。

>[!NOTE]
>8 GB または 16 GB のストレージで、FAT32 として書式設定された USB 3.0 ドライブを使用します。

1. 別の PC から、 [Surface recovery web サイト](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) から .zip ファイルの回復イメージをダウンロードして、次の手順に戻ります。 

1. ダウンロードしたファイルを USB ドライブのルートに解凍します。  

1. Usb ドライブを USB-C または USB に接続します (Surface Hub 2S の場合)。

1. デバイスをオフにします。

   1. 音量を上げるボタンを押しながら、電源ボタンを押します。
   1. Windows ロゴが表示されるまで、両方のボタンを押し続けます。
   1. 電源ボタンを放しますが、インストール UI が開始されるまでは [音量を上げる] ボタンを押し続けます。

   ![* ボリュームダウンと電源ボタンを使用して回復 * を開始 *](images/sh2-keypad.png) <br>
   **図 2.  ボリュームと電源ボタン**

1. [言語の選択] 画面で、Surface Hub 2S の表示言語を選択します。

1. [ **ドライブからの回復** ] を選択し、 **ドライブを完全にクリーンアップ**して、[ **復元**] を選択します。 BitLocker キーの入力を求めるメッセージが表示されたら、[ **このドライブをスキップ**] を選択します。 Surface Hub 2S は何度か再起動します。回復処理が完了するまでに約30分かかります。

初回起動時のセットアップ画面が表示されたら、USB ドライブを削除します。

## サポートに問い合わせ

質問がある場合やヘルプが必要な場合は、 [サポートリクエストを作成](https://support.microsoft.com/supportforbusiness/productselection)できます。
