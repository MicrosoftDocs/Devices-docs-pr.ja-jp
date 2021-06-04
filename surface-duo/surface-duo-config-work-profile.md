---
title: Surface Surface の Android Enterprise Work Profile を構成する
description: この記事では、Surface Surface の仕事用プロファイルを設定する方法について説明します。
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/25/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 393844a4e4f0f06f16d11d1313ec9aacfa109d57
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326211"
---
# Surface Surface の Android Enterprise Work Profile を構成する

BYOD 展開を対象として、仕事用プロファイルは、仕事用アプリとデータ用の別の領域を、仕事用アプリとデータ用に別の領域を提供します。従業員が個人のアプリやデータにデバイスを使用するのを防ぐことなく、組織はデータ、アプリ、およびセキュリティ ポリシーを完全に制御できます。

###  <a name="set-up-android-enterprise-work-profile"></a>Android Enterprise Work Profile のセットアップ

仕事用プロファイルを使用して、ユーザーが所有する Android デバイス上の企業データとアプリを管理します。 既定では、個人所有の仕事用プロファイル デバイスの登録が有効になっているので、それ以上管理者の構成は必要とされません。  

**エンタープライズワーク プロファイルを有効にするには:**

- エンドポイント マネージャーで、[Android デバイスの登録 **]** を選択し、[仕事用プロファイルを持つ  >  ****  >  ******個人用デバイス] を選択します**。
<br><br>
 ![エンタープライズワーク プロファイルを有効にする](images/enroll-start.png)

 
**Android Enterprise Work Profile を使用して Surface の携帯電話にサインインする**

1. Google Play ストアからポータル サイト アプリをインストールし、Microsoft の会社または学校のアカウントでサインインします。<br><br>
![Surface の合間にサインインする](images/duo-wp-1.png)
 
2. [Access セットアップ] ページで、[開始] を選択 **します**。<br><br>
![Begin](images/duo-wp-2.png)

3. プライバシー ページの情報を確認し、[続行] を選択 **します**。<br><br>
 ![続行](images/duo-wp-3.png)
<br><br>
 ![[続行] を選択](images/duo-wp-4.png)
 
4. 作業プロファイルのセットアップが完了したら、[続行] **を選択して** デバイスのライセンス認証と登録を行います。<br><br>
 ![Select continue to activate and register the device](images/duo-wp-5.png)

5. **[続行]** を選びます。<br><br>
 ![もう一度 [続行] を選択する](images/duo-wp-6.png)

6. 作業プロファイルをアクティブ化した後、[続行] **を選択して** デバイス設定を更新します。 この例では、仕事用プロファイルで MDM 設定を適用して、より強力な 6 桁の英数字パスワードを要求します。 <br><br>

     ![英数字パスワードの例](images/duo-wp-7.png)<br><br>
7. [ **解決] を** 選択して必要な認証を入力し、[続行] **を選択して** ワーク プロファイルのセットアップを完了します。 <br><br>
     ![[続行] を選択してセットアップを完了する](images/duo-wp-8.png)<br><br>
     ![セットアップの完了](images/duo-wp-9.png)<br><br>

##  <a name="learn-more"></a>詳細情報

- [Android Enterprise の仕事用プロファイル デバイスの登録を設定する](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)

