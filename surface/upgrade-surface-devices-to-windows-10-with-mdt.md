---
title: Microsoft Deployment Toolkit による Surface デバイスの Windows 10 へのアップグレード (Surface)
description: Surface デバイスへの Windows 10 アップグレードの展開を実行する方法について説明します。
keywords: Windows 10 surface, アップグレード, カスタマイズ, mdt
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
ms.openlocfilehash: e1a1d34c4d32c5e6f95c985e335e405c0d9e59e4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835534"
---
# <span data-ttu-id="8cf5d-104">Microsoft Deployment Toolkit による Surface デバイスの Windows 10 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="8cf5d-104">Upgrade Surface devices to Windows 10 with Microsoft Deployment Toolkit</span></span>

#### <span data-ttu-id="8cf5d-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="8cf5d-105">Applies to</span></span>
- <span data-ttu-id="8cf5d-106">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="8cf5d-106">Surface Pro 6</span></span>
- <span data-ttu-id="8cf5d-107">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="8cf5d-107">Surface Laptop 2</span></span>
- <span data-ttu-id="8cf5d-108">Surface Go</span><span class="sxs-lookup"><span data-stu-id="8cf5d-108">Surface Go</span></span>
- <span data-ttu-id="8cf5d-109">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="8cf5d-109">Surface Go with LTE</span></span>
- <span data-ttu-id="8cf5d-110">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="8cf5d-110">Surface Book 2</span></span>
- <span data-ttu-id="8cf5d-111">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="8cf5d-111">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="8cf5d-112">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="8cf5d-112">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="8cf5d-113">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="8cf5d-113">Surface Laptop</span></span>
- <span data-ttu-id="8cf5d-114">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="8cf5d-114">Surface Studio</span></span>
- <span data-ttu-id="8cf5d-115">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="8cf5d-115">Surface Studio 2</span></span>
- <span data-ttu-id="8cf5d-116">Surface Book</span><span class="sxs-lookup"><span data-stu-id="8cf5d-116">Surface Book</span></span>
- <span data-ttu-id="8cf5d-117">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="8cf5d-117">Surface Pro 4</span></span>
- <span data-ttu-id="8cf5d-118">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="8cf5d-118">Surface 3 LTE</span></span>
- <span data-ttu-id="8cf5d-119">Surface 3</span><span class="sxs-lookup"><span data-stu-id="8cf5d-119">Surface 3</span></span>
- <span data-ttu-id="8cf5d-120">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="8cf5d-120">Surface Pro 3</span></span>
- <span data-ttu-id="8cf5d-121">Surface Pro 2</span><span class="sxs-lookup"><span data-stu-id="8cf5d-121">Surface Pro 2</span></span>
- <span data-ttu-id="8cf5d-122">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="8cf5d-122">Surface Pro</span></span>
- <span data-ttu-id="8cf5d-123">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8cf5d-123">Windows 10</span></span>

<span data-ttu-id="8cf5d-124">デバイスを再イメージ化する従来の展開方法に加えて、Windows 8.1 または Windows 10 を実行している Surface デバイスをアップグレードする管理者は、アップグレード展開のオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8cf5d-124">In addition to the traditional deployment method of reimaging devices, administrators who want to upgrade Surface devices that are running Windows 8.1 or Windows 10 have the option of deploying upgrades.</span></span> <span data-ttu-id="8cf5d-125">アップグレードの展開を実行することにより、ユーザー、アプリ、または構成を削除することなく Windows 10 をデバイスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8cf5d-125">By performing an upgrade deployment, Windows 10 can be applied to devices without removing users, apps, or configuration.</span></span> <span data-ttu-id="8cf5d-126">展開されたデバイスのユーザーは、アップグレード前に使用していたものと同じアプリと設定が適用されたデバイスを引き続き使うことができます。</span><span class="sxs-lookup"><span data-stu-id="8cf5d-126">The users of the deployed devices can simply continue using the devices with the same apps and settings that they used prior to the upgrade.</span></span> 

<span data-ttu-id="8cf5d-127">MDT を使用して Surface デバイスをアップグレードする方法の詳細は、「[MDT を使って Windows 10 のインプレース アップグレードを実行する](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/upgrade-to-windows-10-with-the-microsoft-deployment-toolkit)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cf5d-127">For the latest information about upgrading surface devices using MDT, refer to [Perform an in-place upgrade to Windows 10 with MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/upgrade-to-windows-10-with-the-microsoft-deployment-toolkit).</span></span>

