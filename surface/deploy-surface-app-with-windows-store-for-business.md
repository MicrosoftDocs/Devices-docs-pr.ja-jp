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
ms.openlocfilehash: 811feff1f0643ab0ba5d624c5f7d561ba5b0cd4d
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114715"
---
# <span data-ttu-id="b9adf-104">一般法人向けおよび教育機関向け Microsoft Store で Surface アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="b9adf-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="b9adf-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="b9adf-105">Applies to</span></span>**

- <span data-ttu-id="b9adf-106">Surface のノート Pc の移動</span><span class="sxs-lookup"><span data-stu-id="b9adf-106">Surface Laptop Go</span></span>
- <span data-ttu-id="b9adf-107">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="b9adf-107">Surface Pro 7</span></span>
- <span data-ttu-id="b9adf-108">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="b9adf-108">Surface Laptop 3</span></span>
- <span data-ttu-id="b9adf-109">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="b9adf-109">Surface Pro 6</span></span>
- <span data-ttu-id="b9adf-110">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="b9adf-110">Surface Laptop 2</span></span>
- <span data-ttu-id="b9adf-111">Surface Go</span><span class="sxs-lookup"><span data-stu-id="b9adf-111">Surface Go</span></span>
- <span data-ttu-id="b9adf-112">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="b9adf-112">Surface Go with LTE</span></span>
- <span data-ttu-id="b9adf-113">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="b9adf-113">Surface Book 2</span></span>
- <span data-ttu-id="b9adf-114">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="b9adf-114">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="b9adf-115">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="b9adf-115">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="b9adf-116">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="b9adf-116">Surface Laptop</span></span>
- <span data-ttu-id="b9adf-117">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="b9adf-117">Surface Studio</span></span>
- <span data-ttu-id="b9adf-118">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="b9adf-118">Surface Studio 2</span></span>
- <span data-ttu-id="b9adf-119">Surface Book</span><span class="sxs-lookup"><span data-stu-id="b9adf-119">Surface Book</span></span>
- <span data-ttu-id="b9adf-120">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="b9adf-120">Surface Pro 4</span></span>
- <span data-ttu-id="b9adf-121">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="b9adf-121">Surface 3 LTE</span></span>
- <span data-ttu-id="b9adf-122">Surface 3</span><span class="sxs-lookup"><span data-stu-id="b9adf-122">Surface 3</span></span>
- <span data-ttu-id="b9adf-123">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="b9adf-123">Surface Pro 3</span></span>


<span data-ttu-id="b9adf-124">Surface アプリは、次のようなさまざまなサーフェス固有の設定とオプションを管理するための、軽量の Microsoft Store アプリです。</span><span class="sxs-lookup"><span data-stu-id="b9adf-124">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="b9adf-125">Surface デバイスの Windows ボタンを有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="b9adf-125">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="b9adf-126">Surface ペンの感度を調整する
</span><span class="sxs-lookup"><span data-stu-id="b9adf-126">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="b9adf-127">Surface ペンのボタンの操作をカスタマイズする
</span><span class="sxs-lookup"><span data-stu-id="b9adf-127">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="b9adf-128">Surface のオーディオ拡張機能を有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="b9adf-128">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="b9adf-129">デバイスのサポートドキュメントと情報にすばやくアクセスする</span><span class="sxs-lookup"><span data-stu-id="b9adf-129">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="b9adf-130">Windows Update を使用しているユーザーは、通常、自動更新の一部として Surface アプリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-130">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="b9adf-131">ただし、組織で Surface デバイスへの展開用のイメージを準備している場合は、個々のデバイスのユーザーに対して、Microsoft ストアまたは Microsoft Store からアプリをダウンロードしてインストールするのではなく、イメージと展開プロセスに Surface アプリ (旧称 Surface Hub) を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-131">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="b9adf-132">この記事は Surface Pro X には適用されません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9adf-132">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <span data-ttu-id="b9adf-133">Surface アプリの概要</span><span class="sxs-lookup"><span data-stu-id="b9adf-133">Surface app overview</span></span>

