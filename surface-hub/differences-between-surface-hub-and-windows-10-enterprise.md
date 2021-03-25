---
title: オペレーティングシステムの基礎 (Surface Hub)
description: このトピックでは、Windows 10 Team オペレーティング システムの固有の側面と、Windows 10 Enterprise との違いについて説明します。
keywords: 変更履歴
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/23/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 9c76f9405146c5cda4afe6b46ce7e1cce0062682
ms.sourcegitcommit: 88ce9e77afdc3d09984edc05286cd0f1eb054223
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "11448301"
---
# <a name="operating-system-essentials-surface-hub"></a><span data-ttu-id="7b637-104">オペレーティングシステムの基礎 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="7b637-104">Operating system essentials (Surface Hub)</span></span>

<span data-ttu-id="7b637-105">Surface Hub のオペレーティング システムである Windows 10 Team は Windows 10 Enterprise をベースとしていて、エンタープライズ管理、セキュリティ、およびその他の機能の豊富なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b637-105">The Surface Hub operating system, Windows 10 Team, is based on Windows 10 Enterprise, providing rich support for enterprise management, security, and other features.</span></span> <span data-ttu-id="7b637-106">しかし、これらの間には重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="7b637-106">However, there are important differences between them.</span></span> <span data-ttu-id="7b637-107">Enterprise エディションは、PC 向けに設計されていますが、Windows 10 Team は大画面および会議室での使用向けに新たに設計されています。</span><span class="sxs-lookup"><span data-stu-id="7b637-107">While the Enterprise edition is designed for PCs, Windows 10 Team is designed from the ground up for large screens and meeting rooms.</span></span> <span data-ttu-id="7b637-108">Surface Hub のセキュリティおよび管理の要件を評価する場合、新しいオペレーティング システムと見なすことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7b637-108">When you evaluate security and management requirements for Surface Hub, it's best to consider it as a new operating system.</span></span> <span data-ttu-id="7b637-109">この記事は、Surface Hub の Windows 10 Team と Windows 10 Enterprise の主な相違点と、その相違点が組織にどう影響を与えるかを示すことを目的としています。</span><span class="sxs-lookup"><span data-stu-id="7b637-109">This article is designed to help highlight the key differences between Windows 10 Team on Surface Hub and Windows 10 Enterprise, and what the differences mean for your organization.</span></span>

<span data-ttu-id="7b637-110">2020 年 9 月から、お客様は Surface Hub 2S で Windows 10 Pro または Enterprise に移行できます。</span><span class="sxs-lookup"><span data-stu-id="7b637-110">Beginning in September 2020, customers have the option of migrating to Windows 10 Pro or Enterprise on Surface Hub 2S.</span></span> <span data-ttu-id="7b637-111">詳しくは、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7b637-111">To learn more, see the following:</span></span>

- <span data-ttu-id="7b637-112">[Surface Hub 2 での Windows 10 Pro と Enterprise の可用性を発表します](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/announcing-the-availability-of-windows-10-pro-and-enterprise-on/ba-p/1624107)。</span><span class="sxs-lookup"><span data-stu-id="7b637-112">[Announcing the availability of Windows 10 Pro and Enterprise on Surface Hub 2](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/announcing-the-availability-of-windows-10-pro-and-enterprise-on/ba-p/1624107).</span></span>

- [<span data-ttu-id="7b637-113">Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</span><span class="sxs-lookup"><span data-stu-id="7b637-113">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>](surface-hub-2s-migrate-os.md)

## <a name="user-interface"></a><span data-ttu-id="7b637-114">ユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b637-114">User interface</span></span>

### <a name="shell-os-user-interface"></a><span data-ttu-id="7b637-115">シェル (OSのユーザー インターフェイス)</span><span class="sxs-lookup"><span data-stu-id="7b637-115">Shell (OS user interface)</span></span>

<span data-ttu-id="7b637-116">Surface Hub のシェルは、大画面での表示およびタッチ操作向けに、新たに設計されています。</span><span class="sxs-lookup"><span data-stu-id="7b637-116">The Surface Hub's shell is designed from the ground up to be large screen and touch optimized.</span></span> <span data-ttu-id="7b637-117">Windows 10 Enterprise と同じシェルは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-117">It doesn't use the same shell as Windows 10 Enterprise.</span></span>

