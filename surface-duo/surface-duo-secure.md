---
title: Surface Duo のセキュリティの概要
description: この記事では、Surface Surface が Android OS と Microsoft によって設計された UEFI を介してモバイル デバイスでエンタープライズ レベルのセキュリティを提供する方法について説明します。
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 8/12/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 91eb893dbdc6dae93cf402a602b64a83309388e8
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326210"
---
# Surface Duo のセキュリティの概要

Surface Surface の保護は、デバイス、ID、およびデータのセキュリティを維持するために、深く統合されたハードウェア、ファームウェア、ソフトウェアを使用して、すべてのレイヤーに組み込されています。 Android 10 デバイスとして、Surface Surface は OS レベルと Google サービス レイヤーで Android のセキュリティ機能を利用します。 Android OS では、従来の OS セキュリティ制御を利用してユーザー データとシステム リソースを保護し、デバイスの整合性をマルウェアから保護し、アプリケーションを分離します。 さらに、Google は、Android OS のセキュリティと組み合わせると、Android ユーザーを継続的に保護するのに役立つ、OS の上にレイヤー化された多くのサービスを提供します。

- **カスタムの UEFI を設計しました。** Android デバイスの中でも Surface Over に固有の機能は、ファームウェア コンポーネントを完全に制御できる Microsoft のカスタム 設計 Unified Extensible Firmware Interface (UEFI) です。 Microsoft は、Enterprise レベルのセキュリティを Surface Surface に提供します。このセキュリティは、すべての行のファームウェア コードを作成またはレビューすることで、Microsoft がファームウェアの潜在的な脅威に直接迅速に対応し、サプライ チェーンのセキュリティ リスクを軽減することができます。
- **検証済みのブート。** サインイン時のハードウェア レベルから、検証済みブートでは、実行されたコードが信頼できるソースからのみ取得される必要があります。 ハードウェアで保護された信頼のルートからブートローダー、ブート パーティション、その他の検証済みパーティションへの完全な信頼チェーンを確立します。 Surface Duo が起動すると、各ステージは、実行を引き渡す前に、次のステージの整合性と信頼性を検証します。
- **アプリの分離。** アプリケーション サンドボックスは、Android アプリを分離して保護し、悪意のあるアプリによる個人情報へのアクセスを防止します。 必須の常時有効な暗号化とキーの処理は、デバイスが誤った手に入った場合でも、転送中および保存中のデータを保護するのに役立ちます。 暗号化は、コンテナーに暗号化キーを格納する多くのキーで保護され、デバイスからの抽出が困難になります。
- **Google Play Protect。** ソフトウェアレイヤーでは、Surface Surface は Google Play Protect 脅威検出を使用します。この検出では、Google Play からのパブリック アプリ、Microsoft によって更新されたシステム アプリ、およびキャリアによって更新されたシステム アプリ、サイドローディングされたアプリを含む、すべてのアプリケーションがスキャンされます。
- **Microsoft Defender ATP。** Windows 10 のエンタープライズ レベルのウイルス対策およびマルウェア保護ソフトウェアは、Intune から管理されている Android デバイスで利用できます。 詳細については、Android 用 [Microsoft Defender ATP に関するページを参照してください](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-android)。 


## モバイル デバイス管理のセキュリティ

Surface Surface のセキュリティは、Enterprise Mobility Management (EMM) ソリューションを使用して企業環境でセキュリティ保護されます。このソリューションは、組織とコンプライアンスの要件に合わせて調整できる一貫した保護ツール、テクノロジ、ベスト プラクティスのセットを提供します。 幅広い管理 API により、IT 部門はさまざまなシナリオでデータ漏洩を防止し、コンプライアンスを実施するためのツールを提供します。 マルチプロファイル サポートとデバイス管理オプションを使用すると、仕事用データと個人データを分離し、会社のデータのセキュリティを維持できます。

MDM セキュリティは、拡張された一連の構成テクノロジを基に構築され、ユーザーが企業の重要な知的財産を保護しながら、ユーザーの生産性を高めることができます。 これには、環境に応じて特定の目標を達成するために設計されたアプリ保護ポリシー、デバイス制限ポリシー、および関連するテクノロジが含まれます。企業がレストランの注文の提供、オフィス向け IT サービスの管理、機密性の高い国のセキュリティ情報の処理で構成されるかどうかなどです。 

たとえば、ユーザーに 6 桁の英数字のピンと 2 要素認証を入力する必要が生じ、デバイス認証を強化できます。  ユーザーが登録できるデバイスを制限して、ライセンスの制限に準拠し続けるか、"脱獄" 電話などのサポートされていないデバイスの種類へのアクセスを許可しないようにすることができます。
Intune とその他の EMM は、組織のニーズに応じてデバイスを柔軟に管理できます。

