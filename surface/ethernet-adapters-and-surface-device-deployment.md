---
title: イーサネット アダプターと Surface の展開 (Surface)
description: この記事では、Surface デバイスへのネットワーク展開を行うためのガイダンスと手法を示します。
ms.assetid: 5273C59E-6039-4E50-96B3-426BB38A64C0
ms.reviewer: ''
manager: laurawi
keywords: イーサネット, 展開, リムーバブル, ネットワーク, 接続, ブート, ファームウェア, デバイス, アダプター, PXE ブート, USB, ethernet, deploy, removable, network, connectivity, boot, firmware, device, adapter, PXE boot, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 4b0cfd9cadab33d82ae3d0acaa83e007229c6fb8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834709"
---
# <span data-ttu-id="bc0c1-104">イーサネット アダプターと Surface の展開</span><span class="sxs-lookup"><span data-stu-id="bc0c1-104">Ethernet adapters and Surface deployment</span></span>


<span data-ttu-id="bc0c1-105">この記事では、Surface Pro 3 以降を含む Surface デバイスへのネットワーク展開を実行するのに役立つガイダンスと回答を紹介します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-105">This article provides guidance and answers to help you perform a network deployment to Surface devices including Surface Pro 3 and later.</span></span>

<span data-ttu-id="bc0c1-106">Surface デバイスへのネットワーク展開では、システム管理者は独自の課題に対処することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-106">Network deployment to Surface devices can pose some unique challenges for system administrators.</span></span> <span data-ttu-id="bc0c1-107">ネイティブの有線イーサネット アダプターがないため、管理者はリムーバブル イーサネット アダプターを使った接続を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-107">Due to the lack of a native wired Ethernet adapter, administrators must provide connectivity through a removable Ethernet adapter.</span></span>

## <span data-ttu-id="bc0c1-108">Surface デバイス用のイーサネット アダプターを選ぶ</span><span class="sxs-lookup"><span data-stu-id="bc0c1-108">Select an Ethernet adapter for Surface devices</span></span>


<span data-ttu-id="bc0c1-109">展開環境を起動する方法や、展開ソリューションでデバイスを認識する方法に関する懸念事項に対処する前に、有線ネットワーク アダプターを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-109">Before you can address the concerns of how you will boot to your deployment environment or how devices will be recognized by your deployment solution, you have to use a wired network adapter.</span></span>

