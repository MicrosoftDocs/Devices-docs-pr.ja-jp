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
ms.openlocfilehash: 272c19baedb295abac08e90012246e453b88f42f
ms.sourcegitcommit: 6fd7008992503db9ae1f56654aa80110348924d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "10903396"
---
# <span data-ttu-id="10fce-104">Surface デバイス での Wake On Power の使用</span><span class="sxs-lookup"><span data-stu-id="10fce-104">Wake on Power for Surface devices</span></span>

<span data-ttu-id="10fce-105">Surface デバイスは、机の外にいるときにオフにすることができます。または、休止モードに設定してバッテリーを節約できます。</span><span class="sxs-lookup"><span data-stu-id="10fce-105">Surface devices can be powered off while you're away from your desk, or set to hibernate mode to save battery life.</span></span> <span data-ttu-id="10fce-106">これらのデバイスの管理性を向上させるために、電源をオンにすると、互換性のある Surface デバイスは、電源に再接続したときに自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="10fce-106">To improve the manageability of these devices, Wake on Power enables compatible Surface devices to automatically start when they're reconnected to power.</span></span> <span data-ttu-id="10fce-107">Wake on Power を構成するには、surface Enterprise 管理モード (SEMM) で Surface UEFI コンフィギュレーターまたは UEFI Manager のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="10fce-107">To configure Wake on Power, you can use Surface Enterprise Management Mode (SEMM) either through Surface UEFI Configurator or the UEFI Manager.</span></span>

<span data-ttu-id="10fce-108">電源投入時の機能は、以下のデバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="10fce-108">The Wake on Power feature is available on the following devices:</span></span>

- <span data-ttu-id="10fce-109">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="10fce-109">Surface Book 3</span></span>
- <span data-ttu-id="10fce-110">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="10fce-110">Surface Pro 7</span></span>
- <span data-ttu-id="10fce-111">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="10fce-111">Surface Laptop 3</span></span>
- <span data-ttu-id="10fce-112">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="10fce-112">Surface Pro X</span></span> 

## <span data-ttu-id="10fce-113">概要と前提条件</span><span class="sxs-lookup"><span data-stu-id="10fce-113">Overview and prerequisites</span></span>

<span data-ttu-id="10fce-114">Surface UEFI コンフィギュレーターでは、ターゲットデバイスに配布するために、個々の UEFI 設定を Windows Installer の .msi パッケージに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="10fce-114">Surface UEFI Configurator lets you save individual UEFI settings in a Windows Installer .msi package for distribution to target devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="10fce-115">この記事では、SEMM の使い方を理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="10fce-115">This article assumes that you know how to use SEMM.</span></span> <span data-ttu-id="10fce-116">詳細については、「 [Surface Enterprise 管理モード (SEMM)](surface-enterprise-management-mode.md)ドキュメント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10fce-116">For more information, see [Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md) documentation.</span></span>

## <span data-ttu-id="10fce-117">Power on Wake を有効にするには</span><span class="sxs-lookup"><span data-stu-id="10fce-117">To enable Wake on Power</span></span>

