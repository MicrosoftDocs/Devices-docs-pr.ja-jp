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
ms.openlocfilehash: afc583ddf2d3aba9f487a3238e2b64d6e5876ada
ms.sourcegitcommit: 19d2a78242777590bd09af3ac6552c07b032e0a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "11142945"
---
# Windows 10 Team 2020 更新プログラムの新機能

Windows 10 Team 2020 更新プログラムでは、Windows 10 の最新機能と共に、デバイスの展開と管理性が大幅に向上しています。

##  展開と管理性

- クラウドデバイスアカウントの先進認証: Surface Hub は exchange Web Services (EWS) ベースの認証をサポートしており、Exchange に接続することで、ユーザーは基本的な認証を廃止することができます。 詳しくは、「 [Surface Hub での先進認証](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth)」をご覧ください。
- 20を超える新規および更新されたモバイルデバイス管理 (MDM) ポリシー: これらのポリシーは、Microsoft Store からのアプリの更新、インフラストラクチャ経由の Miracast、802.1 x ワイヤード認証などのネットワーク設定、および新しいプライバシー/GDPR 関連の設定など、複数のデバイス設定の管理を強化します。

##  Azure Active Directory に参加したデバイス

- Azure AD に参加しているデバイス用のシングルサインオン (SSO)。 ユーザーが Microsoft 365 の資格情報を使って "自分の会議とファイル" にサインインすると、ユーザーの資格情報がアプリからアプリにシームレスに流れるようになります。これには、ブラウザーでの Microsoft 365 エクスペリエンスが含まれます。
- Azure AD に参加しているデバイス用の条件付きアクセス (CA)。        IT 管理者は、デバイスレベルのセキュリティポリシーを Azure AD に参加した Surface Hub に展開して、企業のセキュリティとコンプライアンスの要件に従って、組織のリソースへのアクセスを制御できます。
- Azure AD に参加しているデバイス用のグローバル管理者以外はサポートされません。        ユーザーは、Surface Hub を管理するために、管理階層内でさらに細かい管理者のセットを選ぶことができます。 詳しくは、「[管理者グループの管理](https://docs.microsoft.com/surface-hub/admin-group-management-for-surface-hub)」をご覧ください。


## 追加機能


- 新しい Microsoft Edge のサポート。 Microsoft Edge は、最適な互換性を保つために再構築されています。 詳細については、「 [Surface Hub に新しい Microsoft Edge をインストールして構成](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge)する」を参照してください。
- Microsoft Teams を展開する office の機能が向上しました。新しい Surface Hub デバイスには、既定の会議、通話、コラボレーションアプリとして Microsoft Teams が含まれています。これは、設定アプリを使って MDM または直接 Surface Hub で変更または構成することができます。 詳細については、「 [Microsoft Teams を展開](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub)する」を参照してください。
- Microsoft Teams の近接通信を使用した近接結合のサポートにより、ユーザーはノート pc またはスマートフォンを使用して、近くの Surface Hub でスケジュールされている Microsoft Teams の通話を実行したり、進行中の会議を隣接する Surface Hub にシームレスに切り替えたりすることができます。 Windows 10 Team 2020 Update では、近接通信を構成するためのモバイルデバイス管理 (MDM) のサポートが追加され、この機能は、microsoft Store 経由で Microsoft Teams の更新としてリリースされます。
- Microsoft teams の会議室で、Surface Hub と Microsoft Teams Room device、または2つの Surface Hub デバイスを備えたスペースでの共同会議のサポートによって、Microsoft Teams の会議中にユーザーは両方のデバイスを簡単に活用できるようになりました。 1回タップするだけで、ユーザーは1つのデバイスにビデオフィードを表示し、もう一方のデバイスにデジタルのホワイトボードまたはコンテンツを表示することで、どちらのデバイスからでも会議に参加できます。 Windows 10 Team 2020 更新プログラムは、調整された会議を構成するためのモバイルデバイス管理 (MDM) のサポートを追加します。その後、この機能は、microsoft Store 経由で Microsoft Teams の更新としてリリースされます。
- パスワードを使用しないサインイン FIDO2 セキュリティキーを使用すると、ユーザー名とパスワードを入力しなくても、簡単に Surface Hub にサインインすることができます。 この機能を単一の Sign-On (SSO) と組み合わせることで、会議中にファイル、アプリ、web サイトの迅速でシームレスな認証を行うことができます。 詳細については、「 [Surface Hub でのパスワードをあまりサインイン](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate)しないように構成する」を参照してください。
- Microsoft Authenticator を使用したパスワードの入力を減らしたサインインの改善 Azure AD を使用している組織向けの microsoft authenticator アプリを使用すると、ユーザー名とパスワードを入力せずにサインインできます。 さらに、ユーザーは、ユーザープリンシパル名 (UPN) に加えて、Azure AD で優先メールエイリアスを使ってサインインすることもできます。 詳細については、「 [Microsoft Authenticator で Surface Hub にサインインする](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app)」を参照してください。
- Surface Hub の2つのペンを使用して、surface hub の2つのペンを使用して、surface hub の2つのペンを使って、surface hub の2つのペンで、2つのペンによる手描き入力 デュアルペン手書き入力を有効にするために必要なファームウェア更新プログラムは、それ以降の更新プログラムでリリースされる予定です。

 
 
 
