---
title: コマンドを使用してビジネス向け Surface 診断ツールキットを実行する
description: コマンド コンソールで Surface Diagnostic Toolkitを実行する方法
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
ms.openlocfilehash: f3856499bd769b96e22c0a47323c984eb38d8a18
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327331"
---
# <span data-ttu-id="c85c4-103">コマンドを使用してビジネス向け Surface 診断ツールキットを実行する</span><span class="sxs-lookup"><span data-stu-id="c85c4-103">Run Surface Diagnostic Toolkit for Business using commands</span></span>

<span data-ttu-id="c85c4-104">コマンド プロンプトで Surface Diagnostic Toolkit (SDT) を実行するには、SDT アプリ コンソールをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-104">Running the Surface Diagnostic Toolkit (SDT) at a command prompt requires downloading the SDT app console.</span></span> <span data-ttu-id="c85c4-105">インストール後、Windows コマンド コンソール (cmd.exe) を介してコマンド プロンプトで、またはコマンドのオートコンプリート、コピー/貼り付け、その他の機能のサポートを提供する PowerShell Integrated Scripting Environment (ISE) を含む Windows PowerShell を使用して SDT を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-105">After it's installed, you can run SDT at a command prompt via the Windows command console (cmd.exe) or using Windows PowerShell, including PowerShell Integrated Scripting Environment (ISE), which provides support for autocompletion of commands, copy/paste, and other features.</span></span>  <span data-ttu-id="c85c4-106">SDT でサポートされている Surface デバイスの一覧については [、「Surface Diagnostic Toolkit for Business の展開」を参照してください](surface-diagnostic-toolkit-business.md)。</span><span class="sxs-lookup"><span data-stu-id="c85c4-106">For a list of supported Surface devices in SDT, refer to [Deploy Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-business.md).</span></span>

>[!NOTE]
><span data-ttu-id="c85c4-107">コマンドを使用して SDT を実行するには、Administrator アカウントにサインインするか、Surface デバイスの Administrator グループのメンバーであるアカウントにサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-107">To run SDT using commands, you must be signed in to the Administrator account or signed in to an account that is a member of the Administrator group on your Surface device.</span></span>

## <span data-ttu-id="c85c4-108">SDT アプリ コンソールの実行</span><span class="sxs-lookup"><span data-stu-id="c85c4-108">Running SDT app console</span></span>

