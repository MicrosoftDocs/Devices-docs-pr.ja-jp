---
title: 互換性のある Surface デバイスでの SSD の削除
description: この記事では、認定 IT 技術者を対象に、Surface Laptop 3、Surface Pro X、Surface Laptop Go の SSD の取り外しと交換に関する推奨ベスト プラクティスについて説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 01/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 51ef676e7379f0898d6b601bb08c96002c9e6ace
ms.sourcegitcommit: d4e2a29aa21a911ee55642cd66b4337b89eebdd8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "11270632"
---
# <span data-ttu-id="90a45-103">互換性のある Surface デバイスからの SSD 削除のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="90a45-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90a45-104">この記事は、エンタープライズ組織の認定 IT 技術者のみを対象にしています。</span><span class="sxs-lookup"><span data-stu-id="90a45-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="90a45-105">以下の互換性のある Surface デバイスでの SSD の削除と交換に、認定 IT 技術者が使用するための推奨ベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="90a45-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="90a45-106">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="90a45-106">Surface Pro 7+</span></span>
- <span data-ttu-id="90a45-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="90a45-107">Surface Pro X</span></span>
- <span data-ttu-id="90a45-108">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="90a45-108">Surface Laptop Go</span></span>
- <span data-ttu-id="90a45-109">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="90a45-109">Surface Laptop 3</span></span>

> [!WARNING]
> <span data-ttu-id="90a45-110">デバイスを開いてデバイス コンポーネントを交換すると、電気に対する損傷、デバイスの損傷、火災、および個人のけがのリスク、その他の危険が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90a45-110">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="90a45-111">このような作業を行う場合は、常に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="90a45-111">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="90a45-112">「エンタープライズ向け [rSSD](https://www.microsoft.com/download/100440)削除ガイド」に示されている安全上の予防措置と手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="90a45-112">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="90a45-113">「rSSD Removal Guide for Enterprise」で指定されている安全上の予防措置と手順に従できない場合は、プロフェッショナルなサポートを受けてください。</span><span class="sxs-lookup"><span data-stu-id="90a45-113">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="90a45-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="90a45-114">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90a45-115">この記事では、「rSSD Removal Guide for Enterprise」で説明されている一般的な安全対策と安全に関するポリシーと手順を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="90a45-115">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="90a45-116">SSD の削除を準備する</span><span class="sxs-lookup"><span data-stu-id="90a45-116">Prepare for SSD removal</span></span> 

### <span data-ttu-id="90a45-117">最新の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="90a45-117">Install the latest updates</span></span> 

<span data-ttu-id="90a45-118">開始する前に、Windows のバージョンに最新の更新プログラムがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90a45-118">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="90a45-119">[スタート設定**の**  >  **更新とセキュリティ**  >  **] に&し**、[更新**プログラムの確認] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-119">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="90a45-120">利用可能なすべての更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="90a45-120">Install all available updates.</span></span>
3. <span data-ttu-id="90a45-121">デバイスへのアクセスに必要なパスワードを確認します。</span><span class="sxs-lookup"><span data-stu-id="90a45-121">Verify any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="90a45-122">[BitLocker の管理]</span><span class="sxs-lookup"><span data-stu-id="90a45-122">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="90a45-123">このセクションには、ハード ディスクに対して BitLocker 暗号化を有効にしている組織に関する推奨事項が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90a45-123">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="90a45-124">詳しくは  [、BitLocker 回復ガイドに関するページをご覧ください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)。</span><span class="sxs-lookup"><span data-stu-id="90a45-124">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="90a45-125">SSD の削除と交換中に BitLocker 暗号化が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="90a45-125">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="90a45-126">SSD の削除と交換の前にデバイスを暗号化解除できる場合は、次の手順に従って BitLocker をオフにします。</span><span class="sxs-lookup"><span data-stu-id="90a45-126">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="90a45-127">[**設定] に\*\*\*\*「BitLocker」と入力し、[BitLocker**の**管理] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-127">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="90a45-128">**[BitLocker をオフにする] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-128">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="90a45-129">デバイスの電源を落とします。</span><span class="sxs-lookup"><span data-stu-id="90a45-129">Power down the device.</span></span> 

### <span data-ttu-id="90a45-130">SSD の削除と交換中に BitLocker 暗号化が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="90a45-130">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="90a45-131">SSD の削除と交換の前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="90a45-131">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="90a45-132">[**設定] に\*\*\*\*「BitLocker」と入力します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-132">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="90a45-133">**[BitLocker の BitLocker 生成回復**  > **キーの管理] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-133">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="90a45-134">USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="90a45-134">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="90a45-135">回復キーを USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="90a45-135">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="90a45-136">USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="90a45-136">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="90a45-137">デバイスの電源を落とします。</span><span class="sxs-lookup"><span data-stu-id="90a45-137">Power down the device.</span></span> 

