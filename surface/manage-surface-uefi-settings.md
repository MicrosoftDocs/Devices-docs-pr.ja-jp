---
title: Surface UEFI の設定の管理
description: デバイスまたはコンポーネントの有効化または無効化、セキュリティ設定の構成、Surface デバイスのブート設定の調整を行うには、Surface UEFI の設定を使用します。
keywords: ファームウェア, セキュリティ, 機能, 設定, ハードウェア, firmware, security, features, configure, hardware
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: devices, surface
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.date: 10/12/2020
ms.openlocfilehash: 218f98b23adcb7bae2af92655d85144c6e5665e6
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114725"
---
# <span data-ttu-id="e1a13-104">Surface UEFI の設定を管理する</span><span class="sxs-lookup"><span data-stu-id="e1a13-104">Manage Surface UEFI settings</span></span>

<span data-ttu-id="e1a13-105">Surface デバイスの現在および将来のすべての世代では、これらのデバイス専用の統合された固有の拡張ファームウェアインターフェイス (UEFI) が Microsoft によって設計されています。</span><span class="sxs-lookup"><span data-stu-id="e1a13-105">All current and future generations of Surface devices use a unique Unified Extensible Firmware Interface (UEFI) engineered by Microsoft specifically for these devices.</span></span> <span data-ttu-id="e1a13-106">Surface UEFI の設定では、組み込みのデバイスとコンポーネントを有効または無効にしたり、UEFI 設定を変更できないように保護したり、Surface device のブート設定を調整したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-106">Surface UEFI settings provide the ability to enable or disable built-in devices and components, protect UEFI settings from being changed, and adjust the Surface device boot settings.</span></span> 

## <span data-ttu-id="e1a13-107">サポートされる製品</span><span class="sxs-lookup"><span data-stu-id="e1a13-107">Supported products</span></span>

<span data-ttu-id="e1a13-108">UEFI 管理は、次のようにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e1a13-108">UEFI management is supported on the following:</span></span> 

- <span data-ttu-id="e1a13-109">Surface Pro 4、Surface Pro (5 番目のジェネレーション)、surface Pro 6、Surface pro 7、surface Pro X</span><span class="sxs-lookup"><span data-stu-id="e1a13-109">Surface Pro 4, Surface Pro (5th Gen), Surface Pro 6, Surface Pro 7, Surface Pro X</span></span>
- <span data-ttu-id="e1a13-110">Surface ラップトップ (1 つ目のジェネレーション)、Surface ノート Pc 2、surface ノート pc 3、surface ラップトップの移動</span><span class="sxs-lookup"><span data-stu-id="e1a13-110">Surface Laptop (1st Gen), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go</span></span>
- <span data-ttu-id="e1a13-111">Surface Studio (第1世代)、Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="e1a13-111">Surface Studio (1st Gen), Surface Studio 2</span></span>
- <span data-ttu-id="e1a13-112">Surface book、Surface Book 2、Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="e1a13-112">Surface Book, Surface Book 2, Surface Book 3</span></span>
- <span data-ttu-id="e1a13-113">Surface Go、Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="e1a13-113">Surface Go, Surface Go 2</span></span>

## <span data-ttu-id="e1a13-114">クラウドベースの管理のサポート</span><span class="sxs-lookup"><span data-stu-id="e1a13-114">Support for cloud-based management</span></span>

<span data-ttu-id="e1a13-115">Microsoft Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると (パブリックプレビューで利用できるようになりました)、Surface UEFI 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-115">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="e1a13-116">DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-116">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="e1a13-117">DFCI は、現在 Surface Pro 7、Surface Pro X、Surface Pc 3 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-117">DFCI is currently available for Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="e1a13-118">詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1a13-118">For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="e1a13-119">Surface UEFI を開くメニュー</span><span class="sxs-lookup"><span data-stu-id="e1a13-119">Open Surface UEFI menu</span></span>

<span data-ttu-id="e1a13-120">システムの起動時に UEFI 設定を調整するには:</span><span class="sxs-lookup"><span data-stu-id="e1a13-120">To adjust UEFI settings during system startup:</span></span>

