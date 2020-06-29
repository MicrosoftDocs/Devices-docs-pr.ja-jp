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
# <span data-ttu-id="ed205-106">Skype for Business のドメイン名の構成</span><span class="sxs-lookup"><span data-stu-id="ed205-106">Configure domain name for Skype for Business</span></span>

<span data-ttu-id="ed205-107">Skype for Business サーバーのドメイン名を指定する必要があるシナリオには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="ed205-107">There are a few scenarios where you need to specify the domain name of your Skype for Business server:</span></span>
- <span data-ttu-id="ed205-108">**複数の DNS サフィックス** - 1 つ以上のサーバーの DNS サフィックスが Skype for Business のサインイン アドレス (SIP) のサフィックスと一致しないなど、Skype for Business のインフラストラクチャに関連のない名前空間がある場合。</span><span class="sxs-lookup"><span data-stu-id="ed205-108">**Multiple DNS suffixes** - When your Skype for Business infrastructure has disjointed namespaces such that one or more servers have a DNS suffix that doesn't match the suffix of the sign-in address (SIP) for Skype for Business.</span></span>  
- <span data-ttu-id="ed205-109">**Skype for Business のサフィックスと Exchange のサフィックスが異なる** - Skype for Business のサインイン アドレスのサフィックスが、デバイス アカウントに使用される Exchange アドレスのサフィックスと異なる場合。</span><span class="sxs-lookup"><span data-stu-id="ed205-109">**Skype for Business and Exchange suffixes are different** - When the suffix of the sign-in address for Skype for Business differs from the suffix of the Exchange address used for the device account.</span></span>
- <span data-ttu-id="ed205-110">**証明書の操作**-オンプレミスの Skype for business サーバーを使用する大企業は、独自のルート証明機関 (CA) で証明書を使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ed205-110">**Working with certificates** - Large organizations with on-premises Skype for Business servers commonly use certificates with their own root certificate authority (CA).</span></span> <span data-ttu-id="ed205-111">CA のドメインが Skype for Business サーバーのドメインと異なるため、証明書が信頼されず、サインインが失敗することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="ed205-111">It is common for the CA domain to be different than the domain of the Skype for Business server which causes the certificate to not be trusted, and sign-in fails.</span></span>  <span data-ttu-id="ed205-112">信頼関係を設定するには、Skype が証明書のドメイン名を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed205-112">Skype needs to know the domain name of the certificate in order to set up a trust relationship.</span></span> <span data-ttu-id="ed205-113">通常、企業はグループ ポリシーを使って FQDN を Skype のデスクトップにプッシュしますが、Surface Hub ではグループ ポリシーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ed205-113">Enterprises typically use Group Policy to push this out to Skype desktop, but Group Policy is not supported on Surface Hub.</span></span>

**<span data-ttu-id="ed205-114">Skype for Business サーバーのドメイン名を構成するには</span><span class="sxs-lookup"><span data-stu-id="ed205-114">To configure the domain name for your Skype for Business server</span></span>**</br>
1. <span data-ttu-id="ed205-115">Surface Hub で、**[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ed205-115">On Surface Hub, open **Settings**.</span></span>
2. <span data-ttu-id="ed205-116">**[Surface Hub]** をクリックし、**[通話とオーディオ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed205-116">Click **Surface Hub**, and then click **Calling & Audio**.</span></span> 
3. <span data-ttu-id="ed205-117">**[Skype for Business の構成]** の **[ドメイン名の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed205-117">Under **Skype for Business configuration**, click **Configure domain name**.</span></span> 
4. <span data-ttu-id="ed205-118">Skype for Business サーバーのドメイン名を入力し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed205-118">Type the domain name for your Skype for Business server, and then click **Ok**.</span></span> 
   > [!TIP]
   > <span data-ttu-id="ed205-119">複数のドメイン名をコンマで区切って入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed205-119">You can type multiple domain names, separated by commas.</span></span> <br> <span data-ttu-id="ed205-120">例: lync.com、outlook.com、lync.glbdns.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="ed205-120">For example: lync.com, outlook.com, lync.glbdns.microsoft.com</span></span>

    ![Skype for Business FQDN を設定に追加する](images/system-settings-add-fqdn.png)
