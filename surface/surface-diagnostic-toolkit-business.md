---
title: ビジネス向け Surface 診断ツールキットを展開する
description: このトピックでは、Surface Diagnostic Toolkit for Business の使い方について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 01/15/2021
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 227463e484a6f3b933fc1118d9dec058f93074a8
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271581"
---
# ビジネス向け Surface 診断ツールキットを展開する

Microsoft Surface Diagnostic Toolkit for Business (SDT) を使用すると、IT 管理者は Surface デバイスに関するハードウェア、ソフトウェア、ファームウェアの問題をすばやく調査、トラブルシューティング、解決できます。 デバイスの正常性に関する分析情報や問題を解決するためのガイダンスを取得する以外に、さまざまな診断テストとソフトウェア修復を実行できます。 

具体的には、SDT for Business を使用すると、次の操作を実行できます。

- [パッケージをカスタマイズします。](#preparing-the-sdt-package-for-distribution)
- [コマンドを使ってアプリを実行します。](surface-diagnostic-toolkit-command-line.md)
- [複数のハードウェア テストを実行して問題をトラブルシューティングします。](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [問題を分析するためのログを生成します。](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [デバイスと最適な構成を比較して詳細なレポートを取得します。](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## 主なシナリオとダウンロード リソース 

SDT for Business を実行するには、次の表に示すコンポーネントをダウンロードします。


モード |  主なシナリオ | ダウンロード | 詳細情報
--- | --- | --- | ---
デスクトップ モード |  ユーザーが Surface デバイスで SDT を実行して問題のトラブルシューティングを行うのを支援します。<br>1 つ以上の Surface デバイスに展開するカスタム パッケージを作成すると、ユーザーは特定のログを選択して収集および分析できます。 | SDT 配布可能 MSI パッケージ:<br>Microsoft Surface Diagnostic Toolkit for Business インストーラー<br>[IT 担当者向け Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703) | [デスクトップ モードで Surface Diagnostic Toolkitを使用する](surface-diagnostic-toolkit-desktop-mode.md)
コマンド ライン |  Configuration Manager などの標準ツールを使用して、ユーザーの操作なしにリモートで Surface デバイスを直接トラブルシューティングします。 これには、次のコマンドが含まれます。<br>`-DataCollector` すべてのログ ファイルを収集します<br>`-bpa` ベスト プラクティス アナライザーを使用して正常性診断を実行します。<br>`-windowsupdate` ファームウェアまたはドライバーの更新プログラムが見つからないか Windows Update をチェックします。<br>`-warranty` 保証情報を確認します。 <br><br>| SDT コンソール アプリ:<br>Microsoft Surface Diagnostics アプリ コンソール<br>[IT 担当者向け Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703) | [コマンドを使用して Surface 診断Toolkitを実行する](surface-diagnostic-toolkit-command-line.md)

##  <a name="supported-devices"></a>サポートされるデバイス 

SDT for Business は、次の Surface 3 以降のデバイスでサポートされています。

- Surface Book - すべての世代
- Surface Go - すべての世代
- Surface Laptop - すべての世代
- Surface Pro 3 以降
- Surface Pro X - すべての世代
- Surface Studio - すべての世代
- Surface 3 LTE
- Surface 3


## Surface Diagnostic Toolkit for Business のインストール

組織内のユーザーに配布できる SDT パッケージを作成するには、

1. 管理者アカウントを使用して Surface デバイスにサインインします。
2. IT 向け [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) のダウンロード ページから SDT Windows インストーラー パッケージ (.msi) をダウンロードし、デスクトップなどの Surface デバイスの優先する場所にコピーします。
3. 図 1 に示すように、SDT セットアップ ウィザードが表示されます。 **[次へ]** をクリックします。 

    >[!NOTE]
    >セットアップ ウィザードが表示されない場合は、コンピューターの Administrator アカウントにサインインしている必要があります。 

    ![Surface Diagnostic Toolkit セットアップ ウィザードへようこそ](images/sdt-1.png)

    *図 1.  Surface Diagnostic Toolkit セットアップ ウィザード*

4. SDT セットアップ ウィザードが表示されたら、[次へ] **をクリックし**、使用許諾契約書 (EULA) に同意します。

5. [インストール オプション] 画面で、必要に応じて既定のインストール場所を変更します。 
6. [セットアップの種類] で、[詳細設定] を **選択します**。 

    >[!NOTE]
    >標準オプションでは、管理者アカウントを使用してデバイスにサインインしている場合、ユーザーは Surface デバイスで直接診断ツールを実行できます。 
    
     ![インストール オプション: 詳細](images/sdt-install.png)

7. [次 **へ] をクリック** し、[インストール] を **クリックします**。 

## コマンド ラインを使用したインストール
必要に応じて、コマンド プロンプトで SDT をインストールし、カスタム フラグを設定して管理モードでツールをインストールできます。 SDT には、次のインストール オプション フラグが含まれます。

- `SENDTELEMETRY` 利用統計情報を Microsoft に送信します。 フラグは無効または `0` 有効を `1` 受け入れる。 既定値は利用統計情報 `1` を送信します。
- `ADMINMODE` 管理モードでインストールするツールを構成します。 このフラグは、クライアント `0` モードまたは `1` IT 管理者モードに対して受け入れ可能です。 既定値は、`0` です。

### コマンド ラインから SDT をインストールするには、次の手順を実行します。

1. コマンド プロンプトを開き、次のコマンドを入力します。

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **例:**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## Surface デバイスでの SDT の検索

SDT と SDT アプリ コンソールの両方がインストールされます `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` 。

図 2 に示すように、SDT は .exe ファイルに加えて、JSON ファイルと admin.dll ファイル (modules\admin.dll) をインストールします。

![エクスプローラーにインストールされている SDT ファイルの一覧](images/sdt-2.png)

*図 2.  SDT によってインストールされるファイル*

## 配布用の SDT パッケージの準備

カスタム パッケージを作成すると、特定の既知の問題をツールのターゲットに設定できます。

1. [ **スタート] ボタン>実行] を**クリックし **、「Surface」** と入力して **、[Surface Diagnostic Toolkit for Business] をクリックします**。 
2. ツールが開いたら、図 3 に示 **すように**[カスタム パッケージの作成] をクリックします。

    ![カスタム パッケージ の作成オプション](images/sdt-3.png)

    *図 3.  カスタム パッケージを作成する*

### 言語と利用統計情報の設定

  パッケージを作成する場合は、言語設定を選択するか、利用統計情報の Microsoft への送信をオプトアウトできます。 既定では、SDT は、Microsoft のプライバシーに関する声明に従って、アプリケーションの改善に使用される利用統計情報を Microsoft に [送信します](https://privacy.microsoft.com/privacystatement)。 拒否する場合は、次に示すように、カスタム パッケージを作成するときにチェック ボックスをオフにします。 または、SDT セットアップ中に [インストール**** オプション] ページの **[Microsoft**に利用統計情報を送信する] チェック ボックスをオフにします。 

>[!NOTE]
>この設定は、Windows Update やソフトウェアの修復など、インターネット接続が必要なテストと修復を実行する場合や、アプリ ツール バーの [にこぼれ] ボタンまたは [Frown] ボタンを使用してフィードバックを提供する場合に、Microsoft サーバーに自動的に保存される最小限の利用統計情報には影響しません。 


![言語と利用統計情報の設定を選択する](images/sdt-4.png)

*図 4:  言語と利用統計情報の設定を選択する*


### Windows Update ページ

組織に適したオプションを選択します。 図 5 に示すように、複数のユーザーを持つほとんどの組織では、通常、Windows Server Update Services (WSUS) 経由で更新プログラムを受信します。 ローカルの Windows Update パッケージまたは WSUS を使う場合は、必要に応じてパスを入力します。 

![Windows Update オプションの選択](images/sdt-5.png)

*図 5:  Windows Update オプション*

### ソフトウェア修復ページ

これにより、ソフトウェア修復の更新を実行するオプションを選択または削除できます。 

![ソフトウェア修復オプションの選択](images/sdt-6.png)

*図 6.  ソフトウェア修復オプション*

### ログの収集とパッケージ の保存ページ

さまざまなアプリケーション、ドライバー、ハードウェア、オペレーティング システムでさまざまなログを実行できます。 該当する領域をクリックし、使用可能なログのメニューから選択します。 その後、ユーザーがアクセスできるソフトウェア配布ポイントまたは同等の場所にパッケージを保存できます。 

![ログ オプションの選択](images/sdt-7.png)

*図 7. ログ オプションとパッケージの保存*

## 次のステップ

- [ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する](surface-diagnostic-toolkit-desktop-mode.md)
- [コマンドを使用して Surface Diagnostic Toolkit for Business を使用する](surface-diagnostic-toolkit-command-line.md)

##  <a name="changes-and-updates"></a>変更と更新

### バージョン 2.131.139.0

このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。

- Surface Pro 7+ のサポート
- Surface Pro X でのシームレスなサポート エクスペリエンス
- セキュリティの強化
- 包括的なユーザー エクスペリエンスの向上

### バージョン 2.124.139.0

このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。

- シームレスな統合サポート
- すべてのテスト結果を保存する
- イメージがカスタム作成されたのか確認する
- デバイス マネージャーからの警告を含める
- ドックのファームウェアのバージョン
- ストレージ テストで発生する可能性がある障害としてドライブにフラグを設定する
- ストアリンクを削除する 

### バージョン 2.121.139
*リリース日: 2020 年 7 月 31 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。

- シームレスなサポート エクスペリエンス
- バグ修正

### バージョン 2.94.139.0
*リリース日: 2020 年 5 月 11 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。

- Windows Update をスキップしてハードウェア チェックを実行する機能。
- 最新バージョンの更新に関する通知を受信する機能
- Surface Go 2
- Surface Book 3
- 進行状況インジケーターを表示する


### バージョン 2.43.139.0
*リリース日: 2019 年 10 月 21 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。

- Surface Pro 7
- Surface Laptop 3

### バージョン 2.42.139.0
*リリース日: 2019 年 9 月 24 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。 
- ハードウェア レポートをダウンロードする機能。
- ツールから直接 Microsoft サポートに問い合わせ可能。 <br>

### バージョン 2.41.139.0
*リリース日: 2019 年 6 月 24 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。 
- ログとレポートに含まれるドライバーのバージョン情報。
- アプリに関するフィードバックを提供する機能。<br>


### バージョン 2.36.139.0
*リリース日: 2019 年 4 月 26 日*<br>
このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。 
- コマンド ライン構成を必要とせずに、インストーラー UI を使用して管理機能をロック解除するための高度なセットアップ オプション。
- アクセシビリティの向上。
- ログに含まれるサーフェスの明るさの制御設定。
- レポート ジェネレーターの外部モニター互換性サポート リンク。