*<span data-ttu-id="7b637-118">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-118">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-119">Windows 10 Enterprise のシェルのコントロールに関する設定は、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-119">Settings related to controls in the Windows 10 Enterprise shell don't apply for Surface Hub.</span></span>

### <a name="lock-screen-and-screensaver"></a><span data-ttu-id="7b637-120">ロック画面とスクリーン セーバー</span><span class="sxs-lookup"><span data-stu-id="7b637-120">Lock screen and screensaver</span></span>

<span data-ttu-id="7b637-121">Surface Hub にはロック画面やスクリーン セーバーがありませんが、ようこそ画面と呼ばれる同様の機能があります。</span><span class="sxs-lookup"><span data-stu-id="7b637-121">Surface Hub doesn't have a lock screen or a screen saver, but it has a similar feature called the welcome screen.</span></span> <span data-ttu-id="7b637-122">ようこそ画面には、デバイス アカウントのカレンダーでスケジュール設定済みの会議、および Skype for Business、ホワイトボード、接続といった Surface Hub のトップ アプリへの簡易エントリ ポイントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b637-122">The welcome screen shows scheduled meetings from the device account's calendar, and easy entry points to the Surface Hub's top apps - Skype for Business, Whiteboard, and Connect.</span></span>

*<span data-ttu-id="7b637-123">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-123">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-124">ロック画面、画面のタイムアウト、およびスクリーン セーバーの設定は、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-124">Settings for lock screen, screen timeout, and screen saver don't apply for Surface Hub.</span></span>

### <a name="user-sign-in"></a><span data-ttu-id="7b637-125">ユーザー サインイン</span><span class="sxs-lookup"><span data-stu-id="7b637-125">User sign-in</span></span>

<span data-ttu-id="7b637-126">Surface Hub は、会議室などの共同スペースで使用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="7b637-126">Surface Hub is designed to be used in communal spaces, such as meeting rooms.</span></span> <span data-ttu-id="7b637-127">Windows PC とは異なり、ユーザーにサインインが求められることなく、だれでも Surface Hub を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b637-127">Unlike Windows PCs, anyone can walk up and use a Surface Hub without requiring a user to sign in.</span></span> <span data-ttu-id="7b637-128">この共有機能を有効にするために、Surface Hub では、Windows 10 Enterprise のような (ユーザーが OS にサインインして、その資格情報が OS 全体で使用される形式の) Windows サインインがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-128">To enable this communal functionality, Surface Hub does not support Windows sign-in the same way that Windows 10 Enterprise does (e.g., signing in a user to the OS and using those credentials throughout the OS).</span></span> <span data-ttu-id="7b637-129">代わりに、ローカルで自動サインインの低特権ユーザーが、常に Surface Hub にログインしているという形になります。</span><span class="sxs-lookup"><span data-stu-id="7b637-129">Instead, there is always a local, auto signed-in, low-privilege user signed in to the Surface Hub.</span></span> <span data-ttu-id="7b637-130">管理ユーザーを含めて、追加ユーザーのサインインはサポートされません (つまり、管理者がサインインしても、OS へのサインインではありません)。</span><span class="sxs-lookup"><span data-stu-id="7b637-130">It doesn't support signing in any additional users, including admin users (e.g., when an admin signs in, they are not signed in to the OS).</span></span>

<span data-ttu-id="7b637-131">ユーザーは Surface Hub にサインインできますが、OS へのサインインにはなりません。</span><span class="sxs-lookup"><span data-stu-id="7b637-131">Users can sign in to a Surface Hub, but they will not be signed in to the OS.</span></span> <span data-ttu-id="7b637-132">たとえば、ユーザーがアプリまたは "会議とファイル" にサインインしても、このユーザーは OS ではなくアプリまたはサービスにサインインしているだけです。</span><span class="sxs-lookup"><span data-stu-id="7b637-132">For example, when a user signs in to Apps or My Meetings and Files, the users is signed in only to the apps or services, not to the OS.</span></span> <span data-ttu-id="7b637-133">結果として、サインインしたユーザーは、自身のクラウド ファイルや、クラウドに保存されている個人的な会議を取得できますが、**[セッションの終了]** が有効になると資格情報が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="7b637-133">As a result, the signed-in user is able to retrieve their cloud files and personal meetings stored in the cloud, and these credentials are discarded when **End session** is activated.</span></span>


