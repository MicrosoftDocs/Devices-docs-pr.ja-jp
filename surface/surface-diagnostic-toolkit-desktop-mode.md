---
title: ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する
description: SDT を使用して、組織内のユーザーが Surface デバイスに関する問題を特定して診断し、ツールから直接サポート要求を送信できるようにする方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 7/31/2020
ms.openlocfilehash: ec4a90d0d72956eaa4f98e928d128dca70d49c59
ms.sourcegitcommit: f875a45961ff5f3c04006afc8690b5e5965e4d80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2020
ms.locfileid: "10902975"
---
# <span data-ttu-id="48aba-103">ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する</span><span class="sxs-lookup"><span data-stu-id="48aba-103">Use Surface Diagnostic Toolkit for Business in desktop mode</span></span>

<span data-ttu-id="48aba-104">このトピックでは、Surface Diagnostic ツールキット (SDT) を使用して、組織内のユーザーが Surface デバイスの問題を識別して診断し、ツールから直接サポート要求を送信できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="48aba-104">This topic explains how to use the Surface Diagnostic Toolkit (SDT) to help users in your organization run the tool to identify and diagnose issues with their Surface device as well as submit Support requests directly from the tool.</span></span> 

<span data-ttu-id="48aba-105">SDT を正常に実行すると、報告された問題の原因がハードウェアまたはユーザーのエラーであるかどうかがすぐにわかります。</span><span class="sxs-lookup"><span data-stu-id="48aba-105">Successfully running SDT can quickly determine if a reported issue is caused by failed hardware or user error.</span></span> <span data-ttu-id="48aba-106">SDT でサポートされている Surface デバイスの一覧については、「[展開 Surface 診断ツールキット](surface-diagnostic-toolkit-business.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48aba-106">For a list of supported Surface devices in SDT, refer to [Deploy Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-business.md).</span></span>


1. <span data-ttu-id="48aba-107">ソフトウェアの配布ポイントまたはネットワーク共有から[SDT パッケージ](surface-diagnostic-toolkit-business.md#create-custom-sdt)をインストールするようにユーザーに指示します。</span><span class="sxs-lookup"><span data-stu-id="48aba-107">Direct the user to install [the SDT package](surface-diagnostic-toolkit-business.md#create-custom-sdt) from a software distribution point or network share.</span></span> <span data-ttu-id="48aba-108">インストールされた後、一連のテストを通じてユーザーを導くことができます。</span><span class="sxs-lookup"><span data-stu-id="48aba-108">After it is installed, you’re ready to guide the user through a series of tests.</span></span> 

2. <span data-ttu-id="48aba-109">[ホーム] ページから開始します。これにより、ユーザーは問題の説明を入力することができます。図1のように [**続行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48aba-109">Begin at the home page, which allows users to enter a description of the issue, and click **Continue**, as shown in figure 1.</span></span>

    ![<span data-ttu-id="48aba-110">デスクトップモードで SDT を開始 ](images/sdt-desk-1.png)
 *します図1。デスクトップモードでの SDT*</span><span class="sxs-lookup"><span data-stu-id="48aba-110">Start SDT in desktop mode](images/sdt-desk-1.png)
*Figure 1. SDT in desktop mode*</span></span>

3. <span data-ttu-id="48aba-111">デバイスに最新の更新プログラムがあることが確認された場合は、[**続行**] をクリックして、使用可能なテストのカタログに進みます (図2を参照)。</span><span class="sxs-lookup"><span data-stu-id="48aba-111">When SDT indicates the device has the latest updates, click **Continue** to advance to the catalog of available tests, as shown in figure 2.</span></span>

    ![<span data-ttu-id="48aba-112">[SDT options] オプションから選択し ](images/sdt1.png)
 *ます。図2[SDT] オプションを選択*する</span><span class="sxs-lookup"><span data-stu-id="48aba-112">Select from SDT options](images/sdt1.png)
*Figure 2. Select from SDT options*</span></span>

4. <span data-ttu-id="48aba-113">すべての診断テストを実行するかどうかを選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="48aba-113">You can choose to run all the diagnostic tests.</span></span> <span data-ttu-id="48aba-114">または、不適切なディスプレイや電源の問題など、特定の問題が発生している可能性がある場合は、[**選択**] をクリックして使用可能なテストから選び、[**選択した実行**] をクリックします (図3を参照)。</span><span class="sxs-lookup"><span data-stu-id="48aba-114">Or, if you already suspect a particular issue such as a faulty display or a power supply problem, click **Select** to choose from the available tests and click **Run Selected**, as shown in figure 3.</span></span> <span data-ttu-id="48aba-115">各テストの詳細については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48aba-115">See the following table for details of each test.</span></span> 

    ![<span data-ttu-id="48aba-116">[ハードウェアテスト] 図3を選択し ](images/sdt2.png)
 *ます。ハードウェアテストを選ぶ*</span><span class="sxs-lookup"><span data-stu-id="48aba-116">Select hardware tests](images/sdt2.png)
