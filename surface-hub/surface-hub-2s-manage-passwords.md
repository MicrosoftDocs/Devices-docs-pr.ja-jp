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
# <span data-ttu-id="779aa-104">デバイス アカウントでのパスワード循環の管理</span><span class="sxs-lookup"><span data-stu-id="779aa-104">Manage device account password rotation</span></span>

<span data-ttu-id="779aa-105">デバイスアカウント情報を手動で更新せずに、デバイスアカウントのパスワードを自動的に変更するように Surface Hub 2S を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="779aa-105">You can configure Surface Hub 2S to automatically change a device account password without requiring you to manually update the device account information.</span></span>

<span data-ttu-id="779aa-106">パスワードのローテーションを有効にした場合、Surface Hub 2S では、7日ごとにパスワードを変更します。</span><span class="sxs-lookup"><span data-stu-id="779aa-106">If you turn on Password Rotation, Surface Hub 2S changes the password every 7 days.</span></span> <span data-ttu-id="779aa-107">自動生成されるパスワードには、大文字と小文字の英字、数字、特殊文字の組み合わせなど、15-32 文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="779aa-107">The automatically generated passwords contain 15-32 characters including  a combination of uppercase and lowercase letters, numbers, and special characters.</span></span>

<span data-ttu-id="779aa-108">会議中にパスワードが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="779aa-108">Passwords do not change during a meeting.</span></span> <span data-ttu-id="779aa-109">Surface Hub の2S がオフになっている場合は、有効になったときにすぐに、または成功するまで10分ごとにパスワードを変更しようとします。</span><span class="sxs-lookup"><span data-stu-id="779aa-109">If Surface Hub 2S is turned off, it attempts to change the password immediately when turned on or every 10 minutes until successful.</span></span>
