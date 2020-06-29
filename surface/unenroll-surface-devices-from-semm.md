---
title: SEMM (Surface) からの登録解除 Surface デバイス
description: Surface UEFI リセットパッケージまたは回復要求オプションを使用して、SEMM からデバイスの登録を解除する方法について説明します。
keywords: surface enterprise 管理
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: aa24ff1ac8a93ebc8078490c5e0c8fa34c940a25
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834606"
---
# <span data-ttu-id="1fbff-104">SEMM からの Surface デバイスの登録解除</span><span class="sxs-lookup"><span data-stu-id="1fbff-104">Unenroll Surface devices from SEMM</span></span>

<span data-ttu-id="1fbff-105">Surface デバイスが Surface Enterprise 管理モード (SEMM) に登録されている場合、証明書はそのデバイスのファームウェアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-105">When a Surface device is enrolled in Surface Enterprise Management Mode (SEMM), a certificate is stored in the firmware of that device.</span></span> <span data-ttu-id="1fbff-106">この証明書と SEMM の登録によって、デバイスが SEMM に登録されているときに、Surface UEFI の設定やオプションに対する承認されていない変更を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-106">The presence of that certificate and the enrollment in SEMM prevent any unauthorized changes to Surface UEFI settings or options while the device is enrolled in SEMM.</span></span> <span data-ttu-id="1fbff-107">Surface UEFI 設定の制御をユーザーに対して復元するには、Surface デバイスを SEMM から登録解除する必要があります。これは、"リセット" または "回復" と呼ばれるプロセスです。</span><span class="sxs-lookup"><span data-stu-id="1fbff-107">To restore control of Surface UEFI settings to the user, the Surface device must be unenrolled from SEMM, a process sometimes described as reset or recovery.</span></span> <span data-ttu-id="1fbff-108">SEMM からデバイスの登録を解除するには、Surface UEFI リセットパッケージと回復要求という2つのメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-108">There are two methods you can use to unenroll a device from SEMM—a Surface UEFI reset package and a Recovery Request.</span></span>

>[!WARNING]
><span data-ttu-id="1fbff-109">SEMM からデバイスの登録を解除して Surface UEFI 設定のユーザーコントロールを復元するには、SEMM でデバイスを登録するために使用された SEMM 証明書を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbff-109">To unenroll a device from SEMM and restore user control of Surface UEFI settings, you must have the SEMM certificate that was used to enroll the device in SEMM.</span></span> <span data-ttu-id="1fbff-110">この証明書が消失または破損した場合、SEMM から登録を解除することはできません。</span><span class="sxs-lookup"><span data-stu-id="1fbff-110">If this certificate becomes lost or corrupted, it is not possible to unenroll from SEMM.</span></span> <span data-ttu-id="1fbff-111">SEMM 証明書をバックアップして保護します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-111">Back up and protect your SEMM certificate accordingly.</span></span>

<span data-ttu-id="1fbff-112">SEMM の詳細については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fbff-112">For more information about SEMM, see [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).</span></span>

## <span data-ttu-id="1fbff-113">Surface UEFI リセットパッケージを使用して、SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-113">Unenroll a Surface device from SEMM with a Surface UEFI reset package</span></span>

<span data-ttu-id="1fbff-114">Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除するために使用する主要な方法です。</span><span class="sxs-lookup"><span data-stu-id="1fbff-114">The Surface UEFI reset package is the primary method you use to unenroll a Surface device from SEMM.</span></span> <span data-ttu-id="1fbff-115">Surface UEFI 構成パッケージと同様に、リセットパッケージは、デバイスで SEMM を構成する Windows インストーラー (.msi) ファイルです。</span><span class="sxs-lookup"><span data-stu-id="1fbff-115">Like a Surface UEFI configuration package, the reset package is a Windows Installer (.msi) file that configures SEMM on the device.</span></span> <span data-ttu-id="1fbff-116">構成パッケージとは異なり、リセットパッケージは Surface デバイス上の Surface UEFI 構成を既定の設定にリセットし、SEMM 証明書を削除して、SEMM からデバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-116">Unlike the configuration package, the reset package will reset the Surface UEFI configuration on a Surface device to its default settings, remove the SEMM certificate, and unenroll the device from SEMM.</span></span>

