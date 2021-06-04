---
title: Surface Hub のセキュリティ概要
description: このページでは、Surface Hub の多層防御設計と、Surface Hub 2S におけるセキュリティ機能強化としてワイヤレス セキュリティ保護および関連機能について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: coveminer
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 01/26/2021
ms.localizationpriority: High
ms.openlocfilehash: 446166618161fc54a77bab94b2d61ad85359a082
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304850"
---
# Surface Hub のセキュリティ概要

Surface Hub は、Windows 10 Team オペレーティング システムを実行するカスタム プラットフォーム ファームウェアで、ロックダウンされたアプライアンスのようなエクスペリエンスを提供します。 これによりデバイスは、従来の "単一使用" セキュア キオスクの "必要なものだけを実行する" 戦略を採用し、それに基づいて先進のセキュリティを実現できます。 Surface Hub は、多様なコラボレーション ユーザー エクスペリエンスに対応するように構築されていて、常に進化しているセキュリティの脅威から保護されています。

Windows 10 上に構築されている Surface Hub は、エンタープライズ レベルの最新のセキュリティを実現します。IT 管理者は、BitLocker、トラステッド プラットフォーム モジュール 2.0 (TPM)、さらには Windows Defender (Microsoft Defender とも呼ばれます) を使用したクラウドベースのセキュリティを使ってデータ保護を強化できます。

##  <a name="defense-in-depth-security"></a>多層防御セキュリティ

セキュリティ プロトコルは Surface Hub が有効になるとすぐに開始されます。 ファームウェア レベルで開始されると、Surface Hub は複数のセキュリティ チェックに反応してオペレーティング システムとそのコンポーネントの読み込みのみを行います。 Surface Hub では、多層防御と呼ばれる戦略が採用されています。この戦略では、独立した防御サブコンポーネントを多層化することによって、部分的に障害が発生した場合にシステム全体を保護します。 この業界手法は、潜在する一方的なエクスプロイトや、サブコンポーネント内の脆弱性を極めて効率的に軽減する実効性があることが分かっています。

最新の Unified Extensible Firmware Interface (UEFI) は、認証済みの Windows 10 Team オペレーティング システムのみを内部ストレージから起動するように、Microsoft によって静的かつ安全に構成されています。  Surface Hub で実行されるすべてのコード行には、実行前に検証される署名が含まれています。 オペレーティング システムの一部としてであれ、Microsoft Store を介してインストールされたものであれ、Microsoft による署名のあるアプリケーションのみが、Surface Hub 上で実行できます。 これらの要件を満たさないコードやアプリはブロックされます。

Surface Hub のセキュリティ システムには以下のものが含まれます。

- **ブート時防御。** 信頼できる Surface Hub オペレーティング システム コンポーネントのみを読み込みます。
- **オペレーティング システム防御。** 意図しない、または悪意のあるソフトウェアやコードの実行を防ぎます。
- **ユーザー インターフェイス防御。** コマンドラインからの実行可能ファイルの実行などのリスクのあるアクティビティへのアクセスを防止し、エンドユーザーを安全に保護するユーザー インターフェイスを提供します。

###  <a name="boot-time-defenses"></a>ブート時防御

SoC には、他のコアとは分離しているセキュリティ プロセッサが備わっています。 Surface Hub を初めて起動すると、このセキュリティ プロセッサのみが開始されてから、他のものを読み込めるようになります。

![セキュリティ プロセッサ保護が示されている Hub スタートアップ ブート フェーズ](images/hub-sec-1.png)

#### セキュア ブート

セキュア ブートは、ブート プロセスのコンポーネント (ドライバー、オペレーティング システムなど) が、有効で既知の署名のデータベースに照らして検証されていることを確認するために使用されます。 Surface Hub では、認定された Windows Team オペレーティング システムを読み込めるようになるには、その前に、プラットフォーム固有の署名を検証する必要があります。 これにより、通常のユーザー エクスペリエンスではわからないように隠された悪意のあるコードを実行する、複製または変更されたシステムを攻撃者が実行するのを防ぐことができます。  詳しくは、[セキュア ブートの概要](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot)を参照してください。

###  <a name="operating-system-defenses"></a>オペレーティング システム防御

