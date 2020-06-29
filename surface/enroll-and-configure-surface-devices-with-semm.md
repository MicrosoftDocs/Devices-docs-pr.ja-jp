---
title: SEMM (Surface) を使って Surface デバイスを登録および構成する
description: Surface uefi の設定を制御する Surface UEFI 構成パッケージを作成する方法、および SEMM に Surface デバイスを登録する方法について説明します。
keywords: surface enterprise 管理
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 183eceee47eba8b8d1e794e9e7d3efffa7a9b2e0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835950"
---
# SEMM による Surface デバイスの登録と構成

Microsoft Surface Enterprise Management Mode (SEMM) を使用すると、Surface デバイス上の Surface UEFI の設定を安全に構成し、組織内の Surface デバイスでそれらの設定を管理できます。 Surface デバイスが SEMM によって管理される場合、そのデバイスは*登録*されていると見なされます (アクティブ化と呼ばれることもあります)。 この記事では、surface UEFI の設定のみを制御する Surface UEFI 構成パッケージを作成する方法について説明しますが、SEMM には Surface デバイスも登録します。

SEMM の大まかな概要については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」をご覧ください。

Surface pro 7 のクラウドからファームウェアを管理するための合理化された方法です。 Surface Pro X と Surface のノート Pc 3 はパブリックプレビューで利用できるようになりました。 詳細については、「 [SURFACE UEFI の設定の Intune 管理](surface-manage-dfci-guide.md)」を参照してください。

> [!NOTE]
> SEMM は、UEFI Manager のみを通じて Surface Pro X でサポートされています。 詳細については、「[展開、管理、およびサービス Surface Pro X](surface-pro-arm-app-management.md)」を参照してください。

