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
ms.date: 07/22/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 9177b184d7a1d6dca63e94740b6208987d97229f
ms.sourcegitcommit: df1e178b724966e4cf8ff219c5e937e6c31cd9b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "10894113"
---
# <span data-ttu-id="7a61f-104">Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする</span><span class="sxs-lookup"><span data-stu-id="7a61f-104">Install Windows 10 Team 2020 Update Preview Build</span></span> 

<span data-ttu-id="7a61f-105">Surface hub オペレーティングシステムの最新の更新プログラム ( **windows 10 Team 2020 更新**プログラム) は、 [windows Insider プログラム](https://insider.windows.com)からの surface Hub 50 インチおよび surface hub 2s 55 インチデバイスでは追加料金なしで利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7a61f-105">The latest update of the Surface Hub operating system, **Windows 10 Team 2020 Update**, is now available at no additional cost for the Surface Hub 50-inch and Surface Hub 2S 55-inch devices from the [Windows Insider Program](https://insider.windows.com).</span></span> <span data-ttu-id="7a61f-106">Surface Hub 84 インチモデルは、Windows 10 Team 2020 Update の最終リリースでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-106">The Surface Hub 84-inch model will be supported in the final release of Windows 10 Team 2020 Update.</span></span>

<span data-ttu-id="7a61f-107">Windows 10 Team 2020 更新プログラムでは、Windows 10 の最新機能と共に、デバイスの展開と管理性が大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-107">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="7a61f-108">新機能の詳細については、次のブログ投稿を参照してください。[パブリックプレビュー用の新しい Surface HUB OS 更新プログラムがリリース](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)されました。</span><span class="sxs-lookup"><span data-stu-id="7a61f-108">To learn more about what's new, see the following blog post: [New Surface Hub OS update released for public preview.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)</span></span> <span data-ttu-id="7a61f-109">既知の問題については、下記の「既知の問題」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-109">For known issues, refer to the "Known issues" section below.</span></span>
 
## <span data-ttu-id="7a61f-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="7a61f-110">Prerequisites</span></span>

- <span data-ttu-id="7a61f-111">[Windows Insider program](https://insider.windows.com/)に登録します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-111">Register with the [Windows Insider Program](https://insider.windows.com/).</span></span>
- <span data-ttu-id="7a61f-112">Windows Insider Program Fast チャネルから Windows 10 Team 2020 更新プログラムプレビュービルドをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-112">Download the Windows 10 Team 2020 Update Preview Build from the Windows Insider Program Fast Channel.</span></span>
- <span data-ttu-id="7a61f-113">プレビュービルドをインストールしたら、必要なファームウェアの更新プログラムをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-113">After you install the Preview build, download the required firmware updates.</span></span> <span data-ttu-id="7a61f-114">注: Windows Insider プログラムを終了した場合でも、ファームウェアの更新プログラムをアンインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7a61f-114">Note: Firmware updates cannot be uninstalled even if you decide to leave the Windows Insider Program.</span></span>

## <span data-ttu-id="7a61f-115">Surface Hub を準備する</span><span class="sxs-lookup"><span data-stu-id="7a61f-115">Prepare your Surface Hub</span></span>

<span data-ttu-id="7a61f-116">作業を始める前に、Surface Hub に Windows Update からの最新の更新プログラムが含まれていることを確認し、デバイスに関連付けられている BitLocker キーを保存していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-116">Before you begin, check that your Surface Hub has the latest updates from Windows Update and make sure you save the BitLocker key associated with your device.</span></span>

**<span data-ttu-id="7a61f-117">更新プログラムを手動で確認するには:</span><span class="sxs-lookup"><span data-stu-id="7a61f-117">To manually check for updates:</span></span>**

1. <span data-ttu-id="7a61f-118">Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-118">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="7a61f-119">[**セキュリティ**  >  **Windows update** & 更新] に移動して、[**更新プログラムの確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-119">Navigate to **Update & Security** > **Windows Update** and then select **Check for updates**.</span></span>

<span data-ttu-id="7a61f-120">詳細については、「 [Surface Hub で Windows 更新プログラムを管理](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-120">For more information, see [Manage Windows updates on Surface Hub](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub).</span></span>

**<span data-ttu-id="7a61f-121">BitLocker キーを手動で保存するには:</span><span class="sxs-lookup"><span data-stu-id="7a61f-121">To manually save your BitLocker key:</span></span>**

1. <span data-ttu-id="7a61f-122">Surface Hub に USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-122">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="7a61f-123">Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-123">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="7a61f-124">「**更新 & セキュリティ**  >  の**回復**」に移動します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-124">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="7a61f-125">[ **BitLocker**] で [**保存**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-125">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="7a61f-126">BitLocker キーは、USB ドライブ上のテキストファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-126">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="7a61f-127">詳細については、「 [BitLocker キーの保存](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-127">For more information, see [Save your BitLocker key](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub).</span></span>
 
## <span data-ttu-id="7a61f-128">Windows 10 Team 2020 更新プログラムプレビュービルドをインストールする</span><span class="sxs-lookup"><span data-stu-id="7a61f-128">Install the Windows 10 Team 2020 Update Preview Build</span></span>

1. <span data-ttu-id="7a61f-129">Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-129">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="7a61f-130">[ **Update & Security**  >  **Windows Insider program** ] に移動して、[**はじめ**に] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-130">Navigate to **Update & Security** > **Windows Insider Program** and then select **Get started**.</span></span>
3. <span data-ttu-id="7a61f-131">指示に従って、職場アカウント (推奨) または個人の Microsoft アカウントを使って Windows Insider として登録します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-131">Follow the prompts to register as a Windows Insider using either your work account (recommended) or your personal Microsoft account.</span></span> <span data-ttu-id="7a61f-132">職場のアカウントで登録する利点の詳細については、「一般[法人向け Windows Insider プログラムに登録](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-132">For details on the benefits of registering with your work account, see [Register for the Windows Insider Program for Business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).</span></span>
4. <span data-ttu-id="7a61f-133">[ **Insider の設定を選択して**ください] で、[**高速**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-133">Under **Pick your Insider settings**, select **Fast**.</span></span>
5. <span data-ttu-id="7a61f-134">Surface Hub で、次の 3 ~ 4 日の間にプレビュービルドと必要なファームウェアの更新プログラムが自動的にインストールされるようにします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-134">Allow the Surface Hub to automatically install the Preview Build and the required firmware updates over the next 3 to 4 days.</span></span> <span data-ttu-id="7a61f-135">このデバイスでは、毎日の[メンテナンス](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)期間中に更新プログラムを自動的にダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-135">The device will automatically download and install the updates during daily [maintenance windows](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window).</span></span> <span data-ttu-id="7a61f-136">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-136">For example:</span></span>

- <span data-ttu-id="7a61f-137">最初のメンテナンスウィンドウで、Surface Hub は、Windows Update からプレビュービルドのダウンロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-137">During the first maintenance window, Surface Hub starts downloading the Preview Build from Windows Update.</span></span>
- <span data-ttu-id="7a61f-138">第2のメンテナンスウィンドウで、デバイスが再起動して更新プログラムを完了します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-138">During a second maintenance window, the device restarts to complete the update.</span></span>
- <span data-ttu-id="7a61f-139">3番目のメンテナンスウィンドウで、デバイスは必要なファームウェアの更新プログラムをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-139">During a third maintenance window, the device downloads and installs the required firmware updates.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a61f-140">Microsoft は、Surface Hub を3-4 日間予約して、デバイスでプレビュービルドのインストールと必要なファームウェアの更新を完了できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-140">Microsoft recommends reserving the Surface Hub for 3-4 days to allow the device to finish installing the Preview Build and the required firmware updates.</span></span> <span data-ttu-id="7a61f-141">このプロセスでデバイスを使用すると、グラフィックス、オーディオ、ユーザーインターフェイスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-141">You may experience graphics, audio, and user interface issues if you use the device during this process.</span></span>

### <span data-ttu-id="7a61f-142">プレビュービルドと必要なファームウェア更新プログラムを手動でインストールする場合は、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-142">If you choose to manually install the Preview Build and required firmware updates:</span></span>

1. <span data-ttu-id="7a61f-143">Windows Insider program に登録した後、[**設定**  >  の**更新] & [セキュリティ**  >  の**Windows Update** ] に移動し、[**更新プログラムの確認**] を選んでプレビュービルドをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a61f-143">After you've registered with the Windows Insider Program, go to **Settings** > **Update & Security** > **Windows Update** and select **Check for updates** to install the Preview Build.</span></span>
2. <span data-ttu-id="7a61f-144">プレビュービルドがインストールされたら (最大14時間かかることがあります)、[**今すぐ再起動**] を選択してインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-144">Once the Preview Build installs (it may take up to 14 hours), select **Restart now** to complete the installation.</span></span>
3. <span data-ttu-id="7a61f-145">デバイスが再起動したら、[**設定**  >  の**更新 & セキュリティ**  >  の**Windows Update**] に移動し、[更新プログラムの確認] を選んで、**必要なファームウェアの更新プログラムをインストール**します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-145">After the device restarts, go to **Settings** > **Update & Security** > **Windows Update**, and select **Check for updates to install required firmware updates**.</span></span>
4. <span data-ttu-id="7a61f-146">ファームウェアがインストールされたら、[**今すぐ再起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-146">Once the firmware installs, select **Restart now**.</span></span>

> [!WARNING]
> <span data-ttu-id="7a61f-147">必要なファームウェアの更新プログラムをインストールせずにプレビュービルドをインストールした場合、グラフィックス、オーディオ、ユーザーインターフェイスの問題が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-147">You may see graphics, audio, and user interface issues if you install the Preview Build without installing the required firmware updates.</span></span>

> [!NOTE]
> <span data-ttu-id="7a61f-148">Windows Insider プログラムを終了して Surface Hub を旧バージョンのオペレーティングシステムに戻す場合は、まず[デバイスをリセット](https://docs.microsoft.com/surface-hub/device-reset-surface-hub)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-148">If you choose to leave the Windows Insider Program and revert your Surface Hub to an older version of the operating system, you must first [reset your device](https://docs.microsoft.com/surface-hub/device-reset-surface-hub).</span></span> <span data-ttu-id="7a61f-149">後でデバイスを再構成するには、[最初の run プログラムを実行](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-149">Afterwards, you will need to go through the [first run program](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) to re-configure your device.</span></span>
 
## <span data-ttu-id="7a61f-150">既知の問題: Windows 10 Team 2020 更新プログラムプレビュービルド</span><span class="sxs-lookup"><span data-stu-id="7a61f-150">Known issues: Windows 10 Team 2020 Update Preview Build</span></span>

### <span data-ttu-id="7a61f-151">グラフィックス、オーディオ、ユーザーインターフェイスの問題</span><span class="sxs-lookup"><span data-stu-id="7a61f-151">Graphics, audio, and user interface issues</span></span> 

<span data-ttu-id="7a61f-152">プレビュービルドをインストールしても、必要なファームウェアの更新プログラムをすぐにインストールしないと、さまざまなグラフィックスとユーザーインターフェイスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-152">You may experience various graphics and user interface issues if you install the Preview Build, but do not immediately install the required firmware updates afterward.</span></span> <span data-ttu-id="7a61f-153">Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこれらの問題を解決する予定です。</span><span class="sxs-lookup"><span data-stu-id="7a61f-153">Microsoft plans to fix these issues in the release build of Windows 10 Team 2020 Update.</span></span>

### <span data-ttu-id="7a61f-154">Surface Hub 84 インチ: グラフィックスとユーザーインターフェイスの問題</span><span class="sxs-lookup"><span data-stu-id="7a61f-154">Surface Hub 84-inch: graphics and user interface issues</span></span>

<span data-ttu-id="7a61f-155">第1世代の Surface Hub 84 インチデバイスにプレビュービルドをインストールすると、さまざまなグラフィックスとユーザーインターフェイスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-155">You may experience various graphics and user interface issues if you install the Preview Build on a first-generation Surface Hub 84-inch device.</span></span> <span data-ttu-id="7a61f-156">Surface Hub 84 インチは、Windows 10 Team 2020 Update の最終リリースでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-156">The Surface Hub 84-inch will be supported in the final release of Windows 10 Team 2020 Update.</span></span>

### <span data-ttu-id="7a61f-157">条件付きアクセスポリシーが適用されると、サインインが影響を受ける</span><span class="sxs-lookup"><span data-stu-id="7a61f-157">Sign in is impacted when Conditional Access policies are applied</span></span>

- <span data-ttu-id="7a61f-158">Microsoft ホワイトボードなどのアプリにサインインしようとすると、サインインが失敗します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-158">Sign in fails when attempting to sign into apps such as Microsoft Whiteboard.</span></span> <span data-ttu-id="7a61f-159">ユーザーは、[スタート] メニューから[[自分の会議] と [ファイル](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub)] から初めてサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-159">Users must first sign in from [My meetings and files](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub) from the Start menu.</span></span>

- <span data-ttu-id="7a61f-160">ユーザーアカウントが、Surface Hub で Azure AD join によって使用されているものとは異なる Azure AD テナントに登録されている場合、サインインが失敗します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-160">Sign in fails if your user account is registered to a different Azure AD tenant than the one used by Surface Hub to Azure AD join.</span></span>

<span data-ttu-id="7a61f-161">Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこれらの問題を解決する予定です。</span><span class="sxs-lookup"><span data-stu-id="7a61f-161">Microsoft plans to fix these issues in the release build of Windows 10 Team 2020 Update.</span></span>

### <span data-ttu-id="7a61f-162">Windows Update によって、利用できない場合に新しいドライバーをインストールするように求められる</span><span class="sxs-lookup"><span data-stu-id="7a61f-162">Windows Update prompts to install new drivers when none are available</span></span>

<span data-ttu-id="7a61f-163">**Settings**  >  **Update & Security**  >  Windows 10 Team 2020 更新プログラムと必要なファームウェア更新プログラムをインストールした後、[設定の更新] & セキュリティの**Windows Update**に移動すると、次のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-163">When you go to **Settings** > **Update & Security** > **Windows Update** after you’ve installed Windows 10 Team 2020 Update and the required firmware updates, you may see the following error:</span></span> 

- <span data-ttu-id="7a61f-164">"お使いの PC の最新のドライバーは、インストールしようとしているドライバーよりも優れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-164">“A current driver on your PC may be better than the driver we’re trying to install.</span></span> <span data-ttu-id="7a61f-165">引き続きインストールしようとしています。 "</span><span class="sxs-lookup"><span data-stu-id="7a61f-165">We’ll keep trying to install.”</span></span> 

<span data-ttu-id="7a61f-166">このエラーは安全に無視することができます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-166">This error can be safely ignored.</span></span> <span data-ttu-id="7a61f-167">Microsoft は、この問題を積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-167">Microsoft is actively investigating this issue.</span></span>

### <span data-ttu-id="7a61f-168">プロビジョニングパッケージを使用して Surface Hub ポリシーをインストールできない</span><span class="sxs-lookup"><span data-stu-id="7a61f-168">Unable to install Surface Hub policies using provisioning packages</span></span>

<span data-ttu-id="7a61f-169">Surface Hub 構成サービスプロバイダー (CSP) のポリシーを使用するプロビジョニングパッケージは、インストールに失敗します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-169">Provisioning packages that use policies from the Surface Hub Configuration Service Provider (CSP) fail to install.</span></span> <span data-ttu-id="7a61f-170">ここでは、Microsoft Intune または別のモバイルデバイス管理 (MDM) プロバイダーを使用して Surface Hub ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-170">For now, use Microsoft Intune or another mobile device management (MDM) provider to apply Surface Hub policies.</span></span> <span data-ttu-id="7a61f-171">Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこの問題を解決する予定です。</span><span class="sxs-lookup"><span data-stu-id="7a61f-171">Microsoft plans to fix this issue in the release build of Windows 10 Team 2020 Update.</span></span>

### <span data-ttu-id="7a61f-172">初めて実行するときに、USB ドライブを削除するかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="7a61f-172">Prompt to remove USB drive prematurely during first run</span></span>

<span data-ttu-id="7a61f-173">初めて実行するときに、プロビジョニングパッケージを使って Surface Hub をセットアップすると、デバイスが Surface Hub 構成ファイルを読み取ることができるようになる前に、USB ドライブを削除するように求められます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-173">When using a provisioning package to setup Surface Hub during first run, you’re prompted to remove the USB drive before the device is able to read the Surface Hub configuration file.</span></span> <span data-ttu-id="7a61f-174">構成ファイルを使ってデバイスアカウントを設定している場合は、このメッセージを無視します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-174">Ignore the message if you’re using a configure file to setup your device account.</span></span> <span data-ttu-id="7a61f-175">Microsoft は、この問題を積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-175">Microsoft is actively investigating this issue.</span></span>
 
### <span data-ttu-id="7a61f-176">初回実行時にプロキシ設定を設定できない</span><span class="sxs-lookup"><span data-stu-id="7a61f-176">Unable to set up proxy settings during first run</span></span>

<span data-ttu-id="7a61f-177">プロキシを使ってインターネットに接続している場合は、初回実行プログラムでインターネット接続が制限されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-177">If you use a proxy to connect to the Internet, you may have limited Internet connectivity during the first run program.</span></span> <span data-ttu-id="7a61f-178">Microsoft は、Windows 10 Team 2020 更新プログラムのリリースビルドでこの問題を解決する予定です。</span><span class="sxs-lookup"><span data-stu-id="7a61f-178">Microsoft plans to fix this issue in the release build of Windows 10 Team 2020 Update.</span></span>
 
### <span data-ttu-id="7a61f-179">Microsoft Store からアプリをダウンロードするとエラーが表示される</span><span class="sxs-lookup"><span data-stu-id="7a61f-179">An error appears when you download apps from Microsoft Store</span></span>

<span data-ttu-id="7a61f-180">Microsoft Store からアプリをダウンロードするには、サインインを求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-180">To download an app from the Microsoft Store, you will see a prompt to sign in.</span></span> <span data-ttu-id="7a61f-181">既知の問題により、サインイン中にエラーが発生しますが、アプリのダウンロード機能には影響しません。</span><span class="sxs-lookup"><span data-stu-id="7a61f-181">A known issue causes an error to appear during sign-in, but this doesn't affect your ability to download apps.</span></span> <span data-ttu-id="7a61f-182">Microsoft は、この問題を積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-182">Microsoft is actively investigating this issue.</span></span>

### <span data-ttu-id="7a61f-183">Surface Hub 2S が断続的に Wi-fi 接続を切断する</span><span class="sxs-lookup"><span data-stu-id="7a61f-183">Surface Hub 2S intermittently loses Wi-Fi connection</span></span>

<span data-ttu-id="7a61f-184">デバイスを取り外してもう一度接続するか、またはイーサネットケーブルを使ってインターネットに接続してみてください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-184">Try unplugging your device and plugging it back in, or using an Ethernet cable to connect to the Internet.</span></span> <span data-ttu-id="7a61f-185">Microsoft は、この問題を積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-185">Microsoft is actively investigating this issue.</span></span>

### <span data-ttu-id="7a61f-186">Surface Hub の2S がスリープ状態から再開できない</span><span class="sxs-lookup"><span data-stu-id="7a61f-186">Surface Hub 2S intermittently fails to resume from sleep</span></span>

<span data-ttu-id="7a61f-187">Surface Hub 2S が断続的にスリープ状態から再開せず、Microsoft ロゴが表示された画面で応答しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-187">Surface Hub 2S may intermittently fail to fully resume from sleep and appear to stop responding on a screen showing the Microsoft logo.</span></span> <span data-ttu-id="7a61f-188">デバイスを取り外して、もう一度接続してみてください。</span><span class="sxs-lookup"><span data-stu-id="7a61f-188">Try unplugging your device and plugging it back in.</span></span> 

<span data-ttu-id="7a61f-189">この問題を回避するには:</span><span class="sxs-lookup"><span data-stu-id="7a61f-189">To prevent this issue:</span></span>

1. <span data-ttu-id="7a61f-190">Surface Hub で、[**設定**] を開き、メッセージが表示されたら、管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-190">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="7a61f-191">Power & **Surface Hub**  >  **セッション**に移動します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-191">Navigate to **Surface Hub** > **Session & power**.</span></span> 
3. <span data-ttu-id="7a61f-192">[**デバイスがスリープ状態になったとき] で、この電源設定を使用**し、[**接続さ**れたスタンバイ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-192">Under **When the device goes to sleep, use this power setting**, select **Connected Standby.**</span></span>
4. <span data-ttu-id="7a61f-193">[**存在しない場合は、デバイスをスリープ状態にする**] で [なし] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="7a61f-193">Under **When no one is present, put the device to sleep after**, select **Never.**</span></span>

<span data-ttu-id="7a61f-194">Microsoft は、Windows 10 Team 2020 更新プログラムの最終リリース前のファームウェア更新プログラムでこの問題を解決する予定です。</span><span class="sxs-lookup"><span data-stu-id="7a61f-194">Microsoft plans to fix this issue in a firmware update prior to the final release of Windows 10 Team 2020 Update.</span></span>

### <span data-ttu-id="7a61f-195">Connect アプリが表示されていない場合のプロジェクションの問題</span><span class="sxs-lookup"><span data-stu-id="7a61f-195">Projection issues when the Connect app is not in view</span></span>

- <span data-ttu-id="7a61f-196">ケーブルを使用して Surface Hub に接続すると、Connect アプリから移動したときに touchback が機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="7a61f-196">When you use a cable to project to Surface Hub, touchback stops working if you navigate away from the Connect app.</span></span>
- <span data-ttu-id="7a61f-197">Miracast を使用して Surface Hub にプロジェクトを作成すると、接続アプリから移動した後すぐにワイヤレス接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="7a61f-197">When you project to Surface Hub using Miracast, the wireless connection drops soon after you navigate away from the Connect app.</span></span>

<span data-ttu-id="7a61f-198">Microsoft は、これらの問題について積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-198">Microsoft is actively investigating these issues.</span></span>

### <span data-ttu-id="7a61f-199">Skype for Business がメディアトラフィックにプロキシを使用していない</span><span class="sxs-lookup"><span data-stu-id="7a61f-199">Skype for Business isn't using proxy for media traffic</span></span>

<span data-ttu-id="7a61f-200">プロキシを使用する一部のデバイスでは、Skype for Business でサインインすることはできますが、メディアトラフィックにプロキシサーバーを使いません。</span><span class="sxs-lookup"><span data-stu-id="7a61f-200">For some devices that use a proxy, Skype for Business can sign in, but will not use the proxy server for media traffic.</span></span> <span data-ttu-id="7a61f-201">Microsoft は、この問題を積極的に調査しています。</span><span class="sxs-lookup"><span data-stu-id="7a61f-201">Microsoft is actively investigating this issue.</span></span>

<span data-ttu-id="7a61f-202">Microsoft のサポートを利用して、お客様の洞察と提案を共有します。</span><span class="sxs-lookup"><span data-stu-id="7a61f-202">We invite you to share your insights and suggestions with Microsoft Support.</span></span>

## <span data-ttu-id="7a61f-203">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7a61f-203">Learn more</span></span>

- [<span data-ttu-id="7a61f-204">パブリックプレビュー用の新しい Surface Hub OS 更新プログラムがリリースされました。</span><span class="sxs-lookup"><span data-stu-id="7a61f-204">New Surface Hub OS update released for public preview.</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [<span data-ttu-id="7a61f-205">Windows Insider Program for Business をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="7a61f-205">Getting started with the Windows Insider Program for Business</span></span>](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)