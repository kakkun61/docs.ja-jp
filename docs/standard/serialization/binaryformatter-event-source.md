---
title: BinaryFormatter イベント ソース
description: シリアル化または逆シリアル化が発生したときに、BinaryFormatter イベント ソースを使用してログを記録する方法について説明します。
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740390"
---
# <a name="binaryformatter-event-source"></a><span data-ttu-id="fa5ff-103">BinaryFormatter イベント ソース</span><span class="sxs-lookup"><span data-stu-id="fa5ff-103">BinaryFormatter event source</span></span>

<span data-ttu-id="fa5ff-104">.NET 5.0 以降、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> には、オブジェクトのシリアル化または逆シリアル化が発生したタイミングを可視化できる、組み込みの <xref:System.Diagnostics.Tracing.EventSource> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-104">Starting with .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> includes a built-in <xref:System.Diagnostics.Tracing.EventSource> that gives you visibility into when an object serialization or deserialization is occurring.</span></span> <span data-ttu-id="fa5ff-105">アプリでは、<xref:System.Diagnostics.Tracing.EventListener> から派生した型を使用してこれらの通知をリッスンし、ログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-105">Apps can use <xref:System.Diagnostics.Tracing.EventListener>-derived types to listen for these notifications and log them.</span></span>

<span data-ttu-id="fa5ff-106">この機能は <xref:System.Runtime.Serialization.SerializationBinder> または <xref:System.Runtime.Serialization.ISerializationSurrogate> に代わるものではなく、シリアル化または逆シリアル化されるデータを変更するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-106">This functionality is not a substitute for a <xref:System.Runtime.Serialization.SerializationBinder> or an <xref:System.Runtime.Serialization.ISerializationSurrogate> and can't be used to modify the data being serialized or deserialized.</span></span> <span data-ttu-id="fa5ff-107">むしろ、このイベント システムは、シリアル化または逆シリアル化される型についての分析情報を提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-107">Rather, this eventing system is intended to provide insight into the types being serialized or deserialized.</span></span> <span data-ttu-id="fa5ff-108">また、`BinaryFormatter` インフラストラクチャへの意図しない呼び出し (サード パーティ製のライブラリ コードからの呼び出しなど) を検出するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-108">It can also be used to detect unintended calls into the `BinaryFormatter` infrastructure, such as calls originating from third-party library code.</span></span>

## <a name="description-of-events"></a><span data-ttu-id="fa5ff-109">イベントの説明</span><span class="sxs-lookup"><span data-stu-id="fa5ff-109">Description of events</span></span>

<span data-ttu-id="fa5ff-110">`BinaryFormatter` イベント ソースには、`System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` という既知の名前があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-110">The `BinaryFormatter` event source has the well-known name `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span></span> <span data-ttu-id="fa5ff-111">リスナーは 6 つのイベントをサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-111">Listeners may subscribe to 6 events.</span></span>

### <a name="serializationstart-event-id--10"></a><span data-ttu-id="fa5ff-112">SerializationStart イベント (id = `10`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-112">SerializationStart event (id = `10`)</span></span>

<span data-ttu-id="fa5ff-113"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> が呼び出され、シリアル化プロセスが開始されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-113">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> has been called and has started the serialization process.</span></span> <span data-ttu-id="fa5ff-114">このイベントは、`SerializationEnd` イベントとペアになります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-114">This event is paired with the `SerializationEnd` event.</span></span> <span data-ttu-id="fa5ff-115">`SerializationStart` イベントは、オブジェクトがそれ自体のシリアル化ルーチン内で `BinaryFormatter.Serialize` を呼び出す場合、再帰的に呼び出される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-115">The `SerializationStart` event can be called recursively if an object calls `BinaryFormatter.Serialize` within its own serialization routine.</span></span>

<span data-ttu-id="fa5ff-116">このイベントにはペイロードが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-116">This event doesn't contain a payload.</span></span>

### <a name="serializationend-event-id--11"></a><span data-ttu-id="fa5ff-117">SerializationEnd イベント (id = `11`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-117">SerializationEnd event (id = `11`)</span></span>

<span data-ttu-id="fa5ff-118">`BinaryFormatter.Serialize` の処理が完了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-118">Raised when `BinaryFormatter.Serialize` has completed its work.</span></span> <span data-ttu-id="fa5ff-119">`SerializationEnd` が発生するたびに、最後のペアになっていない `SerializationStart` イベントが完了したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-119">Each occurrence of `SerializationEnd` denotes the completion of the last unpaired `SerializationStart` event.</span></span>

