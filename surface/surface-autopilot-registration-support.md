---
title: Windows Autopilot の Surface 登録サポート
description: この記事では、Autopilot 登録要求を Microsoft サポートに提出する場合の要件について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/14/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: b31cacad5a744dcb29fc3dd2822c656d528fcd40
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304840"
---
# Windows Autopilot の Surface 登録サポート

Windows Autopilot 展開用に Surface デバイスを登録するプロセスが簡略化されました。Microsoft サポートから利用できます。 2020 年 9 月から、お客様と Microsoft クラウド ソリューション プロバイダー (CSP) は、Microsoft サポートに要求を送信することで Surface デバイスを登録できます。 このページでは、次のサポートされている Autopilot 登録シナリオの要件の概要を示します。
 
- **Surface Device Autopilot Registration**. Surface デバイスを Windows Autopilot に登録する要求を送信します。
- **Surface デバイスのハードウェア ハッシュ要求。** Microsoft サポートに要求を送信して、Microsoft Intune または Microsoft パートナー センターを介してデバイスを自己登録するために顧客または CSP が使用できるハードウェア ハッシュを提供します。
- **Surface Device Autopilot Deregistration。** Windows Autopilot からデバイスを削除する要求を送信します。通常は、デバイスの寿命のシナリオで使用されます。

Microsoft サポートに登録要求を提出する前に収集する必要がある情報の詳細については、次の表を参照してください。 すべての Surface デバイスの正式なシステム モデル名については [、Surface System SKU リファレンスを参照してください](surface-system-sku-reference.md)。
 
**表 1. Autopilot 登録要求に必要な情報**
 

| 必要な情報                   | 説明                                                                                                                                                                                                                                                                                    | Autopilot Registration | ハードウェア ハッシュ要求 | Autopilot<br>登録解除 |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **Azure Active Directory テナント ID**   | Azure Active Directory テナント ID は、組織名またはドメインとは異なるグローバル一意識別子 (GUID) です。<br> <br>テナント ID を見つけるには、ここで Azure Portal にサインイン [します](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)。 | Y                      | N                     | Y                           |
| **Azure Active Directory ドメイン名** | トップ レベルのドメイン名。たとえば、contoso.com。                                                                                                                                                                                                                                          | Y                      | N                     | Y                           |
| **所有権の証明**                 | 元の販売請求書または請求書を PDF 形式でアップロードして、所有権の証明を確認します。 スクリーンショットは受け付けされません。<br> <br>販売請求書には、次のものが含まれる必要があります。<br>デバイスのシリアル番号。<br>会社名。                                                           | Y                      | Y                     | Y                           |
| **デバイスのシリアル番号**              | 新しい行に各デバイスのシリアル番号を含む CSV 形式の Excel ファイルをアップロードします。                                                                                                                                                                                                                  | Y                      | Y                     | Y                           |

 

##  <a name="submit-support-requests"></a>サポート要求を送信する

  [![Get Autopilot Registration Support for Surface](images/autopilot-reg-support-surface.png)](https://prod.support.services.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
##  <a name="learn-more"></a>詳細情報

- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md)
- [Windows Autopilot を使用して、Intune での Windows デバイスを登録する](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [Windows Autopilot の概要](https://docs.microsoft.com/mem/autopilot/windows-autopilot)
- [Surface システム SKU リファレンス](surface-system-sku-reference.md)

 
 
 

