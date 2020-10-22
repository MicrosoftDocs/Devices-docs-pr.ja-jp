---
title: 互換性のある Surface デバイスでの SSD の削除
description: この記事は、IT 技術者を対象としています。 Surface Pc 3、Surface Pro X、Surface Pc での Ssd の削除と交換については、推奨されるベストプラクティスについて説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 10/21/2020
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 56c740b39d86ea3fab386e88efa6932e050bb957
ms.sourcegitcommit: 959d2d856b1e5b5c72cd636f576b5feb1b633048
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "11133172"
---
# <span data-ttu-id="18f33-103">互換性のある Surface デバイスからの SSD の削除に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="18f33-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18f33-104">この記事は、組織内で限定された IT 技術者による使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="18f33-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="18f33-105">以下の互換性のある Surface デバイスで、お勧めの技術者が Ssd の削除と交換を行う際に推奨されるベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="18f33-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="18f33-106">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="18f33-106">Surface Laptop 3</span></span> 
- <span data-ttu-id="18f33-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="18f33-107">Surface Pro X</span></span> 
- <span data-ttu-id="18f33-108">Surface のノート Pc の移動</span><span class="sxs-lookup"><span data-stu-id="18f33-108">Surface Laptop Go</span></span>

> [!WARNING]
> <span data-ttu-id="18f33-109">デバイスを開いたり、デバイスコンポーネントを交換したりすると、感電、デバイスの損傷、火災、および個人の傷害のリスク、およびその他の危険を生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18f33-109">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="18f33-110">このようなアクティビティを行うときは、常に注意してください。</span><span class="sxs-lookup"><span data-stu-id="18f33-110">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="18f33-111">[エンタープライズ向けの Rssd の削除ガイド](https://www.microsoft.com/download/100440)に記載されている安全性に関する注意事項と手順に従います。</span><span class="sxs-lookup"><span data-stu-id="18f33-111">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="18f33-112">「Enterprise 向けの rSSD の削除ガイド」で指定されている安全性の予防策と手順に従うことができない場合は、プロフェッショナルサポートを受けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18f33-112">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="18f33-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="18f33-113">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18f33-114">この記事では、「rSSD の削除ガイド (エンタープライズ向け)」に記載されている一般的な安全対策と安全性のポリシーと手順について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="18f33-114">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="18f33-115">SSD の削除の準備</span><span class="sxs-lookup"><span data-stu-id="18f33-115">Prepare for SSD removal</span></span> 

### <span data-ttu-id="18f33-116">最新の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="18f33-116">Install the latest updates</span></span> 

