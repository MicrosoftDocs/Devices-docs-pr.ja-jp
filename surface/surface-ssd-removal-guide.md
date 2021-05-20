---
title: 互換性のある Surface デバイスでの SSD の削除
description: この記事では、認定された IT 技術者を対象に、Surface Laptop 4、Surface Laptop 3、Surface Pro 7+、Surface Pro X、および Surface Laptop Go の SSD の削除と交換に関する推奨ベスト プラクティスについて説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: brrecord
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
- Surface Laptop 4
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 7ba66981c021f1f0a08ebf33aab0a73481111a4d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576907"
---
# <a name="best-practices-for-ssd-removal-from-compatible-surface-devices"></a>互換性のある Surface デバイスからの SSD 削除のベスト プラクティス

> [!IMPORTANT]
> この記事は、エンタープライズ組織でのみ、資格のある IT 技術者による使用を目的とします。 次の互換性のある Surface デバイスの SSD の削除と置き換えで、資格のある IT 技術者が使用する推奨されるベスト プラクティスについて説明します。 

- Surface Pro 7+
- Surface Pro X
- Surface LaptopGo
- Surface Laptop 3
- Surface Laptop 4

> [!WARNING]
> デバイスを開き、デバイス コンポーネントを交換すると、感電、デバイスの損傷、火災、および人的傷害のリスク、その他の危険が発生する可能性があります。  そのような活動を行う場合は、常に注意してください。 [rSSD](https://www.microsoft.com/download/100440)の削除ガイドで示されている安全上の注意事項と手順に従Enterprise。 「rSSD 削除ガイド for Enterprise」で指定されている安全上の注意事項と手順に従えなき場合は、専門的なサポートを受Enterprise。

## <a name="prerequisites"></a>前提条件

> [!IMPORTANT]
> この記事では、「rSSD 削除ガイド for Enterprise」に記載されている一般的な安全に関する注意事項と安全に関するポリシーと手順について理解Enterprise。

## <a name="prepare-for-ssd-removal"></a>SSD の削除の準備 

### <a name="install-the-latest-updates"></a>最新の更新プログラムをインストールする 

開始する前に、最新の更新プログラムがインストールWindowsバージョンがインストールされていることを確認してください。

1.  [セキュリティの**更新設定**  >  ****  >  **開始&に移動**し、[更新プログラムの確認 **] を選択します**。
2. 利用可能なすべての更新プログラムをインストールします。
3. デバイスにアクセスするために必要なパスワードを確認します。  
 
## <a name="manage-bitlocker"></a>[BitLocker の管理] 

> [!NOTE]
> このセクションには、ハード ディスクの暗号化を有効にしたBitLocker推奨事項が含まれています。 詳細については、「回復ガイド[」をBitLockerしてください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)。 

### <a name="if-bitlocker-encryption-is-disabled-during-ssd-removal-and-replacement"></a>SSD のBitLocker交換中に暗号化が無効になっている場合

SSD の削除と交換の前にデバイスを暗号化解除できる場合は、次の手順に従ってデバイスをオフBitLocker。

1.  **[設定]** に「BitLocker」**と入力し、[****管理]** をBitLocker。 
2.  [**電源を切る] をBitLocker**します。 
3.  デバイスの電源をオフにします。 

### <a name="if-bitlocker-encryption-is-enabled-during-ssd-removal-and-replacement"></a>SSD のBitLocker交換中に暗号化が有効になっている場合

SSD の削除と交換の前にデバイスが暗号化されている場合は、次の手順に従って、回復キー BitLockerを生成し、USB ストレージに保存します。

1.  **[設定]** に「BitLocker」**と入力します**。
2. [回復**キーのBitLocker**  > **をBitLockerする] を選択します**。
2.  USB ドライブを挿入します。 
4.  回復キーを USB ストレージに保存します。  
5.  USB ドライブを取り外します。  
6.  デバイスの電源をオフにします。 

## <a name="remove-and-replace-ssd"></a>SSD を削除して置き換える 

1.  [rSSD](https://www.microsoft.com/download/100440)の削除ガイドに含まれているデバイスの適切な手順を使用して SSD を削除Enterprise。 
2.  元の SSD を新しいデバイスに入れ、新しいデバイスを有線インターネット接続に接続します。
3.  新しいデバイスの電源をオンにします。 デバイスは、起動時にファームウェア更新プログラムを通過する可能性があります。  
 
## <a name="after-ssd-removal-and-replacement"></a>SSD の削除と交換の後

### <a name="manage-unencrypted-ssds"></a>暗号化されていない SSD の管理 

転送中に SSD が暗号化されていない場合は、次の手順を実行します。 

1.  [サインイン**オプション パスワード]**  >  **** (左側のキー アイコンで表される) に移動します。  
2.  パスワードを入力し、2 要素認証の保留中の完了 (該当する場合) にサインインします。
3.  完全にサインインした後、[アカウントサインアウトの**** 開始  >  **]**  >  **に移動します**。  
4.  パスワードを使用してサインインし、メッセージが表示されたら、hello Windows PIN を設定します。 
    - デバイスが SSD のBitLockerと交換を容易にするために無効にされ、交換後に BitLocker を有効にする場合は、「BitLocker Manage ****  >  **BitLocker**Resume BitLocker」に  >  **移動**します。  
6.  Microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) を実行して、デバイスの完全な機能を確認します。  
7.  [ライセンス認証Windowsに移動して、ライセンス認証**を設定**  >  **します**。  エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。 
8.  アプリをOfficeして、Officeアカウントに移動し****、エラー メッセージ****  >  **** を確認します。  

### <a name="managing-encrypted-ssds"></a>暗号化された SSD の管理 

> [!NOTE]
> USB ドライブに保存された回復キーを読み取BitLockerデバイスが 2 つ必要です。 

転送中に SSD が暗号化されている場合は、次の手順を実行します。

1.  回復キーを含む USB ドライブBitLocker 2 番目のデバイスに挿入します。 
2.  Bitlocker 回復.txtを含むファイルを開きます。 
3.  元の SSD をBitLocker新しいデバイスの回復キーを手動で入力します。  
4.  BitLocker回復キーを正常に入力したら、[サインイン オプション パスワード] (**** 左側のキー アイコンで表される)  >  **** に移動します。  
5.  パスワードを入力してサインインし、2 要素認証の完了を保留します (該当する場合)。
6.  完全にサインインした後、[アカウントサインアウトの**** 開始  >  **]**  >  **に移動します**。  
7.  パスワードを使用してサインインし、Hello Windowsを設定し、PIN を追加します。 
8.  SSD の取りBitLocker交換を容易にするためにデバイスがBitLocker無効になっている場合、および交換後に BitLocker を有効にする場合は、設定**** BitLocker  >  ****  >  **管理**  >  **** BitLocker Resume BitLocker に移動します。  
9.  **[SDT を実行して](surface-diagnostic-toolkit-for-business-intro.md)**、デバイスの完全な機能を確認します。  
10. ライセンス認証をWindowsするには、[ライセンス認証]**設定**  >  **選択します**。  エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。
11. Office アカウントの状態を確認するには、Office App を**** 開き、[ファイル アカウント]**** に移動してエラー メッセージ  >  **** を確認します。

## <a name="learn-more"></a>詳細情報

- [rSSD 削除ガイド for Enterprise](https://www.microsoft.com/download/100440)
- [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

問題が解決しない場合は、 [Microsoft Community][に移動します](https://answers.microsoft.com/)。