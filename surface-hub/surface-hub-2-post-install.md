---
title: Surface Hub 2 で Windows 10 Pro または Enterprise を構成する
description: この記事では、カスタマイズされた大型スクリーンタッチとペンコンピューターを使用する際の最適なエクスペリエンスを実現するための推奨事項について説明します。
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
ms.date: 11/03/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: b86776b56e892c34ea8b5abbc55d5c48723a5f9e
ms.sourcegitcommit: 3ca1d1bc77452acca914d0af03e252ee260ebf1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "11154129"
---
# <span data-ttu-id="2bd1f-104">Surface Hub 2 で Windows 10 Pro または Enterprise を構成する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

<span data-ttu-id="2bd1f-105">Windows 10 Pro または Enterprise に移行するためのインストールプロセスが完了したら、次の手順を実行して Surface Hub 2 のアプリと設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-105">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="2bd1f-106">この手順は、カスタマイズされた大型スクリーンタッチとペンコンピューターを使用するときに最適なエクスペリエンスを確保するためにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-106">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="2bd1f-107">この手順を実行すると、有線またはワイヤレスキーボード、マウスを使うと便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-107">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <span data-ttu-id="2bd1f-108">システム設定を構成する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-108">Configure system settings</span></span>

1. <span data-ttu-id="2bd1f-109">デバイスのローカル管理者権限を持つアカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-109">Sign in with an account that has local administrator privileges on the device.</span></span>  

    - <span data-ttu-id="2bd1f-110">Azure AD に参加しているデバイスでは、Azure AD join を実行するユーザーが自動的にローカル管理者グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-110">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="2bd1f-111">Azure AD グローバル管理者と Azure AD デバイス管理者は、 <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> ローカル管理者でも </a> あります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-111">Azure AD global administrators and Azure AD devices administrators are <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank">also local administrators</a>.</span></span> 
    
    - <span data-ttu-id="2bd1f-112">コマンドプロンプトで **net localgroup の管理者** と入力すると、ローカル管理者の権限を持つアカウントを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-112">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
    
2. <span data-ttu-id="2bd1f-113">フレンドリ名を使用してデバイスの名前を変更します。たとえば、「 **username-SHub-Desktop**」と指定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-113">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>

3. <span data-ttu-id="2bd1f-114">[設定を**開始**する] を選択し  >  **Settings**  >  **Accounts**  >  **て、設定を同期**し、**同期設定**をオフにします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-114">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 

    - <span data-ttu-id="2bd1f-115">ここで使用する設定は、画面上の最良のタッチエクスペリエンスを実現することを目的としているため、その他のデバイスを同期しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-115">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
    
4. <span data-ttu-id="2bd1f-116">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-116">Restart the device.</span></span>

## <span data-ttu-id="2bd1f-117">タッチキーボードとタッチパッドを有効にする</span><span class="sxs-lookup"><span data-stu-id="2bd1f-117">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="2bd1f-118">タスクバーをタップしたままにするか、右クリックして、[ **タッチキーボードボタンを表示** し、 **タッチパッドボタンを表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-118">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 

    - <span data-ttu-id="2bd1f-119">タッチキーボードは、ユーザーが直接入力する場合に便利です。また、仮想タッチパッドは、正確な選択、ホバー画面のヒント、右クリックの代わりに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-119">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    
    - <span data-ttu-id="2bd1f-120">次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-120">See the following example.</span></span>

      ![タッチ設定](images/touch.png)

2. <span data-ttu-id="2bd1f-122">タッチキーボードを QWERTY と浮動に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-122">Configure the touch keyboard to QWERTY and floating.</span></span>

    1. <span data-ttu-id="2bd1f-123">タスクバーの **キーボード** アイコンを選択してタッチキーボードを表示します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-123">Select the **Keyboard** icon on the taskbar to show the touch keyboard.</span></span>
    
    2. <span data-ttu-id="2bd1f-124">タッチキーボードで、左上隅にあるキーボードアイコンを選択して、キーボード設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-124">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    
    3. <span data-ttu-id="2bd1f-125">上の行で QWERTY を有効にするには、[最後のキーボードの種類] の横にある [次へ] を選択します。これは、この大きな画面では非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-125">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="2bd1f-126">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-126">See the following examples.</span></span>

       ![キーボードの設定](images/kbd.png)
 
3. <span data-ttu-id="2bd1f-128">ソフトキーボード設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-128">Configure the soft keyboard settings.</span></span>

    1. <span data-ttu-id="2bd1f-129">タッチキーボードの **設定** アイコンを選択するか、 **入力設定**を検索して開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-129">Select the **Settings** icon on the touch keyboard or search for and open **Typing settings**.</span></span>
    
       ![ソフトキーボードの設定](images/sh2-softkeyboard.png)

    1. <span data-ttu-id="2bd1f-131">[スペルチェック]、[入力]、[タッチキーボード] のすべてのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-131">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="2bd1f-132">次の例は、トラックパッドを示しています。このオプションは、移動やオプションの選択に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-132">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="2bd1f-133">Microsoft Store の検索には、スクリーンキーボードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-133">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![トラックパッドを使用する](images/store.png)

## <span data-ttu-id="2bd1f-135">Bluetooth キーボードとマウスを構成する (オプション)</span><span class="sxs-lookup"><span data-stu-id="2bd1f-135">Configure bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="2bd1f-136">デバイスをプライマリ Windows デバイスとして使用している場合はキーボードとマウスを接続する、または入力や精度の作業に頻繁に使用する場合は、キーボードとマウスを接続します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-136">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="2bd1f-137">Surface Hub デバイスが PC に近い場合は、 <a href="https://aka.ms/mm" target="_blank"> 境界線のないマウスを使用して、 </a> surface HUB と pc の間でシームレスに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-137">If your Surface Hub device is near to a PC, you can use <a href="https://aka.ms/mm" target="_blank"> Mouse without Borders</a> to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="2bd1f-138">詳細については、「 <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> ガレージを使わないで Microsoft ダウンロード」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-138">For more information, see <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> Microsoft download from The Garage: Mouse without Borders.</span></span> </a>

