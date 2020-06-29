---
title: Surface Hub の回復ツールの使用
description: Surface Hub の回復ツールを使用して、SSD を再イメージする方法について説明します。
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub の管理
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/22/2018
ms.localizationpriority: medium
ms.openlocfilehash: 1988a6ed59525d7dc77872e532247dbc50f01bdf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836897"
---
# <span data-ttu-id="94f2f-104">Surface Hub の回復ツールの使用</span><span class="sxs-lookup"><span data-stu-id="94f2f-104">Using the Surface Hub Recovery Tool</span></span>

<span data-ttu-id="94f2f-105">[Microsoft Surface hub の回復ツール](https://www.microsoft.com/download/details.aspx?id=52210)では、Windows 10 デスクトップデバイスを使用して Surface Hub のソリッドステートドライブ (ssd) を再イメージすることができます。これには、サポートに問い合わせるか、ssd を交換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-105">The [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) helps you re-image your Surface Hub Solid State Drive (SSD) using a Windows 10 desktop device, without calling support or replacing the SSD.</span></span> <span data-ttu-id="94f2f-106">このツールを使用すると、管理者パスワードが不明な SSD、ブートエラー、クラウドの回復を完了できなかったデバイス、または以前のバージョンのオペレーティングシステムを搭載しているデバイスの SSD を再作成することができます。</span><span class="sxs-lookup"><span data-stu-id="94f2f-106">With this tool, you can reimage an SSD that has an unknown Administrator password, boot errors, was unable to complete a cloud recovery, or for a device that has an older version of the operating system.</span></span> <span data-ttu-id="94f2f-107">このツールでは、物理的に破損した Ssd は解決されません。</span><span class="sxs-lookup"><span data-stu-id="94f2f-107">The tool will not fix physically damaged SSDs.</span></span>

<span data-ttu-id="94f2f-108">回復ツールを使用して Surface Hub SSD を再イメージするには、Surface Hub から SSD を取り外す必要があります。ドライブを USB 対 SATA ケーブルに接続して、回復ツールがインストールされているデスクトップ PC にケーブルを接続します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-108">To re-image the Surface Hub SSD using the Recovery Tool, you'll need to remove the SSD from the Surface Hub, connect the drive to the USB-to-SATA cable, and then connect the cable to the desktop PC on which the Recovery Tool is installed.</span></span> <span data-ttu-id="94f2f-109">Surface Hub から既存のドライブを削除する方法について詳しくは、「 [Surface HUB SSD の交換](surface-hub-ssd-replacement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-109">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94f2f-110">デバイスがスリープ状態になったり、イメージファイルのダウンロードが中断されたりしないようにします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-110">Do not let the device go to sleep or interrupt the download of the image file.</span></span>

<span data-ttu-id="94f2f-111">このツールでドライブの再作成に失敗した場合は、 [Surface Hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-111">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="94f2f-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="94f2f-112">Prerequisites</span></span>

### <span data-ttu-id="94f2f-113">Mandatory</span><span class="sxs-lookup"><span data-stu-id="94f2f-113">Mandatory</span></span>

- <span data-ttu-id="94f2f-114">64ビット版の Windows 10 バージョン1607以降を実行しているホスト PC。</span><span class="sxs-lookup"><span data-stu-id="94f2f-114">Host PC running 64-bit version of Windows 10, version 1607 or higher.</span></span>
- <span data-ttu-id="94f2f-115">インターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="94f2f-115">Internet access</span></span>
- <span data-ttu-id="94f2f-116">USB 2.0 以上のポートを開く</span><span class="sxs-lookup"><span data-stu-id="94f2f-116">Open USB 2.0 or greater port</span></span>
- <span data-ttu-id="94f2f-117">USB 対 SATA ケーブル</span><span class="sxs-lookup"><span data-stu-id="94f2f-117">USB-to-SATA cable</span></span>
- <span data-ttu-id="94f2f-118">ホストコンピューター上の 10 GB の空きディスク領域</span><span class="sxs-lookup"><span data-stu-id="94f2f-118">10 GB of free disk space on the host computer</span></span>
- <span data-ttu-id="94f2f-119">SSDs は Surface Hub に同梱されています。また、交換としてサポートによって提供される SSD。</span><span class="sxs-lookup"><span data-stu-id="94f2f-119">SSDs shipped with Surface Hub or a SSD provided by Support as a replacement.</span></span> <span data-ttu-id="94f2f-120">Microsoft によって提供されていない Ssd はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="94f2f-120">SSDs not supplied by Microsoft are not supported.</span></span>

### <span data-ttu-id="94f2f-121">推奨</span><span class="sxs-lookup"><span data-stu-id="94f2f-121">Recommended</span></span>

- <span data-ttu-id="94f2f-122">高速インターネット接続</span><span class="sxs-lookup"><span data-stu-id="94f2f-122">High-speed Internet connection</span></span>
- <span data-ttu-id="94f2f-123">USB 3.0 ポートを開く</span><span class="sxs-lookup"><span data-stu-id="94f2f-123">Open USB 3.0 port</span></span>
- <span data-ttu-id="94f2f-124">Usb 3.0 以上の USB ケーブル</span><span class="sxs-lookup"><span data-stu-id="94f2f-124">USB 3.0 or higher USB-to-SATA cable</span></span>
- <span data-ttu-id="94f2f-125">イメージングツールは、次のようなケーブルのメーカーとモデルを使ってテストされています。</span><span class="sxs-lookup"><span data-stu-id="94f2f-125">The imaging tool was tested with the following make and model of cables:</span></span>
    - <span data-ttu-id="94f2f-126">Startech USB312SAT3CB</span><span class="sxs-lookup"><span data-stu-id="94f2f-126">Startech USB312SAT3CB</span></span>
    - <span data-ttu-id="94f2f-127">Rosewill</span><span class="sxs-lookup"><span data-stu-id="94f2f-127">Rosewill RCUC16001</span></span>
    - <span data-ttu-id="94f2f-128">Ugreen 20231</span><span class="sxs-lookup"><span data-stu-id="94f2f-128">Ugreen 20231</span></span>

## <span data-ttu-id="94f2f-129">Surface Hub 回復ツールをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="94f2f-129">Download Surface Hub Recovery Tool</span></span>

<span data-ttu-id="94f2f-130">Surface hub 回復ツールは、[ファイル名**SurfaceHub_Recovery_v1.14.137.0.msi**の下[にある surface hub ツール](https://www.microsoft.com/download/details.aspx?id=52210)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="94f2f-130">Surface Hub Recovery Tool is available for download from [Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)  under the file name **SurfaceHub_Recovery_v1.14.137.0.msi**.</span></span>

<span data-ttu-id="94f2f-131">ダウンロードを開始するには、[**ダウンロード**] をクリックし、一覧から [ **SurfaceHub_Recovery_v1.14.137.0.msi** ] を選択して、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-131">To start the download, click **Download**, choose **SurfaceHub_Recovery_v1.14.137.0.msi** from the list, and click **Next**.</span></span> <span data-ttu-id="94f2f-132">ポップアップで、次のいずれかのオプションを選びます。</span><span class="sxs-lookup"><span data-stu-id="94f2f-132">From the pop-up, choose one of the following:</span></span>

- <span data-ttu-id="94f2f-133">[**実行**] をクリックして、すぐにインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-133">Click **Run** to start the installation immediately.</span></span>
- <span data-ttu-id="94f2f-134">[**保存**] をクリックして、後でインストールするためにダウンロードしたファイルをコンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-134">Click **Save** to copy the download to your computer for later installation.</span></span>

<span data-ttu-id="94f2f-135">Surface Hub 回復ツールをホスト PC にインストールします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-135">Install Surface Hub Recovery Tool on the host PC.</span></span>

## <span data-ttu-id="94f2f-136">Surface Hub 回復ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="94f2f-136">Run Surface Hub Recovery Tool</span></span>

1. <span data-ttu-id="94f2f-137">ホスト PC で、[**スタート**] ボタンを選択し、左側のアルファベット順の一覧をスクロールして、回復ツールのショートカットを選択します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-137">On the host PC, select the **Start** button, scroll through the alphabetical list on the left, and select the recovery tool shortcut.</span></span>

    ![Microsoft Surface Hub 回復ツールのショートカット](images/shrt-shortcut.png)

2. <span data-ttu-id="94f2f-139">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-139">Click **Start**.</span></span>

    ![回復ツールの [スタート] ボタン](images/shrt-start.png)

3. <span data-ttu-id="94f2f-141">[**ガイダンス**] ウィンドウで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-141">In the **Guidance** window, click **Next**.</span></span>

    ![マシンがスリープガイダンスに移動しないようにする](images/shrt-guidance.png)

4. <span data-ttu-id="94f2f-143">画像をダウンロードするには、[**はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-143">click **Yes** to download the image.</span></span> <span data-ttu-id="94f2f-144">回復イメージのダウンロードにかかる時間は、インターネット接続の速度によって異なります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-144">Time to download the recovery image is dependent on internet connection speeds.</span></span> <span data-ttu-id="94f2f-145">企業の平均的な接続では、8GB の画像ファイルをダウンロードするまでに最長で1時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-145">On an average corporate connection, it can take up to an hour to download the 8GB image file.</span></span>

    ![画像をダウンロードしますか?](images/shrt-download.png)

5. <span data-ttu-id="94f2f-147">ダウンロードが完了すると、SSD ドライブへの接続を指示するツールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94f2f-147">When the download is complete, the tool instructs you to connect an SSD drive.</span></span> <span data-ttu-id="94f2f-148">このツールで接続されているドライブが見つからない場合は、使用されているケーブルで SSD の名前が Windows に報告されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-148">If the tool is unable to locate the attached drive, there is a good chance that the cable being used is not reporting the name of the SSD to Windows.</span></span>  <span data-ttu-id="94f2f-149">イメージングツールは、続行する前に、ドライブの名前を "LITEON L CH-128V2S USB デバイス" として探す必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-149">The imaging tool must find the name of the drive as "LITEON L CH-128V2S USB Device" before it can continue.</span></span>  <span data-ttu-id="94f2f-150">Surface Hub から既存のドライブを削除する方法について詳しくは、「 [Surface HUB SSD の交換](surface-hub-ssd-replacement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-150">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

    ![SSD の接続](images/shrt-drive.png)

6. <span data-ttu-id="94f2f-152">ドライブが認識されたら、[**開始**] をクリックして再イメージングプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-152">When the drive is recognized, click **Start** to begin the re-imaging process.</span></span> <span data-ttu-id="94f2f-153">ドライブ上のすべてのデータが消去されるという警告が表示されたら、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f2f-153">On the warning that all data on the drive will be erased, click **OK**.</span></span>

    ![SSD の再イメージングを開始する](images/shrt-drive-start.png)

    <span data-ttu-id="94f2f-155">システムイメージをドライブに適用する前に、SSD は repartitioned および書式設定されています。</span><span class="sxs-lookup"><span data-stu-id="94f2f-155">Prior to applying the system image to the drive, the SSD is repartitioned and formatted.</span></span> <span data-ttu-id="94f2f-156">システムバイナリのコピーには約30分かかりますが、USB バスの速度、使用されているケーブル、またはシステムにインストールされているウイルス対策ソフトウェアによって、より長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="94f2f-156">Copying the system binaries will take approximately 30 minutes, but can take longer depending on the speed of your USB bus, the cable being used, or antivirus software installed on your system.</span></span>

    ![コピーが完了しました](images/shrt-done.png)

    ![イメージの完成](images/shrt-complete.png)

## <span data-ttu-id="94f2f-159">トラブルシューティングと一般的な問題</span><span class="sxs-lookup"><span data-stu-id="94f2f-159">Troubleshooting and common problems</span></span>

<span data-ttu-id="94f2f-160">問題</span><span class="sxs-lookup"><span data-stu-id="94f2f-160">Issue</span></span> | <span data-ttu-id="94f2f-161">備考</span><span class="sxs-lookup"><span data-stu-id="94f2f-161">Notes</span></span>
--- | ---
<span data-ttu-id="94f2f-162">このツールでは、SSD の画像に失敗します</span><span class="sxs-lookup"><span data-stu-id="94f2f-162">The tool fails to image the SSD</span></span> | <span data-ttu-id="94f2f-163">工場で供給されている SSD とテストしたケーブルのいずれかを使用していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-163">Make sure you are using a factory-supplied SSD and one of the tested cables.</span></span>
<span data-ttu-id="94f2f-164">再イメージのプロセスが停止またはフリーズする</span><span class="sxs-lookup"><span data-stu-id="94f2f-164">The reimaging process appears halted/frozen</span></span> | <span data-ttu-id="94f2f-165">SSD に悪影響を及ぼすことなく Surface Hub の回復ツールを終了して再起動することは安全です。</span><span class="sxs-lookup"><span data-stu-id="94f2f-165">It is safe to close and restart the Surface Hub Recovery Tool with no ill effect to the SSD.</span></span>
<span data-ttu-id="94f2f-166">ドライブがツールによって認識されない</span><span class="sxs-lookup"><span data-stu-id="94f2f-166">The drive isn’t recognized by the tool</span></span> | <span data-ttu-id="94f2f-167">Surface Hub SSD がライトツードライブとして列挙されていることを確認します ("LITEON L CH-128V2S USB デバイス")。</span><span class="sxs-lookup"><span data-stu-id="94f2f-167">Verify that the Surface Hub SSD is enumerated as a Lite-On drive, "LITEON L CH-128V2S USB Device".</span></span>  <span data-ttu-id="94f2f-168">ドライブが別の名前付きデバイスとして認識された場合、現在のケーブルには互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="94f2f-168">If the drive is recognized as another named device, your current cable isn’t compatible.</span></span> <span data-ttu-id="94f2f-169">別のケーブルを試すか、上に記載されているテスト済みケーブルのいずれかを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-169">Try another cable or one of the tested cable listed above.</span></span>
<span data-ttu-id="94f2f-170">エラー:-2147024809</span><span class="sxs-lookup"><span data-stu-id="94f2f-170">Error: -2147024809</span></span> | <span data-ttu-id="94f2f-171">ディスクマネージャーを開き、Surface Hub ドライブのパーティションを削除します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-171">Open Disk Manager and remove the partitions on the Surface Hub drive.</span></span>  <span data-ttu-id="94f2f-172">ドライブを切断し、ホストコンピューターに再接続します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-172">Disconnect and reconnect the drive to the host machine.</span></span> <span data-ttu-id="94f2f-173">もう一度イメージングツールを再起動します。</span><span class="sxs-lookup"><span data-stu-id="94f2f-173">Restart the imaging tool again.</span></span>

<span data-ttu-id="94f2f-174">このツールでドライブの再作成に失敗した場合は、 [Surface Hub のサポート](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="94f2f-174">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>