*Figure 3. Select hardware tests*</span></span>

    <span data-ttu-id="48aba-117">ハードウェアテスト</span><span class="sxs-lookup"><span data-stu-id="48aba-117">Hardware test</span></span> | <span data-ttu-id="48aba-118">説明</span><span class="sxs-lookup"><span data-stu-id="48aba-118">Description</span></span>
    --- | ---
    <span data-ttu-id="48aba-119">電源とバッテリ</span><span class="sxs-lookup"><span data-stu-id="48aba-119">Power Supply and Battery</span></span> |  <span data-ttu-id="48aba-120">Power サプライが最適に機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="48aba-120">Checks Power supply is functioning optimally</span></span>
    <span data-ttu-id="48aba-121">ディスプレイとサウンド</span><span class="sxs-lookup"><span data-stu-id="48aba-121">Display and Sound</span></span>   | <span data-ttu-id="48aba-122">明るさ、停止、またはデッドピクセル、スピーカーとマイクの機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="48aba-122">Checks brightness, stuck or dead pixels, speaker and microphone functioning</span></span>
    <span data-ttu-id="48aba-123">ポートとアクセサリ</span><span class="sxs-lookup"><span data-stu-id="48aba-123">Ports and Accessories</span></span>   | <span data-ttu-id="48aba-124">アクセサリ、画面接続、USB 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="48aba-124">Checks accessories, screen attach and USB functioning</span></span>
    <span data-ttu-id="48aba-125">Connectivity</span><span class="sxs-lookup"><span data-stu-id="48aba-125">Connectivity</span></span> |  <span data-ttu-id="48aba-126">Bluetooth、ワイヤレス、LTE の接続性を確認します</span><span class="sxs-lookup"><span data-stu-id="48aba-126">Checks Bluetooth, wireless and LTE connectivity</span></span>
    <span data-ttu-id="48aba-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="48aba-127">Security</span></span>    | <span data-ttu-id="48aba-128">セキュリティ関連の問題をチェックする</span><span class="sxs-lookup"><span data-stu-id="48aba-128">Checks security related issues</span></span>
    <span data-ttu-id="48aba-129">タッチ</span><span class="sxs-lookup"><span data-stu-id="48aba-129">Touch</span></span>   | <span data-ttu-id="48aba-130">タッチ関連の問題をチェックします</span><span class="sxs-lookup"><span data-stu-id="48aba-130">Checks touch related issues</span></span>
    <span data-ttu-id="48aba-131">キーボードとタッチ</span><span class="sxs-lookup"><span data-stu-id="48aba-131">Keyboard and touch</span></span> |    <span data-ttu-id="48aba-132">内蔵キーボード接続と表紙の種類を確認する</span><span class="sxs-lookup"><span data-stu-id="48aba-132">Checks integrated keyboard connection and type cover</span></span>
    <span data-ttu-id="48aba-133">センサー</span><span class="sxs-lookup"><span data-stu-id="48aba-133">Sensors</span></span> | <span data-ttu-id="48aba-134">デバイスでのさまざまなセンサーの機能を確認します</span><span class="sxs-lookup"><span data-stu-id="48aba-134">Checks functioning of different sensors in the device</span></span>
    <span data-ttu-id="48aba-135">ハードウェア</span><span class="sxs-lookup"><span data-stu-id="48aba-135">Hardware</span></span> |  <span data-ttu-id="48aba-136">グラフィックスカードやカメラなど、さまざまなハードウェアコンポーネントに関する問題をチェックします。</span><span class="sxs-lookup"><span data-stu-id="48aba-136">Checks issues with different hardware components such as graphics card and camera</span></span>

