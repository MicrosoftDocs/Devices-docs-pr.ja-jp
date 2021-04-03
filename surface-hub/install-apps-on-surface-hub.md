---
title: Microsoft Surface Hub へのアプリのインストール
description: 管理者は、Microsoft ストアまたはビジネス向け Microsoft ストアからアプリをインストールできます。
ms.assetid: 3885CB45-D496-4424-8533-C9E3D0EDFD94
ms.reviewer: ''
manager: laurawi
keywords: アプリのインストール, Microsoft ストア, ビジネス向け Microsoft ストア
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/23/2018
ms.localizationpriority: medium
audience: ITPro
ms.openlocfilehash: a6e791defed4970b9a1940580b5f80bbe4f006a4
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470475"
---
# <a name="install-apps-on-your-microsoft-surface-hub"></a><span data-ttu-id="7a3ad-104">Microsoft Surface Hub へのアプリのインストール</span><span class="sxs-lookup"><span data-stu-id="7a3ad-104">Install apps on your Microsoft Surface Hub</span></span>

<span data-ttu-id="7a3ad-105">チームまたは組織のニーズに合わせて、Surface Hub に追加のアプリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-105">You can install additional apps on your Surface Hub to fit your team or organization's needs.</span></span> <span data-ttu-id="7a3ad-106">アプリの開発やテストを行うか、リリースされたアプリを展開するかによって、アプリをインストールするための方法は異なります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-106">There are different methods for installing apps depending on whether you are developing and testing an app, or deploying a released app.</span></span> <span data-ttu-id="7a3ad-107">このトピックでは、それぞれのシナリオ向けにアプリをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-107">This topic describes methods for installing apps for either scenario.</span></span>

