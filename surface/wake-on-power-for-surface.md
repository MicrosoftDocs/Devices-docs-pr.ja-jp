---
title: Surface の電源でスリープ解除を有効にする方法
ms.author: v-todmc
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121602
ms.reviewer: hachidan
description: Surface デバイスの電源でスリープ解除を有効または無効にする方法について説明します。
keywords: 更新, 展開, ドライバー, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.date: 01/15/2021
ms.openlocfilehash: 6ad359861f6af29c567bf0fbf26878ec15c7c642
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271561"
---
# <span data-ttu-id="bff8c-104">Surface デバイス での Wake On Power の使用</span><span class="sxs-lookup"><span data-stu-id="bff8c-104">Wake on Power for Surface devices</span></span>

<span data-ttu-id="bff8c-105">Surface デバイスは、デスクから離れた状態で電源をオフにしたり、休止モードに設定してバッテリ残量を節約できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-105">Surface devices can be powered off while you're away from your desk, or set to hibernate mode to save battery life.</span></span> <span data-ttu-id="bff8c-106">これらのデバイスの管理性を向上させるために、Wake on Power を使用すると、互換性のある Surface デバイスが電源に再接続されると自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-106">To improve the manageability of these devices, Wake on Power enables compatible Surface devices to automatically start when they're reconnected to power.</span></span> <span data-ttu-id="bff8c-107">電源でのスリープ解除を構成するには、Surface UEFI コンフィエーターまたは UEFI マネージャーを使用して Surface Enterprise Management Mode (SEMM) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-107">To configure Wake on Power, you can use Surface Enterprise Management Mode (SEMM) either through Surface UEFI Configurator or the UEFI Manager.</span></span>

<span data-ttu-id="bff8c-108">電源でのスリープ解除機能は、次のデバイスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-108">The Wake on Power feature is available on the following devices:</span></span>

- <span data-ttu-id="bff8c-109">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="bff8c-109">Surface Pro 7+</span></span>
- <span data-ttu-id="bff8c-110">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="bff8c-110">Surface Book 3</span></span>
- <span data-ttu-id="bff8c-111">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="bff8c-111">Surface Pro 7</span></span>
- <span data-ttu-id="bff8c-112">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="bff8c-112">Surface Laptop 3</span></span>
- <span data-ttu-id="bff8c-113">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="bff8c-113">Surface Laptop Go</span></span>
- <span data-ttu-id="bff8c-114">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="bff8c-114">Surface Pro X</span></span> 


## <span data-ttu-id="bff8c-115">概要と前提条件</span><span class="sxs-lookup"><span data-stu-id="bff8c-115">Overview and prerequisites</span></span>

<span data-ttu-id="bff8c-116">Surface UEFI Configurator を使うと、ターゲット デバイスに配布するために、Windows インストーラー .msi パッケージに個々の UEFI 設定を保存できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-116">Surface UEFI Configurator lets you save individual UEFI settings in a Windows Installer .msi package for distribution to target devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="bff8c-117">この記事では、SEMM の使い方を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bff8c-117">This article assumes that you know how to use SEMM.</span></span> <span data-ttu-id="bff8c-118">詳細については [、Surface Enterprise Management Mode (SEMM) のドキュメントを参照](surface-enterprise-management-mode.md) してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-118">For more information, see [Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md) documentation.</span></span>

## <span data-ttu-id="bff8c-119">電源でスリープ解除を有効にするには</span><span class="sxs-lookup"><span data-stu-id="bff8c-119">To enable Wake on Power</span></span>

