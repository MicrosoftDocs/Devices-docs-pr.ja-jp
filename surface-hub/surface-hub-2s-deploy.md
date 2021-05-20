---
title: Surface Hub 2S 用プロビジョニング パッケージの作成
description: このページでは、プロビジョニング パッケージや他のツールSurface Hub 2S を展開する方法について説明します。
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
ms.openlocfilehash: 214a71a759358ae08eb0da7942ea190946deb327
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576867"
---
# <a name="create-provisioning-packages-for-surface-hub-2s"></a><span data-ttu-id="153c9-104">Surface Hub 2S 用プロビジョニング パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="153c9-104">Create provisioning packages for Surface Hub 2S</span></span>

<span data-ttu-id="153c9-105">構成デザイナー (WCD) Windows使用して、プロビジョニング パッケージを作成して、2S の展開Surface Hubできます。</span><span class="sxs-lookup"><span data-stu-id="153c9-105">You can use Windows Configuration Designer (WCD) to create provisioning packages to automate deployment of Surface Hub 2S.</span></span> <span data-ttu-id="153c9-106">プロビジョニング パッケージを使用して、証明書の追加、プロキシの構成、デバイス管理者とデバイス アカウントのセットアップを行います。</span><span class="sxs-lookup"><span data-stu-id="153c9-106">Use provisioning packages to add certificates, configure proxies, set up device administrators and device accounts.</span></span> <span data-ttu-id="153c9-107">構成ファイルと共にプロビジョニング パッケージを使用して、1 つの USB サム ドライブで複数の Surface Hub を展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="153c9-107">You can also use provisioning packages along with a configuration file to deploy multiple Surface Hubs with a single USB thumb drive.</span></span>

### <a name="install-windows-configuration-designer"></a><span data-ttu-id="153c9-108">Windows 構成デザイナーのインストール</span><span class="sxs-lookup"><span data-stu-id="153c9-108">Install Windows Configuration Designer</span></span>

