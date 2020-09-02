---
title: Windows 10 Surface Hub 2 インストール後構成
description: Windows 10 Surface Hub 2 インストール後構成
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
ms.collection: M365-modern-desktop
ms.topic: article
ms.openlocfilehash: d6a1cdb2cac01b48c80e0fa4b7ccb6d3bcdb76ac
ms.sourcegitcommit: 6618e8fe05628aa8b17654584657eff0f784dbfd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "10986590"
---
# <span data-ttu-id="e6bee-104">Windows 10 Surface Hub 2 インストール後構成</span><span class="sxs-lookup"><span data-stu-id="e6bee-104">Windows 10 for Surface Hub 2 post-install configuration</span></span>

**<span data-ttu-id="e6bee-105">適用対象: Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="e6bee-105">Applies to: Surface Hub 2S</span></span>** 

<span data-ttu-id="e6bee-106">Windows 10 Pro または Enterprise に移行するためのインストールプロセスが完了したら、次の手順を実行して Surface Hub 2 のアプリと設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-106">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="e6bee-107">この手順は、カスタマイズされた大型スクリーンタッチとペンコンピューターを使用するときに最適なエクスペリエンスを確保するためにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-107">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="e6bee-108">この手順を実行すると、有線またはワイヤレスキーボード、マウスを使うと便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6bee-108">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <span data-ttu-id="e6bee-109">システム設定を構成する</span><span class="sxs-lookup"><span data-stu-id="e6bee-109">Configure system settings</span></span>

1. <span data-ttu-id="e6bee-110">デバイスのローカル管理者権限を持つアカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-110">Sign in with an account that has local administrator privileges on the device.</span></span>  
    - <span data-ttu-id="e6bee-111">Azure AD に参加しているデバイスでは、Azure AD join を実行するユーザーが自動的にローカル管理者グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-111">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="e6bee-112">Azure AD グローバル管理者と Azure AD デバイス管理者は、 [ローカル管理者でも](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin)あります。</span><span class="sxs-lookup"><span data-stu-id="e6bee-112">Azure AD global administrators and Azure AD devices administrators are [also local administrators](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin).</span></span> 
    - <span data-ttu-id="e6bee-113">コマンドプロンプトで **net localgroup の管理者** と入力すると、ローカル管理者の権限を持つアカウントを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-113">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
2. <span data-ttu-id="e6bee-114">フレンドリ名を使用してデバイスの名前を変更します。たとえば、「 **username-SHub-Desktop**」と指定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-114">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>
3. <span data-ttu-id="e6bee-115">[設定を**開始**する] を選択し  >  **Settings**  >  **Accounts**  >  **て、設定を同期**し、**同期設定**をオフにします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-115">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 
    - <span data-ttu-id="e6bee-116">ここで使用する設定は、画面上の最良のタッチエクスペリエンスを実現することを目的としているため、その他のデバイスを同期しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-116">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
4. <span data-ttu-id="e6bee-117">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-117">Reboot the device.</span></span>

## <span data-ttu-id="e6bee-118">タッチキーボードとタッチパッドを有効にする</span><span class="sxs-lookup"><span data-stu-id="e6bee-118">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="e6bee-119">タスクバーをタップしたままにするか、右クリックして、[ **タッチキーボードボタンを表示** し、 **タッチパッドボタンを表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-119">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 
    - <span data-ttu-id="e6bee-120">タッチキーボードは、ユーザーが直接入力する場合に便利です。また、仮想タッチパッドは、正確な選択、ホバー画面のヒント、右クリックの代わりに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-120">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    - <span data-ttu-id="e6bee-121">次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-121">See the following example.</span></span>

     ![タッチ設定](images/touch.png)

2. <span data-ttu-id="e6bee-123">タッチキーボードを QWERTY と浮動に設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-123">Configure the touch keyboard to QWERTY and floating.</span></span>
    1. <span data-ttu-id="e6bee-124">タスクバーのキーボードアイコンを選択してタッチキーボードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-124">Select the keyboard icon on the taskbar to show the touch keyboard.</span></span>
    2. <span data-ttu-id="e6bee-125">タッチキーボードで、左上隅にあるキーボードアイコンを選択して、キーボード設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-125">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    3. <span data-ttu-id="e6bee-126">上の行で QWERTY を有効にするには、[最後のキーボードの種類] の横にある [次へ] を選択します。これは、この大きな画面では非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="e6bee-126">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="e6bee-127">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-127">See the following examples.</span></span>

     ![キーボードの設定](images/kbd.png)

3. <span data-ttu-id="e6bee-129">ソフトキーボード設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-129">Configure the soft keyboard settings.</span></span>
    1. <span data-ttu-id="e6bee-130">**入力の設定**を検索して開く</span><span class="sxs-lookup"><span data-stu-id="e6bee-130">Search for and open **Typing settings**</span></span> 
    2. <span data-ttu-id="e6bee-131">[スペルチェック]、[入力]、[タッチキーボード] のすべてのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-131">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="e6bee-132">次の例は、トラックパッドを示しています。このオプションは、移動やオプションの選択に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-132">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="e6bee-133">Microsoft Store の検索には、スクリーンキーボードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="e6bee-133">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![トラックパッドを使用する](images/store.png)

