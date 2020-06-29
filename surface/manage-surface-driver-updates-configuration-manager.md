---
title: Configuration Manager で Surface driver の更新を管理する
description: この記事では、Surface デバイスのファームウェアとドライバーの更新プログラムを管理および展開するために使用できるオプションについて説明します。
ms.assetid: b64879c4-37eb-4fcf-a000-e05cbb3d26ea
ms.reviewer: ''
author: v-miegge
manager: laurawi
keywords: Surface, Surface Pro 3, ファームウェア, 更新プログラム, デバイス, 管理, 展開, ドライバー, USB, Surface, Surface Pro 3, firmware, update, device, manage, deploy, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.author: daclark
ms.topic: article
audience: itpro
ms.openlocfilehash: 1a9c8c64bd524de58696c73a28795b69cc70a7b2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835869"
---
# Configuration Manager で Surface driver の更新を管理する

## まとめ

[Microsoft System Center Configuration manager バージョン 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates)以降では、configuration manager クライアントを通じて、microsoft Surface ファームウェアとドライバー更新プログラムを直接、同期して展開することができます。 このプロセスは、定期的な更新プログラムの展開と似ています。 ただし、Surface driver の更新をカタログに追加するには、いくつかの追加構成が必要です。

## 前提条件

Surface driver の更新を管理するには、次の前提条件が満たされている必要があります。

- Configuration Manager バージョン1710またはそれ以降のバージョンを使用する必要があります。
- すべてのソフトウェア更新ポイント (SUPs) は、Windows Server 2016 以降を実行している必要があります。 そうしないと、構成マネージャーはこの設定を無視し、Surface ドライバーは同期されません。

