---
title: SYSLIB0006 警告
description: コンパイル時の警告 SYSLIB0006 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 222b669a8a0260713e85721e6031144bb7bda5cc
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440661"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="3913e-103">SYSLIB0006: Thread.Abort はサポート対象外</span><span class="sxs-lookup"><span data-stu-id="3913e-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="3913e-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="3913e-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="3913e-105">これらの API を使用すると、コンパイル時に警告 `SYSLIB0006` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3913e-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="3913e-106">回避策</span><span class="sxs-lookup"><span data-stu-id="3913e-106">Workarounds</span></span>

<span data-ttu-id="3913e-107"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す代わりに、<xref:System.Threading.CancellationToken> を使用して作業単位の処理を中止します。</span><span class="sxs-lookup"><span data-stu-id="3913e-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3913e-108">次の例は、<xref:System.Threading.CancellationToken>の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3913e-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="3913e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3913e-109">See also</span></span>

- [<span data-ttu-id="3913e-110">Thread.Abort は旧型式 - 破壊的変更</span><span class="sxs-lookup"><span data-stu-id="3913e-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="3913e-111">マネージド スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="3913e-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