## <span data-ttu-id="e6bee-135">Bluetooth キーボードとマウスを構成する (オプション)</span><span class="sxs-lookup"><span data-stu-id="e6bee-135">Configure bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="e6bee-136">デバイスをプライマリ Windows デバイスとして使用している場合はキーボードとマウスを接続する、または入力や精度の作業に頻繁に使用する場合は、キーボードとマウスを接続します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-136">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="e6bee-137">Surface Hub デバイスが PC に近い場合は、 [境界線のないマウス](https://aka.ms/mm) を使用して、surface HUB と pc の間でシームレスに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-137">If your Surface Hub device is near to a PC, you can use [Mouse without Borders](https://aka.ms/mm) to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="e6bee-138">詳細については、「 [ガレージを使わないで Microsoft ダウンロード](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-138">For more information, see [Microsoft download from The Garage: Mouse without Borders](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).</span></span>

## <span data-ttu-id="e6bee-139">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e6bee-139">OneDrive for Business</span></span>

<span data-ttu-id="e6bee-140">[OneDrive For business](https://docs.microsoft.com/onedrive/onedrive)を使用すると、すべての作業デバイス間でツール、ログ、その他のファイルを簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-140">Use [OneDrive for Business](https://docs.microsoft.com/onedrive/onedrive) to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="e6bee-141">OneDrive を使用すると、ノート pc、Surface Hub のデスクトップ、および Intune で管理されているモバイルデバイス間で作業ファイルを共有できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-141">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="e6bee-142">任意のデバイスでファイルを編集できます。また、ネットワーク接続されているすべてのデバイスが変更されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-142">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>
- <span data-ttu-id="e6bee-143">Surface hub SSD (128GB) のサイズを考慮してください。 Surface Hub のデスクトップデバイスで OneDrive を構成する場合は、既定の構成でファイルをオンラインのままにして、ファイルを使用するときにダウンロードするようにします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-143">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="e6bee-144">必要な場合にのみファイルをダウンロードするように OneDrive を構成するには、ファイルを使用するときに、**スペースを節約し、ファイルをダウンロード**するように**ファイルのオンデマンド**設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-144">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="e6bee-145">詳細については、「 [Windows でのファイルのオンデマンド状態の照会と設定](https://docs.microsoft.com/onedrive/files-on-demand-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-145">For more information, see [Query and set Files On-Demand states in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).</span></span>

![OneDrive の設定](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="e6bee-147">また、これらの手順を繰り返して個人用の OneDrive を構成することもできますが、ドライブの容量を節約し、必要に応じてファイルをダウンロードするだけです。</span><span class="sxs-lookup"><span data-stu-id="e6bee-147">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <span data-ttu-id="e6bee-148">SharePoint とチーム</span><span class="sxs-lookup"><span data-stu-id="e6bee-148">SharePoint and Teams</span></span>

<span data-ttu-id="e6bee-149">SharePoint と Teams のチャネルファイルは、OneDrive 同期エンジンを使って、ノート pc や Surface Hub などのデスクトップデバイスにもローカルで同期できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-149">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="e6bee-150">OneDrive 同期アプリを使用して社内のファイルをローカルドライブに同期するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e6bee-150">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="e6bee-151">SharePoint サイトに移動し、ローカルデバイスから表示または編集するファイルのトップレベルのドキュメントディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-151">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>
2. <span data-ttu-id="e6bee-152">SharePoint リボンの上部にある [ **同期** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-152">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>
3. <span data-ttu-id="e6bee-153">このサイトのポップアップで [ **開く** ] を選択し **て、Microsoft OneDrive を開こうとして**います。</span><span class="sxs-lookup"><span data-stu-id="e6bee-153">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>
4. <span data-ttu-id="e6bee-154">タスクバーの右下にある OneDrive アイコンを選択して、SharePoint ファイルがローカルドライブと同期されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-154">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>
5. <span data-ttu-id="e6bee-155">ファイルをオンラインのままにして、使用しているときにのみファイルをダウンロードするように構成が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-155">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>
    1. <span data-ttu-id="e6bee-156">エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-156">Open file explorer.</span></span>
    2. <span data-ttu-id="e6bee-157">\*\*Microsoft \ \<SharePoint Document Folder Name\> \*\*のに移動して、右選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-157">Navigate to and right select on the **Microsoft \ \<SharePoint Document Folder Name\>**.</span></span>
    3. <span data-ttu-id="e6bee-158">[ **空き容量を増やす**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-158">Select **Free up space**.</span></span>
    4. <span data-ttu-id="e6bee-159">[状態] 列には、ファイルとフォルダーの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-159">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="e6bee-160">詳細については、「 [OneDrive 同期クライアントを使用して SharePoint ファイルを同期する](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-160">For more information, see [Sync SharePoint files with the OneDrive sync client](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).</span></span>
6. <span data-ttu-id="e6bee-161">Teams のチャネルファイルは SharePoint サイトに保存され、バージョン履歴やローカルデスクトップデバイスとの同期など、同じ SharePoint ドキュメントのすべての機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-161">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="e6bee-162">Teams のチャネルファイルを同期するには:</span><span class="sxs-lookup"><span data-stu-id="e6bee-162">To sync Teams Channel files:</span></span>
    1. <span data-ttu-id="e6bee-163">関心のある Teams チャネルに移動し、上部にある [ **ファイル** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-163">Navigate to the Teams Channel of interest and select on the **Files** tab at the top.</span></span> <span data-ttu-id="e6bee-164">次に、[**同期**] を選びます。ファイルが同期を開始し、\*\*デスクトップの \ Microsoft \ \<name of the Teams Channel\> \*\*のファイルエクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-164">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Microsoft \ \<name of the Teams Channel\>**.</span></span>
    2. <span data-ttu-id="e6bee-165">SharePoint サイトの同期に使用したのと同じ手順を使用して、ファイルをクラウドに残し、使用するときにのみダウンロードすることができます。そのためには、Teams のチャネル名でエクスプローラーをタップしたままにするか、右クリックして、[ **空き容量**を増やす] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-165">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <span data-ttu-id="e6bee-166">Surface Hub ペンをペアリングする</span><span class="sxs-lookup"><span data-stu-id="e6bee-166">Pair the Surface Hub pen</span></span>

<span data-ttu-id="e6bee-167">ペンデバイスをペアリングするには:</span><span class="sxs-lookup"><span data-stu-id="e6bee-167">To pair the pen device:</span></span>

1. <span data-ttu-id="e6bee-168">[ **Start**  >  **設定**  >  **デバイス**の開始] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-168">Select **Start** > **Settings** > **Devices**.</span></span>
2. <span data-ttu-id="e6bee-169">[ **Bluetooth またはその他のデバイスの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-169">Select **Add Bluetooth or other device**.</span></span>
3. <span data-ttu-id="e6bee-170">[ **Bluetooth**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-170">Choose **Bluetooth**.</span></span>
4. <span data-ttu-id="e6bee-171">[ペンの尾] ボタンを外し、シェイクしてバッテリ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-171">Remove the pen tail button and shake to disconnect the battery connection.</span></span>
5. <span data-ttu-id="e6bee-172">キャップをもう一度オンにして、ペアリング LED が点滅するまでキャップを長押しします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-172">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>
6. <span data-ttu-id="e6bee-173">Surface Hub Bluetooth の設定で、[ **Surface hub 2 ペン**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-173">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>
7. <span data-ttu-id="e6bee-174">ペアリング操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-174">Complete the pairing operation.</span></span> 
8. <span data-ttu-id="e6bee-175">ペアリングに失敗した場合は、もう一度ペンをペアリングしてみてください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-175">If the pairing is not successful, attempt to pair the pen again.</span></span> <span data-ttu-id="e6bee-176">必要に応じて、デバイスを再起動してから、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-176">If necessary, reboot the device and then try again.</span></span>

## <span data-ttu-id="e6bee-177">カメラの設定</span><span class="sxs-lookup"><span data-stu-id="e6bee-177">Camera configuration</span></span>

<span data-ttu-id="e6bee-178">カメラは、デバイスの一番上または横側にマウントできます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-178">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="e6bee-179">カメラを1つの位置に配置して、カートの代わりにデスクトップスタンドでハブを使っている場合、またはハブに近接している場合は、カメラのアングルを最適化します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-179">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="e6bee-180">カメラは自動的に回転しないため、カメラを手動で回転させるには、2mm の16進数のキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="e6bee-180">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="e6bee-181">カメラのサイドマウントとカメラの回転を手動で行う方法について詳しくは、「 [Surface Hub 2s camera lens の向き](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-181">For more information on how to side-mount the camera and rotate the camera manually, see [Surface Hub 2S camera lens orientation](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).</span></span>

## <span data-ttu-id="e6bee-182">Windows Hello の構成</span><span class="sxs-lookup"><span data-stu-id="e6bee-182">Windows Hello configuration</span></span>

<span data-ttu-id="e6bee-183">Windows 10 Enterprise を実行する Surface Hub 2S では、すべての Win32 デスクトップアプリケーションと生体認証の Windows Hello オプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-183">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="e6bee-184">Surface Hub 2 指紋リーダーアクセサリは、デバイスの任意の USB C ポートに接続できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-184">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

> <i><span data-ttu-id="e6bee-185">Surface Hub 2 の指紋リーダがまもなく購入できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e6bee-185">The Surface Hub 2 Fingerprint Reader will be available for purchase soon.</span></span> <span data-ttu-id="e6bee-186">購入方法などの詳細については、このページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-186">Please check back on this page for more information including how to purchase.</span></span></i>

<span data-ttu-id="e6bee-187">指紋リーダーを挿入した後で、[設定の**開始**] を選び、  >  **Settings**  >  **Accounts**  >  **Sign-in options**  >  **Windows Hello 指紋**を登録します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-187">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="e6bee-188">表面認識のために Windows Hello 認定デバイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-188">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="e6bee-189">Surface Hub 2S camera は、Windows Hello フェイス認識をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e6bee-189">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <span data-ttu-id="e6bee-190">タスクバーのロック画面ショートカットアイコンを有効にする</span><span class="sxs-lookup"><span data-stu-id="e6bee-190">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="e6bee-191">Windows-L キーボードショートカットと同様のタッチスクリーンロックを有効にするアイコンをタスクバーに追加するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e6bee-191">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="e6bee-192">デスクトップ上でタップして長押しするか、右クリックし、[**新しい**  >  **ショートカット**を  >  **開く**] の横にある [  >  **Desktop**  >  **OK]** を選択し  >  **Next**ます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-192">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>
2.  <span data-ttu-id="e6bee-193">[ **マイコンピューターのロック**] などのショートカットの名前を入力し、[ **完了**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-193">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>
3.  <span data-ttu-id="e6bee-194">デスクトップで新しく作成したショートカットを右クリックするかタップしたままにして、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-194">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="e6bee-195">[ **ショートカット** ] タブの [ **ターゲット** ] フィールドに、次のように入力します: **Rundll32.exe User32.dll、lockworkstation**</span><span class="sxs-lookup"><span data-stu-id="e6bee-195">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>
4.  <span data-ttu-id="e6bee-196">[ **アイコンの変更** ] ボタンを選択し、[ **C:\Windows\System32\imageres.dll** を参照して、使用するアイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-196">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 
5. <span data-ttu-id="e6bee-197">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-197">See the following example:</span></span>

    ![アイコンを選ぶ](images/lock.png)
6.  <span data-ttu-id="e6bee-199">[ **OK]** を選択してショートカットを保存します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-199">Select **OK** to save the shortcut.</span></span>
7.  <span data-ttu-id="e6bee-200">ショートカットを右クリックするか、またはタップして押し続け、[ **タスクバーにピン留め**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-200">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

## <span data-ttu-id="e6bee-201">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e6bee-201">Applications</span></span>

### <span data-ttu-id="e6bee-202">インストールされているアプリを更新する</span><span class="sxs-lookup"><span data-stu-id="e6bee-202">Update installed apps</span></span>

<span data-ttu-id="e6bee-203">インストールされているすべてのストアアプリを更新するには:</span><span class="sxs-lookup"><span data-stu-id="e6bee-203">To update all installed Store apps:</span></span>

1. <span data-ttu-id="e6bee-204">Microsoft Store アプリを開き、右上隅にある [ **その他** ] の省略記号を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-204">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>
2. <span data-ttu-id="e6bee-205">[ **ダウンロードと更新**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-205">Select **Downloads and updates**.</span></span>
2. <span data-ttu-id="e6bee-206">[ **更新内容の取得**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-206">Select **Get updates**.</span></span>

### <span data-ttu-id="e6bee-207">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="e6bee-207">Microsoft Whiteboard</span></span>

<span data-ttu-id="e6bee-208">Microsoft ホワイトボードをインストールするには:</span><span class="sxs-lookup"><span data-stu-id="e6bee-208">To install the Microsoft Whiteboard:</span></span>

1. <span data-ttu-id="e6bee-209">タスクバーの右下にある **Windows Ink ワークスペース** アイコンの ![ インクワークスペースを選択して、 ](images/ink.png) **ホワイトボード**をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-209">Select the **Windows Ink Workspace** icon ![Ink workspace](images/ink.png) on the lower right of the taskbar and download **Whiteboard**.</span></span>

<span data-ttu-id="e6bee-210">または、Microsoft Store からホワイトボードをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-210">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="e6bee-211">Microsoft Store アプリを開いて、 **ホワイトボード**を検索します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-211">Open Microsoft Store app and search for **Whiteboard**.</span></span>
2. <span data-ttu-id="e6bee-212">[サインインしてデバイス間で使用 **する] を選択します** 。</span><span class="sxs-lookup"><span data-stu-id="e6bee-212">Choose **No thanks** to sign in and use across devices.</span></span>
3. <span data-ttu-id="e6bee-213">ホワイトボードをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-213">Pin Whiteboard to the taskbar.</span></span>

### <span data-ttu-id="e6bee-214">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="e6bee-214">Surface app</span></span>

1. <span data-ttu-id="e6bee-215">Microsoft Store で、 **Surface**を検索します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-215">In the Microsoft Store, search for **Surface**.</span></span>
2. <span data-ttu-id="e6bee-216">**[利用可能な**フィルターを**すべてのデバイス**に設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-216">Set the **Available on** filter to **All devices**.</span></span>
3. <span data-ttu-id="e6bee-217">**Surface**アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-217">Install the **Surface** app.</span></span> <span data-ttu-id="e6bee-218">これは最初に表示されているアプリです。</span><span class="sxs-lookup"><span data-stu-id="e6bee-218">This should be the first app listed.</span></span> <span data-ttu-id="e6bee-219">アプリをインストールするために、MSA をストアに関連付ける必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6bee-219">You might need to associate your MSA to the Store in order to install the app.</span></span>
4. <span data-ttu-id="e6bee-220">**Surface**アプリをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-220">Pin the **Surface** app to taskbar.</span></span>

### <span data-ttu-id="e6bee-221">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="e6bee-221">Snip & Sketch</span></span>

1. <span data-ttu-id="e6bee-222">**切り取り領域 & スケッチ**アプリを開き、タスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-222">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>
2. <span data-ttu-id="e6bee-223">右上にある省略記号 (...) を選択し、[ **設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-223">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>
3. <span data-ttu-id="e6bee-224">[ **設定**] で、 **[自動コピー**] を [クリップボード] に、[ **切り取り領域の保存**]、および [複数の **ウィンドウ** を表示] (オプション) をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-224">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <span data-ttu-id="e6bee-225">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="e6bee-225">Microsoft Office</span></span>

1. <span data-ttu-id="e6bee-226">[Office ポータル](https://portal.office.com/account#installs)を開き、目的のアプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-226">Open the [Office Portal](https://portal.office.com/account#installs) and install your desired applications.</span></span>
2. <span data-ttu-id="e6bee-227">目的の Office アプリケーションをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-227">Pin desired Office applications to the taskbar.</span></span>
3. <span data-ttu-id="e6bee-228">Outlook がインストールされている場合は、過去2週間のキャッシュのみを保存するように Outlook OST を設定してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-228">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="e6bee-229">これにより、ディスク使用量とセットアップ時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-229">This will vastly reduce disk usage and setup time.</span></span>
    - <span data-ttu-id="e6bee-230">[**ファイル**  >  **アカウント設定**] を選択して、アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-230">Select **File** > **Account Settings** and select your account.</span></span>
    - <span data-ttu-id="e6bee-231">[ **変更** ] を選択し、[ **Exchange キャッシュモード** を14日間に使用する] のスライダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-231">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <span data-ttu-id="e6bee-232">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e6bee-232">Microsoft Teams</span></span>

1. <span data-ttu-id="e6bee-233">[Microsoft Teams](https://teams.microsoft.com/downloads)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-233">Download and install [Microsoft Teams](https://teams.microsoft.com/downloads).</span></span>
2. <span data-ttu-id="e6bee-234">アプリケーションを自動起動するように設定を構成します (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="e6bee-234">Configure settings to Auto-start application (optional).</span></span>
3. <span data-ttu-id="e6bee-235">チームをタスクバーに固定する。</span><span class="sxs-lookup"><span data-stu-id="e6bee-235">Pin Teams to the taskbar.</span></span>
4. <span data-ttu-id="e6bee-236">集中を回避するために、デバイスで Teams の通知を減らすことを検討してください (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="e6bee-236">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

  ![Teams の通知](images/teams.png)

### <span data-ttu-id="e6bee-238">アプリの接続</span><span class="sxs-lookup"><span data-stu-id="e6bee-238">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6bee-239">Windows 10 バージョン2004以降では、Miracast を使用するワイヤレスプロジェクション用の Connect アプリは既定ではインストールされていませんが、オプションの機能として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-239">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="e6bee-240">アプリをインストールするには、[**設定**] アプリのオプション機能を選び、  >  **Apps**  >  **Optional features**  >  **機能を追加**してから、**ワイヤレスディスプレイ**アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-240">To install the app, select on **Settings** > **Apps** > **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

1. <span data-ttu-id="e6bee-241">**Connect**を検索します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-241">Search for **Connect**.</span></span>
2. <span data-ttu-id="e6bee-242">アプリを開き、アプリを閉じます (アプリが少なくとも1回実行されていない場合、**この PC へのプロジェクト** が機能しないことがあります)。</span><span class="sxs-lookup"><span data-stu-id="e6bee-242">Open the app and then close it (**Project to this PC** might not work unless the app has been run at least once).</span></span>
3. <span data-ttu-id="e6bee-243">タップして長押しするか、右クリックしてタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-243">Tap and hold or right-click to pin to taskbar.</span></span>
4. <span data-ttu-id="e6bee-244">**プロジェクション設定**を検索します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-244">Search for **Projection settings**.</span></span>
5. <span data-ttu-id="e6bee-245">**一部の Windows と Android デバイスでは、[OK] という音声が表示**された場合は、デバイスが企業ネットワーク上にない場合は、[**利用可能な場所**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-245">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose **Available everywhere** if the device is not on a corporate network.</span></span> <span data-ttu-id="e6bee-246">それ以外の場合は、 **セキュリティで保護されたネットワーク上のどこ**でも利用できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-246">Otherwise, you can choose **Available everywhere on secure networks**.</span></span>
6. <span data-ttu-id="e6bee-247">[ **この PC への project**を選択する] で、[ **最初の時刻のみ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-247">Under **Ask to project to this PC**, choose **First time only**.</span></span>
7. <span data-ttu-id="e6bee-248">[ **ペアリングの PIN を必須にする**] で [ **なし**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-248">Under **Require PIN for pairing**, choose **Never**.</span></span>

<span data-ttu-id="e6bee-249">企業ネットワーク上にない場合の推奨される構成:</span><span class="sxs-lookup"><span data-stu-id="e6bee-249">Recommended configuration when not on the corporate network:</span></span>

  ![自宅での設定](images/project1.png)

<span data-ttu-id="e6bee-251">企業ネットワークで推奨される構成:</span><span class="sxs-lookup"><span data-stu-id="e6bee-251">Recommended configuration on the corporate network:</span></span>

  ![職場での設定](images/project2.png)

### <span data-ttu-id="e6bee-253">スマホ同期</span><span class="sxs-lookup"><span data-stu-id="e6bee-253">Your Phone</span></span>

<span data-ttu-id="e6bee-254">Windows 10 の既定では、 **電話** アプリはインストールされています。</span><span class="sxs-lookup"><span data-stu-id="e6bee-254">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="e6bee-255">存在しない場合は、Windows ストアからインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-255">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="e6bee-256">アプリのセットアップについては、「 [Windows 10 で電話を設定する方法」および「PC とスマートフォンの間でデータを同期する方法](https://www.windowscentral.com/how-set-your-phone-windows-10)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-256">For information about setting up the app, see [How to set up Your Phone on Windows 10 and sync data between your PC and phone](https://www.windowscentral.com/how-set-your-phone-windows-10).</span></span> <span data-ttu-id="e6bee-257">また [、Windows 10 の電話アプリに関する一般的な問題を解決する方法に](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10)ついても説明します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-257">Also see [How to fix common problems with Your Phone app on Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).</span></span>

### <span data-ttu-id="e6bee-258">スーパーデザインのゾーン</span><span class="sxs-lookup"><span data-stu-id="e6bee-258">Super Fancy Zones</span></span>

<span data-ttu-id="e6bee-259">**スーパーの装飾** 的なゾーンにより、ユーザーはウィンドウを配置して画面領域を最大化できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-259">**Super Fancy Zones** helps users arrange windows to maximize screen real estate.</span></span> <span data-ttu-id="e6bee-260">これは、GitHub の [powertoy](https://github.com/microsoft/PowerToys/releases) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6bee-260">It is now included in [PowerToys](https://github.com/microsoft/PowerToys/releases) on GitHub.</span></span>

### <span data-ttu-id="e6bee-261">Edge Chromium browser</span><span class="sxs-lookup"><span data-stu-id="e6bee-261">Edge Chromium browser</span></span>

<span data-ttu-id="e6bee-262">新しい [Edge Chromium browser](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-262">Download and install the new [Edge Chromium browser](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).</span></span>

## <span data-ttu-id="e6bee-263">追加設定</span><span class="sxs-lookup"><span data-stu-id="e6bee-263">Additional settings</span></span>

### <span data-ttu-id="e6bee-264">[ペンの尾] でホワイトボードを起動する</span><span class="sxs-lookup"><span data-stu-id="e6bee-264">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="e6bee-265">[ **ペン** ] を検索し、[ペン] を選択し **& Windows Ink の設定**を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-265">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>
2. <span data-ttu-id="e6bee-266">ページの下部にある [ペンの**ショートカット**] で、[ **Microsoft ホワイトボード**の**1 回] を選択**します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-266">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <span data-ttu-id="e6bee-267">電源とスリープの設定</span><span class="sxs-lookup"><span data-stu-id="e6bee-267">Power and sleep settings</span></span>

1. <span data-ttu-id="e6bee-268">[設定の**開始**] を選び  >  **Settings**  >  **System**  >  、**スリープ &** します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-268">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>
2. <span data-ttu-id="e6bee-269">[電源モード] スライダーを [ **最適なパフォーマンス**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-269">Set the power mode slider to **Best performance**.</span></span>
3. <span data-ttu-id="e6bee-270">画面とスリープの値を好みに合わせて構成します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-270">Configure screen and sleep values to your preference.</span></span>

### <span data-ttu-id="e6bee-271">スクリーンセーバー</span><span class="sxs-lookup"><span data-stu-id="e6bee-271">Screen saver</span></span>

1. <span data-ttu-id="e6bee-272">**ロック画面**を検索し、**ロック画面の設定**を開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-272">Search for **Lock Screen** and open **Lock screen settings**.</span></span>
2. <span data-ttu-id="e6bee-273">**画面のタイムアウト設定**と**スクリーンセーバーの設定**を好みに合わせて構成します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-273">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span>

### <span data-ttu-id="e6bee-274">ストレージ センサー</span><span class="sxs-lookup"><span data-stu-id="e6bee-274">Storage Sense</span></span>

<span data-ttu-id="e6bee-275">Surface Hub 2 にはローカルストレージ用に 128GB SSD が搭載されているため、通常の使用時に記憶域の節約の測定値を使用することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6bee-275">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="e6bee-276">記憶域の感覚を構成するには:</span><span class="sxs-lookup"><span data-stu-id="e6bee-276">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="e6bee-277">[**システム設定**] の下にある [**記憶域の設定**] を検索します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-277">Search for **storage settings**, which is found under **System settings**.</span></span>
2.  <span data-ttu-id="e6bee-278">[ **設定**] で、[ **ストレージの感覚を有効** にする] を選択して、[ **記憶域** の設定] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-278">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>
3.  <span data-ttu-id="e6bee-279">ストレージ **の**感覚をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-279">Turn Storage Sense to **On**.</span></span>
4.  <span data-ttu-id="e6bee-280">[ **記憶域の構成] または [今すぐ実行** ] を選択して、ファイルを可能な限りオンラインのままにする (ドライブの空き領域が限られているため) ように設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-280">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="e6bee-281">推奨される設定:</span><span class="sxs-lookup"><span data-stu-id="e6bee-281">Recommended settings:</span></span>
- <span data-ttu-id="e6bee-282">ストレージを実行するには、毎日。</span><span class="sxs-lookup"><span data-stu-id="e6bee-282">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="e6bee-283">自分のアプリで使用されていない一時ファイル (少なくとも14日間) を削除します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-283">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="e6bee-284">[自分のダウンロード] フォルダーに含まれているファイルがある場合は、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-284">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="e6bee-285">OneDrive: コンテンツはオンラインになります。数が30日以上開かれていない場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-285">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <span data-ttu-id="e6bee-286">タブレット モード</span><span class="sxs-lookup"><span data-stu-id="e6bee-286">Tablet mode</span></span>

<span data-ttu-id="e6bee-287">アクセシビリティが必要な場合は、タブレットモードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-287">Turn on Tablet mode if desired for accessibility needs.</span></span>

### <span data-ttu-id="e6bee-288">Power management</span><span class="sxs-lookup"><span data-stu-id="e6bee-288">Power management</span></span>

> [!NOTE]
> <span data-ttu-id="e6bee-289">次の手順を実行する前に、IT 部門に問い合わせて、Surface Hub 2S デバイスをグローバルな power management ポリシーから除外するように依頼してください。</span><span class="sxs-lookup"><span data-stu-id="e6bee-289">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="e6bee-290">一部の電源管理設定では、プレゼンス検出機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-290">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="e6bee-291">**ソフトウェアセンター**を検索して開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-291">Search for **Software Center** and open it.</span></span>
2. <span data-ttu-id="e6bee-292">ナビゲーションウィンドウで [ **オプション** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-292">Select **Options** in the navigation pane.</span></span>
3. <span data-ttu-id="e6bee-293">[ **Power management** ] セクションを展開し、[ **このコンピューターに IT 部門の電源設定を適用しない**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-293">Expand the **Power management** section and select the checkbox **Do not apply power settings from my IT department to this computer**.</span></span>

  ![ソフトウェアの設定](images/soft-cntr.png)

### <span data-ttu-id="e6bee-295">サウンド設定</span><span class="sxs-lookup"><span data-stu-id="e6bee-295">Sound settings</span></span>

1. <span data-ttu-id="e6bee-296">[ **サウンドの設定** ] を検索して、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-296">Search for **Sounds settings** and open this page.</span></span>
2. <span data-ttu-id="e6bee-297">右側の [ **サウンドコントロールパネル** ] を選択し、[ **サウンド** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-297">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>
3. <span data-ttu-id="e6bee-298">[ **プログラムイベント** ] で、 **デバイス接続** と **デバイスの切断** を [ **なし**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-298">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <span data-ttu-id="e6bee-299">無音通知</span><span class="sxs-lookup"><span data-stu-id="e6bee-299">Silence notifications</span></span>

1. <span data-ttu-id="e6bee-300">**フォーカスアシスト**を検索して、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-300">Search for **Focus assist** and open this page.</span></span>
2. <span data-ttu-id="e6bee-301">[ **アラームのみ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-301">Select **Alarms Only**.</span></span> <span data-ttu-id="e6bee-302">これにより、一定の通知ポップアップを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-302">This will avoid constant notification flyouts.</span></span>

### <span data-ttu-id="e6bee-303">ディスク クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="e6bee-303">Disk Cleanup</span></span>

1. <span data-ttu-id="e6bee-304">**ディスククリーンアップ**を検索して、このアプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-304">Search for **Disk Cleanup** and open this app.</span></span>
2. <span data-ttu-id="e6bee-305">[ **削除するファイル**] で、削除するファイルを選びます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-305">Under **Files to delete**, select the files you wish to delete.</span></span> 
3. <span data-ttu-id="e6bee-306">また、[ **システムファイルのクリーンアップ**] も選択します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-306">Also select **Clean up system files**.</span></span>

## <span data-ttu-id="e6bee-307">完了して確認する</span><span class="sxs-lookup"><span data-stu-id="e6bee-307">Complete and verify</span></span>

1. <span data-ttu-id="e6bee-308">すべての Windows 更新プログラムをスキャンしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="e6bee-308">Scan for and install all Windows Updates.</span></span>
2. <span data-ttu-id="e6bee-309">グループポリシーの更新</span><span class="sxs-lookup"><span data-stu-id="e6bee-309">Update Group Policy</span></span>
    1. <span data-ttu-id="e6bee-310">昇格されたコマンドプロンプトで、「 **gpupdate/force/boot/wait: 0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-310">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
3. <span data-ttu-id="e6bee-311">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-311">Reboot the device.</span></span>
4. <span data-ttu-id="e6bee-312">タスクバーのアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-312">Verify taskbar apps.</span></span>
    - <span data-ttu-id="e6bee-313">アプリを接続する</span><span class="sxs-lookup"><span data-stu-id="e6bee-313">Connect App</span></span>
    - <span data-ttu-id="e6bee-314">ロックアイコン</span><span class="sxs-lookup"><span data-stu-id="e6bee-314">Lock Icon</span></span>
    - <span data-ttu-id="e6bee-315">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="e6bee-315">Snip & Sketch</span></span>
    - <span data-ttu-id="e6bee-316">Teams (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="e6bee-316">Teams (if applicable)</span></span>
    - <span data-ttu-id="e6bee-317">Office アプリ (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="e6bee-317">Office Apps (if applicable)</span></span>
    - <span data-ttu-id="e6bee-318">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="e6bee-318">Surface App</span></span>
    - <span data-ttu-id="e6bee-319">ホワイトボード</span><span class="sxs-lookup"><span data-stu-id="e6bee-319">Whiteboard</span></span>
5. <span data-ttu-id="e6bee-320">プレゼンス検出を確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-320">Verify presence detection.</span></span>
    - <span data-ttu-id="e6bee-321">プレゼンス検出はシステムトレイに緑のアイコンとして表示される</span><span class="sxs-lookup"><span data-stu-id="e6bee-321">Presence detection will be a green icon in the system tray</span></span>
6. <span data-ttu-id="e6bee-322">[この PC へのプロジェクション] が接続アプリで有効になっていることを確認します (アプリケーションは接続する前に実行する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="e6bee-322">Verify projecting to this PC is enabled with the Connect App (the application does not need to be running before connecting).</span></span>
7. <span data-ttu-id="e6bee-323">電源とスリープの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-323">Verify power and sleep settings.</span></span>
    - <span data-ttu-id="e6bee-324">スクリーンセーバー:15 分、[なし]、[Mystify]、または [空白] に設定します。[パスワードを要求する] チェックボックスがオンになっている</span><span class="sxs-lookup"><span data-stu-id="e6bee-324">Screen Saver: 15 minutes, set to (none), Mystify or Blank; check box for requiring password is checked</span></span>
    - <span data-ttu-id="e6bee-325">画面: 2 時間</span><span class="sxs-lookup"><span data-stu-id="e6bee-325">Screen: 2 hours</span></span>
    - <span data-ttu-id="e6bee-326">PC: 4 時間</span><span class="sxs-lookup"><span data-stu-id="e6bee-326">PC: 4 hours</span></span>
8. <span data-ttu-id="e6bee-327">Windows Hello が動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-327">Verify Windows Hello is working.</span></span>
9. <span data-ttu-id="e6bee-328">電源設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-328">Verify power settings.</span></span>
10. <span data-ttu-id="e6bee-329">同期設定が無効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-329">Verify sync your settings is disabled.</span></span>
11. <span data-ttu-id="e6bee-330">スタートアップアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6bee-330">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="e6bee-331">Windows 10 をインストールして構成した後、Surface Hub 2S は、他の Windows 10 デバイスと同じように管理できます。</span><span class="sxs-lookup"><span data-stu-id="e6bee-331">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <span data-ttu-id="e6bee-332">関連トピック</span><span class="sxs-lookup"><span data-stu-id="e6bee-332">Related topics</span></span>

[<span data-ttu-id="e6bee-333">Surface Hub 2 で Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="e6bee-333">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>](surface-hub-2s-migrate-os.md)
