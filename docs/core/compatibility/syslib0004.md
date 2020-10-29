---
title: SYSLIB0004 警告
description: コンパイル時の警告 SYSLIB0004 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ba7cd8a890a89000b241d286c9d8069ba1398849
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333131"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="eb3a8-103">SYSLIB0004: 制約された実行領域 (CER) 機能はサポートされていません</span><span class="sxs-lookup"><span data-stu-id="eb3a8-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="eb3a8-104">[制約された実行領域 (CER)](../../framework/performance/constrained-execution-regions.md) 機能は、.NET Framework でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eb3a8-104">The [Constrained execution regions (CER)](../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="eb3a8-105">そのため、さまざまな CER 関連 API は、.NET 5.0 以降、古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="eb3a8-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="eb3a8-106">これらの API を使用すると、コンパイル時に警告 `SYSLIB0004` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="eb3a8-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="eb3a8-107">次の CER 関連の API は旧型式です。</span><span class="sxs-lookup"><span data-stu-id="eb3a8-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="eb3a8-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb3a8-108">See also</span></span>

- [<span data-ttu-id="eb3a8-109">制約された実行領域</span><span class="sxs-lookup"><span data-stu-id="eb3a8-109">Constrained execution regions</span></span>](../../framework/performance/constrained-execution-regions.md)
