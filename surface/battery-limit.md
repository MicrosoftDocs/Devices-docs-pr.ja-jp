---
title: バッテリー制限の設定 (Surface)
description: バッテリー制限は、Surface デバイスのバッテリーの充電方法を変更し、その寿命を延ばす可能性がある UEFI 設定です。
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.reviewer: jesko
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
manager: laurawi
audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 8ce1dcfc621a547aca9ca1db322f3ed2ce082728
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271144"
---
# バッテリーの制限の設定

バッテリー制限オプションは、Surface デバイスのバッテリーの充電方法を変更し、その寿命を延ばす可能性がある UEFI 設定です。 デバイスがキオスク ソリューションに統合されている場合など、デバイスが継続的に電源に接続されている場合は、この設定をお勧めします。  

##  <a name="how-battery-limit-works"></a>バッテリー制限のしくみ

[バッテリー制限] でデバイスを設定すると、デバイスのバッテリーを充電するプロトコルが変更されます。 バッテリー制限を有効にすると、バッテリ残量は最大容量の 50% に制限されます。 Windows で報告される課金レベルには、この制限が反映されます。 したがって、バッテリーは最大 50% 充電され、この制限を超えて充電されません。 デバイスの充電量が 50% を超えた状態でバッテリー制限を有効にした場合、バッテリー アイコンには、デバイスが接続されているが、デバイスが最大充電容量の 50% に達するまで充電中であることが表示されます。  

##  <a name="supported-devices"></a>サポートされるデバイス

バッテリー制限 UEFI の設定は、Surface Pro 7+、Surface Pro 7、Surface Laptop 3 などの最新の Surface デバイスに組み込されています。 以前のデバイスでは [、Windows](manage-surface-driver-and-firmware-updates.md)Update または Surface サポート サイトの MSI ドライバーおよびファームウェア パッケージから利用できる Surface UEFI ファームウェア更新 [プログラムが必要です](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface)。 サポート [されている各デバイス](https://support.microsoft.com/help/4464941) に必要な特定の Surface UEFI バージョンについて、延長期間に接続する必要がある Surface デバイスに対して [バッテリー制限] を有効にします。 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-4-and-later)"></a>Surface UEFI でのバッテリー制限の有効化 (Surface Pro 4 以降)

Surface UEFI のバッテリー制限の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。** ブート**構成を選択し**、[詳細オプション****] で [バッテリ制限モードを有効にする] を [オン]**に****切り替えます**。  

![バッテリー制限の詳細オプション](images/enable-bl.png) 

##  <a name="enabling-battery-limit-on-surface-go-and-surface-go-2"></a>Surface Go と Surface Go 2 でバッテリー制限を有効にする
Surface Battery Limit の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。** ブート**構成を選択**し、[キオスク**** モード] でスライダーを右に移動し、[バッテリー制限] を [有効] に設定**します**。  

![Surface Go でのキオスク モードのバッテリー制限](images/go-batterylimit.png) 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-3)"></a>Surface UEFI でのバッテリー制限の有効化 (Surface Pro 3)

Surface UEFI のバッテリー制限の設定は、Surface UEFI を起動することで構成できます (デバイスの電源を入れるときに**Power + Vol Up)。** [ **キオスク モード] を選択**し、[バッテリー制限 **] を**選択して、[有効] を **選択します**。

![詳細オプションのスクリーンショット](images/enable-bl-sp3.png) 

![詳細設定オプション](images/enable-bl-sp3-2.png) 

##  <a name="enabling-battery-limit-using-surface-enterprise-management-mode-(semm)-or-surface-pro-3-firmware-powershell-scripts"></a>Surface Enterprise 管理モード (SEMM) または Surface Pro 3 ファームウェア PowerShell スクリプトを使用したバッテリ制限の有効化

Surface UEFI バッテリーの制限は、次の方法で構成に使用できます。

- Surface Pro 4 以降 
    - [Microsoft Surface UEFI コンフィエーター](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - Surface Tools [for IT](https://www.microsoft.com/download/details.aspx?id=46703)ダウンロードの Surface UEFI マネージャー Powershell スクリプト (SEMM_Powershell.zip)
- Surface Pro 3 
    - [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)

###  <a name="using-microsoft-surface-uefi-configurator"></a>Microsoft Surface UEFI コンフィエーターの使用

バッテリー制限モードを構成するには、SEMM (Surface Pro **** 4 以降) の [詳細設定] 構成ページで [キオスクの上書き] 設定を設定します。 ****

![詳細設定のスクリーンショット](images/semm-bl.png)

###  <a name="using-surface-uefi-manager-powershell-scripts"></a>Surface UEFI マネージャー PowerShell スクリプトの使用

バッテリ制限機能は、次の設定によって制御されます。  

`407 = Battery Profile`

**説明**: バッテリ使用パターンのアクティブな管理スキーム

**既定値は次の値です**。  `0` 

バッテリ制限を `1` 有効にするには、これを設定します。

###  <a name="using-surface-pro-3-firmware-tools"></a>Surface Pro 3 ファームウェア ツールの使用

バッテリ制限機能は、次の設定によって制御されます。  

**Name**: BatteryLimitEnable

**説明**: BatteryLimit

**現在の値**:  `0` 

**既定値**: `0`

**提案された値**: `0` 

バッテリ制限を `1` 有効にするには、これを設定します。

>[!NOTE]
>この設定を構成するには、次のコマンドを使用[SP3_Firmware_Powershell_Scripts.zip。 ](https://www.microsoft.com/download/details.aspx?id=46703) 

