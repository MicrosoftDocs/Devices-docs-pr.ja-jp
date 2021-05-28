---
title: ビジネス向け Surface 診断ツールキットを展開する
description: このトピックでは、Surface Diagnostic Toolkit for Business の使い方について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 01/15/2021
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 227463e484a6f3b933fc1118d9dec058f93074a8
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271581"
---
# <span data-ttu-id="9b927-103">ビジネス向け Surface 診断ツールキットを展開する</span><span class="sxs-lookup"><span data-stu-id="9b927-103">Deploy Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="9b927-104">Microsoft Surface Diagnostic Toolkit for Business (SDT) を使用すると、IT 管理者は Surface デバイスに関するハードウェア、ソフトウェア、ファームウェアの問題をすばやく調査、トラブルシューティング、解決できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-104">The Microsoft Surface Diagnostic Toolkit for Business (SDT) enables IT administrators to quickly investigate, troubleshoot, and resolve hardware, software, and firmware issues with Surface devices.</span></span> <span data-ttu-id="9b927-105">デバイスの正常性に関する分析情報や問題を解決するためのガイダンスを取得する以外に、さまざまな診断テストとソフトウェア修復を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-105">You can run a range of diagnostic tests and software repairs in addition to obtaining device health insights and guidance for resolving issues.</span></span> 

<span data-ttu-id="9b927-106">具体的には、SDT for Business を使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-106">Specifically, SDT for Business enables you to:</span></span>

