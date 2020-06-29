---
title: Surface Hub でのサービスの品質の実装
ms.reviewer: ''
manager: laurawi
description: Surface Hub で QoS を構成する方法について説明します。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 99172e77be260559c770f5fc8a1438734bed660f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835190"
---
# <span data-ttu-id="4b698-103">Surface Hub にサービスの品質 (QoS) を実装する</span><span class="sxs-lookup"><span data-stu-id="4b698-103">Implement Quality of Service (QoS) on Surface Hub</span></span>

<span data-ttu-id="4b698-104">QoS (Quality of Service) は、管理者がリアルタイムの音声/ビデオとアプリケーション共有通信のエクスペリエンスを最適化できるネットワークテクノロジを組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="4b698-104">Quality of Service (QoS) is a combination of network technologies that allows the administrators to optimize the experience of real time audio/video and application sharing communications.</span></span>
 
<span data-ttu-id="4b698-105">Surface Hub で[の Skype For business の QoS の](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)構成は、[モバイルデバイス管理 (MDM) プロバイダー](manage-settings-with-mdm-for-surface-hub.md)または[プロビジョニングパッケージ](provisioning-packages-for-surface-hub.md)を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4b698-105">Configuring [QoS for Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) on the Surface Hub can be done using your [mobile device management (MDM) provider](manage-settings-with-mdm-for-surface-hub.md) or through a [provisioning package](provisioning-packages-for-surface-hub.md).</span></span> 
 
 
<span data-ttu-id="4b698-106">この手順では、Microsoft Intune を使用して Surface Hub の QoS を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b698-106">This procedure explains how to configure QoS for Surface Hub using Microsoft Intune.</span></span> 

