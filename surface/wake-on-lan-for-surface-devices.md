---
title: Surface デバイス用のスリープ解除 (LAN) (Surface)
description: Wake On LAN を使ってデバイスをリモートでスリープ解除して管理タスクやメンテナンス タスクを実行する方法、または管理ソリューションを自動的に有効にする方法 (デバイスの電源が切っている場合でも) を参照してください。
keywords: 更新, 展開, ドライバー, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 709286cc0d62bd0b4c1e28e7626529fc4a215ae2
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271124"
---
# Surface デバイス での Wake On LAN の使用

Windows 10 バージョン 1607 (Windows 10 Anniversary Update とも呼ばれる) 以降を実行し、Surface イーサネット アダプターを使って有線ネットワークに接続する Surface デバイスは、コネクト スタンバイから Wake On LAN (WOL) を使用できます。 WOL を使用すると、デバイスをリモートで起動して管理タスクやメンテナンス タスクを実行したり、管理ソリューション (Microsoft Endpoint Configuration Manager など) を自動的に有効にできます。 たとえば、オフィスが空の夜間のウィンドウで Microsoft Endpoint Configuration Manager を使用して、Surface ドックまたは Surface Pro 3 ドッキング ステーションにドッキングされた Surface デバイスにアプリケーションを展開できます。

>[!NOTE]
>WOL をサポートするには、Surface デバイスを AC 電源と接続スタンバイ (スリープ) に接続する必要があります。 休止状態にあるデバイスや電源がオフになっているデバイスでは、WOL を使用できません。

## サポートされるデバイス

WOL では、次のデバイスがサポートされています。

* Surface Ethernet アダプター
* Surface USB-C からイーサネットおよび USB アダプター
* Surface ドック
* Surface Pro 3 用 Surface ドッキング ステーション
* Surface 3
* Surface Pro 3
* Surface Pro 4
* Surface Pro (第 5 世代)
* Surface Pro (第 5 世代) LTE Advanced
* Surface Book
* Surface Laptop (第 1 世代)
* Surface Pro 6
* Surface Book 2
* Surface Laptop 2
* Surface Go
* Surface Go LTE Advanced
* Surface Studio 2 (下記の Surface Studio 2 の手順を参照)
* Surface Pro 7
* Surface Laptop 3
* Surface Laptop Go
* Surface Pro 7+

## WOL ドライバー

Surface デバイスで WOL サポートを有効にするには、Surface イーサネット アダプター用の特定のドライバーが必要です。 このドライバーは、Surface デバイスの標準のドライバーおよびファームウェア パックには含まれていません。別途ダウンロードしてインストールする必要があります。 Surface WOL ドライバー (SurfaceWOL.msi) は、Microsoft ダウンロード センターの [[Surface Tools for IT]](https://www.microsoft.com/download/details.aspx?id=46703) ページからダウンロードできます。

Surface デバイスでこの Microsoft Windows インストーラー (.msi) ファイルを実行して Surface WOL ドライバーをインストールしたり、Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して Surface デバイスに配布することができます。 展開中に Surface WOL ドライバーを含めるには、展開プロセス中に .msi ファイルをアプリケーションとしてインストールします。 展開プロセスに含める Surface WOL ドライバー ファイルを抽出することもできます。 たとえば、Microsoft Deployment Toolkit (MDT) 展開共有に含めできます。 MDT による Surface の展開の詳細については、「Microsoft Deployment Toolkit を使った Surface デバイスへの [Windows 10 の展開」をご覧ください](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt)。

> [!NOTE]
> SurfaceWOL.msi のインストール時に、次のレジストリ キーの値を 1 に設定すると、WOL ドライバーがインストールされているシステムを簡単に識別できます。 展開中にこれらのドライバーを個別に抽出してインストールすることを選択した場合、このレジストリ キーは構成されません。また、手動またはスクリプトを使用して構成する必要があります。
> 
> **HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests** 

SurfaceWOL.msi の内容を抽出するには、次の例に示すように MSIExec 管理インストール オプション (**/a)** を使用して、コンテンツを C:\WOL\ フォルダーに抽出します。

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## Surface Studio 2 の手順

Surface Studio 2 で WOL を有効にするには、次の手順を使用する必要があります。

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

2. 次のコマンドを実行します。

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```

## Surface WOL の使用

Surface WOL ドライバーは WOL 標準に準拠しています。この場合、デバイスは、魔法のパケットと呼ばれる特別なネットワーク通信によって発生します。 この魔法のパケットは、255 の 6 バイト (または 16 進数の FF) と、ターゲット コンピューターの MAC アドレスの 16 回の繰り返しで構成されます。 魔法のパケットと WOL 標準の詳細については [、Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet)を参照してください。

>[!NOTE]
>WOL を使用して魔法のパケットを送信し、デバイスをスリープ解除するには、ターゲット デバイスとイーサネット アダプターの MAC アドレスを知っている必要があります。 この魔法のパケットは IP ネットワーク プロトコルを使用しないので、デバイスの IP アドレスまたは DNS 名を使用することはできません。

Configuration Manager などの多くの管理ソリューションは、WOL の組み込みサポートを提供します。 また、Microsoft Store アプリ、PowerShell モジュール、サード パーティ製アプリケーション、サード パーティ製の管理ソリューションなど、多くのソリューションを使用して、デバイスをスリープ解除する魔法のパケットを送信できます。 たとえば、TechNet スクリプト センターの [Wake On LAN PowerShell](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) モジュールを使用できます。 

>[!NOTE]
>デバイスが魔法のパケットで起動された後、アプリケーションがシステム上のスリープをアクティブに妨げない場合、または AllowSystemRequiredPowerRequests レジストリ キーが 1 に構成されていない場合、デバイスはスリープ状態に戻ります。これにより、アプリケーションはスリープ状態を回避できます。 このレジストリ [キーの詳細については](#wol-driver) 、この記事の WOL ドライバーセクションを参照してください。
