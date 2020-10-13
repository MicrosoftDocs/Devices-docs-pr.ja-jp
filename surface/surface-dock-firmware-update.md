---
title: Microsoft Surface Dock ファームウェア更新プログラム-IT 管理者向けの技術情報
description: この記事では、Microsoft Surface Dock ファームウェア更新プログラムを使用して Surface Dock ファームウェアを更新する方法について説明します。 Surface デバイスにインストールすると、surface デバイスに接続されている Surface Dock が更新されます。
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
ms.date: 8/07/2020
ms.openlocfilehash: 9069903421d6e621dfbc31cd1cfaffb045fa9f19
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114555"
---
# <span data-ttu-id="459c1-104">Microsoft Surface Dock ファームウェアの更新: IT 管理者向けの技術情報</span><span class="sxs-lookup"><span data-stu-id="459c1-104">Microsoft Surface Dock Firmware Update: Technical information for IT admins</span></span>

> [!IMPORTANT]
> <span data-ttu-id="459c1-105">この記事には、IT 管理者向けの技術的な手順が記載されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-105">This article contains technical instructions for IT administrators.</span></span> <span data-ttu-id="459c1-106">ホームユーザーの場合は、Microsoft サポートサイトで[Surface Dock のファームウェアを更新する方法を](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)参照してください   。</span><span class="sxs-lookup"><span data-stu-id="459c1-106">If you are a home user, please see [How to update your Surface Dock Firmware](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) on the Microsoft Support site.</span></span> <span data-ttu-id="459c1-107">サポートサイトの手順は、以下の一般的なインストール手順と同じですが、この記事には、ネットワーク上の複数のデバイスの更新を監視、確認、展開するための追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-107">The instructions at the support site are the same as the general installation steps below, but this article has additional information for monitoring, verifying, and deploying the update to multiple devices on a network.</span></span>

<span data-ttu-id="459c1-108">この記事では、Microsoft Surface Dock ファームウェア更新プログラムを使用して、元の Surface Dock 1 のファームウェアを更新する方法について説明します。 Surface Dock 2 には適用されません。</span><span class="sxs-lookup"><span data-stu-id="459c1-108">This article explains how to use Microsoft Surface Dock Firmware Update to update firmware on the original Surface Dock 1 and does not apply to Surface Dock 2.</span></span> <span data-ttu-id="459c1-109">Surface デバイスにインストールすると、surface デバイスに接続されている Surface Dock が更新されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-109">When installed on your Surface device, it will update any Surface Dock attached to your Surface device.</span></span> 

<span data-ttu-id="459c1-110">このツールは、以前は、Surface tool の一部としてダウンロードできる以前の Microsoft Surface Dock アップデーターツールの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-110">This tool supersedes the earlier Microsoft Surface Dock Updater tool, previously available for download as part of Surface Tools for IT.</span></span> <span data-ttu-id="459c1-111">以前のツールには Surface_Dock_Updater_vx.xx.xxx.x.msi (x はバージョン番号を示す) という名前が付けられたため、ダウンロードできなくなり、使用できません。</span><span class="sxs-lookup"><span data-stu-id="459c1-111">The earlier tool was named Surface_Dock_Updater_vx.xx.xxx.x.msi (where x indicates the version number) and is no longer available for download and should not be used.</span></span>

## <span data-ttu-id="459c1-112">Surface Dock ファームウェアの更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="459c1-112">Install the Surface Dock Firmware Update</span></span>

<span data-ttu-id="459c1-113">このセクションでは、手動でファームウェア更新プログラムをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="459c1-113">This section describes how to manually install the firmware update.</span></span>

> [!NOTE]
> <span data-ttu-id="459c1-114">Microsoft は、Surface Dock ファームウェア更新プログラムの新しいバージョンを定期的にリリースしています。</span><span class="sxs-lookup"><span data-stu-id="459c1-114">Microsoft periodically releases new versions of Surface Dock Firmware Update.</span></span> <span data-ttu-id="459c1-115">MSI ファイルが自動更新されていない。</span><span class="sxs-lookup"><span data-stu-id="459c1-115">The MSI file is not self-updating.</span></span> <span data-ttu-id="459c1-116">MSI デバイスに MSI デバイスを展開し、ファームウェアの新しいバージョンがリリースされている場合は、新しいバージョンを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="459c1-116">If you have deployed the MSI to Surface devices and a new version of the firmware is released, you will need to deploy the new version.</span></span>

