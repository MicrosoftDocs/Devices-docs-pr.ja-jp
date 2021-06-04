---
title: SEMM を使用して Surface デバイスを登録および構成する (Surface)
description: Surface UEFI 構成パッケージを作成して Surface UEFI の設定を制御する方法と、SEMM に Surface デバイスを登録する方法について説明します。
keywords: Surface Enterprise の管理
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: hachinda
manager: laurawi
ms.date: 1/15/2021
ms.openlocfilehash: f310b4a43a8a0fc0e77295344ac723770ce821bc
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271064"
---
# SEMM による Surface デバイスの登録と構成

Microsoft Surface Enterprise 管理モード (SEMM) を使用すると、Surface デバイスで Surface UEFI の設定を安全に構成し、組織内の Surface デバイスでそれらの設定を管理できます。 SURFACE デバイスが SEMM によって管理されている場合、そのデバイスは登録 *されている* (アクティブ化とも呼ばれる) と見なされます。 この記事では、Surface UEFI の設定を制御するだけでなく、SEMM に Surface デバイスを登録する Surface UEFI 構成パッケージを作成する方法について説明します。

SEMM の概要については、「Microsoft Surface Enterprise 管理モード」 [を参照してください](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)。

SEMM の代わりに、新しい Surface デバイスは、Microsoft Intune を介したファームウェア設定のサブセットのリモート管理をサポートします。 詳しくは [、Surface UEFI 設定の Intune 管理に関するページをご覧ください](surface-manage-dfci-guide.md)。

> [!NOTE]
> SEMM は、UEFI マネージャーを介して Surface Pro X でのみサポートされます。 詳細については、「Surface Pro X の展開、管理、サービス提供」 [を参照してください](surface-pro-arm-app-management.md)。

#### Microsoft Surface UEFI コンフィエーターをダウンロードしてインストールする

