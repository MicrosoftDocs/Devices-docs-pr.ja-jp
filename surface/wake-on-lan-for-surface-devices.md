---
title: Surface devices 用の Wake on LAN (Surface)
description: デバイスに電源が入っていない場合でも、Wake on LAN を使用して、管理またはメンテナンスタスクを実行したり、管理ソリューションを自動的に有効にしたりする方法について説明します。
keywords: update、deploy、driver、wol、wake on-lan
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
ms.openlocfilehash: a56f6e01a4d7bf1cc40d73f34c3abf8e04443989
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114615"
---
# Surface デバイス での Wake On LAN の使用

Windows 10、バージョン 1607 (Windows 10 記念日更新とも呼ばれます) 以降を実行している surface デバイスで、Surface Ethernet アダプターを使って有線ネットワークに接続し、接続されたスタンバイからの Wake On LAN (WOL) 機能を使用できます。 WOL を使用すると、デバイスをリモートでスリープ解除して管理またはメンテナンスタスクを実行したり、管理ソリューション (Microsoft Endpoint Configuration Manager など) を自動的に有効にしたりすることができます。 たとえば、Surface Dock または Surface Pro 3 のドッキングステーションと共にドッキングされた Surface デバイスにアプリケーションを展開するには、office が空になっているときに、夜間中央のウィンドウで Microsoft Endpoint Configuration Manager を使用します。

>[!NOTE]
>WOL をサポートするには、Surface デバイスが AC 電源に接続され、接続されたスタンバイ (スリープ) に接続されている必要があります。 休止状態または電源がオフになっているデバイスから WOL は使用できません。

## サポートされるデバイス

WOL では、次のデバイスがサポートされています。

* Surface Ethernet アダプター
* Surface USB-C ~ Ethernet および USB アダプター
* Surface ドック
* Surface Pro 3 用 surface ドッキングステーション
* Surface 3
* Surface Pro 3
* Surface Pro 4
* Surface Pro (第5世代)
* LTE アドバンスト付き Surface Pro (第5世代)
* Surface Book
* Surface ラップトップ (第1世代)
* Surface Pro 6
* Surface Book 2
* Surface Laptop 2
* Surface Go
* Surface Go LTE Advanced
* Surface Studio 2 (以下の「Surface Studio 2 の手順」を参照)
* Surface Pro 7
* Surface Laptop 3
* Surface のノート Pc の移動

## WOL ドライバー

Surface デバイスで WOL サポートを有効にするには、Surface Ethernet アダプター用の特定のドライバーが必要です。 このドライバーは、Surface デバイス用の標準ドライバーとファームウェアパックに含まれていません。別途ダウンロードしてインストールする必要があります。 Surface WOL ドライバー (SurfaceWOL.msi) は、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。

Surface デバイスでこの Microsoft Windows インストーラー (.msi) ファイルを実行して Surface WOL ドライバーをインストールしたり、Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して Surface デバイスに配布したりすることができます。 展開時に Surface WOL ドライバーを含めるには、展開プロセス中に .msi ファイルをアプリケーションとしてインストールできます。 Surface WOL ドライバーファイルを抽出して展開プロセスに含めることもできます。 たとえば、Microsoft 展開ツールキット (MDT) 展開共有にそれらを含めることができます。 MDT での Surface の展開の詳細については、「 [Windows 10 を surface デバイスに展開して Microsoft 展開ツールキットを使用](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt)する」を参照してください。

> [!NOTE]
> SurfaceWOL.msi のインストール中に、次のレジストリキーが1の値に設定されます。これにより、WOL ドライバーがインストールされているシステムを簡単に識別できるようになります。 展開時にこれらのドライバーを個別に抽出してインストールする場合は、このレジストリキーは構成されず、手動で、またはスクリプトを使って構成する必要があります。
> 
> **HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests** 

SurfaceWOL.msi の内容を抽出するには、次の例に示すように MSIExec 管理インストールオプション (**/a**) を使用して、コンテンツを C:\WOL\ フォルダーに抽出します。

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## Surface Studio 2 の手順

Surface Studio 2 で WOL を有効にするには、次の手順を使用する必要があります。

1. 次のレジストリキーを作成します。

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

Surface WOL ドライバーは、WOL 標準に準拠しているため、デバイスはマジックパケットと呼ばれる特殊なネットワーク通信によって呼び出されます。 Magic packet は、6バイトの 255 (または16進数の FF) で構成され、その後にターゲットコンピューターの MAC アドレスが16回繰り返されます。 この magic packet と [ウィキペディア](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet)の WOL 標準の詳細については、こちらをご覧ください。

>[!NOTE]
>WOL を使って magic packet を送信し、デバイスをウェイクアップするには、ターゲットデバイスとイーサネットアダプターの MAC アドレスがわかっている必要があります。 Magic packet では IP ネットワークプロトコルを使用していないため、デバイスの IP アドレスまたは DNS 名を使うことはできません。

Configuration Manager などの多くの管理ソリューションは、WOL の組み込みサポートを提供しています。 Microsoft ストアアプリ、PowerShell モジュール、サードパーティ製のアプリケーション、サードパーティ製の管理ソリューションなど、デバイスをスリープ状態にするための magic packet を送信できるソリューションも数多くあります。 たとえば、TechNet スクリプトセンターで [Wake ON LAN PowerShell モジュール](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) を使用することができます。 

>[!NOTE]
>デバイスが magic packet で起動された後、アプリケーションがシステムのスリープを積極的に妨害していない場合、または AllowSystemRequiredPowerRequests レジストリキーが1に設定されていない場合は、デバイスはスリープ状態に戻ります。これにより、アプリケーションはスリープを防ぐことができます。 このレジストリキーの詳細については、この記事の「 [WOL ドライバー](#wol-driver) 」セクションを参照してください。
