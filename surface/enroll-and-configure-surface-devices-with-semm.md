---
title: SEMM (Surface) を使って Surface デバイスを登録および構成する
description: Surface uefi の設定を制御する Surface UEFI 構成パッケージを作成する方法、および SEMM に Surface デバイスを登録する方法について説明します。
keywords: surface enterprise 管理
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 183eceee47eba8b8d1e794e9e7d3efffa7a9b2e0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835950"
---
# <span data-ttu-id="0274e-104">SEMM による Surface デバイスの登録と構成</span><span class="sxs-lookup"><span data-stu-id="0274e-104">Enroll and configure Surface devices with SEMM</span></span>

<span data-ttu-id="0274e-105">Microsoft Surface Enterprise Management Mode (SEMM) を使用すると、Surface デバイス上の Surface UEFI の設定を安全に構成し、組織内の Surface デバイスでそれらの設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="0274e-105">With Microsoft Surface Enterprise Management Mode (SEMM), you can securely configure the settings of Surface UEFI on a Surface device and manage those settings on Surface devices in your organization.</span></span> <span data-ttu-id="0274e-106">Surface デバイスが SEMM によって管理される場合、そのデバイスは*登録*されていると見なされます (アクティブ化と呼ばれることもあります)。</span><span class="sxs-lookup"><span data-stu-id="0274e-106">When a Surface device is managed by SEMM, that device is considered to be *enrolled* (sometimes referred to as activated).</span></span> <span data-ttu-id="0274e-107">この記事では、surface UEFI の設定のみを制御する Surface UEFI 構成パッケージを作成する方法について説明しますが、SEMM には Surface デバイスも登録します。</span><span class="sxs-lookup"><span data-stu-id="0274e-107">This article shows you how to create a Surface UEFI configuration package that will not only control the settings of Surface UEFI, but will also enroll a Surface device in SEMM.</span></span>

<span data-ttu-id="0274e-108">SEMM の大まかな概要については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0274e-108">For a more high-level overview of SEMM, see [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).</span></span>

<span data-ttu-id="0274e-109">Surface pro 7 のクラウドからファームウェアを管理するための合理化された方法です。 Surface Pro X と Surface のノート Pc 3 はパブリックプレビューで利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="0274e-109">A streamlined method of managing firmware from the cloud on Surface Pro 7,Surface Pro X and Surface Laptop 3 is now available via public preview.</span></span> <span data-ttu-id="0274e-110">詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0274e-110">For more information,refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0274e-111">SEMM は、UEFI Manager のみを通じて Surface Pro X でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0274e-111">SEMM is supported on Surface Pro X via the UEFI Manager only.</span></span> <span data-ttu-id="0274e-112">詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0274e-112">For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).</span></span>

#### <span data-ttu-id="0274e-113">Microsoft Surface UEFI コンフィギュレーターをダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="0274e-113">Download and install Microsoft Surface UEFI Configurator</span></span>
<span data-ttu-id="0274e-114">SEMM パッケージの作成に使用するツールは、Microsoft Surface UEFI コンフィギュレーターです。</span><span class="sxs-lookup"><span data-stu-id="0274e-114">The tool used to create SEMM packages is Microsoft Surface UEFI Configurator.</span></span> <span data-ttu-id="0274e-115">Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0274e-115">You can download Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>
<span data-ttu-id="0274e-116">Microsoft Surface UEFI Configurator Windows Installer (.msi) ファイルを実行して、ツールのインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="0274e-116">Run the Microsoft Surface UEFI Configurator Windows Installer (.msi) file to start the installation of the tool.</span></span> <span data-ttu-id="0274e-117">インストーラーが完了したら、[スタート] メニューの [すべてのアプリ] セクションで Microsoft Surface UEFI コンフィギュレーターを見つけます。</span><span class="sxs-lookup"><span data-stu-id="0274e-117">When the installer completes, find Microsoft Surface UEFI Configurator in the All Apps section of your Start menu.</span></span>

