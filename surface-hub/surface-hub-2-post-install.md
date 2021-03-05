---
title: Surface Hub 2 で Windows 10 Pro または Enterprise を構成する
description: この記事には、パーソナライズされた大画面タッチとペン コンピューターを使用する場合に最適なエクスペリエンスを確保するための推奨事項が含まれています。
keywords: Surface Hub、Windows 10、デスクトップ、インストール、構成
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.collection: M365-modern-desktop
ms.topic: article
ms.date: 12/08/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: 076d29462ffb949492291e120bcdad538f4287ec
ms.sourcegitcommit: e859374f90d640a5cd4be1c8dcc823bcd537ebdc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "11393591"
---
# <a name="configure-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Surface Hub 2 で Windows 10 Pro または Enterprise を構成する

Windows 10 Pro または Enterprise への移行のインストール プロセスが完了したら、次の手順を実行して、Surface Hub 2 でアプリと設定を構成できます。 これらの手順は、このパーソナライズされた大画面タッチとペン コンピューターを使用する場合に最適なエクスペリエンスを確保するためにお勧めします。

これらの手順を実行する場合は、有線またはワイヤレスのキーボードとマウスを使用すると便利です。

## <a name="configure-system-settings"></a>システム設定の構成

1. デバイスに対するローカル管理者特権を持つアカウントでサインインします。  

    - Azure ADに参加しているデバイスでは、Azure ADを実行するユーザーがローカル管理者グループに自動的に追加されます。 Azure AD管理者と Azure ADデバイス管理者も <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> ローカル管理者です </a> 。 
    
    - コマンド プロンプトに **「net localgroup administrators」** と入力して、ローカル管理者権限を持つアカウントを一覧表示できます。
    
2. ユーザー名 **-SHub-Desktop など、表示名を使用してデバイスの名前を変更します**。

3. [スタート**設定**  >  **アカウント**  >  **]**  >  **[設定の同期] を選択し**、[**同期設定] をオフ**にします。 

    - ここで使用する設定は、最高の大画面タッチ エクスペリエンスを有効にすることを目的とするため、他のデバイスを同期したくない場合があります。
    
4. デバイスを再起動します。

## <a name="enable-the-touch-keyboard-and-touchpad"></a>タッチ キーボードとタッチパッドを有効にする

1. [**設定の開始**デバイスの入力] を選択し、[タブレット モードではないときにタッチ キーボードを表示する] をオンにし、キーボード  >  ****  >  ****  >  ******が接続されていない場合はオン**にします。

2. タスク バーを長押しまたは右クリックし、[タッチ **キーボード** ボタンの表示] と [タッチパッド ボタンの表示] **を選択します**。 

    - タッチ キーボードはユーザーの直接入力に役立ち、仮想タッチパッドは正確な選択、画面のヒントのホバー、または右クリックのタップとホールドの代わりに役立ちます。 
    
    - 次の例をご覧ください。

      ![タッチ設定](images/touch.png)

3. タッチ キーボードを QWERTY とフローティングに構成します。

    1. タスク バーの **[キーボード** ] アイコンを選択して、タッチ キーボードを表示します。
    
    1. タッチ キーボードで、左上隅にあるキーボード アイコンを選択してキーボード設定を開きます。
    
    1. 上の行の次から最後のキーボードの種類を選択して QWERTY を有効にし、2 行目の最後のオプションを選択して浮動を有効にします。これは、この大きな画面で非常に役立ちます。 次の例を参照してください。

       ![キーボード設定](images/kbd.png)
 
4. ソフト キーボードの設定を構成します。

    1. タッチ キーボードの **[設定** ] アイコンを選択するか、入力設定を検索して **開きます**。
    
       ![ソフト キーボードの設定](images/sh2-softkeyboard.png)

    1. [スペル チェック]、[タイピング]、および [タッチ キーボード] の下のすべてのオプションを有効にします。


次の使用例は、オプションの移動と選択に役立つトラックパッドを示しています。 画面上のキーボードは、Microsoft Store の検索に使用されています。

