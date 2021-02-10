---
title: Surface のMicrosoft 起動ツールを構成する
description: この記事では、商用環境で管理対象デバイス用に Microsoft 起動ツールを構成する方法を要約します。
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 8/12/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 1254f28ce65894c8d43d89188f22ed161cd72098
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326297"
---
# <span data-ttu-id="d687e-103">Surface のMicrosoft 起動ツールを構成する</span><span class="sxs-lookup"><span data-stu-id="d687e-103">Configure Microsoft Launcher for Surface Duo</span></span>

<span data-ttu-id="d687e-104">SurfaceDac は Microsoft 起動ツール for enterprise をサポートしています。この Android アプリケーションを使用すると、ユーザーは携帯電話をカスタマイズし、移動中も整理を続け、モバイル デバイスと PC 間で予定表、タスク、メモなどとシームレスに同期できます。</span><span class="sxs-lookup"><span data-stu-id="d687e-104">Surface Duo supports Microsoft Launcher for enterprise, an Android application that lets users personalize their phone, stay organized on the go, and seamlessly sync their Calendar, Task, Notes and more between mobile devices and their PCs.</span></span> <span data-ttu-id="d687e-105">実際、Surface Launcher は 2 画面でカスタマイズされた Microsoft 起動ツール のバージョンで、組織の完全に管理されたデバイスで推奨されるエクスペリエンスを定義するために調整できます。また、ユーザーがこれらの企業のデバイスでエクスペリエンスをカスタマイズできるオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="d687e-105">In fact, the Surface Duo launcher is a two-screen customized version of  Microsoft Launcher that you can adjust to define the preferred experiences on the fully managed devices for your organization as well as allow users some options to personalize their experiences on these corporate devices.</span></span> <span data-ttu-id="d687e-106">たとえば、ホーム画面にピン留めするアプリを選択したり、ブランドの壁紙を展開したり、必要に応じて検索バーを有効にしながら検索バーを非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="d687e-106">For example, you can select which apps you want pinned to the home screen, deploy a branded wallpaper, or hide a search bar while allowing users to enable the Search bar if desired.</span></span>

## <span data-ttu-id="d687e-107">Microsoft 起動ツール設定</span><span class="sxs-lookup"><span data-stu-id="d687e-107">Microsoft Launcher settings</span></span>

<span data-ttu-id="d687e-108">Microsoft 起動ツールには、エンド ユーザー エクスペリエンスをカスタマイズするための次の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d687e-108">Microsoft Launcher includes the following settings to customize the end user experience:</span></span>


- <span data-ttu-id="d687e-109">ホーム画面アプリの注文ユーザーの変更が許可される</span><span class="sxs-lookup"><span data-stu-id="d687e-109">Home Screen App Order User Change Allowed</span></span>
- <span data-ttu-id="d687e-110">グリッド サイズの設定</span><span class="sxs-lookup"><span data-stu-id="d687e-110">Set Grid Size</span></span>
- <span data-ttu-id="d687e-111">デバイスの壁紙を設定する</span><span class="sxs-lookup"><span data-stu-id="d687e-111">Set Device Wallpaper</span></span>
- <span data-ttu-id="d687e-112">デバイスの壁紙のユーザー変更を許可する設定</span><span class="sxs-lookup"><span data-stu-id="d687e-112">Set Device Wallpaper User Change Allowed</span></span>
- <span data-ttu-id="d687e-113">フィードの有効化</span><span class="sxs-lookup"><span data-stu-id="d687e-113">Feed Enable</span></span>
- <span data-ttu-id="d687e-114">フィードを有効にするユーザーの変更を許可する</span><span class="sxs-lookup"><span data-stu-id="d687e-114">Feed Enable User Change Allowed</span></span>
- <span data-ttu-id="d687e-115">検索バーの配置</span><span class="sxs-lookup"><span data-stu-id="d687e-115">Search Bar Placement</span></span>
- <span data-ttu-id="d687e-116">検索バーの配置ユーザーの変更を許可する</span><span class="sxs-lookup"><span data-stu-id="d687e-116">Search Bar Placement User Change Allowed</span></span>
- <span data-ttu-id="d687e-117">ドック モード</span><span class="sxs-lookup"><span data-stu-id="d687e-117">Dock Mode</span></span>
- <span data-ttu-id="d687e-118">ドック モードのユーザー変更が許可される</span><span class="sxs-lookup"><span data-stu-id="d687e-118">Dock Mode User Change Allowed</span></span>

<span data-ttu-id="d687e-119">各設定の詳細については [、「Intune](https://docs.microsoft.com/mem/intune/apps/configure-microsoft-launcher)で Microsoft 起動ツール for Android Enterprise を構成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d687e-119">For full details of each setting, refer to [Configure Microsoft Launcher for Android Enterprise with Intune](https://docs.microsoft.com/mem/intune/apps/configure-microsoft-launcher).</span></span>

<span data-ttu-id="d687e-120">展開手順については、「Intune で Android Enterprise [Fully Managed Devices](https://techcommunity.microsoft.com/t5/intune-customer-success/how-to-setup-microsoft-launcher-on-android-enterprise-fully/ba-p/1482134)で Microsoft 起動ツール をセットアップする方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d687e-120">For step by step deployment instructions, refer to [How to Setup Microsoft Launcher on Android Enterprise Fully Managed Devices with Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/how-to-setup-microsoft-launcher-on-android-enterprise-fully/ba-p/1482134).</span></span>
