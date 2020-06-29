---
title: Configuration Manager で Surface driver の更新を管理する
description: この記事では、Surface デバイスのファームウェアとドライバーの更新プログラムを管理および展開するために使用できるオプションについて説明します。
ms.assetid: b64879c4-37eb-4fcf-a000-e05cbb3d26ea
ms.reviewer: ''
author: v-miegge
manager: laurawi
keywords: Surface, Surface Pro 3, ファームウェア, 更新プログラム, デバイス, 管理, 展開, ドライバー, USB, Surface, Surface Pro 3, firmware, update, device, manage, deploy, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.author: daclark
ms.topic: article
audience: itpro
ms.openlocfilehash: 1a9c8c64bd524de58696c73a28795b69cc70a7b2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835869"
---
# <span data-ttu-id="266c3-104">Configuration Manager で Surface driver の更新を管理する</span><span class="sxs-lookup"><span data-stu-id="266c3-104">Manage Surface driver updates in Configuration Manager</span></span>

## <span data-ttu-id="266c3-105">まとめ</span><span class="sxs-lookup"><span data-stu-id="266c3-105">Summary</span></span>

<span data-ttu-id="266c3-106">[Microsoft System Center Configuration manager バージョン 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates)以降では、configuration manager クライアントを通じて、microsoft Surface ファームウェアとドライバー更新プログラムを直接、同期して展開することができます。</span><span class="sxs-lookup"><span data-stu-id="266c3-106">Starting in [Microsoft System Center Configuration Manager version 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates), you can synchronize and deploy Microsoft Surface firmware and driver updates directly through the Configuration Manager client.</span></span> <span data-ttu-id="266c3-107">このプロセスは、定期的な更新プログラムの展開と似ています。</span><span class="sxs-lookup"><span data-stu-id="266c3-107">The process resembles deploying regular updates.</span></span> <span data-ttu-id="266c3-108">ただし、Surface driver の更新をカタログに追加するには、いくつかの追加構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="266c3-108">However, some additional configurations are required to get the Surface driver updates into your catalog.</span></span>

## <span data-ttu-id="266c3-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="266c3-109">Prerequisites</span></span>

<span data-ttu-id="266c3-110">Surface driver の更新を管理するには、次の前提条件が満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-110">To manage Surface driver updates, the following prerequisites must be met:</span></span>

- <span data-ttu-id="266c3-111">Configuration Manager バージョン1710またはそれ以降のバージョンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-111">You must use Configuration Manager version 1710 or a later version.</span></span>
- <span data-ttu-id="266c3-112">すべてのソフトウェア更新ポイント (SUPs) は、Windows Server 2016 以降を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-112">All Software Update Points (SUPs) must run Windows Server 2016 or a later version.</span></span> <span data-ttu-id="266c3-113">そうしないと、構成マネージャーはこの設定を無視し、Surface ドライバーは同期されません。</span><span class="sxs-lookup"><span data-stu-id="266c3-113">Otherwise, Configuration Manager ignores this setting and Surface drivers won't be synchronized.</span></span>