<span data-ttu-id="153c9-109">テストWindows評価および展開キット (ADK) からWindows構成デザイナーをインストールWindows 10。</span><span class="sxs-lookup"><span data-stu-id="153c9-109">Install Windows Configuration Designer from the Windows Assessment and Deployment Kit (ADK) for Windows 10.</span></span> <span data-ttu-id="153c9-110">ADK for [Windows 10バージョン 1703 をダウンロードしてインストールします](https://go.microsoft.com/fwlink/p/?LinkId=845542)。</span><span class="sxs-lookup"><span data-stu-id="153c9-110">Download and install the [ADK for Windows 10, version 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542).</span></span> <span data-ttu-id="153c9-111">詳細については、「[Windows ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="153c9-111">For more information, see [Download and install the Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span></span>

### <a name="add-certificates"></a><span data-ttu-id="153c9-112">証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="153c9-112">Add certificates</span></span>

<span data-ttu-id="153c9-113">証明機関の証明書を 2S Surface Hubできます。</span><span class="sxs-lookup"><span data-stu-id="153c9-113">You can import Certificate Authority certificates to Surface Hub 2S.</span></span>
<span data-ttu-id="153c9-114">証明書を 2S Surface Hubするには、.cer 形式の X.509 として各証明書のコピーが必要です。</span><span class="sxs-lookup"><span data-stu-id="153c9-114">To add certificates to Surface Hub 2S, you need a copy of each certificate as X.509 in .cer format.</span></span> <span data-ttu-id="153c9-115">.crt、.pfx、その他のコンテナー形式はインポートできません。</span><span class="sxs-lookup"><span data-stu-id="153c9-115">You cannot import .crt, .pfx or other container formats.</span></span> <span data-ttu-id="153c9-116">証明書は、構成デザイナーにインポートWindows階層別に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="153c9-116">Certificates must be imported into Windows Configuration Designer and arranged by hierarchy:</span></span>

> [!div class="mx-imgBorder"]
> ![証明書を追加する](images/sh2-wcd.png)

### <a name="configure-proxy-during-oobe"></a><span data-ttu-id="153c9-118">OOBE 中にプロキシを構成する</span><span class="sxs-lookup"><span data-stu-id="153c9-118">Configure proxy during OOBE</span></span>

<span data-ttu-id="153c9-119">[Windowsデザイナー] で、[プロキシ設定の構成] タブに移動し、次に示すように適切な設定を入力します。</span><span class="sxs-lookup"><span data-stu-id="153c9-119">In Windows Configuration Designer, go to the Configure proxy settings tab and enter the appropriate settings as shown below.</span></span>

> [!div class="mx-imgBorder"]
> ![プロキシ設定の構成](images/sh2-proxy.png) 

> [!NOTE]
> <span data-ttu-id="153c9-121">プロキシ設定を構成する場合は、[\*\*\*\* セットアップ スクリプトまたはプロキシ サーバーを使用する場合は、設定を自動的に検出する] をオフにします。</span><span class="sxs-lookup"><span data-stu-id="153c9-121">When configuring proxy settings, turn off **Automatically detect settings** if you intend to use a setup script or a proxy server.</span></span> <span data-ttu-id="153c9-122">セットアップ スクリプトまたはプロキシ サーバー *を* 使用できます。両方を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="153c9-122">You can use a setup script *or* a proxy server, not both.</span></span>

### <a name="affiliate-surface-hub-2s-with-azure-active-directory"></a><span data-ttu-id="153c9-123">アフィリエイト Surface Hub 2S と Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="153c9-123">Affiliate Surface Hub 2S with Azure Active Directory</span></span>

<span data-ttu-id="153c9-124">Surface Hub 2S を Azure Active Directory に関連付けするには、プロビジョニング パッケージを使用します。Azure Active Directory グローバル管理者として、大量の新しい Windows デバイスを Azure Active Directory と Intune に一括トークンを使用して参加できます。</span><span class="sxs-lookup"><span data-stu-id="153c9-124">You can affiliate Surface Hub 2S with Azure Active Directory using a provisioning package: As an Azure Active Directory Global Administrator, you can join large numbers of new Windows devices to Azure Active Directory and Intune using a bulk token.</span></span>

<span data-ttu-id="153c9-125">一括トークンを作成するには、親しき名前を付け、有効期限 (最大 30 日間) を構成し、管理者資格情報を使用して、以下に示すようにトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="153c9-125">To create a bulk token, give it a friendly name, configure the expiration date (maximum of 30 days) and use your Admin credentials to acquire the token as shown below:</span></span>

> [!div class="mx-imgBorder"]
> ![デバイス管理者のセットアップ例 1](images/sh2-token.png)

> [!div class="mx-imgBorder"]
> ![デバイス管理者のセットアップ例 2](images/sh2-token2.png)

> [!div class="mx-imgBorder"]
> ![デバイス管理者の設定例 3](images/sh2-token3.png)


### <a name="provisioning-multiple-devices-csv-file"></a><span data-ttu-id="153c9-129">複数のデバイスをプロビジョニングする (.csv ファイル)</span><span class="sxs-lookup"><span data-stu-id="153c9-129">Provisioning multiple devices (.csv file)</span></span>

<span data-ttu-id="153c9-130">プロビジョニング パッケージに加えて、Surface Hub構成ファイルを使用して、デバイスのセットアップを簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="153c9-130">In addition to the provisioning package, you can use a Surface Hub configuration file to make it even easier to set up your devices.</span></span> <span data-ttu-id="153c9-131">このSurface Hub構成ファイルには、デバイス アカウントの一覧とワイヤレスプロジェクションの表示名が含まれる。</span><span class="sxs-lookup"><span data-stu-id="153c9-131">A Surface Hub configuration file contains a list of device accounts and friendly names for wireless projection.</span></span> <span data-ttu-id="153c9-132">最初の実行時に、構成ファイルからデバイス アカウントと分名を選択するオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="153c9-132">During first run, you get an option to choose a device account and friendly name from a configuration file.</span></span>

### <a name="to-create-a-surface-hub-configuration-file"></a><span data-ttu-id="153c9-133">構成ファイルをSurface Hubするには</span><span class="sxs-lookup"><span data-stu-id="153c9-133">To create a Surface Hub configuration file</span></span>

1. <span data-ttu-id="153c9-134">ユーザー Microsoft Excel別の CSV エディターを使用して、次の名前の CSV**ファイルをSurfaceHubConfiguration.csv**</span><span class="sxs-lookup"><span data-stu-id="153c9-134">Using Microsoft Excel or another CSV editor, create a CSV file named: **SurfaceHubConfiguration.csv**</span></span>

2. <span data-ttu-id="153c9-135">次の形式で、デバイス アカウントとユーザー名の一覧を入力します。</span><span class="sxs-lookup"><span data-stu-id="153c9-135">Enter a list of device accounts and friendly names in this format:</span></span>

    `<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>`

3. <span data-ttu-id="153c9-136">PPKG ファイルをコピーした USB サム ドライブのルートにファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="153c9-136">Save the file to the root of the USB thumb drive where you copied the PPKG file.</span></span>

    > [!div class="mx-imgBorder"]
    > ![構成ファイルの例](images/sh2-config-file.png)
