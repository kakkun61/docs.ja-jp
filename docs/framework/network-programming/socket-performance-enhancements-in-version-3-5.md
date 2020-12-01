---
title: バージョン 3.5 のソケット パフォーマンスの強化
description: .NET Framework のバージョン 3.5 における System.Net.Sockets.Socket クラスのパフォーマンス改善について説明します。
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5bd7c97d6a6edd5f914d6fe3118b6d81b64544e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263140"
---
# <a name="socket-performance-enhancements-in-version-35"></a><span data-ttu-id="cfe8a-103">バージョン 3.5 のソケット パフォーマンスの強化</span><span class="sxs-lookup"><span data-stu-id="cfe8a-103">Socket Performance Enhancements in Version 3.5</span></span>

<span data-ttu-id="cfe8a-104">非同期ネットワーク I/O を利用して最高のパフォーマンスを達成するために、バージョン 3.5 で、<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> クラスが機能強化されました。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-104">The <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class has been enhanced in Version 3.5 for use by applications that use asynchronous network I/O to achieve the highest performance.</span></span> <span data-ttu-id="cfe8a-105"><xref:System.Net.Sockets.Socket> クラスの機能強化の一環として、一連の新しいクラスが追加されました。これが提供する代替非同期パターンは、目的に特化した高パフォーマンスのソケット アプリケーションで利用できます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-105">A series of new classes have been added as part of a set of enhancements to the <xref:System.Net.Sockets.Socket> class that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span> <span data-ttu-id="cfe8a-106">この機能強化は、高いパフォーマンスを必要とするネットワーク サーバー アプリケーションのために設計されたものです。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-106">These enhancements were specifically designed for network server applications that require high performance.</span></span> <span data-ttu-id="cfe8a-107">あるアプリケーションで、機能強化された非同期パターンを排他的に、言い換えると、アプリケーションの高負荷領域 (大量のデータを受け取るときなど) のみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-107">An application can use the enhanced asynchronous pattern exclusively, or only in targeted hot areas of their application (when receiving large amounts of data, for example).</span></span>  
  
## <a name="class-enhancements"></a><span data-ttu-id="cfe8a-108">クラスの拡張機能</span><span class="sxs-lookup"><span data-stu-id="cfe8a-108">Class Enhancements</span></span>  

 <span data-ttu-id="cfe8a-109">この機能強化の主な特徴は、高ボリュームの非同期ソケット I/O 中、オブジェクトの割り当てと同期が繰り返されることを避けることにあります。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-109">The main feature of these enhancements is the avoidance of the repeated allocation and synchronization of objects during high-volume asynchronous socket I/O.</span></span> <span data-ttu-id="cfe8a-110">非同期ソケット I/O のために <xref:System.Net.Sockets.Socket> クラスにより現在実装されている開始/終了設計パターンでは、非同期ソケット操作のたびに、<xref:System.IAsyncResult?displayProperty=nameWithType> オブジェクトを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-110">The Begin/End design pattern currently implemented by the <xref:System.Net.Sockets.Socket> class for asynchronous socket I/O requires a <xref:System.IAsyncResult?displayProperty=nameWithType> object be allocated for each asynchronous socket operation.</span></span>  
  
 <span data-ttu-id="cfe8a-111">新しい <xref:System.Net.Sockets.Socket> クラス機能強化では、非同期ソケット操作は、アプリケーションにより割り当てられ、保守管理される再利用可能 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> クラス オブジェクトによって記述されます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-111">In the new <xref:System.Net.Sockets.Socket> class enhancements, asynchronous socket operations are described by reusable <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> class objects allocated and maintained by the application.</span></span> <span data-ttu-id="cfe8a-112">高パフォーマンスのソケット アプリケーションは、維持する必要があるオーバーラップしたソケット操作の量を効率的に認識します。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-112">High-performance socket applications know best the amount of overlapped socket operations that must be sustained.</span></span> <span data-ttu-id="cfe8a-113">アプリケーションは <xref:System.Net.Sockets.SocketAsyncEventArgs> オブジェクトを必要な数だけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-113">The application can create as many of the <xref:System.Net.Sockets.SocketAsyncEventArgs> objects that it needs.</span></span> <span data-ttu-id="cfe8a-114">たとえば、サーバー アプリケーションが、入ってくるクライアント接続レートに対応するために、15 のソケット受け取り操作を常に未処理状態にしておく必要がある場合、その目的のために前もって 15 の再利用可能 <xref:System.Net.Sockets.SocketAsyncEventArgs> オブジェクトを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-114">For example, if a server application needs to have 15 socket accept operations outstanding at all times to support incoming client connection rates, it can allocate 15 reusable <xref:System.Net.Sockets.SocketAsyncEventArgs> objects in advance for that purpose.</span></span>  
  
 <span data-ttu-id="cfe8a-115">このクラスで非同期ソケット操作を実行するパターンは次の手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-115">The pattern for performing an asynchronous socket operation with this class consists of the following steps:</span></span>  
  
