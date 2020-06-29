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
ms.openlocfilehash: 32d8fded8c325766f7ab6bbc750ba7fe13e01d70
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834390"
---
# <span data-ttu-id="803ee-104">Microsoft Surface Deployment Accelerator</span><span class="sxs-lookup"><span data-stu-id="803ee-104">Microsoft Surface Deployment Accelerator</span></span>

<span data-ttu-id="803ee-105">Microsoft Surface Deployment Accelerator (SDA) は、無料の Microsoft 展開ツールを使用して、Microsoft が推奨する展開操作の作成と構成を自動化します。</span><span class="sxs-lookup"><span data-stu-id="803ee-105">Microsoft Surface Deployment Accelerator (SDA) automates the creation and configuration of a Microsoft recommended deployment experience by using free Microsoft deployment tools.</span></span>

<span data-ttu-id="803ee-106">2020年4月に再設計されたため、企業環境での Surface イメージの展開が簡素化および自動化されています。 SDA ツールを使用すると、組織の要件に合わせてカスタマイズできる "工場のような" Windows イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="803ee-106">Redesigned in April 2020 to simplify and automate deployment of Surface images in a corporate environment, the SDA tool allows you to build a “factory-like” Windows image that you can customize to your organizational requirements.</span></span>

<span data-ttu-id="803ee-107">オープンソース、スクリプト駆動型 SDA ツールは、windows 10 の Windows アセスメント & デプロイメントキット (ADK) を活用し、テスト環境または運用環境での Windows イメージ (WIM) の作成を容易にします。</span><span class="sxs-lookup"><span data-stu-id="803ee-107">The open source, script-driven SDA tool leverages the Windows Assessment and Deployment Kit (ADK) for Windows 10, facilitating the creation of Windows images (WIM) in test or production environments.</span></span> <span data-ttu-id="803ee-108">最新の ADK がまだインストールされていない場合は、SDA ツールの実行時にダウンロードされてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="803ee-108">If the latest ADK is not already installed, it will be downloaded and installed when running the SDA tool.</span></span>

<span data-ttu-id="803ee-109">結果として得られるイメージは、Microsoft Office や Surface UWP アプリケーションなどのプレインストールされているアプリケーションがない場合に、ベアメタル回復 (BMR) イメージの構成にほぼ一致します。</span><span class="sxs-lookup"><span data-stu-id="803ee-109">The resulting image closely matches the configuration of Bare Metal Recovery (BMR) images, without any pre-installed applications such as Microsoft Office or the Surface UWP application.</span></span>

**<span data-ttu-id="803ee-110">SDA を実行するには:</span><span class="sxs-lookup"><span data-stu-id="803ee-110">To run SDA:</span></span>**

1. <span data-ttu-id="803ee-111">GitHub の[SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="803ee-111">Go to [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) on GitHub.</span></span> 
2. <span data-ttu-id="803ee-112">[**クローン] または [ダウンロード**] を選択して、Readme ファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="803ee-112">Select **Clone or Download** and review the Readme file.</span></span>
3. <span data-ttu-id="803ee-113">Readme に記載されているように、環境に適した変数を使ってスクリプトを編集し、テスト環境で実行する前に確認します。</span><span class="sxs-lookup"><span data-stu-id="803ee-113">Edit the script with the appropriate variables for your environment, as documented in the Readme, and review before running it in your test environment.</span></span> 

   ![Surface 展開アクセラレータツールの実行](images/surface-deployment-accelerator.png)

## <span data-ttu-id="803ee-115">関連リンク</span><span class="sxs-lookup"><span data-stu-id="803ee-115">Related links</span></span>

 - [<span data-ttu-id="803ee-116">GitHub でリリースされたソースイメージ展開ツールを開く</span><span class="sxs-lookup"><span data-stu-id="803ee-116">Open source image deployment tool released on GitHub</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [<span data-ttu-id="803ee-117">Windows ADK をダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="803ee-117">Download and install the Windows ADK</span></span>](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
