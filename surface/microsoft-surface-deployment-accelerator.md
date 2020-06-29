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
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) は、無料の Microsoft 展開ツールを使用して、Microsoft が推奨する展開操作の作成と構成を自動化します。

2020年4月に再設計されたため、企業環境での Surface イメージの展開が簡素化および自動化されています。 SDA ツールを使用すると、組織の要件に合わせてカスタマイズできる "工場のような" Windows イメージを作成できます。

オープンソース、スクリプト駆動型 SDA ツールは、windows 10 の Windows アセスメント & デプロイメントキット (ADK) を活用し、テスト環境または運用環境での Windows イメージ (WIM) の作成を容易にします。 最新の ADK がまだインストールされていない場合は、SDA ツールの実行時にダウンロードされてインストールされます。

結果として得られるイメージは、Microsoft Office や Surface UWP アプリケーションなどのプレインストールされているアプリケーションがない場合に、ベアメタル回復 (BMR) イメージの構成にほぼ一致します。

**SDA を実行するには:**

1. GitHub の[SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator)にアクセスします。 
2. [**クローン] または [ダウンロード**] を選択して、Readme ファイルを確認します。
3. Readme に記載されているように、環境に適した変数を使ってスクリプトを編集し、テスト環境で実行する前に確認します。 

   ![Surface 展開アクセラレータツールの実行](images/surface-deployment-accelerator.png)

## 関連リンク

 - [GitHub でリリースされたソースイメージ展開ツールを開く](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [Windows ADK をダウンロードしてインストールする](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
