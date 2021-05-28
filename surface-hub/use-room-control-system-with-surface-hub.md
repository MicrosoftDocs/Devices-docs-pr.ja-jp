---
title: ルーム コントロール システムを使う (Surface Hub)
description: Microsoft Surface Hub では、ルーム コントロール システムを使用できます。
ms.assetid: DC365002-6B35-45C5-A2B8-3E1EB0CB8B50
ms.reviewer: ''
manager: laurawi
keywords: ルーム コントロール システム, room control system, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0e3b1706e58edb6e37156eda8d06fb0faefa4c91
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834846"
---
# <span data-ttu-id="13b7f-104">ルーム コントロール システムを使う (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="13b7f-104">Using a room control system (Surface Hub)</span></span>


<span data-ttu-id="13b7f-105">Microsoft Surface Hub では、ルーム コントロール システムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-105">Room control systems can be used with your Microsoft Surface Hub.</span></span>

<span data-ttu-id="13b7f-106">Surface Hub でルーム コントロール システムを使用するには、ルーム コントロール ハードウェアを Surface Hub に接続します。通常、接続には Surface Hub の下部にある RJ11 シリアル ポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-106">Using a room control system with your Surface Hub involves connecting room control hardware to the Surface Hub, usually through the RJ11 serial port on the bottom of the Surface Hub.</span></span>

## <a name="terminal-settings"></a><span data-ttu-id="13b7f-107">端末の設定</span><span class="sxs-lookup"><span data-stu-id="13b7f-107">Terminal settings</span></span>

<span data-ttu-id="13b7f-108">ルーム コントロール システムのコントロール パネルに接続するために、Surface Hub で端末の設定を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="13b7f-108">To connect to a room control system control panel, you don't need to configure any terminal settings on the Surface Hub.</span></span> <span data-ttu-id="13b7f-109">PC やノート PC を Surface Hub に接続して Surface Hub からシリアル コマンドを送信する場合は、Tera Term や PuTTY などの端末エミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-109">If you want to connect a PC or laptop to your Surface Hub and send serial commands from the Surface Hub, you can use a terminal emulator program like Tera Term or PuTTY.</span></span> 

| <span data-ttu-id="13b7f-110">設定</span><span class="sxs-lookup"><span data-stu-id="13b7f-110">Setting</span></span> | <span data-ttu-id="13b7f-111">値</span><span class="sxs-lookup"><span data-stu-id="13b7f-111">Value</span></span> |
| --- | --- |
| <span data-ttu-id="13b7f-112">ボー レート</span><span class="sxs-lookup"><span data-stu-id="13b7f-112">Baud rate</span></span> | <span data-ttu-id="13b7f-113">115200</span><span class="sxs-lookup"><span data-stu-id="13b7f-113">115200</span></span> |
| <span data-ttu-id="13b7f-114">データ ビット</span><span class="sxs-lookup"><span data-stu-id="13b7f-114">Data bits</span></span> | <span data-ttu-id="13b7f-115">個</span><span class="sxs-lookup"><span data-stu-id="13b7f-115">8</span></span> | 
| <span data-ttu-id="13b7f-116">ストップ ビット</span><span class="sxs-lookup"><span data-stu-id="13b7f-116">Stop bits</span></span> | <span data-ttu-id="13b7f-117">件</span><span class="sxs-lookup"><span data-stu-id="13b7f-117">1</span></span> |
| <span data-ttu-id="13b7f-118">パリティ</span><span class="sxs-lookup"><span data-stu-id="13b7f-118">Parity</span></span> | <span data-ttu-id="13b7f-119">なし</span><span class="sxs-lookup"><span data-stu-id="13b7f-119">none</span></span> |
| <span data-ttu-id="13b7f-120">フロー制御</span><span class="sxs-lookup"><span data-stu-id="13b7f-120">Flow control</span></span> | <span data-ttu-id="13b7f-121">なし</span><span class="sxs-lookup"><span data-stu-id="13b7f-121">none</span></span> |
| <span data-ttu-id="13b7f-122">ライン フィード</span><span class="sxs-lookup"><span data-stu-id="13b7f-122">Line feed</span></span> | <span data-ttu-id="13b7f-123">すべてのキャリッジ リターン</span><span class="sxs-lookup"><span data-stu-id="13b7f-123">every carriage return</span></span> |
 

