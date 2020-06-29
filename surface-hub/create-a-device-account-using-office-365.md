---
title: UI を使用してデバイス アカウントを作成する (Surface Hub)
description: グラフィカル ユーザー インターフェイスを使用する場合は、Office 365 の UI または Exchange 管理センターを使って Microsoft Surface Hub のデバイス アカウントを作成できます。
ms.assetid: D11BCDC4-DABA-4B9A-9ECB-58E02CC8218C
ms.reviewer: ''
manager: laurawi
keywords: デバイスアカウント、Office 365 UI、Exchange 管理センター、Microsoft 365 管理センター、Skype for Business、モバイルデバイスメールボックスポリシーを作成する
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/04/2018
ms.localizationpriority: medium
ms.openlocfilehash: e1f82f084103d4eef942e812c5e4f0e8bf425def
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836742"
---
# <span data-ttu-id="30d3d-104">UI を使用してデバイス アカウントを作成する (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="30d3d-104">Create a device account using UI (Surface Hub)</span></span>


<span data-ttu-id="30d3d-105">グラフィカル ユーザー インターフェイスを使用する場合は、[Office 365 の UI](#create-device-acct-o365) または [Exchange 管理センター](#create-device-acct-eac)を使って Microsoft Surface Hub のデバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-105">If you prefer to use a graphical user interface, you can create a device account for your Microsoft Surface Hub with either the [Office 365 UI](#create-device-acct-o365) or the [Exchange Admin Center](#create-device-acct-eac).</span></span>

## <a href="" id="create-device-acct-o365"></a><span data-ttu-id="30d3d-106">Office 365 を使ったデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="30d3d-106">Create a device account using Office 365</span></span>


1.  <span data-ttu-id="30d3d-107">[Microsoft 365 管理センターでアカウントを作成](#create-device-acct-o365-admin-ctr)します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-107">[Create the account in the Microsoft 365 Admin Center](#create-device-acct-o365-admin-ctr).</span></span>
2.  <span data-ttu-id="30d3d-108">[Microsoft Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成](#create-device-acct-o365-mbx-policy)</span><span class="sxs-lookup"><span data-stu-id="30d3d-108">[Create a mobile device mailbox (ActiveSync) policy from the Microsoft Exchange Admin Center](#create-device-acct-o365-mbx-policy).</span></span>
3.  <span data-ttu-id="30d3d-109">[PowerShell の使用によるデバイス アカウント作成の完了](#create-device-acct-o365-complete-acct).</span><span class="sxs-lookup"><span data-stu-id="30d3d-109">[Use PowerShell to complete device account creation](#create-device-acct-o365-complete-acct).</span></span>
4.  <span data-ttu-id="30d3d-110">[PowerShell の使用によるアカウントの Exchange プロパティの構成](#create-device-acct-o365-configure-exch-prop)</span><span class="sxs-lookup"><span data-stu-id="30d3d-110">[Use PowerShell to configure Exchange properties of the account](#create-device-acct-o365-configure-exch-prop).</span></span>
5.  <span data-ttu-id="30d3d-111">[Skype for Business に対するアカウントの有効化](#create-device-acct-o365-skype-for-business)</span><span class="sxs-lookup"><span data-stu-id="30d3d-111">[Enable the account with Skype for Business](#create-device-acct-o365-skype-for-business).</span></span>

### <a href="" id="create-device-acct-o365-admin-ctr"></a><span data-ttu-id="30d3d-112">管理センターでアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="30d3d-112">Create the account in the admin center</span></span>

1.  <span data-ttu-id="30d3d-113">アクセスして、Office 365 にサインインします。https://portal.office.com</span><span class="sxs-lookup"><span data-stu-id="30d3d-113">Sign in to Office 365 by visiting https://portal.office.com</span></span>
2.  <span data-ttu-id="30d3d-114">Office 365 テナントの管理者資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-114">Provide the admin credentials for your Office 365 tenant.</span></span> <span data-ttu-id="30d3d-115">この操作を行うと、Microsoft 365 管理センターに移動します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-115">This will take you to your Microsoft 365 Admin Center.</span></span>

    ![Microsoft 365 管理センター](images/setupdeviceaccto365-02.png)

3. <span data-ttu-id="30d3d-117">管理センターで、左側のパネルにある [**リソース**] に移動し、[**ルーム & 備品**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-117">In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.</span></span>

    ![管理センターで & の会議室のオプション](images/room-equipment.png)

4. <span data-ttu-id="30d3d-119">**[追加]** をクリックして会議室アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-119">Click **Add** to create a new Room account.</span></span> <span data-ttu-id="30d3d-120">アカウントの表示名とメール アドレスを入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-120">Enter a display name and email address for the account, and then click **Add**.</span></span>

    ![新しい会議室アカウントの作成ウィンドウ](images/room-add.png)

5. <span data-ttu-id="30d3d-122">作成した会議室アカウントを [アクティブなユーザー] の一覧で選択します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-122">Select the Room account you just created in the Active Users list.</span></span> <span data-ttu-id="30d3d-123">右側のパネルに、アカウントのプロパティといくつかの省略可能なオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-123">In the right panel, you can see the account properties and several optional actions.</span></span> <span data-ttu-id="30d3d-124">**[パスワードのリセット]** をクリックしてパスワードを変更し、**[このユーザーが最初にサインインしたときに、パスワードの変更を行うようにする]** をオフにします (Surface Hub のサインイン フローではパスワードを変更できないため)。</span><span class="sxs-lookup"><span data-stu-id="30d3d-124">Click **Reset password** to change the password, and unselect **Make this user change their password when they first sign in**, because it is not possible to change the password from the Surface Hub sign-in flow.</span></span>

6. <span data-ttu-id="30d3d-125">**[割り当て済みのライセンス]** セクションの **[編集]** をクリックし、適切なライセンスの横に表示されているドロップダウン矢印をクリックして詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-125">In the **Assigned license** section, click **Edit**, and then click the dropdown arrow next to the appropriate license to expand the details.</span></span> <span data-ttu-id="30d3d-126">ユーザーの場所を選択し、ライセンスの一覧で、**[Skype for Business Online (プラン 2)]** をオンにして **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-126">Select a user location, and in the list of licenses, toggle on **Skype for Business Online (Plan 2)**, and then click **Save**.</span></span> <span data-ttu-id="30d3d-127">このライセンスは組織によって異なる場合があります (たとえば、プラン 2 の場合も プラン 3 の場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="30d3d-127">The license may vary depending on your organization (for example, you might have Plan 2 or Plan 3).</span></span>

### <a href="" id="create-device-acct-o365-mbx-policy"></a><span data-ttu-id="30d3d-128">Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="30d3d-128">Create a mobile device mailbox (ActiveSync) policy from the Exchange Admin Center</span></span>

1.  <span data-ttu-id="30d3d-129">管理センターの左側のパネルで、[**管理者**] をクリックし、[ **Exchange**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-129">In the admin center’s left panel, click **ADMIN**, and then click **Exchange**.</span></span>

    ![管理センター、exchange のアクティブユーザーを示しています。](images/setupdeviceaccto365-08.png)

2.  <span data-ttu-id="30d3d-131">ブラウザーの別のタブが開き、Exchange 管理センターが表示されます。ここで、Surface Hub のメールボックスの設定を作成して設定できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-131">This will open another tab on your browser to take you to the Exchange Admin Center, where you can create and set the Mailbox Setting for Surface Hub.</span></span>

    ![Exchange 管理センター。](images/setupdeviceaccto365-09.png)

3.  <span data-ttu-id="30d3d-133">モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-133">To create a Mobile Device Mailbox Policy, click **Mobile** from the left panel and then click **Mobile device mailbox policies**.</span></span> <span data-ttu-id="30d3d-134">Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-134">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="30d3d-135">それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-135">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Exchange 管理センター - モバイル デバイス メールボックス ポリシーの作成。](images/setupdeviceaccto365-10.png)

4.  <span data-ttu-id="30d3d-137">新しい Surface Hub のモバイル デバイス メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-137">To create a New Surface Hub mobile device mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="30d3d-138">名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-138">For the name, provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="30d3d-139">ポリシーに割り当てられたデバイスのパスワードがこのポリシーで要求されないようにします。そのため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-139">Make sure the policy does not require a password for the devices assigned to, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![新しいモバイル デバイス ポリシーを示す画像。](images/setupdeviceaccto365-11.png)

5.  <span data-ttu-id="30d3d-141">新しいモバイル デバイス メールボックス ポリシーを作成したら、**Exchange 管理センター**に戻ります。新しいポリシーが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-141">After you have created the new mobile device mailbox policy, go back to the **Exchange Admin Center** and you will see the new policy listed.</span></span>

    ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーの画像。](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a><span data-ttu-id="30d3d-143">PowerShell の使用によるデバイス アカウント作成の完了</span><span class="sxs-lookup"><span data-stu-id="30d3d-143">Use PowerShell to complete device account creation</span></span>

<span data-ttu-id="30d3d-144">ここからは、PowerShell を使って構成を設定し、アカウント作成処理を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-144">From here on, you'll need to finish the account creation process using PowerShell to set up some configuration.</span></span>

<span data-ttu-id="30d3d-145">これらの PowerShell スクリプトで使用されるコマンドレットを実行するには、次のツールを管理者用 PowerShell コンソールにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-145">In order to run cmdlets used by these PowerShell scripts, the following must be installed for the admin PowerShell console:</span></span>

-   [<span data-ttu-id="30d3d-146">IT プロフェッショナル向け Microsoft Online Service サインインアシスタントプロフェッショナル用 RTWHTTP://GO.MICROSOFT.COM/FWLINK/?LINKID=625123</span><span class="sxs-lookup"><span data-stu-id="30d3d-146">Microsoft Online Services Sign-In Assistant for IT Professionals RTW</span></span>](https://www.microsoft.com/download/details.aspx?id=41950)
-   [<span data-ttu-id="30d3d-147">Windows PowerShell 用 Microsoft Azure Active Directory モジュール</span><span class="sxs-lookup"><span data-stu-id="30d3d-147">Windows Azure Active Directory Module for Windows PowerShell</span></span>](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [<span data-ttu-id="30d3d-148">Windows PowerShell Module for Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="30d3d-148">Skype for Business Online, Windows PowerShell Module</span></span>](https://www.microsoft.com/download/details.aspx?id=39366)

<span data-ttu-id="30d3d-149">Powershell で次のモジュールをインストールする</span><span class="sxs-lookup"><span data-stu-id="30d3d-149">Install the following module in Powershell</span></span>
``` syntax
    install-module AzureAD
    Install-module MsOnline
```

### <span data-ttu-id="30d3d-150">オンライン サービスへの接続</span><span class="sxs-lookup"><span data-stu-id="30d3d-150">Connecting to online services</span></span>

1.  <span data-ttu-id="30d3d-151">管理者として Windows PowerShell を実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-151">Run Windows PowerShell as Administrator.</span></span>

    ![Windows PowerShell を起動し、管理者として実行する方法を示す画像。](images/setupdeviceaccto365-17.png)

2.  <span data-ttu-id="30d3d-153">Credentials オブジェクトを作成し、Skype for Business Online に接続している新しいセッションを作成します。次に、グローバルのテナント管理者アカウントを指定し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-153">Create a Credentials object, then create a new session that connects to Skype for Business Online, and provide the global tenant administrator account, then click **OK**.</span></span>

    ![Windows PowerShell 資格情報の要求の画像。](images/setupdeviceaccto365-18.png)

3.  <span data-ttu-id="30d3d-155">Microsoft Online Services に接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-155">To connect to Microsoft Online Services, run:</span></span>

    ``` syntax
    Connect-MsolService -Credential $Cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-19.png)

4.  <span data-ttu-id="30d3d-157">ここで、Skype for Business Online サービスに接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-157">Now to connect to Skype for Business Online Services, run:</span></span>

    ``` syntax
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-20.png)

5.  <span data-ttu-id="30d3d-159">最後に、Exchange Online サービスに接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-159">Finally, to connect to Exchange Online Services, run:</span></span>

    ``` syntax
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-21.png)

6.  <span data-ttu-id="30d3d-161">ここで、Skype for Business Online セッションと、前の手順で作成した Exchange Online セッションをインポートする必要があります。これにより、Exchange と Skype のコマンドをローカルで使用できるようにインポートします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-161">Now you have to import the Skype for Business Online Session and the Exchange Online session you have just created, which will import the Exchange and Skype Commands so you can use them locally.</span></span>

    ``` syntax
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    <span data-ttu-id="30d3d-162">この手順の完了には時間がかかることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-162">Note that this could take a while to complete.</span></span>

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-22.png)

7.  <span data-ttu-id="30d3d-164">オンライン サービスに接続したら、さらにいくつかのコマンドレットを実行して、このアカウントを Surface Hub デバイス アカウントとして構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-164">Once you’re connected to the online services you need to run a few more cmdlets to configure this account as a Surface Hub device account.</span></span>

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a><span data-ttu-id="30d3d-165">PowerShell の使用によるアカウントの Exchange プロパティの構成</span><span class="sxs-lookup"><span data-stu-id="30d3d-165">Use PowerShell to configure Exchange properties of the account</span></span>

<span data-ttu-id="30d3d-166">オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-166">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="30d3d-167">デバイス アカウントのメール アドレスには、次の用途があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-167">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="30d3d-168">メールボックスの種類を標準から会議室に変更する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-168">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="30d3d-169">パスワードを設定して、会議室メールボックスのアカウントを有効にする。</span><span class="sxs-lookup"><span data-stu-id="30d3d-169">Set the password and enable the room mailbox account</span></span>
-   <span data-ttu-id="30d3d-170">さまざまな Exchange プロパティを変更する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-170">Change various Exchange properties</span></span>
-   <span data-ttu-id="30d3d-171">ユーザー アカウントのパスワードを無期限に設定する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-171">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="30d3d-172">アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-172">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="30d3d-173">値を格納するには、メールボックスからその値を取得します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-173">To store the value get it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="30d3d-174">値を出力します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-174">Print the value:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="30d3d-175">正しいメール アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-175">You will see the correct email address.</span></span>

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-23.png)

2. <span data-ttu-id="30d3d-177">次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-177">Run the following cmdlet:</span></span>

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  <span data-ttu-id="30d3d-178">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-178">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="30d3d-179">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-179">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-26.png)

5.  <span data-ttu-id="30d3d-181">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-181">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="30d3d-182">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-182">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ``` syntax
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a><span data-ttu-id="30d3d-183">Skype for Business に対するアカウントの有効化</span><span class="sxs-lookup"><span data-stu-id="30d3d-183">Enable the account with Skype for Business</span></span>

<span data-ttu-id="30d3d-184">デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-184">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="30d3d-185">Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-185">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="30d3d-186">O365 プランでは、Skype for Business Online スタンドアロンプラン2以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="30d3d-186">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="30d3d-187">プランで会議機能がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-187">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="30d3d-188">Surface Hub のテレフォニーサービスプロバイダーを使用してエンタープライズ Voip (PSTN テレフォニー) が必要な場合は、Skype for Business Online スタンドアロンプラン3が必要です。</span><span class="sxs-lookup"><span data-stu-id="30d3d-188">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="30d3d-189">テナント ユーザーが Exchange メールボックスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-189">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="30d3d-190">Surface Hub アカウントには、Skype for Business Online Standalone Plan 2 または Skype for Business Online Standalone Plan 3 ライセンスが必要ですが、Exchange Online のライセンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="30d3d-190">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="30d3d-191">まず、PC でリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-191">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  <span data-ttu-id="30d3d-192">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-192">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

    ```PowerShell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

    <span data-ttu-id="30d3d-193">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-193">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a><span data-ttu-id="30d3d-194">Exchange 管理センターの使用によるデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="30d3d-194">Create a device account using the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="30d3d-195">この方法は、オンプレミスの Active Directory から同期している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-195">This method will only work if you are syncing from an on-premises Active Directory.</span></span>

<span data-ttu-id="30d3d-196">Exchange 管理センターを使用して、デバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-196">You can use the Exchange Admin Center to create a device account:</span></span>

1.  <span data-ttu-id="30d3d-197">[Exchange 管理センターの使用によるアカウントとメールボックスの作成](#create-device-acct-exch-admin-ctr)</span><span class="sxs-lookup"><span data-stu-id="30d3d-197">[Create an account and mailbox with the Exchange Admin Center](#create-device-acct-exch-admin-ctr).</span></span>
2.  <span data-ttu-id="30d3d-198">[Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成](#create-device-acct-exch-mbx-policy)</span><span class="sxs-lookup"><span data-stu-id="30d3d-198">[Create a mobile device mailbox policy from the Exchange Admin Center](#create-device-acct-exch-mbx-policy).</span></span>
3.  <span data-ttu-id="30d3d-199">[PowerShell の使用によるアカウントの構成](#create-device-acct-exch-powershell-conf)</span><span class="sxs-lookup"><span data-stu-id="30d3d-199">[Use PowerShell to configure the account](#create-device-acct-exch-powershell-conf).</span></span>
4.  <span data-ttu-id="30d3d-200">[Skype for Business に対するアカウントの有効化](#create-device-acct-exch-skype-for-business)</span><span class="sxs-lookup"><span data-stu-id="30d3d-200">[Enable the account with Skype for Business](#create-device-acct-exch-skype-for-business).</span></span>

### <a href="" id="create-device-acct-exch-admin-ctr"></a><span data-ttu-id="30d3d-201">Exchange 管理センターの使用によるアカウントとメールボックスの作成</span><span class="sxs-lookup"><span data-stu-id="30d3d-201">Create an account and mailbox with the Exchange Admin Center</span></span>

1.  <span data-ttu-id="30d3d-202">Exchange 管理者の資格情報を使用して、Exchange 管理センターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-202">Sign in to your Exchange Admin Center using Exchange admin credentials.</span></span>
2.  <span data-ttu-id="30d3d-203">Exchange 管理センター (EAC) が表示されたら、左側のパネルの **[受信者]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-203">Once you are at the Exchange Admin Center (EAC), navigate to **Recipients** in the left panel.</span></span>

    ![Exchange 管理センターのメールボックスを示す画像。](images/setupdeviceacctexch-01.png)

3.  <span data-ttu-id="30d3d-205">メールボックスの一覧の上に表示されているコントロールで **[+]** をクリックして新しいメールボックスを作成し、**[表示名]**、**[名]**、および **[ユーザー ログオン名]** を指定して、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-205">On the controls above the list of mailboxess, choose **+** to create a new one, and provide a **Display name**, **Name**, and **User logon name**, and then click **Save**.</span></span>

    ![新しいメールボックスの作成を示す画像。](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a><span data-ttu-id="30d3d-207">Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="30d3d-207">Create a mobile device mailbox policy from the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="30d3d-208">作成したアカウントにポリシーを作成して割り当てる必要がある場合に、Exchange 2010 を使っている場合は、ポリシーの作成とポリシーの割り当てについて、EMC (Exchange 管理コンソール) を使用する際に、対応する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-208">If you want to create and assign a policy to the account you created, and are using Exchange 2010, look up the corresponding information regarding policy creation and policy assignment when using the EMC (Exchange management console).</span></span>

 

1.  <span data-ttu-id="30d3d-209">Exchange 管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-209">Go to the Exchange Admin Center.</span></span>

    ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-03.png)

2.  <span data-ttu-id="30d3d-211">モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-211">To create a mobile device mailbox policy, click **Mobile** from the left panel, then **Mobile device mailbox policies**.</span></span> <span data-ttu-id="30d3d-212">Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-212">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="30d3d-213">それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-213">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Exchange 管理センターの使用によるモバイル デバイス メールボックス ポリシーの作成を示す映像。](images/setupdeviceacctexch-05.png)

3.  <span data-ttu-id="30d3d-215">新しいモバイル デバイス アカウント メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-215">To create a new mobile device account mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="30d3d-216">名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-216">For the name provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="30d3d-217">ポリシーをパスワードで保護する必要があるため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-217">The policy must not be password-protected, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-06.png)

4.  <span data-ttu-id="30d3d-219">新しいモバイル デバイス メールボックス ポリシーを作成したら、Exchange 管理センターに戻ります。新しいポリシーが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-219">After you have created the new mobile device mailbox policy, go back to the Exchange Admin Center and you will see the new policy listed.</span></span>

    ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-07.png)

5.  <span data-ttu-id="30d3d-221">PowerShell を使用せずに ActiveSync ポリシーを適用するには、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-221">To apply the ActiveSync policy without using PowerShell, you can do the following:</span></span>

    -   <span data-ttu-id="30d3d-222">EAC で、**[受信者]** &gt; **[メールボックス]** の順にクリックし、メールボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-222">In the EAC, click **Recipients** &gt; **Mailboxes** and select a mailbox.</span></span>

        ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-08.png)

    -   <span data-ttu-id="30d3d-224">**詳細**ウィンドウで、**[電話機能と音声機能]** までスクロールし、**[詳細の表示]** をクリックして、**[モバイル デバイスの詳細]** 画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-224">In the **Details** pane, scroll to **Phone and Voice Features** and click **View details** to display the **Mobile Device Details** screen.</span></span>

        ![メールボックスの詳細を示す画像。](images/setupdeviceacctexch-09.png)

    -   <span data-ttu-id="30d3d-226">現在割り当てられているモバイル デバイス メールボックス ポリシーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-226">The mobile device mailbox policy that’s currently assigned is displayed.</span></span> <span data-ttu-id="30d3d-227">モバイル デバイス メールボックス ポリシーを変更するには、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-227">To change the mobile device mailbox policy, click **Browse**.</span></span>

        ![現在割り当てられているモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-10.png)

    -   <span data-ttu-id="30d3d-229">一覧から適切なモバイル デバイス メールボックス ポリシーを選択し、**[OK]**、**[保存]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-229">Choose the appropriate mobile device mailbox policy from the list, click **OK** and then click **Save**.</span></span>

        ![モバイル デバイス メールボックス ポリシーの一覧を示す画像。](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a><span data-ttu-id="30d3d-231">PowerShell の使用によるアカウントの構成</span><span class="sxs-lookup"><span data-stu-id="30d3d-231">Use PowerShell to configure the account</span></span>

<span data-ttu-id="30d3d-232">オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-232">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="30d3d-233">デバイス アカウントのメール アドレスには、次の用途があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-233">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="30d3d-234">メールボックスの種類を標準から会議室に変更する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-234">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="30d3d-235">さまざまな Exchange プロパティを変更する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-235">Change various Exchange properties</span></span>
-   <span data-ttu-id="30d3d-236">ユーザー アカウントのパスワードを無期限に設定する。</span><span class="sxs-lookup"><span data-stu-id="30d3d-236">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="30d3d-237">アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-237">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ``` syntax
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="30d3d-238">値を格納するには、メールボックスからその値を取得します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-238">To store the value got it from the mailbox:</span></span>

    ``` syntax
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="30d3d-239">次のコマンドレットを実行して値を出力します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-239">Print the value by running:</span></span>

    ``` syntax
    $strEmail
    ```

    <span data-ttu-id="30d3d-240">正しいメール アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-240">You will see the correct email address.</span></span>

2.  <span data-ttu-id="30d3d-241">アカウントを会議室メールボックスに変換する必要があります。そのためには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-241">You need to convert the account into a room mailbox, so run:</span></span>

    ``` syntax
    Set-Mailbox $strEmail -Type Room
    ```

3.  <span data-ttu-id="30d3d-242">Surface Hub に対してデバイス アカウントが認証を受けるには、会議室メールボックス アカウントを有効にしてパスワードを設定します。これにより、アカウントをデバイスで使って、ActiveSync を使って会議情報を取得し、Skype for Business にログインします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-242">In order for the device account to be authenticated on a Surface Hub, you need to enable the room mailbox account and set a password, so the account can be used by the device to get meeting information using ActiveSync and log in to Skype for Business.</span></span>

    ``` syntax
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  <span data-ttu-id="30d3d-243">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-243">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="30d3d-244">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-244">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  <span data-ttu-id="30d3d-245">ここで、AD でプロパティをいくつか設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-245">Now we have to set some properties in AD.</span></span> <span data-ttu-id="30d3d-246">そのためには、アカウントのエイリアス ("@" の前に表記されている部分の UPN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="30d3d-246">To do that, you need the alias of the account (this is the part of the UPN that becomes before the “@”).</span></span>

    ``` syntax
    $strAlias = “<your device account’s alias>”
    ```

6.  <span data-ttu-id="30d3d-247">ユーザーを AD で有効にしてから、Surface Hub を使用して認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-247">The user needs to be enabled in AD before it can authenticate with a Surface Hub.</span></span> <span data-ttu-id="30d3d-248">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-248">Run:</span></span>

    ``` syntax
    Set-ADUser $strAlias -Enabled $True
    ```

7.  <span data-ttu-id="30d3d-249">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-249">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="30d3d-250">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30d3d-250">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ``` syntax
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a><span data-ttu-id="30d3d-251">Skype for Business に対するアカウントの有効化</span><span class="sxs-lookup"><span data-stu-id="30d3d-251">Enable the account with Skype for Business</span></span>

<span data-ttu-id="30d3d-252">デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="30d3d-252">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="30d3d-253">Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-253">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="30d3d-254">O365 プランでは、Skype for Business Online スタンドアロンプラン2以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="30d3d-254">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="30d3d-255">プランで会議機能がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-255">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="30d3d-256">Surface Hub のテレフォニーサービスプロバイダーを使用してエンタープライズ Voip (PSTN テレフォニー) が必要な場合は、Skype for Business Online スタンドアロンプラン3が必要です。</span><span class="sxs-lookup"><span data-stu-id="30d3d-256">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="30d3d-257">テナント ユーザーが Exchange メールボックスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d3d-257">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="30d3d-258">Surface Hub アカウントには、Skype for Business Online Standalone Plan 2 または Skype for Business Online Standalone Plan 3 ライセンスが必要ですが、Exchange Online のライセンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="30d3d-258">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="30d3d-259">まず、PC でリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-259">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. <span data-ttu-id="30d3d-260">Surface Hub アカウントレジストラープールを取得する</span><span class="sxs-lookup"><span data-stu-id="30d3d-260">Retrieve your Surface Hub account Registrar Pool</span></span>

<span data-ttu-id="30d3d-261">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="30d3d-261">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```
    
3. <span data-ttu-id="30d3d-262">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d3d-262">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```

    





