---
title: デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)
description: Microsoft Surface Hub のデバイス アカウントでは、ActiveSync を使用してメールとカレンダーが同期されます。 これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。
ms.assetid: FAABBA74-3088-4275-B58E-EC1070F4D110
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, ActiveSync ポリシー
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: 6e93069c2d90bdc4c2f505bc28ba0ec1a4f08076
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835798"
---
# <span data-ttu-id="a6ee2-105">デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="a6ee2-105">Applying ActiveSync policies to device accounts (Surface Hub)</span></span>


<span data-ttu-id="a6ee2-106">Microsoft Surface Hub のデバイス アカウントでは、ActiveSync を使用してメールとカレンダーが同期されます。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-106">The Microsoft Surface Hub's device account uses ActiveSync to sync mail and calendar.</span></span> <span data-ttu-id="a6ee2-107">これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-107">This allows people to join and start scheduled meetings from the Surface Hub, and allows them to email any whiteboards they have made during their meeting.</span></span>

<span data-ttu-id="a6ee2-108">これらの機能が動作するには、組織の ActiveSync ポリシーが次のように構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-108">For these features to work, the ActiveSync policies for your organization must be configured as follows:</span></span>

-   <span data-ttu-id="a6ee2-109">Surface Hub のデバイス アカウントによって使用されるリソース メールボックスの、同期をブロックするグローバル ポリシーは、存在できません。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-109">There can't be any global policies that block synchronization of the resource mailbox that's being used by the Surface Hub’s device account.</span></span> <span data-ttu-id="a6ee2-110">このようなブロックポリシーがある場合は、Surface Hub を許可されたデバイスとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-110">If there is such a blocking policy, you need to add the Surface Hub as an allowed device.</span></span>
-   <span data-ttu-id="a6ee2-111">**PasswordEnabled** 設定が False に設定されているモバイル デバイス メールボックス ポリシーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-111">You must set a mobile device mailbox policy where the **PasswordEnabled** setting is set to False.</span></span> <span data-ttu-id="a6ee2-112">その他のモバイル デバイス メールボックス ポリシーには、Surface Hub との互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-112">Other mobile device mailbox policy settings are not compatible with the Surface Hub.</span></span>

## <span data-ttu-id="a6ee2-113">DeviceID の許可</span><span class="sxs-lookup"><span data-stu-id="a6ee2-113">Allowing the DeviceID</span></span>


<span data-ttu-id="a6ee2-114">組織には、Surface Hub にプロビジョニングされたデバイス アカウントが同期されないようにするグローバル ポリシーが存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-114">Your organization may have a global policy that prevents syncing of device accounts provisioned on Surface Hubs.</span></span> <span data-ttu-id="a6ee2-115">このプロパティを構成するには、「 [ActiveSync に対するデバイス ID の許可](appendix-a-powershell-scripts-for-surface-hub.md#whitelisting-device-ids-cmdlet)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-115">To configure this property, see [Allowing device IDs for ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#whitelisting-device-ids-cmdlet).</span></span>

## <span data-ttu-id="a6ee2-116">PasswordEnabled の設定</span><span class="sxs-lookup"><span data-stu-id="a6ee2-116">Setting PasswordEnabled</span></span>


<span data-ttu-id="a6ee2-117">デバイス アカウントには、 **PasswordEnabled** 属性が False または 0 に設定された ActiveSync ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-117">The device account must have an ActiveSync policy where the **PasswordEnabled** attribute is set to False or 0.</span></span> <span data-ttu-id="a6ee2-118">このプロパティを構成するには、「 [Surface Hub と互換性のある Microsoft Exchange ActiveSync ポリシーの作成](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6ee2-118">To configure this property, see [Creating a Surface Hub-compatible Microsoft Exchange ActiveSync policy](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).</span></span>

 

 





