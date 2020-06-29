---
title: オペレーティングシステムの基礎 (Surface Hub)
description: このトピックでは、Windows 10 Team オペレーティングシステムの固有の側面と、Windows 10 Enterprise との違いについて説明します。
keywords: 変更履歴
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 92a634e897d3e0c9163fe092aaf7992f625de991
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835502"
---
# <span data-ttu-id="db730-104">オペレーティングシステムの基礎 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="db730-104">Operating system essentials (Surface Hub)</span></span>

<span data-ttu-id="db730-105">Surface Hub のオペレーティング システムである Windows 10 Team は Windows 10 Enterprise をベースとしていて、エンタープライズ管理、セキュリティ、およびその他の機能の豊富なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="db730-105">The Surface Hub operating system, Windows 10 Team, is based on Windows 10 Enterprise, providing rich support for enterprise management, security, and other features.</span></span> <span data-ttu-id="db730-106">しかし、これらの間には重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="db730-106">However, there are important differences between them.</span></span> <span data-ttu-id="db730-107">Enterprise エディションは、PC 向けに設計されていますが、Windows 10 Team は大画面および会議室での使用向けに新たに設計されています。</span><span class="sxs-lookup"><span data-stu-id="db730-107">While the Enterprise edition is designed for PCs, Windows 10 Team is designed from the ground up for large screens and meeting rooms.</span></span> <span data-ttu-id="db730-108">Surface Hub のセキュリティおよび管理の要件を評価する場合、新しいオペレーティング システムと見なすことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db730-108">When you evaluate security and management requirements for Surface Hub, it's best to consider it as a new operating system.</span></span> <span data-ttu-id="db730-109">この記事は、Surface Hub の Windows 10 Team と Windows 10 Enterprise の主な相違点と、その相違点が組織にどう影響を与えるかを示すことを目的としています。</span><span class="sxs-lookup"><span data-stu-id="db730-109">This article is designed to help highlight the key differences between Windows 10 Team on Surface Hub and Windows 10 Enterprise, and what the differences mean for your organization.</span></span>

## <span data-ttu-id="db730-110">ユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="db730-110">User interface</span></span>

### <span data-ttu-id="db730-111">シェル (OSのユーザー インターフェイス)</span><span class="sxs-lookup"><span data-stu-id="db730-111">Shell (OS user interface)</span></span>

<span data-ttu-id="db730-112">Surface Hub のシェルは、大画面での表示およびタッチ操作向けに、新たに設計されています。</span><span class="sxs-lookup"><span data-stu-id="db730-112">The Surface Hub's shell is designed from the ground up to be large screen and touch optimized.</span></span> <span data-ttu-id="db730-113">Windows 10 Enterprise と同じシェルは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="db730-113">It doesn't use the same shell as Windows 10 Enterprise.</span></span>

*<span data-ttu-id="db730-114">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-114">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-115">Windows 10 Enterprise のシェルのコントロールに関する設定は、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-115">Settings related to controls in the Windows 10 Enterprise shell don't apply for Surface Hub.</span></span>

### <span data-ttu-id="db730-116">ロック画面とスクリーン セーバー</span><span class="sxs-lookup"><span data-stu-id="db730-116">Lock screen and screensaver</span></span>

<span data-ttu-id="db730-117">Surface Hub にはロック画面やスクリーン セーバーがありませんが、ようこそ画面と呼ばれる同様の機能があります。</span><span class="sxs-lookup"><span data-stu-id="db730-117">Surface Hub doesn't have a lock screen or a screen saver, but it has a similar feature called the welcome screen.</span></span> <span data-ttu-id="db730-118">ようこそ画面には、デバイス アカウントのカレンダーでスケジュール設定済みの会議、および Skype for Business、ホワイトボード、接続といった Surface Hub のトップ アプリへの簡易エントリ ポイントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="db730-118">The welcome screen shows scheduled meetings from the device account's calendar, and easy entry points to the Surface Hub's top apps - Skype for Business, Whiteboard, and Connect.</span></span>

