---
title: プロビジョニング パッケージの作成
description: Windows 10 では、レジストリや構成サービス プロバイダー (CSP) を使用する設定を、プロビジョニング パッケージによって構成することができます。
ms.assetid: 8AA25BD4-8A8F-4B95-9268-504A49BA5345
ms.reviewer: dpandre
manager: laurawi
keywords: 証明書の追加, プロビジョニング パッケージ
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/28/2021
ms.localizationpriority: medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 087826a7a0cba7a47accc0d3d66714289f2ae9d2
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613984"
---
# <a name="create-provisioning-packages-for-surface-hub"></a>ユーザーのプロビジョニング パッケージを作成Surface Hub

プロビジョニング パッケージを使用すると、主要な機能の展開を自動化し、組織内のすべての Surface Hub で一貫性のあるエクスペリエンスを提供できます。  別Windows PC で構成デザイナー (WCD) を使用すると、次のタスクを実行できます。

- Active Directory または Active Directory に登録Azure Active Directory
- デバイス管理者アカウントの作成
- アプリケーションと証明書の追加
- プロキシ設定の構成
- Surface Hub の構成ファイルの追加
- 構成 [サービス プロバイダー (CSP) の設定を構成する](/windows/client-management/mdm/surfacehub-csp)

## <a name="overview"></a>概要