<span data-ttu-id="1fbff-117">リセットパッケージは、個別のサーフェスデバイス専用に作成されます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-117">Reset packages are created specifically for an individual Surface device.</span></span> <span data-ttu-id="1fbff-118">リセットパッケージの作成プロセスを開始するには、登録を解除するデバイスのシリアル番号と、デバイスを登録するために使用される SEMM 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbff-118">To begin the process of creating a reset package, you will need the serial number of the device you want to unenroll, as well as the SEMM certificate used to enroll the device.</span></span> <span data-ttu-id="1fbff-119">Surface デバイスのシリアル番号は、図1のように、Surface UEFI の**PC 情報**ページで確認できます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-119">You can find the serial number of your Surface device on the **PC information** page of Surface UEFI, as shown in Figure 1.</span></span> <span data-ttu-id="1fbff-120">このページは、Surface UEFI がパスワードで保護されていて、パスワードが正しく入力されていない場合でも表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-120">This page is displayed even if Surface UEFI is password protected and the incorrect password is entered.</span></span>

![Surface デバイスのシリアル番号が表示されます](images/surface-semm-unenroll-fig1.png "Serial number of Surface device is displayed")

*<span data-ttu-id="1fbff-122">図 1. </span><span class="sxs-lookup"><span data-stu-id="1fbff-122">Figure 1.</span></span> <span data-ttu-id="1fbff-123">Surface UEFI PC 情報ページに Surface デバイスのシリアル番号が表示されます</span><span class="sxs-lookup"><span data-stu-id="1fbff-123">The serial number of the Surface device is displayed on the Surface UEFI PC information page</span></span>*

>[!NOTE]
><span data-ttu-id="1fbff-124">Surface UEFI を起動するには、デバイスの**電源が**オフになっている状態で音量を**上げ**て、同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-124">To boot to Surface UEFI, press **Volume Up** and **Power** simultaneously while the device is off.</span></span> <span data-ttu-id="1fbff-125">Surface ロゴが表示され、デバイスが起動するまで**音量を**保持します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-125">Hold **Volume Up** until the Surface logo is displayed and the device begins to boot.</span></span>

<span data-ttu-id="1fbff-126">Surface UEFI リセットパッケージを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-126">To create a Surface UEFI reset package, follow these steps:</span></span>

