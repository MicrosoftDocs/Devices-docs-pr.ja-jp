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
ms.date: 04/24/2020
ms.openlocfilehash: b13b0a7fa486d2360c5e69ad1578c85a5e46a91d
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835662"
---
# <span data-ttu-id="c19f0-104">Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="c19f0-104">Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit</span></span>

**<span data-ttu-id="c19f0-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="c19f0-105">Applies to</span></span>**

- <span data-ttu-id="c19f0-106">Surface Studio 以降</span><span class="sxs-lookup"><span data-stu-id="c19f0-106">Surface Studio and later</span></span>
- <span data-ttu-id="c19f0-107">Surface Pro 4 以降</span><span class="sxs-lookup"><span data-stu-id="c19f0-107">Surface Pro 4 and later</span></span>
- <span data-ttu-id="c19f0-108">Surface Book 以降</span><span class="sxs-lookup"><span data-stu-id="c19f0-108">Surface Book and later</span></span>
- <span data-ttu-id="c19f0-109">Surface Pc 以降</span><span class="sxs-lookup"><span data-stu-id="c19f0-109">Surface Laptop and later</span></span>
- <span data-ttu-id="c19f0-110">Surface Go</span><span class="sxs-lookup"><span data-stu-id="c19f0-110">Surface Go</span></span>
- <span data-ttu-id="c19f0-111">Surface 3</span><span class="sxs-lookup"><span data-stu-id="c19f0-111">Surface 3</span></span>
- <span data-ttu-id="c19f0-112">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c19f0-112">Windows 10</span></span>

> [!NOTE]
> <span data-ttu-id="c19f0-113">MDT は Surface Pro X ではサポートされていません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19f0-113">MDT is not supported on Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>

<span data-ttu-id="c19f0-114">MDT の使用に関する最新情報については、「 [mdt を使用した Windows 10 イメージの展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19f0-114">For the latest information about using MDT, refer to [Deploy a Windows 10 image using MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).</span></span>

