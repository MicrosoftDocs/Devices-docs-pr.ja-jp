---
title: Microsoft Exchange プロパティ (Surface Hub)
description: デバイス アカウントの一部の Microsoft Exchange プロパティは、Microsoft Surface Hub で最適な会議エクスペリエンスを得られるように、特定の値に設定する必要があります。
ms.assetid: 3E84393B-C425-45BF-95A6-D6502BA1BF29
ms.reviewer: ''
manager: laurawi
keywords: Microsoft Exchange プロパティ, デバイス アカウント, Surface Hub, Windows PowerShell コマンドレット, Microsoft Exchange properties, device account, Surface Hub, Windows PowerShell cmdlet
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: 8879762857146011f3e1a198b72a895bc6bf9473
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836238"
---
# <span data-ttu-id="fef7b-104">Microsoft Exchange プロパティ (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="fef7b-104">Microsoft Exchange properties (Surface Hub)</span></span>


<span data-ttu-id="fef7b-105">デバイス アカウントの一部の Microsoft Exchange プロパティは、Microsoft Surface Hub で最適な会議エクスペリエンスを得られるように、特定の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fef7b-105">Some Microsoft Exchange properties of the device account must be set to particular values to have the best meeting experience on Microsoft Surface Hub.</span></span> <span data-ttu-id="fef7b-106">次の表に、PowerShell コマンドレット パラメーター、その目的、および設定する値に基づいて、さまざまな Exchange プロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-106">The following table lists various Exchange properties based on PowerShell cmdlet parameters, their purpose, and the values they should be set to.</span></span>

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fef7b-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fef7b-107">Property</span></span></th>
<th align="left"><span data-ttu-id="fef7b-108">説明</span><span class="sxs-lookup"><span data-stu-id="fef7b-108">Description</span></span></th>
<th align="left"><span data-ttu-id="fef7b-109">値</span><span class="sxs-lookup"><span data-stu-id="fef7b-109">Value</span></span></th>
<th align="left"><span data-ttu-id="fef7b-110">影響</span><span class="sxs-lookup"><span data-stu-id="fef7b-110">Impact</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fef7b-111">AutomateProcessing</span><span class="sxs-lookup"><span data-stu-id="fef7b-111">AutomateProcessing</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-112">AutomateProcessing パラメーターは、メールボックスのカレンダー処理を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="fef7b-112">The AutomateProcessing parameter enables or disables calendar processing on the mailbox.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-113">AutoAccept</span><span class="sxs-lookup"><span data-stu-id="fef7b-113">AutoAccept</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-114">Surface Hub で、空き時間に基づいて会議出席依頼を自動的に承諾または辞退できます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-114">The Surface Hub will be able to automatically accept or decline meeting requests based on its availability.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="fef7b-115">AddOrganizerToSubject</span><span class="sxs-lookup"><span data-stu-id="fef7b-115">AddOrganizerToSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-116">AddOrganizerToSubject パラメーターは、会議の開催者名を会議出席依頼の件名として使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-116">The AddOrganizerToSubject parameter specifies whether the meeting organizer's name is used as the subject of the meeting request.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-117">$False</span><span class="sxs-lookup"><span data-stu-id="fef7b-117">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-118">ようこそ画面には、会議の開催者が 2 回表示されません (2 回表示される場合は、開催者としてと会議の件名の両方に表示されます)。</span><span class="sxs-lookup"><span data-stu-id="fef7b-118">The welcome screen will not show the meeting organizer twice (instead of showing it as both the organizer and in the meeting subject).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fef7b-119">AllowConflicts</span><span class="sxs-lookup"><span data-stu-id="fef7b-119">AllowConflicts</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-120">AllowConflicts パラメーターは、競合する会議出席依頼を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-120">The AllowConflicts parameter specifies whether to allow conflicting meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-121">$False</span><span class="sxs-lookup"><span data-stu-id="fef7b-121">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-122">Surface Hub では、別の会議時間と競合する会議出席依頼を辞退します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-122">The Surface Hub will decline meeting requests that conflict with another meeting’s time.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="fef7b-123">DeleteComments</span><span class="sxs-lookup"><span data-stu-id="fef7b-123">DeleteComments</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-124">DeleteComments パラメーターは、受信した会議出席依頼のメッセージ本文で任意のテキストを削除または保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-124">The DeleteComments parameter specifies whether to remove or keep any text in the message body of incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-125">$False</span><span class="sxs-lookup"><span data-stu-id="fef7b-125">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-126">会議中に必要であれば、会議のメッセージ本文を Surface Hub から取得して保持できます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-126">The message body of meetings can be retained and retrieved from a Surface Hub if you need it during a meeting.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fef7b-127">DeleteSubject</span><span class="sxs-lookup"><span data-stu-id="fef7b-127">DeleteSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-128">DeleteSubject パラメーターは、受信した会議出席依頼の件名を削除または保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-128">The DeleteSubject parameter specifies whether to remove or keep the subject of incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-129">$False</span><span class="sxs-lookup"><span data-stu-id="fef7b-129">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-130">会議出席依頼の件名を Surface Hub に表示できます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-130">Meeting request subjects can be shown on the Surface Hub.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="fef7b-131">RemovePrivateProperty</span><span class="sxs-lookup"><span data-stu-id="fef7b-131">RemovePrivateProperty</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-132">RemovePrivateProperty パラメーターは、受信した会議出席依頼に設定されたプライベート フラグをクリアするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-132">The RemovePrivateProperty parameter specifies whether to clear the private flag for incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-133">$False</span><span class="sxs-lookup"><span data-stu-id="fef7b-133">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-134">プライベート会議の件名は、ようこそ画面にプライベートとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-134">Private meeting subjects will show as Private on the welcome screen.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fef7b-135">AddAdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="fef7b-135">AddAdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-136">AddAdditionalResponse パラメーターは、会議出席依頼に返信するときにリソース メールボックスから追加情報を送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-136">The AddAdditionalResponse parameter specifies whether additional information will be sent from the resource mailbox when responding to meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-137">$True</span><span class="sxs-lookup"><span data-stu-id="fef7b-137">$True</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-138">会議出席依頼に返信を送ると、応答にカスタム テキストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-138">When a response is sent to a meeting request, custom text will be provided in the response.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="fef7b-139">AdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="fef7b-139">AdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-140">AdditionalResponse パラメーターは、会議出席依頼への応答に含める追加情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="fef7b-140">The AdditionalResponse parameter specifies the additional information to be included in responses to meeting requests.</span></span></p>
<div class="alert">
<strong><span data-ttu-id="fef7b-141">注: </strong> このテキストは、AddAdditionalResponse が $True に設定されていない場合は送信されません。</span><span class="sxs-lookup"><span data-stu-id="fef7b-141">Note</strong>This text will not be sent unless AddAdditionalResponse is set to $True.</span></span>
</div>
<div>
 
</div></td>
<td align="left"><p><span data-ttu-id="fef7b-142">選択: 追加の応答を使って、Surface Hub を使用するか Surface Hub からリソースにポイントする方法をユーザーに通知できます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-142">Your choice—the additional response can be used to inform people how to use a Surface Hub or point them towards resources.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fef7b-143">追加の応答メッセージを追加すると、会議での Surface Hub 使用方法の概要をユーザーに通知できます。</span><span class="sxs-lookup"><span data-stu-id="fef7b-143">Adding an additional response message can provide people an introduction to how they can use a Surface Hub in their meeting.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 





