---
title: Surface Hub 2S の環境の準備
description: Surface Hub 2S の環境を準備するために必要な操作について学習します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/28/2020
ms.localizationpriority: Medium
ms.openlocfilehash: af66449806c9aa525fa3f5df84012d3daeed96ba
ms.sourcegitcommit: dbd14649442ad039aeb265cd60ed029d483a4bb0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/29/2020
ms.locfileid: "11251454"
---
# Surface Hub 2S の環境の準備

## Office 365 の準備

Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft Whiteboard を使用し、Intune で Surface Hub 2S を管理する場合は、まずエンドポイントの [Office 365](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)の要件を確認します。

Office 365 エンドポイントは、すべての信頼できる Office 365 ネットワーク要求をファイアウォール経由で直接送信し、追加のパケット レベルの検査または処理をバイパスすることで、ネットワークを最適化するのに役立ちます。 この機能により、待機時間と境界容量の要件が軽減されます。

Microsoft は、Office 365 サービスを定期的に更新し、必要なポート、URL、IP アドレスを変更する可能性があります。 変更を評価、構成、および最新の情報を得るには、Office [365 IP アドレス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)と URL Web サービスにサブスクライブします。

> [!NOTE]
> Surface Hub は、Microsoft Teams、Skype for Business Server 2019、Skype for Business Server 2015、または Skype for Business Online と一緒に動作します。
Lync Server 2013 などの以前のプラットフォームはサポートされていません。 Surface Hub は、GCC-High DoD 環境ではサポートされていません。


## デバイスの所属

デバイスの所属を使用して、Surface Hub 2S の設定アプリへのユーザー アクセスを管理します。
Windows 10 Team オペレーティング システム (Surface Hub 2S で実行) では、承認されたユーザーのみが設定アプリを使って設定を調整できます。 所属を選択すると機能の可用性に影響を与える可能性があります。そのため、ユーザーが意図した方法で機能にアクセスできるよう適切に計画します。

> [!NOTE]
> デバイスの所属は、初期の Out-Of-Box Experience (OOBE) セットアップ時にのみ設定できます。 デバイスの所属をリセットする必要がある場合は、OOBE セットアップを繰り返す必要があります。

## 所属なし

所属は、各 Surface Hub 2S で異なるローカル管理者アカウントを持つワークグループに Surface Hub 2S を持つような関係はありません。 [No affiliation] (所属なし) を選択した場合は、BitLocker キーを USB サム [ドライブにローカルに保存する必要があります](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)。 デバイスを Intune に登録することもできます。ただし、OOBE 中に構成されたアカウント資格情報を使用して設定アプリにアクセスできるのはローカル管理者のみです。 管理者アカウントのパスワードは、設定アプリから変更できます。

## Active Directory Domain Services

Surface Hub 2S をオンプレミスの Active Directory ドメイン サービスと関連付けられている場合は、ドメインのセキュリティ グループを使用して設定アプリへのアクセスを管理する必要があります。 これにより、すべてのセキュリティ グループ メンバーに、Surface Hub 2S の設定を変更するアクセス許可が付与されます。 次の点にも注意してください。

- Surface Hub 2S がオンプレミスの Active Directory ドメイン サービスと提携している場合、BitLocker キーを Active Directory スキーマに保存できます。 詳細については [、「BitLocker 用に組織を準備する: 計画とポリシー」を参照してください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)。

- 組織の信頼されたルート CA が Surface Hub 2S の同じコンテナーにプッシュされます。つまり、プロビジョニング パッケージを使ってインポートする必要はありません。

- デバイスを Intune に登録して、Surface Hub 2S の設定を一中央に管理することもできます。

## Azure Active Directory

Surface Hub 2S を Azure Active Directory (Azure AD) と関連付け選択すると、グローバル管理者セキュリティ グループのユーザーは、Surface Hub 2S の設定アプリにサインインできます。 現在、Surface Hub 2S の設定アプリにサインインする他のグループは委任されません。

組織で Intune の自動登録を有効にした場合、Surface Hub 2S は自動的に Intune に登録します。 デバイスの BitLocker キーは、Azure AD に自動的に保存されます。 Azure AD を使用して Surface Hub 2S に関連付けすると、シングル サインオンと簡単な認証は機能しません。