![トラックパッドの使用](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a>キーボードBluetoothマウスを構成する (オプション)

デバイスをプライマリ Windows デバイスとして使用している場合や、入力や精度の向上のために頻繁に使用する場合は、キーボードとマウスを接続します。

Surface Hub デバイスが PC に近い場合は、境界線のないマウスを使用して Surface Hub と PC の間をシームレスに <a href="https://aka.ms/mm" target="_blank"> </a> 移動できます。 詳細については <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> 、「Microsoft download from the Garage: Mouse without Borders」を参照してください。 </a>

## <a name="example-of-taskbar-layout"></a>タスク バーのレイアウトの例

Windows 10 Professional または Enterprise 用の Surface Hub 2 をセットアップ/構成する以下の手順を完了した後、最も使用されているアプリケーションをタスク バーにピン留めして、各アプリケーションをワンタッチで簡単に起動することをお勧めします。 タスク バーの外観の例を次に示します。

 ![タスク バーのレイアウト](images/taskblyt.png)
### <a name="update-installed-apps"></a>インストールされているアプリを更新する

インストールされているストア アプリを更新するには、次の方法を実行します。

1. Microsoft Store アプリを開き、右上隅にある **[その** 他の省略記号を表示する] を選択します。
2. [ダウンロード **と更新] を選択します。**
3. [更新 **プログラムの取得] を選択します。**

### <a name="scan-for-and-install-all-windows-updates"></a>すべての Windows 更新プログラムをスキャンしてインストールする
Windows 10 Professional または Windows 10 Enterprise に移行した後、サービスと機能更新プログラムをインストールできる場合があります。 

- [設定の**更新**  >  **プログラム&セキュリティ >]** に移動し、[更新プログラムの確認 **] を選択します**。
- 更新プログラムがある場合は、インストールして再起動し、次の通知が表示されるまでプロセスを繰り返します。

> [!div class="mx-imgBorder"]
> ![Windows Update 'You'up to date' 通知](images/wustatus.png)


## <a name="onedrive-for-business"></a>OneDrive for Business

OneDrive for Business を使用すると、すべての作業デバイス間でツール、ログ、その他のファイル <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> </a> を簡単に共有できます。

- OneDrive を使用すると、ノート PC、Surface Hub Desktop、Intune で管理されるモバイル デバイス間で作業ファイルを共有できます。 ファイルは任意のデバイスで編集できます。すべてのネットワーク接続デバイスが変更に合って更新されます。

- Surface Hub SSD (128 GB) のサイズを考慮して、Surface Hub Desktop デバイスで OneDrive を構成する場合は、ファイルをオンラインに保ち、使用するファイルをダウンロードする既定の構成を確認してください。

必要な場合にのみファイルをダウンロードする OneDrive を構成するには、[Files **On-Demand]** 設定を [スペースの節約] に設定し、使用するファイルを **ダウンロードします**。 詳細については、「Windows でファイルのオンデマンド状態をクエリおよび設定 <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> する」を参照してください </a> 。

![OneDrive の設定](images/onedrive.png)

> [!NOTE]
> また、これらの手順を繰り返して個人用 OneDrive を構成することもできますが、ドライブ領域を節約し、必要に応じてファイルのみをダウンロードしてください。

## <a name="sharepoint-and-teams"></a>SharePoint と Teams

SharePoint および Teams チャネル ファイルは、OneDrive 同期エンジンを使用して、ラップトップや Surface Hubs などのデスクトップ デバイスにローカルで同期することもできます。

OneDrive 同期アプリを使用して内部企業ファイルをローカル ドライブに同期するには、次の手順を実行します。

1. SharePoint サイトに移動し、ローカル デバイスから表示または編集するファイルのトップ レベルのドキュメント ディレクトリに移動します。

2. SharePoint リボン **の上部** にある [同期] ボタンを選択します。

3. ポップアップで **[開く** ] を選択します このサイトでは **、Microsoft OneDrive を開きます**。

4. タスク バーの右下にある OneDrive アイコンを選択して、SharePoint ファイルがローカル ドライブと同期しているのを確認します。

5. ファイルをオンラインに保ち、ファイルを使用する場合にのみダウンロードする構成が設定されているのを確認します。

    1. エクスプローラーを開きます。
    
    2. SharePoint 名に移動して右クリックします。たとえば **、Contoso \ \<SharePoint Document Folder Name\> . **
    
    3. [ **空き領域を解放する] を選択します**。
    
    4. [状態] 列には、ファイルとフォルダーの状態が表示されます。 詳細については <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> 、「SharePoint ファイルを OneDrive 同期クライアントと同期する」を参照してください </a> 。
    
6. Teams チャネル ファイルは SharePoint サイトに保存され、バージョン履歴やローカル デスクトップ デバイスとの同期など、すべての同じ SharePoint ドキュメント機能を使用します。 Teams チャネル ファイルを同期するには、次の手順を実行します。

    1. 目的の Teams チャネルに移動し、上部の **[ファイル** ] タブを選択します。 次に、[同期]**を選択します**。ファイルは同期を開始し、デスクトップ \ Contoso \ の**エクスプローラーに \<name of the Teams Channel\> 表示されます**。
    
    2. SharePoint サイトの同期に使用したのと同じ手順を使用して、クラウドにファイルを保持し、それらを使用する場合にのみダウンロードします。Teams チャネル名のエクスプローラーをタップして長押しまたは右クリックし、[**** 空き領域] を選択します。

## <a name="surface-hub-pen-settings"></a>Surface Hub ペンの設定

**Surface Hub ペンBluetoothペアリングする**

ペンをペアリングしてペンのファームウェアを最新の状態に保ち、ペンショートカットを設定し、Bluetooth デバイス設定ページまたは Surface アプリでバッテリー充電情報を取得します。

1. [スタート**設定デバイス**  >  **]**  >  **を選択します**。

2. [デバイス **または他Bluetooth追加] を選択します**。

3. [Bluetooth] **を選択します**。

4. ペンの尾ボタンを外して、バッテリー接続を切断します。

5. キャップをオンに戻し、ペアリング LED が点滅するまでキャップを長押しします。

6. Surface Hub の設定で **Bluetooth[Surface Hub 2 Pen] を選択します**。

7. ペアリング操作を完了します。 

8. ペアリングが成功しない場合は、もう一度ペンのペアリングを試みます。 それでも問題が発生しない場合は、ホワイトボード アプリケーションでペンが動作するを確認して、バッテリーが充電されるのをテストできます。 ない場合は、バッテリーを交換し、もう一度ペンのペアリングを試みます。 必要に応じて、デバイスを再起動してから、もう一度やり直してください。

**ペンのショートカットを設定する** Surface Hub ペンには、"tail click" とも呼ばれるショートカット ボタンがあります。 ショートカットを構成するには、前述のように、最初にペンをペアリングする必要があります。

1. [ペン] を検索し、[ **ペン] を選択& Windows Ink の設定を選択します**。

2. ページの下部付近で、[ペン ショートカット] を選択してダイアログ ボックスを開きます。次に示します。

   ![ペンのショートカット](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a>カメラの構成

カメラは、デバイスの上部またはどちら側にマウントすることもできます。 カートではなくデスクトップ スタンドでハブを使用している場合、またはハブに近接している場合は、カメラの角度を最適化する位置にカメラをマウントします。 カメラは自動回転しないので、カメラを手動で回転するには 2mm の 16 進キーが必要です。 

カメラをサイド マウントし、カメラを手動で回転する方法の詳細については、「Surface Hub 2S カメラレンズの向き」 <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> を参照してください </a> 。

## <a name="windows-hello-configuration"></a>Windows Hello の構成

Windows 10 Enterprise を実行する Surface Hub 2S では、Win32 デスクトップ アプリケーションと生体認証 Windows Hello オプションの完全なスイートを使用できます。 Surface Hub 2 指紋リーダー アクセサリは、デバイス上の任意の USB-C ポートに接続できます。 

Surface Hub 2 指紋リーダーを注文するか、技術的な仕様を表示するには、「(surface-hub-2-essential-add-ons.md" target="_blank">Essential アドオン for Windows 10 Pro および Enterprise on Surface Hub 2」を参照してください。 </a> 

指紋リーダーを挿入した後、[スタート**** 設定] [アカウント] サインイン  >  ****  >  ****  >  **オプション**  >  **[Windows Hello Fingerprint]** を選択して指紋を登録します。

顔認識には Windows Hello 認定デバイスを使用します。 Surface Hub 2S カメラでは、Windows Hello の顔認識はサポートされていません。

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a>タスク バーの [画面のロック] ショートカット アイコンを有効にする

Windows-L キーボード ショートカットのようなワンタッチ画面ロックを有効にするアイコンをタスク バーに追加するには、次の操作を行います。 

1.  デスクトップを長押しまたは右クリックし、[新しい**** ショートカットの参照  >  ****  >  **デスクトップ OK**  >  **次**へ]  >  **を**  >  **選択します**。

1.  [自分の PC をロックする] などのショートカットの **名前を指定**し、[完了] を **選択します**。

1.  デスクトップ上で新しく作成したショートカットを右クリックまたはタップして長押しし、[プロパティ] を **選択します**。 [ショートカット **] タブ**で、[ターゲット] フィールドに次の情報を**入力します****Rundll32.exe User32.dll、LockWorkStation**

1.  [アイコンの **変更] ボタンを** 選択 ** し、C:\Windows\System32\imageres.dll** を参照して、使用するアイコンを選択します。 

    次に例を示します。

    ![アイコンを選択する](images/lock.png)
    
1.  **[OK] を**選択してショートカットを保存します。

1.  ショートカットを右クリックまたはタップして長押しし、[タスク バーに **ピン留めする] を選択します**。

1. ロック ショートカットをタスク バーにピン留めした後、デスクトップから削除できます。

## <a name="applications"></a>アプリケーション


### <a name="microsoft-whiteboard"></a>Microsoft Whiteboard

Microsoft ホワイトボードをインストールするには、次の手順を実行します。

 - タスク バーの **右下にある [Windows Ink Workspace]** アイコンを選択し、ホワイトボードを **ダウンロードします**。
 
   ![インク ワークスペース](images/ink.png) 

または、Microsoft ストアからホワイトボードをインストールできます。

1. Microsoft Store アプリを開き、ホワイトボード **を検索します**。

2. [サインイン **してデバイス間** で使用する] を選択して[いいえ] を選択します。

3. ホワイトボードをタスク バーにピン留めします。

### <a name="surface-app"></a>Surface アプリ

1. Microsoft Store で Surface を **検索します**。

2. [使用可能な **フィルター] を [** すべてのデバイス] **に設定します**。

3. Surface アプリ **をインストール** します。 これは、最初に表示されるアプリである必要があります。 アプリをインストールするには、MSA をストアに関連付ける必要がある場合があります。

4. Surface アプリ **をタスク バー** にピン留めします。

### <a name="snip--sketch"></a>切り取り & スケッチ

1. **Snip &スケッチ アプリを開**き、タスク バーにピン留めします。

2. 右上隅にある省略記号を選択し、[設定] を **選択します**。

3. [ **設定]** で、[クリップボードに **自動コピー]**、[切り取 **りを保存**] 、および [複数のウィンドウ **]** をオンにします (オプション)。

### <a name="microsoft-office"></a>Microsoft Office

1. [ポータル] <a href="https://portal.office.com/account#installs" target="_blank"> Office開 </a> き、目的のアプリケーションをインストールします。

2. 必要なアプリケーションOfficeタスク バーにピン留めします。

3. Outlook がインストールされている場合は、最後の 2 週間のキャッシュのみを保存する Outlook OST を設定してください。 これにより、ディスク使用量とセットアップ時間が大幅に短縮されます。

    - [**ファイル アカウント**  >  **の設定] を選択**し、アカウントを選択します。
    
    - [ **変更]** を選択し **、[Exchange** キャッシュ モードを使用する] のスライダーを 14 日間に設定します。

### <a name="microsoft-teams"></a>Microsoft Teams

1. Microsoft Teams を <a href="https://teams.microsoft.com/downloads" target="_blank"> ダウンロードしてインストールします </a> 。

2. 自動起動アプリケーションに設定を構成します (オプション)。

3. タスク バーに Teams をピン留めします。

4. デバイス上の Teams 通知を減らすことを検討して、注意をそらさないようにします (オプション)。

   ![Teams 通知](images/teams.png)

### <a name="connect-app"></a>アプリの接続

> [!IMPORTANT]
> Windows 10 バージョン 2004 以降では、Miracast を使用したワイヤレス プロジェクション用の Connect アプリは既定ではインストールされていませんが、オプションの機能として使用できます。 Windows バージョン 2004 以降をインストール (または更新) した場合は、設定の [この PC への投影] 画面に次の情報が表示される場合があります。

![この PC へのプロジェクト](images/sh2-project.png) 


1. [この PC への投影] 設定ページからアプリをインストールするには、[**** オプション機能] [機能の追加] を選択し、ワイヤレスディスプレイ アプリ  >  ******をインストール**します。

2. [ **一部の Windows デバイスと Android デバイスでは、この PC**に投影できます。[OK] と表示されている場合は、次のオプションを選択します。

    - **デバイスが企業ネットワーク** 上にない場合は、どこでも使用できます。
    - それ以外の場合は、[ **セキュリティで保護されたネットワーク上のすべての場所で利用可能] を選択します**。
    
3. [この **PC にプロジェクトを求める] で、[** 初回 **のみ] を選択します**。

4. [ペアリング **に PIN を要求する] で、[** しない] を **選択します**。

5. 次に、アプリを起動し、タスク バーにピン留めするには、[接続] を **検索します**。

6. アプリを開きます。 アプリが開いている間に、タスク バーの [アプリの接続] アイコンを右クリックし、[タスク バーにピン留め **する] を選択します**。

7. 次に、Connect アプリを閉じます。 **アプリを少なくとも 1** 回実行しない限り、この PC へのプロジェクトは機能しない場合があります。

企業ネットワークに含めない場合の推奨構成:

![自宅の設定](images/project1.png)

企業ネットワークでの推奨される構成:

![作業中の設定](images/project2.png)

### <a name="your-phone"></a>スマホ同期

電話 **アプリは** 、Windows 10 に既定でインストールされます。 存在しない場合は、Windows ストアからインストールできます。

アプリのセットアップの詳細については、「Windows 10 で電話をセットアップし、PC と電話の間でデータ <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> を同期する方法」を参照してください </a> 。 また、「Windows 10 の電話アプリで一般的な問題を解決する方法 <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> 」も参照してください </a> 。

###  <a name="fancy-zones"></a>ファンシー ゾーン


**ファンシー** ゾーンは、GitHub の <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys と呼ばれるツール </a> のコレクションの一部です。 Surface Hub 2 の画面の不動産を利用するには、ディスプレイ ("zone") で固定レイアウトを定義し、各領域で実行するアプリを選択できます。 


[PowerToys Wiki には、各](https://github.com/microsoft/PowerToys/wiki)ツールの使い方とカスタマイズ方法 (ファンシーゾーンを含む)[の手順があります](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview)。 PowerToys をインストールした後で、カスタム レイアウトを選択または作成し、シフト キーを押したまま、キーボード キーをドラッグまたは使用して実行中のアプリを特定の領域に移動できます。 この操作Bluetooth USB キーボードとマウスを使用すると役立ちます。また、オンスクリーン タッチ キーボードとタッチパッドを使用することもできます。

**Power Toys のヒント**
- GitHub で PowerToys リリースの更新プログラムの電子メール通知を受信するには、ページの上部にある [サインアップ] ボタンをクリック [します](https://github.com/microsoft/PowerToys/releases)。
- PowerToys をインストールすると、PowerToys の設定を構成して Windows 通知を受信したり、最新の更新プログラムをダウンロードしてインストールしたりできます。更新プログラムを自動的に **オン** にダウンロードします。
- PowerToys 設定に移動するには、タスク バーでアップ カラット **の実行中** のアプリを選択し、メニューが表示されるまで PowerToys アイコンを右クリックまたは押したままにします。 [設定] を選択します。
- PowerToys 設定ページの下部で、[更新プログラムを自動的にダウンロードする **] をオン** にします。
- 更新プログラムがリリースされると、更新プログラムをインストールする場合のオプションを示す Windows 通知が表示されます。


### <a name="edge-chromium-browser"></a>エッジ クロム ブラウザー

新しいエッジ クロム ブラウザー <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> をダウンロードしてインストールします </a> 。


### <a name="surface-hub-hardware-diagnostic-tool"></a>Surface Hub ハードウェア診断ツール

<a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank">Microsoft Store から無料で利用できる Surface Hub </a> ハードウェア診断ツール。 このツールは、Surface Hub が最高のパフォーマンスを提供するように設計されています。 ファームウェアが最新で正しく構成されたかどうかを判断するテストが含まれている。 対話型テストを使用すると、重要な機能が期待通り動作しているのを確認できます。 問題が発生した場合は、結果を保存して Surface Hub のサポート チームと共有できます。 リンクをクリックして Microsoft Store からインストールし、アプリケーションをタスク バーにピン留めします。

## <a name="additional-settings"></a>追加設定

### <a name="pen-tail-select-to-launch-whiteboard"></a>ホワイトボードを起動するペンの尾の選択

1. [ペン] **を検索し** 、[ **ペン] & Windows インクの設定] を選択します**。

2. ページの下部付近の [ペン のショートカット] **で** 、[一度選択] を **[Microsoft** **ホワイトボード] に設定します**。 

### <a name="power-management"></a>電源管理

Windows 10 Pro または Enterprise on Surface Hub 2 を使用して最高のエクスペリエンスを得るには、いくつかの電源設定があります。 これには、画面と PC のタイムアウトと、組み込みの人間のプレゼンス検出 (Doppler)、スクリーン セーバー、パスワード保護、およびラップトップ/デスクトップ ユーザーを対象としたグループ ポリシーの電源設定を適切に通過する方法が含まれます。

Windows 10 Pro または Enterprise on Surface Hub 2 では、タッチ、マウス、キーボード操作、および組み込みの人間の占有検出 (Doppler) によって画面がスリープ状態に保たれる。 人間の占有率の検出は既定で有効になっていますが、必要に応じて、初期移行の一環として Surface UEFI コンフィギュレーター ツールのデバイス オプションを切り当て、または後の UEFI 構成パッケージを構築して適用することで、UEFI で無効にすることができます。 

**電源管理: 画面と PC のスリープ設定**

1. [スタート**設定**  >  **]**  >  **[システムの**  >  **電源&スリープ] を選択します**。

2. [電源モード] スライダーを [最適なパフォーマンス **] に設定します**。

3. 画面とスリープの値を好みに応じて構成し、動きが検出されるとデバイスを目を覚ますドップラープレゼンス検出も管理します。 したがって、ベスト プラクティスとして、[画面] を **[2**時間後にオフにする] に設定し、PC を**4**時間後にオフに設定してください。

**電源管理: スクリーン セーバー**

1. ロック画面を **検索し、[** 画面の **ロック設定] を開きます**。

2. [画面 **のタイムアウト設定] と** [ **スクリーン セーバーの設定] を基本** 設定に構成します。 推奨される既定値は次のとおりです。

   - (なし) または選択したスクリーン セーバーへのスクリーン セーバー。
   - 待機時間を 15 分に設定します。
   - 再開時に、ログオン画面を表示します。


**電源管理: グループ ポリシー**

次の手順を実行する前に、IT 部門に確認して承認を得て、Surface Hub 2S デバイスをグローバル電源管理ポリシーから除外します。 一部の電源管理設定では、プレゼンス検出機能を無効にできます。

1. ソフトウェア センター **を検索して** 開きます。

2. [オプション **] を選択します**。

3. [電源管理 **] を展開し**  、[自分の IT 部門からこのコンピューターに電源 **設定を適用しない] を選択します**。

   ![ソフトウェア設定](images/soft-cntr.png)

### <a name="storage-sense"></a>ストレージ センサー

Surface Hub 2 にはローカル ストレージ用の 128 GB SSD が搭載されています。  記憶域の検出を構成するには、次の手順を行います。

1.  [システム設定 **] の**下にある記憶域の設定 **を検索します**。

2.  [設定 **] で**、[ **ストレージセンスを有効** にする] を選択して、[記憶域の設定] **ページを** 開きます。

3.  [記憶域の検出] を **[オン] に切り返します**。

4.  [ **ストレージセンスの構成] を** 選択するか、今すぐ実行し、ファイルを可能な限りオンラインに保つ設定を構成します (ドライブの容量が制限されています)。

推奨設定:

- Run Storage Sense = Every Day.
- アプリで使用していない一時ファイルを削除する = 14 日ごとに (少なくとも)。
- [ダウンロード] フォルダー内のファイルが 30 日間以上保存されている場合は、削除します。
- OneDrive: コンテンツは、30 日間以上開かされていない場合、オンライン専用になります。

### <a name="tablet-mode"></a>タブレット モード

必要に応じて、アクセシビリティのニーズに合ったタブレット モードを有効にします。


### <a name="sound-settings"></a>サウンド設定

1. サウンドの設定 **を検索し** 、このページを開きます。

2. 右側 **の [サウンド コントロール パネル** ] を選択し、[サウンド] タブ **を選択** します。

3. [**プログラム イベント] で**、[**デバイス接続] と [****デバイス切断] を [なし]** に**設定します**。

### <a name="silence-notifications"></a>無音通知

1. フォーカス アシストを **検索し** 、このページを開きます。

2. [アラーム **のみ] を選択します**。 これにより、一定の通知の飛び出しが回避されます。

### <a name="disk-cleanup"></a>ディスク クリーンアップ

1. ディスククリーンアップ **を検索し** 、このアプリを開きます。

2. [ **削除するファイル] で**、削除するファイルを選択します。 

3. また、[システム **ファイルのクリーンアップ] を選択します**。

## <a name="complete-and-verify"></a>完了して確認する

1. すべての Windows 更新プログラムをスキャンしてインストールします。

2. グループ ポリシーを更新します。

   1. 管理者特権のコマンド プロンプトで **、gpupdate /force /boot /wait:0 と入力します**。
   
3. デバイスを再起動します。

4. タスク バー アプリを確認します。

   - アプリの接続
   - ロック アイコン
   - 切り取り & スケッチ
   - Teams (該当する場合)
   - Officeアプリ (該当する場合)
   - Surface アプリ
   - ホワイトボード
    
5. プレゼンス検出を確認します。

   - プレゼンス検出は、システム トレイの緑色のアイコンになります。
    
6. この PC への投影が Connect アプリで有効になっているか確認します。 Project をこの  **PC 設定に構成** したら、少なくとも 1 回は接続アプリを実行します。 (その後、Surface Hub にプロジェクトを実行するために Connect アプリを実行する必要が生じない。

7. 電源とスリープの設定を確認します。

    - スクリーン セーバー: 15 分、(なし)、Mystify、または Blank に設定します。パスワードを要求するためのチェック ボックスがオンに設定されている必要があります。
    - 画面: **2 時間後にオフにします**。
    - PC:  **4 時間後にオフにします**。
    
8. Windows Hello が動作しているのを確認します。

9. 設定が無効になっている同期を確認します。

10. スタートアップ アプリを確認します。

> [!TIP]
> Windows 10 をインストールして構成した後、Surface Hub 2S は他の Windows 10 デバイスと同じ方法で管理できます。

## <a name="related-topics"></a>関連トピック

<a href="surface-hub-2s-migrate-os.md" target="_blank"> Surface Hub 2 の Windows 10 Pro または Enterprise に移行する</a>
