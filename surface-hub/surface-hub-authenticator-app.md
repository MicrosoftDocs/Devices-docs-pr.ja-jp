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
# <a name="sign-in-to-surface-hub-with-microsoft-authenticator"></a><span data-ttu-id="8d285-103">Microsoft Authenticator を使った Surface Hub へのサインイン</span><span class="sxs-lookup"><span data-stu-id="8d285-103">Sign in to Surface Hub with Microsoft Authenticator</span></span>

<span data-ttu-id="8d285-104">組織内のユーザーは、Android と iOS で使用できる Microsoft Authenticator アプリを使用して、パスワードを使用せずに Surface Hub にサインインできます。</span><span class="sxs-lookup"><span data-stu-id="8d285-104">People in your organization can sign in to a Surface Hub  without a password using the Microsoft Authenticator app, available on Android and iOS.</span></span>

## <a name="organization-prerequisites"></a><span data-ttu-id="8d285-105">組織の前提条件</span><span class="sxs-lookup"><span data-stu-id="8d285-105">Organization prerequisites</span></span>

<span data-ttu-id="8d285-106">組織内のユーザーがパスワードの代わりにスマートフォンやその他のデバイスを使用して Surface Hub にサインインできるようにするには、組織が以下の前提条件を満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d285-106">To let people in your organization sign in to Surface Hub with their phones and other devices instead of a password, you’ll need to make sure that your organization meets these prerequisites:</span></span> 

- <span data-ttu-id="8d285-107">組織は、Azure Active Directory (Azure AD) によってサポートされる、ハイブリッドまたはクラウドのみの組織である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d285-107">Your organization must be a hybrid or cloud-only organization, backed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="8d285-108">詳しくは、「[Azure Active Directory とは](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d285-108">For more information, see [What is Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)</span></span>

- <span data-ttu-id="8d285-109">Office 365 E3 以上のサブスクリプションがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d285-109">Make sure you have at minimum an Office 365 E3 subscription.</span></span> 

- <span data-ttu-id="8d285-110">[多要素認証を構成します](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings)。</span><span class="sxs-lookup"><span data-stu-id="8d285-110">[Configure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings).</span></span> <span data-ttu-id="8d285-111">**[モバイル アプリによる通知]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d285-111">Make sure **Notification through mobile app** is selected.</span></span> 

    ![多要素認証のオプション](images/mfa-options.png)

- <span data-ttu-id="8d285-113">Azure ADサービス (Office SharePoint など) でコンテンツ ホスティングを有効にする。</span><span class="sxs-lookup"><span data-stu-id="8d285-113">Enable content hosting on Azure AD services such as Office, SharePoint, etc.</span></span> 

- <span data-ttu-id="8d285-114">Surface Hub で Windows 10 バージョン 1703 以降が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d285-114">Surface Hub must be running Windows 10, version 1703 or later.</span></span>

- <span data-ttu-id="8d285-115">Surface Hub は、ローカル アカウントまたはドメインに参加しているアカウントを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="8d285-115">Surface Hub is set up with either a local or domain-joined account.</span></span>

## <a name="individual-prerequisites"></a><span data-ttu-id="8d285-116">個々の前提条件</span><span class="sxs-lookup"><span data-stu-id="8d285-116">Individual prerequisites</span></span>

- <span data-ttu-id="8d285-117">Android 6.0 以降を実行する Android フォンまたは iOS9 以降を実行する iPhone や iPad。</span><span class="sxs-lookup"><span data-stu-id="8d285-117">An Android phone running 6.0 or later, or an iPhone or iPad running iOS9 or later</span></span> 

- <span data-ttu-id="8d285-118">適切なアプリ ストアから入手した最新バージョンの Microsoft Authenticator アプリ。</span><span class="sxs-lookup"><span data-stu-id="8d285-118">The most recent version of the Microsoft Authenticator app from the appropriate app store</span></span>

    >[!NOTE]
    ><span data-ttu-id="8d285-119">iOS では、アプリのバージョンは 5.4.0 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d285-119">On iOS, the app version must be 5.4.0 or higher.</span></span>
    >
    ><span data-ttu-id="8d285-120">Windows オペレーティング システムを実行するスマートフォンでは、Microsoft Authenticator アプリを使用して Surface Hub にサインインすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8d285-120">The Microsoft Authenticator app on phones running a Windows operating system can't be used to sign in to Surface Hub.</span></span>

- <span data-ttu-id="8d285-121">デバイスでパスコードや画面のロックが有効になっていること。</span><span class="sxs-lookup"><span data-stu-id="8d285-121">Passcode or screen lock on your device is enabled</span></span>

