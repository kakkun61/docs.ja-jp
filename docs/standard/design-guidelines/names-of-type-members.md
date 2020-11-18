---
title: 型のメンバーの名前
description: メソッド、プロパティ、イベント、フィールドなど、.NET での型のメンバーの名前付けのガイドラインについて説明します。
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 85f3137b4a8d75de92b12d6535415743395db890
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820914"
---
# <a name="names-of-type-members"></a><span data-ttu-id="5111a-103">型のメンバーの名前</span><span class="sxs-lookup"><span data-stu-id="5111a-103">Names of Type Members</span></span>
<span data-ttu-id="5111a-104">型は次のメンバーで構成されています: メソッド、プロパティ、イベント、コンストラクター、フィールド。</span><span class="sxs-lookup"><span data-stu-id="5111a-104">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="5111a-105">次のセクションは、型のメンバーに名前を付けるためのガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="5111a-105">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="5111a-106">メソッドの名前</span><span class="sxs-lookup"><span data-stu-id="5111a-106">Names of Methods</span></span>
 <span data-ttu-id="5111a-107">メソッドはアクションを実行する手段であるため、デザインのガイドラインでは、メソッド名を動詞または動詞句にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5111a-107">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="5111a-108">また、このガイドラインに従うと、名詞句または形容詞句であるプロパティ名および型名と、メソッド名を区別するためにも機能します。</span><span class="sxs-lookup"><span data-stu-id="5111a-108">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="5111a-109">✔️動詞または動詞句であるメソッド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5111a-109">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="5111a-110">プロパティの名前</span><span class="sxs-lookup"><span data-stu-id="5111a-110">Names of Properties</span></span>
 <span data-ttu-id="5111a-111">他のメンバーとは異なり、プロパティには名詞句または形容詞の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5111a-111">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="5111a-112">つまり、プロパティはデータを参照するため、プロパティの名前にはデータが反映されます。</span><span class="sxs-lookup"><span data-stu-id="5111a-112">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="5111a-113">プロパティ名には、常に Pascal 形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5111a-113">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="5111a-114">名詞、名詞句、または形容詞を使用してプロパティに名前を指定する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="5111a-114">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="5111a-115">❌ 次の例のように、"Get" メソッドの名前と一致するプロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="5111a-115">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="5111a-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="5111a-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="5111a-117">通常、このパターンは、プロパティが実際にメソッドであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5111a-117">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="5111a-118">コレクションのプロパティには、単数形の語句の後に "List" または "Collection" を続けて使用するのではなく、コレクション内の項目を記述する複数形の名前を付けて✔️します。</span><span class="sxs-lookup"><span data-stu-id="5111a-118">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="5111a-119">✔️は、(ではなく) 肯定的な句を使用してブール型のプロパティに名前を付け `CanSeek` `CantSeek` ます。</span><span class="sxs-lookup"><span data-stu-id="5111a-119">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="5111a-120">必要に応じて、ブール型プロパティの前に "Is"、"has"、または "has" を付けることもできますが、値を追加する場所のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5111a-120">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="5111a-121">✔️プロパティに型と同じ名前を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5111a-121">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="5111a-122">たとえば、次のプロパティは、`Color` という名前の列挙値を適切に取得および設定するため、プロパティは `Color` という名前になります。</span><span class="sxs-lookup"><span data-stu-id="5111a-122">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="5111a-123">イベントの名前</span><span class="sxs-lookup"><span data-stu-id="5111a-123">Names of Events</span></span>
 <span data-ttu-id="5111a-124">イベントは常に、発生中のアクションまたは発生したアクションのいずれかのアクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="5111a-124">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="5111a-125">そのため、メソッドと同様、イベントには動詞の名前が付けられ、イベントが発生した時刻を示すために動詞の時制が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5111a-125">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="5111a-126">✔️動詞または動詞句を使用してイベントに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5111a-126">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="5111a-127">例として、`Clicked`、`Painting`、`DroppedDown` などがあります。</span><span class="sxs-lookup"><span data-stu-id="5111a-127">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="5111a-128">✔️は、現在と過去の時制を使用して、before と after の概念でイベント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5111a-128">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="5111a-129">たとえば、ウィンドウを閉じる前に発生するクローズ イベントは `Closing` と呼ばれ、ウィンドウを閉じた後に発生するクローズ イベントは `Closed` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5111a-129">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="5111a-130">❌ "Before" または "After" プレフィックスまたは事後修正を使用して、イベントの前後を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5111a-130">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="5111a-131">前述のように、現在形と過去形を使用します。</span><span class="sxs-lookup"><span data-stu-id="5111a-131">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="5111a-132">次の例に示すように、イベントハンドラー (イベントの種類として使用されるデリゲート) に "EventHandler" サフィックスを付ける✔️ます。</span><span class="sxs-lookup"><span data-stu-id="5111a-132">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="5111a-133">`sender`イベントハンドラーでは、とという名前の2つのパラメーターを使用✔️ `e` ます。</span><span class="sxs-lookup"><span data-stu-id="5111a-133">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="5111a-134">sender パラメーターは、イベントを発生させたオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="5111a-134">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="5111a-135">より具体的な型を使用できる場合も、通常、sender パラメーターの型は `object` になります。</span><span class="sxs-lookup"><span data-stu-id="5111a-135">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="5111a-136">"EventArgs" サフィックスを使用して、イベント引数クラスの名前を✔️します。</span><span class="sxs-lookup"><span data-stu-id="5111a-136">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="5111a-137">フィールドの名前</span><span class="sxs-lookup"><span data-stu-id="5111a-137">Names of Fields</span></span>
 <span data-ttu-id="5111a-138">フィールドの名前付けのガイドラインは、静的パブリック フィールドと保護されたフィールドを対象とします。</span><span class="sxs-lookup"><span data-stu-id="5111a-138">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="5111a-139">内部フィールドとプライベート フィールドは、ガイドラインの対象ではありません。また、パブリック インスタンス フィールドや保護されたインスタンス フィールドは、「[メンバーのデザインのガイドライン](member.md)」で許可されていません。</span><span class="sxs-lookup"><span data-stu-id="5111a-139">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="5111a-140">フィールド名の大文字と小文字の区別を✔️します。</span><span class="sxs-lookup"><span data-stu-id="5111a-140">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="5111a-141">✔️は、名詞、名詞句、または形容詞を使用してフィールドに名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5111a-141">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="5111a-142">❌ フィールド名にはプレフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5111a-142">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="5111a-143">たとえば、静的フィールドを示すために、"g_" や "s_" を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5111a-143">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="5111a-144">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="5111a-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5111a-145">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="5111a-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5111a-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="5111a-146">See also</span></span>

- [<span data-ttu-id="5111a-147">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5111a-147">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="5111a-148">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5111a-148">Naming Guidelines</span></span>](naming-guidelines.md)
