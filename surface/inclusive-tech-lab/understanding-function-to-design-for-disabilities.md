---
title: 障がいを持つデザインの機能について
description: 包括的な技術ラボからの Microsoft Inclusive Design リファレンス
ms.localizationpriority: medium
ms.sitesec: library
author: InclusiveTechLab
ms.author: brycejo
ms.topic: article
ms.date: 05/20/2021
manager: krhunter
ms.prod: surface
ms.technology: windows
ms.openlocfilehash: d423fb3e4aa6f87ae0d6686607cd30920ecad5b8
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11578142"
---
# <a name="understanding-function-to-design-for-disabilities"></a><span data-ttu-id="42918-103">障がいを持つデザインの機能について</span><span class="sxs-lookup"><span data-stu-id="42918-103">Understanding Function to Design for Disabilities</span></span>
**<span data-ttu-id="42918-104">包括的な技術ラボからの Microsoft Inclusive Design リファレンス</span><span class="sxs-lookup"><span data-stu-id="42918-104">A Microsoft Inclusive Design reference from the Inclusive Tech Lab</span></span>**

<span data-ttu-id="42918-105">Microsoft の包括的なデザインのプラクティスでは、Nothing &ldquo; About Us,Without Us を信じています。 &rdquo; 障がい者コミュニティと一緒に設計し、障がいのある人がもっと多くを達成する力を与える製品やサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="42918-105">In our Inclusive Design practice at Microsoft, we believe in &ldquo;Nothing About Us, Without Us.&rdquo; We design with the disability community to create products and services that empower people with disabilities to achieve more.</span></span> 

<span data-ttu-id="42918-106">私たちの実践では、エンジニアやデザイナーが作業している人の機能の側面を伝えるのに苦労する場合があります。</span><span class="sxs-lookup"><span data-stu-id="42918-106">In our practice we have observed that engineers and designers sometimes struggle to communicate the aspects of function for the people they are working with.</span></span> <span data-ttu-id="42918-107">診断や状態を理解しようとすると、生産性に反する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42918-107">Trying to understand diagnosis or conditions can be counter productive.</span></span> <span data-ttu-id="42918-108">ほとんどの人は医療従事者ではないので、語彙が不足しています。また、医療用語が必ずしも適切とは限らない。</span><span class="sxs-lookup"><span data-stu-id="42918-108">Most of us aren’t medical professionals so we lack the vocabulary; also medical terminology isn’t always appropriate.</span></span>

<span data-ttu-id="42918-109">この参照を作成して、エンジニアとデザイナーは、相互作用の障壁につながる可能性がある機能の側面と、これらの障壁を克服するために必要なファシリテーターについて理解し、議論する方法を提供しました。</span><span class="sxs-lookup"><span data-stu-id="42918-109">We created this reference to provide engineers and designers a way to understand and discuss the aspects of function that can lead to barriers in interaction, and the facilitators needed to overcome these barriers.</span></span> <span data-ttu-id="42918-110">包括的な設計プラクティスの目標は、障壁を実装する前に認識する方法です。</span><span class="sxs-lookup"><span data-stu-id="42918-110">The goal of our inclusive design practice is to recognize the barriers before we implement them.</span></span> <span data-ttu-id="42918-111">人間の多様性の機能を促進するフォームを作成する。</span><span class="sxs-lookup"><span data-stu-id="42918-111">To create forms that facilitate the function of human diversity.</span></span>

