---
title: Surface Hub 2S のリセットと回復
description: Surface Hub 2S を復元およびリセットする方法について説明します。
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
ms.openlocfilehash: e3b1e380f9776fc56e99b8d4e35f708aa952759c
ms.sourcegitcommit: e075b46f14b730464d66246b0280ef2cfa16b3fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "10963585"
---
# <span data-ttu-id="16c06-104">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="16c06-104">Reset and recovery for Surface Hub 2S</span></span>

<span data-ttu-id="16c06-105">Surface Hub 2S で問題が発生した場合は、デバイスを出荷時の設定にリセットするか、USB ドライブを使って復元することができます。</span><span class="sxs-lookup"><span data-stu-id="16c06-105">If you encounter problems with Surface Hub 2S, you can reset the device to factory settings or restore by using a USB drive.</span></span>

<span data-ttu-id="16c06-106">開始するには、管理者の資格情報で Surface Hub 2S にサインインし、[ **設定** ] アプリを開き、[ **更新 & のセキュリティ**] を選択して、[ **回復**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="16c06-106">To begin, sign in to Surface Hub 2S with admin credentials, open the **Settings** app, select **Update & security**, and then select **Recovery**.</span></span>

## <span data-ttu-id="16c06-107">デバイスをリセットする</span><span class="sxs-lookup"><span data-stu-id="16c06-107">Reset the device</span></span>

1. <span data-ttu-id="16c06-108">デバイスをリセットするには、[ **はじめ**に] を選びます。</span><span class="sxs-lookup"><span data-stu-id="16c06-108">To reset the device, select **Get Started**.</span></span>

2. <span data-ttu-id="16c06-109">[ **このデバイスをリセットする準備ができ** ました] ウィンドウが表示されたら、[ **リセット**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="16c06-109">When the **Ready to reset this device** window appears, select **Reset**.</span></span> 
  
   > [!NOTE]
   > <span data-ttu-id="16c06-110">Surface Hub 2S 回復パーティションからオペレーティングシステムを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="16c06-110">Surface Hub 2S reinstalls the operating system from the recovery partition.</span></span> <span data-ttu-id="16c06-111">完了までに最長で1時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="16c06-111">This may take up to one hour to complete.</span></span>
  
3. <span data-ttu-id="16c06-112">デバイスを再構成するには、1回目のセットアッププログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="16c06-112">To reconfigure the device, run the first-time Setup program.</span></span>

4. <span data-ttu-id="16c06-113">Microsoft Intune または他のモバイルデバイス管理ソリューションを使用してデバイスを管理している場合は、以前のレコードを削除してから、新しいデバイスを再登録します。</span><span class="sxs-lookup"><span data-stu-id="16c06-113">If you manage the device using Microsoft Intune or another mobile device management solution, retire and delete the previous record, and then re-enroll the new device.</span></span> <span data-ttu-id="16c06-114">詳細については、「 [デバイスのワイプまたは削除を使用してデバイスを削除する」または「手動でデバイスを登録解除する](https://docs.microsoft.com/intune/devices-wipe)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c06-114">For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/devices-wipe).</span></span>

> [!div class="mx-imgBorder"]
> ![\* Surface Hub 2S のリセットと回復 \*](images/sh2-reset.png)
<br/>*<span data-ttu-id="16c06-116">図 1. </span><span class="sxs-lookup"><span data-stu-id="16c06-116">Figure 1.</span></span> <span data-ttu-id="16c06-117">Surface Hub 2S のリセットと回復</span><span class="sxs-lookup"><span data-stu-id="16c06-117">Reset and recovery for Surface Hub 2S</span></span>* 

## <span data-ttu-id="16c06-118">USB 回復ドライブを使用して Surface Hub 2S を回復する</span><span class="sxs-lookup"><span data-stu-id="16c06-118">Recover Surface Hub 2S by using a USB recovery drive</span></span>

<span data-ttu-id="16c06-119">Surface Hub 2S の新機能により、回復イメージを使用してデバイスを再インストールできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="16c06-119">New in Surface Hub 2S, you can now reinstall the device by using a recovery image.</span></span>

### <span data-ttu-id="16c06-120">USB ドライブからの回復</span><span class="sxs-lookup"><span data-stu-id="16c06-120">Recovery from a USB drive</span></span>

<span data-ttu-id="16c06-121">Surface Hub 2S を使って、回復イメージを使用してデバイスを再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="16c06-121">Using Surface Hub 2S, you can reinstall the device by using a recovery image.</span></span> <span data-ttu-id="16c06-122">これにより、BitLocker キーを紛失した場合、または設定アプリの管理者資格情報がなくなった場合に、デバイスを出荷時の設定に再インストールできます。</span><span class="sxs-lookup"><span data-stu-id="16c06-122">By doing this, you can reinstall the device to the factory settings if you lost the BitLocker key, or if you no longer have admin credentials to the Settings app.</span></span>

>[!NOTE]
><span data-ttu-id="16c06-123">8 GB または 16 GB のストレージで、FAT32 として書式設定された USB 3.0 ドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="16c06-123">Use a USB 3.0 drive with 8 GB or 16 GB of storage, formatted as FAT32.</span></span>

1. <span data-ttu-id="16c06-124">別の PC から、 [Surface recovery web サイト](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) から .zip ファイルの回復イメージをダウンロードして、次の手順に戻ります。</span><span class="sxs-lookup"><span data-stu-id="16c06-124">From a separate PC, download the .zip file recovery image from the [Surface Recovery website](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) and then return to these instructions.</span></span> 

1. <span data-ttu-id="16c06-125">ダウンロードしたファイルを USB ドライブのルートに解凍します。</span><span class="sxs-lookup"><span data-stu-id="16c06-125">Unzip the downloaded file onto the root of the USB drive.</span></span>  

1. <span data-ttu-id="16c06-126">Usb ドライブを USB-C または USB に接続します (Surface Hub 2S の場合)。</span><span class="sxs-lookup"><span data-stu-id="16c06-126">Connect the USB drive to any USB-C or USB-A port on Surface Hub 2S.</span></span>

1. <span data-ttu-id="16c06-127">デバイスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="16c06-127">Turn off the device:</span></span>

   1. <span data-ttu-id="16c06-128">[音量を下げる] ボタンを押しながら、電源ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="16c06-128">While pressing the Volume down button, press the Power button.</span></span>
   1. <span data-ttu-id="16c06-129">Windows ロゴが表示されるまで、両方のボタンを押し続けます。</span><span class="sxs-lookup"><span data-stu-id="16c06-129">Keep pressing both buttons until you see the Windows logo.</span></span>
   1. <span data-ttu-id="16c06-130">電源ボタンを放しますが、インストール UI が開始されるまでは [音量を下げる] ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="16c06-130">Release the Power button but continue to hold the Volume down button until the Install UI begins.</span></span>

   ![\* ボリュームダウンと電源ボタンを使用して回復 \* を開始 \*](images/sh2-keypad.png) <br>
   **<span data-ttu-id="16c06-132">図 2. </span><span class="sxs-lookup"><span data-stu-id="16c06-132">Figure 2.</span></span> <span data-ttu-id="16c06-133">ボリュームと電源ボタン</span><span class="sxs-lookup"><span data-stu-id="16c06-133">Volume and Power buttons</span></span>**

1. <span data-ttu-id="16c06-134">[言語の選択] 画面で、Surface Hub 2S の表示言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="16c06-134">On the language selection screen, select the display language for your Surface Hub 2S.</span></span>

1. <span data-ttu-id="16c06-135">[ **ドライブからの回復** ] を選択し、 **ドライブを完全にクリーンアップ**して、[ **復元**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="16c06-135">Select **Recover from a drive** and **Fully clean the drive**, and then select **Recover**.</span></span> <span data-ttu-id="16c06-136">BitLocker キーの入力を求めるメッセージが表示されたら、[ **このドライブをスキップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="16c06-136">If you're prompted for a BitLocker key, select **Skip this drive**.</span></span> <span data-ttu-id="16c06-137">Surface Hub 2S は何度か再起動します。回復処理が完了するまでに約30分かかります。</span><span class="sxs-lookup"><span data-stu-id="16c06-137">Surface Hub 2S reboots several times and takes approximately 30 minutes to complete the recovery process.</span></span>

<span data-ttu-id="16c06-138">初回起動時のセットアップ画面が表示されたら、USB ドライブを削除します。</span><span class="sxs-lookup"><span data-stu-id="16c06-138">When the first-time setup screen appears, remove the USB drive.</span></span>

## <span data-ttu-id="16c06-139">サポートに問い合わせ</span><span class="sxs-lookup"><span data-stu-id="16c06-139">Contact Support</span></span>

<span data-ttu-id="16c06-140">質問がある場合やヘルプが必要な場合は、 [サポートリクエストを作成](https://support.microsoft.com/supportforbusiness/productselection)できます。</span><span class="sxs-lookup"><span data-stu-id="16c06-140">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>
