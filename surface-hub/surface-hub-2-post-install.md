---
title: Surface Hub 2 で Windows 10 Pro または Enterprise を構成する
description: この記事には、パーソナライズされた大画面タッチとペン コンピューターを使用する場合に最適なエクスペリエンスを確保するための推奨事項が含まれています。
keywords: Surface Hub、Windows 10、デスクトップ、インストール、構成
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.collection: M365-modern-desktop
ms.topic: article
ms.date: 12/08/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: 076d29462ffb949492291e120bcdad538f4287ec
ms.sourcegitcommit: e859374f90d640a5cd4be1c8dcc823bcd537ebdc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "11393591"
---
# <a name="configure-windows-10-pro-or-enterprise-on-surface-hub-2"></a><span data-ttu-id="441c1-104">Surface Hub 2 で Windows 10 Pro または Enterprise を構成する</span><span class="sxs-lookup"><span data-stu-id="441c1-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

<span data-ttu-id="441c1-105">Windows 10 Pro または Enterprise への移行のインストール プロセスが完了したら、次の手順を実行して、Surface Hub 2 でアプリと設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-105">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="441c1-106">これらの手順は、このパーソナライズされた大画面タッチとペン コンピューターを使用する場合に最適なエクスペリエンスを確保するためにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-106">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="441c1-107">これらの手順を実行する場合は、有線またはワイヤレスのキーボードとマウスを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="441c1-107">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <a name="configure-system-settings"></a><span data-ttu-id="441c1-108">システム設定の構成</span><span class="sxs-lookup"><span data-stu-id="441c1-108">Configure system settings</span></span>

1. <span data-ttu-id="441c1-109">デバイスに対するローカル管理者特権を持つアカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="441c1-109">Sign in with an account that has local administrator privileges on the device.</span></span>  

    - <span data-ttu-id="441c1-110">Azure ADに参加しているデバイスでは、Azure ADを実行するユーザーがローカル管理者グループに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-110">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="441c1-111">Azure AD管理者と Azure ADデバイス管理者も <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> ローカル管理者です </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-111">Azure AD global administrators and Azure AD devices administrators are <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank">also local administrators</a>.</span></span> 
    
    - <span data-ttu-id="441c1-112">コマンド プロンプトに **「net localgroup administrators」** と入力して、ローカル管理者権限を持つアカウントを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-112">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
    
2. <span data-ttu-id="441c1-113">ユーザー名 **-SHub-Desktop など、表示名を使用してデバイスの名前を変更します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-113">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>

3. <span data-ttu-id="441c1-114">[スタート**設定**  >  **アカウント**  >  **]**  >  **[設定の同期] を選択し**、[**同期設定] をオフ**にします。</span><span class="sxs-lookup"><span data-stu-id="441c1-114">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 

    - <span data-ttu-id="441c1-115">ここで使用する設定は、最高の大画面タッチ エクスペリエンスを有効にすることを目的とするため、他のデバイスを同期したくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-115">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
    
4. <span data-ttu-id="441c1-116">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="441c1-116">Restart the device.</span></span>

## <a name="enable-the-touch-keyboard-and-touchpad"></a><span data-ttu-id="441c1-117">タッチ キーボードとタッチパッドを有効にする</span><span class="sxs-lookup"><span data-stu-id="441c1-117">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="441c1-118">[**設定の開始**デバイスの入力] を選択し、[タブレット モードではないときにタッチ キーボードを表示する] をオンにし、キーボード  >  \*\*\*\*  >  \*\*\*\*  >  \*\*\*\*\*\*が接続されていない場合はオン\*\*にします。</span><span class="sxs-lookup"><span data-stu-id="441c1-118">Select **Start** > **Settings** > **Devices** > **Typing** and turn **Show the touch keyboard when not in tablet mode and there's no keyboard attached** on.</span></span>

2. <span data-ttu-id="441c1-119">タスク バーを長押しまたは右クリックし、[タッチ **キーボード** ボタンの表示] と [タッチパッド ボタンの表示] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-119">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 

    - <span data-ttu-id="441c1-120">タッチ キーボードはユーザーの直接入力に役立ち、仮想タッチパッドは正確な選択、画面のヒントのホバー、または右クリックのタップとホールドの代わりに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="441c1-120">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    
    - <span data-ttu-id="441c1-121">次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="441c1-121">See the following example.</span></span>

      ![タッチ設定](images/touch.png)

3. <span data-ttu-id="441c1-123">タッチ キーボードを QWERTY とフローティングに構成します。</span><span class="sxs-lookup"><span data-stu-id="441c1-123">Configure the touch keyboard to QWERTY and floating.</span></span>

    1. <span data-ttu-id="441c1-124">タスク バーの **[キーボード** ] アイコンを選択して、タッチ キーボードを表示します。</span><span class="sxs-lookup"><span data-stu-id="441c1-124">Select the **Keyboard** icon on the taskbar to show the touch keyboard.</span></span>
    
    1. <span data-ttu-id="441c1-125">タッチ キーボードで、左上隅にあるキーボード アイコンを選択してキーボード設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-125">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    
    1. <span data-ttu-id="441c1-126">上の行の次から最後のキーボードの種類を選択して QWERTY を有効にし、2 行目の最後のオプションを選択して浮動を有効にします。これは、この大きな画面で非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="441c1-126">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="441c1-127">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-127">See the following examples.</span></span>

       ![キーボード設定](images/kbd.png)
 
