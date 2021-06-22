---
title: オペレーティングシステムの基礎 (Surface Hub)
description: このトピックでは、オペレーティング システムの固有の側面Windows 10 Team、オペレーティング システムと異なる点Windows 10 Enterprise。
keywords: 変更履歴
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/23/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 54fe39fe35a63d27447fb0b4a01642f249475afc
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613816"
---
# <a name="operating-system-essentials-surface-hub"></a>オペレーティングシステムの基礎 (Surface Hub)

Surface Hub のオペレーティング システムである Windows 10 Team は Windows 10 Enterprise をベースとしていて、エンタープライズ管理、セキュリティ、およびその他の機能の豊富なサポートを提供します。 しかし、これらの間には重要な違いがあります。 Enterprise エディションは、PC 向けに設計されていますが、Windows 10 Team は大画面および会議室での使用向けに新たに設計されています。 Surface Hub のセキュリティおよび管理の要件を評価する場合、新しいオペレーティング システムと見なすことをお勧めします。 この記事は、Surface Hub の Windows 10 Team と Windows 10 Enterprise の主な相違点と、その相違点が組織にどう影響を与えるかを示すことを目的としています。

2020 年 9 月から、お客様は 2S の Windows 10 Pro または EnterpriseにSurface Hubできます。 詳しくは、次のトピックをご覧ください。

- [2. 2 でWindows 10 ProとEnterpriseのSurface Hubします](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/announcing-the-availability-of-windows-10-pro-and-enterprise-on/ba-p/1624107)。

- [Surface Hub 2 の Windows 10 Pro または Enterprise に移行する](surface-hub-2s-migrate-os.md)

## <a name="user-interface"></a>ユーザー インターフェイス

### <a name="shell-os-user-interface"></a>シェル (OSのユーザー インターフェイス)

Surface Hub のシェルは、大画面での表示およびタッチ操作向けに、新たに設計されています。 Windows 10 Enterprise と同じシェルは使用されていません。

*これにより影響を受ける可能性のある組織ポリシー:* <br> Windows 10 Enterprise のシェルのコントロールに関する設定は、Surface Hub には適用されません。

### <a name="lock-screen-and-screensaver"></a>ロック画面とスクリーン セーバー

Surface Hub にはロック画面やスクリーン セーバーがありませんが、ようこそ画面と呼ばれる同様の機能があります。 ようこそ画面には、デバイス アカウントのカレンダーでスケジュール設定済みの会議、および Skype for Business、ホワイトボード、接続といった Surface Hub のトップ アプリへの簡易エントリ ポイントが表示されます。

*これにより影響を受ける可能性のある組織ポリシー:* <br> ロック画面、画面のタイムアウト、およびスクリーン セーバーの設定は、Surface Hub には適用されません。

### <a name="user-sign-in"></a>ユーザー サインイン

Surface Hub は、会議室などの共同スペースで使用できるように設計されています。 Windows PC とは異なり、ユーザーにサインインが求められることなく、だれでも Surface Hub を使用できます。 この共有機能を有効にするために、Surface Hub では、Windows 10 Enterprise のような (ユーザーが OS にサインインして、その資格情報が OS 全体で使用される形式の) Windows サインインがサポートされていません。 代わりに、ローカルで自動サインインの低特権ユーザーが、常に Surface Hub にログインしているという形になります。 管理ユーザーを含めて、追加ユーザーのサインインはサポートされません (つまり、管理者がサインインしても、OS へのサインインではありません)。

ユーザーは Surface Hub にサインインできますが、OS へのサインインにはなりません。 たとえば、ユーザーがアプリまたは "会議とファイル" にサインインしても、このユーザーは OS ではなくアプリまたはサービスにサインインしているだけです。 結果として、サインインしたユーザーは、自身のクラウド ファイルや、クラウドに保存されている個人的な会議を取得できますが、**[セッションの終了]** が有効になると資格情報が破棄されます。


*これにより影響を受ける可能性のある組織ポリシー:* <br> 通常、Surface Hub ではセキュリティ強化のため、ユーザー アクセス制御ではなくロックダウン機能を使用します。 パスワード要件、対話型ログオン、ユーザー アカウント、およびアクセス制御に関するポリシーは、Surface Hub には適用されません。

