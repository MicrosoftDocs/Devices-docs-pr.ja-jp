---
title: プロビジョニング パッケージの作成 (Surface Hub)
description: Windows 10 では、レジストリや構成サービス プロバイダー (CSP) を使用する設定を、プロビジョニング パッケージによって構成することができます。
ms.assetid: 8AA25BD4-8A8F-4B95-9268-504A49BA5345
ms.reviewer: ''
manager: laurawi
keywords: 証明書の追加, プロビジョニング パッケージ
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2019
ms.localizationpriority: medium
ms.openlocfilehash: 0ce77122aecfc9a30ac9dc52dfea7e0b0ccf7e1f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836509"
---
# <span data-ttu-id="99d32-104">プロビジョニング パッケージの作成 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="99d32-104">Create provisioning packages (Surface Hub)</span></span>

<span data-ttu-id="99d32-105">このトピックでは、Windows 構成デザイナーを使ってプロビジョニング パッケージを作成し、それを Surface Hub デバイスに適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99d32-105">This topic explains how to create a provisioning package using the Windows Configuration Designer, and apply it to Surface Hub devices.</span></span> <span data-ttu-id="99d32-106">Surface Hub では、プロビジョニング パッケージを使って証明書を追加し、ユニバーサル Windows プラットフォーム (UWP) アプリをインストールして、ポリシーと設定をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-106">For Surface Hub, you can use provisioning packages to add certificates, install Universal Windows Platform (UWP) apps, and customize policies and settings.</span></span>

<span data-ttu-id="99d32-107">最初の実行の設定時に USB スティックを使うか、**設定**アプリを通じてプロビジョニング パッケージを適用できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-107">You can apply a provisioning package using a USB stick during first-run setup, or through the **Settings** app.</span></span> 


## <span data-ttu-id="99d32-108">長所</span><span class="sxs-lookup"><span data-stu-id="99d32-108">Advantages</span></span>
-   <span data-ttu-id="99d32-109">モバイル デバイス管理 (MDM) プロバイダーを使用せずにデバイスをすばやく構成できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-109">Quickly configure devices without using a mobile device management (MDM) provider.</span></span>

-   <span data-ttu-id="99d32-110">ネットワーク接続は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="99d32-110">No network connectivity required.</span></span>

-   <span data-ttu-id="99d32-111">簡単に適用できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-111">Simple to apply.</span></span>

