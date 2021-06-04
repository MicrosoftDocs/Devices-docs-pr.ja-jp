---
title: Surface Pro 3 向けの UEFI の高度なセキュリティ機能 (Surface)
description: この記事では、UEFI の更新プログラム v3.11.760.0 をインストールし、Surface Pro 3 デバイス向けの追加のセキュリティ オプションを有効にするように構成する方法について説明します。
ms.assetid: 90F790C0-E5FC-4482-AD71-60589E3C9C93
ms.reviewer: ''
manager: laurawi
keywords: セキュリティ, 機能, 構成, ハードウェア, デバイス, カスタム, スクリプト, 更新プログラム, security, features, configure, hardware, device, custom, script, update
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 6a5c53c3e161bd4c49069a0665896762ce587618
ms.sourcegitcommit: e9190a6fe68b8a7cd9b024aea4be9f885f0de388
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "11163181"
---
# Surface Pro 3 向けの UEFI の高度なセキュリティ機能


この記事では、UEFI の更新プログラム v3.11.760.0 をインストールし、Surface Pro 3 デバイス向けの追加のセキュリティ オプションを有効にするように構成する方法について説明します。

UEFI の更新プログラム v3.11.760.0 では、Surface デバイスのセキュリティをさらに細かく制御できるように、特定のハードウェア デバイスを無効にしたり、それらのデバイスからの起動を防止したりできる追加のセキュリティ オプションが提供されます。 UEFI の更新プログラムをデバイスにインストールした後、プログラムを手動で構成することも、スクリプトを実行して自動で構成することもできます。

##  <a name="manually-install-the-uefi-update"></a>UEFI の更新プログラムを手動でインストールする


