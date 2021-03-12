---
title: Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト
description: Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト
ms.assetid: a87b7d41-d0a7-4acc-bfa6-b9070f99bc9c
keywords: アクセシビリティの設定, 設定アプリ, 簡単操作
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 6661f2347d2f411ed11fe6057ede8ca2bab07c33
ms.sourcegitcommit: f0c976664116c45605edf3d56c4f58119a246b93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "11406670"
---
# <a name="using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-account"></a><span data-ttu-id="85c8a-104">Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト</span><span class="sxs-lookup"><span data-stu-id="85c8a-104">Using the Surface Hub Hardware Diagnostic Tool to test a device account</span></span>

## <a name="introduction"></a><span data-ttu-id="85c8a-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="85c8a-105">Introduction</span></span>

> [!NOTE]
> <span data-ttu-id="85c8a-106">Surface Hub ハードウェア診断ツールの [アカウント設定] セクションでは、情報は収集されません。</span><span class="sxs-lookup"><span data-stu-id="85c8a-106">The "Account Settings" section of the Surface Hub Hardware Diagnostic tool doesn’t collect any information.</span></span> <span data-ttu-id="85c8a-107">入力として入力される電子メールとパスワードは、環境上でのみ直接使用され、誰にも収集または転送されません。</span><span class="sxs-lookup"><span data-stu-id="85c8a-107">The email and password that are entered as input are used only directly on your environment and not collected or transferred to anyone.</span></span> <span data-ttu-id="85c8a-108">ログイン情報は、アプリケーションが閉じているか、Surface Hub で現在のセッションを終了するまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-108">The login information persists only until the application is closed or you end the current session on the Surface Hub.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="85c8a-109">このアプリケーションを実行するには、管理者特権は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="85c8a-109">Administrator privileges are not required to run this application.</span></span>
> * <span data-ttu-id="85c8a-110">Microsoft でサービス呼び出しを開く前に、ローカル管理者と診断の結果について説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85c8a-110">The results of the diagnostic should be discussed with your local administrator before you open a service call with Microsoft.</span></span>

### <a name="surface-hub-hardware-diagnostic"></a><span data-ttu-id="85c8a-111">Surface Hub ハードウェア診断</span><span class="sxs-lookup"><span data-stu-id="85c8a-111">Surface Hub Hardware Diagnostic</span></span>

