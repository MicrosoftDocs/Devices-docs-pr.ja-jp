---
title: Surface デバイス用の長期サービスチャネル (Surface)
description: LTSB は、汎用的なサーフェスデバイスではサポートされていないため、専用デバイスでのみ使うことをお勧めします。
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 591ab98e79ea1ea7d373a3cdf8867601c7c0e832
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835646"
---
# <span data-ttu-id="c7e8a-103">Surface デバイスの長期サービスチャネル (LTSC)</span><span class="sxs-lookup"><span data-stu-id="c7e8a-103">Long-Term Servicing Channel (LTSC) for Surface devices</span></span>

>[!WARNING]
><span data-ttu-id="c7e8a-104">このトピックの最新情報については、「 [Windows 10 の長期サービスチャネルとのサーフェスデバイスの互換性](surface-device-compatibility-with-windows-10-ltsc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-104">For updated information on this topic, see [Surface device compatibility with Windows 10 Long-Term Servicing Channel](surface-device-compatibility-with-windows-10-ltsc.md).</span></span> <span data-ttu-id="c7e8a-105">この更新の詳細については、IT 担当者向けの Surface ブログの「 [surface And Windows 10 LTSB 互換](https://blogs.technet.microsoft.com/surface/2017/04/11/documentation-updates-for-surface-and-windows-10-ltsb-compatibility)投稿」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-105">For additional information on this update, see the [Documentation Updates for Surface and Windows 10 LTSB Compatibility](https://blogs.technet.microsoft.com/surface/2017/04/11/documentation-updates-for-surface-and-windows-10-ltsb-compatibility) post on the Surface Blog for IT Pros.</span></span>

<span data-ttu-id="c7e8a-106">長期サービスチャネル (LTSC) 内の汎用サーフェスデバイスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-106">General-purpose Surface devices in the Long-Term Servicing Channel (LTSC) are not supported.</span></span> <span data-ttu-id="c7e8a-107">一般的なガイドラインとして、Surface デバイスでは、Microsoft Office などの生産性ソフトウェアが実行されている場合、LTSC の対象ではない汎用デバイスであり、代わりに半期チャネルで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-107">As a general guideline, if a Surface device runs productivity software, such as Microsoft Office, it is a general-purpose device that does not qualify for LTSC and should instead be on the Semi-Annual Channel.</span></span> 

>[!NOTE]
><span data-ttu-id="c7e8a-108">サービスブランチの詳細については、「[サービスとしての Windows の概要](https://technet.microsoft.com/itpro/windows/manage/waas-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-108">For more information about the servicing branches, see [Overview of Windows as a service](https://technet.microsoft.com/itpro/windows/manage/waas-overview).</span></span>

<span data-ttu-id="c7e8a-109">LTSC は、重要な Windows 10 機能の更新と特定のセキュリティ以外のサービスの更新を受信しないようにします。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-109">LTSC prevents Surface devices from receiving critical Windows 10 feature updates and certain non-security servicing updates.</span></span> <span data-ttu-id="c7e8a-110">LTSC 構成で Surface デバイスを使用するときに、エクスペリエンスの質が低いお客様には、半期チャネルに切り替えるように指示されます。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-110">Customers with poor experiences using Surface devices in the LTSC configuration will be instructed to switch to the Semi-Annual Channel.</span></span> <span data-ttu-id="c7e8a-111">さらに、Windows 10 Enterprise LTSB edition では、シームレスな手書き入力やタッチ対応アプリケーションなど、Surface デバイスの主要な機能が削除されています。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-111">Furthermore, the Windows 10 Enterprise LTSB edition removes core features of Surface devices, including seamless inking and touch-friendly applications.</span></span> <span data-ttu-id="c7e8a-112">Microsoft Edge、OneNote、カレンダー、またはカメラなどのキー入力アプリケーションが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-112">It does not contain key in-box applications including Microsoft Edge, OneNote, Calendar or Camera.</span></span> <span data-ttu-id="c7e8a-113">そのため、生産性には影響があり、機能は制限されています。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-113">Therefore, productivity is impacted and functionality is limited.</span></span> <span data-ttu-id="c7e8a-114">LTSC は、汎用サーフェスデバイスに適したサービスソリューションとしてはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-114">LTSC is not supported as a suitable servicing solution for general-purpose Surface devices.</span></span> 

<span data-ttu-id="c7e8a-115">汎用サーフェスデバイスは、半年間チャネルで実行されることを想定しており、完全なサービスとファームウェアの更新を受け取り、新しい Surface 機能の導入との互換性を維持することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-115">General-purpose Surface devices are intended to run on the Semi-Annual Channel to receive full servicing and firmware updates and forward compatibility with the introduction of new Surface features.</span></span> <span data-ttu-id="c7e8a-116">半期チャネルでは、Microsoft が機能更新プログラムをリリースするとすぐに利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-116">In the Semi-Annual Channel, feature updates are available as soon as Microsoft releases them.</span></span>

<span data-ttu-id="c7e8a-117">特殊なシナリオ (医療機器、pos システム、Atm を制御する Pc など) の Surface デバイスは、LTSC の使用を検討している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-117">Surface devices in specialized scenarios–such as PCs that control medical equipment, point-of-sale systems, and ATMs–might consider the use of LTSC.</span></span> <span data-ttu-id="c7e8a-118">通常、これらの専用システムは1つのタスクを実行し、組織内の他のデバイスとして機能更新プログラムを必要としません。</span><span class="sxs-lookup"><span data-stu-id="c7e8a-118">These special-purpose systems typically perform a single task and do not require feature updates as frequently as other devices in the organization.</span></span> 

## <span data-ttu-id="c7e8a-119">関連トピック</span><span class="sxs-lookup"><span data-stu-id="c7e8a-119">Related topics</span></span>

- [<span data-ttu-id="c7e8a-120">IT 担当者向けの Surface のブログ</span><span class="sxs-lookup"><span data-stu-id="c7e8a-120">Surface IT Pro Blog</span></span>](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/bg-p/SurfaceITPro)

