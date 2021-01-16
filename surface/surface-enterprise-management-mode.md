---
title: Surface Enterprise 管理モード (Surface)
description: Surface UEFI を使った Surface デバイスのこの機能によって、組織内のファームウェア設定をセキュリティで保護および管理する方法について説明します。
keywords: uefi, 構成, ファームウェア, セキュア, semm
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
ms.date: 01/15/2021
ms.openlocfilehash: e6f81639253c646f5d3956243a80f4d61c91028a
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271421"
---
# Microsoft Surface Enterprise 管理モード

Microsoft Surface Enterprise Management Mode (SEMM) は、Surface UEFI を備える Surface デバイスの機能で、組織内のファームウェア設定をセキュリティで保護および管理できます。 SEMM を使用すると、IT 担当者は UEFI 設定の構成を準備し、Surface デバイスにインストールできます。 SEMM では、UEFI 設定を構成する機能に加えて、証明書を使用して、不正な改ざんや削除から構成を保護します。 SEMM は、Surface Hub 2S を Windows 10 Pro および Enterprise に移行できる要件です。

>[!NOTE]
>SEMM は、Surface UEFI ファームウェアを持つデバイスでのみ使用できます。 これは、Intel プロセッサを搭載した Surface Pro 7+、Surface Pro X、Surface Hub 2S、Surface Laptop 3 の商用 SKU、Surface Laptop Go など、他のほとんどの Surface デバイスで構成されます。 SEMM は、AMD プロセッサを搭載した 15" Surface Laptop 3 SKU ではサポートされていません (製品 SKU としてのみ利用可能)。 

Surface デバイスは SEMM によって構成され、SEMM 証明書で保護されている場合、SEMM *に登録されたと* 見なされます。 SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM で登録解除されたと見なされます。 **

SEMM の管理と Surface デバイスの登録に使用できる管理オプションには、スタンドアロン ツールと Microsoft Endpoint Configuration Manager との統合の 2 つがあります。 この記事では、SEMM スタンドアロン ツール (Microsoft Surface UEFI Configurator と呼ばれる) について説明します。 Microsoft Endpoint Configuration Manager で SEMM を管理する方法の詳細については [、「Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)を使用して SEMM を使用してデバイスを管理する」を参照してください。


## Microsoft Surface UEFI コンフィエーター

図 1 に示すように、SEMM のプライマリ ワークスペースは Microsoft Surface UEFI コンフィエーターです。 Microsoft Surface UEFI コンフィグレータは、Surface デバイスでの SEMM の登録、構成、および登録解除に使用される Windows インストーラー (.msi) パッケージまたは WinPE イメージを作成するために使用されるツールです。 これらのパッケージには、UEFI の設定が指定された構成ファイルが含まれています。 SEMM パッケージには、ファームウェアにインストールおよび保存され、UEFI 設定を適用する前に構成ファイルの署名を確認するために使用される証明書も含まれています。

>[!NOTE]
>Surface UEFI コンフィエーターと SEMM を使用して、Surface ドック 2 のポートを管理できます。 詳細については [、「SEMM によるセキュア Surface Dock 2 ポート」を参照してください](secure-surface-dock-ports-semm.md)。

