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
ms.date: 8/7/2020
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
ms.openlocfilehash: 9cde08c8106703b50218bf7f5ed60e3d7fea0b67
ms.sourcegitcommit: 83530906c7e34c92bbee90b723321acd61e77669
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2020
ms.locfileid: "10918960"
---
# <span data-ttu-id="7d43d-103">互換性のある Surface デバイスでの SSD の削除に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="7d43d-103">Best practices for SSD removal in compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d43d-104">この記事は、組織内で限定された IT 技術者による使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="7d43d-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="7d43d-105">この資料では、固定された IT 技術者が、着脱可能な Ssd を使って Surface デバイスで SSDs を削除して置き換える場合に推奨されるベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-105">It describes the recommended best practices for use by qualified IT technicians when removing and replacing SSDs in Surface devices with removable SSDs.</span></span> 

> [!WARNING]
> <span data-ttu-id="7d43d-106">デバイスを開いたり、デバイスコンポーネントを交換したりすると、感電、デバイスの損傷、火災、および個人の傷害のリスク、およびその他の危険を生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d43d-106">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="7d43d-107">このようなアクティビティを行うときは、常に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d43d-107">Always use caution when undertaking such activities.</span></span> <span data-ttu-id="7d43d-108">「エンタープライズ向けの rSSD の削除ガイド」で説明されている安全性に関する注意事項と手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7d43d-108">Follow the safety precautions and procedures identified in the rSSD Removal Guide for Enterprise.</span></span> <span data-ttu-id="7d43d-109">エンタープライズ向けの rSSD の削除ガイドで指定されている安全性に関する注意事項と手順に従うことができない場合は、プロフェッショナルサポートを受けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7d43d-109">Microsoft recommends that you seek professional assistance if you are unable to follow the safety precautions and procedures specified in the rSSD Removal Guide for Enterprise.</span></span> 

## <span data-ttu-id="7d43d-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="7d43d-110">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d43d-111">この記事では、 [Enterprise 用の Rssd の削除ガイド](https://www.microsoft.com/download/100440)で説明されている一般的な安全性に関する注意事項と安全性のポリシーと手順を理解していることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="7d43d-111">This article assumes you understand the General Safety Precautions and Safety policies and procedures described in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span>

## <span data-ttu-id="7d43d-112">SSD の削除の準備</span><span class="sxs-lookup"><span data-stu-id="7d43d-112">Prepare for SSD removal</span></span> 

### <span data-ttu-id="7d43d-113">最新の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="7d43d-113">Install the latest updates</span></span> 

<span data-ttu-id="7d43d-114">作業を始める前に、使用している Windows のバージョンに最新の更新プログラムが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-114">Before you begin, make sure your version of Windows has the latest updates.</span></span>

