---
title: Windows 10 Team 2020 の更新プログラムをインストールする
description: Surface Hub オペレーティング システムの最新の更新プログラムである Windows 10 Team 2020 Update を取得します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/17/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 043c7ed49dafab7e0f3d042f5b98d527ffe0610f
ms.sourcegitcommit: 6252903b28f0c410065eb2515c746f5e9920c652
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "11237217"
---
# Windows 10 Team 2020 の更新プログラムをインストールする 

Windows **10 バージョン 20H2**に基づく新しい Surface Hub オペレーティング システムである Windows 10 Team 2020 Update が、すべての Surface Hub 2S デバイスで利用できます。  

- See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-update.md)

## [Distribution] (配布)

Windows 2020 Update は、次のいずれかの方法で入手できます。

- **Windows Update for Business**.
- **ベア メタル回復 (BMR) イメージ**。 デバイスを Azure Active Directory に参加しているお客様、またはデバイスがインターネットから更新プログラムを受信できないお客様に推奨されるオプションです。 開始するには、「Surface の回復 [イメージをダウンロードする」を参照してください](https://support.microsoft.com/surfacerecoveryimage)。
- **Windows Update。** 可用性は、次の表に示す地域/国によって異なります。

| フェーズ | 国/地域                         | 開始          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ、オーストラリア、カナダ、ベルギー、メキシコ | 2020 年 10 月 27 日  |
| 2     | 英国、日本、スイス、イタリア          | 2020 年 11 月 10 日 |
| 3     | 米国、ドイツ                            | TBD |
| 4     | グローバル                                 | TBD  |

## Windows 10 Team Edition v1703 による Surface Hub 2S のサービス 

すべての地域のお客様は、「Surface Hub 2S のリセットと回復」で説明したように、引き続き Windows Update for Business を使用するか、ベア メタル回復 (BMR) イメージを使用して Surface [Hub 2S](surface-hub-2s-recover-reset.md)デバイスを更新できます。 Windows 10 Team Edition バージョン 1703 の完全なサービス サポートは、2021 年 3 月 16 日まで継続する予定です。


## V1 デバイスのサポート 

Surface Hub 2S デバイス用に最初にリリースされた Windows Windows 10 Team 2020 Update は、間もなく Surface Hub v1 デバイスで利用可能になります。 詳細については [、Surface IT Pro ブログを参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-available-october-27/ba-p/1810739)。
 
## 新機能

Windows 10 Team 2020 Update では、最新の Windows 10 機能と共に、デバイスの展開と管理性が大幅に向上しています。 詳しくは [、Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能に関するページをご覧ください。
 
## 始める前に

Windows 10 Team 2020 更新プログラムをインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。 

**BitLocker キーを手動で保存するには**

1. Surface Hub に USB ドライブを挿入します。
2. Surface Hub で[設定] を **開** き、メッセージが表示されたら管理者の資格情報を入力します。
3. [更新とセキュリティ**の回復&に**  >  **移動します**。
4. **[BitLocker] で、[** 保存] を**選択します**。 BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。

詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。

## 詳細情報

- [既知の問題: Windows 10 Team 2020 Update](surface-hub-2020-update.md)
- [Surface Hub Windows 10 Team 2020 Update の重要な更新プログラム](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/important-updates-on-the-surface-hub-windows-10-team-2020-update/ba-p/1960897)
