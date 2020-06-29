---
title: Surface Hub での BitLocker のクラウド回復の使用方法
description: Surface Hub での BitLocker のクラウド回復の使用方法
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: アクセシビリティの設定, 設定アプリ, 簡単操作
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7912f9d1bab2ba625995c56d6d7da4e6b2d3df37
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834870"
---
# <span data-ttu-id="bf31c-104">まとめ</span><span class="sxs-lookup"><span data-stu-id="bf31c-104">Summary</span></span>

<span data-ttu-id="bf31c-105">この記事では、Surface Hub デバイスで BitLocker によって予期せずメッセージが表示される場合に、クラウド回復機能を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-105">This article describes how to use the cloud recovery function if you are unexpectedly prompted by BitLocker on a Surface Hub device.</span></span>

> [!NOTE]
> <span data-ttu-id="bf31c-106">BitLocker 回復キーが利用できない場合にのみ、次の手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf31c-106">You should follow these steps only if a BitLocker recovery key isn't available.</span></span>

> [!WARNING]
> * <span data-ttu-id="bf31c-107">この回復プロセスでは、内部ドライブの内容を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-107">This recovery process deletes the contents of the internal drive.</span></span> <span data-ttu-id="bf31c-108">プロセスが失敗すると、内部ドライブは完全に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bf31c-108">If the process fails, the internal drive will become completely unusable.</span></span> <span data-ttu-id="bf31c-109">この問題が発生した場合は、解決するために Microsoft のサービスリクエストをログに記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf31c-109">If this occurs, you will have to log a service request with Microsoft for a resolution.</span></span>
> * <span data-ttu-id="bf31c-110">回復プロセスが完了すると、デバイスは出荷時の設定にリセットされ、Box でのエクスペリエンスの状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="bf31c-110">After the recovery process is complete, the device will be reset to the factory settings and returned to its Out of Box Experience state.</span></span>
> * <span data-ttu-id="bf31c-111">回復後、Surface Hub を完全に再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf31c-111">After the recovery, the Surface Hub must be completely reconfigured.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf31c-112">このプロセスでは、プロキシまたはその他の認証方法を使用しないオープンインターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="bf31c-112">This process requires an open Internet connection that does not use a proxy or other authentication method.</span></span>

## <span data-ttu-id="bf31c-113">クラウドの回復プロセス</span><span class="sxs-lookup"><span data-stu-id="bf31c-113">Cloud recovery process</span></span>

<span data-ttu-id="bf31c-114">クラウドの回復を実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-114">To perform a cloud recovery, follow these steps:</span></span>

1. <span data-ttu-id="bf31c-115">**さらに回復オプションを使用するには、Esc キーを押し**ます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-115">Select **Press Esc for more recovery options**.</span></span>

   ![Escape のスクリーンショット](images/01-escape.png)

1. <span data-ttu-id="bf31c-117">[**このドライブをスキップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-117">Select **Skip this drive**.</span></span>

   ![このドライブをスキップするスクリーンショット](images/02-skip-this-drive.png)

1. <span data-ttu-id="bf31c-119">[**クラウドからの回復**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-119">Select **Recover from the cloud**.</span></span>

   ![クラウドからの回復のスクリーンショット](images/03-recover-from-cloud.png)

1. <span data-ttu-id="bf31c-121">[**はい]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-121">Select **Yes**.</span></span>

   ![[はい] のスクリーンショット](images/04-yes.png)

1. <span data-ttu-id="bf31c-123">[**再インストール**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-123">Select **Reinstall**.</span></span>

   ![再インストールのスクリーンショット](images/05a-reinstall.png)

   ![ダウンロードのスクリーンショット](images/05b-downloading.png)

1. <span data-ttu-id="bf31c-126">クラウドの回復プロセスが完了したら、**ボックスの外のエクスペリエンス**を使用して、再構成を開始します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-126">After the cloud recovery process is complete, start the reconfiguration by using the **Out of Box Experience**.</span></span>

   ![ボックスの外側にあるスクリーンショット](images/06-out-of-box.png)

## <span data-ttu-id="bf31c-128">"問題が発生しました" というエラーメッセージ</span><span class="sxs-lookup"><span data-stu-id="bf31c-128">"Something went Wrong" error message</span></span>

<span data-ttu-id="bf31c-129">通常、このエラーは、回復のダウンロード中に発生したネットワークの問題が原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-129">This error is usually caused by network issues that occur during the recovery download.</span></span> <span data-ttu-id="bf31c-130">この問題が発生した場合は、ハブを再起動できないため、ハブをオフにしないでください。</span><span class="sxs-lookup"><span data-stu-id="bf31c-130">When this issue occurs, don't turn off the Hub because you won't be able to restart it.</span></span> <span data-ttu-id="bf31c-131">このエラーメッセージが表示された場合は、「クラウドから回復する」の手順に戻り、回復処理を再実行します。</span><span class="sxs-lookup"><span data-stu-id="bf31c-131">If you receive this error message, return to the "Recover from the cloud" step, and then restart the recovery process.</span></span>

1. <span data-ttu-id="bf31c-132">[**キャンセル**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-132">Select **Cancel**.</span></span>

   ![[キャンセル] のスクリーンショット](images/07-cancel.png)

1. <span data-ttu-id="bf31c-134">[**トラブルシューティング**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-134">Select **Troubleshoot**.</span></span>

   ![トラブルシューティングのスクリーンショット](images/08-troubleshoot.png)

1. <span data-ttu-id="bf31c-136">[**クラウドからの回復**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bf31c-136">Select **Recover from the cloud**.</span></span>

   ![クラウドからの回復のスクリーンショット](images/09-recover-from-cloud2.png)

1. <span data-ttu-id="bf31c-138">**有線ネットワークが見つからない**というエラーが発生する場合は、[**キャンセル**] を選択し、Surface Hub が有線ネットワークを再検出できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bf31c-138">If the **Wired network isn't found** error occurs, select **Cancel**, and then let the Surface Hub rediscover the wired network.</span></span>

   ![ワイヤードネットワークのスクリーンショットが見つからない](images/10-cancel.png)