1. <span data-ttu-id="e1a13-121">Surface をシャットダウンして、約10秒待ってから、停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e1a13-121">Shut down your Surface and wait about 10 seconds to make sure it's off.</span></span>
2. <span data-ttu-id="e1a13-122">**音量を上げる**ボタンを押したままにして、電源ボタンを押しながら離し**ます。**</span><span class="sxs-lookup"><span data-stu-id="e1a13-122">Press and hold the **Volume-up** button  and - at the same time - press and release the **Power button.**</span></span>
3. <span data-ttu-id="e1a13-123">Microsoft または Surface のロゴが画面に表示されたら、[UEFI] 画面が表示されるまで **音量を上げ** たままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-123">As the Microsoft or Surface logo appears on your screen, continue to hold the **Volume-up** button until the UEFI screen appears.</span></span>

## <span data-ttu-id="e1a13-124">UEFI PC 情報ページ</span><span class="sxs-lookup"><span data-stu-id="e1a13-124">UEFI PC information page</span></span>

<span data-ttu-id="e1a13-125">[PC 情報] ページには、Surface デバイスに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-125">The PC information page includes detailed information about your Surface device:</span></span> 

- <span data-ttu-id="e1a13-126">**モデル** – surface device のモデルがここに表示されます (surface Book 2 または surface Pro 7 など)。</span><span class="sxs-lookup"><span data-stu-id="e1a13-126">**Model** – Your Surface device’s model will be displayed here, such as Surface Book 2 or Surface Pro 7.</span></span> <span data-ttu-id="e1a13-127">デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。</span><span class="sxs-lookup"><span data-stu-id="e1a13-127">The exact configuration of your device is not shown, (such as processor, disk size, or memory size).</span></span> 
- <span data-ttu-id="e1a13-128">**UUID** – このユニバーサル固有識別子の番号はデバイスに固有であり、展開または管理の際にデバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-128">**UUID** – This Universally Unique Identification number is specific to your device and is used to identify the device during deployment or management.</span></span> 

