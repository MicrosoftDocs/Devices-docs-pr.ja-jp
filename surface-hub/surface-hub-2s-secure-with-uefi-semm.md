---
title: SEMM で Surface Hub の2S をセキュリティで保護し、管理する
description: 詳細については、「SEMM による Surface Hub のセキュリティ保護」を参照してください。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 03ce1dfa48ade8aade545c63818ca5ae8947e6b7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835270"
---
# <span data-ttu-id="d3d74-104">SEMM と UEFI による Surface Hub 2S のセキュリティ保護と管理</span><span class="sxs-lookup"><span data-stu-id="d3d74-104">Secure and manage Surface Hub 2S with SEMM and UEFI</span></span>

<span data-ttu-id="d3d74-105">Surface Hub 2S の新機種では、SEMM を使ってデバイスの UEFI 設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-105">New in Surface Hub 2S, you can use SEMM to manage the UEFI setting of the device.</span></span>
<span data-ttu-id="d3d74-106">Microsoft Surface UEFI コンフィギュレーターを使用して、次のコンポーネントを制御します。</span><span class="sxs-lookup"><span data-stu-id="d3d74-106">Use the Microsoft Surface UEFI Configurator to control the following components:</span></span>

- <span data-ttu-id="d3d74-107">ワイヤード (有線) LAN</span><span class="sxs-lookup"><span data-stu-id="d3d74-107">Wired LAN</span></span>
- <span data-ttu-id="d3d74-108">カメラ</span><span class="sxs-lookup"><span data-stu-id="d3d74-108">Cameras</span></span>
- <span data-ttu-id="d3d74-109">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d3d74-109">Bluetooth</span></span>
- <span data-ttu-id="d3d74-110">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="d3d74-110">Wi-Fi</span></span>
- <span data-ttu-id="d3d74-111">占有センサー</span><span class="sxs-lookup"><span data-stu-id="d3d74-111">Occupancy sensor</span></span>

<span data-ttu-id="d3d74-112">Microsoft Surface UEFI コンフィギュレーターを使用して、次の UEFI 設定のオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-112">Use the Microsoft Surface UEFI Configurator to turn on or off the following UEFI settings:</span></span>

- <span data-ttu-id="d3d74-113">Boot</span><span class="sxs-lookup"><span data-stu-id="d3d74-113">Boot</span></span>

    - <span data-ttu-id="d3d74-114">PXE ブート用 IPv6</span><span class="sxs-lookup"><span data-stu-id="d3d74-114">IPv6 for PXE Boot</span></span>
    - <span data-ttu-id="d3d74-115">代替ブート</span><span class="sxs-lookup"><span data-stu-id="d3d74-115">Alternate Boot</span></span>
    - <span data-ttu-id="d3d74-116">ブート順序ロック</span><span class="sxs-lookup"><span data-stu-id="d3d74-116">Boot Order Lock</span></span>
    - <span data-ttu-id="d3d74-117">USB ブート</span><span class="sxs-lookup"><span data-stu-id="d3d74-117">USB Boot</span></span>
- <span data-ttu-id="d3d74-118">UEFI の先頭ページ</span><span class="sxs-lookup"><span data-stu-id="d3d74-118">UEFI Front Page</span></span>

    - <span data-ttu-id="d3d74-119">デバイス</span><span class="sxs-lookup"><span data-stu-id="d3d74-119">Devices</span></span>
    - <span data-ttu-id="d3d74-120">Boot</span><span class="sxs-lookup"><span data-stu-id="d3d74-120">Boot</span></span>
    - <span data-ttu-id="d3d74-121">日付/時刻</span><span class="sxs-lookup"><span data-stu-id="d3d74-121">Date/Time</span></span>

## <span data-ttu-id="d3d74-122">UEFI 構成のイメージを作成する</span><span class="sxs-lookup"><span data-stu-id="d3d74-122">Create UEFI configuration image</span></span>

