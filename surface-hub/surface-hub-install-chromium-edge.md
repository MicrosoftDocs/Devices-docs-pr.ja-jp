---
title: Surface Hub に新しい Microsoft Edge をインストールして構成する
description: Surface Hub に新しい Microsoft Edge をインストールして構成します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/10/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 2bc11fb18137ce21cba27368e0c12bbb9e73a4c2
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327311"
---
# Surface Hub に新しい Microsoft Edge をインストールして構成する

Windows 10 Team 2020 Update は、Surface Hub 2S および Surface Hub (v1) の推奨ブラウザーとして Chromium (バージョン 85 以上) に基づく新しい Microsoft Edge をサポートしています。 この記事では、プロビジョニング パッケージ、Microsoft Intune、またはサード パーティのモバイル デバイス管理 (MDM) プロバイダーの 3 つの方法のいずれかを使用してブラウザーをインストールする方法について説明します。

> [!IMPORTANT]
> 既定では、Surface Hub デバイスには Microsoft Edge レガシ (バージョン 44) がプレインストールされています。 [2020 Update](surface-hub-2020-update.md)をインストールした後、新しい Microsoft Edge ブラウザーに切り替えておきます。Microsoft [Edge レガシのサポートは](https://support.microsoft.com/microsoft-edge/what-is-microsoft-edge-legacy-3e779e55-4c55-08e6-ecc8-2333768c0fb0)2021 年 3 月 9 日に終了します。

## プロビジョニング パッケージを使用して Microsoft Edge をインストールする

1. PC から [、Microsoft Edge](https://aka.ms/HubEdge) プロビジョニング パッケージ (MicrosoftEdgeInstaller.ppkg) を USB ドライブのルート フォルダーにダウンロードします。
2. USB ドライブを Surface Hub に挿入します。
3. Surface Hub から [設定] を **開** き、メッセージが表示されたら管理者の資格情報を入力します。
4. **[Surface Hub]** > **[デバイス管理]** に移動します。 **[プロビジョニング パッケージ]** で、**[プロビジョニング パッケージを追加または削除する]** を選択します。
5. **[パッケージの追加]** を選択します。
6. Microsoft Edge プロビジョニング パッケージを選択し、[追加] を **選択します**。
7. プロビジョニング パッケージが適用される変更の概要が表示されます。 **[はい、追加する]** を選びます。
8. Microsoft Edge のインストールが完了するまで待ちます。 インストールが完了したら、Surface Hub のスタート メニューに移動して、新しい Microsoft Edge にアクセスします。              

> [!NOTE]
> 利用可能な Microsoft Edge の新しいバージョンがある場合は、自動的に更新されます。
 
## Intune を使用して Microsoft Edge をインストールする
 
> [!NOTE]
> Surface Hub デバイスは、Intune を使用して登録および管理する必要があります。 詳細については、「Microsoft Intune での [Surface Hub 2S の管理」を参照してください](https://docs.microsoft.com/surface-hub/surface-hub-2s-manage-intune)。
 

1. [Microsoft Edge インストーラーをダウンロードします](https://www.microsoft.com/edge/business/download)。
    - Stable チャネルの現在の [バージョンを使用する](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(バージョン 85)**
    - **Windows 64 ビットの選択**
2. [Microsoft Edge インストーラーを](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows)、Microsoft Intune に業務用アプリとして追加します。
    - Microsoft Edge Update を使用して Microsoft Edge への自動更新を処理する場合は****、必ず [アプリ情報] ウィンドウの [アプリのバージョンを無視する] 設定**を構成**してください。 この設定を [は**** い] に切り替えた場合、Microsoft Intune では、Surface Hub デバイスにインストールされているアプリのバージョンは適用されません。

## サード パーティの MDM プロバイダーを使用して Microsoft Edge をインストールする

1. [Microsoft Edge インストーラーを Microsoft からダウンロードします](https://www.microsoft.com/edge/business/download)。
    - Stable チャネルの現在の [バージョンを使用する](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(バージョン 85)**
    - **Windows 64 ビットの選択**
2. ローカル ファイル共有 (\\server\share\MicrosoftEdgeEnterpriseX64.msi) などのホストされた場所に Microsoft Edge インストーラーを\\server\share\MicrosoftEdgeEnterpriseX64.msi。 Surface Hub デバイスには、ホストされている場所にアクセスするためのアクセス許可が必要です。
3. MDM [プロバイダーで EnterpriseDesktopAppManagement 構成](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp) サービス プロバイダー (CSP) を使用して、Microsoft Edge をインストールします。

## Microsoft Edge を構成する

### Surface Hub の既定の Microsoft Edge ポリシー

Microsoft Edge には、Surface Hub 向けに最適化されたエクスペリエンスを提供するために、次のポリシー設定が事前に構成されています。
 
> [!TIP]
> これらのポリシー設定の既定値を保持する必要があります。
 

| ポリシー設定                                                                                                   | 推奨されるエクスペリエンス                                                                                                                                                                                                                                               | 既定値 |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Microsoft Edge レガシからデータ型と設定を自動的にインポートしない。 これにより、サインインしているユーザーのプロファイルを Surface Hub の共有設定で変更する必要がなされます。                                                                                                 | 4                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | 最後のブラウザー ウィンドウを閉じた後でも Microsoft Edge プロセスをバックグラウンドで実行し続け、セッション中に Web アプリに高速にアクセスできます。                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | ユーザーが Microsoft Edge で新しいプロファイルを作成できない。 これにより、閲覧とサインインエクスペリエンスが簡素化されます。                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | 1 人のユーザーだけが Microsoft Edge にサインインできます。 これにより、閲覧とサインインエクスペリエンスが簡素化されます。                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | ユーザーは Microsoft Edge でシングル Sign-On (SSO) を利用できます。 ユーザーが Surface Hub にサインインすると、ユーザーの資格情報は、再認証を必要とせずに、サポートされている Web サイトに流れる可能性があります。  | 1                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | 管理者以外のユーザーが Microsoft Edge に新しい拡張機能をインストールし込むのを防ぐ。 既定でインストールする拡張機能の一覧を構成するには [、ExtensionInstallForcelist を使用します](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist)。 | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | ユーザーが Microsoft Edge を初めて実行するときに通常表示される最初の実行エクスペリエンスとスプラッシュ画面を非表示にします。 Surface Hub は共有デバイスです。これにより、ユーザー エクスペリエンスが簡素化されます。                                                                      | 1                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | InPrivate モードを無効にします。 終了セッションでは閲覧データが既にクリアされています。これにより、閲覧とサインインのエクスペリエンスが簡素化されます。                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | 新しいタブ Office 365 フィード エクスペリエンスを表示します。 ユーザーが Surface Hub にサインインすると、ユーザーのファイルやコンテンツに Officeできます。                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | ユーザーが Surface Hub にサインインすると、組織のアカウントを使用してリムーバブル以外のプロファイルが作成されます。 これにより、シングル Sign-On (SSO) エクスペリエンスが簡素化されます。                                                                                                 | 1                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | Microsoft Edge での印刷を無効にします。 Surface Hub では、印刷はサポートされていません。                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Microsoft Edge で、サインインしているユーザーを Microsoft サービスで事前に認証できます。 これにより、シングル Sign-On (SSO) エクスペリエンスが簡素化されます。                                                                                                                         | 1                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | ファイルを保存する場所をユーザーに確認するのではなく、自動的に [ダウンロード] フォルダーにファイルを保存します。 これにより、閲覧エクスペリエンスが簡素化されます。                                                                                                                             | 0                 |

> [!IMPORTANT]
> 展開可能な段階的な Web アプリ (PAS) は、現在、Windows 10 Team オペレーティング システムではサポートされていません。  また、Microsoft Edge ポリシー設定 [WebAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist) は Surface Hub ではサポートされていません。 

### Microsoft Edge ポリシー設定を構成する

[Microsoft Edge のブラウザー ポリシーを使用して](https://docs.microsoft.com/deployedge/microsoft-edge-policies)、Microsoft Edge のブラウザー設定を構成します。 これらのポリシーは、以下を使用して適用できます。

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune)、
- [ADMX インジェストを](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)サポートする、お好みのモバイル デバイス管理 (MDM) プロバイダー
- [Windows 構成デザイナーで ADMX インジェストを使用したプロビジョニング パッケージ](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion)。

 
### Microsoft Edge 更新プログラムを構成する

既定では、Microsoft Edge は自動的に更新されます。 [Microsoft Edge 更新ポリシーを使用して、Microsoft](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies) Edge Update の設定を構成します。
Surface Hub は、次の Microsoft Edge 更新ポリシーをサポートしていない点に注意してください。

- **Allowsx -** Surface Hub では、Microsoft Edge Stable チャネルは常に Microsoft Edge レガシに取って代わる機能です。
- **CreateDesktopShortcut** – Surface Hub はデスクトップ ショートカットを使用しない。

> [!TIP]
>  Microsoft Edge の機能を利用するには、インターネットに接続する必要があります。 ファイアウォールや [他のセキュリティ メカニズムを](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) 介した通信を確実に行う場合は、必要なドメイン URL が許可リストに追加されます。

## 関連リンク

- [Microsoft Edge ドキュメント](https://docs.microsoft.com/microsoft-edge/)

