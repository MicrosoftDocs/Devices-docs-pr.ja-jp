---
title: Windows 自動操縦の表面登録サポート
description: この記事では、Microsoft サポートに対して自動操縦登録リクエストを提出するための要件について説明します。
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
ms.openlocfilehash: 9a308edb37cc2cfd99490acad16bd2ae6a4d458a
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016479"
---
# <span data-ttu-id="f98fa-103">Windows 自動操縦の表面登録サポート</span><span class="sxs-lookup"><span data-stu-id="f98fa-103">Surface Registration Support for Windows Autopilot</span></span>

<span data-ttu-id="f98fa-104">Windows 自動操縦用 Surface デバイスの登録プロセスが簡素化され、Microsoft サポートから利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f98fa-104">A simplified process of registering Surface devices for Windows Autopilot deployment is now available from Microsoft Support.</span></span> <span data-ttu-id="f98fa-105">2020年9月から、お客様と Microsoft Cloud Solution Providers (Csp) は、Microsoft サポートに要求を送信して、Surface デバイスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="f98fa-105">Beginning September 2020, customers and Microsoft Cloud Solution Providers (CSPs) can register Surface devices by submitting requests to Microsoft Support.</span></span> <span data-ttu-id="f98fa-106">このページでは、次のようにサポートされている自動操縦登録シナリオの要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="f98fa-106">This page outlines the requirements for the following supported Autopilot registration scenarios:</span></span>
 

- <span data-ttu-id="f98fa-107">**Surface Device 自動操縦登録**。</span><span class="sxs-lookup"><span data-stu-id="f98fa-107">**Surface Device Autopilot Registration**.</span></span> <span data-ttu-id="f98fa-108">Surface デバイスを Windows 自動操縦に登録するための要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="f98fa-108">Submits request to register Surface devices into Windows Autopilot.</span></span>
- **<span data-ttu-id="f98fa-109">Surface Device ハードウェアハッシュ要求。</span><span class="sxs-lookup"><span data-stu-id="f98fa-109">Surface Device Hardware Hash Request.</span></span>** <span data-ttu-id="f98fa-110">Microsoft サポートにリクエストを送信して、お客様や Csp が Microsoft Intune または Microsoft パートナーセンター経由でデバイスを自己登録するために使用できるハードウェアハッシュを提供します。</span><span class="sxs-lookup"><span data-stu-id="f98fa-110">Submits request to Microsoft Support to provide you with hardware hashes that customers or CSPs can use to self-register devices via Microsoft Intune or the Microsoft Partner Center.</span></span>
- **<span data-ttu-id="f98fa-111">Surface Device 自動操縦登録解除。</span><span class="sxs-lookup"><span data-stu-id="f98fa-111">Surface Device Autopilot Deregistration.</span></span>** <span data-ttu-id="f98fa-112">Windows 自動操縦からデバイスを削除する要求を送信します。通常は、デバイスのサポート終了シナリオで使われます。</span><span class="sxs-lookup"><span data-stu-id="f98fa-112">Submits request to delete devices from Windows Autopilot, typically used in device end of life scenarios.</span></span>

<span data-ttu-id="f98fa-113">登録要求を Microsoft サポートに提出する前に収集する必要がある情報の詳細については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f98fa-113">See the following table for details of the information you will need to collect prior to submitting registration requests to Microsoft Support.</span></span>
 
**<span data-ttu-id="f98fa-114">表 1.</span><span class="sxs-lookup"><span data-stu-id="f98fa-114">Table 1.</span></span> <span data-ttu-id="f98fa-115">自動操縦登録要求に必要な情報</span><span class="sxs-lookup"><span data-stu-id="f98fa-115">Required information for Autopilot registration requests</span></span>**
 

