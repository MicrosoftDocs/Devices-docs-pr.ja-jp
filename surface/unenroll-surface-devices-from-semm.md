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
# SEMM からの Surface デバイスの登録解除

Surface デバイスが Surface Enterprise 管理モード (SEMM) に登録されている場合、証明書はそのデバイスのファームウェアに格納されます。 この証明書と SEMM の登録によって、デバイスが SEMM に登録されているときに、Surface UEFI の設定やオプションに対する承認されていない変更を防ぐことができます。 Surface UEFI 設定の制御をユーザーに対して復元するには、Surface デバイスを SEMM から登録解除する必要があります。これは、"リセット" または "回復" と呼ばれるプロセスです。 SEMM からデバイスの登録を解除するには、Surface UEFI リセットパッケージと回復要求という2つのメソッドを使用できます。

>[!WARNING]
>SEMM からデバイスの登録を解除して Surface UEFI 設定のユーザーコントロールを復元するには、SEMM でデバイスを登録するために使用された SEMM 証明書を持っている必要があります。 この証明書が消失または破損した場合、SEMM から登録を解除することはできません。 SEMM 証明書をバックアップして保護します。

SEMM の詳細については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」を参照してください。

##  <a name="unenroll-a-surface-device-from-semm-with-a-surface-uefi-reset-package"></a>Surface UEFI リセットパッケージを使用して、SEMM から Surface デバイスの登録を解除します。

Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除するために使用する主要な方法です。 Surface UEFI 構成パッケージと同様に、リセットパッケージは、デバイスで SEMM を構成する Windows インストーラー (.msi) ファイルです。 構成パッケージとは異なり、リセットパッケージは Surface デバイス上の Surface UEFI 構成を既定の設定にリセットし、SEMM 証明書を削除して、SEMM からデバイスの登録を解除します。

リセットパッケージは、個別のサーフェスデバイス専用に作成されます。 リセットパッケージの作成プロセスを開始するには、登録を解除するデバイスのシリアル番号と、デバイスを登録するために使用される SEMM 証明書が必要です。 Surface デバイスのシリアル番号は、図1のように、Surface UEFI の**PC 情報**ページで確認できます。 このページは、Surface UEFI がパスワードで保護されていて、パスワードが正しく入力されていない場合でも表示されます。

![Surface デバイスのシリアル番号が表示されます](images/surface-semm-unenroll-fig1.png "Serial number of Surface device is displayed")

*図 1.  Surface UEFI PC 情報ページに Surface デバイスのシリアル番号が表示されます*

>[!NOTE]
>Surface UEFI を起動するには、デバイスの**電源が**オフになっている状態で音量を**上げ**て、同時に実行します。 Surface ロゴが表示され、デバイスが起動するまで**音量を**保持します。

Surface UEFI リセットパッケージを作成するには、次の手順を実行します。

