---
title: SYSLIB0010 警告
description: コンパイル時の警告 SYSLIB0010 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333075"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="460df-103">SYSLIB0010:サポートされていないリモート処理 API</span><span class="sxs-lookup"><span data-stu-id="460df-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="460df-104">[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))は従来のテクノロジであり、インフラストラクチャは .NET Framework にのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="460df-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="460df-105">.NET 5.0 以降、次のリモート処理関連の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="460df-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="460df-106">これらをコードで使用すると、コンパイル時に警告 `SYSLIB0010` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="460df-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="460df-107">回避策</span><span class="sxs-lookup"><span data-stu-id="460df-107">Workaround</span></span>

<span data-ttu-id="460df-108">他のアプリケーションの、または複数のコンピューターのオブジェクトと通信する場合は、WCF または HTTP ベースの REST サービスの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="460df-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="460df-109">詳細については、[.NET Core で使用できない .NET Framework テクノロジ](../porting/net-framework-tech-unavailable.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="460df-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="460df-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="460df-110">See also</span></span>

- <span data-ttu-id="460df-111">[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="460df-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
