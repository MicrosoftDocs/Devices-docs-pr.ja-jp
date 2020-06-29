---
title: Surface Hub 2S のパスワードを使用しない電話のサインインを構成する
description: モバイルデバイスでパスワードを使用しないパスワードを使用して、Surface Hub 2S へのサインインを簡素化する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 95873e41588a6f07ece53fd04f7d63bf56143914
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835366"
---
# <span data-ttu-id="fa9a0-104">Surface Hub 2S のパスワードを使用しない電話のサインインを構成する</span><span class="sxs-lookup"><span data-stu-id="fa9a0-104">Configure password-less phone sign-in  for Surface Hub 2S</span></span>

<span data-ttu-id="fa9a0-105">パスワードを使用しないパスワードを使用すると、会議へのサインインが簡単になり、Surface Hub 2S のファイルにも参加できます。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-105">Password-less phone sign-in simplifies signing-in to your meetings and files on Surface Hub 2S.</span></span>

> [!NOTE]
> <span data-ttu-id="fa9a0-106">パスワードを使用しない場合は、プライマリメールアドレスが UPN と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-106">Password-less phone sign-in requires that your primary email address must match your UPN.</span></span>

## <span data-ttu-id="fa9a0-107">パスワードを設定しないようにするには</span><span class="sxs-lookup"><span data-stu-id="fa9a0-107">To set up password-less phone sign-in</span></span>

1. <span data-ttu-id="fa9a0-108">IPhone または Android 用の[Microsoft Authenticator](https://www.microsoft.com/account/authenticator)アプリを携帯電話にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-108">Download the [Microsoft Authenticator](https://www.microsoft.com/account/authenticator) app for iPhone or Android to your phone.</span></span>
2. <span data-ttu-id="fa9a0-109">PC で、にアクセスし [https://aka.ms/MFASetup](https://aka.ms/MFASetup) て、アカウントでサインインし、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-109">From your PC, go to [https://aka.ms/MFASetup](https://aka.ms/MFASetup) , sign in with your account, and select **Next.**</span></span>
3. <span data-ttu-id="fa9a0-110">[追加のセキュリティ検証] 画面で、[モバイルアプリ] を選択し、確認コードを使用して、[**セットアップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-110">In the Additional security verification screen, select Mobile App and Use verification code, and then select **Setup**.</span></span>

## <span data-ttu-id="fa9a0-111">モバイルアプリを構成するには</span><span class="sxs-lookup"><span data-stu-id="fa9a0-111">To configure mobile app</span></span>

1. <span data-ttu-id="fa9a0-112">電話の Microsoft authenticator アプリで、アカウントを追加し、[**職場または学校アカウント**] を選択して、PC に表示される QR コードをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-112">In the Microsoft authenticator app on your phone, add an account, choose **Work or School Account**, and then scan the QR code displayed on your PC</span></span>
2. <span data-ttu-id="fa9a0-113">電話に通知を送信し、サインイン要求を承認します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-113">Send a notification to your phone and then approve the sign-in request.</span></span>
3. <span data-ttu-id="fa9a0-114">スマートフォンの認証アプリで、アカウントの横にあるドロップダウンメニューを使用して、[**電話でのサインインを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-114">In the Authenticator app on your phone, use the drop-down menu next to your account and select **Enable phone sign-in**.</span></span>
4. <span data-ttu-id="fa9a0-115">必要に応じて、デバイスを組織に登録し、画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-115">If required, register your device with your organization and follow the on-screen instructions.</span></span>

## <span data-ttu-id="fa9a0-116">Surface Hub にサインインするには</span><span class="sxs-lookup"><span data-stu-id="fa9a0-116">To sign in to Surface Hub</span></span>

1. <span data-ttu-id="fa9a0-117">Surface Hub で、 **[自分の会議] と [ファイル**] にサインインし、メッセージが表示されたら [**通知の送信**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-117">On Surface Hub, sign into **My meetings and files** and select **Send notification** when prompted.</span></span>
2. <span data-ttu-id="fa9a0-118">サインイン要求を承認するために、携帯電話に表示される番号と Surface Hub に表示される番号を一致させます。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-118">Match the number displayed on your phone with the number displayed on Surface Hub to approve your sign-in request.</span></span>
3. <span data-ttu-id="fa9a0-119">メッセージが表示されたら、電話の PIN または生体認証 ID を入力して、サインインを完了します。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-119">If prompted, enter the PIN or biometric ID on your phone to complete sign-in.</span></span>

## <span data-ttu-id="fa9a0-120">詳細情報</span><span class="sxs-lookup"><span data-stu-id="fa9a0-120">Learn more</span></span>
<span data-ttu-id="fa9a0-121">詳細については、「 [Microsoft Authenticator アプリでのパスワードを使用しない電話でのサインイン](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-phone-sign-in)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9a0-121">For more information, see [Password-less phone sign-in with the Microsoft Authenticator app](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-phone-sign-in).</span></span>
