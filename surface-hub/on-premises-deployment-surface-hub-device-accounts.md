---
title: 単一フォレスト環境でのオンプレミス展開 (Surface Hub)
description: このトピックでは、単一フォレスト環境のオンプレミス展開を使っている場合に、Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。
ms.assetid: 80E12195-A65B-42D1-8B84-ECC3FCBAAFC6
ms.reviewer: ''
manager: laurawi
keywords: 単一フォレスト展開, オンプレミス展開, デバイス アカウント, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.localizationpriority: medium
ms.openlocfilehash: 37b157268769ddcdeaef67b7e19cc7260cd392b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836166"
---
# 単一フォレスト環境での Surface Hub のオンプレミス展開


このトピックでは、単一フォレスト環境のオンプレミス展開を使っている場合に、Microsoft Surface Hub のデバイス アカウントを追加する方法について説明します。

Microsoft Exchange 2013 以降と Skype for Business 2013 以降を搭載した単一フォレスト環境のオンプレミス展開を使っている場合は、[提供されている PowerShell スクリプトを使用](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts)してデバイス アカウントを作成できます。 複数フォレスト展開を使っている場合は、「[複数フォレスト環境での Surface Hub のオンプレミス展開](on-premises-deployment-surface-hub-multi-forest.md)」をご覧ください。

1. PC でリモート PowerShell セッションを開始し、Exchange に接続します。

   関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。

   ここで `$strExchangeServer` は Exchange サーバーの完全修飾ドメイン名 (FQDN) であり、 `$strLyncFQDN` は Skype for Business サーバーの FQDN です。

   ```PowerShell
   Set-ExecutionPolicy Unrestricted
   $org='contoso.microsoft.com'
   $cred=Get-Credential $admin@$org
   $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $cred -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
   $sessLync = New-PSSession -Credential $cred -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
   Import-PSSession $sessExchange
   Import-PSSession $sessLync
   ```

2. セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。 これにより、アカウントを Surface Hub に対して認証できます。

   既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。

   ```PowerShell
   New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
> [!IMPORTANT] 
> ActiveSync 仮想ディレクトリの基本認証は、Surface Hub で他の認証方法を使用して認証できないため、有効にする必要があります。

3. メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。

   Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。 このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。

   互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。 ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
   ```

   互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。 ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。 メールボックスを変換して種類をユーザーにし、ポリシーを適用して、変換でメールボックスに戻す必要があります。また、メールボックスを有効に戻してパスワードをもう一度設定することが必要になる場合もあります。

   ```PowerShell
   $acctUpn = Get-Mailbox -Identity "<mailbox identity>"
   $credNewAccount.Password = ConvertTo-SecureString -String <room mailbox password> -AsPlainText -Force
   Set-Mailbox $acctUpn -Type Regular
   Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy
   Set-Mailbox $acctUpn -Type Room
   Set-Mailbox $acctUpn -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```

4. ユーザーの会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

   ```PowerShell
   Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。 詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。

   ```PowerShell
   Set-AdUser $acctUpn -PasswordNeverExpires $true
   ```

6. Active Directory のアカウントが Surface Hub に認証されるように、アカウントを有効にします。

   ```PowerShell
   Set-AdUser $acctUpn -Enabled $true
   ```

7. Skype for Business Server プールの Surface Hub AD アカウントを有効にして、デバイス アカウントを Skype for Business に対して有効にします。

   ```PowerShell
   Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
    -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
    -Identity HUB01
   ```

   Surface Hub のセッション開始プロトコル (SIP) アドレスとドメイン コントローラーに加えて、専用の Skype for Business Server プール ID とユーザー ID を使用する必要があります。

8. 省略可能: アカウントのエンタープライズ VoIP を有効にして、Surface Hub での公衆交換電話網 (PSTN) 電話の発信と着信を許可することもできます。 エンタープライズ VoIP は Surface Hub の要件ではありませんが、Surface Hub クライアントで PSTN ダイヤル機能を使用する場合、実現方法は次のとおりです。

   ```PowerShell
   Set-CsMeetingRoom  -Identity HUB01 -DomainController DC-ND-001.contoso.com -LineURI "tel:+14255550555;ext=50555"  -EnterpriseVoiceEnabled $true
   ```

   この場合も、提供されているドメインコントローラーと電話番号の例を独自の情報で置き換える必要があります。 パラメーターの値 `$true` は変更されません。
    

 ## 匿名のメールと IM を無効にする




Surface Hub は、デバイスアカウントを使用して、メールおよびコラボレーションサービス (IM、ビデオ、音声) を提供します。 このデバイスアカウントは、メール、IM、通話の発信時に、送信元の身元 ("差出人") として使用されます。 このアカウントは個人の識別可能なユーザーからのものではないため、Surface Hub のデバイスアカウントから送信されたため、"匿名" と見なされます。  

Id が**SurfaceHubPolicy**の各会議室デバイスに、ユーザーごとのクライアントポリシーが割り当てられているものとします。 匿名のメールとメッセージングを無効にするには、次のコマンドを使用して、このクライアントポリシーに clientPolicyEntry を追加します。

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $false
$clientPolicy = Get-CsClientPolicy -Identity SurfaceHubPolicy
$clientPolicy.PolicyEntry.Add($policyEntry)
Set-CsClientPolicy -Instance $clientPolicy
```

ポリシーが設定されていることを確認するには、次の操作を行います。

```
Select-Object -InputObject $clientPolicy -Property PolicyEntry
```

出力は次のようになります。

```
PolicyEntry
-----------
{Name=AllowResourceAccountSendMessage;Value=False}
```
    
    
ポリシーエントリを変更するには、次の操作を行います。

```
$policyEntry =  New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Replace = $policyEntry}
``` 
    
ポリシーのエントリを削除するには、次の操作を行います。

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Remove = $policyEntry}
```

 





