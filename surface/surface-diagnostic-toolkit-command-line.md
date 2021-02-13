---
title: コマンドを使用してビジネス向け Surface 診断ツールキットを実行する
description: コマンド コンソールで Surface Diagnostic Toolkitを実行する方法
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
ms.openlocfilehash: f3856499bd769b96e22c0a47323c984eb38d8a18
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327331"
---
# コマンドを使用してビジネス向け Surface 診断ツールキットを実行する

コマンド プロンプトで Surface Diagnostic Toolkit (SDT) を実行するには、SDT アプリ コンソールをダウンロードする必要があります。 インストール後、Windows コマンド コンソール (cmd.exe) を介してコマンド プロンプトで、またはコマンドのオートコンプリート、コピー/貼り付け、その他の機能のサポートを提供する PowerShell Integrated Scripting Environment (ISE) を含む Windows PowerShell を使用して SDT を実行できます。  SDT でサポートされている Surface デバイスの一覧については [、「Surface Diagnostic Toolkit for Business の展開」を参照してください](surface-diagnostic-toolkit-business.md)。

>[!NOTE]
>コマンドを使用して SDT を実行するには、Administrator アカウントにサインインするか、Surface デバイスの Administrator グループのメンバーであるアカウントにサインインする必要があります。

## SDT アプリ コンソールの実行