1. <span data-ttu-id="cfe8a-116">新しい <xref:System.Net.Sockets.SocketAsyncEventArgs> コンテキスト オブジェクトを割り当てるか、アプリケーション プールから空きコンテキスト オブジェクトを入手します。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-116">Allocate a new <xref:System.Net.Sockets.SocketAsyncEventArgs> context object, or get a free one from an application pool.</span></span>  
  
2. <span data-ttu-id="cfe8a-117">コンテキスト オブジェクトのプロパティをこれから実行する操作 (コールバック デリゲート メソッドやデータ バッファーなど) に設定します。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-117">Set properties on the context object to the operation about to be performed (the callback delegate method and data buffer, for example).</span></span>  
  
3. <span data-ttu-id="cfe8a-118">適切なソケット メソッド (xxxAsync) を呼び出し、非同期操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-118">Call the appropriate socket method (xxxAsync) to initiate the asynchronous operation.</span></span>  
  
4. <span data-ttu-id="cfe8a-119">非同期ソケット メソッド (xxxAsync) がコールバックで true を返した場合、コンテキスト プロパティに完了状態を問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-119">If the asynchronous socket method (xxxAsync) returns true in the callback, query the context properties for completion status.</span></span>  
  
5. <span data-ttu-id="cfe8a-120">非同期ソケット メソッド (xxxAsync) がコールバックで false を返した場合、操作は非同期で完了しています。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-120">If the asynchronous socket method (xxxAsync) returns false in the callback, the operation completed synchronously.</span></span> <span data-ttu-id="cfe8a-121">コンテキスト プロパティに操作結果が問い合わされることがあります。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-121">The context properties may be queried for the operation result.</span></span>  
  
6. <span data-ttu-id="cfe8a-122">別の操作でコンテキストを再利用するか、プールに戻すか、破棄します。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-122">Reuse the context for another operation, put it back in the pool, or discard it.</span></span>  
  
 <span data-ttu-id="cfe8a-123">新しい非同期ソケット操作コンテキスト オブジェクトの有効期間は、アプリケーション コードの参照と非同期 I/O の参照により決定されます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-123">The lifetime of the new asynchronous socket operation context object is determined by references in the application code and asynchronous I/O references.</span></span> <span data-ttu-id="cfe8a-124">非同期ソケット操作メソッドの 1 つにパラメーターとして送信された後、非同期ソケット操作コンテキスト オブジェクトの参照をアプリケーションが維持する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-124">It is not necessary for the application to retain a reference to an asynchronous socket operation context object after it is submitted as a parameter to one of the asynchronous socket operation methods.</span></span> <span data-ttu-id="cfe8a-125">完了コールバックが戻るまで、参照状態が維持されます。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-125">It will remain referenced until the completion callback returns.</span></span> <span data-ttu-id="cfe8a-126">ただし、コンテキスト オブジェクトの参照をアプリケーションが維持することには、将来の非同期ソケット操作で再利用できるため、利便性があります。</span><span class="sxs-lookup"><span data-stu-id="cfe8a-126">However it is advantageous for the application to retain the reference to the context object so that it can be reused for a future asynchronous socket operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe8a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfe8a-127">See also</span></span>

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [<span data-ttu-id="cfe8a-128">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="cfe8a-128">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="cfe8a-129">ソケットのコード例</span><span class="sxs-lookup"><span data-stu-id="cfe8a-129">Socket Code Examples</span></span>](socket-code-examples.md)
