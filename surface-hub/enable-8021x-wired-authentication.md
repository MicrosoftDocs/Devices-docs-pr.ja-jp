---
title: 802.1x ワイヤード (有線) 認証を有効にする
description: Surface Hub デバイスでは、802.1x ワイヤード (有線) 認証の MDM ポリシーが有効になっています。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/15/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 119f879d74ccda5d53da27d842413346a50693f1
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836253"
---
# 802.1x ワイヤード (有線) 認証を有効にする

[Windows 10 の 2017 年 11 月 14 日の更新プログラム](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (ビルド 15063.726) により、Surface Hub デバイスでの 802.1x ワイヤード (有線) 認証の MDM ポリシーが有効になります。 この機能により、組織で [IEEE 802.1x 認証プロトコル](http://www.ieee802.org/1/pages/802.1x-2010.html)を使用する、標準化されたワイヤード (有線) ネットワーク認証を適用できます。 これは MDM を介して WLAN プロファイルを使用するワイヤレス認証では既に利用可能です。 このトピックでは、ワイヤード (有線) 認証で使用するための Surface Hub の構成方法について説明します。 

Surface Hub での 802.1x ワイヤード (有線) 認証の適用と有効化は、MDM [OMA URI 定義](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings)で構成できます。 

設定するプライマリ構成は **LanProfile** ポリシーです。 選択した認証方法によっては、**EapUserData** ポリシーまたはユーザーやコンピューターの証明書を追加するための MDM ポリシー (ユーザー/デバイスの証明書用の [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)、デバイス証明書用の [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) など) のいずれかのポリシーが必要になる場合があります。 

## LanProfile ポリシー要素

サポートされている 802.1x 認証方法のいずれかを使用するように Surface Hub を構成するには、次の OMA-URI を使用します。 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

この OMA-URI ノードは、XML のテキスト文字列をパラメーターとして取得します。 パラメーターとして提供される XML は、[802.1X スキーマ](https://msdn.microsoft.com/library/cc233003.aspx)の要素を含む [ワイヤード (有線) LAN プロファイル スキーマ](https://msdn.microsoft.com/library/cc233002.aspx)に準拠している必要があります。 

ほとんどの場合、管理者またはユーザーは、次の NETSH コマンドを使用して、ネットワーク上で既に 802.1X 用に構成されている既存の PC から LanProfile XML をエクスポートできます。 

```
netsh lan export profile folder=.
```

このコマンドを実行すると、次のように出力され、現在のディレクトリに **Ethernet.xml** という名前のファイルが配置されます。 

```
Interface: Ethernet
Profile File Name: .\Ethernet.xml
1 profile(s) were exported successfully.
```

## EapUserData ポリシー要素

証明書ではなく、ユーザー名とパスワードを必要とする認証方法を選択した場合、**EapUserData** 要素を使用して、ネットワークで認証するために使用するデバイスの資格情報を指定できます。 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

この OMA-URI ノードは、XML のテキスト文字列をパラメーターとして取得します。 パラメーターとして提供される XML は、[PEAP MS-CHAPv2 ユーザー プロパティの例](https://msdn.microsoft.com/library/windows/desktop/bb891979)に準拠している必要があります。 この例で、*test* と *ias-domain* のすべてのインスタンスを自分の情報に置き換える必要があります。



## 証明書の追加

選択した認証方法が証明書ベースの場合は、[プロビジョニングパッケージを作成](provisioning-packages-for-surface-hub.md)するか、 [MDM を利用](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)するか、または設定 (**設定**の更新とセキュリティ証明書) から証明書をインポートして、それらの証明書を  >  **Update and Security**  >  **Certificates**適切な証明書ストアの Surface Hub デバイスに展開する必要があります。 証明書を追加する場合、各 PFX には証明書を 1 つだけ含める必要があります (PFX に複数の証明書を含めることはできません)。