1.  <span data-ttu-id="bff8c-120">Surface UEFI コンフィエーター [の最新バージョンをダウンロードします](https://www.microsoft.com/download/confirmation.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="bff8c-120">Download the latest version of [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span></span>
2.  <span data-ttu-id="bff8c-121">管理者として Surface デバイスにサインインし **、Surface UEFI**コンフィケーターを開き **、Surface デバイス**を選択して、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-121">Sign in to your Surface device as an administrator, open **Surface UEFI Configurator**, select **Surface Devices**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="[Surface デバイス] を選択し、[次へ] を選択します。":::
3.  <span data-ttu-id="bff8c-123">[**スタート] を**選択し、[構成パッケージ]**で [作成\*\*\*\*] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-123">Select **Start**, and then select **Create** under **Configuration Package**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="[構成パッケージの作成] を選択します。":::
4.  <span data-ttu-id="bff8c-125">[ **証明書の保護]** を選択し、証明書の .pfx ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-125">Select **Certificate Protection**, and add your certificate .pfx file.</span></span> 
5. <span data-ttu-id="bff8c-126">パスワードを入力し、[ **次へ] を選択し**、必要に応じて **パスワード**保護を追加して、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-126">Enter your password, select **Next**, add **Password Protection**, as appropriate, and then select **Next**.</span></span>
6.  <span data-ttu-id="bff8c-127">[ターゲット **とする Surface の種類の選択** ] ページで、必要に応じてターゲット デバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-127">On the **Choose which Surface type you want to target** page, select your target devices as appropriate.</span></span> <span data-ttu-id="bff8c-128">たとえば **、Surface Pro 7 を選択します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-128">For example, select **Surface Pro 7**.</span></span>
7.  <span data-ttu-id="bff8c-129">[高度 **な機能] ページ** で、[ **電源でスリープ**解除] を選択し、機能を **[オン**] に設定して、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-129">On the **Advanced Features** page, select **Wake on Power**, set the feature to **On**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="[電源でスリープ解除] を選択し、[オン] に設定します。"::: 
8.  <span data-ttu-id="bff8c-131">[成功] **ページで** 、[終了] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="bff8c-131">On the **Successful** page, select **End**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bff8c-132">初めて設定をデバイスに提供する場合は、証明書の拇印の最後の 2 文字も入力するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-132">If this is the first time that you are providing settings to your device, you will be prompted to also provide the last two characters of the certificate thumbprint.</span></span> 
9.  <span data-ttu-id="bff8c-133">.msi パッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-133">Save the .msi package.</span></span> 

## <span data-ttu-id="bff8c-134">MSI パッケージを適用する</span><span class="sxs-lookup"><span data-stu-id="bff8c-134">Apply the MSI package</span></span> 

<span data-ttu-id="bff8c-135">Microsoft Endpoint Configuration Manager などのソフトウェア配布ツールを使用して、ネットワーク上のデバイスに MSI パッケージを適用できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-135">You can apply the MSI package to devices across your network by using software distribution tools such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="bff8c-136">この手順には、ローカル コンピューターにパッケージをインストールする手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bff8c-136">This procedure includes steps to install the package on your local computer.</span></span> 

1.  <span data-ttu-id="bff8c-137">管理者特権でのコマンド プロンプトで、.msi ファイルの完全パスを入力して .msi パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-137">At an elevated command prompt, enter the full path of the .msi file to run the .msi package.</span></span> 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  <span data-ttu-id="bff8c-138">[警告 **] ダイアログ ボックス** で **、[OK]** を選択するか、必要に応じて BitLocker を無効にします。</span><span class="sxs-lookup"><span data-stu-id="bff8c-138">In the **Warning** dialog box, select **OK** or disable BitLocker, as appropriate.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="[OK] を選択するか、必要に応じて BitLocker を無効にします。":::
3.  <span data-ttu-id="bff8c-140">[ようこそ] ページで、[次へ] **を選択** してパッケージを実行し、新しく構成した UEFI 設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-140">On the Welcome page, select **Next** to run the package and apply the newly configured UEFI setting.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="ウェルカム ページの 1 つで、[次へ] を選択します。":::
4.  <span data-ttu-id="bff8c-142">デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-142">Restart your device.</span></span> 

<span data-ttu-id="bff8c-143">電源でスリープ解除が構成されます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-143">Wake on Power is now configured.</span></span> <span data-ttu-id="bff8c-144">設定をテストするには、デバイスをオフにし、電源を切り、電源を再接続します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-144">To test the settings, turn off your device, disconnect the power, and then reconnect the power.</span></span> <span data-ttu-id="bff8c-145">デバイスが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-145">The device should start automatically.</span></span> 

## <span data-ttu-id="bff8c-146">参考資料</span><span class="sxs-lookup"><span data-stu-id="bff8c-146">References</span></span>

<span data-ttu-id="bff8c-147">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-147">For more information, see the following articles.</span></span> 

- [<span data-ttu-id="bff8c-148">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="bff8c-148">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="bff8c-149">Surface デバイスの LAN でのスリープ解除</span><span class="sxs-lookup"><span data-stu-id="bff8c-149">Wake on LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)

<span data-ttu-id="bff8c-150">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="bff8c-150">Still need help?</span></span> <span data-ttu-id="bff8c-151">Microsoft コミュニティ [に移動します](https://answers.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="bff8c-151">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>