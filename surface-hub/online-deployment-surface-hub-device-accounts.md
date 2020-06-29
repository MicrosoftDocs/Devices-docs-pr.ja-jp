---
title: Office 365 を使ったオンライン展開 (Surface Hub)
description: このトピックでは、純粋なオンライン展開がある場合に Microsoft Surface Hub のデバイス アカウントを追加する手順を示します。
ms.assetid: D325CA68-A03F-43DF-8520-EACF7C3EDEC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のデバイス アカウント, オンライン展開, device account for Surface Hub, online deployment
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/21/2018
ms.localizationpriority: medium
ms.openlocfilehash: b38b8eb0ef13c2e945d63821e6e246ac7a59b2d7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836133"
---
# Office 365 を使ったオンライン展開 (Surface Hub)


このトピックでは、純粋なオンライン展開がある場合に Microsoft Surface Hub のデバイス アカウントを追加する手順を示します。

純粋なオンライン (O365) 展開がある場合は、[提供されている PowerShell スクリプトを使用](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts)してデバイス アカウントを作成できます。 

1. PC でリモート PowerShell セッションを開始し、Exchange に接続します。

   関連付けられたコマンドレットを実行するための適切なアクセス許可が設定されていることを確認します。

   ```PowerShell
   Set-ExecutionPolicy RemoteSigned
   $org='contoso.microsoft.com'
   $cred=Get-Credential admin@$org
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```

2. セッションを確立したら、新しいメールボックスを作成して RoomMailboxAccount として有効にするか、既存の会議室メールボックスの設定を変更します。 これにより、アカウントを Surface Hub に対して認証できます。

   既存のリソース メールボックスを変更する場合は、次のコマンドレットを実行します。

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   新しいリソース メールボックスを作成する場合は、次のコマンドレットを実行します。

   ```PowerShell
   New-Mailbox -MicrosoftOnlineServicesID HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。

   Surface Hub は、 **PasswordEnabled** プロパティが False に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。 このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。

   互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します。このコマンドレットは、"Surface Hubs" というポリシーを作成します。 ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false -AllowNonProvisionableDevices $True
   ```

   互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。

   ```PowerShell
   Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.Id
   ```

4. 会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

   ```PowerShell
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. Azure AD に接続します。
    
   PowerShell バージョン 2 用の Azure AD モジュールをインストールする必要があります。 管理者特権の PowerShell プロンプトで次のコマンドを実行します。
    
   ```PowerShell
   Install-Module -Name AzureAD
   ```
   一部のアカウント設定を適用するには、Azure AD に接続する必要があります。 次のコマンドレットを実行すると接続できます。

   ```PowerShell
   Import-Module AzureAD
   Connect-AzureAD -Credential $cred
   ```

6. パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。 詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。

   ```PowerShell
   Set-AzureADUser -ObjectId "HUB01@contoso.com" -PasswordPolicies "DisablePasswordExpiration"
   ```

7. Surface Hub には、Skype for Business 機能のライセンスが必要です。 Skype for Business を有効にするには、環境が [Skype for Business Online の前提条件](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online)を満たしている必要があります。
   
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

8. デバイス アカウントを Skype for Business に対して有効にします。
   Skype for Business の PowerShell モジュールがインストールされていない場合は、[Windows PowerShell Module for Skype for Business Online をダウンロード](https://www.microsoft.com/download/details.aspx?id=39366)します。 

   - まず、PC でリモート PowerShell セッションを作成します。

     ```PowerShell
     Import-Module SkypeOnlineConnector  
     $cssess=New-CsOnlineSession -Credential $cred  
     Import-PSSession $cssess -AllowClobber
     ```

   - 次に、環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、このコマンドレット (<em>alice@contoso.com</em> など) を使って、既存の Skype for Business ユーザーから値を取得できます。

       ```PowerShell
       Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool
       ```
       または、次の変数を設定します。
        
       ```PowerShell
    $strRegistrarPool = Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool | out-string
    $strRegistrarPool = $strRegistrarPool.Substring($strRegistrarPool.IndexOf(':') + 2)
       ```
        
   - 次のコマンドレットを使って Surface Hub アカウントを有効にします。
      
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool yourRegistrarPool -SipAddressType EmailAddress
       ```
        
       または、上のコマンドレットで $strRegistarPool 変数を使います。
        
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool $strRegistrarPool -SipAddressType EmailAddress
       ```

検証するには、任意の Skype for Business クライアント (PC、Android など) を使ってこのアカウントにサインインできる必要があります。