1.  <span data-ttu-id="10fce-118">[SURFACE UEFI コンフィギュレーター](https://www.microsoft.com/download/confirmation.aspx?id=46703)の最新バージョンをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="10fce-118">Download the latest version of [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span></span>
2.  <span data-ttu-id="10fce-119">管理者として Surface デバイスにサインインして、 **SURFACE UEFI コンフィギュレーター**を開き、[ **surface Devices**]、[**次へ**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="10fce-119">Sign in to your Surface device as an administrator, open **Surface UEFI Configurator**, select **Surface Devices**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="[Surface デバイス] を選択し、[次へ] を選択します。":::
3.  <span data-ttu-id="10fce-121">[**スタート**] を選択し、[**構成パッケージ**] の [**作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10fce-121">Select **Start**, and then select **Create** under **Configuration Package**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="[構成パッケージの作成] を選びます。":::
4.  <span data-ttu-id="10fce-123">[**証明書の保護**] を選択し、証明書の .pfx ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="10fce-123">Select **Certificate Protection**, and add your certificate .pfx file.</span></span> 
5. <span data-ttu-id="10fce-124">パスワードを入力し、[**次へ**] を選択し、必要に応じて**パスワード保護**を追加して、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10fce-124">Enter your password, select **Next**, add **Password Protection**, as appropriate, and then select **Next**.</span></span>
6.  <span data-ttu-id="10fce-125">[**ターゲットにするサーフェスの種類を選択**してください] ページで、必要に応じてターゲットデバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="10fce-125">On the **Choose which Surface type you want to target** page, select your target devices as appropriate.</span></span> <span data-ttu-id="10fce-126">たとえば、[ **Surface Pro 7**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="10fce-126">For example, select **Surface Pro 7**.</span></span>
7.  <span data-ttu-id="10fce-127">[**高度な機能**] ページで、[**電源によるスリープ解除**] を選択し、機能を **[オン**] に設定して、[**次へ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="10fce-127">On the **Advanced Features** page, select **Wake on Power**, set the feature to **On**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="[電源をオンにする] を選択し、[オン] に設定します。"::: 
8.  <span data-ttu-id="10fce-129">[**成功**] ページで [**終了**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="10fce-129">On the **Successful** page, select **End**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="10fce-130">初めてデバイスに設定を提供する場合は、証明書の拇印の最後の2文字も入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="10fce-130">If this is the first time that you are providing settings to your device, you will be prompted to also provide the last two characters of the certificate thumbprint.</span></span> 
9.  <span data-ttu-id="10fce-131">.Msi パッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="10fce-131">Save the .msi package.</span></span> 

## <span data-ttu-id="10fce-132">MSI パッケージを適用する</span><span class="sxs-lookup"><span data-stu-id="10fce-132">Apply the MSI package</span></span> 

<span data-ttu-id="10fce-133">Microsoft Endpoint Configuration Manager などのソフトウェア配布ツールを使用して、ネットワーク上のデバイスに MSI パッケージを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="10fce-133">You can apply the MSI package to devices across your network by using software distribution tools such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="10fce-134">この手順では、ローカルコンピューターにパッケージをインストールする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="10fce-134">This procedure includes steps to install the package on your local computer.</span></span> 

1.  <span data-ttu-id="10fce-135">管理者特権のコマンドプロンプトで、.msi ファイルの完全なパスを入力して .msi パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="10fce-135">At an elevated command prompt, enter the full path of the .msi file to run the .msi package.</span></span> 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  <span data-ttu-id="10fce-136">[**警告**] ダイアログボックスで、[ **OK]** を選択するか、必要に応じて BitLocker を無効にします。</span><span class="sxs-lookup"><span data-stu-id="10fce-136">In the **Warning** dialog box, select **OK** or disable BitLocker, as appropriate.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="[OK] を選択するか、必要に応じて BitLocker を無効にします。":::
3.  <span data-ttu-id="10fce-138">[ようこそ] ページで、[**次**へ] を選んでパッケージを実行し、新しく構成された UEFI 設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="10fce-138">On the Welcome page, select **Next** to run the package and apply the newly configured UEFI setting.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="[ようこそ] ページにある [次へ] を選びます。":::
4.  <span data-ttu-id="10fce-140">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="10fce-140">Restart your device.</span></span> 

<span data-ttu-id="10fce-141">電源がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="10fce-141">Wake on Power is now configured.</span></span> <span data-ttu-id="10fce-142">設定をテストするには、デバイスの電源を切って、電源を切り、電源を再接続します。</span><span class="sxs-lookup"><span data-stu-id="10fce-142">To test the settings, turn off your device, disconnect the power, and then reconnect the power.</span></span> <span data-ttu-id="10fce-143">デバイスが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="10fce-143">The device should start automatically.</span></span> 

## <span data-ttu-id="10fce-144">参考資料</span><span class="sxs-lookup"><span data-stu-id="10fce-144">References</span></span>

<span data-ttu-id="10fce-145">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10fce-145">For more information, see the following articles.</span></span> 

- [<span data-ttu-id="10fce-146">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="10fce-146">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="10fce-147">Surface デバイス用の Wake on LAN</span><span class="sxs-lookup"><span data-stu-id="10fce-147">Wake on LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)

<span data-ttu-id="10fce-148">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="10fce-148">Still need help?</span></span> <span data-ttu-id="10fce-149">[Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="10fce-149">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>