---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成する方法と、ターゲットサーフェスデバイスのファームウェア設定を管理する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 11/13/2019
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 0aa69bb229f0d76972620bc58f236e43e03075b2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835582"
---
# Surface UEFI の設定の Intune 管理

## はじめに

クラウドからデバイスを管理する機能によって、ライフサイクル全体の IT 展開とプロビジョニングが大幅に簡略化されました。 Microsoft Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると ([パブリックプレビュー](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)で利用できるようになりました)、Surface uefi 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。 DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。 よく寄せられる質問に対する回答については、「 [Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理のアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)」を参照してください。

### Background

Windows 10 を実行しているコンピューターと同様に、Surface デバイスは、ハードドライブ、ディスプレイデバイス、USB ポート、その他のデバイスとのインターフェイスを可能にする SoC に保存されているコードに依存します。 この読み取り専用メモリ (ROM) に保存されているプログラムは、ファームウェアと呼ばれます (動的メディアに保存されているプログラムはソフトウェアと呼ばれます)。

現在市場で利用できる他の Windows 10 デバイスとは対照的に、Surface は、豊富な UEFI 構成設定を使用してファームウェアを構成および管理する機能を IT 管理者に提供します。 これにより、モバイルデバイス管理 (MDM) ポリシー、構成マネージャー、またはグループポリシーによって実装された、ソフトウェアベースのポリシー管理の上にある、ハードウェアコントロールのレイヤーが提供されます。 たとえば、機密情報が含まれるセキュリティの高い領域にデバイスを展開する組織では、ハードウェアレベルで機能を削除することにより、カメラの使用を防ぐことができます。 デバイスの観点から見ると、ファームウェア設定を使用してカメラをオフにすることは、カメラを物理的に取り外すことと同じです。 ファームウェアレベルでの管理の追加セキュリティと比較して、オペレーティングシステムソフトウェアの設定のみに依存するようにします。 たとえば、ドメイン環境のポリシー設定を使用して Windows audio サービスを無効にした場合、ローカル管理者は引き続きサービスを再び有効にすることができます。

### DFCI と SEMM

この時点では、ファームウェアの管理には、手動での IT 集約的なタスクのオーバーヘッドにより、デバイスを Surface Enterprise 管理モード (SEMM) に登録する必要があります。 例として、SEMM は、IT スタッフが各 PC に物理的にアクセスして、証明書管理プロセスの一部として2桁の pin を入力する必要があります。 SEMM は、厳格なオンプレミス環境における組織向けの優れたソリューションですが、複雑さと IT 集約的な要件によって使用コストが高くなります。

Microsoft Intune で新しく統合された UEFI ファームウェア管理機能を使用すると、ハードウェアのロックダウン機能が簡素化され、1つのコンソールでのプロビジョニング、セキュリティ、効率化された更新のための新しい機能で簡単に使用できるようになりました。 [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)として統合されました。 次の図は、デバイスに直接表示されている UEFI の設定を示しています (左側)。また、エンドポイントマネージャー本体 (右) に表示されています。

![デバイス (左側) とエンドポイントマネージャーコンソール (右) に表示される UEFI の設定](images/uefidfci.png)

Crucially を使用すると、IT 管理者による手動の操作が不要になって、ゼロのタッチ管理が可能になります。 DFCI は、Intune のデバイスプロファイル機能を使用して、Windows 自動操縦を介して展開されます。 デバイスプロファイルを使用すると、設定の追加と構成を行うことができます。これは、組織内の管理に登録されたデバイスに展開することができます。 デバイスがデバイスプロファイルを受信すると、その機能と設定が自動的に適用されます。 一般的なデバイスプロファイルの例には、メール、デバイスの制限、VPN、Wi-fi、管理用テンプレートがあります。 DFCI は、オンプレミスのインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できる追加のデバイスプロファイルです。  

## サポートされるデバイス

現時点では、DFCI は次のデバイスでサポートされています。

- Surface Pro 7
- Surface Pro X
- Surface Laptop 3

> [!NOTE]
> Surface Pro X では、組み込みのカメラ、オーディオ、Wi-fi/Bluetooth 用の DFCI 設定管理はサポートされていません。

## 前提条件

