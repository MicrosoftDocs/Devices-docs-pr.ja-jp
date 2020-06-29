---
title: Intune を使用して Surface Hub 2S にアプリを展開する
description: Intune を使用して Surface Hub 2S にアプリを展開する方法について説明します。
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
ms.openlocfilehash: 51e54a5b2881519f2fc361675253c9e50bad0864
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835686"
---
# Intune を使用して Surface Hub 2S にアプリを展開する

チームまたは組織のニーズに合わせて、追加のアプリをインストールできます。

## 開発者向けガイドライン

- Surface Hub で実行できるのは、[ユニバーサル Windows プラットフォーム (UWP) アプリ](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp)のみです。 [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) を使用して作成されたアプリは、Surface Hub では動作しません。
- アプリは、[ユニバーサル デバイス ファミリ](https://msdn.microsoft.com/library/windows/apps/dn894631)または Windows チーム デバイス ファミリに対応している必要があります。
- Surface Hub は、一般[法人向け Microsoft Store](https://businessstore.microsoft.com/store)の[オフラインライセンスアプリ](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)のみをサポートしています。
- 既定では、アプリをインストールするには、アプリにストアの署名が必要です。 テストおよび開発時には、開発者モードでデバイスを配置することによって、開発者が署名した UWP アプリの実行を選択することもできます。
- Microsoft ストアへのアプリの開発と申請を行うときは、デバイスファミリの可用性と組織のライセンスオプションを設定して、Surface Hub でアプリを実行できるようにします。
- Surface Hub にアプリをインストールするには、管理者の資格情報が必要です。 会議室や他の共有スペースで使用するように設計されています。 Surface Hub は、通常のユーザーが Microsoft Store にアクセスしてアプリをダウンロードしてインストールすることを防止します。

## 展開のガイドライン

Intune を使用してユニバーサル Windows プラットフォーム (UWP) アプリを Surface Hub 2S に展開し、デバイスへのアプリの展開を容易にすることができます。

1. アプリを展開するには、組織の MDM を有効にします。 Intune ポータルで、MDM オーソリティとして [ **Intune** ] を選択します (推奨)。 <br>

    ![MDM 権限を選ぶ](images/sh2-set-intune5.png)

2. Intune で Microsoft Store for Business を有効にします。 Intune を開き、[**クライアントアプリ**for Business] を選択し  >  **ます。** <br>

    ![ビジネス用ストアを有効にする](images/sh2-deploy-apps-sync.png)

3. Intune で [**ビジネス向け Microsoft Store** ] を開き、[**設定**] [  >  **Distribute**  >  **管理ツール**の配布] を選択します。 管理ツールとして**Microsoft Intune**を選択します。 <br>

    ![管理ツールとして Intune を追加する](images/sh2-set-intune8.png)

4. [Microsoft Store for Business] で、[**設定**] ショッピング体験を選択し、[  >  **Shop**  >  **Shopping Experience****オフラインアプリの表示**] を選択します。 オフラインアプリは、Intune との間で同期され、1つのデバイスに展開できるアプリを指します。
5. オフラインショッピングを有効にした後は、オフラインライセンスを取得して、Intune に同期し、デバイスライセンスとして展開することができます。
6. **Intune**  >  **クライアントアプリ**の  >  **Microsoft ストア for Business**で、[**同期**] を選びます。
7. [クライアントアプリ] ページで、アプリの一覧からアプリを検索します。 アプリを目的のデバイスグループまたはグループに割り当てます。 [**課題**  >  の**追加] グループ**を選択します。 <br>

![* グループへのアプリの割り当て *](images/sh2-assign-group.png) <br>

8. [割り当ての種類] で [**必須**] を選択します。 <br>

![* グループへのアプリの割り当て *](images/sh2-add-group.png) <br>

9. 選択したグループについて、[**デバイスライセンス**] を選択し、[ **OK]** を選択して課題を保存します。 <br>
 
![* グループへのアプリの割り当て *](images/sh2-apps-assign.png)
