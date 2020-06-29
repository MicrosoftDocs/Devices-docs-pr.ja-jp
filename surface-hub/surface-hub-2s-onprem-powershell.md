---
title: PowerShell を使用して Surface Hub 2S オンプレミスのアカウントを構成する
description: PowerShell を使用して Surface Hub のオンプレミスアカウントを構成する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 6832f4e4b5bc307746ec5838c0f80d043a22021a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836645"
---
# PowerShell を使用して Surface Hub 2S オンプレミスのアカウントを構成する

## Exchange Server PowerShell に接続する

> [!IMPORTANT]
> これらのコマンドレットの一部では、オンプレミスの Exchange サーバーのクライアントアクセスサービスの完全修飾ドメイン名 (FQDN) が必要です。

```PowerShell
$ExchServer = Read-Host "Please Enter the FQDN of your Exchange Server"
$ExchSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://$ExchServer/PowerShell/ -Authentication Kerberos -Credential (Get-Credential)
Import-PSSession $ExchSession
```

## デバイスアカウントを作成する

```PowerShell
New-Mailbox -UserPrincipalName Hub01@contoso.com -Alias Hub01 -Name "Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

## カレンダーの自動処理を設定する

```PowerShell
Set-CalendarProcessing -Identity "HUB01@contoso.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

## Skype for Business オブジェクトを有効にする

> [!NOTE]
> Skype for Business レジストラープールの FQDN を知っていることが重要です。

```PowerShell
Enable-CsMeetingRoom -Identity Contoso\HUB01 -SipAddressType emailaddress -RegistrarPool SfbIEFE01.contoso.local
```

## モバイルデバイスメールボックスポリシー

Surface Hub がオンラインまたはオンプレミス環境に接続できるように、モバイルデバイスメールボックスポリシー (ActiveSync ポリシーとも呼ばれます) を作成する必要がある場合があります。

## Surface Hub モバイルデバイスメールボックスポリシーを作成する

```PowerShell
New-MobileDeviceMailboxPolicy -Name “Surface Hubs” -PasswordEnabled $false
```

## 追加設定

ユーザーが会議を Skype for Business または Teams 会議にすることを忘れないように、メールヒントを Surface Hub ルームに追加することをお勧めします。

```PowerShell
Set-Mailbox "Surface Hub 2S" -MailTip "This is a Surface Hub room. Please make sure this is a Microsoft Teams meeting."
```