1. <span data-ttu-id="459c1-117">[Microsoft Surface Dock ファームウェアの更新プログラム](https://www.microsoft.com/download/details.aspx?id=46703)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="459c1-117">Download and install [Microsoft Surface Dock Firmware Update](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
    - <span data-ttu-id="459c1-118">更新プログラムでは、Windows 10 バージョン1803以降を搭載した Surface デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="459c1-118">The update requires a Surface device running Windows 10, version 1803 or later.</span></span>
    - <span data-ttu-id="459c1-119">MSI ファイルをインストールすると、Surface を再起動するように求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="459c1-119">Installing the MSI file might prompt you to restart Surface.</span></span> <span data-ttu-id="459c1-120">ただし、更新を実行するために再起動は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="459c1-120">However, restarting is not required to perform the update.</span></span>

2. <span data-ttu-id="459c1-121">Surface Dock から Surface デバイスを切り離し、最大5秒間待ってから再接続します。</span><span class="sxs-lookup"><span data-stu-id="459c1-121">Disconnect your Surface device from the Surface Dock, wait ~5 seconds, and then reconnect.</span></span> <span data-ttu-id="459c1-122">Surface Dock ファームウェアの更新により、Dock がバックグラウンドで自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-122">The Surface Dock Firmware Update will update the dock silently in background.</span></span> <span data-ttu-id="459c1-123">処理が完了するまで数分かかることがあり、中断された場合でも続行されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-123">The process can take a few minutes to complete and will continue even if interrupted.</span></span> 

## <span data-ttu-id="459c1-124">Surface Dock ファームウェアの更新を監視する</span><span class="sxs-lookup"><span data-stu-id="459c1-124">Monitor the Surface Dock Firmware Update</span></span>

<span data-ttu-id="459c1-125">このセクションはオプションであり、ファームウェア更新プログラムのインストールを監視する方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="459c1-125">This section is optional and provides an overview of how to monitor installation of the firmware update.</span></span> 

<span data-ttu-id="459c1-126">更新プログラムを監視するには:</span><span class="sxs-lookup"><span data-stu-id="459c1-126">To monitor the update:</span></span>

1. <span data-ttu-id="459c1-127">イベントビューアーを開き、[ **Windows ログ**] を参照し > アプリケーション] を参照して、右側のウィンドウの [**アクション**] で [**現在のログをフィルター**] をクリックし、[**イベントソース**] の横に**SurfaceDockFwUpdate**と入力して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="459c1-127">Open Event Viewer, browse to **Windows Logs > Application**, and then under **Actions** in the right-hand pane click **Filter Current Log**, enter **SurfaceDockFwUpdate** next to **Event sources**, and then click **OK**.</span></span>