- <span data-ttu-id="e1a13-129">**Serial Number** (シリアル番号) – この番号は、アセットのタグ付けやサポートでこの特定の Surface デバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-129">**Serial Number** – This number is used to identify this specific Surface device for asset tagging and support scenarios.</span></span>
- <span data-ttu-id="e1a13-130">**Asset Tag** (アセット タグ) – アセット タグは、[アセット タグ ツール](https://docs.microsoft.com/surface/assettag)で Surface デバイスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-130">**Asset Tag** – The asset tag is assigned to the Surface device with the [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span></span> 

<span data-ttu-id="e1a13-131">Surface デバイスのファームウェアに関する詳細情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-131">You will also find detailed information about the firmware of your Surface device.</span></span> <span data-ttu-id="e1a13-132">Surface デバイスには複数の内部コンポーネントがあり、それぞれが異なるバージョンのファームウェアを実行しています。</span><span class="sxs-lookup"><span data-stu-id="e1a13-132">Surface devices have several internal components that each run different versions of firmware.</span></span> <span data-ttu-id="e1a13-133">次の各デバイスのファームウェア バージョンが、**[PC information]** (PC の情報) ページに表示されます (図 1 を参照)。</span><span class="sxs-lookup"><span data-stu-id="e1a13-133">The firmware version of each of the following devices is displayed on the **PC information** page (as shown in Figure 1):</span></span> 

- <span data-ttu-id="e1a13-134">System UEFI (システム UEFI)</span><span class="sxs-lookup"><span data-stu-id="e1a13-134">System UEFI</span></span> 

- <span data-ttu-id="e1a13-135">SAM Controller (SAM コントローラー)</span><span class="sxs-lookup"><span data-stu-id="e1a13-135">SAM Controller</span></span> 

- <span data-ttu-id="e1a13-136">Intel Management Engine (Intel 管理エンジン)</span><span class="sxs-lookup"><span data-stu-id="e1a13-136">Intel Management Engine</span></span> 

- <span data-ttu-id="e1a13-137">System Embedded Controller (システム埋め込みコントローラー)</span><span class="sxs-lookup"><span data-stu-id="e1a13-137">System Embedded Controller</span></span> 

- <span data-ttu-id="e1a13-138">Touch Firmware (タッチ ファームウェア)</span><span class="sxs-lookup"><span data-stu-id="e1a13-138">Touch Firmware</span></span> 

![システム情報とファームウェアのバージョン情報](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*<span data-ttu-id="e1a13-140">図 1.</span><span class="sxs-lookup"><span data-stu-id="e1a13-140">Figure 1.</span></span> <span data-ttu-id="e1a13-141">システム情報とファームウェアのバージョン情報</span><span class="sxs-lookup"><span data-stu-id="e1a13-141">System information and firmware version information</span></span>*

<span data-ttu-id="e1a13-142">Surface デバイスの最新のファームウェア バージョンに関する最新情報は、お使いのデバイスの「[Surface 更新履歴](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history)」で確認できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-142">You can find up-to-date information about the latest firmware version for your Surface device in the [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) for your device.</span></span> 

## <span data-ttu-id="e1a13-143">UEFI セキュリティページ</span><span class="sxs-lookup"><span data-stu-id="e1a13-143">UEFI Security page</span></span> 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*<span data-ttu-id="e1a13-145">図 2. </span><span class="sxs-lookup"><span data-stu-id="e1a13-145">Figure 2.</span></span> <span data-ttu-id="e1a13-146">Surface UEFI のセキュリティ設定を構成する</span><span class="sxs-lookup"><span data-stu-id="e1a13-146">Configure Surface UEFI security settings</span></span>*

<span data-ttu-id="e1a13-147">[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-147">The Security page allows you to set a password to protect UEFI settings.</span></span> <span data-ttu-id="e1a13-148">Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1a13-148">This password must be entered when you boot the Surface device to UEFI.</span></span> <span data-ttu-id="e1a13-149">パスワードには、次の文字を含めることができます (図3を参照)。</span><span class="sxs-lookup"><span data-stu-id="e1a13-149">The password can contain the following characters (as shown in Figure 3):</span></span> 

- <span data-ttu-id="e1a13-150">大文字: A ～ Z</span><span class="sxs-lookup"><span data-stu-id="e1a13-150">Uppercase letters: A-Z</span></span> 

- <span data-ttu-id="e1a13-151">小文字: a ～ z</span><span class="sxs-lookup"><span data-stu-id="e1a13-151">Lowercase letters: a-z</span></span> 

- <span data-ttu-id="e1a13-152">数字: 1 ～ 0</span><span class="sxs-lookup"><span data-stu-id="e1a13-152">Numbers: 1-0</span></span> 

- <span data-ttu-id="e1a13-153">特殊文字:! @ # $% ^& \* ()? <>{} []-_ = + |.,;: ' ' "</span><span class="sxs-lookup"><span data-stu-id="e1a13-153">Special characters: !@#$%^&\*()?<>{}[]-_=+|.,;:’\`”</span></span> 

<span data-ttu-id="e1a13-154">パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-154">The password must be at least 6 characters and is case sensitive.</span></span> 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*<span data-ttu-id="e1a13-156">図 3. </span><span class="sxs-lookup"><span data-stu-id="e1a13-156">Figure 3.</span></span> <span data-ttu-id="e1a13-157">Surface UEFI の設定を保護するためのパスワードを追加する</span><span class="sxs-lookup"><span data-stu-id="e1a13-157">Add a password to protect Surface UEFI settings</span></span>*

<span data-ttu-id="e1a13-158">[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-158">On the Security page you can also change the configuration of Secure Boot on your Surface device.</span></span> <span data-ttu-id="e1a13-159">セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-159">Secure Boot technology prevents unauthorized boot code from booting on your Surface device, which protects against bootkit and rootkit-type malware infections.</span></span> <span data-ttu-id="e1a13-160">セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-160">You can disable Secure Boot to allow your Surface device to boot third-party operating systems or bootable media.</span></span> <span data-ttu-id="e1a13-161">図4に示すように、サードパーティの証明書を使用するために、セキュアブートを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-161">You can also configure Secure Boot to work with third-party certificates, as shown in Figure 4.</span></span> <span data-ttu-id="e1a13-162">詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e1a13-162">Read more about [Secure Boot](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) in the TechNet Library.</span></span>

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*<span data-ttu-id="e1a13-164">図 4: </span><span class="sxs-lookup"><span data-stu-id="e1a13-164">Figure 4.</span></span> <span data-ttu-id="e1a13-165">セキュア ブートを設定する</span><span class="sxs-lookup"><span data-stu-id="e1a13-165">Configure Secure Boot</span></span>*

<span data-ttu-id="e1a13-166">お使いのデバイスによっては、TPM が有効か無効かを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-166">Depending on your device, you may also be able to see if your TPM is enabled or disabled.</span></span> <span data-ttu-id="e1a13-167">[ **Tpm を有効にする**  ] 設定が表示されない場合は、「Windows で tpm を開く」を参照して、状態を確認してください (図 5)。</span><span class="sxs-lookup"><span data-stu-id="e1a13-167">If you do not see the **Enable TPM**  setting, open tpm.msc in Windows to check the status, as shown in Figure 5.</span></span> <span data-ttu-id="e1a13-168">TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-168">The TPM is used to authenticate encryption for your device’s data with BitLocker.</span></span> <span data-ttu-id="e1a13-169">詳細については、「 [BitLocker の概要](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1a13-169">To learn more, see [BitLocker overview](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span></span> 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*<span data-ttu-id="e1a13-171">図 5: </span><span class="sxs-lookup"><span data-stu-id="e1a13-171">Figure 5.</span></span> <span data-ttu-id="e1a13-172">TPM コンソール</span><span class="sxs-lookup"><span data-stu-id="e1a13-172">TPM console</span></span>*


## <span data-ttu-id="e1a13-173">UEFI メニュー: デバイス</span><span class="sxs-lookup"><span data-stu-id="e1a13-173">UEFI menu: Devices</span></span> 

<span data-ttu-id="e1a13-174">[デバイス] ページでは、次のような特定のデバイスとコンポーネントを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-174">The Devices page allows you to  enable or disable specific devices and components including:</span></span>

- <span data-ttu-id="e1a13-175">ドッキング ポートと USB ポート</span><span class="sxs-lookup"><span data-stu-id="e1a13-175">Docking and USB Ports</span></span> 

- <span data-ttu-id="e1a13-176">MicroSD スロットと SD カード スロット</span><span class="sxs-lookup"><span data-stu-id="e1a13-176">MicroSD or SD Card Slot</span></span> 

- <span data-ttu-id="e1a13-177">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="e1a13-177">Rear Camera</span></span> 

- <span data-ttu-id="e1a13-178">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="e1a13-178">Front Camera</span></span> 

- <span data-ttu-id="e1a13-179">赤外線 (IR) カメラ</span><span class="sxs-lookup"><span data-stu-id="e1a13-179">Infrared (IR) Camera</span></span> 

- <span data-ttu-id="e1a13-180">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e1a13-180">Wi-Fi and Bluetooth</span></span> 

- <span data-ttu-id="e1a13-181">オンボード オーディオ (スピーカー、マイク)</span><span class="sxs-lookup"><span data-stu-id="e1a13-181">Onboard Audio (Speakers and Microphone)</span></span> 

<span data-ttu-id="e1a13-182">各デバイスは、図6に示すように、 **[オン** ] (有効) または [ **オフ** ] (無効) の位置に移動できるスライダボタンと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-182">Each device is listed with a slider button that you can move to **On** (enabled) or **Off** (disabled) position, as shown in Figure 6.</span></span> 

![特定のデバイスを有効および無効にする](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*<span data-ttu-id="e1a13-184">図 6. </span><span class="sxs-lookup"><span data-stu-id="e1a13-184">Figure 6.</span></span> <span data-ttu-id="e1a13-185">特定のデバイスを有効および無効にする</span><span class="sxs-lookup"><span data-stu-id="e1a13-185">Enable and disable specific devices</span></span>*

## <span data-ttu-id="e1a13-186">UEFI メニュー: ブート構成</span><span class="sxs-lookup"><span data-stu-id="e1a13-186">UEFI menu: Boot configuration</span></span> 

<span data-ttu-id="e1a13-187">[ブート構成] ページでは、ブートデバイスの順序を変更したり、次のデバイスの起動を有効または無効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-187">The Boot Configuration page allows you to change the order of your boot devices as well as enable or disable boot of the following devices:</span></span> 

- <span data-ttu-id="e1a13-188">Windows ブート マネージャー</span><span class="sxs-lookup"><span data-stu-id="e1a13-188">Windows Boot Manager</span></span> 

- <span data-ttu-id="e1a13-189">USB 記憶装置</span><span class="sxs-lookup"><span data-stu-id="e1a13-189">USB Storage</span></span> 

- <span data-ttu-id="e1a13-190">PXE ネットワーク</span><span class="sxs-lookup"><span data-stu-id="e1a13-190">PXE Network</span></span> 

- <span data-ttu-id="e1a13-191">内部ストレージ</span><span class="sxs-lookup"><span data-stu-id="e1a13-191">Internal Storage</span></span> 

<span data-ttu-id="e1a13-192">特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-192">You can boot from a specific device immediately, or you can swipe left on that device’s entry in the list using the touchscreen.</span></span> <span data-ttu-id="e1a13-193">また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-193">You can also boot immediately to a USB device or USB Ethernet adapter when the Surface device is powered off by pressing the **Volume Down** button and the **Power** button simultaneously.</span></span> 

<span data-ttu-id="e1a13-194">指定したブート順序を有効にするには、図7に示すように、[ **代替のブートシーケンスを有効** にする] オプションを **[オン**] に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1a13-194">For the specified boot order to take effect, you must set the **Enable Alternate Boot Sequence** option to **On**, as shown in Figure 7.</span></span> 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*<span data-ttu-id="e1a13-196">図 7.</span><span class="sxs-lookup"><span data-stu-id="e1a13-196">Figure 7.</span></span> <span data-ttu-id="e1a13-197">Surface デバイスのブート順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e1a13-197">Configure the boot order for your Surface device</span></span>* 

<span data-ttu-id="e1a13-198">また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="e1a13-198">You can also turn on and off IPv6 support for PXE with the **Enable IPv6 for PXE Network Boot** option, for example when performing a Windows deployment using PXE where the PXE server is configured for IPv4 only.</span></span>  

## <span data-ttu-id="e1a13-199">UEFI メニュー: 管理</span><span class="sxs-lookup"><span data-stu-id="e1a13-199">UEFI menu: Management</span></span>
<span data-ttu-id="e1a13-200">[管理] ページでは、Surface Pro 7、Surface Pro X、Surface Pc 3 などの適格なデバイスでゼロタッチの UEFI 管理とその他の機能の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-200">The Management page allows you to manage use of Zero Touch UEFI Management and other features on eligible devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

![<span data-ttu-id="e1a13-201">ゼロタッチの UEFI 管理とその他の機能へのアクセスを管理する ( ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *図 8)。ゼロタッチの UEFI 管理およびその他の機能へのアクセスを管理する*</span><span class="sxs-lookup"><span data-stu-id="e1a13-201">Manage access to Zero Touch UEFI Management and other features](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
*Figure 8. Manage access to Zero Touch UEFI Management and other features*</span></span> 


<span data-ttu-id="e1a13-202">ゼロタッチ UEFI 管理では、「デバイスファームウェア構成インターフェイス (DFCI)」と呼ばれるデバイスプロファイルを使用して、UEFI 設定をリモートで管理できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-202">Zero Touch UEFI Management lets you remotely manage UEFI settings  by using a device profile within Intune called Device Firmware Configuration Interface (DFCI).</span></span> <span data-ttu-id="e1a13-203">この設定を構成しない場合は、DFCI を使って適格なデバイスを管理する機能が [ **準備完了**] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-203">If you do not configure this setting, the ability to manage eligible devices with DFCI is set to **Ready**.</span></span> <span data-ttu-id="e1a13-204">DFCI を無効にするには、[ **オプトアウト**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-204">To prevent DFCI, select **Opt-Out**.</span></span> 

> [!NOTE]
> <span data-ttu-id="e1a13-205">[UEFI 管理の設定] ページと DFCI の使用は、Surface Pro 7、Surface Pro X、Surface ノートブック3でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-205">The UEFI Management settings page and use of DFCI is only available on Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

<span data-ttu-id="e1a13-206">詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1a13-206">For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="e1a13-207">UEFI メニュー: 終了</span><span class="sxs-lookup"><span data-stu-id="e1a13-207">UEFI menu: Exit</span></span> 

<span data-ttu-id="e1a13-208">図9に示すように、[**終了**] ページの [**今すぐ再起動**] ボタンを使用して、UEFI の設定を終了します。</span><span class="sxs-lookup"><span data-stu-id="e1a13-208">Use the **Restart Now** button on the **Exit** page to exit UEFI settings, as shown in Figure 9.</span></span> 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*<span data-ttu-id="e1a13-210">図 9.</span><span class="sxs-lookup"><span data-stu-id="e1a13-210">Figure 9.</span></span> <span data-ttu-id="e1a13-211">Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする</span><span class="sxs-lookup"><span data-stu-id="e1a13-211">Click Restart Now to exit Surface UEFI and restart the device</span></span>*

## <span data-ttu-id="e1a13-212">Surface UEFI のブート画面</span><span class="sxs-lookup"><span data-stu-id="e1a13-212">Surface UEFI boot screens</span></span>

<span data-ttu-id="e1a13-213">Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-213">When you update Surface device firmware, by using either Windows Update or manual installation, the updates are not applied immediately to the device, but instead during the next reboot cycle.</span></span> <span data-ttu-id="e1a13-214">Surface のファームウェアの更新プロセスについて詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e1a13-214">You can find out more about the Surface firmware update process in [Manage Surface driver and firmware updates](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates).</span></span> <span data-ttu-id="e1a13-215">ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-215">The progress of the firmware update is displayed on a screen with progress bars of differing colors to indicate the firmware for each component.</span></span> <span data-ttu-id="e1a13-216">各コンポーネントの進行状況バーは、図 9 ~ 18 に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-216">Each component’s progress bar is shown in Figures 9 through 18.</span></span>

![青色の進行状況バーで表示される Surface UEFI のファームウェアの更新](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*<span data-ttu-id="e1a13-218">図 10.</span><span class="sxs-lookup"><span data-stu-id="e1a13-218">Figure 10.</span></span> <span data-ttu-id="e1a13-219">青色の進行状況バーで表示される Surface UEFI のファームウェア更新</span><span class="sxs-lookup"><span data-stu-id="e1a13-219">The Surface UEFI firmware update displays a blue progress bar</span></span>*

![緑色の進行状況バーで表示される System Embedded Controller のファームウェア](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*<span data-ttu-id="e1a13-221">図 11.</span><span class="sxs-lookup"><span data-stu-id="e1a13-221">Figure 11.</span></span> <span data-ttu-id="e1a13-222">緑色の進行状況バーで表示される System Embedded Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="e1a13-222">The System Embedded Controller firmware update displays a green progress bar</span></span>*

![オレンジの進行状況バーで表示される SAM Controller のファームウェアの更新](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*<span data-ttu-id="e1a13-224">図 12.</span><span class="sxs-lookup"><span data-stu-id="e1a13-224">Figure 12.</span></span> <span data-ttu-id="e1a13-225">オレンジ色の進行状況バーで表示される SAM Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="e1a13-225">The SAM Controller firmware update displays an orange progress bar</span></span>*

![赤色の進行状況バーで表示される Intel Management Engine のファームウェア](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*<span data-ttu-id="e1a13-227">図 13.</span><span class="sxs-lookup"><span data-stu-id="e1a13-227">Figure 13.</span></span> <span data-ttu-id="e1a13-228">赤色の進行状況バーで表示される Intel Management Engine のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="e1a13-228">The Intel Management Engine firmware update displays a red progress bar</span></span>*

![灰色の進行状況バーで表示される Surface Touch のファームウェア](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*<span data-ttu-id="e1a13-230">図 14.</span><span class="sxs-lookup"><span data-stu-id="e1a13-230">Figure 14.</span></span> <span data-ttu-id="e1a13-231">灰色の進行状況バーで表示される Surface Touch のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="e1a13-231">The Surface touch firmware update displays a gray progress bar</span></span>*

![淡い緑の進行状況バーが表示された Surface キープファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*<span data-ttu-id="e1a13-233">図 15.</span><span class="sxs-lookup"><span data-stu-id="e1a13-233">Figure 15.</span></span> <span data-ttu-id="e1a13-234">Surface キープファームウェア更新プログラムには、薄い緑色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="e1a13-234">The Surface KIP firmware update displays a light green progress bar</span></span>*

![ピンク色の進行状況バーが表示された Surface の赤のファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*<span data-ttu-id="e1a13-236">図 16 Surface の "ファームウェア更新プログラム" に明るいピンクの進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="e1a13-236">Figure 16 The Surface ISH firmware update displays a light pink progress bar</span></span>*

![Surface トラックパッドファームウェアと灰色の進行状況バー](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*<span data-ttu-id="e1a13-238">図 17.</span><span class="sxs-lookup"><span data-stu-id="e1a13-238">Figure 17.</span></span> <span data-ttu-id="e1a13-239">Surface トラックパッドファームウェア更新プログラムにより、ピンクの進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="e1a13-239">The Surface Trackpad firmware update displays a pink progress bar</span></span>*

![薄い灰色の進行状況バーが表示されたファームウェアの Surface tc](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*<span data-ttu-id="e1a13-241">図 18.</span><span class="sxs-lookup"><span data-stu-id="e1a13-241">Figure 18.</span></span> <span data-ttu-id="e1a13-242">ファームウェア更新プログラムの Surface TCON 淡い灰色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="e1a13-242">The Surface TCON firmware update displays a light gray progress bar</span></span>*


![Surface TPM ファームウェアと明るい紫色の進行状況バー](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*<span data-ttu-id="e1a13-244">図 19: </span><span class="sxs-lookup"><span data-stu-id="e1a13-244">Figure 19.</span></span> <span data-ttu-id="e1a13-245">Surface TPM ファームウェア更新プログラムによって紫色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="e1a13-245">The Surface TPM firmware update displays a purple progress bar</span></span>*


>[!NOTE]
><span data-ttu-id="e1a13-246">図19に示すように、セキュアブートが無効であることを示す追加の警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1a13-246">An additional warning message that indicates Secure Boot is disabled is displayed, as shown in Figure 19.</span></span>

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*<span data-ttu-id="e1a13-248">図 20.</span><span class="sxs-lookup"><span data-stu-id="e1a13-248">Figure 20.</span></span> <span data-ttu-id="e1a13-249">Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面</span><span class="sxs-lookup"><span data-stu-id="e1a13-249">Surface boot screen that indicates Secure Boot has been disabled in Surface UEFI settings</span></span>*

## <span data-ttu-id="e1a13-250">関連トピック</span><span class="sxs-lookup"><span data-stu-id="e1a13-250">Related topics</span></span>

- [<span data-ttu-id="e1a13-251">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="e1a13-251">Intune management of Surface UEFI settings</span></span>](surface-manage-dfci-guide.md)

-  [<span data-ttu-id="e1a13-252">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="e1a13-252">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
