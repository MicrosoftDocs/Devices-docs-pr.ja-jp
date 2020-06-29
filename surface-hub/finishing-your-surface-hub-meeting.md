---
title: セッションの終了 - Surface Hub の会議を終了する
description: Surface Hub の会議を終了するには、[セッションの終了] をタップします。 Surface Hub では、次の会議に備えて、アプリケーションの状態、オペレーティング システムの状態、およびユーザー インターフェイスがクリーンアップされます。
keywords: 終了, Surface Hub 会議の終了, Surface Hub 会議を終了, Surface Hub 会議のクリーンアップ
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: b18bc4b15b8a3925aeecdd9999b09b61011d1db5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836237"
---
# <span data-ttu-id="4d326-105">[セッションの終了] をタップして Surface Hub の会議を終了する</span><span class="sxs-lookup"><span data-stu-id="4d326-105">End a Surface Hub meeting with End session</span></span>
<span data-ttu-id="4d326-106">Surface Hub は、ミーティング スペースでさまざまなユーザーのグループが使用できるコラボレーション デバイスです。</span><span class="sxs-lookup"><span data-stu-id="4d326-106">Surface Hub is a collaboration device designed to be used in meeting spaces by different groups of people.</span></span> <span data-ttu-id="4d326-107">会議の終了時、ユーザーは **[セッションの終了]** をタップすることによって、機密データをクリーンアップし、次の会議用にデバイスを準備できます。</span><span class="sxs-lookup"><span data-stu-id="4d326-107">At the end of a meeting, users can tap **End session** to clean up any sensitive data and prepare the device for the next meeting.</span></span> <span data-ttu-id="4d326-108">Surface Hub は、次の状態をクリーンアップ、つまりリセットします。</span><span class="sxs-lookup"><span data-stu-id="4d326-108">Surface Hub will clean up, or reset, the following states:</span></span>
- <span data-ttu-id="4d326-109">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4d326-109">Applications</span></span>
- <span data-ttu-id="4d326-110">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="4d326-110">Operating system</span></span>
- <span data-ttu-id="4d326-111">ユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d326-111">User interface</span></span>

<span data-ttu-id="4d326-112">このトピックでは、**[セッションの終了]** を使用することでリセットされる各状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d326-112">This topic explains what **End session** resets for each of these states.</span></span>

## <span data-ttu-id="4d326-113">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4d326-113">Applications</span></span>
<span data-ttu-id="4d326-114">Surface Hub でアプリを起動すると、アプリはメモリに格納され、データはアプリケーション レベルで格納されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-114">When you start apps on Surface Hub, they are stored in memory and data is stored at the application level.</span></span> <span data-ttu-id="4d326-115">データは、削除または上書きされない限り、そのセッション (会議) のあいだはすべてのユーザーが利用できます。</span><span class="sxs-lookup"><span data-stu-id="4d326-115">Data is available to all users during that session (or meeting) until date is removed or overwritten.</span></span> <span data-ttu-id="4d326-116">**[セッションの終了]** を選択すると、アプリケーションの終了、ブラウザーの履歴の削除、アプリケーションのリセット、Skype のログの削除が行われ、Surface Hub のアプリケーションの状態が消去されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-116">When **End session** is selected, Surface Hub application state is cleared out by closing applications, deleting browser history, resetting applications, and removing Skype logs.</span></span>

### <span data-ttu-id="4d326-117">アプリケーションの終了</span><span class="sxs-lookup"><span data-stu-id="4d326-117">Close applications</span></span>
<span data-ttu-id="4d326-118">Win32 およびユニバーサル Windows プラットフォーム (UWP) アプリケーションも含めて、表示されているすべてのウィンドウが Surface Hub によって閉じられます。</span><span class="sxs-lookup"><span data-stu-id="4d326-118">Surface Hub closes all visible windows, including Win32 and Universal Windows Platform (UWP) applications.</span></span> <span data-ttu-id="4d326-119">アプリケーションの終了段階では、マルチタスク ビューを使用して、表示されているウィンドウが照会されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-119">The application close stage uses the multitasking view to query the visible windows.</span></span> <span data-ttu-id="4d326-120">一定の時間内に終了されない Win32 ウィンドウは、**TerminateProcess** を使用して終了されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-120">Win32 windows that do not close within a certain timeframe are closed using **TerminateProcess**.</span></span> 
   
