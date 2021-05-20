---
title: Surface アプリを展開するには、ビジネス向け Microsoft Storeまたは教育機関向け Microsoft Storeを使用します (Surface)
description: PowerShell と MDT を使用して Surface アプリビジネス向け Microsoft Storeまたは教育機関向け Microsoft Store Surface アプリをインストールする方法について説明します。
keywords: surface アプリ、アプリ、展開、カスタマイズ
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, store
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.date: 4/16/2021
ms.openlocfilehash: c7a882859339ff3d7feeb685c62672bc57c301ec
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576527"
---
# <a name="deploy-surface-app-with-microsoft-store-for-business-and-education"></a>アプリと教育を使用ビジネス向け Microsoft Store Surface アプリを展開する

**適用対象**

- Surface Laptop 4
- Surface Pro 7+
- Surface LaptopGo
- Surface Pro 7
- Surface Laptop 3
- Surface Pro 6
- Surface Laptop 2
- Surface Go
- Surface Go LTE
- Surface Book 2
- Surface Pro LTE Advanced (モデル 1807)
- Surface Pro (モデル 1796)
- Surface Laptop
- Surface Studio
- Surface Studio 2
- Surface Book
- Surface Pro 4
- Surface 3 LTE
- Surface 3
- Surface Pro 3


Surface アプリは、次Microsoft Store Surface 固有の設定とオプションを制御できる軽量なアプリです。 

* Surface デバイスの Windows ボタンを有効または無効にする
 

* Surface ペンの感度を調整する
 

* Surface ペンのボタンの操作をカスタマイズする
 

* Surface のオーディオ拡張機能を有効または無効にする
 

* デバイスのサポート ドキュメントと情報へのクイック アクセス

更新プログラムをWindowsユーザーは、通常、自動更新の一部として Surface アプリを受け取ります。 ただし、組織が Surface デバイスへの展開用にイメージを準備している場合は、個々のデバイスのユーザーが Microsoft Store または ビジネス向け Microsoft Store からアプリをダウンロードしてインストールする必要が生じなくても、Surface アプリ (以前は Surface Hub) をイメージングおよび展開プロセスに含める必要があります。 

> [!NOTE]
> この記事は、X のSurface Proされません。詳細については、「X の展開、管理、およびサービス[」をSurface Proしてください。](surface-pro-arm-app-management.md)

## <a name="surface-app-overview"></a>Surface アプリの概要

