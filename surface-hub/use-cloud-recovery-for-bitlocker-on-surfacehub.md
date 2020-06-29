---
title: Surface Hub での BitLocker のクラウド回復の使用方法
description: Surface Hub での BitLocker のクラウド回復の使用方法
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: アクセシビリティの設定, 設定アプリ, 簡単操作
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7912f9d1bab2ba625995c56d6d7da4e6b2d3df37
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834870"
---
# まとめ

この記事では、Surface Hub デバイスで BitLocker によって予期せずメッセージが表示される場合に、クラウド回復機能を使用する方法について説明します。

> [!NOTE]
> BitLocker 回復キーが利用できない場合にのみ、次の手順に従う必要があります。

> [!WARNING]
> * この回復プロセスでは、内部ドライブの内容を削除します。 プロセスが失敗すると、内部ドライブは完全に使用できなくなります。 この問題が発生した場合は、解決するために Microsoft のサービスリクエストをログに記録する必要があります。
> * 回復プロセスが完了すると、デバイスは出荷時の設定にリセットされ、Box でのエクスペリエンスの状態に戻ります。
> * 回復後、Surface Hub を完全に再構成する必要があります。

> [!IMPORTANT]
> このプロセスでは、プロキシまたはその他の認証方法を使用しないオープンインターネット接続が必要です。

## クラウドの回復プロセス

クラウドの回復を実行するには、次の手順を実行します。

1. **さらに回復オプションを使用するには、Esc キーを押し**ます。

   ![Escape のスクリーンショット](images/01-escape.png)

1. [**このドライブをスキップ**] を選択します。

   ![このドライブをスキップするスクリーンショット](images/02-skip-this-drive.png)

1. [**クラウドからの回復**] を選びます。

   ![クラウドからの回復のスクリーンショット](images/03-recover-from-cloud.png)

1. [**はい]** を選びます。

   ![[はい] のスクリーンショット](images/04-yes.png)

1. [**再インストール**] を選びます。

   ![再インストールのスクリーンショット](images/05a-reinstall.png)

   ![ダウンロードのスクリーンショット](images/05b-downloading.png)

1. クラウドの回復プロセスが完了したら、**ボックスの外のエクスペリエンス**を使用して、再構成を開始します。

   ![ボックスの外側にあるスクリーンショット](images/06-out-of-box.png)

## "問題が発生しました" というエラーメッセージ

通常、このエラーは、回復のダウンロード中に発生したネットワークの問題が原因で発生します。 この問題が発生した場合は、ハブを再起動できないため、ハブをオフにしないでください。 このエラーメッセージが表示された場合は、「クラウドから回復する」の手順に戻り、回復処理を再実行します。

1. [**キャンセル**] を選びます。

   ![[キャンセル] のスクリーンショット](images/07-cancel.png)

1. [**トラブルシューティング**] を選びます。

   ![トラブルシューティングのスクリーンショット](images/08-troubleshoot.png)

1. [**クラウドからの回復**] を選びます。

   ![クラウドからの回復のスクリーンショット](images/09-recover-from-cloud2.png)

1. **有線ネットワークが見つからない**というエラーが発生する場合は、[**キャンセル**] を選択し、Surface Hub が有線ネットワークを再検出できるようにします。

   ![ワイヤードネットワークのスクリーンショットが見つからない](images/10-cancel.png)