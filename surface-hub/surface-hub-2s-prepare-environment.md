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
ms.date: 12/28/2020
ms.localizationpriority: Medium
ms.openlocfilehash: af66449806c9aa525fa3f5df84012d3daeed96ba
ms.sourcegitcommit: dbd14649442ad039aeb265cd60ed029d483a4bb0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/29/2020
ms.locfileid: "11251454"
---
# <span data-ttu-id="263e9-104">Surface Hub 2S の環境の準備</span><span class="sxs-lookup"><span data-stu-id="263e9-104">Prepare your environment for Surface Hub 2S</span></span>

## <span data-ttu-id="263e9-105">Office 365 の準備</span><span class="sxs-lookup"><span data-stu-id="263e9-105">Office 365 readiness</span></span>

<span data-ttu-id="263e9-106">Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft Whiteboard を使用し、Intune で Surface Hub 2S を管理する場合は、まずエンドポイントの [Office 365](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="263e9-106">If you use Exchange Online, Skype for Business Online, Microsoft Teams, or Microsoft Whiteboard, and intend to manage Surface Hub 2S with Intune, first review the [Office 365 requirements for endpoints](https://docs.microsoft.com/office365/enterprise/office-365-endpoints).</span></span>

<span data-ttu-id="263e9-107">Office 365 エンドポイントは、すべての信頼できる Office 365 ネットワーク要求をファイアウォール経由で直接送信し、追加のパケット レベルの検査または処理をバイパスすることで、ネットワークを最適化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="263e9-107">Office 365 endpoints help optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet-level inspection or processing.</span></span> <span data-ttu-id="263e9-108">この機能により、待機時間と境界容量の要件が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="263e9-108">This feature reduces latency and your perimeter capacity requirements.</span></span>

<span data-ttu-id="263e9-109">Microsoft は、Office 365 サービスを定期的に更新し、必要なポート、URL、IP アドレスを変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="263e9-109">Microsoft regularly updates the Office 365 service with new features and functionality, which may alter required ports, URLs, and IP addresses.</span></span> <span data-ttu-id="263e9-110">変更を評価、構成、および最新の情報を得るには、Office [365 IP アドレス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)と URL Web サービスにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="263e9-110">To evaluate, configure, and stay up to date with changes, subscribe to the [Office 365 IP Address and URL Web service](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).</span></span>

> [!NOTE]
> <span data-ttu-id="263e9-111">Surface Hub は、Microsoft Teams、Skype for Business Server 2019、Skype for Business Server 2015、または Skype for Business Online と一緒に動作します。</span><span class="sxs-lookup"><span data-stu-id="263e9-111">Surface Hub works with Microsoft Teams, Skype for Business Server 2019, Skype for Business Server 2015, or Skype for Business Online.</span></span>
<span data-ttu-id="263e9-112">Lync Server 2013 などの以前のプラットフォームはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="263e9-112">Earlier platforms, such as Lync Server 2013, are not supported.</span></span> <span data-ttu-id="263e9-113">Surface Hub は、GCC-High DoD 環境ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="263e9-113">Surface Hub is not supported in GCC-High or DoD environments.</span></span>


## <span data-ttu-id="263e9-114">デバイスの所属</span><span class="sxs-lookup"><span data-stu-id="263e9-114">Device affiliation</span></span>

<span data-ttu-id="263e9-115">デバイスの所属を使用して、Surface Hub 2S の設定アプリへのユーザー アクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="263e9-115">Use Device affiliation to manage user access to the Settings app on Surface Hub 2S.</span></span>
<span data-ttu-id="263e9-116">Windows 10 Team オペレーティング システム (Surface Hub 2S で実行) では、承認されたユーザーのみが設定アプリを使って設定を調整できます。</span><span class="sxs-lookup"><span data-stu-id="263e9-116">With the Windows 10 Team operating system (that runs on Surface Hub 2S),  only authorized users can adjust settings using the Settings app.</span></span> <span data-ttu-id="263e9-117">所属を選択すると機能の可用性に影響を与える可能性があります。そのため、ユーザーが意図した方法で機能にアクセスできるよう適切に計画します。</span><span class="sxs-lookup"><span data-stu-id="263e9-117">Since choosing the affiliation can impact feature availability, plan appropriately to ensure that users can access features as intended.</span></span>

> [!NOTE]
> <span data-ttu-id="263e9-118">デバイスの所属は、初期の Out-Of-Box Experience (OOBE) セットアップ時にのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="263e9-118">You can only set Device affiliation during the initial out-of-box experience (OOBE) setup.</span></span> <span data-ttu-id="263e9-119">デバイスの所属をリセットする必要がある場合は、OOBE セットアップを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="263e9-119">If you need to reset Device affiliation, you’ll have to repeat OOBE setup.</span></span>

## <span data-ttu-id="263e9-120">所属なし</span><span class="sxs-lookup"><span data-stu-id="263e9-120">No affiliation</span></span>

<span data-ttu-id="263e9-121">所属は、各 Surface Hub 2S で異なるローカル管理者アカウントを持つワークグループに Surface Hub 2S を持つような関係はありません。</span><span class="sxs-lookup"><span data-stu-id="263e9-121">No affiliation is like having Surface Hub 2S in a workgroup with a different local Administrator account on each Surface Hub 2S.</span></span> <span data-ttu-id="263e9-122">[No affiliation] (所属なし) を選択した場合は、BitLocker キーを USB サム [ドライブにローカルに保存する必要があります](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)。</span><span class="sxs-lookup"><span data-stu-id="263e9-122">If you choose No affiliation, you must locally save the [BitLocker Key to a USB thumb drive](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq).</span></span> <span data-ttu-id="263e9-123">デバイスを Intune に登録することもできます。ただし、OOBE 中に構成されたアカウント資格情報を使用して設定アプリにアクセスできるのはローカル管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="263e9-123">You can still enroll the device with Intune; however, only the local admin can access the Settings app using the account credentials configured during OOBE.</span></span> <span data-ttu-id="263e9-124">管理者アカウントのパスワードは、設定アプリから変更できます。</span><span class="sxs-lookup"><span data-stu-id="263e9-124">You can change the Administrator account password from the Settings app.</span></span>

## <span data-ttu-id="263e9-125">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="263e9-125">Active Directory Domain Services</span></span>

<span data-ttu-id="263e9-126">Surface Hub 2S をオンプレミスの Active Directory ドメイン サービスと関連付けられている場合は、ドメインのセキュリティ グループを使用して設定アプリへのアクセスを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="263e9-126">If you affiliate Surface Hub 2S with on-premises Active Directory Domain Services, you need to manage access to the Settings app using a security group on your domain.</span></span> <span data-ttu-id="263e9-127">これにより、すべてのセキュリティ グループ メンバーに、Surface Hub 2S の設定を変更するアクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="263e9-127">This helps ensure that all security group members have permissions to change settings on Surface Hub 2S.</span></span> <span data-ttu-id="263e9-128">次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="263e9-128">Also note the following:</span></span>

- <span data-ttu-id="263e9-129">Surface Hub 2S がオンプレミスの Active Directory ドメイン サービスと提携している場合、BitLocker キーを Active Directory スキーマに保存できます。</span><span class="sxs-lookup"><span data-stu-id="263e9-129">When Surface Hub 2S affiliates with your on-premises Active Directory Domain Services, the BitLocker key can be saved in the Active Directory Schema.</span></span> <span data-ttu-id="263e9-130">詳細については [、「BitLocker 用に組織を準備する: 計画とポリシー」を参照してください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)。</span><span class="sxs-lookup"><span data-stu-id="263e9-130">For more information, see [Prepare your organization for BitLocker: Planning and policies](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies).</span></span>

- <span data-ttu-id="263e9-131">組織の信頼されたルート CA が Surface Hub 2S の同じコンテナーにプッシュされます。つまり、プロビジョニング パッケージを使ってインポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="263e9-131">Your organization’s Trusted Root CAs are pushed to the same container in Surface Hub 2S, which means you don’t need to import them using a provisioning package.</span></span>

- <span data-ttu-id="263e9-132">デバイスを Intune に登録して、Surface Hub 2S の設定を一中央に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="263e9-132">You can still enroll the device with Intune to centrally manage settings on your Surface Hub 2S.</span></span>

## <span data-ttu-id="263e9-133">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="263e9-133">Azure Active Directory</span></span>

<span data-ttu-id="263e9-134">Surface Hub 2S を Azure Active Directory (Azure AD) と関連付け選択すると、グローバル管理者セキュリティ グループのユーザーは、Surface Hub 2S の設定アプリにサインインできます。</span><span class="sxs-lookup"><span data-stu-id="263e9-134">When you choose to affiliate your Surface Hub 2S with Azure Active Directory (Azure AD), any user in the Global Admins Security Group can sign in to the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="263e9-135">現在、Surface Hub 2S の設定アプリにサインインする他のグループは委任されません。</span><span class="sxs-lookup"><span data-stu-id="263e9-135">Currently, no other group can be delegated to sign in to the Settings app on Surface Hub 2S.</span></span>

<span data-ttu-id="263e9-136">組織で Intune の自動登録を有効にした場合、Surface Hub 2S は自動的に Intune に登録します。</span><span class="sxs-lookup"><span data-stu-id="263e9-136">If you enabled Intune Automatic Enrollment for your organization, Surface Hub 2S will automatically enroll itself with Intune.</span></span> <span data-ttu-id="263e9-137">デバイスの BitLocker キーは、Azure AD に自動的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="263e9-137">The device’s BitLocker key is automatically saved in Azure AD.</span></span> <span data-ttu-id="263e9-138">Azure AD を使用して Surface Hub 2S に関連付けすると、シングル サインオンと簡単な認証は機能しません。</span><span class="sxs-lookup"><span data-stu-id="263e9-138">When affiliating Surface Hub 2S with Azure AD, single sign-on and Easy Authentication will not work.</span></span>