1. [スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。
2. **[開始]** をクリックします。
3. 図2に示すように、[**パッケージのリセット**] をクリックします。

   ![[パッケージのリセット] を選択して、SEMM から登録解除する Surface デバイスのパッケージを作成する](images/surface-semm-unenroll-fig2.png "Select Reset Package to create a package to unenroll Surface device from SEMM")

   *図 2.  SEMM から Surface デバイスの登録を解除するパッケージを作成するには、[パッケージのリセット] をクリックします。*

4. [**証明書の保護**] をクリックして、図3に示すように、秘密キー (.pfx) で semm 証明書ファイルを追加します。 証明書ファイルの場所を参照し、ファイルを選択して、[ **OK]** をクリックします。

   ![Surface の UEFI リセットパッケージに SEMM 証明書を追加する](images/surface-semm-unenroll-fig3.png "Add the SEMM certificate to Surface UEFI reset package")

   *図 3.  Surface の UEFI リセットパッケージに SEMM 証明書を追加する*

5. **[次へ]** をクリックします。
6. [SEMM] (図4に示すように) から、登録を解除するデバイスのシリアル番号を入力し、[**ビルド**] をクリックして Surface UEFI リセットパッケージを生成します。

   ![Surface デバイスのシリアル番号を使用して Surface UEFI リセットパッケージを作成する](images/surface-semm-unenroll-fig4.png "Create a Surface UEFI reset package with serial number of Surface device")

   *図 4:  Surface デバイスのシリアル番号を使用して Surface UEFI リセットパッケージを作成する*

7. [名前を**付けて保存**] ダイアログボックスで、Surface UEFI リセットパッケージの名前を指定し、ファイルを保存する場所を参照して、[**保存**] をクリックします。
8. パッケージの生成が完了すると、ページが**正常**に表示されます。 [**終了**] をクリックしてパッケージの作成を完了し、MICROSOFT Surface UEFI コンフィギュレーターを終了します。

Surface デバイス上の Surface UEFI リセットパッケージ Windows インストーラー (.msi) ファイルを実行して、SEMM からデバイスの登録を解除します。 リセットパッケージでは、登録解除操作を実行するには再起動が必要です。 デバイスの登録が解除された後、正常に削除されたことを確認するには、「**プログラムと機能**」 (図 5) で**Microsoft Surface 構成パッケージ**項目が表示されなくなったことを確認します。

![デバイスが「SEMM」に登録されていることを示す画面](images/surface-semm-unenroll-fig5.png "Screen that shows device is enrolled in SEMM")

*図 5:  [プログラムと機能] に Microsoft Surface 構成パッケージ項目が存在することは、デバイスが SEMM に登録されていることを示します。*

##  <a name="unenroll-a-surface-device-from-semm-with-a-recovery-request"></a>回復要求を使用して SEMM から Surface デバイスの登録を解除します。

一部のシナリオでは、Surface UEFI リセットパッケージは、SEMM から Surface デバイスの登録を解除することができない場合があります (たとえば、Windows が使用できなくなった場合)。 これらのシナリオでは、Surface UEFI 内から生成された回復要求を使用して、デバイスの登録を解除できます。 回復要求プロセスは、Surface UEFI パスワードを持っていないデバイスでも開始できます。

回復要求のプロセスは、Surface デバイス上の Surface UEFI から開始され、別のコンピューターで Microsoft Surface UEFI コンフィギュレーターとして承認され、Surface UEFI で完了します。 リセットパッケージと同様に、Microsoft Surface UEFI コンフィギュレーターによる回復要求を承認するには、Surface デバイスの登録に使用した SEMM 証明書へのアクセスが必要です。

回復要求を開始するには、次の手順を実行します。

1. SEMM から Surface UEFI への登録を解除する Surface デバイスを起動します。
2. Surface UEFI パスワードの入力を求めるメッセージが表示された場合は、入力します。
3. 図6に示すように、[**エンタープライズ管理**] ページをクリックします。

   ![エンタープライズ管理ページ](images/surface-semm-unenroll-fig6.png "Enterprise Management page")

   *図 6.  SEMM に登録されているデバイスで、[エンタープライズ管理] ページが Surface UEFI に表示される*

4. [**今すぐ開始**] をクリックまたはクリックします。
5. [次へ] をクリックするか、[**次へ**] をクリックして回復要求のプロセスを開始します
   >[!NOTE]
   >回復要求は、作成後2時間後に期限切れになります。 この時点で回復要求が完了していない場合は、回復要求の処理を再開する必要があります。
6. [ **Semm reset キーの選択**] ページに表示される証明書の一覧から [ **semm 証明書**] を選びます (図7を参照)。次に、[次へ] をクリックするか、[**次へ**] をクリックします。

   ![回復要求の場合は SEMM 証明書を選ぶ](images/surface-semm-unenroll-fig7.png "Select SEMM certificate for your Recovery Request")

   *図 7. 回復要求 (リセット要求) に対して SEMM 証明書を選ぶ*

7. [ **SEMM リセット確認コードの入力**] ページで、[ **QR コード**] または [**テキスト**] ボタンをクリックすると、図8に示すように、回復要求 (リセット要求) が usb ドライブに保存**されます**。これは、図9に示すように、回復要求 (リセット要求) をファイルとして保存することです。

   ![QR コードとして表示される回復要求](images/surface-semm-unenroll-fig8.png "Recovery Request displayed as a QR Code")

   *図 8. QR コードとして表示される回復要求 (リセット要求)*

   ![回復要求を USB ドライブに保存する](images/surface-semm-unenroll-fig9.png "Save a recovery request to a USB drive")

   *図 9. 回復要求 (リセット要求) を USB ドライブに保存する*

   * QR コードの回復要求 (リセット要求) を使うには、モバイルデバイスで QR リーダーアプリを使ってコードを読み取ります。 QR リーダーアプリは、QR コードを英数字の文字列に変換します。 その後、Microsoft Surface UEFI コンフィギュレーターでリセット確認コードを生成する管理者にメールまたはメッセージを送信することができます。
   * USB ドライブにファイルとして保存されている回復要求 (リセット要求) を使用するには、USB ドライブを使用して、Microsoft Surface UEFI コンフィギュレーターを使ってリセット確認コードを生成するコンピューターにファイルを転送します。 また、ファイルを別のデバイスの USB ドライブからコピーして、ネットワーク経由でメール送信または転送することもできます。
   * 回復要求 (リセット要求) をテキストとして使用するには、テキストを直接 Microsoft Surface UEFI コンフィギュレーターに入力します。

8. 別のコンピューターの [スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。
    >[!NOTE]
    >Microsoft Surface UEFI コンフィギュレーターは、SEMM 証明書の証明書チェーンを認証できる環境で実行される必要があります。
9. **[開始]** をクリックします。
10. 図10に示すように、[**回復要求**] をクリックします。

    ![回復要求を承認するためのプロセスを開始する](images/surface-semm-unenroll-fig10.png "Start process to approve a Recovery Request")

    *図 10. [回復要求] をクリックして、回復要求の承認プロセスを開始する*

11. [**証明書の保護**] をクリックして、semm 証明書を使用して回復要求を認証します。
12. SEMM 証明書ファイルを参照して選び、[ **OK]** をクリックします。
13. 図11に示すように、証明書のパスワードの入力を求めるメッセージが表示されたら、証明書ファイルのパスワードを入力して確認し、[ **OK]** をクリックします。

    ![SEMM 証明書のパスワードを入力します。](images/surface-semm-unenroll-fig11.png "Type password for SEMM certificate")

    *図 11. SEMM 証明書のパスワードを入力します。*

14. **[次へ]** をクリックします。
15. 回復要求 (リセット要求) を入力し、[**生成**] をクリックして、リセット確認コードを作成します (図12を参照)。

    ![回復要求を入力する](images/surface-semm-unenroll-fig12.png "Enter the recovery request")

    *図 12. 回復要求 (リセット要求) を入力する*

    * リセットされる Surface デバイス上のテキストとして回復要求 (リセット要求) を表示した場合は、キーボードを使用して、指定されたフィールドの回復要求 (リセット要求) を入力します。
    * QR コードとして回復要求 (リセット要求) を表示し、メッセージングまたはメールアプリケーションを使用して、Microsoft Surface UEFI コンフィギュレーターを備えたコンピューターにコードを送信した場合は、コードを指定されたフィールドにコピーして貼り付けます。
    * 回復要求 (リセット要求) をファイルとして USB ドライブに保存した場合は、[**インポート**] をクリックし、回復要求 (リセット要求) ファイルを参照して選び、[ **OK**] をクリックします。

16. 図13に示すように、リセット確認コードが Microsoft Surface UEFI コンフィギュレーターに表示されます。

    ![再設定の確認コードの表示](images/surface-semm-unenroll-fig13.png "Display of the reset verification code")

    *図 13. Microsoft Surface UEFI コンフィギュレーターに表示されるリセット確認コード*

    * [**共有**] ボタンをクリックして、リセットの確認コードをメールで送信します。

17. Surface デバイスの提供フィールド (図 8) に再設定の確認コードを入力し、[**確認**] をクリックまたは押してデバイスをリセットし、semm からデバイスの登録を解除します。
18. 「 **Semm リセット成功**ページ」で「**今すぐ再起動**」をクリックして、「semm」で unenrollment を完了します。

    ![SEMM からの成功した unenrollment の例](images/surface-semm-unenroll-fig14.png "Example display of successful unenrollment from SEMM")

    *図 14. SEMM からの unenrollment 成功*

19. [Microsoft Surface UEFI コンフィギュレーターで**終了**] をクリックして回復要求 (リセット要求) プロセスを完了し、MICROSOFT Surface uefi コンフィギュレーターを終了します。


