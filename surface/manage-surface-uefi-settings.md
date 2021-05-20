---
title: Surface UEFI の設定の管理
description: デバイスまたはコンポーネントの有効化または無効化、セキュリティ設定の構成、Surface デバイスのブート設定の調整を行うには、Surface UEFI の設定を使用します。
keywords: ファームウェア, セキュリティ, 機能, 設定, ハードウェア, firmware, security, features, configure, hardware
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: devices, surface
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.date: 04/13/2021
ms.openlocfilehash: ea995eda277ecf235eedd92f3af6edb0b60ae68a
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576507"
---
# <a name="manage-surface-uefi-settings"></a>Surface UEFI の設定を管理する

 Surface PC デバイスは、Microsoft が特にこれらのデバイス用に設計した一意の統合拡張可能ファームウェア インターフェイス (UEFI) を利用するように設計されています。 Surface UEFI 設定では、組み込みのデバイスとコンポーネントを有効または無効にし、UEFI 設定を変更から保護し、Surface デバイスのブート設定を調整できます。 

## <a name="supported-products"></a>サポートされている製品

UEFI 管理は、次の場合にサポートされます。 

- Surface Pro 4、Surface Pro (第 5 世代)、Surface Pro 6、Surface Pro 7、Surface Pro 7+、Surface Pro X
- Surface Laptop (第 1 世代), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4
- Surface Studio (第 1 世代), Surface Studio 2
- Surface Book、Surface Book 2、Surface Book 3
- Surface Go、 Surface Go 2[ <sup> 1 </sup> ](#references)

## <a name="support-for-cloud-based-management"></a>クラウドベースの管理のサポート

Microsoft Intune に組み込むデバイス ファームウェア構成インターフェイス (DFCI) プロファイル (パブリック プレビューで利用可能) を使用すると、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。 DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を築きます。 DFCI は現在、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 3、Surface Pro 7、および Surface Pro X で使用できます。 詳細については[、「Surface UEFI 設定の Intune 管理」を参照してください](surface-manage-dfci-guide.md)。

## <a name="open-surface-uefi-menu"></a>Surface UEFI メニューを開く

システムの起動時に UEFI 設定を調整するには、次の方法を実行します。

1. Surface をシャットダウンし、約 10 秒待ってオフにしてください。
2. 音量アップ ボタン **を長押** しし、同時に [電源] ボタンを押したまま **離します。**
3. Microsoft または Surface のロゴが画面に表示されたら、UEFI**** 画面が表示されるまで[ボリュームアップ] ボタンを押し続けます。

## <a name="uefi-pc-information-page"></a>UEFI PC 情報ページ

[PC 情報] ページには、Surface デバイスに関する詳細情報が含まれています。 

- **Model** – Surface デバイスのモデルがここに表示されます (例: Surface Book 2 または Surface Pro 7)。 デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。 
- **UUID** – このユニバーサル固有識別子の番号はデバイスに固有であり、展開または管理の際にデバイスを識別するために使用されます。 

- **Serial Number** (シリアル番号) – この番号は、アセットのタグ付けやサポートでこの特定の Surface デバイスを識別するために使用されます。
- **Asset Tag** (アセット タグ) – アセット タグは、[アセット タグ ツール](https://docs.microsoft.com/surface/assettag)で Surface デバイスに割り当てます。 

Surface デバイスのファームウェアに関する詳細情報も表示されます。 Surface デバイスには複数の内部コンポーネントがあり、それぞれが異なるバージョンのファームウェアを実行しています。 次の各デバイスのファームウェア バージョンが、**[PC information]** (PC の情報) ページに表示されます (図 1 を参照)。 

- System UEFI (システム UEFI) 

- SAM Controller (SAM コントローラー) 

- Intel Management Engine (Intel 管理エンジン) 

- System Embedded Controller (システム埋め込みコントローラー) 

- Touch Firmware (タッチ ファームウェア) 

![システム情報とファームウェアのバージョン情報](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*図 1. システム情報とファームウェアのバージョン情報*

Surface デバイスの最新のファームウェア バージョンに関する最新情報は、お使いのデバイスの「[Surface 更新履歴](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history)」で確認できます。 

## <a name="uefi-security-page"></a>UEFI セキュリティ ページ 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*図 2. Surface UEFI のセキュリティ設定を構成する*

[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。 Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。 パスワードには、次の文字を含めることができます (図 3 を参照)。 

- 大文字: A ～ Z 

- 小文字: a ～ z 

- 数字: 1 ～ 0 

- 特殊文字: !@#$%^&*()?<>{} []-_=+|.;:'' 

パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*図 3.  Surface UEFI の設定を保護するためのパスワードを追加する*

[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。 セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。 セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。 図 4 に示すように、サードパーティの証明書を使用するセキュア ブートを構成できます。 詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*図 4:  セキュア ブートを設定する*

デバイスによっては、TPM が有効になっているか無効になっているかも確認できます。 [TPM の有効化]**** 設定が表示されない場合は、図 5 に示すように、Windowsで tpm.msc を開き、状態を確認します。 TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。 詳細については、「概要」[をBitLockerしてください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)。 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*図 5:  TPM コンソール*


## <a name="uefi-menu-devices"></a>UEFI メニュー: デバイス 

[デバイス] ページでは、次を含む特定のデバイスとコンポーネントを有効または無効にできます。

- ドッキング ポートと USB ポート 

- MicroSD スロットと SD カード スロット 

- 背面カメラ 

- 前面カメラ 

- 赤外線 (IR) カメラ 

- Wi-Fi と Bluetooth 

- オンボード オーディオ (スピーカー、マイク) 

図 6 に示すように、各デバイスにはスライダー ボタンが表示され、オン **(有効** ) またはオフ **(無効** ) の位置に移動できます。 

![特定のデバイスを有効および無効にする](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*図 6.  特定のデバイスを有効および無効にする*

## <a name="uefi-menu-boot-configuration"></a>UEFI メニュー: ブート構成 

[ブート構成] ページでは、ブート デバイスの順序を変更したり、次のデバイスの起動を有効または無効にできます。 

- Windows ブート マネージャー 

- USB 記憶装置 

- PXE ネットワーク 

- 内部ストレージ 

特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。 また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。 

指定したブート順序を有効にするには、図 7**** に示すように、[代替ブート シーケンスを有効にする] オプションを **[オン**] に設定する必要があります。 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*図 7. Surface デバイスのブート順序を設定する* 

また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。  

## <a name="uefi-menu-management"></a>UEFI メニュー: 管理
[管理] ページでは、ゼロ タッチ UEFI 管理の使用と、Surface Pro 7、Surface Pro X、および Surface Laptop 3 を含む対象デバイス上の他の機能を管理できます。  

![図 8 は、ゼロ タッチ UEFI 管理などの機能 ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *へのアクセスを管理します。ゼロ タッチ UEFI 管理などの機能へのアクセスを管理する* 


ゼロ タッチ UEFI 管理を使用すると、Intune (デバイス ファームウェア構成インターフェイス (DFCI) と呼ばれるデバイス プロファイルを使用して、UEFI 設定をリモートで管理できます。 この設定を構成しない場合、DFCI を使用して対象デバイスを管理する機能は [準備完了] に設定 **されます**。 DFCI を防止するには、[オプトアウト] **を選択します**。 

> [!NOTE]
> 現在、UEFI 管理設定ページと DFCI の使用は、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 4、Surface Laptop 3、Surface Pro 7、Surface Pro X で利用できます。詳細については[、「Surface UEFI 設定の Intune 管理」を参照してください](surface-manage-dfci-guide.md)。

## <a name="uefi-menu-exit"></a>UEFI メニュー: 終了 

図 9 **に示すように** 、[ **終了** ] ページの [今すぐ再起動] ボタンを使用して UEFI 設定を終了します。 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*図 9. Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする*

## <a name="surface-uefi-boot-screens"></a>Surface UEFI のブート画面

Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。 Surface ファームウェア更新プロセスの詳細については、「Surface ドライバーとファームウェア更新プログラムの管理 [と展開」を参照してください](manage-surface-driver-and-firmware-updates.md)。 ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。 各コンポーネントの進行状況バーを図 9 ~ 18 に示します。

![青色の進行状況バーで表示される Surface UEFI のファームウェアの更新](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*図 10. 青色の進行状況バーで表示される Surface UEFI のファームウェア更新*

![緑色の進行状況バーで表示される System Embedded Controller のファームウェア](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*図 11. 緑色の進行状況バーで表示される System Embedded Controller のファームウェアの更新*

![オレンジの進行状況バーで表示される SAM Controller のファームウェアの更新](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*図 12. オレンジ色の進行状況バーで表示される SAM Controller のファームウェアの更新*

![赤色の進行状況バーで表示される Intel Management Engine のファームウェア](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*図 13. 赤色の進行状況バーで表示される Intel Management Engine のファームウェアの更新*

![灰色の進行状況バーで表示される Surface Touch のファームウェア](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*図 14. 灰色の進行状況バーで表示される Surface Touch のファームウェアの更新*

![薄緑色の進行状況バーを含む Surface KIP ファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*図 15. Surface KIP ファームウェア更新プログラムは、淡い緑色の進行状況バーを表示します*

![ピンクの進行状況バーを含む Surface ISH ファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*図 16 Surface ISH ファームウェア更新プログラムに薄いピンク色の進行状況バーが表示される*

![灰色の進行状況バーを含む Surface Trackpad ファームウェア](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*図 17. Surface Trackpad ファームウェアの更新プログラムにピンクの進行状況バーが表示される*

![淡い灰色の進行状況バーを含む Surface TCON ファームウェア](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*図 18. Surface TCON ファームウェア更新プログラムは、淡い灰色の進行状況バーを表示します。*


![薄紫色の進行状況バーを含む Surface TPM ファームウェア](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*図 19:  Surface TPM ファームウェアの更新プログラムに紫色の進行状況バーが表示される*


>[!NOTE]
>図 19 に示すように、Secure Boot が無効になっているという追加の警告メッセージが表示されます。

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*図 20. Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面*

## <a name="references"></a>参考資料

1. Surface Go と Surface Go 2 はサードパーティの UEFI を使用し、DFCI はサポートされていません。 

## <a name="related-topics"></a>関連トピック

- [Surface UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)

-  [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
