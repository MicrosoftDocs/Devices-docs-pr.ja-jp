---
title: コマンドを使用してビジネス向け Surface 診断ツールキットを実行する
description: コマンドコンソールで Surface 診断ツールキットを実行する方法
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 6a56e1231ff5d2f672305d7166bbfa46d1bc0354
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834294"
---
# コマンドを使用してビジネス向け Surface 診断ツールキットを実行する

コマンドプロンプトで Surface 診断ツールキット (SDT) を実行するには、STD アプリ本体をダウンロードする必要があります。 インストール後、コマンドプロンプトで、Windows コマンドコンソール (cmd.exe) 経由で、または Windows PowerShell を使用して、コマンド、コピー/貼り付け、その他の機能のオートコンプリートのサポートを提供することができます。  SDT でサポートされている Surface デバイスの一覧については、「[展開 Surface 診断ツールキット](surface-diagnostic-toolkit-business.md)」を参照してください。

>[!NOTE]
>コマンドを使用して SDT を実行するには、管理者アカウントにサインインしているか、Surface デバイスの管理者グループのメンバーであるアカウントにサインインしている必要があります。

## SDT アプリ本体の実行

[ [Surface Tools FOR IT] ダウンロードページ](https://www.microsoft.com/download/details.aspx?id=46703)から、SDT アプリ本体をダウンロードしてインストールします。 Windows コマンドプロンプト (cmd.exe) または Windows PowerShell を使用して、次のことを行うことができます。 

- すべてのログファイルを収集します。
- ベストプラクティスアナライザーを使用して正常性診断を実行します。
- 更新プログラムが見つからないことを確認します。

>[!NOTE]
>このリリースでは、SDT アプリ本体は単一のコマンドのみをサポートしています。 複数のコマンドラインオプションを実行するには、コマンドごとにコンソール exe を個別に実行する必要があります。 

既定では、出力ファイルは本体のアプリと同じ場所に保存されます。 コマンドの完全な一覧については、次の表を参照してください。

コマンド | 備考
--- | ---
-DataCollector "出力ファイル" | システムの詳細を zip ファイルに収集します。 "出力ファイル" は、システムの詳細 zip ファイルを作成するためのファイルパスです。<br><br>**例**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-bpa "出力ファイル" | デバイスの複数の設定と状態インジケーターを確認します。 "出力ファイル" は、HTML レポートを作成するためのファイルパスです。<br><br>**例**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-windows 版 | Windows Update online サーバーでファームウェアやドライバーの更新プログラムが見つからないかどうかを確認します。<br><br>**例**:<br>Microsoft.Surface.Diagnostics.App.Console.exe windows 版
保証 "出力ファイル" | デバイスの保証情報を確認します (有効または無効)。 省略可能な "output file" は、xml ファイルを作成するためのファイルパスです。 <br><br>**例**: <br>Microsoft.Surface.Diagnostics.App.Console.exe –保証 "warranty.xml"


>[!NOTE]
>ターゲットデバイスで SDT アプリコンソールをリモートで実行するには、Microsoft Endpoint Configuration Manager などの構成管理ツールを使用できます。 または、コンソールアプリと適切な本体のコマンドを含む .zip ファイルを作成し、組織のソフトウェア配布プロセスごとに展開することもできます。 

## ベストプラクティスアナライザーを実行する 

BPA テストは、BitLocker、セキュアブート、トラステッドプラットフォームモジュール (TPM) などの主要コンポーネント全体で実行でき、結果は共有可能なファイルに出力されます。 このツールは、色分けされた見出しと条件記述子付きの一連の表を生成し、その問題を解決する方法についてのガイダンスを示します。 

- 緑は、コンポーネントが最適な条件 (最適) で実行されていることを示します。
- オレンジは、コンポーネントが最適な状態で実行されていないことを示します (最適な状態ではありません)。
- 赤は、コンポーネントが異常な状態であることを示します。 

### BPA 結果の出力の例

<table>
<tr><th colspan="2"><font color="00ff00">BitLocker</font></th></tr>
<tr><td><strong>説明:</strong></td><td>システムドライブで BitLocker が有効になっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>保護</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>データを保護するために BitLocker を有効にすることを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">セキュア ブート</font></th></tr>
<tr><td><strong>説明:</strong></td><td>セキュアブートが有効になっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>True</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>PC を保護するには、セキュアブートを有効にすることを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">トラステッド プラットフォーム モジュール</font></th></tr>
<tr><td><strong>説明:</strong></td><td>TPM が機能していることを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>True</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>機能している TPM がない場合、BitLocker などのセキュリティベースの機能が正しく動作しないことがあります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">コネクトスタンバイ</font></th></tr>
<tr><td><strong>説明:</strong></td><td>接続されているスタンバイが有効であるかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>True</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>コネクトスタンバイにより、Surface デバイスは、使用されていないときに更新と通知を受け取ることができます。 最適なエクスペリエンスを実現するには、接続されたスタンバイを有効にする必要があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>説明:</strong></td><td>Bluetooth が有効になっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>有効</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">デバッグモード</font></th></tr>
<tr><td><strong>説明:</strong></td><td>オペレーティングシステムがデバッグモードになっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>通常</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>Debug ブートオプションは、Windows オペレーティングシステムのカーネルデバッグを有効または無効にします。 このオプションを有効にすると、システムが不安定になったり、DRM (デジタル著作権管理の emend) での保護されたメディアが再生されなくなる可能性があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">署名のテスト</font></th></tr>
<tr><td><strong>説明:</strong></td><td>テスト署名が有効になっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>通常</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>テスト署名は、プレリリース版のドライバーのテストにのみ使用される Windows のスタートアップ設定です。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">アクティブな Power Plan</font></th></tr>
<tr><td><strong>説明:</strong></td><td>適切な電源プランがアクティブになっていることを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>カッコ</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>生産性とバッテリー寿命を最大限に活用するには、"バランス" の power plan を使用することを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>説明:</strong></td><td>デバイスが Windows 更新プログラムによって最新の状態になっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>Microsoft Silverlight (KB4023307)、Windows Defender ウイルス対策の定義更新プログラム-KB2267602 (定義 1.279.1433.0)</td></tr>
<tr><td><strong>条件</strong></td><td><font color="ff9500">最適でない</font></td></tr>
<tr><td><strong>勧め</strong></td><td>最新の windows に更新すると、最新のファームウェアとドライバーが使用されます。 デバイスを常に最新の状態に維持することをお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">ハードドライブの空き領域</font></th></tr>
<tr><td><strong>説明:</strong></td><td>ハードドライブの空き領域が少なくなっているかどうかを確認します。</td></tr>
<tr><td><strong>値</strong></td><td>66%</td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>最高のパフォーマンスを得るには、ハードドライブの容量の少なくとも10% が空き容量である必要があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">機能していないデバイス</font></th></tr>
<tr><td><strong>説明:</strong></td><td>デバイスマネージャーで機能していないデバイスの一覧。</td></tr>
<tr><td><strong>値</strong></td><td></td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>デバイスマネージャーで機能していないデバイスを使用すると、各ハードウェアコンポーネントの電力を節約することなく、一定の表面デバイスで予期しない問題が発生する場合があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">外部モニター</font></th></tr>
<tr><td><strong>説明:</strong></td><td>互換性の問題がある可能性がある外付けモニターを確認します。</td></tr>
<tr><td><strong>値</strong></td><td></td></tr>
<tr><td><strong>条件</strong></td><td><font color="00ff00">しも</font></td></tr>
<tr><td><strong>勧め</strong></td><td>Surface デバイスとの互換性については、元の機器の製造元に確認してください。</td></tr>
</table>
