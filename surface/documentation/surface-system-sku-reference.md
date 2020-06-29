---
title: Surface システム SKU リファレンス
description: このトピックでは、特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステム SKU 名のリファレンスを提供します。
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 29cd47beb855c9b643fca42d91c7b316c374fcca
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835102"
---
# <span data-ttu-id="ab5b3-103">Surface System SKU リファレンス</span><span class="sxs-lookup"><span data-stu-id="ab5b3-103">Surface System SKU Reference</span></span>
<span data-ttu-id="ab5b3-104">このドキュメントでは、PowerShell、WMI、および関連ツールを使って、特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステム SKU 名のリファレンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-104">This document provides a reference of System SKU names that you can use to quickly determine the machine state of a specific device using PowerShell, WMI, and related tools.</span></span> 

<span data-ttu-id="ab5b3-105">システム SKU は、Surface デバイスの UEFI レイヤーのシステム管理 BIOS (SMBIOS) テーブルに格納されている変数 (およびシステムモデルおよび他のユーザーと共に含まれます) です。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-105">System SKU is a variable (along with System Model and others) stored in System Management BIOS (SMBIOS) tables in the UEFI layer of Surface devices.</span></span>  <span data-ttu-id="ab5b3-106">"Surface Pro" と "Surface Advanced" という同じシステムモデル名のデバイスを区別する必要がある場合は、必ずシステムの SKU 名を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-106">Use the System SKU name whenever you need to differentiate between devices with the same System Model name, such as Surface Pro and Surface Pro with LTE Advanced.</span></span> 

