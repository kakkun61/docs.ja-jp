---
title: 接続のグループ化
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 8bd4412a4c13dd490fce3118f59b5bb1f0d3ea85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250568"
---
# <a name="connection-grouping"></a><span data-ttu-id="3ae35-102">接続のグループ化</span><span class="sxs-lookup"><span data-stu-id="3ae35-102">Connection Grouping</span></span>

<span data-ttu-id="3ae35-103">接続のグループ化では、1 つのアプリケーション内の特定の要求を定義済みの接続プールに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="3ae35-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="3ae35-104">これは、ユーザーの代わりにバック エンド サーバーに接続し、デリゲートをサポートする認証プロトコル (Kerberos など) を使用する中間層アプリケーションや、以下の例のように、独自の資格情報を指定する中間層アプリケーションで必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ae35-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="3ae35-105">たとえば、Joe というユーザーが、自分の給与情報を表示する内部 Web サイトにアクセスするとします。</span><span class="sxs-lookup"><span data-stu-id="3ae35-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="3ae35-106">Joe の認証後、中間層アプリケーション サーバーは、Joe の資格情報を使用してバック エンド サーバーに接続し、Joe の給与情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3ae35-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="3ae35-107">次に、Susan がサイトにアクセスし、自分の給与情報を要求します。</span><span class="sxs-lookup"><span data-stu-id="3ae35-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="3ae35-108">中間層アプリケーションが Joe の資格情報を使用して既に接続しているため、バック エンド サーバーは Joe の情報で応答します。</span><span class="sxs-lookup"><span data-stu-id="3ae35-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="3ae35-109">ただし、アプリケーションがバック エンド サーバーに送信される各要求をユーザー名から形成される接続グループに割り当てると、各ユーザーは個別の接続プールに属すことになり、誤って他のユーザーと認証情報を共有することがなくなります。</span><span class="sxs-lookup"><span data-stu-id="3ae35-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="3ae35-110">要求を特定の接続グループに割り当てるには、要求を行う前に、<xref:System.Net.WebRequest> の <xref:System.Net.WebRequest.ConnectionGroupName%2A> プロパティに名前を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ae35-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae35-111">参照</span><span class="sxs-lookup"><span data-stu-id="3ae35-111">See also</span></span>

- [<span data-ttu-id="3ae35-112">接続の管理</span><span class="sxs-lookup"><span data-stu-id="3ae35-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="3ae35-113">方法: グループの接続にユーザー情報を割り当てる</span><span class="sxs-lookup"><span data-stu-id="3ae35-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
