---
title: 管理者グループの管理
description: デバイスで設定アプリを起動すると、すべての Microsoft Surface Hub を個別に構成できます。
ms.assetid: FA67209E-B355-4333-B903-482C4A3BDCCE
ms.reviewer: ''
manager: laurawi
keywords: 管理者グループの管理, 設定アプリ, Surface Hub の構成
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: medium
ms.openlocfilehash: 36c6010307603b36b8798a09aed26f8b337b2c1b
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "11311953"
---
# Surface Hub の管理グループの管理


デバイスで設定アプリを使用すると、すべての Surface Hub をローカルで構成できます。 承認されていないユーザーによって設定が変更されるのを防ぐため、設定アプリでは、アプリを起動する際に管理者の資格情報が求められます。


## 管理者グループの管理

デバイスの管理者アカウントは、次の方法で設定できます。

- [ローカル管理者アカウントを作成する](#create-a-local-admin-account)
- [デバイスを Active Directory にドメイン参加する](#domain-join-the-device-to-active-directory)
- [Azure ADデバイスに参加する](#azure-ad-join-the-device)
- [参加しているデバイスに Azure AD管理者以外のアカウントを構成する (Surface Hub 2S)](#configure-non-global-admin-accounts-on-azure-ad-joined-devices)


### ローカル管理者アカウントを作成する

ローカル管理者を作成するには、[最初の実行時にローカル管理者の使用を選択します](first-run-program-surface-hub.md#use-a-local-admin)。 これにより、Surface Hub に、選択したユーザー名とパスワードを使用するローカル管理者アカウントが 1 つ作成されます。 これらの資格情報を使用して、設定アプリを開きます。

ローカル管理者アカウントの情報は、ディレクトリ サービスによってサポートされないことに注意してください。 デバイスで Active Directory (AD) または Azure Active Directory (Azure AD) にアクセスできない場合にのみ、ローカル管理者を選ぶことをお勧めします。 ローカル管理者のパスワードを変更する場合は、[設定] で変更できます。 ただし、ローカル管理者アカウントの使用からドメインまたは Azure AD テナントのグループの使用に変更する場合は、[デバイスをリセット](device-reset-surface-hub.md)して、初回設定プログラムを再度実行する必要があります。

### デバイスを Active Directory にドメイン参加

Surface Hub を AD ドメインに参加させると、指定したセキュリティ グループのユーザーが設定を構成できるようになります。 初回実行時に、[Active Directory ドメイン サービス](first-run-program-surface-hub.md#use-active-directory-domain-services)の使用を選択します。 選択したドメインに参加させる権限のある資格情報と既存のセキュリティ グループの名前を指定する必要があります。 そのセキュリティ グループのメンバーであるユーザーが自身の資格情報を入力すると、設定のロックを解除できます。

#### Surface Hub をドメインに参加させた場合の動作
Surface Hub をドメインに参加させると、次のような処理が可能になります。
- AD 内の指定したセキュリティ グループのメンバーに管理者権限を付与します。
- デバイスの BitLocker 回復キーを AD のコンピューター オブジェクトに保存することによって、BitLocker 回復キーをバックアップします。 詳しくは、「[BitLocker キーの保存](save-bitlocker-key-surface-hub.md)」をご覧ください。
- 暗号化された通信用にシステム クロックをドメイン コントローラーと同期します。

Surface Hub では、ドメイン コントローラーからグループ ポリシーまたは証明書を適用することはサポートされていません。

> [!NOTE]
> Surface Hub にドメインとの信頼がなくなった場合 (たとえば、ドメイン参加後にドメインから Surface Hub を削除する場合)、デバイスに対して認証を受けて設定を開くことができなくなります。 Surface Hub とドメインとの信頼関係を削除する場合は、先に[デバイスをリセット](device-reset-surface-hub.md)します。


### Azure ADデバイスに参加する

Azure Active Directory (Azure AD) を使用して Surface Hub に参加すると、Azure AD テナントの IT 管理者が設定を構成できます。 初回実行時に、[Microsoft Azure Active Directory](first-run-program-surface-hub.md#use-microsoft-azure-active-directory) の使用を選択します。 選択した Azure AD テナントに参加させることのできる資格情報を入力する必要があります。 Azure AD への参加が正常に完了すると、適切なユーザーにデバイスの管理者権限が付与されます。

既定では、すべての**グローバル管理者**に、Azure AD に参加している Surface Hub の管理者権限が与えられます。 **Azure AD Premium** または **Enterprise Mobility Suite (EMS)** では、その他の管理者を追加できます。
1.  [Azure クラシック ポータル](https://manage.windowsazure.com/)で、**[Active Directory]** をクリックし、組織のディレクトリの名前をクリックします。
2.  **[構成]** ページの **[デバイス]** > **[Azure AD 参加済みデバイスの追加の管理者]** で、**[選択済み]** をクリックします。
3.  **[追加]** をクリックし、Surface Hub や他の Azure AD 参加済みデバイスの管理者として追加するユーザーを選択します。
4.  作業が完了したら、チェックマーク ボタンをクリックして変更を保存します。

#### Surface Hub を Azure AD に参加させた場合の動作
Surface Hub を Azure AD に参加させると、次のような処理が可能になります。
- Azure AD テナントの適切なユーザーに管理者権限を付与します。
- デバイスの BitLocker 回復キーを、Azure AD にデバイスを参加させるときに使用したアカウントに保存することによって、BitLocker 回復キーをバックアップします。 詳しくは、「[BitLocker キーの保存](save-bitlocker-key-surface-hub.md)」をご覧ください。

#### Azure Active Directory への参加による自動登録

Surface Hub では、デバイスを Azure Active Directory に参加することで、Intune に自動的に登録する機能がサポートされます。 

詳しくは [、「Windows 10 の自動登録を有効にする」をご覧ください](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)。

#### 選択に関する推奨事項

組織で AD または Azure AD を使用している場合は、主にセキュリティ上の理由から、ドメインまたは Azure AD に参加させることをお勧めします。 ユーザーは、自身の資格情報を使用して、認証を行ったり、設定のロックを解除することができ、ドメインに関連付けられているセキュリティ グループの内外に移動することができます。

| オプション                                            | 要件                            | 設定アプリへのアクセスに使用できる資格情報  |
|---------------------------------------------------|-----------------------------------------|-------|
| ローカル管理者アカウントを作成する                      | なし                                    | 初回実行時に指定したユーザー名とパスワード |
| Active Directory (AD) ドメインに参加させる              | 組織で AD を使用している               | ドメイン内の特定のセキュリティ グループに属する任意の AD ユーザー |
| デバイスを Azure Active Directory (Azure AD) に参加させる | 組織で Azure AD Basic を使用している   | グローバル管理者のみ |
| &nbsp;                                            | 組織でAzure AD Premium または Enterprise Mobility Suite (EMS) を使用している | グローバル管理者と追加の管理者 |


### Azure に参加しているデバイスでグローバル管理者ADアカウントを構成する

Azure AD に参加している Surface Hub 2S デバイスの場合、Windows 10 Team 2020 Update では、Surface Hub 2S の設定アプリの管理に対する管理者権限を制限できます。 これにより、Surface Hub 2S の管理者アクセス許可のみをスコープ設定し、望ましくない可能性のある管理者が Azure AD ドメイン全体にアクセスすることを防止できます。 詳細については [、「Surface Hub 2S でグローバル管理者以外のアカウントを構成する」を参照してください](surface-hub-2s-nonglobal-admin.md)。