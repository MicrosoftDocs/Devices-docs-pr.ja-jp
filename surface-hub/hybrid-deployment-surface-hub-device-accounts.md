---
title: ハイブリッド展開 (Surface Hub)
description: ハイブリッド展開では、Microsoft Surface Hub のデバイス アカウントを設定するには特別な手順が必要です。
ms.assetid: 7BFBB7BE-F587-422E-9CE4-C9DDF829E4F1
ms.reviewer: ''
manager: laurawi
keywords: ハイブリッド展開, Surface Hub のデバイス アカウント, 社内でホストされている Exchange, オンラインでホストされている Exchange
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/30/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7444c3f31f7a144200a0b8b89cfa509ef7a7afc4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836205"
---
# ハイブリッド展開 (Surface Hub)

ハイブリッド展開では、Microsoft Surface Hub のデバイス アカウントを設定するには特別な手順が必要です。 組織に社内でホストされているサービスとオンラインでホストされているサービスが混在しているハイブリッド展開を使っている場合、各サービスがホストされている場所によって構成が異なります。 このトピックでは、[オンプレミスでホストされている Exchange](#exchange-on-premises)、[オンラインでホストされている Exchange](#exchange-online)、Skype for Business オンプレミス、Skype for Business Online、および Skype for Business ハイブリッドを対象としたハイブリッド展開について説明します。 この種類の展開には非常に多くのバリエーションがあるため、すべてのバリエーションについて詳しい手順を示すことはできません。 次の手順は、多くの構成に利用できます。 手順が実際のセットアップに適していない場合は、PowerShell の使用をお勧めします (「[付録: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)」をご覧ください)。PowerShell を使用して、ここでの説明と同じ結果を得ることや、他の展開オプションを使用することができます。 その後、提供されている PowerShell スクリプトを使って Surface Hub のセットアップを検証する必要があります  (「[アカウント検証スクリプト](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts)」をご覧ください)。

> [!NOTE]
> Exchange ハイブリッド環境では、 [exchange on-premises](#exchange-on-premises)の手順に従います。 Exchange オブジェクトを Office 365 に移動するには、 [MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps)コマンドレットを使用します。

## Exchange On-Premises

Exchange On-Premises を使用している場合は、次の手順を使用します。

1. この手順では、AD 管理ツールを使ってオンプレミス ドメイン アカウントのメール アドレスを追加します。 このアカウントは、Office 365 と同期されます。

- **Active Directory ユーザーとコンピューター** AD ツールで、Surface Hub アカウントの作成先となるフォルダーまたは組織単位を右クリックし、**[新規作成]**、**[ユーザー]** の順にクリックします。
- 前のコマンドレットの表示名を **[フル ネーム]** ボックスに入力し、エイリアスを **[ユーザー ログオン名]** ボックスに入力します。 **[次へ]** をクリックします。<p>

![Active Directory で新しいユーザーを作成するための [新しいオブジェクト] ダイアログ ボックス。](images/hybriddeployment-01a.png)

- このアカウントのパスワードを入力します。 確認用に再入力する必要があります。 必ず、**[パスワードを無期限にする]** チェック ボックスだけをオンにします。

> **重要** **[パスワードを無期限にする]** をオンにすることは、Surface Hub で Skype for Business を使用するための要件です。 ドメイン ルールによっては、無期限のパスワードが禁止されています。 その場合は、Surface Hub デバイス アカウントごとに例外を作成する必要があります。

![パスワードのダイアログ ボックスを示す画像。](images/hybriddeployment-02a.png)

-   **[完了]** をクリックしてアカウントを作成します。

![新しいユーザーのアカウント名、ログオン名、およびパスワード オプションが表示された画像。](images/hybriddeployment-03a.png)

2. リモート メールボックスを有効にします。

オンプレミスの Exchange 管理シェルを管理者のアクセス許可で開き、次のコマンドレットを実行します。

```PowerShell
Enable-RemoteMailbox 'HUB01@contoso.com' -RemoteRoutingAddress 'HUB01@contoso.com' -Room
```

> [!NOTE]
> このコマンドレットを実行するオンプレミスの Exchange 環境がない場合は、アカウントの Active Directory オブジェクトに直接同じ変更を行うことができます。
>
> msExchRemoteRecipientType = 33
>
> msExchRecipientDisplayType = -2147481850
>
> msExchRecipientTypeDetails = 8589934592

3. アカウントを作成したら、ディレクトリ同期を実行します。 完了したら、Microsoft 365 管理センターの [ユーザー] ページに移動し、前の手順で作成したアカウントがオンラインに統合されていることを確認します。

4. Microsoft Exchange Online に接続し、Office 365 のアカウントのプロパティをいくつか設定します。

PC でリモート PowerShell セッションを開始し、Microsoft Exchange に接続します。 関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。

以降の手順は、Office 365 テナントで実行します。

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri 'https://ps.outlook.com/powershell' -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

5. 新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使います。

メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。

Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。 このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。

互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。 ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

互換性のあるポリシーを取得したら、デバイスアカウントにポリシーを適用する必要があります。 

```PowerShell
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
```

6. Exchange プロパティを設定します。

会議エクスペリエンスを向上させるには、Exchange プロパティをデバイス アカウントに設定します。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse 'This is a Surface Hub room!'
```

7. Azure AD に接続します。

PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。 管理者特権の PowerShell プロンプトで、次のコマンドを実行します。

```PowerShell
Install-Module -Name AzureAD
```

一部のアカウント設定を適用するには、Azure AD に接続する必要があります。 次のコマンドレットを実行すると接続できます。

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. Office 365 のライセンスを割り当てます。

デバイス アカウントには、有効な Office 365 (O365) のライセンスが必要です。ライセンスがない場合、Exchange と Skype for Business を利用できません。 ライセンスがある場合は、利用場所をデバイス アカウントに割り当てる必要があります。これにより、アカウントで利用可能なライセンス SKU が決まります。

`Get-AzureADSubscribedSku` を使って、O365 テナントで利用可能な SKU の一覧を取得できます。

SKU の一覧を取得したら、`$License.SkuId` 変数に必要な SkuId を割り当てる必要があります。

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

次に、[Skype for Business Online](#skype-for-business-online)、[Skype for Business オンプレミス](#skype-for-business-on-premises)、または [Skype for Business ハイブリッド](#skype-for-business-hybrid)でデバイス アカウントを有効にします。

### Skype for Business Online

Skype for Business Online を有効にするには、テナント ユーザーが Exchange メールボックスを持っている必要があります (テナント内に 1 つ以上の Exchange メールボックスが必要です)。 次の表では、必要なプランや追加のサービスについて説明します。

| Skype ルーム システムのシナリオ | Office 365 Premium、Microsoft 365 アプリ (enterprise 向け)、または Skype for Business Standalone Plan 2 を使用している場合は、次のものが必要です。 | エンタープライズ ベースのプランを利用している場合に必要なもの: | Skype for Business Server 2015 (オンプレミスまたはハイブリッド) を使用している場合は、次のものが必要です。 |
| --- | --- | --- | --- |
| スケジュールされた会議に参加する | Skype for Business スタンドアロン プラン 1 | E1、3、4、または 5 | Skype for Business Server Standard の CAL |
| 臨時の会議を開始する | Skype for Business スタンドアロン プラン 2 | E 1、3、4、または 5 | Skype for Business Server Standard の CAL または Enterprise の CAL |
| アドホック会議を開始し、会議から電話番号にダイヤルアウトする | Skype for Business Standalone Plan 2 (電話会議あり)</br></br>**注** PSTN 従量課金はオプションです | 電話会議または E5 付きの E1 または E3| Skype for Business Server Standard の CAL または Enterprise の CAL |
| ルームに電話番号を提供して、ルームから電話をかけるまたは受ける、電話番号を使用してダイヤルイン会議に参加する | Skype for Business Standalone Plan 2 (電話システムと PSTN 音声通話プラン) | 電話システムと PSTN 音声通話プラン (E5) を使用した E1 または E3 | Skype for Business Server Standard の CAL または Plus の CAL |

次の表に、Office 365 のプランと Skype for Business のオプションの一覧を示します。

| Office 365 のプラン | Skype for Business | 電話システム | 電話会議 | 通話プラン |
| --- | --- | --- | --- | --- |
| Office 365 Business Essentials | 含まれる |  |  |  |
| Office 365 Business Premium | 含まれる |  |  |  |
| E1 | 含まれる | アドオン | アドオン | アドオン (電話システムアドオンが必要) |
| E3 | 含まれる | アドオン | アドオン | アドオン (電話システムアドオンが必要) |
| E5 | 含まれる | 含まれる | 含まれる | アドオン  |

1. まず PC で、Skype for Business Online 環境に対するリモート PowerShell セッションを作成します。

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool 'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。

```PowerShell
Get-CsOnlineUser -Identity ‘HUB01@contoso.com’| fl *registrarpool*
```

3. Skype for Business のライセンスを Surface Hub アカウントに割り当てます。

 ここまでの手順を完了して Skype for Business Online で Surface Hub アカウントを有効にしたら、Surface Hub にライセンスを割り当てる必要があります。 O365 管理ポータルを使用して、デバイスに Skype for Business Online (プラン 2) または Skype for Business Online (Plan 3) ライセンスを割り当てます。

- テナント管理者としてログインし、O365 管理ポータルを開いて、"管理者" アプリをクリックします。

- **[ユーザーとグループ]**、**[ユーザーの追加、パスワードのリセットなど]** の順にクリックします。

- Surface Hub アカウントをクリックし、次にペン アイコンをクリックして、アカウント情報を編集します。

- **[ライセンス]** をクリックします。

- [**ライセンスの割り当て**] で、ライセンスおよびエンタープライズボイスの要件に応じて、[Skype for Business (プラン 1)] または [Skype for Business (plan 2)] を選択します。 Surface Hub でエンタープライズボイスを使用する場合は、プラン2ライセンスを使用する必要があります。

- **[保存]** をクリックします。

> [!NOTE]
> これらのライセンスのいずれかの割り当てに必要なコマンドレットを実行するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールも使用できますが、ここでは説明しません。

検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。

### Skype for Business オンプレミス

コマンドレットを実行するには、いずれかの Skype フロントエンドに接続する必要があります。 Skype PowerShell を開き、以下を実行します。

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### Skype for Business ハイブリッド

組織で、[Skype for Business Server と Skype for Business Online 間のハイブリッド接続](https://technet.microsoft.com/library/jj205403.aspx)を設定している場合は、アカウントを作成するためのガイダンスは標準的な Surface Hub の展開とは異なります。

Surface Hub では種類が `meetingroom` の Skype アカウントが必要になりますが、一般ユーザーの場合は種類が user の Skype アカウントを使用します。 Skype サーバーがハイブリッド用に設定されていて、ローカル Skype サーバーのユーザーと Office 365 でホストされているユーザーが存在する場合、Surface Hub アカウントを作成しようとするといくつかの問題が発生する可能性があります。

Skype for Business Server 2015 ハイブリッド環境では、Skype for business Online で使用するすべてのユーザーは、まずオンプレミス展開で作成し、ユーザーアカウントが Active Directory ドメインサービスで作成されるようにする必要があります。 その後、ユーザーを Skype for Business Online に移行することができます。 オンプレミスからオンラインへのユーザーアカウントの移動は、 [move-csuser](https://technet.microsoft.com/library/gg398528.aspx)コマンドレットによって実行されます。 Csroom Room オブジェクトを移動するには、 [move-Csroom room](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396)コマンドレットを使います。

> [!NOTE]
> 6.0.9319.281 のムーブルームコマンドレットを使用するには、 [Skype For Business server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)または[Lync server 2013 の2017年7月の累積更新プログラム 5.0.8308.992](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)の2017年5月の累積更新プログラムをインストールしている必要があります。


## Exchange Online

Exchange Online を使用している場合は、次の手順を使用します。

1. Office 365 のメール アカウントを作成します。

PC でリモート PowerShell セッションを開始し、Exchange に接続します。 関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/PowerShell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2. メールボックスを設定します。

セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。 これにより、アカウントを Surface Hub に対して認証できます。

既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。

```PowerShell
Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。

```PowerShell
New-Mailbox -MicrosoftOnlineServicesID 'HUB01@contoso.com' -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3. Exchange ActiveSync ポリシーを作成します。

メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。

Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。 正しく設定されていない場合、Surface Hub 上の Exchange サービス (メール、予定表、会議への参加) は有効になりません。

互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。 ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

互換性のあるポリシーを取得したら、デバイスアカウントにポリシーを適用する必要があります。 ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。 メールボックスを変換して種類をユーザーにし、ポリシーを適用して、変換でメールボックスに戻す必要があります。また、メールボックスを有効に戻してパスワードをもう一度設定することが必要になる場合もあります。

```PowerShell
Set-Mailbox 'HUB01@contoso.com' -Type Regular
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
Set-Mailbox 'HUB01@contoso.com' -Type Room
$credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
Set-Mailbox 'HUB01@contoso.com' -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
```

4. Exchange プロパティを設定します。

会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
```

5. オンプレミスのドメインアカウントのメールアドレスを追加します。

この手順では、AD 管理ツールを使ってオンプレミス ドメイン アカウントのメール アドレスを追加します。

- **Active Directory ユーザーとコンピューター** AD ツールで、Surface Hub アカウントの作成先となるフォルダーまたは組織単位を右クリックし、**[新規作成]**、**[ユーザー]** の順にクリックします。
- 前のコマンドレットの表示名を **[フル ネーム]** ボックスに入力し、エイリアスを **[ユーザー ログオン名]** ボックスに入力します。 **[次へ]** をクリックします。

![Active Directory で新しいユーザーを作成するための [新しいオブジェクト] ダイアログ ボックス。](images/hybriddeployment-01a.png)

- このアカウントのパスワードを入力します。 確認用に再入力する必要があります。 必ず、**[パスワードを無期限にする]** チェック ボックスだけをオンにします。

> [!IMPORTANT]
> [**パスワードを無期限**にする] は、Surface Hub 上の Skype for business の要件です。 ドメイン ルールによっては、無期限のパスワードが禁止されています。 その場合は、Surface Hub デバイス アカウントごとに例外を作成する必要があります。

![パスワードのダイアログ ボックスを示す画像。](images/hybriddeployment-02a.png)

- **[完了]** をクリックしてアカウントを作成します。

![新しいユーザーのアカウント名、ログオン名、およびパスワード オプションが表示された画像。](images/hybriddeployment-03a.png)

6. ディレクトリ同期を実行します。

アカウントを作成したら、ディレクトリ同期を実行します。 完了したら、ユーザー ページに移動して、前の手順で作成した 2 つのアカウントが結合していることを確かめます。

7. Azure AD に接続します。

PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。 管理者特権の PowerShell プロンプトで、次のコマンドを実行します。

```PowerShell
Install-Module -Name AzureAD
```

一部のアカウント設定を適用するには、Azure AD に接続する必要があります。 接続するには、次のコマンドレットを実行します。

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. Office 365 のライセンスを割り当てます。

デバイス アカウントには、有効な Office 365 (O365) のライセンスが必要です。ライセンスがない場合、Exchange と Skype for Business を利用できません。 ライセンスがある場合は、利用場所をデバイス アカウントに割り当てる必要があります。これにより、アカウントで利用可能なライセンス SKU が決まります。

次に、`Get-AzureADSubscribedSku` を使って、O365 テナントで利用可能な SKU の一覧を取得できます。

SKU の一覧を取得したら、`$License.SkuId` 変数に必要な SkuId を割り当てる必要があります。

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

次に、[Skype for Business Online](#skype-for-business-online)、[Skype for Business オンプレミス](#skype-for-business-on-premises)、または [Skype for Business ハイブリッド](#skype-for-business-hybrid)でデバイス アカウントを有効にします。

### Skype for Business Online

Skype for Business を有効にするには、環境が [Skype for Business Online の前提条件](#skype-for-business-online)を満たしている必要があります。

1. まず PC で、Skype for Business Online 環境に対するリモート PowerShell セッションを作成します。

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool  
'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

   環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。

```PowerShell
Get-CsOnlineUser -Identity 'HUB01@contoso.com'| fl *registrarpool*
```

10. Skype for Business のライセンスを Surface Hub アカウントに割り当てます。

ここまでの手順を完了して Skype for Business Online で Surface Hub アカウントを有効にしたら、Surface Hub にライセンスを割り当てる必要があります。 O365 管理ポータルを使用して、デバイスに Skype for Business Online (プラン 2) または Skype for Business Online (Plan 3) ライセンスを割り当てます。

- テナント管理者としてサインインし、O365 管理ポータルを開いて、"管理者" アプリをクリックします。

- **[ユーザーとグループ]**、**[ユーザーの追加、パスワードのリセットなど]** の順にクリックします。

- Surface Hub アカウントをクリックし、次にペン アイコンをクリックして、アカウント情報を編集します。

- **[ライセンス]** をクリックします。

- **[ライセンスの割り当て]** で、ライセンスとエンタープライズ VoIP の要件に応じて、Skype for Business (プラン 2) または Skype for Business (プラン 3) を選択します。 Surface Hub でエンタープライズ VoIP を使用する場合は、プラン 3 のライセンスを使う必要があります。

- **[保存]** をクリックします。

> [!NOTE]
> これらのライセンスのいずれかの割り当てに必要なコマンドレットを実行するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールも使用できますが、ここでは説明しません。

検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。

### Skype for Business オンプレミス

コマンドレットを実行するには、いずれかの Skype フロントエンドに接続する必要があります。 Skype PowerShell を開き、以下を実行します。

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### Skype for Business ハイブリッド

組織で、[Skype for Business Server と Skype for Business Online 間のハイブリッド接続](https://technet.microsoft.com/library/jj205403.aspx)を設定している場合は、アカウントを作成するためのガイダンスは標準的な Surface Hub の展開とは異なります。

Surface Hub では種類が *meetingroom* の Skype アカウントが必要になりますが、一般ユーザーの場合は種類が *user* の Skype アカウントを使用します。 Skype サーバーがハイブリッド用に設定されていて、ローカル Skype サーバーのユーザーと Office 365 でホストされているユーザーが存在する場合、Surface Hub アカウントを作成しようとするといくつかの問題が発生する可能性があります。

Skype for Business Server 2015 ハイブリッド環境では、Skype for business Online で使用するすべてのユーザーは、まずオンプレミス展開で作成し、ユーザーアカウントが Active Directory ドメインサービスで作成されるようにする必要があります。 その後、ユーザーを Skype for Business Online に移行することができます。 オンプレミスからオンラインへのユーザーアカウントの移動は、 [move-csuser](https://technet.microsoft.com/library/gg398528.aspx)コマンドレットによって実行されます。 Csroom Room オブジェクトを移動するには、 [move-Csroom room](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396)コマンドレットを使います。

> [!NOTE]
> 6.0.9319.281 のムーブルームコマンドレットを使用するには、 [Skype For Business server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)または[Lync server 2013 の2017年7月の累積更新プログラム 5.0.8308.992](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p)の2017年5月の累積更新プログラムをインストールしている必要があります。
