---
title: 型のデザインのガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: a20744f76433ff12456967e4d41d9a13b6f5d46c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677532"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="87ad6-102">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="87ad6-102">Type Design Guidelines</span></span>

<span data-ttu-id="87ad6-103">CLR の観点からは、参照型と値型のカテゴリは2つだけですが、フレームワークの設計について説明するために、型をより多くの論理グループに分割し、それぞれに固有のデザインルールを使用します。</span><span class="sxs-lookup"><span data-stu-id="87ad6-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="87ad6-104">クラスは、参照型の一般的なケースです。</span><span class="sxs-lookup"><span data-stu-id="87ad6-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="87ad6-105">多くのフレームワークでは、多くの型が構成されています。</span><span class="sxs-lookup"><span data-stu-id="87ad6-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="87ad6-106">クラスは、サポートされているオブジェクト指向の機能の豊富なセットと、その一般的な適用性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="87ad6-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="87ad6-107">基本クラスと抽象クラスは、機能拡張に関連する特殊な論理グループです。</span><span class="sxs-lookup"><span data-stu-id="87ad6-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="87ad6-108">インターフェイスは、参照型と値型の両方で実装できる型です。</span><span class="sxs-lookup"><span data-stu-id="87ad6-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="87ad6-109">これにより、参照型と値型のポリモーフィック階層のルートとして機能することができます。</span><span class="sxs-lookup"><span data-stu-id="87ad6-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="87ad6-110">さらに、インターフェイスを使用して、CLR でネイティブにサポートされていない複数の継承をシミュレートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="87ad6-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="87ad6-111">構造体は値型の一般的なケースであり、言語プリミティブと同様に、小規模な単純型用に予約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ad6-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="87ad6-112">列挙型は、曜日やコンソールの色など、短い値のセットを定義するために使用される特殊な値型です。</span><span class="sxs-lookup"><span data-stu-id="87ad6-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="87ad6-113">静的クラスは、静的メンバーのコンテナーとして使用される型です。</span><span class="sxs-lookup"><span data-stu-id="87ad6-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="87ad6-114">一般的に、他の操作へのショートカットを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="87ad6-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="87ad6-115">デリゲート、例外、属性、配列、およびコレクションは、特定の用途を想定した参照型のすべての特殊なケースであり、その設計と使用に関するガイドラインについては、このブックの別の部分で説明します。</span><span class="sxs-lookup"><span data-stu-id="87ad6-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="87ad6-116">✔️、関連性のない機能をランダムにコレクションするだけでなく、適切に定義された一連の関連するメンバーであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="87ad6-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="87ad6-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="87ad6-117">In This Section</span></span>

 <span data-ttu-id="87ad6-118">[クラスと構造体の間の](choosing-between-class-and-struct.md)[抽象クラスのデザイン](abstract-class.md)[静的クラスデザイン](static-class.md)[インターフェイス](interface.md)のデザイン [構造体](struct.md)を設計する [入れ子になった型](nested-types.md)のデザイン [Enum Design](enum.md) *© 2005, 2009 Microsoft Corporation.すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="87ad6-118">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="87ad6-119">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="87ad6-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="87ad6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="87ad6-120">See also</span></span>

- [<span data-ttu-id="87ad6-121">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="87ad6-121">Framework Design Guidelines</span></span>](index.md)
