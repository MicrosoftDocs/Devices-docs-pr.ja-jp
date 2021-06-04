---
title: Surface Hub でのパスワードをあまり持たないサインインを構成する
description: Surface Hub へのサインインを簡素化する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/21/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 0eaa48200be9ff3c8087530b6dfddeb9aa4620d8
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893049"
---
# Surface Hub での passwordless サインインの構成

 
パスワードを使用しないサインインでは、アプリ、会議、ファイルへのアクセスが簡単になります。 Surface Hub は、組織が提供する Microsoft Authenticator アプリと FIDO2 セキュリティキーを使用したサインインをサポートしています。

**重要:** このコンテンツは、ユーザーを対象としています。 パスワードのないサインインを使用するには、IT 管理者が組織に対してパスワードを使用しない認証を有効にする必要があります。 詳細については、以下を参照してください。

- [パスワードを有効にする電話サインインを有効にする](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [パスワードを使用したセキュリティキーのサインインを有効にする](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


##  <a name="configure-sign-in-using-microsoft-authenticator-app"></a>Microsoft Authenticator アプリを使用してサインインを構成する

**注:** Windows 10 Team 2020 更新プログラム以降では、ユーザーは Azure AD で優先メールエイリアスを使用し、ユーザープリンシパル名 (UPN) を使って Microsoft Authenticator を使ってサインインすることができます。 たとえば、ユーザーは自分の優先エイリアス (John.Doe@contoso.com) またはその UPN (jdoe@contoso.com) を使ってサインインすることができます。
 
Microsoft Authenticator アプリを使用すると、モバイルデバイスを使って Surface Hub にサインインすることができます。 Microsoft Authenticator を使用してサインインを構成するには、次の操作を行います。


1. モバイルデバイスで、Microsoft Authenticator アプリをダウンロードします。
    - Google Android: Android デバイスで、Google Play にアクセスして[、Microsoft Authenticator アプリをダウンロードしてインストール](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator)します。
    - Apple iOS: Apple iOS デバイスでは、App Store にアクセスして、 [Microsoft Authenticator アプリをダウンロードしてインストール](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458)します。
2. PC で、職場または学校のアカウントの [[セキュリティ情報] ページから Microsoft Authenticator アプリをセットアップ](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page)します。
3. モバイルデバイスの Microsoft Authenticator アプリで、職場または学校のアカウントの[電話サインインを有効にして使用](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account)します。

 
##  <a name="configure-sign-in-using-fido2-security-keys"></a>FIDO2 セキュリティキーを使用してサインインを構成する

> [!NOTE]
>  FIDO2 のセキュリティキーを使用した、Surface Hub での passwordless サインインには、Windows 10 Team 2020 更新プログラムが必要です。

> [!IMPORTANT]
> Surface Hub は、USB セキュリティキーのみをサポートしています。
 
組織から提供された FIDO2 セキュリティキーを使用して、Surface Hub にサインインすることもできます。 

###  <a name="to-configure-sign-in-using-a-security-key"></a>セキュリティキーを使用してサインインを構成するには、次の操作を行います。


1. PC で、ページにアクセス [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) し、職場または学校のアカウントにサインインします。
2. 左側のナビゲーションウィンドウから、または**セキュリティ**情報ブロックのリンクから [**セキュリティ情報**] を選び、[**セキュリティ情報**] ページから [**メソッドの追加**] を選びます。
3. [**メソッドの追加**] ページで、ドロップダウンリストから [**セキュリティキー** ] を選択し、[**追加**] を選択します。
4. [**セキュリティキー** ] ページで、[ **USB デバイス**] を選びます。
5. セキュリティキーを用意して、[**次へ**] を選びます。
6. ダイアログボックスが表示されたら、指示に従ってセキュリティキーを挿入するか、PIN を作成または入力して、必要なジェスチャ (生体認証またはタッチ) を実行します。
7. [**セキュリティキー** ] ページで、セキュリティキーの名前を入力し、[**次へ**] を選択します。
8. [**完了**] を選択して処理を完了します。

##  <a name="sign-in-to-surface-hub"></a>Surface Hub にサインインする

パスワードが少なくなったサインインを設定すると、Surface Hub 上のアプリ、会議、ファイルに簡単にアクセスできるようになります。

- 会議にすばやく参加し、最近の Microsoft 365 ファイルを開きます。 詳細については、「サインインして[**会議やファイルを表示する**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub)」を参照してください。
- ホワイトボード、PowerPoint、Word、Excel、OneDrive、Power BI などの Microsoft アプリにすばやくサインインします。
- 新しい Microsoft Edge にサインインすると、お気に入りと参照設定にアクセスできます。 詳細については、「[新しい Microsoft Edge をインストールして構成する](surface-hub-install-chromium-edge.md)」を参照してください。
- Surface Hub にサインインした後は、[**終了セッション**] を選択するまで、もう一度サインインしなくても、他のアプリを使うことができます。 [**終了セッション**] を選ぶと、資格情報、ファイル、個人データがデバイスから削除されます。 詳細については、「[セッションを終了](finishing-your-surface-hub-meeting.md)する」を参照してください。


##  <a name="learn-more"></a>詳細情報

- [Azure Active Directory の passwordless 認証オプション](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)
- [Microsoft Authenticator アプリを使用した passwordless サインイン](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [FIDO2 セキュリティキーを使用した passwordless サインイン](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)

