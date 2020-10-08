---
title: プロビジョニング パッケージの作成 (Surface Hub)
description: Windows 10 では、レジストリや構成サービス プロバイダー (CSP) を使用する設定を、プロビジョニング パッケージによって構成することができます。
ms.assetid: 8AA25BD4-8A8F-4B95-9268-504A49BA5345
ms.reviewer: ''
manager: laurawi
keywords: 証明書の追加, プロビジョニング パッケージ
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2019
ms.localizationpriority: medium
ms.openlocfilehash: ecbeca9f0910f1fa1ff2721bcf1b745195552ca2
ms.sourcegitcommit: f74253629aaf073b35b1af69439f76e63392c5aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "11103801"
---
# プロビジョニング パッケージの作成 (Surface Hub)

このトピックでは、Windows 構成デザイナーを使ってプロビジョニング パッケージを作成し、それを Surface Hub デバイスに適用する方法について説明します。 Surface Hub では、プロビジョニング パッケージを使って証明書を追加し、ユニバーサル Windows プラットフォーム (UWP) アプリをインストールして、ポリシーと設定をカスタマイズすることができます。

最初の実行の設定時に USB スティックを使うか、**設定**アプリを通じてプロビジョニング パッケージを適用できます。 


## 長所
-   モバイル デバイス管理 (MDM) プロバイダーを使用せずにデバイスをすばやく構成できます。

-   ネットワーク接続は必要ありません。

-   簡単に適用できます。

