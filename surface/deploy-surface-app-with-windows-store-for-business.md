---
title: Microsoft Store for Business または Microsoft ストア (教育機関向け) を使用した Surface アプリの展開 (Surface)
description: 教育機関向け Microsoft Store for Business または Microsoft ストアで Surface アプリを追加してダウンロードする方法、および PowerShell と MDT を使ったインストール Surface アプリについて説明します。
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
ms.openlocfilehash: e25e146de49110dca1fea797f9630d9fa2d953e3
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835125"
---
# 一般法人向けおよび教育機関向け Microsoft Store で Surface アプリを展開する

**適用対象**

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


Surface アプリは、次のようなさまざまなサーフェス固有の設定とオプションを管理するための、軽量の Microsoft Store アプリです。 

* Surface デバイスの Windows ボタンを有効または無効にする
 

* Surface ペンの感度を調整する
 

* Surface ペンのボタンの操作をカスタマイズする
 

* Surface のオーディオ拡張機能を有効または無効にする
 

* デバイスのサポートドキュメントと情報にすばやくアクセスする

Windows Update を使用しているユーザーは、通常、自動更新の一部として Surface アプリを受け取ります。 ただし、組織で Surface デバイスへの展開用のイメージを準備している場合は、個々のデバイスのユーザーに対して、Microsoft ストアまたは Microsoft Store からアプリをダウンロードしてインストールするのではなく、イメージと展開プロセスに Surface アプリ (旧称 Surface Hub) を含めることをお勧めします。 

> [!NOTE]
> この記事は Surface Pro X には適用されません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md) 」を参照してください。

## Surface アプリの概要

