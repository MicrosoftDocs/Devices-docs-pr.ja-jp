---
title: Surface Hub の回復ツールの使用
description: Surface Hub 回復ツールを使って SSD を再イメージ化する方法について説明します。
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 12/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: a9ebab6848efa706609a39b0eb99fa42df2156bf
ms.sourcegitcommit: ce7ad475b776a78ba215e77111ea5371afeb4f28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "11237343"
---
# <span data-ttu-id="e4b55-104">Surface Hub の回復ツールの使用</span><span class="sxs-lookup"><span data-stu-id="e4b55-104">Using the Surface Hub Recovery Tool</span></span>

<span data-ttu-id="e4b55-105">[Microsoft Surface Hub 回復](https://www.microsoft.com/download/details.aspx?id=52210)ツールは、サポートを呼び出したり SSD を交換したりすることなく、Windows 10 デスクトップ デバイスを使って Surface Hub Solid State Drive (SSD) のイメージを再イメージ化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-105">The [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) helps you re-image your Surface Hub Solid State Drive (SSD) using a Windows 10 desktop device, without calling support or replacing the SSD.</span></span> <span data-ttu-id="e4b55-106">このツールを使用すると、不明な管理者パスワードを持つ SSD、ブート エラー、クラウド回復を完了できなかった SSD、またはオペレーティング システムの古いバージョンを持つデバイスのイメージを再作成できます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-106">With this tool, you can reimage an SSD that has an unknown Administrator password, boot errors, was unable to complete a cloud recovery, or for a device that has an older version of the operating system.</span></span> <span data-ttu-id="e4b55-107">物理的に破損した SSD は修正されません。</span><span class="sxs-lookup"><span data-stu-id="e4b55-107">The tool will not fix physically damaged SSDs.</span></span>

<span data-ttu-id="e4b55-108">回復ツールを使って Surface Hub SSD を再イメージ化するには、Surface Hub から SSD を取り外し、ドライブを USB から SATA ケーブルに接続し、回復ツールがインストールされているデスクトップ PC にケーブルを接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-108">To re-image the Surface Hub SSD using the Recovery Tool, you'll need to remove the SSD from the Surface Hub, connect the drive to the USB-to-SATA cable, and then connect the cable to the desktop PC on which the Recovery Tool is installed.</span></span> <span data-ttu-id="e4b55-109">Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。</span><span class="sxs-lookup"><span data-stu-id="e4b55-109">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4b55-110">デバイスをスリープ状態にしたり、イメージ ファイルのダウンロードを中断したりしない。</span><span class="sxs-lookup"><span data-stu-id="e4b55-110">Do not let the device go to sleep or interrupt the download of the image file.</span></span>

<span data-ttu-id="e4b55-111">ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。</span><span class="sxs-lookup"><span data-stu-id="e4b55-111">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="e4b55-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="e4b55-112">Prerequisites</span></span>

### <span data-ttu-id="e4b55-113">Mandatory</span><span class="sxs-lookup"><span data-stu-id="e4b55-113">Mandatory</span></span>

- <span data-ttu-id="e4b55-114">64 ビット バージョンの Windows 10 バージョン 1607 以上を実行しているホスト PC。</span><span class="sxs-lookup"><span data-stu-id="e4b55-114">Host PC running 64-bit version of Windows 10, version 1607 or higher.</span></span>
- <span data-ttu-id="e4b55-115">インターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="e4b55-115">Internet access</span></span>
- <span data-ttu-id="e4b55-116">USB 2.0 以上のポートを開く</span><span class="sxs-lookup"><span data-stu-id="e4b55-116">Open USB 2.0 or greater port</span></span>
- <span data-ttu-id="e4b55-117">USB から SATA ケーブル</span><span class="sxs-lookup"><span data-stu-id="e4b55-117">USB-to-SATA cable</span></span>
- <span data-ttu-id="e4b55-118">ホスト コンピューター上の 10 GB の空きディスク領域</span><span class="sxs-lookup"><span data-stu-id="e4b55-118">10 GB of free disk space on the host computer</span></span>
- <span data-ttu-id="e4b55-119">代替としてサポートによって提供される Surface Hub または SSD に付属する SSD。</span><span class="sxs-lookup"><span data-stu-id="e4b55-119">SSDs shipped with Surface Hub or a SSD provided by Support as a replacement.</span></span> <span data-ttu-id="e4b55-120">Microsoft から提供されていない SSD はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e4b55-120">SSDs not supplied by Microsoft are not supported.</span></span>

### <span data-ttu-id="e4b55-121">推奨</span><span class="sxs-lookup"><span data-stu-id="e4b55-121">Recommended</span></span>

- <span data-ttu-id="e4b55-122">高速インターネット接続</span><span class="sxs-lookup"><span data-stu-id="e4b55-122">High-speed Internet connection</span></span>
- <span data-ttu-id="e4b55-123">USB 3.0 ポートを開く</span><span class="sxs-lookup"><span data-stu-id="e4b55-123">Open USB 3.0 port</span></span>
- <span data-ttu-id="e4b55-124">USB 3.0 以上の USB- SATA ケーブル</span><span class="sxs-lookup"><span data-stu-id="e4b55-124">USB 3.0 or higher USB-to-SATA cable</span></span>
- <span data-ttu-id="e4b55-125">イメージング ツールは、次のケーブルの作成とモデルでテストされました。</span><span class="sxs-lookup"><span data-stu-id="e4b55-125">The imaging tool was tested with the following make and model of cables:</span></span>
    - <span data-ttu-id="e4b55-126">Startech USB312SAT3CB</span><span class="sxs-lookup"><span data-stu-id="e4b55-126">Startech USB312SAT3CB</span></span>
    - <span data-ttu-id="e4b55-127">サギット RCUC16001</span><span class="sxs-lookup"><span data-stu-id="e4b55-127">Rosewill RCUC16001</span></span>
    - <span data-ttu-id="e4b55-128">Ugreen 20231</span><span class="sxs-lookup"><span data-stu-id="e4b55-128">Ugreen 20231</span></span>

## <span data-ttu-id="e4b55-129">Surface Hub 回復ツールのダウンロード</span><span class="sxs-lookup"><span data-stu-id="e4b55-129">Download Surface Hub Recovery Tool</span></span>

<span data-ttu-id="e4b55-130">Surface Hub 回復ツールは[、Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)からファイル名の下にダウンロード\*\*SurfaceHub_Recovery_v2.0.139.0.msi。 \*\*</span><span class="sxs-lookup"><span data-stu-id="e4b55-130">Surface Hub Recovery Tool is available for download from [Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)  under the file name **SurfaceHub_Recovery_v2.0.139.0.msi**.</span></span>

<span data-ttu-id="e4b55-131">ダウンロードを開始するには、[ダウンロード] を **クリック**し、一覧から **SurfaceHub_Recovery_v2.0.139.0.msi** を選択して、[次へ] をクリック **します**。</span><span class="sxs-lookup"><span data-stu-id="e4b55-131">To start the download, click **Download**, choose **SurfaceHub_Recovery_v2.0.139.0.msi** from the list, and click **Next**.</span></span> <span data-ttu-id="e4b55-132">ポップアップから、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-132">From the pop-up, choose one of the following:</span></span>

- <span data-ttu-id="e4b55-133">[ **ファイル名を指定** して実行] をクリックして、インストールをすぐに開始します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-133">Click **Run** to start the installation immediately.</span></span>
- <span data-ttu-id="e4b55-134">[ **保存]** をクリックして、後でインストールするためにダウンロードをコンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e4b55-134">Click **Save** to copy the download to your computer for later installation.</span></span>

<span data-ttu-id="e4b55-135">ホスト PC に Surface Hub 回復ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e4b55-135">Install Surface Hub Recovery Tool on the host PC.</span></span>

## <span data-ttu-id="e4b55-136">Surface Hub 回復ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="e4b55-136">Run Surface Hub Recovery Tool</span></span>

1. <span data-ttu-id="e4b55-137">ホスト PC で、[スタート\*\*\*\*] ボタンを選択し、左側のアルファベット順の一覧をスクロールして、回復ツールのショートカットを選択します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-137">On the host PC, select the **Start** button, scroll through the alphabetical list on the left, and select the recovery tool shortcut.</span></span>

    ![Microsoft Surface Hub 回復ツールのショートカット](images/shrt-shortcut.png)

2. <span data-ttu-id="e4b55-139">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b55-139">Click **Start**.</span></span>

    ![回復ツールの [スタート] ボタン](images/shrt-start.png)


3. <span data-ttu-id="e4b55-141">[ガイダンス] **ウィンドウで** 、[次へ] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="e4b55-141">In the **Guidance** window, click **Next**.</span></span>

    ![コンピューターをスリープ状態にしない](images/shrt-guidance.png)

4. <span data-ttu-id="e4b55-143">[イメージの選択] ウィンドウで **、RS2**または後続の**20H2**をクリックし、[続行] を選択して、[イメージのダウンロード]**を選択します。** \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e4b55-143">In the Select image window, click either **RS2** or its successor **20H2**, select **Continue,** and then select **Download image.**</span></span>

     <span data-ttu-id="e4b55-144">![回復ツール イメージの選択 ](images/shrt-select-image.png) ![ 回復ツールのダウンロード イメージ](images/shrt-download-image.png)</span><span class="sxs-lookup"><span data-stu-id="e4b55-144">![Recovery Tool Select image](images/shrt-select-image.png) ![Recovery Tool Download image](images/shrt-download-image.png)</span></span>

5. <span data-ttu-id="e4b55-145">回復イメージをダウンロードする時間は、インターネット接続の速度に依存します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-145">Time to download the recovery image is dependent on internet connection speeds.</span></span> <span data-ttu-id="e4b55-146">企業の平均接続では、8 GB の画像ファイルをダウンロードするために最大 1 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-146">On an average corporate connection, it can take up to an hour to download the 8GB image file.</span></span>

    ![イメージのダウンロード](images/shrt-download.png)



5. <span data-ttu-id="e4b55-148">ダウンロードが完了すると、SSD ドライブを接続するように指示されます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-148">When the download is complete, the tool instructs you to connect an SSD drive.</span></span> <span data-ttu-id="e4b55-149">ツールが接続されているドライブを見つからない場合は、使用されているケーブルが SSD の名前を Windows に報告していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-149">If the tool is unable to locate the attached drive, there is a good chance that the cable being used is not reporting the name of the SSD to Windows.</span></span>  <span data-ttu-id="e4b55-150">イメージング ツールは、続行する前にドライブの名前を "LITEON L CH-128V2S USB デバイス" として見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-150">The imaging tool must find the name of the drive as "LITEON L CH-128V2S USB Device" before it can continue.</span></span>  <span data-ttu-id="e4b55-151">Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。</span><span class="sxs-lookup"><span data-stu-id="e4b55-151">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

    ![SSD の接続](images/shrt-drive.png)

6. <span data-ttu-id="e4b55-153">ドライブが認識されると、[スタート] を **クリック** して再イメージング プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-153">When the drive is recognized, click **Start** to begin the re-imaging process.</span></span> <span data-ttu-id="e4b55-154">ドライブ上のすべてのデータが消去されるという警告で **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b55-154">On the warning that all data on the drive will be erased, click **OK**.</span></span>



    <span data-ttu-id="e4b55-155">ドライブにシステム イメージを適用する前に、SSD が再パーティション化され、フォーマットされます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-155">Prior to applying the system image to the drive, the SSD is repartitioned and formatted.</span></span> <span data-ttu-id="e4b55-156">システム バイナリのコピーには約 30 分かかりますが、USB バスの速度、使用しているケーブル、システムにインストールされているウイルス対策ソフトウェアによっては、時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-156">Copying the system binaries will take approximately 30 minutes, but can take longer depending on the speed of your USB bus, the cable being used, or antivirus software installed on your system.</span></span>



## <span data-ttu-id="e4b55-157">トラブルシューティングと一般的な問題</span><span class="sxs-lookup"><span data-stu-id="e4b55-157">Troubleshooting and common problems</span></span>

<span data-ttu-id="e4b55-158">問題</span><span class="sxs-lookup"><span data-stu-id="e4b55-158">Issue</span></span> | <span data-ttu-id="e4b55-159">備考</span><span class="sxs-lookup"><span data-stu-id="e4b55-159">Notes</span></span>
--- | ---
<span data-ttu-id="e4b55-160">SSD のイメージ作成に失敗する</span><span class="sxs-lookup"><span data-stu-id="e4b55-160">The tool fails to image the SSD</span></span> | <span data-ttu-id="e4b55-161">出荷時の SSD とテスト済みケーブルのいずれかを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e4b55-161">Make sure you are using a factory-supplied SSD and one of the tested cables.</span></span>
<span data-ttu-id="e4b55-162">再作プロセスが停止/フリーズしたと表示される</span><span class="sxs-lookup"><span data-stu-id="e4b55-162">The reimaging process appears halted/frozen</span></span> | <span data-ttu-id="e4b55-163">SSD に影響を与え、Surface Hub 回復ツールを閉じて再起動しても安全です。</span><span class="sxs-lookup"><span data-stu-id="e4b55-163">It is safe to close and restart the Surface Hub Recovery Tool with no ill effect to the SSD.</span></span>
<span data-ttu-id="e4b55-164">ドライブがツールによって認識されない</span><span class="sxs-lookup"><span data-stu-id="e4b55-164">The drive isn’t recognized by the tool</span></span> | <span data-ttu-id="e4b55-165">Surface Hub SSD が"LITEON L CH-128V2S USB デバイスLite-Onドライブとして列挙されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-165">Verify that the Surface Hub SSD is enumerated as a Lite-On drive, "LITEON L CH-128V2S USB Device".</span></span>  <span data-ttu-id="e4b55-166">ドライブが別の名前付きデバイスとして認識される場合、現在のケーブルは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="e4b55-166">If the drive is recognized as another named device, your current cable isn’t compatible.</span></span> <span data-ttu-id="e4b55-167">別のケーブルまたは上記のテスト済みケーブルのいずれかを試してください。</span><span class="sxs-lookup"><span data-stu-id="e4b55-167">Try another cable or one of the tested cable listed above.</span></span>
<span data-ttu-id="e4b55-168">エラー: -2147024809</span><span class="sxs-lookup"><span data-stu-id="e4b55-168">Error: -2147024809</span></span> | <span data-ttu-id="e4b55-169">ディスク マネージャーを開き、Surface Hub ドライブ上のパーティションを削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-169">Open Disk Manager and remove the partitions on the Surface Hub drive.</span></span>  <span data-ttu-id="e4b55-170">ドライブを切断し、ホスト コンピューターに再接続します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-170">Disconnect and reconnect the drive to the host machine.</span></span> <span data-ttu-id="e4b55-171">イメージング ツールを再度再起動します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-171">Restart the imaging tool again.</span></span>

<span data-ttu-id="e4b55-172">ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。</span><span class="sxs-lookup"><span data-stu-id="e4b55-172">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="e4b55-173">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="e4b55-173">Version history</span></span>

### <span data-ttu-id="e4b55-174">バージョン v2.0.139.0</span><span class="sxs-lookup"><span data-stu-id="e4b55-174">Version v2.0.139.0</span></span>

*<span data-ttu-id="e4b55-175">リリース日: 2020 年 12 月 18 日</span><span class="sxs-lookup"><span data-stu-id="e4b55-175">Release date: December 18, 2020</span></span>*<br>
<span data-ttu-id="e4b55-176">このバージョンの Surface Hub 回復ツールでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="e4b55-176">This version of Surface Hub Recovery Tool adds support for the following:</span></span>
- <span data-ttu-id="e4b55-177">Windows 10 Team 2020 Update (20H2) をサポートする更新プログラム</span><span class="sxs-lookup"><span data-stu-id="e4b55-177">Update to support Windows 10 Team 2020 Update (20H2)</span></span>
- <span data-ttu-id="e4b55-178">ユーザー エクスペリエンスの向上</span><span class="sxs-lookup"><span data-stu-id="e4b55-178">User experience improvements</span></span>
- <span data-ttu-id="e4b55-179">アーキテクチャの変更</span><span class="sxs-lookup"><span data-stu-id="e4b55-179">Architectural changes</span></span>
- <span data-ttu-id="e4b55-180">テレメトリの追加</span><span class="sxs-lookup"><span data-stu-id="e4b55-180">Telemetry additions</span></span>

