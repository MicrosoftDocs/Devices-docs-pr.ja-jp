---
title: Windows 10 の長期サービスチャネル (Surface) との Surface デバイスの互換性
description: Windows 10 Enterprise LTSB edition を実行している Surface デバイスの互換性と制限事項を確認してください。
keywords: ltsb、update、surface サービスのオプション
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: scottmca
manager: laurawi
ms.openlocfilehash: db3dfd57c3b79fcec507ffd146483915490801b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834293"
---
# Windows 10 の長期サービスチャネル (LTSC) とのサーフェスデバイスの互換性

Surface デバイスは、生産性と一般的なシナリオにおいて、クラス内で最高のエクスペリエンスを実現するように設計されています。 定期的な更新プログラムを使うと、最新の革新技術を実現し、Windows 10 の機能更新プログラムによって提供される新機能を利用して進化させることができます。 機能更新プログラムは、半年チャネル (SAC) を通じて継続的な更新プログラムを受け取る Windows 10 Pro または Windows 10 Enterprise エディションでのみ利用できます。

以前は現在のブランチ (CB) または現在の支店 (CBB) のサービスオプションと呼ばれる SAC のサービスオプションとは対照的に、Windows 10 の設定で [LTSC] オプションを選択することはできません。 LTSC サービスオプションを使用するには、windows 10 enterprise の LTSC と呼ばれる、windows 10 enterprise LTSB (長期間のサービス分岐) と呼ばれる個別のエディションの Windows 10 Enterprise をインストールする必要があります。 拡張サービスモデルの提供に加えて、Windows 10 Enterprise LTSC edition では、いくつかの Windows コンポーネントが削除された環境も提供されています。 LTSC によって影響を受ける主要なサーフェスエクスペリエンスには、次のものがあります。

* Windows の機能更新プログラム、次のような拡張機能が含まれます。

  *  Windows 10 バージョン 1607 (記念日アップデートとも呼ばれます) で提供されるダイレクトインクと palm の却下の改善
  *  Windows 10 バージョン1703で提供される高 DPI アプリケーションのサポートが改善されました (クリエーター更新とも呼ばれます)。

* Surface アプリによって提供される筆圧感知設定

* Windows Ink ワークスペース

* Microsoft Edge、OneNote、予定表、カメラなど、タッチ操作に最適化された主要なアプリケーション

Surface デバイスで Windows 10 Enterprise LTSC environment を使用すると、非常に最適なエンドユーザーエクスペリエンスが得られ、ユーザーが必要としている premium のユーザーエクスペリエンスが期待されている環境では使用しないようにする必要があります。

LTSC サービスオプションは、デバイスの種類とシナリオ向けに設計されており、重要な属性が機能や機能のために変更されることはありません。 例としては、電源製造や医療機器、または Atm や空港のチケットシステムなどのキオスクシステムに組み込まれているシステムがあります。

>[!NOTE]
>LTSC を含む Windows サービスブランチの一般的な情報については、「[サービスとしての windows の概要](https://technet.microsoft.com/itpro/windows/update/waas-overview#long-term-servicing-branch)」を参照してください。

一般的なガイドラインとして、次の条件を満たすデバイスは、一般的な目的のデバイスと見なされ、半半期チャネルサービスオプションを使用して、Windows 10 Pro または Windows 10 Enterprise とペアリングする必要があります。

* 生産性向上ソフトウェア (Microsoft Office など) を実行しているデバイス

* Microsoft Store アプリケーションを使用するデバイス

* 一般的なインターネット閲覧に使用されるデバイス (たとえば、リサーチまたはソーシャルメディアへのアクセスなど)

Surface デバイスで Windows 10 Enterprise LTSC edition を使用する前に、次の制限事項を考慮してください。

* ドライバーとファームウェアの更新プログラムは、Windows 10 Enterprise LTSC のリリースに対して明示的にテストされることはありません。

* 問題が発生した場合は、Microsoft サポートがトラブルシューティングのサポートを提供します。 ただし、Windows LTSC のサービスの性質上、問題を解決するには、デバイスをより新しいバージョンの Windows 10 Enterprise LTSC にアップグレードするか、SAC のサービスオプションを使用して Windows 10 Pro または Enterprise にアップグレードする必要があります。

* Surface デバイスの代替 (たとえば、[保証] の下にあるデバイス) には、デバイスドライバーとファームウェアの更新が必要なハードウェアコンポーネントの微妙なバリエーションが含まれている場合があります。 これらの更新プログラムとの互換性には、SAC のサービスオプションを使用して、より新しいバージョンの Windows 10 Enterprise LTSC または Windows 10 Pro または Enterprise をインストールする必要があります。

>[!NOTE]
>特定のバージョンの Windows 10 Enterprise LTSC で標準化されている組織では、Windows 10 Enterprise LTSC または Windows 10 Pro または Enterprise の新しいバージョンにアップグレードすることなく、surface Pro 7、Surface Pro X、Surface Pc 3 などの新しい世代の Surface ハードウェアを導入することはできません。 詳細については、「windows **10 LTSBs のサポート**について」を参照してください。「ライフサイクルポリシーの**windows での最新のプロセッサとチップセット**のサポート[(windows 製品)](https://support.microsoft.com/help/18581/lifecycle-policy-faq-windows-products#b4)」のトピックを参照してください。

Windows 10 Enterprise LTSC edition を実行している Surface デバイスでは、新しい機能は取得されません。 多くの場合、これらの機能は、Surface ハードウェアの操作性と機能を向上させるためにユーザーによって要求されます。 たとえば、Windows 10 バージョン1703での高 DPI アプリケーションの新機能強化。 LTSC 構成で Surface デバイスを使っているユーザーは、新しい Windows 10 Enterprise LTSC リリースに更新するか、SAC のサービスオプションをサポートしているバージョンの Windows 10 にアップグレードするまで、この機能の改善を確認できません。

デバイスは、アップグレードインストールを実行してユーザーデータを損失することなく、SAC のサービスオプションをサポートすることで、Windows 10 Enterprise LTSC から最新バージョンの Windows 10 Enterprise に変更できます。 Microsoft 展開ツールキット (MDT) と Microsoft Endpoint Configuration Manager で利用可能なアップグレードタスクシーケンステンプレートを活用して、複数のデバイスでアップグレードインストールを実行することもできます。 詳細については、「 [Microsoft 展開ツールキットを使用して Surface デバイスを Windows 10 にアップグレードする](https://technet.microsoft.com/itpro/surface/upgrade-surface-devices-to-windows-10-with-mdt)」を参照してください。
