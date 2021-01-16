---
title: SEMM を使用して Surface デバイスを登録および構成する (Surface)
description: Surface UEFI 構成パッケージを作成して Surface UEFI の設定を制御する方法と、SEMM に Surface デバイスを登録する方法について説明します。
keywords: Surface Enterprise の管理
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: hachinda
manager: laurawi
ms.date: 1/15/2021
ms.openlocfilehash: f310b4a43a8a0fc0e77295344ac723770ce821bc
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271064"
---
# <span data-ttu-id="7d06b-104">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="7d06b-104">Enroll and configure Surface devices with SEMM</span></span>

<span data-ttu-id="7d06b-105">Microsoft Surface Enterprise 管理モード (SEMM) を使用すると、Surface デバイスで Surface UEFI の設定を安全に構成し、組織内の Surface デバイスでそれらの設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-105">With Microsoft Surface Enterprise Management Mode (SEMM), you can securely configure the settings of Surface UEFI on a Surface device and manage those settings on Surface devices in your organization.</span></span> <span data-ttu-id="7d06b-106">SURFACE デバイスが SEMM によって管理されている場合、そのデバイスは登録 *されている* (アクティブ化とも呼ばれる) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-106">When a Surface device is managed by SEMM, that device is considered to be *enrolled* (sometimes referred to as activated).</span></span> <span data-ttu-id="7d06b-107">この記事では、Surface UEFI の設定を制御するだけでなく、SEMM に Surface デバイスを登録する Surface UEFI 構成パッケージを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-107">This article shows you how to create a Surface UEFI configuration package that will not only control the settings of Surface UEFI, but will also enroll a Surface device in SEMM.</span></span>

