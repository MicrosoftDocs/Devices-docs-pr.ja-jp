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
# Surface デバイスでの DMA の保護

DMA (直接メモリアクセス) の保護は、リムーバブルの SSDs または外部ストレージデバイスの使用に関連する潜在的なセキュリティの脆弱性を軽減するために設計されています。 新しい Surface デバイスには、既定で DMA 保護が有効になっています。 これには Surface Pro 7、Surface ラップトップ3、Surface Pro X が含まれます。 デバイスで DMA 保護機能が存在するかどうかを確認するには、次の図に示すように、[システム情報 (**Start**  >  **msinfo32.exe**) を開きます。

![DMA 保護が有効になっているシステム情報](images/systeminfodma.png)

リムーバブル SSD の表面が改ざんされた場合は、デバイスの電源がシャットオフになります。 再起動によって、UEFI でメモリが消去され、残留データが消去されます。