### <a name="saving-and-browsing-files"></a>ファイルの保存と参照

ユーザーがアクセスできるのは、次に示す Surface Hub の一部のディレクトリのみです。
- ミュージック
- ビデオ
- ドキュメント
- ピクチャ
- ダウンロード

これらのディレクトリにローカルに保存されたファイルは、ユーザーが **[セッションの終了]** を押すと削除されます。 会議中に作成したコンテンツを保存するには、USB ドライブや OneDrive にファイルを保存する必要があります。

*これにより影響を受ける可能性のある組織ポリシー:* <br> アクセス許可およびファイルとフォルダーの所有権に関するポリシーは、Surface Hub には適用されません。 ユーザーは、システム ディレクトリやネットワーク フォルダーを参照したり、そこにファイルを保存したりすることはできません。

## <a name="applications"></a>アプリケーション

### <a name="default-applications"></a>既定のアプリケーション

ほとんど例外なく、Surface Hub の既定の ユニバーサル Windows プラットフォーム (UWP) アプリは、Windows 10 PC でも利用可能です。

Surface Hub にプレインストールされている UWP アプリ:

- アラーム & クロック
- 電卓
- 接続
- Excel Mobile
- フィードバック Hub
- エクスプローラー
- はじめに
- マップ
- Microsoft Edge
- Microsoft Power BI
- Microsoft Teams
- Microsoft Whiteboard
- OneDrive
- フォト
- PowerPoint Mobile
- 設定
- ストア
- ヒント
- Word Mobile

*これにより影響を受ける可能性のある組織ポリシー:* <br> Windows 10 Enterprise のガイドラインを使用して、Surface Hub の既定のアプリの機能およびネットワーク要件を判断します。

### <a name="installing-apps-drivers-and-services"></a>アプリ、ドライバー、およびサービスのインストール

アプライアンスのようなデバイス特性を維持するために、Surface Hub でサポートされているのはユニバーサル Windows プラットフォーム (UWP) アプリのインストールのみで、従来の Win32 アプリ、サービス、およびドライバーのインストールはサポートされていません。 さらに、UWP アプリをインストールするためのアクセス権を持つのは管理者だけです。

*これにより影響を受ける可能性のある組織ポリシー:* <br> 従業員は管理者がインストールしたアプリを使用することしかできないため、意図しない使用の軽減に役立ちます。 Surface Hub では、従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。

## <a name="security-and-lockdown"></a>セキュリティとロックダウン

会議室などの共同スペースで使用するため、Surface Hub のカスタム OS には、Windows 10 で利用可能なセキュリティ機能とロックダウン機能の多くが実装されています。