<span data-ttu-id="c85c4-109">Surface Tools for IT ダウンロード ページから SDT アプリ コンソール [をダウンロードしてインストールします](https://www.microsoft.com/download/details.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="c85c4-109">Download and install SDT app console from the [Surface Tools for IT download page](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> <span data-ttu-id="c85c4-110">Windows コマンド プロンプト (cmd.exe) または次のWindows PowerShell使用できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-110">You can use the Windows command prompt (cmd.exe) or Windows PowerShell to:</span></span> 

- <span data-ttu-id="c85c4-111">すべてのログ ファイルを収集します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-111">Collect all log files.</span></span>
- <span data-ttu-id="c85c4-112">ベスト プラクティス アナライザーを使用して正常性診断を実行します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-112">Run health diagnostics using Best Practice Analyzer.</span></span>
- <span data-ttu-id="c85c4-113">ファームウェアまたはドライバーの更新プログラムが見つからないか、更新プログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-113">Check update for missing firmware or driver updates.</span></span>

>[!NOTE]
><span data-ttu-id="c85c4-114">このリリースでは、SDT アプリ コンソールは単一のコマンドのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c85c4-114">In this release, the SDT app console supports single commands only.</span></span> <span data-ttu-id="c85c4-115">複数のコマンド ライン オプションを実行するには、コマンドごとにコンソール exe を個別に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-115">Running multiple command line options requires running the console exe separately for each command.</span></span> 

<span data-ttu-id="c85c4-116">既定では、出力ファイルはコンソール アプリと同じ場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-116">By default, output files are saved in the same location as the console app.</span></span> <span data-ttu-id="c85c4-117">コマンドの完全な一覧については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c85c4-117">Refer to the following table for a complete list of commands.</span></span>

<span data-ttu-id="c85c4-118">コマンド</span><span class="sxs-lookup"><span data-stu-id="c85c4-118">Command</span></span> | <span data-ttu-id="c85c4-119">備考</span><span class="sxs-lookup"><span data-stu-id="c85c4-119">Notes</span></span>
--- | ---
<span data-ttu-id="c85c4-120">-DataCollector "output file"</span><span class="sxs-lookup"><span data-stu-id="c85c4-120">-DataCollector "output file"</span></span> | <span data-ttu-id="c85c4-121">zip ファイルにシステムの詳細を収集します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-121">Collects system details into a zip file.</span></span> <span data-ttu-id="c85c4-122">"出力ファイル" は、システムの詳細 zip ファイルを作成するファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="c85c4-122">"output file" is the file path to create system details zip file.</span></span><br><br><span data-ttu-id="c85c4-123">**例**:</span><span class="sxs-lookup"><span data-stu-id="c85c4-123">**Example**:</span></span><br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
<span data-ttu-id="c85c4-124">-bpa "出力ファイル"</span><span class="sxs-lookup"><span data-stu-id="c85c4-124">-bpa "output file"</span></span> | <span data-ttu-id="c85c4-125">デバイス内のいくつかの設定と正常性インジケーターをチェックします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-125">Checks several settings and health indicators in the device.</span></span> <span data-ttu-id="c85c4-126">"出力ファイル" は、HTML レポートを作成するファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="c85c4-126">“output file" is the file path to create the HTML report.</span></span><br><br><span data-ttu-id="c85c4-127">**例**:</span><span class="sxs-lookup"><span data-stu-id="c85c4-127">**Example**:</span></span><br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
<span data-ttu-id="c85c4-128">-windowsupdate</span><span class="sxs-lookup"><span data-stu-id="c85c4-128">-windowsupdate</span></span> | <span data-ttu-id="c85c4-129">ファームウェアやドライバーの更新プログラムが見つからないか、Windows Update オンライン サーバーをチェックします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-129">Checks Windows Update online servers for missing firmware and/or driver updates.</span></span><br><br><span data-ttu-id="c85c4-130">**例**:</span><span class="sxs-lookup"><span data-stu-id="c85c4-130">**Example**:</span></span><br><span data-ttu-id="c85c4-131">Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate</span><span class="sxs-lookup"><span data-stu-id="c85c4-131">Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate</span></span>
<span data-ttu-id="c85c4-132">-warranty "output file"</span><span class="sxs-lookup"><span data-stu-id="c85c4-132">-warranty "output file"</span></span> | <span data-ttu-id="c85c4-133">デバイスの保証情報を確認します (有効または無効)。</span><span class="sxs-lookup"><span data-stu-id="c85c4-133">Checks warranty information on the device (valid or invalid).</span></span> <span data-ttu-id="c85c4-134">オプションの "出力ファイル" は、xml ファイルを作成するファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="c85c4-134">The optional “output file” is the file path to create the xml file.</span></span> <br><br><span data-ttu-id="c85c4-135">**例**:</span><span class="sxs-lookup"><span data-stu-id="c85c4-135">**Example**:</span></span> <br><span data-ttu-id="c85c4-136">Microsoft.Surface.Diagnostics.App.Console.exe –保証 "warranty.xml"</span><span class="sxs-lookup"><span data-stu-id="c85c4-136">Microsoft.Surface.Diagnostics.App.Console.exe –warranty “warranty.xml”</span></span>


>[!NOTE]
><span data-ttu-id="c85c4-137">SDT アプリ コンソールをターゲット デバイスでリモートで実行するには、Microsoft Endpoint Configuration Manager などの構成管理ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-137">To run the SDT app console remotely on target devices, you can use a configuration management tool such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="c85c4-138">または、コンソール アプリと適切なコンソール コマンドを含む .zip ファイルを作成し、組織のソフトウェア配布プロセスごとに展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-138">Alternatively, you can create a .zip file containing the console app and appropriate console commands and deploy per your organization’s software distribution processes.</span></span> 

## <span data-ttu-id="c85c4-139">ベスト プラクティス アナライザーの実行</span><span class="sxs-lookup"><span data-stu-id="c85c4-139">Running Best Practice Analyzer</span></span> 

<span data-ttu-id="c85c4-140">BitLocker、セキュア ブート、トラステッド プラットフォーム モジュール (TPM) などの主要コンポーネント間で BPA テストを実行し、共有可能なファイルに結果を出力できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-140">You can run BPA tests across key components such as BitLocker, Secure Boot, and Trusted Platform Module (TPM) and then output the results to a shareable file.</span></span> <span data-ttu-id="c85c4-141">このツールは、色分けされた見出しと条件記述子を持つ一連のテーブルと、問題を解決する方法に関するガイダンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-141">The tool generates a series of tables with color-coded headings and condition descriptors along with guidance about how to approach resolving the issue.</span></span> 

- <span data-ttu-id="c85c4-142">緑は、コンポーネントが最適な状態 (最適) で実行されている状態を示します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-142">Green indicates the component is running in an optimal condition (optimal).</span></span>
- <span data-ttu-id="c85c4-143">オレンジ色は、コンポーネントが最適な状態で実行されていない (最適ではない) 状態を示します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-143">Orange indicates the component is not running in an optimal condition (not optimal).</span></span>
- <span data-ttu-id="c85c4-144">赤は、コンポーネントが異常な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-144">Red indicates the component is in an abnormal state.</span></span> 

### <span data-ttu-id="c85c4-145">サンプル BPA 結果の出力</span><span class="sxs-lookup"><span data-stu-id="c85c4-145">Sample BPA results output</span></span>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-146">BitLocker</span><span class="sxs-lookup"><span data-stu-id="c85c4-146">BitLocker</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-147">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-147">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-148">システム ドライブで BitLocker が有効になっているか確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-148">Checks if BitLocker is enabled on the system drive.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-149">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-149">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-150">保護のオン</span><span class="sxs-lookup"><span data-stu-id="c85c4-150">Protection On</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-151">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-151">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-152">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-152">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-153">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-153">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-154">BitLocker を有効にしてデータを保護することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-154">It is highly recommended to enable BitLocker to protect your data.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-155">セキュア ブート</span><span class="sxs-lookup"><span data-stu-id="c85c4-155">Secure Boot</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-156">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-156">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-157">セキュア ブートが有効になっているか確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-157">Checks if Secure Boot is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-158">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-158">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-159">True</span><span class="sxs-lookup"><span data-stu-id="c85c4-159">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-160">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-160">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-161">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-161">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-162">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-162">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-163">PC を保護するためにセキュア ブートを有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-163">It is highly recommended to enable Secure Boot to protect your PC.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-164">トラステッド プラットフォーム モジュール</span><span class="sxs-lookup"><span data-stu-id="c85c4-164">Trusted Platform Module</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-165">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-165">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-166">TPM が機能している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-166">Ensures that the TPM is functional.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-167">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-167">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-168">True</span><span class="sxs-lookup"><span data-stu-id="c85c4-168">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-169">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-169">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-170">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-170">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-171">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-171">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-172">機能する TPM がない場合、BitLocker などのセキュリティ ベースの機能が正しく動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-172">Without a functional TPM, security-based functions such as BitLocker may not work properly.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-173">Connected Standby</span><span class="sxs-lookup"><span data-stu-id="c85c4-173">Connected Standby</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-174">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-174">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-175">接続スタンバイが有効になっているか確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-175">Checks if Connected Standby is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-176">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-176">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-177">True</span><span class="sxs-lookup"><span data-stu-id="c85c4-177">True</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-178">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-178">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-179">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-179">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-180">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-180">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-181">Connected Standby を使用すると、Surface デバイスは、使用されていない間に更新と通知を受信できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-181">Connected Standby allows a Surface device to receive updates and notifications while not being used.</span></span> <span data-ttu-id="c85c4-182">最適なエクスペリエンスを得る場合は、Connected Standby を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-182">For best experience, Connected Standby should be enabled.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-183">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c85c4-183">Bluetooth</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-184">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-184">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-185">有効になっているBluetoothチェックします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-185">Checks if Bluetooth is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-186">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-186">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-187">有効</span><span class="sxs-lookup"><span data-stu-id="c85c4-187">Enabled</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-188">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-188">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-189">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-189">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-190">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-190">Guidance:</span></span></strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-191">デバッグ モード</span><span class="sxs-lookup"><span data-stu-id="c85c4-191">Debug Mode</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-192">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-192">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-193">オペレーティング システムがデバッグ モードにあるか確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-193">Checks if the operating system is in Debug mode.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-194">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-194">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-195">通常</span><span class="sxs-lookup"><span data-stu-id="c85c4-195">Normal</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-196">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-196">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-197">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-197">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-198">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-198">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-199">デバッグ ブート オプションは、Windows オペレーティング システムのカーネル デバッグを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-199">The debug boot option enables or disables kernel debugging of the Windows operating system.</span></span> <span data-ttu-id="c85c4-200">このオプションを有効にすると、システムが不安定化し、DRM (デジタル著作権管理) で保護されたメディアの再生が妨げる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-200">Enabling this option can cause system instability and can prevent DRM (digital rights managemend) protected media from playing.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-201">テスト署名</span><span class="sxs-lookup"><span data-stu-id="c85c4-201">Test Signing</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-202">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-202">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-203">テスト署名が有効になっているか確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-203">Checks if Test Signing is enabled.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-204">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-204">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-205">通常</span><span class="sxs-lookup"><span data-stu-id="c85c4-205">Normal</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-206">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-206">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-207">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-207">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-208">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-208">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-209">テスト署名は、プレリリース版のドライバーのテストにのみ使用する必要がある Windows スタートアップ設定です。</span><span class="sxs-lookup"><span data-stu-id="c85c4-209">Test Signing is a Windows startup setting that should only be used to test pre-release drivers.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-210">アクティブな電源プラン</span><span class="sxs-lookup"><span data-stu-id="c85c4-210">Active Power Plan</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-211">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-211">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-212">正しい電源計画がアクティブな状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-212">Checks that the correct power plan is active.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-213">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-213">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-214">バランス</span><span class="sxs-lookup"><span data-stu-id="c85c4-214">Balanced</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-215">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-215">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-216">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-216">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-217">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-217">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-218">生産性とバッテリー残量を最大化するには、"バランス" 電源プランを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-218">It is highly recommended to use the "Balanced" power plan to maximize productivity and battery life.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500"><span data-ttu-id="c85c4-219">Windows Update</span><span class="sxs-lookup"><span data-stu-id="c85c4-219">Windows Update</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-220">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-220">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-221">デバイスが Windows 更新プログラムで最新の情報を提供している場合にチェックします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-221">Checks if the device is up to date with Windows updates.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-222">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-222">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-223">Microsoft Silverlight (KB4023307)、Windows Defender ウイルス対策の定義の更新 - KB2267602 (定義 1.279.1433.0)</span><span class="sxs-lookup"><span data-stu-id="c85c4-223">Microsoft Silverlight (KB4023307), Definition Update for Windows Defender Antivirus - KB2267602 (Definition 1.279.1433.0)</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-224">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-224">Condition:</span></span></strong></td><td><font color="ff9500"><span data-ttu-id="c85c4-225">最適ではない</span><span class="sxs-lookup"><span data-stu-id="c85c4-225">Not Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-226">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-226">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-227">最新のウィンドウに更新すると、最新のファームウェアとドライバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c85c4-227">Updating to the latest windows makes sure you are on the latest firmware and drivers.</span></span> <span data-ttu-id="c85c4-228">デバイスを常に最新の状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-228">It is recommended to always keep your device up to date</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-229">空きハード ドライブ領域</span><span class="sxs-lookup"><span data-stu-id="c85c4-229">Free Hard Drive Space</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-230">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-230">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-231">低い空きハード ドライブ領域をチェックします。</span><span class="sxs-lookup"><span data-stu-id="c85c4-231">Checks for low free hard drive space.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-232">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-232">Value:</span></span></strong></td><td><span data-ttu-id="c85c4-233">66%</span><span class="sxs-lookup"><span data-stu-id="c85c4-233">66%</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-234">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-234">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-235">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-235">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-236">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-236">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-237">最適なパフォーマンスを得る場合は、ハード ドライブの容量の少なくとも 10% が空き領域として必要です。</span><span class="sxs-lookup"><span data-stu-id="c85c4-237">For best performance, your hard drive should have at least 10% of its capacity as free space.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-238">非機能デバイス</span><span class="sxs-lookup"><span data-stu-id="c85c4-238">Non-Functioning Devices</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-239">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-239">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-240">デバイス マネージャーの機能しないデバイスの一覧。</span><span class="sxs-lookup"><span data-stu-id="c85c4-240">List of non-functioning devices in Device Manager.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-241">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-241">Value:</span></span></strong></td><td></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-242">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-242">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-243">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-243">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-244">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-244">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-245">デバイス マネージャーの非機能デバイスは、各ハードウェア コンポーネントの省電力など、Surface デバイスで予期しない問題を引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c85c4-245">Non-functioning devices in Device Manager may cause unpredictable problems with Surface devices such as, but not limited to, no power savings for the respective hardware component.</span></span></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00"><span data-ttu-id="c85c4-246">外部モニター</span><span class="sxs-lookup"><span data-stu-id="c85c4-246">External Monitor</span></span></font></th></tr>
<tr><td><strong><span data-ttu-id="c85c4-247">説明:</span><span class="sxs-lookup"><span data-stu-id="c85c4-247">Description:</span></span></strong></td><td><span data-ttu-id="c85c4-248">互換性の問題がある可能性がある外部モニターを確認します。</span><span class="sxs-lookup"><span data-stu-id="c85c4-248">Checks for an external monitor that may have compatibility issues.</span></span></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-249">値:</span><span class="sxs-lookup"><span data-stu-id="c85c4-249">Value:</span></span></strong></td><td></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-250">条件:</span><span class="sxs-lookup"><span data-stu-id="c85c4-250">Condition:</span></span></strong></td><td><font color="00ff00"><span data-ttu-id="c85c4-251">最適</span><span class="sxs-lookup"><span data-stu-id="c85c4-251">Optimal</span></span></font></td></tr>
<tr><td><strong><span data-ttu-id="c85c4-252">ガイダンス:</span><span class="sxs-lookup"><span data-stu-id="c85c4-252">Guidance:</span></span></strong></td><td><span data-ttu-id="c85c4-253">Surface デバイスとの互換性については、元の機器の製造元に確認してください。</span><span class="sxs-lookup"><span data-stu-id="c85c4-253">Check with the original equipment manufacturer for compatibility with your Surface device.</span></span></td></tr>
</table>
