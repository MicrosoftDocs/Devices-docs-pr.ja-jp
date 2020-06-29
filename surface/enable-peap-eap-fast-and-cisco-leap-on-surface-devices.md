---
title: Surface デバイスで PEAP、EAP-FAST、Cisco LEAP を有効にする (Surface)
description: Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP プロトコルのサポートを有効にする方法を説明します。
ms.assetid: A281EFA3-1552-467D-8A21-EB151E58856D
ms.reviewer: ''
manager: laurawi
keywords: ネットワーク, ワイヤレス, デバイス, 展開, 認証, プロトコル, network, wireless, device, deploy, authentication, protocol
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 1a9bef0a6e0bfdd4bede1b508b4013fd14e1a0bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835973"
---
# <span data-ttu-id="e5488-104">Surface デバイスで PEAP、EAP-FAST、Cisco LEAP を有効にする</span><span class="sxs-lookup"><span data-stu-id="e5488-104">Enable PEAP, EAP-FAST, and Cisco LEAP on Surface devices</span></span>


<span data-ttu-id="e5488-105">Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP プロトコルのサポートを有効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e5488-105">Find out how to enable support for PEAP, EAP-FAST, or Cisco LEAP protocols on your Surface device.</span></span>

<span data-ttu-id="e5488-106">エンタープライズ ネットワークで PEAP、EAP-FAST、または Cisco LEAP を使っている場合は、導入直後の Surface デバイスではこれら 3 つのワイヤレス認証プロトコルがサポートされていないことを既にご存じかもしれません。</span><span class="sxs-lookup"><span data-stu-id="e5488-106">If you use PEAP, EAP-FAST, or Cisco LEAP in your enterprise network, you probably already know that these three wireless authentication protocols are not supported by Surface devices out of the box.</span></span> <span data-ttu-id="e5488-107">ワイヤレス ネットワークに接続しようとしたときに気付くユーザーや、ファイル共有や内部サイトなどのネットワーク内部のリソースにアクセスできないときに気付くユーザーもいます。</span><span class="sxs-lookup"><span data-stu-id="e5488-107">Some users may discover this when they attempt to connect to your wireless network; others may discover it when they are unable to gain access to resources inside the network, like file shares and internal sites.</span></span> <span data-ttu-id="e5488-108">詳しくは、[拡張認証プロトコルに関するページ](https://technet.microsoft.com/network/bb643147)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5488-108">For more information, see [Extensible Authentication Protocol](https://technet.microsoft.com/network/bb643147).</span></span>

<span data-ttu-id="e5488-109">USB スティックやファイル共有から小さな MSI パッケージを実行することで、各プロトコルのサポートを追加できます。</span><span class="sxs-lookup"><span data-stu-id="e5488-109">You can add support for each protocol by executing a small MSI package from a USB stick or from a file share.</span></span> <span data-ttu-id="e5488-110">Surface デバイスで EAP のサポートを有効にする組織の場合、MSI パッケージ形式では、Microsoft 展開ツールキット (MDT) や Microsoft Endpoint Configuration Manager などのさまざまな管理ツールと展開ツールを使用して展開をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e5488-110">For organizations that want to enable EAP support on their Surface devices, the MSI package format supports deployment with many management and deployment tools, like the Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager.</span></span>

## <a href="" id="download-peap--eap-fast--or-cisco-leap-installation-files--"></a><span data-ttu-id="e5488-111">PEAP、EAP-FAST、または Cisco LEAP のインストール ファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e5488-111">Download PEAP, EAP-FAST, or Cisco LEAP installation files</span></span>


<span data-ttu-id="e5488-112">PEAP、EAP-FAST、または Cisco LEAP のインストール ファイルを、Microsoft ダウンロード センターから 1 つの zip アーカイブ ファイルでダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e5488-112">You can download the MSI installation files for PEAP, EAP-FAST, or Cisco LEAP in a single zip archive file from the Microsoft Download Center.</span></span> <span data-ttu-id="e5488-113">このファイルをダウンロードするには、Microsoft ダウンロード センターの [IT 向け Surface ツールに関するページ](https://www.microsoft.com/download/details.aspx?id=46703)で、**[ダウンロード]** をクリックし、**[Cisco EAP-Supplicant Installer.zip]** ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e5488-113">To download this file, go to the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page on the Microsoft Download Center, click **Download**, and then select the **Cisco EAP-Supplicant Installer.zip** file.</span></span>

## <span data-ttu-id="e5488-114">MDT で PEAP、EAP-FAST、または Cisco LEAP を展開する</span><span class="sxs-lookup"><span data-stu-id="e5488-114">Deploy PEAP, EAP-FAST, or Cisco LEAP with MDT</span></span>


<span data-ttu-id="e5488-115">組織内で Surface デバイスへの Windows の展開を既に行っている場合は、展開中に各プロトコルのインストール ファイルを展開共有に追加し、自動インストールを構成する方法が迅速かつ簡単です。</span><span class="sxs-lookup"><span data-stu-id="e5488-115">If you are already performing a Windows deployment to Surface devices in your organization, it is quick and easy to add the installation files for each protocol to your deployment share and configure automatic installation during deployment.</span></span> <span data-ttu-id="e5488-116">以前に展開した Surface デバイスを更新するタスク シーケンスを構成して、同じプロセスを使ってこれらのプロトコルのサポートを提供するようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e5488-116">You can even configure a task sequence that updates previously deployed Surface devices to provide support for these protocols using the same process.</span></span>

<span data-ttu-id="e5488-117">新たに展開された Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP のサポートを有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e5488-117">To enable support for PEAP, EAP-FAST, or Cisco LEAP on newly deployed Surface devices, follow these steps:</span></span>

1.  <span data-ttu-id="e5488-118">各プロトコルのインストール ファイルをダウンロードし、簡単にアクセス可能な場所の個別フォルダーに抽出します。</span><span class="sxs-lookup"><span data-stu-id="e5488-118">Download and extract the installation files for each protocol to separate folders in an easily accessible location.</span></span>

2.  <span data-ttu-id="e5488-119">MDT の Deployment Workbench を開き、展開共有を **Applications** フォルダーに展開します。</span><span class="sxs-lookup"><span data-stu-id="e5488-119">Open the MDT Deployment Workbench and expand your deployment share to the **Applications** folder.</span></span>

3.  <span data-ttu-id="e5488-120">**[操作]** ウィンドウから、**[新しいアプリケーション]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="e5488-120">Select **New Application** from the **Action** pane.</span></span>

4.  <span data-ttu-id="e5488-121">**[Application with source files]** (アプリケーションとソース ファイル) を選択して、MSI ファイルを展開共有にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e5488-121">Choose **Application with source files** to copy the MSI files into the Deployment Share.</span></span>

5.  <span data-ttu-id="e5488-122">目的のプロトコルの手順 1 で作成したフォルダーを選びます。</span><span class="sxs-lookup"><span data-stu-id="e5488-122">Select the folder you created in step 1 for the desired protocol.</span></span>

6.  <span data-ttu-id="e5488-123">インストール ファイルが格納される展開共有でフォルダーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e5488-123">Name the folder in the deployment share where the installation files will be stored.</span></span>

7.  <span data-ttu-id="e5488-124">次のように、アプリケーションを展開するコマンド ラインを指定します。</span><span class="sxs-lookup"><span data-stu-id="e5488-124">Specify the command line to deploy the application:</span></span>

    -   <span data-ttu-id="e5488-125">PEAP の場合は、**EAP PEAP.msi/qn/norestart** を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5488-125">For PEAP use **EAP-PEAP.msi /qn /norestart**.</span></span>

    -   <span data-ttu-id="e5488-126">LEAP の場合は、**EAP-LEAP.msi/qn/norestart** を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5488-126">For LEAP use **EAP-LEAP.msi /qn /norestart**.</span></span>

    -   <span data-ttu-id="e5488-127">EAP-FAST の場合は、**EAP FAST.msi/qn/norestart** を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5488-127">For EAP-FAST use **EAP-FAST.msi /qn /norestart**.</span></span>

8.  <span data-ttu-id="e5488-128">既定のオプションを使用して、New Application Wizard (新しいアプリケーション ウィザード) を完了します。</span><span class="sxs-lookup"><span data-stu-id="e5488-128">Use the default options to complete the New Application Wizard.</span></span>

9.  <span data-ttu-id="e5488-129">目的のプロトコルごとに手順 3 ～ 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e5488-129">Repeat steps 3 through 8 for each desired protocol.</span></span>

<span data-ttu-id="e5488-130">これらの手順に従って 3 つの MSI パッケージをアプリケーションとして MDT にインポートしたら、Windows 展開ウィザードの [アプリケーション] ページでそれらを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e5488-130">After you’ve performed these steps to import the three MSI packages as applications into MDT, they will be available for selection in the Applications page of the Windows Deployment Wizard.</span></span> <span data-ttu-id="e5488-131">一部の簡単な展開シナリオでは、展開時に技術者が各パッケージを選ぶだけで十分な場合もありますが、それは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="e5488-131">Although in some simple deployment scenarios it might be sufficient to have technicians select each package at the time of deployment, it is not recommended.</span></span> <span data-ttu-id="e5488-132">このやり方では、ヒューマン エラーのために技術者が Surface デバイス以外のコンピューターにこれらのパッケージを適用しようとしたり、EAP サポートなしで Surface デバイスが展開されたりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5488-132">This practice introduces the possibility that a technician could attempt to apply these packages to computers other than Surface devices, or that a Surface device could be deployed without EAP support due to human error.</span></span>

<span data-ttu-id="e5488-133">[アプリケーションのインストール] ページでこれらのアプリケーションを非表示にするには、各アプリケーションのプロパティで **[Hide this application in the Deployment Wizard]** (展開ウィザードでこのアプリケーションを非表示にする) チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e5488-133">To hide these applications from the Install Applications page, select the **Hide this application in the Deployment Wizard** checkbox in the properties of each application.</span></span> <span data-ttu-id="e5488-134">アプリケーションを非表示にすると、それらは展開中にオプションのアプリケーションとして表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="e5488-134">After the applications are hidden, they will not be displayed as optional applications during deployment.</span></span> <span data-ttu-id="e5488-135">非表示のアプリケーションを Surface の展開タスク シーケンスで展開するには、それらをタスク シーケンス内の別のステップを通じたインストール向けに明示的に定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5488-135">To deploy them in your Surface deployment task sequence, they must be explicitly defined for installation through a separate step in the task sequence.</span></span>

<span data-ttu-id="e5488-136">プロトコルを明示的に指定するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e5488-136">To specify the protocol(s) explicitly, follow these steps:</span></span>

1.  <span data-ttu-id="e5488-137">MDT の Deployment Workbench から、Surface の展開タスク シーケンスのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="e5488-137">Open your Surface deployment task sequence properties from the MDT Deployment Workbench.</span></span>

2.  <span data-ttu-id="e5488-138">**[タスク シーケンス]** タブで、**[状態の復元]** の **[アプリケーションのインストール]** ステップを選びます。</span><span class="sxs-lookup"><span data-stu-id="e5488-138">On the **Task Sequence** tab, select the **Install Applications** step under **State Restore**.</span></span> <span data-ttu-id="e5488-139">これは通常、Windows Update の Pre-application ステップと Post-application ステップの間にあります。</span><span class="sxs-lookup"><span data-stu-id="e5488-139">This is typically found between the pre-application and post-application Windows Update steps.</span></span>

3.  <span data-ttu-id="e5488-140">**[追加]** ボタンを使って、**[全般]** カテゴリから新しい **[アプリケーションのインストール]** ステップを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5488-140">Use the **Add** button to create a new **Install Application** step from the **General** category.</span></span>

4.  <span data-ttu-id="e5488-141">ステップの **[プロパティ]** タブで **[アプリケーションを 1 つだけインストールする]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="e5488-141">Select **Install a single application** in the step **Properties** tab.</span></span>

5.  <span data-ttu-id="e5488-142">一覧から目的の EAP プロトコルを選びます。</span><span class="sxs-lookup"><span data-stu-id="e5488-142">Select the desired EAP protocol from the list.</span></span>

6.  <span data-ttu-id="e5488-143">目的のプロトコルごとに手順 2 ～ 5 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e5488-143">Repeat steps 2 through 5 for each desired protocol.</span></span>

## <span data-ttu-id="e5488-144">Configuration Manager で PEAP、EAP-FAST、または Cisco LEAP を展開する</span><span class="sxs-lookup"><span data-stu-id="e5488-144">Deploy PEAP, EAP-FAST, or Cisco LEAP with Configuration Manager</span></span>


<span data-ttu-id="e5488-145">Configuration Manager で Surface デバイスを管理する組織の場合は、さらに簡単に PEAP、EAP-FAST、または Cisco LEAP のサポートを Surface デバイスに展開できます。</span><span class="sxs-lookup"><span data-stu-id="e5488-145">For organizations that manage Surface devices with Configuration Manager, it is even easier to deploy PEAP, EAP-FAST, or Cisco LEAP support to Surface devices.</span></span> <span data-ttu-id="e5488-146">ソフトウェア ライブラリからアプリケーションとして各 MSI ファイルをインポートし、Surface デバイス コレクションへの展開を構成するだけです。</span><span class="sxs-lookup"><span data-stu-id="e5488-146">Simply import each MSI file as an application from the Software Library and configure a deployment to your Surface device collection.</span></span>

<span data-ttu-id="e5488-147">Configuration Manager でアプリケーションを展開する方法について詳しくは、「[Configuration Manager のアプリケーションの作成方法](https://technet.microsoft.com/library/gg682159.aspx)」と「[Configuration Manager のアプリケーションの展開方法](https://technet.microsoft.com/library/gg682082.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5488-147">For more information on how to deploy applications with Configuration Manager see [How to Create Applications in Configuration Manager](https://technet.microsoft.com/library/gg682159.aspx) and [How to Deploy Applications in Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx).</span></span>

 

 





