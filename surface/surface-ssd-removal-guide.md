---
title: 互換性のある Surface デバイスでの SSD の削除
description: この記事では、認定された IT 技術者を対象に、Surface Laptop 4、Surface Laptop 3、Surface Pro 7+、Surface Pro X、および Surface Laptop Go の SSD の削除と交換に関する推奨ベスト プラクティスについて説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: brrecord
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
- Surface Laptop 4
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 7ba66981c021f1f0a08ebf33aab0a73481111a4d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576907"
---
# <a name="best-practices-for-ssd-removal-from-compatible-surface-devices"></a><span data-ttu-id="b9227-103">互換性のある Surface デバイスからの SSD 削除のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="b9227-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9227-104">この記事は、エンタープライズ組織でのみ、資格のある IT 技術者による使用を目的とします。</span><span class="sxs-lookup"><span data-stu-id="b9227-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="b9227-105">次の互換性のある Surface デバイスの SSD の削除と置き換えで、資格のある IT 技術者が使用する推奨されるベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9227-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="b9227-106">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="b9227-106">Surface Pro 7+</span></span>
- <span data-ttu-id="b9227-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="b9227-107">Surface Pro X</span></span>
- <span data-ttu-id="b9227-108">Surface LaptopGo</span><span class="sxs-lookup"><span data-stu-id="b9227-108">Surface Laptop Go</span></span>
- <span data-ttu-id="b9227-109">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="b9227-109">Surface Laptop 3</span></span>
- <span data-ttu-id="b9227-110">Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="b9227-110">Surface Laptop 4</span></span>

