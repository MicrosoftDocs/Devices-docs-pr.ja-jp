---
title: Surface デバイス での Wake On LAN の使用
description: Wake On LAN を使用してデバイスをリモートで起動して管理タスクを自動的に実行する方法について説明します。
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
ms.date: 6/04/2021
ms.openlocfilehash: 83989461ca557d27740252149418056688774d3f
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613803"
---
# <a name="wake-on-lan-for-surface-devices"></a>Surface デバイス での Wake On LAN の使用

デバイスを完全に最新の状態に保つために、IT 管理者は、通常は夜間のメンテナンス期間中に、使用していないデバイスを管理できる必要があります。 Wake on LAN (WOL) を使用すると、管理者はデバイスをリモートで起動し、Microsoft エンドポイント マネージャーまたはサード パーティ製のソリューションを使用して管理タスクを自動的に実行できます。

## <a name="requirements"></a>要件

デバイスは AC 電源に接続され、次のいずれかの互換性のあるイーサネット アダプターとの有線接続が必要です。

- Surface USB 3.0 ギガビット イーサネット アダプター
- Surface Ethernet Adapter
- Surface USB-C からイーサネットおよび USB アダプター
- Microsoft USB-C トラベル アダプター ハブ
- Surface ドック
- Surface Dock 2

> [!NOTE]
> Surface Dock 2 は、追加の IT 構成を必要とせずに Wake on LAN を最高のサポートを提供します。 詳細については [、「Wake on LAN for Surface Dock 2」を参照してください。](wake-on-lan-surface-dock2.md)

## <a name="how-it-works"></a>動作のしくみ

使用しない場合、Surface デバイスは、モダン スタンバイまたは接続スタンバイと呼ばれるアイドル状態の低電力状態になります。 IT 管理者は、対象の Surface デバイスのメディア アクセス制御 (MAC) アドレスを含むウェイク 要求 (マジック パケット) を使用してデバイスをリモートでトリガーできます。 WOL の組み込Microsoft Endpoint Configuration Managerサポートを提供する Microsoft Storeサードパーティ製アプリなど、多くの管理ソリューション。 エンドポイント構成マネージャーを使用してデバイスを起動する方法の詳細については [、「Configure Wake on LAN - Configuration Manager」を参照してください](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)。

Wake on LAN のサポートは、スリープ状態 (接続スタンバイまたは休止状態 (S4 電源状態) によって異なります。

## <a name="connected-standby"></a>接続スタンバイ

既定では、Windows 10スタンバイの Surface デバイスの Wake on LAN がサポートされています。

### <a name="supported-surface-devices---connected-standby"></a>サポートされている Surface デバイス - 接続スタンバイ

- Surface Laptop 4 (Intel プロセッサのみ)
- Surface Laptop 3 (Intel プロセッサのみ)
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Go 2
- Surface LaptopGo
- Surface Book 3

## <a name="hibernation"></a>休止状態

デバイスを休止状態から解除するには[、Surface Enterprise](surface-enterprise-management-mode.md)管理モード (SEMM) を介して UEFI ポリシー設定を有効にする必要があります (Surface ドック 2 に接続されているデバイスでは必要ありません)。

### <a name="supported-surface-devices---hibernation"></a>サポートされている Surface デバイス - 休止状態

- Surface Laptop 4 (Intel プロセッサのみ)
- Surface Laptop 3 (Intel プロセッサのみ)
- Surface Pro 7+
- Surface Pro 7
- Surface LaptopGo
- Surface Book 3

### <a name="to-enable-wake-on-lan-uefi-setting"></a>Wake on LAN UEFI の設定を有効にするには

Wake on LAN UEFI 設定を有効にするには、ターゲット デバイスを SEMM に登録し、構成パッケージを作成し、デバイスにパッケージを適用する必要があります。 詳しくは、以下をご覧ください。

- [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
- [SEMM による Surface デバイスの登録と構成](enroll-and-configure-surface-devices-with-semm.md)

1. [**Surface UEFI コンフィギュレーターをダウンロードしてインストールします**](https://www.microsoft.com/download/details.aspx?id=46703)。
2. [構成**パッケージ**  >  **の作成と**  >  **証明書の**  > **保護の開始] を選択します**。
3. [詳細設定]**に移動し****、[Wake on LAN] を [オン]** に**切り替えます**。
4. パッケージをターゲット デバイスに適用します。

    > [!div class="mx-imgBorder"]
    > ![[LAN UEFI のスリープ解除] ポリシー設定を有効にする](images/wol-uefi.png)

## <a name="learn-more"></a>詳細情報

- [Surface Dock 2 の WAKE on LAN](wake-on-lan-surface-dock2.md)
- [Microsoft Surface USB-C からイーサネットおよび USB アダプター](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)
- [Surface USB 3.0 ギガビット イーサネット アダプター](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)
