---
title: Surface Hub SSD の交換
ms.reviewer: ''
manager: laurawi
description: Surface Hub でソリッドステートドライブを置き換える方法について説明します。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 17e6018478b608b34c47ce0acd602deb70035474
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835126"
---
# <span data-ttu-id="32d5a-103">Surface Hub SSD の交換</span><span class="sxs-lookup"><span data-stu-id="32d5a-103">Surface Hub SSD replacement</span></span>

<span data-ttu-id="32d5a-104">Surface hub[回復ツール](surface-hub-recovery-tool.md)を使用してイメージを再作成したり、交換したドライブを送信したりしたために、surface hub からソリッドステートドライブ (SSD) を削除しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="32d5a-104">You might need to remove the solid state drive (SSD) from your Surface Hub so that you can reimage it using the [Surface Hub Recovery Tool](surface-hub-recovery-tool.md) or because you've been sent a replacement drive.</span></span> <span data-ttu-id="32d5a-105">Windows update の失敗、BitLocker の問題、リセットエラー、ハードウェア障害などのオペレーティングシステムが起動不可能になった場合は、SSD を再作成します。</span><span class="sxs-lookup"><span data-stu-id="32d5a-105">You would reimage your SSD when the operating system is no longer bootable, such as from a Windows update failure, BitLocker issues, reset failure, or hardware failure.</span></span> 


>[!WARNING]
><span data-ttu-id="32d5a-106">AC スイッチで Surface Hub がオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="32d5a-106">Make sure the Surface Hub is turned off at the AC switch.</span></span>

1. <span data-ttu-id="32d5a-107">下の図のような場所にある Surface Hub の背面にある SSD のコンパートメントドアを見つけます。</span><span class="sxs-lookup"><span data-stu-id="32d5a-107">Locate the SSD compartment door on the rear, upper portion of the Surface Hub in the locations illustrated below.</span></span> <span data-ttu-id="32d5a-108">ドアは、開いている換気スロットがないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="32d5a-108">The door is identifiable as it doesn't have open ventilation slots.</span></span>

    ![SSD のコンパートメントドア](images/ssd-location.png)

    *<span data-ttu-id="32d5a-110">Surface Hub ハードドライブの場所</span><span class="sxs-lookup"><span data-stu-id="32d5a-110">Surface Hub hard drive locations</span></span>*

2. <span data-ttu-id="32d5a-111">ハードドライブコンパートメントドアの [ロッキング] タブを見つけます。</span><span class="sxs-lookup"><span data-stu-id="32d5a-111">Locate the locking tab on the hard drive compartment door.</span></span> <span data-ttu-id="32d5a-112">Surface Hub 55 では、[ロッキング] タブはドアの左側にあります。</span><span class="sxs-lookup"><span data-stu-id="32d5a-112">On the Surface Hub 55, the locking tab will be located on the left-hand side of the door.</span></span> <span data-ttu-id="32d5a-113">Surface Hub 84 では、図に示すように、右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="32d5a-113">On the Surface Hub 84, it will be on the right-hand side as shown in the illustration.</span></span>

    ![SSD のコンパートメントのロックタブ](images/ssd-lock-tab.png)

    *<span data-ttu-id="32d5a-115">ハードドライブコンパートメントドアのロックタブ</span><span class="sxs-lookup"><span data-stu-id="32d5a-115">Locking tab on hard drive compartment door</span></span>*

3. <span data-ttu-id="32d5a-116">[コンパートメント] ドアを開いて、ハードドライブにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="32d5a-116">Lift open the compartment door to access the hard drive.</span></span>

    ![離し](images/ssd-lift-door.png)

    *<span data-ttu-id="32d5a-118">コンパートメントドアを持ち上げる</span><span class="sxs-lookup"><span data-stu-id="32d5a-118">Lift compartment door</span></span>*

4. <span data-ttu-id="32d5a-119">[プル] タブを探します。これは背面カバーの下に表示されています。</span><span class="sxs-lookup"><span data-stu-id="32d5a-119">Locate the pull tab, which may be partially hidden under the rear cover.</span></span> <span data-ttu-id="32d5a-120">タブを引いて、コンパートメントからハードドライブを取り出します。</span><span class="sxs-lookup"><span data-stu-id="32d5a-120">Pull on the tab to eject the hard drive from the compartment.</span></span>

    ![プル](images/ssd-pull-tab.png)

    *<span data-ttu-id="32d5a-122">[プル] タブ</span><span class="sxs-lookup"><span data-stu-id="32d5a-122">Pull tab</span></span>*

5. <span data-ttu-id="32d5a-123">カチッという音が聞こえるまで、代わりのドライブをスライドします。</span><span class="sxs-lookup"><span data-stu-id="32d5a-123">Slide the replacement drive into place until you hear it click.</span></span>

    ![ドライブのスライド](images/ssd-click.png)
    
    *<span data-ttu-id="32d5a-125">代替ドライブの位置をスライドする</span><span class="sxs-lookup"><span data-stu-id="32d5a-125">Slide replacement drive into place</span></span>*

6. <span data-ttu-id="32d5a-126">コンパートメントドアを閉じます。</span><span class="sxs-lookup"><span data-stu-id="32d5a-126">Close the compartment door.</span></span>

7. <span data-ttu-id="32d5a-127">Surface Hub にパワーを適用します。</span><span class="sxs-lookup"><span data-stu-id="32d5a-127">Apply power to the Surface Hub.</span></span>
