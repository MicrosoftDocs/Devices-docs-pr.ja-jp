---
title: Surface の展開用の OOBE をカスタマイズする (Surface)
description: この記事では、Surface の Out-Of-Box Experience を組織内のエンド ユーザー向けにカスタマイズするプロセスを説明します。
ms.assetid: F6910315-9FA9-4297-8FA8-2C284A4B1D87
ms.reviewer: ''
manager: laurawi
keywords: 展開, カスタマイズ, 自動化, ネットワーク, ペン, ペアリング, ブート, deploy, customize, automate, network, Pen, pair, boot
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 97cc262d803875a76427d04c8f9b70547152f895
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835669"
---
# <span data-ttu-id="7af2f-104">Surface の展開用の OOBE をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7af2f-104">Customize the OOBE for Surface deployments</span></span>

<span data-ttu-id="7af2f-105">この記事では、組織内のエンドユーザーに対して、Surface の既定の環境をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7af2f-105">This article describes customizing the Surface out-of-box experience for end users in your organization.</span></span>

<span data-ttu-id="7af2f-106">Windows の展開では、展開するコンピューターの初回起動時のユーザー エクスペリエンス、つまり Out-Of-Box Experience (OOBE) をカスタマイズすることが一般的です。</span><span class="sxs-lookup"><span data-stu-id="7af2f-106">It is common practice in a Windows deployment to customize the user experience for the first startup of deployed computers — the out-of-box experience, or OOBE.</span></span>

