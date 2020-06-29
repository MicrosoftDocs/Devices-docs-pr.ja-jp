---
title: デバイス アカウントの作成およびテスト (Surface Hub)
description: このトピックでは、Microsoft Exchange や Skype と通信するために Microsoft Surface Hub で使用するデバイス アカウントを作成およびテストする方法について説明します。
ms.assetid: C8605B5F-2178-4C3A-B4E0-CE32C70ECF67
ms.reviewer: rikot
manager: laurawi
keywords: デバイス アカウントの作成とテスト, デバイス アカウント, Surface Hub と Microsoft Exchange, Surface Hub と Skype
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/06/2018
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 20ec9b3a81ad511bcb7880de6b53025fbac0a561
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836341"
---
# <span data-ttu-id="2c57f-104">デバイス アカウントの作成およびテスト (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="2c57f-104">Create and test a device account (Surface Hub)</span></span>


<span data-ttu-id="2c57f-105">このトピックでは、Microsoft Exchange や Skype と通信するために Microsoft Surface Hub で使用するデバイス アカウントを作成およびテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c57f-105">This topic introduces how to create and test the device account that Microsoft Surface Hub uses to communicate with Microsoft Exchange and Skype.</span></span>

<span data-ttu-id="2c57f-106">**デバイス アカウント**とは、Surface Hub で次の用途に使用する Exchange リソース アカウントです。</span><span class="sxs-lookup"><span data-stu-id="2c57f-106">A **device account** is an Exchange resource account that Surface Hub uses to:</span></span>

-   <span data-ttu-id="2c57f-107">会議のカレンダーを表示する</span><span class="sxs-lookup"><span data-stu-id="2c57f-107">Display its meeting calendar</span></span>
-   <span data-ttu-id="2c57f-108">Teams または Skype for Business の通話に参加する</span><span class="sxs-lookup"><span data-stu-id="2c57f-108">Join Teams or Skype for Business calls</span></span>
-   <span data-ttu-id="2c57f-109">メールを送信する (たとえば、会議からホワイトボード コンテンツをメール送信するなど)</span><span class="sxs-lookup"><span data-stu-id="2c57f-109">Send email (for example, email whiteboard content from a meeting)</span></span>

<span data-ttu-id="2c57f-110">Surface Hub にデバイス アカウントをプロビジョニングすると、ユーザーは、会議室に招待するのと同様に、会議出席依頼にこのアカウントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="2c57f-110">Once the device account is provisioned to a Surface Hub, people can add this account to a meeting invitation the same way that they would invite a meeting room.</span></span> 

## <span data-ttu-id="2c57f-111">構成の概要</span><span class="sxs-lookup"><span data-stu-id="2c57f-111">Configuration overview</span></span>

<span data-ttu-id="2c57f-112">次の表では、デバイス アカウントを作成する際の主な手順と構成の決定について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c57f-112">This table explains the main steps and configuration decisions when you create a device account.</span></span> 
 
