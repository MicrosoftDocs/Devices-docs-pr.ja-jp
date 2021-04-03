---
title: Surface Hub でのサービスの品質の実装
ms.reviewer: ''
manager: laurawi
description: Surface Hub で QoS を構成する方法について学習します。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 32d7493dc4a76b8e7642b927ec5db41a1e697b2a
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470485"
---
# <a name="implement-quality-of-service-qos-on-surface-hub"></a><span data-ttu-id="19c97-103">Surface Hub でのサービス品質 (QoS) の実装</span><span class="sxs-lookup"><span data-stu-id="19c97-103">Implement Quality of Service (QoS) on Surface Hub</span></span>

<span data-ttu-id="19c97-104">サービス品質 (QoS) は、管理者がリアルタイムのオーディオ/ビデオとアプリケーション共有通信のエクスペリエンスを最適化できるネットワーク テクノロジの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="19c97-104">Quality of Service (QoS) is a combination of network technologies that allows the administrators to optimize the experience of real time audio/video and application sharing communications.</span></span>
 
<span data-ttu-id="19c97-105">Surface Hub で Skype for Business の [QoS](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) を構成するには、モバイル デバイス管理 [(MDM)](manage-settings-with-mdm-for-surface-hub.md) プロバイダーを使用するか、プロビジョニング [パッケージを使用します](provisioning-packages-for-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="19c97-105">Configuring [QoS for Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) on the Surface Hub can be done using your [mobile device management (MDM) provider](manage-settings-with-mdm-for-surface-hub.md) or through a [provisioning package](provisioning-packages-for-surface-hub.md).</span></span> 
 
 
<span data-ttu-id="19c97-106">この手順では、Microsoft Intune を使用して Surface Hub の QoS を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19c97-106">This procedure explains how to configure QoS for Surface Hub using Microsoft Intune.</span></span> 

1. <span data-ttu-id="19c97-107">Intune で、 [カスタム ポリシーを作成します](https://docs.microsoft.com/intune/custom-settings-configure)。</span><span class="sxs-lookup"><span data-stu-id="19c97-107">In Intune, [create a custom policy](https://docs.microsoft.com/intune/custom-settings-configure).</span></span>

    > [!div class="mx-imgBorder"]
    > ![Intune のカスタム ポリシー作成ダイアログのスクリーンショット](images/qos-create.png)

2. <span data-ttu-id="19c97-109">[ **カスタム OMA-URI 設定] で、[** 追加] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="19c97-109">In **Custom OMA-URI Settings**, select **Add**.</span></span> <span data-ttu-id="19c97-110">追加する設定ごとに、名前、説明 (オプション)、データ型、OMA-URI、および値を入力します。</span><span class="sxs-lookup"><span data-stu-id="19c97-110">For each setting that you add, you will enter a name, description (optional), data type, OMA-URI, and value.</span></span>

    > [!div class="mx-imgBorder"]
    > ![空白の OMA-URI 設定ダイアログ ボックスのスクリーンショット](images/qos-setting.png)

3. <span data-ttu-id="19c97-112">次のカスタム OMA-URI 設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="19c97-112">Add the following custom OMA-URI settings:</span></span><br/><br/>

    <span data-ttu-id="19c97-113">名前</span><span class="sxs-lookup"><span data-stu-id="19c97-113">Name</span></span> | <span data-ttu-id="19c97-114">データ型</span><span class="sxs-lookup"><span data-stu-id="19c97-114">Data type</span></span> | <span data-ttu-id="19c97-115">OMA-URI</span><span class="sxs-lookup"><span data-stu-id="19c97-115">OMA-URI</span></span><br><span data-ttu-id="19c97-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span><span class="sxs-lookup"><span data-stu-id="19c97-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span></span> |  <span data-ttu-id="19c97-117">値</span><span class="sxs-lookup"><span data-stu-id="19c97-117">Value</span></span>
    --- | --- | --- | ---
    <span data-ttu-id="19c97-118">オーディオ ソース ポート</span><span class="sxs-lookup"><span data-stu-id="19c97-118">Audio Source Port</span></span> | <span data-ttu-id="19c97-119">String</span><span class="sxs-lookup"><span data-stu-id="19c97-119">String</span></span> |  <span data-ttu-id="19c97-120">/HubAudio/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="19c97-120">/HubAudio/SourcePortMatchCondition</span></span>  |   <span data-ttu-id="19c97-121">Skype 管理者から値を取得する</span><span class="sxs-lookup"><span data-stu-id="19c97-121">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="19c97-122">オーディオ DSCP</span><span class="sxs-lookup"><span data-stu-id="19c97-122">Audio DSCP</span></span> | <span data-ttu-id="19c97-123">Integer</span><span class="sxs-lookup"><span data-stu-id="19c97-123">Integer</span></span> |  <span data-ttu-id="19c97-124">/HubAudio/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="19c97-124">/HubAudio/DSCPAction</span></span>  |   <span data-ttu-id="19c97-125">46</span><span class="sxs-lookup"><span data-stu-id="19c97-125">46</span></span>
    <span data-ttu-id="19c97-126">ビデオ ソース ポート</span><span class="sxs-lookup"><span data-stu-id="19c97-126">Video Source Port</span></span> | <span data-ttu-id="19c97-127">String</span><span class="sxs-lookup"><span data-stu-id="19c97-127">String</span></span> |  <span data-ttu-id="19c97-128">/HubVideo/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="19c97-128">/HubVideo/SourcePortMatchCondition</span></span>   |  <span data-ttu-id="19c97-129">Skype 管理者から値を取得する</span><span class="sxs-lookup"><span data-stu-id="19c97-129">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="19c97-130">ビデオ DSCP</span><span class="sxs-lookup"><span data-stu-id="19c97-130">Video DSCP</span></span> | <span data-ttu-id="19c97-131">Integer</span><span class="sxs-lookup"><span data-stu-id="19c97-131">Integer</span></span> |  <span data-ttu-id="19c97-132">/HubVideo/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="19c97-132">/HubVideo/DSCPAction</span></span>   |   <span data-ttu-id="19c97-133">34</span><span class="sxs-lookup"><span data-stu-id="19c97-133">34</span></span>
    <span data-ttu-id="19c97-134">オーディオ プロセス名</span><span class="sxs-lookup"><span data-stu-id="19c97-134">Audio Process Name</span></span> | <span data-ttu-id="19c97-135">String</span><span class="sxs-lookup"><span data-stu-id="19c97-135">String</span></span> |  <span data-ttu-id="19c97-136">/HubAudio/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="19c97-136">/HubAudio/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="19c97-137">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="19c97-137">Microsoft.PPISkype.Windows.exe</span></span>
    <span data-ttu-id="19c97-138">ビデオ プロセス名</span><span class="sxs-lookup"><span data-stu-id="19c97-138">Video Process Name</span></span> | <span data-ttu-id="19c97-139">String</span><span class="sxs-lookup"><span data-stu-id="19c97-139">String</span></span> |  <span data-ttu-id="19c97-140">/HubVideo/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="19c97-140">/HubVideo/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="19c97-141">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="19c97-141">Microsoft.PPISkype.Windows.exe</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="19c97-142">各 **OMA-URI パス** はで始まります `./Device/Vendor/MSFT/NetworkQoSPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="19c97-142">Each **OMA-URI** path begins with `./Device/Vendor/MSFT/NetworkQoSPolicy`.</span></span> <span data-ttu-id="19c97-143">たとえば、オーディオ ソース ポートの設定の完全なパスは、 です `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` 。</span><span class="sxs-lookup"><span data-stu-id="19c97-143">The full path for the audio source port setting, for example, will be `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition`.</span></span>

4. <span data-ttu-id="19c97-144">ポリシーが作成された場合は、Surface Hub に展開します。</span><span class="sxs-lookup"><span data-stu-id="19c97-144">When the policy has been created, deploy it to Surface Hub.</span></span>


>[!WARNING]
><span data-ttu-id="19c97-145">現時点では、NetworkQoSPolicy CSP で **IPProtocolMatchCondition** の設定 [を構成できません](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)。</span><span class="sxs-lookup"><span data-stu-id="19c97-145">Currently, you cannot configure the setting **IPProtocolMatchCondition** in the [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).</span></span> <span data-ttu-id="19c97-146">この設定が構成されている場合、ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="19c97-146">If this setting is configured, the policy will fail to apply.</span></span>
 
