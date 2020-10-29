---
title: Windows 10 Team 2020 更新プログラムの新機能
description: Surface Hub オペレーティングシステムの最新の更新プログラム、Windows 10 Team 2020 更新プログラムの新機能を確認してください。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/27/2020
ms.localizationpriority: Medium
ms.openlocfilehash: accdc8519ad90b5137e2b8f340290d9a7214e696
ms.sourcegitcommit: b4cfb718274fd632661f9112e9fd086a2ad45640
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "11143632"
---
# Windows 10 Team 2020 更新プログラムの新機能

Windows 10 Team 2020 更新プログラムでは、Windows 10 の最新機能と共に、デバイスの展開と管理性が大幅に向上しています。

##  展開と管理性

- **クラウドデバイスアカウントの先進認証**。 Surface Hub は Exchange Web Services (EWS) ベースの認証をサポートし、Exchange に接続することで、ユーザーは基本的な認証を廃止することができます。 詳しくは、「 [Surface Hub での先進認証](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth)」をご覧ください。
- **20 以上の新しいモバイルデバイス管理 (MDM) ポリシーが追加されました**。      これらのポリシーによって、IT 管理者は、Microsoft ストアからのアプリの更新、インフラストラクチャ経由の Miracast などのワイヤレスプロジェクション、サービス品質や 802.1 x ワイヤード認証などのネットワーク設定、および新しいプライバシー/GDPR 関連設定など、複数のデバイス設定の制御が強化されます。

##  Azure Active Directory に参加したデバイス

- **AZURE AD に参加しているデバイス用のシングルサインオン (SSO)**。 ユーザーが Microsoft 365 の資格情報を使って "自分の会議とファイル" にサインインすると、ユーザーの資格情報がアプリからアプリにシームレスに流れるようになります。これには、ブラウザーでの Microsoft 365 エクスペリエンスが含まれます。
- **AZURE AD に参加しているデバイス用の条件付きアクセス (CA)**。       IT 管理者は、デバイスレベルのセキュリティポリシーを Azure AD に参加した Surface Hub に展開して、企業のセキュリティとコンプライアンスの要件に従って、組織のリソースへのアクセスを制御できます。
- **AZURE AD に参加しているデバイス用のグローバル管理者以外はサポート**されません。       ユーザーは、Surface Hub を管理するために、管理階層内でさらに細かい管理者のセットを選ぶことができます。 詳しくは、「[管理者グループの管理](https://docs.microsoft.com/surface-hub/admin-group-management-for-surface-hub)」をご覧ください。


## 追加機能


- **新しい Microsoft Edge のサポート**。 Microsoft Edge は、最適な互換性を保つために再構築されています。 詳細については、「 [Surface Hub に新しい Microsoft Edge をインストールして構成](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge)する」を参照してください。
- **Microsoft Teams は既定でインストールされ**ています。        Microsoft Teams は、既定の会議、通話、コラボレーションアプリとして、MDM 経由で、または直接 Surface Hub 上で設定アプリを使用して、変更または構成できる新しい Surface Hub デバイス上に存在します。 詳細については、「 [Microsoft Teams を展開](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub)する」を参照してください。
- **Microsoft Teams を使用した近接通信のサポート**。  近接通信を使用すると、ユーザーは、ノート pc またはスマートフォンを使用して、近くにある Surface Hub で Microsoft Teams のスケジュールを設定したり、進行中の会議を隣接する Surface Hub にシームレスに切り替えたりすることができます。 Windows 10 Team 2020 Update では、近接通信を構成するためのモバイルデバイス管理 (MDM) のサポートが追加され、この機能は、microsoft Store 経由で Microsoft Teams の更新としてリリースされます。
- **Microsoft Teams との調和した会議のサポート**。 Surface Hub と Microsoft Teams Room device、または2つの Surface Hub デバイスを持つスペースなどの会議室では、調整された会議で、Microsoft Teams の会議中に両方のデバイスを簡単に活用できます。 1回タップするだけで、ユーザーは1つのデバイスにビデオフィードを表示し、もう一方のデバイスにデジタルのホワイトボードまたはコンテンツを表示することで、どちらのデバイスからでも会議に参加できます。 Windows 10 Team 2020 更新プログラムは、調整された会議を構成するためのモバイルデバイス管理 (MDM) のサポートを追加します。その後、この機能は、microsoft Store 経由で Microsoft Teams の更新としてリリースされます。
- **FIDO2 セキュリティキーを使用した Passwordless サインイン**     FIDO2 セキュリティキーを使用すると、ユーザー名とパスワードを入力しなくても、ユーザーはすばやく簡単に Surface Hub にサインインすることができます。 この機能を単一の Sign-On (SSO) と組み合わせることで、会議中にファイル、アプリ、web サイトの迅速でシームレスな認証を行うことができます。 詳細については、「 [Surface Hub でのパスワードをあまりサインイン](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate)しないように構成する」を参照してください。
- **Microsoft Authenticator を使用したパスワードを超えたサインインの改善**。  Azure AD を使用している組織の場合、ユーザーは、ユーザー名とパスワードを入力しなくても、Microsoft Authenticator アプリを使用してサインインすることができます。 さらに、ユーザーは、ユーザープリンシパル名 (UPN) に加えて、Azure AD で優先メールエイリアスを使ってサインインすることもできます。 詳細については、「 [Microsoft Authenticator で Surface Hub にサインインする](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app)」を参照してください。
- **Surface Hub 2s でのデュアルペン手描き**入力。   ユーザーは、Surface hub 2 の2つのペンを使用して、Surface Hub の2台でのホワイトボードと共同作業を行うことができます。 デュアルペン手書き入力を有効にするために必要なファームウェア更新プログラムは、それ以降の更新プログラムでリリースされる予定です。

 
 
 