| **<span data-ttu-id="ab5b3-107">デバイス</span><span class="sxs-lookup"><span data-stu-id="ab5b3-107">Device</span></span>**| **<span data-ttu-id="ab5b3-108">システムモデル</span><span class="sxs-lookup"><span data-stu-id="ab5b3-108">System Model</span></span>** | **<span data-ttu-id="ab5b3-109">システム SKU</span><span class="sxs-lookup"><span data-stu-id="ab5b3-109">System SKU</span></span>**|
| --- | ---| --- |
| <span data-ttu-id="ab5b3-110">Surface 3 WiFI</span><span class="sxs-lookup"><span data-stu-id="ab5b3-110">Surface 3 WiFI</span></span>                                               | <span data-ttu-id="ab5b3-111">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-111">Surface 3</span></span>        | <span data-ttu-id="ab5b3-112">Surface_3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-112">Surface_3</span></span>                        |
| <span data-ttu-id="ab5b3-113">&T の Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="ab5b3-113">Surface 3 LTE AT&T</span></span>                                           | <span data-ttu-id="ab5b3-114">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-114">Surface 3</span></span>        | <span data-ttu-id="ab5b3-115">Surface_3_US1</span><span class="sxs-lookup"><span data-stu-id="ab5b3-115">Surface_3_US1</span></span>                    |
| <span data-ttu-id="ab5b3-116">Surface 3 LTE Verizon</span><span class="sxs-lookup"><span data-stu-id="ab5b3-116">Surface 3 LTE Verizon</span></span>                                        | <span data-ttu-id="ab5b3-117">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-117">Surface 3</span></span>        | <span data-ttu-id="ab5b3-118">Surface_3_US2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-118">Surface_3_US2</span></span>                    |
| <span data-ttu-id="ab5b3-119">Surface 3 LTE 北アメリカ</span><span class="sxs-lookup"><span data-stu-id="ab5b3-119">Surface 3 LTE North America</span></span>                                  | <span data-ttu-id="ab5b3-120">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-120">Surface 3</span></span>        | <span data-ttu-id="ab5b3-121">Surface_3_NAG</span><span class="sxs-lookup"><span data-stu-id="ab5b3-121">Surface_3_NAG</span></span>                    |
| <span data-ttu-id="ab5b3-122">北アメリカ以外の Surface 3 LTE と日本の携帯電話</span><span class="sxs-lookup"><span data-stu-id="ab5b3-122">Surface 3 LTE Outside of North America and T-Mobile In Japan</span></span> | <span data-ttu-id="ab5b3-123">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ab5b3-123">Surface 3</span></span>        | <span data-ttu-id="ab5b3-124">Surface_3_ROW</span><span class="sxs-lookup"><span data-stu-id="ab5b3-124">Surface_3_ROW</span></span>                    |
| <span data-ttu-id="ab5b3-125">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="ab5b3-125">Surface Pro</span></span>                                                  | <span data-ttu-id="ab5b3-126">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="ab5b3-126">Surface Pro</span></span>      | <span data-ttu-id="ab5b3-127">Surface_Pro_1796</span><span class="sxs-lookup"><span data-stu-id="ab5b3-127">Surface_Pro_1796</span></span>                 |
| <span data-ttu-id="ab5b3-128">Surface Pro LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="ab5b3-128">Surface Pro with LTE Advanced</span></span>                                | <span data-ttu-id="ab5b3-129">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="ab5b3-129">Surface Pro</span></span>      | <span data-ttu-id="ab5b3-130">Surface_Pro_1807</span><span class="sxs-lookup"><span data-stu-id="ab5b3-130">Surface_Pro_1807</span></span>                 |
| <span data-ttu-id="ab5b3-131">Surface Book 2 13inch</span><span class="sxs-lookup"><span data-stu-id="ab5b3-131">Surface Book 2 13inch</span></span>                                        | <span data-ttu-id="ab5b3-132">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-132">Surface Book 2</span></span>   | <span data-ttu-id="ab5b3-133">Surface_Book_1832</span><span class="sxs-lookup"><span data-stu-id="ab5b3-133">Surface_Book_1832</span></span>                |
| <span data-ttu-id="ab5b3-134">Surface Book 2 15inch</span><span class="sxs-lookup"><span data-stu-id="ab5b3-134">Surface Book 2 15inch</span></span>                                        | <span data-ttu-id="ab5b3-135">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-135">Surface Book 2</span></span>   | <span data-ttu-id="ab5b3-136">Surface_Book_1793</span><span class="sxs-lookup"><span data-stu-id="ab5b3-136">Surface_Book_1793</span></span>                |
| <span data-ttu-id="ab5b3-137">Surface Go コンシューマー</span><span class="sxs-lookup"><span data-stu-id="ab5b3-137">Surface Go Consumer</span></span>                                          | <span data-ttu-id="ab5b3-138">Surface Go</span><span class="sxs-lookup"><span data-stu-id="ab5b3-138">Surface Go</span></span>       | <span data-ttu-id="ab5b3-139">Surface_Go_1824_Consumer</span><span class="sxs-lookup"><span data-stu-id="ab5b3-139">Surface_Go_1824_Consumer</span></span>         |
| <span data-ttu-id="ab5b3-140">Surface Go コマーシャル</span><span class="sxs-lookup"><span data-stu-id="ab5b3-140">Surface Go Commercial</span></span>                                        | <span data-ttu-id="ab5b3-141">Surface Go</span><span class="sxs-lookup"><span data-stu-id="ab5b3-141">Surface Go</span></span>       | <span data-ttu-id="ab5b3-142">Surface_Go_1824_Commercial</span><span class="sxs-lookup"><span data-stu-id="ab5b3-142">Surface_Go_1824_Commercial</span></span>       |
| <span data-ttu-id="ab5b3-143">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-143">Surface Go 2</span></span>                                                 | <span data-ttu-id="ab5b3-144">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-144">Surface Go 2</span></span>     | <span data-ttu-id="ab5b3-145">Surface_Go_2_1927</span><span class="sxs-lookup"><span data-stu-id="ab5b3-145">Surface_Go_2_1927</span></span>                |
| <span data-ttu-id="ab5b3-146">Surface Pro 6 コンシューマー</span><span class="sxs-lookup"><span data-stu-id="ab5b3-146">Surface Pro 6 Consumer</span></span>                                       | <span data-ttu-id="ab5b3-147">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="ab5b3-147">Surface Pro 6</span></span>    | <span data-ttu-id="ab5b3-148">Surface_Pro_6_1796_Consumer</span><span class="sxs-lookup"><span data-stu-id="ab5b3-148">Surface_Pro_6_1796_Consumer</span></span>      |
| <span data-ttu-id="ab5b3-149">Surface Pro 6 商用</span><span class="sxs-lookup"><span data-stu-id="ab5b3-149">Surface Pro 6 Commercial</span></span>                                     | <span data-ttu-id="ab5b3-150">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="ab5b3-150">Surface Pro 6</span></span>    | <span data-ttu-id="ab5b3-151">Surface_Pro_6_1796_Commercial</span><span class="sxs-lookup"><span data-stu-id="ab5b3-151">Surface_Pro_6_1796_Commercial</span></span>    |
| <span data-ttu-id="ab5b3-152">Surface ノート Pc 2 の利用者</span><span class="sxs-lookup"><span data-stu-id="ab5b3-152">Surface Laptop 2 Consumer</span></span>                                    | <span data-ttu-id="ab5b3-153">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-153">Surface Laptop 2</span></span> | <span data-ttu-id="ab5b3-154">Surface_Laptop_2_1769_Consumer</span><span class="sxs-lookup"><span data-stu-id="ab5b3-154">Surface_Laptop_2_1769_Consumer</span></span>   |
| <span data-ttu-id="ab5b3-155">Surface ノート Pc 2 商用</span><span class="sxs-lookup"><span data-stu-id="ab5b3-155">Surface Laptop 2 Commercial</span></span>                                  | <span data-ttu-id="ab5b3-156">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="ab5b3-156">Surface Laptop 2</span></span> | <span data-ttu-id="ab5b3-157">Surface_Laptop_2_1769_Commercial</span><span class="sxs-lookup"><span data-stu-id="ab5b3-157">Surface_Laptop_2_1769_Commercial</span></span> |

