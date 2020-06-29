---
title: Microsoft Surface Hub デバイス アカウントの変更
description: デバイス アカウントを [設定] で変更すると、デバイス アカウントがプロビジョニングされていない場合にアカウントを追加したり、プロビジョニング済みのアカウントのプロパティを変更したりすることができます。
ms.assetid: AFC43043-3319-44BC-9310-29B1F375E672
ms.reviewer: ''
manager: laurawi
keywords: デバイス アカウントの変更, プロパティの変更, Surface Hub, change device account, change properties, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: b90ef3e208f1e76e4b02fb9f49e3e24030947bc7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836750"
---
# Microsoft Surface Hub デバイス アカウントの変更


デバイス アカウントを [設定] で変更すると、デバイス アカウントがプロビジョニングされていない場合にアカウントを追加したり、プロビジョニング済みのアカウントのプロパティを変更したりすることができます。

## 詳細


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">値</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ユーザー プリンシパル名</p></td>
<td align="left"><p>デバイス アカウントのユーザー プリンシパル名 (UPN) です。</p></td>
</tr>
<tr class="even">
<td align="left"><p>パスワード</p></td>
<td align="left"><p>デバイス アカウントに対応するパスワードです。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ドメイン</p></td>
<td align="left"><p>デバイス アカウントが属するドメインです。 Office 365 アカウントでは、このフィールドに入力する必要はありません。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ユーザー名</p></td>
<td align="left"><p>デバイス アカウントのユーザー名です。 Office 365 アカウントでは、このフィールドに入力する必要はありません。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>セッション開始プロトコル (SIP) アドレス</p></td>
<td align="left"><p>デバイス アカウントの SIP アドレスです。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Exchange サーバー</p></td>
<td align="left"><p>これは、デバイス アカウントの Exchange サーバーです。 デバイス アカウントのユーザー名とパスワードは、指定された Exchange サーバーに認証できる必要があります。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Exchange サービスの有効化</p></td>
<td align="left"><p>オンにすると、すべての Exchange サービスが有効になります (ようこそ画面のカレンダー、ホワイトボードのメール送信など)。 オフにすると、すべての Exchange サービスが無効になるため、Exchange サーバーを指定する必要はありません。</p></td>
</tr>
</tbody>
</table>

 

## 動作


UPN とパスワードは、AD または Azure AD のアカウントを検証するために使用されます。 検証に失敗した場合は、ドメインとユーザー名の指定が必要になる場合があります。

入力された資格情報を使用して、SIP アドレスの検出を試みます。 SIP アドレスが見つからない場合、Skype for Business では、SIP アドレスとして UPN が使用されます。 UPN がアカウントの SIP アドレスでない場合は、SIP アドレスを指定する必要があります。

デバイスでログイン資格情報に関連付けられているサーバーが見つからない場合は、Exchange サーバーのアドレスを指定する必要があります。 Microsoft Surface Hub は、Exchange サーバーを使用して ActiveSync と通信します。これにより、デバイスで複数の主要機能を有効にすることができます。

## 関連トピック


[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

 

 





