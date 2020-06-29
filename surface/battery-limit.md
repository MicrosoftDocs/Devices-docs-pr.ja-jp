---
title: バッテリー制限の設定 (等高線)
description: バッテリー制限は、Surface デバイスのバッテリの充電方法を変更する UEFI の設定であり、その寿命を延長する可能性があります。
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
ms.date: 5/06/2020
ms.openlocfilehash: 927f00681bd5756f380025adf00a08a34a3f411f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835989"
---
# バッテリーの制限の設定

[バッテリー制限] オプションは、Surface デバイスのバッテリの充電方法を変更する UEFI 設定で、その寿命を延長する可能性があります。 この設定は、デバイスがキオスクのソリューションに統合されている場合など、デバイスが継続的に電源に接続されている場合にお勧めします。  

## バッテリの制限のしくみ

バッテリー制限でデバイスを設定すると、デバイスのバッテリーを充電するためのプロトコルが変更されます。 バッテリの上限を有効にすると、バッテリの充電量が最大容量の50% に制限されます。 Windows で報告される充電レベルは、この制限を反映します。 そのため、バッテリーが50% まで充電され、この制限を超えて充電されないことが示されます。 デバイスの充電率が50% の場合にバッテリの制限を有効にすると、デバイスが接続されていることを示すバッテリアイコンが表示されますが、デバイスが最大充電容量の50% に到達するまで放電します。  

## サポートされるデバイス
バッテリー制限 UEFI 設定は、Surface Pro 7 と Surface ノート Pc 3 を含む最新の Surface デバイスに組み込まれています。 以前のデバイスでは[SURFACE UEFI ファームウェアの更新](manage-surface-driver-and-firmware-updates.md)が必要です。 Windows update または[surface サポートサイト](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface)の MSI ドライバーとファームウェアパッケージを通じて入手できます。 サポートされている各デバイスに必要な特定の Surface UEFI バージョンのために[長時間接続する必要がある surface デバイスに対して、"バッテリー制限" を有効](https://support.microsoft.com/help/4464941)にすることを確認します。 

## Surface UEFI でのバッテリー制限の有効化 (Surface Pro 4 以降)

Surface UEFI バッテリ制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。 [**ブート構成**] を選択し、[**詳細オプション**] で [**バッテリー制限モードを有効**にする] を **[オン**] に切り替えます。  

![詳細オプションのスクリーンショット](images/enable-bl.png) 

## Surface の移動と Surface 移動でのバッテリ制限の有効化2
Surface バッテリー制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。 [**ブート構成**] を選択し、[**キオスクモード**] の下にあるスライダーを右に動かして、[バッテリーの上限] を [**有効**] に設定します。  

![Surface Go のキオスクモードのバッテリー制限のスクリーンショット](images/go-batterylimit.png) 

## Surface UEFI でのバッテリー制限の有効化 (Surface Pro 3)

Surface UEFI バッテリ制限の設定は、Surface UEFI でブートして構成できます (デバイスをオンにすると、**Power + Vol Up** )。 [**キオスクモード**] を選択し、[**バッテリーの上限**] を選択して、[**有効**] を選びます。

![詳細オプションのスクリーンショット](images/enable-bl-sp3.png) 

![詳細オプションのスクリーンショット](images/enable-bl-sp3-2.png) 

## Surface Enterprise Management Mode (SEMM) または Surface Pro 3 ファームウェア PowerShell スクリプトを使用してバッテリ制限を有効にする

Surface UEFI バッテリ制限は、次の方法で構成することもできます。

- Surface Pro 4 以降 
    - [Microsoft Surface UEFI コンフィギュレーター](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - Surface [Tools FOR IT をダウンロードするため](https://www.microsoft.com/download/details.aspx?id=46703)の Surface UEFI Manager Powershell スクリプト (SEMM_Powershell.zip)
- Surface Pro 3 
    - [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)

### Microsoft Surface UEFI コンフィギュレーターの使用

バッテリー制限モードを構成するには、SEMM (Surface Pro 4 以降) の **[詳細設定**] 構成ページで [ **Kiosk Overrides** ] 設定を設定します。

![詳細設定のスクリーンショット](images/semm-bl.png)

### Surface UEFI Manager PowerShell スクリプトを使用する

バッテリー制限機能は、次の設定によって制御されます。  

`407 = Battery Profile`

**説明**: バッテリ使用パターンのアクティブな管理スキーム

**既定値**:  `0` 

バッテリの上限を有効にするには、これを設定し `1` ます。

### Surface Pro 3 のファームウェアツールの使用

バッテリー制限機能は、次の設定によって制御されます。  

**名前**: BatteryLimitEnable

**説明**: BatteryLimit

**現在の値**:  `0` 

**既定値**: `0`

**提案**された値: `0` 

バッテリの上限を有効にするには、これを設定し `1` ます。

>[!NOTE]
>この設定を構成するには、 [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)を使用する必要があります。 

