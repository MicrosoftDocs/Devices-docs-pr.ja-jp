---
title: Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある
description: 自動更新に関する Surface Hub のトラブルシューティング情報
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub、メンテナンスウィンドウ、更新プログラム
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 117c18cfce6dfb84b4fe2156ea98198f96da2abf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836405"
---
# Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある

特定の状況では、Surface Hub は通常のメンテナンスウィンドウではなく、業務時間中に更新プログラムをインストールします。 必要に応じて、デバイスが再起動します。 プロセスが完了するまでは、デバイスを使用することはできません。

> [!NOTE]  
> これは、メンテナンスウィンドウが見つからない場合の予期しない動作です。 これは、デバイスの日付が長いときにのみ発生します。

## 原因
Surface Hub を業務時間中も使用できるようにするために、ハブは設定で定義されているメンテナンスウィンドウで管理機能を実行するように構成されています (以下の「参照」を参照してください)。 このメンテナンス期間中、ハブは Windows Update または Windows Server Update Service (WSUS) を通じて、利用可能な更新プログラムを自動的にインストールします。 更新が完了すると、ハブが再起動されることがあります。

更新プログラムは、Surface Hub がオンになっているが、使用されていない場合、または予約されている場合にのみ、メンテナンスウィンドウでインストールできます。 たとえば、24時間継続する会議のために Surface Hub がスケジュールされている場合、インストールがスケジュールされている更新は、次のメンテナンスウィンドウでハブが利用可能になるまで延期されます。 ハブがビジー状態で、複数のメンテナンスウィンドウが見つからない場合、ハブは最終的に更新プログラムのインストールとダウンロードを開始します。 これは、メンテナンスウィンドウの途中または外部で発生する可能性があります。 ダウンロードとインストールが開始されると、デバイスが再起動されることがあります。

## この問題を回避するには

管理機能を実行するには、Surface Hub のメンテナンス時間を確保することが重要です。 24時間間隔で Surface Hub を予約するか、メンテナンスウィンドウ中にデバイスを使用すると、更新プログラムのインストールが遅延します。 スケジュールされているメンテナンス期間中はハブを使用しないことをお勧めします。 2時間のウィンドウは更新のために予約されている必要があります。

更新プログラムの可用性を制御するために使用できるオプションの1つは、Windows Server Update Service (WSUS) です。 WSUS は、どの更新プログラムがインストールされているかを制御します。

## 参考文献 
 
[Surface Hub の更新](first-run-program-surface-hub.md#update-the-surface-hub) 

[メンテナンス期間](manage-windows-updates-for-surface-hub.md#maintenance-window) 

[Windows Server Update Services (WSUS) を使った Windows 10 更新プログラムの展開](/windows/deployment/update/waas-manage-updates-wsus) 


