---
title: Microsoft Surface Dock 1 Firmware Update
description: この記事では、Microsoft Surface Dock Firmware Update を使用して、元の Surface Dock 1 にファームウェアをインストールして管理する方法について説明します。 Surface デバイスにインストールすると、Surface デバイスに接続されている Surface Dock 1 デバイスが更新されます。
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
ms.date: 2/08/2021
ms.openlocfilehash: a0acaaf0676c3f4403a2b233297781579ca1f4ae
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319211"
---
# Microsoft Surface Dock Firmware Update

> [!IMPORTANT]
> この記事には、IT 管理者向け技術的な手順が記載されています。 ホーム ユーザーの場合は、Microsoft サポート サイトで[Surface ドックのファームウェア](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)を更新   する方法を参照してください。 サポート サイトの手順は、以下の一般的なインストール手順と同じですが、この記事には、ネットワーク上の複数のデバイスへの更新プログラムの監視、検証、展開に関する追加情報が記載されています。

この記事では、Microsoft Surface Dock Firmware Update を使用して、元の Surface Dock 1 にファームウェアをインストールして管理する方法について説明します。 Surface デバイスにインストールすると、Surface デバイスに接続されている Surface Dock 1 デバイスが更新されます。

> [!NOTE]
> この記事は、Windows Update または Microsoft Endpoint Configuration Manager または他の MSI 展開ツールを使用して自動的に更新プログラムを受信する Surface Dock 2 には適用されません。 詳しくは [、Surface ドックの新機能をご覧ください](surface-dock-whats-new.md)。

このツールは、以前は It 向け Surface Tools の一部としてダウンロード可能だった、以前の Microsoft Surface Dock Updater ツールに取ってかわるツールです。 以前のツールの名前は Surface_Dock_Updater_vx.xx.xxx.x.msi (x はバージョン番号を示します) で、ダウンロードできなくなったので、使用できません。

## Surface ドックのファームウェア更新プログラムをインストールする

このセクションでは、ファームウェア更新プログラムを手動でインストールする方法について説明します。

> [!NOTE]
> Microsoft は、Surface Dock Firmware Update の新しいバージョンを定期的にリリースしています。 MSI ファイルは自己更新ではありません。 MSI を Surface デバイスに展開し、ファームウェアの新しいバージョンがリリースされている場合は、新しいバージョンを展開する必要があります。