![Microsoft Surface UEFI コンフィエーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*図 1.  Microsoft Surface UEFI コンフィエーター*


Microsoft Surface UEFI コンフィエーター ツールは、次の 3 つのモードで使用できます。

* [Surface UEFI 構成パッケージ](#configuration-package)。 このモードを使って Surface UEFI 構成パッケージを作成し、SURFACE デバイスを SEMM に登録し、登録済みデバイスで UEFI 設定を構成します。
* [Surface UEFI リセット パッケージ](#reset-package)。 SEMM から Surface デバイスを登録解除するには、このモードを使用します。
* [Surface UEFI 回復要求](#recovery-request)。 このモードを使用して、パッケージのリセット操作が失敗した SEMM から Surface デバイスを登録解除する回復要求に応答します。


#### Microsoft Surface UEFI コンフィエーターのダウンロード

Microsoft Surface UEFI コンフィエーターは [、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703) ダウンロード センターの Surface Tools for IT ページからダウンロードできます。

### 構成パッケージ

Surface UEFI 構成パッケージは、Surface デバイスに SEMM を実装および管理するための主要なメカニズムです。 これらのパッケージには、図 2 に示すように、Microsoft Surface UEFI Configurator でのパッケージの作成時に指定された UEFI 設定の構成ファイルと証明書ファイルが含まれています。 SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアに証明書ファイルがプロビジョニングされ、デバイスが SEMM に登録されます。 SEMM にデバイスを登録するときに、証明書ファイルを保存して登録を完了する前に、SEMM 証明書の拇印の最後の 2 桁を指定して操作の確認を求めるメッセージが表示されます。 この確認では、登録時にユーザーがデバイスに物理的に存在し、確認を実行する必要があります。

![証明書を使用して SEMM 構成パッケージをセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*図 2.  証明書を使用して SEMM 構成パッケージをセキュリティで保護する*

SEMM [証明書の要件の詳細については](#surface-enterprise-management-mode-certificate-requirements) 、この記事の「Surface Enterprise 管理モード証明書の要件」セクションを参照してください。

>[!NOTE]
>SURFACE UEFI の [セキュリティ]、[デバイス]、[ブート構成]、または****[エンタープライズ管理****] ページを表示するために必要な SEMM で UEFI パスワードを指定することもできます。 **** ****

デバイスを SEMM に登録すると、構成ファイルが読み取り、ファイルで指定された設定が UEFI に適用されます。 SEMM に既に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名が、デバイスのファームウェアに格納されている証明書と対してチェックされます。 署名が一致しない場合、変更はデバイスに適用されません。

### SEMM による Surface UEFI のデバイスの有効化または無効化

以下に、SEMM で管理できるすべての利用可能なデバイスを示します。

* USB ポートのドッキング
* オンボード オーディオ
* DGPU
* タイプ カバー
* Micro SD カード
* 前面カメラ
* 背面カメラ
* Windows Hello 用の赤外線カメラ
* Bluetoothのみ
* Wi-Fi と Bluetooth
*              LTE           

 >[!NOTE]
>[UEFI デバイス] ページに表示される組み込みデバイスは、デバイスまたは企業の環境によって異なる場合があります。 たとえば、UEFI デバイス ページは Surface Pro X ではサポートされていません。LTE は LTE 搭載デバイスでのみ表示されます。 
### SEMM を使用して詳細設定を構成する
**表 1. 詳細設定**

| 設定                            | 説明                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PXE ブート用 IPv6                  | PXE ブートの IPv6 サポートを管理できます。 この設定を構成しない場合、PXE ブートの IPv6 サポートは無効になります。                                                                               |
| 代替ブート                     | ブート中にボリューム ダウン ボタンと電源ボタンの両方を押すことで、代替ブート順序の使用を管理して USB デバイスまたはイーサネット デバイスで直接起動できます。 この設定を構成しない場合は、代替ブートが有効になります。 |
| ブート順序ロック                    | 変更を防ぐためにブート順序をロックできます。 この設定を構成しない場合、ブート 順序ロックは無効になります。                                                                                                        |
| USB ブート                           | USB デバイスの起動を管理できます。 この設定を構成しない場合は、USB ブートが有効になります。                                                                                                                 |
| ネットワーク スタック                      | ネットワーク スタックのブート設定を管理できます。 この設定を構成しない場合、ネットワーク スタックのブート設定を管理する機能は無効になります。                                                                                                           |
| 自動電源オン                      | 自動電源オンのブート設定を管理できます。 この設定を構成しない場合は、自動電源が有効になります。                                                                                                        |
| 同時マルチスレッド (SMT) | 同時マルチスレッド (SMT) を管理して、ハイパースレッジを有効または無効にできます。 この設定を構成しない場合は、SMT が有効になります。                                                  |
|バッテリ制限を有効にする| バッテリー制限機能を管理できます。 この設定を構成しない場合、バッテリ制限が有効になります。 |
| セキュリティ                           | Surface UEFI セキュリティ ページ **を表示** します。 この設定を構成しない場合は、[セキュリティ] ページが表示されます。                                                                                                                 |
| デバイス                            | [Surface UEFI デバイス] ページ **を表示** します。 この設定を構成しない場合は、[デバイス] ページが表示されます。                                                                                                                     |
| Boot                               | Surface UEFI ブート ページ **を表示** します。 この設定を構成しない場合は、ブート ページが表示されます。                                                                                                                                                            |
| DateTime                           | Surface UEFI **の DateTime ページを表示** します。 この設定を構成しない場合は、[DateTime] ページが表示されます。                                                                                                                |
| EnableOSMigration                          | Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できます。 この設定を構成しない場合、Surface Hub 2 デバイスで実行できるのは Windows 10 Team OS のみです。   注: Windows 10 Team と Windows 10 Pro/Enterprise の間のデュアル ブートは、Surface Hub 2 では使用できません。                                                                                                           |


>[!NOTE]
>図 3 に示すように、SEMM 構成パッケージを**** 作成すると、[成功] ページに 2 文字が表示されます。

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*図 3.  [成功] ページでの証明書の拇印の最後の 2 文字の表示*

これらの文字は証明書の拇印の最後の 2 文字であり、書き込むか記録する必要があります。 図 4 に示すように、文字は Surface デバイスの SEMM への登録を確認するために必要です。

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*図 4:  SEMM 証明書の拇印を使用した SEMM での登録確認*

>[!NOTE]
>証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開いて、いつでも拇印を読み取る可能性があります。 CertMgr で拇印を表示するには、次のプロセスに従います。
>1. .pfx ファイルを右クリックし、[開く] をクリック **します**。
>2. ナビゲーション ウィンドウでフォルダーを展開します。
>3. **[証明書]** をクリックします。
>4. メイン ウィンドウで証明書を右クリックし、[開く] をクリック **します**。
>5. [詳細] **タブをクリック** します。
>6. **[** 表示 **] ドロップダウン メニュー** で [すべて] または [プロパティ **のみ]** を選択する必要があります。
>7. フィールド **Thumbprint を選択します**。

SEMM に Surface デバイスを登録したり、構成パッケージから UEFI 構成を適用したりするには、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行する必要があります。 アプリケーション展開または Microsoft [Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) や Microsoft Deployment Toolkit などのオペレーティング システム展開テクノロジ [を使用できます](https://technet.microsoft.com/windows/dn475741)。 SEMM にデバイスを登録する場合は、デバイスへの登録を確認するために物理的に存在する必要があります。 SEMM に既に登録されているデバイスに構成を適用する場合、ユーザーの操作は必要ありません。

SEMM で Surface デバイスを登録する方法、または SEMM で Surface UEFI 構成を適用する方法の詳しいチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)を使用して Surface デバイスを登録および構成する」を参照してください。

### パッケージをリセットする

Surface UEFI リセット パッケージは、SEMM から Surface デバイスを登録解除するために、1 つのタスクのみを実行するために使用されます。 リセット パッケージには、デバイスのファームウェアから SEMM 証明書を削除し、UEFI 設定を出荷時の既定値にリセットする署名済み手順が含まれています。 Surface UEFI 構成パッケージと同様に、リセット パッケージは、Surface デバイスでプロビジョニングされたのと同じ SEMM 証明書で署名する必要があります。 SEMM リセット パッケージを作成する場合は、リセットする Surface デバイスのシリアル番号を指定する必要があります。 SEMM リセット パッケージはユニバーサルではなく、1 つのデバイスに固有です。

### 回復要求

シナリオによっては、Surface UEFI リセット パッケージを使えない場合があります。 (たとえば、Surface デバイスで Windows が使用できなくなる場合など)。これらのシナリオでは、回復要求操作を使用して、Surface UEFI**** の [エンタープライズ管理] ページ (図 5 を参照) を介して SEMM から Surface デバイスを登録解除できます。

![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*図 5:  [エンタープライズ管理] ページで SEMM 回復要求を開始する*

[エンタープライズ管理] ページの**** プロセスを使用して Surface デバイスで SEMM をリセットすると、リセット要求が表示されます。 このリセット要求は、ファイルとして USB ドライブに保存したり、テキストとしてコピーしたり、モバイル デバイスで QR コードとして読み取って、簡単にメールやメッセージを送信することができます。 Microsoft Surface UEFI コンフィエーターのリセット要求オプションを使用して、リセット要求ファイルを読み込むか、要求のリセット テキストまたは QR コードを入力します。 Microsoft Surface UEFI Configurator は、Surface デバイスで入力できる検証コードを生成します。 Surface デバイスでコードを入力して **[Restart]** をクリックすると、デバイスは SEMM から登録解除されます。 

>[!NOTE]
>リセット要求は、作成後 2 時間で期限切れになります。

SEMM から Surface デバイスを登録解除する方法の詳しいチュートリアルについては [、「SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)から Surface デバイスを登録解除する」を参照してください。

## Surface Enterprise 管理モードの証明書の要件
SEMM を Microsoft Surface UEFI コンフィグレータと一緒に使用するには、UEFI 設定を適用する前に、構成ファイルの署名を検証する証明書が必要です。 この証明書を使用すると、デバイスを SEMM に登録した後で、UEFI の設定を変更するために、承認された証明書で作成されたパッケージのみを使用できます。

>[!NOTE]
>SEMM 証明書は、登録済み Surface デバイスで SEMM または Surface UEFI の設定に対する変更を実行するために必要です。 SEMM 証明書が破損または失われた場合、SEMM を削除またはリセットすることはできません。 バックアップと復元に適したソリューションを使用して、SEMM 証明書を適切に管理します。

Microsoft Surface UEFI Configurator ツールで作成されたパッケージは、証明書で署名されます。 この証明書を使用すると、デバイスを SEMM に登録した後で、UEFI の設定を変更するために、承認された証明書で作成されたパッケージのみを使用できます。 
### 推奨される証明書の設定
SEMM 証明書には次の設定が推奨されます。

* **キー アルゴリズム** – RSA 
* **キーの長** さ - 2048
* **ハッシュ アルゴリズム** – SHA-256
* **種類** – SSL サーバー認証
* **キー使用法** – デジタル署名、キー暗号化
* **プロバイダー** – Microsoft Enhanced RSA and AES Cryptographic Provider
* **有効期限 –** 証明書の作成から 15 か月
* **キーのエクスポート ポリシー** - エクスポート可能

また、中間証明機関 (CA) が SEMM 専用である 2 層公開キー基盤 (PKI) アーキテクチャで SEMM 証明書を認証し、証明書の失効を可能にしてください。 2 層 PKI 構成の詳細については、「テスト ラボ ガイド: AD CS および PKI 階層Two-Tier [参照してください](https://technet.microsoft.com/library/hh831348)。

### 自己署名証明書 
次の PowerShell スクリプトの例を使用して、概念実証シナリオで使用する自己署名証明書を作成できます。
このスクリプトを使用するには、次のテキストをメモ帳にコピーし、PowerShell スクリプト (.ps1) としてファイルを保存します。 

> [!NOTE]
> このスクリプトは、次のパスワードを持つ証明書を作成します `12345678` 。このスクリプトによって生成される証明書は、実稼働環境では推奨されません。
  
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
>SEMM および Microsoft Surface UEFI コンフィエーターで使用するには、証明書をプライベート キーとパスワード保護を使用してエクスポートする必要があります。 必要に応じて、SemM 証明書ファイル (.pfx) と証明書パスワードを選択するように求めるメッセージが表示されます。

1.  スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM などです。
2.  サンプル スクリプトをメモ帳または同等のテキスト エディターにコピーし、PowerShell スクリプト (.ps1) としてファイルを保存します。
3.  管理者の資格情報で PC にサインインし、管理者特権の PowerShell セッションを開きます。
4.  スクリプトの実行を許可するアクセス許可が設定されている必要があります。 既定では、実行ポリシーを変更しない限り、スクリプトの実行はブロックされます。 詳細については、「実行ポリシー [について」を参照してください](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。
5.  コマンド プロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。 このスクリプトは、TempOwner.pfx という名前のデモ証明書を作成します。

または、PowerShell を使用して独自の自己署名証明書を作成できます。 詳細については、PowerShell のドキュメント [New-SelfSignedCertificate を参照してください](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。




>[!NOTE]
>PKI インフラストラクチャでオフライン ルートを使用する組織の場合、SEMM 証明書を認証するには、ルート CA に接続された環境で Microsoft Surface UEFI コンフィフィケーターを実行する必要があります。 Microsoft Surface UEFI Configurator によって生成されたパッケージはファイルとして転送されるため、USB スティックなどのリムーバブル記憶域を使用してオフライン ネットワーク環境の外部に転送できます。

### 証明書の管理に関する FAQ

推奨される *最小の* 長さは 15 か月です。 有効期限が 15 か月未満の証明書を使用するか、15 か月より長く有効期限が切れた証明書を使用できます。

>[!NOTE] 
>証明書の有効期限が切れると、証明書は自動的に更新されません。 


**有効期限が切れた証明書は SEMM に登録されたデバイスの機能に影響しますか?**<br><br>
いいえ。証明書は SEMM の IT 管理者管理タスクにのみ影響し、有効期限が切れるとデバイスの機能には影響しません。


**SEMM パッケージと証明書があるすべてのコンピューターで SEMM パッケージと証明書を更新する必要がありますか?**

SEMM のリセットまたは回復を機能するには、証明書が有効であり、有効期限が切れていない必要があります。 

**注文するサーフェスごとにパッケージを一括リセットできますか? 環境内のすべてのコンピューターをリセットするビルドは可能ですか?**

特定のデバイスの種類の構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセット パッケージを作成することもできます。 証明書がまだ有効な場合は、PowerShell を使用して SEMM をリセットするリセット パッケージを作成できます。

## バージョン履歴

### バージョン 2.79.139.0

このバージョンの SEMM には以下が含まれます。
- Surface Pro 7+ のサポート
- ユーザー エクスペリエンスの向上


### バージョン 2.78.139.0

このバージョンの SEMM には以下が含まれます。

- Surface Laptop Go と Surface Pro X のサポート
- 新しいバージョン リリースの通知
- 所有権を変更するカスタム パッケージを作成する機能
- バグ修正

### バージョン 2.73.136.0

このバージョンの SEMM には以下が含まれます。

- SEMM を使用して Surface Hub2S でオーディオを無効にできる
- Surface Pro X for Dock 2 のサポート
- ドック 2 関連操作の UEFI マネージャーのサポート
- Surface Go リセット パッケージのバグ修正
- Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行のサポート。

### バージョン 2.71.139.0

このバージョンの SEMM では、Surface Book 3、Surface Laptop 3、Surface Pro 7 の Surface ドック 2 管理機能のサポートが追加されています。

- オーディオの有効化 (ロック/ロック解除)、イーサネット ポートと USB ポート
- 認証されたホストと認証されていないホストの両方のドック パッケージを作成する機能

### バージョン 2.70.130.0

このバージョンの SEMM には以下が含まれます。

- Surface Go 2 のサポート
- Surface Book 3 のサポート
- バグ修正


### バージョン 2.59.139.0

* Intel プロセッサを搭載した Surface Pro 7、Surface Pro X、Surface Laptop 3 13.5" および 15" モデルのサポート。 注: Surface Laptop 3 15" AMD プロセッサはサポートされていません。

- 電源でのスリープ解除機能のサポート

### バージョン 2.54.139.0
* Surface Hub 2S のサポート
* バグ修正

### バージョン 2.43.136.0
* マルチマルチサーティングの有効化/無効化のサポート 
* 一部のデバイスでは、WiFi とBluetoothオプションを個別に使用できます。 
* Surface Studio のバッテリー制限の削除 

### バージョン 2.26.136.0
* Surface Studio 2 へのサポートの追加
* バッテリー制限機能

### バージョン 2.21.136.0
* Surface Pro 6 へのサポートの追加
* Surface Laptop 2 へのサポートの追加

### バージョン 2.14.136.0
* Surface Go へのサポートの追加

### バージョン 2.9.136.0
* Surface Book 2 へのサポートの追加
* Surface Pro LTE へのサポートの追加
* アクセシビリティの強化

### バージョン 1.0.74.0
* Surface Laptop へのサポートの追加
* Surface Pro へのサポートの追加
* バグ修正と一般的な改善

## 関連トピック

- [SEMM による Surface デバイスの登録と構成](enroll-and-configure-surface-devices-with-semm.md)
- [SEMM からの Surface デバイスの登録解除](unenroll-surface-devices-from-semm.md)
- [SEMM を使用して Surface Dock 2 ポートを保護する](secure-surface-dock-ports-semm.md)
