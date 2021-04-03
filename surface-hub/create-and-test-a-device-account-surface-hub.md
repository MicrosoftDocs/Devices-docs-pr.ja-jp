---
title: デバイス アカウントの作成およびテスト (Surface Hub)
description: このトピックでは、Microsoft Exchange や Skype と通信するために Microsoft Surface Hub で使用するデバイス アカウントを作成およびテストする方法について説明します。
ms.assetid: C8605B5F-2178-4C3A-B4E0-CE32C70ECF67
ms.reviewer: rikot
manager: laurawi
keywords: デバイス アカウントの作成とテスト, デバイス アカウント, Surface Hub と Microsoft Exchange, Surface Hub と Skype
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/01/2021
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 685359f1371a1bef8bd216223a98b934c997a1d8
ms.sourcegitcommit: 879e80200aea26f6705c887fa392db5db35b99ed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2021
ms.locfileid: "11475091"
---
# <a name="create-and-test-a-device-account-surface-hub"></a>デバイス アカウントの作成およびテスト (Surface Hub)

Surface Hub デバイス アカウント (リソース アカウント/会議室メールボックスとも呼ばれる) を作成すると、Surface Hub は会議出席依頼の受信、承認、または辞退を行い、会議に参加できます。

デバイス アカウントが Surface Hub でプロビジョニングされた後、ユーザーは会議室を招待するのと同じ方法で、このアカウントを会議出席依頼に追加できます。 

デバイス アカウントは、アウトオブボックス エクスペリエンス [(OOBE) のセットアップ中に構成できます](first-run-program-surface-hub.md)。 必要に応じて、[設定] Surface Hub**** アカウントで後で  >  **変更**  >  **することもできます**。

## <a name="configuration-overview"></a>構成の概要

次の表では、デバイス アカウントを作成する際の主な手順と構成の決定について説明します。
 
