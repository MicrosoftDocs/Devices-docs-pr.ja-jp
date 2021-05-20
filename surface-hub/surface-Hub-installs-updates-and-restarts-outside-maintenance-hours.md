---
title: Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある
description: 自動更新に関するSurface Hubトラブルシューティング情報
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub, メンテナンス ウィンドウ, 更新
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.date: 04/15/2021
ms.openlocfilehash: 7df7857258c1baeedf4ff239eda17c66c93a531c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577027"
---
# <a name="surface-hub-may-install-updates-and-restart-outside-maintenance-hours"></a>Surface Hub が更新プログラムをインストールして、メンテナンス時間外に再起動することがある

特定の状況では、Surface Hubメンテナンス期間中ではなく、営業時間内に更新プログラムをインストールします。 必要に応じて、デバイスが再起動します。 プロセスが完了するまで、デバイスを使用できません。

> [!NOTE]  
> メンテナンス ウィンドウが見つからない場合、これは予期しない動作です。 これは、デバイスが長時間古い場合にのみ発生します。

## <a name="cause"></a>原因

営業時間内Surface Hub使用できる状態を維持するために、ハブは 設定 で定義されているメンテナンス ウィンドウ中に管理機能を実行するように構成されています (以下の「参照」を参照)。 このメンテナンス期間中、ハブは、ビジネス向け更新プログラム (WUfB) Windows更新プログラムWindowsを使用して、利用可能な更新プログラムを自動的にインストールします。 更新が完了すると、ハブが再起動する場合があります。

更新プログラムは、更新プログラムが有効になっているが、Surface Hub予約されていない場合にのみ、メンテナンス 期間中にインストールできます。 たとえば、Surface Hub が 24 時間続く会議にスケジュールされている場合、インストールがスケジュールされている更新プログラムは、次のメンテナンス 期間中にハブが利用可能になるまで延期されます。 ハブが引き続きビジー状態で、複数のメンテナンス ウィンドウを逃した場合、ハブは最終的に更新プログラムのインストールとダウンロードを開始します。 これは、メンテナンス ウィンドウの間または外部で発生する可能性があります。 ダウンロードとインストールが開始すると、デバイスが再起動する場合があります。

## <a name="to-avoid-this-issue"></a>この問題を回避するには

管理機能を実行する場合は、Surface Hubを確保することが重要です。 24 時間Surface Hub予約するか、メンテナンス ウィンドウで更新プログラムのインストールが遅れる間にデバイスを使用します。 スケジュールされたメンテナンス期間中は、ハブを使用または予約することをお勧めします。 更新用に 2 時間のウィンドウを予約する必要があります。

更新プログラムの可用性を制御するために使用できるオプションの 1 つは、「Update for Business Windowsを使用する方法です。

## <a name="learn-more"></a>詳細情報
 
- [Surface Hub の更新](first-run-program-surface-hub.md#update-the-surface-hub) 
- [メンテナンス期間](manage-windows-updates-for-surface-hub.md#maintenance-window) 
