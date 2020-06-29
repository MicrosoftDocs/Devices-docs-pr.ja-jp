---
title: Surface Hub でのサービスの品質の実装
ms.reviewer: ''
manager: laurawi
description: Surface Hub で QoS を構成する方法について説明します。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 99172e77be260559c770f5fc8a1438734bed660f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835190"
---
# Surface Hub にサービスの品質 (QoS) を実装する

QoS (Quality of Service) は、管理者がリアルタイムの音声/ビデオとアプリケーション共有通信のエクスペリエンスを最適化できるネットワークテクノロジを組み合わせたものです。
 
Surface Hub で[の Skype For business の QoS の](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)構成は、[モバイルデバイス管理 (MDM) プロバイダー](manage-settings-with-mdm-for-surface-hub.md)または[プロビジョニングパッケージ](provisioning-packages-for-surface-hub.md)を使用して行うことができます。 
 
 
この手順では、Microsoft Intune を使用して Surface Hub の QoS を構成する方法について説明します。 

1. Intune で、[カスタムポリシーを作成](https://docs.microsoft.com/intune/custom-settings-configure)します。

    ![Intune の [カスタムポリシーの作成] ダイアログのスクリーンショット](images/qos-create.png)

2. [**カスタムの Oma-uri 設定**] で、[**追加**] を選択します。 追加する各設定について、名前、説明 (省略可能)、データ型、OMA-URI、値を入力します。

    ![空白の [OMA-URI 設定] ダイアログボックスのスクリーンショット](images/qos-setting.png)

3. 次のカスタムの OMA URI 設定を追加します。

    名前 | データ型 | OMA-URI<br>./Device/Vendor/MSFT/NetworkQoSPolicy |  値
    --- | --- | --- | ---
    オーディオソースポート | String |  /HubAudio/SourcePortMatchCondition  |   Skype 管理者から値を取得する
    オーディオ DSCP | Integer |  /HubAudio/DSCPAction  |   46
    ビデオソースポート | String |  /HubVideo/SourcePortMatchCondition   |  Skype 管理者から値を取得する
    ビデオ DSCP | Integer |  /HubVideo/DSCPAction   |   34
    オーディオプロセス名 | String |  /HubAudio/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe
    ビデオプロセス名 | String |  /HubVideo/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe

    >[!IMPORTANT]
    >各**oma-uri**パスは、で始まり `./Device/Vendor/MSFT/NetworkQoSPolicy` ます。 オーディオソースポートの設定の完全なパスがあり `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` ます。




4. ポリシーが作成されたら、 [Surface Hub に展開します。](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)


>[!WARNING]
>現時点では、 [NETWORKQOSPOLICY CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)で**Ipprotocolmatchcondition**を設定することはできません。 この設定を構成すると、ポリシーは適用されません。
 
