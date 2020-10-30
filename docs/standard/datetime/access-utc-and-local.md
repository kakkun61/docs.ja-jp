---
title: '方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 598cd631fab1ddc115bc6153580351b1dc14d5bf
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063886"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="cdc42-102">方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="cdc42-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="cdc42-103"><xref:System.TimeZoneInfo>クラスには、とという2つのプロパティが用意されており、これにより、 <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> 定義済みのタイムゾーンオブジェクトにコードからアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="cdc42-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="cdc42-104">このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cdc42-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="cdc42-105">世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="cdc42-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="cdc42-106">`static`( `Shared` Visual Basic) プロパティを使用して、 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 協定世界時にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cdc42-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="cdc42-107"><xref:System.TimeZoneInfo>プロパティによって返されたオブジェクトをオブジェクト変数に割り当てるのではなく、プロパティを使用して世界協定時刻にアクセスし続け <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="cdc42-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="cdc42-108">ローカル タイム ゾーンにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="cdc42-108">To access the local time zone</span></span>

1. <span data-ttu-id="cdc42-109">`static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ローカルシステムのタイムゾーンにアクセスするには、(Visual Basic) プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdc42-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="cdc42-110"><xref:System.TimeZoneInfo>プロパティによって返されたオブジェクトをオブジェクト変数に割り当てるのではなく、引き続きプロパティを使用してローカルタイムゾーンにアクセスし <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="cdc42-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="cdc42-111">例</span><span class="sxs-lookup"><span data-stu-id="cdc42-111">Example</span></span>

<span data-ttu-id="cdc42-112">次のコードでは、 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティとプロパティを使用し <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> て、米国およびカナダ東部標準時のタイムゾーンから時刻を変換し、タイムゾーン名をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="cdc42-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="cdc42-113">ローカルタイムゾーンは、 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ローカルタイムゾーンをオブジェクト変数に割り当てるのではなく、常にプロパティを使用してアクセスする必要があり <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="cdc42-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="cdc42-114">同様に、 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC ゾーンをオブジェクト変数に割り当てるのではなく、常にプロパティを使用して世界協定時刻にアクセスする必要があり <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="cdc42-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="cdc42-115">これにより、 <xref:System.TimeZoneInfo> メソッドの呼び出しによってオブジェクト変数が無効になるのを防ぐことができ <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="cdc42-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="cdc42-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cdc42-116">Compiling the code</span></span>

<span data-ttu-id="cdc42-117">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cdc42-117">This example requires:</span></span>

- <span data-ttu-id="cdc42-118"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="cdc42-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="cdc42-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdc42-119">See also</span></span>

- [<span data-ttu-id="cdc42-120">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="cdc42-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="cdc42-121">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="cdc42-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="cdc42-122">方法: TimeZoneInfo オブジェクトをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="cdc42-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
