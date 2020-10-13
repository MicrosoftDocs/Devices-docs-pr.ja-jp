---
title: システム SKU リファレンス (Surface)
description: システムモデル名とシステム SKU 名のリファレンスを参照してください。
keywords: uefi、構成、ファームウェア、secure、semm
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/12/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: ec1d53a4bdbcaaf6606dcb0e52fc81de92a2a53b
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114545"
---
# システム SKU リファレンス

このドキュメントでは、PowerShell または WMI を使用して、特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステムモデルとシステムの SKU 名のリファレンスを提供します。

システムモデルとシステム SKU は、Surface デバイスの UEFI レイヤーのシステム管理 BIOS (SMBIOS) テーブルに格納されている変数です。 "Surface Pro" と "Surface Advanced" という同じシステムモデル名のデバイスを区別する必要がある場合は、必ずシステムの SKU 名を使用します。

| デバイス   | システムモデル | システム SKU       |
| ---------- | ----------- | -------------- |
| Surface 3 WiFI                                               | Surface 3        | Surface_3                        |
| &T の Surface 3 LTE                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE 北アメリカ                                  | Surface 3        | Surface_3_NAG                    |
| 北米以外の Surface 3 LTE、日本の携帯電話 | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13 "                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15 "                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13 "                                        | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15 "                                        | Surface Book 3   | Surface_Book_3_1899
| Surface Go LTE 商用 | System Go | Surface_Go_1825_Commercial |
| Surface Go コンシューマー                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go コマーシャル                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go 2                                                 | Surface Go 2     | Surface_Go_2_1927                |
| Surface Pro 6 コンシューマー                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 6 商用                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Surface ノート Pc 2 の利用者                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface ノート Pc 2 商用                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Pro 7                 | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro X                 | Surface Pro X    | Surface_Pro_X_1876         |
| Surface Pro X と SQ2 プロセッサ                | Surface Pro X    | Surface_Pro_X_H_1876        |
| Surface ノートパソコン 3 13 "Intel | Surface Laptop 3 | Surface_Laptop_3_1867: 1868 |
| Surface ノートパソコン 3 15 "Intel | Surface Laptop 3 | Surface_Laptop_3_1872      |
| Surface ノートパソコン 3 15 "AMD   | Surface Laptop 3 | Surface_Laptop_3_1873      | 
| Surface のノート Pc の移動  | Surface のノート Pc の移動 | Surface_Laptop_Go_1943      | 

## 例 

**PowerShell を使用して SKU を取得する**  
システムの SKU 情報を取得するには、次の PowerShell コマンドを使用します。

 ``` powershell  
gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 
```

**システム情報を使用して SKU を取得する**  
システム **情報**で、デバイスのシステム SKU とシステムモデルを見つけることもできます。 これを行うためには、次の手順を実行します。

1. [ **スタート**] を選択し、検索ボックスに「 **MSInfo32** 」と入力します。  
1. [ **システム情報**] を選びます。

**タスクシーケンスの WMI 条件で SKU を使用する**  
タスクシーケンス WMI 条件の一部として、Microsoft 展開ツールキット (MDT) または Microsoft Endpoint Configuration Manager のシステム SKU 情報を使用することができます。

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ``` 
