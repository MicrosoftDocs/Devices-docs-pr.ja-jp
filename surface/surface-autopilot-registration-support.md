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
ms.openlocfilehash: 4ff3803701ffe71e1c5c0c36200c40e833a7fb25
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271391"
---
# <span data-ttu-id="38215-103">Windows Autopilot の Surface 登録サポート</span><span class="sxs-lookup"><span data-stu-id="38215-103">Surface Registration Support for Windows Autopilot</span></span>

<span data-ttu-id="38215-104">Windows Autopilot 展開用に Surface デバイスを登録するプロセスが簡略化されました。Microsoft サポートから利用できます。</span><span class="sxs-lookup"><span data-stu-id="38215-104">A simplified process of registering Surface devices for Windows Autopilot deployment is now available from Microsoft Support.</span></span> <span data-ttu-id="38215-105">2020 年 9 月から、お客様と Microsoft クラウド ソリューション プロバイダー (CSP) は、Microsoft サポートに要求を送信することで Surface デバイスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="38215-105">Beginning September 2020, customers and Microsoft Cloud Solution Providers (CSPs) can register Surface devices by submitting requests to Microsoft Support.</span></span> <span data-ttu-id="38215-106">このページでは、次のサポートされている Autopilot 登録シナリオの要件の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="38215-106">This page outlines the requirements for the following supported Autopilot registration scenarios:</span></span>
 

- <span data-ttu-id="38215-107">**Surface Device Autopilot Registration**.</span><span class="sxs-lookup"><span data-stu-id="38215-107">**Surface Device Autopilot Registration**.</span></span> <span data-ttu-id="38215-108">Surface デバイスを Windows Autopilot に登録する要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="38215-108">Submits request to register Surface devices into Windows Autopilot.</span></span>
- **<span data-ttu-id="38215-109">Surface デバイスのハードウェア ハッシュ要求。</span><span class="sxs-lookup"><span data-stu-id="38215-109">Surface Device Hardware Hash Request.</span></span>** <span data-ttu-id="38215-110">Microsoft サポートに要求を送信して、Microsoft Intune または Microsoft パートナー センターを介してデバイスを自己登録するためにユーザーまたは CSP が使用できるハードウェア ハッシュを提供します。</span><span class="sxs-lookup"><span data-stu-id="38215-110">Submits request to Microsoft Support to provide you with hardware hashes that customers or CSPs can use to self-register devices via Microsoft Intune or the Microsoft Partner Center.</span></span>
- **<span data-ttu-id="38215-111">Surface Device Autopilot Deregistration。</span><span class="sxs-lookup"><span data-stu-id="38215-111">Surface Device Autopilot Deregistration.</span></span>** <span data-ttu-id="38215-112">Windows Autopilot からデバイスを削除する要求を送信します。通常は、デバイスの寿命のシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="38215-112">Submits request to delete devices from Windows Autopilot, typically used in device end of life scenarios.</span></span>

<span data-ttu-id="38215-113">Microsoft サポートに登録要求を提出する前に収集する必要がある情報の詳細については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38215-113">See the following table for details of the information you will need to collect prior to submitting registration requests to Microsoft Support.</span></span>
 
**<span data-ttu-id="38215-114">表 1.</span><span class="sxs-lookup"><span data-stu-id="38215-114">Table 1.</span></span> <span data-ttu-id="38215-115">Autopilot 登録要求に必要な情報</span><span class="sxs-lookup"><span data-stu-id="38215-115">Required information for Autopilot registration requests</span></span>**
 

