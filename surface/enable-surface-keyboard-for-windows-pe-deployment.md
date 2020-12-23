---
title: MDT の展開中に Surface Laptop キーボードを有効にする方法
description: MDT を使って Windows 10 を Surface ノート PC に展開する場合は、Windows PE 環境で使うキーボード ドライバーをインポートする必要があります。
keywords: Windows 10 surface, 自動化, カスタマイズ, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
ms.reviewer: scottmca
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: d7ae6fc434f77cad86e73f111243968493de4ff2
ms.sourcegitcommit: e6224f81f8efb6ac862afec0e60e3ddb182e9e6f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "11247309"
---
# MDT の展開中に Surface Laptop キーボードを有効にする方法

この記事では、Microsoft Deployment Toolkit (MDT) を使用する展開方法について説明します。 この情報は、他の展開方法にも適用できます。 ほとんどの種類の Surface デバイスでは、ライト タッチ インストール (LTI) 中にキーボードが動作する必要があります。 ただし、Surface Laptop では、キーボードを有効にするために追加のドライバーが必要です。 Surface Laptop (第 1 世代) デバイスと Surface Laptop 2 デバイスでは、LTI の Windows プレインストール環境 (Windows PE) フェーズで使用するキーボード ドライバーを指定できるフォルダー構造と選択プロファイルを準備する必要があります。 このフォルダー構造の詳細については、「MDT を使った [Windows 10 イメージの展開: 手順 5:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)ドライバー リポジトリを準備する」を参照してください。


> [!IMPORTANT]
> Windows 10 (S モード) がプレインストールされている Surface Laptop に Windows 10 イメージを展開する場合は、KB [4032347](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)を参照してください。S モードでプレインストールされた Windows 10 を使用して Surface デバイスに Windows を展開する際の問題について説明します。

キーボード ドライバーを選択プロファイルに追加するには、次の手順を実行します。

1. 適切な場所から最新の Surface Laptop MSI ファイルをダウンロードします。
    - [Surface Laptop (第 1 世代) のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface Laptop 2 のドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Intel プロセッサ ドライバーとファームウェアを搭載した Surface Laptop 3](https://www.microsoft.com/download/details.aspx?id=100429)

2. Surface Laptop MSI ファイルの内容を、見つけやすいフォルダー (c:\surface_laptop_drivers など) に抽出します。 内容を抽出するには、管理者特権のコマンド プロンプト ウィンドウを開き、次の例からコマンドを実行します。

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Deployment Workbench を開き **、[Deployment Shares]** ノードと展開共有を展開し **、WindowsPEX64 フォルダーに移動** します。

   ![Deployment Workbench 内の WindowsPEX64 フォルダーの場所を示す画像](./images/surface-laptop-keyboard-1.png)

4. **WindowsPEX64 フォルダーを右クリック**し、[Import **Drivers] (ドライバーのインポート) を選択します**。
5. ドライバーのインポート ウィザードの指示に従って、ドライバー フォルダーを WindowsPEX64 フォルダーにインポートします。  

> [!NOTE]
>  ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。  ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。 

Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\SurfaceHidMiniDriver
- SurfaceUpdate\SurfaceSerialHubDriver
- SurfaceUpdate\Itouch

Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\I2C
 - SurfacePlatformInstaller\Drivers\System\SPI
 - SurfacePlatformInstaller\Drivers\System\UART
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\Itouch

 
Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。

- SurfaceUpdate\IclSerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\SurfaceHotPlug
- SurfaceUpdate\Itouch

次のフォルダーをインポートすると、Surface Laptop 3 の PE でキーボード、トラックパッド、タッチの完全な機能を有効にできます。

- IclSerialIOGPIO
- IclSerialIOI2C
- IclSerialIOSPI
- IclSerialIOUART
- itouch
- IclChipset
- IclChipsetLPSS
- IclChipsetNorthpeak
- ManagementEngine
- SurfaceAcpiNotify
- SurfaceBattery
- SurfaceDockIntegration
- SurfaceHidMini
- SurfaceHotPlug
- SurfaceIntegration
- SurfaceSerialHub
- SurfaceService
- SurfaceStorageFwUpdate


    > [!NOTE]
    >  ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。  ディレクトリ構造は、MSI がリリースされた時期に応じて、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) で始めます。 

    Surface Laptop (第 1 世代) をサポートするには、次のフォルダーをインポートします。

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\SurfaceHidMiniDriver
    - SurfaceUpdate\SurfaceSerialHubDriver
    - SurfaceUpdate\Itouch

    Surface Laptop 2 をサポートするには、次のフォルダーをインポートします。

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\I2C
     - SurfacePlatformInstaller\Drivers\System\SPI
     - SurfacePlatformInstaller\Drivers\System\UART
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次の値を使用します。

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\Itouch

    Intel Processor で Surface Laptop 3 をサポートするには、次のフォルダーをインポートします。

    - SurfaceUpdate\IclSerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\SurfaceHotPlug
    - SurfaceUpdate\Itouch

    > [!NOTE]
    > Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。 残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。

6. WindowsPEX64 フォルダーにインポートされたドライバーが含まれているのを確認します。 フォルダーは次のようになります。  

   ![Deployment Workbench の WindowsPEX64 フォルダーに新しくインポートされたドライバーを示す画像](./images/surface-laptop-keyboard-2.png)

7. WindowsPEX64 フォルダーを使用する選択プロファイルを構成します。 選択プロファイルは次のようになります。  

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)

8. 次のように、新しい選択プロファイルを使う MDT 展開共有の Windows PE プロパティを構成します。  

   - プラットフォーム **の場合**は **、x64 を選択します**。
   - [ **選択プロファイル] で**、新しいプロファイルを選択します。
   - [ **選択プロファイルからすべてのドライバーを含める] を選択します**。
   
   ![MDT 展開共有の Windows PE プロパティを示す画像](./images/surface-laptop-keyboard-4.png)

9. 選択プロファイルまたは **DriverGroup001** 変数を使って、残りの Surface Laptop ドライバーが構成されていることを確認します。  
   - Surface Laptop (第 1 世代) の場合、モデルは **Surface Laptop です**。 残りの Surface Laptop ドライバーは、次の図に示すように、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop フォルダーにあります。
   - Surface Laptop 2 の場合、モデルは **Surface Laptop 2 です**。 残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 フォルダーにあります。 
   - Intel プロセッサを搭載した Surface Laptop 3 の場合、モデルは Surface Laptop 3 です。 残りの Surface Laptop ドライバーは、\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 フォルダーにあります。

   ![Deployment Workbench の Surface Laptop フォルダーにある通常の Surface Laptop (第 1 世代) ドライバーを示す画像](./images/surface-laptop-keyboard-5.png)

新しい選択プロファイルと関連する設定を使って MDT 展開共有を構成した後、「MDT を使った Windows 10 イメージの展開 [: 手順 6:](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)展開タスク シーケンスを作成する」の説明に従って展開プロセスを続行します。