### <span data-ttu-id="4d326-121">ブラウザーの履歴の削除</span><span class="sxs-lookup"><span data-stu-id="4d326-121">Delete browser history</span></span>
<span data-ttu-id="4d326-122">Surface Hub は、Edge のブラウザーの履歴の削除 (DBH) 機能を使用して、Edge の履歴とキャッシュされたデータをクリアします。</span><span class="sxs-lookup"><span data-stu-id="4d326-122">Surface Hub uses Delete Browser History (DBH) in Edge to clear Edge history and cached data.</span></span> <span data-ttu-id="4d326-123">これは、ユーザーが手動でブラウザー履歴を消去する方法に似ていますが、**[セッションの終了]** を使う場合は、次のセッション、つまり会議が開始される前に、確実にアプリケーションの状態がクリアされ、データが削除されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-123">This is similar to how a user can clear out their browser history manually, but **End session** also ensures that application states are cleared and data is removed before the next session, or meeting, starts.</span></span> 
 
### <span data-ttu-id="4d326-124">アプリケーションのリセット</span><span class="sxs-lookup"><span data-stu-id="4d326-124">Reset applications</span></span>
<span data-ttu-id="4d326-125">**[セッションの終了]** によって、Surface Hub にインストールされている各アプリケーションの状態がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="4d326-125">**End session** resets the state of each application that is installed on the Surface Hub.</span></span> <span data-ttu-id="4d326-126">アプリケーションをリセットすると、すべてのバックグラウンド タスク、アプリケーション データ、通知、ユーザーの承認ダイアログがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="4d326-126">Resetting an application clears all background tasks, application data, notifications, and user consent dialogs.</span></span> <span data-ttu-id="4d326-127">アプリケーションは、次に Surface Hub を使用するユーザーのために、最初の実行時の状態に戻されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-127">Applications are returned to their first-run state for the next people that use Surface Hub.</span></span>  
 
### <span data-ttu-id="4d326-128">Skype のログの削除</span><span class="sxs-lookup"><span data-stu-id="4d326-128">Remove Skype logs</span></span>
<span data-ttu-id="4d326-129">Skype は、個人を特定できる情報を Surface Hub に保存しません。</span><span class="sxs-lookup"><span data-stu-id="4d326-129">Skype does not store personally-identifiable information on Surface Hub.</span></span> <span data-ttu-id="4d326-130">情報は、既存の Skype for Business のガイダンスに従い、Skype サービスに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-130">Information is stored in the Skype service to meet existing Skype for Business guidance.</span></span> <span data-ttu-id="4d326-131">**[セッションの終了]** を選択すると、ローカルの Skype ログ情報のみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-131">Local Skype logging information is the only data removed when **End session** is selected.</span></span> <span data-ttu-id="4d326-132">これには、統合コミュニケーション クライアント プラットフォーム (UCCP) ログとメディア ログが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d326-132">This includes Unified Communications Client Platform (UCCP) logs and media logs.</span></span>   

## <span data-ttu-id="4d326-133">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="4d326-133">Operating System</span></span>
<span data-ttu-id="4d326-134">オペレーティング システムは、セッションの状態についてのさまざまな情報を保持しますが、Surface Hub の会議が終わるたびにこの情報はクリアされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d326-134">The operating system hosts a variety of information about the state of the sessions that needs to be cleared after each Surface Hub meeting.</span></span> 

### <span data-ttu-id="4d326-135">ファイル システム</span><span class="sxs-lookup"><span data-stu-id="4d326-135">File System</span></span>
<span data-ttu-id="4d326-136">会議の出席者は、Surface Hub の一部のディレクトリにしかアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="4d326-136">Meeting attendees have access to a limited set of directories on the Surface Hub.</span></span> <span data-ttu-id="4d326-137">**[セッションの終了]** を選択すると、Surface Hub では以下のディレクトリの内容が消去されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-137">When **End session** is selected, Surface Hub clears these directories:</span></span><br>
- <span data-ttu-id="4d326-138">ミュージック</span><span class="sxs-lookup"><span data-stu-id="4d326-138">Music</span></span>
- <span data-ttu-id="4d326-139">ビデオ</span><span class="sxs-lookup"><span data-stu-id="4d326-139">Videos</span></span>
- <span data-ttu-id="4d326-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="4d326-140">Documents</span></span>
- <span data-ttu-id="4d326-141">ピクチャ</span><span class="sxs-lookup"><span data-stu-id="4d326-141">Pictures</span></span>
- <span data-ttu-id="4d326-142">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="4d326-142">Downloads</span></span>