*<span data-ttu-id="7b637-134">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-134">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-135">通常、Surface Hub ではセキュリティ強化のため、ユーザー アクセス制御ではなくロックダウン機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b637-135">Generally, Surface Hub uses lockdown features rather than user access control to enforce security.</span></span> <span data-ttu-id="7b637-136">パスワード要件、対話型ログオン、ユーザー アカウント、およびアクセス制御に関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-136">Policies related to password requirements, interactive logon, user accounts, and access control don't apply for Surface Hub.</span></span>

### <a name="saving-and-browsing-files"></a><span data-ttu-id="7b637-137">ファイルの保存と参照</span><span class="sxs-lookup"><span data-stu-id="7b637-137">Saving and browsing files</span></span>

<span data-ttu-id="7b637-138">ユーザーがアクセスできるのは、次に示す Surface Hub の一部のディレクトリのみです。</span><span class="sxs-lookup"><span data-stu-id="7b637-138">Users have access to a limited set of directories on the Surface Hub:</span></span>
- <span data-ttu-id="7b637-139">ミュージック</span><span class="sxs-lookup"><span data-stu-id="7b637-139">Music</span></span>
- <span data-ttu-id="7b637-140">ビデオ</span><span class="sxs-lookup"><span data-stu-id="7b637-140">Videos</span></span>
- <span data-ttu-id="7b637-141">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="7b637-141">Documents</span></span>
- <span data-ttu-id="7b637-142">ピクチャ</span><span class="sxs-lookup"><span data-stu-id="7b637-142">Pictures</span></span>
- <span data-ttu-id="7b637-143">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="7b637-143">Downloads</span></span>

<span data-ttu-id="7b637-144">これらのディレクトリにローカルに保存されたファイルは、ユーザーが **[セッションの終了]** を押すと削除されます。</span><span class="sxs-lookup"><span data-stu-id="7b637-144">Files saved locally in these directories are deleted when users press **End session**.</span></span> <span data-ttu-id="7b637-145">会議中に作成したコンテンツを保存するには、USB ドライブや OneDrive にファイルを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b637-145">To save content created during a meeting, users should save files to a USB drive or to OneDrive.</span></span>

*<span data-ttu-id="7b637-146">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-146">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-147">アクセス許可およびファイルとフォルダーの所有権に関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-147">Policies related to access permissions and ownership of files and folders don't apply for Surface Hub.</span></span> <span data-ttu-id="7b637-148">ユーザーは、システム ディレクトリやネットワーク フォルダーを参照したり、そこにファイルを保存したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7b637-148">Users can't browse and save files to system directories and network folders.</span></span>

## <a name="applications"></a><span data-ttu-id="7b637-149">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7b637-149">Applications</span></span>

### <a name="default-applications"></a><span data-ttu-id="7b637-150">既定のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="7b637-150">Default applications</span></span>

<span data-ttu-id="7b637-151">ほとんど例外なく、Surface Hub の既定の ユニバーサル Windows プラットフォーム (UWP) アプリは、Windows 10 PC でも利用可能です。</span><span class="sxs-lookup"><span data-stu-id="7b637-151">With few exceptions, the default Universal Windows Platform (UWP) apps on Surface Hub are also available on Windows 10 PCs.</span></span>

<span data-ttu-id="7b637-152">Surface Hub にプレインストールされている UWP アプリ:</span><span class="sxs-lookup"><span data-stu-id="7b637-152">UWP apps pre-installed on Surface Hub:</span></span>