[<span data-ttu-id="99d32-112">プロビジョニング パッケージの利点と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99d32-112">Learn more about the benefits and uses of provisioning packages.</span></span>](https://technet.microsoft.com/itpro/windows/configure/provisioning-packages)


## <span data-ttu-id="99d32-113">要件</span><span class="sxs-lookup"><span data-stu-id="99d32-113">Requirements</span></span> 

<span data-ttu-id="99d32-114">プロビジョニング パッケージを作成して Surface Hub に適用するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="99d32-114">To create and apply a provisioning package to a Surface Hub, you'll need the following:</span></span>

-   <span data-ttu-id="99d32-115">Windows 構成デザイナー。これは Microsoft Store または Windows 10 アセスメント & デプロイメント キット (ADK) からインストールできます。</span><span class="sxs-lookup"><span data-stu-id="99d32-115">Windows Configuration Designer, which can be installed from Microsoft Store or from the Windows 10 Assessment and Deployment Kit (ADK).</span></span> [<span data-ttu-id="99d32-116">Windows 構成デザイナーをインストールする方法をこちらで確認できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-116">Learn how to install Windows Configuration Designer.</span></span>](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)
-   <span data-ttu-id="99d32-117">USB スティック 1 個。</span><span class="sxs-lookup"><span data-stu-id="99d32-117">A USB stick.</span></span>
-   <span data-ttu-id="99d32-118">**設定**アプリを使ってパッケージを適用する場合は、デバイスの管理者資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="99d32-118">If you apply the package using the **Settings** app, you'll need device admin credentials.</span></span>

<span data-ttu-id="99d32-119">Windows 10 を実行している PC でプロビジョニング パッケージを作成して、パッケージを USB ドライブに保存し、それを Surface Hub に展開します。</span><span class="sxs-lookup"><span data-stu-id="99d32-119">You create the provisioning package on a PC running Windows 10, save the package to a USB drive, and then deploy it to your Surface Hub.</span></span>


## <span data-ttu-id="99d32-120">Surface Hub プロビジョニング パッケージ向けにサポートされる項目</span><span class="sxs-lookup"><span data-stu-id="99d32-120">Supported items for Surface Hub provisioning packages</span></span>

<span data-ttu-id="99d32-121">**プロビジョニング Surface Hub デバイス**ウィザードでは、以下を実行できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-121">Using the **Provision Surface Hub devices** wizard, you can:</span></span>

- <span data-ttu-id="99d32-122">Active Directory、Azure Active Directory、MDM への登録</span><span class="sxs-lookup"><span data-stu-id="99d32-122">Enroll in Active Directory, Azure Active Directory, or MDM</span></span> 
- <span data-ttu-id="99d32-123">デバイス管理者アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="99d32-123">Create an device administrator account</span></span> 
- <span data-ttu-id="99d32-124">アプリケーションと証明書の追加</span><span class="sxs-lookup"><span data-stu-id="99d32-124">Add applications and certificates</span></span>
- <span data-ttu-id="99d32-125">プロキシ設定の構成</span><span class="sxs-lookup"><span data-stu-id="99d32-125">Configure proxy settings</span></span>
- <span data-ttu-id="99d32-126">Surface Hub の構成ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="99d32-126">Add a Surface Hub configuration file</span></span>

>[!WARNING]
><span data-ttu-id="99d32-127">ウィザードを使って Azure Active Directory の登録を構成するには、Windows 10 で Windows 構成デザイナーを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-127">You must run Windows Configuration Designer on Windows 10 to configure Azure Active Directory enrollment using the wizard.</span></span>

<span data-ttu-id="99d32-128">詳細プロビジョニング エディターを使って、Surface Hub 向けのプロビジョニング パッケージに次の項目を追加できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-128">Using the advanced provisioning editor, you can add these items to provisioning packages for Surface Hub:</span></span>

- <span data-ttu-id="99d32-129">**ポリシー** - Surface Hub は、[ポリシー構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#surfacehubpolicies)のポリシーのサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="99d32-129">**Policies** - Surface Hub supports a subset of the policies in the [Policy configuration service provider](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#surfacehubpolicies).</span></span> 
- <span data-ttu-id="99d32-130">**設定** - [SurfaceHub 構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)のすべての設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-130">**Settings** - You can configure any setting in the [SurfaceHub configuration service provider](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx).</span></span>

>[!TIP]
> <span data-ttu-id="99d32-131">ウィザードを使用して共通設定のパッケージを作成した後、詳細エディターに切り替えて他の設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="99d32-131">Use the wizard to create a package with the common settings, then switch to the advanced editor to add other settings.</span></span>
>
>![詳細エディターの起動](images/icd-simple-edit.png)

## <span data-ttu-id="99d32-133">Surface Hub プロビジョニング ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="99d32-133">Use the Surface Hub provisioning wizard</span></span>

<span data-ttu-id="99d32-134">[Windows 構成デザイナーのインストール](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)が完了した後、プロビジョニング パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-134">After you [install Windows Configuration Designer](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd), you can create a provisioning package.</span></span>

### <span data-ttu-id="99d32-135">プロビジョニング パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="99d32-135">Create the provisioning package</span></span> 

1. <span data-ttu-id="99d32-136">次の手順で Windows 構成デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="99d32-136">Open Windows Configuration Designer:</span></span>
   - <span data-ttu-id="99d32-137">スタート画面または [スタート] メニューの検索ウィンドウで、「Windows 構成デザイナー」と入力して Windows 構成デザイナーのショートカットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-137">From either the Start screen or Start menu search, type 'Windows Configuration Designer' and click on the Windows Configuration Designer shortcut,</span></span> 
    
     <span data-ttu-id="99d32-138">または</span><span class="sxs-lookup"><span data-stu-id="99d32-138">or</span></span>
    
   - <span data-ttu-id="99d32-139">Windows 構成デザイナーを ADK からインストールした場合は、`C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (x64 コンピューター) または `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (x86 コンピューター) に移動し、**ICD.exe** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-139">If you installed Windows Configuration Designer from the ADK, navigate to `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (on an x64 computer) or `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (on an x86 computer), and then double-click **ICD.exe**.</span></span>

2. <span data-ttu-id="99d32-140">**[プロビジョニング Surface Hub デバイス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-140">Click **Provision Surface Hub devices**.</span></span>

3. <span data-ttu-id="99d32-141">プロジェクトに名前を付け、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-141">Name your project and click **Next**.</span></span>

### <span data-ttu-id="99d32-142">設定の構成</span><span class="sxs-lookup"><span data-stu-id="99d32-142">Configure settings</span></span>

<table>
<tr><td style="width:45%" valign="top"><img src="images/one.png" alt="step one"/> <img src="images/add-certificates.png" alt="add certificates"/></br></br><span data-ttu-id="99d32-143">証明書を使ってデバイスをプロビジョニングするには、<strong>[証明書の追加]</strong> をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-143">To provision the device with a certificate, click <strong>Add a certificate</strong>.</span></span> <span data-ttu-id="99d32-144">証明書の名前を入力し、使用する証明書を表示して選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-144">Enter a name for the certificate, and then browse to and select the certificate to be used.</span></span></td><td><img src="images/add-certificates-details.png" alt="add a certificate"/></td></tr> 
<tr><td style="width:45%" valign="top"><img src="images/two.png" alt="step two"/>  <img src="images/proxy.png" alt="configure proxy settings"/></br></br><span data-ttu-id="99d32-145">プロキシ設定を <strong>[はい]</strong> または <strong>[いいえ]</strong> に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="99d32-145">Toggle <strong>Yes</strong> or <strong>No</strong> for proxy settings.</span></span> <span data-ttu-id="99d32-146">Surface Hub の既定の構成では、プロキシ設定が自動的に検出されます。設定を変更する必要がない場合は、<strong>[いいえ]</strong> を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-146">The default configuration for Surface Hub is to automatically detect proxy settings, so you can select <strong>No</strong> if that is the setting that you want.</span></span> <span data-ttu-id="99d32-147">ただし、それまでのプロキシ サーバーの使用を必要とするインフラストラクチャから、プロキシ サーバーを必要としないインフラストラクチャに変更した場合は、<strong>[はい]</strong> と <strong>[設定を自動的に検出]</strong> を選択することで、プロビジョニング パッケージを使って Surface Hub デバイスを既定の設定に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-147">However, if your infrastructure previously required using a proxy server and has changed to not require a proxy server, you can use a provisioning package to revert your Surface Hub devices to the default settings by selecting <strong>Yes</strong> and <strong>Automatically detect settings</strong>.</span></span> </br></br><span data-ttu-id="99d32-148"><strong>[はい]</strong> に切り替えると、プロキシ設定を自動的に検出するか、設定を手動で構成するかを選択でき、手動で構成する場合は、スクリプトを設定するための URL を入力するか、静的なプロキシ サーバー アドレスを入力できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-148">If you toggle <strong>Yes</strong>, you can select to automatically detect proxy settings, or you can manually configure the settings by entering a URL to a setup script, or a static proxy server address.</span></span> <span data-ttu-id="99d32-149">さらにローカルのアドレスにプロキシ サーバーを使うかどうか、また例外 (Surface Hub がプロキシ サーバーを使用せずに直接接続する必要があるアドレス) を入力するかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="99d32-149">You can also identify whether to use the proxy server for local addresses, and enter exceptions (addresses that Surface Hub should connect to directly without using the proxy server).</span></span>  </td><td><img src="images/proxy-details.png" alt="configure proxy settings"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/three.png" alt="step three"/>  <img src="images/set-up-device-admins.png" alt="device admins"/></br></br><span data-ttu-id="99d32-150">デバイスを Active Directory に登録し、設定アプリを使用するセキュリティ グループを指定するか、Azure Active Directory に登録してグローバル管理者が設定アプリを使用できる環境にするか、デバイス上にローカル管理者アカウントを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-150">You can enroll the device in Active Directory and specify a security group to use the Settings app, enroll in Azure Active Directory to allow global admins to use the Settings app, or create a local administrator account on the device.</span></span></br></br><span data-ttu-id="99d32-151">デバイスを Active Directory に登録するには、最小限の特権を持つユーザー アカウントの資格情報を入力して、デバイスをドメインに参加させ、Surface Hub で管理者資格情報を持つセキュリティ グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-151">To enroll the device in Active Directory, enter the credentials for a least-privileged user account to join the device to the domain, and specify the security group to have admin credentials on Surface Hub.</span></span> <span data-ttu-id="99d32-152">デバイスを Active Directory に登録するプロビジョニング パッケージを、リセットされた Surface Hub に適用する場合、同じドメイン アカウントを使用できるのは、表示されているアカウントがドメイン管理者である場合か、Surface Hub を最初に設定したのと同じアカウントである場合のみです。</span><span class="sxs-lookup"><span data-stu-id="99d32-152">If a provisioning package that enrolls a device in Active Directory is going to be applied to a Surface Hub that was reset, the same domain account can only be used if the account listed is a domain administrator or is the same account that set up the Surface Hub initially.</span></span> <span data-ttu-id="99d32-153">そうでない場合は、別のドメイン アカウントをプロビジョニング パッケージで使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-153">Otherwise, a different domain account must be used in the provisioning package.</span></span></br></br><span data-ttu-id="99d32-154">Windows 構成デザイナー ウィザードを使って Azure AD の登録を一括で構成する前に、<a href="https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup" data-raw-source="[set up Azure AD join in your organization](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup)">組織での Azure AD 参加の設定</a>を行います。</span><span class="sxs-lookup"><span data-stu-id="99d32-154">Before you use a Windows Configuration Designer wizard to configure bulk Azure AD enrollment, <a href="https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup" data-raw-source="[set up Azure AD join in your organization](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup)">set up Azure AD join in your organization</a>.</span></span> <span data-ttu-id="99d32-155">Azure AD テナントの <strong>[ユーザーあたりのデバイスの最大数]</strong> の設定は、ウィザードで利用できる一括トークンを使用できる回数を決定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-155">The <strong>maximum number of devices per user</strong> setting in your Azure AD tenant determines how many times the bulk token that you get in the wizard can be used.</span></span> <span data-ttu-id="99d32-156">Azure AD にデバイスを登録するには、そのオプションを選択して、ウィザードを使って取得する一括トークンのフレンドリ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-156">To enroll the device in Azure AD, select that option and enter a friendly name for the bulk token you will get using the wizard.</span></span> <span data-ttu-id="99d32-157">トークンの有効期限を設定します (最大、トークンの取得日から 30 日間)。</span><span class="sxs-lookup"><span data-stu-id="99d32-157">Set an expiration date for the token (maximum is 30 days from the date you get the token).</span></span> <span data-ttu-id="99d32-158"><strong>[一括トークンを取得する]</strong> をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-158">Click <strong>Get bulk token</strong>.</span></span> <span data-ttu-id="99d32-159"><strong>[&#39;s にサインインします </strong> ] ウィンドウで、Azure AD にデバイスを参加するためのアクセス許可を持つアカウントを入力し、その後、パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-159">In the <strong>Let&#39;s get you signed in</strong> window, enter an account that has permissions to join a device to Azure AD, and then the password.</span></span> <span data-ttu-id="99d32-160"><strong>[承諾]</strong> をクリックして、Windows 構成デザイナーに必要なアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="99d32-160">Click <strong>Accept</strong> to give Windows Configuration Designer the necessary permissions.</span></span></br></br><span data-ttu-id="99d32-161">ローカル管理者アカウントを作成するには、そのオプションを選択して、ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-161">To create a local administrator account, select that option and enter a user name and password.</span></span> </br></br><strong><span data-ttu-id="99d32-162">重要:</strong> プロビジョニング パッケージにローカル アカウントを作成する場合、42 日ごとに<strong>設定</strong>アプリを使ってパスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-162">Important:</strong> If you create a local account in the provisioning package, you must change the password using the <strong>Settings</strong> app every 42 days.</span></span> <span data-ttu-id="99d32-163">その期間内にパスワードを変更しない場合、アカウントがロックされてサインインできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-163">If the password is not changed during that period, the account might be locked out and unable to sign in.</span></span>  </td><td><img src="images/set-up-device-admins-details.png" alt="join Active Directory, Azure AD, or create a local admin account"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/four.png" alt="step four"/> <img src="images/enroll-mdm.png" alt="enroll in device management"/></br></br><span data-ttu-id="99d32-164">MDM への登録について、<strong>[はい]</strong> または <strong>[いいえ]</strong> を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="99d32-164">Toggle <strong>Yes</strong> or <strong>No</strong> for enrollment in MDM.</span></span> </br></br><span data-ttu-id="99d32-165"><strong>[はい]</strong> を選択した場合、デバイスの登録を許可されたサービス アカウントとパスワードまたは証明書サムプリントを指定し、併せて認証の種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-165">If you toggle <strong>Yes</strong>, you must provide a service account and password or certificate thumbprint that is authorized to enroll the device, and also specify the authentication type.</span></span> <span data-ttu-id="99d32-166">MDM プロバイダーで必要な場合は、探索サービス、登録サービス、ポリシー サービスの URL も入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-166">If required by your MDM provider, also enter the URLs for the discovery service, enrollment service, and policy service.</span></span> <a href="manage-settings-with-mdm-for-surface-hub.md" data-raw-source="[Learn more about managing Surface Hub with MDM.](manage-settings-with-mdm-for-surface-hub.md)"><span data-ttu-id="99d32-167">MDM による Surface Hub の管理について詳しく知る。</span><span class="sxs-lookup"><span data-stu-id="99d32-167">Learn more about managing Surface Hub with MDM.</span></span></a></td><td><img src="images/enroll-mdm-details.png" alt="enroll in mobile device management"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/five.png" alt="step five"/> <img src="images/add-applications.png" alt="add applications"/></br></br><span data-ttu-id="99d32-168">プロビジョニング パッケージには、複数のユニバーサル Windows プラットフォーム (UWP) アプリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="99d32-168">You can install multiple Universal Windows Platform (UWP) apps in a provisioning package.</span></span> <span data-ttu-id="99d32-169">設定について詳しくは「<a href="https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps" data-raw-source="[Provision PCs with apps](https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps)">アプリを使用して PC をプロビジョニングする</a>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99d32-169">For help with the settings, see <a href="https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps" data-raw-source="[Provision PCs with apps](https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps)">Provision PCs with apps</a>.</span></span> </br></br><strong><span data-ttu-id="99d32-170">重要: </strong> ウィザードインターフェイスで従来の Win32 アプリを選ぶことはできますが、Surface Hub に適用されるプロビジョニングパッケージには UWP アプリのみを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-170">Important:</strong> Although the wizard interface allows you to select a Classic Win32 app, only include UWP apps in a provisioning package that will be applied to Surface Hub.</span></span> <span data-ttu-id="99d32-171">従来の Win32 アプリを含めると、プロビジョニングが失敗します。</span><span class="sxs-lookup"><span data-stu-id="99d32-171">If you include a Classic Win32 app, provisioning will fail.</span></span> </td><td><img src="images/add-applications-details.png" alt="add an application"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/six.png" alt="step six"/>  <img src="images/add-config-file.png" alt="Add configuration file"/></br></br><span data-ttu-id="99d32-172">この手順では、どの設定も構成し&#39;ません。</span><span class="sxs-lookup"><span data-stu-id="99d32-172">You don&#39;t configure any settings in this step.</span></span> <span data-ttu-id="99d32-173">ここではデバイス アカウントの一覧が含まれた構成ファイルを含める手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="99d32-173">It provides instructions for including a configuration file that contains a list of device accounts.</span></span> <span data-ttu-id="99d32-174">構成ファイルには、列ヘッダーを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="99d32-174">The configuration file must not contain column headers.</span></span> <span data-ttu-id="99d32-175">プロビジョニング パッケージを Surface Hub に適用するときに、Surface Hub の構成ファイルが USB ドライブに含まれている場合は、アカウントとデバイスのフレンドリ名をファイルから選択できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-175">When you apply the provisioning package to Surface Hub, if a Surface Hub configuration file is included on the USB drive, you can select the account and friendly name for the device from the file.</span></span> <span data-ttu-id="99d32-176">例については、「<a href="#sample-configuration-file" data-raw-source="[Sample configuration file](#sample-configuration-file)">構成ファイルの例</a>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99d32-176">See <a href="#sample-configuration-file" data-raw-source="[Sample configuration file](#sample-configuration-file)">Sample configuration file</a> for an example.</span></span></br></br><strong><span data-ttu-id="99d32-177">重要: </strong> 構成ファイルは、既定のセットアップエクスペリエンス (OOBE) 中にのみ適用できます。また、windows 10 バージョン1703でリリースされた Windows 構成デザイナーを使って作成されたプロビジョニングパッケージでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-177">Important:</strong> The configuration file can only be applied during the out-of-box setup experience (OOBE) and can only be used with provisioning packages created using the Windows Configuration Designer released with Windows 10, version 1703.</span></span>  </td><td><img src="images/add-config-file-details.png" alt="Add a Surface Hub configuration file"/></td></tr>
<tr><td style="width:45%" valign="top">  <img src="images/finish.png" alt="finish"/></br></br><span data-ttu-id="99d32-178">プロビジョニング パッケージを保護するためのパスワードを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-178">You can set a password to protect your provisioning package.</span></span> <span data-ttu-id="99d32-179">プロビジョニング パッケージをデバイスに適用する場合は、このパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-179">You must enter this password when you apply the provisioning package to a device.</span></span></td><td><img src="images/finish-details.png" alt="Protect your package"/></td></tr>
</table>

<span data-ttu-id="99d32-180">完了したら、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-180">After you're done, click **Create**.</span></span> <span data-ttu-id="99d32-181">これは数秒で終わります。</span><span class="sxs-lookup"><span data-stu-id="99d32-181">It only takes a few seconds.</span></span> <span data-ttu-id="99d32-182">パッケージがビルドされると、ページの下部に、パッケージの格納場所がハイパーリンクで表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-182">When the package is built, the location where the package is stored is displayed as a hyperlink at the bottom of the page.</span></span>

## <span data-ttu-id="99d32-183">構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="99d32-183">Sample configuration file</span></span>

<span data-ttu-id="99d32-184">Surface Hub の構成ファイルには、デバイスが Exchange および Skype for Business との接続に使用できるデバイス アカウントの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="99d32-184">A Surface Hub configuration file contains a list of device accounts that your device can use to connect to Exchange and Skype for Business.</span></span> <span data-ttu-id="99d32-185">プロビジョニング パッケージを Surface Hub に適用するときに、構成ファイルを USB フラッシュ ドライブのルート ディレクトリに含めたうえで、そのデバイスに適用する適切なアカウントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-185">When you apply a provisioning package to Surface Hub, you can include a configuration file in the root directory of the USB flash drive, and then select the desired account to apply to that device.</span></span> <span data-ttu-id="99d32-186">構成ファイルは、アウトオブボックスの設定エクスペリエンス (OOBE) でのみ適用でき、Windows 10 バージョン 1703 でリリースされた Windows 構成デザイナーを使って作成したプロビジョニング パッケージでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-186">The configuration file can only be applied during the out-of-box setup experience (OOBE) and can only be used with provisioning packages created using the Windows Configuration Designer released with Windows 10, version 1703.</span></span>

<span data-ttu-id="99d32-187">Microsoft Excel などの CSV エディターを使って、`SurfaceHubConfiguration.csv` という名前の CSV ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d32-187">Use Microsoft Excel or other CSV editor to create a CSV file named `SurfaceHubConfiguration.csv`.</span></span> <span data-ttu-id="99d32-188">作成したファイルに、デバイス アカウントとフレンドリ名の一覧を次の形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-188">In the file, enter a list of device accounts and friendly names in this format:</span></span>

```
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```
>[!IMPORTANT]
><span data-ttu-id="99d32-189">構成ファイルではデバイス アカウントのパスワードがプレーンテキストで保存されるため、デバイスにプロビジョニング パッケージを適用した後、パスワードを更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="99d32-189">Because the configuration file stores the device account passwords in plaintext, we recommend that you update the passwords after you've applied the provisioning package to your devices.</span></span> <span data-ttu-id="99d32-190">MDM 経由でのパスワードの更新には、[Surface Hub 構成サービス プロバイダー (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) の [DeviceAccount ノード](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp#deviceaccount)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-190">You can use the [DeviceAccount node](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp#deviceaccount) in the [Surface Hub configuration service provider (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) to update the passwords via MDM.</span></span>


<span data-ttu-id="99d32-191">次に `SurfaceHubConfiguration.csv` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="99d32-191">The following is an example of `SurfaceHubConfiguration.csv`.</span></span> 

```
Rainier@contoso.com,password,Rainier Surface Hub
Adams@contoso.com,password,Adams Surface Hub
Baker@contoso.com,password,Baker Surface Hub
Glacier@constoso.com,password,Glacier Surface Hub
Stuart@contoso.com,password,Stuart Surface Hub
Fernow@contoso.com,password,Fernow Surface Hub
Goode@contoso.com,password,Goode Surface Hub
Shuksan@contoso.com,password,Shuksan Surface Hub
Buckner@contoso.com,password,Buckner Surface Hub
Logan@contoso.com,password,Logan Surface Hub
Maude@consoto.com,password,Maude Surface hub
Spickard@contoso.com,password,Spickard Surface Hub
Redoubt@contoso.com,password,Redoubt Surface Hub
Dome@contoso.com,password,Dome Surface Hub
Eldorado@contoso.com,password,Eldorado Surface Hub
Dragontail@contoso.com,password,Dragontail Surface Hub
Forbidden@contoso.com,password,Forbidden Surface Hub
Oval@contoso.com,password,Oval Surface Hub
StHelens@contoso.com,password,St Helens Surface Hub
Rushmore@contoso.com,password,Rushmore Surface Hub
```

## <span data-ttu-id="99d32-192">高度なプロビジョニングの使用</span><span class="sxs-lookup"><span data-stu-id="99d32-192">Use advanced provisioning</span></span>

<span data-ttu-id="99d32-193">[Windows 構成デザイナーのインストール](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)が完了した後、プロビジョニング パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-193">After you [install Windows Configuration Designer](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd), you can create a provisioning package.</span></span>

### <span data-ttu-id="99d32-194">プロビジョニング パッケージの作成 (上級)</span><span class="sxs-lookup"><span data-stu-id="99d32-194">Create the provisioning package (advanced)</span></span>

1. <span data-ttu-id="99d32-195">次の手順で Windows 構成デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="99d32-195">Open Windows Configuration Designer:</span></span>
   - <span data-ttu-id="99d32-196">スタート画面または [スタート] メニューの検索ウィンドウで、「Windows 構成デザイナー」と入力して Windows 構成デザイナーのショートカットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-196">From either the Start screen or Start menu search, type 'Windows Configuration Designer' and click on the Windows Configuration Designer shortcut,</span></span> 
    
     <span data-ttu-id="99d32-197">または</span><span class="sxs-lookup"><span data-stu-id="99d32-197">or</span></span>
    
   - <span data-ttu-id="99d32-198">Windows 構成デザイナーを ADK からインストールした場合は、`C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (x64 コンピューターを使用している場合) または `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (x86 コンピューターを使用している場合) に移動し、**ICD.exe** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-198">If you installed Windows Configuration Designer from the ADK, navigate to `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (on an x64 computer) or `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (on an x86 computer), and then double-click **ICD.exe**.</span></span>

2. <span data-ttu-id="99d32-199">**[プロビジョニングの詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-199">Click **Advanced provisioning**.</span></span>
   
3. <span data-ttu-id="99d32-200">プロジェクトに名前を付け、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-200">Name your project and click **Next**.</span></span>

4. <span data-ttu-id="99d32-201">**[Common to Windows 10 Team edition]** (Windows 10 Team Edition に共通) を選択し、**[次へ]** をクリックして、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-201">Select **Common to Windows 10 Team edition**, click **Next**, and then click **Finish**.</span></span>

    ![ICD の新しいプロジェクト](images/icd-new-project.png)

5. <span data-ttu-id="99d32-203">プロジェクトで、**[使用可能なカスタマイズ]** の **[一般的なチーム エディションの設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-203">In the project, under **Available customizations**, select **Common Team edition settings**.</span></span>

    ![ICD の一般的な設定](images/icd-common-settings.png)


### <span data-ttu-id="99d32-205">証明書をパッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="99d32-205">Add a certificate to your package</span></span>
<span data-ttu-id="99d32-206">プロビジョニング パッケージを使って、デバイスが Microsoft Exchange への認証に使う証明書をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-206">You can use provisioning packages to install certificates that will allow the device to authenticate to Microsoft Exchange.</span></span>

> [!NOTE]
> <span data-ttu-id="99d32-207">証明書をインストールできるのはデバイス (ローカル コンピューター) ストアのみで、ユーザー ストアにはインストールできません。</span><span class="sxs-lookup"><span data-stu-id="99d32-207">Provisioning packages can only install certificates to the device (local machine) store, and not to the user store.</span></span> <span data-ttu-id="99d32-208">組織でユーザー ストアに証明書をインストールする必要がある場合は、モバイル デバイス管理 (MDM) を使ってこれらの証明書を展開します。</span><span class="sxs-lookup"><span data-stu-id="99d32-208">If your organization requires that certificates must be installed to the user store, use Mobile Device Management (MDM) to deploy these certificates.</span></span> <span data-ttu-id="99d32-209">詳細については、MDM ソリューションのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d32-209">See your MDM solution documentation for details.</span></span>

1. <span data-ttu-id="99d32-210">**[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[Certificates]** > **[ClientCertificates]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-210">In the **Available customizations** pane, go to **Runtime settings** > **Certificates** > **ClientCertificates**.</span></span> 

2. <span data-ttu-id="99d32-211">**[CertificateName]** を入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-211">Enter a **CertificateName** and then click **Add**.</span></span> 

2. <span data-ttu-id="99d32-212">**[CertificatePassword]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-212">Enter the **CertificatePassword**.</span></span> 

3. <span data-ttu-id="99d32-213">**[CertificatePath]** で、証明書を探して選びます。</span><span class="sxs-lookup"><span data-stu-id="99d32-213">For **CertificatePath**, browse and select the certificate.</span></span> 

4. <span data-ttu-id="99d32-214">**[ExportCertificate]** を **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-214">Set **ExportCertificate** to **False**.</span></span>

5. <span data-ttu-id="99d32-215">**[KeyLocation]** で、**[ソフトウェアのみ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="99d32-215">For **KeyLocation**, select **Software only**.</span></span>


### <span data-ttu-id="99d32-216">ユニバーサル Windows プラットフォーム (UWP) アプリをパッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="99d32-216">Add a Universal Windows Platform (UWP) app to your package</span></span>
<span data-ttu-id="99d32-217">UWP アプリをプロビジョニング パッケージに追加する前に、アプリ パッケージ (.appx または .appxbundle) と依存関係ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="99d32-217">Before adding a UWP app to a provisioning package, you need the app package (either an .appx, or .appxbundle) and any dependency files.</span></span> <span data-ttu-id="99d32-218">ビジネス向け Microsoft Store からアプリを入手した場合は、*エンコードされていない*アプリのライセンスも必要です。</span><span class="sxs-lookup"><span data-stu-id="99d32-218">If you acquired the app from the Microsoft Store for Business, you will also need the *unencoded* app license.</span></span> <span data-ttu-id="99d32-219">ビジネス向け Microsoft Store からこれらの項目をダウンロードする方法については、「[オフライン アプリの配布](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99d32-219">See [Distribute offline apps](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app) to learn how to download these items from the Microsoft Store for Business.</span></span>

1. <span data-ttu-id="99d32-220">**[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[UniversalAppInstall]** > **[DeviceContextApp]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-220">In the **Available customizations** pane, go to **Runtime settings** > **UniversalAppInstall** > **DeviceContextApp**.</span></span>

2. <span data-ttu-id="99d32-221">アプリの **PackageFamilyName** を入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-221">Enter a **PackageFamilyName** for the app and then click **Add**.</span></span> <span data-ttu-id="99d32-222">一貫性を保つために、アプリのパッケージ ファミリ名を使います。</span><span class="sxs-lookup"><span data-stu-id="99d32-222">For consistency, use the app's package family name.</span></span> <span data-ttu-id="99d32-223">ビジネス向け Microsoft Store からアプリを入手した場合は、アプリのライセンスからパッケージ ファミリ名がわかります。</span><span class="sxs-lookup"><span data-stu-id="99d32-223">If you acquired the app from the Microsoft Store for Business, you can find the package family name in the app license.</span></span> <span data-ttu-id="99d32-224">テキストエディターを使用してライセンスファイルを開き、... タグの間の値を使います。 \<PFM\> \</PFM\></span><span class="sxs-lookup"><span data-stu-id="99d32-224">Open the license file using a text editor, and use the value between the \<PFM\>...\</PFM\> tags.</span></span>

3. <span data-ttu-id="99d32-225">**[ApplicationFile]** で、**[参照]** をクリックし、ターゲット アプリ (\*.appx または \*.appxbundle のどちらか) を探して選びます。</span><span class="sxs-lookup"><span data-stu-id="99d32-225">For **ApplicationFile**, click **Browse** to find and select the target app (either an \*.appx or \*.appxbundle).</span></span>

4. <span data-ttu-id="99d32-226">**[DependencyAppxFiles]** で、**[参照]** をクリックし、アプリの依存関係を探して追加します。</span><span class="sxs-lookup"><span data-stu-id="99d32-226">For **DependencyAppxFiles**, click **Browse** to find and add any dependencies for the app.</span></span> <span data-ttu-id="99d32-227">Surface Hub の場合、必要なのはこれらの依存関係の x64 バージョンだけです。</span><span class="sxs-lookup"><span data-stu-id="99d32-227">For Surface Hub, you will only need the x64 versions of these dependencies.</span></span>

<span data-ttu-id="99d32-228">ビジネス向け Microsoft Store からアプリを入手した場合は、プロビジョニング パッケージにアプリのライセンスを追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="99d32-228">If you acquired the app from the Microsoft Store for Business, you will also need to add the app license to your provisioning package.</span></span>

1. <span data-ttu-id="99d32-229">アプリのライセンスのコピーを作成し、その名前を拡張子 **.ms-windows-store-license** を使うように変更します。</span><span class="sxs-lookup"><span data-stu-id="99d32-229">Make a copy of the app license, and rename it to use a **.ms-windows-store-license** extension.</span></span> <span data-ttu-id="99d32-230">たとえば、"example.xml" は "example.ms-windows-store-license" になります。</span><span class="sxs-lookup"><span data-stu-id="99d32-230">For example, "example.xml" becomes "example.ms-windows-store-license".</span></span>

2. <span data-ttu-id="99d32-231">ICD の **[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[UniversalAppInstall]** > **[DeviceContextAppLicense]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-231">In ICD, in the **Available customizations** pane, go to **Runtime settings** > **UniversalAppInstall** > **DeviceContextAppLicense**.</span></span>

3. <span data-ttu-id="99d32-232">**[LicenseProductId]** を入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-232">Enter a **LicenseProductId** and then click **Add**.</span></span> <span data-ttu-id="99d32-233">一貫性を保つのために、アプリのライセンスにあるアプリのライセンス ID を使います。</span><span class="sxs-lookup"><span data-stu-id="99d32-233">For consistency, use the app's license ID from the app license.</span></span> <span data-ttu-id="99d32-234">テキスト エディタでライセンス ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="99d32-234">Open the license file using a text editor.</span></span> <span data-ttu-id="99d32-235">次に、タグで、 \<License\> **licenseid**属性の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="99d32-235">Then, in the \<License\> tag, use the value in the **LicenseID** attribute.</span></span>

4. <span data-ttu-id="99d32-236">新しい **[LicenseProductId]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-236">Select the new **LicenseProductId** node.</span></span> <span data-ttu-id="99d32-237">**[LicenseInstall]** では、**[参照]** をクリックして、手順 1 で名前を変更したライセンス ファイルを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-237">For **LicenseInstall**, click **Browse** to find and select the license file that you renamed in Step 1.</span></span>


### <span data-ttu-id="99d32-238">ポリシーをパッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="99d32-238">Add a policy to your package</span></span>
<span data-ttu-id="99d32-239">Surface Hub は、[ポリシー構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)のポリシーのサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="99d32-239">Surface Hub supports a subset of the policies in the [Policy configuration service provider](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx).</span></span> <span data-ttu-id="99d32-240">これらのポリシーの一部は ICD で構成できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-240">Some of those policies can be configured with ICD.</span></span>

1. <span data-ttu-id="99d32-241">**[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[ポリシー]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-241">In the **Available customizations** pane, go to **Runtime settings** > **Policies**.</span></span>

2. <span data-ttu-id="99d32-242">利用可能なポリシー領域のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-242">Select one of the available policy areas.</span></span>

3. <span data-ttu-id="99d32-243">プロビジョニング パッケージに追加するポリシーを選択して設定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-243">Select and set the policy you want to add to your provisioning package.</span></span>


### <span data-ttu-id="99d32-244">Surface Hub の設定をパッケージに追加する</span><span class="sxs-lookup"><span data-stu-id="99d32-244">Add Surface Hub settings to your package</span></span> 

<span data-ttu-id="99d32-245">[SurfaceHub 構成サービス プロバイダー](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx)から、設定をプロビジョニング パッケージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-245">You can add settings from the [SurfaceHub configuration service provider](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx) to your provisioning package.</span></span> 

1. <span data-ttu-id="99d32-246">**[利用可能なカスタマイズ]** ウィンドウで、**[実行時の設定]** > **[WindowsTeamSettings]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-246">In the **Available customizations** pane, go to **Runtime settings** > **WindowsTeamSettings**.</span></span>

2. <span data-ttu-id="99d32-247">利用可能な設定領域のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-247">Select one of the available setting areas.</span></span>

3. <span data-ttu-id="99d32-248">プロビジョニング パッケージに追加する設定を選択して設定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-248">Select and set the setting you want to add to your provisioning package.</span></span> 


## <span data-ttu-id="99d32-249">パッケージをビルドする</span><span class="sxs-lookup"><span data-stu-id="99d32-249">Build your package</span></span>

1. <span data-ttu-id="99d32-250">プロビジョニング パッケージの構成が完了したら、**[ファイル]** メニューの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-250">When you are done configuring the provisioning package, on the **File** menu, click **Save**.</span></span>

2. <span data-ttu-id="99d32-251">プロジェクト ファイルに機密情報が含まれている可能性があることを示す警告を確認し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-251">Read the warning that project files may contain sensitive information, and click **OK**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="99d32-252">プロビジョニング パッケージを作成する場合、プロジェクト ファイルとプロビジョニング パッケージ (.ppkg) ファイルに機密情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-252">When you build a provisioning package, you may include sensitive information in the project files and in the provisioning package (.ppkg) file.</span></span> <span data-ttu-id="99d32-253">.ppkg ファイルは暗号化するかどうかを選べますが、プロジェクト ファイルは暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="99d32-253">Although you have the option to encrypt the .ppkg file, project files are not encrypted.</span></span> <span data-ttu-id="99d32-254">プロジェクト ファイルは、安全な場所に保存し、不要になったときに削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-254">You should store the project files in a secure location and delete the project files when they are no longer needed.</span></span>

3. <span data-ttu-id="99d32-255">**[エクスポート]** メニューの **[プロビジョニング パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-255">On the **Export** menu, click **Provisioning package**.</span></span>

4. <span data-ttu-id="99d32-256">**[所有者]** を **[IT 管理者]** に変更して、このプロビジョニング パッケージの優先順位を他のソースからこのデバイスに適用されるプロビジョニング パッケージよりも高くします。</span><span class="sxs-lookup"><span data-stu-id="99d32-256">Change **Owner** to **IT Admin**, which will set the precedence of this provisioning package higher than provisioning packages applied to this device from other sources.</span></span>

5. <span data-ttu-id="99d32-257">**[パッケージのバージョン]** の値を設定し、**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-257">Set a value for **Package Version**, and then select **Next.**</span></span>

    > [!TIP]
    > <span data-ttu-id="99d32-258">既存のパッケージに変更を加えてバージョン番号を変更することで、以前に適用されたパッケージを更新できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-258">You can make changes to existing packages and change the version number to update previously applied packages.</span></span>

6. <span data-ttu-id="99d32-259">オプション: パッケージの暗号化を選択し、パッケージの署名を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="99d32-259">Optional: You can choose to encrypt the package and enable package signing.</span></span>

    -   <span data-ttu-id="99d32-260">**[パッケージの暗号化を有効にする]**: このオプションを選択した場合、自動生成されたパスワードが画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-260">**Enable package encryption** - If you select this option, an auto-generated password will be shown on the screen.</span></span>

    -   <span data-ttu-id="99d32-261">**[パッケージの署名を有効にする]**: このオプションを選択した場合、パッケージの署名に使用する有効な証明書を選ぶ必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-261">**Enable package signing** - If you select this option, you must select a valid certificate to use for signing the package.</span></span> <span data-ttu-id="99d32-262">**[参照]** をクリックし、パッケージの署名に使う証明書を選んで、証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-262">You can specify the certificate by clicking **Browse...** and choosing the certificate you want to use to sign the package.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="99d32-263">プロビジョニング パッケージに信頼済みプロビジョニング証明書を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="99d32-263">We recommend that you include a trusted provisioning certificate in your provisioning package.</span></span> <span data-ttu-id="99d32-264">パッケージがデバイスに適用されると、証明書がシステム ストアに追加されます。その後、システム メッセージを表示せずに、その証明書で署名されたすべてのパッケージを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-264">When the package is applied to a device, the certificate is added to the system store and any package signed with that certificate thereafter can be applied silently.</span></span> 

7. <span data-ttu-id="99d32-265">**[次へ]** をクリックし、ビルドしたプロビジョニング パッケージの出力先を指定します。</span><span class="sxs-lookup"><span data-stu-id="99d32-265">Click **Next** to specify the output location where you want the provisioning package to go once it's built.</span></span> <span data-ttu-id="99d32-266">既定では、Windows ICD はプロジェクト フォルダーを出力先として使います。</span><span class="sxs-lookup"><span data-stu-id="99d32-266">By default, Windows ICD uses the project folder as the output location.</span></span><p>
<span data-ttu-id="99d32-267">必要に応じて、 **[参照]** をクリックして既定の出力先を変更できます。</span><span class="sxs-lookup"><span data-stu-id="99d32-267">Optionally, you can click **Browse** to change the default output location.</span></span>

8. <span data-ttu-id="99d32-268">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-268">Click **Next**.</span></span>

9. <span data-ttu-id="99d32-269">パッケージのビルドを開始するには、 **[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-269">Click **Build** to start building the package.</span></span> <span data-ttu-id="99d32-270">ビルド ページにプロジェクト情報が表示され、進行状況バーでビルドの状態が示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-270">The project information is displayed in the build page and the progress bar indicates the build status.</span></span><p>
<span data-ttu-id="99d32-271">ビルドを取り消す必要がある場合は、**[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-271">If you need to cancel the build, click **Cancel**.</span></span> <span data-ttu-id="99d32-272">これにより、現在のビルド プロセスが取り消され、ウィザードが閉じられて、**[カスタマイズ ページ]** に戻ります。</span><span class="sxs-lookup"><span data-stu-id="99d32-272">This cancels the current build process, closes the wizard, and takes you back to the **Customizations Page**.</span></span>

10. <span data-ttu-id="99d32-273">ビルドに失敗した場合は、プロジェクト フォルダーへのリンクが含まれたエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-273">If your build fails, an error message will show up that includes a link to the project folder.</span></span> <span data-ttu-id="99d32-274">エラーの原因を特定するには、ログを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-274">You can scan the logs to determine what caused the error.</span></span> <span data-ttu-id="99d32-275">問題が解決したら、パッケージをもう一度ビルドしてみてください。</span><span class="sxs-lookup"><span data-stu-id="99d32-275">Once you fix the issue, try building the package again.</span></span><p>
<span data-ttu-id="99d32-276">ビルドに成功した場合は、プロビジョニング パッケージの名前、出力ディレクトリ、プロジェクト ディレクトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-276">If your build is successful, the name of the provisioning package, output directory, and project directory will be shown.</span></span>

    -   <span data-ttu-id="99d32-277">必要に応じて、パッケージの出力先として別のパスを選択し、もう一度プロビジョニング パッケージをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="99d32-277">If you choose, you can build the provisioning package again and pick a different path for the output package.</span></span> <span data-ttu-id="99d32-278">これを行うには、**[戻る]** をクリックして出力パッケージの名前とパスを変更し、**[次へ]** をクリックしてもう一度ビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="99d32-278">To do this, click **Back** to change the output package name and path, and then click **Next** to start another build.</span></span>
    
    -   <span data-ttu-id="99d32-279">完了したら、 **[完了]** をクリックしてウィザードを閉じ、 **[カスタマイズ ページ]** に戻ります。</span><span class="sxs-lookup"><span data-stu-id="99d32-279">If you are done, click **Finish** to close the wizard and go back to the **Customizations Page**.</span></span>

11. <span data-ttu-id="99d32-280">**[出力場所]** リンクを選び、パッケージの場所へ移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-280">Select the **output location** link to go to the location of the package.</span></span> <span data-ttu-id="99d32-281">.ppkg を空の USB フラッシュ ドライブにコピーします。</span><span class="sxs-lookup"><span data-stu-id="99d32-281">Copy the .ppkg to an empty USB flash drive.</span></span>


## <span data-ttu-id="99d32-282">プロビジョニング パッケージを Surface Hub に適用する</span><span class="sxs-lookup"><span data-stu-id="99d32-282">Apply a provisioning package to Surface Hub</span></span>

<span data-ttu-id="99d32-283">プロビジョニング パッケージを Surface Hub に展開するためのオプションは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="99d32-283">There are two options for deploying provisioning packages to a Surface Hub.</span></span> <span data-ttu-id="99d32-284">[初めて実行するウィザード](#apply-a-provisioning-package-during-first-run)では、証明書をインストールするプロビジョニングパッケージを適用できます。または、初回実行プログラムが完了した後、設定を使用して、設定、アプリ、証明書を構成するプロビジョニングパッケージを適用[できます。](#apply-a-package-using-settings)</span><span class="sxs-lookup"><span data-stu-id="99d32-284">[During the first run wizard](#apply-a-provisioning-package-during-first-run), you can apply a provisioning package that installs certificates, or after the first-run program is complete, you can apply a provisioning package that configures settings, apps, and certificates by using [Settings](#apply-a-package-using-settings).</span></span> 


### <span data-ttu-id="99d32-285">最初の実行時にプロビジョニング パッケージを適用する</span><span class="sxs-lookup"><span data-stu-id="99d32-285">Apply a provisioning package during first run</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99d32-286">初めて実行するプログラムでは、プロビジョニングパッケージを使って証明書をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-286">During the first-run program, you can only use provisioning packages to install certificates.</span></span> <span data-ttu-id="99d32-287">**設定**アプリを使って、アプリをインストールし、その他の設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="99d32-287">Use the **Settings** app to install apps and apply other settings.</span></span>

1. <span data-ttu-id="99d32-288">Surface Hub を初めて起動すると、[**[こんにちは]**](first-run-program-surface-hub.md#first-page) というページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-288">When you turn on the Surface Hub for the first time, the first-run program will display the [**Hi there page**](first-run-program-surface-hub.md#first-page).</span></span> <span data-ttu-id="99d32-289">操作を続行する前に、設定が適切に構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="99d32-289">Make sure that the settings are properly configured before proceeding.</span></span>

2. <span data-ttu-id="99d32-290">.ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。</span><span class="sxs-lookup"><span data-stu-id="99d32-290">Insert the USB flash drive containing the .ppkg file into the Surface Hub.</span></span> <span data-ttu-id="99d32-291">パッケージがドライブのルート ディレクトリにある場合は、初回実行プログラムによってそれが認識され、デバイスをセットアップするかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-291">If the package is in the root directory of the drive, the first-run program will recognize it and ask if you want to set up the device.</span></span> <span data-ttu-id="99d32-292">**[セットアップ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-292">Select **Set up**.</span></span>

    ![デバイスをセットアップしますか?](images/provisioningpackageoobe-01.png)

3. <span data-ttu-id="99d32-294">次にプロビジョニング元を選択する画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-294">The next screen asks you to select a provisioning source.</span></span> <span data-ttu-id="99d32-295">**[リムーバブル メディア]** を選んで **[次へ]** をタップします。</span><span class="sxs-lookup"><span data-stu-id="99d32-295">Select **Removable Media** and tap **Next**.</span></span>

    ![このデバイスのプロビジョニング](images/provisioningpackageoobe-02.png)
    
4. <span data-ttu-id="99d32-297">適用するプロビジョニング パッケージ (\*.ppkg) を選んで、**[次へ]** をタップします。</span><span class="sxs-lookup"><span data-stu-id="99d32-297">Select the provisioning package (\*.ppkg) that you want to apply, and tap **Next**.</span></span> <span data-ttu-id="99d32-298">最初の実行時にインストールできるパッケージは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="99d32-298">Note that you can only install one package during first run.</span></span>

    ![パッケージの選択](images/provisioningpackageoobe-03.png)

5. <span data-ttu-id="99d32-300">初回実行プログラムによって、プロビジョニング パッケージが適用される変更の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-300">The first-run program will show you a summary of the changes that the provisioning package will apply.</span></span> <span data-ttu-id="99d32-301">**[はい、追加する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-301">Select **Yes, add it**.</span></span>  

    ![このパッケージを信頼しますか?](images/provisioningpackageoobe-04.png)
    
6. <span data-ttu-id="99d32-303">構成ファイルが USB フラッシュ ドライブのルート ディレクトリに含まれる場合、**[構成を選択します]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-303">If a configuration file is included in the root directory of the USB flash drive, you will see **Select a configuration**.</span></span> <span data-ttu-id="99d32-304">構成ファイルの最初のデバイス アカウントが、Surface Hub に適用されるアカウント情報の概要と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-304">The first device account in the configuration file will be shown with a summary of the account information that will be applied to the Surface Hub.</span></span>

    ![構成を選択します](images/ppkg-config.png)    

7. <span data-ttu-id="99d32-306">**[構成を選択します]** で、適用するデバイス名を選択し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99d32-306">In **Select a configuration**, select the device name to apply, and then click **Next**.</span></span>

    ![デバイスのフレンドリ名を選択します](images/ppkg-csv.png)
    
<span data-ttu-id="99d32-308">プロビジョニング パッケージに含まれている設定がデバイスに適用され、OOBE が完了します。</span><span class="sxs-lookup"><span data-stu-id="99d32-308">The settings from the provisioning package will be applied to the device and OOBE will be complete.</span></span> <span data-ttu-id="99d32-309">デバイスの再起動後、USB フラッシュ ドライブを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="99d32-309">After the device restarts, you can remove the USB flash drive.</span></span>

### <span data-ttu-id="99d32-310">設定を使ってパッケージを適用する</span><span class="sxs-lookup"><span data-stu-id="99d32-310">Apply a package using Settings</span></span>

1. <span data-ttu-id="99d32-311">.ppkg ファイルを格納した USB フラッシュ ドライブを Surface Hub に挿入します。</span><span class="sxs-lookup"><span data-stu-id="99d32-311">Insert the USB flash drive containing the .ppkg file into the Surface Hub.</span></span>

2. <span data-ttu-id="99d32-312">Surface Hub から**設定**を起動し、メッセージが表示されたら管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="99d32-312">From the Surface Hub, start **Settings** and enter the admin credentials when prompted.</span></span>

3. <span data-ttu-id="99d32-313">**[Surface Hub]** > **[デバイス管理]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="99d32-313">Navigate to **Surface Hub** > **Device management**.</span></span> <span data-ttu-id="99d32-314">**[プロビジョニング パッケージ]** で、**[プロビジョニング パッケージを追加または削除する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-314">Under **Provisioning packages**, select **Add or remove a provisioning package**.</span></span>

4. <span data-ttu-id="99d32-315">**[パッケージの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-315">Select **Add a package**.</span></span>

5. <span data-ttu-id="99d32-316">プロビジョニング パッケージを選択し、**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-316">Choose your provisioning package and select **Add**.</span></span> <span data-ttu-id="99d32-317">求められた場合は、管理者の資格情報を再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d32-317">You may have to re-enter the admin credentials if prompted.</span></span>

6. <span data-ttu-id="99d32-318">プロビジョニング パッケージによって適用される変更の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d32-318">You'll see a summary of the changes that the provisioning package will apply.</span></span> <span data-ttu-id="99d32-319">**[はい、追加する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="99d32-319">Select **Yes, add it**.</span></span>


