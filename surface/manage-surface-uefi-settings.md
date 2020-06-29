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
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: ce857260c3f4b42ae560a7dba51d47d0e20233bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835854"
---
# <span data-ttu-id="557f6-104">Surface UEFI の設定を管理する</span><span class="sxs-lookup"><span data-stu-id="557f6-104">Manage Surface UEFI settings</span></span>

<span data-ttu-id="557f6-105">Surface デバイスの現在および将来のすべての世代では、これらのデバイス専用の統合された固有の拡張ファームウェアインターフェイス (UEFI) が Microsoft によって設計されています。</span><span class="sxs-lookup"><span data-stu-id="557f6-105">All current and future generations of Surface devices use a unique Unified Extensible Firmware Interface (UEFI) engineered by Microsoft specifically for these devices.</span></span> <span data-ttu-id="557f6-106">Surface UEFI の設定では、組み込みのデバイスとコンポーネントを有効または無効にしたり、UEFI 設定を変更できないように保護したり、Surface device のブート設定を調整したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="557f6-106">Surface UEFI settings provide the ability to enable or disable built-in devices and components, protect UEFI settings from being changed, and adjust the Surface device boot settings.</span></span> 

## <span data-ttu-id="557f6-107">クラウドベースの管理のサポート</span><span class="sxs-lookup"><span data-stu-id="557f6-107">Support for cloud-based management</span></span>

<span data-ttu-id="557f6-108">Microsoft Intune に組み込まれたデバイスファームウェア構成インターフェイス (DFCI) プロファイルを使用すると (パブリックプレビューで利用できるようになりました)、Surface UEFI 管理では、最新の管理スタックが UEFI ハードウェアレベルまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-108">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="557f6-109">DFCI は、ゼロタッチプロビジョニングをサポートします。 BIOS パスワードを除去し、ブートオプションや内蔵周辺機器を含むセキュリティ設定の制御を提供して、今後高度なセキュリティシナリオの土台を固めることができます。</span><span class="sxs-lookup"><span data-stu-id="557f6-109">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="557f6-110">DFCI は、現在 Surface Pro 7、Surface Pro X、Surface Pc 3 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-110">DFCI is currently available for Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> <span data-ttu-id="557f6-111">詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="557f6-111">For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="557f6-112">Surface UEFI を開くメニュー</span><span class="sxs-lookup"><span data-stu-id="557f6-112">Open Surface UEFI menu</span></span>

<span data-ttu-id="557f6-113">システムの起動時に UEFI 設定を調整するには:</span><span class="sxs-lookup"><span data-stu-id="557f6-113">To adjust UEFI settings during system startup:</span></span>

1. <span data-ttu-id="557f6-114">Surface をシャットダウンして、約10秒待ってから、停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="557f6-114">Shut down your Surface and wait about 10 seconds to make sure it's off.</span></span>
2. <span data-ttu-id="557f6-115">**音量を上げる**ボタンを押したままにして、電源ボタンを押しながら離し**ます。**</span><span class="sxs-lookup"><span data-stu-id="557f6-115">Press and hold the **Volume-up** button  and - at the same time - press and release the **Power button.**</span></span>
3. <span data-ttu-id="557f6-116">Microsoft または Surface のロゴが画面に表示されたら、[UEFI] 画面が表示されるまで**音量を上げ**たままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="557f6-116">As the Microsoft or Surface logo appears on your screen, continue to hold the **Volume-up** button until the UEFI screen appears.</span></span>

## <span data-ttu-id="557f6-117">UEFI PC 情報ページ</span><span class="sxs-lookup"><span data-stu-id="557f6-117">UEFI PC information page</span></span>

<span data-ttu-id="557f6-118">[PC 情報] ページには、Surface デバイスに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-118">The PC information page includes detailed information about your Surface device:</span></span> 

