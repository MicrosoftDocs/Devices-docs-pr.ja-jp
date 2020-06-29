---
title: 802.1x ワイヤード (有線) 認証を有効にする
description: Surface Hub デバイスでは、802.1x ワイヤード (有線) 認証の MDM ポリシーが有効になっています。
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/15/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 119f879d74ccda5d53da27d842413346a50693f1
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836253"
---
# <span data-ttu-id="04355-103">802.1x ワイヤード (有線) 認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="04355-103">Enable 802.1x wired authentication</span></span>

<span data-ttu-id="04355-104">[Windows 10 の 2017 年 11 月 14 日の更新プログラム](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (ビルド 15063.726) により、Surface Hub デバイスでの 802.1x ワイヤード (有線) 認証の MDM ポリシーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="04355-104">The [November 14, 2017 update to Windows 10](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (build 15063.726) enables 802.1x wired authentication MDM policies on Surface Hub devices.</span></span> <span data-ttu-id="04355-105">この機能により、組織で [IEEE 802.1x 認証プロトコル](http://www.ieee802.org/1/pages/802.1x-2010.html)を使用する、標準化されたワイヤード (有線) ネットワーク認証を適用できます。</span><span class="sxs-lookup"><span data-stu-id="04355-105">The feature allows organizations to enforce standardized wired network authentication using the [IEEE 802.1x authentication protocol](http://www.ieee802.org/1/pages/802.1x-2010.html).</span></span> <span data-ttu-id="04355-106">これは MDM を介して WLAN プロファイルを使用するワイヤレス認証では既に利用可能です。</span><span class="sxs-lookup"><span data-stu-id="04355-106">This is already available for wireless authentication using WLAN profiles via MDM.</span></span> <span data-ttu-id="04355-107">このトピックでは、ワイヤード (有線) 認証で使用するための Surface Hub の構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04355-107">This topic explains how to  configure a Surface Hub for use with wired authentication.</span></span> 

<span data-ttu-id="04355-108">Surface Hub での 802.1x ワイヤード (有線) 認証の適用と有効化は、MDM [OMA URI 定義](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings)で構成できます。</span><span class="sxs-lookup"><span data-stu-id="04355-108">Enforcement and enablement of 802.1x wired authentication on Surface Hub can be done through MDM [OMA-URI definition](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings).</span></span> 

<span data-ttu-id="04355-109">設定するプライマリ構成は **LanProfile** ポリシーです。</span><span class="sxs-lookup"><span data-stu-id="04355-109">The primary configuration to set is the **LanProfile** policy.</span></span> <span data-ttu-id="04355-110">選択した認証方法によっては、**EapUserData** ポリシーまたはユーザーやコンピューターの証明書を追加するための MDM ポリシー (ユーザー/デバイスの証明書用の [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)、デバイス証明書用の [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) など) のいずれかのポリシーが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="04355-110">Depending on the authentication method selected, other policies may be required, either the **EapUserData** policy or through MDM policies for adding user or machine certificates (such as [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) for user/device certificates or [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) for device certificates).</span></span> 

## <span data-ttu-id="04355-111">LanProfile ポリシー要素</span><span class="sxs-lookup"><span data-stu-id="04355-111">LanProfile policy element</span></span>

<span data-ttu-id="04355-112">サポートされている 802.1x 認証方法のいずれかを使用するように Surface Hub を構成するには、次の OMA-URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="04355-112">To configure Surface Hub to use one of the supported 802.1x authentication methods, utilize the following OMA-URI.</span></span> 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

<span data-ttu-id="04355-113">この OMA-URI ノードは、XML のテキスト文字列をパラメーターとして取得します。</span><span class="sxs-lookup"><span data-stu-id="04355-113">This OMA-URI node takes a text string of XML as a parameter.</span></span> <span data-ttu-id="04355-114">パラメーターとして提供される XML は、[802.1X スキーマ](https://msdn.microsoft.com/library/cc233003.aspx)の要素を含む [ワイヤード (有線) LAN プロファイル スキーマ](https://msdn.microsoft.com/library/cc233002.aspx)に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="04355-114">The XML provided as a parameter should conform to the [Wired LAN Profile Schema](https://msdn.microsoft.com/library/cc233002.aspx) including elements from the [802.1X schema](https://msdn.microsoft.com/library/cc233003.aspx).</span></span> 

<span data-ttu-id="04355-115">ほとんどの場合、管理者またはユーザーは、次の NETSH コマンドを使用して、ネットワーク上で既に 802.1X 用に構成されている既存の PC から LanProfile XML をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="04355-115">In most instances, an administrator or user can export the LanProfile XML from an existing PC that is already configured on the network for 802.1X using this following NETSH command.</span></span> 

```
netsh lan export profile folder=.
```

<span data-ttu-id="04355-116">このコマンドを実行すると、次のように出力され、現在のディレクトリに **Ethernet.xml** という名前のファイルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="04355-116">Running this command will give the following output and place a file titled **Ethernet.xml** in the current directory.</span></span> 

```
Interface: Ethernet
Profile File Name: .\Ethernet.xml
1 profile(s) were exported successfully.
```

## <span data-ttu-id="04355-117">EapUserData ポリシー要素</span><span class="sxs-lookup"><span data-stu-id="04355-117">EapUserData policy element</span></span>

<span data-ttu-id="04355-118">証明書ではなく、ユーザー名とパスワードを必要とする認証方法を選択した場合、**EapUserData** 要素を使用して、ネットワークで認証するために使用するデバイスの資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="04355-118">If your selected authentication method requires a username and password as opposed to a certificate, you can use the **EapUserData** element to specify credentials for the device to use to authenticate to the network.</span></span> 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

<span data-ttu-id="04355-119">この OMA-URI ノードは、XML のテキスト文字列をパラメーターとして取得します。</span><span class="sxs-lookup"><span data-stu-id="04355-119">This OMA-URI node takes a text string of XML as a parameter.</span></span> <span data-ttu-id="04355-120">パラメーターとして提供される XML は、[PEAP MS-CHAPv2 ユーザー プロパティの例](https://msdn.microsoft.com/library/windows/desktop/bb891979)に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="04355-120">The XML provided as a parameter should conform to the [PEAP MS-CHAPv2 User Properties example](https://msdn.microsoft.com/library/windows/desktop/bb891979).</span></span> <span data-ttu-id="04355-121">この例で、*test* と *ias-domain* のすべてのインスタンスを自分の情報に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="04355-121">In the example, you will need to replace all instances of *test* and *ias-domain* with your information.</span></span>



## <span data-ttu-id="04355-122">証明書の追加</span><span class="sxs-lookup"><span data-stu-id="04355-122">Adding certificates</span></span>

<span data-ttu-id="04355-123">選択した認証方法が証明書ベースの場合は、[プロビジョニングパッケージを作成](provisioning-packages-for-surface-hub.md)するか、 [MDM を利用](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)するか、または設定 (**設定**の更新とセキュリティ証明書) から証明書をインポートして、それらの証明書を  >  **Update and Security**  >  **Certificates**適切な証明書ストアの Surface Hub デバイスに展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04355-123">If your selected authentication method is certificate-based, you will need to [create a provisioning package](provisioning-packages-for-surface-hub.md), [utilize MDM](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp), or import a certificate from settings (**Settings** > **Update and Security** > **Certificates**) to deploy those certificates to your Surface Hub device in the appropriate Certificate Store.</span></span> <span data-ttu-id="04355-124">証明書を追加する場合、各 PFX には証明書を 1 つだけ含める必要があります (PFX に複数の証明書を含めることはできません)。</span><span class="sxs-lookup"><span data-stu-id="04355-124">When adding certificates, each PFX must contain only one certificate (a PFX cannot have multiple certificates).</span></span>

