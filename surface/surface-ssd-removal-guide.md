---
title: 互換性のある Surface デバイスでの SSD の削除
description: この記事では、認定 IT 技術者を対象に、Surface Laptop 3、Surface Pro X、Surface Laptop Go の SSD の取り外しと交換に関する推奨ベスト プラクティスについて説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 01/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 51ef676e7379f0898d6b601bb08c96002c9e6ace
ms.sourcegitcommit: d4e2a29aa21a911ee55642cd66b4337b89eebdd8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "11270632"
---
# 互換性のある Surface デバイスからの SSD 削除のベスト プラクティス

> [!IMPORTANT]
> この記事は、エンタープライズ組織の認定 IT 技術者のみを対象にしています。 以下の互換性のある Surface デバイスでの SSD の削除と交換に、認定 IT 技術者が使用するための推奨ベスト プラクティスについて説明します。 

- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3

> [!WARNING]
> デバイスを開いてデバイス コンポーネントを交換すると、電気に対する損傷、デバイスの損傷、火災、および個人のけがのリスク、その他の危険が発生する可能性があります。  このような作業を行う場合は、常に注意が必要です。 「エンタープライズ向け [rSSD](https://www.microsoft.com/download/100440)削除ガイド」に示されている安全上の予防措置と手順に従ってください。 「rSSD Removal Guide for Enterprise」で指定されている安全上の予防措置と手順に従できない場合は、プロフェッショナルなサポートを受けてください。

## 前提条件

> [!IMPORTANT]
> この記事では、「rSSD Removal Guide for Enterprise」で説明されている一般的な安全対策と安全に関するポリシーと手順を理解している必要があります。

## SSD の削除を準備する 

### 最新の更新プログラムをインストールする 

開始する前に、Windows のバージョンに最新の更新プログラムがインストールされていることを確認してください。

1.  [スタート設定**の**  >  **更新とセキュリティ**  >  **] に&し**、[更新**プログラムの確認] を選択します**。
2. 利用可能なすべての更新プログラムをインストールします。
3. デバイスへのアクセスに必要なパスワードを確認します。  
 
## [BitLocker の管理] 

> [!NOTE]
> このセクションには、ハード ディスクに対して BitLocker 暗号化を有効にしている組織に関する推奨事項が含まれています。 詳しくは  [、BitLocker 回復ガイドに関するページをご覧ください](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)。 

### SSD の削除と交換中に BitLocker 暗号化が無効になっている場合

SSD の削除と交換の前にデバイスを暗号化解除できる場合は、次の手順に従って BitLocker をオフにします。

1.  [**設定] に****「BitLocker」と入力し、[BitLocker**の**管理] を選択します**。 
2.  **[BitLocker をオフにする] を選択します**。 
3.  デバイスの電源を落とします。 

### SSD の削除と交換中に BitLocker 暗号化が有効になっている場合

SSD の削除と交換の前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。

1.  [**設定] に****「BitLocker」と入力します**。
2. **[BitLocker の BitLocker 生成回復**  > **キーの管理] を選択します**。
2.  USB ドライブを挿入します。 
4.  回復キーを USB ストレージに保存します。  
5.  USB ドライブを取り外します。  
6.  デバイスの電源を落とします。 

## SSD の取り外しと交換 

1.  エンタープライズ向け [rSSD](https://www.microsoft.com/download/100440)削除ガイドに含まれているデバイスに適した手順を使用して、SSD を削除します。 
2.  元の SSD を新しいデバイスに入れ、新しいデバイスをワイヤード (有線) インターネット接続に接続します。
3.  新しいデバイスの電源を入します。 デバイスは起動時にファームウェア更新プログラムを通過する可能性があります。  
 
## SSD の取り外しと交換後

### 暗号化されていない SSD を管理する 

転送中に SSD が暗号化されていない場合は、次の手順を実行します。 

1.  サインイン オプション**パスワード**(左側のキー アイコンで  >  **** 表される) に移動します。  
2.  パスワードを入力し、2 要素認証の保留中の完了にサインインします (該当する場合)。
3.  完全にサインインした後、[アカウントの**サインアウトの**開始]  >  ****  >  **に移動します**。  
4.  パスワードを使用してサインインし、メッセージが表示されたら Windows Hello と PIN を設定します。 
    - デバイスが SSD の削除と交換を容易にするために BitLocker が無効になっている場合に、置換後に BitLocker を有効にする場合は **、BitLocker**の BitLocker の管理  >  **BitLocker**再開  >  **BitLocker**に移動します。  
6.  Microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) を実行して、デバイスの完全な機能を確認します。  
7.  [設定のアクティブ化] に移動して、Windows のライセンス**認証を**  >  **確認します**。  エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。 
8.  アプリをOfficeして、Office アカウントを確認**** し、[ファイル アカウント] に**** 移動して、エラー メッセージ  >  **** を確認します。  

### 暗号化された SSD の管理 

> [!NOTE]
> USB ドライブに保存された BitLocker 回復キーを読み取る 2 番目のデバイスが必要です。 

転送中に SSD が暗号化されている場合は、次の手順を実行します。

1.  BitLocker 回復キーを含む USB ドライブを 2 番目のデバイスに挿入します。 
2.  Bitlocker 回復キーを含む .txt ファイルを開きます。 
3.  元の SSD を含む新しいデバイスで BitLocker 回復キーを手動で入力します。  
4.  BitLocker 回復キーを正常に入力したら、[サインイン オプション**** パスワード] (左側のキー アイコンで表されます)  >  **** に移動します。  
5.  パスワードを入力してサインインし、2 要素認証の完了を保留します (該当する場合)。
6.  完全にサインインした後、[アカウントの**サインアウトの**開始]  >  ****  >  **に移動します**。  
7.  パスワードを使用してサインインし、Windows Hello をセットアップして PIN を追加します。 
8.  デバイスが SSD の削除と交換を容易にするために BitLocker が無効になっている場合、および置換後に BitLocker**** を有効にする場合は、[設定]  >  **BitLocker の [BitLocker**の管理  >  **BitLocker**の再開  >  **BitLocker**の管理] に移動します。  
9.  **[SDT を実行して](surface-diagnostic-toolkit-for-business-intro.md)**、デバイスの完全な機能を確認します。  
10. Windows のライセンス認証を確認するには、[設定のアクティブ化 **] を**  >  **選択します**。  エラー メッセージが表示された場合は、[トラブルシューティング] を **選択します**。
11. Office アカウントの状態を確認するには、Office **App**を開き、[ファイル アカウント] に**** 移動してエラー メッセージ  >  **** を確認します。

## 詳細情報

- [エンタープライズ向け rSSD 削除ガイド](https://www.microsoft.com/download/100440)
- [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

問題が解決しない場合は、 Microsoft コミュニティ [に移動します](https://answers.microsoft.com/)。