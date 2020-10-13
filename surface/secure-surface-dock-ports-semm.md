---
title: Surface Enterprise 管理モード (SEMM) での Secure Surface Dock 2 ポート
description: このドキュメントでは、surface Dock 3、surface Pc 3、Surface Pro 7 など、互換性のある Surface デバイスに接続されている場合に、Surface Dock 2 の UEFI ポート設定を構成する方法について説明します。
ms.assetid: 2808a8be-e2d4-4cb6-bd53-9d10c0d3e1d6
ms.reviewer: ''
manager: laurawi
keywords: 一般的な問題のトラブルシューティング, セットアップの問題
ms.prod: w10
ms.mktglfcycl: support
ms.sitesec: library
ms.pagetype: surfacehub
author: v-miegge
ms.author: jesko
ms.topic: article
ms.date: 06/08/2020
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 641d023b59426582130dcfb7e0d86c6f3af456e8
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114695"
---
# Surface Enterprise 管理モード (SEMM) での Secure Surface Dock 2 ポート

## はじめに

Surface Enterprise 管理モード (SEMM) を使用すると、IT 管理者は、Windows インストーラー構成パッケージで UEFI 設定を構成することによって Surface Dock 2 ポートをセキュリティで保護し、管理することができます。MSI ファイル) 企業環境全体で互換性のある Surface デバイスに展開されます。

### サポートされるデバイス

SEMM での surface Dock 2 の管理は、surface Book 3、surface ノートブック3、surface ノートブック移動、surface Pro 7、Surface Pro X に接続されているドックで利用できます。これらの互換性のある Surface デバイスは、一般的に **ホストデバイス**と呼ばれます。 ホストデバイスが **認証** されているか、 **認証**されていないかに基づいて、パッケージがデバイスに適用されます。 構成済みの設定は、IT 管理者である、カメラなどの他の組み込みのペリフェラルと同じように、Surface Dock 2 を管理するために、ホストデバイス上の UEFI レイヤーに存在します。

>[!NOTE]
>Surface Dock 2 のポートを管理できるのは、Dock が次の互換性のあるデバイスのいずれかに接続されている場合のみです。 Surface Book 3、Surface Pc 3、Surface Pro 7。 UEFI 認証されたポリシー設定を受け取らないデバイスは、本質的に認証されていないデバイスです。

### シナリオ

