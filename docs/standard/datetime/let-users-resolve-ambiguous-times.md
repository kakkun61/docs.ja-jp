---
title: '方法: ユーザーがあいまいな時刻を解決できるようにする'
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: d543db20161057764749210533f35f7c2a1ec81d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817797"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="1a744-102">方法: ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="1a744-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="1a744-103">あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="1a744-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="1a744-104">あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="1a744-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="1a744-105">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1a744-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="1a744-106">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="1a744-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="1a744-107">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="1a744-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="1a744-108">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="1a744-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="1a744-109">このトピックでは、ユーザーがあいまいな時刻を解決できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a744-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="1a744-110">ユーザーにあいまいな時刻を解決させるには</span><span class="sxs-lookup"><span data-stu-id="1a744-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="1a744-111">ユーザーによって入力された日付と時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a744-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="1a744-112">メソッドを呼び出して <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 、時刻があいまいであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a744-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="1a744-113">時刻があいまいな場合は、メソッドを呼び出して <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> オブジェクトの配列を取得し <xref:System.TimeSpan> ます。</span><span class="sxs-lookup"><span data-stu-id="1a744-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="1a744-114">配列の各要素には、あいまいな時刻をマップできる UTC オフセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a744-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="1a744-115">ユーザーに目的のオフセットを選択させます。</span><span class="sxs-lookup"><span data-stu-id="1a744-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="1a744-116">ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a744-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="1a744-117">`static`( `Shared` Visual Basic .net で) メソッドを呼び出して、 <xref:System.DateTime.SpecifyKind%2A> UTC の日付と時刻の値の <xref:System.DateTime.Kind%2A> プロパティをに設定し <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="1a744-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="1a744-118">例</span><span class="sxs-lookup"><span data-stu-id="1a744-118">Example</span></span>

<span data-ttu-id="1a744-119">次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。</span><span class="sxs-lookup"><span data-stu-id="1a744-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="1a744-120">この例のコードの中核となるのは、オブジェクトの配列を使用して、 <xref:System.TimeSpan> UTC からのあいまいな時刻のオフセットを示すことです。</span><span class="sxs-lookup"><span data-stu-id="1a744-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="1a744-121">ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a744-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="1a744-122">オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。</span><span class="sxs-lookup"><span data-stu-id="1a744-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="1a744-123">このコードでは、オフセットをプロパティの値と比較することによって、標準の時間と夏時間を判断し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="1a744-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="1a744-124">このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。</span><span class="sxs-lookup"><span data-stu-id="1a744-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="1a744-125">この例では、ローカルタイムゾーンへのすべての参照は、プロパティを使用して行われ <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ます。ローカルタイムゾーンは、オブジェクト変数に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="1a744-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="1a744-126">メソッドを呼び出すと、 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> ローカルタイムゾーンが割り当てられているオブジェクトが無効になるため、この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1a744-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1a744-127">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1a744-127">Compiling the code</span></span>

<span data-ttu-id="1a744-128">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a744-128">This example requires:</span></span>

- <span data-ttu-id="1a744-129"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="1a744-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a744-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a744-130">See also</span></span>

- [<span data-ttu-id="1a744-131">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="1a744-131">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="1a744-132">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="1a744-132">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)
