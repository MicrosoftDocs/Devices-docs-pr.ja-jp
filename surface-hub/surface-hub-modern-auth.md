---
title: Surface Hub での先進認証
description: このページでは、従来の基本認証とは対照的に、Surface Hub での先進認証の使用について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/21/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 387d799e15ae25bb1043e9ee3417aa3c31676825
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893154"
---
# Surface Hub での先進認証

クラウドベースのアカウントの先進認証のサポートは、Windows 10 Team 2020 Update に完全に統合されています。これにより、従来の基本認証から移行したり、Microsoft Azure と Exchange Online の最新のセキュリティ向上を利用したりすることができます。 2020更新プログラムでは、Surface Hub は Exchange Web サービス (EWS) プロトコルと Active Directory Authentication Library (ADAL) ベースの認証をサポートしており、デバイスアカウントの同期に Exchange Online を有効にします。

新しいクラウドベースのアカウントの場合、Surface Hub は、format [alias@contoso.com](mailto:alias@contoso.com)を使ってデバイスアカウントを作成するだけでなく、追加の構成を必要とせずに、自動的に先進認証を使用して Exchange Online に接続します。 モダン認証でサポートされていない従来の形式 (Contoso\alias) は使用しないでください。 詳細については、「 [Surface Hub のデバイスアカウントを作成する](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)」を参照してください。

> [!NOTE]
> Surface Hub は、オンプレミスアカウントの先進認証をサポートしていません。 アカウントがクラウドで作成されている必要があります。

