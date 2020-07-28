---
title: Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する
description: この記事では、Surface デバイスのファームウェアとドライバーの更新プログラムを管理および展開するために使用できるオプションについて説明します。
ms.assetid: CD1219BA-8EDE-4BC8-BEEF-99B50C211D73
ms.reviewer: ''
manager: laurawi
keywords: Surface, Surface Pro 3, ファームウェア, 更新プログラム, デバイス, 管理, 展開, ドライバー, USB, Surface, Surface Pro 3, firmware, update, device, manage, deploy, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: f41974193d62e4c0cbc1e286976105c20534d906
ms.sourcegitcommit: ed4478dd3c6116a25b1e01a3a0f5ff6c1f940013
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "10897065"
---
# Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する

Surface ドライバーとファームウェア更新プログラムの管理方法は、環境や組織の要件によって異なります。 Surface デバイスでは、ファームウェアはオペレーティングシステムにドライバーとして公開され、デバイスマネージャーに表示されます。 これにより、デバイスのファームウェアとドライバーは、一般法人向け Windows Update または Windows Update を使用して自動的に更新されます。 この簡素化されたアプローチは、新興企業や中小企業にとって実現可能な場合もありますが、大規模な組織では通常、更新プログラムを社内で配布する必要があります。 これには、ネットワーク全体での最終的な承認および配布前に、包括的な計画、アプリケーションの互換性テスト、および更新プログラムの検証を行う必要があります。

