---
title: MDT の展開中にSurface Laptopキーボードを有効にする方法
description: MDT を使用して Surface Windows 10に展開する場合は、PE 環境で使用するキーボード ドライバーをインポートWindows必要があります。
keywords: windows 10 surface, 自動化, カスタマイズ, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: coveminer
ms.author: v-tea
ms.topic: article
ms.reviewer: carlol
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
ms.date: 06/21/2021
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
- Surface Laptop 4
ms.openlocfilehash: c02837b0cfda72c6f2a447b99ff4c94a027bb29c
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613866"
---
# <a name="how-to-enable-the-surface-laptop-keyboard-during-mdt-deployment"></a>MDT の展開中にSurface Laptopキーボードを有効にする方法

この記事では、Microsoft Deployment Toolkit (MDT) を使用する展開方法について説明します。 また、この情報を他の展開方法に適用できます。 ほとんどの種類の Surface デバイスでは、キーボードはライト タッチ インストール (LTI) 中に動作する必要があります。 ただし、Surface Laptopを有効にするには、追加のドライバーが必要です。 Surface Laptop (第 1 世代) および Surface Laptop 2 台のデバイスでは、LTI の Windows プレインストール環境 (Windows PE) フェーズで使用するキーボード ドライバーを指定できるフォルダー構造と選択プロファイルを準備する必要があります。 このフォルダー構造の詳細については、「MDT を使用して Windows 10イメージを展開する: 手順 5: ドライバー リポジトリ[を準備する」を参照してください](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)。

> [!TIP]
> 同じ Windows PE ブート インスタンスで Surface Laptop 2 と Surface Laptop 3 のキーボード ドライバーを使用する場合、Windows PE でキーボードまたはタッチパッドが動作しない場合は、ファームウェアを手動でリセットする必要があります。
>
> - [電源] ボタンを 30 秒間長押しします。 電源ユニット (PSU) に接続している場合は、電源ボタンを長押しして、電源をオンにする前に、PSU コードの最後のライトが短時間オフになるまで押し続きます。

> [!IMPORTANT]
> S モードで Windows 10 がプレインストールされている Surface Laptop に Windows 10 イメージを展開する場合は、「KB [4032347、S](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)モードでプレインストールされた Windows 10 を使用して surface デバイスに Windows を展開する場合の問題」を参照してください。

## <a name="add-keyboard-drivers-to-the-selection-profile"></a>選択プロファイルにキーボード ドライバーを追加する

