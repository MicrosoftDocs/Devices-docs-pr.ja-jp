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
ms.openlocfilehash: 215736527121306c712932f57a5a3a853fb3bb20
ms.sourcegitcommit: 366eedceb9f859f5e87ba032b161f248360cb895
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "11445583"
---
# <a name="password-management-surface-hub"></a>パスワード管理 (Surface Hub)

すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。 セキュリティ上の理由から、このパスワードを定期的に変更 (または "循環") することをお勧めします。 ただし、デバイス アカウントのパスワードを変更すると、以前に Surface Hub に保存されたパスワードは無効になり、デバイス アカウントを利用するすべての機能が無効になります。 設定アプリで Surface Hub のデバイス アカウントのパスワードを更新して、これらの機能をもう一度有効にする必要があります。

Surface Hub デバイス アカウントのパスワードの管理を簡略化するために、次の 2 つのオプションがあります。

1.  デバイス アカウントのパスワードの有効期限をオフにする。
2.  Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする。


## <a name="turn-off-password-rotation-for-the-device-account"></a>デバイス アカウントのパスワードの循環をオフにする

デバイス アカウントの **PasswordNeverExpires** プロパティを True に設定します。 この設定が組織のセキュリティ要件を満たしていることを確認する必要があります。


## <a name="allow-the-surface-hub-to-automatically-rotate-the-device-accounts-password"></a>Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする

Surface Hub では、デバイス アカウントのパスワードを手動で更新する必要なく、デバイス アカウントのパスワードを自動的に変更できます。 この機能は、[設定] Surface Hub**アカウント**  >  **で有効**  >  **にできます**。 [パスワードのローテーション] をオンにした場合、Surface Hub はメンテナンス時間中に 7 日ごとにパスワードの変更を試行します。 会議中にパスワードは変更されません。 前回のパスワードローテーションから 7 日が経過したが、Surface Hub がオフの場合は、有効になったときにすぐにパスワードを変更するか、成功するまで 10 分ごとにパスワードの変更を試みます。

自動的に生成されるパスワードには、大文字と小文字、数字、特殊文字の組み合わせを含む 15 ~ 32 文字が含まれています。 デバイス アカウントのパスワードが変更された場合、新しいパスワードは表示されません。 アカウントにサインインする必要がある場合や、もう一度パスワードを入力する必要がある場合 (Surface Hub のデバイス アカウント設定を変更する場合など)、Active Directory または Microsoft 365 管理ポータルを使用してパスワードをリセットする必要があります。

> [!IMPORTANT]
> Surface Hub にデバイス アカウントを追加するときに使用される形式は、パスワード[](prepare-your-environment-for-surface-hub.md)のローテーションを機能するために使用する必要があるデバイスの所属オプションに影響を与えます。 domain\username 形式で **アカウントを追加する** 場合は、初期セットアップ中にハブをオンプレミスの Active Directory に関連付けます。 アカウントを形式で追加する `username@domain.com` 場合は、初期セットアップ中にハブを Azure Active Directory に関連付けします。 そうしないと、パスワードの循環が機能しません。
