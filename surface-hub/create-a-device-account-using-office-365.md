---
title: UI を使ったデバイス アカウントの作成 (Surface Hub v1)
description: グラフィカル ユーザー インターフェイスを使用する場合は、Office 365 の UI または Exchange 管理センターを使って Microsoft Surface Hub のデバイス アカウントを作成できます。
ms.assetid: D11BCDC4-DABA-4B9A-9ECB-58E02CC8218C
ms.reviewer: ''
manager: laurawi
keywords: デバイス アカウントの作成, Office 365 UI, Exchange 管理センター, Microsoft 365 管理センター, Skype for Business, モバイル デバイス メールボックス ポリシー
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/04/2018
ms.localizationpriority: medium
ms.openlocfilehash: dd19e2fd2417acd29e71c7555e94ee849fbc1bec
ms.sourcegitcommit: 32b6c25698479fa289f642c5b5761ff3be15b686
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2021
ms.locfileid: "11318011"
---
# <span data-ttu-id="b46a6-104">UI を使ったデバイス アカウントの作成 (Surface Hub v1)</span><span class="sxs-lookup"><span data-stu-id="b46a6-104">Create a device account using UI (Surface Hub v1)</span></span>

 > [!NOTE]
 ><span data-ttu-id="b46a6-105">このページには、元の Surface Hub (v1) に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b46a6-105">This page includes information about the original Surface Hub (v1).</span></span> <span data-ttu-id="b46a6-106">Surface Hub 2S の場合は、「Surface Hub 2S デバイス アカウントの [作成」を参照してください](surface-hub-2s-account.md)。</span><span class="sxs-lookup"><span data-stu-id="b46a6-106">For Surface Hub 2S, see [Create Surface Hub 2S device account](surface-hub-2s-account.md).</span></span>

