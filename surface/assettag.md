---
title: Surface Asset タグツール
description: このトピックでは、Surface Asset タグツールの使用方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.openlocfilehash: ca6a71a6b864692953fcd96eb687c2752527c9f5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834749"
---
# <span data-ttu-id="3252b-103">Surface Asset タグツール</span><span class="sxs-lookup"><span data-stu-id="3252b-103">Surface Asset Tag Tool</span></span>

<span data-ttu-id="3252b-104">Surface Asset Tag は、Surface デバイスの割り当て済みアセットタグ値の表示、割り当て、変更を可能にするコマンドラインインターフェイス (CLI) ユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="3252b-104">Surface Asset Tag is a command line interface (CLI) utility that allows you to view, assign, and modify an assigned asset tag value for Surface devices.</span></span> <span data-ttu-id="3252b-105">Surface Pro 3 と、それ以降のすべての Surface デバイスで動作します。</span><span class="sxs-lookup"><span data-stu-id="3252b-105">It works on Surface Pro 3 and all newer Surface devices.</span></span>

## <span data-ttu-id="3252b-106">システム要件</span><span class="sxs-lookup"><span data-stu-id="3252b-106">System requirements</span></span>

- <span data-ttu-id="3252b-107">Surface Pro 3 以降</span><span class="sxs-lookup"><span data-stu-id="3252b-107">Surface Pro 3 or later</span></span>

- <span data-ttu-id="3252b-108">UEFI ファームウェアバージョン3.9.150.0 以降</span><span class="sxs-lookup"><span data-stu-id="3252b-108">UEFI firmware version 3.9.150.0 or later</span></span>

## <span data-ttu-id="3252b-109">Surface Asset タグを使用する</span><span class="sxs-lookup"><span data-stu-id="3252b-109">Using Surface Asset Tag</span></span> 

<span data-ttu-id="3252b-110">Surface アセットタグを実行するには:</span><span class="sxs-lookup"><span data-stu-id="3252b-110">To run Surface Asset Tag:</span></span>

1.  <span data-ttu-id="3252b-111">Surface デバイスの場合は、 [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=46703)から [ **surface アセットの Tag.zip**をダウンロードして、zip ファイルを抽出し、AssetTag.exe を目的のフォルダーに保存します (この例では C:\\assets)。</span><span class="sxs-lookup"><span data-stu-id="3252b-111">On the Surface device, download **Surface Asset Tag.zip** from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=46703), extract the zip file, and save AssetTag.exe in desired folder (in this example, C:\\assets).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3252b-112">Surface Pro X の場合は、ZIP ファイルで**AssetTag_x86**という名前のアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3252b-112">For Surface Pro X, use the application named **AssetTag_x86**  in the ZIP file.</span></span> 

2.  <span data-ttu-id="3252b-113">管理者としてコマンドコンソールを開き、ツールへのフルパスを入力して AssetTag.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="3252b-113">Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.</span></span>

3.  <span data-ttu-id="3252b-114">Surface を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3252b-114">Restart Surface.</span></span>

### <span data-ttu-id="3252b-115">資産タグツールのコマンド</span><span class="sxs-lookup"><span data-stu-id="3252b-115">Asset Tag tool commands</span></span>   
<span data-ttu-id="3252b-116">次の例では、AssetTag.exe はローカルコンピューター (C:\ アセット) のディレクトリに保存されています。</span><span class="sxs-lookup"><span data-stu-id="3252b-116">In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).</span></span> 

<span data-ttu-id="3252b-117">提案されたアセットタグを取得するには、AssetTag-g を実行します。</span><span class="sxs-lookup"><span data-stu-id="3252b-117">To get the proposed asset tag, run AssetTag -g.</span></span>

