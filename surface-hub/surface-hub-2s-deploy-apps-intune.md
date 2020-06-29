---
title: Intune を使用して Surface Hub 2S にアプリを展開する
description: Intune を使用して Surface Hub 2S にアプリを展開する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 51e54a5b2881519f2fc361675253c9e50bad0864
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835686"
---
# <span data-ttu-id="fd8a3-104">Intune を使用して Surface Hub 2S にアプリを展開する</span><span class="sxs-lookup"><span data-stu-id="fd8a3-104">Deploy apps to Surface Hub 2S using Intune</span></span>

<span data-ttu-id="fd8a3-105">チームまたは組織のニーズに合わせて、追加のアプリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-105">You can install additional apps to fit your team or organization's needs.</span></span>

## <span data-ttu-id="fd8a3-106">開発者向けガイドライン</span><span class="sxs-lookup"><span data-stu-id="fd8a3-106">Developer guidelines</span></span>

- <span data-ttu-id="fd8a3-107">Surface Hub で実行できるのは、[ユニバーサル Windows プラットフォーム (UWP) アプリ](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp)のみです。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-107">Surface Hub only runs [Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp).</span></span> <span data-ttu-id="fd8a3-108">[Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) を使用して作成されたアプリは、Surface Hub では動作しません。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-108">Apps created using the [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) will not run on Surface Hub.</span></span>
- <span data-ttu-id="fd8a3-109">アプリは、[ユニバーサル デバイス ファミリ](https://msdn.microsoft.com/library/windows/apps/dn894631)または Windows チーム デバイス ファミリに対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-109">Apps must be targeted for the [Universal device family](https://msdn.microsoft.com/library/windows/apps/dn894631) or Windows Team device family.</span></span>
- <span data-ttu-id="fd8a3-110">Surface Hub は、一般[法人向け Microsoft Store](https://businessstore.microsoft.com/store)の[オフラインライセンスアプリ](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-110">Surface Hub only supports [offline-licensed apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) from [Microsoft Store for Business](https://businessstore.microsoft.com/store).</span></span>
- <span data-ttu-id="fd8a3-111">既定では、アプリをインストールするには、アプリにストアの署名が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-111">By default, apps must be Store-signed to be installed.</span></span> <span data-ttu-id="fd8a3-112">テストおよび開発時には、開発者モードでデバイスを配置することによって、開発者が署名した UWP アプリの実行を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-112">During testing and development, you can also choose to run developer-signed UWP apps by placing the device in developer mode.</span></span>
- <span data-ttu-id="fd8a3-113">Microsoft ストアへのアプリの開発と申請を行うときは、デバイスファミリの可用性と組織のライセンスオプションを設定して、Surface Hub でアプリを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-113">When developing and submitting apps to the Microsoft Store, set Device family availability and Organizational licensing options to ensure that apps are available to run on Surface Hub.</span></span>
- <span data-ttu-id="fd8a3-114">Surface Hub にアプリをインストールするには、管理者の資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-114">You need admin credentials to install apps on Surface Hub.</span></span> <span data-ttu-id="fd8a3-115">会議室や他の共有スペースで使用するように設計されています。 Surface Hub は、通常のユーザーが Microsoft Store にアクセスしてアプリをダウンロードしてインストールすることを防止します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-115">Designed for use in meeting rooms and other shared spaces, Surface Hub prevents regular users from accessing the Microsoft Store to download and install apps.</span></span>

## <span data-ttu-id="fd8a3-116">展開のガイドライン</span><span class="sxs-lookup"><span data-stu-id="fd8a3-116">Deployment guidelines</span></span>

<span data-ttu-id="fd8a3-117">Intune を使用してユニバーサル Windows プラットフォーム (UWP) アプリを Surface Hub 2S に展開し、デバイスへのアプリの展開を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-117">You can deploy Universal Windows Platform (UWP) apps to Surface Hub 2S using Intune, easing app deployment to devices.</span></span>

1. <span data-ttu-id="fd8a3-118">アプリを展開するには、組織の MDM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-118">To deploy apps, enable MDM for your organization.</span></span> <span data-ttu-id="fd8a3-119">Intune ポータルで、MDM オーソリティとして [ **Intune** ] を選択します (推奨)。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-119">In the Intune portal, select **Intune** as your MDM Authority (recommended).</span></span> <br>

    ![MDM 権限を選ぶ](images/sh2-set-intune5.png)

2. <span data-ttu-id="fd8a3-121">Intune で Microsoft Store for Business を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-121">Enable the Microsoft Store for Business in Intune.</span></span> <span data-ttu-id="fd8a3-122">Intune を開き、[**クライアントアプリ**for Business] を選択し  >  **ます。**</span><span class="sxs-lookup"><span data-stu-id="fd8a3-122">Open Intune, select **Client apps** > **Microsoft Store for Business.**</span></span> <br>

    ![ビジネス用ストアを有効にする](images/sh2-deploy-apps-sync.png)

3. <span data-ttu-id="fd8a3-124">Intune で [**ビジネス向け Microsoft Store** ] を開き、[**設定**] [  >  **Distribute**  >  **管理ツール**の配布] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-124">In Intune open **Microsoft Store for Business** and select **Settings** > **Distribute** > **Management tools**.</span></span> <span data-ttu-id="fd8a3-125">管理ツールとして**Microsoft Intune**を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-125">Choose **Microsoft Intune** as your management tool.</span></span> <br>

    ![管理ツールとして Intune を追加する](images/sh2-set-intune8.png)

4. <span data-ttu-id="fd8a3-127">[Microsoft Store for Business] で、[**設定**] ショッピング体験を選択し、[  >  **Shop**  >  **Shopping Experience\*\*\*\*オフラインアプリの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-127">In Microsoft Store for Business, select **Settings** > **Shop** > **Shopping Experience**, and then select **Show offline apps**.</span></span> <span data-ttu-id="fd8a3-128">オフラインアプリは、Intune との間で同期され、1つのデバイスに展開できるアプリを指します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-128">Offline apps refer to apps that can be synced to Intune and centrally deployed to a device.</span></span>
5. <span data-ttu-id="fd8a3-129">オフラインショッピングを有効にした後は、オフラインライセンスを取得して、Intune に同期し、デバイスライセンスとして展開することができます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-129">After enabling Offline shopping, you can acquire offline licenses for apps that you can sync to Intune and deploy as Device licensing.</span></span>
6. <span data-ttu-id="fd8a3-130">**Intune**  >  **クライアントアプリ**の  >  **Microsoft ストア for Business**で、[**同期**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-130">In **Intune** > **Client apps** > **Microsoft Store for Business**, select **Sync**.</span></span>
7. <span data-ttu-id="fd8a3-131">[クライアントアプリ] ページで、アプリの一覧からアプリを検索します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-131">In the Client apps page, search for the app in the apps list.</span></span> <span data-ttu-id="fd8a3-132">アプリを目的のデバイスグループまたはグループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-132">Assign the apps to the desired device group or groups.</span></span> <span data-ttu-id="fd8a3-133">[**課題**  >  の**追加] グループ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-133">Select **Assignments** > **Add group**.</span></span> <br>

![\* グループへのアプリの割り当て \*](images/sh2-assign-group.png) <br>

8. <span data-ttu-id="fd8a3-135">[割り当ての種類] で [**必須**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-135">Under assignment type, choose **Required**.</span></span> <br>

![\* グループへのアプリの割り当て \*](images/sh2-add-group.png) <br>

9. <span data-ttu-id="fd8a3-137">選択したグループについて、[**デバイスライセンス**] を選択し、[ **OK]** を選択して課題を保存します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-137">For the selected groups, choose **Device licensing** and then select **OK** and save the assignment.</span></span> <br>
 
![\* グループへのアプリの割り当て \*](images/sh2-apps-assign.png)
