---
title: Windows Autopilot の Surface 登録サポート
description: この記事では、Autopilot 登録要求を Microsoft サポートに提出する場合の要件について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/14/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: b31cacad5a744dcb29fc3dd2822c656d528fcd40
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304840"
---
# <span data-ttu-id="8cbc7-103">Windows Autopilot の Surface 登録サポート</span><span class="sxs-lookup"><span data-stu-id="8cbc7-103">Surface Registration Support for Windows Autopilot</span></span>

<span data-ttu-id="8cbc7-104">Windows Autopilot 展開用に Surface デバイスを登録するプロセスが簡略化されました。Microsoft サポートから利用できます。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-104">A simplified process of registering Surface devices for Windows Autopilot deployment is now available from Microsoft Support.</span></span> <span data-ttu-id="8cbc7-105">2020 年 9 月から、お客様と Microsoft クラウド ソリューション プロバイダー (CSP) は、Microsoft サポートに要求を送信することで Surface デバイスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-105">Beginning September 2020, customers and Microsoft Cloud Solution Providers (CSPs) can register Surface devices by submitting requests to Microsoft Support.</span></span> <span data-ttu-id="8cbc7-106">このページでは、次のサポートされている Autopilot 登録シナリオの要件の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-106">This page outlines the requirements for the following supported Autopilot registration scenarios:</span></span>
 
- <span data-ttu-id="8cbc7-107">**Surface Device Autopilot Registration**.</span><span class="sxs-lookup"><span data-stu-id="8cbc7-107">**Surface Device Autopilot Registration**.</span></span> <span data-ttu-id="8cbc7-108">Surface デバイスを Windows Autopilot に登録する要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-108">Submits request to register Surface devices into Windows Autopilot.</span></span>
- **<span data-ttu-id="8cbc7-109">Surface デバイスのハードウェア ハッシュ要求。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-109">Surface Device Hardware Hash Request.</span></span>** <span data-ttu-id="8cbc7-110">Microsoft サポートに要求を送信して、Microsoft Intune または Microsoft パートナー センターを介してデバイスを自己登録するために顧客または CSP が使用できるハードウェア ハッシュを提供します。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-110">Submits request to Microsoft Support to provide you with hardware hashes that customers or CSPs can use to self-register devices via Microsoft Intune or the Microsoft Partner Center.</span></span>
- **<span data-ttu-id="8cbc7-111">Surface Device Autopilot Deregistration。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-111">Surface Device Autopilot Deregistration.</span></span>** <span data-ttu-id="8cbc7-112">Windows Autopilot からデバイスを削除する要求を送信します。通常は、デバイスの寿命のシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-112">Submits request to delete devices from Windows Autopilot, typically used in device end of life scenarios.</span></span>

<span data-ttu-id="8cbc7-113">Microsoft サポートに登録要求を提出する前に収集する必要がある情報の詳細については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-113">See the following table for details of the information you will need to collect prior to submitting registration requests to Microsoft Support.</span></span> <span data-ttu-id="8cbc7-114">すべての Surface デバイスの正式なシステム モデル名については [、Surface System SKU リファレンスを参照してください](surface-system-sku-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-114">For the official System Model names of all Surface devices, refer to [Surface System SKU reference](surface-system-sku-reference.md).</span></span>
 
**<span data-ttu-id="8cbc7-115">表 1.</span><span class="sxs-lookup"><span data-stu-id="8cbc7-115">Table 1.</span></span> <span data-ttu-id="8cbc7-116">Autopilot 登録要求に必要な情報</span><span class="sxs-lookup"><span data-stu-id="8cbc7-116">Required information for Autopilot registration requests</span></span>**
 

