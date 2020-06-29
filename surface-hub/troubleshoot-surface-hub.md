---
title: Microsoft Surface Hub のトラブルシューティング
description: セットアップの問題、Exchange ActiveSync エラーなどの一般的な問題のトラブルシューティングを行います。
ms.assetid: CF58F74D-8077-48C3-981E-FCFDCA34B34A
ms.reviewer: ''
manager: laurawi
keywords: 一般的な問題のトラブルシューティング, セットアップの問題, Exchange ActiveSync エラー, Troubleshoot common problems, setup issues, Exchange ActiveSync errors
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2018
ms.localizationpriority: medium
ms.openlocfilehash: fe87c56474a05152f991a5b63f6abf0cf05e8b03
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834893"
---
# Microsoft Surface Hub のトラブルシューティング


セットアップの問題、Exchange ActiveSync エラーなどの一般的な問題のトラブルシューティングを行います。

[Surface Hub Hardware Diagnostic ツール](https://www.microsoft.com/store/p/surface-hub-hardware-diagnostic/9nblggh51f2g?rtc=1&activetab=pivot%3aoverviewtab)には、ハブの重要な機能が仕様どおりに動作することを確認するための対話型テストが含まれています。 この診断では、ハードウェアだけでなく、リソース アカウントをテストして、環境に合わせて適切に構成されていることも確認できます。 問題が発生した場合は、結果を保存して Surface Hub のサポート チームと共有できます。 使用方法については、[Surface Hub Hardware Diagnostic ツールを使用してデバイス アカウントをテストする方法に関するページ](https://support.microsoft.com/help/4077574/using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-accoun)を参照してください。

一般的な問題と、その原因や考えられる修正方法を次の表に示します。 「[セットアップのトラブルシューティング](#setup-troubleshooting)」セクションでは、デバイス上の問題と、最初の実行エクスペリエンスで発生する各種問題の一覧を示します。 「[Exchange ActiveSync エラー](#exchange-activesync-errors)」セクションでは、デバイスを Microsoft Exchange ActiveSync サーバーと同期しようとするときに発生する可能性のある一般的なエラーを示します。




## セットアップのトラブルシューティング


このセクションでは、Microsoft Surface Hub を設定するときに想定される問題のトラブルシューティングに役立つ、原因および考えられる修正方法の一覧を示します。

### デバイス上

最初の実行プログラムの完了後に Surface Hub で発生する問題に対して考えられる修正方法です。

<table>
<tr>
<th>問題</th>
<th>原因</th>
<th>考えられる修正方法</th>
</tr>
<tr>
<td rowspan="2">
<p>自動承諾/辞退メッセージが届かない。</p>
</td>
<td>
<p>デバイス アカウントが、メッセージを自動的に承諾または辞退するように構成されていません。</p>
</td>
<td>
<p>PowerShell コマンドレット <code>Set-CalendarProcessing $upn -AutomateProcessing AutoAccept</code> を使います。</p>
</td>
</tr>
<tr>
<td>
<p>デバイス アカウントが、外部会議出席依頼を処理するように構成されていません。</p>
</td>
<td>
<p>PowerShell コマンドレット <code>Set-CalendarProcessing $upn -ProcessExternalMeetingMessages $true</code> を使います。</p>
</td>
</tr>
<tr>
<td>
<p>カレンダーがようこそ画面に表示されていない、または "予定は古くなっている可能性があります (アカウントが準備されていません)" というメッセージが表示されている。</p>
</td>
<td>
<p>この Surface Hub にデバイス アカウントが設定されていません。</p>
</td>
<td>
<p>[設定] を使ってデバイス アカウントをプロビジョニングします。</p>
</td>
</tr>
<tr>
<td>
<p>カレンダーがようこそ画面に表示されない、または "今日の予定 (プロビジョニング超過)" というメッセージが表示されている。</p>
</td>
<td>
<p>デバイス アカウントがプロビジョニングされているデバイスが多すぎます。</p>
</td>
<td>
<p>他のプロビジョニング先デバイスからデバイス アカウントを削除します。 これは Exchange 管理ポータルを使って行うことができます。</p>
</td>
</tr>
<tr>
<td>
<p>カレンダーがようこそ画面に表示されない、または "今日の予定 (資格情報が無効です)" というメッセージが表示されている。</p>
</td>
<td>
<p>デバイス アカウントのパスワードの期限が切れ、無効になりました。</p>
</td>
<td>
<p>[設定] でアカウントのパスワードを更新します。 「<a href="password-management-for-surface-hub-device-accounts.md">パスワード管理</a>」もご覧ください。</p>
</td>
</tr>
<tr>
<td>
<p>カレンダーがようこそ画面に表示されない、または "今日の予定 (アカウント ポリシー)" というメッセージが表示されている。</p>
</td>
<td>
<p>デバイス アカウントで無効な ActiveSync ポリシーが使用されています。</p>
</td>
<td>
<p><code>PasswordEnabled == False</code> となる ActiveSync ポリシーがデバイス アカウントにあることを確認します。</p>
</td>
</tr>
<tr>
<td>
<p>カレンダーがようこそ画面に表示されない、または "予定は古くなっている可能性があります。" というメッセージが表示されている。</p>
</td>
<td>
<p>Exchange が有効ではありません。</p>
</td>
<td>[設定] を使って Exchange サービスのデバイス アカウントを有効にします。 正しいセットの ActiveSync ポリシーがあって、Exchange サービスが動作するうえで必要な証明書もインストールされていることを確認する必要があります。</td>
</tr>
<tr>
<td>
<p>Skype for Business にログインできない。</p>
</td>
<td>
<p>デバイス アカウントに、セッション開始プロトコル (SIP) アドレス プロパティがありません。</p>
</td>
<td>
<p>アカウントに SIP アドレス プロパティがなく、アカウントのユーザー プリンシパル名 (UPN) が実際の SIP アドレスと一致していません。 アカウントに SIP アドレスが設定されているか、設定アプリを使って SIP アドレスを追加する必要があります。</p>
</td>
</tr>
<tr>
<td>
<p>Skype for Business にログインできない。</p>
</td>
<td>
<p>デバイス アカウントには、Skype for Business に対して認証を受けるために証明書が必要です。</p>
</td>
<td>
<p>プロビジョニング パッケージを使って適切な証明書をインストールします。</p>
</td>
</tr>
</table>
 

### 最初の実行

Surface Hub の最初の実行プログラムで発生する問題に対して考えられる修正方法です。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">問題</th>
<th align="left">原因</th>
<th align="left">考えられる修正方法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ドメインとユーザー名の入力が求められたときにアカウントが見つからない。</p></td>
<td align="left"><p>ドメインが完全修飾ドメイン名 (FQDN) である必要があります。</p></td>
<td align="left"><p>ドメイン フィールドに FQDN を指定する必要があります。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-device-acct-page"></a>[デバイス アカウント] ページ (新しいアカウントの設定に関する問題)

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">問題</th>
<th align="left">原因</th>
<th align="left">考えられる修正方法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>指定されたアカウントが Azure AD で見つからない。</p></td>
<td align="left"><p>指定されたアカウントのユーザー プリンシパル名 (UPN) に、Azure AD でアクセスできないテナントが設定されています。</p></td>
<td align="left"><p>機能しているインターネット接続があること、およびデバイスから Microsoft Online Services にアクセスできることを確認します。 アカウントの資格情報が正しく入力されていることを確認します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>指定されたディレクトリに到達できない。</p></td>
<td align="left"><p>指定されたアカウントのドメインに、到達できないドメインが指定されています。</p></td>
<td align="left"><p>機能しているネットワーク接続があること、およびデバイスからドメイン コントローラーにアクセスできることを確認します。 アカウントの資格情報が正しく入力されていることを確認します。 代わりに FQDN を使うこともできます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Exchange サーバーを自動検出できない。</p></td>
<td align="left"><p>Exchange サーバーが自動検出用に構成されていません。</p></td>
<td align="left"><p>デバイス アカウントに対して Exchange サーバーの自動検出を有効にするか、アカウントの Exchange サーバーのアドレスを手動で入力します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>アカウントの資格情報を入力した後で SIP アドレスを検出できなかった。</p></td>
<td align="left"><p>Active Directory または Azure AD に SIP アドレス エントリがありませんでした。</p></td>
<td align="left"><p>アカウントが Skype for Business に対して有効になっていることと、アカウントに SIP アドレスが指定されていることを確認します。 確認できない場合は、テキスト ボックスに SIP アドレスを手動で入力できます。</p></td>
</tr>
</tbody>
</table>

 

### [デバイス アカウント] ページ (既存のアカウントの設定に関する問題)

<table>
<tr>
<th>問題</th>
<th>原因</th>
<th>エラー コード</th>
<th>考えられる修正方法</th>
</tr>
<tr>
<td>
<p>指定した資格情報を使ってアカウントが認証されなかった。</p>
</td>
<td>
<p>Active Directory (AD) のユーザーとしてアカウントが有効になっていないか、または認証を受けるためにパスワードが必要です。あるいは、パスワードが正しくありません。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>資格情報が正しく入力されていることを確認します。 アカウントを AD のユーザーとして有効にしてパスワードを追加するか、RoomMailboxPassword を設定します</p>. </td>
</tr>
<tr>
<td>
<p>Exchange サーバーを指定すると、エラー 0x800C0019 が表示される。</p>
</td>
<td>
<p>デバイス アカウントには、認証を受けるために証明書が必要です。</p>
</td>
<td>
<p>0x800C0019</p>
</td>
<td>
<p>プロビジョニング パッケージを使って適切な証明書をインストールします。</p>
</td>
</tr>
<tr>
<td>
<p>デバイス アカウントの資格情報が、指定された Exchange サーバーに対して有効ではない。</p>
</td>
<td>
<p>指定された Exchange サーバーが、デバイス アカウントのメールボックスがホストされている場所ではありません。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>デバイス アカウントに対して正しい Exchange メール サーバーを指定していることを確認します。</p>
</td>
</tr>
<tr>
<td>
<p>Exchange サーバーにアクセスしようとすると HTTP タイムアウトが発生する。</p>
</td>
<td></td>
<td>
<p>0x80072EE2</p>
</td>
<td></td>
</tr>
<tr>
<td>
<p>指定された Exchange サーバーが見つからなかった。</p>
</td>
<td>
<p>指定された Exchange サーバーが見つかりませんでした。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>機能しているネットワークまたはインターネット接続があること、および指定した Exchange サーバーが正しいことを確認します。</p>
</td>
</tr>
<tr>
<td>
<p>http がサポートされていない。</p>
</td>
<td>
<p><i>https://</i> ではなく <i>http://</i> を使う Exchange サーバーが指定されました。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>https を使う Exchange サーバーを使います。</p>
</td>
</tr>
<tr>
<td rowspan="3">
<div><p>ActiveSync に関する [このアカウントに問題があります] というページが表示される。</p>
</div>
<div> </div>
</td>
<td>
<p>ActiveSync ポリシー PasswordEnabled が True (1) に設定されています。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>PasswordEnabled が False (0) に設定された新しい ActiveSync ポリシーを作成し、そのポリシーをアカウントに適用します。</p>
</td>
</tr>
<tr>
<td>
<p>Surface Hub が Exchange に接続していません。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>機能しているネットワークまたはインターネット接続があることを確認します。</p>
</td>
</tr>
<tr>
<td>
<p>Exchange からエラーを示す状態コードが返されます。</p>
</td>
<td>
<p>なし</p>
</td>
<td>
<p>機能しているネットワークまたはインターネット接続があることを確認します。</p>
</td>
</tr>
</table>
 

### <a href="" id="first-run-domain-join-page"></a>最初の実行 (ドメイン参加ページの問題)

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">問題</th>
<th align="left">原因</th>
<th align="left">考えられる修正方法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ドメインに参加しようとすると、指定された資格情報を使ってアカウントを認証できなかったことを示すエラーが発生する。</p></td>
<td align="left"><p>指定された資格情報では、指定されたドメインに参加できません。</p></td>
<td align="left"><p>指定されたドメインに存在するアカウントの正しい資格情報を入力します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ドメイン内のグループを指定すると、グループがドメインに見つからなかったことを示すエラーが発生する。</p></td>
<td align="left"><p>グループが削除されたか、存在しなくなっています。</p></td>
<td align="left"><p>ドメイン内にグループが存在することを確認します。</p></td>
</tr>
</tbody>
</table>

 

### 最初の実行 (Exchange サーバー ページ)

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">問題</th>
<th align="left">原因</th>
<th align="left">考えられる修正方法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>このページが表示され、Exchange サーバーのアドレスを入力するように求められる。</p></td>
<td align="left"><p>Exchange サーバーが自動検出用に構成されていません。</p></td>
<td align="left"><p>デバイス アカウントに対して Exchange サーバーの自動検出を有効にするか、アカウントの Exchange サーバーのアドレスを手動で入力します。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-on-device"></a>最初の実行 (デバイス上の問題)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">問題</th>
<th align="left">原因</th>
<th align="left">エラー コード</th>
<th align="left">考えられる修正方法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>メール/カレンダーを同期できない。</p></td>
<td align="left"><p>アカウントで、許可されたデバイスとして Surface Hub が許可されていません。</p></td>
<td align="left"><p>0x86000C1C</p></td>
<td align="left"><p><strong>メールボックスの ActiveSyncAllowedDeviceIds プロパティを設定して、Surface Hub デバイス ID を許可リストに追加し </strong> ます。</p></td>
</tr>
</tbody>
</table>

 



 

## Exchange ActiveSync エラー


このセクションでは、状態コード、マッピング、ユーザー メッセージ、および管理者が Exchange ActiveSync エラーを解決するために実行できる操作を示します。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">16 進コード</th>
<th align="left">マッピング</th>
<th align="left">ユーザーにわかりやすいメッセージ</th>
<th align="left">管理者が実行する操作</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x85010002</p></td>
<td align="left"><p>E_HTTP_DENIED</p></td>
<td align="left"><p>パスワードを更新する必要があります。</p></td>
<td align="left"><p>パスワードを更新します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072EFD</p></td>
<td align="left"><p>WININET_E_CANNOT_CONNECT</p></td>
<td align="left"><p>現在、サーバに接続できません。 しばらく待ってからやり直すか、アカウントの設定を確認してください。</p></td>
<td align="left"><p>サーバー名が正しく、到達できることを確認します。 デバイスがネットワークに接続されていることを確認します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C29</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_NOTPROVISIONED (ポリシーが一致しません)</p></td>
<td align="left"><p>アカウントが、Surface Hub と互換性のないポリシーで構成されています。</p></td>
<td align="left"><p>このアカウントの <strong>PasswordEnabled</strong> ポリシーを無効にします。</p>
<p>アカウントがポリシー更新間隔内でサーバー通知を受け取らなかった場合、エラーが発生したというバグがありました。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C4C</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAXIMUMDEVICESREACHED</p></td>
<td align="left"><p>アカウントのデバイス パートナーシップが多すぎます。</p></td>
<td align="left"><p>サーバーのパートナーシップを 1 つ以上削除します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C0A</p></td>
<td align="left"><p>E_NEXUS_STATUS_SERVERERROR_RETRYLATER</p></td>
<td align="left"><p>現在、サーバに接続できません。</p></td>
<td align="left"><p>サーバーがオンラインに戻るまで待機します。 問題が解決しない場合は、アカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050003</p></td>
<td align="left"><p>E_CREDENTIALS_EXPIRED (資格情報は期限が切れているため、更新する必要があります)</p></td>
<td align="left"><p>パスワードを更新する必要があります。</p></td>
<td align="left"><p>パスワードを更新します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x8505000D</p></td>
<td align="left"><p>E_AIRSYNC_RESET_RETRY</p></td>
<td align="left"><p>現在、サーバに接続できません。 しばらく待つか、アカウントの設定を確認してください。</p></td>
<td align="left"><p>これは、通常は一時的なエラーです。ただし、問題が解決しない場合は、アカウントに関連付けられているデバイスの数を確認して、数が多すぎるときは一部のデバイスを削除します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C16</p></td>
<td align="left"><p>E_NEXUS_STATUS_USER_HASNOMAILBOX</p></td>
<td align="left"><p>メールボックスは、別のサーバーに移行されました。</p></td>
<td align="left"><p>このエラーは表示されません。 問題が解決しない場合は、アカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010004</p></td>
<td align="left"><p>E_HTTP_FORBIDDEN</p></td>
<td align="left"><p>現在、サーバに接続できません。 しばらく待ってからもう一度やり直すか、アカウントの設定を確認してください。</p></td>
<td align="left"><p>サーバー名を確認してサーバー名が正しいことを確かめます。 アカウントで証明書ベースの認証を使っている場合は、証明書がまだ有効なことを確認します。有効ではない場合は証明書を更新します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85030028</p></td>
<td align="left"><p>E_ACTIVESYNC_PASSWORD_OR_GETCERT</p></td>
<td align="left"><p>アカウントのパスワードまたはクライアント証明書が存在しないか、無効です。</p></td>
<td align="left"><p>パスワードの更新、クライアント証明書の展開、またはその両方を実行します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C2A</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_POLICYREFRESH</p></td>
<td align="left"><p>アカウントが、Surface Hub と互換性のないポリシーで構成されています。</p></td>
<td align="left"><p>このアカウントの PasswordEnabled ポリシーを無効にします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050002</p></td>
<td align="left"><p>E_CREDENTIALS_UNAVAILABLE</p></td>
<td align="left"><p>パスワードを更新する必要があります。</p></td>
<td align="left"><p>パスワードを更新します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE2</p></td>
<td align="left"><p>WININET_E_TIMEOUT</p></td>
<td align="left"><p>ネットワークがサーバー通知を受信するために必要なアイドルタイムアウトの最小値をサポートしていないか、サーバーがオフラインになっています。</p></td>
<td align="left"><p>サーバーが実行されていることを確認します。 NAT 設定を確認します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85002004</p></td>
<td align="left"><p>E_FAIL_ABORT</p></td>
<td align="left"><p>このエラーは、ハングしている同期を中断するために使用され、ユーザーには公開されません。 対話型同期の強制、アカウントの削除、またはアカウント設定の更新を実行する場合に、診断データに表示されます。</p></td>
<td align="left"><p>なし。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010017</p></td>
<td align="left"><p>E_HTTP_SERVICE_UNAVAIL</p></td>
<td align="left"><p>現在、サーバに接続できません。 しばらく待つか、アカウントの設定を確認してください。</p></td>
<td align="left"><p>サーバー名を確認してサーバー名が正しいことを確かめます。 サーバーがオンラインに戻るまで待機します。 問題が解決しない場合は、アカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C0D</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAILBOX_SERVEROFFLINE</p></td>
<td align="left"><p>現在、サーバに接続できません。 しばらく待つか、アカウントの設定を確認してください。</p></td>
<td align="left"><p>サーバー名を確認してサーバー名が正しいことを確かめます。 サーバーがオンラインに戻るまで待機します。 問題が解決しない場合は、アカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85030027</p></td>
<td align="left"><p>E_ACTIVESYNC_GETCERT</p></td>
<td align="left"><p>Exchange サーバーには証明書が必要です。</p></td>
<td align="left"><p>Surface Hub に適切な EAS 証明書をインポートします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C2B</p></td>
<td align="left"><p>E_NEXUS_STATUS_INVALID_POLICYKEY</p></td>
<td align="left"><p>アカウントが、Surface Hub と互換性のないポリシーで構成されています。</p></td>
<td align="left"><p>このアカウントの PasswordEnabled ポリシーを無効にします。</p>
<p>アカウントがポリシー更新間隔内でサーバー通知を受け取らなかった場合、エラーが発生したというバグがありました。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010005</p></td>
<td align="left"><p>E_HTTP_NOT_FOUND</p></td>
<td align="left"><p>サーバー名が無効です。</p></td>
<td align="left"><p>サーバー名を確認してサーバー名が正しいことを確かめます。 問題が解決しない場合は、アカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85010014</p></td>
<td align="left"><p>E_HTTP_SERVER_ERROR</p></td>
<td align="left"><p>サーバーに接続できません。</p></td>
<td align="left"><p>サーバー名を確認してサーバー名が正しいことを確かめます。 同期をトリガーし、問題が解決しない場合はアカウントを再プロビジョニングします。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE7</p></td>
<td align="left"><p>WININET_E_NAME_NOT_RESOLVED</p></td>
<td align="left"><p>サーバー名またはアドレスは解決されませんでした。</p></td>
<td align="left"><p>サーバー名が正しく入力されていることを確認します。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x8007052F</p></td>
<td align="left"><p>ERROR_ACCOUNT_RESTRICTION</p></td>
<td align="left"><p>Exchange サーバーの自動検出中に、ログインしているユーザーがサーバーにログインできなくなるポリシーが、適用されています。</p></td>
<td align="left"><p>これは、タイミングの問題です。 アカウントの資格情報を再確認します。 資格情報が正しい場合は、再プロビジョニングしてみます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x800C0019</p></td>
<td align="left"><p>INET_E_INVALID_CERTIFICATE</p></td>
<td align="left"><p>このリソースへのアクセスに必要なセキュリティ証明書は無効です。</p></td>
<td align="left"><p>指定されたデバイス アカウントに必要な、正しい ActiveSync 証明書をインストールします。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072F0D</p></td>
<td align="left"><p>WININET_E_INVALID_CA</p></td>
<td align="left"><p>証明機関が無効か、正しくありません。 証明書がないため、Exchange サーバーを自動検出できません。</p></td>
<td align="left"><p>指定されたデバイス アカウントに必要な、正しい ActiveSync 証明書をインストールします。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80004005</p></td>
<td align="left"><p>E_FAIL</p></td>
<td align="left"><p>指定されたドメインが見つかりませんでした。 Exchange サーバーを自動検出できず、設定で指定されていませんでした。</p></td>
<td align="left"><p>入力したドメインが FQDN であること、および Exchange サーバーのテキスト ボックスに Exchange サーバーを入力していることを確認します。</p></td>
</tr>
</tbody>
</table>

## サポートに問い合わせ

質問がある場合やヘルプが必要な場合は、[サポートリクエストを作成](https://support.microsoft.com/supportforbusiness/productselection)できます。


 
## 関連するコンテンツ

- [Surface Hub への Miracast 接続のトラブルシューティング](https://docs.microsoft.com/surface-hub/miracast-troubleshooting)
 