4. <span data-ttu-id="441c1-129">ソフト キーボードの設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="441c1-129">Configure the soft keyboard settings.</span></span>

    1. <span data-ttu-id="441c1-130">タッチ キーボードの **[設定** ] アイコンを選択するか、入力設定を検索して **開きます**。</span><span class="sxs-lookup"><span data-stu-id="441c1-130">Select the **Settings** icon on the touch keyboard or search for and open **Typing settings**.</span></span>
    
       ![ソフト キーボードの設定](images/sh2-softkeyboard.png)

    1. <span data-ttu-id="441c1-132">[スペル チェック]、[タイピング]、および [タッチ キーボード] の下のすべてのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="441c1-132">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="441c1-133">次の使用例は、オプションの移動と選択に役立つトラックパッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="441c1-133">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="441c1-134">画面上のキーボードは、Microsoft Store の検索に使用されています。</span><span class="sxs-lookup"><span data-stu-id="441c1-134">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![トラックパッドの使用](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a><span data-ttu-id="441c1-136">キーボードBluetoothマウスを構成する (オプション)</span><span class="sxs-lookup"><span data-stu-id="441c1-136">Configure Bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="441c1-137">デバイスをプライマリ Windows デバイスとして使用している場合や、入力や精度の向上のために頻繁に使用する場合は、キーボードとマウスを接続します。</span><span class="sxs-lookup"><span data-stu-id="441c1-137">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="441c1-138">Surface Hub デバイスが PC に近い場合は、境界線のないマウスを使用して Surface Hub と PC の間をシームレスに <a href="https://aka.ms/mm" target="_blank"> </a> 移動できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-138">If your Surface Hub device is near to a PC, you can use <a href="https://aka.ms/mm" target="_blank"> Mouse without Borders</a> to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="441c1-139">詳細については <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> 、「Microsoft download from the Garage: Mouse without Borders」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-139">For more information, see <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> Microsoft download from The Garage: Mouse without Borders.</span></span> </a>

## <a name="example-of-taskbar-layout"></a><span data-ttu-id="441c1-140">タスク バーのレイアウトの例</span><span class="sxs-lookup"><span data-stu-id="441c1-140">Example of Taskbar layout</span></span>

<span data-ttu-id="441c1-141">Windows 10 Professional または Enterprise 用の Surface Hub 2 をセットアップ/構成する以下の手順を完了した後、最も使用されているアプリケーションをタスク バーにピン留めして、各アプリケーションをワンタッチで簡単に起動することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-141">After completing the below steps to setup/configure your Surface Hub 2 for Windows 10 Professional or Enterprise, we recommend you utilize pinning your most used applications to the Taskbar for a quick one-touch launch of each application.</span></span> <span data-ttu-id="441c1-142">タスク バーの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="441c1-142">Below is an example of what your taskbar could look like:</span></span>

 ![タスク バーのレイアウト](images/taskblyt.png)
### <a name="update-installed-apps"></a><span data-ttu-id="441c1-144">インストールされているアプリを更新する</span><span class="sxs-lookup"><span data-stu-id="441c1-144">Update installed apps</span></span>

<span data-ttu-id="441c1-145">インストールされているストア アプリを更新するには、次の方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="441c1-145">To update all installed Store apps:</span></span>

1. <span data-ttu-id="441c1-146">Microsoft Store アプリを開き、右上隅にある **[その** 他の省略記号を表示する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-146">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>
2. <span data-ttu-id="441c1-147">[ダウンロード **と更新] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="441c1-147">Select **Downloads and updates.**</span></span>
3. <span data-ttu-id="441c1-148">[更新 **プログラムの取得] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="441c1-148">Select **Get updates**</span></span>

### <a name="scan-for-and-install-all-windows-updates"></a><span data-ttu-id="441c1-149">すべての Windows 更新プログラムをスキャンしてインストールする</span><span class="sxs-lookup"><span data-stu-id="441c1-149">Scan for and install all Windows Updates</span></span>
<span data-ttu-id="441c1-150">Windows 10 Professional または Windows 10 Enterprise に移行した後、サービスと機能更新プログラムをインストールできる場合があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-150">After migrating to Windows 10 Professional or Windows 10 Enterprise, there may be servicing and feature updates available for you to install.</span></span> 

- <span data-ttu-id="441c1-151">[設定の**更新**  >  **プログラム&セキュリティ >]** に移動し、[更新プログラムの確認 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-151">Go to **Settings** > **Update & Security** > and then select **Check for updates**.</span></span>
- <span data-ttu-id="441c1-152">更新プログラムがある場合は、インストールして再起動し、次の通知が表示されるまでプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="441c1-152">If there are any updates, install them, reboot, and then repeat the process until you see the following notification:</span></span>

> [!div class="mx-imgBorder"]
> ![Windows Update 'You'up to date' 通知](images/wustatus.png)


## <a name="onedrive-for-business"></a><span data-ttu-id="441c1-154">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="441c1-154">OneDrive for Business</span></span>

<span data-ttu-id="441c1-155">OneDrive for Business を使用すると、すべての作業デバイス間でツール、ログ、その他のファイル <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> </a> を簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-155">Use <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business</a> to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="441c1-156">OneDrive を使用すると、ノート PC、Surface Hub Desktop、Intune で管理されるモバイル デバイス間で作業ファイルを共有できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-156">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="441c1-157">ファイルは任意のデバイスで編集できます。すべてのネットワーク接続デバイスが変更に合って更新されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-157">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>

- <span data-ttu-id="441c1-158">Surface Hub SSD (128 GB) のサイズを考慮して、Surface Hub Desktop デバイスで OneDrive を構成する場合は、ファイルをオンラインに保ち、使用するファイルをダウンロードする既定の構成を確認してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-158">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="441c1-159">必要な場合にのみファイルをダウンロードする OneDrive を構成するには、[Files **On-Demand]** 設定を [スペースの節約] に設定し、使用するファイルを **ダウンロードします**。</span><span class="sxs-lookup"><span data-stu-id="441c1-159">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="441c1-160">詳細については、「Windows でファイルのオンデマンド状態をクエリおよび設定 <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> する」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-160">For more information, see <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Query and set Files On-Demand states in Windows</a>.</span></span>

![OneDrive の設定](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="441c1-162">また、これらの手順を繰り返して個人用 OneDrive を構成することもできますが、ドライブ領域を節約し、必要に応じてファイルのみをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="441c1-162">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <a name="sharepoint-and-teams"></a><span data-ttu-id="441c1-163">SharePoint と Teams</span><span class="sxs-lookup"><span data-stu-id="441c1-163">SharePoint and Teams</span></span>

<span data-ttu-id="441c1-164">SharePoint および Teams チャネル ファイルは、OneDrive 同期エンジンを使用して、ラップトップや Surface Hubs などのデスクトップ デバイスにローカルで同期することもできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-164">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="441c1-165">OneDrive 同期アプリを使用して内部企業ファイルをローカル ドライブに同期するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="441c1-165">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="441c1-166">SharePoint サイトに移動し、ローカル デバイスから表示または編集するファイルのトップ レベルのドキュメント ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="441c1-166">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>

2. <span data-ttu-id="441c1-167">SharePoint リボン **の上部** にある [同期] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-167">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>

3. <span data-ttu-id="441c1-168">ポップアップで **[開く** ] を選択します このサイトでは **、Microsoft OneDrive を開きます**。</span><span class="sxs-lookup"><span data-stu-id="441c1-168">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>

4. <span data-ttu-id="441c1-169">タスク バーの右下にある OneDrive アイコンを選択して、SharePoint ファイルがローカル ドライブと同期しているのを確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-169">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>

5. <span data-ttu-id="441c1-170">ファイルをオンラインに保ち、ファイルを使用する場合にのみダウンロードする構成が設定されているのを確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-170">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>

    1. <span data-ttu-id="441c1-171">エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-171">Open file explorer.</span></span>
    
    2. <span data-ttu-id="441c1-172">SharePoint 名に移動して右クリックします。たとえば \*\*、Contoso \ \<SharePoint Document Folder Name\> . \*\*</span><span class="sxs-lookup"><span data-stu-id="441c1-172">Navigate to and right click your SharePoint name; for example, **Contoso \ \<SharePoint Document Folder Name\>**.</span></span>
    
    3. <span data-ttu-id="441c1-173">[ **空き領域を解放する] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-173">Select **Free up space**.</span></span>
    
    4. <span data-ttu-id="441c1-174">[状態] 列には、ファイルとフォルダーの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-174">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="441c1-175">詳細については <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> 、「SharePoint ファイルを OneDrive 同期クライアントと同期する」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-175">For more information, see <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sync SharePoint files with the OneDrive sync client</a>.</span></span>
    
6. <span data-ttu-id="441c1-176">Teams チャネル ファイルは SharePoint サイトに保存され、バージョン履歴やローカル デスクトップ デバイスとの同期など、すべての同じ SharePoint ドキュメント機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="441c1-176">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="441c1-177">Teams チャネル ファイルを同期するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="441c1-177">To sync Teams Channel files:</span></span>

    1. <span data-ttu-id="441c1-178">目的の Teams チャネルに移動し、上部の **[ファイル** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-178">Navigate to the Teams Channel of interest and select the **Files** tab at the top.</span></span> <span data-ttu-id="441c1-179">次に、[同期]**を選択します**。ファイルは同期を開始し、デスクトップ \ Contoso \ の**エクスプローラーに \<name of the Teams Channel\> 表示されます**。</span><span class="sxs-lookup"><span data-stu-id="441c1-179">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Contoso \ \<name of the Teams Channel\>**.</span></span>
    
    2. <span data-ttu-id="441c1-180">SharePoint サイトの同期に使用したのと同じ手順を使用して、クラウドにファイルを保持し、それらを使用する場合にのみダウンロードします。Teams チャネル名のエクスプローラーをタップして長押しまたは右クリックし、[\*\*\*\* 空き領域] を選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-180">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <a name="surface-hub-pen-settings"></a><span data-ttu-id="441c1-181">Surface Hub ペンの設定</span><span class="sxs-lookup"><span data-stu-id="441c1-181">Surface Hub pen settings</span></span>

**<span data-ttu-id="441c1-182">Surface Hub ペンBluetoothペアリングする</span><span class="sxs-lookup"><span data-stu-id="441c1-182">Pair the Bluetooth Surface Hub Pen</span></span>**

<span data-ttu-id="441c1-183">ペンをペアリングしてペンのファームウェアを最新の状態に保ち、ペンショートカットを設定し、Bluetooth デバイス設定ページまたは Surface アプリでバッテリー充電情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="441c1-183">Pair the pen to keep the pen firmware up to date, set the pen shortcuts, and get battery charge information on the Bluetooth device settings page, or in the Surface app:</span></span>

1. <span data-ttu-id="441c1-184">[スタート**設定デバイス**  >  **]**  >  **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-184">Select **Start** > **Settings** > **Devices**.</span></span>

2. <span data-ttu-id="441c1-185">[デバイス **または他Bluetooth追加] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-185">Select **Add Bluetooth or other device**.</span></span>

3. <span data-ttu-id="441c1-186">[Bluetooth] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-186">Choose **Bluetooth**.</span></span>

4. <span data-ttu-id="441c1-187">ペンの尾ボタンを外して、バッテリー接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="441c1-187">Remove the pen tail button and shake to disconnect the battery connection.</span></span>

5. <span data-ttu-id="441c1-188">キャップをオンに戻し、ペアリング LED が点滅するまでキャップを長押しします。</span><span class="sxs-lookup"><span data-stu-id="441c1-188">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>

6. <span data-ttu-id="441c1-189">Surface Hub の設定で **Bluetooth[Surface Hub 2 Pen] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-189">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>

7. <span data-ttu-id="441c1-190">ペアリング操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="441c1-190">Complete the pairing operation.</span></span> 

8. <span data-ttu-id="441c1-191">ペアリングが成功しない場合は、もう一度ペンのペアリングを試みます。</span><span class="sxs-lookup"><span data-stu-id="441c1-191">If the pairing is not successful, you can attempt to pair the pen again.</span></span> <span data-ttu-id="441c1-192">それでも問題が発生しない場合は、ホワイトボード アプリケーションでペンが動作するを確認して、バッテリーが充電されるのをテストできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-192">If that doesn't work, you can test to see if the battery is charged by verifying the pen works in the Whiteboard application.</span></span> <span data-ttu-id="441c1-193">ない場合は、バッテリーを交換し、もう一度ペンのペアリングを試みます。</span><span class="sxs-lookup"><span data-stu-id="441c1-193">If not, then replace the battery and then try to pair the pen again.</span></span> <span data-ttu-id="441c1-194">必要に応じて、デバイスを再起動してから、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-194">If necessary, restart the device and then try again.</span></span>

<span data-ttu-id="441c1-195">**ペンのショートカットを設定する** Surface Hub ペンには、"tail click" とも呼ばれるショートカット ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="441c1-195">**Set pen shortcuts** The Surface Hub pen has a shortcut button sometimes referred to as a "tail click".</span></span> <span data-ttu-id="441c1-196">ショートカットを構成するには、前述のように、最初にペンをペアリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-196">Configuring shortcuts requires you to first pair the pen, as described earlier.</span></span>

1. <span data-ttu-id="441c1-197">[ペン] を検索し、[ **ペン] を選択& Windows Ink の設定を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-197">Search for Pen and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="441c1-198">ページの下部付近で、[ペン ショートカット] を選択してダイアログ ボックスを開きます。次に示します。</span><span class="sxs-lookup"><span data-stu-id="441c1-198">Near the bottom of the page, select Pen shortcuts which opens the dialog box, shown here:</span></span>

   ![ペンのショートカット](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a><span data-ttu-id="441c1-200">カメラの構成</span><span class="sxs-lookup"><span data-stu-id="441c1-200">Camera configuration</span></span>

<span data-ttu-id="441c1-201">カメラは、デバイスの上部またはどちら側にマウントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-201">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="441c1-202">カートではなくデスクトップ スタンドでハブを使用している場合、またはハブに近接している場合は、カメラの角度を最適化する位置にカメラをマウントします。</span><span class="sxs-lookup"><span data-stu-id="441c1-202">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="441c1-203">カメラは自動回転しないので、カメラを手動で回転するには 2mm の 16 進キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="441c1-203">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="441c1-204">カメラをサイド マウントし、カメラを手動で回転する方法の詳細については、「Surface Hub 2S カメラレンズの向き」 <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-204">For more information on how to side-mount the camera and rotate the camera manually, see <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> Surface Hub 2S camera lens orientation</a>.</span></span>

## <a name="windows-hello-configuration"></a><span data-ttu-id="441c1-205">Windows Hello の構成</span><span class="sxs-lookup"><span data-stu-id="441c1-205">Windows Hello configuration</span></span>

<span data-ttu-id="441c1-206">Windows 10 Enterprise を実行する Surface Hub 2S では、Win32 デスクトップ アプリケーションと生体認証 Windows Hello オプションの完全なスイートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-206">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="441c1-207">Surface Hub 2 指紋リーダー アクセサリは、デバイス上の任意の USB-C ポートに接続できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-207">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

<span data-ttu-id="441c1-208">Surface Hub 2 指紋リーダーを注文するか、技術的な仕様を表示するには、「(surface-hub-2-essential-add-ons.md" target="_blank">Essential アドオン for Windows 10 Pro および Enterprise on Surface Hub 2」を参照してください。 </a></span><span class="sxs-lookup"><span data-stu-id="441c1-208">To order a Surface Hub 2 Fingerprint Reader or view technical specs, see (surface-hub-2-essential-add-ons.md" target="_blank">Essential add-ons for Windows 10 Pro and Enterprise on Surface Hub 2 </a>.</span></span> 

<span data-ttu-id="441c1-209">指紋リーダーを挿入した後、[スタート\*\*\*\* 設定] [アカウント] サインイン  >  \*\*\*\*  >  \*\*\*\*  >  **オプション**  >  **[Windows Hello Fingerprint]** を選択して指紋を登録します。</span><span class="sxs-lookup"><span data-stu-id="441c1-209">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="441c1-210">顔認識には Windows Hello 認定デバイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="441c1-210">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="441c1-211">Surface Hub 2S カメラでは、Windows Hello の顔認識はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="441c1-211">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a><span data-ttu-id="441c1-212">タスク バーの [画面のロック] ショートカット アイコンを有効にする</span><span class="sxs-lookup"><span data-stu-id="441c1-212">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="441c1-213">Windows-L キーボード ショートカットのようなワンタッチ画面ロックを有効にするアイコンをタスク バーに追加するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="441c1-213">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="441c1-214">デスクトップを長押しまたは右クリックし、[新しい\*\*\*\* ショートカットの参照  >  \*\*\*\*  >  **デスクトップ OK**  >  **次**へ]  >  **を**  >  **選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-214">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>

1.  <span data-ttu-id="441c1-215">[自分の PC をロックする] などのショートカットの **名前を指定**し、[完了] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-215">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>

1.  <span data-ttu-id="441c1-216">デスクトップ上で新しく作成したショートカットを右クリックまたはタップして長押しし、[プロパティ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-216">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="441c1-217">[ショートカット **] タブ**で、[ターゲット] フィールドに次の情報を**入力します\*\*\*\*Rundll32.exe User32.dll、LockWorkStation**</span><span class="sxs-lookup"><span data-stu-id="441c1-217">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>

1.  <span data-ttu-id="441c1-218">[アイコンの **変更] ボタンを** 選択 \*\* し、C:\Windows\System32\imageres.dll\*\* を参照して、使用するアイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-218">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 

    <span data-ttu-id="441c1-219">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="441c1-219">See the following example:</span></span>

    ![アイコンを選択する](images/lock.png)
    
1.  <span data-ttu-id="441c1-221">**[OK] を**選択してショートカットを保存します。</span><span class="sxs-lookup"><span data-stu-id="441c1-221">Select **OK** to save the shortcut.</span></span>

1.  <span data-ttu-id="441c1-222">ショートカットを右クリックまたはタップして長押しし、[タスク バーに **ピン留めする] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-222">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

1. <span data-ttu-id="441c1-223">ロック ショートカットをタスク バーにピン留めした後、デスクトップから削除できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-223">After you have pinned the lock shortcut to the taskbar, you can delete it from the desktop.</span></span>

## <a name="applications"></a><span data-ttu-id="441c1-224">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="441c1-224">Applications</span></span>


### <a name="microsoft-whiteboard"></a><span data-ttu-id="441c1-225">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="441c1-225">Microsoft Whiteboard</span></span>

<span data-ttu-id="441c1-226">Microsoft ホワイトボードをインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="441c1-226">To install the Microsoft Whiteboard:</span></span>

 - <span data-ttu-id="441c1-227">タスク バーの **右下にある [Windows Ink Workspace]** アイコンを選択し、ホワイトボードを **ダウンロードします**。</span><span class="sxs-lookup"><span data-stu-id="441c1-227">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span></span>
 
   ![インク ワークスペース](images/ink.png) 

<span data-ttu-id="441c1-229">または、Microsoft ストアからホワイトボードをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-229">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="441c1-230">Microsoft Store アプリを開き、ホワイトボード **を検索します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-230">Open Microsoft Store app and search for **Whiteboard**.</span></span>

2. <span data-ttu-id="441c1-231">[サインイン **してデバイス間** で使用する] を選択して[いいえ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-231">Choose **No thanks** to sign in and use across devices.</span></span>

3. <span data-ttu-id="441c1-232">ホワイトボードをタスク バーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-232">Pin Whiteboard to the taskbar.</span></span>

### <a name="surface-app"></a><span data-ttu-id="441c1-233">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="441c1-233">Surface app</span></span>

1. <span data-ttu-id="441c1-234">Microsoft Store で Surface を **検索します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-234">In the Microsoft Store, search for **Surface**.</span></span>

2. <span data-ttu-id="441c1-235">[使用可能な **フィルター] を [** すべてのデバイス] **に設定します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-235">Set the **Available on** filter to **All devices**.</span></span>

3. <span data-ttu-id="441c1-236">Surface アプリ **をインストール** します。</span><span class="sxs-lookup"><span data-stu-id="441c1-236">Install the **Surface** app.</span></span> <span data-ttu-id="441c1-237">これは、最初に表示されるアプリである必要があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-237">This should be the first app listed.</span></span> <span data-ttu-id="441c1-238">アプリをインストールするには、MSA をストアに関連付ける必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-238">You might need to associate your MSA to the Store in order to install the app.</span></span>

4. <span data-ttu-id="441c1-239">Surface アプリ **をタスク バー** にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-239">Pin the **Surface** app to taskbar.</span></span>

### <a name="snip--sketch"></a><span data-ttu-id="441c1-240">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="441c1-240">Snip & Sketch</span></span>

1. <span data-ttu-id="441c1-241">**Snip &スケッチ アプリを開**き、タスク バーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-241">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>

2. <span data-ttu-id="441c1-242">右上隅にある省略記号を選択し、[設定] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-242">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>

3. <span data-ttu-id="441c1-243">[ **設定]** で、[クリップボードに **自動コピー]**、[切り取 **りを保存**] 、および [複数のウィンドウ **]** をオンにします (オプション)。</span><span class="sxs-lookup"><span data-stu-id="441c1-243">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <a name="microsoft-office"></a><span data-ttu-id="441c1-244">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="441c1-244">Microsoft Office</span></span>

1. <span data-ttu-id="441c1-245">[ポータル] <a href="https://portal.office.com/account#installs" target="_blank"> Office開 </a> き、目的のアプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="441c1-245">Open the <a href="https://portal.office.com/account#installs" target="_blank"> Office Portal</a> and install your desired applications.</span></span>

2. <span data-ttu-id="441c1-246">必要なアプリケーションOfficeタスク バーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-246">Pin desired Office applications to the taskbar.</span></span>

3. <span data-ttu-id="441c1-247">Outlook がインストールされている場合は、最後の 2 週間のキャッシュのみを保存する Outlook OST を設定してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-247">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="441c1-248">これにより、ディスク使用量とセットアップ時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-248">This will vastly reduce disk usage and setup time.</span></span>

    - <span data-ttu-id="441c1-249">[**ファイル アカウント**  >  **の設定] を選択**し、アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-249">Select **File** > **Account Settings** and select your account.</span></span>
    
    - <span data-ttu-id="441c1-250">[ **変更]** を選択し **、[Exchange** キャッシュ モードを使用する] のスライダーを 14 日間に設定します。</span><span class="sxs-lookup"><span data-stu-id="441c1-250">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <a name="microsoft-teams"></a><span data-ttu-id="441c1-251">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="441c1-251">Microsoft Teams</span></span>

1. <span data-ttu-id="441c1-252">Microsoft Teams を <a href="https://teams.microsoft.com/downloads" target="_blank"> ダウンロードしてインストールします </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-252">Download and install <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft Teams </a>.</span></span>

2. <span data-ttu-id="441c1-253">自動起動アプリケーションに設定を構成します (オプション)。</span><span class="sxs-lookup"><span data-stu-id="441c1-253">Configure settings to Auto-start application (optional).</span></span>

3. <span data-ttu-id="441c1-254">タスク バーに Teams をピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-254">Pin Teams to the taskbar.</span></span>

4. <span data-ttu-id="441c1-255">デバイス上の Teams 通知を減らすことを検討して、注意をそらさないようにします (オプション)。</span><span class="sxs-lookup"><span data-stu-id="441c1-255">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

   ![Teams 通知](images/teams.png)

### <a name="connect-app"></a><span data-ttu-id="441c1-257">アプリの接続</span><span class="sxs-lookup"><span data-stu-id="441c1-257">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="441c1-258">Windows 10 バージョン 2004 以降では、Miracast を使用したワイヤレス プロジェクション用の Connect アプリは既定ではインストールされていませんが、オプションの機能として使用できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-258">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="441c1-259">Windows バージョン 2004 以降をインストール (または更新) した場合は、設定の [この PC への投影] 画面に次の情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-259">If you have installed (or updated to) Windows version 2004 or later, you may see the following on the Projecting to this PC screen in settings:</span></span>

![この PC へのプロジェクト](images/sh2-project.png) 


1. <span data-ttu-id="441c1-261">[この PC への投影] 設定ページからアプリをインストールするには、[\*\*\*\* オプション機能] [機能の追加] を選択し、ワイヤレスディスプレイ アプリ  >  \*\*\*\*\*\*をインストール\*\*します。</span><span class="sxs-lookup"><span data-stu-id="441c1-261">To install the app from the “Projecting to this PC” settings page, select **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

2. <span data-ttu-id="441c1-262">[ **一部の Windows デバイスと Android デバイスでは、この PC**に投影できます。[OK] と表示されている場合は、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-262">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose:</span></span>

    - <span data-ttu-id="441c1-263">**デバイスが企業ネットワーク** 上にない場合は、どこでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-263">**Available everywhere** if the device is not on a corporate network.</span></span>
    - <span data-ttu-id="441c1-264">それ以外の場合は、[ **セキュリティで保護されたネットワーク上のすべての場所で利用可能] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-264">Otherwise, choose **Available everywhere on secure networks**.</span></span>
    
3. <span data-ttu-id="441c1-265">[この **PC にプロジェクトを求める] で、[** 初回 **のみ] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-265">Under **Ask to project to this PC**, choose **First time only**.</span></span>

4. <span data-ttu-id="441c1-266">[ペアリング **に PIN を要求する] で、[** しない] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-266">Under **Require PIN for pairing**, choose **Never**.</span></span>

5. <span data-ttu-id="441c1-267">次に、アプリを起動し、タスク バーにピン留めするには、[接続] を **検索します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-267">To then launch the app and pin it to the taskbar, search for **Connect**.</span></span>

6. <span data-ttu-id="441c1-268">アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-268">Open the app.</span></span> <span data-ttu-id="441c1-269">アプリが開いている間に、タスク バーの [アプリの接続] アイコンを右クリックし、[タスク バーにピン留め **する] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-269">While the app is open, right-click on the Connect app icon on the taskbar, and select **pin to taskbar**.</span></span>

7. <span data-ttu-id="441c1-270">次に、Connect アプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="441c1-270">Then close the Connect app.</span></span> <span data-ttu-id="441c1-271">**アプリを少なくとも 1** 回実行しない限り、この PC へのプロジェクトは機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-271">**Project to this PC** might not work unless the app has been run at least once.</span></span>

<span data-ttu-id="441c1-272">企業ネットワークに含めない場合の推奨構成:</span><span class="sxs-lookup"><span data-stu-id="441c1-272">Recommended configuration when not on the corporate network:</span></span>

![自宅の設定](images/project1.png)

<span data-ttu-id="441c1-274">企業ネットワークでの推奨される構成:</span><span class="sxs-lookup"><span data-stu-id="441c1-274">Recommended configuration on the corporate network:</span></span>

![作業中の設定](images/project2.png)

### <a name="your-phone"></a><span data-ttu-id="441c1-276">スマホ同期</span><span class="sxs-lookup"><span data-stu-id="441c1-276">Your Phone</span></span>

<span data-ttu-id="441c1-277">電話 **アプリは** 、Windows 10 に既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="441c1-277">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="441c1-278">存在しない場合は、Windows ストアからインストールできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-278">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="441c1-279">アプリのセットアップの詳細については、「Windows 10 で電話をセットアップし、PC と電話の間でデータ <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> を同期する方法」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-279">For information about setting up the app, see <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> How to set up Your Phone on Windows 10 and sync data between your PC and phone</a>.</span></span> <span data-ttu-id="441c1-280">また、「Windows 10 の電話アプリで一般的な問題を解決する方法 <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> 」も参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-280">Also see <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> How to fix common problems with Your Phone app on Windows 10</a>.</span></span>

###  <a name="fancy-zones"></a><span data-ttu-id="441c1-281">ファンシー ゾーン</span><span class="sxs-lookup"><span data-stu-id="441c1-281">Fancy Zones</span></span>


<span data-ttu-id="441c1-282">**ファンシー** ゾーンは、GitHub の <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys と呼ばれるツール </a> のコレクションの一部です。</span><span class="sxs-lookup"><span data-stu-id="441c1-282">**Fancy Zones** is part of a collection of tools called <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys</a> on GitHub..</span></span> <span data-ttu-id="441c1-283">Surface Hub 2 の画面の不動産を利用するには、ディスプレイ ("zone") で固定レイアウトを定義し、各領域で実行するアプリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-283">It is a great way to utilize the screen real-estate on a Surface Hub 2 by giving you the ability to define fixed layouts on your display (“zones”), and then select which app will then run in each zone.</span></span> 


<span data-ttu-id="441c1-284">[PowerToys Wiki には、各](https://github.com/microsoft/PowerToys/wiki)ツールの使い方とカスタマイズ方法 (ファンシーゾーンを含む)[の手順があります](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview)。</span><span class="sxs-lookup"><span data-stu-id="441c1-284">The [PowerToys wiki](https://github.com/microsoft/PowerToys/wiki) has instructions for how to use and customize each tool, including [FancyZones](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview).</span></span> <span data-ttu-id="441c1-285">PowerToys をインストールした後で、カスタム レイアウトを選択または作成し、シフト キーを押したまま、キーボード キーをドラッグまたは使用して実行中のアプリを特定の領域に移動できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-285">At a high level – after installing PowerToys, you can select or create a custom layout, and then hold the shift key down and drag or use keyboard keys to move a running app into specific zones.</span></span> <span data-ttu-id="441c1-286">この操作Bluetooth USB キーボードとマウスを使用すると役立ちます。また、オンスクリーン タッチ キーボードとタッチパッドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-286">Using a Bluetooth or USB keyboard and mouse will help with this, or you can use the on-screen touch keyboard and touchpad.</span></span>

**<span data-ttu-id="441c1-287">Power Toys のヒント</span><span class="sxs-lookup"><span data-stu-id="441c1-287">Power toys tips</span></span>**
- <span data-ttu-id="441c1-288">GitHub で PowerToys リリースの更新プログラムの電子メール通知を受信するには、ページの上部にある [サインアップ] ボタンをクリック [します](https://github.com/microsoft/PowerToys/releases)。</span><span class="sxs-lookup"><span data-stu-id="441c1-288">To receive email notifications of PowerToys release updates on GitHub, click the “sign-up” button at the top of the [page](https://github.com/microsoft/PowerToys/releases).</span></span>
- <span data-ttu-id="441c1-289">PowerToys をインストールすると、PowerToys の設定を構成して Windows 通知を受信したり、最新の更新プログラムをダウンロードしてインストールしたりできます。更新プログラムを自動的に **オン** にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="441c1-289">Once PowerToys is installed, you can receive Windows notifications and/or download and install the latest updates by configuring the PowerToys settings **Download updates automatically** to on.</span></span>
- <span data-ttu-id="441c1-290">PowerToys 設定に移動するには、タスク バーでアップ カラット **の実行中** のアプリを選択し、メニューが表示されるまで PowerToys アイコンを右クリックまたは押したままにします。</span><span class="sxs-lookup"><span data-stu-id="441c1-290">To get to the PowerToys settings, select the up carat **Running apps** on the taskbar, and then right click or press and hold the PowerToys icon until the menu appears.</span></span> <span data-ttu-id="441c1-291">[設定] を選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-291">Select “Settings”.</span></span>
- <span data-ttu-id="441c1-292">PowerToys 設定ページの下部で、[更新プログラムを自動的にダウンロードする **] をオン** にします。</span><span class="sxs-lookup"><span data-stu-id="441c1-292">At the bottom of the PowerToys settings page, turn **Download updates automatically** to on.</span></span>
- <span data-ttu-id="441c1-293">更新プログラムがリリースされると、更新プログラムをインストールする場合のオプションを示す Windows 通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-293">When an update has been released, a Windows notification will appear giving you the option of when to install the update.</span></span>


### <a name="edge-chromium-browser"></a><span data-ttu-id="441c1-294">エッジ クロム ブラウザー</span><span class="sxs-lookup"><span data-stu-id="441c1-294">Edge Chromium browser</span></span>

<span data-ttu-id="441c1-295">新しいエッジ クロム ブラウザー <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> をダウンロードしてインストールします </a> 。</span><span class="sxs-lookup"><span data-stu-id="441c1-295">Download and install the new <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank">Edge Chromium browser</a>.</span></span>


### <a name="surface-hub-hardware-diagnostic-tool"></a><span data-ttu-id="441c1-296">Surface Hub ハードウェア診断ツール</span><span class="sxs-lookup"><span data-stu-id="441c1-296">Surface Hub Hardware Diagnostic tool</span></span>

<span data-ttu-id="441c1-297"><a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank">Microsoft Store から無料で利用できる Surface Hub </a> ハードウェア診断ツール。</span><span class="sxs-lookup"><span data-stu-id="441c1-297">The <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> Surface Hub Hardware Diagnostic tool</a> available for free from the Microsoft Store.</span></span> <span data-ttu-id="441c1-298">このツールは、Surface Hub が最高のパフォーマンスを提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="441c1-298">The tool is designed to help you make sure your Surface Hub is performing at its best.</span></span> <span data-ttu-id="441c1-299">ファームウェアが最新で正しく構成されたかどうかを判断するテストが含まれている。</span><span class="sxs-lookup"><span data-stu-id="441c1-299">It contains tests to determine if your firmware is up to date and configured correctly.</span></span> <span data-ttu-id="441c1-300">対話型テストを使用すると、重要な機能が期待通り動作しているのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-300">Interactive tests allow you to confirm essential functionality is working as expected.</span></span> <span data-ttu-id="441c1-301">問題が発生した場合は、結果を保存して Surface Hub のサポート チームと共有できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-301">If problems are encountered, results can be saved and shared with the Surface Hub Support Team.</span></span> <span data-ttu-id="441c1-302">リンクをクリックして Microsoft Store からインストールし、アプリケーションをタスク バーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="441c1-302">Click on the link to install it from the Microsoft Store, and then pin the application to your taskbar.</span></span>

## <a name="additional-settings"></a><span data-ttu-id="441c1-303">追加設定</span><span class="sxs-lookup"><span data-stu-id="441c1-303">Additional settings</span></span>

### <a name="pen-tail-select-to-launch-whiteboard"></a><span data-ttu-id="441c1-304">ホワイトボードを起動するペンの尾の選択</span><span class="sxs-lookup"><span data-stu-id="441c1-304">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="441c1-305">[ペン] **を検索し** 、[ **ペン] & Windows インクの設定] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-305">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="441c1-306">ページの下部付近の [ペン のショートカット] **で** 、[一度選択] を **[Microsoft** **ホワイトボード] に設定します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-306">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <a name="power-management"></a><span data-ttu-id="441c1-307">電源管理</span><span class="sxs-lookup"><span data-stu-id="441c1-307">Power management</span></span>

<span data-ttu-id="441c1-308">Windows 10 Pro または Enterprise on Surface Hub 2 を使用して最高のエクスペリエンスを得るには、いくつかの電源設定があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-308">There are several power settings available to get the best experience using Windows 10 Pro or Enterprise on Surface Hub 2.</span></span> <span data-ttu-id="441c1-309">これには、画面と PC のタイムアウトと、組み込みの人間のプレゼンス検出 (Doppler)、スクリーン セーバー、パスワード保護、およびラップトップ/デスクトップ ユーザーを対象としたグループ ポリシーの電源設定を適切に通過する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="441c1-309">This includes screen and pc timeouts and how they interact with the built-in human presence detection (Doppler), the screen saver and password protection, and then if appropriate how to by-pass group policy power settings intended for laptop / desktop users.</span></span>

<span data-ttu-id="441c1-310">Windows 10 Pro または Enterprise on Surface Hub 2 では、タッチ、マウス、キーボード操作、および組み込みの人間の占有検出 (Doppler) によって画面がスリープ状態に保たれる。</span><span class="sxs-lookup"><span data-stu-id="441c1-310">Windows 10 Pro or Enterprise on Surface Hub 2 keeps the screen from going to sleep by touch, mouse, and keyboard actions, as well as the built-in human occupancy detection (Doppler).</span></span> <span data-ttu-id="441c1-311">人間の占有率の検出は既定で有効になっていますが、必要に応じて、初期移行の一環として Surface UEFI コンフィギュレーター ツールのデバイス オプションを切り当て、または後の UEFI 構成パッケージを構築して適用することで、UEFI で無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="441c1-311">Human occupancy detection is enabled by default, but if desired it can be disabled in UEFI by toggling the device option in the Surface UEFI Configurator tool either as part of the initial migration, or by building and applying a later UEFI configuration package.</span></span> 

**<span data-ttu-id="441c1-312">電源管理: 画面と PC のスリープ設定</span><span class="sxs-lookup"><span data-stu-id="441c1-312">Power Management: Screen and PC sleep settings</span></span>**

1. <span data-ttu-id="441c1-313">[スタート**設定**  >  **]**  >  **[システムの**  >  **電源&スリープ] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-313">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>

2. <span data-ttu-id="441c1-314">[電源モード] スライダーを [最適なパフォーマンス **] に設定します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-314">Set the power mode slider to **Best performance**.</span></span>

3. <span data-ttu-id="441c1-315">画面とスリープの値を好みに応じて構成し、動きが検出されるとデバイスを目を覚ますドップラープレゼンス検出も管理します。</span><span class="sxs-lookup"><span data-stu-id="441c1-315">Configure screen and sleep values to your preference while also accounting for Doppler presence detection that wakes up the device when movement is detected.</span></span> <span data-ttu-id="441c1-316">したがって、ベスト プラクティスとして、[画面] を **[2**時間後にオフにする] に設定し、PC を**4**時間後にオフに設定してください。</span><span class="sxs-lookup"><span data-stu-id="441c1-316">Accordingly, as a best practice, it's recommended to set Screen to **Turn off after 2 hours** and the PC to **Turn off after 4 hours.**</span></span>

**<span data-ttu-id="441c1-317">電源管理: スクリーン セーバー</span><span class="sxs-lookup"><span data-stu-id="441c1-317">Power Management: Screen saver</span></span>**

1. <span data-ttu-id="441c1-318">ロック画面を **検索し、[** 画面の **ロック設定] を開きます**。</span><span class="sxs-lookup"><span data-stu-id="441c1-318">Search for **Lock Screen** and open **Lock screen settings**.</span></span>

2. <span data-ttu-id="441c1-319">[画面 **のタイムアウト設定] と** [ **スクリーン セーバーの設定] を基本** 設定に構成します。</span><span class="sxs-lookup"><span data-stu-id="441c1-319">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span> <span data-ttu-id="441c1-320">推奨される既定値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="441c1-320">Recommended default values are:</span></span>

   - <span data-ttu-id="441c1-321">(なし) または選択したスクリーン セーバーへのスクリーン セーバー。</span><span class="sxs-lookup"><span data-stu-id="441c1-321">Screen saver to (None) or a screen saver of your choice.</span></span>
   - <span data-ttu-id="441c1-322">待機時間を 15 分に設定します。</span><span class="sxs-lookup"><span data-stu-id="441c1-322">Wait time to 15 minutes.</span></span>
   - <span data-ttu-id="441c1-323">再開時に、ログオン画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="441c1-323">On resume, display logon screen.</span></span>


**<span data-ttu-id="441c1-324">電源管理: グループ ポリシー</span><span class="sxs-lookup"><span data-stu-id="441c1-324">Power Management: Group Policy</span></span>**

<span data-ttu-id="441c1-325">次の手順を実行する前に、IT 部門に確認して承認を得て、Surface Hub 2S デバイスをグローバル電源管理ポリシーから除外します。</span><span class="sxs-lookup"><span data-stu-id="441c1-325">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="441c1-326">一部の電源管理設定では、プレゼンス検出機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="441c1-326">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="441c1-327">ソフトウェア センター **を検索して** 開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-327">Search for **Software Center** and open it.</span></span>

2. <span data-ttu-id="441c1-328">[オプション **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-328">Select **Options**.</span></span>

3. <span data-ttu-id="441c1-329">[電源管理 **] を展開し**  、[自分の IT 部門からこのコンピューターに電源 **設定を適用しない] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-329">Expand the **Power management**  and select **Do not apply power settings from my IT department to this computer**.</span></span>

   ![ソフトウェア設定](images/soft-cntr.png)

### <a name="storage-sense"></a><span data-ttu-id="441c1-331">ストレージ センサー</span><span class="sxs-lookup"><span data-stu-id="441c1-331">Storage Sense</span></span>

<span data-ttu-id="441c1-332">Surface Hub 2 にはローカル ストレージ用の 128 GB SSD が搭載されています。</span><span class="sxs-lookup"><span data-stu-id="441c1-332">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="441c1-333">記憶域の検出を構成するには、次の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="441c1-333">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="441c1-334">[システム設定 **] の**下にある記憶域の設定 **を検索します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-334">Search for **storage settings**, which is found under **System settings**.</span></span>

2.  <span data-ttu-id="441c1-335">[設定 **] で**、[ **ストレージセンスを有効** にする] を選択して、[記憶域の設定] **ページを** 開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-335">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>

3.  <span data-ttu-id="441c1-336">[記憶域の検出] を **[オン] に切り返します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-336">Turn Storage Sense to **On**.</span></span>

4.  <span data-ttu-id="441c1-337">[ **ストレージセンスの構成] を** 選択するか、今すぐ実行し、ファイルを可能な限りオンラインに保つ設定を構成します (ドライブの容量が制限されています)。</span><span class="sxs-lookup"><span data-stu-id="441c1-337">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="441c1-338">推奨設定:</span><span class="sxs-lookup"><span data-stu-id="441c1-338">Recommended settings:</span></span>

- <span data-ttu-id="441c1-339">Run Storage Sense = Every Day.</span><span class="sxs-lookup"><span data-stu-id="441c1-339">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="441c1-340">アプリで使用していない一時ファイルを削除する = 14 日ごとに (少なくとも)。</span><span class="sxs-lookup"><span data-stu-id="441c1-340">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="441c1-341">[ダウンロード] フォルダー内のファイルが 30 日間以上保存されている場合は、削除します。</span><span class="sxs-lookup"><span data-stu-id="441c1-341">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="441c1-342">OneDrive: コンテンツは、30 日間以上開かされていない場合、オンライン専用になります。</span><span class="sxs-lookup"><span data-stu-id="441c1-342">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <a name="tablet-mode"></a><span data-ttu-id="441c1-343">タブレット モード</span><span class="sxs-lookup"><span data-stu-id="441c1-343">Tablet mode</span></span>

<span data-ttu-id="441c1-344">必要に応じて、アクセシビリティのニーズに合ったタブレット モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="441c1-344">Turn on Tablet mode if desired for accessibility needs.</span></span>


### <a name="sound-settings"></a><span data-ttu-id="441c1-345">サウンド設定</span><span class="sxs-lookup"><span data-stu-id="441c1-345">Sound settings</span></span>

1. <span data-ttu-id="441c1-346">サウンドの設定 **を検索し** 、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-346">Search for **Sounds settings** and open this page.</span></span>

2. <span data-ttu-id="441c1-347">右側 **の [サウンド コントロール パネル** ] を選択し、[サウンド] タブ **を選択** します。</span><span class="sxs-lookup"><span data-stu-id="441c1-347">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>

3. <span data-ttu-id="441c1-348">[**プログラム イベント] で**、[**デバイス接続] と [\*\*\*\*デバイス切断] を [なし]** に**設定します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-348">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <a name="silence-notifications"></a><span data-ttu-id="441c1-349">無音通知</span><span class="sxs-lookup"><span data-stu-id="441c1-349">Silence notifications</span></span>

1. <span data-ttu-id="441c1-350">フォーカス アシストを **検索し** 、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-350">Search for **Focus assist** and open this page.</span></span>

2. <span data-ttu-id="441c1-351">[アラーム **のみ] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-351">Select **Alarms Only**.</span></span> <span data-ttu-id="441c1-352">これにより、一定の通知の飛び出しが回避されます。</span><span class="sxs-lookup"><span data-stu-id="441c1-352">This will avoid constant notification flyouts.</span></span>

### <a name="disk-cleanup"></a><span data-ttu-id="441c1-353">ディスク クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="441c1-353">Disk Cleanup</span></span>

1. <span data-ttu-id="441c1-354">ディスククリーンアップ **を検索し** 、このアプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="441c1-354">Search for **Disk Cleanup** and open this app.</span></span>

2. <span data-ttu-id="441c1-355">[ **削除するファイル] で**、削除するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="441c1-355">Under **Files to delete**, select the files you wish to delete.</span></span> 

3. <span data-ttu-id="441c1-356">また、[システム **ファイルのクリーンアップ] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-356">Also select **Clean up system files**.</span></span>

## <a name="complete-and-verify"></a><span data-ttu-id="441c1-357">完了して確認する</span><span class="sxs-lookup"><span data-stu-id="441c1-357">Complete and verify</span></span>

1. <span data-ttu-id="441c1-358">すべての Windows 更新プログラムをスキャンしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="441c1-358">Scan for and install all Windows Updates.</span></span>

2. <span data-ttu-id="441c1-359">グループ ポリシーを更新します。</span><span class="sxs-lookup"><span data-stu-id="441c1-359">Update Group Policy.</span></span>

   1. <span data-ttu-id="441c1-360">管理者特権のコマンド プロンプトで **、gpupdate /force /boot /wait:0 と入力します**。</span><span class="sxs-lookup"><span data-stu-id="441c1-360">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
   
3. <span data-ttu-id="441c1-361">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="441c1-361">Restart the device.</span></span>

4. <span data-ttu-id="441c1-362">タスク バー アプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-362">Verify taskbar apps.</span></span>

   - <span data-ttu-id="441c1-363">アプリの接続</span><span class="sxs-lookup"><span data-stu-id="441c1-363">Connect App</span></span>
   - <span data-ttu-id="441c1-364">ロック アイコン</span><span class="sxs-lookup"><span data-stu-id="441c1-364">Lock Icon</span></span>
   - <span data-ttu-id="441c1-365">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="441c1-365">Snip & Sketch</span></span>
   - <span data-ttu-id="441c1-366">Teams (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="441c1-366">Teams (if applicable)</span></span>
   - <span data-ttu-id="441c1-367">Officeアプリ (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="441c1-367">Office Apps (if applicable)</span></span>
   - <span data-ttu-id="441c1-368">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="441c1-368">Surface App</span></span>
   - <span data-ttu-id="441c1-369">ホワイトボード</span><span class="sxs-lookup"><span data-stu-id="441c1-369">Whiteboard</span></span>
    
5. <span data-ttu-id="441c1-370">プレゼンス検出を確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-370">Verify presence detection.</span></span>

   - <span data-ttu-id="441c1-371">プレゼンス検出は、システム トレイの緑色のアイコンになります。</span><span class="sxs-lookup"><span data-stu-id="441c1-371">Presence detection will be a green icon in the system tray.</span></span>
    
6. <span data-ttu-id="441c1-372">この PC への投影が Connect アプリで有効になっているか確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-372">Verify projecting to this PC is enabled with the Connect App.</span></span> <span data-ttu-id="441c1-373">Project をこの  **PC 設定に構成** したら、少なくとも 1 回は接続アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="441c1-373">After configuring  **Project to this PC** settings, run the Connect App at least once.</span></span> <span data-ttu-id="441c1-374">(その後、Surface Hub にプロジェクトを実行するために Connect アプリを実行する必要が生じない。</span><span class="sxs-lookup"><span data-stu-id="441c1-374">(Subsequently, the Connect App does not need to be running in order to project to Surface Hub.)</span></span>

7. <span data-ttu-id="441c1-375">電源とスリープの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-375">Verify power and sleep settings.</span></span>

    - <span data-ttu-id="441c1-376">スクリーン セーバー: 15 分、(なし)、Mystify、または Blank に設定します。パスワードを要求するためのチェック ボックスがオンに設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="441c1-376">Screen Saver: 15 minutes, set to (none), Mystify or Blank; ensure the check box for requiring password is selected.</span></span>
    - <span data-ttu-id="441c1-377">画面: **2 時間後にオフにします**。</span><span class="sxs-lookup"><span data-stu-id="441c1-377">Screen: **Turn off after 2 hours**.</span></span>
    - <span data-ttu-id="441c1-378">PC:  **4 時間後にオフにします**。</span><span class="sxs-lookup"><span data-stu-id="441c1-378">PC:  **Turn off after 4 hours**.</span></span>
    
8. <span data-ttu-id="441c1-379">Windows Hello が動作しているのを確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-379">Verify Windows Hello is working.</span></span>

9. <span data-ttu-id="441c1-380">設定が無効になっている同期を確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-380">Verify sync your settings is disabled.</span></span>

10. <span data-ttu-id="441c1-381">スタートアップ アプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="441c1-381">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="441c1-382">Windows 10 をインストールして構成した後、Surface Hub 2S は他の Windows 10 デバイスと同じ方法で管理できます。</span><span class="sxs-lookup"><span data-stu-id="441c1-382">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <a name="related-topics"></a><span data-ttu-id="441c1-383">関連トピック</span><span class="sxs-lookup"><span data-stu-id="441c1-383">Related topics</span></span>

<a href="surface-hub-2s-migrate-os.md" target="_blank"> <span data-ttu-id="441c1-384">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="441c1-384">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span></a>
