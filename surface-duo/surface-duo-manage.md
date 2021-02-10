---
title: Surface Duo の管理の概要
description: この記事では、商用環境で Surface Surface を管理するためのオプションについて説明します。
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/23/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 19ef3f5d20b22997aa339a462a34b84da27fb922
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326213"
---
# Surface Duo の管理の概要

商用顧客は、従業員所有または会社所有のデバイスの管理に関して、クラウドベースのデバイス管理機能の一貫性のあるセットを提供する、さまざまなエンタープライズ モビリティ管理 (EMM) ソリューションを使用して Surface Surface を管理できます。

統合コンソール (Microsoft Endpoint Manager) と Microsoft Intune のような拡張可能なコンポーネントを使用する [Microsoft EMM](https://androidenterprisepartners.withgoogle.com/provider/#!/75) を介して、Intune を管理できます。 または、Google の Android エコシステムで任意の EMM プロバイダーを使用できます。 場合によっては、サードパーティの EMM ソリューションは、環境に応じて役立つ可能性がある特定のシナリオに対応するために追加のサポートを提供します。

 EMM ソリューションを比較するには [、Android Enterprise Solutions Directory を参照してください](https://androidenterprisepartners.withgoogle.com/emm/)。
Intune を使用したエンドポイント マネージャーでは、最新のモバイル デバイス管理ポリシーと、モバイル デバイス管理ポリシーなどの以前のテクノロジを使用して、Exchange ActiveSync。 モバイル デバイスの管理に Exchange ActiveSync設定を既に使用している場合は、電子メール デバイス構成プロファイルを使用して Intune を使用して、それらの設定を Intune のデバイスに適用できます。  詳細については、「Intune を使用 [してデバイスにメール設定を追加する」を参照してください](https://docs.microsoft.com/mem/intune/configuration/email-settings-configure)。

Intune でデバイスを管理する主な手段であるプロファイルは、組織のニーズに合わせてカスタマイズできる既定の設定を提供します。 

## 個人所有の Surface Surface のデバイスを管理する
| ソリューション                                          | 機能                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 詳細情報                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| デバイス登録なしのアプリ保護ポリシー | アプリケーション内で組織のデータを管理および保護できます。<br>デバイスの登録を必要としない軽量な管理ソリューションであるアプリ保護ポリシーを展開します。<br>Microsoft Office や Adobe Adobe、Service Now、Zoom などのサード パーティ製アプリを含むアプリ保護ポリシーを使用して、増え続けるアプリを管理できます。 完全な一覧については [、Microsoft Intune で保護されたアプリを参照してください](https://docs.microsoft.com/mem/intune/apps/apps-supported-intune-apps)。 | - [アプリ保護ポリシーの概要](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android)<br>- [Microsoft Intune の Android アプリ保護ポリシー設定](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android)。<br>- [Intune アプリ ラッピング ツールを使用して、アプリ保護ポリシー用に Android アプリを準備します](https://docs.microsoft.com/mem/intune/developer/app-wrapper-prepare-android)。 |
| Android Enterprise の作業プロファイル                   | BYOD 展開を対象として、仕事用プロファイルは、仕事用アプリとデータ用の別の領域を、仕事用アプリとデータ用に別の領域を提供します。ユーザーが個人のアプリやデータにデバイスを使用する操作を制限することなく、組織はデータ、アプリ、およびセキュリティ ポリシーを完全に制御できます。                                                                                                                                                                                                                                                  | - [Surface Surface の Android Enterprise Work Profile を構成します](surface-duo-config-work-profile.md)。                                                                                                                                                                                                                                                                                                               |


## 企業所有の Surface Surface のデバイスを管理する

| ソリューション                                  | 説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 詳細情報                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 会社所有のデバイスと仕事用プロファイル | 企業が所有する、仕事用に提供したシングル ユーザー デバイスで個人使用を有効にする組織を対象にしています。 これは、組織が仕事用プロファイルを使用して管理するよりも細かく制御するように設計されています。ただし、完全なデバイス管理または専用のデバイス管理を使用してデバイスを完全にロックダウンする必要はしません。<br>Android OS によって分離された仕事用および個人用プロファイルアプリのデータが、管理者により多くのデバイス レベルの制御を提供することで、Android Enterprise の仕事用プロファイルとは異なります。<br>IT 管理者は、仕事用プロファイルの作業アカウント、アプリケーション、およびデータを表示、制御、および構成できます。一方、エンド ユーザーは、管理者が個人プロファイル内のデータとアプリケーションを表示することはできません。 | - [Intune、仕事用プロファイルを含む Android Enterprise 企業所有デバイスのパブリック プレビューを発表](https://techcommunity.microsoft.com/t5/intune-customer-success/intune-announcing-public-preview-for-android-enterprise/ba-p/1524325)                                                                    |
| Android Enterprise Fully Managed          | 1 人のユーザーに関連付けられた会社所有のデバイスに対して包括的なデバイスおよびアプリ管理機能を提供し、個人使用ではなく、仕事専用に利用できます。<br> <br>完全なデバイス管理により、IT はデバイス のデータとセキュリティを完全に制御できるだけでなく、Android の一部のアプリ管理機能にアクセスできます。 次に、例を示します。<br><br>- デバイスでパスワードの最小要件を設定できます<br>- デバイスをリモートでワイプしてロックする<br>- アプリのアクセス許可要求への既定の応答を設定します。<br>- Microsoft 起動ツール を使用してエンド ユーザー エクスペリエンスをカスタマイズする<br><br>また、リモートでアプリをインストールおよび削除する機能など、デバイス上のアプリを完全に制御することもできます。                                 | - [Android Enterprise の完全に管理されたデバイスの Intune 登録を設定します](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-enroll)。 |
| 専用デバイス管理               | このエンタープライズ展開シナリオは、ロジスティックス、交通、工場のフロアなど、特定の使用事例に展開されたデバイスを対象とします。 使用を 1 つまたは 2 つのアプリに制限し、ユーザーによる設定の変更を禁止する必要があるロックダウン エクスペリエンスに使用します。                                                                                                                                                                                                                                                                                                                                                                                                                                                           | - [Android Enterprise 専用デバイスの Intune 登録をセットアップする](https://docs.microsoft.com/mem/intune/enrollment/android-kiosk-enroll)                                                                                                                                                               |

 
## 詳細情報
- [Ignite Session: Deploy, Manage, and Enable Productivity with Surface Duo in the Enterprise](https://youtu.be/DOsBMNFmdfw)
- [Microsoft Intune でデバイスを管理する](https://docs.microsoft.com/mem/intune/remote-actions/device-management)
- [Intune 展開の計画、設計、実装のガイド](https://docs.microsoft.com/mem/intune/fundamentals/planning-guide)
- [Intune で Android デバイスを登録する](https://docs.microsoft.com/mem/intune/enrollment/android-enroll)