2. <span data-ttu-id="459c1-128">昇格されたコマンドプロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="459c1-128">Type the following command at an elevated command prompt:</span></span>

    ```cmd
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. <span data-ttu-id="459c1-129">この記事の [次のセクション](#install-the-surface-dock-firmware-update) で説明するように、更新プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="459c1-129">Install the update as described in the [next section](#install-the-surface-dock-firmware-update) of this article.</span></span>
4. <span data-ttu-id="459c1-130">次のテキストが表示されたイベント2007は、ファームウェアの更新が完了したことを示し **ます。 DriverTelementry EventCode = 2007**。</span><span class="sxs-lookup"><span data-stu-id="459c1-130">Event 2007 with the following text indicates a successful update: **Firmware update finished. hr=0 DriverTelementry EventCode = 2007**.</span></span> 
    - <span data-ttu-id="459c1-131">更新に失敗した場合、イベント ID 2007 は**情報**ではなく**エラー**イベントとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-131">If the update is not successful, then event ID 2007 will be displayed as an **Error** event rather than **Information**.</span></span> <span data-ttu-id="459c1-132">さらに、Windows レジストリで報告されたバージョンは最新のものではありません。</span><span class="sxs-lookup"><span data-stu-id="459c1-132">Additionally, the version reported in the Windows Registry will not be current.</span></span>
5. <span data-ttu-id="459c1-133">更新が完了すると、更新された DWORD 値が、ツールの現在のバージョンに対応する Windows レジストリに表示されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-133">When the update is complete, updated DWORD values will be displayed in the Windows Registry, corresponding to the current version of the tool.</span></span> <span data-ttu-id="459c1-134">詳細については、この記事の「 [バージョンのリファレンス](#versions-reference) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="459c1-134">See the [Versions reference](#versions-reference) section in this article for details.</span></span> <span data-ttu-id="459c1-135">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="459c1-135">For example:</span></span>
    - <span data-ttu-id="459c1-136">Component10CurrentFwVersion 0x04ac3970 (78395760)</span><span class="sxs-lookup"><span data-stu-id="459c1-136">Component10CurrentFwVersion 0x04ac3970 (78395760)</span></span>
    - <span data-ttu-id="459c1-137">Component20CurrentFwVersion 0x04915a70 (76634736)</span><span class="sxs-lookup"><span data-stu-id="459c1-137">Component20CurrentFwVersion 0x04915a70 (76634736)</span></span>

>[!TIP]
><span data-ttu-id="459c1-138">イベントテキストに "ソース SurfaceDockFwUpdate のイベント ID xxxx の説明が見つかりません" と表示される場合は、これは予期されており、無視できます。</span><span class="sxs-lookup"><span data-stu-id="459c1-138">If you see "The description for Event ID xxxx from source SurfaceDockFwUpdate cannot be found" in event text, this is expected and can be ignored.</span></span>

<span data-ttu-id="459c1-139">この記事の次のセクションも参照してください。</span><span class="sxs-lookup"><span data-stu-id="459c1-139">Also see the following sections in this article:</span></span> 
  - [<span data-ttu-id="459c1-140">ファームウェア更新プログラムの完了を確認する方法</span><span class="sxs-lookup"><span data-stu-id="459c1-140">How to verify completion of firmware update</span></span>](#how-to-verify-completion-of-the-firmware-update)
  - [<span data-ttu-id="459c1-141">イベントログ</span><span class="sxs-lookup"><span data-stu-id="459c1-141">Event logging</span></span>](#event-logging)
  - [<span data-ttu-id="459c1-142">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="459c1-142">Troubleshooting tips</span></span>](#troubleshooting-tips)
  - [<span data-ttu-id="459c1-143">バージョンリファレンス</span><span class="sxs-lookup"><span data-stu-id="459c1-143">Versions reference</span></span>](#versions-reference)

## <span data-ttu-id="459c1-144">ネットワーク展開</span><span class="sxs-lookup"><span data-stu-id="459c1-144">Network deployment</span></span>

<span data-ttu-id="459c1-145">Windows Installer コマンド (Msiexec.exe) を使って、ネットワーク上の複数のデバイスに Surface Dock ファームウェア更新プログラムを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="459c1-145">You can use Windows Installer commands (Msiexec.exe) to deploy Surface Dock Firmware Update to multiple devices across your network.</span></span> <span data-ttu-id="459c1-146">Microsoft Endpoint Configuration Manager またはその他の展開ツールを使用している場合は、次の構文を入力して、インストールがサイレントモードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="459c1-146">When using Microsoft Endpoint Configuration Manager or other deployment tool, enter the following syntax to ensure the installation is silent:</span></span>

- **<span data-ttu-id="459c1-147">Msiexec.exe/i \<path to msi file\> /quiet/norestart</span><span class="sxs-lookup"><span data-stu-id="459c1-147">Msiexec.exe /i \<path to msi file\> /quiet /norestart</span></span>** 

  <span data-ttu-id="459c1-148">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="459c1-148">For example:</span></span>
  ```
  msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
  ```

  > [!NOTE]
  > <span data-ttu-id="459c1-149">既定では、ログファイルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="459c1-149">A log file is not created by default.</span></span> <span data-ttu-id="459c1-150">ログファイルを作成するには、"/l*v [path]" を追加する必要があります。例: Msiexec.exe/i \<path to msi file\> /l*v%windir%\logs\ SurfaceDockFWI "</span><span class="sxs-lookup"><span data-stu-id="459c1-150">In order to create a log file, you will need to append "/l*v [path]". For example: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"</span></span>

  <span data-ttu-id="459c1-151">詳細については、「 [コマンドラインオプション](https://docs.microsoft.com/windows/win32/msi/command-line-options) のドキュメント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="459c1-151">For more information, refer to [Command line options](https://docs.microsoft.com/windows/win32/msi/command-line-options) documentation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="459c1-152">他の方法を使用して Surface Dock を更新したままにする場合は、「 [Surface dock の更新](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="459c1-152">If you want to keep your Surface Dock updated using any other method, refer to [Update your Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) for details.</span></span>

## <span data-ttu-id="459c1-153">Intune の展開</span><span class="sxs-lookup"><span data-stu-id="459c1-153">Intune deployment</span></span>

<span data-ttu-id="459c1-154">Intune を使用して、Surface Dock ファームウェアの更新プログラムをデバイスに配布することができます。</span><span class="sxs-lookup"><span data-stu-id="459c1-154">You can use Intune to distribute Surface Dock Firmware Update to your devices.</span></span> <span data-ttu-id="459c1-155">最初に、次のドキュメントで説明されているように、MSI ファイルを、次の「 [Intune Standalone-Win32 アプリ管理](https://docs.microsoft.com/intune/apps/apps-win32-app-management)」という形式で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="459c1-155">First you will need to convert the MSI file to the .intunewin format, as described in the following documentation: [Intune Standalone - Win32 app management](https://docs.microsoft.com/intune/apps/apps-win32-app-management).</span></span>

<span data-ttu-id="459c1-156">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="459c1-156">Use the following command:</span></span>
  - **<span data-ttu-id="459c1-157">msiexec/i \<path to msi file\> /quiet/q</span><span class="sxs-lookup"><span data-stu-id="459c1-157">msiexec /i \<path to msi file\> /quiet /q</span></span>**

## <span data-ttu-id="459c1-158">ファームウェア更新プログラムの完了を確認する方法</span><span class="sxs-lookup"><span data-stu-id="459c1-158">How to verify completion of the firmware update</span></span>

<span data-ttu-id="459c1-159">Surface dock ファームウェアは、次の2つのコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-159">Surface dock firmware consists of two components:</span></span>

- <span data-ttu-id="459c1-160">**Component10:** マイクロコントローラーユニット (MCU) ファームウェア</span><span class="sxs-lookup"><span data-stu-id="459c1-160">**Component10:** Micro controller unit (MCU) firmware</span></span>
- <span data-ttu-id="459c1-161">**Component20:** ディスプレイポート (DP) ファームウェア。</span><span class="sxs-lookup"><span data-stu-id="459c1-161">**Component20:** Display port (DP) firmware.</span></span>

<span data-ttu-id="459c1-162">Surface Dock のファームウェア更新が正常に完了すると、これらのファームウェアコンポーネントの新しいレジストリキー値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-162">Successful completion of Surface Dock Firmware Update results in new registry key values for these firmware components.</span></span>

**<span data-ttu-id="459c1-163">更新を確認するには:</span><span class="sxs-lookup"><span data-stu-id="459c1-163">To verify updates:</span></span>**

1. <span data-ttu-id="459c1-164">Regedit を開き、次のレジストリパスに移動します。</span><span class="sxs-lookup"><span data-stu-id="459c1-164">Open Regedit and navigate to the following registry path:</span></span>

    - **<span data-ttu-id="459c1-165">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span><span class="sxs-lookup"><span data-stu-id="459c1-165">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span></span>**

2. <span data-ttu-id="459c1-166">**Component10CurrentFwVersion と Component20CurrentFwVersion**のレジストリキーを探します。これは、現在デバイス上にあるファームウェアを指します。</span><span class="sxs-lookup"><span data-stu-id="459c1-166">Look for the registry keys: **Component10CurrentFwVersion and Component20CurrentFwVersion**, which refer to the firmware that is currently on the device.</span></span>

   ![Surface Dock ファームウェア更新プログラムのインストールプロセス](images/regeditDock.png)

3. <span data-ttu-id="459c1-168">新しいレジストリキーの値が、このドキュメントの最後のバージョン参照で示されている更新されたレジストリキー値と一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="459c1-168">Verify the new registry key values match the updated registry key values listed in the Versions reference at the end of this document.</span></span> <span data-ttu-id="459c1-169">値が一致する場合、ファームウェアは正常に更新されました。</span><span class="sxs-lookup"><span data-stu-id="459c1-169">If the values match, the firmware was updated successfully.</span></span>

4. <span data-ttu-id="459c1-170">確認できない場合は、次のセクションのイベントログとトラブルシューティングのヒントを確認してください。</span><span class="sxs-lookup"><span data-stu-id="459c1-170">If unable to verify, review Event logging and Troubleshooting tips in the next section.</span></span>

## <span data-ttu-id="459c1-171">イベントログ</span><span class="sxs-lookup"><span data-stu-id="459c1-171">Event logging</span></span>

**<span data-ttu-id="459c1-172">表 1.</span><span class="sxs-lookup"><span data-stu-id="459c1-172">Table 1.</span></span> <span data-ttu-id="459c1-173">Surface Dock ファームウェア更新プログラムのログファイル</span><span class="sxs-lookup"><span data-stu-id="459c1-173">Log files for Surface Dock Firmware Update</span></span>**

| <span data-ttu-id="459c1-174">Log</span><span class="sxs-lookup"><span data-stu-id="459c1-174">Log</span></span>                              | <span data-ttu-id="459c1-175">Location</span><span class="sxs-lookup"><span data-stu-id="459c1-175">Location</span></span>                               | <span data-ttu-id="459c1-176">備考</span><span class="sxs-lookup"><span data-stu-id="459c1-176">Notes</span></span>                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="459c1-177">Surface Dock ファームウェア更新ログ</span><span class="sxs-lookup"><span data-stu-id="459c1-177">Surface Dock Firmware Update log</span></span> | <span data-ttu-id="459c1-178">Path を指定する必要があります (注を参照)。</span><span class="sxs-lookup"><span data-stu-id="459c1-178">Path needs to be specified (see note)</span></span> | <span data-ttu-id="459c1-179">このツールの以前のバージョンでは、Logs\Microsoft Surface Dock アップデーターにイベントが書き込まれました。</span><span class="sxs-lookup"><span data-stu-id="459c1-179">Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>                                                                                                  |
| <span data-ttu-id="459c1-180">Windows デバイスのインストールログ</span><span class="sxs-lookup"><span data-stu-id="459c1-180">Windows Device Install log</span></span>       | <span data-ttu-id="459c1-181">%windir%\inf\setupapi.dev.log</span><span class="sxs-lookup"><span data-stu-id="459c1-181">%windir%\inf\setupapi.dev.log</span></span>           | <span data-ttu-id="459c1-182">デバイスインストールログの使用について詳しくは、「[ [Setupapi.log Logging](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) ] のドキュメント」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="459c1-182">For more information about using Device Install Log, refer to [SetupAPI Logging](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) documentation.</span></span> |


**<span data-ttu-id="459c1-183">表 2.</span><span class="sxs-lookup"><span data-stu-id="459c1-183">Table 2.</span></span> <span data-ttu-id="459c1-184">Surface Dock ファームウェア更新プログラムのイベントログ Id</span><span class="sxs-lookup"><span data-stu-id="459c1-184">Event log IDs for Surface Dock Firmware Update</span></span>**<br>
<span data-ttu-id="459c1-185">イベントは、アプリケーションイベントログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-185">Events are logged in the Application Event Log.</span></span>  <span data-ttu-id="459c1-186">注: このツールの以前のバージョンでは、Logs\Microsoft Surface Dock アップデーターにイベントが書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="459c1-186">Note:  Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>

| <span data-ttu-id="459c1-187">イベント ID</span><span class="sxs-lookup"><span data-stu-id="459c1-187">Event ID</span></span> | <span data-ttu-id="459c1-188">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="459c1-188">Event type</span></span>                                                           |
| -------- | -------------------------------------------------------------------- |
| <span data-ttu-id="459c1-189">2001</span><span class="sxs-lookup"><span data-stu-id="459c1-189">2001</span></span>     | <span data-ttu-id="459c1-190">Dock ファームウェアの更新が開始されました。</span><span class="sxs-lookup"><span data-stu-id="459c1-190">Dock firmware update has started.</span></span>                                    |
| <span data-ttu-id="459c1-191">2002</span><span class="sxs-lookup"><span data-stu-id="459c1-191">2002</span></span>     | <span data-ttu-id="459c1-192">Dock が最新であることがわかっているため、dock ファームウェアの更新はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="459c1-192">Dock firmware update skipped because dock is known to be up to date.</span></span> |
| <span data-ttu-id="459c1-193">2003</span><span class="sxs-lookup"><span data-stu-id="459c1-193">2003</span></span>     | <span data-ttu-id="459c1-194">Dock ファームウェアの更新でファームウェアのバージョンを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="459c1-194">Dock firmware update failed to get firmware version.</span></span>                 |
| <span data-ttu-id="459c1-195">2004</span><span class="sxs-lookup"><span data-stu-id="459c1-195">2004</span></span>     | <span data-ttu-id="459c1-196">ファームウェアバージョンの照会。</span><span class="sxs-lookup"><span data-stu-id="459c1-196">Querying the firmware version.</span></span>                                       |
| <span data-ttu-id="459c1-197">2005</span><span class="sxs-lookup"><span data-stu-id="459c1-197">2005</span></span>     | <span data-ttu-id="459c1-198">Dock ファームウェアの更新を開始できませんでした。</span><span class="sxs-lookup"><span data-stu-id="459c1-198">Dock firmware failed to start update.</span></span>                                |
| <span data-ttu-id="459c1-199">2006</span><span class="sxs-lookup"><span data-stu-id="459c1-199">2006</span></span>     | <span data-ttu-id="459c1-200">オファー/ペイロードのペアを送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="459c1-200">Failed to send offer/payload pairs.</span></span>                                  |
| <span data-ttu-id="459c1-201">2007</span><span class="sxs-lookup"><span data-stu-id="459c1-201">2007</span></span>     | <span data-ttu-id="459c1-202">ファームウェアの更新が完了しました。</span><span class="sxs-lookup"><span data-stu-id="459c1-202">Firmware update finished.</span></span>                                            |
| <span data-ttu-id="459c1-203">2008</span><span class="sxs-lookup"><span data-stu-id="459c1-203">2008</span></span>     | <span data-ttu-id="459c1-204">Dock テレメトリを開始します。</span><span class="sxs-lookup"><span data-stu-id="459c1-204">BEGIN dock telemetry.</span></span>                                                |
| <span data-ttu-id="459c1-205">2011</span><span class="sxs-lookup"><span data-stu-id="459c1-205">2011</span></span>     | <span data-ttu-id="459c1-206">Dock のテレメトリを終了します。</span><span class="sxs-lookup"><span data-stu-id="459c1-206">END dock telemetry.</span></span>                                                  |

## <span data-ttu-id="459c1-207">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="459c1-207">Troubleshooting tips</span></span>

- <span data-ttu-id="459c1-208">Surface dock の電源を AC 電源から完全に切断して、Surface Dock をリセットします。</span><span class="sxs-lookup"><span data-stu-id="459c1-208">Completely disconnect power for Surface dock from the AC power to reset the Surface Dock.</span></span>
- <span data-ttu-id="459c1-209">Surface Dock 以外のすべての周辺機器の接続を解除します。</span><span class="sxs-lookup"><span data-stu-id="459c1-209">Disconnect all peripherals except for the Surface Dock.</span></span>
- <span data-ttu-id="459c1-210">現在の Surface Dock ファームウェア更新プログラムをアンインストールして、最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="459c1-210">Uninstall any current Surface Dock Firmware Update and then install the latest version.</span></span>
- <span data-ttu-id="459c1-211">Surface Dock が切断されていることを確認し、Dock のイーサネットポートの LED を使って、更新が監視されるまで十分な時間を確保します。</span><span class="sxs-lookup"><span data-stu-id="459c1-211">Ensure that the Surface Dock is disconnected, and then allow enough time for the update to complete as monitored via an LED in the Ethernet port of the dock.</span></span> <span data-ttu-id="459c1-212">電源から Surface Dock を取り外す前に、LED が点滅しなくなるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="459c1-212">Wait until the LED stops blinking before you unplug Surface Dock from power.</span></span>
- <span data-ttu-id="459c1-213">Surface Dock を別のデバイスに接続して、dock を更新できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="459c1-213">Connect the Surface Dock to a different device to see if it is able to update the dock.</span></span>

## <span data-ttu-id="459c1-214">バージョンリファレンス</span><span class="sxs-lookup"><span data-stu-id="459c1-214">Versions reference</span></span>

>[!NOTE]
><span data-ttu-id="459c1-215">インストールファイルは、次の名前付け形式でリリースされます。 **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ex: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) と既定では C:\Program Files\SurfaceUpdate. にインストールします。</span><span class="sxs-lookup"><span data-stu-id="459c1-215">The installation file is released with the following naming format: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ex: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) and installs by default to C:\Program Files\SurfaceUpdate.</span></span>

### <span data-ttu-id="459c1-216">バージョン1.53.139.0</span><span class="sxs-lookup"><span data-stu-id="459c1-216">Version 1.53.139.0</span></span>
*<span data-ttu-id="459c1-217">リリース日: 2020 年8月4日</span><span class="sxs-lookup"><span data-stu-id="459c1-217">Release Date: August 4, 2020</span></span>*

<span data-ttu-id="459c1-218">このバージョンの Surface Dock ファームウェア更新プログラムには、次のようなバグ修正とサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="459c1-218">This version of Surface Dock Firmware Update includes bug fixes and support for:</span></span>
- <span data-ttu-id="459c1-219">Surface Pro X を使用した Surface Dock 1 の更新。</span><span class="sxs-lookup"><span data-stu-id="459c1-219">Updating Surface Dock 1 using Surface Pro X.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="459c1-220">Surface Pro X を実行している場合は、をダウンロードします。ARM64 ビルド。</span><span class="sxs-lookup"><span data-stu-id="459c1-220">If you're running Surface Pro X, download the .ARM64 build.</span></span> <span data-ttu-id="459c1-221">その他のすべてのデバイスについては、AMD64 ビルドを使用します。</span><span class="sxs-lookup"><span data-stu-id="459c1-221">For all other devices, use the AMD64 build.</span></span> 
 


### <span data-ttu-id="459c1-222">バージョン1.42.139</span><span class="sxs-lookup"><span data-stu-id="459c1-222">Version 1.42.139</span></span> 
*<span data-ttu-id="459c1-223">リリース日:18 2019 年9月</span><span class="sxs-lookup"><span data-stu-id="459c1-223">Release Date: September 18 2019</span></span>*

<span data-ttu-id="459c1-224">このバージョンは Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI に含まれていますが、バックグラウンドでファームウェアを更新しています。</span><span class="sxs-lookup"><span data-stu-id="459c1-224">This version, contained in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, updates firmware in the background.</span></span> 
**<span data-ttu-id="459c1-225">更新されたレジストリキー値:</span><span class="sxs-lookup"><span data-stu-id="459c1-225">Updated registry key values:</span></span>**<br>

- <span data-ttu-id="459c1-226">Component10CurrentFwVersion は **4ac3970**に更新されました。</span><span class="sxs-lookup"><span data-stu-id="459c1-226">Component10CurrentFwVersion updated to **4ac3970**.</span></span>
- <span data-ttu-id="459c1-227">Component20CurrentFwVersion は、 **4a1d570**に更新されました。</span><span class="sxs-lookup"><span data-stu-id="459c1-227">Component20CurrentFwVersion updated to **4a1d570**.</span></span>

<span data-ttu-id="459c1-228">Surface Pro 7 と Surface ノート Pc 3 のサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="459c1-228">It adds support for Surface Pro 7 and Surface Laptop 3.</span></span>

## <span data-ttu-id="459c1-229">以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="459c1-229">Legacy versions</span></span>

### <span data-ttu-id="459c1-230">バージョン2.23.139.0</span><span class="sxs-lookup"><span data-stu-id="459c1-230">Version 2.23.139.0</span></span>
*<span data-ttu-id="459c1-231">リリース日: 2018 年10月10日</span><span class="sxs-lookup"><span data-stu-id="459c1-231">Release Date: 10 October 2018</span></span>*

<span data-ttu-id="459c1-232">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-232">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="459c1-233">Surface Pro 6 のサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="459c1-233">Add support for Surface Pro 6</span></span>
- <span data-ttu-id="459c1-234">Surface ラップトップのサポートを追加する2</span><span class="sxs-lookup"><span data-stu-id="459c1-234">Add support for Surface Laptop 2</span></span>


### <span data-ttu-id="459c1-235">バージョン2.22.139.0</span><span class="sxs-lookup"><span data-stu-id="459c1-235">Version 2.22.139.0</span></span>
*<span data-ttu-id="459c1-236">リリース日: 2018 年7月26日</span><span class="sxs-lookup"><span data-stu-id="459c1-236">Release Date: 26 July 2018</span></span>*

<span data-ttu-id="459c1-237">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-237">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="459c1-238">更新の信頼性を向上させる</span><span class="sxs-lookup"><span data-stu-id="459c1-238">Increase update reliability</span></span>
- <span data-ttu-id="459c1-239">Surface Go のサポートを追加する</span><span class="sxs-lookup"><span data-stu-id="459c1-239">Add support for Surface Go</span></span>

### <span data-ttu-id="459c1-240">バージョン 2.12.136.0</span><span class="sxs-lookup"><span data-stu-id="459c1-240">Version 2.12.136.0</span></span>
*<span data-ttu-id="459c1-241">リリース日: 2018 年 1 月 29 日</span><span class="sxs-lookup"><span data-stu-id="459c1-241">Release Date: 29 January 2018</span></span>*

<span data-ttu-id="459c1-242">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-242">This version of Surface Dock Updater adds support for the following:</span></span>
* <span data-ttu-id="459c1-243">Surface ドックのメイン チップセットのファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-243">Update for Surface Dock Main Chipset Firmware</span></span>
* <span data-ttu-id="459c1-244">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-244">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="459c1-245">Surface Book 2 または Surface Book で使用する場合の、外部ディスプレイの表示安定性の向上</span><span class="sxs-lookup"><span data-stu-id="459c1-245">Improved display stability for external displays when used with Surface Book or Surface Book 2</span></span>

<span data-ttu-id="459c1-246">さらに、Surface Book デバイスにこのバージョンの Surface Dock Updater をインストールした場合、以下の機能も含まれます。</span><span class="sxs-lookup"><span data-stu-id="459c1-246">Additionally, installation of this version of Surface Dock Updater on Surface Book devices includes the following:</span></span>
* <span data-ttu-id="459c1-247">Surface Book Base Firmware 更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-247">Update for Surface Book Base Firmware</span></span>
* <span data-ttu-id="459c1-248">Surface Book デバイスを対象とした機能強化による Surface ドック ファームウェア更新プログラムのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="459c1-248">Added support for Surface Dock firmware updates with improvements targeted to Surface Book devices</span></span>


### <span data-ttu-id="459c1-249">バージョン 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="459c1-249">Version 2.9.136.0</span></span>
*<span data-ttu-id="459c1-250">リリース日: 2017 年 11 月 3 日</span><span class="sxs-lookup"><span data-stu-id="459c1-250">Release date: November 3, 2017</span></span>*

<span data-ttu-id="459c1-251">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-251">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="459c1-252">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-252">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="459c1-253">パッシブ ディスプレイ ポート アダプター経由でのオーディオの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="459c1-253">Resolves an issue with audio over passive display port adapters</span></span>

### <span data-ttu-id="459c1-254">バージョン 2.1.15.0</span><span class="sxs-lookup"><span data-stu-id="459c1-254">Version 2.1.15.0</span></span>
*<span data-ttu-id="459c1-255">リリース日 : 2017 年 6 月 19 日</span><span class="sxs-lookup"><span data-stu-id="459c1-255">Release date: June 19, 2017</span></span>*

<span data-ttu-id="459c1-256">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-256">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="459c1-257">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="459c1-257">Surface Laptop</span></span>
* <span data-ttu-id="459c1-258">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="459c1-258">Surface Pro</span></span>

### <span data-ttu-id="459c1-259">バージョン 2.1.6.0</span><span class="sxs-lookup"><span data-stu-id="459c1-259">Version 2.1.6.0</span></span>
*<span data-ttu-id="459c1-260">リリース日: 2016 年 4 月 7 日</span><span class="sxs-lookup"><span data-stu-id="459c1-260">Release date: April 7, 2017</span></span>*

<span data-ttu-id="459c1-261">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-261">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="459c1-262">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-262">Update for Surface Dock DisplayPort firmware</span></span>
* <span data-ttu-id="459c1-263">Windows 10 が必要</span><span class="sxs-lookup"><span data-stu-id="459c1-263">Requires Windows 10</span></span>

### <span data-ttu-id="459c1-264">バージョン 2.0.22.0</span><span class="sxs-lookup"><span data-stu-id="459c1-264">Version 2.0.22.0</span></span>
*<span data-ttu-id="459c1-265">リリース日: 2016 年 10 月 21 日</span><span class="sxs-lookup"><span data-stu-id="459c1-265">Release date: October 21, 2016</span></span>*

<span data-ttu-id="459c1-266">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-266">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="459c1-267">Surface ドックの USB ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-267">Update for Surface Dock USB firmware</span></span>
* <span data-ttu-id="459c1-268">イーサネット、オーディオ、USB ポートの信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="459c1-268">Improved reliability of Ethernet, audio, and USB ports</span></span>

### <span data-ttu-id="459c1-269">バージョン 1.0.8.0</span><span class="sxs-lookup"><span data-stu-id="459c1-269">Version 1.0.8.0</span></span>
*<span data-ttu-id="459c1-270">リリース日: 2016 年 4 月 26 日</span><span class="sxs-lookup"><span data-stu-id="459c1-270">Release date: April 26, 2016</span></span>*

<span data-ttu-id="459c1-271">このバージョンの Surface Dock Updater では、次の機能のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="459c1-271">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="459c1-272">Surface ドックのメイン チップセットのファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-272">Update for Surface Dock Main Chipset firmware</span></span>
* <span data-ttu-id="459c1-273">Surface ドックの DisplayPort ファームウェア更新プログラム</span><span class="sxs-lookup"><span data-stu-id="459c1-273">Update for Surface Dock DisplayPort firmware</span></span>

