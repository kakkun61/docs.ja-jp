---
title: プロパティのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: ed287b98c012622caa5f8f1cc90fced90dda3e62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730969"
---
# <a name="property-design"></a><span data-ttu-id="515aa-102">プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="515aa-102">Property Design</span></span>

<span data-ttu-id="515aa-103">プロパティは技術的にはメソッドとよく似ていますが、使用シナリオの観点からは非常に異なります。</span><span class="sxs-lookup"><span data-stu-id="515aa-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="515aa-104">スマートフィールドとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="515aa-104">They should be seen as smart fields.</span></span> <span data-ttu-id="515aa-105">これらのメソッドには、フィールドの呼び出し構文とメソッドの柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="515aa-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>

 <span data-ttu-id="515aa-106">呼び出し元がプロパティの値を変更できない場合は、get 専用プロパティを作成✔️ます。</span><span class="sxs-lookup"><span data-stu-id="515aa-106">✔️ DO create get-only properties if the caller should not be able to change the value of the property.</span></span>

 <span data-ttu-id="515aa-107">プロパティの型が変更可能な参照型である場合は、プロパティが get 専用であってもプロパティ値を変更できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="515aa-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>

 <span data-ttu-id="515aa-108">❌ Set 専用のプロパティまたはプロパティを指定しないでください。 setter を使用するよりもアクセシビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="515aa-108">❌ DO NOT provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>

 <span data-ttu-id="515aa-109">たとえば、public setter および protected getter を持つプロパティは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="515aa-109">For example, do not use properties with a public setter and a protected getter.</span></span>

 <span data-ttu-id="515aa-110">プロパティ getter を指定できない場合は、代わりにメソッドとして機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="515aa-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="515aa-111">でメソッド名を開始し、プロパティとして指定した内容に従うことを検討してください `Set` 。</span><span class="sxs-lookup"><span data-stu-id="515aa-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="515aa-112">たとえば、に <xref:System.AppDomain> は、 `SetCachePath` という名前のセットのみのプロパティを使用する代わりに、というメソッドが呼び出され `CachePath` ます。</span><span class="sxs-lookup"><span data-stu-id="515aa-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>

 <span data-ttu-id="515aa-113">✔️は、すべてのプロパティに対して適切な既定値を提供します。既定では、セキュリティホールや非常に非効率的なコードにはなりません。</span><span class="sxs-lookup"><span data-stu-id="515aa-113">✔️ DO provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>

 <span data-ttu-id="515aa-114">✔️、オブジェクトが一時的に無効な状態になる場合でも、プロパティを任意の順序で設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="515aa-114">✔️ DO allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>

 <span data-ttu-id="515aa-115">同じオブジェクトの他のプロパティの値を指定すると、1つのプロパティの値が無効になる可能性がある点に対して、2つ以上のプロパティが相互に関連付けられることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="515aa-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="515aa-116">このような場合は、相互に関連するプロパティがオブジェクトによって実際に使用されるまで、無効な状態に起因する例外を延期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="515aa-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>

 <span data-ttu-id="515aa-117">プロパティ setter が例外をスローした場合は、前の値を保持✔️。</span><span class="sxs-lookup"><span data-stu-id="515aa-117">✔️ DO preserve the previous value if a property setter throws an exception.</span></span>

 <span data-ttu-id="515aa-118">❌ プロパティの getter から例外をスローしないようにします。</span><span class="sxs-lookup"><span data-stu-id="515aa-118">❌ AVOID throwing exceptions from property getters.</span></span>

 <span data-ttu-id="515aa-119">プロパティの getter は単純な操作である必要があり、事前条件を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="515aa-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="515aa-120">Getter が例外をスローする場合は、メソッドとして再設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="515aa-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="515aa-121">この規則はインデクサーには適用されませんが、引数を検証した結果として例外が発生することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="515aa-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>

