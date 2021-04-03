---
title: Surface Hub の先進認証
description: このページでは、従来の基本認証とは対照的に、Surface Hub でのモダン認証の使用について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/10/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: 3873d0ac7ffff3fa790f44b474d937772e5a0900
ms.sourcegitcommit: 4ec96ff1cd563d055fa0689a63f136acf2794a2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "11474764"
---
# <a name="modern-authentication-on-surface-hub"></a>Surface Hub の先進認証

Windows 10 Team 2020 Update では、一部のシナリオでハブ デバイス アカウントのモダン認証のサポートが追加されています。 2020 更新プログラムをインストールすると、デバイス アカウントが Azure Active Directory 経由で認証され、アカウントのメールボックスが Exchange Online でホストされている場合、従来の基本認証から移行して最新のセキュリティ改善を利用できます。 2020 Update では、デバイス アカウントを Exchange Online と同期するときに、Surface Hub は Exchange Web Services (EWS) プロトコルと Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートします。

新しいクラウドベースのアカウントの場合、Surface Hub はモダン認証を自動的に使用して Exchange Online に接続し、デバイス アカウントを Surface Hub に追加するだけで、alias@contoso.com 形式を使用して Surface Hub にデバイス アカウントを追加する以外の構成 [は必要ありません](mailto:alias@contoso.com)。 従来の形式を使用しない – Contoso\alias(最新の認証ではサポートされていません)。 詳細については、「デバイス アカウントの [作成とテスト」を参照してください](create-and-test-a-device-account-surface-hub.md)。

> [!NOTE]
> モダン認証は、オンプレミスの Surface Hub アカウントではサポートされていません。 アカウントは、認証に Azure ADのみを使用する必要があります。
