---
title: デバイス アカウントでのパスワード循環の管理
description: PowerShell を使用して Surface Hub のオンプレミスアカウントを構成する方法について説明します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: ea445588fe2242e3200284a39fdb4a3a8473f94a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836638"
---
# デバイス アカウントでのパスワード循環の管理

デバイスアカウント情報を手動で更新せずに、デバイスアカウントのパスワードを自動的に変更するように Surface Hub 2S を構成することができます。

パスワードのローテーションを有効にした場合、Surface Hub 2S では、7日ごとにパスワードを変更します。 自動生成されるパスワードには、大文字と小文字の英字、数字、特殊文字の組み合わせなど、15-32 文字が含まれています。

会議中にパスワードが変更されることはありません。 Surface Hub の2S がオフになっている場合は、有効になったときにすぐに、または成功するまで10分ごとにパスワードを変更しようとします。
