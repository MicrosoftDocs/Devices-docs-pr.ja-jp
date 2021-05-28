---
title: Microsoft Endpoint Configuration Manager を使用して SEMM (Surface) でデバイスを管理する
description: エンドポイント構成マネージャーを使用して、Microsoft Surface Enterprise Management Mode (SEMM) を管理する方法について説明します。
keywords: 登録、更新、スクリプト、設定
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2020
ms.openlocfilehash: 2d31f520d8c4da54f47b2b89b58b43e2cb983f1a
ms.sourcegitcommit: 7f5b97275fe301ef700f9c77954a1054e2e8d046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "11145618"
---
# <span data-ttu-id="e02d3-104">Microsoft Endpoint Configuration Manager を使用して SEMM によりデバイスを管理する</span><span class="sxs-lookup"><span data-stu-id="e02d3-104">Use Microsoft Endpoint Configuration Manager to manage devices with SEMM</span></span>

<span data-ttu-id="e02d3-105">Surface UEFI デバイスの Microsoft Surface Enterprise Management Mode (SEMM) 機能を使用すると、管理者は Surface UEFI 設定の構成を管理し、セキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-105">The Microsoft Surface Enterprise Management Mode (SEMM) feature of Surface UEFI devices lets administrators manage and help secure the configuration of Surface UEFI settings.</span></span> <span data-ttu-id="e02d3-106">ほとんどの組織では、このプロセスは、Microsoft Surface UEFI コンフィギュレーターツールを使って Windows Installer (.msi) パッケージを作成することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-106">For most organizations, this process is accomplished by creating Windows Installer (.msi) packages with the Microsoft Surface UEFI Configurator tool.</span></span> <span data-ttu-id="e02d3-107">次に、これらのパッケージを実行するか、クライアントサーフェスデバイスに展開して SEMM でデバイスを登録し、Surface UEFI 設定の構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-107">These packages are then run or deployed to the client Surface devices to enroll the devices in SEMM and to update the Surface UEFI settings configuration.</span></span>

<span data-ttu-id="e02d3-108">Microsoft Endpoint Configuration Manager を使用している組織では、Microsoft Surface UEFI Configurator のプロセスを使用して SEMM の展開と管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-108">For organizations with Microsoft Endpoint Configuration Manager there is an alternative to using the Microsoft Surface UEFI Configurator .msi process to deploy and administer SEMM.</span></span> <span data-ttu-id="e02d3-109">Microsoft Surface UEFI Manager は、SEMM 管理に必要なアセンブリをデバイスで利用できるようにするための軽量インストーラーです。</span><span class="sxs-lookup"><span data-stu-id="e02d3-109">Microsoft Surface UEFI Manager is a lightweight installer that makes required assemblies for SEMM management available on a device.</span></span> <span data-ttu-id="e02d3-110">マネージクライアントで Microsoft Surface UEFI Manager と共にこれらのアセンブリをインストールすることで、SEMM は、アプリケーションとして展開された PowerShell スクリプトを使って構成マネージャーによって管理できます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-110">By installing these assemblies with Microsoft Surface UEFI Manager on a managed client, SEMM can be administered by Configuration Manager with PowerShell scripts, deployed as applications.</span></span> <span data-ttu-id="e02d3-111">このプロセスでは、SEMM 管理は構成マネージャー内で実行されるため、外部の Microsoft Surface UEFI コンフィギュレーターツールの必要性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-111">With this process, SEMM management is performed within Configuration Manager, which eliminates the need for the external Microsoft Surface UEFI Configurator tool.</span></span>

> [!Note]
> <span data-ttu-id="e02d3-112">この記事で説明されているプロセスは、以前のバージョンのエンドポイント構成マネージャー、または他のサードパーティの管理ソリューションでも動作する可能性がありますが、Microsoft Surface UEFI Manager と PowerShell を使用した SEMM の管理は、エンドポイント構成マネージャーの現在の分岐でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-112">Although the process described in this article may work with earlier versions of Endpoint Configuration Manager or with other third-party management solutions, management of SEMM with Microsoft Surface UEFI Manager and PowerShell is supported only with the Current Branch of Endpoint Configuration Manager.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="e02d3-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="e02d3-113">Prerequisites</span></span>

<span data-ttu-id="e02d3-114">この記事で説明されている手順を開始する前に、次のテクノロジとツールについて理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-114">Before you begin the process outlined in this article, familiarize yourself with the following technologies and tools:</span></span>

