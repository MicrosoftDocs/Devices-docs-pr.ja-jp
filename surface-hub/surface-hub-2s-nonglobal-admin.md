---
title: Surface Hub 2S でグローバル管理者以外のアカウントを構成する
description: この記事では、Surface Hub 2S を管理するためにグローバル管理者以外のアカウントを構成する方法について説明します。
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
ms.openlocfilehash: e16e4f8bd4b2b253233fa9790987287cf17966c7
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385175"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub-2s"></a><span data-ttu-id="db9f8-104">Surface Hub 2S でグローバル管理者以外のアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="db9f8-104">Configure non Global admin accounts on Surface Hub 2S</span></span>

<span data-ttu-id="db9f8-105">Surface Hub 2S を Azure AD ドメインに参加する場合、Surface Hub 2S の設定アプリの管理に対するアクセス許可を制限するグローバル管理者以外のアカウントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-105">When you join Surface Hub 2S to an Azure AD domain, you can configure non Global admin accounts that limit permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="db9f8-106">これにより、Surface Hub 2S の管理者アクセス許可のみを対象範囲に設定し、Azure Hub ドメイン全体で望ましくない可能性のある管理者アクセスをADできます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-106">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> <span data-ttu-id="db9f8-107">開始する前に、Surface Hub 2S が Azure サーバーに参加AD。</span><span class="sxs-lookup"><span data-stu-id="db9f8-107">Before you begin, make sure your Surface Hub 2S is joined to Azure AD.</span></span> <span data-ttu-id="db9f8-108">設定されていない場合は、Surface Hub 2S をリセットし、初めての既定の (OOBE) セットアップ プログラムを完了し、Azure AD に参加するオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db9f8-108">If not, you will need to reset Surface Hub 2S and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <a name="summary"></a><span data-ttu-id="db9f8-109">要約</span><span class="sxs-lookup"><span data-stu-id="db9f8-109">Summary</span></span> 

<span data-ttu-id="db9f8-110">グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="db9f8-111">Microsoft Intune で、Surface Hub 2S の管理に指定された管理者を含むセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub 2S.</span></span>
2. <span data-ttu-id="db9f8-112">PowerShell を使用AD Azure グループ SID を取得します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="db9f8-113">Azure グループ SID を含む XML AD作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="db9f8-114">グローバル管理者以外のセキュリティ グループによって管理される Surface Hub 2S デバイスを含むセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-114">Create a Security Group containing the Surface Hub 2S devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="db9f8-115">Surface Hub 2S デバイスを含むセキュリティ グループを対象とするカスタム構成プロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub 2S devices.</span></span> 


## <a name="create-azure-ad-security-groups"></a><span data-ttu-id="db9f8-116">Azure ADセキュリティ グループを作成する</span><span class="sxs-lookup"><span data-stu-id="db9f8-116">Create Azure AD security groups</span></span>

<span data-ttu-id="db9f8-117">まず、管理者アカウントを含むセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="db9f8-118">次に、Surface Hub デバイス用に別のセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-118">Then create another security group for Surface Hub devices.</span></span>  

### <a name="create-security-group-for-admin-accounts"></a><span data-ttu-id="db9f8-119">管理者アカウントのセキュリティ グループを作成する</span><span class="sxs-lookup"><span data-stu-id="db9f8-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="db9f8-120">Microsoft Endpoint Manager 管理センターを介して\*\*\*\* Intune にサインインし、[[グループ](https://go.microsoft.com/fwlink/?linkid=2109431)の新しいグループ] を選択し、[グループ>の種類] で  >  \*\*\*\*、[セキュリティ] を**選択します。**</span><span class="sxs-lookup"><span data-stu-id="db9f8-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="db9f8-121">グループ名 (Surface Hub ローカル管理者など) を入力 **し** 、[作成] を選択 **します。**</span><span class="sxs-lookup"><span data-stu-id="db9f8-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![ハブ管理者のセキュリティ グループを作成する](images/sh-create-sec-group.png)

3. <span data-ttu-id="db9f8-123">グループを開き、[**メンバー**] を選択\*\*\*\* し、[メンバーの追加] を選択して、Surface Hub 2S でグローバル管理者以外として指定する管理者アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub 2S.</span></span> <span data-ttu-id="db9f8-124">Intune でグループを作成する方法の詳細については、「グループを追加してユーザーとデバイスを整理  [する」を参照してください](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)。</span><span class="sxs-lookup"><span data-stu-id="db9f8-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span></span>

### <a name="create-security-group-for-surface-hub-2s-devices"></a><span data-ttu-id="db9f8-125">Surface Hub 2S デバイスのセキュリティ グループを作成する</span><span class="sxs-lookup"><span data-stu-id="db9f8-125">Create security group for Surface Hub 2S devices</span></span>

