---
title: Surface Hub 2S の環境の準備
description: Surface Hub 2S の環境を準備するために必要な操作について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 11/21/2019
ms.localizationpriority: Medium
ms.openlocfilehash: dddab2adce1bec9ff722a3324b9c4b1be609ae89
ms.sourcegitcommit: ac34f0ec1a9df74ea688bf0da2a51fadf5139a41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/18/2020
ms.locfileid: "10934847"
---
# <span data-ttu-id="166cd-104">Surface Hub 2S の環境の準備</span><span class="sxs-lookup"><span data-stu-id="166cd-104">Prepare your environment for Surface Hub 2S</span></span>

## <span data-ttu-id="166cd-105">Office 365 の準備</span><span class="sxs-lookup"><span data-stu-id="166cd-105">Office 365 readiness</span></span>

<span data-ttu-id="166cd-106">Exchange Online、Skype for Business Online、Microsoft Teams、または Microsoft ホワイトボードを使用しており、Intune で Surface Hub 2 を管理する必要がある場合は、まず [エンドポイントの Office 365 の要件](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="166cd-106">If you use Exchange Online, Skype for Business Online, Microsoft Teams, or Microsoft Whiteboard, and intend to manage Surface Hub 2S with Intune, first review the [Office 365 requirements for endpoints](https://docs.microsoft.com/office365/enterprise/office-365-endpoints).</span></span>

<span data-ttu-id="166cd-107">Office 365 エンドポイントは、すべての信頼された Office 365 ネットワーク要求をファイアウォール経由で直接送信することで、ネットワークの最適化を支援します。追加のパケットレベルの検査や処理はすべてバイパスします。</span><span class="sxs-lookup"><span data-stu-id="166cd-107">Office 365 endpoints help optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet-level inspection or processing.</span></span> <span data-ttu-id="166cd-108">この機能により、待機時間と境界容量の要件を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="166cd-108">This feature reduces latency and your perimeter capacity requirements.</span></span>

<span data-ttu-id="166cd-109">Microsoft は、Office 365 サービスを定期的に更新します。新機能により、必要なポート、Url、IP アドレスが変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="166cd-109">Microsoft regularly updates the Office 365 service with new features and functionality, which may alter required ports, URLs, and IP addresses.</span></span> <span data-ttu-id="166cd-110">変更を評価、構成して最新の状態に保つには、 [Office 365 IP アドレスと URL Web サービス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)を購読します。</span><span class="sxs-lookup"><span data-stu-id="166cd-110">To evaluate, configure, and stay up to date with changes, subscribe to the [Office 365 IP Address and URL Web service](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).</span></span>

## <span data-ttu-id="166cd-111">デバイスの所属</span><span class="sxs-lookup"><span data-stu-id="166cd-111">Device affiliation</span></span>

<span data-ttu-id="166cd-112">デバイスの所属を使って、Surface Hub 2S の設定アプリへのユーザーアクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="166cd-112">Use Device affiliation to manage user access to the Settings app on Surface Hub 2S.</span></span>
<span data-ttu-id="166cd-113">Windows 10 Team オペレーティングシステム (Surface Hub 2S で実行される) では、許可されたユーザーのみが設定アプリを使って設定を調整できます。</span><span class="sxs-lookup"><span data-stu-id="166cd-113">With the Windows 10 Team operating system (that runs on Surface Hub 2S),  only authorized users can adjust settings using the Settings app.</span></span> <span data-ttu-id="166cd-114">所属の選択によって機能の可用性に影響を与える可能性があるため、ユーザーが意図した機能に確実にアクセスできるように、適切な計画を立ててください。</span><span class="sxs-lookup"><span data-stu-id="166cd-114">Since choosing the affiliation can impact feature availability, plan appropriately to ensure that users can access features as intended.</span></span>

> [!NOTE]
> <span data-ttu-id="166cd-115">デバイスの所属を設定できるのは、初期の既定のエクスペリエンス (OOBE) セットアップ時のみです。</span><span class="sxs-lookup"><span data-stu-id="166cd-115">You can only set Device affiliation during the initial out-of-box experience (OOBE) setup.</span></span> <span data-ttu-id="166cd-116">デバイスの所属をリセットする必要がある場合は、OOBE のセットアップを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="166cd-116">If you need to reset Device affiliation, you’ll have to repeat OOBE setup.</span></span>

## <span data-ttu-id="166cd-117">所属しません</span><span class="sxs-lookup"><span data-stu-id="166cd-117">No affiliation</span></span>

<span data-ttu-id="166cd-118">所属しません。各 Surface Hub 2S に異なるローカル管理者アカウントがあるワークグループには Surface Hub の2S があります。</span><span class="sxs-lookup"><span data-stu-id="166cd-118">No affiliation is like having Surface Hub 2S in a workgroup with a different local Administrator account on each Surface Hub 2S.</span></span> <span data-ttu-id="166cd-119">[所属しない] を選んだ場合は、 [BitLocker キーを USB サムドライブにローカルに](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq)保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="166cd-119">If you choose No affiliation, you must locally save the [BitLocker Key to a USB thumb drive](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq).</span></span> <span data-ttu-id="166cd-120">引き続き、Intune でデバイスを登録することができます。ただし、OOBE 中に構成されたアカウントの資格情報を使用して設定アプリにアクセスできるのは、ローカル管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="166cd-120">You can still enroll the device with Intune; however, only the local admin can access the Settings app using the account credentials configured during OOBE.</span></span> <span data-ttu-id="166cd-121">設定アプリから管理者アカウントのパスワードを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="166cd-121">You can change the Administrator account password from the Settings app.</span></span>

## <span data-ttu-id="166cd-122">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="166cd-122">Active Directory Domain Services</span></span>

<span data-ttu-id="166cd-123">オンプレミスの Active Directory ドメインサービスと Surface Hub 2S を利用している場合は、ドメインのセキュリティグループを使用して、設定アプリへのアクセスを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="166cd-123">If you affiliate Surface Hub 2S with on-premises Active Directory Domain Services, you need to manage access to the Settings app using a security group on your domain.</span></span> <span data-ttu-id="166cd-124">これにより、すべてのセキュリティグループメンバーに、Surface Hub 2S の設定を変更するアクセス許可を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="166cd-124">This helps ensure that all security group members have permissions to change settings on Surface Hub 2S.</span></span> <span data-ttu-id="166cd-125">次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="166cd-125">Also note the following:</span></span>

- <span data-ttu-id="166cd-126">Surface Hub の系列がオンプレミスの Active Directory ドメインサービスと関連付けられている場合、BitLocker キーを Active Directory スキーマに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="166cd-126">When Surface Hub 2S affiliates with your on-premises Active Directory Domain Services, the BitLocker key can be saved in the Active Directory Schema.</span></span> <span data-ttu-id="166cd-127">詳細については、「 [組織の BitLocker 用の準備: 計画とポリシー](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="166cd-127">For more information, see [Prepare your organization for BitLocker: Planning and policies](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies).</span></span> 
- <span data-ttu-id="166cd-128">組織の信頼されたルート Ca は Surface Hub 2S の同じコンテナーにプッシュされるため、プロビジョニングパッケージを使ってインポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="166cd-128">Your organization’s Trusted Root CAs are pushed to the same container in Surface Hub 2S, which means you don’t need to import them using a provisioning package.</span></span>
- <span data-ttu-id="166cd-129">引き続き、Intune でデバイスを登録して、Surface Hub 2S の設定を一元管理することができます。</span><span class="sxs-lookup"><span data-stu-id="166cd-129">You can still enroll the device with Intune to centrally manage settings on your Surface Hub 2S.</span></span>

## <span data-ttu-id="166cd-130">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="166cd-130">Azure Active Directory</span></span>

<span data-ttu-id="166cd-131">Surface Hub 2S を Azure Active Directory (Azure AD) と連携するように選択すると、グローバル管理者セキュリティグループのユーザーは Surface Hub 2S の設定アプリにサインインできるようになります。</span><span class="sxs-lookup"><span data-stu-id="166cd-131">When you choose to affiliate your Surface Hub 2S with Azure Active Directory (Azure AD), any user in the Global Admins Security Group can sign in to the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="166cd-132">現在、他のグループを委任して、Surface Hub 2S の設定アプリにサインインすることはできません。</span><span class="sxs-lookup"><span data-stu-id="166cd-132">Currently, no other group can be delegated to sign in to the Settings app on Surface Hub 2S.</span></span>

<span data-ttu-id="166cd-133">組織の Intune 自動登録を有効にしている場合、Surface Hub 2S は Intune に自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="166cd-133">If you enabled Intune Automatic Enrollment for your organization, Surface Hub 2S will automatically enroll itself with Intune.</span></span> <span data-ttu-id="166cd-134">デバイスの BitLocker キーは、Azure AD に自動的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="166cd-134">The device’s BitLocker key is automatically saved in Azure AD.</span></span> <span data-ttu-id="166cd-135">Azure AD で affiliating Surface Hub 2S が使用されている場合、シングルサインオンと簡単な認証は機能しません。</span><span class="sxs-lookup"><span data-stu-id="166cd-135">When affiliating Surface Hub 2S with Azure AD, single sign-on and Easy Authentication will not work.</span></span>