- [<span data-ttu-id="9b927-107">パッケージをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="9b927-107">Customize the package.</span></span>](#preparing-the-sdt-package-for-distribution)
- [<span data-ttu-id="9b927-108">コマンドを使ってアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9b927-108">Run the app using commands.</span></span>](surface-diagnostic-toolkit-command-line.md)
- [<span data-ttu-id="9b927-109">複数のハードウェア テストを実行して問題をトラブルシューティングします。</span><span class="sxs-lookup"><span data-stu-id="9b927-109">Run multiple hardware tests to troubleshoot issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [<span data-ttu-id="9b927-110">問題を分析するためのログを生成します。</span><span class="sxs-lookup"><span data-stu-id="9b927-110">Generate logs for analyzing issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [<span data-ttu-id="9b927-111">デバイスと最適な構成を比較して詳細なレポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b927-111">Obtain detailed report comparing device vs optimal configuration.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## <a name="primary-scenarios-and-download-resources"></a><span data-ttu-id="9b927-112">主なシナリオとダウンロード リソース</span><span class="sxs-lookup"><span data-stu-id="9b927-112">Primary scenarios and download resources</span></span> 

<span data-ttu-id="9b927-113">SDT for Business を実行するには、次の表に示すコンポーネントをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9b927-113">To run SDT for Business, download the components listed in the following table.</span></span>


<span data-ttu-id="9b927-114">モード</span><span class="sxs-lookup"><span data-stu-id="9b927-114">Mode</span></span> |  <span data-ttu-id="9b927-115">主なシナリオ</span><span class="sxs-lookup"><span data-stu-id="9b927-115">Primary scenarios</span></span> | <span data-ttu-id="9b927-116">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="9b927-116">Download</span></span> | <span data-ttu-id="9b927-117">詳細情報</span><span class="sxs-lookup"><span data-stu-id="9b927-117">Learn more</span></span>
--- | --- | --- | ---
<span data-ttu-id="9b927-118">デスクトップ モード</span><span class="sxs-lookup"><span data-stu-id="9b927-118">Desktop mode</span></span> |  <span data-ttu-id="9b927-119">ユーザーが Surface デバイスで SDT を実行して問題のトラブルシューティングを行うのを支援します。</span><span class="sxs-lookup"><span data-stu-id="9b927-119">Assist users in running SDT on their Surface devices to troubleshoot issues.</span></span><br><span data-ttu-id="9b927-120">1 つ以上の Surface デバイスに展開するカスタム パッケージを作成すると、ユーザーは特定のログを選択して収集および分析できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-120">Create a custom package to deploy on one or more Surface devices allowing users to select specific logs to collect and analyze.</span></span> | <span data-ttu-id="9b927-121">SDT 配布可能 MSI パッケージ:</span><span class="sxs-lookup"><span data-stu-id="9b927-121">SDT distributable MSI package:</span></span><br><span data-ttu-id="9b927-122">Microsoft Surface Diagnostic Toolkit for Business インストーラー</span><span class="sxs-lookup"><span data-stu-id="9b927-122">Microsoft Surface Diagnostic Toolkit for Business Installer</span></span><br>[<span data-ttu-id="9b927-123">IT 担当者向け Surface ツール</span><span class="sxs-lookup"><span data-stu-id="9b927-123">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="9b927-124">デスクトップ モードで Surface Diagnostic Toolkitを使用する</span><span class="sxs-lookup"><span data-stu-id="9b927-124">Use Surface Diagnostic Toolkit in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
<span data-ttu-id="9b927-125">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="9b927-125">Command line</span></span> |  <span data-ttu-id="9b927-126">Configuration Manager などの標準ツールを使用して、ユーザーの操作なしにリモートで Surface デバイスを直接トラブルシューティングします。</span><span class="sxs-lookup"><span data-stu-id="9b927-126">Directly troubleshoot Surface devices remotely without user interaction, using standard tools such as Configuration Manager.</span></span> <span data-ttu-id="9b927-127">これには、次のコマンドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9b927-127">It includes the following commands:</span></span><br>`-DataCollector` <span data-ttu-id="9b927-128">すべてのログ ファイルを収集します</span><span class="sxs-lookup"><span data-stu-id="9b927-128">collects all log files</span></span><br>`-bpa` <span data-ttu-id="9b927-129">ベスト プラクティス アナライザーを使用して正常性診断を実行します。</span><span class="sxs-lookup"><span data-stu-id="9b927-129">runs health diagnostics using Best Practice Analyzer.</span></span><br>`-windowsupdate` <span data-ttu-id="9b927-130">ファームウェアまたはドライバーの更新プログラムが見つからないか Windows Update をチェックします。</span><span class="sxs-lookup"><span data-stu-id="9b927-130">checks Windows Update for missing firmware or driver updates.</span></span><br>`-warranty` <span data-ttu-id="9b927-131">保証情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="9b927-131">checks warranty information.</span></span> <br><br>| <span data-ttu-id="9b927-132">SDT コンソール アプリ:</span><span class="sxs-lookup"><span data-stu-id="9b927-132">SDT console app:</span></span><br><span data-ttu-id="9b927-133">Microsoft Surface Diagnostics アプリ コンソール</span><span class="sxs-lookup"><span data-stu-id="9b927-133">Microsoft Surface Diagnostics App Console</span></span><br>[<span data-ttu-id="9b927-134">IT 担当者向け Surface ツール</span><span class="sxs-lookup"><span data-stu-id="9b927-134">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="9b927-135">コマンドを使用して Surface 診断Toolkitを実行する</span><span class="sxs-lookup"><span data-stu-id="9b927-135">Run Surface Diagnostic Toolkit using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <a name="supported-devices-"></a><span data-ttu-id="9b927-136">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="9b927-136">Supported devices</span></span> 

<span data-ttu-id="9b927-137">SDT for Business は、次の Surface 3 以降のデバイスでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9b927-137">SDT for Business is supported on Surface 3 and later devices, including:</span></span>

- <span data-ttu-id="9b927-138">Surface Book - すべての世代</span><span class="sxs-lookup"><span data-stu-id="9b927-138">Surface Book - all generations</span></span>
- <span data-ttu-id="9b927-139">Surface Go - すべての世代</span><span class="sxs-lookup"><span data-stu-id="9b927-139">Surface Go - all generations</span></span>
- <span data-ttu-id="9b927-140">Surface Laptop - すべての世代</span><span class="sxs-lookup"><span data-stu-id="9b927-140">Surface Laptop - all generations</span></span>
- <span data-ttu-id="9b927-141">Surface Pro 3 以降</span><span class="sxs-lookup"><span data-stu-id="9b927-141">Surface Pro 3 and later</span></span>
- <span data-ttu-id="9b927-142">Surface Pro X - すべての世代</span><span class="sxs-lookup"><span data-stu-id="9b927-142">Surface Pro X - all generations</span></span>
- <span data-ttu-id="9b927-143">Surface Studio - すべての世代</span><span class="sxs-lookup"><span data-stu-id="9b927-143">Surface Studio - all generations</span></span>
- <span data-ttu-id="9b927-144">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="9b927-144">Surface 3 LTE</span></span>
- <span data-ttu-id="9b927-145">Surface 3</span><span class="sxs-lookup"><span data-stu-id="9b927-145">Surface 3</span></span>


## <a name="installing-surface-diagnostic-toolkit-for-business"></a><span data-ttu-id="9b927-146">Surface Diagnostic Toolkit for Business のインストール</span><span class="sxs-lookup"><span data-stu-id="9b927-146">Installing Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="9b927-147">組織内のユーザーに配布できる SDT パッケージを作成するには、</span><span class="sxs-lookup"><span data-stu-id="9b927-147">To create an SDT package that you can distribute to users in your organization:</span></span>

1. <span data-ttu-id="9b927-148">管理者アカウントを使用して Surface デバイスにサインインします。</span><span class="sxs-lookup"><span data-stu-id="9b927-148">Sign in to your Surface device using the Administrator account.</span></span>
2. <span data-ttu-id="9b927-149">IT 向け [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) のダウンロード ページから SDT Windows インストーラー パッケージ (.msi) をダウンロードし、デスクトップなどの Surface デバイスの優先する場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9b927-149">Download SDT Windows Installer Package (.msi) from the [Surface Tools for IT download page](https://www.microsoft.com/download/details.aspx?id=46703) and copy it to a preferred location on your Surface device, such as Desktop.</span></span>
3. <span data-ttu-id="9b927-150">図 1 に示すように、SDT セットアップ ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b927-150">The SDT setup wizard appears, as shown in figure 1.</span></span> <span data-ttu-id="9b927-151">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b927-151">Click **Next**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="9b927-152">セットアップ ウィザードが表示されない場合は、コンピューターの Administrator アカウントにサインインしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b927-152">If the setup wizard does not appear, ensure that you are signed into the Administrator account on your computer.</span></span> 

    ![Surface Diagnostic Toolkit セットアップ ウィザードへようこそ](images/sdt-1.png)

    *<span data-ttu-id="9b927-154">図 1. </span><span class="sxs-lookup"><span data-stu-id="9b927-154">Figure 1.</span></span> <span data-ttu-id="9b927-155">Surface Diagnostic Toolkit セットアップ ウィザード</span><span class="sxs-lookup"><span data-stu-id="9b927-155">Surface Diagnostic Toolkit setup wizard</span></span>*

4. <span data-ttu-id="9b927-156">SDT セットアップ ウィザードが表示されたら、[次へ] **をクリックし**、使用許諾契約書 (EULA) に同意します。</span><span class="sxs-lookup"><span data-stu-id="9b927-156">When the SDT setup wizard appears, click **Next**, accept the End User License Agreement (EULA)</span></span>

5. <span data-ttu-id="9b927-157">[インストール オプション] 画面で、必要に応じて既定のインストール場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="9b927-157">On the Install Options screen, change the default install location if desired.</span></span> 
6. <span data-ttu-id="9b927-158">[セットアップの種類] で、[詳細設定] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="9b927-158">Under Setup Type, select **Advanced**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="9b927-159">標準オプションでは、管理者アカウントを使用してデバイスにサインインしている場合、ユーザーは Surface デバイスで直接診断ツールを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-159">The standard option allows users to run the diagnostic tool directly on their Surface device provided they are signed into their device using an Administrator account.</span></span> 
    
     ![インストール オプション: 詳細](images/sdt-install.png)

7. <span data-ttu-id="9b927-161">[次 **へ] をクリック** し、[インストール] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="9b927-161">Click **Next** and then click **Install**.</span></span> 

## <a name="installing-using-the-command-line"></a><span data-ttu-id="9b927-162">コマンド ラインを使用したインストール</span><span class="sxs-lookup"><span data-stu-id="9b927-162">Installing using the command line</span></span>
<span data-ttu-id="9b927-163">必要に応じて、コマンド プロンプトで SDT をインストールし、カスタム フラグを設定して管理モードでツールをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9b927-163">If desired, you can install SDT at a command prompt and set a custom flag to install the tool in admin mode.</span></span> <span data-ttu-id="9b927-164">SDT には、次のインストール オプション フラグが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9b927-164">SDT contains the following install option flags:</span></span>

- `SENDTELEMETRY` <span data-ttu-id="9b927-165">利用統計情報を Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="9b927-165">sends telemetry data to Microsoft.</span></span> <span data-ttu-id="9b927-166">フラグは無効または `0` 有効を `1` 受け入れる。</span><span class="sxs-lookup"><span data-stu-id="9b927-166">The flag accepts `0` for disabled or `1` for enabled.</span></span> <span data-ttu-id="9b927-167">既定値は利用統計情報 `1` を送信します。</span><span class="sxs-lookup"><span data-stu-id="9b927-167">The default value is `1` to send telemetry.</span></span>
- `ADMINMODE` <span data-ttu-id="9b927-168">管理モードでインストールするツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="9b927-168">configures the tool to be installed in admin mode.</span></span> <span data-ttu-id="9b927-169">このフラグは、クライアント `0` モードまたは `1` IT 管理者モードに対して受け入れ可能です。</span><span class="sxs-lookup"><span data-stu-id="9b927-169">The flag accepts `0` for client mode or `1` for IT Administrator mode.</span></span> <span data-ttu-id="9b927-170">既定値は、`0` です。</span><span class="sxs-lookup"><span data-stu-id="9b927-170">The default value is `0`.</span></span>

### <a name="to-install-sdt-from-the-command-line"></a><span data-ttu-id="9b927-171">コマンド ラインから SDT をインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9b927-171">To install SDT from the command line:</span></span>

1. <span data-ttu-id="9b927-172">コマンド プロンプトを開き、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9b927-172">Open a command prompt and enter:</span></span>

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **<span data-ttu-id="9b927-173">例:</span><span class="sxs-lookup"><span data-stu-id="9b927-173">Example:</span></span>**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## <a name="locating-sdt-on-your-surface-device"></a><span data-ttu-id="9b927-174">Surface デバイスでの SDT の検索</span><span class="sxs-lookup"><span data-stu-id="9b927-174">Locating SDT on your Surface device</span></span>

<span data-ttu-id="9b927-175">SDT と SDT アプリ コンソールの両方がインストールされます `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` 。</span><span class="sxs-lookup"><span data-stu-id="9b927-175">Both SDT and the SDT app console are installed at `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business`.</span></span>

<span data-ttu-id="9b927-176">図 2 に示すように、SDT は .exe ファイルに加えて、JSON ファイルと admin.dll ファイル (modules\admin.dll) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9b927-176">In addition to the .exe file, SDT installs a JSON file and an admin.dll file (modules\admin.dll), as shown in figure 2.</span></span>

![エクスプローラーにインストールされている SDT ファイルの一覧](images/sdt-2.png)

*<span data-ttu-id="9b927-178">図 2. </span><span class="sxs-lookup"><span data-stu-id="9b927-178">Figure 2.</span></span> <span data-ttu-id="9b927-179">SDT によってインストールされるファイル</span><span class="sxs-lookup"><span data-stu-id="9b927-179">Files installed by SDT</span></span>*

## <a name="preparing-the-sdt-package-for-distribution"></a><span data-ttu-id="9b927-180">配布用の SDT パッケージの準備</span><span class="sxs-lookup"><span data-stu-id="9b927-180">Preparing the SDT package for distribution</span></span>

<span data-ttu-id="9b927-181">カスタム パッケージを作成すると、特定の既知の問題をツールのターゲットに設定できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-181">Creating a custom package allows you to target the tool to specific known issues.</span></span>

1. <span data-ttu-id="9b927-182">[ **スタート] ボタン>実行] を**クリックし **、「Surface」** と入力して **、[Surface Diagnostic Toolkit for Business] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="9b927-182">Click **Start > Run**, enter **Surface** and then click **Surface Diagnostic Toolkit for Business**.</span></span> 
2. <span data-ttu-id="9b927-183">ツールが開いたら、図 3 に示 **すように**[カスタム パッケージの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b927-183">When the tool opens, click **Create Custom Package**, as shown in figure 3.</span></span>

    ![カスタム パッケージ の作成オプション](images/sdt-3.png)

    *<span data-ttu-id="9b927-185">図 3. </span><span class="sxs-lookup"><span data-stu-id="9b927-185">Figure 3.</span></span> <span data-ttu-id="9b927-186">カスタム パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="9b927-186">Create custom package</span></span>*

### <a name="language-and-telemetry-settings"></a><span data-ttu-id="9b927-187">言語と利用統計情報の設定</span><span class="sxs-lookup"><span data-stu-id="9b927-187">Language and telemetry settings</span></span>

  <span data-ttu-id="9b927-188">パッケージを作成する場合は、言語設定を選択するか、利用統計情報の Microsoft への送信をオプトアウトできます。</span><span class="sxs-lookup"><span data-stu-id="9b927-188">When creating a package, you can select language settings or opt out of sending telemetry information to Microsoft.</span></span> <span data-ttu-id="9b927-189">既定では、SDT は、Microsoft のプライバシーに関する声明に従って、アプリケーションの改善に使用される利用統計情報を Microsoft に [送信します](https://privacy.microsoft.com/privacystatement)。</span><span class="sxs-lookup"><span data-stu-id="9b927-189">By default, SDT sends telemetry to Microsoft that is used to improve the application in accordance with the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).</span></span> <span data-ttu-id="9b927-190">拒否する場合は、次に示すように、カスタム パッケージを作成するときにチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="9b927-190">If you wish to decline, clear the check box when creating a custom package, as shown below.</span></span> <span data-ttu-id="9b927-191">または、SDT セットアップ中に [インストール\*\*\*\* オプション] ページの **[Microsoft**に利用統計情報を送信する] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="9b927-191">Or clear the **Send telemetry to Microsoft** check box on the **Install Options** page during SDT Setup.</span></span> 

>[!NOTE]
><span data-ttu-id="9b927-192">この設定は、Windows Update やソフトウェアの修復など、インターネット接続が必要なテストと修復を実行する場合や、アプリ ツール バーの [にこぼれ] ボタンまたは [Frown] ボタンを使用してフィードバックを提供する場合に、Microsoft サーバーに自動的に保存される最小限の利用統計情報には影響しません。</span><span class="sxs-lookup"><span data-stu-id="9b927-192">This setting does not affect the minimal telemetry automatically stored on Microsoft servers when running tests and repairs that require an Internet connection, such as Windows Update and Software repair, or providing feedback using the Smile or Frown buttons in the app toolbar.</span></span> 


![言語と利用統計情報の設定を選択する](images/sdt-4.png)

*<span data-ttu-id="9b927-194">図 4: </span><span class="sxs-lookup"><span data-stu-id="9b927-194">Figure 4.</span></span> <span data-ttu-id="9b927-195">言語と利用統計情報の設定を選択する</span><span class="sxs-lookup"><span data-stu-id="9b927-195">Select language and telemetry settings</span></span>*


### <a name="windows-update-page"></a><span data-ttu-id="9b927-196">Windows Update ページ</span><span class="sxs-lookup"><span data-stu-id="9b927-196">Windows Update page</span></span>

<span data-ttu-id="9b927-197">組織に適したオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b927-197">Select the option appropriate for your organization.</span></span> <span data-ttu-id="9b927-198">図 5 に示すように、複数のユーザーを持つほとんどの組織では、通常、Windows Server Update Services (WSUS) 経由で更新プログラムを受信します。</span><span class="sxs-lookup"><span data-stu-id="9b927-198">Most organizations with multiple users will typically select to receive updates via Windows Server Update Services (WSUS), as shown in figure 5.</span></span> <span data-ttu-id="9b927-199">ローカルの Windows Update パッケージまたは WSUS を使う場合は、必要に応じてパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="9b927-199">If using local Windows Update packages or WSUS, enter the path as appropriate.</span></span> 

![Windows Update オプションの選択](images/sdt-5.png)

*<span data-ttu-id="9b927-201">図 5: </span><span class="sxs-lookup"><span data-stu-id="9b927-201">Figure 5.</span></span> <span data-ttu-id="9b927-202">Windows Update オプション</span><span class="sxs-lookup"><span data-stu-id="9b927-202">Windows Update option</span></span>*

### <a name="software-repair-page"></a><span data-ttu-id="9b927-203">ソフトウェア修復ページ</span><span class="sxs-lookup"><span data-stu-id="9b927-203">Software repair page</span></span>

<span data-ttu-id="9b927-204">これにより、ソフトウェア修復の更新を実行するオプションを選択または削除できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-204">This allows you to select or remove the option to run software repair updates.</span></span> 

![ソフトウェア修復オプションの選択](images/sdt-6.png)

*<span data-ttu-id="9b927-206">図 6. </span><span class="sxs-lookup"><span data-stu-id="9b927-206">Figure 6.</span></span> <span data-ttu-id="9b927-207">ソフトウェア修復オプション</span><span class="sxs-lookup"><span data-stu-id="9b927-207">Software repair option</span></span>*

### <a name="collecting-logs-and-saving-package-page"></a><span data-ttu-id="9b927-208">ログの収集とパッケージ の保存ページ</span><span class="sxs-lookup"><span data-stu-id="9b927-208">Collecting logs and saving package page</span></span>

<span data-ttu-id="9b927-209">さまざまなアプリケーション、ドライバー、ハードウェア、オペレーティング システムでさまざまなログを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-209">You can select to run a wide range of logs across applications, drivers, hardware, and the operating system.</span></span> <span data-ttu-id="9b927-210">該当する領域をクリックし、使用可能なログのメニューから選択します。</span><span class="sxs-lookup"><span data-stu-id="9b927-210">Click the appropriate area and select from the menu of available logs.</span></span> <span data-ttu-id="9b927-211">その後、ユーザーがアクセスできるソフトウェア配布ポイントまたは同等の場所にパッケージを保存できます。</span><span class="sxs-lookup"><span data-stu-id="9b927-211">You can then save the package to a software distribution point or equivalent location that users can access.</span></span> 

![ログ オプションの選択](images/sdt-7.png)

*<span data-ttu-id="9b927-213">図 7.</span><span class="sxs-lookup"><span data-stu-id="9b927-213">Figure 7.</span></span> <span data-ttu-id="9b927-214">ログ オプションとパッケージの保存</span><span class="sxs-lookup"><span data-stu-id="9b927-214">Log option and save package</span></span>*

## <a name="next-steps"></a><span data-ttu-id="9b927-215">次のステップ</span><span class="sxs-lookup"><span data-stu-id="9b927-215">Next steps</span></span>

- [<span data-ttu-id="9b927-216">ビジネス向け Surface 診断ツールキットをデスクトップ モードで使用する</span><span class="sxs-lookup"><span data-stu-id="9b927-216">Use Surface Diagnostic Toolkit for Business in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
- [<span data-ttu-id="9b927-217">コマンドを使用して Surface Diagnostic Toolkit for Business を使用する</span><span class="sxs-lookup"><span data-stu-id="9b927-217">Use Surface Diagnostic Toolkit for Business using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <a name="changes-and-updates"></a><span data-ttu-id="9b927-218">変更と更新</span><span class="sxs-lookup"><span data-stu-id="9b927-218">Changes and updates</span></span>

### <a name="version-2.131.139.0"></a><span data-ttu-id="9b927-219">バージョン 2.131.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-219">Version 2.131.139.0</span></span>

<span data-ttu-id="9b927-220">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-220">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="9b927-221">Surface Pro 7+ のサポート</span><span class="sxs-lookup"><span data-stu-id="9b927-221">Support for Surface Pro 7+</span></span>
- <span data-ttu-id="9b927-222">Surface Pro X でのシームレスなサポート エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="9b927-222">Seamless support experience on Surface Pro X</span></span>
- <span data-ttu-id="9b927-223">セキュリティの強化</span><span class="sxs-lookup"><span data-stu-id="9b927-223">Security improvements</span></span>
- <span data-ttu-id="9b927-224">包括的なユーザー エクスペリエンスの向上</span><span class="sxs-lookup"><span data-stu-id="9b927-224">Inclusive user experience improvements</span></span>

### <a name="version-2.124.139.0"></a><span data-ttu-id="9b927-225">バージョン 2.124.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-225">Version 2.124.139.0</span></span>

<span data-ttu-id="9b927-226">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-226">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="9b927-227">シームレスな統合サポート</span><span class="sxs-lookup"><span data-stu-id="9b927-227">Seamless integrated support</span></span>
- <span data-ttu-id="9b927-228">すべてのテスト結果を保存する</span><span class="sxs-lookup"><span data-stu-id="9b927-228">Save all test results</span></span>
- <span data-ttu-id="9b927-229">イメージがカスタム作成されたのか確認する</span><span class="sxs-lookup"><span data-stu-id="9b927-229">Check if the image is custom created</span></span>
- <span data-ttu-id="9b927-230">デバイス マネージャーからの警告を含める</span><span class="sxs-lookup"><span data-stu-id="9b927-230">Include warnings from device manager</span></span>
- <span data-ttu-id="9b927-231">ドックのファームウェアのバージョン</span><span class="sxs-lookup"><span data-stu-id="9b927-231">Dock firmware version</span></span>
- <span data-ttu-id="9b927-232">ストレージ テストで発生する可能性がある障害としてドライブにフラグを設定する</span><span class="sxs-lookup"><span data-stu-id="9b927-232">Flag drives as potential failures in storage test</span></span>
- <span data-ttu-id="9b927-233">ストアリンクを削除する</span><span class="sxs-lookup"><span data-stu-id="9b927-233">Remove store link</span></span> 

### <a name="version-2.121.139"></a><span data-ttu-id="9b927-234">バージョン 2.121.139</span><span class="sxs-lookup"><span data-stu-id="9b927-234">Version 2.121.139</span></span>
*<span data-ttu-id="9b927-235">リリース日: 2020 年 7 月 31 日</span><span class="sxs-lookup"><span data-stu-id="9b927-235">Release date: July 31 2020</span></span>*<br>
<span data-ttu-id="9b927-236">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-236">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="9b927-237">シームレスなサポート エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="9b927-237">Seamless support experience</span></span>
- <span data-ttu-id="9b927-238">バグ修正</span><span class="sxs-lookup"><span data-stu-id="9b927-238">Bug fixes</span></span>

### <a name="version-2.94.139.0"></a><span data-ttu-id="9b927-239">バージョン 2.94.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-239">Version 2.94.139.0</span></span>
*<span data-ttu-id="9b927-240">リリース日: 2020 年 5 月 11 日</span><span class="sxs-lookup"><span data-stu-id="9b927-240">Release date: May 11, 2020</span></span>*<br>
<span data-ttu-id="9b927-241">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-241">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="9b927-242">Windows Update をスキップしてハードウェア チェックを実行する機能。</span><span class="sxs-lookup"><span data-stu-id="9b927-242">Ability to skip Windows Update to perform hardware check.</span></span>
- <span data-ttu-id="9b927-243">最新バージョンの更新に関する通知を受信する機能</span><span class="sxs-lookup"><span data-stu-id="9b927-243">Ability to receive notifications for about the latest version update</span></span>
- <span data-ttu-id="9b927-244">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="9b927-244">Surface Go 2</span></span>
- <span data-ttu-id="9b927-245">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="9b927-245">Surface Book 3</span></span>
- <span data-ttu-id="9b927-246">進行状況インジケーターを表示する</span><span class="sxs-lookup"><span data-stu-id="9b927-246">Show progress indicator</span></span>


### <a name="version-2.43.139.0"></a><span data-ttu-id="9b927-247">バージョン 2.43.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-247">Version 2.43.139.0</span></span>
*<span data-ttu-id="9b927-248">リリース日: 2019 年 10 月 21 日</span><span class="sxs-lookup"><span data-stu-id="9b927-248">Release date: October 21, 2019</span></span>*<br>
<span data-ttu-id="9b927-249">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-249">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="9b927-250">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="9b927-250">Surface Pro 7</span></span>
- <span data-ttu-id="9b927-251">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="9b927-251">Surface Laptop 3</span></span>

### <a name="version-2.42.139.0"></a><span data-ttu-id="9b927-252">バージョン 2.42.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-252">Version 2.42.139.0</span></span>
*<span data-ttu-id="9b927-253">リリース日: 2019 年 9 月 24 日</span><span class="sxs-lookup"><span data-stu-id="9b927-253">Release date: September 24, 2019</span></span>*<br>
<span data-ttu-id="9b927-254">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-254">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="9b927-255">ハードウェア レポートをダウンロードする機能。</span><span class="sxs-lookup"><span data-stu-id="9b927-255">Ability to download hardware reports.</span></span>
- <span data-ttu-id="9b927-256">ツールから直接 Microsoft サポートに問い合わせ可能。</span><span class="sxs-lookup"><span data-stu-id="9b927-256">Ability to contact Microsoft Support directly from the tool.</span></span> <br>

### <a name="version-2.41.139.0"></a><span data-ttu-id="9b927-257">バージョン 2.41.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-257">Version 2.41.139.0</span></span>
*<span data-ttu-id="9b927-258">リリース日: 2019 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="9b927-258">Release date: June 24, 2019</span></span>*<br>
<span data-ttu-id="9b927-259">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-259">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="9b927-260">ログとレポートに含まれるドライバーのバージョン情報。</span><span class="sxs-lookup"><span data-stu-id="9b927-260">Driver version information included in logs and report.</span></span>
- <span data-ttu-id="9b927-261">アプリに関するフィードバックを提供する機能。</span><span class="sxs-lookup"><span data-stu-id="9b927-261">Ability to provide feedback about the app.</span></span><br>


### <a name="version-2.36.139.0"></a><span data-ttu-id="9b927-262">バージョン 2.36.139.0</span><span class="sxs-lookup"><span data-stu-id="9b927-262">Version 2.36.139.0</span></span>
*<span data-ttu-id="9b927-263">リリース日: 2019 年 4 月 26 日</span><span class="sxs-lookup"><span data-stu-id="9b927-263">Release date: April 26, 2019</span></span>*<br>
<span data-ttu-id="9b927-264">このバージョンの Surface Diagnostic Toolkit for Business では、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="9b927-264">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="9b927-265">コマンド ライン構成を必要とせずに、インストーラー UI を使用して管理機能をロック解除するための高度なセットアップ オプション。</span><span class="sxs-lookup"><span data-stu-id="9b927-265">Advanced Setup option to unlock admin capabilities through the installer UI, without requiring command line configuration.</span></span>
- <span data-ttu-id="9b927-266">アクセシビリティの向上。</span><span class="sxs-lookup"><span data-stu-id="9b927-266">Accessibility improvements.</span></span>
- <span data-ttu-id="9b927-267">ログに含まれるサーフェスの明るさの制御設定。</span><span class="sxs-lookup"><span data-stu-id="9b927-267">Surface brightness control settings included in logs.</span></span>
- <span data-ttu-id="9b927-268">レポート ジェネレーターの外部モニター互換性サポート リンク。</span><span class="sxs-lookup"><span data-stu-id="9b927-268">External monitor compatibility support link in report generator.</span></span>
