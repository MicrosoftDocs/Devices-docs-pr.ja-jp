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
ms.date: 10/12/2020
ms.openlocfilehash: 218f98b23adcb7bae2af92655d85144c6e5665e6
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114725"
---
# Surface UEFI の設定を管理する

Surface デバイスの現在および将来のすべての世代では、これらのデバイス専用の統合された固有の拡張ファームウェアインターフェイス (UEFI) が Microsoft によって設計されています。 Surface UEFI の設定では、組み込みのデバイスとコンポーネントを有効または無効にしたり、UEFI 設定を変更できないように保護したり、Surface device のブート設定を調整したりすることができます。 

## サポートされる製品

UEFI 管理は、次のようにサポートされています。 

- Surface Pro 4、Surface Pro (5 番目のジェネレーション)、surface Pro 6、Surface pro 7、surface Pro X
- Surface ラップトップ (1 つ目のジェネレーション)、Surface ノート Pc 2、surface ノート pc 3、surface ラップトップの移動
- Surface Studio (第1世代)、Surface Studio 2
- Surface book、Surface Book 2、Surface Book 3
- Surface Go、Surface Go 2

## クラウドベースの管理のサポート

Microsoft Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると (パブリックプレビューで利用できるようになりました)、Surface UEFI 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。 DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。 DFCI は、現在 Surface Pro 7、Surface Pro X、Surface Pc 3 で利用できます。 詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。

## Surface UEFI を開くメニュー

システムの起動時に UEFI 設定を調整するには:

1. Surface をシャットダウンして、約10秒待ってから、停止していることを確認します。
2. **音量を上げる**ボタンを押したままにして、電源ボタンを押しながら離し**ます。**
3. Microsoft または Surface のロゴが画面に表示されたら、[UEFI] 画面が表示されるまで **音量を上げ** たままにしておきます。

## UEFI PC 情報ページ

[PC 情報] ページには、Surface デバイスに関する詳細情報が表示されます。 

- **モデル** – surface device のモデルがここに表示されます (surface Book 2 または surface Pro 7 など)。 デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。 
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

## UEFI セキュリティページ 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*図 2.  Surface UEFI のセキュリティ設定を構成する*

[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。 Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。 パスワードには、次の文字を含めることができます (図3を参照)。 

- 大文字: A ～ Z 

- 小文字: a ～ z 

- 数字: 1 ～ 0 

- 特殊文字:! @ # $% ^& * ()? <>{} []-_ = + |.,;: ' ' " 

パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*図 3.  Surface UEFI の設定を保護するためのパスワードを追加する*

[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。 セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。 セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。 図4に示すように、サードパーティの証明書を使用するために、セキュアブートを構成することもできます。 詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*図 4:  セキュア ブートを設定する*

お使いのデバイスによっては、TPM が有効か無効かを確認することもできます。 [ **Tpm を有効にする**  ] 設定が表示されない場合は、「Windows で tpm を開く」を参照して、状態を確認してください (図 5)。 TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。 詳細については、「 [BitLocker の概要](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)」を参照してください。 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*図 5:  TPM コンソール*


## UEFI メニュー: デバイス 

[デバイス] ページでは、次のような特定のデバイスとコンポーネントを有効または無効にすることができます。

- ドッキング ポートと USB ポート 

- MicroSD スロットと SD カード スロット 

- 背面カメラ 

- 前面カメラ 

- 赤外線 (IR) カメラ 

- Wi-Fi と Bluetooth 

- オンボード オーディオ (スピーカー、マイク) 

各デバイスは、図6に示すように、 **[オン** ] (有効) または [ **オフ** ] (無効) の位置に移動できるスライダボタンと共に表示されます。 

![特定のデバイスを有効および無効にする](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*図 6.  特定のデバイスを有効および無効にする*

## UEFI メニュー: ブート構成 

[ブート構成] ページでは、ブートデバイスの順序を変更したり、次のデバイスの起動を有効または無効にしたりすることができます。 

- Windows ブート マネージャー 

- USB 記憶装置 

- PXE ネットワーク 

- 内部ストレージ 

特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。 また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。 

指定したブート順序を有効にするには、図7に示すように、[ **代替のブートシーケンスを有効** にする] オプションを **[オン**] に設定する必要があります。 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*図 7. Surface デバイスのブート順序を設定する* 

また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。  

## UEFI メニュー: 管理
[管理] ページでは、Surface Pro 7、Surface Pro X、Surface Pc 3 などの適格なデバイスでゼロタッチの UEFI 管理とその他の機能の使用を管理できます。  

![ゼロタッチの UEFI 管理とその他の機能へのアクセスを管理する ( ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *図 8)。ゼロタッチの UEFI 管理およびその他の機能へのアクセスを管理する* 


ゼロタッチ UEFI 管理では、「デバイスファームウェア構成インターフェイス (DFCI)」と呼ばれるデバイスプロファイルを使用して、UEFI 設定をリモートで管理できます。 この設定を構成しない場合は、DFCI を使って適格なデバイスを管理する機能が [ **準備完了**] に設定されます。 DFCI を無効にするには、[ **オプトアウト**] を選びます。 

> [!NOTE]
> [UEFI 管理の設定] ページと DFCI の使用は、Surface Pro 7、Surface Pro X、Surface ノートブック3でのみ利用できます。  

詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。

## UEFI メニュー: 終了 

図9に示すように、[**終了**] ページの [**今すぐ再起動**] ボタンを使用して、UEFI の設定を終了します。 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*図 9. Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする*

## Surface UEFI のブート画面

Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。 Surface のファームウェアの更新プロセスについて詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。 ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。 各コンポーネントの進行状況バーは、図 9 ~ 18 に表示されます。

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

![淡い緑の進行状況バーが表示された Surface キープファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*図 15. Surface キープファームウェア更新プログラムには、薄い緑色の進行状況バーが表示される*

![ピンク色の進行状況バーが表示された Surface の赤のファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*図 16 Surface の "ファームウェア更新プログラム" に明るいピンクの進行状況バーが表示される*

![Surface トラックパッドファームウェアと灰色の進行状況バー](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*図 17. Surface トラックパッドファームウェア更新プログラムにより、ピンクの進行状況バーが表示される*

![薄い灰色の進行状況バーが表示されたファームウェアの Surface tc](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*図 18. ファームウェア更新プログラムの Surface TCON 淡い灰色の進行状況バーが表示される*


![Surface TPM ファームウェアと明るい紫色の進行状況バー](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*図 19:  Surface TPM ファームウェア更新プログラムによって紫色の進行状況バーが表示される*


>[!NOTE]
>図19に示すように、セキュアブートが無効であることを示す追加の警告メッセージが表示されます。

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*図 20. Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面*

## 関連トピック

- [Surface UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)

-  [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