## <a name="how-to-set-up-the-microsoft-authenticator-app"></a><span data-ttu-id="8d285-122">Microsoft Authenticator アプリの使い方</span><span class="sxs-lookup"><span data-stu-id="8d285-122">How to set up the Microsoft Authenticator app</span></span>

>[!NOTE]
><span data-ttu-id="8d285-123">Android デバイスにポータル サイトがインストールされている場合は、Microsoft Authenticator をセットアップする前にアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="8d285-123">If Company Portal is installed on your Android device, uninstall it before you set up Microsoft Authenticator.</span></span> <span data-ttu-id="8d285-124">アプリをセットアップした後、ポータル サイトを再インストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="8d285-124">After you set up the app, you can reinstall Company Portal.</span></span>
>
><span data-ttu-id="8d285-125">スマートフォンで Microsoft Authenticator を既にセットアップし、デバイスを登録している場合は、サインインの手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="8d285-125">If you have already set up Microsoft Authenticator on your phone and registered your device, go to the sign-in instructions.</span></span>

1. <span data-ttu-id="8d285-126">多要素認証の Microsoft Authenticator に職場または学校アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d285-126">Add your work or school account to Microsoft Authenticator for Multi-Factor Authentication.</span></span> <span data-ttu-id="8d285-127">IT 部門によって提供される QR コードが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d285-127">You will need a QR code provided by your IT department.</span></span> <span data-ttu-id="8d285-128">ヘルプについては、「[Microsoft Authenticator アプリの概要](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d285-128">For help, see [Get started with the Microsoft Authenticator app](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).</span></span>
2. <span data-ttu-id="8d285-129">**設定**に移動し、デバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="8d285-129">Go to **Settings** and register your device.</span></span>
3. <span data-ttu-id="8d285-130">アカウント ページに戻り、アカウントのドロップダウン メニューから **[電話によるサインインを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d285-130">Return to the accounts page and choose **Enable phone sign-in** from the account dropdown menu.</span></span>

## <a name="how-to-sign-in-to-surface-hub-during-a-meeting"></a><span data-ttu-id="8d285-131">会議中に Surface Hub にサインインする方法</span><span class="sxs-lookup"><span data-stu-id="8d285-131">How to sign in to Surface Hub during a meeting</span></span>

1. <span data-ttu-id="8d285-132">会議をセットアップした後、Surface Hub に移動し、**[サインインしてミーティングとファイルを参照する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d285-132">After you’ve set up a meeting, go to the Surface Hub and select **Sign in to see your meetings and files**.</span></span>

    >[!NOTE]
    ><span data-ttu-id="8d285-133">Surface Hub で会議をスケジュールする方法がわからない場合は、「[Surface Hub のスケジュール](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d285-133">If you’re not sure how to schedule a meeting on a Surface Hub, see [Schedule a meeting on Surface Hub](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting).</span></span>

    ![Surface Hub でのサインイン オプションのスクリーンショット](images/sign-in.png)

2. <span data-ttu-id="8d285-135">会議に招待されているユーザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d285-135">You’ll see a list of the people invited to the meeting.</span></span> <span data-ttu-id="8d285-136">自分自身 (またはサインインさせたいユーザー。会議の前に、このユーザーがデバイスをセットアップする手順を実行済みであることを確認します) を選択し、**[続行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d285-136">Select yourself (or the person who wants to sign in – make sure this person has gone through the steps to set up their device before your meeting), and then select **Continue**.</span></span>

    ![会議の出席者の一覧のスクリーンショット](images/attendees.png)

    <span data-ttu-id="8d285-138">Surface Hub にコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d285-138">You'll see a code on the Surface Hub.</span></span>

    ![サインインを承認するためのコードのスクリーンショット](images/approve-signin.png)

3. <span data-ttu-id="8d285-140">サインインを承認するには、Authenticator アプリを開き、Surface Hub に表示される 4 桁のコードを入力し、**[承認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d285-140">To approve the sign-in, open the Authenticator app, enter the four-digit code that’s displayed on the Surface Hub, and select **Approve**.</span></span> <span data-ttu-id="8d285-141">サインインを完了するために、PIN の入力または指紋認証を求められます。</span><span class="sxs-lookup"><span data-stu-id="8d285-141">You will then be asked to enter the PIN or use your fingerprint to complete the sign in.</span></span> 

    ![Microsoft Authenticator のサインインの承認画面のスクリーンショット](images/approve-signin2.png)

<span data-ttu-id="8d285-143">これで、OneDrive アプリを使用してすべてのファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8d285-143">You can now access all files through the OneDrive app.</span></span>
