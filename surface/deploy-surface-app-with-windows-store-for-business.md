---
title: ビジネス向け Microsoft Store または教育向け Microsoft Store を使った Surface アプリの展開 (Surface)
description: ビジネス向け Microsoft Store または Education 向け Microsoft Store を使って Surface アプリを追加およびダウンロードする方法と、PowerShell と MDT を使って Surface アプリをインストールする方法について説明します。
keywords: surface アプリ, アプリ, 展開, カスタマイズ
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
ms.date: 1/15/2021
ms.openlocfilehash: 87e24bcfa1e2d4ab05d24a05b203fea92637d3f4
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271074"
---
# ビジネスおよび教育向け Microsoft Store を使った Surface アプリの展開

**適用対象**

- Surface Pro 7+
- Surface Laptop Go
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


Surface アプリは、次の Surface 固有の設定とオプションを制御できる軽量の Microsoft Store アプリです。 

* Surface デバイスの Windows ボタンを有効または無効にする
 

* Surface ペンの感度を調整する
 

* Surface ペンのボタンの操作をカスタマイズする
 

* Surface のオーディオ拡張機能を有効または無効にする
 

* デバイスのサポート ドキュメントと情報へのクイック アクセス

Windows Update を使うお客様は、通常、自動更新の一部として Surface アプリを受け取ります。 ただし、組織が Surface デバイスに展開するためのイメージを準備している場合は、個々のデバイスのユーザーに Microsoft Store またはビジネス向け Microsoft Store からアプリをダウンロードしてインストールする代わりに、イメージングおよび展開プロセスに Surface アプリ (以前の Surface Hub) を含める必要があります。 

> [!NOTE]
> この記事は、Surface Pro X には適用されません。詳細については、「Surface Pro X の展開、管理、サービス提供」[を参照してください](surface-pro-arm-app-management.md)。

## Surface アプリの概要

