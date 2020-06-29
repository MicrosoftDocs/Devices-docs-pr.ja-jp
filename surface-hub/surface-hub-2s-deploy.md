---
title: Surface Hub 2S 用プロビジョニング パッケージの作成
description: このページでは、プロビジョニングパッケージとその他のツールを使用して Surface Hub の2S を展開する方法について説明します。
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
ms.openlocfilehash: 8f91b751a10977d80210d10ac1b48a93d9ba0f6f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836938"
---
# <span data-ttu-id="d2a86-104">Surface Hub 2S 用プロビジョニング パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="d2a86-104">Create provisioning packages for Surface Hub 2S</span></span>

<span data-ttu-id="d2a86-105">Windows 構成デザイナー (WCD) を使ってプロビジョニングパッケージを作成し、Surface Hub 2S の展開プロセスを自動化することができます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-105">You can use Windows Configuration Designer (WCD) to create provisioning packages to automate the deployment process of Surface Hub 2S.</span></span> <span data-ttu-id="d2a86-106">プロビジョニングパッケージを使用して、証明書の追加、プロキシの構成、デバイス管理者とデバイスアカウントのセットアップを行います。</span><span class="sxs-lookup"><span data-stu-id="d2a86-106">Use provisioning packages to add certificates, configure proxies, set up device administrators and device accounts.</span></span> <span data-ttu-id="d2a86-107">プロビジョニングパッケージと構成ファイルを使用して、1つの USB サムドライブで複数の Surface Hub を展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-107">You can also use provisioning packages along with a configuration file to deploy multiple Surface Hubs with a single USB thumb drive.</span></span>

### <span data-ttu-id="d2a86-108">Windows 構成デザイナーのインストール</span><span class="sxs-lookup"><span data-stu-id="d2a86-108">Install Windows Configuration Designer</span></span>

