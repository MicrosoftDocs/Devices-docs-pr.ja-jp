---
title: Microsoft Surface Dock ファームウェア更新プログラム-IT 管理者向けの技術情報
description: この記事では、Microsoft Surface Dock ファームウェア更新プログラムを使用して Surface Dock ファームウェアを更新する方法について説明します。 Surface デバイスにインストールすると、surface デバイスに接続されている Surface Dock が更新されます。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 8/05/2020
ms.openlocfilehash: 331d5122c6c64a99dad48ff6e5a90f38ce3d4ed4
ms.sourcegitcommit: 603bcb41dc1b7dd92d3bab1601fa6336480e1218
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "10916028"
---
# Microsoft Surface Dock ファームウェアの更新: IT 管理者向けの技術情報

> [!IMPORTANT]
> この記事には、IT 管理者向けの技術的な手順が記載されています。 ホームユーザーの場合は、Microsoft サポートサイトで[Surface Dock のファームウェアを更新する方法を](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)参照してください   。 サポートサイトの手順は、以下の一般的なインストール手順と同じですが、この記事には、ネットワーク上の複数のデバイスの更新を監視、確認、展開するための追加情報が記載されています。

この記事では、Microsoft Surface Dock ファームウェア更新プログラムを使用して Surface Dock ファームウェアを更新する方法について説明します。 Surface デバイスにインストールすると、surface デバイスに接続されている Surface Dock が更新されます。 

このツールは、以前は、Surface tool の一部としてダウンロードできる以前の Microsoft Surface Dock アップデーターツールの代わりに使用されます。 以前のツールには Surface_Dock_Updater_vx.xx.xxx.x.msi (x はバージョン番号を示す) という名前が付けられたため、ダウンロードできなくなり、使用できません。

## Surface Dock ファームウェアの更新プログラムをインストールする

このセクションでは、手動でファームウェア更新プログラムをインストールする方法について説明します。

> [!NOTE]
> Microsoft は、Surface Dock ファームウェア更新プログラムの新しいバージョンを定期的にリリースしています。 MSI ファイルが自動更新されていない。 MSI デバイスに MSI デバイスを展開し、ファームウェアの新しいバージョンがリリースされている場合は、新しいバージョンを展開する必要があります。

1. [Microsoft Surface Dock ファームウェアの更新プログラム](https://www.microsoft.com/download/details.aspx?id=46703)をダウンロードしてインストールします。
    - 更新プログラムでは、Windows 10 バージョン1803以降を搭載した Surface デバイスが必要です。
    - MSI ファイルをインストールすると、Surface を再起動するように求められる場合があります。 ただし、更新を実行するために再起動は必要ありません。

2. Surface Dock から Surface デバイスを切り離し (電源アダプターを使用)、最大5秒間待ってから再接続します。 Surface Dock ファームウェアの更新により、Dock がバックグラウンドで自動的に更新されます。 処理が完了するまで数分かかることがあり、中断された場合でも続行されます。 

## Surface Dock ファームウェアの更新を監視する

このセクションはオプションであり、ファームウェア更新プログラムのインストールを監視する方法の概要を説明します。 

更新プログラムを監視するには:

1. イベントビューアーを開き、[ **Windows ログ**] を参照し > アプリケーション] を参照して、右側のウィンドウの [**アクション**] で [**現在のログをフィルター**] をクリックし、[**イベントソース**] の横に**SurfaceDockFwUpdate**と入力して、[ **OK]** をクリックします。