*<span data-ttu-id="db730-119">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-119">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-120">ロック画面、画面のタイムアウト、およびスクリーン セーバーの設定は、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-120">Settings for lock screen, screen timeout, and screen saver don't apply for Surface Hub.</span></span>

### <span data-ttu-id="db730-121">ユーザー サインイン</span><span class="sxs-lookup"><span data-stu-id="db730-121">User sign-in</span></span>

<span data-ttu-id="db730-122">Surface Hub は、会議室などの共同スペースで使用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="db730-122">Surface Hub is designed to be used in communal spaces, such as meeting rooms.</span></span> <span data-ttu-id="db730-123">Windows PC とは異なり、ユーザーにサインインが求められることなく、だれでも Surface Hub を使用できます。</span><span class="sxs-lookup"><span data-stu-id="db730-123">Unlike Windows PCs, anyone can walk up and use a Surface Hub without requiring a user to sign in.</span></span> <span data-ttu-id="db730-124">この共有機能を有効にするために、Surface Hub では、Windows 10 Enterprise のような (ユーザーが OS にサインインして、その資格情報が OS 全体で使用される形式の) Windows サインインがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-124">To enable this communal functionality, Surface Hub does not support Windows sign-in the same way that Windows 10 Enterprise does (e.g., signing in a user to the OS and using those credentials throughout the OS).</span></span> <span data-ttu-id="db730-125">代わりに、ローカルで自動サインインの低特権ユーザーが、常に Surface Hub にログインしているという形になります。</span><span class="sxs-lookup"><span data-stu-id="db730-125">Instead, there is always a local, auto signed-in, low-privilege user signed in to the Surface Hub.</span></span> <span data-ttu-id="db730-126">管理ユーザーを含めて、追加ユーザーのサインインはサポートされません (つまり、管理者がサインインしても、OS へのサインインではありません)。</span><span class="sxs-lookup"><span data-stu-id="db730-126">It doesn't support signing in any additional users, including admin users (e.g., when an admin signs in, they are not signed in to the OS).</span></span>

<span data-ttu-id="db730-127">ユーザーは Surface Hub にサインインできますが、OS へのサインインにはなりません。</span><span class="sxs-lookup"><span data-stu-id="db730-127">Users can sign in to a Surface Hub, but they will not be signed in to the OS.</span></span> <span data-ttu-id="db730-128">たとえば、ユーザーがアプリまたは "会議とファイル" にサインインしても、このユーザーは OS ではなくアプリまたはサービスにサインインしているだけです。</span><span class="sxs-lookup"><span data-stu-id="db730-128">For example, when a user signs in to Apps or My Meetings and Files, the users is signed in only to the apps or services, not to the OS.</span></span> <span data-ttu-id="db730-129">結果として、サインインしたユーザーは、自身のクラウド ファイルや、クラウドに保存されている個人的な会議を取得できますが、**[セッションの終了]** が有効になると資格情報が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="db730-129">As a result, the signed-in user is able to retrieve their cloud files and personal meetings stored in the cloud, and these credentials are discarded when **End session** is activated.</span></span>


*<span data-ttu-id="db730-130">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-130">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-131">通常、Surface Hub ではセキュリティ強化のため、ユーザー アクセス制御ではなくロックダウン機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="db730-131">Generally, Surface Hub uses lockdown features rather than user access control to enforce security.</span></span> <span data-ttu-id="db730-132">パスワード要件、対話型ログオン、ユーザー アカウント、およびアクセス制御に関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-132">Policies related to password requirements, interactive logon, user accounts, and access control don't apply for Surface Hub.</span></span>

### <span data-ttu-id="db730-133">ファイルの保存と参照</span><span class="sxs-lookup"><span data-stu-id="db730-133">Saving and browsing files</span></span>

