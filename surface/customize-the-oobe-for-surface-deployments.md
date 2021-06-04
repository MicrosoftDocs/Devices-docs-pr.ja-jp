---
title: Surface の展開用の OOBE をカスタマイズする (Surface)
description: この記事では、Surface の Out-Of-Box Experience を組織内のエンド ユーザー向けにカスタマイズするプロセスを説明します。
ms.assetid: F6910315-9FA9-4297-8FA8-2C284A4B1D87
ms.reviewer: ''
manager: laurawi
keywords: 展開, カスタマイズ, 自動化, ネットワーク, ペン, ペアリング, ブート, deploy, customize, automate, network, Pen, pair, boot
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 97cc262d803875a76427d04c8f9b70547152f895
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835669"
---
# Surface の展開用の OOBE をカスタマイズする

この記事では、組織内のエンドユーザーに対して、Surface の既定の環境をカスタマイズする方法について説明します。

Windows の展開では、展開するコンピューターの初回起動時のユーザー エクスペリエンス、つまり Out-Of-Box Experience (OOBE) をカスタマイズすることが一般的です。

>[!NOTE]
>OOBE は、ユーザー エクスペリエンスが表示される Windows セットアップのフェーズ、つまり構成パスを記述するためにもよく使われます。 セットアップの OOBE フェーズについて詳しくは、「[構成パスのしくみ](https://msdn.microsoft.com/library/windows/hardware/dn898581.aspx)」をご覧ください。

シナリオによっては、完全に自動化して、ユーザーの介在なしに展開の最後にコンピューターが使用可能になっているようにすることもできます。 別のシナリオでは、ユーザーが必要な操作を実行したり、重要な選択肢から選択したりできるように、エクスペリエンスの主要な要素をそのままにすることもできます。 Surface デバイスに展開する管理者にとっては、シナリオそれぞれに対処すべき固有の課題があります。

> [!NOTE]
> この記事は Surface Pro X には適用されません。詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md) 」を参照してください。

この記事では、展開に追加の手順が必要なシナリオについて概要を示します。 新たに展開された Surface デバイスで目的のエクスペリエンスを実現するために必要な情報についても説明します。 この記事は、展開プロセスの詳細や応答ファイル、[参照イメージ](https://technet.microsoft.com/itpro/windows/deploy/create-a-windows-10-reference-image)などの概念についてよく知っている管理者向けに書かれています。

>[!NOTE]
>[Microsoft 展開ツールキット (MDT)](https://go.microsoft.com/fwlink/p/?LinkId=618117)や Microsoft Endpoint Configuration Manager オペレーティングシステム展開 (OSD) などの自動展開ソリューションを使用して、セットアップの OOBE フェーズはまだ実行されていますが、展開ウィザードとタスクシーケンスで提供される設定によって自動化されています。 詳しくは、次のトピックをご覧ください。<br/>
>- [Microsoft Deployment Toolkit による Windows 10 の展開](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)
>- [System Center 2012 R2 Configuration Manager による Windows 10 の展開](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-system-center-2012-r2-configuration-manager)

 

##  <a name="scenario-1:-wireless-networking-in-oobe-with-mdt-2013"></a>シナリオ 1: MDT 2013 を使う OOBE でのワイヤレス ネットワーク


OOBE 中にワイヤレス ネットワーク アダプターが存在する場合、**[ワイヤレス ネットワークへの接続]** ページが表示され、ユーザーにワイヤレス ネットワークに接続するよう求めるメッセージが表示されます。 このページは MDT 2013 などの展開テクノロジによって自動的に非表示にならないため、展開が完全な自動化で構成されている場合でも表示されます。

自動化された展開がこのページで停止しないようにするには、応答ファイル **HideWirelessSetupInOOBE** で追加の設定を構成してページを非表示にする必要があります。 **HideWirelessSetupInOOBE** の設定について詳しくは、[Windows の無人セットアップのリファレンスに関するページ](https://technet.microsoft.com/library/ff716213.aspx)をご覧ください。

##  <a name="scenario-2:-surface-pen-pairing-in-oobe"></a>シナリオ 2: OOBE での Surface ペンのペアリング


Surface Pro 3、Surface Pro 4、Surface Book、または Surface Studio をパッケージから取り出して最初に起動するとき、最初の実行エクスペリエンスには、付属する Surface ペンをデバイスとペアリングするように求めるプロンプトが含まれています。 このプロンプトは、デバイスに付属する出荷時のイメージでのみ提供され、ボリューム ライセンス サービス センターからダウンロードする Windows Enterprise インストール メディアなど、展開に使用されるその他のイメージには含まれていません。 このエクスペリエンス以外で Bluetooth Surface ペンのペアリングを行うには、コントロール パネルまたは [PC 設定] に移動して手動で Bluetooth デバイスをペアリングする必要があるため、ユーザーや技術者がこのプロンプトを使用してペアリング操作を行うようにする必要があります。

OOBE で Surface ペンの出荷時のペアリング エクスペリエンスを提供するには、Surface の出荷時のイメージから参照イメージに 4 つのファイルをコピーする必要があります。 参照イメージをキャプチャする前に参照環境にこれらのファイルをコピーすることも、展開イメージのサービスと管理 (DISM) を使用してイメージをマウントすることで、後で追加することもできます。 次の 4 つのファイルが必要です。

-   %windir%\\system32\\oobe\\info\\default\\1033\\oobe.xml
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenPairing\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenError\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenSuccess\_en-US.png

>[!NOTE]
>展開する予定の Surface デバイスと同じモデルの出荷時イメージからファイルをコピーしてください。 たとえば、surface Pro 7 のファイルを使用して surface Pro 7 に展開し、surface book 2 のファイルを使用して surface book 2 を展開する必要がありますが、surface Pro 7 のファイルを使用して Surface Book または Surface Pro 6 を展開しないでください。

 

必要なファイルをイメージに追加するための手順は、[Surface Pro 3 ペンおよび OneNote の展開のヒント](https://blogs.technet.microsoft.com/askcore/2014/07/15/deploying-surface-pro-3-pen-and-onenote-tips/)に関するページに記載されています。 このブログの投稿には、Surface ペンの Quick Note-Taking Experience に必要な更新プログラムがインストールされていることを確認するためのヒントも含まれています。これを利用すると、ユーザーはシングルクリックで OneNote にメモを送信することができます。

 

 





