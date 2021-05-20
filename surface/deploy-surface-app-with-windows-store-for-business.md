---
title: Surface アプリを展開するには、ビジネス向け Microsoft Storeまたは教育機関向け Microsoft Storeを使用します (Surface)
description: PowerShell と MDT を使用して Surface アプリビジネス向け Microsoft Storeまたは教育機関向け Microsoft Store Surface アプリをインストールする方法について説明します。
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
ms.date: 4/16/2021
ms.openlocfilehash: c7a882859339ff3d7feeb685c62672bc57c301ec
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576527"
---
# <a name="deploy-surface-app-with-microsoft-store-for-business-and-education"></a><span data-ttu-id="4473a-104">アプリと教育を使用ビジネス向け Microsoft Store Surface アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="4473a-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="4473a-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="4473a-105">Applies to</span></span>**

- <span data-ttu-id="4473a-106">Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="4473a-106">Surface Laptop 4</span></span>
- <span data-ttu-id="4473a-107">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="4473a-107">Surface Pro 7+</span></span>
- <span data-ttu-id="4473a-108">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="4473a-108">Surface Laptop Go</span></span>
- <span data-ttu-id="4473a-109">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="4473a-109">Surface Pro 7</span></span>
- <span data-ttu-id="4473a-110">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="4473a-110">Surface Laptop 3</span></span>
- <span data-ttu-id="4473a-111">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="4473a-111">Surface Pro 6</span></span>
- <span data-ttu-id="4473a-112">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="4473a-112">Surface Laptop 2</span></span>
- <span data-ttu-id="4473a-113">Surface Go</span><span class="sxs-lookup"><span data-stu-id="4473a-113">Surface Go</span></span>
- <span data-ttu-id="4473a-114">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="4473a-114">Surface Go with LTE</span></span>
- <span data-ttu-id="4473a-115">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="4473a-115">Surface Book 2</span></span>
- <span data-ttu-id="4473a-116">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="4473a-116">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="4473a-117">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="4473a-117">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="4473a-118">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="4473a-118">Surface Laptop</span></span>
- <span data-ttu-id="4473a-119">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="4473a-119">Surface Studio</span></span>
- <span data-ttu-id="4473a-120">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="4473a-120">Surface Studio 2</span></span>
- <span data-ttu-id="4473a-121">Surface Book</span><span class="sxs-lookup"><span data-stu-id="4473a-121">Surface Book</span></span>
- <span data-ttu-id="4473a-122">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="4473a-122">Surface Pro 4</span></span>
- <span data-ttu-id="4473a-123">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="4473a-123">Surface 3 LTE</span></span>
- <span data-ttu-id="4473a-124">Surface 3</span><span class="sxs-lookup"><span data-stu-id="4473a-124">Surface 3</span></span>
- <span data-ttu-id="4473a-125">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="4473a-125">Surface Pro 3</span></span>


<span data-ttu-id="4473a-126">Surface アプリは、次Microsoft Store Surface 固有の設定とオプションを制御できる軽量なアプリです。</span><span class="sxs-lookup"><span data-stu-id="4473a-126">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="4473a-127">Surface デバイスの Windows ボタンを有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="4473a-127">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="4473a-128">Surface ペンの感度を調整する
</span><span class="sxs-lookup"><span data-stu-id="4473a-128">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="4473a-129">Surface ペンのボタンの操作をカスタマイズする
</span><span class="sxs-lookup"><span data-stu-id="4473a-129">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="4473a-130">Surface のオーディオ拡張機能を有効または無効にする
</span><span class="sxs-lookup"><span data-stu-id="4473a-130">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="4473a-131">デバイスのサポート ドキュメントと情報へのクイック アクセス</span><span class="sxs-lookup"><span data-stu-id="4473a-131">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="4473a-132">更新プログラムをWindowsユーザーは、通常、自動更新の一部として Surface アプリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4473a-132">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="4473a-133">ただし、組織が Surface デバイスへの展開用にイメージを準備している場合は、個々のデバイスのユーザーが Microsoft Store または ビジネス向け Microsoft Store からアプリをダウンロードしてインストールする必要が生じなくても、Surface アプリ (以前は Surface Hub) をイメージングおよび展開プロセスに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-133">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="4473a-134">この記事は、X のSurface Proされません。詳細については、「X の展開、管理、およびサービス[」をSurface Proしてください。](surface-pro-arm-app-management.md)</span><span class="sxs-lookup"><span data-stu-id="4473a-134">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <a name="surface-app-overview"></a><span data-ttu-id="4473a-135">Surface アプリの概要</span><span class="sxs-lookup"><span data-stu-id="4473a-135">Surface app overview</span></span>

