---
title: Surface Hub 2S のペン ファームウェアを更新する
description: このページでは、2 ペンのファームウェアを更新Surface Hub説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 04/15/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 6f1ca4f05653ec798ed1b47d2e42e974e7f7414d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576957"
---
# <a name="update-pen-firmware-on-surface-hub-2s"></a><span data-ttu-id="1a98a-104">Surface Hub 2S のペン ファームウェアを更新する</span><span class="sxs-lookup"><span data-stu-id="1a98a-104">Update pen firmware on Surface Hub 2S</span></span>

<span data-ttu-id="1a98a-105">ファームウェアは、Surface Hub 2 ペンWindowsから、または別の PC にファームウェア更新プログラムをダウンロードして更新できます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-105">You can update firmware on Surface Hub 2 pen from Windows Update for Business or by downloading the firmware update to a separate PC.</span></span> <span data-ttu-id="1a98a-106">更新されたファームウェアは、2020 Windows 2 月 26 日から更新プログラムから利用できます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-106">Updated firmware is available from Windows Update beginning February 26, 2020.</span></span> 

## <a name="update-pen-firmware-using-windows-update-for-business"></a><span data-ttu-id="1a98a-107">Update for Business を使用してペンWindowsを更新する</span><span class="sxs-lookup"><span data-stu-id="1a98a-107">Update pen firmware using Windows Update for Business</span></span>

<span data-ttu-id="1a98a-108">このセクションでは、Windows Update の自動メンテナンス サイクルを使用してペン ファームウェアを更新する方法について説明します。既定では、夜間 3 時に発生するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="1a98a-108">This section describes how to update pen firmware via the automated maintenance cycles for Windows Update, configured by default to occur nightly at 3 a.m.</span></span> <span data-ttu-id="1a98a-109">更新プログラムを 2 ペンに適用する前に、2 つのメンテナンス サイクルを完了Surface Hub必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-109">You will need to plan for two maintenance cycles to complete before applying the update to the Surface Hub 2 pen.</span></span> <span data-ttu-id="1a98a-110">または、他の更新プログラムと同様に、Windows Update for Business (WUfB) を使用してペン ファームウェアを適用できます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-110">Alternately, like any other update, you can use Windows Update for Business (WUfB) to apply the pen firmware.</span></span> <span data-ttu-id="1a98a-111">詳細については、「更新プログラムの[管理」をWindowsを参照Surface Hub。](manage-windows-updates-for-surface-hub.md)</span><span class="sxs-lookup"><span data-stu-id="1a98a-111">For more information, see [Managing Windows updates on Surface Hub](manage-windows-updates-for-surface-hub.md).</span></span>

1. <span data-ttu-id="1a98a-112">Surface Hub 2 ペンが Surface Hub 2S にペアリングされている必要があります。白いインジケーター \*\*\*\* LED ライトが点滅し始めるまで、トップ ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-112">Ensure the Surface Hub 2 pen is paired to Surface Hub 2S: Press and hold the **top** button until the white indicator LED light begins to blink.</span></span> <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. <span data-ttu-id="1a98a-114">このSurface Hub管理者としてログインし、**新しいデバイス**設定開き、新しいデバイスBluetoothします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-114">On Surface Hub, login as an Admin, open **Settings**, and then scan for new Bluetooth devices.</span></span>
3. <span data-ttu-id="1a98a-115">ペンを選択してペアリングプロセスを完了します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-115">Select the pen to complete the pairing process.</span></span>
4. <span data-ttu-id="1a98a-116">ペンの **上ボタン** を押して更新プログラムを適用します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-116">Press the **top** button on the pen to apply the update.</span></span> <span data-ttu-id="1a98a-117">完了には最大 2 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-117">It may take up to two hours to complete.</span></span>

## <a name="update-pen-firmware-by-downloading-to-separate-pc"></a><span data-ttu-id="1a98a-118">個別の PC にダウンロードしてペンのファームウェアを更新する</span><span class="sxs-lookup"><span data-stu-id="1a98a-118">Update pen firmware by downloading to separate PC</span></span>

