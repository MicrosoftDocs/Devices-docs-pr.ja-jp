---
title: Surface Hub 2S デバイス アカウントの作成
description: このページでは、Surface Hub 2S device アカウントを作成する手順について説明します。
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
ms.openlocfilehash: 6d8c41872481d86316d8985871fe74823e005ed8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836381"
---
# Surface Hub 2S デバイス アカウントの作成

Surface Hub デバイスアカウント (Room メールボックスとも呼ばれます) を作成すると、Surface Hub 2 で、Microsoft Teams または Skype for Business を使用して会議出席依頼を受信、承認、または拒否し、会議に参加することができます。 Box (OOBE) セットアップ中にデバイスアカウントを構成します。 必要に応じて、後で変更することができます (OOBE セットアップを開始する必要はありません)。

既定では無効になっている標準的な会議用メールボックスとは異なり、Surface Hub の 2S device アカウントを有効にして、Microsoft Teams と Skype for Business にサインインする必要があります。 Surface Hub 2S は Exchange ActiveSync に依存します。これには、デバイスアカウントに ActiveSync メールボックスポリシーが必要です。 Exchange Online に付属の既定の ActiveSync メールボックスポリシーを適用します。

Microsoft 365 管理センターを使用するか、PowerShell を使用して、アカウントを作成します。 Exchange Online PowerShell を使用して、次のような特定の機能を構成することができます。

- すべての Surface Hub デバイスアカウントの予定表処理
- スケジュール要求に対するユーザー設定の自動応答
- 既定の ActiveSync メールボックスポリシーが、他のユーザーまたは別のプロセスによって既に変更されている場合は、新しい ActiveSync メールボックスポリシーを作成して割り当てる必要があります。

> [!NOTE]  
> Surface Hub デバイスアカウントは、サードパーティフェデレーション Id プロバイダー (FIPs) をサポートしておらず、標準の Active Directory アカウントまたは Azure Active Directory アカウントである必要があります。

## Microsoft 365 管理センターを使用してアカウントを作成する

1. Microsoft 365 管理センターで、[**リソース**] に移動し、[**会議 & 室**] を選択して、[ **+ Room**] を選択します。

2. デバイスアカウントの名前とメールアドレスを入力します。 残りの設定は既定の状態のままにしておきます。

   ![名前とメールアドレスを入力する](images/sh2-account2.png)

   ![その他の設定は既定の状態のままにします。](images/sh2-account3.png)

3. デバイスアカウントのパスワードを設定します。 パスワードを設定するには、[**ユーザー** ]、[**アクティブなユーザー**] の順に選択します。 新しく作成されたユーザーを検索して、パスワードを設定します。 [**このユーザーが最初にサインインしたときにパスワードの変更を行う**] オプションを選択して**いない**ことを確認します。

   ![デバイスアカウントのパスワードを設定する](images/sh2-account4.png)

4. Office 365 ライセンスを持つ会議室を割り当てます。 Skype for Business Online および Microsoft Teams のアカウントを自動的に有効にする新しいオプションとして、Office 365**会議室**ライセンスを割り当てることをお勧めします。

   ![Office 365 ライセンスを割り当てる](images/sh2-account5.png)

### PowerShell を使用してセットアップを完了する

- **Skype For business:** Skype for Business のみ (オンプレミスまたはオンライン) の場合、Skype for business オブジェクトを有効にするには、[ **enable-Csroom room** ] を実行して、音声およびロビーホールドの会議室のプロンプトなどの機能を有効にします。

- **Microsoft Teams と Skype For business の予定表:** このアカウントの[**カレンダー自動処理**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing)を設定します。

## PowerShell を使用してアカウントを作成する

Microsoft 管理センターポータルを使用する代わりに、PowerShell を使用してアカウントを作成することができます。

### Exchange Online PowerShell に接続する

```powershell
$365Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential (Get-Credential) -Authentication Basic –AllowRedirection
$ImportResults = Import-PSSession $365Session
```

### 新しい会議室メールボックスを作成する

```powershell
New-Mailbox -MicrosoftOnlineServicesID account@YourDomain.com -Alias SurfaceHub2S -Name SurfaceHub2S -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString  -String "<Enter Strong Password>" -AsPlainText -Force)
```

### 予定表の自動処理を設定する

```powershell
Set-CalendarProcessing -Identity "account@YourDomain.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

### ライセンスを割り当てる

```powershell
Connect-MsolService
Set-Msoluser -UserPrincipalName account@YourDomain.com -UsageLocation IE
Set-MsolUserLicense -UserPrincipalName "account@YourDomain.com" -AddLicenses "contoso:MEETING_ROOM"
```

## PowerShell を使用して Skype for Business Online に接続する

### 前提条件をインストールする

- [Visual C++ 2017 再頒布可能](https://aka.ms/vs/15/release/vc_redist.x64.exe)
- [Skype for Business Online PowerShell モジュール](https://www.microsoft.com/download/confirmation.aspx?id=39366)

```powershell
Import-Module LyncOnlineConnector
$SfBSession = New-CsOnlineSession -Credential (Get-Credential)
Import-PSSession $SfBSession -AllowClobber

# Enable the Skype for Business meeting room
Enable-CsMeetingRoom -Identity account@YourDomain.com -RegistrarPool(Get-CsTenant).Registrarpool -SipAddressType EmailAddress
```
