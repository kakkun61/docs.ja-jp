---
title: ピアツーピア ネットワーク
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 001185dc38c06b6546bc7f973bb155cd0af5cf9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272086"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="583d9-102">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="583d9-102">Peer-to-Peer Networking</span></span>

<span data-ttu-id="583d9-103">ピアチャネルは、Windows Communication Foundation (WCF) における、マルチパーティのピアツーピア (P2P) 通信テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="583d9-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="583d9-104">この技術によって、アプリケーション開発者は安全で拡張可能なメッセージ ベースの P2P 通信チャネルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="583d9-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="583d9-105">ピア チャネルのメリットを活用するマルチパーティ アプリケーションの一般的な例は、チャットなどの共同作業アプリケーションです。チャットでは、ユーザーのグループがサーバーなしのピアツーピア方式で互いに会話します。</span><span class="sxs-lookup"><span data-stu-id="583d9-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="583d9-106">ピア チャネルを使用することで、顧客シナリオや企業シナリオでの P2P コラボレーション、コンテンツ配布、負荷分散、および分散処理が実現します。</span><span class="sxs-lookup"><span data-stu-id="583d9-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="583d9-107">Windows Vista では、ピアチャネルが既定で有効になっています。これはすべて WCF です。</span><span class="sxs-lookup"><span data-stu-id="583d9-107">Peer Channel is enabled by default on Windows Vista, as is all of WCF.</span></span> <span data-ttu-id="583d9-108">ピア チャネルのクラスにアクセスするには、プロジェクトに System.ServiceModel.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="583d9-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="583d9-109">次の各セクションには、ピアツーピア ネットワークに関する情報と、ピア チャネルのクラスを使用してピア対応のネットワーク アプリケーションを作成する方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="583d9-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="583d9-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="583d9-110">In This Section</span></span>  

 <span data-ttu-id="583d9-111">[ピアチャネルのシナリオ](peer-channel-scenarios.md): パブリケーション/サブスクリプションメッセージング、コラボレーション、分散処理、ゲームなど、ピアチャネル api でサポートされる開発シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="583d9-111">[Peer Channel Scenarios](peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="583d9-112">[ピアチャネルの概念](peer-channel-concepts.md): ピアメッシュ、ピアノード、ピアチャネルのセキュリティ、およびピアリゾルバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="583d9-112">[Peer Channel Concepts](peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="583d9-113">[ピアチャネルアプリケーションの構築](building-a-peer-channel-application.md): ピアチャネルアプリケーションの開発に関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="583d9-113">[Building a Peer Channel Application](building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="583d9-114">ピア チャネルのコード例</span><span class="sxs-lookup"><span data-stu-id="583d9-114">Peer Channel Code Examples</span></span>  

 <span data-ttu-id="583d9-115">[ピア チャネル カスタム ピア リゾルバー](/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="583d9-115">[Peer Channel Custom Peer Resolver](/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="583d9-116">ピア チャネル チームのブログ</span><span class="sxs-lookup"><span data-stu-id="583d9-116">Peer Channel Team blog</span></span>  

 [<span data-ttu-id="583d9-117">ピアチャネルチームのブログ</span><span class="sxs-lookup"><span data-stu-id="583d9-117">Peer Channel Team Blog</span></span>](/archive/blogs/peerchan/)
