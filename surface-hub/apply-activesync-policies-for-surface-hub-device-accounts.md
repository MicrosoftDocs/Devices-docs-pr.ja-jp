---
title: デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)
description: Microsoft Surface Hub のデバイス アカウントでは、ActiveSync を使用してメールとカレンダーが同期されます。 これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。
ms.assetid: FAABBA74-3088-4275-B58E-EC1070F4D110
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, ActiveSync ポリシー
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 7ead08e49d3eee2d616ac9fcf06b85dd82e136dc
ms.sourcegitcommit: 4ec96ff1cd563d055fa0689a63f136acf2794a2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "11474734"
---
# <a name="applying-activesync-policies-to-device-accounts-surface-hub"></a>デバイス アカウントへの ActiveSync ポリシーの適用 (Surface Hub)


Active Directory デバイス アカウントを使用する Surface Hub (ドメイン **\** ユーザー名形式でハブにプロビジョニング) とオンプレミスの Exchange サービスでは、ActiveSync を使用してメールと予定表を同期します。 これにより、スケジュール設定済みの会議に Surface Hub から参加して開始でき、会議中に作成したすべてのホワイトボードをメールで送信できます。

これらの機能が動作するには、組織の ActiveSync ポリシーが次のように構成されている必要があります。

-   Surface Hub のデバイス アカウントによって使用されるリソース メールボックスの、同期をブロックするグローバル ポリシーは、存在できません。 このようなブロック ポリシーがある場合は、許可されたデバイスとして Surface Hub を追加する必要があります。
-   **PasswordEnabled** 設定が False に設定されているモバイル デバイス メールボックス ポリシーを設定する必要があります。 その他のモバイル デバイス メールボックス ポリシーには、Surface Hub との互換性がありません。

## <a name="allowing-the-deviceid"></a>DeviceID の許可

組織には、Surface Hub にプロビジョニングされたデバイス アカウントが同期されないようにするグローバル ポリシーが存在している場合があります。 このプロパティを構成するには、「 [ActiveSync に対するデバイス ID の許可](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync)」をご覧ください。

## <a name="setting-passwordenabled"></a>PasswordEnabled の設定

デバイス アカウントには、 **PasswordEnabled** 属性が False または 0 に設定された ActiveSync ポリシーが必要です。 このプロパティを構成するには、「 [Surface Hub と互換性のある Microsoft Exchange ActiveSync ポリシーの作成](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy)」をご覧ください。

 

 