<span data-ttu-id="d3d74-123">他の Surface デバイスとは異なり、MSI ファイルまたは Win PE イメージを使って Surface Hub 2S でこれらの設定を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d3d74-123">Unlike other Surface devices, you cannot use an MSI file or a Win PE image to apply these settings on Surface Hub 2S.</span></span> <span data-ttu-id="d3d74-124">代わりに、デバイスに読み込む USB イメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3d74-124">Instead, you need to create a USB image to load into the device.</span></span> <span data-ttu-id="d3d74-125">Surface Hub 2S UEFI 構成イメージを作成するには、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページから、最新バージョンの MICROSOFT Surface uefi コンフィギュレーターをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="d3d74-125">To create a Surface Hub 2S UEFI configuration image, download and install the latest version of the Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span> <span data-ttu-id="d3d74-126">UEFI と SEMM の使い方について詳しくは、「 [Microsoft Surface Enterprise Management モード](https://docs.microsoft.com/surface/surface-enterprise-management-mode)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d3d74-126">For more information about using UEFI and SEMM, see [Microsoft Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>

## <span data-ttu-id="d3d74-127">Surface Hub 2S で UEFI を構成するには</span><span class="sxs-lookup"><span data-stu-id="d3d74-127">To configure UEFI on Surface Hub 2S</span></span>

1. <span data-ttu-id="d3d74-128">UEFI コンフィギュレーターを起動し、最初の画面で [**構成パッケージ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-128">Start the UEFI Configurator and on the first screen, choose **Configuration Package**.</span></span><br><br>
![\* UEFI コンフィギュレーターを開始し、「構成パッケージ」を選択します。](images/sh2-uefi1.png) <br> <br>
2. <span data-ttu-id="d3d74-130">パッケージに証明書を追加するには、パッケージを署名して保護するために、秘密キーに関する有効な証明書を .pfx ファイル形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3d74-130">To add the certificate to your package, you must have a valid certificate with the private key in a .pfx file format to sign and protect the package.</span></span> <span data-ttu-id="d3d74-131">[ **+ 証明書による保護**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3d74-131">Select **+ Certificate Protection.**</span></span> <br>
![\* 選択 + 証明書の保護 \*](images/sh2-uefi2.png) <br><br>
3. <span data-ttu-id="d3d74-133">証明書の秘密キーのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d3d74-133">Enter the certificate’s private key’s password.</span></span><br>
![\* 証明書の秘密キーのパスワードを入力 \*](images/sh2-uefi3.png) <br><br>
4. <span data-ttu-id="d3d74-135">秘密キーをインポートしたら、続けてパッケージの作成を行います。</span><span class="sxs-lookup"><span data-stu-id="d3d74-135">After importing the private key, continue creating the package.</span></span><br>
![\* パッケージの作成を続けます \*](images/sh2-uefi4.png) <br><br>
5. <span data-ttu-id="d3d74-137">UEFI 構成パッケージのターゲットとして、[ **hub**および**Surface hub 2s** ] を選びます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-137">Choose **Hub** and **Surface Hub 2S** as the target for the UEFI configuration package.</span></span><br>
![\* UEFI 構成パッケージのターゲットとしてハブおよび Surface Hub 2S を選ぶ \*](images/sh2-uefi5.png) <br><br>
6. <span data-ttu-id="d3d74-139">Surface Hub 2S でアクティブ化または非アクティブ化するコンポーネントと設定を選びます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-139">Choose the components and settings you want to activate or deactivate on Surface Hub 2S.</span></span><br>
![\* アクティブ化または非アクティブ化するコンポーネントと設定を選択してください \*](images/sh2-uefi6.png) <br><br>
7. <span data-ttu-id="d3d74-141">[USB] オプションを使用して、ファイルをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="d3d74-141">Use the USB option to export the file.</span></span><br>
![\* USB オプションを使用してファイルをエクスポート \*](images/sh2-uefi8.png) <br><br>
8. <span data-ttu-id="d3d74-143">このパッケージに使用する USB ドライブを挿入して選択します。</span><span class="sxs-lookup"><span data-stu-id="d3d74-143">Insert and choose the USB drive you’d like to use for this package.</span></span> <span data-ttu-id="d3d74-144">USB ドライブの書式が設定され、お持ちの情報が失われます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-144">The USB drive will be formatted and you lose any information you have on it.</span></span><br>
![\* パッケージ用の USB ドライブを挿入して選択します \*](images/sh2-uefi9.png) <br><br>
9. <span data-ttu-id="d3d74-146">パッケージの作成が正常に完了すると、証明書の拇印の最後の2文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3d74-146">Upon successful creation of the package, the Configurator will display the last two characters of your certificate’s thumbprint.</span></span> <span data-ttu-id="d3d74-147">Surface Hub 2S に構成をインポートするときは、これらの文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3d74-147">You need these characters when you import to the configuration to Surface Hub 2S.</span></span><br>
![\* パッケージの正常な構成 \*](images/sh2-uefi10.png) <br>

## <span data-ttu-id="d3d74-149">UEFI を起動するには</span><span class="sxs-lookup"><span data-stu-id="d3d74-149">To boot into UEFI</span></span>

<span data-ttu-id="d3d74-150">Surface Hub 2S をオフにします。</span><span class="sxs-lookup"><span data-stu-id="d3d74-150">Turn off Surface Hub 2S.</span></span> <span data-ttu-id="d3d74-151">**音量を上げる**ボタンを長押しして、**電源**ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="d3d74-151">Press and hold the **Volume Up** button and press the **Power** Button.</span></span> <span data-ttu-id="d3d74-152">[UEFI] メニューが表示されるまで、[音量を上げる] ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="d3d74-152">Keep holding the Volume Up button until the UEFI menu appears.</span></span>
