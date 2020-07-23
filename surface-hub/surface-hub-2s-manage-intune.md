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
ms.date: 07/23/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 05279a54b51113ca96c4c939e8d64e51c4eca543
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893112"
---
# Intune で Surface Hub 2S を管理する

## Intune で Surface Hub 2S を登録する

IT 管理者は Surface Hub 2S で、モバイル デバイス管理 (MDM) プロバイダーを使用して設定やポリシーを管理できます。 Surface Hub 2S には、管理サーバーと通信するための管理コンポーネントが組み込まれているため、デバイスに追加のクライアントをインストールする必要はありません。

### 手動登録

1. Surface Hub 2S にローカル管理者としてサインインし、**設定**アプリを開きます。 **[Surface Hub]** > **[デバイス管理]** を選択し、**+** を選択して追加します。
2. 認証後、デバイスは Intune に自動的に登録されます。

   ![Intune で Surface Hub 2S を登録する](images/sh2-set-intune1.png)<br>

### 自動登録 — Azure Active Directory 連携

初期セットアップ プロセスで、Intune の自動登録が有効になっている Azure AD テナントに Surface Hub を連携すると、デバイスは自動的に Intune に登録されます。 詳しくは、「[Windows デバイスの Intune 登録方法](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods)」をご覧ください。 Surface Hub を Intune の "対応デバイス" にするには、Azure AD 連携と Intune の自動登録が必要です。 

## Intune で Windows 10 Team Edition の設定を管理する

1. **Microsoft Endpoint Manager**にサインインして、[**デバイス**  >  **構成プロファイル**  >  の**作成プロファイル**] を選択します。 
2. [**プラットフォーム**] で、[ **windows 10**以降の  >  **デバイスの制限] (windows 10 チーム)** を選択し、[**作成**] を選択します。 
3. Surface Hub と Surface Hub 2S のデバイス制限の設定を参照して選択できるようになりました。

 ![Surface Hub 2S のデバイス制限を設定します。](images/sh2-set-intune3.png) <br>

これらの設定は、アプリとエクスペリエンス、Azure operational insights、メンテナンス、セッション、ワイヤレスプロジェクションの各カテゴリに該当します。  

## サポートされている構成サービスプロバイダー (Csp)

Intune コンソールから直接利用可能なポリシーに加えて、レジストリキーまたはファイルにマッピングされる構成サービスプロバイダー (Csp) が数多くあります。 

Microsoft では、通常、新しいバージョンの Windows 10 オペレーティングシステムごとに新しい Csp を提供しています。 Windows Insider プログラムを使用してプレビューで利用できる[windows 10 Team 2020 更新プログラム](surface-hub-install-2020preview.md)には、surface Hub と Surface hub 2s に対して、20以上の新しいデバイス管理ポリシーが用意されています。 これらの MDM ポリシーは、IT 管理者が Microsoft ストアからのアプリの更新の制御を強化し、インフラストラクチャ経由の Miracast、サービス品質や 802.1 x ワイヤード認証などのネットワーク設定、新しいプライバシー/GDPR 関連設定などのワイヤレスプロジェクション設定を行うことができるようにします。

詳しくは、次のリソースをご覧ください。 

- [構成サービス プロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) 
- [SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
- [Microsoft Surface Hub でサポートされている Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)

## サービスの品質 (QoS) の設定

Surface Hub 2S で最適なビデオおよびオーディオ品質を確保するには、次の QoS 設定をデバイスに追加します。 

### Microsoft Teams の QoS 設定 

|**名前**|**説明**|**OMA-URI**|**型**|**値**|
|:------ |:------------- |:--------- |:------ |:------- |
|**オーディオ ポート**| オーディオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DestinationPortMatchCondition | String  | 3478-3479 |
|**オーディオ DSCP**| オーディオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction | Integer | 46 |
|**ビデオ ポート**| ビデオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DestinationPortMatchCondition | String  | 3480 |
|**ビデオ DSCP**| ビデオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction | Integer | 34 |
|**P2P オーディオ ポート**| オーディオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DestinationPortMatchCondition | String  | 50000-50019 |
|**P2P オーディオ DSCP**| オーディオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DSCPAction | Integer | 46 |
|**P2P ビデオ ポート**| ビデオ ポートの範囲 | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DestinationPortMatchCondition | String  | 50020-50039 |
|**P2P ビデオ DSCP**| ビデオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DSCPAction | Integer | 34 |


### Skype for Business の QoS 設定

| 名前               | 説明         | OMA-URI                                                                  | 型    | 値                          |
| ------------------ | ------------------- | ------------------------------------------------------------------------ | ------- | ------------------------------ |
| オーディオ ポート        | オーディオ ポートの範囲    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/SourcePortMatchCondition  | String  | 50000-50019                    |
| オーディオ DSCP         | オーディオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/DSCPAction                | Integer | 46                             |
| オーディオ メディア ソース | Skype アプリ名      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |
| ビデオ ポート        | ビデオ ポートの範囲    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/SourcePortMatchCondition  | String  | 50020-50039                    |
| ビデオ DSCP         | ビデオ ポートのマーキング | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/DSCPAction                | Integer | 34                             |
| ビデオ メディア ソース | Skype アプリ名      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |

> [!NOTE]
> 両方の表に、既定のポート範囲が表示されます。 管理者は、Skype for Business と Teams のコントロール パネルでポート範囲を変更できます。

## Microsoft Teams のモード設定

Intune を使用して Microsoft Teams アプリ モードを設定できます。 Surface Hub 2S は Microsoft Teams と共にモード 0 でインストールされます。このモードでは、Microsoft Teams と Skype for Business の両方がサポートされます。 モードは次のように調整できます。

### モード:

- モード 0 — スケジュール設定済みの会議に対応する Microsoft Teams 機能を備えた Skype for Business です。
- モード 1 — スケジュール設定済みの会議に対応する Skype for Business 機能を備えた Microsoft Teams です。
- モード 2 — Microsoft Teams のみ。

モードを設定するには、カスタムのデバイス構成プロファイルに次の設定を追加します。

|**名前**|**説明**|**OMA-URI**|**型**|**値**|
|:--- |:--- |:--- |:--- |:--- |
|**Teams アプリ ID**|アプリ名|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Teams アプリ モード**|Teams モード|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0、1、2 のいずれか|
