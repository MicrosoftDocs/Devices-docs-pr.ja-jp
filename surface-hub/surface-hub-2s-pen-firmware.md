---
title: Surface Hub 2S のペン ファームウェアを更新する
description: このページでは、2 ペンのファームウェアを更新Surface Hub説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 04/15/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 6f1ca4f05653ec798ed1b47d2e42e974e7f7414d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576957"
---
# <a name="update-pen-firmware-on-surface-hub-2s"></a>Surface Hub 2S のペン ファームウェアを更新する

ファームウェアは、Surface Hub 2 ペンWindowsから、または別の PC にファームウェア更新プログラムをダウンロードして更新できます。 更新されたファームウェアは、2020 Windows 2 月 26 日から更新プログラムから利用できます。 

## <a name="update-pen-firmware-using-windows-update-for-business"></a>Update for Business を使用してペンWindowsを更新する

このセクションでは、Windows Update の自動メンテナンス サイクルを使用してペン ファームウェアを更新する方法について説明します。既定では、夜間 3 時に発生するように構成されています。 更新プログラムを 2 ペンに適用する前に、2 つのメンテナンス サイクルを完了Surface Hub必要があります。 または、他の更新プログラムと同様に、Windows Update for Business (WUfB) を使用してペン ファームウェアを適用できます。 詳細については、「更新プログラムの[管理」をWindowsを参照Surface Hub。](manage-windows-updates-for-surface-hub.md)

1. Surface Hub 2 ペンが Surface Hub 2S にペアリングされている必要があります。白いインジケーター **** LED ライトが点滅し始めるまで、トップ ボタンを長押しします。 <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. このSurface Hub管理者としてログインし、**新しいデバイス**設定開き、新しいデバイスBluetoothします。
3. ペンを選択してペアリングプロセスを完了します。
4. ペンの **上ボタン** を押して更新プログラムを適用します。 完了には最大 2 時間かかる場合があります。

## <a name="update-pen-firmware-by-downloading-to-separate-pc"></a>個別の PC にダウンロードしてペンのファームウェアを更新する

2 ペンのファームウェアは、Surface Hub実行している別の PC から更新Windows 10。 また、このメソッドを使用すると、ペン のファームウェアが最新バージョンに正常に更新されたことを確認できます。

1. Surface Hub 2 ペンを Bluetooth 対応 PC とペアリングします。白いインジケーター LED**** ライトが点滅し始めるまで、トップ ボタンを長押しします。 <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. PC で、新しいデバイスをBluetoothします。
3. ペンを選択してペアリングプロセスを完了します。
4. 新しい更新プログラムをSurface Hubする前に、他のすべての 2s ペンを切断します。
3. PC に[Surface Hub 2 ペン ファームウェア更新ツール](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip)をダウンロードします。
4. 実行 **PenCfu.exe。** インストールの進行状況がツールに表示されます。 更新が完了するために数分かかる場合があります。 


## <a name="check-firmware-version-of-surface-hub-2-pen"></a>2 ペンのファームウェア バージョンSurface Hub確認する

1. **[get_version.bat**を実行し、ペンの**上**ボタンを押します。
2. ツールは、ペンのファームウェア バージョンを報告します。 例:
    - 古いファームウェアは 468.2727.368 です
    - 新しいファームウェアは 468.3347.368 です

## <a name="command-line-options"></a>コマンド ライン オプション

コマンド ラインから Surface Hub 2 ペン ファームウェア更新ツール (PenCfu.exe) を実行できます。

1. ペンを PC にペアリングし、ペンの **上ボタン** をクリックします。
2. [ファームウェアの更新 **PenCfu.exe** を開始するには、[次へ] をダブルクリックします。 構成ファイルとファームウェア イメージ ファイルは、ツールと同じフォルダーに格納する必要があります。
3. その他のオプションについては ** 、PenCfu.exe -h** を実行して、次の表に示す使用可能なパラメーターを表示します。  
    - 例: PenCfu.exe -h
4. ツール **を安全にシャットダウンするには、Ctrl** + C と入力します。

 

| **コマンド**    | **説明**                                                                                                                                                                                                                                                                                                                                                                                |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -h ヘルプ        | 表示ツールのコマンド ライン インターフェイスのヘルプと終了。                                                                                                                                                                                                                                                                                                                                             |
| -v バージョン     | 表示ツールのバージョンと終了。                                                                                                                                                                                                                                                                                                                                                                 |
| -l ログ フィルター  | ログ ファイルのフィルター レベルを設定します。 ログ メッセージには、DEBUG (最下位)、INFO、WARNING、ERROR (最も高い) の 4 つのレベルがあります。 ログ フィルター レベルを設定すると、ログ メッセージは同じレベル以上のメッセージにのみフィルター処理されます。 たとえば、フィルター レベルが WARNING に設定されている場合、警告メッセージとエラー メッセージだけがログに記録されます。 既定では、このオプションは OFF に設定され、ログが無効になります。 |
| -g get-version | 指定した場合、ツールは、ツールと同じフォルダーに格納されている構成ファイルに一致する接続されているペンの FW バージョンのみを取得します。                                                                                                                                                                                                                                    
