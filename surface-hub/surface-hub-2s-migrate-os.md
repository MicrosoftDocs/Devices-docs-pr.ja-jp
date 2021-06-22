---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: 2 で 2 Windows 10 Team から Surface HubまたはWindows 10 Proに移行Windows 10 Enterprise。
keywords: Surface Hubデスクトップ、Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 472dc41bd73ace90cccdeb4e52884401c2f9d6d7
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613856"
---
# <a name="migrate-to-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Surface Hub 2 の Windows 10 Pro または Enterprise に移行する

- [記事のバージョン履歴](#version-history)

Surface Hub 2S には、インストールWindows 10 Team付属しています。 このカスタマイズされたエディションのWindows 10会議室環境でのコラボレーションを容易にします。 代わりに、他の PC とWindows 10 Pro、Enterprise 2S を使用Surface Hubを実行できます。

> [!IMPORTANT]
> この移行プロセスでは、この記事で説明されている特定の手順に従う必要があります。 続行する前に、「 [ソリューション コンポーネント」と「移行](#solution-components) とインストール [のワークフロー」を参照してください](#migration-and-installation-workflow-summary)。

> [!NOTE]
> Surface Hub 2S に Windows 10 Pro または Enterprise をインストールする場合は、デバイスに用意されている既存の Windows 10 Team ライセンスとは異なる新しいライセンスが必要です。

別の PC とダウンロードWindows 10 Team Surface *UEFI コン*フィギュレーター ツールを使用して、コンピューターから移行を開始します。 このツールは、新しい UEFI 設定を含むパッケージを作成し、この設定を 2S Surface Hubします。  

Surface UEFI コンフィギュレーターは、Surface 管理モード (SEMM) Enterpriseインターフェイスとして機能します。 企業環境の Surface デバイスのファームウェア設定を一元的に管理できます。 詳細については[、「Microsoft Surface Enterprise管理モード」を参照してください](/surface/surface-enterprise-management-mode)。
 
## <a name="solution-components"></a>ソリューション コンポーネント

- Surface Hubを実行している 2S Windows 10 Team
- デバイスを実行している個別のWindows 10
- SEMM パッケージを作成する Surface UEFI コンフィギュレーター ツール
- Windows 10 Pro OS Enterpriseバージョン 1903 以降
- 16 GB のストレージ、FAT32 形式を持つ 2 つの USB ドライブ
- Microsoft 2 Microsoft Windows 10 Pro インストーラー (MSI) EnterpriseファイルSurface HubとWindowsのドライバーとファームウェア
- インターネット接続
- イメージング ソリューション (オプション)
 
## <a name="migration-and-installation-workflow-summary"></a>移行とインストールのワークフローの概要

| ステップ  | 操作                                                                                                 | 要約                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [UEFI バージョンを 2S Surface Hubします](#verify-the-uefi-version-on-surface-hub-2s)。                                  | UEFI バージョンはバージョン *694.2938.768.0* 以降である必要があります。                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Surface UEFI Configurator と 2 Surface Hubファームウェアをダウンロードします。](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | [IT 用 **[Surface ツール] ページで、[](https://www.microsoft.com/download/details.aspx?id=46703)** </a> ダウンロード] を **選択します**。 次に **、Surface UEFI Configurator MSI**ファイルを選択してダウンロードし、別の PC にインストールします。 また、2 MSI ファイル上の Windows 10 Pro OS および Enterprise OS の[Surface Hubファームウェアをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。</a> 手順 5 で使用するために、このパッケージを保存します。 |
| 3 | [SEMM 証明書を準備します。](#prepare-the-semm-certificate)                                                                          | Surface UEFI コンフィギュレーターを実行するために必要な証明書を準備するか、現在の証明書を使用します。                                                                                                                                                                                                                                                                                                      |
| 4 | [SEMM パッケージを作成します。](#create-a-semm-package)                                                                               | Surface UEFI コンフィギュレーターを起動して、USB ドライブに SEMM パッケージを作成します。 このパッケージには、2S に適用する必要がある構成Surface Hubされます。 これらの SEMM パッケージ ファイルを PC 上のフォルダーにコピーします。                                                                                                                                                                                          |
| 5 | [イメージ、SEMM パッケージWindows 10ドライバーとファームウェアを含む USB フラッシュ ドライブを読み込む。](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | イメージを含む USB ドライブをWindows 10します。 この例では、ドライブの名前は *BOOTME です*。 Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (手順 2 から) と SEMM パッケージ ファイル (手順 4 から) を*BOOTME*ドライブに追加します。                                                                                                                                                                                                  |
| 6 | [OS の移行を有効にするには、Surface Hub UEFI を更新します。](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | *BOOTME ドライブを使用*して UEFI Surface Hub 2S を起動し、SEMM パッケージをインストールします。|
| 7 | [インストールWindows 10 ProまたはEnterprise。](#install-windows-10-pro-or-enterprise)                                        | *BOOTME ドライブを使用*して、バージョン 1903 以降Windows 10 ProまたはEnterpriseインストールします。                                                                                                                                                                                                                                                                                 |
| 8 | [ドライバーとファームウェアをインストールして、Windows 10 ProとEnterprise。](#install-surface-hub-2-drivers-and-firmware)                                        | デバイスに最新の更新プログラムとドライバーがインストールされているのを確認するには、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを 2 MSI ファイルSurface Hub <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> インストールします。</a>                                                                                                                                                                                                                                                                                  |
| 9 | [2S Surface Hub個人の生産性デバイスとして構成します。](#configure-recommended-settings)                                        |  推奨される設定とアプリケーションを有効にして、Surface Hub生産性デバイスとして 2S を最適化します。                                                                                                                                                                                                                                                                    |

### <a name="verify-the-uefi-version-on-surface-hub-2s"></a>UEFI バージョンを 2S Surface Hubする

Surface Hub から Windows 10 Team デスクトップWindows 10に移行する前に *、UEFI バージョン 694.2938.768.0*以降が必要です。
 
**システムの UEFI バージョンを確認するには、次の手順を実行します。**

1. [2S Surface Hub] ホーム ページで、[**スタート**] を選択し、Surface アプリ (すべてのアプリ**Surface) を開**  >  **きます**。

2. デバイス**上の現在**の UEFI バージョンSurface Hub、Surface を選択して、デバイスに関する情報を表示します。 
   - UEFI バージョンが *694.2938.768.0* 以降の場合は、次の図に示すように、SEMM パッケージを作成して OS の移行を有効にできます。

       ![スクリーンショットは、Surface アプリの "Surface" ページを示しています。](images/shm-fig1.png)
 
   - UEFI バージョンがバージョン *694.2938.768.0*より前の場合は、次のいずれかの方法を使用して新しいバージョンを取得します。
   
#### <a name="update-uefi-via-windows-update"></a>更新プログラムを使用して UEFI Windows更新する

1. 2S Surface Hub、管理者としてサインイン**します**。

    >[!Note]
    > ユーザー名または管理者パスワードが分からない場合は、デバイスをリセットする必要があります。 詳細については、「Reset [and recovery for Surface Hub 2S」を参照してください](/surface-hub/surface-hub-2s-recover-reset)。

1. [更新プログラム**とセキュリティ] 設定**[更新Windowsすべてのアプリ] に移動し、  >  ****  >  ****  >  **** すべての更新プログラムをインストールします。
1. デバイスを再起動します。
1. Surface アプリを使用して UEFI バージョンを確認します。 UEFI バージョンが *バージョン 694.2938.768.0* 以降ではない場合は、これらの手順を繰り返すか、次の手順を使用して最新の UEFI バージョンを取得します。

#### <a name="update-the-uefi-via-bare-metal-recovery-bmr-image"></a>ベア メタル回復 (BMR) イメージを使用して UEFI を更新する

1.  Surface 回復サイト[に移動し](https://support.microsoft.com/surfacerecoveryimage)、[2S] **Surface Hub選択します**。
3.  ハブのシリアル番号を入力します。 電源接続の横にあるハブの背面に位置します。
4.  指示に従って、2020 Update にインストールして、フォーマットされた USB ドライブにイメージをダウンロードWindows 10 Teamします。
5.  更新後、デバイスはアウト オブ ボックス エクスペリエンス (OOBE) セットアップを開始します。 セットアップを完了する必要はない。 UEFI バージョンは既に更新されています。 代わりに、画面がオフになるまで電源ボタンを押し続け、デバイスの電源を切ります。

### <a name="download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware"></a>Surface UEFI Configurator をダウンロードし、Surface Hub 2 つのドライバーとファームウェアをダウンロードする

別の PC で、次の手順を実行します。

1. [IT 用 <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Surface ツール] ページで、[ </a> ダウンロード] を **選択します**。  
1. Surface UEFI Configurator MSI ファイルを選択してダウンロードし、別の PC にインストールします。 Surface UEFI コンフィギュレーター ツールは、エディションのインストール中Surface Hub 2S Windows 10 Team実行できない。

1. インストーラー [MSI ファイルSurface Hub 2 つのドライバーとWindowsをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。 このファイルは、新しいオペレーティング システムをインストールするときに使用します。

### <a name="prepare-the-semm-certificate"></a>SEMM 証明書を準備する

Surface UEFI コンフィギュレーターを使用したことがない場合は、証明書を準備する必要があります。 この証明書を使用すると、デバイスが SEMM に登録された後で、承認済み証明書で作成されたパッケージを使用して UEFI 設定のみを変更できます。

証明書の取得方法は、組織のサイズまたは複雑さによって異なります。

- Enterprise組織は通常、標準のセキュリティプラクティスに従って証明書を生成するために独自のインフラストラクチャを維持します。

- 中規模の企業や他の企業は、多くの場合、パートナー プロバイダーから証明書を取得します。 このオプションは、IT の専門知識があまりない組織や、専用の IT セキュリティ チームが不足している組織にお勧めします。

- または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 詳細については、「Surface 管理モード証明書Enterprise[を参照してください](/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。 または、PowerShell を使用して独自の証明書を作成できます。 詳細については、「自己署名証明書」 [のドキュメントを参照](/dotnet/core/additional-tools/self-signed-certificates-guide#create-a-self-signed-certificate) してください。

Surface UEFI Configurator が作成する SEMM パッケージは、証明書で保護する必要があります。 証明書は、UEFI 設定を適用する前に構成ファイルの署名を確認します。 詳細については [、SEMM のドキュメントを参照](/surface/surface-enterprise-management-mode) してください。
 
### <a name="create-a-semm-package"></a>SEMM パッケージの作成

1. 別の PC で、前にダウンロードした Surface UEFI コンフィギュレーター ツールをインストールします。

1. Surface UEFI コンフィギュレーターを開き、[スタート] を **選択します**。

   ![Surface UEFI コンフィギュレーターの開始画面。](images/shm-fig2.png)
   
1. [Surface **Devices] を選択**し、[次へ] を **選択します**。

   ![スクリーンショットは、選択されている Surface Devices オプションを示しています。](images/shm-fig3.png)
  
1. [構成 **パッケージ] を選択します**。

   ![スクリーンショットには、選択されている "構成パッケージの選択" が表示されます。](images/shm-fig4.png)
  
1. [証明書 **の保護] を選択します**。

   ![スクリーンショットは、[証明書保護の選択] を選択する方法を示しています。](images/shm-fig5.png)

   証明書 .pfx ファイルの追加を求めるメッセージが表示されます。

   ![スクリーンショットは、証明書ファイルを追加する場所を示しています。](images/shm-fig6.png)
   
1. 証明書のパスワードを入力し **、[OK] を選択します**。

   ![スクリーンショットには、証明書のパスワードを入力して確認するフィールドが表示されます。](images/shm-fig7.png)

1. [ **パスワード保護] を** 選択して、Surface UEFI にパスワードを追加します。 UEFI を起動するたびに、このパスワードが必要です。 *UEFI パスワードは、2S で使用する UEFI パスワードSurface Hub強く推奨します。*

   ![スクリーンショットは、[パスワード保護] を選択する場所を示しています。](images/shm-fig8.png)
   
1. UEFI パスワードを設定し **、[OK] を選択します**。

   > [!IMPORTANT]
   > パスワードは、管理者が管理する IT 管理者がアクセスできる安全な場所に保存Surface Hub。 *このパスワードが失われた場合は、回復できません。*

   ![スクリーンショットは、UEFI パスワードを設定した場所を示しています。](images/shm-fig9.png)

1. [Surface Hub **2S] を選択し、[** 次へ] を**選択します**。

    ![スクリーンショットは、2S のSurface Hub示しています。](images/shm-fig10.png)
   
1. もう一度 **[次へ] を** 選択します。

    ![スクリーンショットは、[コンポーネントの選択] で [次へ] を選択する場合に表示されます。](images/shm-fig10a.png)

1. サーバーまたはサーバーのインストールをWindows 10 Pro Enterprise **EnableOsMigration**をオンにして、[次へ] を**選択します**。

    ![スクリーンショットは、[O S 移行を有効にする] を選択する場所を示しています。](images/shm-fig11.png)
    
    ![スクリーンショットは、[OS の移行を有効にする] をオンに設定する場所を示しています。](images/shm-fig12.png)

### <a name="manage-semm-enrollment"></a>SEMM 登録の管理

デバイスを SEMM に登録すると、デバイスの管理方法に影響します。 たとえば、SEMM パッケージを適用した後、すべての UEFI 設定はデバイスの UEFI メニューで使用できません (ロックされています)。 PXE ブート用 **IPv6 などの他の設定の** 既定値も使用できません。

移行が完了した後で UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除します。 別の SEMM パッケージを適用して UEFI 設定を変更する場合は、新しい SEMM パッケージをビルドするときに元の証明書を使用する必要があります。 UEFI コンフィギュレーター ツールを使用し **、EnableOSMigration** *をオフのままに*します (元の移行手順のようにオンではありません)。 **

#### <a name="if-you-work-with-partners"></a>パートナーと連携する場合

会社が Surface Hub 2 の移行を Windows 10 Pro または Enterprise にアウトソーシングする場合は、パートナーに SEMM 証明書、SEMM パッケージ、および UEFI パスワードを転送する必要があります。 または、ハブを移行した後、SEMM からすぐに登録を解除できます。 この手順では、UEFI のローカル管理とデバイスの別のパーティへの転送を有効にします。 ただし、移行後に構成できる UEFI パスワードを使用することを強く推奨します。 詳細については [、「Manage Surface UEFI の設定」を参照してください](/surface/manage-surface-uefi-settings)。 

#### <a name="to-roll-back-to-windows-10-team"></a>ユーザーにロールバックWindows 10 Team

この記事で後述するように、移行Windows 10 Teamデバイスを復元する場合は、[](#to-roll-back-to-windows-10-team)まず SEMM から Hub の登録を解除することをお勧めします。 詳細については [、「SEMM からの Surface デバイスの登録を解除する」を参照してください](/surface/unenroll-surface-devices-from-semm)。

#### <a name="save-the-semm-package-to-a-usb-drive"></a>SEMM パッケージを USB ドライブに保存する

1. Connect USB ドライブを PC に接続します。
1. [ **ハブ 2S] を選択し、[** 次へ] を **選択します**。

   ![スクリーンショットは、ハブ 2S を選択する場所を示しています](images/shm-fig13.png)

   > [!WARNING]
   > SEMM パッケージのビルド時に、USB ドライブ上のすべての既存のデータが消去されます。 SEMM パッケージをビルドする前に、USB ドライブから必要なファイルを削除します。
   
1. [ビルド **] を選択します**。

   ![スクリーンショットは、[ビルド] を選択する場所を示しています。](images/shm-fig14.png)

1. このページのスクリーンショットをキャプチャし、[終了] を **選択します**。 SEMM パッケージの準備ができました。 SEMM パッケージ *DfciUpdate.dfi* と、証明書の拇印の最後の 2 文字である *SEMM*拇印を含むテキスト ファイルが含まれています。

   ![スクリーンショットは、[終了] を選択する場所を示しています。](images/shm-fig15.png)
   
4. 証明書の拇印の最後の 2 文字を保存します。 パッケージを 2S に適用する場合は、SEMM をアクティブ化するためにSurface Hubがあります。

### <a name="load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware"></a>イメージ、SEMM パッケージ、および 2 つのドライバー Windows 10ファームウェアを使用して USB フラッシュ Surface Hubを読み込む

次のいずれかのオプションをWindows 10 Pro、Enterpriseイメージ (*バージョン 1903*以降) をインストールできます。

- 現在のイメージング ソリューション。

- [Surface Deployment Accelerator](/surface/microsoft-surface-deployment-accelerator). このツールを使用して、起動可能なイメージをWindows 10します。 イメージには、現在の更新プログラム、Windows 10、Microsoft Office、必要なドライバーとファームウェアが含まれます。

- イメージまたはイメージを含むWindows 10 Pro USB フラッシュ Enterpriseドライブ。 このオプションは、Wi-Fiエクスペリエンス (OOBE) のセットアップ後まで使用できません。 セットアップが完了したら、デバイスにSurface Hub [2](https://www.microsoft.com/download/details.aspx?id=101974)つのドライバーとファームウェアWindows 10 ProインストールEnterpriseインストールします。
 
次の手順では、インストール メディアから USB フラッシュ ドライブを作成し、SEMM パッケージ ファイルと、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub MSI ファイルに追加する方法を示します。 別の展開方法を使用する場合は、この記事の「Update [UEFI on Surface Hub 2S」](#update-uefi-on-surface-hub-2s-to-enable-os-migration)セクションを参照してください。

> [!NOTE]
> インストールが完了したら、既存のライセンスとは別に、Windows 10 ProまたはWindows 10 Enterpriseの有効なライセンスがWindows 10 Teamされます。

1. インストールを作成するにはWindows 10 Proの手順に従って、[ダウンロード] ページのメディア作成ツールを[ダウンロードWindows 10。](https://www.microsoft.com/software-download/windows10) ダウンロードするにはWindows 10 Enterprise Microsoft ボリューム ライセンス[サービス センターに移動します](https://www.microsoft.com/licensing/servicecenter/default.aspx)。

1. 新しい USB ストレージ ドライブを挿入します。
1. メディア作成ツールを開き、[インストール メディアの作成] **を選択し**、[次へ] を **選択します**。

   ![スクリーンショットは、インストール メディアを作成するオプションを示しています。](images/shm-fig16.png)
   
3. 言語を選択し、64**ビットWindows 10** **(x64) を選択します**。 次に、[次へ] **を選択します**。

   ![スクリーンショットは、言語、O S エディション、およびアーキテクチャの種類を選択する場所を示しています。](images/shm-fig17.png)
   
4. [USB **フラッシュ ドライブ] を選択**し、[次へ] を **選択します**。

   ![スクリーンショットは、U S B フラッシュ ドライブを選択する場所を示しています。](images/shm-fig18.png)
   
5. ダウンロードが完了したら、[完了] を **選択します**。

   ![画面は、U S B ドライブの準備が完了し、[完了] ボタンが含まれることを報告します。](images/shm-fig19.png)
   
6. Surface Hub 2 の Windows 10 Pro および Enterprise OS の SEMM パッケージ ファイルとドライバーとファームウェア (MSI ファイル) を、Windows 10 イメージを含む USB フラッシュ ドライブ *(BOOTME)* のルートにコピーします。 BOOTME USB ドライブには次の情報が含まれる。

    - 起動Windows 10イメージ。
    
    - SEMM パッケージ ファイルは、USB ドライブのルートにコピーされます。
    
      - *DfciUpdate.dfi*.
      - SEMM 拇印を含むテキスト ファイル。 (この例では、ファイルは次 *SurfaceUEFI_2020Aug25_1058.txt*です。自動的に生成された日時スタンプは、Surface UEFI コンフィギュレーターを使用してファイルを作成した日付に対応します。

   - バージョン 2 (Windows 10 Pro) の Windows 10 Pro OS Enterprise SurfaceHub2S_Win10_18362_20.082.25682.0.msiとSurface Hubファームウェア。 このファイルを USB ドライブのルートにコピーします。

### <a name="update-uefi-on-surface-hub-2s-to-enable-os-migration"></a>UEFI on Surface Hub 2S を更新して OS の移行を有効にする

1. BOOTME ドライブをデバイス 2S の USB-A ポートSurface Hubします。 必要なコンテンツの一覧については、前のセクションを参照してください。

1. UEFI を起動するには、次の方法を実行します。

   1. 2S でデバイスをオフ (シャットダウン) Surface Hubします。
   1. 音量 + を **長押し**し、電源ボタンを長押しします。 UEFI メニュー **が表示されるまで** 、ボリューム + を押し続ける。
   
      ![図面には、音量ボタンと電源ボタンが表示されます。](images/shm-fig20.png)
      
3. デバイスが再起動したら、以前に作成した UEFI パスワード (該当する場合は推奨) を入力します。

   ![[システム パスワード] 画面。](images/shm-fig22.png)
   
4. UEFI メニューから、[管理] を **選択します**。 次に  **、[USB からインストール] を選択します**。

   ![スクリーンショットは、[管理] を選択し、[U S B からインストール] を選択する場所を示しています。](images/shm-fig21.png)
   
5. 次の **図に示すように**、[今すぐ再起動] を選択します。 デバイスが再起動します。 ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンされます。

   ![スクリーンショットには、再起動を求めるメッセージが表示されます。](images/shm-fig25.png)
   
6. 電源ボタンを押して離します。 表示される赤いダイアログ ボックスで、Surface 管理モードをアクティブEnterprise選択します。

7. 2 文字の証明書拇印と UEFI 設定パスワードを入力します。 次に **、[OK] を選択します**。

   ![スクリーンショットには、2 文字の証明書の拇印と UEFI 設定パスワードを入力する確認ライセンス認証ダイアログ ボックスが表示されます。](images/shm-fig23.png)
 
   > [!NOTE]
   > デバイスで SEMM をアクティブ化すると、新しい UEFI 設定 **EnableOSMigration が** 適用されます。 ユーザーは、アクセスできなくなったWindows 10 Team。 代わりに、次の手順に進み、次の手順に進み、Windows 10 ProまたはWindows 10 Enterprise。

   デバイスが再起動します。 画面の中央に白いロゴが表示され、もう一度シャットダウンします。

### <a name="install-windows-10-pro-or-enterprise"></a>インストールWindows 10 ProまたはEnterprise

1. 起動可能なWindows 10 ProまたはEnterpriseドライブが 2 USB-A ポートSurface Hubされていない場合は、ここで挿入します。 次に、電源ボタンを押して離します。

    デバイスが起動すると、画面の中央に白いロゴが表示されます。 次に、回転する円が白いロゴの下に表示されます。

3. Surface デバイスが USB ドライブに自動的に起動しない場合は、デバイスの電源をオフにします (電源コードを抜いてから、もう一方のプラグを差し込む)。 電源コードを再度接続した後、デバイスは数秒後に起動する必要があります。 次に、画面の中央に白いロゴが表示されます。

    デバイスの電源が入らない場合は、電源ボタンを押して離します。 画面の中央にロゴが表示された直後に、白いロゴの下に回転円が表示されるまで、音量を下にボタンを押し続けます。
 
   ![音量ボタンと電源ボタンの画像。](images/shm-fig26.png)
   
4. アウトオブボックス エクスペリエンス (OOBE) セットアップが開始したら、手順に従って Windows 10 Pro または Enterprise (バージョン 1903 以降) をインストールします。

### <a name="install-surface-hub-2-drivers-and-firmware"></a>2 Surface Hubとファームウェアをインストールする

デバイス 2 が最新Surface Hub確認するには、ドライバーとファームウェアをインストールして、Windows 10 Pro[と](https://www.microsoft.com/download/details.aspx?id=101974)Enterprise。 次に、デバイスを再起動します。 Surface を 1 時間有効にし、もう一度再起動します。 2 回目の再起動を求めるメッセージは表示されません。 この一時停止と追加の再起動により、ファームウェアが完全に更新されます。
 
## <a name="configure-recommended-settings"></a>推奨設定の構成

2S Surface Hubを個人の生産性デバイスとして構成するには、「Configure Windows 10 Pro Enterprise [on Surface Hub 2」を参照してください](surface-hub-2-post-install.md)。

> [!NOTE]
>この記事で説明されている手順に従って Windows 10 Pro または Surface Hub Enterprise Enterprise にデバイスを正常に移行できない場合は、Surface Hub[サポートにお問い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。

## <a name="to-roll-back-to-windows-10-team"></a>ユーザーにロールバックWindows 10 Team

デバイスを別のデバイスに復元する場合Windows 10 Team [2S のリセットと回復Surface Hub参照してください](surface-hub-2s-recover-reset.md)。

> [!NOTE]
> ユーザーにロールバックする前Windows 10 Team、SEMM から最初にSurface Hubをお勧めします。 詳細については [、「SEMM からの Surface デバイスの登録を解除する」を参照してください](/surface/unenroll-surface-devices-from-semm)。

## <a name="version-history"></a>バージョン履歴

次の表に、この記事の変更点を示します。

| バージョン | 日付               | 説明                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1.4  | 2020 年 12 月 14 日 | 「Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア」の MSI ファイルのインストールに関する詳細情報を提供します。システムの状態によっては、2 回目の再起動が必要になる場合があります。 [](#install-surface-hub-2-drivers-and-firmware)                                                          |
| v. 1.3  | 2020 年 12 月 3 日 | SEMM 登録の管理に [関するガイダンスが更新されました](#manage-semm-enrollment)。                                                       |
| v. 1.2  | 2020 年 9 月 29 日 | 使いやすさのフィードバックに対処するその他の更新プログラム。                                                        |
| v. 1.1  | 2020 年 9 月 15 日 | 新しい OS のインストールに関するライセンス要件を明確にした追加のメモを紹介します。 |
| v. 1.0  | 2020 年 9 月 1 日  | 新しい記事。                                                                                           |
