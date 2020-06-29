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
# <span data-ttu-id="52d66-104">PowerShell を使用して Surface Hub 2S オンプレミスのアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="52d66-104">Configure Surface Hub 2S on-premises accounts with PowerShell</span></span>

## <span data-ttu-id="52d66-105">Exchange Server PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="52d66-105">Connect to Exchange Server PowerShell</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52d66-106">これらのコマンドレットの一部では、オンプレミスの Exchange サーバーのクライアントアクセスサービスの完全修飾ドメイン名 (FQDN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="52d66-106">You'll need the Fully Qualified Domain Name (FQDN) for the Client Access service of the on-premises Exchange server for some of these cmdlets.</span></span>

```PowerShell
$ExchServer = Read-Host "Please Enter the FQDN of your Exchange Server"
$ExchSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://$ExchServer/PowerShell/ -Authentication Kerberos -Credential (Get-Credential)
Import-PSSession $ExchSession
```

## <span data-ttu-id="52d66-107">デバイスアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="52d66-107">Create the device account</span></span>

```PowerShell
New-Mailbox -UserPrincipalName Hub01@contoso.com -Alias Hub01 -Name "Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

## <span data-ttu-id="52d66-108">カレンダーの自動処理を設定する</span><span class="sxs-lookup"><span data-stu-id="52d66-108">Set automatic calendar processing</span></span>

```PowerShell
Set-CalendarProcessing -Identity "HUB01@contoso.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

## <span data-ttu-id="52d66-109">Skype for Business オブジェクトを有効にする</span><span class="sxs-lookup"><span data-stu-id="52d66-109">Enable the Skype for Business object</span></span>

> [!NOTE]
> <span data-ttu-id="52d66-110">Skype for Business レジストラープールの FQDN を知っていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="52d66-110">It is important that you know the FQDN of the Skype for Business Registrar Pool.</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity Contoso\HUB01 -SipAddressType emailaddress -RegistrarPool SfbIEFE01.contoso.local
```

## <span data-ttu-id="52d66-111">モバイルデバイスメールボックスポリシー</span><span class="sxs-lookup"><span data-stu-id="52d66-111">Mobile Device Mailbox Policy</span></span>

<span data-ttu-id="52d66-112">Surface Hub がオンラインまたはオンプレミス環境に接続できるように、モバイルデバイスメールボックスポリシー (ActiveSync ポリシーとも呼ばれます) を作成する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="52d66-112">You may need to create a Mobile Device Mailbox Policy (also known as ActiveSync Policy) to allow your Surface Hub to connect to your online or on-premises environment.</span></span>

## <span data-ttu-id="52d66-113">Surface Hub モバイルデバイスメールボックスポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="52d66-113">Create a Surface Hub mobile device mailbox policy</span></span>

```PowerShell
New-MobileDeviceMailboxPolicy -Name “Surface Hubs” -PasswordEnabled $false
```

## <span data-ttu-id="52d66-114">追加設定</span><span class="sxs-lookup"><span data-stu-id="52d66-114">Additional settings</span></span>

<span data-ttu-id="52d66-115">ユーザーが会議を Skype for Business または Teams 会議にすることを忘れないように、メールヒントを Surface Hub ルームに追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52d66-115">It is recommended to add a MailTip to Surface Hub rooms so users remember to make the meeting a Skype for Business or Teams meeting:</span></span>

```PowerShell
Set-Mailbox "Surface Hub 2S" -MailTip "This is a Surface Hub room. Please make sure this is a Microsoft Teams meeting."
```
