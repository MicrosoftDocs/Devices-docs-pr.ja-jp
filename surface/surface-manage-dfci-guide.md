---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成し、対象となる Surface デバイスのファームウェア設定を管理する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/09/2020
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
ms.openlocfilehash: dde34126c726ec0ac8093a665804c4fb0f639e3e
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271571"
---
# Surface UEFI の設定の Intune 管理

## はじめに

クラウドからデバイスを管理する機能により、ライフサイクル全体にわたって IT の展開とプロビジョニングが大幅に簡素化されました。 [Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)に組み込みのデバイス ファームウェア構成インターフェイス (DFCI) プロファイルにより、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。 DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を構築します。 よく寄せられる質問への回答については [、「Ignite 2019: Announcing remote management of Surface UEFI settings from Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)」を参照してください。

### Background

Windows 10 を実行している他のコンピューターと同様に、Surface デバイスは SoC に格納されているコードを利用して、CPU がハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスできます。 この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに保存されているプログラムはソフトウェアと呼ばれています)。

現在、市場で利用可能な他の Windows 10 デバイスとは対照的に、Surface は、豊富な UEFI 構成設定を通じてファームウェアを構成および管理する機能を IT 管理者に提供します。 これにより、モバイル デバイス管理 (MDM) ポリシー、Configuration Manager、またはグループ ポリシーを通じて実装されるソフトウェア ベースのポリシー管理の上にハードウェア制御のレイヤーが提供されます。 たとえば、機密性の高い情報を持つ高度なセキュリティ領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することでカメラの使用を防止できます。 デバイスの観点から、ファームウェア設定でカメラをオフにした場合は、カメラを物理的に取り外すのと同じです。 ファームウェア レベルでの管理に関する追加のセキュリティと、オペレーティング システムのソフトウェア設定にのみ依存するセキュリティを比較します。 たとえば、ドメイン環境のポリシー設定を使用して Windows オーディオ サービスを無効にした場合でも、ローカル管理者はサービスを再び有効にできます。

### DFCI と SEMM の比較

以前は、ファームウェアを管理するには、進行中の手動 IT 集中型タスクのオーバーヘッドを利用して、デバイスを Surface Enterprise Management Mode (SEMM) に登録する必要があります。 たとえば、SEMM では、証明書管理プロセスの一環として、IT スタッフが各 PC に物理的にアクセスして 2 桁のピンを入力する必要があります。 SEMM は厳密にオンプレミス環境の組織に対する優れたソリューションであり続けますが、複雑性と IT 負荷の高い要件により、使用にコストがかかります。

 Microsoft Intune に統合された UEFI ファームウェア管理機能により、ハードウェアをロックダウンする機能が簡素化され、プロビジョニング、セキュリティ、および合理化された更新のための新機能を 1 つのコンソールで簡単に使用できます。Microsoft [Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)として統合されました。 次の図は、デバイスで直接表示され (左)、エンドポイント マネージャー コンソール (右) で表示される UEFI 設定を示しています。

![デバイス (左側) とエンドポイント マネージャー コンソール (右) に表示される UEFI 設定](images/uefidfci.png)

非常に重要な点として、DFCI ではタッチ管理が不要で、IT 管理者による手動操作の必要性がなくなります。 DFCI は、Intune のデバイス プロファイル機能を使用して Windows Autopilot 経由で展開されます。 デバイス プロファイルを使用すると、組織内の管理に登録されているデバイスに展開できる設定を追加および構成できます。 デバイスがデバイス プロファイルを受信すると、機能と設定が自動的に適用されます。 一般的なデバイス プロファイルの例には、メール、デバイスの制限、VPN、Wi-Fi、管理用テンプレートがあります。 DFCI は、単に追加のデバイス プロファイルで、オンプレミスのインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できます。  

## サポートされるデバイス

DFCI は、次のデバイスでサポートされています。

- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go

> [!NOTE]
> Surface Pro X は、組み込みのカメラ、オーディオ、Wi-Fi/Bluetooth の DFCI 設定管理をサポートBluetooth。

## 前提条件

