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
ms.openlocfilehash: 811feff1f0643ab0ba5d624c5f7d561ba5b0cd4d
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114715"
---
# 一般法人向けおよび教育機関向け Microsoft Store で Surface アプリを展開する

**適用対象**

- Surface のノート Pc の移動
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

Surface アプリは、 [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P)から無料でダウンロードできます。 ユーザーは Microsoft ストアからダウンロードしてインストールできますが、組織で一般法人向け Microsoft Store を使用している場合は、アプリをストアのインベントリに追加して、Windows 展開プロセスの一部としてアプリを含める必要があります。 これらのプロセスについては、この記事を通して説明します。 一般法人向け Microsoft Store の詳細については、「Windows TechCenter で一般 [法人向け Microsoft store](https://docs.microsoft.com/microsoft-store/) 」を参照してください。 

## Microsoft Store for Business アカウントに Surface アプリを追加する 

ユーザーが会社の Microsoft ストアのビジネスアカウントを使用してアプリをインストールまたは展開する前に、必要なアプリを最初に利用可能にして、ビジネスユーザーに対してライセンスを取得する必要があります。 

1. [ビジネスアカウント用に Microsoft Store](https://www.microsoft.com/business-store)をまだ作成していない場合は、作成します。 

2. ポータルにログオンします。 

3. [オフラインライセンスを有効にする]: [管理]、[ **>ストアの設定**] の順にクリックし、[ **オフラインライセンス** を持つアプリをストアに表示する] チェックボックスをオンにします (図1のように)。 一般法人向け Microsoft Store for Business アプリのライセンスモデルの詳細については、「一般 [法人向け Microsoft store のアプリ](https://docs.microsoft.com/microsoft-store/)」を参照してください。

   > [!div class="mx-imgBorder"]
   > ![[オフラインライセンスアプリの表示] チェックボックス](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *図 1.  オフラインでのアプリの使用を有効にする*

4. 次の手順に従って、ビジネスアカウントの Microsoft ストアに Surface アプリを追加します。

    * [ **ショップ** ] メニューをクリックします。
    
    * 検索ボックスに「 **Surface app**」と入力し、[検索] アイコンをクリックします。
    
    * Surface アプリが検索結果に表示されたら、アプリのアイコンをクリックします。
    
    * 図2に示すように、選択肢が表示されます ([ **オンライン** または **オフライン**] を選択します)。
    
      > [!div class="mx-imgBorder"]
      > ![オフラインライセンスモードを選択し、アプリをインベントリに追加します。](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *図 2.  オフラインライセンスモードを選択し、アプリをインベントリに追加します。*
    
    * [ **オフライン** ] をクリックして、オフラインライセンスモードを選択します。
    
    * [ **アプリの取得** ] をクリックして、アプリを Microsoft Store for Business のインベントリに追加します。 図3に示すように、管理ツールを使用してオフラインアプリを展開できること、またはプライベートストアの会社の在庫ページからダウンロードできることを確認するダイアログボックスが表示されます。
    
      > [!div class="mx-imgBorder"]
      > ![オフライン-ライセンス付与されたアプリ確認ウィンドウ ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *図3オフライン-ライセンス付与されたアプリの確認*
      
    * **[OK]** をクリックします。

## Microsoft Store for Business アカウントから Surface アプリをダウンロードする
オフラインモードで、ビジネスアカウント用の Microsoft ストアにアプリを追加した後で、アプリをダウンロードして展開共有に追加することができます。

1. のビジネスアカウント用の Microsoft ストアにログオン https://businessstore.microsoft.com します。

2. [ **Manage >app & software**] をクリックします。 この記事の「 [surface アプリを Microsoft Store For Business アカウントに追加](#add-surface-app-to-a-microsoft-store-for-business-account) する」で追加した surface アプリなど、すべての会社のアプリの一覧が表示されます。

3. [ **アクション**] で、省略記号 ([**...**]) をクリックし、[Surface アプリの **オフライン使用のためにダウンロード** ] をクリックします。

4. 図4に示すように、選択したアプリで利用可能な **プラットフォーム** と **アーキテクチャ** のオプションを選択します。

    > [!div class="mx-imgBorder"]
    > ![.Appxbundle パッケージの例](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *図 4:  アプリの .Appxbundle パッケージをダウンロードする*
    
5. [ **ダウンロード**] をクリックします。 .Appxbundle パッケージがダウンロードされます。 この記事で後述する必要があるため、ダウンロードしたファイルのパスをメモしておきます。

6. **エンコード**済みライセンスまたはエンコード済み**ライセンス**オプションをクリックします。 エンコードされたライセンスオプションは、Microsoft Endpoint Configuration Manager などの管理ツールで使用するか、Windows 構成デザイナーを使ってプロビジョニングパッケージを作成するときに使います。 展開イメージのサービスと管理 (DISM) またはイメージングに基づく展開ソリューション (Microsoft 展開ツールキット (MDT) を含む) を使用する場合は、[エンコードされていないライセンス] オプションを選択します。

7. [ **生成** ] をクリックして、アプリのライセンスを生成し、ダウンロードします。 この記事で後述する必要があるため、ライセンスファイルのパスをメモしておきます。

>[!NOTE]
>Surface アプリなど、オフラインで使用するためのアプリをダウンロードすると、ページの下部にある [ **必須フレームワーク**] というセクションが表示されることがあります。 ターゲットコンピューターには、アプリを実行するためのフレームワークがインストールされている必要があるため、アーキテクチャ (x86 または x64) に必要な各フレームワークのダウンロードプロセスを繰り返して、この記事の後半で説明する Windows の展開の一部として追加する必要がある場合もあります。

図5は、Surface アプリに必要なフレームワークを示しています。

> [!div class="mx-imgBorder"]
> ![Surface アプリの必須フレームワーク](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*図 5:  Surface アプリの必須フレームワーク*

>[!NOTE]
>Surface アプリのバージョン番号と必須のフレームワークは、アプリが更新されると変更されます。 最新バージョンの Surface アプリと、Microsoft Store for Business の各フレームワークについて確認します。 一般法人向け Microsoft Store によって提供されているように、常に Surface アプリと推奨される framework のバージョンを使用します。 古いフレームワークまたは不適切なバージョンを使用すると、エラーが発生したり、アプリケーションがクラッシュすることがあります。

Surface アプリに必要なフレームワークをダウンロードするには、次の手順を実行します。

1. [Microsoft 140.00] の下の [ **ダウンロード** ] ボタンをクリックします。 **23816 _x64__8wekyb3d8bbwe**。 これにより、140.00 _ 23816 _x64__8wekyb3d8bbwe のような内容がダウンロードされます。Appx ファイルを指定したフォルダーに保存します。

2. [ **23406 _x64__8wekyb3d8bbwe**] の下の [**ダウンロード**] ボタンをクリックします。。 これにより、指定したフォルダーに23406ファイルをダウンロードすることができます。この場合は、_x64__8wekyb3d8bbwe ファイルを指定します。

>[!NOTE]
>Surface デバイスには、64ビット (x64) バージョンの各フレームワークのみが必要です。 Surface デバイスは、ネイティブの64ビット UEFI デバイスであり、32ビットフレームワークを必要とする32ビット (x86) バージョンの Windows とは互換性がありません。 

## PowerShell を使用してコンピューターに Surface アプリをインストールする
次の手順では、Surface アプリをコンピューターに準備し、そのコンピューター上で作成されたユーザーアカウントで利用できるようにします。

1. この記事の「 [Microsoft Store For Business アカウントから surface アプリをダウンロードする方法](#download-surface-app-from-a-microsoft-store-for-business-account) 」に記載されている手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。 

2. 管理者特権で PowerShell セッションを開始します。

    >[!NOTE]
    >管理者として PowerShell を実行しない場合、セッションにはアプリをインストールするために必要なアクセス許可がありません。
    
3. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    [場所] `<DownloadPath>` は、Microsoft Store For Business アカウントから .appxbundle とライセンスファイルをダウンロードしたフォルダーです。

    たとえば、ファイルを c:\Temp にダウンロードした場合は、次のコマンドを実行します。
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. これで、Surface アプリは現在の Windows コンピューターで使用可能になります。 

   Surface アプリがプロビジョニングされているコンピューターで機能する前に、この記事で前に説明したフレームワークをプロビジョニングする必要もあります。 これらのフレームワークをプロビジョニングするには、Surface アプリのプロビジョニングに使用した管理者である PowerShell セッションで次の手順を使用します。

5. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. 管理者特権の PowerShell セッションで、次のコマンドをコピーして貼り付けます。

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## MDT を使用して Surface アプリをインストールする
次の手順では、MDT を使って、配置時に Surface アプリのインストールを自動化します。 アプリケーションは展開時に MDT によって自動的にプロビジョニングされるため、既存のイメージでこのプロセスを使用できます。 これは、windows イメージのクロスプラットフォームの互換性を低下させないため、surface デバイスに Windows 展開の一部として Surface アプリを展開する場合に推奨されるプロセスです。

1. [この記事で前に](#download-surface-app-from-a-microsoft-store-for-business-account)説明した手順を使用して、Surface app .appxbundle とライセンスファイルをダウンロードします。 

2. MDT 展開ワークベンチの新しいアプリケーションウィザードを使って、ダウンロードしたファイルを新しいアプリケーションとして **ソースファイルと**してインポートします。

3. 新しいアプリケーションウィザードの [ **コマンドの詳細** ] ページで、既定の **作業ディレクトリ** を指定します。 **コマンド** には、次のように、.appxbundle のファイル名を指定します。

   * コマンド
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * ワーキングディレクトリ:%DEPLOYROOT%\Applications\SurfaceApp

Surface アプリをターゲットコンピューターで機能させるには、この記事で前に説明したフレームワークも必要になります。 次の手順を使用して、Surface アプリに必要なフレームワークを MDT にインポートし、それを依存関係として構成します。

1. この記事の前半で説明した手順を使用して、フレームワークファイルをダウンロードします。 各フレームワークを個別のフォルダーに保存します。

2. MDT 展開ワークベンチの新しいアプリケーションウィザードを使って、ダウンロードしたファイルを新しいアプリケーションとして **ソースファイルと**してインポートします。

3. [ **コマンドの詳細** ] ページで、ダウンロードした各アプリケーションのファイル名を、 **コマンド** フィールドと既定の作業ディレクトリに入力します。

Surface アプリの依存関係としてフレームワークを構成するには、次のプロセスを実行します。

1. MDT 展開ワークベンチで Surface アプリのプロパティを開きます。

2. [ **依存関係** ] タブをクリックし、[ **追加**] をクリックします。

3. 新しいアプリケーションウィザードで指定した名前を使用して、各フレームワークのチェックボックスをオンにします。

インポート後、Surface アプリは、Windows 展開ウィザードの [ **アプリケーション** ] ステップで選択できるようになります。 次のプロセスに従って展開タスク シーケンスでアプリケーションを指定することで、アプリケーションを自動的にインストールすることもできます。

1. MDT の Deployment Workbench で、展開タスク シーケンスを開きます。

2. 展開の **[状態の復元]** セクションに、新しい **[アプリケーションのインストール]** タスクを追加します。

3. [**単一のアプリケーションをインストール**する] を選択し、**インストールするアプリケーション**として**Surface アプリ**を指定します。

Windows 展開にアプリを含める方法について詳しくは、「 [Microsoft 展開ツールキットを使用して windows 10 を展開](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)する」をご覧ください。
