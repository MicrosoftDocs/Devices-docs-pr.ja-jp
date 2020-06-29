---
title: Surface デバイスで PEAP、EAP-FAST、Cisco LEAP を有効にする (Surface)
description: Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP プロトコルのサポートを有効にする方法を説明します。
ms.assetid: A281EFA3-1552-467D-8A21-EB151E58856D
ms.reviewer: ''
manager: laurawi
keywords: ネットワーク, ワイヤレス, デバイス, 展開, 認証, プロトコル, network, wireless, device, deploy, authentication, protocol
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 1a9bef0a6e0bfdd4bede1b508b4013fd14e1a0bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835973"
---
# Surface デバイスで PEAP、EAP-FAST、Cisco LEAP を有効にする


Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP プロトコルのサポートを有効にする方法を説明します。

エンタープライズ ネットワークで PEAP、EAP-FAST、または Cisco LEAP を使っている場合は、導入直後の Surface デバイスではこれら 3 つのワイヤレス認証プロトコルがサポートされていないことを既にご存じかもしれません。 ワイヤレス ネットワークに接続しようとしたときに気付くユーザーや、ファイル共有や内部サイトなどのネットワーク内部のリソースにアクセスできないときに気付くユーザーもいます。 詳しくは、[拡張認証プロトコルに関するページ](https://technet.microsoft.com/network/bb643147)をご覧ください。

USB スティックやファイル共有から小さな MSI パッケージを実行することで、各プロトコルのサポートを追加できます。 Surface デバイスで EAP のサポートを有効にする組織の場合、MSI パッケージ形式では、Microsoft 展開ツールキット (MDT) や Microsoft Endpoint Configuration Manager などのさまざまな管理ツールと展開ツールを使用して展開をサポートしています。

## <a href="" id="download-peap--eap-fast--or-cisco-leap-installation-files--"></a>PEAP、EAP-FAST、または Cisco LEAP のインストール ファイルをダウンロードする


PEAP、EAP-FAST、または Cisco LEAP のインストール ファイルを、Microsoft ダウンロード センターから 1 つの zip アーカイブ ファイルでダウンロードできます。 このファイルをダウンロードするには、Microsoft ダウンロード センターの [IT 向け Surface ツールに関するページ](https://www.microsoft.com/download/details.aspx?id=46703)で、**[ダウンロード]** をクリックし、**[Cisco EAP-Supplicant Installer.zip]** ファイルを選択します。

## MDT で PEAP、EAP-FAST、または Cisco LEAP を展開する


組織内で Surface デバイスへの Windows の展開を既に行っている場合は、展開中に各プロトコルのインストール ファイルを展開共有に追加し、自動インストールを構成する方法が迅速かつ簡単です。 以前に展開した Surface デバイスを更新するタスク シーケンスを構成して、同じプロセスを使ってこれらのプロトコルのサポートを提供するようにすることもできます。

新たに展開された Surface デバイスで PEAP、EAP-FAST、または Cisco LEAP のサポートを有効にするには、次の手順に従います。

1.  各プロトコルのインストール ファイルをダウンロードし、簡単にアクセス可能な場所の個別フォルダーに抽出します。

2.  MDT の Deployment Workbench を開き、展開共有を **Applications** フォルダーに展開します。

3.  **[操作]** ウィンドウから、**[新しいアプリケーション]** を選びます。

4.  **[Application with source files]** (アプリケーションとソース ファイル) を選択して、MSI ファイルを展開共有にコピーします。

5.  目的のプロトコルの手順 1 で作成したフォルダーを選びます。

6.  インストール ファイルが格納される展開共有でフォルダーに名前を付けます。

7.  次のように、アプリケーションを展開するコマンド ラインを指定します。

    -   PEAP の場合は、**EAP PEAP.msi/qn/norestart** を指定します。

    -   LEAP の場合は、**EAP-LEAP.msi/qn/norestart** を指定します。

    -   EAP-FAST の場合は、**EAP FAST.msi/qn/norestart** を指定します。

8.  既定のオプションを使用して、New Application Wizard (新しいアプリケーション ウィザード) を完了します。

9.  目的のプロトコルごとに手順 3 ～ 8 を繰り返します。

これらの手順に従って 3 つの MSI パッケージをアプリケーションとして MDT にインポートしたら、Windows 展開ウィザードの [アプリケーション] ページでそれらを選択できるようになります。 一部の簡単な展開シナリオでは、展開時に技術者が各パッケージを選ぶだけで十分な場合もありますが、それは推奨されません。 このやり方では、ヒューマン エラーのために技術者が Surface デバイス以外のコンピューターにこれらのパッケージを適用しようとしたり、EAP サポートなしで Surface デバイスが展開されたりする可能性があります。

[アプリケーションのインストール] ページでこれらのアプリケーションを非表示にするには、各アプリケーションのプロパティで **[Hide this application in the Deployment Wizard]** (展開ウィザードでこのアプリケーションを非表示にする) チェック ボックスをオンにします。 アプリケーションを非表示にすると、それらは展開中にオプションのアプリケーションとして表示されなくなります。 非表示のアプリケーションを Surface の展開タスク シーケンスで展開するには、それらをタスク シーケンス内の別のステップを通じたインストール向けに明示的に定義しておく必要があります。

プロトコルを明示的に指定するには、次の手順に従います。

1.  MDT の Deployment Workbench から、Surface の展開タスク シーケンスのプロパティを開きます。

2.  **[タスク シーケンス]** タブで、**[状態の復元]** の **[アプリケーションのインストール]** ステップを選びます。 これは通常、Windows Update の Pre-application ステップと Post-application ステップの間にあります。

3.  **[追加]** ボタンを使って、**[全般]** カテゴリから新しい **[アプリケーションのインストール]** ステップを作成します。

4.  ステップの **[プロパティ]** タブで **[アプリケーションを 1 つだけインストールする]** を選びます。

5.  一覧から目的の EAP プロトコルを選びます。

6.  目的のプロトコルごとに手順 2 ～ 5 を繰り返します。

## Configuration Manager で PEAP、EAP-FAST、または Cisco LEAP を展開する


Configuration Manager で Surface デバイスを管理する組織の場合は、さらに簡単に PEAP、EAP-FAST、または Cisco LEAP のサポートを Surface デバイスに展開できます。 ソフトウェア ライブラリからアプリケーションとして各 MSI ファイルをインポートし、Surface デバイス コレクションへの展開を構成するだけです。

Configuration Manager でアプリケーションを展開する方法について詳しくは、「[Configuration Manager のアプリケーションの作成方法](https://technet.microsoft.com/library/gg682159.aspx)」と「[Configuration Manager のアプリケーションの展開方法](https://technet.microsoft.com/library/gg682082.aspx)」をご覧ください。

 

 





