---
title: Surface UEFI の設定の Intune 管理
description: この記事では、ターゲットとなる Surface デバイスのファームウェア設定Microsoft Intune管理するために DFCI 環境を構成する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 04/13/2021
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
- Surface Laptop 4
ms.openlocfilehash: b74aeab45dd2354550f0dff712af5b37b853111c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576517"
---
# <a name="intune-management-of-surface-uefi-settings"></a>Surface UEFI の設定の Intune 管理

## <a name="introduction"></a>はじめに

クラウドからデバイスを管理する機能により、ライフサイクル全体にわたる IT の展開とプロビジョニングが大幅に簡素化されました。 デバイス ファームウェア構成インターフェイス (DFCI) プロファイルを[Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)に組み込むと、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。 DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を築きます。 よく寄せられる質問に対する回答については [、「Ignite 2019: Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)から Surface UEFI 設定のリモート管理を発表する」を参照してください。

### <a name="background"></a>Background

Surface デバイスは、Windows 10 を実行しているコンピューターと同様に、SoC に格納されているコードを使用して、CPU がハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスできます。 この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに格納されているプログラムはソフトウェアと呼ばれています)。

現在市場でWindows 10されている他のデバイスとは対照的に、Surface は、豊富な UEFI 構成設定を使用してファームウェアを構成および管理する機能を IT 管理者に提供します。 これにより、モバイル デバイス管理 (MDM) ポリシー、Configuration Manager、またはグループ ポリシーを介して実装されるソフトウェア ベースのポリシー管理の上に、ハードウェア制御の層が提供されます。 たとえば、機密情報を含むセキュリティの高い領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することで、カメラの使用を防止できます。 デバイスの観点から、ファームウェア設定を介してカメラをオフに設定すると、カメラを物理的に取り外すのと同じです。 ファームウェア レベルでの管理に関する追加のセキュリティと、オペレーティング システム のソフトウェア設定にのみ依存するセキュリティを比較します。 たとえば、ドメイン環境でポリシー設定をWindowsオーディオ サービスを無効にした場合でも、ローカル管理者はサービスを再び有効にできます。

### <a name="dfci-versus-semm"></a>DFCI と SEMM の比較

以前は、ファームウェアを管理するには、継続的な手動 IT 集中タスクのオーバーヘッドを利用して、Surface Enterprise 管理モード (SEMM) にデバイスを登録する必要があります。 たとえば、SEMM では、証明書管理プロセスの一環として、IT スタッフが各 PC に物理的にアクセスして 2 桁のピンを入力する必要があります。 SEMM は、厳密にオンプレミス環境の組織に対する優れたソリューションですが、複雑で IT の負荷の高い要件により、使用コストが高い状態になります。

 Microsoft Intune に統合された UEFI ファームウェア管理機能を使用すると、ハードウェアをロックダウンする機能が簡素化され、プロビジョニング、セキュリティ、および合理化された更新のための新機能を 1 つのコンソールで簡単かつ簡単に使用できます。現在は Microsoft エンドポイント マネージャー と[統合](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)されています。 次の図は、デバイス (左) で直接表示され、コンソール (右) で表示される UEFI エンドポイント マネージャー示しています。

![デバイス (左) とコンソール (右) に表示エンドポイント マネージャー UEFI 設定](images/uefidfci.png)

重要な点として、DFCI はゼロ タッチ管理を可能にし、IT 管理者による手動操作の必要性を排除します。 DFCI は、Intune のWindows機能を使用して、自動パイロットを介して展開されます。 デバイス プロファイルを使用すると、組織の管理に登録されているデバイスに展開できる設定を追加および構成できます。 デバイスがデバイス プロファイルを受信すると、機能と設定が自動的に適用されます。 一般的なデバイス プロファイルの例としては、メール、デバイス制限、VPN、Wi-Fi、管理用テンプレートがあります。 DFCI は、単に追加のデバイス プロファイルで、オンプレミスインフラストラクチャを維持することなく、クラウドから UEFI 構成設定を管理できます。  

