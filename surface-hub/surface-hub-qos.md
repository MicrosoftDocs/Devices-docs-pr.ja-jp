---
title: Surface Hub でのサービスの品質の実装
ms.reviewer: ''
manager: laurawi
description: Surface Hub で QoS を構成する方法について学習します。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 32d7493dc4a76b8e7642b927ec5db41a1e697b2a
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470485"
---
# <a name="implement-quality-of-service-qos-on-surface-hub"></a>Surface Hub でのサービス品質 (QoS) の実装

サービス品質 (QoS) は、管理者がリアルタイムのオーディオ/ビデオとアプリケーション共有通信のエクスペリエンスを最適化できるネットワーク テクノロジの組み合わせです。
 
Surface Hub で Skype for Business の [QoS](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) を構成するには、モバイル デバイス管理 [(MDM)](manage-settings-with-mdm-for-surface-hub.md) プロバイダーを使用するか、プロビジョニング [パッケージを使用します](provisioning-packages-for-surface-hub.md)。 
 
 
この手順では、Microsoft Intune を使用して Surface Hub の QoS を構成する方法について説明します。 

1. Intune で、 [カスタム ポリシーを作成します](https://docs.microsoft.com/intune/custom-settings-configure)。

    > [!div class="mx-imgBorder"]
    > ![Intune のカスタム ポリシー作成ダイアログのスクリーンショット](images/qos-create.png)

2. [ **カスタム OMA-URI 設定] で、[** 追加] を **選択します**。 追加する設定ごとに、名前、説明 (オプション)、データ型、OMA-URI、および値を入力します。

    > [!div class="mx-imgBorder"]
    > ![空白の OMA-URI 設定ダイアログ ボックスのスクリーンショット](images/qos-setting.png)

3. 次のカスタム OMA-URI 設定を追加します。<br/><br/>

    名前 | データ型 | OMA-URI<br>./Device/Vendor/MSFT/NetworkQoSPolicy |  値
    --- | --- | --- | ---
    オーディオ ソース ポート | String |  /HubAudio/SourcePortMatchCondition  |   Skype 管理者から値を取得する
    オーディオ DSCP | Integer |  /HubAudio/DSCPAction  |   46
    ビデオ ソース ポート | String |  /HubVideo/SourcePortMatchCondition   |  Skype 管理者から値を取得する
    ビデオ DSCP | Integer |  /HubVideo/DSCPAction   |   34
    オーディオ プロセス名 | String |  /HubAudio/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe
    ビデオ プロセス名 | String |  /HubVideo/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe

    >[!IMPORTANT]
    >各 **OMA-URI パス** はで始まります `./Device/Vendor/MSFT/NetworkQoSPolicy` 。 たとえば、オーディオ ソース ポートの設定の完全なパスは、 です `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` 。

4. ポリシーが作成された場合は、Surface Hub に展開します。


>[!WARNING]
>現時点では、NetworkQoSPolicy CSP で **IPProtocolMatchCondition** の設定 [を構成できません](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)。 この設定が構成されている場合、ポリシーは適用されません。
 
