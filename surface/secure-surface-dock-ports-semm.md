---
title: Surface Enterprise 管理モード (SEMM) での Secure Surface Dock 2 ポート
description: このドキュメントでは、surface Dock 3、surface Pc 3、Surface Pro 7 など、互換性のある Surface デバイスに接続されている場合に、Surface Dock 2 の UEFI ポート設定を構成する方法について説明します。
ms.assetid: 2808a8be-e2d4-4cb6-bd53-9d10c0d3e1d6
ms.reviewer: ''
manager: laurawi
keywords: 一般的な問題のトラブルシューティング, セットアップの問題
ms.prod: w10
ms.mktglfcycl: support
ms.sitesec: library
ms.pagetype: surfacehub
author: v-miegge
ms.author: jesko
ms.topic: article
ms.date: 06/08/2020
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: de16d76581926a90585b2c6beb2a7bf3b7a695bc
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834342"
---
# <span data-ttu-id="ee91f-104">Surface Enterprise 管理モード (SEMM) での Secure Surface Dock 2 ポート</span><span class="sxs-lookup"><span data-stu-id="ee91f-104">Secure Surface Dock 2 ports with Surface Enterprise Management Mode (SEMM)</span></span>

## <span data-ttu-id="ee91f-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="ee91f-105">Introduction</span></span>

<span data-ttu-id="ee91f-106">Surface Enterprise 管理モード (SEMM) を使用すると、IT 管理者は、Windows インストーラー構成パッケージで UEFI 設定を構成することによって Surface Dock 2 ポートをセキュリティで保護し、管理することができます。MSI ファイル) 企業環境全体で互換性のある Surface デバイスに展開されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-106">Surface Enterprise Management Mode (SEMM) enables IT admins to secure and manage Surface Dock 2 ports by configuring UEFI settings in a Windows installer configuration package (.MSI file) deployed to compatible Surface devices across a corporate environment.</span></span>

### <span data-ttu-id="ee91f-107">サポートされるデバイス</span><span class="sxs-lookup"><span data-stu-id="ee91f-107">Supported devices</span></span>

<span data-ttu-id="ee91f-108">SEMM での surface Dock 2 の管理は、surface Book 3、Surface ラップトップ3、Surface Pro 7 に接続されているドックで利用できます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-108">Managing Surface Dock 2 with SEMM is available for docks connected to Surface Book 3, Surface Laptop 3, and Surface Pro 7.</span></span> <span data-ttu-id="ee91f-109">これらの互換性のある Surface デバイスは、一般的に**ホストデバイス**と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-109">These compatible Surface devices are commonly referred to as **host devices**.</span></span> <span data-ttu-id="ee91f-110">ホストデバイスが**認証**されているか、**認証**されていないかに基づいて、パッケージがデバイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-110">A package is applied to host devices based on if a host device is **authenticated** or **unauthenticated**.</span></span> <span data-ttu-id="ee91f-111">構成済みの設定は、IT 管理者である、カメラなどの他の組み込みのペリフェラルと同じように、Surface Dock 2 を管理するために、ホストデバイス上の UEFI レイヤーに存在します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-111">Configured settings reside in the UEFI layer on host devices enabling you — the IT admin — to manage Surface Dock 2 just like any other built-in peripheral such as the camera.</span></span>

>[!NOTE]
><span data-ttu-id="ee91f-112">Surface Dock 2 のポートを管理できるのは、Dock が次の互換性のあるデバイスのいずれかに接続されている場合のみです。 Surface Book 3、Surface Pc 3、Surface Pro 7。</span><span class="sxs-lookup"><span data-stu-id="ee91f-112">You can manage Surface Dock 2 ports only when the dock is connected to one of the following compatible devices:  Surface Book 3, Surface Laptop 3, and Surface Pro 7.</span></span> <span data-ttu-id="ee91f-113">UEFI 認証されたポリシー設定を受け取らないデバイスは、本質的に認証されていないデバイスです。</span><span class="sxs-lookup"><span data-stu-id="ee91f-113">Any device that doesn't receive the UEFI Authenticated policy settings is inherently an unauthenticated device.</span></span>