>[!NOTE]
><span data-ttu-id="0274e-118">Microsoft Surface UEFI コンフィギュレーターは、Windows 10 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0274e-118">Microsoft Surface UEFI Configurator is supported only on Windows 10.</span></span>

## <span data-ttu-id="0274e-119">Surface UEFI 構成パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="0274e-119">Create a Surface UEFI configuration package</span></span>

<span data-ttu-id="0274e-120">Surface UEFI 構成パッケージは、SEMM と共に管理される Surface デバイスと SEMM での surface device の役割の両方に、Surface UEFI の設定の新しい構成を適用する役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="0274e-120">The Surface UEFI configuration package performs both the role of applying a new configuration of Surface UEFI settings to a Surface device managed with SEMM and the role of enrolling Surface devices in SEMM.</span></span> <span data-ttu-id="0274e-121">構成パッケージを作成するには、各 Surface デバイスで UEFI 設定の構成をセキュリティで保護するために、SEMM と共に使用する署名証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="0274e-121">The creation of a configuration package requires you to have a signing certificate to be used with SEMM to secure the configuration of UEFI settings on each Surface device.</span></span> <span data-ttu-id="0274e-122">SEMM 証明書の要件の詳細については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0274e-122">For more information about the requirements for the SEMM certificate, see [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).</span></span>

<span data-ttu-id="0274e-123">Surface UEFI 構成パッケージを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0274e-123">To create a Surface UEFI configuration package, follow these steps:</span></span>

