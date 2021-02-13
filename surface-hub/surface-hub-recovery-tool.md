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
ms.date: 02/11/2020
ms.localizationpriority: medium
ms.openlocfilehash: 34a05eeabd284e0ad43317577b8e7ff9348ffe21
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327341"
---
# <span data-ttu-id="b97db-104">Surface Hub の回復ツールの使用</span><span class="sxs-lookup"><span data-stu-id="b97db-104">Using the Surface Hub Recovery Tool</span></span>

<span data-ttu-id="b97db-105">[Microsoft Surface Hub 回復](https://www.microsoft.com/download/details.aspx?id=52210)ツールは、サポートを呼び出したり SSD を交換したりすることなく、Windows 10 デスクトップ デバイスを使って Surface Hub Solid State Drive (SSD) のイメージを再イメージ化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b97db-105">The [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) helps you re-image your Surface Hub Solid State Drive (SSD) using a Windows 10 desktop device, without calling support or replacing the SSD.</span></span> <span data-ttu-id="b97db-106">このツールを使用すると、不明な管理者パスワードを持つ SSD、ブート エラー、クラウド回復を完了できなかった SSD、またはオペレーティング システムの古いバージョンを持つデバイスのイメージを再作成できます。</span><span class="sxs-lookup"><span data-stu-id="b97db-106">With this tool, you can reimage an SSD that has an unknown Administrator password, boot errors, was unable to complete a cloud recovery, or for a device that has an older version of the operating system.</span></span> <span data-ttu-id="b97db-107">物理的に破損した SSD は修正されません。</span><span class="sxs-lookup"><span data-stu-id="b97db-107">The tool will not fix physically damaged SSDs.</span></span>

<span data-ttu-id="b97db-108">回復ツールを使って Surface Hub SSD を再イメージ化するには、Surface Hub から SSD を取り外し、ドライブを USB から SATA ケーブルに接続し、回復ツールがインストールされているデスクトップ PC にケーブルを接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-108">To re-image the Surface Hub SSD using the Recovery Tool, you'll need to remove the SSD from the Surface Hub, connect the drive to the USB-to-SATA cable, and then connect the cable to the desktop PC on which the Recovery Tool is installed.</span></span> <span data-ttu-id="b97db-109">Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。</span><span class="sxs-lookup"><span data-stu-id="b97db-109">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b97db-110">デバイスをスリープ状態にしたり、イメージ ファイルのダウンロードを中断したりしない。</span><span class="sxs-lookup"><span data-stu-id="b97db-110">Do not let the device go to sleep or interrupt the download of the image file.</span></span>

<span data-ttu-id="b97db-111">ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。</span><span class="sxs-lookup"><span data-stu-id="b97db-111">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="b97db-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="b97db-112">Prerequisites</span></span>

### <span data-ttu-id="b97db-113">Mandatory</span><span class="sxs-lookup"><span data-stu-id="b97db-113">Mandatory</span></span>

- <span data-ttu-id="b97db-114">64 ビット バージョンの Windows 10 バージョン 1607 以上を実行しているホスト PC。</span><span class="sxs-lookup"><span data-stu-id="b97db-114">Host PC running 64-bit version of Windows 10, version 1607 or higher.</span></span>
- <span data-ttu-id="b97db-115">インターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="b97db-115">Internet access</span></span>
- <span data-ttu-id="b97db-116">USB 2.0 以上のポートを開く</span><span class="sxs-lookup"><span data-stu-id="b97db-116">Open USB 2.0 or greater port</span></span>
- <span data-ttu-id="b97db-117">USB から SATA ケーブル</span><span class="sxs-lookup"><span data-stu-id="b97db-117">USB-to-SATA cable</span></span>
- <span data-ttu-id="b97db-118">ホスト コンピューター上の 10 GB の空きディスク領域</span><span class="sxs-lookup"><span data-stu-id="b97db-118">10 GB of free disk space on the host computer</span></span>
- <span data-ttu-id="b97db-119">代替としてサポートによって提供される Surface Hub または SSD に付属する SSD。</span><span class="sxs-lookup"><span data-stu-id="b97db-119">SSDs shipped with Surface Hub or a SSD provided by Support as a replacement.</span></span> <span data-ttu-id="b97db-120">Microsoft から提供されていない SSD はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b97db-120">SSDs not supplied by Microsoft are not supported.</span></span>

### <span data-ttu-id="b97db-121">推奨</span><span class="sxs-lookup"><span data-stu-id="b97db-121">Recommended</span></span>

- <span data-ttu-id="b97db-122">高速インターネット接続</span><span class="sxs-lookup"><span data-stu-id="b97db-122">High-speed Internet connection</span></span>
- <span data-ttu-id="b97db-123">USB 3.0 ポートを開く</span><span class="sxs-lookup"><span data-stu-id="b97db-123">Open USB 3.0 port</span></span>
- <span data-ttu-id="b97db-124">USB 3.0 以上の USB- SATA ケーブル</span><span class="sxs-lookup"><span data-stu-id="b97db-124">USB 3.0 or higher USB-to-SATA cable</span></span>
- <span data-ttu-id="b97db-125">イメージング ツールは、次のケーブルの作成とモデルでテストされました。</span><span class="sxs-lookup"><span data-stu-id="b97db-125">The imaging tool was tested with the following make and model of cables:</span></span>
    - <span data-ttu-id="b97db-126">Startech USB312SAT3CB</span><span class="sxs-lookup"><span data-stu-id="b97db-126">Startech USB312SAT3CB</span></span>
    - <span data-ttu-id="b97db-127">サギス RCUC16001</span><span class="sxs-lookup"><span data-stu-id="b97db-127">Rosewill RCUC16001</span></span>
    - <span data-ttu-id="b97db-128">Ugreen 20231</span><span class="sxs-lookup"><span data-stu-id="b97db-128">Ugreen 20231</span></span>

## <span data-ttu-id="b97db-129">Surface Hub 回復ツールのダウンロード</span><span class="sxs-lookup"><span data-stu-id="b97db-129">Download Surface Hub Recovery Tool</span></span>

<span data-ttu-id="b97db-130">Surface Hub 回復ツールは[、Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)からファイル名の下でダウンロード\*\*SurfaceHub_Recovery_v2.7.139.0.msi。 \*\*</span><span class="sxs-lookup"><span data-stu-id="b97db-130">Surface Hub Recovery Tool is available for download from [Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)  under the file name **SurfaceHub_Recovery_v2.7.139.0.msi**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b97db-131">2021 年 2 月 11 日にリリースされたこのバージョンは、機能しなくなった以前のビルドに置き換わるものになります。</span><span class="sxs-lookup"><span data-stu-id="b97db-131">This version, released Feb 11, 2021, replaces the earlier build, which is no longer functional.</span></span> <span data-ttu-id="b97db-132">このツールを以前にダウンロードした場合は、現在のバージョンを破棄して使用してください。</span><span class="sxs-lookup"><span data-stu-id="b97db-132">If you downloaded this tool previously, please discard and use the current version.</span></span>

<span data-ttu-id="b97db-133">ダウンロードを開始するには、[ダウンロード] を **クリック**し、一覧から **SurfaceHub_Recovery_v2.7.139.0.msi**  を選択して、[次へ] をクリック **します**。</span><span class="sxs-lookup"><span data-stu-id="b97db-133">To start the download, click **Download**, choose **SurfaceHub_Recovery_v2.7.139.0.msi**  from the list, and click **Next**.</span></span> <span data-ttu-id="b97db-134">ポップアップから、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="b97db-134">From the pop-up, choose one of the following:</span></span>

- <span data-ttu-id="b97db-135">[ **ファイル名を指定** して実行] をクリックして、インストールをすぐに開始します。</span><span class="sxs-lookup"><span data-stu-id="b97db-135">Click **Run** to start the installation immediately.</span></span>
- <span data-ttu-id="b97db-136">[ **保存]** をクリックして、後でインストールするためにダウンロードをコンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b97db-136">Click **Save** to copy the download to your computer for later installation.</span></span>

<span data-ttu-id="b97db-137">ホスト PC に Surface Hub 回復ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b97db-137">Install Surface Hub Recovery Tool on the host PC.</span></span>

## <span data-ttu-id="b97db-138">Surface Hub 回復ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="b97db-138">Run Surface Hub Recovery Tool</span></span>

1. <span data-ttu-id="b97db-139">ホスト PC で、[スタート\*\*\*\*] ボタンを選択し、左側のアルファベット順の一覧をスクロールして、回復ツールのショートカットを選択します。</span><span class="sxs-lookup"><span data-stu-id="b97db-139">On the host PC, select the **Start** button, scroll through the alphabetical list on the left, and select the recovery tool shortcut.</span></span>

    ![Microsoft Surface Hub 回復ツールのショートカット](images/shrt-shortcut.png)

2. <span data-ttu-id="b97db-141">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b97db-141">Click **Start**.</span></span>

    ![回復ツールの [スタート] ボタン](images/shrt-start.png)


3. <span data-ttu-id="b97db-143">[ガイダンス] **ウィンドウで** 、[次へ] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b97db-143">In the **Guidance** window, click **Next**.</span></span>

    ![コンピューターをスリープ状態にしない](images/shrt-guidance.png)

4. <span data-ttu-id="b97db-145">[イメージの選択] ウィンドウで **、RS2**または後続の**20H2**をクリックし、[続行] を選択して、[イメージのダウンロード]**を選択します。** \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b97db-145">In the Select image window, click either **RS2** or its successor **20H2**, select **Continue,** and then select **Download image.**</span></span>

     <span data-ttu-id="b97db-146">![回復ツール イメージの選択 ](images/shrt-select-image.png) ![ 回復ツールのダウンロード イメージ](images/shrt-download-image.png)</span><span class="sxs-lookup"><span data-stu-id="b97db-146">![Recovery Tool Select image](images/shrt-select-image.png) ![Recovery Tool Download image](images/shrt-download-image.png)</span></span>

5. <span data-ttu-id="b97db-147">回復イメージをダウンロードする時間は、インターネット接続の速度に依存します。</span><span class="sxs-lookup"><span data-stu-id="b97db-147">Time to download the recovery image is dependent on internet connection speeds.</span></span> <span data-ttu-id="b97db-148">平均的な企業接続では、8 GB の画像ファイルをダウンロードするために最大 1 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-148">On an average corporate connection, it can take up to an hour to download the 8GB image file.</span></span>

    ![イメージのダウンロード](images/shrt-download.png)



5. <span data-ttu-id="b97db-150">ダウンロードが完了すると、SSD ドライブを接続するように指示されます。</span><span class="sxs-lookup"><span data-stu-id="b97db-150">When the download is complete, the tool instructs you to connect an SSD drive.</span></span> <span data-ttu-id="b97db-151">ツールが接続されているドライブを見つからない場合は、使用されているケーブルが SSD の名前を Windows に報告していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-151">If the tool is unable to locate the attached drive, there is a good chance that the cable being used is not reporting the name of the SSD to Windows.</span></span>  <span data-ttu-id="b97db-152">イメージング ツールは、続行する前にドライブの名前を "LITEON L CH-128V2S USB デバイス" として見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-152">The imaging tool must find the name of the drive as "LITEON L CH-128V2S USB Device" before it can continue.</span></span>  <span data-ttu-id="b97db-153">Surface Hub から既存のドライブを削除する方法について詳しくは、Surface Hub SSD の交換に関する [ページをご覧ください](surface-hub-ssd-replacement.md)。</span><span class="sxs-lookup"><span data-stu-id="b97db-153">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

    ![SSD の接続](images/shrt-drive.png)

6. <span data-ttu-id="b97db-155">ドライブが認識されると、[スタート] を **クリック** して再イメージング プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b97db-155">When the drive is recognized, click **Start** to begin the re-imaging process.</span></span> <span data-ttu-id="b97db-156">ドライブ上のすべてのデータが消去されるという警告で **、[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b97db-156">On the warning that all data on the drive will be erased, click **OK**.</span></span>



    <span data-ttu-id="b97db-157">ドライブにシステム イメージを適用する前に、SSD が再パーティション化され、フォーマットされます。</span><span class="sxs-lookup"><span data-stu-id="b97db-157">Prior to applying the system image to the drive, the SSD is repartitioned and formatted.</span></span> <span data-ttu-id="b97db-158">システム バイナリのコピーには約 30 分かかりますが、USB バスの速度、使用しているケーブル、システムにインストールされているウイルス対策ソフトウェアによっては、時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-158">Copying the system binaries will take approximately 30 minutes, but can take longer depending on the speed of your USB bus, the cable being used, or antivirus software installed on your system.</span></span>



## <span data-ttu-id="b97db-159">トラブルシューティングと一般的な問題</span><span class="sxs-lookup"><span data-stu-id="b97db-159">Troubleshooting and common problems</span></span>

<span data-ttu-id="b97db-160">問題</span><span class="sxs-lookup"><span data-stu-id="b97db-160">Issue</span></span> | <span data-ttu-id="b97db-161">備考</span><span class="sxs-lookup"><span data-stu-id="b97db-161">Notes</span></span>
--- | ---
<span data-ttu-id="b97db-162">SSD のイメージ作成に失敗する</span><span class="sxs-lookup"><span data-stu-id="b97db-162">The tool fails to image the SSD</span></span> | <span data-ttu-id="b97db-163">出荷時の SSD とテスト済みケーブルのいずれかを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b97db-163">Make sure you are using a factory-supplied SSD and one of the tested cables.</span></span>
<span data-ttu-id="b97db-164">再作プロセスが停止/固定された状態で表示される</span><span class="sxs-lookup"><span data-stu-id="b97db-164">The reimaging process appears halted/frozen</span></span> | <span data-ttu-id="b97db-165">SSD に影響を与え、Surface Hub 回復ツールを閉じて再起動しても安全です。</span><span class="sxs-lookup"><span data-stu-id="b97db-165">It is safe to close and restart the Surface Hub Recovery Tool with no ill effect to the SSD.</span></span>
<span data-ttu-id="b97db-166">ドライブがツールによって認識されない</span><span class="sxs-lookup"><span data-stu-id="b97db-166">The drive isn’t recognized by the tool</span></span> | <span data-ttu-id="b97db-167">Surface Hub SSD が"LITEON L CH-128V2S USB デバイスLite-Onドライブとして列挙されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b97db-167">Verify that the Surface Hub SSD is enumerated as a Lite-On drive, "LITEON L CH-128V2S USB Device".</span></span>  <span data-ttu-id="b97db-168">ドライブが別の名前付きデバイスとして認識される場合、現在のケーブルは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="b97db-168">If the drive is recognized as another named device, your current cable isn’t compatible.</span></span> <span data-ttu-id="b97db-169">別のケーブルまたは上記のテスト済みケーブルのいずれかを試してください。</span><span class="sxs-lookup"><span data-stu-id="b97db-169">Try another cable or one of the tested cable listed above.</span></span>
<span data-ttu-id="b97db-170">エラー: -2147024809</span><span class="sxs-lookup"><span data-stu-id="b97db-170">Error: -2147024809</span></span> | <span data-ttu-id="b97db-171">ディスク マネージャーを開き、Surface Hub ドライブ上のパーティションを削除します。</span><span class="sxs-lookup"><span data-stu-id="b97db-171">Open Disk Manager and remove the partitions on the Surface Hub drive.</span></span>  <span data-ttu-id="b97db-172">ドライブを切断し、ホスト コンピューターに再接続します。</span><span class="sxs-lookup"><span data-stu-id="b97db-172">Disconnect and reconnect the drive to the host machine.</span></span> <span data-ttu-id="b97db-173">イメージング ツールを再度再起動します。</span><span class="sxs-lookup"><span data-stu-id="b97db-173">Restart the imaging tool again.</span></span>

<span data-ttu-id="b97db-174">ドライブの再インストールに失敗した場合は、Surface Hub サポートにお問 [い合わせください](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)。</span><span class="sxs-lookup"><span data-stu-id="b97db-174">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="b97db-175">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="b97db-175">Version history</span></span>


### <span data-ttu-id="b97db-176">バージョン v2.7.139.0</span><span class="sxs-lookup"><span data-stu-id="b97db-176">Version v2.7.139.0</span></span>

*<span data-ttu-id="b97db-177">リリース日: 2021 年 2 月 11 日</span><span class="sxs-lookup"><span data-stu-id="b97db-177">Release date: February 11, 2021</span></span>*<br>
<span data-ttu-id="b97db-178">このバージョンの Surface Hub 回復ツールでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="b97db-178">This version of Surface Hub Recovery Tool adds support for the following:</span></span>

- <span data-ttu-id="b97db-179">セキュリティに関する更新</span><span class="sxs-lookup"><span data-stu-id="b97db-179">Security update</span></span>


### <span data-ttu-id="b97db-180">バージョン v2.0.139.0</span><span class="sxs-lookup"><span data-stu-id="b97db-180">Version v2.0.139.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b97db-181">このバージョンは機能しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b97db-181">This version is no longer functional.</span></span> <span data-ttu-id="b97db-182">上記の現在のバージョンをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b97db-182">Please download the current version, listed above.</span></span> 

*<span data-ttu-id="b97db-183">リリース日: 2020 年 12 月 18 日</span><span class="sxs-lookup"><span data-stu-id="b97db-183">Release date: December 18, 2020</span></span>*<br>
<span data-ttu-id="b97db-184">このバージョンの Surface Hub 回復ツールでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="b97db-184">This version of Surface Hub Recovery Tool adds support for the following:</span></span>
- <span data-ttu-id="b97db-185">Windows 10 Team 2020 Update (20H2) をサポートする更新プログラム</span><span class="sxs-lookup"><span data-stu-id="b97db-185">Update to support Windows 10 Team 2020 Update (20H2)</span></span>
- <span data-ttu-id="b97db-186">ユーザー エクスペリエンスの向上</span><span class="sxs-lookup"><span data-stu-id="b97db-186">User experience improvements</span></span>
- <span data-ttu-id="b97db-187">アーキテクチャの変更</span><span class="sxs-lookup"><span data-stu-id="b97db-187">Architectural changes</span></span>
- <span data-ttu-id="b97db-188">利用統計情報の追加</span><span class="sxs-lookup"><span data-stu-id="b97db-188">Telemetry additions</span></span>

