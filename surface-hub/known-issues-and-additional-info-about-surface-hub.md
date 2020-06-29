---
title: Microsoft Surface Hub に関する既知の問題と追加情報
description: Microsoft Surface Hub の既知の問題について概要を示します。
ms.assetid: aee90a0c-fb05-466e-a2b1-92de89d0f2b7
keywords: surface、ハブ、問題
ms.prod: surface-hub
ms.sitesec: library
author: todmccoy
ms.author: v-todmc
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ec6746098203b5e91e2aaf3b044d21b81c31c897
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "10835430"
---
# Microsoft Surface Hub に関する既知の問題と追加情報

お待ちしています。 品質は最優先事項であり、お客様に影響を及ぼす問題について常に把握しておく必要があります。 Microsoft Surface Hub の既知の問題を次に示します。

- **Skype for Business が RS2 でメディアトラフィックにプロキシを使用していない**
<br/>一部の Surface Hub ユーザーがプロキシを使用している場合、Skype for Business では、メディアのプロキシサーバーは使用されません。 ただし、Surface Hub はアカウントにサインインすることができます。 お客様からのフィードバックを受け取りました。プロキシを使用しているときのメディアトラフィックの問題を認識しています。 この問題を積極的に調査しており、解決策を特定してテストしたらすぐに、この問題を解決することになります。 

- **AAD に参加しているデバイスでは、ユーザーが "自分の会議 & ファイル" にサインインしようとしたときに、Surface Hub からインターネットに接続していないという報告があります。**
<br/>Surface Hub でのサインインとドキュメントアクセスに影響する問題を認識しています。 この問題について積極的に調査しています。 解決策として、解決策がリリースされるまでの間、ユーザーはデバイスをリセットし、ローカル管理者アカウントを使用するようにハブを設定することができます。 ローカルの管理者アカウントを使用するように再構成した後、[自分の会議とファイル] は期待どおりに動作します。
- **Azure AD が参加している場合のシングルサインイン**
<br/>Surface Hub は共用スペース向けに設計されていました。これは、ユーザーの資格情報が保存される方法に影響します。 このため、デバイスが Azure AD に参加している場合、シングルサインインのしくみについて、現時点では制限があります。 Microsoft はこの制限を認識しており、解決策のために積極的に調査しています。
- **Surface hub のフレンドリ名にドット文字 (.) が含まれている場合、Surface Hub に対するインフラストラクチャプロジェクションの Miracast が失敗する**
<br/>フレンドリ名に名前のピリオドまたはドットが含まれている場合、Surface Hub ユーザーは、"Room42" のように、デバイスへのプロジェクションで問題が発生する可能性があります。 この問題を回避するには、[**設定**] Surface Hub でハブのフレンドリ名を変更  >  **Surface Hub**  >  **About**し、デバイスを再起動します。 Microsoft は、この問題の解決に取り組んでいます。