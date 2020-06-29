---
title: Surface Hub 2S の初めてのセットアップ
description: Surface Hub 2S の初めてのセットアップを完了する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 47a393944c1b524931a6ac56962cc2cd60786007
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836125"
---
# <span data-ttu-id="09594-104">Surface Hub 2S の初めてのセットアップ</span><span class="sxs-lookup"><span data-stu-id="09594-104">First time Setup for Surface Hub 2S</span></span>

<span data-ttu-id="09594-105">初めて Surface Hub 2S を起動すると、デバイスは、アカウントの構成と関連設定についてのガイドとして、最初にセットアップモードに自動的に入力します。</span><span class="sxs-lookup"><span data-stu-id="09594-105">When you first start Surface Hub 2S, the device automatically enters first time Setup mode to guide you through account configuration and related settings.</span></span>

## <span data-ttu-id="09594-106">Surface Hub 2S アカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="09594-106">Configuring Surface Hub 2S account</span></span>

1. **<span data-ttu-id="09594-107">ロケールを構成します。</span><span class="sxs-lookup"><span data-stu-id="09594-107">Configure your locale.</span></span>** <span data-ttu-id="09594-108">地域、言語、キーボードレイアウト、タイムゾーン情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="09594-108">Enter region, language, keyboard layout and time zone information.</span></span> <span data-ttu-id="09594-109">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="09594-109">Select **Next**.</span></span>

   ![\* ロケールを設定する \*](images/sh2-run1.png) <br>
1. **<span data-ttu-id="09594-111">ワイヤレスネットワークに接続します。</span><span class="sxs-lookup"><span data-stu-id="09594-111">Connect  to a wireless network.</span></span>** <span data-ttu-id="09594-112">優先ワイヤレスネットワークを選択して、[次へ] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="09594-112">Choose your preferred wireless network and select **Next.**</span></span>

- <span data-ttu-id="09594-113">イーサネットケーブルを使って接続している場合は、このオプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="09594-113">This option is not shown if connected using an Ethernet cable.</span></span>
- <span data-ttu-id="09594-114">サインイン要求をプロバイダーの web サイトにリダイレクトするホットスポット (専用ポータル) 内のワイヤレスネットワークに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="09594-114">You cannot connect to a wireless network in hotspots (captive portals) that redirect sign-in requests to a provider’s website.</span></span>

