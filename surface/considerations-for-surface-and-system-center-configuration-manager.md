---
title: Surface および Microsoft Endpoint Configuration Manager の考慮事項
description: 構成マネージャーを使用した Surface デバイスの管理と展開は、他の PC と基本的に同じです。この記事では、追加の考慮事項が必要なシナリオについて説明します。
keywords: 管理、展開、更新、ドライバー、ファームウェア
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 4fa62d227deb0b0b07fa0fbc6552ea5b04c1b87b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834733"
---
# Surface および Microsoft Endpoint Configuration Manager の考慮事項

Microsoft Endpoint Configuration Manager を使用した Surface デバイスの基本的な管理と展開は、他の PC の管理と展開と同じです。 他の PC と同様に、Surface デバイスへの展開には、ドライバーのインポート、Windows イメージのインポート、展開タスクシーケンスの準備、タスクシーケンスのコレクションへの展開が含まれます。 展開後、Surface デバイスは、他の Windows クライアントと似ています。アプリ、設定、ポリシーを公開するには、その他のデバイスで使用するのと同じプロセスを使用します。

構成マネージャーを使用して、 [Microsoft Endpoint Configuration manager のドキュメント](https://docs.microsoft.com/sccm/index)でデバイスを展開および管理する方法の詳細については、こちらを参照してください。

Surface デバイスの展開と管理は、どの PC とも基本的に同じですが、追加の考慮事項や手順が必要になる場合があります。 この記事では、これらのシナリオの説明とガイダンスについて説明します。 この記事で説明されているソリューションは、他のデバイスや製造元にも適用される可能性があります。

> [!NOTE]
> Surface デバイスを管理するには、Microsoft Endpoint Configuration Manager の現在の分岐を使用することをお勧めします。

##  <a name="updating-surface-device-drivers-and-firmware"></a>Surface デバイスドライバーとファームウェアの更新

Windows Update を使用して更新プログラムを受け取るデバイスの場合、Surface コンポーネント (およびファームウェアの更新プログラムも含む) のドライバーは、Windows Update プロセスの一部として自動的に適用されます。 Windows Server Update Services (WSUS) 経由で更新されたデバイスや構成マネージャーなど、管理された更新プログラムがあるデバイスについては、「 [Surface ドライバーとファームウェア更新プログラムを管理](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates/)する」をご覧ください。

> [!NOTE]
> Surface デバイスドライバーとファームウェアは、Windows Server 2008 R2 ではネイティブでサポートされていませんが、SHA-256 を使って署名されています。 回避策は、Windows Server 2008 R2 で実行されている Configuration Manager 環境で利用できます。 詳細については、「 [Microsoft Endpoint Configuration Manager (KB3025419) にドライバーをインポートできない](https://support.microsoft.com/kb/3025419)」を参照してください。

##  <a name="surface-ethernet-adapters-and-configuration-manager-deployment"></a>Surface Ethernet アダプターおよび Configuration Manager の展開

Configuration Manager で展開中にデバイスを識別するために使用される既定のメカニズムは、メディアアクセス制御 (MAC) アドレスです。 MAC アドレスはイーサネットコントローラーと関連付けられているため、複数のデバイス間で共有されるイーサネットアダプターによって、構成マネージャーは各デバイスを1つのデバイスとしてのみ識別します。 これにより、Windows の Configuration Manager の展開が、意図したデバイスに適用されないことがあります。

同じイーサネットアダプターを使用する Surface デバイスが展開時に一意のデバイスとして識別されるようにするには、別の方法を使用してデバイスを識別するように Configuration Manager に指示することができます。 この他の方法には、ワイヤレスネットワークアダプターの MAC アドレス、またはシステムのユニバーサル一意識別子 (システム UUID) を使うことができます。 次のオプションを使用して、Configuration Manager で他の識別方法を使用するように指定できます。

* 「 [Microsoft Endpoint Configuration Manager の OSD ブログ投稿での複数の PXE で開始された展開に同じ NIC](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/)を再利用する」で説明されているように、Surface Ethernet アダプターの mac アドレスの除外を追加します。

* [Microsoft Endpoint Configuration Manager の OSD ブログ投稿での複数の PXE で開始される展開に同じ NIC](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/)を再利用する方法に関する説明に従って、システム UUID によってデバイスを事前登録します。

* 新しい展開された Surface デバイスをワイヤレスアダプターの MAC アドレスで識別するには、スクリプトを使用します。[複数の SCCM OSD ブログ投稿に同じ外部イーサネットアダプターを使用する方法](https://blogs.technet.microsoft.com/askpfeplat/2014/07/27/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm-osd/)について説明します。

構成マネージャーを使用した展開中の Surface Ethernet アダプターのもう1つの考慮事項は、イーサネットコントローラー用のドライバーです。 Windows 10 バージョン1511以降では、Surface Ethernet アダプターのドライバーは既定で Windows に含まれています。 最新バージョンの Windows 10 を展開し、最新バージョンの WinPE を使用する組織の場合、Surface Ethernet アダプターを使うには、追加の操作は必要ありません。

Windows 10、バージョン1511より前の windows のバージョン (Windows 10 RTM および Windows 8.1 を含む) は、Surface Ethernet アダプタードライバーをインストールして、WinPE のブートメディアにドライバーを含める必要があります。 Windows 10 に組み込まれているので、Microsoft ダウンロードセンターからドライバーをダウンロードすることはできなくなりました。 Surface Ethernet adapter ドライバーをダウンロードするには、「コアチームのブログを求める」の「 [Surface Ethernet ドライバー](https://blogs.technet.microsoft.com/askcore/2016/08/18/surface-ethernet-drivers/)のブログ投稿」の説明に従って Microsoft Update カタログからダウンロードします。

##  <a name="deploy-surface-app-with-configuration-manager"></a>Configuration Manager を使用した Surface アプリの展開

Microsoft Store for Business のリリースにより、Surface アプリはドライバーとファームウェアのダウンロードとしては利用できなくなりました。 Surface アプリを管理された Surface デバイスに展開したり、Configuration Manager を使用して展開中に展開したりするには、一般法人向け Microsoft Store を通じて Surface アプリを取得し、PowerShell を使って Surface アプリを展開する必要があります。 Surface アプリの展開用の PowerShell コマンド、surface アプリをダウンロードする手順、および TechNet ライブラリのビジネス向け microsoft[ストアアプリの展開 surface アプリ](https://technet.microsoft.com/itpro/surface/deploy-surface-app-with-windows-store-for-business)での、一般法人向け microsoft store の前提条件フレームワークを見つけることができます。

##  <a name="use-prestaged-media-with-surface-clients"></a>ステージングメディアを Surface クライアントと共に使用する

構成マネージャーを使用して展開する前に、組織で事前にステージングメディアを使って展開リソースをコンピューターに事前に読み込む場合、UEFI デバイスとしての Surface デバイスの性質では、追加の手順を実行する必要があります。 具体的には、ネイティブの UEFI 環境では、システムのブートディスクに複数のパーティションを作成する必要があります。 事前にステージングされた[メディアのドキュメント](https://technet.microsoft.com/library/79465d90-4831-4872-96c2-2062d80f5583?f=255&MSPPError=-2147217396#BKMK_CreatePrestagedMedia)をフォローしている場合、手順は1つのパーティションブートディスクのみを提供するため、Surface デバイスに適用すると失敗します。

Surface デバイスなどの UEFI デバイスに事前にステージングされたメディアを適用する手順については、「 [Microsoft Endpoint Configuration Manager のブログ投稿で、BIOS または UEFI pc のマルチパーティションディスクにタスクシーケンスの事前登録済みメディアを適用する方法](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2014/04/02/how-to-apply-task-sequence-prestaged-media-on-multi-partitioned-disks-for-bios-or-uefi-pcs-in-system-center-configuration-manager/)」を参照してください。

##  <a name="licensing-conflicts-with-oem-activation-3.0"></a>OEM ライセンス認証3.0 とのライセンスの競合

Surface デバイスは、ライセンス許諾された Windows のコピーと共にプレインストールされています。 たとえば、Surface Pro 4 は Windows 10 Professional にプレインストールされています。 プレインストールされている Windows のコピーのライセンスキーは、OEM ライセンス認証 3.0 (OA 3.0) を搭載したデバイスのファームウェアに埋め込まれています。 OA 3.0 キーを持つデバイスで Windows インストールメディアを実行すると、Windows セットアップによってライセンスキーが自動的に読み取られ、windows のインストールとライセンス認証に使用されます。 ほとんどの状況では、ユーザーがライセンスキーを検索または入力する必要がないため、Windows の再インストールが簡単になります。

Windows Enterprise を使用してデバイスを再作成すると、この埋め込みライセンスキーによって競合が発生することはありません。 これは、Windows Enterprise 用のインストールメディアが Enterprise edition の Windows のみをインストールするように構成されているため、システムファームウェアに組み込まれているライセンスキーとの互換性がないためです。 プロダクトキーが指定されていない場合 (キー管理サービス (KMS) または Active Directory ベースのライセンス認証を使用してライセンス認証を行う場合など)、Windows がこれらのテクノロジのいずれかによってアクティブ化されるまで、汎用ボリュームライセンスキー (GVLK) が使用されます。

ただし、ファームウェアの埋め込みキーと互換性のあるバージョンの Windows が使用されている場合は、問題が発生する可能性があります。 たとえば、windows 10 Home edition と共に出荷された Surface 3 デバイスに Windows 10 Professional をインストールしようとしている組織では、Windows セットアップがインストール中に Home edition キーを自動的に読み取り、Professional ではなく Home edition としてインストールすると、問題が発生する可能性があります。 この競合を回避するには、Ei ファイルまたは Pid.txt ファイルを使用して、Windows セットアップでプロダクトキーの入力を求めるメッセージが表示されるようにするか、展開タスクシーケンスに特定のプロダクトキーを入力します。 詳細については、「 [Windows のセットアップエディションの構成と製品 ID のファイル](https://technet.microsoft.com/library/hh824952.aspx)」を参照してください。 特定のキーを持っていない場合は、Windows の既定のプロダクトキーを使うことができます。これは、デバイスパートナーセンターで[windows 10 オペレーティングシステムをカスタマイズして展開](https://dpcenter.microsoft.com/en/Windows/Build/cp-Windows-10-build)するときに表示されます。

##  <a name="apply-an-asset-tag-during-deployment"></a>展開時に資産タグを適用する

Surface Studio、Surface Book、Surface Pro 4、surface Pro 3、Surface 3 デバイスはすべて、UEFI での asset tag のアプリケーションをサポートしています。 このアセットタグは、オペレーティングシステムに障害が発生した場合でも UEFI からデバイスを識別するために使用できます。また、オペレーティングシステム内から照会することもできます。 Surface Asset Tag 関数の詳細については、「 [Surface Pro 3 のブログ投稿用のアセットタグツール](https://blogs.technet.microsoft.com/askcore/2014/10/20/asset-tag-tool-for-surface-pro-3/)」を参照してください。

構成マネージャーの展開タスクシーケンス中に[Surface Asset TAG CLI ユーティリティ](https://www.microsoft.com/download/details.aspx?id=44076)を使用してアセットタグを適用するには、構成マネージャーのタスクシーケンスのブログの投稿[中に、Set Surface asset タグ](https://blogs.technet.microsoft.com/jchalfant/set-surface-pro-3-asset-tag-during-a-configuration-manager-task-sequence/)に含まれるスクリプトと手順を使用します。

##  <a name="configure-push-button-reset"></a>プッシュボタンのリセットを構成する

Surface デバイスに Windows を展開すると、Windows のプッシュボタンのリセット機能が既定で構成されます。システムは、環境がまだ構成されていない状態に戻されます。 Reset 関数を使うと、インストールされているアプリケーションと設定がシステムによって破棄されます。 場合によっては、本格的な環境でシステムをアプリケーションと設定が含まれていない状態に復元すると便利なことがあります。これにより、システムはエンドユーザーに対して使用できなくなります。

ただし、プッシュボタンのリセットを構成することもできますが、システム構成をエンドユーザーが使用できる状態に復元することができます。 「[展開プッシュボタンのリセット機能](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/deploy-push-button-reset-features)」で説明したプロセスに従って、デバイスのプッシュボタンのリセットエクスペリエンスをカスタマイズします。
