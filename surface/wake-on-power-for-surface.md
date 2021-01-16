---
title: Surface の電源でスリープ解除を有効にする方法
ms.author: v-todmc
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121602
ms.reviewer: hachidan
description: Surface デバイスの電源でスリープ解除を有効または無効にする方法について説明します。
keywords: 更新, 展開, ドライバー, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.date: 01/15/2021
ms.openlocfilehash: 6ad359861f6af29c567bf0fbf26878ec15c7c642
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271561"
---
# Surface デバイス での Wake On Power の使用

Surface デバイスは、デスクから離れた状態で電源をオフにしたり、休止モードに設定してバッテリ残量を節約できます。 これらのデバイスの管理性を向上させるために、Wake on Power を使用すると、互換性のある Surface デバイスが電源に再接続されると自動的に起動します。 電源でのスリープ解除を構成するには、Surface UEFI コンフィエーターまたは UEFI マネージャーを使用して Surface Enterprise Management Mode (SEMM) を使用できます。

電源でのスリープ解除機能は、次のデバイスで利用できます。

- Surface Pro 7+
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Laptop Go
- Surface Pro X 


## 概要と前提条件

Surface UEFI Configurator を使うと、ターゲット デバイスに配布するために、Windows インストーラー .msi パッケージに個々の UEFI 設定を保存できます。 

> [!NOTE]
> この記事では、SEMM の使い方を知っている必要があります。 詳細については [、Surface Enterprise Management Mode (SEMM) のドキュメントを参照](surface-enterprise-management-mode.md) してください。

## 電源でスリープ解除を有効にするには

1.  Surface UEFI コンフィエーター [の最新バージョンをダウンロードします](https://www.microsoft.com/download/confirmation.aspx?id=46703)。
2.  管理者として Surface デバイスにサインインし **、Surface UEFI**コンフィケーターを開き **、Surface デバイス**を選択して、[次へ] を選択 **します**。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="[Surface デバイス] を選択し、[次へ] を選択します。":::
3.  [**スタート] を**選択し、[構成パッケージ]**で [作成****] を選択します**。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="[構成パッケージの作成] を選択します。":::
4.  [ **証明書の保護]** を選択し、証明書の .pfx ファイルを追加します。 
5. パスワードを入力し、[ **次へ] を選択し**、必要に応じて **パスワード**保護を追加して、[次へ] を選択 **します**。
6.  [ターゲット **とする Surface の種類の選択** ] ページで、必要に応じてターゲット デバイスを選択します。 たとえば **、Surface Pro 7 を選択します**。
7.  [高度 **な機能] ページ** で、[ **電源でスリープ**解除] を選択し、機能を **[オン**] に設定して、[次へ] を選択 **します**。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="[電源でスリープ解除] を選択し、[オン] に設定します。"::: 
8.  [成功] **ページで** 、[終了] を **選択します**。

    > [!NOTE]
    > 初めて設定をデバイスに提供する場合は、証明書の拇印の最後の 2 文字も入力するように求めるメッセージが表示されます。 
9.  .msi パッケージを保存します。 

## MSI パッケージを適用する 

Microsoft Endpoint Configuration Manager などのソフトウェア配布ツールを使用して、ネットワーク上のデバイスに MSI パッケージを適用できます。 この手順には、ローカル コンピューターにパッケージをインストールする手順が含まれています。 

1.  管理者特権でのコマンド プロンプトで、.msi ファイルの完全パスを入力して .msi パッケージを実行します。 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  [警告 **] ダイアログ ボックス** で **、[OK]** を選択するか、必要に応じて BitLocker を無効にします。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="[OK] を選択するか、必要に応じて BitLocker を無効にします。":::
3.  [ようこそ] ページで、[次へ] **を選択** してパッケージを実行し、新しく構成した UEFI 設定を適用します。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="ウェルカム ページの 1 つで、[次へ] を選択します。":::
4.  デバイスを再起動します。 

電源でスリープ解除が構成されます。 設定をテストするには、デバイスをオフにし、電源を切り、電源を再接続します。 デバイスが自動的に起動します。 

## 参考資料

詳細については、次の記事を参照してください。 

- [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
- [Surface デバイスの LAN でのスリープ解除](wake-on-lan-for-surface-devices.md)

問題が解決しない場合は、 Microsoft コミュニティ [に移動します](https://answers.microsoft.com/)。