| ステップ | 説明                     |  目的                             |
|------|---------------------------------|--------------------------------------|
| 1    | ログオンが有効なルーム メールボックスを作成する (Exchange Online または Exchange Server 2016 以降) | この種類のメールボックスを使用すると、デバイスは会議の予定表を維持し、会議出席依頼を受信し、メールを送信できます。 Surface Hub で使用するには、ログオンが有効になっている必要があります。 |
| 2    | メールボックスのプロパティを構成する | Surface Hub で最適な会議エクスペリエンスを実現するには、メールボックスのプロパティを適切に構成する必要があります。 メールボックスのプロパティについて詳しくは、[メールボックスのプロパティに関するページ](exchange-properties-for-surface-hub-device-accounts.md)をご覧ください。 |
| 3    | Exchange Web Services (EWS) が有効で、多要素認証 (MFA) が無効になっているか確認する | Surface Hub は EWS を使用して予定表を同期します。 既定で環境で EWS を許可しない場合は、ハブ メールボックスを明示的に有効にする必要があります。 Surface Hub は、ユーザー操作なしでバックグラウンドで Exchange にログインします。MFA などの対話型のプロンプトには応答できません。 作成するデバイス アカウントは、そのような認証要件から除外する必要があります。 このように設定していない場合、Surface Hub はメールとカレンダーの情報を同期できません。 |
| 4    | Teams または Skype for Business のアカウントを有効にする (Skype for Business Server 2015 以降) | ビデオ通話、IM、画面共有など、会議機能を使用するには、Skype for Business または Teams を有効にする必要があります。 Teams を有効にするライセンスの詳細については [、「Teams ミーティング](https://docs.microsoft.com/MicrosoftTeams/rooms/rooms-licensing) ルームのライセンス」および「Teams サービスの説明 [」を参照してください](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description)。 |
| 5    | (省略可能) パスワードの有効期限を無効にする | 管理を合理化するために、デバイス アカウントのパスワードの有効期限をオフにし、Surface Hub でデバイス アカウントのパスワードを自動的に循環できるように設定できます。 パスワード管理について詳しくは、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。  |
| 6    | (省略可能)ActiveSync を許可する Exchange ポリシーを構成する | Active Directory 展開の特定のオンプレミス Exchange Server & ActiveSync を使用して、デバイス アカウントのメールと予定表の情報を同期します。 構成するポリシーの詳細については、「Surface Hub アカウントの [ActiveSync ポリシー」を参照してください](apply-activesync-policies-for-surface-hub-device-accounts.md)。 |

> [!NOTE]  
> Surface Hub デバイス アカウントは、サード パーティのフェデレーション ID プロバイダー (IdP) をサポートし、Active Directory または Azure Active Directory を介して認証する必要があります。

## <a name="detailed-configuration-steps"></a>詳細な構成手順 

リモート デバイス アカウントを使用して Surface Hub デバイス アカウントをセットアップすることをおWindows PowerShell。 Microsoft は [SkypeRoomProvisioningScript.ps1、 ](https://go.microsoft.com/fwlink/?linkid=870105)新しいリソース アカウントの作成や既存のリソース アカウントの検証に役立つスクリプトを提供し、それらを互換性のある Surface Hub デバイス アカウントに変換するのに役立ちます。 必要に応じて、以下の表からオプションを選択し、組織の展開に基づいて詳細な PowerShell の手順に従います。

| 組織での展開             |  説明                  |        Surface Hub のセットアップ中に使用する形式
|---------------------------------|--------------------------------------|
| [オンライン展開 (Microsoft 365 または Office 365)](https://docs.microsoft.com/microsoftteams/rooms/with-office-365) |組織の環境は、Microsoft 365 または microsoft 365 Office展開されます。 | username@domain.com |
| [ハイブリッド展開 (Exchange オンプレミス)](https://docs.microsoft.com/microsoftteams/rooms/with-exchange-on-premises) | 組織には、オンプレミスと Microsoft Teams オンラインでホストExchange Serverサービスが混在しています。 | username@domain.com [Exchange でハイブリッドモダン](https://docs.microsoft.com/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication) 認証が有効になっている場合、それ以外の場合は DOMAIN\username |
| [ハイブリッド展開 (Exchange Online)](https://docs.microsoft.com/microsoftteams/rooms/with-exchange-online) | 組織には、Skype for Business Server がオンプレミスでホストされているサービスと Exchange Online が混在しています。 | username@domain.com SfB [でハイブリッドモダン認証](https://docs.microsoft.com/microsoft-365/enterprise/configure-skype-for-business-for-hybrid-modern-authentication) が有効になっている場合、それ以外の場合は DOMAIN\username |
| [オンプレミス展開 (単一フォレスト)](https://docs.microsoft.com/microsoftteams/rooms/with-skype-for-business-server-2015) | 組織には、Active Directory、Exchange、Skype for Business Server が単一フォレスト環境でホストされているサーバーがあります。  | DOMAIN\username |
| [オンプレミス展開 (複数フォレスト)](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/multiple-forest-on-premises-deployments) | 組織には、Active Directory、Exchange、Skype for Business Server が複数フォレスト環境でホストされている、制御するサーバーがあります。 | ACCOUNTFOREST\username |


## <a name="account-verification-and-testing"></a>アカウントの検証とテスト

Surface Hub デバイス アカウントの検証とテストに使用できる方法は、SkypeRoomProvisioningScript.ps1Surface [](https://go.microsoft.com/fwlink/?linkid=870105) [Hub](https://www.microsoft.com/store/apps/9nblggh51f2g)ハードウェア診断アプリです。 アカウント プロビジョニング スクリプトは、PC から PowerShell を使用して、以前に作成したデバイス アカウントを検証できます。 Surface Hub Hardware Diagnostic アプリは、Surface Hub にインストールされ、サインインや通信の障害に関する詳細なフィードバックを提供します。 どちらも新しく作成したデバイス アカウントをテストするための優れたツールであり、最適なアカウントの可用性を確保するために使用する必要があります。
