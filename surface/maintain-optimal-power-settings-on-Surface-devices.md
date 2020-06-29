---
title: Surface デバイスの最適な電源設定
description: このトピックでは、最適なパワー設定を維持するためのベストプラクティスの推奨事項を示します。また、Surface による power management エクスペリエンスの効率化についても説明します。 この記事は、Surface Pro 7、Surface Pro X、Surface Pc 3 など、現在サポートされているすべての Surface デバイスに適用されます。
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2019
ms.openlocfilehash: 73a74dc05a5a6929fa6360e04aac5d342b9c06a8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834661"
---
# Surface デバイスの最適な電源設定

Surface デバイスは、さまざまなモバイルデバイスの電力消費量に関する最新の進歩を利用して、ワークロード全体で最適化された合理化されたエクスペリエンスを実現するように設計されています。 実行している操作によっては、個々のハードウェアコンポーネントに対する電力の流れを動的に調整して、受信メールやネットワークトラフィックなどのバックグラウンドタスクを一時的に停止してから、低電力アイドル状態 (S0ix) に戻すことができます。

## IT 管理者向けの推奨事項の概要

組織全体の Surface デバイスが Surface power optimization 機能を最大限に活用できるようにするには、次の操作を行います。

-  Windows Update または Surface ドライバーとファームウェア MSI から最新のドライバーとファームウェアをインストールします。 これにより、バランスのある power plan (power profile) が既定で作成され、最適な電源設定が構成されます。  詳細については、「 [Surface ドライバーとファームウェア更新プログラムの管理と展開](manage-surface-driver-and-firmware-updates.md)」を参照してください。
- カスタムの power profiles を作成したり、既定の UI に表示されていない advanced power settings を調整したりする (**システム**  >  **電源 & スリープ**) ことは避けてください。
- ネットワーク全体でデバイスの power profile を管理する必要がある場合 (高度な管理された組織など) は、powercfg コマンドツールを使用して Surface デバイスのファクトリイメージから power plan をエクスポートし、Surface デバイスのプロビジョニングパッケージにインポートします。 

    >[!NOTE]
    >Power plan は、同じ種類の Surface デバイスでのみエクスポートできます。  たとえば、Surface のラップトップから power plan をエクスポートして Surface Pro にインポートすることはできません。  詳細については、「[電源設定を構成](https://docs.microsoft.com/windows-hardware/customize/power-settings/configure-power-settings)する」を参照してください。

- 既存の電源管理ポリシー設定から Surface デバイスを除外します。 

## Background

Surface の power management の実装方法は、以前のオペレーティングシステムとは大きく異なり、一連のスリープ状態を通じて電力を段階的に削減して、電源をオフにします。たとえば、S1、S2、S3 などを順番に切り替えます。

代わりに、Surface は、従来のスリープおよびエネルギー消費機能と最新のスタンバイ機能および動的な微調整に代わるカスタムの power profile でイメージングされます。 このカスタムの power profile は、Surface Serial Hub ドライバーとシステムアグリゲーターモジュール (SAM) を使って実装されています。 SAM チップは Surface デバイスの power policy の所有者として機能します。アルゴリズムを使って最適な電力要件を計算します。 この機能は、Windows power manager と連携して、ハードウェアコンポーネントが機能するために必要な電力量のみを割り当てまたは調整します。 この記事は、Surface Pro 7、Surface Pro X、Surface Pc 3 など、現在サポートされているすべての Surface デバイスに適用されます。

## Surface 内のカスタムの power profile の利用

Surface デバイスの電源オプションに移動すると、1つの電源プランが利用できることがわかります。 これはカスタムの power profile です。 さらに、[advanced power settings] に移動すると、Windows 10 を実行している一般的な PC と比べて、power オプションの小さなサブセットが表示されます。 一般的なデバイスとは異なり、Surface には、これらの電源オプションを管理するためのファームウェアとカスタムコンポーネントが含まれています。


## モダンスタンバイ

Algorithmically embedded custom power profile は、スマートフォンの一般的なオン/オフ機能のために低電力の状態を維持することで、Surface の先進のスタンバイ接続を実現します。 S0ix は、基本的なランタイム Idle Platform State (DRIPS) とも呼ばれ、Surface デバイスの既定の電源モードです。 モダンスタンバイには、次の2つのモードがあります。

- **コネクトスタンバイ。** メール、メッセージング、およびクラウドで同期されたデータの既定のモードである、コネクトスタンバイは Wi-fi を使用してネットワーク接続を維持します。

- **スタンバイ状態が解除されました。** バッテリーを長持ちさせるためのオプションのモードであるスタンバイ状態は、Wi-fi、Bluetooth、関連するネットワーク接続をオフにすることで、同じように瞬時に動作し、電力を節約することができます。

モダンスタンバイの詳細については、 [Microsoft ハードウェアデベロッパーセンター](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)を参照してください。

## Surface による power management エクスペリエンスの効率化 

Surface には、ユーザーが power management エクスペリエンスを最適化するために設計された次の機能が組み込まれています。

- [単数形の power plan](#singular-power-plan)

- [効率化された電源設定のユーザーインターフェイス](#simplified-power-settings-user-interface)

- [Windows のパフォーマンスの power slider](#windows-performance-power-slider)

### 単数形の power plan

Surface は、ユーザー設定の電源プランを作成したり、手動で電源設定を構成したりする必要がないように、電源管理エクスペリエンスの合理化を目的として設計されています。 Microsoft は、標準の Windows ビルドからの複数の電源プランに代わる単一の power plan (均衡) を提供することで、ユーザーエクスペリエンスを合理化します。

### 効率化された電源設定のユーザーインターフェイス

Surface は、ベストプラクティスの accord の推奨事項によって、簡素化された UI を提供します。 通常は、既定のユーザーインターフェイスに表示される設定のみを調整し、advanced power settings またはグループポリシー設定を構成しないようにすることをお勧めします。 既定の画面とスリープタイムアウトを使うと、最大の明るさのレベルが回避され、ユーザーはバッテリの寿命を延ばすことができます。

![図 1.  シンプルな power & スリープ設定](images/powerintrofig1.png)

図 1.  簡素化された電源とスリープの設定

### Windows のパフォーマンスの power slider

Windows 10 ビルド1709以降を実行している Surface デバイスには、必要に応じてバッテリ寿命の優先度を指定したり、必要に応じてパフォーマンスを重視したりするための電源スライダーが含まれています。 バッテリアイコンをクリックすると、タスクバーから電源スライダーにアクセスできます。 スライダーを左にスライドすると、バッテリの寿命が長くなります (バッテリーセーバーモード)。または、スライドを右に移動して、パフォーマンスを向上

![図 2.  Power slider](images/powerintrofig2a.png)

図 2.  Power slider

次の表に示す4つの状態を有効にするには、Power slider を使用します。

| スライダーモード| 説明 |
|---|---|
| バッテリーセーバー| システムが電源に接続されていない場合は、電力を節約してバッテリ寿命を延ばすことができます。 バッテリー節約機能がオンになっていると、一部の Windows 機能が無効、調整、または動作が異なる場合があります。 画面の明るさも短くなります。 バッテリー節約機能は、バッテリー電源 (DC) を使用している場合にのみ使用できます。 詳細については、「[バッテリー節約](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)機能」を参照してください。|
| 推奨 | 以前のバージョンの Windows の既定の設定よりも、バッテリー寿命が長くなります。 |
| パフォーマンスの向上 | バッテリー寿命のパフォーマンスがわずかに優先され、既定のスライダーモードとして機能します。 |
| 最高のパフォーマンス | バッテリ消費量に関係なく、パフォーマンスと応答性を最大にする必要があるワークロードのパフォーマンスを優先します。|

Power slider モードでは、次の表に示すように、特定のハードウェアコンポーネントを直接制御します。

| コンポーネント | スライダー機能 |
|---|---|
| Intel の速度シフト (CPU エネルギーレジスタ) とエネルギーパフォーマンスの優先順位に関するヒント。 | 最適な動作周波数と電圧を選択し、最適なパフォーマンスとパワーを実現します。 エネルギーのパフォーマンスの優先順位 (PERFEPP) は、CPU に対するグローバルな電力効率のヒントです。 |
| ファンの速度 (RPM)| 必要に応じて、バッテリー節約スライダーモードでファンをサイレントのままにするなどの条件を調整します。|
| プロセッサパッケージの電力制限 (PL1/PL2)。| 定常状態 (PL1) およびターボ (PL2) の各ワークロードの実行平均電力制限に対応するために、CPU の周波数を管理する必要があります。|
| プロセッサターボ周波数の制限 (IA ターボの制限) | プロセッサのコアを、定格の動作周波数よりも速く、または遅く実行できるように調整します。                                                |

>[!NOTE]
>Power slider は、コントロールパネル/電源オプション、グループポリシー、または関連メソッドから構成されているかどうかに関係なく、オペレーティングシステムの電源設定に完全に依存しません。

詳細については、次を参照してください。

-   [Windows のパフォーマンスの power slider をカスタマイズする](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

-   [バッテリー節約機能。](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)

## バッテリ寿命の延長のベストプラクティス


| ベスト プラクティス | 次の場所に移動します。 | 次のステップ |
|---|---|---|                                                                                                                                    
| Surface デバイスが最新の状態であることを確認する| Windows Update | タスクバーの検索ボックスに「 **Windows Update** 」と入力し、[**更新プログラムの確認**] を選択します。 |
| 実行している操作に最適な電源設定を選ぶ | Power slider | タスクバーで、バッテリアイコンを選択し、[**最適なパフォーマンス**]、[**最高のバッテリー寿命**]、またはその間の任意の場所を選択します。|
| バッテリー残量が少なくなったときにバッテリを節約する | バッテリーセーバー | タスクバーで、バッテリアイコンを選択し、[**バッテリーの設定**] をクリックします。 バッテリーが下に表示されて**いる場合は**、[バッテリー節約機能を自動的にオンにする] を選び、スライダーを右に動かしてバッテリー残量を延ばすことができます。 |
| 最適な画面の明るさを設定する | バッテリーセーバー | タスクバーでバッテリアイコンを選択し、[**バッテリーの設定**] をクリックして、**バッテリーセーバーで [画面の明るさを下げる**] を選択します。 |
| 接続していないときは常に電力を節約する | バッテリーセーバー| [**次の充電まで、バッテリー節約機能を有効にする**] を選びます。|
| 電源設定の問題を調査します。 | Power のトラブルシューティングツール | タスクバーの [トラブルシューティング] で、[**トラブルシューティング**] を選択してから、[**電源**] を選択し、指示に従います。|
| アプリの使用状況を確認する | アプリ | アプリを閉じます。|
| 電源コードが破損していないかどうかを確認します。| 電源コード | 電源ケーブルが磨耗または破損している場合は交換します。|

## 詳細情報 

- [モダンスタンバイ](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)

<!-- -->

- [Windows のパフォーマンスの power slider をカスタマイズする](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

- [バッテリー節約機能](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)
- [Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する](manage-surface-driver-and-firmware-updates.md)
