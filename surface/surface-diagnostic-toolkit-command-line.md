---
title: コマンドを使用してビジネス向け Surface 診断ツールキットを実行する
description: コマンドコンソールで Surface 診断ツールキットを実行する方法
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 6a56e1231ff5d2f672305d7166bbfa46d1bc0354
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834294"
---
# <span data-ttu-id="35264-103">コマンドを使用してビジネス向け Surface 診断ツールキットを実行する</span><span class="sxs-lookup"><span data-stu-id="35264-103">Run Surface Diagnostic Toolkit for Business using commands</span></span>

<span data-ttu-id="35264-104">コマンドプロンプトで Surface 診断ツールキット (SDT) を実行するには、STD アプリ本体をダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35264-104">Running the Surface Diagnostic Toolkit (SDT) at a command prompt requires downloading the STD app console.</span></span> <span data-ttu-id="35264-105">インストール後、コマンドプロンプトで、Windows コマンドコンソール (cmd.exe) 経由で、または Windows PowerShell を使用して、コマンド、コピー/貼り付け、その他の機能のオートコンプリートのサポートを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="35264-105">After it's installed, you can run SDT at a command prompt via the Windows command console (cmd.exe) or using Windows PowerShell, including PowerShell Integrated Scripting Environment (ISE), which provides support for autocompletion of commands, copy/paste, and other features.</span></span>  <span data-ttu-id="35264-106">SDT でサポートされている Surface デバイスの一覧については、「[展開 Surface 診断ツールキット](surface-diagnostic-toolkit-business.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35264-106">For a list of supported Surface devices in SDT, refer to [Deploy Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-business.md).</span></span>

>[!NOTE]
><span data-ttu-id="35264-107">コマンドを使用して SDT を実行するには、管理者アカウントにサインインしているか、Surface デバイスの管理者グループのメンバーであるアカウントにサインインしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="35264-107">To run SDT using commands, you must be signed in to the Administrator account or signed in to an account that is a member of the Administrator group on your Surface device.</span></span>

## <span data-ttu-id="35264-108">SDT アプリ本体の実行</span><span class="sxs-lookup"><span data-stu-id="35264-108">Running SDT app console</span></span>

