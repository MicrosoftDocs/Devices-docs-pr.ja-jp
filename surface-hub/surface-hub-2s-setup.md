---
title: Surface Hub 2S の初めてのセットアップ
description: Surface Hub 2S の初めてのセットアップを完了する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 47a393944c1b524931a6ac56962cc2cd60786007
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836125"
---
# Surface Hub 2S の初めてのセットアップ

初めて Surface Hub 2S を起動すると、デバイスは、アカウントの構成と関連設定についてのガイドとして、最初にセットアップモードに自動的に入力します。

## Surface Hub 2S アカウントを構成する

1. **ロケールを構成します。** 地域、言語、キーボードレイアウト、タイムゾーン情報を入力します。 **[次へ]** を選択します。

   ![* ロケールを設定する *](images/sh2-run1.png) <br>
1. **ワイヤレスネットワークに接続します。** 優先ワイヤレスネットワークを選択して、[次へ] を選択し**ます。**

- イーサネットケーブルを使って接続している場合は、このオプションは表示されません。
- サインイン要求をプロバイダーの web サイトにリダイレクトするホットスポット (専用ポータル) 内のワイヤレスネットワークに接続することはできません。

3. **デバイスアカウント情報を入力します。** オンプレミスおよびハイブリッド環境には**domain\user** 、オンライン環境では**ユーザー \ @example .com**を使用します。 [**次へ**] を選びます。

   ![* デバイスアカウント情報を入力 *](images/sh2-run2.png) <br>
1. **追加情報を入力します。** 要求された場合は、Exchange サーバーのアドレスを入力して、[次へ] を選び**ます。**

    ![* 情報を入力してください。たとえば、Exchange server 名 *](images/sh2-run3.png) <br>

1. **このデバイスに名前を指定します。** お使いのデバイスの名前を入力するか、お使いのアカウントの表示名とユーザプリンシパル名に基づいて推奨されるものを使用してください。 **[次へ] を選び**ます。

- **フレンドリ名**は Surface Hub 2s の左下隅に表示され、デバイスに投影したときに表示されます。

- デバイス**名**は、Active directory または Azure Active directory に関連している場合と、デバイスを Intune に登録する場合に、デバイスを識別します。

  ![* このデバイス名 *](images/sh2-run4.png) <br>
 
## デバイス管理者アカウントを構成する

初めてセットアップするときにのみ、デバイス管理者を設定できます。 詳細については、「 [Surface Hub 2s デバイスの所属](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation)」を参照してください。

 [**このデバイスのセットアップ管理者**] ウィンドウで、次のいずれかのオプション (Active Directory ドメインサービス、Azure Active directory、またはローカル管理者) を選びます。

   ![* このデバイスの管理者のセットアップ *](images/sh2-run5.png) <br>

### Active Directory Domain Services

1. デバイスを Active Directory に参加する権限を持つユーザーの資格情報を入力します。

    ![* ドメイン参加を使用して管理者を設定する *](images/sh2-run6.png) <br>

2. Surface Hub 2S の設定アプリへのログオンが許可されているメンバーが含まれている Active Directory セキュリティグループを選択します。

    ![* セキュリティグループの入力 *](images/sh2-run7.png) <br>
1. [**完了**] を選びます。 デバイスが再起動します。

### Azure Active Directory

Azure Active Directory でデバイスを利用することを選択すると、デバイスは直ちに再起動し、次のページが表示されます。 **[次へ]** を選択します。

![* Office 365 または Microsoft の他のビジネスサービスを使用している組織では、このデバイスを組織に enrolll *](images/sh2-run8.png) <br>

1. **Intune Plan 1**以上のアカウントのメールアドレスまたは UPN を入力し、[次へ] を選択し**ます。**

    ![* 職場または学校のアカウントを入力してください *](images/sh2-run9.png) <br>

2. リダイレクトされた場合は、組織のサインインページを使用して認証し、必要に応じて追加のログオン情報を提供します。 デバイスが再起動します。

## ローカル管理者アカウント

- ローカル管理者のユーザー名とパスワードを入力します。デバイスが再起動します。

     ![* 管理アカウントのセットアップ *](images/sh2-run10.png) <br>
 
## プロビジョニングパッケージの使用

Surface Hub 2S を起動したときに、プロビジョニングパッケージ付きの USB サムドライブを USB ポートの1つに挿入すると、デバイスに次のページが表示されます。

1. 要求された設定を入力し、[**設定**] を選択します。

    ![* プロビジョニングパッケージの地域設定を入力 *](images/sh2-run11.png) <br>

    ![* リムーバブルメディアからこのデバイスをプロビジョニング *](images/sh2-run12.png) <br>
2. 使用するプロビジョニングパッケージを選択します。

   ![* 使用するプロビジョニングパッケージを選ぶ *](images/sh2-run13.png) <br>

3. 複数のデバイス CSV ファイルを作成した場合は、デバイス構成を選ぶことができます。 詳細については、「 [Surface Hub 2s のプロビジョニングパッケージの作成](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file)」を参照してください。


    ![* 構成ファイルからデバイスアカウントとフレンドリ名を選択します *](images/sh2-run14.png) <br>

4. 指示に従って、初回のセットアップを完了します。
