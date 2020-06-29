---
title: Surface Hub 2S のペンファームウェアの更新
description: このページでは、Surface Hub 2 ペンのファームウェアを更新する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/26/2020
ms.localizationpriority: Medium
ms.openlocfilehash: c0ad8f275d2476e42c9a5bd3f1130fbca85a5599
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835382"
---
# <span data-ttu-id="7c5e0-104">Surface Hub 2S のペンファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="7c5e0-104">Update pen firmware on Surface Hub 2S</span></span>

<span data-ttu-id="7c5e0-105">Surface Hub 2pen のファームウェアは、一般法人向け Windows Update から更新するか、または別の PC にファームウェア更新プログラムをダウンロードして更新できます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-105">You can update firmware on Surface Hub 2 pen from Windows Update for Business or by downloading the firmware update to a separate PC.</span></span> <span data-ttu-id="7c5e0-106">更新されたファームウェアは、2020年2月26日以降の Windows Update から利用できます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-106">Updated firmware is available from Windows Update beginning February 26, 2020.</span></span> 

## <span data-ttu-id="7c5e0-107">Windows Update for Business を使用してペンのファームウェアを更新する</span><span class="sxs-lookup"><span data-stu-id="7c5e0-107">Update pen firmware using Windows Update for Business</span></span>

<span data-ttu-id="7c5e0-108">このセクションでは、Windows Update の自動メンテナンスサイクルを通じて pen ファームウェアを更新する方法について説明します。既定では、午前3時に実行されるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-108">This section describes how to update pen firmware via the automated maintenance cycles for Windows Update, configured by default to occur nightly at 3 a.m.</span></span> <span data-ttu-id="7c5e0-109">Surface Hub 2 ペンに更新プログラムを適用する前に、2つのメンテナンスサイクルを完了するように計画する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-109">You will need to plan for two maintenance cycles to complete before applying the update to the Surface Hub 2 pen.</span></span> <span data-ttu-id="7c5e0-110">または、他の更新プログラムと同様に、Windows Server Update Services (WSUS) を使ってペンファームウェアを適用できます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-110">Alternately, like any other update, you can use Windows Server Update Services (WSUS) to apply the pen firmware.</span></span> <span data-ttu-id="7c5e0-111">詳細については、「 [Surface Hub での Windows 更新プログラムの管理](manage-windows-updates-for-surface-hub.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-111">For more information, see [Managing Windows updates on Surface Hub](manage-windows-updates-for-surface-hub.md).</span></span>

1. <span data-ttu-id="7c5e0-112">Surface Hub 2 ペンが Surface Hub 2S とペアリングされていることを確認します。**トップ**ボタンを長押しすると、白いインジケーター LED が点滅します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-112">Ensure the Surface Hub 2 pen is paired to Surface Hub 2S: Press and hold the **top** button until the white indicator LED light begins to blink.</span></span> <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. <span data-ttu-id="7c5e0-114">Surface Hub で、管理者としてログインし、[**設定**] を開いて、新しい Bluetooth デバイスをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-114">On Surface Hub, login as an Admin, open **Settings**, and then scan for new Bluetooth devices.</span></span>
3. <span data-ttu-id="7c5e0-115">ペアリングプロセスを完了するには、ペンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-115">Select the pen to complete the pairing process.</span></span>
4. <span data-ttu-id="7c5e0-116">ペンの**上部**のボタンを押して、更新プログラムを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-116">Press the **top** button on the pen to apply the update.</span></span> <span data-ttu-id="7c5e0-117">完了までに最大2時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-117">It may take up to two hours to complete.</span></span>

## <span data-ttu-id="7c5e0-118">別の PC にダウンロードして、ペンのファームウェアを更新する</span><span class="sxs-lookup"><span data-stu-id="7c5e0-118">Update pen firmware by downloading to separate PC</span></span>