<span data-ttu-id="4d326-143">Surface Hub では、以下のディレクトリについても、多くのアプリケーションがデータを書き込むことが多いため、クリアされます。</span><span class="sxs-lookup"><span data-stu-id="4d326-143">Surface Hub also clears these directories, since many applications often write to them:</span></span>
- <span data-ttu-id="4d326-144">デスクトップ</span><span class="sxs-lookup"><span data-stu-id="4d326-144">Desktop</span></span>
- <span data-ttu-id="4d326-145">お気に入り</span><span class="sxs-lookup"><span data-stu-id="4d326-145">Favorites</span></span>
- <span data-ttu-id="4d326-146">最近使用したファイル</span><span class="sxs-lookup"><span data-stu-id="4d326-146">Recent</span></span>
- <span data-ttu-id="4d326-147">パブリック ドキュメント</span><span class="sxs-lookup"><span data-stu-id="4d326-147">Public Documents</span></span>
- <span data-ttu-id="4d326-148">パブリック ミュージック</span><span class="sxs-lookup"><span data-stu-id="4d326-148">Public Music</span></span>
- <span data-ttu-id="4d326-149">パブリック ビデオ</span><span class="sxs-lookup"><span data-stu-id="4d326-149">Public Videos</span></span>
- <span data-ttu-id="4d326-150">パブリック ダウンロード</span><span class="sxs-lookup"><span data-stu-id="4d326-150">Public Downloads</span></span>

### <span data-ttu-id="4d326-151">資格情報</span><span class="sxs-lookup"><span data-stu-id="4d326-151">Credentials</span></span>
<span data-ttu-id="4d326-152">**TokenBroker**、**PasswordVault**、または**資格情報マネージャー**に保存されているユーザー資格情報は、**[セッションの終了]** をタップすると、クリアされます。</span><span class="sxs-lookup"><span data-stu-id="4d326-152">User credentials that are stored in **TokenBroker**, **PasswordVault**, or **Credential Manager** are cleared when you tap **End session**.</span></span>

## <span data-ttu-id="4d326-153">ユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d326-153">User interface</span></span>
<span data-ttu-id="4d326-154">ユーザー インターフェイス (UI) 設定は、**[セッションの終了]** が選択されると、既定値に戻されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-154">User interface (UI) settings are returned to their default values when **End session** is selected.</span></span> 

### <span data-ttu-id="4d326-155">UI 項目</span><span class="sxs-lookup"><span data-stu-id="4d326-155">UI items</span></span>
- <span data-ttu-id="4d326-156">クイック アクションを既定の状態にリセット</span><span class="sxs-lookup"><span data-stu-id="4d326-156">Reset Quick Actions to default state</span></span>
- <span data-ttu-id="4d326-157">トースト通知をクリア</span><span class="sxs-lookup"><span data-stu-id="4d326-157">Clear Toast notifications</span></span>
- <span data-ttu-id="4d326-158">音量レベルをリセット</span><span class="sxs-lookup"><span data-stu-id="4d326-158">Reset volume levels</span></span>
- <span data-ttu-id="4d326-159">サイドバーの幅をリセット</span><span class="sxs-lookup"><span data-stu-id="4d326-159">Reset sidebar width</span></span>
- <span data-ttu-id="4d326-160">タブレット モードのレイアウトをリセット</span><span class="sxs-lookup"><span data-stu-id="4d326-160">Reset tablet mode layout</span></span>
- <span data-ttu-id="4d326-161">Sign user out of Office 365 meetings and files (ユーザーを Office 365 会議とファイルからサインアウト)</span><span class="sxs-lookup"><span data-stu-id="4d326-161">Sign user out of Office 365 meetings and files</span></span>

### <span data-ttu-id="4d326-162">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="4d326-162">Accessibility</span></span>
<span data-ttu-id="4d326-163">アクセシビリティ関連の機能やアプリは、**[セッションの終了]** が選択されると、既定の設定に戻されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-163">Accessibility features and apps are returned to default settings when **End session** is selected.</span></span>
- <span data-ttu-id="4d326-164">フィルター キー機能</span><span class="sxs-lookup"><span data-stu-id="4d326-164">Filter keys</span></span>
- <span data-ttu-id="4d326-165">ハイ コントラスト</span><span class="sxs-lookup"><span data-stu-id="4d326-165">High contrast</span></span>
- <span data-ttu-id="4d326-166">固定キー機能</span><span class="sxs-lookup"><span data-stu-id="4d326-166">Sticky keys</span></span>
- <span data-ttu-id="4d326-167">切り替えキー機能</span><span class="sxs-lookup"><span data-stu-id="4d326-167">Toggle keys</span></span>
- <span data-ttu-id="4d326-168">マウス キー機能</span><span class="sxs-lookup"><span data-stu-id="4d326-168">Mouse keys</span></span>
- <span data-ttu-id="4d326-169">拡大鏡</span><span class="sxs-lookup"><span data-stu-id="4d326-169">Magnifier</span></span>
- <span data-ttu-id="4d326-170">ナレーター</span><span class="sxs-lookup"><span data-stu-id="4d326-170">Narrator</span></span>

