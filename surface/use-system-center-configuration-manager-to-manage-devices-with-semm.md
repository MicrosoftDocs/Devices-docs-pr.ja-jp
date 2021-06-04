---
title: Microsoft Endpoint Configuration Manager を使用して SEMM (Surface) でデバイスを管理する
description: エンドポイント構成マネージャーを使用して、Microsoft Surface Enterprise Management Mode (SEMM) を管理する方法について説明します。
keywords: 登録、更新、スクリプト、設定
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2020
ms.openlocfilehash: 2d31f520d8c4da54f47b2b89b58b43e2cb983f1a
ms.sourcegitcommit: 7f5b97275fe301ef700f9c77954a1054e2e8d046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "11145618"
---
# Microsoft Endpoint Configuration Manager を使用して SEMM によりデバイスを管理する

Surface UEFI デバイスの Microsoft Surface Enterprise Management Mode (SEMM) 機能を使用すると、管理者は Surface UEFI 設定の構成を管理し、セキュリティで保護することができます。 ほとんどの組織では、このプロセスは、Microsoft Surface UEFI コンフィギュレーターツールを使って Windows Installer (.msi) パッケージを作成することによって実現されます。 次に、これらのパッケージを実行するか、クライアントサーフェスデバイスに展開して SEMM でデバイスを登録し、Surface UEFI 設定の構成を更新します。

Microsoft Endpoint Configuration Manager を使用している組織では、Microsoft Surface UEFI Configurator のプロセスを使用して SEMM の展開と管理を行うことができます。 Microsoft Surface UEFI Manager は、SEMM 管理に必要なアセンブリをデバイスで利用できるようにするための軽量インストーラーです。 マネージクライアントで Microsoft Surface UEFI Manager と共にこれらのアセンブリをインストールすることで、SEMM は、アプリケーションとして展開された PowerShell スクリプトを使って構成マネージャーによって管理できます。 このプロセスでは、SEMM 管理は構成マネージャー内で実行されるため、外部の Microsoft Surface UEFI コンフィギュレーターツールの必要性がなくなります。

> [!Note]
> この記事で説明されているプロセスは、以前のバージョンのエンドポイント構成マネージャー、または他のサードパーティの管理ソリューションでも動作する可能性がありますが、Microsoft Surface UEFI Manager と PowerShell を使用した SEMM の管理は、エンドポイント構成マネージャーの現在の分岐でのみサポートされます。

####  <a name="prerequisites"></a>前提条件

この記事で説明されている手順を開始する前に、次のテクノロジとツールについて理解しておく必要があります。

* [Surface UEFI](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)
* [Surface エンタープライズ管理モード (SEMM)](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)
* [PowerShell スクリプト](https://technet.microsoft.com/scriptcenter/dd742419)
* [System Center Configuration Manager アプリケーションの展開](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)
* 証明書の管理

> [!Note]
> また、SEMM の安全を確保するために使用する証明書へのアクセス権も必要になります。 この証明書の要件の詳細については、「 [Surface Enterprise 管理モードの証明書の要件](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)」を参照してください。
> 
> この証明書は安全な場所に保管し、適切にバックアップすることが非常に重要です。 この証明書が失われたか、使用できなくなった場合は、Surface UEFI のリセット、マネージ Surface UEFI 設定の変更、または登録サーフェスデバイスからの SEMM の削除を行うことはできません。

#### Microsoft Surface UEFI Manager をダウンロードする

構成マネージャーを使用した SEMM の管理では、各クライアントサーフェスデバイスに Microsoft Surface UEFI Manager をインストールする必要があります。 Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) は、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。

#### 構成マネージャー用の SEMM スクリプトのダウンロード