<span data-ttu-id="fa5ff-120">このイベントにはペイロードが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-120">This event doesn't contain a payload.</span></span>

### <a name="serializingobject-event-id--12"></a><span data-ttu-id="fa5ff-121">SerializingObject イベント (id = `12`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-121">SerializingObject event (id = `12`)</span></span>

<span data-ttu-id="fa5ff-122">`BinaryFormatter.Serialize` によって非プリミティブ型をシリアル化する処理が行われているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-122">Raised when `BinaryFormatter.Serialize` is in the process of serializing a non-primitive type.</span></span> <span data-ttu-id="fa5ff-123">`BinaryFormatter` インフラストラクチャでは特定の型 (`string` や `int` など) が特別なケースとして処理され、これらの型が検出されてもこのイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-123">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="fa5ff-124">このイベントは、ユーザー定義型、および `BinaryFormatter` によってネイティブに認識されないその他の型に対して発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-124">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="fa5ff-125">このイベントは、`SerializationStart` イベントと `SerializationEnd` イベントの間で 0 回以上発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-125">This event may be raised zero or more times between `SerializationStart` and `SerializationEnd` events.</span></span>

<span data-ttu-id="fa5ff-126">このイベントには、1 つの引数を持つペイロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-126">This event contains a payload with one argument:</span></span>

* <span data-ttu-id="fa5ff-127">`typeName` (`string`):シリアル化される型のアセンブリ修飾名 (<xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> を参照)。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-127">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being serialized.</span></span>

### <a name="deserializationstart-event-id--20"></a><span data-ttu-id="fa5ff-128">DeserializationStart イベント (id = `20`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-128">DeserializationStart event (id = `20`)</span></span>

<span data-ttu-id="fa5ff-129"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> が呼び出され、逆シリアル化プロセスが開始されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-129">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> has been called and has started the deserialization process.</span></span> <span data-ttu-id="fa5ff-130">このイベントは、`DeserializationEnd` イベントとペアになります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-130">This event is paired with the `DeserializationEnd` event.</span></span> <span data-ttu-id="fa5ff-131">`DeserializationStart` イベントは、オブジェクトがそれ自体の逆シリアル化ルーチン内で `BinaryFormatter.Deserialize` を呼び出す場合、再帰的に呼び出される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-131">The `DeserializationStart` event can be called recursively if an object calls `BinaryFormatter.Deserialize` within its own deserialization routine.</span></span>

<span data-ttu-id="fa5ff-132">このイベントにはペイロードが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-132">This event doesn't contain a payload.</span></span>

### <a name="deserializationend-event-id--21"></a><span data-ttu-id="fa5ff-133">DeserializationEnd イベント (id = `21`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-133">DeserializationEnd event (id = `21`)</span></span>

<span data-ttu-id="fa5ff-134">`BinaryFormatter.Deserialize` の処理が完了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-134">Raised when `BinaryFormatter.Deserialize` has completed its work.</span></span> <span data-ttu-id="fa5ff-135">`DeserializationEnd` が発生するたびに、最後のペアになっていない `DeserializationStart` イベントが完了したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-135">Each occurrence of `DeserializationEnd` denotes the completion of the last unpaired `DeserializationStart` event.</span></span>

<span data-ttu-id="fa5ff-136">このイベントにはペイロードが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-136">This event doesn't contain a payload.</span></span>

### <a name="deserializingobject-event-id--22"></a><span data-ttu-id="fa5ff-137">DeserializingObject イベント (id = `22`)</span><span class="sxs-lookup"><span data-stu-id="fa5ff-137">DeserializingObject event (id = `22`)</span></span>

<span data-ttu-id="fa5ff-138">`BinaryFormatter.Deserialize` によって非プリミティブ型を逆シリアル化する処理が行われているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-138">Raised when `BinaryFormatter.Deserialize` is in the process of deserializing a non-primitive type.</span></span> <span data-ttu-id="fa5ff-139">`BinaryFormatter` インフラストラクチャでは特定の型 (`string` や `int` など) が特別なケースとして処理され、これらの型が検出されてもこのイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-139">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="fa5ff-140">このイベントは、ユーザー定義型、および `BinaryFormatter` によってネイティブに認識されないその他の型に対して発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-140">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="fa5ff-141">このイベントは、`DeserializationStart` イベントと `DeserializationEnd` イベントの間で 0 回以上発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-141">This event may be raised zero or more times between `DeserializationStart` and `DeserializationEnd` events.</span></span>

