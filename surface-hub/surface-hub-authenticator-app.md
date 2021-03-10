---
title: Microsoft Authenticator を使った Surface Hub へのサインイン
description: モバイル デバイスで Microsoft Authenticator を使用して、Surface Hub にログインします。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/28/2017
ms.reviewer: ''
manager: laurawi
localizationpriority: medium
ms.openlocfilehash: f8a2bf8ddb75ca6dd3ff89e16fe0d37e099be29d
ms.sourcegitcommit: 85f5a2e67b34fe073ec588ed441ebee239ab0ac6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "11400738"
---
# <a name="sign-in-to-surface-hub-with-microsoft-authenticator"></a>Microsoft Authenticator を使った Surface Hub へのサインイン

組織内のユーザーは、Android と iOS で使用できる Microsoft Authenticator アプリを使用して、パスワードを使用せずに Surface Hub にサインインできます。

## <a name="organization-prerequisites"></a>組織の前提条件

組織内のユーザーがパスワードの代わりにスマートフォンやその他のデバイスを使用して Surface Hub にサインインできるようにするには、組織が以下の前提条件を満たしていることを確認する必要があります。 

- 組織は、Azure Active Directory (Azure AD) によってサポートされる、ハイブリッドまたはクラウドのみの組織である必要があります。 詳しくは、「[Azure Active Directory とは](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)」をご覧ください。

- Office 365 E3 以上のサブスクリプションがあることを確認します。 

- [多要素認証を構成します](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings)。 **[モバイル アプリによる通知]** が選択されていることを確認します。 

    ![多要素認証のオプション](images/mfa-options.png)

- Azure ADサービス (Office SharePoint など) でコンテンツ ホスティングを有効にする。 

- Surface Hub で Windows 10 バージョン 1703 以降が実行されている必要があります。

- Surface Hub は、ローカル アカウントまたはドメインに参加しているアカウントを使用して設定します。

## <a name="individual-prerequisites"></a>個々の前提条件

- Android 6.0 以降を実行する Android フォンまたは iOS9 以降を実行する iPhone や iPad。 

- 適切なアプリ ストアから入手した最新バージョンの Microsoft Authenticator アプリ。

    >[!NOTE]
    >iOS では、アプリのバージョンは 5.4.0 以上である必要があります。
    >
    >Windows オペレーティング システムを実行するスマートフォンでは、Microsoft Authenticator アプリを使用して Surface Hub にサインインすることはできません。

- デバイスでパスコードや画面のロックが有効になっていること。

## <a name="how-to-set-up-the-microsoft-authenticator-app"></a>Microsoft Authenticator アプリの使い方

>[!NOTE]
>Android デバイスにポータル サイトがインストールされている場合は、Microsoft Authenticator をセットアップする前にアンインストールします。 アプリをセットアップした後、ポータル サイトを再インストールすることができます。
>
>スマートフォンで Microsoft Authenticator を既にセットアップし、デバイスを登録している場合は、サインインの手順に進みます。

1. 多要素認証の Microsoft Authenticator に職場または学校アカウントを追加します。 IT 部門によって提供される QR コードが必要です。 ヘルプについては、「[Microsoft Authenticator アプリの概要](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)」をご覧ください。
2. **設定**に移動し、デバイスを登録します。
3. アカウント ページに戻り、アカウントのドロップダウン メニューから **[電話によるサインインを有効にする]** を選択します。

## <a name="how-to-sign-in-to-surface-hub-during-a-meeting"></a>会議中に Surface Hub にサインインする方法

1. 会議をセットアップした後、Surface Hub に移動し、**[サインインしてミーティングとファイルを参照する]** を選択します。

    >[!NOTE]
    >Surface Hub で会議をスケジュールする方法がわからない場合は、「[Surface Hub のスケジュール](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting)」を参照してください。

    ![Surface Hub でのサインイン オプションのスクリーンショット](images/sign-in.png)

2. 会議に招待されているユーザーの一覧が表示されます。 自分自身 (またはサインインさせたいユーザー。会議の前に、このユーザーがデバイスをセットアップする手順を実行済みであることを確認します) を選択し、**[続行]** を選択します。

    ![会議の出席者の一覧のスクリーンショット](images/attendees.png)

    Surface Hub にコードが表示されます。

    ![サインインを承認するためのコードのスクリーンショット](images/approve-signin.png)

3. サインインを承認するには、Authenticator アプリを開き、Surface Hub に表示される 4 桁のコードを入力し、**[承認]** を選択します。 サインインを完了するために、PIN の入力または指紋認証を求められます。 

    ![Microsoft Authenticator のサインインの承認画面のスクリーンショット](images/approve-signin2.png)

これで、OneDrive アプリを使用してすべてのファイルにアクセスできます。
