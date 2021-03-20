---
title: Surface Enterprise Management Mode (Surface)
description: Surface UEFI を使用した Surface デバイスのこの機能が、組織内のファームウェア設定のセキュリティ保護と管理に役立つ方法について説明します。
keywords: uefi、構成、ファームウェア、セキュア、semm
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
audience: itpro
ms.date: 03/18/2021
ms.openlocfilehash: 011f4d0270c47b976e10dbece2adb70559222b79
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442185"
---
# <a name="microsoft-surface-enterprise-management-mode"></a>Microsoft Surface Enterprise 管理モード

Microsoft Surface Enterprise Management Mode (SEMM) は、Surface UEFI を備える Surface デバイスの機能で、組織内のファームウェア設定をセキュリティで保護および管理できます。 SEMM を使用すると、IT 担当者は UEFI 設定の構成を準備し、Surface デバイスにインストールできます。 UEFI 設定を構成する機能に加えて、SEMM は証明書を使用して、承認されていない改ざんや削除から構成を保護します。 SEMM は、Surface Hub 2S を Windows 10 Pro および Enterprise に移行できる要件です。

>[!NOTE]
>SEMM は Surface UEFI ファームウェアを持つデバイスでのみ使用できます。 これには、Surface Pro 7+、Surface Pro 7、Surface Pro X、Surface Hub 2S、Intel プロセッサを搭載した Surface Laptop 3 商用 SKU、Surface Laptop Go などのほとんどの Surface デバイスが含まれます。 SEMM は、AMD プロセッサ付き 15" Surface Laptop 3 SKU ではサポートされていません (小売 SKU としてのみ利用可能)。 

Surface デバイスが SEMM によって構成され、SEMM 証明書で保護されている場合、デバイスは SEMM *に登録されたと* 見なされます。 SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM で登録されていない *と* 見なされます。

SEMM を管理し、Surface デバイスを登録するために使用できる管理オプションには、スタンドアロン ツールまたは Microsoft Endpoint Configuration Manager との統合の 2 つがあります。 この記事では、Microsoft Surface UEFI コンフィギュレーターと呼ばれる SEMM スタンドアロン ツールについて説明します。 Microsoft Endpoint Configuration Manager を使用して SEMM を管理する方法の詳細については、「Use Microsoft Endpoint Configuration Manager を使用して SEMM を使用してデバイスを管理する」 [を参照してください](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)。