> [!NOTE]
> 環境が前提条件を満たしていない場合は、「[よく寄せ](#frequently-asked-questions-faq)られる質問 (FAQ)」で、「Surface ドライバーとファームウェアの更新プログラムを展開するための[別の方法](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1)」を参照してください。

## 有用なログファイル

次のログは、Surface ドライバーの更新を管理するときに特に便利です。

|ログ名|説明|
|---|---|
|WCM|登録されている更新のカテゴリ、分類、言語に対応する、ソフトウェアの更新ポイント構成と WSUS サーバーへの接続に関する詳細を記録します。|
|WsyncMgr|ソフトウェアの更新プログラムの同期プロセスの詳細を記録します。|

これらのログは、SUP を管理するサイトサーバー上、または SUP 自体がサイトサーバーに直接インストールされている場合は、SUP 上にあります。
Configuration Manager ログの完全な一覧については、「 [System Center Configuration manager でログファイル](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files)を確認する」を参照してください。

## Surface driver の更新管理を有効にする

Configuration Manager で Surface driver の更新プログラムの管理を有効にするには、次の手順を実行します。

1. Configuration Manager コンソールで、[**管理**  >  **概要**  >  **サイトの構成**  >  **サイト**] に移動します。
1. 使用している環境に対応するトップレベルの SUP サーバーが含まれているサイトを選びます。
1. リボンで、[**サイトコンポーネントの構成**]、[**ソフトウェアの更新ポイント**] の順に選択します。 または、サイトを右クリックして、[**サイトコンポーネント**  >  **ソフトウェアの更新ポイント**の構成] を選びます。
1. [**分類**] タブで、[ **Microsoft Surface ドライバーとファームウェアの更新を含める**] チェックボックスをオンにします。

   ![ソフトウェアの更新ポイントコンポーネントのプロパティ](images/manage-surface-driver-updates-1.png)

1. 次の警告メッセージが表示されたら、[ **OK]** を選択します。

   ![Configuration Manager](images/manage-surface-driver-updates-2.png)

1. [製品] タブで、更新する製品を選択し、[ **OK]** を選択します。

   ほとんどのドライバーは、次の製品グループに属しています。

   - Windows 10 以降のバージョンドライバー
   - Windows 10 以降のアップグレード & サービスドライバー
   - Windows 10 記念日更新プログラムおよび以降のサービスドライバー
   - Windows 10 記念日更新プログラムと & サービスドライバー
   - Windows 10 の作成者が更新後にドライバーを提供する
   - Windows 10 の作成者が更新後にアップグレードして & サービスドライバー
   - Windows 10 では、作成者が更新し、後でドライバーを提供しています
   - Windows 10 では、作成者が更新され、後でアップグレード & のドライバーがインストールされる
   - Windows 10 S 以降のサービスドライバー
   - Windows 10 S バージョン1709および以降のテスト用ドライバーのサービス
   - Windows 10 S バージョン1709以降のアップグレード & テスト用のドライバーを提供する

   > [!NOTE]
   > ほとんどの Surface ドライバーは、複数の Windows 10 製品グループに属しています。 ここに記載されているすべての製品を選択する必要はありません。 更新プログラムカタログに設定されている製品の数を減らすために、同期のために環境で必要な製品のみを選ぶことをお勧めします。

## 構成を確認する

SUP が正しく構成されていることを確認するには、次の手順を実行します。

1. WsyncMgr を開いて、次のエントリを探します。

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   次のいずれかのエントリが WsyncMgr に記録されている場合は、前のセクションの手順4を再確認してください。

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. WCM を開き、次のようなエントリを探します。

   ![WCM の設定](images/manage-surface-driver-updates-3.png)

   このエントリは、SUP サーバーによって現在同期されているすべての製品グループとクラスを一覧表示する XML 要素です。 たとえば、次のようなエントリが表示されることがあります。

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   前のセクションの手順6で選んだ製品が見つからない場合は、SUP の設定が保存されているかどうかをダブルチェックします。

   次の同期が完了するまで待ってから、Surface ドライバーとファームウェア更新プログラムが Configuration Manager コンソールのソフトウェア更新プログラムに一覧表示されているかどうかを確認することもできます。 たとえば、コンソールに次の情報が表示される場合があります。

   ![すべてのソフトウェア更新プログラムの検索結果](images/manage-surface-driver-updates-4.png)

## 手動同期

次の同期を待つ必要がない場合は、次の手順に従って同期を開始します。

1. Configuration Manager コンソールで、[ソフトウェア**ライブラリ**の概要] に移動し、[ソフトウェアの更新プログラム] を選択  >  **Overview**  >  **Software Updates**  >  **All Software Updates**します。
1. リボンで、[**ソフトウェアの更新を同期**] を選択します。 または、[**すべてのソフトウェア更新プログラム**] を右クリックして、[**ソフトウェア更新プログラムの同期**] を選びます。
1. WsyncMgr で次のエントリを探して、同期の進行状況を監視します。

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   sync: SMS synchronizing categories 
   sync: SMS synchronizing categories, processed 0 out of 311 items (0%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing updates

   Synchronizing update 7eaa0148-c42b-45fd-a1ab-012c82972de6 - Microsoft driver update for Surface Type Cover Integration
   Synchronizing update 2dcb07f8-37ec-41ef-8cd5-030bf24dc1d8 - Surface driver update for Surface Pen Pairing
   Synchronizing update 63067414-ae52-422b-b3d1-0382a4d6519a - Surface driver update for Surface UEFI
   Synchronizing update 8e4e3a41-a784-4dd7-9a42-041f43ddb775 - Surface driver update for Surface Integration
   Synchronizing update 7f8baee8-419f-47e2-918a-045a15a188e7 - Microsoft driver update for Surface DTX
   Synchronizing update aed66e05-719b-48cd-a0e7-059e50f67fdc - Microsoft driver update for Surface Base Firmware Update
   Synchronizing update 8ffe1526-6e66-43cc-86e3-05ad92a24e3a - Surface driver update for Surface UEFI
   Synchronizing update 74102899-0a49-48cf-97e6-05bde18a27ff - Microsoft driver update for Surface UEFI
   ```

## Surface ファームウェアとドライバー更新プログラムを展開する

他の更新プログラムを展開する場合と同じ方法で、Surface ファームウェアとドライバーの更新プログラムを展開することができます。

展開の詳細については、「 [System Center 2012 構成マネージャー– Part7: ソフトウェア更新プログラム (展開)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/)」を参照してください。

## よく寄せられる質問 (FAQ)

**この記事の手順を実行しても、Surface ドライバーが同期されません。 どうしてでしょうか?**

Microsoft Update ではなく、上流の Windows Server Update Services (WSUS) サーバーから同期する場合は、Surface driver の更新プログラムをサポートし、同期するように上流の WSUS サーバーが構成されていることを確認してください。 すべてのダウンストリームサーバーは、上流の WSUS サーバーデータベースに存在する更新プログラムに制限されます。

WSUS でドライバーとして分類される、68000を超える更新プログラムがあります。 Surface 関連以外のドライバーが構成マネージャーに同期されないようにするために、ドライバーの同期を許可リストに対してフィルター処理します。 新しい許可リストが公開されて Configuration Manager に組み込まれると、次の同期の後に新しいドライバーがコンソールに追加されます。 Microsoft の目標は、Configuration Manager との同期に使用できるようにするために、各月の [許可] リストに追加された Surface ドライバーを更新プログラムの火曜日と共に取得することです。

構成マネージャー環境がオフラインの場合、[サービス更新プログラム](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool)を configuration manager にインポートするたびに、新しい許可リストがインポートされます。 また、更新プログラムが Configuration Manager コンソールに表示される前に、ドライバーを含む[新しい WSUS カタログ](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected)をインポートする必要があります。 スタンドアロンの WSUS 環境には構成マネージャー SUP よりも多くのドライバーが含まれているため、オンライン機能を備えた構成マネージャー環境を確立して、Surface ドライバーを同期するように構成することをお勧めします。 これにより、オフライン環境とよく似た小さな WSUS のエクスポートが提供されます。

構成マネージャー環境がオンラインで、新しい更新プログラムを検出できる場合は、一覧の更新プログラムが自動的に受信されます。 予期されるドライバーが表示されない場合は、WsyncMgr とを確認して、同期エラーを確認してください。

**Configuration Manager 環境がオフラインになっている場合、Surface ドライバーを手動で WSUS にインポートすることはできますか?**

いいえ、そうではありません。 更新プログラムが WSUS にインポートされても、[許可] 一覧に表示されていない場合は、展開用の Configuration Manager コンソールに更新プログラムがインポートされません。 [サービス接続ツール](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool)を使用して、サービス更新プログラムを Configuration Manager にインポートし、許可リストを更新する必要があります。

**Surface ドライバーとファームウェアの更新プログラムを展開するために必要な代替メソッドは何ですか?**

代替チャネルを使用して Surface ドライバーとファームウェア更新プログラムを展開する方法について詳しくは、「 [surface ドライバーとファームウェア更新プログラムを管理](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates)する」をご覧ください。 .Msi または .exe ファイルをダウンロードして、従来のソフトウェア展開チャネルを使用して展開する場合は、「 [Surface ファームウェアを Configuration Manager で更新](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager)する」を参照してください。

## 追加情報

Surface ドライバーとファームウェアの更新の詳細については、次の記事を参照してください。

- [Surface デバイス用の最新のファームウェアとドライバーをダウンロードする](https://docs.microsoft.com/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices)
- [Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)
- [Surface および System Center Configuration Manager に関する考慮事項](https://docs.microsoft.com/surface/considerations-for-surface-and-system-center-configuration-manager)
