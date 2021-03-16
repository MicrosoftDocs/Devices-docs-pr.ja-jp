---
title: Surface Hub のリセットまたは回復
description: Surface Hub のリセットおよび回復プロセスについて説明し、手順を示します。
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub のリセット、回復
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/10/2021
ms.localizationpriority: medium
ms.openlocfilehash: 8d9a4f995abda4e005e8136ace62e10fb564c9b8
ms.sourcegitcommit: ea853f2dba67e63e6df33538670fd581e17facab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "11408812"
---
# <a name="reset-or-recover-a-surface-hub"></a>Surface Hub のリセットまたは回復

この記事では、Microsoft Surface Hub をリセットまたは回復する方法について説明します。  

[Surface Hub をリセットすると](#reset-a-surface-hub) 、オペレーティング システムは最後の累積的な Windows 更新プログラムに戻され、すべてのローカル ユーザー ファイルと構成情報が削除されます。 削除される情報には、次の情報が含まれます。

- デバイス アカウント
- デバイスのローカル管理者のアカウント情報
- ドメイン参加または Azure AD参加情報
- モバイル デバイス管理 (MDM) 登録情報
- MDM または設定アプリを使用して設定された構成情報

[クラウドから Surface Hub を復元すると、](#recover-a-surface-hub-from-the-cloud) この情報も削除されます。 さらに、Surface Hub は新しいオペレーティング システム イメージをダウンロードしてインストールします。 回復プロセスが Surface Hub に保存されている他の情報を保持するかどうかを指定できます。 これらのどちらのオプションも使用しない Surface Hub を回復する必要がある場合は [、Surface Hub](surface-hub-recovery-tool.md) 回復ツールで同じオペレーティング システム イメージが使用されます。

## <a name="reset-a-surface-hub"></a>Surface Hub のリセット

次のような理由で Surface Hub をリセットする必要がある場合があります。

- 新しい会議スペース用にデバイスを再利用し、再構成します。
- ローカルでのデバイスの管理方法を変更したい。
- デバイス アカウントまたは管理者アカウントのユーザー名またはパスワードが失われました。
- 更新プログラムをインストールすると、デバイスのパフォーマンスが低下します。

リセットプロセス中に、長時間空白の画面が表示される場合は、何も実行しないでお待ちください。

> [!WARNING]
> デバイスのリセット プロセスには最大 6 時間かかる場合があります。 プロセスが完了するまで、Surface Hub の電源をオフにしたり、プラグを抜かしたりしない。 プロセスを中断すると、デバイスは操作不能になります。 デバイスが再び機能するには、保証サービスが必要です。

1. Surface Hub で **[設定]** を開きます。

   > [!div class="mx-imgBorder"]
   > ![Surface Hub の設定アプリを示す画像。](images/sh-settings.png)

2. [ **セキュリティの更新&] を選択します**。

   > [!div class="mx-imgBorder"]
   > ![Surface Hub の設定アプリ&セキュリティ グループの更新プログラムを示す画像。](images/sh-settings-update-security.png)

3. [ **回復] を**選択し、[デバイスのリセット] **で**、[スタート] **を選択します**。

   > [!IMPORTANT]
   > デバイスをリセットする前に、BitLocker キーを使用できる状態にしてください。後でデバイスの入力を求めるメッセージが表示されます。 詳細については [、「Save your BitLocker key 」を参照してください](save-bitlocker-key-surface-hub.md)。 ハブが回復パーティションに再起動すると、BitLocker キーを入力するように求めるメッセージが表示されます。 このプロンプトをスキップすると、リセットが失敗します。
   
   > [!div class="mx-imgBorder"]
   > ![Surface Hub の設定アプリの [デバイスのリセット] オプションを示す画像。](images/sh-settings-reset-device.png)

   リセット プロセスが完了すると、Surface Hub は最初の実行 [プログラムを再度開始](first-run-program-surface-hub.md) します。 リセット プロセスで問題が発生した場合は、Surface Hub を以前のオペレーティング システム イメージにロールバックし、[ようこそ] 画面を表示します。

<span id="cloud-recovery" />

## <a name="recover-a-surface-hub-from-the-cloud"></a>クラウドから Surface Hub を回復する

何らかの理由で Surface Hub が使用できなくなっている場合でも、Microsoft サポートの支援を受けずにクラウドから回復できます。 Surface Hub は、クラウドから新しいオペレーティング システム イメージをダウンロードし、そのイメージを使用してオペレーティング システムを再インストールできます。

次の状況では、この種類の回復プロセスを使用する必要がある場合があります。

- [Surface Hub または関連するアカウントが不安定な状態になった](#recover-a-surface-hub-in-a-bad-state)
- [Surface Hub がロックされている](#recover-a-locked-surface-hub)

>[!IMPORTANT]
>クラウド **からの回復プロセスでは** 、オープン インターネット接続を提供する有線接続が必要です (プロキシや他の認証プロンプトはありません)。

### <a name="recover-a-surface-hub-in-a-bad-state"></a>正常な状態でない Surface Hub を回復する

デバイス アカウントが不安定な状態になった場合、または管理者アカウントに問題が発生した場合は、設定アプリを使用してクラウド回復プロセスを開始できます。 デバイスのリセット プロセスで問題が解決しない[](#reset-a-surface-hub)場合にのみ、クラウド回復プロセスを使用する必要があります。

1. Surface Hub で、[設定の更新] **を** &gt; **選択&回復** &gt; **します**。

2. [ **クラウドからの回復] で、[** 今すぐ再起動 **する] を選択します**。

   > [!div class="mx-imgBorder"]
   > ![クラウドから回復する](images/recover-from-the-cloud.png)

### <a name="recover-a-locked-surface-hub"></a>ロックされた Surface Hub を回復する

まれに、Surface Hub で、セッションの終了時にユーザーとアプリのデータのクリーンアップする際にエラーが発生する場合があります。 この場合、デバイスは自動的に再起動し、操作を再度試行します。 ただし、この操作が繰り返し失敗した場合、デバイスは自動的にロックしてユーザー データを保護します。 ロックを解除するには、デバイス [をリセット](#reset-a-surface-hub) するか、動作しない場合はクラウドから復元する必要があります。

1. Surface Hub の下部にある電源スイッチを見つける。 電源スイッチは、電源コード接続の横に表示されます。 電源スイッチの詳細については [、「Surface Hub Site 準備ガイド (PDF)」を参照してください](surface-hub-site-readiness-guide.md)。

2. Surface Hub に [ようこそ] 画面が表示されている間は、電源スイッチを使用して Surface Hub をオフにします。

3. Surface Hub をオンに戻す場合は、電源スイッチを使用します。 デバイスが起動し、[Surface Hub ロゴ] 画面が表示されます。 Surface Hub ロゴの下に回転ドットが表示されている場合は、電源スイッチを使用して Surface Hub を再度オフにします。  

4. 手順 3 を 3 回繰り返します。または Surface Hub に [自動修復の準備] メッセージが表示されるまで繰り返します。 このメッセージが表示された後、Surface Hub は Windows RE 画面を表示します。
 
5. **[リセット]** を選択します。 

6. BitLocker キーの入力を求めるメッセージが表示されたら、次のいずれかの操作を行います。
   - Surface Hub で BitLocker が保護する情報を保持するには、BitLocker キーを入力します。
   - 保護された情報を破棄するには、[このドライブをスキップする] を選択します。

7. [クラウド **ダウンロード] を選択します。** 

   ![クラウドダウンロード](images/recover-cloud-download.png)

   >[!IMPORTANT]
   >[ダウンロードできない] を示す**** エラー メッセージが表示された場合は、[**キャンセル**] を選択し、[リセット] を**再度選択**します。

8. [ **ドライブを完全にクリーンアップする] を選択します。**
 
   ![ドライブの回復と完全なクリーン](images/recover-fully-clean-drive.png)

9. このデバイスをリセットする **準備ができているかという質問が表示されます**。 **[リセット]** を選択します。 
   
   ![リセットの回復と確認](images/recover-confirm-reset.png)

10. ダウンロードが開始され、回復プロセスは、このデバイス **のリセットを示します**。

    ![進行中の回復](images/recover-in-progress.png)

## <a name="contact-support"></a>サポートに問い合わせ

質問がある場合やサポートが必要な場合は、サポート [要求を作成できます](https://support.microsoft.com/supportforbusiness/productselection)。


## <a name="related-topics"></a>関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)
