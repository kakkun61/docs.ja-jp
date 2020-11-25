---
title: 入れ子にされた型
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: bc0aee32b5cc1d40afdd9cce8260d5b5341a687d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706399"
---
# <a name="nested-types"></a><span data-ttu-id="19acb-102">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="19acb-102">Nested Types</span></span>

<span data-ttu-id="19acb-103">入れ子になった型は、外側の型と呼ばれる別の型のスコープ内で定義された型です。</span><span class="sxs-lookup"><span data-stu-id="19acb-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="19acb-104">入れ子になった型は、それを囲む型のすべてのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="19acb-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="19acb-105">たとえば、外側の型で定義されているプライベートフィールドと、それを囲む型のすべての先祖で定義されている保護されたフィールドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="19acb-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="19acb-106">一般に、入れ子になった型は控えめに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19acb-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="19acb-107">直接呼び出すべきではないいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="19acb-107">There are several reasons for this.</span></span> <span data-ttu-id="19acb-108">一部の開発者は、この概念について完全には理解していません。</span><span class="sxs-lookup"><span data-stu-id="19acb-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="19acb-109">たとえば、これらの開発者は、入れ子になった型の変数を宣言する構文で問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19acb-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="19acb-110">入れ子になった型もその外側の型と密接に結び付いています。そのため、汎用型には適していません。</span><span class="sxs-lookup"><span data-stu-id="19acb-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="19acb-111">入れ子になった型は、それを囲む型の実装の詳細をモデリングする場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="19acb-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="19acb-112">エンドユーザーは、入れ子にされた型の変数を宣言する必要はほとんどなく、入れ子になった型を明示的にインスタンス化する必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="19acb-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="19acb-113">たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="19acb-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="19acb-114">列挙子は、通常、それを囲む型によってインスタンス化されます。また、多くの言語では foreach ステートメントがサポートされるため、列挙子の変数はエンドユーザーが宣言することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="19acb-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="19acb-115">入れ子になった型とその外側の型のリレーションシップが望ましい場合は、入れ子にされた型を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="19acb-115">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="19acb-116">❌ 入れ子になったパブリック型を論理グループ化構成体として使用しないでください。このには名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="19acb-116">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="19acb-117">❌ 公開されている入れ子にされた型は避けてください。</span><span class="sxs-lookup"><span data-stu-id="19acb-117">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="19acb-118">唯一の例外は、入れ子にされた型の変数は、サブクラス化やその他の高度なカスタマイズシナリオなど、まれなシナリオでのみ宣言する必要がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="19acb-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="19acb-119">❌ 型が含まれている型の外で参照される可能性が高い場合は、入れ子にされた型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="19acb-119">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="19acb-120">たとえば、クラスで定義されたメソッドに渡される列挙型は、クラスで入れ子にされた型として定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="19acb-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="19acb-121">❌ クライアントコードによってインスタンス化する必要がある場合は、入れ子にされた型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="19acb-121">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="19acb-122">型にパブリックコンストラクターがある場合は、入れ子になっていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19acb-122">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="19acb-123">型がインスタンス化できる場合、型がそれ自体のフレームワーク内に配置されていることを示しているように見えます (作成、操作、外部型を使用せずに破棄できます)。したがって、入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="19acb-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="19acb-124">外部型に関係なく、外側の型の外部で内部型を広く再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="19acb-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="19acb-125">❌ 入れ子になった型は、インターフェイスのメンバーとして定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="19acb-125">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="19acb-126">多くの言語では、このようなコンストラクトはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="19acb-126">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="19acb-127">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="19acb-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="19acb-128">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="19acb-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="19acb-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="19acb-129">See also</span></span>

- [<span data-ttu-id="19acb-130">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="19acb-130">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="19acb-131">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="19acb-131">Framework Design Guidelines</span></span>](index.md)
