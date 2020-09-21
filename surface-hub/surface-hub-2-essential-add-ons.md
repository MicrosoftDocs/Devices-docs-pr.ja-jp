---
title: Surface Hub 2 での Windows 10 Pro と Enterprise の重要なアドオン
description: この記事では、Surface Hub 2 で Windows 10 Pro または Enterprise で使用できるオプションのアクセサリについて説明します。
keywords: Surface Hub、Windows 10、デスクトップ、指紋リーダ、Windows Hello
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.date: 09/16/2020
ms.collection: M365-modern-desktop
ms.topic: article
ms.openlocfilehash: d908c937c331e36f6b82f4c3c5ee213abf8a0176
ms.sourcegitcommit: 2ac88d30b7d104d86b3bec657941457c916a116c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "11027006"
---
# Surface Hub 2 での Windows 10 Pro と Enterprise の重要なアドオン

Windows 10 Team から Windows 10 Pro または Surface Hub 2 上のエンタープライズに移行した場合は、USB-C、USB-A、HDMI、または Bluetooth を使用して接続するさまざまなアクセサリから選ぶことができます。 

## Surface Hub 2 の指紋リーダー

Windows 10 Pro または windows 10 Enterprise を Surface Hub 2 で実行している場合は、オプションの Surface Hub 2 指紋リーダーである、 [Windows Hello](https://docs.microsoft.com/windows-hardware/design/device-experiences/windows-hello)を使用するバイオメトリクス認証オプションを使ってサインインできます。

### 販売

商用のお客様は、Surface 認定デバイス販売店を通じて注文を行うことができます。

**Surface Hub 2 の指紋リーダーを使用するには、次の操作を行います。**

1. デバイスの各側にある USB C ドアポートに指紋リーダーを挿入します。
2. スタート画面に**移動し**  >  ます。**設定**  > **アカウント**  > **サインインオプション**  > **Windows Hello 指紋**を使って指紋を登録します。

Windows Hello を使ってサインインするための指紋リーダーの構成の詳細については、次を参照してください。

- [Windows Hello の概要とセットアップ](https://support.microsoft.com/help/4028017/windows-learn-about-windows-hello-and-set-it-up)
- [企業の Windows Hello 生体認証](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-biometrics-in-enterprise)。

  
### 表 1. Surface Hub 2 指紋リーダの技術仕様


| コンポーネント                       | 説明                                                                                                                          |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **USB**                         | カスタマイズされた USB タイプ C                                                                                                           |
| **システム要件**          | Windows 10 Pro、Windows 10 Enterprise。                                                                                               |
| **Windows 認定**       | Windows 10                                                                                                                           |
| **誤承諾率 (FAR)** | 1/1.5 百万。 これまでに、バイオメトリクスのセキュリティシステムが不正ユーザーによるアクセス試行を正しく受け入れない確率を示しています。 |


> [!NOTE]
> Surface Hub 2S で実行される Windows 10 チームは Surface Hub 2 の指紋リーダーをサポートしていません。 これは、Windows 10 チームが、複数のユーザーが会議室の環境でデバイスを操作できるように設計されているためです。 
 
## Windows Hello フェイス認識

Surface Hub 2 の windows 10 Pro と Enterprise は、Windows Hello を認証するためにサポートしており、Windows Hello 認定カメラアクセサリを必要とします。 Surface Hub 2S 用の内蔵カメラは、認証用に設計されておらず、Windows Hello をサポートしていないことに注意してください。 詳細については、「 [Windows Hello](https://docs.microsoft.com/windows-hardware/design/device-experiences/windows-hello) 」を参照してください。


## オーディオとビデオのアクセサリ

USB-C または USB-A ポートを使って、Surface Hub 2 のオーディオおよびビデオ機能をオーディオおよびカメラの周辺機器で拡張することができます。

推奨されるアクセサリの詳細については、以下を参照してください。

- [Microsoft Teams で認定された USB オーディオデバイスおよびビデオデバイス](https://docs.microsoft.com/microsoftteams/devices/usb-devices)
- [Microsoft Teams で認定を受けた IP 電話](https://docs.microsoft.com/microsoftteams/devices/teams-ip-phones)



## その他のアクセサリ
Surface Hub 2 には、さまざまなデバイスを接続するための次のポートが含まれています。 

- USB の1つはコンピューティングモジュール上のポート (表示の背面)
- bezels の 4 x USB C ポート
- Bluetooth 4.1 のサポート
- HDMI 2.0

 ![I/o 接続と物理ボタンの正面と背面のビュー](images/hub2s-schematic.png)

詳細については、「 [Surface Hub の2s ポートとキーパッドの概要](surface-hub-2s-port-keypad-overview.md)」を参照してください。


## 詳細情報

- [Windows 10 Pro または Enterprise On Surface Hub 2 を構成](surface-hub-2-post-install.md)します。