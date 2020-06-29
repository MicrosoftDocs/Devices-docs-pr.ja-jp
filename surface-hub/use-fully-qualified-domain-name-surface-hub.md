---
title: Surface Hub で完全修飾ドメイン名を使う
description: セットアップの問題、Exchange ActiveSync エラーなどの一般的な問題のトラブルシューティングを行います。
keywords:
- 一般的な問題のトラブルシューティング
- セットアップの問題
- Exchange ActiveSync エラー
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.prod: surface-hub
ms.sitesec: library
ms.openlocfilehash: 79507f5b4bb22b23d1e6c4db6b4aab6ea891d876
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834853"
---
# Skype for Business のドメイン名の構成

Skype for Business サーバーのドメイン名を指定する必要があるシナリオには、次のようなものがあります。
- **複数の DNS サフィックス** - 1 つ以上のサーバーの DNS サフィックスが Skype for Business のサインイン アドレス (SIP) のサフィックスと一致しないなど、Skype for Business のインフラストラクチャに関連のない名前空間がある場合。  
- **Skype for Business のサフィックスと Exchange のサフィックスが異なる** - Skype for Business のサインイン アドレスのサフィックスが、デバイス アカウントに使用される Exchange アドレスのサフィックスと異なる場合。
- **証明書の操作**-オンプレミスの Skype for business サーバーを使用する大企業は、独自のルート証明機関 (CA) で証明書を使用するのが一般的です。 CA のドメインが Skype for Business サーバーのドメインと異なるため、証明書が信頼されず、サインインが失敗することがよくあります。  信頼関係を設定するには、Skype が証明書のドメイン名を知っている必要があります。 通常、企業はグループ ポリシーを使って FQDN を Skype のデスクトップにプッシュしますが、Surface Hub ではグループ ポリシーはサポートされていません。

**Skype for Business サーバーのドメイン名を構成するには**</br>
1. Surface Hub で、**[設定]** を開きます。
2. **[Surface Hub]** をクリックし、**[通話とオーディオ]** をクリックします。 
3. **[Skype for Business の構成]** の **[ドメイン名の構成]** をクリックします。 
4. Skype for Business サーバーのドメイン名を入力し、**[OK]** をクリックします。 
   > [!TIP]
   > 複数のドメイン名をコンマで区切って入力することもできます。 <br> 例: lync.com、outlook.com、lync.glbdns.microsoft.com

    ![Skype for Business FQDN を設定に追加する](images/system-settings-add-fqdn.png)
