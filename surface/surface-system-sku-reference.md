---
title: Surface システム SKU リファレンス
description: すべての Surface デバイスの System Model および System SKU 名の参照を参照してください。
keywords: uefi、configure、firmware、secure、semm、Autopilot
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 04/19/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: bf3fb926c5e66f5f02f921f1c0d4fbe5f016f02d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577047"
---
# <a name="surface-system-sku-reference"></a>Surface システム SKU リファレンス

このドキュメントでは、Surface デバイスを Windows Autopilot に登録したり、PowerShell や WMI を使用して特定のデバイスのマシン状態を確認したりなど、さまざまな IT タスクに使用できる参照を提供します。

システム モデルとシステム SKU は、Surface デバイスの UEFI 層のシステム管理 BIOS (SMBIOS) テーブルに格納される変数です。 同じシステム モデル名を持つデバイスを区別する必要がある場合は常に、システム SKU 名を使用します (LTE Advanced を使用Surface Pro、Surface Proなど)。

| デバイス   | システム モデル | システム SKU       |
| ---------- | ----------- | -------------- |
| Surface 3 WiFI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE AT&T                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE North America                                  | Surface 3        | Surface_3_NAG                    |
| 北米以外の Surface 3 LTE と日本の Y!mobile | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13"                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15"                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13"                                        | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15"                                        | Surface Book 3   | Surface_Book_3_1899
| Surface Go LTE Commercial | System Go | Surface_Go_1825_Commercial |
| Surface Go Consumer                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go 2                                                 | Surface Go 2     | Surface_Go_2_1927                |
| Surface Pro 6 コンシューマー                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 6 商用                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Surface Laptop 2 コンシューマー                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface Laptop 2 商用                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Pro 7+                                               | Surface Pro 7+ | Surface_Pro_7+_1960|
| Surface Pro 7+ LTE                                           | Surface Pro 7+ | Surface_Pro_7+_with_LTE_Advanced_1961|
| Surface Pro 7                 | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro X                 | Surface Pro X    | Surface_Pro_X_1876         |
| Surface ProX と SQ2 プロセッサ                | Surface Pro X    | Surface_Pro_X_H_1876        |
| Surface Laptop 3 13" Intel | Surface Laptop 3 | Surface_Laptop_3_1867:1868 |
| Surface Laptop 3 15" Intel | Surface Laptop 3 | Surface_Laptop_3_1872      |
| Surface Laptop 3 15" AMD   | Surface Laptop 3 | Surface_Laptop_3_1873      | 
| Surface LaptopGo  | Surface LaptopGo | Surface_Laptop_Go_1943      | 
| Surface Laptop 4 13" Intel | Surface Laptop 4 | Surface_Laptop_4_1950:1951 |
| Surface Laptop 4 15" Intel | Surface Laptop 4 | Surface_Laptop_4_1978:1979     |
| Surface Laptop 4 15" AMD   | Surface Laptop 4 | Surface_Laptop_4_1952:1953     | 
| Surface Laptop 4 13" AMD   | Surface Laptop 4 | Surface_Laptop_4_1958:1959    | 
| Surface Hub 2S 50"  | Surface Hub 2S | Surface Hub 2S   | 
| Surface Hub 2S 85"  | Surface Hub 2S | Surface Hub 2S 85   | 

## <a name="examples"></a>例 

**PowerShell を使用した SKU の取得**  
次の PowerShell コマンドを使用して、System SKU 情報を取得します。

 ``` powershell  
gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 
```

**データを使用して SKU を取得システム情報**  
デバイスの System SKU と System Model は、次のページ**システム情報。** これを行うには、次の手順を実行します。

1. [ **スタート] を**選択し、検索 **ボックスに「MSInfo32」** と入力します。  
1. [システム情報]**を選択します**。

**タスク シーケンス WMI 条件での SKU の使用**  
System SKU 情報は、Microsoft Deployment Toolkit (MDT) またはタスク シーケンス WMI Microsoft Endpoint Configuration Managerとして使用できます。

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ``` 

## <a name="learn-more"></a>詳細情報

- [WMI リファレンス](https://docs.microsoft.com/windows/win32/wmisdk/wmi-reference)
- [Windows Autopilot の Surface 登録サポート](surface-autopilot-registration-support.md)