## <span data-ttu-id="ab5b3-158">システム SKU 変数の使用</span><span class="sxs-lookup"><span data-stu-id="ab5b3-158">Using System SKU variables</span></span> 

### <span data-ttu-id="ab5b3-159">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab5b3-159">PowerShell</span></span>

     gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 

### <span data-ttu-id="ab5b3-160">システム情報</span><span class="sxs-lookup"><span data-stu-id="ab5b3-160">System Information</span></span>
<span data-ttu-id="ab5b3-161">システム情報で、デバイスのシステム SKU とシステムモデルを見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-161">You can also find the System SKU and System Model for a device in System Information.</span></span> 
- <span data-ttu-id="ab5b3-162">[ **Start**  >   **MSInfo32**の開始] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-162">Click **Start** >  **MSInfo32**.</span></span>  

### <span data-ttu-id="ab5b3-163">WMI</span><span class="sxs-lookup"><span data-stu-id="ab5b3-163">WMI</span></span>
<span data-ttu-id="ab5b3-164">システム SKU 変数は、Microsoft 展開ツールキット (MDT) または Microsoft Endpoint Configuration Manager のタスクシーケンス WMI 条件で使うことができます。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-164">You can use System SKU variables in a Task Sequence WMI Condition in the Microsoft Deployment Toolkit (MDT) or Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="ab5b3-165">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-165">For example:</span></span> 

    - <span data-ttu-id="ab5b3-166">WMI 名前空間– Root\WMI</span><span class="sxs-lookup"><span data-stu-id="ab5b3-166">WMI Namespace – Root\WMI</span></span>
    - <span data-ttu-id="ab5b3-167">WQL クエリ– SystemSKU = "Surface_Pro_1796" の MS_SystemInformation から \* を選びます。</span><span class="sxs-lookup"><span data-stu-id="ab5b3-167">WQL Query – SELECT \* FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"</span></span>

 
 
 


