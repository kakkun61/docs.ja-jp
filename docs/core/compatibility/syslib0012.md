---
title: SYSLIB0012 警告
description: コンパイル時の警告 SYSLIB0012 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dc139d5c5cb6d6a34d161147b350b3324d15117e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440583"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="06353-103">SYSLIB0012:Assembly.CodeBase と Assembly.EscapedCodeBase は旧型式</span><span class="sxs-lookup"><span data-stu-id="06353-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="06353-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="06353-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="06353-105">これらをコードで使用すると、コンパイル時に警告 `SYSLIB0012` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="06353-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="06353-106">回避策</span><span class="sxs-lookup"><span data-stu-id="06353-106">Workarounds</span></span>

<span data-ttu-id="06353-107">代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="06353-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
