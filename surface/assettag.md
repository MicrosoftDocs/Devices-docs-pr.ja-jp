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
# Surface Asset タグツール

Surface Asset Tag は、Surface デバイスの割り当て済みアセットタグ値の表示、割り当て、変更を可能にするコマンドラインインターフェイス (CLI) ユーティリティです。 Surface Pro 3 と、それ以降のすべての Surface デバイスで動作します。

## システム要件

- Surface Pro 3 以降

- UEFI ファームウェアバージョン3.9.150.0 以降

## Surface Asset タグを使用する 

Surface アセットタグを実行するには:

1.  Surface デバイスの場合は、 [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=46703)から [ **surface アセットの Tag.zip**をダウンロードして、zip ファイルを抽出し、AssetTag.exe を目的のフォルダーに保存します (この例では C:\\assets)。

    > [!NOTE]
    > Surface Pro X の場合は、ZIP ファイルで**AssetTag_x86**という名前のアプリケーションを使用します。 

2.  管理者としてコマンドコンソールを開き、ツールへのフルパスを入力して AssetTag.exe を実行します。

3.  Surface を再起動します。

### 資産タグツールのコマンド   
次の例では、AssetTag.exe はローカルコンピューター (C:\ アセット) のディレクトリに保存されています。 

提案されたアセットタグを取得するには、AssetTag-g を実行します。

**例**

   ```
 C:\assets\AssetTag.exe -g
  ```
 
 提案されたアセットタグをクリアするには、AssetTag を実行します。
 
 **例**
 
   ```
C:\assets\AssetTag.exe -s
  ```
提案されたアセットタグを設定するには、AssetTag-s testassettag12 を実行します。

**例**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>資産タグの値は、1 ~ 36 文字の範囲内である必要があります。 有効な文字は、A-z、a-z、0-9、ピリオド (.)、ハイフン (-) です。


## アセットタグの管理

[デバイス情報] の下にある UEFI 設定で既存のアセットタグを表示できます (**コントロールパネル > 回復 > [今すぐ再起動] >** ます)。

次の図は、Surface Go でアセットタグツールを実行した結果を示しています。

![Surface Asset タグツールが表面移動で実行された結果。
](images/assettag-fig1.png)

> **図 1. ** Surface の移動で表面のアセットタグツールが実行された結果

または、WMI を使って、デバイス上の既存のアセットタグを照会することもできます。

(Get-WmiObject-query "Select * from Win32_SystemEnclosure")

**例**

   ```
C:\Windows\System32> (Get-WmiObject -query “Select * from Win32_SystemEnclosure”)
  ```
  
### PowerShell を使用する

提案された値を取得してエラーを解釈する方法として、次のスクリプトを使うことができます。

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
