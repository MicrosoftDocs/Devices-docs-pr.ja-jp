---
title: Windows Autopilot と Surface デバイス
ms.reviewer: ''
manager: laurawi
description: Surface デバイスの Windows Autopilot 展開オプションについて説明します。
keywords: autopilot, windows 10, surface, deployment
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 9/14/2020
ms.openlocfilehash: 31f11db8c3ab12d1af754267022d9060d3a8c026
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271103"
---
# Windows Autopilot と Surface デバイス

Windows Autopilot は、Windows 10 のクラウドベースの展開テクノロジです。 Windows Autopilot を使って、ゼロタッチ プロセスでデバイスをリモートで展開および構成できます。

従来、IT のプロは、イメージの構築とカスタマイズに多くの時間を費やしていました。イメージは、既に完全に優れた OS が既にインストールされているデバイスに後で展開されます。 Windows Autopilot では、Windows デバイスをセットアップおよび構成するためのテクノロジのコレクションを使用して、新しいゼロタッチ展開アプローチが導入されています。 これにより、IT 部門は、管理するインフラストラクチャをほとんどまたは全く使用し、簡単で簡単なプロセスでイメージを構成/カスタマイズできます。 ユーザーの観点からは、Surface を生産性の高い状態にするための簡単な手順がいくつか必要です。 実際、エンド ユーザーが必要とする唯一の操作は、ネットワークに接続し、資格情報を確認する操作です。 その後のすべてが完全に自動化されます。

Windows Autopilot を使用すると、次のタスクを実行できます。

- デバイスを Azure Active Directory (Azure AD) に自動的に参加AD。
- Microsoft Intune などの MDM サービスにデバイスを自動登録します (Azure AD Premium サブスクリプションが必要)。
- 管理者アカウントの作成を制限する。 Autopilot は、Windows にログインした最初のユーザーが標準ユーザーとして入力する唯一の方法です。
- デバイス プロファイルに基づいて、デバイスを作成し、構成グループに自動割り当てします。
- 組織の要件に合わせて OOBE (Out of Box Experience) コンテンツとブランド化をカスタマイズします。
- Intune でデバイスの完全な構成を有効にします。
- デバイスをリモートでリセットまたは再起動します。

##  <a name="how-it-works"></a>動作のしくみ

Windows Autopilot に登録されたデバイスは、最初の起動時に、ハードウェア ハッシュと呼ばれる一意のデバイス署名によってインターネット経由で *識別されます*。 Azure Active Directory (Azure AD) やモバイル デバイス管理などの最新の管理ソリューションを使用して、自動的に登録および構成されます。

購入時に、Windows Autopilot が有効になっている Surface パートナーから Surface デバイスを登録できます。 これらのパートナーは、ユーザーに新しいデバイスを直接出荷できます。 デバイスは、最初にオンになったときに自動的に登録され、構成されます。 このプロセスでは、展開時の再インストールが不要になります。これにより、デバイス管理と配布の新しいアジャイル メソッドを実装できます。

##  <a name="modern-management"></a>最新の管理機能

Autopilot は、Surface Pro 7+、Surface Laptop 3、Surface Pro 7、Surface Pro X など、特に Autopilot による展開用に設計された Surface デバイスに推奨される展開オプションです。

 Microsoft クラウド ソリューション プロバイダーの支援を受け、Surface デバイスを登録するのをお手伝いします。 この手順では、Intune から直接 Surface の UEFI ファームウェア設定を管理できます。 証明書を管理するためにデバイスに物理的にタッチする必要が排除されます。 詳 [しくは、Surface UEFI 設定の Intune 管理](surface-manage-dfci-guide.md) に関するページをご覧ください。

##  <a name="windows-version-considerations"></a>Windows のバージョンに関する考慮事項

購入時の Surface パートナーによる登録を含め、Windows Autopilot による Surface デバイスの広範な展開には、Windows 10 Version 1709 (Fall Creators Update) 以降が必要です。

これらの Windows バージョンでは、大規模な展開に必要な Windows Autopilot のデバイスを一意に識別する 4,000 バイト (4k) ハッシュ値がサポートされています。 Surface Pro 7 以降、Surface Pro X、Surface Laptop 3 を含むすべての新しい Surface デバイスは、Windows 10 Version 1903 以降に搭載されています。

##  <a name="exchange-experience-on-surface-devices-in-need-of-repair-or-replacement"></a>修復または交換が必要な Surface デバイスでの Exchange エクスペリエンス

Microsoft は、すべての Surface で Autopilot 登録を自動的にチェックし、お客様のテナントからデバイスの登録を解除します。  Microsoft では、代替デバイスが顧客に出荷された後、代替デバイスが Windows Autopilot に登録されます。 このサービスは、Microsoft と直接のすべてのデバイス交換サービス注文で利用できます。

> [!NOTE]
> お客様がパートナーを使用してデバイスを返却する場合、パートナーは Windows Autopilot へのデバイスの登録解除や登録などの交換プロセスの管理を担当します。

##  <a name="microsoft-support-registration"></a>Microsoft サポートの登録

お客様と Microsoft クラウド ソリューション プロバイダー (CSP) には、Microsoft サポートに要求を送信して Surface デバイスを登録するオプションがあります。 詳しくは [、Windows Autopilot の Surface 登録サポートに関するページをご覧ください](surface-autopilot-registration-support.md)。

##  <a name="surface-partners-enabled-for-windows-autopilot"></a>Windows Autopilot が有効になっている Surface パートナー

Surface パートナーは、購入時に Surface デバイスを Windows Autopilot に登録できます。 また、登録済みデバイスをユーザーに直接出荷することもできます。 デバイスは、Windows Autopilot、Azure AD、およびモバイル デバイス管理を使用して、ゼロタッチ プロセスを通じて完全に構成できます。

Windows Autopilot が有効になっている Surface パートナーには、次のものが含まれます。

| 米国パートナー | グローバル パートナー | 米国のディストリビューター |
|--------------|---------------|-------------------|
| * [CDW](https://www.cdw.com/) | * [また](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp) | * [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)  |
| * [接続](https://www.connection.com/brand/microsoft/microsoft-surface)   | * [ATEA](https://www.atea.com/) | * [Techdata](https://www.techdata.com/)  |
| * [Insight](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)  | * [ベクトレ](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot) | * [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)   |
| * [数日](https://www.shi.com/Surface) | * [Cancom](https://www.cancom.de/) |    |
| * [LDI Connect](https://www.myldi.com/managed-it/)  | * [Computacenter](https://www.computacenter.com/uk) |    |
| * [F1](https://www.functiononeit.com/#empower)  |   |  |
| * [保護された信頼](https://go.microsoft.com/fwlink/p/?LinkID=2129005) | | | 

##  <a name="learn-more"></a>詳細情報

Windows Autopilot の詳細については、以下を参照してください。
- [Windows Autopilot の概要](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)
- [Windows Autopilot の要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements)
- [Windows Autopilot の Surface 登録サポート](surface-autopilot-registration-support.md)