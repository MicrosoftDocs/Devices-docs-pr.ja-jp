---
title: Surface Hub 2S でグローバル管理者以外のアカウントを構成する
description: この記事では、グローバル管理者以外のアカウントを構成して Surface Hub 2S を管理する方法について説明します。
keywords: Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/07/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: 647a7bf53e5ca8dc52ddec21ec8393cc574ee95a
ms.sourcegitcommit: 16cc2e8d9dfc5d6e061e0b5b6ddfcf35547643f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "11196816"
---
# Surface Hub 2S でグローバル管理者以外のアカウントを構成する

Surface Hub 2S を Azure AD ドメインに参加させるときは、Surface Hub 2S の設定アプリの管理に対するアクセス許可を制限する、グローバル管理者以外のアカウントを構成することができます。 これにより、Surface Hub 2S の管理権限のスコープのみが可能になり、不要な管理者が Azure AD ドメイン全体にアクセスできなくなります。 作業を始める前に、Surface Hub の2S が Azure AD に参加していることを確認してください。 それ以外の場合は、Surface Hub 2 をリセットし、初めての (OOBE) セットアッププログラムを実行して、Azure AD に参加するためのオプションを選択する必要があります。

## まとめ 

グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。 

1. Microsoft Intune で、Surface Hub 2S を管理するために指定された管理者を含むセキュリティグループを作成します。
2. PowerShell を使用して Azure AD グループ SID を取得します。
3. Azure AD グループ SID を含む XML ファイルを作成します。
4. 非グローバル管理者セキュリティグループによって管理される Surface Hub 2S デバイスを含むセキュリティグループを作成します。
5. Surface Hub 2S デバイスを含むセキュリティグループを対象としたカスタム構成プロファイルを作成します。 


## Azure AD セキュリティグループを作成する

最初に、管理者アカウントを含むセキュリティグループを作成します。 次に、Surface Hub デバイス用の別のセキュリティグループを作成します。  

### 管理者アカウントのセキュリティグループを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)を使用して Intune にサインインして、 **[グループの**  >  **新しいグループ**] を選択し > [グループの種類] で [セキュリティ] を選択し**ます。** 
2. グループ名を入力します。たとえば、 **Surface Hub のローカル管理者** で、[作成] を選び **ます。** 

     ![ハブ管理者のセキュリティグループを作成する](images/sh-create-sec-group.png)

3. グループを開き、[ **メンバー**] を選択し、[ **メンバーの追加** ] を選択して、Surface Hub 2s の非グローバル管理者として指定する管理者アカウントを入力します。 Intune でグループを作成する方法の詳細については、「  [ユーザーとデバイスを整理するためにグループを追加する](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)」を参照してください。

### Surface Hub 2S デバイスのセキュリティグループを作成する

1. ハブデバイス用の別のセキュリティグループを作成するには、前の手順を繰り返します。たとえば、 **Surface Hub デバイス**などです。 

     ![ハブデバイスのセキュリティグループを作成する](images/sh-create-sec-group-devices.png) 

## PowerShell を使用して Azure AD グループ SID を取得する

1. 昇格されたアカウントの特権 (**管理者として実行**) で powershell を起動し、システムが powershell スクリプトを実行するように構成されていることを確認します。 詳細については、「 [実行ポリシーについて](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)」を参照してください。 
2. [Azure PowerShell モジュールをインストール](https://docs.microsoft.com/powershell/azure/install-az-ps)します。
3. Azure AD テナントにサインインします。

    ```powershell
    Connect-AzureAD
    ```

4. テナントにサインインしたら、次の方法レットを実行します。 "Azure AD グループのオブジェクト ID を入力してください" というメッセージが表示されます。

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. [Intune] で、前に作成したグループを選択し、次の図に示すように、オブジェクト id をコピーします。 

     ![セキュリティグループのオブジェクト id をコピーする](images/sh-objectid.png)

6. セキュリティグループの SID を取得するには、次の方法レットを実行します。

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. オブジェクト id を PowerShell の入力レットに貼り付け、 **enter**キーを押してから、 **Azure AD グループの SID** をテキストエディターにコピーします。 

## Azure AD グループ SID を含む XML ファイルを作成する

1. テキストエディターに次の内容をコピーします。 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. プレースホルダー SID (S ~ 1-12-1 以降) を **AZURE AD グループ SID** に置き換えて、そのファイルを XML として保存します。たとえば、 **aad-local-admin.xml**とします。 

## カスタム構成プロファイルを作成する

1. エンドポイントマネージャーで、[**デバイス**  >  **構成プロファイル**の  >  **作成プロファイル**] を選択します。 
2. [プラットフォーム] で **、[Windows 10**以降] を選びます。 [プロファイル] で、[ **カスタム**] を選択し、[作成] を選択し **ます。**
3. 名前と説明を追加して、[次へ] を選び **ます。**
4. [**構成設定**  >  の**oma-uri 設定**] で [**追加**] を選びます。
5. [行の追加] ウィンドウで、名前と [     **oma-uri] URI**に次の文字列を追加します。 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. [データ型] で [ **文字列 XML** ] を選択し、前の手順で作成した xml ファイルを参照して開きます。 

     ![ローカル管理 xml 構成ファイルをアップロードする](images/sh-local-admin-config.png)

7. **[保存]** をクリックします。
8. [ **グループの選択] を** クリックして、 [前に作成したセキュリティグループ](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub デバイス**) を追加して選択します。 **[次へ]** をクリックします。
9. [適用規則] で、必要に応じてルールを追加します。 それ以外の場合は、[ **次へ** ] を選択し、[ **作成**] を選択します。

OMA-URI 文字列を使ったカスタム構成プロファイルの詳細については、「 [Intune で Windows 10 デバイスのカスタム設定を使用](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)する」を参照してください。


## Surface Hub 2S を管理するグローバル管理者以外

**Surface hub のローカル管理者**セキュリティグループのメンバーは、Surface hub 2S の設定アプリにサインインして、設定を管理できるようになりました。
