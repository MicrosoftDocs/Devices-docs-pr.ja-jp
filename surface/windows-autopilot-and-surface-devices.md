---
title: Windows Autopilot と Surface デバイス
ms.reviewer: ''
manager: laurawi
description: Surface デバイスの Windows 自動操縦展開オプションについては、こちらを参照してください。
keywords: 自動操縦、windows 10、サーフェス、展開
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: ea5920649a4a29841b102de73c88187440968910
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834621"
---
# <span data-ttu-id="e465d-104">Windows Autopilot と Surface デバイス</span><span class="sxs-lookup"><span data-stu-id="e465d-104">Windows Autopilot and Surface devices</span></span>

<span data-ttu-id="e465d-105">Windows 自動操縦は、Windows 10 のクラウドベースの展開テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="e465d-105">Windows Autopilot is a cloud-based deployment technology in Windows 10.</span></span> <span data-ttu-id="e465d-106">Windows 自動操縦を使用して、ゼロタッチプロセスでデバイスをリモートで展開して構成することができます。</span><span class="sxs-lookup"><span data-stu-id="e465d-106">You can use Windows Autopilot to remotely deploy and configure devices in a zero-touch process right out of the box.</span></span>

<span data-ttu-id="e465d-107">Windows 自動操縦装置-登録済みデバイスは、最初の起動時に、*ハードウェアハッシュ*と呼ばれる一意のデバイス署名を介してインターネット経由で識別されます。</span><span class="sxs-lookup"><span data-stu-id="e465d-107">Windows Autopilot-registered devices are identified over the Internet at first startup through a unique device signature that's called a *hardware hash*.</span></span> <span data-ttu-id="e465d-108">これらのユーザーは、Azure Active Directory (Azure AD) やモバイルデバイス管理などの先進の管理ソリューションを使用して、自動的に登録および構成されています。</span><span class="sxs-lookup"><span data-stu-id="e465d-108">They're automatically enrolled and configured by using modern management solutions such as Azure Active Directory (Azure AD) and mobile device management.</span></span>

<span data-ttu-id="e465d-109">Surface devices は、Windows 自動操縦が有効になっている Surface パートナーから購入した時点で登録できます。</span><span class="sxs-lookup"><span data-stu-id="e465d-109">You can register Surface devices at the time of purchase from a Surface partner that's enabled for Windows Autopilot.</span></span> <span data-ttu-id="e465d-110">これらのパートナーは、新しいデバイスを直接ユーザーに送ることができます。</span><span class="sxs-lookup"><span data-stu-id="e465d-110">These partners can ship new devices directly to your users.</span></span> <span data-ttu-id="e465d-111">デバイスは、最初にオンになったときに自動的に登録され、構成されます。</span><span class="sxs-lookup"><span data-stu-id="e465d-111">The devices will be automatically enrolled and configured when they are first turned on.</span></span> <span data-ttu-id="e465d-112">このプロセスでは、展開中のイメージの再作成が不要になります。これにより、デバイスの管理と配布に関する新しい機敏な方法を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="e465d-112">This process eliminates reimaging during deployment, which lets you implement new, agile methods of device management and distribution.</span></span>

## <span data-ttu-id="e465d-113">最新の管理機能</span><span class="sxs-lookup"><span data-stu-id="e465d-113">Modern management</span></span>