<span data-ttu-id="7a3ad-108">Surface Hub でのアプリについては、次のような注意点があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-108">A few things to know about apps on Surface Hub:</span></span>
- <span data-ttu-id="7a3ad-109">Surface Hub で実行できるのは、[ユニバーサル Windows プラットフォーム (UWP) アプリ](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp)のみです。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-109">Surface Hub only runs [Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp).</span></span> <span data-ttu-id="7a3ad-110">[Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) を使用して作成されたアプリは、Surface Hub では動作しません。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-110">Apps created using the [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) will not run on Surface Hub.</span></span>
- <span data-ttu-id="7a3ad-111">アプリは、[ユニバーサル デバイス ファミリ](https://msdn.microsoft.com/library/windows/apps/dn894631)または Windows チーム デバイス ファミリに対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-111">Apps must be targeted for the [Universal device family](https://msdn.microsoft.com/library/windows/apps/dn894631) or Windows Team device family.</span></span>
- <span data-ttu-id="7a3ad-112">Surface Hub [は、Microsoft](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) Store for Business からのオフライン [ライセンス アプリのみをサポートします](https://businessstore.microsoft.com/store)。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-112">Surface Hub only supports [offline-licensed apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) from [Microsoft Store for Business](https://businessstore.microsoft.com/store).</span></span>
- <span data-ttu-id="7a3ad-113">既定では、アプリをインストールするには、アプリにストアの署名が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-113">By default, apps must be Store-signed to be installed.</span></span> <span data-ttu-id="7a3ad-114">テストおよび開発時には、開発者モードでデバイスを配置することによって、開発者が署名した UWP アプリの実行を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-114">During testing and development, you can also choose to run developer-signed UWP apps by placing the device in developer mode.</span></span>
- <span data-ttu-id="7a3ad-115">Microsoft Store にアプリを提出する場合、開発者はデバイス ファミリの可用性と組織のライセンス オプションを設定して、Surface Hub でアプリを実行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-115">When submitting an app to the Microsoft Store, developers need to set Device family availability and Organizational licensing options to make sure an app will be available to run on Surface Hub.</span></span>
- <span data-ttu-id="7a3ad-116">Surface Hub にアプリをインストールするには、管理者の資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-116">You need admin credentials to install apps on your Surface Hub.</span></span> <span data-ttu-id="7a3ad-117">このデバイスは、会議室などの共同スペースで使用するよう設計されているため、ユーザーが Microsoft ストアにアクセスし、アプリをダウンロードしてインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-117">Since the device is designed to be used in communal spaces like meeting rooms, people can't access the Microsoft Store to download and install apps.</span></span>


## <a name="develop-and-test-apps"></a><span data-ttu-id="7a3ad-118">アプリを開発およびテストする</span><span class="sxs-lookup"><span data-stu-id="7a3ad-118">Develop and test apps</span></span>
<span data-ttu-id="7a3ad-119">独自のアプリの開発時に Surface Hub 上のアプリをテストするためのオプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-119">While you're developing your own app, there are a few options for testing apps on Surface Hub.</span></span>

### <a name="developer-mode"></a><span data-ttu-id="7a3ad-120">開発者モード</span><span class="sxs-lookup"><span data-stu-id="7a3ad-120">Developer Mode</span></span>
<span data-ttu-id="7a3ad-121">既定では、Surface Hub は、Microsoft ストアに公開され、Microsoft ストアによって署名された UWP アプリのみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-121">By default, Surface Hub only runs UWP apps that have been published to and signed by the Microsoft Store.</span></span> <span data-ttu-id="7a3ad-122">Microsoft ストアに提出するアプリは、[アプリの認定プロセス](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process)の一環として、セキュリティとコンプライアンスのテストに合格している必要があります。これにより、Surface Hub を悪意のあるアプリから保護できます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-122">Apps submitted to the Microsoft Store go through security and compliance tests as part of the [app certification process](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process), so this helps safeguard your Surface Hub against malicious apps.</span></span>
 
<span data-ttu-id="7a3ad-123">開発者モードを有効にすると、開発者が署名した UWP アプリをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-123">By enabling developer mode, you can also install developer-signed UWP apps.</span></span>
 
> [!IMPORTANT]
> <span data-ttu-id="7a3ad-124">開発者モードを有効にした後、これを無効にするには、Surface Hub をリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-124">After developer mode has been enabled, you will need to reset the Surface Hub to disable it.</span></span> <span data-ttu-id="7a3ad-125">デバイスをリセットすると、すべてのローカル ユーザーのファイルと構成が削除され、Windows が再インストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-125">Resetting the device removes all local user files and configurations and then reinstalls Windows.</span></span>

**<span data-ttu-id="7a3ad-126">開発者モードを有効にするには</span><span class="sxs-lookup"><span data-stu-id="7a3ad-126">To turn on developer mode</span></span>** 
1. <span data-ttu-id="7a3ad-127">Surface Hub から、**[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-127">From your Surface Hub, start **Settings**.</span></span>
2. <span data-ttu-id="7a3ad-128">メッセージが表示されたら、デバイスの管理者資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-128">Type the device admin credentials when prompted.</span></span>
3. <span data-ttu-id="7a3ad-129">**[更新プログラムとセキュリティ]** > **[開発者向け]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-129">Navigate to **Update & security** > **For developers**.</span></span>
4. <span data-ttu-id="7a3ad-130">**[開発者モード]** を選択し、警告メッセージに同意します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-130">Select **Developer mode** and accept the warning prompt.</span></span>

### <a name="visual-studio"></a><span data-ttu-id="7a3ad-131">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a3ad-131">Visual Studio</span></span>
<span data-ttu-id="7a3ad-132">開発中に、Surface Hub でアプリをテストする最も簡単な方法は、Visual Studio を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-132">During development, the easiest way to test your app on a Surface Hub is using Visual Studio.</span></span> <span data-ttu-id="7a3ad-133">Visual Studio のリモート デバッグ機能は、広く展開する前に、アプリで問題を見つけるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-133">Visual Studio's remote debugging feature helps you discover issues in your app before deploying it broadly.</span></span> <span data-ttu-id="7a3ad-134">詳しくは、「[Visual Studio を使った Surface Hub アプリのテスト](https://msdn.microsoft.com/windows/uwp/debug-test-perf/test-surface-hub-apps-using-visual-studio)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-134">For more information, see [Test Surface Hub apps using Visual Studio](https://msdn.microsoft.com/windows/uwp/debug-test-perf/test-surface-hub-apps-using-visual-studio).</span></span>

### <a name="provisioning-package"></a><span data-ttu-id="7a3ad-135">プロビジョニング パッケージ</span><span class="sxs-lookup"><span data-stu-id="7a3ad-135">Provisioning package</span></span>
<span data-ttu-id="7a3ad-136">Visual Studio を使用して、テスト証明書で署名された、UWP アプリ用の[アプリ パッケージを作成](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-136">Use Visual Studio to [create an app package](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) for your UWP app, signed using a test certificate.</span></span> <span data-ttu-id="7a3ad-137">Windows イメージングおよび構成デザイナー (ICD) を使用して、アプリ パッケージを含むプロビジョニング パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-137">Then use Windows Imaging and Configuration Designer (ICD) to create a provisioning package containing the app package.</span></span> <span data-ttu-id="7a3ad-138">詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-138">For more information, see [Create provisioning packages](provisioning-packages-for-certificates-surface-hub.md).</span></span>


## <a name="submit-apps-to-the-microsoft-store"></a><span data-ttu-id="7a3ad-139">Microsoft ストアにアプリを提出する</span><span class="sxs-lookup"><span data-stu-id="7a3ad-139">Submit apps to the Microsoft Store</span></span>
<span data-ttu-id="7a3ad-140">アプリのリリースの準備ができたら、開発者は、Microsoft ストアにアプリを提出し、公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-140">Once an app is ready for release, developers need to submit and publish it to the Microsoft Store.</span></span> <span data-ttu-id="7a3ad-141">詳しくは、「[Windows アプリの公開](https://developer.microsoft.com/store/publish-apps)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-141">For more information, see [Publish Windows apps](https://developer.microsoft.com/store/publish-apps).</span></span>

<span data-ttu-id="7a3ad-142">アプリの提出時に、開発者は、アプリが Surface Hub で確実に実行できるように、**[デバイス ファミリの利用可否]** オプションと **[組織のライセンス]** オプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-142">During app submission, developers need to set **Device family availability** and **Organizational licensing** options to make sure the app will be available to run on Surface Hub.</span></span>

**<span data-ttu-id="7a3ad-143">デバイス ファミリの利用可否を設定するには</span><span class="sxs-lookup"><span data-stu-id="7a3ad-143">To set device family availability</span></span>**

1. <span data-ttu-id="7a3ad-144">[Windows デベロッパー センター](https://developer.microsoft.com)のアプリの申請ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-144">On the [Windows Dev Center](https://developer.microsoft.com), navigate to your app submission page.</span></span>

2. <span data-ttu-id="7a3ad-145">**[パッケージ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-145">Select **Packages**.</span></span>
3. <span data-ttu-id="7a3ad-146">**[デバイス ファミリの利用可否]** で、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-146">Under **Device family availability**, select these options:</span></span>
    
    - **<span data-ttu-id="7a3ad-147">Windows 10 Team</span><span class="sxs-lookup"><span data-stu-id="7a3ad-147">Windows 10 Team</span></span>**
    - **<span data-ttu-id="7a3ad-148">[このアプリを将来のデバイス ファミリで使用できるようにするかどうかをマイクロソフトが決定できる]</span><span class="sxs-lookup"><span data-stu-id="7a3ad-148">Let Microsoft decide whether to make the app available to any future device families</span></span>**
  
   ![[デバイス ファミリの利用可否] ページ (Microsoft ストア アプリの申請プロセスの一部) を示す画像。](images/device-family.png)  
    
   <span data-ttu-id="7a3ad-150">詳しくは、「[デバイス ファミリの利用可否](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages#device-family-availability)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-150">For more information, see [Device family availability](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages#device-family-availability).</span></span>

**<span data-ttu-id="7a3ad-151">組織のライセンスを設定するには</span><span class="sxs-lookup"><span data-stu-id="7a3ad-151">To set organizational licensing</span></span>**

1. <span data-ttu-id="7a3ad-152">[Windows デベロッパー センター](https://developer.microsoft.com)のアプリの申請ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-152">On the [Windows Dev Center](https://developer.microsoft.com), navigate to your app submission page.</span></span>

2. <span data-ttu-id="7a3ad-153">**[価格と使用可能状況]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-153">Select **Pricing and availability**.</span></span>

3. <span data-ttu-id="7a3ad-154">[組織のライセンス] の **[組織による未接続状態 (オフライン) でのライセンスの購入を許可する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-154">Under Organizational licensing, select **Allow disconnected (offline) licensing for organizations**.</span></span>

   ![[組織のライセンス] ページ (Microsoft ストア アプリの申請プロセスの一部) を示す画像。](images/sh-org-licensing.png)

   > [!NOTE]
   > <span data-ttu-id="7a3ad-156">**[ストアで管理される (オンライン) ボリューム ライセンスと配布に基づいて組織がこのアプリを購入できるようにする]** チェック ボックスは既定でオンになっています。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-156">**Make my app available to organizations with Store-managed (online) licensing and distribution** is selected by default.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7a3ad-157">開発者は、基幹業務アプリを企業に直接公開することもできます。アプリをストアで一般公開する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-157">Developers can also publish line-of-business apps directly to enterprises without making them broadly available in the Store.</span></span> <span data-ttu-id="7a3ad-158">詳しくは、「[LOB アプリの企業への配布](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-158">For more information, see [Distribute LOB apps to enterprises](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises).</span></span>

   <span data-ttu-id="7a3ad-159">詳しくは、「[組織のライセンス オプション](https://msdn.microsoft.com/windows/uwp/publish/organizational-licensing)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-159">For more information, see [Organizational licensing options](https://msdn.microsoft.com/windows/uwp/publish/organizational-licensing).</span></span>


## <a name="deploy-released-apps"></a><span data-ttu-id="7a3ad-160">リリースされたアプリを展開する</span><span class="sxs-lookup"><span data-stu-id="7a3ad-160">Deploy released apps</span></span>

<span data-ttu-id="7a3ad-161">いくつかのデバイスでアプリを評価するか、または組織に広くアプリを展開するかに応じて、Microsoft ストアにリリースされているアプリをインストールする方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-161">There are several options for installing apps that have been released to the Microsoft Store, depending on whether you want to evaluate them on a few devices, or deploy them broadly to your organization.</span></span>

<span data-ttu-id="7a3ad-162">リリースされたアプリをインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-162">To install released apps:</span></span>
- <span data-ttu-id="7a3ad-163">Microsoft ストア アプリを使ってアプリをダウンロードする、または</span><span class="sxs-lookup"><span data-stu-id="7a3ad-163">Download the app using the Microsoft Store app, or</span></span>
- <span data-ttu-id="7a3ad-164">ビジネス向け Microsoft ストアからアプリ パッケージをダウンロードし、プロビジョニング パッケージまたはサポートされている MDM プロバイダーを使用して配布する。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-164">Download the app package from the Microsoft Store for Business, and distribute it using a provisioning package or a supported MDM provider.</span></span>

### <a name="microsoft-store-app"></a><span data-ttu-id="7a3ad-165">Microsoft ストア アプリ</span><span class="sxs-lookup"><span data-stu-id="7a3ad-165">Microsoft Store app</span></span>
<span data-ttu-id="7a3ad-166">Microsoft ストアにリリースされたアプリを評価するには、Surface Hub で Microsoft ストア アプリを使ってアプリを参照し、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-166">To evaluate apps released on the Microsoft Store, use the Microsoft Store app on the Surface Hub to browse and download apps.</span></span>

> [!NOTE]
> <span data-ttu-id="7a3ad-167">Microsoft ストア アプリを使用する方法は、組織にアプリを大規模に展開する場合はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-167">Using the Microsoft Store app is not the recommended method of deploying apps at scale to your organization:</span></span>
> - <span data-ttu-id="7a3ad-168">アプリをダウンロードするには、Microsoft アカウントまたは組織のアカウントを使って Microsoft ストア アプリにサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-168">To download apps, you must sign in to the Microsoft Store app with a Microsoft account or organizational account.</span></span> <span data-ttu-id="7a3ad-169">ただし、1 つのアカウントで接続できるのは最大 10 台のデバイスのみです。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-169">However, you can only connect an account to a maximum of 10 devices at once.</span></span> <span data-ttu-id="7a3ad-170">10 台以上の Surface Hub がある場合は、複数のアカウントを作成するか、アプリのインストールが終了するたびにアカウントからデバイスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-170">If you have more than 10 Surface Hubs, you will need to create multiple accounts or remove devices from your account between app installations.</span></span>
> - <span data-ttu-id="7a3ad-171">アプリをインストールするには、自分が所有する各 Surface Hub で手動で Microsoft ストア アプリにサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-171">To install apps, you will need to manually sign in to the Microsoft Store app on each Surface Hub you own.</span></span>

**<span data-ttu-id="7a3ad-172">Surface Hub で Microsoft ストアを参照するには</span><span class="sxs-lookup"><span data-stu-id="7a3ad-172">To browse the Microsoft Store on Surface Hub</span></span>** 
1. <span data-ttu-id="7a3ad-173">Surface Hub から、**[設定]** を起動します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-173">From your Surface Hub, start **Settings**.</span></span>
2. <span data-ttu-id="7a3ad-174">メッセージが表示されたら、デバイスの管理者資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-174">Type the device admin credentials when prompted.</span></span>
3. <span data-ttu-id="7a3ad-175">**[このデバイス]** > **[アプリと機能]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-175">Navigate to **This device** > **Apps & features**.</span></span>
4. <span data-ttu-id="7a3ad-176">**[ストアを開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-176">Select **Open Store**.</span></span>

### <a name="download-app-packages-from-microsoft-store-for-business"></a><span data-ttu-id="7a3ad-177">ビジネス向け Microsoft ストアからアプリ パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7a3ad-177">Download app packages from Microsoft Store for Business</span></span>
<span data-ttu-id="7a3ad-178">必要なアプリ パッケージをダウンロードして Surface Hub にアプリをインストールするには、[ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-178">To download the app package you need to install apps on your Surface Hub, visit the [Microsoft Store for Business](https://www.microsoft.com/business-store).</span></span> <span data-ttu-id="7a3ad-179">ビジネス向けストアは、Surface Hub を含め、組織内の Windows 10デバイス用のアプリの検索、取得、管理を行うことができる場所です。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-179">The Store for Business is where you can find, acquire, and manage apps for the Windows 10 devices in your organization, including Surface Hub.</span></span>
 
> [!NOTE]
> <span data-ttu-id="7a3ad-180">現在、Surface Hub は、ビジネス向けストアで利用可能なオフライン ライセンスのアプリのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-180">Currently, Surface Hub only supports offline-licensed apps available through the Store for Business.</span></span> <span data-ttu-id="7a3ad-181">アプリの開発者は、アプリを提出するときに、オフライン ライセンスを利用できるかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-181">App developers set offline-license availability when they submit apps.</span></span>

<span data-ttu-id="7a3ad-182">必要なアプリを検索して入手し、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-182">Find and acquire the app you want, then download:</span></span>
- <span data-ttu-id="7a3ad-183">オフライン ライセンスのアプリ パッケージ (.appx または .appxbundle)</span><span class="sxs-lookup"><span data-stu-id="7a3ad-183">The offline-licensed app package (either an .appx or an .appxbundle)</span></span>
- <span data-ttu-id="7a3ad-184">*エンコードされていない*ライセンス ファイル (プロビジョニング パッケージを使ってアプリをインストールする場合)</span><span class="sxs-lookup"><span data-stu-id="7a3ad-184">The *unencoded* license file (if you're using provisioning packages to install the app)</span></span>
- <span data-ttu-id="7a3ad-185">*エンコード*されたライセンス ファイル (MDM を使ってアプリを配布する場合)</span><span class="sxs-lookup"><span data-stu-id="7a3ad-185">The *encoded* license file (if you're using MDM to distribute the app)</span></span>
- <span data-ttu-id="7a3ad-186">必要な依存関係ファイル</span><span class="sxs-lookup"><span data-stu-id="7a3ad-186">Any necessary dependency files</span></span>

<span data-ttu-id="7a3ad-187">詳しくは、[オフライン ライセンス アプリのダウンロードに関するページ](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-187">For more information, see [Download an offline-licensed app](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app).</span></span>

### <a name="provisioning-package"></a><span data-ttu-id="7a3ad-188">プロビジョニング パッケージ</span><span class="sxs-lookup"><span data-stu-id="7a3ad-188">Provisioning package</span></span>
<span data-ttu-id="7a3ad-189">プロビジョニング パッケージを使って、数台の Surface Hub に、ビジネス向けストアからダウンロードしたオフライン ライセンス アプリを手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-189">You can manually install the offline-licensed apps that you downloaded from the Store for Business on a few Surface Hubs using provisioning packages.</span></span> <span data-ttu-id="7a3ad-190">Windows イメージングおよび構成デザイナー (ICD) を使って、ビジネス向けストアからダウンロードしたアプリ パッケージと*エンコードされていない*ライセンス ファイルを含むプロビジョニング パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-190">Use Windows Imaging and Configuration Designer (ICD) to create a provisioning package containing the app package and *unencoded* license file that you downloaded from the Store for Business.</span></span> <span data-ttu-id="7a3ad-191">詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-191">For more information, see [Create provisioning packages](provisioning-packages-for-certificates-surface-hub.md).</span></span>

### <a name="supported-mdm-provider"></a><span data-ttu-id="7a3ad-192">サポートされる MDM プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7a3ad-192">Supported MDM provider</span></span>
<span data-ttu-id="7a3ad-193">組織内の多くの Surface Hub にアプリを展開するには、サポートされているMDMプロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-193">To deploy apps to a large number of Surface Hubs in your organization, use a supported MDM provider.</span></span> <span data-ttu-id="7a3ad-194">次の表は、オフライン ライセンスのアプリ パッケージの展開をサポートする MDM プロバイダーを示しています。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-194">The table below shows which MDM providers support deploying offline-licensed app packages.</span></span>

| <span data-ttu-id="7a3ad-195">MDM プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7a3ad-195">MDM provider</span></span>                | <span data-ttu-id="7a3ad-196">オフライン ライセンスのアプリ パッケージのサポート</span><span class="sxs-lookup"><span data-stu-id="7a3ad-196">Supports offline-licensed app packages</span></span> |
|-----------------------------|----------------------------------------|
| <span data-ttu-id="7a3ad-197">Configuration Manager を使用したオンプレミス MDM (バージョン 1602 から)</span><span class="sxs-lookup"><span data-stu-id="7a3ad-197">On-premises MDM with  Configuration Manager (beginning in version 1602)</span></span> | <span data-ttu-id="7a3ad-198">あり</span><span class="sxs-lookup"><span data-stu-id="7a3ad-198">Yes</span></span> |
|
| <span data-ttu-id="7a3ad-199">サードパーティの MDM プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7a3ad-199">Third-party MDM provider</span></span>    | <span data-ttu-id="7a3ad-200">MDM プロバイダーがオフライン ライセンスのアプリ パッケージの展開をサポートしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-200">Check to make sure your MDM provider supports deploying offline-licensed app packages.</span></span> |

**<span data-ttu-id="7a3ad-201">Microsoft Endpoint Configuration Manager を使用してアプリをリモートで展開するには</span><span class="sxs-lookup"><span data-stu-id="7a3ad-201">To deploy apps remotely using Microsoft Endpoint Configuration Manager</span></span>**

> [!NOTE]
> <span data-ttu-id="7a3ad-202">これらの手順は、Microsoft Endpoint Configuration Manager の現在のブランチに基づいて行います。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-202">These instructions are based on the current branch of Microsoft Endpoint Configuration Manager.</span></span>

1. <span data-ttu-id="7a3ad-203">Surface Hubs を MDM 管理に登録します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-203">Enroll your Surface Hubs into MDM management.</span></span> <span data-ttu-id="7a3ad-204">詳細については、「MDM プロバイダーを [使用して Surface Hub を管理する」を参照してください](manage-settings-with-mdm-for-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-204">For more information, see [Manage Surface Hub with an MDM provider](manage-settings-with-mdm-for-surface-hub.md).</span></span>

2. <span data-ttu-id="7a3ad-205">オフライン ライセンスのアプリ パッケージ、*エンコードされた*ライセンス ファイル、必要な依存関係ファイルを、ビジネス向けストアからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-205">Download the offline-licensed app package, the *encoded* license file, and any necessary dependency files from the Store for Business.</span></span> <span data-ttu-id="7a3ad-206">詳しくは、[オフライン ライセンス アプリのダウンロードに関するページ](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-206">For more information, see [Download an offline-licensed app](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app).</span></span> <span data-ttu-id="7a3ad-207">ネットワーク共有上の同じフォルダーにダウンロードしたファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-207">Place the downloaded files in the same folder on a network share.</span></span>

3. <span data-ttu-id="7a3ad-208">Configuration Manager コンソールの **[ソフトウェア ライブラリ]** ワークスペースで、**[概要]** > **[アプリケーション管理]** > **[アプリケーション]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-208">In the **Software Library** workspace of the Configuration Manager console, click **Overview** > **Application Management** > **Applications**.</span></span>

4. <span data-ttu-id="7a3ad-209">**[ホーム]** タブの **[作成]** グループで、**[アプリケーションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-209">On the **Home** tab, in the **Create** group, click **Create Application**.</span></span>

5. <span data-ttu-id="7a3ad-210">**アプリケーションの作成ウィザード**の **[全般]** ページで、**[このアプリケーションの情報をインストール ファイルから自動的に検出する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-210">On the **General** page of the **Create Application Wizard**, select the **Automatically detect information about this application from installation files** check box.</span></span>

6. <span data-ttu-id="7a3ad-211">**[種類]** ドロップダウン リストで、**[Windows アプリ パッケージ (\*.appx、\*.appxbundle)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-211">In the **Type** drop-down list, select **Windows app package (\*.appx, \*.appxbundle)**.</span></span>

7. <span data-ttu-id="7a3ad-212">**[場所]** フィールドで、ビジネス向けストアからダウンロードしたオフライン ライセンスのアプリ パッケージの UNC パスを、\\server\share\\filename の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-212">In the **Location** field, specify the UNC path in the form \\server\share\\filename for the offline-licensed app package that you downloaded from the Store for Business.</span></span> <span data-ttu-id="7a3ad-213">または、**[参照]** をクリックしてアプリ パッケージを参照します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-213">Alternatively, click **Browse** to browse to the app package.</span></span>

8. <span data-ttu-id="7a3ad-214">**[情報のインポート]** ページで、インポートされた情報を確認し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-214">On the **Import Information** page, review the information that was imported, and then click **Next**.</span></span> <span data-ttu-id="7a3ad-215">必要に応じて、**[前へ]** をクリックして戻り、エラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-215">If necessary, you can click **Previous** to go back and correct any errors.</span></span>

9. <span data-ttu-id="7a3ad-216">**[一般情報]** ページで、アプリに関する追加の詳細情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-216">On the **General Information** page, complete additional details about the app.</span></span> <span data-ttu-id="7a3ad-217">アプリ パッケージから自動的に取得された場合、この情報の一部は既に入力されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-217">Some of this information might already be populated if it was automatically obtained from the app package.</span></span>

10. <span data-ttu-id="7a3ad-218">**[次へ]** をクリックし、[概要] ページでアプリケーションの情報を確認し、アプリケーションの作成ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-218">Click **Next**, review the application information on the Summary page, and then complete the Create Application Wizard.</span></span> 

11. <span data-ttu-id="7a3ad-219">アプリケーションの展開の種類を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-219">Create a deployment type for the application.</span></span> <span data-ttu-id="7a3ad-220">詳しくは、[アプリケーションの展開の種類の作成に関するページ](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-220">For more information, see [Create deployment types for the application](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).</span></span>

12. <span data-ttu-id="7a3ad-221">Surface Hub にアプリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-221">Deploy the application to your Surface Hubs.</span></span> <span data-ttu-id="7a3ad-222">詳細については [、「Deploy applications with Microsoft Endpoint Configuration Manager」を参照してください](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-222">For more information, see [Deploy applications with Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications).</span></span>

13. <span data-ttu-id="7a3ad-223">必要に応じて、ビジネス向けストアから新しいパッケージをダウンロードし、Configuration Managerでアプリケーションのリビジョンを発行することによって、アプリを更新します。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-223">As needed, update the app by downloading a new package from the Store for Business, and publishing an application revision in Configuration Manager.</span></span> <span data-ttu-id="7a3ad-224">詳細については [、「Update and retire applications with Microsoft Endpoint Configuration Manager」を参照してください](https://technet.microsoft.com/library/mt595704.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-224">For more information, see [Update and retire applications with Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt595704.aspx).</span></span> 

> [!NOTE] 
> <span data-ttu-id="7a3ad-225">Microsoft Endpoint Configuration Manager (現在のブランチ) を使用している場合は、Store for Business を Configuration Manager に接続することで、上記の手順をバイパスできます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-225">If you are using Microsoft Endpoint Configuration Manager (current branch), you can bypass the above steps by connecting the Store for Business to Configuration Manager.</span></span> <span data-ttu-id="7a3ad-226">これにより、購入したアプリの一覧を Configuration Manager と同期し、Configuration Manager コンソールで表示し、他のアプリと同様に展開できます。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-226">By doing so, you can synchronize the list of apps you've purchased with Configuration Manager, view these in the Configuration Manager console, and deploy them like you would any other app.</span></span> <span data-ttu-id="7a3ad-227">詳細については、「Configuration Manager を使用して Microsoft Store for Business から [アプリを管理する」を参照してください](https://technet.microsoft.com/library/mt740630.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-227">For more information, see [Manage apps from the Microsoft Store for Business with Configuration Manager](https://technet.microsoft.com/library/mt740630.aspx).</span></span>


## <a name="summary"></a><span data-ttu-id="7a3ad-228">要約</span><span class="sxs-lookup"><span data-stu-id="7a3ad-228">Summary</span></span>

<span data-ttu-id="7a3ad-229">Surface Hub にアプリをインストールする方法は、アプリの開発、少数のデバイスでのアプリの評価、または組織へのアプリの広範な展開によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-229">There are a few different ways to install apps on your Surface Hub depending on whether you are developing apps, evaluating apps on a small number of devices, or deploying apps broadly to your organization.</span></span> <span data-ttu-id="7a3ad-230">次の表はサポートされる方法をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7a3ad-230">This table summarizes the supported methods:</span></span>

| <span data-ttu-id="7a3ad-231">インストール方法</span><span class="sxs-lookup"><span data-stu-id="7a3ad-231">Install method</span></span>             | <span data-ttu-id="7a3ad-232">アプリの開発</span><span class="sxs-lookup"><span data-stu-id="7a3ad-232">Developing apps</span></span> | <span data-ttu-id="7a3ad-233">少数のデバイスでの</span><span class="sxs-lookup"><span data-stu-id="7a3ad-233">Evaluating apps on</span></span> <br> <span data-ttu-id="7a3ad-234">アプリの評価</span><span class="sxs-lookup"><span data-stu-id="7a3ad-234">a few devices</span></span> | <span data-ttu-id="7a3ad-235">組織での大規模な</span><span class="sxs-lookup"><span data-stu-id="7a3ad-235">Deploying apps broadly</span></span> <br> <span data-ttu-id="7a3ad-236">アプリの展開</span><span class="sxs-lookup"><span data-stu-id="7a3ad-236">to your organization</span></span> |
| -------------------------- | --------------- | ------------------------------------- | ---------------------- |
| <span data-ttu-id="7a3ad-237">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a3ad-237">Visual Studio</span></span>              | <span data-ttu-id="7a3ad-238">○</span><span class="sxs-lookup"><span data-stu-id="7a3ad-238">X</span></span> |   |   |
| <span data-ttu-id="7a3ad-239">プロビジョニング パッケージ</span><span class="sxs-lookup"><span data-stu-id="7a3ad-239">Provisioning package</span></span>       | <span data-ttu-id="7a3ad-240">○</span><span class="sxs-lookup"><span data-stu-id="7a3ad-240">X</span></span> | <span data-ttu-id="7a3ad-241">○</span><span class="sxs-lookup"><span data-stu-id="7a3ad-241">X</span></span> |   |
| <span data-ttu-id="7a3ad-242">Microsoft ストア アプリ</span><span class="sxs-lookup"><span data-stu-id="7a3ad-242">Microsoft Store app</span></span>          |   | <span data-ttu-id="7a3ad-243">○</span><span class="sxs-lookup"><span data-stu-id="7a3ad-243">X</span></span> |   |
| <span data-ttu-id="7a3ad-244">サポートされる MDM プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7a3ad-244">Supported MDM provider</span></span>     |   |   | <span data-ttu-id="7a3ad-245">○</span><span class="sxs-lookup"><span data-stu-id="7a3ad-245">X</span></span> |

## <a name="more-information"></a><span data-ttu-id="7a3ad-246">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7a3ad-246">More information</span></span>

- [<span data-ttu-id="7a3ad-247">ブログの投稿: Intune を使用して Surface Hub に Windows ストア アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="7a3ad-247">Blog post:  Deploy Windows Store apps to Surface Hub using Intune</span></span>](https://blogs.technet.microsoft.com/y0av/2018/01/18/7-2/)


## <a name="related-topics"></a><span data-ttu-id="7a3ad-248">関連トピック</span><span class="sxs-lookup"><span data-stu-id="7a3ad-248">Related topics</span></span>

[<span data-ttu-id="7a3ad-249">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="7a3ad-249">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="7a3ad-250">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="7a3ad-250">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

 

 





