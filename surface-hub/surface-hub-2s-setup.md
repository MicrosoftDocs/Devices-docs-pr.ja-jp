---
title: Surface Hub 2S の初回セットアップ
description: Surface Hub 2S の初回セットアップを完了する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 9cbce8bf0cc9c729af4cd052167fef016197274f
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442195"
---
# <a name="first-time-setup-for-surface-hub-2s"></a>Surface Hub 2S の初回セットアップ

Surface Hub 2S を初めて起動すると、デバイスは初回セットアップ モードに自動的に入り、アカウントの構成と関連する設定を案内します。

## <a name="configuring-surface-hub-2s-account"></a>Surface Hub 2S アカウントの構成

1. **ロケールを構成します。** 地域、言語、キーボード レイアウト、タイム ゾーン情報を入力します。 **[次へ]** を選択します。

   ![* ロケールを構成する *](images/sh2-run1.png)

1. **ワイヤレス ネットワークに接続します。** 優先するワイヤレス ネットワークを選択し、[次へ] を **選択します。**

   - イーサネット ケーブルを使用して接続されている場合、このオプションは表示されません。

   - プロバイダーの Web サイトにサインイン要求をリダイレクトするホットスポット (キャプティブ ポータル) のワイヤレス ネットワークに接続することはできません。

3. **デバイス アカウント情報を入力します。** オンプレミス **環境とハイブリッド環境には domain\user、** オンライン環境には **user\@example.com** を使用します。 [次 **へ] を選択します。**

   ![* デバイス アカウント情報の入力 *](images/sh2-run2.png)

1. **追加情報を入力します。** 要求された場合は、Exchange サーバー のアドレスを指定し、[次へ] を選択 **します。**

   ![* 詳細情報を入力します。たとえば、Exchange サーバー名*](images/sh2-run3.png)

1. **このデバイスの名前を指定します。** デバイスの名前を入力するか、アカウントの表示名とユーザー原則名 [UPN] に基づいて候補の名前を使用します。 **[次へ] を選択します**。

   - [ **フレンドリー] 名** は Surface Hub 2S の左下隅に表示され、デバイスに投影するときに表示されます。

   - デバイス **名は** 、Active Directory または Azure Active Directory に関連付け、Intune にデバイスを登録するときにデバイスを識別します。

   ![* このデバイスに名前を付け*](images/sh2-run4.png)
 

## <a name="configuring-device-admin-accounts"></a>デバイス管理者アカウントの構成

デバイス管理者は、初回セットアップ時にのみ設定できます。 詳細については [、「Surface Hub 2S デバイスの所属」を参照してください](https://docs.microsoft.com/surface-hub/prepare-your-environment-for-surface-hub#device-affiliation)。

[このデバイス **のセットアップ管理者]** ウィンドウで、Active Directory ドメイン サービス、Azure Active Directory、またはローカル管理者のいずれかのオプションを選択します。

![* このデバイスのセットアップ管理者 *](images/sh2-run5.png)

### <a name="active-directory-domain-services"></a>Active Directory Domain Services

1. デバイスを Active Directory に参加するためのアクセス許可を持つユーザーの資格情報を入力します。

    ![* ドメイン参加を使用した管理者のセットアップ *](images/sh2-run6.png)

2. Surface Hub 2S の設定アプリにログオンできるメンバーを含む Active Directory セキュリティ グループを選択します。

   ![* セキュリティ グループを入力する *](images/sh2-run7.png)

1. [完了 **] を選択します**。 デバイスが再起動します。

### <a name="azure-active-directory"></a>Azure Active Directory

デバイスを Azure Active Directory に関連付けする場合、デバイスは直ちに再起動して次のページを表示します。

![* 組織が Microsoft Office 365 または他のビジネス サービスを使用している場合は、このデバイスを組織に登録します*](images/sh2-run8.png)

1. **[次へ]** を選択します。

1. Intune プラン **1** 以上のアカウントの電子メール アドレスまたは UPN を入力し、[次へ] を選択 **します。**

   ![* 仕事または学校のアカウントを入力*](images/sh2-run9.png)

1. リダイレクトされた場合は、組織のサインイン ページを使用して認証し、要求された場合は追加のログオン情報を提供します。 デバイスが再起動します。

## <a name="local-administrator-account"></a>ローカル管理者アカウント

- ローカル管理者のユーザー名とパスワードを入力します。デバイスが再起動します。

  ![* 管理者アカウントを設定する*](images/sh2-run10.png)
 
## <a name="using-provisioning-packages"></a>プロビジョニング パッケージの使用

Surface Hub 2S を起動するときに、プロビジョニング パッケージ付き USB サム ドライブを USB ポートの 1 つに挿入すると、次のページが表示されます。

1. 要求された設定を入力し、[セットアップ] **を選択します**。

   ![* プロビジョニング パッケージの地域設定を入力します*](images/sh2-run11.png)

   ![* リムーバブル メディアからこのデバイスをプロビジョニングする*](images/sh2-run12.png)

2. 使用するプロビジョニング パッケージを選択します。

   ![* 使用するプロビジョニング パッケージの選択*](images/sh2-run13.png)

3. 複数のデバイス CSV ファイルを作成した場合は、デバイス構成を選択できます。 詳細については [、「Create provisioning packages for Surface Hub 2S」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file)。

   ![* 構成ファイルからデバイス アカウントと分名を選択します*](images/sh2-run14.png)

4. 手順に従って初回セットアップを完了します。
