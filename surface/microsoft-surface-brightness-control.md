---
title: Surface の明るさの制御
description: このトピックでは、Surface 明度コントロールアプリを使用して、pos とキオスクのシナリオでディスプレイの明るさを管理する方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 197ed9fe1abc880779ad6bb0f85d2970086395f6
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835806"
---
# Surface の明るさの制御

販売時点またはその他の "常時オン" のキオスクシナリオで Surface デバイスを展開する場合は、新しい Surface 輝度コントロールアプリを使用して、電源管理を最適化することができます。

[Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703)を使ってダウンロードできます。
Surface 輝度コントロールは、熱荷重を軽減し、展開された Surface デバイスの全体的な二酸化炭素排出量を削減するために設計されています。
このツールのみをダウンロードページから入手する予定の場合は、利用可能なリストで**Surface_Brightness_Control_v1.16.137.0.msi**ファイルを選択します。
このツールは、使用されていないときに自動的に画面を暗くします。次の設定オプションが含まれています。

- 画面を暗くするまでの非アクティブな時間。

- 明るさのレベルは淡色表示されます。

- 使用中の最大輝度レベル。

**Surface 輝度コントロールを実行するには:**

- ターゲットデバイスに surfacebrightnesscontrol.msi をインストールすると、[Surface 輝度] コントロールはすぐに機能し始めます。

## Surface 輝度コントロールの構成

既定の値は、Windows レジストリを使って調整できます。 Windows レジストリの使用の詳細については、[レジストリのドキュメント](https://docs.microsoft.com/windows/desktop/sysinfo/registry)を参照してください。

1.  コマンドプロンプトから regedit を実行して、Windows レジストリエディターを開きます。
    
      - Computer\HKEY\ _LOCAL \ _MACHINE \SOFTWARE\WOW6432Node\Microsoft\Surface\Surface 輝度コントロール \ 
    
    以前のバージョンの Surface 明度コントロールを実行している場合は、代わりに次のコマンドを実行します。
    
      - Computer\HKEY\ _LOCAL \ _MACHINE \SOFTWARE\Microsoft\Surface\Surface 輝度コントロール \


| レジストリ設定 | データ| 説明  
|-----------|------------|---------------
| 輝度コントロールが有効  |  既定値:01  <br> オプション:01、00 <br> 「REG_BINARY」と入力します。 |  この設定により、表面の輝度調整を有効または無効にすることができます。 表面の明るさの制御を無効にするには、値を00に設定します。 この設定を構成しない場合、Surface 輝度コントロールはオンになります。 |
| Power Enabled の輝度コントロール| 既定値:01 <br> オプション:01、00 <br> 「REG_BINARY」と入力します。 | この設定では、デバイスが直接電源に接続されているときに表面の輝度調整をオフにすることができます。 電源が接続されているときに表面の輝度コントロールを無効にするには、値を00に設定します。 この設定を構成しない場合、Surface 輝度コントロールはオンになります。 |
| 淡色表示の明るさ   | 既定値:20  <br>オプション: 画面の明るさの0-100% の範囲 <br> データ型: 正の整数 <br> 「REG_DWORD」と入力します。 | この設定を使用すると、非アクティブな時間帯に明るさの範囲を管理することができます。 この設定を構成しない場合、明るさのレベルは、アイドル状態が30秒続いたときの完全な輝度の20% に低下します。 |
すべての明るさ   | 既定値: 100  <br>オプション: 画面の明るさの0-100% の範囲 <br> データ型: 正の整数 <br> 「REG_DWORD」と入力します。  | この設定では、デバイスの最大輝度範囲を管理することができます。 この設定を構成しない場合、最大輝度範囲は100パーセントになります。|  
| 無通信タイムアウト| 既定値:30 秒 <br>オプション: 任意の数値  <br>データ型: 整数  <br> 「REG_DWORD」と入力します。 | この設定では、デバイスを淡色表示する前に、非アクティブな状態の期間を管理することができます。 この設定を構成しない場合、非アクティブなタイムアウトは30秒です。|
| テレメトリが有効 | 既定値:01 <br>オプション:01、00 <br> 「REG_BINARY」と入力します。  | この設定では、アプリの使用状況情報の共有を管理して、ソフトウェアを向上させ、ユーザーエクスペリエンスを向上させることができます。 テレメトリを無効にするには、値を00に設定します。 この設定を構成しない場合、利用統計情報は microsoft のプライバシーに関する[声明](https://privacy.microsoft.com/privacystatement)に従って microsoft と共有されます。 |

## 変更と更新

### バージョン1.16.137<br>
*リリース日: 2019 年10月22日*<br>
このバージョンの Surface 明度コントロールでは、次のサポートが追加されます:-x86 用の再コンパイル。 Surface Pro 7、Surface Pro X、Surface ノート Pc 3 のサポートを追加します。 

### バージョン1.12.239.0
*リリース日: 2019 年4月26日*<br>
このバージョンの Surface 明度コントロールでは、次のサポートが追加されています。
- タッチの遅延が修正されました。


## 関連トピック

- [バッテリー制限の設定](battery-limit.md)
