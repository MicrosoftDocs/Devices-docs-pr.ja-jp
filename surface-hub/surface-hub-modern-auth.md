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
# <span data-ttu-id="c4f03-104">Surface Hub の先進認証</span><span class="sxs-lookup"><span data-stu-id="c4f03-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="c4f03-105">クラウドベースのアカウントの先進認証のサポートは、 [Windows Insider プログラム](https://insider.windows.com/)から利用可能なプレビュービルドを含む、Windows 10 Team 2020 の今後の更新プログラムに完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="c4f03-105">Support for modern authentication of cloud-based accounts is fully integrated in the upcoming Windows 10 Team 2020 Update, with preview builds available from the [Windows Insider Program](https://insider.windows.com/).</span></span> <span data-ttu-id="c4f03-106">[プレビュービルドをインストール](surface-hub-install-2020preview.md)すると、従来の基本認証から移行したり、Microsoft Azure および Exchange Online の最新のセキュリティ向上を利用したりできます。</span><span class="sxs-lookup"><span data-stu-id="c4f03-106">Once you [install the preview build](surface-hub-install-2020preview.md), you can migrate from legacy basic authentication and utilize the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="c4f03-107">2020更新プログラムでは、Surface Hub は Exchange Web サービス (EWS) プロトコルと Active Directory Authentication Library (ADAL) ベースの認証をサポートしており、デバイスアカウントの同期に Exchange Online を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c4f03-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="c4f03-108">新しいクラウドベースのアカウントの場合、Surface Hub は、format [alias@contoso.com](mailto:alias@contoso.com)を使ってデバイスアカウントを作成するだけでなく、追加の構成を必要とせずに、自動的に先進認証を使用して Exchange Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="c4f03-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="c4f03-109">モダン認証でサポートされていない従来の形式 (Contoso\alias) は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c4f03-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="c4f03-110">詳細については、「 [Surface Hub のデバイスアカウントを作成する](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4f03-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="c4f03-111">Surface Hub は、オンプレミスアカウントの先進認証をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c4f03-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="c4f03-112">アカウントがクラウドで作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4f03-112">The accounts must be created in the cloud.</span></span>

