---
title: Surface Dock の新機能
description: この記事では、次世代 Surface Dock の新機能について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 12/2/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: b93813498dc19bc7fff95f651fca77ca2c677746
ms.sourcegitcommit: 071ca4874e807bb61a22b38a04f53802478d8391
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "11194843"
---
# Surface Dock の新機能 

Surface Dock 2 (次世代 Surface dock) では、ユーザーは外部モニターと複数の周辺機器を接続して、Surface デバイスから完全に最新のデスクトップエクスペリエンスを得ることができます。 Office、柔軟なワークスペース、または自宅で最大限に活用できるように設計されています。 Surface Dock 2 には、2つのフロントに面した USB C ポート (電話とアクセサリの15ワットの充電電力) が含まれています。 

### 完全なデバイス管理のサポート

Surface Dock 2 は、IT 管理の簡素化を目的として設計されています。管理者は、Windows Update を使用して、または社内のソフトウェア配布ツールを使用して更新プログラムを一元管理できます。

- Surface Enterprise 管理モード (SEMM) を使用すると、IT 管理者は Surface Dock 2 上のポートをセキュリティで保護できます。 詳しくは、「 [Surface Enterprise Management モードでの Secure Surface Dock 2 ポート](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/secure-surface-dock-2-ports-with-surface-enterprise-management/ba-p/1418999)」をご覧ください。
-  Windows Management Instrumentation (WMI) サポートを利用すると、IT 管理者は Surface Dock 2 デバイス間で最新のファームウェア、ポリシーの状態、関連データをリモートで監視および管理できます。 詳細については、「 [WMI を使用して Surface Dock 2 を管理](surface-dock2-wmi.md)する」を参照してください。

## 一般的なシステム要件

- Windows 10 バージョン1809。 Windows 7、Windows 8、または Surface 以外のホストデバイスはサポートされません。 Surface Dock 2 は、次の Surface デバイスで動作します。

  - Surface Pro (第5世代)
  - Surface ラップトップ (第1世代)
  - Surface Pro 6
  - Surface Book 2
  - Surface Laptop 2
  - Surface Go
  - Surface Pro 7
  - Surface Pro X 
  - Surface Laptop 3
  - Surface Book 3
  - Surface Go 2
  - Surface のノート Pc の移動

## Surface Dock 2 コンポーネント

![Surface Dock 2 コンポーネント](./images/surface-dock2.png)
 
### USB

- 2つの正面に面した USB C ポート。
- 2つの後方に面した USB C (gen 2) ポート。
- リア接続の2つの USB ポート。 

### ビデオ
    
- デュアル4K@60hz。 次のデバイスでは、最大2つのディスプレイをサポートしています。

  - Surface Book 3
  - Surface Go 2
  - Surface Pro 7
  - Surface Pro X
  - Surface Laptop 3

- デュアル 4K@ 4K@30Hz。 次のデバイスでは、最大2つのディスプレイをサポートしています。

  - Surface Pro 6
  - Surface Pro (第5世代)
  - Surface Laptop 2
  - Surface ラップトップ (第1世代)
  - Surface Go
  - Surface Book 2

### Ethernet

- 1ギガビットイーサネットポート。 

### 外部電源