1. サーバーを実行している別Windows 10、Windows[構成デザイナー](https://www.microsoft.com/store/apps/9nblggh4tx22)をインストールMicrosoft Store。
1. [[**デバイスのプロビジョニングSurface Hubウィザード**](#use-surface-hub-provisioning-wizard)を使用して共通の設定を構成する] を選択します。 または、[ [高度なプロビジョニング] を選択](#use-advanced-provisioning) して、可能なすべての設定を表示および構成します。
1. プロビジョニング パッケージを作成し、USB ドライブに保存します。
1. 最初に実行するセットアップ中Surface Hub、またはアプリを使用して、パッケージを設定します。 詳細については、「Create [a provisioning package for a provisioning package for Windows 10」 を参照してください](/windows/configuration/provisioning-packages/provisioning-create-package)。

## <a name="use-surface-hub-provisioning-wizard"></a>プロビジョニング ウィザードSurface Hub使用する

1. [構成Windowsを開き、[デバイスのプロビジョニング **] をSurface Hubします**。<br>
    ![Surface Hub プロビジョニング ウィザードの使用](images/sh-prov-start.png)
    
2. プロジェクトに名前を付け、[次へ] を **選択します**。

### <a name="add-certificates"></a>証明書を追加する

> [!div class="mx-imgBorder"]
> ![証明書の追加](images/sh-prov-cert.png)

デバイスを証明書でプロビジョニングするには、[証明書の追加 **] を選択します**。 証明書の名前を入力し、参照して使用する証明書を選択します。  高度なプロビジョニング オプションについては、「パッケージに証明書を追加 [する」のセクションを参照してください](#add-a-certificate-to-your-package)。

### <a name="configure-proxy-settings"></a>プロキシ設定の構成

> [!div class="mx-imgBorder"]
> ![プロキシ設定の構成](images/sh-prov-proxy.png)

1. プロキシ設定を **[はい]** または **[いいえ]** に切り替えます。 既定では、Surface Hubプロキシ設定が自動的に検出されます。 ただし、それまでのプロキシ サーバーの使用を必要とするインフラストラクチャから、プロキシ サーバーを必要としないインフラストラクチャに変更した場合は、**[はい]** と **[設定を自動的に検出]** を選択することで、プロビジョニング パッケージを使って Surface Hub デバイスを既定の設定に戻すことができます。
2. [はい] **を切り**替える場合は、プロキシ設定を自動的に検出するか、次のいずれかを入力して手動で設定を構成できます。

    - セットアップ スクリプトの URL。
    - 静的プロキシ サーバーのアドレスとポート情報。

3. セットアップ スクリプトまたはプロキシ サーバーを使用する場合は、[設定を自動的に検出 **する] をオフにします**。 セットアップ スクリプトまたはプロキシ サーバー *を* 使用できます。両方を使用することはできません。
4. 例外 (プロキシ サーバーをSurface Hub直接接続する必要があるアドレス) を入力します。 **例:** *.office365.com
5. プロキシ サーバーをローカル アドレスに使用するかどうかを指定します。

### <a name="set-up-device-admins"></a>デバイス管理者の設定

 > [!div class="mx-imgBorder"]
 > ![Active Directory、Azure ADに参加する、またはローカル管理者アカウントを作成する](images/sh2-wcd.png)

デバイスを Active Directory に登録し、設定アプリを使用するセキュリティ グループを指定するか、Azure Active Directory に登録してグローバル管理者が設定アプリを使用できる環境にするか、デバイス上にローカル管理者アカウントを作成することができます。

1. デバイスを Active Directory に登録するには、最小限の特権を持つユーザー アカウントの資格情報を入力して、デバイスをドメインに参加させ、Surface Hub で管理者資格情報を持つセキュリティ グループを指定します。 パッケージをリセットされた Surface Hubに適用する場合は、最初に設定したアカウントと同じアカウントである限り、同じSurface Hubできます。 そうでない場合は、別のドメイン アカウントをプロビジョニング パッケージで使う必要があります。
2. Azure の一括登録Windows構成する前に[、Azure](/azure/active-directory/devices/azureadjoin-plan)AD参加実装を計画ADしてください。 Azure AD テナントの **[ユーザーあたりのデバイスの最大数]** の設定は、ウィザードで利用できる一括トークンを使用できる回数を決定します。
3. Azure AD にデバイスを登録するには、そのオプションを選択して、ウィザードを使って取得する一括トークンのフレンドリ名を入力します。 トークンの有効期限を設定します (最大、トークンの取得日から 30 日間)。 [一 **括トークンの取得] を選択します**。 **[サインインしましょう]** ウィンドウで、デバイスを Azure AD に参加させるアクセス許可を持つアカウントを入力し、次にパスワードを入力します。 [**同意する]** を選択Windows構成デザイナーに必要なアクセス許可を付与します。
4. ローカル管理者アカウントを作成するには、そのオプションを選択して、ユーザー名とパスワードを入力します。

> [!IMPORTANT]
> プロビジョニング パッケージにローカル アカウントを作成する場合、42 日ごとに**設定**アプリを使ってパスワードを変更する必要があります。 その期間内にパスワードを変更しない場合、アカウントがロックされてサインインできなくなる可能性があります。

### <a name="enroll-in-third-party-mdm-provider"></a>サード パーティの MDM プロバイダーに登録する

> [!div class="mx-imgBorder"]
> ![サードパーティのモバイル デバイス管理に登録する](images/sh-prov-mdm.png)

サード パーティのモバイル デバイス管理 (MDM) プロバイダーを使用する場合は、このセクションを使用してデバイスを登録Surface Hub。 Intune に登録するには、前のセクションで説明したように、最初に Azure AD 参加をセットアップし、次の Intune ドキュメントの手順に従います。Windows 10 デバイスの自動登録[を設定](/mem/intune/enrollment/quickstart-setup-auto-enrollment)します。

1. サード パーティ **製 MDM** への登録の場合は、[はい] または [ **いいえ** ] を切り替えます。
2. [はい] **を切**り替える場合は、デバイスの登録を承認されているサービス アカウントとパスワードまたは証明書の拇印を指定し、認証の種類を指定します。
3. MDM プロバイダーが必要な場合は、探索サービス、登録サービス、およびポリシー サービスの URL を入力します。

 詳細については、「MDM プロバイダーを[使用Surface Hub管理する」を参照してください。](manage-settings-with-mdm-for-surface-hub.md)

### <a name="add-applications"></a>アプリケーションの追加

> [!div class="mx-imgBorder"]
> ![アプリケーションの追加](images/sh-prov-apps.png)

プロビジョニング パッケージには、複数のユニバーサル Windows プラットフォーム (UWP) アプリをインストールできます。 詳細については、「アプリを使用して [PC をプロビジョニングする」を参照してください](/windows/configuration/provisioning-packages/provision-pcs-with-apps)。

> [!NOTE]
> このWindows構成デザイナーでは、クラシック Win32 アプリをプロビジョニング パッケージに追加することができますが、Surface Hub UWP アプリのみを受け入れる必要があります。 従来の Win32 アプリを含めると、プロビジョニングが失敗します。

### <a name="add-a-configuration-file"></a>構成ファイルの追加

このプロビジョニング パッケージに加えて、Surface Hub構成ファイルを使用して、デバイスのセットアップをより簡単に行えます。 Surface Hub構成ファイルには、Exchange、Microsoft Teams、または Skype for Business に接続するためのデバイス アカウントの一覧と、ワイヤレスプロジェクション用の "分名" が含まれる。

**構成ファイルをSurface Hubするには、次のSurface Hub使用します。**

1. [Microsoft Excel (または他の.csv エディター) を開き、.csvという名前SurfaceHubConfiguration.csv
2. 次の形式で、デバイス アカウントとユーザー名の一覧を入力します。

    ```
    <DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
    ```

    > [!NOTE]
    > 構成ファイルには、列ヘッダーを含めないでください。 アプリケーションに適用されるプロビジョニング パッケージに含Surface Hub、ファイルからデバイスのアカウントと親近感の名前を選択できます。 .csvファイルを作成するには、UPN アドレス形式 (rainier@contoso.com) またはダウンレベルログオン名形式 (contoso\rainier) を使用します。

- rainier@contoso.com,password,Rainier Surface Hub

3. ファイルをプロジェクト フォルダーに保存し、プロビジョニング パッケージを使用して USB キーにコピーします。

> [!NOTE]
> 構成ファイルは、最初の実行セットアップ時にのみ適用できます。

### <a name="password-protect-provisioning-package"></a>パスワード保護プロビジョニング パッケージ

パスワードを使用する場合は、プロビジョニング パッケージをデバイスに適用する度にパスワードを入力する必要があります。

### <a name="complete-provisioning-wizard"></a>完全なプロビジョニング ウィザード

共通の設定のみを構成する必要がある場合は****、[作成の完了] を選択し、[パッケージのビルド  >  ****[] セクションにスキップします](#build-your-package)。 または、[高度なプロビジョニング] に切り替えて設定の構成を続行します。

## <a name="use-advanced-provisioning"></a>高度なプロビジョニングの使用

> [!TIP]
> ウィザードを使用して共通設定のパッケージを作成した後、詳細エディターに切り替えて他の設定を追加します。<br><br> ![詳細エディターに切り替える](images/icd-simple-edit.png)

1. 前のセクションから続行する場合は、[**詳細エディターに**切り替える] を選択します。それ**以外の場合**は、[構成デザイナー] Windows開き、[高度なプロビジョニング]**を選択します**。<br>
  ![高度なプロビジョニングの使用](images/sh-prov-adv.png)

2. プロジェクトに名前を付け、[次へ] を **選択します**。
3. [共通 **] を選択Windows 10 Team、[** 次へ] を選択**し**、[完了] を**選択します**。<br>
     ![WCD の新しいプロジェクト](images/icd-new-project.png)

4. プロジェクトの [利用可能なカスタマイズ **] で、[** 共通チーム設定 **] を選択します**。<br>
     ![WCD 共通設定](images/icd-common-settings.png)

### <a name="add-a-certificate-to-your-package"></a>証明書をパッケージに追加する

プロビジョニング パッケージを使って、デバイスが Microsoft Exchange への認証に使う証明書をインストールすることができます。

> [!NOTE]
> 証明書をインストールできるのはデバイス (ローカル コンピューター) ストアのみで、ユーザー ストアにはインストールできません。 組織でユーザー ストアに証明書をインストールする必要がある場合は、Hub**** 設定 アプリを使用します&**セキュリティ**証明書  >  ****  >  **のインポート証明書を更新します**。
または  [**、MDM**](manage-settings-with-mdm-for-surface-hub.md) ポリシーを使用して、デバイス ストアまたはユーザー ストアに証明書を展開することもできます。

> [!TIP]
> **ClientCertificates**セクションは、プライベート キーを持つ .pfx ファイル用です。ルート CA 用の .cer ファイルは、[ルート証明書] セクションと **[CACertificates]** セクションの [中間 CA] に配置する必要があります。 ****

1. [**構成Windows利用可能**な  >  **カスタマイズ] で、[****ランタイム**設定  >  **証明書**  >  **クライアントCertificates] に移動します**。
2. CertificateName のラベルを **入力し、[** 追加] を **選択します**。
3. **[CertificatePassword]** を入力します。
4. **[CertificatePath]** で、証明書を探して選びます。
5. **[ExportCertificate]** を **[False]** に設定します。
6. **[KeyLocation]** で、**[ソフトウェアのみ]** を選びます。

### <a name="add-a-uwp-app-to-your-package"></a>パッケージに UWP アプリを追加する

UWP アプリをプロビジョニング パッケージに追加するには、アプリ パッケージ (.appx または .appxbundle ファイル) と依存関係ファイルが必要です。 ビジネス向け Microsoft Store からアプリを入手した場合は、*エンコードされていない*アプリのライセンスも必要です。 ビジネス向け Microsoft Store からこれらの項目をダウンロードする方法については、「[オフライン アプリの配布](/microsoft-store/distribute-offline-apps)」をご覧ください。

**UWP アプリを追加するには、次の方法を実行します。**

1. **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[UniversalAppInstall]** > **[DeviceContextApp]** の順に移動します。
2. アプリの **PackageFamilyName** を入力し、[追加] を **選択します**。 一貫性を保つために、アプリのパッケージ ファミリ名を使います。 ビジネス向け Microsoft Store からアプリを入手した場合は、アプリのライセンスからパッケージ ファミリ名がわかります。 テキスト エディターを使用してライセンス ファイルを開き、PFM タグ間の値を使用します。
3. **[ApplicationFile]** で、[**参照]** を選択してターゲット アプリ (.appx または .appxbundle) を検索して選択します。
4. **[DependencyAppxFiles] で、[****参照**] を選択して、アプリの依存関係を検索して追加します。 Surface Hub の場合、必要なのはこれらの依存関係の x64 バージョンだけです。

アプリをプロビジョニング パッケージからビジネス向け Microsoft Store場合は、プロビジョニング パッケージにアプリ ライセンスを追加する必要があります。

**アプリ ライセンスを追加するには、次の方法を実行します。**

1. アプリのライセンスのコピーを作成し、その名前を拡張子 **.ms-windows-store-license** を使うように変更します。 たとえば、"example.xml" の名前を "example.ms-windows-store-license" に変更します。
2. [Windowsデザイナー] で、[使用可能なカスタマイズ **]**  >  **ランタイム設定**  >  **UniversalAppInstall**  >  **DeviceContextAppLicense に移動します**。
3. **LicenseProductId を入力し、[** 追加] を**選択します**。 一貫性を保つのために、アプリのライセンスにあるアプリのライセンス ID を使います。 テキスト エディタでライセンス ファイルを開きます。 次に **、License タグ** で LicenseID 属性の **値を使用** します。
4. 新しい **[LicenseProductId]** ノードを選択します。 LicenseInstall **の**場合は、[ **参照]** を選択して、名前を変更したライセンス ファイル (example.ms windows-store-license) を検索して選択します。

### <a name="add-a-policy-to-your-package"></a>ポリシーをパッケージに追加する

Surface Hub は、[ポリシー構成サービス プロバイダー](/windows/client-management/mdm/policy-configuration-service-provider)のポリシーのサブセットをサポートします。 これらのポリシーの一部は、構成デザイナーで構成Windowsできます。

 **CSP ポリシー [を追加するには、次の手順を実行します](/windows/client-management/mdm/policies-in-policy-csp-supported-by-surface-hub)。**

1. [使用可能な**カスタマイズ] ランタイム**  >  **設定の**  >  **[ポリシー] に移動します**。
2. 管理するコンポーネントを選択し、必要に応じてポリシー設定を構成します。 たとえば、従業員がユーザーに対して InPrivate Web サイトの閲覧を使用**Surface Hub、AllowInPrivate**を選択し、[無効にする] を選択**します**。  

    > [!div class="mx-imgBorder"]
    > ![ポリシー設定の構成](images/sh-prov-policies.png)

### <a name="add-surface-hub-settings-to-your-package"></a>Surface Hub の設定をパッケージに追加する

[SurfaceHub 構成サービス プロバイダー](/windows/client-management/mdm/surfacehub-csp)から、設定をプロビジョニング パッケージに追加できます。

1. [利用可能な**カスタマイズ]**  >  **[共通のチーム エディション] 設定。**
1. 管理するコンポーネントを選択し、必要に応じてポリシー設定を構成します。
1. プロビジョニング パッケージの構成が完了したら、[ファイル保存]**を**  >  **選択します**。
1. プロジェクト ファイルに機密情報が含まれている可能性があるという警告を読み **、[OK] を選択します。**

### <a name="build-your-package"></a>パッケージをビルドする

プロビジョニング パッケージを作成する場合、プロジェクト ファイルとプロビジョニング パッケージ (.ppkg) ファイルに機密情報を含めることができます。 .ppkg ファイルは暗号化するかどうかを選べますが、プロジェクト ファイルは暗号化されません。  プロジェクト ファイルを安全な場所に保存するか、必要なくなった場合は削除します。

1. [**構成Windowsエクスポート**  >  **プロビジョニング パッケージ]**  >  **を開きます**。
2. 所有者 **を** **IT 管理者に変更します**。  
3. **[パッケージのバージョン]** の値を設定し、**[次へ]** を選択します。

> [!TIP]
> 所有者を IT 管理者に設定すると、パッケージ設定が適切な "優先順位プロパティ" を維持し、その後他のプロビジョニング パッケージが他のソースから適用された場合、Surface Hub に対して有効なままになります。

> [!TIP]
> 既存のパッケージを変更し、バージョン番号を変更して、以前に適用したパッケージを更新できます。

4. オプション: パッケージの暗号化とパッケージ署名の有効化を選択できます。

    1. [パッケージ **の暗号化] を** 選択し、パスワードを入力します。
    1. [**パッケージの参照に**  >  **署名] を**選択し、必要に応じて証明書を選択します。

    > [!IMPORTANT]
    > プロビジョニング パッケージに信頼できるプロビジョニング証明書を含めてお勧めします。 パッケージがデバイスに適用されると、証明書がシステム ストアに追加され、後続のパッケージをサイレント モードで適用できます。

5. [次 **へ] を** 選択して、出力場所を指定します。 既定では、Windows 構成デザイナーはプロジェクト フォルダーを出力先として使います。 または、[ **参照] を** 選択して既定の出力場所を変更します。 **[次へ]** を選択します。
6. [ **ビルド] を** 選択して、パッケージのビルドを開始します。 プロジェクト情報がビルド ページに表示されます。
7. ビルドに失敗した場合は、プロジェクト フォルダーへのリンクを含むエラー メッセージが表示されます。 ログを確認してエラーを診断し、パッケージの構築を再試行します。
8. ビルドが成功すると、プロビジョニング パッケージ、出力ディレクトリ、およびプロジェクト ディレクトリの名前が表示されます。 [ **完了] を** 選択してウィザードを閉じ、[カスタマイズ] ページに戻ります。
9. 出力  **場所を選択**  して、パッケージの場所に移動します。 .ppkg を空の USB フラッシュ ドライブにコピーします。

## <a name="apply-a-provisioning-package-to-surface-hub"></a>プロビジョニング パッケージを Surface Hub に適用する

プロビジョニング パッケージを Surface Hub に展開するためのオプションは 2 つあります。 [](#apply-a-provisioning-package-during-first-run)最初の実行ウィザードでは、証明書をインストールするプロビジョニング パッケージを適用するか、最初の実行プログラムが完了した後に、設定 を使用して設定、アプリ、および証明書を構成するプロビジョニング パッケージ[を適用できます](#apply-a-provisioning-package-using-settings-app)。

### <a name="apply-a-provisioning-package-during-first-run"></a>最初の実行時にプロビジョニング パッケージを適用する

> [!IMPORTANT]
> 最初の実行プログラムでは、プロビジョニング パッケージのみを使用して証明書をインストールできます。 **設定**アプリを使って、アプリをインストールし、その他の設定を適用します。

1. 最初に画面をSurface Hubすると、最初に実行されたプログラムに[**[こんにちは] ページが表示されます**](first-run-program-surface-hub.md)。 操作を続行する前に、設定が適切に構成されていることを確認してください。
2. .ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。 パッケージがドライブのルート ディレクトリにある場合は、初回実行プログラムによってそれが認識され、デバイスをセットアップするかどうかを確認するメッセージが表示されます。 **[セットアップ]** を選択します。
3. 次にプロビジョニング元を選択する画面が表示されます。 **[リムーバブル メディア]** を選んで **[次へ]** をタップします。
4. 適用するプロビジョニング パッケージ (*.ppkg) を選択し、[次へ] をタップ **します**。 最初の実行時にインストールできるパッケージは 1 つだけです。
5. 初回実行プログラムによって、プロビジョニング パッケージが適用される変更の概要が表示されます。 **[はい、追加する]** を選択します。
6. 構成ファイルが USB フラッシュ ドライブのルート ディレクトリに含まれる場合、**[構成を選択します]** が表示されます。 構成ファイルの最初のデバイス アカウントが、Surface Hub に適用されるアカウント情報の概要と共に表示されます。
7. [ **構成の選択] で**、適用するデバイス名を選択し、[次へ] を **選択します**。

プロビジョニング パッケージに含まれている設定がデバイスに適用され、OOBE が完了します。 デバイスの再起動後、USB フラッシュ ドライブを削除することができます。

### <a name="apply-a-provisioning-package-using-settings-app"></a>アプリを使用してプロビジョニング パッケージを設定する

1. .ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。
2. この**Surface Hubを開始**設定、プロンプトが表示されたら管理者資格情報を入力します。
3. **[Surface Hub]** > **[デバイス管理]** に移動します。 [**プロビジョニング パッケージ] で、[** プロビジョニング パッケージの追加と削除]**を選択します**  >  **。[パッケージの追加] を選択します**。
4. プロビジョニング パッケージを選択し、**[追加]** を選択します。  メッセージが表示されたら、管理者資格情報を再度入力します。
5. 適用する変更の概要が表示されます。 **[はい、追加する]** を選びます。

## <a name="learn-more"></a>詳細情報

- [構成Windowsダウンロード](https://www.microsoft.com/store/apps/9nblggh4tx22)
- [Windows 10 向けのプロビジョニング パッケージの作成](/windows/configuration/provisioning-packages/provisioning-create-package)
- [MDM プロバイダーを使用して Surface Hub を管理する](manage-settings-with-mdm-for-surface-hub.md)
