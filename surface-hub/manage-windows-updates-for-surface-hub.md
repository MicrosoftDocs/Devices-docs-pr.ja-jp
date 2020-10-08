---
title: Surface Hub で Windows 更新プログラムを管理する
description: Microsoft Surface Hub または Surface Hub 2S で、メンテナンスウィンドウを設定するか、更新を延期するか、または Windows Server Update Services (WSUS) を使用して、Windows 更新プログラムを管理できます。
ms.assetid: A737BD50-2D36-4DE5-A604-55053D549045
ms.reviewer: ''
manager: laurawi
keywords: Windows 更新プログラムの管理, Surface Hub, Windows Server Update Services, WSUS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 72214ec9436e6ea106d9e42c957664631ee88a0a
ms.sourcegitcommit: f74253629aaf073b35b1af69439f76e63392c5aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "11103791"
---
# Surface Hub で Windows 更新プログラムを管理する

Surface Hub のオペレーティング システムの新しいリリースは、Windows 10 のリリースと同様に、Windows Update を通じて公開されます。 Surface Hub にインストールする更新プログラムと、更新プログラムを適用するタイミングを管理するには、いくつかの方法があります。
- **Windows Update for Business** - Windows 10 の新機能である Windows Update for Business は、企業がデバイス管理コストを削減しながら、Windows Update でリリースがインストールされる方法やタイミングをさらに細かく管理できるように設計された一連の機能です。 この方法を使用する場合、Surface Hub は Microsoft の Windows Update サービスに直接接続されます。
- **Windows Server Update Services (WSUS)** - IT 管理者は、このサービスを使用することで、Windows Update で企業内のデバイスに適用されると判断された更新プログラムを取得し、更新プログラムに追加のテストと評価を実行してから、インストールする更新プログラムを選択できます。 この方法を使用する場合、Surface Hub は、Windows Update からではなく WSUS から更新プログラムを受け取ります。

