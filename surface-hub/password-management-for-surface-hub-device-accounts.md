---
title: パスワード管理 (Surface Hub)
description: すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。
ms.assetid: 0FBFB546-05F0-430E-905E-87111046E4B8
ms.reviewer: ''
manager: laurawi
keywords: パスワード, パスワードの管理, パスワードの循環, デバイス アカウント
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: bef626fce875d5074f3ed47ed957e821beec7c77
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836678"
---
# <span data-ttu-id="c97b2-104">パスワード管理 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="c97b2-104">Password management (Surface Hub)</span></span>

<span data-ttu-id="c97b2-105">すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="c97b2-105">Every Microsoft Surface Hub device account requires a password to authenticate and enable features on the device.</span></span> <span data-ttu-id="c97b2-106">セキュリティ上の理由から、このパスワードを定期的に変更 (または "循環") することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c97b2-106">For security reasons, you may want to change (or "rotate") this password regularly.</span></span> <span data-ttu-id="c97b2-107">ただし、デバイス アカウントのパスワードを変更すると、以前に Surface Hub に保存されたパスワードは無効になり、デバイス アカウントを利用するすべての機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-107">However, if the device account’s password changes, the password that was previously stored on the Surface Hub will be invalid, and all features that depend on the device account will be disabled.</span></span> <span data-ttu-id="c97b2-108">設定アプリで Surface Hub のデバイス アカウントのパスワードを更新して、これらの機能をもう一度有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-108">You will need to update the device account’s password on the Surface Hub from the Settings app to re-enable these features.</span></span>

<span data-ttu-id="c97b2-109">Surface Hub デバイス アカウントのパスワードの管理を簡略化するために、次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-109">To simplify password management for your Surface Hub device accounts, there are two options:</span></span>

1.  <span data-ttu-id="c97b2-110">デバイス アカウントのパスワードの有効期限をオフにする。</span><span class="sxs-lookup"><span data-stu-id="c97b2-110">Turn off password expiration for the device account.</span></span>
2.  <span data-ttu-id="c97b2-111">Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする。</span><span class="sxs-lookup"><span data-stu-id="c97b2-111">Allow the Surface Hub to automatically rotate the device account’s password.</span></span>


## <span data-ttu-id="c97b2-112">デバイス アカウントのパスワードの循環をオフにする</span><span class="sxs-lookup"><span data-stu-id="c97b2-112">Turn off password rotation for the device account</span></span>

<span data-ttu-id="c97b2-113">デバイス アカウントの **PasswordNeverExpires** プロパティを True に設定します。</span><span class="sxs-lookup"><span data-stu-id="c97b2-113">Set the device account’s **PasswordNeverExpires** property to True.</span></span> <span data-ttu-id="c97b2-114">この設定が組織のセキュリティ要件を満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-114">You should verify whether this meets your organization’s security requirements.</span></span>


## <span data-ttu-id="c97b2-115">Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする</span><span class="sxs-lookup"><span data-stu-id="c97b2-115">Allow the Surface Hub to automatically rotate the device account’s password</span></span>

<span data-ttu-id="c97b2-116">Surface Hub では、デバイス アカウントの情報を手動で更新しなくても、デバイス アカウントのパスワードを頻繁に変更して管理できます。</span><span class="sxs-lookup"><span data-stu-id="c97b2-116">The Surface Hub can manage a device account’s password by changing it frequently without requiring you to manually update the device account’s information.</span></span> <span data-ttu-id="c97b2-117">この機能は、**[設定]** で有効にできます。</span><span class="sxs-lookup"><span data-stu-id="c97b2-117">You can enable this feature in **Settings**.</span></span> <span data-ttu-id="c97b2-118">有効にすると、デバイス アカウントのパスワードは、週ごとにメンテナンス時間に変更されます。</span><span class="sxs-lookup"><span data-stu-id="c97b2-118">Once enabled, the device account's password will change weekly during maintenance hours.</span></span>

<span data-ttu-id="c97b2-119">デバイス アカウントのパスワードが変更されても、新しいパスワードは表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c97b2-119">Note that when the device account’s password is changed, you will not be shown the new password.</span></span> <span data-ttu-id="c97b2-120">アカウントにサインインする場合や、もう一度パスワードを入力する場合は (たとえば、Surface Hub でのデバイス アカウントの設定を変更する場合)、Active Directory または Office 365 管理ポータルを使ってパスワードをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-120">If you need to sign in to the account, or to provide the password again (for example, if you want to change the device account settings on the Surface Hub), then you'll need use Active Directory or the Office 365 admin portal to reset the password.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c97b2-121">組織でハイブリッド トポロジを使っている場合は (オンプロミスでホストされているサービスと、Office 365 を介してオンラインでホストされているサービスが混在します)、デバイス アカウントを**ドメイン\ユーザー名**形式で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c97b2-121">If your organization uses a hybrid topology (some services are hosted on-premises and some are hosted online through Office 365), you must setup the device account in **domain\username** format.</span></span> <span data-ttu-id="c97b2-122">そうしないと、パスワードの循環が機能しません。</span><span class="sxs-lookup"><span data-stu-id="c97b2-122">Otherwise, password rotation will not work.</span></span>
