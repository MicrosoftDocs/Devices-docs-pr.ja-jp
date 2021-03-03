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
ms.date: 2/26/2021
ms.localizationpriority: Medium
ms.openlocfilehash: caa6372820222f6f2f225f028161b3441b147a82
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385145"
---
# <a name="prepare-your-environment-for-surface-hub-2s"></a>Surface Hub 2S の環境の準備

## <a name="office-365-readiness"></a>Office 365 準備

Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft ホワイトボードを使用し、Intune で Surface Hub 2S を管理する場合は、まずエンドポイントの [Office 365](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)要件を確認してください。

Office 365 エンドポイントは、すべての信頼できる Office 365 ネットワーク要求をファイアウォール経由で直接送信し、追加のパケット レベルの検査または処理をバイパスすることで、ネットワークを最適化するのに役立ちます。 この機能により、待機時間と境界容量の要件が軽減されます。

Microsoft は、Office 365 サービスを定期的に更新し、必要なポート、URL、IP アドレスを変更する可能性があります。 変更を評価、構成、および最新の情報に更新するには [、365 IP](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)アドレスと URL Web サービスOfficeを購読します。

> [!NOTE]
> Surface Hub は、Microsoft Teams、Skype for Business Server 2019、Skype for Business Server 2015、または Skype for Business Online と動作します。
Lync Server 2013 などの以前のプラットフォームはサポートされていません。 Surface Hub は、ユーザーまたは DoD GCC-Highサポートされていません。


## <a name="device-affiliation"></a>デバイスの所属

デバイスの所属を使用して、Surface Hub 2S の設定アプリへのユーザー アクセスを管理します。
Windows 10 Team オペレーティング システム (Surface Hub 2S で実行) を使用すると、承認されたユーザーのみが設定アプリを使用して設定を調整できます。 所属を選択すると機能の可用性に影響を与える可能性があるから、ユーザーが意図した通り機能にアクセスできるよう適切に計画してください。

> [!NOTE]
> デバイスの所属は、最初のアウトオブボックス エクスペリエンス (OOBE) セットアップ中にのみ設定できます。 デバイスの所属をリセットする必要がある場合は、OOBE セットアップを繰り返す必要があります。

## <a name="no-affiliation"></a>所属なし

各 Surface Hub 2S に別のローカル管理者アカウントを持つワークグループに Surface Hub 2S を含む所属はありません。 [所属なし] を選択した場合は、BitLocker キーを USB サム [ドライブにローカルに保存する必要があります](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)。 Intune でデバイスを登録することもできます。ただし、OOBE 中に構成されたアカウント資格情報を使用して、ローカル管理者だけが設定アプリにアクセスできます。 管理者アカウントのパスワードは、設定アプリから変更できます。

## <a name="active-directory-domain-services"></a>Active Directory Domain Services

Surface Hub 2S をオンプレミスの Active Directory ドメイン サービスに関連付けられている場合は、ドメインのセキュリティ グループを使用して設定アプリへのアクセスを管理する必要があります。 これにより、すべてのセキュリティ グループ メンバーに Surface Hub 2S の設定を変更するアクセス許可が付与されます。 また、次の点に注意してください。

- Surface Hub 2S がオンプレミスの Active Directory ドメイン サービスに関連付けられている場合、BitLocker キーを Active Directory スキーマに保存できます。 詳細については、「組織を BitLocker 用に準備する: 計画と [ポリシー」を参照してください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)。

- 組織の信頼されたルート CA は Surface Hub 2S の同じコンテナーにプッシュされます。つまり、プロビジョニング パッケージを使用してインポートする必要はありません。

- デバイスを Intune に登録して、Surface Hub 2S の設定を一方的に管理することもできます。

## <a name="azure-active-directory"></a>Azure Active Directory

Surface Hub 2S を Azure Active Directory (Azure AD) に関連付け選択すると、グローバル管理者セキュリティ グループのすべてのユーザーが Surface Hub 2S の設定アプリにサインインできます。 また、Surface Hub 2S の設定アプリの管理に対するアクセス許可を制限するグローバル管理者以外のアカウントを構成することもできます。 これにより、Surface Hub 2S の管理者アクセス許可のみを対象範囲に設定し、Azure Hub ドメイン全体で望ましくない可能性のある管理者アクセスをADできます。 

組織で Intune 自動登録を有効にした場合、Surface Hub 2S は自動的に Intune に登録されます。 デバイスの BitLocker キーは、Azure サーバーに自動的にAD。 

Azure を使用して Surface Hub を管理する方法の詳細についてはADを参照してください。 

 - [管理者グループの管理](admin-group-management-for-surface-hub.md)
 - [Surface Hub 2S でグローバル管理者以外のアカウントを構成する](surface-hub-2s-nonglobal-admin.md)

