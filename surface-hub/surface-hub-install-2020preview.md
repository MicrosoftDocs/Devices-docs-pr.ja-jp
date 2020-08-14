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
ms.date: 08/13/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 51d6b9169b0074eb474ddc89b6fe9b43a921bb07
ms.sourcegitcommit: feb81137d009d9b7c743aabd7d02615e89842200
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "10929769"
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

1. Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
2. [**セキュリティ**  >  **Windows update** & 更新] に移動して、[**更新プログラムの確認**] を選びます。

詳細については、「 [Surface Hub で Windows 更新プログラムを管理](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub)する」を参照してください。

**BitLocker キーを手動で保存するには:**

1. Surface Hub に USB ドライブを挿入します。
2. Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
3. 「**更新 & セキュリティ**  >  の**回復**」に移動します。
4. [ **BitLocker**] で [ **保存**] を選びます。 BitLocker キーは、USB ドライブ上のテキストファイルに保存されます。

詳細については、「 [BitLocker キーの保存](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub)」を参照してください。
 
## Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする

1. Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
2. [ **プライバシー > 診断 & フィードバック** に移動し、診断データを [ **完全**] に設定します。 一部の地域や組織では、MDM ポリシーまたは PPKG ファイルを使用してこの設定を適用する必要がある場合があります。
   - **MDM の場合:** 次のポリシーを設定します。**/Vendor/MSFT/Policy/System/AllowTelemetry** の整数値3を使用します。
    
        ![AllowTelemetry を3に設定します](images/hub-2020-allow-telemetry.png)

    - **PPKG:**[Ppkg ファイル](https://aka.ms/HubTltmtry)をダウンロードします。

3. [ **Update & Security**  >  **Windows Insider program** ] に移動して、[登録の**開始**] を選びます。
4. 指示に従って、職場アカウント (推奨) または個人の Microsoft アカウントを使って Windows Insider として登録します。 職場のアカウントで登録する利点の詳細については、「一般 [法人向け Windows Insider プログラムに登録](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register)する」を参照してください。
5. [ **Insider の設定を選択して**ください] で、[ **高速**] を選びます。
6. Surface Hub で、次の 3 ~ 4 日の間にプレビュービルドと必要なファームウェアの更新プログラムが自動的にインストールされるようにします。 このデバイスでは、毎日の [メンテナンス](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)期間中に更新プログラムを自動的にダウンロードしてインストールします。 次に、例を示します。

- 最初のメンテナンスウィンドウで、Surface Hub は、Windows Update からプレビュービルドのダウンロードを開始します。
- 第2のメンテナンスウィンドウで、デバイスが再起動して更新プログラムを完了します。
- 3番目のメンテナンスウィンドウで、デバイスは必要なファームウェアの更新プログラムをダウンロードしてインストールします。

> [!IMPORTANT]
> Microsoft は、Surface Hub を3-4 日間予約して、デバイスでプレビュービルドのインストールと必要なファームウェアの更新を完了できるようにすることをお勧めします。 このプロセスでデバイスを使用すると、グラフィックス、オーディオ、ユーザーインターフェイスの問題が発生する可能性があります。

### プレビュービルドと必要なファームウェア更新プログラムを手動でインストールする場合は、次の操作を実行します。

1. Windows Insider program に登録した後、[**設定**  >  の**更新] & [セキュリティ**  >  の**Windows Update** ] に移動し、[**更新プログラムの確認**] を選んでプレビュービルドをインストールします。
2. プレビュービルドがインストールされたら (最大14時間かかることがあります)、[ **今すぐ再起動** ] を選択してインストールを完了します。
3. デバイスが再起動したら、[**設定**  >  の**更新 & セキュリティ**  >  の**Windows Update**] に移動し、[更新プログラムの確認] を選んで、**必要なファームウェアの更新プログラムをインストール**します。
4. ファームウェアがインストールされたら、[ **今すぐ再起動**] を選択します。

> [!WARNING]
> 必要なファームウェアの更新プログラムをインストールせずにプレビュービルドをインストールした場合、グラフィックス、オーディオ、ユーザーインターフェイスの問題が表示されることがあります。

> [!NOTE]
> Windows Insider プログラムを終了して Surface Hub を旧バージョンのオペレーティングシステムに戻す場合は、まず [デバイスをリセット](https://docs.microsoft.com/surface-hub/device-reset-surface-hub)する必要があります。 後でデバイスを再構成するには、 [最初の run プログラムを実行](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) する必要があります。
 

## 詳細情報

- [既知の問題: Windows 10 Team 2020 更新プログラム](surface-hub-2020-team-update-known-issues.md)
- [パブリックプレビュー用の新しい Surface Hub OS 更新プログラムがリリースされました。](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [Windows Insider Program for Business をお使いになる前に](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)