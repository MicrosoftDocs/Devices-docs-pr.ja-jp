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
ms.date: 03/06/2018
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 20ec9b3a81ad511bcb7880de6b53025fbac0a561
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836341"
---
# デバイス アカウントの作成およびテスト (Surface Hub)


このトピックでは、Microsoft Exchange や Skype と通信するために Microsoft Surface Hub で使用するデバイス アカウントを作成およびテストする方法について説明します。

**デバイス アカウント**とは、Surface Hub で次の用途に使用する Exchange リソース アカウントです。

-   会議のカレンダーを表示する
-   Teams または Skype for Business の通話に参加する
-   メールを送信する (たとえば、会議からホワイトボード コンテンツをメール送信するなど)

Surface Hub にデバイス アカウントをプロビジョニングすると、ユーザーは、会議室に招待するのと同様に、会議出席依頼にこのアカウントを追加できます。 

## 構成の概要

次の表では、デバイス アカウントを作成する際の主な手順と構成の決定について説明します。 
 
| ステップ | 説明                     |  目的                             |
|------|---------------------------------|--------------------------------------|
| 件    | ログオンが可能な Exchange リソース メールボックス (Exchange 2013 以降または Exchange Online) を作成する | このリソース メールボックスにより、デバイスで会議のカレンダーの管理、会議出席依頼の受信、メールの送信を行うことができます。 Surface Hub にプロビジョニングするには、このメールボックスがログオン可能である必要があります。 |
| 両面    | メールボックスのプロパティを構成する | Surface Hub で最適な会議エクスペリエンスを実現するには、メールボックスのプロパティを適切に構成する必要があります。 メールボックスのプロパティについて詳しくは、[メールボックスのプロパティに関するページ](exchange-properties-for-surface-hub-device-accounts.md)をご覧ください。 |
| -    | メールボックスに互換性のあるモバイル デバイス メールボックス ポリシーを適用する | Surface Hub は、モバイル デバイス メールボックス ポリシーではなく、モバイル デバイス管理 (MDM) を使用して管理されています。 互換性のため、デバイス アカウントのモバイル デバイス メールボックス ポリシーでは、**PasswordEnabled** 設定を False に設定する必要があります。 このように設定していない場合、Surface Hub はメールとカレンダーの情報を同期できません。 |
| 4d    | Skype for Business (Lync Server 2013 以降または Skype for Business Online) でメールボックスを有効にする | ビデオ通話、IM、画面共有など、さまざまな会議機能を使用するには、Skype for Business を有効にする必要があります。  |
| 個    | (省略可能) ActiveSync デバイス ID をホワイトリストに追加する | 組織によっては、デバイス アカウントでメールとカレンダーの情報を同期することを、グローバル ポリシーで禁止している場合があります。 その場合は、Surface Hub の ActiveSync デバイス ID を許可する必要があります。 |
| =    | (省略可能) パスワードの有効期限を無効にする | 管理を合理化するために、デバイス アカウントのパスワードの有効期限をオフにし、Surface Hub でデバイス アカウントのパスワードを自動的に循環できるように設定できます。 パスワード管理について詳しくは、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。  |

## 詳細な構成手順 

リモートの PowerShell を使用して、デバイス アカウントを設定することをお勧めします。 デバイス アカウントの作成と検証に役立つ PowerShell スクリプトが用意されています。PowerShell スクリプトと操作手順について詳しくは、「[付録 A: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)」をご覧ください。 

PowerShell を使用してデバイス アカウントをプロビジョニングする詳しい手順については、組織での展開に基づいて、次の表のオプションを選択してください。 

| 組織での展開             |  説明                  |
|---------------------------------|--------------------------------------|
| [オンライン展開 (Office 365)](online-deployment-surface-hub-device-accounts.md) | 組織の環境全体が Office 365 に展開されています。 |
| [オンプレミス展開 (単一フォレスト)](on-premises-deployment-surface-hub-device-accounts.md) | 組織で複数のサーバーを管理しており、これらのサーバーを使用して Active Directory、Exchange、Skype for Business (または Lync) を単一フォレスト環境でホストしています。 |
| [オンプレミス展開 (複数フォレスト)](on-premises-deployment-surface-hub-multi-forest.md) | 組織で複数のサーバーを管理しており、これらのサーバーを使用して Active Directory、Exchange、Skype for Business (または Lync) を複数フォレスト環境でホストしています。 |
| [ハイブリッド展開](hybrid-deployment-surface-hub-device-accounts.md) | 組織には、オンプレミスでホストされているサービスと、Office 365 を介してオンラインでホストされているサービスの両方が混在しています。 |
| [Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開](skype-hybrid-voice.md) | 組織では、クラウド上に Skype for Business のホーム プールと Exchange サーバーがあり、Skype for Business 2015、または公衆交換電話網 (PSTN) 経由で接続されたクラウド コネクタ エディションのオンプレミス プールを使っています。 |


グラフィカル ユーザー インターフェイス (UI) を使用する場合は、一部の手順を PowerShellではなく、UI を使用して実行できます。 詳しくは、「[UI を使用してデバイス アカウントを作成する ](create-a-device-account-using-office-365.md)」をご覧ください。

## アカウントの検証とテスト

Surface Hub デバイス アカウントを検証およびテストするための方法としては、[アカウント検証スクリプト](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts)と [Surface Hub Hardware Diagnostic アプリ](https://www.microsoft.com/store/apps/9nblggh51f2g)の 2 つの方法があります。 アカウント検証スクリプトでは、デスクトップから PowerShell を使用して、以前に作成したデバイス アカウントを検証します。 Surface Hub Hardware Diagnostic アプリは、Surface Hub にインストールされ、サインインや通信の障害に関する詳細なフィードバックを提供します。 どちらも新しく作成したデバイス アカウントをテストするための優れたツールであり、最適なアカウントの可用性を確保するために使用する必要があります。

 

 

 





