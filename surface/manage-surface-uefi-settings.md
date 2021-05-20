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
ms.date: 04/13/2021
ms.openlocfilehash: ea995eda277ecf235eedd92f3af6edb0b60ae68a
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576507"
---
# <a name="manage-surface-uefi-settings"></a><span data-ttu-id="45842-104">Surface UEFI の設定を管理する</span><span class="sxs-lookup"><span data-stu-id="45842-104">Manage Surface UEFI settings</span></span>

 <span data-ttu-id="45842-105">Surface PC デバイスは、Microsoft が特にこれらのデバイス用に設計した一意の統合拡張可能ファームウェア インターフェイス (UEFI) を利用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="45842-105">Surface PC devices are designed to utilize a unique Unified Extensible Firmware Interface (UEFI) engineered by Microsoft specifically for these devices.</span></span> <span data-ttu-id="45842-106">Surface UEFI 設定では、組み込みのデバイスとコンポーネントを有効または無効にし、UEFI 設定を変更から保護し、Surface デバイスのブート設定を調整できます。</span><span class="sxs-lookup"><span data-stu-id="45842-106">Surface UEFI settings provide the ability to enable or disable built-in devices and components, protect UEFI settings from being changed, and adjust the Surface device boot settings.</span></span> 

## <a name="supported-products"></a><span data-ttu-id="45842-107">サポートされている製品</span><span class="sxs-lookup"><span data-stu-id="45842-107">Supported products</span></span>

<span data-ttu-id="45842-108">UEFI 管理は、次の場合にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="45842-108">UEFI management is supported on the following:</span></span> 

