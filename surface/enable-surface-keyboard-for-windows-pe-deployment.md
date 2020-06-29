---
title: MDT の展開時に Surface ラップトップキーボードを有効にする方法
description: MDT を使用して Windows 10 を Surface のノート pc に展開する場合は、Windows PE 環境で使うキーボードドライバーをインポートする必要があります。
keywords: windows 10 surface、オートメーション、カスタマイズ、mdt
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
ms.openlocfilehash: 5d4e4b46c109d9fe24fe75151c9eb1e0a8b702c0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834717"
---
# MDT の展開時に Surface ラップトップキーボードを有効にする方法

この記事では、Microsoft 展開ツールキット (MDT) を使用する展開方法について説明します。 この情報は、その他の展開方法論にも適用することができます。 ほとんどの種類の Surface デバイスでは、キーボードは、ライトタッチインストール (LTI) で動作する必要があります。 ただし、Surface ノートパソコンでキーボードを有効にするには、追加のドライバーが必要です。 Surface Pc (第1世代) および Surface ノートブック2台の場合、LTI の Windows Preinstallation Environment (Windows PE) フェーズで使用するキーボードドライバーを指定できるようにするには、フォルダー構造と選択プロファイルを準備する必要があります。 このフォルダー構造の詳細については、「 [MDT を使用した Windows 10 イメージの展開: 手順 5: ドライバーリポジトリを準備する](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)」を参照してください。

> [!NOTE]
> ドライバーの競合により、現在のところ、同じ Windows PE ブートインスタンスで Surface ノートブック2と Surface ノートブックの3つのキーボードドライバーを追加することはサポートされていません。代わりに別のインスタンスを使用してください。

> [!IMPORTANT]
> Windows 10 イメージを S モードでプレインストールされた Surface ノート Pc に展開している場合は、「windows 10 を[プレインストールしているときに、s モードで](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)windows 10 をインストールすると、KB 4032347、問題が発生する」を参照してください。

選択プロファイルにキーボードドライバーを追加するには、次の手順を実行します。

1. 適切な場所から最新の Surface ラップトップ MSI ファイルをダウンロードします。
    - [Surface ラップトップ (第1世代) ドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface ラップトップ2ドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Intel プロセッサドライバーとファームウェアを搭載した Surface ノートパソコン3](https://www.microsoft.com/download/details.aspx?id=100429)

2. Surface ラップトップ MSI ファイルの内容を、簡単に見つけることができるフォルダー (c:\ surface_laptop_drivers など) に抽出します。 コンテンツを抽出するには、管理者特権のコマンドプロンプトウィンドウを開いて、次の例のコマンドを実行します。

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. 展開ワークベンチを開き **、展開共有ノードと**展開共有を展開して、 **WindowsPEX64**フォルダーに移動します。

   ![展開ワークベンチでの WindowsPEX64 フォルダーの場所を示す画像](./images/surface-laptop-keyboard-1.png)

4. **WindowsPEX64**フォルダーを右クリックして、[**ドライバーのインポート**] を選択します。
5. ドライバーのインポートウィザードの指示に従って、WindowsPEX64 フォルダーにドライバーフォルダーをインポートします。  

> [!NOTE]
>  ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。  MSI がリリースされたタイミングに応じて、ディレクトリ構造は、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) のいずれかで開始されます。 

Surface Pc (第1世代) をサポートするには、次のフォルダーをインポートします。

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\SurfaceHidMiniDriver
- SurfaceUpdate\SurfaceSerialHubDriver
- SurfaceUpdate\Itouch

Surface ノート Pc 2 をサポートするには、次のフォルダーをインポートします。

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\I2C
 - SurfacePlatformInstaller\Drivers\System\SPI
 - SurfacePlatformInstaller\Drivers\System\UART
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\Itouch

 
Intel プロセッサを搭載した Surface ノート Pc 3 をサポートするには、次のフォルダーをインポートします。

- SurfaceUpdate\IclSerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\SurfaceHotPlug
- SurfaceUpdate\Itouch

