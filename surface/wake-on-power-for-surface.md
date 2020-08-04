---
title: Power Surface でスリープ解除を有効にする方法
ms.author: v-todmc
author: mccoybot
ms.date: 7/30/2020
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121602
ms.reviewer: johnk@cadencepreferred.com
description: Surface デバイス用のスリープ解除機能を有効または無効にする方法について説明します。
keywords: update、deploy、driver、wol、wake on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 272c19baedb295abac08e90012246e453b88f42f
ms.sourcegitcommit: 6fd7008992503db9ae1f56654aa80110348924d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "10903396"
---
# Surface デバイス での Wake On Power の使用

Surface デバイスは、机の外にいるときにオフにすることができます。または、休止モードに設定してバッテリーを節約できます。 これらのデバイスの管理性を向上させるために、電源をオンにすると、互換性のある Surface デバイスは、電源に再接続したときに自動的に起動します。 Wake on Power を構成するには、surface Enterprise 管理モード (SEMM) で Surface UEFI コンフィギュレーターまたは UEFI Manager のいずれかを使用できます。

電源投入時の機能は、以下のデバイスで利用できます。

- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X 

## 概要と前提条件

Surface UEFI コンフィギュレーターでは、ターゲットデバイスに配布するために、個々の UEFI 設定を Windows Installer の .msi パッケージに保存することができます。 

> [!NOTE]
> この記事では、SEMM の使い方を理解していることを前提としています。 詳細については、「 [Surface Enterprise 管理モード (SEMM)](surface-enterprise-management-mode.md)ドキュメント」を参照してください。

## Power on Wake を有効にするには

1.  [SURFACE UEFI コンフィギュレーター](https://www.microsoft.com/download/confirmation.aspx?id=46703)の最新バージョンをダウンロードします。
2.  管理者として Surface デバイスにサインインして、 **SURFACE UEFI コンフィギュレーター**を開き、[ **surface Devices**]、[**次へ**] の順に選択します。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="[Surface デバイス] を選択し、[次へ] を選択します。":::
3.  [**スタート**] を選択し、[**構成パッケージ**] の [**作成**] を選択します。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="[構成パッケージの作成] を選びます。":::
4.  [**証明書の保護**] を選択し、証明書の .pfx ファイルを追加します。 
5. パスワードを入力し、[**次へ**] を選択し、必要に応じて**パスワード保護**を追加して、[**次へ**] を選択します。
6.  [**ターゲットにするサーフェスの種類を選択**してください] ページで、必要に応じてターゲットデバイスを選択します。 たとえば、[ **Surface Pro 7**] を選びます。
7.  [**高度な機能**] ページで、[**電源によるスリープ解除**] を選択し、機能を **[オン**] に設定して、[**次へ**] を選びます。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="[電源をオンにする] を選択し、[オン] に設定します。"::: 
8.  [**成功**] ページで [**終了**] を選びます。

    > [!NOTE]
    > 初めてデバイスに設定を提供する場合は、証明書の拇印の最後の2文字も入力するように求められます。 
9.  .Msi パッケージを保存します。 

## MSI パッケージを適用する 

Microsoft Endpoint Configuration Manager などのソフトウェア配布ツールを使用して、ネットワーク上のデバイスに MSI パッケージを適用することができます。 この手順では、ローカルコンピューターにパッケージをインストールする手順について説明します。 

1.  管理者特権のコマンドプロンプトで、.msi ファイルの完全なパスを入力して .msi パッケージを実行します。 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  [**警告**] ダイアログボックスで、[ **OK]** を選択するか、必要に応じて BitLocker を無効にします。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="[OK] を選択するか、必要に応じて BitLocker を無効にします。":::
3.  [ようこそ] ページで、[**次**へ] を選んでパッケージを実行し、新しく構成された UEFI 設定を適用します。

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="[ようこそ] ページにある [次へ] を選びます。":::
4.  デバイスを再起動します。 

電源がオンになっています。 設定をテストするには、デバイスの電源を切って、電源を切り、電源を再接続します。 デバイスが自動的に起動します。 

## 参考資料

詳細については、次の記事を参照してください。 

- [Surface エンタープライズ管理モード](surface-enterprise-management-mode.md)
- [Surface デバイス用の Wake on LAN](wake-on-lan-for-surface-devices.md)

問題が解決しない場合は、 [Microsoft コミュニティ](https://answers.microsoft.com/)に移動します。