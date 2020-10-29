---
title: SYSLIB0006 警告
description: コンパイル時の警告 SYSLIB0006 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 45d2d8ec6ad99996f8b8f46d0c2e0ac2e02cf450
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333146"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="61d5a-103">SYSLIB0006: Thread.Abort はサポート対象外</span><span class="sxs-lookup"><span data-stu-id="61d5a-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="61d5a-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="61d5a-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="61d5a-105">これらの API を使用すると、コンパイル時に警告 `SYSLIB0006` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="61d5a-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="61d5a-106">回避策</span><span class="sxs-lookup"><span data-stu-id="61d5a-106">Workaround</span></span>

<span data-ttu-id="61d5a-107"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す代わりに、<xref:System.Threading.CancellationToken> を使用して作業単位の処理を中止します。</span><span class="sxs-lookup"><span data-stu-id="61d5a-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="61d5a-108">次の例は、<xref:System.Threading.CancellationToken>の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="61d5a-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

```csharp
void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
{
    if (QueryIsMoreWorkPending())
    {
        // If the CancellationToken is marked as "needs to cancel",
        // this will throw the appropriate exception.
        cancellationToken.ThrowIfCancellationRequested();

        WorkItem work = DequeueWorkItem();
        ProcessWorkItem(work);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="61d5a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="61d5a-109">See also</span></span>

- [<span data-ttu-id="61d5a-110">Thread.Abort は旧型式 - 破壊的変更</span><span class="sxs-lookup"><span data-stu-id="61d5a-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="61d5a-111">マネージド スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="61d5a-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