<span data-ttu-id="7c5e0-119">Surface Hub 2 ペンのファームウェアは、Windows 10 を実行している別の PC から更新できます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-119">You can update the firmware on Surface Hub 2 pen from a separate PC running Windows 10.</span></span> <span data-ttu-id="7c5e0-120">この方法では、pen ファームウェアが正常に最新バージョンに更新されたことを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-120">This method also enables you to verify that the pen firmware has successfully updated to the latest version.</span></span>

1. <span data-ttu-id="7c5e0-121">Surface Hub 2 ペンを Bluetooth 対応 PC にペアリングします。白いインジケータ LED が点滅するまで、**上部**のボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-121">Pair the Surface Hub 2 pen to your Bluetooth-capable PC: Press and hold the **top** button until the white indicator LED light begins to blink.</span></span> <br>
![Surface Hub 2 ペン](images/sh2-pen-1.png) <br>
2. <span data-ttu-id="7c5e0-123">PC で、新しい Bluetooth デバイスをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-123">On the PC, scan for new Bluetooth devices.</span></span>
3. <span data-ttu-id="7c5e0-124">ペアリングプロセスを完了するには、ペンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-124">Select the pen to complete the pairing process.</span></span>
4. <span data-ttu-id="7c5e0-125">新しい更新プログラムを開始する前に、他のすべての Surface Hub 2s pens を切断します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-125">Disconnect all other Surface Hub 2s pens before starting a new update.</span></span>
3. <span data-ttu-id="7c5e0-126">[Surface Hub 2 Pen ファームウェアアップデートツール](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip)を PC にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-126">Download the [Surface Hub 2 Pen Firmware Update Tool](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip) to your PC.</span></span>
4. <span data-ttu-id="7c5e0-127">**PenCfu.exe を実行します。**</span><span class="sxs-lookup"><span data-stu-id="7c5e0-127">Run **PenCfu.exe.**</span></span> <span data-ttu-id="7c5e0-128">インストールの進行状況がツールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-128">The install progress is displayed in the tool.</span></span> <span data-ttu-id="7c5e0-129">更新が完了するまで数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-129">It may take several minutes to finish updating.</span></span> 


## <span data-ttu-id="7c5e0-130">Surface Hub のファームウェアバージョン2ペンを確認する</span><span class="sxs-lookup"><span data-stu-id="7c5e0-130">Check firmware version of Surface Hub 2 pen</span></span>

1. <span data-ttu-id="7c5e0-131">**get_version.bat**を実行して、ペンの**上部**のボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-131">Run **get_version.bat** and press the **top** button on the pen.</span></span>
2. <span data-ttu-id="7c5e0-132">このツールによって、ファームウェアバージョンのペンが報告されます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-132">The tool will report the firmware version of the pen.</span></span> <span data-ttu-id="7c5e0-133">例:</span><span class="sxs-lookup"><span data-stu-id="7c5e0-133">Example:</span></span>
    - <span data-ttu-id="7c5e0-134">古いファームウェアは468.2727.368</span><span class="sxs-lookup"><span data-stu-id="7c5e0-134">Old firmware is 468.2727.368</span></span>
    - <span data-ttu-id="7c5e0-135">新しいファームウェアは468.2863.369</span><span class="sxs-lookup"><span data-stu-id="7c5e0-135">New firmware is 468.2863.369</span></span>

## <span data-ttu-id="7c5e0-136">コマンドラインオプション</span><span class="sxs-lookup"><span data-stu-id="7c5e0-136">Command line options</span></span>

<span data-ttu-id="7c5e0-137">Surface Hub 2 Pen ファームウェア更新ツール (PenCfu.exe) は、コマンドラインから実行できます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-137">You can run Surface Hub 2 Pen Firmware Update Tool (PenCfu.exe) from the command line.</span></span>

