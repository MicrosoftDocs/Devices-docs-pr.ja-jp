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
# <a name="surface-asset-tag-tool"></a>Surface Asset Tag Tool

Surface Asset Tag はコマンド ライン インターフェイス (CLI) ユーティリティで、Surface デバイスに割り当てられたアセット タグ値を表示、割り当て、変更できます。 この機能は、Surface Pro 3 以降のすべての Surface デバイスで動作します。

## <a name="system-requirements"></a>システム要件

- Surface Pro 3 以降

- UEFI ファームウェア バージョン 3.9.150.0 以降

## <a name="using-surface-asset-tag"></a>Surface アセット タグの使用

Surface アセット タグを実行するには、次のコマンドを実行します。

1. Surface デバイスで[、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703)ダウンロード センターから**Surface Asset Tag.zip**をダウンロードし、zip ファイルを抽出し、AssetTag.exe を目的のフォルダー (この例では C:\\assets) に保存します。

    > [!NOTE]
    > X Surface Pro、ZIP ファイルで AssetTag_x86という**名前**のアプリケーションを使用します。

2. コマンド コンソールを管理者として開き、AssetTag.exeツールへの完全なパスを入力して実行します。

3. Surface を再起動します。

    > [!NOTE]
    > アセット タグを設定した後、WMI に表示される前に 2 回目の再起動が必要になります。

### <a name="asset-tag-tool-commands"></a>アセット タグ ツール のコマンド

次の例では、AssetTag.exeコンピューター (C:\assets) のディレクトリに保存されます。

提案されたアセット タグを取得するには **、AssetTag -g を実行します**。

```console
C:\assets\AssetTag.exe -g
```

提案されたアセット タグをクリアするには **、AssetTag -s を実行します**。

```console
C:\assets\AssetTag.exe -s
```

提案されたアセット タグを設定するには **、AssetTag -s testassettag12 を実行します**。

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>アセット タグの値には、1 ~ 36 文字を含む必要があります。 有効な文字には、A-Z、a-z、0 から 9、ピリオド (.)、ハイフン (-) が含まれます。

## <a name="managing-asset-tags"></a>アセット タグの管理

既存のアセット タグは、[デバイス情報] ([コントロール パネル] > [回復] > [今すぐ再起動>] の UEFI**設定で表示できます**。

次の図は、Surface Go でアセット タグ ツールを実行した結果を示しています。

![Surface Go で Surface アセット タグ ツールを実行した結果。](images/assettag-fig1.png)

> **図 1.** Surface Go で Surface Asset Tag ツールを実行した結果

または、WMI を使用してデバイス上の既存のアセット タグを照会することもできます。

(Get-WmiObject -query "Select * from Win32_SystemEnclosure")

### <a name="example"></a>例

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a>PowerShell を使用する

提案された値を取得し、エラーを解釈する方法として、以下のスクリプトを使用できます。

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