- デバイスは、Microsoft クラウド ソリューション プロバイダー [(CSP)](https://partner.microsoft.com/membership/cloud-solution-provider) パートナーまたは OEM ディストリビューターによって Windows Autopilot に登録されている必要があります。

- Surface の DFCI を構成する前に  [、Microsoft Intune](https://docs.microsoft.com/intune/) および Azure Active [Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD) の Autopilot 構成要件を理解している必要があります。

## 始める前に

ターゲット Surface デバイスを Azure AD セキュリティ グループに追加します。 セキュリティ グループの作成と管理の詳細については、Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。

## Surface デバイスの DFCI 管理を構成する

DFCI 環境では、設定を含む DFCI プロファイルを設定し、登録されたデバイスに設定を適用する Autopilot プロファイルを設定する必要があります。 登録状態プロファイルは、ユーザーが初めてデバイスを起動するときに、OOBE のセットアップ中に設定がプッシュダウンされるのを確認するためにも推奨されます。 このガイドでは、DFCI 環境を構成し、対象となる Surface デバイスの UEFI 構成設定を管理する方法について説明します。

## DFCI プロファイルを作成する

DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てる必要があります。

1. サインイン時にテナントにdevicemanagement.microsoft.com。
2. Microsoft Endpoint Manager 管理センターで、[デバイスと構成>を選択>プロファイルを作成 **し** 、名前を入力します。たとえば **、DFCI 構成ポリシーです。**
3. プラットフォーム **の種類として Windows 10 以降** を選択します。
4. [プロファイルの種類] ドロップダウン リストで、[ **デバイス** ファームウェア構成インターフェイス] を選択し、使用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。 DFCI 設定の詳細については、このページの表 1 または Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。 初期セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。

    ![DFCI プロファイルを作成する](images/df1.png)

5. **[OK] を**クリックし、[作成] を**選択します**。
6. 次**の図に**示**** すように、[割り当て] を選択し、[グループの選択] でターゲット デバイスを含む Azure AD セキュリティ グループを選択します。 **[保存]** をクリックします。

    ![セキュリティ グループを割り当てる](images/df2a.png)

## Autopilot プロファイルを作成する

1. In Endpoint Manager at devicemanagement.microsoft.com, select **devices > windows enrollment** and scroll down to Deployment **profiles**.
2. [プロファイル **の作成] を** 選択し、名前を入力します。For example, **My Autopilot profile,** and select **Next**.
3. 次の設定を選択します。

    - 展開モード: **ユーザー駆動型**。
    - 参加の種類: Azure **AD参加しています**。

4. 次の図に示すように、残りの**** 既定の設定は変更されず、[次へ] を選択します。

    ![Autopilot プロファイルを作成する](images/df3b.png)

5. [割り当て]**** ページで、[含めるグループの選択] を選択し、Azure AD セキュリティ グループをクリックします。 **[次へ]** を選択します。
6. 概要を受け入れ、[作成] を **選択します**。 これで、Autopilot プロファイルが作成され、グループに割り当てられます。

## [登録状態の構成] ページ

ユーザーがサインインする前に OOBE 中にデバイスが DFCI 構成を適用するには、登録状態を構成する必要があります。

詳細については、「登録状態の [設定」ページを参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。


## Surface デバイスで DFCI 設定を構成する

DFCI には、ハードウェア レベルでデバイスをロックダウンすることで、より高いレベルのセキュリティを提供する UEFI 構成ポリシーの合理化されたセットが含まれています。 DFCI は、ソフトウェア レベルでのモバイル デバイス管理設定と組み合わせて使用するように設計されています。 DFCI 設定は Surface デバイスに組み込みのハードウェア コンポーネントにのみ影響し、USB Web カメラなどの接続された周辺機器には適用されません。 (ただし、Intune のデバイス制限ポリシーを使用して、ソフトウェア レベルで接続された周辺機器へのアクセスをオフにできます)。

以下の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。 

- エンドポイント マネージャーの devicemanagement.microsoft.comで、Windows > > Configuration Profiles > **"DFCI profile name"**> Properties > Settings ] を選択します。

    ![DFCI 設定を構成する](images/dfciconfig.png)

### UEFI 設定へのユーザー アクセスをブロックする

多くのお客様にとって、ユーザーが UEFI 設定を変更することをブロックする機能は非常に重要であり、DFCI を使用する主な理由です。 表 1 に示す通り、これはローカル ユーザーによる UEFI 設定の変更を許可する設定 **によって管理されます**。 この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。 そのため、ローカル ユーザーによる UEFI 設定の変更を許可することを無効に **することを強くお勧めします。**
残りの DFCI 設定では、ユーザーが使用できない機能を無効にできます。 たとえば、セキュリティが高い領域で機密情報を保護する必要がある場合は、カメラを無効にし、ユーザーが USB ドライブから起動したくない場合は、無効にすることもできます。

### 表 1. DFCI シナリオ

| デバイス管理の目標                        | 構成手順                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ローカル ユーザーが UEFI 設定を変更することをブロックする | [ **セキュリティ機能] >ローカル ユーザーによる UEFI**設定の変更を許可する] で、[なし] を **選択します**。              |
| カメラを無効にする                               | [ **組み込みのハードウェア > カメラ**] で、[無効] を **選択します**。                                       |
| マイクとスピーカーを無効にする              | [Built **in Hardware > Microphones and speakers]** で、[無効] を選択 **します**。                      |
| 無線を無効にする (Bluetooth、Wi-Fi)             | [Built **in Hardware > Radios (Bluetooth, Wi-Fi など)]** で、[無効] を選択 **します**。                   |
| 外部メディア (USB、SD) からのブートを無効にする    | [Built **in Hardware > Boot Options > Boot from external media (USB, SD)**] で、[無効] を選択 **します**。 |

> [!CAUTION]
> Disable **radios (Bluetooth, Wi-Fi)** 設定は、ワイヤード (有線) イーサネット接続を備えるデバイスでのみ使用してください。
 
> [!NOTE]
>  Intune の DFCI には、現在 Surface デバイスには適用されない 2 つの設定が含まれています。(1) CPU と IO の仮想化と (2) ネットワーク アダプターからのブートを無効にします。
 
Intune には、管理権限を委任するためのスコープ タグと、デバイスの種類を管理するための適用性ルールが提供されています。 ポリシー管理のサポートとすべての DFCI 設定の詳細については、Microsoft Intune のドキュメント [を参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。

## Autopilot でデバイスを登録する

上記のように、DFCI は、リセラーまたはディストリビューターによって Windows Autopilot に登録されているデバイスにのみ適用できます。また、Surface Pro 7+、Surface Laptop Go、Surface Pro 7、Surface Pro X、Surface Laptop 3 でのみサポートされます。 セキュリティ上の理由から、デバイスを Autopilot に "セルフ プロビジョニング" できません。 詳しくは、Windows Autopilot の Surface [登録サポートに関するページをご覧ください](surface-autopilot-registration-support.md)。 

## Autopilot デバイスを手動で同期する

Intune ポリシー設定は通常、ほぼ即座に適用されます。ただし、設定が対象デバイスに適用される前に、10 分の遅延が発生する可能性があります。 まれな状況では、最大 8 時間の遅延が発生する可能性があります。 (テスト シナリオなど) 設定をできるだけ早く適用するには、ターゲット デバイスを手動で同期できます。

- In Endpoint Manager at devicemanagement.microsoft.com, go **to Devices > Device enrollment > Windows enrollment > Windows Autopilot Devices** and select **Sync**.

 詳しくは、「Windows デバイスを手動 [で同期する」をご覧ください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。

> [!NOTE]
> UEFI で直接設定を調整する場合は、デバイスが標準の Windows ログインに完全に再起動することを確認する必要があります。

## DFCI で管理されるデバイスでの UEFI 設定の確認

テスト環境では、Surface UEFI インターフェイスの設定を確認できます。

1. Surface UEFI を開きます。ボリューム**ボタンと****電源**ボタンを同時に押す必要があります。
2. [デバイス **] を選択します**。 次の図に示すように、UEFI メニューには構成済みの設定が反映されます。

    ![Surface UEFI](images/df3.png)

    次の点に注意してください。

      - ローカル ユーザーによる **UEFI** 設定の変更を許可する設定が [なし] に設定されている場合、設定は灰色表示されます。
      - マイクとスピーカーが無効に設定されているので、 **オーディオがオフ** に設定 **されています**。

## DFCI ポリシー設定の削除

DFCI プロファイルを作成する場合、構成済みのすべての設定は、プロファイルの管理範囲内のすべてのデバイスで有効なままです。 DFCI ポリシー設定は、DFCI プロファイルを直接編集することでのみ削除できます。

元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。

## DFCI 管理の削除

**DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻す方法:**

1. Intune からデバイスをリタイアします。
    1. In Endpoint Manager at devicemanagement.microsoft.com, choose **Groups > All Devices**. リタイアするデバイスを選択し、[リタイア/ワイプ **] を選択します。** 詳細については、「ワイプ、リタイア、または手動でのデバイスの登録解除を使用してデバイスを削除する」 [を参照してください](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。 
2. Intune から Autopilot 登録を削除します。
    1.  Choose **Device enrollment > Windows enrollment > Devices**.
    2. [Windows Autopilot デバイス] で、削除するデバイスを選択し、[削除] を選択 **します**。
3. Surface ブランドのイーサネット アダプターを使用して、デバイスを有線インターネットに接続します。 デバイスを再起動し、UEFI メニューを開きます (音量を上げながら電源ボタンを長押しします)。
4. [ **管理] >構成>ネットワーク** から更新] を選択し、[オプトアウト] **を選択します。**

Intune を使用してデバイスを管理し続けるが、DFCI 管理を使用しない場合は、デバイスを Autopilot に自己登録し、Intune に登録します。 DFCI は、自己登録デバイスには適用されません。

## 詳細情報
- [Ignite 2019: Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)からの Surface UEFI 設定のリモート管理の発表 
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md) 
- [Microsoft Intune の Windows デバイスで DFCI プロファイルを使用する](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
