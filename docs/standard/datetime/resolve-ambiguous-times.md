---
title: '方法: あいまいな時刻を解決する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 29a549d519bd3b6c10fef8205b30a07a71f01d1a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817758"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="b6c51-102">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="b6c51-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="b6c51-103">あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="b6c51-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="b6c51-104">あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="b6c51-105">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b6c51-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="b6c51-106">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="b6c51-107">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="b6c51-108">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="b6c51-109">このトピックでは、タイムゾーンの標準時刻を表すと想定して、あいまいな時刻を解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="b6c51-110">あいまいな時刻をタイム ゾーンの標準時刻にマップするには</span><span class="sxs-lookup"><span data-stu-id="b6c51-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="b6c51-111">メソッドを呼び出して <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 、時刻があいまいであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="b6c51-112">時刻があいまいな場合は、タイム <xref:System.TimeSpan> ゾーンのプロパティによって返されたオブジェクトから時刻を減算し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="b6c51-113">`static`( `Shared` Visual Basic .net で) メソッドを呼び出して、 <xref:System.DateTime.SpecifyKind%2A> UTC の日付と時刻の値の <xref:System.DateTime.Kind%2A> プロパティをに設定し <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b6c51-114">例</span><span class="sxs-lookup"><span data-stu-id="b6c51-114">Example</span></span>

<span data-ttu-id="b6c51-115">次の例は、ローカルタイムゾーンの標準時刻を表すと想定して、あいまいな時刻を UTC に変換する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b6c51-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="b6c51-116">この例は、渡された `ResolveAmbiguousTime` 値があいまいであるかどうかを判断するという名前のメソッドで構成されてい <xref:System.DateTime> ます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="b6c51-117">値があいまいな場合、メソッドは対応する <xref:System.DateTime> UTC 時刻を表す値を返します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="b6c51-118">メソッドは、ローカルタイムゾーンのプロパティの値をローカル時刻から減算することによって、この変換を処理し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="b6c51-119">通常、あいまいな時刻は、メソッドを呼び出して、 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> あいまいな時刻の UTC オフセットを含むオブジェクトの配列を取得することによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="b6c51-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="b6c51-120">しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b6c51-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="b6c51-121">プロパティは、 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> UTC とタイムゾーンの標準時刻の間のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="b6c51-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="b6c51-122">この例では、ローカルタイムゾーンへのすべての参照は、プロパティを使用して行われ <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ます。ローカルタイムゾーンは、オブジェクト変数に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="b6c51-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="b6c51-123">メソッドを呼び出すと、 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> ローカルタイムゾーンが割り当てられているオブジェクトが無効になるため、この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b6c51-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b6c51-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b6c51-124">Compiling the code</span></span>

<span data-ttu-id="b6c51-125">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b6c51-125">This example requires:</span></span>

- <span data-ttu-id="b6c51-126"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="b6c51-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c51-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6c51-127">See also</span></span>

- [<span data-ttu-id="b6c51-128">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="b6c51-128">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="b6c51-129">方法: ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="b6c51-129">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