1. [Microsoft Surface Dock Firmware Update をダウンロードしてインストールします](https://www.microsoft.com/download/details.aspx?id=46703)。
    - この更新プログラムには、Windows 10 バージョン 1803 以降を実行している Surface デバイスが必要です。
    - MSI ファイルをインストールすると、Surface を再起動するように求めるメッセージが表示される場合があります。 ただし、更新を実行するために再起動する必要はありません。

2. Surface ドックから Surface デバイスを取り外し、5 秒待って再接続します。 Surface ドックのファームウェア更新プログラムは、バックグラウンドでサイレント モードでドックを更新します。 プロセスが完了するには数分かかる場合があります。中断された場合でも続行されます。 

## Surface ドックのファームウェア更新プログラムを監視する

このセクションは省略可能であり、ファームウェア更新プログラムのインストールを監視する方法の概要を示します。 

更新プログラムを監視するには:

1. イベント ビューアーを開き **、Windows Logs > アプリケーション**を参照し****、右側のウィンドウの [操作****] で [現在のログのフィルター処理]**** をクリックし、イベント ソースの横に**SurfaceDockFwUpdate**と入力して **、[OK]** をクリックします。

2. 管理者特権でのコマンド プロンプトで次のコマンドを入力します。

    ```console
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. この記事の次のセクションで説明するように [、更新プログラム](#install-the-surface-dock-firmware-update) をインストールします。

4. 次のテキストを含むイベント 2007 は、更新が正常に完了したかどうかを示します。ファームウェアの更新が完了しました **。hr=0 DriverTelementry EventCode = 2007**。 

   更新に失敗した場合、イベント ID 2007 は情報ではなく **Error** イベントとして **表示されます**。 また、Windows レジストリで報告されているバージョンは最新の状態ではありません。
   
5. 更新が完了すると、更新された DWORD 値が現在のバージョンのツールに対応する Windows レジストリに表示されます。 詳細については [、この記事の「](#versions-reference) バージョンリファレンス」セクションを参照してください。 次に、例を示します。

    - Component10CurrentFwVersion 0x04ac3970 (78395760)
    - Component20CurrentFwVersion 0x04915a70 (76634736)

>[!TIP]
>イベント テキストに 「ソース SurfaceDockFwUpdate のイベント ID xxxx の説明が見つかりません」と表示される場合、これは予期される値であり、無視してもかまいません。

この記事の以下のセクションも参照してください。 
  - [ファームウェア更新の完了を確認する方法](#how-to-verify-completion-of-the-firmware-update)
  - [イベント ログ](#event-logging)
  - [トラブルシューティングのヒント](#troubleshooting-tips)
  - [バージョン リファレンス](#versions-reference)

## ネットワーク展開

Windows インストーラー コマンド (Msiexec.exe) を使って、Surface Dock Firmware Update をネットワーク上の複数のデバイスに展開できます。 Microsoft Endpoint Configuration Manager または他の展開ツールを使用する場合は、次の構文を入力してインストールがサイレント モードに設定されます。

- **Msiexec.exe /i \<path to msi file\> /quiet /norestart** 

次に、例を示します。

```console
msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
```

> [!NOTE]
> ログ ファイルは既定では作成されません。 ログ ファイルを作成するには、"/l*v [path]" を追加する必要があります。例: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"

詳細については、コマンド ライン オプション [のドキュメントを参照](https://docs.microsoft.com/windows/win32/msi/command-line-options) してください。

> [!IMPORTANT]
> 他の方法で Surface ドックを最新の状態に保つ場合は [、「Surface ドック](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) の更新」を参照してください。

## Intune の展開

Intune を使って Surface ドックのファームウェア更新プログラムをデバイスに配布できます。 まず、次のドキュメントで説明するように、MSI ファイルを .intunewin 形式に変換する [必要があります。Intune スタンドアロン - Win32 アプリ管理](https://docs.microsoft.com/intune/apps/apps-win32-app-management)。

次のコマンドを使用します。
  - **msiexec /i \<path to msi file\> /quiet /q**

## ファームウェア更新プログラムの完了を確認する方法

Surface ドックのファームウェアは、次の 2 つのコンポーネントで構成されています。

- **Component10:** マイクロ コントローラー ユニット (MCU) ファームウェア
- **Component20:** ディスプレイ ポート (DP) ファームウェア。

Surface Dock Firmware Update が正常に完了すると、これらのファームウェア コンポーネントの新しいレジストリ キー値が生成されます。

**更新プログラムを確認するには:**

1. Regedit を開き、次のレジストリ パスに移動します。

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters**

2. 次のレジストリ キーを探します **。Component10CurrentFwVersion と Component20CurrentFwVersion**は、デバイスに現在インストールされているファームウェアを参照します。

   ![Surface ドックファームウェア更新プログラムのインストール プロセス](images/regeditDock.png)

3. 新しいレジストリ キーの値が、このドキュメントの最後の「バージョン」のリファレンスに記載されている更新されたレジストリ キー値と一致する必要があります。 値が一致する場合、ファームウェアは正常に更新されました。

4. 確認できない場合は、次のセクションでイベント ログとトラブルシューティングのヒントを確認してください。

## イベント ログ

**表 1. Surface Dock Firmware Update のログ ファイル**

| ログ                              | Location                               | 備考                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface ドックのファームウェア更新ログ | パスを指定する必要があります (注を参照) | このツールの以前のバージョンでは、アプリケーションとサービス ログ\Microsoft Surface Dock Updater にイベントが書き込まれます。                                                                                                  |
| Windows デバイス インストール ログ       | %windir%\inf\setupapi.dev.log           | デバイス インストール ログの使用の詳細については [、SetupAPI ログのドキュメントを参照](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) してください。 |


**表 2. Surface ドックファームウェア更新プログラムのイベント ログの ID**<br>
イベントは、アプリケーション イベント ログに記録されます。  注: このツールの以前のバージョンでは、アプリケーションとサービス ログ\Microsoft Surface Dock Updater にイベントが書き込まれます。

| イベント ID | イベントの種類                                                           |
| -------- | -------------------------------------------------------------------- |
| 2001     | ドックのファームウェア更新が開始されました。                                    |
| 2002     | ドックのファームウェアの更新は、ドックが最新の情報として知られているため、スキップされました。 |
| 2003     | ドックのファームウェア更新プログラムがファームウェアのバージョンを取得できなかった。                 |
| 2004     | ファームウェアバージョンの照会。                                       |
| 2005     | ドックのファームウェアが更新を開始できなかった。                                |
| 2006     | オファーとペイロードのペアの送信に失敗しました。                                  |
| 2007     | ファームウェアの更新が完了しました。                                            |
| 2008     | BEGIN ドックの利用統計情報。                                                |
| 2011     | END ドックの利用統計情報。                                                  |

## トラブルシューティングのヒント

- Surface ドックの電源を AC 電源から完全に取り外して、Surface ドックをリセットします。
- Surface ドック以外のすべての周辺機器を取り外します。
- 現在の Surface Dock Firmware Update をアンインストールし、最新バージョンをインストールします。
- Surface ドックが取り外され、ドックのイーサネット ポートの LED を介して監視された状態で更新が完了するのに十分な時間を確保します。 Surface ドックの電源を取り外す前に、LED が点滅し始めるまで待ちます。
- Surface ドックを別のデバイスに接続して、ドックを更新することができるか確認します。

## バージョン リファレンス

>[!NOTE]
>インストール ファイルは、Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi ** など) の名前付け形式でリリースされ、既定では C:\Program Files\SurfaceUpdate にインストールされます。

### バージョン 1.53.139.0
*リリース日: 2020 年 8 月 4 日*

このバージョンの Surface Dock Firmware Update には、次のバグ修正プログラムとサポートが含まれています。
- Surface Pro X を使った Surface ドック 1 の更新。 
   > [!NOTE]
   > Surface Pro X を実行している場合は、次をダウンロードします。ARM64 ビルド。 その他すべてのデバイスでは、AMD64 ビルドを使います。 

#### レジストリ キーの値

ファームウェア更新プログラムの状態を示すレジストリ値は、このツールの以前のバージョンから変更されていません。 

- Component10CurrentFwVersion を **4ac3970 に更新しました**。
- Component20CurrentFwVersion を **4a1d570**に更新しました。
 
### バージョン 1.42.139 
*リリース日: 2019 年 9 月 18 日*

このバージョンは、Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSIに含まれている場合に、ファームウェアを更新します。 

#### レジストリ キーの値の更新

- Component10CurrentFwVersion を **4ac3970 に更新しました**。
- Component20CurrentFwVersion を **4a1d570**に更新しました。

Surface Pro 7 と Surface Laptop 3 のサポートが追加されました。

## レガシ バージョン

### バージョン 2.23.139.0
*リリース日: 2018 年 10 月 10 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

- Surface Pro 6 のサポートを追加する
- Surface Laptop 2 のサポートを追加する


### バージョン 2.22.139.0
*リリース日: 2018 年 7 月 26 日*

このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。

- 更新の信頼性を高める
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