- デバイスは、 [Microsoft クラウドソリューションプロバイダー (CSP) パートナー](https://partner.microsoft.com/membership/cloud-solution-provider)または OEM ディストリビューターによって Windows 自動操縦に登録されている必要があります。

- Surface 用の DFCI を構成する前に、 [Microsoft Intune](https://docs.microsoft.com/intune/)と[azure Active DIRECTORY](https://docs.microsoft.com/azure/active-directory/) (azure AD) での自動操縦の構成要件について理解している必要があります。

## 始める前に

ターゲット Surface デバイスを Azure AD セキュリティグループに追加します。 セキュリティグループの作成と管理の詳細については、「 [Intune ドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)」を参照してください。

## Surface デバイス用の DFCI 管理を構成する

DFCI 環境では、登録済みデバイスに設定を適用するために、設定と自動操縦プロファイルを含む DFCI プロファイルを設定する必要があります。 また、ユーザーがデバイスを初めて起動したときに、OOBE のセットアップ中に設定をプッシュダウンすることを確認するために、登録ステータスプロファイルをお勧めします。 このガイドでは、DFCI 環境を構成し、ターゲット Surface デバイスの UEFI 構成設定を管理する方法について説明します。

## DFCI プロフィールの作成

DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲットデバイスを含む Azure AD セキュリティグループに割り当てる必要があります。

1. Devicemanagement.microsoft.com でテナントにサインインします。
2. Microsoft Endpoint Manager 管理センターで、[**デバイス] > 構成プロファイル**] の [プロファイルの作成] > 名前を入力します。たとえば、 **Dfci 構成ポリシーなどです。**
3. プラットフォームの種類については **、[Windows 10**以降] を選択します。
4. [Profile type] ドロップダウンリストで、[ **Device ファームウェア構成インターフェイス**] を選択して、利用可能なすべてのポリシー設定が含まれている dfci ブレードを開きます。 DFCI の設定の詳細については、このページまたは[Intune のドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)の表1を参照してください。 Dfci プロファイルを編集することにより、初期セットアッププロセスまたは後で DFCI 設定を構成できます。

    ![DFCI プロフィールの作成](images/df1.png)

5. [ **OK]** をクリックし、[**作成**] を選択します。
6. [**割り当て**] を選択し、次の図に示すよう**に**、ターゲットデバイスを含む Azure AD セキュリティグループを選択します。 **[保存]** をクリックします。

    ![セキュリティグループの割り当て](images/df2a.png)

## 自動操縦プロファイルを作成する

1. Devicemanagement.microsoft.com のエンドポイントマネージャーで、[ **Windows 登録 > デバイス**] を選択し、[**展開プロファイル**] まで下にスクロールします。
2. [**プロファイルの作成**] を選択し、名前を入力します。たとえば、 **[自動操縦プロファイル**] を選び、[**次へ**] を選びます。
3. 次の設定を選択します。

    - 展開モード:**ユーザー主導型**。
    - 参加の種類: Azure **AD が結合**されました。

4. その他の既定の設定はそのままにして、次の図に示すように [**次へ**] を選びます。

    ![自動操縦プロファイルを作成する](images/df3b.png)

5. [割り当て] ページで、[**グループの選択**] を選んで、Azure AD セキュリティグループを追加してクリックします。 **[次へ]** を選択します。
6. 概要を承諾し、[**作成**] を選択します。 自動操縦プロファイルが作成され、グループに割り当てられました。

## 登録状態のページを構成する

ユーザーがサインインする前に、デバイスで OOBE 中に DFCI 構成が適用されるようにするには、登録の状態を構成する必要があります。

詳細については、「[登録の状態を設定](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)する」ページを参照してください。


## Surface デバイスで DFCI 設定を構成する

DFCI には、ハードウェアレベルでデバイスをロックダウンすることによって、より高度なセキュリティを提供する、合理的な一連の UEFI 構成ポリシーが含まれています。 DFCI は、ソフトウェアレベルでモバイルデバイス管理設定と連携して使用するように設計されています。 DFCI 設定は、Surface デバイスに組み込まれているハードウェアコンポーネントにのみ影響します。 USB web カメラなどの添付された周辺機器に拡張されることはありません。 (ただし、Intune のデバイス制限ポリシーを使用して、添付されている周辺機器へのアクセスをソフトウェアレベルでオフにすることができます)。

次の図に示すように、[エンドポイントマネージャー] から DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。 

- Devicemanagement.microsoft.com のエンドポイントマネージャーで、[**デバイス > Windows > 構成プロファイル] > "DFCI profile name" > Properties > Settings**] を選びます。

    ![DFCI 設定を構成する](images/dfciconfig.png)

### ユーザーによる UEFI 設定へのアクセスをブロックする

多くのお客様は、ユーザーが UEFI 設定を変更できないようにする機能は非常に重要であり、DFCI を使用する主な理由です。 表1で示したように、これは [**ローカルユーザーによる UEFI 設定の変更を許可**する] 設定によって管理されます。 この設定を編集または構成しない場合、ローカルユーザーは Intune で管理されていない UEFI 設定を変更できます。 そのため、**ローカルユーザーによる UEFI 設定の変更を許可**しないことを強くお勧めします。
DFCI 設定の残りの部分では、ユーザーが使用できる機能を無効にすることができます。 たとえば、安全性の高い領域の機密情報を保護する必要がある場合は、カメラを無効にすることができます。また、ユーザーが USB ドライブから起動したくない場合は、無効にすることもできます。

### 表 1. DFCI のシナリオ