- <span data-ttu-id="7b637-153">アラーム & クロック</span><span class="sxs-lookup"><span data-stu-id="7b637-153">Alarms & Clock</span></span>
- <span data-ttu-id="7b637-154">電卓</span><span class="sxs-lookup"><span data-stu-id="7b637-154">Calculator</span></span>
- <span data-ttu-id="7b637-155">接続</span><span class="sxs-lookup"><span data-stu-id="7b637-155">Connect</span></span>
- <span data-ttu-id="7b637-156">Excel Mobile</span><span class="sxs-lookup"><span data-stu-id="7b637-156">Excel Mobile</span></span>
- <span data-ttu-id="7b637-157">フィードバック Hub</span><span class="sxs-lookup"><span data-stu-id="7b637-157">Feedback Hub</span></span>
- <span data-ttu-id="7b637-158">エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="7b637-158">File Explorer</span></span>
- <span data-ttu-id="7b637-159">はじめに</span><span class="sxs-lookup"><span data-stu-id="7b637-159">Get Started</span></span>
- <span data-ttu-id="7b637-160">マップ</span><span class="sxs-lookup"><span data-stu-id="7b637-160">Maps</span></span>
- <span data-ttu-id="7b637-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7b637-161">Microsoft Edge</span></span>
- <span data-ttu-id="7b637-162">Microsoft Power BI</span><span class="sxs-lookup"><span data-stu-id="7b637-162">Microsoft Power BI</span></span>
- <span data-ttu-id="7b637-163">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7b637-163">Microsoft Teams</span></span>
- <span data-ttu-id="7b637-164">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="7b637-164">Microsoft Whiteboard</span></span>
- <span data-ttu-id="7b637-165">OneDrive</span><span class="sxs-lookup"><span data-stu-id="7b637-165">OneDrive</span></span>
- <span data-ttu-id="7b637-166">フォト</span><span class="sxs-lookup"><span data-stu-id="7b637-166">Photos</span></span>
- <span data-ttu-id="7b637-167">PowerPoint Mobile</span><span class="sxs-lookup"><span data-stu-id="7b637-167">PowerPoint Mobile</span></span>
- <span data-ttu-id="7b637-168">設定</span><span class="sxs-lookup"><span data-stu-id="7b637-168">Settings</span></span>
- <span data-ttu-id="7b637-169">ストア</span><span class="sxs-lookup"><span data-stu-id="7b637-169">Store</span></span>
- <span data-ttu-id="7b637-170">ヒント</span><span class="sxs-lookup"><span data-stu-id="7b637-170">Tips</span></span>
- <span data-ttu-id="7b637-171">Word Mobile</span><span class="sxs-lookup"><span data-stu-id="7b637-171">Word Mobile</span></span>

*<span data-ttu-id="7b637-172">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-172">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-173">Windows 10 Enterprise のガイドラインを使用して、Surface Hub の既定のアプリの機能およびネットワーク要件を判断します。</span><span class="sxs-lookup"><span data-stu-id="7b637-173">Use guidelines for Windows 10 Enterprise to determine the features and network requirements for default apps on the Surface Hub.</span></span>

### <a name="installing-apps-drivers-and-services"></a><span data-ttu-id="7b637-174">アプリ、ドライバー、およびサービスのインストール</span><span class="sxs-lookup"><span data-stu-id="7b637-174">Installing apps, drivers, and services</span></span>

<span data-ttu-id="7b637-175">アプライアンスのようなデバイス特性を維持するために、Surface Hub でサポートされているのはユニバーサル Windows プラットフォーム (UWP) アプリのインストールのみで、従来の Win32 アプリ、サービス、およびドライバーのインストールはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-175">To help preserve the appliance-like nature of the device, Surface Hub only supports installing Universal Windows Platform (UWP) apps, and does not support installing classic Win32 apps, services and drivers.</span></span> <span data-ttu-id="7b637-176">さらに、UWP アプリをインストールするためのアクセス権を持つのは管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="7b637-176">Furthermore, only admins have access to install UWP apps.</span></span>

*<span data-ttu-id="7b637-177">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-177">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-178">従業員は管理者がインストールしたアプリを使用することしかできないため、意図しない使用の軽減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7b637-178">Employees can only use the apps that have been installed by admins, helping mitigate against unintended use.</span></span> <span data-ttu-id="7b637-179">Surface Hub では、従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-179">Surface Hub doesn't support installing Win32 agents required by most traditional PC management and monitoring tools.</span></span>

## <a name="security-and-lockdown"></a><span data-ttu-id="7b637-180">セキュリティとロックダウン</span><span class="sxs-lookup"><span data-stu-id="7b637-180">Security and lockdown</span></span>

<span data-ttu-id="7b637-181">会議室などの共同スペースで使用するため、Surface Hub のカスタム OS には、Windows 10 で利用可能なセキュリティ機能とロックダウン機能の多くが実装されています。</span><span class="sxs-lookup"><span data-stu-id="7b637-181">For Surface Hub to be used in communal spaces, such as meeting rooms, its custom OS implements many of the security and lockdown features available in Windows 10.</span></span>

