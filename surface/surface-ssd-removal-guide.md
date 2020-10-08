---
title: 互換性のある Surface デバイスでの SSD の削除
description: SSD を1つの Surface デバイスから別の機種に移動する方法を説明します。
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 10/7/2020
ms.reviewer: johnk
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 00109e4e1bb3873fc2914b2044f58e6fa3b6c211
ms.sourcegitcommit: d0a5c8fb2b37eb11858c7be4549e55c4b36d7471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2020
ms.locfileid: "11104809"
---
# 互換性のある Surface デバイスからの SSD の削除に関するベストプラクティス

> [!IMPORTANT]
> この記事は、組織内で限定された IT 技術者による使用を目的としています。 Surface ノート Pc 3 または Surface Pro X でのみ、お勧めの IT 技術者が Ssd を削除して交換する際に推奨されるベストプラクティスについて説明します。 

> [!WARNING]
> デバイスを開いたり、デバイスコンポーネントを交換したりすると、感電、デバイスの損傷、火災、および個人の傷害のリスク、およびその他の危険を生じる可能性があります。  このようなアクティビティを行うときは、常に注意してください。 [エンタープライズ向けの Rssd の削除ガイド](https://www.microsoft.com/download/100440)に記載されている安全性に関する注意事項と手順に従います。 「Enterprise 向けの rSSD の削除ガイド」で指定されている安全性の予防策と手順に従うことができない場合は、プロフェッショナルサポートを受けることをお勧めします。

## 前提条件

> [!IMPORTANT]
> この記事では、「rSSD の削除ガイド (エンタープライズ向け)」に記載されている一般的な安全対策と安全性のポリシーと手順について理解していることを前提としています。

## SSD の削除の準備 

### 最新の更新プログラムをインストールする 

作業を開始する前に、使用している Windows のバージョンに最新の更新プログラムが含まれていることを確認してください。

1.  [**スタート**  >  ]**設定**  >  の**更新 & セキュリティ**] に移動して、[**更新プログラムの確認**] を選びます。 利用可能な更新プログラムをすべてインストールします。 
2. 利用可能な更新プログラムをすべてインストールします。
3. デバイスへのアクセスに必要なパスワードがあることを確認します。  
 
## [BitLocker の管理] 

> [!NOTE]
> このセクションでは、ハードディスクの BitLocker 暗号化を有効にしている組織向けの推奨事項について説明します。 詳細については、「 [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)」を参照してください。 

### SSD の削除中に BitLocker 暗号化が無効になっている場合

SSD を削除して交換する前に、デバイスが暗号化されていない場合は、次の手順に従って BitLocker をオフにします。

1.  [ **設定**] で、「 **bitlocker**」と入力し、[ **bitlocker の管理**] を選択します。 
2.  [ **Bitlocker をオフにする**] を選びます。 
3.  デバイスの電源を切ります。 

### SSD の削除および交換中に BitLocker 暗号化が有効になっている場合

SSD の削除と交換前にデバイスが暗号化されている場合は、次の手順に従って BitLocker 回復キーを生成し、USB ストレージに保存します。

1.  [ **設定**] で、「 **Bitlocker**」と入力します。
2. [ **Bitlocker の管理**] を選び  > **Generate Bitlocker Recovery Key**ます。
2.  USB ドライブを挿入します。 
3.  回復キーを USB ストレージに保存します。  
4.  USB ドライブを取り外します。  
5.  デバイスの電源を切ります。 

## SSD を削除して置き換える 

1.  「 [Enterprise 用の Rssd の削除ガイド](https://www.microsoft.com/download/100440)」の手順に従って、SSD を削除します。 
2. 元の SSD を新しいデバイスに取り付け、新しいデバイスを有線インターネット接続に接続します。
2.  新しいデバイスの電源を入れます。 デバイスは、起動時にファームウェアの更新プログラムを実行することがあります。  
 
## SSD の削除と交換後

### 暗号化されていない Ssd の管理 

転送中に SSD が暗号化されていない場合は、次の手順に従います。 

1.  [**サインインオプション**  >  ] の**パスワード**に移動します (左側に鍵のアイコンが表示されます)。  
2.  パスワードを入力し、2段階認証が完了していない状態でサインインします (該当する場合)。
3.  完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。  
4.  パスワードを使用してもう一度サインインし、メッセージが表示されたら、Windows Hello と PIN をセットアップします。 
    - デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしていて、置換後に bitlocker を有効にする場合は、「 **bitlocker**  >  **管理**bitlocker  >  **Resume bitlocker**」を参照してください。  
6.  Microsoft Surface Diagnostics ツールキット for Business (SDT) を実行して、デバイスのすべての機能を確認します。  
7.  「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。  エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。 
8.  Office**アプリ**を開いて office アカウントを確認し、[**ファイル**アカウント] に移動して、  >  **Account**エラーメッセージがあるかどうかを確認します。  

### 暗号化された SSDs の管理 

> [!NOTE]
> USB ドライブに保存されている BitLocker 回復キーを読み取るには、2番目のデバイスが必要です。 

転送中に SSD が暗号化されたままになっている場合は、次の手順に従います。

1.  Bitlocker 回復キーが格納されている USB ドライブを2番目のデバイスに挿入します。 
2.  Bitlocker 回復キーが含まれている .txt ファイルを開きます。 
3.  元の SSD を含む新しいデバイスに Bitlocker 回復キーを手動で入力します。  
4.  BitLocker 回復キーを正常に入力したら、[**サインインオプション**  >  **]** (左側にあるキーアイコンで表示されます) に移動します。  
5.  パスワードを入力してサインインします。2段階認証が完了していません (該当する場合)。
6.  完全にサインインしたら、[アカウントの**開始**] に移動  >  **Account**  >  **Sign out**します。  
7.  パスワードを使用してもう一度サインインし、Windows Hello をセットアップして PIN を追加します。 
8.  デバイスが、SSD の削除と交換を容易にするために bitlocker を無効にしている場合、置換後に bitlocker を有効にするには、[**設定**] の [bitlocker の管理] bitlocker  >  **Bitlocker**  >  **Manage Bitlocker**  >  **Resume bitlocker を選び**ます。  
9.  すべてのデバイスの機能を確認するには、 **SDT** を実行します。  
10. 「**設定**のアクティブ化」に移動して、Windows のライセンス認証を確認  >  **Activation**します。  エラーメッセージが表示された場合は、[ **トラブルシューティング**] を選びます。
11. Office アカウントの状態を確認するには、 **office アプリ**を開き、[**ファイル**アカウント] に移動して  >  **Account**エラーメッセージを確認します。

## 詳細情報 

詳細については、次の記事を参照してください。

- [rSSD のエンタープライズ向けの削除ガイド](https://www.microsoft.com/download/100440)
- [BitLocker 回復ガイド](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

問題が解決しない場合は、 [Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。