---
title: Surface Hub の先進認証
description: このページでは、従来の基本認証とは対照的に、Surface Hub での先進認証の使用について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 14be433923ca564123952c2d1d7b1c158e725af3
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004469"
---
# Surface Hub の先進認証

クラウドベースのアカウントの先進認証のサポートは、 [Windows Insider プログラム](https://insider.windows.com/)から利用可能なプレビュービルドを含む、Windows 10 Team 2020 の今後の更新プログラムに完全に統合されています。 [プレビュービルドをインストール](surface-hub-install-2020preview.md)すると、従来の基本認証から移行したり、Microsoft Azure および Exchange Online の最新のセキュリティ向上を利用したりできます。 2020更新プログラムでは、Surface Hub は Exchange Web サービス (EWS) プロトコルと Active Directory Authentication Library (ADAL) ベースの認証をサポートしており、デバイスアカウントの同期に Exchange Online を有効にします。

新しいクラウドベースのアカウントの場合、Surface Hub は、format [alias@contoso.com](mailto:alias@contoso.com)を使ってデバイスアカウントを作成するだけでなく、追加の構成を必要とせずに、自動的に先進認証を使用して Exchange Online に接続します。 モダン認証でサポートされていない従来の形式 (Contoso\alias) は使用しないでください。 詳細については、「 [Surface Hub のデバイスアカウントを作成する](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)」を参照してください。

> [!NOTE]
> Surface Hub は、オンプレミスアカウントの先進認証をサポートしていません。 アカウントがクラウドで作成されている必要があります。