Windows Update for Business と WSUS の両方から更新プログラムを受け取るように Surface Hub を構成することもできます。 詳しくは、「[Windows Update for Business と Windows Server Update Services の統合](https://technet.microsoft.com/itpro/windows/manage/waas-integrate-wufb#integrate-windows-update-for-business-with-windows-server-update-services)」をご覧ください。

| 機能 | Windows Update for Business | Windows Server Update Services (WSUS) |
| ------------ | --------------------------- | ------------------------------------- |
| Microsoft の Windows Update サービスから直接更新プログラムを受け取る。追加のインフラストラクチャは不要。  | あり  | ×  |
| テストと評価のための追加の時間を提供するために更新プログラムを延期する。 | あり  | あり  |
| 限定されたデバイスのグループに更新プログラムを展開する。 | あり | あり |
| 更新プログラムをインストールするためのメンテナンス期間を定義する。 | あり  | あり  |

> [!TIP]
> ピア ツー ピアのコンテンツ共有を使用して、更新時の帯域幅の問題を緩和します。 詳しくは、「[Windows 10 更新プログラムの配信の最適化](https://technet.microsoft.com/itpro/windows/manage/waas-optimize-windows-10-updates)」をご覧ください。

> [!NOTE]
> Surface Hub は、現在、更新のロールバックをサポートしていません。


## Surface Hub のサービス モデル

Surface Hub では、[サービスとしての Windows (WaaS)](https://docs.microsoft.com/windows/deployment/update/waas-overview) と呼ばれる、Windows 10 サービス モデルが使用されています。 従来、新機能は数年ごとにリリースされる Windows の新しいバージョンでのみ追加されてきました。 新しいバージョンごとに、組織で展開するには時間と労力のかかるプロセスが必要でした。 その結果、エンドユーザーや組織が新しい技術革新のメリットを十分に享受できていませんでした。 サービスとしての Windows の目標は、高いレベルの品質を維持しながら継続的に新機能を提供することです。

Microsoft では、2 種類の Surface Hub のリリースを広く継続的に公開しています。
- **機能更新プログラム** - 最新の機能とエクスペリエンスをインストールする更新プログラム。 Microsoft は、年ごとに2つの新しい機能更新プログラムを公開することを想定しています。
- **品質更新プログラム** - セキュリティ修正プログラム、ドライバー、その他のサービス更新プログラムのインストールに重点を置いた更新プログラム。 Microsoft は、毎月 1 回、累積的な品質更新プログラムを公開する予定です。

リリースの品質を向上させ、展開を簡略化するために、Surface Hub を含む Windows 10 向けに Microsoft が公開するすべての新しいリリースは累積的です。 つまり、新しい機能更新プログラムや品質更新プログラムには、以前のすべてのリリースのペイロードが (ストレージとネットワークの要件を下げるために最適化された形式で) 含まれており、デバイスにリリースをインストールすると、デバイスは完全に最新の状態になります。 また、以前のバージョンの Windows とは異なり、Windows 10 の品質更新プログラムの内容のサブセットをインストールすることはできません。 たとえば、品質更新プログラムに 3 つのセキュリティの脆弱性と 1 つの信頼性の問題の修正が含まれている場合、更新プログラムを展開すると、4 つすべての修正がインストールされます。

Surface Hub オペレーティング システムでは、[半期チャネル](https://docs.microsoft.com/windows/deployment/update/waas-overview#naming-changes)の更新プログラムを受け取ります。 他のバージョンの Windows 10 と同じように、サービスの有効期間は限定されます。 引き続き品質更新プログラムを受信するために、これらのブランチを実行しているコンピューターに、新しい機能更新プログラムをインストールする必要があります。

サービスとしての Windows について詳しくは、「[サービスとしての Windows の概要](https://technet.microsoft.com/itpro/windows/manage/waas-overview)」をご覧ください。


## Windows Update for Business の使用
Surface Hub には、すべての Windows 10 デバイスと同様に、**Windows Update for Business (WUfB)** が含まれており、デバイスの更新方法を制御することができます。 Windows Update for Business は、デバイス管理コストの削減、更新プログラムの展開方法の制御、セキュリティ更新プログラムへのすばやいアクセスを実現し、さらに Microsoft から継続的に最新の革新的機能を入手するのに役立ちます。 詳しくは、「[Windows Update for Business を使った更新プログラムの管理](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)」をご覧ください。

**Windows Update for Business を設定するには:**
1. [Surface Hub を展開リングにグループ化します。](#group-surface-hub-into-deployment-rings)
2. [Surface Hub で更新プログラムを受信する時期を構成します](#configure-when-surface-hub-receives-updates)。

> [!NOTE]
> Microsoft Intune、Microsoft Endpoint Configuration Manager、サポートされているサードパーティ MDM プロバイダーを使用して、WUfB をセットアップすることができます。 [チュートリアル: Microsoft Intune を使った Windows Update for Business の構成。](https://docs.microsoft.com/windows/deployment/update/waas-wufb-intune)


### Surface Hub を展開リングにグループ化する
展開リングを使用することによって、Surface Hub に更新プログラムをロールアウトする時期を制御し、更新プログラムを検証する時間を提供できます。 たとえば、最初に少数のデバイスを更新して品質を確認した後、組織に広範なロールアウトを実行できます。 組織内の Surface Hub の管理者がだれであるかにもよりますが、他の Windows 10デバイス用に作成した展開リングに Surface Hub を組み込むことを検討します。 展開リングについて詳しくは、「[Windows 10 更新プログラムの展開リングの構築](https://technet.microsoft.com/itpro/windows/manage/waas-deployment-rings-windows-10-updates)」をご覧ください。

次の表に、展開リングの例を示します。

| 展開リング | リング サイズ | サービス ブランチ | 機能更新プログラムの延期 | 品質更新プログラム (セキュリティ修正プログラム、ドライバー、その他の更新プログラム) の延期 | 検証手順 |
| --------- | --------- | --------- | --------- | --------- | --------- |
| プレビュー (例: 重要でないデバイスやテスト デバイス) | 小 | Windows Insider Preview | なし。  | なし。  | 新機能を手動でテストして評価します。 問題がある場合は、更新プログラムを一時停止します。 |
| リリース (例: 限定的なチームによって使用されるデバイス) | 中 | 半期チャネル  | なし。 | なし。  | デバイスの使用状況とユーザーのフィードバックを監視します。 問題がある場合は、更新プログラムを一時停止します。 |
| 広範な展開 (例: 組織内のほとんどのデバイス) | 大 | 半期チャネル |  リリースの 120 日後。 | リリースの 7 ～ 14 日後。 | デバイスの使用状況とユーザーのフィードバックを監視します。 問題がある場合は、更新プログラムを一時停止します。 |
| ミッション クリティカル (例: 役員室のデバイス) | 小 | 半期チャネル |  リリースの 180 日後 (機能更新プログラムの最大保留期間)。 | リリースの 30 日後 (品質更新プログラムの最大保留期間)。 | デバイスの使用状況とユーザーのフィードバックを監視します。 |





### Surface Hub で更新プログラムを受信する時期を構成する
Surface Hub の展開リングを決定した後、各リングでの更新の延期ポリシーを構成します。
- 機能更新プログラムを延期するには、各リングについて適切な [Update/DeferFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays) ポリシーを設定します。
- 品質更新プログラムを延期するには、各リングについて適切な [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays) ポリシーを設定します。

> [!NOTE]
> 更新プログラムのロールアウト時に問題が発生した場合は、[Update/PauseFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausefeatureupdates) と [Update/PauseQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausequalityupdates) を使用して更新プログラムを一時停止することができます


## Windows Server Update Services の使用

Surface Hub を Windows Server Update Services (WSUS) サーバーに接続することで、更新プログラムを管理できます。 更新プログラムは、承認または WSUS サーバーで構成された自動展開ルールによって管理されるため、更新プログラムの展開を選択するまで、新しい更新プログラムが適用されることはありません。

**Surface Hub を WSUS サーバーに手動で接続するには:**
1. Surface Hub で**設定**を開きます。
2. メッセージが表示されたら、デバイスの管理者資格情報を入力します。
3. **[更新とセキュリティ]** > **[Windows Update]** > **[詳細オプション]** > **[Windows Server Update Services (WSUS) サーバーを構成する]** に移動します。
4. **[WSUS サーバーを使用して更新プログラムをダウンロードします]** をクリックし、WSUS サーバーの URL を入力します。

MDM を使用して Surface Hub を WSUS サーバーに接続するには、適切な [Update/UpdateServiceUrl](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_UpdateServiceUrl) ポリシーを設定します。

**プロキシ サーバーなどの方法を使って URL をブロックしている場合**

WSUS 以外の方法で特定の URL をブロックしているために更新できない場合は、次の Windows update の信頼済みサイトの URL を "許可リスト" に追加する必要があります。
- `http(s)://*.update.microsoft.com`
- `http://download.windowsupdate.com` 
- `http://windowsupdate.microsoft.com`

Windows 10 Team Anniversary Update がインストールされた後、これらのアドレスを削除して Surface Hub を以前の状態に戻すことができます。

## メンテナンス期間

業務時間中は常にデバイスを使用できるように、Surface Hub では、指定したメンテナンス期間中に管理機能を実行します。 メンテナンスウィンドウの場合、Surface Hub は、Windows Update または WSUS によって更新プログラムを自動的にインストールし、ウィンドウの終了の20分前にデバイスを再起動します。

Surface Hub では、次のガイドラインに従って更新プログラムを適用します。
- 次のメンテナンス期間中に、更新プログラムをインストールします。 メンテナンス期間中に開始するように会議がスケジュールされている場合や、Surface Hub センサーによってデバイスが使用中であることが検出された場合は、保留中の更新プログラムは次のメンテナンス期間まで延期されます。
- 次のメンテナンス期間が更新プログラムの所定の猶予期間を過ぎた後である場合、デバイスは、更新プログラムのメタデータから推定されたインストール時間を用いて、業務時間内で次に利用可能な空き時間を計算します。 会議がスケジュールされている場合や、Surface Hub センサーによってデバイスが使用中であることが検出された場合は、Surface Hub は引き続き更新プログラムを延期します。
- 次のメンテナンスウィンドウが更新の猶予期間を過ぎ **ていない** 場合、Surface Hub は更新プログラムの延期を続行します。
- 再起動が必要な場合、Surface Hub は次のメンテナンス期間中に自動的に再起動します。

> [!NOTE]
> Surface Hub を初めてセットアップするときは、更新プログラムを適用するための時間を考慮しておきます。 たとえば、ウイルス定義のバックログが入手可能である場合、すぐにインストールする必要があります。

すべての新しい Surface Hub で、既定のメンテナンス期間が設定されています。
-   **開始時刻:** 2:00 AM
-   **再生時間:** 2 時間

**メンテナンス期間を手動で変更するには:**
1.  Surface Hub で**設定**を開きます。
2.  **[更新とセキュリティ]** > **[Windows Update]** > **[詳細オプション]** に移動します。
3.  **[メンテナンス時間]** の **[変更]** を選択します。

MDM を使用してメンテナンス期間を変更するには、[SurfaceHub 構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)の **MOMAgent** ノードを設定します。 詳しくは、「[MDM プロバイダーによる設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。


## 詳細情報

- [ブログ投稿: Surface Hub のサービス、Flighting、および更新プログラムの管理 (もちろん、Intune を使用)](https://blogs.technet.microsoft.com/y0av/2018/05/31/7-3/)


## 関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

