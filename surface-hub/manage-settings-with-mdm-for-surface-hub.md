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
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 4308ce1ea8ff382dc15706e68d2d706d0fd33f5f
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576757"
---
# <a name="manage-surface-hub-with-an-mdm-provider"></a>MDM プロバイダーを使用して Surface Hub を管理する

Surface Hub IT 管理者は、モバイル デバイス管理 (MDM) プロバイダー (MDM) プロバイダー (モバイル デバイス管理など) を使用して設定とポリシーを管理Microsoft Intune。 Surface Hub管理サーバーと通信するための組み込みの管理コンポーネントがあります。 デバイスに追加のクライアントをインストールする必要はありません。

## <a name="enrolling-surface-hub-into-mdm-management"></a>MDM 管理Surface Hub登録する 

Surface を手動または自動登録Microsoft Intune、他の MDM プロバイダーに登録できます。

### <a name="manual-enrollment"></a>手動登録

1. アプリを**開設定**ローカル管理者としてサインインします。 [**デバイス**  >  **Surface Hub] を選択し**、[+デバイス管理]**を選択します**。
2. MDM プロバイダーに使用するアカウントでサインインするように求めるメッセージが表示されます。 認証後、デバイスは MDM プロバイダーに自動的に登録されます。

> [!TIP]
> Intune を使用している場合にサーバー アドレスが検出されない場合は、 **次の**manage.microsoft.com。
   
> [!NOTE]
> MDM 登録では、認証用に提供されたアカウントの詳細が使用されます。 このアカウントには、Intune ライセンス (またはサード パーティの MDM プロバイダーで構成された同等の登録の省略) と同様に、Windows デバイスを登録するためのアクセス許可が必要です。

### <a name="auto-enrollment--azure-ad-affiliated"></a>自動登録 - Azure AD関連付け

初期セットアップ プロセス中に、Intune 自動登録が有効になっている Azure Active Directory (AD) テナントで Surface Hub を関連付けすると、デバイスは自動的に Intune に登録されます。 詳細については、「Intune 登録方法」[を参照して、デバイスWindowsしてください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods)。 Surface Hub を Intune の "対応デバイス" にするには、Azure AD 連携と Intune の自動登録が必要です。 

## <a name="manage-surface-hub-windows-10-team-settings-with-intune"></a>Intune でSurface Hub Windows 10 Team設定を管理する

Intune および他の MDM プロバイダーのポリシー設定管理の基礎ブロックは、XML ベースの Open Mobile Alliance-Device管理 (OMA-DM) プロトコルです。 Windows 10 AccountManagement CSP、DeviceStatus CSP、WiFi-CSP など、多くの利用可能な構成サービス プロバイダー (CSP) のいずれかを介して OMA-DM XML を実装します。 完全な一覧については、次のセクションでサポート[されている MICROSOFT SURFACE HUB を参照してください](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)。

