---
title: Microsoft Surface Hub の監視
description: Microsoft Surface Hub デバイスの監視は、Microsoft Operations Management Suite (OMS) を通じて有効にすることができます。
ms.assetid: 1D2ED317-DFD9-423D-B525-B16C2B9D6942
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の監視, Microsoft Operations Management Suite, OMS, monitor Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 108f24036a0e02295cf2a5588bb6b51e517eba8d
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836181"
---
# Microsoft Surface Hub の監視

Microsoft Surface Hub デバイスの監視は、Microsoft Operations Management Suite (OMS) を通じて有効にすることができます。 [Operations Management Suite](https://go.microsoft.com/fwlink/?LinkId=718138) は、Microsoft の IT 管理ソリューションで、Surface Hub を含む IT インフラストラクチャ全体を管理および保護するのに役立ちます。


Surface Hub は OMS の Log Analytics ソリューションとして提供されるため、すべての Surface Hub にわたって使用状況と信頼性のデータを収集して表示することができます。 Surface Hub ソリューションを使って、次のことができます。
- Surface Hub のインベントリを作成する。
- Skype 会議、ワイヤード (有線) およびワイヤレス プロジェクション、および Surface Hub 上のアプリの使用状況や信頼性のデータのスナップショットを表示する。
- Surface Hub でソフトウェアまたはハードウェアの問題が報告された場合に迅速に対応するためのカスタム アラートを作成する。

## Surface Hub を Operations Management Suite に追加する

1. **Sign in to Operations Management Suite (OMS) にサインインします**。 Microsoft アカウントか職場または学校アカウントを使って、ワークスペースを作成することができます。 会社が既に Azure Active Directory (Azure AD) を使っている場合は、OMS にサインインするときに職場または学校アカウントを使います。 職場または学校アカウントを使うと、OMS で Azure AD の ID を使ってアクセス許可を管理できます。
2. **新しい OMS ワークスペースを作成します**。 ワークスペースの名前を入力して、ワークスペースの地域を選択し、このワークスペースに関連付けるメール アドレスを指定します。 **[作成]** を選択します。
3. **Azure サブスクリプションをワークスペースにリンクします**。 組織に既に Azure サブスクリプションがある場合は、それをワークスペースにリンクすることができます。 組織の Azure 管理者にアクセスを要求する必要がある場合があります。

    > [!NOTE] 
    > 組織に Azure サブスクリプションがない場合は、新規のサブスクリプションを作成するか、一覧から既定の OMS Azure サブスクリプションを選択します。 ワークスペースが開きます。

4. **Surface Hub ソリューションを追加します**。 ソリューション ギャラリーで、**[Surface Hub]** タイルを選択し、ソリューションの詳細ページの **[追加]** を選択します。 これで、ソリューションがワークスペースに表示されます。

## Surface Hub ダッシュ ボードを使用する
OMS ワークスペースの **[概要]** ページから、[Surface Hub] タイルをクリックして Surface Hub ダッシュ ボードを表示します。 ダッシュ ボードを使って、Surface Hub 全体の使用状況と信頼性のデータのスナップショットを入手します。 ダッシュ ボードの各ビューをクリックして詳細なデータを表示し、必要に応じてクエリを変更し、アラートを作成します。

> [!NOTE]
> これらのビューのほとんどには過去 30 日間のデータが表示されますが、内容はサブスクリプションのデータ保持ポリシーによって変わります。

**アクティブな Surface Hub**

このビューを使って、すべての Surface Hub のインベントリを取得します。 OMS に接続されると、各 Surface Hub は定期的に "ハートビート" イベントをサーバーに送信します。 このビューに、過去 24 時間以内にハートビートを報告した Surface Hub が示されます。

<!--
**Skype meetings**

Use this view to get usage data for Skype over the past 30 days. The graph shows the total number of Skype Meetings started across your Surface Hubs, and a breakdown between scheduled meetings, ad hoc meetings, and PSTN calls.
-->
 
**ワイヤレス プロジェクション**

このビューを使って、過去 30 日間のワイヤレス プロジェクションの使用状況と信頼性のデータを入手します。 グラフにすべての Surface Hub にわたるワイヤレス接続の合計数が示され、組織内のユーザーがこの機能を使っているかどうかがわかります。 これが小さい値である場合は、組織内のユーザーに Surface Hub にワイヤレスで接続する方法についてトレーニングを提供する必要があると思われます。
 
また、グラフには成功した接続と失敗した接続の詳細も示されます。 失敗した接続の数が多い場合は、デバイスが Miracast を使ってワイヤレス プロジェクションを正しくサポートしていない可能性があります。 最良のパフォーマンスを得るために、デバイスで WDI Wi-Fi ドライバーと WDDM 2.0 グラフィックス ドライバーを実行することをお勧めします。 詳細ビューを使って、ワイヤレス プロジェクションの問題が特定のデバイスでよく見られるかどうかを確認してください。
 
接続が失敗した場合、Windows ノート PC または Windows Phone を使っている場合は次のことを試すことができます。
- **[設定]** > **[デバイス]** > **[接続中のデバイス]** からペアリングされたデバイスを削除し、接続をもう一度試みます。
- デバイスを再起動します。
 
**ワイヤード (有線) プロジェクション**

このビューを使って、過去 30 日間のワイヤード (有線) プロジェクションの使用状況と信頼性のデータを入手します。 グラフに失敗した接続が多数示されている場合は、オーディオビジュアル パイプラインに接続の問題がある可能性があります。 たとえば、HDMI リピーターや部屋中央のコントロール パネルを使っている場合は、それらを再起動する必要があることがあります。
 
**アプリケーションの使用状況**

このビューを使って、過去 30 日間にわたる Surface Hub でのアプリの使用状況データを入手します。 データは Surface Hub でのアプリの起動に基づきます。Skype for Business は含まれません。 このビューは、どの Surface Hub アプリが組織で最も利用価値が高いかを理解するのに役立ちます。 環境に新しい基幹業務アプリを展開している場合は、それらが使われる頻度を理解するのにも役立ちます。
 
**アプリケーションのクラッシュ**

このビューを使って、過去 30 日間にわたる Surface Hub でのアプリの信頼性データを入手します。 データは Surface Hub でのアプリのクラッシュに基づきます。 このビューは、インボックス アプリと基幹業務アプリが適切に動作しているかどうかを検出し、開発者に知らせるために役立ちます。
 
**サンプル クエリ**

これを使って、推奨される一連のクエリに基づくカスタム アラートを作成します。 アラートは、Surface Hub でソフトウェアまたはハードウェアの問題が報告された場合に迅速に対応するのに役立ちます。 詳しくは、「[サンプル クエリを使ってアラートを設定する](#set-up-alerts-with-sample-queries)」をご覧ください。

## サンプル クエリを使ってアラートを設定する

アラートを使って、Surface Hub でソフトウェアまたはハードウェアの問題が報告された場合に迅速に対応します。 アラート ルールによってスケジュールに従って自動的にログ検索が実行され、結果が特定の条件に一致する場合は 1 つ以上の操作が実行されます。 詳しくは、「[Log Analytics のアラート](https://azure.microsoft.com/documentation/articles/log-analytics-alerts/)」をご覧ください。
 
Surface Hub Log Analytics ソリューションには、適切なアラートを設定し、発生する可能性がある問題を解決する方法を理解するために役立つ一連のサンプル クエリが付属します。 それらのサンプルを、監視およびサポート戦略を計画する出発点として使います。

次の表で、Surface Hub ソリューションに含まれるサンプル クエリについて説明します。

| アラートの種類 | 影響 | 推奨される修復方法 | 詳細 |
| ---------- | ------ | ----------------------- | ------- |
| ソフトウェア   | エラー  | **デバイスを再起動します**。 <br> 手動で再起動するか、[再起動構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt720802(v=vs.85).aspx)を使って再起動します。 <br> 組織内のユーザーへの影響を最小限に抑えるために、会議の間に再起動することをお勧めします。 | トリガーの条件: <br> - シェル、プロジェクション、Skype など、Surface Hub オペレーティング システムの重要なプロセスがクラッシュするか、応答しなくなる。 <br> - デバイスが過去 24 時間以内にハートビートを報告していない。 これはネットワーク接続の問題やネットワークに関連するハードウェア障害、または診断データ レポート システムのエラーが原因である可能性があります。 |
| ソフトウェア   | エラー  | **Exchange サービスを確認します**。 <br> 次のことを確認します。 <br> - サービスが利用可能である。 <br> - デバイス アカウントのパスワードが最新である – 詳しくは「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。| デバイス カレンダーの Exchange との同期でエラーが発生するとトリガーされます。 |
| ソフトウェア   | エラー  | **Skype for Business サービスを確認します**。 <br> 次のことを確認します。 <br> - サービスが利用可能である。 <br> - デバイス アカウントのパスワードが最新である – 詳しくは「[パスワード管理](password-management-for-surface-hub-device-accounts.md)」をご覧ください。 <br> - Skype for Business のドメイン名が正しく構成されている - 詳しくは「[ドメイン名の構成](use-fully-qualified-domain-name-surface-hub.md)」をご覧ください。 | Skype がサインインに失敗するとトリガーされます。 |
| ソフトウェア   | エラー  | **デバイスをリセットします**。 <br> これには少し時間がかかるため、デバイスをオフラインにしてください。 <br> 詳しくは、「[デバイスのリセット](device-reset-surface-hub.md)」をご覧ください。| セッションの最後にユーザーとアプリのデータをクリーンアップするときにエラーが発生するとトリガーされます。 この操作が繰り返し失敗すると、ユーザー データを保護するためにデバイスはロックされます。 続行するには、デバイスをリセットする必要があります。 |
| ハードウェア   | 警告 | **ありません**。 機能への影響が無視できることを示しています。| 次のハードウェア コンポーネントのいずれかでエラーが発生するとトリガーされます。 <br> - 仮想ペン スロット <br> - NFC ドライバー <br> - USB ハブ ドライバー <br> - Bluetooth ドライバー <br> - 近接センサー <br> - グラフィカル パフォーマンス (ビデオ カード ドライバー) <br> - 一致しないハード ドライブ <br> - キーボード/マウスが検出されない |
| ハードウェア   | エラー | **Microsoft サポートに問い合わせます**。 <br> コア機能 (Skype、プロジェクション、タッチ、インターネット接続など) に影響があることを示します。 <br> **注** ハートビートなど一部のイベントには、サポートに問い合わせるときに使用できるデバイスのシリアル番号が含まれています。| 次のハードウェア コンポーネントのいずれかでエラーが発生するとトリガーされます。 <br> **Skype に影響があるコンポーネント**: <br> - スピーカー ドライバー <br> - マイク ドライバー <br> - カメラ ドライバー <br> **ワイヤード (有線) およびワイヤレス プロジェクションに影響があるコンポーネント**: <br> - ワイヤード (有線) タッチバック ドライバー <br> - ワイヤード (有線) 取り込みドライバー <br> - ワイヤレス アダプター ドライバー <br> - Wi-Fi Direct エラー <br> **その他のコンポーネント**: <br> - タッチ デジタイザー ドライバー <br> - ネットワーク アダプター エラー (OMS に報告されない)|

**アラートを設定するには**
1. Surface Hub ソリューションから、いずれかのサンプル クエリを選択します。
2. 必要に応じて、クエリを変更します。 詳しくは、Log Analytics の検索リファレンスを参照してください。
3. ページ上部の **[アラート]** をクリックして、**[アラート ルールの追加]** 画面を開きます。 アラートを構成するためのオプションについて詳しくは、「[Log Analytics のアラート](https://azure.microsoft.com/documentation/articles/log-analytics-alerts/)」をご覧ください。
4. **[保存]** をクリックして、アラート ルールを完成させます。 すぐにルールの実行が開始されます。

## Surface Hub を登録する

Surface Hub を OMS サービスに接続して登録するには、ドメインのポート番号と URL にアクセスできる必要があります。 次の表に、OMS に必要なポートの一覧を示します。 詳しくは、「[Log Analytics のプロキシ設定とファイアウォール設定の構成](https://azure.microsoft.com/documentation/articles/log-analytics-proxy-firewall/)」をご覧ください。

>[!NOTE]
>現在、Surface Hub は、OMSサービスと通信するプロキシ サーバーの使用をサポートしていません。

| エージェント リソース              | ポート | HTTPS 検査をバイパスする |
| --------------------------- | ----- | ------------------------ |
| *.ods.opinsights.azure.com  | 443   | はい |
| *.oms.opinsights.azure.com  | 443   | はい |
| *.blob.core.windows.net     | 443   | はい |
| ods.systemcenteradvisor.com | 443   | いいえ  |

デバイスを OMS に接続するために使用される Microsoft Monitoring Agent は、Surface Hub オペレーティング システムと統合されているため、Surface Hub を OMS に接続するために追加のクライアントをインストールする必要はありません。
 
OMS ワークスペースを設定した後、Surface Hub デバイスを登録する方法はいくつかあります。
- [設定アプリ](#enroll-using-the-settings-app)
- [プロビジョニング パッケージ](#enroll-using-a-provisioning-package)
- [MDM プロバイダー](#enroll-using-a-mdm-provider) (Microsoft Intune や Configuration Manager など)
 
OMS ワークスペースのワークスペース ID と主キーが必要です。 これらは OMS ポータルから取得できます。
 
### 設定アプリを使って登録する

**設定アプリを使って登録するには**

1. Surface Hub から、**[設定]** を起動します。
2. メッセージが表示されたら、デバイスの管理者資格情報を入力します。
3. **[このデバイス]** を選択し、**[デバイス管理]** に移動します。
4. **[監視]** の **[OMS 設定の構成]** を選択します。
5. OMS 設定のダイアログ ボックスで、**[監視を有効にする]** を選択します。
6. OMS ワークスペースのワークスペース ID と主キーを入力します。 これらは OMS ポータルから取得できます。
7. **[OK]** をクリックして構成を完了します。
 
OMS の構成が適切にデバイスに適用されたかどうかを通知する、確認用のダイアログが表示されます。 適切に適用されている場合は、デバイスで OMS へのデータ送信が開始されます。

### プロビジョニング パッケージを使って登録する
プロビジョニング パッケージを使って、Surface Hub を登録することができます。 詳しくは、「[プロビジョニング パッケージの作成](provisioning-packages-for-certificates-surface-hub.md)」をご覧ください。
 
### MDM プロバイダーを使って登録する
SurfaceHub CSP を使って、Surface Hub を OMS に登録することができます。 Intune と Configuration Manager は、Surface Hub のポリシー テンプレートの作成に役立つ組み込みのエクスペリエンスを提供します。 詳しくは、「[MDM プロバイダーによる Surface Hub 設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。

## 関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

 

 





