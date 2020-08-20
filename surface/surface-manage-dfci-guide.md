---
title: Surface UEFI の設定の Intune 管理
description: この記事では、Microsoft Intune で DFCI 環境を構成し、対象の Surface デバイスのファームウェア設定を管理する方法について説明します。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 08/19/2020
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
ms.openlocfilehash: 9d83fe9b7febf996d2cb314399505ed050a69a92
ms.sourcegitcommit: b94832cba98e01014f7d184c85d79f8339e046c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2020
ms.locfileid: "10941660"
---
# Surface UEFI の設定の Intune 管理

## 概要

クラウドからデバイスを管理する機能は、IT の展開とライフサイクルにわたってプロビジョニングを行っています。 Microsoft Intune に組み込まれた (パブリック プレビューで利用 [可能にな](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)りました) に組み込まれたデバイス ファームウェア構成インターフェイス (DFCI) プロファイルを使用すると、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルに拡張します。 DFCI は、ゼロタッチ プロビジョニング、BIOS パスワードを消します。ボット オプションと組み込み周期など、セキュリティ設定を制御し、以降の高度なセキュリティ シナリオの基本的なセキュリティ設定を制御できます。 よく寄せられる質問への回答については [、「Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発信する」を参照してください](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)。

### Background

Windows 10 を実行しているコンピューターと同様に、Surface デバイスはソートシップに保存されているコードに使用されます。CPU はハード ドライブ、ディスプレイ デバイス、USB ポート、その他のデバイスとインターフェイスを使用できるようにします。 この読み取り専用メモリ (ROM) に格納されているプログラムはファームウェアと呼ばれています (動的メディアに保存されているプログラムはソフトウェアと呼ばれています)。

現在マーケットで利用できる他の Windows 10 デバイスとは対して、さまざまな UEFI 構成設定を通じてファームウェアを構成および管理できる機能を IT 管理者に提供しています。 これにより、モバイル デバイス管理 (MDM) ポリシー、構成マネージャー、グループ ポリシーを使用して実装される、ソフトウェア ベースのポリシー管理の上位のハードウェア制御が提供されます。 たとえば、重要な情報を含む、セキュリティで保護された分析領域にデバイスを展開している組織では、ハードウェア レベルで機能を削除することでカメラを使用できなくなることがあります。 デバイスのスタンドポイントから、ファームウェア設定でカメラをオフにすると、カメラを入れるのとよくなります。 追加されたセキュリティを、オペレーティング システムソフトウェア設定のみにのみ表示されるようにします。 たとえば、ドメイン環境のポリシー設定を使用して Windows オーディオ サービスを無効にした場合、ローカルの管理者は引き続きサービスを再度有効にすることができます。

### DFCI と SEMM

これまでは、ファームウェアを Surface Enterprise Management Mode (SEMM) にエントリを管理し、進行中の手動タスクのオーバーヘッドをオーバーヘッドしていました。 たとえば、SEMM は、Certificate Management プロセスの一部として 2 桁の PC にアクセスするのに IT スタッフを各 PC にてても必要としています。 SEMM は、オンプレミス環境の組織にとっても、あまり優れたソリューションですが、複雑さと IT を積が大量に利用する必要があります。

Microsoft Intune の新しく統合された UEFI ファームウェア管理機能が新しく統合されました。ハードウェアをロックする機能はシンプルであり、Microsoft エンドポイント マネージャーとして統合されるように [なりました](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)。 次の図は、デバイスに直接表示され(左側) で表示され、エンドポイント マネージャー コンソール (右) で表示される UEFI 設定を示しています。

![デバイス (左側) およびエンドポイント マネージャー コンソール (右) に表示される UEFI 設定](images/uefidfci.png)