Surface アプリは、 [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。 ユーザーは Microsoft ストアからダウンロードしてインストールできますが、組織で一般法人向け Microsoft Store を使用している場合は、アプリをストアのインベントリに追加して、Windows 展開プロセスの一部としてアプリを含める必要があります。 これらのプロセスについては、この記事を通して説明します。 一般法人向け Microsoft Store の詳細については、「Windows TechCenter で一般[法人向け Microsoft store](https://docs.microsoft.com/microsoft-store/) 」を参照してください。 

## Microsoft Store for Business アカウントに Surface アプリを追加する 

ユーザーが会社の Microsoft ストアのビジネスアカウントを使用してアプリをインストールまたは展開する前に、必要なアプリを最初に利用可能にして、ビジネスユーザーに対してライセンスを取得する必要があります。 

1. [ビジネスアカウント用に Microsoft Store](https://www.microsoft.com/business-store)をまだ作成していない場合は、作成します。 

2. ポータルにログオンします。 

3. [オフラインライセンスを有効にする]: [管理]、[ **>ストアの設定**] の順にクリックし、[**オフラインライセンス**を持つアプリをストアに表示する] チェックボックスをオンにします (図1のように)。 一般法人向け Microsoft Store for Business アプリのライセンスモデルの詳細については、「一般[法人向け Microsoft store のアプリ](https://docs.microsoft.com/microsoft-store/)」を参照してください。<br/> <br/>
   ![[オフラインライセンスアプリの表示] チェックボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *図 1.  オフラインでのアプリの使用を有効にする*

4. 次の手順に従って、ビジネスアカウントの Microsoft ストアに Surface アプリを追加します。
    * [**ショップ**] メニューをクリックします。
    * 検索ボックスに「 **Surface app**」と入力し、[検索] アイコンをクリックします。
    * Surface アプリが検索結果に表示されたら、アプリのアイコンをクリックします。
    * 図2に示すように、選択肢が表示されます ([**オンライン**または**オフライン**] を選択します)。<br/><br/>
    
    ![オフラインライセンスモードを選択し、アプリをインベントリに追加します。](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")
    
    *図 2.  オフラインライセンスモードを選択し、アプリをインベントリに追加します。*
    
    * [**オフライン**] をクリックして、オフラインライセンスモードを選択します。
    * [**アプリの取得**] をクリックして、アプリを Microsoft Store for Business のインベントリに追加します。 図3に示すように、管理ツールを使用してオフラインアプリを展開できること、またはプライベートストアの会社の在庫ページからダウンロードできることを確認するダイアログボックスが表示されます。
    
    ![オフライン-ライセンス付与されたアプリ確認ウィンドウ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
    
    *図 3.  オフライン-ライセンス付与されたアプリの確認*
    * **[OK]** をクリックします。

## Microsoft Store for Business アカウントから Surface アプリをダウンロードする
オフラインモードで、ビジネスアカウント用の Microsoft ストアにアプリを追加した後で、アプリをダウンロードして展開共有に追加することができます。
1. のビジネスアカウント用の Microsoft ストアにログオン https://businessstore.microsoft.com します。
2. [ **Manage >app & software**] をクリックします。 この記事の「 [surface アプリを Microsoft Store For Business アカウントに追加](#add-surface-app-to-a-microsoft-store-for-business-account)する」で追加した surface アプリなど、すべての会社のアプリの一覧が表示されます。
3. [**アクション**] で、省略記号 ([**...**]) をクリックし、[Surface アプリの**オフライン使用のためにダウンロード**] をクリックします。
4. 図4に示すように、選択したアプリで利用可能な**プラットフォーム**と**アーキテクチャ**のオプションを選択します。

    ![.Appxbundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")

    *図 4:  アプリの .Appxbundle パッケージをダウンロードする*
5. [**ダウンロード**] をクリックします。 .Appxbundle パッケージがダウンロードされます。 この記事で後述する必要があるため、ダウンロードしたファイルのパスをメモしておきます。
6. **エンコード**済みライセンスまたはエンコード済み**ライセンス**オプションをクリックします。 エンコードされたライセンスオプションは、Microsoft Endpoint Configuration Manager などの管理ツールで使用するか、Windows 構成デザイナーを使ってプロビジョニングパッケージを作成するときに使います。 展開イメージのサービスと管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft 展開ツールキット (MDT) を含む) を使用する場合は、[エンコードされていないライセンス] オプションを選択します。
7. [**生成**] をクリックして、アプリのライセンスを生成し、ダウンロードします。 この記事で後述する必要があるため、ライセンスファイルのパスをメモしておきます。

>[!NOTE]
>Surface アプリなど、オフラインで使用するためのアプリをダウンロードすると、ページの下部にある [**必須フレームワーク**] というセクションが表示されることがあります。 ターゲットコンピューターには、アプリを実行するためのフレームワークがインストールされている必要があるため、アーキテクチャ (x86 または x64) に必要な各フレームワークのダウンロードプロセスを繰り返して、この記事の後半で説明する Windows の展開の一部として追加する必要がある場合もあります。

図5は、Surface アプリに必要なフレームワークを示しています。

![Surface アプリの必須フレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")

*図 5:  Surface アプリの必須フレームワーク*

>[!NOTE]
>Surface アプリのバージョン番号と必須のフレームワークは、アプリが更新されると変更されます。 最新バージョンの Surface アプリと、Microsoft Store for Business の各フレームワークについて確認します。 一般法人向け Microsoft Store によって提供されているように、常に Surface アプリと推奨される framework のバージョンを使用します。 古いフレームワークまたは不適切なバージョンを使用すると、エラーが発生したり、アプリケーションがクラッシュすることがあります。

Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。
1. [ **140.00 _ 0_x64__8wekyb3d8bbwe 14.0.23816**] の下の [**ダウンロード**] ボタンをクリックします。 これにより、140.00 _ 14.0.23816 0_x64__8wekyb3d8bbwe がダウンロードされます。Appx ファイルを指定したフォルダーに保存します。
2. [ **0_x64__8wekyb3d8bbwe 1.1.23406**] の下の [**ダウンロード**] ボタンをクリックします。 これにより、指定したフォルダーに1.1.23406 ファイルの0_x64__8wekyb3d8bbwe がダウンロードされます。

>[!NOTE]
>Surface デバイスには、64ビット (x64) バージョンの各フレームワークのみが必要です。 Surface デバイスは、ネイティブの64ビット UEFI デバイスであり、32ビットフレームワークを必要とする32ビット (x86) バージョンの Windows とは互換性がありません。 

## PowerShell を使用してコンピューターに Surface アプリをインストールする
次の手順では、Surface アプリをコンピューターに準備し、そのコンピューター上で作成されたユーザーアカウントで利用できるようにします。
1. この記事の「 [Microsoft Store For Business アカウントから surface アプリをダウンロードする方法](#download-surface-app-from-a-microsoft-store-for-business-account)」に記載されている手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。 
2. 管理者特権で PowerShell セッションを開始します。

    >[!NOTE]
    >管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可がありません。
    
3. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。
    ```
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    [場所] `<DownloadPath>` は、Microsoft Store For Business アカウントから .appxbundle とライセンスファイルをダウンロードしたフォルダーです。

    たとえば、ファイルを c:\Temp にダウンロードした場合は、次のコマンドを実行します。
    ````
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. The Surface app will now be available on your current Windows computer. 

Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article. To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.

5. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
6. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## Install Surface app with MDT
The following procedure uses MDT to automate installation of the Surface app at the time of deployment. The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images. This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.
1. Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file. 
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:

   * Command:
     ```
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
   * Working Directory: %DEPLOYROOT%\Applications\SurfaceApp

For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article. Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.
1. Using the procedure described earlier in this article, download the framework files. Store each framework in a separate folder.
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.

To configure the frameworks as dependencies of the Surface app, use this process:
1. Open the properties of the Surface app in the MDT Deployment Workbench.
2. Click the **Dependencies** tab, and then click **Add**.
3. Select the check box for each framework using the name you provided in the New Application Wizard.

After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard. You can also install the application automatically by specifying the application in the deployment task sequence by following this process:
1. Open your deployment task sequence in the MDT Deployment Workbench.
2. Add a new **Install Application** task in the **State Restore** section of deployment.
3. Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.

For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).