SEMM パッケージの作成に使用されるツールは、Microsoft Surface UEFI コンフィエーターです。 Microsoft Surface UEFI コンフィエーターは [、Microsoft](https://www.microsoft.com/download/details.aspx?id=46703) ダウンロード センターの Surface Tools for IT ページからダウンロードできます。
Microsoft Surface UEFI Configurator Windows インストーラー (.msi) ファイルを実行して、ツールのインストールを開始します。 インストーラーが完了したら、スタート メニューの [すべてのアプリ] セクションで Microsoft Surface UEFI コンフィエーターを探します。

>[!NOTE]
>Microsoft Surface UEFI コンフィエーターは、Windows 10 でのみサポートされています。

##  <a name="create-a-surface-uefi-configuration-package"></a>Surface UEFI 構成パッケージを作成する

Surface UEFI 構成パッケージは、SEMM で管理される Surface デバイスに Surface UEFI 設定の新しい構成を適用する役割と、SEMM に Surface デバイスを登録する役割の両方を実行します。 構成パッケージを作成するには、各 Surface デバイスで UEFI 設定の構成をセキュリティで保護するために、SEMM で使用する署名証明書が必要です。 SEMM 証明書の要件の詳細については、Microsoft Surface Enterprise 管理モード [を参照してください](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)。

Surface UEFI 構成パッケージを作成するには、次の手順を実行します。

1. スタート メニューから Microsoft Surface UEFI コンフィエーターを開きます。
2. **[開始]** をクリックします。
3. 図 1 **に示**すように、[構成パッケージ] をクリックします。

   ![SEMM 登録用のパッケージを作成する](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *図 1.  SEMM の登録と構成用のパッケージを作成するには、[構成パッケージ] を選択します。*

4. 図 2 **に示** すように、[証明書の保護] をクリックして、エクスポートした証明書ファイルをプライベート キー (.pfx) と一緒に追加します。 証明書ファイルの場所を参照し、ファイルを選択して **、[OK]** をクリックします。

   ![SEM 証明書と Surface UEFI パスワードを構成パッケージに追加する](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *図 2.  SEMM 証明書と Surface UEFI パスワードを Surface UEFI 構成パッケージに追加する*

5. 証明書のパスワードの確認を求めるメッセージが表示されたら、証明書ファイルのパスワードを入力して確認し **、[OK]** をクリックします。
6. パスワード **保護をクリック** して、Surface UEFI にパスワードを追加します。 このパスワードは、UEFI を起動するたびに必要になります。 このパスワードを入力しない場合は **、PC**情報 、[ **会社**情報]、[ **エンタープライズ**管理]、および [ **終了** ] ページだけが表示されます。 この手順は省略可能です。
7. メッセージが表示されたら、選択した Surface UEFI のパスワードを入力して確認し **、[OK]** をクリックします。 既存の Surface UEFI パスワードをクリアする場合は、パスワード フィールドを空白のままにします。
8. Surface UEFI パッケージを特定のデバイスに適用しない場合は、[ターゲットにする**Surface**の種類の選択] ページで、対応する Surface Book または Surface Pro 4 イメージの下にある**** スライダーをクリックして、オフの位置に配置します。 (図 3 に示すように)
   > [!NOTE] 
   > 既定では、デバイスを選択する必要があります。デバイスは選択されません。

   ![パッケージ互換性のためにデバイスを選択する](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *図 3.  パッケージの互換性を確保するデバイスを選択する*

9. **[次へ]** をクリックします。
10. 管理対象 Surface デバイスでコンポーネントを非アクティブ化する場合は、[**** アクティブ化または非アクティブ化するコンポーネントの選択] ページで、非アクティブ化するデバイスまたはデバイスのグループの横にあるスライダーをクリックして、スライダーが**オフ**の位置に配置されます。 (図 4 を参照)。各デバイスの既定の構成は **オンです**。 すべてのスライダー **を既定** の位置に戻す場合は、[リセット] ボタンをクリックします。

    ![Surface コンポーネントを無効または有効にする](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *図 4:  個々の Surface コンポーネントを無効または有効にする*

11. **[次へ]** をクリックします。
12. Surface UEFI または Surface UEFI ページの表示で高度なオプションを有効**** または無効にするには、[デバイスの詳細設定の選択] ページで、目的の設定の横にあるスライダーをクリックして、そのオプションを**オン**または**オフに構成**します (図 5 を参照)。 **UEFI**フロント ページ セクションでは、セキュリティ、デバイス、ブートのスライダー**** を使って****、Surface UEFI で起動するユーザーが利用できるページを制御できます。 **** (Surface UEFI の設定について詳しくは [、「Surface UEFI の設定の管理」をご覧ください](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings))。パッケージ **を生成** して保存するオプションの選択が完了したら、[ビルド] をクリックします。

    ![高度な Surface UEFI 設定と Surface UEFI ページの制御](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *図 5:  SEMM による高度な Surface UEFI 設定と Surface UEFI ページの制御*

13. [名前 **を付けて** 保存] ダイアログ ボックスで、Surface UEFI 構成パッケージの名前を指定し、ファイルを保存する場所を参照して、[保存] をクリック **します**。
14. パッケージを作成して保存すると、[成功] **ページ** が表示されます。

>[!NOTE]
>図 6 に示すように、このページに表示される証明書の拇印文字を記録します。 SEMM での新しい Surface デバイスの登録を確認するには、これらの文字が必要です。 **[End]** をクリックしてパッケージの作成を完了し、Microsoft Surface UEFI コンフィエーターを閉じます。

![証明書の拇印文字の表示](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*図 6.  証明書の拇印の最後の 2 文字が [成功] ページに表示されます。*

Surface UEFI 構成パッケージを作成したら、Surface デバイスを登録または構成できます。

>[!NOTE]
>Surface UEFI 構成パッケージが作成されると、構成パッケージの設定とオプションの詳細を含むログ ファイルがデスクトップに作成されます。

##  <a name="enroll-a-surface-device-in-semm"></a>SEMM での Surface デバイスの登録
Surface UEFI 構成パッケージが実行されると、SEMM 証明書と Surface UEFI 構成ファイルが Surface デバイスのファームウェア ストレージに格納されます。 Surface デバイスが再起動すると、Surface UEFI がこれらのファイルを処理し、図 7 に示すように、Surface UEFI 構成の適用または SEMM での Surface デバイスの登録のプロセスを開始します。

![Surface UEFI または登録の構成に関する SEMM プロセス](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*図 7. Surface UEFI の構成または Surface デバイスの登録のための SEMM プロセス*

SEMM に Surface デバイスを登録するプロセスを開始する前に、証明書の拇印の最後の 2 文字が手に入っている必要があります。 デバイスの登録を確認するには、これらの文字が必要です (図 6 を参照)。

SURFACE UEFI 構成パッケージを使用して SEMM に Surface デバイスを登録するには、次の手順を実行します。

1. SEMM に登録する Surface デバイスで、Surface UEFI 構成パッケージ .msi ファイルを実行します。 これにより、デバイスのファームウェアに Surface UEFI 構成ファイルがプロビジョニングされます。
2. 使用許諾契約書 **(EULA)** に同意するには、[使用許諾契約書に同意します] チェック ボックスをオンにし****、[インストール] をクリックしてインストール プロセスを開始します。
3. [ **完了]** をクリックして Surface UEFI 構成パッケージのインストールを完了し、実行するように求めるメッセージが表示されたら Surface デバイスを再起動します。
4. Surface UEFI は構成ファイルを読み込み、SEMM がデバイスで有効になっていないと判断します。 Surface UEFI は、次のように SEMM 登録プロセスを開始します。
   * Surface UEFI は、SEMM 構成ファイルに SEMM 証明書が含まれているか確認します。
   * 図 8 に示すように、Surface UEFI は、SEMM での Surface デバイスの登録を確認するために、証明書の拇印の最後の 2 文字を入力するように求めるメッセージを表示します。

      ![SEMM 登録には、証明書の拇印の最後の 2 文字が必要です](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *図 8. SEMM への登録には、証明書の拇印の最後の 2 文字が必要です。*

   * Surface UEFI は SEMM 証明書をファームウェアに格納し、Surface UEFI 構成ファイルで指定された構成設定を適用します。
   
5. Surface デバイスは SEMM に登録され、Windows で起動します。

**SEMM**に Surface デバイスが正常に登録されたことを確認するには、プログラムと機能 の**Microsoft Surface 構成**パッケージ (図 9 を参照)、またはイベント ビューアーの [アプリケーションとサービス ログ] (図**** 10 を参照) にある Microsoft **Surface UEFI**構成ログに格納されているイベントを探します。

![SEMM での Surface デバイスの登録を確認プログラムと機能](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*図 9. SEMM での Surface デバイスの登録を確認プログラムと機能*

![イベント ビューアーで SEMM に Surface デバイスの登録を確認する](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*図 10. イベント ビューアーで SEMM で Surface デバイスの登録を確認する*

デバイスが Surface UEFI の SEMM に登録されているのを確認することもできます。デバイスが登録されている間、Surface UEFI には [ **エンタープライズ** 管理] ページが表示されます (図 11 を参照)。

![Surface UEFI Enterprise の管理ページ](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*図 11. Surface UEFI Enterprise の管理ページ*


##  <a name="configure-surface-uefi-settings-with-semm"></a>SEMM を使用して Surface UEFI の設定を構成する

デバイスを SEMM に登録した後、同じ SEMM 証明書で署名された Surface UEFI 構成パッケージを実行して、新しい Surface UEFI 設定を適用できます。 これらの設定は、次回デバイスが起動すると自動的に適用され、ユーザーによる操作は行われます。 Microsoft Endpoint Configuration Manager のようなアプリケーション展開ソリューションを使用して、Surface UEFI 構成パッケージを Surface デバイスに展開し、Surface UEFI の設定を変更または管理できます。

Configuration Manager で Windows インストーラー (.msi) ファイルを展開する方法の詳細については [、「Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959)を使ったアプリケーションの展開と管理」を参照してください。

パスワードを使って Surface UEFI をセキュリティで保護した場合、パスワードを使わずに Surface UEFI を起動しようとするユーザーには **、PC**情報****、**バージョン**情報、**エンタープライズ**管理、および終了ページだけが表示されます。

パスワードを使って Surface UEFI をセキュリティで保護していない場合、またはユーザーがパスワードを正しく入力した場合、SEMM で構成されている設定は淡色表示 (利用不可) され、図 12 に示すように、組織で一部の設定が管理されているテキストがページの上部に表示されます。

![SURFACE UEFI で SEMM によって管理される設定が無効になっている](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*図 12. SEMM によって管理される設定は Surface UEFI で無効になります。*
