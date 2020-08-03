---
title: Power Surface でスリープ解除を有効にする方法
ms.author: v-todmc
author: mccoybot
ms.date: 7/30/2020
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121602
ms.reviewer: johnk@cadencepreferred.com
description: Surface デバイス用のスリープ解除機能を有効または無効にする方法について説明します。
keywords: update、deploy、driver、wol、wake on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 271831651280299a40c4e7a7480fa86e29bd1cf5
ms.sourcegitcommit: f875a45961ff5f3c04006afc8690b5e5965e4d80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2020
ms.locfileid: "10903020"
---
# <span data-ttu-id="9a33a-104">Surface デバイスの電源をオンにする</span><span class="sxs-lookup"><span data-stu-id="9a33a-104">Wake on Power for Surface devices</span></span>

<span data-ttu-id="9a33a-105">Surface デバイスは、机から離れているときにオフにすることも、休止モードに設定してバッテリーを節約することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-105">Surface devices can be powered off while away from the desk or set to hibernate mode to save battery.</span></span> <span data-ttu-id="9a33a-106">これらのデバイスの管理性を向上させるために、電源をスリープ状態にすると、電源に再接続すると、互換性のある Surface デバイスが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-106">To improve the manageability of these devices, Wake on Power enables compatible Surface devices to automatically start when reconnected to power.</span></span> <span data-ttu-id="9a33a-107">Power on Wake を構成するには、surface Enterprise Management Mode (SEMM) を使って Surface UEFI コンフィギュレーターまたは UEFI Manager を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a33a-107">Configuring Wake on Power requires using Surface Enterprise Management Mode (SEMM) either through Surface UEFI Configurator or the UEFI Manager.</span></span>

<span data-ttu-id="9a33a-108">電源をオンにすると、次のデバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-108">Wake on Power is a feature available on the following devices:</span></span>

- <span data-ttu-id="9a33a-109">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="9a33a-109">Surface Book 3</span></span>
- <span data-ttu-id="9a33a-110">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="9a33a-110">Surface Pro 7</span></span>
- <span data-ttu-id="9a33a-111">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="9a33a-111">Surface Laptop 3</span></span>
- <span data-ttu-id="9a33a-112">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="9a33a-112">Surface Pro X</span></span> 

## <span data-ttu-id="9a33a-113">概要と前提条件</span><span class="sxs-lookup"><span data-stu-id="9a33a-113">Overview and prerequisites</span></span>

<span data-ttu-id="9a33a-114">Surface UEFI コンフィギュレーターを使用して、ターゲットデバイスに配布するために Windows Installer パッケージに保存されている個々の UEFI 設定を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-114">You can use the Surface UEFI Configurator to configure individual UEFI settings that are saved in a Windows Installer .msi package for distribution to target devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="9a33a-115">この記事では、SEMM の使い方を理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9a33a-115">This article assumes that you are familiar with using SEMM.</span></span> <span data-ttu-id="9a33a-116">詳細については、「 [Surface Enterprise 管理モード (SEMM)](surface-enterprise-management-mode.md)ドキュメント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a33a-116">For more information, see [Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md) documentation.</span></span>

## <span data-ttu-id="9a33a-117">Power on Wake を有効にするには</span><span class="sxs-lookup"><span data-stu-id="9a33a-117">To enable Wake on Power</span></span>

