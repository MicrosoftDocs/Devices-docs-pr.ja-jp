---
title: Surface Hub 2 の Windows 10 Pro または Enterprise に移行する
description: この記事では、Surface Hub 2 上の Windows 10 Team から Windows 10 Pro または Windows 10 Enterprise に移行する方法について説明します。
keywords: Surface Hub デスクトップ、Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/13/2020
ms.localizationpriority: Medium
ms.openlocfilehash: d1099da397e47ad1ea44645623dce48498259eaa
ms.sourcegitcommit: 5c396f37ed90f81373b9fdf8464cb9163f2797d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "11168576"
---
# Surface Hub 2 の Windows 10 Pro または Enterprise に移行する

Surface Hub 2S は、Windows 10 チームにプレインストールされています。 この Windows 10 のカスタマイズされたエディションは、会議室環境での共同作業を容易にするために設計されています。 これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub の2S を使用できるようになりました。 

> [!IMPORTANT]
>通常のアップグレードや移行とは異なり、このプロセスでは、この記事で説明するように、規範となる手順を実行する必要があります。 続行する前に、 [ソリューションのコンポーネント](#solution-components) と [移行とインストールのワークフロー](#migration-and-installation-workflow-summary) を確認します。


> [!NOTE]
> Windows 10 Pro または Enterprise をインストールする場合、既存の Windows 10 チームライセンスとは別の新しいライセンスが必要です。 


別の PC とダウンロード可能なツール *SURFACE UEFI コンフィギュレーター*を使用して、Windows 10 チームからの移行を開始します。 このツールを使用して、Surface Hub 2S に適用する新しい UEFI 設定を含むパッケージを作成します。  

Surface UEFI コンフィギュレーターは、Surface Enterprise 管理モード (SEMM) のインターフェイスとして動作します。 企業環境の Surface デバイスでのファームウェア設定の一元管理を容易にするように設計されています。 詳細については、「 <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> Microsoft SEMM ドキュメント」を参照してください。</a>
 

## ソリューションのコンポーネント

- Windows 10 Team オペレーティングシステムを実行している Surface Hub 2S デバイス
- Windows 10 を実行している別のデバイス
- SEMM パッケージを作成するための Surface UEFI コンフィギュレーターツール
- Windows 10 Pro または Enterprise OS イメージ、バージョン1903以降
- 16 GB の記憶域を持つ2つの USB ドライブ、FAT32 形式
- Surface Hub 2 の Microsoft Windows Installer (MSI) ファイル上の Windows 10 Pro および Enterprise OS 用のドライバーとファームウェア
- インターネット接続
- イメージングソリューション (オプション)

 
## 移行とインストールワークフローの概要

| ステップ  | 操作                                                                                                 | まとめ                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 件 | [Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認します。](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | UEFI バージョンが694.2938.768.0 以降であることを確認します。                                                                                                                                                                                                                                                                                                                                                      |
| 両面 | [Surface UEFI コンフィギュレーターおよび Surface Hub 2 のドライバーとファームウェアをダウンロードします。](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | [ <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> **Surface TOOLS for IT** ] ページで </a> 、[**ダウンロード**] を選びます。 次に、Surface UEFI コンフィギュレーターを選択してダウンロードし **ます。MSI ファイル** を別の PC にインストールします。 <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Surface Hub 2 MSI ファイル上の Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをダウンロードします。</a> 手順5で使用するために保存します。 |
| - | [SEMM 証明書を準備します。](#prepare-the-semm-certificate)                                                                          | Surface UEFI コンフィギュレーターの実行に必要な証明書を準備します。 または、現在の証明書を使用します。                                                                                                                                                                                                                                                                                                      |
| 4d | [SEMM パッケージを作成します。](#create-a-semm-package)                                                                               | 開始 Surface UEFI コンフィギュレーターを使用して、USB ドライブ上に SEMM パッケージを作成します。これには、Surface Hub 2S に適用する必要がある構成ファイルが含まれます。 これらの SEMM パッケージファイルを PC 上のフォルダーにコピーします。                                                                                                                                                                                          |
| 個 | [Windows 10 のイメージ、SEMM パッケージ、および Windows 10 Pro とエンタープライズ OS 用の windows 10 Pro およびドライバーとファームウェアを含む USB フラッシュドライブを Surface Hub 2 で準備します。](#prepare-a-usb-flash-drive-that-contains-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Windows 10 イメージを含む USB ドライブを1つ作成します。 この例では、ドライブは *Bootme*という名前になっています。 Surface Hub 2 (手順 2) と SEMM パッケージファイル (手順 4) に Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアを *Bootme* ドライブに追加します。                                                                                                                                                                                                  |
| = | [OS の移行を有効にするには、Surface Hub 2S で UEFI を更新します。](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | *Bootme*ドライブを使って、[UEFI] メニューに Surface Hub 2s を起動し、semm パッケージをインストールします。|
| 日 | [Windows 10 Pro または Enterprise バージョン1903以降をインストールします。](#install-windows-10-pro-or-enterprise)                                        | *Bootme*ドライブを使用して、Windows 10 Pro または Enterprise バージョン1903以降をインストールします。                                                                                                                                                                                                                                                                                 |
| 個 | [Surface Hub 2 で Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアをインストールします。](#install-surface-hub-2-drivers-and-firmware)                                        | デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Surface Hub 2 MSI ファイルに Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをインストールします。</a>                                                                                                                                                                                                                                                                                  |
| ファイブ | [パーソナルの生産性向上デバイスとして Surface Hub 2S を完全に構成します。](#configure-recommended-settings)                                        |  推奨される設定とアプリケーションを有効にして、個人用の生産性デバイスとして Surface Hub の2S を最適化します。                                                                                                                                                                                                                                                                    |

### Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する

Surface Hub を Windows 10 Team から Windows 10 デスクトップに移行する前に、少なくとも *694.2938.768.0*の UEFI バージョンが必要です。
 
システムの UEFI バージョンを確認するには、次の操作を行います。

1. Surface Hub 2s のホームページで、[**開始**] を選び、surface アプリ ([**すべてのアプリ**]  >  **サーフェス**) を開きます。

2. **Surface**を選択して、デバイス上の現在の UEFI バージョンなど、surface Hub に関する情報を表示します。 
   - UEFI バージョンが *694.2938.768.0* 以降の場合は、次の図に示すように、semm パッケージを作成して OS の移行を有効にすることができます。

       ![Surface アプリの Surface ページを示すスクリーンショット。](images/shm-fig1.png)
 
   - UEFI バージョンが *694.2938.768.0*より前のバージョンである場合は、Windows Update を使用して現在のバージョンを取得します。

Windows Update を使用して UEFI を更新するには、次の操作を行います。

1. Surface Hub 2S で、 **管理者**としてサインインします。 
    >[!Note]
    > ユーザー名または管理者パスワードがわからない場合は、デバイスをリセットする必要があります。 詳細については、「 <a href="https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset" target="_blank"> Surface Hub 2s のリセットと回復」を参照してください。</a>

1. [**すべてのアプリ**  >  **設定**  >  の**更新とセキュリティ**  >  **Windows Update**] に移動して、すべての更新プログラムをインストールします。 
1. デバイスを再起動します。 
1. Surface アプリを使用して、UEFI バージョンを確認します。 
2. UEFI バージョンが *694.2938.768.0* 以降になるまで、この手順を繰り返します。
3. 複数回試行しても更新された UEFI が表示されない場合は、 **更新履歴** を確認して、失敗したファームウェアインストールのインスタンスを探してください。 デバイスをリセットする必要がある場合があります (**設定**  >  **更新 & セキュリティ**  >  **リセットデバイス**)。

### ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア

別の PC では、次の操作を行います。

1. [ <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Surface Tools FOR IT] ページで </a> 、[ **ダウンロード**] を選びます。  
1. Surface UEFI コンフィギュレーター MSI ファイルを選択してダウンロードし、別の PC にインストールします。 Surface UEFI コンフィギュレーターツールは、Windows 10 Team edition がインストールされているときに Surface Hub 2S で実行することはできません。

1. <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">Surface Hub 2 ドライバーとファームウェア Windows インストーラー MSI ファイルをダウンロードし </a> ます。 このファイルは、新しいオペレーティングシステムをインストールするときに使用します。

### SEMM 証明書を準備する

Surface UEFI コンフィギュレーターを以前に使用していない場合は、証明書を準備する必要があります。 この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージを使用してのみ UEFI 設定を変更できることを確認します。 

証明書を取得する方法は、組織の規模または複雑さによって異なります。

- 通常、エンタープライズ組織は、標準セキュリティの慣行に従って証明書を生成するために独自のインフラストラクチャを維持します。

- 中規模企業や他のユーザーが、パートナープロバイダーから証明書を取得することを選択する場合があります。 十分な IT 専門知識を持っていない組織や専用の IT セキュリティチームの場合は、このオプションをお勧めします。

- または、PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 詳細については、「 <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements" target="_blank"> Surface Enterprise 管理モードの証明書の要件」を参照してください </a> 。 または、PowerShell を使用して独自の証明書を作成することもできます。 詳しくは、 <a href="https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate" target="_blank"> 新しい自己 Signedcertificate のドキュメントをご覧ください </a> 。

Surface UEFI コンフィギュレーターで作成される SEMM パッケージは、証明書を使ってセキュリティで保護されている必要があります。 UEFI 設定を適用する前に、証明書によって構成ファイルの署名が確認されます。 詳細については、「semm ドキュメント」を参照してください <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> </a> 。
 
 
### SEMM パッケージを作成する

1. 別の PC で、以前にダウンロードした Surface UEFI コンフィギュレーターツールをインストールします。 

2. [Surface UEFI コンフィギュレーター] を開き、[ **開始**] を選びます。

   ![Surface UEFI コンフィギュレーターを開きます。](images/shm-fig2.png)
   
3. [ **Surface Devices**] を選択し、[ **次へ**] を選択します。

   ![[Surface Devices] を選びます。](images/shm-fig3.png)
  
4. [ **構成パッケージ**] を選びます。

   ![[構成パッケージ] を選びます。](images/shm-fig4.png)
  
5. [ **証明書の保護**] を選びます。

   ![[証明書の保護] を選びます。](images/shm-fig5.png)

   証明書 .pfx ファイルを追加するように求められます。

   ![証明書を追加します。](images/shm-fig6.png)
   
7. 証明書のパスワードを入力して、[ **OK]** を選択します。

   ![証明書のパスワードを入力して、[OK] を選択します。](images/shm-fig7.png)

8. Surface UEFI にパスワードを追加するには、[ **パスワードによる保護** ] を選択します。 このパスワードは、UEFI を起動するたびに必要になります。 Surface Hub 2S で使う UEFI パスワードを設定することを *強くお勧め* します。

   ![[パスワードによる保護] を選びます。](images/shm-fig8.png)
   
9. UEFI パスワードを設定して、[ **OK]** を選択します。

   > [!IMPORTANT]
   > Surface Hub を管理する IT 管理者がアクセスできる安全な場所にパスワードを保存します。 パスワードを紛失した場合、復元することはできません。 

   ![UEFI パスワードを入力します。](images/shm-fig9.png)

10. [ **Surface Hub 2s**] を選択し、[ **次へ**] を選択します。

    ![[Surface Hub 2S] を選びます。](images/shm-fig10.png)
   
11. **[次へ]** を選択します。

    ![[次へ] を選択します。](images/shm-fig10a.png)

12. Windows 10 Pro または Enterprise のインストールを許可するには、 **EnableOsMigration**を有効にして、[ **次へ**] を選びます。

    ![[O S の移行を有効にする] を選択します。](images/shm-fig11.png)
    
    ![[OS 移行の有効化] を [オン] に設定します。](images/shm-fig12.png)

> [!NOTE]
> SEMM パッケージを適用した後、デバイスの UEFI メニューでは、すべての UEFI 設定を使用できなくなります (ロックされています)。 その他の設定については、 **IPv6 の場合、IPv6 の場合** の既定値も使用できません。 
>
>移行が完了した後で UEFI の設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除します。 別の SEMM パッケージを適用して UEFI の設定を変更する場合は、新しい SEMM パッケージをビルドするときに、元の証明書を使用する必要があります。 UEFI コンフィギュレーターツールを使用して、 **EnableOSMigration** をオフのままにしておきます (元の移行手順で示されています)。

#### SEMM パッケージを USB ドライブに保存する

1. USB ドライブを PC に接続します。 
1. [ **Hub 2s**] を選び、[ **次へ**] を選びます。

   ![USB を選ぶ](images/shm-fig13.png)

   > [!WARNING]
   > SEMM パッケージをビルドすると、USB ドライブ上の既存のデータはすべて消去されます。 SEMM パッケージを作成する前に、保存する USB ドライブからファイルを削除します。
   
2. [ **ビルド**] を選びます。

   ![[ビルド] を選びます。](images/shm-fig14.png)

3. このページのスクリーンショットをキャプチャして、[ **終了**] を選びます。 これで、SEMM パッケージの準備ができました。 このファイルには、SEMM パッケージ *Dfciupdate* と、semm 拇印 (証明書の拇印の最後の2文字) が含まれているテキストファイルが含まれています。

   ![[終了] を選びます。](images/shm-fig15.png)
   
4. 証明書の拇印の最後の2文字を保存します。 Surface Hub 2S でパッケージを適用するときに、SEMM を有効にするには、これらの文字が必要です。

### Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 ドライバーとファームウェアを含む USB フラッシュドライブを準備する

次のいずれかのオプションを使用して、Windows 10 Pro または Enterprise のイメージ (バージョン1903以降) をインストールできます。

- 現在のイメージングソリューション。

- <a href="https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator" target="_blank"> Surface Deployment Accelerator </a> 。 このツールを使用して、起動可能な Windows 10 イメージを作成します。 画像には、現在使用しているすべての Windows 10 の更新プログラム、Office、選択したその他のアプリ、および必要なドライバーとファームウェアが含まれていることがあります。 

- Windows 10 Pro または Enterprise のイメージが含まれている USB フラッシュドライブ。 次 <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> に、Surface Hub 2 の Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをインストールし </a> ます。
 
次の手順では、インストールメディアから USB フラッシュドライブを作成した後、SEMM パッケージファイルと、Surface Hub 2 MSI ファイルの Windows 10 Pro と Enterprise OS 用のドライバーとファームウェアを追加する方法について説明します。 他の展開方法を使用している場合は、この記事の「 [Surface Hub 2s での更新プログラム](#update-uefi-on-surface-hub-2s-to-enable-os-migration) のインストール」を参照してください。

> [!NOTE]
> インストールが完了したら、既存の Windows 10 Team ライセンスとは別の Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要です。

1. Windows 10 Pro のインストールを作成するには、[ <a href="https://www.microsoft.com/software-download/windows10" target="_blank"> windows 10 のダウンロード </a> ] ページで指示に従ってメディア作成ツールをダウンロードします。 Windows 10 Enterprise をダウンロードするには、 <a href="https://www.microsoft.com/licensing/servicecenter/default.aspx" target="_blank"> Microsoft ボリュームライセンスサービスセンターにアクセスして </a> ください。

2. 新しい USB ストレージドライブを挿入します。 
1. メディア作成ツールを開き、[ **インストールメディアの作成**] を選択して、[ **次へ**] を選択します。

   ![インストールメディアを作成します。](images/shm-fig16.png)
   
3. 言語を選択し、[ **Windows 10** ] と [ **64 ビット (x64)**] を選択します。 [ **次へ**] を選びます。

   ![[言語] を選択し、[Windows 10] と [64 ビット] を選択します。 [次へ] を選びます。](images/shm-fig17.png)
   
4. [ **USB フラッシュドライブ**] を選択し、[ **次へ**] を選択します。

   ![[U S B フラッシュドライブ] を選択し、[次へ] を選択します。](images/shm-fig18.png)
   
5. ダウンロードが完了したら、[ **完了**] を選びます。

   ![[完了] を選びます。](images/shm-fig19.png)
   
6. Surface Hub 2 (MSI ファイル) 上の Windows 10 Pro および Enterprise OS のドライバーとファームウェアを、Windows 10 イメージが含まれている USB フラッシュドライブ (*Bootme*) のルートにコピーします。 BOOTME USB ドライブの内容:

    - Windows 10 の起動可能なイメージ。
    
    - SEMM パッケージファイル (USB ドライブのルートにコピーされます)。
    
      - *Dfi をダウンロード*します。
      - SEMM 拇印を含むテキストファイル。 (この例では、ファイルは *SurfaceUEFI_2020Aug25_1058.txt*ています)。自動的に生成された日付タイムスタンプは、Surface UEFI コンフィギュレーターを使用してファイルを作成した日付に対応します。

   - Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) での Windows 10 Pro と Enterprise OS のドライバーとファームウェア。 このファイルを USB ドライブのルートにコピーします。

### Surface Hub 2S で UEFI を更新して OS の移行を有効にする

1. BOOT ME ドライブを USB に挿入します。 Surface Hub 2S の A ポート。 必要なファイルの一覧については、前のセクションを参照してください。

2. UEFI を起動するには、次の操作を行います。

   1. Surface Hub 2S をオフにします (シャットダウンします)。
   1. **ボリューム +** を押しながら、電源ボタンを押して離します。
   1. [UEFI] メニューが表示さ **れるまで、[保持]** を選びます。
   
      ![[UEFI] メニューが表示されるまで、音量を調節したままにします。](images/shm-fig20.png)
      
3. デバイスが再起動したら、前に作成した UEFI パスワード (該当する場合) を入力します (強くお勧めします)。

   ![UEFI パスワードを入力します。](images/shm-fig22.png)
   
4. [UEFI] メニューで、[**管理**インストール (USB)] を選択し  >  **Install from USB**ます。

   ![[管理] を選択し、U S B からインストールします。](images/shm-fig21.png)
   
5. 次の図に示すように、[ **今すぐ再起動**] を選択します。 デバイスが再起動します。 ウィンドウの中央に白い Microsoft ロゴが表示され、シャットダウンします。

   ![[今すぐ再起動] を選択します。](images/shm-fig25.png)
   
6. 電源ボタンを押してから離します。 表示される赤いウィンドウで、[Surface Enterprise Management] モードを有効にします。 

7. 2文字の証明書の拇印と UEFI 設定のパスワードを入力します。 [ **OK]** を選びます。

   ![2文字の証明書の拇印と UEFI 設定のパスワードを入力します。](images/shm-fig23.png)
 
   > [!NOTE]
   > デバイスで SEMM のライセンス認証を行うと、新しい UEFI 設定 **EnableOSMigration** が適用されます。 Windows 10 チームにはアクセスできなくなります。 代わりに、次の手順に進んで、Windows 10 Pro または Windows 10 Enterprise をインストールする必要があります。 

   デバイスが再起動します。 画面の中央に白いロゴが表示され、もう一度停止します。

### Windows 10 Pro または Enterprise をインストールする

1. 起動可能な Windows 10 Pro または Enterprise ドライブが、Surface Hub 2 USB-ポートにまだ入っていない場合は、ここで挿入します。 次に、電源ボタンを押してから離します。 

    デバイスが起動すると、画面の中央に白いロゴが表示されます。 白いロゴの下にスピンしている円が表示されます。

3. デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切ってください (電源コードを外してから、もう一度接続します)。 電源コードをもう一度接続すると、数秒経ってもデバイスが起動します。 画面の中央に白いロゴが表示されます。 

    デバイスの電源がオンになっていない場合は、電源ボタンを押してから離します。 画面中央にロゴが表示されたらすぐに、白いロゴの下にスピンしている円が表示されるまで音量ボタンを長押しします。
 
   ![U S B ドライブから Windows 10 に起動します。](images/shm-fig26.png)
   
4. 既定のエクスペリエンス (OOBE) セットアップが開始されたら、手順に従って Windows 10 Pro または Enterprise (バージョン1903以降) をインストールします。

### Surface Hub 2 ドライバーとファームウェアをインストールする

デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Surface Hub 2 で Windows 10 Pro と ENTERPRISE OS 用のドライバーとファームウェアをインストールし </a> ます。
 
## 推奨設定を構成する

Surface Hub をパーソナルの生産性デバイスとして完全に構成する方法については、「 <a href="surface-hub-2-post-install.md" target="_blank"> Surface hub 2 で Windows 10 Pro または Enterprise を構成する」を参照してください </a> 。

> [!NOTE]
>この記事に記載されている手順を実行してもデバイスが Windows 10 Pro または Surface Hub 2 のエンタープライズに正常に移行されない場合は、surface Hub のサポートにお問い合わせください <a href="https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support" target="_blank"> </a> 。

## Windows 10 チームにロールバックする

デバイスを Windows 10 チームに復元する場合は、「 <a href="surface-hub-2s-recover-reset.md" target="_blank"> Surface Hub 2s のリセットと回復」を参照してください </a> 。

## バージョン履歴

次の表は、この記事に加えられた変更をまとめたものです。

| バージョン | 日付               | 説明                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| 部. 1.2  | 2020年9月29日 | ユーザビリティのフィードバックに対応するその他の更新プログラム。                                                        |
| 部. 1.1  | 2020年9月15日 | 新しい OS をインストールするためのライセンス要件を明確に示す追加メモを導入しています。 |
| 部. 1.0  | 2020年9月1日  | 新しい記事。                                                                                           |