<span data-ttu-id="35264-109">[ [Surface Tools FOR IT] ダウンロードページ](https://www.microsoft.com/download/details.aspx?id=46703)から、SDT アプリ本体をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="35264-109">Download and install SDT app console from the [Surface Tools for IT download page](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> <span data-ttu-id="35264-110">Windows コマンドプロンプト (cmd.exe) または Windows PowerShell を使用して、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35264-110">You can use the Windows command prompt (cmd.exe) or Windows PowerShell to:</span></span> 

- <span data-ttu-id="35264-111">すべてのログファイルを収集します。</span><span class="sxs-lookup"><span data-stu-id="35264-111">Collect all log files.</span></span>
- <span data-ttu-id="35264-112">ベストプラクティスアナライザーを使用して正常性診断を実行します。</span><span class="sxs-lookup"><span data-stu-id="35264-112">Run health diagnostics using Best Practice Analyzer.</span></span>
- <span data-ttu-id="35264-113">更新プログラムが見つからないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-113">Check update for missing firmware or driver updates.</span></span>

>[!NOTE]
><span data-ttu-id="35264-114">このリリースでは、SDT アプリ本体は単一のコマンドのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="35264-114">In this release, the SDT app console supports single commands only.</span></span> <span data-ttu-id="35264-115">複数のコマンドラインオプションを実行するには、コマンドごとにコンソール exe を個別に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35264-115">Running multiple command line options requires running the console exe separately for each command.</span></span> 

<span data-ttu-id="35264-116">既定では、出力ファイルは本体のアプリと同じ場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="35264-116">By default, output files are saved in the same location as the console app.</span></span> <span data-ttu-id="35264-117">コマンドの完全な一覧については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35264-117">Refer to the following table for a complete list of commands.</span></span>

<span data-ttu-id="35264-118">コマンド</span><span class="sxs-lookup"><span data-stu-id="35264-118">Command</span></span> | <span data-ttu-id="35264-119">備考</span><span class="sxs-lookup"><span data-stu-id="35264-119">Notes</span></span>
--- | ---
<span data-ttu-id="35264-120">-DataCollector "出力ファイル"</span><span class="sxs-lookup"><span data-stu-id="35264-120">-DataCollector "output file"</span></span> | <span data-ttu-id="35264-121">システムの詳細を zip ファイルに収集します。</span><span class="sxs-lookup"><span data-stu-id="35264-121">Collects system details into a zip file.</span></span> <span data-ttu-id="35264-122">"出力ファイル" は、システムの詳細 zip ファイルを作成するためのファイルパスです。</span><span class="sxs-lookup"><span data-stu-id="35264-122">"output file" is the file path to create system details zip file.</span></span><br><br><span data-ttu-id="35264-123">**例**:</span><span class="sxs-lookup"><span data-stu-id="35264-123">**Example**:</span></span><br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
<span data-ttu-id="35264-124">-bpa "出力ファイル"</span><span class="sxs-lookup"><span data-stu-id="35264-124">-bpa "output file"</span></span> | <span data-ttu-id="35264-125">デバイスの複数の設定と状態インジケーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-125">Checks several settings and health indicators in the device.</span></span> <span data-ttu-id="35264-126">"出力ファイル" は、HTML レポートを作成するためのファイルパスです。</span><span class="sxs-lookup"><span data-stu-id="35264-126">“output file" is the file path to create the HTML report.</span></span><br><br><span data-ttu-id="35264-127">**例**:</span><span class="sxs-lookup"><span data-stu-id="35264-127">**Example**:</span></span><br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
<span data-ttu-id="35264-128">-windows 版</span><span class="sxs-lookup"><span data-stu-id="35264-128">-windowsupdate</span></span> | <span data-ttu-id="35264-129">Windows Update online サーバーでファームウェアやドライバーの更新プログラムが見つからないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-129">Checks Windows Update online servers for missing firmware and/or driver updates.</span></span><br><br><span data-ttu-id="35264-130">**例**:</span><span class="sxs-lookup"><span data-stu-id="35264-130">**Example**:</span></span><br><span data-ttu-id="35264-131">Microsoft.Surface.Diagnostics.App.Console.exe windows 版</span><span class="sxs-lookup"><span data-stu-id="35264-131">Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate</span></span>
<span data-ttu-id="35264-132">保証 "出力ファイル"</span><span class="sxs-lookup"><span data-stu-id="35264-132">-warranty "output file"</span></span> | <span data-ttu-id="35264-133">デバイスの保証情報を確認します (有効または無効)。</span><span class="sxs-lookup"><span data-stu-id="35264-133">Checks warranty information on the device (valid or invalid).</span></span> <span data-ttu-id="35264-134">省略可能な "output file" は、xml ファイルを作成するためのファイルパスです。</span><span class="sxs-lookup"><span data-stu-id="35264-134">The optional “output file” is the file path to create the xml file.</span></span> <br><br><span data-ttu-id="35264-135">**例**:</span><span class="sxs-lookup"><span data-stu-id="35264-135">**Example**:</span></span> <br><span data-ttu-id="35264-136">Microsoft.Surface.Diagnostics.App.Console.exe –保証 "warranty.xml"</span><span class="sxs-lookup"><span data-stu-id="35264-136">Microsoft.Surface.Diagnostics.App.Console.exe –warranty “warranty.xml”</span></span>


>[!NOTE]
><span data-ttu-id="35264-137">ターゲットデバイスで SDT アプリコンソールをリモートで実行するには、Microsoft Endpoint Configuration Manager などの構成管理ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35264-137">To run the SDT app console remotely on target devices, you can use a configuration management tool such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="35264-138">または、コンソールアプリと適切な本体のコマンドを含む .zip ファイルを作成し、組織のソフトウェア配布プロセスごとに展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="35264-138">Alternatively, you can create a .zip file containing the console app and appropriate console commands and deploy per your organization’s software distribution processes.</span></span> 

## <span data-ttu-id="35264-139">ベストプラクティスアナライザーを実行する</span><span class="sxs-lookup"><span data-stu-id="35264-139">Running Best Practice Analyzer</span></span> 

<span data-ttu-id="35264-140">BPA テストは、BitLocker、セキュアブート、トラステッドプラットフォームモジュール (TPM) などの主要コンポーネント全体で実行でき、結果は共有可能なファイルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="35264-140">You can run BPA tests across key components such as BitLocker, Secure Boot, and Trusted Platform Module (TPM) and then output the results to a shareable file.</span></span> <span data-ttu-id="35264-141">このツールは、色分けされた見出しと条件記述子付きの一連の表を生成し、その問題を解決する方法についてのガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="35264-141">The tool generates a series of tables with color-coded headings and condition descriptors along with guidance about how to approach resolving the issue.</span></span> 

- <span data-ttu-id="35264-142">緑は、コンポーネントが最適な条件 (最適) で実行されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="35264-142">Green indicates the component is running in an optimal condition (optimal).</span></span>
- <span data-ttu-id="35264-143">オレンジは、コンポーネントが最適な状態で実行されていないことを示します (最適な状態ではありません)。</span><span class="sxs-lookup"><span data-stu-id="35264-143">Orange indicates the component is not running in an optimal condition (not optimal).</span></span>
- <span data-ttu-id="35264-144">赤は、コンポーネントが異常な状態であることを示します。</span><span class="sxs-lookup"><span data-stu-id="35264-144">Red indicates the component is in an abnormal state.</span></span> 

### <span data-ttu-id="35264-145">BPA 結果の出力の例</span><span class="sxs-lookup"><span data-stu-id="35264-145">Sample BPA results output</span></span>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-146">BitLocker</span><span class="sxs-lookup"><span data-stu-id="35264-146">BitLocker</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-147">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-147">Description:</span></span></strong></td><td><span data-ttu-id="35264-148">システムドライブで BitLocker が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-148">Checks if BitLocker is enabled on the system drive.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-149">値</span><span class="sxs-lookup"><span data-stu-id="35264-149">Value:</span></span></strong></td><td><span data-ttu-id="35264-150">保護</span><span class="sxs-lookup"><span data-stu-id="35264-150">Protection On</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-151">条件</span><span class="sxs-lookup"><span data-stu-id="35264-151">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-152">しも</span><span class="sxs-lookup"><span data-stu-id="35264-152">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-153">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-153">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-154">データを保護するために BitLocker を有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35264-154">It is highly recommended to enable BitLocker to protect your data.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-155">セキュア ブート</span><span class="sxs-lookup"><span data-stu-id="35264-155">Secure Boot</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-156">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-156">Description:</span></span></strong></td><td><span data-ttu-id="35264-157">セキュアブートが有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-157">Checks if Secure Boot is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-158">値</span><span class="sxs-lookup"><span data-stu-id="35264-158">Value:</span></span></strong></td><td><span data-ttu-id="35264-159">True</span><span class="sxs-lookup"><span data-stu-id="35264-159">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-160">条件</span><span class="sxs-lookup"><span data-stu-id="35264-160">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-161">しも</span><span class="sxs-lookup"><span data-stu-id="35264-161">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-162">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-162">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-163">PC を保護するには、セキュアブートを有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35264-163">It is highly recommended to enable Secure Boot to protect your PC.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-164">トラステッド プラットフォーム モジュール</span><span class="sxs-lookup"><span data-stu-id="35264-164">Trusted Platform Module</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-165">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-165">Description:</span></span></strong></td><td><span data-ttu-id="35264-166">TPM が機能していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-166">Ensures that the TPM is functional.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-167">値</span><span class="sxs-lookup"><span data-stu-id="35264-167">Value:</span></span></strong></td><td><span data-ttu-id="35264-168">True</span><span class="sxs-lookup"><span data-stu-id="35264-168">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-169">条件</span><span class="sxs-lookup"><span data-stu-id="35264-169">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-170">しも</span><span class="sxs-lookup"><span data-stu-id="35264-170">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-171">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-171">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-172">機能している TPM がない場合、BitLocker などのセキュリティベースの機能が正しく動作しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="35264-172">Without a functional TPM, security-based functions such as BitLocker may not work properly.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-173">コネクトスタンバイ</span><span class="sxs-lookup"><span data-stu-id="35264-173">Connected Standby</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-174">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-174">Description:</span></span></strong></td><td><span data-ttu-id="35264-175">接続されているスタンバイが有効であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-175">Checks if Connected Standby is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-176">値</span><span class="sxs-lookup"><span data-stu-id="35264-176">Value:</span></span></strong></td><td><span data-ttu-id="35264-177">True</span><span class="sxs-lookup"><span data-stu-id="35264-177">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-178">条件</span><span class="sxs-lookup"><span data-stu-id="35264-178">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-179">しも</span><span class="sxs-lookup"><span data-stu-id="35264-179">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-180">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-180">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-181">コネクトスタンバイにより、Surface デバイスは、使用されていないときに更新と通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="35264-181">Connected Standby allows a Surface device to receive updates and notifications while not being used.</span></span> <span data-ttu-id="35264-182">最適なエクスペリエンスを実現するには、接続されたスタンバイを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35264-182">For best experience, Connected Standby should be enabled.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-183">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="35264-183">Bluetooth</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-184">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-184">Description:</span></span></strong></td><td><span data-ttu-id="35264-185">Bluetooth が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-185">Checks if Bluetooth is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-186">値</span><span class="sxs-lookup"><span data-stu-id="35264-186">Value:</span></span></strong></td><td><span data-ttu-id="35264-187">有効</span><span class="sxs-lookup"><span data-stu-id="35264-187">Enabled</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-188">条件</span><span class="sxs-lookup"><span data-stu-id="35264-188">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-189">しも</span><span class="sxs-lookup"><span data-stu-id="35264-189">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-190">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-190">Guidance:</span></span></strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-191">デバッグモード</span><span class="sxs-lookup"><span data-stu-id="35264-191">Debug Mode</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-192">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-192">Description:</span></span></strong></td><td><span data-ttu-id="35264-193">オペレーティングシステムがデバッグモードになっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-193">Checks if the operating system is in Debug mode.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-194">値</span><span class="sxs-lookup"><span data-stu-id="35264-194">Value:</span></span></strong></td><td><span data-ttu-id="35264-195">通常</span><span class="sxs-lookup"><span data-stu-id="35264-195">Normal</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-196">条件</span><span class="sxs-lookup"><span data-stu-id="35264-196">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-197">しも</span><span class="sxs-lookup"><span data-stu-id="35264-197">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-198">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-198">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-199">Debug ブートオプションは、Windows オペレーティングシステムのカーネルデバッグを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="35264-199">The debug boot option enables or disables kernel debugging of the Windows operating system.</span></span> <span data-ttu-id="35264-200">このオプションを有効にすると、システムが不安定になったり、DRM (デジタル著作権管理の emend) での保護されたメディアが再生されなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35264-200">Enabling this option can cause system instability and can prevent DRM (digital rights managemend) protected media from playing.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-201">署名のテスト</span><span class="sxs-lookup"><span data-stu-id="35264-201">Test Signing</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-202">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-202">Description:</span></span></strong></td><td><span data-ttu-id="35264-203">テスト署名が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-203">Checks if Test Signing is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-204">値</span><span class="sxs-lookup"><span data-stu-id="35264-204">Value:</span></span></strong></td><td><span data-ttu-id="35264-205">通常</span><span class="sxs-lookup"><span data-stu-id="35264-205">Normal</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-206">条件</span><span class="sxs-lookup"><span data-stu-id="35264-206">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-207">しも</span><span class="sxs-lookup"><span data-stu-id="35264-207">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-208">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-208">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-209">テスト署名は、プレリリース版のドライバーのテストにのみ使用される Windows のスタートアップ設定です。</span><span class="sxs-lookup"><span data-stu-id="35264-209">Test Signing is a Windows startup setting that should only be used to test pre-release drivers.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-210">アクティブな Power Plan</span><span class="sxs-lookup"><span data-stu-id="35264-210">Active Power Plan</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-211">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-211">Description:</span></span></strong></td><td><span data-ttu-id="35264-212">適切な電源プランがアクティブになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-212">Checks that the correct power plan is active.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-213">値</span><span class="sxs-lookup"><span data-stu-id="35264-213">Value:</span></span></strong></td><td><span data-ttu-id="35264-214">カッコ</span><span class="sxs-lookup"><span data-stu-id="35264-214">Balanced</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-215">条件</span><span class="sxs-lookup"><span data-stu-id="35264-215">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-216">しも</span><span class="sxs-lookup"><span data-stu-id="35264-216">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-217">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-217">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-218">生産性とバッテリー寿命を最大限に活用するには、"バランス" の power plan を使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35264-218">It is highly recommended to use the "Balanced" power plan to maximize productivity and battery life.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500"><span data-ttu-id="35264-219">Windows Update</span><span class="sxs-lookup"><span data-stu-id="35264-219">Windows Update</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-220">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-220">Description:</span></span></strong></td><td><span data-ttu-id="35264-221">デバイスが Windows 更新プログラムによって最新の状態になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-221">Checks if the device is up to date with Windows updates.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-222">値</span><span class="sxs-lookup"><span data-stu-id="35264-222">Value:</span></span></strong></td><td><span data-ttu-id="35264-223">Microsoft Silverlight (KB4023307)、Windows Defender ウイルス対策の定義更新プログラム-KB2267602 (定義 1.279.1433.0)</span><span class="sxs-lookup"><span data-stu-id="35264-223">Microsoft Silverlight (KB4023307), Definition Update for Windows Defender Antivirus - KB2267602 (Definition 1.279.1433.0)</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-224">条件</span><span class="sxs-lookup"><span data-stu-id="35264-224">Condition:</span></span></strong></td><td><font color="ff9500"><span data-ttu-id="35264-225">最適でない</span><span class="sxs-lookup"><span data-stu-id="35264-225">Not Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-226">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-226">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-227">最新の windows に更新すると、最新のファームウェアとドライバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="35264-227">Updating to the latest windows makes sure you are on the latest firmware and drivers.</span></span> <span data-ttu-id="35264-228">デバイスを常に最新の状態に維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35264-228">It is recommended to always keep your device up to date</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-229">ハードドライブの空き領域</span><span class="sxs-lookup"><span data-stu-id="35264-229">Free Hard Drive Space</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-230">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-230">Description:</span></span></strong></td><td><span data-ttu-id="35264-231">ハードドライブの空き領域が少なくなっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-231">Checks for low free hard drive space.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-232">値</span><span class="sxs-lookup"><span data-stu-id="35264-232">Value:</span></span></strong></td><td><span data-ttu-id="35264-233">66%</span><span class="sxs-lookup"><span data-stu-id="35264-233">66%</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-234">条件</span><span class="sxs-lookup"><span data-stu-id="35264-234">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-235">しも</span><span class="sxs-lookup"><span data-stu-id="35264-235">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-236">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-236">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-237">最高のパフォーマンスを得るには、ハードドライブの容量の少なくとも10% が空き容量である必要があります。</span><span class="sxs-lookup"><span data-stu-id="35264-237">For best performance, your hard drive should have at least 10% of its capacity as free space.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-238">機能していないデバイス</span><span class="sxs-lookup"><span data-stu-id="35264-238">Non-Functioning Devices</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-239">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-239">Description:</span></span></strong></td><td><span data-ttu-id="35264-240">デバイスマネージャーで機能していないデバイスの一覧。</span><span class="sxs-lookup"><span data-stu-id="35264-240">List of non-functioning devices in Device Manager.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-241">値</span><span class="sxs-lookup"><span data-stu-id="35264-241">Value:</span></span></strong></td><td></td></tr>
<tr><td><strong><span data-ttu-id="35264-242">条件</span><span class="sxs-lookup"><span data-stu-id="35264-242">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-243">しも</span><span class="sxs-lookup"><span data-stu-id="35264-243">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-244">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-244">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-245">デバイスマネージャーで機能していないデバイスを使用すると、各ハードウェアコンポーネントの電力を節約することなく、一定の表面デバイスで予期しない問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="35264-245">Non-functioning devices in Device Manager may cause unpredictable problems with Surface devices such as, but not limited to, no power savings for the respective hardware component.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="35264-246">外部モニター</span><span class="sxs-lookup"><span data-stu-id="35264-246">External Monitor</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="35264-247">説明:</span><span class="sxs-lookup"><span data-stu-id="35264-247">Description:</span></span></strong></td><td><span data-ttu-id="35264-248">互換性の問題がある可能性がある外付けモニターを確認します。</span><span class="sxs-lookup"><span data-stu-id="35264-248">Checks for an external monitor that may have compatibility issues.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="35264-249">値</span><span class="sxs-lookup"><span data-stu-id="35264-249">Value:</span></span></strong></td><td></td></tr>
<tr><td><strong><span data-ttu-id="35264-250">条件</span><span class="sxs-lookup"><span data-stu-id="35264-250">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="35264-251">しも</span><span class="sxs-lookup"><span data-stu-id="35264-251">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="35264-252">勧め</span><span class="sxs-lookup"><span data-stu-id="35264-252">Guidance:</span></span></strong></td><td><span data-ttu-id="35264-253">Surface デバイスとの互換性については、元の機器の製造元に確認してください。</span><span class="sxs-lookup"><span data-stu-id="35264-253">Check with the original equipment manufacturer for compatibility with your Surface device.</span></span></td></tr>
</table>
