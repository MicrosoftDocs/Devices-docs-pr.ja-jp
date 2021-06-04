---
title: Microsoft Surface Deployment Accelerator (Surface)
description: Microsoft Surface Deployment Accelerator は、組織で Surface デバイスのイメージを再作成するためのクイックでシンプルな展開メカニズムを提供します。
ms.assetid: E7991E90-4AAE-44B6-8822-58BFDE3EADE4
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: 展開, インストール, ツール, deploy, install, tool
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 5/08/2020
ms.openlocfilehash: 3ede7311289dc4bc720735c0142ff3a46fbb69e7
ms.sourcegitcommit: 582c5a79881c58c4f1aa66cfcab46db966ca9f24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016558"
---
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) は、無料の Microsoft 展開ツールを使用して、Microsoft が推奨する展開操作の作成と構成を自動化します。

2020年4月に再設計されたため、企業環境での Surface イメージの展開が簡素化および自動化されています。 SDA ツールを使用すると、組織の要件に合わせてカスタマイズできる "工場のような" Windows イメージを作成できます。

オープンソース、スクリプト駆動型 SDA ツールは、windows 10 の Windows アセスメント & デプロイメントキット (ADK) を活用し、テスト環境または運用環境での Windows イメージ (WIM) の作成を容易にします。 最新の ADK がまだインストールされていない場合は、SDA ツールの実行時にダウンロードされてインストールされます。

結果として得られるイメージは、Microsoft Office や Surface UWP アプリケーションなどのプレインストールされているアプリケーションがない場合に、ベアメタル回復 (BMR) イメージの構成にほぼ一致します。

##  <a name="requirements"></a>要件

1. USB サムドライブのサイズが 16 GB 以上。 USB ドライブは、書式設定されます。
2. Windows 10 Pro または Windows 10 Enterprise を含む .iso ファイル。 メディア作成ツールを使って、Windows 10 をダウンロードし、.iso ファイルを作成することができます。 詳細については、「 [Windows 10 をダウンロード](https://www.microsoft.com/software-download/windows10)する」を参照してください。
3. インターネットアクセスが可能な Windows 10 バージョン2004以降を実行しているデバイス。

要件の詳細については、README ドキュメントの「 [前提条件](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) 」を参照してください。

##  <a name="how-to-run-the-sda"></a>SDA の実行方法

**SDA を実行するには:**

1. GitHub の [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) にアクセスします。 
2. [README](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md)のドキュメントを確認します。
3. [ [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) ] ページで、[ **コード** ] ボタンをクリックし、[ **ZIP のダウンロード** ] を選択して、ファイルをローカルコンピューターに保存します。
4. .Zip ファイルを右クリックし、[ **プロパティ**] をクリックします。
5. [ **全般** ] タブで、[ **ブロックの解除** ] チェックボックスをオンにし、[ **OK**] をクリックします。
6. .Zip ファイルをハードドライブ上の場所に抽出します (例: C:\SDA)。
7. 昇格された Windows PowerShell プロンプトを開いて、現在のセッションの Set-executionpolicy を [制限しない] に設定します。

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. 環境のパラメーターを指定して SDA スクリプトを実行します。 このスクリプトを使って、さまざまな Surface デバイスに Windows 10 をインストールするためのイメージを作成することができます。 サポートされているデバイスの完全な一覧については、SDA の README 記事の [デバイスパラメーターの説明](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) を参照してください。 

    たとえば、次のコマンドを実行すると、 [Surface Hub 2 に Windows 10 をインストール](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os)するために使用できる起動可能な USB ドライブが作成されます。

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```
    サンプルスクリプトの出力を次に示します。

   ![Surface 展開アクセラレータツールの実行](images/sda1.png)

    スクリプトでは、実行に約45分の時間が必要ですが、使用可能な CPU とディスクリソースによっては、より長い時間がかかることがあります。 

    Windows イメージを作成した後、スクリプトによって USB ドライブのドライブ文字を挿入して確認するように求められます。 USB ドライブの書式が設定され、起動可能として構成され、ファイルがコピーされて、Surface デバイス用のカスタム Windows 10 イメージのインストールが可能になります。

9. Windows 10 をインストールするデバイスに USB ドライブを挿入し、再起動して Windows 10 のインストールを開始します。 USB ブートは BIOS で有効にする必要があります。これには、セキュアブートを一時的に無効にする必要があります。

> [!IMPORTANT]
> USB ドライブから起動すると、Windows 10 のインストールが直ちに開始されます。 USB を挿入して再起動する前に、デバイスの準備ができていることを確認します。 

##  <a name="related-links"></a>関連リンク

 - [GitHub でリリースされたソースイメージ展開ツールを開く](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)
 - [Windows ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
