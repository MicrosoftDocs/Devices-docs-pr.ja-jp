---
title: Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする
description: Surface Hub オペレーティングシステムの最新の更新プログラムである Windows 10 Team 2020 Update を使用できるようになりました。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/22/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 9177b184d7a1d6dca63e94740b6208987d97229f
ms.sourcegitcommit: df1e178b724966e4cf8ff219c5e937e6c31cd9b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "10894113"
---
# Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする 

Surface hub オペレーティングシステムの最新の更新プログラム ( **windows 10 Team 2020 更新**プログラム) は、 [windows Insider プログラム](https://insider.windows.com)からの surface Hub 50 インチおよび surface hub 2s 55 インチデバイスでは追加料金なしで利用できるようになりました。 Surface Hub 84 インチモデルは、Windows 10 Team 2020 Update の最終リリースでサポートされます。

Windows 10 Team 2020 更新プログラムでは、Windows 10 の最新機能と共に、デバイスの展開と管理性が大幅に向上しています。 新機能の詳細については、次のブログ投稿を参照してください。[パブリックプレビュー用の新しい Surface HUB OS 更新プログラムがリリース](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)されました。 既知の問題については、下記の「既知の問題」を参照してください。
 
## 前提条件

- [Windows Insider program](https://insider.windows.com/)に登録します。
- Windows Insider Program Fast チャネルから Windows 10 Team 2020 更新プログラムプレビュービルドをダウンロードします。
- プレビュービルドをインストールしたら、必要なファームウェアの更新プログラムをダウンロードします。 注: Windows Insider プログラムを終了した場合でも、ファームウェアの更新プログラムをアンインストールすることはできません。

## Surface Hub を準備する

作業を始める前に、Surface Hub に Windows Update からの最新の更新プログラムが含まれていることを確認し、デバイスに関連付けられている BitLocker キーを保存していることを確認します。

**更新プログラムを手動で確認するには:**

1. Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
2. [**セキュリティ**  >  **Windows update** & 更新] に移動して、[**更新プログラムの確認**] を選びます。

詳細については、「 [Surface Hub で Windows 更新プログラムを管理](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub)する」を参照してください。

**BitLocker キーを手動で保存するには:**

1. Surface Hub に USB ドライブを挿入します。
2. Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
3. 「**更新 & セキュリティ**  >  の**回復**」に移動します。
4. [ **BitLocker**] で [**保存**] を選びます。 BitLocker キーは、USB ドライブ上のテキストファイルに保存されます。

詳細については、「 [BitLocker キーの保存](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub)」を参照してください。
 
## Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする

1. Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
2. [ **Update & Security**  >  **Windows Insider program** ] に移動して、[**はじめ**に] を選びます。
3. 指示に従って、職場アカウント (推奨) または個人の Microsoft アカウントを使って Windows Insider として登録します。 職場のアカウントで登録する利点の詳細については、「一般[法人向け Windows Insider プログラムに登録](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register)する」を参照してください。
4. [ **Insider の設定を選択して**ください] で、[**高速**] を選びます。
5. Surface Hub で、次の 3 ~ 4 日の間にプレビュービルドと必要なファームウェアの更新プログラムが自動的にインストールされるようにします。 このデバイスでは、毎日の[メンテナンス](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)期間中に更新プログラムを自動的にダウンロードしてインストールします。 次に、例を示します。

- 最初のメンテナンスウィンドウで、Surface Hub は、Windows Update からプレビュービルドのダウンロードを開始します。
- 第2のメンテナンスウィンドウで、デバイスが再起動して更新プログラムを完了します。
- 3番目のメンテナンスウィンドウで、デバイスは必要なファームウェアの更新プログラムをダウンロードしてインストールします。

> [!IMPORTANT]
> Microsoft は、Surface Hub を3-4 日間予約して、デバイスでプレビュービルドのインストールと必要なファームウェアの更新を完了できるようにすることをお勧めします。 このプロセスでデバイスを使用すると、グラフィックス、オーディオ、ユーザーインターフェイスの問題が発生する可能性があります。

### プレビュービルドと必要なファームウェア更新プログラムを手動でインストールする場合は、次の操作を実行します。

1. Windows Insider program に登録した後、[**設定**  >  の**更新] & [セキュリティ**  >  の**Windows Update** ] に移動し、[**更新プログラムの確認**] を選んでプレビュービルドをインストールします。
2. プレビュービルドがインストールされたら (最大14時間かかることがあります)、[**今すぐ再起動**] を選択してインストールを完了します。
3. デバイスが再起動したら、[**設定**  >  の**更新 & セキュリティ**  >  の**Windows Update**] に移動し、[更新プログラムの確認] を選んで、**必要なファームウェアの更新プログラムをインストール**します。
4. ファームウェアがインストールされたら、[**今すぐ再起動**] を選択します。

> [!WARNING]
> 必要なファームウェアの更新プログラムをインストールせずにプレビュービルドをインストールした場合、グラフィックス、オーディオ、ユーザーインターフェイスの問題が表示されることがあります。

> [!NOTE]
> Windows Insider プログラムを終了して Surface Hub を旧バージョンのオペレーティングシステムに戻す場合は、まず[デバイスをリセット](https://docs.microsoft.com/surface-hub/device-reset-surface-hub)する必要があります。 後でデバイスを再構成するには、[最初の run プログラムを実行](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub)する必要があります。
 
## 既知の問題: Windows 10 Team 2020 更新プログラムプレビュービルド

### グラフィックス、オーディオ、ユーザーインターフェイスの問題 

プレビュービルドをインストールしても、必要なファームウェアの更新プログラムをすぐにインストールしないと、さまざまなグラフィックスとユーザーインターフェイスの問題が発生する可能性があります。 Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこれらの問題を解決する予定です。

### Surface Hub 84 インチ: グラフィックスとユーザーインターフェイスの問題

第1世代の Surface Hub 84 インチデバイスにプレビュービルドをインストールすると、さまざまなグラフィックスとユーザーインターフェイスの問題が発生する可能性があります。 Surface Hub 84 インチは、Windows 10 Team 2020 Update の最終リリースでサポートされます。

### 条件付きアクセスポリシーが適用されると、サインインが影響を受ける

- Microsoft ホワイトボードなどのアプリにサインインしようとすると、サインインが失敗します。 ユーザーは、[スタート] メニューから[[自分の会議] と [ファイル](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub)] から初めてサインインする必要があります。

- ユーザーアカウントが、Surface Hub で Azure AD join によって使用されているものとは異なる Azure AD テナントに登録されている場合、サインインが失敗します。

Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこれらの問題を解決する予定です。

### Windows Update によって、利用できない場合に新しいドライバーをインストールするように求められる

**Settings**  >  **Update & Security**  >  Windows 10 Team 2020 更新プログラムと必要なファームウェア更新プログラムをインストールした後、[設定の更新] & セキュリティの**Windows Update**に移動すると、次のエラーが表示されることがあります。 

- "お使いの PC の最新のドライバーは、インストールしようとしているドライバーよりも優れている可能性があります。 引き続きインストールしようとしています。 " 

このエラーは安全に無視することができます。 Microsoft は、この問題を積極的に調査しています。

### プロビジョニングパッケージを使用して Surface Hub ポリシーをインストールできない

Surface Hub 構成サービスプロバイダー (CSP) のポリシーを使用するプロビジョニングパッケージは、インストールに失敗します。 ここでは、Microsoft Intune または別のモバイルデバイス管理 (MDM) プロバイダーを使用して Surface Hub ポリシーを適用します。 Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこの問題を解決する予定です。

### 初めて実行するときに、USB ドライブを削除するかどうかを確認する

初めて実行するときに、プロビジョニングパッケージを使って Surface Hub をセットアップすると、デバイスが Surface Hub 構成ファイルを読み取ることができるようになる前に、USB ドライブを削除するように求められます。 構成ファイルを使ってデバイスアカウントを設定している場合は、このメッセージを無視します。 Microsoft は、この問題を積極的に調査しています。
 
### 初回実行時にプロキシ設定を設定できない

プロキシを使ってインターネットに接続している場合は、初回実行プログラムでインターネット接続が制限されている可能性があります。 Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこの問題を解決する予定です。
 
### Microsoft Store からアプリをダウンロードするとエラーが表示される

Microsoft Store からアプリをダウンロードするには、サインインを求めるメッセージが表示されます。 既知の問題により、サインイン中にエラーが発生しますが、アプリのダウンロード機能には影響しません。 Microsoft は、この問題を積極的に調査しています。

### Surface Hub 2S が断続的に Wi-fi 接続を切断する

デバイスを取り外してもう一度接続するか、またはイーサネットケーブルを使ってインターネットに接続してみてください。 Microsoft は、この問題を積極的に調査しています。

### Surface Hub の2S がスリープ状態から再開できない

Surface Hub 2S が断続的にスリープ状態から再開せず、Microsoft ロゴが表示された画面で応答しなくなることがあります。 デバイスを取り外して、もう一度接続してみてください。 

この問題を回避するには:

1. Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
2. Power & **Surface Hub**  >  **セッション**に移動します。 
3. [**デバイスがスリープ状態になったとき] で、この電源設定を使用**し、[**接続さ**れたスタンバイ] を選択します。
4. [**存在しない場合は、デバイスをスリープ状態にする**] で [なし] を選択し**ます。**

Microsoft は、Windows 10 Team 2020 更新プログラムの最終リリース前のファームウェア更新プログラムでこの問題を解決する予定です。

### Connect アプリが表示されていない場合のプロジェクションの問題

- ケーブルを使用して Surface Hub に接続すると、Connect アプリから移動したときに touchback が機能しなくなります。
- Miracast を使用して Surface Hub にプロジェクトを作成すると、接続アプリから移動した後すぐにワイヤレス接続が切断されます。

Microsoft は、これらの問題について積極的に調査しています。

### Skype for Business がメディアトラフィックにプロキシを使用していない

プロキシを使用する一部のデバイスでは、Skype for Business でサインインすることはできますが、メディアトラフィックにプロキシサーバーを使いません。 Microsoft は、この問題を積極的に調査しています。

Microsoft のサポートを利用して、お客様の洞察と提案を共有します。

## 詳細情報

- [パブリックプレビュー用の新しい Surface Hub OS 更新プログラムがリリースされました。](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [Windows Insider Program for Business をお使いになる前に](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)