1. <span data-ttu-id="0274e-124">[スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。</span><span class="sxs-lookup"><span data-stu-id="0274e-124">Open Microsoft Surface UEFI Configurator from the Start menu.</span></span>
2. <span data-ttu-id="0274e-125">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-125">Click **Start**.</span></span>
3. <span data-ttu-id="0274e-126">図1に示すように、[**構成パッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-126">Click **Configuration Package**, as shown in Figure 1.</span></span>

   ![SEMM 登録用のパッケージを作成する](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *<span data-ttu-id="0274e-128">図 1. </span><span class="sxs-lookup"><span data-stu-id="0274e-128">Figure 1.</span></span> <span data-ttu-id="0274e-129">構成パッケージを選択して SEMM の登録と構成のパッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="0274e-129">Select Configuration Package to create a package for SEMM enrollment and configuration</span></span>*

4. <span data-ttu-id="0274e-130">[**証明書の保護**] をクリックして、図2に示すように、エクスポートされた証明書ファイルを秘密キー (.pfx) で追加します。</span><span class="sxs-lookup"><span data-stu-id="0274e-130">Click **Certificate Protection** to add your exported certificate file with private key (.pfx), as shown in Figure 2.</span></span> <span data-ttu-id="0274e-131">証明書ファイルの場所を参照し、ファイルを選択して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-131">Browse to the location of your certificate file, select the file, and then click **OK**.</span></span>

   ![SEM certificate and Surface UEFI パスワードを構成パッケージに追加する](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *<span data-ttu-id="0274e-133">図 2. </span><span class="sxs-lookup"><span data-stu-id="0274e-133">Figure 2.</span></span> <span data-ttu-id="0274e-134">SEMM 証明書と Surface UEFI パスワードを Surface UEFI 構成パッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="0274e-134">Add the SEMM certificate and Surface UEFI password to a Surface UEFI configuration package</span></span>*

5. <span data-ttu-id="0274e-135">証明書のパスワードを確認するように求められたら、証明書ファイルのパスワードを入力して確認し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-135">When you are prompted to confirm the certificate password, enter and confirm the password for your certificate file, and then click **OK**.</span></span>
6. <span data-ttu-id="0274e-136">[**パスワードによる保護**] をクリックして、Surface UEFI にパスワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0274e-136">Click **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="0274e-137">このパスワードは、UEFI を起動するたびに必要になります。</span><span class="sxs-lookup"><span data-stu-id="0274e-137">This password will be required whenever you boot to UEFI.</span></span> <span data-ttu-id="0274e-138">このパスワードが入力されていない場合は、 **PC 情報**、**バージョン**情報、**エンタープライズ管理**、**終了**ページのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-138">If this password is not entered, only the **PC information**, **About**, **Enterprise management**, and **Exit** pages will be displayed.</span></span> <span data-ttu-id="0274e-139">この手順は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0274e-139">This step is optional.</span></span>
7. <span data-ttu-id="0274e-140">メッセージが表示されたら、Surface UEFI 用に選択したパスワードを入力して確定し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-140">When you are prompted, enter and confirm your chosen password for Surface UEFI, and then click **OK**.</span></span> <span data-ttu-id="0274e-141">既存の Surface UEFI パスワードをクリアする場合は、パスワードフィールドを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="0274e-141">If you want to clear an existing Surface UEFI password, leave the password field blank.</span></span>
8. <span data-ttu-id="0274e-142">Surface UEFI パッケージを特定のデバイスに適用しない場合は、[**ターゲットにするサーフェスの種類を選択**] ページで、対応する surface Book または surface Pro 4 の画像の下にあるスライダーをクリックして、その位置が**オフ**になるようにします。</span><span class="sxs-lookup"><span data-stu-id="0274e-142">If you do not want the Surface UEFI package to apply to a particular device, on the **Choose which Surface type you want to target** page, click the slider beneath the corresponding Surface Book or Surface Pro 4 image so that it is in the **Off** position.</span></span> <span data-ttu-id="0274e-143">(図3に示すように)。</span><span class="sxs-lookup"><span data-stu-id="0274e-143">(As shown in Figure 3.)</span></span>
   > [!NOTE] 
   > <span data-ttu-id="0274e-144">既定では [なし] が選択されているため、デバイスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0274e-144">You must select a device as none are selected by default.</span></span>

   ![パッケージの互換性を維持するためのデバイスの選択](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *<span data-ttu-id="0274e-146">図 3. </span><span class="sxs-lookup"><span data-stu-id="0274e-146">Figure 3.</span></span> <span data-ttu-id="0274e-147">パッケージの互換性を維持するためのデバイスの選択</span><span class="sxs-lookup"><span data-stu-id="0274e-147">Choose the devices for package compatibility</span></span>*

9. <span data-ttu-id="0274e-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-148">Click **Next**.</span></span>
10. <span data-ttu-id="0274e-149">管理された Surface デバイスのコンポーネントを非アクティブ化する場合は、[**アクティブ化または非**アクティブ化するコンポーネントの選択] ページで、非アクティブ化するデバイスまたはデバイスのグループの横にあるスライダーをクリックして、スライダーが [**オフ**] の位置になるようにします。</span><span class="sxs-lookup"><span data-stu-id="0274e-149">If you want to deactivate a component on managed Surface devices, on the **Choose which components you want to activate or deactivate** page, click the slider next to any device or group of devices you want to deactivate so that the slider is in the **Off** position.</span></span> <span data-ttu-id="0274e-150">(図4に示されています)。各デバイスの既定の構成が**オンに**なっている。</span><span class="sxs-lookup"><span data-stu-id="0274e-150">(Shown in Figure 4.) The default configuration for each device is **On**.</span></span> <span data-ttu-id="0274e-151">すべてのスライダーを既定の位置に戻したい場合は、[**リセット**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-151">Click the **Reset** button if you want to return all sliders to the default position.</span></span>

    ![Surface コンポーネントを無効または有効にする](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *<span data-ttu-id="0274e-153">図 4: </span><span class="sxs-lookup"><span data-stu-id="0274e-153">Figure 4.</span></span> <span data-ttu-id="0274e-154">サーフェスコンポーネントを個別に無効または有効にする</span><span class="sxs-lookup"><span data-stu-id="0274e-154">Disable or enable individual Surface components</span></span>*

11. <span data-ttu-id="0274e-155">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-155">Click **Next**.</span></span>
12. <span data-ttu-id="0274e-156">Surface UEFI または Surface UEFI ページの表示で詳細オプションを有効または無効にするには、[**デバイスの詳細設定を選択**します] ページで、目的の設定の横にあるスライダーをクリックして、そのオプションを [**オン**] または [**オフ**] に設定します (図5を参照)。</span><span class="sxs-lookup"><span data-stu-id="0274e-156">To enable or disable advanced options in Surface UEFI or the display of Surface UEFI pages, on the **Choose the advanced settings for your devices** page, click the slider beside the desired setting to configure that option to **On** or **Off** (shown in Figure 5).</span></span> <span data-ttu-id="0274e-157">Uefi の [ **Front Page** ] セクションで、[**セキュリティ**、**デバイス**、**ブート**] のスライダーを使用して、Surface UEFI で起動したユーザーが利用できるページを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="0274e-157">In the **UEFI Front Page** section, you can use the sliders for **Security**, **Devices**, and **Boot** to control what pages are available to users who boot into Surface UEFI.</span></span> <span data-ttu-id="0274e-158">Surface UEFI の設定の詳細については、「 [SURFACE uefi の設定を管理](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)する」を参照してください。パッケージを生成および保存するオプションの選択が完了したら、[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-158">(For more information about Surface UEFI settings, see [Manage Surface UEFI settings](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings).) Click **Build** when you have finished selecting options to generate and save the package.</span></span>

    ![高度な Surface UEFI 設定と Surface UEFI ページの制御](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *<span data-ttu-id="0274e-160">図 5: </span><span class="sxs-lookup"><span data-stu-id="0274e-160">Figure 5.</span></span> <span data-ttu-id="0274e-161">SEMM で詳細 Surface UEFI 設定と Surface UEFI ページを制御する</span><span class="sxs-lookup"><span data-stu-id="0274e-161">Control advanced Surface UEFI settings and Surface UEFI pages with SEMM</span></span>*

13. <span data-ttu-id="0274e-162">[名前を**付けて保存**] ダイアログボックスで、Surface UEFI 構成パッケージの名前を指定し、ファイルを保存する場所を参照して、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0274e-162">In the **Save As** dialog box, specify a name for the Surface UEFI configuration package, browse to the location where you would like to save the file, and then click **Save**.</span></span>
14. <span data-ttu-id="0274e-163">パッケージが作成されて保存されると、**成功**したページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-163">When the package is created and saved, the **Successful** page is displayed.</span></span>

>[!NOTE]
><span data-ttu-id="0274e-164">図6に示すように、このページに表示される証明書の拇印文字を記録します。</span><span class="sxs-lookup"><span data-stu-id="0274e-164">Record the certificate thumbprint characters that are displayed on this page, as shown in Figure 6.</span></span> <span data-ttu-id="0274e-165">SEMM で新しい Surface デバイスの登録を確認するには、次の文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="0274e-165">You will need these characters to confirm enrollment of new Surface devices in SEMM.</span></span> <span data-ttu-id="0274e-166">[**終了**] をクリックしてパッケージの作成を完了し、MICROSOFT Surface UEFI コンフィギュレーターを終了します。</span><span class="sxs-lookup"><span data-stu-id="0274e-166">Click **End** to complete package creation and close Microsoft Surface UEFI Configurator.</span></span>

![証明書の拇印文字の表示](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*<span data-ttu-id="0274e-168">図 6. </span><span class="sxs-lookup"><span data-stu-id="0274e-168">Figure 6.</span></span> <span data-ttu-id="0274e-169">証明書の拇印の最後の2文字が、[成功] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-169">The last two characters of the certificate thumbprint are displayed on the Successful page</span></span>*

<span data-ttu-id="0274e-170">Surface UEFI 構成パッケージを作成したので、Surface デバイスを登録または構成することができます。</span><span class="sxs-lookup"><span data-stu-id="0274e-170">Now that you have created your Surface UEFI configuration package, you can enroll or configure Surface devices.</span></span>

>[!NOTE]
><span data-ttu-id="0274e-171">Surface UEFI 構成パッケージを作成すると、構成パッケージの設定とオプションの詳細を含むログファイルがデスクトップ上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-171">When a Surface UEFI configuration package is created, a log file is created on the desktop with details of the configuration package settings and options.</span></span>

## <span data-ttu-id="0274e-172">SEMM に Surface デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="0274e-172">Enroll a Surface device in SEMM</span></span>
<span data-ttu-id="0274e-173">Surface UEFI 構成パッケージが実行されると、SEMM 証明書と Surface UEFI 構成ファイルが Surface デバイスのファームウェアストレージにステージングされます。</span><span class="sxs-lookup"><span data-stu-id="0274e-173">When the Surface UEFI configuration package is executed, the SEMM certificate and Surface UEFI configuration files are staged in the firmware storage of the Surface device.</span></span> <span data-ttu-id="0274e-174">Surface デバイスが再起動すると、Surface UEFI によってこれらのファイルが処理され、Surface UEFI 構成の適用プロセスまたは SEMM での Surface デバイスの登録が開始されます (図7参照)。</span><span class="sxs-lookup"><span data-stu-id="0274e-174">When the Surface device reboots, Surface UEFI processes these files and begins the process of applying the Surface UEFI configuration or enrolling the Surface device in SEMM, as shown in Figure 7.</span></span>

![Surface UEFI または登録を構成するための SEMM プロセス](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*<span data-ttu-id="0274e-176">図 7.</span><span class="sxs-lookup"><span data-stu-id="0274e-176">Figure 7.</span></span> <span data-ttu-id="0274e-177">Surface UEFI または Surface デバイスの登録を構成するための SEMM プロセス</span><span class="sxs-lookup"><span data-stu-id="0274e-177">The SEMM process for configuration of Surface UEFI or enrollment of a Surface device</span></span>*

<span data-ttu-id="0274e-178">SEMM で Surface デバイスを登録するプロセスを開始する前に、証明書の拇印の最後の2文字が入力されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0274e-178">Before you begin the process to enroll a Surface device in SEMM, ensure that you have the last two characters of the certificate thumbprint on hand.</span></span> <span data-ttu-id="0274e-179">これらの文字は、デバイスの登録を確認するために必要です (図6を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0274e-179">You will need these characters to confirm the device’s enrollment (see Figure 6).</span></span>

<span data-ttu-id="0274e-180">Surface UEFI 構成パッケージを使用して Surface デバイスを SEMM に登録するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0274e-180">To enroll a Surface device in SEMM with a Surface UEFI configuration package, follow these steps:</span></span>

1. <span data-ttu-id="0274e-181">SEMM に登録する Surface デバイスで Surface UEFI 構成パッケージの .msi ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="0274e-181">Run the Surface UEFI configuration package .msi file on the Surface device you want to enroll in SEMM.</span></span> <span data-ttu-id="0274e-182">これにより、デバイスのファームウェアで Surface UEFI 構成ファイルがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="0274e-182">This will provision the Surface UEFI configuration file in the device’s firmware.</span></span>
2. <span data-ttu-id="0274e-183">[使用許諾契約書の**条項に同意**します] チェックボックスをオンにして、エンドユーザーライセンス契約 (EULA) に同意し、[**インストール**] をクリックしてインストールプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="0274e-183">Select the **I accept the terms in the License Agreement** check box to accept the End User License Agreement (EULA), and then click **Install** to begin the installation process.</span></span>
3. <span data-ttu-id="0274e-184">[**完了**] をクリックして surface UEFI 構成パッケージのインストールを完了し、画面の指示に従って surface デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="0274e-184">Click **Finish** to complete the Surface UEFI configuration package installation and restart the Surface device when you are prompted to do so.</span></span>
4. <span data-ttu-id="0274e-185">Surface UEFI は構成ファイルを読み込んで、デバイスで SEMM が有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0274e-185">Surface UEFI will load the configuration file and determine that SEMM is not enabled on the device.</span></span> <span data-ttu-id="0274e-186">Surface UEFI は、次のように SEMM 登録プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="0274e-186">Surface UEFI will then begin the SEMM enrollment process, as follows:</span></span>
   * <span data-ttu-id="0274e-187">Surface UEFI は、SEMM 構成ファイルに SEMM 証明書が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0274e-187">Surface UEFI will verify that the SEMM configuration file contains a SEMM certificate.</span></span>
   * <span data-ttu-id="0274e-188">Surface UEFI では、図8に示すように、SEMM で Surface デバイスの登録を確認するために、証明書拇印の最後の2文字を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="0274e-188">Surface UEFI will prompt you to enter the last two characters of the certificate thumbprint to confirm enrollment of the Surface device in SEMM, as shown in Figure 8.</span></span>

      ![SEMM 登録には、証明書の拇印の最後の2文字が必要](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *<span data-ttu-id="0274e-190">図 8.</span><span class="sxs-lookup"><span data-stu-id="0274e-190">Figure 8.</span></span> <span data-ttu-id="0274e-191">SEMM での登録には、証明書の拇印の最後の2文字が必要</span><span class="sxs-lookup"><span data-stu-id="0274e-191">Enrollment in SEMM requires the last two characters of the certificate thumbprint</span></span>*

   * <span data-ttu-id="0274e-192">Surface UEFI はファームウェアに SEMM 証明書を格納し、Surface UEFI 構成ファイルで指定されている構成設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="0274e-192">Surface UEFI will store the SEMM certificate in firmware and apply the configuration settings that are specified in the Surface UEFI configuration file.</span></span>
   
5. <span data-ttu-id="0274e-193">Surface デバイスが SEMM に登録され、Windows で起動します。</span><span class="sxs-lookup"><span data-stu-id="0274e-193">The Surface device is now enrolled in SEMM and will boot to Windows.</span></span>

<span data-ttu-id="0274e-194">(図9に示すように)**プログラムと機能**(図9に示す) では、[**アプリケーションとサービスログ**] の下に表示されている、 **microsoft surface** **構成パッケージ**を検索することで、surface デバイスが semm に正常に登録されたことを確認することができます (図10を参照)。</span><span class="sxs-lookup"><span data-stu-id="0274e-194">You can verify that a Surface device has been successfully enrolled in SEMM by looking for **Microsoft Surface Configuration Package** in **Programs and Features** (as shown in Figure 9), or in the events stored in the **Microsoft Surface UEFI Configurator** log, found under **Applications and Services Logs** in Event Viewer (as shown in Figure 10).</span></span>

![[プログラムと機能] で SEMM で Surface デバイスの登録を確認する](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*<span data-ttu-id="0274e-196">図 9.</span><span class="sxs-lookup"><span data-stu-id="0274e-196">Figure 9.</span></span> <span data-ttu-id="0274e-197">[プログラムと機能] で SEMM で Surface デバイスの登録を確認する</span><span class="sxs-lookup"><span data-stu-id="0274e-197">Verify the enrollment of a Surface device in SEMM in Programs and Features</span></span>*

![イベントビューアーの SEMM で Surface デバイスの登録を確認する](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*<span data-ttu-id="0274e-199">図 10.</span><span class="sxs-lookup"><span data-stu-id="0274e-199">Figure 10.</span></span> <span data-ttu-id="0274e-200">イベントビューアーの SEMM で Surface デバイスの登録を確認する</span><span class="sxs-lookup"><span data-stu-id="0274e-200">Verify the enrollment of a Surface device in SEMM in Event Viewer</span></span>*

<span data-ttu-id="0274e-201">また、デバイスが Surface UEFI の SEMM に登録されていることを確認することもできます。デバイスが登録されている間、Surface UEFI には、図11に示すように、[**エンタープライズ管理**] ページが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0274e-201">You can also verify that the device is enrolled in SEMM in Surface UEFI – while the device is enrolled, Surface UEFI will contain the **Enterprise management** page (as shown in Figure 11).</span></span>

![Surface UEFI Enterprise 管理ページ](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*<span data-ttu-id="0274e-203">図 11.</span><span class="sxs-lookup"><span data-stu-id="0274e-203">Figure 11.</span></span> <span data-ttu-id="0274e-204">Surface UEFI Enterprise 管理ページ</span><span class="sxs-lookup"><span data-stu-id="0274e-204">The Surface UEFI Enterprise management page</span></span>*


## <span data-ttu-id="0274e-205">SEMM を使用して Surface UEFI の設定を構成する</span><span class="sxs-lookup"><span data-stu-id="0274e-205">Configure Surface UEFI settings with SEMM</span></span>

<span data-ttu-id="0274e-206">デバイスが SEMM に登録されたら、同じ SEMM 証明書で署名された Surface UEFI 構成パッケージを実行して、新しい Surface UEFI 設定を適用できます。</span><span class="sxs-lookup"><span data-stu-id="0274e-206">After a device is enrolled in SEMM, you can run Surface UEFI configuration packages signed with the same SEMM certificate to apply new Surface UEFI settings.</span></span> <span data-ttu-id="0274e-207">これらの設定は、次回デバイスを起動したときに、ユーザーの操作なしで自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-207">These settings are applied automatically the next time the device boots, without any interaction from the user.</span></span> <span data-ttu-id="0274e-208">Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して、surface uefi 構成パッケージを surface デバイスに展開して、Surface UEFI の設定を変更または管理することができます。</span><span class="sxs-lookup"><span data-stu-id="0274e-208">You can use application deployment solutions like Microsoft Endpoint Configuration Manager to deploy Surface UEFI configuration packages to Surface devices to change or manage the settings in Surface UEFI.</span></span>

<span data-ttu-id="0274e-209">Configuration Manager を使用して Windows Installer (.msi) ファイルを展開する方法の詳細については、「 [Microsoft Endpoint Configuration manager を使用してアプリケーションを展開および管理](https://technet.microsoft.com/library/mt627959)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0274e-209">For more information about how to deploy Windows Installer (.msi) files with Configuration Manager, see [Deploy and manage applications with Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959).</span></span>

<span data-ttu-id="0274e-210">セキュリティで保護された Surface UEFI をパスワードで使用している場合、Surface UEFI を起動しようとしているパスワードを持たないユーザーには、 **PC 情報**、**バージョン**情報、**エンタープライズ管理**、**終了**ページのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-210">If you have secured Surface UEFI with a password, users without the password who attempt to boot to Surface UEFI will only have the **PC information**, **About**, **Enterprise management**, and **Exit** pages displayed to them.</span></span>

<span data-ttu-id="0274e-211">パスワードを使用して Surface UEFI をセキュリティで保護していない場合、またはユーザーがパスワードを正しく入力していない場合は、SEMM で構成されている設定は淡色 (使用不可) になり、組織で管理されている設定のテキストは、図12のように、ページ上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0274e-211">If you have not secured Surface UEFI with a password or a user enters the password correctly, settings that are configured with SEMM will be dimmed (unavailable) and the text Some settings are managed by your organization will be displayed at the top of the page, as shown in Figure 12.</span></span>

![Surface UEFI での SEMM によって管理されている設定](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*<span data-ttu-id="0274e-213">図 12.</span><span class="sxs-lookup"><span data-stu-id="0274e-213">Figure 12.</span></span> <span data-ttu-id="0274e-214">SEMM によって管理される設定は Surface UEFI で無効になります</span><span class="sxs-lookup"><span data-stu-id="0274e-214">Settings managed by SEMM will be disabled in Surface UEFI</span></span>*
