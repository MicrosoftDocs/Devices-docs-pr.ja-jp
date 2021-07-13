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
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a><span data-ttu-id="6948e-104">Surface Hub でグローバル管理者以外のアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="6948e-104">Configure non Global admin accounts on Surface Hub</span></span>

<span data-ttu-id="6948e-105">Windows 10 Team 2020 Update では、Azure AD ドメインに参加している Surface Hub デバイス上の 設定 アプリの管理にアクセス許可を制限するグローバル管理者以外のアカウントを構成するためのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="6948e-105">The Windows 10 Team 2020 Update adds support for configuring non Global admin accounts that limit permissions to management of the Settings app on Surface Hub devices joined to an Azure AD domain.</span></span> <span data-ttu-id="6948e-106">これにより、管理者のアクセス許可の範囲をSurface Hub、Azure ドメイン全体で望ましくない可能性のある管理者アクセスをADできます。</span><span class="sxs-lookup"><span data-stu-id="6948e-106">This enables you to scope admin permissions for Surface Hub only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> <span data-ttu-id="6948e-107">開始する前に、アプリが Azure Surface Hubに参加し、Intune AD登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6948e-107">Before you begin, make sure your Surface Hub is joined to Azure AD and Intune auto-enrolled.</span></span> <span data-ttu-id="6948e-108">設定されていない場合は、Surface Hub をリセットし、Azure AD に参加するオプションを選択して、初めての既定の (OOBE) セットアップ プログラムを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6948e-108">If not, you will need to reset Surface Hub and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <a name="summary"></a><span data-ttu-id="6948e-109">要約</span><span class="sxs-lookup"><span data-stu-id="6948e-109">Summary</span></span> 

<span data-ttu-id="6948e-110">グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6948e-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="6948e-111">[Microsoft Intune] で、管理者を管理するために指定された管理者を含むセキュリティ グループをSurface Hub。</span><span class="sxs-lookup"><span data-stu-id="6948e-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub.</span></span>
2. <span data-ttu-id="6948e-112">PowerShell を使用AD Azure グループ SID を取得します。</span><span class="sxs-lookup"><span data-stu-id="6948e-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="6948e-113">Azure グループ SID を含む XML AD作成します。</span><span class="sxs-lookup"><span data-stu-id="6948e-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="6948e-114">グローバル管理者以外のセキュリティ グループSurface Hubデバイスを含むセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="6948e-114">Create a Security Group containing the Surface Hub devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="6948e-115">ユーザーのデバイスを含むセキュリティ グループを対象とするカスタム構成プロファイルSurface Hubします。</span><span class="sxs-lookup"><span data-stu-id="6948e-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub devices.</span></span> 


## <a name="create-azure-ad-security-groups"></a><span data-ttu-id="6948e-116">Azure ADセキュリティ グループを作成する</span><span class="sxs-lookup"><span data-stu-id="6948e-116">Create Azure AD security groups</span></span>

<span data-ttu-id="6948e-117">まず、管理者アカウントを含むセキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="6948e-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="6948e-118">次に、デバイス用に別のセキュリティ Surface Hub作成します。</span><span class="sxs-lookup"><span data-stu-id="6948e-118">Then create another security group for Surface Hub devices.</span></span>  

### <a name="create-security-group-for-admin-accounts"></a><span data-ttu-id="6948e-119">管理者アカウントのセキュリティ グループを作成する</span><span class="sxs-lookup"><span data-stu-id="6948e-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="6948e-120">管理センターから Intune にサインイン[Microsoft エンドポイント マネージャー、[](https://go.microsoft.com/fwlink/?linkid=2109431)グループの新\*\*\*\* しいグループ] を選択し、[グループ>の種類] で、[セキュリティ  >  \*\*\*\*] を**選択します。**</span><span class="sxs-lookup"><span data-stu-id="6948e-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="6948e-121">グループ名を入力します 。たとえば、[\*\*\*\* ローカル管理者] Surface Hubなど) を入力し、[作成] を選択**します。**</span><span class="sxs-lookup"><span data-stu-id="6948e-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![ハブ管理者のセキュリティ グループを作成する](images/sh-create-sec-group.png)