1.  <span data-ttu-id="7d43d-115">[**スタート**  >  ]**設定**  >  の**更新 & セキュリティ**] に移動して、[**更新プログラムの確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-115">Go to **Start** > **Settings** > **Update & Security** and select **Check for updates**.</span></span> <span data-ttu-id="7d43d-116">利用可能な更新プログラムをすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="7d43d-116">Install all available updates.</span></span>  

2.  <span data-ttu-id="7d43d-117">デバイスへのアクセスに必要なパスワードがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-117">Confirm that you have any passwords needed to access the device.</span></span>  
 
## <span data-ttu-id="7d43d-118">Bitlocker を管理する</span><span class="sxs-lookup"><span data-stu-id="7d43d-118">Manage Bitlocker</span></span> 

> [!NOTE]
> <span data-ttu-id="7d43d-119">このセクションでは、ハードドライブの BitLocker 暗号化を有効にしている組織向けの推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-119">This section includes recommendations for organizations that have enabled BitLocker encryption for hard drives.</span></span> <span data-ttu-id="7d43d-120">詳細については、「 [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d43d-120">For more information, see the [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="7d43d-121">SSD の削除中に BitLocker 暗号化が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="7d43d-121">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="7d43d-122">SSD を削除して交換する前に、デバイスが暗号化されていない場合は、次の手順に従って BitLocker をオフにします。</span><span class="sxs-lookup"><span data-stu-id="7d43d-122">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="7d43d-123">[**設定**] で、「 **bitlocker** 」と入力し、[ **bitlocker の管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-123">In **Settings**, type **Bitlocker** and select **Manage Bitlocker**.</span></span> 
2.  <span data-ttu-id="7d43d-124">[ **Bitlocker をオフにする**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-124">Select **Turn Off Bitlocker**.</span></span> 
3.  <span data-ttu-id="7d43d-125">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="7d43d-125">Power down the device.</span></span> 

### <span data-ttu-id="7d43d-126">SSD の削除および交換中に BitLocker 暗号化が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="7d43d-126">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="7d43d-127">SSD の削除と交換前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-127">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="7d43d-128">[**設定**] に移動し、「 **Bitlocker**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-128">Go to **Settings** and type **Bitlocker**.</span></span>
2. <span data-ttu-id="7d43d-129">[ **Bitlocker の管理**] を選び  > **Generate Bitlocker Recovery Key**ます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-129">Select **Manage Bitlocker** >**Generate Bitlocker Recovery Key**.</span></span>
2.  <span data-ttu-id="7d43d-130">USB ドライブを挿入します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-130">Insert a USB drive.</span></span> 
3.  <span data-ttu-id="7d43d-131">回復キーを USB ストレージに保存します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-131">Save the recovery key to USB storage.</span></span>  
4.  <span data-ttu-id="7d43d-132">USB ドライブを取り外します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-132">Remove the USB drive.</span></span>  
5.  <span data-ttu-id="7d43d-133">デバイスの電源を切ります。</span><span class="sxs-lookup"><span data-stu-id="7d43d-133">Power down the device.</span></span> 

## <span data-ttu-id="7d43d-134">SSD を削除して置き換える</span><span class="sxs-lookup"><span data-stu-id="7d43d-134">Remove and replace the SSD</span></span> 

1.  <span data-ttu-id="7d43d-135">「 [Enterprise 用の Rssd の削除ガイド](https://www.microsoft.com/download/100440)」の手順に従って SSD を削除します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-135">Remove the SSD using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2. <span data-ttu-id="7d43d-136">新しいデバイスに元の SSD を配置し、新しいデバイスを有線インターネット接続に接続します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-136">Place the original SSD in a new device and connect the new device to a wired internet connection.</span></span>
2.  <span data-ttu-id="7d43d-137">新しいデバイスの電源を入れます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-137">Power on the new device.</span></span> <span data-ttu-id="7d43d-138">デバイスは、起動時にファームウェアの更新プログラムを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="7d43d-138">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="7d43d-139">SSD の削除と交換後</span><span class="sxs-lookup"><span data-stu-id="7d43d-139">After SSD removal and replacement</span></span>

### <span data-ttu-id="7d43d-140">暗号化されていない Ssd の管理</span><span class="sxs-lookup"><span data-stu-id="7d43d-140">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="7d43d-141">転写中に SSD が暗号化されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-141">If the SSD remains unencrypted during the transfer, complete the following:</span></span> 

1.  <span data-ttu-id="7d43d-142">[**サインインオプション**  >  ] の**パスワード**に移動します (左側に鍵のアイコンとして表示されます)。</span><span class="sxs-lookup"><span data-stu-id="7d43d-142">Go to **Sign-In Options** > **Password** (represented as the key icon on the left side).</span></span>  
2.  <span data-ttu-id="7d43d-143">パスワードを入力し、2段階認証が完了していない状態でサインインします (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="7d43d-143">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="7d43d-144">サインインが完了したら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-144">Once fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="7d43d-145">パスワードを使用してもう一度サインインし、メッセージが表示されたら Windows Hello と PIN をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="7d43d-145">Sign back in with the password and set up Windows Hello and a PIN when prompted.</span></span> 
    - <span data-ttu-id="7d43d-146">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしていて、置換後に bitlocker を有効にする場合は、「 **bitlocker**  >  **管理**bitlocker  >  **Resume bitlocker**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d43d-146">If the device was BitLocker-disabled to facilitate SSD removal and replacement and you want to enable BitLocker after the replacement, go to **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
6.  <span data-ttu-id="7d43d-147">すべてのデバイスの機能を確認するには、 **SDT**を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-147">Run **SDT** to confirm full device functionality.</span></span>  
7.  <span data-ttu-id="7d43d-148">「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-148">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="7d43d-149">エラーメッセージが表示される場合は、[**トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-149">If there are any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="7d43d-150">Office**アプリ**を開いて office アカウントを確認し、[**ファイル**アカウント] に移動して、  >  **Account**エラーメッセージがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-150">Check the Office account by opening the **Office App**, then navigate to **File** > **Account** and check for any error messages.</span></span>  

### <span data-ttu-id="7d43d-151">暗号化された SSDs の管理</span><span class="sxs-lookup"><span data-stu-id="7d43d-151">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="7d43d-152">USB ドライブに保存されている BitLocker 回復キーを読み取るには、2番目のデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="7d43d-152">You will need a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="7d43d-153">転送中に SSD が暗号化されたままになっている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-153">If the SSD remained encrypted during the transfer, complete the following:</span></span>

1.  <span data-ttu-id="7d43d-154">Bitlocker 回復キーが保存されている USB ドライブを2番目のデバイスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-154">Insert the USB drive containing the Bitlocker Recovery key into the second device.</span></span> 
2.  <span data-ttu-id="7d43d-155">Bitlocker 回復キーが含まれている .txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-155">Open the .txt file containing the Bitlocker Recovery key.</span></span> 
3.  <span data-ttu-id="7d43d-156">元の SSD を含む新しいデバイスに Bitlocker 回復キーを手動で入力します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-156">Manually enter the Bitlocker Recovery key into the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="7d43d-157">BitLocker 回復キーを正常に入力したら、[**サインインオプション**  >  **]** (左側にあるキーアイコンで表示されます) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-157">After you have successfully entered the BitLocker Recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="7d43d-158">パスワードを入力してサインインします。2段階認証が完了していません (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="7d43d-158">Enter the password and sign in, pending completion of two-factor authentication (if applicable)</span></span> 
6.  <span data-ttu-id="7d43d-159">サインインが完了したら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-159">Once fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="7d43d-160">パスワードを使用してもう一度サインインし、Windows Hello をセットアップして PIN を追加します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-160">Sign back in with the password and set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="7d43d-161">デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしている場合に、置換後に bitlocker を有効にするには、[**設定**] に移動して、bitlocker の再開 bitlocker を  >  **Bitlocker**  >  **管理**し  >  **Resume Bitlocker**ます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-161">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to to **Settings** > **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
9.  <span data-ttu-id="7d43d-162">すべてのデバイスの機能を確認するには、 **SDT**を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-162">Run **SDT** to confirm full device functionality.</span></span>  
10. <span data-ttu-id="7d43d-163">「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-163">Check Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="7d43d-164">エラーメッセージが表示される場合は、[**トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="7d43d-164">If there are any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="7d43d-165">Office アカウントを確認するには、 **office アプリ**を開き、[**ファイル**アカウント] に移動して、エラーメッセージがないか  >  **Account**確認します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-165">To check the Office Account, open the **Office App**, then go to **File** > **Account** and check for any error messages.</span></span>

## <span data-ttu-id="7d43d-166">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7d43d-166">More information</span></span> 

<span data-ttu-id="7d43d-167">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d43d-167">For more information, see the following articles:</span></span>

- [<span data-ttu-id="7d43d-168">rSSD のエンタープライズ向けの削除ガイド</span><span class="sxs-lookup"><span data-stu-id="7d43d-168">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="7d43d-169">BitLocker 回復ガイド</span><span class="sxs-lookup"><span data-stu-id="7d43d-169">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="7d43d-170">問題が解決しない場合は、</span><span class="sxs-lookup"><span data-stu-id="7d43d-170">Still need help?</span></span> <span data-ttu-id="7d43d-171">[Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d43d-171">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>