| <span data-ttu-id="2c57f-113">ステップ</span><span class="sxs-lookup"><span data-stu-id="2c57f-113">Step</span></span> | <span data-ttu-id="2c57f-114">説明</span><span class="sxs-lookup"><span data-stu-id="2c57f-114">Description</span></span>                     |  <span data-ttu-id="2c57f-115">目的</span><span class="sxs-lookup"><span data-stu-id="2c57f-115">Purpose</span></span>                             |
|------|---------------------------------|--------------------------------------|
| <span data-ttu-id="2c57f-116">件</span><span class="sxs-lookup"><span data-stu-id="2c57f-116">1</span></span>    | <span data-ttu-id="2c57f-117">ログオンが可能な Exchange リソース メールボックス (Exchange 2013 以降または Exchange Online) を作成する</span><span class="sxs-lookup"><span data-stu-id="2c57f-117">Created a logon-enabled Exchange resource mailbox (Exchange 2013 or later, or Exchange Online)</span></span> | <span data-ttu-id="2c57f-118">このリソース メールボックスにより、デバイスで会議のカレンダーの管理、会議出席依頼の受信、メールの送信を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2c57f-118">This resource mailbox allows the device to maintain a meeting calendar, receive meeting requests, and send mail.</span></span> <span data-ttu-id="2c57f-119">Surface Hub にプロビジョニングするには、このメールボックスがログオン可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-119">It must be logon-enabled to be provisioned to a Surface Hub.</span></span> |
| <span data-ttu-id="2c57f-120">両面</span><span class="sxs-lookup"><span data-stu-id="2c57f-120">2</span></span>    | <span data-ttu-id="2c57f-121">メールボックスのプロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="2c57f-121">Configure mailbox properties</span></span> | <span data-ttu-id="2c57f-122">Surface Hub で最適な会議エクスペリエンスを実現するには、メールボックスのプロパティを適切に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-122">The mailbox must be configured with the correct properties to enable the best meeting experience on Surface Hub.</span></span> <span data-ttu-id="2c57f-123">メールボックスのプロパティについて詳しくは、[メールボックスのプロパティに関するページ](exchange-properties-for-surface-hub-device-accounts.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c57f-123">For more information on mailbox properties, see [Mailbox properties](exchange-properties-for-surface-hub-device-accounts.md).</span></span> |
| <span data-ttu-id="2c57f-124">-</span><span class="sxs-lookup"><span data-stu-id="2c57f-124">3</span></span>    | <span data-ttu-id="2c57f-125">メールボックスに互換性のあるモバイル デバイス メールボックス ポリシーを適用する</span><span class="sxs-lookup"><span data-stu-id="2c57f-125">Apply a compatible mobile device mailbox policy to the mailbox</span></span> | <span data-ttu-id="2c57f-126">Surface Hub は、モバイル デバイス メールボックス ポリシーではなく、モバイル デバイス管理 (MDM) を使用して管理されています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-126">Surface Hub is managed using mobile device management (MDM) rather than through mobile device mailbox policies.</span></span> <span data-ttu-id="2c57f-127">互換性のため、デバイス アカウントのモバイル デバイス メールボックス ポリシーでは、**PasswordEnabled** 設定を False に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-127">For compatibility, the device account must have a mobile device mailbox policy where the **PasswordEnabled** setting is set to False.</span></span> <span data-ttu-id="2c57f-128">このように設定していない場合、Surface Hub はメールとカレンダーの情報を同期できません。</span><span class="sxs-lookup"><span data-stu-id="2c57f-128">Otherwise, Surface Hub can't sync mail and calendar info.</span></span> |
| <span data-ttu-id="2c57f-129">4d</span><span class="sxs-lookup"><span data-stu-id="2c57f-129">4</span></span>    | <span data-ttu-id="2c57f-130">Skype for Business (Lync Server 2013 以降または Skype for Business Online) でメールボックスを有効にする</span><span class="sxs-lookup"><span data-stu-id="2c57f-130">Enable mailbox with Skype for Business (Lync Server 2013 or later, or Skype for Business Online)</span></span> | <span data-ttu-id="2c57f-131">ビデオ通話、IM、画面共有など、さまざまな会議機能を使用するには、Skype for Business を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-131">Skype for Business must be enabled to use conferencing features like video calls, IM, and screen sharing.</span></span>  |
| <span data-ttu-id="2c57f-132">個</span><span class="sxs-lookup"><span data-stu-id="2c57f-132">5</span></span>    | <span data-ttu-id="2c57f-133">(省略可能) ActiveSync デバイス ID をホワイトリストに追加する</span><span class="sxs-lookup"><span data-stu-id="2c57f-133">(Optional) Whitelist ActiveSync Device ID</span></span> | <span data-ttu-id="2c57f-134">組織によっては、デバイス アカウントでメールとカレンダーの情報を同期することを、グローバル ポリシーで禁止している場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-134">Your organization may have a global policy that prevents device accounts from syncing mail and calendar info.</span></span> <span data-ttu-id="2c57f-135">その場合は、Surface Hub の ActiveSync デバイス ID を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-135">If so, you need to allow the ActiveSync Device ID of your Surface Hub.</span></span> |
| <span data-ttu-id="2c57f-136">=</span><span class="sxs-lookup"><span data-stu-id="2c57f-136">6</span></span>    | <span data-ttu-id="2c57f-137">(省略可能) パスワードの有効期限を無効にする</span><span class="sxs-lookup"><span data-stu-id="2c57f-137">(Optional) Disable password expiration</span></span> | <span data-ttu-id="2c57f-138">管理を合理化するために、デバイス アカウントのパスワードの有効期限をオフにし、Surface Hub でデバイス アカウントのパスワードを自動的に循環できるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="2c57f-138">To simplify management, you can turn off password expiration for the device account and allow Surface Hub to automatically rotate the device account password.</span></span> <span data-ttu-id="2c57f-139">パスワード管理について詳しくは、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c57f-139">For more information about password management, see [Password management](password-management-for-surface-hub-device-accounts.md).</span></span>  |

## <span data-ttu-id="2c57f-140">詳細な構成手順</span><span class="sxs-lookup"><span data-stu-id="2c57f-140">Detailed configuration steps</span></span> 

<span data-ttu-id="2c57f-141">リモートの PowerShell を使用して、デバイス アカウントを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c57f-141">We recommend setting up your device accounts using remote PowerShell.</span></span> <span data-ttu-id="2c57f-142">デバイス アカウントの作成と検証に役立つ PowerShell スクリプトが用意されています。PowerShell スクリプトと操作手順について詳しくは、「[付録 A: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c57f-142">There are PowerShell scripts available to help create and validate device accounts For more information on PowerShell scripts and instructions, see [Appendix A: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md).</span></span> 

<span data-ttu-id="2c57f-143">PowerShell を使用してデバイス アカウントをプロビジョニングする詳しい手順については、組織での展開に基づいて、次の表のオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="2c57f-143">For detailed steps using PowerShell to provision a device account, choose an option from the table, based on your organization deployment.</span></span> 

