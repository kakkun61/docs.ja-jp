---
title: '方法: 調整規則のないタイム ゾーンを作成する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 411a0c0b581830a45a986216681ca2800a9a4c42
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817992"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="16d65-102">方法: 調整規則のないタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="16d65-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="16d65-103">アプリケーションで必要とされる正確なタイムゾーン情報は、次のような理由で特定のシステムに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="16d65-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="16d65-104">タイムゾーンがローカルシステムのレジストリに定義されていません。</span><span class="sxs-lookup"><span data-stu-id="16d65-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="16d65-105">タイムゾーンに関するデータは、レジストリから変更または削除されています。</span><span class="sxs-lookup"><span data-stu-id="16d65-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="16d65-106">タイムゾーンは存在しますが、特定の履歴期間のタイムゾーン調整に関する正確な情報がありません。</span><span class="sxs-lookup"><span data-stu-id="16d65-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="16d65-107">このような場合は、メソッドを呼び出し <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> て、アプリケーションで必要とされるタイムゾーンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="16d65-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="16d65-108">このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイムゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="16d65-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="16d65-109">タイムゾーンで夏時間がサポートされている場合は、固定調整規則または浮動調整規則のいずれかを使用して調整を定義できます。</span><span class="sxs-lookup"><span data-stu-id="16d65-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="16d65-110">(これらの用語の定義については、「タイムゾーンの [概要](time-zone-overview.md)」の「タイムゾーンの用語」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="16d65-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16d65-111">メソッドを呼び出すことによって作成されたカスタムタイムゾーン <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> は、レジストリには追加されません。</span><span class="sxs-lookup"><span data-stu-id="16d65-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="16d65-112">代わりに、メソッド呼び出しによって返されるオブジェクト参照を使用してのみアクセスでき <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="16d65-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="16d65-113">このトピックでは、調整規則を使用せずにタイムゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="16d65-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="16d65-114">夏時間調整規則をサポートするタイムゾーンを作成するには、「 [方法: 調整規則を使用してタイムゾーンを作成](create-time-zones-with-adjustment-rules.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16d65-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="16d65-115">調整規則のないタイムゾーンを作成するには</span><span class="sxs-lookup"><span data-stu-id="16d65-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="16d65-116">タイムゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="16d65-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="16d65-117">表示名は、標準形式に準拠しています。この形式では、世界協定時刻 (UTC) からのタイムゾーンのオフセットがかっこで囲まれ、タイムゾーンの1つまたは複数の都市を識別する文字列、またはタイムゾーンの1つ以上の国または地域が続きます。</span><span class="sxs-lookup"><span data-stu-id="16d65-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="16d65-118">タイムゾーンの標準時刻の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="16d65-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="16d65-119">通常、この文字列はタイムゾーンの識別子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="16d65-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="16d65-120">タイムゾーンの標準名とは異なる識別子を使用する場合は、タイムゾーン識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="16d65-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="16d65-121"><xref:System.TimeSpan>タイムゾーンの UTC からのオフセットを定義するオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="16d65-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="16d65-122">時刻が UTC より遅いタイムゾーンには、正のオフセットがあります。</span><span class="sxs-lookup"><span data-stu-id="16d65-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="16d65-123">時刻が UTC より前のタイムゾーンでは、負のオフセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="16d65-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="16d65-124">メソッドを呼び出して <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> 、新しいタイムゾーンをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="16d65-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="16d65-125">例</span><span class="sxs-lookup"><span data-stu-id="16d65-125">Example</span></span>

<span data-ttu-id="16d65-126">次の例では、調整規則のない Mawson、南極のカスタムタイムゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="16d65-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="16d65-127">プロパティに割り当てられた文字列は、 <xref:System.TimeZoneInfo.DisplayName%2A> 標準形式に従います。この形式では、UTC からのタイムゾーンのオフセットの後にタイムゾーンのわかりやすい説明が続きます。</span><span class="sxs-lookup"><span data-stu-id="16d65-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="16d65-128">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="16d65-128">Compiling the code</span></span>

<span data-ttu-id="16d65-129">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16d65-129">This example requires:</span></span>

- <span data-ttu-id="16d65-130">次の名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="16d65-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="16d65-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="16d65-131">See also</span></span>

- [<span data-ttu-id="16d65-132">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="16d65-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="16d65-133">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="16d65-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="16d65-134">方法: 調整規則のあるタイムゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="16d65-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
