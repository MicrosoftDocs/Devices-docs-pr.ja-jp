---
title: Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする
description: Surface Hub オペレーティングシステムの最新の更新プログラムである Windows 10 Team 2020 Update を使用できるようになりました。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 08/13/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 51d6b9169b0074eb474ddc89b6fe9b43a921bb07
ms.sourcegitcommit: feb81137d009d9b7c743aabd7d02615e89842200
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "10929769"
---
# <span data-ttu-id="4b9a0-104">Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする</span><span class="sxs-lookup"><span data-stu-id="4b9a0-104">Install Windows 10 Team 2020 Update Preview Build</span></span> 

<span data-ttu-id="4b9a0-105">Surface hub オペレーティングシステムの最新の更新プログラム ( **windows 10 Team 2020 更新**プログラム) は、 [windows Insider プログラム](https://insider.windows.com)からの surface Hub 50 インチおよび surface hub 2s 55 インチデバイスでは追加料金なしで利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-105">The latest update of the Surface Hub operating system, **Windows 10 Team 2020 Update**, is now available at no additional cost for the Surface Hub 50-inch and Surface Hub 2S 55-inch devices from the [Windows Insider Program](https://insider.windows.com).</span></span> <span data-ttu-id="4b9a0-106">Surface Hub 84 インチモデルは、Windows 10 Team 2020 Update の最終リリースでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-106">The Surface Hub 84-inch model will be supported in the final release of Windows 10 Team 2020 Update.</span></span>

<span data-ttu-id="4b9a0-107">Windows 10 Team 2020 更新プログラムでは、Windows 10 の最新機能と共に、デバイスの展開と管理性が大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-107">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="4b9a0-108">新機能の詳細については、次のブログ投稿を参照してください。[パブリックプレビュー用の新しい Surface HUB OS 更新プログラムがリリース](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)されました。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-108">To learn more about what's new, see the following blog post: [New Surface Hub OS update released for public preview.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)</span></span> <span data-ttu-id="4b9a0-109">既知の問題については、下記の「既知の問題」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-109">For known issues, refer to the "Known issues" section below.</span></span>
 
## <span data-ttu-id="4b9a0-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="4b9a0-110">Prerequisites</span></span>

- <span data-ttu-id="4b9a0-111">[Windows Insider program](https://insider.windows.com/)に登録します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-111">Register with the [Windows Insider Program](https://insider.windows.com/).</span></span>
- <span data-ttu-id="4b9a0-112">Windows Insider Program Fast チャネルから Windows 10 Team 2020 更新プログラムプレビュービルドをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-112">Download the Windows 10 Team 2020 Update Preview Build from the Windows Insider Program Fast Channel.</span></span>
- <span data-ttu-id="4b9a0-113">プレビュービルドをインストールしたら、必要なファームウェアの更新プログラムをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-113">After you install the Preview build, download the required firmware updates.</span></span> <span data-ttu-id="4b9a0-114">注: Windows Insider プログラムを終了した場合でも、ファームウェアの更新プログラムをアンインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-114">Note: Firmware updates cannot be uninstalled even if you decide to leave the Windows Insider Program.</span></span>

## <span data-ttu-id="4b9a0-115">Surface Hub を準備する</span><span class="sxs-lookup"><span data-stu-id="4b9a0-115">Prepare your Surface Hub</span></span>

<span data-ttu-id="4b9a0-116">作業を始める前に、Surface Hub に Windows Update からの最新の更新プログラムが含まれていることを確認し、デバイスに関連付けられている BitLocker キーを保存していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-116">Before you begin, check that your Surface Hub has the latest updates from Windows Update and make sure you save the BitLocker key associated with your device.</span></span>

**<span data-ttu-id="4b9a0-117">更新プログラムを手動で確認するには:</span><span class="sxs-lookup"><span data-stu-id="4b9a0-117">To manually check for updates:</span></span>**

1. <span data-ttu-id="4b9a0-118">Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-118">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="4b9a0-119">[**セキュリティ**  >  **Windows update** & 更新] に移動して、[**更新プログラムの確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-119">Navigate to **Update & Security** > **Windows Update** and then select **Check for updates**.</span></span>

<span data-ttu-id="4b9a0-120">詳細については、「 [Surface Hub で Windows 更新プログラムを管理](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-120">For more information, see [Manage Windows updates on Surface Hub](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub).</span></span>

**<span data-ttu-id="4b9a0-121">BitLocker キーを手動で保存するには:</span><span class="sxs-lookup"><span data-stu-id="4b9a0-121">To manually save your BitLocker key:</span></span>**

1. <span data-ttu-id="4b9a0-122">Surface Hub に USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-122">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="4b9a0-123">Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-123">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="4b9a0-124">「**更新 & セキュリティ**  >  の**回復**」に移動します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-124">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="4b9a0-125">[ **BitLocker**] で [ **保存**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-125">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="4b9a0-126">BitLocker キーは、USB ドライブ上のテキストファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-126">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="4b9a0-127">詳細については、「 [BitLocker キーの保存](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-127">For more information, see [Save your BitLocker key](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub).</span></span>
 
## <span data-ttu-id="4b9a0-128">Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする</span><span class="sxs-lookup"><span data-stu-id="4b9a0-128">Install the Windows 10 Team 2020 Update Preview Build</span></span>

1. <span data-ttu-id="4b9a0-129">Surface Hub で、[ **設定** ] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-129">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="4b9a0-130">[ **プライバシー > 診断 & フィードバック** に移動し、診断データを [ **完全**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-130">Navigate to **Privacy > Diagnostics & feedback** and set Diagnostic data to **Full**.</span></span> <span data-ttu-id="4b9a0-131">一部の地域や組織では、MDM ポリシーまたは PPKG ファイルを使用してこの設定を適用する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-131">Some regions or organizations may need to apply this setting via MDM policy or PPKG file:</span></span>
   - <span data-ttu-id="4b9a0-132">**MDM の場合:** 次のポリシーを設定します。**/Vendor/MSFT/Policy/System/AllowTelemetry** の整数値3を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-132">**For MDM:** Set the following policy: .**/Vendor/MSFT/Policy/System/AllowTelemetry** with the integer value of 3:</span></span>
    
        ![AllowTelemetry を3に設定します](images/hub-2020-allow-telemetry.png)

    - <span data-ttu-id="4b9a0-134">**PPKG:**[Ppkg ファイル](https://aka.ms/HubTltmtry)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-134">**For PPKG:** Download the [PPKG file](https://aka.ms/HubTltmtry).</span></span>

3. <span data-ttu-id="4b9a0-135">[ **Update & Security**  >  **Windows Insider program** ] に移動して、[登録の**開始**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-135">Navigate to **Update & Security** > **Windows Insider Program** and then select **Get started** to enroll.</span></span>
4. <span data-ttu-id="4b9a0-136">指示に従って、職場アカウント (推奨) または個人の Microsoft アカウントを使って Windows Insider として登録します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-136">Follow the prompts to register as a Windows Insider using either your work account (recommended) or your personal Microsoft account.</span></span> <span data-ttu-id="4b9a0-137">職場のアカウントで登録する利点の詳細については、「一般 [法人向け Windows Insider プログラムに登録](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-137">For details on the benefits of registering with your work account, see [Register for the Windows Insider Program for Business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).</span></span>
5. <span data-ttu-id="4b9a0-138">[ **Insider の設定を選択して**ください] で、[ **高速**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-138">Under **Pick your Insider settings**, select **Fast**.</span></span>
6. <span data-ttu-id="4b9a0-139">Surface Hub で、次の 3 ~ 4 日の間にプレビュービルドと必要なファームウェアの更新プログラムが自動的にインストールされるようにします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-139">Allow the Surface Hub to automatically install the Preview Build and the required firmware updates over the next 3 to 4 days.</span></span> <span data-ttu-id="4b9a0-140">このデバイスでは、毎日の [メンテナンス](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)期間中に更新プログラムを自動的にダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-140">The device will automatically download and install the updates during daily [maintenance windows](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window).</span></span> <span data-ttu-id="4b9a0-141">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-141">For example:</span></span>

- <span data-ttu-id="4b9a0-142">最初のメンテナンスウィンドウで、Surface Hub は、Windows Update からプレビュービルドのダウンロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-142">During the first maintenance window, Surface Hub starts downloading the Preview Build from Windows Update.</span></span>
- <span data-ttu-id="4b9a0-143">第2のメンテナンスウィンドウで、デバイスが再起動して更新プログラムを完了します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-143">During a second maintenance window, the device restarts to complete the update.</span></span>
- <span data-ttu-id="4b9a0-144">3番目のメンテナンスウィンドウで、デバイスは必要なファームウェアの更新プログラムをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-144">During a third maintenance window, the device downloads and installs the required firmware updates.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b9a0-145">Microsoft は、Surface Hub を3-4 日間予約して、デバイスでプレビュービルドのインストールと必要なファームウェアの更新を完了できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-145">Microsoft recommends reserving the Surface Hub for 3-4 days to allow the device to finish installing the Preview Build and the required firmware updates.</span></span> <span data-ttu-id="4b9a0-146">このプロセスでデバイスを使用すると、グラフィックス、オーディオ、ユーザーインターフェイスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-146">You may experience graphics, audio, and user interface issues if you use the device during this process.</span></span>

### <span data-ttu-id="4b9a0-147">プレビュービルドと必要なファームウェア更新プログラムを手動でインストールする場合は、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-147">If you choose to manually install the Preview Build and required firmware updates:</span></span>

1. <span data-ttu-id="4b9a0-148">Windows Insider program に登録した後、[**設定**  >  の**更新] & [セキュリティ**  >  の**Windows Update** ] に移動し、[**更新プログラムの確認**] を選んでプレビュービルドをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-148">After you've registered with the Windows Insider Program, go to **Settings** > **Update & Security** > **Windows Update** and select **Check for updates** to install the Preview Build.</span></span>
2. <span data-ttu-id="4b9a0-149">プレビュービルドがインストールされたら (最大14時間かかることがあります)、[ **今すぐ再起動** ] を選択してインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-149">Once the Preview Build installs (it may take up to 14 hours), select **Restart now** to complete the installation.</span></span>
3. <span data-ttu-id="4b9a0-150">デバイスが再起動したら、[**設定**  >  の**更新 & セキュリティ**  >  の**Windows Update**] に移動し、[更新プログラムの確認] を選んで、**必要なファームウェアの更新プログラムをインストール**します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-150">After the device restarts, go to **Settings** > **Update & Security** > **Windows Update**, and select **Check for updates to install required firmware updates**.</span></span>
4. <span data-ttu-id="4b9a0-151">ファームウェアがインストールされたら、[ **今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-151">Once the firmware installs, select **Restart now**.</span></span>

> [!WARNING]
> <span data-ttu-id="4b9a0-152">必要なファームウェアの更新プログラムをインストールせずにプレビュービルドをインストールした場合、グラフィックス、オーディオ、ユーザーインターフェイスの問題が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-152">You may see graphics, audio, and user interface issues if you install the Preview Build without installing the required firmware updates.</span></span>

> [!NOTE]
> <span data-ttu-id="4b9a0-153">Windows Insider プログラムを終了して Surface Hub を旧バージョンのオペレーティングシステムに戻す場合は、まず [デバイスをリセット](https://docs.microsoft.com/surface-hub/device-reset-surface-hub)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-153">If you choose to leave the Windows Insider Program and revert your Surface Hub to an older version of the operating system, you must first [reset your device](https://docs.microsoft.com/surface-hub/device-reset-surface-hub).</span></span> <span data-ttu-id="4b9a0-154">後でデバイスを再構成するには、 [最初の run プログラムを実行](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-154">Afterwards, you will need to go through the [first run program](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) to re-configure your device.</span></span>
 

## <span data-ttu-id="4b9a0-155">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4b9a0-155">Learn more</span></span>

- [<span data-ttu-id="4b9a0-156">既知の問題: Windows 10 Team 2020 更新プログラム</span><span class="sxs-lookup"><span data-stu-id="4b9a0-156">Known issues: Windows 10 Team 2020 Update</span></span>](surface-hub-2020-team-update-known-issues.md)
- [<span data-ttu-id="4b9a0-157">パブリックプレビュー用の新しい Surface Hub OS 更新プログラムがリリースされました。</span><span class="sxs-lookup"><span data-stu-id="4b9a0-157">New Surface Hub OS update released for public preview.</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [<span data-ttu-id="4b9a0-158">Windows Insider Program for Business をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="4b9a0-158">Getting started with the Windows Insider Program for Business</span></span>](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)