## <a name="wiring-diagram"></a><span data-ttu-id="13b7f-124">配線図</span><span class="sxs-lookup"><span data-stu-id="13b7f-124">Wiring diagram</span></span>

<span data-ttu-id="13b7f-125">Surface Hub のシリアル ポートをルーム コントロール システムに接続する際は、標準的な RJ-11 (6P6C) コネクタを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-125">You can use a standard RJ-11 (6P6C) connector to connect the Surface Hub serial port to a room control system.</span></span> <span data-ttu-id="13b7f-126">これは、推奨されている接続方法です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-126">This is the recommended method.</span></span> <span data-ttu-id="13b7f-127">RJ-11 4 コンダクター ケーブルを使用することもできますが、この方法は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="13b7f-127">You can also use an RJ-11 4-conductor cable, but we do not recommend this method.</span></span>

<span data-ttu-id="13b7f-128">次の図では、DB9 ケーブルに対する RJ-11 (6P6C) に使用する適切なピンアウトを示します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-128">This diagram shows the correct pinout used for an RJ-11 (6P6C) to DB9 cable.</span></span>

![配線図を示す画像。](images/room-control-wiring-diagram.png)

## <a name="command-sets"></a><span data-ttu-id="13b7f-130">コマンド セット</span><span class="sxs-lookup"><span data-stu-id="13b7f-130">Command sets</span></span>

<span data-ttu-id="13b7f-131">ルーム コントロール システムでは、コマンドに関して一般的な会議室シナリオを使用します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-131">Room control systems use common meeting-room scenarios for commands.</span></span> <span data-ttu-id="13b7f-132">コマンドはルーム コントロール システムで生成され、Surface Hub とのシリアル接続を介して伝達されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-132">Commands originate from the room control system, and are communicated over a serial connection to a Surface Hub.</span></span> <span data-ttu-id="13b7f-133">コマンドは ASCII ベースで、Surface Hub は状態変化の発生を認識します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-133">Commands are ASCII based, and the Surface Hub will acknowledge when state changes occur.</span></span>

<span data-ttu-id="13b7f-134">以下のコマンド修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-134">The following command modifiers are available.</span></span> <span data-ttu-id="13b7f-135">コマンドは、改行文字 (\n) に到達すると終了します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-135">Commands terminate with a new line character (\n).</span></span> <span data-ttu-id="13b7f-136">管理ポート コマンドによって直接トリガーされていない状態変化では、応答があらゆる時点で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13b7f-136">Responses can come at any time in response to state changes not triggered directly by a management port command.</span></span>

| <span data-ttu-id="13b7f-137">修飾子</span><span class="sxs-lookup"><span data-stu-id="13b7f-137">Modifier</span></span> | <span data-ttu-id="13b7f-138">結果</span><span class="sxs-lookup"><span data-stu-id="13b7f-138">Result</span></span> |
| --- | --- |
| + | <span data-ttu-id="13b7f-139">値を増やす</span><span class="sxs-lookup"><span data-stu-id="13b7f-139">Increment a value</span></span> |
| - | <span data-ttu-id="13b7f-140">値を減らす</span><span class="sxs-lookup"><span data-stu-id="13b7f-140">Decrease a value</span></span> |
| = | <span data-ttu-id="13b7f-141">個別の値を設定する</span><span class="sxs-lookup"><span data-stu-id="13b7f-141">Set a discrete value</span></span> |
| <span data-ttu-id="13b7f-142">?</span><span class="sxs-lookup"><span data-stu-id="13b7f-142">?</span></span> | <span data-ttu-id="13b7f-143">現在の値を照会する</span><span class="sxs-lookup"><span data-stu-id="13b7f-143">Queries for a current value</span></span> |
 

## <a name="power"></a><span data-ttu-id="13b7f-144">電源</span><span class="sxs-lookup"><span data-stu-id="13b7f-144">Power</span></span>

<span data-ttu-id="13b7f-145">Surface Hub の電力は、以下のいずれかの状態になります。</span><span class="sxs-lookup"><span data-stu-id="13b7f-145">Surface Hub can be in one of these power states.</span></span>

