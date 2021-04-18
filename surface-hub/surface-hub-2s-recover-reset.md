---
title: Surface Hub 2S のリセットと回復
description: Surface Hub 2S を回復およびリセットする方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/05/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 64ceee291d3d3e067f581707d9431fa92398c785
ms.sourcegitcommit: ecb4909c091e69b7bdb1faacfc8c34b480dc884b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "11342977"
---
# <span data-ttu-id="a5ca6-104">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="a5ca6-104">Reset and recovery for Surface Hub 2S</span></span>

<span data-ttu-id="a5ca6-105">Surface Hub 2S で問題が発生した場合は、デバイスを工場出荷時の設定にリセットするか、USB ドライブを使用して復元できます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-105">If you encounter problems with Surface Hub 2S, you can reset the device to factory settings or restore by using a USB drive.</span></span>

<span data-ttu-id="a5ca6-106">まず、管理者の資格情報を使用して Surface Hub 2S にサインインし、**[設定]** アプリを開き、**[更新とセキュリティ]**、**[回復]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-106">To begin, sign in to Surface Hub 2S with admin credentials, open the **Settings** app, select **Update & security**, and then select **Recovery**.</span></span>

## <span data-ttu-id="a5ca6-107">デバイスをリセットする</span><span class="sxs-lookup"><span data-stu-id="a5ca6-107">Reset the device</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="a5ca6-108">デバイスをリセットする前に、BitLocker キーが使用できることを確認してください。後で入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-108">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="a5ca6-109">詳細については、「[BitLocker キーの保存](save-bitlocker-key-surface-hub.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-109">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