> [!WARNING]
> <span data-ttu-id="b9227-111">デバイスを開き、デバイス コンポーネントを交換すると、感電、デバイスの損傷、火災、および人的傷害のリスク、その他の危険が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9227-111">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="b9227-112">そのような活動を行う場合は、常に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9227-112">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="b9227-113">[rSSD](https://www.microsoft.com/download/100440)の削除ガイドで示されている安全上の注意事項と手順に従Enterprise。</span><span class="sxs-lookup"><span data-stu-id="b9227-113">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="b9227-114">「rSSD 削除ガイド for Enterprise」で指定されている安全上の注意事項と手順に従えなき場合は、専門的なサポートを受Enterprise。</span><span class="sxs-lookup"><span data-stu-id="b9227-114">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b9227-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="b9227-115">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9227-116">この記事では、「rSSD 削除ガイド for Enterprise」に記載されている一般的な安全に関する注意事項と安全に関するポリシーと手順について理解Enterprise。</span><span class="sxs-lookup"><span data-stu-id="b9227-116">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <a name="prepare-for-ssd-removal"></a><span data-ttu-id="b9227-117">SSD の削除の準備</span><span class="sxs-lookup"><span data-stu-id="b9227-117">Prepare for SSD removal</span></span> 

### <a name="install-the-latest-updates"></a><span data-ttu-id="b9227-118">最新の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="b9227-118">Install the latest updates</span></span> 

<span data-ttu-id="b9227-119">開始する前に、最新の更新プログラムがインストールWindowsバージョンがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b9227-119">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="b9227-120">[セキュリティの**更新設定**  >  \*\*\*\*  >  **開始&に移動**し、[更新プログラムの確認 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-120">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="b9227-121">利用可能なすべての更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b9227-121">Install all available updates.</span></span>
3. <span data-ttu-id="b9227-122">デバイスにアクセスするために必要なパスワードを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9227-122">Verify any passwords that are necessary to access the device.</span></span>  
 
## <a name="manage-bitlocker"></a><span data-ttu-id="b9227-123">[BitLocker の管理]</span><span class="sxs-lookup"><span data-stu-id="b9227-123">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="b9227-124">このセクションには、ハード ディスクの暗号化を有効にしたBitLocker推奨事項が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9227-124">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="b9227-125">詳細については、「回復ガイド[」をBitLockerしてください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)。</span><span class="sxs-lookup"><span data-stu-id="b9227-125">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <a name="if-bitlocker-encryption-is-disabled-during-ssd-removal-and-replacement"></a><span data-ttu-id="b9227-126">SSD のBitLocker交換中に暗号化が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="b9227-126">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="b9227-127">SSD の削除と交換の前にデバイスを暗号化解除できる場合は、次の手順に従ってデバイスをオフBitLocker。</span><span class="sxs-lookup"><span data-stu-id="b9227-127">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="b9227-128">**[設定]** に「BitLocker」**と入力し、[\*\*\*\*管理]** をBitLocker。</span><span class="sxs-lookup"><span data-stu-id="b9227-128">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="b9227-129">[**電源を切る] をBitLocker**します。</span><span class="sxs-lookup"><span data-stu-id="b9227-129">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="b9227-130">デバイスの電源をオフにします。</span><span class="sxs-lookup"><span data-stu-id="b9227-130">Power down the device.</span></span> 

### <a name="if-bitlocker-encryption-is-enabled-during-ssd-removal-and-replacement"></a><span data-ttu-id="b9227-131">SSD のBitLocker交換中に暗号化が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="b9227-131">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="b9227-132">SSD の削除と交換の前にデバイスが暗号化されている場合は、次の手順に従って、回復キー BitLockerを生成し、USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="b9227-132">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="b9227-133">**[設定]** に「BitLocker」**と入力します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-133">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="b9227-134">[回復**キーのBitLocker**  > **をBitLockerする] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-134">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="b9227-135">USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="b9227-135">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="b9227-136">回復キーを USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="b9227-136">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="b9227-137">USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="b9227-137">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="b9227-138">デバイスの電源をオフにします。</span><span class="sxs-lookup"><span data-stu-id="b9227-138">Power down the device.</span></span> 

## <a name="remove-and-replace-ssd"></a><span data-ttu-id="b9227-139">SSD を削除して置き換える</span><span class="sxs-lookup"><span data-stu-id="b9227-139">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="b9227-140">[rSSD](https://www.microsoft.com/download/100440)の削除ガイドに含まれているデバイスの適切な手順を使用して SSD を削除Enterprise。</span><span class="sxs-lookup"><span data-stu-id="b9227-140">Remove the SSD by using the appropriate instructions for your device included in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="b9227-141">元の SSD を新しいデバイスに入れ、新しいデバイスを有線インターネット接続に接続します。</span><span class="sxs-lookup"><span data-stu-id="b9227-141">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="b9227-142">新しいデバイスの電源をオンにします。</span><span class="sxs-lookup"><span data-stu-id="b9227-142">Power on the new device.</span></span> <span data-ttu-id="b9227-143">デバイスは、起動時にファームウェア更新プログラムを通過する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9227-143">The device may go through a firmware update during startup.</span></span>  
 
## <a name="after-ssd-removal-and-replacement"></a><span data-ttu-id="b9227-144">SSD の削除と交換の後</span><span class="sxs-lookup"><span data-stu-id="b9227-144">After SSD removal and replacement</span></span>

### <a name="manage-unencrypted-ssds"></a><span data-ttu-id="b9227-145">暗号化されていない SSD の管理</span><span class="sxs-lookup"><span data-stu-id="b9227-145">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="b9227-146">転送中に SSD が暗号化されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9227-146">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="b9227-147">[サインイン**オプション パスワード]**  >  \*\*\*\* (左側のキー アイコンで表される) に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9227-147">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="b9227-148">パスワードを入力し、2 要素認証の保留中の完了 (該当する場合) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="b9227-148">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="b9227-149">完全にサインインした後、[アカウントサインアウトの\*\*\*\* 開始  >  **]**  >  **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-149">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="b9227-150">パスワードを使用してサインインし、メッセージが表示されたら、hello Windows PIN を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9227-150">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="b9227-151">デバイスが SSD のBitLockerと交換を容易にするために無効にされ、交換後に BitLocker を有効にする場合は、「BitLocker Manage \*\*\*\*  >  **BitLocker**Resume BitLocker」に  >  **移動**します。</span><span class="sxs-lookup"><span data-stu-id="b9227-151">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="b9227-152">Microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) を実行して、デバイスの完全な機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="b9227-152">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="b9227-153">[ライセンス認証Windowsに移動して、ライセンス認証**を設定**  >  **します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-153">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="b9227-154">エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-154">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="b9227-155">アプリをOfficeして、Officeアカウントに移動し\*\*\*\*、エラー メッセージ\*\*\*\*  >  \*\*\*\* を確認します。</span><span class="sxs-lookup"><span data-stu-id="b9227-155">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <a name="managing-encrypted-ssds"></a><span data-ttu-id="b9227-156">暗号化された SSD の管理</span><span class="sxs-lookup"><span data-stu-id="b9227-156">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="b9227-157">USB ドライブに保存された回復キーを読み取BitLockerデバイスが 2 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="b9227-157">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="b9227-158">転送中に SSD が暗号化されている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9227-158">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="b9227-159">回復キーを含む USB ドライブBitLocker 2 番目のデバイスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="b9227-159">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="b9227-160">Bitlocker 回復.txtを含むファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9227-160">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="b9227-161">元の SSD をBitLocker新しいデバイスの回復キーを手動で入力します。</span><span class="sxs-lookup"><span data-stu-id="b9227-161">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="b9227-162">BitLocker回復キーを正常に入力したら、[サインイン オプション パスワード] (\*\*\*\* 左側のキー アイコンで表される)  >  \*\*\*\* に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9227-162">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="b9227-163">パスワードを入力してサインインし、2 要素認証の完了を保留します (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="b9227-163">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="b9227-164">完全にサインインした後、[アカウントサインアウトの\*\*\*\* 開始  >  **]**  >  **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-164">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="b9227-165">パスワードを使用してサインインし、Hello Windowsを設定し、PIN を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9227-165">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="b9227-166">SSD の取りBitLocker交換を容易にするためにデバイスがBitLocker無効になっている場合、および交換後に BitLocker を有効にする場合は、設定\*\*\*\* BitLocker  >  \*\*\*\*  >  **管理**  >  \*\*\*\* BitLocker Resume BitLocker に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9227-166">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="b9227-167">**[SDT を実行して](surface-diagnostic-toolkit-for-business-intro.md)**、デバイスの完全な機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="b9227-167">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="b9227-168">ライセンス認証をWindowsするには、[ライセンス認証]**設定**  >  **選択します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-168">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="b9227-169">エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="b9227-169">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="b9227-170">Office アカウントの状態を確認するには、Office App を\*\*\*\* 開き、[ファイル アカウント]\*\*\*\* に移動してエラー メッセージ  >  \*\*\*\* を確認します。</span><span class="sxs-lookup"><span data-stu-id="b9227-170">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <a name="learn-more"></a><span data-ttu-id="b9227-171">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b9227-171">Learn more</span></span>

- [<span data-ttu-id="b9227-172">rSSD 削除ガイド for Enterprise</span><span class="sxs-lookup"><span data-stu-id="b9227-172">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="b9227-173">BitLocker 回復ガイド</span><span class="sxs-lookup"><span data-stu-id="b9227-173">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="b9227-174">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="b9227-174">Still need help?</span></span> <span data-ttu-id="b9227-175">[Microsoft Community][に移動します](https://answers.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="b9227-175">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>