<span data-ttu-id="7d06b-108">SEMM の概要については、「Microsoft Surface Enterprise 管理モード」 [を参照してください](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-108">For a more high-level overview of SEMM, see [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).</span></span>

<span data-ttu-id="7d06b-109">SEMM の代わりに、新しい Surface デバイスは、Microsoft Intune を介したファームウェア設定のサブセットのリモート管理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-109">As an alternative to SEMM, newer Surface devices support remote management of a subset of firmware settings via Microsoft Intune.</span></span> <span data-ttu-id="7d06b-110">詳しくは [、Surface UEFI 設定の Intune 管理に関するページをご覧ください](surface-manage-dfci-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-110">For more information,refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7d06b-111">SEMM は、UEFI マネージャーを介して Surface Pro X でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-111">SEMM is supported on Surface Pro X via the UEFI Manager only.</span></span> <span data-ttu-id="7d06b-112">詳細については、「Surface Pro X の展開、管理、サービス提供」 [を参照してください](surface-pro-arm-app-management.md)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-112">For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>

#### <span data-ttu-id="7d06b-113">Microsoft Surface UEFI コンフィエーターをダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="7d06b-113">Download and install Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="7d06b-114">SEMM パッケージの作成に使用されるツールは、Microsoft Surface UEFI コンフィエーターです。</span><span class="sxs-lookup"><span data-stu-id="7d06b-114">The tool used to create SEMM packages is Microsoft Surface UEFI Configurator.</span></span> <span data-ttu-id="7d06b-115">Microsoft Surface UEFI コンフィエーターは [、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703) ダウンロード センターの Surface Tools for IT ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-115">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>
<span data-ttu-id="7d06b-116">Microsoft Surface UEFI Configurator Windows インストーラー (.msi) ファイルを実行して、ツールのインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-116">Run the Microsoft Surface UEFI Configurator Windows Installer (.msi) file to start the installation of the tool.</span></span> <span data-ttu-id="7d06b-117">インストーラーが完了したら、スタート メニューの [すべてのアプリ] セクションで Microsoft Surface UEFI コンフィエーターを探します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-117">When the installer completes, find Microsoft Surface UEFI Configurator in the All Apps section of your Start menu.</span></span>

>[!NOTE]
><span data-ttu-id="7d06b-118">Microsoft Surface UEFI コンフィエーターは、Windows 10 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d06b-118">Microsoft Surface UEFI Configurator is supported only on Windows 10.</span></span>

## <span data-ttu-id="7d06b-119">Surface UEFI 構成パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="7d06b-119">Create a Surface UEFI configuration package</span></span>

<span data-ttu-id="7d06b-120">Surface UEFI 構成パッケージは、SEMM で管理される Surface デバイスに Surface UEFI 設定の新しい構成を適用する役割と、SEMM に Surface デバイスを登録する役割の両方を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-120">The Surface UEFI configuration package performs both the role of applying a new configuration of Surface UEFI settings to a Surface device managed with SEMM and the role of enrolling Surface devices in SEMM.</span></span> <span data-ttu-id="7d06b-121">構成パッケージを作成するには、各 Surface デバイスで UEFI 設定の構成をセキュリティで保護するために、SEMM で使用する署名証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d06b-121">The creation of a configuration package requires you to have a signing certificate to be used with SEMM to secure the configuration of UEFI settings on each Surface device.</span></span> <span data-ttu-id="7d06b-122">SEMM 証明書の要件の詳細については、Microsoft Surface Enterprise 管理モード [を参照してください](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-122">For more information about the requirements for the SEMM certificate, see [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).</span></span>

<span data-ttu-id="7d06b-123">Surface UEFI 構成パッケージを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-123">To create a Surface UEFI configuration package, follow these steps:</span></span>

1. <span data-ttu-id="7d06b-124">スタート メニューから Microsoft Surface UEFI コンフィエーターを開きます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-124">Open Microsoft Surface UEFI Configurator from the Start menu.</span></span>
2. <span data-ttu-id="7d06b-125">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-125">Click **Start**.</span></span>
3. <span data-ttu-id="7d06b-126">図 1 **に示**すように、[構成パッケージ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-126">Click **Configuration Package**, as shown in Figure 1.</span></span>

   ![SEMM 登録用のパッケージを作成する](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *<span data-ttu-id="7d06b-128">図 1. </span><span class="sxs-lookup"><span data-stu-id="7d06b-128">Figure 1.</span></span> <span data-ttu-id="7d06b-129">SEMM の登録と構成用のパッケージを作成するには、[構成パッケージ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-129">Select Configuration Package to create a package for SEMM enrollment and configuration</span></span>*

4. <span data-ttu-id="7d06b-130">図 2 **に示** すように、[証明書の保護] をクリックして、エクスポートした証明書ファイルをプライベート キー (.pfx) と一緒に追加します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-130">Click **Certificate Protection** to add your exported certificate file with private key (.pfx), as shown in Figure 2.</span></span> <span data-ttu-id="7d06b-131">証明書ファイルの場所を参照し、ファイルを選択して **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-131">Browse to the location of your certificate file, select the file, and then click **OK**.</span></span>

   ![SEM 証明書と Surface UEFI パスワードを構成パッケージに追加する](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *<span data-ttu-id="7d06b-133">図 2. </span><span class="sxs-lookup"><span data-stu-id="7d06b-133">Figure 2.</span></span> <span data-ttu-id="7d06b-134">SEMM 証明書と Surface UEFI パスワードを Surface UEFI 構成パッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="7d06b-134">Add the SEMM certificate and Surface UEFI password to a Surface UEFI configuration package</span></span>*

5. <span data-ttu-id="7d06b-135">証明書のパスワードの確認を求めるメッセージが表示されたら、証明書ファイルのパスワードを入力して確認し **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-135">When you are prompted to confirm the certificate password, enter and confirm the password for your certificate file, and then click **OK**.</span></span>
6. <span data-ttu-id="7d06b-136">パスワード **保護をクリック** して、Surface UEFI にパスワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-136">Click **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="7d06b-137">このパスワードは、UEFI を起動するたびに必要になります。</span><span class="sxs-lookup"><span data-stu-id="7d06b-137">This password will be required whenever you boot to UEFI.</span></span> <span data-ttu-id="7d06b-138">このパスワードを入力しない場合は **、PC**情報 、[ **会社**情報]、[ **エンタープライズ**管理]、および [ **終了** ] ページだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-138">If this password is not entered, only the **PC information**, **About**, **Enterprise management**, and **Exit** pages will be displayed.</span></span> <span data-ttu-id="7d06b-139">この手順は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7d06b-139">This step is optional.</span></span>
7. <span data-ttu-id="7d06b-140">メッセージが表示されたら、選択した Surface UEFI のパスワードを入力して確認し **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-140">When you are prompted, enter and confirm your chosen password for Surface UEFI, and then click **OK**.</span></span> <span data-ttu-id="7d06b-141">既存の Surface UEFI パスワードをクリアする場合は、パスワード フィールドを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-141">If you want to clear an existing Surface UEFI password, leave the password field blank.</span></span>
8. <span data-ttu-id="7d06b-142">Surface UEFI パッケージを特定のデバイスに適用しない場合は、[ターゲットにする**Surface**の種類の選択] ページで、対応する Surface Book または Surface Pro 4 イメージの下にある\*\*\*\* スライダーをクリックして、オフの位置に配置します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-142">If you do not want the Surface UEFI package to apply to a particular device, on the **Choose which Surface type you want to target** page, click the slider beneath the corresponding Surface Book or Surface Pro 4 image so that it is in the **Off** position.</span></span> <span data-ttu-id="7d06b-143">(図 3 に示すように)</span><span class="sxs-lookup"><span data-stu-id="7d06b-143">(As shown in Figure 3.)</span></span>
   > [!NOTE] 
   > <span data-ttu-id="7d06b-144">既定では、デバイスを選択する必要があります。デバイスは選択されません。</span><span class="sxs-lookup"><span data-stu-id="7d06b-144">You must select a device as none are selected by default.</span></span>

   ![パッケージ互換性のためにデバイスを選択する](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *<span data-ttu-id="7d06b-146">図 3. </span><span class="sxs-lookup"><span data-stu-id="7d06b-146">Figure 3.</span></span> <span data-ttu-id="7d06b-147">パッケージの互換性を確保するデバイスを選択する</span><span class="sxs-lookup"><span data-stu-id="7d06b-147">Choose the devices for package compatibility</span></span>*

9. <span data-ttu-id="7d06b-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-148">Click **Next**.</span></span>
10. <span data-ttu-id="7d06b-149">管理対象 Surface デバイスでコンポーネントを非アクティブ化する場合は、[\*\*\*\* アクティブ化または非アクティブ化するコンポーネントの選択] ページで、非アクティブ化するデバイスまたはデバイスのグループの横にあるスライダーをクリックして、スライダーが**オフ**の位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-149">If you want to deactivate a component on managed Surface devices, on the **Choose which components you want to activate or deactivate** page, click the slider next to any device or group of devices you want to deactivate so that the slider is in the **Off** position.</span></span> <span data-ttu-id="7d06b-150">(図 4 を参照)。各デバイスの既定の構成は **オンです**。</span><span class="sxs-lookup"><span data-stu-id="7d06b-150">(Shown in Figure 4.) The default configuration for each device is **On**.</span></span> <span data-ttu-id="7d06b-151">すべてのスライダー **を既定** の位置に戻す場合は、[リセット] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-151">Click the **Reset** button if you want to return all sliders to the default position.</span></span>

    ![Surface コンポーネントを無効または有効にする](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *<span data-ttu-id="7d06b-153">図 4: </span><span class="sxs-lookup"><span data-stu-id="7d06b-153">Figure 4.</span></span> <span data-ttu-id="7d06b-154">個々の Surface コンポーネントを無効または有効にする</span><span class="sxs-lookup"><span data-stu-id="7d06b-154">Disable or enable individual Surface components</span></span>*

11. <span data-ttu-id="7d06b-155">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-155">Click **Next**.</span></span>
12. <span data-ttu-id="7d06b-156">Surface UEFI または Surface UEFI ページの表示で高度なオプションを有効\*\*\*\* または無効にするには、[デバイスの詳細設定の選択] ページで、目的の設定の横にあるスライダーをクリックして、そのオプションを**オン**または**オフに構成**します (図 5 を参照)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-156">To enable or disable advanced options in Surface UEFI or the display of Surface UEFI pages, on the **Choose the advanced settings for your devices** page, click the slider beside the desired setting to configure that option to **On** or **Off** (shown in Figure 5).</span></span> <span data-ttu-id="7d06b-157">**UEFI**フロント ページ セクションでは、セキュリティ、デバイス、ブートのスライダー\*\*\*\* を使って\*\*\*\*、Surface UEFI で起動するユーザーが利用できるページを制御できます。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7d06b-157">In the **UEFI Front Page** section, you can use the sliders for **Security**, **Devices**, and **Boot** to control what pages are available to users who boot into Surface UEFI.</span></span> <span data-ttu-id="7d06b-158">(Surface UEFI の設定について詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings))。パッケージ **を生成** して保存するオプションの選択が完了したら、[ビルド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d06b-158">(For more information about Surface UEFI settings, see [Manage Surface UEFI settings](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings).) Click **Build** when you have finished selecting options to generate and save the package.</span></span>

    ![高度な Surface UEFI 設定と Surface UEFI ページの制御](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *<span data-ttu-id="7d06b-160">図 5: </span><span class="sxs-lookup"><span data-stu-id="7d06b-160">Figure 5.</span></span> <span data-ttu-id="7d06b-161">SEMM による高度な Surface UEFI 設定と Surface UEFI ページの制御</span><span class="sxs-lookup"><span data-stu-id="7d06b-161">Control advanced Surface UEFI settings and Surface UEFI pages with SEMM</span></span>*

13. <span data-ttu-id="7d06b-162">[名前 **を付けて** 保存] ダイアログ ボックスで、Surface UEFI 構成パッケージの名前を指定し、ファイルを保存する場所を参照して、[保存] をクリック **します**。</span><span class="sxs-lookup"><span data-stu-id="7d06b-162">In the **Save As** dialog box, specify a name for the Surface UEFI configuration package, browse to the location where you would like to save the file, and then click **Save**.</span></span>
14. <span data-ttu-id="7d06b-163">パッケージを作成して保存すると、[成功] **ページ** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-163">When the package is created and saved, the **Successful** page is displayed.</span></span>

>[!NOTE]
><span data-ttu-id="7d06b-164">図 6 に示すように、このページに表示される証明書の拇印文字を記録します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-164">Record the certificate thumbprint characters that are displayed on this page, as shown in Figure 6.</span></span> <span data-ttu-id="7d06b-165">SEMM での新しい Surface デバイスの登録を確認するには、これらの文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d06b-165">You will need these characters to confirm enrollment of new Surface devices in SEMM.</span></span> <span data-ttu-id="7d06b-166">**[End]** をクリックしてパッケージの作成を完了し、Microsoft Surface UEFI コンフィエーターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-166">Click **End** to complete package creation and close Microsoft Surface UEFI Configurator.</span></span>

![証明書の拇印文字の表示](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*<span data-ttu-id="7d06b-168">図 6. </span><span class="sxs-lookup"><span data-stu-id="7d06b-168">Figure 6.</span></span> <span data-ttu-id="7d06b-169">証明書の拇印の最後の 2 文字が [成功] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-169">The last two characters of the certificate thumbprint are displayed on the Successful page</span></span>*

<span data-ttu-id="7d06b-170">Surface UEFI 構成パッケージを作成したら、Surface デバイスを登録または構成できます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-170">Now that you have created your Surface UEFI configuration package, you can enroll or configure Surface devices.</span></span>

>[!NOTE]
><span data-ttu-id="7d06b-171">Surface UEFI 構成パッケージが作成されると、構成パッケージの設定とオプションの詳細を含むログ ファイルがデスクトップに作成されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-171">When a Surface UEFI configuration package is created, a log file is created on the desktop with details of the configuration package settings and options.</span></span>

## <span data-ttu-id="7d06b-172">SEMM での Surface デバイスの登録</span><span class="sxs-lookup"><span data-stu-id="7d06b-172">Enroll a Surface device in SEMM</span></span>
<span data-ttu-id="7d06b-173">Surface UEFI 構成パッケージが実行されると、SEMM 証明書と Surface UEFI 構成ファイルが Surface デバイスのファームウェア ストレージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-173">When the Surface UEFI configuration package is executed, the SEMM certificate and Surface UEFI configuration files are staged in the firmware storage of the Surface device.</span></span> <span data-ttu-id="7d06b-174">Surface デバイスが再起動すると、Surface UEFI がこれらのファイルを処理し、図 7 に示すように、Surface UEFI 構成の適用または SEMM での Surface デバイスの登録のプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-174">When the Surface device reboots, Surface UEFI processes these files and begins the process of applying the Surface UEFI configuration or enrolling the Surface device in SEMM, as shown in Figure 7.</span></span>

![Surface UEFI または登録の構成に関する SEMM プロセス](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*<span data-ttu-id="7d06b-176">図 7.</span><span class="sxs-lookup"><span data-stu-id="7d06b-176">Figure 7.</span></span> <span data-ttu-id="7d06b-177">Surface UEFI の構成または Surface デバイスの登録のための SEMM プロセス</span><span class="sxs-lookup"><span data-stu-id="7d06b-177">The SEMM process for configuration of Surface UEFI or enrollment of a Surface device</span></span>*

<span data-ttu-id="7d06b-178">SEMM に Surface デバイスを登録するプロセスを開始する前に、証明書の拇印の最後の 2 文字が手に入っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d06b-178">Before you begin the process to enroll a Surface device in SEMM, ensure that you have the last two characters of the certificate thumbprint on hand.</span></span> <span data-ttu-id="7d06b-179">デバイスの登録を確認するには、これらの文字が必要です (図 6 を参照)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-179">You will need these characters to confirm the device’s enrollment (see Figure 6).</span></span>

<span data-ttu-id="7d06b-180">SURFACE UEFI 構成パッケージを使用して SEMM に Surface デバイスを登録するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-180">To enroll a Surface device in SEMM with a Surface UEFI configuration package, follow these steps:</span></span>

1. <span data-ttu-id="7d06b-181">SEMM に登録する Surface デバイスで、Surface UEFI 構成パッケージ .msi ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-181">Run the Surface UEFI configuration package .msi file on the Surface device you want to enroll in SEMM.</span></span> <span data-ttu-id="7d06b-182">これにより、デバイスのファームウェアに Surface UEFI 構成ファイルがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-182">This will provision the Surface UEFI configuration file in the device’s firmware.</span></span>
2. <span data-ttu-id="7d06b-183">使用許諾契約書 **(EULA)** に同意するには、[使用許諾契約書に同意します] チェック ボックスをオンにし\*\*\*\*、[インストール] をクリックしてインストール プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-183">Select the **I accept the terms in the License Agreement** check box to accept the End User License Agreement (EULA), and then click **Install** to begin the installation process.</span></span>
3. <span data-ttu-id="7d06b-184">[ **完了]** をクリックして Surface UEFI 構成パッケージのインストールを完了し、実行するように求めるメッセージが表示されたら Surface デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-184">Click **Finish** to complete the Surface UEFI configuration package installation and restart the Surface device when you are prompted to do so.</span></span>
4. <span data-ttu-id="7d06b-185">Surface UEFI は構成ファイルを読み込み、SEMM がデバイスで有効になっていないと判断します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-185">Surface UEFI will load the configuration file and determine that SEMM is not enabled on the device.</span></span> <span data-ttu-id="7d06b-186">Surface UEFI は、次のように SEMM 登録プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-186">Surface UEFI will then begin the SEMM enrollment process, as follows:</span></span>
   * <span data-ttu-id="7d06b-187">Surface UEFI は、SEMM 構成ファイルに SEMM 証明書が含まれているか確認します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-187">Surface UEFI will verify that the SEMM configuration file contains a SEMM certificate.</span></span>
   * <span data-ttu-id="7d06b-188">図 8 に示すように、Surface UEFI は、SEMM での Surface デバイスの登録を確認するために、証明書の拇印の最後の 2 文字を入力するように求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-188">Surface UEFI will prompt you to enter the last two characters of the certificate thumbprint to confirm enrollment of the Surface device in SEMM, as shown in Figure 8.</span></span>

      ![SEMM 登録には、証明書の拇印の最後の 2 文字が必要です](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *<span data-ttu-id="7d06b-190">図 8.</span><span class="sxs-lookup"><span data-stu-id="7d06b-190">Figure 8.</span></span> <span data-ttu-id="7d06b-191">SEMM への登録には、証明書の拇印の最後の 2 文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d06b-191">Enrollment in SEMM requires the last two characters of the certificate thumbprint</span></span>*

   * <span data-ttu-id="7d06b-192">Surface UEFI は SEMM 証明書をファームウェアに格納し、Surface UEFI 構成ファイルで指定された構成設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-192">Surface UEFI will store the SEMM certificate in firmware and apply the configuration settings that are specified in the Surface UEFI configuration file.</span></span>
   
5. <span data-ttu-id="7d06b-193">Surface デバイスは SEMM に登録され、Windows で起動します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-193">The Surface device is now enrolled in SEMM and will boot to Windows.</span></span>

<span data-ttu-id="7d06b-194">**SEMM**に Surface デバイスが正常に登録されたことを確認するには、プログラムと機能 の**Microsoft Surface 構成**パッケージ (図 9 を参照)、またはイベント ビューアーの [アプリケーションとサービス ログ] (図\*\*\*\* 10 を参照) にある Microsoft **Surface UEFI**構成ログに格納されているイベントを探します。</span><span class="sxs-lookup"><span data-stu-id="7d06b-194">You can verify that a Surface device has been successfully enrolled in SEMM by looking for **Microsoft Surface Configuration Package** in **Programs and Features** (as shown in Figure 9), or in the events stored in the **Microsoft Surface UEFI Configurator** log, found under **Applications and Services Logs** in Event Viewer (as shown in Figure 10).</span></span>

![SEMM での Surface デバイスの登録を確認プログラムと機能](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*<span data-ttu-id="7d06b-196">図 9.</span><span class="sxs-lookup"><span data-stu-id="7d06b-196">Figure 9.</span></span> <span data-ttu-id="7d06b-197">SEMM での Surface デバイスの登録を確認プログラムと機能</span><span class="sxs-lookup"><span data-stu-id="7d06b-197">Verify the enrollment of a Surface device in SEMM in Programs and Features</span></span>*

![イベント ビューアーで SEMM に Surface デバイスの登録を確認する](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*<span data-ttu-id="7d06b-199">図 10.</span><span class="sxs-lookup"><span data-stu-id="7d06b-199">Figure 10.</span></span> <span data-ttu-id="7d06b-200">イベント ビューアーで SEMM で Surface デバイスの登録を確認する</span><span class="sxs-lookup"><span data-stu-id="7d06b-200">Verify the enrollment of a Surface device in SEMM in Event Viewer</span></span>*

<span data-ttu-id="7d06b-201">デバイスが Surface UEFI の SEMM に登録されているのを確認することもできます。デバイスが登録されている間、Surface UEFI には [ **エンタープライズ** 管理] ページが表示されます (図 11 を参照)。</span><span class="sxs-lookup"><span data-stu-id="7d06b-201">You can also verify that the device is enrolled in SEMM in Surface UEFI – while the device is enrolled, Surface UEFI will contain the **Enterprise management** page (as shown in Figure 11).</span></span>

![Surface UEFI Enterprise の管理ページ](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*<span data-ttu-id="7d06b-203">図 11.</span><span class="sxs-lookup"><span data-stu-id="7d06b-203">Figure 11.</span></span> <span data-ttu-id="7d06b-204">Surface UEFI Enterprise の管理ページ</span><span class="sxs-lookup"><span data-stu-id="7d06b-204">The Surface UEFI Enterprise management page</span></span>*


## <span data-ttu-id="7d06b-205">SEMM を使用して Surface UEFI の設定を構成する</span><span class="sxs-lookup"><span data-stu-id="7d06b-205">Configure Surface UEFI settings with SEMM</span></span>

<span data-ttu-id="7d06b-206">デバイスを SEMM に登録した後、同じ SEMM 証明書で署名された Surface UEFI 構成パッケージを実行して、新しい Surface UEFI 設定を適用できます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-206">After a device is enrolled in SEMM, you can run Surface UEFI configuration packages signed with the same SEMM certificate to apply new Surface UEFI settings.</span></span> <span data-ttu-id="7d06b-207">これらの設定は、次回デバイスが起動すると自動的に適用され、ユーザーによる操作は行われます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-207">These settings are applied automatically the next time the device boots, without any interaction from the user.</span></span> <span data-ttu-id="7d06b-208">Microsoft Endpoint Configuration Manager のようなアプリケーション展開ソリューションを使用して、Surface UEFI 構成パッケージを Surface デバイスに展開し、Surface UEFI の設定を変更または管理できます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-208">You can use application deployment solutions like Microsoft Endpoint Configuration Manager to deploy Surface UEFI configuration packages to Surface devices to change or manage the settings in Surface UEFI.</span></span>

<span data-ttu-id="7d06b-209">Configuration Manager で Windows インストーラー (.msi) ファイルを展開する方法の詳細については [、「Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959)を使ったアプリケーションの展開と管理」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d06b-209">For more information about how to deploy Windows Installer (.msi) files with Configuration Manager, see [Deploy and manage applications with Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959).</span></span>

<span data-ttu-id="7d06b-210">パスワードを使って Surface UEFI をセキュリティで保護した場合、パスワードを使わずに Surface UEFI を起動しようとするユーザーには **、PC**情報\*\*\*\*、**バージョン**情報、**エンタープライズ**管理、および終了ページだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-210">If you have secured Surface UEFI with a password, users without the password who attempt to boot to Surface UEFI will only have the **PC information**, **About**, **Enterprise management**, and **Exit** pages displayed to them.</span></span>

<span data-ttu-id="7d06b-211">パスワードを使って Surface UEFI をセキュリティで保護していない場合、またはユーザーがパスワードを正しく入力した場合、SEMM で構成されている設定は淡色表示 (利用不可) され、図 12 に示すように、組織で一部の設定が管理されているテキストがページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d06b-211">If you have not secured Surface UEFI with a password or a user enters the password correctly, settings that are configured with SEMM will be dimmed (unavailable) and the text Some settings are managed by your organization will be displayed at the top of the page, as shown in Figure 12.</span></span>

![SURFACE UEFI で SEMM によって管理される設定が無効になっている](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*<span data-ttu-id="7d06b-213">図 12.</span><span class="sxs-lookup"><span data-stu-id="7d06b-213">Figure 12.</span></span> <span data-ttu-id="7d06b-214">SEMM によって管理される設定は Surface UEFI で無効になります。</span><span class="sxs-lookup"><span data-stu-id="7d06b-214">Settings managed by SEMM will be disabled in Surface UEFI</span></span>*