1. <span data-ttu-id="db9f8-126">前の手順を繰り返して、ハブ デバイス用に別のセキュリティ グループを作成します。たとえば **、Surface Hub デバイス**。</span><span class="sxs-lookup"><span data-stu-id="db9f8-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![ハブ デバイスのセキュリティ グループを作成する](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a><span data-ttu-id="db9f8-128">PowerShell を使用AD Azure グループ SID を取得する</span><span class="sxs-lookup"><span data-stu-id="db9f8-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="db9f8-129">管理者特権 (管理者として**実行)** を使用して PowerShell を起動し、PowerShell スクリプトを実行するようにシステムが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="db9f8-130">詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)。</span><span class="sxs-lookup"><span data-stu-id="db9f8-130">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="db9f8-131">[Azure PowerShell モジュールをインストールします](https://docs.microsoft.com/powershell/azure/install-az-ps)。</span><span class="sxs-lookup"><span data-stu-id="db9f8-131">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="db9f8-132">Azure のテナントにサインインADします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="db9f8-133">テナントにサインインしている場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="db9f8-134">「Azure グループのオブジェクト ID を入力してください」というメッセージが表示ADされます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="db9f8-135">Intune で、前に作成したグループを選択し、次の図に示すようにオブジェクト ID をコピーします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![セキュリティ グループのオブジェクト ID のコピー](images/sh-objectid.png)

6. <span data-ttu-id="db9f8-137">セキュリティ グループの SID を取得するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="db9f8-138">オブジェクト ID を PowerShell コマンドレットに貼り付け **、Enter**キーを押して **、Azure** AD SID をテキスト エディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a><span data-ttu-id="db9f8-139">Azure グループ SID を含む XML ファイルAD作成する</span><span class="sxs-lookup"><span data-stu-id="db9f8-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="db9f8-140">以下をテキスト エディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. <span data-ttu-id="db9f8-141">プレースホルダー SID (S-1-12-1 以降) を Azure AD **グループ SID** に置き換え、ファイルを XML として保存します。たとえば \*\* 、aad-local-admin.xml\*\*。</span><span class="sxs-lookup"><span data-stu-id="db9f8-141">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

## <a name="create-custom-configuration-profile"></a><span data-ttu-id="db9f8-142">カスタム構成プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="db9f8-142">Create Custom configuration profile</span></span>

1. <span data-ttu-id="db9f8-143">エンドポイント マネージャーで、[\*\*\*\* デバイス構成プロファイル  >  **プロファイルの作成**  >  **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="db9f8-143">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="db9f8-144">[プラットフォーム] で **、[Windows 10 以降] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="db9f8-144">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="db9f8-145">[プロファイル] で、[カスタム] **を**選択し、[作成] を **選択します。**</span><span class="sxs-lookup"><span data-stu-id="db9f8-145">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="db9f8-146">名前と説明を追加し、[次へ] を **選択します。**</span><span class="sxs-lookup"><span data-stu-id="db9f8-146">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="db9f8-147">[**構成設定**  >  **OMA-URI の設定] で、[** 追加] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="db9f8-147">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="db9f8-148">[行の追加] ウィンドウで、名前を追加し     **、[OMA-URI]** の下に次の文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-148">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="db9f8-149">[データ型] で[ **文字列 XML]** を選択し、前の手順で作成した XML ファイルを参照して開きます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-149">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![ローカル管理者 xml 構成ファイルのアップロード](images/sh-local-admin-config.png)

7. <span data-ttu-id="db9f8-151">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-151">Click **Save**.</span></span>
8. <span data-ttu-id="db9f8-152">[グループ**の選択] をクリックして**含め、前に作成したセキュリティ[グループ](#create-security-group-for-surface-hub-2s-devices)**(Surface Hub デバイス) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="db9f8-152">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="db9f8-153">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db9f8-153">Click **Next.**</span></span>
9. <span data-ttu-id="db9f8-154">[適用ルール] で、必要に応じてルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="db9f8-154">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="db9f8-155">それ以外の場合は、[ **次へ] を選択** し、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="db9f8-155">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="db9f8-156">OMA-URI 文字列を使用したカスタム構成プロファイルの詳細については、「Intune で [Windows 10](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)デバイスのカスタム設定を使用する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db9f8-156">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <a name="non-global-admins-managing-surface-hub-2s"></a><span data-ttu-id="db9f8-157">Surface Hub 2S を管理する非グローバル管理者</span><span class="sxs-lookup"><span data-stu-id="db9f8-157">Non Global admins managing Surface Hub 2S</span></span>

<span data-ttu-id="db9f8-158">**Surface Hub ローカル管理者**セキュリティ グループのメンバーは、Surface Hub 2S の設定アプリにサインインし、設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="db9f8-158">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub 2S and manage settings.</span></span>