| <span data-ttu-id="13b7f-146">状態</span><span class="sxs-lookup"><span data-stu-id="13b7f-146">State</span></span> | <span data-ttu-id="13b7f-147">Energy Star の状態</span><span class="sxs-lookup"><span data-stu-id="13b7f-147">Energy Star state</span></span>| <span data-ttu-id="13b7f-148">説明</span><span class="sxs-lookup"><span data-stu-id="13b7f-148">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-149">0</span><span class="sxs-lookup"><span data-stu-id="13b7f-149">0</span></span> | <span data-ttu-id="13b7f-150">S5</span><span class="sxs-lookup"><span data-stu-id="13b7f-150">S5</span></span> | <span data-ttu-id="13b7f-151">オフ</span><span class="sxs-lookup"><span data-stu-id="13b7f-151">Off</span></span> |
| <span data-ttu-id="13b7f-152">件</span><span class="sxs-lookup"><span data-stu-id="13b7f-152">1</span></span> | - | <span data-ttu-id="13b7f-153">電源投入 (不確定状態)</span><span class="sxs-lookup"><span data-stu-id="13b7f-153">Power up (indeterminate)</span></span> |
| <span data-ttu-id="13b7f-154">両面</span><span class="sxs-lookup"><span data-stu-id="13b7f-154">2</span></span> | <span data-ttu-id="13b7f-155">S3</span><span class="sxs-lookup"><span data-stu-id="13b7f-155">S3</span></span> | <span data-ttu-id="13b7f-156">スリープ</span><span class="sxs-lookup"><span data-stu-id="13b7f-156">Sleep</span></span> |
| <span data-ttu-id="13b7f-157">個</span><span class="sxs-lookup"><span data-stu-id="13b7f-157">5</span></span> | <span data-ttu-id="13b7f-158">S0</span><span class="sxs-lookup"><span data-stu-id="13b7f-158">S0</span></span> | <span data-ttu-id="13b7f-159">準備完了</span><span class="sxs-lookup"><span data-stu-id="13b7f-159">Ready</span></span> |


<span data-ttu-id="13b7f-160">代替 PC モードでは、電源状態は準備完了とオフのみであり、ディスプレイのみを変更します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-160">In Replacement PC mode, the power states are only Ready and Off and only change the display.</span></span> <span data-ttu-id="13b7f-161">管理ポートを使って代替 PC の電源を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="13b7f-161">The management port can't be used to power on the replacement PC.</span></span> 

| <span data-ttu-id="13b7f-162">状態</span><span class="sxs-lookup"><span data-stu-id="13b7f-162">State</span></span> | <span data-ttu-id="13b7f-163">Energy Star の状態</span><span class="sxs-lookup"><span data-stu-id="13b7f-163">Energy Star state</span></span>| <span data-ttu-id="13b7f-164">説明</span><span class="sxs-lookup"><span data-stu-id="13b7f-164">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-165">0</span><span class="sxs-lookup"><span data-stu-id="13b7f-165">0</span></span> | <span data-ttu-id="13b7f-166">S5</span><span class="sxs-lookup"><span data-stu-id="13b7f-166">S5</span></span> | <span data-ttu-id="13b7f-167">オフ</span><span class="sxs-lookup"><span data-stu-id="13b7f-167">Off</span></span> |
| <span data-ttu-id="13b7f-168">個</span><span class="sxs-lookup"><span data-stu-id="13b7f-168">5</span></span> | <span data-ttu-id="13b7f-169">S0</span><span class="sxs-lookup"><span data-stu-id="13b7f-169">S0</span></span> | <span data-ttu-id="13b7f-170">準備完了</span><span class="sxs-lookup"><span data-stu-id="13b7f-170">Ready</span></span> |

<span data-ttu-id="13b7f-171">コントロール デバイスの場合、5/準備完了以外はすべてオフと考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="13b7f-171">For a control device, anything other than 5 / Ready should be considered off.</span></span> <span data-ttu-id="13b7f-172">各 PowerOn コマンドは、2つの状態の変更と応答を生成します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-172">Each PowerOn command results in two state changes and responses.</span></span> 