- <span data-ttu-id="45842-109">Surface Pro 4、Surface Pro (第 5 世代)、Surface Pro 6、Surface Pro 7、Surface Pro 7+、Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="45842-109">Surface Pro 4, Surface Pro (5th Gen), Surface Pro 6, Surface Pro 7, Surface Pro 7+, Surface Pro X</span></span>
- <span data-ttu-id="45842-110">Surface Laptop (第 1 世代), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="45842-110">Surface Laptop (1st Gen), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4</span></span>
- <span data-ttu-id="45842-111">Surface Studio (第 1 世代), Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="45842-111">Surface Studio (1st Gen), Surface Studio 2</span></span>
- <span data-ttu-id="45842-112">Surface Book、Surface Book 2、Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="45842-112">Surface Book, Surface Book 2, Surface Book 3</span></span>
- <span data-ttu-id="45842-113">Surface Go、 Surface Go 2[ <sup> 1 </sup> ](#references)</span><span class="sxs-lookup"><span data-stu-id="45842-113">Surface Go, Surface Go 2[<sup>1</sup>](#references)</span></span>

## <a name="support-for-cloud-based-management"></a><span data-ttu-id="45842-114">クラウドベースの管理のサポート</span><span class="sxs-lookup"><span data-stu-id="45842-114">Support for cloud-based management</span></span>

<span data-ttu-id="45842-115">Microsoft Intune に組み込むデバイス ファームウェア構成インターフェイス (DFCI) プロファイル (パブリック プレビューで利用可能) を使用すると、Surface UEFI 管理は最新の管理スタックを UEFI ハードウェア レベルまで拡張します。</span><span class="sxs-lookup"><span data-stu-id="45842-115">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="45842-116">DFCI はゼロタッチ プロビジョニングをサポートし、BIOS パスワードを排除し、ブート オプションや組み込みの周辺機器などのセキュリティ設定を制御し、将来の高度なセキュリティ シナリオの基礎を築きます。</span><span class="sxs-lookup"><span data-stu-id="45842-116">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="45842-117">DFCI は現在、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 3、Surface Pro 7、および Surface Pro X で使用できます。 詳細については[、「Surface UEFI 設定の Intune 管理」を参照してください](surface-manage-dfci-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="45842-117">DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7, and Surface Pro X.  For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <a name="open-surface-uefi-menu"></a><span data-ttu-id="45842-118">Surface UEFI メニューを開く</span><span class="sxs-lookup"><span data-stu-id="45842-118">Open Surface UEFI menu</span></span>

<span data-ttu-id="45842-119">システムの起動時に UEFI 設定を調整するには、次の方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="45842-119">To adjust UEFI settings during system startup:</span></span>

1. <span data-ttu-id="45842-120">Surface をシャットダウンし、約 10 秒待ってオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="45842-120">Shut down your Surface and wait about 10 seconds to make sure it's off.</span></span>
2. <span data-ttu-id="45842-121">音量アップ ボタン **を長押** しし、同時に [電源] ボタンを押したまま **離します。**</span><span class="sxs-lookup"><span data-stu-id="45842-121">Press and hold the **Volume-up** button  and - at the same time - press and release the **Power button.**</span></span>
3. <span data-ttu-id="45842-122">Microsoft または Surface のロゴが画面に表示されたら、UEFI\*\*\*\* 画面が表示されるまで[ボリュームアップ] ボタンを押し続けます。</span><span class="sxs-lookup"><span data-stu-id="45842-122">As the Microsoft or Surface logo appears on your screen, continue to hold the **Volume-up** button until the UEFI screen appears.</span></span>

## <a name="uefi-pc-information-page"></a><span data-ttu-id="45842-123">UEFI PC 情報ページ</span><span class="sxs-lookup"><span data-stu-id="45842-123">UEFI PC information page</span></span>

<span data-ttu-id="45842-124">[PC 情報] ページには、Surface デバイスに関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="45842-124">The PC information page includes detailed information about your Surface device:</span></span> 

- <span data-ttu-id="45842-125">**Model** – Surface デバイスのモデルがここに表示されます (例: Surface Book 2 または Surface Pro 7)。</span><span class="sxs-lookup"><span data-stu-id="45842-125">**Model** – Your Surface device’s model will be displayed here, such as Surface Book 2 or Surface Pro 7.</span></span> <span data-ttu-id="45842-126">デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。</span><span class="sxs-lookup"><span data-stu-id="45842-126">The exact configuration of your device is not shown, (such as processor, disk size, or memory size).</span></span> 
- <span data-ttu-id="45842-127">**UUID** – このユニバーサル固有識別子の番号はデバイスに固有であり、展開または管理の際にデバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="45842-127">**UUID** – This Universally Unique Identification number is specific to your device and is used to identify the device during deployment or management.</span></span> 

- <span data-ttu-id="45842-128">**Serial Number** (シリアル番号) – この番号は、アセットのタグ付けやサポートでこの特定の Surface デバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="45842-128">**Serial Number** – This number is used to identify this specific Surface device for asset tagging and support scenarios.</span></span>
- <span data-ttu-id="45842-129">**Asset Tag** (アセット タグ) – アセット タグは、[アセット タグ ツール](https://docs.microsoft.com/surface/assettag)で Surface デバイスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="45842-129">**Asset Tag** – The asset tag is assigned to the Surface device with the [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span></span> 

<span data-ttu-id="45842-130">Surface デバイスのファームウェアに関する詳細情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="45842-130">You will also find detailed information about the firmware of your Surface device.</span></span> <span data-ttu-id="45842-131">Surface デバイスには複数の内部コンポーネントがあり、それぞれが異なるバージョンのファームウェアを実行しています。</span><span class="sxs-lookup"><span data-stu-id="45842-131">Surface devices have several internal components that each run different versions of firmware.</span></span> <span data-ttu-id="45842-132">次の各デバイスのファームウェア バージョンが、**[PC information]** (PC の情報) ページに表示されます (図 1 を参照)。</span><span class="sxs-lookup"><span data-stu-id="45842-132">The firmware version of each of the following devices is displayed on the **PC information** page (as shown in Figure 1):</span></span> 

- <span data-ttu-id="45842-133">System UEFI (システム UEFI)</span><span class="sxs-lookup"><span data-stu-id="45842-133">System UEFI</span></span> 

- <span data-ttu-id="45842-134">SAM Controller (SAM コントローラー)</span><span class="sxs-lookup"><span data-stu-id="45842-134">SAM Controller</span></span> 

- <span data-ttu-id="45842-135">Intel Management Engine (Intel 管理エンジン)</span><span class="sxs-lookup"><span data-stu-id="45842-135">Intel Management Engine</span></span> 

- <span data-ttu-id="45842-136">System Embedded Controller (システム埋め込みコントローラー)</span><span class="sxs-lookup"><span data-stu-id="45842-136">System Embedded Controller</span></span> 

- <span data-ttu-id="45842-137">Touch Firmware (タッチ ファームウェア)</span><span class="sxs-lookup"><span data-stu-id="45842-137">Touch Firmware</span></span> 

![システム情報とファームウェアのバージョン情報](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*<span data-ttu-id="45842-139">図 1.</span><span class="sxs-lookup"><span data-stu-id="45842-139">Figure 1.</span></span> <span data-ttu-id="45842-140">システム情報とファームウェアのバージョン情報</span><span class="sxs-lookup"><span data-stu-id="45842-140">System information and firmware version information</span></span>*

<span data-ttu-id="45842-141">Surface デバイスの最新のファームウェア バージョンに関する最新情報は、お使いのデバイスの「[Surface 更新履歴](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history)」で確認できます。</span><span class="sxs-lookup"><span data-stu-id="45842-141">You can find up-to-date information about the latest firmware version for your Surface device in the [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) for your device.</span></span> 

## <a name="uefi-security-page"></a><span data-ttu-id="45842-142">UEFI セキュリティ ページ</span><span class="sxs-lookup"><span data-stu-id="45842-142">UEFI Security page</span></span> 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*<span data-ttu-id="45842-144">図 2.</span><span class="sxs-lookup"><span data-stu-id="45842-144">Figure 2.</span></span> <span data-ttu-id="45842-145">Surface UEFI のセキュリティ設定を構成する</span><span class="sxs-lookup"><span data-stu-id="45842-145">Configure Surface UEFI security settings</span></span>*

<span data-ttu-id="45842-146">[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="45842-146">The Security page allows you to set a password to protect UEFI settings.</span></span> <span data-ttu-id="45842-147">Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45842-147">This password must be entered when you boot the Surface device to UEFI.</span></span> <span data-ttu-id="45842-148">パスワードには、次の文字を含めることができます (図 3 を参照)。</span><span class="sxs-lookup"><span data-stu-id="45842-148">The password can contain the following characters (as shown in Figure 3):</span></span> 

- <span data-ttu-id="45842-149">大文字: A ～ Z</span><span class="sxs-lookup"><span data-stu-id="45842-149">Uppercase letters: A-Z</span></span> 

- <span data-ttu-id="45842-150">小文字: a ～ z</span><span class="sxs-lookup"><span data-stu-id="45842-150">Lowercase letters: a-z</span></span> 

- <span data-ttu-id="45842-151">数字: 1 ～ 0</span><span class="sxs-lookup"><span data-stu-id="45842-151">Numbers: 1-0</span></span> 

- <span data-ttu-id="45842-152">特殊文字: !@#$%^&\*()?<>{} []-_=+|.;:''</span><span class="sxs-lookup"><span data-stu-id="45842-152">Special characters: !@#$%^&\*()?<>{}[]-_=+|.,;:’\`”</span></span> 

<span data-ttu-id="45842-153">パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="45842-153">The password must be at least 6 characters and is case sensitive.</span></span> 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*<span data-ttu-id="45842-155">図 3. </span><span class="sxs-lookup"><span data-stu-id="45842-155">Figure 3.</span></span> <span data-ttu-id="45842-156">Surface UEFI の設定を保護するためのパスワードを追加する</span><span class="sxs-lookup"><span data-stu-id="45842-156">Add a password to protect Surface UEFI settings</span></span>*

<span data-ttu-id="45842-157">[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="45842-157">On the Security page you can also change the configuration of Secure Boot on your Surface device.</span></span> <span data-ttu-id="45842-158">セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="45842-158">Secure Boot technology prevents unauthorized boot code from booting on your Surface device, which protects against bootkit and rootkit-type malware infections.</span></span> <span data-ttu-id="45842-159">セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="45842-159">You can disable Secure Boot to allow your Surface device to boot third-party operating systems or bootable media.</span></span> <span data-ttu-id="45842-160">図 4 に示すように、サードパーティの証明書を使用するセキュア ブートを構成できます。</span><span class="sxs-lookup"><span data-stu-id="45842-160">You can also configure Secure Boot to work with third-party certificates, as shown in Figure 4.</span></span> <span data-ttu-id="45842-161">詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="45842-161">Read more about [Secure Boot](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) in the TechNet Library.</span></span>

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*<span data-ttu-id="45842-163">図 4: </span><span class="sxs-lookup"><span data-stu-id="45842-163">Figure 4.</span></span> <span data-ttu-id="45842-164">セキュア ブートを設定する</span><span class="sxs-lookup"><span data-stu-id="45842-164">Configure Secure Boot</span></span>*

<span data-ttu-id="45842-165">デバイスによっては、TPM が有効になっているか無効になっているかも確認できます。</span><span class="sxs-lookup"><span data-stu-id="45842-165">Depending on your device, you may also be able to see if your TPM is enabled or disabled.</span></span> <span data-ttu-id="45842-166">[TPM の有効化]\*\*\*\* 設定が表示されない場合は、図 5 に示すように、Windowsで tpm.msc を開き、状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="45842-166">If you do not see the **Enable TPM**  setting, open tpm.msc in Windows to check the status, as shown in Figure 5.</span></span> <span data-ttu-id="45842-167">TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="45842-167">The TPM is used to authenticate encryption for your device’s data with BitLocker.</span></span> <span data-ttu-id="45842-168">詳細については、「概要」[をBitLockerしてください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)。</span><span class="sxs-lookup"><span data-stu-id="45842-168">To learn more, see [BitLocker overview](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span></span> 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*<span data-ttu-id="45842-170">図 5: </span><span class="sxs-lookup"><span data-stu-id="45842-170">Figure 5.</span></span> <span data-ttu-id="45842-171">TPM コンソール</span><span class="sxs-lookup"><span data-stu-id="45842-171">TPM console</span></span>*


## <a name="uefi-menu-devices"></a><span data-ttu-id="45842-172">UEFI メニュー: デバイス</span><span class="sxs-lookup"><span data-stu-id="45842-172">UEFI menu: Devices</span></span> 

<span data-ttu-id="45842-173">[デバイス] ページでは、次を含む特定のデバイスとコンポーネントを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="45842-173">The Devices page allows you to  enable or disable specific devices and components including:</span></span>

- <span data-ttu-id="45842-174">ドッキング ポートと USB ポート</span><span class="sxs-lookup"><span data-stu-id="45842-174">Docking and USB Ports</span></span> 

- <span data-ttu-id="45842-175">MicroSD スロットと SD カード スロット</span><span class="sxs-lookup"><span data-stu-id="45842-175">MicroSD or SD Card Slot</span></span> 

- <span data-ttu-id="45842-176">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="45842-176">Rear Camera</span></span> 

- <span data-ttu-id="45842-177">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="45842-177">Front Camera</span></span> 

- <span data-ttu-id="45842-178">赤外線 (IR) カメラ</span><span class="sxs-lookup"><span data-stu-id="45842-178">Infrared (IR) Camera</span></span> 

- <span data-ttu-id="45842-179">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="45842-179">Wi-Fi and Bluetooth</span></span> 

- <span data-ttu-id="45842-180">オンボード オーディオ (スピーカー、マイク)</span><span class="sxs-lookup"><span data-stu-id="45842-180">Onboard Audio (Speakers and Microphone)</span></span> 

<span data-ttu-id="45842-181">図 6 に示すように、各デバイスにはスライダー ボタンが表示され、オン **(有効** ) またはオフ **(無効** ) の位置に移動できます。</span><span class="sxs-lookup"><span data-stu-id="45842-181">Each device is listed with a slider button that you can move to **On** (enabled) or **Off** (disabled) position, as shown in Figure 6.</span></span> 

![特定のデバイスを有効および無効にする](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*<span data-ttu-id="45842-183">図 6. </span><span class="sxs-lookup"><span data-stu-id="45842-183">Figure 6.</span></span> <span data-ttu-id="45842-184">特定のデバイスを有効および無効にする</span><span class="sxs-lookup"><span data-stu-id="45842-184">Enable and disable specific devices</span></span>*

## <a name="uefi-menu-boot-configuration"></a><span data-ttu-id="45842-185">UEFI メニュー: ブート構成</span><span class="sxs-lookup"><span data-stu-id="45842-185">UEFI menu: Boot configuration</span></span> 

<span data-ttu-id="45842-186">[ブート構成] ページでは、ブート デバイスの順序を変更したり、次のデバイスの起動を有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="45842-186">The Boot Configuration page allows you to change the order of your boot devices as well as enable or disable boot of the following devices:</span></span> 

- <span data-ttu-id="45842-187">Windows ブート マネージャー</span><span class="sxs-lookup"><span data-stu-id="45842-187">Windows Boot Manager</span></span> 

- <span data-ttu-id="45842-188">USB 記憶装置</span><span class="sxs-lookup"><span data-stu-id="45842-188">USB Storage</span></span> 

- <span data-ttu-id="45842-189">PXE ネットワーク</span><span class="sxs-lookup"><span data-stu-id="45842-189">PXE Network</span></span> 

- <span data-ttu-id="45842-190">内部ストレージ</span><span class="sxs-lookup"><span data-stu-id="45842-190">Internal Storage</span></span> 

<span data-ttu-id="45842-191">特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。</span><span class="sxs-lookup"><span data-stu-id="45842-191">You can boot from a specific device immediately, or you can swipe left on that device’s entry in the list using the touchscreen.</span></span> <span data-ttu-id="45842-192">また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="45842-192">You can also boot immediately to a USB device or USB Ethernet adapter when the Surface device is powered off by pressing the **Volume Down** button and the **Power** button simultaneously.</span></span> 

<span data-ttu-id="45842-193">指定したブート順序を有効にするには、図 7\*\*\*\* に示すように、[代替ブート シーケンスを有効にする] オプションを **[オン**] に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45842-193">For the specified boot order to take effect, you must set the **Enable Alternate Boot Sequence** option to **On**, as shown in Figure 7.</span></span> 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*<span data-ttu-id="45842-195">図 7.</span><span class="sxs-lookup"><span data-stu-id="45842-195">Figure 7.</span></span> <span data-ttu-id="45842-196">Surface デバイスのブート順序を設定する</span><span class="sxs-lookup"><span data-stu-id="45842-196">Configure the boot order for your Surface device</span></span>* 

<span data-ttu-id="45842-197">また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="45842-197">You can also turn on and off IPv6 support for PXE with the **Enable IPv6 for PXE Network Boot** option, for example when performing a Windows deployment using PXE where the PXE server is configured for IPv4 only.</span></span>  

## <a name="uefi-menu-management"></a><span data-ttu-id="45842-198">UEFI メニュー: 管理</span><span class="sxs-lookup"><span data-stu-id="45842-198">UEFI menu: Management</span></span>
<span data-ttu-id="45842-199">[管理] ページでは、ゼロ タッチ UEFI 管理の使用と、Surface Pro 7、Surface Pro X、および Surface Laptop 3 を含む対象デバイス上の他の機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="45842-199">The Management page allows you to manage use of Zero Touch UEFI Management and other features on eligible devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

![<span data-ttu-id="45842-200">図 8 は、ゼロ タッチ UEFI 管理などの機能 ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *へのアクセスを管理します。ゼロ タッチ UEFI 管理などの機能へのアクセスを管理する*</span><span class="sxs-lookup"><span data-stu-id="45842-200">Manage access to Zero Touch UEFI Management and other features](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
*Figure 8. Manage access to Zero Touch UEFI Management and other features*</span></span> 


<span data-ttu-id="45842-201">ゼロ タッチ UEFI 管理を使用すると、Intune (デバイス ファームウェア構成インターフェイス (DFCI) と呼ばれるデバイス プロファイルを使用して、UEFI 設定をリモートで管理できます。</span><span class="sxs-lookup"><span data-stu-id="45842-201">Zero Touch UEFI Management lets you remotely manage UEFI settings  by using a device profile within Intune called Device Firmware Configuration Interface (DFCI).</span></span> <span data-ttu-id="45842-202">この設定を構成しない場合、DFCI を使用して対象デバイスを管理する機能は [準備完了] に設定 **されます**。</span><span class="sxs-lookup"><span data-stu-id="45842-202">If you do not configure this setting, the ability to manage eligible devices with DFCI is set to **Ready**.</span></span> <span data-ttu-id="45842-203">DFCI を防止するには、[オプトアウト] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="45842-203">To prevent DFCI, select **Opt-Out**.</span></span> 

> [!NOTE]
> <span data-ttu-id="45842-204">現在、UEFI 管理設定ページと DFCI の使用は、Surface Pro 7+、Surface Laptop Go、Surface Book 3、Surface Laptop 4、Surface Laptop 3、Surface Pro 7、Surface Pro X で利用できます。詳細については[、「Surface UEFI 設定の Intune 管理」を参照してください](surface-manage-dfci-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="45842-204">The UEFI Management settings page and use of DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Pro 7, and Surface Pro X. To learn more, see [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <a name="uefi-menu-exit"></a><span data-ttu-id="45842-205">UEFI メニュー: 終了</span><span class="sxs-lookup"><span data-stu-id="45842-205">UEFI menu: Exit</span></span> 

<span data-ttu-id="45842-206">図 9 **に示すように** 、[ **終了** ] ページの [今すぐ再起動] ボタンを使用して UEFI 設定を終了します。</span><span class="sxs-lookup"><span data-stu-id="45842-206">Use the **Restart Now** button on the **Exit** page to exit UEFI settings, as shown in Figure 9.</span></span> 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*<span data-ttu-id="45842-208">図 9.</span><span class="sxs-lookup"><span data-stu-id="45842-208">Figure 9.</span></span> <span data-ttu-id="45842-209">Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする</span><span class="sxs-lookup"><span data-stu-id="45842-209">Click Restart Now to exit Surface UEFI and restart the device</span></span>*

## <a name="surface-uefi-boot-screens"></a><span data-ttu-id="45842-210">Surface UEFI のブート画面</span><span class="sxs-lookup"><span data-stu-id="45842-210">Surface UEFI boot screens</span></span>

<span data-ttu-id="45842-211">Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="45842-211">When you update Surface device firmware, by using either Windows Update or manual installation, the updates are not applied immediately to the device, but instead during the next reboot cycle.</span></span> <span data-ttu-id="45842-212">Surface ファームウェア更新プロセスの詳細については、「Surface ドライバーとファームウェア更新プログラムの管理 [と展開」を参照してください](manage-surface-driver-and-firmware-updates.md)。</span><span class="sxs-lookup"><span data-stu-id="45842-212">You can find out more about the Surface firmware update process in [Manage and deploy Surface driver and firmware updates](manage-surface-driver-and-firmware-updates.md).</span></span> <span data-ttu-id="45842-213">ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="45842-213">The progress of the firmware update is displayed on a screen with progress bars of differing colors to indicate the firmware for each component.</span></span> <span data-ttu-id="45842-214">各コンポーネントの進行状況バーを図 9 ~ 18 に示します。</span><span class="sxs-lookup"><span data-stu-id="45842-214">Each component’s progress bar is shown in Figures 9 through 18.</span></span>

![青色の進行状況バーで表示される Surface UEFI のファームウェアの更新](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*<span data-ttu-id="45842-216">図 10.</span><span class="sxs-lookup"><span data-stu-id="45842-216">Figure 10.</span></span> <span data-ttu-id="45842-217">青色の進行状況バーで表示される Surface UEFI のファームウェア更新</span><span class="sxs-lookup"><span data-stu-id="45842-217">The Surface UEFI firmware update displays a blue progress bar</span></span>*

![緑色の進行状況バーで表示される System Embedded Controller のファームウェア](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*<span data-ttu-id="45842-219">図 11.</span><span class="sxs-lookup"><span data-stu-id="45842-219">Figure 11.</span></span> <span data-ttu-id="45842-220">緑色の進行状況バーで表示される System Embedded Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="45842-220">The System Embedded Controller firmware update displays a green progress bar</span></span>*

![オレンジの進行状況バーで表示される SAM Controller のファームウェアの更新](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*<span data-ttu-id="45842-222">図 12.</span><span class="sxs-lookup"><span data-stu-id="45842-222">Figure 12.</span></span> <span data-ttu-id="45842-223">オレンジ色の進行状況バーで表示される SAM Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="45842-223">The SAM Controller firmware update displays an orange progress bar</span></span>*

![赤色の進行状況バーで表示される Intel Management Engine のファームウェア](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*<span data-ttu-id="45842-225">図 13.</span><span class="sxs-lookup"><span data-stu-id="45842-225">Figure 13.</span></span> <span data-ttu-id="45842-226">赤色の進行状況バーで表示される Intel Management Engine のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="45842-226">The Intel Management Engine firmware update displays a red progress bar</span></span>*

![灰色の進行状況バーで表示される Surface Touch のファームウェア](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*<span data-ttu-id="45842-228">図 14.</span><span class="sxs-lookup"><span data-stu-id="45842-228">Figure 14.</span></span> <span data-ttu-id="45842-229">灰色の進行状況バーで表示される Surface Touch のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="45842-229">The Surface touch firmware update displays a gray progress bar</span></span>*

![薄緑色の進行状況バーを含む Surface KIP ファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*<span data-ttu-id="45842-231">図 15.</span><span class="sxs-lookup"><span data-stu-id="45842-231">Figure 15.</span></span> <span data-ttu-id="45842-232">Surface KIP ファームウェア更新プログラムは、淡い緑色の進行状況バーを表示します</span><span class="sxs-lookup"><span data-stu-id="45842-232">The Surface KIP firmware update displays a light green progress bar</span></span>*

![ピンクの進行状況バーを含む Surface ISH ファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*<span data-ttu-id="45842-234">図 16 Surface ISH ファームウェア更新プログラムに薄いピンク色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="45842-234">Figure 16 The Surface ISH firmware update displays a light pink progress bar</span></span>*

![灰色の進行状況バーを含む Surface Trackpad ファームウェア](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*<span data-ttu-id="45842-236">図 17.</span><span class="sxs-lookup"><span data-stu-id="45842-236">Figure 17.</span></span> <span data-ttu-id="45842-237">Surface Trackpad ファームウェアの更新プログラムにピンクの進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="45842-237">The Surface Trackpad firmware update displays a pink progress bar</span></span>*

![淡い灰色の進行状況バーを含む Surface TCON ファームウェア](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*<span data-ttu-id="45842-239">図 18.</span><span class="sxs-lookup"><span data-stu-id="45842-239">Figure 18.</span></span> <span data-ttu-id="45842-240">Surface TCON ファームウェア更新プログラムは、淡い灰色の進行状況バーを表示します。</span><span class="sxs-lookup"><span data-stu-id="45842-240">The Surface TCON firmware update displays a light gray progress bar</span></span>*


![薄紫色の進行状況バーを含む Surface TPM ファームウェア](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*<span data-ttu-id="45842-242">図 19: </span><span class="sxs-lookup"><span data-stu-id="45842-242">Figure 19.</span></span> <span data-ttu-id="45842-243">Surface TPM ファームウェアの更新プログラムに紫色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="45842-243">The Surface TPM firmware update displays a purple progress bar</span></span>*


>[!NOTE]
><span data-ttu-id="45842-244">図 19 に示すように、Secure Boot が無効になっているという追加の警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45842-244">An additional warning message that indicates Secure Boot is disabled is displayed, as shown in Figure 19.</span></span>

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*<span data-ttu-id="45842-246">図 20.</span><span class="sxs-lookup"><span data-stu-id="45842-246">Figure 20.</span></span> <span data-ttu-id="45842-247">Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面</span><span class="sxs-lookup"><span data-stu-id="45842-247">Surface boot screen that indicates Secure Boot has been disabled in Surface UEFI settings</span></span>*

## <a name="references"></a><span data-ttu-id="45842-248">参考資料</span><span class="sxs-lookup"><span data-stu-id="45842-248">References</span></span>

1. <span data-ttu-id="45842-249">Surface Go と Surface Go 2 はサードパーティの UEFI を使用し、DFCI はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="45842-249">Surface Go and Surface Go 2 use a third-party UEFI and do not support DFCI.</span></span> 

## <a name="related-topics"></a><span data-ttu-id="45842-250">関連トピック</span><span class="sxs-lookup"><span data-stu-id="45842-250">Related topics</span></span>

- [<span data-ttu-id="45842-251">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="45842-251">Intune management of Surface UEFI settings</span></span>](surface-manage-dfci-guide.md)

-  [<span data-ttu-id="45842-252">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="45842-252">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