| <span data-ttu-id="8cbc7-117">必要な情報</span><span class="sxs-lookup"><span data-stu-id="8cbc7-117">Required information</span></span>                   | <span data-ttu-id="8cbc7-118">説明</span><span class="sxs-lookup"><span data-stu-id="8cbc7-118">Description</span></span>                                                                                                                                                                                                                                                                                    | <span data-ttu-id="8cbc7-119">Autopilot Registration</span><span class="sxs-lookup"><span data-stu-id="8cbc7-119">Autopilot Registration</span></span> | <span data-ttu-id="8cbc7-120">ハードウェア ハッシュ要求</span><span class="sxs-lookup"><span data-stu-id="8cbc7-120">Hardware Hash Request</span></span> | <span data-ttu-id="8cbc7-121">Autopilot</span><span class="sxs-lookup"><span data-stu-id="8cbc7-121">Autopilot</span></span><br><span data-ttu-id="8cbc7-122">登録解除</span><span class="sxs-lookup"><span data-stu-id="8cbc7-122">Deregistration</span></span> |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **<span data-ttu-id="8cbc7-123">Azure Active Directory テナント ID</span><span class="sxs-lookup"><span data-stu-id="8cbc7-123">Azure Active Directory Tenant ID</span></span>**   | <span data-ttu-id="8cbc7-124">Azure Active Directory テナント ID は、組織名またはドメインとは異なるグローバル一意識別子 (GUID) です。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-124">Your Azure Active Directory tenant ID is a globally unique identifier (GUID) that is different than your organization name or domain.</span></span><br> <br><span data-ttu-id="8cbc7-125">テナント ID を見つけるには、ここで Azure Portal にサインイン [します](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-125">To find your Tenant ID sign into the Azure Portal [here](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).</span></span> | <span data-ttu-id="8cbc7-126">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-126">Y</span></span>                      | <span data-ttu-id="8cbc7-127">N</span><span class="sxs-lookup"><span data-stu-id="8cbc7-127">N</span></span>                     | <span data-ttu-id="8cbc7-128">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-128">Y</span></span>                           |
| **<span data-ttu-id="8cbc7-129">Azure Active Directory ドメイン名</span><span class="sxs-lookup"><span data-stu-id="8cbc7-129">Azure Active Directory Domain Name</span></span>** | <span data-ttu-id="8cbc7-130">トップ レベルのドメイン名。たとえば、contoso.com。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-130">Your top-level domain name; for example, contoso.com.</span></span>                                                                                                                                                                                                                                          | <span data-ttu-id="8cbc7-131">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-131">Y</span></span>                      | <span data-ttu-id="8cbc7-132">N</span><span class="sxs-lookup"><span data-stu-id="8cbc7-132">N</span></span>                     | <span data-ttu-id="8cbc7-133">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-133">Y</span></span>                           |
| **<span data-ttu-id="8cbc7-134">所有権の証明</span><span class="sxs-lookup"><span data-stu-id="8cbc7-134">Proof of ownership</span></span>**                 | <span data-ttu-id="8cbc7-135">元の販売請求書または請求書を PDF 形式でアップロードして、所有権の証明を確認します。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-135">Verify proof of ownership by uploading the original bill of sale or invoice in PDF format.</span></span> <span data-ttu-id="8cbc7-136">スクリーンショットは受け付けされません。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-136">Screenshots are not accepted.</span></span><br> <br><span data-ttu-id="8cbc7-137">販売請求書には、次のものが含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-137">The bill of sale or invoice  must include the following:</span></span><br><span data-ttu-id="8cbc7-138">デバイスのシリアル番号。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-138">Device serial numbers.</span></span><br><span data-ttu-id="8cbc7-139">会社名。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-139">Company name.</span></span>                                                           | <span data-ttu-id="8cbc7-140">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-140">Y</span></span>                      | <span data-ttu-id="8cbc7-141">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-141">Y</span></span>                     | <span data-ttu-id="8cbc7-142">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-142">Y</span></span>                           |
| **<span data-ttu-id="8cbc7-143">デバイスのシリアル番号</span><span class="sxs-lookup"><span data-stu-id="8cbc7-143">Device serial numbers</span></span>**              | <span data-ttu-id="8cbc7-144">新しい行に各デバイスのシリアル番号を含む CSV 形式の Excel ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="8cbc7-144">Upload Excel file in CSV format with each device serial number in a new line.</span></span>                                                                                                                                                                                                                  | <span data-ttu-id="8cbc7-145">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-145">Y</span></span>                      | <span data-ttu-id="8cbc7-146">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-146">Y</span></span>                     | <span data-ttu-id="8cbc7-147">Y</span><span class="sxs-lookup"><span data-stu-id="8cbc7-147">Y</span></span>                           |

 

## <span data-ttu-id="8cbc7-148">サポート要求を送信する</span><span class="sxs-lookup"><span data-stu-id="8cbc7-148">Submit support requests</span></span>

  [![G<span data-ttu-id="8cbc7-149">et Autopilot Registration Support for Surface]</span><span class="sxs-lookup"><span data-stu-id="8cbc7-149">et Autopilot Registration Support for Surface]</span></span>(images/autopilot-reg-support-surface.png)](https://prod.support.services.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## <span data-ttu-id="8cbc7-150">詳細情報</span><span class="sxs-lookup"><span data-stu-id="8cbc7-150">Learn more</span></span>

- [<span data-ttu-id="8cbc7-151">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="8cbc7-151">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md)
- [<span data-ttu-id="8cbc7-152">Windows Autopilot を使用して、Intune での Windows デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="8cbc7-152">Enroll Windows devices in Intune by using Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [<span data-ttu-id="8cbc7-153">Windows Autopilot の概要</span><span class="sxs-lookup"><span data-stu-id="8cbc7-153">Overview of Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/windows-autopilot)
- [<span data-ttu-id="8cbc7-154">Surface システム SKU リファレンス</span><span class="sxs-lookup"><span data-stu-id="8cbc7-154">Surface System SKU reference</span></span>](surface-system-sku-reference.md)

 
 
 