<span data-ttu-id="bc0c1-110">イーサネット アダプターを選択する際に最も重要なのは、そのアダプターでネットワークから Surface デバイスを起動する方法です。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-110">The primary concern when selecting an Ethernet adapter is how that adapter will boot your Surface device from the network.</span></span> <span data-ttu-id="bc0c1-111">Windows 展開サービス (WDS) を使ってクライアントを事前にステージングしている場合、または Microsoft Endpoint Configuration Manager を使用している場合は、リムーバブルイーサネットアダプターを特定の Surface デバイス専用にするか、複数のデバイスで共有するかを検討することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-111">If you are pre-staging clients with Windows Deployment Services (WDS) or if you are using Microsoft Endpoint Configuration Manager, you may also want to consider whether the removable Ethernet adapters will be dedicated to a specific Surface device or shared among multiple devices.</span></span> <span data-ttu-id="bc0c1-112">共有アダプターとの競合の可能性の詳細については、この記事の後半の「[リムーバブルイーサネットアダプターで MAC アドレスを管理](#manage-mac-addresses)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-112">For more information on potential conflicts with shared adapters, see [Manage MAC addresses with removable Ethernet adapters](#manage-mac-addresses) later in this article.</span></span>

<span data-ttu-id="bc0c1-113">ネットワークからの起動 (PXE ブート) は、イーサネット アダプターまたは Microsoft のドッキング ステーションを使うときにのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-113">Booting from the network (PXE boot) is only supported when you use an Ethernet adapter or docking station from Microsoft.</span></span> <span data-ttu-id="bc0c1-114">ネットワークから起動するには、Surface デバイスのファームウェアでイーサネット アダプターまたはドックのチップセットが検出され、起動デバイスとして構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-114">To boot from the network, the chipset in the Ethernet adapter or dock must be detected and configured as a boot device in the firmware of the Surface device.</span></span> <span data-ttu-id="bc0c1-115">Surface イーサネット アダプターや [Surface ドック](https://www.microsoft.com/surface/accessories/surface-dock)などの Microsoft のイーサネット アダプターは、Surface のファームウェアと互換性があるチップ セットを使用しています。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-115">Microsoft Ethernet adapters, such as the Surface Ethernet Adapter and the [Surface Dock](https://www.microsoft.com/surface/accessories/surface-dock) use a chipset that is compatible with the Surface firmware.</span></span>

<span data-ttu-id="bc0c1-116">Surface デバイスでのネットワーク ブート向けに、次のイーサネット デバイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-116">The following Ethernet devices are supported for network boot with Surface devices:</span></span>

-   <span data-ttu-id="bc0c1-117">Surface USB-C ~ Ethernet および USB 3.0 アダプター</span><span class="sxs-lookup"><span data-stu-id="bc0c1-117">Surface USB-C to Ethernet and USB 3.0 Adapter</span></span>

-   <span data-ttu-id="bc0c1-118">Surface USB 3.0 からギガビットイーサネットアダプター</span><span class="sxs-lookup"><span data-stu-id="bc0c1-118">Surface USB 3.0 to Gigabit Ethernet Adapter</span></span>

-   <span data-ttu-id="bc0c1-119">Surface ドック</span><span class="sxs-lookup"><span data-stu-id="bc0c1-119">Surface Dock</span></span>

-   <span data-ttu-id="bc0c1-120">Surface 3 ドッキング ステーション</span><span class="sxs-lookup"><span data-stu-id="bc0c1-120">Surface 3 Docking Station</span></span>

-   <span data-ttu-id="bc0c1-121">Surface Pro 3 ドッキング ステーション</span><span class="sxs-lookup"><span data-stu-id="bc0c1-121">Surface Pro 3 Docking Station</span></span>

-   <span data-ttu-id="bc0c1-122">Surface Pro および Surface Pro 2 向けドッキング ステーション</span><span class="sxs-lookup"><span data-stu-id="bc0c1-122">Docking Station for Surface Pro and Surface Pro 2</span></span>

<span data-ttu-id="bc0c1-123">サード パーティ製のイーサネット アダプターは、PXE ブートをサポートしていませんが、ネットワーク展開向けにサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-123">Third-party Ethernet adapters are also supported for network deployment, although they do not support PXE boot.</span></span> <span data-ttu-id="bc0c1-124">サード パーティ製のイーサネット アダプターを使うには、展開のブート イメージにドライバーを読み込む必要があり、USB スティックなどの独立した記憶域デバイスからそのブート イメージを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-124">To use a third-party Ethernet adapter, you must load the drivers into the deployment boot image and you must launch that boot image from a separate storage device, such as a USB stick.</span></span>

## <span data-ttu-id="bc0c1-125">ネットワークから Surface デバイスを起動する</span><span class="sxs-lookup"><span data-stu-id="bc0c1-125">Boot Surface devices from the network</span></span>

<span data-ttu-id="bc0c1-126">ネットワークまたは接続されている USB スティックから起動するには、代替ブート デバイスから起動するように Surface デバイスに指示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-126">To boot from the network or a connected USB stick, you must instruct the Surface device to boot from an alternate boot device.</span></span> <span data-ttu-id="bc0c1-127">システム ファームウェアでブート順を変更して USB ブート デバイスに優先順位を付けることも、プロセスの起動中に代替ブート デバイスから起動するように指示することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-127">You can alter the boot order in the system firmware to prioritize USB boot devices, or you can instruct it to boot from an alternate boot device during the boot up process.</span></span>

<span data-ttu-id="bc0c1-128">代替ブート デバイスから Surface デバイスを起動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-128">To boot a Surface device from an alternative boot device, follow these steps:</span></span>

1.  <span data-ttu-id="bc0c1-129">Surface デバイスの電源がオフになってことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-129">Ensure the Surface device is powered off.</span></span>
2.  <span data-ttu-id="bc0c1-130">**[音量を下げる]** ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-130">Press and hold the **Volume Down** button.</span></span>
3.  <span data-ttu-id="bc0c1-131">**電源**ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-131">Press and release the **Power** button.</span></span>
4.  <span data-ttu-id="bc0c1-132">USB スティックまたはイーサネット アダプターからシステムの起動が開始されたら、**[音量を下げる]** ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-132">After the system begins to boot from the USB stick or Ethernet adapter, release the **Volume Down** button.</span></span>

>[!NOTE]
><span data-ttu-id="bc0c1-133">プレインストール環境に入り、展開ウィザードを操作するには、イーサネット アダプターに加えて、キーボードも Surface デバイスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-133">In addition to an Ethernet adapter, a keyboard must also be connected to the Surface device to enter the preinstallation environment and navigate the deployment wizard.</span></span>

 
<span data-ttu-id="bc0c1-134">Windows 10 Version 1511 以降では、Windows 10 Version 1511 向けの Windows アセスメント & デプロイメント キット (Windows ADK) も含めて、Microsoft Surface イーサネット アダプターのドライバーが既定で用意されています。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-134">For Windows 10, version 1511 and later – including the Windows Assessment and Deployment Kit (Windows ADK) for Windows 10, version 1511 – the drivers for Microsoft Surface Ethernet Adapters are present by default.</span></span> <span data-ttu-id="bc0c1-135">Microsoft Deployment Toolkit などの Windows プレインストール環境 (WinPE) を利用する展開ソリューションを使い、PXE によってネットワークから起動している場合は、その展開ソリューションで使われている Windows ADK のバージョンが最新であることを確かめてください。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-135">If you are using a deployment solution that uses Windows Preinstallation Environment (WinPE), like the Microsoft Deployment Toolkit, and booting from the network with PXE, ensure that your deployment solution is using the latest version of the Windows ADK.</span></span>

## <a href="" id="manage-mac-addresses"></a><span data-ttu-id="bc0c1-136">リムーバブル イーサネット アダプターの MAC アドレスを管理する</span><span class="sxs-lookup"><span data-stu-id="bc0c1-136">Manage MAC addresses with removable Ethernet adapters</span></span>

<span data-ttu-id="bc0c1-137">ネットワーク経由で Windows の展開を行う管理者にとってのもう 1 つの考慮事項は、同じイーサネット アダプターを使用して複数のコンピューターに展開するときにコンピューターを識別する方法です。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-137">Another consideration for administrators performing Windows deployment over the network is how you will identify computers when you use the same Ethernet adapter to deploy to more than one computer.</span></span> <span data-ttu-id="bc0c1-138">展開テクノロジで使われる共通の識別子は、各イーサネット アダプターに関連付けられているメディア アクセス コントロール (MAC) アドレスです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-138">A common identifier used by deployment technologies is the Media Access Control (MAC) address that is associated with each Ethernet adapter.</span></span> <span data-ttu-id="bc0c1-139">ただし、同じイーサネット アダプターを使って複数のコンピューターに展開するときは、MAC アドレスを調査する展開テクノロジを使うことはできません。別のコンピューターで使われたときに、リムーバブル アダプターの MAC アドレスを区別する方法がないためです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-139">However, when you use the same Ethernet adapter to deploy to multiple computers, you cannot use a deployment technology that inspects MAC addresses because there is no way to differentiate the MAC address of the removable adapter when used on the different computers.</span></span>

<span data-ttu-id="bc0c1-140">MAC アドレスの競合を避けるための最も簡単なソリューションは、Surface デバイスごとに専用のリムーバブル イーサネット アダプターを提供することです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-140">The simplest solution to avoid MAC address conflicts is to provide a dedicated removable Ethernet adapter for each Surface device.</span></span> <span data-ttu-id="bc0c1-141">これは、イーサネット アダプターやドッキング ステーションの追加機能を使う多くのシナリオには意味があります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-141">This can make sense in many scenarios where the Ethernet adapter or the additional functionality of the docking station will be used regularly.</span></span> <span data-ttu-id="bc0c1-142">しかし、すべてのシナリオでドッキング ステーションの追加接続機能や有線ネットワークのサポートが必要になるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-142">However, not all scenarios call for the additional connectivity of a docking station or support for wired networks.</span></span>

<span data-ttu-id="bc0c1-143">アダプターを共有するときに競合を回避できる別のソリューションは、[Microsoft Deployment Toolkit (MDT)](https://technet.microsoft.com/windows/dn475741) を使って Surface デバイスへの展開を行うことです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-143">Another potential solution to avoid conflict when adapters are shared is to use the [Microsoft Deployment Toolkit (MDT)](https://technet.microsoft.com/windows/dn475741) to perform deployment to Surface devices.</span></span> <span data-ttu-id="bc0c1-144">MDT では、個々のコンピューターを識別するために MAC アドレスを使っていないため、この制限の対象ではありません。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-144">MDT does not use the MAC address to identify individual computers and thus is not subject to this limitation.</span></span> <span data-ttu-id="bc0c1-145">ただし、MDT は Windows 展開サービスを使って PXE ブート機能を提供しているため、このセクションで後で説明する事前設定されたクライアントに関する制限の対象になります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-145">However, MDT does use Windows Deployment Services to provide PXE boot functionality, and is subject to the limitations regarding pre-staged clients which is covered later in this section.</span></span>

<span data-ttu-id="bc0c1-146">展開用に共有アダプターを使うとき、影響を受ける展開テクノロジ向けのソリューションは、別の手段で固有のシステムを識別することです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-146">When you use a shared adapter for deployment, the solution for affected deployment technologies is to use another means to identify unique systems.</span></span> <span data-ttu-id="bc0c1-147">構成マネージャーと WDS はどちらもこの問題の影響を受けますが、そのソリューションは、コンピューターの製造元によってコンピューターのファームウェアに組み込まれているシステム ユニバーサル固有識別子 (システム UUID) を使うことです。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-147">For Configuration Manager and WDS, both of which can be affected by this issue, the solution is to use the System Universal Unique Identifier (System UUID) that is embedded in the computer firmware by the computer manufacturer.</span></span> <span data-ttu-id="bc0c1-148">Surface デバイスの場合、このエントリはコンピューターのファームウェアの **[デバイス情報]** の下にあります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-148">For Surface devices, you can see this entry in the computer firmware under **Device Information**.</span></span>

<span data-ttu-id="bc0c1-149">Surface デバイスのファームウェアにアクセスするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-149">To access the firmware of a Surface device, follow these steps:</span></span>

1.  <span data-ttu-id="bc0c1-150">Surface デバイスの電源がオフになってことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-150">Ensure the Surface device is powered off.</span></span>
2.  <span data-ttu-id="bc0c1-151">**[音量を上げる]** ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-151">Press and hold the **Volume Up** button.</span></span>
3.  <span data-ttu-id="bc0c1-152">**電源**ボタンを押して離します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-152">Press and release the **Power** button.</span></span>
4.  <span data-ttu-id="bc0c1-153">デバイスの起動が開始されたら、**[音量を上げる]** ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-153">After the device begins to boot, release the **Volume Up** button.</span></span>

<span data-ttu-id="bc0c1-154">WDS で展開する場合、展開サーバーが事前設定された既知のクライアントにのみ応答するように構成されているときにだけ、コンピューターを識別するために MAC アドレスが使われます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-154">When deploying with WDS, the MAC address is only used to identify a computer when the deployment server is configured to respond only to known, pre-staged clients.</span></span> <span data-ttu-id="bc0c1-155">クライアントを事前設定するとき、管理者は Active Directory でコンピューター アカウントを作成し、MAC アドレスまたはシステム UUID でそのコンピューターを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-155">When pre-staging a client, an administrator creates a computer account in Active Directory and defines that computer by the MAC address or the System UUID.</span></span> <span data-ttu-id="bc0c1-156">共有イーサネット アダプターによって起こる ID の競合を避けるために、[システム UUID](https://technet.microsoft.com/library/cc742034) を使って事前設定されたクライアントを定義してください。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-156">To avoid the identity conflicts caused by shared Ethernet adapters, you should use [System UUID to define pre-staged clients](https://technet.microsoft.com/library/cc742034).</span></span> <span data-ttu-id="bc0c1-157">または、**[Windows Deployment Server Properties]** の [**[PXE 応答]** タブ](https://technet.microsoft.com/library/cc732360)で **[すべて (既知および不明) のクライアント コンピューターに応答する]** オプションを選択することで、MAC アドレスまたはシステム UUID による定義を必要としない不明なクライアントに応答するように WDS を構成できます。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-157">Alternatively, you can configure WDS to respond to unknown clients that do not require definition by either MAC address or System UUID by selecting the **Respond to all client computers (known and unknown)** option on the [**PXE Response** tab](https://technet.microsoft.com/library/cc732360) in **Windows Deployment Server Properties**.</span></span>

<span data-ttu-id="bc0c1-158">共有イーサネット アダプターを使うと、Configuration Manager を使う場合より競合の可能性がはるかに高くなります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-158">The potential for conflicts with shared Ethernet adapters is much higher with Configuration Manager.</span></span> <span data-ttu-id="bc0c1-159">WDS が MAC アドレスのみを使って個々のシステムを定義する場合、構成時に Configuration Manager は、新規または不明なコンピューターへの展開を行うたびに MAC アドレスを使って個々のシステムを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-159">Where WDS only uses MAC addresses to define individual systems when configured to do so, Configuration Manager uses the MAC address to define individual systems whenever performing a deployment to new or unknown computers.</span></span> <span data-ttu-id="bc0c1-160">これにより、デバイスが不適切に構成されたり、共有イーサネット アダプターで複数のシステムを展開できなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-160">This can result in improperly configured devices or even the inability to deploy more than one system with a shared Ethernet adapter.</span></span> <span data-ttu-id="bc0c1-161">この状況では、複数の SCCM OSD (コアインフラストラクチャとセキュリティブログのブログ投稿) に[同じ外部イーサネットアダプターを使用する方法](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374)について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="bc0c1-161">There are several potential solutions for this situation that are described in detail in [How to Use The Same External Ethernet Adapter For Multiple SCCM OSD](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374), a blog post on the Core Infrastructure and Security Blog.</span></span>

 

 





