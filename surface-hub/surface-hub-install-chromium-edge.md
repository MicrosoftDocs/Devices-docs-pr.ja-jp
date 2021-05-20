---
title: Surface Hub に新しい Microsoft Edge をインストールして構成する
description: 新しいサーバーをインストールし、Microsoft Edge構成Surface Hub。
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
ms.openlocfilehash: 93f76cadafe2570197fbe70db88540b6be90c3f1
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576727"
---
# <a name="install-and-configure-the-new-microsoft-edge-on-surface-hub"></a>Surface Hub に新しい Microsoft Edge をインストールして構成する

Windows 10 Team 2020 Update では、Chromium (バージョン 85 以上) に基づく新しい Microsoft Edge が、Surface Hub 2S および Surface Hub (v1) の推奨ブラウザーとしてサポートされています。 この記事では、プロビジョニング パッケージ、Microsoft Intune、またはサード パーティのモバイル デバイス管理 (MDM) プロバイダーの 3 つの方法のいずれかを使用してブラウザーをインストールする方法について説明します。

> [!IMPORTANT]
> 既定では、Surface Hub (バージョン 44) にMicrosoft Edge 従来版インストールされます。 [2020 Update](surface-hub-2020-update.md)をインストールした後は、新しいブラウザーに切りMicrosoft Edge勧めします。サポートは[Microsoft Edge 従来版](https://support.microsoft.com/microsoft-edge/what-is-microsoft-edge-legacy-3e779e55-4c55-08e6-ecc8-2333768c0fb0)2021 年 3 月 9 日に終了します。

> [!NOTE]
> 画面ジェスチャの上から下にスワイプしてフルスクリーン モードを終了するには、新しい操作を使用して 2 本の指Microsoft Edge。 長押しタッチ後に表示されるコンテキスト メニューでは、画面の終了操作も使用できます。


## <a name="install-microsoft-edge-using-a-provisioning-package"></a>プロビジョニング Microsoft Edgeを使用してインストールする

1. PC から、USB ドライブの[ルート](https://aka.ms/HubEdge)フォルダー Microsoft Edgeプロビジョニング パッケージ (MicrosoftEdgeInstaller.ppkg) をダウンロードします。
2. USB ドライブをデバイスに挿入Surface Hub。
3. [Surface Hub]**を開**設定プロンプトが表示されたら、管理者の資格情報を入力します。
4. **[Surface Hub]** > **[デバイス管理]** に移動します。 **[プロビジョニング パッケージ]** で、**[プロビジョニング パッケージを追加または削除する]** を選択します。
5. **[パッケージの追加]** を選択します。
6. プロビジョニング パッケージのMicrosoft Edge選択し、[追加] を**選択します**。
7. プロビジョニング パッケージが適用される変更の概要が表示されます。 **[はい、追加する]** を選びます。
8. インストールが完了するまでMicrosoft Edge待ちます。 インストールが完了したら、[スタート] メニューの [Surface Hub] に移動して、新しいサーバーにアクセスMicrosoft Edge。              

> [!NOTE]
> 利用可能な新しいバージョンのMicrosoft Edge、自動的に更新されます。
 
## <a name="install-microsoft-edge-using-intune"></a>Intune をMicrosoft Edgeインストールする
 
> [!NOTE]
> このインストール方法を利用するには、Intune を使用Surface Hubデバイスを登録して管理する必要があります。 詳細については、「MDM を使用して[2S Surface Hubを管理する」を参照してください](manage-settings-with-mdm-for-surface-hub.md)。
 

1. [インストーラーをMicrosoft Edgeします](https://www.microsoft.com/edge/business/download)。
    - Stable チャネルの現在の[バージョンを使用](https://docs.microsoft.com/deployedge/microsoft-edge-channels)**する (バージョン 85)**
    - **64 ビットWindowsを選択する**
2. [アプリにMicrosoft Edgeをビジネス 向け](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows)アプリとして追加Microsoft Intune。
    - アプリの自動更新をMicrosoft Edge Updateする場合Microsoft Edgeアプリのバージョンを無視する設定をアプリ情報**ウィンドウで構成**してください。 **** この設定を **[は**い] に切り替Microsoft IntuneデバイスにインストールされているアプリのバージョンはSurface Hubされません。

## <a name="install-microsoft-edge-using-third-party-mdm-provider"></a>サード パーティMicrosoft Edge MDM プロバイダーを使用してインストールする

1. [Microsoft からMicrosoft Edgeインストーラーをダウンロードします](https://www.microsoft.com/edge/business/download)。
    - Stable チャネルの現在の[バージョンを使用](https://docs.microsoft.com/deployedge/microsoft-edge-channels)**する (バージョン 85)**
    - **64 ビットWindowsを選択する**
2. ローカル ファイルMicrosoft Edge (ローカル ファイル共有) など、ホストされた場所に\\server\share\MicrosoftEdgeEnterpriseX64.msi。 デバイスSurface Hubホストされている場所にアクセスするためのアクセス許可が必要です。
3. [MDM プロバイダーを介して EnterpriseDesktopAppManagement Configuration Service Provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp)を使用して、Microsoft Edge。

## <a name="configure-microsoft-edge"></a>Microsoft Edge を構成する

### <a name="default-microsoft-edge-policies-for-surface-hub"></a>既定Microsoft Edgeポリシー Surface Hub

Microsoft Edgeは、次のポリシー セットを使用して事前構成され、ユーザーに最適なエクスペリエンスを提供Surface Hub。
 
> [!TIP]
> これらのポリシー設定の既定値を保持する必要があります。
 

| ポリシー設定                                                                                                   | 推奨されるエクスペリエンス                                                                                                                                                                                                                                               | 既定値 |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | データ型と設定をデータ型から自動的にインポートMicrosoft Edge 従来版。 これにより、サインインしているユーザーのプロファイルと共有設定を共有するユーザーのプロファイルを、Surface Hub。                                                                                                 | 4                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | 最後Microsoft Edgeウィンドウを閉じた後でも、プロセスをバックグラウンドで実行し続け、セッション中に Web アプリに高速にアクセスできます。                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | ユーザーがユーザーに新しいプロファイルを作成Microsoft Edge。 これにより、閲覧とサインインのエクスペリエンスが簡略化されます。                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | 1 人のユーザーだけがサインインしてサインインMicrosoft Edge。 これにより、閲覧とサインインのエクスペリエンスが簡素化されます。                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | ユーザーがシングル Sign-On (SSO) をMicrosoft Edge。 ユーザーが web サイトにサインインSurface Hub資格情報は、再認証を必要とせずに、サポートされている Web サイトに流れ込む可能性があります。  | 1                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | 管理者以外のユーザーが新しい拡張機能をインストールMicrosoft Edge。 既定でインストールする拡張機能の一覧を構成するには [、ExtensionInstallForcelist を使用します](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist)。 | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | ユーザーが初めて実行するときに通常表示される最初の実行エクスペリエンスとスプラッシュMicrosoft Edge非表示にします。 このSurface Hubは共有デバイスです。これにより、ユーザー エクスペリエンスが簡略化されます。                                                                      | 1                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | InPrivate モードを無効にします。 終了セッションでは既に閲覧データがクリアされています。これにより、閲覧とサインインのエクスペリエンスが簡素化されます。                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | 新しいタブ ページOffice 365フィード エクスペリエンスを表示します。 ユーザーがユーザーにサインインすると、Surface Hubのファイルとコンテンツに高速にアクセスOffice 365。                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | ユーザーが組織アカウントにサインインSurface Hub、リムーバブル以外のプロファイルが組織アカウントを使用して作成されます。 これにより、シングル Sign-On (SSO) エクスペリエンスが簡略化されます。                                                                                                 | 1                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | ユーザー設定での印刷をMicrosoft Edge。 Surface Hub印刷はサポートされていません。                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | ユーザー Microsoft Edgeを使用してサインインしているユーザーを事前に認証Microsoft サービス。 これにより、シングル Sign-On (SSO) エクスペリエンスが簡略化されます。                                                                                                                         | 1                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | ファイルを保存する場所をユーザーに確認するのではなく、ファイルをダウンロード フォルダーに自動的に保存します。 これにより、閲覧エクスペリエンスが簡略化されます。                                                                                                                             | 0                 |

> [!IMPORTANT]
> 展開可能なプログレッシブ Web アプリ (PWA) は、現在、オペレーティング システムWindows 10 Teamサポートされていません。  また[、WebAppInstallForceList Microsoft Edgeポリシー設定は、WebAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist)ではサポートSurface Hub。 

### <a name="configure-microsoft-edge-policy-settings"></a>ポリシー Microsoft Edge構成する

ブラウザー [Microsoft Edgeポリシーを使用して](https://docs.microsoft.com/deployedge/microsoft-edge-policies)、ブラウザーの設定を構成Microsoft Edge。 次のポリシーを使用して適用できます。

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune)、
- [ADMX インジェストを](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)サポートする優先モバイル デバイス管理 (MDM) プロバイダー
- [ADMX インジェストを使用したパッケージのプロビジョニングは、Windows デザイナーで行います](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion)。

 
### <a name="configure-microsoft-edge-updates"></a>更新プログラムMicrosoft Edge構成する

既定では、Microsoft Edge自動的に更新されます。 更新[Microsoft Edgeを使用して](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies)、更新プログラムの設定を構成Microsoft Edge Update。
次の更新Surface HubポリシーはサポートMicrosoft Edge注意してください。

- **Allowsxs** – この場合Surface Hub、Microsoft Edge安定チャネルは常にデータを置き換Microsoft Edge 従来版。
- **CreateDesktopShortcut** – Surface Hubショートカットを使用しない場合。

> [!TIP]
>  Microsoft Edge の機能を利用するには、インターネットに接続する必要があります。 ファイアウォールや他 [のセキュリティ メカニズム](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) を介した通信を確保するために、必要なドメイン URL が [許可] リストに追加されます。

## <a name="related-links"></a>関連リンク

- [Microsoft Edge ドキュメント](https://docs.microsoft.com/microsoft-edge/)