<span data-ttu-id="db730-134">ユーザーがアクセスできるのは、次に示す Surface Hub の一部のディレクトリのみです。</span><span class="sxs-lookup"><span data-stu-id="db730-134">Users have access to a limited set of directories on the Surface Hub:</span></span>
- <span data-ttu-id="db730-135">ミュージック</span><span class="sxs-lookup"><span data-stu-id="db730-135">Music</span></span>
- <span data-ttu-id="db730-136">ビデオ</span><span class="sxs-lookup"><span data-stu-id="db730-136">Videos</span></span>
- <span data-ttu-id="db730-137">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="db730-137">Documents</span></span>
- <span data-ttu-id="db730-138">ピクチャ</span><span class="sxs-lookup"><span data-stu-id="db730-138">Pictures</span></span>
- <span data-ttu-id="db730-139">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="db730-139">Downloads</span></span>

<span data-ttu-id="db730-140">これらのディレクトリにローカルに保存されたファイルは、ユーザーが **[セッションの終了]** を押すと削除されます。</span><span class="sxs-lookup"><span data-stu-id="db730-140">Files saved locally in these directories are deleted when users press **End session**.</span></span> <span data-ttu-id="db730-141">会議中に作成したコンテンツを保存するには、USB ドライブや OneDrive にファイルを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db730-141">To save content created during a meeting, users should save files to a USB drive or to OneDrive.</span></span>

*<span data-ttu-id="db730-142">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-142">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-143">アクセス許可およびファイルとフォルダーの所有権に関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-143">Policies related to access permissions and ownership of files and folders don't apply for Surface Hub.</span></span> <span data-ttu-id="db730-144">ユーザーは、システム ディレクトリやネットワーク フォルダーを参照したり、そこにファイルを保存したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="db730-144">Users can't browse and save files to system directories and network folders.</span></span>

## <span data-ttu-id="db730-145">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="db730-145">Applications</span></span>

### <span data-ttu-id="db730-146">既定のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="db730-146">Default applications</span></span>

<span data-ttu-id="db730-147">ほとんど例外なく、Surface Hub の既定の ユニバーサル Windows プラットフォーム (UWP) アプリは、Windows 10 PC でも利用可能です。</span><span class="sxs-lookup"><span data-stu-id="db730-147">With few exceptions, the default Universal Windows Platform (UWP) apps on Surface Hub are also available on Windows 10 PCs.</span></span>

<span data-ttu-id="db730-148">Surface Hub にプレインストールされている UWP アプリ:</span><span class="sxs-lookup"><span data-stu-id="db730-148">UWP apps pre-installed on Surface Hub:</span></span>
- <span data-ttu-id="db730-149">アラーム & クロック</span><span class="sxs-lookup"><span data-stu-id="db730-149">Alarms & Clock</span></span>
- <span data-ttu-id="db730-150">電卓</span><span class="sxs-lookup"><span data-stu-id="db730-150">Calculator</span></span>
- <span data-ttu-id="db730-151">接続</span><span class="sxs-lookup"><span data-stu-id="db730-151">Connect</span></span>
- <span data-ttu-id="db730-152">Excel Mobile</span><span class="sxs-lookup"><span data-stu-id="db730-152">Excel Mobile</span></span>
- <span data-ttu-id="db730-153">フィードバック Hub</span><span class="sxs-lookup"><span data-stu-id="db730-153">Feedback Hub</span></span>
- <span data-ttu-id="db730-154">エクスプローラー\*</span><span class="sxs-lookup"><span data-stu-id="db730-154">File Explorer\*</span></span>
- <span data-ttu-id="db730-155">はじめに</span><span class="sxs-lookup"><span data-stu-id="db730-155">Get Started</span></span>
- <span data-ttu-id="db730-156">マップ</span><span class="sxs-lookup"><span data-stu-id="db730-156">Maps</span></span>
- <span data-ttu-id="db730-157">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="db730-157">Microsoft Edge</span></span>
- <span data-ttu-id="db730-158">Microsoft Power BI</span><span class="sxs-lookup"><span data-stu-id="db730-158">Microsoft Power BI</span></span>
- <span data-ttu-id="db730-159">OneDrive</span><span class="sxs-lookup"><span data-stu-id="db730-159">OneDrive</span></span>
- <span data-ttu-id="db730-160">フォト</span><span class="sxs-lookup"><span data-stu-id="db730-160">Photos</span></span>
- <span data-ttu-id="db730-161">PowerPoint Mobile</span><span class="sxs-lookup"><span data-stu-id="db730-161">PowerPoint Mobile</span></span>
- <span data-ttu-id="db730-162">設定\*</span><span class="sxs-lookup"><span data-stu-id="db730-162">Settings\*</span></span>
- <span data-ttu-id="db730-163">Skype for Business\*</span><span class="sxs-lookup"><span data-stu-id="db730-163">Skype for Business\*</span></span>
- <span data-ttu-id="db730-164">ストア</span><span class="sxs-lookup"><span data-stu-id="db730-164">Store</span></span>
- <span data-ttu-id="db730-165">ホワイトボード\*</span><span class="sxs-lookup"><span data-stu-id="db730-165">Whiteboard\*</span></span>
- <span data-ttu-id="db730-166">Word Mobile</span><span class="sxs-lookup"><span data-stu-id="db730-166">Word Mobile</span></span>

