---
title: Surface Hub のリセットまたは回復
description: Surface Hub のリセットおよび回復プロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット、回復
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/10/2021
ms.localizationpriority: medium
ms.openlocfilehash: 4b6797a83936b919aa43a7ae9fc8ae4dd720223a
ms.sourcegitcommit: f0c976664116c45605edf3d56c4f58119a246b93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "11406640"
---
# <a name="reset-or-recover-a-surface-hub"></a><span data-ttu-id="9ab56-104">Surface Hub のリセットまたは回復</span><span class="sxs-lookup"><span data-stu-id="9ab56-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="9ab56-105">この記事では、Microsoft Surface Hub をリセットまたは回復する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="9ab56-106">[Surface Hub をリセットすると](#reset-a-surface-hub) 、オペレーティング システムは最後の累積的な Windows 更新プログラムに戻され、すべてのローカル ユーザー ファイルと構成情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="9ab56-107">削除される情報には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="9ab56-108">デバイス アカウント</span><span class="sxs-lookup"><span data-stu-id="9ab56-108">The device account</span></span>
- <span data-ttu-id="9ab56-109">デバイスのローカル管理者のアカウント情報</span><span class="sxs-lookup"><span data-stu-id="9ab56-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="9ab56-110">ドメイン参加または Azure AD参加情報</span><span class="sxs-lookup"><span data-stu-id="9ab56-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="9ab56-111">モバイル デバイス管理 (MDM) 登録情報</span><span class="sxs-lookup"><span data-stu-id="9ab56-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="9ab56-112">MDM または設定アプリを使用して設定された構成情報</span><span class="sxs-lookup"><span data-stu-id="9ab56-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="9ab56-113">[クラウドから Surface Hub を復元すると、](#recover-a-surface-hub-from-the-cloud) この情報も削除されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="9ab56-114">さらに、Surface Hub は新しいオペレーティング システム イメージをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="9ab56-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="9ab56-115">回復プロセスが Surface Hub に保存されている他の情報を保持するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span> <span data-ttu-id="9ab56-116">これらのどちらのオプションも使用しない Surface Hub を回復する必要がある場合は [、Surface Hub](surface-hub-recovery-tool.md) 回復ツールで同じオペレーティング システム イメージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-116">The same operating system image is used by the [Surface Hub Recovery Tool](surface-hub-recovery-tool.md) if you need to recover a Surface Hub for which neither of these options can be used.</span></span>

## <a name="reset-a-surface-hub"></a><span data-ttu-id="9ab56-117">Surface Hub のリセット</span><span class="sxs-lookup"><span data-stu-id="9ab56-117">Reset a Surface Hub</span></span>

<span data-ttu-id="9ab56-118">次のような理由で Surface Hub をリセットする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-118">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="9ab56-119">新しい会議スペース用にデバイスを再削除し、再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-119">You are re-purposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="9ab56-120">ローカルでのデバイスの管理方法を変更したい。</span><span class="sxs-lookup"><span data-stu-id="9ab56-120">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="9ab56-121">デバイス アカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。</span><span class="sxs-lookup"><span data-stu-id="9ab56-121">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="9ab56-122">更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-122">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="9ab56-123">リセットプロセス中に、長時間空白の画面が表示される場合は、何も実行しないでお待ちください。</span><span class="sxs-lookup"><span data-stu-id="9ab56-123">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="9ab56-124">デバイスのリセット プロセスには最大 6 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-124">The device reset process may take up to six hours.</span></span> <span data-ttu-id="9ab56-125">プロセスが完了するまで、Surface Hub の電源をオフにしたり、プラグを抜かしたりしない。</span><span class="sxs-lookup"><span data-stu-id="9ab56-125">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="9ab56-126">プロセスを中断すると、デバイスは操作不能になります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-126">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="9ab56-127">デバイスが再び機能するには、保証サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9ab56-127">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="9ab56-128">Surface Hub で **[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-128">On your Surface Hub, open **Settings**.</span></span>

   ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

2. <span data-ttu-id="9ab56-130">[ **セキュリティの更新&] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-130">Select **Update & Security**.</span></span>

   ![Surface Hub の設定アプリ&セキュリティ グループの更新プログラムを示す画像。](images/sh-settings-update-security.png)

3. <span data-ttu-id="9ab56-132">[ **回復] を**選択し、[デバイスのリセット] **で**、[スタート] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-132">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="9ab56-133">デバイスをリセットする前に、BitLocker キーを使用できる状態にしてください。後でデバイスの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-133">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="9ab56-134">詳細については [、「Save your BitLocker key 」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab56-134">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span> <span data-ttu-id="9ab56-135">ハブが回復パーティションに再起動すると、BitLocker キーを入力するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-135">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="9ab56-136">このプロンプトをスキップすると、リセットが失敗します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-136">Skipping that prompt will cause reset to fail.</span></span>
   
   ![Surface Hub の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   <span data-ttu-id="9ab56-138">リセット プロセスが完了すると、Surface Hub は最初の実行 [プログラムを再度開始](first-run-program-surface-hub.md) します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-138">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="9ab56-139">リセット プロセスで問題が発生した場合は、Surface Hub を以前のオペレーティング システム イメージにロールバックし、[ようこそ] 画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-139">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <a name="recover-a-surface-hub-from-the-cloud"></a><span data-ttu-id="9ab56-140">クラウドから Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="9ab56-140">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="9ab56-141">何らかの理由で Surface Hub が使用できなくなっている場合でも、Microsoft サポートの支援を受けずにクラウドから回復できます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-141">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="9ab56-142">Surface Hub は、クラウドから新しいオペレーティング システム イメージをダウンロードし、そのイメージを使用してオペレーティング システムを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-142">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="9ab56-143">次の状況では、この種類の回復プロセスを使用する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-143">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="9ab56-144">Surface Hub または関連するアカウントが不安定な状態になった</span><span class="sxs-lookup"><span data-stu-id="9ab56-144">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="9ab56-145">Surface Hub がロックされている</span><span class="sxs-lookup"><span data-stu-id="9ab56-145">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="9ab56-146">クラウド **からの回復プロセスでは** 、オープン インターネット接続を提供する有線接続が必要です (プロキシや他の認証プロンプトはありません)。</span><span class="sxs-lookup"><span data-stu-id="9ab56-146">The **Recover from the cloud** process requires a wired connection that provides open internet connectivity (no proxy or other authentication prompts).</span></span>

### <a name="recover-a-surface-hub-in-a-bad-state"></a><span data-ttu-id="9ab56-147">正常な状態でない Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="9ab56-147">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="9ab56-148">デバイス アカウントが不安定な状態になった場合、または管理者アカウントに問題が発生した場合は、設定アプリを使用してクラウド回復プロセスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-148">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="9ab56-149">デバイスのリセット プロセスで問題が解決しない[](#reset-a-surface-hub)場合にのみ、クラウド回復プロセスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-149">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="9ab56-150">Surface Hub で、[設定の更新] **を** &gt; **選択&回復** &gt; **します**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-150">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

2. <span data-ttu-id="9ab56-151">[ **クラウドからの回復] で、[** 今すぐ再起動 **する] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-151">Under **Recover from the cloud**, select **Restart now**.</span></span>

   ![クラウドから回復する](images/recover-from-the-cloud.png)

### <a name="recover-a-locked-surface-hub"></a><span data-ttu-id="9ab56-153">ロックされた Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="9ab56-153">Recover a locked Surface Hub</span></span>

<span data-ttu-id="9ab56-154">まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-154">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="9ab56-155">この場合、デバイスは自動的に再起動し、操作を再度試行します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-155">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="9ab56-156">ただし、この操作が繰り返し失敗した場合、デバイスは自動的にロックしてユーザー データを保護します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-156">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="9ab56-157">ロックを解除するには、デバイス [をリセット](#reset-a-surface-hub) するか、動作しない場合はクラウドから復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab56-157">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="9ab56-158">Surface Hub の下部にある電源スイッチを見つける。</span><span class="sxs-lookup"><span data-stu-id="9ab56-158">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="9ab56-159">電源スイッチは、電源コード接続の横に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-159">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="9ab56-160">電源スイッチの詳細については [、「Surface Hub Site 準備ガイド (PDF)」を参照してください](surface-hub-site-readiness-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab56-160">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

2. <span data-ttu-id="9ab56-161">Surface Hub に [ようこそ] 画面が表示されている間は、電源スイッチを使用して Surface Hub をオフにします。</span><span class="sxs-lookup"><span data-stu-id="9ab56-161">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

3. <span data-ttu-id="9ab56-162">Surface Hub をオンに戻す場合は、電源スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-162">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="9ab56-163">デバイスが起動し、[Surface Hub ロゴ] 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ab56-163">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="9ab56-164">Surface Hub ロゴの下に回転ドットが表示されている場合は、電源スイッチを使用して Surface Hub を再度オフにします。</span><span class="sxs-lookup"><span data-stu-id="9ab56-164">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

4. <span data-ttu-id="9ab56-165">手順 3 を 3 回繰り返します。または Surface Hub に [自動修復の準備] メッセージが表示されるまで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-165">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="9ab56-166">このメッセージが表示された後、Surface Hub は Windows RE 画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-166">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>

 
5. <span data-ttu-id="9ab56-167">[リセット **] を選択して Windows を再インストールします**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-167">Select **Reset to re-install Windows**.</span></span> 
![再インストールへのリセット](images/recover-from-cloud.png)

8. <span data-ttu-id="9ab56-169">[クラウド **ダウンロード] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="9ab56-169">Select **Cloud download.**</span></span> 

   ![クラウドダウンロード](images/recover-cloud-download.png)

>[!IMPORTANT]
><span data-ttu-id="9ab56-171">[ダウンロードできない] というエラー\*\*\*\* メッセージが表示された場合は、[キャンセル] を選択**し**、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="9ab56-171">If you get an error message indicating **Unable to Download**, select **Cancel** and try again.</span></span>

9. <span data-ttu-id="9ab56-172">[**ドライブを完全にクリーンアップする] を選択します。**  
![ドライブの回復と完全なクリーン</span><span class="sxs-lookup"><span data-stu-id="9ab56-172">Select **Fully clean the drive.** 
![recover and fully clean drive</span></span>](images/recover-fully-clean-drive.png)

10. <span data-ttu-id="9ab56-173">このデバイスをリセットする **準備ができているかという質問が表示されます**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-173">You will be asked **Are you ready to reset this device?**.</span></span> <span data-ttu-id="9ab56-174">**[リセット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-174">Select **Reset**.</span></span> 
![リセットの回復と確認](images/recover-confirm-reset.png)

11. <span data-ttu-id="9ab56-176">ダウンロードが開始され、回復プロセスは、このデバイス **のリセットを示します**。</span><span class="sxs-lookup"><span data-stu-id="9ab56-176">The download begins and the recovery process indicates **Resetting this device**.</span></span> 
![進行中の回復](images/recover-in-progress.png)

## <a name="contact-support"></a><span data-ttu-id="9ab56-178">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="9ab56-178">Contact Support</span></span>

<span data-ttu-id="9ab56-179">質問がある場合やサポートが必要な場合は、サポート [要求を作成できます](https://support.microsoft.com/supportforbusiness/productselection)。</span><span class="sxs-lookup"><span data-stu-id="9ab56-179">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <a name="related-topics"></a><span data-ttu-id="9ab56-180">関連トピック</span><span class="sxs-lookup"><span data-stu-id="9ab56-180">Related topics</span></span>

[<span data-ttu-id="9ab56-181">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="9ab56-181">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="9ab56-182">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="9ab56-182">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)
