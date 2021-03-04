---
title: Microsoft Surface Hub の管理
description: 最初の実行プログラムが完了した後に Surface Hub を管理する方法を説明します。
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/17/2018
ms.localizationpriority: medium
ms.openlocfilehash: 5e7fca007549d8804a756ef2a042f092f0acb1c3
ms.sourcegitcommit: 5c904229a0257297be7f724c264e484d2c4b5168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "11387434"
---
# <a name="manage-microsoft-surface-hub"></a>Microsoft Surface Hub の管理

Microsoft Surface Hub の初期セットアップ後、デバイスの設定と構成は、次の 2 つの方法で変更または変更できます。

- **ローカル管理** - デバイスで**設定**アプリを使用すると、すべての Surface Hub をローカルで構成できます。 承認されていないユーザーによって設定が変更されるのを防ぐため、設定アプリでは、アプリを起動する際に管理者の資格情報が求められます。 詳しくは、「[Surface Hub の設定のローカル管理](local-management-surface-hub-settings.md)」をご覧ください。
- **リモート管理** - Surface Hub を使用すると、IT 管理者は、Microsoft Intune、Microsoft Endpoint Configuration Manager、その他のサードパーティ プロバイダーなどのモバイル デバイス管理 (MDM) プロバイダーを使用して設定とポリシーを管理できます。 さらに、管理者は Azure Monitor を使用して Surface Hubs を監視できます。  詳細については [、「MDM](manage-settings-with-mdm-for-surface-hub.md)プロバイダーを使用して設定を管理する」および「Azure Monitor を使用して Surface Hubs を監視して正常性を [追跡する」を参照してください](https://docs.microsoft.com/azure/azure-monitor/insights/surface-hubs)。 

> [!NOTE]
> これらの管理方法は、相互に排他的ではありません。 必要に応じて、デバイスをローカルとリモートの両方で管理できます。 ただし、MDM ポリシーと設定は、Surface Hub が管理サーバーと同期するときにローカルの変更を上書きします。 

## <a name="in-this-section"></a>このセクションの内容

Surface Hub の管理と更新について説明します。

| トピック | 説明 |
| ----- | ----------- |
| [Surface Hub のリモート管理](remote-surface-hub-management.md) |Surface Hub のリモート管理に関連するトピックです。 アプリのインストール、MDM による設定の管理、Operations Management Suite による監視について説明します。 |
| [Surface Hub の設定の管理](manage-surface-hub-settings.md) |Surface Hub の設定の管理に関連するトピックです。アクセシビリティ、デバイス アカウント、デバイスのリセット、完全修飾ドメイン名、Windows Update の設定、ワイヤレス ネットワークについて説明します。 |
| [Surface Hub へのアプリのインストール]( https://technet.microsoft.com/itpro/surface-hub/install-apps-on-surface-hub) | 管理者は、Microsoft Store またはビジネス向け Microsoft Store からアプリをインストールできます。|
[Surface Hub のスタート メニューの構成](surface-hub-start-menu.md) | MDM を使用して、Surface Hub のスタート メニューをカスタマイズできます。
| [Microsoft Whiteboard のセットアップと使用](whiteboard-collaboration.md)  | Microsoft Whiteboard の最新の更新プログラムには、2 つの Surface Hub で同じボードを使用してリアルタイムに共同作業を行うための機能が含まれています。   |
| [[セッションの終了] をタップして会議を終了する](https://technet.microsoft.com/itpro/surface-hub/finishing-your-surface-hub-meeting) | 会議の終了時、ユーザーは **[セッションの終了]** をタップすることによって、機密データをクリーンアップし、次の会議用にデバイスを準備できます。|
| [Microsoft Authenticator を使った Surface Hub へのサインイン](surface-hub-authenticator-app.md) | Android と iOS で使用できる Microsoft Authenticator アプリを使用して、パスワードを使用せずに Surface Hub にサインインできます。   |
| [BitLocker キーの保存](https://technet.microsoft.com/itpro/surface-hub/save-bitlocker-key-surface-hub) | すべての Surface Hub は、自動的に BitLocker ドライブ暗号化ソフトウェアによってセットアップされます。 BitLocker 回復キーはバックアップしておくことを強くお勧めします。|
| [Surface Hub への他のデバイスの接続と表示](https://technet.microsoft.com/itpro/surface-hub/connect-and-display-with-surface-hub) | Surface Hub に他のデバイスを接続して、コンテンツを表示できます。|
| [既存のワイヤレス ネットワークまたは LAN での Miracast](miracast-over-infrastructure.md) | ワイヤレス ネットワークまたは LAN で Miracast を使用して、Surface Hub に接続できます。 |
 [802.1x ワイヤード (有線) 認証を有効にする](enable-8021x-wired-authentication.md) | Surface Hub デバイスでは、802.1x ワイヤード (有線) 認証の MDM ポリシーが有効になっています。 
| [ルーム コントロール システムの使用](https://technet.microsoft.com/itpro/surface-hub/use-room-control-system-with-surface-hub) | Microsoft Surface Hub では、ルーム コントロール システムを使用できます。|
[Surface Hub の回復ツールの使用](surface-hub-recovery-tool.md) | Surface Hub 回復ツールを使用して Surface Hub SSD を再イメージ化します。
[Surface Hub SSD の交換](surface-hub-ssd-replacement.md) | Surface Hub でソリッド ステート ドライブを削除して置き換える方法について学習します。

## <a name="related-topics"></a>関連トピック

- [Surface Hub と Windows 10 での Power BI プレゼンテーション モードの表示](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-app-presentation-mode/)
