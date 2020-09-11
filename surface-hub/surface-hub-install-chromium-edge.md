---
title: Surface Hub に新しい Microsoft Edge をインストールして構成する
description: Surface Hub の新しい Microsoft Edge をインストールして構成します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/10/2020
ms.localizationpriority: Medium
ms.openlocfilehash: fe5f76034b5b8ae4801a8fb403d6db0ed423c144
ms.sourcegitcommit: 75940bb1ab4e08c96736923859c7dd673dcf8d79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "11009615"
---
# Surface Hub に新しい Microsoft Edge をインストールして構成する

Windows 10 Team 2020 Update では、Surface Hub の推奨ブラウザーとして、Chromium (バージョン85以降) に基づく新しい Microsoft Edge がサポートされています。 プロビジョニングパッケージを使用して Microsoft Edge を手動でインストールするか、Microsoft Intune またはお好みのモバイルデバイス管理 (MDM) プロバイダーを使用してリモートでインストールすることができます。

既定では、Surface Hub デバイスは Microsoft Edge Legacy (バージョン 44) にプレインストールされています。
 
既に Edge Dev をインストールしている場合は、次の手順を実行します。

1. 使用しているバージョンがわからない場合、または確認したい場合は、Edge ブラウザーを開いて edge://version にアクセスしてください。
2. 「 **デバイス管理 > Surface Hub**に移動します。 [**プロビジョニングパッケージ**] で、[**プロビジョニングパッケージの追加または削除**] を選択します。
3. 以前のインストーラーを使って Microsoft Edge Dev を [スタート] メニューにピン留めしている場合は、一覧から [ **カスタムのスタートメニュー]** をクリックし、[削除] をクリックし **ます。**
4. カスタムの開始レイアウトポリシーを使っている場合は、「 [Surface Hub のスタートメニューで Microsoft edge を表示](#display-microsoft-edge-in-the-surface-hub-start-menu)する」のセクションで説明されているように、最新の Edge パスを使用してアプリを変更する必要があります。
5. これで、MicrosoftEdgeDevUninstaller をプロビジョニングすることができます。
6. **すべてのアプリ**から Edge Dev が削除されたら、最初に "MicrosoftEdgeDevInstaller" を削除し、"MicrosoftEdgeDevUninstaller" を削除します。
7. これにより、Microsoft Edge Dev が正常にアンインストールされます。 これで標準バージョンをインストールできるようになりました。

 
 
## Microsoft Edge をインストールする

### プロビジョニングパッケージを使用して Microsoft Edge をインストールする

1. PC から、 [Microsoft Edge provisioning パッケージ](https://aka.ms/HubEdge) (MicrosoftEdgeDevInstaller kg) を USB ドライブのルートフォルダーにダウンロードします。
2. Surface Hub に USB ドライブを挿入します。
3. Surface Hub から [ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。
4. **[Surface Hub]** > **[デバイス管理]** に移動します。 **[プロビジョニング パッケージ]** で、**[プロビジョニング パッケージを追加または削除する]** を選択します。
5. **[パッケージの追加]** を選択します。
6. Microsoft Edge プロビジョニングパッケージを選択し、[ **追加**] を選択します。
7. プロビジョニングパッケージで適用される変更の概要が表示されます。 **[はい、追加する]** を選びます。
8. Microsoft Edge のインストールが完了するまで待ちます。 インストールが完了したら、Surface Hub の [スタート] メニューに移動して、新しい Microsoft Edge にアクセスします。              

> [!NOTE]
> 使用可能な新しいバージョンの Microsoft Edge がある場合は、それが自動的に更新されます。
 
### Intune を使用して Microsoft Edge をインストールする
 
> [!NOTE]
> Surface Hub デバイスは、Intune を使って登録および管理されている必要があります。 詳細については、「 [Microsoft Intune を使用して Surface Hub を管理](https://docs.microsoft.com/surface-hub/surface-hub-2s-manage-intune)する」を参照してください。
 

1. Microsoft[から Microsoft Edge インストーラーをダウンロード](https://www.microsoft.com/edge/business/download)します。
    - 安定した [チャネル](https://docs.microsoft.com/deployedge/microsoft-edge-channels)から現在のバージョンを使用する **(バージョン 85)**
    - **Windows 64 ビット版**を選ぶ
2. Microsoft [Edge インストーラーを、基幹業務アプリとして Microsoft Intune に追加](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows)します。
    - Microsoft edge 更新プログラムを使用して Microsoft Edge の自動更新を処理する場合は、必ず [アプリの **バージョンを無視** する] 設定を [ **アプリ情報** ] ウィンドウで構成してください。 この設定を **[はい]** に切り替えると、Surface Hub デバイスにインストールされているアプリのバージョンは、Microsoft Intune では強制されません。

 
### モバイルデバイス管理を使用して Microsoft Edge をインストールする

1. Microsoft[から Microsoft Edge インストーラーをダウンロード](https://www.microsoft.com/edge/business/download)します。
    - 安定した [チャネル](https://docs.microsoft.com/deployedge/microsoft-edge-channels)から現在のバージョンを使用する **(バージョン 85)**
    - **Windows 64 ビット版**を選ぶ
2. ローカルファイル共有 (\\server\share\MicrosoftEdgeEnterpriseX64.msi) など、ホストされている場所に Microsoft Edge installer をステージします。 Surface Hub デバイスは、ホストされている場所にアクセスするためのアクセス許可を持っている必要があります。
3. MDM プロバイダーで [EnterpriseDesktopAppManagement 構成サービスプロバイダー (CSP)](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp) を使用して Microsoft Edge をインストールします。

 

## Microsoft Edge を構成する

### Surface Hub の既定の Microsoft Edge ポリシー
Microsoft Edge は、Surface Hub の最適化されたエクスペリエンスを提供するために、次のポリシーで事前構成されています。
 
> [!NOTE]
>  これらのポリシーには既定値のままにすることをお勧めします。
 

| Microsoft Edge ポリシー                                                                                                    | 推奨される操作                                                                                                                                                                                                                                               | 既定値 |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Microsoft Edge Legacy からデータのデータと設定を自動的にインポートしないでください。 これにより、Surface Hub から共有設定を使用して、サインインしたユーザーのプロファイルが変更されるのを回避できます。                                                                                                 | 4d                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | 最後のブラウザーウィンドウを閉じた後でも、バックグラウンドでの Microsoft Edge プロセスの実行を許可することで、セッション中の web アプリへのアクセスが高速になります。                                                                                                      | 件                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Microsoft Edge でユーザーが新しいプロファイルを作成することを許可しないでください。 これにより、閲覧とサインインの操作が簡単になります。                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Microsoft Edge へのサインインを1人のユーザーのみに有効にします。 これにより、閲覧とサインインの操作性が簡素化されます。                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | ユーザーが Microsoft Edge でシングルサインオン (SSO) を利用できるようにします。 ユーザーが Surface Hub にサインインすると、その資格情報は、再認証を要求することなく、サポートされている web サイトに流れることができます。  | 件                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | 管理者以外のユーザーが Microsoft Edge で新しい拡張機能をインストールできないようにします。 既定でインストールされる拡張子の一覧を構成するには、 [Extensioninstallforcelist](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist)を使用します。 | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | ユーザーが Microsoft Edge を初めて実行したときに表示される、最初の実行環境とスプラッシュ画面を非表示にします。 Surface Hub は共有デバイスであるため、ユーザーエクスペリエンスが簡単になります。                                                                      | 件                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | InPrivate モードを無効にします。 エンドセッションでは既に参照データが消去されるため、これにより、閲覧とサインインの操作が簡単になります。                                                                                                                                          | 件                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | 新しいタブページの Office 365 フィードエクスペリエンスを示しています。 ユーザーが Surface Hub にサインインすると、Office 365 上のファイルやコンテンツにすばやくアクセスできるようになります。                                                                                                        | 件                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | ユーザーが Surface Hub にサインインすると、その組織アカウントを使用して非リムーバブルプロファイルが作成されます。 これにより、シングルサインオン (SSO) エクスペリエンスが簡素化されます。                                                                                                 | 件                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | Microsoft Edge での印刷を無効にします。 Surface Hub は印刷をサポートしていません。                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Microsoft Edge で、Microsoft サービスを使ってサインインしたユーザーを事前に認証できるようにします。 これにより、シングルサインオン (SSO) エクスペリエンスが簡素化されます。                                                                                                                         | 件                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | ファイルを保存する場所をユーザーに確認するのではなく、[ダウンロード] フォルダーに自動的にファイルを保存します。 これにより、ブラウジング操作が簡単になります。                                                                                                                             | 0                 |

> [!IMPORTANT]
> Windows 10 Team オペレーティングシステムでは、展開可能なプログレッシブ web アプリ (PWAs) は現在サポートされていません。  Microsoft Edge ポリシーの設定 [WebAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist) は Surface Hub ではサポートされていないことにも注意してください。 

### Microsoft Edge のポリシー設定を構成する

Microsoft edge [ブラウザーのポリシー](https://docs.microsoft.com/deployedge/microsoft-edge-policies) を使って、microsoft edge でブラウザーの設定を構成します。 これらのポリシーは、次の方法で適用できます。

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune)
- [ADMX の取り込みをサポートしている、お好みのモバイルデバイス管理 (MDM) プロバイダー](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)
- [Windows 構成デザイナーでの ADMX の取り込みを使用したパッケージのプロビジョニング](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion)。

 
### Microsoft Edge の更新プログラムを構成する

既定では、Microsoft Edge は自動的に更新されます。 Microsoft edge [更新ポリシー](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies) を使って Microsoft Edge 更新プログラムの設定を構成します。
Surface Hub では、次の Microsoft Edge 更新ポリシーはサポートされていないことに注意してください。

- **Allowsxs** – Surface Hub では、microsoft Edge の厩舎チャネルは常に Microsoft edge Legacy に置き換わるものです。
- **Createdesktopshortcut** – Surface Hub では、デスクトップショートカットは使用されません。

> [!NOTE]
>  Microsoft Edge の機能を利用するには、インターネットに接続する必要があります。 ファイアウォールとその他のセキュリティメカニズムを通じて通信するために [必要なドメイン url](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) が許可リストに追加されていることを確認します。
 
### Surface Hub のスタートメニューに Microsoft Edge を表示する

既定の [スタート] メニューレイアウトを使用している場合は、microsoft Edge プロビジョニングパッケージで [スタート] メニューをインストールして、Microsoft Edge を固定アプリとして追加することができます。
カスタマイズされた [スタート] メニューレイアウトを適用する場合は、次の XML を使用して、Microsoft Edge 用にピン留めされたタイルを追加します。

```xml

<start:DesktopApplicationTile

DesktopApplicationLinkPath="C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"

Size="2x2"

Row="0"

Column="0"/>
```

詳細については、「 [Surface Hub の [スタート] メニューを構成する](https://docs.microsoft.com/surface-hub/surface-hub-start-menu)」を参照してください。
 
> [!NOTE]
> 新しい Microsoft Edge では、SecondaryTiles を使用した固定 web サイトとリンクはサポートされません。

## 関連リンク

- [Microsoft Edge のドキュメント](https://docs.microsoft.com/microsoft-edge/)。