1. <span data-ttu-id="a5ca6-110">デバイスをリセットするには、**[作業の開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-110">To reset the device, select **Get Started**.</span></span>

2. <span data-ttu-id="a5ca6-111">**[このデバイスをリセットする準備完了]** ウィンドウが表示されたら、**[リセット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-111">When the **Ready to reset this device** window appears, select **Reset**.</span></span> 
  
   > [!IMPORTANT]
   > <span data-ttu-id="a5ca6-112">ハブが回復パーティションに再起動すると、BitLocker キーを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-112">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="a5ca6-113">このプロンプトをスキップすると、リセットが失敗します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-113">Skipping that prompt will cause reset to fail.</span></span> <span data-ttu-id="a5ca6-114">BitLocker キーを入力すると、ハブは回復パーティションからオペレーティング システムを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-114">Once you enter the BitLocker key the Hub reinstalls the operating system from the recovery partition.</span></span> <span data-ttu-id="a5ca6-115">完了には最大 1 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-115">This may take up to one hour to complete.</span></span>
  
3. <span data-ttu-id="a5ca6-116">デバイスを再構成するには、初回セットアップ プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-116">To reconfigure the device, run the first-time Setup program.</span></span>

4. <span data-ttu-id="a5ca6-117">Microsoft Intune または別のモバイル デバイス管理ソリューションを使用してデバイスを管理する場合は、前のレコードをインベントリから削除してから削除し、新しいデバイスを再登録します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-117">If you manage the device using Microsoft Intune or another mobile device management solution, retire and delete the previous record, and then re-enroll the new device.</span></span> <span data-ttu-id="a5ca6-118">詳細については、「[ワイプ、インベントリからの削除、デバイス登録の手動解除を使用し、デバイスを削除する](https://docs.microsoft.com/intune/devices-wipe)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-118">For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/devices-wipe).</span></span>

   > [!div class="mx-imgBorder"]
   > ![*Surface Hub 2S のリセットと回復*](images/sh2-reset.png)
   <br/>*<span data-ttu-id="a5ca6-120">図 1.</span><span class="sxs-lookup"><span data-stu-id="a5ca6-120">Figure 1.</span></span> <span data-ttu-id="a5ca6-121">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="a5ca6-121">Reset and recovery for Surface Hub 2S</span></span>* 

## <span data-ttu-id="a5ca6-122">USB 回復ドライブを使用して Surface Hub 2S を回復する</span><span class="sxs-lookup"><span data-stu-id="a5ca6-122">Recover Surface Hub 2S by using a USB recovery drive</span></span>

<span data-ttu-id="a5ca6-123">Surface Hub 2S の新機能で、回復イメージを使用してデバイスを再インストールできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-123">New in Surface Hub 2S, you can now reinstall the device by using a recovery image.</span></span>

### <span data-ttu-id="a5ca6-124">USB ドライブからの回復</span><span class="sxs-lookup"><span data-stu-id="a5ca6-124">Recovery from a USB drive</span></span>

<span data-ttu-id="a5ca6-125">Surface Hub 2S を使用すると、回復イメージを使用してデバイスを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-125">Using Surface Hub 2S, you can reinstall the device by using a recovery image.</span></span> <span data-ttu-id="a5ca6-126">これにより、BitLocker キーを紛失した場合、または設定アプリへの管理者の資格情報がなくなった場合に、デバイスを工場出荷時の設定に再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-126">By doing this, you can reinstall the device to the factory settings if you lost the BitLocker key, or if you no longer have admin credentials to the Settings app.</span></span>

>[!NOTE]
><span data-ttu-id="a5ca6-127">FAT32 形式でストレージが 8 GB または 16 GB の USB 3.0 ドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-127">Use a USB 3.0 drive with 8 GB or 16 GB of storage, formatted as FAT32.</span></span>

1. <span data-ttu-id="a5ca6-128">別の PC で、[Surface の回復に関する Web サイト](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s)から .zip ファイルの回復イメージをダウンロードし、これらの手順に戻ります。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-128">From a separate PC, download the .zip file recovery image from the [Surface Recovery website](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) and then return to these instructions.</span></span> 

1. <span data-ttu-id="a5ca6-129">タスクバーの検索ボックスに **"回復ドライブ"** と入力し、結果から **[回復ドライブの作成]** または **[回復ドライブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-129">In the search box on the taskbar, enter **recovery drive**, and then select **Create a recovery drive** or **Recovery Drive** from the results.</span></span> <span data-ttu-id="a5ca6-130">管理者パスワードを入力するか、選択内容を確認する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-130">You may need to enter an admin password or confirm your choice.</span></span>

1. <span data-ttu-id="a5ca6-131">**[ユーザー アカウント制御]** ボックスで、**[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-131">In the **User Account Control** box, select **Yes**.</span></span>

1. <span data-ttu-id="a5ca6-132">**[システム ファイルを回復ドライブにバックアップする]** チェック ボックスをオフにして、**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-132">Make sure to clear the **Back up system files to the recovery drive** check box and then select **Next**.</span></span>

1. <span data-ttu-id="a5ca6-133">USB ドライブを選択して、**[次へ] > [作成]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-133">Select your USB drive, and then select **Next > Create**.</span></span>  <span data-ttu-id="a5ca6-134">複数のユーティリティを回復ドライブにコピーする必要があるため、これには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-134">Some utilities need to be copied to the recovery drive, so this might take a few minutes.</span></span>

1. <span data-ttu-id="a5ca6-135">回復ドライブの準備ができたら、**[完了]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-135">When the recovery drive is ready, select **Finish**.</span></span>

1. <span data-ttu-id="a5ca6-136">以前にダウンロードした回復イメージの .zip ファイルをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-136">Double-click the recovery image .zip file that you previously downloaded to open it.</span></span>

1. <span data-ttu-id="a5ca6-137">回復イメージ フォルダーからすべてのファイルを選択し、USB ドライブのルートにコピーし、**[コピー先のファイルを置き換える]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-137">Select all the files from the recovery image folder, copy them to the root of your USB drive, and then select **Choose to replace the files in the destination**.</span></span>

1. <span data-ttu-id="a5ca6-138">ファイルのコピーが完了したら、タスクバーの **[ハードウェアを安全に取り外してメディアを取り出す]** アイコンを選択し、USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-138">Once the files have finished copying, select the **Safely Remove Hardware and Eject Media** icon on the taskbar, and remove your USB drive.</span></span>

1. <span data-ttu-id="a5ca6-139">Surface Hub 2S の任意の USB-C ポートまたは USB-A ポートに USB ドライブを接続します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-139">Connect the USB drive to any USB-C or USB-A port on the Surface Hub 2S.</span></span>

1. <span data-ttu-id="a5ca6-140">ハブをオフにして、次の手順を実行して USB ドライブから起動します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-140">Turn off the Hub and then take these steps to boot from the USB drive:</span></span>

   1. <span data-ttu-id="a5ca6-141">[音量を下げる] ボタンを押しながら、電源ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-141">While pressing the Volume down button, press the Power button.</span></span>
   1. <span data-ttu-id="a5ca6-142">Windows ロゴが表示されるまで、両方のボタンを押し続けます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-142">Keep pressing both buttons until you see the Windows logo.</span></span>
   1. <span data-ttu-id="a5ca6-143">電源ボタンを離し、インストール UI が開始するまで [音量を下げる] ボタンを押し続けます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-143">Release the Power button but continue to hold the Volume down button until the Install UI begins.</span></span>

      ![*[音量を下げる] ボタンと電源ボタンを使用して回復を開始する*](images/sh2-keypad.png)
      <br>*<span data-ttu-id="a5ca6-145">図 2.</span><span class="sxs-lookup"><span data-stu-id="a5ca6-145">Figure 2.</span></span> <span data-ttu-id="a5ca6-146">音量ボタンと電源ボタン</span><span class="sxs-lookup"><span data-stu-id="a5ca6-146">Volume and Power buttons</span></span>*

1. <span data-ttu-id="a5ca6-147">言語選択画面で、Surface Hub 2S の表示言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-147">On the language selection screen, select the display language for your Surface Hub 2S.</span></span>

1. <span data-ttu-id="a5ca6-148">**[ドライブから回復する]**、**[ドライブを完全にクリーニングする]** の順に選択し、**[回復]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-148">Select **Recover from a drive** and **Fully clean the drive**, and then select **Recover**.</span></span> <span data-ttu-id="a5ca6-149">BitLocker キーの入力が求められたら、**[このドライブをスキップする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-149">If you're prompted for a BitLocker key, select **Skip this drive**.</span></span> <span data-ttu-id="a5ca6-150">Surface Hub 2S は数回再起動し、回復プロセス完了には約 30 分かかります。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-150">Surface Hub 2S reboots several times and takes approximately 30 minutes to complete the recovery process.</span></span>

<span data-ttu-id="a5ca6-151">初回セットアップ画面が表示されたら、USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-151">When the first-time setup screen appears, remove the USB drive.</span></span>

## <span data-ttu-id="a5ca6-152">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="a5ca6-152">Contact Support</span></span>

<span data-ttu-id="a5ca6-153">ご質問がある場合や、移行を開始するためのサポートが必要な場合は、[サポート要求を作成](https://support.microsoft.com/supportforbusiness/productselection)できます。</span><span class="sxs-lookup"><span data-stu-id="a5ca6-153">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>
