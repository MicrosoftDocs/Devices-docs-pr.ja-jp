---
title: Windows 10 バージョン 1703 での Surface Hub の新機能
description: Windows 10 バージョン 1703 (Creators Update) では、Microsoft Surface Hub に新機能が追加されます。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/18/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: bdc6e384839606fe6138c75e190d68a84679f5b4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834894"
---
# <span data-ttu-id="91f9d-103">Windows 10 バージョン 1703 での Microsoft Surface Hub の新機能</span><span class="sxs-lookup"><span data-stu-id="91f9d-103">What's new in Windows 10, version 1703 for Microsoft Surface Hub?</span></span>

<span data-ttu-id="91f9d-104">Surface Hub エンジニアの Jordan Marchese による、Windows 10 バージョン 1703 (Creators Update) を実行する Microsoft Surface Hub で更新された機能についてのプレゼンテーションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f9d-104">Watch Surface Hub engineer Jordan Marchese present updates to Microsoft Surface Hub with Windows 10, version 1703 (Creators Update).</span></span> 

<a href="https://www.youtube.com/watch?v=R8tX10VIgq0" target="_blank"> <img src="images/whats-new-video-thumbnail.png" alt="Link to Surface Hub video on Youtube" /></a>

<span data-ttu-id="91f9d-105">Windows 10 バージョン 1703 (Creators Update) では、Microsoft Surface Hub に次の変更が加えられています。</span><span class="sxs-lookup"><span data-stu-id="91f9d-105">Windows 10, version 1703 (also called the Creators Update), introduces the following changes for Microsoft Surface Hub.</span></span>

## <span data-ttu-id="91f9d-106">新しい設定</span><span class="sxs-lookup"><span data-stu-id="91f9d-106">New settings</span></span>

<span data-ttu-id="91f9d-107">モバイル デバイス管理 (MDM) と構成サービス プロバイダー (CSP) に設定が追加され、Surface Hub の管理機能が拡張されました。</span><span class="sxs-lookup"><span data-stu-id="91f9d-107">Settings have been added to mobile device management (MDM) and configuration service providers (CSPs) to expand the Surface Hub management capabilities.</span></span> <span data-ttu-id="91f9d-108">[新しい設定は次のとおりです](manage-settings-with-mdm-for-surface-hub.md)。</span><span class="sxs-lookup"><span data-stu-id="91f9d-108">[New settings include](manage-settings-with-mdm-for-surface-hub.md):</span></span>

- <span data-ttu-id="91f9d-109">InBoxApps/SkypeForBusiness/DomainName</span><span class="sxs-lookup"><span data-stu-id="91f9d-109">InBoxApps/SkypeForBusiness/DomainName</span></span>
- <span data-ttu-id="91f9d-110">InBoxApps/Connect/AutoLaunch</span><span class="sxs-lookup"><span data-stu-id="91f9d-110">InBoxApps/Connect/AutoLaunch</span></span>
- <span data-ttu-id="91f9d-111">Properties/DefaultVolume</span><span class="sxs-lookup"><span data-stu-id="91f9d-111">Properties/DefaultVolume</span></span>
- <span data-ttu-id="91f9d-112">Properties/ScreenTimeout</span><span class="sxs-lookup"><span data-stu-id="91f9d-112">Properties/ScreenTimeout</span></span>
- <span data-ttu-id="91f9d-113">Properties/SessionTimeout</span><span class="sxs-lookup"><span data-stu-id="91f9d-113">Properties/SessionTimeout</span></span>
- <span data-ttu-id="91f9d-114">Properties/SleepTimeout</span><span class="sxs-lookup"><span data-stu-id="91f9d-114">Properties/SleepTimeout</span></span>
- <span data-ttu-id="91f9d-115">Properties/AllowSessionResume</span><span class="sxs-lookup"><span data-stu-id="91f9d-115">Properties/AllowSessionResume</span></span>
- <span data-ttu-id="91f9d-116">Properties/AllowAutoProxyAuth</span><span class="sxs-lookup"><span data-stu-id="91f9d-116">Properties/AllowAutoProxyAuth</span></span>
- <span data-ttu-id="91f9d-117">Properties/DisableSigninSuggestions</span><span class="sxs-lookup"><span data-stu-id="91f9d-117">Properties/DisableSigninSuggestions</span></span>
- <span data-ttu-id="91f9d-118">Properties/DoNotShowMyMeetingsAndFiles</span><span class="sxs-lookup"><span data-stu-id="91f9d-118">Properties/DoNotShowMyMeetingsAndFiles</span></span>
- <span data-ttu-id="91f9d-119">System/AllowStorageCard</span><span class="sxs-lookup"><span data-stu-id="91f9d-119">System/AllowStorageCard</span></span>