3. **<span data-ttu-id="09594-115">デバイスアカウント情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="09594-115">Enter device account info.</span></span>** <span data-ttu-id="09594-116">オンプレミスおよびハイブリッド環境には**domain\user** 、オンライン環境では**ユーザー \ @example .com**を使用します。</span><span class="sxs-lookup"><span data-stu-id="09594-116">Use **domain\user** for on-premises and hybrid environments and **user\@example.com** for online environments.</span></span> <span data-ttu-id="09594-117">[**次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="09594-117">Select **Next.**</span></span>

   ![\* デバイスアカウント情報を入力 \*](images/sh2-run2.png) <br>
1. **<span data-ttu-id="09594-119">追加情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="09594-119">Enter additional info.</span></span>** <span data-ttu-id="09594-120">要求された場合は、Exchange サーバーのアドレスを入力して、[次へ] を選び**ます。**</span><span class="sxs-lookup"><span data-stu-id="09594-120">If requested, provide your Exchange server address and then select **Next.**</span></span>

    ![\* 情報を入力してください。たとえば、Exchange server 名 \*](images/sh2-run3.png) <br>

1. **<span data-ttu-id="09594-122">このデバイスに名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="09594-122">Name this device.</span></span>** <span data-ttu-id="09594-123">お使いのデバイスの名前を入力するか、お使いのアカウントの表示名とユーザプリンシパル名に基づいて推奨されるものを使用してください。</span><span class="sxs-lookup"><span data-stu-id="09594-123">Enter a name for your device or use the suggested one based on your account’s display name and user principle name [UPN].</span></span> <span data-ttu-id="09594-124">**[次へ] を選び**ます。</span><span class="sxs-lookup"><span data-stu-id="09594-124">**Select Next**.</span></span>

- <span data-ttu-id="09594-125">**フレンドリ名**は Surface Hub 2s の左下隅に表示され、デバイスに投影したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="09594-125">The **Friendly name** is visible on the bottom left corner of Surface Hub 2S and is shown when projecting to the device.</span></span>

- <span data-ttu-id="09594-126">デバイス**名**は、Active directory または Azure Active directory に関連している場合と、デバイスを Intune に登録する場合に、デバイスを識別します。</span><span class="sxs-lookup"><span data-stu-id="09594-126">The **Device name** identifies the device when affiliated with Active Directory or Azure Active Directory, and when enrolling the device with Intune.</span></span>

  ![\* このデバイス名 \*](images/sh2-run4.png) <br>
 
## <span data-ttu-id="09594-128">デバイス管理者アカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="09594-128">Configuring device admin accounts</span></span>

<span data-ttu-id="09594-129">初めてセットアップするときにのみ、デバイス管理者を設定できます。</span><span class="sxs-lookup"><span data-stu-id="09594-129">You can only set up device admins during first time Setup.</span></span> <span data-ttu-id="09594-130">詳細については、「 [Surface Hub 2s デバイスの所属](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09594-130">For more information, refer to [Surface Hub 2S device affiliation](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation).</span></span>

 <span data-ttu-id="09594-131">[**このデバイスのセットアップ管理者**] ウィンドウで、次のいずれかのオプション (Active Directory ドメインサービス、Azure Active directory、またはローカル管理者) を選びます。</span><span class="sxs-lookup"><span data-stu-id="09594-131">In the **Setup admins for this device** window, select one of the following options: Active Directory Domain Services, Azure Active Directory, or Local admin.</span></span>

   ![\* このデバイスの管理者のセットアップ \*](images/sh2-run5.png) <br>

### <span data-ttu-id="09594-133">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="09594-133">Active Directory Domain Services</span></span>

1. <span data-ttu-id="09594-134">デバイスを Active Directory に参加する権限を持つユーザーの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="09594-134">Enter the credentials of a user who has permissions to join the device to Active Directory.</span></span>

    ![\* ドメイン参加を使用して管理者を設定する \*](images/sh2-run6.png) <br>

2. <span data-ttu-id="09594-136">Surface Hub 2S の設定アプリへのログオンが許可されているメンバーが含まれている Active Directory セキュリティグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="09594-136">Select the Active Directory Security Group containing members allowed to log on to the Settings app on Surface Hub 2S.</span></span>

    ![\* セキュリティグループの入力 \*](images/sh2-run7.png) <br>
1. <span data-ttu-id="09594-138">[**完了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="09594-138">Select **Finish**.</span></span> <span data-ttu-id="09594-139">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="09594-139">The device will restart.</span></span>

### <span data-ttu-id="09594-140">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="09594-140">Azure Active Directory</span></span>

<span data-ttu-id="09594-141">Azure Active Directory でデバイスを利用することを選択すると、デバイスは直ちに再起動し、次のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09594-141">When choosing to affiliate your device with Azure Active Directory, the device will immediately restart and display the following page.</span></span> <span data-ttu-id="09594-142">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="09594-142">Select **Next**.</span></span>

![\* Office 365 または Microsoft の他のビジネスサービスを使用している組織では、このデバイスを組織に enrolll \*](images/sh2-run8.png) <br>

1. <span data-ttu-id="09594-144">**Intune Plan 1**以上のアカウントのメールアドレスまたは UPN を入力し、[次へ] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="09594-144">Enter the email address or UPN of an account **with Intune Plan 1** or greater and then select **Next.**</span></span>

    ![\* 職場または学校のアカウントを入力してください \*](images/sh2-run9.png) <br>

2. <span data-ttu-id="09594-146">リダイレクトされた場合は、組織のサインインページを使用して認証し、必要に応じて追加のログオン情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="09594-146">If redirected, authenticate using your organization’s sign-in page and provide additional logon information if requested.</span></span> <span data-ttu-id="09594-147">デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="09594-147">The device will restart.</span></span>

## <span data-ttu-id="09594-148">ローカル管理者アカウント</span><span class="sxs-lookup"><span data-stu-id="09594-148">Local Administrator account</span></span>

- <span data-ttu-id="09594-149">ローカル管理者のユーザー名とパスワードを入力します。デバイスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="09594-149">Enter a username and password for your local admin. The device will restart.</span></span>

     ![\* 管理アカウントのセットアップ \*](images/sh2-run10.png) <br>
 
## <span data-ttu-id="09594-151">プロビジョニングパッケージの使用</span><span class="sxs-lookup"><span data-stu-id="09594-151">Using provisioning packages</span></span>

<span data-ttu-id="09594-152">Surface Hub 2S を起動したときに、プロビジョニングパッケージ付きの USB サムドライブを USB ポートの1つに挿入すると、デバイスに次のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09594-152">If you insert a USB thumb drive with a provisioning package into one of the USB ports when you start Surface Hub 2S, the device displays the following page.</span></span>

1. <span data-ttu-id="09594-153">要求された設定を入力し、[**設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="09594-153">Enter the requested settings and select **Set up**.</span></span>

    ![\* プロビジョニングパッケージの地域設定を入力 \*](images/sh2-run11.png) <br>

    ![\* リムーバブルメディアからこのデバイスをプロビジョニング \*](images/sh2-run12.png) <br>
2. <span data-ttu-id="09594-156">使用するプロビジョニングパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="09594-156">Choose the provisioning package you’d like to use.</span></span>

   ![\* 使用するプロビジョニングパッケージを選ぶ \*](images/sh2-run13.png) <br>

3. <span data-ttu-id="09594-158">複数のデバイス CSV ファイルを作成した場合は、デバイス構成を選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="09594-158">If you created a multiple devices CSV file, you will be able to choose a device configuration.</span></span> <span data-ttu-id="09594-159">詳細については、「 [Surface Hub 2s のプロビジョニングパッケージの作成](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09594-159">For more information, refer to [Create provisioning packages for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file).</span></span>


    ![\* 構成ファイルからデバイスアカウントとフレンドリ名を選択します \*](images/sh2-run14.png) <br>

4. <span data-ttu-id="09594-161">指示に従って、初回のセットアップを完了します。</span><span class="sxs-lookup"><span data-stu-id="09594-161">Follow the instructions to complete first time Setup.</span></span>
