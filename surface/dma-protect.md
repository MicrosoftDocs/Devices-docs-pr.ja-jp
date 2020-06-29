---
title: Surface DMA 保護
description: この記事では、互換性のある Surface デバイスでの DMA の保護について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 6/10/2020
ms.reviewer: carlol
manager: laurawi
audience: itpro
ms.openlocfilehash: 00994263cd61086ab86996920543a717a63d5078
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835109"
---
# <span data-ttu-id="488b4-103">Surface デバイスでの DMA の保護</span><span class="sxs-lookup"><span data-stu-id="488b4-103">DMA Protection on Surface devices</span></span>

<span data-ttu-id="488b4-104">DMA (直接メモリアクセス) の保護は、リムーバブルの SSDs または外部ストレージデバイスの使用に関連する潜在的なセキュリティの脆弱性を軽減するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="488b4-104">Direct Memory Access (DMA) protection is designed to mitigate potential security vulnerabilities associated with using removable SSDs or external storage devices.</span></span> <span data-ttu-id="488b4-105">新しい Surface デバイスには、既定で DMA 保護が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="488b4-105">Newer Surface devices come with DMA Protection enabled by default.</span></span> <span data-ttu-id="488b4-106">これには Surface Pro 7、Surface ラップトップ3、Surface Pro X が含まれます。 デバイスで DMA 保護機能が存在するかどうかを確認するには、次の図に示すように、[システム情報 (**Start**  >  **msinfo32.exe**) を開きます。</span><span class="sxs-lookup"><span data-stu-id="488b4-106">These include Surface Pro 7, Surface Laptop 3, and Surface Pro X.  To check the presence of DMA protection feature on your device, open System Information (**Start** > **msinfo32.exe**), as shown in the figure below.</span></span>

![DMA 保護が有効になっているシステム情報](images/systeminfodma.png)

<span data-ttu-id="488b4-108">リムーバブル SSD の表面が改ざんされた場合は、デバイスの電源がシャットオフになります。</span><span class="sxs-lookup"><span data-stu-id="488b4-108">If a Surface removable SSD is tampered with, the device will shutoff power.</span></span> <span data-ttu-id="488b4-109">再起動によって、UEFI でメモリが消去され、残留データが消去されます。</span><span class="sxs-lookup"><span data-stu-id="488b4-109">The resulting reboot causes UEFI to wipe memory, to erase any residual data.</span></span>
