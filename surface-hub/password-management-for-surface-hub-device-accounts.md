---
title: パスワード管理 (Surface Hub)
description: すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。
ms.assetid: 0FBFB546-05F0-430E-905E-87111046E4B8
ms.reviewer: ''
manager: laurawi
keywords: パスワード, パスワードの管理, パスワードの循環, デバイス アカウント
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: bef626fce875d5074f3ed47ed957e821beec7c77
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836678"
---
# パスワード管理 (Surface Hub)

すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。 セキュリティ上の理由から、このパスワードを定期的に変更 (または "循環") することをお勧めします。 ただし、デバイス アカウントのパスワードを変更すると、以前に Surface Hub に保存されたパスワードは無効になり、デバイス アカウントを利用するすべての機能が無効になります。 設定アプリで Surface Hub のデバイス アカウントのパスワードを更新して、これらの機能をもう一度有効にする必要があります。

Surface Hub デバイス アカウントのパスワードの管理を簡略化するために、次の 2 つのオプションがあります。

1.  デバイス アカウントのパスワードの有効期限をオフにする。
2.  Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする。


## デバイス アカウントのパスワードの循環をオフにする

デバイス アカウントの **PasswordNeverExpires** プロパティを True に設定します。 この設定が組織のセキュリティ要件を満たしていることを確認する必要があります。


## Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする

Surface Hub では、デバイス アカウントの情報を手動で更新しなくても、デバイス アカウントのパスワードを頻繁に変更して管理できます。 この機能は、**[設定]** で有効にできます。 有効にすると、デバイス アカウントのパスワードは、週ごとにメンテナンス時間に変更されます。

デバイス アカウントのパスワードが変更されても、新しいパスワードは表示されないことに注意してください。 アカウントにサインインする場合や、もう一度パスワードを入力する場合は (たとえば、Surface Hub でのデバイス アカウントの設定を変更する場合)、Active Directory または Office 365 管理ポータルを使ってパスワードをリセットする必要があります。

> [!IMPORTANT]
> 組織でハイブリッド トポロジを使っている場合は (オンプロミスでホストされているサービスと、Office 365 を介してオンラインでホストされているサービスが混在します)、デバイス アカウントを**ドメイン\ユーザー名**形式で設定する必要があります。 そうしないと、パスワードの循環が機能しません。
