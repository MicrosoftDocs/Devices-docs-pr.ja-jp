---
title: Surface Hub でグローバル管理者以外のアカウントを構成する
description: この記事では、グローバル管理者以外のアカウントを構成して、2S Surface Hub管理Surface Hub説明します。
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
ms.openlocfilehash: 11170f6c202faef7aa3dddcb8aa8c6fa84bea80f
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643863"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a>Surface Hub でグローバル管理者以外のアカウントを構成する

Windows 10 Team 2020 Update では、Azure AD ドメインに参加している Surface Hub デバイス上の 設定 アプリの管理にアクセス許可を制限するグローバル管理者以外のアカウントを構成するためのサポートが追加されています。 これにより、管理者のアクセス許可の範囲をSurface Hub、Azure ドメイン全体で望ましくない可能性のある管理者アクセスをADできます。 開始する前に、アプリが Azure Surface Hubに参加し、Intune AD登録されている必要があります。 設定されていない場合は、Surface Hub をリセットし、Azure AD に参加するオプションを選択して、初めての既定の (OOBE) セットアップ プログラムを完了する必要があります。

## <a name="summary"></a>要約 

グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。 

1. [Microsoft Intune] で、管理者を管理するために指定された管理者を含むセキュリティ グループをSurface Hub。
2. PowerShell を使用AD Azure グループ SID を取得します。
3. Azure グループ SID を含む XML AD作成します。
4. グローバル管理者以外のセキュリティ グループSurface Hubデバイスを含むセキュリティ グループを作成します。
5. ユーザーのデバイスを含むセキュリティ グループを対象とするカスタム構成プロファイルSurface Hubします。 


## <a name="create-azure-ad-security-groups"></a>Azure ADセキュリティ グループを作成する

まず、管理者アカウントを含むセキュリティ グループを作成します。 次に、デバイス用に別のセキュリティ Surface Hub作成します。  

### <a name="create-security-group-for-admin-accounts"></a>管理者アカウントのセキュリティ グループを作成する

1. 管理センターから Intune にサインイン[Microsoft エンドポイント マネージャー、[](https://go.microsoft.com/fwlink/?linkid=2109431)グループの新**** しいグループ] を選択し、[グループ>の種類] で、[セキュリティ  >  ****] を**選択します。** 
2. グループ名を入力します 。たとえば、[**** ローカル管理者] Surface Hubなど) を入力し、[作成] を選択**します。** 

     ![ハブ管理者のセキュリティ グループを作成する](images/sh-create-sec-group.png)

3. グループを開き、[**メンバー]** を選択**** し、[メンバーの追加] を選択して、管理者アカウントとして指定する管理者アカウントを入力Surface Hub。 Intune でグループを作成する方法の詳細については、「グループを追加してユーザーとデバイスを整理  [する」を参照してください](/mem/intune/fundamentals/groups-add)。

### <a name="create-security-group-for-surface-hub-devices"></a>デバイスのセキュリティ グループSurface Hubする

1. 前の手順を繰り返して、ハブ デバイス用に別のセキュリティ グループを作成します。たとえば、デバイス**Surface Hubします**。 

     ![ハブ デバイスのセキュリティ グループを作成する](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>PowerShell を使用AD Azure グループ SID を取得する

1. 管理者特権 (管理者として**実行)** を使用して PowerShell を起動し、PowerShell スクリプトを実行するようにシステムが構成されていることを確認します。 詳細については、「実行ポリシー [について」を参照してください](/powershell/module/microsoft.powershell.core/about/about_execution_policies?)。 
2. [モジュールAzure PowerShellインストールします](/powershell/azure/install-az-ps)。
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
      <accessgroup desc = "S-1-5-32-544">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > 管理者アカウントにローカライズされた [名前を使用する必要がある場合があります](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx)。 XML ファイルから既定の Administrator メンバーを削除しない。

2. プレースホルダー SID (S-1-12-1 以降) を Azure AD **グループ SID** に置き換え、ファイルを XML として保存します。たとえば ** 、aad-local-admin.xml**。 

      > [!NOTE]
      > グループは SID を介して指定する必要があります。Azure ユーザーを直接追加する場合は、次の形式でユーザー プリンシパル名 (UPN) を指定して追加できます。 `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a>カスタム構成プロファイルの作成

1. [エンドポイント マネージャー] で、[**デバイス**  >  **構成プロファイル] [プロファイル**  >  **の作成] を選択します**。 
2. [プラットフォーム] で、[Windows 10**以降] を選択します。** [プロファイル] で、[カスタム] **を**選択し、[作成] を **選択します。**
3. 名前と説明を追加し、[次へ] を **選択します。**
4. [**構成設定**  >  **OMA-URI の設定] 設定、[追加**] を**選択します**。
5. [行の追加] ウィンドウで、名前を追加し     **、[OMA-URI]** の下に次の文字列を追加します。 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. [データ型] で[ **文字列 XML]** を選択し、前の手順で作成した XML ファイルを参照して開きます。 

     ![ローカル管理者 xml 構成ファイルのアップロード](images/sh-local-admin-config.png)

7. **[保存]** をクリックします。
8. [グループ**を選択して含める]** をクリックし、前に作成したセキュリティ グループ[(Surface Hub](#create-security-group-for-surface-hub-devices)**選択します**)。 **[次へ]** をクリックします。
9. [適用ルール] で、必要に応じてルールを追加します。 それ以外の場合は、[ **次へ] を選択** し、[作成] を **選択します**。

OMA-URI 文字列を使用したカスタム構成プロファイルの詳細については、「Intune のデバイスでカスタム設定を使用Windows 10[を参照してください](/mem/intune/configuration/custom-settings-windows-10)。


## <a name="non-global-admins-managing-surface-hub"></a>管理者を管理するグローバルSurface Hub

ローカル管理者セキュリティ**グループSurface Hubメンバー**は、設定の管理と管理で 設定 アプリSurface Hubサインインできます。

> [!IMPORTANT]
> グローバル管理者のアプリへの既定のアクセス設定 (この新しいセキュリティ グループのメンバーである場合を除き) は削除されます。
