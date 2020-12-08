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
# <span data-ttu-id="42bc8-104">Surface Hub 2S でグローバル管理者以外のアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-104">Configure non Global admin accounts on Surface Hub 2S</span></span>

<span data-ttu-id="42bc8-105">Surface Hub 2S を Azure AD ドメインに参加させるときは、Surface Hub 2S の設定アプリの管理に対するアクセス許可を制限する、グローバル管理者以外のアカウントを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-105">When you join Surface Hub 2S to an Azure AD domain, you can configure non Global admin accounts that limit permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="42bc8-106">これにより、Surface Hub 2S の管理権限のスコープのみが可能になり、不要な管理者が Azure AD ドメイン全体にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="42bc8-106">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access an entire Azure AD domain.</span></span> <span data-ttu-id="42bc8-107">作業を始める前に、Surface Hub の2S が Azure AD に参加していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="42bc8-107">Before you begin, make sure your Surface Hub 2S is joined to Azure AD.</span></span> <span data-ttu-id="42bc8-108">それ以外の場合は、Surface Hub 2 をリセットし、初めての (OOBE) セットアッププログラムを実行して、Azure AD に参加するためのオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42bc8-108">If not, you will need to reset Surface Hub 2S and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <span data-ttu-id="42bc8-109">まとめ</span><span class="sxs-lookup"><span data-stu-id="42bc8-109">Summary</span></span> 

<span data-ttu-id="42bc8-110">グローバル管理者以外のアカウントを作成するプロセスには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="42bc8-111">Microsoft Intune で、Surface Hub 2S を管理するために指定された管理者を含むセキュリティグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub 2S.</span></span>
2. <span data-ttu-id="42bc8-112">PowerShell を使用して Azure AD グループ SID を取得します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="42bc8-113">Azure AD グループ SID を含む XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="42bc8-114">非グローバル管理者セキュリティグループによって管理される Surface Hub 2S デバイスを含むセキュリティグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-114">Create a Security Group containing the Surface Hub 2S devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="42bc8-115">Surface Hub 2S デバイスを含むセキュリティグループを対象としたカスタム構成プロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub 2S devices.</span></span> 


## <span data-ttu-id="42bc8-116">Azure AD セキュリティグループを作成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-116">Create Azure AD security groups</span></span>

<span data-ttu-id="42bc8-117">最初に、管理者アカウントを含むセキュリティグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="42bc8-118">次に、Surface Hub デバイス用の別のセキュリティグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-118">Then create another security group for Surface Hub devices.</span></span>  

### <span data-ttu-id="42bc8-119">管理者アカウントのセキュリティグループを作成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="42bc8-120">[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)を使用して Intune にサインインして、 **[グループの**  >  **新しいグループ**] を選択し > [グループの種類] で [セキュリティ] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="42bc8-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="42bc8-121">グループ名を入力します。たとえば、 **Surface Hub のローカル管理者** で、[作成] を選び **ます。**</span><span class="sxs-lookup"><span data-stu-id="42bc8-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![ハブ管理者のセキュリティグループを作成する](images/sh-create-sec-group.png)