次のフォルダーをインポートすると、Surface Pc 3 の PE でのフルキーボード、トラックパッド、タッチ機能が有効になります。

- IclSerialIOGPIO
- IclSerialIOI2C
- Iclて、
- お絵
- itouch
- IclChipset セット
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
    >  ダウンロードした MSI パッケージを確認して、形式とディレクトリ構造を確認します。  MSI がリリースされたタイミングに応じて、ディレクトリ構造は、SurfacePlatformInstaller (古い MSI ファイル) または SurfaceUpdate (新しい MSI ファイル) のいずれかで開始されます。 

    Surface Pc (第1世代) をサポートするには、次のフォルダーをインポートします。

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\SurfaceHidMiniDriver
    - SurfaceUpdate\SurfaceSerialHubDriver
    - SurfaceUpdate\Itouch

    Surface ノート Pc 2 をサポートするには、次のフォルダーをインポートします。

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\I2C
     - SurfacePlatformInstaller\Drivers\System\SPI
     - SurfacePlatformInstaller\Drivers\System\UART
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    または、"SurfaceUpdate" で始まる新しい MSI ファイルの場合は、次のように使用します。

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\Itouch

    Intel プロセッサを搭載した Surface ノート Pc 3 をサポートするには、次のフォルダーをインポートします。

    - SurfaceUpdate\IclSerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\SurfaceHotPlug
    - SurfaceUpdate\Itouch

    > [!NOTE]
    > Surface Pc 3 (Intel プロセッサ搭載) では、モデルは Surface ノートブック3です。 残りの Surface のラップトップドライバーは、「\ MDT の展開」という Drivers\Windows10\X64\Surface の [ラップトップの 3] フォルダーにあります。

6. WindowsPEX64 フォルダーに、インポートしたドライバーが含まれていることを確認します。 フォルダーは次のようになります。  

   ![展開ワークベンチの WindowsPEX64 フォルダーに新しくインポートされたドライバーを示す画像](./images/surface-laptop-keyboard-2.png)

7. WindowsPEX64 フォルダーを使う選択プロファイルを構成します。 選択プロファイルは、次のようになります。  

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)

8. 新しい選択プロファイルを使用するために、MDT 展開共有の Windows PE プロパティを構成します。次のようにします。  

   - **プラットフォーム**の場合は、[ **x64**] を選びます。
   - [**選択プロファイル**] で、新しいプロファイルを選択します。
   - 選択**プロファイルから [すべてのドライバーを含める**] を選択します。
   
   ![MDT 展開共有の Windows PE プロパティを示す画像](./images/surface-laptop-keyboard-4.png)

9. 選択プロファイルまたは**DriverGroup001**変数のいずれかを使用して、残りの Surface ラップトップドライバーが構成されていることを確認します。  
   - Surface ラップトップ (第1世代) では、モデルは**Surface pc**です。 残りの Surface のラップトップドライバーは、このリストの後の図に示すように、[/MDT 展開] の [Drivers\Windows10\X64\Surface のラップトップ] フォルダーに存在している必要があります。
   - Surface ノートブック2の場合、モデルは**Surface ノートブック 2**です。 残りの Surface のラップトップドライバーは、\ MDT の展開用の [Drivers\Windows10\X64\Surface] ボックスに常駐している必要があります。 
   - Surface Pc 3 (Intel プロセッサ搭載) では、モデルは Surface ノートブック3です。 残りの Surface のラップトップドライバーは、「\ MDT の展開」という Drivers\Windows10\X64\Surface の [ラップトップの 3] フォルダーにあります。

   ![展開ワークベンチの Surface ラップトップフォルダーの標準 Surface (第1世代) ドライバーを示す画像](./images/surface-laptop-keyboard-5.png)

新しい選択プロファイルと関連設定を使用するために MDT 展開共有を構成した後、「 [mdt を使用した Windows 10 イメージの展開: 手順 6: 展開タスクシーケンスを作成](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)する」の説明に従って展開プロセスを続行します。
