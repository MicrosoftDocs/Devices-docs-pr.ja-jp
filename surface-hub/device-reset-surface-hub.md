---
title: Surface Hub をリセットまたは復元する
description: Surface Hub のリセットと回復のプロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット, 回復
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73c7cf5a387bf7506bb69f62100171df4d94ad2d
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304820"
---
# Surface Hub をリセットまたは復元する

この記事では、Microsoft Surface Hub をリセットまたは復元する方法について説明します。  

[Surface Hub をリセットすると](#reset-a-surface-hub) 、オペレーティング システムは最後の累積的な Windows 更新プログラムに戻り、ローカル ユーザー ファイルと構成情報はすべて削除されます。 削除される情報には、次の情報が含まれます。

- デバイス アカウント
- デバイスのローカル管理者のアカウント情報
- ドメイン参加または Azure AD参加情報
- モバイル デバイス管理 (MDM) 登録情報
- MDM または設定アプリを使用して設定された構成情報

[クラウドから Surface Hub を回復すると、](#recover-a-surface-hub-from-the-cloud) この情報も削除されます。 さらに、Surface Hub は新しいオペレーティング システム イメージをダウンロードしてインストールします。 回復プロセスで、Surface Hub に保存されている他の情報を保持するかどうかを指定できます。 どちらのオプションも使用しない Surface Hub を回復する必要がある場合は [、Surface Hub](surface-hub-recovery-tool.md) 回復ツールでも同じオペレーティング システム イメージが使用されます。

## Surface Hub をリセットする

次のような理由により、Surface Hub のリセットが必要な場合があります。

- 新しい会議スペース用にデバイスを再利用し、再構成する場合。
- ローカルでのデバイスの管理方法を変更したい。
- デバイス アカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。
- 更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。

リセットプロセス中に、長時間空白の画面が表示される場合は、何も実行しないでお待ちください。

> [!WARNING]
> デバイスのリセット プロセスには、最大 6 時間かかる場合があります。 プロセスが完了するまで、Surface Hub をオフにしたり、取り外したりしない。 プロセスを中断すると、デバイスは動作しなくなります。 デバイスが再び機能するには、保証サービスが必要です。

1. Surface Hub で **[設定]** を開きます。

   ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

2. [セキュリティ **の更新&選択します**。

   ![Surface Hub の設定アプリ&セキュリティ グループの更新プログラムを示す画像。](images/sh-settings-update-security.png)

3. [ **回復] を**選択し、[デバイスの **リセット]** で [開始] **を選択します**。

   > [!IMPORTANT]
   > デバイスをリセットする前に、BitLocker キーが利用可能な状態にしてください(後で入力を求めるメッセージが表示されます)。 詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。 ハブが回復パーティションに再起動すると、BitLocker キーの入力を求めるメッセージが表示されます。 このプロンプトをスキップすると、リセットが失敗します。
   
   ![Surface Hub の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   リセット プロセスが完了すると、Surface Hub は最初の実行 [プログラムを再度起動](first-run-program-surface-hub.md) します。 リセット プロセスで問題が発生した場合は、Surface Hub を以前のオペレーティング システム イメージにロールバックし、ようこそ画面を表示します。

<span id="cloud-recovery" />

## クラウドから Surface Hub を回復する

何らかの理由で Surface Hub が使用できなくなる場合でも、Microsoft サポートの支援なしにクラウドから回復できます。 Surface Hub は、クラウドから新しいオペレーティング システム イメージをダウンロードし、そのイメージを使ってオペレーティング システムを再インストールできます。

次の状況では、この種類の回復プロセスの使用が必要な場合があります。

- [Surface Hub または関連アカウントが不安定な状態になった](#recover-a-surface-hub-in-a-bad-state)
- [Surface Hub がロックされている](#recover-a-locked-surface-hub)

>[!IMPORTANT]
>クラウド **プロセスからの回復** には、オープン インターネット接続を提供するワイヤード (有線) 接続が必要です (プロキシや他の認証プロンプトはありません)。

### 正常な状態でない Surface Hub を回復する

デバイス アカウントが不安定な状態になった場合、または管理者アカウントで問題が発生した場合は、設定アプリを使用してクラウド回復プロセスを開始できます。 クラウド回復プロセスは、デバイスのリセット プロセス[](#reset-a-surface-hub)で問題が解決しない場合にのみ使用してください。

1. Surface Hub で、[設定の更新] **を**選択 &gt; **&回復** &gt; **します**。

2. [ **クラウドからの回復] で、[今**すぐ **再起動] を選択します**。

   ![クラウドから回復する](images/recover-from-the-cloud.png)

### ロックされた Surface Hub を回復する

まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。 この場合、デバイスは自動的に再起動し、もう一度操作を試みます。 ただし、この操作が繰り返し失敗した場合、デバイスはユーザー データを保護するために自動的にロックされます。 ロックを解除するには [、デバイスを](#reset-a-surface-hub) リセットするか、デバイスが動作しない場合はクラウドから回復する必要があります。

1. Surface Hub の下部にある電源スイッチを見つける。 電源スイッチが電源コード接続の横にある。 電源スイッチについて詳しくは、Surface Hub サイトの準備ガイド [(PDF) をご覧ください](surface-hub-site-readiness-guide.md)。

2. Surface Hub にようこそ画面が表示されている間は、電源スイッチを使って Surface Hub をオフにします。

3. 電源スイッチを使って Surface Hub をオンに戻します。 デバイスが起動し、Surface Hub ロゴ画面が表示されます。 Surface Hub ロゴの下に回転するドットが表示された場合は、電源スイッチを使って Surface Hub を再びオフにします。  

4. 手順 3 を 3 回繰り返します。または、Surface Hub に [自動修復の準備] メッセージが表示されるまで繰り返します。 このメッセージが表示された後、Surface Hub には Windows RE 画面が表示されます。

5. [詳細 **オプション] を選択します**。

6. [クラウド **からの回復] を選択します**。 (必要に応じて、[リセット] を選択 **できます**。 ただし、 **クラウドからの回復が** 推奨されるアプローチです)。

   ![クラウドからの回復](images/recover-from-cloud.png)
7. Bitlocker キーの入力を求めるメッセージが表示されたら、次のいずれかの操作を行います。

   - Surface Hub で Bitlocker が保護する情報を保持するには、Bitlocker キーを入力します。
   - 保護された情報を破棄するには、[このドライブをスキップ **する] を選択します。**  

8. メッセージが表示されたら、[再インストール] を **選択します**。

    ![再インストール](images/reinstall.png)

9. ディスクを再パーティション化するには、[はい] を **選択します**。

   ![パーティションの再作成](images/repartition.png)

   最初に、回復プロセスによって、クラウドからオペレーティング システム イメージがダウンロードされます。  

   ![ダウンロード中 97&](images/recover-progress.png)

   ダウンロードが完了すると、選択したオプションに従って回復プロセスによって Surface Hub が復元されます。
   

## サポートに問い合わせ

質問がある場合やサポートが必要な場合は、サポート [リクエストを作成できます](https://support.microsoft.com/supportforbusiness/productselection)。


## 関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)