<span data-ttu-id="e465d-114">自動操縦は、surface Pro 7、Surface ノート Pc 3、Surface Pro X など、Surface デバイスに推奨される展開オプションであり、自動操縦を通じて展開するために特別に設計されています。</span><span class="sxs-lookup"><span data-stu-id="e465d-114">Autopilot is the recommended deployment option for Surface devices, including Surface Pro 7, Surface Laptop 3, and Surface Pro X, which is specifically designed for deployment through Autopilot.</span></span>

 <span data-ttu-id="e465d-115">Surface デバイスの登録は、Microsoft クラウドソリューションプロバイダーの支援として行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e465d-115">It's best to enroll your Surface devices with the help of a Microsoft Cloud Solution Provider.</span></span> <span data-ttu-id="e465d-116">この手順により、Intune から直接、Surface 上の UEFI ファームウェア設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="e465d-116">This step allows you to manage UEFI firmware settings on Surface directly from Intune.</span></span> <span data-ttu-id="e465d-117">これにより、デバイスを直接操作して証明書を管理する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e465d-117">It eliminates the need to physically touch devices for certificate management.</span></span> <span data-ttu-id="e465d-118">詳細については、「 [Surface の UEFI 管理のための Intune の設定](surface-manage-dfci-guide.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e465d-118">See [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md) for details.</span></span>

## <span data-ttu-id="e465d-119">Windows のバージョンに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e465d-119">Windows version considerations</span></span>

<span data-ttu-id="e465d-120">Windows 自動操縦を介した Surface デバイスの広範な展開 (購入時に Surface パートナーによる登録を含む) には、Windows 10 バージョン 1709 (秋の更新プログラム) 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="e465d-120">Broad deployment of Surface devices through Windows Autopilot, including enrollment by Surface partners at the time of purchase, requires Windows 10 Version 1709 (Fall Creators Update) or later.</span></span>

<span data-ttu-id="e465d-121">これらの Windows のバージョンでは、Windows 自動操縦用のデバイスを一意に識別する4000バイト (4k) ハッシュ値がサポートされています。これは、展開時の展開に必要です。</span><span class="sxs-lookup"><span data-stu-id="e465d-121">These Windows versions support a 4,000-byte (4k) hash value that uniquely identifies devices for Windows Autopilot, which is necessary for deployments at scale.</span></span> <span data-ttu-id="e465d-122">Surface Pro 7、Surface Pro X、Surface のノート Pc 3 などのすべての新しい Surface デバイスは、Windows 10 バージョン1903以降で出荷されています。</span><span class="sxs-lookup"><span data-stu-id="e465d-122">All new Surface devices, including Surface Pro 7, Surface Pro X, and Surface Laptop 3, ship with Windows 10 Version 1903 or later.</span></span>

## <span data-ttu-id="e465d-123">修復または交換の必要性に応じた Surface デバイスでの Exchange の操作性</span><span class="sxs-lookup"><span data-stu-id="e465d-123">Exchange experience on Surface devices in need of repair or replacement</span></span>

<span data-ttu-id="e465d-124">Microsoft は、自動操縦のための各サーフェスを自動的にチェックし、お客様のテナントからデバイスを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="e465d-124">Microsoft automatically checks every Surface for Autopilot enrollment and will deregister the device from the customer's tenant.</span></span>  <span data-ttu-id="e465d-125">Microsoft は、交換されたデバイスが、お客様にリリースされると、Windows 自動操縦に登録されることを保証します。</span><span class="sxs-lookup"><span data-stu-id="e465d-125">Microsoft ensures the replacement device is enrolled into Windows Autopilot once a replacement is shipped back to the customer.</span></span> <span data-ttu-id="e465d-126">このサービスは、Microsoft とのすべてのデバイス交換サービス注文で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e465d-126">This service is available on all device exchange service orders directly with Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="e465d-127">顧客がパートナーを使ってデバイスを返品する場合、パートナーは Windows 自動操縦の登録解除とデバイスの登録など、exchange プロセスの管理を担当します。</span><span class="sxs-lookup"><span data-stu-id="e465d-127">When customers use a Partner to return devices, the Partner is responsible for managing the exchange process including deregistering and enrolling devices into Windows Autopilot.</span></span>

## <span data-ttu-id="e465d-128">Windows 自動操縦に対応した Surface パートナー</span><span class="sxs-lookup"><span data-stu-id="e465d-128">Surface partners enabled for Windows Autopilot</span></span>

<span data-ttu-id="e465d-129">[Surface パートナーの選択] では、購入時に Windows 自動操縦に Surface デバイスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="e465d-129">Select Surface partners can enroll Surface devices in Windows Autopilot for you at the time of purchase.</span></span> <span data-ttu-id="e465d-130">また、登録されたデバイスを直接ユーザーに送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="e465d-130">They can also ship enrolled devices directly to your users.</span></span> <span data-ttu-id="e465d-131">デバイスは、Windows 自動操縦機能、Azure AD、モバイルデバイス管理を使用して、ゼロタッチプロセスで完全に構成できます。</span><span class="sxs-lookup"><span data-stu-id="e465d-131">The devices can be configured entirely through a zero-touch process by using Windows Autopilot, Azure AD, and mobile device management.</span></span>

<span data-ttu-id="e465d-132">Windows 自動操縦に対応した Surface パートナーには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="e465d-132">Surface partners that are enabled for Windows Autopilot include:</span></span>

| <span data-ttu-id="e465d-133">US パートナー</span><span class="sxs-lookup"><span data-stu-id="e465d-133">US partners</span></span> | <span data-ttu-id="e465d-134">グローバルパートナー</span><span class="sxs-lookup"><span data-stu-id="e465d-134">Global partners</span></span> | <span data-ttu-id="e465d-135">US 販売業者</span><span class="sxs-lookup"><span data-stu-id="e465d-135">US distributors</span></span> |
|--------------|---------------|-------------------|
| <span data-ttu-id="e465d-136">\* [CDW](https://www.cdw.com/)</span><span class="sxs-lookup"><span data-stu-id="e465d-136">\* [CDW](https://www.cdw.com/)</span></span> | <span data-ttu-id="e465d-137">\* [また](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp)</span><span class="sxs-lookup"><span data-stu-id="e465d-137">\* [ALSO](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp)</span></span> | <span data-ttu-id="e465d-138">\* [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)</span><span class="sxs-lookup"><span data-stu-id="e465d-138">\* [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)</span></span>  |
| <span data-ttu-id="e465d-139">\* [関連](https://www.connection.com/brand/microsoft/microsoft-surface)</span><span class="sxs-lookup"><span data-stu-id="e465d-139">\* [Connection](https://www.connection.com/brand/microsoft/microsoft-surface)</span></span>   | <span data-ttu-id="e465d-140">\* [ATEA](https://www.atea.com/)</span><span class="sxs-lookup"><span data-stu-id="e465d-140">\* [ATEA](https://www.atea.com/)</span></span> | <span data-ttu-id="e465d-141">\* [テクニカルデータ](https://www.techdata.com/)</span><span class="sxs-lookup"><span data-stu-id="e465d-141">\* [Techdata](https://www.techdata.com/)</span></span>  |
| <span data-ttu-id="e465d-142">\* [知る](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)</span><span class="sxs-lookup"><span data-stu-id="e465d-142">\* [Insight](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)</span></span>  | <span data-ttu-id="e465d-143">\* [/Htle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot)</span><span class="sxs-lookup"><span data-stu-id="e465d-143">\* [Bechtle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot)</span></span> | <span data-ttu-id="e465d-144">\* [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)</span><span class="sxs-lookup"><span data-stu-id="e465d-144">\* [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)</span></span>   |
| <span data-ttu-id="e465d-145">\* [SHI](https://www.shi.com/Surface)</span><span class="sxs-lookup"><span data-stu-id="e465d-145">\* [SHI](https://www.shi.com/Surface)</span></span> | <span data-ttu-id="e465d-146">\* [Cancom](https://www.cancom.de/)</span><span class="sxs-lookup"><span data-stu-id="e465d-146">\* [Cancom](https://www.cancom.de/)</span></span> |    |
| <span data-ttu-id="e465d-147">\* [LDI Connect](https://www.myldi.com/managed-it/)</span><span class="sxs-lookup"><span data-stu-id="e465d-147">\* [LDI Connect](https://www.myldi.com/managed-it/)</span></span>  | <span data-ttu-id="e465d-148">\* [Computacenter](https://www.computacenter.com/uk)</span><span class="sxs-lookup"><span data-stu-id="e465d-148">\* [Computacenter](https://www.computacenter.com/uk)</span></span> |    |
| <span data-ttu-id="e465d-149">\* [F1](https://www.functiononeit.com/#empower)</span><span class="sxs-lookup"><span data-stu-id="e465d-149">\* [F1](https://www.functiononeit.com/#empower)</span></span>  |   |  |
| <span data-ttu-id="e465d-150">\* [保護された信頼](https://go.microsoft.com/fwlink/p/?LinkID=2129005)</span><span class="sxs-lookup"><span data-stu-id="e465d-150">\* [Protected Trust](https://go.microsoft.com/fwlink/p/?LinkID=2129005)</span></span> | | | 

## <span data-ttu-id="e465d-151">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e465d-151">Learn more</span></span>

<span data-ttu-id="e465d-152">Windows 自動操縦の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e465d-152">For more information about Windows Autopilot, see:</span></span>
- [<span data-ttu-id="e465d-153">Windows Autopilot の概要</span><span class="sxs-lookup"><span data-stu-id="e465d-153">Overview of Windows Autopilot</span></span>](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)
- [<span data-ttu-id="e465d-154">Windows Autopilot の要件</span><span class="sxs-lookup"><span data-stu-id="e465d-154">Windows Autopilot requirements</span></span>](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements)