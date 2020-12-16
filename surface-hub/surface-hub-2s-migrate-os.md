---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
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
ms.openlocfilehash: c2851505b3595ea768217de443676b45cc01a9ae
ms.sourcegitcommit: efc38524f81238e0c36371f462eb57123e46d09b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "11228558"
---
# Surface Hub 2 の Windows 10 Pro または Enterprise に移行する

- [記事のバージョン履歴](#version-history)

Surface Hub 2S には、Windows 10 Team がプレインストールされています。 このカスタマイズされた Windows 10 エディションは、会議室環境でのコラボレーションを容易にするように設計されています。 これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub 2S を使用するオプションが提供されます。 

> [!IMPORTANT]
>一般的なアップグレードや移行とは異なり、このプロセスでは、この記事で説明するように、標準的な手順に従う必要があります。 続行する[前に、ソリューション コンポーネントと](#solution-components)[移行とインストールのワークフロー](#migration-and-installation-workflow-summary)を確認します。


> [!NOTE]
> Windows 10 Pro または Enterprise をインストールする場合は、既存の Windows 10 Team ライセンスとは別の新しいライセンスが必要です。 


別の PC とダウンロード可能なツール Surface UEFI コンフィケーターを使って、Windows 10 Team からの移行 *を開始します*。 このツールを使って、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。  

Surface UEFI コンフィエーターは、Surface Enterprise 管理モード (SEMM) へのインターフェイスとして機能します。 企業環境の Surface デバイスでファームウェア設定の一元管理を容易にするように設計されています。 詳細については <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> 、Microsoft SEMM ドキュメントを参照してください。</a>
 

## ソリューション コンポーネント

- Windows 10 Team オペレーティング システムを実行している Surface Hub 2S デバイス
- Windows 10 を実行している個別のデバイス
- SEMM パッケージを作成する Surface UEFI 構成ツール
- Windows 10 Pro または Enterprise OS イメージ バージョン 1903 以降
- 16 GB のストレージ、FAT32 形式の 2 つの USB ドライブ
- Surface Hub 2 Microsoft Windows インストーラー (MSI) ファイル上の Windows 10 Pro および Enterprise OS のドライバーとファームウェア
- インターネット接続
- イメージング ソリューション (オプション)

 
## 移行とインストールのワークフローの概要

| ステップ  | 操作                                                                                                 | まとめ                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認します。](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | UEFI バージョンが 694.2938.768.0 以降である必要があります。                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードします。](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | [Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> **Tools for IT] ページで、[** </a> ダウンロード] を**選択します**。 次に **、Surface UEFI コンフィエーターを選択してダウンロードします。MSI ファイルを** 作成し、別の PC にインストールします。 Surface Hub 2 MSI ファイルに <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Windows 10 Pro および Enterprise OS のドライバーとファームウェアをダウンロードします。</a> 手順 5 で使用するために保存します。 |
| 3 | [SEMM 証明書を準備します。](#prepare-the-semm-certificate)                                                                          | Surface UEFI コンフィエーターを実行するために必要な証明書を準備します。 または、現在の証明書を使用します。                                                                                                                                                                                                                                                                                                      |
| 4 | [SEMM パッケージを作成します。](#create-a-semm-package)                                                                               | Surface UEFI コンフィエーターを起動して、USB ドライブに SEMM パッケージを作成します。このパッケージには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。 これらの SEMM パッケージ ファイルを PC 上のフォルダーにコピーします。                                                                                                                                                                                          |
| 5 | [Surface Hub 2 で Windows 10 Pro および Enterprise OS 用の Windows 10 イメージ、SEMM パッケージ、ドライバーとファームウェアを含む USB フラッシュ ドライブを準備します。](#prepare-a-usb-flash-drive-that-contains-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Windows 10 イメージを含む単一の USB ドライブを作成します。 この例では、ドライブの名前は *BOOTME です*。 Surface Hub 2 (手順 2) と SEMM パッケージ ファイル (手順 4) で Windows 10 Pro および Enterprise OS のドライバーとファームウェアを *BOOTME* ドライブに追加します。                                                                                                                                                                                                  |
| 6 | [Surface Hub 2S で UEFI を更新して、OS の移行を有効にします。](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | *BOOTME ドライブを使*って Surface Hub 2S を UEFI メニューで起動し、SEMM パッケージをインストールします。|
| 7 | [Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。](#install-windows-10-pro-or-enterprise)                                        | *BOOTME ドライブを使*って、Windows 10 Pro または Enterprise バージョン 1903 以降をインストールします。                                                                                                                                                                                                                                                                                 |
| 8 | [Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 にインストールします。](#install-surface-hub-2-drivers-and-firmware)                                        | デバイスに最新の更新プログラムとドライバーがインストールされている必要がある場合は、Surface Hub 2 MSI ファイルに Windows 10 Pro および Enterprise OS のドライバーとファームウェア <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> をインストールします。</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Surface Hub 2S を個人用生産性デバイスとして完全に構成します。](#configure-recommended-settings)                                        |  推奨設定とアプリケーションを有効にして、個人用生産性デバイスとして Surface Hub 2S を最適化します。                                                                                                                                                                                                                                                                    |

### Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する

Surface Hub を Windows 10 Team から Windows 10 Desktop に移行する前に *、694.2938.768.0*以上の UEFI バージョンが必要です。
 
**システムで UEFI バージョンを確認するには、次の手順を実行します。**

1. Surface Hub 2S ホーム ページで、[スタート]**を選択し**、Surface アプリ (すべてのアプリの Surface)**を開**  >  **きます**。

2. Surface **を選び** 、デバイス上の現在の UEFI バージョンを含む Surface Hub に関する情報を表示します。 
   - 次の図に示すように *、UEFI バージョンが 694.2938.768.0* 以降の場合は、SEMM パッケージを作成して OS の移行を有効にできます。

       ![Surface アプリの [Your Surface] ページを示すスクリーンショット。](images/shm-fig1.png)
 
   - UEFI バージョンがバージョン 694.2938.768.0 より前の場合は、Window 10 Team 2020 Update Bare Metal Recovery (BMR) イメージをインストールするか、Windows Update を使用して、現在のバージョンを入手する必要があります。
   
**Windows Update を使って UEFI を更新するには:**

1. Surface Hub 2S で、管理者としてサインイン **します**。 
    >[!Note]
    > ユーザー名または管理者パスワードが分からない場合は、デバイスをリセットする必要があります。 詳しくは <a href="https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset" target="_blank"> 、「Surface Hub 2S のリセットと回復」をご覧ください。</a>

1. [すべてのアプリ**の設定の**  >  **更新と**  >  **セキュリティ**  >  **] Windows Update に移動し**、すべての更新プログラムをインストールします。 
1. デバイスを再起動します。 
1. Surface アプリを使って UEFI バージョンを確認します。 
1. この時点で、UEFI バージョンがまだバージョン 694.2938.768.0 以降ではない場合は、上記の手順を繰り返し実行するか、Windows 10 Team 2020 Update Bare Metal Recovery (BMR) イメージをインストールして最新の UEFI を取得できます。

**ベア メタル回復 (BMR) イメージを使用して UEFI を更新するには:**

1.  Surface の回復サイト [に移動し、[Surface](https://support.microsoft.com/surfacerecoveryimage) **Hub 2S] を選択します。**
3.  ハブのシリアル番号を入力します (電源接続の横のハブの背面にあります)。
4.  指示に従って、Windows 10 Team 2020 Update をインストールして、フォーマットされた USB ドライブにイメージをダウンロードします。
5.  更新が完了し、デバイスが初めて OOBE に入った後は、OOBE を完了する必要はなんか、UEFI バージョンが更新されます。 代わりに、画面がオフになるまで電源ボタンを押し続け、デバイスの電源を切ります。 

### Surface UEFI コンフィエーターと Surface Hub 2 のドライバーとファームウェアをダウンロードする

別の PC の場合:

1. [Surface <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Tools for IT] ページで、[ </a> ダウンロード] を **選択します**。  
1. Surface UEFI Configurator MSI ファイルを選択してダウンロードし、別の PC にインストールします。 Windows 10 Team エディションがインストールされている間、Surface Hub 2S で Surface UEFI コンフィエーター ツールを実行できない。

1. Surface <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Hub 2 Drivers and Firmware Windows Installer MSI ファイルをダウンロードします </a> 。 このファイルは、新しいオペレーティング システムをインストールするときに使用します。

### SEMM 証明書を準備する

Surface UEFI コンフィエーターを使用したことがない場合は、証明書を準備する必要があります。 この証明書により、デバイスを SEMM に登録した後で、承認された証明書で作成されたパッケージを使用する場合にのみ UEFI 設定を変更できます。 

証明書を取得する方法は、組織の規模や複雑さによって異なります。

- 通常、エンタープライズ組織は、標準のセキュリティプラクティスに従って証明書を生成するための独自のインフラストラクチャを維持しています。

- 中規模企業などでは、パートナー プロバイダーから証明書を取得する場合があります。 このオプションは、十分な IT 専門知識や専用の IT セキュリティ チームがいない組織に推奨されます。

- または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 詳しくは <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements" target="_blank"> 、Surface Enterprise 管理モードの証明書要件に関するページをご覧ください </a> 。 または、PowerShell を使用して独自の証明書を作成できます。 詳細については <a href="https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate" target="_blank"> 、New-SelfSignedCertificate ドキュメントを参照 </a> してください。

Surface UEFI コンフィフィエーターが作成する SEMM パッケージは、証明書で保護する必要があります。 証明書は、UEFI 設定を適用する前に構成ファイルの署名を検証します。 詳細については <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> 、SEMM ドキュメントを参照してください </a> 。
 
 
### SEMM パッケージを作成する

1. 別の PC に、前にダウンロードした Surface UEFI コンフィエーター ツールをインストールします。 

2. Surface UEFI コンフィエーターを開き、[スタート] を選択 **します**。

   ![Surface UEFI コンフィエーターを開きます。](images/shm-fig2.png)
   
3. **[Surface デバイス] を選択し**、[次へ] を**選択します**。

   ![[Surface デバイス] を選択します。](images/shm-fig3.png)
  
4. 構成パッケージ **を選択します**。

   ![[構成パッケージ] を選択します。](images/shm-fig4.png)
  
5. [証明書 **の保護] を選択します**。

   ![[証明書の保護] を選択します。](images/shm-fig5.png)

   証明書 .pfx ファイルを追加するように求めるメッセージが表示されます。

   ![証明書を追加します。](images/shm-fig6.png)
   
7. 証明書のパスワードを入力し **、[OK] を選択します**。

   ![証明書のパスワードを入力し、[OK] を選択します。](images/shm-fig7.png)

8. パスワード **保護を選** び、Surface UEFI にパスワードを追加します。 UEFI を起動するたびに、このパスワードが必要です。 Surface ** Hub 2S で使用する UEFI パスワードを設定することを強く推奨します。

   ![[パスワード保護] を選択します。](images/shm-fig8.png)
   
9. UEFI パスワードを設定し **、[OK] を選択します**。

   > [!IMPORTANT]
   > パスワードは、Surface Hub を管理する IT 管理者がアクセスできる安全な場所に保存します。 パスワードが失われた場合は、復元できません。 

   ![UEFI パスワードを入力します。](images/shm-fig9.png)

10. **[Surface Hub 2S] を選択し、[次**へ] を**選択します**。

    ![[Surface Hub 2S] を選択します。](images/shm-fig10.png)
   
11. **[次へ]** を選択します。

    ![[次へ] を選択します。](images/shm-fig10a.png)

12. Windows 10 Pro または Enterprise のインストールを許可するには **、EnableOsMigration**を有効にし、[次へ] を選択 **します**。

    ![[O S 移行を有効にする] を選択します。](images/shm-fig11.png)
    
    ![[OS 移行を有効にする] を [オン] に設定します。](images/shm-fig12.png)

### SEMM 登録の管理

SEMM へのデバイスの登録は、今後のデバイスの管理方法に影響します。 たとえば、SEMM パッケージを適用した後、デバイスの UEFI メニューで、すべての UEFI 設定を使用できません (ロックされています)。 PXE ブートの **IPv6 などのその他の設定の** 既定値も使用できません。 

移行後に UEFI 設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスを登録解除します。 別の SEMM パッケージを適用して UEFI 設定を変更する場合は、新しい SEMM パッケージをビルドするときに元の証明書を使用する必要があります。 UEFI コンフィグレータ ツールを使用し **、EnableOSMigration** をオフのままにします (元の移行手順に示すようにオンではありません)。

#### パートナーとの連携

会社が Surface Hub 2 の Windows 10 Pro または Enterprise への移行をアウトソーシングしている場合は、パートナーに SEMM 証明書、SEMM パッケージ、および UEFI パスワードを転送する必要がある場合があります。  または、ハブを移行した後、SEMM からすぐに登録を解除できます。この場合、UEFI のローカル管理とデバイスの別のパーティへの転送が可能になります。 それでも、移行後に構成できる UEFI パスワードを使用することを強く推奨します。 詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://docs.microsoft.com/surface/manage-surface-uefi-settings)。 

#### Windows 10 Team へのロールバック

移行後に、後述するようにデバイスを Windows 10 Team[](#roll-back-to-windows-10-team)に復元する場合は、まず SEMM から Hub を登録解除してください。 詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。


#### SEMM パッケージを USB ドライブに保存する

1. USB ドライブを PC に接続します。 
1. [ **ハブ 2S] を選択し、[** 次へ] を **選択します**。

   ![USB の選択](images/shm-fig13.png)

   > [!WARNING]
   > SEMM パッケージをビルドすると、USB ドライブ上のすべての既存のデータが消去されます。 SEMM パッケージを作成する前に、保存する USB ドライブからファイルを削除します。
   
2. [ビルド **] を選択します**。

   ![[ビルド] を選択します。](images/shm-fig14.png)

3. このページのスクリーンショットをキャプチャし、[終了] を選択 **します**。 SEMM パッケージの準備ができました。 このファイルには、SEMM パッケージ *DfciUpdate.dfi* と、SEMM 拇印 (証明書の拇印の最後の 2 文字) を含むテキスト ファイルが含まれます。

   ![[終了] を選択します。](images/shm-fig15.png)
   
4. 証明書の拇印の最後の 2 文字を保存します。 Surface Hub 2S でパッケージを適用するときに SEMM をアクティブ化するには、これらの文字が必要です。

### Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 のドライバーとファームウェアを含む USB フラッシュ ドライブを準備する

Windows 10 Pro または Enterprise イメージ (バージョン 1903 以降) をインストールするには、次のいずれかのオプションを使用します。

- 現在のイメージング ソリューション。

- <a href="https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator" target="_blank"> Surface Deployment Accelerator </a> . このツールを使って、起動可能な Windows 10 イメージを作成します。 イメージには、現在のすべての Windows 10 更新プログラム、Office、選択した他のアプリ、必要なドライバーとファームウェアを含めできます。 

- Windows 10 Pro または Enterprise イメージを含む USB フラッシュ ドライブ。 次に <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> 、Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 にインストールします </a> 。
 
次の手順では、インストール メディアから USB フラッシュ ドライブを作成し、SEMM パッケージ ファイルと Windows 10 Pro および Enterprise OS のドライバーとファームウェアを Surface Hub 2 MSI ファイルに追加する方法について説明します。 他の展開方法を使用している場合は [、Surface Hub 2S](#update-uefi-on-surface-hub-2s-to-enable-os-migration) の Update UEFI に移動して、この記事の OS 移行セクションを有効にします。

> [!NOTE]
> インストールが完了したら、既存の Windows 10 Team ライセンスとは別に、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。

1. Windows 10 Pro インストールを作成するには、Windows 10 のダウンロード ページで、指示に従ってメディア作成ツール <a href="https://www.microsoft.com/software-download/windows10" target="_blank"> </a> をダウンロードします。 Windows 10 Enterprise をダウンロードするには、Microsoft ボリューム ライセンス サービス センター <a href="https://www.microsoft.com/licensing/servicecenter/default.aspx" target="_blank"> にアクセスします </a> 。

2. 新しい USB ストレージ ドライブを挿入します。 
1. メディア作成ツールを開き、[インストール メディアの作成] **を**選択し、[次へ] を選択 **します**。

   ![インストール メディアを作成します。](images/shm-fig16.png)
   
3. 言語を選択し **、Windows 10 と 64** ビット **(x64) を選択します**。 次に、[次へ] を **選択します**。

   ![言語を選択し、Windows 10 と 64 ビットを選択します。 次に、[次へ] を選択します。](images/shm-fig17.png)
   
4. USB **フラッシュ ドライブを選択し、[** 次へ] を **選択します**。

   ![[U S B フラッシュ ドライブ] を選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. ダウンロードが完了したら、[完了] を選択 **します**。

   ![[完了] を選択します。](images/shm-fig19.png)
   
6. SURFACE Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS の SEMM パッケージ ファイルとドライバーとファームウェアを、Windows 10 イメージを含む USB フラッシュ ドライブ *(BOOTME)* のルートにコピーします。 BOOTME USB ドライブには次が含まれる。

    - Windows 10 の起動可能なイメージ。
    
    - SEMM パッケージ ファイル (USB ドライブのルートにコピー)。
    
      - *DfciUpdate.dfi*.
      - SEMM 拇印を含むテキスト ファイル。 (この例では、ファイルは次 *SurfaceUEFI_2020Aug25_1058.txt*です)。自動的に生成される日付のタイム スタンプは、Surface UEFI コンフィエーターを使用してファイルを作成した日付に対応します。

   - Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)。 このファイルを USB ドライブのルートにコピーします。

### Surface Hub 2S で UEFI を更新して OS の移行を有効にする

1. BOOTME ドライブを Surface Hub 2S の USB-A ポートに挿入します。 必要なファイルの一覧については、前のセクションを参照してください。

2. UEFI を起動するには:

   1. Surface Hub 2S をオフ (シャットダウン) します。
   1. 音量 + を **長押**しし、電源ボタンを長押しします。
   1. UEFI メニュー **が表示されるまで** 、Volume + を保持し続ける。
   
      ![UEFI メニューが表示されるまで、音量を上げボタンを長押しします。](images/shm-fig20.png)
      
3. デバイスが再起動したら、前に作成した UEFI パスワードを入力します (該当する場合は、強く推奨)。

   ![UEFI パスワードを入力します。](images/shm-fig22.png)
   
4. UEFI メニューで、USB から **[管理**  >  **インストール] を選択します**。

   ![[管理] を選択し、[U S B] から [インストール] を選択します。](images/shm-fig21.png)
   
5. 次 **の図に示すように**、[今すぐ再起動] を選択します。 デバイスが再起動します。 ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンします。

   ![[今すぐ再起動] を選択します。](images/shm-fig25.png)
   
6. 電源ボタンを押して離します。 表示される赤いウィンドウで、Surface Enterprise 管理モードをアクティブにします。 

7. 2 文字の証明書の拇印と UEFI 設定パスワードを入力します。 **[OK] を選択します**。

   ![2 文字の証明書の拇印と UEFI 設定パスワードを入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > デバイスで SEMM をアクティブ化すると、新しい UEFI 設定 **EnableOSMigration が** 適用されます。 Windows 10 Team にアクセスできなくなりました。 代わりに、次の手順に進み、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。 

   デバイスが再起動します。 画面の中央に白いロゴが表示され、もう一度シャットダウンされます。

### Windows 10 Pro または Enterprise のインストール

1. 起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-A ポートにまだ存在しない場合は、ここで挿入します。 次に、電源ボタンを押して離します。 

    デバイスが起動すると、画面の中央に白いロゴが表示されます。 次に、白いロゴの下に回転する円が表示されます。

3. デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切ります (電源コードを取り外してから、もう一方の電源を差し込む)。 電源コードを再度接続すると、数秒後にデバイスが起動します。 次に、画面の中央に白いロゴが表示されます。 

    デバイスが有効でなかった場合は、電源ボタンを押して離します。 画面の中央にロゴが表示された直後に、白いロゴの下に回転する円が表示されるまでボリューム ボタンを長押しします。
 
   ![U S B ドライブから Windows 10 を起動します。](images/shm-fig26.png)
   
4. Out-Of-Box Experience (OOBE) のセットアップが開始したら、指示に従って Windows 10 Pro または Enterprise (バージョン 1903 以降) をインストールします。

### Surface Hub 2 のドライバーとファームウェアをインストールする

デバイスに最新の更新プログラムとドライバーが含まれていますので、Surface Hub 2 に Windows 10 Pro および Enterprise OS のドライバーとファームウェアを <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> インストールします </a> 。 ドライバーとファームウェア MSI のインストール後、デバイスを再起動します。 次に、ハブの電源を再び入れ、PC の電源を 1 時間保持し、デバイスを再起動します。 2 回目の再起動を求めるメッセージは表示されません。 Windows 10 Pro または Enterprise に移行する前のコンピューターの状態によっては、すべてのファームウェアが更新された状態を確認するために、この 2 番目の手順が必要になる場合があります。
 
## 推奨設定を構成する

個人の生産性向上デバイスとして Surface Hub 2S を完全に構成するには、「Surface Hub 2 で Windows 10 Pro または Enterprise を構成する」を参照 <a href="surface-hub-2-post-install.md" target="_blank"> してください </a> 。

> [!NOTE]
>この記事で説明されている手順で、デバイスを Windows 10 Pro または Enterprise for Surface Hub 2 に正常に移行できない場合は、Surface Hub サポートにお問い <a href="https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support" target="_blank"> 合わせください </a> 。

## Windows 10 Team にロールバックする

デバイスを Windows 10 Team に復元する場合は、「Surface Hub 2S のリセットと回復」 <a href="surface-hub-2s-recover-reset.md" target="_blank"> を参照してください </a> 。

> [!NOTE]
> Windows 10 Team にロールバックする前に、まず SEMM から Hub を登録解除してください。 詳細については [、「SEMM からの Surface デバイスの登録解除」を参照してください](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm)。

## バージョン履歴

次の表に、この記事の変更点を示します。

| バージョン | 日付               | 説明                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1.4  | 2020 年 12 月 14 日 | 「Surface Hub 2 の Windows 10 Pro および Enterprise OS のドライバーとファームウェア」用の MSI ファイルのインストールに関する詳細な情報を提供します。システムの状態によっては、2 回目の再起動が必要になる場合があります。 [](#install-surface-hub-2-drivers-and-firmware)                                                          |
| v. 1.3  | 2020 年 12 月 3 日 | SEMM 登録の管理 [に関するガイダンスを更新しました](#managing-semm-enrollment)。                                                       |
| v. 1.2  | 2020 年 9 月 29 日 | 使いやすさのフィードバックに対処するその他の更新プログラム。                                                        |
| v. 1.1  | 2020 年 9 月 15 日 | 新しい OS をインストールする場合のライセンス要件を明確に示す追加のメモを紹介に追加しました。 |
| v. 1.0  | 2020 年 9 月 1 日  | 新しい記事。                                                                                           |