> [!NOTE]
> <span data-ttu-id="266c3-114">環境が前提条件を満たしていない場合は、「[よく寄せ](#frequently-asked-questions-faq)られる質問 (FAQ)」で、「Surface ドライバーとファームウェアの更新プログラムを展開するための[別の方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-114">If your environment doesn’t meet the prerequisites, refer to the [alternative methods](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) to deploy Surface driver and firmware updates in the [FAQ](#frequently-asked-questions-faq) section.</span></span>

## <span data-ttu-id="266c3-115">有用なログファイル</span><span class="sxs-lookup"><span data-stu-id="266c3-115">Useful log files</span></span>

<span data-ttu-id="266c3-116">次のログは、Surface ドライバーの更新を管理するときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="266c3-116">The following logs are especially useful when you manage Surface driver updates.</span></span>

|<span data-ttu-id="266c3-117">ログ名</span><span class="sxs-lookup"><span data-stu-id="266c3-117">Log name</span></span>|<span data-ttu-id="266c3-118">説明</span><span class="sxs-lookup"><span data-stu-id="266c3-118">Description</span></span>|
|---|---|
|<span data-ttu-id="266c3-119">WCM</span><span class="sxs-lookup"><span data-stu-id="266c3-119">WCM.log</span></span>|<span data-ttu-id="266c3-120">登録されている更新のカテゴリ、分類、言語に対応する、ソフトウェアの更新ポイント構成と WSUS サーバーへの接続に関する詳細を記録します。</span><span class="sxs-lookup"><span data-stu-id="266c3-120">Records details about the software update point configuration and connections to the WSUS server for subscribed update categories, classifications, and languages.</span></span>|
|<span data-ttu-id="266c3-121">WsyncMgr</span><span class="sxs-lookup"><span data-stu-id="266c3-121">WsyncMgr.log</span></span>|<span data-ttu-id="266c3-122">ソフトウェアの更新プログラムの同期プロセスの詳細を記録します。</span><span class="sxs-lookup"><span data-stu-id="266c3-122">Records details about the software updates sync process.</span></span>|

<span data-ttu-id="266c3-123">これらのログは、SUP を管理するサイトサーバー上、または SUP 自体がサイトサーバーに直接インストールされている場合は、SUP 上にあります。</span><span class="sxs-lookup"><span data-stu-id="266c3-123">These logs are located on the site server that manages the SUP, or on the SUP itself if it's installed directly on a site server.</span></span>
<span data-ttu-id="266c3-124">Configuration Manager ログの完全な一覧については、「 [System Center Configuration manager でログファイル](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files)を確認する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-124">For a complete list of Configuration Manager logs, see [Log files in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).</span></span>

## <span data-ttu-id="266c3-125">Surface driver の更新管理を有効にする</span><span class="sxs-lookup"><span data-stu-id="266c3-125">Enabling Surface driver updates management</span></span>

<span data-ttu-id="266c3-126">Configuration Manager で Surface driver の更新プログラムの管理を有効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="266c3-126">To enable Surface driver updates management in Configuration Manager, follow these steps:</span></span>

1. <span data-ttu-id="266c3-127">Configuration Manager コンソールで、[**管理**  >  **概要**  >  **サイトの構成**  >  **サイト**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="266c3-127">In the Configuration Manager console, go to **Administration** > **Overview** > **Site Configuration** > **Sites**.</span></span>
1. <span data-ttu-id="266c3-128">使用している環境に対応するトップレベルの SUP サーバーが含まれているサイトを選びます。</span><span class="sxs-lookup"><span data-stu-id="266c3-128">Select the site that contains the top-level SUP server for your environment.</span></span>
1. <span data-ttu-id="266c3-129">リボンで、[**サイトコンポーネントの構成**]、[**ソフトウェアの更新ポイント**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="266c3-129">On the ribbon, select **Configure Site Components**, and then select **Software Update Point**.</span></span> <span data-ttu-id="266c3-130">または、サイトを右クリックして、[**サイトコンポーネント**  >  **ソフトウェアの更新ポイント**の構成] を選びます。</span><span class="sxs-lookup"><span data-stu-id="266c3-130">Or, right-click the site, and then select **Configure Site Components** > **Software Update Point**.</span></span>
1. <span data-ttu-id="266c3-131">[**分類**] タブで、[ **Microsoft Surface ドライバーとファームウェアの更新を含める**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="266c3-131">On the **Classifications** tab, select the **Include Microsoft Surface drivers and firmware updates** check box.</span></span>

   ![ソフトウェアの更新ポイントコンポーネントのプロパティ](images/manage-surface-driver-updates-1.png)

1. <span data-ttu-id="266c3-133">次の警告メッセージが表示されたら、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="266c3-133">When you're prompted by the following warning message, select **OK**.</span></span>

   ![Configuration Manager](images/manage-surface-driver-updates-2.png)

1. <span data-ttu-id="266c3-135">[製品] タブで、更新する製品を選択し、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="266c3-135">On the Products tab, select the products that you want to update, and then select **OK**.</span></span>

   <span data-ttu-id="266c3-136">ほとんどのドライバーは、次の製品グループに属しています。</span><span class="sxs-lookup"><span data-stu-id="266c3-136">Most drivers belong to the following product groups:</span></span>

   - <span data-ttu-id="266c3-137">Windows 10 以降のバージョンドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-137">Windows 10 and later version drivers</span></span>
   - <span data-ttu-id="266c3-138">Windows 10 以降のアップグレード & サービスドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-138">Windows 10 and later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-139">Windows 10 記念日更新プログラムおよび以降のサービスドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-139">Windows 10 Anniversary Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-140">Windows 10 記念日更新プログラムと & サービスドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-140">Windows 10 Anniversary Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-141">Windows 10 の作成者が更新後にドライバーを提供する</span><span class="sxs-lookup"><span data-stu-id="266c3-141">Windows 10 Creators Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-142">Windows 10 の作成者が更新後にアップグレードして & サービスドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-142">Windows 10 Creators Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-143">Windows 10 では、作成者が更新し、後でドライバーを提供しています</span><span class="sxs-lookup"><span data-stu-id="266c3-143">Windows 10 Fall Creators Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-144">Windows 10 では、作成者が更新され、後でアップグレード & のドライバーがインストールされる</span><span class="sxs-lookup"><span data-stu-id="266c3-144">Windows 10 Fall Creators Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-145">Windows 10 S 以降のサービスドライバー</span><span class="sxs-lookup"><span data-stu-id="266c3-145">Windows 10 S and Later Servicing Drivers</span></span>
   - <span data-ttu-id="266c3-146">Windows 10 S バージョン1709および以降のテスト用ドライバーのサービス</span><span class="sxs-lookup"><span data-stu-id="266c3-146">Windows 10 S Version 1709 and Later Servicing Drivers for testing</span></span>
   - <span data-ttu-id="266c3-147">Windows 10 S バージョン1709以降のアップグレード & テスト用のドライバーを提供する</span><span class="sxs-lookup"><span data-stu-id="266c3-147">Windows 10 S Version 1709 and Later Upgrade & Servicing Drivers for testing</span></span>

   > [!NOTE]
   > <span data-ttu-id="266c3-148">ほとんどの Surface ドライバーは、複数の Windows 10 製品グループに属しています。</span><span class="sxs-lookup"><span data-stu-id="266c3-148">Most Surface drivers belong to multiple Windows 10 product groups.</span></span> <span data-ttu-id="266c3-149">ここに記載されているすべての製品を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="266c3-149">You may not have to select all the products that are listed here.</span></span> <span data-ttu-id="266c3-150">更新プログラムカタログに設定されている製品の数を減らすために、同期のために環境で必要な製品のみを選ぶことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="266c3-150">To help reduce the number of products that populate your Update Catalog, we recommend that you select only the products that are required by your environment for synchronization.</span></span>

## <span data-ttu-id="266c3-151">構成を確認する</span><span class="sxs-lookup"><span data-stu-id="266c3-151">Verifying the configuration</span></span>

<span data-ttu-id="266c3-152">SUP が正しく構成されていることを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="266c3-152">To verify that the SUP is configured correctly, follow these steps:</span></span>

1. <span data-ttu-id="266c3-153">WsyncMgr を開いて、次のエントリを探します。</span><span class="sxs-lookup"><span data-stu-id="266c3-153">Open WsyncMgr.log, and then look for the following entry:</span></span>

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   <span data-ttu-id="266c3-154">次のいずれかのエントリが WsyncMgr に記録されている場合は、前のセクションの手順4を再確認してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-154">If either of the following entries is logged in WsyncMgr.log, recheck step 4 in the previous section:</span></span>

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. <span data-ttu-id="266c3-155">WCM を開き、次のようなエントリを探します。</span><span class="sxs-lookup"><span data-stu-id="266c3-155">Open WCM.log, and then look for an entry that resembles the following:</span></span>

   ![WCM の設定](images/manage-surface-driver-updates-3.png)

   <span data-ttu-id="266c3-157">このエントリは、SUP サーバーによって現在同期されているすべての製品グループとクラスを一覧表示する XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="266c3-157">This entry is an XML element that lists every product group and classification that's currently synchronized by your SUP server.</span></span> <span data-ttu-id="266c3-158">たとえば、次のようなエントリが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="266c3-158">For example, you might see an entry that resembles the following:</span></span>

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   <span data-ttu-id="266c3-159">前のセクションの手順6で選んだ製品が見つからない場合は、SUP の設定が保存されているかどうかをダブルチェックします。</span><span class="sxs-lookup"><span data-stu-id="266c3-159">If you can't find the products that you selected in step 6 in the previous section, double-check whether the SUP settings are saved.</span></span>

   <span data-ttu-id="266c3-160">次の同期が完了するまで待ってから、Surface ドライバーとファームウェア更新プログラムが Configuration Manager コンソールのソフトウェア更新プログラムに一覧表示されているかどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="266c3-160">You can also wait until the next synchronization finishes, and then check whether the Surface driver and firmware updates are listed in Software Updates in the Configuration Manager console.</span></span> <span data-ttu-id="266c3-161">たとえば、コンソールに次の情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-161">For example, the console might display the following information:</span></span>

   ![すべてのソフトウェア更新プログラムの検索結果](images/manage-surface-driver-updates-4.png)

## <span data-ttu-id="266c3-163">手動同期</span><span class="sxs-lookup"><span data-stu-id="266c3-163">Manual synchronization</span></span>

<span data-ttu-id="266c3-164">次の同期を待つ必要がない場合は、次の手順に従って同期を開始します。</span><span class="sxs-lookup"><span data-stu-id="266c3-164">If you don't want to wait until the next synchronization, follow these steps to start a synchronization:</span></span>

1. <span data-ttu-id="266c3-165">Configuration Manager コンソールで、[ソフトウェア**ライブラリ**の概要] に移動し、[ソフトウェアの更新プログラム] を選択  >  **Overview**  >  **Software Updates**  >  **All Software Updates**します。</span><span class="sxs-lookup"><span data-stu-id="266c3-165">In the Configuration Manager console, go to **Software Library** > **Overview** > **Software Updates** > **All Software Updates**.</span></span>
1. <span data-ttu-id="266c3-166">リボンで、[**ソフトウェアの更新を同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="266c3-166">On the ribbon, select **Synchronize Software Updates**.</span></span> <span data-ttu-id="266c3-167">または、[**すべてのソフトウェア更新プログラム**] を右クリックして、[**ソフトウェア更新プログラムの同期**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="266c3-167">Or, right-click **All Software Update**, and then select **Synchronize Software Update**.</span></span>
1. <span data-ttu-id="266c3-168">WsyncMgr で次のエントリを探して、同期の進行状況を監視します。</span><span class="sxs-lookup"><span data-stu-id="266c3-168">Monitor the synchronization progress by looking for the following entries in WsyncMgr.log:</span></span>

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   sync: SMS synchronizing categories 
   sync: SMS synchronizing categories, processed 0 out of 311 items (0%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing updates

   Synchronizing update 7eaa0148-c42b-45fd-a1ab-012c82972de6 - Microsoft driver update for Surface Type Cover Integration
   Synchronizing update 2dcb07f8-37ec-41ef-8cd5-030bf24dc1d8 - Surface driver update for Surface Pen Pairing
   Synchronizing update 63067414-ae52-422b-b3d1-0382a4d6519a - Surface driver update for Surface UEFI
   Synchronizing update 8e4e3a41-a784-4dd7-9a42-041f43ddb775 - Surface driver update for Surface Integration
   Synchronizing update 7f8baee8-419f-47e2-918a-045a15a188e7 - Microsoft driver update for Surface DTX
   Synchronizing update aed66e05-719b-48cd-a0e7-059e50f67fdc - Microsoft driver update for Surface Base Firmware Update
   Synchronizing update 8ffe1526-6e66-43cc-86e3-05ad92a24e3a - Surface driver update for Surface UEFI
   Synchronizing update 74102899-0a49-48cf-97e6-05bde18a27ff - Microsoft driver update for Surface UEFI
   ```

## <span data-ttu-id="266c3-169">Surface ファームウェアとドライバー更新プログラムを展開する</span><span class="sxs-lookup"><span data-stu-id="266c3-169">Deploying Surface firmware and driver updates</span></span>

<span data-ttu-id="266c3-170">他の更新プログラムを展開する場合と同じ方法で、Surface ファームウェアとドライバーの更新プログラムを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="266c3-170">You can deploy Surface firmware and driver updates in the same manner as you deploy other updates.</span></span>

<span data-ttu-id="266c3-171">展開の詳細については、「 [System Center 2012 構成マネージャー– Part7: ソフトウェア更新プログラム (展開)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-171">For more information about deployment, see [System Center 2012 Configuration Manager–Part7: Software Updates (Deploy)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).</span></span>

## <span data-ttu-id="266c3-172">よく寄せられる質問 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="266c3-172">Frequently asked questions (FAQ)</span></span>

**<span data-ttu-id="266c3-173">この記事の手順を実行しても、Surface ドライバーが同期されません。</span><span class="sxs-lookup"><span data-stu-id="266c3-173">After I follow the steps in this article, my Surface drivers are still not synchronized.</span></span> <span data-ttu-id="266c3-174">どうしてでしょうか?</span><span class="sxs-lookup"><span data-stu-id="266c3-174">Why?</span></span>**

<span data-ttu-id="266c3-175">Microsoft Update ではなく、上流の Windows Server Update Services (WSUS) サーバーから同期する場合は、Surface driver の更新プログラムをサポートし、同期するように上流の WSUS サーバーが構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-175">If you synchronize from an upstream Windows Server Update Services (WSUS) server, instead of Microsoft Update, make sure that the upstream WSUS server is configured to support and synchronize Surface driver updates.</span></span> <span data-ttu-id="266c3-176">すべてのダウンストリームサーバーは、上流の WSUS サーバーデータベースに存在する更新プログラムに制限されます。</span><span class="sxs-lookup"><span data-stu-id="266c3-176">All downstream servers are limited to updates that are present in the upstream WSUS server database.</span></span>

<span data-ttu-id="266c3-177">WSUS でドライバーとして分類される、68000を超える更新プログラムがあります。</span><span class="sxs-lookup"><span data-stu-id="266c3-177">There are more than 68,000 updates that are classified as drivers in WSUS.</span></span> <span data-ttu-id="266c3-178">Surface 関連以外のドライバーが構成マネージャーに同期されないようにするために、ドライバーの同期を許可リストに対してフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="266c3-178">To prevent non-Surface related drivers from synchronizing to Configuration Manager, Microsoft filters driver synchronization against an allow list.</span></span> <span data-ttu-id="266c3-179">新しい許可リストが公開されて Configuration Manager に組み込まれると、次の同期の後に新しいドライバーがコンソールに追加されます。</span><span class="sxs-lookup"><span data-stu-id="266c3-179">After the new allow list is published and incorporated into Configuration Manager, the new drivers are added to the console following the next synchronization.</span></span> <span data-ttu-id="266c3-180">Microsoft の目標は、Configuration Manager との同期に使用できるようにするために、各月の [許可] リストに追加された Surface ドライバーを更新プログラムの火曜日と共に取得することです。</span><span class="sxs-lookup"><span data-stu-id="266c3-180">Microsoft aims to get the Surface drivers added to the allow list each month in line with Patch Tuesday to make them available for synchronization to Configuration Manager.</span></span>

<span data-ttu-id="266c3-181">構成マネージャー環境がオフラインの場合、[サービス更新プログラム](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool)を configuration manager にインポートするたびに、新しい許可リストがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="266c3-181">If your Configuration Manager environment is offline, a new allow list is imported every time you import [servicing updates](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) to Configuration Manager.</span></span> <span data-ttu-id="266c3-182">また、更新プログラムが Configuration Manager コンソールに表示される前に、ドライバーを含む[新しい WSUS カタログ](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected)をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-182">You will also have to import a [new WSUS catalog](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) that contains the drivers before the updates are displayed in the Configuration Manager console.</span></span> <span data-ttu-id="266c3-183">スタンドアロンの WSUS 環境には構成マネージャー SUP よりも多くのドライバーが含まれているため、オンライン機能を備えた構成マネージャー環境を確立して、Surface ドライバーを同期するように構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="266c3-183">Because a stand-alone WSUS environment contains more drivers than a Configuration Manager SUP, we recommend that you establish a Configuration Manager environment that has online capabilities, and that you configure it to synchronize Surface drivers.</span></span> <span data-ttu-id="266c3-184">これにより、オフライン環境とよく似た小さな WSUS のエクスポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="266c3-184">This provides a smaller WSUS export that closely resembles the offline environment.</span></span>

<span data-ttu-id="266c3-185">構成マネージャー環境がオンラインで、新しい更新プログラムを検出できる場合は、一覧の更新プログラムが自動的に受信されます。</span><span class="sxs-lookup"><span data-stu-id="266c3-185">If your Configuration Manager environment is online and able to detect new updates, you will receive updates to the list automatically.</span></span> <span data-ttu-id="266c3-186">予期されるドライバーが表示されない場合は、WsyncMgr とを確認して、同期エラーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-186">If you don’t see the expected drivers, please review the WCM.log and WsyncMgr.log for any synchronization failures.</span></span>

**<span data-ttu-id="266c3-187">Configuration Manager 環境がオフラインになっている場合、Surface ドライバーを手動で WSUS にインポートすることはできますか?</span><span class="sxs-lookup"><span data-stu-id="266c3-187">My Configuration Manager environment is offline, can I manually import Surface drivers into WSUS?</span></span>**

<span data-ttu-id="266c3-188">いいえ、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="266c3-188">No.</span></span> <span data-ttu-id="266c3-189">更新プログラムが WSUS にインポートされても、[許可] 一覧に表示されていない場合は、展開用の Configuration Manager コンソールに更新プログラムがインポートされません。</span><span class="sxs-lookup"><span data-stu-id="266c3-189">Even if the update is imported into WSUS, the update won't be imported into the Configuration Manager console for deployment if it isn't listed in the allow list.</span></span> <span data-ttu-id="266c3-190">[サービス接続ツール](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool)を使用して、サービス更新プログラムを Configuration Manager にインポートし、許可リストを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="266c3-190">You must use the [Service Connection Tool](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) to import servicing updates to Configuration Manager to update the allow list.</span></span>

**<span data-ttu-id="266c3-191">Surface ドライバーとファームウェアの更新プログラムを展開するために必要な代替メソッドは何ですか?</span><span class="sxs-lookup"><span data-stu-id="266c3-191">What alternative methods do I have to deploy Surface driver and firmware updates?</span></span>**

<span data-ttu-id="266c3-192">代替チャネルを使用して Surface ドライバーとファームウェア更新プログラムを展開する方法について詳しくは、「 [surface ドライバーとファームウェア更新プログラムを管理](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates)する」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="266c3-192">For information about how to deploy Surface driver and firmware updates through alternative channels, see [Manage Surface driver and firmware updates](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates).</span></span> <span data-ttu-id="266c3-193">.Msi または .exe ファイルをダウンロードして、従来のソフトウェア展開チャネルを使用して展開する場合は、「 [Surface ファームウェアを Configuration Manager で更新](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-193">If you want to download the .msi or .exe file, and then deploy through traditional software deployment channels, see [Keeping Surface Firmware Updated with Configuration Manager](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager).</span></span>

## <span data-ttu-id="266c3-194">追加情報</span><span class="sxs-lookup"><span data-stu-id="266c3-194">Additional Information</span></span>

<span data-ttu-id="266c3-195">Surface ドライバーとファームウェアの更新の詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="266c3-195">For more information about Surface driver and firmware updates, see the following articles:</span></span>

- [<span data-ttu-id="266c3-196">Surface デバイス用の最新のファームウェアとドライバーをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="266c3-196">Download the latest firmware and drivers for Surface devices</span></span>](https://docs.microsoft.com/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices)
- [<span data-ttu-id="266c3-197">Surface のドライバーおよびファームウェアの更新プログラムを管理する</span><span class="sxs-lookup"><span data-stu-id="266c3-197">Manage Surface driver and firmware updates</span></span>](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)
- [<span data-ttu-id="266c3-198">Surface および System Center Configuration Manager に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="266c3-198">Considerations for Surface and System Center Configuration Manager</span></span>](https://docs.microsoft.com/surface/considerations-for-surface-and-system-center-configuration-manager)
