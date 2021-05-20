---
title: 速度
description: 制限時間が経過する前に必要な速度でアクションを実行する機能
ms.localizationpriority: medium
ms.sitesec: library
author: InclusiveTechLab
ms.author: brycejo
ms.topic: article
ms.date: 05/20/2021
manager: krhunter
ms.prod: surface
ms.technology: windows
ms.openlocfilehash: 438824d1900dad284de2a0db9c18ed51702e499f
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11578146"
---
# <a name="speed"></a><span data-ttu-id="e8eed-103">速度</span><span class="sxs-lookup"><span data-stu-id="e8eed-103">Speed</span></span>

**<span data-ttu-id="e8eed-104">制限時間が切れている前に、必要な速度でアクションを実行する機能。</span><span class="sxs-lookup"><span data-stu-id="e8eed-104">The ability to perform an action at the necessary rate before the time limit has expired.</span></span>**

<span data-ttu-id="e8eed-105">移動速度は、移動の開始に要する時間と、移動の完了に要する時間の両方によって特徴付けされます。</span><span class="sxs-lookup"><span data-stu-id="e8eed-105">Speed of movement is characterized by both the amount of time it takes to initiate the movement and the amount of time it takes to complete the movement.</span></span> <span data-ttu-id="e8eed-106">タスクを高速で実行するのが難しいと、デバイスとのやり取りが困難で面倒になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8eed-106">Difficulty performing tasks at a high speed can make interaction with devices difficult and cumbersome.</span></span> <span data-ttu-id="e8eed-107">たとえば、手の動きが遅い場合、1 つの文を長く、手の込むプロセスに入力できます。</span><span class="sxs-lookup"><span data-stu-id="e8eed-107">For example, slow hand movements can make typing a single sentence into a long, arduous process.</span></span> <span data-ttu-id="e8eed-108">画面のロックを解除するために "スワイプアップ" などの迅速な動きを必要とするジェスチャでは、このような速度でこのモーションを実行できないユーザーへのアクセスが除外される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8eed-108">Gestures that require swift movements such as “swiping up” to unlock the screen may exclude access to users who can’t perform this motion at such a speed.</span></span>

<span data-ttu-id="e8eed-109">遅い動きは、動きや協調に影響を与える任意の種類の状態によって引き起こされます。疲労、パーキンソン病や脳性麻痺などの神経学的な状態、脳または脊髄の傷害、手と指の傷害。</span><span class="sxs-lookup"><span data-stu-id="e8eed-109">Slow movements can be caused by any kind of condition that affects movement or coordination—fatigue, neurological conditions like Parkinson’s or cerebral palsy, injuries to the brain or spinal cord, and injuries to hands and fingers.</span></span>


## <a name="barriers"></a><span data-ttu-id="e8eed-110">バリア</span><span class="sxs-lookup"><span data-stu-id="e8eed-110">Barriers</span></span>
* <span data-ttu-id="e8eed-111">タスクを完了するために迅速で流動的なモーションを必要とするジェスチャ (タッチ 画面のジェスチャ、ユーザーによるジェスチャー入力HoloLens)</span><span class="sxs-lookup"><span data-stu-id="e8eed-111">Gestures that require swift, fluid motions to complete a task (such as touch screen gestures, gestural input with HoloLens)</span></span>
* <span data-ttu-id="e8eed-112">2 つのアクションを同時に実行する必要があるタスク (ショートカット、固定キーを有効にする場合は、FN と F1 を押すなど)</span><span class="sxs-lookup"><span data-stu-id="e8eed-112">Tasks that require performing two actions simultaneously (such as holding down FN and F1 to turn on a shortcut, sticky keys)</span></span>
* <span data-ttu-id="e8eed-113">繰り返しモーションが必要なアクション (入力、ダブルクリックなど)</span><span class="sxs-lookup"><span data-stu-id="e8eed-113">Actions that require repetitive motions (such as typing, double-clicking)</span></span>
* <span data-ttu-id="e8eed-114">割り当てられた時間が経過する前にアクションを実行しない場合に期限切れになる時間指定応答</span><span class="sxs-lookup"><span data-stu-id="e8eed-114">Timed responses which expire if action isn’t taken before the allotted time is up</span></span>

## <a name="facilitators"></a><span data-ttu-id="e8eed-115">ファシリテーター</span><span class="sxs-lookup"><span data-stu-id="e8eed-115">Facilitators</span></span>

* <span data-ttu-id="e8eed-116">速度を補完する代替入力のサポート (入力の代わりにディクテーションなど)</span><span class="sxs-lookup"><span data-stu-id="e8eed-116">Support for alternate inputs that supplement speed (such as dictation instead of typing)</span></span>
* <span data-ttu-id="e8eed-117">変更されたアクセシビリティ設定のサポート (マウス カーソルの移動速度の向上など)</span><span class="sxs-lookup"><span data-stu-id="e8eed-117">Support for altered accessibility settings (such as increasing mouse cursor movement speed)</span></span>
* <span data-ttu-id="e8eed-118">設定応答を排除または細長くする機能</span><span class="sxs-lookup"><span data-stu-id="e8eed-118">Settings that eliminate or elongate timed responses</span></span>


## <a name="examples"></a><span data-ttu-id="e8eed-119">例</span><span class="sxs-lookup"><span data-stu-id="e8eed-119">Examples</span></span>

:::image type="content" source="images/mobility-speed-barrier.jpg" alt-text="女性は車いすに座り、ひたの上にタブレットを持っています。 タッチスクリーンで入力中に見下ろしている彼女は、ストレスを感じているように見えます。":::

<span data-ttu-id="e8eed-122">BARRIER — キーボードでの入力のようなタスクは、速いペースで指を動かできない人には時間がかかり、激しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8eed-122">BARRIER — Tasks like typing on a keyboard can be time consuming and strenuous for someone who can't move their fingers at a fast pace.</span></span>

:::image type="content" source="images/mobility-speed-facilitator.jpg" alt-text="タブレット画面にオンスクリーン キーボードが表示され、誰かが入力した &quot; I'm without &quot; the apostrophe.":::

<span data-ttu-id="e8eed-124">FACILITATOR : 予測テキストのような機能をサポートすると、入力の物理的な要求が減少し、誰かがタスクをより速い速度で実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e8eed-124">FACILITATOR — Support for features like predictive text can decrease the physical demands of typing and allow someone to perform a task at a faster rate.</span></span>

&nbsp;

[comment]: # (フッター ステートメント)
___
<span data-ttu-id="e8eed-126">この参照の目的は、ユーザーが関数の側面を文書化して議論するために使用できる概念を提供します。</span><span class="sxs-lookup"><span data-stu-id="e8eed-126">The purpose of this reference is to provide concepts people can use to document and discuss aspects of function.</span></span> <span data-ttu-id="e8eed-127">デザインは障がいを持つユーザーに対して行う必要があります。この参照は、そのアクティビティをサポートすることを意図しています。代わるのではありません。</span><span class="sxs-lookup"><span data-stu-id="e8eed-127">Design should happen with people with disabilities, this reference is meant to support that activity, not replace it.</span></span> 