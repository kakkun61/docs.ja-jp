---
title: クライアントでのデバッグ
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 4fc647bcde3d9aed27a46298be8d863947ba0726
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243990"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="b9459-102">クライアントでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="b9459-102">Debugging on the Client</span></span>

<span data-ttu-id="b9459-103">ユーザーが WCF サービスのクライアントアプリケーションを簡単に作成できるようにするには、サービス [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) の構成ファイルにサービスの動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9459-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="b9459-104">この動作は、ヘルプ ページを公開し、クライアントに返される SOAP エラーの詳細にマネージド例外情報を表示するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9459-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