| <span data-ttu-id="2c57f-144">組織での展開</span><span class="sxs-lookup"><span data-stu-id="2c57f-144">Organization deployment</span></span>             |  <span data-ttu-id="2c57f-145">説明</span><span class="sxs-lookup"><span data-stu-id="2c57f-145">Description</span></span>                  |
|---------------------------------|--------------------------------------|
| [<span data-ttu-id="2c57f-146">オンライン展開 (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2c57f-146">Online deployment (Office 365)</span></span>](online-deployment-surface-hub-device-accounts.md) | <span data-ttu-id="2c57f-147">組織の環境全体が Office 365 に展開されています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-147">Your organization's environment is deployed entirely on Office 365.</span></span> |
| [<span data-ttu-id="2c57f-148">オンプレミス展開 (単一フォレスト)</span><span class="sxs-lookup"><span data-stu-id="2c57f-148">On-premises deployment (single-forest)</span></span>](on-premises-deployment-surface-hub-device-accounts.md) | <span data-ttu-id="2c57f-149">組織で複数のサーバーを管理しており、これらのサーバーを使用して Active Directory、Exchange、Skype for Business (または Lync) を単一フォレスト環境でホストしています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-149">Your organization has servers that it controls and uses to host Active Directory, Exchange, and Skype for Business (or Lync) in a single-forest environment.</span></span> |
| [<span data-ttu-id="2c57f-150">オンプレミス展開 (複数フォレスト)</span><span class="sxs-lookup"><span data-stu-id="2c57f-150">On-premises deployment (multiple forests)</span></span>](on-premises-deployment-surface-hub-multi-forest.md) | <span data-ttu-id="2c57f-151">組織で複数のサーバーを管理しており、これらのサーバーを使用して Active Directory、Exchange、Skype for Business (または Lync) を複数フォレスト環境でホストしています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-151">Your organization has servers that it controls and uses to host Active Directory, Exchange, and Skype for Business (or Lync) in a multi-forest environment.</span></span> |
| [<span data-ttu-id="2c57f-152">ハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="2c57f-152">Hybrid deployment</span></span>](hybrid-deployment-surface-hub-device-accounts.md) | <span data-ttu-id="2c57f-153">組織には、オンプレミスでホストされているサービスと、Office 365 を介してオンラインでホストされているサービスの両方が混在しています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-153">Your organization has a mix of services, with some hosted on-premises and some hosted online through Office 365.</span></span> |
| [<span data-ttu-id="2c57f-154">Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="2c57f-154">Online or hybrid deployment using Skype Hybrid Voice environment</span></span>](skype-hybrid-voice.md) | <span data-ttu-id="2c57f-155">組織では、クラウド上に Skype for Business のホーム プールと Exchange サーバーがあり、Skype for Business 2015、または公衆交換電話網 (PSTN) 経由で接続されたクラウド コネクタ エディションのオンプレミス プールを使っています。</span><span class="sxs-lookup"><span data-stu-id="2c57f-155">Your organization has Skype for Business home pools and Exchange servers in the cloud, and uses an on-premises pool of Skype for Business 2015 or Cloud Connector edition connected via Public Switched Telephone Network (PSTN).</span></span> |


<span data-ttu-id="2c57f-156">グラフィカル ユーザー インターフェイス (UI) を使用する場合は、一部の手順を PowerShellではなく、UI を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="2c57f-156">If you prefer to use a graphical user interface (UI), some steps can be done using UI instead of PowerShell.</span></span> <span data-ttu-id="2c57f-157">詳しくは、「[UI を使用してデバイス アカウントを作成する ](create-a-device-account-using-office-365.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c57f-157">For more information, see [Creating a device account using UI](create-a-device-account-using-office-365.md).</span></span>

## <span data-ttu-id="2c57f-158">アカウントの検証とテスト</span><span class="sxs-lookup"><span data-stu-id="2c57f-158">Account verification and testing</span></span>

<span data-ttu-id="2c57f-159">Surface Hub デバイス アカウントを検証およびテストするための方法としては、[アカウント検証スクリプト](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts)と [Surface Hub Hardware Diagnostic アプリ](https://www.microsoft.com/store/apps/9nblggh51f2g)の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-159">There are two methods available that you can use to validate and test a Surface Hub device account: [account verifications scripts](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts) and the [Surface Hub Hardware Diagnostic app](https://www.microsoft.com/store/apps/9nblggh51f2g).</span></span> <span data-ttu-id="2c57f-160">アカウント検証スクリプトでは、デスクトップから PowerShell を使用して、以前に作成したデバイス アカウントを検証します。</span><span class="sxs-lookup"><span data-stu-id="2c57f-160">The account verification script will validate a previously-created device account using PowerShell from your desktop.</span></span> <span data-ttu-id="2c57f-161">Surface Hub Hardware Diagnostic アプリは、Surface Hub にインストールされ、サインインや通信の障害に関する詳細なフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="2c57f-161">The Surface Hub Hardware Diagnostic app is installed on your Surface Hub and provides detailed feedback about signin and communication failures.</span></span> <span data-ttu-id="2c57f-162">どちらも新しく作成したデバイス アカウントをテストするための優れたツールであり、最適なアカウントの可用性を確保するために使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c57f-162">Both are valuable tools to test newly created device accounts and should be used to ensure optimal account availability.</span></span>

 

 

 





