---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: Surface Hub 2 の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
keywords: Surface Hub デスクトップ、Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: d7ecee2ca66640b054efc106191d12c1844b90a1
ms.sourcegitcommit: 1bc22f7343af9b1b1b8b375d540adee2af68e693
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2021
ms.locfileid: "11297640"
---
# Surface Hub 2 の Windows 10 Pro または Enterprise に移行する

- [記事のバージョン履歴](#version-history)

Surface Hub 2S には、Windows 10 Team がインストールされています。 このカスタマイズされた Windows 10 エディションは、会議室環境でのコラボレーションを容易にします。 代わりに、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub 2S を使用できます。

> [!IMPORTANT]
> この移行プロセスでは、この記事で説明されている特定の手順に従う必要があります。 続行する前に、ソリューション[コンポーネントと移行とインストール](#solution-components)[のワークフローを参照してください](#migration-and-installation-workflow-summary)。

> [!NOTE]
> Windows 10 Pro または Enterprise をインストールする場合は、既存の Windows 10 Team ライセンスとは別の新しいライセンスが必要です。

別の PC とダウンロード可能な *Surface UEFI* 構成ツールを使って、Windows 10 Team からの移行を開始します。 このツールは、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。  

Surface UEFI コンフィエーターは、Surface Enterprise 管理モード (SEMM) へのインターフェイスとして機能します。 企業環境の Surface デバイスでファームウェア設定を一元的に管理できます。 詳しくは [、Microsoft Surface Enterprise 管理モードに関するページをご覧ください](https://docs.microsoft.com/surface/surface-enterprise-management-mode)。
 
## ソリューション コンポーネント

- Windows 10 Team を実行している Surface Hub 2S デバイス
- Windows 10 を実行している個別のデバイス
- SEMM パッケージを作成する Surface UEFI 構成ツール
- Windows 10 Pro または Enterprise OS イメージ バージョン 1903 以降
- 16 GB のストレージ、FAT32 形式の 2 つの USB ドライブ
- Surface Hub 2 Microsoft Windows インストーラー (MSI) ファイルの Windows 10 Pro および Enterprise のドライバーとファームウェア
- インターネット接続
- イメージング ソリューション (オプション)
 
## 移行とインストールのワークフローの概要

| ステップ  | 操作                                                                                                 | 要約                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Surface Hub 2S で UEFI バージョンを確認します](#verify-the-uefi-version-on-surface-hub-2s)。                                  | UEFI バージョンはバージョン *694.2938.768.0 以降である* 必要があります。                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードします。](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | [Surface **[Tools for IT] ページで、[](https://www.microsoft.com/download/details.aspx?id=46703)** </a> ダウンロード] を **選択します**。 次に **、Surface UEFI Configurator MSI**ファイルを選択してダウンロードし、別の PC にインストールします。 [また、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェアをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。</a> 手順 5 で使用するためにこのパッケージを保存します。 |
| 3 | [SEMM 証明書を準備します。](#prepare-the-semm-certificate)                                                                          | Surface UEFI コンフィエーターを実行するために必要な証明書を準備するか、現在の証明書を使用します。                                                                                                                                                                                                                                                                                                      |
| 4 | [SEMM パッケージを作成します。](#create-a-semm-package)                                                                               | Surface UEFI コンフィエーターを起動して、USB ドライブに SEMM パッケージを作成します。 このパッケージには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。 これらの SEMM パッケージ ファイルを PC 上のフォルダーにコピーします。                                                                                                                                                                                          |
| 5 | [Windows 10 イメージ、SEMM パッケージ、ドライバーとファームウェアを含む USB フラッシュ ドライブを読み込む。](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Windows 10 イメージを含む USB ドライブを作成します。 この例では、ドライブの名前は *BOOTME です*。 Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (手順 2 から) と SEMM パッケージ ファイル (手順 4 から) を *BOOTME* ドライブに追加します。                                                                                                                                                                                                  |
| 6 | [Surface Hub 2S の UEFI を更新して、OS の移行を有効にします。](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | *BOOTME ドライブを使*って Surface Hub 2S を UEFI メニューで起動し、SEMM パッケージをインストールします。|
| 7 | [Windows 10 Pro または Enterprise をインストールします。](#install-windows-10-pro-or-enterprise)                                        | *BOOTME ドライブを使*って、Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。                                                                                                                                                                                                                                                                                 |
| 8 | [Windows 10 Pro と Enterprise のドライバーとファームウェアをインストールします。](#install-surface-hub-2-drivers-and-firmware)                                        | デバイスに最新の更新プログラムとドライバーがインストールされている必要がある場合は、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェアをインストール <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> します。</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Surface Hub 2S を個人の生産性向上デバイスとして構成します。](#configure-recommended-settings)                                        |  推奨される設定とアプリケーションを有効にして、個人の生産性デバイスとして Surface Hub 2S を最適化します。                                                                                                                                                                                                                                                                    |

### Surface Hub 2S で UEFI バージョンを確認する

Surface Hub を Windows 10 Team から Windows 10 Desktop に移行する前に *、UEFI バージョン 694.2938.768.0* 以降が必要です。
 
**システムで UEFI バージョンを確認するには、次の手順を実行します。**

1. Surface Hub 2S ホーム ページで、[スタート]**を選択し**、Surface アプリ (すべてのアプリの Surface)**を開**  >  **きます**。

2. Surface **を選び** 、デバイス上の現在の UEFI バージョンを含む Surface Hub に関する情報を表示します。 
   - 次の図に示すように *、UEFI バージョンが 694.2938.768.0* 以降の場合は、SEMM パッケージを作成して OS の移行を有効にできます。

       ![Screenshot shows the "Your Surface" page in the Surface app.](images/shm-fig1.png)
 
   - UEFI バージョンが *バージョン 694.2938.768.0*より前の場合は、次のいずれかの方法を使用して新しいバージョンを取得します。
   
#### Windows Update による UEFI の更新

1. Surface Hub 2S で、管理者としてサインイン **します**。

    >[!Note]
    > ユーザー名または管理者パスワードが分からない場合は、デバイスをリセットする必要があります。 詳しくは [、「Surface Hub 2S のリセットと回復」をご覧ください](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)。

1. [すべてのアプリ**の設定の**  >  **更新と**  >  **セキュリティ**  >  **の Windows Update] に移動し**、すべての更新プログラムをインストールします。
1. デバイスを再起動します。
1. Surface アプリを使って UEFI バージョンを確認します。 UEFI バージョンが *バージョン 694.2938.768.0* 以降ではない場合は、これらの手順を繰り返します。または、次の手順を使用して最新の UEFI バージョンを取得します。

#### ベア メタル回復 (BMR) イメージを使用して UEFI を更新する

1.  Surface の回復サイト [に移動し、Surface](https://support.microsoft.com/surfacerecoveryimage) **Hub 2S を選択します**。
3.  ハブのシリアル番号を入力します。 電源接続の横のハブの背面に位置します。
4.  指示に従って、Windows 10 Team 2020 Update をインストールして、フォーマットされた USB ドライブにイメージをダウンロードします。
5.  更新後、デバイスは Out-Of-Box-Experience (OOBE) セットアップに入った。 セットアップを完了する必要はない。 UEFI バージョンは既に更新されています。 代わりに、画面がオフになるまで電源ボタンを押し続け、デバイスの電源を切ります。

### Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードする

別の PC で、次の手順を実行します。

1. [Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Tools for IT] ページで、[ </a> ダウンロード] を **選択します**。  
1. Surface UEFI Configurator MSI ファイルを選択してダウンロードし、別の PC にインストールします。 Windows 10 Team エディションのインストール中は、Surface Hub 2S で Surface UEFI コンフィエーター ツールを実行できない。

1. Surface [Hub 2 のドライバーとファームウェアの Windows インストーラー MSI ファイルをダウンロードします](https://www.microsoft.com/download/details.aspx?id=101974)。 このファイルは、新しいオペレーティング システムをインストールするときに使用します。

### SEMM 証明書を準備する

Surface UEFI コンフィエーターを使用したことがない場合は、証明書を準備する必要があります。 この証明書により、デバイスを SEMM に登録した後で、承認された証明書で作成されたパッケージを使用する場合にのみ UEFI 設定を変更できます。

証明書を取得する方法は、組織の規模や複雑さによって異なります。

- 通常、エンタープライズ組織は、標準のセキュリティプラクティスに従って証明書を生成するための独自のインフラストラクチャを維持しています。

- 中規模企業や他の企業は、多くの場合、パートナー プロバイダーから証明書を取得します。 このオプションは、IT の専門知識があまりない組織や、専用の IT セキュリティ チームがいない組織に推奨されます。

- または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 詳しくは [、Surface Enterprise 管理モードの証明書要件に関するページをご覧ください](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。 または、PowerShell を使用して独自の証明書を作成できます。 詳細については [、New-SelfSignedCertificate ドキュメントを参照](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) してください。

Surface UEFI コンフィフィエーターが作成する SEMM パッケージは、証明書で保護する必要があります。 証明書は、UEFI 設定を適用する前に構成ファイルの署名を検証します。 詳細については [、SEMM ドキュメントを参照](https://docs.microsoft.com/surface/surface-enterprise-management-mode) してください。
 
### SEMM パッケージを作成する

1. 別の PC に、前にダウンロードした Surface UEFI コンフィエーター ツールをインストールします。

1. Surface UEFI コンフィエーターを開き、[スタート] を選択 **します**。

   ![Surface UEFI コンフィエーターのスタート画面。](images/shm-fig2.png)
   
1. **[Surface デバイス] を選択し**、[次へ] を**選択します**。

   ![スクリーン ショットは、選択されている Surface Devices オプションを示しています。](images/shm-fig3.png)
  
1. 構成パッケージ **を選択します**。

   ![Screenshot shows "Select Configuration Package" selected.](images/shm-fig4.png)
  
1. [証明書 **の保護] を選択します**。

   ![Screenshot shows were to choose "Select Certificate Protection".](images/shm-fig5.png)

   証明書 .pfx ファイルを追加するように求めるメッセージが表示されます。

   ![スクリーンショットは、証明書ファイルを追加する場所を示しています。](images/shm-fig6.png)
   
1. 証明書のパスワードを入力し **、[OK] を選択します**。

   ![Screenshot shows fields to enter and confirm your certificate password.](images/shm-fig7.png)

1. パスワード **保護を選** び、Surface UEFI にパスワードを追加します。 UEFI を起動するたびに、このパスワードが必要です。 *Surface Hub 2S で使用する UEFI パスワードを設定することを強く推奨します。*

   ![Screenshot shows where to select Password Protection.](images/shm-fig8.png)
   
1. UEFI パスワードを設定し **、[OK] を選択します**。

   > [!IMPORTANT]
   > パスワードは、Surface Hub を管理する IT 管理者がアクセスできる安全な場所に保存します。 *このパスワードが失われた場合は、復元できません。*

   ![Screenshot shows where you set the UEFI password.](images/shm-fig9.png)

1. **[Surface Hub 2S] を選択し、[次**へ] を**選択します**。

    ![Screenshot shows where to select Surface Hub 2S.](images/shm-fig10.png)
   
1. もう一 **度 [次へ] を選択** します。

    ![Screenshot shows to select Next under "Choose which components".](images/shm-fig10a.png)

1. Windows 10 Pro または Enterprise のインストールを許可するには **、EnableOsMigration**を有効にし、[次へ] を選択 **します**。

    ![Screenshot shows where to select Enable O S Migration.](images/shm-fig11.png)
    
    ![Screenshot shows where to set Enable OS Migration to on.](images/shm-fig12.png)

### SEMM 登録を管理する

SEMM へのデバイスの登録は、デバイスの管理方法に影響します。 たとえば、SEMM パッケージを適用すると、デバイスの UEFI メニューですべての UEFI 設定が使用できなくなった (ロックされます)。 PXE ブートの **IPv6 などのその他の設定の** 既定値も使用できません。

移行後に UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスを登録解除します。 別の SEMM パッケージを適用して UEFI 設定を変更する場合は、新しい SEMM パッケージをビルドするときに元の証明書を使用する必要があります。 UEFI コンフィグレータ ツールを使用し **、EnableOSMigration**を*オフのままにします*(元の移行手順ではオンではありません)。 **

#### パートナーと連携する場合

会社が Surface Hub 2 の Windows 10 Pro または Enterprise への移行をアウトソーシングしている場合は、パートナーに SEMM 証明書、SEMM パッケージ、UEFI パスワードを転送する必要がある場合があります。 または、ハブを移行した後、SEMM からすぐに登録を解除できます。 この手順では、UEFI のローカル管理とデバイスの別のパーティへの転送を有効にします。 ただし、移行後に構成できる UEFI パスワードを使用することを強く推奨します。 詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://docs.microsoft.com/surface/manage-surface-uefi-settings)。 

#### Windows 10 Team にロールバックする

この記事で後述するように、移行後にデバイスを Windows 10 Team に復元する場合は、まず SEMM から Hub を登録解除することをお勧めします。 [](#to-roll-back-to-windows-10-team) 詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。

#### SEMM パッケージを USB ドライブに保存する

1. USB ドライブを PC に接続します。
1. [ **ハブ 2S] を選択し、[** 次へ] を **選択します**。

   ![Screenshot shows where to select Hub 2S](images/shm-fig13.png)

   > [!WARNING]
   > SEMM パッケージをビルドすると、USB ドライブ上のすべての既存のデータが消去されます。 SEMM パッケージをビルドする前に、USB ドライブから必要なファイルを削除します。
   
1. [ビルド **] を選択します**。

   ![Screenshot shows where to select Build.](images/shm-fig14.png)

1. このページのスクリーンショットをキャプチャし、[終了] を選択 **します**。 SEMM パッケージの準備ができました。 このファイルには、SEMM パッケージ *DfciUpdate.dfi* と、証明書の拇印の最後の 2 文字である *SEMM*拇印を含むテキスト ファイルが含まれます。

   ![Screenshot shows where to select End.](images/shm-fig15.png)
   
4. 証明書の拇印の最後の 2 文字を保存します。 Surface Hub 2S でパッケージを適用するときに SEMM をアクティブ化するには、これらの文字が必要です。

### Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 のドライバーとファームウェアを使って USB フラッシュ ドライブを読み込む

Windows 10 Pro または Enterprise イメージ (バージョン *1903* 以降) をインストールするには、次のいずれかのオプションを使用します。

- 現在のイメージング ソリューション。

- [Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator). このツールを使って、起動可能な Windows 10 イメージを作成します。 イメージには、現在のすべての Windows 10 更新プログラム、Microsoft Office、その他のアプリ、および必要なドライバーとファームウェアを含めできます。

- Windows 10 Pro または Enterprise イメージを含む USB フラッシュ ドライブ。 次に、Surface Hub 2 に [Windows 10 Pro と Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) のドライバーとファームウェアをインストールします。
 
次の手順は、インストール メディアから USB フラッシュ ドライブを作成し、SEMM パッケージ ファイル、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 MSI ファイルに追加する方法を示しています。 別の展開方法を使用する場合は [、Surface Hub 2S](#update-uefi-on-surface-hub-2s-to-enable-os-migration) の Update UEFI に移動して、この記事の OS 移行セクションを有効にします。

> [!NOTE]
> インストールが完了したら、既存の Windows 10 Team ライセンスとは別に、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。

1. Windows 10 Pro インストールを作成するには、Windows 10 のダウンロードでメディア作成ツールをダウンロードする手順 [に従います](https://www.microsoft.com/software-download/windows10)。 Windows 10 Enterprise をダウンロードするには、Microsoft ボリューム ライセンス サービス センター [にアクセスします](https://www.microsoft.com/licensing/servicecenter/default.aspx)。

1. 新しい USB ストレージ ドライブを挿入します。
1. メディア作成ツールを開き、[インストール メディアの作成] **を**選択し、[次へ] を選択 **します**。

   ![スクリーンショットは、インストール メディアを作成するオプションを示しています。](images/shm-fig16.png)
   
3. 言語を選択し **、Windows 10 と 64** ビット **(x64) を選択します**。 次に、[次へ] を **選択します**。

   ![Screenshot shows where you select the language, O S edition, and architecture type.](images/shm-fig17.png)
   
4. USB **フラッシュ ドライブを選択し、[** 次へ] を **選択します**。

   ![Screenshot shows where to select U S B flash drive.](images/shm-fig18.png)
   
5. ダウンロードが完了したら、[完了] を選択 **します**。

   ![画面は、U S B ドライブの準備が完了したと報告し、[完了] ボタンが含まれています。](images/shm-fig19.png)
   
6. SURFACE Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS の SEMM パッケージ ファイルとドライバーとファームウェアを、Windows 10 イメージを含む USB フラッシュ ドライブ *(BOOTME)* のルートにコピーします。 BOOTME USB ドライブには、次の情報が含まれている必要があります。

    - Windows 10 の起動可能なイメージ。
    
    - SEMM パッケージ ファイル。USB ドライブのルートにコピーされます。
    
      - *DfciUpdate.dfi*.
      - SEMM 拇印を含むテキスト ファイル。 (この例では、ファイルは次 *SurfaceUEFI_2020Aug25_1058.txt*です)。自動的に生成される日付とタイム スタンプは、Surface UEFI コンフィエーターを使用してファイルを作成した日付に対応します。

   - Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)。 このファイルを USB ドライブのルートにコピーします。

### Surface Hub 2S で UEFI を更新して OS の移行を有効にする

1. BOOTME ドライブを Surface Hub 2S の USB-A ポートに挿入します。 必要なコンテンツの一覧については、前のセクションを参照してください。

1. UEFI を起動するには:

   1. Surface Hub 2S をオフ (シャットダウン) します。
   1. 音量 + を **長押**しし、電源ボタンを長押しします。 UEFI メニュー **が表示されるまで** 、Volume + を保持し続ける。
   
      ![図面には、音量ボタンと電源ボタンが表示されます。](images/shm-fig20.png)
      
3. デバイスが再起動したら、前に作成した UEFI パスワードを入力します (該当する場合は推奨)。

   ![システム パスワード画面。](images/shm-fig22.png)
   
4. UEFI メニューから [管理] を **選択します**。 次に  **、[USB からインストール] を選択します**。

   ![Screenshot shows where to select Management and then "Install from U S B".](images/shm-fig21.png)
   
5. 次 **の図に示すように**、[今すぐ再起動] を選択します。 デバイスが再起動します。 ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンされます。

   ![Screenshot shows a message prompting you to restart.](images/shm-fig25.png)
   
6. 電源ボタンを押して離します。 表示される赤いダイアログ ボックスで、Surface Enterprise 管理モードのアクティブ化を選択します。

7. 2 文字の証明書の拇印と UEFI 設定パスワードを入力します。 **[OK] を選択します**。

   ![Screenshot shows the confirm-activation dialog box where you enter your two-character certificate thumbprint and your UEFI settings password.](images/shm-fig23.png)
 
   > [!NOTE]
   > デバイスで SEMM をアクティブ化すると、新しい UEFI 設定 **EnableOSMigration が** 適用されます。 Windows 10 Team にアクセスできなくなりました。 代わりに、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。

   デバイスが再起動します。 画面の中央に白いロゴが表示され、もう一度シャットダウンされます。

### Windows 10 Pro または Enterprise のインストール

1. 起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-A ポートにまだ存在しない場合は、ここで挿入します。 次に、電源ボタンを押して離します。

    デバイスが起動すると、画面の中央に白いロゴが表示されます。 次に、回転する円が白いロゴの下に表示されます。

3. Surface デバイスが自動的に USB ドライブを起動しない場合は、デバイスの電源を切ります (電源コードを取り外してから、もう一方の電源を差し込む)。 電源コードを再度接続すると、数秒後にデバイスが起動します。 次に、画面の中央に白いロゴが表示されます。

    デバイスが有効でなかった場合は、電源ボタンを押して離します。 画面の中央にロゴが表示された直後に、白いロゴの下に回転する円が表示されるまでボリューム ボタンを長押しします。
 
   ![音量ボタンと電源ボタンの画像。](images/shm-fig26.png)
   
4. Out-Of-Box Experience (OOBE) のセットアップが開始したら、指示に従って Windows 10 Pro または Enterprise (バージョン 1903 以降) をインストールします。

### Surface Hub 2 のドライバーとファームウェアをインストールする

Surface Hub 2 を最新の情報に更新するには [、Windows 10 Pro](https://www.microsoft.com/download/details.aspx?id=101974)と Enterprise のドライバーとファームウェアをインストールします。 その後、デバイスを再起動します。 Surface を 1 時間有効にし、再起動します。 2 回目の再起動を求めるメッセージは表示されません。 この一時停止と追加の再起動により、ファームウェアが完全に更新されます。
 
## 推奨設定を構成する

個人の生産性向上デバイスとして Surface Hub 2S を構成するには [、「Surface Hub 2 で Windows 10 Pro または Enterprise](surface-hub-2-post-install.md)を構成する」を参照してください。

> [!NOTE]
>この記事で説明されている手順に従って、デバイスを Windows 10 Pro または Enterprise for Surface Hub 2 に正常に移行できない場合は [、Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)サポートにお問い合わせください。

## Windows 10 Team にロールバックする

デバイスを Windows 10 Team に復元する場合は [、「Surface Hub 2S](surface-hub-2s-recover-reset.md)のリセットと回復」を参照してください。

> [!NOTE]
> Windows 10 Team にロールバックする前に、まず SEMM から Surface Hub を登録解除してください。 詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。

## バージョン履歴

次の表に、この記事の変更点を示します。

| バージョン | 日付               | 説明                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1.4  | 2020 年 12 月 14 日 | 「Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア」用の MSI ファイルのインストールに関する詳細な情報を提供します。システムの状態によっては、2 回目の再起動が必要になる場合があります。 [](#install-surface-hub-2-drivers-and-firmware)                                                          |
| v. 1.3  | 2020 年 12 月 3 日 | SEMM 登録の管理 [に関するガイダンスを更新しました](#manage-semm-enrollment)。                                                       |
| v. 1.2  | 2020 年 9 月 29 日 | 使いやすさのフィードバックに対処するその他の更新プログラム。                                                        |
| v. 1.1  | 2020 年 9 月 15 日 | 新しい OS をインストールする場合のライセンス要件を明確に示す追加のメモを紹介に追加しました。 |
| v. 1.0  | 2020 年 9 月 1 日  | 新しい記事。                                                                                           |
