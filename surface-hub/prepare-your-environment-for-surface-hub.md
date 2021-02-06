---
title: Microsoft Surface Hub の環境を準備する (v1)
description: このセクションでは、Microsoft Surface Hub の全機能を使用できるように環境を準備するために必要な手順の概要を説明します。
ms.assetid: 336A206C-5893-413E-A270-61BFF3DF7DA9
ms.reviewer: ''
manager: laurawi
keywords: 環境の準備, Surface Hub の機能, デバイス アカウントの作成およびテスト, ネットワークが使用可能かどうかの確認
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 12/04/2017
ms.localizationpriority: medium
appliesto:
- Surface Hub
ms.openlocfilehash: 95b575e5213e3e11685b342cb2a7b77eb3e868a0
ms.sourcegitcommit: 7809222a51eb184f07d6b3ffbdd04a6272b247f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "11314400"
---
# Microsoft Surface Hub の環境を準備する (v1)


ここでは、設定の依存関係とセットアップ プロセスの概要を示します。 Surface Hub のセットアップに必要な情報を収集し、環境を準備するには、このセクションの内容をご確認ください。


## インフラストラクチャの依存関係の確認
お使いの IT インフラストラクチャで Surface Hub の機能が確実に動作するように、次の依存関係を確認してください。

| 依存関係        | 目的           |
|-------------|------------------|
| Active Directory または Azure Active Directory (Azure AD) | <p>Surface Hub は、Active Directory または Azure AD のアカウント (**デバイス アカウント**と呼ばれます) を使用して Exchange および Skype for Business のサービスにアクセスします。 デバイス アカウントの資格情報を検証し、デバイス アカウントの表示名、エイリアス、Exchange サーバー、セッション開始プロトコル (SIP) アドレスなどの情報にアクセスすることを目的に、Surface Hub が Active Directory ドメイン コントローラーまたは Azure AD テナントに接続できる必要があります。</p>また、Surface Hub のドメイン参加または Azure AD 参加により、承認されたユーザーのグループによる Surface Hub の設定の構成が可能になります。 |
| Exchange (Exchange 2013 以降または Exchange Online)、Exchange ActiveSync | <p>Exchange は、メールとカレンダーの機能を有効にするために使用されます。また、デバイスを使用しているユーザーが会議出席依頼を Surface Hub に送信できるようになり、ワンタッチでの会議参加が可能になります。</p>ActiveSync は、デバイス アカウントのカレンダーとメールを Surface Hub に同期するために使用されます。 デバイスで ActiveSync を使用できない場合は、ようこそ画面に会議が表示されず、会議への参加とホワイトボードのメール送信が有効になりません。 |
| Skype for Business (Lync Server 2013 以降または Skype for Business Online)  | Skype for Business は、ビデオ通話、インスタント メッセージング、画面の共有など、さまざまな会議機能に使用されます。|
| モバイル デバイス管理 (MDM) ソリューション (Microsoft Intune、Microsoft Endpoint Configuration Manager、またはサポートされているサード パーティの MDM プロバイダー) | リモートで同時に複数のデバイスに設定を適用し、アプリをインストールするには、MDM ソリューションをセットアップして、そのソリューションにデバイスを登録する必要があります。 詳しくは、「[MDM プロバイダーによる設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。 |
| Microsoft Operations Management Suite (OMS)   | OMS は、Surface Hub デバイスの正常性を監視するために使用されます。 詳しくは、「[Surface Hub の監視](monitor-surface-hub.md)」をご覧ください。 |
| ネットワークとインターネット アクセス   | Surface Hub が正常に機能するには、ワイヤード (有線) またはワイヤレス ネットワークへのアクセスが必要です。 一般的には、ワイヤード (有線) 接続をお勧めします。 802.1X 認証は、ワイヤード (有線) 接続とワイヤレス接続の両方をサポートします。</br></br></br>**802.1X 認証:** Surface Hub の Windows 10 Version 1703 では、ワイヤード (有線) およびワイヤレス接続用に 802.1X 認証が既定で有効になっています。 組織で 802.1X 認証を使用しない場合、構成の必要はなく、Surface Hub は引き続き通常どおりに機能します。 802.1X 認証を使用する場合は、Surface Hub に認証証明書がインストールされていることを確認する必要があります。 MDM で [ClientCertificateInstall CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/clientcertificateinstall-csp) を使用して、Surface Hub に証明書を配布することも、[プロビジョニング パッケージを作成](provisioning-packages-for-surface-hub.md)して、最初の実行時または設定アプリでインストールすることもできます。 証明書が Surface Hub に適用されると、802.1X 認証は自動的に機能し始めます。</br>**注:** Surface Hub で 802.1X ワイヤード (有線) 認証を有効にする方法の詳細については、「[802.1x ワイヤード (有線) 認証を有効にする](enable-8021x-wired-authentication.md)」をご覧ください。</br></br>**動的 IP:** 静的 IP を使うように Surface Hub を構成することはできません。 IP アドレスを割り当てるには DHCP を使う必要があります。</br></br>**プロキシ サーバー:** インターネット サービスに到達するためにプロキシ サーバーへの接続がトポロジによって求められる場合は、最初の実行時または [設定] でこの接続を構成できます。 プロキシの資格情報は、Surface Hub のセッション間で保存されるため、設定は一度だけで済みます。 |

さらに、Surface Hub では次のポートを開けておくことが求められます。
- HTTPS: 443
- HTTP: 80
- NTP: 123

Skype for Business で Surface Hub を使用している場合は、追加のポートを開く必要があります。 以下のガイダンスに従ってください。
- Skype for Business Online を使用する場合は、「Office [365 IP URL](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US)と IP アドレス範囲」を参照してください。
- Skype for Business Server を使用する場合は [、「Skype for Business Server: 内部サーバーのポートとプロトコル」を参照してください](https://docs.microsoft.com/SkypeForBusiness/plan-your-deployment/network-requirements/ports-and-protocols)。 
- If you use a hybrid of Skype for Business Online and Skype for Business Server, you need to open all documented ports from [Office 365 IP URLs and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US) and Skype for Business [Server: Ports and protocols for internal servers](https://docs.microsoft.com/SkypeForBusiness/plan-your-deployment/network-requirements/ports-and-protocols?toc=/SkypeForBusiness/toc.json&bc=/SkypeForBusiness/breadcrumb/toc.json).

Microsoft は、Surface Hub エクスペリエンスの改善に役立てるために、診断データを収集します。 以下のサイトを許可リストに追加してください。
- 診断データ クライアント エンドポイント: `https://vortex.data.microsoft.com/`
- 診断データ設定エンドポイント: `https://settings.data.microsoft.com/`

### プロキシの構成

ネットワーク上のコンピューターがインターネットに接続できないように社内で制限している場合、ビジネス向け Microsoft Store を利用するデバイスのために、いくつかの URL を利用可能な状態にしておく必要があります。 ビジネス向け Store のいくつかの機能には、Microsoft Store アプリと Microsoft Store Services が使われています。 ビジネス向け Store を使ってアプリを取得、インストール、更新するデバイスは、以下の URL にアクセスします。 プロキシ サーバーを使ってトラフィックをブロックしている場合、実際の構成でこれらの URL を許可する必要があります。

- login.live.com
- login.windows.net
- account.live.com
- clientconfig.passport.net
- windowsphone.com
- *.wns.windows.com
- *.microsoft.com
- www.msftncsi.com (Windows 10 バージョン 1607 より前の場合)
- www.msftconnecttest.com/connecttest.txt (Windows 10 バージョン 1607 以降の場合。www.msftncsi.com に置き換わる URL です)


## 他の管理者との連携

Surface Hub は、他の少数の製品やサービスと連携しています。 組織の規模によっては、お使いの環境に含まれるさまざまな製品をサポートする担当者が複数存在することがあります。 Exchange、Active Directory (または Azure Active Directory)、モバイル デバイス管理 (MDM)、およびネットワーク リソースの管理者を計画に含めて、Surface Hub の展開を準備してください。 


## デバイス アカウントの作成と検証

デバイス アカウントは、会議カレンダーの表示、Skype for Business 通話への参加、メールの送信、(オプションの) Exchange への認証などの目的で、Surface Hub で使用される Exchange リソース アカウントです。 詳しくは、「[デバイス アカウントの作成およびテスト](create-and-test-a-device-account-surface-hub.md)」をご覧ください。

デバイス アカウントを作成した後、正しくセットアップされていることを確認するには、Surface Hub デバイス アカウント検証 PowerShell スクリプトを実行します。 詳細については、このガイドの「[Surface Hub 用 PowerShell スクリプト](appendix-a-powershell-scripts-for-surface-hub.md)」をご覧ください。 

 

## 最初の実行プログラム用の準備 
[最初の実行プログラム](first-run-program-surface-hub.md)を開始する前に、あといくつかの点を考慮する必要があります。  

### プロビジョニング パッケージの作成 (省略可能)
プロビジョニング パッケージを使用して、証明書の追加、設定のカスタマイズ、アプリのインストールを行うことができます。 詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。 [プロビジョニング パッケージは、最初の実行でインストール](first-run-program-surface-hub.md#first-page)することができます。

### 管理者グループのセットアップ
デバイスで設定アプリを使用すると、すべての Surface Hub をローカルで構成できます。 承認されていないユーザーによって設定が変更されるのを防ぐため、設定アプリでは、アプリを起動する際に管理者の資格情報が求められます。 管理者グループを設定および管理する方法の詳細については、「[管理者グループの管理](admin-group-management-for-surface-hub.md)」をご覧ください。 [デバイスの管理者は最初の実行時にセットアップ](first-run-program-surface-hub.md#setup-admins)します。

### Surface Hub セットアップ ワークシートの確認と完了 (省略可能)
Surface Hub 用に最初の実行プログラムを実行する場合、指定する必要のある情報がいくつかあります。 セットアップ ワークシートを使用すると、指定する必要のある情報をまとめて、最初の実行プログラムを実行する場合に必要な環境固有の情報を一覧にすることができます。 詳しくは、「[セットアップのワークシート](setup-worksheet-surface-hub.md)」をご覧ください。


## このセクションの内容

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">トピック</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="create-and-test-a-device-account-surface-hub.md" data-raw-source="[Create and test a device account](create-and-test-a-device-account-surface-hub.md)">デバイス アカウントの作成およびテスト</a></p></td>
<td align="left"><p>このトピックでは、Skype と通信するために Surface Hub で使用するデバイス アカウントを作成およびテストする方法について説明します。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="provisioning-packages-for-certificates-surface-hub.md" data-raw-source="[Create provisioning packages](provisioning-packages-for-certificates-surface-hub.md)">プロビジョニング パッケージの作成</a></p></td>
<td align="left"><p>Windows 10 では、レジストリやコンテンツ サービス プラットフォーム (CSP) を使用する設定を、プロビジョニング パッケージによって構成することができます。 また、プロビジョニングを使用して、初回実行プロセスで証明書を追加することもできます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="admin-group-management-for-surface-hub.md" data-raw-source="[Admin group management](admin-group-management-for-surface-hub.md)">管理者グループの管理</a></p></td>
<td align="left"><p>デバイスで設定アプリを起動すると、すべての Surface Hub を個別に構成できます。 ただし、管理者でないユーザーによって設定が変更されるのを防ぐため、設定アプリでは、アプリを起動して設定を変更する際に管理者の資格情報が求められます。</p>
<p>設定アプリを開くには、ローカル管理者の資格情報が必要です。</p></td>
</tr>
</tbody>
</table>

## 詳細情報

- [ブログの投稿: Surface Hub と Skype for Business の信頼される側のドメインの一覧](https://blogs.technet.microsoft.com/y0av/2017/10/25/95/)
- [ブログの投稿: マルチドメイン環境での Surface Hub](https://blogs.technet.microsoft.com/y0av/2017/11/08/11/)
- [ブログの投稿: Surface Hub のプロキシの構成](https://blogs.technet.microsoft.com/y0av/2017/12/03/7/)

 

 





