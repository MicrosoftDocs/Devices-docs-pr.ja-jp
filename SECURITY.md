---
ms.openlocfilehash: bc66462291f4b1959fe1080ab33849c935218ebd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834525"
---
<!-- BEGIN MICROSOFT SECURITY.MD V0.0.5 BLOCK -->

## <span data-ttu-id="6d51e-101">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6d51e-101">Security</span></span>

<span data-ttu-id="6d51e-102">Microsoft は、 [microsoft](https://github.com/Microsoft)、 [Azure](https://github.com/Azure)、 [.net](https://github.com/dotnet)、 [AspNet](https://github.com/aspnet)、 [Xamarin](https://github.com/xamarin)、および[github の組織](https://opensource.microsoft.com/)を含む github 組織によって管理されるすべてのソースコードリポジトリを、真剣に受け止めています。</span><span class="sxs-lookup"><span data-stu-id="6d51e-102">Microsoft takes the security of our software products and services seriously, which includes all source code repositories managed through our GitHub organizations, which include [Microsoft](https://github.com/Microsoft), [Azure](https://github.com/Azure), [DotNet](https://github.com/dotnet), [AspNet](https://github.com/aspnet), [Xamarin](https://github.com/xamarin), and [our GitHub organizations](https://opensource.microsoft.com/).</span></span>

<span data-ttu-id="6d51e-103">[Microsoft のセキュリティの脆弱性](https://docs.microsoft.com/en-us/previous-versions/tn-archive/cc751383(v=technet.10))を満たしている microsoft 所有のリポジトリで、セキュリティの脆弱性を発見したと判断される場合は、以下の説明に従ってご報告ください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-103">If you believe you have found a security vulnerability in any Microsoft-owned repository that meets [Microsoft's definition of a security vulnerability](https://docs.microsoft.com/en-us/previous-versions/tn-archive/cc751383(v=technet.10)), please report it to us as described below.</span></span>

## <span data-ttu-id="6d51e-104">セキュリティの問題を報告する</span><span class="sxs-lookup"><span data-stu-id="6d51e-104">Reporting Security Issues</span></span>

**<span data-ttu-id="6d51e-105">パブリック GitHub の問題により、セキュリティの脆弱性を報告しないでください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-105">Please do not report security vulnerabilities through public GitHub issues.</span></span>**

<span data-ttu-id="6d51e-106">代わりに、の Microsoft セキュリティレスポンスセンター (MSRC) に報告してください [https://msrc.microsoft.com/create-report](https://msrc.microsoft.com/create-report) 。</span><span class="sxs-lookup"><span data-stu-id="6d51e-106">Instead, please report them to the Microsoft Security Response Center (MSRC) at [https://msrc.microsoft.com/create-report](https://msrc.microsoft.com/create-report).</span></span>

<span data-ttu-id="6d51e-107">ログインしないで送信する場合は、 [secure@microsoft.com](mailto:secure@microsoft.com)にメールを送信してください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-107">If you prefer to submit without logging in, send email to [secure@microsoft.com](mailto:secure@microsoft.com).</span></span>  <span data-ttu-id="6d51e-108">可能であれば、PGP キーでメッセージを暗号化します。[Microsoft セキュリティレスポンスセンター PGP キーページ](https://www.microsoft.com/en-us/msrc/pgp-key-msrc)からダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-108">If possible, encrypt your message with our PGP key; please download it from the [Microsoft Security Response Center PGP Key page](https://www.microsoft.com/en-us/msrc/pgp-key-msrc).</span></span>

<span data-ttu-id="6d51e-109">24時間以内に回答を受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d51e-109">You should receive a response within 24 hours.</span></span> <span data-ttu-id="6d51e-110">何らかの理由で、元のメッセージを受信したことをメールで確認してください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-110">If for some reason you do not, please follow up via email to ensure we received your original message.</span></span> <span data-ttu-id="6d51e-111">追加情報については、 [microsoft.com/msrc](https://www.microsoft.com/msrc)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-111">Additional information can be found at [microsoft.com/msrc](https://www.microsoft.com/msrc).</span></span> 

<span data-ttu-id="6d51e-112">考えられる問題の性質と範囲の詳細については、以下に記載されているお客様の情報をご記入ください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-112">Please include the requested information listed below (as much as you can provide) to help us better understand the nature and scope of the possible issue:</span></span>

  * <span data-ttu-id="6d51e-113">問題の種類 (バッファーオーバーフロー、SQL インジェクション、クロスサイトスクリプティングなど)</span><span class="sxs-lookup"><span data-stu-id="6d51e-113">Type of issue (e.g. buffer overflow, SQL injection, cross-site scripting, etc.)</span></span>
  * <span data-ttu-id="6d51e-114">問題の影響に関連するソースファイルの完全パス</span><span class="sxs-lookup"><span data-stu-id="6d51e-114">Full paths of source file(s) related to the manifestation of the issue</span></span>
  * <span data-ttu-id="6d51e-115">影響を受けるソースコードの場所 (タグ/分岐/コミットまたは直接 URL)</span><span class="sxs-lookup"><span data-stu-id="6d51e-115">The location of the affected source code (tag/branch/commit or direct URL)</span></span>
  * <span data-ttu-id="6d51e-116">問題を再現するために必要な特別な構成</span><span class="sxs-lookup"><span data-stu-id="6d51e-116">Any special configuration required to reproduce the issue</span></span>
  * <span data-ttu-id="6d51e-117">問題を再現するためのステップバイステップの手順</span><span class="sxs-lookup"><span data-stu-id="6d51e-117">Step-by-step instructions to reproduce the issue</span></span>
  * <span data-ttu-id="6d51e-118">概念実証または悪用コード (可能な場合)</span><span class="sxs-lookup"><span data-stu-id="6d51e-118">Proof-of-concept or exploit code (if possible)</span></span>
  * <span data-ttu-id="6d51e-119">攻撃者が問題をどのように活用するかなど、問題が発生した場合の影響</span><span class="sxs-lookup"><span data-stu-id="6d51e-119">Impact of the issue, including how an attacker might exploit the issue</span></span>

<span data-ttu-id="6d51e-120">この情報は、より迅速にレポートを選別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d51e-120">This information will help us triage your report more quickly.</span></span>

<span data-ttu-id="6d51e-121">バグ bounty を報告している場合は、さらに包括的なレポートをより高い bounty 賞に投稿できます。</span><span class="sxs-lookup"><span data-stu-id="6d51e-121">If you are reporting for a bug bounty, more complete reports can contribute to a higher bounty award.</span></span> <span data-ttu-id="6d51e-122">お客様のアクティブなプログラムの詳細については、 [Microsoft のバグ Bounty プログラム](https://microsoft.com/msrc/bounty)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d51e-122">Please visit our [Microsoft Bug Bounty Program](https://microsoft.com/msrc/bounty) page for more details about our active programs.</span></span>

## <span data-ttu-id="6d51e-123">優先する言語</span><span class="sxs-lookup"><span data-stu-id="6d51e-123">Preferred Languages</span></span>

<span data-ttu-id="6d51e-124">すべての通信は英語で行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6d51e-124">We prefer all communications to be in English.</span></span>

## <span data-ttu-id="6d51e-125">ポリシー</span><span class="sxs-lookup"><span data-stu-id="6d51e-125">Policy</span></span>

<span data-ttu-id="6d51e-126">Microsoft は、調整された[脆弱性の漏えい](https://www.microsoft.com/en-us/msrc/cvd)の原則に従います。</span><span class="sxs-lookup"><span data-stu-id="6d51e-126">Microsoft follows the principle of [Coordinated Vulnerability Disclosure](https://www.microsoft.com/en-us/msrc/cvd).</span></span>

<!-- END MICROSOFT SECURITY.MD BLOCK -->