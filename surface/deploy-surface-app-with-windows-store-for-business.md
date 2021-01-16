---
title: ビジネス向け Microsoft Store または教育向け Microsoft Store を使った Surface アプリの展開 (Surface)
description: ビジネス向け Microsoft Store または Education 向け Microsoft Store を使って Surface アプリを追加およびダウンロードする方法と、PowerShell と MDT を使って Surface アプリをインストールする方法について説明します。
keywords: surface アプリ, アプリ, 展開, カスタマイズ
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
ms.date: 1/15/2021
ms.openlocfilehash: 87e24bcfa1e2d4ab05d24a05b203fea92637d3f4
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271074"
---
# <span data-ttu-id="44172-104">ビジネスおよび教育向け Microsoft Store を使った Surface アプリの展開</span><span class="sxs-lookup"><span data-stu-id="44172-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="44172-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="44172-105">Applies to</span></span>**

- <span data-ttu-id="44172-106">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="44172-106">Surface Pro 7+</span></span>
- <span data-ttu-id="44172-107">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="44172-107">Surface Laptop Go</span></span>
- <span data-ttu-id="44172-108">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="44172-108">Surface Pro 7</span></span>
- <span data-ttu-id="44172-109">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="44172-109">Surface Laptop 3</span></span>
- <span data-ttu-id="44172-110">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="44172-110">Surface Pro 6</span></span>
- <span data-ttu-id="44172-111">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="44172-111">Surface Laptop 2</span></span>
- <span data-ttu-id="44172-112">Surface Go</span><span class="sxs-lookup"><span data-stu-id="44172-112">Surface Go</span></span>
- <span data-ttu-id="44172-113">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="44172-113">Surface Go with LTE</span></span>
- <span data-ttu-id="44172-114">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="44172-114">Surface Book 2</span></span>
- <span data-ttu-id="44172-115">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="44172-115">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="44172-116">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="44172-116">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="44172-117">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="44172-117">Surface Laptop</span></span>
- <span data-ttu-id="44172-118">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="44172-118">Surface Studio</span></span>
- <span data-ttu-id="44172-119">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="44172-119">Surface Studio 2</span></span>
- <span data-ttu-id="44172-120">Surface Book</span><span class="sxs-lookup"><span data-stu-id="44172-120">Surface Book</span></span>
- <span data-ttu-id="44172-121">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="44172-121">Surface Pro 4</span></span>
- <span data-ttu-id="44172-122">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="44172-122">Surface 3 LTE</span></span>
- <span data-ttu-id="44172-123">Surface 3</span><span class="sxs-lookup"><span data-stu-id="44172-123">Surface 3</span></span>
- <span data-ttu-id="44172-124">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="44172-124">Surface Pro 3</span></span>


<span data-ttu-id="44172-125">Surface アプリは、次の Surface 固有の設定とオプションを制御できる軽量の Microsoft Store アプリです。</span><span class="sxs-lookup"><span data-stu-id="44172-125">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="44172-126">Surface デバイスの Windows ボタンを有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="44172-126">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="44172-127">Surface ペンの感度を調整する
</span><span class="sxs-lookup"><span data-stu-id="44172-127">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="44172-128">Surface ペンのボタンの操作をカスタマイズする
</span><span class="sxs-lookup"><span data-stu-id="44172-128">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="44172-129">Surface のオーディオ拡張機能を有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="44172-129">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="44172-130">デバイスのサポート ドキュメントと情報へのクイック アクセス</span><span class="sxs-lookup"><span data-stu-id="44172-130">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="44172-131">Windows Update を使うお客様は、通常、自動更新の一部として Surface アプリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="44172-131">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="44172-132">ただし、組織が Surface デバイスに展開するためのイメージを準備している場合は、個々のデバイスのユーザーに Microsoft Store またはビジネス向け Microsoft Store からアプリをダウンロードしてインストールする代わりに、イメージングおよび展開プロセスに Surface アプリ (以前の Surface Hub) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="44172-132">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="44172-133">この記事は、Surface Pro X には適用されません。詳細については、「Surface Pro X の展開、管理、サービス提供」[を参照してください](surface-pro-arm-app-management.md)。</span><span class="sxs-lookup"><span data-stu-id="44172-133">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <span data-ttu-id="44172-134">Surface アプリの概要</span><span class="sxs-lookup"><span data-stu-id="44172-134">Surface app overview</span></span>

