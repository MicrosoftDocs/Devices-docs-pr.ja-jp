---
title: Surface Enterprise 管理モード (Surface)
description: Surface UEFI を使用した Surface デバイスのこの機能を使って、組織内のファームウェア設定をセキュリティで保護し、管理する方法について説明します。
keywords: uefi、構成、ファームウェア、secure、semm
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
ms.date: 09/01/2020
ms.openlocfilehash: 239b5e4659ff48e6c0fd9d2fca03341eadb9a27d
ms.sourcegitcommit: 78694f3958117a339a28d3a5854908181f1b65d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "10993667"
---
# Microsoft Surface Enterprise 管理モード

Microsoft Surface Enterprise Management Mode (SEMM) は、組織内のファームウェア設定をセキュリティで保護し、管理できる surface UEFI を備えた Surface デバイスの機能です。 SEMM では、IT プロフェッショナルが UEFI 設定の構成を準備し、それを Surface デバイスにインストールすることができます。 UEFI 設定を構成する機能に加えて、SEMM は証明書を使用して、許可されていない改ざんまたは削除から構成を保護します。 SEMM は、Surface Hub の2S を Windows 10 Pro と Enterprise に移行できるようにするための要件です。

>[!NOTE]
>SEMM は、Surface UEFI ファームウェアを搭載したデバイスでのみ利用できます。 これは、Surface Pro 7、Surface Pro X、Surface Hub 2S、Surface Pc 3 の市販 Sku など、Intel プロセッサを搭載した、他の多くの Surface デバイスで構成されています。 SEMM は、(小売 SKU としてのみ利用可能) AMD プロセッサを搭載した15インチ Surface ノートパソコン 3 SKU ではサポートされていません。 

Surface デバイスが SEMM によって構成され、SEMM 証明書によって保護されている場合は、SEMM に *登録* されていると見なされます。 SEMM 証明書が削除され、UEFI 設定の制御がデバイスのユーザーに返されると、Surface デバイスは SEMM に *登録* されていないと見なされます。

SEMM および登録 Surface デバイスを管理するために使用できる管理オプションは2つあります。スタンドアロンツールとして、または Microsoft Endpoint Configuration Manager との統合です。 この記事では、Microsoft Surface UEFI コンフィギュレーターと呼ばれる SEMM 単体ツールについて説明します。 Microsoft Endpoint Configuration Manager を使用して SEMM を管理する方法の詳細については、「 [Microsoft Endpoint Configuration manager を使用して semm でデバイスを管理](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm)する」を参照してください。


## Microsoft Surface UEFI コンフィギュレーター

SEMM のプライマリワークスペースは、図1のように Microsoft Surface UEFI コンフィギュレーターです。 Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスで SEMM を登録、構成、登録解除するために使用される Windows Installer (.msi) パッケージまたは WinPE イメージを作成するために使用されるツールです。 これらのパッケージには、UEFI の設定が指定されている構成ファイルが含まれています。 SEMM パッケージには証明書も含まれています。これは、インストールされ、ファームウェアに保存され、UEFI 設定が適用される前に構成ファイルの署名を確認するために使用されます。

>[!NOTE]
>Surface UEFI コンフィギュレーターと SEMM を使って Surface Dock 2 上のポートを管理できるようになりました。 詳細については、「 [SEMM での Secure Surface Dock 2 ポート](secure-surface-dock-ports-semm.md)」を参照してください。

