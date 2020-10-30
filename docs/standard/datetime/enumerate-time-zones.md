---
title: '方法: コンピューター上に存在するタイム ゾーンを列挙する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: a51e9d0c51968d57e0d79dd80d8619ab11cdbf93
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063769"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="2ea19-102">方法: コンピューター上に存在するタイム ゾーンを列挙する</span><span class="sxs-lookup"><span data-stu-id="2ea19-102">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="2ea19-103">指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea19-103">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="2ea19-104">Windows XP および Windows Vista オペレーティングシステムでは、この情報はレジストリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-104">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="2ea19-105">しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。</span><span class="sxs-lookup"><span data-stu-id="2ea19-105">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="2ea19-106">さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="2ea19-106">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="2ea19-107">その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。</span><span class="sxs-lookup"><span data-stu-id="2ea19-107">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="2ea19-108">タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。</span><span class="sxs-lookup"><span data-stu-id="2ea19-108">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="2ea19-109">これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea19-109">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="2ea19-110">アプリケーションが、ローカルシステムで定義されていない特定のタイムゾーンの存在に依存している場合は、タイムゾーンに関する情報をシリアル化および逆シリアル化することによって、アプリケーションの存在を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-110">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="2ea19-111">タイムゾーンは、アプリケーションユーザーが選択できるように、リストコントロールに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-111">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="2ea19-112">詳細については、「 [方法: 埋め込みリソースにタイムゾーンを保存](save-time-zones-to-an-embedded-resource.md) する」および「 [方法: 埋め込みリソースからタイムゾーンを復元](restore-time-zones-from-an-embedded-resource.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea19-112">For details, see [How to: Save Time Zones to an Embedded Resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="2ea19-113">ローカル システムに存在するタイム ゾーンを列挙するには</span><span class="sxs-lookup"><span data-stu-id="2ea19-113">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="2ea19-114"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-114">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2ea19-115">メソッドは、 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> オブジェクトのジェネリックコレクションを返し <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-115">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="2ea19-116">コレクション内のエントリは、プロパティによって並べ替えられ <xref:System.TimeZoneInfo.DisplayName%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-116">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="2ea19-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-117">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="2ea19-118"><xref:System.TimeZoneInfo> `foreach` ループ (C# の場合) または... を使用して、コレクション内の個々のオブジェクトを列挙します。 `For Each``Next`</span><span class="sxs-lookup"><span data-stu-id="2ea19-118">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="2ea19-119">ループ (Visual Basic) を実行し、各オブジェクトに対して必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-119">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="2ea19-120">たとえば、次のコードは、 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> 手順1で返されたオブジェクトのコレクションを列挙し、各タイムゾーンの表示名をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-120">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="2ea19-121">ローカルシステム上に存在するタイムゾーンの一覧をユーザーに表示するには</span><span class="sxs-lookup"><span data-stu-id="2ea19-121">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="2ea19-122"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-122">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2ea19-123">メソッドは、 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> オブジェクトのジェネリックコレクションを返し <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-123">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="2ea19-124">手順 1. で返されたコレクションを、 `DataSource` Windows フォームまたは ASP.NET list コントロールのプロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-124">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="2ea19-125"><xref:System.TimeZoneInfo>ユーザーが選択したオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-125">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="2ea19-126">この例は、Windows アプリケーションの図解を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ea19-126">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="2ea19-127">例</span><span class="sxs-lookup"><span data-stu-id="2ea19-127">Example</span></span>

<span data-ttu-id="2ea19-128">この例では、システムで定義されているタイムゾーンをリストボックスに表示する Windows アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-128">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="2ea19-129">この例では、 <xref:System.TimeZoneInfo.DisplayName%2A> ユーザーによって選択されたタイムゾーンオブジェクトのプロパティの値を含むダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-129">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="2ea19-130">ほとんどのリストコントロール (やコントロールなど) を使用すると、 <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> `DataSource` そのコレクションがインターフェイスを実装している限り、オブジェクト変数のコレクションをそのプロパティに割り当てることができ <xref:System.Collections.IEnumerable> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-130">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="2ea19-131">(ジェネリッククラスはこれを行い <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> ます)。コレクション内の個々のオブジェクトを表示するために、コントロールはそのオブジェクトのメソッドを呼び出して、 `ToString` オブジェクトを表すために使用される文字列を抽出します。</span><span class="sxs-lookup"><span data-stu-id="2ea19-131">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="2ea19-132">オブジェクトの場合 <xref:System.TimeZoneInfo> 、 `ToString` メソッドは <xref:System.TimeZoneInfo> オブジェクトの表示名 (プロパティの値) を返し <xref:System.TimeZoneInfo.DisplayName%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-132">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="2ea19-133">リストコントロールはオブジェクトのメソッドを呼び出すため、オブジェクト `ToString` のコレクションを <xref:System.TimeZoneInfo> コントロールに割り当て、各オブジェクトに対してわかりやすい名前をコントロールに表示し、ユーザーが選択したオブジェクトを取得することができ <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-133">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="2ea19-134">これにより、コレクション内の各オブジェクトに対して文字列を抽出し、その文字列をコントロールのプロパティに割り当てられているコレクションに割り当て、 `DataSource` ユーザーが選択した文字列を取得して、この文字列を使用して記述されたオブジェクトを抽出する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="2ea19-134">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2ea19-135">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2ea19-135">Compiling the code</span></span>

<span data-ttu-id="2ea19-136">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2ea19-136">This example requires:</span></span>

- <span data-ttu-id="2ea19-137">次の名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="2ea19-137">That the following namespaces be imported:</span></span>

  <span data-ttu-id="2ea19-138"><xref:System> (C# コードの場合)</span><span class="sxs-lookup"><span data-stu-id="2ea19-138"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="2ea19-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ea19-139">See also</span></span>

- [<span data-ttu-id="2ea19-140">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="2ea19-140">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="2ea19-141">方法: 埋め込みリソースにタイムゾーンを保存する</span><span class="sxs-lookup"><span data-stu-id="2ea19-141">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
- [<span data-ttu-id="2ea19-142">方法: 埋め込みリソースからタイムゾーンを復元する</span><span class="sxs-lookup"><span data-stu-id="2ea19-142">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)