<span data-ttu-id="1a98a-119">2 ペンのファームウェアは、Surface Hub実行している別の PC から更新Windows 10。</span><span class="sxs-lookup"><span data-stu-id="1a98a-119">You can update the firmware on Surface Hub 2 pen from a separate PC running Windows 10.</span></span> <span data-ttu-id="1a98a-120">また、このメソッドを使用すると、ペン のファームウェアが最新バージョンに正常に更新されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-120">This method also enables you to verify that the pen firmware has successfully updated to the latest version.</span></span>

1. <span data-ttu-id="1a98a-121">Surface Hub 2 ペンを Bluetooth 対応 PC とペアリングします。白いインジケーター LED\*\*\*\* ライトが点滅し始めるまで、トップ ボタンを長押しします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-121">Pair the Surface Hub 2 pen to your Bluetooth-capable PC: Press and hold the **top** button until the white indicator LED light begins to blink.</span></span> <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. <span data-ttu-id="1a98a-123">PC で、新しいデバイスをBluetoothします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-123">On the PC, scan for new Bluetooth devices.</span></span>
3. <span data-ttu-id="1a98a-124">ペンを選択してペアリングプロセスを完了します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-124">Select the pen to complete the pairing process.</span></span>
4. <span data-ttu-id="1a98a-125">新しい更新プログラムをSurface Hubする前に、他のすべての 2s ペンを切断します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-125">Disconnect all other Surface Hub 2s pens before starting a new update.</span></span>
3. <span data-ttu-id="1a98a-126">PC に[Surface Hub 2 ペン ファームウェア更新ツール](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-126">Download the [Surface Hub 2 Pen Firmware Update Tool](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip) to your PC.</span></span>
4. <span data-ttu-id="1a98a-127">実行 **PenCfu.exe。**</span><span class="sxs-lookup"><span data-stu-id="1a98a-127">Run **PenCfu.exe.**</span></span> <span data-ttu-id="1a98a-128">インストールの進行状況がツールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-128">The install progress is displayed in the tool.</span></span> <span data-ttu-id="1a98a-129">更新が完了するために数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-129">It may take several minutes to finish updating.</span></span> 


## <a name="check-firmware-version-of-surface-hub-2-pen"></a><span data-ttu-id="1a98a-130">2 ペンのファームウェア バージョンSurface Hub確認する</span><span class="sxs-lookup"><span data-stu-id="1a98a-130">Check firmware version of Surface Hub 2 pen</span></span>

1. <span data-ttu-id="1a98a-131">**[get_version.bat**を実行し、ペンの**上**ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-131">Run **get_version.bat** and press the **top** button on the pen.</span></span>
2. <span data-ttu-id="1a98a-132">ツールは、ペンのファームウェア バージョンを報告します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-132">The tool will report the firmware version of the pen.</span></span> <span data-ttu-id="1a98a-133">例:</span><span class="sxs-lookup"><span data-stu-id="1a98a-133">Example:</span></span>
    - <span data-ttu-id="1a98a-134">古いファームウェアは 468.2727.368 です</span><span class="sxs-lookup"><span data-stu-id="1a98a-134">Old firmware is 468.2727.368</span></span>
    - <span data-ttu-id="1a98a-135">新しいファームウェアは 468.3347.368 です</span><span class="sxs-lookup"><span data-stu-id="1a98a-135">New firmware is 468.3347.368</span></span>

## <a name="command-line-options"></a><span data-ttu-id="1a98a-136">コマンド ライン オプション</span><span class="sxs-lookup"><span data-stu-id="1a98a-136">Command line options</span></span>

<span data-ttu-id="1a98a-137">コマンド ラインから Surface Hub 2 ペン ファームウェア更新ツール (PenCfu.exe) を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-137">You can run Surface Hub 2 Pen Firmware Update Tool (PenCfu.exe) from the command line.</span></span>

1. <span data-ttu-id="1a98a-138">ペンを PC にペアリングし、ペンの **上ボタン** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-138">Pair the pen to your PC and click the **top** button on the pen.</span></span>
2. <span data-ttu-id="1a98a-139">[ファームウェアの更新 **PenCfu.exe** を開始するには、[次へ] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a98a-139">Double click **PenCfu.exe** to initiate the firmware update.</span></span> <span data-ttu-id="1a98a-140">構成ファイルとファームウェア イメージ ファイルは、ツールと同じフォルダーに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-140">Note that the configuration file and the firmware image files must be stored in the same folder as the tool.</span></span>
3. <span data-ttu-id="1a98a-141">その他のオプションについては \*\* 、PenCfu.exe -h\*\* を実行して、次の表に示す使用可能なパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-141">For additional options, run **PenCfu.exe -h** to display the available parameters, as listed in the following table.</span></span>  
    - <span data-ttu-id="1a98a-142">例: PenCfu.exe -h</span><span class="sxs-lookup"><span data-stu-id="1a98a-142">Example: PenCfu.exe -h</span></span>
4. <span data-ttu-id="1a98a-143">ツール **を安全にシャットダウンするには、Ctrl** + C と入力します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-143">Enter **Ctrl+C** to safely shut down the tool.</span></span>

 

| **<span data-ttu-id="1a98a-144">コマンド</span><span class="sxs-lookup"><span data-stu-id="1a98a-144">Command</span></span>**    | **<span data-ttu-id="1a98a-145">説明</span><span class="sxs-lookup"><span data-stu-id="1a98a-145">Description</span></span>**                                                                                                                                                                                                                                                                                                                                                                                |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1a98a-146">-h ヘルプ</span><span class="sxs-lookup"><span data-stu-id="1a98a-146">-h help</span></span>        | <span data-ttu-id="1a98a-147">表示ツールのコマンド ライン インターフェイスのヘルプと終了。</span><span class="sxs-lookup"><span data-stu-id="1a98a-147">Display tool command line interface help and exit.</span></span>                                                                                                                                                                                                                                                                                                                                             |
| <span data-ttu-id="1a98a-148">-v バージョン</span><span class="sxs-lookup"><span data-stu-id="1a98a-148">-v version</span></span>     | <span data-ttu-id="1a98a-149">表示ツールのバージョンと終了。</span><span class="sxs-lookup"><span data-stu-id="1a98a-149">Display tool version and exit.</span></span>                                                                                                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="1a98a-150">-l ログ フィルター</span><span class="sxs-lookup"><span data-stu-id="1a98a-150">-l log-filter</span></span>  | <span data-ttu-id="1a98a-151">ログ ファイルのフィルター レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-151">Set a filter level for the log file.</span></span> <span data-ttu-id="1a98a-152">ログ メッセージには、DEBUG (最下位)、INFO、WARNING、ERROR (最も高い) の 4 つのレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-152">Log messages have 4 possible levels: DEBUG (lowest), INFO, WARNING and ERROR (highest).</span></span> <span data-ttu-id="1a98a-153">ログ フィルター レベルを設定すると、ログ メッセージは同じレベル以上のメッセージにのみフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-153">Setting a log filter level filters log messages to only message with the same level or higher.</span></span> <span data-ttu-id="1a98a-154">たとえば、フィルター レベルが WARNING に設定されている場合、警告メッセージとエラー メッセージだけがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="1a98a-154">For example, if the filter level is set to WARNING, only WARNING and ERROR messages will be logged.</span></span> <span data-ttu-id="1a98a-155">既定では、このオプションは OFF に設定され、ログが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1a98a-155">By default, this option is set to OFF, which disables logging.</span></span> |
| <span data-ttu-id="1a98a-156">-g get-version</span><span class="sxs-lookup"><span data-stu-id="1a98a-156">-g get-version</span></span> | <span data-ttu-id="1a98a-157">指定した場合、ツールは、ツールと同じフォルダーに格納されている構成ファイルに一致する接続されているペンの FW バージョンのみを取得します。</span><span class="sxs-lookup"><span data-stu-id="1a98a-157">If specified, the tool will only get the FW version of the connected pen that matches the configuration file that is stored in the same folder as the tool.</span></span>                                                                                                                                                                                                                                    
