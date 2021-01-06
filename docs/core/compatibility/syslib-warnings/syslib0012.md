---
title: SYSLIB0012 警告
description: コンパイル時の警告 SYSLIB0012 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596300"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="0c85f-103">SYSLIB0012:Assembly.CodeBase と Assembly.EscapedCodeBase は旧型式</span><span class="sxs-lookup"><span data-stu-id="0c85f-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="0c85f-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="0c85f-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0c85f-105">これらをコードで使用すると、コンパイル時に警告 `SYSLIB0012` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c85f-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="0c85f-106">回避策</span><span class="sxs-lookup"><span data-stu-id="0c85f-106">Workarounds</span></span>

<span data-ttu-id="0c85f-107">代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="0c85f-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
