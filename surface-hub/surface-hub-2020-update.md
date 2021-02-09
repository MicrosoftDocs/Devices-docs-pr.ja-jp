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
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 291a2eda0c1fa6e5e2fd2240861c8570d00054df
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319181"
---
# Windows 10 Team 2020 の更新プログラムをインストールする 

Windows **10 バージョン 20H2**に基づく新しい Surface Hub オペレーティング システムである Windows 10 Team 2020 Update が、Surface Hub 2S と元の Surface Hub (v1) で利用できます。 

- See also: [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-team-update-known-issues.md)

## [Distribution] (配布)

Windows 2020 Update は、次のいずれかの方法で入手できます。

- **Windows Update for Business**.
- **ベア メタル回復 (BMR) イメージ**。 デバイスを Azure Active Directory に参加しているユーザー、またはデバイスがインターネットから更新プログラムを受信できない場合に推奨されるオプションです。 開始するには、「Surface の回復 [イメージをダウンロードする」を参照してください](https://support.microsoft.com/surfacerecoveryimage)。
- **Windows Update。** 可用性は、次の表に示す地域/国によって異なります。

| フェーズ | 国/地域                         | 開始          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ、オーストラリア、カナダ、ベルギー、メキシコ | 2020 年 10 月  |
| 2     | 英国、日本、スイス、イタリア          | 2020 年 11 月 |
| 3     | 米国、ドイツ                            | 2021 年 2 月後半 |
| 4     | グローバル                                 | 2021 年 2 月後半 |

## Windows 10 Team Edition バージョン 1703 での Surface Hub のサービス提供 

[Windows 10 Team Edition バージョン 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f)の完全なサービス サポートは、2021 年 3 月 16 日まで継続する予定です。

### 2S デバイス 

すべての地域のお客様は、「Surface Hub 2S のリセットと回復」で説明したように、引き続き Windows Update for Business を使用するか、ベア メタル回復 (BMR) イメージを使用して Surface Hub 2S デバイスを [2020](surface-hub-2s-recover-reset.md)Update に更新できます。

### V1 デバイス 

すべての地域のお客様は、Surface Hub 回復ツールを使って Surface Hub v1 デバイスを 2020 Update に [更新できます](surface-hub-recovery-tool.md)。 これらのデバイスを Windows 10 Team 2020 Update に更新する他の方法は、間もなく利用可能になります。 詳細については [、Surface IT Pro ブログを参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)。
 
## 新機能

Windows 10 Team 2020 Update では、最新の Windows 10 機能と共に、デバイスの展開と管理性が大幅に向上しています。 詳しくは [、Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能に関するページをご覧ください。
 
## 始める前に

Windows 10 Team 2020 Update をインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。 

**BitLocker キーを手動で保存するには**

1. Surface Hub に USB ドライブを挿入します。
2. Surface Hub で[設定] を **開** き、メッセージが表示されたら管理者の資格情報を入力します。
3. [更新とセキュリティの**回復&に**  >  **移動します**。
4. **[BitLocker] で、[** 保存] を**選択します**。 BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。

詳細については [、「BitLocker キーを保存する」を参照してください](save-bitlocker-key-surface-hub.md)。

## 詳細情報

- [Windows 10 Team 2020 更新プログラムの新機能](surface-hub-2020-update-whats-new.md)
- [Windows 10 Team のロールアウトに関する更新プログラム](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)