- 199ワット (100V-240V をサポート。


## サーフェスドックの比較 

**表 1. Surface Dock と USB-C トラベルハブ**


| コンポーネント                           | Surface ドック                                                | Surface Dock 2                                                                                      | USB-C トラベルハブ |
| ----------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------- |
| \ Flink                            | あり                                                         | あり                                                                                                 | なし               |
| USB-A                               | 2フロントフェーシング USB 3.1 Gen 1<br>2背面向け USB 3.1 Gen 1 | 2リア接続 USB 3.2 Gen 2 (7.5 W power)                                                            | 1 USB 3.1 Gen 2  |
| ミニディスプレイポート                   | リアの見開き 2 (DP 1.2)                                       | なし                                                                                                | なし             |
| USB-C                               | なし                                                        | USB 3.2 Gen 2 のフロントパネル<br>(15 w パワー)<br>2リア接続 USB 3.2 Gen 2 (DP 1.4 a)<br>(7.5 w power) | 1 USB 3.2 Gen 2  |
| 3.5 mm 音声のイン/アウト                 | あり                                                         | あり                                                                                                 | あり              |
| Ethernet                            | ○、1ギガビット                                              | ○1ギガビット                                                                                       | ○、1ギガビット   |
| DC 電源                         | あり                                                         | あり                                                                                                 |                  |
| Kensington lock                     | あり                                                         | あり                                                                                                 |                  |
| リンクケーブルの長さ               | 65cm                                                        | 80cm                                                                                                | 20cm             |
| リンクホストの電源                 | 60W                                                         | 120W                                                                                                | 該当せず              |
| USB 読み込みの電源                      | 30W                                                         | 60W                                                                                                 |                  |
| USB ビットレート                        | 5 Gbps                                                      | 10 Gbps                                                                                             | 10 Gbps          |
| サポートを監視する                     | 2 x 4 kb @30fps、または<br>1 x 4 kb @ 60 fps                         | 2 x 4 Kb @ 60 fps                                                                                      | 1 x 4 Kb @ 60 fps   |
| 接続されたスタンバイ1からの Wake on LAN <sup></sup> | あり                                                         | あり                                                                                                 |                  |
| S4/S5 スリープモードからの Wake on LAN  | なし                                                          | あり                                                                                                 |          あり        |
| ネットワーク PXE ブート                    | あり                                                         | あり                                                                                                 |        あり          |
| SEMM ホストアクセス制御            | なし                                                          | あり                                                                                                 | なし               |
| SEMM ポートアクセス制御 <sup> 2</sup>          | なし                                                          | あり                                                                                                 | なし               |
| サービスのサポート                   | MSI                                                         | Windows Update または MSI                                                                               |                  |

 



1. *休止状態または Power-Off 状態から復帰するには、Surface Enterprise 管理モード (SEMM) またはデバイスファームウェアコントロールインターフェイス (DFCI) を使用した Wake on LAN 用のデバイスを構成する必要があります。 ハイバネーションまたは Power-Off のスリープ解除は Surface Pro 7、Surface ノートブック3、Surface Pro X、surface Book 3、Surface Go 2 でサポートされています。  一部の機能に必要なソフトウェアライセンス。 別途販売されています。*

2. *一部の機能に必要なソフトウェアライセンス。 別途販売されています。*

## 合理化されたデバイス管理

Surface は、Windows Update を使用して、IT 管理者が次のエンタープライズクラスの機能を利用できるようにすることで、管理機能がリリースされました。

- **競合**のない更新。 Windows Update または Microsoft Endpoint Configuration Manager (旧 System Center Configuration Manager-SCCM) またはその他の MSI 展開ツールを使用して、自動的にドックを更新します。 
- **ネットワークからスリープを解除**します。 ユーザーに依存することなく、会社のデバイスを管理してアクセスし、デバイスの電源を入れます。 ドッキングされたデバイスがスリープ、休止状態、または電源オフモードになっている場合でも、エンドポイント構成マネージャーまたは他のエンタープライズ管理ツールを使用して、サービスや管理のためにネットワークからスリープを解除することができます。
- **IT の一元管理**。 ポートをオンまたはオフにして、Surface Dock 2 に接続できるユーザーを制御します。 Surface Dock 2 で使うことができるホストデバイスを制限します。 ドックへのアクセスを1人のユーザーに制限するか、ドックを構成して、チーム内の特定のユーザーのみがアクセスできるようにします。または、会社全体に対してのみアクセスできます。

## 次のステップ

- [Surface Enterprise Management モードでの Secure Surface Dock 2 ポート](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/secure-surface-dock-2-ports-with-surface-enterprise-management/ba-p/1418999)
- [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
- [Surface デバイスの最適な電源設定](maintain-optimal-power-settings-on-Surface-devices.md)
