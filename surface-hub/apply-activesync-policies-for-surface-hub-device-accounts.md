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
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 7ead08e49d3eee2d616ac9fcf06b85dd82e136dc
ms.sourcegitcommit: 4ec96ff1cd563d055fa0689a63f136acf2794a2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "11474734"
---
# <a name="applying-activesync-policies-to-device-accounts-surface-hub"></a><span data-ttu-id="2e24e-105">デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="2e24e-105">Applying ActiveSync policies to device accounts (Surface Hub)</span></span>


<span data-ttu-id="2e24e-106">Active Directory デバイス アカウントを使用する Surface Hub (ドメイン \**\** ユーザー名形式でハブにプロビジョニング) とオンプレミスの Exchange サービスでは、ActiveSync を使用してメールと予定表を同期します。</span><span class="sxs-lookup"><span data-stu-id="2e24e-106">Surface Hubs using Active Directory device accounts (provisioned on the Hub in **domain\username** format) and on-premises Exchange services make use of ActiveSync to sync mail and calendar.</span></span> <span data-ttu-id="2e24e-107">これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。</span><span class="sxs-lookup"><span data-stu-id="2e24e-107">This allows people to join and start scheduled meetings from the Surface Hub, and allows them to email any whiteboards they have made during their meeting.</span></span>

<span data-ttu-id="2e24e-108">これらの機能が動作するには、組織の ActiveSync ポリシーが次のように構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e24e-108">For these features to work, the ActiveSync policies for your organization must be configured as follows:</span></span>

-   <span data-ttu-id="2e24e-109">Surface Hub のデバイス アカウントによって使用されるリソース メールボックスの、同期をブロックするグローバル ポリシーは、存在できません。</span><span class="sxs-lookup"><span data-stu-id="2e24e-109">There can't be any global policies that block synchronization of the resource mailbox that's being used by the Surface Hub’s device account.</span></span> <span data-ttu-id="2e24e-110">このようなブロック ポリシーがある場合は、許可されたデバイスとして Surface Hub を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e24e-110">If there is such a blocking policy, you need to add the Surface Hub as an allowed device.</span></span>
-   <span data-ttu-id="2e24e-111">**PasswordEnabled** 設定が False に設定されているモバイル デバイス メールボックス ポリシーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e24e-111">You must set a mobile device mailbox policy where the **PasswordEnabled** setting is set to False.</span></span> <span data-ttu-id="2e24e-112">その他のモバイル デバイス メールボックス ポリシーには、Surface Hub との互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="2e24e-112">Other mobile device mailbox policy settings are not compatible with the Surface Hub.</span></span>

## <a name="allowing-the-deviceid"></a><span data-ttu-id="2e24e-113">DeviceID の許可</span><span class="sxs-lookup"><span data-stu-id="2e24e-113">Allowing the DeviceID</span></span>

<span data-ttu-id="2e24e-114">組織には、Surface Hub にプロビジョニングされたデバイス アカウントが同期されないようにするグローバル ポリシーが存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="2e24e-114">Your organization may have a global policy that prevents syncing of device accounts provisioned on Surface Hubs.</span></span> <span data-ttu-id="2e24e-115">このプロパティを構成するには、「 [ActiveSync に対するデバイス ID の許可](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e24e-115">To configure this property, see [Allowing device IDs for ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).</span></span>

## <a name="setting-passwordenabled"></a><span data-ttu-id="2e24e-116">PasswordEnabled の設定</span><span class="sxs-lookup"><span data-stu-id="2e24e-116">Setting PasswordEnabled</span></span>

<span data-ttu-id="2e24e-117">デバイス アカウントには、 **PasswordEnabled** 属性が False または 0 に設定された ActiveSync ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="2e24e-117">The device account must have an ActiveSync policy where the **PasswordEnabled** attribute is set to False or 0.</span></span> <span data-ttu-id="2e24e-118">このプロパティを構成するには、「 [Surface Hub と互換性のある Microsoft Exchange ActiveSync ポリシーの作成](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e24e-118">To configure this property, see [Creating a Surface Hub-compatible Microsoft Exchange ActiveSync policy](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).</span></span>

 

 