*<span data-ttu-id="db730-167">アスタリスク (&ast;) が付いているアプリは Surface Hub に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="db730-167">Apps with an asterisk (&ast;) are unique to Surface Hub</span></span>*

*<span data-ttu-id="db730-168">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-168">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-169">Windows 10 Enterprise のガイドラインを使用して、Surface Hub の既定のアプリの機能およびネットワーク要件を判断します。</span><span class="sxs-lookup"><span data-stu-id="db730-169">Use guidelines for Windows 10 Enterprise to determine the features and network requirements for default apps on the Surface Hub.</span></span>

### <span data-ttu-id="db730-170">アプリ、ドライバー、およびサービスのインストール</span><span class="sxs-lookup"><span data-stu-id="db730-170">Installing apps, drivers, and services</span></span>

<span data-ttu-id="db730-171">アプライアンスのようなデバイス特性を維持するために、Surface Hub でサポートされているのはユニバーサル Windows プラットフォーム (UWP) アプリのインストールのみで、従来の Win32 アプリ、サービス、およびドライバーのインストールはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-171">To help preserve the appliance-like nature of the device, Surface Hub only supports installing Universal Windows Platform (UWP) apps, and does not support installing classic Win32 apps, services and drivers.</span></span> <span data-ttu-id="db730-172">さらに、UWP アプリをインストールするためのアクセス権を持つのは管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="db730-172">Furthermore, only admins have access to install UWP apps.</span></span>

*<span data-ttu-id="db730-173">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-173">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-174">従業員は管理者がインストールしたアプリを使用することしかできないため、意図しない使用の軽減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="db730-174">Employees can only use the apps that have been installed by admins, helping mitigate against unintended use.</span></span> <span data-ttu-id="db730-175">Surface Hub では、従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-175">Surface Hub doesn't support installing Win32 agents required by most traditional PC management and monitoring tools.</span></span>

## <span data-ttu-id="db730-176">セキュリティとロックダウン</span><span class="sxs-lookup"><span data-stu-id="db730-176">Security and lockdown</span></span>

<span data-ttu-id="db730-177">会議室などの共同スペースで使用するため、Surface Hub のカスタム OS には、Windows 10 で利用可能なセキュリティ機能とロックダウン機能の多くが実装されています。</span><span class="sxs-lookup"><span data-stu-id="db730-177">For Surface Hub to be used in communal spaces, such as meeting rooms, its custom OS implements many of the security and lockdown features available in Windows 10.</span></span>