> [!NOTE]
> この記事は、テクニカルサポート担当者と IT プロフェッショナルを対象としています。 Surface デバイスにのみ適用されます。 Surface の更新プログラムまたはファームウェアをホームデバイスにインストールする方法については、「 [surface ファームウェアと Windows 10 を更新](https://support.microsoft.com/help/4023505)する」を参照してください。

エンタープライズグレードのソフトウェア配布ソリューションは進化し続けていますが、更新プログラムを一元管理するためのビジネスの根拠は変わりません。 Surface デバイスのセキュリティを維持し、最新のオペレーティングシステムと機能の改善によって更新された状態を維持します。 これは、安定した運用環境を維持し、ユーザーが生産性をブロックされないようにするために不可欠です。 この記事では、大規模な組織がこれらの目標を達成するための推奨ツールとプロセスの概要について説明します。

## 商用環境での一元的な更新管理

Microsoft には、ドライバーやファームウェアの更新プログラムなど、デバイスを管理するための合理化されたツールがあります。これは、 [Microsoft Endpoint Manager 管理センター](https://devicemanagement.microsoft.com/)という名前の単一の統合されたエクスペリエンスで、 [devicemanagement.microsoft.com](https://devicemanagement.microsoft.com/#home)からアクセスされます。

### Configuration Manager と Intune を使用して更新プログラムを管理する

Microsoft Endpoint Configuration Manager を使用すると、Configuration Manager クライアントを使用して、Surface ファームウェアとドライバー更新プログラムの同期と展開を行うことができます。 Microsoft Intune との統合により、管理対象、共同管理、パートナーが管理するすべてのデバイスを1か所で確認できます。 これは、大規模な組織が Surface の更新を管理するために推奨されるソリューションです。

詳細な手順については、次のリソースを参照してください。

- [構成マネージャーのドライバーの更新](https://docs.microsoft.com/surface/manage-surface-driver-updates-configuration-manager)
- [Configuration Manager を使用してアプリケーションを展開する](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [エンドポイント構成マネージャーのドキュメント](https://docs.microsoft.com/configmgr/)

### Microsoft 展開ツールキットを使用して更新プログラムを管理する

Microsoft 展開ツールキット (MDT) は、エンドポイント構成マネージャーに含まれています。 環境によっては、使用する必要があるオプションの展開ツールが含まれています。 これには、windows の評価と展開キット (Windows ADK)、Windows システムイメージマネージャー (Windows SIM)、展開イメージのサービスと管理 (DISM)、ユーザー状態移行ツール (USMT) が含まれます。 最新バージョンの MDT は、 [Microsoft 展開ツールキットのダウンロードページ](https://www.microsoft.com/download/details.aspx?id=54259)からダウンロードできます。

詳細な手順については、次のリソースを参照してください。

- [Microsoft 展開ツールキットのドキュメント](https://docs.microsoft.com/configmgr/mdt/)
- [Microsoft Deployment Toolkit による Windows 10 の展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)

Surface ドライバーとファームウェアの更新プログラムは、Windows Installer (* .msi) ファイルとしてパッケージ化されています。 これらの Windows インストーラーパッケージを展開するには、エンドポイント構成マネージャーまたは MDT を使用できます。 デバイスとオペレーティングシステムに適切な .msi ファイルを選択する方法については、次のセクションの「.msi ファイルのダウンロードに関するガイドライン」を参照してください。

エンドポイント構成マネージャーを使用して更新プログラムを展開する方法については、「 [Configuration manager を](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)使用してアプリケーションを展開する」を参照してください。 MDT を使用して更新プログラムを展開する方法については、「 [mdt を使用した Windows 10 イメージの展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)」を参照してください。

**WindowsPE および Surface ファームウェアとドライバー**

エンドポイント構成マネージャーと MDT では、展開プロセス中に Windows Preinstallation Environment (WindowsPE) が使用されます。 WindowsPE は、ネットワークアダプターや記憶域コントローラーなどの一部の基本的なドライバーのみをサポートしています。 WindowsPE の一部ではない Windows コンポーネントのドライバーは、エラーを発生する可能性があります。 最善の方法として、このようなエラーを回避するには、WindowsPE フェーズ中に必要なドライバーのみを使用するように展開プロセスを構成します。

### Endpoint Configuration Manager

エンドポイント構成マネージャーから開始すると、Configuration Manager クライアントを使用して、Microsoft Surface ファームウェアとドライバーの更新プログラムを同期して展開することができます。 詳細については、「KB 4098906、[構成マネージャーで Surface driver の更新プログラムを管理する方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)」を参照してください。

## サポートされるデバイス

Surface Pro 2 以降のデバイスでは、ダウンロード可能な .msi ファイルを使用できます。 Surface Pro 7 や Surface ノートブック3など、最新の Surface デバイスの .msi ファイルに関する情報は、リリース時にこのページから入手できます。

## DFCI でのファームウェアの管理

Intune にデバイスファームウェア構成インターフェイス (DFCI) プロファイルを構築することによって ([パブリックプレビュー](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)で利用できるようになりました)、Surface UEFI 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。 DFCI では、ゼロタッチプロビジョニング、BIOS パスワードの排除、セキュリティ設定の制御 (起動オプションや内蔵の周辺機器を含む)、今後の高度なセキュリティシナリオの基盤を構築しています。 詳細については、次の記事を参照してください。

- [Surface UEFI の設定の Intune 管理](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。

## 更新プログラムの展開プロセスのためのベストプラクティス

安定した環境を維持するには、最新バージョンの Windows 10 とのパリティを保持することを強くお勧めします。  ベストプラクティスの推奨事項については、「 [Windows 10 の更新プログラムの展開リングを作成する](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)」を参照してください。

## ダウンロード可能な Surface 更新パッケージ

Windows 10 の特定のバージョンには個別の .msi ファイルがあり、各ファイルには、Surface デバイスのために必要な累積ドライバーとファームウェア更新プログラムがすべて含まれています。 更新プログラムパッケージには、次のコンポーネントの一部またはすべてが含まれる場合があります。

- Wi-fi および LTE
- ビデオ
- ソリッドステートドライブ
- システムアグリゲーターモジュール (SAM)
- バッテリー
- キーボードコントローラー
- 埋め込みコントローラー (EC)
- 管理エンジン (ME)
- 統合された拡張ファームウェアインターフェイス (UEFI)

### .Msi ファイルのダウンロード

1. Microsoft ダウンロードセンターで、 [Surface のドライバーとファームウェアのダウンロード](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)を参照してください。
2. Windows のサーフェスモデルとバージョンと一致する .msi ファイル名を選びます。 .Msi ファイル名には、ドライバーとファームウェアをインストールするために必要な最小サポートされる Windows ビルド番号が含まれています。 たとえば、次の図を参照してください。 Windows 10 のビルド18362を持つ Surface Book 2 を更新するには、[SurfaceBook2_Win10_18362_19.101.13994.msi] を選び**ます。** Windows 10 のビルド16299を持つ Surface Book 2 の場合は、[ **SurfaceBook2_Win10_16299_1803509_3.msi**] を選びます。

    ![図 1.  サーフェスの更新プログラムのダウンロード](images/fig1-downloads-msi.png)

    *図 1.  サーフェスの更新プログラムのダウンロード*

### Surface の名前付け規則

2019年8月の .msi ファイルでは、次の名前付け規則が使用されています。

- *Product*_*windows release*_*windows ビルド番号*_*バージョン*_*番号 (通常はゼロ) の*バージョン番号。

**例**

- SurfacePro6_Win10_18362_19.073.44195_0.msi

このファイル名には、次の情報が記載されています。

- **製品:** SurfacePro6
- **Windows リリース:** Win10
- **ビルド:** 18362
- [**バージョン]:** 19.073.44195 –ファイルが作成された日付と時刻が、次のように表示されます。
  - **年:** 19 (2019)
  - **Month and week:** 073 (7 月3日)
  - **月の分:** 44195
- **バージョンのリビジョン:** 0 (このバージョンの最初のリリース)

### 以前の Surface の名前付け規則

従来の .msi ファイル (2019 年8月より前にビルドされたファイル) は、全体的な名前付けのすべての式に従いますが、別の方法でバージョン番号を派生させます。

**例**

- SurfacePro6_Win10_16299_1900307_0.msi

このファイル名には、次の情報が記載されています。

- **製品:** SurfacePro6
- **Windows リリース:** Win10
- **ビルド:** 16299
- **バージョン:** 1900307 –次のように、ファイルが作成された日付と、リリースシーケンスでの位置を示します。
  - **年:** 19 (2019)
  - **リリース数:** 003 (年の第3リリース)
  - **製品バージョン番号:** 07 (surface pro 6 は正式には、surface pro の7番目のバージョンです)
- **バージョンのリビジョン:** 0 (このバージョンの最初のリリース)

## 詳細情報

- [Surface 用のドライバーとファームウェアをダウンロードする](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)
- [Configuration Manager で Surface driver の更新プログラムを管理する方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [Configuration Manager を使用してアプリケーションを展開する](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [エンドポイント構成マネージャーのドキュメント](https://docs.microsoft.com/configmgr/)
- [Microsoft 展開ツールキットのドキュメント](https://docs.microsoft.com/configmgr/mdt/)
- [Microsoft Deployment Toolkit による Windows 10 の展開](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Microsoft 展開ツールキットを使用して Windows 10 を Surface デバイスに展開する](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)  
- [Surface UEFI の設定の Intune 管理](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理をアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)します。
- [Windows 10 更新プログラムの展開リングの構築](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)
