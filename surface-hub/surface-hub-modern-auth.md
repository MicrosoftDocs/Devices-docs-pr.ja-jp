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
ms.openlocfilehash: dd0b0ad257abbc52c443b075e62db00dcf5713ea
ms.sourcegitcommit: 4b1cfcac090910a3ea634929942063eb51fc54f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "11206281"
---
# <span data-ttu-id="2d033-104">Surface Hub の先進認証</span><span class="sxs-lookup"><span data-stu-id="2d033-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="2d033-105">クラウドベースのアカウントの最新認証のサポートは [、Windows 10 Team 2020 Update に完全に統合されています](surface-hub-2020-update.md)。</span><span class="sxs-lookup"><span data-stu-id="2d033-105">Support for modern authentication of cloud-based accounts is fully integrated in [Windows 10 Team 2020 Update](surface-hub-2020-update.md).</span></span> <span data-ttu-id="2d033-106">2020 更新プログラムをインストールすると、従来の基本認証から移行し、Microsoft Azure と Exchange Online の最新のセキュリティ強化機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d033-106">Once you install the 2020 update, you can migrate from legacy basic authentication and use the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="2d033-107">2020 Update では、Surface Hub は Exchange Web サービス (EWS) プロトコルと Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートし、デバイス アカウントの同期用に Exchange Online を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2d033-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="2d033-108">新しいクラウドベースのアカウントの場合、Surface Hub はモダン認証を自動的に使用して Exchange Online に接続します。単に alias@contoso.com という形式を使用してデバイス アカウントを作成する以外に、追加の構成 [は必要ありません](mailto:alias@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="2d033-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="2d033-109">従来の形式である Contoso\alias は使用しない。これは、最新の認証ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2d033-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="2d033-110">詳しくは [、「Surface Hub 2S デバイス アカウントの作成」をご覧ください](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)。</span><span class="sxs-lookup"><span data-stu-id="2d033-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="2d033-111">Surface Hub では、オンプレミス アカウントの最新の認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2d033-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="2d033-112">アカウントはクラウドで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d033-112">The accounts must be created in the cloud.</span></span>

