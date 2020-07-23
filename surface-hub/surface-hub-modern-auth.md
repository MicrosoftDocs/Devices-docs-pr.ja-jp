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
# <span data-ttu-id="8b817-104">Surface Hub での先進認証</span><span class="sxs-lookup"><span data-stu-id="8b817-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="8b817-105">クラウドベースのアカウントの先進認証のサポートは、Windows 10 Team 2020 Update に完全に統合されています。これにより、従来の基本認証から移行したり、Microsoft Azure と Exchange Online の最新のセキュリティ向上を利用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b817-105">Support for modern authentication of cloud-based accounts is fully integrated in Windows 10 Team 2020 Update, allowing you to migrate from legacy basic authentication and utilize the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="8b817-106">2020更新プログラムでは、Surface Hub は Exchange Web サービス (EWS) プロトコルと Active Directory Authentication Library (ADAL) ベースの認証をサポートしており、デバイスアカウントの同期に Exchange Online を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b817-106">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="8b817-107">新しいクラウドベースのアカウントの場合、Surface Hub は、format [alias@contoso.com](mailto:alias@contoso.com)を使ってデバイスアカウントを作成するだけでなく、追加の構成を必要とせずに、自動的に先進認証を使用して Exchange Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="8b817-107">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="8b817-108">モダン認証でサポートされていない従来の形式 (Contoso\alias) は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8b817-108">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="8b817-109">詳細については、「 [Surface Hub のデバイスアカウントを作成する](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b817-109">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="8b817-110">Surface Hub は、オンプレミスアカウントの先進認証をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8b817-110">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="8b817-111">アカウントがクラウドで作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b817-111">The accounts must be created in the cloud.</span></span>