Surface Hub に実装されている Windows 10 のセキュリティ機能:
- [UEFI セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)
- [Windows Defender アプリケーション制御とコード整合性の仮想化ベースの保護](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [AppLocker を使用したアプリケーション制限ポリシー](https://technet.microsoft.com/itpro/windows/keep-secure/applocker-overview)
- [BitLocker ドライブ暗号化](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview)
- [トラステッド プラットフォーム モジュール (TPM)](https://technet.microsoft.com/itpro/windows/keep-secure/trusted-platform-module-overview)
- [Microsoft Defender](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-in-windows-10)
- 設定アプリにアクセスするための[ユーザー アカウント制御 (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview)

これらの Surface Hub 機能によって提供される追加のセキュリティ:
- カスタムの UEFI ファームウェア
- デバイスを会議機能だけに制限するカスタムのシェルとスタート メニュー
- マイ ドキュメントに含まれるファイルとフォルダーへのアクセスのみを許可するカスタムのエクスプローラー
- デバイス設定の変更を管理者にのみ許可するカスタムの設定アプリ
- 高度なプラグ アンド プレイ ドライバーのダウンロードの無効化

*これにより影響を受ける可能性のある組織ポリシー:* <br> Surface Hub のセキュリティの評価を行うときは、これらの機能を考慮してください。

詳細については、「セキュリティの概要[Surface Hub」を参照してください。](surface-hub-security.md)

## <a name="management"></a>管理

### <a name="device-settings"></a>デバイス設定

デバイス設定は、設定アプリで構成できます。 設定アプリは Surface Hub 用にカスタマイズされていますが、Windows 10 デスクトップで使い慣れた設定も多く含まれています。 設定アプリを開くと、管理者の資格情報を検証するためにユーザー アカウント制御 (UAC) のプロンプトが表示されますが、管理者としてサインインすることはできません。

*これにより影響を受ける可能性のある組織ポリシー:* <br> 従業員は会議で Surface Hub を使用できますが、デバイスの設定を変更することはできません。 ロックダウン機能と UAC により、従業員は会議機能の使用しかできません。

### <a name="administrative-features"></a>管理機能

Microsoft 管理コンソール、ファイル名を指定して実行、コマンド プロンプト、PowerShell、レジストリ エディター、イベント ビューアー、タスク マネージャーといった Windows 10 Enterprise の管理機能は、Surface Hub ではサポートされていません。 設定アプリに、Surface Hub のローカルで利用可能な管理機能がすべて含まれています。

### <a name="remote-management-and-monitoring"></a>リモート管理および監視

Surface Hubは、Azure Monitor を介したリモート 管理や監視などのモバイル[デバイス管理](/mem/intune/)(MDM) ソリューションMicrosoft Intuneを[サポートします](/azure/azure-monitor/)。 

*これにより影響を受ける可能性のある組織ポリシー:* <br> Surface Hub では、System Center Operations Manager といった従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。

### <a name="group-policy"></a>グループ ポリシー

Surface Hub監査を含むWindowsグループ ポリシーはサポートされていません。 代わりに、MDM を使用して Surface Hub にポリシーを適用します。 MDM について詳しくは、「[MDM プロバイダーによる設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。

*これにより影響を受ける可能性のある組織ポリシー:* <br> グループ ポリシーではなく MDM を使用して Surface Hub を管理します。

### <a name="remote-assistance"></a>リモート アシスタンス

Surface Hub では、リモート アシスタンスがサポートされていません。

*これにより影響を受ける可能性のある組織ポリシー:* <br> リモート アシスタンスに関するポリシーは、Surface Hub には適用されません。

## <a name="network"></a>ネットワーク

### <a name="domain-join-and-azure-active-directory-azure-ad-join"></a>ドメイン参加と Azure Active Directory (Azure AD) 参加 

Surface Hub は主にドメイン参加と Azure AD 参加を使用して、ディレクトリでサポートされる管理者グループを提供します。 ハイブリッド参加はサポートされていません。 ユーザーは、ドメイン アカウントではサインインできません。 詳しくは、「[管理者グループの管理](admin-group-management-for-surface-hub.md)」をご覧ください。

*これにより影響を受ける可能性のある組織ポリシー:* <br> Surface Hub がドメインに参加している場合、グループ ポリシーは適用されません。 ドメイン メンバーシップに関するポリシーは、Surface Hub には適用されません。

### <a name="accessing-domain-resources"></a>ドメインのリソースへのアクセス

ユーザーは、Microsoft Edge にサインインしてイントラネット サイトと (Office 365 などの) オンライン リソースにアクセスできます。 Surface Hub がデバイス アカウントで構成されている場合は、システムはそのアカウントを使用して Exchange と Skype for Business にアクセスします。 ただし、Surface Hub では、ファイル共有やプリンターといったドメインのリソースへのアクセスはサポートされていません。

*これにより影響を受ける可能性のある組織ポリシー:* <br> ドメイン オブジェクトへのアクセスに関するポリシーは、Surface Hub には適用されません。

<!--
### Endpoints



*Organization policies that this may affect:* <br> 
-->

### <a name="diagnostic-data"></a>診断データ

Surface Hub の OS は、Windows 10 の接続ユーザー エクスペリエンスとテレメトリのコンポーネントを使用して診断データを収集して送信します。 詳細については、「[組織内の Windows 診断データの構成](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization)」を参照してください。

*これにより影響を受ける可能性のある組織ポリシー:* <br> Windows 10 Enterprise の場合と同じ方法で、Surface Hub の診断データのレベルを構成します。
