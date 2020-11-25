---
title: クラス、構造体、およびインターフェイスの名前
description: .NET ライブラリを拡張および操作するライブラリを設計するためのガイドラインの一部として、クラス、構造体、およびインターフェイスの名前付けについては、これらのガイドラインを使用します。
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 49bafda0d5c362fa02313c5304436069d054cfd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706516"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="18e28-103">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="18e28-103">Names of Classes, Structs, and Interfaces</span></span>

<span data-ttu-id="18e28-104">次に示す名前付けのガイドラインは、一般的な型の名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="18e28-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="18e28-105">✔️は、文字の大文字と小文字の区別を使用して、名詞または名詞句でクラスと構造体に名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="18e28-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="18e28-106">これにより、動詞句を使用して名前が付けられたメソッドの型名が区別されます。</span><span class="sxs-lookup"><span data-stu-id="18e28-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="18e28-107">✔️には、形容詞のフレーズを使用するか、名詞や名詞句を使用することもあります。</span><span class="sxs-lookup"><span data-stu-id="18e28-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="18e28-108">名詞と名詞句を使用することはほとんどなく、型がインターフェイスではなく抽象クラスであることを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18e28-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="18e28-109">❌ クラス名にプレフィックス (例: "C") を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="18e28-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="18e28-110">✔️派生クラスの名前を基底クラスの名前で終了することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="18e28-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="18e28-111">これは非常に読みやすく、リレーションシップについて明確に説明しています。</span><span class="sxs-lookup"><span data-stu-id="18e28-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="18e28-112">コードでのこの例としては、の一種であるがあり `ArgumentOutOfRangeException` `Exception` `SerializableAttribute` `Attribute` ます。これは、の一種です。</span><span class="sxs-lookup"><span data-stu-id="18e28-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="18e28-113">ただし、このガイドラインを適用するには、適切な判断を使用することが重要です。たとえば、クラスは `Button` イベントの一種であり、 `Control` `Control` 名前には表示されません。</span><span class="sxs-lookup"><span data-stu-id="18e28-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="18e28-114">型がインターフェイスであることを示すには、インターフェイス名の前に I という文字を付ける✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="18e28-115">たとえば、 `IComponent` (わかりやすい名詞)、 `ICustomAttributeProvider` (名詞句)、 `IPersistable` (形容詞) は、適切なインターフェイス名です。</span><span class="sxs-lookup"><span data-stu-id="18e28-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="18e28-116">他の型名と同様に、省略形を避けます。</span><span class="sxs-lookup"><span data-stu-id="18e28-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="18e28-117">クラスがインターフェイスの標準実装であるクラスインターフェイスのペアを定義する場合は、名前がインターフェイス名の "I" プレフィックスによってのみ異なることを✔️してください。</span><span class="sxs-lookup"><span data-stu-id="18e28-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="18e28-118">ジェネリック型パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="18e28-118">Names of Generic Type Parameters</span></span>

 <span data-ttu-id="18e28-119">ジェネリックが .NET Framework 2.0 に追加されました。</span><span class="sxs-lookup"><span data-stu-id="18e28-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="18e28-120">この機能では、 *型パラメーター* と呼ばれる新しい種類の識別子が導入されました。</span><span class="sxs-lookup"><span data-stu-id="18e28-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="18e28-121">1文字の名前が完全に記述されており、わかりやすい名前で値が追加されない場合を除き、ジェネリック型パラメーターにわかりやすい名前を付ける✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="18e28-122">1つの `T` 1 文字の型パラメーターを持つ型の型パラメーター名としてを使用することを✔️してください。</span><span class="sxs-lookup"><span data-stu-id="18e28-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="18e28-123">✔️は、で説明する型パラメーター名をプレフィックスとして使用 `T` します。</span><span class="sxs-lookup"><span data-stu-id="18e28-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="18e28-124">パラメーターの名前の型パラメーターに設定されている制約を示す✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="18e28-125">たとえば、に制約されたパラメーターを `ISession` 呼び出すことができ `TSession` ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="18e28-126">共通型の名前</span><span class="sxs-lookup"><span data-stu-id="18e28-126">Names of Common Types</span></span>

 <span data-ttu-id="18e28-127">✔️は、次の表に記載されているガイドラインに従って、特定の .NET Framework 型から派生した型に名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="18e28-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="18e28-128">基本型</span><span class="sxs-lookup"><span data-stu-id="18e28-128">Base Type</span></span>|<span data-ttu-id="18e28-129">派生/実装型のガイドライン</span><span class="sxs-lookup"><span data-stu-id="18e28-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="18e28-130">カスタム属性クラスの名前にサフィックス "Attribute" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="18e28-131">✔️は、イベントで使用されるデリゲートの名前に "EventHandler" というサフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="18e28-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="18e28-132">イベントハンドラーとして使用されていないデリゲートの名前に "Callback" というサフィックスを追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="18e28-133">❌ デリゲートにサフィックス "Delegate" を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="18e28-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="18e28-134">サフィックス "EventArgs" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="18e28-135">❌ このクラスから派生させることはできません。代わりに、お使いの言語でサポートされているキーワードを使用してください。たとえば、C# では、キーワードを使用し `enum` ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="18e28-136">❌ サフィックス "Enum" または "Flag" は追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="18e28-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="18e28-137">サフィックス "Exception" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="18e28-138">サフィックス "Dictionary" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="18e28-139">`IDictionary`は特定の種類のコレクションであることに注意してくださいが、このガイドラインは、次に示す一般的なコレクションのガイドラインよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="18e28-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="18e28-140">サフィックス "Collection" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="18e28-141">サフィックス "Stream" を追加✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18e28-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="18e28-142">✔️サフィックス "Permission" を追加します。</span><span class="sxs-lookup"><span data-stu-id="18e28-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="18e28-143">列挙型に名前を付ける</span><span class="sxs-lookup"><span data-stu-id="18e28-143">Naming Enumerations</span></span>

 <span data-ttu-id="18e28-144">一般的に、列挙型の名前 (列挙型とも呼ばれます) は、標準的な型の名前付け規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e28-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="18e28-145">ただし、列挙型に特に適用される追加のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="18e28-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="18e28-146">✔️値がビットフィールドでない限り、列挙体には単数型名を使用します。</span><span class="sxs-lookup"><span data-stu-id="18e28-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="18e28-147">✔️は、値としてビットフィールドを持つ列挙体に対して複数形の型名を使用します (flags enum とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="18e28-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="18e28-148">❌ 列挙型の名前に "Enum" サフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="18e28-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="18e28-149">❌ 列挙型の名前に "Flag" または "Flags" サフィックスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="18e28-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="18e28-150">❌ 列挙値の名前にプレフィックスを使用しないでください (たとえば、ADO 列挙型の場合は "ad"、リッチテキスト列挙型の場合は "rtf" など)。</span><span class="sxs-lookup"><span data-stu-id="18e28-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="18e28-151">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="18e28-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="18e28-152">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="18e28-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="18e28-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="18e28-153">See also</span></span>

- [<span data-ttu-id="18e28-154">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="18e28-154">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="18e28-155">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="18e28-155">Naming Guidelines</span></span>](naming-guidelines.md)