5. <span data-ttu-id="48aba-137">すべてのテストが完了したら、問題が修正されたかどうかを確認するようにツールによって求められます。</span><span class="sxs-lookup"><span data-stu-id="48aba-137">When all tests have finished, the tool asks you to confirm if your issue is fixed.</span></span> 

 ![<span data-ttu-id="48aba-138">問題は解決されましたか? ](images/sdt3.png)
*図3a問題は解決されましたか?*</span><span class="sxs-lookup"><span data-stu-id="48aba-138">Has your problem been resolved?](images/sdt3.png)
*Figure 3a. Has your problem been resolved?*</span></span>

6. <span data-ttu-id="48aba-139">問題が解決しない、またはわからない場合は、[**お問い合わせ**] を選択してサポートチケットを送信でき**ます。**</span><span class="sxs-lookup"><span data-stu-id="48aba-139">If the issue isn't resolved or you don't know, you can submit a Support ticket by selecting **Contact us** to **Get help now.**</span></span>
 
 ![<span data-ttu-id="48aba-140">サポートチケットを送信する ](images/sdt4.png)
 *図3bサポートチケットを送信する*</span><span class="sxs-lookup"><span data-stu-id="48aba-140">Submit a Support ticket](images/sdt4.png)
*Figure 3b. Submit a Support ticket*</span></span>

<span id="multiple" />

## <span data-ttu-id="48aba-141">複数のハードウェアテストを実行して問題のトラブルシューティングを行う</span><span class="sxs-lookup"><span data-stu-id="48aba-141">Running multiple hardware tests to troubleshoot issues</span></span>

<span data-ttu-id="48aba-142">SDT は、一連のテストを実行する対話型ツールとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="48aba-142">SDT is designed as an interactive tool that runs a series of tests.</span></span> <span data-ttu-id="48aba-143">各テストについて、SDT では、テストの性質と、テストを成功させるためにユーザーが必要としている、または探していることを確認する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="48aba-143">For each test, SDT provides instructions summarizing  the nature of the test and what users should expect or look for in order for the test to be successful.</span></span> <span data-ttu-id="48aba-144">たとえば、ディスプレイの輝度が正常に機能しているかどうかを診断するために、SDT は100ゼロから始まり、 **[はい**] または [**いいえ**] に応答することで、ユーザーに確認を求めます。図4に示すように、明るさは期待どおりに機能しています。</span><span class="sxs-lookup"><span data-stu-id="48aba-144">For example, to diagnose if the display brightness is working properly, SDT starts at zero and increases the brightness to 100 percent, asking users to confirm – by answering **Yes** or **No** -- that brightness is functioning as expected, as shown in figure 4.</span></span> 

<span data-ttu-id="48aba-145">各テストにおいて、機能が予期したとおりに動作しない場合にユーザーが [**いいえ**] をクリックすると、SDT で考えられる原因とトラブルシューティング方法のレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="48aba-145">For each test, if functionality does not work as expected and the user clicks **No**, SDT generates a report of the possible causes and ways to troubleshoot it.</span></span> 

![<span data-ttu-id="48aba-146">ハードウェア診断 ](images/sdt-desk-4.png)
 *を実行しています図4。ハードウェア診断を実行中*</span><span class="sxs-lookup"><span data-stu-id="48aba-146">Running hardware diagnostics](images/sdt-desk-4.png)