![Microsoft Surface UEFI コンフィギュレーター](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*図 1.  Microsoft Surface UEFI コンフィギュレーター*


Microsoft Surface UEFI コンフィギュレーターツールは、次の3つのモードで使うことができます。

* [SURFACE UEFI 構成パッケージ](#configuration-package)。 Surface UEFI 構成パッケージを作成して SEMM に Surface デバイスを登録し、登録済みデバイスで UEFI 設定を構成するには、このモードを使用します。
* [SURFACE UEFI リセットパッケージ](#reset-package)。 このモードを使って、SEMM から Surface デバイスの登録を解除します。
* [SURFACE UEFI 回復要求](#recovery-request)。 このモードを使って、回復要求に応答して、Reset Package 操作が失敗した場合に、SEMM から Surface デバイスの登録を解除します。


#### Microsoft Surface UEFI コンフィギュレーターをダウンロードする

Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。

### 構成パッケージ

Surface UEFI 構成パッケージは、Surface デバイスで SEMM を実装して管理するための主要なメカニズムです。 これらのパッケージには、図2に示すように、Microsoft Surface UEFI コンフィギュレーターおよび証明書ファイルでパッケージの作成時に指定した UEFI 設定の構成ファイルが含まれています。 まだ SEMM に登録されていない Surface デバイスで構成パッケージを初めて実行すると、デバイスのファームウェアで証明書ファイルがプロビジョニングされ、SEMM にデバイスが登録されます。 SEMM でデバイスを登録すると、証明書ファイルが保存され、登録が完了する前に、SEMM 証明書の拇印の最後の2桁を指定して、操作を確認するように求められます。 この確認を行うには、登録時にユーザーがデバイスに物理的に存在していることを確認する必要があります。

![SEMM 構成パッケージと証明書をセキュリティで保護する](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*図 2.  SEMM 構成パッケージと証明書をセキュリティで保護する*

SEMM 証明書の要件の詳細については、この記事の「 [Surface Enterprise 管理モード証明書の要件](#surface-enterprise-management-mode-certificate-requirements) 」を参照してください。

>[!NOTE]
>Surface UEFI の **セキュリティ**、 **デバイス**、 **ブート構成**、または **エンタープライズ管理** ページを表示するために必要となる、semm を使って uefi パスワードを指定することもできます。

デバイスが SEMM に登録されると、構成ファイルが読み込まれ、ファイルで指定された設定が UEFI に適用されます。 既に SEMM に登録されているデバイスで構成パッケージを実行すると、構成ファイルの署名が、デバイスファームウェアに保存されている証明書に照らしてチェックされます。 署名が一致しない場合、デバイスに変更は適用されません。

### SEMM で Surface UEFI のデバイスを有効または無効にする

次のリストは、SEMM で管理可能なすべてのデバイスを示しています。

* ドッキング USB ポート
* ボードオーディオ
* DGPU
* タイプ カバー
* マイクロ SD カード
* 前面カメラ
* 背面カメラ
* Windows Hello の赤外線カメラ
* Bluetooth のみ
* Wi-Fi と Bluetooth
*              LTE           

 >[!NOTE]
>[UEFI デバイス] ページに表示される組み込みデバイスは、お使いのデバイスまたは企業環境によって異なる場合があります。 たとえば、[UEFI デバイス] ページは Surface Pro X ではサポートされていません。LTE が装備されているデバイスにのみ表示されます。 
### SEMM で詳細設定を構成する
**表 1. 詳細設定**

| 設定                            | 説明                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PXE ブート用 IPv6                  | PXE ブートの IPv6 サポートを管理できるようにします。 この設定を構成しない場合は、IPv6 の PXE ブートのサポートは無効になります。                                                                               |
| 代替ブート                     | 起動時に音量を下げるボタンと電源ボタンの両方を押して、USB またはイーサネットデバイスを直接起動することで、代替のブート順序の使用を管理できます。 この設定を構成しない場合は、代替ブートが有効になります。 |
| ブート順序ロック                    | 変更を防止するために、ブート順序をロックすることができます。 この設定を構成しないと、起動順序のロックが無効になります。                                                                                                        |
| USB ブート                           | USB デバイスの起動を管理できます。 この設定を構成しない場合は、USB のブートが有効になります。                                                                                                                 |
| ネットワークスタック                      | ネットワークスタックのブート設定を管理できます。 この設定を構成しない場合、ネットワークスタックのブート設定を管理する機能は無効になります。                                                                                                           |
| 自動電源オン                      | 自動電源オンのブート設定を管理できます。 この設定を構成しない場合、自動電源オンが有効になります。                                                                                                        |
| 同時マルチスレッド (SMT) | ハイパースレッディングを有効または無効にするために、同時マルチスレッド (SMT) を管理できます。 この設定を構成しない場合、SMT は有効になります。                                                  |
|バッテリー制限を有効にする| バッテリー制限機能を管理できます。 この設定を構成しない場合は、バッテリー制限が有効になっています |
| セキュリティ                           | Surface UEFI **セキュリティ** ページを表示します。 この設定を構成しない場合、[セキュリティ] ページが表示されます。                                                                                                                 |
| デバイス                            | Surface UEFI **デバイス** ページを表示します。 この設定を構成しないと、[デバイス] ページが表示されます。                                                                                                                     |
| Boot                               | Surface UEFI **ブート** ページを表示します。 この設定を構成しない場合、[ブート] ページが表示されます。                                                                                                                                                            |
| DateTime                           | Surface UEFI の [ **DateTime** ] ページを表示します。 この設定を構成しない場合、[DateTime] ページが表示されます。                                                                                                                |
| EnableOSMigration                          | Surface Hub 2 を Windows 10 Team から Windows 10 Pro または Enterprise に移行できるようにします。 この設定を構成しない場合、Surface Hub 2 のデバイスでは、Windows 10 Team OS のみを実行できます。   注: Windows 10 Team と Windows 10 Pro/Enterprise の間のデュアルブートは Surface Hub 2 では利用できません。                                                                                                           |


>[!NOTE]
>SEMM 構成パッケージを作成すると、図3に示すように、 **成功** したページに2つの文字が表示されます。

![証明書の拇印の表示](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*図 3.  成功したページの証明書の拇印の最後の2文字を表示する*

これらの文字は、証明書の拇印の最後の2文字であり、書き留めたり記録したりする必要があります。 図4に示すように、Surface デバイス上の SEMM での登録を確認するために文字が必要です。

![SEMM での登録確認](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*図 4:  Semm 証明書拇印での SEMM の登録確認*

>[!NOTE]
>証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開くと、いつでも拇印を読むことができます。 CertMgr で拇印を表示するには、次の手順を実行します。
>1. .Pfx ファイルを右クリックし、[ **開く**] をクリックします。
>2. ナビゲーションウィンドウでフォルダーを展開します。
>3. **[証明書]** をクリックします。
>4. メインウィンドウで証明書を右クリックし、[ **開く**] をクリックします。
>5. [ **詳細** ] タブをクリックします。
>6. [表示] ドロップダウンメニューで [**すべて**] または [**プロパティ** **]** を選択する必要があります。
>7. フィールドの **拇印**を選択します。

SEMM で Surface デバイスを登録したり、構成パッケージから UEFI 構成を適用したりするには、必要な操作は、目的の Surface デバイスで管理者権限を持つ .msi ファイルを実行することだけです。 [Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023)や[Microsoft 展開ツールキット](https://technet.microsoft.com/windows/dn475741)などの、アプリケーションの展開やオペレーティングシステムの展開テクノロジを使用できます。 SEMM でデバイスを登録する場合、デバイスでの登録を確認するために物理的に存在する必要があります。 既に SEMM に登録されているデバイスに構成を適用する場合は、ユーザーの操作は必要ありません。

Semm で Surface デバイスを登録する方法、または SEMM を使って surface UEFI 構成を適用する方法の詳しい手順については、「 [semm を使って surface デバイスを登録して構成](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm)する」を参照してください。

### パッケージのリセット

Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除するために、1つのタスクを実行するために使用されます。 リセットパッケージには、デバイスのファームウェアから SEMM 証明書を削除する、または UEFI 設定を出荷時の既定にリセットするための、署名された手順が含まれています。 Surface UEFI 構成パッケージと同様に、リセットパッケージは Surface デバイスでプロビジョニングされた同じ SEMM 証明書で署名する必要があります。 SEMM reset パッケージを作成するときは、リセットする Surface デバイスのシリアル番号を指定する必要があります。 SEMM リセットパッケージはユニバーサルではなく、1つのデバイスに固有のものです。

### 回復要求

一部のシナリオでは、Surface UEFI リセットパッケージを使用できない場合があります。 (たとえば、Surface デバイスで Windows が使用できなくなった場合など)。このようなシナリオでは、回復要求操作によって、surface デバイスの (図5に表示されている) Surface UEFI の [ **エンタープライズ管理** ] ページを、semm から登録解除できます。

![SEMM 回復要求を開始する](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*図 5:  [エンタープライズ管理] ページで SEMM 回復要求を開始する*

[ **エンタープライズ管理** ] ページのプロセスを使用して Surface デバイス上の semm をリセットすると、リセット要求が提供されます。 このリセット要求は、ファイルとして USB ドライブに保存するか、テキストとしてコピーするか、モバイルデバイスを使用して簡単にメールや送信先を送信する QR コードとして読み取ることができます。 Microsoft Surface UEFI Configurator のリセット要求オプションを使用して、リセット要求ファイルを読み込むか、リセット要求のテキストまたは QR コードを入力します。 Microsoft Surface UEFI コンフィギュレーターは、Surface デバイスに入力できる確認コードを生成します。 Surface デバイスにコードを入力し、[ **再起動**] をクリックすると、デバイスは semm からアン登録されます。 

>[!NOTE]
>再設定要求は、作成後2時間後に期限切れになります。

SEMM から Surface デバイスの登録を解除する方法についての詳しいチュートリアルについては、「 [SEMM からのサーデバイスの](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm)登録解除」をご覧ください。

## Surface Enterprise 管理モードの証明書の要件
Microsoft Surface UEFI コンフィギュレーターで SEMM を使用するには、UEFI 設定を適用する前に、証明書を使って構成ファイルの署名を確認する必要があります。 この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI の設定を変更できることを保証します。

>[!NOTE]
>Semm 証明書は、登録されている Surface デバイスで SEMM または Surface UEFI の設定を変更する場合に必要です。 SEMM 証明書が破損または紛失した場合、SEMM は削除またはリセットできません。 必要に応じて、バックアップと復元に適したソリューションを使用して、SEMM 証明書を管理します。

Microsoft Surface UEFI コンフィギュレーターツールで作成されたパッケージは、証明書で署名されます。 この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI の設定を変更できることを保証します。 
### 推奨される証明書の設定
SEMM 証明書には、次の設定が推奨されます。

* **キーアルゴリズム** – RSA 
* **キーの長さ** –2048
* **ハッシュアルゴリズム** – SHA-256
* **種類** – SSL サーバー認証
* **キー使用法** –デジタル署名、キーの暗号化
* **プロバイダー** – Microsoft エンハンス RSA および AES 暗号化プロバイダー
* **有効期限** : 証明書の作成から15ヶ月
* **キーエクスポートポリシー** –エクスポート可能

また、SEMM 証明書は、中間証明機関 (CA) が SEMM 専用であり、証明書の失効を有効にする2階層の公開キー基盤 (PKI) アーキテクチャで認証することをお勧めします。 2階層の PKI 構成の詳細については、「 [テストラボガイド: AD CS 2 階層の Pki 階層の展開](https://technet.microsoft.com/library/hh831348)」を参照してください。

### 自己署名証明書 
次の PowerShell スクリプト例では、コンセプトのあるシナリオで使用する自己署名証明書を作成する方法についてご紹介します。
このスクリプトを使用するには、次のテキストをメモ帳にコピーして、ファイルを PowerShell スクリプト (. ps1) として保存します。 注: このスクリプトでは、というパスワードの証明書を作成し `12345678` ます。このスクリプトによって生成された証明書は、運用環境では推奨されません。
  
   ```
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
>SEMM および Microsoft Surface UEFI コンフィギュレーターで使用するには、証明書を秘密キーでエクスポートし、パスワード保護を使用する必要があります。 Microsoft Surface UEFI コンフィギュレーターは、必要に応じて SEMM 証明書ファイル (.pfx) と証明書のパスワードを選択するように求めるメッセージを表示します。

1.  スクリプトを保存する C: ドライブにフォルダーを作成します。たとえば、C:\SEMM.
2.  このサンプルスクリプトをメモ帳または同等のテキストエディターにコピーして、ファイルを PowerShell スクリプト (ps1) として保存します。
3.  管理者の資格情報を使って PC にサインインし、管理者特権の PowerShell セッションを開きます。
4.  スクリプトの実行を許可するようにアクセス許可が設定されていることを確認します。 既定では、実行ポリシーを変更しない限り、スクリプトは実行されません。 詳細については、「 [実行ポリシーについ](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)て」を参照してください。
5.  コマンドプロンプトで、スクリプトの完全なパスを入力し、Enter キーを押します。 このスクリプトでは、TempOwner というデモ証明書を作成します。

または、PowerShell を使用して、独自の自己署名証明書を作成することもできます。 詳細については、次の PowerShell ドキュメントを参照してください。 [新しい-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate)。




>[!NOTE]
>PKI インフラストラクチャでオフラインルートを使用している組織の場合、Microsoft Surface UEFI コンフィギュレーターは、ルート CA に接続されている環境で SEMM 証明書を認証するために実行する必要があります。 Microsoft Surface UEFI コンフィギュレーターによって生成されたパッケージは、ファイルとして転送することができます。そのため、USB スティックなどのリムーバブル記憶域を使用して、オフラインネットワーク環境以外の場所に移動することができます。

### 証明書の管理に関する FAQ

推奨される *最小* の長さは15か月です。 有効期限が15か月以内の証明書を使用するか、有効期限が15か月を超える証明書を使用することができます。

>[!NOTE] 
>証明書の有効期限が切れた場合は、自動的に更新されません。 


**有効期限が切れた証明書は、SEMM 登録済みデバイスの機能に影響しますか?**<br><br>
いいえ。証明書は、SEMM の IT 管理者の管理タスクにのみ影響し、有効期限が切れたときにデバイスの機能に影響を与えることはありません。


**SEMM パッケージと証明書は、それがインストールされているすべてのコンピューターで更新する必要がありますか?**

SEMM のリセットまたは回復機能が必要な場合は、証明書が有効であり、期限切れになっていないことが必要です。 

**注文した各サーフェスに対してパッケージを一括リセットできますか? 環境内のすべてのマシンをリセットするように構築することはできますか?**

特定のデバイスの種類に対して構成パッケージを作成する PowerShell サンプルを使用して、シリアル番号に依存しないリセットパッケージを作成することもできます。 証明書が有効な場合は、PowerShell を使用して、SEMM をリセットすることでリセットパッケージを作成できます。

## バージョン履歴


### バージョン2.73.136.0

SEMM のこのバージョンには、次のものが含まれます。

- SEMM を使用して、Surface Hub2S でオーディオを無効にできるようになりました
- Dock 2 用 Surface Pro X のサポート
- Dock 2 関連操作のための UEFI Manager のサポート
- Surface Go リセットパッケージのバグ修正
- Windows 10 Team OS から Windows 10 Pro または Enterprise への Surface Hub 2 デバイスの移行をサポートします。

### バージョン2.71.139.0

このバージョンの SEMM は、surface Dock 3、surface Pc 3、Surface Pro 7 の surface Dock 2 の管理機能のサポートを追加します。

- オーディオ (ロック/ロック解除)、イーサネットおよび USB ポートを有効にする
- 認証されたホストと認証されていないホストの両方に対して、dock パッケージを作成する機能

### バージョン2.70.130.0

SEMM のこのバージョンには、次のものが含まれます。

- Surface Go 2 のサポート
- Surface Book 3 のサポート
- バグ修正


### バージョン2.59.139.0

* Surface Pro 7、Surface Pro X、Surface ノート Pc の 3 13.5 "と 15" のモデルを、Intel プロセッサでサポートします。 注: Surface ノート Pc 3 15 "AMD processor はサポートされていません。

- Power on on Power 機能のサポート

### バージョン2.54.139.0
* Surface Hub 2S へのサポート
* バグ修正

### バージョン2.43.136.0
* Simulatenous を有効/無効にするサポート (複数) 
* 一部のデバイスで WiFi と Bluetooth の個別のオプションを使用する 
* Surface Studio のバッテリー制限が削除されました 

### バージョン2.26.136.0
* Surface Studio 2 にサポートを追加する
* バッテリー制限機能

### バージョン2.21.136.0
* Surface Pro 6 にサポートを追加する
* Surface ノート Pc にサポートを追加する2

### バージョン2.14.136.0
* Surface Go にサポートを追加する

### バージョン 2.9.136.0
* Surface Book 2 にサポートを追加する
* Surface Pro LTE にサポートを追加する
* ユーザー補助機能の改善

### バージョン1.0.74.0
* Surface のノート Pc にサポートを追加する
* Surface Pro にサポートを追加する
* バグ修正と全般的な改善

## 関連トピック

- [SEMM による Surface デバイスの登録と構成](enroll-and-configure-surface-devices-with-semm.md)
- [SEMM からの Surface デバイスの登録解除](unenroll-surface-devices-from-semm.md)
- [SEMM を使用して Surface Dock 2 ポートを保護する](secure-surface-dock-ports-semm.md)
