---
title: システム SKU リファレンス (Surface)
description: システム モデルとシステム SKU 名のリファレンスを参照してください。
keywords: uefi, 構成, ファームウェア, セキュア, semm
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 1/15/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 2140faf346229842bffc4f9348041f4667b94686
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271371"
---
# システム SKU リファレンス

このドキュメントでは、PowerShell または WMI を使用して特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステム モデルとシステム SKU 名の参照を提供します。

システム モデルとシステム SKU は、Surface デバイスの UEFI レイヤーのシステム管理 BIOS (SMBIOS) テーブルに格納される変数です。 Surface Pro や LTE Advanced を搭載した Surface Pro など、同じシステム モデル名を持つデバイスを区別する必要がある場合は常に、システム SKU 名を使います。

| デバイス   | システム モデル | システム SKU       |
| ---------- | ----------- | -------------- |
| Surface 3 WiFI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE AT&T                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE 北米                                  | Surface 3        | Surface_3_NAG                    |
| 北米以外の Surface 3 LTE と日本の Y!mobile | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13"                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15"                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13"                                        | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15"                                        | Surface Book 3   | Surface_Book_3_1899
| Surface Go LTE Commercial | System Go | Surface_Go_1825_Commercial |
| Surface Go コンシューマー                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go 2                                                 | Surface Go 2     | Surface_Go_2_1927                |
| Surface Pro 6 コンシューマー                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 6 Commercial                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Surface Laptop 2 コンシューマー                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface Laptop 2 Commercial                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Pro 7+                                               | Surface Pro 7+ | Surface_Pro_7+_1960|
| Surface Pro 7+ LTE                                           | Surface Pro 7+ | Surface_Pro_7 + _with_LTE_Advanced_1961|
| Surface Pro 7                 | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro X                 | Surface Pro X    | Surface_Pro_X_1876         |
| Sq2 プロセッサを搭載した Surface Pro X                | Surface Pro X    | Surface_Pro_X_H_1876        |
| Surface Laptop 3 13" Intel | Surface Laptop 3 | Surface_Laptop_3_1867:1868 |
| Surface Laptop 3 15" Intel | Surface Laptop 3 | Surface_Laptop_3_1872      |
| Surface Laptop 3 15" AMD   | Surface Laptop 3 | Surface_Laptop_3_1873      | 
| Surface Laptop Go  | Surface Laptop Go | Surface_Laptop_Go_1943      | 

## 例 

**PowerShell を使用して SKU を取得する**  
次の PowerShell コマンドを使用して、システム SKU 情報を取得します。

 ``` powershell  
gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 
```

**システム情報を使用して SKU を取得する**  
システム情報には、デバイスのシステム SKU とシステム モデルも **表示されます**。 これを行うには、次の手順を実行します。

1. [ **スタート]** を選択し、検索ボックスに **「MSInfo32」** と入力します。  
1. [システム **情報] を選択します**。

**タスク シーケンス WMI 条件で SKU を使用する**  
タスク シーケンス WMI 条件の一部として、Microsoft Deployment Toolkit (MDT) または Microsoft Endpoint Configuration Manager のシステム SKU 情報を使用できます。

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ``` 
