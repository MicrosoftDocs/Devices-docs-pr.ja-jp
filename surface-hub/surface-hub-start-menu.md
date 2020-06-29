---
title: Surface Hub のスタート メニューの構成
description: MDM を使用して、Surface Hub のスタート メニューをカスタマイズできます。
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.date: 08/15/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: c5b6a083d543649eab899d2fea36327d08f8bc29
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834517"
---
# <span data-ttu-id="39fd9-103">Surface Hub のスタート メニューの構成</span><span class="sxs-lookup"><span data-stu-id="39fd9-103">Configure Surface Hub Start menu</span></span>

<span data-ttu-id="39fd9-104">[Windows 10 の 2018 年 1 月 17日 の更新プログラム](https://support.microsoft.com/help/4057144) (ビルド 15063.877) により、Surface Hub デバイスでスタート メニューをカスタマイズできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39fd9-104">The [January 17, 2018 update to Windows 10](https://support.microsoft.com/help/4057144) (build 15063.877) enables customized Start menus on Surface Hub devices.</span></span> <span data-ttu-id="39fd9-105">カスタマイズしたスタート メニューのレイアウトを適用するには、モバイル デバイス管理 (MDM) を使用します。</span><span class="sxs-lookup"><span data-stu-id="39fd9-105">You apply the customized Start menu layout using mobile device management (MDM).</span></span>

<span data-ttu-id="39fd9-106">カスタマイズしたスタート メニューのレイアウトを Surface Hub に適用すると、ユーザーはスタート画面でアプリをピン留めしたり、ピン留めを外したり、アンインストールしたりすることはできなません。</span><span class="sxs-lookup"><span data-stu-id="39fd9-106">When you apply a customized Start menu layout to Surface Hub, users cannot pin, unpin, or uninstall apps from Start.</span></span> 

## <span data-ttu-id="39fd9-107">Surface Hub にカスタマイズしたスタート メニューを適用する方法</span><span class="sxs-lookup"><span data-stu-id="39fd9-107">How to apply a customized Start menu to Surface Hub</span></span>

<span data-ttu-id="39fd9-108">カスタマイズしたスタート メニューは、スタート画面のレイアウトの XML ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="39fd9-108">The customized Start menu is defined in a Start layout XML file.</span></span> <span data-ttu-id="39fd9-109">スタート画面のレイアウト XML ファイルを作成するには、2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="39fd9-109">You have two options for creating your Start layout XML file:</span></span>

- <span data-ttu-id="39fd9-110">[既定の Surface Hub のスタート画面の XML](#default) を編集する</span><span class="sxs-lookup"><span data-stu-id="39fd9-110">Edit the [default Surface Hub Start XML](#default)</span></span>

    <span data-ttu-id="39fd9-111">- または -</span><span class="sxs-lookup"><span data-stu-id="39fd9-111">-or-</span></span>

- <span data-ttu-id="39fd9-112">デスクトップで目的のスタート メニューを構成し (Surface Hub で利用できるアプリのみをピン留めし)、[そのレイアウトをエクスポート](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout)する</span><span class="sxs-lookup"><span data-stu-id="39fd9-112">Configure the desired Start menu on a desktop (pinning only apps that are available on Surface Hub), and then [export the layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout).</span></span>

>[!TIP]
><span data-ttu-id="39fd9-113">デスクトップのスタート メニューに Web リンクを含むタイルを追加するには、Microsoft Edge でそのリンクに移動し、右上隅にある [`...`] を選択して、**[このページをスタートにピン留めする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="39fd9-113">To add a tile with a web link to your desktop start menu, go to the link in Microsoft Edge, select `...` in the top right corner, and select **Pin this page to Start**.</span></span> <span data-ttu-id="39fd9-114">リンクが XML でどのように表示されるかを示す例については、[Microsoft Edge のリンクを含むスタート画面のレイアウト](#edge)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39fd9-114">See [a Start layout that includes a Microsoft Edge link](#edge) for an example of how links will appear in the XML.</span></span>

<span data-ttu-id="39fd9-115">既定の XML またはエクスポートしたレイアウトを編集するには、[スタート画面のレイアウトの XML](https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop) について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="39fd9-115">To edit the default XML or the exported layout, familiarize yourself with the [Start layout XML](https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop).</span></span> <span data-ttu-id="39fd9-116">[デスクトップと Surface Hub ではスタート画面のレイアウトの相違点](#differences)がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="39fd9-116">There are a few [differences between Start layout on a deskop and a Surface Hub.](#differences)</span></span>

<span data-ttu-id="39fd9-117">スタート画面のレイアウトの XML でスタート メニューが定義されている場合、[レイアウトを適用するための MDM ポリシーを作成します](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management#a-href-idbkmk-domaingpodeploymentacreate-a-policy-for-your-customized-start-layout)。</span><span class="sxs-lookup"><span data-stu-id="39fd9-117">When you have your Start menu defined in a Start layout XML, [create an MDM policy to apply the layout.](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management#a-href-idbkmk-domaingpodeploymentacreate-a-policy-for-your-customized-start-layout)</span></span>

<span id="differences" />
## <span data-ttu-id="39fd9-118">Surface Hub とデスクトップのスタートメニューの相違点</span><span class="sxs-lookup"><span data-stu-id="39fd9-118">Differences between Surface Hub and desktop Start menu</span></span>

<span data-ttu-id="39fd9-119">Surface Hub と Windows 10 デスクトップでは、スタート メニューのカスタマイズにいくつかの大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="39fd9-119">There are a few key differences between Start menu customization for Surface Hub and a Windows 10 desktop:</span></span>

- <span data-ttu-id="39fd9-120">**DesktopApplicationTile** https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop#startdesktopapplicationtile) Windows デスクトップアプリケーション (Win32) は Surface Hub ではサポートされていないため、desktopapplicationtile は使用できません (スタートレイアウト XML では使用できません)。</span><span class="sxs-lookup"><span data-stu-id="39fd9-120">You cannot use **DesktopApplicationTile** (https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop#startdesktopapplicationtile) in your Start layout XML because Windows desktop applications (Win32) are not supported on Surface Hub.</span></span>
- <span data-ttu-id="39fd9-121">スタート画面のレイアウトの XML を使用して、Surface Hub のタスク バーやようこそ画面を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="39fd9-121">You cannot use the Start layout XML to configure the taskbar or the Welcome screen for Surface Hub.</span></span>  
- <span data-ttu-id="39fd9-122">Surface Hub がサポートしているのは最大 6 列 (6 個の 1 x 1 タイル) ですが、`GroupCellWidth=8` を定義する**必要があります**。ただし、Surface Hub で表示されるのは列 0 ～ 5 のタイルのみで、列 6 および 7 は表示されません。</span><span class="sxs-lookup"><span data-stu-id="39fd9-122">Surface Hub supports a maximum of 6 columns (6 1x1 tiles), however, you **must** define `GroupCellWidth=8` even though Surface Hub will only display tiles in columns 0-5, not columns 6 and 7.</span></span>
- <span data-ttu-id="39fd9-123">Surface Hub は最大 6 行 (6 個の 1 x 1 タイル) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="39fd9-123">Surface Hub supports a maximum 6 rows (6 1x1 tiles)</span></span>
- `SecondaryTile`<span data-ttu-id="39fd9-124"> は、リンク用に使用され、Microsoft Edge でリンクを開くために使用されます。</span><span class="sxs-lookup"><span data-stu-id="39fd9-124">, which is used for links, will open the link in Microsoft Edge.</span></span>


<span id="default" />
## <span data-ttu-id="39fd9-125">例: 既定の Surface Hub のスタート画面のレイアウト</span><span class="sxs-lookup"><span data-stu-id="39fd9-125">Example: Default Surface Hub Start layout</span></span>

```xml
<LayoutModificationTemplate Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification">
  <LayoutOptions StartTileGroupCellWidth="8" />
  <DefaultLayoutOverride>
    <StartLayoutCollection>
      <defaultlayout:StartLayout GroupCellWidth="8" xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout">
        <start:Group Name="" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
        <start:Tile
            AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
            Size="2x2"
            Row="0"
            Column="0"/>
        <start:Tile
            AppUserModelID="Microsoft.Getstarted_8wekyb3d8bbwe!App"
            Size="4x2"
            Row="0"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.PowerPoint_8wekyb3d8bbwe!Microsoft.pptim"
            Size="2x2"
            Row="2"
            Column="0"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!Microsoft.Word"
            Size="2x2"
            Row="2"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!Microsoft.Excel"
            Size="2x2"
            Row="2"
            Column="4"/>
        <start:Tile
            AppUserModelID="c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy!App"
            Size="2x2"
            Row="4"
            Column="0"/>
        <start:Tile
            AppUserModelID="microsoft.microsoftskydrive_8wekyb3d8bbwe!App"
            Size="2x2"
            Row="4"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.MicrosoftPowerBIForWindows_8wekyb3d8bbwe!Microsoft.MicrosoftPowerBIForWindows"
            Size="2x2"
            Row="4"
            Column="4"/>
        </start:Group>
      </defaultlayout:StartLayout>
    </StartLayoutCollection>
  </DefaultLayoutOverride>
</LayoutModificationTemplate>
```

<span id="edge" />
## <span data-ttu-id="39fd9-126">例: Microsoft Edge のリンクを含むスタート画面のレイアウト</span><span class="sxs-lookup"><span data-stu-id="39fd9-126">Example: Start layout that includes a Microsoft Edge link</span></span>

<span data-ttu-id="39fd9-127">この例では、Web サイトへのリンクと .pdf ファイルへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="39fd9-127">This example shows a link to a website and a link to a .pdf file.</span></span> <span data-ttu-id="39fd9-128">Microsoft Edge のセカンダリタイルでは、150 x 150 ピクセルのアイコンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="39fd9-128">The secondary tile for Microsoft Edge uses a 150 x 150 pixel icon.</span></span>

```xml
<LayoutModificationTemplate Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification">
  <LayoutOptions StartTileGroupCellWidth="8" />
  <DefaultLayoutOverride>
    <StartLayoutCollection>
      <defaultlayout:StartLayout GroupCellWidth="8" xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout">
        <start:Group Name="" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
    <start:Tile
              AppUserModelID="Microsoft.Office.PowerPoint_8wekyb3d8bbwe!Microsoft.pptim"
              Size="2x2"
              Row="0"
              Column="0"/>
          <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!Microsoft.Word"
              Size="2x2"
              Row="0"
              Column="2"/>
          <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!Microsoft.Excel"
              Size="2x2"
              Row="0"
              Column="4"/>
    <start:Tile
              AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
              Size="2x2"
              Row="2"
              Column="0"/>
    <start:Tile
              AppUserModelID="microsoft.microsoftskydrive_8wekyb3d8bbwe!App"
              Size="2x2" 
             Row="2"
             Column="2"/>   
  <start:SecondaryTile
            AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
           TileID="2678823080"
           DisplayName="Bing"
           Arguments="https://www.bing.com/"
           Square150x150LogoUri="ms-appx:///"
           Wide310x150LogoUri="ms-appx:///"
           ShowNameOnSquare150x150Logo="true"
           ShowNameOnWide310x150Logo="false"
           BackgroundColor="#ffe9e7e7"
           ForegroundText="dark"
           Size="2x2"
           Column="4"
           Row="2"  />
    <start:Tile
              AppUserModelID="Microsoft.Windows.Photos_8wekyb3d8bbwe!App"
              Size="2x2"
              Row="4"
              Column="0"/>
    <start:SecondaryTile
             AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
             TileID="6153963000"
             DisplayName="cstrtqbiology.pdf"
             Arguments="-contentTile -formatVersion 0x00000003 -pinnedTimeLow 0x45b7376e -pinnedTimeHigh 0x01d2356c -securityFlags 0x00000000 -tileType 0x00000000 -url 0x0000003a https://www.ada.gov/regs2010/2010ADAStandards/Guidance_2010ADAStandards.pdf"
             Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png"
             Wide310x150LogoUri="ms-appx:///" 
             ShowNameOnSquare150x150Logo="true"
             ShowNameOnWide310x150Logo="false"
             BackgroundColor="#ff4e4248"
             Size="4x2" 
             Row="4"
             Column="2"/>
        </start:Group>
      </defaultlayout:StartLayout>
    </StartLayoutCollection>
  </DefaultLayoutOverride>
</LayoutModificationTemplate>
```

>[!NOTE]
><span data-ttu-id="39fd9-129">Is light の既定値 `ForegroundText` は、値を `ForegroundText` ダークに変更しない限り、XML に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39fd9-129">The default value for `ForegroundText` is light; you don't need to include `ForegroundText` in your XML unless you're changing the value to dark.</span></span>
