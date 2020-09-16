---
title: Windows Autopilot と Surface デバイス
ms.reviewer: ''
manager: laurawi
description: Surface デバイスの Windows 自動操縦展開オプションについては、こちらを参照してください。
keywords: 自動操縦、windows 10、サーフェス、展開
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
ms.openlocfilehash: d2a948d236ffa286192937cc5ca71099b6eeeafb
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016426"
---
# Windows Autopilot と Surface デバイス

Windows 自動操縦は、Windows 10 のクラウドベースの展開テクノロジです。 Windows 自動操縦を使用して、ゼロタッチプロセスでデバイスをリモートで展開して構成することができます。

これまで、IT プロフェッショナルは、後で、まったく正常にインストールされている OS がインストールされているデバイスに展開されるように、多くの時間を費やしています。 Windows 自動操縦では、Windows デバイスをセットアップして構成するための一連のテクノロジを使って、新しいゼロタッチの展開方法が導入されています。 これにより、IT 部門は、管理するインフラストラクチャをほとんど必要とせずに、また簡単かつ簡単に処理を行うことができます。 ユーザーの視点から見ると、いくつかの簡単な手順を実行して、生産的な状態にすることができます。 実際には、エンドユーザーからの唯一の操作として、ネットワークに接続し、資格情報を確認する必要があります。 その後のすべての機能が完全に自動化されます。

Windows 自動操縦機能を使用すると、次のことができます。

- Azure Active Directory (Azure AD) にデバイスを自動的に参加します。
- Microsoft Intune などの MDM サービスにデバイスを自動登録します (Azure AD Premium サブスクリプションが必要です)。
- 管理者アカウントの作成を制限する。 自動操縦は、Windows にログインする最初のユーザーを標準ユーザーとして入力する唯一の方法です。
- デバイスプロファイルに基づいて、デバイスを作成し、構成グループに自動的に割り当てます。
- 組織の要件を満たすために、OOBE (Box) のコンテンツとブランドをカスタマイズします。
- Intune で完全なデバイス構成を有効にします。
- デバイスをリモートでリセットまたは再起動します。

## 動作のしくみ

Windows 自動操縦装置-登録済みデバイスは、最初の起動時に、 *ハードウェアハッシュ*と呼ばれる一意のデバイス署名を介してインターネット経由で識別されます。 これらのユーザーは、Azure Active Directory (Azure AD) やモバイルデバイス管理などの先進の管理ソリューションを使用して、自動的に登録および構成されています。

Surface devices は、Windows 自動操縦が有効になっている Surface パートナーから購入した時点で登録できます。 これらのパートナーは、新しいデバイスを直接ユーザーに送ることができます。 デバイスは、最初にオンになったときに自動的に登録され、構成されます。 このプロセスでは、展開中のイメージの再作成が不要になります。これにより、デバイスの管理と配布に関する新しい機敏な方法を実装することができます。

## 最新の管理機能

自動操縦は、surface Pro 7、Surface ノート Pc 3、Surface Pro X など、Surface デバイスに推奨される展開オプションであり、自動操縦を通じて展開するために特別に設計されています。

 Surface デバイスの登録は、Microsoft クラウドソリューションプロバイダーの支援として行うことをお勧めします。 この手順により、Intune から直接、Surface 上の UEFI ファームウェア設定を管理できます。 これにより、デバイスを直接操作して証明書を管理する必要がなくなります。 詳細については、「 [Surface の UEFI 管理のための Intune の設定](surface-manage-dfci-guide.md) 」をご覧ください。

## Windows のバージョンに関する考慮事項

Windows 自動操縦を介した Surface デバイスの広範な展開 (購入時に Surface パートナーによる登録を含む) には、Windows 10 バージョン 1709 (秋の更新プログラム) 以降が必要です。

これらの Windows のバージョンでは、Windows 自動操縦用のデバイスを一意に識別する4000バイト (4k) ハッシュ値がサポートされています。これは、展開時の展開に必要です。 Surface Pro 7、Surface Pro X、Surface のノート Pc 3 などのすべての新しい Surface デバイスは、Windows 10 バージョン1903以降で出荷されています。

## 修復または交換の必要性に応じた Surface デバイスでの Exchange の操作性

Microsoft は、自動操縦のための各サーフェスを自動的にチェックし、お客様のテナントからデバイスを登録解除します。  Microsoft は、交換されたデバイスが、お客様にリリースされると、Windows 自動操縦に登録されることを保証します。 このサービスは、Microsoft とのすべてのデバイス交換サービス注文で利用できます。

> [!NOTE]
> 顧客がパートナーを使ってデバイスを返品する場合、パートナーは Windows 自動操縦の登録解除とデバイスの登録など、exchange プロセスの管理を担当します。

## Microsoft サポートの登録

顧客および Microsoft クラウドソリューションプロバイダー (Csp) には、Microsoft サポートに要求を送信することによって Surface デバイスを登録するオプションがあります。 詳細については、「 [Windows 自動操縦の表面登録サポート](surface-autopilot-registration-support.md)」を参照してください。

## Windows 自動操縦に対応した Surface パートナー

[Surface パートナーの選択] では、購入時に Windows 自動操縦に Surface デバイスを登録できます。 また、登録されたデバイスを直接ユーザーに送ることもできます。 デバイスは、Windows 自動操縦機能、Azure AD、モバイルデバイス管理を使用して、ゼロタッチプロセスで完全に構成できます。

Windows 自動操縦に対応した Surface パートナーには次のものがあります。

| US パートナー | グローバルパートナー | US 販売業者 |
|--------------|---------------|-------------------|
| * [CDW](https://www.cdw.com/) | * [また](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp) | * [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)  |
| * [関連](https://www.connection.com/brand/microsoft/microsoft-surface)   | * [ATEA](https://www.atea.com/) | * [テクニカルデータ](https://www.techdata.com/)  |
| * [知る](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)  | * [/Htle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot) | * [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)   |
| * [SHI](https://www.shi.com/Surface) | * [Cancom](https://www.cancom.de/) |    |
| * [LDI Connect](https://www.myldi.com/managed-it/)  | * [Computacenter](https://www.computacenter.com/uk) |    |
| * [F1](https://www.functiononeit.com/#empower)  |   |  |
| * [保護された信頼](https://go.microsoft.com/fwlink/p/?LinkID=2129005) | | | 

## 詳細情報

Windows 自動操縦の詳細については、以下を参照してください。
- [Windows Autopilot の概要](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)
- [Windows Autopilot の要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements)
- [Windows 自動操縦の表面登録サポート](surface-autopilot-registration-support.md)