---
title: SYSLIB0012 警告
description: コンパイル時の警告 SYSLIB0012 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2ed93b6eefbaa861faca319f0cc9bf19ac741f3b
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333073"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="0a93b-103">SYSLIB0012:Assembly.CodeBase と Assembly.EscapedCodeBase は旧型式</span><span class="sxs-lookup"><span data-stu-id="0a93b-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="0a93b-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="0a93b-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0a93b-105">これらをコードで使用すると、コンパイル時に警告 `SYSLIB0012` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a93b-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

<span data-ttu-id="0a93b-106">回避策</span><span class="sxs-lookup"><span data-stu-id="0a93b-106">Workaround</span></span>

<span data-ttu-id="0a93b-107">代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="0a93b-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>
