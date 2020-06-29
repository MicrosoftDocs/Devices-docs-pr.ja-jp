---
title: Surface Hub 2S のパスワードを使用しない電話のサインインを構成する
description: モバイルデバイスでパスワードを使用しないパスワードを使用して、Surface Hub 2S へのサインインを簡素化する方法について説明します。
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
ms.openlocfilehash: 95873e41588a6f07ece53fd04f7d63bf56143914
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835366"
---
# Surface Hub 2S のパスワードを使用しない電話のサインインを構成する

パスワードを使用しないパスワードを使用すると、会議へのサインインが簡単になり、Surface Hub 2S のファイルにも参加できます。

> [!NOTE]
> パスワードを使用しない場合は、プライマリメールアドレスが UPN と一致している必要があります。

## パスワードを設定しないようにするには

1. IPhone または Android 用の[Microsoft Authenticator](https://www.microsoft.com/account/authenticator)アプリを携帯電話にダウンロードします。
2. PC で、にアクセスし [https://aka.ms/MFASetup](https://aka.ms/MFASetup) て、アカウントでサインインし、[**次へ**] を選択します。
3. [追加のセキュリティ検証] 画面で、[モバイルアプリ] を選択し、確認コードを使用して、[**セットアップ**] を選択します。

## モバイルアプリを構成するには

1. 電話の Microsoft authenticator アプリで、アカウントを追加し、[**職場または学校アカウント**] を選択して、PC に表示される QR コードをスキャンします。
2. 電話に通知を送信し、サインイン要求を承認します。
3. スマートフォンの認証アプリで、アカウントの横にあるドロップダウンメニューを使用して、[**電話でのサインインを有効にする**] を選択します。
4. 必要に応じて、デバイスを組織に登録し、画面の指示に従います。

## Surface Hub にサインインするには

1. Surface Hub で、 **[自分の会議] と [ファイル**] にサインインし、メッセージが表示されたら [**通知の送信**] を選択します。
2. サインイン要求を承認するために、携帯電話に表示される番号と Surface Hub に表示される番号を一致させます。
3. メッセージが表示されたら、電話の PIN または生体認証 ID を入力して、サインインを完了します。

## 詳細情報
詳細については、「 [Microsoft Authenticator アプリでのパスワードを使用しない電話でのサインイン](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-phone-sign-in)」を参照してください。