Surface Dock 2 を会社のホストデバイスにサインインした許可されたユーザーに制限すると、データ保護の別のレイヤーが提供されます。 Surface Dock 2 のロックダウン機能は、厳密なセキュリティプロトコルのコンプライアンスを維持しながら、Dock の機能と生産性の向上を望む、安全性の高い環境では、特定のユーザーにとって重要です。 Surface Dock 2 での SEMM の使用は、セキュリティ上の理由から USB ポートをロックする必要があるお客様に特に便利です。 ビデオのデモについては、「 [Surface Dock 2 用の Semm](https://youtu.be/VLV19ISvq_s)」をご覧ください。

## Surface Dock 2 の UEFI 設定を構成して展開する

このセクションでは、次のタスクを実行するためのステップバイステップのガイダンスを示します。

1. [**SURFACE UEFI コンフィギュレーター**](https://www.microsoft.com/download/details.aspx?id=46703)をインストールします。
1. 公開キー証明書を作成または取得します。
1. を作成します。MSI 構成パッケージ。
   1. 証明書を追加します。
   1. Surface Dock 2 デバイスの16桁の RN 番号を入力します。
   1. UEFI 設定を構成します。
1. 構成パッケージをビルドし、対象サーフェスデバイス (Surface Book 3、Surface ノート Pc 3、Surface Pro 7) に適用します。

>[!NOTE]
>**ランダム番号 (RN)** は、工場でプロビジョニングされ、ドックの下側に小さい形式で印刷される一意の16桁の16進数コード識別子です。 RN は、電子的には読み取れないため、ほとんどのシリアル番号とは異なります。 これにより、所有権の証明が主に、デバイスに物理的にアクセスしたときに、RN を読み取ることによってのみ確立されます。 この RN は、購入トランザクション中に取得されることもあり、Microsoft インベントリシステムで記録されます。

### SEMM および Surface の UEFI コンフィギュレーターをインストールする

**SurfaceUEFI_Configurator_v2.71.139.0.msi**を実行して semm をインストールします。 これはスタンドアロンのインストーラーであり、Surface Dock 2 の構成パッケージを作成して配布するために必要なすべてが含まれています。

- Surface [Tools](https://www.microsoft.com/en-us/download/details.aspx?id=46703)から**Surface の UEFI コンフィギュレーター**をダウンロードします。

## 公開キー証明書を作成する

このセクションでは、Surface Dock 2 のポートを管理するために必要な証明書を作成するための仕様を示します。

### 前提条件

この記事では、サードパーティプロバイダーから証明書を取得するか、PKI 証明書サービスの専門知識を既に持っており、独自の技術情報を作成することを前提としています。  「 [Surface Enterprise 管理モード (SEMM)](https://docs.microsoft.com/surface/surface-enterprise-management-mode) ドキュメント」で説明されているように、証明書を作成する際の一般的な推奨事項について理解している必要があります。 このページに記載されている証明書には、 **Dock 証明機関**の場合は30年、 **ホスト認証証明書**には20年の有効期限が必要です。

詳細については、「 [証明書サービスのアーキテクチャ](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture) に関するドキュメント」を参照してください。 [windows server 2019](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)内の適切な章、または Microsoft Press から提供されている [Windows Server 2008 PKI および証明書のセキュリティ](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788) を確認してください。

### ルートとホストの証明書の要件

構成パッケージを作成する前に、Surface Dock 2 の所有権を認証する公開キー証明書を用意して、デバイスのライフサイクル中に所有権のその後の変更を容易にする必要があります。 ホストとプロビジョニングの証明書では、 **クライアント認証の拡張キー使用法 (EKU) オブジェクト識別子 (oid)** と呼ばれているものとして、eku id を入力する必要があります。

必要な EKU 値が、表1と表2に一覧表示されています。

#### 表 1. ルートとドックの証明書の要件

|証明書|アルゴリズム|説明|有効期限|EKU OID|
|---|---|---|---|---|
|ルート証明機関|ECDSA_P384|-384 ビット素数楕円曲線デジタル署名アルゴリズム (ECDSA) を含むルート証明書<br>-SHA 256 キー使用法:<br>CERT_DIGITAL_SIGNATURE_KEY_USAGE<br>-CERT_KEY_CERT_SIGN_KEY_USAGE<br>CERT_CRL_SIGN_KEY_USAGE|30年|該当せず
|ドック証明機関|ECC P256 curve|-256 ビットの楕円曲線暗号 (ECC) でのホスト証明書<br>-SHA 256 キー使用法:<br>CERT_KEY_CERT_SIGN_KEY_USAGE<br>-Path Length 制約 = 0|20年|1.3.6.1.4.1.311.76.9.21.2<br>1.3.6.1.4.1.311.76.9.21.3|

   >[!NOTE]
   >Dock CA は、p7b ファイルとしてエクスポートする必要があります。

### 管理証明書の要件のプロビジョニング

各ホストデバイスは、表2に示すように、doc CA と2つの証明書を持っている必要があります。

#### 表 2. 管理証明書の要件のプロビジョニング

|証明書|アルゴリズム|説明|EKU OID|
|---|---|---|---|
|Host authentication certificate|ECC P256<br>SHA 256|ホストデバイスの id を証明します。|1.3.6.1.4.1.311.76.9.21.2|
|プロビジョニング管理証明書|ECC P256<br>SHA256|ドックに現在インストールされている CA を置き換えられるようにすることで、dock の所有権やポリシー設定を変更できます。|1.3.6.1.4.1.311.76.9.21.3<br>1.3.6.1.4.1.311.76.9.21.4|

   >[!NOTE]
   >ホスト認証とプロビジョニング証明書は、.pfx ファイル形式でエクスポートする必要があります。

### 構成パッケージを作成する

証明書を取得または作成したら、ターゲット Surface デバイスに適用される MSI 構成パッケージを作成できます。

1. Surface **UEFI コンフィギュレーター**を実行します。

   ![Surface UEFI コンフィギュレーターの実行](images/secure-surface-dock-ports-semm-1.png)

1. [ **Surface Dock**] を選びます。

   ![Surface Dock を選ぶ](images/secure-surface-dock-ports-semm-2.png)

1. [証明書] ページで、適切な **証明書**を入力します。

   ![適切な証明書を入力する](images/secure-surface-dock-ports-semm-3.png)

1. 適切な dock RNs をリストに追加します。

   >[!NOTE]
   >複数の Surface Dock 2 デバイスの構成パッケージを作成する場合、各 RN を手動で入力する代わりに、RNs のリストを含む .csv ファイルを使うことができます。

1. USB データ、イーサネット、およびオーディオポートのポリシー設定を指定します。 UEFI コンフィギュレーター認証済みユーザー (認証済みポリシー) と認証されていないユーザー (認証されていないポリシー) のポリシー設定を構成できます。 次の図は、認証されたユーザーに対して [ポートアクセス] がオンになっていることを示しています。

   ![アクティブ化または非アクティブ化するコンポーネントを選択します。](images/secure-surface-dock-ports-semm-4.png)

   - Authenticated user は、で構成されている適切な証明書がインストールされている Surface デバイスを指します。ターゲットデバイスに適用した MSI 構成パッケージ。 これは、デバイスにサインインしたユーザー認証済みのユーザーに適用されます。 
   - 認証されていないユーザーは、他のデバイスを参照しています。
   - [ **リセット** ] を選択して、dock によって承認された以前の構成パッケージを削除する特別な "リセット" パッケージを作成します。

1. [ **ビルド** ] を選択して、指定どおりにパッケージを作成します。

### 構成パッケージを Surface Dock 2 に適用する

1. Surface UEFI コンフィギュレーターによって生成された MSI ファイルを取得して Surface host デバイスにインストールします。 互換性のあるホストデバイスとしては、surface Book 3、Surface ノート Pc 3、Surface Pro 7 があります。
1. ホストデバイスを Surface Dock 2 に接続します。 ドックに接続すると、UEFI ポリシー設定が適用されます。

## Surface アプリを使用して管理状態を確認する

構成パッケージを適用した後は、Surface の結果ポリシーの状態を、Surface アプリから直接確認することができます。これは、既定ですべての Surface デバイスにインストールされています。 Surface アプリがデバイスに存在しない場合は、Microsoft Store からダウンロードしてインストールできます。

### テストシナリオ

目的: 認証されたユーザーのみがアクセスできるようにポリシー設定を構成します。

1. 認証されたユーザーのためにすべてのポートを有効にし、認証されていないユーザーに対してオフにします。

   ![認証されたユーザーのポートを有効にする](images/secure-surface-dock-ports-semm-4.png)

1. 構成パッケージをターゲットデバイスに適用し、Surface Dock 2 を接続します。

1. Surface **アプリ** を開き、[ **surface dock** ] を選択して、surface dock の結果ポリシーの状態を表示します。 ポリシー設定が適用されると、Surface アプリは、ポートが利用可能であることを示します。

   ![Surface アプリは、認証されたユーザーがすべてのポートを利用できることを示します。](images/secure-surface-dock-ports-semm-5.png)

1. 次に、ポリシー設定で、認証されていないユーザーのすべてのポートが正常にオフになっていることを確認する必要があります。 Surface Dock 2 を非管理対象デバイスに接続します。つまり、作成した構成パッケージの管理の範囲外にある任意の Surface デバイス。

1. **Surface アプリ**を開いて、[ **surface Dock**] を選択します。 ポリシーの状態には、ポートがオフになっていることが示されます。

   ![認証されていないユーザーに対して無効になっているポートを示す Surface アプリ ](images/secure-surface-dock-ports-semm-6.png)

>[!NOTE]
>デバイスの所有権を保持したいが、すべてのユーザーにフルアクセスを許可する場合は、新しいパッケージを作成してすべての機能を有効にすることができます。 デバイスの制限と所有権を完全に削除する (これを非管理する) には、[Surface UEFI 構成の **リセット** ] を選択して、ターゲットデバイスに適用するパッケージを作成します。

お疲れさまでした。 ターゲットとなるホストデバイスで、Surface Dock の2つのポートが正常に管理されました。

## 詳細情報

- [Surface Enterprise 管理モード (SEMM) のドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)
- [証明書サービスのアーキテクチャ](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture)
- [Windows Server 2019 インサイド Out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)
- [Windows Server 2008 PKI および証明書のセキュリティ](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)