<span data-ttu-id="db730-178">Surface Hub に実装されている Windows 10 のセキュリティ機能:</span><span class="sxs-lookup"><span data-stu-id="db730-178">Surface Hub implements these Windows 10 security features:</span></span>
- [<span data-ttu-id="db730-179">UEFI セキュア ブート</span><span class="sxs-lookup"><span data-stu-id="db730-179">UEFI Secure Boot</span></span>](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)
- [<span data-ttu-id="db730-180">Device Guard を使用したユーザー モード コード整合性 (UMCI)</span><span class="sxs-lookup"><span data-stu-id="db730-180">User Mode Code Integrity (UMCI) with Device Guard</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [<span data-ttu-id="db730-181">AppLocker を使用したアプリケーション制限ポリシー</span><span class="sxs-lookup"><span data-stu-id="db730-181">Application restriction policies using AppLocker</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/applocker-overview)
- [<span data-ttu-id="db730-182">BitLocker ドライブ暗号化</span><span class="sxs-lookup"><span data-stu-id="db730-182">BitLocker Drive Encryption</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview)
- [<span data-ttu-id="db730-183">トラステッド プラットフォーム モジュール (TPM)</span><span class="sxs-lookup"><span data-stu-id="db730-183">Trusted Platform Module (TPM)</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/trusted-platform-module-overview)
- [<span data-ttu-id="db730-184">Windows Defender</span><span class="sxs-lookup"><span data-stu-id="db730-184">Windows Defender</span></span>](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-in-windows-10)
- <span data-ttu-id="db730-185">設定アプリにアクセスするための[ユーザー アカウント制御 (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview)</span><span class="sxs-lookup"><span data-stu-id="db730-185">[User Account Control (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview) for access to the Settings app</span></span>

<span data-ttu-id="db730-186">これらの Surface Hub 機能によって提供される追加のセキュリティ:</span><span class="sxs-lookup"><span data-stu-id="db730-186">These Surface Hub features provide additional security:</span></span>
- <span data-ttu-id="db730-187">カスタムの UEFI ファームウェア</span><span class="sxs-lookup"><span data-stu-id="db730-187">Custom UEFI firmware</span></span>
- <span data-ttu-id="db730-188">デバイスを会議機能だけに制限するカスタムのシェルとスタート メニュー</span><span class="sxs-lookup"><span data-stu-id="db730-188">Custom shell and Start menu limits device to meeting functions</span></span>
- <span data-ttu-id="db730-189">マイ ドキュメントに含まれるファイルとフォルダーへのアクセスのみを許可するカスタムのエクスプローラー</span><span class="sxs-lookup"><span data-stu-id="db730-189">Custom File Explorer only grants access to files and folders under My Documents</span></span>
- <span data-ttu-id="db730-190">デバイス設定の変更を管理者にのみ許可するカスタムの設定アプリ</span><span class="sxs-lookup"><span data-stu-id="db730-190">Custom Settings app only allows admins to modify device settings</span></span>
- <span data-ttu-id="db730-191">高度なプラグ アンド プレイ ドライバーのダウンロードの無効化</span><span class="sxs-lookup"><span data-stu-id="db730-191">Downloading advanced Plug and Play drivers is disabled</span></span>

*<span data-ttu-id="db730-192">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-192">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-193">Surface Hub のセキュリティの評価を行うときは、これらの機能を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="db730-193">Consider these features when performing your security assessment for Surface Hub.</span></span>

## <span data-ttu-id="db730-194">管理</span><span class="sxs-lookup"><span data-stu-id="db730-194">Management</span></span>

### <span data-ttu-id="db730-195">デバイス設定</span><span class="sxs-lookup"><span data-stu-id="db730-195">Device settings</span></span>

<span data-ttu-id="db730-196">デバイス設定は、設定アプリで構成できます。</span><span class="sxs-lookup"><span data-stu-id="db730-196">Device settings can be configured through the Settings app.</span></span> <span data-ttu-id="db730-197">設定アプリは Surface Hub 用にカスタマイズされていますが、Windows 10 デスクトップで使い慣れた設定も多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="db730-197">The Settings app is customized for Surface Hub, but also contains many familiar settings from Windows 10 Desktop.</span></span> <span data-ttu-id="db730-198">設定アプリを開くと、管理者の資格情報を検証するためにユーザー アカウント制御 (UAC) のプロンプトが表示されますが、管理者としてサインインすることはできません。</span><span class="sxs-lookup"><span data-stu-id="db730-198">A User Accounts Control (UAC) prompt appears when opening up the Settings app to verify the admin's credentials, but this does not sign in the admin.</span></span>

*<span data-ttu-id="db730-199">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-199">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-200">従業員は会議で Surface Hub を使用できますが、デバイスの設定を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="db730-200">Employees can use the Surface Hub for meetings, but cannot modify any device settings.</span></span> <span data-ttu-id="db730-201">ロックダウン機能と UAC により、従業員は会議機能の使用しかできません。</span><span class="sxs-lookup"><span data-stu-id="db730-201">In addition to lockdown features, this ensures that employees only use the device for meeting functions.</span></span>

### <span data-ttu-id="db730-202">管理機能</span><span class="sxs-lookup"><span data-stu-id="db730-202">Administrative features</span></span>

<span data-ttu-id="db730-203">Microsoft 管理コンソール、ファイル名を指定して実行、コマンド プロンプト、PowerShell、レジストリ エディター、イベント ビューアー、タスク マネージャーといった Windows 10 Enterprise の管理機能は、Surface Hub ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-203">The administrative features in Windows 10 Enterprise, such as the Microsoft Management Console, Run, Command Prompt, PowerShell, registry editor, event viewer, and task manager are not supported on Surface Hub.</span></span> <span data-ttu-id="db730-204">設定アプリに、Surface Hub のローカルで利用可能な管理機能がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="db730-204">The Settings app contains all of the administrative features locally available on Surface Hub.</span></span>

*<span data-ttu-id="db730-205">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-205">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-206">Surface Hub は、従来の PC と同様の方法では管理されません。</span><span class="sxs-lookup"><span data-stu-id="db730-206">Surface Hubs are not managed like traditional PCs.</span></span> <span data-ttu-id="db730-207">設定の構成には MDM を使用し、Surface Hub の監視には OMS を使用します。</span><span class="sxs-lookup"><span data-stu-id="db730-207">Use MDM to configure settings and OMS to monitor your Surface Hub.</span></span>

### <span data-ttu-id="db730-208">リモート管理および監視</span><span class="sxs-lookup"><span data-stu-id="db730-208">Remote management and monitoring</span></span>

<span data-ttu-id="db730-209">Surface Hub は、 [Microsoft Intune](https://docs.microsoft.com/intune/)などのモバイルデバイス管理 (MDM) ソリューションでのリモート管理をサポートしています。また、 [Azure モニター](https://azure.microsoft.com/services/monitor/)での監視もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="db730-209">Surface Hub supports remote management through mobile device management (MDM) solutions such as [Microsoft Intune](https://docs.microsoft.com/intune/) and monitoring through [Azure Monitor](https://azure.microsoft.com/services/monitor/).</span></span> 

*<span data-ttu-id="db730-210">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-210">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-211">Surface Hub では、System Center Operations Manager といった従来の多くの PC 管理および監視ツールで必要とされる Win32 エージェントのインストールがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-211">Surface Hub doesn't support installing Win32 agents required by most traditional PC management and monitoring tools, such as System Center Operations Manager.</span></span>

### <span data-ttu-id="db730-212">グループ ポリシー</span><span class="sxs-lookup"><span data-stu-id="db730-212">Group Policy</span></span>

<span data-ttu-id="db730-213">Surface Hub は、監査を含む Windows グループポリシーをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="db730-213">Surface Hub does not support Windows Group Policy, including auditing.</span></span> <span data-ttu-id="db730-214">代わりに、MDM を使用して Surface Hub にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="db730-214">Instead, use MDM to apply policies to your Surface Hub.</span></span> <span data-ttu-id="db730-215">MDM について詳しくは、「[MDM プロバイダーによる設定の管理](manage-settings-with-mdm-for-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="db730-215">For more information about MDM, see [Manage settings with an MDM provider](manage-settings-with-mdm-for-surface-hub.md).</span></span>

*<span data-ttu-id="db730-216">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-216">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-217">グループ ポリシーではなく MDM を使用して Surface Hub を管理します。</span><span class="sxs-lookup"><span data-stu-id="db730-217">Use MDM to manage Surface Hub rather than group policy.</span></span>

### <span data-ttu-id="db730-218">リモート アシスタンス</span><span class="sxs-lookup"><span data-stu-id="db730-218">Remote assistance</span></span>

<span data-ttu-id="db730-219">Surface Hub では、リモート アシスタンスがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-219">Surface Hub does not support remote assistance.</span></span>

*<span data-ttu-id="db730-220">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-220">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-221">リモート アシスタンスに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-221">Policies related to remote assistance don't apply for Surface Hub.</span></span>

## <span data-ttu-id="db730-222">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="db730-222">Network</span></span>

### <span data-ttu-id="db730-223">ドメイン参加と Azure Active Directory (Azure AD) 参加</span><span class="sxs-lookup"><span data-stu-id="db730-223">Domain join and Azure Active Directory (Azure AD) join</span></span> 

<span data-ttu-id="db730-224">Surface Hub は主にドメイン参加と Azure AD 参加を使用して、ディレクトリでサポートされる管理者グループを提供します。</span><span class="sxs-lookup"><span data-stu-id="db730-224">Surface Hub uses domain join and Azure AD join primarily to provide a directory-backed admin group.</span></span> <span data-ttu-id="db730-225">ユーザーは、ドメイン アカウントではサインインできません。</span><span class="sxs-lookup"><span data-stu-id="db730-225">Users can't sign in with a domain account.</span></span> <span data-ttu-id="db730-226">詳しくは、「[管理者グループの管理](admin-group-management-for-surface-hub.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="db730-226">For more information, see [Admin group management](admin-group-management-for-surface-hub.md).</span></span>

*<span data-ttu-id="db730-227">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-227">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-228">Surface Hub がドメインに参加している場合、グループ ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-228">Group policies are not applied when a Surface Hub is joined to your domain.</span></span> <span data-ttu-id="db730-229">ドメイン メンバーシップに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-229">Policies related to domain membership don't apply for Surface Hub.</span></span>

### <span data-ttu-id="db730-230">ドメインのリソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="db730-230">Accessing domain resources</span></span>

<span data-ttu-id="db730-231">ユーザーは、Microsoft Edge にサインインしてイントラネット サイトと (Office 365 などの) オンライン リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="db730-231">Users can sign in to Microsoft Edge to access intranet sites and online resources (such as Office 365).</span></span> <span data-ttu-id="db730-232">Surface Hub がデバイス アカウントで構成されている場合は、システムはそのアカウントを使用して Exchange と Skype for Business にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="db730-232">If your Surface Hub is configured with a device account, the system uses it to access Exchange and Skype for Business.</span></span> <span data-ttu-id="db730-233">ただし、Surface Hub では、ファイル共有やプリンターといったドメインのリソースへのアクセスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db730-233">However, Surface Hub doesn't support accessing domain resources such as file shares and printers.</span></span>

*<span data-ttu-id="db730-234">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-234">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-235">ドメイン オブジェクトへのアクセスに関するポリシーは、Surface Hub には適用されません。</span><span class="sxs-lookup"><span data-stu-id="db730-235">Policies related to accessing domain objects don't apply for Surface Hub.</span></span>

<!--
### Endpoints



*Organization policies that this may affect:* <br> 
-->

### <span data-ttu-id="db730-236">診断データ</span><span class="sxs-lookup"><span data-stu-id="db730-236">Diagnostic data</span></span>

<span data-ttu-id="db730-237">Surface Hub の OS は、Windows 10 の接続ユーザー エクスペリエンスとテレメトリのコンポーネントを使用して診断データを収集して送信します。</span><span class="sxs-lookup"><span data-stu-id="db730-237">The Surface Hub OS uses the Windows 10 Connected User Experience and Telemetry component to gather and transmit diagnostic data.</span></span> <span data-ttu-id="db730-238">詳細については、「[組織内の Windows 診断データの構成](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db730-238">For more information, see [Configure Windows diagnostic data in your organization](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization).</span></span>

*<span data-ttu-id="db730-239">これにより影響を受ける可能性のある組織ポリシー:</span><span class="sxs-lookup"><span data-stu-id="db730-239">Organization policies that this may affect:</span></span>* <br> <span data-ttu-id="db730-240">Windows 10 Enterprise の場合と同じ方法で、Surface Hub の診断データのレベルを構成します。</span><span class="sxs-lookup"><span data-stu-id="db730-240">Configure diagnostic data levels for Surface Hub in the same way as you do for Windows 10 Enterprise.</span></span>
