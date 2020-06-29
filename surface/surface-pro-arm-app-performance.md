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
# <span data-ttu-id="dbcc3-103">Surface Pro X アプリの互換性</span><span class="sxs-lookup"><span data-stu-id="dbcc3-103">Surface Pro X app compatibility</span></span>

<span data-ttu-id="dbcc3-104">ARM ベースの Windows 10 Pc (Surface Pro X など) では、アプリケーションの動作が異なります。次のような制限があります。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-104">Applications run differently on ARM-based Windows 10 PCs such as Surface Pro X. Limitations include the following:</span></span>

- <span data-ttu-id="dbcc3-105">**ハードウェア、ゲーム、アプリのドライバーは、Windows 10 ARM ベースの PC 向けに設計されている場合にのみ機能**します。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-105">**Drivers for hardware, games and apps will only work if they're designed for a Windows 10 ARM-based PC**.</span></span> <span data-ttu-id="dbcc3-106">詳しい情報については、ハードウェアの製造元、またはドライバーを開発した組織に確認してください。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-106">For more info, check with the hardware manufacturer or the organization that developed the driver.</span></span> <span data-ttu-id="dbcc3-107">ドライバーは、ハードウェアデバイスと通信するソフトウェアプログラムであり、ウイルス対策ソフトウェアとマルウェア対策ソフトウェア、印刷または PDF ソフトウェア、支援技術、CD と DVD のユーティリティ、および仮想化ソフトウェアで一般的に使用されています。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-107">Drivers are software programs that communicate with hardware devices—they're commonly used for antivirus and antimalware software, printing or PDF software, assistive technologies, CD and DVD utilities, and virtualization software.</span></span> <span data-ttu-id="dbcc3-108">ドライバーが機能しない場合は、そのドライバーに依存するアプリまたはハードウェアは動作しません (少なくとも完全ではありません)。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-108">If a driver doesn’t work, the app or hardware that relies on it won’t work either (at least not fully).</span></span> <span data-ttu-id="dbcc3-109">周辺機器とデバイスは、依存するドライバーが Windows 10 に組み込まれている場合、またはハードウェアの開発者がデバイス用の ARM64 ドライバーをリリースした場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-109">Peripherals and devices only work if the drivers they depend on are built into Windows 10, or if the hardware developer has released ARM64 drivers for the device.</span></span>
- <span data-ttu-id="dbcc3-110">**64 ビット (x64) のアプリは動作しません**。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-110">**64-bit (x64) apps won’t work**.</span></span> <span data-ttu-id="dbcc3-111">64ビット (ARM64) アプリ、32ビット (ARM32) アプリ、または32ビット (x86) アプリが必要です。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-111">You'll need 64-bit (ARM64) apps, 32-bit (ARM32) apps, or 32-bit (x86) apps.</span></span> <span data-ttu-id="dbcc3-112">通常は、32ビット (x86) バージョンのアプリが見つかりますが、一部のアプリ開発者は、64ビット (x64) アプリのみを提供します。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-112">You can usually find 32-bit (x86) versions of apps, but some app developers only offer 64-bit (x64) apps.</span></span>
- <span data-ttu-id="dbcc3-113">**一部のゲームは動作しません**。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-113">**Certain games won’t work**.</span></span> <span data-ttu-id="dbcc3-114">ゲームとアプリは、1.1 よりも大きいバージョンの OpenGL を使用している場合、または Windows 10 ARM ベースの Pc 向けに作成されていない "" クイック実行 "ドライバーに依存している場合には動作しません。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-114">Games and apps won't work if they use a version of OpenGL greater than 1.1, or if they rely on "anti-cheat" drivers that haven't been made for Windows 10 ARM-based PCs.</span></span> <span data-ttu-id="dbcc3-115">ゲームのパブリッシャーに問い合わせて、ゲームが機能するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-115">Check with your game publisher to see if a game will work.</span></span>
- <span data-ttu-id="dbcc3-116">**Windows エクスペリエンスをカスタマイズするアプリに問題が発生する可能性が**あります。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-116">**Apps that customize the Windows experience might have problems**.</span></span> <span data-ttu-id="dbcc3-117">これには、入力方式エディター (Ime)、支援技術、クラウドストレージアプリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-117">This includes some input method editors (IMEs), assistive technologies, and cloud storage apps.</span></span> <span data-ttu-id="dbcc3-118">アプリを開発する組織は、アプリが Windows 10 ARM ベースの PC で動作するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-118">The organization that develops the app determines whether their app will work on a Windows 10 ARM-based PC.</span></span>
- <span data-ttu-id="dbcc3-119">**一部のサードパーティ製ウイルス対策ソフトウェアをインストールできません**。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-119">**Some third-party antivirus software can’t be installed**.</span></span> <span data-ttu-id="dbcc3-120">Windows 10 ARM ベースの PC でサードパーティ製のウイルス対策ソフトウェアをインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-120">You won't be able to install some third-party antivirus software on a Windows 10 ARM-based PC.</span></span> <span data-ttu-id="dbcc3-121">ただし、windows セキュリティは、Windows 10 デバイスでサポートされている有効期間の安全性を維持するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-121">However, Windows Security will help keep you safe for the supported lifetime of your Windows 10 device.</span></span>
- <span data-ttu-id="dbcc3-122">**Windows Fax とスキャンは使用できません**。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-122">**Windows Fax and Scan isn’t available**.</span></span> <span data-ttu-id="dbcc3-123">この機能は、Windows 10 ARM ベースの PC では使用できません。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-123">This feature isn’t available on a Windows 10 ARM-based PC.</span></span>

<span data-ttu-id="dbcc3-124">アプリの互換性の詳細については、「 [Windows 10 ARM ベースの pc](https://support.microsoft.com/en-us/help/4521606)に関する FAQ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbcc3-124">For more information about app compatibility, refer to [Windows 10 ARM-based PCs FAQ](https://support.microsoft.com/en-us/help/4521606)</span></span>