<span data-ttu-id="85c8a-112">既定では [、Surface Hub ハードウェア診断](https://www.microsoft.com/store/apps/9nblggh51f2g) アプリケーションは以前のバージョンの Surface Hub システムにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="85c8a-112">By default, the [Surface Hub Hardware Diagnostic](https://www.microsoft.com/store/apps/9nblggh51f2g) application isn’t installed in earlier versions of the Surface Hub system.</span></span> <span data-ttu-id="85c8a-113">アプリケーションは、Microsoft Store から無料で利用できます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-113">The application is available for free from the Microsoft Store.</span></span> <span data-ttu-id="85c8a-114">アプリケーションをインストールするには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="85c8a-114">Administrator privileges are required to install the application.</span></span>

   ![ハードウェア診断のスクリーンショット](images/01-diagnostic.png)

## <a name="about-the-surface-hub-hardware-diagnostic-tool"></a><span data-ttu-id="85c8a-116">Surface Hub ハードウェア診断ツールについて</span><span class="sxs-lookup"><span data-stu-id="85c8a-116">About the Surface Hub Hardware Diagnostic Tool</span></span>

<span data-ttu-id="85c8a-117">Surface Hub ハードウェア診断ツールは、ユーザーが Surface Hub デバイス内の多くのハードウェア コンポーネントをテストできる、簡単に操作できるツールです。</span><span class="sxs-lookup"><span data-stu-id="85c8a-117">The Surface Hub Hardware Diagnostic tool is an easy-to-navigate tool that lets the user test many of the hardware components within the Surface Hub device.</span></span> <span data-ttu-id="85c8a-118">このツールでは、Surface Hub デバイス アカウントをテストして確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-118">This tool can also test and verify a Surface Hub device account.</span></span> <span data-ttu-id="85c8a-119">この記事では、Surface Hub ハードウェア診断ツール内でアカウント設定テストを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-119">This article describes how to use the Account Settings test within the Surface Hub Hardware Diagnostic tool.</span></span>

> [!NOTE]
> <span data-ttu-id="85c8a-120">テストが完了する前に、Surface Hub のデバイス アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85c8a-120">The device account for the Surface Hub should be created before any testing is done.</span></span> <span data-ttu-id="85c8a-121">Surface Hub 管理者ガイドには、オンプレミス、オンライン (Office365)、またはハイブリッド デバイス アカウントの作成に役立つ手順と PowerShell スクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="85c8a-121">The Surface Hub Administrator Guide provides instructions and PowerShell scripts to help you create on-premises, online (Office365), or hybrid device accounts.</span></span> <span data-ttu-id="85c8a-122">詳細については、ガイドの「デバイス アカウントの作成とテスト [(Surface Hub)」](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85c8a-122">For more information, go to the [Create and test a device account (Surface Hub)](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) topic in the guide.</span></span>

### <a name="device-account-testing-process"></a><span data-ttu-id="85c8a-123">デバイス アカウントのテスト プロセス</span><span class="sxs-lookup"><span data-stu-id="85c8a-123">Device account testing process</span></span>

1. <span data-ttu-id="85c8a-124">[すべてのアプリ **] に移動**し、Surface Hub ハードウェア診断アプリケーションを探します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-124">Navigate to **All Apps**, and then locate the Surface Hub Hardware Diagnostic application.</span></span>

    ![すべてのアプリのスクリーンショット](images/02-all-apps.png)

1. <span data-ttu-id="85c8a-126">アプリケーションが起動すると、[ようこそ] **ページ** に、ハブをテストする理由を示すテキスト ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-126">When the application starts, the **Welcome** page provides a text window to document the reason why you are testing the Hub.</span></span> <span data-ttu-id="85c8a-127">このメモは、テストの最後に診断結果と共に USB に保存できます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-127">This note can be saved to USB together with the diagnostic results at the conclusion of testing.</span></span> <span data-ttu-id="85c8a-128">メモの入力が完了したら、[続行] ボタン **を選択** します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-128">After you finish entering a note, select the **Continue** button.</span></span>

    >[!NOTE]
    ><span data-ttu-id="85c8a-129">診断結果を保存する場合は、既定のパスを変更したり、サブディレクトリを選択したりしない。</span><span class="sxs-lookup"><span data-stu-id="85c8a-129">When saving diagnostic results, do not change the default path or select a subdirectory.</span></span> <span data-ttu-id="85c8a-130">ファイルは、後でエクスプローラー アプリを使用してコピーできます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-130">The files can be copied later via the File Explorer app.</span></span>

    ![ようこそのスクリーンショット](images/03-welcome.png)

1. <span data-ttu-id="85c8a-132">次の画面では、Surface Hub コンポーネントのすべてまたは一部をテストできます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-132">The next screen provides you the option to test all or some of the Surface Hub components.</span></span> <span data-ttu-id="85c8a-133">デバイス アカウントのテストを開始するには、[テスト結果] **アイコンを選択** します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-133">To begin testing the device account, select the **Test Results** icon.</span></span>

    ![テスト オプションのスクリーンショット](images/04-test-results-1.png)

    ![テスト結果のスクリーンショット](images/05-test-results-2.png)

1. <span data-ttu-id="85c8a-136">[アカウント **設定] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="85c8a-136">Select **Account Settings**.</span></span>  

    ![アカウント設定のスクリーンショット](images/06-account-settings.png)

    <span data-ttu-id="85c8a-138">[アカウント設定] 画面を使用して、デバイス アカウントをテストします。</span><span class="sxs-lookup"><span data-stu-id="85c8a-138">The Account Settings screen is used to test your device account.</span></span>

    ![アカウント設定の詳細のスクリーンショット](images/07-account-settings-details.png)

1. <span data-ttu-id="85c8a-140">デバイス アカウントのメール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-140">Enter the email address of your device account.</span></span> <span data-ttu-id="85c8a-141">パスワードは省略可能ですが、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="85c8a-141">The password is optional but is recommended.</span></span> <span data-ttu-id="85c8a-142">続行する **準備ができたら** 、[テスト アカウント] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-142">Select the **Test Account** button when you are ready to continue.</span></span>

    ![テスト アカウントのスクリーンショット](images/08-test-account.png)

1. <span data-ttu-id="85c8a-144">テストが完了したら、テストの 4 つの領域の結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-144">After testing is finished, review the results for the four areas of testing.</span></span> <span data-ttu-id="85c8a-145">各セクションは、各トピックの横にあるプラス記号またはマイナス記号を選択して展開または折りたたみできます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-145">Each section can be expanded or collapsed by selecting the Plus or Minus sign next to each topic.</span></span>

    **<span data-ttu-id="85c8a-146">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="85c8a-146">Network</span></span>**

    ![ネットワークのスクリーンショット](images/09-network.png)

    **<span data-ttu-id="85c8a-148">環境</span><span class="sxs-lookup"><span data-stu-id="85c8a-148">Environment</span></span>**

    ![環境のスクリーンショット](images/10-environment.png)

    **<span data-ttu-id="85c8a-150">証明書</span><span class="sxs-lookup"><span data-stu-id="85c8a-150">Certificates</span></span>**

    ![証明書のスクリーンショット](images/11-certificates.png)

    **<span data-ttu-id="85c8a-152">信頼モデル</span><span class="sxs-lookup"><span data-stu-id="85c8a-152">Trust Model</span></span>**

    ![信頼モデルのスクリーンショット](images/12-trust-model.png)

## <a name="appendix"></a><span data-ttu-id="85c8a-154">付録</span><span class="sxs-lookup"><span data-stu-id="85c8a-154">Appendix</span></span>

### <a name="field-messages-and-resolution"></a><span data-ttu-id="85c8a-155">フィールド メッセージと解決</span><span class="sxs-lookup"><span data-stu-id="85c8a-155">Field messages and resolution</span></span>

#### <a name="network"></a><span data-ttu-id="85c8a-156">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="85c8a-156">Network</span></span>

<span data-ttu-id="85c8a-157">フィールド</span><span class="sxs-lookup"><span data-stu-id="85c8a-157">Field</span></span> |<span data-ttu-id="85c8a-158">成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-158">Success</span></span> |<span data-ttu-id="85c8a-159">失敗</span><span class="sxs-lookup"><span data-stu-id="85c8a-159">Failure</span></span> |<span data-ttu-id="85c8a-160">コメント</span><span class="sxs-lookup"><span data-stu-id="85c8a-160">Comment</span></span> |<span data-ttu-id="85c8a-161">リファレンス</span><span class="sxs-lookup"><span data-stu-id="85c8a-161">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="85c8a-162">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="85c8a-162">Internet Connectivity</span></span> |<span data-ttu-id="85c8a-163">デバイスにインターネット接続がある</span><span class="sxs-lookup"><span data-stu-id="85c8a-163">Device does have Internet connectivity</span></span> |<span data-ttu-id="85c8a-164">デバイスにインターネット接続が存在しない</span><span class="sxs-lookup"><span data-stu-id="85c8a-164">Device does not have Internet connectivity</span></span> |<span data-ttu-id="85c8a-165">プロキシ接続を含むインターネット接続を確認する</span><span class="sxs-lookup"><span data-stu-id="85c8a-165">Verifies internet connectivity, including proxy connection</span></span> |
<span data-ttu-id="85c8a-166">HTTP バージョン</span><span class="sxs-lookup"><span data-stu-id="85c8a-166">HTTP Version</span></span> |<span data-ttu-id="85c8a-167">1.1</span><span class="sxs-lookup"><span data-stu-id="85c8a-167">1.1</span></span> |<span data-ttu-id="85c8a-168">1.0</span><span class="sxs-lookup"><span data-stu-id="85c8a-168">1.0</span></span> |<span data-ttu-id="85c8a-169">HTTP 1.0 が見つかった場合、WU とストアで問題が発生します</span><span class="sxs-lookup"><span data-stu-id="85c8a-169">If HTTP 1.0 found, it will cause issue with WU and Store</span></span> |
<span data-ttu-id="85c8a-170">ダイレクト インターネット接続</span><span class="sxs-lookup"><span data-stu-id="85c8a-170">Direct Internet Connectivity</span></span> |<span data-ttu-id="85c8a-171">デバイスにプロキシが構成されているデバイスにプロキシが構成されていない</span><span class="sxs-lookup"><span data-stu-id="85c8a-171">Device has a Proxy configured Device has no Proxy configured</span></span> |<span data-ttu-id="85c8a-172">該当せず</span><span class="sxs-lookup"><span data-stu-id="85c8a-172">N/A</span></span> |<span data-ttu-id="85c8a-173">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-173">Informational.</span></span> <span data-ttu-id="85c8a-174">デバイスがプロキシの背後にあるか。</span><span class="sxs-lookup"><span data-stu-id="85c8a-174">Is your device behind a proxy?</span></span> |
<span data-ttu-id="85c8a-175">プロキシ アドレス</span><span class="sxs-lookup"><span data-stu-id="85c8a-175">Proxy Address</span></span> | | |<span data-ttu-id="85c8a-176">構成されている場合は、プロキシ アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-176">If configured, returns proxy address.</span></span> |
<span data-ttu-id="85c8a-177">プロキシ認証</span><span class="sxs-lookup"><span data-stu-id="85c8a-177">Proxy Authentication</span></span> |<span data-ttu-id="85c8a-178">プロキシは認証を必要としない</span><span class="sxs-lookup"><span data-stu-id="85c8a-178">Proxy does not require Authentication</span></span> |<span data-ttu-id="85c8a-179">プロキシにはプロキシ認証が必要です</span><span class="sxs-lookup"><span data-stu-id="85c8a-179">Proxy requires Proxy Auth</span></span> |<span data-ttu-id="85c8a-180">ユーザーがエッジで開いているセッションを既に持ち、プロキシを介して認証されている場合、結果は誤検知になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="85c8a-180">Result may be a false positive if a user already has an open session in Edge and has authenticated through the proxy.</span></span> |
<span data-ttu-id="85c8a-181">プロキシ認証の種類</span><span class="sxs-lookup"><span data-stu-id="85c8a-181">Proxy Auth Types</span></span> | | |<span data-ttu-id="85c8a-182">プロキシ認証を使用する場合は、プロキシによってアドバタイズされた認証メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-182">If proxy authentication is used, return the Authentication methods advertised by the proxy.</span></span>  |

#### <a name="environment"></a><span data-ttu-id="85c8a-183">環境</span><span class="sxs-lookup"><span data-stu-id="85c8a-183">Environment</span></span>

<span data-ttu-id="85c8a-184">フィールド</span><span class="sxs-lookup"><span data-stu-id="85c8a-184">Field</span></span> |<span data-ttu-id="85c8a-185">成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-185">Success</span></span> |<span data-ttu-id="85c8a-186">失敗</span><span class="sxs-lookup"><span data-stu-id="85c8a-186">Failure</span></span> |<span data-ttu-id="85c8a-187">コメント</span><span class="sxs-lookup"><span data-stu-id="85c8a-187">Comment</span></span> |<span data-ttu-id="85c8a-188">リファレンス</span><span class="sxs-lookup"><span data-stu-id="85c8a-188">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="85c8a-189">SIP ドメイン</span><span class="sxs-lookup"><span data-stu-id="85c8a-189">SIP Domain</span></span> | | |<span data-ttu-id="85c8a-190">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-190">Informational.</span></span>  |
<span data-ttu-id="85c8a-191">Skype 環境</span><span class="sxs-lookup"><span data-stu-id="85c8a-191">Skype Environment</span></span> |<span data-ttu-id="85c8a-192">Skype for Business Online, Skype for Business OnPrem, Skype for Business Hybrid</span><span class="sxs-lookup"><span data-stu-id="85c8a-192">Skype for Business Online, Skype for Business OnPrem, Skype for Business Hybrid</span></span> |<span data-ttu-id="85c8a-193">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-193">Informational.</span></span> |<span data-ttu-id="85c8a-194">検出された環境の種類。</span><span class="sxs-lookup"><span data-stu-id="85c8a-194">What type of environment was detected.</span></span> <span data-ttu-id="85c8a-195">注: ハイブリッドは、パスワードが入力されている場合にのみ検出できます。</span><span class="sxs-lookup"><span data-stu-id="85c8a-195">Note: Hybrid can only be detected if the password is entered.</span></span>
<span data-ttu-id="85c8a-196">LyncDiscover FQDN</span><span class="sxs-lookup"><span data-stu-id="85c8a-196">LyncDiscover FQDN</span></span> | | |<span data-ttu-id="85c8a-197">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-197">Informational.</span></span> <span data-ttu-id="85c8a-198">LyncDiscover DNS の結果を表示する</span><span class="sxs-lookup"><span data-stu-id="85c8a-198">Displays the LyncDiscover DNS result</span></span> |
<span data-ttu-id="85c8a-199">LyncDiscover URI</span><span class="sxs-lookup"><span data-stu-id="85c8a-199">LyncDiscover URI</span></span> | | |<span data-ttu-id="85c8a-200">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-200">Informational.</span></span> <span data-ttu-id="85c8a-201">環境で LyncDiscover を実行するために使用される URL を表示します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-201">Displays the URL used to perform a LyncDiscover on your environment.</span></span>|
<span data-ttu-id="85c8a-202">LyncDiscover</span><span class="sxs-lookup"><span data-stu-id="85c8a-202">LyncDiscover</span></span> |<span data-ttu-id="85c8a-203">接続成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-203">Connection Successful</span></span> |<span data-ttu-id="85c8a-204">接続に失敗しました</span><span class="sxs-lookup"><span data-stu-id="85c8a-204">Connection Failed</span></span> |<span data-ttu-id="85c8a-205">LyncDiscover Web サービスからの応答。</span><span class="sxs-lookup"><span data-stu-id="85c8a-205">Response from LyncDiscover web service.</span></span> |
<span data-ttu-id="85c8a-206">SIP プールのホスト名</span><span class="sxs-lookup"><span data-stu-id="85c8a-206">SIP Pool Hostname</span></span> | | |<span data-ttu-id="85c8a-207">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-207">Informational.</span></span> <span data-ttu-id="85c8a-208">LyncDiscover から検出された SIP プール名を表示する</span><span class="sxs-lookup"><span data-stu-id="85c8a-208">Display the SIP pool name discovered from LyncDiscover</span></span> |

#### <a name="certificates-in-premises-hybrid-only"></a><span data-ttu-id="85c8a-209">証明書 (オンプレミスハイブリッドのみ)</span><span class="sxs-lookup"><span data-stu-id="85c8a-209">Certificates (in-premises hybrid only)</span></span>

<span data-ttu-id="85c8a-210">LyncDiscover 証明書</span><span class="sxs-lookup"><span data-stu-id="85c8a-210">LyncDiscover Certificate</span></span>

<span data-ttu-id="85c8a-211">フィールド</span><span class="sxs-lookup"><span data-stu-id="85c8a-211">Field</span></span> |<span data-ttu-id="85c8a-212">成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-212">Success</span></span> |<span data-ttu-id="85c8a-213">失敗</span><span class="sxs-lookup"><span data-stu-id="85c8a-213">Failure</span></span> |<span data-ttu-id="85c8a-214">コメント</span><span class="sxs-lookup"><span data-stu-id="85c8a-214">Comment</span></span> |<span data-ttu-id="85c8a-215">リファレンス</span><span class="sxs-lookup"><span data-stu-id="85c8a-215">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="85c8a-216">LyncDiscover 証明書 CN</span><span class="sxs-lookup"><span data-stu-id="85c8a-216">LyncDiscover Cert CN</span></span> | | |<span data-ttu-id="85c8a-217">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-217">Informational.</span></span> <span data-ttu-id="85c8a-218">LD 証明書の共通名を表示します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-218">Displays the LD cert Common name</span></span> |
<span data-ttu-id="85c8a-219">LyncDiscover 証明書 CA</span><span class="sxs-lookup"><span data-stu-id="85c8a-219">LyncDiscover Cert CA</span></span> | | |<span data-ttu-id="85c8a-220">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-220">Informational.</span></span> <span data-ttu-id="85c8a-221">LD 証明書 CA を表示します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-221">Displays the LD Cert CA</span></span> |
<span data-ttu-id="85c8a-222">LyncDiscover 証明書ルート CA</span><span class="sxs-lookup"><span data-stu-id="85c8a-222">LyncDiscover Cert Root CA</span></span> | | |<span data-ttu-id="85c8a-223">Informational。</span><span class="sxs-lookup"><span data-stu-id="85c8a-223">Informational.</span></span> <span data-ttu-id="85c8a-224">LD Cert ルート CA を表示します (使用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="85c8a-224">Displays the LD Cert Root CA, if available.</span></span> |
<span data-ttu-id="85c8a-225">LD の信頼状態</span><span class="sxs-lookup"><span data-stu-id="85c8a-225">LD Trust Status</span></span> |<span data-ttu-id="85c8a-226">証明書は信頼済みです。</span><span class="sxs-lookup"><span data-stu-id="85c8a-226">Certificate is Trusted.</span></span> |<span data-ttu-id="85c8a-227">証明書が信頼されていない場合は、ルート CA を追加してください。</span><span class="sxs-lookup"><span data-stu-id="85c8a-227">Certificate is not trusted, please add the Root CA.</span></span> |<span data-ttu-id="85c8a-228">ローカル証明書ストアに対して証明書を確認します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-228">Verify the certificate against the local cert store.</span></span> <span data-ttu-id="85c8a-229">コンピューターが証明書を信頼する場合は、正の値を返します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-229">Returns positive if the machine trusts the certificate.</span></span>|<span data-ttu-id="85c8a-230">[PowerShell を使用して Skype for Business 証明書をダウンロードして展開する](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) /[Surface Hub プロビジョニング パッケージでサポートされているアイテム](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)</span><span class="sxs-lookup"><span data-stu-id="85c8a-230">[Download and deploy Skype for Business certificates using PowerShell](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/)/[Supported items for Surface Hub provisioning packages](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)</span></span>

<span data-ttu-id="85c8a-231">SIP プール認定</span><span class="sxs-lookup"><span data-stu-id="85c8a-231">SIP Pool Certification</span></span>

<span data-ttu-id="85c8a-232">フィールド</span><span class="sxs-lookup"><span data-stu-id="85c8a-232">Field</span></span> |<span data-ttu-id="85c8a-233">成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-233">Success</span></span> |<span data-ttu-id="85c8a-234">失敗</span><span class="sxs-lookup"><span data-stu-id="85c8a-234">Failure</span></span> |<span data-ttu-id="85c8a-235">コメント</span><span class="sxs-lookup"><span data-stu-id="85c8a-235">Comment</span></span> |<span data-ttu-id="85c8a-236">リファレンス</span><span class="sxs-lookup"><span data-stu-id="85c8a-236">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="85c8a-237">SIP プール証明書 CN</span><span class="sxs-lookup"><span data-stu-id="85c8a-237">SIP Pool Cert CN</span></span> | | |<span data-ttu-id="85c8a-238">(CONTENTS)</span><span class="sxs-lookup"><span data-stu-id="85c8a-238">(CONTENTS)</span></span> |
<span data-ttu-id="85c8a-239">SIP プール証明書 CA</span><span class="sxs-lookup"><span data-stu-id="85c8a-239">SIP Pool Cert CA</span></span> | | |<span data-ttu-id="85c8a-240">(CONTENTS)</span><span class="sxs-lookup"><span data-stu-id="85c8a-240">(CONTENTS)</span></span> |
<span data-ttu-id="85c8a-241">SIP プールの信頼状態</span><span class="sxs-lookup"><span data-stu-id="85c8a-241">SIP Pool Trust Status</span></span> |<span data-ttu-id="85c8a-242">証明書は信頼済みです。</span><span class="sxs-lookup"><span data-stu-id="85c8a-242">Certificate is Trusted.</span></span> |<span data-ttu-id="85c8a-243">証明書が信頼されていない場合は、ルート CA を追加してください。</span><span class="sxs-lookup"><span data-stu-id="85c8a-243">Certificate is not trusted, please add the Root CA.</span></span> |<span data-ttu-id="85c8a-244">ローカル証明書ストアに対して証明書を確認し、デバイスが証明書を信頼している場合は正の値を返します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-244">Verify the certificate against the local cert store and return a positive if the devices trusts the certificate.</span></span> |
<span data-ttu-id="85c8a-245">SIP プール証明書ルート CA</span><span class="sxs-lookup"><span data-stu-id="85c8a-245">SIP Pool Cert Root CA</span></span> | | |<span data-ttu-id="85c8a-246">情報。</span><span class="sxs-lookup"><span data-stu-id="85c8a-246">Information.</span></span> <span data-ttu-id="85c8a-247">使用可能な場合は、SIP プール証明書ルート CA を表示します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-247">Display the SIP Pool Cert Root CA, if available.</span></span> |

#### <a name="trust-model-on-premises-hybrid-only"></a><span data-ttu-id="85c8a-248">信頼モデル (オンプレミス ハイブリッドのみ)</span><span class="sxs-lookup"><span data-stu-id="85c8a-248">Trust Model (on-premises hybrid only)</span></span>

<span data-ttu-id="85c8a-249">フィールド</span><span class="sxs-lookup"><span data-stu-id="85c8a-249">Field</span></span> |<span data-ttu-id="85c8a-250">成功</span><span class="sxs-lookup"><span data-stu-id="85c8a-250">Success</span></span> |<span data-ttu-id="85c8a-251">失敗</span><span class="sxs-lookup"><span data-stu-id="85c8a-251">Failure</span></span> |<span data-ttu-id="85c8a-252">コメント</span><span class="sxs-lookup"><span data-stu-id="85c8a-252">Comment</span></span> |<span data-ttu-id="85c8a-253">リファレンス</span><span class="sxs-lookup"><span data-stu-id="85c8a-253">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="85c8a-254">信頼モデルの状態</span><span class="sxs-lookup"><span data-stu-id="85c8a-254">Trust Model Status</span></span> |<span data-ttu-id="85c8a-255">信頼モデルの問題が検出されません。</span><span class="sxs-lookup"><span data-stu-id="85c8a-255">No Trust Model Issue Detected.</span></span> |<span data-ttu-id="85c8a-256">SIP ドメインとサーバー ドメインが異なる場合は、次のドメインを追加してください。</span><span class="sxs-lookup"><span data-stu-id="85c8a-256">SIP Domain and server domain are different please add the following domains.</span></span> |<span data-ttu-id="85c8a-257">信頼モデルの問題については、LD FQDN/LD Server 名/プール サーバー名を確認してください。</span><span class="sxs-lookup"><span data-stu-id="85c8a-257">Check the LD FQDN/ LD Server Name/ Pool Server name for Trust model issue.</span></span> 
<span data-ttu-id="85c8a-258">ドメイン名</span><span class="sxs-lookup"><span data-stu-id="85c8a-258">Domain Name(s)</span></span> | | |<span data-ttu-id="85c8a-259">SFB が接続するために追加する必要があるドメインの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="85c8a-259">Return the list of domains that should be added for SFB to connect.</span></span> |
