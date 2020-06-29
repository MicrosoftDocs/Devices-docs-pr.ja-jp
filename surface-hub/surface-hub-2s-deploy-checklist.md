---
title: Surface Hub 2S 展開チェックリスト
description: 展開前と展開後のチェックリストを使用して Surface Hub 2S の展開を確認します。
keywords: コンマで値を区切る
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 3c30892a3ae4f534006aa32ad6d969b42a52cbf2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836366"
---
# Surface Hub 2S 展開チェックリスト

## Surface Hub 2S 事前展開チェックリスト

|**項目**|**応答**|
|:------ |:------ |
|**デバイスアカウント名**| |
|**デバイスアカウントの UPN**| |
|**ActiveSync ポリシー**| |
|**予定表処理の構成が完了しました**| ☐はい <br>  ☐いいえ |
|**デバイスフレンドリ名**| |
|**デバイスのホスト名**| |
|**危害**| ☐なし <br> Active Directory の所属☐ <br> Azure Active Directory の☐ |
|**Microsoft Teams モード**| ☐モード0 <br> ☐モード1 <br> ☐モード2 |
|**デバイス管理**| ☐はい、Microsoft Intune <br> ☐はい、その他のモバイルデバイスマネージャー [MDM] <br> ☐なし |  
|**プロキシ**| 自動構成の☐ <br> ☐プロキシサーバー <br> ☐プロキシ自動構成 (PAC) ファイル |
|**プロキシ認証**| ☐デバイスアカウントの資格情報 <br> 資格情報の入力を求める☐ |
|**パスワードの循環**| ☐ <br> ☐オフ |
|**Skype for Business のその他のドメイン名 (オンプレミスのみ)**| |
|**セッションのタイムアウト時間**| |
|**セッションタイムアウトアクション**| ☐の終了セッション <br> ☐履歴書の許可 |
|**自分の会議とファイル**| ☐有効 <br> ☐無効 |
|**ロック画面のタイムアウト**| |
|**スリープアイドルタイムアウト**| |
|**Bluetooth**| ☐ <br> ☐オフ |
|**BitLocker USB ドライブのみを使用する**| ☐ <br> ☐オフ |
|**追加の証明書をインストールする (オンプレミスのみ)**| |
|**Windows Update**| 一般法人向け Windows Update の☐ <br> ☐ Windows Server Update Services (WSUS) |
|**Surface app スピーカーの設定**| ☐のローリングスタンド <br> ☐壁搭載 |
|**IP アドレス**| ☐ワイヤード (有線)、DHCP <br> ☐ワイヤード (有線)、DHCP 予約 <br> ワイヤレス☐ (DHCP) <br> ☐ Wireless — DHCP 予約 |

## Surface Hub 2S 展開後のチェックリスト

|**チェックマーク**|**応答**|
|:------|:---------|
|**デバイスアカウントの同期**| ☐はい <br> ☐いいえ |
|**Bitlocker キー**| ☐ファイルに保存されました (所属しません) <br> Active Directory (AD の所属) に保存されている☐ <br>Azure AD に保存されている☐ (Azure AD の所属) |
|**デバイス OS の更新プログラム**| ☐完了 |
|**Windows ストアの更新プログラム**| 自動☐ <br> 手動☐ |
|**Microsoft Teams のスケジュールされた会議**| ☐確認メールを受信しました <br> ☐会議がスタート画面に表示される <br>  ☐ワンタッチ結合関数 <br> オーディオに参加できる☐ <br> ビデオに参加できる☐ <br> 画面を共有できる☐ ||
|**Skype for Business のスケジュールされた会議**| ☐確認メールを受信しました <br> ☐会議がスタート画面に表示される <br> ☐のワンタッチ結合関数が正しく動作する <br> オーディオに参加できる☐ <br> ビデオに参加できる☐ <br> 画面を共有できる☐ <br> IM の送受信が可能☐ |
|**既に招待されている会議のスケジュール**| 会議の辞退☐ |
|**Microsoft Teams のアドホック会議**| 他のユーザーを招待する☐ <br> オーディオに参加できる☐ <br> ビデオに参加できる☐ <br> 画面を共有できる☐ |
|**Skype for Business のスケジュールされた会議**| 他のユーザーを招待する☐ <br> オーディオに参加できる☐ <br> ビデオに参加できる☐ <br> 画面を共有できる☐ <br> IM の送受信が可能☐ |
|**Microsoft Whiteboard**| ようこそ/スタート画面からの起動☐ <br> Microsoft Teams からの☐起動 | 
|**Skype/Teams 通話の着信**| オーディオに参加できる☐<br>ビデオに参加できる☐ <br> 画面を共有できる☐ <br> IM の送受信が可能☐ (Skype for Business のみ) |
|**ライブビデオストリームの受信**| ☐の最大値 2 (Skype for Business) <br> ☐の最大値 4 (Microsoft Teams) |
|**Microsoft Teams モード0の動作**| ようこそ/スタート画面の Skype for Business タイルを☐ <br> スケジュールされた Skype for Business 会議に参加できる☐ (Skype UI) <br> スケジュールされたチーム会議に参加できる☐ (Teams UI) |
|**Microsoft Teams モード1の動作**| ようこそ/スタート画面の [チーム] タイルを☐ <br> スケジュールされた Skype for Business 会議に参加できる☐ (Skype UI) <br> スケジュールされたチーム会議に参加できる☐ (Teams UI) |
|**Microsoft Teams モード2の動作**| ようこそ/スタート画面の [チーム] タイルを☐ <br> スケジュールされたチーム会議に参加できる☐ <br> Skype for Business 会議に参加できない☐ |