| <span data-ttu-id="f98fa-116">必要な情報</span><span class="sxs-lookup"><span data-stu-id="f98fa-116">Required information</span></span>                   | <span data-ttu-id="f98fa-117">説明</span><span class="sxs-lookup"><span data-stu-id="f98fa-117">Description</span></span>                                                                                                                                                                                                                                                                                    | <span data-ttu-id="f98fa-118">自動操縦の登録</span><span class="sxs-lookup"><span data-stu-id="f98fa-118">Autopilot Registration</span></span> | <span data-ttu-id="f98fa-119">ハードウェアハッシュ要求</span><span class="sxs-lookup"><span data-stu-id="f98fa-119">Hardware Hash Request</span></span> | <span data-ttu-id="f98fa-120">パイロット</span><span class="sxs-lookup"><span data-stu-id="f98fa-120">Autopilot</span></span><br><span data-ttu-id="f98fa-121">登録解除</span><span class="sxs-lookup"><span data-stu-id="f98fa-121">Deregistration</span></span> |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **<span data-ttu-id="f98fa-122">Azure Active Directory テナント ID</span><span class="sxs-lookup"><span data-stu-id="f98fa-122">Azure Active Directory Tenant ID</span></span>**   | <span data-ttu-id="f98fa-123">Azure Active Directory テナント ID は、組織名またはドメインとは異なるグローバル一意識別子 (GUID) です。</span><span class="sxs-lookup"><span data-stu-id="f98fa-123">Your Azure Active Directory tenant ID is a globally unique identifier (GUID) that is different than your organization name or domain.</span></span><br> <br><span data-ttu-id="f98fa-124">テナント ID を検索するに [は、ここで](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)Azure Portal にサインインします。</span><span class="sxs-lookup"><span data-stu-id="f98fa-124">To find your Tenant ID sign into the Azure Portal [here](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).</span></span> | <span data-ttu-id="f98fa-125">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-125">Y</span></span>                      | <span data-ttu-id="f98fa-126">N</span><span class="sxs-lookup"><span data-stu-id="f98fa-126">N</span></span>                     | <span data-ttu-id="f98fa-127">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-127">Y</span></span>                           |
| **<span data-ttu-id="f98fa-128">Azure Active Directory ドメイン名</span><span class="sxs-lookup"><span data-stu-id="f98fa-128">Azure Active Directory Domain Name</span></span>** | <span data-ttu-id="f98fa-129">最上位レベルのドメイン名。たとえば、contoso.com のようになります。</span><span class="sxs-lookup"><span data-stu-id="f98fa-129">Your top-level domain name; for example, contoso.com.</span></span>                                                                                                                                                                                                                                          | <span data-ttu-id="f98fa-130">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-130">Y</span></span>                      | <span data-ttu-id="f98fa-131">N</span><span class="sxs-lookup"><span data-stu-id="f98fa-131">N</span></span>                     | <span data-ttu-id="f98fa-132">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-132">Y</span></span>                           |
| **<span data-ttu-id="f98fa-133">所有権の証明</span><span class="sxs-lookup"><span data-stu-id="f98fa-133">Proof of ownership</span></span>**                 | <span data-ttu-id="f98fa-134">元の販売請求書または請求書を PDF 形式でアップロードして、所有権の証明を確認します。</span><span class="sxs-lookup"><span data-stu-id="f98fa-134">Verify proof of ownership by uploading the original bill of sale or invoice in PDF format.</span></span> <span data-ttu-id="f98fa-135">スクリーンショットは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="f98fa-135">Screenshots are not accepted.</span></span><br> <br><span data-ttu-id="f98fa-136">売上請求書または請求書には、次の情報を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f98fa-136">The bill of sale or invoice  must include the following:</span></span><br><span data-ttu-id="f98fa-137">デバイスのシリアル番号。</span><span class="sxs-lookup"><span data-stu-id="f98fa-137">Device serial numbers.</span></span><br><span data-ttu-id="f98fa-138">会社名。</span><span class="sxs-lookup"><span data-stu-id="f98fa-138">Company name.</span></span>                                                           | <span data-ttu-id="f98fa-139">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-139">Y</span></span>                      | <span data-ttu-id="f98fa-140">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-140">Y</span></span>                     | <span data-ttu-id="f98fa-141">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-141">Y</span></span>                           |
| **<span data-ttu-id="f98fa-142">デバイスのシリアル番号</span><span class="sxs-lookup"><span data-stu-id="f98fa-142">Device serial numbers</span></span>**              | <span data-ttu-id="f98fa-143">各デバイスのシリアル番号を新しい行に CSV 形式で Excel ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="f98fa-143">Upload Excel file in CSV format with each device serial number in a new line.</span></span>                                                                                                                                                                                                                  | <span data-ttu-id="f98fa-144">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-144">Y</span></span>                      | <span data-ttu-id="f98fa-145">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-145">Y</span></span>                     | <span data-ttu-id="f98fa-146">Y</span><span class="sxs-lookup"><span data-stu-id="f98fa-146">Y</span></span>                           |

 

## <span data-ttu-id="f98fa-147">サポートリクエストを送信する</span><span class="sxs-lookup"><span data-stu-id="f98fa-147">Submit support requests</span></span>

  [![G<span data-ttu-id="f98fa-148">et 自動操縦 (Surface の登録サポート)</span><span class="sxs-lookup"><span data-stu-id="f98fa-148">et Autopilot Registration Support for Surface]</span></span>(images/autopilot-reg-support-surface.png)](https://support.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## <span data-ttu-id="f98fa-149">詳細情報</span><span class="sxs-lookup"><span data-stu-id="f98fa-149">Learn more</span></span>

- [<span data-ttu-id="f98fa-150">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="f98fa-150">Windows Autopilot and Surface devices</span></span>](windows-autopilot-and-surface-devices.md)
- [<span data-ttu-id="f98fa-151">Windows Autopilot を使用して、Intune での Windows デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="f98fa-151">Enroll Windows devices in Intune by using Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [<span data-ttu-id="f98fa-152">Windows Autopilot の概要</span><span class="sxs-lookup"><span data-stu-id="f98fa-152">Overview of Windows Autopilot</span></span>](https://docs.microsoft.com/mem/autopilot/windows-autopilot)

 
 
 

