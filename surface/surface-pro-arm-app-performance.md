---
title: Surface Pro X アプリの互換性
description: この記事では、Surface Pro X ARM ベースの Pc のアプリの基本的な互換性情報について説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/03/2019
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: c236bf066d22cae80f4c0df39cc04450ad57a419
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835566"
---
# Surface Pro X アプリの互換性

ARM ベースの Windows 10 Pc (Surface Pro X など) では、アプリケーションの動作が異なります。次のような制限があります。

- **ハードウェア、ゲーム、アプリのドライバーは、Windows 10 ARM ベースの PC 向けに設計されている場合にのみ機能**します。 詳しい情報については、ハードウェアの製造元、またはドライバーを開発した組織に確認してください。 ドライバーは、ハードウェアデバイスと通信するソフトウェアプログラムであり、ウイルス対策ソフトウェアとマルウェア対策ソフトウェア、印刷または PDF ソフトウェア、支援技術、CD と DVD のユーティリティ、および仮想化ソフトウェアで一般的に使用されています。 ドライバーが機能しない場合は、そのドライバーに依存するアプリまたはハードウェアは動作しません (少なくとも完全ではありません)。 周辺機器とデバイスは、依存するドライバーが Windows 10 に組み込まれている場合、またはハードウェアの開発者がデバイス用の ARM64 ドライバーをリリースした場合にのみ機能します。
- **64 ビット (x64) のアプリは動作しません**。 64ビット (ARM64) アプリ、32ビット (ARM32) アプリ、または32ビット (x86) アプリが必要です。 通常は、32ビット (x86) バージョンのアプリが見つかりますが、一部のアプリ開発者は、64ビット (x64) アプリのみを提供します。
- **一部のゲームは動作しません**。 ゲームとアプリは、1.1 よりも大きいバージョンの OpenGL を使用している場合、または Windows 10 ARM ベースの Pc 向けに作成されていない "" クイック実行 "ドライバーに依存している場合には動作しません。 ゲームのパブリッシャーに問い合わせて、ゲームが機能するかどうかを確認します。
- **Windows エクスペリエンスをカスタマイズするアプリに問題が発生する可能性が**あります。 これには、入力方式エディター (Ime)、支援技術、クラウドストレージアプリなどがあります。 アプリを開発する組織は、アプリが Windows 10 ARM ベースの PC で動作するかどうかを決定します。
- **一部のサードパーティ製ウイルス対策ソフトウェアをインストールできません**。 Windows 10 ARM ベースの PC でサードパーティ製のウイルス対策ソフトウェアをインストールすることはできません。 ただし、windows セキュリティは、Windows 10 デバイスでサポートされている有効期間の安全性を維持するのに役立ちます。
- **Windows Fax とスキャンは使用できません**。 この機能は、Windows 10 ARM ベースの PC では使用できません。

アプリの互換性の詳細については、「 [Windows 10 ARM ベースの pc](https://support.microsoft.com/en-us/help/4521606)に関する FAQ」を参照してください。