## <span data-ttu-id="90a45-138">SSD の取り外しと交換</span><span class="sxs-lookup"><span data-stu-id="90a45-138">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="90a45-139">エンタープライズ向け [rSSD](https://www.microsoft.com/download/100440)削除ガイドに含まれているデバイスに適した手順を使用して、SSD を削除します。</span><span class="sxs-lookup"><span data-stu-id="90a45-139">Remove the SSD by using the appropriate instructions for your device included in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="90a45-140">元の SSD を新しいデバイスに入れ、新しいデバイスをワイヤード (有線) インターネット接続に接続します。</span><span class="sxs-lookup"><span data-stu-id="90a45-140">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="90a45-141">新しいデバイスの電源を入します。</span><span class="sxs-lookup"><span data-stu-id="90a45-141">Power on the new device.</span></span> <span data-ttu-id="90a45-142">デバイスは起動時にファームウェア更新プログラムを通過する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90a45-142">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="90a45-143">SSD の取り外しと交換後</span><span class="sxs-lookup"><span data-stu-id="90a45-143">After SSD removal and replacement</span></span>

### <span data-ttu-id="90a45-144">暗号化されていない SSD を管理する</span><span class="sxs-lookup"><span data-stu-id="90a45-144">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="90a45-145">転送中に SSD が暗号化されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90a45-145">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="90a45-146">サインイン オプション**パスワード**(左側のキー アイコンで  >  \*\*\*\* 表される) に移動します。</span><span class="sxs-lookup"><span data-stu-id="90a45-146">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="90a45-147">パスワードを入力し、2 要素認証の保留中の完了にサインインします (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="90a45-147">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="90a45-148">完全にサインインした後、[アカウントの**サインアウトの**開始]  >  \*\*\*\*  >  **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-148">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="90a45-149">パスワードを使用してサインインし、メッセージが表示されたら Windows Hello と PIN を設定します。</span><span class="sxs-lookup"><span data-stu-id="90a45-149">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="90a45-150">デバイスが SSD の削除と交換を容易にするために BitLocker が無効になっている場合に、置換後に BitLocker を有効にする場合は **、BitLocker**の BitLocker の管理  >  **BitLocker**再開  >  **BitLocker**に移動します。</span><span class="sxs-lookup"><span data-stu-id="90a45-150">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="90a45-151">Microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) を実行して、デバイスの完全な機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="90a45-151">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="90a45-152">[設定のアクティブ化] に移動して、Windows のライセンス**認証を**  >  **確認します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-152">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="90a45-153">エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-153">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="90a45-154">アプリをOfficeして、Office アカウントを確認\*\*\*\* し、[ファイル アカウント] に\*\*\*\* 移動して、エラー メッセージ  >  \*\*\*\* を確認します。</span><span class="sxs-lookup"><span data-stu-id="90a45-154">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="90a45-155">暗号化された SSD の管理</span><span class="sxs-lookup"><span data-stu-id="90a45-155">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="90a45-156">USB ドライブに保存された BitLocker 回復キーを読み取る 2 番目のデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="90a45-156">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="90a45-157">転送中に SSD が暗号化されている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90a45-157">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="90a45-158">BitLocker 回復キーを含む USB ドライブを 2 番目のデバイスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="90a45-158">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="90a45-159">Bitlocker 回復キーを含む .txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="90a45-159">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="90a45-160">元の SSD を含む新しいデバイスで BitLocker 回復キーを手動で入力します。</span><span class="sxs-lookup"><span data-stu-id="90a45-160">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="90a45-161">BitLocker 回復キーを正常に入力したら、[サインイン オプション\*\*\*\* パスワード] (左側のキー アイコンで表されます)  >  \*\*\*\* に移動します。</span><span class="sxs-lookup"><span data-stu-id="90a45-161">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="90a45-162">パスワードを入力してサインインし、2 要素認証の完了を保留します (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="90a45-162">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="90a45-163">完全にサインインした後、[アカウントの**サインアウトの**開始]  >  \*\*\*\*  >  **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-163">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="90a45-164">パスワードを使用してサインインし、Windows Hello をセットアップして PIN を追加します。</span><span class="sxs-lookup"><span data-stu-id="90a45-164">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="90a45-165">デバイスが SSD の削除と交換を容易にするために BitLocker が無効になっている場合、および置換後に BitLocker\*\*\*\* を有効にする場合は、[設定]  >  **BitLocker の [BitLocker**の管理  >  **BitLocker**の再開  >  **BitLocker**の管理] に移動します。</span><span class="sxs-lookup"><span data-stu-id="90a45-165">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="90a45-166">**[SDT を実行して](surface-diagnostic-toolkit-for-business-intro.md)**、デバイスの完全な機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="90a45-166">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="90a45-167">Windows のライセンス認証を確認するには、[設定のアクティブ化 **] を**  >  **選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-167">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="90a45-168">エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="90a45-168">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="90a45-169">Office アカウントの状態を確認するには、Office **App**を開き、[ファイル アカウント] に\*\*\*\* 移動してエラー メッセージ  >  \*\*\*\* を確認します。</span><span class="sxs-lookup"><span data-stu-id="90a45-169">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="90a45-170">詳細情報</span><span class="sxs-lookup"><span data-stu-id="90a45-170">Learn more</span></span>

- [<span data-ttu-id="90a45-171">エンタープライズ向け rSSD 削除ガイド</span><span class="sxs-lookup"><span data-stu-id="90a45-171">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="90a45-172">BitLocker 回復ガイド</span><span class="sxs-lookup"><span data-stu-id="90a45-172">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="90a45-173">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="90a45-173">Still need help?</span></span> <span data-ttu-id="90a45-174">Microsoft コミュニティ [に移動します](https://answers.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="90a45-174">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>