| <span data-ttu-id="38215-116">必要な情報</span><span class="sxs-lookup"><span data-stu-id="38215-116">Required information</span></span>                   | <span data-ttu-id="38215-117">説明</span><span class="sxs-lookup"><span data-stu-id="38215-117">Description</span></span>                                                                                                                                                                                                                                                                                    | <span data-ttu-id="38215-118">Autopilot Registration</span><span class="sxs-lookup"><span data-stu-id="38215-118">Autopilot Registration</span></span> | <span data-ttu-id="38215-119">ハードウェア ハッシュ要求</span><span class="sxs-lookup"><span data-stu-id="38215-119">Hardware Hash Request</span></span> | <span data-ttu-id="38215-120">Autopilot</span><span class="sxs-lookup"><span data-stu-id="38215-120">Autopilot</span></span><br><span data-ttu-id="38215-121">登録解除</span><span class="sxs-lookup"><span data-stu-id="38215-121">Deregistration</span></span> |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **<span data-ttu-id="38215-122">Azure Active Directory テナント ID</span><span class="sxs-lookup"><span data-stu-id="38215-122">Azure Active Directory Tenant ID</span></span>**   | <span data-ttu-id="38215-123">Azure Active Directory テナント ID は、組織名またはドメインとは異なるグローバル一意識別子 (GUID) です。</span><span class="sxs-lookup"><span data-stu-id="38215-123">Your Azure Active Directory tenant ID is a globally unique identifier (GUID) that is different than your organization name or domain.</span></span><br> <br><span data-ttu-id="38215-124">テナント ID を見つけるには、ここで Azure Portal にサインイン [します](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)。</span><span class="sxs-lookup"><span data-stu-id="38215-124">To find your Tenant ID sign into the Azure Portal [here](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).</span></span> | <span data-ttu-id="38215-125">Y</span><span class="sxs-lookup"><span data-stu-id="38215-125">Y</span></span>                      | <span data-ttu-id="38215-126">N</span><span class="sxs-lookup"><span data-stu-id="38215-126">N</span></span>                     | <span data-ttu-id="38215-127">Y</span><span class="sxs-lookup"><span data-stu-id="38215-127">Y</span></span>                           |
| **<span data-ttu-id="38215-128">Azure Active Directory ドメイン名</span><span class="sxs-lookup"><span data-stu-id="38215-128">Azure Active Directory Domain Name</span></span>** | <span data-ttu-id="38215-129">トップ レベルのドメイン名たとえば、contoso.com。</span><span class="sxs-lookup"><span data-stu-id="38215-129">Your top-level domain name; for example, contoso.com.</span></span>                                                                                                                                                                                                                                          | <span data-ttu-id="38215-130">Y</span><span class="sxs-lookup"><span data-stu-id="38215-130">Y</span></span>                      | <span data-ttu-id="38215-131">N</span><span class="sxs-lookup"><span data-stu-id="38215-131">N</span></span>                     | <span data-ttu-id="38215-132">Y</span><span class="sxs-lookup"><span data-stu-id="38215-132">Y</span></span>                           |
| **<span data-ttu-id="38215-133">所有権の証明</span><span class="sxs-lookup"><span data-stu-id="38215-133">Proof of ownership</span></span>**                 | <span data-ttu-id="38215-134">元の販売請求書または請求書を PDF 形式でアップロードして、所有権の証明を確認します。</span><span class="sxs-lookup"><span data-stu-id="38215-134">Verify proof of ownership by uploading the original bill of sale or invoice in PDF format.</span></span> <span data-ttu-id="38215-135">スクリーンショットは受け付けされません。</span><span class="sxs-lookup"><span data-stu-id="38215-135">Screenshots are not accepted.</span></span><br> <br><span data-ttu-id="38215-136">販売請求書には、次のものが含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="38215-136">The bill of sale or invoice  must include the following:</span></span><br><span data-ttu-id="38215-137">デバイスのシリアル番号。</span><span class="sxs-lookup"><span data-stu-id="38215-137">Device serial numbers.</span></span><br><span data-ttu-id="38215-138">会社名。</span><span class="sxs-lookup"><span data-stu-id="38215-138">Company name.</span></span>                                                           | <span data-ttu-id="38215-139">Y</span><span class="sxs-lookup"><span data-stu-id="38215-139">Y</span></span>                      | <span data-ttu-id="38215-140">Y</span><span class="sxs-lookup"><span data-stu-id="38215-140">Y</span></span>                     | <span data-ttu-id="38215-141">Y</span><span class="sxs-lookup"><span data-stu-id="38215-141">Y</span></span>                           |
| **<span data-ttu-id="38215-142">デバイスのシリアル番号</span><span class="sxs-lookup"><span data-stu-id="38215-142">Device serial numbers</span></span>**              | <span data-ttu-id="38215-143">新しい行に各デバイスのシリアル番号を含む CSV 形式の Excel ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="38215-143">Upload Excel file in CSV format with each device serial number in a new line.</span></span>                                                                                                                                                                                                                  | <span data-ttu-id="38215-144">Y</span><span class="sxs-lookup"><span data-stu-id="38215-144">Y</span></span>                      | <span data-ttu-id="38215-145">Y</span><span class="sxs-lookup"><span data-stu-id="38215-145">Y</span></span>                     | <span data-ttu-id="38215-146">Y</span><span class="sxs-lookup"><span data-stu-id="38215-146">Y</span></span>                           |

 

## <span data-ttu-id="38215-147">サポート要求を送信する</span><span class="sxs-lookup"><span data-stu-id="38215-147">Submit support requests</span></span>

  [![G<span data-ttu-id="38215-148">et Autopilot Registration Support for Surface]</span><span class="sxs-lookup"><span data-stu-id="38215-148">et Autopilot Registration Support for Surface]</span></span>(images/autopilot-reg-support-surface.png)](https://prod.support.services.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## <span data-ttu-id="38215-149">詳細情報</span><span class="sxs-lookup"><span data-stu-id="38215-149">Learn more</span></span>

- [<span data-ttu-id="38215-150">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="38215-150">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md)
- [<span data-ttu-id="38215-151">Windows Autopilot を使用して、Intune での Windows デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="38215-151">Enroll Windows devices in Intune by using Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [<span data-ttu-id="38215-152">Windows Autopilot の概要</span><span class="sxs-lookup"><span data-stu-id="38215-152">Overview of Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/windows-autopilot)

 
 
 

