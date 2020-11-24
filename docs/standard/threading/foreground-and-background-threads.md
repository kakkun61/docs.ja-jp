---
title: フォアグラウンド スレッドとバックグラウンド スレッド
description: .NET で Thread.IsBackground プロパティを使用してスレッドがバックグラウンド スレッドであるか、フォアグラウンド スレッドであるかを判断します。
ms.date: 03/30/2017
helpviewer_keywords:
- threading [.NET], foreground
- threading [.NET], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 9f0ea1d53eb2f96b8a56cacc089cf90eb2f079a0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819904"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="a0875-103">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="a0875-103">Foreground and background threads</span></span>

<span data-ttu-id="a0875-104">マネージド スレッドは、バックグラウンド スレッドまたはフォアグラウンド スレッドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="a0875-104">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="a0875-105">バックグラウンド スレッドは、1 つの例外を除き、フォアグラウンド スレッドと同じです。その例外とは、バックグラウンド スレッドではマネージド実行環境を実行させておくことができないことです。</span><span class="sxs-lookup"><span data-stu-id="a0875-105">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="a0875-106">すべてのフォアグラウンド スレッドが (.exe ファイルがマネージド アセンブリである) マネージド プロセスで停止されると、システムはすべてのバックグラウンド スレッドを停止し、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="a0875-106">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0875-107">プロセスがシャットダウンしているため、ランタイムがバックグラウンド スレッドを停止した場合、スレッドでは例外がスローされません。</span><span class="sxs-lookup"><span data-stu-id="a0875-107">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="a0875-108">ただし、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドがアプリケーション ドメインをアンロードしたために、スレッドが停止された場合、フォアグラウンド スレッドとバックグラウンド スレッドの両方で <xref:System.Threading.ThreadAbortException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a0875-108">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="a0875-109">スレッドがバックグラウンド スレッドであるか、フォアグラウンド スレッドであるかを判断する場合や、その状態を変更する場合は、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0875-109">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="a0875-110">スレッドは、<xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定することで、いつでもバックグラウンド スレッドに変更できます。</span><span class="sxs-lookup"><span data-stu-id="a0875-110">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0875-111">スレッドのフォアグラウンドまたはバックグラウンドの状態が、スレッドのハンドルされない例外の結果に影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="a0875-111">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="a0875-112">フォアグラウンドまたはバックグラウンド スレッドのハンドルされない例外により、アプリケーションが終了します。</span><span class="sxs-lookup"><span data-stu-id="a0875-112">An unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="a0875-113">「[マネージド スレッドの例外](exceptions-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0875-113">See [Exceptions in Managed Threads](exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="a0875-114">マネージド スレッド プールに属するスレッド (つまり、<xref:System.Threading.Thread.IsThreadPoolThread%2A> プロパティが `true` のスレッド) はバックグラウンド スレッドです。</span><span class="sxs-lookup"><span data-stu-id="a0875-114">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="a0875-115">アンマネージド コードからマネージド実行環境に入るすべてのスレッドは、バックグラウンド スレッドとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="a0875-115">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="a0875-116">新しい <xref:System.Threading.Thread> オブジェクトを作成して開始することで生成されるすべてのスレッドは、既定でフォアグラウンド スレッドとなります。</span><span class="sxs-lookup"><span data-stu-id="a0875-116">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="a0875-117">スレッドを使用して、ソケット接続などのアクティビティを監視する場合は、その <xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定して、スレッドがプロセスの終了を回避しないようにします。</span><span class="sxs-lookup"><span data-stu-id="a0875-117">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0875-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0875-118">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