1. <span data-ttu-id="1fbff-127">[スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-127">Open Microsoft Surface UEFI Configurator from the Start menu.</span></span>
2. <span data-ttu-id="1fbff-128">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-128">Click **Start**.</span></span>
3. <span data-ttu-id="1fbff-129">図2に示すように、[**パッケージのリセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-129">Click **Reset Package**, as shown in Figure 2.</span></span>

   ![[パッケージのリセット] を選択して、SEMM から登録解除する Surface デバイスのパッケージを作成する](images/surface-semm-unenroll-fig2.png "Select Reset Package to create a package to unenroll Surface device from SEMM")

   *<span data-ttu-id="1fbff-131">図 2. </span><span class="sxs-lookup"><span data-stu-id="1fbff-131">Figure 2.</span></span> <span data-ttu-id="1fbff-132">SEMM から Surface デバイスの登録を解除するパッケージを作成するには、[パッケージのリセット] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-132">Click Reset Package to create a package to unenroll a Surface device from SEMM</span></span>*

4. <span data-ttu-id="1fbff-133">[**証明書の保護**] をクリックして、図3に示すように、秘密キー (.pfx) で semm 証明書ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-133">Click **Certificate Protection** to add your SEMM certificate file with private key (.pfx), as shown in Figure 3.</span></span> <span data-ttu-id="1fbff-134">証明書ファイルの場所を参照し、ファイルを選択して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-134">Browse to the location of your certificate file, select the file, and then click **OK**.</span></span>

   ![Surface の UEFI リセットパッケージに SEMM 証明書を追加する](images/surface-semm-unenroll-fig3.png "Add the SEMM certificate to Surface UEFI reset package")

   *<span data-ttu-id="1fbff-136">図 3. </span><span class="sxs-lookup"><span data-stu-id="1fbff-136">Figure 3.</span></span> <span data-ttu-id="1fbff-137">Surface の UEFI リセットパッケージに SEMM 証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="1fbff-137">Add the SEMM certificate to a Surface UEFI reset package</span></span>*

5. <span data-ttu-id="1fbff-138">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-138">Click **Next**.</span></span>
6. <span data-ttu-id="1fbff-139">[SEMM] (図4に示すように) から、登録を解除するデバイスのシリアル番号を入力し、[**ビルド**] をクリックして Surface UEFI リセットパッケージを生成します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-139">Type the serial number of the device you want to unenroll from SEMM (as shown in Figure 4), and then click **Build** to generate the Surface UEFI reset package.</span></span>

   ![Surface デバイスのシリアル番号を使用して Surface UEFI リセットパッケージを作成する](images/surface-semm-unenroll-fig4.png "Create a Surface UEFI reset package with serial number of Surface device")

   *<span data-ttu-id="1fbff-141">図 4: </span><span class="sxs-lookup"><span data-stu-id="1fbff-141">Figure 4.</span></span> <span data-ttu-id="1fbff-142">Surface デバイスのシリアル番号を使用して Surface UEFI リセットパッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="1fbff-142">Use the serial number of your Surface device to create a Surface UEFI reset package</span></span>*

7. <span data-ttu-id="1fbff-143">[名前を**付けて保存**] ダイアログボックスで、Surface UEFI リセットパッケージの名前を指定し、ファイルを保存する場所を参照して、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-143">In the **Save As** dialog box, specify a name for the Surface UEFI reset package, browse to the location where you would like to save the file, and then click **Save**.</span></span>
8. <span data-ttu-id="1fbff-144">パッケージの生成が完了すると、ページが**正常**に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-144">When the package generation has completed, the **Successful** page is displayed.</span></span> <span data-ttu-id="1fbff-145">[**終了**] をクリックしてパッケージの作成を完了し、MICROSOFT Surface UEFI コンフィギュレーターを終了します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-145">Click **End** to complete package creation and close Microsoft Surface UEFI Configurator.</span></span>

<span data-ttu-id="1fbff-146">Surface デバイス上の Surface UEFI リセットパッケージ Windows インストーラー (.msi) ファイルを実行して、SEMM からデバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-146">Run the Surface UEFI reset package Windows Installer (.msi) file on the Surface device to unenroll the device from SEMM.</span></span> <span data-ttu-id="1fbff-147">リセットパッケージでは、登録解除操作を実行するには再起動が必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbff-147">The reset package will require a reboot to perform the unenroll operation.</span></span> <span data-ttu-id="1fbff-148">デバイスの登録が解除された後、正常に削除されたことを確認するには、「**プログラムと機能**」 (図 5) で**Microsoft Surface 構成パッケージ**項目が表示されなくなったことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-148">After the device has been unenrolled, you can verify the successful removal by ensuring that the **Microsoft Surface Configuration Package** item in **Programs and Features** (shown in Figure 5) is no longer present.</span></span>

![デバイスが「SEMM」に登録されていることを示す画面](images/surface-semm-unenroll-fig5.png "Screen that shows device is enrolled in SEMM")

*<span data-ttu-id="1fbff-150">図 5: </span><span class="sxs-lookup"><span data-stu-id="1fbff-150">Figure 5.</span></span> <span data-ttu-id="1fbff-151">[プログラムと機能] に Microsoft Surface 構成パッケージ項目が存在することは、デバイスが SEMM に登録されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-151">The presence of the Microsoft Surface Configuration Package item in Programs and Features indicates that the device is enrolled in SEMM</span></span>*

## <span data-ttu-id="1fbff-152">回復要求を使用して SEMM から Surface デバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-152">Unenroll a Surface device from SEMM with a Recovery Request</span></span>

<span data-ttu-id="1fbff-153">一部のシナリオでは、Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除することができない場合があります (たとえば、Windows が使用できなくなった場合)。</span><span class="sxs-lookup"><span data-stu-id="1fbff-153">In some scenarios, a Surface UEFI reset package may not be a viable option to unenroll a Surface device from SEMM (for example, where Windows has become unusable).</span></span> <span data-ttu-id="1fbff-154">これらのシナリオでは、Surface UEFI 内から生成された回復要求を使用して、デバイスの登録を解除できます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-154">In these scenarios you can unenroll the device by using a Recovery Request generated from within Surface UEFI.</span></span> <span data-ttu-id="1fbff-155">回復要求プロセスは、Surface UEFI パスワードを持っていないデバイスでも開始できます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-155">The Recovery Request process can be initiated even on devices where you do not have the Surface UEFI password.</span></span>

<span data-ttu-id="1fbff-156">回復要求のプロセスは、Surface デバイス上の Surface UEFI から開始され、別のコンピューターで Microsoft Surface UEFI コンフィギュレーターとして承認され、Surface UEFI で完了します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-156">The Recovery Request process is initiated from Surface UEFI on the Surface device, approved with Microsoft Surface UEFI Configurator on another computer, and then completed in Surface UEFI.</span></span> <span data-ttu-id="1fbff-157">リセットパッケージと同様に、Microsoft Surface UEFI コンフィギュレーターによる回復要求を承認するには、Surface デバイスの登録に使用した SEMM 証明書へのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="1fbff-157">Like the reset package, approving a Recovery Request with Microsoft Surface UEFI Configurator requires access to the SEMM certificate that was used to enroll the Surface device.</span></span>

<span data-ttu-id="1fbff-158">回復要求を開始するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-158">To initiate a Recovery Request, follow these steps:</span></span>

1. <span data-ttu-id="1fbff-159">SEMM から Surface UEFI への登録を解除する Surface デバイスを起動します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-159">Boot the Surface device that is to be unenrolled from SEMM to Surface UEFI.</span></span>
2. <span data-ttu-id="1fbff-160">Surface UEFI パスワードの入力を求めるメッセージが表示された場合は、入力します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-160">Type the Surface UEFI password if you are prompted to do so.</span></span>
3. <span data-ttu-id="1fbff-161">図6に示すように、[**エンタープライズ管理**] ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-161">Click the **Enterprise management** page, as shown in Figure 6.</span></span>

   ![エンタープライズ管理ページ](images/surface-semm-unenroll-fig6.png "Enterprise Management page")

   *<span data-ttu-id="1fbff-163">図 6. </span><span class="sxs-lookup"><span data-stu-id="1fbff-163">Figure 6.</span></span> <span data-ttu-id="1fbff-164">SEMM に登録されているデバイスで、[エンタープライズ管理] ページが Surface UEFI に表示される</span><span class="sxs-lookup"><span data-stu-id="1fbff-164">The Enterprise management page is displayed in Surface UEFI on devices enrolled in SEMM</span></span>*

4. <span data-ttu-id="1fbff-165">[**今すぐ開始**] をクリックまたはクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-165">Click or press **Get Started**.</span></span>
5. <span data-ttu-id="1fbff-166">[次へ] をクリックするか、[**次へ**] をクリックして回復要求のプロセスを開始します</span><span class="sxs-lookup"><span data-stu-id="1fbff-166">Click or press **Next** to begin the Recovery Request process.</span></span>
   >[!NOTE]
   ><span data-ttu-id="1fbff-167">回復要求は、作成後2時間後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="1fbff-167">A Recovery Request expires two hours after it is created.</span></span> <span data-ttu-id="1fbff-168">この時点で回復要求が完了していない場合は、回復要求の処理を再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbff-168">If a Recovery Request is not completed in this time, you will have to restart the Recovery Request process.</span></span>
6. <span data-ttu-id="1fbff-169">[ **Semm reset キーの選択**] ページに表示される証明書の一覧から [ **semm 証明書**] を選びます (図7を参照)。次に、[次へ] をクリックするか、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-169">Select **SEMM Certificate** from the list of certificates displayed on the **Choose a SEMM reset key** page (shown in Figure 7), and then click or press **Next**.</span></span>

   ![回復要求の場合は SEMM 証明書を選ぶ](images/surface-semm-unenroll-fig7.png "Select SEMM certificate for your Recovery Request")

   *<span data-ttu-id="1fbff-171">図 7.</span><span class="sxs-lookup"><span data-stu-id="1fbff-171">Figure 7.</span></span> <span data-ttu-id="1fbff-172">回復要求 (リセット要求) に対して SEMM 証明書を選ぶ</span><span class="sxs-lookup"><span data-stu-id="1fbff-172">Choose SEMM Certificate for your Recovery Request (Reset Request)</span></span>*

7. <span data-ttu-id="1fbff-173">[ **SEMM リセット確認コードの入力**] ページで、[ **QR コード**] または [**テキスト**] ボタンをクリックすると、図8に示すように、回復要求 (リセット要求) が usb ドライブに保存**されます**。これは、図9に示すように、回復要求 (リセット要求) をファイルとして保存することです。</span><span class="sxs-lookup"><span data-stu-id="1fbff-173">On the **Enter SEMM reset verification code** page you can click the **QR Code** or **Text** buttons to display your Recovery Request (Reset Request) as shown in Figure 8, or the **USB** button to save your Recovery Request (Reset Request) as a file to a USB drive, as shown in Figure 9.</span></span>

   ![QR コードとして表示される回復要求](images/surface-semm-unenroll-fig8.png "Recovery Request displayed as a QR Code")

   *<span data-ttu-id="1fbff-175">図 8.</span><span class="sxs-lookup"><span data-stu-id="1fbff-175">Figure 8.</span></span> <span data-ttu-id="1fbff-176">QR コードとして表示される回復要求 (リセット要求)</span><span class="sxs-lookup"><span data-stu-id="1fbff-176">A Recovery Request (Reset Request) displayed as a QR Code</span></span>*

   ![回復要求を USB ドライブに保存する](images/surface-semm-unenroll-fig9.png "Save a recovery request to a USB drive")

   *<span data-ttu-id="1fbff-178">図 9.</span><span class="sxs-lookup"><span data-stu-id="1fbff-178">Figure 9.</span></span> <span data-ttu-id="1fbff-179">回復要求 (リセット要求) を USB ドライブに保存する</span><span class="sxs-lookup"><span data-stu-id="1fbff-179">Save a Recovery Request (Reset Request) to a USB drive</span></span>*

   * <span data-ttu-id="1fbff-180">QR コードの回復要求 (リセット要求) を使うには、モバイルデバイスで QR リーダーアプリを使ってコードを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1fbff-180">To use a QR Code Recovery Request (Reset Request), use a QR reader app on a mobile device to read the code.</span></span> <span data-ttu-id="1fbff-181">QR リーダーアプリは、QR コードを英数字の文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-181">The QR reader app will translate the QR code into an alphanumeric string.</span></span> <span data-ttu-id="1fbff-182">その後、Microsoft Surface UEFI コンフィギュレーターでリセット確認コードを生成する管理者にメールまたはメッセージを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-182">You can then email or message that string to the administrator that will produce the reset verification code with Microsoft Surface UEFI Configurator.</span></span>
   * <span data-ttu-id="1fbff-183">USB ドライブにファイルとして保存されている回復要求 (リセット要求) を使用するには、USB ドライブを使用して、Microsoft Surface UEFI コンフィギュレーターを使ってリセット確認コードを生成するコンピューターにファイルを転送します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-183">To use a Recovery Request (Reset Request) saved to a USB drive as a file, use the USB drive to transfer the file to the computer where Microsoft Surface UEFI Configurator will be used to produce the Reset Verification Code.</span></span> <span data-ttu-id="1fbff-184">また、ファイルを別のデバイスの USB ドライブからコピーして、ネットワーク経由でメール送信または転送することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-184">The file can also be copied from the USB drive on another device to be emailed or transferred over the network.</span></span>
   * <span data-ttu-id="1fbff-185">回復要求 (リセット要求) をテキストとして使用するには、テキストを直接 Microsoft Surface UEFI コンフィギュレーターに入力します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-185">To use the Recovery Request (Reset Request) as text, simply type the text directly into Microsoft Surface UEFI Configurator.</span></span>

8. <span data-ttu-id="1fbff-186">別のコンピューターの [スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-186">Open Microsoft Surface UEFI Configurator from the Start menu on another computer.</span></span>
    >[!NOTE]
    ><span data-ttu-id="1fbff-187">Microsoft Surface UEFI コンフィギュレーターは、SEMM 証明書の証明書チェーンを認証できる環境で実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fbff-187">Microsoft Surface UEFI Configurator must run in an environment that is able to authenticate the certificate chain for the SEMM certificate.</span></span>
9. <span data-ttu-id="1fbff-188">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-188">Click **Start**.</span></span>
10. <span data-ttu-id="1fbff-189">図10に示すように、[**回復要求**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-189">Click **Recovery Request**, as shown in Figure 10.</span></span>

    ![回復要求を承認するためのプロセスを開始する](images/surface-semm-unenroll-fig10.png "Start process to approve a Recovery Request")

    *<span data-ttu-id="1fbff-191">図 10.</span><span class="sxs-lookup"><span data-stu-id="1fbff-191">Figure 10.</span></span> <span data-ttu-id="1fbff-192">[回復要求] をクリックして、回復要求の承認プロセスを開始する</span><span class="sxs-lookup"><span data-stu-id="1fbff-192">Click Recovery Request to begin the process to approve a Recovery Request</span></span>*

11. <span data-ttu-id="1fbff-193">[**証明書の保護**] をクリックして、semm 証明書を使用して回復要求を認証します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-193">Click **Certificate Protection** to authenticate the Recovery Request with the SEMM certificate.</span></span>
12. <span data-ttu-id="1fbff-194">SEMM 証明書ファイルを参照して選び、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-194">Browse to and select your SEMM certificate file, and then click **OK**.</span></span>
13. <span data-ttu-id="1fbff-195">図11に示すように、証明書のパスワードの入力を求めるメッセージが表示されたら、証明書ファイルのパスワードを入力して確認し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-195">When you are prompted to enter the certificate password as shown in Figure 11, type and confirm the password for the certificate file, and then click **OK**.</span></span>

    ![SEMM 証明書のパスワードを入力します。](images/surface-semm-unenroll-fig11.png "Type password for SEMM certificate")

    *<span data-ttu-id="1fbff-197">図 11.</span><span class="sxs-lookup"><span data-stu-id="1fbff-197">Figure 11.</span></span> <span data-ttu-id="1fbff-198">SEMM 証明書のパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-198">Type the password for the SEMM certificate</span></span>*

14. <span data-ttu-id="1fbff-199">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-199">Click **Next**.</span></span>
15. <span data-ttu-id="1fbff-200">回復要求 (リセット要求) を入力し、[**生成**] をクリックして、リセット確認コードを作成します (図12を参照)。</span><span class="sxs-lookup"><span data-stu-id="1fbff-200">Enter the Recovery Request (Reset Request), and then click **Generate** to create a reset verification code (as shown in Figure 12).</span></span>

    ![回復要求を入力する](images/surface-semm-unenroll-fig12.png "Enter the recovery request")

    *<span data-ttu-id="1fbff-202">図 12.</span><span class="sxs-lookup"><span data-stu-id="1fbff-202">Figure 12.</span></span> <span data-ttu-id="1fbff-203">回復要求 (リセット要求) を入力する</span><span class="sxs-lookup"><span data-stu-id="1fbff-203">Enter the Recovery Request (Reset Request)</span></span>*

    * <span data-ttu-id="1fbff-204">リセットされる Surface デバイス上のテキストとして回復要求 (リセット要求) を表示した場合は、キーボードを使用して、指定されたフィールドの回復要求 (リセット要求) を入力します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-204">If you displayed the Recovery Request (Reset Request) as text on the Surface device being reset, use the keyboard to type the Recovery Request (Reset Request)  in the provided field.</span></span>
    * <span data-ttu-id="1fbff-205">QR コードとして回復要求 (リセット要求) を表示し、メッセージングまたはメールアプリケーションを使用して、Microsoft Surface UEFI コンフィギュレーターを備えたコンピューターにコードを送信した場合は、コードを指定されたフィールドにコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-205">If you displayed the Recovery Request (Reset Request) as a QR Code and then used a messaging or email application to send the code to the computer with Microsoft Surface UEFI Configurator, copy and paste the code into the provided field.</span></span>
    * <span data-ttu-id="1fbff-206">回復要求 (リセット要求) をファイルとして USB ドライブに保存した場合は、[**インポート**] をクリックし、回復要求 (リセット要求) ファイルを参照して選び、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fbff-206">If you saved the Recovery Request (Reset Request) as a file to a USB drive, click the **Import** button, browse to and select the Recovery Request (Reset Request) file, and then click **OK**.</span></span>

16. <span data-ttu-id="1fbff-207">図13に示すように、リセット確認コードが Microsoft Surface UEFI コンフィギュレーターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fbff-207">The reset verification code is displayed in Microsoft Surface UEFI Configurator, as shown in Figure 13.</span></span>

    ![再設定の確認コードの表示](images/surface-semm-unenroll-fig13.png "Display of the reset verification code")

    *<span data-ttu-id="1fbff-209">図 13.</span><span class="sxs-lookup"><span data-stu-id="1fbff-209">Figure 13.</span></span> <span data-ttu-id="1fbff-210">Microsoft Surface UEFI コンフィギュレーターに表示されるリセット確認コード</span><span class="sxs-lookup"><span data-stu-id="1fbff-210">The reset verification code displayed in Microsoft Surface UEFI Configurator</span></span>*

    * <span data-ttu-id="1fbff-211">[**共有**] ボタンをクリックして、リセットの確認コードをメールで送信します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-211">Click the **Share** button to send the reset verification code by email.</span></span>

17. <span data-ttu-id="1fbff-212">Surface デバイスの提供フィールド (図 8) に再設定の確認コードを入力し、[**確認**] をクリックまたは押してデバイスをリセットし、semm からデバイスの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-212">Enter the reset verification code in the provided field on the Surface device (shown in Figure 8), and then click or press **Verify** to reset the device and unenroll the device from SEMM.</span></span>
18. <span data-ttu-id="1fbff-213">「 **Semm リセット成功**ページ」で「**今すぐ再起動**」をクリックして、「semm」で unenrollment を完了します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-213">Click or press **Restart now** on the **SEMM reset successful** page to complete the unenrollment from SEMM, as shown in Figure 14.</span></span>

    ![SEMM からの成功した unenrollment の例](images/surface-semm-unenroll-fig14.png "Example display of successful unenrollment from SEMM")

    *<span data-ttu-id="1fbff-215">図 14.</span><span class="sxs-lookup"><span data-stu-id="1fbff-215">Figure 14.</span></span> <span data-ttu-id="1fbff-216">SEMM からの unenrollment 成功</span><span class="sxs-lookup"><span data-stu-id="1fbff-216">Successful unenrollment from SEMM</span></span>*

19. <span data-ttu-id="1fbff-217">[Microsoft Surface UEFI コンフィギュレーターで**終了**] をクリックして回復要求 (リセット要求) プロセスを完了し、MICROSOFT Surface uefi コンフィギュレーターを終了します。</span><span class="sxs-lookup"><span data-stu-id="1fbff-217">Click **End** in Microsoft Surface UEFI Configurator to complete the Recovery Request (Reset Request) process and close Microsoft Surface UEFI Configurator.</span></span>


