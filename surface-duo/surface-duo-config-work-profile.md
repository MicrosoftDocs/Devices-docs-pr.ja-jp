---
title: Surface Surface の Android Enterprise Work Profile を構成する
description: この記事では、Surface Surface の仕事用プロファイルを設定する方法について説明します。
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/25/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 393844a4e4f0f06f16d11d1313ec9aacfa109d57
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326211"
---
# <span data-ttu-id="9c0be-103">Surface Surface の Android Enterprise Work Profile を構成する</span><span class="sxs-lookup"><span data-stu-id="9c0be-103">Configure Android Enterprise Work Profile for Surface Duo</span></span>

<span data-ttu-id="9c0be-104">BYOD 展開を対象として、仕事用プロファイルは、仕事用アプリとデータ用の別の領域を、仕事用アプリとデータ用に別の領域を提供します。従業員が個人のアプリやデータにデバイスを使用するのを防ぐことなく、組織はデータ、アプリ、およびセキュリティ ポリシーを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="9c0be-104">Targeted at  BYOD deployments, work profiles provide a separate space on Duo for work apps and data, giving organizations full control of their data, apps, and security policies without preventing employees from using their device for personal apps and data.</span></span>

### <span data-ttu-id="9c0be-105">Android Enterprise Work Profile のセットアップ</span><span class="sxs-lookup"><span data-stu-id="9c0be-105">Set up Android Enterprise Work Profile</span></span>

<span data-ttu-id="9c0be-106">仕事用プロファイルを使用して、ユーザーが所有する Android デバイス上の企業データとアプリを管理します。</span><span class="sxs-lookup"><span data-stu-id="9c0be-106">Use work profiles to manage corporate data and apps on user-owned Android devices.</span></span> <span data-ttu-id="9c0be-107">既定では、個人所有の仕事用プロファイル デバイスの登録が有効になっているので、それ以上管理者の構成は必要とされません。</span><span class="sxs-lookup"><span data-stu-id="9c0be-107">By default, enrollment of personally owned work profile devices is enabled and requires no further admin configuration.</span></span>  

**<span data-ttu-id="9c0be-108">エンタープライズワーク プロファイルを有効にするには:</span><span class="sxs-lookup"><span data-stu-id="9c0be-108">To enable Enterprise Work Profile:</span></span>**

- <span data-ttu-id="9c0be-109">エンドポイント マネージャーで、[Android デバイスの登録 **]** を選択し、[仕事用プロファイルを持つ  >  \*\*\*\*  >  \*\*\*\*\*\*個人用デバイス] を選択します\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c0be-109">In Endpoint Manager, select **Devices** > **Android** > **Android enrollment** and then select **Personal devices with work profile**.</span></span>
<br><br>
 ![エンタープライズワーク プロファイルを有効にする](images/enroll-start.png)

 
**<span data-ttu-id="9c0be-111">Android Enterprise Work Profile を使用して Surface の携帯電話にサインインする</span><span class="sxs-lookup"><span data-stu-id="9c0be-111">Sign into Surface Duo with Android Enterprise Work Profile</span></span>**

1. <span data-ttu-id="9c0be-112">Google Play ストアからポータル サイト アプリをインストールし、Microsoft の会社または学校のアカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="9c0be-112">Install the Company Portal app from Google Play Store and sign in with your Microsoft work or school account.</span></span><br><br>
![Surface の合間にサインインする](images/duo-wp-1.png)
 
2. <span data-ttu-id="9c0be-114">[Access セットアップ] ページで、[開始] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9c0be-114">On the Access Setup page, select **Begin**.</span></span><br><br>
![Begin](images/duo-wp-2.png)

3. <span data-ttu-id="9c0be-116">プライバシー ページの情報を確認し、[続行] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="9c0be-116">Review the information on the privacy page and select **Continue**.</span></span><br><br>
 ![続行](images/duo-wp-3.png)
<br><br>
 ![[続行] を選択](images/duo-wp-4.png)
 
4. <span data-ttu-id="9c0be-119">作業プロファイルのセットアップが完了したら、[続行] **を選択して** デバイスのライセンス認証と登録を行います。</span><span class="sxs-lookup"><span data-stu-id="9c0be-119">When the work profile setup completes, select **Continue** to activate and register the device.</span></span><br><br>
 ![Select continue to activate and register the device](images/duo-wp-5.png)

5. <span data-ttu-id="9c0be-121">**[続行]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="9c0be-121">Select **Continue**.</span></span><br><br>
 ![もう一度 [続行] を選択する](images/duo-wp-6.png)

6. <span data-ttu-id="9c0be-123">作業プロファイルをアクティブ化した後、[続行] **を選択して** デバイス設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="9c0be-123">When you have activated the work profile, select **Continue** to update device settings.</span></span> <span data-ttu-id="9c0be-124">この例では、仕事用プロファイルで MDM 設定を適用して、より強力な 6 桁の英数字パスワードを要求します。</span><span class="sxs-lookup"><span data-stu-id="9c0be-124">In this example, the work profile applies an MDM setting to require a stronger 6-digit alphanumeric password.</span></span> <br><br>

     ![英数字パスワードの例](images/duo-wp-7.png)<br><br>
7. <span data-ttu-id="9c0be-126">[ **解決] を** 選択して必要な認証を入力し、[続行] **を選択して** ワーク プロファイルのセットアップを完了します。</span><span class="sxs-lookup"><span data-stu-id="9c0be-126">Select **Resolve** to enter the required authentication and then select **Continue** to complete Work Profile setup.</span></span> <br><br>
     ![[続行] を選択してセットアップを完了する](images/duo-wp-8.png)<br><br>
     ![セットアップの完了](images/duo-wp-9.png)<br><br>

## <span data-ttu-id="9c0be-129">詳細情報</span><span class="sxs-lookup"><span data-stu-id="9c0be-129">Learn more</span></span>

- [<span data-ttu-id="9c0be-130">Android Enterprise の仕事用プロファイル デバイスの登録を設定する</span><span class="sxs-lookup"><span data-stu-id="9c0be-130">Set up enrollment of Android Enterprise work profile devices</span></span>](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)

