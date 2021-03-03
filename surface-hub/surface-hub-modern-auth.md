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
ms.openlocfilehash: 1674b7abd74a666e2ab1040f66d9ea548ab3c201
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385165"
---
# <a name="modern-authentication-on-surface-hub"></a>Surface Hub の先進認証

Windows 10 Team 2020 Update では、一部のシナリオでハブ デバイス アカウントのモダン認証のサポートが追加されています。 2020 更新プログラムをインストールすると、デバイス アカウントが Azure Active Directory 経由で認証され、アカウントのメールボックスが Exchange Online でホストされている場合、従来の基本認証から移行して最新のセキュリティ改善を利用できます。 2020 Update では、デバイス アカウントを Exchange Online と同期するときに、Surface Hub は Exchange Web Services (EWS) プロトコルと Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートします。

新しいクラウドベースのアカウントの場合、Surface Hub はモダン認証を自動的に使用して Exchange Online に接続し、単にデバイス アカウントを作成する以外の構成を必要とせずに、次の形式でデバイス アカウントを作成[alias@contoso.com。](mailto:alias@contoso.com) 従来の形式を使用しない – Contoso\alias(最新の認証ではサポートされていません)。 詳細については [、「Create Surface Hub 2S デバイス アカウント」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)。

> [!NOTE]
> Surface Hub では、オンプレミス アカウントの最新の認証はサポートされていません。 アカウントはクラウドに作成する必要があります。

