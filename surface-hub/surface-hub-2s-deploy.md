---
title: Surface Hub 2S 用プロビジョニング パッケージの作成
description: このページでは、プロビジョニングパッケージとその他のツールを使用して Surface Hub の2S を展開する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 8f91b751a10977d80210d10ac1b48a93d9ba0f6f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836938"
---
# Surface Hub 2S 用プロビジョニング パッケージの作成

Windows 構成デザイナー (WCD) を使ってプロビジョニングパッケージを作成し、Surface Hub 2S の展開プロセスを自動化することができます。 プロビジョニングパッケージを使用して、証明書の追加、プロキシの構成、デバイス管理者とデバイスアカウントのセットアップを行います。 プロビジョニングパッケージと構成ファイルを使用して、1つの USB サムドライブで複数の Surface Hub を展開することもできます。

### Windows 構成デザイナーのインストール

Windows 10 の Windows アセスメント & デプロイメントキット (ADK) から Windows 構成デザイナーをインストールします。 [ADK For Windows 10 バージョン 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542)をダウンロードしてインストールします。 詳細については、「 [WINDOWS ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)」を参照してください。

### 証明書を追加する

証明機関証明書は Surface Hub 2S にインポートできます。
Surface Hub 2S に証明書を追加するには、各証明書のコピーを .cer 形式で x.509 として指定する必要があります。 .Crt、.pfx、その他のコンテナー形式をインポートすることはできません。 証明書は Windows 構成デザイナーにインポートされ、階層ごとに配置されている必要があります。

 ![証明書を追加する](images/sh2-wcd.png)

### OOBE 中にプロキシを構成する

Windows 構成デザイナーで、[プロキシ設定の構成] タブに移動し、次に示すように適切な設定を入力します。

 ![プロキシ設定の構成](images/sh2-proxy.png) 

> [!NOTE]
> プロキシ設定を構成する場合、セットアップスクリプトまたはプロキシサーバーを使用する場合は、[**設定を自動的に検出**しない] をオフにします。 セットアップスクリプト*また*はプロキシサーバーの両方を使用することはできません。

### Azure Active Directory での関連 Surface Hub 2S

プロビジョニングパッケージを使用して、Azure Active directory と共に Surface Hub 2S を使用できます。 Azure Active Directory 全体管理者は、一括トークンを使って、多数の新しい Windows デバイスを Azure Active Directory と Intune に参加させることができます。

一括トークンを作成するには、わかりやすい名前を付け、有効期限の日付 (最大30日間) を構成し、管理者の資格情報を使ってトークンを取得します。次のようにします。

 ![デバイス管理者を設定する](images/sh2-token.png) <br><br>
 ![デバイス管理者を設定する](images/sh2-token2.png) <br><br>
 ![デバイス管理者を設定する](images/sh2-token3.png) <br><br>

### 複数のデバイスのプロビジョニング (.csv ファイル)

プロビジョニングパッケージに加えて、Surface Hub 構成ファイルを使用して、デバイスのセットアップをより簡単に行うことができます。 Surface Hub 構成ファイルには、ワイヤレスプロジェクションのデバイスアカウントとフレンドリ名の一覧が含まれています。 初めて実行するときに、構成ファイルからデバイスアカウントとフレンドリ名を選択するオプションが表示されます。

### Surface Hub 構成ファイルを作成するには

1. Microsoft Excel または別の CSV エディターを使用して、次のような CSV ファイルを作成し**SurfaceHubConfiguration.csv**
2. デバイスアカウントとフレンドリ名の一覧を次の形式で入力します。

```
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```

3. ファイルを、PPKG ファイルをコピーした USB サムドライブのルートに保存します。

    ![構成ファイルの例](images/sh2-config-file.png)