DFCI により、DFCI によって、IT 管理者による手動操作の必要性をなくすために、正常に動作する必要がなくなります。 DFCI は、Intune のデバイス プロファイル機能を使用して、Windows AutoPilot を使用して展開されます。 デバイス プロファイルを使用すると、組織内の管理に加集されるデバイスに展開できる設定を追加および構成できます。 デバイスのプロファイルを受信すると、機能と設定が自動的に適用されます。 一般的なデバイス プロファイルの例としては、メール、デバイスの制限、VPN、Wi-Fi、管理用テンプレートなどがあります。 DFCI は、追加のデバイス プロファイルで、オンプレミス インフラストラクチャを維保持しなくても、クラウドから UEFI 構成設定を管理できます。  

## サポートされるデバイス

DFCI は、次のデバイスでサポートされています。

- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3

> [!NOTE]
> Surface Pro X では、内部カメラ、オーディオ、Wi-Fi/Bluetooth の DFCI 設定の管理をサポートしていません。

## 前提条件

- デバイスは、Microsoft クラウド ソリューション プロバイダー [(CSP)](https://partner.microsoft.com/membership/cloud-solution-provider) パートナーまたは OEM 配布リストによって Windows AutoPilot に登録する必要があります。

- Surface 用 DFCI を構成する前に  [、Microsoft Intune](https://docs.microsoft.com/intune/) および [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure AD) での AutoPilot 構成要件について理いる必要があります。

## 始める前に

Azure セキュリティ グループにターゲットの Surface デバイスADします。 セキュリティ グループの作成と管理の詳細については [、Intune ドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)。

## Surface デバイス用の DFCI 管理を構成する

DFCI 環境では、登録済みデバイスに設定を適用する設定と自動パイロット プロファイルを含む DFCI プロファイルを設定する必要があります。 ユーザーが初めてデバイスを起動したときに、OOBE セットアップ時に設定がプッシュされるようにするには、加わりのステータス プロファイルもあります。 このガイドでは、DFCI 環境を構成し、対象の Surface デバイスの UEFI 構成設定を管理する方法について説明します。

## DFCI プロファイルを作成する

DFCI ポリシー設定を構成する前に、最初に DFCI プロファイルを作成し、ターゲット デバイスを含む Azure AD セキュリティ グループに割り当てます。

1. テナントのテナントdevicemanagement.microsoft.com。
2. Microsoft エンドポイント マネージャ **ー管理センターで、[デバイスの作成] >作成して名前を入力する>選択** します。たとえば **、DFCI 構成ポリシーなどです。**
3. プ **ラットフォーム タイプに Windows 10** 以降を選択します。
4. [プロファイルの種類] ドロップダウン リストで **、[Device ファームウ** ェア構成インターフェイス] を選択して、利用可能なすべてのポリシー設定を含む DFCI ブレードを開きます。 DFCI 設定の詳細については、このページのテーブル 1 または [Intune ドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。 セットアップ プロセス中または後で DFCI プロファイルを編集することで、DFCI 設定を構成できます。

    ![DFCI プロファイルを作成する](images/df1.png)

5. **[OK] を**クリックし、[作成] を**選択します**。
6. [ **課題] を選択** し **、[グループの選択] グループ** に、ターゲット デバイスを含む Azure AD セキュリティ グループを選択します。次の図に示すように、ターゲット デバイスを含む Azure セキュリティ グループが選択されます。 **[保存]** をクリックします。

    ![セキュリティ グループの割り当て](images/df2a.png)

## Autopilot プロファイルの作成

1. devicemanagement.microsoft.com のエンドポイント マネー **ジャーで、Windows の>を選択し、** 下にスクロールして **展開プロファイルに移動します**。
2. [プロ **ファイルの作成** ] を選択して名前を入力します。たとえば、 **自動パイロット プロファイルを選び**、[次へ] を **選択します**。
3. 次の設定を選択します。

    - 展開モード: **ユーザー ドライブ**。
    - 結合の種類: Azure **AD結合されています**。

4. 下の図に示すように、残りの既定の設定は変更されていないままにして、[ **次**へ] を選びます。

    ![Autopilot プロファイルの作成](images/df3b.png)

5. [課題] ページで、[Azure とセキュリティ **グループを** 追加するグループを選択ADクリックします。 **[次へ]** を選択します。
6. 概要を承諾してから、[作成] を **選択します**。 これで AutoPilot プロファイルが作成され、グループに割り当てられています。

## 加集の状態ページを構成する

ユーザーがサインインする前に OOBE の間に DFCI 構成を適用するには、加注ステータスを構成する必要があります。

詳細については、「加えたことを確認する [」のページを参照してください](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status)。


## Surface デバイスで DFCI 設定を構成する

DFCI には、ハードウェア レベルでデバイスをロックダウンして、追加のセキュリティ レベルを提供する UEFI 構成ポリシーの効率化されたセットが含まれています。 DFCI は、ソフトウェア レベルでモバイル デバイス管理設定とを使用することで使用されるように設計されています。 DFCI 設定は、Surface デバイスに組み込まれたハードウェア コンポーネントにのみ影響し、USB Web カメラなどのリニシャル接続の選択にも拡張されないことに注意してください。 ただし、Intune でデバイス制限ポリシーを使用して、ソフトウェア レベルで添付されている機内者へのアクセスをオフにすることができます。)

次の図に示すように、エンドポイント マネージャーから DFCI プロファイルを編集して、DFCI ポリシー設定を構成します。 

- devicemanagement.microsoft.com エンドポイント マネージャーで **、Windows >構成プロ >ファイル名> "DFCI プロファイル名" >のプロパティ>選択します**。

    ![DFCI 設定を構成する](images/dfciconfig.png)

### UEFI 設定へのユーザー アクセスのブロック

多くのお客様にとって、ユーザーが UEFI 設定の変更を禁止する機能は重要であり、DFCI を使用する主な理由は重要です。 テーブル 1 に示されているように、これはローカル ユーザーに UEFI 設定を変更する設定 **によって管理されます**。 この設定を編集または構成しない場合、ローカル ユーザーは Intune で管理されていない UEFI 設定を変更できます。 そのため、ローカル ユーザーに UEFI 設定の変更を許可することを強 **くお勧めします。**
残りの DFCI 設定では、他の方法では、他の方法ではユーザーが使用できるようにする機能をオフにすることができます。 たとえば、高度にセキュリティで保護された領域で機関情報を保護する必要がある場合、カメラを無効にしたり、ユーザーが USB ドライブからブードを起動しないようにしたりする場合は、無効にすることもできます。

### 表 1. DFCI シナリオ

| デバイス管理の目標                        | 構成手順                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ローカル ユーザーが UEFI 設定を変更できないことを禁止する | [**セキュリティ機能] >UEFI 設定の変更を許可する] で [****なし] を選びます**。              |
| カメラを無効にする                               | ハ **ードウェアの組み込みの>で、[無効**] を **選択します**。                                       |
| マイクとスピーカーを無効にする              | ハ **ードウェアの組み込み>マ**イクとスピーカーで、[無効] を **選択します**。                      |
| ラジオを無効にBluetooth (Wi-Fi)             | ハ **ードウェア>ラジオ (Bluetooth Wi-Fi**など) で、[無効] を **選択します**。                   |
| 外部メディア (USB、SD) からのボットの無効化    | ハ **ードウェアの組み込みの> ブート オプション > ブ**ートからボットを表示する) で、[ **無効にする] を選択します**。 |

> [!CAUTION]
> 無 **線接続のBluetoothデバイスで** のみ、[無効にする] の設定を使用する必要があります。
 
> [!NOTE]
>  Intune の DFCI には、現在、Surface デバイスに適用されない 2 つの設定が含まれます。(1) CPU と IO 仮想化、(2) ネットワーク アダプターから Boot を無効にします。
 
Intune では、デバイス タイプを管理する管理権限と適用のルールを代理人にするスコープ タグを提供します。 ポリシー管理サポートとすべての DFCI 設定の詳細については [、Microsoft Intune のドキュメントを参照してください](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)。

## AutoPilot でデバイスを登録する

前述のように、DFCI は、再保護者または配布者が Windows Autopilot に登録されているデバイスにのみ適用でき、現在は Surface Pro 7、Surface Pro X、Surface Laptop 3 でのみサポートされています。 セキュリティ上の理えから、デバイスを AutoPilot に "セルフプロビジョニング" することはできません。

## 自動デバイスを手動で同期する

通常、Intune ポリシー設定はほぼすぐに適用されますが、設定が対象デバイスに反映されるまでに 10 分かかる場合があります。 まず、最大 8 時間の遅延が可能です。 設定が可能な限りすぐに (テスト シナリオなど) を確かめるようにするには、ターゲット デバイスを手動で同期できます。

- devicemanagement.microsoft.com のエンドポイント マ**ネージャー >で、Windows Autopilot デバイス> Windows の加入>Windows の加入>を確認し、[同期] を****選択します**。

 詳細については、「Windows デバイスを [手動で同期する」を参照してください](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。

> [!NOTE]
> UEFI で設定を直接調整する場合、デバイスが標準の Windows ログインに完全に再起動されるようにする必要があります。

## DFCI で管理されているデバイスでの UEFI 設定の確認

テスト環境では、Surface UEFI インターフェイスで設定を確認できます。

1. Surface UEFI を開きます。この場合、ボリューム + ボタンと**電**源**ボ**タンの押下が同時に押されます。
2. [デバイス **] を選びます**。 次の図に示すように、構成された設定が UEFI メニューに表示されます。

    ![Surface UEFI](images/df3.png)

    方法は次のとおりです。

      - ローカル ユーザーに **UEFI** 設定の変更を許可する設定が [なし] に設定されているため、設定はグレー表示されます。
      - マイクとスピーカーが無効に設定されているため、**オーディオはオフ****に設定されています**。

## DFCI ポリシー設定の削除

DFCI プロファイルを作成する場合、構成されたすべての設定は、管理のためのプロファイルのスコープ内のすべてのデバイスで有効です。 DFCI プロファイルを直接編集することで、DFCI ポリシー設定を削除できます。

元の DFCI プロファイルが削除されている場合は、新しいプロファイルを作成し、必要に合って設定を編集することで、ポリシー設定を削除できます。

## DFCI 管理の削除

**DFCI 管理を削除してデバイスを出発新状態に戻すには:**

1. Intune からデバイスを廃止します。
    1. エンドポイント マネージャdevicemanagement.microsoft.comで、[グループ **>] を選択します**。 回復するデバイスを選択し、[廃 **止/ワイプ] を選択します。** デバイスの追加や手動の解除の詳細については、ワイプ、廃止、またはデバイスの [追加を手動で解除します](https://docs.microsoft.com/intune/remote-actions/devices-wipe)。 
2. Intune から自動登録を削除します。
    1.  **デバイスの加入>を >選択します**。
    2. Windows Autopilot デバイスで、削除するデバイスを選択し、[削除] を選択 **します**。
3. Surface ブランド イーサネット アダプターで有線インターネットに接続します。 デバイスを再起動し、UEFI メニューを開きます (電源ボタンを押したままにしてから、電源ボタンを押したままにします)。
4. [ **管理] >ネットワークからの [>を更新を構成** してから [ **オプトアウト] を選びます。**

Intune でデバイスを管理し、DFCI 管理がなくても、DFCI 管理がない場合は、デバイスを AutoPilot に登録し、Intune に登録します。 自己登録デバイスには DFCI は適用されません。

## 詳細情報
- [Ignite 2019: Intune から Surface UEFI 設定のリモート管理を発行する](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
[Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md) 
- [Microsoft Intune で Windows デバイスで DFCI プロファイルを使用する](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)
