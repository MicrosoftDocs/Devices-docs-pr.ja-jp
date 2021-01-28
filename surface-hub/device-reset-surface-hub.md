---
title: Surface Hub をリセットまたは復元する
description: Surface Hub のリセットと回復のプロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット, 回復
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73c7cf5a387bf7506bb69f62100171df4d94ad2d
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304820"
---
# <span data-ttu-id="85050-104">Surface Hub をリセットまたは復元する</span><span class="sxs-lookup"><span data-stu-id="85050-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="85050-105">この記事では、Microsoft Surface Hub をリセットまたは復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85050-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="85050-106">[Surface Hub をリセットすると](#reset-a-surface-hub) 、オペレーティング システムは最後の累積的な Windows 更新プログラムに戻り、ローカル ユーザー ファイルと構成情報はすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="85050-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="85050-107">削除される情報には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="85050-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="85050-108">デバイス アカウント</span><span class="sxs-lookup"><span data-stu-id="85050-108">The device account</span></span>
- <span data-ttu-id="85050-109">デバイスのローカル管理者のアカウント情報</span><span class="sxs-lookup"><span data-stu-id="85050-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="85050-110">ドメイン参加または Azure AD参加情報</span><span class="sxs-lookup"><span data-stu-id="85050-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="85050-111">モバイル デバイス管理 (MDM) 登録情報</span><span class="sxs-lookup"><span data-stu-id="85050-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="85050-112">MDM または設定アプリを使用して設定された構成情報</span><span class="sxs-lookup"><span data-stu-id="85050-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="85050-113">[クラウドから Surface Hub を回復すると、](#recover-a-surface-hub-from-the-cloud) この情報も削除されます。</span><span class="sxs-lookup"><span data-stu-id="85050-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="85050-114">さらに、Surface Hub は新しいオペレーティング システム イメージをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="85050-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="85050-115">回復プロセスで、Surface Hub に保存されている他の情報を保持するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="85050-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span> <span data-ttu-id="85050-116">どちらのオプションも使用しない Surface Hub を回復する必要がある場合は [、Surface Hub](surface-hub-recovery-tool.md) 回復ツールでも同じオペレーティング システム イメージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="85050-116">The same operating system image is used by the [Surface Hub Recovery Tool](surface-hub-recovery-tool.md) if you need to recover a Surface Hub for which neither of these options can be used.</span></span>

## <span data-ttu-id="85050-117">Surface Hub をリセットする</span><span class="sxs-lookup"><span data-stu-id="85050-117">Reset a Surface Hub</span></span>

<span data-ttu-id="85050-118">次のような理由により、Surface Hub のリセットが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="85050-118">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="85050-119">新しい会議スペース用にデバイスを再利用し、再構成する場合。</span><span class="sxs-lookup"><span data-stu-id="85050-119">You are re-purposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="85050-120">ローカルでのデバイスの管理方法を変更したい。</span><span class="sxs-lookup"><span data-stu-id="85050-120">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="85050-121">デバイス アカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。</span><span class="sxs-lookup"><span data-stu-id="85050-121">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="85050-122">更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="85050-122">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="85050-123">リセットプロセス中に、長時間空白の画面が表示される場合は、何も実行しないでお待ちください。</span><span class="sxs-lookup"><span data-stu-id="85050-123">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="85050-124">デバイスのリセット プロセスには、最大 6 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="85050-124">The device reset process may take up to six hours.</span></span> <span data-ttu-id="85050-125">プロセスが完了するまで、Surface Hub をオフにしたり、取り外したりしない。</span><span class="sxs-lookup"><span data-stu-id="85050-125">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="85050-126">プロセスを中断すると、デバイスは動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="85050-126">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="85050-127">デバイスが再び機能するには、保証サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="85050-127">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="85050-128">Surface Hub で **[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="85050-128">On your Surface Hub, open **Settings**.</span></span>

   ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

2. <span data-ttu-id="85050-130">[セキュリティ **の更新&選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-130">Select **Update & Security**.</span></span>

   ![Surface Hub の設定アプリ&セキュリティ グループの更新プログラムを示す画像。](images/sh-settings-update-security.png)

3. <span data-ttu-id="85050-132">[ **回復] を**選択し、[デバイスの **リセット]** で [開始] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-132">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="85050-133">デバイスをリセットする前に、BitLocker キーが利用可能な状態にしてください(後で入力を求めるメッセージが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="85050-133">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="85050-134">詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="85050-134">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span> <span data-ttu-id="85050-135">ハブが回復パーティションに再起動すると、BitLocker キーの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="85050-135">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="85050-136">このプロンプトをスキップすると、リセットが失敗します。</span><span class="sxs-lookup"><span data-stu-id="85050-136">Skipping that prompt will cause reset to fail.</span></span>
   
   ![Surface Hub の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   <span data-ttu-id="85050-138">リセット プロセスが完了すると、Surface Hub は最初の実行 [プログラムを再度起動](first-run-program-surface-hub.md) します。</span><span class="sxs-lookup"><span data-stu-id="85050-138">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="85050-139">リセット プロセスで問題が発生した場合は、Surface Hub を以前のオペレーティング システム イメージにロールバックし、ようこそ画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="85050-139">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <span data-ttu-id="85050-140">クラウドから Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="85050-140">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="85050-141">何らかの理由で Surface Hub が使用できなくなる場合でも、Microsoft サポートの支援なしにクラウドから回復できます。</span><span class="sxs-lookup"><span data-stu-id="85050-141">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="85050-142">Surface Hub は、クラウドから新しいオペレーティング システム イメージをダウンロードし、そのイメージを使ってオペレーティング システムを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="85050-142">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="85050-143">次の状況では、この種類の回復プロセスの使用が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="85050-143">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="85050-144">Surface Hub または関連アカウントが不安定な状態になった</span><span class="sxs-lookup"><span data-stu-id="85050-144">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="85050-145">Surface Hub がロックされている</span><span class="sxs-lookup"><span data-stu-id="85050-145">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="85050-146">クラウド **プロセスからの回復** には、オープン インターネット接続を提供するワイヤード (有線) 接続が必要です (プロキシや他の認証プロンプトはありません)。</span><span class="sxs-lookup"><span data-stu-id="85050-146">The **Recover from the cloud** process requires a wired connection that provides open internet connectivity (no proxy or other authentication prompts).</span></span>

### <span data-ttu-id="85050-147">正常な状態でない Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="85050-147">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="85050-148">デバイス アカウントが不安定な状態になった場合、または管理者アカウントで問題が発生した場合は、設定アプリを使用してクラウド回復プロセスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="85050-148">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="85050-149">クラウド回復プロセスは、デバイスのリセット プロセス[](#reset-a-surface-hub)で問題が解決しない場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="85050-149">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="85050-150">Surface Hub で、[設定の更新] **を**選択 &gt; **&回復** &gt; **します**。</span><span class="sxs-lookup"><span data-stu-id="85050-150">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

2. <span data-ttu-id="85050-151">[ **クラウドからの回復] で、[今**すぐ **再起動] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-151">Under **Recover from the cloud**, select **Restart now**.</span></span>

   ![クラウドから回復する](images/recover-from-the-cloud.png)

### <span data-ttu-id="85050-153">ロックされた Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="85050-153">Recover a locked Surface Hub</span></span>

<span data-ttu-id="85050-154">まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="85050-154">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="85050-155">この場合、デバイスは自動的に再起動し、もう一度操作を試みます。</span><span class="sxs-lookup"><span data-stu-id="85050-155">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="85050-156">ただし、この操作が繰り返し失敗した場合、デバイスはユーザー データを保護するために自動的にロックされます。</span><span class="sxs-lookup"><span data-stu-id="85050-156">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="85050-157">ロックを解除するには [、デバイスを](#reset-a-surface-hub) リセットするか、デバイスが動作しない場合はクラウドから回復する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85050-157">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="85050-158">Surface Hub の下部にある電源スイッチを見つける。</span><span class="sxs-lookup"><span data-stu-id="85050-158">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="85050-159">電源スイッチが電源コード接続の横にある。</span><span class="sxs-lookup"><span data-stu-id="85050-159">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="85050-160">電源スイッチについて詳しくは、Surface Hub サイトの準備ガイド [(PDF) をご覧ください](surface-hub-site-readiness-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="85050-160">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

2. <span data-ttu-id="85050-161">Surface Hub にようこそ画面が表示されている間は、電源スイッチを使って Surface Hub をオフにします。</span><span class="sxs-lookup"><span data-stu-id="85050-161">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

3. <span data-ttu-id="85050-162">電源スイッチを使って Surface Hub をオンに戻します。</span><span class="sxs-lookup"><span data-stu-id="85050-162">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="85050-163">デバイスが起動し、Surface Hub ロゴ画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="85050-163">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="85050-164">Surface Hub ロゴの下に回転するドットが表示された場合は、電源スイッチを使って Surface Hub を再びオフにします。</span><span class="sxs-lookup"><span data-stu-id="85050-164">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

4. <span data-ttu-id="85050-165">手順 3 を 3 回繰り返します。または、Surface Hub に [自動修復の準備] メッセージが表示されるまで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="85050-165">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="85050-166">このメッセージが表示された後、Surface Hub には Windows RE 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="85050-166">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>

5. <span data-ttu-id="85050-167">[詳細 **オプション] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-167">Select **Advanced Options**.</span></span>

6. <span data-ttu-id="85050-168">[クラウド **からの回復] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-168">Select **Recover from the cloud**.</span></span> <span data-ttu-id="85050-169">(必要に応じて、[リセット] を選択 **できます**。</span><span class="sxs-lookup"><span data-stu-id="85050-169">(Optionally, you can select **Reset**.</span></span> <span data-ttu-id="85050-170">ただし、 **クラウドからの回復が** 推奨されるアプローチです)。</span><span class="sxs-lookup"><span data-stu-id="85050-170">However, **Recover from the cloud** is the recommended approach.)</span></span>

   ![クラウドからの回復](images/recover-from-cloud.png)
7. <span data-ttu-id="85050-172">Bitlocker キーの入力を求めるメッセージが表示されたら、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="85050-172">If you are prompted to enter the Bitlocker key, do one of the following:</span></span>

   - <span data-ttu-id="85050-173">Surface Hub で Bitlocker が保護する情報を保持するには、Bitlocker キーを入力します。</span><span class="sxs-lookup"><span data-stu-id="85050-173">To preserve the information that Bitlocker protects on the Surface Hub, enter the Bitlocker key.</span></span>
   - <span data-ttu-id="85050-174">保護された情報を破棄するには、[このドライブをスキップ **する] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="85050-174">To discard the protected information, select **Skip this drive**</span></span>  

8. <span data-ttu-id="85050-175">メッセージが表示されたら、[再インストール] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-175">When you are prompted, select **Reinstall**.</span></span>

    ![再インストール](images/reinstall.png)

9. <span data-ttu-id="85050-177">ディスクを再パーティション化するには、[はい] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="85050-177">To repartition the disk, select **Yes**.</span></span>

   ![パーティションの再作成](images/repartition.png)

   <span data-ttu-id="85050-179">最初に、回復プロセスによって、クラウドからオペレーティング システム イメージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="85050-179">First, the recovery process downloads the operating system image from the cloud.</span></span>  

   ![ダウンロード中 97&](images/recover-progress.png)

   <span data-ttu-id="85050-181">ダウンロードが完了すると、選択したオプションに従って回復プロセスによって Surface Hub が復元されます。</span><span class="sxs-lookup"><span data-stu-id="85050-181">When the download finishes, the recovery process restores the Surface Hub according to the options that you selected.</span></span>
   

## <span data-ttu-id="85050-182">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="85050-182">Contact Support</span></span>

<span data-ttu-id="85050-183">質問がある場合やサポートが必要な場合は、サポート [リクエストを作成できます](https://support.microsoft.com/supportforbusiness/productselection)。</span><span class="sxs-lookup"><span data-stu-id="85050-183">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <span data-ttu-id="85050-184">関連トピック</span><span class="sxs-lookup"><span data-stu-id="85050-184">Related topics</span></span>

[<span data-ttu-id="85050-185">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="85050-185">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="85050-186">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="85050-186">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)