3. <span data-ttu-id="42bc8-123">グループを開き、[ **メンバー**] を選択し、[ **メンバーの追加** ] を選択して、Surface Hub 2s の非グローバル管理者として指定する管理者アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub 2S.</span></span> <span data-ttu-id="42bc8-124">Intune でグループを作成する方法の詳細については、「  [ユーザーとデバイスを整理するためにグループを追加する](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42bc8-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span></span>

### <span data-ttu-id="42bc8-125">Surface Hub 2S デバイスのセキュリティグループを作成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-125">Create security group for Surface Hub 2S devices</span></span>

1. <span data-ttu-id="42bc8-126">ハブデバイス用の別のセキュリティグループを作成するには、前の手順を繰り返します。たとえば、 **Surface Hub デバイス**などです。</span><span class="sxs-lookup"><span data-stu-id="42bc8-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![ハブデバイスのセキュリティグループを作成する](images/sh-create-sec-group-devices.png) 

## <span data-ttu-id="42bc8-128">PowerShell を使用して Azure AD グループ SID を取得する</span><span class="sxs-lookup"><span data-stu-id="42bc8-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="42bc8-129">昇格されたアカウントの特権 (**管理者として実行**) で powershell を起動し、システムが powershell スクリプトを実行するように構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="42bc8-130">詳細については、「 [実行ポリシーについて](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42bc8-130">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="42bc8-131">[Azure PowerShell モジュールをインストール](https://docs.microsoft.com/powershell/azure/install-az-ps)します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-131">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="42bc8-132">Azure AD テナントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="42bc8-133">テナントにサインインしたら、次の方法レットを実行します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="42bc8-134">"Azure AD グループのオブジェクト ID を入力してください" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="42bc8-135">[Intune] で、前に作成したグループを選択し、次の図に示すように、オブジェクト id をコピーします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![セキュリティグループのオブジェクト id をコピーする](images/sh-objectid.png)

6. <span data-ttu-id="42bc8-137">セキュリティグループの SID を取得するには、次の方法レットを実行します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="42bc8-138">オブジェクト id を PowerShell の入力レットに貼り付け、 **enter**キーを押してから、 **Azure AD グループの SID** をテキストエディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <span data-ttu-id="42bc8-139">Azure AD グループ SID を含む XML ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="42bc8-140">テキストエディターに次の内容をコピーします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. <span data-ttu-id="42bc8-141">プレースホルダー SID (S ~ 1-12-1 以降) を **AZURE AD グループ SID** に置き換えて、そのファイルを XML として保存します。たとえば、 **aad-local-admin.xml**とします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-141">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

## <span data-ttu-id="42bc8-142">カスタム構成プロファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="42bc8-142">Create Custom configuration profile</span></span>

1. <span data-ttu-id="42bc8-143">エンドポイントマネージャーで、[**デバイス**  >  **構成プロファイル**の  >  **作成プロファイル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-143">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="42bc8-144">[プラットフォーム] で **、[Windows 10**以降] を選びます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-144">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="42bc8-145">[プロファイル] で、[ **カスタム**] を選択し、[作成] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="42bc8-145">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="42bc8-146">名前と説明を追加して、[次へ] を選び **ます。**</span><span class="sxs-lookup"><span data-stu-id="42bc8-146">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="42bc8-147">[**構成設定**  >  の**oma-uri 設定**] で [**追加**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-147">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="42bc8-148">[行の追加] ウィンドウで、名前と [     **oma-uri] URI**に次の文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-148">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="42bc8-149">[データ型] で [ **文字列 XML** ] を選択し、前の手順で作成した xml ファイルを参照して開きます。</span><span class="sxs-lookup"><span data-stu-id="42bc8-149">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![ローカル管理 xml 構成ファイルをアップロードする](images/sh-local-admin-config.png)

7. <span data-ttu-id="42bc8-151">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-151">Click **Save**.</span></span>
8. <span data-ttu-id="42bc8-152">[ **グループの選択] を** クリックして、 [前に作成したセキュリティグループ](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub デバイス**) を追加して選択します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-152">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="42bc8-153">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42bc8-153">Click **Next.**</span></span>
9. <span data-ttu-id="42bc8-154">[適用規則] で、必要に応じてルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-154">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="42bc8-155">それ以外の場合は、[ **次へ** ] を選択し、[ **作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="42bc8-155">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="42bc8-156">OMA-URI 文字列を使ったカスタム構成プロファイルの詳細については、「 [Intune で Windows 10 デバイスのカスタム設定を使用](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42bc8-156">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <span data-ttu-id="42bc8-157">Surface Hub 2S を管理するグローバル管理者以外</span><span class="sxs-lookup"><span data-stu-id="42bc8-157">Non Global admins managing Surface Hub 2S</span></span>

<span data-ttu-id="42bc8-158">**Surface hub のローカル管理者**セキュリティグループのメンバーは、Surface hub 2S の設定アプリにサインインして、設定を管理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="42bc8-158">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub 2S and manage settings.</span></span>