[プロビジョニング パッケージの利点と使用方法について説明します。](https://technet.microsoft.com/itpro/windows/configure/provisioning-packages)


## 要件 

プロビジョニング パッケージを作成して Surface Hub に適用するには、次のものが必要です。

-   Windows 構成デザイナー。これは Microsoft Store または Windows 10 アセスメント & デプロイメント キット (ADK) からインストールできます。 [Windows 構成デザイナーをインストールする方法をこちらで確認できます。](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)
-   USB スティック 1 個。
-   **設定**アプリを使ってパッケージを適用する場合は、デバイスの管理者資格情報が必要です。

Windows 10 を実行している PC でプロビジョニング パッケージを作成して、パッケージを USB ドライブに保存し、それを Surface Hub に展開します。


## Surface Hub プロビジョニング パッケージ向けにサポートされる項目

**プロビジョニング Surface Hub デバイス**ウィザードでは、以下を実行できます。

- Active Directory、Azure Active Directory、MDM への登録 
- デバイス管理者アカウントの作成 
- アプリケーションと証明書の追加
- プロキシ設定の構成
- Surface Hub の構成ファイルの追加

>[!WARNING]
>ウィザードを使って Azure Active Directory の登録を構成するには、Windows 10 で Windows 構成デザイナーを実行する必要があります。

詳細プロビジョニング エディターを使って、Surface Hub 向けのプロビジョニング パッケージに次の項目を追加できます。

- **ポリシー** - Surface Hub は、[ポリシー構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#surfacehubpolicies)のポリシーのサブセットをサポートします。 
- **設定** - [SurfaceHub 構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)のすべての設定を構成できます。

>[!TIP]
> ウィザードを使用して共通設定のパッケージを作成した後、詳細エディターに切り替えて他の設定を追加します。
>
>![詳細エディターの起動](images/icd-simple-edit.png)

## Surface Hub プロビジョニング ウィザードの使用

[Windows 構成デザイナーのインストール](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)が完了した後、プロビジョニング パッケージを作成できます。

### プロビジョニング パッケージを作成する 

1. 次の手順で Windows 構成デザイナーを開きます。
   - スタート画面または [スタート] メニューの検索ウィンドウで、「Windows 構成デザイナー」と入力して Windows 構成デザイナーのショートカットをクリックします。 
    
     または
    
   - Windows 構成デザイナーを ADK からインストールした場合は、`C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (x64 コンピューターを使用している場合) または `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (x86 コンピューターを使用している場合) に移動し、**ICD.exe** をダブルクリックします。

2. **[プロビジョニング Surface Hub デバイス]** をクリックします。

3. プロジェクトに名前を付け、**[次へ]** をクリックします。

### 設定の構成

<table>
<tr><td style="width:45%" valign="top"><img src="images/one.png" alt="step one"/> <img src="images/add-certificates.png" alt="add certificates"/></br></br>証明書を使ってデバイスをプロビジョニングするには、<strong>[証明書の追加]</strong> をクリックします。 証明書の名前を入力し、使用する証明書を表示して選択します。</td><td><img src="images/add-certificates-details.png" alt="add a certificate"/></td></tr> 
<tr><td style="width:45%" valign="top"><img src="images/two.png" alt="step two"/>  <img src="images/proxy.png" alt="configure proxy settings"/></br></br>プロキシ設定を <strong>[はい]</strong> または <strong>[いいえ]</strong> に切り替えます。 Surface Hub の既定の構成では、プロキシ設定が自動的に検出されます。設定を変更する必要がない場合は、<strong>[いいえ]</strong> を選択します。 ただし、それまでのプロキシ サーバーの使用を必要とするインフラストラクチャから、プロキシ サーバーを必要としないインフラストラクチャに変更した場合は、<strong>[はい]</strong> と <strong>[設定を自動的に検出]</strong> を選択することで、プロビジョニング パッケージを使って Surface Hub デバイスを既定の設定に戻すことができます。 </br></br><strong>[はい]</strong> に切り替えると、プロキシ設定を自動的に検出するか、設定を手動で構成するかを選択でき、手動で構成する場合は、スクリプトを設定するための URL を入力するか、静的なプロキシ サーバー アドレスを入力できます。 さらにローカルのアドレスにプロキシ サーバーを使うかどうか、また例外 (Surface Hub がプロキシ サーバーを使用せずに直接接続する必要があるアドレス) を入力するかどうかを指定することもできます。  </td><td><img src="images/proxy-details.png" alt="configure proxy settings"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/three.png" alt="step three"/>  <img src="images/set-up-device-admins.png" alt="device admins"/></br></br>デバイスを Active Directory に登録し、設定アプリを使用するセキュリティ グループを指定するか、Azure Active Directory に登録してグローバル管理者が設定アプリを使用できる環境にするか、デバイス上にローカル管理者アカウントを作成することができます。</br></br>デバイスを Active Directory に登録するには、最小限の特権を持つユーザー アカウントの資格情報を入力して、デバイスをドメインに参加させ、Surface Hub で管理者資格情報を持つセキュリティ グループを指定します。 デバイスを Active Directory に登録するプロビジョニング パッケージを、リセットされた Surface Hub に適用する場合、同じドメイン アカウントを使用できるのは、表示されているアカウントがドメイン管理者である場合か、Surface Hub を最初に設定したのと同じアカウントである場合のみです。 そうでない場合は、別のドメイン アカウントをプロビジョニング パッケージで使う必要があります。</br></br>Windows 構成デザイナー ウィザードを使って Azure AD の登録を一括で構成する前に、<a href="https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup" data-raw-source="[set up Azure AD join in your organization](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup)">組織での Azure AD 参加の設定</a>を行います。 Azure AD テナントの <strong>[ユーザーあたりのデバイスの最大数]</strong> の設定は、ウィザードで利用できる一括トークンを使用できる回数を決定します。 Azure AD にデバイスを登録するには、そのオプションを選択して、ウィザードを使って取得する一括トークンのフレンドリ名を入力します。 トークンの有効期限を設定します (最大、トークンの取得日から 30 日間)。 <strong>[一括トークンを取得する]</strong> をクリックします。 <strong>[&#39;s にサインインします </strong> ] ウィンドウで、Azure AD にデバイスを参加するためのアクセス許可を持つアカウントを入力し、その後、パスワードを入力します。 <strong>[承諾]</strong> をクリックして、Windows 構成デザイナーに必要なアクセス許可を付与します。</br></br>ローカル管理者アカウントを作成するには、そのオプションを選択して、ユーザー名とパスワードを入力します。 </br></br><strong>重要:</strong> プロビジョニング パッケージにローカル アカウントを作成する場合、42 日ごとに<strong>設定</strong>アプリを使ってパスワードを変更する必要があります。 その期間内にパスワードを変更しない場合、アカウントがロックされてサインインできなくなる可能性があります。  </td><td><img src="images/set-up-device-admins-details.png" alt="join Active Directory, Azure AD, or create a local admin account"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/four.png" alt="step four"/> <img src="images/enroll-mdm.png" alt="enroll in device management"/></br></br>MDM への登録について、<strong>[はい]</strong> または <strong>[いいえ]</strong> を切り替えます。 </br></br><strong>[はい]</strong> を選択した場合、デバイスの登録を許可されたサービス アカウントとパスワードまたは証明書サムプリントを指定し、併せて認証の種類を指定する必要があります。 MDM プロバイダーで必要な場合は、探索サービス、登録サービス、ポリシー サービスの URL も入力します。 <a href="manage-settings-with-mdm-for-surface-hub.md" data-raw-source="[Learn more about managing Surface Hub with MDM.](manage-settings-with-mdm-for-surface-hub.md)">MDM による Surface Hub の管理について詳しく知る。</a></td><td><img src="images/enroll-mdm-details.png" alt="enroll in mobile device management"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/five.png" alt="step five"/> <img src="images/add-applications.png" alt="add applications"/></br></br>プロビジョニング パッケージには、複数のユニバーサル Windows プラットフォーム (UWP) アプリをインストールできます。 設定について詳しくは「<a href="https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps" data-raw-source="[Provision PCs with apps](https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps)">アプリを使用して PC をプロビジョニングする</a>」をご覧ください。 </br></br><strong>重要: </strong> ウィザードインターフェイスで従来の Win32 アプリを選ぶことはできますが、Surface Hub に適用されるプロビジョニングパッケージには UWP アプリのみを含める必要があります。 従来の Win32 アプリを含めると、プロビジョニングが失敗します。 </td><td><img src="images/add-applications-details.png" alt="add an application"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/six.png" alt="step six"/>  <img src="images/add-config-file.png" alt="Add configuration file"/></br></br>この手順では、どの設定も構成し&#39;ません。 ここではデバイス アカウントの一覧が含まれた構成ファイルを含める手順を説明します。 構成ファイルには、列ヘッダーを含めないでください。 プロビジョニング パッケージを Surface Hub に適用するときに、Surface Hub の構成ファイルが USB ドライブに含まれている場合は、アカウントとデバイスのフレンドリ名をファイルから選択できます。 例については、「<a href="#sample-configuration-file" data-raw-source="[Sample configuration file](#sample-configuration-file)">構成ファイルの例</a>」をご覧ください。</br></br><strong>重要: </strong> 構成ファイルは、既定のセットアップエクスペリエンス (OOBE) 中にのみ適用できます。また、windows 10 バージョン1703でリリースされた Windows 構成デザイナーを使って作成されたプロビジョニングパッケージでのみ使うことができます。  </td><td><img src="images/add-config-file-details.png" alt="Add a Surface Hub configuration file"/></td></tr>
<tr><td style="width:45%" valign="top">  <img src="images/finish.png" alt="finish"/></br></br>プロビジョニング パッケージを保護するためのパスワードを設定することができます。 プロビジョニング パッケージをデバイスに適用する場合は、このパスワードを入力する必要があります。</td><td><img src="images/finish-details.png" alt="Protect your package"/></td></tr>
</table>

完了したら、[**作成**] をクリックします。 これは数秒で終わります。 パッケージがビルドされると、ページの下部に、パッケージの格納場所がハイパーリンクで表示されます。

## 構成ファイルの例

Surface Hub の構成ファイルには、デバイスが Exchange および Skype for Business との接続に使用できるデバイス アカウントの一覧が含まれています。 プロビジョニング パッケージを Surface Hub に適用するときに、構成ファイルを USB フラッシュ ドライブのルート ディレクトリに含めたうえで、そのデバイスに適用する適切なアカウントを選択できます。 構成ファイルは、アウトオブボックスの設定エクスペリエンス (OOBE) でのみ適用でき、Windows 10 バージョン 1703 でリリースされた Windows 構成デザイナーを使って作成したプロビジョニング パッケージでのみ使用できます。

Microsoft Excel などの CSV エディターを使って、`SurfaceHubConfiguration.csv` という名前の CSV ファイルを作成します。 作成したファイルに、デバイス アカウントとフレンドリ名の一覧を次の形式で入力します。

```console
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```
>[!IMPORTANT]
>構成ファイルではデバイス アカウントのパスワードがプレーンテキストで保存されるため、デバイスにプロビジョニング パッケージを適用した後、パスワードを更新することをお勧めします。 MDM 経由でのパスワードの更新には、[Surface Hub 構成サービス プロバイダー (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) の [DeviceAccount ノード](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp#deviceaccount)を使用できます。


次に `SurfaceHubConfiguration.csv` の例を示します。 

```console
Rainier@contoso.com,password,Rainier Surface Hub
Adams@contoso.com,password,Adams Surface Hub
Baker@contoso.com,password,Baker Surface Hub
Glacier@constoso.com,password,Glacier Surface Hub
Stuart@contoso.com,password,Stuart Surface Hub
Fernow@contoso.com,password,Fernow Surface Hub
Goode@contoso.com,password,Goode Surface Hub
Shuksan@contoso.com,password,Shuksan Surface Hub
Buckner@contoso.com,password,Buckner Surface Hub
Logan@contoso.com,password,Logan Surface Hub
Maude@consoto.com,password,Maude Surface hub
Spickard@contoso.com,password,Spickard Surface Hub
Redoubt@contoso.com,password,Redoubt Surface Hub
Dome@contoso.com,password,Dome Surface Hub
Eldorado@contoso.com,password,Eldorado Surface Hub
Dragontail@contoso.com,password,Dragontail Surface Hub
Forbidden@contoso.com,password,Forbidden Surface Hub
Oval@contoso.com,password,Oval Surface Hub
StHelens@contoso.com,password,St Helens Surface Hub
Rushmore@contoso.com,password,Rushmore Surface Hub
```

## 高度なプロビジョニングの使用

[Windows 構成デザイナーのインストール](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)が完了した後、プロビジョニング パッケージを作成できます。

### プロビジョニング パッケージの作成 (上級)

1. 次の手順で Windows 構成デザイナーを開きます。
   - スタート画面または [スタート] メニューの検索ウィンドウで、「Windows 構成デザイナー」と入力して Windows 構成デザイナーのショートカットをクリックします。 
    
     または
    
   - Windows 構成デザイナーを ADK からインストールした場合は、`C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (x64 コンピューターを使用している場合) または `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (x86 コンピューターを使用している場合) に移動し、**ICD.exe** をダブルクリックします。

2. **[プロビジョニングの詳細設定]** をクリックします。
   
3. プロジェクトに名前を付け、**[次へ]** をクリックします。

4. [ **Windows 10 チーム**との共通] を選択し、[ **次へ**] をクリックして、[ **完了**] をクリックします。

    ![ICD の新しいプロジェクト](images/icd-new-project.png)

5. プロジェクトの [ **利用可能なカスタマイズ**] で、[ **一般的なチームの設定**] を選択します。

    ![ICD の一般的な設定](images/icd-common-settings.png)


### 証明書をパッケージに追加する
プロビジョニング パッケージを使って、デバイスが Microsoft Exchange への認証に使う証明書をインストールすることができます。

> [!NOTE]
> 証明書をインストールできるのはデバイス (ローカル コンピューター) ストアのみで、ユーザー ストアにはインストールできません。 組織でユーザー ストアに証明書をインストールする必要がある場合は、モバイル デバイス管理 (MDM) を使ってこれらの証明書を展開します。 詳細については、MDM ソリューションのドキュメントを参照してください。

1. **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[Certificates]** > **[ClientCertificates]** の順に移動します。 

2. **[CertificateName]** を入力し、**[追加]** をクリックします。 

2. **[CertificatePassword]** を入力します。 

3. **[CertificatePath]** で、証明書を探して選びます。 

4. **[ExportCertificate]** を **[False]** に設定します。

5. **[KeyLocation]** で、**[ソフトウェアのみ]** を選びます。


### ユニバーサル Windows プラットフォーム (UWP) アプリをパッケージに追加する
UWP アプリをプロビジョニング パッケージに追加する前に、アプリ パッケージ (.appx または .appxbundle) と依存関係ファイルが必要です。 ビジネス向け Microsoft Store からアプリを入手した場合は、*エンコードされていない*アプリのライセンスも必要です。 ビジネス向け Microsoft Store からこれらの項目をダウンロードする方法については、「[オフライン アプリの配布](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)」をご覧ください。

1. **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[UniversalAppInstall]** > **[DeviceContextApp]** の順に移動します。

2. アプリの **PackageFamilyName** を入力し、**[追加]** をクリックします。 一貫性を保つために、アプリのパッケージ ファミリ名を使います。 ビジネス向け Microsoft Store からアプリを入手した場合は、アプリのライセンスからパッケージ ファミリ名がわかります。 テキストエディターを使用してライセンスファイルを開き、... タグの間の値を使います。 \<PFM\> \</PFM\>

3. **[ApplicationFile]** で、**[参照]** をクリックし、ターゲット アプリ (\*.appx または \*.appxbundle のどちらか) を探して選びます。

4. **[DependencyAppxFiles]** で、**[参照]** をクリックし、アプリの依存関係を探して追加します。 Surface Hub の場合、必要なのはこれらの依存関係の x64 バージョンだけです。

ビジネス向け Microsoft Store からアプリを入手した場合は、プロビジョニング パッケージにアプリのライセンスを追加する必要もあります。

1. アプリのライセンスのコピーを作成し、その名前を拡張子 **.ms-windows-store-license** を使うように変更します。 たとえば、"example.xml" は "example.ms-windows-store-license" になります。

2. ICD の **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[UniversalAppInstall]** > **[DeviceContextAppLicense]** の順に移動します。

3. **[LicenseProductId]** を入力し、**[追加]** をクリックします。 一貫性を保つのために、アプリのライセンスにあるアプリのライセンス ID を使います。 テキスト エディタでライセンス ファイルを開きます。 次に、タグで、 \<License\> **licenseid** 属性の値を使用します。

4. 新しい **[LicenseProductId]** ノードを選択します。 **[LicenseInstall]** では、**[参照]** をクリックして、手順 1 で名前を変更したライセンス ファイルを見つけて選択します。


### ポリシーをパッケージに追加する
Surface Hub は、[ポリシー構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)のポリシーのサブセットをサポートします。 これらのポリシーの一部は ICD で構成できます。

1. **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[ポリシー]** の順に移動します。

2. 利用可能なポリシー領域のいずれかを選択します。

3. プロビジョニング パッケージに追加するポリシーを選択して設定します。


### Surface Hub の設定をパッケージに追加する 

[SurfaceHub 構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)から、設定をプロビジョニング パッケージに追加できます。 

1. [**利用可能なカスタマイズ**] ウィンドウで、[**ランタイム設定**  >  **SurfaceHub**に移動します。

2. 利用可能な設定領域のいずれかを選択します。

3. プロビジョニング パッケージに追加する設定を選択して設定します。 


## パッケージをビルドする

1. プロビジョニング パッケージの構成が完了したら、**[ファイル]** メニューの **[保存]** をクリックします。

2. プロジェクト ファイルに機密情報が含まれている可能性があることを示す警告を確認し、**[OK]** をクリックします。

    > [!IMPORTANT]
    > プロビジョニング パッケージを作成する場合、プロジェクト ファイルとプロビジョニング パッケージ (.ppkg) ファイルに機密情報を含めることができます。 .ppkg ファイルは暗号化するかどうかを選べますが、プロジェクト ファイルは暗号化されません。 プロジェクト ファイルは、安全な場所に保存し、不要になったときに削除する必要があります。

3. **[エクスポート]** メニューの **[プロビジョニング パッケージ]** をクリックします。

4. **[所有者]** を **[IT 管理者]** に変更して、このプロビジョニング パッケージの優先順位を他のソースからこのデバイスに適用されるプロビジョニング パッケージよりも高くします。

5. **[パッケージのバージョン]** の値を設定し、**[次へ]** を選択します。

    > [!TIP]
    > 既存のパッケージに変更を加えてバージョン番号を変更することで、以前に適用されたパッケージを更新できます。

6. オプション: パッケージの暗号化を選択し、パッケージの署名を有効にできます。

    -   **[パッケージの暗号化を有効にする]**: このオプションを選択した場合、自動生成されたパスワードが画面に表示されます。

    -   **[パッケージの署名を有効にする]**: このオプションを選択した場合、パッケージの署名に使用する有効な証明書を選ぶ必要があります。 **[参照]** をクリックし、パッケージの署名に使う証明書を選んで、証明書を指定します。

        > [!IMPORTANT]
        > プロビジョニング パッケージに信頼済みプロビジョニング証明書を含めることをお勧めします。 パッケージがデバイスに適用されると、証明書がシステム ストアに追加されます。その後、システム メッセージを表示せずに、その証明書で署名されたすべてのパッケージを適用することができます。 

7. **[次へ]** をクリックし、ビルドしたプロビジョニング パッケージの出力先を指定します。 既定では、Windows ICD はプロジェクト フォルダーを出力先として使います。<p>
必要に応じて、 **[参照]** をクリックして既定の出力先を変更できます。

8. **[次へ]** をクリックします。

9. パッケージのビルドを開始するには、 **[ビルド]** をクリックします。 ビルド ページにプロジェクト情報が表示され、進行状況バーでビルドの状態が示されます。<p>
ビルドを取り消す必要がある場合は、**[キャンセル]** をクリックします。 これにより、現在のビルド プロセスが取り消され、ウィザードが閉じられて、**[カスタマイズ ページ]** に戻ります。

10. ビルドに失敗した場合は、プロジェクト フォルダーへのリンクが含まれたエラー メッセージが表示されます。 エラーの原因を特定するには、ログを調べることができます。 問題が解決したら、パッケージをもう一度ビルドしてみてください。<p>
ビルドに成功した場合は、プロビジョニング パッケージの名前、出力ディレクトリ、プロジェクト ディレクトリが表示されます。

    -   必要に応じて、パッケージの出力先として別のパスを選択し、もう一度プロビジョニング パッケージをビルドすることもできます。 これを行うには、**[戻る]** をクリックして出力パッケージの名前とパスを変更し、**[次へ]** をクリックしてもう一度ビルドを開始します。
    
    -   完了したら、 **[完了]** をクリックしてウィザードを閉じ、 **[カスタマイズ ページ]** に戻ります。

11. **[出力場所]** リンクを選び、パッケージの場所へ移動します。 .ppkg を空の USB フラッシュ ドライブにコピーします。


## プロビジョニング パッケージを Surface Hub に適用する

プロビジョニング パッケージを Surface Hub に展開するためのオプションは 2 つあります。 [初めて実行するウィザード](#apply-a-provisioning-package-during-first-run)では、証明書をインストールするプロビジョニングパッケージを適用できます。または、初回実行プログラムが完了した後、設定を使用して、設定、アプリ、証明書を構成するプロビジョニングパッケージを適用[できます。](#apply-a-package-using-settings) 


### 最初の実行時にプロビジョニング パッケージを適用する

> [!IMPORTANT]
> 初めて実行するプログラムでは、プロビジョニングパッケージを使って証明書をインストールする必要があります。 **設定**アプリを使って、アプリをインストールし、その他の設定を適用します。

1. Surface Hub を初めて起動すると、[**[こんにちは]**](first-run-program-surface-hub.md#first-page) というページが表示されます。 操作を続行する前に、設定が適切に構成されていることを確認してください。

2. .ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。 パッケージがドライブのルート ディレクトリにある場合は、初回実行プログラムによってそれが認識され、デバイスをセットアップするかどうかを確認するメッセージが表示されます。 **[セットアップ]** を選択します。

    ![デバイスをセットアップしますか?](images/provisioningpackageoobe-01.png)

3. 次にプロビジョニング元を選択する画面が表示されます。 **[リムーバブル メディア]** を選んで **[次へ]** をタップします。

    ![このデバイスのプロビジョニング](images/provisioningpackageoobe-02.png)
    
4. 適用するプロビジョニング パッケージ (\*.ppkg) を選んで、**[次へ]** をタップします。 最初の実行時にインストールできるパッケージは 1 つだけです。

    ![パッケージの選択](images/provisioningpackageoobe-03.png)

5. 初回実行プログラムによって、プロビジョニング パッケージが適用される変更の概要が表示されます。 **[はい、追加する]** を選択します。  

    ![このパッケージを信頼しますか?](images/provisioningpackageoobe-04.png)
    
6. 構成ファイルが USB フラッシュ ドライブのルート ディレクトリに含まれる場合、**[構成を選択します]** が表示されます。 構成ファイルの最初のデバイス アカウントが、Surface Hub に適用されるアカウント情報の概要と共に表示されます。

    ![構成を選択します](images/ppkg-config.png)    

7. **[構成を選択します]** で、適用するデバイス名を選択し、**[次へ]** をクリックします。

    ![デバイスのフレンドリ名を選択します](images/ppkg-csv.png)
    
プロビジョニング パッケージに含まれている設定がデバイスに適用され、OOBE が完了します。 デバイスの再起動後、USB フラッシュ ドライブを削除することができます。

### 設定を使ってパッケージを適用する

1. .ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。

2. Surface Hub から**設定**を起動し、メッセージが表示されたら管理者の資格情報を入力します。

3. **[Surface Hub]** > **[デバイス管理]** に移動します。 **[プロビジョニング パッケージ]** で、**[プロビジョニング パッケージを追加または削除する]** を選択します。

4. **[パッケージの追加]** を選択します。

5. プロビジョニング パッケージを選択し、**[追加]** を選択します。 求められた場合は、管理者の資格情報を再入力する必要があります。

6. プロビジョニング パッケージによって適用される変更の概要が表示されます。 **[はい、追加する]** を選択します。