<span data-ttu-id="4473a-136">Surface アプリは、アプリから無料でダウンロード[Microsoft Store。](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)</span><span class="sxs-lookup"><span data-stu-id="4473a-136">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="4473a-137">ユーザーは Microsoft Store からダウンロードしてインストールできますが、組織で代わりに ビジネス向け Microsoft Store を使用している場合は、ストアのインベントリに追加し、Windows 展開プロセスの一部としてアプリを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-137">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="4473a-138">これらのプロセスについては、この記事で説明します。</span><span class="sxs-lookup"><span data-stu-id="4473a-138">These processes are discussed throughout this article.</span></span> <span data-ttu-id="4473a-139">このサイトの詳細についてはビジネス向け Microsoft Store [TechCenter](https://docs.microsoft.com/microsoft-store/)のビジネス向け Microsoft StoreをWindowsしてください。</span><span class="sxs-lookup"><span data-stu-id="4473a-139">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <a name="add-surface-app-to-a-microsoft-store-for-business-account"></a><span data-ttu-id="4473a-140">Surface アプリをアカウントにビジネス向け Microsoft Storeする</span><span class="sxs-lookup"><span data-stu-id="4473a-140">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="4473a-141">ユーザーが会社の ビジネス向け Microsoft Store アカウントからアプリをインストールまたは展開する前に、目的のアプリを最初に使用可能にし、ビジネスのユーザーにライセンスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-141">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="4473a-142">まだ作成していない場合は、アカウントを作成ビジネス向け Microsoft Store[します](https://www.microsoft.com/business-store)。</span><span class="sxs-lookup"><span data-stu-id="4473a-142">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="4473a-143">ポータルにログオンします。</span><span class="sxs-lookup"><span data-stu-id="4473a-143">Log on to the portal.</span></span> 

3. <span data-ttu-id="4473a-144">オフライン ライセンスを有効にする: **[Manage->ストア**の設定]\*\*\*\* をクリックし、図 1 に示すように、[ストアで購入するユーザーにオフライン ライセンス アプリを表示する] チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4473a-144">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="4473a-145">アプリ のライセンス モデルのビジネス向け Microsoft Store詳細については、「アプリ」および[「Education ビジネス向け Microsoft Store」を参照してください](https://docs.microsoft.com/microsoft-store/)。</span><span class="sxs-lookup"><span data-stu-id="4473a-145">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span>

   > [!div class="mx-imgBorder"]
   > ![[オフライン ライセンス アプリを表示する] チェック ボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="4473a-147">図 1.</span><span class="sxs-lookup"><span data-stu-id="4473a-147">Figure 1.</span></span> <span data-ttu-id="4473a-148">オフラインで使用するアプリを有効にする</span><span class="sxs-lookup"><span data-stu-id="4473a-148">Enable apps for offline use</span></span>*

4. <span data-ttu-id="4473a-149">次の手順に従って、ビジネス向け Microsoft Storeに Surface アプリを追加します。</span><span class="sxs-lookup"><span data-stu-id="4473a-149">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>

    * <span data-ttu-id="4473a-150">[ショップ] **メニューをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="4473a-150">Click the **Shop** menu.</span></span>
    
    * <span data-ttu-id="4473a-151">検索ボックスに **「Surface app」と入力**し、検索アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4473a-151">In the search box, type **Surface app**, and then click the search icon.</span></span>
    
    * <span data-ttu-id="4473a-152">Surface アプリが検索結果に表示された後、アプリのアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4473a-152">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    
    * <span data-ttu-id="4473a-153">図 2 に示すように、選択項目 **([オンライン** ] または [ **オフライン**] を選択) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4473a-153">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンス モードを選択し、アプリをインベントリに追加する](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *<span data-ttu-id="4473a-155">図 2.</span><span class="sxs-lookup"><span data-stu-id="4473a-155">Figure 2.</span></span> <span data-ttu-id="4473a-156">オフライン ライセンス モードを選択し、アプリをインベントリに追加する</span><span class="sxs-lookup"><span data-stu-id="4473a-156">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="4473a-157">[ **オフライン] を** クリックしてオフライン ライセンス モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="4473a-157">Click **Offline** to select the Offline licensing mode.</span></span>
    
    * <span data-ttu-id="4473a-158">[**アプリの取得] を**クリックして、アプリをインベントリにビジネス向け Microsoft Storeします。</span><span class="sxs-lookup"><span data-stu-id="4473a-158">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="4473a-159">図 3 に示すように、管理ツールを使用してオフライン アプリを展開するか、プライベート ストアの会社の在庫ページからダウンロードできると確認するダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4473a-159">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![<span data-ttu-id="4473a-160">オフライン ライセンスのアプリ確認ウィンドウ図 ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *3.オフライン ライセンスのアプリの確認*</span><span class="sxs-lookup"><span data-stu-id="4473a-160">Offline-licensed app acknowledgement window](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
*Figure 3. Offline-licensed app acknowledgement*</span></span>
      
    * <span data-ttu-id="4473a-161">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4473a-161">Click **OK**.</span></span>

## <a name="download-surface-app-from-a-microsoft-store-for-business-account"></a><span data-ttu-id="4473a-162">Surface アプリをアカウントからビジネス向け Microsoft Storeする</span><span class="sxs-lookup"><span data-stu-id="4473a-162">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="4473a-163">オフライン モードでアプリを ビジネス向け Microsoft Store アカウントに追加した後、アプリを AppxBundle として展開共有にダウンロードして追加できます。</span><span class="sxs-lookup"><span data-stu-id="4473a-163">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>

1. <span data-ttu-id="4473a-164">でアカウントにビジネス向け Microsoft Storeします https://businessstore.microsoft.com 。</span><span class="sxs-lookup"><span data-stu-id="4473a-164">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>

2. <span data-ttu-id="4473a-165">[ **アプリの管理] >ソフトウェア&クリックします**。</span><span class="sxs-lookup"><span data-stu-id="4473a-165">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="4473a-166">この記事の [Surface アプリを ビジネス向け Microsoft Store アカウントに追加した Surface アプリを含む、会社[のすべてのアプリ](#add-surface-app-to-a-microsoft-store-for-business-account)の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4473a-166">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>

3. <span data-ttu-id="4473a-167">[ **アクション]** で、省略記号 (**...) を**クリックし、[Surface アプリのオフラインで使用するために **ダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4473a-167">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>

4. <span data-ttu-id="4473a-168">図 4**に示**すように、選択したアプリで使用可能な選択項目から、目的のプラットフォームとアーキテクチャのオプションを選択します。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4473a-168">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    > [!div class="mx-imgBorder"]
    > ![AppxBundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *<span data-ttu-id="4473a-170">図 4: </span><span class="sxs-lookup"><span data-stu-id="4473a-170">Figure 4.</span></span> <span data-ttu-id="4473a-171">アプリの AppxBundle パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="4473a-171">Download the AppxBundle package for an app</span></span>*
    
5. <span data-ttu-id="4473a-172">[ダウンロード **] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="4473a-172">Click **Download**.</span></span> <span data-ttu-id="4473a-173">AppxBundle パッケージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="4473a-173">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="4473a-174">この記事の後半で必要になりますので、ダウンロードしたファイルのパスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4473a-174">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>

6. <span data-ttu-id="4473a-175">[エンコードされた**ライセンス] または [\*\*\*\*コード化されていないライセンス] オプションをクリック**します。</span><span class="sxs-lookup"><span data-stu-id="4473a-175">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="4473a-176">[エンコードされたライセンス] オプションは、Microsoft Endpoint Configuration Managerのような管理ツールを使用するか、Windows構成デザイナーを使用してプロビジョニング パッケージを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="4473a-176">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="4473a-177">展開イメージ サービスおよび管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft Deployment Toolkit (MDT) を使用する場合は、[コード化されていないライセンス] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4473a-177">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>

7. <span data-ttu-id="4473a-178">[ **生成] を** クリックして、アプリのライセンスを生成してダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4473a-178">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="4473a-179">この記事の後半で必要になりますので、ライセンス ファイルのパスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4473a-179">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="4473a-180">Surface アプリなどのオフラインで使用するアプリをダウンロードすると、[必須フレームワーク] というラベルが付いたページの下部にセクション **が表示されることがあります**。</span><span class="sxs-lookup"><span data-stu-id="4473a-180">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="4473a-181">対象のコンピューターには、アプリを実行するフレームワークがインストールされている必要があります。そのため、アーキテクチャに必要な各フレームワーク (x86 または x64) のダウンロード プロセスを繰り返し、この記事で後で説明する Windows 展開の一部として含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-181">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="4473a-182">図 5 は、Surface アプリに必要なフレームワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="4473a-182">Figure 5 shows the required frameworks for the Surface app.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface アプリに必要なフレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*<span data-ttu-id="4473a-184">図 5: </span><span class="sxs-lookup"><span data-stu-id="4473a-184">Figure 5.</span></span> <span data-ttu-id="4473a-185">Surface アプリに必要なフレームワーク</span><span class="sxs-lookup"><span data-stu-id="4473a-185">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="4473a-186">Surface アプリと必要なフレームワークのバージョン番号は、アプリの更新に応じて変更されます。</span><span class="sxs-lookup"><span data-stu-id="4473a-186">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="4473a-187">Surface アプリと各フレームワークの最新バージョンを確認ビジネス向け Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="4473a-187">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="4473a-188">常に Surface アプリと推奨されるフレームワーク バージョンを使用します (このバージョンビジネス向け Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="4473a-188">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="4473a-189">古いフレームワークや正しくないバージョンを使用すると、エラーやアプリケーションがクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-189">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="4473a-190">Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4473a-190">To download the required frameworks for the Surface app, follow these steps:</span></span>

1. <span data-ttu-id="4473a-191">**Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4473a-191">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="4473a-192">これにより、Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe がダウンロードされます。指定したフォルダーへの Appx ファイル。</span><span class="sxs-lookup"><span data-stu-id="4473a-192">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

2. <span data-ttu-id="4473a-193">[ダウンロード **] ボタン** をクリック **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span><span class="sxs-lookup"><span data-stu-id="4473a-193">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="4473a-194">これにより、Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx ファイルが指定したフォルダーにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="4473a-194">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="4473a-195">Surface デバイスには、各フレームワークの 64 ビット (x64) バージョンだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="4473a-195">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="4473a-196">Surface デバイスはネイティブの 64 ビット UEFI デバイスであり、32 ビット フレームワークを必要とする 32 ビット (x86) バージョンの Windows と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="4473a-196">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <a name="install-surface-app-on-your-computer-with-powershell"></a><span data-ttu-id="4473a-197">PowerShell を使用して Surface アプリをコンピューターにインストールする</span><span class="sxs-lookup"><span data-stu-id="4473a-197">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="4473a-198">次の手順では、Surface アプリをコンピューターにプロビジョニングし、その後コンピューターで作成されたユーザー アカウントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4473a-198">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>

1. <span data-ttu-id="4473a-199">この記事の「ビジネス向け Microsoft Store アカウントから[Surface](#download-surface-app-from-a-microsoft-store-for-business-account)アプリをダウンロードする方法」セクションで説明されている手順を使用して、Surface アプリ AppxBundle とライセンス ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4473a-199">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="4473a-200">管理者特権で PowerShell セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="4473a-200">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4473a-201">PowerShell を管理者として実行しない場合、セッションにはアプリのインストールに必要なアクセス許可はありません。</span><span class="sxs-lookup"><span data-stu-id="4473a-201">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="4473a-202">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4473a-202">In the elevated PowerShell session, copy and paste the following command:</span></span>

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="4473a-203">AppxBundle とライセンス ファイルをアカウントからダウンロードした `<DownloadPath>` フォルダーはビジネス向け Microsoft Storeです。</span><span class="sxs-lookup"><span data-stu-id="4473a-203">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="4473a-204">たとえば、ファイルを c:\Temp にダウンロードした場合、実行するコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4473a-204">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. <span data-ttu-id="4473a-205">これで、Surface アプリは現在の Windows コンピューターで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="4473a-205">The Surface app will now be available on your current Windows computer.</span></span> 

   <span data-ttu-id="4473a-206">Surface アプリがプロビジョニングされているコンピューターで機能する前に、この記事で前述したフレームワークも準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4473a-206">Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article.</span></span> <span data-ttu-id="4473a-207">これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した昇格された PowerShell セッションで次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="4473a-207">To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.</span></span>

5. <span data-ttu-id="4473a-208">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4473a-208">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. <span data-ttu-id="4473a-209">管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4473a-209">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <a name="install-surface-app-with-mdt"></a><span data-ttu-id="4473a-210">MDT を使用して Surface アプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="4473a-210">Install Surface app with MDT</span></span>
<span data-ttu-id="4473a-211">次の手順では、MDT を使用して、展開時に Surface アプリのインストールを自動化します。</span><span class="sxs-lookup"><span data-stu-id="4473a-211">The following procedure uses MDT to automate installation of the Surface app at the time of deployment.</span></span> <span data-ttu-id="4473a-212">アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4473a-212">The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images.</span></span> <span data-ttu-id="4473a-213">これは、Surface デバイスへの Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。これは、Windows イメージのクロス プラットフォームの互換性を低下さないのでです。</span><span class="sxs-lookup"><span data-stu-id="4473a-213">This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.</span></span>

1. <span data-ttu-id="4473a-214">この記事で前述 [した手順を使用して](#download-surface-app-from-a-microsoft-store-for-business-account)、Surface アプリ AppxBundle とライセンス ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4473a-214">Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="4473a-215">MDT 展開ワークベンチで新しいアプリケーション ウィザードを使用して、ダウンロードしたファイルを新しいアプリケーションとしてインポートし、ソース ファイル **を使用します**。</span><span class="sxs-lookup"><span data-stu-id="4473a-215">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="4473a-216">新しい**アプリケーション ウィザードの**[コマンドの詳細] ページ\*\*\*\* で、既定の作業ディレクトリを指定し **、Command**に AppxBundle のファイル名を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="4473a-216">On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:</span></span>

   * <span data-ttu-id="4473a-217">コマンド:</span><span class="sxs-lookup"><span data-stu-id="4473a-217">Command:</span></span>
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * <span data-ttu-id="4473a-218">作業ディレクトリ: %DEPLOYROOT%\Applications\SurfaceApp</span><span class="sxs-lookup"><span data-stu-id="4473a-218">Working Directory: %DEPLOYROOT%\Applications\SurfaceApp</span></span>

<span data-ttu-id="4473a-219">Surface アプリがターゲット コンピューターで機能するには、この記事で前述したフレームワークも必要です。</span><span class="sxs-lookup"><span data-stu-id="4473a-219">For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article.</span></span> <span data-ttu-id="4473a-220">Surface アプリに必要なフレームワークを MDT にインポートし、依存関係として構成するには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="4473a-220">Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.</span></span>

1. <span data-ttu-id="4473a-221">この記事で前述した手順を使用して、フレームワーク ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4473a-221">Using the procedure described earlier in this article, download the framework files.</span></span> <span data-ttu-id="4473a-222">各フレームワークを個別のフォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="4473a-222">Store each framework in a separate folder.</span></span>

2. <span data-ttu-id="4473a-223">MDT 展開ワークベンチで新しいアプリケーション ウィザードを使用して、ダウンロードしたファイルを新しいアプリケーションとしてインポートし、ソース ファイル **を使用します**。</span><span class="sxs-lookup"><span data-stu-id="4473a-223">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="4473a-224">[コマンド**の詳細]** ページで、ダウンロードした各アプリケーションのファイル名を\*\*\*\*[コマンド] フィールドと既定の作業ディレクトリに入力します。</span><span class="sxs-lookup"><span data-stu-id="4473a-224">On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.</span></span>

<span data-ttu-id="4473a-225">Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4473a-225">To configure the frameworks as dependencies of the Surface app, use this process:</span></span>

1. <span data-ttu-id="4473a-226">MDT 展開ワークベンチで Surface アプリのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="4473a-226">Open the properties of the Surface app in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="4473a-227">[依存関係] **タブをクリック** し、[追加] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="4473a-227">Click the **Dependencies** tab, and then click **Add**.</span></span>

3. <span data-ttu-id="4473a-228">新しいアプリケーション ウィザードで指定した名前を使用して、各フレームワークのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4473a-228">Select the check box for each framework using the name you provided in the New Application Wizard.</span></span>

<span data-ttu-id="4473a-229">インポート後、Surface アプリは、展開ウィザードの **[アプリケーション**] Windows選択できます。</span><span class="sxs-lookup"><span data-stu-id="4473a-229">After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard.</span></span> <span data-ttu-id="4473a-230">次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4473a-230">You can also install the application automatically by specifying the application in the deployment task sequence by following this process:</span></span>

1. <span data-ttu-id="4473a-231">MDT の Deployment Workbench で、展開タスク シーケンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="4473a-231">Open your deployment task sequence in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="4473a-232">展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="4473a-232">Add a new **Install Application** task in the **State Restore** section of deployment.</span></span>

3. <span data-ttu-id="4473a-233">[ **単一のアプリケーションをインストールする** ] を選択し、 **インストール** する **アプリケーションとして Surface App を指定します**。</span><span class="sxs-lookup"><span data-stu-id="4473a-233">Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.</span></span>

<span data-ttu-id="4473a-234">アプリを展開環境に含Windows詳細については、「Deploy Windows 10 with [the Microsoft Deployment Toolkit」 を参照してください](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)。</span><span class="sxs-lookup"><span data-stu-id="4473a-234">For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).</span></span>
