---
title: Microsoft 展開ツールキット (Surface) を使用して Windows 10 を Surface デバイスに展開する
description: Microsoft 展開ツールキットを使用して、Surface デバイスに Windows 10 を展開する方法の推奨されるプロセスについて説明します。
keywords: windows 10 surface、オートメーション、カスタマイズ、mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.date: 10/12/2020
ms.openlocfilehash: 858b6726f1127e3c439864f8946274ed0ea1edd3
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114565"
---
# <span data-ttu-id="89b5f-104">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="89b5f-104">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>

**<span data-ttu-id="89b5f-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="89b5f-105">Applies to</span></span>**

- <span data-ttu-id="89b5f-106">Surface Studio 以降</span><span class="sxs-lookup"><span data-stu-id="89b5f-106">Surface Studio and later</span></span>
- <span data-ttu-id="89b5f-107">Surface Pro 4 以降</span><span class="sxs-lookup"><span data-stu-id="89b5f-107">Surface Pro 4 and later</span></span>
- <span data-ttu-id="89b5f-108">Surface Book 以降</span><span class="sxs-lookup"><span data-stu-id="89b5f-108">Surface Book and later</span></span>
- <span data-ttu-id="89b5f-109">Surface Pc 以降</span><span class="sxs-lookup"><span data-stu-id="89b5f-109">Surface Laptop and later</span></span>
- <span data-ttu-id="89b5f-110">Surface のノート Pc の移動</span><span class="sxs-lookup"><span data-stu-id="89b5f-110">Surface Laptop Go</span></span>
- <span data-ttu-id="89b5f-111">Surface Go</span><span class="sxs-lookup"><span data-stu-id="89b5f-111">Surface Go</span></span>
- <span data-ttu-id="89b5f-112">Surface 3</span><span class="sxs-lookup"><span data-stu-id="89b5f-112">Surface 3</span></span>
- <span data-ttu-id="89b5f-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="89b5f-113">Windows 10</span></span>

> [!NOTE]
> <span data-ttu-id="89b5f-114">MDT は Surface Pro X ではサポートされていません。詳細については、「 [展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b5f-114">MDT is not supported on Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>

<span data-ttu-id="89b5f-115">MDT の使用に関する最新情報については、「 [mdt を使用した Windows 10 イメージの展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b5f-115">For the latest information about using MDT, refer to [Deploy a Windows 10 image using MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).</span></span>