Microsoft Surface UEFI Manager がクライアント Surface デバイスにインストールされた後、SEMM は PowerShell スクリプトを使って展開および管理されます。 [Semm 管理スクリプト](https://www.microsoft.com/download/details.aspx?id=46703)のサンプルは、ダウンロードセンターからダウンロードできます。

## Microsoft Surface UEFI Manager を展開する

Microsoft Surface UEFI Manager の展開は、一般的なアプリケーションの展開です。 Microsoft Surface UEFI マネージャーのインストーラーファイルは、標準の [quiet オプション](https://msdn.microsoft.com/library/windows/desktop/aa367988)と共にインストールできる標準の Windows インストーラーファイルです。

Microsoft Surface UEFI Manager をインストールするコマンドは、次のようになります。

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

Microsoft Surface UEFI Manager をアンインストールするコマンドは、次のようになります。

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

新しいアプリケーションを作成し、それを Surface デバイスを含むコレクションに展開するには、次の手順を実行します。

1. **スタート**画面または [**スタート**] メニューから Configuration Manager コンソールを開きます。
2. ウィンドウの左下隅にある [ **ソフトウェアライブラリ** ] を選びます。
3. ソフトウェアライブラリの [ **アプリケーション管理** ] ノードを展開し、[ **アプリケーション**] を選択します。
4. ウィンドウの上部にある [**ホーム**] タブの [**アプリケーションの作成**] ボタンを選択します。 これにより、アプリケーションの作成ウィザードが開始されます。
5. アプリケーションの作成ウィザードでは、次の一連の手順を実行します。

   * **[全般** ]-[ **インストールファイルに関する情報を自動的に検出** する] オプションが既定で選択されています。 [ **種類** ] フィールドでは、既定で [ **Windows インストーラー (.msi ファイル)** ] も選択されています。 [ **参照** ] を選択して移動し、[ **SurfaceUEFIManagerSetup.msi**] を選択して、[ **次へ**] を選択します。
   
      > [!Note]
      > SurfaceUEFIManagerSetup.msi の場所はネットワーク共有上にあり、他のファイルが含まれていないフォルダー内にある必要があります。 ローカルファイルの場所は使用できません。

   * **情報のインポート** –アプリケーションの作成ウィザードは、.msi ファイルを解析し、 **アプリケーション名** と **製品コード**を読み取ります。 図1のように、SurfaceUEFIManagerSetup.msi は、行の **コンテンツファイル**の下に唯一のファイルとして表示される必要があります。 [ **次へ** ] を選択して続行します。

      ![Surface Manager のセットアップからの情報が自動的に解析される](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *図 1.  Microsoft Surface UEFI Manager のセットアップからの情報が自動的に解析される*

   * **一般的な情報** : アプリケーションの名前や、発行元とバージョンに関する情報の変更、またはこのページへのコメントの追加を行うことができます。 Microsoft Surface UEFI Manager のインストールコマンドが、[インストールプログラム] フィールドに表示されます。 システム用 Install の既定のインストール動作では、ユーザーが Surface デバイスにログオンしていない場合でも、Microsoft Surface UEFI Manager は SEMM に必要なアセンブリをインストールすることができます。 [ **次へ** ] を選択して続行します。
   * **概要** : **情報のインポート** 手順で解析された情報と、 **[一般的な情報** ] 手順で選択した情報が、このページに表示されます。 [ **次へ** ] を選択して、選択内容を確認してアプリケーションを作成します。
   * [**進行状況**]-アプリケーションがインポートされ、ソフトウェアライブラリに追加されると、進行状況バーと状態が表示されます。
   * [**完了**]-アプリケーションの作成プロセスが完了すると、アプリケーションの作成が成功したことが確認されます。 [ **閉じる** ] を選択して、アプリケーションの作成ウィザードを終了します。

Configuration Manager でアプリケーションを作成したら、それを配布ポイントに配布して、Surface デバイスを含むコレクションに展開することができます。 このアプリケーションは Surface デバイス上で SEMM をインストールしたり有効にしたりすることはありません。 これには、PowerShell スクリプトを使用して SEMM を有効にするために必要なアセンブリのみが提供されます。

SEMM で管理されないデバイスに Microsoft Surface UEFI Manager アセンブリをインストールしない場合は、Microsoft Surface UEFI Manager を SEMM Configuration Manager スクリプトの依存関係として構成できます。 このシナリオについては、この記事の後半の「 [SEMM 構成マネージャースクリプトの展開](#deploy-semm-configuration-manager-scripts) 」を参照してください。

## SEMM 構成マネージャーのスクリプトを作成または変更する

必要なアセンブリがデバイスにインストールされた後、SEMM でデバイスを登録して Surface UEFI を構成するプロセスは、PowerShell スクリプトで実行され、Configuration Manager を使用してスクリプトアプリケーションとして展開されます。 これらのスクリプトは、組織と環境のニーズに合わせて変更できます。 たとえば、さまざまな部門またはロールで、管理された Surface デバイスの複数の構成を作成できます。 SEMM および Configuration Manager のスクリプトのサンプルは、この記事の最初の「 [前提条件](#prerequisites) 」セクションのリンクからダウンロードできます。

構成マネージャーを使用して SEMM の展開を実行するには、2つの主要なスクリプトが必要です。

* **ConfigureSEMM.ps1** –このスクリプトを使用して、surface デバイスの構成パッケージを、surface デバイスに適用するために、指定された設定を surface デバイスに適用するため、semm でデバイスを登録するため、semm でデバイスの登録を識別するために使用するレジストリキーを設定するために使います。
* **ResetSEMM.ps1** –このスクリプトを使用して、surface デバイス上の semm をリセットします。これにより、semm から登録解除され、surface UEFI 設定の制御が削除されます。

サンプルスクリプトには、Surface UEFI 設定を設定する方法と、それらの設定へのアクセス許可を制御する方法の例が含まれています。 これらの設定を変更して Surface UEFI をセキュリティで保護し、環境のニーズに応じて Surface UEFI 設定を設定することができます。 この記事の以下のセクションでは、ConfigureSEMM.ps1 スクリプトについて説明し、要件に合わせてスクリプトを作成するために必要な変更について説明します。

> [!NOTE]
> SEMM 構成マネージャーのスクリプトとエクスポートされた SEMM 証明書ファイル (.pfx) は、構成マネージャーに追加される前に、他のファイルを持たない同じフォルダーに配置する必要があります。

### 証明書とパッケージ名を指定する

変更する必要があるスクリプトの最初の領域は、SEMM 証明書を指定して読み込む部分であり、SurfaceUEFIManager のバージョン、および SEMM 構成パッケージと SEMM のリセットパッケージの名前も示しています。 証明書の名前と SurfaceUEFIManager のバージョンは、スクリプト ConfigureSEMM.ps1 の 56 ~ 73 の行に指定されています。

  ```powershell
  56    $WorkingDirPath = split-path -parent $MyInvocation.MyCommand.Definition
  57    $packageRoot = "$WorkingDirPath\Config"
  58    $certName = "FabrikamSEMMSample.pfx"
  59  $DllVersion = "2.26.136.0"
  60
  61  $certNameOnly = [System.IO.Path]::GetFileNameWithoutExtension($certName)
  62  $ProvisioningPackage = $certNameOnly + "ProvisioningPackage.pkg"
  63  $ResetPackage = $certNameOnly + "ResetPackage.pkg"
  64
  65    if (-not (Test-Path $packageRoot))  { New-Item -ItemType Directory -Force -Path $packageRoot }
  66    Copy-Item "$WorkingDirPath\$certName" $packageRoot
  67    
  68    $privateOwnerKey = Join-Path -Path $packageRoot -ChildPath $certName
  69    $ownerPackageName = Join-Path -Path $packageRoot -ChildPath $ProvisioningPackage
  70    $resetPackageName = Join-Path -Path $packageRoot -ChildPath $ResetPackage
  71    
  72    # If your PFX file requires a password then it can be set here, otherwise use a blank string.
  73    $password = "1234" 
  ```

**$CertName**変数の**FabrikamSEMMSample**値を、58行の semm 証明書ファイルの名前に置き換えます。 スクリプトが配置されているフォルダーに (Config という名前の) 作業ディレクトリが作成され、証明書ファイルがこの作業ディレクトリにコピーされます。

また、所有者パッケージとリセットパッケージは、構成ディレクトリ内に作成され、Surface UEFI の設定とスクリプトによって生成されるアクセス許可の構成を保持します。

73の場合は、 **$password** 変数の値を **1234** から証明書ファイルのパスワードに置き換えます。 パスワードが必要ない場合は、 **1234** のテキストを削除します。

> [!Note]
> SEMM でデバイスを登録するには、証明書の拇印の最後の2文字が必要です。 このスクリプトでは、ユーザーにこれらの数字が表示されます。これにより、システムを再起動してからデバイスを SEMM に登録する前に、ユーザーまたは技術者がこれらの数字を記録することができます。 このスクリプトでは、150-155 行にある次のコードを実行します。

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開くと、いつでも拇印を読むことができます。 CertMgr で拇印を表示するには、次の手順を実行します。

1. .Pfx ファイルを右クリックし、[ **開く**] を選択します。
2. ナビゲーションウィンドウでフォルダーを展開します。
3. [ **証明書**] を選択します。
4. メインウィンドウで証明書を右クリックし、[ **開く**] を選択します。
5. [ **詳細** ] タブを選択します。
6. [表示] ドロップダウンメニューで [**すべて**] または [**プロパティ** **]** を選択する必要があります。
7. フィールドの **拇印**を選択します。

> [!NOTE]
> 構成マネージャーがアンインストールアクションを使ってデバイスから SEMM を削除できるようにするには、ResetSEMM.ps1 スクリプトのこのセクションに SEMM 証明書の名前とパスワードも入力する必要があります。

### 権限を構成する

Surface UEFI の構成を指定するスクリプトの最初の領域は、 **"アクセス許可の構成"** 領域です。 この領域は、 **"# Configure アクセス許可"** というコメントを含むサンプルスクリプトの行210から始まり、行247まで続きます。 次のコード例では、最初にすべての Surface UEFI 設定へのアクセス許可を設定します。これにより、これらの設定が SEMM のみで変更される可能性があります。また、ローカルユーザーが Surface UEFI パスワード、TPM、およびフロントカメラとバックカメラを変更できるように、明示的な権限を追加します。

```powershell
210 # Configure Permissions
211 foreach ($uefiV2 IN $surfaceDevices.Values) {
212 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
213 Write-Host "Configuring permissions"
214 Write-Host $Device.Model
215 Write-Host "======================="
216
217 # Here we define which "identities" will be allowed to modify which settings
218 #   PermissionSignerOwner = The primary SEMM enterprise owner identity
219 #   PermissionLocal = The user when booting to the UEFI pre-boot GUI
220 #   PermissionSignerUser, PermissionSignerUser1, PermissionSignerUser2 =
221 #     Additional user identities created so that the signer owner
222 #     can delegate permission control for some settings.
223 $ownerOnly = [Microsoft.Surface.IUefiSetting]::PermissionSignerOwner
224 $ownerAndLocalUser = ([Microsoft.Surface.IUefiSetting]::PermissionSignerOwner -bor [Microsoft.Surface.IUefiSetting]::PermissionLocal)
225 
226 # Make all permissions owner only by default
227 foreach ($setting IN $uefiV2.Settings.Values) {
228 $setting.ConfiguredPermissionFlags = $ownerOnly
229 }
230 
231 # Allow the local user to change their own password
232 $uefiV2.SettingsById[501].ConfiguredPermissionFlags = $ownerAndLocalUser
233
234 Write-Host ""
235  
236 # Create a unique package name based on family and LSV.
237 # We will choose a name that can be parsed by later scripts.
238 $packageName = $uefiV2.SurfaceUefiFamily + "^Permissions^" + $lsv + ".pkg"
239 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
240 
241 # Build and sign the Permission package then save it to a file.
242 $permissionPackageStream =  $uefiV2.BuildAndSignPermissionPackage($privateOwnerKey, $password, "", $null, $lsv)
243 $permissionPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
244 $permissionPackageStream.CopyTo($permissionPackage)
245 $permissionPackage.Close()
246 }
247 }
```

各 **$uefiV 2** 変数は、名前または ID を設定して Surface UEFI 設定を識別し、次のいずれかの値にアクセス許可を構成します。

* **$ownerOnly** –この設定を変更する権限は、semm に対してのみ許可されています。
* **$ownerAndLocalUser** –この設定を変更する権限は、ローカルユーザーが Surface UEFI と semm に対して起動するために許可されています。

Surface UEFI の使用可能な設定名と Id については、この記事の「 [設定名と id](#settings-names-and-ids) 」セクションを参照してください。

### 設定の構成

Surface UEFI の構成を指定するスクリプトの2番目の領域は、各設定を有効または無効にするかどうかを構成する、ConfigureSEMM.ps1 スクリプトの **構成設定** 領域です。 サンプルスクリプトには、すべての設定を既定値に設定する手順が含まれています。 次に、スクリプトは、PXE ブートのために IPv6 を無効にするための明示的な指示を提供し、Surface UEFI 管理者パスワードは変更しないでください。 この領域は、最初に **# Configure 設定** のコメント (291 から行335のサンプルスクリプト) から始まります。 次のような領域が表示されます。

```powershell
291 # Configure Settings
292 foreach ($uefiV2 IN $surfaceDevices.Values) {
293 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
294 Write-Host "Configuring settings"
295 Write-Host $Device.Model
296 Write-Host "===================="
297
298 # In this demo, we will start by setting every setting to the default factory setting.
299 # You may want to start by doing this in your scripts
300 # so that every setting gets set to a known state.
301 foreach ($setting IN $uefiV2.Settings.Values) {
302 $setting.ConfiguredValue = $setting.DefaultValue
303 }
304 
305 $EnabledValue = "Enabled"
306 $DisabledValue = "Disabled"
307
308 # If you want to set something to a different value from the default,
309 # here are examples of how to accomplish this.
310 # This disables IPv6 PXE boot by name:
311 $uefiV2.Settings["IPv6 for PXE Boot"].ConfiguredValue = $DisabledValue
312
313 # This disables IPv6 PXE Boot by ID:
314 $uefiV2.SettingsById[400].ConfiguredValue = $DisabledValue
315
316 Write-Host ""
317
318 # If you want to leave the setting unmodified, set it to $null
319 # PowerShell has issues setting things to $null so ClearConfiguredValue()
320 # is supplied to do this explicitly.
321 # Here is an example of leaving the UEFI administrator password as-is,
322 # even after we initially set it to factory default above.
323 $uefiV2.SettingsById[501].ClearConfiguredValue()
324 
325 # Create a unique package name based on family and LSV.
326 # We will choose a name that can be parsed by later scripts.
327 $packageName = $uefiV2.SurfaceUefiFamily + "^Settings^" + $lsv + ".pkg"
328 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
329 
330 # Build and sign the Settings package then save it to a file.
331 $settingsPackageStream =  $uefiV2.BuildAndSignSecuredSettingsPackage($privateOwnerKey, $password, "", $null, $lsv)
332 $settingsPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
333 $settingsPackageStream.CopyTo($settingsPackage)
334 $settingsPackage.Close()
335 }
```

スクリプトの [ **アクセス許可の構成** ] セクションで設定したアクセス許可と同様に、各 Surface UEFI 設定の構成は、 **$uefiV 2** 変数を定義して実行されます。 **$UefiV 2**変数を定義する各行について、Surface UEFI の設定は名前または ID を設定することによって識別され、構成された値は [**有効**] または [**無効**] に設定されます。

Surface uefi の設定を変更する必要がない場合 (たとえば、surface uefi 管理者のパスワードが、すべての Surface UEFI 設定を既定の状態にリセットする操作によってクリアされないようにする) には、 **ClearConfiguredValue ()** を使って、この設定が変更されないようにすることができます。 このサンプルスクリプトでは、行323でこの値を使って、サンプルスクリプトで **501**の設定 ID によって識別された Surface UEFI 管理者パスワードをクリアしないようにしています。

Surface UEFI の使用可能な設定名と Id の詳細については、この記事の後半の「 [設定名と id](#settings-names-and-ids) 」を参照してください。

### 設定レジストリキー

Configuration Manager の登録済みシステムを特定するために、ConfigureSEMM.ps1 スクリプトは、SEMM 構成スクリプトを使用してインストールされている登録済みシステムを識別するために使用できるレジストリキーを書き込みます。 これらのキーは、次の場所にあります。

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

これらのレジストリキーを作成するには、380-477 行にある次のコード片を使用します。

```powershell
380 # For Endpoint Configuration Manager or other management solutions that wish to know what version is applied, tattoo the LSV and current DateTime (in UTC) to the registry:
381 $UTCDate = (Get-Date).ToUniversalTime().ToString()
382 $certIssuer = $certPrint.Issuer
383 $certSubject = $certPrint.Subject
384 
385 $SurfaceRegKey = "HKLM:\SOFTWARE\Microsoft\Surface\SEMM"
386 New-RegKey $SurfaceRegKey
387 $LSVRegValue = Get-ItemProperty $SurfaceRegKey LSV -ErrorAction SilentlyContinue
388 $DateTimeRegValue = Get-ItemProperty $SurfaceRegKey LastConfiguredUTC -ErrorAction SilentlyContinue
389 $OwnershipSessionIdRegValue = Get-ItemProperty $SurfaceRegKey OwnershipSessionId -ErrorAction SilentlyContinue
390 $PermissionSessionIdRegValue = Get-ItemProperty $SurfaceRegKey PermissionSessionId -ErrorAction SilentlyContinue
391 $SettingsSessionIdRegValue = Get-ItemProperty $SurfaceRegKey SettingsSessionId -ErrorAction SilentlyContinue
392 $IsResetRegValue = Get-ItemProperty $SurfaceRegKey IsReset -ErrorAction SilentlyContinue
393 $certUsedRegValue = Get-ItemProperty $SurfaceRegKey CertName -ErrorAction SilentlyContinue
394 $certIssuerRegValue = Get-ItemProperty $SurfaceRegKey CertIssuer -ErrorAction SilentlyContinue
395 $certSubjectRegValue = Get-ItemProperty $SurfaceRegKey CertSubject -ErrorAction SilentlyContinue
396 
397 
398 If ($LSVRegValue -eq $null)
399 {
400     New-ItemProperty -Path $SurfaceRegKey -Name LSV -PropertyType DWORD -Value $lsv | Out-Null
401 }
402 Else
403 {
404     Set-ItemProperty -Path $SurfaceRegKey -Name LSV -Value $lsv
405 }
406 
407 If ($DateTimeRegValue -eq $null)
408 {
409     New-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -PropertyType String -Value $UTCDate | Out-Null
410 }
411 Else
412 {
413     Set-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -Value $UTCDate
414 }
415 
416 If ($OwnershipSessionIdRegValue -eq $null)
417 {
418     New-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -PropertyType String -Value $ownerSessionIdValue | Out-Null
419 }
420 Else
421 {
422     Set-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -Value $ownerSessionIdValue
423 }
424 
425 If ($PermissionSessionIdRegValue -eq $null)
426 {
427     New-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -PropertyType String -Value $permissionSessionIdValue | Out-Null
428 }
429 Else
430 {
431     Set-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -Value $permissionSessionIdValue
432 }
433 
434 If ($SettingsSessionIdRegValue -eq $null)
435 {
436     New-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -PropertyType String -Value $settingsSessionIdValue | Out-Null
437 }
438 Else
439 {
440     Set-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -Value $settingsSessionIdValue
441 }
442 
443 If ($IsResetRegValue -eq $null)
444 {
445     New-ItemProperty -Path $SurfaceRegKey -Name IsReset -PropertyType DWORD -Value 0 | Out-Null
446 }
447 Else
448 {
449     Set-ItemProperty -Path $SurfaceRegKey -Name IsReset -Value 0
450 }
451 
452 If ($certUsedRegValue -eq $null)
453 {
454     New-ItemProperty -Path $SurfaceRegKey -Name CertName -PropertyType String -Value $certName | Out-Null
455 }
456 Else
457 {
458     Set-ItemProperty -Path $SurfaceRegKey -Name CertName -Value $certName
459 }
460 
461 If ($certIssuerRegValue -eq $null)
462 {
463     New-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -PropertyType String -Value $certIssuer | Out-Null
464 }
465 Else
466 {
467     Set-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -Value $certIssuer
468 }
469 
470 If ($certSubjectRegValue -eq $null)
471 {
472     New-ItemProperty -Path $SurfaceRegKey -Name CertSubject -PropertyType String -Value $certSubject | Out-Null
473 }
474 Else
475 {
476     Set-ItemProperty -Path $SurfaceRegKey -Name CertSubject -Value $certSubject
477 }
```

### 設定名と Id

Surface uefi の設定または Surface UEFI 設定の権限を構成するには、設定名または設定 ID のいずれかで、各設定を参照する必要があります。 Surface UEFI の新しい更新があるたびに、新しい設定が追加されることがあります。 Surface デバイスで利用可能な設定の完全な一覧を取得する最適な方法は、[設定名] と [設定] Id と共に、 [Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703)の SEMM_Powershell.zip の ShowSettingsOptions.ps1 スクリプトを使って、IT をダウンロードすることです。 

ShowSettingsOptions.ps1 を実行するコンピューターには Microsoft Surface UEFI Manager がインストールされている必要がありますが、スクリプトは Surface デバイスを必要としません。


## SEMM Configuration Manager スクリプトの展開

クライアントデバイスで SEMM を構成して有効にする準備ができたら、次の手順として、これらのスクリプトを Configuration Manager でアプリケーションとして追加します。 構成マネージャーを開く前に、他のファイルを含まない共有フォルダーに次のファイルが存在することを確認します。

* ConfigureSEMM.ps1
* ResetSEMM.ps1
* SEMM 証明書 (たとえば、SEMMCertificate. .pfx)

SEMM 構成マネージャーのスクリプトは、スクリプトアプリケーションとして Configuration Manager に追加されます。 ConfigureSEMM.ps1 で SEMM をインストールするコマンドは、次のようになります。

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

SEMM を ResetSEMM.ps1 でアンインストールするコマンドは、次のようになります。

`Powershell.exe -file ".\ResetSEMM.ps1"`

SEMM Configuration Manager のスクリプトをアプリケーションとして Configuration Manager に追加するには、次の手順を実行します。

1. この記事の前半の「 [Microsoft SURFACE UEFI マネージャーの展開](#deploy-microsoft-surface-uefi-manager) 」セクションの手順1から手順5を実行して、アプリケーションの作成ウィザードを起動します。

2. 次の手順に従って、アプリケーションの作成ウィザードを実行します。

   - **[全般** ]- **アプリケーション情報を手動で指定**し、[ **次へ**] を選択します。

   - **[全般情報** ]-アプリケーションの名前 (semm など) と、このページの publisher、バージョン、コメントなどの必要な情報を入力します。 [ **次へ** ] を選択して続行します。

   - [**アプリケーションカタログ**] –このページのフィールドには、既定値を指定したままにすることができます。 **[次へ]** を選択します。

   - **展開の種類** – [ **追加** ] を選んで、展開の種類の作成ウィザードを開始します。

   - 次に示すように、展開の種類の作成ウィザードの手順を実行します。

     * **[全般**]-[ **Type** ] ドロップダウンメニューから [**スクリプトインストーラー** ] を選択します。 [ **展開の種類の情報を手動で指定** する] オプションが自動的に選択されます。 [ **次へ** ] を選択して続行します。
     * **[General Information** ]: 展開の種類の名前 (「Semm 構成スクリプト」など) を入力し、[ **次へ** ] をクリックして続行します。
     * **コンテンツ**-[**コンテンツの場所**] フィールドの横にある [**参照**] を選択し、semm 構成マネージャーのスクリプトが配置されているフォルダーを選択します。 [ **インストールプログラム** ] フィールドに、この記事の前半で説明した [インストールコマンド](#deploy-semm-configuration-manager-scripts) を入力します。 [ **アンインストールプログラム** ] フィールドに、この記事の前半で説明した [アンインストールコマンド](#deploy-semm-configuration-manager-scripts) を入力します (図2を参照)。 次のページに移動するには、[ **次へ** ] を選びます。
    
     ![SEMM 構成マネージャーのスクリプトをインストールコマンドとアンインストールコマンドとして設定する](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *図 2.  SEMM 構成マネージャーのスクリプトをインストールコマンドとアンインストールコマンドとして設定する*

     * **検出方法** – [ **句の追加** ] を選択して、semm Configuration Manager スクリプトレジストリキー検出ルールを追加します。 図3に示すように、 **検出ルール** のウィンドウが表示されます。 次の設定を使います。

       - [**設定の種類**] ドロップダウンメニューから [**レジストリ**] を選びます。
       - [**ハイブ**] ドロップダウンメニューから [ **HKEY_LOCAL_MACHINE** ] を選択します。
       - [**キー** ] フィールドに「 **SOFTWARE\Microsoft\Surface\SEMM** 」と入力します。
       - [**値**] フィールドに「 **certname** 」と入力します。
       - [**データ型**] ドロップダウンメニューから [**文字列**] を選択します。
       - この **アプリケーションボタンのプレゼンスを示すために、このレジストリ設定** を選択してください。
       - [ **値** ] フィールドに、スクリプトの58行目に入力した証明書の名前を入力します。
       - [ **OK]** を選択して、[ **検出ルール** ] ウィンドウを閉じます。

     ![レジストリキーを使用して SEMM に登録されているデバイスを特定する](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *図 3.  レジストリキーを使用して SEMM に登録されているデバイスを特定する*

     * [ **次へ** ] を選択して次のページに進みます。
     
     * [**ユーザーエクスペリエンス**] – [**インストールの動作**] ドロップダウンメニューから [**システム用にインストール**] を選びます。 ユーザーが証明書の拇印自体を記録して入力する必要がある場合は、 **ユーザーがログオンしたときにのみ**ログオン要件を設定しておきます。 管理者がユーザーの拇印を入力して、ユーザーがその拇印を表示する必要がない場合は、ユーザーが**ログオン要件**のドロップダウンメニューからログオンしている**かどうか**を選択します。

     * **要件** – ConfigureSEMM.ps1 スクリプトは、semm を有効にする前に、デバイスが Surface デバイスであるかどうかを自動的に確認します。 ただし、SEMM で管理する必要がないデバイスを持つコレクションにこのスクリプトアプリケーションを展開する場合は、ここに要件を追加して、このアプリケーションが SEMM で管理する Surface デバイスまたはデバイスでのみ実行されることを確認します。 [ **次へ** ] を選択して続行します。
     
     * **依存関係** -[ **追加** ] を選択して、[ **依存関係の追加** ] ウィンドウを開きます。

       * [ **追加** ] を選択して、[ **必要なアプリケーションの指定** ] ウィンドウを開きます。

          - [ **依存関係グループ名** ] フィールドに semm の依存関係の名前を入力します (たとえば、 *semm アセンブリ*)。

          - **利用可能なアプリケーション**の一覧と MSI 展開の種類から [ **Microsoft Surface UEFI Manager** ] を選択し、[ **OK** ] を選択して [**必要なアプリケーションの指定**] ウィンドウを閉じます。
          
         *   Configuration Manager スクリプトを使用して SEMM を有効にしようとしたときに Microsoft Surface UEFI Manager がデバイスに自動的にインストールされるようにするには、[ **自動インストール** ] チェックボックスをオンのままにします。 [ **OK]** を選択して、[ **依存関係の追加** ] ウィンドウを閉じます。

     * [ **次へ** ] を選択して続行します。
     
     * **概要** : 展開の種類の作成ウィザードで入力した情報が、このページに表示されます。 [ **次へ** ] を選んで選択内容を確認します。
     
     * **進行状況** : このページには、semm スクリプトアプリケーションの展開の種類が追加されたときの進行状況バーと状態が表示されます。
     
     * **完了** -展開の種類の作成の確認は、プロセスが完了したときに表示されます。 [展開の種類の作成] ウィザードを終了するには、[ **閉じる** ] を選択します。

   - **概要** : アプリケーションの作成ウィザードで入力した情報が表示されます。 [ **次へ** ] を選択してアプリケーションを作成します。

   - **進行状況** : ソフトウェアライブラリにアプリケーションが追加されたときの進行状況バーと状態は、このページに表示されます。

   - [**完了**]-アプリケーションの作成プロセスが完了すると、アプリケーションの作成が成功したことが確認されます。 [ **閉じる** ] を選択して、アプリケーションの作成ウィザードを終了します。

構成マネージャーのソフトウェアライブラリでスクリプトアプリケーションを利用できるようになったら、デバイスまたはコレクションに対して作成したスクリプトを使用して、SEMM を配布し、展開することができます。 自動的にインストールされる依存関係として Microsoft Surface UEFI Manager アセンブリを構成している場合は、1つのステップで SEMM を展開できます。 依存関係としてアセンブリを構成していない場合は、SEMM を有効にする前に、管理するデバイスにそれらのアセンブリをインストールする必要があります。

このスクリプトアプリケーションとエンドユーザーに表示される構成を使用して SEMM を展開すると、PowerShell スクリプトが開始され、証明書の拇印が PowerShell ウィンドウに表示されます。 デバイスの再起動後に、ユーザーがこの拇印を記録して、Surface UEFI のプロンプトに従って入力することができます。

または、アプリケーションのインストールを構成して、自動的に再起動し、ユーザーに表示されないようにインストールすることもできます。 このシナリオでは、再起動時に各デバイスに拇印を入力する必要があります。 証明書ファイルへのアクセス権を持つすべての技術者は、CertMgr で証明書を表示して、拇印を読み取ることができます。 CertMgr で拇印を表示する手順については、この記事の「 [SEMM 構成マネージャーのスクリプトを作成または変更](#create-or-modify-the-semm-configuration-manager-scripts) する」を参照してください。

構成マネージャーと共に展開されたデバイスからの SEMM の削除は、Configuration Manager を使用してアプリケーションをアンインストールするのと同じように簡単です。 このアクションは ResetSEMM.ps1 スクリプトを開始し、SEMM の展開時に使用されたものと同じ証明書ファイルを使ってデバイスを登録解除します。

> [!NOTE]
> Microsoft Surface では、デバイスの登録を解除する必要がある場合にのみ、リセットパッケージを作成することをお勧めします。 通常、これらのリセットパッケージは、シリアル番号によって識別される1つのデバイスに対してのみ有効です。 ただし、この証明書で SEMM に登録されているすべてのデバイスで動作するユニバーサルリセットパッケージを作成することもできます。
> 
> ユニバーサルリセットパッケージは、SEMM でデバイスを登録するために使った証明書と同じように保護することを強くお勧めします。 証明書自体と同じように、このユニバーサルリセットパッケージを使って、SEMM から組織の Surface デバイスの登録を解除することもできます。
> 
> リセットパッケージをインストールすると、サポートされている最小の値 (LSV) が1の値にリセットされます。 既存の構成パッケージを使用して、デバイスを reenroll することができます。 所有権が取得される前に、デバイスによって証明書の拇印の入力を求められます。
> 
> このため、SEMM のデバイスの reenrollment では、新しいパッケージを作成し、そのデバイスにインストールする必要があります。 この操作は新しい登録であり、SEMM にすでに登録されているデバイスの構成に変更がないため、デバイスでは、所有権が取得される前に、証明書の拇印の入力を求められます。