1. 適切な場所からSurface Laptop .msiファイルをダウンロードします。
    - [Surface Laptop (第 1 世代) ドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface Laptop 2 つのドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Surface Laptop 3 と Intel プロセッサ ドライバーとファームウェア](https://www.microsoft.com/download/details.aspx?id=100429)
    - [Surface Laptop 4 と Intel プロセッサ ドライバーとファームウェア](https://www.microsoft.com/download/102924)
    - [Surface Laptop 4 AMD プロセッサ ドライバーとファームウェア](https://www.microsoft.com/download/102923)
2. Surface Laptop .msiファイルの内容を、簡単に見つけやすいフォルダー (c:\\surface_laptop_drivers など) に展開します。 コンテンツを抽出するには、管理者特権でコマンド プロンプト ウィンドウを開き、次の例からコマンドを実行します。

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Deployment Workbench を開き、[展開共有] **ノード** と展開共有を展開し **、WindowsPEX64 フォルダーに移動** します。
4. **WindowsPEX64 フォルダーを右クリック**し、[ドライバーのインポート **] を選択します**。
5. ドライバーのインポート ウィザードの指示に従って、ドライバー フォルダーを WindowsPEX64 フォルダーにインポートします。

 > [!NOTE]
 > ダウンロードしたパッケージを.msi、形式とディレクトリ構造を確認します。  ディレクトリ構造は、.msi ファイルがリリースされた時期に応じて、SurfacePlatformInstaller (古い .msi ファイル) または SurfaceUpdate (新しい .msi ファイル) で開始されます。

## <a name="import-drivers-for-surface-devices"></a>Surface デバイスのドライバーをインポートする

デバイスに応じて、次のフォルダーをSurface Laptopします。  

| デバイス                                | フォルダーのインポート                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 詳細情報                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface Laptop 4 と Intel プロセッサ | TglSerial<br>IntelPreciseTouch<br>SurfaceEthernetAdapter<br>SurfaceBattery<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceSerialHub<br>SurfaceTconDriver<br>surfacetimealarmacpifilter<br>surfacevirtualfunctionenum<br>TglChipset<br>ManagementEngine                                                                                                                                                                                                                                                                                                                          |n/a                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 4 AMD プロセッサ付き   | U0361415<br>AMDfendr<br>AMDGpio2<br>AMDI2c<br>AMDLpcFilterDriverAMDMicroPEP<br>AMDPsp<br>AMDSmf<br>AMDSpi<br>AMDUart<br>SurfaceEthernetAdapter<br>SMBUS<br>SurfaceBattery<br>SurfaceButton<br>SurfaceDigitizerHidSpiExtnPackage<br>SurfaceHIDFriendlyNames<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceOemPanel<br>SurfacePowerMeter<br>SurfacePowerTrackerCore<br>SurfaceSerialHub<br>SurfaceSMFClient<br>SurfaceSmfDisplayClient<br>SurfaceSystemManagementFramework<br>SurfaceTconDriver<br>SurfaceThermalPolicy<br>Surfacetimealarmacpifilter<br>SurfaceUcmUcsiHidClient |n/a                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 3 と Intel プロセッサ | SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SerialIOI2C<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\SurfaceHotPlug<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                                                                                                   | 次のフォルダーをインポートすると、PE の完全なキーボード、トラックパッド、タッチ機能が有効です。<br><br>SerialIOGPIO<br>SerialIOI2C<br>SerialIOSPI<br>SerialIOUART<br>itouch<br>チップセット<br>ChipsetLPSS<br>ChipsetNorthpeak<br>ManagementEngine<br>SurfaceAcpiNotify<br>SurfaceBattery<br>SurfaceDockIntegration<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceIntegration<br>SurfaceSerialHub<br>SurfaceService<br>SurfaceStorageFwUpdat |
| Surface Laptop 2                      | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\I2C<br>SurfacePlatformInstaller\Drivers\System\SPI<br>SurfacePlatformInstaller\Drivers\System\UART<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                           | "SurfaceUpdate" .msi始まる新しいファイルの場合は、次のコマンドを使用します。<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\serialioi2c<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\Itouch                                                                                                                                                                    |
| Surface Laptop (第 1 世代)              | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                                                                                                                                                                         | "SurfaceUpdate" .msi始まる新しいファイルの場合は、次のコマンドを使用します。<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SurfaceHidMiniDriver<br>SurfaceUpdate\SurfaceSerialHubDriver<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                |

  > [!TIP]
  > ダウンロードしたパッケージを.msi、形式とディレクトリ構造を確認します。  ディレクトリ構造は、バージョンがリリースされた時期に応じて、SurfacePlatformInstaller (古い .msi ファイル) または SurfaceUpdate (新しい .msi ファイル) で始.msiされます。

## <a name="verify-imported-drivers--configure-windows-pe-properties"></a>インポートされたドライバーを確認& PE プロパティWindows構成する

1. 次の図に示すように、WindowsPEX64 フォルダーにインポートされたドライバーが含まれているのを確認します。

   ![展開ワークベンチの WindowsPEX64 フォルダーに新しくインポートされたドライバーを示すイメージ](./images/surface-laptop-keyboard-2.png)
1. 次の図に示すように、WindowsPEX64 フォルダーを使用する選択プロファイルを構成します。

   ![選択プロファイルの一部として選択された WindowsPEX64 フォルダーを示す画像](./images/surface-laptop-keyboard-3.png)
1. 次のようにWindows選択プロファイルを使用する MDT 展開共有の PE プロパティを構成します。
    - [**プラットフォーム] で****、[x64] を選択します**。
    - [ **選択プロファイル] で**、新しいプロファイルを選択します。
    - [選択 **プロファイルからすべてのドライバーを含める] を選択します**。

    ![MDT 展開共有Windows PE プロパティを示すイメージ](./images/surface-laptop-keyboard-4.png)
4. 選択プロファイルまたは**DriverGroup001**変数Surface Laptopを使用して、残りのドライバーが構成されていることを確認します。
    - このSurface Laptop (第 1 世代) の場合、**モデルは次**Surface Laptop。 次の図にSurface Laptop\MDT 展開共有\アウトオブボックス ドライバー\Windows10\X64\Surface Laptop フォルダーに残りの Surface Laptop ドライバーが存在する必要があります。
    - 2 Surface Laptopの場合、モデルは**2 Surface Laptopです**。 残りの Surface Laptopドライバーは、\MDT 展開共有\アウトオブボックス ドライバー\Windows10\X64\Surface Laptop 2 フォルダーに存在する必要があります。
    - Intel Surface Laptop 3 の場合、モデルは 3 Surface Laptopです。 残りの Surface Laptopは、\MDT 展開共有\アウトオブボックス ドライバー\Windows10\X64\Surface Laptop 3 フォルダーにあります。

    ![Deployment Workbench の [Surface Laptop] フォルダーにある標準のドライバー (第 1 世代) Surface Laptopを示すイメージ](./images/surface-laptop-keyboard-5.png)

新しい選択プロファイルと関連する設定を使用するように MDT 展開共有を構成したら、「MDT を使用して Windows 10 イメージを展開する: 手順[6:](/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)展開タスク シーケンスを作成する」の説明に従って展開プロセスを続行します。
