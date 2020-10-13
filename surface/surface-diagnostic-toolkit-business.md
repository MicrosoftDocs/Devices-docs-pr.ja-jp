---
title: ビジネス向け Surface 診断ツールキットを展開する
description: このトピックでは、ビジネス向け Surface 診断ツールキットの使用方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/12/2020
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 1f2661811516507abd432dba602cf8ce81e6dbb3
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114665"
---
# ビジネス向け Surface 診断ツールキットを展開する

Microsoft Surface Diagnostic ツールキット for Business (SDT) を使うと、IT 管理者は Surface デバイスに関するハードウェア、ソフトウェア、ファームウェアの問題をすばやく調査、トラブルシューティング、解決できます。 デバイス正常性の分析や問題解決のガイダンスなど、さまざまな診断テストとソフトウェア修復を実行できます。 

具体的には、SDT for Business で次のことが可能になります。

- [パッケージをカスタマイズします。](#create-custom-sdt)
- [コマンドを使用してアプリを実行します。](surface-diagnostic-toolkit-command-line.md)
- [問題のトラブルシューティングを行うために複数のハードウェアテストを実行します。](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [問題を分析するためのログを生成します。](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [デバイスと最適な構成の比較の詳細レポートを入手します。](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## 主要なシナリオとリソースのダウンロード 

一般法人向けの SDT を実行するには、次の表に示されているコンポーネントをダウンロードします。


モード |  主要なシナリオ | ダウンロード | 詳細情報
--- | --- | --- | ---
デスクトップ モード |  問題のトラブルシューティングを行うために、ユーザーが Surface デバイスで SDT を実行するのを支援します。<br>1つ以上の Surface デバイスに展開するカスタムパッケージを作成して、ユーザーが収集および分析する特定のログを選択できるようにします。 | SDT 配布可能 MSI パッケージ:<br>Microsoft Surface Diagnostic Toolkit for Business Installer<br>[IT 担当者向け Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703) | [デスクトップモードで Surface 診断ツールキットを使う](surface-diagnostic-toolkit-desktop-mode.md)
コマンド ライン |  構成マネージャーなどの標準ツールを使用して、ユーザーの操作なしで Surface デバイスをリモートで直接トラブルシューティングします。 次のコマンドが含まれます。<br>`-DataCollector` すべてのログファイルを収集します<br>`-bpa` ベストプラクティスアナライザーを使用して正常性診断を実行します。<br>`-windowsupdate` Windows Update でファームウェアまたはドライバーの更新プログラムが見つからないかどうかを確認します。<br>`-warranty` 保証情報を確認します。 <br><br>| SDT コンソールアプリ:<br>Microsoft Surface Diagnostics アプリ本体<br>[IT 担当者向け Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703) | [コマンドを使用して Surface 診断ツールキットを実行する](surface-diagnostic-toolkit-command-line.md)

## サポートされるデバイス 

一般法人向けの SDT は、次のような、Surface 3 以降のデバイスでサポートされています。

- Surface のノート Pc の移動
- Surface Book 3
- Surface Go 2
- Surface Pro X
- Surface Pro 7
- Surface Laptop 3
- Surface Pro 6
- Surface Laptop 2
- Surface Go
- Surface Go LTE
- Surface Book 2
- Surface Pro LTE Advanced (モデル 1807)
- Surface Pro (モデル 1796)
- Surface Laptop
- Surface Studio
- Surface Studio 2
- Surface Book
- Surface Pro 4
- Surface 3 LTE
- Surface 3
- Surface Pro 3

## 一般法人向け Surface 診断ツールキットをインストールする

組織内のユーザーに配布できる SDT パッケージを作成するには、次の操作を行います。

1. 管理者アカウントを使用して Surface デバイスにサインインします。
2. [ [Surface Tools FOR IT] のダウンロードページ](https://www.microsoft.com/download/details.aspx?id=46703) から SDT Windows Installer パッケージ (.msi) をダウンロードして、デスクトップなどの surface デバイス上の希望する場所にコピーします。
3. 図1に示すように、SDT セットアップウィザードが表示されます。 **[次へ]** をクリックします。 

    >[!NOTE]
    >セットアップウィザードが表示されない場合は、コンピューターの管理者アカウントにサインインしていることを確認します。 

    ![Surface 診断ツールキットのセットアップウィザードへようこそ](images/sdt-1.png)

    *図 1.  Surface 診断ツールキットのセットアップウィザード*

4. SDT セットアップウィザードが表示されたら、[ **次へ**] をクリックし、エンドユーザーライセンス契約に同意します (EULA)

5. [インストールオプション] 画面で、必要に応じて既定のインストール場所を変更します。 
6. [セットアップの種類] で、[ **詳細設定**] を選択します。 

    >[!NOTE]
    >[標準] オプションを使うと、ユーザーは管理者アカウントを使用してデバイスにサインインしていることを提供して、Surface デバイスで診断ツールを直接実行できます。 
    
     ![インストールオプション: Advanced](images/sdt-install.png)

7. [ **次へ** ] をクリックし、[ **インストール**] をクリックします。 

## コマンドラインを使用してインストールする
必要に応じて、コマンドプロンプトで SDT をインストールし、ユーザー設定のフラグを設定して、ツールを管理モードでインストールすることができます。 SDT には、次のインストールオプションフラグが含まれます。

- `SENDTELEMETRY` テレメトリデータを Microsoft に送信します。 このフラグは、 `0` 無効または有効に受け入れ `1` ます。 既定値は、 `1` テレメトリを送信することです。
- `ADMINMODE` 管理者モードでインストールするツールを構成します。 このフラグは、 `0` クライアントモードまたは `1` IT 管理者モードを受け取ります。 既定値は、`0` です。

### コマンドラインから SDT をインストールするには、次の操作を行います。

1. コマンドプロンプトを開き、次のように入力します。

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **例:**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## Surface デバイスで SDT を検索する

SDT と SDT アプリ本体は両方ともインストールされてい `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` ます。

(図2のように)、SDT には .exe ファイルのほかに、JSON ファイルと admin.dll ファイル (modules\admin.dll) がインストールされます。

![ファイルエクスプローラーでインストールされた SDT ファイルのリスト](images/sdt-2.png)

*図 2.  SDT によってインストールされたファイル*

<span id="create-custom-sdt" />

## 配布用の SDT パッケージを準備する

カスタムパッケージを作成することで、特定の既知の問題にツールをターゲットにすることができます。

1. [ **Start > Run**] をクリックし、 **surface** と入力して、[ **surface Diagnostic Toolkit for Business**] をクリックします。 
2. ツールが開いたら、図3に示すように、[ **カスタムパッケージの作成**] をクリックします。

    ![[カスタムパッケージの作成] オプション](images/sdt-3.png)

    *図 3.  カスタムパッケージを作成する*

### 言語とテレメトリの設定

  パッケージを作成するときに、言語設定を選択したり、テレメトリ情報を Microsoft に送信しないようにしたりすることができます。 既定では、SDT は microsoft のプライバシーに関する [声明](https://privacy.microsoft.com/privacystatement)に基づいてアプリケーションを改善するために使用されるテレメトリを microsoft に送信します。 拒否する場合は、以下に示すように、カスタムパッケージを作成するときにチェックボックスをオフにします。 または、SDT のセットアップ中に、[**インストールオプション**] ページの [**テレメトリを Microsoft に送信する**] チェックボックスをオフにします。 

>[!NOTE]
>この設定は、Windows Update とソフトウェアの修復などのインターネット接続を必要とするテストや修復を実行しているとき、またはアプリツールバーで [スマイル] または [Frown] ボタンを使用してフィードバックを提供するときに、Microsoft サーバーに自動的に保存される最小のテレメトリには影響しません。 


![言語とテレメトリの設定を選ぶ](images/sdt-4.png)

*図 4:  言語とテレメトリの設定を選ぶ*


### Windows Update ページ

組織に適したオプションを選択します。 通常、複数のユーザーがいる組織では、通常、Windows Server Update Services (WSUS) 経由で更新プログラムを受信することを選択します (図 5)。 ローカルの Windows Update パッケージまたは WSUS を使用している場合は、必要に応じてパスを入力します。 

![[Windows Update] オプションを選ぶ](images/sdt-5.png)

*図 5:  [Windows Update] オプション*

### ソフトウェア修復ページ

これにより、ソフトウェア修復の更新プログラムを実行するためのオプションを選択または削除することができます。 

![ソフトウェア修復オプションを選ぶ](images/sdt-6.png)

*図 6.  ソフトウェア修復オプション*

### ログの収集とパッケージの保存ページ

アプリケーション、ドライバー、ハードウェア、オペレーティングシステム全体でさまざまなログを実行することを選択できます。 適切な領域をクリックして、使用可能なログのメニューから選択します。 その後、ユーザーがアクセスできるソフトウェアの配布ポイントまたは同等の場所にパッケージを保存することができます。 

![ログオプションを選択する](images/sdt-7.png)

*図 7. ログオプションとパッケージの保存*

## 次のステップ

- [ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する](surface-diagnostic-toolkit-desktop-mode.md)
- [コマンドを使用して一般法人向け Surface 診断ツールキットを使用する](surface-diagnostic-toolkit-command-line.md)

## 変更と更新

### バージョン2.124.139.0

このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。

- シームレスに統合されたサポート
- すべてのテスト結果を保存する
- 画像がカスタム作成されているかどうかを確認する
- デバイスマネージャーからの警告を含める
- Dock ファームウェアバージョン
- 記憶域テストでの潜在的な障害としてのドライブへのフラグ設定
- ストアリンクの削除 

### バージョン2.121.139
*リリース日:31 2020 年7月*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。

- シームレスなサポートエクスペリエンス
- バグ修正

### バージョン2.94.139.0
*リリース日: 2020 年5月11日*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。

- ハードウェアチェックを実行するために Windows Update をスキップする機能。
- 最新バージョンの更新に関する通知を受信する機能
- Surface Go 2
- Surface Book 3
- 進行状況インジケーターを表示する


### バージョン2.43.139.0
*リリース日: 2019 年10月21日*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。

- Surface Pro 7
- Surface Laptop 3

### バージョン2.42.139.0
*リリース日: 2019 年9月24日*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。 
- ハードウェアレポートをダウンロードする機能。
- ツールから直接 Microsoft サポートに問い合わせることができます。 <br>

### バージョン2.41.139.0
*リリース日: 2019 年6月24日*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。 
- ログとレポートに含まれるドライバーのバージョン情報。
- アプリについてのフィードバックを提供する機能。<br>


### バージョン2.36.139.0
*リリース日: 2019 年4月26日*<br>
このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。 
- コマンドラインの構成を必要とせずに、インストーラ UI を通じて管理機能のロックを解除する詳細なセットアップオプション。
- ユーザー補助機能の改善。
- サーフェスの明るさコントロールの設定がログに含まれています。
- レポートジェネレーターの外部モニター互換性サポートリンク。
