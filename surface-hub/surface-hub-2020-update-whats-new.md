---
title: Windows 10 Team 2020 更新プログラムの新機能
description: Surface Hub オペレーティング システムの最新の更新プログラムである Windows 10 Team 2020 Update の新機能を確認してください。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 14e08cf099ac441f7b2b3b76366406868ac6c056
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470425"
---
# <a name="whats-new-in-windows-10-team-2020-update"></a>Windows 10 Team 2020 更新プログラムの新機能

Windows 10 Team 2020 Update は、最新の Windows 10 機能と共に、デバイスの展開と管理性に大きな改善を提供します。

##  <a name="deployment-and-manageability"></a>展開と管理のしやすさ

- **クラウド デバイス アカウントの最新の認証**。 Surface Hub は、Exchange に接続するための Exchange Web サービス (EWS) および Active Directory 認証ライブラリ (ADAL) ベースの認証をサポートしており、お客様は基本認証の使用を非推奨にできます。 詳細については [、「Surface Hub でのモダン認証」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth)。
- **20 を超える新規および更新されたモバイル デバイス管理 (MDM) ポリシー設定**。  これらのポリシー設定により、IT 管理者は、Microsoft Store からのアプリの更新、インフラストラクチャ上の Miracast などのワイヤレスプロジェクション設定、Quality-Of-Service や 802.1x 有線認証などのネットワーク設定、プライバシー/GDPR 関連の新しい設定など、複数のデバイス設定を制御できます。 新しい構成サービス プロバイダー (CSP) には、次のものが含まれます。 

  - [Accounts CSP](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) 
  - [Firewall-CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) 
  - [RemoteWipe CSP](https://docs.microsoft.com/windows/client-management/mdm/remotewipe-csp) 
  - [Wifi-CSP](https://docs.microsoft.com/windows/client-management/mdm/wifi-csp) 
  - [Wirednetwork-CSP](https://docs.microsoft.com/windows/client-management/mdm/wirednetwork-csp) 

詳細については、次を参照してください。 
- [Microsoft Surface Hub でサポートされている CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [MDM プロバイダーを使用して Surface Hub を管理する](manage-settings-with-mdm-for-surface-hub.md)


##  <a name="azure-active-directory-joined-devices"></a>Azure Active Directory 参加デバイス

- **Azure に参加しているデバイスのシングル サインオン (SSO) ADサインインします**。 ユーザーが Microsoft 365 資格情報を使用して "My Meetings and files" にサインインすると、ユーザー資格情報はアプリからアプリにシームレスに流れ、ブラウザーでの Microsoft 365 エクスペリエンスも含めます。
- **参加しているデバイスに対する Azure ADアクセス (CA)**。       IT 管理者は、デバイス レベルのセキュリティ ポリシーを Azure AD に参加している Surface Hub に展開して、企業のセキュリティとコンプライアンスの要件に従って組織のリソースへのアクセスを制御できます。
- **参加しているデバイスに対する Azure 管理者以外ADサポート**。 顧客は、Surface Hub を管理するために、管理者階層内の管理者のより詳細なセットを選択できます。 詳細については [、「Surface Hub でグローバル以外の管理者アカウントを構成する」を参照してください](surface-hub-2s-nonglobal-admin.md)。


## <a name="browser-and-pen"></a>ブラウザーとペン

- **新しい Microsoft Edge のサポート**。 Microsoft Edge は、最適な互換性のパフォーマンス、セキュリティ、プライバシーのために再構築されました。 詳細については、「Surface Hub に新しい Microsoft Edge をインストールして [構成する」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge)。
- **Surface Hub 2S**でのデュアル ペン インク。   ユーザーは、2 つの Surface Hub 2 ペンを使用して、Surface Hub 2S でサイド バイ サイドでホワイトボードと共同作業を行います。 デュアル ペンインクを有効にするために必要なファームウェア更新プログラムは、以降の更新プログラムでリリースされます。

## <a name="microsoft-teams"></a>Microsoft Teams  

- **Microsoft Teams は既定でインストールされています**。        Microsoft Teams は、MDM を介して、または設定アプリを使用して Surface Hub で直接変更または構成できる、新しい Surface Hub デバイス上の既定の会議、通話、およびコラボレーション アプリとして含まれています。 詳細については [、「Deploy Microsoft Teams」を参照してください](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub)。
- **Microsoft Teams との近接参加のサポート**。  近接参加を使用すると、ユーザーは、ラップトップ/電話を使用して近くの Surface Hub でスケジュールされた Microsoft Teams 通話を受け取る、または進行中の会議を近くの Surface Hub にシームレスに移行できます。 Windows 10 Team 2020 Update は、モバイル デバイス管理 (MDM) のサポートを追加して、近接参加を構成します。 詳細については、次を参照してください。 

  - [Microsoft Teams ブログ](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833). 
  - [Surface Hub で Microsoft Teams の設定を管理する](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

- **Microsoft Teams との調整された会議のサポート**。 Surface Hub と Microsoft Teams Room デバイスを備える会議室、または 2 台の Surface Hub デバイスを備えるスペースでは、調整された会議を使用すると、Microsoft Teams 会議中に両方のデバイスを簡単に利用できます。 1 回のタップで、ユーザーはいずれかのデバイスから会議に参加し、1 つのデバイスにビデオ フィードを表示し、もう一方のデバイスにデジタル ホワイトボードまたはコンテンツを表示することで、画面の不動産を最大化できます。 Windows 10 Team 2020 Update では、モバイル デバイス管理 (MDM) のサポートが追加され、調整された会議を構成する機能が Microsoft Store.To を通じて Microsoft Teams の更新プログラムとしてリリースされます。詳細については、「Set up Coordinated Meetings with Microsoft Teams Rooms and [Surface Hub」](https://docs.microsoft.com/microsoftteams/rooms/coordinated-meetings)を参照してください。

## <a name="security"></a>Security

- **FIDO2 セキュリティ キーを使用したパスワードレス サインイン**     FIDO2 セキュリティ キーを使用すると、ユーザー名とパスワードを入力することなく、Surface Hub にすばやく簡単にサインインできます。 シングル Sign-On (SSO) と組み合わせて、この機能は会議中にファイル、アプリ、および Web サイトに高速かつシームレスな認証を提供します。 詳細については [、「Configure passwordless sign-in on Surface Hub」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate)。
- **Microsoft Authenticator を使用したパスワードレス サインインの機能強化**。  Azure ADを使用する組織では、ユーザーはユーザー名とパスワードを入力することなく、Microsoft Authenticator アプリを使用してサインインできます。 さらに、ユーザーは、ユーザー プリンシパル名 (UPN) に加えて、Azure AD優先メール エイリアスを使用してサインインできます。 詳細については [、「Microsoft Authenticator を使用して Surface Hub にサインインする」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app)。


## <a name="learn-more"></a>詳細情報

- [Windows 10 Team のロールアウトに関する更新プログラム](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)
- [Windows 10 Team 2020 の更新プログラムをインストールする](surface-hub-2020-update.md)  
 