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
ms.openlocfilehash: 6661f2347d2f411ed11fe6057ede8ca2bab07c33
ms.sourcegitcommit: f0c976664116c45605edf3d56c4f58119a246b93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "11406670"
---
# <a name="using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-account"></a>Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト

## <a name="introduction"></a>はじめに

> [!NOTE]
> Surface Hub ハードウェア診断ツールの [アカウント設定] セクションでは、情報は収集されません。 入力として入力される電子メールとパスワードは、環境上でのみ直接使用され、誰にも収集または転送されません。 ログイン情報は、アプリケーションが閉じているか、Surface Hub で現在のセッションを終了するまで保持されます。

> [!IMPORTANT]
> * このアプリケーションを実行するには、管理者特権は必要ありません。
> * Microsoft でサービス呼び出しを開く前に、ローカル管理者と診断の結果について説明する必要があります。

### <a name="surface-hub-hardware-diagnostic"></a>Surface Hub ハードウェア診断

既定では [、Surface Hub ハードウェア診断](https://www.microsoft.com/store/apps/9nblggh51f2g) アプリケーションは以前のバージョンの Surface Hub システムにインストールされていません。 アプリケーションは、Microsoft Store から無料で利用できます。 アプリケーションをインストールするには、管理者特権が必要です。

   ![ハードウェア診断のスクリーンショット](images/01-diagnostic.png)

## <a name="about-the-surface-hub-hardware-diagnostic-tool"></a>Surface Hub ハードウェア診断ツールについて

Surface Hub ハードウェア診断ツールは、ユーザーが Surface Hub デバイス内の多くのハードウェア コンポーネントをテストできる、簡単に操作できるツールです。 このツールでは、Surface Hub デバイス アカウントをテストして確認することもできます。 この記事では、Surface Hub ハードウェア診断ツール内でアカウント設定テストを使用する方法について説明します。

> [!NOTE]
> テストが完了する前に、Surface Hub のデバイス アカウントを作成する必要があります。 Surface Hub 管理者ガイドには、オンプレミス、オンライン (Office365)、またはハイブリッド デバイス アカウントの作成に役立つ手順と PowerShell スクリプトが用意されています。 詳細については、ガイドの「デバイス アカウントの作成とテスト [(Surface Hub)」](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) を参照してください。

### <a name="device-account-testing-process"></a>デバイス アカウントのテスト プロセス

1. [すべてのアプリ **] に移動**し、Surface Hub ハードウェア診断アプリケーションを探します。

    ![すべてのアプリのスクリーンショット](images/02-all-apps.png)

1. アプリケーションが起動すると、[ようこそ] **ページ** に、ハブをテストする理由を示すテキスト ウィンドウが表示されます。 このメモは、テストの最後に診断結果と共に USB に保存できます。 メモの入力が完了したら、[続行] ボタン **を選択** します。

    >[!NOTE]
    >診断結果を保存する場合は、既定のパスを変更したり、サブディレクトリを選択したりしない。 ファイルは、後でエクスプローラー アプリを使用してコピーできます。

    ![ようこそのスクリーンショット](images/03-welcome.png)

1. 次の画面では、Surface Hub コンポーネントのすべてまたは一部をテストできます。 デバイス アカウントのテストを開始するには、[テスト結果] **アイコンを選択** します。

    ![テスト オプションのスクリーンショット](images/04-test-results-1.png)

    ![テスト結果のスクリーンショット](images/05-test-results-2.png)

1. [アカウント **設定] を選択します**。  

    ![アカウント設定のスクリーンショット](images/06-account-settings.png)

    [アカウント設定] 画面を使用して、デバイス アカウントをテストします。

    ![アカウント設定の詳細のスクリーンショット](images/07-account-settings-details.png)

1. デバイス アカウントのメール アドレスを入力します。 パスワードは省略可能ですが、お勧めします。 続行する **準備ができたら** 、[テスト アカウント] ボタンを選択します。

    ![テスト アカウントのスクリーンショット](images/08-test-account.png)

1. テストが完了したら、テストの 4 つの領域の結果を確認します。 各セクションは、各トピックの横にあるプラス記号またはマイナス記号を選択して展開または折りたたみできます。

    **ネットワーク**

    ![ネットワークのスクリーンショット](images/09-network.png)

    **環境**

    ![環境のスクリーンショット](images/10-environment.png)

    **証明書**

    ![証明書のスクリーンショット](images/11-certificates.png)

    **信頼モデル**

    ![信頼モデルのスクリーンショット](images/12-trust-model.png)

## <a name="appendix"></a>付録

### <a name="field-messages-and-resolution"></a>フィールド メッセージと解決

#### <a name="network"></a>ネットワーク

フィールド |成功 |失敗 |コメント |リファレンス
|------|------|------|------|------|
インターネット接続 |デバイスにインターネット接続がある |デバイスにインターネット接続が存在しない |プロキシ接続を含むインターネット接続を確認する |
HTTP バージョン |1.1 |1.0 |HTTP 1.0 が見つかった場合、WU とストアで問題が発生します |
ダイレクト インターネット接続 |デバイスにプロキシが構成されているデバイスにプロキシが構成されていない |該当せず |Informational。 デバイスがプロキシの背後にあるか。 |
プロキシ アドレス | | |構成されている場合は、プロキシ アドレスを返します。 |
プロキシ認証 |プロキシは認証を必要としない |プロキシにはプロキシ認証が必要です |ユーザーがエッジで開いているセッションを既に持ち、プロキシを介して認証されている場合、結果は誤検知になる可能性があります。 |
プロキシ認証の種類 | | |プロキシ認証を使用する場合は、プロキシによってアドバタイズされた認証メソッドを返します。  |

#### <a name="environment"></a>環境

フィールド |成功 |失敗 |コメント |リファレンス
|------|------|------|------|------|
SIP ドメイン | | |Informational。  |
Skype 環境 |Skype for Business Online, Skype for Business OnPrem, Skype for Business Hybrid |Informational。 |検出された環境の種類。 注: ハイブリッドは、パスワードが入力されている場合にのみ検出できます。
LyncDiscover FQDN | | |Informational。 LyncDiscover DNS の結果を表示する |
LyncDiscover URI | | |Informational。 環境で LyncDiscover を実行するために使用される URL を表示します。|
LyncDiscover |接続成功 |接続に失敗しました |LyncDiscover Web サービスからの応答。 |
SIP プールのホスト名 | | |Informational。 LyncDiscover から検出された SIP プール名を表示する |

#### <a name="certificates-in-premises-hybrid-only"></a>証明書 (オンプレミスハイブリッドのみ)

LyncDiscover 証明書

フィールド |成功 |失敗 |コメント |リファレンス
|------|------|------|------|------|
LyncDiscover 証明書 CN | | |Informational。 LD 証明書の共通名を表示します。 |
LyncDiscover 証明書 CA | | |Informational。 LD 証明書 CA を表示します。 |
LyncDiscover 証明書ルート CA | | |Informational。 LD Cert ルート CA を表示します (使用可能な場合)。 |
LD の信頼状態 |証明書は信頼済みです。 |証明書が信頼されていない場合は、ルート CA を追加してください。 |ローカル証明書ストアに対して証明書を確認します。 コンピューターが証明書を信頼する場合は、正の値を返します。|[PowerShell を使用して Skype for Business 証明書をダウンロードして展開する](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) /[Surface Hub プロビジョニング パッケージでサポートされているアイテム](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)

SIP プール認定

フィールド |成功 |失敗 |コメント |リファレンス
|------|------|------|------|------|
SIP プール証明書 CN | | |(CONTENTS) |
SIP プール証明書 CA | | |(CONTENTS) |
SIP プールの信頼状態 |証明書は信頼済みです。 |証明書が信頼されていない場合は、ルート CA を追加してください。 |ローカル証明書ストアに対して証明書を確認し、デバイスが証明書を信頼している場合は正の値を返します。 |
SIP プール証明書ルート CA | | |情報。 使用可能な場合は、SIP プール証明書ルート CA を表示します。 |

#### <a name="trust-model-on-premises-hybrid-only"></a>信頼モデル (オンプレミス ハイブリッドのみ)

フィールド |成功 |失敗 |コメント |リファレンス
|------|------|------|------|------|
信頼モデルの状態 |信頼モデルの問題が検出されません。 |SIP ドメインとサーバー ドメインが異なる場合は、次のドメインを追加してください。 |信頼モデルの問題については、LD FQDN/LD Server 名/プール サーバー名を確認してください。 
ドメイン名 | | |SFB が接続するために追加する必要があるドメインの一覧を返します。 |