<span data-ttu-id="44172-135">Surface アプリは [、Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="44172-135">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="44172-136">ユーザーは Microsoft Store からダウンロードしてインストールできますが、組織でビジネス向け Microsoft Store を使用している場合は、ストアのインベントリにアプリを追加し、Windows 展開プロセスの一部としてアプリを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="44172-136">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="44172-137">これらのプロセスについては、この記事全体で説明します。</span><span class="sxs-lookup"><span data-stu-id="44172-137">These processes are discussed throughout this article.</span></span> <span data-ttu-id="44172-138">ビジネス向け Microsoft Store について詳しくは、Windows TechCenter のビジネス向け [Microsoft Store](https://docs.microsoft.com/microsoft-store/) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="44172-138">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <span data-ttu-id="44172-139">ビジネス向け Microsoft Store アカウントに Surface アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="44172-139">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="44172-140">ユーザーが企業のビジネス向け Microsoft Store アカウントからアプリをインストールまたは展開する前に、目的のアプリを最初に利用可能にし、ビジネスユーザーにライセンスを割り当てなければならない。</span><span class="sxs-lookup"><span data-stu-id="44172-140">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="44172-141">まだ作成していない場合は、ビジネス向け [Microsoft Store アカウントを作成します](https://www.microsoft.com/business-store)。</span><span class="sxs-lookup"><span data-stu-id="44172-141">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="44172-142">ポータルにログオンします。</span><span class="sxs-lookup"><span data-stu-id="44172-142">Log on to the portal.</span></span> 

3. <span data-ttu-id="44172-143">オフライン ライセンスを有効にします。図 1 に示すように、[Manage->**Store settings]** をクリックし、[ストアでショッピングを行うユーザーにオフライン ライセンス アプリを表示する] チェック ボックスをオンにします。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="44172-143">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="44172-144">ビジネス向け Microsoft Store アプリのライセンス モデルについて詳しくは、「ビジネスおよび教育向け Microsoft Store の [アプリ」をご覧ください](https://docs.microsoft.com/microsoft-store/)。</span><span class="sxs-lookup"><span data-stu-id="44172-144">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span>

   > [!div class="mx-imgBorder"]
   > ![[オフライン ライセンス アプリを表示する] チェック ボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="44172-146">図 1. </span><span class="sxs-lookup"><span data-stu-id="44172-146">Figure 1.</span></span> <span data-ttu-id="44172-147">オフラインで使用するアプリを有効にする</span><span class="sxs-lookup"><span data-stu-id="44172-147">Enable apps for offline use</span></span>*

4. <span data-ttu-id="44172-148">次の手順に従って、ビジネス向け Microsoft Store アカウントに Surface アプリを追加します。</span><span class="sxs-lookup"><span data-stu-id="44172-148">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>

    * <span data-ttu-id="44172-149">[ショップ **] メニューをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="44172-149">Click the **Shop** menu.</span></span>
    
    * <span data-ttu-id="44172-150">検索ボックスに「Surface アプリ」 **と入力し**、検索アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="44172-150">In the search box, type **Surface app**, and then click the search icon.</span></span>
    
    * <span data-ttu-id="44172-151">Surface アプリが検索結果に表示された後、アプリのアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="44172-151">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    
    * <span data-ttu-id="44172-152">図 2 に示すように、選択項目 ([ **オンライン** ] または [ **オフライン**] を選択) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="44172-152">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンス モードを選択し、アプリをインベントリに追加する](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *<span data-ttu-id="44172-154">図 2. </span><span class="sxs-lookup"><span data-stu-id="44172-154">Figure 2.</span></span> <span data-ttu-id="44172-155">オフライン ライセンス モードを選択し、アプリをインベントリに追加する</span><span class="sxs-lookup"><span data-stu-id="44172-155">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="44172-156">[ **オフライン] を** クリックしてオフライン ライセンス モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="44172-156">Click **Offline** to select the Offline licensing mode.</span></span>
    
    * <span data-ttu-id="44172-157">[ **アプリの取得] を** クリックして、ビジネス向け Microsoft Store のインベントリにアプリを追加します。</span><span class="sxs-lookup"><span data-stu-id="44172-157">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="44172-158">図 3 に示すように、オフライン アプリを管理ツールを使用して展開したり、プライベート ストアの会社の在庫ページからダウンロードしたりできる点を確認するダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44172-158">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![<span data-ttu-id="44172-159">オフライン ライセンスのアプリ確認ウィンドウ図 ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *3.オフライン ライセンスのアプリの確認*</span><span class="sxs-lookup"><span data-stu-id="44172-159">Offline-licensed app acknowledgement window](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
*Figure 3. Offline-licensed app acknowledgement*</span></span>
      
    * <span data-ttu-id="44172-160">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44172-160">Click **OK**.</span></span>

## <span data-ttu-id="44172-161">ビジネス向け Microsoft Store アカウントから Surface アプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="44172-161">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="44172-162">オフライン モードでビジネス向け Microsoft Store アカウントにアプリを追加した後、アプリをダウンロードして展開共有に AppxBundle として追加できます。</span><span class="sxs-lookup"><span data-stu-id="44172-162">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>

1. <span data-ttu-id="44172-163">ビジネス向け Microsoft Store アカウントにログオンします https://businessstore.microsoft.com 。</span><span class="sxs-lookup"><span data-stu-id="44172-163">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>

2. <span data-ttu-id="44172-164">Click **Manage->Apps & software**.</span><span class="sxs-lookup"><span data-stu-id="44172-164">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="44172-165">会社のすべてのアプリの一覧が表示されます。この記事の「ビジネス向け [Microsoft Store](#add-surface-app-to-a-microsoft-store-for-business-account) アカウントに Surface アプリを追加する」セクションに追加した Surface アプリも含めて表示されます。</span><span class="sxs-lookup"><span data-stu-id="44172-165">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>

3. <span data-ttu-id="44172-166">[**操作]** で省略記号 **(...)** をクリック\*\*\*\* し、Surface アプリでオフラインで使用するために [ダウンロード] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44172-166">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>

4. <span data-ttu-id="44172-167">図 4**に示**すように、選択したアプリで使用可能な選択項目から目的のプラットフォームとアーキテクチャのオプションを選択します。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="44172-167">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    > [!div class="mx-imgBorder"]
    > ![AppxBundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *<span data-ttu-id="44172-169">図 4: </span><span class="sxs-lookup"><span data-stu-id="44172-169">Figure 4.</span></span> <span data-ttu-id="44172-170">アプリの AppxBundle パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="44172-170">Download the AppxBundle package for an app</span></span>*
    
5. <span data-ttu-id="44172-171">[ダウンロード **] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="44172-171">Click **Download**.</span></span> <span data-ttu-id="44172-172">AppxBundle パッケージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="44172-172">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="44172-173">ダウンロードしたファイルのパスをメモしてください。これは、この記事で後で必要になります。</span><span class="sxs-lookup"><span data-stu-id="44172-173">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>

6. <span data-ttu-id="44172-174">[エンコードされたライセンス **] または [** エンコードされていないライセンス] **オプションをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="44172-174">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="44172-175">Microsoft Endpoint Configuration Manager のような管理ツールや、Windows 構成デザイナーを使用してプロビジョニング パッケージを作成する場合は、エンコードされたライセンス オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="44172-175">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="44172-176">展開イメージのサービスと管理 (DISM) を使用する場合、またはイメージングに基づく展開ソリューション (Microsoft Deployment Toolkit (MDT) を含む) を使用する場合は、[コード化されていないライセンス] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="44172-176">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>

7. <span data-ttu-id="44172-177">**[Generate]** (生成) をクリックして、アプリのライセンスを生成してダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="44172-177">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="44172-178">ライセンス ファイルのパスは、この記事で後で必要になりますので、注意してください。</span><span class="sxs-lookup"><span data-stu-id="44172-178">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="44172-179">Surface アプリなど、オフラインで使うアプリをダウンロードすると、ページの下部に [必須のフレームワーク] というラベルのセクションが表示**されることがあります。**</span><span class="sxs-lookup"><span data-stu-id="44172-179">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="44172-180">ターゲット コンピューターにはアプリを実行するためにフレームワークがインストールされている必要があります。そのため、アーキテクチャに必要な各フレームワーク (x86 または x64) についてダウンロード プロセスを繰り返し、後で説明する Windows 展開の一部として含める必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="44172-180">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="44172-181">図 5 は、Surface アプリに必要なフレームワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="44172-181">Figure 5 shows the required frameworks for the Surface app.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface アプリに必要なフレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*<span data-ttu-id="44172-183">図 5: </span><span class="sxs-lookup"><span data-stu-id="44172-183">Figure 5.</span></span> <span data-ttu-id="44172-184">Surface アプリに必要なフレームワーク</span><span class="sxs-lookup"><span data-stu-id="44172-184">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="44172-185">Surface アプリのバージョン番号と必要なフレームワークは、アプリの更新に応じて変更されます。</span><span class="sxs-lookup"><span data-stu-id="44172-185">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="44172-186">ビジネス向け Microsoft Store の Surface アプリと各フレームワークの最新バージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="44172-186">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="44172-187">ビジネス向け Microsoft Store で提供されている Surface アプリと推奨されるフレームワーク バージョンを常に使用します。</span><span class="sxs-lookup"><span data-stu-id="44172-187">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="44172-188">古いフレームワークや正しくないバージョンを使用すると、エラーやアプリケーションのクラッシュが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44172-188">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="44172-189">Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="44172-189">To download the required frameworks for the Surface app, follow these steps:</span></span>

1. <span data-ttu-id="44172-190">**Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="44172-190">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="44172-191">これにより、Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe がダウンロードされます。指定したフォルダーの Appx ファイル。</span><span class="sxs-lookup"><span data-stu-id="44172-191">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

2. <span data-ttu-id="44172-192">**Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="44172-192">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="44172-193">これにより、Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx ファイルが指定したフォルダーにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="44172-193">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="44172-194">Surface デバイスでは、各フレームワークの 64 ビット (x64) バージョンだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="44172-194">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="44172-195">Surface デバイスは、ネイティブの 64 ビット UEFI デバイスであり、32 ビット フレームワークを必要とする 32 ビット (x86) バージョンの Windows と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="44172-195">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <span data-ttu-id="44172-196">PowerShell を使用して Surface アプリをコンピューターにインストールする</span><span class="sxs-lookup"><span data-stu-id="44172-196">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="44172-197">次の手順では、Surface アプリをコンピューターにプロビジョニングし、その後コンピューターで作成されたユーザー アカウントで利用できます。</span><span class="sxs-lookup"><span data-stu-id="44172-197">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>

1. <span data-ttu-id="44172-198">この記事の「ビジネス向け [Microsoft Store](#download-surface-app-from-a-microsoft-store-for-business-account) アカウントから Surface アプリをダウンロードする方法」セクションで説明されている手順に従って、Surface アプリの AppxBundle とライセンス ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="44172-198">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="44172-199">管理者特権で PowerShell セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="44172-199">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="44172-200">管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可が付与されません。</span><span class="sxs-lookup"><span data-stu-id="44172-200">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="44172-201">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="44172-201">In the elevated PowerShell session, copy and paste the following command:</span></span>

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="44172-202">ここで、ビジネス向け Microsoft Store アカウントから AppxBundle とライセンス ファイルをダウンロードした `<DownloadPath>` フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="44172-202">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="44172-203">たとえば、ファイルを c:\Temp にダウンロードした場合、実行するコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44172-203">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. <span data-ttu-id="44172-204">これで、Surface アプリは現在の Windows コンピューターで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="44172-204">The Surface app will now be available on your current Windows computer.</span></span> 

   <span data-ttu-id="44172-205">Surface アプリがプロビジョニングされたコンピューターで機能する前に、この記事で既に説明したフレームワークもプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="44172-205">Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article.</span></span> <span data-ttu-id="44172-206">これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した管理者特権の PowerShell セッションで次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="44172-206">To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.</span></span>

5. <span data-ttu-id="44172-207">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="44172-207">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. <span data-ttu-id="44172-208">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="44172-208">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <span data-ttu-id="44172-209">MDT を使った Surface アプリのインストール</span><span class="sxs-lookup"><span data-stu-id="44172-209">Install Surface app with MDT</span></span>
<span data-ttu-id="44172-210">次の手順では、MDT を使って、展開時に Surface アプリのインストールを自動化します。</span><span class="sxs-lookup"><span data-stu-id="44172-210">The following procedure uses MDT to automate installation of the Surface app at the time of deployment.</span></span> <span data-ttu-id="44172-211">アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="44172-211">The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images.</span></span> <span data-ttu-id="44172-212">これは、Surface デバイスへの Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。これは、Windows イメージのクロス プラットフォームの互換性を低下さないのでです。</span><span class="sxs-lookup"><span data-stu-id="44172-212">This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.</span></span>

1. <span data-ttu-id="44172-213">この記事で前述した [手順を使用して](#download-surface-app-from-a-microsoft-store-for-business-account)、Surface appxBundle とライセンス ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="44172-213">Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="44172-214">MDT Deployment Workbench の新しいアプリケーション ウィザードを使って、ダウンロードしたファイルを、ソース ファイルを含む新しい **アプリケーションとしてインポートします**。</span><span class="sxs-lookup"><span data-stu-id="44172-214">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="44172-215">新しい**アプリケーション**ウィザードの [コマンドの詳細] ページ\*\*\*\* で、既定の作業ディレクトリを指定し、**コマンド**で AppxBundle のファイル名を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="44172-215">On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:</span></span>

   * <span data-ttu-id="44172-216">コマンド:</span><span class="sxs-lookup"><span data-stu-id="44172-216">Command:</span></span>
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * <span data-ttu-id="44172-217">作業ディレクトリ: %DEPLOYROOT%\Applications\SurfaceApp</span><span class="sxs-lookup"><span data-stu-id="44172-217">Working Directory: %DEPLOYROOT%\Applications\SurfaceApp</span></span>

<span data-ttu-id="44172-218">Surface アプリがターゲット コンピューターで機能するには、この記事で既に説明したフレームワークも必要です。</span><span class="sxs-lookup"><span data-stu-id="44172-218">For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article.</span></span> <span data-ttu-id="44172-219">Surface アプリに必要なフレームワークを MDT にインポートし、依存関係として構成するには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="44172-219">Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.</span></span>

1. <span data-ttu-id="44172-220">この記事で前述した手順を使用して、フレームワーク ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="44172-220">Using the procedure described earlier in this article, download the framework files.</span></span> <span data-ttu-id="44172-221">各フレームワークを個別のフォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="44172-221">Store each framework in a separate folder.</span></span>

2. <span data-ttu-id="44172-222">MDT Deployment Workbench の新しいアプリケーション ウィザードを使って、ダウンロードしたファイルを、ソース ファイルを含む新しい **アプリケーションとしてインポートします**。</span><span class="sxs-lookup"><span data-stu-id="44172-222">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="44172-223">[コマンド **の詳細]** ページで、ダウンロードした各アプリケーションのファイル名を **Command** フィールドと既定の作業ディレクトリに入力します。</span><span class="sxs-lookup"><span data-stu-id="44172-223">On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.</span></span>

<span data-ttu-id="44172-224">Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="44172-224">To configure the frameworks as dependencies of the Surface app, use this process:</span></span>

1. <span data-ttu-id="44172-225">MDT Deployment Workbench で Surface アプリのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="44172-225">Open the properties of the Surface app in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="44172-226">[依存関係 **] タブをクリック** し、[追加] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="44172-226">Click the **Dependencies** tab, and then click **Add**.</span></span>

3. <span data-ttu-id="44172-227">新しいアプリケーション ウィザードで指定した名前を使用して、各フレームワークのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="44172-227">Select the check box for each framework using the name you provided in the New Application Wizard.</span></span>

<span data-ttu-id="44172-228">インポート後、Surface アプリは Windows 展開ウィザードの **[アプリケーション** ] ステップで選択できます。</span><span class="sxs-lookup"><span data-stu-id="44172-228">After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard.</span></span> <span data-ttu-id="44172-229">次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="44172-229">You can also install the application automatically by specifying the application in the deployment task sequence by following this process:</span></span>

1. <span data-ttu-id="44172-230">MDT の Deployment Workbench で、展開タスク シーケンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="44172-230">Open your deployment task sequence in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="44172-231">展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="44172-231">Add a new **Install Application** task in the **State Restore** section of deployment.</span></span>

3. <span data-ttu-id="44172-232">[Install **a single application] (単一のアプリケーション** のインストール) を選択し、インストールするアプリケーションとして Surface **App** **を指定します**。</span><span class="sxs-lookup"><span data-stu-id="44172-232">Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.</span></span>

<span data-ttu-id="44172-233">Windows 展開へのアプリの組み込みについて詳しくは、「Microsoft Deployment Toolkit を使った [Windows 10 の展開」をご覧ください](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)。</span><span class="sxs-lookup"><span data-stu-id="44172-233">For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).</span></span>