1.  <span data-ttu-id="9a33a-118">[SURFACE UEFI コンフィギュレーター](https://www.microsoft.com/download/confirmation.aspx?id=46703)の最新バージョンをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9a33a-118">Download the latest version of [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span></span>
2.  <span data-ttu-id="9a33a-119">管理者として Surface デバイスにサインインし、 **SURFACE UEFI コンフィギュレーター**を開いて、[ **surface Devices**]、[**次へ**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-119">Sign into your Surface device as an Administrator, open **Surface UEFI Configurator**, select **Surface Devices**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="[Surface デバイス] を選択し、[次へ] を選択します。":::
3.  <span data-ttu-id="9a33a-121">[**スタート**] を選択し、[**構成パッケージ**] で [**作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-121">Select **Start** and then under **Configuration Package** select **Create**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="[構成パッケージの作成] を選びます。":::
4.  <span data-ttu-id="9a33a-123">[**証明書の保護**] を選択し、証明書の .pfx ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-123">Select **Certificate Protection** and add your certificate .pfx file.</span></span> <span data-ttu-id="9a33a-124">パスワードを入力した後、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-124">After entering your password, select **Next**.</span></span> <span data-ttu-id="9a33a-125">必要に応じて**パスワード保護**を追加し、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-125">Add **Password Protection**, as appropriate, and then select **Next**.</span></span>
5.  <span data-ttu-id="9a33a-126">[**ターゲットにするサーフェスの種類を選択**してください] ページで、必要に応じてターゲットデバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-126">On the **Choose which Surface type you want to target** page, select your target devices as appropriate.</span></span> <span data-ttu-id="9a33a-127">たとえば、 **Surface Pro 7**とします。</span><span class="sxs-lookup"><span data-stu-id="9a33a-127">For example, **Surface Pro 7**.</span></span>
6.  <span data-ttu-id="9a33a-128">[**高度な機能**] ページで、[**電源を**オンにする] を選択し、 **[オン**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-128">On the **Advanced Features** page, select **Wake on Power** and set to **On**.</span></span> <span data-ttu-id="9a33a-129">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-129">Select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="[電源をオンにする] を選択し、[オン] に設定します。"::: 
7.  <span data-ttu-id="9a33a-131">[**成功**] ページで [**終了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-131">On the **Successful** page, select **End**.</span></span> <span data-ttu-id="9a33a-132">デバイスに初めて設定を提供する場合は、証明書の拇印の最後の2文字を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-132">If this is your first time providing settings to your device, you will be prompted to provide the last two characters of the certificate thumbprint.</span></span> 
8.  <span data-ttu-id="9a33a-133">.Msi パッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-133">Save the .msi package.</span></span> 

## <span data-ttu-id="9a33a-134">MSI パッケージを適用する</span><span class="sxs-lookup"><span data-stu-id="9a33a-134">Apply the MSI package</span></span> 

<span data-ttu-id="9a33a-135">Microsoft Endpoint Configuration Manager などのソフトウェア配布ツールを使用して、ネットワーク上のデバイスに MSI パッケージを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="9a33a-135">You can apply the MSI package to devices across your network using software distribution tools such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="9a33a-136">この手順では、ローカルコンピューターにパッケージをインストールする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-136">This procedure includes steps for installing the package on your local machine.</span></span> 

1.  <span data-ttu-id="9a33a-137">管理者特権でコマンドプロンプトを開き、.msi ファイルの完全なパスを入力して .msi パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-137">Open an elevated command prompt and enter the full path of the .msi file to run the .msi package.</span></span> 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  <span data-ttu-id="9a33a-138">[**警告**] ダイアログボックスで、[ **OK]** を選択するか、必要に応じて Bitlocker を無効にします。</span><span class="sxs-lookup"><span data-stu-id="9a33a-138">On the **Warning** dialog box, select **OK** or disable Bitlocker as appropriate.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="[OK] を選択するか、必要に応じて Bitlocker を無効にします。":::
3.  <span data-ttu-id="9a33a-140">[ようこそ] ページで、[**次**へ] を選んでパッケージを実行し、新しく構成された UEFI 設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-140">On the Welcome page, select **Next** to run the package and apply the newly configured UEFI setting.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="[ようこそ] ページにある [次へ] を選びます。":::
4.  <span data-ttu-id="9a33a-142">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-142">Restart your device.</span></span> 

<span data-ttu-id="9a33a-143">電源がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="9a33a-143">Wake on Power is now configured.</span></span> <span data-ttu-id="9a33a-144">設定をテストするには、デバイスの電源を切り、電源を切り、電源を接続し直します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-144">To test the setting, turn off your device, disconnect the power, and then reconnect the power.</span></span> <span data-ttu-id="9a33a-145">デバイスが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-145">The device will start automatically.</span></span> 

## <span data-ttu-id="9a33a-146">詳細情報</span><span class="sxs-lookup"><span data-stu-id="9a33a-146">More information</span></span>

<span data-ttu-id="9a33a-147">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a33a-147">For more information, see the following articles.</span></span> 

- [<span data-ttu-id="9a33a-148">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="9a33a-148">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="9a33a-149">Surface デバイス用の Wake on LAN</span><span class="sxs-lookup"><span data-stu-id="9a33a-149">Wake on LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)

<span data-ttu-id="9a33a-150">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="9a33a-150">Still need help?</span></span> <span data-ttu-id="9a33a-151">[Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="9a33a-151">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>