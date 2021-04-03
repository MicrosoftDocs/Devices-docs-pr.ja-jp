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
# <a name="modern-authentication-on-surface-hub"></a><span data-ttu-id="a9936-104">Surface Hub の先進認証</span><span class="sxs-lookup"><span data-stu-id="a9936-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="a9936-105">Windows 10 Team 2020 Update では、一部のシナリオでハブ デバイス アカウントのモダン認証のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="a9936-105">The Windows 10 Team 2020 Update adds support for modern authentication of the Hub device account in some scenarios.</span></span> <span data-ttu-id="a9936-106">2020 更新プログラムをインストールすると、デバイス アカウントが Azure Active Directory 経由で認証され、アカウントのメールボックスが Exchange Online でホストされている場合、従来の基本認証から移行して最新のセキュリティ改善を利用できます。</span><span class="sxs-lookup"><span data-stu-id="a9936-106">Once you install the 2020 update, you can migrate from legacy basic authentication to make use of the latest security improvements if the device account authenticates via Azure Active Directory and the account's mailbox is hosted in Exchange Online.</span></span> <span data-ttu-id="a9936-107">2020 Update では、デバイス アカウントを Exchange Online と同期するときに、Surface Hub は Exchange Web Services (EWS) プロトコルと Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a9936-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication when syncing the device account with Exchange Online.</span></span>

<span data-ttu-id="a9936-108">新しいクラウドベースのアカウントの場合、Surface Hub はモダン認証を自動的に使用して Exchange Online に接続し、デバイス アカウントを Surface Hub に追加するだけで、alias@contoso.com 形式を使用して Surface Hub にデバイス アカウントを追加する以外の構成 [は必要ありません](mailto:alias@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="a9936-108">For new cloud-based accounts, the Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply adding the device account to the Surface Hub using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="a9936-109">従来の形式を使用しない – Contoso\alias(最新の認証ではサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="a9936-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="a9936-110">詳細については、「デバイス アカウントの [作成とテスト」を参照してください](create-and-test-a-device-account-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="a9936-110">For more information, see [create and test a device account](create-and-test-a-device-account-surface-hub.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a9936-111">モダン認証は、オンプレミスの Surface Hub アカウントではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a9936-111">Modern authentication is not supported for on-premises Surface Hub accounts.</span></span> <span data-ttu-id="a9936-112">アカウントは、認証に Azure ADのみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9936-112">The accounts must use only Azure AD for authentication.</span></span>