| <span data-ttu-id="13b7f-173">コマンド</span><span class="sxs-lookup"><span data-stu-id="13b7f-173">Command</span></span> | <span data-ttu-id="13b7f-174">状態の変化</span><span class="sxs-lookup"><span data-stu-id="13b7f-174">State change</span></span>| <span data-ttu-id="13b7f-175">応答</span><span class="sxs-lookup"><span data-stu-id="13b7f-175">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-176">PowerOn</span><span class="sxs-lookup"><span data-stu-id="13b7f-176">PowerOn</span></span> | <span data-ttu-id="13b7f-177">デバイスの電源が入ります (ディスプレイ + PC)。</span><span class="sxs-lookup"><span data-stu-id="13b7f-177">Device turns on (display + PC).</span></span></br></br><span data-ttu-id="13b7f-178">PC サービスによって、PC の準備ができたことが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-178">PC service notifies SMC that the PC is ready.</span></span> |  <span data-ttu-id="13b7f-179">Power=0</span><span class="sxs-lookup"><span data-stu-id="13b7f-179">Power=0</span></span></br></br><span data-ttu-id="13b7f-180">Power=5</span><span class="sxs-lookup"><span data-stu-id="13b7f-180">Power=5</span></span> |
| <span data-ttu-id="13b7f-181">PowerOff</span><span class="sxs-lookup"><span data-stu-id="13b7f-181">PowerOff</span></span> | <span data-ttu-id="13b7f-182">デバイスが環境状態に移行します (PC オン、ディスプレイ暗転)。</span><span class="sxs-lookup"><span data-stu-id="13b7f-182">Device transitions to ambient state (PC on, display dim).</span></span> |  <span data-ttu-id="13b7f-183">Power=0</span><span class="sxs-lookup"><span data-stu-id="13b7f-183">Power=0</span></span> |
| <span data-ttu-id="13b7f-184">Power?</span><span class="sxs-lookup"><span data-stu-id="13b7f-184">Power?</span></span> |  <span data-ttu-id="13b7f-185">SMC は最後にわかっている電源状態を報告します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-185">SMC reports the last-known power state.</span></span> |  <span data-ttu-id="13b7f-186">Power=<#></span><span class="sxs-lookup"><span data-stu-id="13b7f-186">Power=<#></span></span> |



## <a name="brightness"></a><span data-ttu-id="13b7f-187">Brightness</span><span class="sxs-lookup"><span data-stu-id="13b7f-187">Brightness</span></span>

<span data-ttu-id="13b7f-188">現在の明るさレベルの範囲は、0 ~ 100 です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-188">The current brightness level is a range from 0 to 100.</span></span>

<span data-ttu-id="13b7f-189">明るさレベルの変更は、ルーム コントロール システムなどのシステムによって送信できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-189">Changes to brightness levels can be sent by a room control system, or other system.</span></span>

| <span data-ttu-id="13b7f-190">コマンド</span><span class="sxs-lookup"><span data-stu-id="13b7f-190">Command</span></span> | <span data-ttu-id="13b7f-191">状態の変化</span><span class="sxs-lookup"><span data-stu-id="13b7f-191">State change</span></span> |<span data-ttu-id="13b7f-192">応答</span><span class="sxs-lookup"><span data-stu-id="13b7f-192">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-193">Brightness+</span><span class="sxs-lookup"><span data-stu-id="13b7f-193">Brightness+</span></span> | <span data-ttu-id="13b7f-194">システム管理コントローラー (SMC) が、明るさを上げるコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-194">System management controller (SMC) sends the brightness up command.</span></span></br></br><span data-ttu-id="13b7f-195">ルーム コントロール システムの PC サービスによって、新しい明るさレベルが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-195">PC service on the room control system notifies SMC of new brightness level.</span></span> |  <span data-ttu-id="13b7f-196">Brightness = 51</span><span class="sxs-lookup"><span data-stu-id="13b7f-196">Brightness = 51</span></span> |
| <span data-ttu-id="13b7f-197">Brightness-</span><span class="sxs-lookup"><span data-stu-id="13b7f-197">Brightness-</span></span> |  <span data-ttu-id="13b7f-198">SMC が、明るさを下げるコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-198">SMC sends the brightness down command.</span></span></br></br><span data-ttu-id="13b7f-199">PC サービスによって、新しい明るさレベルが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-199">PC service notifies SMC of new brightness level.</span></span> | <span data-ttu-id="13b7f-200">Brightness = 50</span><span class="sxs-lookup"><span data-stu-id="13b7f-200">Brightness = 50</span></span> |

