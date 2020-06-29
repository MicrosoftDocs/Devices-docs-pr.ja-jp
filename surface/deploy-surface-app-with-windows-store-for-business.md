---
title: Microsoft Store for Business または Microsoft ストア (教育機関向け) を使用した Surface アプリの展開 (Surface)
description: 教育機関向け Microsoft Store for Business または Microsoft ストアで Surface アプリを追加してダウンロードする方法、および PowerShell と MDT を使ったインストール Surface アプリについて説明します。
keywords: surface アプリ、アプリ、展開、カスタマイズ
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, store
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: e25e146de49110dca1fea797f9630d9fa2d953e3
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835125"
---
# <span data-ttu-id="141e2-104">一般法人向けおよび教育機関向け Microsoft Store で Surface アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="141e2-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="141e2-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="141e2-105">Applies to</span></span>**

- <span data-ttu-id="141e2-106">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="141e2-106">Surface Pro 7</span></span>
- <span data-ttu-id="141e2-107">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="141e2-107">Surface Laptop 3</span></span>
- <span data-ttu-id="141e2-108">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="141e2-108">Surface Pro 6</span></span>
- <span data-ttu-id="141e2-109">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="141e2-109">Surface Laptop 2</span></span>
- <span data-ttu-id="141e2-110">Surface Go</span><span class="sxs-lookup"><span data-stu-id="141e2-110">Surface Go</span></span>
- <span data-ttu-id="141e2-111">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="141e2-111">Surface Go with LTE</span></span>
- <span data-ttu-id="141e2-112">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="141e2-112">Surface Book 2</span></span>
- <span data-ttu-id="141e2-113">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="141e2-113">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="141e2-114">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="141e2-114">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="141e2-115">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="141e2-115">Surface Laptop</span></span>
- <span data-ttu-id="141e2-116">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="141e2-116">Surface Studio</span></span>
- <span data-ttu-id="141e2-117">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="141e2-117">Surface Studio 2</span></span>
- <span data-ttu-id="141e2-118">Surface Book</span><span class="sxs-lookup"><span data-stu-id="141e2-118">Surface Book</span></span>
- <span data-ttu-id="141e2-119">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="141e2-119">Surface Pro 4</span></span>
- <span data-ttu-id="141e2-120">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="141e2-120">Surface 3 LTE</span></span>
- <span data-ttu-id="141e2-121">Surface 3</span><span class="sxs-lookup"><span data-stu-id="141e2-121">Surface 3</span></span>
- <span data-ttu-id="141e2-122">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="141e2-122">Surface Pro 3</span></span>


<span data-ttu-id="141e2-123">Surface アプリは、次のようなさまざまなサーフェス固有の設定とオプションを管理するための、軽量の Microsoft Store アプリです。</span><span class="sxs-lookup"><span data-stu-id="141e2-123">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="141e2-124">Surface デバイスの Windows ボタンを有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="141e2-124">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="141e2-125">Surface ペンの感度を調整する
</span><span class="sxs-lookup"><span data-stu-id="141e2-125">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="141e2-126">Surface ペンのボタンの操作をカスタマイズする
</span><span class="sxs-lookup"><span data-stu-id="141e2-126">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="141e2-127">Surface のオーディオ拡張機能を有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="141e2-127">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="141e2-128">デバイスのサポートドキュメントと情報にすばやくアクセスする</span><span class="sxs-lookup"><span data-stu-id="141e2-128">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="141e2-129">Windows Update を使用しているユーザーは、通常、自動更新の一部として Surface アプリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="141e2-129">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="141e2-130">ただし、組織で Surface デバイスへの展開用のイメージを準備している場合は、個々のデバイスのユーザーに対して、Microsoft ストアまたは Microsoft Store からアプリをダウンロードしてインストールするのではなく、イメージと展開プロセスに Surface アプリ (旧称 Surface Hub) を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="141e2-130">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="141e2-131">この記事は Surface Pro X には適用されません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141e2-131">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <span data-ttu-id="141e2-132">Surface アプリの概要</span><span class="sxs-lookup"><span data-stu-id="141e2-132">Surface app overview</span></span>

