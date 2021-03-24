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
ms.openlocfilehash: 215736527121306c712932f57a5a3a853fb3bb20
ms.sourcegitcommit: 366eedceb9f859f5e87ba032b161f248360cb895
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "11445583"
---
# <a name="password-management-surface-hub"></a><span data-ttu-id="0d353-104">パスワード管理 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="0d353-104">Password management (Surface Hub)</span></span>

<span data-ttu-id="0d353-105">すべての Microsoft Surface Hub デバイス アカウントには、認証を受けてデバイスの機能を有効にするためのパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="0d353-105">Every Microsoft Surface Hub device account requires a password to authenticate and enable features on the device.</span></span> <span data-ttu-id="0d353-106">セキュリティ上の理由から、このパスワードを定期的に変更 (または "循環") することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0d353-106">For security reasons, you may want to change (or "rotate") this password regularly.</span></span> <span data-ttu-id="0d353-107">ただし、デバイス アカウントのパスワードを変更すると、以前に Surface Hub に保存されたパスワードは無効になり、デバイス アカウントを利用するすべての機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="0d353-107">However, if the device account’s password changes, the password that was previously stored on the Surface Hub will be invalid, and all features that depend on the device account will be disabled.</span></span> <span data-ttu-id="0d353-108">設定アプリで Surface Hub のデバイス アカウントのパスワードを更新して、これらの機能をもう一度有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d353-108">You will need to update the device account’s password on the Surface Hub from the Settings app to re-enable these features.</span></span>

<span data-ttu-id="0d353-109">Surface Hub デバイス アカウントのパスワードの管理を簡略化するために、次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="0d353-109">To simplify password management for your Surface Hub device accounts, there are two options:</span></span>

1.  <span data-ttu-id="0d353-110">デバイス アカウントのパスワードの有効期限をオフにする。</span><span class="sxs-lookup"><span data-stu-id="0d353-110">Turn off password expiration for the device account.</span></span>
2.  <span data-ttu-id="0d353-111">Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする。</span><span class="sxs-lookup"><span data-stu-id="0d353-111">Allow the Surface Hub to automatically rotate the device account’s password.</span></span>


## <a name="turn-off-password-rotation-for-the-device-account"></a><span data-ttu-id="0d353-112">デバイス アカウントのパスワードの循環をオフにする</span><span class="sxs-lookup"><span data-stu-id="0d353-112">Turn off password rotation for the device account</span></span>

<span data-ttu-id="0d353-113">デバイス アカウントの **PasswordNeverExpires** プロパティを True に設定します。</span><span class="sxs-lookup"><span data-stu-id="0d353-113">Set the device account’s **PasswordNeverExpires** property to True.</span></span> <span data-ttu-id="0d353-114">この設定が組織のセキュリティ要件を満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d353-114">You should verify whether this meets your organization’s security requirements.</span></span>


## <a name="allow-the-surface-hub-to-automatically-rotate-the-device-accounts-password"></a><span data-ttu-id="0d353-115">Surface Hub でデバイス アカウントのパスワードを自動的に循環できるようにする</span><span class="sxs-lookup"><span data-stu-id="0d353-115">Allow the Surface Hub to automatically rotate the device account’s password</span></span>

<span data-ttu-id="0d353-116">Surface Hub では、デバイス アカウントのパスワードを手動で更新する必要なく、デバイス アカウントのパスワードを自動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="0d353-116">The Surface Hub can automatically change a device account's password without requiring you to manually update it.</span></span> <span data-ttu-id="0d353-117">この機能は、[設定] Surface Hub**アカウント**  >  **で有効**  >  **にできます**。</span><span class="sxs-lookup"><span data-stu-id="0d353-117">You can enable this feature in **Settings** > **Surface Hub** > **Accounts**.</span></span> <span data-ttu-id="0d353-118">[パスワードのローテーション] をオンにした場合、Surface Hub はメンテナンス時間中に 7 日ごとにパスワードの変更を試行します。</span><span class="sxs-lookup"><span data-stu-id="0d353-118">If you turn on Password Rotation, the Surface Hub will attempt to change the password every 7 days during maintenance hours.</span></span> <span data-ttu-id="0d353-119">会議中にパスワードは変更されません。</span><span class="sxs-lookup"><span data-stu-id="0d353-119">Passwords do not change during a meeting.</span></span> <span data-ttu-id="0d353-120">前回のパスワードローテーションから 7 日が経過したが、Surface Hub がオフの場合は、有効になったときにすぐにパスワードを変更するか、成功するまで 10 分ごとにパスワードの変更を試みます。</span><span class="sxs-lookup"><span data-stu-id="0d353-120">If 7 days have passed since the last password rotation, but the Surface Hub was off, it will attempt to change the password immediately when turned on or every 10 minutes until successful.</span></span>

<span data-ttu-id="0d353-121">自動的に生成されるパスワードには、大文字と小文字、数字、特殊文字の組み合わせを含む 15 ~ 32 文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d353-121">The automatically generated passwords contain 15-32 characters including a combination of uppercase and lowercase letters, numbers, and special characters.</span></span> <span data-ttu-id="0d353-122">デバイス アカウントのパスワードが変更された場合、新しいパスワードは表示されません。</span><span class="sxs-lookup"><span data-stu-id="0d353-122">Note that when the device account's password is changed, you will not be shown the new password.</span></span> <span data-ttu-id="0d353-123">アカウントにサインインする必要がある場合や、もう一度パスワードを入力する必要がある場合 (Surface Hub のデバイス アカウント設定を変更する場合など)、Active Directory または Microsoft 365 管理ポータルを使用してパスワードをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d353-123">If you need to sign in to the account, or to provide the password again (for example, if you want to change the device account settings on the Surface Hub), then you'll need use Active Directory or the Microsoft 365 admin portal to reset the password.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d353-124">Surface Hub にデバイス アカウントを追加するときに使用される形式は、パスワード[](prepare-your-environment-for-surface-hub.md)のローテーションを機能するために使用する必要があるデバイスの所属オプションに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="0d353-124">The format used when adding the device account to the Surface Hub has an impact on which [device affiliation](prepare-your-environment-for-surface-hub.md) option must be used in order for password rotation to work.</span></span> <span data-ttu-id="0d353-125">domain\username 形式で **アカウントを追加する** 場合は、初期セットアップ中にハブをオンプレミスの Active Directory に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="0d353-125">If adding the account in **domain\username** format, affiliate the Hub with on-premises Active Directory during initial setup.</span></span> <span data-ttu-id="0d353-126">アカウントを形式で追加する `username@domain.com` 場合は、初期セットアップ中にハブを Azure Active Directory に関連付けします。</span><span class="sxs-lookup"><span data-stu-id="0d353-126">If adding the account in `username@domain.com` format, affiliate the Hub with Azure Active Directory during initial setup.</span></span> <span data-ttu-id="0d353-127">そうしないと、パスワードの循環が機能しません。</span><span class="sxs-lookup"><span data-stu-id="0d353-127">Otherwise, password rotation will not work.</span></span>