<span data-ttu-id="42918-112">この作品は、世界保健機関の国際機能、障[](https://www.who.int/standards/classifications/international-classification-of-functioning-disability-and-health)がい、健康の分類 (ICF) に影響を受けました。</span><span class="sxs-lookup"><span data-stu-id="42918-112">This work was inspired by the World Health Organization’s – [International Classification of Functioning, Disability and Health](https://www.who.int/standards/classifications/international-classification-of-functioning-disability-and-health) (ICF).</span></span> <span data-ttu-id="42918-113">この資料を簡潔で、アプローチ可能で、技術の分野に応じた文脈に合ったものにするためのガイドに取り組む。</span><span class="sxs-lookup"><span data-stu-id="42918-113">We strive in our guide to make this material concise, approachable, and contextual to our field of technology.</span></span> <span data-ttu-id="42918-114">これは、変化と成長が予想される生きているドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="42918-114">This is a living document that we expect will change and grow.</span></span>

<span data-ttu-id="42918-115">繰り返しになりますが、障がい者コミュニティと一緒に設計しています。この参照は、相互作用の文書化、採用ススクリーンとアンケートの作成、使いやすさのレビューやバグの作成などのアクティビティの一部です。</span><span class="sxs-lookup"><span data-stu-id="42918-115">To reiterate, we design WITH the disability community – we see this reference being part of activities like documenting interactions, creating recruitment screeners and surveys, and writing usability reviews and bugs.</span></span> <span data-ttu-id="42918-116">製品の作成プロセスの一環として、この資料を効果的に活用できる可能性のある方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="42918-116">There are many potential ways that this material can be leveraged effectively as part of our product creation process.</span></span>

## <a name="what-this-is"></a><span data-ttu-id="42918-117">これが何か</span><span class="sxs-lookup"><span data-stu-id="42918-117">What this is</span></span>

<span data-ttu-id="42918-118">この作業の目的は、包括的なデザインを実践する際に考慮すべき人間の多様性要因の参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="42918-118">The goal of this work is to provide a reference of human diversity factors to consider when practicing inclusive design.</span></span> <span data-ttu-id="42918-119">このフレームワークは、毎日使用するテクノロジの認知、モビリティ、ビジョン、聴覚、音声、および感覚的な要求の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="42918-119">This framework outlines the cognitive, mobility, vision, hearing, speech, and sensory demands of the technology we all use daily.</span></span> <span data-ttu-id="42918-120">アプローチ可能な例を通して、能力のレベルと製品の設計との間に不一致の相互作用が発生した場合に人が直面する可能性がある障壁を説明します。</span><span class="sxs-lookup"><span data-stu-id="42918-120">Through approachable examples, we try to illustrate barriers a person may face when they experience a mismatched interaction between their level of abilities and the design of a product.</span></span>

## <a name="what-this-is-not"></a><span data-ttu-id="42918-121">これが何ではないか</span><span class="sxs-lookup"><span data-stu-id="42918-121">What this is not</span></span>

<span data-ttu-id="42918-122">この参照は、アクセシビリティ ソリューションを作成するための基準ガイドラインではありません。</span><span class="sxs-lookup"><span data-stu-id="42918-122">This reference is not a prescriptive guideline for creating accessibility solutions.</span></span> <span data-ttu-id="42918-123">むしろ、人が遭遇する可能性のある障壁を特定するために使用できるリソースです。</span><span class="sxs-lookup"><span data-stu-id="42918-123">Rather, it’s a resource you can use to identify potential barriers a person may encounter.</span></span> <span data-ttu-id="42918-124">このドキュメントは静的ではないので、大きくなることを覚えておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="42918-124">It is important to remember that this document isn’t static and will grow.</span></span> <span data-ttu-id="42918-125">包括的に取り組む一方で、説明されている多くのインスタンスは(個人によって)一緒に発生する可能性があります。また、人によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="42918-125">While we strive to be comprehensive, many instances described can occur in conjunction with one another (depending on the individual) and may present differently from one person to another.</span></span>

## <a name="contents-of-this-reference"></a><span data-ttu-id="42918-126">このリファレンスの内容</span><span class="sxs-lookup"><span data-stu-id="42918-126">Contents of this reference</span></span>

**[<span data-ttu-id="42918-127">認知とは</span><span class="sxs-lookup"><span data-stu-id="42918-127">What is cognition?</span></span>](cognition.md)** <span data-ttu-id="42918-128">— [注意](cognition-attention.md); [メモリ](cognition-memory.md); [判断](cognition-judgment.md); [処理 (速度)](cognition-processing-speed.md); [処理 (理解)](cognition-processing-comprehension.md);</span><span class="sxs-lookup"><span data-stu-id="42918-128">— [Attention](cognition-attention.md); [Memory](cognition-memory.md); [Judgment](cognition-judgment.md); [Processing (speed)](cognition-processing-speed.md); [Processing (comprehension)](cognition-processing-comprehension.md);</span></span> 

**[<span data-ttu-id="42918-129">モビリティとは</span><span class="sxs-lookup"><span data-stu-id="42918-129">What is mobility?</span></span>](mobility.md)** <span data-ttu-id="42918-130">— [把握します](mobility-grasp.md)。 [細かい運動能力](mobility-fine-motor-skills.md); [調整](mobility-coordination.md); [コントロール (自発的な動きと不本意な動き)](mobility-control.md); [速度](mobility-speed.md); [筋のトーン](mobility-muscle-tone.md); [持久力](mobility-endurance.md); [ポスチャ](mobility-posture.md);</span><span class="sxs-lookup"><span data-stu-id="42918-130">— [Grasp](mobility-grasp.md); [Fine motor skills](mobility-fine-motor-skills.md); [Coordination](mobility-coordination.md); [Control (voluntary vs. involuntary movement)](mobility-control.md); [Speed](mobility-speed.md); [Muscle tone](mobility-muscle-tone.md); [Endurance](mobility-endurance.md); [Posture](mobility-posture.md);</span></span> 

**[<span data-ttu-id="42918-131">ビジョンとは</span><span class="sxs-lookup"><span data-stu-id="42918-131">What is vision?</span></span>](vision.md)** <span data-ttu-id="42918-132">— [失明 (視力なし)](vision-blindness-sightlessness.md); [低視力 (部分的に見える)](vision-low-vision-partially-sighted.md); [減少した acuity](vision-decreased-acuity.md); [視覚フィールドの損失](vision-visual-field-loss.md)。 [色覚失明](vision-color-blindness.md); [Photophobia (光感度)](vision-photophobia-light-sensitivity.md);</span><span class="sxs-lookup"><span data-stu-id="42918-132">— [Blindness (sightlessness)](vision-blindness-sightlessness.md); [Low vision (partially sighted)](vision-low-vision-partially-sighted.md); [Decreased acuity](vision-decreased-acuity.md); [Visual field loss](vision-visual-field-loss.md); [Color blindness](vision-color-blindness.md); [Photophobia (light sensitivity)](vision-photophobia-light-sensitivity.md);</span></span> 

**[<span data-ttu-id="42918-133">ヒアリングとは</span><span class="sxs-lookup"><span data-stu-id="42918-133">What is hearing?</span></span>](hearing.md)** <span data-ttu-id="42918-134">— [難聴 (軽度)](hearing-mild.md); [難聴 (中等度/重度)](hearing-moderate-severe.md); [難聴 (深遠)](hearing-profound.md); [難聴 (非対称)](hearing-asymmetrical.md);</span><span class="sxs-lookup"><span data-stu-id="42918-134">— [Hearing Loss (mild)](hearing-mild.md); [Hearing loss (moderate/severe)](hearing-moderate-severe.md); [Hearing loss (profound)](hearing-profound.md); [Hearing loss (asymmetrical)](hearing-asymmetrical.md);</span></span> 

**[<span data-ttu-id="42918-135">音声、音声、およびコミュニケーションとは</span><span class="sxs-lookup"><span data-stu-id="42918-135">What is voice, speech, and communication?</span></span>](voice-speech-communication.md)** <span data-ttu-id="42918-136">— [Aphasia (受け入れ)](voice-speech-communication-aphasia-receptive.md);[Aphasia (表現力)](voice-speech-communication-aphasia-expressive.md);[音声品質](voice-speech-communication-speech-quality.md);[ソーシャル参加](voice-speech-communication-social-participation.md);[非言語 ;](voice-speech-communication-non-verbal.md)</span><span class="sxs-lookup"><span data-stu-id="42918-136">— [Aphasia (receptive)](voice-speech-communication-aphasia-receptive.md); [Aphasia (expressive)](voice-speech-communication-aphasia-expressive.md); [Speech quality](voice-speech-communication-speech-quality.md); [Social participation](voice-speech-communication-social-participation.md); [Non-verbal](voice-speech-communication-non-verbal.md);</span></span> 

**[<span data-ttu-id="42918-137">感覚と知覚とは</span><span class="sxs-lookup"><span data-stu-id="42918-137">What is sensation and perception?</span></span>](sensation-perception.md)** <span data-ttu-id="42918-138">—[前庭 ;](sensation-perception-vestibular.md)[慢性的な痛み](sensation-perception-chronic-pain.md);[スキンの整合性](sensation-perception-skin-integrity.md)。[感覚 (過敏と過敏)](sensation-perception-sensation.md);[Proprioception](sensation-perception-proprioception.md);</span><span class="sxs-lookup"><span data-stu-id="42918-138">— [Vestibular](sensation-perception-vestibular.md); [Chronic pain](sensation-perception-chronic-pain.md); [Skin integrity](sensation-perception-skin-integrity.md); [Sensation (hypersensitive and hyposensitive)](sensation-perception-sensation.md); [Proprioception](sensation-perception-proprioception.md);</span></span> 

## <a name="created-by"></a><span data-ttu-id="42918-139">作成者</span><span class="sxs-lookup"><span data-stu-id="42918-139">Created by</span></span>

### <a name="authors"></a><span data-ttu-id="42918-140">作成者</span><span class="sxs-lookup"><span data-stu-id="42918-140">Authors</span></span>
<span data-ttu-id="42918-141">Kaitlyn Jones, Bryce Johnson, Kris Hunter</span><span class="sxs-lookup"><span data-stu-id="42918-141">Kaitlyn Jones, Bryce Johnson, Kris Hunter</span></span>

### <a name="illustrator"></a><span data-ttu-id="42918-142">イラストレーター</span><span class="sxs-lookup"><span data-stu-id="42918-142">Illustrator</span></span>
<span data-ttu-id="42918-143">Lou Patnode</span><span class="sxs-lookup"><span data-stu-id="42918-143">Lou Patnode</span></span>

### <a name="editors"></a><span data-ttu-id="42918-144">エディター</span><span class="sxs-lookup"><span data-stu-id="42918-144">Editors</span></span>
<span data-ttu-id="42918-145">Cat Jackson, Martina Dalton, Solomon Romney</span><span class="sxs-lookup"><span data-stu-id="42918-145">Cat Jackson, Martina Dalton, Solomon Romney</span></span>

### <a name="special-thanks"></a><span data-ttu-id="42918-146">特別な感謝</span><span class="sxs-lookup"><span data-stu-id="42918-146">Special Thanks</span></span>
<span data-ttu-id="42918-147">Panos Panay, Robin Seiler, Allison Flanigan, Aimee Hayes, Steve Godfrey, John Porter, Tiffany Chen, Jenny Lay-Flurrie, Mary Bellard, David Dzumba, David Dame</span><span class="sxs-lookup"><span data-stu-id="42918-147">Panos Panay, Robin Seiler, Allison Flanigan, Aimee Hayes, Steve Godfrey, John Porter, Tiffany Chen, Jenny Lay-Flurrie, Mary Bellard, David Dzumba, David Dame</span></span>


[comment]: # (フッターを含める)
