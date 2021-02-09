---
title: Microsoft Surface Dock 1 Firmware Update
description: この記事では、Microsoft Surface Dock Firmware Update を使用して、元の Surface Dock 1 にファームウェアをインストールして管理する方法について説明します。 Surface デバイスにインストールすると、Surface デバイスに接続されている Surface Dock 1 デバイスが更新されます。
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 2/08/2021
ms.openlocfilehash: a0acaaf0676c3f4403a2b233297781579ca1f4ae
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319211"
---
# <span data-ttu-id="7b670-104">Microsoft Surface Dock Firmware Update</span><span class="sxs-lookup"><span data-stu-id="7b670-104">Microsoft Surface Dock Firmware Update</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b670-105">この記事には、IT 管理者向け技術的な手順が記載されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-105">This article contains technical instructions for IT administrators.</span></span> <span data-ttu-id="7b670-106">ホーム ユーザーの場合は、Microsoft サポート サイトで[Surface ドックのファームウェア](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)を更新   する方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-106">If you are a home user, please see [How to update your Surface Dock Firmware](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) on the Microsoft Support site.</span></span> <span data-ttu-id="7b670-107">サポート サイトの手順は、以下の一般的なインストール手順と同じですが、この記事には、ネットワーク上の複数のデバイスへの更新プログラムの監視、検証、展開に関する追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-107">The instructions at the support site are the same as the general installation steps below, but this article has additional information for monitoring, verifying, and deploying the update to multiple devices on a network.</span></span>

<span data-ttu-id="7b670-108">この記事では、Microsoft Surface Dock Firmware Update を使用して、元の Surface Dock 1 にファームウェアをインストールして管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b670-108">This article explains how to use Microsoft Surface Dock Firmware Update to install and manage firmware on the original Surface Dock 1.</span></span> <span data-ttu-id="7b670-109">Surface デバイスにインストールすると、Surface デバイスに接続されている Surface Dock 1 デバイスが更新されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-109">When installed on your Surface device, it will update Surface Dock 1 devices attached to your Surface device.</span></span>

> [!NOTE]
> <span data-ttu-id="7b670-110">この記事は、Windows Update または Microsoft Endpoint Configuration Manager または他の MSI 展開ツールを使用して自動的に更新プログラムを受信する Surface Dock 2 には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7b670-110">This article does not apply to Surface Dock 2, which receives updates automatically via Windows Update or by using Microsoft Endpoint Configuration Manager or other MSI deployment tools.</span></span> <span data-ttu-id="7b670-111">詳しくは [、Surface ドックの新機能をご覧ください](surface-dock-whats-new.md)。</span><span class="sxs-lookup"><span data-stu-id="7b670-111">To learn more, see [What’s new in Surface Dock](surface-dock-whats-new.md).</span></span>

<span data-ttu-id="7b670-112">このツールは、以前は It 向け Surface Tools の一部としてダウンロード可能だった、以前の Microsoft Surface Dock Updater ツールに取ってかわるツールです。</span><span class="sxs-lookup"><span data-stu-id="7b670-112">This tool supersedes the earlier Microsoft Surface Dock Updater tool, previously available for download as part of Surface Tools for IT.</span></span> <span data-ttu-id="7b670-113">以前のツールの名前は Surface_Dock_Updater_vx.xx.xxx.x.msi (x はバージョン番号を示します) で、ダウンロードできなくなったので、使用できません。</span><span class="sxs-lookup"><span data-stu-id="7b670-113">The earlier tool was named Surface_Dock_Updater_vx.xx.xxx.x.msi (where x indicates the version number) and is no longer available for download and should not be used.</span></span>

## <span data-ttu-id="7b670-114">Surface ドックのファームウェア更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="7b670-114">Install the Surface Dock Firmware Update</span></span>

<span data-ttu-id="7b670-115">このセクションでは、ファームウェア更新プログラムを手動でインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b670-115">This section describes how to manually install the firmware update.</span></span>

> [!NOTE]
> <span data-ttu-id="7b670-116">Microsoft は、Surface Dock Firmware Update の新しいバージョンを定期的にリリースしています。</span><span class="sxs-lookup"><span data-stu-id="7b670-116">Microsoft periodically releases new versions of Surface Dock Firmware Update.</span></span> <span data-ttu-id="7b670-117">MSI ファイルは自己更新ではありません。</span><span class="sxs-lookup"><span data-stu-id="7b670-117">The MSI file is not self-updating.</span></span> <span data-ttu-id="7b670-118">MSI を Surface デバイスに展開し、ファームウェアの新しいバージョンがリリースされている場合は、新しいバージョンを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b670-118">If you have deployed the MSI to Surface devices and a new version of the firmware is released, you will need to deploy the new version.</span></span>