オペレーティング システムの発行元が Microsoft であることが確かめられ、Surface Hub によってブート プロセスが正常に実行されると、実行可能コードがデバイスによって綿密に検証されます。 オペレーティング システムのセキュリティを確保するための処理には、すべての実行可能ファイルのコード署名を識別することが関係します。それにより、Microsoft の制限に合格したものだけがランタイムに読み込まれるようになります。 このコード署名方式により、オペレーティング システムで作成者を検証し、デバイス上で実行する前にコードが変更されていないことを確認できます。

Surface Hub では、Windows Application Control (旧称 Device Guard) で User Mode Code Integrity (UMCI) というコード署名機能が使用されます。 以下のいずれかの要件を満たすアプリのみが許可されるようにポリシー設定が構成されています。

- [公式認定を受けた](https://docs.microsoft.com/windows/uwp/publish/the-app-certification-process)ユニバーサル Windows プラットフォーム (Microsoft Store) アプリ。
- 一意の Microsoft 製品ルート証明機関 (CA) による署名を受けたアプリ。この署名は、これらの証明書に対する承認されたアクセス権を持つ Microsoft 社員のみが行えます。
- 一意の Surface Hub 製品ルート CA による署名を受けたアプリ。

構成ファイルは、サードパーティによって制限が取り除かれたり変更されたりすることがないように、Microsoft 製品ルート証明機関によって署名されます。 この時点で他のすべての実行ファイルはオペレーティング システム ランタイム レベルで単純にブロックされ、処理能力に影響しないようにできます。 この攻撃表面の縮小によって、以下の保護が提供されます。

- 従来のドキュメント モードがないようにする
- レガシ スクリプト エンジンがないようにする
- Vector Markup Language がないようにする
- ブラウザー ヘルパー オブジェクトがないようにする
- ActiveX コントロールがないようにする

UMCI を使用して未署名または不適切な署名があるコードをブロックすることに加え、Surface Hub は Windows Application Control を使用して、コマンド プロンプト、PowerShell、タスク マネージャーなどの Windows コンポーネントをブロックします。 これらの保護機能は、セキュア コンピューティング アプライアンスとしての Surface Hub の主要な設計機能を反映しています。 詳細については、以下を参照してください。

- [アプリケーション制御の概要](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender アプリケーション制御とコード整合性の仮想化ベースの保護](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

###  <a name="user-interface-defenses"></a>ユーザー インターフェイス防御

ブート時防御とオペレーティング システム ロックダウン保護によって基礎的なセキュリティが確保され、ユーザー インターフェイスでは、リスクをさらに軽減するための追加の層が用意されています。 悪意のあるコードがデバイスにドライバー経由で達するのを防ぐため、Surface Hub はプラグ アンド プレイ (PnP) デバイス用の拡張ドライバーをダウンロードしません。 USB フラッシュ ドライブ、Surface Hub 認定周辺機器 (スピーカー、マイク、カメラ) などの基本ドライバーを使用しているデバイスは正常に動作しますが、プリンターなどの高度なシステムは期待どおりには動作しません。

また、ユーザー インターフェイス防御では UI が簡略化されているので、悪意のあるソフトウェアやコードの実行の防止がさらに強化されます。 次の Surface Hub UI 要素が、コード署名によって提供されている中核的なセキュリティを多層化しています。

- **エクスプローラー。** Surface Hub に備わっているカスタム エクスプローラーを使用すると、システム ファイルやプログラム ファイルがユーザーに表示されない方法で、音楽、ビデオ、ドキュメント、画像、およびダウンロードのフォルダーにすばやくアクセスできます。 ローカル ハード ドライブ上の他の場所は、エクスプローラーでは利用できません。 また、.exe や .msi インストール ファイルなど、多くの種類のファイルは実行できないので、悪意のある可能性がある実行可能ファイルに対する追加の層となります。

- **[スタート]、[すべてのアプリ]。** Surface Hub の [スタート] と [すべてのアプリ] のコンポーネントでは、コマンド プロンプト、PowerShell、またはアクセス制御によってブロックされる他の Windows コンポーネントにアクセスできません。 さらに、PC の検索ボックスで通常はアクセスできる Windows の実行機能は、Surface Hub では無効になっています。

##  <a name="security-enhancements-in-surface-hub-2s"></a>Surface Hub 2S におけるセキュリティ拡張機能

Surface Hub と Surface Hub 2S はどちらも同じオペレーティング システム ソフトウェアを実行しますが、Surface Hub 2S 特有の一部の機能では管理とセキュリティの機能が追加され、IT 管理者は以下のタスクを実行できます。

- SEMM で UEFI 設定を管理する
- ブート可能 USB を使用して Hub を回復する
- パスワードの循環によってデバイス アカウントを強化する

###  <a name="manage-uefi-settings-with-semm"></a>SEMM で UEFI 設定を管理する

UEFI は、基盤となるハードウェア プラットフォーム要素とオペレーティング システム間のインターフェイスです。 Surface Hub ではカスタムの UEFI が実装されているので、これらの設定をきめ細かく制御でき、Microsoft 以外のエンティティがデバイスの UEFI 設定を変更したり、リムーバブル ドライブからブートしてオペレーティング システムに変更を加えたりするのを防げます。

大まかに言うと、工場出荷処理中に、Surface Hub UEFI はセキュア ブートを有効にするように事前構成され、UEFI メニューがロックされてショートカットが除去された、内部 SSD (Solid-State Drive) からのみブートできるように設定されています。 これにより UEFI によるアクセスが封印され、デバイスが Surface Hub にインストールされている Windows Team オペレーティング システムでのみブートできるようになります。

Microsoft Surface Enterprise Management Mode (SEMM) を使用して管理する場合、IT 管理者は、組織全体の Hub デバイスに UEFI 設定を配置できます。 これには、組み込みのハードウェア コンポーネントの有効化/無効化、許可されていないユーザーによる UEFI 設定の変更の禁止、ブート設定の調整が含まれます。

![Surface Hub UEFI 設定](images/hub-sec-2.png)

管理者は SEMM を実装し、ダウンロード可能な [Microsoft Surface UEFI コンフィギュレータ](https://www.microsoft.com/download/details.aspx?id=46703)を使用して登録された Surface Hub 2S デバイスを実装できます。 詳しくは、[SEMM と UEFI による Surface Hub 2S のセキュリティ保護と管理](https://docs.microsoft.com/surface-hub/surface-hub-2s-secure-with-uefi-semm)を参照してください。
SEMM では、許可されていない改ざんや削除から構成を保護するために証明書を使用してセキュリティで保護し、以下のコンポーネントを管理できます。

- ワイヤード (有線) LAN
- カメラ
- Bluetooth
- Wi-Fi
- 占有センサー
- PXE ブート用 IPv6
- 代替ブート
- ブート順序ロック
- USB ブート
- UEFI フロント ページ インターフェイス
    - デバイス
    - Boot
    - 日付/時刻

    
###  <a name="recover-hub-with-bootable-usb"></a>ブート可能 USB を使用して Hub を回復する

Surface Hub 2S では、管理者は、早ければわずか 20 分以内に回復イメージを使用してデバイスを出荷時の設定に再インストールできます。 通常、この操作が必要になるのは、Surface Hub が正常に動作しなくなった場合のみです。 回復は、Bitlocker キーを紛失した場合や、設定アプリへの管理者資格情報がなくなった場合にも役立ちます。

###  <a name="harden-device-account-with-password-rotation"></a>パスワードの循環によってデバイス アカウントを強化する

Surface Hub では、Exchange、Microsoft Teams、その他のサービスで認証を受けるために「ルーム アカウント」とも呼ばれるデバイス アカウントを使用します。 パスワードの循環を有効にすると、Hub 2S によって 7 日ごとに新しいパスワードが自動的に生成されます。パスワードは、大文字、小文字、数字、特殊文字を組み合わせた 15 から 32 文字の範囲で構成されます。 このパスワードは誰も知らないので、デバイス アカウントでパスワードの循環を使用すると、人的なエラーやソーシャル エンジニアリングのセキュリティ攻撃の可能性に関連するリスクを効率的に低減できます。

##  <a name="windows-10-enterprise-grade-security"></a>Windows 10 のエンタープライズ レベルのセキュリティ

この資料で扱われている Surface Hub 特有の構成および機能に加え、Surface Hub では Windows 10 標準のセキュリティ機能も使用しています。 以下に例を示します。

- **BitLocker**。 Surface Hub SSD には BitLocker が搭載されていて、デバイス上のデータを保護します。 その構成は業界標準に準拠しています。 詳しくは、[BitLocker の概要](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot)を参照してください。
- **Windows Defender。** Windows Defender マルウェア対策エンジンは Surface Hub で継続的に実行され、Surface Hub で検出された脅威を自動的に修復します。 Windows Defender エンジンは自動的に更新プログラムを受け取り、IT 管理者用のリモート管理ツールを使用して管理できます。 Windows Defender エンジンは、Microsoft の多層防御アプローチの最適な例です。マルウェアがコア コード サイネージ ベースのセキュリティ ソリューションの迂回路を見つけた場合でも、ここでキャッチされます。 詳しくは、[Windows Defender アプリケーション制御とコード整合性の仮想化ベースの保護](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)を参照してください。
- **プラグ アンド プレイ ドライバー。** 悪意のあるコードがデバイスにドライバー経由で達するのを防ぐため、Surface Hub は PnP デバイス用の拡張ドライバーをダウンロードしません。 これにより、USB フラッシュ ドライブなどの基本ドライバーを使用するデバイスは期待どおりに動作しますが、プリンターなどの高度なシステムはブロックされます。
- **トラステッド プラットフォーム モジュール 2.0。** Surface Hub には、暗号化キーとハッシュを生成および格納するために、業界標準の離散トラステッド プラットフォーム モジュール (dTPM) があります。 dTPM は、ブート フェーズの検証に使用されるキー、BitLocker マスター キー、パスワードなしのサインオン キーなどを保護します。 dTPM は、米国政府のコンピューター セキュリティ基準である [FIPS 140-2 Level 2](https://docs.microsoft.com/windows/security/threat-protection/fips-140-validation) 認定と、世界中で採用されている[情報セキュリティ国際評価基準](https://docs.microsoft.com/windows/security/threat-protection/windows-platform-common-criteria)認定に適合しています。

##  <a name="wireless-security-for-surface-hub"></a>Surface Hub のワイヤレス セキュリティ

Surface Hub は、Wi-Fi Direct と Miracast テクノロジ、およびそれらに関連する 802.11、Wi-Fi 保護アクセス (WPA2)、Wireless Protected Setup (WPS) 規格を使用しています。 このデバイスでは WPA2 Pre-Shared Key (PSK) や WPA2 EnterpriseWPS をサポートせず、WPS のみをサポートすることで、802.11 暗号化に伴う従来の問題に根本的に緩和しています。

Miracast は Wi-Fi Display 規格に含まれ、それ自体が Wi-Fi Display プロトコルでサポートされています。 最新のモバイル デバイスでは、これらの規格をサポートすることで画面の共有とコラボレーションを実現しています。

Wi-Fi Direct、つまり Wi-Fi 経由の "ピア ツー ピア" (P2P) は、Wi-Fi Alliance から "アドホック" ネットワークとして公開された規格です。 この規格では、規格に対応するデバイス同士が、従来のような Wi-Fi アクセス ポイントやインターネット接続経由ではなく、直接通信し、ネットワーク グループを作成できます。

Wi-Fi Direct のセキュリティは、WPS を使用する WPA2 によって提供されます。 デバイスは、数値の暗証番号 (PIN)、物理または仮想プッシュ ボタン、近距離無線通信による帯域外メッセージのいずれかを使用して認証を受けることができます。 Surface Hub は、既定のプッシュ ボタンと PIN の両方の方式をサポートしています。 詳しくは、[Surface Hub による Wi-Fi Direct のセキュリティ問題への対応](https://docs.microsoft.com/surface-hub/surface-hub-wifi-direct)を参照してください。

##  <a name="learn-more"></a>詳細情報

- [セキュア ブートの概要](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot)

- [BitLocker の概要](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)

- [アプリケーション制御の概要](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [SEMM と UEFI による Surface Hub 2S のセキュリティ保護と管理](https://docs.microsoft.com/surface-hub/surface-hub-2s-secure-with-uefi-semm)

- [Surface Hub による Wi-Fi Direct のセキュリティ問題への対応](https://docs.microsoft.com/surface-hub/surface-hub-wifi-direct)

- [Windows Defender アプリケーション制御とコード整合性の仮想化ベースの保護](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

- [IT 担当者向け Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703)

- [FIPS 140-2 レベル 2](https://docs.microsoft.com/windows/security/threat-protection/fips-140-validation)

- [共通基準の証明書](https://docs.microsoft.com/windows/security/threat-protection/windows-platform-common-criteria)
