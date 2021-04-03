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
ms.openlocfilehash: e8181ec499364c48586f5218983f667331788fc3
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470445"
---
# <a name="applying-activesync-policies-to-device-accounts-surface-hub"></a><span data-ttu-id="56e3f-105">デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="56e3f-105">Applying ActiveSync policies to device accounts (Surface Hub)</span></span>


<span data-ttu-id="56e3f-106">Windows 10 Team 1703 オペレーティング システムを使用する Surface Hubs では、ActiveSync を使用してデバイス アカウントのメールと予定表を同期します。</span><span class="sxs-lookup"><span data-stu-id="56e3f-106">Surface Hubs using the Windows 10 Team 1703 operating system make use of ActiveSync to sync mail and calendar of the device account.</span></span> <span data-ttu-id="56e3f-107">これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。</span><span class="sxs-lookup"><span data-stu-id="56e3f-107">This allows people to join and start scheduled meetings from the Surface Hub, and allows them to email any whiteboards they have made during their meeting.</span></span>

<span data-ttu-id="56e3f-108">これらの機能が動作するには、組織の ActiveSync ポリシーが次のように構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="56e3f-108">For these features to work, the ActiveSync policies for your organization must be configured as follows:</span></span>

-   <span data-ttu-id="56e3f-109">Surface Hub のデバイス アカウントによって使用されるリソース メールボックスの、同期をブロックするグローバル ポリシーは、存在できません。</span><span class="sxs-lookup"><span data-stu-id="56e3f-109">There can't be any global policies that block synchronization of the resource mailbox that's being used by the Surface Hub’s device account.</span></span> <span data-ttu-id="56e3f-110">このようなブロック ポリシーがある場合は、許可されたデバイスとして Surface Hub を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56e3f-110">If there is such a blocking policy, you need to add the Surface Hub as an allowed device.</span></span>
-   <span data-ttu-id="56e3f-111">**PasswordEnabled** 設定が False に設定されているモバイル デバイス メールボックス ポリシーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56e3f-111">You must set a mobile device mailbox policy where the **PasswordEnabled** setting is set to False.</span></span> <span data-ttu-id="56e3f-112">その他のモバイル デバイス メールボックス ポリシーには、Surface Hub との互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="56e3f-112">Other mobile device mailbox policy settings are not compatible with the Surface Hub.</span></span>

## <a name="allowing-the-deviceid"></a><span data-ttu-id="56e3f-113">DeviceID の許可</span><span class="sxs-lookup"><span data-stu-id="56e3f-113">Allowing the DeviceID</span></span>

<span data-ttu-id="56e3f-114">組織には、Surface Hub にプロビジョニングされたデバイス アカウントが同期されないようにするグローバル ポリシーが存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="56e3f-114">Your organization may have a global policy that prevents syncing of device accounts provisioned on Surface Hubs.</span></span> <span data-ttu-id="56e3f-115">このプロパティを構成するには、「 [ActiveSync に対するデバイス ID の許可](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56e3f-115">To configure this property, see [Allowing device IDs for ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).</span></span>

## <a name="setting-passwordenabled"></a><span data-ttu-id="56e3f-116">PasswordEnabled の設定</span><span class="sxs-lookup"><span data-stu-id="56e3f-116">Setting PasswordEnabled</span></span>

<span data-ttu-id="56e3f-117">デバイス アカウントには、 **PasswordEnabled** 属性が False または 0 に設定された ActiveSync ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="56e3f-117">The device account must have an ActiveSync policy where the **PasswordEnabled** attribute is set to False or 0.</span></span> <span data-ttu-id="56e3f-118">このプロパティを構成するには、「 [Surface Hub と互換性のある Microsoft Exchange ActiveSync ポリシーの作成](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56e3f-118">To configure this property, see [Creating a Surface Hub-compatible Microsoft Exchange ActiveSync policy](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).</span></span>

 

 





