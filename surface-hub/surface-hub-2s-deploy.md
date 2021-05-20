---
title: Surface Hub 2S 用プロビジョニング パッケージの作成
description: このページでは、プロビジョニング パッケージや他のツールSurface Hub 2S を展開する方法について説明します。
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
ms.openlocfilehash: 214a71a759358ae08eb0da7942ea190946deb327
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576867"
---
# <a name="create-provisioning-packages-for-surface-hub-2s"></a>Surface Hub 2S 用プロビジョニング パッケージの作成

構成デザイナー (WCD) Windows使用して、プロビジョニング パッケージを作成して、2S の展開Surface Hubできます。 プロビジョニング パッケージを使用して、証明書の追加、プロキシの構成、デバイス管理者とデバイス アカウントのセットアップを行います。 構成ファイルと共にプロビジョニング パッケージを使用して、1 つの USB サム ドライブで複数の Surface Hub を展開することもできます。

### <a name="install-windows-configuration-designer"></a>Windows 構成デザイナーのインストール

テストWindows評価および展開キット (ADK) からWindows構成デザイナーをインストールWindows 10。 ADK for [Windows 10バージョン 1703 をダウンロードしてインストールします](https://go.microsoft.com/fwlink/p/?LinkId=845542)。 詳細については、「[Windows ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)」を参照してください。

### <a name="add-certificates"></a>証明書を追加する

証明機関の証明書を 2S Surface Hubできます。
証明書を 2S Surface Hubするには、.cer 形式の X.509 として各証明書のコピーが必要です。 .crt、.pfx、その他のコンテナー形式はインポートできません。 証明書は、構成デザイナーにインポートWindows階層別に配置する必要があります。

> [!div class="mx-imgBorder"]
> ![証明書を追加する](images/sh2-wcd.png)

### <a name="configure-proxy-during-oobe"></a>OOBE 中にプロキシを構成する

[Windowsデザイナー] で、[プロキシ設定の構成] タブに移動し、次に示すように適切な設定を入力します。

> [!div class="mx-imgBorder"]
> ![プロキシ設定の構成](images/sh2-proxy.png) 

> [!NOTE]
> プロキシ設定を構成する場合は、[**** セットアップ スクリプトまたはプロキシ サーバーを使用する場合は、設定を自動的に検出する] をオフにします。 セットアップ スクリプトまたはプロキシ サーバー *を* 使用できます。両方を使用することはできません。

### <a name="affiliate-surface-hub-2s-with-azure-active-directory"></a>アフィリエイト Surface Hub 2S と Azure Active Directory

Surface Hub 2S を Azure Active Directory に関連付けするには、プロビジョニング パッケージを使用します。Azure Active Directory グローバル管理者として、大量の新しい Windows デバイスを Azure Active Directory と Intune に一括トークンを使用して参加できます。

一括トークンを作成するには、親しき名前を付け、有効期限 (最大 30 日間) を構成し、管理者資格情報を使用して、以下に示すようにトークンを取得します。

> [!div class="mx-imgBorder"]
> ![デバイス管理者のセットアップ例 1](images/sh2-token.png)

> [!div class="mx-imgBorder"]
> ![デバイス管理者のセットアップ例 2](images/sh2-token2.png)

> [!div class="mx-imgBorder"]
> ![デバイス管理者の設定例 3](images/sh2-token3.png)


### <a name="provisioning-multiple-devices-csv-file"></a>複数のデバイスをプロビジョニングする (.csv ファイル)

プロビジョニング パッケージに加えて、Surface Hub構成ファイルを使用して、デバイスのセットアップを簡単に行えます。 このSurface Hub構成ファイルには、デバイス アカウントの一覧とワイヤレスプロジェクションの表示名が含まれる。 最初の実行時に、構成ファイルからデバイス アカウントと分名を選択するオプションが表示されます。

### <a name="to-create-a-surface-hub-configuration-file"></a>構成ファイルをSurface Hubするには

1. ユーザー Microsoft Excel別の CSV エディターを使用して、次の名前の CSV**ファイルをSurfaceHubConfiguration.csv**

2. 次の形式で、デバイス アカウントとユーザー名の一覧を入力します。

    `<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>`

3. PPKG ファイルをコピーした USB サム ドライブのルートにファイルを保存します。

    > [!div class="mx-imgBorder"]
    > ![構成ファイルの例](images/sh2-config-file.png)