>[!NOTE]
><span data-ttu-id="7af2f-107">OOBE は、ユーザー エクスペリエンスが表示される Windows セットアップのフェーズ、つまり構成パスを記述するためにもよく使われます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-107">OOBE is also often used to describe the phase, or configuration pass, of Windows setup during which the user experience is displayed.</span></span> <span data-ttu-id="7af2f-108">セットアップの OOBE フェーズについて詳しくは、「[構成パスのしくみ](https://msdn.microsoft.com/library/windows/hardware/dn898581.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-108">For more information about the OOBE phase of setup, see [How Configuration Passes Work](https://msdn.microsoft.com/library/windows/hardware/dn898581.aspx).</span></span>

<span data-ttu-id="7af2f-109">シナリオによっては、完全に自動化して、ユーザーの介在なしに展開の最後にコンピューターが使用可能になっているようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-109">In some scenarios, you may want to provide complete automation to ensure that at the end of a deployment, computers are ready for use without any interaction from the user.</span></span> <span data-ttu-id="7af2f-110">別のシナリオでは、ユーザーが必要な操作を実行したり、重要な選択肢から選択したりできるように、エクスペリエンスの主要な要素をそのままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-110">In other scenarios, you may want to leave key elements of the experience for users to perform necessary actions or select between important choices.</span></span> <span data-ttu-id="7af2f-111">Surface デバイスに展開する管理者にとっては、シナリオそれぞれに対処すべき固有の課題があります。</span><span class="sxs-lookup"><span data-stu-id="7af2f-111">For administrators deploying to Surface devices, each of these scenarios presents a unique challenge to overcome.</span></span>

> [!NOTE]
> <span data-ttu-id="7af2f-112">この記事は Surface Pro X には適用されません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-112">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

<span data-ttu-id="7af2f-113">この記事では、展開に追加の手順が必要なシナリオについて概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7af2f-113">This article provides a summary of the scenarios where a deployment might require additional steps.</span></span> <span data-ttu-id="7af2f-114">新たに展開された Surface デバイスで目的のエクスペリエンスを実現するために必要な情報についても説明します。</span><span class="sxs-lookup"><span data-stu-id="7af2f-114">It also provides the required information to ensure that the desired experience is achieved on any newly deployed Surface device.</span></span> <span data-ttu-id="7af2f-115">この記事は、展開プロセスの詳細や応答ファイル、[参照イメージ](https://technet.microsoft.com/itpro/windows/deploy/create-a-windows-10-reference-image)などの概念についてよく知っている管理者向けに書かれています。</span><span class="sxs-lookup"><span data-stu-id="7af2f-115">This article is intended for administrators who are familiar with the deployment process, as well as concepts such as answer files and [reference images](https://technet.microsoft.com/itpro/windows/deploy/create-a-windows-10-reference-image).</span></span>

>[!NOTE]
><span data-ttu-id="7af2f-116">[Microsoft 展開ツールキット (MDT)](https://go.microsoft.com/fwlink/p/?LinkId=618117)や Microsoft Endpoint Configuration Manager オペレーティングシステム展開 (OSD) などの自動展開ソリューションを使用して、セットアップの OOBE フェーズはまだ実行されていますが、展開ウィザードとタスクシーケンスで提供される設定によって自動化されています。</span><span class="sxs-lookup"><span data-stu-id="7af2f-116">Although the OOBE phase of setup is still run during a deployment with an automated deployment solution such as the [Microsoft Deployment Toolkit (MDT)](https://go.microsoft.com/fwlink/p/?LinkId=618117) or Microsoft Endpoint Configuration Manager Operating System Deployment (OSD), it is automated by the settings supplied in the Deployment Wizard and task sequence.</span></span> <span data-ttu-id="7af2f-117">詳しくは、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-117">For more information see:</span></span><br/>
>- [<span data-ttu-id="7af2f-118">Microsoft Deployment Toolkit による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="7af2f-118">Deploy Windows 10 with the Microsoft Deployment Toolkit</span></span>](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)
>- [<span data-ttu-id="7af2f-119">System Center 2012 R2 Configuration Manager による Windows 10 の展開</span><span class="sxs-lookup"><span data-stu-id="7af2f-119">Deploy Windows 10 with System Center 2012 R2 Configuration Manager</span></span>](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-system-center-2012-r2-configuration-manager)

 

## <span data-ttu-id="7af2f-120">シナリオ 1: MDT 2013 を使う OOBE でのワイヤレス ネットワーク</span><span class="sxs-lookup"><span data-stu-id="7af2f-120">Scenario 1: Wireless networking in OOBE with MDT 2013</span></span>


<span data-ttu-id="7af2f-121">OOBE 中にワイヤレス ネットワーク アダプターが存在する場合、**[ワイヤレス ネットワークへの接続]** ページが表示され、ユーザーにワイヤレス ネットワークに接続するよう求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-121">When a wireless network adapter is present during OOBE, the **Join a wireless network** page is displayed, which prompts a user to connect to a wireless network.</span></span> <span data-ttu-id="7af2f-122">このページは MDT 2013 などの展開テクノロジによって自動的に非表示にならないため、展開が完全な自動化で構成されている場合でも表示されます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-122">This page is not automatically hidden by deployment technologies, including MDT 2013, and therefore will be displayed even when a deployment is configured for complete automation.</span></span>

<span data-ttu-id="7af2f-123">自動化された展開がこのページで停止しないようにするには、応答ファイル **HideWirelessSetupInOOBE** で追加の設定を構成してページを非表示にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af2f-123">To ensure that an automated deployment is not stopped by this page, the page must be hidden by configuring an additional setting in the answer file, **HideWirelessSetupInOOBE**.</span></span> <span data-ttu-id="7af2f-124">**HideWirelessSetupInOOBE** の設定について詳しくは、[Windows の無人セットアップのリファレンスに関するページ](https://technet.microsoft.com/library/ff716213.aspx)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-124">You can find additional information about the **HideWirelessSetupInOOBE** setting in [Unattended Windows Setup Reference](https://technet.microsoft.com/library/ff716213.aspx).</span></span>

## <span data-ttu-id="7af2f-125">シナリオ 2: OOBE での Surface ペンのペアリング</span><span class="sxs-lookup"><span data-stu-id="7af2f-125">Scenario 2: Surface Pen pairing in OOBE</span></span>


<span data-ttu-id="7af2f-126">Surface Pro 3、Surface Pro 4、Surface Book、または Surface Studio をパッケージから取り出して最初に起動するとき、最初の実行エクスペリエンスには、付属する Surface ペンをデバイスとペアリングするように求めるプロンプトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7af2f-126">When you first take a Surface Pro 3, Surface Pro 4, Surface Book, or Surface Studio out of the package and start it up, the first-run experience of the factory image includes a prompt that asks you to pair the included Surface Pen to the device.</span></span> <span data-ttu-id="7af2f-127">このプロンプトは、デバイスに付属する出荷時のイメージでのみ提供され、ボリューム ライセンス サービス センターからダウンロードする Windows Enterprise インストール メディアなど、展開に使用されるその他のイメージには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="7af2f-127">This prompt is only provided by the factory image that ships with the device and is not included in other images used for deployment, such as the Windows Enterprise installation media downloaded from the Volume Licensing Service Center.</span></span> <span data-ttu-id="7af2f-128">このエクスペリエンス以外で Bluetooth Surface ペンのペアリングを行うには、コントロール パネルまたは [PC 設定] に移動して手動で Bluetooth デバイスをペアリングする必要があるため、ユーザーや技術者がこのプロンプトを使用してペアリング操作を行うようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af2f-128">Because pairing the Bluetooth Surface Pen outside of this experience requires that you enter the Control Panel or PC Settings and manually pair a Bluetooth device, you may want to have users or a technician use this prompt to perform the pairing operation.</span></span>

<span data-ttu-id="7af2f-129">OOBE で Surface ペンの出荷時のペアリング エクスペリエンスを提供するには、Surface の出荷時のイメージから参照イメージに 4 つのファイルをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af2f-129">To provide the factory Surface Pen pairing experience in OOBE, you must copy four files from the factory Surface image into the reference image.</span></span> <span data-ttu-id="7af2f-130">参照イメージをキャプチャする前に参照環境にこれらのファイルをコピーすることも、展開イメージのサービスと管理 (DISM) を使用してイメージをマウントすることで、後で追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-130">You can copy these files into the reference environment before you capture the reference image, or you can add them later by using Deployment Image Servicing and Management (DISM) to mount the image.</span></span> <span data-ttu-id="7af2f-131">次の 4 つのファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="7af2f-131">The four required files are:</span></span>

-   <span data-ttu-id="7af2f-132">%windir%\\system32\\oobe\\info\\default\\1033\\oobe.xml</span><span class="sxs-lookup"><span data-stu-id="7af2f-132">%windir%\\system32\\oobe\\info\\default\\1033\\oobe.xml</span></span>
-   <span data-ttu-id="7af2f-133">%windir%\\system32\\oobe\\info\\default\\1033\\PenPairing\_en-US.png</span><span class="sxs-lookup"><span data-stu-id="7af2f-133">%windir%\\system32\\oobe\\info\\default\\1033\\PenPairing\_en-US.png</span></span>
-   <span data-ttu-id="7af2f-134">%windir%\\system32\\oobe\\info\\default\\1033\\PenError\_en-US.png</span><span class="sxs-lookup"><span data-stu-id="7af2f-134">%windir%\\system32\\oobe\\info\\default\\1033\\PenError\_en-US.png</span></span>
-   <span data-ttu-id="7af2f-135">%windir%\\system32\\oobe\\info\\default\\1033\\PenSuccess\_en-US.png</span><span class="sxs-lookup"><span data-stu-id="7af2f-135">%windir%\\system32\\oobe\\info\\default\\1033\\PenSuccess\_en-US.png</span></span>

>[!NOTE]
><span data-ttu-id="7af2f-136">展開する予定の Surface デバイスと同じモデルの出荷時イメージからファイルをコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-136">You should copy the files from a factory image for the same model Surface device that you intend to deploy to.</span></span> <span data-ttu-id="7af2f-137">たとえば、surface Pro 7 のファイルを使用して surface Pro 7 に展開し、surface book 2 のファイルを使用して surface book 2 を展開する必要がありますが、surface Pro 7 のファイルを使用して Surface Book または Surface Pro 6 を展開しないでください。</span><span class="sxs-lookup"><span data-stu-id="7af2f-137">For example, you should use the files from a Surface Pro 7 to deploy to Surface Pro 7, and the files from Surface Book 2 to deploy Surface Book 2, but you should not use the files from a Surface Pro 7 to deploy Surface Book or Surface Pro 6.</span></span>

 

<span data-ttu-id="7af2f-138">必要なファイルをイメージに追加するための手順は、[Surface Pro 3 ペンおよび OneNote の展開のヒント](https://blogs.technet.microsoft.com/askcore/2014/07/15/deploying-surface-pro-3-pen-and-onenote-tips/)に関するページに記載されています。</span><span class="sxs-lookup"><span data-stu-id="7af2f-138">The step-by-step process for adding these required files to an image is described in [Deploying Surface Pro 3 Pen and OneNote Tips](https://blogs.technet.microsoft.com/askcore/2014/07/15/deploying-surface-pro-3-pen-and-onenote-tips/).</span></span> <span data-ttu-id="7af2f-139">このブログの投稿には、Surface ペンの Quick Note-Taking Experience に必要な更新プログラムがインストールされていることを確認するためのヒントも含まれています。これを利用すると、ユーザーはシングルクリックで OneNote にメモを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="7af2f-139">This blog post also includes tips to ensure that the necessary updates for the Surface Pen Quick Note-Taking Experience are installed, which allows users to send notes to OneNote with a single click.</span></span>

 

 





