---
title: Surface DMA 保護
description: この記事では、互換性のある Surface デバイスでの DMA 保護について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 1/14/2021
ms.reviewer: carlol
manager: laurawi
audience: itpro
appliesto:
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.openlocfilehash: af5187a2b110804a2dff82291f1d5f912ac61a7b
ms.sourcegitcommit: d4e2a29aa21a911ee55642cd66b4337b89eebdd8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "11270622"
---
# <span data-ttu-id="5f2c9-103">Surface デバイスでの DMA 保護</span><span class="sxs-lookup"><span data-stu-id="5f2c9-103">DMA Protection on Surface devices</span></span>

<span data-ttu-id="5f2c9-104">直接メモリ アクセス (DMA) 保護は、リムーバブル SSD または外部ストレージ デバイスの使用に関連する潜在的なセキュリティ脆弱性を軽減するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-104">Direct Memory Access (DMA) protection is designed to mitigate potential security vulnerabilities associated with using removable SSDs or external storage devices.</span></span> <span data-ttu-id="5f2c9-105">新しい Surface デバイスでは、DMA 保護が既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-105">Newer Surface devices come with DMA Protection enabled by default.</span></span> <span data-ttu-id="5f2c9-106">これには Surface Pro 7 以上が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-106">These include Surface Pro 7+.</span></span> <span data-ttu-id="5f2c9-107">Surface Pro 7、Surface Laptop 3、Surface Pro X。 デバイスに DMA 保護機能が存在する状態を確認するには、次の図に示すように、[システム**情報]** ([スタート]  >  \*\* \*\*msinfo32.exe) を開きます。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-107">Surface Pro 7, Surface Laptop 3, and Surface Pro X.  To check the presence of DMA protection feature on your device, open System Information (**Start** > **msinfo32.exe**), as shown in the figure below.</span></span>

![DMA 保護が有効になっているシステム情報](images/systeminfodma.png)

<span data-ttu-id="5f2c9-109">Surface リムーバブル SSD が改ざんされた場合、デバイスは電源をシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-109">If a Surface removable SSD is tampered with, the device will shutoff power.</span></span> <span data-ttu-id="5f2c9-110">その結果、UEFI はメモリをワイプし、残余データを消去します。</span><span class="sxs-lookup"><span data-stu-id="5f2c9-110">The resulting reboot causes UEFI to wipe memory, to erase any residual data.</span></span>