## <span data-ttu-id="2bd1f-139">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="2bd1f-139">OneDrive for Business</span></span>

<span data-ttu-id="2bd1f-140"><a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank">OneDrive For business </a> を使用すると、すべての作業デバイス間でツール、ログ、その他のファイルを簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-140">Use <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business</a> to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="2bd1f-141">OneDrive を使用すると、ノート pc、Surface Hub のデスクトップ、および Intune で管理されているモバイルデバイス間で作業ファイルを共有できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-141">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="2bd1f-142">任意のデバイスでファイルを編集できます。また、ネットワーク接続されているすべてのデバイスが変更されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-142">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>

- <span data-ttu-id="2bd1f-143">Surface hub SSD (128GB) のサイズを考慮してください。 Surface Hub のデスクトップデバイスで OneDrive を構成する場合は、既定の構成でファイルをオンラインのままにして、ファイルを使用するときにダウンロードするようにします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-143">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="2bd1f-144">必要な場合にのみファイルをダウンロードするように OneDrive を構成するには、ファイルを使用するときに、**スペースを節約し、ファイルをダウンロード**するように**ファイルのオンデマンド**設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-144">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="2bd1f-145">詳細については、「 <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Windows でのファイルのオンデマンド状態の照会と設定」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-145">For more information, see <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Query and set Files On-Demand states in Windows</a>.</span></span>

