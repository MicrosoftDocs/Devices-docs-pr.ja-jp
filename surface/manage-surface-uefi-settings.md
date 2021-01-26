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
ms.date: 01/25/2021
ms.openlocfilehash: af9eac171dea5d29ce9776766a2c5842bea9eb8c
ms.sourcegitcommit: 1b12ea363785697ddc705b0a0cc7bb35cad6b327
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "11300698"
---
# Surface UEFI の設定を管理する

 Surface PC デバイスは、Microsoft が特にこれらのデバイス向けに設計した独自の Unified Extensible Firmware Interface (UEFI) を利用するように設計されています。 Surface UEFI の設定では、組み込みのデバイスとコンポーネントを有効または無効にし、UEFI 設定の変更を保護し、Surface デバイスのブート設定を調整できます。 

## サポートされる製品

UEFI 管理は、次の場合にサポートされます。 

- Surface Pro 4、Surface Pro (第 5 世代)、Surface Pro 6、Surface Pro 7、Surface Pro 7+、Surface Pro X
- Surface Laptop (第 1 世代)、Surface Laptop 2、Surface Laptop 3、Surface Laptop Go
- Surface Studio (第 1 世代)、Surface Studio 2
- Surface Book、Surface Book 2、Surface Book 3
- Surface Go、Surface Go 2[ <sup> 1 </sup> ](#references)

## クラウドベースの管理のサポート

Microsoft Intune (パブリック プレビューで使用可能) に組み込みのデバイス ファームウェア構成インターフェイス (DFCI) プロファイルにより、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。 DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を構築します。 DFCI は現在、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 3、Surface Pro 7、Surface Pro X で利用できます。 詳しくは [、Surface UEFI 設定の Intune 管理に関するページをご覧ください](surface-manage-dfci-guide.md)。

## Surface UEFI メニューを開く

システム起動時に UEFI 設定を調整するには:

1. Surface をシャットダウンし、約 10 秒待って、電源が切れるのを確認します。
2. 音量を上げ **ボタン** を長押しし、同時に電源ボタンを長押し **します。**
3. Microsoft または Surface ロゴが画面に表示されたら、UEFI**** 画面が表示されるまで音量を上げ続けます。

## UEFI PC 情報ページ

[PC 情報] ページには、Surface デバイスに関する詳細情報が表示されます。 

- **モデル** – Surface Book 2 や Surface Pro 7 など、Surface デバイスのモデルがここに表示されます。 デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。 
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

## UEFI セキュリティ ページ 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*図 2.  Surface UEFI のセキュリティ設定を構成する*

[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。 Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。 パスワードには、次の文字を含めることができます (図 3 を参照)。 

- 大文字: A ～ Z 

- 小文字: a ～ z 

- 数字: 1 ～ 0 

- 特殊文字: !@#$%^&*()?<>{} []-_=+|.,;:''" 

パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*図 3.  Surface UEFI の設定を保護するためのパスワードを追加する*

[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。 セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。 セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。 図 4 に示すように、サード パーティの証明書で動作するセキュア ブートを構成できます。 詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*図 4:  セキュア ブートを設定する*

デバイスによっては、TPM が有効か無効か確認できる場合があります。 [TPM を有効にする****] 設定が表示されない場合は、Windows で tpm.msc を開き、状態を確認します (図 5 を参照)。 TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。 詳細については [、「BitLocker の概要」を参照してください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)。 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*図 5:  TPM コンソール*


## UEFI メニュー: デバイス 

[デバイス] ページでは、次の特定のデバイスとコンポーネントを有効または無効にできます。

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

## UEFI メニュー: ブート構成 

[ブート構成] ページでは、ブート デバイスの順序を変更したり、次のデバイスのブートを有効または無効にしたりできます。 

- Windows ブート マネージャー 

- USB 記憶装置 

- PXE ネットワーク 

- 内部ストレージ 

特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。 また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。 

図 7 に示すように、指定したブート順序**** を有効にするには、[代替ブート シーケンスの有効化] オプションを **[オン**] に設定する必要があります。 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*図 7. Surface デバイスのブート順序を設定する* 

また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。  

## UEFI メニュー: 管理
[管理] ページでは、ゼロ タッチ UEFI 管理の使用や、Surface Pro 7、Surface Pro X、Surface Laptop 3 などの対象デバイスでのその他の機能の使用を管理できます。  

![ゼロ タッチ UEFI 管理と他の機能へのアクセスを管理する図 ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *8.ゼロ タッチ UEFI 管理と他の機能へのアクセスを管理する* 


ゼロ タッチ UEFI 管理を使用すると、Intune 内のデバイス プロファイル (DFCI) と呼ばれるデバイス プロファイルを使用して、UEFI 設定をリモートで管理できます。 この設定を構成しない場合、DFCI を使用して対象デバイスを管理する機能が [準備完了] に設定 **されます**。 DFCI を回避するには、[オプトアウト] **を選択します**。 

> [!NOTE]
> 現在、UEFI 管理の設定ページと DFCI の使用は、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 3、Surface Pro 7、Surface Pro X で利用できます。詳しくは [、Surface UEFI 設定の Intune 管理に関するページをご覧ください](surface-manage-dfci-guide.md)。

## UEFI メニュー: 終了 

図 9**に示すように****、[Exit]** ページの [Restart Now] ボタンを使用して UEFI 設定を終了します。 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*図 9. Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする*

## Surface UEFI のブート画面

Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。 Surface のファームウェアの更新プロセスについて詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。 ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。 各コンポーネントの進行状況バーを図 9 ~ 18 に示します。

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

![薄い緑色の進行状況バーが表示された Surface KIP ファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*図 15. Surface KIP のファームウェア更新プログラムに、明るい緑色の進行状況バーが表示される*

![ピンクの進行状況バーが表示された Surface ISH ファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*図 16 Surface ISH ファームウェア更新プログラムに薄いピンクの進行状況バーが表示される*

![灰色の進行状況バーが表示された Surface トラックパッドのファームウェア](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*図 17. Surface Trackpad のファームウェア更新プログラムにピンクの進行状況バーが表示される*

![薄い灰色の進行状況バーを含む Surface TCON ファームウェア](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*図 18. Surface TCON のファームウェア更新プログラムに薄い灰色の進行状況バーが表示される*


![薄紫色の進行状況バーが表示された Surface TPM ファームウェア](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*図 19:  Surface TPM のファームウェア更新プログラムに紫色の進行状況バーが表示される*


>[!NOTE]
>図 19 に示すように、セキュア ブートが無効な状態を示す追加の警告メッセージが表示されます。

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*図 20. Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面*

## 参考資料

1. Surface Go と Surface Go 2 はサード パーティ製の UEFI を使用し、DFCI はサポートされていません。 

## 関連トピック

- [Surface UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)

-  [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
