---
title: Microsoft Surface Hub へのアプリのインストール
description: 管理者は、Microsoft ストアまたはビジネス向け Microsoft ストアからアプリをインストールできます。
ms.assetid: 3885CB45-D496-4424-8533-C9E3D0EDFD94
ms.reviewer: ''
manager: laurawi
keywords: アプリのインストール, Microsoft ストア, ビジネス向け Microsoft ストア
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/23/2018
ms.localizationpriority: medium
audience: ITPro
ms.openlocfilehash: 462b76451bd12547d1c1560054a51bb88c218f96
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835781"
---
# Microsoft Surface Hub へのアプリのインストール

チームまたは組織のニーズに合わせて、Surface Hub に追加のアプリをインストールできます。 アプリの開発やテストを行うか、リリースされたアプリを展開するかによって、アプリをインストールするための方法は異なります。 このトピックでは、それぞれのシナリオ向けにアプリをインストールする方法について説明します。

Surface Hub でのアプリについては、次のような注意点があります。
- Surface Hub で実行できるのは、[ユニバーサル Windows プラットフォーム (UWP) アプリ](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp)のみです。 [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) を使用して作成されたアプリは、Surface Hub では動作しません。
- アプリは、[ユニバーサル デバイス ファミリ](https://msdn.microsoft.com/library/windows/apps/dn894631)または Windows チーム デバイス ファミリに対応している必要があります。
- Surface Hub は、一般[法人向け Microsoft Store](https://businessstore.microsoft.com/store)の[オフラインライセンスアプリ](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)のみをサポートしています。
- 既定では、アプリをインストールするには、アプリにストアの署名が必要です。 テストおよび開発時には、開発者モードでデバイスを配置することによって、開発者が署名した UWP アプリの実行を選択することもできます。
- Microsoft ストアにアプリを提出する場合、Surface Hub でアプリを実行できるようにするために、開発者はデバイスファミリの可用性と組織のライセンスオプションを設定する必要があります。
- Surface Hub にアプリをインストールするには、管理者の資格情報が必要です。 このデバイスは、会議室などの共同スペースで使用するよう設計されているため、ユーザーが Microsoft ストアにアクセスし、アプリをダウンロードしてインストールすることはできません。


## アプリを開発およびテストする
独自のアプリの開発時に Surface Hub 上のアプリをテストするためのオプションはいくつかあります。

### 開発者モード
既定では、Surface Hub は、Microsoft ストアに公開され、Microsoft ストアによって署名された UWP アプリのみを実行できます。 Microsoft ストアに提出するアプリは、[アプリの認定プロセス](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process)の一環として、セキュリティとコンプライアンスのテストに合格している必要があります。これにより、Surface Hub を悪意のあるアプリから保護できます。
 
開発者モードを有効にすると、開発者が署名した UWP アプリをインストールすることもできます。
 
> [!IMPORTANT]
> 開発者モードを有効にした後、これを無効にするには、Surface Hub をリセットする必要があります。 デバイスをリセットすると、すべてのローカル ユーザーのファイルと構成が削除され、Windows が再インストールされます。

**開発者モードを有効にするには** 
1. Surface Hub から、**[設定]** を開きます。
2. メッセージが表示されたら、デバイスの管理者資格情報を入力します。
3. **[更新プログラムとセキュリティ]** > **[開発者向け]** の順に移動します。
4. **[開発者モード]** を選択し、警告メッセージに同意します。

### Visual Studio
開発中に、Surface Hub でアプリをテストする最も簡単な方法は、Visual Studio を使用する方法です。 Visual Studio のリモート デバッグ機能は、広く展開する前に、アプリで問題を見つけるのに役立ちます。 詳しくは、「[Visual Studio を使った Surface Hub アプリのテスト](https://msdn.microsoft.com/windows/uwp/debug-test-perf/test-surface-hub-apps-using-visual-studio)」をご覧ください。

### プロビジョニング パッケージ
Visual Studio を使用して、テスト証明書で署名された、UWP アプリ用の[アプリ パッケージを作成](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx)します。 Windows イメージングおよび構成デザイナー (ICD) を使用して、アプリ パッケージを含むプロビジョニング パッケージを作成します。 詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。


## Microsoft ストアにアプリを提出する
アプリのリリースの準備ができたら、開発者は、Microsoft ストアにアプリを提出し、公開する必要があります。 詳しくは、「[Windows アプリの公開](https://developer.microsoft.com/store/publish-apps)」をご覧ください。

アプリの提出時に、開発者は、アプリが Surface Hub で確実に実行できるように、**[デバイス ファミリの利用可否]** オプションと **[組織のライセンス]** オプションを設定する必要があります。

**デバイス ファミリの利用可否を設定するには**  
1. [Windows デベロッパー センター](https://developer.microsoft.com)のアプリの申請ページに移動します。
2. **[パッケージ]** を選択します。
3. **[デバイス ファミリの利用可否]** で、次のオプションを選択します。
    
    - **Windows 10 Team**
    - **[このアプリを将来のデバイス ファミリで使用できるようにするかどうかをマイクロソフトが決定できる]**
  
![[デバイス ファミリの利用可否] ページ (Microsoft ストア アプリの申請プロセスの一部) を示す画像。](images/device-family.png)  
    
詳しくは、「[デバイス ファミリの利用可否](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages#device-family-availability)」をご覧ください。

**組織のライセンスを設定するには**
1. [Windows デベロッパー センター](https://developer.microsoft.com)のアプリの申請ページに移動します。
2. **[価格と使用可能状況]** を選択します。
3. [組織のライセンス] の **[組織による未接続状態 (オフライン) でのライセンスの購入を許可する]** を選択します。

![[組織のライセンス] ページ (Microsoft ストア アプリの申請プロセスの一部) を示す画像。](images/sh-org-licensing.png)

> [!NOTE]
> **[ストアで管理される (オンライン) ボリューム ライセンスと配布に基づいて組織がこのアプリを購入できるようにする]** チェック ボックスは既定でオンになっています。

> [!NOTE]
> 開発者は、基幹業務アプリを企業に直接公開することもできます。アプリをストアで一般公開する必要はありません。 詳しくは、「[LOB アプリの企業への配布](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises)」をご覧ください。

詳しくは、「[組織のライセンス オプション](https://msdn.microsoft.com/windows/uwp/publish/organizational-licensing)」をご覧ください。


## リリースされたアプリを展開する

いくつかのデバイスでアプリを評価するか、または組織に広くアプリを展開するかに応じて、Microsoft ストアにリリースされているアプリをインストールする方法はいくつかあります。

リリースされたアプリをインストールするには、次の手順を実行します。
- Microsoft ストア アプリを使ってアプリをダウンロードする、または
- ビジネス向け Microsoft ストアからアプリ パッケージをダウンロードし、プロビジョニング パッケージまたはサポートされている MDM プロバイダーを使用して配布する。

### Microsoft ストア アプリ
Microsoft ストアにリリースされたアプリを評価するには、Surface Hub で Microsoft ストア アプリを使ってアプリを参照し、ダウンロードします。

> [!NOTE]
> Microsoft ストア アプリを使用する方法は、組織にアプリを大規模に展開する場合はお勧めできません。
> - アプリをダウンロードするには、Microsoft アカウントまたは組織のアカウントを使って Microsoft ストア アプリにサインインする必要があります。 ただし、1 つのアカウントで接続できるのは最大 10 台のデバイスのみです。 10 台以上の Surface Hub がある場合は、複数のアカウントを作成するか、アプリのインストールが終了するたびにアカウントからデバイスを削除する必要があります。
> - アプリをインストールするには、自分が所有する各 Surface Hub で手動で Microsoft ストア アプリにサインインする必要があります。

**Surface Hub で Microsoft ストアを参照するには** 
1. Surface Hub から、**[設定]** を起動します。
2. メッセージが表示されたら、デバイスの管理者資格情報を入力します。
3. **[このデバイス]** > **[アプリと機能]** に移動します。
4. **[ストアを開く]** を選択します。

### ビジネス向け Microsoft ストアからアプリ パッケージをダウンロードする
必要なアプリ パッケージをダウンロードして Surface Hub にアプリをインストールするには、[ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)にアクセスします。 ビジネス向けストアは、Surface Hub を含め、組織内の Windows 10デバイス用のアプリの検索、取得、管理を行うことができる場所です。
 
> [!NOTE]
> 現在、Surface Hub は、ビジネス向けストアで利用可能なオフライン ライセンスのアプリのみをサポートしています。 アプリの開発者は、アプリを提出するときに、オフライン ライセンスを利用できるかどうかを設定します。

必要なアプリを検索して入手し、ダウンロードします。
- オフライン ライセンスのアプリ パッケージ (.appx または .appxbundle)
- *エンコードされていない*ライセンス ファイル (プロビジョニング パッケージを使ってアプリをインストールする場合)
- *エンコード*されたライセンス ファイル (MDM を使ってアプリを配布する場合)
- 必要な依存関係ファイル

詳しくは、[オフライン ライセンス アプリのダウンロードに関するページ](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)をご覧ください。

### プロビジョニング パッケージ
プロビジョニング パッケージを使って、数台の Surface Hub に、ビジネス向けストアからダウンロードしたオフライン ライセンス アプリを手動でインストールできます。 Windows イメージングおよび構成デザイナー (ICD) を使って、ビジネス向けストアからダウンロードしたアプリ パッケージと*エンコードされていない*ライセンス ファイルを含むプロビジョニング パッケージを作成します。 詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。

### サポートされる MDM プロバイダー
組織内の多くの Surface Hub にアプリを展開するには、サポートされているMDMプロバイダーを使用します。 次の表は、オフライン ライセンスのアプリ パッケージの展開をサポートする MDM プロバイダーを示しています。

| MDM プロバイダー                | オフライン ライセンスのアプリ パッケージのサポート |
|-----------------------------|----------------------------------------|
| Configuration Manager を使用したオンプレミス MDM (バージョン1602以降) | あり |
|
| サードパーティの MDM プロバイダー    | MDM プロバイダーがオフライン ライセンスのアプリ パッケージの展開をサポートしていることを確認してください。 |

**Microsoft Endpoint Configuration Manager を使用してリモートでアプリを展開するには**

> [!NOTE]
> これらの手順は、Microsoft Endpoint Configuration Manager の現在の分岐に基づいています。

1. Surface Hub を Configuration Manager に登録します。 詳しくは、「[MDM への Surface Hub の登録](manage-settings-with-mdm-for-surface-hub.md#enroll-into-mdm)」をご覧ください。
2. オフライン ライセンスのアプリ パッケージ、*エンコードされた*ライセンス ファイル、必要な依存関係ファイルを、ビジネス向けストアからダウンロードします。 詳しくは、[オフライン ライセンス アプリのダウンロードに関するページ](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)をご覧ください。 ネットワーク共有上の同じフォルダーにダウンロードしたファイルを配置します。
3. Configuration Manager コンソールの **[ソフトウェア ライブラリ]** ワークスペースで、**[概要]** > **[アプリケーション管理]** > **[アプリケーション]** の順にクリックします。
4. **[ホーム]** タブの **[作成]** グループで、**[アプリケーションの作成]** をクリックします。
5. **アプリケーションの作成ウィザード**の **[全般]** ページで、**[このアプリケーションの情報をインストール ファイルから自動的に検出する]** チェック ボックスをオンにします。
6. **[種類]** ドロップダウン リストで、**[Windows アプリ パッケージ (\*.appx、\*.appxbundle)]** を選択します。
7. **[場所]** フィールドで、ビジネス向けストアからダウンロードしたオフライン ライセンスのアプリ パッケージの UNC パスを、\\server\share\\filename の形式で指定します。 または、**[参照]** をクリックしてアプリ パッケージを参照します。
8. **[情報のインポート]** ページで、インポートされた情報を確認し、**[次へ]** をクリックします。 必要に応じて、**[前へ]** をクリックして戻り、エラーを修正します。
9. **[一般情報]** ページで、アプリに関する追加の詳細情報を入力します。 アプリ パッケージから自動的に取得された場合、この情報の一部は既に入力されている可能性があります。
10. **[次へ]** をクリックし、[概要] ページでアプリケーションの情報を確認し、アプリケーションの作成ウィザードを完了します。 
11. アプリケーションの展開の種類を作成します。 詳しくは、[アプリケーションの展開の種類の作成に関するページ](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application)をご覧ください。
12. Surface Hub にアプリケーションを展開します。 詳細については、「 [Microsoft Endpoint Configuration Manager を使用](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)してアプリケーションを展開する」を参照してください。
13. 必要に応じて、ビジネス向けストアから新しいパッケージをダウンロードし、Configuration Managerでアプリケーションのリビジョンを発行することによって、アプリを更新します。 詳細については、「 [Microsoft Endpoint Configuration Manager を使用してアプリケーションを更新および削除](https://technet.microsoft.com/library/mt595704.aspx)する」を参照してください。 

> [!NOTE] 
> Microsoft Endpoint Configuration Manager (現在のブランチ) を使用している場合は、ビジネス向けストアを Configuration Manager に接続することで、上記の手順を省略できます。 これにより、購入したアプリの一覧を Configuration Manager で同期したり、これらのアプリを Configuration Manager コンソールで表示したり、他のアプリと同様に展開したりすることができます。 詳細については、「 [Microsoft Store For Business から Configuration Manager を使用してアプリを管理する](https://technet.microsoft.com/library/mt740630.aspx)」を参照してください。


## まとめ

Surface Hub にアプリをインストールする方法はいくつかあります。アプリを開発する場合、少数のデバイスでアプリを評価する場合、または組織全体のアプリを展開する場合によって異なります。 次の表はサポートされる方法をまとめたものです。

| インストール方法             | アプリの開発 | 少数のデバイスでの <br> アプリの評価 | 組織での大規模な <br> アプリの展開 |
| -------------------------- | --------------- | ------------------------------------- | ---------------------- |
| Visual Studio              | ○ |   |   |
| プロビジョニング パッケージ       | ○ | ○ |   |
| Microsoft ストア アプリ          |   | ○ |   |
| サポートされる MDM プロバイダー     |   |   | ○ |

## 詳細情報

- [ブログの投稿: Intune を使用して Surface Hub に Windows ストア アプリを展開する](https://blogs.technet.microsoft.com/y0av/2018/01/18/7-2/)


## 関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

 

 





