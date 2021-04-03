---
title: Windows 10 Team 2020 の更新プログラムをインストールする
description: Surface Hub オペレーティング システムの Windows 10 Team 2020 Update の最新の更新プログラムを取得します。
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
ms.openlocfilehash: 4d68f751bd15ef6529bcd16a6305d8c682970747
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470415"
---
# <a name="install-windows-10-team-2020-update"></a>Windows 10 Team 2020 の更新プログラムをインストールする 

新しい Surface Hub オペレーティング システム **である Windows 10 Team 2020 Update は、Windows 10**バージョン 20H2 に基づいて、Surface Hub 2S と元の Surface Hub (v1) で利用できます。 

- 「既知の [問題: Windows 10 Team 2020 Update」も参照してください。](surface-hub-2020-team-update-known-issues.md)

## <a name="distribution"></a>[Distribution] (配布)

Windows 2020 Update は、次のいずれかの方法で取得できます。

- **Windows Update for Business**.
- **ベア メタル回復 (BMR) イメージ**。 デバイスを Azure Active Directory に参加したり、デバイスがインターネットから更新プログラムを受け取るのを許可しない場合に推奨されるオプションです。 開始するには [、「Surface の回復イメージをダウンロードする」を参照してください](https://support.microsoft.com/surfacerecoveryimage)。
- **Windows Update。** 可用性は、次の表に示す地域/国によって異なります。

| フェーズ | 国/地域                         | 開始          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ, オーストラリア, カナダ, ベルギー, メキシコ | 2020 年 10 月  |
| 2     | 英国、日本、スイス、イタリア          | 2020 年 11 月 |
| 3     | ドイツ、オランダ                   | 2021 年 2 月下旬 |
| 4     | グローバル                                 | 2021 年 3 月上旬 |

## <a name="servicing-surface-hubs-with-windows-10-team-edition-version-1703"></a>Windows 10 Team Edition バージョン 1703 での Surface Hubs のサービス 

[Windows 10 Team Edition バージョン 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f)のフル サービス サポートは、2021 年 3 月 16 日まで継続する予定です。

### <a name="2s-devices"></a>2S デバイス 

すべての地域のお客様は、「Surface Hub [2S](surface-hub-2s-recover-reset.md)のリセットと回復」で説明したように、Surface Hub 2S デバイスを Windows Update、Windows Update for Business、またはベア メタル回復 (BMR) イメージを使用して 2020 Update に更新できます。

### <a name="v1-devices"></a>V1 デバイス 

すべての地域のお客様は、Windows Update、Windows Update for Business、または Surface Hub 回復ツールを使用して、Surface Hub v1 デバイスを 2020 Update に [更新できます](surface-hub-recovery-tool.md)。 更新プログラムを受信するには、KB5000749 をインストールする必要があります。 詳細については [、「Surface IT Pro ブログ」を参照してください](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-hub-v1-status/ba-p/2118371)。
 
## <a name="whats-new"></a>新機能

Windows 10 Team 2020 Update は、最新の Windows 10 機能と共に、デバイスの展開と管理性に大きな改善を提供します。 詳細については [、「Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md)の新機能」を参照してください。
 
## <a name="before-you-begin"></a>始める前に

Windows 10 Team 2020 Update をインストールする前に、デバイスに関連付けられている BitLocker キーを保存してください。 

**BitLocker キーを手動で保存するには**

1. Surface Hub に USB ドライブを挿入します。
2. Surface Hub で [設定] を **開** き、プロンプトが表示されたら管理者資格情報を入力します。
3. [セキュリティ回復の**更新&に**  >  **移動します**。
4. **[BitLocker] で**、[保存]**を選択します**。 BitLocker キーは、USB ドライブ上のテキスト ファイルに保存されます。

詳細については [、「Save your BitLocker key 」を参照してください](save-bitlocker-key-surface-hub.md)。

## <a name="learn-more"></a>詳細情報

- [Windows 10 Team 2020 更新プログラムの新機能](surface-hub-2020-update-whats-new.md)
- [Windows 10 Team のロールアウトに関する更新プログラム](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-february-status/ba-p/2118369)
