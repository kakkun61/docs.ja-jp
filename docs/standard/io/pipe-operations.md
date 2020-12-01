---
title: .NET のパイプ操作
description: .NET のパイプ操作について説明します。 パイプは、プロセス間通信の手段となります。 パイプには、匿名パイプと名前付きパイプの 2 種類があります。
ms.date: 03/30/2017
helpviewer_keywords:
- pipes [.NET]
- pipe operations [.NET]
- interprocess communication [.NET], pipes
- I/O [.NET], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: bb8804c32b9f2b54b05298779bddae117c10dcf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734804"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="f25de-105">.NET のパイプ操作</span><span class="sxs-lookup"><span data-stu-id="f25de-105">Pipe Operations in .NET</span></span>

<span data-ttu-id="f25de-106">パイプは、プロセス間通信の手段となります。</span><span class="sxs-lookup"><span data-stu-id="f25de-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="f25de-107">パイプには、2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="f25de-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="f25de-108">匿名パイプ。</span><span class="sxs-lookup"><span data-stu-id="f25de-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="f25de-109">匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="f25de-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="f25de-110">匿名パイプは、名前付きパイプより必要なオーバーヘッドは少ないですが、提供するサービスは限られています。</span><span class="sxs-lookup"><span data-stu-id="f25de-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="f25de-111">匿名パイプは一方向であり、ネットワーク経由で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f25de-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="f25de-112">これでは、1 つのサーバー インスタンスのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f25de-112">They support only a single server instance.</span></span> <span data-ttu-id="f25de-113">匿名パイプは、スレッド間、またはパイプ ハンドルを作成時に子プロセスに簡単に渡すことができる親と子のプロセス間の通信で便利です。</span><span class="sxs-lookup"><span data-stu-id="f25de-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="f25de-114">.NET では、<xref:System.IO.Pipes.AnonymousPipeServerStream> クラスと <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用して匿名パイプを実装します。</span><span class="sxs-lookup"><span data-stu-id="f25de-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="f25de-115">「[方法:ローカルのプロセス間通信で匿名パイプを使用する](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25de-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="f25de-116">名前付きパイプ。</span><span class="sxs-lookup"><span data-stu-id="f25de-116">Named pipes.</span></span>  
  
     <span data-ttu-id="f25de-117">名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="f25de-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="f25de-118">名前付きパイプは、一方向であることも、双方向であることも可能です。</span><span class="sxs-lookup"><span data-stu-id="f25de-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="f25de-119">これでは、メッセージ ベースの通信がサポートされ、同じパイプ名を使用して複数のクライアントが同時にサーバー プロセスに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="f25de-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="f25de-120">名前付きパイプでは、プロセスを接続してリモート サーバーで独自のアクセス許可を使用する、偽装もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f25de-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="f25de-121">.NET では、<xref:System.IO.Pipes.NamedPipeServerStream> クラスと <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用して名前付きパイプを実装します。</span><span class="sxs-lookup"><span data-stu-id="f25de-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="f25de-122">「[方法:ネットワークのプロセス間通信で名前付きパイプを使用する](how-to-use-named-pipes-for-network-interprocess-communication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25de-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25de-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f25de-123">See also</span></span>

- [<span data-ttu-id="f25de-124">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="f25de-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="f25de-125">方法: ローカルのプロセス間通信で匿名パイプを使用する</span><span class="sxs-lookup"><span data-stu-id="f25de-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="f25de-126">方法: ネットワークのプロセス間通信で名前付きパイプを使用する</span><span class="sxs-lookup"><span data-stu-id="f25de-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