1. <span data-ttu-id="7b670-119">[Microsoft Surface Dock Firmware Update をダウンロードしてインストールします](https://www.microsoft.com/download/details.aspx?id=46703)。</span><span class="sxs-lookup"><span data-stu-id="7b670-119">Download and install [Microsoft Surface Dock Firmware Update](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
    - <span data-ttu-id="7b670-120">この更新プログラムには、Windows 10 バージョン 1803 以降を実行している Surface デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="7b670-120">The update requires a Surface device running Windows 10, version 1803 or later.</span></span>
    - <span data-ttu-id="7b670-121">MSI ファイルをインストールすると、Surface を再起動するように求めるメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b670-121">Installing the MSI file might prompt you to restart Surface.</span></span> <span data-ttu-id="7b670-122">ただし、更新を実行するために再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b670-122">However, restarting is not required to perform the update.</span></span>

2. <span data-ttu-id="7b670-123">Surface ドックから Surface デバイスを取り外し、5 秒待って再接続します。</span><span class="sxs-lookup"><span data-stu-id="7b670-123">Disconnect your Surface device from the Surface Dock, wait ~5 seconds, and then reconnect.</span></span> <span data-ttu-id="7b670-124">Surface ドックのファームウェア更新プログラムは、バックグラウンドでサイレント モードでドックを更新します。</span><span class="sxs-lookup"><span data-stu-id="7b670-124">The Surface Dock Firmware Update will update the dock silently in background.</span></span> <span data-ttu-id="7b670-125">プロセスが完了するには数分かかる場合があります。中断された場合でも続行されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-125">The process can take a few minutes to complete and will continue even if interrupted.</span></span> 

## <span data-ttu-id="7b670-126">Surface ドックのファームウェア更新プログラムを監視する</span><span class="sxs-lookup"><span data-stu-id="7b670-126">Monitor the Surface Dock Firmware Update</span></span>

<span data-ttu-id="7b670-127">このセクションは省略可能であり、ファームウェア更新プログラムのインストールを監視する方法の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7b670-127">This section is optional and provides an overview of how to monitor installation of the firmware update.</span></span> 

<span data-ttu-id="7b670-128">更新プログラムを監視するには:</span><span class="sxs-lookup"><span data-stu-id="7b670-128">To monitor the update:</span></span>

1. <span data-ttu-id="7b670-129">イベント ビューアーを開き **、Windows Logs > アプリケーション**を参照し\*\*\*\*、右側のウィンドウの [操作\*\*\*\*] で [現在のログのフィルター処理]\*\*\*\* をクリックし、イベント ソースの横に**SurfaceDockFwUpdate**と入力して **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b670-129">Open Event Viewer, browse to **Windows Logs > Application**, and then under **Actions** in the right-hand pane click **Filter Current Log**, enter **SurfaceDockFwUpdate** next to **Event sources**, and then click **OK**.</span></span>

2. <span data-ttu-id="7b670-130">管理者特権でのコマンド プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b670-130">Type the following command at an elevated command prompt:</span></span>

    ```console
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. <span data-ttu-id="7b670-131">この記事の次のセクションで説明するように [、更新プログラム](#install-the-surface-dock-firmware-update) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b670-131">Install the update as described in the [next section](#install-the-surface-dock-firmware-update) of this article.</span></span>

4. <span data-ttu-id="7b670-132">次のテキストを含むイベント 2007 は、更新が正常に完了したかどうかを示します。ファームウェアの更新が完了しました **。hr=0 DriverTelementry EventCode = 2007**。</span><span class="sxs-lookup"><span data-stu-id="7b670-132">Event 2007 with the following text indicates a successful update: **Firmware update finished. hr=0 DriverTelementry EventCode = 2007**.</span></span> 

   <span data-ttu-id="7b670-133">更新に失敗した場合、イベント ID 2007 は情報ではなく **Error** イベントとして **表示されます**。</span><span class="sxs-lookup"><span data-stu-id="7b670-133">If the update is not successful, then event ID 2007 will be displayed as an **Error** event rather than **Information**.</span></span> <span data-ttu-id="7b670-134">また、Windows レジストリで報告されているバージョンは最新の状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="7b670-134">Additionally, the version reported in the Windows Registry will not be current.</span></span>
   
5. <span data-ttu-id="7b670-135">更新が完了すると、更新された DWORD 値が現在のバージョンのツールに対応する Windows レジストリに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-135">When the update is complete, updated DWORD values will be displayed in the Windows Registry, corresponding to the current version of the tool.</span></span> <span data-ttu-id="7b670-136">詳細については [、この記事の「](#versions-reference) バージョンリファレンス」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-136">See the [Versions reference](#versions-reference) section in this article for details.</span></span> <span data-ttu-id="7b670-137">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="7b670-137">For example:</span></span>

    - <span data-ttu-id="7b670-138">Component10CurrentFwVersion 0x04ac3970 (78395760)</span><span class="sxs-lookup"><span data-stu-id="7b670-138">Component10CurrentFwVersion 0x04ac3970 (78395760)</span></span>
    - <span data-ttu-id="7b670-139">Component20CurrentFwVersion 0x04915a70 (76634736)</span><span class="sxs-lookup"><span data-stu-id="7b670-139">Component20CurrentFwVersion 0x04915a70 (76634736)</span></span>

>[!TIP]
><span data-ttu-id="7b670-140">イベント テキストに 「ソース SurfaceDockFwUpdate のイベント ID xxxx の説明が見つかりません」と表示される場合、これは予期される値であり、無視してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="7b670-140">If you see "The description for Event ID xxxx from source SurfaceDockFwUpdate cannot be found" in event text, this is expected and can be ignored.</span></span>

<span data-ttu-id="7b670-141">この記事の以下のセクションも参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-141">Also see the following sections in this article:</span></span> 
  - [<span data-ttu-id="7b670-142">ファームウェア更新の完了を確認する方法</span><span class="sxs-lookup"><span data-stu-id="7b670-142">How to verify completion of firmware update</span></span>](#how-to-verify-completion-of-the-firmware-update)
  - [<span data-ttu-id="7b670-143">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="7b670-143">Event logging</span></span>](#event-logging)
  - [<span data-ttu-id="7b670-144">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="7b670-144">Troubleshooting tips</span></span>](#troubleshooting-tips)
  - [<span data-ttu-id="7b670-145">バージョン リファレンス</span><span class="sxs-lookup"><span data-stu-id="7b670-145">Versions reference</span></span>](#versions-reference)

## <span data-ttu-id="7b670-146">ネットワーク展開</span><span class="sxs-lookup"><span data-stu-id="7b670-146">Network deployment</span></span>

<span data-ttu-id="7b670-147">Windows インストーラー コマンド (Msiexec.exe) を使って、Surface Dock Firmware Update をネットワーク上の複数のデバイスに展開できます。</span><span class="sxs-lookup"><span data-stu-id="7b670-147">You can use Windows Installer commands (Msiexec.exe) to deploy Surface Dock Firmware Update to multiple devices across your network.</span></span> <span data-ttu-id="7b670-148">Microsoft Endpoint Configuration Manager または他の展開ツールを使用する場合は、次の構文を入力してインストールがサイレント モードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-148">When using Microsoft Endpoint Configuration Manager or other deployment tool, enter the following syntax to ensure the installation is silent:</span></span>

- **<span data-ttu-id="7b670-149">Msiexec.exe /i \<path to msi file\> /quiet /norestart</span><span class="sxs-lookup"><span data-stu-id="7b670-149">Msiexec.exe /i \<path to msi file\> /quiet /norestart</span></span>** 

<span data-ttu-id="7b670-150">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="7b670-150">For example:</span></span>

```console
msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
```

> [!NOTE]
> <span data-ttu-id="7b670-151">ログ ファイルは既定では作成されません。</span><span class="sxs-lookup"><span data-stu-id="7b670-151">A log file is not created by default.</span></span> <span data-ttu-id="7b670-152">ログ ファイルを作成するには、"/l*v [path]" を追加する必要があります。例: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"</span><span class="sxs-lookup"><span data-stu-id="7b670-152">In order to create a log file, you will need to append "/l*v [path]". For example: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"</span></span>

<span data-ttu-id="7b670-153">詳細については、コマンド ライン オプション [のドキュメントを参照](https://docs.microsoft.com/windows/win32/msi/command-line-options) してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-153">For more information, refer to [Command line options](https://docs.microsoft.com/windows/win32/msi/command-line-options) documentation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b670-154">他の方法で Surface ドックを最新の状態に保つ場合は [、「Surface ドック](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) の更新」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-154">If you want to keep your Surface Dock updated using any other method, refer to [Update your Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) for details.</span></span>

## <span data-ttu-id="7b670-155">Intune の展開</span><span class="sxs-lookup"><span data-stu-id="7b670-155">Intune deployment</span></span>

<span data-ttu-id="7b670-156">Intune を使って Surface ドックのファームウェア更新プログラムをデバイスに配布できます。</span><span class="sxs-lookup"><span data-stu-id="7b670-156">You can use Intune to distribute Surface Dock Firmware Update to your devices.</span></span> <span data-ttu-id="7b670-157">まず、次のドキュメントで説明するように、MSI ファイルを .intunewin 形式に変換する [必要があります。Intune スタンドアロン - Win32 アプリ管理](https://docs.microsoft.com/intune/apps/apps-win32-app-management)。</span><span class="sxs-lookup"><span data-stu-id="7b670-157">First you will need to convert the MSI file to the .intunewin format, as described in the following documentation: [Intune Standalone - Win32 app management](https://docs.microsoft.com/intune/apps/apps-win32-app-management).</span></span>

<span data-ttu-id="7b670-158">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b670-158">Use the following command:</span></span>
  - **<span data-ttu-id="7b670-159">msiexec /i \<path to msi file\> /quiet /q</span><span class="sxs-lookup"><span data-stu-id="7b670-159">msiexec /i \<path to msi file\> /quiet /q</span></span>**

## <span data-ttu-id="7b670-160">ファームウェア更新プログラムの完了を確認する方法</span><span class="sxs-lookup"><span data-stu-id="7b670-160">How to verify completion of the firmware update</span></span>

<span data-ttu-id="7b670-161">Surface ドックのファームウェアは、次の 2 つのコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-161">Surface dock firmware consists of two components:</span></span>

- <span data-ttu-id="7b670-162">**Component10:** マイクロ コントローラー ユニット (MCU) ファームウェア</span><span class="sxs-lookup"><span data-stu-id="7b670-162">**Component10:** Micro controller unit (MCU) firmware</span></span>
- <span data-ttu-id="7b670-163">**Component20:** ディスプレイ ポート (DP) ファームウェア。</span><span class="sxs-lookup"><span data-stu-id="7b670-163">**Component20:** Display port (DP) firmware.</span></span>

<span data-ttu-id="7b670-164">Surface Dock Firmware Update が正常に完了すると、これらのファームウェア コンポーネントの新しいレジストリ キー値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-164">Successful completion of Surface Dock Firmware Update results in new registry key values for these firmware components.</span></span>

**<span data-ttu-id="7b670-165">更新プログラムを確認するには:</span><span class="sxs-lookup"><span data-stu-id="7b670-165">To verify updates:</span></span>**

1. <span data-ttu-id="7b670-166">Regedit を開き、次のレジストリ パスに移動します。</span><span class="sxs-lookup"><span data-stu-id="7b670-166">Open Regedit and navigate to the following registry path:</span></span>

    - **<span data-ttu-id="7b670-167">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span><span class="sxs-lookup"><span data-stu-id="7b670-167">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span></span>**

2. <span data-ttu-id="7b670-168">次のレジストリ キーを探します **。Component10CurrentFwVersion と Component20CurrentFwVersion**は、デバイスに現在インストールされているファームウェアを参照します。</span><span class="sxs-lookup"><span data-stu-id="7b670-168">Look for the registry keys: **Component10CurrentFwVersion and Component20CurrentFwVersion**, which refer to the firmware that is currently on the device.</span></span>

   ![Surface ドックファームウェア更新プログラムのインストール プロセス](images/regeditDock.png)

3. <span data-ttu-id="7b670-170">新しいレジストリ キーの値が、このドキュメントの最後の「バージョン」のリファレンスに記載されている更新されたレジストリ キー値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b670-170">Verify the new registry key values match the updated registry key values listed in the Versions reference at the end of this document.</span></span> <span data-ttu-id="7b670-171">値が一致する場合、ファームウェアは正常に更新されました。</span><span class="sxs-lookup"><span data-stu-id="7b670-171">If the values match, the firmware was updated successfully.</span></span>

4. <span data-ttu-id="7b670-172">確認できない場合は、次のセクションでイベント ログとトラブルシューティングのヒントを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-172">If unable to verify, review Event logging and Troubleshooting tips in the next section.</span></span>

## <span data-ttu-id="7b670-173">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="7b670-173">Event logging</span></span>

**<span data-ttu-id="7b670-174">表 1.</span><span class="sxs-lookup"><span data-stu-id="7b670-174">Table 1.</span></span> <span data-ttu-id="7b670-175">Surface Dock Firmware Update のログ ファイル</span><span class="sxs-lookup"><span data-stu-id="7b670-175">Log files for Surface Dock Firmware Update</span></span>**

| <span data-ttu-id="7b670-176">ログ</span><span class="sxs-lookup"><span data-stu-id="7b670-176">Log</span></span>                              | <span data-ttu-id="7b670-177">Location</span><span class="sxs-lookup"><span data-stu-id="7b670-177">Location</span></span>                               | <span data-ttu-id="7b670-178">備考</span><span class="sxs-lookup"><span data-stu-id="7b670-178">Notes</span></span>                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7b670-179">Surface ドックのファームウェア更新ログ</span><span class="sxs-lookup"><span data-stu-id="7b670-179">Surface Dock Firmware Update log</span></span> | <span data-ttu-id="7b670-180">パスを指定する必要があります (注を参照)</span><span class="sxs-lookup"><span data-stu-id="7b670-180">Path needs to be specified (see note)</span></span> | <span data-ttu-id="7b670-181">このツールの以前のバージョンでは、アプリケーションとサービス ログ\Microsoft Surface Dock Updater にイベントが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7b670-181">Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>                                                                                                  |
| <span data-ttu-id="7b670-182">Windows デバイス インストール ログ</span><span class="sxs-lookup"><span data-stu-id="7b670-182">Windows Device Install log</span></span>       | <span data-ttu-id="7b670-183">%windir%\inf\setupapi.dev.log</span><span class="sxs-lookup"><span data-stu-id="7b670-183">%windir%\inf\setupapi.dev.log</span></span>           | <span data-ttu-id="7b670-184">デバイス インストール ログの使用の詳細については [、SetupAPI ログのドキュメントを参照](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) してください。</span><span class="sxs-lookup"><span data-stu-id="7b670-184">For more information about using Device Install Log, refer to [SetupAPI Logging](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) documentation.</span></span> |


**<span data-ttu-id="7b670-185">表 2.</span><span class="sxs-lookup"><span data-stu-id="7b670-185">Table 2.</span></span> <span data-ttu-id="7b670-186">Surface ドックファームウェア更新プログラムのイベント ログの ID</span><span class="sxs-lookup"><span data-stu-id="7b670-186">Event log IDs for Surface Dock Firmware Update</span></span>**<br>
<span data-ttu-id="7b670-187">イベントは、アプリケーション イベント ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="7b670-187">Events are logged in the Application Event Log.</span></span>  <span data-ttu-id="7b670-188">注: このツールの以前のバージョンでは、アプリケーションとサービス ログ\Microsoft Surface Dock Updater にイベントが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7b670-188">Note:  Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>

| <span data-ttu-id="7b670-189">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7b670-189">Event ID</span></span> | <span data-ttu-id="7b670-190">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="7b670-190">Event type</span></span>                                                           |
| -------- | -------------------------------------------------------------------- |
| <span data-ttu-id="7b670-191">2001</span><span class="sxs-lookup"><span data-stu-id="7b670-191">2001</span></span>     | <span data-ttu-id="7b670-192">ドックのファームウェア更新が開始されました。</span><span class="sxs-lookup"><span data-stu-id="7b670-192">Dock firmware update has started.</span></span>                                    |
| <span data-ttu-id="7b670-193">2002</span><span class="sxs-lookup"><span data-stu-id="7b670-193">2002</span></span>     | <span data-ttu-id="7b670-194">ドックのファームウェアの更新は、ドックが最新の情報として知られているため、スキップされました。</span><span class="sxs-lookup"><span data-stu-id="7b670-194">Dock firmware update skipped because dock is known to be up to date.</span></span> |
| <span data-ttu-id="7b670-195">2003</span><span class="sxs-lookup"><span data-stu-id="7b670-195">2003</span></span>     | <span data-ttu-id="7b670-196">ドックのファームウェア更新プログラムがファームウェアのバージョンを取得できなかった。</span><span class="sxs-lookup"><span data-stu-id="7b670-196">Dock firmware update failed to get firmware version.</span></span>                 |
| <span data-ttu-id="7b670-197">2004</span><span class="sxs-lookup"><span data-stu-id="7b670-197">2004</span></span>     | <span data-ttu-id="7b670-198">ファームウェアバージョンの照会。</span><span class="sxs-lookup"><span data-stu-id="7b670-198">Querying the firmware version.</span></span>                                       |
| <span data-ttu-id="7b670-199">2005</span><span class="sxs-lookup"><span data-stu-id="7b670-199">2005</span></span>     | <span data-ttu-id="7b670-200">ドックのファームウェアが更新を開始できなかった。</span><span class="sxs-lookup"><span data-stu-id="7b670-200">Dock firmware failed to start update.</span></span>                                |
| <span data-ttu-id="7b670-201">2006</span><span class="sxs-lookup"><span data-stu-id="7b670-201">2006</span></span>     | <span data-ttu-id="7b670-202">オファーとペイロードのペアの送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="7b670-202">Failed to send offer/payload pairs.</span></span>                                  |
| <span data-ttu-id="7b670-203">2007</span><span class="sxs-lookup"><span data-stu-id="7b670-203">2007</span></span>     | <span data-ttu-id="7b670-204">ファームウェアの更新が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7b670-204">Firmware update finished.</span></span>                                            |
| <span data-ttu-id="7b670-205">2008</span><span class="sxs-lookup"><span data-stu-id="7b670-205">2008</span></span>     | <span data-ttu-id="7b670-206">BEGIN ドックの利用統計情報。</span><span class="sxs-lookup"><span data-stu-id="7b670-206">BEGIN dock telemetry.</span></span>                                                |
| <span data-ttu-id="7b670-207">2011</span><span class="sxs-lookup"><span data-stu-id="7b670-207">2011</span></span>     | <span data-ttu-id="7b670-208">END ドックの利用統計情報。</span><span class="sxs-lookup"><span data-stu-id="7b670-208">END dock telemetry.</span></span>                                                  |

## <span data-ttu-id="7b670-209">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="7b670-209">Troubleshooting tips</span></span>

- <span data-ttu-id="7b670-210">Surface ドックの電源を AC 電源から完全に取り外して、Surface ドックをリセットします。</span><span class="sxs-lookup"><span data-stu-id="7b670-210">Completely disconnect power for Surface dock from the AC power to reset the Surface Dock.</span></span>
- <span data-ttu-id="7b670-211">Surface ドック以外のすべての周辺機器を取り外します。</span><span class="sxs-lookup"><span data-stu-id="7b670-211">Disconnect all peripherals except for the Surface Dock.</span></span>
- <span data-ttu-id="7b670-212">現在の Surface Dock Firmware Update をアンインストールし、最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b670-212">Uninstall any current Surface Dock Firmware Update and then install the latest version.</span></span>
- <span data-ttu-id="7b670-213">Surface ドックが取り外され、ドックのイーサネット ポートの LED を介して監視された状態で更新が完了するのに十分な時間を確保します。</span><span class="sxs-lookup"><span data-stu-id="7b670-213">Ensure that the Surface Dock is disconnected, and then allow enough time for the update to complete as monitored via an LED in the Ethernet port of the dock.</span></span> <span data-ttu-id="7b670-214">Surface ドックの電源を取り外す前に、LED が点滅し始めるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="7b670-214">Wait until the LED stops blinking before you unplug Surface Dock from power.</span></span>
- <span data-ttu-id="7b670-215">Surface ドックを別のデバイスに接続して、ドックを更新することができるか確認します。</span><span class="sxs-lookup"><span data-stu-id="7b670-215">Connect the Surface Dock to a different device to see if it is able to update the dock.</span></span>

## <span data-ttu-id="7b670-216">バージョン リファレンス</span><span class="sxs-lookup"><span data-stu-id="7b670-216">Versions reference</span></span>

>[!NOTE]
><span data-ttu-id="7b670-217">インストール ファイルは、Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI\*\* (Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi \*\* など) の名前付け形式でリリースされ、既定では C:\Program Files\SurfaceUpdate にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b670-217">The installation file is released with the following naming format: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ex: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) and installs by default to C:\Program Files\SurfaceUpdate.</span></span>

### <span data-ttu-id="7b670-218">バージョン 1.53.139.0</span><span class="sxs-lookup"><span data-stu-id="7b670-218">Version 1.53.139.0</span></span>
*<span data-ttu-id="7b670-219">リリース日: 2020 年 8 月 4 日</span><span class="sxs-lookup"><span data-stu-id="7b670-219">Release Date: August 4, 2020</span></span>*

<span data-ttu-id="7b670-220">このバージョンの Surface Dock Firmware Update には、次のバグ修正プログラムとサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b670-220">This version of Surface Dock Firmware Update includes bug fixes and support for:</span></span>
- <span data-ttu-id="7b670-221">Surface Pro X を使った Surface ドック 1 の更新。</span><span class="sxs-lookup"><span data-stu-id="7b670-221">Updating Surface Dock 1 using Surface Pro X.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="7b670-222">Surface Pro X を実行している場合は、次をダウンロードします。ARM64 ビルド。</span><span class="sxs-lookup"><span data-stu-id="7b670-222">If you're running Surface Pro X, download the .ARM64 build.</span></span> <span data-ttu-id="7b670-223">その他すべてのデバイスでは、AMD64 ビルドを使います。</span><span class="sxs-lookup"><span data-stu-id="7b670-223">For all other devices, use the AMD64 build.</span></span> 

#### <span data-ttu-id="7b670-224">レジストリ キーの値</span><span class="sxs-lookup"><span data-stu-id="7b670-224">Registry key values</span></span>

<span data-ttu-id="7b670-225">ファームウェア更新プログラムの状態を示すレジストリ値は、このツールの以前のバージョンから変更されていません。</span><span class="sxs-lookup"><span data-stu-id="7b670-225">The registry values that indicate the status of firmware updates are unchanged from the previous version of this tool:</span></span> 

- <span data-ttu-id="7b670-226">Component10CurrentFwVersion を **4ac3970 に更新しました**。</span><span class="sxs-lookup"><span data-stu-id="7b670-226">Component10CurrentFwVersion updated to **4ac3970**.</span></span>
- <span data-ttu-id="7b670-227">Component20CurrentFwVersion を **4a1d570**に更新しました。</span><span class="sxs-lookup"><span data-stu-id="7b670-227">Component20CurrentFwVersion updated to **4a1d570**.</span></span>
 
### <span data-ttu-id="7b670-228">バージョン 1.42.139</span><span class="sxs-lookup"><span data-stu-id="7b670-228">Version 1.42.139</span></span> 
*<span data-ttu-id="7b670-229">リリース日: 2019 年 9 月 18 日</span><span class="sxs-lookup"><span data-stu-id="7b670-229">Release Date: September 18 2019</span></span>*

<span data-ttu-id="7b670-230">このバージョンは、Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSIに含まれている場合に、ファームウェアを更新します。</span><span class="sxs-lookup"><span data-stu-id="7b670-230">This version, contained in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, updates firmware in the background.</span></span> 

#### <span data-ttu-id="7b670-231">レジストリ キーの値の更新</span><span class="sxs-lookup"><span data-stu-id="7b670-231">Updated registry key values</span></span>

- <span data-ttu-id="7b670-232">Component10CurrentFwVersion を **4ac3970 に更新しました**。</span><span class="sxs-lookup"><span data-stu-id="7b670-232">Component10CurrentFwVersion updated to **4ac3970**.</span></span>
- <span data-ttu-id="7b670-233">Component20CurrentFwVersion を **4a1d570**に更新しました。</span><span class="sxs-lookup"><span data-stu-id="7b670-233">Component20CurrentFwVersion updated to **4a1d570**.</span></span>

<span data-ttu-id="7b670-234">Surface Pro 7 と Surface Laptop 3 のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="7b670-234">It adds support for Surface Pro 7 and Surface Laptop 3.</span></span>

## <span data-ttu-id="7b670-235">レガシ バージョン</span><span class="sxs-lookup"><span data-stu-id="7b670-235">Legacy versions</span></span>

### <span data-ttu-id="7b670-236">バージョン 2.23.139.0</span><span class="sxs-lookup"><span data-stu-id="7b670-236">Version 2.23.139.0</span></span>
*<span data-ttu-id="7b670-237">リリース日: 2018 年 10 月 10 日</span><span class="sxs-lookup"><span data-stu-id="7b670-237">Release Date: 10 October 2018</span></span>*

<span data-ttu-id="7b670-238">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-238">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="7b670-239">Surface Pro 6 のサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="7b670-239">Add support for Surface Pro 6</span></span>
- <span data-ttu-id="7b670-240">Surface Laptop 2 のサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="7b670-240">Add support for Surface Laptop 2</span></span>


### <span data-ttu-id="7b670-241">バージョン 2.22.139.0</span><span class="sxs-lookup"><span data-stu-id="7b670-241">Version 2.22.139.0</span></span>
*<span data-ttu-id="7b670-242">リリース日: 2018 年 7 月 26 日</span><span class="sxs-lookup"><span data-stu-id="7b670-242">Release Date: 26 July 2018</span></span>*

<span data-ttu-id="7b670-243">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-243">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="7b670-244">更新の信頼性を高める</span><span class="sxs-lookup"><span data-stu-id="7b670-244">Increase update reliability</span></span>
- <span data-ttu-id="7b670-245">Surface Go のサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="7b670-245">Add support for Surface Go</span></span>

### <span data-ttu-id="7b670-246">バージョン 2.12.136.0</span><span class="sxs-lookup"><span data-stu-id="7b670-246">Version 2.12.136.0</span></span>
*<span data-ttu-id="7b670-247">リリース日: 2018 年 1 月 29 日</span><span class="sxs-lookup"><span data-stu-id="7b670-247">Release Date: 29 January 2018</span></span>*

<span data-ttu-id="7b670-248">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-248">This version of Surface Dock Updater adds support for the following:</span></span>
* <span data-ttu-id="7b670-249">Surface ドックのメイン チップセットのファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-249">Update for Surface Dock Main Chipset Firmware</span></span>
* <span data-ttu-id="7b670-250">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-250">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="7b670-251">Surface Book 2 または Surface Book で使用する場合の、外部ディスプレイの表示安定性の向上</span><span class="sxs-lookup"><span data-stu-id="7b670-251">Improved display stability for external displays when used with Surface Book or Surface Book 2</span></span>

<span data-ttu-id="7b670-252">さらに、Surface Book デバイスにこのバージョンの Surface Dock Updater をインストールした場合、以下の機能も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b670-252">Additionally, installation of this version of Surface Dock Updater on Surface Book devices includes the following:</span></span>
* <span data-ttu-id="7b670-253">Surface Book Base Firmware 更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-253">Update for Surface Book Base Firmware</span></span>
* <span data-ttu-id="7b670-254">Surface Book デバイスを対象とした機能強化による Surface ドック ファームウェア更新プログラムのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="7b670-254">Added support for Surface Dock firmware updates with improvements targeted to Surface Book devices</span></span>


### <span data-ttu-id="7b670-255">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="7b670-255">Version 2.9.136.0</span></span>
*<span data-ttu-id="7b670-256">リリース日: 2017 年 11 月 3 日</span><span class="sxs-lookup"><span data-stu-id="7b670-256">Release date: November 3, 2017</span></span>*

<span data-ttu-id="7b670-257">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-257">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="7b670-258">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-258">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="7b670-259">パッシブ ディスプレイ ポート アダプター経由でのオーディオの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="7b670-259">Resolves an issue with audio over passive display port adapters</span></span>

### <span data-ttu-id="7b670-260">バージョン 2.1.15.0</span><span class="sxs-lookup"><span data-stu-id="7b670-260">Version 2.1.15.0</span></span>
*<span data-ttu-id="7b670-261">リリース日 : 2017 年 6 月 19 日</span><span class="sxs-lookup"><span data-stu-id="7b670-261">Release date: June 19, 2017</span></span>*

<span data-ttu-id="7b670-262">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-262">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="7b670-263">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="7b670-263">Surface Laptop</span></span>
* <span data-ttu-id="7b670-264">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="7b670-264">Surface Pro</span></span>

### <span data-ttu-id="7b670-265">バージョン 2.1.6.0</span><span class="sxs-lookup"><span data-stu-id="7b670-265">Version 2.1.6.0</span></span>
*<span data-ttu-id="7b670-266">リリース日: 2016 年 4 月 7 日</span><span class="sxs-lookup"><span data-stu-id="7b670-266">Release date: April 7, 2017</span></span>*

<span data-ttu-id="7b670-267">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-267">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="7b670-268">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-268">Update for Surface Dock DisplayPort firmware</span></span>
* <span data-ttu-id="7b670-269">Windows 10 が必要</span><span class="sxs-lookup"><span data-stu-id="7b670-269">Requires Windows 10</span></span>

### <span data-ttu-id="7b670-270">バージョン 2.0.22.0</span><span class="sxs-lookup"><span data-stu-id="7b670-270">Version 2.0.22.0</span></span>
*<span data-ttu-id="7b670-271">リリース日: 2016 年 10 月 21 日</span><span class="sxs-lookup"><span data-stu-id="7b670-271">Release date: October 21, 2016</span></span>*

<span data-ttu-id="7b670-272">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-272">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="7b670-273">Surface ドックの USB ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-273">Update for Surface Dock USB firmware</span></span>
* <span data-ttu-id="7b670-274">イーサネット、オーディオ、USB ポートの信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="7b670-274">Improved reliability of Ethernet, audio, and USB ports</span></span>

### <span data-ttu-id="7b670-275">バージョン 1.0.8.0</span><span class="sxs-lookup"><span data-stu-id="7b670-275">Version 1.0.8.0</span></span>
*<span data-ttu-id="7b670-276">リリース日: 2016 年 4 月 26 日</span><span class="sxs-lookup"><span data-stu-id="7b670-276">Release date: April 26, 2016</span></span>*

<span data-ttu-id="7b670-277">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7b670-277">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="7b670-278">Surface ドックのメイン チップセットのファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-278">Update for Surface Dock Main Chipset firmware</span></span>
* <span data-ttu-id="7b670-279">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="7b670-279">Update for Surface Dock DisplayPort firmware</span></span>

