---
title: Surface Hub 2 で Windows 10 Pro または Enterprise に移行する
description: Surface Hub 2 に Windows 10 Pro または Enterprise を移行してインストールします。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/01/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 7198fd3f18a160a0a50f46d270997e4fb4c03b3c
ms.sourcegitcommit: a828853f227b2eda75f904792f7763dc581e9931
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "10991020"
---
# Surface Hub 2 で Windows 10 Pro または Enterprise に移行する

## はじめに

Surface Hub 2S は、Windows 10 チームでプレインストールされています。カスタマイズされた Windows 10 は、会議室環境での共同作業が容易になるように設計されています。 これで、Windows 10 Pro または Enterprise を実行して、他の PC と同様に Surface Hub の2S を使用できるようになりました。 

別個の PC とダウンロード可能なツールを使用して、Windows 10 チームから移行を開始します。 surface **UEFI コンフィギュレーター** --Surface Hub 2s に適用する新しい UEFI 設定を含むパッケージを作成します。  Surface Enterprise Management Mode (SEMM) へのインターフェイスとしての surface の構成機能。これは、企業環境の Surface デバイスでのファームウェア設定の一元管理を容易にするために設計されています。 SEMM の詳細については、「 [Microsoft Surface Enterprise 管理モードのドキュメント](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」を参照してください。
 

## ソリューションのコンポーネント
- Windows 10 Team オペレーティングシステムを実行している Surface Hub 2S デバイス
- Windows 10 を実行している別のデバイス
- Surface UEFI コンフィギュレーターツール
- Windows 10 Pro または Enterprise OS イメージ、バージョン1903以上
- 2 GB の記憶域を持つ2つの USB ドライブ、FAT32 形式
- Windows 10 Pro および Enterprise のドライバーとファームウェアは Surface Hub 2、Windows Installer で使用できます。MSI ファイル
- インターネット接続
- イメージングソリューション (オプション)

 
## 移行ワークフローの概要

| ステップ  | 操作                                                                                                 | まとめ                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 件 | [Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | UEFI バージョンが694.2938.768.0 以降であることを確認します。                                                                                                                                                                                                                                                                                                                                                      |
| 両面 | [ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Surface Tools から [surface](https://www.microsoft.com/download/details.aspx?id=46703) をダウンロードして、別の PC にインストールします。 [Surface Hub 2 で Windows 10 Pro と Enterprise のドライバーとファームウェアをダウンロードします。MSI ファイル](https://www.microsoft.com/download/details.aspx?id=101974)を保存して、手順5で使用するために保存します。 |
| - | [SEMM 証明書の準備](#prepare-semm-certificate)                                                                          | Surface UEFI コンフィギュレーターの実行に必要な証明書を準備するか、現在の証明書を使用します。                                                                                                                                                                                                                                                                                                      |
| 4d | [SEMM パッケージを作成する](#create-semm-package)                                                                               | Surface UEFI コンフィギュレーターを起動して USB ドライブ上に SEMM パッケージを作成します。これには、Surface Hub 2S に適用する必要な構成ファイルが含まれます。 これらの SEMM パッケージファイルを PC 上のフォルダーにコピーします。                                                                                                                                                                                          |
| 個 | [Windows 10 イメージ、SEMM パッケージ、および Windows 10 Pro とドライバーとファームウェアを含む USB フラッシュドライブを Surface Hub 2 で準備する](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Windows 10 イメージを含む USB ドライブ (この例では **Bootme** という名前) を作成します。 Windows 10 Pro と Enterprise 用のドライバーとファームウェアを Surface Hub 2 (手順 2) と SEMM パッケージファイル (手順 4) に追加して、 **Bootme** ドライブに追加します。                                                                                                                                                                                                  |
| = | [Surface Hub 2S で UEFI を更新して OS の移行を有効にする](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | **Bootme**ドライブを使って、[UEFI] メニューに Surface Hub 2s を起動し、semm パッケージをインストールします。|
| 日 | [Windows 10 Pro または Enterprise バージョン1903以降をインストールする](#install-windows-10-pro-or-enterprise)                                        | **Bootme**ドライブを使用して、 **Windows 10 Pro または Enterprise**バージョン1903以降をインストールします。                                                                                                                                                                                                                                                                                 |
| 個 | [Surface Hub 2 の Windows 10 Pro と Enterprise 用のドライバーとファームウェアをインストールする](#install-surface-hub-2-drivers-and-firmware)                                        | デバイスに最新の更新プログラムとドライバーがすべてインストールされていることを確認するには、Surface Hub 2 で [Windows 10 Pro および Enterprise 用のドライバーとファームウェア] をインストールします。MSI ファイル ( https://www.microsoft.com/download/details.aspx?id=101974)                                                                                                                                                                                                                                                                                  |[
## Surface Hub 2S の UEFI バージョンが最小要件を満たしていることを確認する

Surface Hub を Windows 10 Team から Windows 10 デスクトップに移行する前に、 **694.2938.768.0**の最小 UEFI バージョンが必要です。
 
**システムの現在の UEFI バージョンを確認するには、次の操作を行います。**

1. Surface Hub 2s ホーム画面で、[**開始**] を選択し、 **SurfaceApp** (**すべてのアプリ**の  >  **サーフェス**) を開きます。
2. **Surface**を選択して、surface Hub に関する情報を表示します。これには、デバイス上の UEFI の最新バージョンが含まれます。 以下に示すように、UEFI バージョンが **694.2938.768.0** 以降の場合、uefi は、OS の移行を有効にするための semm パッケージの作成に適しています。<br><br>
 ![Surface アプリを開く & Surface を選択します。](images/shm-fig1.png)<br><br>
1. UEFI バージョンがバージョン694.2938.768.0 よりも古い場合は、Windows Update を使用して現在のバージョンを取得する必要があります。

**Windows Update から UEFI を更新するには:**
1. Surface Hub 2s の場合は、**管理者**としてサインインし、[**すべてのアプリ**の設定]、[  >  **Settings** >  **セキュリティ**  >  **Windows Update** ] の順に移動して、すべての更新プログラムをインストールしてから、デバイスを再起動します。 Surface アプリを使用して、UEFI バージョンを確認します。 注: ユーザー名または管理者のパスワードがわからない場合は、デバイスをリセットする必要があります。 詳細については、「 [Surface Hub 2s のリセットと回復](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset)」を参照してください。
2. UEFI バージョンが **694.2938.768.0** 以降になるまで、この手順を繰り返します。
3. まだ更新されている UEFI が何回も表示されない場合は、 **更新履歴** を確認して、失敗したファームウェアインストールのインスタンスを探します。 デバイスをリセットする必要がある場合があります (**設定**  >  **更新 & セキュリティ**  >  **リセットデバイス**)。

### ダウンロード Surface UEFI コンフィギュレーターおよび Surface Hub 2 ドライバーとファームウェア

別の PC では、次の操作を行います。

- Surface Tools から Microsoft [SURFACE UEFI コンフィギュレーター](https://www.microsoft.com/download/details.aspx?id=46703) をダウンロードしてインストールします。 Surface UEFI コンフィギュレーターは Surface Hub 2S では実行できませんが、Windows 10 Team はインストールされています。
- [Surface Hub 2 ドライバーとファームウェア Windows インストーラーをダウンロードします。](https://www.microsoft.com/download/details.aspx?id=101974)新しいオペレーティングシステムをインストールするときに適用される MSI ファイル。

### SEMM 証明書の準備

Surface UEFI コンフィギュレーターを初めて使用する場合は、証明書を準備する必要があります。 この証明書は、デバイスが SEMM に登録された後、承認された証明書で作成されたパッケージのみを使用して UEFI 設定を変更できることを保証します。 証明書を取得する方法は、組織の規模または複雑さによって異なる場合があります。

- 大規模なエンタープライズ組織では、通常、標準セキュリティの慣行ごとに証明書を生成する独自の証明書インフラストラクチャを維持しています。
- 中規模企業やその他のユーザーが、サードパーティプロバイダーから証明書を取得することを選択できます。 これは、十分な IT 専門知識または専任の IT セキュリティチームを持たない組織向けの推奨オプションです。
- または、次のドキュメントに記載されている PowerShell スクリプトを使用して自己署名証明書を生成することもできます。 [Surface Enterprise 管理モードの証明書の要件](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)。 または、PowerShell を使用して、次のドキュメントに従って独自の証明書を作成します。[新正書法 certificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps)

UEFI 設定を適用する前に、構成ファイルの署名を確認するために、SEMM パッケージを証明書を使用して保護する必要があります。 詳細については、「 [Surface Enterprise 管理モード](https://docs.microsoft.com/surface/surface-enterprise-management-mode) のドキュメント」を参照してください。
 
 
### SEMM パッケージを作成する

1. **SURFACE UEFI コンフィギュレーター**を開き、[**開始**] を選択します。<br><br>
 ![Open Surface UEFI コンフィギュレーター](images/shm-fig2.png)<br><br>
2. [ **Surface デバイス** ] を選択し、[ **次へ**] を選択します。 <br><br>
  ![Surface デバイスの選択](images/shm-fig3.png)<br><br>
  
3. [ **構成パッケージ**] を選びます。<br><br>
 ![構成パッケージを選ぶ](images/shm-fig4.png)<br><br> 
  
4. [ **証明書の保護**] を選びます。<br><br>
  ![証明書の保護を選ぶ](images/shm-fig5.png)<br><br>

5. 証明書 .pfx ファイルを追加するように求められます。 <br><br> 
  ![証明書を追加するように求められます。](images/shm-fig6.png)<br><br>
6. **証明書のパスワード**を入力して、[ **OK]** を選択します。<br><br> 
  ![証明書のパスワードを入力して、[OK] を選択します。](images/shm-fig7.png)<br><br>

7. Surface UEFI にパスワードを追加するには、[ **パスワードによる保護** ] を選択します。 このパスワードは、UEFI を起動するたびに必要になります。 Surface Hub 2S で使用する UEFI パスワードを設定する **ことを強くお勧め** します。<br><br>   
![[パスワードによる保護] をクリック](images/shm-fig8.png)<br><br>
8. **UEFI パスワード**を設定して、[ **OK]** を選択します。<br><br> 
 ![UEFI パスワードを入力する](images/shm-fig9.png)<br><br>

> [!IMPORTANT]
> パスワードをメモしておきます。 パスワードを忘れた場合、または紛失した場合は、回復処理は行われません。 


9. [ **Surface Hub 2s** ] を選択し、[ **次へ**] を選択します。<br><br>
 ![Surface Hub 2S の選択](images/shm-fig10.png)<br><br>
10. **[次へ]** を選択します。<br><br>
 ![[次へ] を選ぶ](images/shm-fig10a.png)<br><br>
11. Windows 10 Pro または Enterprise のインストールを許可するには、[EnableOsMigration] を選択し **ます。**<br><br>
 ![[OS の移行を有効にする] を選ぶ](images/shm-fig11.png)<br><br>
12. **EnableOSMigration**を **[オン**] に設定して、[**次へ**] を選びます。<br><br>
 ![[OS 移行の有効化] を [オン] に設定する](images/shm-fig12.png)<br><br>

> [!NOTE]
> SEMM パッケージを適用した後は、デバイスの UEFI メニューですべての UEFI 設定が灰色表示になります (ロックされています)。 これには、PXE ブート用 IPv6 など、他の設定の既定値が含まれます。 UEFI の設定を変更するには、別の SEMM パッケージを適用するか、SEMM からデバイスの登録を解除する必要があります。

#### SEMM パッケージを USB ドライブに保存する

1. USB ドライブを PC に接続します。 [ **Hub 2s** ] を選び、[ **次へ**] を選びます。 <br><br>
![USB を選ぶ](images/shm-fig13.png)<br><br>
2. [ビルド] を選び **ます。**<br><br>
![[ビルド] を選ぶ](images/shm-fig14.png)<br><br>
3. このページのスクリーンショットをキャプチャして、[ **終了**] を選びます。 SEMM パッケージは現在準備が整っており、semm パッケージ **Dfciupdate** と、semm 拇印 (証明書の拇印の最後の2文字) を含むテキストファイルが含まれています。<br><br>
 ![[終了] を選ぶ](images/shm-fig15.png)<br><br>
 4. Surface Hub 2S でパッケージを適用するときに、SEMM をアクティブ化するために必要な証明書の拇印の最後の2文字を保存します。

### Windows 10 イメージ、SEMM パッケージ、Surface Hub 2 ドライバーとファームウェアを含む USB フラッシュドライブを準備する

次のいずれかのオプションを使用して、Windows 10 Pro または Enterprise のイメージ (バージョン1903以降) をインストールできます。

- 現在のイメージングソリューション。
- [Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) では、現在使用しているすべての windows 10 の更新プログラム、Office、その他のアプリ、および必要なドライバーとファームウェアを含めることができる起動可能な windows 10 イメージを作成できます。 
- Windows 10 Pro または Enterprise のイメージが搭載された USB フラッシュドライブ。その後、  [Surface Hub 2 で windows 10 pro と enterprise 用のドライバーとファームウェアを](https://www.microsoft.com/download/details.aspx?id=101974)インストールします。
 

この手順では、インストールメディアから USB フラッシュドライブを作成して、Windows 10 Pro とドライバーとファームウェアを Surface Hub 2 で追加します。MSI ファイル。 他の展開方法を使用している場合は、次のセクション「 [Surface Hub 2s で UEFI を更新して OS の移行を有効](#update-uefi-on-surface-hub-2s-to-enable-os-migration)にする」に進みます。

> [!NOTE]
> インストールが完了したら、Windows 10 Pro または Windows 10 Enterprise の有効なライセンスが必要になります。

1. Windows 10 Pro のインストールを作成するには、「 [windows 10 のダウンロード](https://www.microsoft.com/software-download/windows10) 」ページの手順に従って、 **メディア作成** ツールを使用します。 Windows 10 Enterprise をダウンロードするには、 [Microsoft ボリュームライセンスサービスセンター](https://www.microsoft.com/licensing/servicecenter/default.aspx)にアクセスしてください。
2. 新しい **USB ストレージ** ドライブを挿入します。 **メディア作成**ツールを起動し、[**インストールメディアの作成**] を選択して、[**次へ**] を選択します。<br><br>
 ![インストールメディアを作成する](images/shm-fig16.png)<br><br>
3. [言語]、[Windows 10]、[64 ビット (x64)] の順に選択し、[ **次へ**] を選択します。<br><br>
 ![[言語]、[Windows 10]、[64 ビット] の & 選択し、[次へ] を選択します。](images/shm-fig17.png)<br><br>
4. [ **USB フラッシュドライブ** ] を選択し、[ **次へ**] を選択します。<br><br>
 ![USB フラッシュドライブを選択し、[次へ] を選択します。](images/shm-fig18.png)<br><br>
5. ダウンロードが完了したら、[ **完了**] を選びます。<br><br>
 ![[完了] を選ぶ](images/shm-fig19.png)<br><br>
6. Surface Hub 2 の Windows 10 Pro および Enterprise 用の SEMM パッケージファイルとドライバーおよびファームウェアをコピーします。Windows 10 イメージを含む USB フラッシュドライブ (**Bootme**) への MSI。
    - DfciUpdate
    - SEMM 拇印のテキストファイル。 (この例では、SurfaceUEFI_2020Aug25_1058.txt)
    - Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) での Windows 10 Pro と Enterprise のドライバーとファームウェア

### Surface Hub 2S で UEFI を更新して OS の移行を有効にする

**Bootme**ドライブを使って、semm パッケージファイルをインストールし、UEFI を更新して、Windows 10 Pro または Enterprise を実行できるように Surface Hub を有効にします。 次に、 **Bootme** ドライブから起動して、Windows 10 をインストールします。

1. SEMM パッケージファイル、Windows 10 Pro 用のドライバーとファームウェアを含む **Bootme** ドライブを Surface Hub 2 に挿入します。MSI、Windows 10 では、ファイルが USB にインストールされます。 Surface Hub 2S のポート。  
2. UEFI を起動するには、次の操作を行います。
    1. Surface Hub 2S の最初の電源オフ (シャットダウン)。
    2. **ボリューム +** を押しながら、**電源**ボタンを押して離します。
    3. [UEFI] メニューが表示さ **れるまで、[保持]** を選びます。<br><br>
     ![[UEFI] メニューが表示されるまで、holdling 音量を維持する](images/shm-fig20.png)<br><br>
3. デバイスが再起動したら、前に作成した UEFI パスワード (該当する場合) を入力します (強くお勧めします)。<br><br>
 ![デバイスが再起動したら、UEFI の paassword を入力します。](images/shm-fig22.png)<br><br>
4. [UEFI] メニューで、[**管理**インストール (USB)] を選択し  >  **Install from USB**ます。<br><br>
 ![[管理 & [USB からインストール] を選ぶ](images/shm-fig21.png)<br><br>
5. 次に示すように、[ **今すぐ再起動**] を選択します。 デバイスがシャットダウンされます。<br><br>
 ![[今すぐ再起動] を選択する](images/shm-fig25.png)<br><br>
6. Power button を押して離すと、Surface Enterprise 管理モードのライセンス認証を求めるメッセージが赤い画面に表示されます。 
7. 2文字の **証明書の拇印**と、 **UEFI 設定のパスワード** を入力して、[ **OK]** を選択します。<br><br>
 ![2文字の証明書の拇印を入力します。](images/shm-fig23.png)<br><br>  
8. デバイスが再起動し、画面中央に白い4乗が表示されたら、もう一度オフにします。

### Windows 10 Pro または Enterprise をインストールする

1. 起動可能な Windows 10 Pro または Enterprise ドライブが Surface Hub 2 USB-ポートにまだ入っていない場合は、ここで挿入して、電源ボタンを押してから離します。
2. デバイスが開始され、画面中央に白い4乗が表示され、白い4乗ロゴの下にスピンした円が表示されます。
3. デバイスが USB ドライブで自動的に起動しない場合は、デバイスの電源を切って (電源コードを外してもう一度接続します)、電源ボタンを押してから離し、白の4乗のロゴの下にスピンしている円が表示されるまで、[音量を下げる] ボタンを押したままにします。 <br><br>
 ![USB から Windows 10 への起動](images/shm-fig26.png)<br><br>
4. 不在時のエクスペリエンス (OOBE) セットアップが起動したら、指示に従って Windows 10 Pro または Enterprise (バージョン1903以降) をインストールします。

### Surface Hub 2 ドライバーとファームウェアをインストールする

1.  デバイスに最新の更新プログラムとドライバーがすべて含まれていることを確認するには、 [Surface Hub 2 で Windows 10 Pro と Enterprise 用のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=101974)をインストールします。
 
### 次のステップ

パーソナルの生産性向上デバイスとして Surface Hub 2 を使用する方法を最適化するには、「 [Windows 10 Surface hub のポストインストール構成](surface-hub-2-post-install.md)」を参照してください。
> [!NOTE]
>このドキュメントで説明されている手順を実行しても、Surface Hub 2 のデバイスを Windows 10 Pro または Enterprise に移行できなかった場合は、 [Surface hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。

