---
title: Surface の明るさの制御
description: このトピックでは、Surface 明度コントロールアプリを使用して、pos とキオスクのシナリオでディスプレイの明るさを管理する方法について説明します。
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 197ed9fe1abc880779ad6bb0f85d2970086395f6
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835806"
---
# <span data-ttu-id="8c346-103">Surface の明るさの制御</span><span class="sxs-lookup"><span data-stu-id="8c346-103">Surface Brightness Control</span></span>

<span data-ttu-id="8c346-104">販売時点またはその他の "常時オン" のキオスクシナリオで Surface デバイスを展開する場合は、新しい Surface 輝度コントロールアプリを使用して、電源管理を最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-104">When deploying Surface devices in point of sale or other “always-on” kiosk scenarios, you can optimize power management using the new Surface Brightness Control app.</span></span>

<span data-ttu-id="8c346-105">[Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703)を使ってダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="8c346-105">Available for download with [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
<span data-ttu-id="8c346-106">Surface 輝度コントロールは、熱荷重を軽減し、展開された Surface デバイスの全体的な二酸化炭素排出量を削減するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="8c346-106">Surface Brightness Control is designed to help reduce thermal load and lower the overall carbon footprint for deployed Surface devices.</span></span>
<span data-ttu-id="8c346-107">このツールのみをダウンロードページから入手する予定の場合は、利用可能なリストで**Surface_Brightness_Control_v1.16.137.0.msi**ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c346-107">If you plan to get only this tool from the download page, select the file **Surface_Brightness_Control_v1.16.137.0.msi** in the available list.</span></span>
<span data-ttu-id="8c346-108">このツールは、使用されていないときに自動的に画面を暗くします。次の設定オプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c346-108">The tool automatically dims the screen when not in use and includes the following configuration options:</span></span>

- <span data-ttu-id="8c346-109">画面を暗くするまでの非アクティブな時間。</span><span class="sxs-lookup"><span data-stu-id="8c346-109">Period of inactivity before dimming the display.</span></span>

- <span data-ttu-id="8c346-110">明るさのレベルは淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c346-110">Brightness level when dimmed.</span></span>

- <span data-ttu-id="8c346-111">使用中の最大輝度レベル。</span><span class="sxs-lookup"><span data-stu-id="8c346-111">Maximum brightness level when in use.</span></span>

**<span data-ttu-id="8c346-112">Surface 輝度コントロールを実行するには:</span><span class="sxs-lookup"><span data-stu-id="8c346-112">To run Surface Brightness Control:</span></span>**

- <span data-ttu-id="8c346-113">ターゲットデバイスに surfacebrightnesscontrol.msi をインストールすると、[Surface 輝度] コントロールはすぐに機能し始めます。</span><span class="sxs-lookup"><span data-stu-id="8c346-113">Install surfacebrightnesscontrol.msi on the target device and Surface Brightness Control will begin working immediately.</span></span>

## <span data-ttu-id="8c346-114">Surface 輝度コントロールの構成</span><span class="sxs-lookup"><span data-stu-id="8c346-114">Configuring Surface Brightness Control</span></span>

<span data-ttu-id="8c346-115">既定の値は、Windows レジストリを使って調整できます。</span><span class="sxs-lookup"><span data-stu-id="8c346-115">You can adjust the default values via the Windows Registry.</span></span> <span data-ttu-id="8c346-116">Windows レジストリの使用の詳細については、[レジストリのドキュメント](https://docs.microsoft.com/windows/desktop/sysinfo/registry)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c346-116">For more information about using the Windows Registry, refer to the [Registry documentation](https://docs.microsoft.com/windows/desktop/sysinfo/registry).</span></span>

1.  <span data-ttu-id="8c346-117">コマンドプロンプトから regedit を実行して、Windows レジストリエディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="8c346-117">Run regedit from a command prompt to open the Windows Registry Editor.</span></span>
    
      - <span data-ttu-id="8c346-118">Computer\HKEY\ _LOCAL \ _MACHINE \SOFTWARE\WOW6432Node\Microsoft\Surface\Surface 輝度コントロール </span><span class="sxs-lookup"><span data-stu-id="8c346-118">Computer\HKEY\_LOCAL\_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Surface\Surface Brightness Control</span></span>\ 
    
    <span data-ttu-id="8c346-119">以前のバージョンの Surface 明度コントロールを実行している場合は、代わりに次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c346-119">If you're running an older version of Surface Brightness control, run the following command instead:</span></span>
    
      - <span data-ttu-id="8c346-120">Computer\HKEY\ _LOCAL \ _MACHINE \SOFTWARE\Microsoft\Surface\Surface 輝度コントロール </span><span class="sxs-lookup"><span data-stu-id="8c346-120">Computer\HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Surface\Surface Brightness Control</span></span>\


| <span data-ttu-id="8c346-121">レジストリ設定</span><span class="sxs-lookup"><span data-stu-id="8c346-121">Registry Setting</span></span> | <span data-ttu-id="8c346-122">データ</span><span class="sxs-lookup"><span data-stu-id="8c346-122">Data</span></span>| <span data-ttu-id="8c346-123">説明</span><span class="sxs-lookup"><span data-stu-id="8c346-123">Description</span></span>  
|-----------|------------|---------------
| <span data-ttu-id="8c346-124">輝度コントロールが有効</span><span class="sxs-lookup"><span data-stu-id="8c346-124">Brightness Control Enabled</span></span>  |  <span data-ttu-id="8c346-125">既定値:01</span><span class="sxs-lookup"><span data-stu-id="8c346-125">Default: 01</span></span>  <br> <span data-ttu-id="8c346-126">オプション:01、00</span><span class="sxs-lookup"><span data-stu-id="8c346-126">Option: 01, 00</span></span> <br> <span data-ttu-id="8c346-127">「REG_BINARY」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-127">Type: REG_BINARY</span></span> |  <span data-ttu-id="8c346-128">この設定により、表面の輝度調整を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-128">This setting allows you to turn Surface Brightness Control on or off.</span></span> <span data-ttu-id="8c346-129">表面の明るさの制御を無効にするには、値を00に設定します。</span><span class="sxs-lookup"><span data-stu-id="8c346-129">To disable Surface Brightness Control, set the value to 00.</span></span> <span data-ttu-id="8c346-130">この設定を構成しない場合、Surface 輝度コントロールはオンになります。</span><span class="sxs-lookup"><span data-stu-id="8c346-130">If you do not configure this setting, Surface Brightness Control is on.</span></span> |
| <span data-ttu-id="8c346-131">Power Enabled の輝度コントロール</span><span class="sxs-lookup"><span data-stu-id="8c346-131">Brightness Control On Power Enabled</span></span>| <span data-ttu-id="8c346-132">既定値:01</span><span class="sxs-lookup"><span data-stu-id="8c346-132">Default: 01</span></span> <br> <span data-ttu-id="8c346-133">オプション:01、00</span><span class="sxs-lookup"><span data-stu-id="8c346-133">Options: 01, 00</span></span> <br> <span data-ttu-id="8c346-134">「REG_BINARY」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-134">Type: REG_BINARY</span></span> | <span data-ttu-id="8c346-135">この設定では、デバイスが直接電源に接続されているときに表面の輝度調整をオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-135">This setting allows you to turn off Surface Brightness Control when the device is directly connected to power.</span></span> <span data-ttu-id="8c346-136">電源が接続されているときに表面の輝度コントロールを無効にするには、値を00に設定します。</span><span class="sxs-lookup"><span data-stu-id="8c346-136">To disable Surface Brightness Control when power is plugged in, set the value to 00.</span></span> <span data-ttu-id="8c346-137">この設定を構成しない場合、Surface 輝度コントロールはオンになります。</span><span class="sxs-lookup"><span data-stu-id="8c346-137">If you do not configure this setting, Surface Brightness Control is on.</span></span> |
| <span data-ttu-id="8c346-138">淡色表示の明るさ</span><span class="sxs-lookup"><span data-stu-id="8c346-138">Dimmed Brightness</span></span>   | <span data-ttu-id="8c346-139">既定値:20</span><span class="sxs-lookup"><span data-stu-id="8c346-139">Default: 20</span></span>  <br><span data-ttu-id="8c346-140">オプション: 画面の明るさの0-100% の範囲</span><span class="sxs-lookup"><span data-stu-id="8c346-140">Option: Range of 0-100 percent of screen brightness</span></span> <br> <span data-ttu-id="8c346-141">データ型: 正の整数</span><span class="sxs-lookup"><span data-stu-id="8c346-141">Data Type: Positive integer</span></span> <br> <span data-ttu-id="8c346-142">「REG_DWORD」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-142">Type: REG_DWORD</span></span> | <span data-ttu-id="8c346-143">この設定を使用すると、非アクティブな時間帯に明るさの範囲を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-143">This setting allows you to manage brightness range during periods of inactivity.</span></span> <span data-ttu-id="8c346-144">この設定を構成しない場合、明るさのレベルは、アイドル状態が30秒続いたときの完全な輝度の20% に低下します。</span><span class="sxs-lookup"><span data-stu-id="8c346-144">If you do not configure this setting, the brightness level will drop to 20 percent of full brightness after 30 seconds of inactivity.</span></span> |
<span data-ttu-id="8c346-145">すべての明るさ</span><span class="sxs-lookup"><span data-stu-id="8c346-145">Full Brightness</span></span>   | <span data-ttu-id="8c346-146">既定値: 100</span><span class="sxs-lookup"><span data-stu-id="8c346-146">Default: 100</span></span>  <br><span data-ttu-id="8c346-147">オプション: 画面の明るさの0-100% の範囲</span><span class="sxs-lookup"><span data-stu-id="8c346-147">Option: Range of 0-100 percent of screen brightness</span></span> <br> <span data-ttu-id="8c346-148">データ型: 正の整数</span><span class="sxs-lookup"><span data-stu-id="8c346-148">Data Type: Positive integer</span></span> <br> <span data-ttu-id="8c346-149">「REG_DWORD」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-149">Type: REG_DWORD</span></span>  | <span data-ttu-id="8c346-150">この設定では、デバイスの最大輝度範囲を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-150">This setting allows you to manage the maximum brightness range for the device.</span></span> <span data-ttu-id="8c346-151">この設定を構成しない場合、最大輝度範囲は100パーセントになります。</span><span class="sxs-lookup"><span data-stu-id="8c346-151">If you do not configure this setting, the maximum brightness range is 100 percent.</span></span>|  
| <span data-ttu-id="8c346-152">無通信タイムアウト</span><span class="sxs-lookup"><span data-stu-id="8c346-152">Inactivity Timeout</span></span>| <span data-ttu-id="8c346-153">既定値:30 秒</span><span class="sxs-lookup"><span data-stu-id="8c346-153">Default: 30 seconds</span></span> <br><span data-ttu-id="8c346-154">オプション: 任意の数値</span><span class="sxs-lookup"><span data-stu-id="8c346-154">Option: Any numeric value</span></span>  <br><span data-ttu-id="8c346-155">データ型: 整数</span><span class="sxs-lookup"><span data-stu-id="8c346-155">Data Type: Integer</span></span>  <br> <span data-ttu-id="8c346-156">「REG_DWORD」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-156">Type: REG_DWORD</span></span> | <span data-ttu-id="8c346-157">この設定では、デバイスを淡色表示する前に、非アクティブな状態の期間を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-157">This setting allows you to manage the period of inactivity before dimming the device.</span></span> <span data-ttu-id="8c346-158">この設定を構成しない場合、非アクティブなタイムアウトは30秒です。</span><span class="sxs-lookup"><span data-stu-id="8c346-158">If you do not configure this setting, the inactivity timeout is 30 seconds.</span></span>|
| <span data-ttu-id="8c346-159">テレメトリが有効</span><span class="sxs-lookup"><span data-stu-id="8c346-159">Telemetry  Enabled</span></span> | <span data-ttu-id="8c346-160">既定値:01</span><span class="sxs-lookup"><span data-stu-id="8c346-160">Default: 01</span></span> <br><span data-ttu-id="8c346-161">オプション:01、00</span><span class="sxs-lookup"><span data-stu-id="8c346-161">Option: 01, 00</span></span> <br> <span data-ttu-id="8c346-162">「REG_BINARY」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c346-162">Type: REG_BINARY</span></span>  | <span data-ttu-id="8c346-163">この設定では、アプリの使用状況情報の共有を管理して、ソフトウェアを向上させ、ユーザーエクスペリエンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="8c346-163">This setting allows you to manage the sharing of app usage information to improve software and provide better user experience.</span></span> <span data-ttu-id="8c346-164">テレメトリを無効にするには、値を00に設定します。</span><span class="sxs-lookup"><span data-stu-id="8c346-164">To disable telemetry, set the value to 00.</span></span> <span data-ttu-id="8c346-165">この設定を構成しない場合、利用統計情報は microsoft のプライバシーに関する[声明](https://privacy.microsoft.com/privacystatement)に従って microsoft と共有されます。</span><span class="sxs-lookup"><span data-stu-id="8c346-165">If you do not configure this setting, telemetry information is shared with Microsoft in accordance with the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).</span></span> |

## <span data-ttu-id="8c346-166">変更と更新</span><span class="sxs-lookup"><span data-stu-id="8c346-166">Changes and updates</span></span>

### <span data-ttu-id="8c346-167">バージョン1.16.137</span><span class="sxs-lookup"><span data-stu-id="8c346-167">Version 1.16.137</span></span><br>
*<span data-ttu-id="8c346-168">リリース日: 2019 年10月22日</span><span class="sxs-lookup"><span data-stu-id="8c346-168">Release Date: 22 October 2019</span></span>*<br>
<span data-ttu-id="8c346-169">このバージョンの Surface 明度コントロールでは、次のサポートが追加されます:-x86 用の再コンパイル。 Surface Pro 7、Surface Pro X、Surface ノート Pc 3 のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="8c346-169">This version of Surface Brightness Control adds support for the following: -Recompiled for x86, adding support for Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span> 

### <span data-ttu-id="8c346-170">バージョン1.12.239.0</span><span class="sxs-lookup"><span data-stu-id="8c346-170">Version 1.12.239.0</span></span>
*<span data-ttu-id="8c346-171">リリース日: 2019 年4月26日</span><span class="sxs-lookup"><span data-stu-id="8c346-171">Release Date: 26 April 2019</span></span>*<br>
<span data-ttu-id="8c346-172">このバージョンの Surface 明度コントロールでは、次のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="8c346-172">This version of Surface Brightness Control adds support for the following:</span></span>
- <span data-ttu-id="8c346-173">タッチの遅延が修正されました。</span><span class="sxs-lookup"><span data-stu-id="8c346-173">Touch delay fixes.</span></span>


## <span data-ttu-id="8c346-174">関連トピック</span><span class="sxs-lookup"><span data-stu-id="8c346-174">Related topics</span></span>

- [<span data-ttu-id="8c346-175">バッテリー制限の設定</span><span class="sxs-lookup"><span data-stu-id="8c346-175">Battery limit setting</span></span>](battery-limit.md)
