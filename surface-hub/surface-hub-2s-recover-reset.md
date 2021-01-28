---
title: Surface Hub 2S のリセットと回復
description: Surface Hub 2S を回復してリセットする方法について学習します。
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
ms.openlocfilehash: 88f5d912f7505aecaa5bd7ba659acab2d6c4fa1a
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304810"
---
# <span data-ttu-id="b73c4-104">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="b73c4-104">Reset and recovery for Surface Hub 2S</span></span>

<span data-ttu-id="b73c4-105">Surface Hub 2S で問題が発生した場合は、デバイスを出荷時の設定にリセットするか、USB ドライブを使用して復元できます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-105">If you encounter problems with Surface Hub 2S, you can reset the device to factory settings or restore by using a USB drive.</span></span>

<span data-ttu-id="b73c4-106">まず、管理者の資格情報で Surface Hub 2S にサインインし\*\*\*\*、設定アプリを\*\*\*\* 開き、[更新とセキュリティ] &を選択して、[回復] を選択**します**。</span><span class="sxs-lookup"><span data-stu-id="b73c4-106">To begin, sign in to Surface Hub 2S with admin credentials, open the **Settings** app, select **Update & security**, and then select **Recovery**.</span></span>

## <span data-ttu-id="b73c4-107">デバイスをリセットする</span><span class="sxs-lookup"><span data-stu-id="b73c4-107">Reset the device</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="b73c4-108">デバイスをリセットする前に、BitLocker キーが利用可能な状態にしてください(後で入力を求めるメッセージが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="b73c4-108">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="b73c4-109">詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="b73c4-109">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

1. <span data-ttu-id="b73c4-110">デバイスをリセットするには、[開始] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="b73c4-110">To reset the device, select **Get Started**.</span></span>

2. <span data-ttu-id="b73c4-111">When the **Ready to reset this device window** appears, select **Reset**.</span><span class="sxs-lookup"><span data-stu-id="b73c4-111">When the **Ready to reset this device** window appears, select **Reset**.</span></span> 
  
   > [!IMPORTANT]
   > <span data-ttu-id="b73c4-112">ハブが回復パーティションに再起動すると、BitLocker キーの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-112">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="b73c4-113">このプロンプトをスキップすると、リセットが失敗します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-113">Skipping that prompt will cause reset to fail.</span></span> <span data-ttu-id="b73c4-114">BitLocker キーを入力すると、Hub は回復パーティションからオペレーティング システムを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="b73c4-114">Once you enter the BitLocker key the Hub reinstalls the operating system from the recovery partition.</span></span> <span data-ttu-id="b73c4-115">完了まで最大 1 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b73c4-115">This may take up to one hour to complete.</span></span>
  
3. <span data-ttu-id="b73c4-116">デバイスを再構成するには、初回セットアップ プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-116">To reconfigure the device, run the first-time Setup program.</span></span>

4. <span data-ttu-id="b73c4-117">Microsoft Intune または別のモバイル デバイス管理ソリューションを使用してデバイスを管理する場合は、前のレコードを廃止して削除してから、新しいデバイスを再登録します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-117">If you manage the device using Microsoft Intune or another mobile device management solution, retire and delete the previous record, and then re-enroll the new device.</span></span> <span data-ttu-id="b73c4-118">詳細については、「ワイプ、リタイア、または手動によるデバイスの登録解除を使用してデバイスを削除する」を [参照してください](https://docs.microsoft.com/intune/devices-wipe)。</span><span class="sxs-lookup"><span data-stu-id="b73c4-118">For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/devices-wipe).</span></span>

   > [!div class="mx-imgBorder"]
   > ![*Surface Hub 2S のリセットと回復*](images/sh2-reset.png)
   <br/>*<span data-ttu-id="b73c4-120">図 1. </span><span class="sxs-lookup"><span data-stu-id="b73c4-120">Figure 1.</span></span> <span data-ttu-id="b73c4-121">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="b73c4-121">Reset and recovery for Surface Hub 2S</span></span>* 

## <span data-ttu-id="b73c4-122">USB 回復ドライブを使用して Surface Hub 2S を回復する</span><span class="sxs-lookup"><span data-stu-id="b73c4-122">Recover Surface Hub 2S by using a USB recovery drive</span></span>

<span data-ttu-id="b73c4-123">Surface Hub 2S の新機能として、回復イメージを使用してデバイスを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-123">New in Surface Hub 2S, you can now reinstall the device by using a recovery image.</span></span>

