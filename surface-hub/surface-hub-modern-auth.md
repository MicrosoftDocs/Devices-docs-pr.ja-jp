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
# <a name="modern-authentication-on-surface-hub"></a><span data-ttu-id="cb639-104">Surface Hub の先進認証</span><span class="sxs-lookup"><span data-stu-id="cb639-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="cb639-105">Windows 10 Team 2020 Update では、一部のシナリオでハブ デバイス アカウントのモダン認証のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="cb639-105">The Windows 10 Team 2020 Update adds support for modern authentication of the Hub device account in some scenarios.</span></span> <span data-ttu-id="cb639-106">2020 更新プログラムをインストールすると、デバイス アカウントが Azure Active Directory 経由で認証され、アカウントのメールボックスが Exchange Online でホストされている場合、従来の基本認証から移行して最新のセキュリティ改善を利用できます。</span><span class="sxs-lookup"><span data-stu-id="cb639-106">Once you install the 2020 update, you can migrate from legacy basic authentication to make use of the latest security improvements if the device account authenticates via Azure Active Directory and the account's mailbox is hosted in Exchange Online.</span></span> <span data-ttu-id="cb639-107">2020 Update では、デバイス アカウントを Exchange Online と同期するときに、Surface Hub は Exchange Web Services (EWS) プロトコルと Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cb639-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication when syncing the device account with Exchange Online.</span></span>

<span data-ttu-id="cb639-108">新しいクラウドベースのアカウントの場合、Surface Hub はモダン認証を自動的に使用して Exchange Online に接続し、単にデバイス アカウントを作成する以外の構成を必要とせずに、次の形式でデバイス アカウントを作成[alias@contoso.com。](mailto:alias@contoso.com)</span><span class="sxs-lookup"><span data-stu-id="cb639-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="cb639-109">従来の形式を使用しない – Contoso\alias(最新の認証ではサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="cb639-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="cb639-110">詳細については [、「Create Surface Hub 2S デバイス アカウント」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)。</span><span class="sxs-lookup"><span data-stu-id="cb639-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="cb639-111">Surface Hub では、オンプレミス アカウントの最新の認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cb639-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="cb639-112">アカウントはクラウドに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb639-112">The accounts must be created in the cloud.</span></span>