<span data-ttu-id="b9adf-134">Surface アプリは、 [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-134">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="b9adf-135">ユーザーは Microsoft ストアからダウンロードしてインストールできますが、組織で一般法人向け Microsoft Store を使用している場合は、アプリをストアのインベントリに追加して、Windows 展開プロセスの一部としてアプリを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-135">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="b9adf-136">これらのプロセスについては、この記事を通して説明します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-136">These processes are discussed throughout this article.</span></span> <span data-ttu-id="b9adf-137">一般法人向け Microsoft Store の詳細については、「Windows TechCenter で一般 [法人向け Microsoft store](https://docs.microsoft.com/microsoft-store/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9adf-137">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <span data-ttu-id="b9adf-138">Microsoft Store for Business アカウントに Surface アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="b9adf-138">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="b9adf-139">ユーザーが会社の Microsoft ストアのビジネスアカウントを使用してアプリをインストールまたは展開する前に、必要なアプリを最初に利用可能にして、ビジネスユーザーに対してライセンスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-139">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="b9adf-140">[ビジネスアカウント用に Microsoft Store](https://www.microsoft.com/business-store)をまだ作成していない場合は、作成します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-140">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="b9adf-141">ポータルにログオンします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-141">Log on to the portal.</span></span> 

3. <span data-ttu-id="b9adf-142">[オフラインライセンスを有効にする]: [管理]、[ **>ストアの設定**] の順にクリックし、[ **オフラインライセンス** を持つアプリをストアに表示する] チェックボックスをオンにします (図1のように)。</span><span class="sxs-lookup"><span data-stu-id="b9adf-142">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="b9adf-143">一般法人向け Microsoft Store for Business アプリのライセンスモデルの詳細については、「一般 [法人向け Microsoft store のアプリ](https://docs.microsoft.com/microsoft-store/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9adf-143">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span>

   > [!div class="mx-imgBorder"]
   > ![[オフラインライセンスアプリの表示] チェックボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="b9adf-145">図 1. </span><span class="sxs-lookup"><span data-stu-id="b9adf-145">Figure 1.</span></span> <span data-ttu-id="b9adf-146">オフラインでのアプリの使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="b9adf-146">Enable apps for offline use</span></span>*

4. <span data-ttu-id="b9adf-147">次の手順に従って、ビジネスアカウントの Microsoft ストアに Surface アプリを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-147">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>

    * <span data-ttu-id="b9adf-148">[ **ショップ** ] メニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-148">Click the **Shop** menu.</span></span>
    
    * <span data-ttu-id="b9adf-149">検索ボックスに「 **Surface app**」と入力し、[検索] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-149">In the search box, type **Surface app**, and then click the search icon.</span></span>
    
    * <span data-ttu-id="b9adf-150">Surface アプリが検索結果に表示されたら、アプリのアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-150">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    
    * <span data-ttu-id="b9adf-151">図2に示すように、選択肢が表示されます ([ **オンライン** または **オフライン**] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="b9adf-151">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![オフラインライセンスモードを選択し、アプリをインベントリに追加します。](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *<span data-ttu-id="b9adf-153">図 2. </span><span class="sxs-lookup"><span data-stu-id="b9adf-153">Figure 2.</span></span> <span data-ttu-id="b9adf-154">オフラインライセンスモードを選択し、アプリをインベントリに追加します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-154">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="b9adf-155">[ **オフライン** ] をクリックして、オフラインライセンスモードを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-155">Click **Offline** to select the Offline licensing mode.</span></span>
    
    * <span data-ttu-id="b9adf-156">[ **アプリの取得** ] をクリックして、アプリを Microsoft Store for Business のインベントリに追加します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-156">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="b9adf-157">図3に示すように、管理ツールを使用してオフラインアプリを展開できること、またはプライベートストアの会社の在庫ページからダウンロードできることを確認するダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-157">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![<span data-ttu-id="b9adf-158">オフライン-ライセンス付与されたアプリ確認ウィンドウ ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *図3オフライン-ライセンス付与されたアプリの確認*</span><span class="sxs-lookup"><span data-stu-id="b9adf-158">Offline-licensed app acknowledgement window](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
*Figure 3. Offline-licensed app acknowledgement*</span></span>
      
    * <span data-ttu-id="b9adf-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-159">Click **OK**.</span></span>

## <span data-ttu-id="b9adf-160">Microsoft Store for Business アカウントから Surface アプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="b9adf-160">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="b9adf-161">オフラインモードで、ビジネスアカウント用の Microsoft ストアにアプリを追加した後で、アプリをダウンロードして展開共有に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-161">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>

1. <span data-ttu-id="b9adf-162">のビジネスアカウント用の Microsoft ストアにログオン https://businessstore.microsoft.com します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-162">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>

2. <span data-ttu-id="b9adf-163">[ **Manage >app & software**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-163">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="b9adf-164">この記事の「 [surface アプリを Microsoft Store For Business アカウントに追加](#add-surface-app-to-a-microsoft-store-for-business-account) する」で追加した surface アプリなど、すべての会社のアプリの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-164">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>

3. <span data-ttu-id="b9adf-165">[ **アクション**] で、省略記号 ([**...**]) をクリックし、[Surface アプリの **オフライン使用のためにダウンロード** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-165">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>

4. <span data-ttu-id="b9adf-166">図4に示すように、選択したアプリで利用可能な **プラットフォーム** と **アーキテクチャ** のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-166">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    > [!div class="mx-imgBorder"]
    > ![.Appxbundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *<span data-ttu-id="b9adf-168">図 4: </span><span class="sxs-lookup"><span data-stu-id="b9adf-168">Figure 4.</span></span> <span data-ttu-id="b9adf-169">アプリの .Appxbundle パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="b9adf-169">Download the AppxBundle package for an app</span></span>*
    
5. <span data-ttu-id="b9adf-170">[ **ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-170">Click **Download**.</span></span> <span data-ttu-id="b9adf-171">.Appxbundle パッケージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-171">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="b9adf-172">この記事で後述する必要があるため、ダウンロードしたファイルのパスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-172">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>

6. <span data-ttu-id="b9adf-173">**エンコード**済みライセンスまたはエンコード済み**ライセンス**オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-173">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="b9adf-174">エンコードされたライセンスオプションは、Microsoft Endpoint Configuration Manager などの管理ツールで使用するか、Windows 構成デザイナーを使ってプロビジョニングパッケージを作成するときに使います。</span><span class="sxs-lookup"><span data-stu-id="b9adf-174">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="b9adf-175">展開イメージのサービスと管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft 展開ツールキット (MDT) を含む) を使用する場合は、[エンコードされていないライセンス] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-175">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>

7. <span data-ttu-id="b9adf-176">[ **生成** ] をクリックして、アプリのライセンスを生成し、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-176">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="b9adf-177">この記事で後述する必要があるため、ライセンスファイルのパスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-177">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="b9adf-178">Surface アプリなど、オフラインで使用するためのアプリをダウンロードすると、ページの下部にある [ **必須フレームワーク**] というセクションが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-178">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="b9adf-179">ターゲットコンピューターには、アプリを実行するためのフレームワークがインストールされている必要があるため、アーキテクチャ (x86 または x64) に必要な各フレームワークのダウンロードプロセスを繰り返して、この記事の後半で説明する Windows の展開の一部として追加する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-179">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="b9adf-180">図5は、Surface アプリに必要なフレームワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9adf-180">Figure 5 shows the required frameworks for the Surface app.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface アプリの必須フレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*<span data-ttu-id="b9adf-182">図 5: </span><span class="sxs-lookup"><span data-stu-id="b9adf-182">Figure 5.</span></span> <span data-ttu-id="b9adf-183">Surface アプリの必須フレームワーク</span><span class="sxs-lookup"><span data-stu-id="b9adf-183">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="b9adf-184">Surface アプリのバージョン番号と必須のフレームワークは、アプリが更新されると変更されます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-184">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="b9adf-185">最新バージョンの Surface アプリと、Microsoft Store for Business の各フレームワークについて確認します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-185">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="b9adf-186">一般法人向け Microsoft Store によって提供されているように、常に Surface アプリと推奨される framework のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-186">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="b9adf-187">古いフレームワークまたは不適切なバージョンを使用すると、エラーが発生したり、アプリケーションがクラッシュすることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-187">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="b9adf-188">Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-188">To download the required frameworks for the Surface app, follow these steps:</span></span>

1. <span data-ttu-id="b9adf-189">[Microsoft 140.00] の下の [ **ダウンロード** ] ボタンをクリックします。 **23816 _x64__8wekyb3d8bbwe**。</span><span class="sxs-lookup"><span data-stu-id="b9adf-189">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="b9adf-190">これにより、140.00 _ 23816 _x64__8wekyb3d8bbwe のような内容がダウンロードされます。Appx ファイルを指定したフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-190">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

2. <span data-ttu-id="b9adf-191">[ **23406 _x64__8wekyb3d8bbwe**] の下の [**ダウンロード**] ボタンをクリックします。。</span><span class="sxs-lookup"><span data-stu-id="b9adf-191">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="b9adf-192">これにより、指定したフォルダーに23406ファイルをダウンロードすることができます。この場合は、_x64__8wekyb3d8bbwe ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-192">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="b9adf-193">Surface デバイスには、64ビット (x64) バージョンの各フレームワークのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="b9adf-193">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="b9adf-194">Surface デバイスは、ネイティブの64ビット UEFI デバイスであり、32ビットフレームワークを必要とする32ビット (x86) バージョンの Windows とは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="b9adf-194">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <span data-ttu-id="b9adf-195">PowerShell を使用してコンピューターに Surface アプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="b9adf-195">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="b9adf-196">次の手順では、Surface アプリをコンピューターに準備し、そのコンピューター上で作成されたユーザーアカウントで利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-196">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>

1. <span data-ttu-id="b9adf-197">この記事の「 [Microsoft Store For Business アカウントから surface アプリをダウンロードする方法](#download-surface-app-from-a-microsoft-store-for-business-account) 」に記載されている手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-197">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="b9adf-198">管理者特権で PowerShell セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-198">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="b9adf-199">管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="b9adf-199">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="b9adf-200">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-200">In the elevated PowerShell session, copy and paste the following command:</span></span>

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="b9adf-201">[場所] `<DownloadPath>` は、Microsoft Store For Business アカウントから .appxbundle とライセンスファイルをダウンロードしたフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="b9adf-201">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="b9adf-202">たとえば、ファイルを c:\Temp にダウンロードした場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-202">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. <span data-ttu-id="b9adf-203">これで、Surface アプリは現在の Windows コンピューターで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-203">The Surface app will now be available on your current Windows computer.</span></span> 

   <span data-ttu-id="b9adf-204">Surface アプリがプロビジョニングされているコンピューターで機能する前に、この記事で前に説明したフレームワークをプロビジョニングする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-204">Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article.</span></span> <span data-ttu-id="b9adf-205">これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した管理者である PowerShell セッションで次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-205">To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.</span></span>

5. <span data-ttu-id="b9adf-206">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-206">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. <span data-ttu-id="b9adf-207">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-207">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <span data-ttu-id="b9adf-208">MDT を使用して Surface アプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="b9adf-208">Install Surface app with MDT</span></span>
<span data-ttu-id="b9adf-209">次の手順では、MDT を使って、配置時に Surface アプリのインストールを自動化します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-209">The following procedure uses MDT to automate installation of the Surface app at the time of deployment.</span></span> <span data-ttu-id="b9adf-210">アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-210">The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images.</span></span> <span data-ttu-id="b9adf-211">これは、windows イメージのクロスプラットフォームの互換性を低下させないため、surface デバイスに Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。</span><span class="sxs-lookup"><span data-stu-id="b9adf-211">This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.</span></span>

1. <span data-ttu-id="b9adf-212">[この記事で前に](#download-surface-app-from-a-microsoft-store-for-business-account)説明した手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-212">Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="b9adf-213">MDT 展開ワークベンチの新しいアプリケーションウィザードを使って、ダウンロードしたファイルを新しいアプリケーションとして **ソースファイルと**してインポートします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-213">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="b9adf-214">新しいアプリケーションウィザードの [ **コマンドの詳細** ] ページで、既定の **作業ディレクトリ** を指定します。 **コマンド** には、次のように、.appxbundle のファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-214">On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:</span></span>

   * <span data-ttu-id="b9adf-215">コマンド</span><span class="sxs-lookup"><span data-stu-id="b9adf-215">Command:</span></span>
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * <span data-ttu-id="b9adf-216">ワーキングディレクトリ:%DEPLOYROOT%\Applications\SurfaceApp</span><span class="sxs-lookup"><span data-stu-id="b9adf-216">Working Directory: %DEPLOYROOT%\Applications\SurfaceApp</span></span>

<span data-ttu-id="b9adf-217">Surface アプリをターゲットコンピューターで機能させるには、この記事で前に説明したフレームワークも必要になります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-217">For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article.</span></span> <span data-ttu-id="b9adf-218">次の手順を使用して、Surface アプリに必要なフレームワークを MDT にインポートし、それを依存関係として構成します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-218">Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.</span></span>

1. <span data-ttu-id="b9adf-219">この記事の前半で説明した手順を使用して、フレームワークファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-219">Using the procedure described earlier in this article, download the framework files.</span></span> <span data-ttu-id="b9adf-220">各フレームワークを個別のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-220">Store each framework in a separate folder.</span></span>

2. <span data-ttu-id="b9adf-221">MDT 展開ワークベンチの新しいアプリケーションウィザードを使って、ダウンロードしたファイルを新しいアプリケーションとして **ソースファイルと**してインポートします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-221">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="b9adf-222">[ **コマンドの詳細** ] ページで、ダウンロードした各アプリケーションのファイル名を、 **コマンド** フィールドと既定の作業ディレクトリに入力します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-222">On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.</span></span>

<span data-ttu-id="b9adf-223">Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-223">To configure the frameworks as dependencies of the Surface app, use this process:</span></span>

1. <span data-ttu-id="b9adf-224">MDT 展開ワークベンチで Surface アプリのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-224">Open the properties of the Surface app in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="b9adf-225">[ **依存関係** ] タブをクリックし、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-225">Click the **Dependencies** tab, and then click **Add**.</span></span>

3. <span data-ttu-id="b9adf-226">新しいアプリケーションウィザードで指定した名前を使用して、各フレームワークのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b9adf-226">Select the check box for each framework using the name you provided in the New Application Wizard.</span></span>

<span data-ttu-id="b9adf-227">インポート後、Surface アプリは、Windows 展開ウィザードの [ **アプリケーション** ] ステップで選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9adf-227">After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard.</span></span> <span data-ttu-id="b9adf-228">次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-228">You can also install the application automatically by specifying the application in the deployment task sequence by following this process:</span></span>

1. <span data-ttu-id="b9adf-229">MDT の Deployment Workbench で、展開タスク シーケンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9adf-229">Open your deployment task sequence in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="b9adf-230">展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-230">Add a new **Install Application** task in the **State Restore** section of deployment.</span></span>

3. <span data-ttu-id="b9adf-231">[**単一のアプリケーションをインストール**する] を選択し、**インストールするアプリケーション**として**Surface アプリ**を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9adf-231">Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.</span></span>

<span data-ttu-id="b9adf-232">Windows 展開にアプリを含める方法について詳しくは、「 [Microsoft 展開ツールキットを使用して windows 10 を展開](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)する」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b9adf-232">For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).</span></span>