### <span data-ttu-id="b73c4-124">USB ドライブからの回復</span><span class="sxs-lookup"><span data-stu-id="b73c4-124">Recovery from a USB drive</span></span>

<span data-ttu-id="b73c4-125">Surface Hub 2S を使用すると、回復イメージを使用してデバイスを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-125">Using Surface Hub 2S, you can reinstall the device by using a recovery image.</span></span> <span data-ttu-id="b73c4-126">これにより、BitLocker キーを紛失した場合、または設定アプリの管理者資格情報を持たなくなった場合に、デバイスを出荷時の設定に再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-126">By doing this, you can reinstall the device to the factory settings if you lost the BitLocker key, or if you no longer have admin credentials to the Settings app.</span></span>

>[!NOTE]
><span data-ttu-id="b73c4-127">FAT32 としてフォーマットされた 8 GB または 16 GB のストレージを備える USB 3.0 ドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-127">Use a USB 3.0 drive with 8 GB or 16 GB of storage, formatted as FAT32.</span></span>

1. <span data-ttu-id="b73c4-128">別の PC から [、Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) Web サイトから .zip ファイルの回復イメージをダウンロードし、次の手順に戻ってください。</span><span class="sxs-lookup"><span data-stu-id="b73c4-128">From a separate PC, download the .zip file recovery image from the [Surface Recovery website](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) and then return to these instructions.</span></span> 

1. <span data-ttu-id="b73c4-129">ダウンロードしたファイルを USB ドライブのルートに解凍します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-129">Unzip the downloaded file onto the root of the USB drive.</span></span>  

1. <span data-ttu-id="b73c4-130">USB ドライブを Surface Hub 2S 上の USB-C ポートまたは USB-A ポートに接続します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-130">Connect the USB drive to any USB-C or USB-A port on Surface Hub 2S.</span></span>

1. <span data-ttu-id="b73c4-131">デバイスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b73c4-131">Turn off the device:</span></span>

   1. <span data-ttu-id="b73c4-132">音量ボタンを押しながら、電源ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-132">While pressing the Volume down button, press the Power button.</span></span>
   1. <span data-ttu-id="b73c4-133">Windows ロゴが表示されるまで、両方のボタンを押し続けます。</span><span class="sxs-lookup"><span data-stu-id="b73c4-133">Keep pressing both buttons until you see the Windows logo.</span></span>
   1. <span data-ttu-id="b73c4-134">電源ボタンを離しますが、インストール UI が開始するまで音量を下すボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="b73c4-134">Release the Power button but continue to hold the Volume down button until the Install UI begins.</span></span>

      ![*ボリューム ダウンボタンと電源ボタンを使用して回復を開始する*](images/sh2-keypad.png)
      <br>*<span data-ttu-id="b73c4-136">図 2. </span><span class="sxs-lookup"><span data-stu-id="b73c4-136">Figure 2.</span></span> <span data-ttu-id="b73c4-137">音量ボタンと電源ボタン</span><span class="sxs-lookup"><span data-stu-id="b73c4-137">Volume and Power buttons</span></span>*

1. <span data-ttu-id="b73c4-138">言語選択画面で、Surface Hub 2S の表示言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-138">On the language selection screen, select the display language for your Surface Hub 2S.</span></span>

1. <span data-ttu-id="b73c4-139">Select **Recover from a drive** and **Fully clean the drive,** and then select **Recover**.</span><span class="sxs-lookup"><span data-stu-id="b73c4-139">Select **Recover from a drive** and **Fully clean the drive**, and then select **Recover**.</span></span> <span data-ttu-id="b73c4-140">BitLocker キーの入力を求めるメッセージが表示されたら、[このドライブをスキップする] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="b73c4-140">If you're prompted for a BitLocker key, select **Skip this drive**.</span></span> <span data-ttu-id="b73c4-141">Surface Hub 2S は数回再起動し、回復プロセスが完了するのに約 30 分かかります。</span><span class="sxs-lookup"><span data-stu-id="b73c4-141">Surface Hub 2S reboots several times and takes approximately 30 minutes to complete the recovery process.</span></span>

<span data-ttu-id="b73c4-142">初回セットアップ画面が表示されたら、USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="b73c4-142">When the first-time setup screen appears, remove the USB drive.</span></span>

## <span data-ttu-id="b73c4-143">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="b73c4-143">Contact Support</span></span>

<span data-ttu-id="b73c4-144">質問がある場合やサポートが必要な場合は、サポート [リクエストを作成できます](https://support.microsoft.com/supportforbusiness/productselection)。</span><span class="sxs-lookup"><span data-stu-id="b73c4-144">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>