| デバイス管理の目標                        | 構成の手順                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ローカルユーザーが UEFI 設定を変更できないようにブロックする | [**セキュリティ機能 > ローカルユーザーによる UEFI の設定の変更を許可する**] で、[**なし**] を選択します。              |
| カメラを無効にする                               | [**内蔵ハードウェア > カメラ**] で [**無効**] を選びます。                                       |
| マイクとスピーカーを無効にする              | [**内蔵ハードウェア > マイクとスピーカー**] で、[**無効**] を選択します。                      |
| 無線を無効にする (Bluetooth、Wi-fi)             | [**内蔵ハードウェア > 無線 (Bluetooth、wi-fi など)**] で [**無効**] を選びます。                   |
| 外部メディアからの起動を無効にする (USB、SD)    | [**内蔵ハードウェア > ブートオプション > 外部メディア (USB、SD) から起動**する] で [**無効**] を選びます。 |

> [!CAUTION]
> [**無線を無効にする (Bluetooth、wi-fi)** ] 設定は、有線イーサネット接続を備えたデバイスでのみ使用してください。
 
> [!NOTE]
>  Intune の DFCI には、現在 Surface デバイスに適用されていない2つの設定が含まれています: (1) CPU および IO の仮想化と (2) ネットワークアダプターからの起動を無効にします。
 
Intune には、管理者権限と適用ルールを委任してデバイスの種類を管理するためのスコープタグが用意されています。 ポリシー管理のサポートとすべての DFCI 設定の詳細については、 [Microsoft Intune のドキュメント](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)を参照してください。

## 自動操縦でデバイスを登録する

上で説明したように、DFCI を適用できるのは、再販業者またはディストリビューターによって Windows 自動操縦に登録されているデバイスに限られます。この時点では、Surface Pro 7、Surface Pro X、Surface ノート Pc 3 でのみサポートされています。 セキュリティ上の理由から、デバイスを自動操縦に "セルフプロビジョニング" することはできません。

## 自動操縦機器を手動で同期する

Intune ポリシー設定は通常、ほぼ即座に適用されますが、ターゲットデバイスで設定が有効になるまで10分ほど時間がかかる場合があります。 まれな状況では、最大8時間の遅延が発生する可能性があります。 設定ができるだけ早く適用されるようにする (テストシナリオなど) には、ターゲットデバイスを手動で同期することができます。

- Devicemanagement.microsoft.com のエンドポイントマネージャーで、[デバイス **> デバイスの登録 > windows enrollment > Windows 自動操縦デバイス**] に移動し、[**同期**] を選択します。

 詳細については、「 [Windows デバイスを手動で同期](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)する」を参照してください。

> [!NOTE]
> UEFI で直接設定を調整する場合は、デバイスが標準の Windows ログインに完全に再起動する必要があります。

## DFCI で管理されているデバイスで UEFI 設定を確認する

テスト環境では、Surface UEFI インターフェイスで設定を確認できます。

1. [Surface UEFI] を開きます。これには、**ボリューム**と**電源**ボタンを同時に押す必要があります。
2. [**デバイス**] を選びます。 次の図に示すように、[UEFI] メニューには、構成済みの設定が反映されます。

    ![Surface UEFI](images/df3.png)

    次の点に注意してください。

      - [**ローカルユーザーによる UEFI の変更を許可**する] 設定が [なし] に設定されているため、設定が灰色表示されています。
      - **マイクとスピーカー**が**無効**に設定されているため、オーディオはオフに設定されます。

## DFCI ポリシー設定の削除

DFCI プロファイルを作成すると、構成されているすべての設定は、プロファイルの管理範囲内のすべてのデバイスで引き続き有効になります。 Dfci のポリシー設定は、DFCI プロファイルを直接編集することによってのみ削除できます。

元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。

## DFCI 管理の削除

**DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻すには、次の操作を行います。**

1. Intune からデバイスを削除する:
    1. Devicemanagement.microsoft.com のエンドポイントマネージャーで、[**グループ > すべてのデバイス**] を選びます。 削除するデバイスを選択し、[インベントリから削除] を選択し**ます。** 詳細について[は、「ワイプを使用してデバイスを削除する」または「手動でデバイスを登録解除](https://docs.microsoft.com/intune/remote-actions/devices-wipe)する」を参照してください。 
2. 自動操縦登録を Intune から削除します。
    1.  [**デバイス登録 > Windows 登録 > デバイス**] を選びます。
    2. [Windows 自動操縦デバイス] で、削除するデバイスを選択し、[**削除**] を選択します。
3. Surface 製のイーサネットアダプターを使って、デバイスを有線インターネットに接続します。 デバイスを再起動して、[UEFI] メニューを開きます (音量を上げるボタンを押したままにして、電源ボタンを押しながら離します)。
4. [**管理 > ネットワークからの更新 > 構成**] を選択し、[停止] を選択し**ます。**

Intune でデバイスを引き続き管理しますが、DFCI 管理がない場合は、デバイスを自動操縦に登録して、Intune に登録します。 DFCI は、自己登録デバイスには適用されません。

## 詳細情報
- [Ignite 2019: Intune からの SURFACE UEFI 設定のリモート管理のアナウンス](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windows 自動操縦](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md) 
- [Microsoft Intune の Windows デバイスで DFCI プロファイルを使用する](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