## <a name="volume"></a><span data-ttu-id="13b7f-201">Volume</span><span class="sxs-lookup"><span data-stu-id="13b7f-201">Volume</span></span>

<span data-ttu-id="13b7f-202">現在の音量レベルの範囲は、0 ~ 100 です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-202">The current volume level is a range from 0 to 100.</span></span>

<span data-ttu-id="13b7f-203">音量レベルの変更は、ルーム コントロール システムなどのシステムによって送信できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-203">Changes to volume levels can be sent by a room control system, or other system.</span></span>

>[!NOTE]
><span data-ttu-id="13b7f-204">Volume コマンドでは、埋め込みモードまたは代替 PC モードの音量のみが制御され、[ゲストのソース](connect-and-display-with-surface-hub.md)は制御されません。</span><span class="sxs-lookup"><span data-stu-id="13b7f-204">The Volume command will only control the volume for embedded or Replacement PC mode, not from [Guest sources](connect-and-display-with-surface-hub.md).</span></span>

| <span data-ttu-id="13b7f-205">コマンド</span><span class="sxs-lookup"><span data-stu-id="13b7f-205">Command</span></span> | <span data-ttu-id="13b7f-206">状態の変化</span><span class="sxs-lookup"><span data-stu-id="13b7f-206">State change</span></span> | <span data-ttu-id="13b7f-207">応答</span><span class="sxs-lookup"><span data-stu-id="13b7f-207">Response</span></span></br><span data-ttu-id="13b7f-208">([代替 PC モード](connect-and-display-with-surface-hub.md#replacement-pc-mode) で有効)</span><span class="sxs-lookup"><span data-stu-id="13b7f-208">(On in [Replacement PC mode](connect-and-display-with-surface-hub.md#replacement-pc-mode))</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-209">Volume+</span><span class="sxs-lookup"><span data-stu-id="13b7f-209">Volume+</span></span> |  <span data-ttu-id="13b7f-210">SMC が音量を上げるコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-210">SMC sends the volume up command.</span></span></br></br><span data-ttu-id="13b7f-211">PC サービスによって、新しい音量レベルが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-211">PC service notifies SMC of new volume level.</span></span> |  <span data-ttu-id="13b7f-212">Volume = 51</span><span class="sxs-lookup"><span data-stu-id="13b7f-212">Volume = 51</span></span> |
| <span data-ttu-id="13b7f-213">Volume-</span><span class="sxs-lookup"><span data-stu-id="13b7f-213">Volume-</span></span> |  <span data-ttu-id="13b7f-214">SMC が音量を下げるコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-214">SMC sends the volume down command.</span></span></br></br><span data-ttu-id="13b7f-215">PC サービスによって、新しい音量レベルが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-215">PC service notifies SMC of new volume level.</span></span> |  <span data-ttu-id="13b7f-216">Volume = 50</span><span class="sxs-lookup"><span data-stu-id="13b7f-216">Volume = 50</span></span> |


 

## <a name="mute-for-audio"></a><span data-ttu-id="13b7f-217">オーディオのミュート</span><span class="sxs-lookup"><span data-stu-id="13b7f-217">Mute for audio</span></span>

<span data-ttu-id="13b7f-218">オーディオをミュートすることができます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-218">Audio can be muted.</span></span>

| <span data-ttu-id="13b7f-219">コマンド</span><span class="sxs-lookup"><span data-stu-id="13b7f-219">Command</span></span> | <span data-ttu-id="13b7f-220">状態の変化</span><span class="sxs-lookup"><span data-stu-id="13b7f-220">State change</span></span> | <span data-ttu-id="13b7f-221">応答</span><span class="sxs-lookup"><span data-stu-id="13b7f-221">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-222">AudioMute+</span><span class="sxs-lookup"><span data-stu-id="13b7f-222">AudioMute+</span></span> |  <span data-ttu-id="13b7f-223">SMC がオーディオのミュート コマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-223">SMC sends the audio mute command.</span></span></br></br><span data-ttu-id="13b7f-224">PC サービスによって、オーディオがミュートされていることが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-224">PC service notifies SMC that audio is muted.</span></span> |  <span data-ttu-id="13b7f-225">なし</span><span class="sxs-lookup"><span data-stu-id="13b7f-225">none</span></span> |


 

## <a name="video-source"></a><span data-ttu-id="13b7f-226">ビデオ ソース</span><span class="sxs-lookup"><span data-stu-id="13b7f-226">Video source</span></span>

<span data-ttu-id="13b7f-227">複数の表示ソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-227">Several display sources can be used.</span></span>

| <span data-ttu-id="13b7f-228">状態</span><span class="sxs-lookup"><span data-stu-id="13b7f-228">State</span></span> | <span data-ttu-id="13b7f-229">説明</span><span class="sxs-lookup"><span data-stu-id="13b7f-229">Description</span></span> | 
| --- | --- |
| <span data-ttu-id="13b7f-230">0</span><span class="sxs-lookup"><span data-stu-id="13b7f-230">0</span></span> |  <span data-ttu-id="13b7f-231">オンボード PC</span><span class="sxs-lookup"><span data-stu-id="13b7f-231">Onboard PC</span></span> |
| <span data-ttu-id="13b7f-232">件</span><span class="sxs-lookup"><span data-stu-id="13b7f-232">1</span></span> |  <span data-ttu-id="13b7f-233">DisplayPort</span><span class="sxs-lookup"><span data-stu-id="13b7f-233">DisplayPort</span></span> |
| <span data-ttu-id="13b7f-234">両面</span><span class="sxs-lookup"><span data-stu-id="13b7f-234">2</span></span> |  <span data-ttu-id="13b7f-235">HDMI</span><span class="sxs-lookup"><span data-stu-id="13b7f-235">HDMI</span></span> |
| <span data-ttu-id="13b7f-236">-</span><span class="sxs-lookup"><span data-stu-id="13b7f-236">3</span></span> |  <span data-ttu-id="13b7f-237">VGA</span><span class="sxs-lookup"><span data-stu-id="13b7f-237">VGA</span></span> |


 

<span data-ttu-id="13b7f-238">表示ソースへの変更は、ルーム コントロール システムなどのシステムによって送信できます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-238">Changes to display source can be sent by a room control system, or other system.</span></span>

| <span data-ttu-id="13b7f-239">コマンド</span><span class="sxs-lookup"><span data-stu-id="13b7f-239">Command</span></span> | <span data-ttu-id="13b7f-240">状態の変化</span><span class="sxs-lookup"><span data-stu-id="13b7f-240">State change</span></span> | <span data-ttu-id="13b7f-241">応答</span><span class="sxs-lookup"><span data-stu-id="13b7f-241">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="13b7f-242">Source=#</span><span class="sxs-lookup"><span data-stu-id="13b7f-242">Source=#</span></span> |  <span data-ttu-id="13b7f-243">SMC によって目的のソースに変更されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-243">SMC changes to the desired source.</span></span></br></br><span data-ttu-id="13b7f-244">PC サービスによって、表示ソースが切り替えられたことが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-244">PC service notifies SMC that the display source has switched.</span></span> |  <span data-ttu-id="13b7f-245">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="13b7f-245">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="13b7f-246">Source+</span><span class="sxs-lookup"><span data-stu-id="13b7f-246">Source+</span></span> |  <span data-ttu-id="13b7f-247">SMC によって次のアクティブな入力ソースに移行されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-247">SMC cycles to the next active input source.</span></span></br></br><span data-ttu-id="13b7f-248">PC サービスによって、現在の入力ソースが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-248">PC service notifies SMC of the current input source.</span></span> |  <span data-ttu-id="13b7f-249">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="13b7f-249">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="13b7f-250">Source-</span><span class="sxs-lookup"><span data-stu-id="13b7f-250">Source-</span></span> | <span data-ttu-id="13b7f-251">SMC によって前のアクティブな入力ソースに移行されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-251">SMC cycles to the previous active input source.</span></span></br></br><span data-ttu-id="13b7f-252">PC サービスによって、現在の入力ソースが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-252">PC service notifies SMC of the current input source.</span></span> |  <span data-ttu-id="13b7f-253">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="13b7f-253">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="13b7f-254">Source?</span><span class="sxs-lookup"><span data-stu-id="13b7f-254">Source?</span></span> |  <span data-ttu-id="13b7f-255">SMC が、PC サービスでアクティブな入力ソースを照会します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-255">SMC queries PC service for the active input source.</span></span></br></br><span data-ttu-id="13b7f-256">PC サービスによって、現在の入力ソースが SMC に通知されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-256">PC service notifies SMC of the current in;put source.</span></span> | <span data-ttu-id="13b7f-257">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="13b7f-257">Source=&lt;#&gt;</span></span> |

## <a name="errors"></a><span data-ttu-id="13b7f-258">Errors</span><span class="sxs-lookup"><span data-stu-id="13b7f-258">Errors</span></span>

<span data-ttu-id="13b7f-259">エラーは、次の表の形式に従って返されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-259">Errors are returned following the format in this table.</span></span>

| <span data-ttu-id="13b7f-260">エラー</span><span class="sxs-lookup"><span data-stu-id="13b7f-260">Error</span></span> | <span data-ttu-id="13b7f-261">注意</span><span class="sxs-lookup"><span data-stu-id="13b7f-261">Notes</span></span> |
| --- | --- |
| <span data-ttu-id="13b7f-262">エラー: 不明なコマンド '&lt;入力値&gt;' です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-262">Error: Unknown command '&lt;input&gt;'.</span></span> |  <span data-ttu-id="13b7f-263">命令に不明な初期コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="13b7f-263">The instruction contains an unknown initial command.</span></span> <span data-ttu-id="13b7f-264">たとえば、&quot;VOL+&quot; では無効になり、&quot;エラー: 不明なコマンド 'VOL' です&quot; と表示されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-264">For example, &quot;VOL+&quot; would be invalid and return &quot; Error: Unknown command 'VOL'&quot;.</span></span> |
| <span data-ttu-id="13b7f-265">エラー: 不明な演算子 '&lt;入力値&gt;' です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-265">Error: Unknown operator '&lt;input&gt;'.</span></span> |  <span data-ttu-id="13b7f-266">命令に不明な演算子が含まれています</span><span class="sxs-lookup"><span data-stu-id="13b7f-266">The instruction contains an unknown operator.</span></span> <span data-ttu-id="13b7f-267">たとえば、&quot;Volume!&quot; では無効となり、&quot;エラー: 不明な演算子 '!' です&quot; が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-267">For example, &quot;Volume!&quot; would be invalid and return &quot; Error: Unknown operator '!'&quot;.</span></span> |
| <span data-ttu-id="13b7f-268">エラー: 不明なパラメーター '&lt;入力値&gt;' です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-268">Error: Unknown parameter '&lt;input&gt;'.</span></span> |  <span data-ttu-id="13b7f-269">命令に不明なパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="13b7f-269">The instruction contains an unknown parameter.</span></span> <span data-ttu-id="13b7f-270">たとえば、&quot;Volume=abc&quot; では無効となり、&quot;エラー: 不明なパラメーター 'abc' です&quot; と表示されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-270">For example, &quot;Volume=abc&quot; would be invalid and return &quot; Error: Unknown parameter 'abc'&quot;.</span></span> |
| <span data-ttu-id="13b7f-271">エラー: 電源が切れているときに使用できないコマンド ('&lt;入力値&gt;') です。</span><span class="sxs-lookup"><span data-stu-id="13b7f-271">Error: Command not available when off '&lt;input&gt;'.</span></span> |  <span data-ttu-id="13b7f-272">Surface Hub の電源が切れている場合、Power 以外のコマンドはこのエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="13b7f-272">When the Surface Hub is off, commands other than Power return this error.</span></span> <span data-ttu-id="13b7f-273">たとえば、&quot;Volume+&quot; では無効となり、&quot;エラー: 電源が切れているときに使用できないコマンド 'Volume' です&quot; と表示されます。</span><span class="sxs-lookup"><span data-stu-id="13b7f-273">For example, &quot;Volume+&quot; would be invalid and return &quot; Error: Command not available when off 'Volume'&quot;.</span></span> |


 

## <a name="related-topics"></a><span data-ttu-id="13b7f-274">関連トピック</span><span class="sxs-lookup"><span data-stu-id="13b7f-274">Related topics</span></span>


[<span data-ttu-id="13b7f-275">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="13b7f-275">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="13b7f-276">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="13b7f-276">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

 

 





