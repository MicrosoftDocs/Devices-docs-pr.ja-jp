---
title: 管理者グループの管理
description: デバイスで設定アプリを起動すると、すべての Microsoft Surface Hub を個別に構成できます。
ms.assetid: FA67209E-B355-4333-B903-482C4A3BDCCE
ms.reviewer: ''
manager: laurawi
keywords: 管理者グループの管理, 設定アプリ, Surface Hub の構成
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: medium
ms.openlocfilehash: 36c6010307603b36b8798a09aed26f8b337b2c1b
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "11311953"
---
# <span data-ttu-id="d5e38-104">Surface Hub の管理グループの管理</span><span class="sxs-lookup"><span data-stu-id="d5e38-104">Admin group management for Surface Hub</span></span>


<span data-ttu-id="d5e38-105">デバイスで設定アプリを使用すると、すべての Surface Hub をローカルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-105">Every Surface Hub can be configured locally using the Settings app on the device.</span></span> <span data-ttu-id="d5e38-106">承認されていないユーザーによって設定が変更されるのを防ぐため、設定アプリでは、アプリを起動する際に管理者の資格情報が求められます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-106">To prevent unauthorized users from changing settings, the Settings app requires admin credentials to open the app.</span></span>


## <span data-ttu-id="d5e38-107">管理者グループの管理</span><span class="sxs-lookup"><span data-stu-id="d5e38-107">Admin Group Management</span></span>

<span data-ttu-id="d5e38-108">デバイスの管理者アカウントは、次の方法で設定できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-108">You can set up administrator accounts for the device in the following ways:</span></span>

