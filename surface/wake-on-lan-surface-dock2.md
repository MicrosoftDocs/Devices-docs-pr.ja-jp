---
title: Surface ドック 2 を使用して LAN をスリープ解除する
description: Surface Dock 2 では、Wake on LAN (WOL) の最適なサポートが提供され、管理者はデバイスをリモートで起動し、管理タスクを自動的に実行できます。
keywords: 更新、展開、ドライバー、wol、wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.date: 6/03/2021
ms.openlocfilehash: 74b36b60cb58ecb9042b73b8cdba7271d0af8c80
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614108"
---
# <a name="wake-on-lan-with-surface-dock-2"></a>Surface ドック 2 を使用して LAN をスリープ解除する

デバイスを完全に最新の状態に保つために、IT 管理者は、通常は夜間のメンテナンス期間中に、使用していないデバイスを管理できる必要があります。 Surface Dock 2 では、Wake on LAN (WOL) に最適なサポートが提供され、管理者はデバイスをリモートで起動し、Microsoft エンドポイント マネージャー または他のサード パーティ製ソリューションを使用して管理タスクを自動的に実行できます。

## <a name="requirements"></a>要件

デバイスは、Surface ドック 2 との有線接続を持ち、AC Power に接続されている必要があります。

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a>サポートされている Surface デバイス

- Surface Laptop 4 (Intel プロセッサ)
- Surface Laptop 4 (AMD プロセッサ)
- Surface Laptop 3 (Intel プロセッサ)
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Go 2
- Surface LaptopGo
- Surface Book 3

Surface Dock 2 は、次の電源状態のデバイスに WOL サポートを提供します。

- コネクト スタンバイ
- 休止状態 (S4 電源状態)
- 休止状態 (S5 "soft off" 電源状態)

電源状態の詳細については [、「System Power States」を参照してください](/windows/win32/power/system-power-states)。

## <a name="how-it-works"></a>動作のしくみ

使用しない場合、Surface デバイスは、モダン スタンバイまたは接続スタンバイと呼ばれるアイドル状態の低電力状態になります。 IT 管理者は、対象の Surface デバイスのメディア アクセス制御 (MAC) アドレスを含むウェイク 要求 (マジック パケット) を使用してデバイスをリモートでトリガーできます。 WOL の組み込Microsoft Endpoint Configuration Managerサポートを提供する Microsoft Storeサードパーティ製アプリなど、多くの管理ソリューション。

Surface ドック 2 を使用しないデバイスで WOL を有効にするには [、「Wake on LAN for Surface デバイス」を参照してください](wake-on-lan-for-surface-devices.md)。

## <a name="learn-more"></a>詳細情報

- [Surface Dock 2](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [Surface デバイス での Wake On LAN の使用](wake-on-lan-for-surface-devices.md)
- [システムの電源状態](/windows/win32/power/system-power-states)
- [Wake on LAN の構成 - Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)
