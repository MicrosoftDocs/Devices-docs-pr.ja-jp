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
# <span data-ttu-id="e9983-105">BitLocker キーの保存 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="e9983-105">Save your BitLocker key (Surface Hub)</span></span>


<span data-ttu-id="e9983-106">すべての Microsoft Surface Hub は、自動的に BitLocker ドライブ暗号化ソフトウェアによってセットアップされます。</span><span class="sxs-lookup"><span data-stu-id="e9983-106">Every Microsoft Surface Hub is automatically set up with BitLocker drive encryption software.</span></span> <span data-ttu-id="e9983-107">BitLocker 回復キーはバックアップしておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e9983-107">Microsoft strongly recommends that you make sure you back up your BitLocker recovery keys.</span></span>

<span data-ttu-id="e9983-108">Surface Hub で BitLocker キーを管理するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e9983-108">There are several ways to manage your BitLocker key on the Surface Hub.</span></span>

1.  <span data-ttu-id="e9983-109">Surface Hub をドメインに参加させている場合、キーはデバイスによってドメインでバックアップされ、コンピューター オブジェクト下に保存されます。</span><span class="sxs-lookup"><span data-stu-id="e9983-109">If you’ve joined the Surface Hub to a domain, the device will back up the key on the domain and store it under the computer object.</span></span>

    <span data-ttu-id="e9983-110">デバイスをドメインに参加させた後に BitLocker キーが見つからない場合は、Active Directory スキーマで BitLocker キーのバックアップがサポートされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e9983-110">If you can’t find the BitLocker key after joining the device to a domain, it’s likely that your Active Directory schema doesn’t support BitLocker key backup.</span></span> <span data-ttu-id="e9983-111">スキーマを変更しない場合は、[設定] に移動し、ローカル管理者アカウントの使用手順 (この一覧の後半で詳しく説明します) に従って BitLocker キーを保存できます。</span><span class="sxs-lookup"><span data-stu-id="e9983-111">If you don’t want to change the schema, you can save the BitLocker key by going to Settings and following the procedure for using a local admin account, which is detailed later in this list.</span></span>

2.  <span data-ttu-id="e9983-112">Surface Hub を Azure Active Directory (Azure AD) に参加させている場合、BitLocker キーは、デバイスの参加に使用したアカウントの下で保存されます。</span><span class="sxs-lookup"><span data-stu-id="e9983-112">If you’ve joined the Surface Hub to Azure Active Directory (Azure AD), the BitLocker key will be stored under the account that was used to join the device.</span></span>

3.  <span data-ttu-id="e9983-113">ローカルの管理者アカウントを使用してデバイスを管理している場合は、[**設定**] アプリに移動して、[**セキュリティ**の回復] & に移動して、BitLocker キーを保存でき &gt; **Recovery**ます。</span><span class="sxs-lookup"><span data-stu-id="e9983-113">If you’re using a local admin account to manage the device, you can save the BitLocker key by going to the **Settings** app and navigating to **Update & security** &gt; **Recovery**.</span></span> <span data-ttu-id="e9983-114">USB ドライブを挿入し、BitLocker キーを保存するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9983-114">Insert a USB drive and select the option to save the BitLocker key.</span></span> <span data-ttu-id="e9983-115">キーは、USB ドライブ上のテキスト ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e9983-115">The key will be saved to a text file on the USB drive.</span></span>


## <span data-ttu-id="e9983-116">関連トピック</span><span class="sxs-lookup"><span data-stu-id="e9983-116">Related topics</span></span>

[<span data-ttu-id="e9983-117">Microsoft Surface Hub の管理</span><span class="sxs-lookup"><span data-stu-id="e9983-117">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="e9983-118">Microsoft Surface Hub 管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="e9983-118">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

 

 