<span data-ttu-id="b46a6-107">グラフィカル ユーザー インターフェイスを使用する場合は、[Office 365 の UI](#create-device-acct-o365) または [Exchange 管理センター](#create-device-acct-eac)を使って Microsoft Surface Hub のデバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-107">If you prefer to use a graphical user interface, you can create a device account for your Microsoft Surface Hub with either the [Office 365 UI](#create-device-acct-o365) or the [Exchange Admin Center](#create-device-acct-eac).</span></span>

## <a href="" id="create-device-acct-o365"></a><span data-ttu-id="b46a6-108">Office 365 を使ったデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="b46a6-108">Create a device account using Office 365</span></span>


1.  <span data-ttu-id="b46a6-109">[Microsoft 365 管理センターでアカウントを作成します](#create-device-acct-o365-admin-ctr)。</span><span class="sxs-lookup"><span data-stu-id="b46a6-109">[Create the account in the Microsoft 365 Admin Center](#create-device-acct-o365-admin-ctr).</span></span>
2.  <span data-ttu-id="b46a6-110">[Microsoft Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成](#create-device-acct-o365-mbx-policy)</span><span class="sxs-lookup"><span data-stu-id="b46a6-110">[Create a mobile device mailbox (ActiveSync) policy from the Microsoft Exchange Admin Center](#create-device-acct-o365-mbx-policy).</span></span>
3.  <span data-ttu-id="b46a6-111">[PowerShell の使用によるデバイス アカウント作成の完了](#create-device-acct-o365-complete-acct).</span><span class="sxs-lookup"><span data-stu-id="b46a6-111">[Use PowerShell to complete device account creation](#create-device-acct-o365-complete-acct).</span></span>
4.  <span data-ttu-id="b46a6-112">[PowerShell の使用によるアカウントの Exchange プロパティの構成](#create-device-acct-o365-configure-exch-prop)</span><span class="sxs-lookup"><span data-stu-id="b46a6-112">[Use PowerShell to configure Exchange properties of the account](#create-device-acct-o365-configure-exch-prop).</span></span>
5.  <span data-ttu-id="b46a6-113">[Skype for Business に対するアカウントの有効化](#create-device-acct-o365-skype-for-business)</span><span class="sxs-lookup"><span data-stu-id="b46a6-113">[Enable the account with Skype for Business](#create-device-acct-o365-skype-for-business).</span></span>

### <a href="" id="create-device-acct-o365-admin-ctr"></a><span data-ttu-id="b46a6-114">管理センターでアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="b46a6-114">Create the account in the admin center</span></span>

1.  <span data-ttu-id="b46a6-115">にアクセスして Office 365 にサインインします [https://portal.office.com](https://portal.office.com) 。</span><span class="sxs-lookup"><span data-stu-id="b46a6-115">Sign in to Office 365 by visiting [https://portal.office.com](https://portal.office.com).</span></span>

2.  <span data-ttu-id="b46a6-116">Office 365 テナントの管理者資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-116">Provide the admin credentials for your Office 365 tenant.</span></span> <span data-ttu-id="b46a6-117">これにより、Microsoft 365 管理センターに移動します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-117">This will take you to your Microsoft 365 Admin Center.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Microsoft 365 管理センター。](images/setupdeviceaccto365-02.png)

3. <span data-ttu-id="b46a6-119">管理センターで、左側のパネルの **[リソース** ] に移動し、[会議室] を& **します**。</span><span class="sxs-lookup"><span data-stu-id="b46a6-119">In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![管理&の会議室と備品オプション](images/room-equipment.png)

4. <span data-ttu-id="b46a6-121">**[追加]** をクリックして会議室アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-121">Click **Add** to create a new Room account.</span></span> <span data-ttu-id="b46a6-122">アカウントの表示名とメール アドレスを入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-122">Enter a display name and email address for the account, and then click **Add**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![新しい会議室アカウントの作成ウィンドウ](images/room-add.png)

5. <span data-ttu-id="b46a6-124">作成した会議室アカウントを [アクティブなユーザー] の一覧で選択します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-124">Select the Room account you just created in the Active Users list.</span></span> <span data-ttu-id="b46a6-125">右側のパネルに、アカウントのプロパティといくつかの省略可能なオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-125">In the right panel, you can see the account properties and several optional actions.</span></span> <span data-ttu-id="b46a6-126">**[パスワードのリセット]** をクリックしてパスワードを変更し、**[このユーザーが最初にサインインしたときに、パスワードの変更を行うようにする]** をオフにします (Surface Hub のサインイン フローではパスワードを変更できないため)。</span><span class="sxs-lookup"><span data-stu-id="b46a6-126">Click **Reset password** to change the password, and unselect **Make this user change their password when they first sign in**, because it is not possible to change the password from the Surface Hub sign-in flow.</span></span>

6. <span data-ttu-id="b46a6-127">**[割り当て済みのライセンス]** セクションの **[編集]** をクリックし、適切なライセンスの横に表示されているドロップダウン矢印をクリックして詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-127">In the **Assigned license** section, click **Edit**, and then click the dropdown arrow next to the appropriate license to expand the details.</span></span> <span data-ttu-id="b46a6-128">ユーザーの場所を選択し、ライセンスの一覧で、**[Skype for Business Online (プラン 2)]** をオンにして **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-128">Select a user location, and in the list of licenses, toggle on **Skype for Business Online (Plan 2)**, and then click **Save**.</span></span> <span data-ttu-id="b46a6-129">このライセンスは組織によって異なる場合があります (たとえば、プラン 2 の場合も プラン 3 の場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="b46a6-129">The license may vary depending on your organization (for example, you might have Plan 2 or Plan 3).</span></span>

### <a href="" id="create-device-acct-o365-mbx-policy"></a><span data-ttu-id="b46a6-130">Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="b46a6-130">Create a mobile device mailbox (ActiveSync) policy from the Exchange Admin Center</span></span>

1.  <span data-ttu-id="b46a6-131">管理センターの左側のパネルで、[管理]**をクリックし\*\*\*\*、[Exchange] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="b46a6-131">In the admin center’s left panel, click **ADMIN**, and then click **Exchange**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![管理センター。Exchange のアクティブなユーザーを表示します。](images/setupdeviceaccto365-08.png)

2.  <span data-ttu-id="b46a6-133">ブラウザーの別のタブが開き、Exchange 管理センターが表示されます。ここで、Surface Hub のメールボックスの設定を作成して設定できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-133">This will open another tab on your browser to take you to the Exchange Admin Center, where you can create and set the Mailbox Setting for Surface Hub.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Exchange 管理センター。](images/setupdeviceaccto365-09.png)

3.  <span data-ttu-id="b46a6-135">モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-135">To create a Mobile Device Mailbox Policy, click **Mobile** from the left panel and then click **Mobile device mailbox policies**.</span></span> <span data-ttu-id="b46a6-136">Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-136">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="b46a6-137">それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-137">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Exchange 管理センター - モバイル デバイス メールボックス ポリシーの作成。](images/setupdeviceaccto365-10.png)

4.  <span data-ttu-id="b46a6-139">新しい Surface Hub のモバイル デバイス メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-139">To create a New Surface Hub mobile device mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="b46a6-140">名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-140">For the name, provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="b46a6-141">ポリシーに割り当てられたデバイスのパスワードがこのポリシーで要求されないようにします。そのため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-141">Make sure the policy does not require a password for the devices assigned to, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![新しいモバイル デバイス ポリシーを示す画像。](images/setupdeviceaccto365-11.png)

5.  <span data-ttu-id="b46a6-143">新しいモバイル デバイス メールボックス ポリシーを作成したら、**Exchange 管理センター**に戻ります。新しいポリシーが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-143">After you have created the new mobile device mailbox policy, go back to the **Exchange Admin Center** and you will see the new policy listed.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーの画像。](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a><span data-ttu-id="b46a6-145">PowerShell の使用によるデバイス アカウント作成の完了</span><span class="sxs-lookup"><span data-stu-id="b46a6-145">Use PowerShell to complete device account creation</span></span>

<span data-ttu-id="b46a6-146">ここからは、PowerShell を使って構成を設定し、アカウント作成処理を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-146">From here on, you'll need to finish the account creation process using PowerShell to set up some configuration.</span></span>

<span data-ttu-id="b46a6-147">これらの PowerShell スクリプトで使用されるコマンドレットを実行するには、次のツールを管理者用 PowerShell コンソールにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-147">In order to run cmdlets used by these PowerShell scripts, the following must be installed for the admin PowerShell console:</span></span>

-   [<span data-ttu-id="b46a6-148">MICROSOFT ONLINE SERVICES Sign-In IT プロフェッショナル RTW アシスタント</span><span class="sxs-lookup"><span data-stu-id="b46a6-148">Microsoft Online Services Sign-In Assistant for IT Professionals RTW</span></span>](https://www.microsoft.com/download/details.aspx?id=41950)
-   [<span data-ttu-id="b46a6-149">Windows PowerShell 用 Microsoft Azure Active Directory モジュール</span><span class="sxs-lookup"><span data-stu-id="b46a6-149">Windows Azure Active Directory Module for Windows PowerShell</span></span>](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [<span data-ttu-id="b46a6-150">Windows PowerShell Module for Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="b46a6-150">Skype for Business Online, Windows PowerShell Module</span></span>](https://www.microsoft.com/download/details.aspx?id=39366)

<span data-ttu-id="b46a6-151">PowerShell に次のモジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-151">Install the following module in PowerShell.</span></span>

```powershell
install-module AzureAD
Install-module MsOnline
```

### <span data-ttu-id="b46a6-152">オンライン サービスへの接続</span><span class="sxs-lookup"><span data-stu-id="b46a6-152">Connecting to online services</span></span>

1.  <span data-ttu-id="b46a6-153">管理者として Windows PowerShell を実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-153">Run Windows PowerShell as Administrator.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Windows PowerShell を起動し、管理者として実行する方法を示す画像。](images/setupdeviceaccto365-17.png)

2.  <span data-ttu-id="b46a6-155">Credentials オブジェクトを作成し、Skype for Business Online に接続している新しいセッションを作成します。次に、グローバルのテナント管理者アカウントを指定し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-155">Create a Credentials object, then create a new session that connects to Skype for Business Online, and provide the global tenant administrator account, then click **OK**.</span></span>

    ![Windows PowerShell 資格情報の要求の画像。](images/setupdeviceaccto365-18.png)

3.  <span data-ttu-id="b46a6-157">Microsoft Online Services に接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-157">To connect to Microsoft Online Services, run:</span></span>

    ```powershell
    Connect-MsolService -Credential $Cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-19.png)

4.  <span data-ttu-id="b46a6-159">ここで、Skype for Business Online サービスに接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-159">Now to connect to Skype for Business Online Services, run:</span></span>

    ```powershell
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-20.png)

5.  <span data-ttu-id="b46a6-161">最後に、Exchange Online サービスに接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-161">Finally, to connect to Exchange Online Services, run:</span></span>

    ```powershell
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-21.png)

6.  <span data-ttu-id="b46a6-163">ここで、Skype for Business Online セッションと、前の手順で作成した Exchange Online セッションをインポートする必要があります。これにより、Exchange と Skype のコマンドをローカルで使用できるようにインポートします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-163">Now you have to import the Skype for Business Online Session and the Exchange Online session you have just created, which will import the Exchange and Skype Commands so you can use them locally.</span></span>

    ```powershell
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    <span data-ttu-id="b46a6-164">この手順の完了には時間がかかることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b46a6-164">Note that this could take a while to complete.</span></span>

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-22.png)

7.  <span data-ttu-id="b46a6-166">オンライン サービスに接続したら、さらにいくつかのコマンドレットを実行して、このアカウントを Surface Hub デバイス アカウントとして構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-166">Once you’re connected to the online services you need to run a few more cmdlets to configure this account as a Surface Hub device account.</span></span>

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a><span data-ttu-id="b46a6-167">PowerShell の使用によるアカウントの Exchange プロパティの構成</span><span class="sxs-lookup"><span data-stu-id="b46a6-167">Use PowerShell to configure Exchange properties of the account</span></span>

<span data-ttu-id="b46a6-168">オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-168">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="b46a6-169">デバイス アカウントのメール アドレスには、次の用途があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-169">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="b46a6-170">メールボックスの種類を標準から会議室に変更する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-170">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="b46a6-171">パスワードを設定して、会議室メールボックスのアカウントを有効にする。</span><span class="sxs-lookup"><span data-stu-id="b46a6-171">Set the password and enable the room mailbox account</span></span>
-   <span data-ttu-id="b46a6-172">さまざまな Exchange プロパティを変更する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-172">Change various Exchange properties</span></span>
-   <span data-ttu-id="b46a6-173">ユーザー アカウントのパスワードを無期限に設定する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-173">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="b46a6-174">アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-174">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="b46a6-175">値を格納するには、メールボックスからその値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-175">To store the value get it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="b46a6-176">値を出力します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-176">Print the value:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="b46a6-177">正しいメール アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-177">You will see the correct email address.</span></span>

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-23.png)

2. <span data-ttu-id="b46a6-179">次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-179">Run the following cmdlet:</span></span>

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  <span data-ttu-id="b46a6-180">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-180">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="b46a6-181">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b46a6-181">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-26.png)

5.  <span data-ttu-id="b46a6-183">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-183">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="b46a6-184">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b46a6-184">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ```powershell
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a><span data-ttu-id="b46a6-185">Skype for Business に対するアカウントの有効化</span><span class="sxs-lookup"><span data-stu-id="b46a6-185">Enable the account with Skype for Business</span></span>

<span data-ttu-id="b46a6-186">デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-186">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="b46a6-187">Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-187">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="b46a6-188">O365 プランに Skype for Business Online スタンドアロン プラン 2 以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="b46a6-188">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="b46a6-189">プランで会議機能がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-189">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="b46a6-190">Surface Hub 用のエンタープライズ VoIPサービス プロバイダーを使用する PSTN テレフォニー (PSTN テレフォニー) が必要な場合は、Skype for Business Online スタンドアロン プラン 3 が必要です。</span><span class="sxs-lookup"><span data-stu-id="b46a6-190">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="b46a6-191">テナント ユーザーが Exchange メールボックスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-191">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="b46a6-192">Surface Hub アカウントには Skype for Business Online スタンドアロン プラン 2 または Skype for Business Online スタンドアロン プラン 3 のライセンスが必要ですが、Exchange Online ライセンスは必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="b46a6-192">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="b46a6-193">まず、PC でリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-193">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  <span data-ttu-id="b46a6-194">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-194">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

    ```powershell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

     <span data-ttu-id="b46a6-195">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-195">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```powershell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a><span data-ttu-id="b46a6-196">Exchange 管理センターの使用によるデバイス アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="b46a6-196">Create a device account using the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="b46a6-197">このメソッドは、オンプレミスの Active Directory から同期する場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-197">This method will only work if you are syncing from an on-premises Active Directory.</span></span>

<span data-ttu-id="b46a6-198">Exchange 管理センターを使用して、デバイス アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-198">You can use the Exchange Admin Center to create a device account:</span></span>

1.  <span data-ttu-id="b46a6-199">[Exchange 管理センターの使用によるアカウントとメールボックスの作成](#create-device-acct-exch-admin-ctr)</span><span class="sxs-lookup"><span data-stu-id="b46a6-199">[Create an account and mailbox with the Exchange Admin Center](#create-device-acct-exch-admin-ctr).</span></span>
2.  <span data-ttu-id="b46a6-200">[Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成](#create-device-acct-exch-mbx-policy)</span><span class="sxs-lookup"><span data-stu-id="b46a6-200">[Create a mobile device mailbox policy from the Exchange Admin Center](#create-device-acct-exch-mbx-policy).</span></span>
3.  <span data-ttu-id="b46a6-201">[PowerShell の使用によるアカウントの構成](#create-device-acct-exch-powershell-conf)</span><span class="sxs-lookup"><span data-stu-id="b46a6-201">[Use PowerShell to configure the account](#create-device-acct-exch-powershell-conf).</span></span>
4.  <span data-ttu-id="b46a6-202">[Skype for Business に対するアカウントの有効化](#create-device-acct-exch-skype-for-business)</span><span class="sxs-lookup"><span data-stu-id="b46a6-202">[Enable the account with Skype for Business](#create-device-acct-exch-skype-for-business).</span></span>

### <a href="" id="create-device-acct-exch-admin-ctr"></a><span data-ttu-id="b46a6-203">Exchange 管理センターの使用によるアカウントとメールボックスの作成</span><span class="sxs-lookup"><span data-stu-id="b46a6-203">Create an account and mailbox with the Exchange Admin Center</span></span>

1.  <span data-ttu-id="b46a6-204">Exchange 管理者の資格情報を使用して、Exchange 管理センターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-204">Sign in to your Exchange Admin Center using Exchange admin credentials.</span></span>
2.  <span data-ttu-id="b46a6-205">Exchange 管理センター (EAC) が表示されたら、左側のパネルの **[受信者]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-205">Once you are at the Exchange Admin Center (EAC), navigate to **Recipients** in the left panel.</span></span>

    ![Exchange 管理センターのメールボックスを示す画像。](images/setupdeviceacctexch-01.png)

3.  <span data-ttu-id="b46a6-207">メールボックスの一覧の上に表示されているコントロールで **[+]** をクリックして新しいメールボックスを作成し、**[表示名]**、**[名]**、および **[ユーザー ログオン名]** を指定して、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-207">On the controls above the list of mailboxess, choose **+** to create a new one, and provide a **Display name**, **Name**, and **User logon name**, and then click **Save**.</span></span>

    ![新しいメールボックスの作成を示す画像。](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a><span data-ttu-id="b46a6-209">Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="b46a6-209">Create a mobile device mailbox policy from the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="b46a6-210">作成したアカウントにポリシーを作成して割り当て、Exchange 2010 を使用する場合は、EMC (Exchange 管理コンソール) を使用するときに、ポリシーの作成とポリシーの割り当てに関する対応する情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-210">If you want to create and assign a policy to the account you created, and are using Exchange 2010, look up the corresponding information regarding policy creation and policy assignment when using the EMC (Exchange management console).</span></span>

 

1.  <span data-ttu-id="b46a6-211">Exchange 管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-211">Go to the Exchange Admin Center.</span></span>

    ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-03.png)

2.  <span data-ttu-id="b46a6-213">モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-213">To create a mobile device mailbox policy, click **Mobile** from the left panel, then **Mobile device mailbox policies**.</span></span> <span data-ttu-id="b46a6-214">Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-214">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="b46a6-215">それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-215">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Exchange 管理センターの使用によるモバイル デバイス メールボックス ポリシーの作成を示す映像。](images/setupdeviceacctexch-05.png)

3.  <span data-ttu-id="b46a6-217">新しいモバイル デバイス アカウント メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-217">To create a new mobile device account mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="b46a6-218">名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-218">For the name provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="b46a6-219">ポリシーをパスワードで保護する必要があるため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-219">The policy must not be password-protected, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-06.png)

4.  <span data-ttu-id="b46a6-221">新しいモバイル デバイス メールボックス ポリシーを作成したら、Exchange 管理センターに戻ります。新しいポリシーが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-221">After you have created the new mobile device mailbox policy, go back to the Exchange Admin Center and you will see the new policy listed.</span></span>

    ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-07.png)

5.  <span data-ttu-id="b46a6-223">PowerShell を使用せずに ActiveSync ポリシーを適用するには、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-223">To apply the ActiveSync policy without using PowerShell, you can do the following:</span></span>

    -   <span data-ttu-id="b46a6-224">EAC で、**[受信者]** &gt; **[メールボックス]** の順にクリックし、メールボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-224">In the EAC, click **Recipients** &gt; **Mailboxes** and select a mailbox.</span></span>

        ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-08.png)

    -   <span data-ttu-id="b46a6-226">**詳細**ウィンドウで、**[電話機能と音声機能]** までスクロールし、**[詳細の表示]** をクリックして、**[モバイル デバイスの詳細]** 画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-226">In the **Details** pane, scroll to **Phone and Voice Features** and click **View details** to display the **Mobile Device Details** screen.</span></span>

        ![メールボックスの詳細を示す画像。](images/setupdeviceacctexch-09.png)

    -   <span data-ttu-id="b46a6-228">現在割り当てられているモバイル デバイス メールボックス ポリシーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-228">The mobile device mailbox policy that’s currently assigned is displayed.</span></span> <span data-ttu-id="b46a6-229">モバイル デバイス メールボックス ポリシーを変更するには、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-229">To change the mobile device mailbox policy, click **Browse**.</span></span>

        ![現在割り当てられているモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-10.png)

    -   <span data-ttu-id="b46a6-231">一覧から適切なモバイル デバイス メールボックス ポリシーを選択し、**[OK]**、**[保存]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-231">Choose the appropriate mobile device mailbox policy from the list, click **OK** and then click **Save**.</span></span>

        ![モバイル デバイス メールボックス ポリシーの一覧を示す画像。](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a><span data-ttu-id="b46a6-233">PowerShell の使用によるアカウントの構成</span><span class="sxs-lookup"><span data-stu-id="b46a6-233">Use PowerShell to configure the account</span></span>

<span data-ttu-id="b46a6-234">オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-234">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="b46a6-235">デバイス アカウントのメール アドレスには、次の用途があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-235">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="b46a6-236">メールボックスの種類を標準から会議室に変更する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-236">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="b46a6-237">さまざまな Exchange プロパティを変更する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-237">Change various Exchange properties</span></span>
-   <span data-ttu-id="b46a6-238">ユーザー アカウントのパスワードを無期限に設定する。</span><span class="sxs-lookup"><span data-stu-id="b46a6-238">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="b46a6-239">アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-239">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="b46a6-240">値を格納するには、メールボックスからその値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-240">To store the value got it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="b46a6-241">次のコマンドレットを実行して値を出力します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-241">Print the value by running:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="b46a6-242">正しいメール アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-242">You will see the correct email address.</span></span>

2.  <span data-ttu-id="b46a6-243">アカウントをルーム メールボックスに変換する必要があります。次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-243">You need to convert the account into a room mailbox, so run:</span></span>

    ```powershell
    Set-Mailbox $strEmail -Type Room
    ```

3.  <span data-ttu-id="b46a6-244">Surface Hub に対してデバイス アカウントが認証を受けるには、会議室メールボックス アカウントを有効にしてパスワードを設定します。これにより、アカウントをデバイスで使って、ActiveSync を使って会議情報を取得し、Skype for Business にログインします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-244">In order for the device account to be authenticated on a Surface Hub, you need to enable the room mailbox account and set a password, so the account can be used by the device to get meeting information using ActiveSync and log in to Skype for Business.</span></span>

    ```powershell
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  <span data-ttu-id="b46a6-245">会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-245">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="b46a6-246">設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b46a6-246">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  <span data-ttu-id="b46a6-247">ここで、AD でプロパティをいくつか設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-247">Now we have to set some properties in AD.</span></span> <span data-ttu-id="b46a6-248">そのためには、アカウントのエイリアス ("@" の前に表記されている部分の UPN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="b46a6-248">To do that, you need the alias of the account (this is the part of the UPN that becomes before the “@”).</span></span>

    ```powershell
    $strAlias = “<your device account’s alias>”
    ```

6.  <span data-ttu-id="b46a6-249">ユーザーを AD で有効にしてから、Surface Hub を使用して認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-249">The user needs to be enabled in AD before it can authenticate with a Surface Hub.</span></span> <span data-ttu-id="b46a6-250">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-250">Run:</span></span>

    ```powershell
    Set-ADUser $strAlias -Enabled $True
    ```

7.  <span data-ttu-id="b46a6-251">パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-251">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="b46a6-252">詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b46a6-252">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ```powershell
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a><span data-ttu-id="b46a6-253">Skype for Business に対するアカウントの有効化</span><span class="sxs-lookup"><span data-stu-id="b46a6-253">Enable the account with Skype for Business</span></span>

<span data-ttu-id="b46a6-254">デバイス アカウントを Skype for Business に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="b46a6-254">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="b46a6-255">Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-255">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

- <span data-ttu-id="b46a6-256">O365 プランに Skype for Business Online スタンドアロン プラン 2 以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="b46a6-256">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="b46a6-257">プランで会議機能がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-257">The plan needs to support conferencing capability.</span></span>
- <span data-ttu-id="b46a6-258">Surface Hub 用のエンタープライズ VoIPサービス プロバイダーを使用して電話 (PSTN テレフォニー) を使用する必要がある場合は、Skype for Business Online スタンドアロン プラン 3 が必要です。</span><span class="sxs-lookup"><span data-stu-id="b46a6-258">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
- <span data-ttu-id="b46a6-259">テナント ユーザーが Exchange メールボックスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b46a6-259">Your tenant users must have Exchange mailboxes.</span></span>
- <span data-ttu-id="b46a6-260">Surface Hub アカウントには Skype for Business Online スタンドアロン プラン 2 または Skype for Business Online スタンドアロン プラン 3 のライセンスが必要ですが、Exchange Online ライセンスは必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="b46a6-260">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1. <span data-ttu-id="b46a6-261">まず、PC でリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-261">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. <span data-ttu-id="b46a6-262">Surface Hub アカウントのレジストラー プールを取得します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-262">Retrieve your Surface Hub account Registrar Pool.</span></span>

   <span data-ttu-id="b46a6-263">環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b46a6-263">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

   ```PowerShell
   Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
   ```

3. <span data-ttu-id="b46a6-264">Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="b46a6-264">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```