---
title: ビジネス向け Surface 診断ツールキットを展開する
description: このトピックでは、ビジネス向け Surface 診断ツールキットの使用方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/12/2020
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 1f2661811516507abd432dba602cf8ce81e6dbb3
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114665"
---
# <span data-ttu-id="d433f-103">ビジネス向け Surface 診断ツールキットを展開する</span><span class="sxs-lookup"><span data-stu-id="d433f-103">Deploy Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="d433f-104">Microsoft Surface Diagnostic ツールキット for Business (SDT) を使うと、IT 管理者は Surface デバイスに関するハードウェア、ソフトウェア、ファームウェアの問題をすばやく調査、トラブルシューティング、解決できます。</span><span class="sxs-lookup"><span data-stu-id="d433f-104">The Microsoft Surface Diagnostic Toolkit for Business (SDT) enables IT administrators to quickly investigate, troubleshoot, and resolve hardware, software, and firmware issues with Surface devices.</span></span> <span data-ttu-id="d433f-105">デバイス正常性の分析や問題解決のガイダンスなど、さまざまな診断テストとソフトウェア修復を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d433f-105">You can run a range of diagnostic tests and software repairs in addition to obtaining device health insights and guidance for resolving issues.</span></span> 

<span data-ttu-id="d433f-106">具体的には、SDT for Business で次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d433f-106">Specifically, SDT for Business enables you to:</span></span>