#### Microsoft Surface UEFI コンフィギュレーターをダウンロードしてインストールする
SEMM パッケージの作成に使用するツールは、Microsoft Surface UEFI コンフィギュレーターです。 Microsoft Surface UEFI コンフィギュレーターは、Microsoft ダウンロードセンターの [ [Surface Tools](https://www.microsoft.com/download/details.aspx?id=46703) ] ページからダウンロードできます。
Microsoft Surface UEFI Configurator Windows Installer (.msi) ファイルを実行して、ツールのインストールを開始します。 インストーラーが完了したら、[スタート] メニューの [すべてのアプリ] セクションで Microsoft Surface UEFI コンフィギュレーターを見つけます。

>[!NOTE]
>Microsoft Surface UEFI コンフィギュレーターは、Windows 10 でのみサポートされています。

## Surface UEFI 構成パッケージを作成する

Surface UEFI 構成パッケージは、SEMM と共に管理される Surface デバイスと SEMM での surface device の役割の両方に、Surface UEFI の設定の新しい構成を適用する役割を果たします。 構成パッケージを作成するには、各 Surface デバイスで UEFI 設定の構成をセキュリティで保護するために、SEMM と共に使用する署名証明書が必要です。 SEMM 証明書の要件の詳細については、「 [Microsoft Surface Enterprise Management モード](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)」を参照してください。

Surface UEFI 構成パッケージを作成するには、次の手順を実行します。

1. [スタート] メニューから Microsoft Surface UEFI コンフィギュレーターを開きます。
2. **[開始]** をクリックします。
3. 図1に示すように、[**構成パッケージ**] をクリックします。

   ![SEMM 登録用のパッケージを作成する](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *図 1.  構成パッケージを選択して SEMM の登録と構成のパッケージを作成する*

4. [**証明書の保護**] をクリックして、図2に示すように、エクスポートされた証明書ファイルを秘密キー (.pfx) で追加します。 証明書ファイルの場所を参照し、ファイルを選択して、[ **OK]** をクリックします。

   ![SEM certificate and Surface UEFI パスワードを構成パッケージに追加する](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *図 2.  SEMM 証明書と Surface UEFI パスワードを Surface UEFI 構成パッケージに追加する*

5. 証明書のパスワードを確認するように求められたら、証明書ファイルのパスワードを入力して確認し、[ **OK]** をクリックします。
6. [**パスワードによる保護**] をクリックして、Surface UEFI にパスワードを追加します。 このパスワードは、UEFI を起動するたびに必要になります。 このパスワードが入力されていない場合は、 **PC 情報**、**バージョン**情報、**エンタープライズ管理**、**終了**ページのみが表示されます。 この手順は省略可能です。
7. メッセージが表示されたら、Surface UEFI 用に選択したパスワードを入力して確定し、[ **OK]** をクリックします。 既存の Surface UEFI パスワードをクリアする場合は、パスワードフィールドを空白のままにします。
8. Surface UEFI パッケージを特定のデバイスに適用しない場合は、[**ターゲットにするサーフェスの種類を選択**] ページで、対応する surface Book または surface Pro 4 の画像の下にあるスライダーをクリックして、その位置が**オフ**になるようにします。 (図3に示すように)。
   > [!NOTE] 
   > 既定では [なし] が選択されているため、デバイスを選択する必要があります。

   ![パッケージの互換性を維持するためのデバイスの選択](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *図 3.  パッケージの互換性を維持するためのデバイスの選択*

9. **[次へ]** をクリックします。
10. 管理された Surface デバイスのコンポーネントを非アクティブ化する場合は、[**アクティブ化または非**アクティブ化するコンポーネントの選択] ページで、非アクティブ化するデバイスまたはデバイスのグループの横にあるスライダーをクリックして、スライダーが [**オフ**] の位置になるようにします。 (図4に示されています)。各デバイスの既定の構成が**オンに**なっている。 すべてのスライダーを既定の位置に戻したい場合は、[**リセット**] ボタンをクリックします。

    ![Surface コンポーネントを無効または有効にする](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *図 4:  サーフェスコンポーネントを個別に無効または有効にする*

11. **[次へ]** をクリックします。
12. Surface UEFI または Surface UEFI ページの表示で詳細オプションを有効または無効にするには、[**デバイスの詳細設定を選択**します] ページで、目的の設定の横にあるスライダーをクリックして、そのオプションを [**オン**] または [**オフ**] に設定します (図5を参照)。 Uefi の [ **Front Page** ] セクションで、[**セキュリティ**、**デバイス**、**ブート**] のスライダーを使用して、Surface UEFI で起動したユーザーが利用できるページを制御することができます。 Surface UEFI の設定の詳細については、「 [SURFACE uefi の設定を管理](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)する」を参照してください。パッケージを生成および保存するオプションの選択が完了したら、[**ビルド**] をクリックします。

    ![高度な Surface UEFI 設定と Surface UEFI ページの制御](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *図 5:  SEMM で詳細 Surface UEFI 設定と Surface UEFI ページを制御する*

13. [名前を**付けて保存**] ダイアログボックスで、Surface UEFI 構成パッケージの名前を指定し、ファイルを保存する場所を参照して、[**保存**] をクリックします。
14. パッケージが作成されて保存されると、**成功**したページが表示されます。

>[!NOTE]
>図6に示すように、このページに表示される証明書の拇印文字を記録します。 SEMM で新しい Surface デバイスの登録を確認するには、次の文字が必要です。 [**終了**] をクリックしてパッケージの作成を完了し、MICROSOFT Surface UEFI コンフィギュレーターを終了します。

![証明書の拇印文字の表示](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*図 6.  証明書の拇印の最後の2文字が、[成功] ページに表示されます。*

Surface UEFI 構成パッケージを作成したので、Surface デバイスを登録または構成することができます。

>[!NOTE]
>Surface UEFI 構成パッケージを作成すると、構成パッケージの設定とオプションの詳細を含むログファイルがデスクトップ上に作成されます。

## SEMM に Surface デバイスを登録する
Surface UEFI 構成パッケージが実行されると、SEMM 証明書と Surface UEFI 構成ファイルが Surface デバイスのファームウェアストレージにステージングされます。 Surface デバイスが再起動すると、Surface UEFI によってこれらのファイルが処理され、Surface UEFI 構成の適用プロセスまたは SEMM での Surface デバイスの登録が開始されます (図7参照)。

![Surface UEFI または登録を構成するための SEMM プロセス](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*図 7. Surface UEFI または Surface デバイスの登録を構成するための SEMM プロセス*

SEMM で Surface デバイスを登録するプロセスを開始する前に、証明書の拇印の最後の2文字が入力されていることを確認します。 これらの文字は、デバイスの登録を確認するために必要です (図6を参照してください)。

Surface UEFI 構成パッケージを使用して Surface デバイスを SEMM に登録するには、次の手順を実行します。

1. SEMM に登録する Surface デバイスで Surface UEFI 構成パッケージの .msi ファイルを実行します。 これにより、デバイスのファームウェアで Surface UEFI 構成ファイルがプロビジョニングされます。
2. [使用許諾契約書の**条項に同意**します] チェックボックスをオンにして、エンドユーザーライセンス契約 (EULA) に同意し、[**インストール**] をクリックしてインストールプロセスを開始します。
3. [**完了**] をクリックして surface UEFI 構成パッケージのインストールを完了し、画面の指示に従って surface デバイスを再起動します。
4. Surface UEFI は構成ファイルを読み込んで、デバイスで SEMM が有効になっていないことを確認します。 Surface UEFI は、次のように SEMM 登録プロセスを開始します。
   * Surface UEFI は、SEMM 構成ファイルに SEMM 証明書が含まれていることを確認します。
   * Surface UEFI では、図8に示すように、SEMM で Surface デバイスの登録を確認するために、証明書拇印の最後の2文字を入力するように求められます。

      ![SEMM 登録には、証明書の拇印の最後の2文字が必要](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *図 8. SEMM での登録には、証明書の拇印の最後の2文字が必要*

   * Surface UEFI はファームウェアに SEMM 証明書を格納し、Surface UEFI 構成ファイルで指定されている構成設定を適用します。
   
5. Surface デバイスが SEMM に登録され、Windows で起動します。

(図9に示すように)**プログラムと機能**(図9に示す) では、[**アプリケーションとサービスログ**] の下に表示されている、 **microsoft surface** **構成パッケージ**を検索することで、surface デバイスが semm に正常に登録されたことを確認することができます (図10を参照)。

![[プログラムと機能] で SEMM で Surface デバイスの登録を確認する](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*図 9. [プログラムと機能] で SEMM で Surface デバイスの登録を確認する*

![イベントビューアーの SEMM で Surface デバイスの登録を確認する](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*図 10. イベントビューアーの SEMM で Surface デバイスの登録を確認する*

また、デバイスが Surface UEFI の SEMM に登録されていることを確認することもできます。デバイスが登録されている間、Surface UEFI には、図11に示すように、[**エンタープライズ管理**] ページが含まれます。

![Surface UEFI Enterprise 管理ページ](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*図 11. Surface UEFI Enterprise 管理ページ*


## SEMM を使用して Surface UEFI の設定を構成する

デバイスが SEMM に登録されたら、同じ SEMM 証明書で署名された Surface UEFI 構成パッケージを実行して、新しい Surface UEFI 設定を適用できます。 これらの設定は、次回デバイスを起動したときに、ユーザーの操作なしで自動的に適用されます。 Microsoft Endpoint Configuration Manager などのアプリケーション展開ソリューションを使用して、surface uefi 構成パッケージを surface デバイスに展開して、Surface UEFI の設定を変更または管理することができます。

Configuration Manager を使用して Windows Installer (.msi) ファイルを展開する方法の詳細については、「 [Microsoft Endpoint Configuration manager を使用してアプリケーションを展開および管理](https://technet.microsoft.com/library/mt627959)する」を参照してください。

セキュリティで保護された Surface UEFI をパスワードで使用している場合、Surface UEFI を起動しようとしているパスワードを持たないユーザーには、 **PC 情報**、**バージョン**情報、**エンタープライズ管理**、**終了**ページのみが表示されます。

パスワードを使用して Surface UEFI をセキュリティで保護していない場合、またはユーザーがパスワードを正しく入力していない場合は、SEMM で構成されている設定は淡色 (使用不可) になり、組織で管理されている設定のテキストは、図12のように、ページ上部に表示されます。

![Surface UEFI での SEMM によって管理されている設定](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*図 12. SEMM によって管理される設定は Surface UEFI で無効になります*