<span data-ttu-id="7b637-182">Surface Hub に実装されている Windows 10 のセキュリティ機能:</span><span class="sxs-lookup"><span data-stu-id="7b637-182">Surface Hub implements these Windows 10 security features:</span></span>
- [<span data-ttu-id="7b637-183">UEFI セキュア ブート</span><span class="sxs-lookup"><span data-stu-id="7b637-183">UEFI Secure Boot</span></span>](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)
- [<span data-ttu-id="7b637-184">Windows Defender アプリケーション制御とコード整合性の仮想化ベースの保護</span><span class="sxs-lookup"><span data-stu-id="7b637-184">Windows Defender Application Control and virtualization-based protection of code integrity</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [<span data-ttu-id="7b637-185">AppLocker を使用したアプリケーション制限ポリシー</span><span class="sxs-lookup"><span data-stu-id="7b637-185">Application restriction policies using AppLocker</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/applocker-overview)
- [<span data-ttu-id="7b637-186">BitLocker ドライブ暗号化</span><span class="sxs-lookup"><span data-stu-id="7b637-186">BitLocker Drive Encryption</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview)
- [<span data-ttu-id="7b637-187">トラステッド プラットフォーム モジュール (TPM)</span><span class="sxs-lookup"><span data-stu-id="7b637-187">Trusted Platform Module (TPM)</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/trusted-platform-module-overview)
- [<span data-ttu-id="7b637-188">Microsoft Defender</span><span class="sxs-lookup"><span data-stu-id="7b637-188">Microsoft Defender</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-in-windows-10)
- <span data-ttu-id="7b637-189">設定アプリにアクセスするための[ユーザー アカウント制御 (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview)</span><span class="sxs-lookup"><span data-stu-id="7b637-189">[User Account Control (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview) for access to the Settings app</span></span>

<span data-ttu-id="7b637-190">これらの Surface Hub 機能によって提供される追加のセキュリティ:</span><span class="sxs-lookup"><span data-stu-id="7b637-190">These Surface Hub features provide additional security:</span></span>
- <span data-ttu-id="7b637-191">カスタムの UEFI ファームウェア</span><span class="sxs-lookup"><span data-stu-id="7b637-191">Custom UEFI firmware</span></span>
- <span data-ttu-id="7b637-192">デバイスを会議機能だけに制限するカスタムのシェルとスタート メニュー</span><span class="sxs-lookup"><span data-stu-id="7b637-192">Custom shell and Start menu limits device to meeting functions</span></span>
- <span data-ttu-id="7b637-193">マイ ドキュメントに含まれるファイルとフォルダーへのアクセスのみを許可するカスタムのエクスプローラー</span><span class="sxs-lookup"><span data-stu-id="7b637-193">Custom File Explorer only grants access to files and folders under My Documents</span></span>
- <span data-ttu-id="7b637-194">デバイス設定の変更を管理者にのみ許可するカスタムの設定アプリ</span><span class="sxs-lookup"><span data-stu-id="7b637-194">Custom Settings app only allows admins to modify device settings</span></span>
- <span data-ttu-id="7b637-195">高度なプラグ アンド プレイ ドライバーのダウンロードの無効化</span><span class="sxs-lookup"><span data-stu-id="7b637-195">Downloading advanced Plug and Play drivers is disabled</span></span>

*<span data-ttu-id="7b637-196">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-196">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-197">Surface Hub のセキュリティの評価を行うときは、これらの機能を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7b637-197">Consider these features when performing your security assessment for Surface Hub.</span></span>

<span data-ttu-id="7b637-198">詳細については [、「Surface Hub セキュリティの概要」を参照してください。](surface-hub-security.md)</span><span class="sxs-lookup"><span data-stu-id="7b637-198">To learn more, see [Surface Hub Security Overview](surface-hub-security.md)</span></span>

## <a name="management"></a><span data-ttu-id="7b637-199">管理</span><span class="sxs-lookup"><span data-stu-id="7b637-199">Management</span></span>

### <a name="device-settings"></a><span data-ttu-id="7b637-200">デバイス設定</span><span class="sxs-lookup"><span data-stu-id="7b637-200">Device settings</span></span>

<span data-ttu-id="7b637-201">デバイス設定は、設定アプリで構成できます。</span><span class="sxs-lookup"><span data-stu-id="7b637-201">Device settings can be configured through the Settings app.</span></span> <span data-ttu-id="7b637-202">設定アプリは Surface Hub 用にカスタマイズされていますが、Windows 10 デスクトップで使い慣れた設定も多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b637-202">The Settings app is customized for Surface Hub, but also contains many familiar settings from Windows 10 Desktop.</span></span> <span data-ttu-id="7b637-203">設定アプリを開くと、管理者の資格情報を検証するためにユーザー アカウント制御 (UAC) のプロンプトが表示されますが、管理者としてサインインすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7b637-203">A User Accounts Control (UAC) prompt appears when opening up the Settings app to verify the admin's credentials, but this does not sign in the admin.</span></span>

*<span data-ttu-id="7b637-204">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-204">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-205">従業員は会議で Surface Hub を使用できますが、デバイスの設定を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="7b637-205">Employees can use the Surface Hub for meetings, but cannot modify any device settings.</span></span> <span data-ttu-id="7b637-206">ロックダウン機能と UAC により、従業員は会議機能の使用しかできません。</span><span class="sxs-lookup"><span data-stu-id="7b637-206">In addition to lockdown features, this ensures that employees only use the device for meeting functions.</span></span>

### <a name="administrative-features"></a><span data-ttu-id="7b637-207">管理機能</span><span class="sxs-lookup"><span data-stu-id="7b637-207">Administrative features</span></span>

<span data-ttu-id="7b637-208">Microsoft 管理コンソール、ファイル名を指定して実行、コマンド プロンプト、PowerShell、レジストリ エディター、イベント ビューアー、タスク マネージャーといった Windows 10 Enterprise の管理機能は、Surface Hub ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-208">The administrative features in Windows 10 Enterprise, such as the Microsoft Management Console, Run, Command Prompt, PowerShell, registry editor, event viewer, and task manager are not supported on Surface Hub.</span></span> <span data-ttu-id="7b637-209">設定アプリに、Surface Hub のローカルで利用可能な管理機能がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b637-209">The Settings app contains all of the administrative features locally available on Surface Hub.</span></span>

### <a name="remote-management-and-monitoring"></a><span data-ttu-id="7b637-210">リモート管理および監視</span><span class="sxs-lookup"><span data-stu-id="7b637-210">Remote management and monitoring</span></span>

<span data-ttu-id="7b637-211">Surface Hub は [、Microsoft Intune](https://docs.microsoft.com/intune/) などのモバイル デバイス管理 (MDM) ソリューションや Azure Monitor による監視を通じてリモート管理 [をサポートします](https://azure.microsoft.com/services/monitor/)。</span><span class="sxs-lookup"><span data-stu-id="7b637-211">Surface Hub supports remote management through mobile device management (MDM) solutions such as [Microsoft Intune](https://docs.microsoft.com/intune/) and monitoring through [Azure Monitor](https://azure.microsoft.com/services/monitor/).</span></span> 

*<span data-ttu-id="7b637-212">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-212">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-213">Surface Hub では、System Center Operations Manager といった従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-213">Surface Hub doesn't support installing Win32 agents required by most traditional PC management and monitoring tools, such as System Center Operations Manager.</span></span>

### <a name="group-policy"></a><span data-ttu-id="7b637-214">グループ ポリシー</span><span class="sxs-lookup"><span data-stu-id="7b637-214">Group Policy</span></span>

<span data-ttu-id="7b637-215">Surface Hub では、監査を含む Windows グループ ポリシーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-215">Surface Hub does not support Windows Group Policy, including auditing.</span></span> <span data-ttu-id="7b637-216">代わりに、MDM を使用して Surface Hub にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7b637-216">Instead, use MDM to apply policies to your Surface Hub.</span></span> <span data-ttu-id="7b637-217">MDM について詳しくは、「[MDM プロバイダーによる設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7b637-217">For more information about MDM, see [Manage settings with an MDM provider](manage-settings-with-mdm-for-surface-hub.md).</span></span>

*<span data-ttu-id="7b637-218">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-218">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-219">グループ ポリシーではなく MDM を使用して Surface Hub を管理します。</span><span class="sxs-lookup"><span data-stu-id="7b637-219">Use MDM to manage Surface Hub rather than group policy.</span></span>

### <a name="remote-assistance"></a><span data-ttu-id="7b637-220">リモート アシスタンス</span><span class="sxs-lookup"><span data-stu-id="7b637-220">Remote assistance</span></span>

<span data-ttu-id="7b637-221">Surface Hub では、リモート アシスタンスがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-221">Surface Hub does not support remote assistance.</span></span>

*<span data-ttu-id="7b637-222">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-222">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-223">リモート アシスタンスに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-223">Policies related to remote assistance don't apply for Surface Hub.</span></span>

## <a name="network"></a><span data-ttu-id="7b637-224">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="7b637-224">Network</span></span>

### <a name="domain-join-and-azure-active-directory-azure-ad-join"></a><span data-ttu-id="7b637-225">ドメイン参加と Azure Active Directory (Azure AD) 参加</span><span class="sxs-lookup"><span data-stu-id="7b637-225">Domain join and Azure Active Directory (Azure AD) join</span></span> 

<span data-ttu-id="7b637-226">Surface Hub は主にドメイン参加と Azure AD 参加を使用して、ディレクトリでサポートされる管理者グループを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b637-226">Surface Hub uses domain join and Azure AD join primarily to provide a directory-backed admin group.</span></span> <span data-ttu-id="7b637-227">ユーザーは、ドメイン アカウントではサインインできません。</span><span class="sxs-lookup"><span data-stu-id="7b637-227">Users can't sign in with a domain account.</span></span> <span data-ttu-id="7b637-228">詳しくは、「[管理者グループの管理](admin-group-management-for-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7b637-228">For more information, see [Admin group management](admin-group-management-for-surface-hub.md).</span></span>

*<span data-ttu-id="7b637-229">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-229">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-230">Surface Hub がドメインに参加している場合、グループ ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-230">Group policies are not applied when a Surface Hub is joined to your domain.</span></span> <span data-ttu-id="7b637-231">ドメイン メンバーシップに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-231">Policies related to domain membership don't apply for Surface Hub.</span></span>

### <a name="accessing-domain-resources"></a><span data-ttu-id="7b637-232">ドメインのリソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="7b637-232">Accessing domain resources</span></span>

<span data-ttu-id="7b637-233">ユーザーは、Microsoft Edge にサインインしてイントラネット サイトと (Office 365 などの) オンライン リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7b637-233">Users can sign in to Microsoft Edge to access intranet sites and online resources (such as Office 365).</span></span> <span data-ttu-id="7b637-234">Surface Hub がデバイス アカウントで構成されている場合は、システムはそのアカウントを使用して Exchange と Skype for Business にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7b637-234">If your Surface Hub is configured with a device account, the system uses it to access Exchange and Skype for Business.</span></span> <span data-ttu-id="7b637-235">ただし、Surface Hub では、ファイル共有やプリンターといったドメインのリソースへのアクセスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7b637-235">However, Surface Hub doesn't support accessing domain resources such as file shares and printers.</span></span>

*<span data-ttu-id="7b637-236">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-236">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-237">ドメイン オブジェクトへのアクセスに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b637-237">Policies related to accessing domain objects don't apply for Surface Hub.</span></span>

<!--
### Endpoints



*Organization policies that this may affect:* <br> 
-->

### <a name="diagnostic-data"></a><span data-ttu-id="7b637-238">診断データ</span><span class="sxs-lookup"><span data-stu-id="7b637-238">Diagnostic data</span></span>

<span data-ttu-id="7b637-239">Surface Hub の OS は、Windows 10 の接続ユーザー エクスペリエンスとテレメトリのコンポーネントを使用して診断データを収集して送信します。</span><span class="sxs-lookup"><span data-stu-id="7b637-239">The Surface Hub OS uses the Windows 10 Connected User Experience and Telemetry component to gather and transmit diagnostic data.</span></span> <span data-ttu-id="7b637-240">詳細については、「[組織内の Windows 診断データの構成](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b637-240">For more information, see [Configure Windows diagnostic data in your organization](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization).</span></span>

*<span data-ttu-id="7b637-241">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="7b637-241">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="7b637-242">Windows 10 Enterprise の場合と同じ方法で、Surface Hub の診断データのレベルを構成します。</span><span class="sxs-lookup"><span data-stu-id="7b637-242">Configure diagnostic data levels for Surface Hub in the same way as you do for Windows 10 Enterprise.</span></span>
