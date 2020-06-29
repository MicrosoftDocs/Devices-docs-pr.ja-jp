---
title: Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト
description: Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト
ms.assetid: a87b7d41-d0a7-4acc-bfa6-b9070f99bc9c
keywords: アクセシビリティの設定, 設定アプリ, 簡単操作
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 127be0a5f320418d8a1086aec3de62e3ef54e42a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834885"
---
# Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト

## はじめに

> [!NOTE]
> Surface Hub ハードウェア診断ツールの [アカウント設定] セクションには、情報は収集されません。 入力として入力されたメールアドレスとパスワードは、環境で直接使用され、すべてのユーザーに収集または転送されることはありません。 ログイン情報は、アプリケーションが閉じられるか、Surface Hub で現在のセッションを終了するまでのみ保持されます。

> [!IMPORTANT]
> * このアプリケーションを実行するには、管理者権限は必要ありません。
> * 診断の結果は、Microsoft とのサービスコールを開始する前に、ローカル管理者に説明する必要があります。

### Surface Hub ハードウェア診断

既定では、 [Surface Hub ハードウェア診断](https://www.microsoft.com/store/apps/9nblggh51f2g)アプリケーションは、以前のバージョンの surface hub システムにはインストールされていません。 アプリケーションは Microsoft ストアから無料で入手できます。 アプリケーションをインストールするには、管理者特権が必要です。

   ![ハードウェア診断のスクリーンショット](images/01-diagnostic.png)

## Surface Hub ハードウェア診断ツールについて

Surface Hub ハードウェア診断ツールは、Surface Hub デバイス内の多くのハードウェアコンポーネントをユーザーがテストできるようにするための、操作の容易なツールです。 このツールは Surface Hub デバイスアカウントをテストして確認することもできます。 この記事では、Surface Hub ハードウェア診断ツール内でのアカウント設定のテストの使い方について説明します。

> [!NOTE]
> テストが完了する前に、Surface Hub のデバイスアカウントを作成する必要があります。 Surface Hub 管理者ガイドには、オンプレミス、オンライン (Office365)、またはハイブリッドデバイスアカウントの作成に役立つ手順と PowerShell スクリプトが用意されています。 詳細については、ガイドの「[デバイスアカウント (Surface Hub) を作成してテスト](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub)する」を参照してください。

### デバイスアカウントのテストプロセス

1. [**すべてのアプリ**] に移動して、Surface Hub ハードウェア診断アプリケーションを見つけます。

    ![すべてのアプリのスクリーンショット](images/02-all-apps.png)

1. アプリケーションが起動すると、[**ようこそ**] ページに、ハブをテストする理由を文書化するためのテキストウィンドウが表示されます。 このメモは、テストの完了時に診断結果と共に、USB に保存することができます。 メモの入力が完了したら、[**続行**] をクリックします。

    ![ようこそのスクリーンショット](images/03-welcome.png)

1. 次の画面では、Surface Hub のコンポーネントをすべてまたは一部テストするオプションが提供されています。 デバイスアカウントのテストを開始するには、[**テスト結果**] アイコンを選択します。

    ![テスト結果のスクリーンショット](images/04-test-results-1.png)

    ![テスト結果のスクリーンショット](images/05-test-results-2.png)

1. [**アカウント設定**] を選びます。  

    ![アカウント設定のスクリーンショット](images/06-account-settings.png)

    [アカウントの設定] 画面を使って、お使いのデバイスアカウントをテストします。

    ![アカウント設定の詳細のスクリーンショット](images/07-account-settings-details.png)

1. デバイスアカウントのメールアドレスを入力します。 パスワードは省略可能ですが、お勧めします。 続行する準備ができたら、[**アカウントのテスト**] を選択します。

    ![テストアカウントのスクリーンショット](images/08-test-account.png)

1. テストが完了したら、テストの4つの領域の結果を確認します。 各セクションの横にあるプラス記号またはマイナス記号を選択すると、各セクションを展開または折りたたむことができます。

    **ネットワーク**

    ![Network のスクリーンショット](images/09-network.png)

    **環境**

    ![環境のスクリーンショット](images/10-environment.png)

    **証明書**

    ![証明書のスクリーンショット](images/11-certificates.png)

    **信頼モデル**

    ![信頼モデルのスクリーンショット](images/12-trust-model.png)

## 付録

### フィールドメッセージと解決策

#### ネットワーク

フィールド |Success |失敗 |コメント |リファレンス
|------|------|------|------|------|
インターネット接続 |デバイスがインターネットに接続されている |デバイスにインターネット接続がありません |プロキシ接続などのインターネット接続を確認します。 |
HTTP バージョン |1.1 |1.0 |HTTP 1.0 が検出されると、WU とストアで問題が発生する可能性があります。 |
直接インターネット接続 |デバイスにプロキシが構成されています。 |なし |情報. お使いのデバイスはプロキシの背後にありますか? |
プロキシアドレス | | |構成されている場合は、プロキシアドレスを返します。 |
プロキシ認証 |プロキシは認証を必要としません |プロキシにはプロキシ認証が必要 |ユーザーが既に Edge で開いているセッションを使っていて、プロキシ経由で認証されている場合、結果は誤認の可能性があります。 |
プロキシ認証の種類 | | |プロキシ認証が使われている場合は、プロキシによってアドバタイズされた認証メソッドを返します。  |

#### 環境

フィールド |Success |失敗 |コメント |リファレンス
|------|------|------|------|------|
SIP ドメイン | | |情報.  |
Skype 環境 |Skype for Business Online、Skype for Business OnPrem、Skype for Business のハイブリッド |情報. |検出された環境の種類。 注: ハイブリッドは、パスワードが入力されている場合にのみ検出されます。
LyncDiscover FQDN | | |情報. LyncDiscover DNS の結果を表示します |
LyncDiscover URI | | |情報. 環境で LyncDiscover を実行するために使用される URL を表示します。|
LyncDiscover |接続に成功しました |接続に失敗しました |LyncDiscover web サービスからの応答。 |
SIP プールのホスト名 | | |情報. LyncDiscover から検出された SIP プール名を表示する |

#### 証明書 (内部設置型ハイブリッドのみ)

LyncDiscover 証明書

フィールド |Success |失敗 |コメント |リファレンス
|------|------|------|------|------|
LyncDiscover Cert CN | | |情報. LD 証明書の共通名を表示します。 |
LyncDiscover Cert CA | | |情報. LD Cert CA を表示します。 |
LyncDiscover Cert ルート CA | | |情報. 利用可能な場合は、LD Cert ルート CA を表示します。 |
LD の信頼状態 |証明書が信頼されている。 |証明書が信頼されていません。ルート CA を追加してください。 |ローカル証明書ストアに対して証明書を確認します。 マシンが証明書を信頼している場合は、正の値を返します。|[PowerShell を使用して Skype For business 証明書をダウンロードして展開する](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) /[Surface Hub プロビジョニングパッケージでサポートされている項目](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)

SIP プール認定

フィールド |Success |失敗 |コメント |リファレンス
|------|------|------|------|------|
SIP プール Cert CN | | |数式 |
SIP プール Cert CA | | |数式 |
SIP プールの信頼状態 |証明書が信頼されている。 |証明書が信頼されていません。ルート CA を追加してください。 |ローカル証明書ストアに対して証明書を確認し、デバイスが証明書を信頼する場合は正の値を返します。 |
SIP プール証明書ルート CA | | |詳しく. SIP プール Cert ルート CA を表示します (利用可能な場合)。 |

#### 信頼モデル (オンプレミスハイブリッドのみ)

フィールド |Success |失敗 |コメント |リファレンス
|------|------|------|------|------|
信頼モデルの状態 |信頼モデルの問題は検出されませんでした。 |SIP ドメインとサーバードメインが異なる場合は、次のドメインを追加してください。 |信頼性モデルの問題については、LD FQDN/LD サーバー名/プールサーバー名を確認してください。 
ドメイン名 | | |SFB に接続するために追加する必要があるドメインの一覧を返します。 |
