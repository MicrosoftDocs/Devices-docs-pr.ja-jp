---
title: Surface Hub をリセットまたは回復する
description: Surface Hub のリセットおよび回復プロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット、復元
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 1c8d8b6d89ec1a20550b7aa13c82c73a239c3965
ms.sourcegitcommit: d0a5c8fb2b37eb11858c7be4549e55c4b36d7471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2020
ms.locfileid: "11104819"
---
# Surface Hub をリセットまたは回復する

この記事では、Microsoft Surface Hub をリセットまたは回復する方法について説明します。  

[Surface Hub をリセット](#reset-a-surface-hub) すると、そのオペレーティングシステムが、最後に累積された Windows update に戻り、ローカルユーザーのファイルと構成情報がすべて削除されます。 削除される情報には、次のものが含まれます。

- デバイス アカウント
- デバイスのローカル管理者のアカウント情報
- ドメイン参加または Azure AD-参加情報
- モバイルデバイス管理 (MDM) の登録情報
- MDM または設定アプリを使用して設定された構成情報

[クラウドから Surface Hub を回復すると、](#recover-a-surface-hub-from-the-cloud) この情報も削除されます。 さらに、Surface Hub は、新しいオペレーティングシステムイメージをダウンロードしてインストールします。 回復プロセスで Surface Hub に保存されている他の情報を保存するかどうかを指定できます。

## Surface Hub をリセットする

次のような理由から Surface Hub のリセットが必要になることがあります。

- 新しい会議スペースのためにデバイスを再利用していて、再設定する必要があります。
- ローカルでのデバイスの管理方法を変更したい。
- デバイスアカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。
- 更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。

リセットプロセス中に、長時間の空白画面が表示される場合は、操作を行わないでください。

> [!WARNING]
> デバイスのリセットプロセスには最大6時間かかることがあります。 プロセスが完了するまで Surface Hub の電源をオフにする、または取り外すことはできません。 プロセスを中断すると、デバイスが使用できなくなります。 再機能させるには、デバイスに保証サービスが必要です。

1. Surface Hub で **[設定]** を開きます。

   ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

1. [ **Update & Security**] を選びます。

   ![Surface Hub 用の設定アプリの [更新 & セキュリティ] グループを示す画像。](images/sh-settings-update-security.png)

1. [ **回復**] を選択し、[ **デバイスのリセット**] で [ **はじめ**に] を選択します。

   ![Surface Hub 用の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   リセットプロセスが完了すると、Surface Hub は、 [最初の run プログラム](first-run-program-surface-hub.md) をもう一度開始します。 リセットプロセスで問題が発生した場合は、Surface Hub を以前の既存のオペレーティングシステムイメージにロールバックし、[ようこそ] 画面を表示します。

<span id="cloud-recovery" />

## クラウドから Surface Hub を回復する

何らかの理由で Surface Hub が使用できなくなった場合は、Microsoft サポートの支援なしでクラウドから回復することができます。 Surface Hub はクラウドから新しいオペレーティングシステムイメージをダウンロードし、そのイメージを使用してそのオペレーティングシステムを再インストールできます。

次のような状況では、この種の回復プロセスを使用することが必要な場合があります。

- [Surface Hub またはその関連アカウントが不安定な状態になった](#recover-a-surface-hub-in-a-bad-state)
- [Surface Hub がロックされている](#recover-a-locked-surface-hub)

>[!IMPORTANT]
>**クラウドプロセスから回復**するには、オープンインターネット接続を提供するワイヤード接続 (プロキシやその他の認証プロンプトは不要) が必要です。

### 正常な状態でない Surface Hub を回復する

デバイスアカウントが不安定な状態になった場合、または管理者アカウントで問題が発生した場合は、設定アプリを使用してクラウドの回復プロセスを開始できます。 [デバイスのリセット](#reset-a-surface-hub)プロセスで問題が解決されない場合にのみ、クラウド回復プロセスを使用してください。

1. Surface Hub で、[ **設定**の &gt; **更新 & セキュリティ** &gt; **回復**] を選びます。

1. [ **クラウドからの回復**] で、[ **今すぐ再起動**] を選択します。

   ![クラウドから回復する](images/recover-from-the-cloud.png)

### ロックされた Surface Hub を回復する

まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。 この問題が発生すると、デバイスは自動的に再起動し、操作を再び試みます。 ただし、この操作が繰り返し失敗すると、デバイスは自動的にロックを解除してユーザーデータを保護します。 ロックを解除するには、 [デバイスをリセット](#reset-a-surface-hub) するか、それが機能しない場合はクラウドからデバイスを回復する必要があります。

1. Surface Hub の下部にある電源スイッチを見つけます。 電源スイッチは、電源ケーブル接続の横にあります。 Power switch の詳細については、 [Surface Hub のサイト準備ガイド (PDF)](surface-hub-site-readiness-guide.md)を参照してください。

1. Surface Hub には [ようこそ] 画面が表示されていますが、power switch を使って Surface Hub をオフにします。

1. Power switch を使用して Surface Hub を再びオンにします。 デバイスが起動し、Surface Hub ロゴ画面が表示されます。 Surface Hub ロゴの下にスピンしている点が表示されたら、電源スイッチを使用して Surface Hub をもう一度オフにします。  

1. 手順 3 3 を繰り返すか、Surface Hub に "自動修復の準備中" というメッセージが表示されるまで繰り返します。 このメッセージが表示されると、Surface Hub に Windows RE の画面が表示されます。

1. [ **詳細オプション**] を選択します。

1. [ **クラウドからの回復**] を選びます。 (必要に応じて、[ **リセット**] を選ぶこともできます。 ただし、 **クラウドからの回復** は、推奨される方法です。)

   ![クラウドからの回復](images/recover-from-cloud.png)
1. Bitlocker キーの入力を求めるメッセージが表示された場合は、次のいずれかの操作を行います。

   - Surface Hub で Bitlocker で保護されている情報を維持するには、Bitlocker キーを入力します。
   - 保護された情報を破棄するには、[**このドライブをスキップ**] を選択します。  

1. メッセージが表示されたら、[ **再インストール**] を選択します。

    ![再インストール](images/reinstall.png)

1. ディスクのパーティションを再分割するには、[ **はい]** を選びます。

   ![パーティションの再作成](images/repartition.png)

   まず、回復プロセスでクラウドからオペレーティングシステムイメージをダウンロードします。  

   ![ダウンロード中 97&](images/recover-progress.png)

   ダウンロードが完了すると、回復プロセスによって、選択したオプションに従って Surface Hub が復元されます。
   

## サポートに問い合わせ

質問がある場合やヘルプが必要な場合は、 [サポートリクエストを作成](https://support.microsoft.com/supportforbusiness/productselection)できます。


## 関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)
