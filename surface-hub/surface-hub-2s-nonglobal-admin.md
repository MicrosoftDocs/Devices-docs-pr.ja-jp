---
title: Surface Hub でグローバル管理者以外のアカウントを構成する
description: この記事では、Surface Hub と Surface Hub 2S を管理するために、グローバル以外の管理者アカウントを構成する方法について説明します。
keywords: Surface Hub、Surface Hub v1、Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/22/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: ceac8fc1b0e168b206d937197ef404990b8e40ae
ms.sourcegitcommit: 6c362c5d5f67449f1adf4618847093eaf6ad087b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "11442901"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a>Surface Hub でグローバル管理者以外のアカウントを構成する

Surface Hub v1 または Surface Hub 2S を Azure AD ドメインに参加する場合、Surface Hub の設定アプリの管理に対するアクセス許可を制限するグローバル管理者以外のアカウントを構成できます。 これにより、Surface Hub の管理者アクセス許可のみを対象範囲に設定し、Azure サーバードメイン全体で望ましくない可能性のある管理者アクセスをADできます。 開始する前に、Surface Hub が Azure サーバーに参加AD。 設定されていない場合は、Surface Hub をリセットし、初めての既定の (OOBE) セットアップ プログラムを完了し、Azure AD に参加するオプションを選択する必要があります。

## <a name="summary"></a>要約 

グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。 

1. Microsoft Intune で、Surface Hub の管理に指定された管理者を含むセキュリティ グループを作成します。
2. PowerShell を使用AD Azure グループ SID を取得します。
3. Azure グループ SID を含む XML AD作成します。
4. グローバル管理者以外のセキュリティ グループによって管理される Surface Hub デバイスを含むセキュリティ グループを作成します。
5. Surface Hub デバイスを含むセキュリティ グループを対象とするカスタム構成プロファイルを作成します。 


## <a name="create-azure-ad-security-groups"></a>Azure ADセキュリティ グループを作成する

まず、管理者アカウントを含むセキュリティ グループを作成します。 次に、Surface Hub デバイス用に別のセキュリティ グループを作成します。  

### <a name="create-security-group-for-admin-accounts"></a>管理者アカウントのセキュリティ グループを作成する

1. Microsoft Endpoint Manager 管理センターを介して**** Intune にサインインし、[[グループ](https://go.microsoft.com/fwlink/?linkid=2109431)の新しいグループ] を選択し、[グループ>の種類] で  >  ****、[セキュリティ] を**選択します。** 
2. グループ名 (Surface Hub ローカル管理者など) を入力 **し** 、[作成] を選択 **します。** 

     ![ハブ管理者のセキュリティ グループを作成する](images/sh-create-sec-group.png)

3. グループを開き、[**メンバー**] を選択**** し、[メンバーの追加] を選択して、Surface Hub でグローバル以外の管理者として指定する管理者アカウントを入力します。 Intune でグループを作成する方法の詳細については、「グループを追加してユーザーとデバイスを整理  [する」を参照してください](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)。

### <a name="create-security-group-for-surface-hub-devices"></a>Surface Hub デバイスのセキュリティ グループを作成する

1. 前の手順を繰り返して、ハブ デバイス用に別のセキュリティ グループを作成します。たとえば **、Surface Hub デバイス**。 

     ![ハブ デバイスのセキュリティ グループを作成する](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>PowerShell を使用AD Azure グループ SID を取得する

1. 管理者特権 (管理者として**実行)** を使用して PowerShell を起動し、PowerShell スクリプトを実行するようにシステムが構成されていることを確認します。 詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)。 
2. [Azure PowerShell モジュールをインストールします](https://docs.microsoft.com/powershell/azure/install-az-ps)。
3. Azure のテナントにサインインADします。

    ```powershell
    Connect-AzureAD
    ```

4. テナントにサインインしている場合は、次のコマンドレットを実行します。 「Azure グループのオブジェクト ID を入力してください」というメッセージが表示ADされます。

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. Intune で、前に作成したグループを選択し、次の図に示すようにオブジェクト ID をコピーします。 

     ![セキュリティ グループのオブジェクト ID のコピー](images/sh-objectid.png)

6. セキュリティ グループの SID を取得するには、次のコマンドレットを実行します。

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. オブジェクト ID を PowerShell コマンドレットに貼り付け **、Enter**キーを押して **、Azure** AD SID をテキスト エディターにコピーします。 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a>Azure グループ SID を含む XML ファイルAD作成する

1. 以下をテキスト エディターにコピーします。 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. プレースホルダー SID (S-1-12-1 以降) を Azure AD **グループ SID** に置き換え、ファイルを XML として保存します。たとえば ** 、aad-local-admin.xml**。 

## <a name="create-custom-configuration-profile"></a>カスタム構成プロファイルの作成

1. エンドポイント マネージャーで、[**** デバイス構成プロファイル  >  **プロファイルの作成**  >  **] を選択します**。 
2. [プラットフォーム] で **、[Windows 10 以降] を選択します。** [プロファイル] で、[カスタム] **を**選択し、[作成] を **選択します。**
3. 名前と説明を追加し、[次へ] を **選択します。**
4. [**構成設定**  >  **OMA-URI の設定] で、[** 追加] を**選択します**。
5. [行の追加] ウィンドウで、名前を追加し     **、[OMA-URI]** の下に次の文字列を追加します。 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. [データ型] で[ **文字列 XML]** を選択し、前の手順で作成した XML ファイルを参照して開きます。 

     ![ローカル管理者 xml 構成ファイルのアップロード](images/sh-local-admin-config.png)

7. **[保存]** をクリックします。
8. [グループ**の選択] をクリックして**含め、前に作成したセキュリティ[グループ](#create-security-group-for-surface-hub-devices)**(Surface Hub デバイス) を選択します**。 **[次へ]** をクリックします。
9. [適用ルール] で、必要に応じてルールを追加します。 それ以外の場合は、[ **次へ] を選択** し、[作成] を **選択します**。

OMA-URI 文字列を使用したカスタム構成プロファイルの詳細については、「Intune で [Windows 10](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)デバイスのカスタム設定を使用する」を参照してください。


## <a name="non-global-admins-managing-surface-hub"></a>Surface Hub を管理する非グローバル管理者

**Surface Hub ローカル管理者セキュリティ グループ**のメンバーは、Surface Hub の設定アプリにサインインし、設定を管理できます。
