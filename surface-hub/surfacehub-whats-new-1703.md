---
title: Windows 10 バージョン 1703 での Surface Hub の新機能
description: Windows 10 バージョン 1703 (Creators Update) では、Microsoft Surface Hub に新機能が追加されます。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/18/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 722309a6b018c32bde329cb7b2cdd68b859fc1ca
ms.sourcegitcommit: 8e809e8481023fe4421abcdaa1e055a6f2f74f5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/11/2020
ms.locfileid: "10924943"
---
# Windows 10 バージョン 1703 での Microsoft Surface Hub の新機能

Surface Hub エンジニアの Jordan Marchese による、Windows 10 バージョン 1703 (Creators Update) を実行する Microsoft Surface Hub で更新された機能についてのプレゼンテーションをご覧ください。 

<a href="https://www.youtube.com/watch?v=R8tX10VIgq0" target="_blank"> <img src="images/whats-new-video-thumbnail.png" alt="Link to Surface Hub video on Youtube" /></a>

Windows 10 バージョン 1703 (Creators Update) では、Microsoft Surface Hub に次の変更が加えられています。

##  <a name="new-settings"></a>新しい設定

モバイル デバイス管理 (MDM) と構成サービス プロバイダー (CSP) に設定が追加され、Surface Hub の管理機能が拡張されました。 [新しい設定は次のとおりです](manage-settings-with-mdm-for-surface-hub.md)。

- InBoxApps/SkypeForBusiness/DomainName
- InBoxApps/Connect/AutoLaunch
- Properties/DefaultVolume
- Properties/ScreenTimeout
- Properties/SessionTimeout
- Properties/SleepTimeout
- Properties/AllowSessionResume
- Properties/AllowAutoProxyAuth
- Properties/DisableSigninSuggestions
- Properties/DoNotShowMyMeetingsAndFiles
- System/AllowStorageCard

さらに、新しい [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) と [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp) に基づく設定があります。
</br>

##  <a name="provisioning-wizard"></a>プロビジョニング ウィザード

使いやすいウィザードにより、複数の Surface Hub デバイスに適用できるプロビジョニング パッケージをすばやく作成できます。Azure Active Directory に一括で参加させる機能もあります。 [Surface Hub のプロビジョニング パッケージの作成方法については、こちらをご覧ください。](provisioning-packages-for-certificates-surface-hub.md)

![Surface Hub デバイスのプロビジョニング ウィザードの手順](images/wcd-wizard.png)
    
##  <a name="miracast-on-your-existing-wireless-network-or-lan"></a>既存のワイヤレス ネットワークまたは LAN での Miracast 

Microsoft はダイレクト ワイヤレス リンク経由ではなく、[ローカル ネットワーク経由で Miracast ストリームを送信](miracast-over-infrastructure.md)できるように機能を拡張しました。 
    
##  <a name="cloud-recovery"></a>クラウド回復

Surface Hub デバイスをリセットするときに、クラウドから工場出荷時のビルドのオペレーティング システムをダウンロードしてインストールすることができます。 [クラウド回復について詳しくは、こちらをご覧ください。](device-reset-surface-hub.md#cloud-recovery)

>[!NOTE]
>クラウド回復は、プロキシ サーバーを使っている場合は機能しません。
    
![再インストール](images/reinstall.png)
    
##  <a name="end-session"></a>セッションの終了

**[終了]** は **[セッションの終了]** になりました。 [[セッションの終了] の使い方については、こちらをご覧ください。](finishing-your-surface-hub-meeting.md) 

![セッションの終了](images/end-session.png)



 

 
