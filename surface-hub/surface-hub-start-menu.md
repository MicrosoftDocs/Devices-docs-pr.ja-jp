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
ms.openlocfilehash: cf9649b8d1f747722064793fbbde70116bc7f424
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576847"
---
# <a name="configure-surface-hub-start-menu"></a>Surface Hub のスタート メニューの構成

[Windows 10 の 2018 年 1 月 17日 の更新プログラム](https://support.microsoft.com/help/4057144) (ビルド 15063.877) により、Surface Hub デバイスでスタート メニューをカスタマイズできるようになりました。 カスタマイズしたスタート メニューのレイアウトを適用するには、モバイル デバイス管理 (MDM) を使用します。

カスタマイズしたスタート メニューのレイアウトを Surface Hub に適用すると、ユーザーはスタート画面でアプリをピン留めしたり、ピン留めを外したり、アンインストールしたりすることはできなません。 

## <a name="how-to-apply-a-customized-start-menu-to-surface-hub"></a>Surface Hub にカスタマイズしたスタート メニューを適用する方法

カスタマイズしたスタート メニューは、スタート画面のレイアウトの XML ファイルで定義されます。 スタート画面のレイアウト XML ファイルを作成するには、2 つのオプションがあります。

- [既定の Surface Hub のスタート画面の XML](#default) を編集する

    - または -

- デスクトップで目的のスタート メニューを構成し (Surface Hub で利用できるアプリのみをピン留めし)、[そのレイアウトをエクスポート](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout)する

>[!TIP]
>デスクトップのスタート メニューに Web リンクを含むタイルを追加するには、Microsoft Edge でそのリンクに移動し、右上隅にある [`...`] を選択して、**[このページをスタートにピン留めする]** を選択します。 リンクが XML でどのように表示されるかを示す例については、[Microsoft Edge のリンクを含むスタート画面のレイアウト](#edge)を参照してください。

既定の XML またはエクスポートしたレイアウトを編集するには、[スタート画面のレイアウトの XML](https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop) について理解しておく必要があります。 [デスクトップと Surface Hub ではスタート画面のレイアウトの相違点](#differences)がいくつかあります。

スタート画面のレイアウトの XML でスタート メニューが定義されている場合、[レイアウトを適用するための MDM ポリシーを作成します](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management#a-href-idbkmk-domaingpodeploymentacreate-a-policy-for-your-customized-start-layout)。

<span id="differences" />

## <a name="differences-between-surface-hub-and-desktop-start-menu"></a>Surface Hub とデスクトップのスタートメニューの相違点

Surface Hub と Windows 10 デスクトップでは、スタート メニューのカスタマイズにいくつかの大きな違いがあります。

- デスクトップ アプリケーション (Win32) は、Windows デスクトップ アプリケーション (Win32) でサポートされていないので、スタート レイアウト XML で**DesktopApplicationTile** https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop#startdesktopapplicationtile) を使用Surface Hub。
- スタート画面のレイアウトの XML を使用して、Surface Hub のタスク バーやようこそ画面を構成することはできません。  
- スタート レイアウト ポリシーは、ユーザーではなくデバイスにのみ割り当てる必要があります。
- ポリシーで使用する OMA-URI 設定は、 `./Device/Vendor/MSFT/Policy/Config/Start/StartLayout`
- Surface Hub がサポートしているのは最大 6 列 (6 個の 1 x 1 タイル) ですが、`GroupCellWidth=8` を定義する**必要があります**。ただし、Surface Hub で表示されるのは列 0 ～ 5 のタイルのみで、列 6 および 7 は表示されません。
- Surface Hub は最大 6 行 (6 個の 1 x 1 タイル) をサポートしています。
- `SecondaryTile` は、リンク用に使用され、Microsoft Edge でリンクを開くために使用されます。


<span id="default" />

## <a name="example-default-surface-hub-start-layout"></a>例: 既定の Surface Hub のスタート画面のレイアウト

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

## <a name="example-start-layout-that-includes-a-microsoft-edge-link"></a>例: Microsoft Edge のリンクを含むスタート画面のレイアウト

この例では、Web サイトへのリンクと .pdf ファイルへのリンクを示します。 ユーザーのセカンダリ タイルMicrosoft Edge 150 x 150 ピクセル のアイコンを使用します。

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
>既定値は明るい値です。値を濃色に変更しない限り、XML に含 `ForegroundText` `ForegroundText` める必要があります。