<span data-ttu-id="fa5ff-142">このイベントには、1 つの引数を持つペイロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-142">This event contains a payload with one argument.</span></span>

* <span data-ttu-id="fa5ff-143">`typeName` (`string`):逆シリアル化される型のアセンブリ修飾名 (<xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> を参照)。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-143">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being deserialized.</span></span>

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a><span data-ttu-id="fa5ff-144">\[高度な設定\] 通知のサブセットをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="fa5ff-144">\[Advanced\] Subscribing to a subset of notifications</span></span>

<span data-ttu-id="fa5ff-145">通知のサブセットのみをサブスクライブする必要があるリスナーでは、有効にするキーワードを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-145">Listeners who wish to subscribe to only a subset of notifications can choose which keywords to enable.</span></span>

* <span data-ttu-id="fa5ff-146">`Serialization` = `(EventKeywords)1`:`SerializationStart`、`SerializationEnd`、および `SerializingObject` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-146">`Serialization` = `(EventKeywords)1`: Raises the `SerializationStart`, `SerializationEnd`, and `SerializingObject` events.</span></span>
* <span data-ttu-id="fa5ff-147">`Deserialization` = `(EventKeywords)2`:`DeserializationStart`、`DeserializationEnd`、および `DeserializingObject` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-147">`Deserialization` = `(EventKeywords)2`: Raises the `DeserializationStart`, `DeserializationEnd`, and `DeserializingObject` events.</span></span>

<span data-ttu-id="fa5ff-148">`EventListener` の登録時にキーワード フィルターが指定されていない場合は、すべてのイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-148">If no keyword filters are provided during `EventListener` registration, all events are raised.</span></span>

<span data-ttu-id="fa5ff-149">詳細については、「<xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-149">For more information, see <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span></span>

## <a name="sample-code"></a><span data-ttu-id="fa5ff-150">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="fa5ff-150">Sample code</span></span>

<span data-ttu-id="fa5ff-151">コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-151">The following code:</span></span>

- <span data-ttu-id="fa5ff-152">`System.Console` に書き込む `EventListener` から派生した型を作成します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-152">creates an `EventListener`-derived type that writes to `System.Console`,</span></span>
- <span data-ttu-id="fa5ff-153">そのリスナーを `BinaryFormatter` によって生成された通知にサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-153">subscribes that listener to `BinaryFormatter`-produced notifications,</span></span>
- <span data-ttu-id="fa5ff-154">`BinaryFormatter` を使用してシンプルなオブジェクト グラフをシリアル化および逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-154">serializes and deserializes a simple object graph using `BinaryFormatter`, and</span></span>
- <span data-ttu-id="fa5ff-155">発生したイベントを分析します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-155">analyzes the events that have been raised.</span></span>

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

<span data-ttu-id="fa5ff-156">上記のコードにより、次の例のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-156">The preceding code produces output similar to the following example:</span></span>

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

<span data-ttu-id="fa5ff-157">このサンプルでは、コンソール ベースの `EventListener` によって、シリアル化が開始され、`Person` と `Book` のインスタンスがシリアル化された後、シリアル化が完了することがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-157">In this sample, the console-based `EventListener` logs that serialization starts, instances of `Person` and `Book` are serialized, and then serialization completes.</span></span> <span data-ttu-id="fa5ff-158">同様に、逆シリアル化が開始されると、`Person` と `Book` のインスタンスが逆シリアル化された後、逆シリアル化が完了します。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-158">Similarly, once deserialization has started, instances of `Person` and `Book` are deserialized, and then deserialization completes.</span></span>

<span data-ttu-id="fa5ff-159">アプリでは次に、逆シリアル化された `Person` に含まれている値が出力され、オブジェクトが実際にシリアル化および逆シリアル化されたことが示されます。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-159">The app then prints the values contained in the deserialized `Person` to demonstrate that the object did in fact serialize and deserialize properly.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa5ff-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa5ff-160">See also</span></span>

<span data-ttu-id="fa5ff-161">`EventListener` を使用して `EventSource` ベースの通知を受信する方法の詳細については、[`EventListener` クラス](xref:System.Diagnostics.Tracing.EventListener)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa5ff-161">For more information on using `EventListener` to receive `EventSource`-based notifications, see [the `EventListener` class](xref:System.Diagnostics.Tracing.EventListener).</span></span>