1. <span data-ttu-id="7c5e0-138">ペンを PC にペアリングし、ペンの**上部**のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-138">Pair the pen to your PC and click the **top** button on the pen.</span></span>
2. <span data-ttu-id="7c5e0-139">[ **PenCfu.exe** ] をダブルクリックして、ファームウェアの更新を開始します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-139">Double click **PenCfu.exe** to initiate the firmware update.</span></span> <span data-ttu-id="7c5e0-140">構成ファイルとファームウェアイメージファイルは、ツールと同じフォルダーに保存されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-140">Note that the configuration file and the firmware image files must be stored in the same folder as the tool.</span></span>
3. <span data-ttu-id="7c5e0-141">その他のオプションについては、 **PenCfu.exe**を実行して、次の表に示すように、使用できるパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-141">For additional options, run **PenCfu.exe -h** to display the available parameters, as listed in the following table.</span></span>  
    - <span data-ttu-id="7c5e0-142">例: PenCfu.exe-h</span><span class="sxs-lookup"><span data-stu-id="7c5e0-142">Example: PenCfu.exe -h</span></span>
4. <span data-ttu-id="7c5e0-143">ツールを安全に終了するには、 **Ctrl キーを押しながら C キーを押し**ます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-143">Enter **Ctrl+C** to safely shut down the tool.</span></span>

 

| **<span data-ttu-id="7c5e0-144">コマンド</span><span class="sxs-lookup"><span data-stu-id="7c5e0-144">Command</span></span>**    | **<span data-ttu-id="7c5e0-145">説明</span><span class="sxs-lookup"><span data-stu-id="7c5e0-145">Description</span></span>**                                                                                                                                                                                                                                                                                                                                                                                |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7c5e0-146">-h ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7c5e0-146">-h help</span></span>        | <span data-ttu-id="7c5e0-147">表示ツールのコマンドラインインターフェイスのヘルプと終了。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-147">Display tool command line interface help and exit.</span></span>                                                                                                                                                                                                                                                                                                                                             |
| <span data-ttu-id="7c5e0-148">-v バージョン</span><span class="sxs-lookup"><span data-stu-id="7c5e0-148">-v version</span></span>     | <span data-ttu-id="7c5e0-149">ツールのバージョンを表示して終了します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-149">Display tool version and exit.</span></span>                                                                                                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="7c5e0-150">-l ログ-フィルター</span><span class="sxs-lookup"><span data-stu-id="7c5e0-150">-l log-filter</span></span>  | <span data-ttu-id="7c5e0-151">ログファイルのフィルターレベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-151">Set a filter level for the log file.</span></span> <span data-ttu-id="7c5e0-152">ログメッセージには、デバッグ (最低)、情報、警告、エラー (最高) の4つのレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-152">Log messages have 4 possible levels: DEBUG (lowest), INFO, WARNING and ERROR (highest).</span></span> <span data-ttu-id="7c5e0-153">ログフィルターレベルを設定すると、同じレベル以上のメッセージのみにログメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-153">Setting a log filter level filters log messages to only message with the same level or higher.</span></span> <span data-ttu-id="7c5e0-154">たとえば、フィルターレベルが [警告] に設定されている場合、警告メッセージとエラーメッセージのみが記録されます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-154">For example, if the filter level is set to WARNING, only WARNING and ERROR messages will be logged.</span></span> <span data-ttu-id="7c5e0-155">既定では、このオプションは [オフ] に設定されています。これにより、ログは無効になります。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-155">By default, this option is set to OFF, which disables logging.</span></span> |
| <span data-ttu-id="7c5e0-156">-g: バージョン</span><span class="sxs-lookup"><span data-stu-id="7c5e0-156">-g get-version</span></span> | <span data-ttu-id="7c5e0-157">指定すると、ツールと同じフォルダーに保存されている構成ファイルと一致する、接続されているペンの FW バージョンのみが取得されます。</span><span class="sxs-lookup"><span data-stu-id="7c5e0-157">If specified, the tool will only get the FW version of the connected pen that matches the configuration file that is stored in the same folder as the tool.</span></span>                                                                                                                                                                                                                                    