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
# UI を使用してデバイス アカウントを作成する (Surface Hub)


グラフィカル ユーザー インターフェイスを使用する場合は、[Office 365 の UI](#create-device-acct-o365) または [Exchange 管理センター](#create-device-acct-eac)を使って Microsoft Surface Hub のデバイス アカウントを作成できます。

## <a href="" id="create-device-acct-o365"></a>Office 365 を使ったデバイス アカウントの作成


1.  [Microsoft 365 管理センターでアカウントを作成](#create-device-acct-o365-admin-ctr)します。
2.  [Microsoft Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成](#create-device-acct-o365-mbx-policy)
3.  [PowerShell の使用によるデバイス アカウント作成の完了](#create-device-acct-o365-complete-acct).
4.  [PowerShell の使用によるアカウントの Exchange プロパティの構成](#create-device-acct-o365-configure-exch-prop)
5.  [Skype for Business に対するアカウントの有効化](#create-device-acct-o365-skype-for-business)

### <a href="" id="create-device-acct-o365-admin-ctr"></a>管理センターでアカウントを作成する

1.  アクセスして、Office 365 にサインインします。https://portal.office.com
2.  Office 365 テナントの管理者資格情報を入力します。 この操作を行うと、Microsoft 365 管理センターに移動します。

    ![Microsoft 365 管理センター](images/setupdeviceaccto365-02.png)

3. 管理センターで、左側のパネルにある [**リソース**] に移動し、[**ルーム & 備品**] をクリックします。

    ![管理センターで & の会議室のオプション](images/room-equipment.png)

4. **[追加]** をクリックして会議室アカウントを作成します。 アカウントの表示名とメール アドレスを入力し、**[追加]** をクリックします。

    ![新しい会議室アカウントの作成ウィンドウ](images/room-add.png)

5. 作成した会議室アカウントを [アクティブなユーザー] の一覧で選択します。 右側のパネルに、アカウントのプロパティといくつかの省略可能なオプションが表示されます。 **[パスワードのリセット]** をクリックしてパスワードを変更し、**[このユーザーが最初にサインインしたときに、パスワードの変更を行うようにする]** をオフにします (Surface Hub のサインイン フローではパスワードを変更できないため)。

6. **[割り当て済みのライセンス]** セクションの **[編集]** をクリックし、適切なライセンスの横に表示されているドロップダウン矢印をクリックして詳細を表示します。 ユーザーの場所を選択し、ライセンスの一覧で、**[Skype for Business Online (プラン 2)]** をオンにして **[保存]** をクリックします。 このライセンスは組織によって異なる場合があります (たとえば、プラン 2 の場合も プラン 3 の場合もあります)。

### <a href="" id="create-device-acct-o365-mbx-policy"></a>Exchange 管理センターからのモバイル デバイス メールボックス (ActiveSync) ポリシーの作成

1.  管理センターの左側のパネルで、[**管理者**] をクリックし、[ **Exchange**] をクリックします。

    ![管理センター、exchange のアクティブユーザーを示しています。](images/setupdeviceaccto365-08.png)

2.  ブラウザーの別のタブが開き、Exchange 管理センターが表示されます。ここで、Surface Hub のメールボックスの設定を作成して設定できます。

    ![Exchange 管理センター。](images/setupdeviceaccto365-09.png)

3.  モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。 Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。 それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。

    ![Exchange 管理センター - モバイル デバイス メールボックス ポリシーの作成。](images/setupdeviceaccto365-10.png)

4.  新しい Surface Hub のモバイル デバイス メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。 名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。 ポリシーに割り当てられたデバイスのパスワードがこのポリシーで要求されないようにします。そのため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。

    ![新しいモバイル デバイス ポリシーを示す画像。](images/setupdeviceaccto365-11.png)

5.  新しいモバイル デバイス メールボックス ポリシーを作成したら、**Exchange 管理センター**に戻ります。新しいポリシーが一覧に表示されます。

    ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーの画像。](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a>PowerShell の使用によるデバイス アカウント作成の完了

ここからは、PowerShell を使って構成を設定し、アカウント作成処理を完了する必要があります。

これらの PowerShell スクリプトで使用されるコマンドレットを実行するには、次のツールを管理者用 PowerShell コンソールにインストールする必要があります。

-   [IT プロフェッショナル向け Microsoft Online Service サインインアシスタントプロフェッショナル用 RTWHTTP://GO.MICROSOFT.COM/FWLINK/?LINKID=625123](https://www.microsoft.com/download/details.aspx?id=41950)
-   [Windows PowerShell 用 Microsoft Azure Active Directory モジュール](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [Windows PowerShell Module for Skype for Business Online](https://www.microsoft.com/download/details.aspx?id=39366)

Powershell で次のモジュールをインストールする
``` syntax
    install-module AzureAD
    Install-module MsOnline
```

### オンライン サービスへの接続

1.  管理者として Windows PowerShell を実行します。

    ![Windows PowerShell を起動し、管理者として実行する方法を示す画像。](images/setupdeviceaccto365-17.png)

2.  Credentials オブジェクトを作成し、Skype for Business Online に接続している新しいセッションを作成します。次に、グローバルのテナント管理者アカウントを指定し、**[OK]** をクリックします。

    ![Windows PowerShell 資格情報の要求の画像。](images/setupdeviceaccto365-18.png)

3.  Microsoft Online Services に接続するには、次のコマンドを実行します。

    ``` syntax
    Connect-MsolService -Credential $Cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-19.png)

4.  ここで、Skype for Business Online サービスに接続するには、次のコマンドを実行します。

    ``` syntax
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-20.png)

5.  最後に、Exchange Online サービスに接続するには、次のコマンドを実行します。

    ``` syntax
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-21.png)

6.  ここで、Skype for Business Online セッションと、前の手順で作成した Exchange Online セッションをインポートする必要があります。これにより、Exchange と Skype のコマンドをローカルで使用できるようにインポートします。

    ``` syntax
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    この手順の完了には時間がかかることに注意してください。

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-22.png)

7.  オンライン サービスに接続したら、さらにいくつかのコマンドレットを実行して、このアカウントを Surface Hub デバイス アカウントとして構成する必要があります。

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a>PowerShell の使用によるアカウントの Exchange プロパティの構成

オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。 デバイス アカウントのメール アドレスには、次の用途があります。

-   メールボックスの種類を標準から会議室に変更する。
-   パスワードを設定して、会議室メールボックスのアカウントを有効にする。
-   さまざまな Exchange プロパティを変更する。
-   ユーザー アカウントのパスワードを無期限に設定する。

1.  アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    値を格納するには、メールボックスからその値を取得します。

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    値を出力します。

    ```powershell
    $strEmail
    ```

    正しいメール アドレスが表示されます。

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-23.png)

2. 次のコマンドレットを実行します。

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![PowerShell コマンドレットを示す画像。](images/setupdeviceaccto365-26.png)

5.  パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。 詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。

    ``` syntax
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a>Skype for Business に対するアカウントの有効化

デバイス アカウントを Skype for Business に対して有効にします。

Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。

-   O365 プランでは、Skype for Business Online スタンドアロンプラン2以上が必要です。 プランで会議機能がサポートされている必要があります。
-   Surface Hub のテレフォニーサービスプロバイダーを使用してエンタープライズ Voip (PSTN テレフォニー) が必要な場合は、Skype for Business Online スタンドアロンプラン3が必要です。
-   テナント ユーザーが Exchange メールボックスを持っている必要があります。
-   Surface Hub アカウントには、Skype for Business Online Standalone Plan 2 または Skype for Business Online Standalone Plan 3 ライセンスが必要ですが、Exchange Online のライセンスは必要ありません。

1.  まず、PC でリモート PowerShell セッションを作成します。

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。

    ```PowerShell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

    環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a>Exchange 管理センターの使用によるデバイス アカウントの作成

>[!NOTE]
>この方法は、オンプレミスの Active Directory から同期している場合にのみ機能します。

Exchange 管理センターを使用して、デバイス アカウントを作成できます。

1.  [Exchange 管理センターの使用によるアカウントとメールボックスの作成](#create-device-acct-exch-admin-ctr)
2.  [Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成](#create-device-acct-exch-mbx-policy)
3.  [PowerShell の使用によるアカウントの構成](#create-device-acct-exch-powershell-conf)
4.  [Skype for Business に対するアカウントの有効化](#create-device-acct-exch-skype-for-business)

### <a href="" id="create-device-acct-exch-admin-ctr"></a>Exchange 管理センターの使用によるアカウントとメールボックスの作成

1.  Exchange 管理者の資格情報を使用して、Exchange 管理センターにサインインします。
2.  Exchange 管理センター (EAC) が表示されたら、左側のパネルの **[受信者]** に移動します。

    ![Exchange 管理センターのメールボックスを示す画像。](images/setupdeviceacctexch-01.png)

3.  メールボックスの一覧の上に表示されているコントロールで **[+]** をクリックして新しいメールボックスを作成し、**[表示名]**、**[名]**、および **[ユーザー ログオン名]** を指定して、**[保存]** をクリックします。

    ![新しいメールボックスの作成を示す画像。](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a>Exchange 管理センターからのモバイル デバイス メールボックス ポリシーの作成

>[!NOTE]
>作成したアカウントにポリシーを作成して割り当てる必要がある場合に、Exchange 2010 を使っている場合は、ポリシーの作成とポリシーの割り当てについて、EMC (Exchange 管理コンソール) を使用する際に、対応する情報を参照してください。

 

1.  Exchange 管理センターにアクセスします。

    ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-03.png)

2.  モバイル デバイス メールボックス ポリシーを作成するには、左側のパネルの **[モバイル]** をクリックし、**[モバイル デバイス メールボックス ポリシー]** をクリックします。 Surface Hub には、パスワードを要求しないモバイル デバイス メールボックス ポリシーが適用されたアカウントが必要です。したがって、この要件に一致するポリシーが既に存在する場合は、アカウントにそのポリシーを適用できます。 それ以外の場合は、次の手順を使用して、Surface Hub デバイス アカウントのみに対して使用される新しいポリシーを作成します。

    ![Exchange 管理センターの使用によるモバイル デバイス メールボックス ポリシーの作成を示す映像。](images/setupdeviceacctexch-05.png)

3.  新しいモバイル デバイス アカウント メールボックス ポリシーを作成するには、ポリシーの一覧の上に表示されているコントロールで **+** をクリックし、新しいポリシーを追加します。 名前については、このポリシーと他のデバイス アカウントを区別しやすい名前 (たとえば、*SurfaceHubDeviceMobilePolicy*) を入力します。 ポリシーをパスワードで保護する必要があるため、**[パスワードを要求する]** チェック ボックスがオフになっていることを確認し、**[保存]** をクリックします。

    ![新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-06.png)

4.  新しいモバイル デバイス メールボックス ポリシーを作成したら、Exchange 管理センターに戻ります。新しいポリシーが一覧に表示されます。

    ![Exchange 管理センターでの新しいモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-07.png)

5.  PowerShell を使用せずに ActiveSync ポリシーを適用するには、次の操作を実行できます。

    -   EAC で、**[受信者]** &gt; **[メールボックス]** の順にクリックし、メールボックスを選択します。

        ![Exchange 管理センターを示す画像。](images/setupdeviceacctexch-08.png)

    -   **詳細**ウィンドウで、**[電話機能と音声機能]** までスクロールし、**[詳細の表示]** をクリックして、**[モバイル デバイスの詳細]** 画面を表示します。

        ![メールボックスの詳細を示す画像。](images/setupdeviceacctexch-09.png)

    -   現在割り当てられているモバイル デバイス メールボックス ポリシーが表示されます。 モバイル デバイス メールボックス ポリシーを変更するには、**[参照]** をクリックします。

        ![現在割り当てられているモバイル デバイス メールボックス ポリシーを示す画像。](images/setupdeviceacctexch-10.png)

    -   一覧から適切なモバイル デバイス メールボックス ポリシーを選択し、**[OK]**、**[保存]** の順にクリックします。

        ![モバイル デバイス メールボックス ポリシーの一覧を示す画像。](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a>PowerShell の使用によるアカウントの構成

オンライン サービスに接続したので、デバイス アカウントの設定を完了できます。 デバイス アカウントのメール アドレスには、次の用途があります。

-   メールボックスの種類を標準から会議室に変更する。
-   さまざまな Exchange プロパティを変更する。
-   ユーザー アカウントのパスワードを無期限に設定する。

1.  アカウントのメール アドレスを入力し、その値が格納された変数を作成する必要があります。

    ``` syntax
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    値を格納するには、メールボックスからその値を取得します。

    ``` syntax
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    次のコマンドレットを実行して値を出力します。

    ``` syntax
    $strEmail
    ```

    正しいメール アドレスが表示されます。

2.  アカウントを会議室メールボックスに変換する必要があります。そのためには、次の操作を実行します。

    ``` syntax
    Set-Mailbox $strEmail -Type Room
    ```

3.  Surface Hub に対してデバイス アカウントが認証を受けるには、会議室メールボックス アカウントを有効にしてパスワードを設定します。これにより、アカウントをデバイスで使って、ActiveSync を使って会議情報を取得し、Skype for Business にログインします。

    ``` syntax
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定できます。 設定が必要なプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  ここで、AD でプロパティをいくつか設定する必要があります。 そのためには、アカウントのエイリアス ("@" の前に表記されている部分の UPN) が必要です。

    ``` syntax
    $strAlias = “<your device account’s alias>”
    ```

6.  ユーザーを AD で有効にしてから、Surface Hub を使用して認証する必要があります。 次のコマンドを実行します。

    ``` syntax
    Set-ADUser $strAlias -Enabled $True
    ```

7.  パスワードを無期限にする場合は、PowerShell コマンドレットでも設定できます。 詳細については、「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。

    ``` syntax
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a>Skype for Business に対するアカウントの有効化

デバイス アカウントを Skype for Business に対して有効にします。

Skype for Business を有効にするには、環境が次の前提条件を満たしている必要があります。

-   O365 プランでは、Skype for Business Online スタンドアロンプラン2以上が必要です。 プランで会議機能がサポートされている必要があります。
-   Surface Hub のテレフォニーサービスプロバイダーを使用してエンタープライズ Voip (PSTN テレフォニー) が必要な場合は、Skype for Business Online スタンドアロンプラン3が必要です。
-   テナント ユーザーが Exchange メールボックスを持っている必要があります。
-   Surface Hub アカウントには、Skype for Business Online Standalone Plan 2 または Skype for Business Online Standalone Plan 3 ライセンスが必要ですが、Exchange Online のライセンスは必要ありません。

1.  まず、PC でリモート PowerShell セッションを作成します。

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. Surface Hub アカウントレジストラープールを取得する

環境内の `RegistrarPool` パラメーターに使用する値がわからない場合は、次のコマンドレットを使用して、既存の Skype for Business ユーザーから値を取得できます。

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```
    
3. Skype for Business Server に対して Surface Hub アカウントを有効にするには、次のコマンドレットを実行します。

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```

    