### <span data-ttu-id="ee91f-114">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ee91f-114">Scenarios</span></span>

<span data-ttu-id="ee91f-115">Surface Dock 2 を会社のホストデバイスにサインインした許可されたユーザーに制限すると、データ保護の別のレイヤーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-115">Restricting Surface Dock 2 to authorized persons signed into a corporate host device provides another layer of data protection.</span></span> <span data-ttu-id="ee91f-116">Surface Dock 2 のロックダウン機能は、厳密なセキュリティプロトコルのコンプライアンスを維持しながら、Dock の機能と生産性の向上を望む、安全性の高い環境では、特定のユーザーにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="ee91f-116">This ability to lock down Surface Dock 2 is critical for specific customers in highly secure environments who want the functionality and productivity benefits of the dock while maintaining compliance with strict security protocols.</span></span> <span data-ttu-id="ee91f-117">Surface Dock 2 での SEMM の使用は、セキュリティ上の理由から USB ポートをロックする必要があるお客様に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ee91f-117">We anticipate SEMM used with Surface Dock 2 will be particularly useful in open offices and shared spaces especially for customers who want to lock USB ports for security reasons.</span></span> <span data-ttu-id="ee91f-118">ビデオのデモについては、「 [Surface Dock 2 用の Semm](https://youtu.be/VLV19ISvq_s)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee91f-118">For a video demo, check out [SEMM for Surface Dock 2](https://youtu.be/VLV19ISvq_s).</span></span>

## <span data-ttu-id="ee91f-119">Surface Dock 2 の UEFI 設定を構成して展開する</span><span class="sxs-lookup"><span data-stu-id="ee91f-119">Configuring and deploying UEFI settings for Surface Dock 2</span></span>

<span data-ttu-id="ee91f-120">このセクションでは、次のタスクを実行するためのステップバイステップのガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-120">This section provides step-by-step guidance for the following tasks:</span></span>

1. <span data-ttu-id="ee91f-121">[**SURFACE UEFI コンフィギュレーター**](https://www.microsoft.com/download/details.aspx?id=46703)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ee91f-121">Install [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
1. <span data-ttu-id="ee91f-122">公開キー証明書を作成または取得します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-122">Create or obtain public key certificates.</span></span>
1. <span data-ttu-id="ee91f-123">を作成します。MSI 構成パッケージ。</span><span class="sxs-lookup"><span data-stu-id="ee91f-123">Create an .MSI configuration package.</span></span>
   1. <span data-ttu-id="ee91f-124">証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-124">Add your certificates.</span></span>
   1. <span data-ttu-id="ee91f-125">Surface Dock 2 デバイスの16桁の RN 番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-125">Enter the 16-digit RN number for your Surface Dock 2 devices.</span></span>
   1. <span data-ttu-id="ee91f-126">UEFI 設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-126">Configure UEFI settings.</span></span>
1. <span data-ttu-id="ee91f-127">構成パッケージをビルドし、対象サーフェスデバイス (Surface Book 3、Surface ノート Pc 3、Surface Pro 7) に適用します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-127">Build and apply the configuration package to targeted Surface devices (Surface Book 3, Surface Laptop 3, or Surface Pro 7.)</span></span>

>[!NOTE]
><span data-ttu-id="ee91f-128">**ランダム番号 (RN)** は、工場でプロビジョニングされ、ドックの下側に小さい形式で印刷される一意の16桁の16進数コード識別子です。</span><span class="sxs-lookup"><span data-stu-id="ee91f-128">The **Random Number (RN)** is a unique 16-digit hex code identifier which is provisioned at the factory, and printed in small type on the underside of the dock.</span></span> <span data-ttu-id="ee91f-129">RN は、電子的には読み取れないため、ほとんどのシリアル番号とは異なります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-129">The RN differs from most serial numbers in that it can't be read electronically.</span></span> <span data-ttu-id="ee91f-130">これにより、所有権の証明が主に、デバイスに物理的にアクセスしたときに、RN を読み取ることによってのみ確立されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-130">This ensures proof of ownership is primarily established only by reading the RN when physically accessing the device.</span></span> <span data-ttu-id="ee91f-131">この RN は、購入トランザクション中に取得されることもあり、Microsoft インベントリシステムで記録されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-131">The RN may also be obtained during the purchase transaction and is recorded in Microsoft inventory systems.</span></span>

### <span data-ttu-id="ee91f-132">SEMM および Surface の UEFI コンフィギュレーターをインストールする</span><span class="sxs-lookup"><span data-stu-id="ee91f-132">Install SEMM and Surface UEFI Configurator</span></span>

<span data-ttu-id="ee91f-133">**SurfaceUEFI_Configurator_v2.71.139.0.msi**を実行して semm をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ee91f-133">Install SEMM by running **SurfaceUEFI_Configurator_v2.71.139.0.msi**.</span></span> <span data-ttu-id="ee91f-134">これはスタンドアロンのインストーラーであり、Surface Dock 2 の構成パッケージを作成して配布するために必要なすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-134">This is a standalone installer and contains everything you need to create and distribute configuration packages for Surface Dock 2.</span></span>

- <span data-ttu-id="ee91f-135">Surface [Tools](https://www.microsoft.com/en-us/download/details.aspx?id=46703)から**Surface の UEFI コンフィギュレーター**をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ee91f-135">Download **Surface UEFI Configurator** from [Surface Tools for IT](https://www.microsoft.com/en-us/download/details.aspx?id=46703).</span></span>

## <span data-ttu-id="ee91f-136">公開キー証明書を作成する</span><span class="sxs-lookup"><span data-stu-id="ee91f-136">Create public key certificates</span></span>

<span data-ttu-id="ee91f-137">このセクションでは、Surface Dock 2 のポートを管理するために必要な証明書を作成するための仕様を示します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-137">This section provides specifications for creating the certificates needed to manage ports for Surface Dock 2.</span></span>

### <span data-ttu-id="ee91f-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="ee91f-138">Prerequisites</span></span>

<span data-ttu-id="ee91f-139">この記事では、サードパーティプロバイダーから証明書を取得するか、PKI 証明書サービスの専門知識を既に持っており、独自の技術情報を作成することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-139">This article assumes that you either obtain certificates from a third-party provider or you already have expertise in PKI certificate services and know how to create your own.</span></span>  <span data-ttu-id="ee91f-140">「 [Surface Enterprise 管理モード (SEMM)](https://docs.microsoft.com/surface/surface-enterprise-management-mode)ドキュメント」で説明されているように、証明書を作成する際の一般的な推奨事項について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-140">You should be familiar with and follow the general recommendations for creating certificates as described in [Surface Enterprise Management Mode (SEMM)](https://docs.microsoft.com/surface/surface-enterprise-management-mode) documentation, with one exception.</span></span> <span data-ttu-id="ee91f-141">このページに記載されている証明書には、 **Dock 証明機関**の場合は30年、**ホスト認証証明書**には20年の有効期限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ee91f-141">The certificates documented on this page require expiration terms of 30 years for the **Dock Certificate Authority**, and 20 years for the **Host Authentication Certificate**.</span></span>

<span data-ttu-id="ee91f-142">詳細については、「[証明書サービスのアーキテクチャ](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture)に関するドキュメント」を参照してください。 [windows server 2019](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)内の適切な章、または Microsoft Press から提供されている[Windows Server 2008 PKI および証明書のセキュリティ](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ee91f-142">For more information, see [Certificate Services Architecture](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture) documentation and review the appropriate chapters in [Windows Server 2019 Inside Out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277), or [Windows Server 2008 PKI and Certificate Security](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788) available from Microsoft Press.</span></span>

### <span data-ttu-id="ee91f-143">ルートとホストの証明書の要件</span><span class="sxs-lookup"><span data-stu-id="ee91f-143">Root and host certificate requirements</span></span>

<span data-ttu-id="ee91f-144">構成パッケージを作成する前に、Surface Dock 2 の所有権を認証する公開キー証明書を用意して、デバイスのライフサイクル中に所有権のその後の変更を容易にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-144">Prior to creating the configuration package, you need to prepare public key certificates that authenticate ownership of Surface Dock 2 and facilitate any subsequent changes in ownership during the device lifecycle.</span></span> <span data-ttu-id="ee91f-145">ホストとプロビジョニングの証明書では、**クライアント認証の拡張キー使用法 (EKU) オブジェクト識別子 (oid)** と呼ばれているものとして、eku id を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-145">The host and provisioning certificates require entering EKU IDs otherwise known as **Client Authentication Enhanced Key Usage (EKU) object identifiers (OIDs)**.</span></span>

<span data-ttu-id="ee91f-146">必要な EKU 値が、表1と表2に一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-146">The required EKU values are listed in Table 1 and Table 2.</span></span>

#### <span data-ttu-id="ee91f-147">表 1.</span><span class="sxs-lookup"><span data-stu-id="ee91f-147">Table 1.</span></span> <span data-ttu-id="ee91f-148">ルートとドックの証明書の要件</span><span class="sxs-lookup"><span data-stu-id="ee91f-148">Root and Dock Certificate requirements</span></span>

|<span data-ttu-id="ee91f-149">証明書</span><span class="sxs-lookup"><span data-stu-id="ee91f-149">Certificate</span></span>|<span data-ttu-id="ee91f-150">アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="ee91f-150">Algorithm</span></span>|<span data-ttu-id="ee91f-151">説明</span><span class="sxs-lookup"><span data-stu-id="ee91f-151">Description</span></span>|<span data-ttu-id="ee91f-152">有効期限</span><span class="sxs-lookup"><span data-stu-id="ee91f-152">Expiration</span></span>|<span data-ttu-id="ee91f-153">EKU OID</span><span class="sxs-lookup"><span data-stu-id="ee91f-153">EKU OID</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="ee91f-154">ルート証明機関</span><span class="sxs-lookup"><span data-stu-id="ee91f-154">Root Certificate Authority</span></span>|<span data-ttu-id="ee91f-155">ECDSA_P384</span><span class="sxs-lookup"><span data-stu-id="ee91f-155">ECDSA_P384</span></span>|<span data-ttu-id="ee91f-156">-384 ビット素数楕円曲線デジタル署名アルゴリズム (ECDSA) を含むルート証明書</span><span class="sxs-lookup"><span data-stu-id="ee91f-156">- Root certificate with 384-bit prime elliptic curve digital signature algorithm (ECDSA)</span></span><br><span data-ttu-id="ee91f-157">-SHA 256 キー使用法:</span><span class="sxs-lookup"><span data-stu-id="ee91f-157">- SHA 256 Key Usage:</span></span><br><span data-ttu-id="ee91f-158">CERT_DIGITAL_SIGNATURE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee91f-158">CERT_DIGITAL_SIGNATURE_KEY_USAGE</span></span><br><span data-ttu-id="ee91f-159">-CERT_KEY_CERT_SIGN_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee91f-159">- CERT_KEY_CERT_SIGN_KEY_USAGE</span></span><br><span data-ttu-id="ee91f-160">CERT_CRL_SIGN_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee91f-160">CERT_CRL_SIGN_KEY_USAGE</span></span>|<span data-ttu-id="ee91f-161">30年</span><span class="sxs-lookup"><span data-stu-id="ee91f-161">30 years</span></span>|<span data-ttu-id="ee91f-162">なし</span><span class="sxs-lookup"><span data-stu-id="ee91f-162">N/A</span></span>
|<span data-ttu-id="ee91f-163">ドック証明機関</span><span class="sxs-lookup"><span data-stu-id="ee91f-163">Dock Certificate Authority</span></span>|<span data-ttu-id="ee91f-164">ECC P256 curve</span><span class="sxs-lookup"><span data-stu-id="ee91f-164">ECC P256 curve</span></span>|<span data-ttu-id="ee91f-165">-256 ビットの楕円曲線暗号 (ECC) でのホスト証明書</span><span class="sxs-lookup"><span data-stu-id="ee91f-165">- Host certificate with 256-bit elliptic-curve cryptography (ECC)</span></span><br><span data-ttu-id="ee91f-166">-SHA 256 キー使用法:</span><span class="sxs-lookup"><span data-stu-id="ee91f-166">- SHA 256 Key Usage:</span></span><br><span data-ttu-id="ee91f-167">CERT_KEY_CERT_SIGN_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee91f-167">CERT_KEY_CERT_SIGN_KEY_USAGE</span></span><br><span data-ttu-id="ee91f-168">-Path Length 制約 = 0</span><span class="sxs-lookup"><span data-stu-id="ee91f-168">- Path Length Constraint = 0</span></span>|<span data-ttu-id="ee91f-169">20年</span><span class="sxs-lookup"><span data-stu-id="ee91f-169">20 years</span></span>|<span data-ttu-id="ee91f-170">1.3.6.1.4.1.311.76.9.21.2</span><span class="sxs-lookup"><span data-stu-id="ee91f-170">1.3.6.1.4.1.311.76.9.21.2</span></span><br><span data-ttu-id="ee91f-171">1.3.6.1.4.1.311.76.9.21.3</span><span class="sxs-lookup"><span data-stu-id="ee91f-171">1.3.6.1.4.1.311.76.9.21.3</span></span>|

   >[!NOTE]
   ><span data-ttu-id="ee91f-172">Dock CA は、p7b ファイルとしてエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-172">The dock CA must be exported as a .p7b file.</span></span>

### <span data-ttu-id="ee91f-173">管理証明書の要件のプロビジョニング</span><span class="sxs-lookup"><span data-stu-id="ee91f-173">Provisioning Administration Certificate requirements</span></span>

<span data-ttu-id="ee91f-174">各ホストデバイスは、表2に示すように、doc CA と2つの証明書を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-174">Each host device must have the doc CA and two certificates as shown in Table 2.</span></span>

#### <span data-ttu-id="ee91f-175">表 2.</span><span class="sxs-lookup"><span data-stu-id="ee91f-175">Table 2.</span></span> <span data-ttu-id="ee91f-176">管理証明書の要件のプロビジョニング</span><span class="sxs-lookup"><span data-stu-id="ee91f-176">Provisioning administration certificate requirements</span></span>

|<span data-ttu-id="ee91f-177">証明書</span><span class="sxs-lookup"><span data-stu-id="ee91f-177">Certificate</span></span>|<span data-ttu-id="ee91f-178">アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="ee91f-178">Algorithm</span></span>|<span data-ttu-id="ee91f-179">説明</span><span class="sxs-lookup"><span data-stu-id="ee91f-179">Description</span></span>|<span data-ttu-id="ee91f-180">EKU OID</span><span class="sxs-lookup"><span data-stu-id="ee91f-180">EKU OID</span></span>|
|---|---|---|---|
|<span data-ttu-id="ee91f-181">Host authentication certificate</span><span class="sxs-lookup"><span data-stu-id="ee91f-181">Host authentication certificate</span></span>|<span data-ttu-id="ee91f-182">ECC P256</span><span class="sxs-lookup"><span data-stu-id="ee91f-182">ECC P256</span></span><br><span data-ttu-id="ee91f-183">SHA 256</span><span class="sxs-lookup"><span data-stu-id="ee91f-183">SHA 256</span></span>|<span data-ttu-id="ee91f-184">ホストデバイスの id を証明します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-184">Proves the identity of the host device.</span></span>|<span data-ttu-id="ee91f-185">1.3.6.1.4.1.311.76.9.21.2</span><span class="sxs-lookup"><span data-stu-id="ee91f-185">1.3.6.1.4.1.311.76.9.21.2</span></span>|
|<span data-ttu-id="ee91f-186">プロビジョニング管理証明書</span><span class="sxs-lookup"><span data-stu-id="ee91f-186">Provisioning administration certificate</span></span>|<span data-ttu-id="ee91f-187">ECC P256</span><span class="sxs-lookup"><span data-stu-id="ee91f-187">ECC P256</span></span><br><span data-ttu-id="ee91f-188">SHA256</span><span class="sxs-lookup"><span data-stu-id="ee91f-188">SHA256</span></span>|<span data-ttu-id="ee91f-189">ドックに現在インストールされている CA を置き換えられるようにすることで、dock の所有権やポリシー設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-189">Enables you to change dock ownership and/or policy settings by allowing you to replace the CA that's currently installed on the dock.</span></span>|<span data-ttu-id="ee91f-190">1.3.6.1.4.1.311.76.9.21.3</span><span class="sxs-lookup"><span data-stu-id="ee91f-190">1.3.6.1.4.1.311.76.9.21.3</span></span><br><span data-ttu-id="ee91f-191">1.3.6.1.4.1.311.76.9.21.4</span><span class="sxs-lookup"><span data-stu-id="ee91f-191">1.3.6.1.4.1.311.76.9.21.4</span></span>|

   >[!NOTE]
   ><span data-ttu-id="ee91f-192">ホスト認証とプロビジョニング証明書は、.pfx ファイル形式でエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-192">The host authentication and provisioning certificates must be exported as .pfx files.</span></span>

### <span data-ttu-id="ee91f-193">構成パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="ee91f-193">Create configuration package</span></span>

<span data-ttu-id="ee91f-194">証明書を取得または作成したら、ターゲット Surface デバイスに適用される MSI 構成パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-194">When you have obtained or created the certificates, you’re ready to build the MSI configuration package that will be applied to target Surface devices.</span></span>

1. <span data-ttu-id="ee91f-195">Surface **UEFI コンフィギュレーター**を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-195">Run Surface **UEFI Configurator**.</span></span>

   ![Surface UEFI コンフィギュレーターの実行](images/secure-surface-dock-ports-semm-1.png)

1. <span data-ttu-id="ee91f-197">[ **Surface Dock**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-197">Select **Surface Dock**.</span></span>

   ![Surface Dock を選ぶ](images/secure-surface-dock-ports-semm-2.png)

1. <span data-ttu-id="ee91f-199">[証明書] ページで、適切な**証明書**を入力します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-199">On the certificate page, enter the appropriate **certificates**.</span></span>

   ![適切な証明書を入力する](images/secure-surface-dock-ports-semm-3.png)

1. <span data-ttu-id="ee91f-201">適切な dock RNs をリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-201">Add appropriate dock RNs to the list.</span></span>

   >[!NOTE]
   ><span data-ttu-id="ee91f-202">複数の Surface Dock 2 デバイスの構成パッケージを作成する場合、各 RN を手動で入力する代わりに、RNs のリストを含む .csv ファイルを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-202">When creating a configuration package for multiple Surface Dock 2 devices, instead of entering each RN manually, you can use a .csv file that contains a list of RNs.</span></span>

1. <span data-ttu-id="ee91f-203">USB データ、イーサネット、およびオーディオポートのポリシー設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-203">Specify your policy settings for USB data, Ethernet, and Audio ports.</span></span> <span data-ttu-id="ee91f-204">UEFI コンフィギュレーター認証済みユーザー (認証済みポリシー) と認証されていないユーザー (認証されていないポリシー) のポリシー設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-204">UEFI Configurator lets you configure policy settings for authenticated users (Authenticated Policy) and unauthenticated users (Unauthenticated Policy).</span></span> <span data-ttu-id="ee91f-205">次の図は、認証されたユーザーに対して [ポートアクセス] がオンになっていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-205">The following figure shows port access turned on for authenticated users and turned off for unauthenticated users.</span></span>

   ![アクティブ化または非アクティブ化するコンポーネントを選択します。](images/secure-surface-dock-ports-semm-4.png)

   - <span data-ttu-id="ee91f-207">Authenticated user は、で構成されている適切な証明書がインストールされている Surface デバイスを指します。ターゲットデバイスに適用した MSI 構成パッケージ。</span><span class="sxs-lookup"><span data-stu-id="ee91f-207">Authenticated user refers to a Surface Device that has the appropriate certificates installed, as configured in the .MSI configuration package that you applied to target devices.</span></span> <span data-ttu-id="ee91f-208">これは、デバイスにサインインしたユーザー認証済みのユーザーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-208">It applies to any user authenticated user who signs into the device.</span></span> 
   - <span data-ttu-id="ee91f-209">認証されていないユーザーは、他のデバイスを参照しています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-209">Unauthenticated user refers to any other device.</span></span>
   - <span data-ttu-id="ee91f-210">[**リセット**] を選択して、dock によって承認された以前の構成パッケージを削除する特別な "リセット" パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-210">Select **Reset** to create a special “Reset” package that will remove any previous configuration package that the dock had accepted.</span></span>

1. <span data-ttu-id="ee91f-211">[**ビルド**] を選択して、指定どおりにパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-211">Select **Build** to create the package as specified.</span></span>

### <span data-ttu-id="ee91f-212">構成パッケージを Surface Dock 2 に適用する</span><span class="sxs-lookup"><span data-stu-id="ee91f-212">Apply the configuration package to a Surface Dock 2</span></span>

1. <span data-ttu-id="ee91f-213">Surface UEFI コンフィギュレーターによって生成された MSI ファイルを取得して Surface host デバイスにインストールします。</span><span class="sxs-lookup"><span data-stu-id="ee91f-213">Take the MSI file that the Surface UEFI Configurator generated and install it on a Surface host device.</span></span> <span data-ttu-id="ee91f-214">互換性のあるホストデバイスとしては、surface Book 3、Surface ノート Pc 3、Surface Pro 7 があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-214">Compatible host devices are Surface Book 3, Surface Laptop 3, or Surface Pro 7.</span></span>
1. <span data-ttu-id="ee91f-215">ホストデバイスを Surface Dock 2 に接続します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-215">Connect the host device to the Surface Dock 2.</span></span> <span data-ttu-id="ee91f-216">ドックに接続すると、UEFI ポリシー設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-216">When you connect the dock UEFI policy settings are applied.</span></span>

## <span data-ttu-id="ee91f-217">Surface アプリを使用して管理状態を確認する</span><span class="sxs-lookup"><span data-stu-id="ee91f-217">Verify managed state using the Surface App</span></span>

<span data-ttu-id="ee91f-218">構成パッケージを適用した後は、Surface の結果ポリシーの状態を、Surface アプリから直接確認することができます。これは、既定ですべての Surface デバイスにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="ee91f-218">Once you have applied the configuration package, you can quickly verify the resultant policy state of the dock directly from the Surface App, installed by default on all Surface devices.</span></span> <span data-ttu-id="ee91f-219">Surface アプリがデバイスに存在しない場合は、Microsoft Store からダウンロードしてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-219">If Surface App isn't present on the device, you can download and install it from the Microsoft Store.</span></span>

### <span data-ttu-id="ee91f-220">テストシナリオ</span><span class="sxs-lookup"><span data-stu-id="ee91f-220">Test scenario</span></span>

<span data-ttu-id="ee91f-221">目的: 認証されたユーザーのみがアクセスできるようにポリシー設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-221">Objective: Configure policy settings to allow port access by authenticated users only.</span></span>

1. <span data-ttu-id="ee91f-222">認証されたユーザーのためにすべてのポートを有効にし、認証されていないユーザーに対してオフにします。</span><span class="sxs-lookup"><span data-stu-id="ee91f-222">Turn on all ports for authenticated users and turn them off for unauthenticated users.</span></span>

   ![認証されたユーザーのポートを有効にする](images/secure-surface-dock-ports-semm-4.png)

1. <span data-ttu-id="ee91f-224">構成パッケージをターゲットデバイスに適用し、Surface Dock 2 を接続します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-224">Apply the configuration package to your target device and then connect Surface Dock 2.</span></span>

1. <span data-ttu-id="ee91f-225">Surface**アプリ**を開き、[ **surface dock** ] を選択して、surface dock の結果ポリシーの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-225">Open **Surface App** and select **Surface Dock** to view the resultant policy state of your Surface Dock.</span></span> <span data-ttu-id="ee91f-226">ポリシー設定が適用されると、Surface アプリは、ポートが利用可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-226">If the policy settings are applied, Surface App will indicate that ports are available.</span></span>

   ![Surface アプリは、認証されたユーザーがすべてのポートを利用できることを示します。](images/secure-surface-dock-ports-semm-5.png)

1. <span data-ttu-id="ee91f-228">次に、ポリシー設定で、認証されていないユーザーのすべてのポートが正常にオフになっていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee91f-228">Now you need to verify that the policy settings have successfully turned off all ports for unauthenticated users.</span></span> <span data-ttu-id="ee91f-229">Surface Dock 2 を非管理対象デバイスに接続します。つまり、作成した構成パッケージの管理の範囲外にある任意の Surface デバイス。</span><span class="sxs-lookup"><span data-stu-id="ee91f-229">Connect Surface Dock 2 to an unmanaged device, i.e., any Surface device outside the scope of management for the configuration package you created.</span></span>

1. <span data-ttu-id="ee91f-230">**Surface アプリ**を開いて、[ **surface Dock**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-230">Open **Surface App** and select **Surface Dock**.</span></span> <span data-ttu-id="ee91f-231">ポリシーの状態には、ポートがオフになっていることが示されます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-231">The resultant policy state will indicate ports are turned off.</span></span>

   ![<span data-ttu-id="ee91f-232">認証されていないユーザーに対して無効になっているポートを示す Surface アプリ</span><span class="sxs-lookup"><span data-stu-id="ee91f-232">Surface app showing ports turned off for unauthenticated users</span></span> ](images/secure-surface-dock-ports-semm-6.png)

>[!NOTE]
><span data-ttu-id="ee91f-233">デバイスの所有権を保持したいが、すべてのユーザーにフルアクセスを許可する場合は、新しいパッケージを作成してすべての機能を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee91f-233">If you want to keep ownership of the device, but allow all users full access, you can make a new package with everything turned on.</span></span> <span data-ttu-id="ee91f-234">デバイスの制限と所有権を完全に削除する (これを非管理する) には、[Surface UEFI 構成の**リセット**] を選択して、ターゲットデバイスに適用するパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee91f-234">If you wish to completely remove the restrictions and ownership of the device (make it unmanaged), select **Reset** in Surface UEFI Configurator to create a package to apply to target devices.</span></span>

<span data-ttu-id="ee91f-235">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="ee91f-235">Congratulations.</span></span> <span data-ttu-id="ee91f-236">ターゲットとなるホストデバイスで、Surface Dock の2つのポートが正常に管理されました。</span><span class="sxs-lookup"><span data-stu-id="ee91f-236">You have successfully managed Surface Dock 2 ports on targeted host devices.</span></span>

## <span data-ttu-id="ee91f-237">詳細情報</span><span class="sxs-lookup"><span data-stu-id="ee91f-237">Learn more</span></span>

- [<span data-ttu-id="ee91f-238">Surface Enterprise 管理モード (SEMM) のドキュメント</span><span class="sxs-lookup"><span data-stu-id="ee91f-238">Surface Enterprise Management Mode (SEMM) documentation</span></span>](https://docs.microsoft.com/surface/surface-enterprise-management-mode)
- [<span data-ttu-id="ee91f-239">証明書サービスのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ee91f-239">Certificate Services Architecture</span></span>](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture)
- [<span data-ttu-id="ee91f-240">Windows Server 2019 インサイド Out</span><span class="sxs-lookup"><span data-stu-id="ee91f-240">Windows Server 2019 Inside Out</span></span>](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)
- [<span data-ttu-id="ee91f-241">Windows Server 2008 PKI および証明書のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ee91f-241">Windows Server 2008 PKI and Certificate Security</span></span>](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)
