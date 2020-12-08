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
ms.date: 12/07/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e171d7c2db8a0d69594ca8d5f3a54f33ecebc9ae
ms.sourcegitcommit: dc08a2096a1fe955eb67e736e2a4453f75e926be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "11196730"
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

1. Microsoft 365 管理センターで、[ **リソース** ] に移動し、[ **会議 & 室** ] を選択して、[ **+ Room**] を選択します。

2. デバイスアカウントの名前とメールアドレスを入力します。 残りの設定は既定の状態のままにしておきます。

   ![名前とメールアドレスを入力する](images/sh2-account2.png)

   ![その他の設定は既定の状態のままにします。](images/sh2-account3.png)

3. デバイスアカウントのパスワードを設定します。 パスワードを設定するには、[ **ユーザー** ]、[ **アクティブなユーザー**] の順に選択します。 新しく作成されたユーザーを検索して、パスワードを設定します。 [**このユーザーが最初にサインインしたときにパスワードの変更を行う**] オプションを選択して**いない**ことを確認します。

   ![デバイスアカウントのパスワードを設定する](images/sh2-account4.png)

4. Office 365 ライセンスを持つ会議室を割り当てます。 Skype for Business Online および Microsoft Teams のアカウントを自動的に有効にする新しいオプションとして、Office 365 **会議室** ライセンスを割り当てることをお勧めします。

   ![Office 365 ライセンスを割り当てる](images/sh2-account5.png)

### PowerShell を使用してセットアップを完了する

- **Microsoft Teams と Skype For business の予定表:** このアカウントの [**カレンダー自動処理**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) を設定します。

## PowerShell を使用してアカウントを作成する

Microsoft 管理センターポータルを使用する代わりに、PowerShell を使用してアカウントを作成することができます。

### Exchange Online PowerShell に接続する

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### メールボックスを作成する

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### 予定表の自動処理を設定する

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### メールアプリを使用する必要がある場合は、ActiveSync を有効にする

 既定の ActiveSync ポリシーは、解除された場合に有効になります。 または、新しいポリシーを作成して割り当てます。

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```
### Azure AD への接続

```powershell
Connect-AzureAD
```

### ライセンスを割り当てる

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### 利用可能なライセンスを確認する

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```