- <span data-ttu-id="557f6-119">**モデル**– surface device のモデルがここに表示されます (surface Book 2 または surface Pro 7 など)。</span><span class="sxs-lookup"><span data-stu-id="557f6-119">**Model** – Your Surface device’s model will be displayed here, such as Surface Book 2 or Surface Pro 7.</span></span> <span data-ttu-id="557f6-120">デバイスの正確な構成 (プロセッサ、ディスク サイズ、メモリ サイズなど) は表示されません。</span><span class="sxs-lookup"><span data-stu-id="557f6-120">The exact configuration of your device is not shown, (such as processor, disk size, or memory size).</span></span> 
- <span data-ttu-id="557f6-121">**UUID** – このユニバーサル固有識別子の番号はデバイスに固有であり、展開または管理の際にデバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-121">**UUID** – This Universally Unique Identification number is specific to your device and is used to identify the device during deployment or management.</span></span> 

- <span data-ttu-id="557f6-122">**Serial Number** (シリアル番号) – この番号は、アセットのタグ付けやサポートでこの特定の Surface デバイスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-122">**Serial Number** – This number is used to identify this specific Surface device for asset tagging and support scenarios.</span></span>
- <span data-ttu-id="557f6-123">**Asset Tag** (アセット タグ) – アセット タグは、[アセット タグ ツール](https://docs.microsoft.com/surface/assettag)で Surface デバイスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="557f6-123">**Asset Tag** – The asset tag is assigned to the Surface device with the [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span></span> 

<span data-ttu-id="557f6-124">Surface デバイスのファームウェアに関する詳細情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-124">You will also find detailed information about the firmware of your Surface device.</span></span> <span data-ttu-id="557f6-125">Surface デバイスには複数の内部コンポーネントがあり、それぞれが異なるバージョンのファームウェアを実行しています。</span><span class="sxs-lookup"><span data-stu-id="557f6-125">Surface devices have several internal components that each run different versions of firmware.</span></span> <span data-ttu-id="557f6-126">次の各デバイスのファームウェア バージョンが、**[PC information]** (PC の情報) ページに表示されます (図 1 を参照)。</span><span class="sxs-lookup"><span data-stu-id="557f6-126">The firmware version of each of the following devices is displayed on the **PC information** page (as shown in Figure 1):</span></span> 

- <span data-ttu-id="557f6-127">System UEFI (システム UEFI)</span><span class="sxs-lookup"><span data-stu-id="557f6-127">System UEFI</span></span> 

- <span data-ttu-id="557f6-128">SAM Controller (SAM コントローラー)</span><span class="sxs-lookup"><span data-stu-id="557f6-128">SAM Controller</span></span> 

- <span data-ttu-id="557f6-129">Intel Management Engine (Intel 管理エンジン)</span><span class="sxs-lookup"><span data-stu-id="557f6-129">Intel Management Engine</span></span> 

- <span data-ttu-id="557f6-130">System Embedded Controller (システム埋め込みコントローラー)</span><span class="sxs-lookup"><span data-stu-id="557f6-130">System Embedded Controller</span></span> 

- <span data-ttu-id="557f6-131">Touch Firmware (タッチ ファームウェア)</span><span class="sxs-lookup"><span data-stu-id="557f6-131">Touch Firmware</span></span> 

![システム情報とファームウェアのバージョン情報](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*<span data-ttu-id="557f6-133">図 1.</span><span class="sxs-lookup"><span data-stu-id="557f6-133">Figure 1.</span></span> <span data-ttu-id="557f6-134">システム情報とファームウェアのバージョン情報</span><span class="sxs-lookup"><span data-stu-id="557f6-134">System information and firmware version information</span></span>*

<span data-ttu-id="557f6-135">Surface デバイスの最新のファームウェア バージョンに関する最新情報は、お使いのデバイスの「[Surface 更新履歴](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history)」で確認できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-135">You can find up-to-date information about the latest firmware version for your Surface device in the [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) for your device.</span></span> 

## <span data-ttu-id="557f6-136">UEFI セキュリティページ</span><span class="sxs-lookup"><span data-stu-id="557f6-136">UEFI Security page</span></span> 

![Surface UEFI のセキュリティ設定を構成する](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*<span data-ttu-id="557f6-138">図 2. </span><span class="sxs-lookup"><span data-stu-id="557f6-138">Figure 2.</span></span> <span data-ttu-id="557f6-139">Surface UEFI のセキュリティ設定を構成する</span><span class="sxs-lookup"><span data-stu-id="557f6-139">Configure Surface UEFI security settings</span></span>*

<span data-ttu-id="557f6-140">[セキュリティ] ページでは、UEFI 設定を保護するためのパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-140">The Security page allows you to set a password to protect UEFI settings.</span></span> <span data-ttu-id="557f6-141">Surface デバイスを UEFI で起動するときは、このパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="557f6-141">This password must be entered when you boot the Surface device to UEFI.</span></span> <span data-ttu-id="557f6-142">パスワードには、次の文字を含めることができます (図3を参照)。</span><span class="sxs-lookup"><span data-stu-id="557f6-142">The password can contain the following characters (as shown in Figure 3):</span></span> 

- <span data-ttu-id="557f6-143">大文字: A ～ Z</span><span class="sxs-lookup"><span data-stu-id="557f6-143">Uppercase letters: A-Z</span></span> 

- <span data-ttu-id="557f6-144">小文字: a ～ z</span><span class="sxs-lookup"><span data-stu-id="557f6-144">Lowercase letters: a-z</span></span> 

- <span data-ttu-id="557f6-145">数字: 1 ～ 0</span><span class="sxs-lookup"><span data-stu-id="557f6-145">Numbers: 1-0</span></span> 

- <span data-ttu-id="557f6-146">特殊文字:! @ # $% ^& \* ()? <>{} []-_ = + |.,;: ' ' "</span><span class="sxs-lookup"><span data-stu-id="557f6-146">Special characters: !@#$%^&\*()?<>{}[]-_=+|.,;:’\`”</span></span> 

<span data-ttu-id="557f6-147">パスワードは、6 文字以上にする必要があり、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-147">The password must be at least 6 characters and is case sensitive.</span></span> 

![Surface UEFI の設定を保護するためのパスワードを追加する](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*<span data-ttu-id="557f6-149">図 3. </span><span class="sxs-lookup"><span data-stu-id="557f6-149">Figure 3.</span></span> <span data-ttu-id="557f6-150">Surface UEFI の設定を保護するためのパスワードを追加する</span><span class="sxs-lookup"><span data-stu-id="557f6-150">Add a password to protect Surface UEFI settings</span></span>*

<span data-ttu-id="557f6-151">[Security] (セキュリティ) ページでは、Surface デバイスでのセキュア ブートの設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="557f6-151">On the Security page you can also change the configuration of Secure Boot on your Surface device.</span></span> <span data-ttu-id="557f6-152">セキュア ブート テクノロジは、承認されていないブート コードが Surface デバイスで起動できないようにして、ブートキット タイプやルートキット タイプのマルウェアの感染を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="557f6-152">Secure Boot technology prevents unauthorized boot code from booting on your Surface device, which protects against bootkit and rootkit-type malware infections.</span></span> <span data-ttu-id="557f6-153">セキュア ブートを無効にすると、サードパーティ製のオペレーティング システムやブート可能なメディアで Surface デバイスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-153">You can disable Secure Boot to allow your Surface device to boot third-party operating systems or bootable media.</span></span> <span data-ttu-id="557f6-154">図4に示すように、サードパーティの証明書を使用するために、セキュアブートを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="557f6-154">You can also configure Secure Boot to work with third-party certificates, as shown in Figure 4.</span></span> <span data-ttu-id="557f6-155">詳しくは、TechNet ライブラリの「[セキュア ブート](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="557f6-155">Read more about [Secure Boot](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) in the TechNet Library.</span></span>

![セキュア ブートを設定する](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*<span data-ttu-id="557f6-157">図 4: </span><span class="sxs-lookup"><span data-stu-id="557f6-157">Figure 4.</span></span> <span data-ttu-id="557f6-158">セキュア ブートを設定する</span><span class="sxs-lookup"><span data-stu-id="557f6-158">Configure Secure Boot</span></span>*

<span data-ttu-id="557f6-159">お使いのデバイスによっては、TPM が有効か無効かを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="557f6-159">Depending on your device, you may also be able to see if your TPM is enabled or disabled.</span></span> <span data-ttu-id="557f6-160">[ **Tpm を有効にする**] 設定が表示されない場合は、「Windows で tpm を開く」を参照して、状態を確認してください (図 5)。</span><span class="sxs-lookup"><span data-stu-id="557f6-160">If you do not see the **Enable TPM**  setting, open tpm.msc in Windows to check the status, as shown in Figure 5.</span></span> <span data-ttu-id="557f6-161">TPM は、BitLocker によるデバイスのデータの暗号化を認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-161">The TPM is used to authenticate encryption for your device’s data with BitLocker.</span></span> <span data-ttu-id="557f6-162">詳細については、「 [BitLocker の概要](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="557f6-162">To learn more, see [BitLocker overview](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span></span> 

![TPM コンソール](images/manage-surface-uefi-fig5-a.png "TPM console")

*<span data-ttu-id="557f6-164">図 5: </span><span class="sxs-lookup"><span data-stu-id="557f6-164">Figure 5.</span></span> <span data-ttu-id="557f6-165">TPM コンソール</span><span class="sxs-lookup"><span data-stu-id="557f6-165">TPM console</span></span>*


## <span data-ttu-id="557f6-166">UEFI メニュー: デバイス</span><span class="sxs-lookup"><span data-stu-id="557f6-166">UEFI menu: Devices</span></span> 

<span data-ttu-id="557f6-167">[デバイス] ページでは、次のような特定のデバイスとコンポーネントを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="557f6-167">The Devices page allows you to  enable or disable specific devices and components including:</span></span>

- <span data-ttu-id="557f6-168">ドッキング ポートと USB ポート</span><span class="sxs-lookup"><span data-stu-id="557f6-168">Docking and USB Ports</span></span> 

- <span data-ttu-id="557f6-169">MicroSD スロットと SD カード スロット</span><span class="sxs-lookup"><span data-stu-id="557f6-169">MicroSD or SD Card Slot</span></span> 

- <span data-ttu-id="557f6-170">背面カメラ</span><span class="sxs-lookup"><span data-stu-id="557f6-170">Rear Camera</span></span> 

- <span data-ttu-id="557f6-171">前面カメラ</span><span class="sxs-lookup"><span data-stu-id="557f6-171">Front Camera</span></span> 

- <span data-ttu-id="557f6-172">赤外線 (IR) カメラ</span><span class="sxs-lookup"><span data-stu-id="557f6-172">Infrared (IR) Camera</span></span> 

- <span data-ttu-id="557f6-173">Wi-Fi と Bluetooth</span><span class="sxs-lookup"><span data-stu-id="557f6-173">Wi-Fi and Bluetooth</span></span> 

- <span data-ttu-id="557f6-174">オンボード オーディオ (スピーカー、マイク)</span><span class="sxs-lookup"><span data-stu-id="557f6-174">Onboard Audio (Speakers and Microphone)</span></span> 

<span data-ttu-id="557f6-175">各デバイスは、図6に示すように、 **[オン**] (有効) または [**オフ**] (無効) の位置に移動できるスライダボタンと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-175">Each device is listed with a slider button that you can move to **On** (enabled) or **Off** (disabled) position, as shown in Figure 6.</span></span> 

![特定のデバイスを有効および無効にする](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*<span data-ttu-id="557f6-177">図 6. </span><span class="sxs-lookup"><span data-stu-id="557f6-177">Figure 6.</span></span> <span data-ttu-id="557f6-178">特定のデバイスを有効および無効にする</span><span class="sxs-lookup"><span data-stu-id="557f6-178">Enable and disable specific devices</span></span>*

## <span data-ttu-id="557f6-179">UEFI メニュー: ブート構成</span><span class="sxs-lookup"><span data-stu-id="557f6-179">UEFI menu: Boot configuration</span></span> 

<span data-ttu-id="557f6-180">[ブート構成] ページでは、ブートデバイスの順序を変更したり、次のデバイスの起動を有効または無効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="557f6-180">The Boot Configuration page allows you to change the order of your boot devices as well as enable or disable boot of the following devices:</span></span> 

- <span data-ttu-id="557f6-181">Windows ブート マネージャー</span><span class="sxs-lookup"><span data-stu-id="557f6-181">Windows Boot Manager</span></span> 

- <span data-ttu-id="557f6-182">USB 記憶装置</span><span class="sxs-lookup"><span data-stu-id="557f6-182">USB Storage</span></span> 

- <span data-ttu-id="557f6-183">PXE ネットワーク</span><span class="sxs-lookup"><span data-stu-id="557f6-183">PXE Network</span></span> 

- <span data-ttu-id="557f6-184">内部ストレージ</span><span class="sxs-lookup"><span data-stu-id="557f6-184">Internal Storage</span></span> 

<span data-ttu-id="557f6-185">特定のデバイスからすぐに起動するか、またはタッチスクリーンを使って一覧でそのデバイスのエントリを左へスワイプすることができます。</span><span class="sxs-lookup"><span data-stu-id="557f6-185">You can boot from a specific device immediately, or you can swipe left on that device’s entry in the list using the touchscreen.</span></span> <span data-ttu-id="557f6-186">また、Surface デバイスが **[音量を下げる]** ボタンと **[電源]** ボタンを同時に押すことによって電源をオフにされている場合は、USB デバイスまたは USB イーサネット アダプターですぐに起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="557f6-186">You can also boot immediately to a USB device or USB Ethernet adapter when the Surface device is powered off by pressing the **Volume Down** button and the **Power** button simultaneously.</span></span> 

<span data-ttu-id="557f6-187">指定したブート順序を有効にするには、図7に示すように、[**代替のブートシーケンスを有効**にする] オプションを **[オン**] に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="557f6-187">For the specified boot order to take effect, you must set the **Enable Alternate Boot Sequence** option to **On**, as shown in Figure 7.</span></span> 

![Surface デバイスのブート順序を設定する](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*<span data-ttu-id="557f6-189">図 7.</span><span class="sxs-lookup"><span data-stu-id="557f6-189">Figure 7.</span></span> <span data-ttu-id="557f6-190">Surface デバイスのブート順序を設定する</span><span class="sxs-lookup"><span data-stu-id="557f6-190">Configure the boot order for your Surface device</span></span>* 

<span data-ttu-id="557f6-191">また、**[Enable IPv6 for PXE Network Boot]** (PXE ネットワーク ブートで IPv6 を有効にする) オプションを使用して、PXE に対する IPv6 のサポートを有効または無効にすることもできます。たとえば、PXE サーバーが IPv4 専用に設定されているときに、PXE を使用して Windows の展開を実行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="557f6-191">You can also turn on and off IPv6 support for PXE with the **Enable IPv6 for PXE Network Boot** option, for example when performing a Windows deployment using PXE where the PXE server is configured for IPv4 only.</span></span>  

## <span data-ttu-id="557f6-192">UEFI メニュー: 管理</span><span class="sxs-lookup"><span data-stu-id="557f6-192">UEFI menu: Management</span></span>
<span data-ttu-id="557f6-193">[管理] ページでは、Surface Pro 7、Surface Pro X、Surface Pc 3 などの適格なデバイスでゼロタッチの UEFI 管理とその他の機能の使用を管理できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-193">The Management page allows you to manage use of Zero Touch UEFI Management and other features on eligible devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

![<span data-ttu-id="557f6-194">ゼロタッチの UEFI 管理とその他の機能へのアクセスを管理する ( ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *図 8)。ゼロタッチの UEFI 管理およびその他の機能へのアクセスを管理する*</span><span class="sxs-lookup"><span data-stu-id="557f6-194">Manage access to Zero Touch UEFI Management and other features](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
*Figure 8. Manage access to Zero Touch UEFI Management and other features*</span></span> 


<span data-ttu-id="557f6-195">ゼロタッチ UEFI 管理では、「デバイスファームウェア構成インターフェイス (DFCI)」と呼ばれるデバイスプロファイルを使用して、UEFI 設定をリモートで管理できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-195">Zero Touch UEFI Management lets you remotely manage UEFI settings  by using a device profile within Intune called Device Firmware Configuration Interface (DFCI).</span></span> <span data-ttu-id="557f6-196">この設定を構成しない場合は、DFCI を使って適格なデバイスを管理する機能が [**準備完了**] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-196">If you do not configure this setting, the ability to manage eligible devices with DFCI is set to **Ready**.</span></span> <span data-ttu-id="557f6-197">DFCI を無効にするには、[**オプトアウト**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="557f6-197">To prevent DFCI, select **Opt-Out**.</span></span> 

> [!NOTE]
> <span data-ttu-id="557f6-198">[UEFI 管理の設定] ページと DFCI の使用は、Surface Pro 7、Surface Pro X、Surface ノートブック3でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="557f6-198">The UEFI Management settings page and use of DFCI is only available on Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

<span data-ttu-id="557f6-199">詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="557f6-199">For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="557f6-200">UEFI メニュー: 終了</span><span class="sxs-lookup"><span data-stu-id="557f6-200">UEFI menu: Exit</span></span> 

<span data-ttu-id="557f6-201">図9に示すように、[**終了**] ページの [**今すぐ再起動**] ボタンを使用して、UEFI の設定を終了します。</span><span class="sxs-lookup"><span data-stu-id="557f6-201">Use the **Restart Now** button on the **Exit** page to exit UEFI settings, as shown in Figure 9.</span></span> 

![Surface UEFI を終了してデバイスを再起動する](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*<span data-ttu-id="557f6-203">図 9.</span><span class="sxs-lookup"><span data-stu-id="557f6-203">Figure 9.</span></span> <span data-ttu-id="557f6-204">Surface UEFI を終了してデバイスを再起動するには [Restart Now] （今すぐ再起動） をクリックする</span><span class="sxs-lookup"><span data-stu-id="557f6-204">Click Restart Now to exit Surface UEFI and restart the device</span></span>*

## <span data-ttu-id="557f6-205">Surface UEFI のブート画面</span><span class="sxs-lookup"><span data-stu-id="557f6-205">Surface UEFI boot screens</span></span>

<span data-ttu-id="557f6-206">Surface デバイスのファームウェアを Windows Update か手動インストールを使って更新する場合、更新はすぐにデバイスに適用されず、次の再起動サイクルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-206">When you update Surface device firmware, by using either Windows Update or manual installation, the updates are not applied immediately to the device, but instead during the next reboot cycle.</span></span> <span data-ttu-id="557f6-207">Surface のファームウェアの更新プロセスについて詳しくは、「[Surface のドライバーおよびファームウェアの更新プログラムを管理する](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="557f6-207">You can find out more about the Surface firmware update process in [Manage Surface driver and firmware updates](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates).</span></span> <span data-ttu-id="557f6-208">ファームウェアの更新の進行状況は、各コンポーネントのファームウェアごとに色が分かれた進行状況バーで画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-208">The progress of the firmware update is displayed on a screen with progress bars of differing colors to indicate the firmware for each component.</span></span> <span data-ttu-id="557f6-209">各コンポーネントの進行状況バーは、図 9 ~ 18 に表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-209">Each component’s progress bar is shown in Figures 9 through 18.</span></span>

![青色の進行状況バーで表示される Surface UEFI のファームウェアの更新](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*<span data-ttu-id="557f6-211">図 10.</span><span class="sxs-lookup"><span data-stu-id="557f6-211">Figure 10.</span></span> <span data-ttu-id="557f6-212">青色の進行状況バーで表示される Surface UEFI のファームウェア更新</span><span class="sxs-lookup"><span data-stu-id="557f6-212">The Surface UEFI firmware update displays a blue progress bar</span></span>*

![緑色の進行状況バーで表示される System Embedded Controller のファームウェア](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*<span data-ttu-id="557f6-214">図 11.</span><span class="sxs-lookup"><span data-stu-id="557f6-214">Figure 11.</span></span> <span data-ttu-id="557f6-215">緑色の進行状況バーで表示される System Embedded Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="557f6-215">The System Embedded Controller firmware update displays a green progress bar</span></span>*

![オレンジの進行状況バーで表示される SAM Controller のファームウェアの更新](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*<span data-ttu-id="557f6-217">図 12.</span><span class="sxs-lookup"><span data-stu-id="557f6-217">Figure 12.</span></span> <span data-ttu-id="557f6-218">オレンジ色の進行状況バーで表示される SAM Controller のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="557f6-218">The SAM Controller firmware update displays an orange progress bar</span></span>*

![赤色の進行状況バーで表示される Intel Management Engine のファームウェア](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*<span data-ttu-id="557f6-220">図 13.</span><span class="sxs-lookup"><span data-stu-id="557f6-220">Figure 13.</span></span> <span data-ttu-id="557f6-221">赤色の進行状況バーで表示される Intel Management Engine のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="557f6-221">The Intel Management Engine firmware update displays a red progress bar</span></span>*

![灰色の進行状況バーで表示される Surface Touch のファームウェア](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*<span data-ttu-id="557f6-223">図 14.</span><span class="sxs-lookup"><span data-stu-id="557f6-223">Figure 14.</span></span> <span data-ttu-id="557f6-224">灰色の進行状況バーで表示される Surface Touch のファームウェアの更新</span><span class="sxs-lookup"><span data-stu-id="557f6-224">The Surface touch firmware update displays a gray progress bar</span></span>*

![淡い緑の進行状況バーが表示された Surface キープファームウェア](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*<span data-ttu-id="557f6-226">図 15.</span><span class="sxs-lookup"><span data-stu-id="557f6-226">Figure 15.</span></span> <span data-ttu-id="557f6-227">Surface キープファームウェア更新プログラムには、薄い緑色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="557f6-227">The Surface KIP firmware update displays a light green progress bar</span></span>*

![ピンク色の進行状況バーが表示された Surface の赤のファームウェア](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*<span data-ttu-id="557f6-229">図 16 Surface の "ファームウェア更新プログラム" に明るいピンクの進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="557f6-229">Figure 16 The Surface ISH firmware update displays a light pink progress bar</span></span>*

![Surface トラックパッドファームウェアと灰色の進行状況バー](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*<span data-ttu-id="557f6-231">図 17.</span><span class="sxs-lookup"><span data-stu-id="557f6-231">Figure 17.</span></span> <span data-ttu-id="557f6-232">Surface トラックパッドファームウェア更新プログラムにより、ピンクの進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="557f6-232">The Surface Trackpad firmware update displays a pink progress bar</span></span>*

![薄い灰色の進行状況バーが表示されたファームウェアの Surface tc](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*<span data-ttu-id="557f6-234">図 18.</span><span class="sxs-lookup"><span data-stu-id="557f6-234">Figure 18.</span></span> <span data-ttu-id="557f6-235">ファームウェア更新プログラムの Surface TCON 淡い灰色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="557f6-235">The Surface TCON firmware update displays a light gray progress bar</span></span>*


![Surface TPM ファームウェアと明るい紫色の進行状況バー](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*<span data-ttu-id="557f6-237">図 19: </span><span class="sxs-lookup"><span data-stu-id="557f6-237">Figure 19.</span></span> <span data-ttu-id="557f6-238">Surface TPM ファームウェア更新プログラムによって紫色の進行状況バーが表示される</span><span class="sxs-lookup"><span data-stu-id="557f6-238">The Surface TPM firmware update displays a purple progress bar</span></span>*


>[!NOTE]
><span data-ttu-id="557f6-239">図19に示すように、セキュアブートが無効であることを示す追加の警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="557f6-239">An additional warning message that indicates Secure Boot is disabled is displayed, as shown in Figure 19.</span></span>

![セキュア ブートが無効になっていることを示す Surface のブート画面](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*<span data-ttu-id="557f6-241">図 20.</span><span class="sxs-lookup"><span data-stu-id="557f6-241">Figure 20.</span></span> <span data-ttu-id="557f6-242">Surface UEFI の設定でセキュア ブートが無効になっていることを示す Surface のブート画面</span><span class="sxs-lookup"><span data-stu-id="557f6-242">Surface boot screen that indicates Secure Boot has been disabled in Surface UEFI settings</span></span>*

## <span data-ttu-id="557f6-243">関連トピック</span><span class="sxs-lookup"><span data-stu-id="557f6-243">Related topics</span></span>

- [<span data-ttu-id="557f6-244">Surface UEFI の設定の Intune 管理</span><span class="sxs-lookup"><span data-stu-id="557f6-244">Intune management of Surface UEFI settings</span></span>](surface-manage-dfci-guide.md)

-  [<span data-ttu-id="557f6-245">Surface エンタープライズ管理モード</span><span class="sxs-lookup"><span data-stu-id="557f6-245">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