* [<span data-ttu-id="e02d3-115">Surface UEFI</span><span class="sxs-lookup"><span data-stu-id="e02d3-115">Surface UEFI</span></span>](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)
* [<span data-ttu-id="e02d3-116">Surface エンタープライズ管理モード (SEMM)</span><span class="sxs-lookup"><span data-stu-id="e02d3-116">Surface Enterprise Management Mode (SEMM)</span></span>](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)
* [<span data-ttu-id="e02d3-117">PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="e02d3-117">PowerShell scripting</span></span>](https://technet.microsoft.com/scriptcenter/dd742419)
* [<span data-ttu-id="e02d3-118">System Center Configuration Manager アプリケーションの展開</span><span class="sxs-lookup"><span data-stu-id="e02d3-118">System Center Configuration Manager application deployment</span></span>](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)
* <span data-ttu-id="e02d3-119">証明書の管理</span><span class="sxs-lookup"><span data-stu-id="e02d3-119">Certificate management</span></span>

> [!Note]
> <span data-ttu-id="e02d3-120">また、SEMM の安全を確保するために使用する証明書へのアクセス権も必要になります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-120">You will also need access to the certificate that you intend to use to secure SEMM.</span></span> <span data-ttu-id="e02d3-121">この証明書の要件の詳細については、「 [Surface Enterprise 管理モードの証明書の要件](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-121">For details about the requirements for this certificate, see [Surface Enterprise Management Mode certificate requirements](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span>
> 
> <span data-ttu-id="e02d3-122">この証明書は安全な場所に保管し、適切にバックアップすることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-122">It is very important that this certificate be kept in a safe location and properly backed up.</span></span> <span data-ttu-id="e02d3-123">この証明書が失われたか、使用できなくなった場合は、Surface UEFI のリセット、マネージ Surface UEFI 設定の変更、または登録サーフェスデバイスからの SEMM の削除を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="e02d3-123">If this certificate becomes lost or unusable, it is not possible to reset Surface UEFI, change managed Surface UEFI settings, or remove SEMM from an enrolled Surface device.</span></span>

#### <span data-ttu-id="e02d3-124">Microsoft Surface UEFI Manager をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e02d3-124">Download Microsoft Surface UEFI Manager</span></span>

<span data-ttu-id="e02d3-125">構成マネージャーを使用した SEMM の管理では、各クライアントサーフェスデバイスに Microsoft Surface UEFI Manager をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-125">Management of SEMM with Configuration Manager requires the installation of Microsoft Surface UEFI Manager on each client Surface device.</span></span> <span data-ttu-id="e02d3-126">Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) は、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-126">You can download Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page on the Microsoft Download Center.</span></span>

#### <span data-ttu-id="e02d3-127">構成マネージャー用の SEMM スクリプトのダウンロード</span><span class="sxs-lookup"><span data-stu-id="e02d3-127">Download SEMM scripts for Configuration Manager</span></span>

<span data-ttu-id="e02d3-128">Microsoft Surface UEFI Manager がクライアント Surface デバイスにインストールされた後、SEMM は PowerShell スクリプトを使って展開および管理されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-128">After Microsoft Surface UEFI Manager is installed on the client Surface device, SEMM is deployed and managed with PowerShell scripts.</span></span> <span data-ttu-id="e02d3-129">[Semm 管理スクリプト](https://www.microsoft.com/download/details.aspx?id=46703)のサンプルは、ダウンロードセンターからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-129">You can download samples of the [SEMM management scripts](https://www.microsoft.com/download/details.aspx?id=46703) from the Download Center.</span></span>

## <a name="deploy-microsoft-surface-uefi-manager"></a><span data-ttu-id="e02d3-130">Microsoft Surface UEFI Manager を展開する</span><span class="sxs-lookup"><span data-stu-id="e02d3-130">Deploy Microsoft Surface UEFI Manager</span></span>

<span data-ttu-id="e02d3-131">Microsoft Surface UEFI Manager の展開は、一般的なアプリケーションの展開です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-131">Deployment of Microsoft Surface UEFI Manager is a typical application deployment.</span></span> <span data-ttu-id="e02d3-132">Microsoft Surface UEFI マネージャーのインストーラーファイルは、標準の [quiet オプション](https://msdn.microsoft.com/library/windows/desktop/aa367988)と共にインストールできる標準の Windows インストーラーファイルです。</span><span class="sxs-lookup"><span data-stu-id="e02d3-132">The Microsoft Surface UEFI Manager installer file is a standard Windows Installer file that you can install with the [standard quiet option](https://msdn.microsoft.com/library/windows/desktop/aa367988).</span></span>

<span data-ttu-id="e02d3-133">Microsoft Surface UEFI Manager をインストールするコマンドは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-133">The command to install Microsoft Surface UEFI Manager is as follows.</span></span>

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

<span data-ttu-id="e02d3-134">Microsoft Surface UEFI Manager をアンインストールするコマンドは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-134">The command to uninstall Microsoft Surface UEFI Manager is as follows.</span></span>

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

<span data-ttu-id="e02d3-135">新しいアプリケーションを作成し、それを Surface デバイスを含むコレクションに展開するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-135">To create a new application and deploy it to a collection that contains your Surface devices, perform the following steps:</span></span>

1. <span data-ttu-id="e02d3-136">**スタート**画面または [**スタート**] メニューから Configuration Manager コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-136">Open Configuration Manager Console from the **Start** screen or **Start** menu.</span></span>
2. <span data-ttu-id="e02d3-137">ウィンドウの左下隅にある [ **ソフトウェアライブラリ** ] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-137">Select **Software Library** in the bottom left corner of the window.</span></span>
3. <span data-ttu-id="e02d3-138">ソフトウェアライブラリの [ **アプリケーション管理** ] ノードを展開し、[ **アプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-138">Expand the **Application Management** node of the Software Library, and then select **Applications**.</span></span>
4. <span data-ttu-id="e02d3-139">ウィンドウの上部にある [**ホーム**] タブの [**アプリケーションの作成**] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-139">Select the **Create Application** button under the **Home** tab at the top of the window.</span></span> <span data-ttu-id="e02d3-140">これにより、アプリケーションの作成ウィザードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-140">This starts the Create Application Wizard.</span></span>
5. <span data-ttu-id="e02d3-141">アプリケーションの作成ウィザードでは、次の一連の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-141">The Create Application Wizard presents a series of steps:</span></span>

   * <span data-ttu-id="e02d3-142">**[全般** ]-[ **インストールファイルに関する情報を自動的に検出** する] オプションが既定で選択されています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-142">**General** – The **Automatically detect information about this application from installation files** option is selected by default.</span></span> <span data-ttu-id="e02d3-143">[ **種類** ] フィールドでは、既定で [ **Windows インストーラー (.msi ファイル)** ] も選択されています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-143">In the **Type** field, **Windows Installer (.msi file)** is also selected by default.</span></span> <span data-ttu-id="e02d3-144">[ **参照** ] を選択して移動し、[ **SurfaceUEFIManagerSetup.msi**] を選択して、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-144">Select **Browse** to navigate to and select **SurfaceUEFIManagerSetup.msi**, and then select **Next**.</span></span>
   
      > [!Note]
      > <span data-ttu-id="e02d3-145">SurfaceUEFIManagerSetup.msi の場所はネットワーク共有上にあり、他のファイルが含まれていないフォルダー内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-145">The location of SurfaceUEFIManagerSetup.msi must be on a network share and located in a folder that contains no other files.</span></span> <span data-ttu-id="e02d3-146">ローカルファイルの場所は使用できません。</span><span class="sxs-lookup"><span data-stu-id="e02d3-146">A local file location cannot be used.</span></span>

   * <span data-ttu-id="e02d3-147">**情報のインポート** –アプリケーションの作成ウィザードは、.msi ファイルを解析し、 **アプリケーション名** と **製品コード**を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-147">**Import Information** – The Create Application Wizard will parse the .msi file and read the **Application Name** and **Product Code**.</span></span> <span data-ttu-id="e02d3-148">図1のように、SurfaceUEFIManagerSetup.msi は、行の **コンテンツファイル**の下に唯一のファイルとして表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-148">SurfaceUEFIManagerSetup.msi should be listed as the only file under the line **Content Files**, as shown in Figure 1.</span></span> <span data-ttu-id="e02d3-149">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-149">Select **Next** to proceed.</span></span>

      ![Surface Manager のセットアップからの情報が自動的に解析される](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *<span data-ttu-id="e02d3-151">図 1. </span><span class="sxs-lookup"><span data-stu-id="e02d3-151">Figure 1.</span></span> <span data-ttu-id="e02d3-152">Microsoft Surface UEFI Manager のセットアップからの情報が自動的に解析される</span><span class="sxs-lookup"><span data-stu-id="e02d3-152">Information from Microsoft Surface UEFI Manager setup is automatically parsed</span></span>*

   * <span data-ttu-id="e02d3-153">**一般的な情報** : アプリケーションの名前や、発行元とバージョンに関する情報の変更、またはこのページへのコメントの追加を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-153">**General Information** – You can modify the name of the application and information about the publisher and version, or add comments on this page.</span></span> <span data-ttu-id="e02d3-154">Microsoft Surface UEFI Manager のインストールコマンドが、[インストールプログラム] フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-154">The installation command for Microsoft Surface UEFI Manager is displayed in the Installation Program field.</span></span> <span data-ttu-id="e02d3-155">システム用 Install の既定のインストール動作では、ユーザーが Surface デバイスにログオンしていない場合でも、Microsoft Surface UEFI Manager は SEMM に必要なアセンブリをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-155">The default installation behavior of Install for system will allow Microsoft Surface UEFI Manager to install the required assemblies for SEMM even if a user is not logged on to the Surface device.</span></span> <span data-ttu-id="e02d3-156">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-156">Select **Next** to proceed.</span></span>
   * <span data-ttu-id="e02d3-157">**概要** : **情報のインポート** 手順で解析された情報と、 **[一般的な情報** ] 手順で選択した情報が、このページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-157">**Summary** – The information that was parsed in the **Import Information** step and your selections from the **General Information** step is displayed on this page.</span></span> <span data-ttu-id="e02d3-158">[ **次へ** ] を選択して、選択内容を確認してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-158">Select **Next** to confirm your selections and create the application.</span></span>
   * <span data-ttu-id="e02d3-159">[**進行状況**]-アプリケーションがインポートされ、ソフトウェアライブラリに追加されると、進行状況バーと状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-159">**Progress** – Displays a progress bar and status as the application is imported and added to the Software Library.</span></span>
   * <span data-ttu-id="e02d3-160">[**完了**]-アプリケーションの作成プロセスが完了すると、アプリケーションの作成が成功したことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-160">**Completion** – Confirmation of the successful application creation is displayed when the application creation process is complete.</span></span> <span data-ttu-id="e02d3-161">[ **閉じる** ] を選択して、アプリケーションの作成ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-161">Select **Close** to finish the Create Application Wizard.</span></span>

<span data-ttu-id="e02d3-162">Configuration Manager でアプリケーションを作成したら、それを配布ポイントに配布して、Surface デバイスを含むコレクションに展開することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-162">After the application is created in Configuration Manager, you can distribute it to your distribution points and deploy it to the collections including your Surface devices.</span></span> <span data-ttu-id="e02d3-163">このアプリケーションは Surface デバイス上で SEMM をインストールしたり有効にしたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="e02d3-163">This application will not install or enable SEMM on the Surface device.</span></span> <span data-ttu-id="e02d3-164">これには、PowerShell スクリプトを使用して SEMM を有効にするために必要なアセンブリのみが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-164">It only provides the assemblies required for SEMM to be enabled using the PowerShell script.</span></span>

<span data-ttu-id="e02d3-165">SEMM で管理されないデバイスに Microsoft Surface UEFI Manager アセンブリをインストールしない場合は、Microsoft Surface UEFI Manager を SEMM Configuration Manager スクリプトの依存関係として構成できます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-165">If you do not want to install the Microsoft Surface UEFI Manager assemblies on devices that will not be managed with SEMM, you can configure Microsoft Surface UEFI Manager as a dependency of the SEMM Configuration Manager scripts.</span></span> <span data-ttu-id="e02d3-166">このシナリオについては、この記事の後半の「 [SEMM 構成マネージャースクリプトの展開](#deploy-semm-configuration-manager-scripts) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-166">This scenario is covered in the [Deploy SEMM Configuration Manager Scripts](#deploy-semm-configuration-manager-scripts) section later in this article.</span></span>

## <a name="create-or-modify-the-semm-configuration-manager-scripts"></a><span data-ttu-id="e02d3-167">SEMM 構成マネージャーのスクリプトを作成または変更する</span><span class="sxs-lookup"><span data-stu-id="e02d3-167">Create or modify the SEMM Configuration Manager scripts</span></span>

<span data-ttu-id="e02d3-168">必要なアセンブリがデバイスにインストールされた後、SEMM でデバイスを登録して Surface UEFI を構成するプロセスは、PowerShell スクリプトで実行され、Configuration Manager を使用してスクリプトアプリケーションとして展開されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-168">After the required assemblies have been installed on the devices, the process of enrolling the devices in SEMM and configuring Surface UEFI is done with PowerShell scripts and deployed as a script application with Configuration Manager.</span></span> <span data-ttu-id="e02d3-169">これらのスクリプトは、組織と環境のニーズに合わせて変更できます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-169">These scripts can be modified to fit the needs of your organization and environment.</span></span> <span data-ttu-id="e02d3-170">たとえば、さまざまな部門またはロールで、管理された Surface デバイスの複数の構成を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-170">For example, you can create multiple configurations for managed Surface devices in different departments or roles.</span></span> <span data-ttu-id="e02d3-171">SEMM および Configuration Manager のスクリプトのサンプルは、この記事の最初の「 [前提条件](#prerequisites) 」セクションのリンクからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-171">You can download samples of the scripts for SEMM and Configuration Manager from the link in the [Prerequisites](#prerequisites) section at the beginning of this article.</span></span>

<span data-ttu-id="e02d3-172">構成マネージャーを使用して SEMM の展開を実行するには、2つの主要なスクリプトが必要です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-172">There are two primary scripts you will need in order to perform a SEMM deployment with Configuration Manager:</span></span>

* <span data-ttu-id="e02d3-173">**ConfigureSEMM.ps1** –このスクリプトを使用して、surface デバイスの構成パッケージを、surface デバイスに適用するために、指定された設定を surface デバイスに適用するため、semm でデバイスを登録するため、semm でデバイスの登録を識別するために使用するレジストリキーを設定するために使います。</span><span class="sxs-lookup"><span data-stu-id="e02d3-173">**ConfigureSEMM.ps1** – Use this script to create configuration packages for your Surface devices with your desired Surface UEFI settings to apply the specified settings to a Surface device, to enroll the device in SEMM, and to set a registry key used to identify the enrollment of the device in SEMM.</span></span>
* <span data-ttu-id="e02d3-174">**ResetSEMM.ps1** –このスクリプトを使用して、surface デバイス上の semm をリセットします。これにより、semm から登録解除され、surface UEFI 設定の制御が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-174">**ResetSEMM.ps1** – Use this script to reset SEMM on a Surface device, which unenrolls it from SEMM and removes the control over Surface UEFI settings.</span></span>

<span data-ttu-id="e02d3-175">サンプルスクリプトには、Surface UEFI 設定を設定する方法と、それらの設定へのアクセス許可を制御する方法の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-175">The sample scripts include examples of how to set Surface UEFI settings and how to control permissions to those settings.</span></span> <span data-ttu-id="e02d3-176">これらの設定を変更して Surface UEFI をセキュリティで保護し、環境のニーズに応じて Surface UEFI 設定を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-176">These settings can be modified to secure Surface UEFI and set Surface UEFI settings according to the needs of your environment.</span></span> <span data-ttu-id="e02d3-177">この記事の以下のセクションでは、ConfigureSEMM.ps1 スクリプトについて説明し、要件に合わせてスクリプトを作成するために必要な変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-177">The following sections of this article explain the ConfigureSEMM.ps1 script and explore the modifications you need to make to the script to fit your requirements.</span></span>

> [!NOTE]
> <span data-ttu-id="e02d3-178">SEMM 構成マネージャーのスクリプトとエクスポートされた SEMM 証明書ファイル (.pfx) は、構成マネージャーに追加される前に、他のファイルを持たない同じフォルダーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-178">The SEMM Configuration Manager scripts and the exported SEMM certificate file (.pfx) should be placed in the same folder with no other files before they are added to Configuration Manager.</span></span>

### <a name="specify-certificate-and-package-names"></a><span data-ttu-id="e02d3-179">証明書とパッケージ名を指定する</span><span class="sxs-lookup"><span data-stu-id="e02d3-179">Specify certificate and package names</span></span>

<span data-ttu-id="e02d3-180">変更する必要があるスクリプトの最初の領域は、SEMM 証明書を指定して読み込む部分であり、SurfaceUEFIManager のバージョン、および SEMM 構成パッケージと SEMM のリセットパッケージの名前も示しています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-180">The first region of the script that you need to modify is the portion that specifies and loads the SEMM certificate, and also indicates SurfaceUEFIManager version, and the names for the SEMM configuration package and SEMM reset package.</span></span> <span data-ttu-id="e02d3-181">証明書の名前と SurfaceUEFIManager のバージョンは、スクリプト ConfigureSEMM.ps1 の 56 ~ 73 の行に指定されています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-181">The certificate name and SurfaceUEFIManager version are specified on lines 56 through 73 in the ConfigureSEMM.ps1 script.</span></span>

  ```powershell
  56    $WorkingDirPath = split-path -parent $MyInvocation.MyCommand.Definition
  57    $packageRoot = "$WorkingDirPath\Config"
  58    $certName = "FabrikamSEMMSample.pfx"
  59  $DllVersion = "2.26.136.0"
  60
  61  $certNameOnly = [System.IO.Path]::GetFileNameWithoutExtension($certName)
  62  $ProvisioningPackage = $certNameOnly + "ProvisioningPackage.pkg"
  63  $ResetPackage = $certNameOnly + "ResetPackage.pkg"
  64
  65    if (-not (Test-Path $packageRoot))  { New-Item -ItemType Directory -Force -Path $packageRoot }
  66    Copy-Item "$WorkingDirPath\$certName" $packageRoot
  67    
  68    $privateOwnerKey = Join-Path -Path $packageRoot -ChildPath $certName
  69    $ownerPackageName = Join-Path -Path $packageRoot -ChildPath $ProvisioningPackage
  70    $resetPackageName = Join-Path -Path $packageRoot -ChildPath $ResetPackage
  71    
  72    # If your PFX file requires a password then it can be set here, otherwise use a blank string.
  73    $password = "1234" 
  ```

<span data-ttu-id="e02d3-182">**$CertName**変数の**FabrikamSEMMSample**値を、58行の semm 証明書ファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-182">Replace the **FabrikamSEMMSample.pfx** value for the **$certName** variable with the name of your SEMM Certificate file on line 58.</span></span> <span data-ttu-id="e02d3-183">スクリプトが配置されているフォルダーに (Config という名前の) 作業ディレクトリが作成され、証明書ファイルがこの作業ディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-183">The script will create a working directory (named Config) in the folder where your scripts are located, and then copies the certificate file to this working directory.</span></span>

<span data-ttu-id="e02d3-184">また、所有者パッケージとリセットパッケージは、構成ディレクトリ内に作成され、Surface UEFI の設定とスクリプトによって生成されるアクセス許可の構成を保持します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-184">Owner package and reset package will also be created in the Config directory and hold the configuration for Surface UEFI settings and permissions generated by the script.</span></span>

<span data-ttu-id="e02d3-185">73の場合は、 **$password** 変数の値を **1234** から証明書ファイルのパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-185">On line 73, replace the value of the **$password** variable, from **1234** to the password for your certificate file.</span></span> <span data-ttu-id="e02d3-186">パスワードが必要ない場合は、 **1234** のテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-186">If a password is not required, delete the **1234** text.</span></span>

> [!Note]
> <span data-ttu-id="e02d3-187">SEMM でデバイスを登録するには、証明書の拇印の最後の2文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-187">The last two characters of the certificate thumbprint are required to enroll a device in SEMM.</span></span> <span data-ttu-id="e02d3-188">このスクリプトでは、ユーザーにこれらの数字が表示されます。これにより、システムを再起動してからデバイスを SEMM に登録する前に、ユーザーまたは技術者がこれらの数字を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-188">This script will display these digits to the user, which allows the user or technician to record these digits before the system reboots to enroll the device in SEMM.</span></span> <span data-ttu-id="e02d3-189">このスクリプトでは、150-155 行にある次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-189">The script uses the following code, found on lines 150-155, to accomplish this.</span></span>

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

証明書ファイル (.pfx) にアクセスできる管理者は、CertMgr で .pfx ファイルを開くと、いつでも拇印を読むことができます。 <span data-ttu-id="e02d3-191">CertMgr で拇印を表示するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-191">To view the thumbprint with CertMgr, follow this process:</span></span>

1. <span data-ttu-id="e02d3-192">.Pfx ファイルを右クリックし、[ **開く**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-192">Right-click the .pfx file, and then select **Open**.</span></span>
2. <span data-ttu-id="e02d3-193">ナビゲーションウィンドウでフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-193">Expand the folder in the navigation pane.</span></span>
3. <span data-ttu-id="e02d3-194">[ **証明書**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-194">Select **Certificates**.</span></span>
4. <span data-ttu-id="e02d3-195">メインウィンドウで証明書を右クリックし、[ **開く**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-195">Right-click your certificate in the main pane, and then select **Open**.</span></span>
5. <span data-ttu-id="e02d3-196">[ **詳細** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-196">Select the **Details** tab.</span></span>
6. <span data-ttu-id="e02d3-197">[表示] ドロップダウンメニューで [**すべて**] または [**プロパティ** **]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-197">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
7. <span data-ttu-id="e02d3-198">フィールドの **拇印**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-198">Select the field **Thumbprint**.</span></span>

> [!NOTE]
> <span data-ttu-id="e02d3-199">構成マネージャーがアンインストールアクションを使ってデバイスから SEMM を削除できるようにするには、ResetSEMM.ps1 スクリプトのこのセクションに SEMM 証明書の名前とパスワードも入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-199">The SEMM certificate name and password must also be entered in this section of the ResetSEMM.ps1 script to enable Configuration Manager to remove SEMM from the device with the uninstall action.</span></span>

### <a name="configure-permissions"></a><span data-ttu-id="e02d3-200">権限を構成する</span><span class="sxs-lookup"><span data-stu-id="e02d3-200">Configure permissions</span></span>

<span data-ttu-id="e02d3-201">Surface UEFI の構成を指定するスクリプトの最初の領域は、 **"アクセス許可の構成"** 領域です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-201">The first region of the script where you will specify the configuration for Surface UEFI is the **Configure Permissions** region.</span></span> <span data-ttu-id="e02d3-202">この領域は、 **"# Configure アクセス許可"** というコメントを含むサンプルスクリプトの行210から始まり、行247まで続きます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-202">This region begins at line 210 in the sample script with the comment **# Configure Permissions** and continues to line 247.</span></span> <span data-ttu-id="e02d3-203">次のコード例では、最初にすべての Surface UEFI 設定へのアクセス許可を設定します。これにより、これらの設定が SEMM のみで変更される可能性があります。また、ローカルユーザーが Surface UEFI パスワード、TPM、およびフロントカメラとバックカメラを変更できるように、明示的な権限を追加します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-203">The following code fragment first sets permissions to all Surface UEFI settings so that they may be modified by SEMM only, then adds explicit permissions to allow the local user to modify the Surface UEFI password, TPM, and front and rear cameras.</span></span>

```powershell
210 # Configure Permissions
211 foreach ($uefiV2 IN $surfaceDevices.Values) {
212 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
213 Write-Host "Configuring permissions"
214 Write-Host $Device.Model
215 Write-Host "======================="
216
217 # Here we define which "identities" will be allowed to modify which settings
218 #   PermissionSignerOwner = The primary SEMM enterprise owner identity
219 #   PermissionLocal = The user when booting to the UEFI pre-boot GUI
220 #   PermissionSignerUser, PermissionSignerUser1, PermissionSignerUser2 =
221 #     Additional user identities created so that the signer owner
222 #     can delegate permission control for some settings.
223 $ownerOnly = [Microsoft.Surface.IUefiSetting]::PermissionSignerOwner
224 $ownerAndLocalUser = ([Microsoft.Surface.IUefiSetting]::PermissionSignerOwner -bor [Microsoft.Surface.IUefiSetting]::PermissionLocal)
225 
226 # Make all permissions owner only by default
227 foreach ($setting IN $uefiV2.Settings.Values) {
228 $setting.ConfiguredPermissionFlags = $ownerOnly
229 }
230 
231 # Allow the local user to change their own password
232 $uefiV2.SettingsById[501].ConfiguredPermissionFlags = $ownerAndLocalUser
233
234 Write-Host ""
235  
236 # Create a unique package name based on family and LSV.
237 # We will choose a name that can be parsed by later scripts.
238 $packageName = $uefiV2.SurfaceUefiFamily + "^Permissions^" + $lsv + ".pkg"
239 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
240 
241 # Build and sign the Permission package then save it to a file.
242 $permissionPackageStream =  $uefiV2.BuildAndSignPermissionPackage($privateOwnerKey, $password, "", $null, $lsv)
243 $permissionPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
244 $permissionPackageStream.CopyTo($permissionPackage)
245 $permissionPackage.Close()
246 }
247 }
```

<span data-ttu-id="e02d3-204">各 **$uefiV 2** 変数は、名前または ID を設定して Surface UEFI 設定を識別し、次のいずれかの値にアクセス許可を構成します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-204">Each **$uefiV2** variable identifies a Surface UEFI setting by setting name or ID, and then configures the permissions to one of the following values:</span></span>

* <span data-ttu-id="e02d3-205">**$ownerOnly** –この設定を変更する権限は、semm に対してのみ許可されています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-205">**$ownerOnly** – Permission to modify this setting is granted only to SEMM.</span></span>
* <span data-ttu-id="e02d3-206">**$ownerAndLocalUser** –この設定を変更する権限は、ローカルユーザーが Surface UEFI と semm に対して起動するために許可されています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-206">**$ownerAndLocalUser** – Permission to modify this setting is granted to a local user booting to Surface UEFI, as well as to SEMM.</span></span>

<span data-ttu-id="e02d3-207">Surface UEFI の使用可能な設定名と Id については、この記事の「 [設定名と id](#settings-names-and-ids) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-207">You can find information about the available settings names and IDs for Surface UEFI in the [Settings Names and IDs](#settings-names-and-ids) section of this article.</span></span>

### <a name="configure-settings"></a><span data-ttu-id="e02d3-208">設定の構成</span><span class="sxs-lookup"><span data-stu-id="e02d3-208">Configure settings</span></span>

<span data-ttu-id="e02d3-209">Surface UEFI の構成を指定するスクリプトの2番目の領域は、各設定を有効または無効にするかどうかを構成する、ConfigureSEMM.ps1 スクリプトの **構成設定** 領域です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-209">The second region of the script where you will specify the configuration for Surface UEFI is the **Configure Settings** region of the ConfigureSEMM.ps1 script, which configures whether each setting is enabled or disabled.</span></span> <span data-ttu-id="e02d3-210">サンプルスクリプトには、すべての設定を既定値に設定する手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-210">The sample script includes instructions to set all settings to their default values.</span></span> <span data-ttu-id="e02d3-211">次に、スクリプトは、PXE ブートのために IPv6 を無効にするための明示的な指示を提供し、Surface UEFI 管理者パスワードは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-211">The script then provides explicit instructions to disable IPv6 for PXE Boot and to leave the Surface UEFI Administrator password unchanged.</span></span> <span data-ttu-id="e02d3-212">この領域は、最初に **# Configure 設定** のコメント (291 から行335のサンプルスクリプト) から始まります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-212">You can find this region beginning with the **# Configure Settings** comment at line 291 through line 335 in the sample script.</span></span> <span data-ttu-id="e02d3-213">次のような領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-213">The region appears as follows.</span></span>

```powershell
291 # Configure Settings
292 foreach ($uefiV2 IN $surfaceDevices.Values) {
293 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
294 Write-Host "Configuring settings"
295 Write-Host $Device.Model
296 Write-Host "===================="
297
298 # In this demo, we will start by setting every setting to the default factory setting.
299 # You may want to start by doing this in your scripts
300 # so that every setting gets set to a known state.
301 foreach ($setting IN $uefiV2.Settings.Values) {
302 $setting.ConfiguredValue = $setting.DefaultValue
303 }
304 
305 $EnabledValue = "Enabled"
306 $DisabledValue = "Disabled"
307
308 # If you want to set something to a different value from the default,
309 # here are examples of how to accomplish this.
310 # This disables IPv6 PXE boot by name:
311 $uefiV2.Settings["IPv6 for PXE Boot"].ConfiguredValue = $DisabledValue
312
313 # This disables IPv6 PXE Boot by ID:
314 $uefiV2.SettingsById[400].ConfiguredValue = $DisabledValue
315
316 Write-Host ""
317
318 # If you want to leave the setting unmodified, set it to $null
319 # PowerShell has issues setting things to $null so ClearConfiguredValue()
320 # is supplied to do this explicitly.
321 # Here is an example of leaving the UEFI administrator password as-is,
322 # even after we initially set it to factory default above.
323 $uefiV2.SettingsById[501].ClearConfiguredValue()
324 
325 # Create a unique package name based on family and LSV.
326 # We will choose a name that can be parsed by later scripts.
327 $packageName = $uefiV2.SurfaceUefiFamily + "^Settings^" + $lsv + ".pkg"
328 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
329 
330 # Build and sign the Settings package then save it to a file.
331 $settingsPackageStream =  $uefiV2.BuildAndSignSecuredSettingsPackage($privateOwnerKey, $password, "", $null, $lsv)
332 $settingsPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
333 $settingsPackageStream.CopyTo($settingsPackage)
334 $settingsPackage.Close()
335 }
```

<span data-ttu-id="e02d3-214">スクリプトの [ **アクセス許可の構成** ] セクションで設定したアクセス許可と同様に、各 Surface UEFI 設定の構成は、 **$uefiV 2** 変数を定義して実行されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-214">Like the permissions set in the **Configure Permissions** section of the script, the configuration of each Surface UEFI setting is performed by defining the **$uefiV2** variable.</span></span> <span data-ttu-id="e02d3-215">**$UefiV 2**変数を定義する各行について、Surface UEFI の設定は名前または ID を設定することによって識別され、構成された値は [**有効**] または [**無効**] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-215">For each line defining the **$uefiV2** variable, a Surface UEFI setting is identified by setting name or ID and the configured value is set to **Enabled** or **Disabled**.</span></span>

<span data-ttu-id="e02d3-216">Surface uefi の設定を変更する必要がない場合 (たとえば、surface uefi 管理者のパスワードが、すべての Surface UEFI 設定を既定の状態にリセットする操作によってクリアされないようにする) には、 **ClearConfiguredValue ()** を使って、この設定が変更されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-216">If you do not want to alter the configuration of a Surface UEFI setting, for example to ensure that the Surface UEFI administrator password is not cleared by the action of resetting all Surface UEFI settings to their default, you can use **ClearConfiguredValue()** to enforce that this setting will not be altered.</span></span> <span data-ttu-id="e02d3-217">このサンプルスクリプトでは、行323でこの値を使って、サンプルスクリプトで **501**の設定 ID によって識別された Surface UEFI 管理者パスワードをクリアしないようにしています。</span><span class="sxs-lookup"><span data-stu-id="e02d3-217">In the sample script, this is used on line 323 to prevent the clearing of the Surface UEFI Administrator password, identified in the sample script by its setting ID, **501**.</span></span>

<span data-ttu-id="e02d3-218">Surface UEFI の使用可能な設定名と Id の詳細については、この記事の後半の「 [設定名と id](#settings-names-and-ids) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-218">You can find information about the available settings names and IDs for Surface UEFI in the [Settings Names and IDs](#settings-names-and-ids) section later in this article.</span></span>

### <a name="settings-registry-key"></a><span data-ttu-id="e02d3-219">設定レジストリキー</span><span class="sxs-lookup"><span data-stu-id="e02d3-219">Settings registry key</span></span>

<span data-ttu-id="e02d3-220">Configuration Manager の登録済みシステムを特定するために、ConfigureSEMM.ps1 スクリプトは、SEMM 構成スクリプトを使用してインストールされている登録済みシステムを識別するために使用できるレジストリキーを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-220">To identify enrolled systems for Configuration Manager, the ConfigureSEMM.ps1 script writes registry keys that can be used to identify enrolled systems as having been installed with the SEMM configuration script.</span></span> <span data-ttu-id="e02d3-221">これらのキーは、次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-221">These keys can be found at the following location.</span></span>

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

<span data-ttu-id="e02d3-222">これらのレジストリキーを作成するには、380-477 行にある次のコード片を使用します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-222">The following code fragment, found on lines 380-477, is used to write these registry keys.</span></span>

```powershell
380 # For Endpoint Configuration Manager or other management solutions that wish to know what version is applied, tattoo the LSV and current DateTime (in UTC) to the registry:
381 $UTCDate = (Get-Date).ToUniversalTime().ToString()
382 $certIssuer = $certPrint.Issuer
383 $certSubject = $certPrint.Subject
384 
385 $SurfaceRegKey = "HKLM:\SOFTWARE\Microsoft\Surface\SEMM"
386 New-RegKey $SurfaceRegKey
387 $LSVRegValue = Get-ItemProperty $SurfaceRegKey LSV -ErrorAction SilentlyContinue
388 $DateTimeRegValue = Get-ItemProperty $SurfaceRegKey LastConfiguredUTC -ErrorAction SilentlyContinue
389 $OwnershipSessionIdRegValue = Get-ItemProperty $SurfaceRegKey OwnershipSessionId -ErrorAction SilentlyContinue
390 $PermissionSessionIdRegValue = Get-ItemProperty $SurfaceRegKey PermissionSessionId -ErrorAction SilentlyContinue
391 $SettingsSessionIdRegValue = Get-ItemProperty $SurfaceRegKey SettingsSessionId -ErrorAction SilentlyContinue
392 $IsResetRegValue = Get-ItemProperty $SurfaceRegKey IsReset -ErrorAction SilentlyContinue
393 $certUsedRegValue = Get-ItemProperty $SurfaceRegKey CertName -ErrorAction SilentlyContinue
394 $certIssuerRegValue = Get-ItemProperty $SurfaceRegKey CertIssuer -ErrorAction SilentlyContinue
395 $certSubjectRegValue = Get-ItemProperty $SurfaceRegKey CertSubject -ErrorAction SilentlyContinue
396 
397 
398 If ($LSVRegValue -eq $null)
399 {
400     New-ItemProperty -Path $SurfaceRegKey -Name LSV -PropertyType DWORD -Value $lsv | Out-Null
401 }
402 Else
403 {
404     Set-ItemProperty -Path $SurfaceRegKey -Name LSV -Value $lsv
405 }
406 
407 If ($DateTimeRegValue -eq $null)
408 {
409     New-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -PropertyType String -Value $UTCDate | Out-Null
410 }
411 Else
412 {
413     Set-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -Value $UTCDate
414 }
415 
416 If ($OwnershipSessionIdRegValue -eq $null)
417 {
418     New-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -PropertyType String -Value $ownerSessionIdValue | Out-Null
419 }
420 Else
421 {
422     Set-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -Value $ownerSessionIdValue
423 }
424 
425 If ($PermissionSessionIdRegValue -eq $null)
426 {
427     New-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -PropertyType String -Value $permissionSessionIdValue | Out-Null
428 }
429 Else
430 {
431     Set-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -Value $permissionSessionIdValue
432 }
433 
434 If ($SettingsSessionIdRegValue -eq $null)
435 {
436     New-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -PropertyType String -Value $settingsSessionIdValue | Out-Null
437 }
438 Else
439 {
440     Set-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -Value $settingsSessionIdValue
441 }
442 
443 If ($IsResetRegValue -eq $null)
444 {
445     New-ItemProperty -Path $SurfaceRegKey -Name IsReset -PropertyType DWORD -Value 0 | Out-Null
446 }
447 Else
448 {
449     Set-ItemProperty -Path $SurfaceRegKey -Name IsReset -Value 0
450 }
451 
452 If ($certUsedRegValue -eq $null)
453 {
454     New-ItemProperty -Path $SurfaceRegKey -Name CertName -PropertyType String -Value $certName | Out-Null
455 }
456 Else
457 {
458     Set-ItemProperty -Path $SurfaceRegKey -Name CertName -Value $certName
459 }
460 
461 If ($certIssuerRegValue -eq $null)
462 {
463     New-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -PropertyType String -Value $certIssuer | Out-Null
464 }
465 Else
466 {
467     Set-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -Value $certIssuer
468 }
469 
470 If ($certSubjectRegValue -eq $null)
471 {
472     New-ItemProperty -Path $SurfaceRegKey -Name CertSubject -PropertyType String -Value $certSubject | Out-Null
473 }
474 Else
475 {
476     Set-ItemProperty -Path $SurfaceRegKey -Name CertSubject -Value $certSubject
477 }
```

### <a name="settings-names-and-ids"></a><span data-ttu-id="e02d3-223">設定名と Id</span><span class="sxs-lookup"><span data-stu-id="e02d3-223">Settings names and IDs</span></span>

<span data-ttu-id="e02d3-224">Surface uefi の設定または Surface UEFI 設定の権限を構成するには、設定名または設定 ID のいずれかで、各設定を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-224">To configure Surface UEFI settings or permissions for Surface UEFI settings, you must refer to each setting by either its setting name or setting ID.</span></span> <span data-ttu-id="e02d3-225">Surface UEFI の新しい更新があるたびに、新しい設定が追加されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-225">With each new update for Surface UEFI, new settings may be added.</span></span> <span data-ttu-id="e02d3-226">Surface デバイスで利用可能な設定の完全な一覧を取得する最適な方法は、[設定名] と [設定] Id と共に、 [Surface ツール](https://www.microsoft.com/download/details.aspx?id=46703)の SEMM_Powershell.zip の ShowSettingsOptions.ps1 スクリプトを使って、IT をダウンロードすることです。</span><span class="sxs-lookup"><span data-stu-id="e02d3-226">The best way to get a complete list of the settings available on a Surface device, along with the settings name and settings IDs, is to use the ShowSettingsOptions.ps1 script from SEMM_Powershell.zip in [Surface Tools for IT Downloads](https://www.microsoft.com/download/details.aspx?id=46703)</span></span> 

<span data-ttu-id="e02d3-227">ShowSettingsOptions.ps1 を実行するコンピューターには Microsoft Surface UEFI Manager がインストールされている必要がありますが、スクリプトは Surface デバイスを必要としません。</span><span class="sxs-lookup"><span data-stu-id="e02d3-227">The computer where ShowSettingsOptions.ps1 is run must have Microsoft Surface UEFI Manager installed, but the script does not require a Surface device.</span></span>


## <a name="deploy-semm-configuration-manager-scripts"></a><span data-ttu-id="e02d3-228">SEMM Configuration Manager スクリプトの展開</span><span class="sxs-lookup"><span data-stu-id="e02d3-228">Deploy SEMM Configuration Manager scripts</span></span>

<span data-ttu-id="e02d3-229">クライアントデバイスで SEMM を構成して有効にする準備ができたら、次の手順として、これらのスクリプトを Configuration Manager でアプリケーションとして追加します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-229">After your scripts are prepared to configure and enable SEMM on the client device, the next step is to add these scripts as an application in Configuration Manager.</span></span> <span data-ttu-id="e02d3-230">構成マネージャーを開く前に、他のファイルを含まない共有フォルダーに次のファイルが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-230">Before you open Configuration Manager, ensure that the following files are in a shared folder that does not include other files:</span></span>

* <span data-ttu-id="e02d3-231">ConfigureSEMM.ps1</span><span class="sxs-lookup"><span data-stu-id="e02d3-231">ConfigureSEMM.ps1</span></span>
* <span data-ttu-id="e02d3-232">ResetSEMM.ps1</span><span class="sxs-lookup"><span data-stu-id="e02d3-232">ResetSEMM.ps1</span></span>
* <span data-ttu-id="e02d3-233">SEMM 証明書 (たとえば、SEMMCertificate. .pfx)</span><span class="sxs-lookup"><span data-stu-id="e02d3-233">Your SEMM certificate (for example SEMMCertificate.pfx)</span></span>

<span data-ttu-id="e02d3-234">SEMM 構成マネージャーのスクリプトは、スクリプトアプリケーションとして Configuration Manager に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-234">The SEMM Configuration Manager scripts will be added to Configuration Manager as a script application.</span></span> <span data-ttu-id="e02d3-235">ConfigureSEMM.ps1 で SEMM をインストールするコマンドは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-235">The command to install SEMM with ConfigureSEMM.ps1 is as follows.</span></span>

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

<span data-ttu-id="e02d3-236">SEMM を ResetSEMM.ps1 でアンインストールするコマンドは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-236">The command to uninstall SEMM with ResetSEMM.ps1 is as follows.</span></span>

`Powershell.exe -file ".\ResetSEMM.ps1"`

<span data-ttu-id="e02d3-237">SEMM Configuration Manager のスクリプトをアプリケーションとして Configuration Manager に追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-237">To add the SEMM Configuration Manager scripts to Configuration Manager as an application, use the following process:</span></span>

1. <span data-ttu-id="e02d3-238">この記事の前半の「 [Microsoft SURFACE UEFI マネージャーの展開](#deploy-microsoft-surface-uefi-manager) 」セクションの手順1から手順5を実行して、アプリケーションの作成ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-238">Start the Create Application Wizard using Step 1 through Step 5 from the [Deploy Microsoft Surface UEFI Manager](#deploy-microsoft-surface-uefi-manager) section earlier in this article.</span></span>

2. <span data-ttu-id="e02d3-239">次の手順に従って、アプリケーションの作成ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-239">Proceed through The Create Application Wizard as follows:</span></span>

   - <span data-ttu-id="e02d3-240">**[全般** ]- **アプリケーション情報を手動で指定**し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-240">**General** – Select **Manually specify the application information**, and then select **Next**.</span></span>

   - <span data-ttu-id="e02d3-241">**[全般情報** ]-アプリケーションの名前 (semm など) と、このページの publisher、バージョン、コメントなどの必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-241">**General Information** – Enter a name for the application (for example SEMM) and any other information you want such as publisher, version, or comments on this page.</span></span> <span data-ttu-id="e02d3-242">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-242">Select **Next** to proceed.</span></span>

   - <span data-ttu-id="e02d3-243">[**アプリケーションカタログ**] –このページのフィールドには、既定値を指定したままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-243">**Application Catalog** – The fields on this page can be left with their default values.</span></span> <span data-ttu-id="e02d3-244">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-244">Select **Next**.</span></span>

   - <span data-ttu-id="e02d3-245">**展開の種類** – [ **追加** ] を選んで、展開の種類の作成ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-245">**Deployment Types** – Select **Add** to start the Create Deployment Type Wizard.</span></span>

   - <span data-ttu-id="e02d3-246">次に示すように、展開の種類の作成ウィザードの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-246">Proceed through the steps of the Create Deployment Type Wizard, as follows:</span></span>

     * <span data-ttu-id="e02d3-247">**[全般**]-[ **Type** ] ドロップダウンメニューから [**スクリプトインストーラー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-247">**General** – Select **Script Installer** from the **Type** drop-down menu.</span></span> <span data-ttu-id="e02d3-248">[ **展開の種類の情報を手動で指定** する] オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-248">The **Manually specify the deployment type information** option will automatically be selected.</span></span> <span data-ttu-id="e02d3-249">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-249">Select **Next** to proceed.</span></span>
     * <span data-ttu-id="e02d3-250">**[General Information** ]: 展開の種類の名前 (「Semm 構成スクリプト」など) を入力し、[ **次へ** ] をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-250">**General Information** – Enter a name for the deployment type (for example SEMM Configuration Scripts), and then select **Next** to continue.</span></span>
     * <span data-ttu-id="e02d3-251">**コンテンツ**-[**コンテンツの場所**] フィールドの横にある [**参照**] を選択し、semm 構成マネージャーのスクリプトが配置されているフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-251">**Content** – Select **Browse** next to the **Content Location** field, and then select the folder where your SEMM Configuration Manager scripts are located.</span></span> <span data-ttu-id="e02d3-252">[ **インストールプログラム** ] フィールドに、この記事の前半で説明した [インストールコマンド](#deploy-semm-configuration-manager-scripts) を入力します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-252">In the **Installation Program** field, type the [installation command](#deploy-semm-configuration-manager-scripts) found earlier in this article.</span></span> <span data-ttu-id="e02d3-253">[ **アンインストールプログラム** ] フィールドに、この記事の前半で説明した [アンインストールコマンド](#deploy-semm-configuration-manager-scripts) を入力します (図2を参照)。</span><span class="sxs-lookup"><span data-stu-id="e02d3-253">In the **Uninstall Program** field, enter the [uninstallation command](#deploy-semm-configuration-manager-scripts) found earlier in this article (shown in Figure 2).</span></span> <span data-ttu-id="e02d3-254">次のページに移動するには、[ **次へ** ] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-254">Select **Next** to move to the next page.</span></span>
    
     ![SEMM 構成マネージャーのスクリプトをインストールコマンドとアンインストールコマンドとして設定する](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *<span data-ttu-id="e02d3-256">図 2. </span><span class="sxs-lookup"><span data-stu-id="e02d3-256">Figure 2.</span></span> <span data-ttu-id="e02d3-257">SEMM 構成マネージャーのスクリプトをインストールコマンドとアンインストールコマンドとして設定する</span><span class="sxs-lookup"><span data-stu-id="e02d3-257">Set the SEMM Configuration Manager scripts as the install and uninstall commands</span></span>*

     * <span data-ttu-id="e02d3-258">**検出方法** – [ **句の追加** ] を選択して、semm Configuration Manager スクリプトレジストリキー検出ルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-258">**Detection Method** – Select **Add Clause** to add the SEMM Configuration Manager script registry key detection rule.</span></span> <span data-ttu-id="e02d3-259">図3に示すように、 **検出ルール** のウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-259">The **Detection Rule** window is displayed, as shown in Figure 3.</span></span> <span data-ttu-id="e02d3-260">次の設定を使います。</span><span class="sxs-lookup"><span data-stu-id="e02d3-260">Use the following settings:</span></span>

       - <span data-ttu-id="e02d3-261">[**設定の種類**] ドロップダウンメニューから [**レジストリ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-261">Select **Registry** from the **Setting Type** drop-down menu.</span></span>
       - <span data-ttu-id="e02d3-262">[**ハイブ**] ドロップダウンメニューから [ **HKEY_LOCAL_MACHINE** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-262">Select **HKEY_LOCAL_MACHINE** from the **Hive** drop-down menu.</span></span>
       - <span data-ttu-id="e02d3-263">[**キー** ] フィールドに「 **SOFTWARE\Microsoft\Surface\SEMM** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-263">Enter **SOFTWARE\Microsoft\Surface\SEMM** in the **Key** field.</span></span>
       - <span data-ttu-id="e02d3-264">[**値**] フィールドに「 **certname** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-264">Enter **CertName** in the **Value** field.</span></span>
       - <span data-ttu-id="e02d3-265">[**データ型**] ドロップダウンメニューから [**文字列**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-265">Select **String** from the **Data Type** drop-down menu.</span></span>
       - <span data-ttu-id="e02d3-266">この **アプリケーションボタンのプレゼンスを示すために、このレジストリ設定** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-266">Select the **This registry setting must satisfy the following rule to indicate the presence of this application** button.</span></span>
       - <span data-ttu-id="e02d3-267">[ **値** ] フィールドに、スクリプトの58行目に入力した証明書の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-267">Enter the name of the certificate you entered in line 58 of the script in the **Value** field.</span></span>
       - <span data-ttu-id="e02d3-268">[ **OK]** を選択して、[ **検出ルール** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-268">Select **OK** to close the **Detection Rule** window.</span></span>

     ![レジストリキーを使用して SEMM に登録されているデバイスを特定する](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *<span data-ttu-id="e02d3-270">図 3. </span><span class="sxs-lookup"><span data-stu-id="e02d3-270">Figure 3.</span></span> <span data-ttu-id="e02d3-271">レジストリキーを使用して SEMM に登録されているデバイスを特定する</span><span class="sxs-lookup"><span data-stu-id="e02d3-271">Use a registry key to identify devices enrolled in SEMM</span></span>*

     * <span data-ttu-id="e02d3-272">[ **次へ** ] を選択して次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-272">Select **Next** to proceed to the next page.</span></span>
     
     * <span data-ttu-id="e02d3-273">[**ユーザーエクスペリエンス**] – [**インストールの動作**] ドロップダウンメニューから [**システム用にインストール**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-273">**User Experience** – Select **Install for system** from the **Installation Behavior** drop-down menu.</span></span> <span data-ttu-id="e02d3-274">ユーザーが証明書の拇印自体を記録して入力する必要がある場合は、 **ユーザーがログオンしたときにのみ**ログオン要件を設定しておきます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-274">If you want your users to record and enter the certificate thumbprint themselves, leave the logon requirement set to **Only when a user is logged on**.</span></span> <span data-ttu-id="e02d3-275">管理者がユーザーの拇印を入力して、ユーザーがその拇印を表示する必要がない場合は、ユーザーが**ログオン要件**のドロップダウンメニューからログオンしている**かどうか**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-275">If you want your administrators to enter the thumbprint for users and the users do not need to see the thumbprint, select **Whether or not a user is logged on** from the **Logon Requirement** drop-down menu.</span></span>

     * <span data-ttu-id="e02d3-276">**要件** – ConfigureSEMM.ps1 スクリプトは、semm を有効にする前に、デバイスが Surface デバイスであるかどうかを自動的に確認します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-276">**Requirements** – The ConfigureSEMM.ps1 script automatically verifies that the device is a Surface device before attempting to enable SEMM.</span></span> <span data-ttu-id="e02d3-277">ただし、SEMM で管理する必要がないデバイスを持つコレクションにこのスクリプトアプリケーションを展開する場合は、ここに要件を追加して、このアプリケーションが SEMM で管理する Surface デバイスまたはデバイスでのみ実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-277">However, if you intend to deploy this script application to a collection with devices other than those to be managed with SEMM, you could add requirements here to ensure this application would run only on Surface devices or devices you intend to manage with SEMM.</span></span> <span data-ttu-id="e02d3-278">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-278">Select **Next** to continue.</span></span>
     
     * <span data-ttu-id="e02d3-279">**依存関係** -[ **追加** ] を選択して、[ **依存関係の追加** ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-279">**Dependencies** – Select **Add** to open the **Add Dependency** window.</span></span>

       * <span data-ttu-id="e02d3-280">[ **追加** ] を選択して、[ **必要なアプリケーションの指定** ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-280">Select **Add** to open the **Specify Required Application** window.</span></span>

          - <span data-ttu-id="e02d3-281">[ **依存関係グループ名** ] フィールドに semm の依存関係の名前を入力します (たとえば、 *semm アセンブリ*)。</span><span class="sxs-lookup"><span data-stu-id="e02d3-281">Enter a name for the SEMM dependencies in the **Dependency Group Name** field (for example, *SEMM Assemblies*).</span></span>

          - <span data-ttu-id="e02d3-282">**利用可能なアプリケーション**の一覧と MSI 展開の種類から [ **Microsoft Surface UEFI Manager** ] を選択し、[ **OK** ] を選択して [**必要なアプリケーションの指定**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-282">Select **Microsoft Surface UEFI Manager** from the list of **Available Applications** and the MSI deployment type, and then select **OK** to close the **Specify Required Application** window.</span></span>
          
         *   <span data-ttu-id="e02d3-283">Configuration Manager スクリプトを使用して SEMM を有効にしようとしたときに Microsoft Surface UEFI Manager がデバイスに自動的にインストールされるようにするには、[ **自動インストール** ] チェックボックスをオンのままにします。</span><span class="sxs-lookup"><span data-stu-id="e02d3-283">Keep the **Auto Install** check box selected if you want Microsoft Surface UEFI Manager installed automatically on devices when you attempt to enable SEMM with the Configuration Manager scripts.</span></span> <span data-ttu-id="e02d3-284">[ **OK]** を選択して、[ **依存関係の追加** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-284">Select **OK** to close the **Add Dependency** window.</span></span>

     * <span data-ttu-id="e02d3-285">[ **次へ** ] を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-285">Select **Next** to proceed.</span></span>
     
     * <span data-ttu-id="e02d3-286">**概要** : 展開の種類の作成ウィザードで入力した情報が、このページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-286">**Summary** – The information you have entered throughout the Create Deployment Type wizard is displayed on this page.</span></span> <span data-ttu-id="e02d3-287">[ **次へ** ] を選んで選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-287">Select **Next** to confirm your selections.</span></span>
     
     * <span data-ttu-id="e02d3-288">**進行状況** : このページには、semm スクリプトアプリケーションの展開の種類が追加されたときの進行状況バーと状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-288">**Progress** – A progress bar and status as the deployment type is added for the SEMM script application is displayed on this page.</span></span>
     
     * <span data-ttu-id="e02d3-289">**完了** -展開の種類の作成の確認は、プロセスが完了したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-289">**Completion** – Confirmation of the deployment type creation is displayed when the process is complete.</span></span> <span data-ttu-id="e02d3-290">[展開の種類の作成] ウィザードを終了するには、[ **閉じる** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-290">Select **Close** to finish the Create Deployment Type Wizard.</span></span>

   - <span data-ttu-id="e02d3-291">**概要** : アプリケーションの作成ウィザードで入力した情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-291">**Summary** – The information that you entered throughout the Create Application Wizard is displayed.</span></span> <span data-ttu-id="e02d3-292">[ **次へ** ] を選択してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-292">Select **Next** to create the application.</span></span>

   - <span data-ttu-id="e02d3-293">**進行状況** : ソフトウェアライブラリにアプリケーションが追加されたときの進行状況バーと状態は、このページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-293">**Progress** – A progress bar and status as the application is added to the Software Library is displayed on this page.</span></span>

   - <span data-ttu-id="e02d3-294">[**完了**]-アプリケーションの作成プロセスが完了すると、アプリケーションの作成が成功したことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-294">**Completion** – Confirmation of the successful application creation is displayed when the application creation process is complete.</span></span> <span data-ttu-id="e02d3-295">[ **閉じる** ] を選択して、アプリケーションの作成ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-295">Select **Close** to finish the Create Application Wizard.</span></span>

<span data-ttu-id="e02d3-296">構成マネージャーのソフトウェアライブラリでスクリプトアプリケーションを利用できるようになったら、デバイスまたはコレクションに対して作成したスクリプトを使用して、SEMM を配布し、展開することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-296">After the script application is available in the Software Library of Configuration Manager, you can distribute and deploy SEMM using the scripts you prepared to devices or collections.</span></span> <span data-ttu-id="e02d3-297">自動的にインストールされる依存関係として Microsoft Surface UEFI Manager アセンブリを構成している場合は、1つのステップで SEMM を展開できます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-297">If you have configured the Microsoft Surface UEFI Manager assemblies as a dependency that will be automatically installed, you can deploy SEMM in a single step.</span></span> <span data-ttu-id="e02d3-298">依存関係としてアセンブリを構成していない場合は、SEMM を有効にする前に、管理するデバイスにそれらのアセンブリをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-298">If you have not configured the assemblies as a dependency, they must be installed on the devices you intend to manage before you enable SEMM.</span></span>

<span data-ttu-id="e02d3-299">このスクリプトアプリケーションとエンドユーザーに表示される構成を使用して SEMM を展開すると、PowerShell スクリプトが開始され、証明書の拇印が PowerShell ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-299">When you deploy SEMM using this script application and with a configuration that is visible to the end user, the PowerShell script will start and the thumbprint for the certificate will be displayed by the PowerShell window.</span></span> <span data-ttu-id="e02d3-300">デバイスの再起動後に、ユーザーがこの拇印を記録して、Surface UEFI のプロンプトに従って入力することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-300">You can have your users record this thumbprint and enter it when prompted by Surface UEFI after the device reboots.</span></span>

<span data-ttu-id="e02d3-301">または、アプリケーションのインストールを構成して、自動的に再起動し、ユーザーに表示されないようにインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-301">Alternatively, you can configure the application installation to reboot automatically and to install invisibly to the user.</span></span> <span data-ttu-id="e02d3-302">このシナリオでは、再起動時に各デバイスに拇印を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-302">In this scenario, a technician will be required to enter the thumbprint on each device as it reboots.</span></span> <span data-ttu-id="e02d3-303">証明書ファイルへのアクセス権を持つすべての技術者は、CertMgr で証明書を表示して、拇印を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-303">Any technician with access to the certificate file can read the thumbprint by viewing the certificate with CertMgr.</span></span> <span data-ttu-id="e02d3-304">CertMgr で拇印を表示する手順については、この記事の「 [SEMM 構成マネージャーのスクリプトを作成または変更](#create-or-modify-the-semm-configuration-manager-scripts) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e02d3-304">Instructions for viewing the thumbprint with CertMgr are in the [Create or modify the SEMM Configuration Manager scripts](#create-or-modify-the-semm-configuration-manager-scripts) section of this article.</span></span>

<span data-ttu-id="e02d3-305">構成マネージャーと共に展開されたデバイスからの SEMM の削除は、Configuration Manager を使用してアプリケーションをアンインストールするのと同じように簡単です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-305">Removal of SEMM from a device deployed with Configuration Manager using these scripts is as easy as uninstalling the application with Configuration Manager.</span></span> <span data-ttu-id="e02d3-306">このアクションは ResetSEMM.ps1 スクリプトを開始し、SEMM の展開時に使用されたものと同じ証明書ファイルを使ってデバイスを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="e02d3-306">This action starts the ResetSEMM.ps1 script and properly unenrolls the device with the same certificate file that was used during the deployment of SEMM.</span></span>

> [!NOTE]
> <span data-ttu-id="e02d3-307">Microsoft Surface では、デバイスの登録を解除する必要がある場合にのみ、リセットパッケージを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e02d3-307">Microsoft Surface recommends that you create reset packages only when you need to unenroll a device.</span></span> <span data-ttu-id="e02d3-308">通常、これらのリセットパッケージは、シリアル番号によって識別される1つのデバイスに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="e02d3-308">These reset packages are typically valid for only one device, identified by its serial number.</span></span> <span data-ttu-id="e02d3-309">ただし、この証明書で SEMM に登録されているすべてのデバイスで動作するユニバーサルリセットパッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-309">You can, however, create a universal reset package that would work for any device enrolled in SEMM with this certificate.</span></span>
> 
> <span data-ttu-id="e02d3-310">ユニバーサルリセットパッケージは、SEMM でデバイスを登録するために使った証明書と同じように保護することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e02d3-310">We strongly recommend that you protect your universal reset package as carefully as the certificate you used to enroll devices in SEMM.</span></span> <span data-ttu-id="e02d3-311">証明書自体と同じように、このユニバーサルリセットパッケージを使って、SEMM から組織の Surface デバイスの登録を解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-311">Please remember that, just like the certificate itself, this universal reset package can be used to unenroll any of your organization’s Surface devices from SEMM.</span></span>
> 
> <span data-ttu-id="e02d3-312">リセットパッケージをインストールすると、サポートされている最小の値 (LSV) が1の値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-312">When you install a reset package, the Lowest Supported Value (LSV) is reset to a value of 1.</span></span> <span data-ttu-id="e02d3-313">既存の構成パッケージを使用して、デバイスを reenroll することができます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-313">You can reenroll a device by using an existing configuration package.</span></span> <span data-ttu-id="e02d3-314">所有権が取得される前に、デバイスによって証明書の拇印の入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-314">The device will prompt for the certificate thumbprint before ownership is taken.</span></span>
> 
> <span data-ttu-id="e02d3-315">このため、SEMM のデバイスの reenrollment では、新しいパッケージを作成し、そのデバイスにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02d3-315">For this reason, the reenrollment of a device in SEMM would require a new package to be created and installed on that device.</span></span> <span data-ttu-id="e02d3-316">この操作は新しい登録であり、SEMM にすでに登録されているデバイスの構成に変更がないため、デバイスでは、所有権が取得される前に、証明書の拇印の入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="e02d3-316">Because this action is a new enrollment and not a change in configuration on a device already enrolled in SEMM, the device will prompt for the certificate thumbprint before ownership is taken.</span></span>
