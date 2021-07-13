---
title: Surface Asset Tag Tool
description: このトピックでは、Surface アセット タグ ツールの使い方について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: carlol
ms.date: 06/29/2021
manager: laurawi
ms.openlocfilehash: b130f6b0bf52dc1c3a28231a2330cae51a5ef44a
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643833"
---
# <a name="surface-asset-tag-tool"></a><span data-ttu-id="3e20a-103">Surface Asset Tag Tool</span><span class="sxs-lookup"><span data-stu-id="3e20a-103">Surface Asset Tag Tool</span></span>

<span data-ttu-id="3e20a-104">Surface Asset Tag はコマンド ライン インターフェイス (CLI) ユーティリティで、Surface デバイスに割り当てられたアセット タグ値を表示、割り当て、変更できます。</span><span class="sxs-lookup"><span data-stu-id="3e20a-104">Surface Asset Tag is a command line interface (CLI) utility that allows you to view, assign, and modify an assigned asset tag value for Surface devices.</span></span> <span data-ttu-id="3e20a-105">この機能は、Surface Pro 3 以降のすべての Surface デバイスで動作します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-105">It works on Surface Pro 3 and all newer Surface devices.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="3e20a-106">システム要件</span><span class="sxs-lookup"><span data-stu-id="3e20a-106">System requirements</span></span>

- <span data-ttu-id="3e20a-107">Surface Pro 3 以降</span><span class="sxs-lookup"><span data-stu-id="3e20a-107">Surface Pro 3 or later</span></span>

- <span data-ttu-id="3e20a-108">UEFI ファームウェア バージョン 3.9.150.0 以降</span><span class="sxs-lookup"><span data-stu-id="3e20a-108">UEFI firmware version 3.9.150.0 or later</span></span>

## <a name="using-surface-asset-tag"></a><span data-ttu-id="3e20a-109">Surface アセット タグの使用</span><span class="sxs-lookup"><span data-stu-id="3e20a-109">Using Surface Asset Tag</span></span>

<span data-ttu-id="3e20a-110">Surface アセット タグを実行するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-110">To run Surface Asset Tag:</span></span>

1. <span data-ttu-id="3e20a-111">Surface デバイスで[、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703)ダウンロード センターから**Surface Asset Tag.zip**をダウンロードし、zip ファイルを抽出し、AssetTag.exe を目的のフォルダー (この例では C:\\assets) に保存します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-111">On the Surface device, download **Surface Asset Tag.zip** from the [Microsoft Download  Center](https://www.microsoft.com/download/details.aspx?id=46703),  extract the zip file, and save AssetTag.exe in desired folder (in  this example, C:\\assets).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3e20a-112">X Surface Pro、ZIP ファイルで AssetTag_x86という**名前**のアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-112">For Surface Pro X, use the application named **AssetTag_x86**  in the ZIP file.</span></span>

2. <span data-ttu-id="3e20a-113">コマンド コンソールを管理者として開き、AssetTag.exeツールへの完全なパスを入力して実行します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-113">Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.</span></span>

3. <span data-ttu-id="3e20a-114">Surface を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3e20a-114">Restart Surface.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3e20a-115">アセット タグを設定した後、WMI に表示される前に 2 回目の再起動が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3e20a-115">After setting the asset tag, a second reboot is required before it appears in WMI.</span></span>

### <a name="asset-tag-tool-commands"></a><span data-ttu-id="3e20a-116">アセット タグ ツール のコマンド</span><span class="sxs-lookup"><span data-stu-id="3e20a-116">Asset Tag tool commands</span></span>

<span data-ttu-id="3e20a-117">次の例では、AssetTag.exeコンピューター (C:\assets) のディレクトリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3e20a-117">In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).</span></span>

<span data-ttu-id="3e20a-118">提案されたアセット タグを取得するには **、AssetTag -g を実行します**。</span><span class="sxs-lookup"><span data-stu-id="3e20a-118">To get the proposed asset tag, run **AssetTag -g**:</span></span>

```console
C:\assets\AssetTag.exe -g
```

<span data-ttu-id="3e20a-119">提案されたアセット タグをクリアするには **、AssetTag -s を実行します**。</span><span class="sxs-lookup"><span data-stu-id="3e20a-119">To clear the proposed asset tag, run **AssetTag -s**:</span></span>

```console
C:\assets\AssetTag.exe -s
```

<span data-ttu-id="3e20a-120">提案されたアセット タグを設定するには **、AssetTag -s testassettag12 を実行します**。</span><span class="sxs-lookup"><span data-stu-id="3e20a-120">To set the proposed asset tag, run **AssetTag -s testassettag12**:</span></span>

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
><span data-ttu-id="3e20a-121">アセット タグの値には、1 ~ 36 文字を含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e20a-121">The asset tag value must contain between 1 and 36 characters.</span></span> <span data-ttu-id="3e20a-122">有効な文字には、A-Z、a-z、0 から 9、ピリオド (.)、ハイフン (-) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3e20a-122">Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).</span></span>

## <a name="managing-asset-tags"></a><span data-ttu-id="3e20a-123">アセット タグの管理</span><span class="sxs-lookup"><span data-stu-id="3e20a-123">Managing asset tags</span></span>

<span data-ttu-id="3e20a-124">既存のアセット タグは、[デバイス情報] ([コントロール パネル] > [回復] > [今すぐ再起動>] の UEFI**設定で表示できます**。</span><span class="sxs-lookup"><span data-stu-id="3e20a-124">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span></span>

<span data-ttu-id="3e20a-125">次の図は、Surface Go でアセット タグ ツールを実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="3e20a-125">The figure below shows the results of running the Asset Tag Tool on Surface Go.</span></span>

![Surface Go で Surface アセット タグ ツールを実行した結果。](images/assettag-fig1.png)

> **<span data-ttu-id="3e20a-127&quot;>図 1.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3e20a-127&quot;>Figure 1.</span></span>** <span data-ttu-id=&quot;3e20a-128&quot;>Surface Go で Surface Asset Tag ツールを実行した結果</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3e20a-128&quot;>Results of running Surface Asset Tag tool on Surface Go</span></span>

<span data-ttu-id=&quot;3e20a-129&quot;>または、WMI を使用してデバイス上の既存のアセット タグを照会することもできます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3e20a-129&quot;>Alternately, you can use WMI to query the existing asset tag on a device:</span></span>

<span data-ttu-id=&quot;3e20a-130&quot;>(Get-WmiObject -query &quot;Select \* from Win32_SystemEnclosure")</span><span class="sxs-lookup"><span data-stu-id="3e20a-130">(Get-WmiObject -query "Select \* from Win32_SystemEnclosure")</span></span>

### <a name="example"></a><span data-ttu-id="3e20a-131">例</span><span class="sxs-lookup"><span data-stu-id="3e20a-131">Example</span></span>

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a><span data-ttu-id="3e20a-132">PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="3e20a-132">Using PowerShell</span></span>

<span data-ttu-id="3e20a-133">提案された値を取得し、エラーを解釈する方法として、以下のスクリプトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e20a-133">You can use the script below as a way of getting the proposed value and interpreting any errors.</span></span>

```powershell
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim("\`r\`n")

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output ("Good Tag = " + $asset\_tag)  
} else {  
Write-Output (  
"Failure: Code = " + $asset\_tag\_return\_code +  
"Tag = " + $asset\_tag +  
"Message = " + $error\_message)

}
```