- [<span data-ttu-id="d5e38-109">ローカル管理者アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="d5e38-109">Create a local admin account</span></span>](#create-a-local-admin-account)
- [<span data-ttu-id="d5e38-110">デバイスを Active Directory にドメイン参加する</span><span class="sxs-lookup"><span data-stu-id="d5e38-110">Domain join the device to Active Directory</span></span>](#domain-join-the-device-to-active-directory)
- [<span data-ttu-id="d5e38-111">Azure ADデバイスに参加する</span><span class="sxs-lookup"><span data-stu-id="d5e38-111">Azure AD join the device</span></span>](#azure-ad-join-the-device)
- [<span data-ttu-id="d5e38-112">参加しているデバイスに Azure AD管理者以外のアカウントを構成する (Surface Hub 2S)</span><span class="sxs-lookup"><span data-stu-id="d5e38-112">Configure non Global admin accounts on Azure AD joined devices (Surface Hub 2S)</span></span>](#configure-non-global-admin-accounts-on-azure-ad-joined-devices)


### <span data-ttu-id="d5e38-113">ローカル管理者アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="d5e38-113">Create a local admin account</span></span>

<span data-ttu-id="d5e38-114">ローカル管理者を作成するには、[最初の実行時にローカル管理者の使用を選択します](first-run-program-surface-hub.md#use-a-local-admin)。</span><span class="sxs-lookup"><span data-stu-id="d5e38-114">To create a local admin, [choose to use a local admin during first run](first-run-program-surface-hub.md#use-a-local-admin).</span></span> <span data-ttu-id="d5e38-115">これにより、Surface Hub に、選択したユーザー名とパスワードを使用するローカル管理者アカウントが 1 つ作成されます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-115">This will create a single local admin account on the Surface Hub with the username and password of your choice.</span></span> <span data-ttu-id="d5e38-116">これらの資格情報を使用して、設定アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-116">Use these credentials to open the Settings app.</span></span>

<span data-ttu-id="d5e38-117">ローカル管理者アカウントの情報は、ディレクトリ サービスによってサポートされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5e38-117">Note that the local admin account information is not backed by any directory service.</span></span> <span data-ttu-id="d5e38-118">デバイスで Active Directory (AD) または Azure Active Directory (Azure AD) にアクセスできない場合にのみ、ローカル管理者を選ぶことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-118">We recommend you only choose a local admin if the device does not have access to Active Directory (AD) or Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="d5e38-119">ローカル管理者のパスワードを変更する場合は、[設定] で変更できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-119">If you decide to change the local admin’s password, you can do so in Settings.</span></span> <span data-ttu-id="d5e38-120">ただし、ローカル管理者アカウントの使用からドメインまたは Azure AD テナントのグループの使用に変更する場合は、[デバイスをリセット](device-reset-surface-hub.md)して、初回設定プログラムを再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-120">However, if you want to change from using the local admin account to using a group from your domain or Azure AD tenant, then you’ll need to [reset the device](device-reset-surface-hub.md) and go through the first-time program again.</span></span>

### <span data-ttu-id="d5e38-121">デバイスを Active Directory にドメイン参加</span><span class="sxs-lookup"><span data-stu-id="d5e38-121">Domain join the device to Active Directory</span></span>

<span data-ttu-id="d5e38-122">Surface Hub を AD ドメインに参加させると、指定したセキュリティ グループのユーザーが設定を構成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-122">You can domain join the Surface Hub to your AD domain to allow users from a specified security group to configure settings.</span></span> <span data-ttu-id="d5e38-123">初回実行時に、[Active Directory ドメイン サービス](first-run-program-surface-hub.md#use-active-directory-domain-services)の使用を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-123">During first run, choose to use [Active Directory Domain Services](first-run-program-surface-hub.md#use-active-directory-domain-services).</span></span> <span data-ttu-id="d5e38-124">選択したドメインに参加させる権限のある資格情報と既存のセキュリティ グループの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-124">You'll need to provide credentials that are capable of joining the domain of your choice, and the name of an existing security group.</span></span> <span data-ttu-id="d5e38-125">そのセキュリティ グループのメンバーであるユーザーが自身の資格情報を入力すると、設定のロックを解除できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-125">Anyone who is a member of that security group can enter their credentials and unlock Settings.</span></span>

#### <span data-ttu-id="d5e38-126">Surface Hub をドメインに参加させた場合の動作</span><span class="sxs-lookup"><span data-stu-id="d5e38-126">What happens when you domain join your Surface Hub?</span></span>
<span data-ttu-id="d5e38-127">Surface Hub をドメインに参加させると、次のような処理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-127">Surface Hubs use domain join to:</span></span>
- <span data-ttu-id="d5e38-128">AD 内の指定したセキュリティ グループのメンバーに管理者権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-128">Grant admin rights to members of a specified security group in AD.</span></span>
- <span data-ttu-id="d5e38-129">デバイスの BitLocker 回復キーを AD のコンピューター オブジェクトに保存することによって、BitLocker 回復キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-129">Backup the device's BitLocker recovery key by storing it under the computer object in AD.</span></span> <span data-ttu-id="d5e38-130">詳しくは、「[BitLocker キーの保存](save-bitlocker-key-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d5e38-130">See [Save your BitLocker key](save-bitlocker-key-surface-hub.md) for details.</span></span>
- <span data-ttu-id="d5e38-131">暗号化された通信用にシステム クロックをドメイン コントローラーと同期します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-131">Synchronize the system clock with the domain controller for encrypted communication</span></span>

<span data-ttu-id="d5e38-132">Surface Hub では、ドメイン コントローラーからグループ ポリシーまたは証明書を適用することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d5e38-132">Surface Hub does not support applying group policies or certificates from the domain controller.</span></span>

> [!NOTE]
> <span data-ttu-id="d5e38-133">Surface Hub にドメインとの信頼がなくなった場合 (たとえば、ドメイン参加後にドメインから Surface Hub を削除する場合)、デバイスに対して認証を受けて設定を開くことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-133">If your Surface Hub loses trust with the domain (for example, if you remove the Surface Hub from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings.</span></span> <span data-ttu-id="d5e38-134">Surface Hub とドメインとの信頼関係を削除する場合は、先に[デバイスをリセット](device-reset-surface-hub.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-134">If you decide to remove the trust relationship of the Surface Hub with your domain, [reset the device](device-reset-surface-hub.md) first.</span></span>


### <span data-ttu-id="d5e38-135">Azure ADデバイスに参加する</span><span class="sxs-lookup"><span data-stu-id="d5e38-135">Azure AD join the device</span></span>

<span data-ttu-id="d5e38-136">Azure Active Directory (Azure AD) を使用して Surface Hub に参加すると、Azure AD テナントの IT 管理者が設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-136">You can Azure Active Directory (Azure AD) to join the Surface Hub to allow IT pros from your Azure AD tenant to configure settings.</span></span> <span data-ttu-id="d5e38-137">初回実行時に、[Microsoft Azure Active Directory](first-run-program-surface-hub.md#use-microsoft-azure-active-directory) の使用を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-137">During first run, choose to use [Microsoft Azure Active Directory](first-run-program-surface-hub.md#use-microsoft-azure-active-directory).</span></span> <span data-ttu-id="d5e38-138">選択した Azure AD テナントに参加させることのできる資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-138">You will need to provide credentials that are capable of joining the Azure AD tenant of your choice.</span></span> <span data-ttu-id="d5e38-139">Azure AD への参加が正常に完了すると、適切なユーザーにデバイスの管理者権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-139">After you successfully Azure AD join, the appropriate people will be granted admin rights on the device.</span></span>

<span data-ttu-id="d5e38-140">既定では、すべての**グローバル管理者**に、Azure AD に参加している Surface Hub の管理者権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-140">By default, all **global administrators** will be given admin rights on an Azure AD joined Surface Hub.</span></span> <span data-ttu-id="d5e38-141">**Azure AD Premium** または **Enterprise Mobility Suite (EMS)** では、その他の管理者を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-141">With **Azure AD Premium** or **Enterprise Mobility Suite (EMS)**, you can add additional administrators:</span></span>
1.  <span data-ttu-id="d5e38-142">[Azure クラシック ポータル](https://manage.windowsazure.com/)で、**[Active Directory]** をクリックし、組織のディレクトリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-142">In the [Azure classic portal](https://manage.windowsazure.com/), click **Active Directory**, and then click the name of your organization's directory.</span></span>
2.  <span data-ttu-id="d5e38-143">**[構成]** ページの **[デバイス]** > **[Azure AD 参加済みデバイスの追加の管理者]** で、**[選択済み]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-143">On the **Configure** page, under **Devices** > **Additional administrators on Azure AD joined devices**, click **Selected**.</span></span>
3.  <span data-ttu-id="d5e38-144">**[追加]** をクリックし、Surface Hub や他の Azure AD 参加済みデバイスの管理者として追加するユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-144">Click **Add**, and select the users you want to add as administrators on your Surface Hub and other Azure AD joined devices.</span></span>
4.  <span data-ttu-id="d5e38-145">作業が完了したら、チェックマーク ボタンをクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-145">When you have finished, click the checkmark button to save your change.</span></span>

#### <span data-ttu-id="d5e38-146">Surface Hub を Azure AD に参加させた場合の動作</span><span class="sxs-lookup"><span data-stu-id="d5e38-146">What happens when you Azure AD join your Surface Hub?</span></span>
<span data-ttu-id="d5e38-147">Surface Hub を Azure AD に参加させると、次のような処理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d5e38-147">Surface Hubs use Azure AD join to:</span></span>
- <span data-ttu-id="d5e38-148">Azure AD テナントの適切なユーザーに管理者権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="d5e38-148">Grant admin rights to the appropriate users in your Azure AD tenant.</span></span>
- <span data-ttu-id="d5e38-149">デバイスの BitLocker 回復キーを、Azure AD にデバイスを参加させるときに使用したアカウントに保存することによって、BitLocker 回復キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-149">Backup the device's BitLocker recovery key by storing it under the account that was used to Azure AD join the device.</span></span> <span data-ttu-id="d5e38-150">詳しくは、「[BitLocker キーの保存](save-bitlocker-key-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d5e38-150">See [Save your BitLocker key](save-bitlocker-key-surface-hub.md) for details.</span></span>

#### <span data-ttu-id="d5e38-151">Azure Active Directory への参加による自動登録</span><span class="sxs-lookup"><span data-stu-id="d5e38-151">Automatic enrollment via Azure Active Directory join</span></span>

<span data-ttu-id="d5e38-152">Surface Hub では、デバイスを Azure Active Directory に参加することで、Intune に自動的に登録する機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-152">Surface Hub now supports the ability to automatically enroll in Intune by joining the device to Azure Active Directory.</span></span> 

<span data-ttu-id="d5e38-153">詳しくは [、「Windows 10 の自動登録を有効にする」をご覧ください](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)。</span><span class="sxs-lookup"><span data-stu-id="d5e38-153">For more information, see [Enable Windows 10 automatic enrollment](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment).</span></span>

#### <span data-ttu-id="d5e38-154">選択に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d5e38-154">Which should I choose?</span></span>

<span data-ttu-id="d5e38-155">組織で AD または Azure AD を使用している場合は、主にセキュリティ上の理由から、ドメインまたは Azure AD に参加させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d5e38-155">If your organization is using AD or Azure AD, we recommend you either domain join or Azure AD join, primarily for security reasons.</span></span> <span data-ttu-id="d5e38-156">ユーザーは、自身の資格情報を使用して、認証を行ったり、設定のロックを解除することができ、ドメインに関連付けられているセキュリティ グループの内外に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-156">People will be able to authenticate and unlock Settings with their own credentials, and can be moved in or out of the security groups associated with your domain.</span></span>

| <span data-ttu-id="d5e38-157">オプション</span><span class="sxs-lookup"><span data-stu-id="d5e38-157">Option</span></span>                                            | <span data-ttu-id="d5e38-158">要件</span><span class="sxs-lookup"><span data-stu-id="d5e38-158">Requirements</span></span>                            | <span data-ttu-id="d5e38-159">設定アプリへのアクセスに使用できる資格情報</span><span class="sxs-lookup"><span data-stu-id="d5e38-159">Which credentials can be used to access the Settings app?</span></span>  |
|---------------------------------------------------|-----------------------------------------|-------|
| <span data-ttu-id="d5e38-160">ローカル管理者アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="d5e38-160">Create a local admin account</span></span>                      | <span data-ttu-id="d5e38-161">なし</span><span class="sxs-lookup"><span data-stu-id="d5e38-161">None</span></span>                                    | <span data-ttu-id="d5e38-162">初回実行時に指定したユーザー名とパスワード</span><span class="sxs-lookup"><span data-stu-id="d5e38-162">The user name and password specified during first run</span></span> |
| <span data-ttu-id="d5e38-163">Active Directory (AD) ドメインに参加させる</span><span class="sxs-lookup"><span data-stu-id="d5e38-163">Domain join to Active Directory (AD)</span></span>              | <span data-ttu-id="d5e38-164">組織で AD を使用している</span><span class="sxs-lookup"><span data-stu-id="d5e38-164">Your organization uses AD</span></span>               | <span data-ttu-id="d5e38-165">ドメイン内の特定のセキュリティ グループに属する任意の AD ユーザー</span><span class="sxs-lookup"><span data-stu-id="d5e38-165">Any AD user from a specific security group in your domain</span></span> |
| <span data-ttu-id="d5e38-166">デバイスを Azure Active Directory (Azure AD) に参加させる</span><span class="sxs-lookup"><span data-stu-id="d5e38-166">Azure Active Directory (Azure AD) join the device</span></span> | <span data-ttu-id="d5e38-167">組織で Azure AD Basic を使用している</span><span class="sxs-lookup"><span data-stu-id="d5e38-167">Your organization uses Azure AD Basic</span></span>   | <span data-ttu-id="d5e38-168">グローバル管理者のみ</span><span class="sxs-lookup"><span data-stu-id="d5e38-168">Global administrators only</span></span> |
| &nbsp;                                            | <span data-ttu-id="d5e38-169">組織でAzure AD Premium または Enterprise Mobility Suite (EMS) を使用している</span><span class="sxs-lookup"><span data-stu-id="d5e38-169">Your organization uses Azure AD Premium or Enterprise Mobility Suite (EMS)</span></span> | <span data-ttu-id="d5e38-170">グローバル管理者と追加の管理者</span><span class="sxs-lookup"><span data-stu-id="d5e38-170">Global administrators and additional administrators</span></span> |


### <span data-ttu-id="d5e38-171">Azure に参加しているデバイスでグローバル管理者ADアカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="d5e38-171">Configure non Global admin accounts on Azure AD-joined devices</span></span>

<span data-ttu-id="d5e38-172">Azure AD に参加している Surface Hub 2S デバイスの場合、Windows 10 Team 2020 Update では、Surface Hub 2S の設定アプリの管理に対する管理者権限を制限できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-172">For Surface Hub 2S devices joined to Azure AD, Windows 10 Team 2020 Update lets you limit admin permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="d5e38-173">これにより、Surface Hub 2S の管理者アクセス許可のみをスコープ設定し、望ましくない可能性のある管理者が Azure AD ドメイン全体にアクセスすることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="d5e38-173">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access an entire Azure AD domain.</span></span> <span data-ttu-id="d5e38-174">詳細については [、「Surface Hub 2S でグローバル管理者以外のアカウントを構成する」を参照してください](surface-hub-2s-nonglobal-admin.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e38-174">To learn more, see [Configure non Global admin accounts on Surface Hub 2S](surface-hub-2s-nonglobal-admin.md).</span></span>