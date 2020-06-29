---
title: Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開 (Surface Hub)
description: このトピックでは、クラウド コネクタ エディションまたは Skype for Business 2015 のプールを使ったオンプレミス PSTN 接続によって、Skype for Business のクラウド PBX を有効にする方法について説明します。
keywords: ハイブリッド展開, Skype Hybrid Voice
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 08349a7d2decb4d4b053cb03fc95808b49d4f2f0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836430"
---
# Skype Hybrid Voice 環境を使ったオンラインまたはハイブリッド展開 (Surface Hub)

このトピックでは、クラウド コネクタ エディションまたは Skype for Business 2015 のプールを使ったオンプレミスの公衆交換電話網 (PSTN) 接続によって、Skype for Business のクラウド PBX を有効にする方法について説明します。 このオプションでは、 クラウド上に Skype for Business のホーム プールと Exchange サーバーがあり、それらが Skype for Business 2015 またはクラウド コネクタ エディションを実行するオンプレミス プールを使って PSTN で接続されています。 詳しくは、[さまざまなクラウド PBX オプション](https://technet.microsoft.com/library/mt612869.aspx)に関するページをご覧ください。  

Skype for Business のクラウド PBX をいずれかのハイブリッド音声オプションで展開している場合は、次の手順に従って、Surface Hub のルーム アカウントを有効にします。 最初に通常のユーザー アカウントを作成し、すべてのハイブリッド音声オプションおよび電話番号を割り当ててから、アカウントをルーム アカウントに変換することが重要です。 この順序に従わない場合、ハイブリッド電話番号を割り当てることはできません。  

>[!WARNING]
>Hybrid Voice の構成前にアカウントを作成した場合 (Enable-CSMeetingRoom コマンドを実行)、必要なハイブリッド音声パラメーターを構成できません。 以前に構成されたアカウントのハイブリッド音声パラメーターを構成するか、または電話番号を再構成するには、E5 または E3 + クラウド PBX アドオン ライセンスを削除し、次の手順に従います (手順 3 から)。

1. Surface Hub の新しいユーザー アカウントを作成します。 この例で <strong> は </strong> 、surfacehub2@adatum.com を使います。 アカウントはローカル Active Directory で作成し、クラウドに同期するか、クラウドで直接作成することができます。 

    ![新しいオブジェクト - ユーザー](images/new-user-hybrid-voice.png)

2. **[パスワードを無期限にする]** を選択します。 これは、Surface Hub デバイスにとって重要です。

   ![パスワードを無期限にする](images/new-user-password-hybrid-voice.png)

3. Office 365 では、**E5** ライセンスまたは **E3 および Cloud PBX** アドオンを、ルーム用に作成したユーザー アカウントに追加します。 これは、Hybrid Voice が機能するために必要です。

   ![製品ライセンスの追加](images/product-license-hybrid-voice.png)

4. ルームのユーザー アカウントが Skype for Business Online に表示されるまで、約 15 分間待ちます。

5. Skype for Business Online でルームのユーザー アカウントが作成されたら、次のコマンドレットを実行して、Skype for Business のリモート PowerShell での Hybrid Voice に対してアカウントを有効にします。

   ```
   Set-csuser surfacehub2@adatum.com EnterpriseVoiceEnabled $true -HostedVoiceMail $true -onpremlineuri tel:+15005000102
   ```
    
6. Surface Hub からテスト通話を行って、Hybrid Voice の呼び出しフローを検証します。

7. PC でリモート PowerShell セッションを開始し、次のコマンドレットを実行して Exchange に接続します。

   ```
   Set-ExecutionPolicy Unrestricted
   $cred=Get-Credential -Message "Please use your Office 365 admin credentials"
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/ps1-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```
    
8. セッションを確立した後、次のコマンドレットを実行してルームのユーザー アカウントを変更し、**RoomMailboxAccount** として有効にします。 これにより、アカウントが Surface Hub で認証できるようになります。

   ```
   Set-Mailbox surfacehub2@adatum.com -Type Room
   Set-Mailbox surfacehub2@adatum.com -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
    
9. メールボックスをセットアップしたら、新しい Exchange ActiveSync ポリシーを作成するか、互換性のある既存のポリシーを使用する必要があります。

   Surface Hub は、**PasswordEnabled** プロパティが **False** に設定された ActiveSync ポリシーが適用されているデバイス アカウントとのみ互換性があります。 このポリシーが正しく設定されていない場合、Surface Hub の Exchange サービス (メール、カレンダー、および会議への参加) が有効になりません。
    
   互換性のあるポリシーをまだ作成していない場合は、次のコマンドレットを使用します (このコマンドレットは、"Surface Hubs" というポリシーを作成します)。 ポリシーを作成すると、同じポリシーを他のデバイス アカウントに適用できます。

   ```
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false
   ```
    
   互換性のあるポリシーを作成したら、デバイス アカウントにポリシーを適用する必要があります。 ただし、ポリシーはユーザー アカウントにのみ適用でき、リソース メールボックスには適用できません。 次のコマンドレットを実行して、メールボックスを変換して種類をユーザーにし、ポリシーを適用してから、変換でメールボックスに戻す必要があります (アカウントを有効に戻し、パスワードをもう一度設定することが必要になる場合もあります)。
    
   ```
   Set-Mailbox surfacehub2@adatum.com -Type Regular
   Set-CASMailbox surfacehub2@adatum.com -ActiveSyncMailboxPolicy $easPolicy.id
   Set-Mailbox surfacehub2@adatum.com -Type Room
   $credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
   Set-Mailbox surfacehub2@adatum.com -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```
    
10. 会議エクスペリエンスを向上させるには、さまざまな Exchange プロパティをデバイス アカウントに設定する必要があります。 設定できるプロパティについては、「[Exchange プロパティ](exchange-properties-for-surface-hub-device-accounts.md)」をご覧ください。 次のコマンドレットは、Exchange プロパティを設定する例を示しています。

    ```
    Set-CalendarProcessing surfacehub2@adatum.com -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing surfacehub2@adatum.com -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

11. Skype for Business Online で、メールボックスを会議デバイスとして有効にします。 アカウントを会議デバイスとして有効にする、次のコマンドレットを実行します。 

    ```
    Get-CsTenant | select registrarpool
    Enable-CsMeetingRoom surfacehub2@adatum.com -RegistrarPool  'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
    ```
    
    このコマンドレットを実行すると、次の図に示すように、ユーザーは会議室にいるかどうかを尋ねられます。 **[はい]** を選択すると、マイクとスピーカーがミュートされます。

    ![](images/adjust-room-audio.png)


    
この時点で、Hybrid Voice を含めてルーム アカウントが完全に構成されます。 Skype をオンプレミスで使用する場合は、説明や位置情報などの追加の属性をオンプレミスで構成できます。 Skype Online でルームを作成する場合は、これらのパラメーターをオンラインで設定できます。 

デバイスは、次の図のようにユーザーに表示されます。


![](images/select-room-hybrid-voice.png)
