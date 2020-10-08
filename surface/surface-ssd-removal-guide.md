---
title: 互換性のある Surface デバイスでの SSD の削除
description: SSD を1つの Surface デバイスから別の機種に移動する方法を説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 10/7/2020
ms.reviewer: johnk
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 00109e4e1bb3873fc2914b2044f58e6fa3b6c211
ms.sourcegitcommit: d0a5c8fb2b37eb11858c7be4549e55c4b36d7471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2020
ms.locfileid: "11104809"
---
# <span data-ttu-id="00aea-103">互換性のある Surface デバイスからの SSD の削除に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="00aea-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00aea-104">この記事は、組織内で限定された IT 技術者による使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="00aea-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="00aea-105">Surface ノート Pc 3 または Surface Pro X でのみ、お勧めの IT 技術者が Ssd を削除して交換する際に推奨されるベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00aea-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in Surface Laptop 3 or Surface Pro X only.</span></span> 

> [!WARNING]
> <span data-ttu-id="00aea-106">デバイスを開いたり、デバイスコンポーネントを交換したりすると、感電、デバイスの損傷、火災、および個人の傷害のリスク、およびその他の危険を生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00aea-106">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="00aea-107">このようなアクティビティを行うときは、常に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00aea-107">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="00aea-108">[エンタープライズ向けの Rssd の削除ガイド](https://www.microsoft.com/download/100440)に記載されている安全性に関する注意事項と手順に従います。</span><span class="sxs-lookup"><span data-stu-id="00aea-108">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="00aea-109">「Enterprise 向けの rSSD の削除ガイド」で指定されている安全性の予防策と手順に従うことができない場合は、プロフェッショナルサポートを受けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="00aea-109">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="00aea-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="00aea-110">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00aea-111">この記事では、「rSSD の削除ガイド (エンタープライズ向け)」に記載されている一般的な安全対策と安全性のポリシーと手順について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="00aea-111">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="00aea-112">SSD の削除の準備</span><span class="sxs-lookup"><span data-stu-id="00aea-112">Prepare for SSD removal</span></span> 

### <span data-ttu-id="00aea-113">最新の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="00aea-113">Install the latest updates</span></span> 

<span data-ttu-id="00aea-114">作業を開始する前に、使用している Windows のバージョンに最新の更新プログラムが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="00aea-114">Before you begin, make sure that your version of Windows has the latest updates intalled:</span></span>

1.  <span data-ttu-id="00aea-115">[**スタート**  >  ]**設定**  >  の**更新 & セキュリティ**] に移動して、[**更新プログラムの確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="00aea-115">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span> <span data-ttu-id="00aea-116">利用可能な更新プログラムをすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="00aea-116">Install all available updates.</span></span> 
2. <span data-ttu-id="00aea-117">利用可能な更新プログラムをすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="00aea-117">Install all available updates.</span></span>
3. <span data-ttu-id="00aea-118">デバイスへのアクセスに必要なパスワードがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00aea-118">Verify that you have any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="00aea-119">[BitLocker の管理]</span><span class="sxs-lookup"><span data-stu-id="00aea-119">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="00aea-120">このセクションでは、ハードディスクの BitLocker 暗号化を有効にしている組織向けの推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="00aea-120">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="00aea-121">詳細については、「 [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00aea-121">For more information, see the [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="00aea-122">SSD の削除中に BitLocker 暗号化が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="00aea-122">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="00aea-123">SSD を削除して交換する前に、デバイスが暗号化されていない場合は、次の手順に従って BitLocker をオフにします。</span><span class="sxs-lookup"><span data-stu-id="00aea-123">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="00aea-124">[ **設定**] で、「 **bitlocker**」と入力し、[ **bitlocker の管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="00aea-124">In **Settings**, type **Bitlocker**, and then select **Manage Bitlocker**.</span></span> 
2.  <span data-ttu-id="00aea-125">[ **Bitlocker をオフにする**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="00aea-125">Select **Turn Off Bitlocker**.</span></span> 
3.  <span data-ttu-id="00aea-126">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="00aea-126">Power down the device.</span></span> 

### <span data-ttu-id="00aea-127">SSD の削除および交換中に BitLocker 暗号化が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="00aea-127">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="00aea-128">SSD の削除と交換前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="00aea-128">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="00aea-129">[ **設定**] で、「 **Bitlocker**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="00aea-129">In **Settings**, type **Bitlocker**.</span></span>
2. <span data-ttu-id="00aea-130">[ **Bitlocker の管理**] を選び  > **Generate Bitlocker Recovery Key**ます。</span><span class="sxs-lookup"><span data-stu-id="00aea-130">Select **Manage Bitlocker** >**Generate Bitlocker Recovery Key**.</span></span>
2.  <span data-ttu-id="00aea-131">USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="00aea-131">Insert a USB drive.</span></span> 
3.  <span data-ttu-id="00aea-132">回復キーを USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="00aea-132">Save the recovery key to USB storage.</span></span>  
4.  <span data-ttu-id="00aea-133">USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="00aea-133">Remove the USB drive.</span></span>  
5.  <span data-ttu-id="00aea-134">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="00aea-134">Power down the device.</span></span> 

## <span data-ttu-id="00aea-135">SSD を削除して置き換える</span><span class="sxs-lookup"><span data-stu-id="00aea-135">Remove and replace the SSD</span></span> 

1.  <span data-ttu-id="00aea-136">「 [Enterprise 用の Rssd の削除ガイド](https://www.microsoft.com/download/100440)」の手順に従って、SSD を削除します。</span><span class="sxs-lookup"><span data-stu-id="00aea-136">Remove the SSD by using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2. <span data-ttu-id="00aea-137">元の SSD を新しいデバイスに取り付け、新しいデバイスを有線インターネット接続に接続します。</span><span class="sxs-lookup"><span data-stu-id="00aea-137">Put the original SSD into a new device, and connect the new device to a wired internet connection.</span></span>
2.  <span data-ttu-id="00aea-138">新しいデバイスの電源を入れます。</span><span class="sxs-lookup"><span data-stu-id="00aea-138">Power on the new device.</span></span> <span data-ttu-id="00aea-139">デバイスは、起動時にファームウェアの更新プログラムを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="00aea-139">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="00aea-140">SSD の削除と交換後</span><span class="sxs-lookup"><span data-stu-id="00aea-140">After SSD removal and replacement</span></span>

### <span data-ttu-id="00aea-141">暗号化されていない Ssd の管理</span><span class="sxs-lookup"><span data-stu-id="00aea-141">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="00aea-142">転送中に SSD が暗号化されていない場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="00aea-142">If the SSD remains unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="00aea-143">[**サインインオプション**  >  ] の**パスワード**に移動します (左側に鍵のアイコンが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="00aea-143">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="00aea-144">パスワードを入力し、2段階認証が完了していない状態でサインインします (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="00aea-144">Enter the password, and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="00aea-145">完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="00aea-145">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="00aea-146">パスワードを使用してもう一度サインインし、メッセージが表示されたら、Windows Hello と PIN をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="00aea-146">Sign back in by using the password, and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="00aea-147">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしていて、置換後に bitlocker を有効にする場合は、「 **bitlocker**  >  **管理**bitlocker  >  **Resume bitlocker**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00aea-147">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
6.  <span data-ttu-id="00aea-148">Microsoft Surface Diagnostics ツールキット for Business (SDT) を実行して、デバイスのすべての機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="00aea-148">Run the Microsoft Surface Diagnostic Toolkit for Business (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="00aea-149">「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。</span><span class="sxs-lookup"><span data-stu-id="00aea-149">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="00aea-150">エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="00aea-150">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="00aea-151">Office**アプリ**を開いて office アカウントを確認し、[**ファイル**アカウント] に移動して、  >  **Account**エラーメッセージがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00aea-151">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="00aea-152">暗号化された SSDs の管理</span><span class="sxs-lookup"><span data-stu-id="00aea-152">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="00aea-153">USB ドライブに保存されている BitLocker 回復キーを読み取るには、2番目のデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="00aea-153">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="00aea-154">転送中に SSD が暗号化されたままになっている場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="00aea-154">If the SSD remained encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="00aea-155">Bitlocker 回復キーが格納されている USB ドライブを2番目のデバイスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="00aea-155">Insert the USB drive that contains the Bitlocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="00aea-156">Bitlocker 回復キーが含まれている .txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="00aea-156">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="00aea-157">元の SSD を含む新しいデバイスに Bitlocker 回復キーを手動で入力します。</span><span class="sxs-lookup"><span data-stu-id="00aea-157">Manually enter the Bitlocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="00aea-158">BitLocker 回復キーを正常に入力したら、[**サインインオプション**  >  **]** (左側にあるキーアイコンで表示されます) に移動します。</span><span class="sxs-lookup"><span data-stu-id="00aea-158">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="00aea-159">パスワードを入力してサインインします。2段階認証が完了していません (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="00aea-159">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="00aea-160">完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="00aea-160">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="00aea-161">パスワードを使用してもう一度サインインし、Windows Hello をセットアップして PIN を追加します。</span><span class="sxs-lookup"><span data-stu-id="00aea-161">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="00aea-162">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしている場合、置換後に bitlocker を有効にするには、[**設定**] の [bitlocker の管理] bitlocker  >  **Bitlocker**  >  **Manage Bitlocker**  >  **Resume bitlocker を選び**ます。</span><span class="sxs-lookup"><span data-stu-id="00aea-162">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
9.  <span data-ttu-id="00aea-163">すべてのデバイスの機能を確認するには、 **SDT** を実行します。</span><span class="sxs-lookup"><span data-stu-id="00aea-163">Run **SDT** to verify full device functionality.</span></span>  
10. <span data-ttu-id="00aea-164">「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。</span><span class="sxs-lookup"><span data-stu-id="00aea-164">Check Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="00aea-165">エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="00aea-165">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="00aea-166">Office アカウントの状態を確認するには、 **office アプリ**を開き、[**ファイル**アカウント] に移動して  >  **Account**エラーメッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="00aea-166">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="00aea-167">詳細情報</span><span class="sxs-lookup"><span data-stu-id="00aea-167">More information</span></span> 

<span data-ttu-id="00aea-168">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00aea-168">For more information, see the following articles:</span></span>

- [<span data-ttu-id="00aea-169">rSSD のエンタープライズ向けの削除ガイド</span><span class="sxs-lookup"><span data-stu-id="00aea-169">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="00aea-170">BitLocker 回復ガイド</span><span class="sxs-lookup"><span data-stu-id="00aea-170">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="00aea-171">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="00aea-171">Still need help?</span></span> <span data-ttu-id="00aea-172">[Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="00aea-172">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>