1. <span data-ttu-id="4b698-107">Intune で、[カスタムポリシーを作成](https://docs.microsoft.com/intune/custom-settings-configure)します。</span><span class="sxs-lookup"><span data-stu-id="4b698-107">In Intune, [create a custom policy](https://docs.microsoft.com/intune/custom-settings-configure).</span></span>

    ![Intune の [カスタムポリシーの作成] ダイアログのスクリーンショット](images/qos-create.png)

2. <span data-ttu-id="4b698-109">[**カスタムの Oma-uri 設定**] で、[**追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b698-109">In **Custom OMA-URI Settings**, select **Add**.</span></span> <span data-ttu-id="4b698-110">追加する各設定について、名前、説明 (省略可能)、データ型、OMA-URI、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b698-110">For each setting that you add, you will enter a name, description (optional), data type, OMA-URI, and value.</span></span>

    ![空白の [OMA-URI 設定] ダイアログボックスのスクリーンショット](images/qos-setting.png)

3. <span data-ttu-id="4b698-112">次のカスタムの OMA URI 設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="4b698-112">Add the following custom OMA-URI settings:</span></span>

    <span data-ttu-id="4b698-113">名前</span><span class="sxs-lookup"><span data-stu-id="4b698-113">Name</span></span> | <span data-ttu-id="4b698-114">データ型</span><span class="sxs-lookup"><span data-stu-id="4b698-114">Data type</span></span> | <span data-ttu-id="4b698-115">OMA-URI</span><span class="sxs-lookup"><span data-stu-id="4b698-115">OMA-URI</span></span><br><span data-ttu-id="4b698-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span><span class="sxs-lookup"><span data-stu-id="4b698-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span></span> |  <span data-ttu-id="4b698-117">値</span><span class="sxs-lookup"><span data-stu-id="4b698-117">Value</span></span>
    --- | --- | --- | ---
    <span data-ttu-id="4b698-118">オーディオソースポート</span><span class="sxs-lookup"><span data-stu-id="4b698-118">Audio Source Port</span></span> | <span data-ttu-id="4b698-119">String</span><span class="sxs-lookup"><span data-stu-id="4b698-119">String</span></span> |  <span data-ttu-id="4b698-120">/HubAudio/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="4b698-120">/HubAudio/SourcePortMatchCondition</span></span>  |   <span data-ttu-id="4b698-121">Skype 管理者から値を取得する</span><span class="sxs-lookup"><span data-stu-id="4b698-121">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="4b698-122">オーディオ DSCP</span><span class="sxs-lookup"><span data-stu-id="4b698-122">Audio DSCP</span></span> | <span data-ttu-id="4b698-123">Integer</span><span class="sxs-lookup"><span data-stu-id="4b698-123">Integer</span></span> |  <span data-ttu-id="4b698-124">/HubAudio/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="4b698-124">/HubAudio/DSCPAction</span></span>  |   <span data-ttu-id="4b698-125">46</span><span class="sxs-lookup"><span data-stu-id="4b698-125">46</span></span>
    <span data-ttu-id="4b698-126">ビデオソースポート</span><span class="sxs-lookup"><span data-stu-id="4b698-126">Video Source Port</span></span> | <span data-ttu-id="4b698-127">String</span><span class="sxs-lookup"><span data-stu-id="4b698-127">String</span></span> |  <span data-ttu-id="4b698-128">/HubVideo/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="4b698-128">/HubVideo/SourcePortMatchCondition</span></span>   |  <span data-ttu-id="4b698-129">Skype 管理者から値を取得する</span><span class="sxs-lookup"><span data-stu-id="4b698-129">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="4b698-130">ビデオ DSCP</span><span class="sxs-lookup"><span data-stu-id="4b698-130">Video DSCP</span></span> | <span data-ttu-id="4b698-131">Integer</span><span class="sxs-lookup"><span data-stu-id="4b698-131">Integer</span></span> |  <span data-ttu-id="4b698-132">/HubVideo/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="4b698-132">/HubVideo/DSCPAction</span></span>   |   <span data-ttu-id="4b698-133">34</span><span class="sxs-lookup"><span data-stu-id="4b698-133">34</span></span>
    <span data-ttu-id="4b698-134">オーディオプロセス名</span><span class="sxs-lookup"><span data-stu-id="4b698-134">Audio Process Name</span></span> | <span data-ttu-id="4b698-135">String</span><span class="sxs-lookup"><span data-stu-id="4b698-135">String</span></span> |  <span data-ttu-id="4b698-136">/HubAudio/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="4b698-136">/HubAudio/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="4b698-137">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="4b698-137">Microsoft.PPISkype.Windows.exe</span></span>
    <span data-ttu-id="4b698-138">ビデオプロセス名</span><span class="sxs-lookup"><span data-stu-id="4b698-138">Video Process Name</span></span> | <span data-ttu-id="4b698-139">String</span><span class="sxs-lookup"><span data-stu-id="4b698-139">String</span></span> |  <span data-ttu-id="4b698-140">/HubVideo/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="4b698-140">/HubVideo/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="4b698-141">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="4b698-141">Microsoft.PPISkype.Windows.exe</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="4b698-142">各**oma-uri**パスは、で始まり `./Device/Vendor/MSFT/NetworkQoSPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="4b698-142">Each **OMA-URI** path begins with `./Device/Vendor/MSFT/NetworkQoSPolicy`.</span></span> <span data-ttu-id="4b698-143">オーディオソースポートの設定の完全なパスがあり `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` ます。</span><span class="sxs-lookup"><span data-stu-id="4b698-143">The full path for the audio source port setting, for example, will be `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition`.</span></span>




4. <span data-ttu-id="4b698-144">ポリシーが作成されたら、 [Surface Hub に展開します。](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)</span><span class="sxs-lookup"><span data-stu-id="4b698-144">When the policy has been created, [deploy it to the Surface Hub.](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)</span></span>


>[!WARNING]
><span data-ttu-id="4b698-145">現時点では、 [NETWORKQOSPOLICY CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)で**Ipprotocolmatchcondition**を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b698-145">Currently, you cannot configure the setting **IPProtocolMatchCondition** in the [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).</span></span> <span data-ttu-id="4b698-146">この設定を構成すると、ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="4b698-146">If this setting is configured, the policy will fail to apply.</span></span>
 