*Figure 4. Running hardware diagnostics*</span></span>

1. <span data-ttu-id="48aba-147">明るさが予期したとおりに0-100 パーセントから正常に調整された場合は、[**はい]** をクリックし、[**続行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48aba-147">If the brightness successfully adjusts from 0-100 percent as expected, direct the user to click **Yes** and then click **Continue**.</span></span> 
2. <span data-ttu-id="48aba-148">輝度の0-100 調整に失敗した場合は、ユーザーに [**いいえ**] をクリックし、[**続行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48aba-148">If the brightness fails to adjust from 0-100 percent as expected, direct the user to click **No** and then click **Continue**.</span></span> 
3. <span data-ttu-id="48aba-149">必要に応じて、残りのテストをユーザーに案内します。</span><span class="sxs-lookup"><span data-stu-id="48aba-149">Guide users through remaining tests as appropriate.</span></span> <span data-ttu-id="48aba-150">完了すると、SDT は、ハードウェアの問題の考えられる原因、および解決のガイダンスなど、レポートの概要を自動的に表示します。</span><span class="sxs-lookup"><span data-stu-id="48aba-150">When finished, SDT automatically provides a high-level summary of the report, including the possible causes of any hardware issues along with guidance for resolution.</span></span>


### <span data-ttu-id="48aba-151">アプリケーションの修復</span><span class="sxs-lookup"><span data-stu-id="48aba-151">Repairing applications</span></span>

<span data-ttu-id="48aba-152">SDT 問題の原因となっている可能性があるアプリケーションを診断して修復することができます。図5に示します。</span><span class="sxs-lookup"><span data-stu-id="48aba-152">SDT enables you to diagnose and repair applications that may be causing issues, as shown in figure 5.</span></span>

![<span data-ttu-id="48aba-153">実行中 ](images/sdt-desk-5.png)
 *の図5の修復修復の実行*</span><span class="sxs-lookup"><span data-stu-id="48aba-153">Running repairs](images/sdt-desk-5.png)
*Figure 5. Running repairs*</span></span>
<span id="logs" />

### <span data-ttu-id="48aba-154">問題を分析するためのログの生成</span><span class="sxs-lookup"><span data-stu-id="48aba-154">Generating logs for analyzing issues</span></span> 

<span data-ttu-id="48aba-155">SDT アプリケーション、ドライバー、ハードウェア、オペレーティングシステムの問題に対して、さまざまなログ対応診断サポートを提供します (図 6)。</span><span class="sxs-lookup"><span data-stu-id="48aba-155">SDT provides extensive log-enabled diagnosis support across applications, drivers, hardware, and operating system issues, as shown in figure 6.</span></span>

![<span data-ttu-id="48aba-156">ログ ](images/sdt-desk-6.png)
 *の生成図6。ログの生成*</span><span class="sxs-lookup"><span data-stu-id="48aba-156">Generating logs](images/sdt-desk-6.png)
*Figure 6. Generating logs*</span></span>

<span id="detailed-report" />

### <span data-ttu-id="48aba-157">デバイスと最適な構成の比較詳細レポートを生成しています</span><span class="sxs-lookup"><span data-stu-id="48aba-157">Generating detailed report comparing device vs. optimal configuration</span></span>

<span data-ttu-id="48aba-158">これらのログに基づいて、SDT は、お好みの場所に保存できるソフトウェアとファームウェアベースの問題に関するレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="48aba-158">Based on the logs, SDT generates a report for software- and firmware-based issues that you can save to a preferred location.</span></span>

## <span data-ttu-id="48aba-159">関連トピック</span><span class="sxs-lookup"><span data-stu-id="48aba-159">Related topics</span></span>

- [<span data-ttu-id="48aba-160">コマンドを使用してビジネス向け Surface 診断ツールキットを実行する</span><span class="sxs-lookup"><span data-stu-id="48aba-160">Run Surface Diagnostic Toolkit for Business using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

