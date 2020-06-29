---
title: Surface Hub 2S の環境の準備
description: Surface Hub 2S の環境を準備するために必要な操作について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 11/21/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 38f02b885a0ac2789ffc82f1ab38dc57fea5e841
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835342"
---
# Surface Hub 2S の環境の準備

## Office 365 の準備

Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft ホワイトボードを使用しており、Intune で Surface Hub 2 を管理する必要がある場合は、まず[エンドポイントの Office 365 の要件](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)を確認してください。

Office 365 エンドポイントは、すべての信頼された Office 365 ネットワーク要求をファイアウォール経由で直接送信することで、ネットワークの最適化を支援します。追加のパケットレベルの検査や処理はすべてバイパスします。 この機能により、待機時間と境界容量の要件を減らすことができます。

Microsoft は、Office 365 サービスを定期的に更新します。新機能により、必要なポート、Url、IP アドレスが変更される可能性があります。 変更を評価、構成して最新の状態に保つには、 [Office 365 IP アドレスと URL Web サービス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)を購読します。

## デバイスの所属

デバイスの所属を使って、Surface Hub 2S の設定アプリへのユーザーアクセスを管理します。
Windows 10 Team Edition オペレーティングシステム (Surface Hub 2S で実行される) では、許可されたユーザーのみが設定アプリを使って設定を調整できます。 所属の選択によって機能の可用性に影響を与える可能性があるため、ユーザーが意図した機能に確実にアクセスできるように、適切な計画を立ててください。

> [!NOTE]
> デバイスの所属を設定できるのは、初期の既定のエクスペリエンス (OOBE) セットアップ時のみです。 デバイスの所属をリセットする必要がある場合は、OOBE のセットアップを繰り返す必要があります。

## 所属しません

所属しません。各 Surface Hub 2S に異なるローカル管理者アカウントがあるワークグループには Surface Hub の2S があります。 [所属しない] を選んだ場合は、 [BitLocker キーを USB サムドライブにローカルに](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)保存する必要があります。 引き続き、Intune でデバイスを登録することができます。ただし、OOBE 中に構成されたアカウントの資格情報を使用して設定アプリにアクセスできるのは、ローカル管理者のみです。 設定アプリから管理者アカウントのパスワードを変更することができます。

## Active Directory Domain Services

オンプレミスの Active Directory ドメインサービスと Surface Hub 2S を利用している場合は、ドメインのセキュリティグループを使用して、設定アプリへのアクセスを管理する必要があります。 これにより、すべてのセキュリティグループメンバーに、Surface Hub 2S の設定を変更するアクセス許可を与えることができます。 次の点にも注意してください。

- Surface Hub の系列がオンプレミスの Active Directory ドメインサービスと関連付けられている場合、BitLocker キーを Active Directory スキーマに保存することができます。 詳細については、「[組織の BitLocker 用の準備: 計画とポリシー](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)」を参照してください。 
- 組織の信頼されたルート Ca は Surface Hub 2S の同じコンテナーにプッシュされるため、プロビジョニングパッケージを使ってインポートする必要はありません。
- 引き続き、Intune でデバイスを登録して、Surface Hub 2S の設定を一元管理することができます。

## Azure Active Directory

Surface Hub 2S を Azure Active Directory (Azure AD) と連携するように選択すると、グローバル管理者セキュリティグループのユーザーは Surface Hub 2S の設定アプリにサインインできるようになります。 現在、他のグループを委任して、Surface Hub 2S の設定アプリにサインインすることはできません。

組織の Intune 自動登録を有効にしている場合、Surface Hub 2S は Intune に自動的に登録されます。 デバイスの BitLocker キーは、Azure AD に自動的に保存されます。 Azure AD で affiliating Surface Hub 2S が使用されている場合、シングルサインオンと簡単な認証は機能しません。
