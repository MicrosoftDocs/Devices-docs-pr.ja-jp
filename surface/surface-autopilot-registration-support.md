---
title: Windows 自動操縦の表面登録サポート
description: この記事では、Microsoft サポートに対して自動操縦登録リクエストを提出するための要件について説明します。
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
ms.openlocfilehash: 9a308edb37cc2cfd99490acad16bd2ae6a4d458a
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016479"
---
# Windows 自動操縦の表面登録サポート

Windows 自動操縦用 Surface デバイスの登録プロセスが簡素化され、Microsoft サポートから利用できるようになりました。 2020年9月から、お客様と Microsoft Cloud Solution Providers (Csp) は、Microsoft サポートに要求を送信して、Surface デバイスを登録できます。 このページでは、次のようにサポートされている自動操縦登録シナリオの要件について説明します。
 

- **Surface Device 自動操縦登録**。 Surface デバイスを Windows 自動操縦に登録するための要求を送信します。
- **Surface Device ハードウェアハッシュ要求。** Microsoft サポートにリクエストを送信して、お客様や Csp が Microsoft Intune または Microsoft パートナーセンター経由でデバイスを自己登録するために使用できるハードウェアハッシュを提供します。
- **Surface Device 自動操縦登録解除。** Windows 自動操縦からデバイスを削除する要求を送信します。通常は、デバイスのサポート終了シナリオで使われます。

登録要求を Microsoft サポートに提出する前に収集する必要がある情報の詳細については、次の表を参照してください。
 
**表 1. 自動操縦登録要求に必要な情報**
 

| 必要な情報                   | 説明                                                                                                                                                                                                                                                                                    | 自動操縦の登録 | ハードウェアハッシュ要求 | パイロット<br>登録解除 |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **Azure Active Directory テナント ID**   | Azure Active Directory テナント ID は、組織名またはドメインとは異なるグローバル一意識別子 (GUID) です。<br> <br>テナント ID を検索するに [は、ここで](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)Azure Portal にサインインします。 | Y                      | N                     | Y                           |
| **Azure Active Directory ドメイン名** | 最上位レベルのドメイン名。たとえば、contoso.com のようになります。                                                                                                                                                                                                                                          | Y                      | N                     | Y                           |
| **所有権の証明**                 | 元の販売請求書または請求書を PDF 形式でアップロードして、所有権の証明を確認します。 スクリーンショットは受け入れられません。<br> <br>売上請求書または請求書には、次の情報を含める必要があります。<br>デバイスのシリアル番号。<br>会社名。                                                           | Y                      | Y                     | Y                           |
| **デバイスのシリアル番号**              | 各デバイスのシリアル番号を新しい行に CSV 形式で Excel ファイルをアップロードします。                                                                                                                                                                                                                  | Y                      | Y                     | Y                           |

 

## サポートリクエストを送信する

  [![Get 自動操縦 (Surface の登録サポート)(images/autopilot-reg-support-surface.png)](https://support.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## 詳細情報

- [Windows Autopilot と Surface デバイス](windows-autopilot-and-surface-devices.md)
- [Windows Autopilot を使用して、Intune での Windows デバイスを登録する](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [Windows Autopilot の概要](https://docs.microsoft.com/mem/autopilot/windows-autopilot)

 
 
 

