---
title: Intune で Surface Hub 2S を管理する
description: Intune を使用して Surface Hub 2S を更新および管理する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/10/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 406fcc58bdb09d7fd47966cd17123d55faec2b65
ms.sourcegitcommit: ea853f2dba67e63e6df33538670fd581e17facab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "11408792"
---
# <a name="manage-surface-hub-2s-with-intune"></a>Intune で Surface Hub 2S を管理する

## <a name="register-surface-hub-2s-with-intune"></a>Intune で Surface Hub 2S を登録する

IT 管理者は Surface Hub 2S で、モバイル デバイス管理 (MDM) プロバイダーを使用して設定やポリシーを管理できます。 Surface Hub 2S には、管理サーバーと通信するための管理コンポーネントが組み込まれているため、デバイスに追加のクライアントをインストールする必要はありません。

### <a name="manual-registration"></a>手動登録

1. Surface **** Hub 2S の [設定] アプリを開き、ローカル管理者としてサインインします。 **[Surface Hub]** > **[デバイス管理]** を選択し、**+** を選択して追加します。
2. Intune で使用するアカウントでログインするように求められます。 認証後、デバイスは Intune に自動的に登録されます。

   ![Intune で Surface Hub 2S を登録する](images/sh2-set-intune1.png)<br>
   
> [!NOTE]
> 認証に使用するアカウントは Intune 登録アカウントであり、Intune のライセンスを取得する必要があります。

### <a name="auto-registration--azure-active-directory-affiliated"></a>自動登録 — Azure Active Directory 連携

初期セットアップ プロセスで、Intune の自動登録が有効になっている Azure AD テナントに Surface Hub を連携すると、デバイスは自動的に Intune に登録されます。 詳しくは、「[Windows デバイスの Intune 登録方法](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods)」をご覧ください。 Surface Hub を Intune の "対応デバイス" にするには、Azure AD 連携と Intune の自動登録が必要です。 

## <a name="managing-windows-10-team-settings-with-intune"></a>Intune を使用した Windows 10 チーム設定の管理

1. Microsoft Endpoint **Manager にサインインし、[****デバイス**  >  **構成プロファイルの作成]**  >  **を選択します**。 
2. [**プラットフォーム] で****、[Windows 10 以降の**テンプレート] デバイスの制限  >  ****  >  **(Windows 10 Team)** を選択し、[作成] を**選択します**。 
3. Surface Hub と Surface Hub 2S のデバイス制限設定を参照して選択できます。

 ![Surface Hub 2S のデバイス制限を設定します。](images/sh2-set-intune3.png) <br>

これらの設定は、アプリとエクスペリエンス、Azure の運用分析情報、メンテナンス、セッション、ワイヤレスプロジェクションのカテゴリにまたがっています。  

## <a name="supported-configuration-service-providers-csps"></a>サポートされている構成サービス プロバイダー (AP)

Intune コンソールから直接利用できるポリシーに加えて、レジストリ キーまたはファイルにマップされる多数の Configuration サービス プロバイダー (CSP) があります。 

Microsoft は通常、Windows 10 オペレーティング システムの新しいバージョンごとに新しい CSP を提供します。 [Windows 10 Team 2020 Update](surface-hub-2020-update.md)には、Surface Hub と Surface Hub 2S の 20 以上の新しいデバイス管理ポリシーと更新されたデバイス管理ポリシーが含まれています。 これらの MDM ポリシーにより、IT 管理者は、Microsoft Store からのアプリ更新プログラム、インフラストラクチャ上の Miracast などのワイヤレスプロジェクション設定、Quality-Of-Service や 802.1x 有線認証などのネットワーク設定、および新しいプライバシー/GDPR 関連の設定を制御できます。

詳しくは、次のリソースを参照してください。 

- [構成サービス プロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) 
- [SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
- [Microsoft Surface Hub でサポートされている Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)
- [Surface Hub Team 2020 Update の新機能](surface-hub-2020-update-whats-new.md)

## <a name="quality-of-service-qos-settings"></a>サービスの品質 (QoS) の設定

Surface Hub 2S で最適なビデオおよびオーディオ品質を確保するには、次の QoS 設定をデバイスに追加します。 

### <a name="microsoft-teams-qos-settings"></a>Microsoft Teams の QoS 設定 

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


### <a name="skype-for-business-qos-settings"></a>Skype for Business の QoS 設定

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

## <a name="microsoft-teams-settings"></a>Microsoft Teams の設定

Intune を使用してさまざまな Microsoft Teams 設定を構成できます。

### <a name="modes"></a>モード

Surface Hub 2S は Microsoft Teams と共にモード 0 でインストールされます。このモードでは、Microsoft Teams と Skype for Business の両方がサポートされます。 以下の説明に従って、モードが機能します。

- モード 0 — スケジュール設定済みの会議に対応する Microsoft Teams 機能を備えた Skype for Business です。
- モード 1 — スケジュール設定済みの会議に対応する Skype for Business 機能を備えた Microsoft Teams です。
- モード 2 — Microsoft Teams のみ。

モードを調整するには、カスタム デバイス構成プロファイルに次の設定 [を追加します](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure)。

| 名前 | 説明 | OMA-URI | 型 | 値 |
|:--- |:--- |:--- |:--- |:--- |
|**Teams アプリ ID**|アプリ名|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Teams アプリ モード**|Teams モード|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0、1、2 のいずれか|

### <a name="coordinated-meetings-and-proximity-join"></a>調整された会議と近接参加

Teams 調整された会議と近接参加機能は、Intune プロファイルを介して展開された [XML](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure) ファイルを介して構成できます。