### <a name="indexed-property-design"></a><span data-ttu-id="515aa-122">インデックス付きプロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="515aa-122">Indexed Property Design</span></span>

 <span data-ttu-id="515aa-123">インデックス付きプロパティは、パラメーターを持つことができる特殊なプロパティであり、配列のインデックス作成に似た特殊な構文を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="515aa-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>

 <span data-ttu-id="515aa-124">インデックス付きプロパティは、通常、インデクサーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="515aa-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="515aa-125">インデクサーは、論理コレクション内の項目へのアクセスを提供する Api でのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="515aa-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="515aa-126">たとえば、文字列は文字のコレクションであり、のインデクサーが <xref:System.String?displayProperty=nameWithType> その文字にアクセスするために追加されています。</span><span class="sxs-lookup"><span data-stu-id="515aa-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>

 <span data-ttu-id="515aa-127">インデクサーを使用して、内部配列に格納されているデータにアクセスできるようにする✔️ます。</span><span class="sxs-lookup"><span data-stu-id="515aa-127">✔️ CONSIDER using indexers to provide access to data stored in an internal array.</span></span>

 <span data-ttu-id="515aa-128">✔️項目のコレクションを表す型にインデクサーを指定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="515aa-128">✔️ CONSIDER providing indexers on types representing collections of items.</span></span>

 <span data-ttu-id="515aa-129">❌ 複数のパラメーターでインデックス付きプロパティを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="515aa-129">❌ AVOID using indexed properties with more than one parameter.</span></span>

 <span data-ttu-id="515aa-130">設計に複数のパラメーターが必要な場合は、プロパティが論理コレクションへのアクセサーを実際に表しているかどうかを再検討します。</span><span class="sxs-lookup"><span data-stu-id="515aa-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="515aa-131">そうでない場合は、代わりにメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="515aa-131">If it does not, use methods instead.</span></span> <span data-ttu-id="515aa-132">またはを使用してメソッド名を開始することを検討してください `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="515aa-132">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="515aa-133">❌<xref:System.Int32?displayProperty=nameWithType>、、 <xref:System.Int64?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType> 、 <xref:System.Object?displayProperty=nameWithType> 、または列挙型以外のパラメーター型を持つインデクサーは避けてください。</span><span class="sxs-lookup"><span data-stu-id="515aa-133">❌ AVOID indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>

 <span data-ttu-id="515aa-134">設計に他の種類のパラメーターが必要な場合は、API が論理コレクションへのアクセサーを実際に表しているかどうかを厳密に再評価します。</span><span class="sxs-lookup"><span data-stu-id="515aa-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="515aa-135">そうでない場合は、メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="515aa-135">If it does not, use a method.</span></span> <span data-ttu-id="515aa-136">またはを使用してメソッド名を開始することを検討してください `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="515aa-136">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="515aa-137">`Item`明らかにわかりやすい名前 (たとえば、のプロパティを参照) がない場合は、インデックス付きプロパティの名前を使用✔️ <xref:System.String.Chars%2A> `System.String` ます。</span><span class="sxs-lookup"><span data-stu-id="515aa-137">✔️ DO use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>

 <span data-ttu-id="515aa-138">C# では、インデクサーは既定で Item という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="515aa-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="515aa-139">を使用すると、 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> この名前をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="515aa-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>

 <span data-ttu-id="515aa-140">❌ 同じ意味を持つインデクサーとメソッドの両方を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="515aa-140">❌ DO NOT provide both an indexer and methods that are semantically equivalent.</span></span>

 <span data-ttu-id="515aa-141">❌ 1つの型でオーバーロードされたインデクサーのファミリを複数指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="515aa-141">❌ DO NOT provide more than one family of overloaded indexers in one type.</span></span>

 <span data-ttu-id="515aa-142">これは、C# コンパイラによって適用されます。</span><span class="sxs-lookup"><span data-stu-id="515aa-142">This is enforced by the C# compiler.</span></span>

 <span data-ttu-id="515aa-143">❌ 既定以外のインデックス付きプロパティは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="515aa-143">❌ DO NOT use nondefault indexed properties.</span></span>

 <span data-ttu-id="515aa-144">これは、C# コンパイラによって適用されます。</span><span class="sxs-lookup"><span data-stu-id="515aa-144">This is enforced by the C# compiler.</span></span>

### <a name="property-change-notification-events"></a><span data-ttu-id="515aa-145">プロパティ変更通知イベント</span><span class="sxs-lookup"><span data-stu-id="515aa-145">Property Change Notification Events</span></span>

 <span data-ttu-id="515aa-146">場合によっては、プロパティ値の変更をユーザーに通知するイベントを提供すると便利です。</span><span class="sxs-lookup"><span data-stu-id="515aa-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="515aa-147">たとえば、は、 `System.Windows.Forms.Control` `TextChanged` プロパティの値が変更された後にイベントを発生 `Text` させます。</span><span class="sxs-lookup"><span data-stu-id="515aa-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>

 <span data-ttu-id="515aa-148">高レベルの Api (通常はデザイナーコンポーネント) のプロパティ値が変更された場合に、変更通知イベントを発生させる✔️を検討してください。</span><span class="sxs-lookup"><span data-stu-id="515aa-148">✔️ CONSIDER raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>

 <span data-ttu-id="515aa-149">オブジェクトのプロパティが変更されたことをユーザーが知るための適切なシナリオがある場合、オブジェクトはプロパティの変更通知イベントを発生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="515aa-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>

 <span data-ttu-id="515aa-150">ただし、基本型やコレクションなどの低レベルの Api に対して、このようなイベントを発生させるオーバーヘッドがあることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="515aa-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="515aa-151">たとえば、は、 <xref:System.Collections.Generic.List%601> 新しい項目がリストに追加され、プロパティが変更された場合に、このようなイベントを発生させません `Count` 。</span><span class="sxs-lookup"><span data-stu-id="515aa-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>

 <span data-ttu-id="515aa-152">プロパティの値が外部の強制によって変更された場合に、変更通知イベントを発生させることを✔️します。</span><span class="sxs-lookup"><span data-stu-id="515aa-152">✔️ CONSIDER raising change notification events when the value of a property changes via external forces.</span></span>

 <span data-ttu-id="515aa-153">プロパティ値が何らかの外部強制 (オブジェクトのメソッドを呼び出す以外の方法で) によって変更された場合、イベントの発生は、値が変更され、変更されたことを開発者に示します。</span><span class="sxs-lookup"><span data-stu-id="515aa-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="515aa-154">たとえば、 `Text` テキストボックスコントロールのプロパティを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="515aa-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="515aa-155">ユーザーがでテキストを入力すると、 `TextBox` プロパティ値が自動的に変更されます。</span><span class="sxs-lookup"><span data-stu-id="515aa-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>

 <span data-ttu-id="515aa-156">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="515aa-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="515aa-157">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="515aa-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="515aa-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="515aa-158">See also</span></span>

- [<span data-ttu-id="515aa-159">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="515aa-159">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="515aa-160">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="515aa-160">Framework Design Guidelines</span></span>](index.md)
