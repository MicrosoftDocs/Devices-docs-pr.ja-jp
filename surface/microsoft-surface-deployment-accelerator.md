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
ms.openlocfilehash: 0e136bd0a69db7a4c4e5cea7d2c065727dcc8fcc
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016442"
---
# <span data-ttu-id="675e0-104">Microsoft Surface Deployment Accelerator</span><span class="sxs-lookup"><span data-stu-id="675e0-104">Microsoft Surface Deployment Accelerator</span></span>

<span data-ttu-id="675e0-105">Microsoft Surface Deployment Accelerator (SDA) は、無料の Microsoft 展開ツールを使用して、Microsoft が推奨する展開操作の作成と構成を自動化します。</span><span class="sxs-lookup"><span data-stu-id="675e0-105">Microsoft Surface Deployment Accelerator (SDA) automates the creation and configuration of a Microsoft recommended deployment experience by using free Microsoft deployment tools.</span></span>

<span data-ttu-id="675e0-106">2020年4月に再設計されたため、企業環境での Surface イメージの展開が簡素化および自動化されています。 SDA ツールを使用すると、組織の要件に合わせてカスタマイズできる "工場のような" Windows イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="675e0-106">Redesigned in April 2020 to simplify and automate deployment of Surface images in a corporate environment, the SDA tool allows you to build a “factory-like” Windows image that you can customize to your organizational requirements.</span></span>

<span data-ttu-id="675e0-107">オープンソース、スクリプト駆動型 SDA ツールは、windows 10 の Windows アセスメント & デプロイメントキット (ADK) を活用し、テスト環境または運用環境での Windows イメージ (WIM) の作成を容易にします。</span><span class="sxs-lookup"><span data-stu-id="675e0-107">The open source, script-driven SDA tool leverages the Windows Assessment and Deployment Kit (ADK) for Windows 10, facilitating the creation of Windows images (WIM) in test or production environments.</span></span> <span data-ttu-id="675e0-108">最新の ADK がまだインストールされていない場合は、SDA ツールの実行時にダウンロードされてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="675e0-108">If the latest ADK is not already installed, it will be downloaded and installed when running the SDA tool.</span></span>

<span data-ttu-id="675e0-109">結果として得られるイメージは、Microsoft Office や Surface UWP アプリケーションなどのプレインストールされているアプリケーションがない場合に、ベアメタル回復 (BMR) イメージの構成にほぼ一致します。</span><span class="sxs-lookup"><span data-stu-id="675e0-109">The resulting image closely matches the configuration of Bare Metal Recovery (BMR) images, without any pre-installed applications such as Microsoft Office or the Surface UWP application.</span></span>

## <span data-ttu-id="675e0-110">要件</span><span class="sxs-lookup"><span data-stu-id="675e0-110">Requirements</span></span>

