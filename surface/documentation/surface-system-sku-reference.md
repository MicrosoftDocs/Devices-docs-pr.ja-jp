---
title: Surface システム SKU リファレンス
description: このトピックでは、特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステム SKU 名のリファレンスを提供します。
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 29cd47beb855c9b643fca42d91c7b316c374fcca
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835102"
---
# Surface System SKU リファレンス
このドキュメントでは、PowerShell、WMI、および関連ツールを使って、特定のデバイスのコンピューターの状態をすばやく判断するために使用できるシステム SKU 名のリファレンスを提供します。 

システム SKU は、Surface デバイスの UEFI レイヤーのシステム管理 BIOS (SMBIOS) テーブルに格納されている変数 (およびシステムモデルおよび他のユーザーと共に含まれます) です。  "Surface Pro" と "Surface Advanced" という同じシステムモデル名のデバイスを区別する必要がある場合は、必ずシステムの SKU 名を使用します。 

| **デバイス**| **システムモデル** | **システム SKU**|
| --- | ---| --- |
| Surface 3 WiFI                                               | Surface 3        | Surface_3                        |
| &T の Surface 3 LTE                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE 北アメリカ                                  | Surface 3        | Surface_3_NAG                    |
| 北アメリカ以外の Surface 3 LTE と日本の携帯電話 | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13inch                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15inch                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Go コンシューマー                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go コマーシャル                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go 2                                                 | Surface Go 2     | Surface_Go_2_1927                |
| Surface Pro 6 コンシューマー                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 6 商用                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface ノート Pc 2 の利用者                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface ノート Pc 2 商用                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |

## システム SKU 変数の使用 

### PowerShell

     gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 

### システム情報
システム情報で、デバイスのシステム SKU とシステムモデルを見つけることもできます。 
- [ **Start**  >   **MSInfo32**の開始] をクリックします。  

### WMI
システム SKU 変数は、Microsoft 展開ツールキット (MDT) または Microsoft Endpoint Configuration Manager のタスクシーケンス WMI 条件で使うことができます。 以下に例を示します。 

    - WMI 名前空間– Root\WMI
    - WQL クエリ– SystemSKU = "Surface_Pro_1796" の MS_SystemInformation から * を選びます。

 
 
 


