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
# <span data-ttu-id="afaf3-104">Surface Hub での passwordless サインインの構成</span><span class="sxs-lookup"><span data-stu-id="afaf3-104">Configure passwordless sign-in on Surface Hub</span></span>

 
<span data-ttu-id="afaf3-105">パスワードを使用しないサインインでは、アプリ、会議、ファイルへのアクセスが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="afaf3-105">Passwordless sign-in simplifies access to your apps, meetings, and files.</span></span> <span data-ttu-id="afaf3-106">Surface Hub は、組織が提供する Microsoft Authenticator アプリと FIDO2 セキュリティキーを使用したサインインをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="afaf3-106">Surface Hub supports signing in using the Microsoft Authenticator app and FIDO2 security keys provided by your organization.</span></span>

<span data-ttu-id="afaf3-107">**重要:** このコンテンツは、ユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="afaf3-107">**Important:** This content is intended for users.</span></span> <span data-ttu-id="afaf3-108">パスワードのないサインインを使用するには、IT 管理者が組織に対してパスワードを使用しない認証を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="afaf3-108">To use passwordless sign-in, your IT admin must enable passwordless authentication for your organization.</span></span> <span data-ttu-id="afaf3-109">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afaf3-109">For more information, see:</span></span>

- [<span data-ttu-id="afaf3-110">パスワードを有効にする電話サインインを有効にする</span><span class="sxs-lookup"><span data-stu-id="afaf3-110">Enable passwordless phone sign-in</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [<span data-ttu-id="afaf3-111">パスワードを使用したセキュリティキーのサインインを有効にする</span><span class="sxs-lookup"><span data-stu-id="afaf3-111">Enable passwordless security key sign-in</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


## <span data-ttu-id="afaf3-112">Microsoft Authenticator アプリを使用してサインインを構成する</span><span class="sxs-lookup"><span data-stu-id="afaf3-112">Configure sign-in using Microsoft Authenticator app</span></span>

<span data-ttu-id="afaf3-113">**注:** Windows 10 Team 2020 更新プログラム以降では、ユーザーは Azure AD で優先メールエイリアスを使用し、ユーザープリンシパル名 (UPN) を使って Microsoft Authenticator を使ってサインインすることができます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-113">**Note:** Starting with Windows 10 Team 2020 Update, users can use their preferred email aliases in Azure AD, as well as their User Principal Name (UPN), to sign in using Microsoft Authenticator.</span></span> <span data-ttu-id="afaf3-114">たとえば、ユーザーは自分の優先エイリアス (John.Doe@contoso.com) またはその UPN (jdoe@contoso.com) を使ってサインインすることができます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-114">For example, a user can use either their preferred alias (John.Doe@contoso.com) or their UPN (jdoe@contoso.com) to sign in.</span></span>
 
<span data-ttu-id="afaf3-115">Microsoft Authenticator アプリを使用すると、モバイルデバイスを使って Surface Hub にサインインすることができます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-115">The Microsoft Authenticator app helps you sign-in to Surface Hub using your mobile device.</span></span> <span data-ttu-id="afaf3-116">Microsoft Authenticator を使用してサインインを構成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="afaf3-116">To configure sign-in using Microsoft Authenticator:</span></span>


1. <span data-ttu-id="afaf3-117">モバイルデバイスで、Microsoft Authenticator アプリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="afaf3-117">On your mobile device, download the Microsoft Authenticator app.</span></span>
    - <span data-ttu-id="afaf3-118">Google Android: Android デバイスで、Google Play にアクセスして[、Microsoft Authenticator アプリをダウンロードしてインストール](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator)します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-118">Google Android: On your Android device, go to Google Play to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).</span></span>
    - <span data-ttu-id="afaf3-119">Apple iOS: Apple iOS デバイスでは、App Store にアクセスして、 [Microsoft Authenticator アプリをダウンロードしてインストール](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458)します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-119">Apple iOS: On your Apple iOS device, go to the App Store to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).</span></span>
2. <span data-ttu-id="afaf3-120">PC で、職場または学校のアカウントの [[セキュリティ情報] ページから Microsoft Authenticator アプリをセットアップ](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page)します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-120">On your PC, [setup the Microsoft Authenticator app from the Security info page](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) for your work or school account.</span></span>
3. <span data-ttu-id="afaf3-121">モバイルデバイスの Microsoft Authenticator アプリで、職場または学校のアカウントの[電話サインインを有効にして使用](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account)します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-121">From the Microsoft Authenticator app on your mobile device, [turn on and use phone sign-in](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) for your work or school account.</span></span>

 
## <span data-ttu-id="afaf3-122">FIDO2 セキュリティキーを使用してサインインを構成する</span><span class="sxs-lookup"><span data-stu-id="afaf3-122">Configure sign-in using FIDO2 security keys</span></span>

> [!NOTE]
>  <span data-ttu-id="afaf3-123">FIDO2 のセキュリティキーを使用した、Surface Hub での passwordless サインインには、Windows 10 Team 2020 更新プログラムが必要です。</span><span class="sxs-lookup"><span data-stu-id="afaf3-123">Passwordless sign-in on Surface Hub using FIDO2 security keys requires the Windows 10 Team 2020 Update.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afaf3-124">Surface Hub は、USB セキュリティキーのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="afaf3-124">Surface Hub only supports USB security keys.</span></span>
 
<span data-ttu-id="afaf3-125">組織から提供された FIDO2 セキュリティキーを使用して、Surface Hub にサインインすることもできます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-125">You can also sign into Surface Hub using a FIDO2 security key provided by your organization.</span></span> 

### <span data-ttu-id="afaf3-126">セキュリティキーを使用してサインインを構成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="afaf3-126">To configure sign-in using a security key:</span></span>


1. <span data-ttu-id="afaf3-127">PC で、ページにアクセス [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) し、職場または学校のアカウントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="afaf3-127">On your PC, go to your [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) page and sign in to your work or school account.</span></span>
2. <span data-ttu-id="afaf3-128">左側のナビゲーションウィンドウから、または**セキュリティ**情報ブロックのリンクから [**セキュリティ情報**] を選び、[**セキュリティ情報**] ページから [**メソッドの追加**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-128">Select **Security info** from the left navigation pane or from the link in the **Security info** block, and then select **Add method** from the **Security info** page.</span></span>
3. <span data-ttu-id="afaf3-129">[**メソッドの追加**] ページで、ドロップダウンリストから [**セキュリティキー** ] を選択し、[**追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-129">On the **Add a method** page, select **Security key** from the drop-down list, and then select **Add**.</span></span>
4. <span data-ttu-id="afaf3-130">[**セキュリティキー** ] ページで、[ **USB デバイス**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-130">On the **Security key** page, choose **USB device**.</span></span>
5. <span data-ttu-id="afaf3-131">セキュリティキーを用意して、[**次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-131">Have your security key ready and select **Next**.</span></span>
6. <span data-ttu-id="afaf3-132">ダイアログボックスが表示されたら、指示に従ってセキュリティキーを挿入するか、PIN を作成または入力して、必要なジェスチャ (生体認証またはタッチ) を実行します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-132">In the dialog box that appears, follow the instructions to insert the security key, create or enter a PIN, and perform the required gesture (either biometric or touch).</span></span>
7. <span data-ttu-id="afaf3-133">[**セキュリティキー** ] ページで、セキュリティキーの名前を入力し、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-133">On the **Security key** page, give your security key a name, then select **Next**.</span></span>
8. <span data-ttu-id="afaf3-134">[**完了**] を選択して処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="afaf3-134">Select **Done** to complete the process.</span></span>

## <span data-ttu-id="afaf3-135">Surface Hub にサインインする</span><span class="sxs-lookup"><span data-stu-id="afaf3-135">Sign-in to Surface Hub</span></span>

<span data-ttu-id="afaf3-136">パスワードが少なくなったサインインを設定すると、Surface Hub 上のアプリ、会議、ファイルに簡単にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="afaf3-136">Once you've configured passwordless sign-in, you can use it to make it easier to access your apps, meetings, and files on the Surface Hub:</span></span>

- <span data-ttu-id="afaf3-137">会議にすばやく参加し、最近の Microsoft 365 ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-137">Quickly join your meetings and open recent Microsoft 365 files.</span></span> <span data-ttu-id="afaf3-138">詳細については、「サインインして[**会議やファイルを表示する**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afaf3-138">For more information, see [**Sign in to see your meetings and files**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub).</span></span>
- <span data-ttu-id="afaf3-139">ホワイトボード、PowerPoint、Word、Excel、OneDrive、Power BI などの Microsoft アプリにすばやくサインインします。</span><span class="sxs-lookup"><span data-stu-id="afaf3-139">Quickly sign in to Microsoft apps like Whiteboard, PowerPoint, Word, Excel, OneDrive, and Power BI.</span></span>
- <span data-ttu-id="afaf3-140">新しい Microsoft Edge にサインインすると、お気に入りと参照設定にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-140">Quickly sign in to the new Microsoft Edge to access your favorites and browsing preferences.</span></span> <span data-ttu-id="afaf3-141">詳細については、「[新しい Microsoft Edge をインストールして構成する](surface-hub-install-chromium-edge.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afaf3-141">For more information, see [Install and configure the new Microsoft Edge](surface-hub-install-chromium-edge.md).</span></span>
- <span data-ttu-id="afaf3-142">Surface Hub にサインインした後は、[**終了セッション**] を選択するまで、もう一度サインインしなくても、他のアプリを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-142">Once you've signed into Surface Hub, you can use other apps without having to sign in again until you select **End session**.</span></span> <span data-ttu-id="afaf3-143">[**終了セッション**] を選ぶと、資格情報、ファイル、個人データがデバイスから削除されます。</span><span class="sxs-lookup"><span data-stu-id="afaf3-143">Selecting **End session** deletes your credentials, files, and personal data from the device.</span></span> <span data-ttu-id="afaf3-144">詳細については、「[セッションを終了](finishing-your-surface-hub-meeting.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afaf3-144">For more information, see [End session](finishing-your-surface-hub-meeting.md).</span></span>


## <span data-ttu-id="afaf3-145">詳細情報</span><span class="sxs-lookup"><span data-stu-id="afaf3-145">Learn more</span></span>

- [<span data-ttu-id="afaf3-146">Azure Active Directory の passwordless 認証オプション</span><span class="sxs-lookup"><span data-stu-id="afaf3-146">Passwordless authentication options for Azure Active Directory</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)
- [<span data-ttu-id="afaf3-147">Microsoft Authenticator アプリを使用した passwordless サインイン</span><span class="sxs-lookup"><span data-stu-id="afaf3-147">Passwordless sign-in with the Microsoft Authenticator app</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [<span data-ttu-id="afaf3-148">FIDO2 セキュリティキーを使用した passwordless サインイン</span><span class="sxs-lookup"><span data-stu-id="afaf3-148">Passwordless sign-in using FIDO2 security keys</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)