<span data-ttu-id="141e2-133">Surface アプリは、 [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="141e2-133">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="141e2-134">ユーザーは Microsoft ストアからダウンロードしてインストールできますが、組織で一般法人向け Microsoft Store を使用している場合は、アプリをストアのインベントリに追加して、Windows 展開プロセスの一部としてアプリを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="141e2-134">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="141e2-135">これらのプロセスについては、この記事を通して説明します。</span><span class="sxs-lookup"><span data-stu-id="141e2-135">These processes are discussed throughout this article.</span></span> <span data-ttu-id="141e2-136">一般法人向け Microsoft Store の詳細については、「Windows TechCenter で一般[法人向け Microsoft store](https://docs.microsoft.com/microsoft-store/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141e2-136">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <span data-ttu-id="141e2-137">Microsoft Store for Business アカウントに Surface アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="141e2-137">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="141e2-138">ユーザーが会社の Microsoft ストアのビジネスアカウントを使用してアプリをインストールまたは展開する前に、必要なアプリを最初に利用可能にして、ビジネスユーザーに対してライセンスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="141e2-138">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="141e2-139">[ビジネスアカウント用に Microsoft Store](https://www.microsoft.com/business-store)をまだ作成していない場合は、作成します。</span><span class="sxs-lookup"><span data-stu-id="141e2-139">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="141e2-140">ポータルにログオンします。</span><span class="sxs-lookup"><span data-stu-id="141e2-140">Log on to the portal.</span></span> 

3. <span data-ttu-id="141e2-141">[オフラインライセンスを有効にする]: [管理]、[ **>ストアの設定**] の順にクリックし、[**オフラインライセンス**を持つアプリをストアに表示する] チェックボックスをオンにします (図1のように)。</span><span class="sxs-lookup"><span data-stu-id="141e2-141">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="141e2-142">一般法人向け Microsoft Store for Business アプリのライセンスモデルの詳細については、「一般[法人向け Microsoft store のアプリ](https://docs.microsoft.com/microsoft-store/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141e2-142">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span><br/> <br/>
   ![[オフラインライセンスアプリの表示] チェックボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="141e2-144">図 1. </span><span class="sxs-lookup"><span data-stu-id="141e2-144">Figure 1.</span></span> <span data-ttu-id="141e2-145">オフラインでのアプリの使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="141e2-145">Enable apps for offline use</span></span>*

4. <span data-ttu-id="141e2-146">次の手順に従って、ビジネスアカウントの Microsoft ストアに Surface アプリを追加します。</span><span class="sxs-lookup"><span data-stu-id="141e2-146">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>
    * <span data-ttu-id="141e2-147">[**ショップ**] メニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-147">Click the **Shop** menu.</span></span>
    * <span data-ttu-id="141e2-148">検索ボックスに「 **Surface app**」と入力し、[検索] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-148">In the search box, type **Surface app**, and then click the search icon.</span></span>
    * <span data-ttu-id="141e2-149">Surface アプリが検索結果に表示されたら、アプリのアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-149">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    * <span data-ttu-id="141e2-150">図2に示すように、選択肢が表示されます ([**オンライン**または**オフライン**] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="141e2-150">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span><br/><br/>
    
    ![オフラインライセンスモードを選択し、アプリをインベントリに追加します。](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")
    
    *<span data-ttu-id="141e2-152">図 2. </span><span class="sxs-lookup"><span data-stu-id="141e2-152">Figure 2.</span></span> <span data-ttu-id="141e2-153">オフラインライセンスモードを選択し、アプリをインベントリに追加します。</span><span class="sxs-lookup"><span data-stu-id="141e2-153">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="141e2-154">[**オフライン**] をクリックして、オフラインライセンスモードを選択します。</span><span class="sxs-lookup"><span data-stu-id="141e2-154">Click **Offline** to select the Offline licensing mode.</span></span>
    * <span data-ttu-id="141e2-155">[**アプリの取得**] をクリックして、アプリを Microsoft Store for Business のインベントリに追加します。</span><span class="sxs-lookup"><span data-stu-id="141e2-155">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="141e2-156">図3に示すように、管理ツールを使用してオフラインアプリを展開できること、またはプライベートストアの会社の在庫ページからダウンロードできることを確認するダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="141e2-156">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
    ![オフライン-ライセンス付与されたアプリ確認ウィンドウ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
    
    *<span data-ttu-id="141e2-158">図 3. </span><span class="sxs-lookup"><span data-stu-id="141e2-158">Figure 3.</span></span> <span data-ttu-id="141e2-159">オフライン-ライセンス付与されたアプリの確認</span><span class="sxs-lookup"><span data-stu-id="141e2-159">Offline-licensed app acknowledgement</span></span>*
    * <span data-ttu-id="141e2-160">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-160">Click **OK**.</span></span>

## <span data-ttu-id="141e2-161">Microsoft Store for Business アカウントから Surface アプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="141e2-161">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="141e2-162">オフラインモードで、ビジネスアカウント用の Microsoft ストアにアプリを追加した後で、アプリをダウンロードして展開共有に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="141e2-162">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>
1. <span data-ttu-id="141e2-163">のビジネスアカウント用の Microsoft ストアにログオン https://businessstore.microsoft.com します。</span><span class="sxs-lookup"><span data-stu-id="141e2-163">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>
2. <span data-ttu-id="141e2-164">[ **Manage >app & software**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-164">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="141e2-165">この記事の「 [surface アプリを Microsoft Store For Business アカウントに追加](#add-surface-app-to-a-microsoft-store-for-business-account)する」で追加した surface アプリなど、すべての会社のアプリの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="141e2-165">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>
3. <span data-ttu-id="141e2-166">[**アクション**] で、省略記号 ([**...**]) をクリックし、[Surface アプリの**オフライン使用のためにダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-166">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>
4. <span data-ttu-id="141e2-167">図4に示すように、選択したアプリで利用可能な**プラットフォーム**と**アーキテクチャ**のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="141e2-167">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    ![.Appxbundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")

    *<span data-ttu-id="141e2-169">図 4: </span><span class="sxs-lookup"><span data-stu-id="141e2-169">Figure 4.</span></span> <span data-ttu-id="141e2-170">アプリの .Appxbundle パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="141e2-170">Download the AppxBundle package for an app</span></span>*
5. <span data-ttu-id="141e2-171">[**ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-171">Click **Download**.</span></span> <span data-ttu-id="141e2-172">.Appxbundle パッケージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="141e2-172">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="141e2-173">この記事で後述する必要があるため、ダウンロードしたファイルのパスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="141e2-173">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>
6. <span data-ttu-id="141e2-174">**エンコード**済みライセンスまたはエンコード済み**ライセンス**オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-174">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="141e2-175">エンコードされたライセンスオプションは、Microsoft Endpoint Configuration Manager などの管理ツールで使用するか、Windows 構成デザイナーを使ってプロビジョニングパッケージを作成するときに使います。</span><span class="sxs-lookup"><span data-stu-id="141e2-175">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="141e2-176">展開イメージのサービスと管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft 展開ツールキット (MDT) を含む) を使用する場合は、[エンコードされていないライセンス] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="141e2-176">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>
7. <span data-ttu-id="141e2-177">[**生成**] をクリックして、アプリのライセンスを生成し、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="141e2-177">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="141e2-178">この記事で後述する必要があるため、ライセンスファイルのパスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="141e2-178">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="141e2-179">Surface アプリなど、オフラインで使用するためのアプリをダウンロードすると、ページの下部にある [**必須フレームワーク**] というセクションが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="141e2-179">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="141e2-180">ターゲットコンピューターには、アプリを実行するためのフレームワークがインストールされている必要があるため、アーキテクチャ (x86 または x64) に必要な各フレームワークのダウンロードプロセスを繰り返して、この記事の後半で説明する Windows の展開の一部として追加する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="141e2-180">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="141e2-181">図5は、Surface アプリに必要なフレームワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="141e2-181">Figure 5 shows the required frameworks for the Surface app.</span></span>

![Surface アプリの必須フレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")

*<span data-ttu-id="141e2-183">図 5: </span><span class="sxs-lookup"><span data-stu-id="141e2-183">Figure 5.</span></span> <span data-ttu-id="141e2-184">Surface アプリの必須フレームワーク</span><span class="sxs-lookup"><span data-stu-id="141e2-184">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="141e2-185">Surface アプリのバージョン番号と必須のフレームワークは、アプリが更新されると変更されます。</span><span class="sxs-lookup"><span data-stu-id="141e2-185">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="141e2-186">最新バージョンの Surface アプリと、Microsoft Store for Business の各フレームワークについて確認します。</span><span class="sxs-lookup"><span data-stu-id="141e2-186">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="141e2-187">一般法人向け Microsoft Store によって提供されているように、常に Surface アプリと推奨される framework のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="141e2-187">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="141e2-188">古いフレームワークまたは不適切なバージョンを使用すると、エラーが発生したり、アプリケーションがクラッシュすることがあります。</span><span class="sxs-lookup"><span data-stu-id="141e2-188">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="141e2-189">Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="141e2-189">To download the required frameworks for the Surface app, follow these steps:</span></span>
1. <span data-ttu-id="141e2-190">[ **140.00 _ 0_x64__8wekyb3d8bbwe 14.0.23816**] の下の [**ダウンロード**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-190">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="141e2-191">これにより、140.00 _ 14.0.23816 0_x64__8wekyb3d8bbwe がダウンロードされます。Appx ファイルを指定したフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="141e2-191">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>
2. <span data-ttu-id="141e2-192">[ **0_x64__8wekyb3d8bbwe 1.1.23406**] の下の [**ダウンロード**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="141e2-192">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="141e2-193">これにより、指定したフォルダーに1.1.23406 ファイルの0_x64__8wekyb3d8bbwe がダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="141e2-193">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="141e2-194">Surface デバイスには、64ビット (x64) バージョンの各フレームワークのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="141e2-194">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="141e2-195">Surface デバイスは、ネイティブの64ビット UEFI デバイスであり、32ビットフレームワークを必要とする32ビット (x86) バージョンの Windows とは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="141e2-195">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <span data-ttu-id="141e2-196">PowerShell を使用してコンピューターに Surface アプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="141e2-196">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="141e2-197">次の手順では、Surface アプリをコンピューターに準備し、そのコンピューター上で作成されたユーザーアカウントで利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="141e2-197">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>
1. <span data-ttu-id="141e2-198">この記事の「 [Microsoft Store For Business アカウントから surface アプリをダウンロードする方法](#download-surface-app-from-a-microsoft-store-for-business-account)」に記載されている手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="141e2-198">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 
2. <span data-ttu-id="141e2-199">管理者特権で PowerShell セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="141e2-199">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="141e2-200">管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="141e2-200">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="141e2-201">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="141e2-201">In the elevated PowerShell session, copy and paste the following command:</span></span>
    ```
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="141e2-202">[場所] `<DownloadPath>` は、Microsoft Store For Business アカウントから .appxbundle とライセンスファイルをダウンロードしたフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="141e2-202">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="141e2-203">たとえば、ファイルを c:\Temp にダウンロードした場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="141e2-203">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    ````
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. The Surface app will now be available on your current Windows computer. 

Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article. To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.

5. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
6. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## Install Surface app with MDT
The following procedure uses MDT to automate installation of the Surface app at the time of deployment. The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images. This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.
1. Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file. 
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:

   * Command:
     ```
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
   * Working Directory: %DEPLOYROOT%\Applications\SurfaceApp

For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article. Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.
1. Using the procedure described earlier in this article, download the framework files. Store each framework in a separate folder.
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.

To configure the frameworks as dependencies of the Surface app, use this process:
1. Open the properties of the Surface app in the MDT Deployment Workbench.
2. Click the **Dependencies** tab, and then click **Add**.
3. Select the check box for each framework using the name you provided in the New Application Wizard.

After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard. You can also install the application automatically by specifying the application in the deployment task sequence by following this process:
1. Open your deployment task sequence in the MDT Deployment Workbench.
2. Add a new **Install Application** task in the **State Restore** section of deployment.
3. Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.

For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).