**<span data-ttu-id="3252b-118">例</span><span class="sxs-lookup"><span data-stu-id="3252b-118">Example</span></span>**

   ```
 C:\assets\AssetTag.exe -g
  ```
 
 <span data-ttu-id="3252b-119">提案されたアセットタグをクリアするには、AssetTag を実行します。</span><span class="sxs-lookup"><span data-stu-id="3252b-119">To clear the proposed asset tag, run AssetTag -s.</span></span>
 
 **<span data-ttu-id="3252b-120">例</span><span class="sxs-lookup"><span data-stu-id="3252b-120">Example</span></span>**
 
   ```
C:\assets\AssetTag.exe -s
  ```
<span data-ttu-id="3252b-121">提案されたアセットタグを設定するには、AssetTag-s testassettag12 を実行します。</span><span class="sxs-lookup"><span data-stu-id="3252b-121">To set the proposed asset tag, run AssetTag -s testassettag12.</span></span>

**<span data-ttu-id="3252b-122">例</span><span class="sxs-lookup"><span data-stu-id="3252b-122">Example</span></span>**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
><span data-ttu-id="3252b-123">資産タグの値は、1 ~ 36 文字の範囲内である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3252b-123">The asset tag value must contain between 1 and 36 characters.</span></span> <span data-ttu-id="3252b-124">有効な文字は、A-z、a-z、0-9、ピリオド (.)、ハイフン (-) です。</span><span class="sxs-lookup"><span data-stu-id="3252b-124">Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).</span></span>


## <span data-ttu-id="3252b-125">アセットタグの管理</span><span class="sxs-lookup"><span data-stu-id="3252b-125">Managing asset tags</span></span>

<span data-ttu-id="3252b-126">[デバイス情報] の下にある UEFI 設定で既存のアセットタグを表示できます (**コントロールパネル > 回復 > [今すぐ再起動] >** ます)。</span><span class="sxs-lookup"><span data-stu-id="3252b-126">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span></span>

<span data-ttu-id="3252b-127">次の図は、Surface Go でアセットタグツールを実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="3252b-127">The figure below shows the results of running the Asset Tag Tool on Surface Go.</span></span>

![<span data-ttu-id="3252b-128">Surface Asset タグツールが表面移動で実行された結果。</span><span class="sxs-lookup"><span data-stu-id="3252b-128">Results of running Surface Asset Tag tool on Surface Go.</span></span>
](images/assettag-fig1.png)

> **<span data-ttu-id="3252b-129">図 1. </span><span class="sxs-lookup"><span data-stu-id="3252b-129">Figure 1.</span></span>** <span data-ttu-id="3252b-130">Surface の移動で表面のアセットタグツールが実行された結果</span><span class="sxs-lookup"><span data-stu-id="3252b-130">Results of running Surface Asset Tag tool on Surface Go</span></span>

<span data-ttu-id="3252b-131">または、WMI を使って、デバイス上の既存のアセットタグを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="3252b-131">Alternately, you can use WMI to query the existing asset tag on a device:</span></span>

<span data-ttu-id="3252b-132">(Get-WmiObject-query "Select \* from Win32_SystemEnclosure")</span><span class="sxs-lookup"><span data-stu-id="3252b-132">(Get-WmiObject -query “Select \* from Win32_SystemEnclosure”)</span></span>

**<span data-ttu-id="3252b-133">例</span><span class="sxs-lookup"><span data-stu-id="3252b-133">Example</span></span>**

   ```
C:\Windows\System32> (Get-WmiObject -query “Select * from Win32_SystemEnclosure”)
  ```
  
### <span data-ttu-id="3252b-134">PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="3252b-134">Using PowerShell</span></span>

<span data-ttu-id="3252b-135">提案された値を取得してエラーを解釈する方法として、次のスクリプトを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="3252b-135">You can use the script below as a way of getting the proposed value and interpreting any errors.</span></span>

 ```
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim(“\`r\`n”)

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output (“Good Tag = ” + $asset\_tag)  
} else {  
Write-Output (  
“Failure: Code = ” + $asset\_tag\_return\_code +  
“Tag = ” + $asset\_tag +  
“Message = ” + $error\_message)

}
 ```
