---
title: Surface Pro X の展開、管理、メンテナンス
description: この記事では、Surface Pro X の展開、管理、およびメンテナンスに関する重要な考慮事項の概要を示します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: high
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/09/2020
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 202818488f19c82ba9d08cfcbfcd091e3e8b7bf6
ms.sourcegitcommit: 7d5b0a7948eb540d6849a0e2c70a1058584cc5f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "11105842"
---
# Surface Pro X の展開、管理、メンテナンス

## はじめに

Surface Pro X は、クラスで最も強力なプロセッサである Microsoft SQ1 および Microsoft SQ1 ARM チップセットを組み込むことにより新境地を開拓し、商用環境での高パフォーマンス要件を処理できるように構築されています。

Surface Pro X では 3GHz CPU と 2.1 テラフロップ GPU を搭載し、完全な Windows エクスペリエンスを提供しています。 15 時間のバッテリー寿命を内蔵した Gigabit LTE と、タッチ、ペン、タブレット、ラップトップの多様性により、金融、法務、医療の分野のモバイル ファーストライン ワーカーおよびプロフェッショナルをはじめ、長いバッテリ寿命と継続的な接続性を必要とするあらゆる業務のユーザーに最適に機能します。

Surface Pro X は、最新のクラウドベース環境専用に設計されており、Microsoft 365、Intune、および Windows Autopilot と組み合わせると最適に機能します。 この記事では、Surface Pro X の概要を示し、展開、管理、およびメンテナンスに関する主な考慮事項について説明します。

## Surface Pro X の展開

最適なエクスペリエンスを得るには、Windows Autopilot で Surface Pro X を展開します。このとき、補助ツールとして Microsoft クラウド ソリューション プロバイダーを使用するか、Autopilot 展開プロファイルおよび関連機能によるセルフプロビジョニングを行います。 詳しくは、以下をご覧ください。

- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md)
- [Windows Autopilot の概要](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)

Autopilot による展開には、いくつかの利点があります。ゼロタッチ展開用に合理化された、工場でプロビジョニング済みのオペレーティング システムを使用して、Office Pro Plus のプレインストールを含めることができます。

既に最新の管理、セキュリティ、および生産性ソリューションを使用している組織は、Surface Pro X 独自のパフォーマンス機能を活用できます。最新のビジネス アプリ、Microsoft Store (UWP) アプリ、またはリモート デスクトップ ソリューションを使用しているお客様も有利です。

## イメージ ベースの展開に関する考慮事項

現在、Microsoft Deployment Toolkit (MDT) および Microsoft Endpoint Configuration Manager (旧称 System Center Configuration Manager) では、Surface Pro X でのオペレーティング システムの展開がサポートされていません。 イメージ ベースの展開をご利用のお客様は、最新の展開ソリューションに移行する適切な時期を引き続き評価しつつ、Surface Pro 7 の使用をご検討ください。 

## Surface Pro X デバイスの管理

### Intune

Intune は、Microsoft Enterprise Mobility + Security のコンポーネントです。これを Azure Active Directory と統合することで、ID およびアクセスの制御を行い、登録済みの Surface Pro X デバイスをきめ細かく管理できます。 Intune モバイル デバイス管理 (MDM) ポリシーには、Windows グループ ポリシーなどの従来のオンプレミス ツールと比較して、多くの利点があります。 これには、デバイスのログイン時間の短縮や、合理的なポリシー カタログによる、クラウドからの総合的なデバイス管理が含まれます。 たとえば、eSIM プロファイルを使用して LTE を管理し、データ通信プランを設定して、アクティブ化コードを複数のデバイスに展開することもできます。<br> 