- [<span data-ttu-id="d433f-107">パッケージをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="d433f-107">Customize the package.</span></span>](#create-custom-sdt)
- [<span data-ttu-id="d433f-108">コマンドを使用してアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="d433f-108">Run the app using commands.</span></span>](surface-diagnostic-toolkit-command-line.md)
- [<span data-ttu-id="d433f-109">問題のトラブルシューティングを行うために複数のハードウェアテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="d433f-109">Run multiple hardware tests to troubleshoot issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [<span data-ttu-id="d433f-110">問題を分析するためのログを生成します。</span><span class="sxs-lookup"><span data-stu-id="d433f-110">Generate logs for analyzing issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [<span data-ttu-id="d433f-111">デバイスと最適な構成の比較の詳細レポートを入手します。</span><span class="sxs-lookup"><span data-stu-id="d433f-111">Obtain detailed report comparing device vs optimal configuration.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## <span data-ttu-id="d433f-112">主要なシナリオとリソースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d433f-112">Primary scenarios and download resources</span></span> 

<span data-ttu-id="d433f-113">一般法人向けの SDT を実行するには、次の表に示されているコンポーネントをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d433f-113">To run SDT for Business, download the components listed in the following table.</span></span>


<span data-ttu-id="d433f-114">モード</span><span class="sxs-lookup"><span data-stu-id="d433f-114">Mode</span></span> |  <span data-ttu-id="d433f-115">主要なシナリオ</span><span class="sxs-lookup"><span data-stu-id="d433f-115">Primary scenarios</span></span> | <span data-ttu-id="d433f-116">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="d433f-116">Download</span></span> | <span data-ttu-id="d433f-117">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d433f-117">Learn more</span></span>
--- | --- | --- | ---
<span data-ttu-id="d433f-118">デスクトップ モード</span><span class="sxs-lookup"><span data-stu-id="d433f-118">Desktop mode</span></span> |  <span data-ttu-id="d433f-119">問題のトラブルシューティングを行うために、ユーザーが Surface デバイスで SDT を実行するのを支援します。</span><span class="sxs-lookup"><span data-stu-id="d433f-119">Assist users in running SDT on their Surface devices to troubleshoot issues.</span></span><br><span data-ttu-id="d433f-120">1つ以上の Surface デバイスに展開するカスタムパッケージを作成して、ユーザーが収集および分析する特定のログを選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d433f-120">Create a custom package to deploy on one or more Surface devices allowing users to select specific logs to collect and analyze.</span></span> | <span data-ttu-id="d433f-121">SDT 配布可能 MSI パッケージ:</span><span class="sxs-lookup"><span data-stu-id="d433f-121">SDT distributable MSI package:</span></span><br><span data-ttu-id="d433f-122">Microsoft Surface Diagnostic Toolkit for Business Installer</span><span class="sxs-lookup"><span data-stu-id="d433f-122">Microsoft Surface Diagnostic Toolkit for Business Installer</span></span><br>[<span data-ttu-id="d433f-123">IT 担当者向け Surface ツール</span><span class="sxs-lookup"><span data-stu-id="d433f-123">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="d433f-124">デスクトップモードで Surface 診断ツールキットを使う</span><span class="sxs-lookup"><span data-stu-id="d433f-124">Use Surface Diagnostic Toolkit in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
<span data-ttu-id="d433f-125">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="d433f-125">Command line</span></span> |  <span data-ttu-id="d433f-126">構成マネージャーなどの標準ツールを使用して、ユーザーの操作なしで Surface デバイスをリモートで直接トラブルシューティングします。</span><span class="sxs-lookup"><span data-stu-id="d433f-126">Directly troubleshoot Surface devices remotely without user interaction, using standard tools such as Configuration Manager.</span></span> <span data-ttu-id="d433f-127">次のコマンドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d433f-127">It includes the following commands:</span></span><br>`-DataCollector` <span data-ttu-id="d433f-128">すべてのログファイルを収集します</span><span class="sxs-lookup"><span data-stu-id="d433f-128">collects all log files</span></span><br>`-bpa` <span data-ttu-id="d433f-129">ベストプラクティスアナライザーを使用して正常性診断を実行します。</span><span class="sxs-lookup"><span data-stu-id="d433f-129">runs health diagnostics using Best Practice Analyzer.</span></span><br>`-windowsupdate` <span data-ttu-id="d433f-130">Windows Update でファームウェアまたはドライバーの更新プログラムが見つからないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d433f-130">checks Windows Update for missing firmware or driver updates.</span></span><br>`-warranty` <span data-ttu-id="d433f-131">保証情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="d433f-131">checks warranty information.</span></span> <br><br>| <span data-ttu-id="d433f-132">SDT コンソールアプリ:</span><span class="sxs-lookup"><span data-stu-id="d433f-132">SDT console app:</span></span><br><span data-ttu-id="d433f-133">Microsoft Surface Diagnostics アプリ本体</span><span class="sxs-lookup"><span data-stu-id="d433f-133">Microsoft Surface Diagnostics App Console</span></span><br>[<span data-ttu-id="d433f-134">IT 担当者向け Surface ツール</span><span class="sxs-lookup"><span data-stu-id="d433f-134">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="d433f-135">コマンドを使用して Surface 診断ツールキットを実行する</span><span class="sxs-lookup"><span data-stu-id="d433f-135">Run Surface Diagnostic Toolkit using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <span data-ttu-id="d433f-136">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="d433f-136">Supported devices</span></span> 

<span data-ttu-id="d433f-137">一般法人向けの SDT は、次のような、Surface 3 以降のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d433f-137">SDT for Business is supported on Surface 3 and later devices, including:</span></span>

- <span data-ttu-id="d433f-138">Surface のノート Pc の移動</span><span class="sxs-lookup"><span data-stu-id="d433f-138">Surface Laptop Go</span></span>
- <span data-ttu-id="d433f-139">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="d433f-139">Surface Book 3</span></span>
- <span data-ttu-id="d433f-140">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="d433f-140">Surface Go 2</span></span>
- <span data-ttu-id="d433f-141">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="d433f-141">Surface Pro X</span></span>
- <span data-ttu-id="d433f-142">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="d433f-142">Surface Pro 7</span></span>
- <span data-ttu-id="d433f-143">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="d433f-143">Surface Laptop 3</span></span>
- <span data-ttu-id="d433f-144">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="d433f-144">Surface Pro 6</span></span>
- <span data-ttu-id="d433f-145">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="d433f-145">Surface Laptop 2</span></span>
- <span data-ttu-id="d433f-146">Surface Go</span><span class="sxs-lookup"><span data-stu-id="d433f-146">Surface Go</span></span>
- <span data-ttu-id="d433f-147">Surface Go LTE</span><span class="sxs-lookup"><span data-stu-id="d433f-147">Surface Go with LTE</span></span>
- <span data-ttu-id="d433f-148">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="d433f-148">Surface Book 2</span></span>
- <span data-ttu-id="d433f-149">Surface Pro LTE Advanced (モデル 1807)</span><span class="sxs-lookup"><span data-stu-id="d433f-149">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="d433f-150">Surface Pro (モデル 1796)</span><span class="sxs-lookup"><span data-stu-id="d433f-150">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="d433f-151">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="d433f-151">Surface Laptop</span></span>
- <span data-ttu-id="d433f-152">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="d433f-152">Surface Studio</span></span>
- <span data-ttu-id="d433f-153">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="d433f-153">Surface Studio 2</span></span>
- <span data-ttu-id="d433f-154">Surface Book</span><span class="sxs-lookup"><span data-stu-id="d433f-154">Surface Book</span></span>
- <span data-ttu-id="d433f-155">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="d433f-155">Surface Pro 4</span></span>
- <span data-ttu-id="d433f-156">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="d433f-156">Surface 3 LTE</span></span>
- <span data-ttu-id="d433f-157">Surface 3</span><span class="sxs-lookup"><span data-stu-id="d433f-157">Surface 3</span></span>
- <span data-ttu-id="d433f-158">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="d433f-158">Surface Pro 3</span></span>

## <span data-ttu-id="d433f-159">一般法人向け Surface 診断ツールキットをインストールする</span><span class="sxs-lookup"><span data-stu-id="d433f-159">Installing Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="d433f-160">組織内のユーザーに配布できる SDT パッケージを作成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d433f-160">To create an SDT package that you can distribute to users in your organization:</span></span>

1. <span data-ttu-id="d433f-161">管理者アカウントを使用して Surface デバイスにサインインします。</span><span class="sxs-lookup"><span data-stu-id="d433f-161">Sign in to your Surface device using the Administrator account.</span></span>
2. <span data-ttu-id="d433f-162">[ [Surface Tools FOR IT] のダウンロードページ](https://www.microsoft.com/download/details.aspx?id=46703) から SDT Windows Installer パッケージ (.msi) をダウンロードして、デスクトップなどの surface デバイス上の希望する場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="d433f-162">Download SDT Windows Installer Package (.msi) from the [Surface Tools for IT download page](https://www.microsoft.com/download/details.aspx?id=46703) and copy it to a preferred location on your Surface device, such as Desktop.</span></span>
3. <span data-ttu-id="d433f-163">図1に示すように、SDT セットアップウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d433f-163">The SDT setup wizard appears, as shown in figure 1.</span></span> <span data-ttu-id="d433f-164">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d433f-164">Click **Next**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="d433f-165">セットアップウィザードが表示されない場合は、コンピューターの管理者アカウントにサインインしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d433f-165">If the setup wizard does not appear, ensure that you are signed into the Administrator account on your computer.</span></span> 

    ![Surface 診断ツールキットのセットアップウィザードへようこそ](images/sdt-1.png)

    *<span data-ttu-id="d433f-167">図 1. </span><span class="sxs-lookup"><span data-stu-id="d433f-167">Figure 1.</span></span> <span data-ttu-id="d433f-168">Surface 診断ツールキットのセットアップウィザード</span><span class="sxs-lookup"><span data-stu-id="d433f-168">Surface Diagnostic Toolkit setup wizard</span></span>*

4. <span data-ttu-id="d433f-169">SDT セットアップウィザードが表示されたら、[ **次へ**] をクリックし、エンドユーザーライセンス契約に同意します (EULA)</span><span class="sxs-lookup"><span data-stu-id="d433f-169">When the SDT setup wizard appears, click **Next**, accept the End User License Agreement (EULA)</span></span>

5. <span data-ttu-id="d433f-170">[インストールオプション] 画面で、必要に応じて既定のインストール場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="d433f-170">On the Install Options screen, change the default install location if desired.</span></span> 
6. <span data-ttu-id="d433f-171">[セットアップの種類] で、[ **詳細設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d433f-171">Under Setup Type, select **Advanced**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="d433f-172">[標準] オプションを使うと、ユーザーは管理者アカウントを使用してデバイスにサインインしていることを提供して、Surface デバイスで診断ツールを直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="d433f-172">The standard option allows users to run the diagnostic tool directly on their Surface device provided they are signed into their device using an Administrator account.</span></span> 
    
     ![インストールオプション: Advanced](images/sdt-install.png)

7. <span data-ttu-id="d433f-174">[ **次へ** ] をクリックし、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d433f-174">Click **Next** and then click **Install**.</span></span> 

## <span data-ttu-id="d433f-175">コマンドラインを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="d433f-175">Installing using the command line</span></span>
<span data-ttu-id="d433f-176">必要に応じて、コマンドプロンプトで SDT をインストールし、ユーザー設定のフラグを設定して、ツールを管理モードでインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-176">If desired, you can install SDT at a command prompt and set a custom flag to install the tool in admin mode.</span></span> <span data-ttu-id="d433f-177">SDT には、次のインストールオプションフラグが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d433f-177">SDT contains the following install option flags:</span></span>

- `SENDTELEMETRY` <span data-ttu-id="d433f-178">テレメトリデータを Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="d433f-178">sends telemetry data to Microsoft.</span></span> <span data-ttu-id="d433f-179">このフラグは、 `0` 無効または有効に受け入れ `1` ます。</span><span class="sxs-lookup"><span data-stu-id="d433f-179">The flag accepts `0` for disabled or `1` for enabled.</span></span> <span data-ttu-id="d433f-180">既定値は、 `1` テレメトリを送信することです。</span><span class="sxs-lookup"><span data-stu-id="d433f-180">The default value is `1` to send telemetry.</span></span>
- `ADMINMODE` <span data-ttu-id="d433f-181">管理者モードでインストールするツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="d433f-181">configures the tool to be installed in admin mode.</span></span> <span data-ttu-id="d433f-182">このフラグは、 `0` クライアントモードまたは `1` IT 管理者モードを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d433f-182">The flag accepts `0` for client mode or `1` for IT Administrator mode.</span></span> <span data-ttu-id="d433f-183">既定値は、`0` です。</span><span class="sxs-lookup"><span data-stu-id="d433f-183">The default value is `0`.</span></span>

### <span data-ttu-id="d433f-184">コマンドラインから SDT をインストールするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d433f-184">To install SDT from the command line:</span></span>

1. <span data-ttu-id="d433f-185">コマンドプロンプトを開き、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d433f-185">Open a command prompt and enter:</span></span>

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **<span data-ttu-id="d433f-186">例:</span><span class="sxs-lookup"><span data-stu-id="d433f-186">Example:</span></span>**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## <span data-ttu-id="d433f-187">Surface デバイスで SDT を検索する</span><span class="sxs-lookup"><span data-stu-id="d433f-187">Locating SDT on your Surface device</span></span>

<span data-ttu-id="d433f-188">SDT と SDT アプリ本体は両方ともインストールされてい `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` ます。</span><span class="sxs-lookup"><span data-stu-id="d433f-188">Both SDT and the SDT app console are installed at `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business`.</span></span>

<span data-ttu-id="d433f-189">(図2のように)、SDT には .exe ファイルのほかに、JSON ファイルと admin.dll ファイル (modules\admin.dll) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d433f-189">In addition to the .exe file, SDT installs a JSON file and an admin.dll file (modules\admin.dll), as shown in figure 2.</span></span>

![ファイルエクスプローラーでインストールされた SDT ファイルのリスト](images/sdt-2.png)

*<span data-ttu-id="d433f-191">図 2. </span><span class="sxs-lookup"><span data-stu-id="d433f-191">Figure 2.</span></span> <span data-ttu-id="d433f-192">SDT によってインストールされたファイル</span><span class="sxs-lookup"><span data-stu-id="d433f-192">Files installed by SDT</span></span>*

<span id="create-custom-sdt" />

## <span data-ttu-id="d433f-193">配布用の SDT パッケージを準備する</span><span class="sxs-lookup"><span data-stu-id="d433f-193">Preparing the SDT package for distribution</span></span>

<span data-ttu-id="d433f-194">カスタムパッケージを作成することで、特定の既知の問題にツールをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-194">Creating a custom package allows you to target the tool to specific known issues.</span></span>

1. <span data-ttu-id="d433f-195">[ **Start > Run**] をクリックし、 **surface** と入力して、[ **surface Diagnostic Toolkit for Business**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d433f-195">Click **Start > Run**, enter **Surface** and then click **Surface Diagnostic Toolkit for Business**.</span></span> 
2. <span data-ttu-id="d433f-196">ツールが開いたら、図3に示すように、[ **カスタムパッケージの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d433f-196">When the tool opens, click **Create Custom Package**, as shown in figure 3.</span></span>

    ![[カスタムパッケージの作成] オプション](images/sdt-3.png)

    *<span data-ttu-id="d433f-198">図 3. </span><span class="sxs-lookup"><span data-stu-id="d433f-198">Figure 3.</span></span> <span data-ttu-id="d433f-199">カスタムパッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="d433f-199">Create custom package</span></span>*

### <span data-ttu-id="d433f-200">言語とテレメトリの設定</span><span class="sxs-lookup"><span data-stu-id="d433f-200">Language and telemetry settings</span></span>

  <span data-ttu-id="d433f-201">パッケージを作成するときに、言語設定を選択したり、テレメトリ情報を Microsoft に送信しないようにしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-201">When creating a package, you can select language settings or opt out of sending telemetry information to Microsoft.</span></span> <span data-ttu-id="d433f-202">既定では、SDT は microsoft のプライバシーに関する [声明](https://privacy.microsoft.com/privacystatement)に基づいてアプリケーションを改善するために使用されるテレメトリを microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="d433f-202">By default, SDT sends telemetry to Microsoft that is used to improve the application in accordance with the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).</span></span> <span data-ttu-id="d433f-203">拒否する場合は、以下に示すように、カスタムパッケージを作成するときにチェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d433f-203">If you wish to decline, clear the check box when creating a custom package, as shown below.</span></span> <span data-ttu-id="d433f-204">または、SDT のセットアップ中に、[**インストールオプション**] ページの [**テレメトリを Microsoft に送信する**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d433f-204">Or clear the **Send telemetry to Microsoft** check box on the **Install Options** page during SDT Setup.</span></span> 

>[!NOTE]
><span data-ttu-id="d433f-205">この設定は、Windows Update とソフトウェアの修復などのインターネット接続を必要とするテストや修復を実行しているとき、またはアプリツールバーで [スマイル] または [Frown] ボタンを使用してフィードバックを提供するときに、Microsoft サーバーに自動的に保存される最小のテレメトリには影響しません。</span><span class="sxs-lookup"><span data-stu-id="d433f-205">This setting does not affect the minimal telemetry automatically stored on Microsoft servers when running tests and repairs that require an Internet connection, such as Windows Update and Software repair, or providing feedback using the Smile or Frown buttons in the app toolbar.</span></span> 


![言語とテレメトリの設定を選ぶ](images/sdt-4.png)

*<span data-ttu-id="d433f-207">図 4: </span><span class="sxs-lookup"><span data-stu-id="d433f-207">Figure 4.</span></span> <span data-ttu-id="d433f-208">言語とテレメトリの設定を選ぶ</span><span class="sxs-lookup"><span data-stu-id="d433f-208">Select language and telemetry settings</span></span>*


### <span data-ttu-id="d433f-209">Windows Update ページ</span><span class="sxs-lookup"><span data-stu-id="d433f-209">Windows Update page</span></span>

<span data-ttu-id="d433f-210">組織に適したオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d433f-210">Select the option appropriate for your organization.</span></span> <span data-ttu-id="d433f-211">通常、複数のユーザーがいる組織では、通常、Windows Server Update Services (WSUS) 経由で更新プログラムを受信することを選択します (図 5)。</span><span class="sxs-lookup"><span data-stu-id="d433f-211">Most organizations with multiple users will typically select to receive updates via Windows Server Update Services (WSUS), as shown in figure 5.</span></span> <span data-ttu-id="d433f-212">ローカルの Windows Update パッケージまたは WSUS を使用している場合は、必要に応じてパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d433f-212">If using local Windows Update packages or WSUS, enter the path as appropriate.</span></span> 

![[Windows Update] オプションを選ぶ](images/sdt-5.png)

*<span data-ttu-id="d433f-214">図 5: </span><span class="sxs-lookup"><span data-stu-id="d433f-214">Figure 5.</span></span> <span data-ttu-id="d433f-215">[Windows Update] オプション</span><span class="sxs-lookup"><span data-stu-id="d433f-215">Windows Update option</span></span>*

### <span data-ttu-id="d433f-216">ソフトウェア修復ページ</span><span class="sxs-lookup"><span data-stu-id="d433f-216">Software repair page</span></span>

<span data-ttu-id="d433f-217">これにより、ソフトウェア修復の更新プログラムを実行するためのオプションを選択または削除することができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-217">This allows you to select or remove the option to run software repair updates.</span></span> 

![ソフトウェア修復オプションを選ぶ](images/sdt-6.png)

*<span data-ttu-id="d433f-219">図 6. </span><span class="sxs-lookup"><span data-stu-id="d433f-219">Figure 6.</span></span> <span data-ttu-id="d433f-220">ソフトウェア修復オプション</span><span class="sxs-lookup"><span data-stu-id="d433f-220">Software repair option</span></span>*

### <span data-ttu-id="d433f-221">ログの収集とパッケージの保存ページ</span><span class="sxs-lookup"><span data-stu-id="d433f-221">Collecting logs and saving package page</span></span>

<span data-ttu-id="d433f-222">アプリケーション、ドライバー、ハードウェア、オペレーティングシステム全体でさまざまなログを実行することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d433f-222">You can select to run a wide range of logs across applications, drivers, hardware, and the operating system.</span></span> <span data-ttu-id="d433f-223">適切な領域をクリックして、使用可能なログのメニューから選択します。</span><span class="sxs-lookup"><span data-stu-id="d433f-223">Click the appropriate area and select from the menu of available logs.</span></span> <span data-ttu-id="d433f-224">その後、ユーザーがアクセスできるソフトウェアの配布ポイントまたは同等の場所にパッケージを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-224">You can then save the package to a software distribution point or equivalent location that users can access.</span></span> 

![ログオプションを選択する](images/sdt-7.png)

*<span data-ttu-id="d433f-226">図 7.</span><span class="sxs-lookup"><span data-stu-id="d433f-226">Figure 7.</span></span> <span data-ttu-id="d433f-227">ログオプションとパッケージの保存</span><span class="sxs-lookup"><span data-stu-id="d433f-227">Log option and save package</span></span>*

## <span data-ttu-id="d433f-228">次のステップ</span><span class="sxs-lookup"><span data-stu-id="d433f-228">Next steps</span></span>

- [<span data-ttu-id="d433f-229">ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する</span><span class="sxs-lookup"><span data-stu-id="d433f-229">Use Surface Diagnostic Toolkit for Business in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
- [<span data-ttu-id="d433f-230">コマンドを使用して一般法人向け Surface 診断ツールキットを使用する</span><span class="sxs-lookup"><span data-stu-id="d433f-230">Use Surface Diagnostic Toolkit for Business using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <span data-ttu-id="d433f-231">変更と更新</span><span class="sxs-lookup"><span data-stu-id="d433f-231">Changes and updates</span></span>

### <span data-ttu-id="d433f-232">バージョン2.124.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-232">Version 2.124.139.0</span></span>

<span data-ttu-id="d433f-233">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-233">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="d433f-234">シームレスに統合されたサポート</span><span class="sxs-lookup"><span data-stu-id="d433f-234">Seamless integrated support</span></span>
- <span data-ttu-id="d433f-235">すべてのテスト結果を保存する</span><span class="sxs-lookup"><span data-stu-id="d433f-235">Save all test results</span></span>
- <span data-ttu-id="d433f-236">画像がカスタム作成されているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="d433f-236">Check if the image is custom created</span></span>
- <span data-ttu-id="d433f-237">デバイスマネージャーからの警告を含める</span><span class="sxs-lookup"><span data-stu-id="d433f-237">Include warnings from device manager</span></span>
- <span data-ttu-id="d433f-238">Dock ファームウェアバージョン</span><span class="sxs-lookup"><span data-stu-id="d433f-238">Dock firmware version</span></span>
- <span data-ttu-id="d433f-239">記憶域テストでの潜在的な障害としてのドライブへのフラグ設定</span><span class="sxs-lookup"><span data-stu-id="d433f-239">Flag drives as potential failures in storage test</span></span>
- <span data-ttu-id="d433f-240">ストアリンクの削除</span><span class="sxs-lookup"><span data-stu-id="d433f-240">Remove store link</span></span> 

### <span data-ttu-id="d433f-241">バージョン2.121.139</span><span class="sxs-lookup"><span data-stu-id="d433f-241">Version 2.121.139</span></span>
*<span data-ttu-id="d433f-242">リリース日:31 2020 年7月</span><span class="sxs-lookup"><span data-stu-id="d433f-242">Release date: July 31 2020</span></span>*<br>
<span data-ttu-id="d433f-243">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-243">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="d433f-244">シームレスなサポートエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="d433f-244">Seamless support experience</span></span>
- <span data-ttu-id="d433f-245">バグ修正</span><span class="sxs-lookup"><span data-stu-id="d433f-245">Bug fixes</span></span>

### <span data-ttu-id="d433f-246">バージョン2.94.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-246">Version 2.94.139.0</span></span>
*<span data-ttu-id="d433f-247">リリース日: 2020 年5月11日</span><span class="sxs-lookup"><span data-stu-id="d433f-247">Release date: May 11, 2020</span></span>*<br>
<span data-ttu-id="d433f-248">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-248">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="d433f-249">ハードウェアチェックを実行するために Windows Update をスキップする機能。</span><span class="sxs-lookup"><span data-stu-id="d433f-249">Ability to skip Windows Update to perform hardware check.</span></span>
- <span data-ttu-id="d433f-250">最新バージョンの更新に関する通知を受信する機能</span><span class="sxs-lookup"><span data-stu-id="d433f-250">Ability to receive notifications for about the latest version update</span></span>
- <span data-ttu-id="d433f-251">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="d433f-251">Surface Go 2</span></span>
- <span data-ttu-id="d433f-252">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="d433f-252">Surface Book 3</span></span>
- <span data-ttu-id="d433f-253">進行状況インジケーターを表示する</span><span class="sxs-lookup"><span data-stu-id="d433f-253">Show progress indicator</span></span>


### <span data-ttu-id="d433f-254">バージョン2.43.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-254">Version 2.43.139.0</span></span>
*<span data-ttu-id="d433f-255">リリース日: 2019 年10月21日</span><span class="sxs-lookup"><span data-stu-id="d433f-255">Release date: October 21, 2019</span></span>*<br>
<span data-ttu-id="d433f-256">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-256">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="d433f-257">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="d433f-257">Surface Pro 7</span></span>
- <span data-ttu-id="d433f-258">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="d433f-258">Surface Laptop 3</span></span>

### <span data-ttu-id="d433f-259">バージョン2.42.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-259">Version 2.42.139.0</span></span>
*<span data-ttu-id="d433f-260">リリース日: 2019 年9月24日</span><span class="sxs-lookup"><span data-stu-id="d433f-260">Release date: September 24, 2019</span></span>*<br>
<span data-ttu-id="d433f-261">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-261">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="d433f-262">ハードウェアレポートをダウンロードする機能。</span><span class="sxs-lookup"><span data-stu-id="d433f-262">Ability to download hardware reports.</span></span>
- <span data-ttu-id="d433f-263">ツールから直接 Microsoft サポートに問い合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d433f-263">Ability to contact Microsoft Support directly from the tool.</span></span> <br>

### <span data-ttu-id="d433f-264">バージョン2.41.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-264">Version 2.41.139.0</span></span>
*<span data-ttu-id="d433f-265">リリース日: 2019 年6月24日</span><span class="sxs-lookup"><span data-stu-id="d433f-265">Release date: June 24, 2019</span></span>*<br>
<span data-ttu-id="d433f-266">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-266">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="d433f-267">ログとレポートに含まれるドライバーのバージョン情報。</span><span class="sxs-lookup"><span data-stu-id="d433f-267">Driver version information included in logs and report.</span></span>
- <span data-ttu-id="d433f-268">アプリについてのフィードバックを提供する機能。</span><span class="sxs-lookup"><span data-stu-id="d433f-268">Ability to provide feedback about the app.</span></span><br>


### <span data-ttu-id="d433f-269">バージョン2.36.139.0</span><span class="sxs-lookup"><span data-stu-id="d433f-269">Version 2.36.139.0</span></span>
*<span data-ttu-id="d433f-270">リリース日: 2019 年4月26日</span><span class="sxs-lookup"><span data-stu-id="d433f-270">Release date: April 26, 2019</span></span>*<br>
<span data-ttu-id="d433f-271">このバージョンの Surface 診断ツールキットでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d433f-271">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="d433f-272">コマンドラインの構成を必要とせずに、インストーラ UI を通じて管理機能のロックを解除する詳細なセットアップオプション。</span><span class="sxs-lookup"><span data-stu-id="d433f-272">Advanced Setup option to unlock admin capabilities through the installer UI, without requiring command line configuration.</span></span>
- <span data-ttu-id="d433f-273">ユーザー補助機能の改善。</span><span class="sxs-lookup"><span data-stu-id="d433f-273">Accessibility improvements.</span></span>
- <span data-ttu-id="d433f-274">サーフェスの明るさコントロールの設定がログに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d433f-274">Surface brightness control settings included in logs.</span></span>
- <span data-ttu-id="d433f-275">レポートジェネレーターの外部モニター互換性サポートリンク。</span><span class="sxs-lookup"><span data-stu-id="d433f-275">External monitor compatibility support link in report generator.</span></span>