<span data-ttu-id="18f33-117">作業を始める前に、使用している Windows のバージョンに最新の更新プログラムがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f33-117">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="18f33-118">[**スタート**  >  ]**設定**  >  の**更新 & セキュリティ**] に移動して、[**更新プログラムの確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="18f33-118">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="18f33-119">利用可能な更新プログラムをすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="18f33-119">Install all available updates.</span></span>
3. <span data-ttu-id="18f33-120">デバイスへのアクセスに必要なパスワードを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f33-120">Verify any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="18f33-121">[BitLocker の管理]</span><span class="sxs-lookup"><span data-stu-id="18f33-121">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="18f33-122">このセクションでは、ハードディスクの BitLocker 暗号化を有効にしている組織向けの推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="18f33-122">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="18f33-123">詳細については、「  [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f33-123">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="18f33-124">SSD の削除中に BitLocker 暗号化が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="18f33-124">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="18f33-125">SSD を削除して交換する前に、デバイスが暗号化されていない場合は、次の手順に従って BitLocker をオフにします。</span><span class="sxs-lookup"><span data-stu-id="18f33-125">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="18f33-126">[ **設定**] で、「 **bitlocker** 」と入力し、[ **bitlocker の管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18f33-126">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="18f33-127">[ **BitLocker をオフにする**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="18f33-127">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="18f33-128">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="18f33-128">Power down the device.</span></span> 

### <span data-ttu-id="18f33-129">SSD の削除および交換中に BitLocker 暗号化が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="18f33-129">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="18f33-130">SSD の削除と交換前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="18f33-130">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="18f33-131">[ **設定**] で、「 **BitLocker**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="18f33-131">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="18f33-132">[ **Bitlocker の管理**] を選び  > **Generate BitLocker Recovery Key**ます。</span><span class="sxs-lookup"><span data-stu-id="18f33-132">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="18f33-133">USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="18f33-133">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="18f33-134">回復キーを USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="18f33-134">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="18f33-135">USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="18f33-135">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="18f33-136">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="18f33-136">Power down the device.</span></span> 

## <span data-ttu-id="18f33-137">SSD を削除して置き換える</span><span class="sxs-lookup"><span data-stu-id="18f33-137">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="18f33-138">「 [Enterprise 用の Rssd の削除ガイド](https://www.microsoft.com/download/100440)」の手順に従って、SSD を削除します。</span><span class="sxs-lookup"><span data-stu-id="18f33-138">Remove the SSD by using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="18f33-139">元の SSD を新しいデバイスに装着し、新しいデバイスを有線インターネット接続に接続します。</span><span class="sxs-lookup"><span data-stu-id="18f33-139">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="18f33-140">新しいデバイスの電源を入れます。</span><span class="sxs-lookup"><span data-stu-id="18f33-140">Power on the new device.</span></span> <span data-ttu-id="18f33-141">デバイスは、起動時にファームウェアの更新プログラムを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="18f33-141">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="18f33-142">SSD の削除と交換後</span><span class="sxs-lookup"><span data-stu-id="18f33-142">After SSD removal and replacement</span></span>

### <span data-ttu-id="18f33-143">暗号化されていない Ssd の管理</span><span class="sxs-lookup"><span data-stu-id="18f33-143">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="18f33-144">転送中に SSD が暗号化されていない場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="18f33-144">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="18f33-145">[**サインインオプション**  >  ] の**パスワード**に移動します (左側に鍵のアイコンが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="18f33-145">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="18f33-146">パスワードを入力し、2段階認証が完了していない状態でサインインします (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="18f33-146">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="18f33-147">完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="18f33-147">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="18f33-148">パスワードを使用してもう一度サインインし、メッセージが表示されたら、Windows Hello と PIN をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="18f33-148">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="18f33-149">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしていて、置換後に bitlocker を有効にする場合は、「 **bitlocker**  >  **管理**bitlocker  >  **Resume bitlocker**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f33-149">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="18f33-150">[Microsoft Surface Diagnostics ツールキット For Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) を実行して、デバイスのすべての機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="18f33-150">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="18f33-151">「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。</span><span class="sxs-lookup"><span data-stu-id="18f33-151">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="18f33-152">エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="18f33-152">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="18f33-153">Office**アプリ**を開いて office アカウントを確認し、[**ファイル**アカウント] に移動して、  >  **Account**エラーメッセージがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f33-153">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="18f33-154">暗号化された SSDs の管理</span><span class="sxs-lookup"><span data-stu-id="18f33-154">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="18f33-155">USB ドライブに保存されている BitLocker 回復キーを読み取るには、2番目のデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="18f33-155">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="18f33-156">転送中に SSD が暗号化されている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="18f33-156">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="18f33-157">BitLocker 回復キーが格納されている USB ドライブを2番目のデバイスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="18f33-157">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="18f33-158">Bitlocker 回復キーが含まれている .txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="18f33-158">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="18f33-159">元の SSD を含む新しいデバイスに BitLocker 回復キーを手動で入力します。</span><span class="sxs-lookup"><span data-stu-id="18f33-159">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="18f33-160">BitLocker 回復キーを正常に入力したら、[**サインインオプション**  >  **]** (左側にあるキーアイコンで表示されます) に移動します。</span><span class="sxs-lookup"><span data-stu-id="18f33-160">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="18f33-161">パスワードを入力してサインインします。2段階認証が完了していません (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="18f33-161">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="18f33-162">完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="18f33-162">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="18f33-163">パスワードを使用してもう一度サインインし、Windows Hello をセットアップして PIN を追加します。</span><span class="sxs-lookup"><span data-stu-id="18f33-163">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="18f33-164">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしている場合、置換後に bitlocker を有効にするには、[**設定**] の [bitlocker の管理] bitlocker  >  **BitLocker**  >  **Manage BitLocker**  >  **Resume bitlocker を選び**ます。</span><span class="sxs-lookup"><span data-stu-id="18f33-164">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="18f33-165">すべてのデバイスの機能を確認するには、 **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** を実行します。</span><span class="sxs-lookup"><span data-stu-id="18f33-165">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="18f33-166">Windows のライセンス認証を確認するには、[**設定**の  >  **アクティブ化**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18f33-166">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="18f33-167">エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="18f33-167">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="18f33-168">Office アカウントの状態を確認するには、 **office アプリ**を開き、[**ファイル**アカウント] に移動して  >  **Account**エラーメッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f33-168">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="18f33-169">詳細情報</span><span class="sxs-lookup"><span data-stu-id="18f33-169">Learn more</span></span>

- [<span data-ttu-id="18f33-170">rSSD のエンタープライズ向けの削除ガイド</span><span class="sxs-lookup"><span data-stu-id="18f33-170">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="18f33-171">BitLocker 回復ガイド</span><span class="sxs-lookup"><span data-stu-id="18f33-171">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="18f33-172">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="18f33-172">Still need help?</span></span> <span data-ttu-id="18f33-173">[Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="18f33-173">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>