<span data-ttu-id="91f9d-120">さらに、新しい [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) と [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp) に基づく設定があります。</span><span class="sxs-lookup"><span data-stu-id="91f9d-120">Plus settings based on the new [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) and [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp).</span></span>
</br>

## <span data-ttu-id="91f9d-121">プロビジョニング ウィザード</span><span class="sxs-lookup"><span data-stu-id="91f9d-121">Provisioning wizard</span></span>

<span data-ttu-id="91f9d-122">使いやすいウィザードにより、複数の Surface Hub デバイスに適用できるプロビジョニング パッケージをすばやく作成できます。Azure Active Directory に一括で参加させる機能もあります。</span><span class="sxs-lookup"><span data-stu-id="91f9d-122">An easy-to-use wizard helps you quickly create provisioning packages that you can apply to multiple Surface Hub devices, and includes bulk join to Azure Active Directory.</span></span> [<span data-ttu-id="91f9d-123">Surface Hub のプロビジョニング パッケージの作成方法については、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f9d-123">Learn how to create a provisioning package for Surface Hub.</span></span>](provisioning-packages-for-certificates-surface-hub.md)

![Surface Hub デバイスのプロビジョニング ウィザードの手順](images/wcd-wizard.png)
    
## <span data-ttu-id="91f9d-125">既存のワイヤレス ネットワークまたは LAN での Miracast</span><span class="sxs-lookup"><span data-stu-id="91f9d-125">Miracast on your existing wireless network or LAN</span></span> 

<span data-ttu-id="91f9d-126">Microsoft はダイレクト ワイヤレス リンク経由ではなく、[ローカル ネットワーク経由で Miracast ストリームを送信](miracast-over-infrastructure.md)できるように機能を拡張しました。</span><span class="sxs-lookup"><span data-stu-id="91f9d-126">Microsoft has extended the ability to [send a Miracast stream over a local network](miracast-over-infrastructure.md) rather than over a direct wireless link.</span></span> 
    
## <span data-ttu-id="91f9d-127">クラウド回復</span><span class="sxs-lookup"><span data-stu-id="91f9d-127">Cloud recovery</span></span>

<span data-ttu-id="91f9d-128">Surface Hub デバイスをリセットするときに、クラウドから工場出荷時のビルドのオペレーティング システムをダウンロードしてインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="91f9d-128">When you reset a Surface Hub device, you now have the ability to download and install a factory build of the operating system from the cloud.</span></span> [<span data-ttu-id="91f9d-129">クラウド回復について詳しくは、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f9d-129">Learn more about cloud recovery.</span></span>](device-reset-surface-hub.md#cloud-recovery)

>[!NOTE]
><span data-ttu-id="91f9d-130">クラウド回復は、プロキシ サーバーを使っている場合は機能しません。</span><span class="sxs-lookup"><span data-stu-id="91f9d-130">Cloud recovery doesn't work if you use proxy servers.</span></span>
    
![再インストール](images/reinstall.png)
    
## <span data-ttu-id="91f9d-132">セッションの終了</span><span class="sxs-lookup"><span data-stu-id="91f9d-132">End session</span></span>

<span data-ttu-id="91f9d-133">**[終了]** は **[セッションの終了]** になりました。</span><span class="sxs-lookup"><span data-stu-id="91f9d-133">**I'm done** is now **End session**.</span></span> [<span data-ttu-id="91f9d-134">[セッションの終了] の使い方については、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f9d-134">Learn how to use End session.</span></span>](i-am-done-finishing-your-surface-hub-meeting.md) 

![セッションの終了](images/end-session.png)



 

 
