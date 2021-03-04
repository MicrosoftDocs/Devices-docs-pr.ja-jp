---
title: MDM プロバイダーによる設定の管理 (Surface Hub)
description: Microsoft Surface Hub は、IT 管理者が、モバイル デバイス管理 (MDM) ソリューションを使用して、これらのデバイスでポリシーとビジネス アプリケーションを管理するためのエンタープライズ管理ソリューションを提供します。
ms.assetid: 18EB8464-6E22-479D-B0C3-21C4ADD168FE
ms.reviewer: ''
manager: laurawi
keywords: モバイル デバイス管理, MDM, ポリシーの管理, mobile device management, MDM, manage policies
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/03/2021
ms.localizationpriority: medium
ms.openlocfilehash: d09a95d25b4f4ae86d64acd7d7f16f004f991ce3
ms.sourcegitcommit: 5c904229a0257297be7f724c264e484d2c4b5168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "11387497"
---
# <a name="manage-settings-with-an-mdm-provider-surface-hub"></a>MDM プロバイダーによる設定の管理 (Surface Hub)

Surface Hub やその他の Windows 10 デバイスでは、IT 管理者はモバイル デバイス管理 (MDM) プロバイダーを使用して設定やポリシーを管理できます。 組み込みの管理コンポーネントで管理サーバーと通信するため、デバイスに追加のクライアントをインストールする必要はありません。 詳しくは、[Windows 10 でのモバイル デバイス管理に関するページ](https://msdn.microsoft.com/library/windows/hardware/dn914769.aspx)をご覧ください。

Surface Hub は、Microsoft のファースト パーティ MDM プロバイダーで検証されています。
- Microsoft Intune スタンドアロン
- Microsoft Endpoint Configuration Manager を使用したオンプレミス MDM

MDM プロトコルで Windows 10と通信可能な任意のサード パーティ製 MDM プロバイダーを使用して、Surface Hub を管理することもできます。

## <a name="enroll-a-surface-hub-into-mdm"></a><a href="" id="enroll-into-mdm"></a>MDM への Surface Hub の登録
Surface Hubs は、一括登録、手動登録、または自動登録を使用して登録できます。

### <a name="bulk-enrollment"></a>一括登録
**一括登録を構成するには**
- Surface Hub は、[Provisioning CSP](https://msdn.microsoft.com/library/windows/hardware/mt203665.aspx) による MDM への一括登録をサポートしています。 詳しくは、[Windows 10 での一括登録に関するページ](https://msdn.microsoft.com/library/windows/hardware/mt613115.aspx)をご覧ください。<br>
または
- オンプレミスの Microsoft Endpoint Configuration Manager インフラストラクチャがある場合は、「Microsoft Endpoint Configuration Manager でオンプレミスのモバイル デバイス管理を使用してデバイスを一括登録する方法」 [を参照してください](https://docs.microsoft.com/configmgr/mdm/deploy-use/bulk-enroll-devices-on-premises-mdm)。

### <a name="manual-enrollment"></a>手動登録
**手動登録を構成するには**
1. Surface Hub で **[設定]** を開きます。
2. メッセージが表示されたら、デバイスの管理者資格情報を入力します。
3. **[このデバイス]** を選択し、**[デバイス管理]** に移動します。
4. **[デバイス管理]** で、**[+ デバイス管理]** を選択します。
5. ダイアログに表示されう指示に従って、MDM プロバイダーに接続します。

### <a name="automatic-enrollment-via-azure-active-directory-join"></a>Azure Active Directory 参加による自動登録

Surface Hub では、デバイスを Azure Active Directory に参加して Intune に自動的に登録する機能がサポートされています。 

最初の手順は、MDM の自動登録を設定します。 「Windows [10 の自動登録を有効にする」を参照してください](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)。

次に、初回実行時にデバイスがセットアップされている場合は、Azure Active Directory に参加するオプションを選択し、「このデバイスの管理者を設定する」ページ[を参照してください](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub#set-up-admins-for-this-device-page)。

## <a name="manage-surface-hub-settings-with-mdm"></a>MDM による Surface Hub の設定の管理

MDM を使用して、一部の [Surface Hub CSP の設定](#supported-surface-hub-csp-settings)や一部の [Windows 10 の設定](#supported-windows-10-settings)を管理できます。 使用する MDM プロバイダーによって、組み込みのユーザー インターフェイスを使用するか、またはカスタム SyncML を展開して、これらの設定項目を設定できます。 Microsoft Intune と Microsoft Endpoint Configuration Manager は、Surface Hub のポリシー テンプレートの作成に役立つ組み込みのエクスペリエンスを提供します。 SyncML を作成して展開する方法については、MDM プロバイダーのドキュメントをご覧ください。

### <a name="supported-surface-hub-csp-settings"></a>サポートされている Surface Hub CSP の設定

MDM を使用して、次の表に示されている Surface Hub の設定を構成できます。 この表は、設定が Microsoft Intune、Microsoft Endpoint Configuration Manager、または SyncML でサポートされる場合を識別します。

詳しくは、[Surface Hub 構成サービス プロバイダーに関するページ](https://msdn.microsoft.com/library/windows/hardware/mt608323)をご覧ください。 


|                                     設定                                      |                                                    SurfaceHub CSP のノード                                                    |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|                                メンテナンス時間                                 |                        MaintenanceHoursSimple/Hours/StartTime <br> MaintenanceHoursSimple/Hours/Duration                         |                       対応                        |                       はい                       |             対応             |
|              モーション センサーを使用して画面を自動的にオンにする               |                                                 InBoxApps/Welcome/AutoWakeScreen                                                 |                       対応                        |                       はい                       |             対応             |
|                      ワイヤレス プロジェクションで PIN を要求する                       |                                             InBoxApps/WirelessProjection/PINRequired                                             |                       対応                        |                       はい                       |             対応             |
|                            ワイヤレス プロジェクションを有効にする                            |                                               InBoxApps/WirelessProjection/Enabled                                               |                       対応                        | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                 ワイヤレス プロジェクションに Miracast チャネルを使用する                  |                                               InBoxApps/WirelessProjection/Channel                                               |                       対応                        | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|              Operations Management Suite ワークスペースに接続する               |                                         MOMAgent/WorkspaceID <br> MOMAgent/WorkspaceKey                                          |                       対応                        | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                         ようこそ画面の背景画像                          |                                             InBoxApps/Welcome/CurrentBackgroundPath                                              |                       対応                        | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               ようこそ画面に表示される会議情報                |                                               InBoxApps/Welcome/MeetingInfoOption                                                |                       対応                        | 対応<br> [カスタム設定を使用します。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager |             対応             |
|                      ワイヤレス プロジェクションのフレンドリ名                       |                                                     Properties/FriendlyName                                                      | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                   デバイス アカウント                                                 | DeviceAccount/*`<name_of_policy>`* <br> [SurfaceHub CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)を参照。 |                        未対応                        |                       いいえ                        |             対応             |
|                               Skype ドメインを指定する                               |                                              InBoxApps/SkypeForBusiness/DomainName                                               |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               プロジェクションが初期化されたときに接続アプリを自動起動する               |                                                   InBoxApps/Connect/AutoLaunch                                                   |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                                既定のボリュームを設定する                                |                                                     Properties/DefaultVolume                                                     |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                                画面のタイムアウトを設定する                                |                                                     Properties/ScreenTimeout                                                     |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                               セッションのタイムアウトを設定する                                |                                                    Properties/SessionTimeout                                                     |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                                スリープ タイムアウトの設定                                 |                                                     Properties/SleepTimeout                                                      |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                   画面のアイドル状態後にセッションを再開できるようにする                   |                                                  Properties/AllowSessionResume                                                   |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|             デバイス アカウントをプロキシ認証に使用できるようにする             |                                                  Properties/AllowAutoProxyAuth                                                   |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
| スケジュール設定済みの会議の出席者とのサインイン ダイアログの自動作成を無効にする |                                               Properties/DisableSignInSuggestions                                                |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|              スタート メニューで「会議とファイル」機能を無効にする               |                                              Properties/DoNotShowMyMeetingsAndFiles                                              |                    対応 </br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                     802.1x ワイヤード (有線) 認証用 LanProfile を設定する                     |                                                         Dot3/LanProfile                                                          | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                    802.1x ワイヤード (有線) 認証用 EapUserData を設定する                     |                                                         Dot3/EapUserData                                                         | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

### <a name="supported-windows-10-settings"></a>サポートされている Windows 10 の設定

Surface Hub に固有の設定に加え、多くの設定がすべての Windows 10 デバイスに共通です。 これらの設定については、[構成サービス プロバイダー リファレンスに関するページ](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)をご覧ください。 

以下の表に、Surface Hub で検証済みの Windows 10 の設定に関する情報を示します。 セキュリティ、ブラウザー、Windows Update、Windows Defender、リモート再起動、証明書、ログの各領域の設定に関する表があります。 各テーブルは、設定が Microsoft Intune、Microsoft Endpoint Configuration Manager、または SyncML でサポートされる場合を識別します。

#### <a name="security-settings"></a>セキュリティの設定

|      設定       |                                            詳細                                             |                                                                          CSP リファレンス                                                                           |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|--------------------|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|  Bluetooth を許可する   |                      Bluetooth 周辺機器をサポートするにはこれを有効にしておいてください。                       |                   [Connectivity/AllowBluetooth](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Connectivity_AllowBluetooth)                   |                    対応 <br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
| Bluetooth ポリシー | Bluetooth デバイス名、広告のブロック、検出、自動ペアリングを設定するために使用します。 |                     Bluetooth/*`<name of policy>`* <br> [Policy CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)を参照                      |                    対応 <br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|    カメラを使用する    |                           Skype for Business 用にこれを有効にしておいてください。                            |                            [Camera/AllowCamera](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Camera_AllowCamera)                            |                    対応 <br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|   位置情報を許可する   |                        マップなどのアプリをサポートするためにこれを有効にしておいてください。                         |                          [System/AllowLocation](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#System_AllowLocation)                          |                   対応 <br> .                    | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|  利用統計情報を許可する   |                    Microsoft が Surface Hub を改善できるようにこれを有効にしておいてください。                    |                         [System/AllowTelemetry](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#System_AllowTelemetry)                         |                    対応 <br>                     | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|  USB ドライブを許可する  |                     Surface Hub で USB ドライブをサポートできるようにこれを有効にしておいてください。                     | [System/AllowStorageCard](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#system-allowstoragecard) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。 

#### <a name="browser-settings"></a>ブラウザーの設定

|                          設定                          |                                                                        詳細                                                                        |                                                                             CSP リファレンス                                                                              |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|                         ホーム ページ                         |                                               Microsoft Edge で既定のホーム ページを構成する場合に使用します。                                               |                                [Browser/Homepages](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_Homepages)                                | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                       Cookie を使用する                       |                    Surface Hub は、セッションの終了時に自動的に Cookie を削除します。 セッション内で Cookie をブロックするには、これを使用します。                     |                             [Browser/AllowCookies](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowCookies)                             | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                   開発者ツールを許可する                   |                                                   ユーザーが F12 開発者ツールを使用することを禁止する場合に使用します。                                                   |                      [Browser/AllowDeveloperTools](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowDeveloperTools)                      | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                    トラッキング拒否を許可する                     |                                                          Do Not Track ヘッダーを有効にするために使用します。                                                          |                          [Browser/AllowDoNotTrack](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowDoNotTrack)                          | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                       ポップアップを許可する                       |                                                         ポップアップ ブラウザー ウィンドウをブロックするために使用します。                                                          |                              [Browser/AllowPopups](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowPopups)                              | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                 検索候補を許可する                  |                                                  アドレス バーの検索候補をブロックするために使用します。                                                  |       [Browser/AllowSearchSuggestionsinAddressBar](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowSearchSuggestionsinAddressBar)       | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|                     SmartScreen Windows Defender許可する                     |                                                       SmartScreen を有効にするには、これを有効Windows Defenderしてください。                                                       |                         [Browser/AllowSmartScreen](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowSmartScreen)                         | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
| Web サイトの smartScreen Windows Defenderを無視する |     セキュリティを強化するには、ユーザーが SmartScreen の警告を無視Windows Defenderし、悪意のある可能性のある Web サイトへのアクセスをブロックします。     |         [Browser/PreventSmartScreenPromptOverride](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_PreventSmartScreenPromptOverride)         | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|  ファイルの SmartScreen Windows Defenderを無視する   | セキュリティを強化するには、ユーザーが SmartScreen の警告を無視Windows Defender停止し、Microsoft Edge から未確認のファイルをダウンロードできません。 | [Browser/PreventSmartScreenPromptOverrideForFiles](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_PreventSmartScreenPromptOverrideForFiles) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="windows-update-settings"></a>Windows Update の設定

|                      設定                      |                                                                                                           詳細                                                                                                            |                                                                    CSP リファレンス                                                                    |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Current Branch または Current Branch for Business を使用する |                                                       Windows Update for Business を構成するために使用します。[Windows Update](manage-windows-updates-for-surface-hub.md) に関するページをご覧ください。                                                       |            [Update/BranchReadinessLevel](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_BranchReadinessLevel)             | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               機能更新プログラムを延期する               |                                                                                                          上記を参照してください。                                                                                                          | [Update/ DeferFeatureUpdatesPeriodInDays](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_DeferFeatureUpdatesPeriodInDays) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               品質更新プログラムを延期する               |                                                                                                          上記を参照してください。                                                                                                          | [Update/DeferQualityUpdatesPeriodInDays](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_DeferQualityUpdatesPeriodInDays)  | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               機能更新プログラムの一時停止               |                                                                                                          上記を参照してください。                                                                                                          |             [Update/PauseFeatureUpdates](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_PauseFeatureUpdates)              | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               品質更新プログラムの一時停止               |                                                                                                          上記を参照してください。                                                                                                          |             [Update/PauseQualityUpdates](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_PauseQualityUpdates)              | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|           WSUS を使用するようデバイスを構成する            |                                            Windows Update ではなく WSUS に Surface Hub を接続するために使用します。「[Windows 更新プログラム](manage-windows-updates-for-surface-hub.md)」をご覧ください。                                             |                [Update/UpdateServiceUrl](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_UpdateServiceUrl)                 | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|               配信の最適化               | ピア ツー ピアのコンテンツ共有を使用して、更新時の帯域幅の問題を緩和します。 詳しくは、[Windows 10 更新プログラムの配信の最適化の構成](https://technet.microsoft.com/itpro/windows/manage/waas-delivery-optimization)」をご覧ください。 |         DeliveryOptimization/*`<name of policy>`* <br> [Policy CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)を参照          | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="windows-defender-settings"></a>Windows Defender の設定

|      設定      |                                              詳細                                               |                                                     CSP リファレンス                                                      |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|-------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Defender ポリシー |            スケジュールされたスキャン時刻を含め、Defender のさまざまな設定を構成するために使用します。            | Defender/*`<name of policy>`* <br> [Policy CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)を参照 | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
|  Defender の状態  | Defender スキャンを開始し、セキュリティ インテリジェンスの更新を強制し、検出された脅威に対してクエリを実行するために使用します。 |                   [Defender CSP](https://msdn.microsoft.com/library/windows/hardware/mt187856.aspx)                    |                       はい                        |                       はい                       |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="remote-reboot"></a>リモート再起動

|                       設定                        |                                                          詳細                                                          |                                                             CSP リファレンス                                                             |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|            デバイスをすぐに再起動する。             | サポート コストを最小限に抑えるために Azure Monitor と組み合わせて使用します [。「Monitor your Microsoft Surface Hub」を参照してください](monitor-surface-hub.md)。 |        ./Vendor/MSFT/Reboot/RebootNow <br> [Reboot CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx)を参照        |                       対応                        |                       いいえ                        |             対応             |
|    スケジュールされた日時にデバイスを再起動する    |                                                        上記を参照してください。                                                         |     ./Vendor/MSFT/Reboot/Schedule/Single <br> [Reboot CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx)を参照     | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |
| 毎日スケジュールされた日時にデバイスを再起動する |                                                        上記を参照してください。                                                         | ./Vendor/MSFT/Reboot/Schedule/DailyRecurrent <br> [Reboot CSP に関するページ](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx)を参照 | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="install-certificates"></a>証明書のインストール

|             設定             |                           詳細                            |                                           CSP リファレンス                                            |                                                         Intune での<br>サポート                                                          |                                                                  Configuration Manager での<br>サポート                                                                  | SyncML での<br>サポート\* |
|---------------------------------|--------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| 信頼された CA 証明書のインストール | 信頼されたルート証明書と中間 CA 証明書を展開するために使用します。 | [RootCATrustedCertificates CSP](https://msdn.microsoft.com/library/windows/hardware/dn904970.aspx) | 対応。 <br> 「[Intune 証明書プロファイルを構成する](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles)」をご覧ください。 | 対応。 <br> 「Microsoft [Endpoint Configuration Manager で証明書プロファイルを作成する方法」を参照してください](https://docs.microsoft.com/configmgr/protect/deploy-use/create-certificate-profiles)。 |             対応             |

<!--
| Install client certificates  | Use to deploy Personal Information Exchange (.pfx, .p12) certificates. | [ClientCertificateInstall CSP](https://msdn.microsoft.com/library/windows/hardware/dn920023.aspx) | Yes. <br> See [How to Create and Deploy PFX Certificate Profiles in Intune Standalone](https://blogs.technet.microsoft.com/karanrustagi/2016/03/16/want-to-push-a-certificate-to-device-but-cant-use-ndes-continue-reading/). | Yes. <br> See [How to create PFX certificate profiles in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/protect/deploy-use/create-pfx-certificate-profiles). | Yes |
-->
\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="collect-logs"></a>ログを収集する

|     設定      |                      詳細                       |                                     CSP リファレンス                                      | Intune での<br>サポート | Configuration Manager での<br>サポート | SyncML での<br>サポート\* |
|------------------|----------------------------------------------------|----------------------------------------------------------------------------------------|---------------------------|------------------------------------------|-----------------------------|
| ETW ログの収集 | リモートで Surface Hub から ETW ログを収集するために使用します。 | [DiagnosticLog CSP](https://msdn.microsoft.com/library/windows/hardware/mt219118.aspx) |            未対応             |                    いいえ                    |             対応             |

<!--
| Collect security auditing logs | Use to remotely collect security auditing logs from Surface Hub. | SecurityAuditing node in [Reporting CSP](https://msdn.microsoft.com/library/windows/hardware/mt608321.aspx) | No | No | Yes |-->
\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="set-network-quality-of-service-qos-policy"></a>ネットワーク サービス品質 (QoS) ポリシーの設定

|        設定         |                                                            詳細                                                             |                                                    CSP リファレンス                                                     |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| ネットワーク QoS ポリシーの設定 | ネットワーク トラフィックに対して、一連のアクションを実行する QoS ポリシーを設定するために使用します。 これは、Skype ネットワーク パケットの優先順位付けに便利です。 | [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="set-network-proxy"></a>ネットワーク プロキシの設定

|      設定      |                               詳細                               |                                                CSP リファレンス                                                 |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|-------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| ネットワーク プロキシの設定 | イーサネットと Wi-Fi 接続に対してプロキシ サーバーを構成するために使用します。 | [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

#### <a name="configure-start-menu"></a>スタート メニューの構成

|       設定        |                                                                       詳細                                                                        |                                                        CSP リファレンス                                                         |            Intune での<br>サポート             |    Configuration Manager での<br>サポート     | SyncML での<br>サポート\* |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| スタート メニューの構成 | スタート メニューに表示するアプリを構成するために使用します。 詳しくは、「[Surface Hub のスタート メニューの構成](surface-hub-start-menu.md)」をご覧ください。 | [ポリシー CSP: Start/StartLayout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start#start-startlayout) | 対応 <br> [カスタム ポリシーを使用。](#example-manage-surface-hub-settings-with-microsoft-intune) | 対応<br> [カスタム設定を使用。](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             対応             |

\*SyncML でサポートされている設定は、Windows 構成デザイナー プロビジョニング パッケージでも構成できます。

### <a name="generate-oma-uris-for-settings"></a>設定の OMA URI を生成する 
設定の OMA URI を使用して Intune でカスタム ポリシーを作成するか、Microsoft Endpoint Configuration Manager でカスタム設定を作成する必要があります。

**CSP ドキュメントの任意の設定について OMA URI を生成するには**
1. CSP ドキュメントで、CSP のルート ノードを識別します。 一般的には、次のようになっています。 `./Vendor/MSFT/<name of CSP>` <br>
*たとえば、[SurfaceHub CSP](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx) のルート ノードは `./Vendor/MSFT/SurfaceHub` です。*
2. 使用する設定のノード パスを識別します。 <br>
*たとえば、ワイヤレス プロジェクションを有効にする設定のノード パスは、`InBoxApps/WirelessProjection/Enabled` です。*
3. ルート ノードにノード パスを追加して、OMA URI を生成します。 <br>
*たとえば、ワイヤレス プロジェクションを有効にする設定の OMA URI は、`./Vendor/MSFT/SurfaceHub/InBoxApps/WirelessProjection/Enabled` です。*

データ型についても、CSP のドキュメントに記載されています。 最も一般的なデータ型は次のとおりです。
- char (文字列)
- int (整数)
- bool (ブール値)


## <a name="example-manage-surface-hub-settings-with-microsoft-intune"></a>例: Microsoft Intune で Surface Hub の設定を管理する

Microsoft Intune を使用して、Surface Hub の設定を管理できます。 カスタム設定の場合は、[Microsoft Intune でカスタム デバイス設定を構成する方法](https://docs.microsoft.com/intune/custom-settings-configure)に関するページの手順に従ってください。 **[プラットフォーム]** で **[Windows 10 以降]** を選択し、**[プロファイルの種類]** で **[デバイスの制限 (Windows 10 Team)]** を選択します。



## <a name="example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager"></a>例: Microsoft Endpoint Configuration Manager を使用して Surface Hub 設定を管理する
Configuration Manager は、Surface Hub を含め、Configuration Manager クライアントが管理する必要ない最新のデバイスの管理をサポートしています。 Configuration Manager を使用して組織内の他のデバイスを管理している場合は、引き続き Configuration Manager コンソールを Surface Hubs を管理するための単一の場所として使用できます。

> [!NOTE]
> これらの手順は、Configuration Manager の現在のブランチに基づいて行います。

**Surface Hub の設定の構成項目を作成するには**

1. Configuration Manager コンソールの **[資産とコンプライアンス]** ワークスペースで、**[概要]** > **[コンプライアンス設定]** > **[構成項目]** の順にクリックします。
2. **[ホーム]** タブの **[作成]** グループで、**[構成項目の作成]** をクリックします。
3. 構成項目の作成ウィザードの **[全般]** ページで、構成項目の名前と必要に応じて説明を指定します。
4. **[Configuration Manager クライアントなしで管理されるデバイスの設定]** で、**[Windows 8.1 と Windows 10]** を選択し、**[次へ]** をクリックします。

    ![UI の例](images/configmgr-create.png)
5. **[サポートされているプラットフォーム]** ページで、**[Windows 10]** を展開し、**[すべての Windows 10 Team 以降]** を選択します。 その他の Windows プラットフォームの選択を解除し、**[次へ]** をクリックします。

    ![プラットフォームの選択](images/configmgr-platform.png)
7. **[デバイス設定]** ページで、**[デバイス設定グループ]** の **[Windows 10 Team]** を選択します。


8. **[Windows 10 Team]** ページで、必要な設定を構成します。

    ![Windows 10 Team](images/configmgr-team.png)
9. [Windows 10 Team] ページにない設定を管理するには、カスタム設定を作成する必要があります。 **[デバイス設定]** ページで、**[既定の設定グループに含まれない追加の設定を構成する]** チェック ボックスをオンにします。

    ![追加設定](images/configmgr-additional.png)
10. **[追加設定]** ページで、**[追加]** をクリックします。
11. **[設定の参照]** ダイアログで、**[設定の作成]** をクリックします。
12. **[設定の作成]** ダイアログの **[全般]** タブで、カスタム設定の名前と必要に応じて説明を指定します。
13. **[設定の種類]** で、**[OMA URI]** を選択します。
14. フォームに入力して新しい設定を作成し、**[OK]** をクリックします。

    ![OMA URI 設定](images/configmgr-oma-uri.png)
15. **[設定の参照]** ダイアログの **[利用可能な設定]** で、作成した新しい設定を選択し、**[選択]** をクリックします。
16. **[規則の作成]** ダイアログで、フォームに入力して設定の規則を指定し、**[OK]** をクリックします。
17. 構成項目に追加する各カスタム設定について、手順 9 ～ 15 を繰り返します。
18. 作業が完了したら、**[設定の参照]** ダイアログで、**[閉じる]** をクリックします。
19. ウィザードを完了します。 <br> 新しい構成項目は、**[資産とコンプライアンス]** ワークスペースの **[構成項目]** ノードで表示できます。

詳細については、「Create configuration [items for Windows 8.1 and Windows 10 devicesmanaged](https://docs.microsoft.com/configmgr/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)without the Microsoft Endpoint Configuration Manager client 」を参照してください。

## <a name="related-topics"></a>関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)











