---
title: セットアップのワークシート (Surface Hub)
description: Microsoft Surface Hub の事前セットアップが完了して、初回セットアップを開始する準備ができたら、このセクションに示されている情報がすべて揃っていることを確認します。
ms.assetid: AC6F925B-BADE-48F5-8D53-8B6FFF6EE3EB
ms.reviewer: ''
manager: laurawi
keywords: セットアップのワークシート, セットアップ前, 初回セットアップ, Setup worksheet, pre-setup, first-time setup
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: e0c31082669336d3762fd02f46a939aa8b0ff1bc
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836446"
---
# セットアップのワークシート (Surface Hub)


Microsoft Surface Hub の事前セットアップが完了して、初回セットアップを開始する準備ができたら、このセクションに示されている情報がすべて揃っていることを確認します。

構成する各 Surface Hub ごとにこれらの情報を入力する必要がありますが、プロキシ情報やドメイン資格情報など、すべての Surface Hub に共通の情報もあります。 デバイスの構成方法や、組織のインフラストラクチャの環境構成によっては、不要になる情報もあります。

<table>
<tr>
<th>プロパティ</th>
<th>用途</th>
<th>例</th>
<th>実際の値</th>
</tr>
<tr>
<td>
<p>プロキシ情報</p>
</td>
<td>
<p>ネットワーク アクセスやインターネット アクセスにプロキシが使用されている場合、スクリプトかサーバー/ポート情報を提供する必要があります。</p>
</td>
<td>
<p>プロキシ スクリプト:  <code>http://contoso/proxy.pa</code> </br>
- または - </br>
サーバー情報とポート情報: 10.10.10.100、ポート 80
</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>ワイヤレス ネットワークの資格情報 (ユーザー名とパスワード)</p>
</td>
<td>
<p>Wi-Fi にデバイスを接続する場合、ワイヤレス ネットワークにユーザー資格情報が必要です。</p>
</td>
<td>
<p>admin1@contoso.com、#MyPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>デバイス アカウントの UPN またはドメイン\ユーザー名、およびデバイス アカウントのパスワード</p>
</td>
<td>
<p>ユーザー プリンシパル名 (UPN) またはドメイン\ユーザー名と、デバイス アカウントのパスワードです。 メール、カレンダー、および Skype for Business は、互換性のあるデバイス アカウントに依存します。</p>
</td>
<td>
<p> UPN: ConfRoom15@contoso.com、#Passw0rd1 </br>
- または - <br> 
ドメインとユーザー名: CONTOSO\ConfRoom15、#Passw0rd1</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>デバイス アカウントの Microsoft Exchange サーバー</p>
</td>
<td>
<p>デバイス アカウントの Exchange サーバーです。
メール、カレンダー、および Skype for Business は、互換性のあるデバイス アカウントに依存します。
メールとカレンダーが機能するには、有効な Exchange サーバーがデバイス アカウントに必要です。 これはデバイスによって自動で検出されます。</p>
</td>
<td>
<p>outlook.office365.com</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>デバイス アカウントのセッション開始プロトコル (SIP) アドレス</p>
</td>
<td>
<p>デバイス アカウントの Skype for Business SIP アドレスです。
メール、カレンダー、および Skype for Business は、互換性のあるデバイス アカウントに依存します。
Skype for Business が機能するには、有効な SIP アドレスがデバイス アカウントに必要です。 これはデバイスによって自動で検出されます。</p>
</td>
<td>
<p>sip: ConfRoom15@contoso.com</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>フレンドリ名</p>
</td>
<td>
<p>デバイスのフレンドリ名とは、ユーザーがワイヤレスで Surface Hub に接続する際に表示される名前です。 この名前は、Surface Hub の画面の目立つ位置に表示されます。
接続時に他の Surface Hub との区別が付きやすいよう、フレンドリ名はわかりやすく他と重複しないものにすることをお勧めします。</p>
</td>
<td>
<p>Conference Room 15</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>デバイス名</p>
</td>
<td>
<p>デバイス名は、ドメイン参加に使用する名前で、デバイスが MDM に登録されている場合に MDM プロバイダーで表示される ID になります。
(デバイスをドメインに参加させる場合) デバイス名は、ユーザーの Active Directory ドメインにおける他のデバイスと同じ名前にしないようにする必要があります。 名前が一意でない場合、デバイスはドメインに参加できません。
</p>
</td>
<td>
<p>confroom15</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>Azure AD に参加する場合</b></p>
</td>
</tr>
<tr>
<td>
<p>Azure AD テナント ユーザー資格情報 (ユーザー名とパスワード)</p>
</td>
<td>
<p>Azure Active Directory (Azure AD) 組織内のユーザーをデバイスの管理者にするためには、Azure AD に参加する必要があります。
Azure AD に参加するには、有効なユーザー資格情報が必要になります。</p>
</td>
<td>
<p>admin1@contoso.com、#MyPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>ドメインに参加する場合</b></p>
</td>
</tr>
<tr>
<td>
<p>参加するドメイン</p>
</td>
<td>
<p>任意のセキュリティ グループをデバイスの管理者にするために参加する必要があるドメインです。
完全修飾ドメイン名 (FQDN) が必要になります。</p>
</td>
<td>
<p>contoso (短い名前) または contoso.corp.com (FQDN)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>ドメイン アカウント資格情報 (ユーザー名とパスワード)</p>
</td>
<td>
<p>ドメイン参加に必要なアカウント資格情報を十分に提供しないと、ドメインに参加することはできません。 参加するドメインと、ドメイン参加に必要な資格情報を提供したら、任意のセキュリティ グループがデバイスの設定を変更することが可能になります。</p>
</td>
<td>
<p>admin1、#MyPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>管理者セキュリティ グループのエイリアス</p>
</td>
<td>
<p>Active Directory (AD) 内のセキュリティ グループです。このセキュリティ グループのメンバーは、デバイスの設定を変更することができます。</p>
</td>
<td>
<p>SurfaceHubAdmins</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>ローカル管理者を使用する場合</b></p>
</td>
</tr>
<tr>
<td>
<p>ローカル管理者アカウント資格情報 (ユーザー名とパスワード)</p>
</td>
<td>
<p>AD ドメインまたは Azure AD に参加しない場合は、デバイスでローカル管理者アカウントを作成することができます。</p>
</td>
<td>
<p>admin1、#MyPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>証明書またはアプリをインストールする必要がある場合</b></p>
</td>
</tr>
<tr>
<td>
<p>USB ドライブ</p>
</td>
<td>
<p>初回の実行前に、証明書またはユニバーサル アプリをインストールすることがわかっていれば、「<a href="provisioning-packages-for-certificates-surface-hub.md">プロビジョニング パッケージの作成</a>」の手順を実行します。 プロビジョニング パッケージは、USB ドライブに作成されます。</p>
</td>
<td>
<p></p>
</td>
<td>
<p></p>
</td>
</tr>
</table> 





