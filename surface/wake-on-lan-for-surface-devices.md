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
ms.date: 3/19/2021
ms.openlocfilehash: 1fbbf899876d154469d48fa75a179196697205c1
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442167"
---
# <a name="wake-on-lan-for-surface-devices"></a>Surface デバイス での Wake On LAN の使用

Surface Ethernet アダプターを使用して有線ネットワークに接続する Surface デバイスは、コネクト スタンバイから Wake On LAN (WOL) を利用できます。 WOL を使用すると、デバイスをリモートで起動し、Microsoft Endpoint Manager/Microsoft Intune などの管理ソリューションを使用して管理タスクを自動的に実行できます。

## <a name="wol-supported-devices"></a>WOL がサポートするデバイス

- Surface Ethernet アダプター
- Surface USB-C からイーサネットおよび USB アダプター
- Surface Dock 2
- Surface Pro 6 以降
- Surface Book (すべての世代)
- Surface Laptop (すべての世代)
- Surface Go (すべての世代)
- Surface Studio 2 (付録を参照)


## <a name="using-surface-wol"></a>Surface WOL の使用

IT 管理者は、対象のコンピューターの MAC アドレスを含むウェイク オン LAN 要求 (マジック パケット) を使用してデバイスをトリガーできます。 WOL を使用してマジック パケットを送信し、デバイスをスリープ解除するには、ターゲット デバイスとイーサネット アダプターの MAC アドレスを知っている必要があります。 マジック パケットは IP ネットワーク プロトコルを使用しないので、デバイスの IP アドレスまたは DNS 名を使用することはできません。

Microsoft Endpoint Configuration Manager やサード パーティの Microsoft Store アプリなどの多くの管理ソリューションは、WOL の組み込みのサポートを提供します。 デバイスは、接続スタンバイ (スリープ) モードで AC 電源に接続されている必要があります。 エンドポイント構成マネージャーを使用してデバイスを起動する方法の詳細については [、「Configure Wake on LAN - Configuration Manager」を参照してください](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan)。


## <a name="to-check-wol-is-enabled-on-your-device"></a>デバイスで WOL が有効になっているのを確認するには

1. イーサネット接続デバイスで、ネットワーク アダプターを選択し、[プロパティ] を **選択します**。

   > [!div class="mx-imgBorder"]
   > ![Surface Ethernet Adapter](images/surface-ethernet.png)

2. [詳細設定**の構成]**  >  **を選択します**。
3. [最新の **スタンバイ WoL マジック パケット] までスクロールし、[** 有効 **] が** 選択されている必要があります。

     ![デバイスで WOL が有効になっているか確認する](images/ethernet-wol-setting.png)

## <a name="appendix-surface-studio-2"></a>付録: Surface Studio 2

Surface Studio 2 で WOL を有効にするには、次の手順を使用します。

1. 次のレジストリ キーを作成します。

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. 次のコマンドを実行する

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```


## <a name="learn-more"></a>詳細情報

- [Microsoft Surface USB-C からイーサネットおよび USB アダプター](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)

- [Surface USB 3.0 ギガビット イーサネット アダプター](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)
