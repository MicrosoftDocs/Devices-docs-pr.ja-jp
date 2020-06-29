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
# Microsoft Exchange プロパティ (Surface Hub)


デバイス アカウントの一部の Microsoft Exchange プロパティは、Microsoft Surface Hub で最適な会議エクスペリエンスを得られるように、特定の値に設定する必要があります。 次の表に、PowerShell コマンドレット パラメーター、その目的、および設定する値に基づいて、さまざまな Exchange プロパティを示します。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">プロパティ</th>
<th align="left">説明</th>
<th align="left">値</th>
<th align="left">影響</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>AutomateProcessing</p></td>
<td align="left"><p>AutomateProcessing パラメーターは、メールボックスのカレンダー処理を有効または無効にします。</p></td>
<td align="left"><p>AutoAccept</p></td>
<td align="left"><p>Surface Hub で、空き時間に基づいて会議出席依頼を自動的に承諾または辞退できます。</p></td>
</tr>
<tr class="even">
<td align="left"><p>AddOrganizerToSubject</p></td>
<td align="left"><p>AddOrganizerToSubject パラメーターは、会議の開催者名を会議出席依頼の件名として使用するかどうかを指定します。</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>ようこそ画面には、会議の開催者が 2 回表示されません (2 回表示される場合は、開催者としてと会議の件名の両方に表示されます)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>AllowConflicts</p></td>
<td align="left"><p>AllowConflicts パラメーターは、競合する会議出席依頼を許可するかどうかを指定します。</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>Surface Hub では、別の会議時間と競合する会議出席依頼を辞退します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DeleteComments</p></td>
<td align="left"><p>DeleteComments パラメーターは、受信した会議出席依頼のメッセージ本文で任意のテキストを削除または保持するかどうかを指定します。</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>会議中に必要であれば、会議のメッセージ本文を Surface Hub から取得して保持できます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DeleteSubject</p></td>
<td align="left"><p>DeleteSubject パラメーターは、受信した会議出席依頼の件名を削除または保持するかどうかを指定します。</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>会議出席依頼の件名を Surface Hub に表示できます。</p></td>
</tr>
<tr class="even">
<td align="left"><p>RemovePrivateProperty</p></td>
<td align="left"><p>RemovePrivateProperty パラメーターは、受信した会議出席依頼に設定されたプライベート フラグをクリアするかどうかを指定します。</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>プライベート会議の件名は、ようこそ画面にプライベートとして表示されます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>AddAdditionalResponse</p></td>
<td align="left"><p>AddAdditionalResponse パラメーターは、会議出席依頼に返信するときにリソース メールボックスから追加情報を送信するかどうかを指定します。</p></td>
<td align="left"><p>$True</p></td>
<td align="left"><p>会議出席依頼に返信を送ると、応答にカスタム テキストが提供されます。</p></td>
</tr>
<tr class="even">
<td align="left"><p>AdditionalResponse</p></td>
<td align="left"><p>AdditionalResponse パラメーターは、会議出席依頼への応答に含める追加情報を指定します。</p>
<div class="alert">
<strong>注: </strong> このテキストは、AddAdditionalResponse が $True に設定されていない場合は送信されません。
</div>
<div>
 
</div></td>
<td align="left"><p>選択: 追加の応答を使って、Surface Hub を使用するか Surface Hub からリソースにポイントする方法をユーザーに通知できます。</p></td>
<td align="left"><p>追加の応答メッセージを追加すると、会議での Surface Hub 使用方法の概要をユーザーに通知できます。</p></td>
</tr>
</tbody>
</table>

 

 

 





