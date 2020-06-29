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
ms.date: 02/28/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 1d1b836c18a41982497bb28c57f379408c04f8a5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836637"
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

## Windows 10 Team Edition 設定

Windows 10 Team を選択すると、Surface Hub および Surface Hub 2S 用に事前設定されたデバイス制限設定を指定できます。

 ![Surface Hub 2S のデバイス制限を設定します。](images/sh2-set-intune3.png) <br>

これらの設定には、ユーザー エクスペリエンスとアプリの動作、Azure Log Analytics の登録、メンテナンス ウィンドウ構成、セッション設定、Miracast 設定が含まれます。 使用可能な Windows 10 Team 設定の完全な一覧については、「[SurfaceHub CSP](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)」をご覧ください。

## サポートされているその他の構成サービス プロバイダー (CSP)

サポートされているその他の CSP については、「[Windows 10 でサポートされている Surface Hub CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)」をご覧ください。

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