## アプリ保護ポリシー

アプリ保護ポリシー (APP) は、組織のデータが安全なままか、管理対象アプリに含まれるかを保証する規則です。 ポリシーには、ユーザーが "企業" データにアクセスまたは移動しようとするときに適用されるルールや、ユーザーがアプリ内にいる際に禁止または監視される一連のアクションを指定できます。 管理対象アプリとは、アプリ保護ポリシーが適用され、Intune で管理できるアプリです。

アプリ保護ポリシーを使用すると、アプリケーション内で組織のデータを管理および保護できます。 アプリなどの生産性アプリの多くは、Microsoft Office Intune MAM で管理できます。 一般利用できる [Microsoft Intune で保護されたアプリの公式](https://docs.microsoft.com/mem/intune/apps/apps-supported-intune-apps) リストをご覧ください。

## Surface Surface の管理に関するセキュリティに関する考慮事項

モバイル デバイス管理ソリューションで利用できるポリシー設定の数が増えているので、組織は特定のニーズに合わせて保護レベルを調整できます。 組織が Surface Surface のセキュリティ設定 (または他の Android デバイス) のセキュリティ設定に優先順位を付け支援するために、Intune では、Android [Enterprise](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework) のセキュリティ構成フレームワークをいくつかの異なる構成シナリオに編成し、作業プロファイルと完全に管理されたシナリオに関するガイダンスを提供しています。
 

| "セキュリティ" レベル                                                                                                       | 対象                                                                                                                                                                      | 要約                                                                                                                                                                                     | 設定情報                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 作業プロファイルの基本セキュリティ - レベル 1                                                                                | 仕事や学校のデータにアクセスできる個人のデバイス。                                                                                                                             | パスワード要件を導入し、作業データと個人データを分離し、Android デバイスの構成証明を検証します。                                                                               | [作業プロファイル レベル 1 の設定](https://microsoft.sharepoint.com/teams/EpsilonAdminGuide/Shared%20Documents/General/•%09https:/docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-basic-security) |
| 作業プロファイルの高セキュリティ - レベル 3<br>(フレームワークの規則により、これはレベル 1 より上の次のレベルです)。<br> ** | 一意にリスクが高いユーザーまたはグループが使用するデバイス。 たとえば、機密性の高いデータを扱うユーザーは、不正な情報が漏えいすると大損失が発生します。 | モバイル脅威防御または Microsoft Defender ATP を導入し、Android の最小バージョンを 8.0 に設定し、より強力なパスワード ポリシーを設定し、業務と個人の分離をさらに制限します。 | [作業プロファイル レベル 3 の設定](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-high-security)                                                                                         |
| 完全に管理された基本セキュリティ -レベル 1                                                                                | 企業デバイスの最小セキュリティ構成。仕事や学校のデータにアクセスするほとんどのモバイル ユーザーに適用されます。                                                          | パスワード要件を導入し、Android の最小バージョンを 8.0 に設定し、特定のデバイスの制限を定しています。                                                                          | [完全に管理されたレベル 1 の設定](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-basic-security)                                                                                     |
| 完全に管理された拡張セキュリティ レベル 2                                                                              | ユーザーが機密情報または機密情報にアクセスするデバイス。                                                                                                                | パスワード ポリシーを強化し、ユーザー/アカウント機能を無効にします。                                                                                                                   | [完全に管理されたレベル 2 の settngs](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-enhanced-security)                                                                                   |
| 完全に管理された高セキュリティ レベル 3                                                                                  | 一意にリスクが高いユーザーまたはグループが使用するデバイス。 たとえば、機密性の高いデータを扱うユーザーは、不正な情報が漏えいすると大損失が発生します。 | Android の最小バージョンを 10.0 に増やし、モバイル脅威防御または Microsoft Defender ATP を導入し、追加のデバイス制限を適用します。                                     | [完全に管理されたレベル 3 の設定](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-high-security)                                                                                      |
 
どのフレームワークの場合と同様に、対応するレベル内の設定は組織のニーズに基づいて調整する必要があります。セキュリティは、脅威環境、リスクリスク、および操作性への影響を評価する必要があります。
 
 
**詳細情報**


- [Android Enterprise セキュリティ構成フレームワーク](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework)
- [アプリ保護ポリシーの概要](https://docs.microsoft.com/mem/intune/apps/app-protection-policy)
- [Microsoft Intune での Android アプリ保護ポリシー設定](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android)
- [登録の制限を設定する](https://docs.microsoft.com/mem/intune/enrollment/enrollment-restrictions-set)
- [Android Enterprise Security ホワイト ペーパー](https://static.googleusercontent.com/media/www.android.com/en//static/2016/pdfs/enterprise/Android_Enterprise_Security_White_Paper_2019.pdf)
 