Intune の使用方法の詳細については、[Intune ドキュメント](https://docs.microsoft.com/intune/)をご覧ください。

### 共同管理

Autopilot で展開すると、Surface Pro X デバイスを Azure ADまたはActive Directory (Hybrid Azure AD Join) に参加させて、Intune でデバイスを管理することも、Endpoint Configuration Manager でデバイスを共同管理することもできます (32 ビットの x86 ConfigMgr クライアントがインストールされます)。

### サード パーティの MDM ソリューション

Surface Pro X デバイスの管理に、サード パーティ製 MDM ツールを使用できる場合があります。 詳しくは、MDM プロバイダーにお問い合わせください。

### ウイルス対策ソフトウェア

Windows Defender は、Windows 10 デバイスの有効なサポート期間中、ARM ベースの PC での Windows 10 の保護に役立ちます。 

サード パーティ製ウイルス対策ソフトウェアには、ARM ベースのプロセッサで動作する Windows 10 PC にインストールできないものもあります。 サードパーティ製のウイルス対策ソフトウェア プロバイダーとのコラボレーションは、ARM ベースの PC での AV アプリの準備用に継続されています。 アプリが利用可能になる時期については、各ウイルス対策ソフトウェア プロバイダーにお問い合わせください。

## Surface Pro X のメンテナンス

Surface Pro X は Windows 10 バージョン 2004 に付属しており、Windows 10 バージョン 1903 以降をサポートしています。 ARM ベースのデバイスとして、最新のドライバーとファームウェアを維持するための特定の要件があります。 

Surface Pro X は、ホーム ユーザーと小規模ビジネス ユーザーの両方を対象とし、ドライバーとファームウェアを最新の状態に保つプロセスを Windows Update で簡略化できるように設計されています。 自動で更新プログラムを受け取るには、既定の設定を使用します。  設定を確認するには、次の操作を実行します。

1. **[スタート]** > **[設定] > [更新とセキュリティ] > [Windows Update]** > **[詳細オプション]** を開きます。
2. **[更新プログラムのインストール方法を選んでください]** で、**[自動 (推奨)]** を選択します。

### 商用利用のお客様向けの推奨事項

- 最新のドライバとファームウェアを維持するには、Windows Update または Windows Update for Business を使用します。 詳しくは、「[Windows Update for Business を使った更新プログラムの展開](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb)」をご覧ください。
- Surface デバイスでの更新プログラムの展開と管理の詳細については、「[Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する](manage-surface-driver-and-firmware-updates.md)」をご覧ください。
- Windows Server Update Services (WSUS) では、ドライバーとファームウェアを Surface Pro X に提供する機能がサポートされていません。

## Surface Pro X でのアプリの実行

一部の例外を除き、ARM ベースの Windows 10 PC では、ほとんどのアプリを実行できます。

### サポートされているアプリ

- Surface Pro X では、ほとんどの x86 Win32 アプリを実行できます。
- ネイティブの ARM64 アプリと Microsoft Store UWP アプリは、バッテリの寿命を最適化しながら、ARM ベースのプロセッサのネイティブ速度をフル活用して、優れたユーザー エクスペリエンスを提供します。
- ARM ベースのプロセッサで動作する Windows 10 PC 用に設計されたドライバーを使用するアプリ。

> [!NOTE]
> 64 ビット エミュレーションが Windows Insider プログラムを介してプレビューで間もなく登場するため、Surface Pro X で 64 ビット (x64) アプリを実行できるようになります。

### FastTrack App Assure 

App Assure プログラムは、ARM 版 Windows 10 を対象とする LOB、ISV、および Microsoft のファーストパーティ アプリの商用のお客様が利用できます。 ARM 版 Windows 10 を使用してアプリの互換性の問題が発生した場合、Microsoft は、追加費用なしで、アプリの修正をトラブルシューティングおよび支援するための開発者向けリソースを提供します。 詳細については、aka.ms/AppAssure にアクセスしてください。


Surface Pro X でのアプリの実行について詳しくは、以下をご覧ください。

- [Windows 10 ARM ベースの PC に関する FAQ](https://support.microsoft.com/help/4521606)
- [ARM 版 Windows 10 のドキュメント](https://docs.microsoft.com/windows/arm)

## 仮想デスクトップ (VDI)

Windows Virtual Desktop を使用すると、任意の場所から任意のコンピューティング デバイスまたはプラットフォーム上の Windows デスクトップ、アプリケーション、およびデータにアクセスできます。 詳しくは、[Windows Virtual Desktop のサイト](https://aka.ms/wvd)をご覧ください。 

## Surface Pro X で使用できるブラウザー

Surface Pro X では、一般的な各種のブラウザーを実行できます。

- また、Surface Pro X では、付属の Edge、Firefox、Chrome、Internet Explorer をすべて使用できます。
- Chromium に基づく Firefox と Microsoft Edge はネイティブで動作するため、ARM ベースのプロセッサで動作する Windows 10 PC で、高いパフォーマンスを発揮します。

## Microsoft Office のインストールと使用

- ARM ベースのプロセッサで動作する Windows 10 PC で最高のエクスペリエンスを実現する Office 365 をご利用ください。
- Office 365 の"クイック実行"により、ARM ベースのプロセッサで動作する Windows 10 PC での実行用に最適化された Outlook、Word、Excel、および PowerPoint がインストールされます。
- Microsoft Teams も、Surface Pro X で快適にご利用いただけます。
- Office 2019 など、Office の "永続バージョン" については、32 ビット バージョンをインストールしてください。

## VPN

ARM ベースのプロセッサで動作する Windows 10 PC が特定のサード パーティ VPN でサポートされているかどうかを確認するには、VPN プロバイダーにお問い合わせください。

## 機能の概要

次の表は、ARM 版 Windows 10 を搭載した Surface Pro X で選択された主要機能の可用性を示しています。


**展開**

| 機能                                                           | Y/N | 備考                                                                                                                             |
| ----------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------- |
| Windows Autopilot                                                 | あり |                                                                                                                                   |
| ネットワーク ブート (PXE) のサポート                                    | なし  |                                                                                                                                   |
| Windows 構成デザイナー                                    | なし  | Surface Pro X では推奨されていません。                                                                                                |
| WinPE                                                             | あり | Surface Pro X では推奨されていません。Microsoft では、Surface Pro X で WinPE をサポートするために必要な .ISO とドライバーが提供されていません。 |
| Endpoint Configuration Manager: オペレーティング システムの展開 (OSD) | なし  | Surface Pro X ではサポートされていません。                                                                                                   |
| MDT                                                               | なし  | Surface Pro X ではサポートされていません。                                                                                                   |

 
 
 **管理**
 

| 機能                                       | Y/N     | 備考                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| Intune                                        | あり     | LTE は eSIM プロファイルで管理します。                                                        |
| Windows Autopilot                             | あり     |                                                                                       |
| Azure AD (共同管理)                      | あり     | Azure AD または Active Directory (Hybrid Azure AD Join) に Surface Pro X を参加させます。 |
| Endpoint Configuration Manager                | あり     |                                                                                       |
| AC 復元時の電源オン                      | あり     |                                                                                       |
| ビジネス向け Surface 診断ツールキット (SDT) | あり     |                                                                                       |
| Surface Asset Tag ツール                        | あり     |                                                                                       |
| Surface Enterprise Management Mode (SEMM)     | 一部 | Surface Pro X のハードウェアをファームウェア レベルで無効にするオプションはありません。                 |
| Surface UEFI コンフィギュレータ                     | なし      | Surface Pro X のハードウェアを ファームウェア レベルで無効にするオプションはありません。                |
| Surface UEFI マネージャー                          | 一部 | Surface Pro X のハードウェアをファームウェア レベルで無効にするオプションはありません。                 |

 

**セキュリティ**
 

 機能                                       | Y/N     | 備考                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| BitLocker                                     | あり     |                                                       |
| Windows Defender                              | あり     |                                                                                       |
| サード パーティ製ウィルス対策のサポート             | 「備考」を参照| サード パーティ製ウイルス対策ソフトウェアには、ARM ベースのプロセッサで動作する Windows 10 PC にインストールできないものもあります。 サードパーティ製のウイルス対策ソフトウェア プロバイダーとのコラボレーションは、ARM ベースの PC での AV アプリの準備用に継続されています。 アプリが利用可能になる時期については、各ウイルス対策ソフトウェア プロバイダーにお問い合わせください。 |
| セキュア ブート               | あり     |                                                                                       |
| Windows 情報保護                      | あり     |                                                                                       |
| Surface Data Eraser (SDE)     | あり     |                                                                                       |




## FAQ

### MDT または Endpoint Configuration Manager を使用して Surface Pro X を展開できますか?

現在、Microsoft Deployment Toolkit (MDT) および Microsoft Endpoint Configuration Manager では、Surface Pro X でのオペレーティング システムの展開がサポートされていません。イメージ ベースの展開をご利用のお客様は、クラウドへの移行に適したタイミングを引き続き評価しつつ、Surface Pro 7 の使用をご検討ください。

### Surface Pro X を展開する方法は?

Surface Pro X は Windows Autopilot を使用して展開できます。

### BMR は利用できますか?

はい、「[Surface の回復イメージのダウンロード](https://support.microsoft.com/surfacerecoveryimage)」を参照してください。

### Surface Pro X を管理するためには Intune が必要ですか?

Intune をお勧めしますが、必須ではありません。 Autopilot で展開すると、Surface Pro X デバイスを Azure ADまたはActive Directory (Hybrid Azure AD Join) に参加させて、Intune でデバイスを管理することも、Endpoint Configuration Manager でデバイスを共同管理することもできます (32 ビットの x86 ConfigMgr クライアントがインストールされます)。