![OneDrive の設定](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="2bd1f-147">また、これらの手順を繰り返して個人用の OneDrive を構成することもできますが、ドライブの容量を節約し、必要に応じてファイルをダウンロードするだけです。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-147">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <span data-ttu-id="2bd1f-148">SharePoint とチーム</span><span class="sxs-lookup"><span data-stu-id="2bd1f-148">SharePoint and Teams</span></span>

<span data-ttu-id="2bd1f-149">SharePoint と Teams のチャネルファイルは、OneDrive 同期エンジンを使って、ノート pc や Surface Hub などのデスクトップデバイスにもローカルで同期できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-149">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="2bd1f-150">OneDrive 同期アプリを使用して社内のファイルをローカルドライブに同期するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-150">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="2bd1f-151">SharePoint サイトに移動し、ローカルデバイスから表示または編集するファイルのトップレベルのドキュメントディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-151">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>

2. <span data-ttu-id="2bd1f-152">SharePoint リボンの上部にある [ **同期** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-152">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>

3. <span data-ttu-id="2bd1f-153">このサイトのポップアップで [ **開く** ] を選択し **て、Microsoft OneDrive を開こうとして**います。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-153">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>

4. <span data-ttu-id="2bd1f-154">タスクバーの右下にある OneDrive アイコンを選択して、SharePoint ファイルがローカルドライブと同期されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-154">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>

5. <span data-ttu-id="2bd1f-155">ファイルをオンラインのままにして、使用しているときにのみファイルをダウンロードするように構成が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-155">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>

    1. <span data-ttu-id="2bd1f-156">エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-156">Open file explorer.</span></span>
    
    2. <span data-ttu-id="2bd1f-157">SharePoint 名に移動し、右クリックします。たとえば、 \*\*Contoso \ \<SharePoint Document Folder Name\> \*\*とします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-157">Navigate to and right click your SharePoint name; for example, **Contoso \ \<SharePoint Document Folder Name\>**.</span></span>
    
    3. <span data-ttu-id="2bd1f-158">[ **空き容量を増やす**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-158">Select **Free up space**.</span></span>
    
    4. <span data-ttu-id="2bd1f-159">[状態] 列には、ファイルとフォルダーの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-159">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="2bd1f-160">詳細については、「 <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> OneDrive 同期クライアントを使用して SharePoint ファイルを同期する」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-160">For more information, see <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sync SharePoint files with the OneDrive sync client</a>.</span></span>
    
6. <span data-ttu-id="2bd1f-161">Teams のチャネルファイルは SharePoint サイトに保存され、バージョン履歴やローカルデスクトップデバイスとの同期など、同じ SharePoint ドキュメントのすべての機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-161">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="2bd1f-162">Teams のチャネルファイルを同期するには:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-162">To sync Teams Channel files:</span></span>

    1. <span data-ttu-id="2bd1f-163">関心のある Teams チャネルに移動し、上部にある [ **ファイル** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-163">Navigate to the Teams Channel of interest and select the **Files** tab at the top.</span></span> <span data-ttu-id="2bd1f-164">次に、[**同期**] を選びます。ファイルの同期が開始され、\*\*デスクトップの \ Contoso \ \<name of the Teams Channel\> \*\*のファイルエクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-164">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Contoso \ \<name of the Teams Channel\>**.</span></span>
    
    2. <span data-ttu-id="2bd1f-165">SharePoint サイトの同期に使用したのと同じ手順を使用して、ファイルをクラウドに残し、使用するときにのみダウンロードすることができます。そのためには、Teams のチャネル名でエクスプローラーをタップしたままにするか、右クリックして、[ **空き容量**を増やす] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-165">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <span data-ttu-id="2bd1f-166">Surface Hub のペンの設定</span><span class="sxs-lookup"><span data-stu-id="2bd1f-166">Surface Hub pen settings</span></span>

**<span data-ttu-id="2bd1f-167">Bluetooth Surface Hub ペンをペアリングする</span><span class="sxs-lookup"><span data-stu-id="2bd1f-167">Pair the Bluetooth Surface Hub Pen</span></span>**

<span data-ttu-id="2bd1f-168">ペンをペアリングして、ペンファームウェアを最新の状態に保ち、Bluetooth デバイス設定ページまたは Surface アプリでバッテリの充電情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-168">Pair the pen to keep the pen firmware up to date and get battery charge information on the Bluetooth device settings page, or in the Surface app:</span></span>

1. <span data-ttu-id="2bd1f-169">[ **Start**  >  **設定**  >  **デバイス**の開始] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-169">Select **Start** > **Settings** > **Devices**.</span></span>

2. <span data-ttu-id="2bd1f-170">[ **Bluetooth またはその他のデバイスの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-170">Select **Add Bluetooth or other device**.</span></span>

3. <span data-ttu-id="2bd1f-171">[ **Bluetooth**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-171">Choose **Bluetooth**.</span></span>

4. <span data-ttu-id="2bd1f-172">[ペンの尾] ボタンを外し、シェイクしてバッテリ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-172">Remove the pen tail button and shake to disconnect the battery connection.</span></span>

5. <span data-ttu-id="2bd1f-173">キャップをもう一度オンにして、ペアリング LED が点滅するまでキャップを長押しします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-173">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>

6. <span data-ttu-id="2bd1f-174">Surface Hub Bluetooth の設定で、[ **Surface hub 2 ペン**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-174">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>

7. <span data-ttu-id="2bd1f-175">ペアリング操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-175">Complete the pairing operation.</span></span> 

8. <span data-ttu-id="2bd1f-176">ペアリングが成功しない場合は、もう一度ペンをペアリングしてみてください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-176">If the pairing is not successful, you can attempt to pair the pen again.</span></span> <span data-ttu-id="2bd1f-177">それでもうまくいかない場合は、ホワイトボードアプリケーションでペンが機能することを確認して、バッテリが充電されているかどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-177">If that doesn't work, you can test to see if the battery is charged by verifying the pen works in the Whiteboard application.</span></span> <span data-ttu-id="2bd1f-178">見つからない場合は、バッテリーを交換して、もう一度ペンをペアリングしてみてください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-178">If not, then replace the battery and then try to pair the pen again.</span></span> <span data-ttu-id="2bd1f-179">必要に応じて、デバイスを再起動してから、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-179">If necessary, restart the device and then try again.</span></span>

<span data-ttu-id="2bd1f-180">**ペンのショートカットを設定** するSurface Hub のペンには、"テールクリック" と呼ばれるショートカットボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-180">**Set pen shortcuts** The Surface Hub pen has a shortcut button sometimes referred to as a "tail click".</span></span> <span data-ttu-id="2bd1f-181">ショートカットを構成するには、前に説明したように、最初にペンをペアリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-181">Configuring shortcuts requires you to first pair the pen, as described earlier.</span></span>

1. <span data-ttu-id="2bd1f-182">[ペン] を検索し、[ペン] を選択し **& Windows Ink の設定**を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-182">Search for Pen and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="2bd1f-183">ページの下部にある [ペンのショートカット] を選択すると、次のようなダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-183">Near the bottom of the page, select Pen shortcuts which opens the dialog box, shown here:</span></span>

   ![ペンのショートカット](images/sh2-pen-shortcuts.png)

## <span data-ttu-id="2bd1f-185">カメラの設定</span><span class="sxs-lookup"><span data-stu-id="2bd1f-185">Camera configuration</span></span>

<span data-ttu-id="2bd1f-186">カメラは、デバイスの一番上または横側にマウントできます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-186">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="2bd1f-187">カメラを1つの位置に配置して、カートの代わりにデスクトップスタンドでハブを使っている場合、またはハブに近接している場合は、カメラのアングルを最適化します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-187">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="2bd1f-188">カメラは自動的に回転しないため、カメラを手動で回転させるには、2mm の16進数のキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-188">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="2bd1f-189">カメラのサイドマウントとカメラの回転を手動で行う方法について詳しくは、「 <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> Surface Hub 2s camera lens の向き」をご覧ください </a> 。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-189">For more information on how to side-mount the camera and rotate the camera manually, see <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> Surface Hub 2S camera lens orientation</a>.</span></span>

## <span data-ttu-id="2bd1f-190">Windows Hello の構成</span><span class="sxs-lookup"><span data-stu-id="2bd1f-190">Windows Hello configuration</span></span>

<span data-ttu-id="2bd1f-191">Windows 10 Enterprise を実行する Surface Hub 2S では、すべての Win32 デスクトップアプリケーションと生体認証の Windows Hello オプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-191">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="2bd1f-192">Surface Hub 2 指紋リーダーアクセサリは、デバイスの任意の USB C ポートに接続できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-192">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

<span data-ttu-id="2bd1f-193">Surface Hub 2 の指紋リーダーを注文したり、技術仕様を表示したりするには、「(surface-hub-2-essential-add-ons.md "target =" _blank >"」を参照してください。 Windows 10 Pro および Enterprise の重要なアドオンは Surface Hub 2 にあり </a> ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-193">To order a Surface Hub 2 Fingerprint Reader or view technical specs, see (surface-hub-2-essential-add-ons.md" target="_blank">Essential add-ons for Windows 10 Pro and Enterprise on Surface Hub 2 </a>.</span></span> 

<span data-ttu-id="2bd1f-194">指紋リーダーを挿入した後で、[設定の**開始**] を選び、  >  **Settings**  >  **Accounts**  >  **Sign-in options**  >  **Windows Hello 指紋**を登録します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-194">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="2bd1f-195">表面認識のために Windows Hello 認定デバイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-195">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="2bd1f-196">Surface Hub 2S camera は、Windows Hello フェイス認識をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-196">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <span data-ttu-id="2bd1f-197">タスクバーのロック画面ショートカットアイコンを有効にする</span><span class="sxs-lookup"><span data-stu-id="2bd1f-197">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="2bd1f-198">Windows-L キーボードショートカットと同様のタッチスクリーンロックを有効にするアイコンをタスクバーに追加するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-198">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="2bd1f-199">デスクトップ上でタップして長押しするか、右クリックし、[**新しい**  >  **ショートカット**を  >  **開く**] の横にある [  >  **Desktop**  >  **OK]** を選択し  >  **Next**ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-199">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>

1.  <span data-ttu-id="2bd1f-200">[ **マイコンピューターのロック**] などのショートカットの名前を入力し、[ **完了**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-200">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>

1.  <span data-ttu-id="2bd1f-201">デスクトップで新しく作成したショートカットを右クリックするかタップしたままにして、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-201">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="2bd1f-202">[ **ショートカット** ] タブの [ **ターゲット** ] フィールドに、次のように入力します: **Rundll32.exe User32.dll、lockworkstation**</span><span class="sxs-lookup"><span data-stu-id="2bd1f-202">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>

1.  <span data-ttu-id="2bd1f-203">[ **アイコンの変更** ] ボタンを選択し、[ **C:\Windows\System32\imageres.dll** を参照して、使用するアイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-203">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 

    <span data-ttu-id="2bd1f-204">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-204">See the following example:</span></span>

    ![アイコンを選ぶ](images/lock.png)
    
1.  <span data-ttu-id="2bd1f-206">[ **OK]** を選択してショートカットを保存します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-206">Select **OK** to save the shortcut.</span></span>

1.  <span data-ttu-id="2bd1f-207">ショートカットを右クリックするか、またはタップして押し続け、[ **タスクバーにピン留め**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-207">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

1. <span data-ttu-id="2bd1f-208">タスクバーへのロックのショートカットを固定したら、デスクトップから削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-208">After you have pinned the lock shortcut to the taskbar, you can delete it from the desktop.</span></span>

## <span data-ttu-id="2bd1f-209">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2bd1f-209">Applications</span></span>

### <span data-ttu-id="2bd1f-210">インストールされているアプリを更新する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-210">Update installed apps</span></span>

<span data-ttu-id="2bd1f-211">インストールされているすべてのストアアプリを更新するには:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-211">To update all installed Store apps:</span></span>

1. <span data-ttu-id="2bd1f-212">Microsoft Store アプリを開き、右上隅にある [ **その他** ] の省略記号を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-212">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>

2. <span data-ttu-id="2bd1f-213">[**ダウンロードと更新プログラム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-213">Select **Downloads and updates**.</span></span>

2. <span data-ttu-id="2bd1f-214">[**更新プログラムを取得する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-214">Select **Get updates**.</span></span>

### <span data-ttu-id="2bd1f-215">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="2bd1f-215">Microsoft Whiteboard</span></span>

<span data-ttu-id="2bd1f-216">Microsoft ホワイトボードをインストールするには:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-216">To install the Microsoft Whiteboard:</span></span>

 - <span data-ttu-id="2bd1f-217">タスクバーの右下にある **Windows Ink ワークスペース** のアイコンを選択して、 **ホワイトボード**をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-217">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span></span>
 
   ![インクワークスペース](images/ink.png) 

<span data-ttu-id="2bd1f-219">または、Microsoft Store からホワイトボードをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-219">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="2bd1f-220">Microsoft Store アプリを開いて、 **ホワイトボード**を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-220">Open Microsoft Store app and search for **Whiteboard**.</span></span>

2. <span data-ttu-id="2bd1f-221">[サインインしてデバイス間で使用 **する] を選択します** 。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-221">Choose **No thanks** to sign in and use across devices.</span></span>

3. <span data-ttu-id="2bd1f-222">ホワイトボードをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-222">Pin Whiteboard to the taskbar.</span></span>

### <span data-ttu-id="2bd1f-223">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="2bd1f-223">Surface app</span></span>

1. <span data-ttu-id="2bd1f-224">Microsoft Store で、 **Surface**を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-224">In the Microsoft Store, search for **Surface**.</span></span>

2. <span data-ttu-id="2bd1f-225">**[利用可能な**フィルターを**すべてのデバイス**に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-225">Set the **Available on** filter to **All devices**.</span></span>

3. <span data-ttu-id="2bd1f-226">**Surface**アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-226">Install the **Surface** app.</span></span> <span data-ttu-id="2bd1f-227">これは最初に表示されているアプリです。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-227">This should be the first app listed.</span></span> <span data-ttu-id="2bd1f-228">アプリをインストールするために、MSA をストアに関連付ける必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-228">You might need to associate your MSA to the Store in order to install the app.</span></span>

4. <span data-ttu-id="2bd1f-229">**Surface**アプリをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-229">Pin the **Surface** app to taskbar.</span></span>

### <span data-ttu-id="2bd1f-230">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="2bd1f-230">Snip & Sketch</span></span>

1. <span data-ttu-id="2bd1f-231">**切り取り領域 & スケッチ**アプリを開き、タスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-231">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>

2. <span data-ttu-id="2bd1f-232">右上にある省略記号 (...) を選択し、[ **設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-232">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>

3. <span data-ttu-id="2bd1f-233">[ **設定**] で、 **[自動コピー**] を [クリップボード] に、[ **切り取り領域の保存**]、および [複数の **ウィンドウ** を表示] (オプション) をオンにします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-233">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <span data-ttu-id="2bd1f-234">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="2bd1f-234">Microsoft Office</span></span>

1. <span data-ttu-id="2bd1f-235"><a href="https://portal.office.com/account#installs" target="_blank">Office ポータルを開き、 </a> 目的のアプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-235">Open the <a href="https://portal.office.com/account#installs" target="_blank"> Office Portal</a> and install your desired applications.</span></span>

2. <span data-ttu-id="2bd1f-236">目的の Office アプリケーションをタスクバーにピン留めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-236">Pin desired Office applications to the taskbar.</span></span>

3. <span data-ttu-id="2bd1f-237">Outlook がインストールされている場合は、過去2週間のキャッシュのみを保存するように Outlook OST を設定してください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-237">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="2bd1f-238">これにより、ディスク使用量とセットアップ時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-238">This will vastly reduce disk usage and setup time.</span></span>

    - <span data-ttu-id="2bd1f-239">[**ファイル**  >  **アカウント設定**] を選択して、アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-239">Select **File** > **Account Settings** and select your account.</span></span>
    
    - <span data-ttu-id="2bd1f-240">[ **変更** ] を選択し、[ **Exchange キャッシュモード** を14日間に使用する] のスライダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-240">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <span data-ttu-id="2bd1f-241">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2bd1f-241">Microsoft Teams</span></span>

1. <span data-ttu-id="2bd1f-242">Microsoft Teams をダウンロードしてインストール <a href="https://teams.microsoft.com/downloads" target="_blank"> </a> します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-242">Download and install <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft Teams </a>.</span></span>

2. <span data-ttu-id="2bd1f-243">アプリケーションを自動起動するように設定を構成します (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-243">Configure settings to Auto-start application (optional).</span></span>

3. <span data-ttu-id="2bd1f-244">チームをタスクバーに固定する。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-244">Pin Teams to the taskbar.</span></span>

4. <span data-ttu-id="2bd1f-245">集中を回避するために、デバイスで Teams の通知を減らすことを検討してください (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-245">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

   ![Teams の通知](images/teams.png)

### <span data-ttu-id="2bd1f-247">アプリの接続</span><span class="sxs-lookup"><span data-stu-id="2bd1f-247">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bd1f-248">Windows 10 バージョン2004以降では、Miracast を使用するワイヤレスプロジェクション用の Connect アプリは既定ではインストールされていませんが、オプションの機能として使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-248">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="2bd1f-249">Windows バージョン2004以降をインストール (または更新) している場合、[設定] の [この PC へのプロジェクション] 画面に次のような画面が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-249">If you have installed (or updated to) Windows version 2004 or later, you may see the following on the Projecting to this PC screen in settings:</span></span>

![この PC へのプロジェクト](images/sh2-project.png) 


1. <span data-ttu-id="2bd1f-251">[この PC にプロジェクションする] 設定ページからアプリをインストールするには、[**オプションの機能**] を選択して機能を  >  **追加**してから、**ワイヤレスディスプレイ**アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-251">To install the app from the “Projecting to this PC” settings page, select **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

2. <span data-ttu-id="2bd1f-252">**一部の Windows および Android デバイスでは、[OK] という音声が表示**されたら、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-252">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose:</span></span>

    - <span data-ttu-id="2bd1f-253">デバイスが企業ネットワークにない場合は、**どこでも利用でき**ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-253">**Available everywhere** if the device is not on a corporate network.</span></span>
    - <span data-ttu-id="2bd1f-254">または、[ **セキュリティで保護されたネットワーク上のすべての場所**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-254">Otherwise, choose **Available everywhere on secure networks**.</span></span>
    
3. <span data-ttu-id="2bd1f-255">[ **この PC への project**を選択する] で、[ **最初の時刻のみ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-255">Under **Ask to project to this PC**, choose **First time only**.</span></span>

4. <span data-ttu-id="2bd1f-256">[ **ペアリングの PIN を必須にする**] で [ **なし**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-256">Under **Require PIN for pairing**, choose **Never**.</span></span>

5. <span data-ttu-id="2bd1f-257">次にアプリを起動し、タスクバーにピン留めして、[ **Connect**] を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-257">To then launch the app and pin it to the taskbar, search for **Connect**.</span></span>

6. <span data-ttu-id="2bd1f-258">アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-258">Open the app.</span></span> <span data-ttu-id="2bd1f-259">アプリが開いている状態で、タスクバーの [アプリの接続] アイコンを右クリックし、[ **タスクバーにピン留め**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-259">While the app is open, right-click on the Connect app icon on the taskbar, and select **pin to taskbar**.</span></span>

7. <span data-ttu-id="2bd1f-260">次に、[Connect] アプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-260">Then close the Connect app.</span></span> <span data-ttu-id="2bd1f-261">アプリが少なくとも1回実行されていない場合、**この PC へのプロジェクト**は機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-261">**Project to this PC** might not work unless the app has been run at least once.</span></span>

<span data-ttu-id="2bd1f-262">企業ネットワーク上にない場合の推奨される構成:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-262">Recommended configuration when not on the corporate network:</span></span>

![自宅での設定](images/project1.png)

<span data-ttu-id="2bd1f-264">企業ネットワークで推奨される構成:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-264">Recommended configuration on the corporate network:</span></span>

![職場での設定](images/project2.png)

### <span data-ttu-id="2bd1f-266">スマホ同期</span><span class="sxs-lookup"><span data-stu-id="2bd1f-266">Your Phone</span></span>

<span data-ttu-id="2bd1f-267">Windows 10 の既定では、 **電話** アプリはインストールされています。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-267">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="2bd1f-268">存在しない場合は、Windows ストアからインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-268">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="2bd1f-269">アプリのセットアップについては、「 <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> Windows 10 で電話を設定する方法」および「PC とスマートフォンの間でデータを同期する方法」を参照してください </a> 。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-269">For information about setting up the app, see <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> How to set up Your Phone on Windows 10 and sync data between your PC and phone</a>.</span></span> <span data-ttu-id="2bd1f-270">また <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> 、Windows 10 の電話アプリに関する一般的な問題を解決する方法についても説明し </a> ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-270">Also see <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> How to fix common problems with Your Phone app on Windows 10</a>.</span></span>

### <span data-ttu-id="2bd1f-271">スーパーデザインのゾーン</span><span class="sxs-lookup"><span data-stu-id="2bd1f-271">Super Fancy Zones</span></span>

<span data-ttu-id="2bd1f-272">**スーパーの装飾** 的なゾーンにより、ユーザーはウィンドウを配置して画面領域を最大化できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-272">**Super Fancy Zones** helps users arrange windows to maximize screen real estate.</span></span> <span data-ttu-id="2bd1f-273">これは、GitHub の powertoy に含まれてい <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> </a> ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-273">It is now included in <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys</a> on GitHub.</span></span>

### <span data-ttu-id="2bd1f-274">Edge Chromium browser</span><span class="sxs-lookup"><span data-stu-id="2bd1f-274">Edge Chromium browser</span></span>

<span data-ttu-id="2bd1f-275">新しい Edge Chromium browser をダウンロードしてインストールし <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> </a> ます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-275">Download and install the new <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank">Edge Chromium browser</a>.</span></span>


### <span data-ttu-id="2bd1f-276">Surface Hub ハードウェア診断ツール</span><span class="sxs-lookup"><span data-stu-id="2bd1f-276">Surface Hub Hardware Diagnostic tool</span></span>

<span data-ttu-id="2bd1f-277"><a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank">Surface Hub ハードウェア診断ツールは、 </a> Microsoft Store から無料で利用できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-277">The <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> Surface Hub Hardware Diagnostic tool</a> available for free from the Microsoft Store.</span></span> <span data-ttu-id="2bd1f-278">このツールは、Surface Hub が最適な状態で実行されていることを確認するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-278">The tool is designed to help you make sure your Surface Hub is performing at its best.</span></span> <span data-ttu-id="2bd1f-279">このアプリには、ファームウェアが最新であり、正しく構成されているかどうかを判断するテストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-279">It contains tests to determine if your firmware is up to date and configured correctly.</span></span> <span data-ttu-id="2bd1f-280">対話型テストを利用すると、重要な機能が予期したとおりに動作していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-280">Interactive tests allow you to confirm essential functionality is working as expected.</span></span> <span data-ttu-id="2bd1f-281">問題が発生した場合は、結果を保存して Surface Hub のサポート チームと共有できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-281">If problems are encountered, results can be saved and shared with the Surface Hub Support Team.</span></span> <span data-ttu-id="2bd1f-282">リンクをクリックして Microsoft Store からインストールし、タスクバーにアプリケーションを固定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-282">Click on the link to install it from the Microsoft Store, and then pin the application to your taskbar.</span></span>

## <span data-ttu-id="2bd1f-283">追加設定</span><span class="sxs-lookup"><span data-stu-id="2bd1f-283">Additional settings</span></span>

### <span data-ttu-id="2bd1f-284">[ペンの尾] でホワイトボードを起動する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-284">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="2bd1f-285">[ **ペン** ] を検索し、[ペン] を選択し **& Windows Ink の設定**を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-285">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="2bd1f-286">ページの下部にある [ペンの**ショートカット**] で、[ **Microsoft ホワイトボード**の**1 回] を選択**します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-286">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <span data-ttu-id="2bd1f-287">Power management</span><span class="sxs-lookup"><span data-stu-id="2bd1f-287">Power management</span></span>

<span data-ttu-id="2bd1f-288">Surface Hub 2 で Windows 10 Pro または Enterprise を使用することで最高のエクスペリエンスを得るために、いくつかの電源設定を利用できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-288">There are several power settings available to get the best experience using Windows 10 Pro or Enterprise on Surface Hub 2.</span></span> <span data-ttu-id="2bd1f-289">これには、画面と pc のタイムアウトのほか、組み込みの人為的機能検出 (ドップラー)、スクリーンセーバー、パスワード保護などの機能が備わっていて、ノート pc やデスクトップユーザーに適したグループポリシーの電源設定を渡す方法も含まれています。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-289">This includes screen and pc timeouts and how they interact with the built-in human presence detection (Doppler), the screen saver and password protection, and then if appropriate how to by-pass group policy power settings intended for laptop / desktop users.</span></span>

<span data-ttu-id="2bd1f-290">Surface Hub 2 上の Windows 10 Pro または Enterprise では、タッチ、マウス、およびキーボード操作による画面のスリープ、または組み込みの人的占有検出 (ドップラー) による画面のスリープ状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-290">Windows 10 Pro or Enterprise on Surface Hub 2 keeps the screen from going to sleep by touch, mouse, and keyboard actions, as well as the built-in human occupancy detection (Doppler).</span></span> <span data-ttu-id="2bd1f-291">人為的占有検出は既定で有効になっていますが、必要に応じて、Surface UEFI コンフィギュレーターツールのデバイスオプションを切り替えて、最初の移行の一環として、または後で UEFI 構成パッケージを作成して適用することによって、UEFI で無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-291">Human occupancy detection is enabled by default, but if desired it can be disabled in UEFI by toggling the device option in the Surface UEFI Configurator tool either as part of the initial migration, or by building and applying a later UEFI configuration package.</span></span> 

**<span data-ttu-id="2bd1f-292">Power Management: 画面と PC のスリープ設定</span><span class="sxs-lookup"><span data-stu-id="2bd1f-292">Power Management: Screen and PC sleep settings</span></span>**

1. <span data-ttu-id="2bd1f-293">[設定の**開始**] を選び  >  **Settings**  >  **System**  >  、**スリープ &** します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-293">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>

2. <span data-ttu-id="2bd1f-294">[電源モード] スライダーを [ **最適なパフォーマンス**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-294">Set the power mode slider to **Best performance**.</span></span>

3. <span data-ttu-id="2bd1f-295">画面とスリープの値を好みに合わせて構成します。また、移動が検出されたときにデバイスがスリープ状態になるように、ドップラーのプレゼンス検出も考慮します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-295">Configure screen and sleep values to your preference while also accounting for Doppler presence detection that wakes up the device when movement is detected.</span></span> <span data-ttu-id="2bd1f-296">したがって、ベストプラクティスとして、 **2 時間後**に画面をオフにすることをお勧めし**ます。また、4時間経過したら**、PC の電源をオフにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-296">Accordingly, as a best practice, it's recommended to set Screen to **Turn off after 2 hours** and the PC to **Turn off after 4 hours.**</span></span>

**<span data-ttu-id="2bd1f-297">Power Management: スクリーンセーバー</span><span class="sxs-lookup"><span data-stu-id="2bd1f-297">Power Management: Screen saver</span></span>**

1. <span data-ttu-id="2bd1f-298">**ロック画面**を検索し、**ロック画面の設定**を開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-298">Search for **Lock Screen** and open **Lock screen settings**.</span></span>

2. <span data-ttu-id="2bd1f-299">**画面のタイムアウト設定**と**スクリーンセーバーの設定**を好みに合わせて構成します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-299">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span> <span data-ttu-id="2bd1f-300">推奨される既定値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-300">Recommended default values are:</span></span>

   - <span data-ttu-id="2bd1f-301">[スクリーンセーバー] (なし) または任意のスクリーンセーバー</span><span class="sxs-lookup"><span data-stu-id="2bd1f-301">Screen saver to (None) or a screen saver of your choice.</span></span>
   - <span data-ttu-id="2bd1f-302">15分間待機します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-302">Wait time to 15 minutes.</span></span>
   - <span data-ttu-id="2bd1f-303">再開時に、ログオン画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-303">On resume, display logon screen.</span></span>


**<span data-ttu-id="2bd1f-304">Power Management: グループポリシー</span><span class="sxs-lookup"><span data-stu-id="2bd1f-304">Power Management: Group Policy</span></span>**

<span data-ttu-id="2bd1f-305">次の手順を実行する前に、IT 部門に問い合わせて、Surface Hub 2S デバイスをグローバルな power management ポリシーから除外するように依頼してください。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-305">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="2bd1f-306">一部の電源管理設定では、プレゼンス検出機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-306">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="2bd1f-307">**ソフトウェアセンター**を検索して開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-307">Search for **Software Center** and open it.</span></span>

2. <span data-ttu-id="2bd1f-308">[ **オプション**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-308">Select **Options**.</span></span>

3. <span data-ttu-id="2bd1f-309">**Power management**を展開し、[**このコンピューターに IT 部門の power settings を適用しない**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-309">Expand the **Power management**  and select **Do not apply power settings from my IT department to this computer**.</span></span>

   ![ソフトウェアの設定](images/soft-cntr.png)

### <span data-ttu-id="2bd1f-311">ストレージ センサー</span><span class="sxs-lookup"><span data-stu-id="2bd1f-311">Storage Sense</span></span>

<span data-ttu-id="2bd1f-312">Surface Hub 2 にはローカルストレージ用に 128GB SSD が搭載されているため、通常の使用時に記憶域の節約の測定値を使用することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-312">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="2bd1f-313">記憶域の感覚を構成するには:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-313">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="2bd1f-314">[**システム設定**] の下にある [**記憶域の設定**] を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-314">Search for **storage settings**, which is found under **System settings**.</span></span>

2.  <span data-ttu-id="2bd1f-315">[ **設定**] で、[ **ストレージの感覚を有効** にする] を選択して、[ **記憶域** の設定] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-315">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>

3.  <span data-ttu-id="2bd1f-316">ストレージ **の**感覚をオンにします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-316">Turn Storage Sense to **On**.</span></span>

4.  <span data-ttu-id="2bd1f-317">[ **記憶域の構成] または [今すぐ実行** ] を選択して、ファイルを可能な限りオンラインのままにする (ドライブの空き領域が限られているため) ように設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-317">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="2bd1f-318">推奨される設定:</span><span class="sxs-lookup"><span data-stu-id="2bd1f-318">Recommended settings:</span></span>

- <span data-ttu-id="2bd1f-319">ストレージを実行するには、毎日。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-319">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="2bd1f-320">自分のアプリで使用されていない一時ファイル (少なくとも14日間) を削除します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-320">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="2bd1f-321">[自分のダウンロード] フォルダーに含まれているファイルがある場合は、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-321">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="2bd1f-322">OneDrive: コンテンツはオンラインになります。数が30日以上開かれていない場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-322">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <span data-ttu-id="2bd1f-323">タブレット モード</span><span class="sxs-lookup"><span data-stu-id="2bd1f-323">Tablet mode</span></span>

<span data-ttu-id="2bd1f-324">アクセシビリティが必要な場合は、タブレットモードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-324">Turn on Tablet mode if desired for accessibility needs.</span></span>


### <span data-ttu-id="2bd1f-325">サウンド設定</span><span class="sxs-lookup"><span data-stu-id="2bd1f-325">Sound settings</span></span>

1. <span data-ttu-id="2bd1f-326">[ **サウンドの設定** ] を検索して、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-326">Search for **Sounds settings** and open this page.</span></span>

2. <span data-ttu-id="2bd1f-327">右側の [ **サウンドコントロールパネル** ] を選択し、[ **サウンド** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-327">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>

3. <span data-ttu-id="2bd1f-328">[ **プログラムイベント** ] で、 **デバイス接続** と **デバイスの切断** を [ **なし**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-328">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <span data-ttu-id="2bd1f-329">無音通知</span><span class="sxs-lookup"><span data-stu-id="2bd1f-329">Silence notifications</span></span>

1. <span data-ttu-id="2bd1f-330">**フォーカスアシスト**を検索して、このページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-330">Search for **Focus assist** and open this page.</span></span>

2. <span data-ttu-id="2bd1f-331">[ **アラームのみ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-331">Select **Alarms Only**.</span></span> <span data-ttu-id="2bd1f-332">これにより、一定の通知ポップアップを回避できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-332">This will avoid constant notification flyouts.</span></span>

### <span data-ttu-id="2bd1f-333">ディスク クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="2bd1f-333">Disk Cleanup</span></span>

1. <span data-ttu-id="2bd1f-334">**ディスククリーンアップ**を検索して、このアプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-334">Search for **Disk Cleanup** and open this app.</span></span>

2. <span data-ttu-id="2bd1f-335">[ **削除するファイル**] で、削除するファイルを選びます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-335">Under **Files to delete**, select the files you wish to delete.</span></span> 

3. <span data-ttu-id="2bd1f-336">また、[ **システムファイルのクリーンアップ**] も選択します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-336">Also select **Clean up system files**.</span></span>

## <span data-ttu-id="2bd1f-337">完了して確認する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-337">Complete and verify</span></span>

1. <span data-ttu-id="2bd1f-338">すべての Windows 更新プログラムをスキャンしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-338">Scan for and install all Windows Updates.</span></span>

2. <span data-ttu-id="2bd1f-339">グループポリシーの更新</span><span class="sxs-lookup"><span data-stu-id="2bd1f-339">Update Group Policy</span></span>

   1. <span data-ttu-id="2bd1f-340">昇格されたコマンドプロンプトで、「 **gpupdate/force/boot/wait: 0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-340">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
   
3. <span data-ttu-id="2bd1f-341">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-341">Restart the device.</span></span>

4. <span data-ttu-id="2bd1f-342">タスクバーのアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-342">Verify taskbar apps.</span></span>

   - <span data-ttu-id="2bd1f-343">アプリを接続する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-343">Connect App</span></span>
   - <span data-ttu-id="2bd1f-344">ロックアイコン</span><span class="sxs-lookup"><span data-stu-id="2bd1f-344">Lock Icon</span></span>
   - <span data-ttu-id="2bd1f-345">切り取り & スケッチ</span><span class="sxs-lookup"><span data-stu-id="2bd1f-345">Snip & Sketch</span></span>
   - <span data-ttu-id="2bd1f-346">Teams (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="2bd1f-346">Teams (if applicable)</span></span>
   - <span data-ttu-id="2bd1f-347">Office アプリ (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="2bd1f-347">Office Apps (if applicable)</span></span>
   - <span data-ttu-id="2bd1f-348">Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="2bd1f-348">Surface App</span></span>
   - <span data-ttu-id="2bd1f-349">ホワイトボード</span><span class="sxs-lookup"><span data-stu-id="2bd1f-349">Whiteboard</span></span>
    
5. <span data-ttu-id="2bd1f-350">プレゼンス検出を確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-350">Verify presence detection.</span></span>

   - <span data-ttu-id="2bd1f-351">プレゼンス検出は、システムトレイに緑のアイコンで表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-351">Presence detection will be a green icon in the system tray.</span></span>
    
6. <span data-ttu-id="2bd1f-352">この PC へのプロジェクションが接続アプリで有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-352">Verify projecting to this PC is enabled with the Connect App.</span></span> <span data-ttu-id="2bd1f-353">**Project をこの PC 設定に**構成した後、少なくとも1回は Connect アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-353">After configuring  **Project to this PC** settings, run the Connect App at least once.</span></span> <span data-ttu-id="2bd1f-354">(その後、Surface Hub に対してプロジェクトを実行するために接続アプリが実行されている必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-354">(Subsequently, the Connect App does not need to be running in order to project to Surface Hub.)</span></span>

7. <span data-ttu-id="2bd1f-355">電源とスリープの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-355">Verify power and sleep settings.</span></span>

    - <span data-ttu-id="2bd1f-356">スクリーンセーバー:15 分、[なし]、[Mystify]、または [空白] に設定します。[パスワードを要求する] チェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-356">Screen Saver: 15 minutes, set to (none), Mystify or Blank; ensure the check box for requiring password is selected.</span></span>
    - <span data-ttu-id="2bd1f-357">画面: **2 時間後にオフに**します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-357">Screen: **Turn off after 2 hours**.</span></span>
    - <span data-ttu-id="2bd1f-358">PC:  **4 時間後にオフに**します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-358">PC:  **Turn off after 4 hours**.</span></span>
    
8. <span data-ttu-id="2bd1f-359">Windows Hello が動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-359">Verify Windows Hello is working.</span></span>

9. <span data-ttu-id="2bd1f-360">同期設定が無効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-360">Verify sync your settings is disabled.</span></span>

10. <span data-ttu-id="2bd1f-361">スタートアップアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-361">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="2bd1f-362">Windows 10 をインストールして構成した後、Surface Hub 2S は、他の Windows 10 デバイスと同じように管理できます。</span><span class="sxs-lookup"><span data-stu-id="2bd1f-362">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <span data-ttu-id="2bd1f-363">関連トピック</span><span class="sxs-lookup"><span data-stu-id="2bd1f-363">Related topics</span></span>

<a href="surface-hub-2s-migrate-os.md" target="_blank"> <span data-ttu-id="2bd1f-364">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="2bd1f-364">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span></a>
