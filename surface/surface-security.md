---
title: Surface セキュリティの概要
description: この記事では、Surface デバイスのセキュリティの概要について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 06/04/2021
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: 67ba96129d69cafaa7a1b24ce3dde98767b676ef
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614118"
---
# <a name="surface-security-overview"></a>Surface セキュリティの概要

セキュリティ調査の最近の進歩は、OS と接続されたサービスにより多くの保護が組み込む中で、攻撃者はファームウェアがトップ ターゲットとして出現する他の悪用の道を探しているという結果を示しています。

今日、デバイス ファームウェアの管理は一貫性のないエクスペリエンスであり、多くの場合、サード パーティプロバイダーがファームウェアの監視を困難にし、保守が複雑になります。 最終的には、ハードウェアメーカーが脅威に対応して、更新プログラムを検出してプッシュアウトする機能が制限される可能性があります。

Microsoft Surface は、2015 年以来、ハードウェア設計の完全なエンドツーエンドの所有権、企業のファームウェア開発、およびデバイスの更新と管理に対する全体的なアプローチを通じて、ファームウェア保護とデバイスセキュリティに統合されたアプローチを使用しています。

Surface の場合、統合拡張可能ファームウェア インターフェイス (UEFI) 1 は、Windows Update を通じて定期的に更新され <sup> [](#references) </sup> 、Windows Autopilot を通じて管理用にシームレスに展開され、デバイスの起動前にリスクを最小限に抑え、ファームウェア レベルでの制御を最大化します。 Microsoft は、UEFI のコード ベースの完全な透明性を、GitHub で管理するオープン ソース Project [Mu](https://microsoft.github.io/mu/)をMicrosoft エンドポイント マネージャー。

## <a name="microsoft-designed-and-built-components"></a>Microsoft が設計および構築したコンポーネント

Surface のチップからクラウドまでの各層は、Microsoft によって開発および保守され、どこにいても作業が行われる場合でも、最終的な制御、予防的な保護、および安心感を提供します。 Surface デバイスには、Microsoft が提供する最も強力なセキュリティ プロトコルが組み込み、IT の複雑さを軽減する合理化された管理が可能になります。これにより、ユーザーは作業に集中できます。

Surface は、独立した防御サブコンポーネントのレイヤーを利用して、防御の詳細なアプローチを通じてセキュリティを強化します。 チップからクラウド、または信頼のルートを保証する UEFI から、高度な脅威を防止、検出、調査、および対応するために機能する AI を搭載した Microsoft Defender for Endpoint まで、Surface は Microsoft の組み込み機能がボルトオンよりも優れた位置を強制します。

| 機能                         | 説明                                                                                                                                                                                                                                                                                                                         | 詳細情報                                                                                                                                                                   |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft Built UEFI            | デバイスを構成し、デバイスを起動するWindows 10<br>デバイスとデバイスの初期起動をWindows 10、OS にファームウェア ランタイム サービスを提供します。 SEMM on-prem 管理および DFCI クラウドベースの管理を使用して、デバイスのハードウェアを大幅に制御Microsoft エンドポイント マネージャー | [Surface UEFI の設定の管理](manage-surface-uefi-settings.md)                                                                        |
| 物理 TPM 2.0                | 信頼できるプラットフォーム モジュール - 統合された暗号化キーを使用してハードウェアをセキュリティで保護するように設計された専用のマイクロコントローラ。<br>キーの暗号化と保存 (BitLocker、Windows Hello、AD資格情報、)<br>PCR - プラットフォーム構成 以前の構成の変更を検出するための測定値と関連する指標をセキュリティで保護するレジスタ  | [トラステッド プラットフォーム モジュール技術概要](/windows/security/information-protection/tpm/trusted-platform-module-overview)                 |
| Windows Hello for Business      | PC とモバイル デバイスの強力な 2 要素認証にパスワードを置き換えます。 この生体認証は、デバイスに関連付け、生体認証または PIN を使用する新しい種類のユーザー資格情報で構成されます。                                                                                                                   | [ビジネスWindows Helloのしくみ - Microsoft 365 セキュリティ](/windows/security/identity-protection/hello-for-business/hello-how-it-works) |
| 統合暗号化           | BitLocker では、統合暗号化を有効にしてデータをセキュリティで保護し、暗号化し、Windows Hello TPM と UEFI を組み合わせてパスワードレス ログインを有効にします。                                                                                                                                                                 | [BitLocker (Windows 10) - Microsoft 365 セキュリティ](/windows/security/information-protection/bitlocker/bitlocker-overview)                     |
| Microsoft Defender for Endpoint | エンタープライズ ネットワークが高度な脅威を防止、検出、調査、および対応するために設計されたエンタープライズ エンドポイント セキュリティ プラットフォームを提供します。                                                                                                                                                                               | [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)                 |

## <a name="factory-level-security-protocols-and-inspection"></a>ファクトリ レベルのセキュリティ プロトコルと検査

ファームウェアからオペレーティング システム、および最終組み立て前のハードウェアのすべてのコンポーネントまで、Surface デバイスは物理的にセキュリティで保護された開発および製造施設でのサプライ チェーン攻撃から安全です。

定義上、安全なサプライ チェーンは、品質、パフォーマンス、および運用目標を満たす完成した製品を提供します。 簡単に言うと、安全なサプライ チェーンを使用すると、すべてのコンポーネントが正規品であり、不正または悪意のある操作や妨害を受け入れなくる必要があります。 UEFI ファームウェアからオペレーティング システムまで、Microsoft から直接提供される高度にセキュリティで保護された工場でデバイスを製造しています。 サードパーティの BIOS ベンダーは関係なし。 これは、Surface 製品のサプライ チェーン攻撃から保護する方法の強力な部分です。 デバイスに必要ないシステム管理モード SMM 機能を含む未使用のコードを削除することで、UEFI の攻撃 Surface を減らしました。

外部のインターネット ベースの攻撃、侵入、その他の脅威から施設を保護するには、次を含む重要な分野にわたる継続的な投資が必要です。

- 最終的なアセンブリの場所ですべてのコンポーネントの厳密な検査とテストを行います。
- 工場で高レベルの物理的なセキュリティを維持する。
- Microsoft が開発したファームウェア、& OS のみを使用します。
- Microsoft リセラーに直接 Surface デバイスのセキュリティで保護されたロジスティクスと信頼できるキャリア配信。

工場を離れると、法人向け Surfaceデバイスはライフサイクル全体を通Windows更新プログラムを介して保護されます。

## <a name="advanced-windows-security-features"></a>高度Windowsセキュリティ機能

特権攻撃のエスカレーションは悪意のあるアクターの親友であり、多くの場合、メモリに格納されている機密情報をターゲットにしています。 このような攻撃は、マイナー ユーザー モードの侵害を OS とデバイスの完全な侵害に変えます。 このような攻撃に対抗するために、Microsoft は仮想化ベースのセキュリティ (VBS) とハイパーバイザーで保護されたコード整合性 (HVCI、一般にメモリ整合性とも呼ばれます) を開発しました。 VBS と HVCI は、仮想化などのハードウェア機能の機能を使用して、分離された環境で機密性の高いセキュリティ操作を実行することで、一般的で高度なマルウェアに対する保護を強化します。

Surface には、これらのWindows強化されたハードウェア セキュリティ機能が組み込みであり、既定で有効になっているセキュリティが強化されています。

## <a name="virtualization-based-security"></a>仮想化ベースのセキュリティ

仮想化ベースのセキュリティ (VBS) は、ハードウェア仮想化機能を使用して、メモリの安全な領域を通常のオペレーティング システムから作成および分離します。 Windowsこの "仮想セキュリティ モード" を使用して、多数のセキュリティ ソリューションをホストし、オペレーティング システムの脆弱性からの保護を大幅に強化し、保護を打ち破る悪意のある悪用の使用を防止できます。

### <a name="hypervisor-enforced-code-integrity-hvci"></a>Hypervisor-Enforcedコード整合性 (HVCI)

HVCI は VBS を使用して、コード整合性ポリシーの適用を大幅に強化します。 カーネル モード のコード整合性は、開始前にすべてのカーネル モード ドライバーとバイナリをチェックし、署名されていないドライバーまたはシステム ファイルがシステム メモリに読み込まれなかから保護します。 次の図に示すように、HVCI は分離された実行環境で実行され、カーネル署名ポリシーに従ってカーネル コードの整合性を確認します。

VBS と HVCI の両方が、次の Surface デバイスで有効になっています。

- Surface Laptop 4
- Surface Pro 7+
- Surface Book 3,
- Surface LaptopGo,
- Surface Pro X

## <a name="secure-boot-and-boot-guard"></a>セキュア ブートとブート ガード

Surface デバイスの信頼のルートは、署名と測定値をチェックして、各ステージが安全で確実に実行され、次の起動フェーズを続行できるようにします。 UEFI と TPM 2.0 で有効になっている Secure Boot を使用すると、Surface デバイス上でコードの署名、測定、および正しく実装されたコードのみを実行できます。

図 2 に示すように、電源ボタンの押下からオペレーティング システムの実行まで、各段階でファームウェアの整合性がチェックされます。

 > [!div class="mx-imgBorder"]
 > ![図 1. Surface デバイスのセキュア ブート ](images/secboot.png)
  *図 1.Surface デバイスのセキュア ブート*

| ステップ  | セキュア ブート フェーズ                                                                                                                                                                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | TPM によって提供される信頼のルートから電源ボタンを押すごとに、セキュリティがインスタンス化されます。 デバイスの電源が最初にオンの場合、システムは一連のセキュリティ チェックを実行して、デバイス のファームウェアが改ざんまたは破損していないか確認します。 |
| **2** | 電源をオンにした場合、SoC はチップセット ベンダー キーを使用して、認証コード モジュール (ACM) (Intel ベースのデバイス) を使用してマイクロコードの読み込みを検証して開始します。                                                                              |
| **3** | ACM は、読み込む前に UEFI コードを測定し、TPM のプラットフォーム構成レジスタ [PCR] の既知の測定値と比較して、UEFI コードが変更されていないか確認します。                                                                |
| **4** | UEFI の実行を許可する前に、Boot Guard は UEFI が Surface OEM キーで署名されているのを確認します。 最初にチェックされた UEFI モジュールは、SEC セキュリティと、図に示す PEI Pre-EFI セクションです。                                                |
| **5** | PEI セクションでは、ドライバーの実行環境である DXE モジュールが読み込まれると、Surface 署名がチェックされます。 DXE モジュールには、ブート デバイスの選択フェーズが含まれています。                                                                          |
| **6** | ブート デバイスを選択すると、UEFI はブート デバイスを読み取り、OS ブート ローダーの署名を確認してから実行を許可します。                                                                                                             |
| **7** | その後、OS はメイン コンポーネントの署名を確認し、OS を起動します。

### <a name="malware-protection"></a>マルウェア保護

悪意のあるソフトウェア攻撃からデバイスを保護するために、Surface はセキュア ブートを有効にし、Windows 10 の本格的なバージョンが開始され、ファームウェアが工場出荷時の状態から離れた時と同じ本物の状態を保証します。

Surface デバイスの SoC には、他のすべてのコアとは別のセキュリティ プロセッサがあります。 Surface デバイスを最初に起動すると、セキュリティ プロセッサだけが起動してから、他のデバイスを読み込む必要があります。 セキュア ブートは、ブート プロセスのコンポーネント (ドライバー、オペレーティング システムなど) が、有効で既知の署名のデータベースに照らして検証されていることを確認するために使用されます。 これにより、通常のユーザー エクスペリエンスではわからないように隠された悪意のあるコードを実行する、複製または変更されたシステムを攻撃者が実行するのを防ぐことができます。 詳しくは、[セキュア ブートの概要](/windows-hardware/design/device-experiences/oem-secure-boot)を参照してください。

オペレーティング システムが Microsoft からの発信元として確認され、Surface デバイスがブート プロセスを正常に完了すると、デバイスは実行可能コードを精査します。 オペレーティング システムのセキュリティを確保するための処理には、すべての実行可能ファイルのコード署名を識別することが関係します。それにより、Microsoft の制限に合格したものだけがランタイムに読み込まれるようになります。 このコード署名方式により、オペレーティング システムで作成者を検証し、デバイス上で実行する前にコードが変更されていないことを確認できます。

## <a name="drtm-protection-in-amd-devices"></a>AMD デバイスでの DRTM 保護

AMD プロセッサを含む Surface デバイスは、同等の方法で Secure Boot を実装します。 Surface Laptop Ryzen Microsoft Surface Edition プロセッサを使用して 4 を使用すると、動的信頼測定値 (DRTM) を使用して初期電源オンからファームウェアを保護します。DRTM は、すべての CPU を制御し、測定されたパスに沿って実行を強い、システム ファームウェア/ソフトウェアの整合性を確認するためにさまざまな段階で信頼を再確立します。 この信頼された状態に早期に移行すると、起動段階での潜在的な攻撃に対する保護が強化されます。

DRTM は、システム メモリの合計暗号化 (TSME) を使用して測定値を暗号化することで、測定値を保護します。 システムのリセット以外でクリアできない場合は、TSME を設定します。 リセットごとに新しい暗号化キーを使用すると、セキュリティのための単一の使用暗号化が保証されます。

システム管理モード (SMM) へのランタイム呼び出しは最高レベルで実行されます。SMM コードに問題がある場合はリスクが高い場合があります。 Surface Laptop 4 と AMD Ryzen は、システム管理割り込み (SMI) を傍受してシステムを保護し、SMM コードの実行をより低いレベル (ユーザー) にディスパッチして、コードとデータへの無効なアクセスからシステムを保護します。 SMM 保護では、ハードウェア保護を使用して、アクセスできるコード、データ、およびシステム リソースを制限し、不注意または悪意のあるインシデントに対する保護をさらに強化します。

Surface Laptop Ryzen の 4 では、堅牢なファームウェア更新プログラムのサポートに加えて[、NIST 800-193](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-193.pdf)プラットフォーム ファームウェアの復元ガイドラインがサポートされています。 ブート ファームウェアの回復力のある更新メカニズムは、ブート シーケンスがブート中にファームウェアの破損したコピーを検出した場合に、ファームウェアのバックアップ コピーに自動回復を提供する A-B 回復メカニズムを使用します。

DRTM と SMM の詳細については、「How a Windows Defender System Guard がセキュリティ 保護をWindows 10 [- Windows」を参照|Microsoft Docs](/windows/security/threat-protection/windows-defender-system-guard/how-hardware-based-root-of-trust-helps-protect-windows)

## <a name="remote-device-management-control"></a>リモート デバイス管理制御

IT 管理者は、すべてのデバイスに物理的に触れることなく、Surface デバイスをリモートで管理できます。 Microsoft エンドポイント マネージャーおよび Windows自動パイロットを使用すると、Azure Cloud から Surface デバイスを完全にリモートで管理し、起動時に完全に構成されたデバイスをユーザーに配信できます。 ワイプ機能と廃止機能を使用すると、IT は新しいリモート ユーザー用にデバイスを簡単に再利用し、盗まれたデバイスをワイプできます。 これにより、Surface デバイスの紛失や盗難が発生した場合に迅速かつ安全な応答機能を使用して、すべての会社のデータをリモートから削除し、Surface を完全に新しいデバイスとして再構成できます。

| 機能                                        | 説明                                                                                                                                                                                                                                                                                                                                                                                                        | 詳細情報                                                                                                                                                                                                                                                              |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DCFI (デバイス ファームウェア構成インターフェイス) | ゼロタッチ デバイスプロビジョニングを使用して、クラウド規模のリモート ファームウェア管理を提供します。 Microsoft 独自の UEFI により、より強力な DCFI 実装が可能になります。これにより、組織はハードウェア要素を無効にし、Intune を使用してリモートで UEFI をロックできます。 ¹                                                                                                                                                                          | [Surface UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)<br> <br>[Surface UEFI の設定の管理](manage-surface-uefi-settings.md)                                          |
| SEMM (Surface Enterprise管理モード)      | オンプレミス環境、ハイブリッド環境、クラウド環境全体で UEFI ファームウェア設定の一元的なエンタープライズ エンゲージメントを実現します。¹                                                                                                                                                                                                                                                                                           | [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)                                                                                                                                                       |
| Windows Update for Business                    | IT 管理者は、これらのシステムを Windows Update サービスに直接接続することにより、組織の Windows 10 デバイスを最新のセキュリティ防御、Windows 機能、および Surface ファームウェアで常に最新の状態に保ちます。 グループ ポリシーや MDM ソリューション (Microsoft Intune など) を使用して、Surface デバイスの更新方法と更新Windowsを制御する Windows Update for Business の設定を構成できます。 | [Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb)<br> <br>[Surface のドライバーおよびファームウェアの更新プログラムを管理および展開する](manage-surface-driver-and-firmware-updates.md) |

## <a name="references"></a>参考資料

1. Surface Go と Surface Go 2 はサードパーティの UEFI を使用し、DFCI はサポートされていません。 DFCI は現在、Surface Laptop 4、Surface Laptop Go、Surface Book 3、Surface Laptop 3、Surface Pro 7+、Surface Pro 7、Surface Pro X で使用できます。 

## <a name="learn-more"></a>詳細情報

- [新しい Surface PC を使用すると、仮想化ベースのセキュリティ (VBS) が既定で有効になって、より多くのことを安全に実行できます。](https://www.microsoft.com/security/blog/2021/01/11/new-surface-pcs-enable-virtualization-based-security-vbs-by-default-to-empower-customers-to-do-more-securely/)
- [Surface ファームウェア保護の重要な役割を強調する調査](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/study-highlights-critical-role-of-surface-firmware-protection/ba-p/2245244)
- [Microsoft Surface および Microsoft Surface および Microsoft Surface のセキュリティとコンプライアンスを強化Microsoft 365](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/enhancing-security-and-compliance-with-microsoft-surface-and/ba-p/2283062)
- [Surface UEFI の設定の管理](manage-surface-uefi-settings.md)
- [Surface UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)
- [ProjectMu](https://microsoft.github.io/mu/)