## <a name="supported-devices"></a>サポートされるデバイス

DFCI は、次のデバイスでサポートされています。

- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface LaptopGo
- Surface Laptop 4

> [!NOTE]
> Surface ProX は、組み込みのカメラ、オーディオ、および Wi-Fi/Bluetooth の DFCI 設定管理をサポートBluetooth。

## <a name="prerequisites"></a>前提条件

- デバイスは、CSP (CSP) パートナー Windows OEM ディストリビューターによって[、Microsoft クラウド ソリューション プロバイダー Autopilot](https://partner.microsoft.com/membership/cloud-solution-provider)に登録されている必要があります。

- SURFACE 用の DFCI を構成する前に、Microsoft Intune および Azure Active Directory [](https://docs.microsoft.com/intune/) [(Azure](https://docs.microsoft.com/azure/active-directory/) AD) のオートパイロット構成要件に精通している必要があります。

## <a name="before-you-begin"></a>始める前に

対象の Surface デバイスを Azure ADに追加します。 セキュリティ グループの作成と管理の詳細については、「Intune のドキュメント」 [を参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。

## <a name="configure-dfci-management-for-surface-devices"></a>Surface デバイスの DFCI 管理を構成する

DFCI 環境では、設定を含む DFCI プロファイルと、登録済みデバイスに設定を適用する自動パイロット プロファイルを設定する必要があります。 ユーザーが最初にデバイスを起動するときに、OOBE セットアップ中に設定がプッシュダウンされるのを確認するには、登録状態プロファイルも推奨されます。 このガイドでは、DFCI 環境を構成し、対象となる Surface デバイスの UEFI 構成設定を管理する方法について説明します。

## <a name="create-dfci-profile"></a>DFCI プロファイルの作成

DFCI ポリシー設定を構成する前に、まず DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てる必要があります。

1. テナントにサインイン devicemanagement.microsoft.com。
2. [管理センター Microsoft エンドポイント マネージャーで、[デバイスと構成プロファイル>プロファイル>作成] を選択し **、名前**を入力します。たとえば **、DFCI 構成ポリシーです。**
3. プラットフォームの**Windows 10を選択します**。
4. [プロファイルの種類] ドロップダウン リストで、[デバイス ファームウェア **構成** インターフェイス] を選択して、使用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。 DFCI 設定の詳細については、このページの表 1 または Intune のドキュメントを [参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。 初期セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。

    ![DFCI プロファイルの作成](images/df1.png)

5. **[OK] をクリック**し、[作成]**を選択します**。
6. [**割り当て**] を選択し、[グループの選択] で、次の図に示すようにADデバイスを含む Azure AD セキュリティ グループを選択します。 **** **[保存]** をクリックします。

    ![セキュリティ グループの割り当て](images/df2a.png)

## <a name="create-autopilot-profile"></a>自動パイロット プロファイルの作成

1. [エンドポイント マネージャーで devicemanagement.microsoft.com 登録するデバイス> Windows**選択**し、[展開プロファイル] まで下**にスクロールします**。
2. [プロファイル **の作成] を** 選択し、名前を入力します。たとえば、[マイ オート **パイロット プロファイル] を選択し、[** 次へ] を **選択します**。
3. 次の設定を選択します。

    - 展開モード: **User-Driven .**
    - 参加の種類: Azure **AD参加しています**。

4. 次の図に示すように、残りの既定の設定はそのままにし、[ **次**へ] を選択します。

    ![自動パイロット プロファイルの作成](images/df3b.png)

5. [割り当て] ページで、[含めるグループの選択] を **選択** し、Azure セキュリティ グループADクリックします。 **[次へ]** を選択します。
6. 概要を受け入れ、[作成] を **選択します**。 自動パイロット プロファイルが作成され、グループに割り当てられます。

## <a name="configure-enrollment-status-page"></a>[登録状態の構成] ページ

ユーザーがサインインする前に、OOBE 中にデバイスが DFCI 構成を適用するには、登録状態を構成する必要があります。

詳細については、「登録状態ページの [設定」を参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。


## <a name="configure-dfci-settings-on-surface-devices"></a>Surface デバイスで DFCI 設定を構成する

DFCI には、ハードウェア レベルでデバイスをロックダウンすることで、より高いレベルのセキュリティを提供する UEFI 構成ポリシーの合理化されたセットが含まれています。 DFCI は、ソフトウェア レベルでのモバイル デバイス管理設定と組み合わせて使用するように設計されています。 DFCI 設定は Surface デバイスに組み込みのハードウェア コンポーネントにのみ影響し、USB Web カメラなどの接続された周辺機器には適用されません。 (ただし、Intune でデバイス制限ポリシーを使用して、ソフトウェア レベルで接続されている周辺機器へのアクセスをオフにできます)。

DFCI ポリシー設定を構成するには、次の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集します。 

- [エンドポイント マネージャー] devicemanagement.microsoft.com で、[デバイス] > Windows >構成プロファイル> **"DFCI**プロファイル名" >を選択> 設定。

    ![DFCI 設定の構成](images/dfciconfig.png)

### <a name="block-user-access-to-uefi-settings"></a>UEFI 設定へのユーザー アクセスをブロックする

多くのお客様にとって、ユーザーが UEFI 設定を変更することをブロックする機能は非常に重要であり、DFCI を使用する主な理由です。 表 1 に示す通り、これは [ローカル ユーザーによる UEFI 設定の変更を許可する] の設定 **を使用して管理されます**。 この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。 そのため、ローカル ユーザーによる UEFI 設定の変更を許可するを無効 **にすることを強くお勧めします。**
残りの DFCI 設定を使用すると、ユーザーが利用できる機能を無効にできます。 たとえば、セキュリティが高い領域で機密情報を保護する必要がある場合は、カメラを無効にし、ユーザーが USB ドライブから起動しない場合は、その情報も無効にできます。

### <a name="table-1-dfci-scenarios"></a>表 1. DFCI のシナリオ

| デバイス管理の目標                        | 構成手順                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ローカル ユーザーが UEFI 設定を変更することをブロックする | [ **セキュリティ機能] >ローカル**ユーザーによる UEFI 設定の変更を許可する] で、[なし] を **選択します**。              |
| カメラを無効にする                               | [ **ハードウェア カメラに組み込>で、[無効**] を **選択します**。                                       |
| マイクとスピーカーを無効にする              | [ **ハードウェアに組み込>マイクとスピーカー]** で、[無効] を **選択します**。                      |
| 無線を無効にする (Bluetooth Wi-Fi)             | [**ハードウェア に組み込> (Bluetooth、Wi-Fi**など) で、[無効] を**選択します**。                   |
| 外部メディアからのブートを無効にする (USB、SD)    | [ **組み込みのハードウェア > ブート オプション>外部メディア (USB、SD)** から起動する] で、[無効] を **選択します**。 |

> [!CAUTION]
> 無線**を無効にする (Bluetooth Wi-Fi)** 設定は、有線イーサネット接続を持つデバイスでのみ使用する必要があります。
 
> [!NOTE]
>  Intune の DFCI には、現在 Surface デバイスには適用されない 2 つの設定が含まれています。(1) CPU と IO の仮想化と (2) ネットワーク アダプターからのブートを無効にします。
 
Intune には、管理権限を委任するためのスコープ タグと、デバイスの種類を管理するための適用ルールが提供されています。 ポリシー管理のサポートとすべての DFCI 設定の詳細については、次のドキュメント[を](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)参照Microsoft Intuneしてください。

## <a name="register-devices-in-autopilot"></a>Autopilot にデバイスを登録する

上記のように、DFCI はリセラーまたはディストリビューターによって Windows Autopilot に登録されているデバイスにのみ適用され、Surface Pro 7+、Surface Laptop Go、Surface Pro 7、Surface Pro X、および Surface Laptop 3 でのみサポートされます。 セキュリティ上の理由から、デバイスを自動パイロットに "自己プロビジョニング" できません。 詳細については、「Surface [Registration Support for Windows」を参照してください](surface-autopilot-registration-support.md)。 

## <a name="manually-sync-autopilot-devices"></a>自動パイロット デバイスを手動で同期する

Intune ポリシー設定は通常、ほぼ即座に適用されます。対象のデバイスで設定が有効になるまで、10 分の遅延が発生する可能性があります。 まれな状況では、最大 8 時間の遅延が発生する可能性があります。 設定ができるだけ早く適用される (テスト シナリオなど) には、ターゲット デバイスを手動で同期できます。

- [エンドポイント マネージャーで devicemanagement.microsoft.com に移動し、[デバイスの登録****>自動パイロット デバイス> Windowsに> Windows同期] を選択**します**。

 詳細については、「デバイスを手動で[同期するWindows参照してください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。

> [!NOTE]
> UEFI で設定を直接調整する場合は、デバイスが標準のユーザー ログインに完全に再起動Windowsがあります。

## <a name="verifying-uefi-settings-on-dfci-managed-devices"></a>DFCI 管理デバイスでの UEFI 設定の確認

テスト環境では、Surface UEFI インターフェイスで設定を確認できます。

1. Surface UEFI を開きます。ボリューム **+** ボタンと **電源** ボタンを同時に押します。
2. [デバイス **] を選択します**。 次の図に示すように、UEFI メニューには構成済みの設定が反映されます。

    ![Surface UEFI](images/df3.png)

    次の方法に注意してください。

      - ローカル ユーザーによる **UEFI** 設定の変更を許可する設定が [なし] に設定されている場合、設定はグレー表示されます。
      - マイクとスピーカーが [無効] に設定されている場合、オーディオ**はオフに****設定されます**。

## <a name="removing-dfci-policy-settings"></a>DFCI ポリシー設定の削除

DFCI プロファイルを作成すると、構成された設定はすべて、プロファイルの管理範囲内のすべてのデバイスで有効になります。 DFCI ポリシー設定は、DFCI プロファイルを直接編集することでのみ削除できます。

元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に応じて設定を編集することで、ポリシー設定を削除できます。

## <a name="removing-dfci-management"></a>DFCI 管理の削除

**DFCI 管理を削除し、デバイスを出荷時の新しい状態に戻す方法:**

1. Intune からデバイスを削除します。
    1. [エンドポイント マネージャー] で devicemanagement.microsoft.com[グループ]**を選択>すべてのデバイスを選択します**。 廃止するデバイスを選択し、[引退/ワイプ **] を選択します。** 詳細については、「デバイスのワイプ、削除、または手動での登録解除を使用してデバイスを削除する」 [を参照してください](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。 
2. Intune から自動パイロット登録を削除します。
    1.  [**デバイスの登録] > Windows [デバイス>選択します**。
    2. [Windows] で、削除するデバイスを選択し、[削除] を選択**します**。
3. Connectブランドのイーサネット アダプターを使用して、デバイスを有線インターネットに接続します。 デバイスを再起動し、UEFI メニューを開きます (音量アップ ボタンを長押ししながら、電源ボタンを長押しします)。
4. [ **管理] > [ネットワーク>更新の構成] を選択し** 、[オプトアウト] **を選択します。**

Intune でデバイスを管理し続けるが、DFCI 管理を行わずに、デバイスを自動パイロットに自己登録し、Intune に登録します。 DFCI は自己登録デバイスには適用されません。

## <a name="learn-more"></a>詳細情報
- [Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発表する](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windowsオートパイロット](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md) 
- [デバイス内のデバイスで DFCI プロファイルWindows使用Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
