---
title: BitLocker キーの保存 (Surface Hub)
description: すべての Microsoft Surface Hub は、自動的に BitLocker ドライブ暗号化ソフトウェアによってセットアップされます。 BitLocker 回復キーはバックアップしておくことを強くお勧めします。
ms.assetid: E11E4AB6-B13E-4ACA-BCE1-4EDC9987E4F2
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, BitLocker, Bitlocker 回復キー, Bitlocker recovery keys
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73efa418fa80ef90a643d4fb4c457280ab982b38
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836462"
---
# BitLocker キーの保存 (Surface Hub)


すべての Microsoft Surface Hub は、自動的に BitLocker ドライブ暗号化ソフトウェアによってセットアップされます。 BitLocker 回復キーはバックアップしておくことを強くお勧めします。

Surface Hub で BitLocker キーを管理するには、いくつかの方法があります。

1.  Surface Hub をドメインに参加させている場合、キーはデバイスによってドメインでバックアップされ、コンピューター オブジェクト下に保存されます。

    デバイスをドメインに参加させた後に BitLocker キーが見つからない場合は、Active Directory スキーマで BitLocker キーのバックアップがサポートされていない可能性があります。 スキーマを変更しない場合は、[設定] に移動し、ローカル管理者アカウントの使用手順 (この一覧の後半で詳しく説明します) に従って BitLocker キーを保存できます。

2.  Surface Hub を Azure Active Directory (Azure AD) に参加させている場合、BitLocker キーは、デバイスの参加に使用したアカウントの下で保存されます。

3.  ローカルの管理者アカウントを使用してデバイスを管理している場合は、[**設定**] アプリに移動して、[**セキュリティ**の回復] & に移動して、BitLocker キーを保存でき &gt; **Recovery**ます。 USB ドライブを挿入し、BitLocker キーを保存するオプションを選択します。 キーは、USB ドライブ上のテキスト ファイルに保存されます。


##  <a name="related-topics"></a>関連トピック

[Microsoft Surface Hub の管理](manage-surface-hub.md)

[Microsoft Surface Hub 管理者ガイド](surface-hub-administrators-guide.md)

 

 