Surface アプリは、アプリから無料でダウンロード[Microsoft Store。](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P) ユーザーは Microsoft Store からダウンロードしてインストールできますが、組織で代わりに ビジネス向け Microsoft Store を使用している場合は、ストアのインベントリに追加し、Windows 展開プロセスの一部としてアプリを含める必要があります。 これらのプロセスについては、この記事で説明します。 このサイトの詳細についてはビジネス向け Microsoft Store [TechCenter](https://docs.microsoft.com/microsoft-store/)のビジネス向け Microsoft StoreをWindowsしてください。 

## <a name="add-surface-app-to-a-microsoft-store-for-business-account"></a>Surface アプリをアカウントにビジネス向け Microsoft Storeする 

ユーザーが会社の ビジネス向け Microsoft Store アカウントからアプリをインストールまたは展開する前に、目的のアプリを最初に使用可能にし、ビジネスのユーザーにライセンスを取得する必要があります。 

1. まだ作成していない場合は、アカウントを作成ビジネス向け Microsoft Store[します](https://www.microsoft.com/business-store)。 

2. ポータルにログオンします。 

3. オフライン ライセンスを有効にする: **[Manage->ストア**の設定]**** をクリックし、図 1 に示すように、[ストアで購入するユーザーにオフライン ライセンス アプリを表示する] チェック ボックスをオンにします。 アプリ のライセンス モデルのビジネス向け Microsoft Store詳細については、「アプリ」および[「Education ビジネス向け Microsoft Store」を参照してください](https://docs.microsoft.com/microsoft-store/)。

   > [!div class="mx-imgBorder"]
   > ![[オフライン ライセンス アプリを表示する] チェック ボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *図 1. オフラインで使用するアプリを有効にする*

4. 次の手順に従って、ビジネス向け Microsoft Storeに Surface アプリを追加します。

    * [ショップ] **メニューをクリック** します。
    
    * 検索ボックスに **「Surface app」と入力**し、検索アイコンをクリックします。
    
    * Surface アプリが検索結果に表示された後、アプリのアイコンをクリックします。
    
    * 図 2 に示すように、選択項目 **([オンライン** ] または [ **オフライン**] を選択) が表示されます。
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンス モードを選択し、アプリをインベントリに追加する](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *図 2. オフライン ライセンス モードを選択し、アプリをインベントリに追加する*
    
    * [ **オフライン] を** クリックしてオフライン ライセンス モードを選択します。
    
    * [**アプリの取得] を**クリックして、アプリをインベントリにビジネス向け Microsoft Storeします。 図 3 に示すように、管理ツールを使用してオフライン アプリを展開するか、プライベート ストアの会社の在庫ページからダウンロードできると確認するダイアログ ボックスが表示されます。
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンスのアプリ確認ウィンドウ図 ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *3.オフライン ライセンスのアプリの確認*
      
    * **[OK]** をクリックします。

## <a name="download-surface-app-from-a-microsoft-store-for-business-account"></a>Surface アプリをアカウントからビジネス向け Microsoft Storeする
オフライン モードでアプリを ビジネス向け Microsoft Store アカウントに追加した後、アプリを AppxBundle として展開共有にダウンロードして追加できます。

1. でアカウントにビジネス向け Microsoft Storeします https://businessstore.microsoft.com 。

2. [ **アプリの管理] >ソフトウェア&クリックします**。 この記事の [Surface アプリを ビジネス向け Microsoft Store アカウントに追加した Surface アプリを含む、会社[のすべてのアプリ](#add-surface-app-to-a-microsoft-store-for-business-account)の一覧が表示されます。

3. [ **アクション]** で、省略記号 (**...) を**クリックし、[Surface アプリのオフラインで使用するために **ダウンロード]** をクリックします。

4. 図 4**に示**すように、選択したアプリで使用可能な選択項目から、目的のプラットフォームとアーキテクチャのオプションを選択します。 ****

    > [!div class="mx-imgBorder"]
    > ![AppxBundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *図 4:  アプリの AppxBundle パッケージをダウンロードする*
    
5. [ダウンロード **] をクリックします**。 AppxBundle パッケージがダウンロードされます。 この記事の後半で必要になりますので、ダウンロードしたファイルのパスに注意してください。

6. [エンコードされた**ライセンス] または [****コード化されていないライセンス] オプションをクリック**します。 [エンコードされたライセンス] オプションは、Microsoft Endpoint Configuration Managerのような管理ツールを使用するか、Windows構成デザイナーを使用してプロビジョニング パッケージを作成する場合に使用します。 展開イメージ サービスおよび管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft Deployment Toolkit (MDT) を使用する場合は、[コード化されていないライセンス] オプションを選択します。

7. [ **生成] を** クリックして、アプリのライセンスを生成してダウンロードします。 この記事の後半で必要になりますので、ライセンス ファイルのパスに注意してください。

>[!NOTE]
>Surface アプリなどのオフラインで使用するアプリをダウンロードすると、[必須フレームワーク] というラベルが付いたページの下部にセクション **が表示されることがあります**。 対象のコンピューターには、アプリを実行するフレームワークがインストールされている必要があります。そのため、アーキテクチャに必要な各フレームワーク (x86 または x64) のダウンロード プロセスを繰り返し、この記事で後で説明する Windows 展開の一部として含める必要があります。

図 5 は、Surface アプリに必要なフレームワークを示しています。

> [!div class="mx-imgBorder"]
> ![Surface アプリに必要なフレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*図 5:  Surface アプリに必要なフレームワーク*

>[!NOTE]
>Surface アプリと必要なフレームワークのバージョン番号は、アプリの更新に応じて変更されます。 Surface アプリと各フレームワークの最新バージョンを確認ビジネス向け Microsoft Store。 常に Surface アプリと推奨されるフレームワーク バージョンを使用します (このバージョンビジネス向け Microsoft Store。 古いフレームワークや正しくないバージョンを使用すると、エラーやアプリケーションがクラッシュする可能性があります。

Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。

1. **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 **** これにより、Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe がダウンロードされます。指定したフォルダーへの Appx ファイル。

2. [ダウンロード **] ボタン** をクリック **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**. これにより、Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx ファイルが指定したフォルダーにダウンロードされます。

>[!NOTE]
>Surface デバイスには、各フレームワークの 64 ビット (x64) バージョンだけが必要です。 Surface デバイスはネイティブの 64 ビット UEFI デバイスであり、32 ビット フレームワークを必要とする 32 ビット (x86) バージョンの Windows と互換性がありません。 

## <a name="install-surface-app-on-your-computer-with-powershell"></a>PowerShell を使用して Surface アプリをコンピューターにインストールする
次の手順では、Surface アプリをコンピューターにプロビジョニングし、その後コンピューターで作成されたユーザー アカウントで使用できます。

1. この記事の「ビジネス向け Microsoft Store アカウントから[Surface](#download-surface-app-from-a-microsoft-store-for-business-account)アプリをダウンロードする方法」セクションで説明されている手順を使用して、Surface アプリ AppxBundle とライセンス ファイルをダウンロードします。 

2. 管理者特権で PowerShell セッションを開始します。

    >[!NOTE]
    >PowerShell を管理者として実行しない場合、セッションにはアプリのインストールに必要なアクセス許可はありません。
    
3. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    AppxBundle とライセンス ファイルをアカウントからダウンロードした `<DownloadPath>` フォルダーはビジネス向け Microsoft Storeです。

    たとえば、ファイルを c:\Temp にダウンロードした場合、実行するコマンドは次のようになります。
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. これで、Surface アプリは現在の Windows コンピューターで使用可能になります。 

   Surface アプリがプロビジョニングされているコンピューターで機能する前に、この記事で前述したフレームワークも準備する必要があります。 これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した昇格された PowerShell セッションで次の手順を使用します。

5. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <a name="install-surface-app-with-mdt"></a>MDT を使用して Surface アプリをインストールする
次の手順では、MDT を使用して、展開時に Surface アプリのインストールを自動化します。 アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。 これは、Surface デバイスへの Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。これは、Windows イメージのクロス プラットフォームの互換性を低下さないのでです。

1. この記事で前述 [した手順を使用して](#download-surface-app-from-a-microsoft-store-for-business-account)、Surface アプリ AppxBundle とライセンス ファイルをダウンロードします。 

2. MDT 展開ワークベンチで新しいアプリケーション ウィザードを使用して、ダウンロードしたファイルを新しいアプリケーションとしてインポートし、ソース ファイル **を使用します**。

3. 新しい**アプリケーション ウィザードの**[コマンドの詳細] ページ**** で、既定の作業ディレクトリを指定し **、Command**に AppxBundle のファイル名を次のように指定します。

   * コマンド:
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * 作業ディレクトリ: %DEPLOYROOT%\Applications\SurfaceApp

Surface アプリがターゲット コンピューターで機能するには、この記事で前述したフレームワークも必要です。 Surface アプリに必要なフレームワークを MDT にインポートし、依存関係として構成するには、次の手順を使用します。

1. この記事で前述した手順を使用して、フレームワーク ファイルをダウンロードします。 各フレームワークを個別のフォルダーに格納します。

2. MDT 展開ワークベンチで新しいアプリケーション ウィザードを使用して、ダウンロードしたファイルを新しいアプリケーションとしてインポートし、ソース ファイル **を使用します**。

3. [コマンド**の詳細]** ページで、ダウンロードした各アプリケーションのファイル名を****[コマンド] フィールドと既定の作業ディレクトリに入力します。

Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを使用します。

1. MDT 展開ワークベンチで Surface アプリのプロパティを開きます。

2. [依存関係] **タブをクリック** し、[追加] を **クリックします**。

3. 新しいアプリケーション ウィザードで指定した名前を使用して、各フレームワークのチェック ボックスをオンにします。

インポート後、Surface アプリは、展開ウィザードの **[アプリケーション**] Windows選択できます。 次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。

1. MDT の Deployment Workbench で、展開タスク シーケンスを開きます。

2. 展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。

3. [ **単一のアプリケーションをインストールする** ] を選択し、 **インストール** する **アプリケーションとして Surface App を指定します**。

アプリを展開環境に含Windows詳細については、「Deploy Windows 10 with [the Microsoft Deployment Toolkit」 を参照してください](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)。
