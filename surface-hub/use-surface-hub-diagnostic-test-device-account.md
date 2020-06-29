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
ms.openlocfilehash: 127be0a5f320418d8a1086aec3de62e3ef54e42a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834885"
---
# <span data-ttu-id="7be3b-104">Surface Hub ハードウェア診断ツールを使用したデバイス アカウントのテスト</span><span class="sxs-lookup"><span data-stu-id="7be3b-104">Using the Surface Hub Hardware Diagnostic Tool to test a device account</span></span>

## <span data-ttu-id="7be3b-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="7be3b-105">Introduction</span></span>

> [!NOTE]
> <span data-ttu-id="7be3b-106">Surface Hub ハードウェア診断ツールの [アカウント設定] セクションには、情報は収集されません。</span><span class="sxs-lookup"><span data-stu-id="7be3b-106">The "Account Settings" section of the Surface Hub Hardware Diagnostic tool doesn’t collect any information.</span></span> <span data-ttu-id="7be3b-107">入力として入力されたメールアドレスとパスワードは、環境で直接使用され、すべてのユーザーに収集または転送されることはありません。</span><span class="sxs-lookup"><span data-stu-id="7be3b-107">The email and password that are entered as input are used only directly on your environment and not collected or transferred to anyone.</span></span> <span data-ttu-id="7be3b-108">ログイン情報は、アプリケーションが閉じられるか、Surface Hub で現在のセッションを終了するまでのみ保持されます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-108">The login information persists only until the application is closed or you end the current session on the Surface Hub.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="7be3b-109">このアプリケーションを実行するには、管理者権限は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7be3b-109">Administrator privileges are not required to run this application.</span></span>
> * <span data-ttu-id="7be3b-110">診断の結果は、Microsoft とのサービスコールを開始する前に、ローカル管理者に説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7be3b-110">The results of the diagnostic should be discussed with your local administrator before you open a service call with Microsoft.</span></span>

### <span data-ttu-id="7be3b-111">Surface Hub ハードウェア診断</span><span class="sxs-lookup"><span data-stu-id="7be3b-111">Surface Hub Hardware Diagnostic</span></span>