Microsoft Intune MDM プロバイダーは CSP を使用して、構成プロファイル内でポリシー設定を構成できる UI を提供します。 Intune では、Surface Hub CSP を組み込みのプロファイル (デバイス制限 **(Windows 10 Team))** に使用して、近接範囲内で近くに移動するたびに Surface Hub が "目を覚ます" のを防ぐなどの基本的な設定を構成できます。 Intune の組み込みプロファイルの外部でハブの設定と機能を管理するには、次に示すようにカスタム プロファイルを使用 [する必要があります](#create-custom-configuration-profile)。 

要約すると、Intune 内でポリシー設定を構成および管理するオプションには、次のものが含まれます。 
 
- **デバイス制限プロファイルを作成します。** Intune の組み込みのプロファイルを使用し、Intune UI で直接設定を構成します。 「 [デバイス制限プロファイルの作成」を参照してください](#create-device-restriction-profile)。
- **デバイス構成プロファイルを作成します。**  Microsoft Defender やセキュリティ証明書などの特定の機能またはテクノロジに焦点を当てたテンプレートを選択します。 「 [デバイス構成プロファイルの作成」を参照してください](#create-device-configuration-profile)。
- **カスタム構成プロファイルを作成します。**  OMA Uniform Resource IDENTIFIER (OMA URI) を使用して管理の範囲を、OMA でサポートされている任意の[CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)から拡張Microsoft Surface Hub。 「カスタム [構成プロファイルの作成」を参照してください](#create-custom-configuration-profile)。

> [!NOTE]
> プロファイルは、登録済みデバイスを含むデバイス グループに割り当Surface Hub必要があります。

## <a name="create-device-restriction-profile"></a>デバイス制限プロファイルの作成

1. 管理センターにサインイン[**Microsoft エンドポイント マネージャー、[**](https://endpoint.microsoft.com/)デバイス****  >  **構成プロファイルプロファイルの作成**  >  **+** **] を選択します**。
2. [**プラットフォーム] で**、[Windows 10**以降] を選択します。** >
3. [****Profile**type] で、[** テンプレート]**を選択**し、[デバイスの制限] **(Windows 10 Team)**
4. [作成 **] を**選択し、名前を追加し、[次へ] を **選択します。**
6. アプリとエクスペリエンス、Azure 運用分析情報、メンテナンス、セッション、ワイヤレスプロジェクションのカテゴリで、Surface Hub のデバイス制限設定を事前に設定して参照して選択できます。 次の図に示す例は、4 時間のメンテナンス ウィンドウと、画面、スリープ、セッション再開の 15 分のタイムアウトを指定します。

     ![Intune デバイスSurface Hubプロファイルを使用してユーザー設定を構成する](images/sh-device-restrictions.png)

プロファイルの作成と管理の詳細については、「ポリシーを使用してデバイス機能を制限する」を参照[Microsoft Intune。](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-configure#create-the-profile)
 
デバイスの機能と設定を管理するSurface Hub詳細については、「Surface Hub Windows 10 Teamデバイスの制限」[を参照Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10-teams)
 

## <a name="create-device-configuration-profile"></a>デバイス構成プロファイルの作成

1. 管理センターにサインイン[**Microsoft エンドポイント マネージャー、[**](https://endpoint.microsoft.com/)デバイス構成プロファイル] ****+ [プロファイルの  >  **作成**  >  **] を選択します**。
2. [**プラットフォーム] で**、[Windows 10**以降] を選択します。** >
3. [**プロファイルの種類]** で 、[**テンプレート] を**選択し、次のテンプレートから選択します。Surface Hub。

    - デバイスの制限 (Windows 10 Team) (前のセクションで[説明したように](#create-device-restriction-profile))。
    - Microsoft Defender for Endpoint (Windows 10 デスクトップ)
    - PKCS 証明書
    - PKCS インポートされた証明書
    - SCEP 証明書
    - 信頼できる証明書

## <a name="create-custom-configuration-profile"></a>カスタム構成プロファイルの作成

管理の範囲を拡張するには、OMA URI を使用してカスタム プロファイルを作成し、このプロファイルでサポートされている[MICROSOFT SURFACE HUB。](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport) [](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure) CSP の各設定には、Intune でカスタム構成プロファイルを使用して設定できる対応する OMA-URI があります。 サポートされている CSP の詳細については、Surface Hubリソースを参照できます。 

- [構成サービス プロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Microsoft Surface Hub でサポートされている Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)
- [SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
> [!NOTE]
> [SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)の設定を使用してデバイス アカウントを管理するには、Intune では現在使用できません。サードパーティの MDM プロバイダーを使用する必要があります。

CSP ベースのポリシー設定を実装するには、まず OMA URI を生成してから、Intune のカスタム構成プロファイルに追加します。

### <a name="generate-oma-uri-for-target-setting"></a>ターゲット設定の OMA URI を生成する
 
任意の設定の OMA URI を生成するには、次の方法を実行します。

1. CSP の [ドキュメントで、CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)のルート ノードを識別します。 一般に、これは **./Vendor/MSFT/ <name of CSP> のように見えます**。 
    - **例:**[SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)のルート ノードは **./Vendor/MSFT/SurfaceHub です**。
2. 使用する設定のノード パスを識別します。 
    - **例:** ワイヤレスプロジェクションを有効にする設定のノード パスは **、InBoxApps/WirelessProjection/Enabled です**。
3. ルート ノードにノード パスを追加して、OMA URI を生成します。 
    - **例:** ワイヤレスプロジェクションを有効にする設定の OMA URI は **、./Vendor/MSFT/SurfaceHub/InBoxApps/WirelessProjection/Enabled です。**
4. データ型についても、CSP のドキュメントに記載されています。 最も一般的なデータ型は次のとおりです。
    - char (文字列)
    - int (整数)
    - bool (ブール値)

### <a name="add-oma-uri-to-custom-configuration-profile"></a>カスタム構成プロファイルに OMA URI を追加する

1. [エンドポイント マネージャー] で、[**デバイス**  >  **構成プロファイル] [プロファイル**  >  **の作成] を選択します**。
2. [プラットフォーム] で、[Windows 10**以降] を選択します。** [プロファイル] で、[カスタム] **を**選択し、[作成] を **選択します。**
3. 名前とオプションの説明を追加し、[次へ] を **選択します。**
4. [**構成設定**  >  **OMA-URI の設定] 設定、[追加**] を**選択します**。

  
## <a name="manage-specific-surface-hub-features"></a>特定の機能Surface Hub管理する

このセクションでは、Intune または他の MDM プロバイダーを介して管理できる機能に関する情報について説明します。 次のようなシナリオが考えられます。

- [サービス品質 (QoS)](#quality-of-service-settings)
- [Microsoft TeamsとSkype for Business](#microsoft-teams-and-skype-for-business-settings)

### <a name="quality-of-service-settings"></a>サービス品質の設定

ビデオとオーディオの品質を最適化するには、Surface Hub QoS 設定をデバイスに追加します。 

| 名前 | 説明 | OMA-URI | 型 | 値 |
|:------ |:------------- |:--------- |:------ |:------- |
|**オーディオ ポート**| オーディオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DestinationPortMatchCondition | String  | 3478-3479 |
|**オーディオ DSCP**| オーディオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction | Integer | 46 |
|**ビデオ ポート**| ビデオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DestinationPortMatchCondition | String  | 3480 |
|**ビデオ DSCP**| ビデオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction | Integer | 34 |
|**共有ポート**| 共有ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DestinationPortMatchCondition | String  | 3481 |
|**DSCP の共有**| ポートマーキングの共有 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DSCPAction | Integer | 18 |
|**P2P オーディオ ポート**| オーディオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DestinationPortMatchCondition | String  | 50000-50019 |
|**P2P オーディオ DSCP**| オーディオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DSCPAction | Integer | 46 |
|**P2P ビデオ ポート**| ビデオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DestinationPortMatchCondition | String  | 50020-50039 |
|**P2P ビデオ DSCP**| ビデオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DSCPAction | Integer | 34 |
|**P2P 共有ポート**| 共有ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DestinationPortMatchCondition | String  | 50040-50059 |
|**P2P 共有 DSCP**| ポートマーキングの共有 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DSCPAction | Integer | 18 |


#### <a name="skype-for-business-qos-settings"></a>Skype for Business の QoS 設定

| 名前                 | 説明           | OMA-URI                                                                    | 型    | 値                          |
| -------------------- | --------------------- | -------------------------------------------------------------------------- | ------- | ------------------------------ |
| オーディオ ポート          | オーディオ ポートの範囲      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/SourcePortMatchCondition    | String  | 50000-50019                    |
| オーディオ DSCP           | オーディオ ポートのマーキング   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/DSCPAction                  | Integer | 46                             |
| オーディオ メディア ソース   | Skype アプリ名        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| ビデオ ポート          | ビデオ ポートの範囲      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/SourcePortMatchCondition    | String  | 50020-50039                    |
| ビデオ DSCP           | ビデオ ポートのマーキング   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/DSCPAction                  | Integer | 34                             |
| ビデオ メディア ソース   | Skype アプリ名        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| 共有ポート        | 共有ポートの範囲    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/SourcePortMatchCondition  | String  | 50040-50059                    |
| DSCP の共有         | ポートマーキングの共有 | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/DSCPAction                | Integer | 18                             |
| メディア ソースの共有 | Skype アプリ名        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |

> [!NOTE]
> 両方の表に、既定のポート範囲が表示されます。 管理者は、Skype for Business と Teams のコントロール パネルでポート範囲を変更できます。

### <a name="microsoft-teams-and-skype-for-business-settings"></a>Microsoft TeamsとSkype for Business設定

カスタム構成プロファイルを作成して、会議Teams近接参加などの機能を管理できます。 詳細については、「Manage [Microsoft Teams 構成」を参照Surface Hub。](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

#### <a name="changing-default-business-communications-platform"></a>既定のビジネスコミュニケーション プラットフォームの変更

既定のビジネス通信プラットフォームは、Surface Hub 2020 Update のインストール方法 (Windows 10 Team 20H2) によってWindows 10されます。 20H2 にイメージをSurface Hub Windows 10場合、Microsoft Teams は既定として設定されます。Skype for Business機能が使用可能になります (モード 1)。 以前の OS バージョンからハブをアップグレードした場合、Skype for Business は既定のままで、Teams の機能 (モード 0) は、Teams を既定として構成していない限り使用できます。 

既定のインストールを変更するには、アプリ[モードを次](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure)のように設定してTeamsプロファイルを使用します。  

- モード 0 — スケジュール設定済みの会議に対応する Microsoft Teams 機能を備えた Skype for Business です。
- モード 1 — スケジュール設定済みの会議に対応する Skype for Business 機能を備えた Microsoft Teams です。
- モード 2 — Microsoft Teams のみ。

| 名前 | 説明 | OMA-URI | 型 | 値 |
|:--- |:--- |:--- |:--- |:--- |
|**Teams アプリ ID**|アプリ名|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Teams アプリ モード**|Teams モード|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0、1、2 のいずれか|










