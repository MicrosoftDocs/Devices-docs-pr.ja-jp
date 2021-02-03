---
title: Windows 10 Team 2020 更新プログラムの新機能
description: Surface Hub オペレーティング システムの最新の更新プログラムである Windows 10 Team 2020 Update の新機能をご確認ください。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: Medium
ms.openlocfilehash: f87b8f084b8731bfb329b6c52403d565bca03e3e
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312053"
---
# Windows 10 Team 2020 更新プログラムの新機能

Windows 10 Team 2020 Update では、最新の Windows 10 機能と共に、デバイスの展開と管理性が大幅に向上しています。

##  展開と管理のしやすさ

- **クラウド デバイス アカウントの最新の認証**。 Surface Hub では、Exchange に接続するための Exchange Web サービス (EWS) および Active Directory 認証ライブラリ (ADAL) ベースの認証がサポートされており、ユーザーは基本認証の使用を廃止できます。 詳しくは [、Surface Hub でのモダン認証に関するページをご覧ください](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth)。
- **20 を超える新規および更新されたモバイル デバイス管理 (MDM) ポリシー**。      これらのポリシーにより、IT 管理者は、Microsoft Store からのアプリの更新、Miracast over インフラストラクチャなどのワイヤレス プロジェクション設定、サービス品質や 802.1x ワイヤード (有線) 認証などのネットワーク設定、新しいプライバシー/GDPR 関連の設定など、複数のデバイス設定に対する制御を強化できます。 詳細については、次を参照してください。 
- [Microsoft Intune を使用して Surface Hub 2S を管理します](surface-hub-2s-manage-intune.md)。
- [Microsoft Surface Hub でサポートされている Policy CSP](https://docs.microsoft.com//windows/client-management/mdm/policy-csps-supported-by-surface-hub)

##  Azure Active Directory に参加しているデバイス

- **Azure のシングル サインオン (SSO) とADデバイス**。 ユーザーが Microsoft 365 の資格情報で "マイ ミーティングとファイル" にサインインすると、ユーザー資格情報はアプリからアプリにシームレスに流れ、ブラウザーでの Microsoft 365 エクスペリエンスも含めます。
- **Azure および参加しているデバイスの条件付AD (CA)。**       IT 管理者は、Azure AD に参加している Surface Hub にデバイス レベルのセキュリティ ポリシーを展開して、企業のセキュリティとコンプライアンスの要件に従って組織のリソースへのアクセスを制御できます。
- **Azure または参加しているデバイスに対するグローバルADサポート**。 お客様は、管理者階層内の管理者のより詳細なセットを選択して、Surface Hub を管理できます。 詳細については [、「Surface Hub 2S でグローバル管理者以外のアカウントを構成する」を参照してください](surface-hub-2s-nonglobal-admin.md)。


## ブラウザーとペン

- **新しい Microsoft Edge のサポート**。 Microsoft Edge は、最適な互換性のパフォーマンス、セキュリティ、プライバシーのために再構築されました。 詳細については、「Surface Hub に新しい Microsoft Edge をインストール [して構成する」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge)。
- - **Surface Hub 2S でのデュアル ペンのインク**入力。   ユーザーは、2 つの Surface Hub 2 ペンを使用して、Surface Hub 2S でホワイトボードと共同作業をサイド バイ サイドで行います。 デュアル ペンによるインク入力を有効にするために必要なファームウェア更新プログラムは、後続の更新プログラムでリリースされます。

## Microsoft Teams  

- **Microsoft Teams は既定でインストールされています**。        Microsoft Teams は、新しい Surface Hub デバイス上の既定の会議、通話、コラボレーション アプリとして含まれています。このアプリは、MDM 経由で、または設定アプリを使用して Surface Hub で直接変更または構成できます。 詳細については [、「Microsoft Teams の展開」を参照してください](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub)。
- **Microsoft Teams での近接参加のサポート**。  近接参加を使用すると、ユーザーはノート PC/電話を使って近くの Surface Hub でスケジュールされた Microsoft Teams 通話を受けるか、進行中の会議を近くの Surface Hub にシームレスに移行できます。 Windows 10 Team 2020 Update では、モバイル デバイス管理 (MDM) のサポートが追加され、近接参加が構成されます。 詳細については、次を参照してください。 

  - [Microsoft Teams ブログ](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833)。 
  - [Surface Hub で Microsoft Teams の設定を管理する](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

- **Microsoft Teams との調整された会議のサポート**。 Surface Hub と Microsoft Teams Room デバイスを備えるミーティング ルーム、または 2 台の Surface Hub デバイスを備えるスペースでは、調整された会議を使用すると、ユーザーは Microsoft Teams の会議中に両方のデバイスを簡単に利用できます。 1 回のタップで、ユーザーはいずれかのデバイスから会議に参加し、1 つのデバイスにビデオ フィードを表示し、もう一方のデバイスにデジタル ホワイトボードまたはコンテンツを表示することで、画面の大きな表示を最大化できます。 Windows 10 Team 2020 Update では、モバイル デバイス管理 (MDM) のサポートが追加され、調整された会議を構成できます。この機能は、Microsoft Store.To を通じて Microsoft Teams の更新プログラムとしてリリースされます。詳細については [、「Microsoft Teams ミーティング](https://docs.microsoft.com/microsoftteams/rooms/coordinated-meetings)と Surface Hub で調整された会議をセットアップする」を参照してください。

## Security

- **FIDO2 セキュリティ キーを使用したパスワードレス サインイン**     FIDO2 セキュリティ キーを使用すると、ユーザーはユーザー名とパスワードを入力することなく、すばやく簡単に Surface Hub にサインインできます。 この機能は、単一Sign-On (SSO) と組み合わせて、会議中にファイル、アプリ、および Web サイトに対して迅速かつシームレスな認証を提供します。 詳細については [、「Surface Hub でパスワードレス サインインを構成する」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate)。
- **Microsoft Authenticator を使用したパスワードレス サインインの機能強化**。  Azure AD を使用する組織では、ユーザーはユーザー名とパスワードを入力せずに Microsoft Authenticator アプリを使用してサインインできます。 さらに、ユーザーは、ユーザー プリンシパル名 (UPN) に加えて、Azure ADの優先メール エイリアスを使用してサインインできます。 詳細については [、「Microsoft Authenticator を使用して Surface Hub にサインインする」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app)。


## 詳細情報

- [Windows 10 Team のロールアウトに関する更新プログラム](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)
- [Windows 10 Team 2020 の更新プログラムをインストールする](surface-hub-2020-update.md)  
 