1. <span data-ttu-id="675e0-111">USB サムドライブのサイズが 16 GB 以上。</span><span class="sxs-lookup"><span data-stu-id="675e0-111">A USB thumb drive at least 16 GB in size.</span></span> <span data-ttu-id="675e0-112">USB ドライブは、書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="675e0-112">The USB drive will be formatted.</span></span>
2. <span data-ttu-id="675e0-113">Windows 10 Pro または Windows 10 Enterprise を含む .iso ファイル。</span><span class="sxs-lookup"><span data-stu-id="675e0-113">An .iso file with Windows 10 Pro or Windows 10 Enterprise.</span></span> <span data-ttu-id="675e0-114">メディア作成ツールを使って、Windows 10 をダウンロードし、.iso ファイルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="675e0-114">The media creation tool can be used to download Windows 10 and create an .iso file.</span></span> <span data-ttu-id="675e0-115">詳細については、「 [Windows 10 をダウンロード](https://www.microsoft.com/software-download/windows10)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="675e0-115">For more information, see [Download Windows 10](https://www.microsoft.com/software-download/windows10).</span></span>

## <span data-ttu-id="675e0-116">SDA を実行する方法</span><span class="sxs-lookup"><span data-stu-id="675e0-116">How to run SDA</span></span>

**<span data-ttu-id="675e0-117">SDA を実行するには:</span><span class="sxs-lookup"><span data-stu-id="675e0-117">To run SDA:</span></span>**

1. <span data-ttu-id="675e0-118">GitHub の [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="675e0-118">Go to [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) on GitHub.</span></span> 
2. <span data-ttu-id="675e0-119">[README](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md)のドキュメントを確認します。</span><span class="sxs-lookup"><span data-stu-id="675e0-119">Review the [README](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) documentation.</span></span>
3. <span data-ttu-id="675e0-120">[ [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) ] ページで、[ **コード** ] ボタンをクリックし、[ **ZIP のダウンロード** ] を選択して、ファイルをローカルコンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="675e0-120">On the [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) page, click the **Code** button and then select **Download ZIP** to save the files locally on your computer.</span></span>
4. <span data-ttu-id="675e0-121">.Zip ファイルを右クリックし、[ **プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="675e0-121">Right-click the .zip file and then click **Properties**.</span></span>
5. <span data-ttu-id="675e0-122">[ **全般** ] タブで、[ **ブロックの解除** ] チェックボックスをオンにし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="675e0-122">On the **General** tab, select the **Unblock** checkbox and then click **OK**.</span></span>
6. <span data-ttu-id="675e0-123">.Zip ファイルをハードドライブ上の場所に抽出します (例: C:\SDA)。</span><span class="sxs-lookup"><span data-stu-id="675e0-123">Extract the .zip file to a location on your hard drive (ex: C:\SDA).</span></span>
7. <span data-ttu-id="675e0-124">昇格された Windows PowerShell プロンプトを開いて、現在のセッションの Set-executionpolicy を [制限しない] に設定します。</span><span class="sxs-lookup"><span data-stu-id="675e0-124">Open an elevated Windows PowerShell prompt and set ExecutionPolicy for the current session to Unrestricted.</span></span>

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. <span data-ttu-id="675e0-125">環境のパラメーターを指定して SDA スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="675e0-125">Run the SDA script specifying parameters for your environment.</span></span> <span data-ttu-id="675e0-126">たとえば、次のコマンドは、Windows 10 を Surface Hub 2 にインストールするために使用できる起動可能な USB ドライブを作成します。</span><span class="sxs-lookup"><span data-stu-id="675e0-126">For example, the following command will create a bootable USB drive that can be used to install Windows 10 on a Surface Hub 2:</span></span>

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```

   ![Surface 展開アクセラレータツールの実行](images/sda1.png)

    <span data-ttu-id="675e0-128">スクリプトでは、実行に約45分の時間が必要ですが、使用可能な CPU とディスクリソースによっては、より長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="675e0-128">The script will require about 45 minutes to run, but could take longer depending on available CPU and disk resources.</span></span> 

    <span data-ttu-id="675e0-129">Windows イメージを作成した後、スクリプトによって USB ドライブのドライブ文字を確認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="675e0-129">After creating a Windows image, the script will ask you to confirm the drive letter of your USB drive.</span></span> <span data-ttu-id="675e0-130">USB ドライブの書式が設定され、起動可能として構成され、ファイルがコピーされて、Surface デバイス用のカスタム Windows 10 イメージのインストールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="675e0-130">The USB drive will then be formatted, configured as bootable, and files copied to enable installation of the custom Windows 10 image for Surface devices.</span></span>

9. <span data-ttu-id="675e0-131">Windows 10 をインストールするデバイスに USB ドライブを挿入し、再起動して Windows 10 のインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="675e0-131">Insert the USB drive into the device where you want to install Windows 10 and reboot to begin installing Windows 10.</span></span> <span data-ttu-id="675e0-132">USB ブートは BIOS で有効にする必要があります。これには、セキュアブートを一時的に無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="675e0-132">USB boot must be enabled in BIOS, which can require that you temporarily disable Secure Boot.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="675e0-133">USB ドライブから起動すると、Windows 10 のインストールが直ちに開始されます。</span><span class="sxs-lookup"><span data-stu-id="675e0-133">Booting from the USB drive will immediately begin installing Windows 10.</span></span> <span data-ttu-id="675e0-134">USB を挿入して再起動する前に、デバイスの準備ができていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="675e0-134">Ensure that your device is ready before inserting the USB and restarting.</span></span> 

## <span data-ttu-id="675e0-135">関連リンク</span><span class="sxs-lookup"><span data-stu-id="675e0-135">Related links</span></span>

 - [<span data-ttu-id="675e0-136">GitHub でリリースされたソースイメージ展開ツールを開く</span><span class="sxs-lookup"><span data-stu-id="675e0-136">Open source image deployment tool released on GitHub</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [<span data-ttu-id="675e0-137">Windows ADK をダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="675e0-137">Download and install the Windows ADK</span></span>](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
