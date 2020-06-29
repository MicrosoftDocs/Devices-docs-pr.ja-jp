---
title: Surface Hub をリセットまたは回復する
description: Surface Hub のリセットおよび回復プロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット、復元
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: c5cf643d0f4a68344bb098916a909dd66e1dac9b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836285"
---
# <span data-ttu-id="cd91c-104">Surface Hub をリセットまたは回復する</span><span class="sxs-lookup"><span data-stu-id="cd91c-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="cd91c-105">この記事では、Microsoft Surface Hub をリセットまたは回復する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="cd91c-106">[Surface Hub をリセット](#reset-a-surface-hub)すると、そのオペレーティングシステムが、最後に累積された Windows update に戻り、ローカルユーザーのファイルと構成情報がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="cd91c-107">削除される情報には、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="cd91c-108">デバイス アカウント</span><span class="sxs-lookup"><span data-stu-id="cd91c-108">The device account</span></span>
- <span data-ttu-id="cd91c-109">デバイスのローカル管理者のアカウント情報</span><span class="sxs-lookup"><span data-stu-id="cd91c-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="cd91c-110">ドメイン参加または Azure AD-参加情報</span><span class="sxs-lookup"><span data-stu-id="cd91c-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="cd91c-111">モバイルデバイス管理 (MDM) の登録情報</span><span class="sxs-lookup"><span data-stu-id="cd91c-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="cd91c-112">MDM または設定アプリを使用して設定された構成情報</span><span class="sxs-lookup"><span data-stu-id="cd91c-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="cd91c-113">[クラウドから Surface Hub を回復すると、](#recover-a-surface-hub-from-the-cloud)この情報も削除されます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="cd91c-114">さらに、Surface Hub は、新しいオペレーティングシステムイメージをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="cd91c-115">回復プロセスで Surface Hub に保存されている他の情報を保存するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span>

## <span data-ttu-id="cd91c-116">Surface Hub をリセットする</span><span class="sxs-lookup"><span data-stu-id="cd91c-116">Reset a Surface Hub</span></span>

<span data-ttu-id="cd91c-117">次のような理由から Surface Hub のリセットが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-117">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="cd91c-118">新しい会議スペースのためにデバイスを再利用していて、再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-118">You are re-purposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="cd91c-119">ローカルでのデバイスの管理方法を変更したい。</span><span class="sxs-lookup"><span data-stu-id="cd91c-119">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="cd91c-120">デバイスアカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。</span><span class="sxs-lookup"><span data-stu-id="cd91c-120">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="cd91c-121">更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-121">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="cd91c-122">リセットプロセス中に、長時間の空白画面が表示される場合は、操作を行わないでください。</span><span class="sxs-lookup"><span data-stu-id="cd91c-122">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="cd91c-123">デバイスのリセットプロセスには最大6時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-123">The device reset process may take up to six hours.</span></span> <span data-ttu-id="cd91c-124">プロセスが完了するまで Surface Hub の電源をオフにする、または取り外すことはできません。</span><span class="sxs-lookup"><span data-stu-id="cd91c-124">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="cd91c-125">プロセスを中断すると、デバイスが使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-125">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="cd91c-126">再機能させるには、デバイスに保証サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="cd91c-126">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="cd91c-127">Surface Hub で **[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-127">On your Surface Hub, open **Settings**.</span></span>

   ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

1. <span data-ttu-id="cd91c-129">[ **Update & Security**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-129">Select **Update & Security**.</span></span>

   ![Surface Hub 用の設定アプリの [更新 & セキュリティ] グループを示す画像。](images/sh-settings-update-security.png)

1. <span data-ttu-id="cd91c-131">[**回復**] を選択し、[**デバイスのリセット**] で [**はじめ**に] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-131">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   ![Surface Hub 用の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   <span data-ttu-id="cd91c-133">リセットプロセスが完了すると、Surface Hub は、[最初の run プログラム](first-run-program-surface-hub.md)をもう一度開始します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-133">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="cd91c-134">リセットプロセスで問題が発生した場合は、Surface Hub を以前の既存のオペレーティングシステムイメージにロールバックし、[ようこそ] 画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-134">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <span data-ttu-id="cd91c-135">クラウドから Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="cd91c-135">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="cd91c-136">何らかの理由で Surface Hub が使用できなくなった場合は、Microsoft サポートの支援なしでクラウドから回復することができます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-136">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="cd91c-137">Surface Hub はクラウドから新しいオペレーティングシステムイメージをダウンロードし、そのイメージを使用してそのオペレーティングシステムを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-137">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="cd91c-138">次のような状況では、この種の回復プロセスを使用することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-138">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="cd91c-139">Surface Hub またはその関連アカウントが不安定な状態になった</span><span class="sxs-lookup"><span data-stu-id="cd91c-139">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="cd91c-140">Surface Hub がロックされている</span><span class="sxs-lookup"><span data-stu-id="cd91c-140">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="cd91c-141">**クラウドプロセスから回復**するには、インターネット接続を開く必要があります (プロキシやその他の認証は必要ありません)。</span><span class="sxs-lookup"><span data-stu-id="cd91c-141">The **Recover from the cloud** process requires an open internet connection (no proxy or other authentications).</span></span> <span data-ttu-id="cd91c-142">イーサネット接続をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-142">An ethernet connection is recommended.</span></span>

### <span data-ttu-id="cd91c-143">正常な状態でない Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="cd91c-143">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="cd91c-144">デバイスアカウントが不安定な状態になった場合、または管理者アカウントで問題が発生した場合は、設定アプリを使用してクラウドの回復プロセスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-144">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="cd91c-145">[デバイスのリセット](#reset-a-surface-hub)プロセスで問題が解決されない場合にのみ、クラウド回復プロセスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="cd91c-145">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="cd91c-146">Surface Hub で、[**設定**の &gt; **更新 & セキュリティ** &gt; **回復**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-146">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

1. <span data-ttu-id="cd91c-147">[**クラウドからの回復**] で、[**今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-147">Under **Recover from the cloud**, select **Restart now**.</span></span>

   ![クラウドから回復する](images/recover-from-the-cloud.png)

### <span data-ttu-id="cd91c-149">ロックされた Surface Hub を回復する</span><span class="sxs-lookup"><span data-stu-id="cd91c-149">Recover a locked Surface Hub</span></span>

<span data-ttu-id="cd91c-150">まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-150">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="cd91c-151">この問題が発生すると、デバイスは自動的に再起動し、操作を再び試みます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-151">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="cd91c-152">ただし、この操作が繰り返し失敗すると、デバイスは自動的にロックを解除してユーザーデータを保護します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-152">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="cd91c-153">ロックを解除するには、[デバイスをリセット](#reset-a-surface-hub)するか、それが機能しない場合はクラウドからデバイスを回復する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-153">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="cd91c-154">Surface Hub の下部にある電源スイッチを見つけます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-154">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="cd91c-155">電源スイッチは、電源ケーブル接続の横にあります。</span><span class="sxs-lookup"><span data-stu-id="cd91c-155">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="cd91c-156">Power switch の詳細については、 [Surface Hub のサイト準備ガイド (PDF)](surface-hub-site-readiness-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd91c-156">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

1. <span data-ttu-id="cd91c-157">Surface Hub には [ようこそ] 画面が表示されていますが、power switch を使って Surface Hub をオフにします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-157">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

1. <span data-ttu-id="cd91c-158">Power switch を使用して Surface Hub を再びオンにします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-158">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="cd91c-159">デバイスが起動し、Surface Hub ロゴ画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-159">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="cd91c-160">Surface Hub ロゴの下にスピンしている点が表示されたら、電源スイッチを使用して Surface Hub をもう一度オフにします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-160">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

1. <span data-ttu-id="cd91c-161">手順 3 3 を繰り返すか、Surface Hub に "自動修復の準備中" というメッセージが表示されるまで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-161">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="cd91c-162">このメッセージが表示されると、Surface Hub に Windows RE の画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-162">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>

1. <span data-ttu-id="cd91c-163">[**詳細オプション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-163">Select **Advanced Options**.</span></span>

1. <span data-ttu-id="cd91c-164">[**クラウドからの回復**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-164">Select **Recover from the cloud**.</span></span> <span data-ttu-id="cd91c-165">(必要に応じて、[**リセット**] を選ぶこともできます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-165">(Optionally, you can select **Reset**.</span></span> <span data-ttu-id="cd91c-166">ただし、**クラウドからの回復**は、推奨される方法です。)</span><span class="sxs-lookup"><span data-stu-id="cd91c-166">However, **Recover from the cloud** is the recommended approach.)</span></span>

   ![クラウドからの回復](images/recover-from-cloud.png)
1. <span data-ttu-id="cd91c-168">Bitlocker キーの入力を求めるメッセージが表示された場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="cd91c-168">If you are prompted to enter the Bitlocker key, do one of the following:</span></span>

   - <span data-ttu-id="cd91c-169">Surface Hub で Bitlocker で保護されている情報を維持するには、Bitlocker キーを入力します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-169">To preserve the information that Bitlocker protects on the Surface Hub, enter the Bitlocker key.</span></span>
   - <span data-ttu-id="cd91c-170">保護された情報を破棄するには、[**このドライブをスキップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-170">To discard the protected information, select **Skip this drive**</span></span>  

1. <span data-ttu-id="cd91c-171">メッセージが表示されたら、[**再インストール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd91c-171">When you are prompted, select **Reinstall**.</span></span>

    ![再インストール](images/reinstall.png)

1. <span data-ttu-id="cd91c-173">ディスクのパーティションを再分割するには、[**はい]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-173">To repartition the disk, select **Yes**.</span></span>

   ![パーティションの再作成](images/repartition.png)

   <span data-ttu-id="cd91c-175">まず、回復プロセスでクラウドからオペレーティングシステムイメージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="cd91c-175">First, the recovery process downloads the operating system image from the cloud.</span></span>  

   ![ダウンロード中 97&](images/recover-progress.png)

   <span data-ttu-id="cd91c-177">ダウンロードが完了すると、回復プロセスによって、選択したオプションに従って Surface Hub が復元されます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-177">When the download finishes, the recovery process restores the Surface Hub according to the options that you selected.</span></span>
   

## <span data-ttu-id="cd91c-178">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="cd91c-178">Contact Support</span></span>

<span data-ttu-id="cd91c-179">質問がある場合やヘルプが必要な場合は、[サポートリクエストを作成](https://support.microsoft.com/supportforbusiness/productselection)できます。</span><span class="sxs-lookup"><span data-stu-id="cd91c-179">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <span data-ttu-id="cd91c-180">関連トピック</span><span class="sxs-lookup"><span data-stu-id="cd91c-180">Related topics</span></span>

[<span data-ttu-id="cd91c-181">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="cd91c-181">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="cd91c-182">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="cd91c-182">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)