3. <span data-ttu-id="6948e-123">グループを開き、[**メンバー]** を選択\*\*\*\* し、[メンバーの追加] を選択して、管理者アカウントとして指定する管理者アカウントを入力Surface Hub。</span><span class="sxs-lookup"><span data-stu-id="6948e-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub.</span></span> <span data-ttu-id="6948e-124">Intune でグループを作成する方法の詳細については、「グループを追加してユーザーとデバイスを整理  [する」を参照してください](/mem/intune/fundamentals/groups-add)。</span><span class="sxs-lookup"><span data-stu-id="6948e-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](/mem/intune/fundamentals/groups-add).</span></span>

### <a name="create-security-group-for-surface-hub-devices"></a><span data-ttu-id="6948e-125">デバイスのセキュリティ グループSurface Hubする</span><span class="sxs-lookup"><span data-stu-id="6948e-125">Create security group for Surface Hub devices</span></span>

1. <span data-ttu-id="6948e-126">前の手順を繰り返して、ハブ デバイス用に別のセキュリティ グループを作成します。たとえば、デバイス**Surface Hubします**。</span><span class="sxs-lookup"><span data-stu-id="6948e-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![ハブ デバイスのセキュリティ グループを作成する](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a><span data-ttu-id="6948e-128">PowerShell を使用AD Azure グループ SID を取得する</span><span class="sxs-lookup"><span data-stu-id="6948e-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="6948e-129">管理者特権 (管理者として**実行)** を使用して PowerShell を起動し、PowerShell スクリプトを実行するようにシステムが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6948e-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="6948e-130">詳細については、「実行ポリシー [について」を参照してください](/powershell/module/microsoft.powershell.core/about/about_execution_policies?)。</span><span class="sxs-lookup"><span data-stu-id="6948e-130">To learn more, refer to [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="6948e-131">[モジュールAzure PowerShellインストールします](/powershell/azure/install-az-ps)。</span><span class="sxs-lookup"><span data-stu-id="6948e-131">[Install Azure PowerShell module](/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="6948e-132">Azure のテナントにサインインADします。</span><span class="sxs-lookup"><span data-stu-id="6948e-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="6948e-133">テナントにサインインしている場合は、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="6948e-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="6948e-134">「Azure グループのオブジェクト ID を入力してください」というメッセージが表示ADされます。</span><span class="sxs-lookup"><span data-stu-id="6948e-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="6948e-135">Intune で、前に作成したグループを選択し、次の図に示すようにオブジェクト ID をコピーします。</span><span class="sxs-lookup"><span data-stu-id="6948e-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![セキュリティ グループのオブジェクト ID のコピー](images/sh-objectid.png)

6. <span data-ttu-id="6948e-137">セキュリティ グループの SID を取得するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="6948e-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="6948e-138">オブジェクト ID を PowerShell コマンドレットに貼り付け **、Enter**キーを押して **、Azure** AD SID をテキスト エディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6948e-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a><span data-ttu-id="6948e-139">Azure グループ SID を含む XML ファイルAD作成する</span><span class="sxs-lookup"><span data-stu-id="6948e-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="6948e-140">以下をテキスト エディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6948e-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "S-1-5-32-544">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > <span data-ttu-id="6948e-141">管理者アカウントにローカライズされた [名前を使用する必要がある場合があります](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6948e-141">You may need to use the [localized name for the Administrator account](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx).</span></span> <span data-ttu-id="6948e-142">XML ファイルから既定の Administrator メンバーを削除しない。</span><span class="sxs-lookup"><span data-stu-id="6948e-142">Do not remove the default Administrator member from the XML file.</span></span>

2. <span data-ttu-id="6948e-143">プレースホルダー SID (S-1-12-1 以降) を Azure AD **グループ SID** に置き換え、ファイルを XML として保存します。たとえば \*\* 、aad-local-admin.xml\*\*。</span><span class="sxs-lookup"><span data-stu-id="6948e-143">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

      > [!NOTE]
      > <span data-ttu-id="6948e-144">グループは SID を介して指定する必要があります。Azure ユーザーを直接追加する場合は、次の形式でユーザー プリンシパル名 (UPN) を指定して追加できます。</span><span class="sxs-lookup"><span data-stu-id="6948e-144">While groups should be specified via their SID, if you would like to add Azure users directly, they can be added by specifying their User Principal Name (UPN) in this format:</span></span> `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a><span data-ttu-id="6948e-145">カスタム構成プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="6948e-145">Create Custom configuration profile</span></span>

1. <span data-ttu-id="6948e-146">[エンドポイント マネージャー] で、[**デバイス**  >  **構成プロファイル] [プロファイル**  >  **の作成] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6948e-146">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="6948e-147">[プラットフォーム] で、[Windows 10**以降] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="6948e-147">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="6948e-148">[プロファイル] で、[カスタム] **を**選択し、[作成] を **選択します。**</span><span class="sxs-lookup"><span data-stu-id="6948e-148">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="6948e-149">名前と説明を追加し、[次へ] を **選択します。**</span><span class="sxs-lookup"><span data-stu-id="6948e-149">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="6948e-150">[**構成設定**  >  **OMA-URI の設定] 設定、[追加**] を**選択します**。</span><span class="sxs-lookup"><span data-stu-id="6948e-150">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="6948e-151">[行の追加] ウィンドウで、名前を追加し     **、[OMA-URI]** の下に次の文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="6948e-151">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="6948e-152">[データ型] で[ **文字列 XML]** を選択し、前の手順で作成した XML ファイルを参照して開きます。</span><span class="sxs-lookup"><span data-stu-id="6948e-152">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![ローカル管理者 xml 構成ファイルのアップロード](images/sh-local-admin-config.png)

7. <span data-ttu-id="6948e-154">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6948e-154">Click **Save**.</span></span>
8. <span data-ttu-id="6948e-155">[グループ**を選択して含める]** をクリックし、前に作成したセキュリティ グループ[(Surface Hub](#create-security-group-for-surface-hub-devices)**選択します**)。</span><span class="sxs-lookup"><span data-stu-id="6948e-155">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="6948e-156">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6948e-156">Click **Next.**</span></span>
9. <span data-ttu-id="6948e-157">[適用ルール] で、必要に応じてルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="6948e-157">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="6948e-158">それ以外の場合は、[ **次へ] を選択** し、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="6948e-158">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="6948e-159">OMA-URI 文字列を使用したカスタム構成プロファイルの詳細については、「Intune のデバイスでカスタム設定を使用Windows 10[を参照してください](/mem/intune/configuration/custom-settings-windows-10)。</span><span class="sxs-lookup"><span data-stu-id="6948e-159">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <a name="non-global-admins-managing-surface-hub"></a><span data-ttu-id="6948e-160">管理者を管理するグローバルSurface Hub</span><span class="sxs-lookup"><span data-stu-id="6948e-160">Non Global admins managing Surface Hub</span></span>

<span data-ttu-id="6948e-161">ローカル管理者セキュリティ**グループSurface Hubメンバー**は、設定の管理と管理で 設定 アプリSurface Hubサインインできます。</span><span class="sxs-lookup"><span data-stu-id="6948e-161">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub and manage settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6948e-162">グローバル管理者のアプリへの既定のアクセス設定 (この新しいセキュリティ グループのメンバーである場合を除き) は削除されます。</span><span class="sxs-lookup"><span data-stu-id="6948e-162">The default access of global admins to the Settings app is removed (unless they are also members of this new security group).</span></span>