Surface アプリは [、Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。 ユーザーは Microsoft Store からダウンロードしてインストールできますが、組織でビジネス向け Microsoft Store を使用している場合は、ストアのインベントリにアプリを追加し、Windows 展開プロセスの一部としてアプリを含める必要があります。 これらのプロセスについては、この記事全体で説明します。 ビジネス向け Microsoft Store について詳しくは、Windows TechCenter のビジネス向け [Microsoft Store](https://docs.microsoft.com/microsoft-store/) をご覧ください。 

## ビジネス向け Microsoft Store アカウントに Surface アプリを追加する 

ユーザーが企業のビジネス向け Microsoft Store アカウントからアプリをインストールまたは展開する前に、目的のアプリを最初に利用可能にし、ビジネスユーザーにライセンスを割り当てなければならない。 

1. まだ作成していない場合は、ビジネス向け [Microsoft Store アカウントを作成します](https://www.microsoft.com/business-store)。 

2. ポータルにログオンします。 

3. オフライン ライセンスを有効にします。図 1 に示すように、[Manage->**Store settings]** をクリックし、[ストアでショッピングを行うユーザーにオフライン ライセンス アプリを表示する] チェック ボックスをオンにします。 **** ビジネス向け Microsoft Store アプリのライセンス モデルについて詳しくは、「ビジネスおよび教育向け Microsoft Store の [アプリ」をご覧ください](https://docs.microsoft.com/microsoft-store/)。

   > [!div class="mx-imgBorder"]
   > ![[オフライン ライセンス アプリを表示する] チェック ボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *図 1.  オフラインで使用するアプリを有効にする*

4. 次の手順に従って、ビジネス向け Microsoft Store アカウントに Surface アプリを追加します。

    * [ショップ **] メニューをクリック** します。
    
    * 検索ボックスに「Surface アプリ」 **と入力し**、検索アイコンをクリックします。
    
    * Surface アプリが検索結果に表示された後、アプリのアイコンをクリックします。
    
    * 図 2 に示すように、選択項目 ([ **オンライン** ] または [ **オフライン**] を選択) が表示されます。
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンス モードを選択し、アプリをインベントリに追加する](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *図 2.  オフライン ライセンス モードを選択し、アプリをインベントリに追加する*
    
    * [ **オフライン] を** クリックしてオフライン ライセンス モードを選択します。
    
    * [ **アプリの取得] を** クリックして、ビジネス向け Microsoft Store のインベントリにアプリを追加します。 図 3 に示すように、オフライン アプリを管理ツールを使用して展開したり、プライベート ストアの会社の在庫ページからダウンロードしたりできる点を確認するダイアログ ボックスが表示されます。
    
      > [!div class="mx-imgBorder"]
      > ![オフライン ライセンスのアプリ確認ウィンドウ図 ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *3.オフライン ライセンスのアプリの確認*
      
    * **[OK]** をクリックします。

## ビジネス向け Microsoft Store アカウントから Surface アプリをダウンロードする
オフライン モードでビジネス向け Microsoft Store アカウントにアプリを追加した後、アプリをダウンロードして展開共有に AppxBundle として追加できます。

1. ビジネス向け Microsoft Store アカウントにログオンします https://businessstore.microsoft.com 。

2. Click **Manage->Apps & software**. 会社のすべてのアプリの一覧が表示されます。この記事の「ビジネス向け [Microsoft Store](#add-surface-app-to-a-microsoft-store-for-business-account) アカウントに Surface アプリを追加する」セクションに追加した Surface アプリも含めて表示されます。

3. [**操作]** で省略記号 **(...)** をクリック**** し、Surface アプリでオフラインで使用するために [ダウンロード] をクリックします。

4. 図 4**に示**すように、選択したアプリで使用可能な選択項目から目的のプラットフォームとアーキテクチャのオプションを選択します。 ****

    > [!div class="mx-imgBorder"]
    > ![AppxBundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *図 4:  アプリの AppxBundle パッケージをダウンロードする*
    
5. [ダウンロード **] をクリックします**。 AppxBundle パッケージがダウンロードされます。 ダウンロードしたファイルのパスをメモしてください。これは、この記事で後で必要になります。

6. [エンコードされたライセンス **] または [** エンコードされていないライセンス] **オプションをクリック** します。 Microsoft Endpoint Configuration Manager のような管理ツールや、Windows 構成デザイナーを使用してプロビジョニング パッケージを作成する場合は、エンコードされたライセンス オプションを使用します。 展開イメージのサービスと管理 (DISM) を使用する場合、またはイメージングに基づく展開ソリューション (Microsoft Deployment Toolkit (MDT) を含む) を使用する場合は、[コード化されていないライセンス] オプションを選択します。

7. **[Generate]** (生成) をクリックして、アプリのライセンスを生成してダウンロードします。 ライセンス ファイルのパスは、この記事で後で必要になりますので、注意してください。

>[!NOTE]
>Surface アプリなど、オフラインで使うアプリをダウンロードすると、ページの下部に [必須のフレームワーク] というラベルのセクションが表示**されることがあります。** ターゲット コンピューターにはアプリを実行するためにフレームワークがインストールされている必要があります。そのため、アーキテクチャに必要な各フレームワーク (x86 または x64) についてダウンロード プロセスを繰り返し、後で説明する Windows 展開の一部として含める必要がある場合があります。

図 5 は、Surface アプリに必要なフレームワークを示しています。

> [!div class="mx-imgBorder"]
> ![Surface アプリに必要なフレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*図 5:  Surface アプリに必要なフレームワーク*

>[!NOTE]
>Surface アプリのバージョン番号と必要なフレームワークは、アプリの更新に応じて変更されます。 ビジネス向け Microsoft Store の Surface アプリと各フレームワークの最新バージョンを確認します。 ビジネス向け Microsoft Store で提供されている Surface アプリと推奨されるフレームワーク バージョンを常に使用します。 古いフレームワークや正しくないバージョンを使用すると、エラーやアプリケーションのクラッシュが発生する可能性があります。

Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。

1. **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 **** これにより、Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe がダウンロードされます。指定したフォルダーの Appx ファイル。

2. **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**の下にある [ダウンロード] ボタンをクリックします。 **** これにより、Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx ファイルが指定したフォルダーにダウンロードされます。

>[!NOTE]
>Surface デバイスでは、各フレームワークの 64 ビット (x64) バージョンだけが必要です。 Surface デバイスは、ネイティブの 64 ビット UEFI デバイスであり、32 ビット フレームワークを必要とする 32 ビット (x86) バージョンの Windows と互換性がありません。 

## PowerShell を使用して Surface アプリをコンピューターにインストールする
次の手順では、Surface アプリをコンピューターにプロビジョニングし、その後コンピューターで作成されたユーザー アカウントで利用できます。

1. この記事の「ビジネス向け [Microsoft Store](#download-surface-app-from-a-microsoft-store-for-business-account) アカウントから Surface アプリをダウンロードする方法」セクションで説明されている手順に従って、Surface アプリの AppxBundle とライセンス ファイルをダウンロードします。 

2. 管理者特権で PowerShell セッションを開始します。

    >[!NOTE]
    >管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可が付与されません。
    
3. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    ここで、ビジネス向け Microsoft Store アカウントから AppxBundle とライセンス ファイルをダウンロードした `<DownloadPath>` フォルダーです。

    たとえば、ファイルを c:\Temp にダウンロードした場合、実行するコマンドは次のようになります。
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. これで、Surface アプリは現在の Windows コンピューターで使用可能になります。 

   Surface アプリがプロビジョニングされたコンピューターで機能する前に、この記事で既に説明したフレームワークもプロビジョニングする必要があります。 これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した管理者特権の PowerShell セッションで次の手順を使用します。

5. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## MDT を使った Surface アプリのインストール
次の手順では、MDT を使って、展開時に Surface アプリのインストールを自動化します。 アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。 これは、Surface デバイスへの Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。これは、Windows イメージのクロス プラットフォームの互換性を低下さないのでです。

1. この記事で前述した [手順を使用して](#download-surface-app-from-a-microsoft-store-for-business-account)、Surface appxBundle とライセンス ファイルをダウンロードします。 

2. MDT Deployment Workbench の新しいアプリケーション ウィザードを使って、ダウンロードしたファイルを、ソース ファイルを含む新しい **アプリケーションとしてインポートします**。

3. 新しい**アプリケーション**ウィザードの [コマンドの詳細] ページ**** で、既定の作業ディレクトリを指定し、**コマンド**で AppxBundle のファイル名を次のように指定します。

   * コマンド:
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * 作業ディレクトリ: %DEPLOYROOT%\Applications\SurfaceApp

Surface アプリがターゲット コンピューターで機能するには、この記事で既に説明したフレームワークも必要です。 Surface アプリに必要なフレームワークを MDT にインポートし、依存関係として構成するには、次の手順を使用します。

1. この記事で前述した手順を使用して、フレームワーク ファイルをダウンロードします。 各フレームワークを個別のフォルダーに格納します。

2. MDT Deployment Workbench の新しいアプリケーション ウィザードを使って、ダウンロードしたファイルを、ソース ファイルを含む新しい **アプリケーションとしてインポートします**。

3. [コマンド **の詳細]** ページで、ダウンロードした各アプリケーションのファイル名を **Command** フィールドと既定の作業ディレクトリに入力します。

Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを使用します。

1. MDT Deployment Workbench で Surface アプリのプロパティを開きます。

2. [依存関係 **] タブをクリック** し、[追加] を **クリックします**。

3. 新しいアプリケーション ウィザードで指定した名前を使用して、各フレームワークのチェック ボックスをオンにします。

インポート後、Surface アプリは Windows 展開ウィザードの **[アプリケーション** ] ステップで選択できます。 次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。

1. MDT の Deployment Workbench で、展開タスク シーケンスを開きます。

2. 展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。

3. [Install **a single application] (単一のアプリケーション** のインストール) を選択し、インストールするアプリケーションとして Surface **App** **を指定します**。

Windows 展開へのアプリの組み込みについて詳しくは、「Microsoft Deployment Toolkit を使った [Windows 10 の展開」をご覧ください](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)。