2. 昇格されたコマンドプロンプトで次のコマンドを入力します。

    ```cmd
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. この記事の[次のセクション](#install-the-surface-dock-firmware-update)で説明するように、更新プログラムをインストールします。
4. 次のテキストが表示されたイベント2007は、ファームウェアの更新が完了したことを示し**ます。 DriverTelementry EventCode = 2007**。 
    - 更新に失敗した場合、イベント ID 2007 は**情報**ではなく**エラー**イベントとして表示されます。 さらに、Windows レジストリで報告されたバージョンは最新のものではありません。
5. 更新が完了すると、更新された DWORD 値が、ツールの現在のバージョンに対応する Windows レジストリに表示されます。 詳細については、この記事の「[バージョンのリファレンス](#versions-reference)」セクションを参照してください。 次に、例を示します。
    - Component10CurrentFwVersion 0x04ac3970 (78395760)
    - Component20CurrentFwVersion 0x04915a70 (76634736)

>[!TIP]
>イベントテキストに "ソース SurfaceDockFwUpdate のイベント ID xxxx の説明が見つかりません" と表示される場合は、これは予期されており、無視できます。

この記事の次のセクションも参照してください。 
  - [ファームウェア更新プログラムの完了を確認する方法](#how-to-verify-completion-of-the-firmware-update)
  - [イベントログ](#event-logging)
  - [トラブルシューティングのヒント](#troubleshooting-tips)
  - [バージョンリファレンス](#versions-reference)

## ネットワーク展開

Windows Installer コマンド (Msiexec.exe) を使って、ネットワーク上の複数のデバイスに Surface Dock ファームウェア更新プログラムを展開することができます。 Microsoft Endpoint Configuration Manager またはその他の展開ツールを使用している場合は、次の構文を入力して、インストールがサイレントモードであることを確認します。

- **Msiexec.exe/i \<path to msi file\> /quiet/norestart** 

  次に、例を示します。
  ```
  msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
  ```

  > [!NOTE]
  > 既定では、ログファイルは作成されません。 ログファイルを作成するには、"/l*v [path]" を追加する必要があります。例: Msiexec.exe/i \<path to msi file\> /l*v%windir%\logs\ SurfaceDockFWI "

  詳細については、「[コマンドラインオプション](https://docs.microsoft.com/windows/win32/msi/command-line-options)のドキュメント」を参照してください。

> [!IMPORTANT]
> 他の方法を使用して Surface Dock を更新したままにする場合は、「 [Surface dock の更新](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)」を参照してください。

## Intune の展開

Intune を使用して、Surface Dock ファームウェアの更新プログラムをデバイスに配布することができます。 最初に、次のドキュメントで説明されているように、MSI ファイルを、次の「 [Intune Standalone-Win32 アプリ管理](https://docs.microsoft.com/intune/apps/apps-win32-app-management)」という形式で変換する必要があります。

次のコマンドを使用します。
  - **msiexec/i \<path to msi file\> /quiet/q**

## ファームウェア更新プログラムの完了を確認する方法

Surface dock ファームウェアは、次の2つのコンポーネントで構成されています。

- **Component10:** マイクロコントローラーユニット (MCU) ファームウェア
- **Component20:** ディスプレイポート (DP) ファームウェア。

Surface Dock のファームウェア更新が正常に完了すると、これらのファームウェアコンポーネントの新しいレジストリキー値が表示されます。

**更新を確認するには:**

1. Regedit を開き、次のレジストリパスに移動します。

    - **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters**

2. **Component10CurrentFwVersion と Component20CurrentFwVersion**のレジストリキーを探します。これは、現在デバイス上にあるファームウェアを指します。

   ![Surface Dock ファームウェア更新プログラムのインストールプロセス](images/regeditDock.png)

3. 新しいレジストリキーの値が、このドキュメントの最後のバージョン参照で示されている更新されたレジストリキー値と一致することを確認します。 値が一致する場合、ファームウェアは正常に更新されました。

4. 確認できない場合は、次のセクションのイベントログとトラブルシューティングのヒントを確認してください。

## イベントログ

**表 1. Surface Dock ファームウェア更新プログラムのログファイル**

| Log                              | Location                               | 備考                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface Dock ファームウェア更新ログ | Path を指定する必要があります (注を参照)。 | このツールの以前のバージョンでは、Logs\Microsoft Surface Dock アップデーターにイベントが書き込まれました。                                                                                                  |
| Windows デバイスのインストールログ       | %windir%\inf\setupapi.dev.log           | デバイスインストールログの使用について詳しくは、「[ [Setupapi.log Logging](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) ] のドキュメント」をご覧ください。 |


**表 2. Surface Dock ファームウェア更新プログラムのイベントログ Id**<br>
イベントは、アプリケーションイベントログに記録されます。  注: このツールの以前のバージョンでは、Logs\Microsoft Surface Dock アップデーターにイベントが書き込まれています。

| イベント ID | イベントの種類                                                           |
| -------- | -------------------------------------------------------------------- |
| 2001     | Dock ファームウェアの更新が開始されました。                                    |
| 2002     | Dock が最新であることがわかっているため、dock ファームウェアの更新はスキップされました。 |
| 2003     | Dock ファームウェアの更新でファームウェアのバージョンを取得できませんでした。                 |
| 2004     | ファームウェアバージョンの照会。                                       |
| 2005     | Dock ファームウェアの更新を開始できませんでした。                                |
| 2006     | オファー/ペイロードのペアを送信できませんでした。                                  |
| 2007     | ファームウェアの更新が完了しました。                                            |
| 2008     | Dock テレメトリを開始します。                                                |
| 2011     | Dock のテレメトリを終了します。                                                  |

## トラブルシューティングのヒント

- Surface dock の電源を AC 電源から完全に切断して、Surface Dock をリセットします。
- Surface Dock 以外のすべての周辺機器の接続を解除します。
- 現在の Surface Dock ファームウェア更新プログラムをアンインストールして、最新バージョンをインストールします。
- Surface Dock が切断されていることを確認し、Dock のイーサネットポートの LED を使って、更新が監視されるまで十分な時間を確保します。 電源から Surface Dock を取り外す前に、LED が点滅しなくなるまで待ちます。
- Surface Dock を別のデバイスに接続して、dock を更新できるかどうかを確認します。

## バージョンリファレンス

>[!NOTE]
>インストールファイルは、次の名前付け形式でリリースされます。 **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ex: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) と既定では C:\Program Files\SurfaceUpdate. にインストールします。

### バージョン1.53.139.0
*リリース日: 2020 年8月4日*

このバージョンの Surface Dock ファームウェア更新プログラムには、次のようなバグ修正とサポートが含まれています。
- Surface Pro X を使用した Surface Dock 1 の更新。 
   > [!NOTE]
   > Surface Pro X を実行している場合は、をダウンロードします。ARM64 ビルド。 その他のすべてのデバイスについては、AMD64 ビルドを使用します。 
 


### バージョン1.42.139 
*リリース日:18 2019 年9月*

このバージョンは Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI に含まれていますが、バックグラウンドでファームウェアを更新しています。 
**更新されたレジストリキー値:**<br>

- Component10CurrentFwVersion は**4ac3970**に更新されました。
- Component20CurrentFwVersion は、 **4a1d570**に更新されました。

Surface Pro 7 と Surface ノート Pc 3 のサポートが追加されます。

## 以前のバージョン

### バージョン2.23.139.0
*リリース日: 2018 年10月10日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

- Surface Pro 6 のサポートを追加する
- Surface ラップトップのサポートを追加する2


### バージョン2.22.139.0
*リリース日: 2018 年7月26日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

- 更新の信頼性を向上させる
- Surface Go のサポートを追加する

### バージョン 2.12.136.0
*リリース日: 2018 年 1 月 29 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。
* Surface ドックのメイン チップセットのファームウェア更新プログラム
* Surface ドックの DisplayPort ファームウェア更新プログラム
* Surface Book 2 または Surface Book で使用する場合の、外部ディスプレイの表示安定性の向上

さらに、Surface Book デバイスにこのバージョンの Surface Dock Updater をインストールした場合、以下の機能も含まれます。
* Surface Book Base Firmware 更新プログラム
* Surface Book デバイスを対象とした機能強化による Surface ドック ファームウェア更新プログラムのサポートの追加


### バージョン 2.9.136.0
*リリース日: 2017 年 11 月 3 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

* Surface ドックの DisplayPort ファームウェア更新プログラム
* パッシブ ディスプレイ ポート アダプター経由でのオーディオの問題を解決します。

### バージョン 2.1.15.0
*リリース日 : 2017 年 6 月 19 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

* Surface Laptop
* Surface Pro

### バージョン 2.1.6.0
*リリース日: 2016 年 4 月 7 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

* Surface ドックの DisplayPort ファームウェア更新プログラム
* Windows 10 が必要

### バージョン 2.0.22.0
*リリース日: 2016 年 10 月 21 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

* Surface ドックの USB ファームウェア更新プログラム
* イーサネット、オーディオ、USB ポートの信頼性の向上

### バージョン 1.0.8.0
*リリース日: 2016 年 4 月 26 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

* Surface ドックのメイン チップセットのファームウェア更新プログラム
* Surface ドックの DisplayPort ファームウェア更新プログラム