Surface Tools for IT ダウンロード ページから SDT アプリ コンソール [をダウンロードしてインストールします](https://www.microsoft.com/download/details.aspx?id=46703)。 Windows コマンド プロンプト (cmd.exe) または次のWindows PowerShell使用できます。 

- すべてのログ ファイルを収集します。
- ベスト プラクティス アナライザーを使用して正常性診断を実行します。
- ファームウェアまたはドライバーの更新プログラムが見つからないか、更新プログラムを確認します。

>[!NOTE]
>このリリースでは、SDT アプリ コンソールは単一のコマンドのみをサポートしています。 複数のコマンド ライン オプションを実行するには、コマンドごとにコンソール exe を個別に実行する必要があります。 

既定では、出力ファイルはコンソール アプリと同じ場所に保存されます。 コマンドの完全な一覧については、次の表を参照してください。

コマンド | 備考
--- | ---
-DataCollector "output file" | zip ファイルにシステムの詳細を収集します。 "出力ファイル" は、システムの詳細 zip ファイルを作成するファイル パスです。<br><br>**例**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-bpa "出力ファイル" | デバイス内のいくつかの設定と正常性インジケーターをチェックします。 "出力ファイル" は、HTML レポートを作成するファイル パスです。<br><br>**例**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-windowsupdate | ファームウェアやドライバーの更新プログラムが見つからないか、Windows Update オンライン サーバーをチェックします。<br><br>**例**:<br>Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate
-warranty "output file" | デバイスの保証情報を確認します (有効または無効)。 オプションの "出力ファイル" は、xml ファイルを作成するファイル パスです。 <br><br>**例**: <br>Microsoft.Surface.Diagnostics.App.Console.exe –保証 "warranty.xml"


>[!NOTE]
>SDT アプリ コンソールをターゲット デバイスでリモートで実行するには、Microsoft Endpoint Configuration Manager などの構成管理ツールを使用できます。 または、コンソール アプリと適切なコンソール コマンドを含む .zip ファイルを作成し、組織のソフトウェア配布プロセスごとに展開することもできます。 

## ベスト プラクティス アナライザーの実行 

BitLocker、セキュア ブート、トラステッド プラットフォーム モジュール (TPM) などの主要コンポーネント間で BPA テストを実行し、共有可能なファイルに結果を出力できます。 このツールは、色分けされた見出しと条件記述子を持つ一連のテーブルと、問題を解決する方法に関するガイダンスを生成します。 

- 緑は、コンポーネントが最適な状態 (最適) で実行されている状態を示します。
- オレンジ色は、コンポーネントが最適な状態で実行されていない (最適ではない) 状態を示します。
- 赤は、コンポーネントが異常な状態を示します。 

### サンプル BPA 結果の出力

<table>
<tr><th colspan="2"><font color="00ff00">BitLocker</font></th></tr>
<tr><td><strong>説明:</strong></td><td>システム ドライブで BitLocker が有効になっているか確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>保護のオン</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>BitLocker を有効にしてデータを保護することを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">セキュア ブート</font></th></tr>
<tr><td><strong>説明:</strong></td><td>セキュア ブートが有効になっているか確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>True</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>PC を保護するためにセキュア ブートを有効にすることを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">トラステッド プラットフォーム モジュール</font></th></tr>
<tr><td><strong>説明:</strong></td><td>TPM が機能している必要があります。</td></tr>
<tr><td><strong>値:</strong></td><td>True</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>機能する TPM がない場合、BitLocker などのセキュリティ ベースの機能が正しく動作しない可能性があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Connected Standby</font></th></tr>
<tr><td><strong>説明:</strong></td><td>接続スタンバイが有効になっているか確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>True</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>Connected Standby を使用すると、Surface デバイスは、使用されていない間に更新と通知を受信できます。 最適なエクスペリエンスを得る場合は、Connected Standby を有効にする必要があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>説明:</strong></td><td>有効になっているBluetoothチェックします。</td></tr>
<tr><td><strong>値:</strong></td><td>有効</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">デバッグ モード</font></th></tr>
<tr><td><strong>説明:</strong></td><td>オペレーティング システムがデバッグ モードにあるか確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>通常</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>デバッグ ブート オプションは、Windows オペレーティング システムのカーネル デバッグを有効または無効にします。 このオプションを有効にすると、システムが不安定化し、DRM (デジタル著作権管理) で保護されたメディアの再生が妨げる可能性があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">テスト署名</font></th></tr>
<tr><td><strong>説明:</strong></td><td>テスト署名が有効になっているか確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>通常</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>テスト署名は、プレリリース版のドライバーのテストにのみ使用する必要がある Windows スタートアップ設定です。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">アクティブな電源プラン</font></th></tr>
<tr><td><strong>説明:</strong></td><td>正しい電源計画がアクティブな状態を確認します。</td></tr>
<tr><td><strong>値:</strong></td><td>バランス</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>生産性とバッテリー残量を最大化するには、"バランス" 電源プランを使用することを強くお勧めします。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>説明:</strong></td><td>デバイスが Windows 更新プログラムで最新の情報を提供している場合にチェックします。</td></tr>
<tr><td><strong>値:</strong></td><td>Microsoft Silverlight (KB4023307)、Windows Defender ウイルス対策の定義の更新 - KB2267602 (定義 1.279.1433.0)</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="ff9500">最適ではない</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>最新のウィンドウに更新すると、最新のファームウェアとドライバーを使用できます。 デバイスを常に最新の状態に保つ必要があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">空きハード ドライブ領域</font></th></tr>
<tr><td><strong>説明:</strong></td><td>低い空きハード ドライブ領域をチェックします。</td></tr>
<tr><td><strong>値:</strong></td><td>66%</td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>最適なパフォーマンスを得る場合は、ハード ドライブの容量の少なくとも 10% が空き領域として必要です。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">非機能デバイス</font></th></tr>
<tr><td><strong>説明:</strong></td><td>デバイス マネージャーの機能しないデバイスの一覧。</td></tr>
<tr><td><strong>値:</strong></td><td></td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>デバイス マネージャーの非機能デバイスは、各ハードウェア コンポーネントの省電力など、Surface デバイスで予期しない問題を引き起こす可能性があります。</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">外部モニター</font></th></tr>
<tr><td><strong>説明:</strong></td><td>互換性の問題がある可能性がある外部モニターを確認します。</td></tr>
<tr><td><strong>値:</strong></td><td></td></tr>
<tr><td><strong>条件:</strong></td><td><font color="00ff00">最適</font></td></tr>
<tr><td><strong>ガイダンス:</strong></td><td>Surface デバイスとの互換性については、元の機器の製造元に確認してください。</td></tr>
</table>
