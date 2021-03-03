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
ms.date: 2/26/2021
ms.localizationpriority: Medium
ms.openlocfilehash: caa6372820222f6f2f225f028161b3441b147a82
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385145"
---
# <a name="prepare-your-environment-for-surface-hub-2s"></a><span data-ttu-id="68198-104">Surface Hub 2S の環境の準備</span><span class="sxs-lookup"><span data-stu-id="68198-104">Prepare your environment for Surface Hub 2S</span></span>

## <a name="office-365-readiness"></a><span data-ttu-id="68198-105">Office 365 準備</span><span class="sxs-lookup"><span data-stu-id="68198-105">Office 365 readiness</span></span>

<span data-ttu-id="68198-106">Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft ホワイトボードを使用し、Intune で Surface Hub 2S を管理する場合は、まずエンドポイントの [Office 365](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)要件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="68198-106">If you use Exchange Online, Skype for Business Online, Microsoft Teams, or Microsoft Whiteboard, and intend to manage Surface Hub 2S with Intune, first review the [Office 365 requirements for endpoints](https://docs.microsoft.com/office365/enterprise/office-365-endpoints).</span></span>

<span data-ttu-id="68198-107">Office 365 エンドポイントは、すべての信頼できる Office 365 ネットワーク要求をファイアウォール経由で直接送信し、追加のパケット レベルの検査または処理をバイパスすることで、ネットワークを最適化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="68198-107">Office 365 endpoints help optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet-level inspection or processing.</span></span> <span data-ttu-id="68198-108">この機能により、待機時間と境界容量の要件が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="68198-108">This feature reduces latency and your perimeter capacity requirements.</span></span>

<span data-ttu-id="68198-109">Microsoft は、Office 365 サービスを定期的に更新し、必要なポート、URL、IP アドレスを変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68198-109">Microsoft regularly updates the Office 365 service with new features and functionality, which may alter required ports, URLs, and IP addresses.</span></span> <span data-ttu-id="68198-110">変更を評価、構成、および最新の情報に更新するには [、365 IP](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)アドレスと URL Web サービスOfficeを購読します。</span><span class="sxs-lookup"><span data-stu-id="68198-110">To evaluate, configure, and stay up to date with changes, subscribe to the [Office 365 IP Address and URL Web service](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).</span></span>

> [!NOTE]
> <span data-ttu-id="68198-111">Surface Hub は、Microsoft Teams、Skype for Business Server 2019、Skype for Business Server 2015、または Skype for Business Online と動作します。</span><span class="sxs-lookup"><span data-stu-id="68198-111">Surface Hub works with Microsoft Teams, Skype for Business Server 2019, Skype for Business Server 2015, or Skype for Business Online.</span></span>
<span data-ttu-id="68198-112">Lync Server 2013 などの以前のプラットフォームはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68198-112">Earlier platforms, such as Lync Server 2013, are not supported.</span></span> <span data-ttu-id="68198-113">Surface Hub は、ユーザーまたは DoD GCC-Highサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68198-113">Surface Hub is not supported in GCC-High or DoD environments.</span></span>


## <a name="device-affiliation"></a><span data-ttu-id="68198-114">デバイスの所属</span><span class="sxs-lookup"><span data-stu-id="68198-114">Device affiliation</span></span>

<span data-ttu-id="68198-115">デバイスの所属を使用して、Surface Hub 2S の設定アプリへのユーザー アクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="68198-115">Use Device affiliation to manage user access to the Settings app on Surface Hub 2S.</span></span>
<span data-ttu-id="68198-116">Windows 10 Team オペレーティング システム (Surface Hub 2S で実行) を使用すると、承認されたユーザーのみが設定アプリを使用して設定を調整できます。</span><span class="sxs-lookup"><span data-stu-id="68198-116">With the Windows 10 Team operating system (that runs on Surface Hub 2S),  only authorized users can adjust settings using the Settings app.</span></span> <span data-ttu-id="68198-117">所属を選択すると機能の可用性に影響を与える可能性があるから、ユーザーが意図した通り機能にアクセスできるよう適切に計画してください。</span><span class="sxs-lookup"><span data-stu-id="68198-117">Since choosing the affiliation can impact feature availability, plan appropriately to ensure that users can access features as intended.</span></span>

> [!NOTE]
> <span data-ttu-id="68198-118">デバイスの所属は、最初のアウトオブボックス エクスペリエンス (OOBE) セットアップ中にのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="68198-118">You can only set Device affiliation during the initial out-of-box experience (OOBE) setup.</span></span> <span data-ttu-id="68198-119">デバイスの所属をリセットする必要がある場合は、OOBE セットアップを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="68198-119">If you need to reset Device affiliation, you’ll have to repeat OOBE setup.</span></span>

## <a name="no-affiliation"></a><span data-ttu-id="68198-120">所属なし</span><span class="sxs-lookup"><span data-stu-id="68198-120">No affiliation</span></span>

<span data-ttu-id="68198-121">各 Surface Hub 2S に別のローカル管理者アカウントを持つワークグループに Surface Hub 2S を含む所属はありません。</span><span class="sxs-lookup"><span data-stu-id="68198-121">No affiliation is like having Surface Hub 2S in a workgroup with a different local Administrator account on each Surface Hub 2S.</span></span> <span data-ttu-id="68198-122">[所属なし] を選択した場合は、BitLocker キーを USB サム [ドライブにローカルに保存する必要があります](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)。</span><span class="sxs-lookup"><span data-stu-id="68198-122">If you choose No affiliation, you must locally save the [BitLocker Key to a USB thumb drive](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq).</span></span> <span data-ttu-id="68198-123">Intune でデバイスを登録することもできます。ただし、OOBE 中に構成されたアカウント資格情報を使用して、ローカル管理者だけが設定アプリにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="68198-123">You can still enroll the device with Intune; however, only the local admin can access the Settings app using the account credentials configured during OOBE.</span></span> <span data-ttu-id="68198-124">管理者アカウントのパスワードは、設定アプリから変更できます。</span><span class="sxs-lookup"><span data-stu-id="68198-124">You can change the Administrator account password from the Settings app.</span></span>

## <a name="active-directory-domain-services"></a><span data-ttu-id="68198-125">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="68198-125">Active Directory Domain Services</span></span>

<span data-ttu-id="68198-126">Surface Hub 2S をオンプレミスの Active Directory ドメイン サービスに関連付けられている場合は、ドメインのセキュリティ グループを使用して設定アプリへのアクセスを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68198-126">If you affiliate Surface Hub 2S with on-premises Active Directory Domain Services, you need to manage access to the Settings app using a security group on your domain.</span></span> <span data-ttu-id="68198-127">これにより、すべてのセキュリティ グループ メンバーに Surface Hub 2S の設定を変更するアクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="68198-127">This helps ensure that all security group members have permissions to change settings on Surface Hub 2S.</span></span> <span data-ttu-id="68198-128">また、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="68198-128">Also note the following:</span></span>

- <span data-ttu-id="68198-129">Surface Hub 2S がオンプレミスの Active Directory ドメイン サービスに関連付けられている場合、BitLocker キーを Active Directory スキーマに保存できます。</span><span class="sxs-lookup"><span data-stu-id="68198-129">When Surface Hub 2S affiliates with your on-premises Active Directory Domain Services, the BitLocker key can be saved in the Active Directory Schema.</span></span> <span data-ttu-id="68198-130">詳細については、「組織を BitLocker 用に準備する: 計画と [ポリシー」を参照してください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)。</span><span class="sxs-lookup"><span data-stu-id="68198-130">For more information, see [Prepare your organization for BitLocker: Planning and policies](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies).</span></span>

- <span data-ttu-id="68198-131">組織の信頼されたルート CA は Surface Hub 2S の同じコンテナーにプッシュされます。つまり、プロビジョニング パッケージを使用してインポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68198-131">Your organization’s Trusted Root CAs are pushed to the same container in Surface Hub 2S, which means you don’t need to import them using a provisioning package.</span></span>

- <span data-ttu-id="68198-132">デバイスを Intune に登録して、Surface Hub 2S の設定を一方的に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="68198-132">You can still enroll the device with Intune to centrally manage settings on your Surface Hub 2S.</span></span>

## <a name="azure-active-directory"></a><span data-ttu-id="68198-133">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="68198-133">Azure Active Directory</span></span>

<span data-ttu-id="68198-134">Surface Hub 2S を Azure Active Directory (Azure AD) に関連付け選択すると、グローバル管理者セキュリティ グループのすべてのユーザーが Surface Hub 2S の設定アプリにサインインできます。</span><span class="sxs-lookup"><span data-stu-id="68198-134">When you choose to affiliate your Surface Hub 2S with Azure Active Directory (Azure AD), any user in the Global Admins Security Group can sign in to the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="68198-135">また、Surface Hub 2S の設定アプリの管理に対するアクセス許可を制限するグローバル管理者以外のアカウントを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="68198-135">You can also configure non Global admin accounts that limit permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="68198-136">これにより、Surface Hub 2S の管理者アクセス許可のみを対象範囲に設定し、Azure Hub ドメイン全体で望ましくない可能性のある管理者アクセスをADできます。</span><span class="sxs-lookup"><span data-stu-id="68198-136">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> 

<span data-ttu-id="68198-137">組織で Intune 自動登録を有効にした場合、Surface Hub 2S は自動的に Intune に登録されます。</span><span class="sxs-lookup"><span data-stu-id="68198-137">If you enabled Intune Automatic Enrollment for your organization, Surface Hub 2S will automatically enroll itself with Intune.</span></span> <span data-ttu-id="68198-138">デバイスの BitLocker キーは、Azure サーバーに自動的にAD。</span><span class="sxs-lookup"><span data-stu-id="68198-138">The device’s BitLocker key is automatically saved in Azure AD.</span></span> 

<span data-ttu-id="68198-139">Azure を使用して Surface Hub を管理する方法の詳細についてはADを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68198-139">To learn more about managing Surface Hub with Azure AD, see:</span></span> 

 - [<span data-ttu-id="68198-140">管理者グループの管理</span><span class="sxs-lookup"><span data-stu-id="68198-140">Admin group management</span></span>](admin-group-management-for-surface-hub.md)
 - [<span data-ttu-id="68198-141">Surface Hub 2S でグローバル管理者以外のアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="68198-141">Configure non Global admin accounts on Surface Hub 2S</span></span>](surface-hub-2s-nonglobal-admin.md)