<span data-ttu-id="d2a86-109">Windows 10 の Windows アセスメント & デプロイメントキット (ADK) から Windows 構成デザイナーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d2a86-109">Install Windows Configuration Designer from the Windows Assessment and Deployment Kit (ADK) for Windows 10.</span></span> <span data-ttu-id="d2a86-110">[ADK For Windows 10 バージョン 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="d2a86-110">Download and install the [ADK for Windows 10, version 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542).</span></span> <span data-ttu-id="d2a86-111">詳細については、「 [WINDOWS ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a86-111">For more information, see [Download and install the Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span></span>

### <span data-ttu-id="d2a86-112">証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="d2a86-112">Add certificates</span></span>

<span data-ttu-id="d2a86-113">証明機関証明書は Surface Hub 2S にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-113">You can import Certificate Authority certificates to Surface Hub 2S.</span></span>
<span data-ttu-id="d2a86-114">Surface Hub 2S に証明書を追加するには、各証明書のコピーを .cer 形式で x.509 として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2a86-114">To add certificates to Surface Hub 2S, you need a copy of each certificate as X.509 in .cer format.</span></span> <span data-ttu-id="d2a86-115">.Crt、.pfx、その他のコンテナー形式をインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d2a86-115">You cannot import .crt, .pfx or other container formats.</span></span> <span data-ttu-id="d2a86-116">証明書は Windows 構成デザイナーにインポートされ、階層ごとに配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2a86-116">Certificates must be imported into Windows Configuration Designer and arranged by hierarchy:</span></span>

 ![証明書を追加する](images/sh2-wcd.png)

### <span data-ttu-id="d2a86-118">OOBE 中にプロキシを構成する</span><span class="sxs-lookup"><span data-stu-id="d2a86-118">Configure proxy during OOBE</span></span>

<span data-ttu-id="d2a86-119">Windows 構成デザイナーで、[プロキシ設定の構成] タブに移動し、次に示すように適切な設定を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2a86-119">In Windows Configuration Designer, go to the Configure proxy settings tab and enter the appropriate settings as shown below.</span></span>

 ![プロキシ設定の構成](images/sh2-proxy.png) 

> [!NOTE]
> <span data-ttu-id="d2a86-121">プロキシ設定を構成する場合、セットアップスクリプトまたはプロキシサーバーを使用する場合は、[**設定を自動的に検出**しない] をオフにします。</span><span class="sxs-lookup"><span data-stu-id="d2a86-121">When configuring proxy settings, turn off **Automatically detect settings** if you intend to use a setup script or a proxy server.</span></span> <span data-ttu-id="d2a86-122">セットアップスクリプト*また*はプロキシサーバーの両方を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2a86-122">You can use a setup script *or* a proxy server, not both.</span></span>

### <span data-ttu-id="d2a86-123">Azure Active Directory での関連 Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="d2a86-123">Affiliate Surface Hub 2S with Azure Active Directory</span></span>

<span data-ttu-id="d2a86-124">プロビジョニングパッケージを使用して、Azure Active directory と共に Surface Hub 2S を使用できます。 Azure Active Directory 全体管理者は、一括トークンを使って、多数の新しい Windows デバイスを Azure Active Directory と Intune に参加させることができます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-124">You can affiliate Surface Hub 2S with Azure Active Directory using a provisioning package: As an Azure Active Directory Global Administrator, you can join large numbers of new Windows devices to Azure Active Directory and Intune using a bulk token.</span></span>

<span data-ttu-id="d2a86-125">一括トークンを作成するには、わかりやすい名前を付け、有効期限の日付 (最大30日間) を構成し、管理者の資格情報を使ってトークンを取得します。次のようにします。</span><span class="sxs-lookup"><span data-stu-id="d2a86-125">To create a bulk token, give it a friendly name, configure the expiration date (maximum of 30 days) and use your Admin credentials to acquire the token as shown below:</span></span>

 ![デバイス管理者を設定する](images/sh2-token.png) <br><br>
 ![デバイス管理者を設定する](images/sh2-token2.png) <br><br>
 ![デバイス管理者を設定する](images/sh2-token3.png) <br><br>

### <span data-ttu-id="d2a86-129">複数のデバイスのプロビジョニング (.csv ファイル)</span><span class="sxs-lookup"><span data-stu-id="d2a86-129">Provisioning multiple devices (.csv file)</span></span>

<span data-ttu-id="d2a86-130">プロビジョニングパッケージに加えて、Surface Hub 構成ファイルを使用して、デバイスのセットアップをより簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-130">In addition to the provisioning package, you can use a Surface Hub configuration file to make it even easier to set up your devices.</span></span> <span data-ttu-id="d2a86-131">Surface Hub 構成ファイルには、ワイヤレスプロジェクションのデバイスアカウントとフレンドリ名の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2a86-131">A Surface Hub configuration file contains a list of device accounts and friendly names for wireless projection.</span></span> <span data-ttu-id="d2a86-132">初めて実行するときに、構成ファイルからデバイスアカウントとフレンドリ名を選択するオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2a86-132">During first run, you get an option to choose a device account and friendly name from a configuration file.</span></span>

### <span data-ttu-id="d2a86-133">Surface Hub 構成ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="d2a86-133">To create a Surface Hub configuration file</span></span>

1. <span data-ttu-id="d2a86-134">Microsoft Excel または別の CSV エディターを使用して、次のような CSV ファイルを作成し**SurfaceHubConfiguration.csv**</span><span class="sxs-lookup"><span data-stu-id="d2a86-134">Using Microsoft Excel or another CSV editor, create a CSV file named: **SurfaceHubConfiguration.csv**</span></span>
2. <span data-ttu-id="d2a86-135">デバイスアカウントとフレンドリ名の一覧を次の形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="d2a86-135">Enter a list of device accounts and friendly names in this format:</span></span>

```
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```

3. <span data-ttu-id="d2a86-136">ファイルを、PPKG ファイルをコピーした USB サムドライブのルートに保存します。</span><span class="sxs-lookup"><span data-stu-id="d2a86-136">Save the file to the root of the USB thumb drive where you copied the PPKG file.</span></span>

    ![構成ファイルの例](images/sh2-config-file.png)