<span data-ttu-id="7be3b-112">既定では、 [Surface Hub ハードウェア診断](https://www.microsoft.com/store/apps/9nblggh51f2g)アプリケーションは、以前のバージョンの surface hub システムにはインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="7be3b-112">By default, the [Surface Hub Hardware Diagnostic](https://www.microsoft.com/store/apps/9nblggh51f2g) application isn’t installed in earlier versions of the Surface Hub system.</span></span> <span data-ttu-id="7be3b-113">アプリケーションは Microsoft ストアから無料で入手できます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-113">The application is available for free from the Microsoft Store.</span></span> <span data-ttu-id="7be3b-114">アプリケーションをインストールするには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="7be3b-114">Administrator privileges are required to install the application.</span></span>

   ![ハードウェア診断のスクリーンショット](images/01-diagnostic.png)

## <span data-ttu-id="7be3b-116">Surface Hub ハードウェア診断ツールについて</span><span class="sxs-lookup"><span data-stu-id="7be3b-116">About the Surface Hub Hardware Diagnostic Tool</span></span>

<span data-ttu-id="7be3b-117">Surface Hub ハードウェア診断ツールは、Surface Hub デバイス内の多くのハードウェアコンポーネントをユーザーがテストできるようにするための、操作の容易なツールです。</span><span class="sxs-lookup"><span data-stu-id="7be3b-117">The Surface Hub Hardware Diagnostic tool is an easy-to-navigate tool that lets the user test many of the hardware components within the Surface Hub device.</span></span> <span data-ttu-id="7be3b-118">このツールは Surface Hub デバイスアカウントをテストして確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-118">This tool can also test and verify a Surface Hub device account.</span></span> <span data-ttu-id="7be3b-119">この記事では、Surface Hub ハードウェア診断ツール内でのアカウント設定のテストの使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-119">This article describes how to use the Account Settings test within the Surface Hub Hardware Diagnostic tool.</span></span>

> [!NOTE]
> <span data-ttu-id="7be3b-120">テストが完了する前に、Surface Hub のデバイスアカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7be3b-120">The device account for the Surface Hub should be created before any testing is done.</span></span> <span data-ttu-id="7be3b-121">Surface Hub 管理者ガイドには、オンプレミス、オンライン (Office365)、またはハイブリッドデバイスアカウントの作成に役立つ手順と PowerShell スクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7be3b-121">The Surface Hub Administrator Guide provides instructions and PowerShell scripts to help you create on-premises, online (Office365), or hybrid device accounts.</span></span> <span data-ttu-id="7be3b-122">詳細については、ガイドの「[デバイスアカウント (Surface Hub) を作成してテスト](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7be3b-122">For more information, go to the [Create and test a device account (Surface Hub)](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) topic in the guide.</span></span>

### <span data-ttu-id="7be3b-123">デバイスアカウントのテストプロセス</span><span class="sxs-lookup"><span data-stu-id="7be3b-123">Device account testing process</span></span>

1. <span data-ttu-id="7be3b-124">[**すべてのアプリ**] に移動して、Surface Hub ハードウェア診断アプリケーションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-124">Navigate to **All Apps**, and then locate the Surface Hub Hardware Diagnostic application.</span></span>

    ![すべてのアプリのスクリーンショット](images/02-all-apps.png)

1. <span data-ttu-id="7be3b-126">アプリケーションが起動すると、[**ようこそ**] ページに、ハブをテストする理由を文書化するためのテキストウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-126">When the application starts, the **Welcome** page provides a text window to document the reason why you are testing the Hub.</span></span> <span data-ttu-id="7be3b-127">このメモは、テストの完了時に診断結果と共に、USB に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-127">This note can be saved to USB together with the diagnostic results at the conclusion of testing.</span></span> <span data-ttu-id="7be3b-128">メモの入力が完了したら、[**続行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7be3b-128">After you finish entering a note, select the **Continue** button.</span></span>

    ![ようこそのスクリーンショット](images/03-welcome.png)

1. <span data-ttu-id="7be3b-130">次の画面では、Surface Hub のコンポーネントをすべてまたは一部テストするオプションが提供されています。</span><span class="sxs-lookup"><span data-stu-id="7be3b-130">The next screen provides you the option to test all or some of the Surface Hub components.</span></span> <span data-ttu-id="7be3b-131">デバイスアカウントのテストを開始するには、[**テスト結果**] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-131">To begin testing the device account, select the **Test Results** icon.</span></span>

    ![テスト結果のスクリーンショット](images/04-test-results-1.png)

    ![テスト結果のスクリーンショット](images/05-test-results-2.png)

1. <span data-ttu-id="7be3b-134">[**アカウント設定**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-134">Select **Account Settings**.</span></span>  

    ![アカウント設定のスクリーンショット](images/06-account-settings.png)

    <span data-ttu-id="7be3b-136">[アカウントの設定] 画面を使って、お使いのデバイスアカウントをテストします。</span><span class="sxs-lookup"><span data-stu-id="7be3b-136">The Account Settings screen is used to test your device account.</span></span>

    ![アカウント設定の詳細のスクリーンショット](images/07-account-settings-details.png)

1. <span data-ttu-id="7be3b-138">デバイスアカウントのメールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-138">Enter the email address of your device account.</span></span> <span data-ttu-id="7be3b-139">パスワードは省略可能ですが、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="7be3b-139">The password is optional but is recommended.</span></span> <span data-ttu-id="7be3b-140">続行する準備ができたら、[**アカウントのテスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-140">Select the **Test Account** button when you are ready to continue.</span></span>

    ![テストアカウントのスクリーンショット](images/08-test-account.png)

1. <span data-ttu-id="7be3b-142">テストが完了したら、テストの4つの領域の結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-142">After testing is finished, review the results for the four areas of testing.</span></span> <span data-ttu-id="7be3b-143">各セクションの横にあるプラス記号またはマイナス記号を選択すると、各セクションを展開または折りたたむことができます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-143">Each section can be expanded or collapsed by selecting the Plus or Minus sign next to each topic.</span></span>

    **<span data-ttu-id="7be3b-144">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="7be3b-144">Network</span></span>**

    ![Network のスクリーンショット](images/09-network.png)

    **<span data-ttu-id="7be3b-146">環境</span><span class="sxs-lookup"><span data-stu-id="7be3b-146">Environment</span></span>**

    ![環境のスクリーンショット](images/10-environment.png)

    **<span data-ttu-id="7be3b-148">証明書</span><span class="sxs-lookup"><span data-stu-id="7be3b-148">Certificates</span></span>**

    ![証明書のスクリーンショット](images/11-certificates.png)

    **<span data-ttu-id="7be3b-150">信頼モデル</span><span class="sxs-lookup"><span data-stu-id="7be3b-150">Trust Model</span></span>**

    ![信頼モデルのスクリーンショット](images/12-trust-model.png)

## <span data-ttu-id="7be3b-152">付録</span><span class="sxs-lookup"><span data-stu-id="7be3b-152">Appendix</span></span>

### <span data-ttu-id="7be3b-153">フィールドメッセージと解決策</span><span class="sxs-lookup"><span data-stu-id="7be3b-153">Field messages and resolution</span></span>

#### <span data-ttu-id="7be3b-154">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="7be3b-154">Network</span></span>

<span data-ttu-id="7be3b-155">フィールド</span><span class="sxs-lookup"><span data-stu-id="7be3b-155">Field</span></span> |<span data-ttu-id="7be3b-156">Success</span><span class="sxs-lookup"><span data-stu-id="7be3b-156">Success</span></span> |<span data-ttu-id="7be3b-157">失敗</span><span class="sxs-lookup"><span data-stu-id="7be3b-157">Failure</span></span> |<span data-ttu-id="7be3b-158">コメント</span><span class="sxs-lookup"><span data-stu-id="7be3b-158">Comment</span></span> |<span data-ttu-id="7be3b-159">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7be3b-159">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="7be3b-160">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="7be3b-160">Internet Connectivity</span></span> |<span data-ttu-id="7be3b-161">デバイスがインターネットに接続されている</span><span class="sxs-lookup"><span data-stu-id="7be3b-161">Device does have Internet connectivity</span></span> |<span data-ttu-id="7be3b-162">デバイスにインターネット接続がありません</span><span class="sxs-lookup"><span data-stu-id="7be3b-162">Device does not have Internet connectivity</span></span> |<span data-ttu-id="7be3b-163">プロキシ接続などのインターネット接続を確認します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-163">Verifies internet connectivity, including proxy connection</span></span> |
<span data-ttu-id="7be3b-164">HTTP バージョン</span><span class="sxs-lookup"><span data-stu-id="7be3b-164">HTTP Version</span></span> |<span data-ttu-id="7be3b-165">1.1</span><span class="sxs-lookup"><span data-stu-id="7be3b-165">1.1</span></span> |<span data-ttu-id="7be3b-166">1.0</span><span class="sxs-lookup"><span data-stu-id="7be3b-166">1.0</span></span> |<span data-ttu-id="7be3b-167">HTTP 1.0 が検出されると、WU とストアで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7be3b-167">If HTTP 1.0 found, it will cause issue with WU and Store</span></span> |
<span data-ttu-id="7be3b-168">直接インターネット接続</span><span class="sxs-lookup"><span data-stu-id="7be3b-168">Direct Internet Connectivity</span></span> |<span data-ttu-id="7be3b-169">デバイスにプロキシが構成されています。</span><span class="sxs-lookup"><span data-stu-id="7be3b-169">Device has a Proxy configured Device has no Proxy configured</span></span> |<span data-ttu-id="7be3b-170">なし</span><span class="sxs-lookup"><span data-stu-id="7be3b-170">N/A</span></span> |<span data-ttu-id="7be3b-171">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-171">Informational.</span></span> <span data-ttu-id="7be3b-172">お使いのデバイスはプロキシの背後にありますか?</span><span class="sxs-lookup"><span data-stu-id="7be3b-172">Is your device behind a proxy?</span></span> |
<span data-ttu-id="7be3b-173">プロキシアドレス</span><span class="sxs-lookup"><span data-stu-id="7be3b-173">Proxy Address</span></span> | | |<span data-ttu-id="7be3b-174">構成されている場合は、プロキシアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-174">If configured, returns proxy address.</span></span> |
<span data-ttu-id="7be3b-175">プロキシ認証</span><span class="sxs-lookup"><span data-stu-id="7be3b-175">Proxy Authentication</span></span> |<span data-ttu-id="7be3b-176">プロキシは認証を必要としません</span><span class="sxs-lookup"><span data-stu-id="7be3b-176">Proxy does not require Authentication</span></span> |<span data-ttu-id="7be3b-177">プロキシにはプロキシ認証が必要</span><span class="sxs-lookup"><span data-stu-id="7be3b-177">Proxy requires Proxy Auth</span></span> |<span data-ttu-id="7be3b-178">ユーザーが既に Edge で開いているセッションを使っていて、プロキシ経由で認証されている場合、結果は誤認の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7be3b-178">Result may be a false positive if a user already has an open session in Edge and has authenticated through the proxy.</span></span> |
<span data-ttu-id="7be3b-179">プロキシ認証の種類</span><span class="sxs-lookup"><span data-stu-id="7be3b-179">Proxy Auth Types</span></span> | | |<span data-ttu-id="7be3b-180">プロキシ認証が使われている場合は、プロキシによってアドバタイズされた認証メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-180">If proxy authentication is used, return the Authentication methods advertised by the proxy.</span></span>  |

#### <span data-ttu-id="7be3b-181">環境</span><span class="sxs-lookup"><span data-stu-id="7be3b-181">Environment</span></span>

<span data-ttu-id="7be3b-182">フィールド</span><span class="sxs-lookup"><span data-stu-id="7be3b-182">Field</span></span> |<span data-ttu-id="7be3b-183">Success</span><span class="sxs-lookup"><span data-stu-id="7be3b-183">Success</span></span> |<span data-ttu-id="7be3b-184">失敗</span><span class="sxs-lookup"><span data-stu-id="7be3b-184">Failure</span></span> |<span data-ttu-id="7be3b-185">コメント</span><span class="sxs-lookup"><span data-stu-id="7be3b-185">Comment</span></span> |<span data-ttu-id="7be3b-186">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7be3b-186">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="7be3b-187">SIP ドメイン</span><span class="sxs-lookup"><span data-stu-id="7be3b-187">SIP Domain</span></span> | | |<span data-ttu-id="7be3b-188">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-188">Informational.</span></span>  |
<span data-ttu-id="7be3b-189">Skype 環境</span><span class="sxs-lookup"><span data-stu-id="7be3b-189">Skype Environment</span></span> |<span data-ttu-id="7be3b-190">Skype for Business Online、Skype for Business OnPrem、Skype for Business のハイブリッド</span><span class="sxs-lookup"><span data-stu-id="7be3b-190">Skype for Business Online, Skype for Business OnPrem, Skype for Business Hybrid</span></span> |<span data-ttu-id="7be3b-191">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-191">Informational.</span></span> |<span data-ttu-id="7be3b-192">検出された環境の種類。</span><span class="sxs-lookup"><span data-stu-id="7be3b-192">What type of environment was detected.</span></span> <span data-ttu-id="7be3b-193">注: ハイブリッドは、パスワードが入力されている場合にのみ検出されます。</span><span class="sxs-lookup"><span data-stu-id="7be3b-193">Note: Hybrid can only be detected if the password is entered.</span></span>
<span data-ttu-id="7be3b-194">LyncDiscover FQDN</span><span class="sxs-lookup"><span data-stu-id="7be3b-194">LyncDiscover FQDN</span></span> | | |<span data-ttu-id="7be3b-195">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-195">Informational.</span></span> <span data-ttu-id="7be3b-196">LyncDiscover DNS の結果を表示します</span><span class="sxs-lookup"><span data-stu-id="7be3b-196">Displays the LyncDiscover DNS result</span></span> |
<span data-ttu-id="7be3b-197">LyncDiscover URI</span><span class="sxs-lookup"><span data-stu-id="7be3b-197">LyncDiscover URI</span></span> | | |<span data-ttu-id="7be3b-198">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-198">Informational.</span></span> <span data-ttu-id="7be3b-199">環境で LyncDiscover を実行するために使用される URL を表示します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-199">Displays the URL used to perform a LyncDiscover on your environment.</span></span>|
<span data-ttu-id="7be3b-200">LyncDiscover</span><span class="sxs-lookup"><span data-stu-id="7be3b-200">LyncDiscover</span></span> |<span data-ttu-id="7be3b-201">接続に成功しました</span><span class="sxs-lookup"><span data-stu-id="7be3b-201">Connection Successful</span></span> |<span data-ttu-id="7be3b-202">接続に失敗しました</span><span class="sxs-lookup"><span data-stu-id="7be3b-202">Connection Failed</span></span> |<span data-ttu-id="7be3b-203">LyncDiscover web サービスからの応答。</span><span class="sxs-lookup"><span data-stu-id="7be3b-203">Response from LyncDiscover web service.</span></span> |
<span data-ttu-id="7be3b-204">SIP プールのホスト名</span><span class="sxs-lookup"><span data-stu-id="7be3b-204">SIP Pool Hostname</span></span> | | |<span data-ttu-id="7be3b-205">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-205">Informational.</span></span> <span data-ttu-id="7be3b-206">LyncDiscover から検出された SIP プール名を表示する</span><span class="sxs-lookup"><span data-stu-id="7be3b-206">Display the SIP pool name discovered from LyncDiscover</span></span> |

#### <span data-ttu-id="7be3b-207">証明書 (内部設置型ハイブリッドのみ)</span><span class="sxs-lookup"><span data-stu-id="7be3b-207">Certificates (in-premises hybrid only)</span></span>

<span data-ttu-id="7be3b-208">LyncDiscover 証明書</span><span class="sxs-lookup"><span data-stu-id="7be3b-208">LyncDiscover Certificate</span></span>

<span data-ttu-id="7be3b-209">フィールド</span><span class="sxs-lookup"><span data-stu-id="7be3b-209">Field</span></span> |<span data-ttu-id="7be3b-210">Success</span><span class="sxs-lookup"><span data-stu-id="7be3b-210">Success</span></span> |<span data-ttu-id="7be3b-211">失敗</span><span class="sxs-lookup"><span data-stu-id="7be3b-211">Failure</span></span> |<span data-ttu-id="7be3b-212">コメント</span><span class="sxs-lookup"><span data-stu-id="7be3b-212">Comment</span></span> |<span data-ttu-id="7be3b-213">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7be3b-213">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="7be3b-214">LyncDiscover Cert CN</span><span class="sxs-lookup"><span data-stu-id="7be3b-214">LyncDiscover Cert CN</span></span> | | |<span data-ttu-id="7be3b-215">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-215">Informational.</span></span> <span data-ttu-id="7be3b-216">LD 証明書の共通名を表示します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-216">Displays the LD cert Common name</span></span> |
<span data-ttu-id="7be3b-217">LyncDiscover Cert CA</span><span class="sxs-lookup"><span data-stu-id="7be3b-217">LyncDiscover Cert CA</span></span> | | |<span data-ttu-id="7be3b-218">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-218">Informational.</span></span> <span data-ttu-id="7be3b-219">LD Cert CA を表示します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-219">Displays the LD Cert CA</span></span> |
<span data-ttu-id="7be3b-220">LyncDiscover Cert ルート CA</span><span class="sxs-lookup"><span data-stu-id="7be3b-220">LyncDiscover Cert Root CA</span></span> | | |<span data-ttu-id="7be3b-221">情報.</span><span class="sxs-lookup"><span data-stu-id="7be3b-221">Informational.</span></span> <span data-ttu-id="7be3b-222">利用可能な場合は、LD Cert ルート CA を表示します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-222">Displays the LD Cert Root CA, if available.</span></span> |
<span data-ttu-id="7be3b-223">LD の信頼状態</span><span class="sxs-lookup"><span data-stu-id="7be3b-223">LD Trust Status</span></span> |<span data-ttu-id="7be3b-224">証明書が信頼されている。</span><span class="sxs-lookup"><span data-stu-id="7be3b-224">Certificate is Trusted.</span></span> |<span data-ttu-id="7be3b-225">証明書が信頼されていません。ルート CA を追加してください。</span><span class="sxs-lookup"><span data-stu-id="7be3b-225">Certificate is not trusted, please add the Root CA.</span></span> |<span data-ttu-id="7be3b-226">ローカル証明書ストアに対して証明書を確認します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-226">Verify the certificate against the local cert store.</span></span> <span data-ttu-id="7be3b-227">マシンが証明書を信頼している場合は、正の値を返します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-227">Returns positive if the machine trusts the certificate.</span></span>|<span data-ttu-id="7be3b-228">[PowerShell を使用して Skype For business 証明書をダウンロードして展開する](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) /[Surface Hub プロビジョニングパッケージでサポートされている項目](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)</span><span class="sxs-lookup"><span data-stu-id="7be3b-228">[Download and deploy Skype for Business certificates using PowerShell](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/)/[Supported items for Surface Hub provisioning packages](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)</span></span>

<span data-ttu-id="7be3b-229">SIP プール認定</span><span class="sxs-lookup"><span data-stu-id="7be3b-229">SIP Pool Certification</span></span>

<span data-ttu-id="7be3b-230">フィールド</span><span class="sxs-lookup"><span data-stu-id="7be3b-230">Field</span></span> |<span data-ttu-id="7be3b-231">Success</span><span class="sxs-lookup"><span data-stu-id="7be3b-231">Success</span></span> |<span data-ttu-id="7be3b-232">失敗</span><span class="sxs-lookup"><span data-stu-id="7be3b-232">Failure</span></span> |<span data-ttu-id="7be3b-233">コメント</span><span class="sxs-lookup"><span data-stu-id="7be3b-233">Comment</span></span> |<span data-ttu-id="7be3b-234">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7be3b-234">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="7be3b-235">SIP プール Cert CN</span><span class="sxs-lookup"><span data-stu-id="7be3b-235">SIP Pool Cert CN</span></span> | | |<span data-ttu-id="7be3b-236">数式</span><span class="sxs-lookup"><span data-stu-id="7be3b-236">(CONTENTS)</span></span> |
<span data-ttu-id="7be3b-237">SIP プール Cert CA</span><span class="sxs-lookup"><span data-stu-id="7be3b-237">SIP Pool Cert CA</span></span> | | |<span data-ttu-id="7be3b-238">数式</span><span class="sxs-lookup"><span data-stu-id="7be3b-238">(CONTENTS)</span></span> |
<span data-ttu-id="7be3b-239">SIP プールの信頼状態</span><span class="sxs-lookup"><span data-stu-id="7be3b-239">SIP Pool Trust Status</span></span> |<span data-ttu-id="7be3b-240">証明書が信頼されている。</span><span class="sxs-lookup"><span data-stu-id="7be3b-240">Certificate is Trusted.</span></span> |<span data-ttu-id="7be3b-241">証明書が信頼されていません。ルート CA を追加してください。</span><span class="sxs-lookup"><span data-stu-id="7be3b-241">Certificate is not trusted, please add the Root CA.</span></span> |<span data-ttu-id="7be3b-242">ローカル証明書ストアに対して証明書を確認し、デバイスが証明書を信頼する場合は正の値を返します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-242">Verify the certificate against the local cert store and return a positive if the devices trusts the certificate.</span></span> |
<span data-ttu-id="7be3b-243">SIP プール証明書ルート CA</span><span class="sxs-lookup"><span data-stu-id="7be3b-243">SIP Pool Cert Root CA</span></span> | | |<span data-ttu-id="7be3b-244">詳しく.</span><span class="sxs-lookup"><span data-stu-id="7be3b-244">Information.</span></span> <span data-ttu-id="7be3b-245">SIP プール Cert ルート CA を表示します (利用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="7be3b-245">Display the SIP Pool Cert Root CA, if available.</span></span> |

#### <span data-ttu-id="7be3b-246">信頼モデル (オンプレミスハイブリッドのみ)</span><span class="sxs-lookup"><span data-stu-id="7be3b-246">Trust Model (on-premises hybrid only)</span></span>

<span data-ttu-id="7be3b-247">フィールド</span><span class="sxs-lookup"><span data-stu-id="7be3b-247">Field</span></span> |<span data-ttu-id="7be3b-248">Success</span><span class="sxs-lookup"><span data-stu-id="7be3b-248">Success</span></span> |<span data-ttu-id="7be3b-249">失敗</span><span class="sxs-lookup"><span data-stu-id="7be3b-249">Failure</span></span> |<span data-ttu-id="7be3b-250">コメント</span><span class="sxs-lookup"><span data-stu-id="7be3b-250">Comment</span></span> |<span data-ttu-id="7be3b-251">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7be3b-251">Reference</span></span>
|------|------|------|------|------|
<span data-ttu-id="7be3b-252">信頼モデルの状態</span><span class="sxs-lookup"><span data-stu-id="7be3b-252">Trust Model Status</span></span> |<span data-ttu-id="7be3b-253">信頼モデルの問題は検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="7be3b-253">No Trust Model Issue Detected.</span></span> |<span data-ttu-id="7be3b-254">SIP ドメインとサーバードメインが異なる場合は、次のドメインを追加してください。</span><span class="sxs-lookup"><span data-stu-id="7be3b-254">SIP Domain and server domain are different please add the following domains.</span></span> |<span data-ttu-id="7be3b-255">信頼性モデルの問題については、LD FQDN/LD サーバー名/プールサーバー名を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7be3b-255">Check the LD FQDN/ LD Server Name/ Pool Server name for Trust model issue.</span></span> 
<span data-ttu-id="7be3b-256">ドメイン名</span><span class="sxs-lookup"><span data-stu-id="7be3b-256">Domain Name(s)</span></span> | | |<span data-ttu-id="7be3b-257">SFB に接続するために追加する必要があるドメインの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="7be3b-257">Return the list of domains that should be added for SFB to connect.</span></span> |