Surface デバイスの高度なセキュリティ機能を構成する前に、まず UEFI の更新プログラム v3.11.760.0 をインストールする必要があります。 この更新プログラムを Windows Update から受け取った場合、プログラムは自動的にインストールされます。 Windows Update を使って自動的に更新されるように Windows を構成する方法について詳しくは、「[Windows での自動更新の構成方法および使用方法](https://support.microsoft.com/kb/306525)」をご覧ください。

Surface Pro 3 の UEFI を更新する場合は、Surface UEFI の更新プログラムを Surface Pro 3 ファームウェアおよびドライバー パックの一部としてダウンロードし、インストールできます。 これらのファームウェアおよびドライバー パックは、Microsoft ダウンロード センターの [Surface Pro 3 のページ](https://www.microsoft.com/download/details.aspx?id=38826)から入手できます。 ファームウェアおよびドライバー パックについて詳しくは、「[Surface デバイス用の最新のファームウェアとドライバーをダウンロードする](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices)」をご覧ください。 ファームウェアおよびドライバー パックは、両方自己完結型の Windows インストーラー (.msi) 形式とアーカイブ (.zip) 形式の両方で提供されています。 これら 2 種類の形式と、それぞれの形式を使用してドライバーを更新する方法について詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。

##  <a name="manually-configure-additional-security-settings"></a>追加のセキュリティ設定を手動で構成する


>[!NOTE]
>Surface デバイスのファームウェアのセットアップ画面に入るには、デバイスの電源を切り、**[音量を上げる]** ボタンを長押ししながら **[電源]** ボタンを押し、デバイスの起動が開始されたら **[音量を上げる]** ボタンを離します。

Surface デバイスに UEFI の更新プログラム v3.11.760.0 をインストールしたら、**[Advanced Device Security]** と呼ばれる追加の UEFI メニューを利用できるようになります。 このメニューをクリックすると、次のオプションが表示されます。

| オプション         | 説明                                                                                                                                                                          | 利用可能な設定 (太字は既定値) |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| ネットワーク ブート   | Surface デバイスをネットワークから起動する機能を有効または無効にします (PXE ブートとも呼ばれます)。                                                                            | **有効**、起動不可                   |
| 側面 USB       | Surface デバイスの側面にある USB ポートを有効または無効にします。 なお、この USB ポートを有効にすることはできますが、このポートからの起動は許可されません。                                                | **有効**、起動不可、無効         |
| ドッキング ポート   | Surface のドッキング ステーションのポートを有効または無効にします なお、ドッキング ポートを有効にすることはできますが、ドッキング ステーションの USB ポートまたはイーサネット ポートからの起動は禁止されます。 | **有効**、起動不可、無効         |
| 前面カメラ   | Surface デバイスの前面のカメラを有効または無効にします。                                                                                                                   | **有効**、無効                       |
| 背面カメラ    | Surface デバイスの背面のカメラを有効または無効にします。                                                                                                                    | **有効**、無効                       |
| オンボード オーディオ | Surface デバイスのオーディオを有効または無効にします。                                                                                                                                     | **有効**、無効                       |
| microSD        | Surface デバイスの microSD スロットを有効または無効にします。                                                                                                                          | **有効**、無効                       |
| WiFi           | Surface デバイスに組み込みの Wi-Fi トランシーバーを有効または無効にします。 これを無効にすると、Bluetooth も無効になります。                                                                              | **有効**、無効                       |
| Bluetooth      | Surface デバイスに組み込みの Bluetooth トランシーバーを有効または無効にします。                                                                                                        | **有効**、無効                       |

 

##  <a name="automate-additional-security-settings"></a>追加のセキュリティ設定を自動化する


管理者権限を持つ IT 担当者は、Microsoft ダウンロード センターから入手できる [Surface Pro 3 Firmware Tools (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) を利用して、UEFI 設定の構成を自動化することができます。 これらのツールを利用すると、すべてのカスタム アプリケーションやスクリプトから呼び出すことができる .NET アセンブリがインストールされます。

**前提条件**

-   以下に示すサンプル スクリプトでは、前に説明した拡張機能を利用しているため、管理されているデバイスにツールがインストールされていることを前提としています。
-   スクリプトは管理者権限で実行する必要があります。
-   サンプル スクリプトがデジタル署名されていない場合は、スクリプトを実行する前に Windows PowerShell コマンド [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) を呼び出す必要があります。

**サンプル スクリプト**

> [!NOTE]
> 以下のサンプル スクリプトで使用される UEFI パスワードはクリア テキストで表示されます。 スクリプトを保護された場所に保存し、管理された環境で実行することを強くお勧めします。


構成可能なオプションをすべて示します。

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
foreach ($uefiOption in $uefiOptions) 
{ 
    Write-Host "Name:" $uefiOption.Name 
    Write-Host " Description =" $uefiOption.Description 
    Write-Host " Current Value =" $uefiOption.CurrentValue 
    Write-Host " Default Value =" $uefiOption.DefaultValue 
    Write-Host " Proposed Value =" $uefiOption.ProposedValue 
     
    # This gives usage and validation information 
    Write-Host " Allowed Values =" $uefiOption.FriendlyRegEx 
    Write-Host " Regular Expression =" $uefiOption.RegEx 
     
    Write-Host 
}
```

UEFI パスワードを設定または変更します。

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
$Password = [Microsoft.Surface.FirmwareOption]::Find("Password") 
 
# Set New value to 12345 
$Password.ProposedValue = "12345"
```

提示された変更の状態を確認します。

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Check update status 
$updateStatus = [Microsoft.Surface.FirmwareOption]::UpdateStatus 
$updateIteration = [Microsoft.Surface.FirmwareOption]::UpdateIteration 
Write-Host "Last Update Status =" $updateStatus 
Write-Host "Last Update Iteration =" $updateIteration 
 
# Get the individual results for the last proposed update 
# If the device has never had an update attempt this will be an empty list 
$details = [Microsoft.Surface.FirmwareOption]::UpdateStatusDetails 
Write-Host $details.Count "Settings were proposed" 
if ($details.Count -gt 0) 
{ 
    Write-Host "Result Details" 
    foreach ($detail in $details.GetEnumerator()) 
    { 
        Write-Host " " $detail.Key "=" $detail.Value 
    } 
}
```

UEFI を既定値に戻します。

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
# Reset all options to the factory default 
foreach ($uefiOption in $uefiOptions) 
{ 
    $uefiOption.ProposedValue = $uefiOption.DefaultValue 
}
```

状態コードの解釈

-   00 - 提示された更新が成功しました。
-   02 - 提示された値の 1 つが無効な値でした。
-   03 - 提示された値セットの 1 つが認識されませんでした。
-   0F - ロック解除パスワードが現在設定されているパスワードと一致しませんでした。

 