> [!NOTE]
> SEMM は、UEFI マネージャーを介して Surface Pro X でのみサポートされます。 IT 向け Surface Tools から UEFI [マネージャーをダウンロードできます](https://www.microsoft.com/download/details.aspx?id=46703)。 詳細については [、「Surface Pro X の展開、管理、およびサービス」を参照してください](surface-pro-arm-app-management.md)。


## <a name="microsoft-surface-uefi-configurator"></a>Microsoft Surface UEFI コンフィギュレーター

図 1 に示すように、SEMM のプライマリ ワークスペースは Microsoft Surface UEFI コンフィギュレーターです。 Microsoft Surface UEFI Configureator は、Surface デバイスでの SEMM の登録、構成、および登録解除に使用される Windows インストーラー (.msi) パッケージまたは WinPE イメージの作成に使用されるツールです。 これらのパッケージには、UEFI の設定を指定する構成ファイルが含まれています。 SEMM パッケージには証明書も含まれています。この証明書はファームウェアにインストールおよび保存され、UEFI 設定を適用する前に構成ファイルの署名を確認するために使用されます。

>[!TIP]
>Surface UEFI コンフィギュレーターと SEMM を使用して、Surface ドック 2 のポートを管理できます。 詳細については [、「Secure Surface Dock 2 ports with SEMM」を参照してください](secure-surface-dock-ports-semm.md)。

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*図 1.  Microsoft Surface UEFI コンフィギュレーター*


Microsoft Surface UEFI コンフィギュレーター ツールは、次の 3 つのモードで使用できます。

* [Surface UEFI 構成パッケージ](#configuration-package)。 このモードを使用して、Surface UEFI 構成パッケージを作成して、Surface デバイスを SEMM に登録し、登録済みデバイスで UEFI 設定を構成します。
* [Surface UEFI リセット パッケージ](#reset-package)。 SEMM から Surface デバイスの登録を解除するには、このモードを使用します。
* [Surface UEFI 回復要求](#recovery-request)。 このモードを使用して、回復要求に応答して、パッケージのリセット操作が成功しない SEMM から Surface デバイスの登録を解除します。


#### <a name="download-microsoft-surface-uefi-configurator"></a>Microsoft Surface UEFI コンフィギュレーターをダウンロードする

Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロード センターの [[Surface Tools for IT]](https://www.microsoft.com/download/details.aspx?id=46703) ページからダウンロードできます。

### <a name="configuration-package"></a>構成パッケージ

Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装および管理するための主要なメカニズムです。 これらのパッケージには、図 2 に示すように、Microsoft Surface UEFI Configurationator でのパッケージの作成時に指定された UEFI 設定の構成ファイルと証明書ファイルが含まれています。 SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアに証明書ファイルが準備され、SEMM にデバイスが登録されます。 SEMM にデバイスを登録するときに、証明書ファイルが保存され、登録が完了する前に、SEMM 証明書の拇印の最後の 2 桁を指定して操作を確認するように求めるメッセージが表示されます。 この確認では、確認を実行するには、登録時にユーザーがデバイスに物理的に存在している必要があります。

![証明書を使用して SEMM 構成パッケージをセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*図 2.  証明書を使用して SEMM 構成パッケージをセキュリティで保護する*

SEMM [証明書の要件の](#surface-enterprise-management-mode-certificate-requirements) 詳細については、この記事の「Surface Enterprise Management Mode 証明書要件」セクションを参照してください。

>[!TIP]
>Surface UEFI のセキュリティ、デバイス、ブート構成、またはエンタープライズ管理ページを表示**** するために必要な SEMM**** を使用して UEFI パスワードを指定することもできます。 **** ****

デバイスが SEMM に登録されると、構成ファイルが読み取り、ファイルで指定された設定が UEFI に適用されます。 SEMM に既に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名がデバイス ファームウェアに保存されている証明書に対してチェックされます。 署名が一致しない場合、デバイスに変更は適用されません。

### <a name="enable-or-disable-devices-in-surface-uefi-with-semm"></a>SEMM を使用して Surface UEFI でデバイスを有効または無効にする

次の一覧は、SEMM で管理できる利用可能なすべてのデバイスを示しています。

* USB ポートのドッキング
* ボード上のオーディオ
* DGPU
* タイプ カバー
* Micro SD カード
* 前面カメラ
* 背面カメラ
* Windows Hello 用赤外線カメラ
* Bluetoothのみ
* Wi-Fi と Bluetooth
*              LTE           

 >[!NOTE]
>UEFI デバイス ページに表示される組み込みのデバイスは、デバイスまたは企業環境によって異なる場合があります。 たとえば、[UEFI デバイス] ページは Surface Pro X ではサポートされていません。LTE は、LTE 搭載デバイスにのみ表示されます。 
### <a name="configure-advanced-settings-with-semm"></a>SEMM を使用して詳細設定を構成する
**表 1. 詳細設定**

| 設定                            | 説明                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PXE ブート用 IPv6                  | PXE ブートの IPv6 サポートを管理できます。 この設定を構成しない場合、PXE ブートの IPv6 サポートは無効になります。                                                                               |
| 代替ブート                     | ブート中に [ボリューム ダウン] ボタンと [電源] ボタンの両方を押して、USB またはイーサネット デバイスに直接起動する代替ブート順序の使用を管理できます。 この設定を構成しない場合は、代替ブートが有効になります。 |
| ブート順序ロック                    | 変更を防ぐためにブート順序をロックできます。 この設定を構成しない場合、ブート順序ロックは無効になります。                                                                                                        |
| USB ブート                           | USB デバイスの起動を管理できます。 この設定を構成しない場合は、USB ブートが有効になります。                                                                                                                 |
| ネットワーク スタック                      | ネットワーク スタックのブート設定を管理できます。 この設定を構成しない場合、ネットワーク スタックのブート設定を管理する機能は無効になります。                                                                                                           |
| 自動電源オン                      | 自動電源オンのブート設定を管理できます。 この設定を構成しない場合は、自動電源オンが有効になります。                                                                                                        |
| 同時マルチスレッド (SMT) | 同時マルチスレッド (SMT) を管理して、ハイパースレッジを有効または無効にできます。 この設定を構成しない場合は、SMT が有効になります。                                                  |
|バッテリーの制限を有効にする| バッテリー制限機能を管理できます。 この設定を構成しない場合は、バッテリーの制限が有効になります。 |
| Security                           | [Surface UEFI セキュリティ] **ページを表示** します。 この設定を構成しない場合は、[セキュリティ] ページが表示されます。                                                                                                                 |
| デバイス                            | [Surface UEFI デバイス] **ページを表示** します。 この設定を構成しない場合は、[デバイス] ページが表示されます。                                                                                                                     |
| Boot                               | [Surface UEFI ブート] **ページを表示** します。 この設定を構成しない場合は、[ブート] ページが表示されます。                                                                                                                                                            |
| DateTime                           | Surface UEFI **DateTime ページを表示** します。 この設定を構成しない場合は、[DateTime] ページが表示されます。                                                                                                                |
| EnableOSMigration                          | Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できます。 この設定を構成しない場合、Surface Hub 2 デバイスは Windows 10 Team OS のみを実行できます。   注: Windows 10 Team と Windows 10 Pro/Enterprise のデュアル ブートは Surface Hub 2 では使用できません。                                                                                                           |


>[!NOTE]
>SEMM 構成パッケージを作成すると、図 3 に**** 示すように、成功ページに 2 文字が表示されます。

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*図 3.  [成功] ページに証明書の拇印の最後の 2 文字を表示する*

これらの文字は、証明書の拇印の最後の 2 文字であり、書き込みまたは記録する必要があります。 図 4 に示すように、Surface デバイスの SEMM での登録を確認するには、文字が必要です。

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*図 4:  SEMM 証明書の拇印を使用した SEMM での登録確認*

>[!NOTE]
>証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開いて、いつでも拇印を読み取りできます。 CertMgr を使用して拇印を表示するには、次の操作を行います。 
>1. .pfx ファイルを右クリックし、[開く] を **クリックします**。
>2. ナビゲーション ウィンドウでフォルダーを展開します。
>3. **[証明書]** をクリックします。
>4. メイン ウィンドウで証明書を右クリックし、[開く] を **クリックします**。
>5. [詳細] **タブをクリック** します。
>6. **[表示** ] **ドロップダウン メニュー** で [すべて] または [ **プロパティのみ]** を選択する必要があります。
>7. [拇印] フィールド **を選択します**。

SURFACE デバイスを SEMM に登録するか、構成パッケージから UEFI 構成を適用するには、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行する必要があります。 アプリケーション展開またはオペレーティング システム展開テクノロジ[(Microsoft Endpoint Configuration Manager、Microsoft Deployment configuration Manager](https://technet.microsoft.com/library/mt346023)など) を使用[Toolkit。](https://technet.microsoft.com/windows/dn475741) SEMM にデバイスを登録する場合は、デバイスの登録を確認するために物理的に存在する必要があります。 SEMM に既に登録されているデバイスに構成を適用する場合、ユーザーの操作は必要ありません。

SURFACE デバイスを [SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)に登録する方法、または SEMM を使用して Surface UEFI 構成を適用する方法の詳細なチュートリアルについては、「SEMM を使用して Surface デバイスを登録して構成する」を参照してください。

### <a name="reset-package"></a>パッケージのリセット

Surface UEFI リセット パッケージは、SEMM から Surface デバイスの登録を解除するために、1 つのタスクのみを実行するために使用されます。 リセット パッケージには、デバイスのファームウェアから SEMM 証明書を削除し、UEFI 設定を出荷時の既定にリセットする署名済み手順が含まれています。 Surface UEFI 構成パッケージと同様に、Surface デバイスでプロビジョニングされたのと同じ SEMM 証明書でリセット パッケージに署名する必要があります。 SEMM リセット パッケージを作成する場合は、リセットする Surface デバイスのシリアル番号を指定する必要があります。 SEMM リセット パッケージは汎用的ではなく、1 つのデバイスに固有です。

### <a name="recovery-request"></a>回復要求

一部のシナリオでは、Surface UEFI リセット パッケージを使用できない場合があります。 (たとえば、Windows が Surface デバイスで使用できなくなった場合など)。これらのシナリオでは、回復要求操作を使用して、Surface UEFI **** (図 5 に示す) のエンタープライズ管理ページを介して SEMM から Surface デバイスの登録を解除できます。

> [!div class="mx-imgBorder"]
> ![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*図 5:  [エンタープライズ管理] ページで SEMM 回復要求を開始する*

[エンタープライズ管理] ページの **プロセスを** 使用して Surface デバイスの SEMM をリセットすると、リセット要求が提供されます。 このリセット要求は、ファイルとして USB ドライブに保存したり、テキストとしてコピーしたり、モバイル デバイスを使用して QR コードとして読み取って、電子メールやメッセージを簡単に送信できます。 Microsoft Surface UEFI Configurator Reset Request オプションを使用して、要求のリセット ファイルを読み込むか、要求のリセット テキストまたは QR コードを入力します。 Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスで入力できる検証コードを生成します。 Surface デバイスでコードを入力し、[再起動] を **クリック**すると、デバイスは SEMM から登録解除されます。 

>[!NOTE]
>リセット要求の有効期限は、作成後 2 時間です。

SEMM から Surface デバイスの登録を解除する方法の詳細なチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)からの Surface デバイスの登録を解除する」を参照してください。

## <a name="surface-enterprise-management-mode-certificate-requirements"></a>Surface Enterprise Management Mode 証明書の要件
MICROSOFT Surface UEFI コンフィギュレーターで SEMM を使用するには、UEFI 設定を適用する前に、構成ファイルの署名を確認するための証明書が必要です。 この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI の設定を変更できます。

>[!NOTE]
>SEMM 証明書は、登録済み Surface デバイスで SEMM または Surface UEFI の設定に対する変更を実行するために必要です。 SEMM 証明書が破損または紛失した場合、SEMM を削除またはリセットすることはできません。 バックアップと回復に適したソリューションを使用して、SEMM 証明書を適切に管理します。

Microsoft Surface UEFI コンフィギュレーター ツールで作成されたパッケージは、証明書で署名されます。 この証明書を使用すると、デバイスが SEMM に登録されると、承認済み証明書で作成されたパッケージのみを使用して UEFI の設定を変更できます。 
### <a name="recommended-certificate-settings"></a>推奨される証明書の設定
SEMM 証明書には、次の設定が推奨されます。

* **キー アルゴリズム** – RSA 
* **キーの長** さ – 2048
* **ハッシュ アルゴリズム** – SHA-256
* **種類** – SSL サーバー認証
* **キー使用法** – デジタル署名、キーエンシファーメント
* **プロバイダー** – Microsoft Enhanced RSA および AES 暗号化プロバイダー
* **有効期限 –** 証明書の作成から 15 か月
* **キーのエクスポート ポリシー** – エクスポート可能

また、中間証明機関 (CA) が SEMM 専用である 2 層公開キー基盤 (PKI) アーキテクチャで SEMM 証明書を認証し、証明書の失効を有効にしてください。 2 層 PKI 構成の詳細については、「Test Lab Guide: Deploying a AD [CS Two-Tier」を参照してください](https://technet.microsoft.com/library/hh831348)。

### <a name="self-signed-certificate"></a>自己署名証明書 
次の PowerShell スクリプトの例を使用して、概念実証シナリオで使用する自己署名証明書を作成できます。
このスクリプトを使用するには、次のテキストをメモ帳にコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。 

> [!NOTE]
> このスクリプトは、 のパスワードを持つ証明書を作成します `12345678` 。このスクリプトによって生成される証明書は、実稼働環境では推奨されません。
  
```powershell
if (-not (Test-Path "Demo Certificate"))  { New-Item -ItemType Directory -Force -Path "Demo Certificate" }
if (Test-Path "Demo Certificate\TempOwner.pfx") { Remove-Item "Demo Certificate\TempOwner.pfx" }

# Generate the Ownership private signing key with password 12345678
$pw = ConvertTo-SecureString "12345678" -AsPlainText -Force

$TestUefiV2 = New-SelfSignedCertificate `
  -Subject "CN=Surface Demo Kit, O=Contoso Corporation, C=US" `
  -Type SSLServerAuthentication `
  -HashAlgorithm sha256 `
  -KeyAlgorithm RSA `
  -KeyLength 2048 `
  -KeyUsage KeyEncipherment `
  -KeyUsageProperty All `
  -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
  -NotAfter (Get-Date).AddYears(25) `
  -TextExtension @("2.5.29.37={text}1.2.840.113549.1.1.1") `
  -KeyExportPolicy Exportable

$TestUefiV2 | Export-PfxCertificate -Password $pw -FilePath "Demo Certificate\TempOwner.pfx"
```

>[!IMPORTANT]
>SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書をプライベート キーとパスワード保護でエクスポートする必要があります。 必要に応じて、SEMM 証明書ファイル (.pfx) と証明書パスワードを選択するように求めるメッセージが表示されます。

1.  スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM。
2.  サンプル スクリプトをメモ帳または同等のテキスト エディターにコピーし、ファイルを PowerShell スクリプト (.ps1) として保存します。
3.  管理者資格情報を使用して PC にサインインし、管理者特権の PowerShell セッションを開きます。
4.  スクリプトの実行を許可するアクセス許可が設定されていないことを確認します。 既定では、実行ポリシーを変更しない限り、スクリプトの実行がブロックされます。 詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。
5.  コマンド プロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。 このスクリプトは、TempOwner.pfx という名前のデモ証明書を作成します。

または、PowerShell を使用して独自の自己署名証明書を作成できます。 詳細については [、「New-SelfSignedCertificate」の PowerShell ドキュメントを参照してください](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。




>[!NOTE]
>PKI インフラストラクチャでオフライン ルートを使用する組織の場合、SEMM 証明書を認証するには、ルート CA に接続された環境で Microsoft Surface UEFI コンフィギュレーターを実行する必要があります。 Microsoft Surface UEFI Configurator によって生成されたパッケージはファイルとして転送されるため、USB スティックなどのリムーバブル ストレージを使用してオフライン ネットワーク環境の外部に転送できます。

### <a name="managing-certificates-faq"></a>証明書の管理に関する FAQ

推奨される *最小長* は 15 か月です。 有効期限が 15 か月未満の証明書を使用するか、15 か月以上経過した証明書を使用できます。

>[!NOTE] 
>証明書の有効期限が切れると、証明書は自動的に更新されません。 


**有効期限が切れた証明書は、SEMM 登録デバイスの機能に影響しますか?**<br><br>
いいえ、証明書は SEMM の IT 管理者管理タスクにのみ影響し、有効期限が切れるとデバイス機能には影響しません。


**SEMM パッケージと証明書を持つすべてのコンピューターで更新する必要がありますか?**

SEMM のリセットまたは回復を機能するには、証明書が有効で有効期限が切れていない必要があります。 

**注文したサーフェスごとにパッケージを一括リセットできますか? 環境内のすべてのコンピューターをリセットするビルドは可能ですか?**

特定のデバイスの種類の構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセット パッケージを作成することもできます。 証明書がまだ有効な場合は、PowerShell を使用してリセット パッケージを作成して SEMM をリセットできます。

## <a name="version-history"></a>バージョン履歴

### <a name="version-2791390"></a>バージョン 2.79.139.0

このバージョンの SEMM には、次の内容が含まれます。
- Surface Pro 7+ のサポート
- ユーザー エクスペリエンスの向上


### <a name="version-2781390"></a>バージョン 2.78.139.0

このバージョンの SEMM には、次の内容が含まれます。

- Surface Laptop Go と Surface Pro X のサポート
- 新しいバージョン リリースの通知
- 所有権を変更するカスタム パッケージを作成する機能
- バグ修正

### <a name="version-2731360"></a>バージョン 2.73.136.0

このバージョンの SEMM には、次の内容が含まれます。

- SEMM を使用して Surface Hub2S でオーディオを無効にできる
- Surface Pro X for Dock 2 のサポート
- ドック 2 関連操作の UEFI マネージャーのサポート
- Surface Go リセット パッケージのバグ修正
- Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行のサポート。

### <a name="version-2711390"></a>バージョン 2.71.139.0

このバージョンの SEMM では、Surface Book 3、Surface Laptop 3、Surface Pro 7 の Surface ドック 2 管理機能のサポートが追加されています。

- オーディオ (ロック/ロック解除)、イーサネット ポート、USB ポートの有効化
- 認証済みホストと認証されていないホストの両方にドック パッケージを作成する機能

### <a name="version-2701300"></a>バージョン 2.70.130.0

このバージョンの SEMM には、次の内容が含まれます。

- Surface Go 2 のサポート
- Surface Book 3 のサポート
- バグ修正


### <a name="version-2591390"></a>バージョン 2.59.139.0

* Surface Pro 7、Surface Pro X、Surface Laptop 3 13.5" および 15" モデルと Intel プロセッサのサポート。

  > [!NOTE]
  > Surface Laptop 3 15" AMD プロセッサはサポートされていません。

- Wake on Power 機能のサポート

### <a name="version-2541390"></a>バージョン 2.54.139.0
* Surface Hub 2S のサポート
* バグ修正

### <a name="version-2431360"></a>バージョン 2.43.136.0
* マルチスレティングのシミュレーションを有効/無効にするサポート 
* 一部のデバイスで WiFi と Bluetoothのオプションを分離する 
* Surface Studio のバッテリー制限が削除されました 

### <a name="version-2261360"></a>バージョン 2.26.136.0
* Surface Studio 2 へのサポートの追加
* バッテリー制限機能

### <a name="version-2211360"></a>バージョン 2.21.136.0
* Surface Pro 6 へのサポートの追加
* Surface Laptop 2 へのサポートの追加

### <a name="version-2141360"></a>バージョン 2.14.136.0
* Surface Go へのサポートの追加

### <a name="version-291360"></a>バージョン 2.9.136.0
* Surface Book 2 へのサポートの追加
* Surface Pro LTE へのサポートの追加
* アクセシビリティの改善

### <a name="version-10740"></a>バージョン 1.0.74.0
* Surface Laptop へのサポートの追加
* Surface Pro へのサポートの追加
* バグ修正と一般的な改善

## <a name="related-topics"></a>関連トピック

- [SEMM による Surface デバイスの登録と構成](enroll-and-configure-surface-devices-with-semm.md)
- [SEMM からの Surface デバイスの登録解除](unenroll-surface-devices-from-semm.md)
- [SEMM を使用して Surface Dock 2 ポートを保護する](secure-surface-dock-ports-semm.md)