### <span data-ttu-id="4d326-171">クリップボード</span><span class="sxs-lookup"><span data-stu-id="4d326-171">Clipboard</span></span>
<span data-ttu-id="4d326-172">クリップボードはクリアされ、セッション中にクリップボードにコピーされたデータは削除されます。</span><span class="sxs-lookup"><span data-stu-id="4d326-172">The clipboard is cleared to remove data that was copied to the clipboard during the session.</span></span> 

## <span data-ttu-id="4d326-173">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="4d326-173">Frequently asked questions</span></span>
**<span data-ttu-id="4d326-174">会議の最後に [セッションの終了] をタップし忘れて、他のユーザーがその後 Surface Hub を使用した場合はどうなりますか。</span><span class="sxs-lookup"><span data-stu-id="4d326-174">What happens if I forget to tap End session at the end of a meeting, and someone else uses the Surface Hub later?</span></span>**<br>
<span data-ttu-id="4d326-175">Surface Hub は、ユーザーが **[セッションの終了]** をタップした場合にのみ、会議コンテンツがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="4d326-175">Surface Hub only cleans up meeting content when users tap **End session**.</span></span> <span data-ttu-id="4d326-176">**[セッションの終了]** をタップせずに会議を終了した場合、しばらくすると、デバイスはようこそ画面に戻ります。</span><span class="sxs-lookup"><span data-stu-id="4d326-176">If you leave the meeting without tapping **End session**, the device will return to the welcome screen after some time.</span></span> <span data-ttu-id="4d326-177">ユーザーは、ようこそ画面から、前のセッションを再開するか、または新しいをセッションを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="4d326-177">From the welcome screen, users have the option to resume the previous session or start a new one.</span></span> <span data-ttu-id="4d326-178">**[セッションの終了]** が表示されない場合にセッションを再開する機能を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4d326-178">You can also disable the ability to resume a session if **End session** is not pressed.</span></span>

**<span data-ttu-id="4d326-179">ドキュメントは回復できますか。</span><span class="sxs-lookup"><span data-stu-id="4d326-179">Are documents recoverable?</span></span>**<br> <span data-ttu-id="4d326-180">**[セッションの終了]** が選択されて、ハード ドライブからファイルが削除された場合の動作は、他の方法でハード ディスク ドライブからファイルを削除した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="4d326-180">Removing files from the hard drive when **End session** is selected is just like any other file deletion from a hard disk drive.</span></span> <span data-ttu-id="4d326-181">サードパーティのソフトウェアによって、ハード ディスク ドライブからデータを回復できる可能性はありますが、Surface Hub では、ファイルの回復はサポートされている機能ではありません。</span><span class="sxs-lookup"><span data-stu-id="4d326-181">Third-party software might be able to recover data from the hard disk drive, but file recovery is not a supported feature on Surface Hub.</span></span> <span data-ttu-id="4d326-182">データの損失を防ぐためには、必ず会議を終了する前に必要なデータを保存してください。</span><span class="sxs-lookup"><span data-stu-id="4d326-182">To prevent data loss, always save the data you need before leaving a meeting.</span></span>

**<span data-ttu-id="4d326-183">[セッションの終了] によるクリーンアップ操作は、米国国防省のデータの消去とサニタイズに関する規格「DoD 5220.22-M」に準拠していますか。</span><span class="sxs-lookup"><span data-stu-id="4d326-183">Do the clean-up actions from End session comply with the US Department of Defense clearing and sanitizing standard: DoD 5220.22-M?</span></span>**<br>
<span data-ttu-id="4d326-184">いいえ。</span><span class="sxs-lookup"><span data-stu-id="4d326-184">No.</span></span> <span data-ttu-id="4d326-185">現時点では、**[セッションの終了]** によるクリーンアップ操作は、この規格には準拠していません。</span><span class="sxs-lookup"><span data-stu-id="4d326-185">Currently, the clean-up actions from **End session** do not comply with this standard.</span></span>  
  
