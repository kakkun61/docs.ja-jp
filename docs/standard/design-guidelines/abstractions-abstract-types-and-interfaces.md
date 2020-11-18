---
title: 抽象化 (抽象型およびインターフェイス)
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 6acefa2d4a2aed8fca5d0b7db634d393baac6b58
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821633"
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="c6d49-102">抽象化 (抽象型およびインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="c6d49-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="c6d49-103">抽象はコントラクトを記述する型ですが、コントラクトの完全な実装は提供しません。</span><span class="sxs-lookup"><span data-stu-id="c6d49-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="c6d49-104">抽象化は通常、抽象クラスまたは抽象インターフェイスとして実装され、適切に定義された一連の参照ドキュメントに含まれており、コントラクトを実装する型の必要なセマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c6d49-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="c6d49-105">.NET Framework の最も重要な抽象化には、、、などがあり <xref:System.IO.Stream> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Object> ます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>

 <span data-ttu-id="c6d49-106">抽象化のコントラクトをサポートする具象型を実装し、抽象化を使用するフレームワーク Api でこの具象型を使用することによって、フレームワークを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>

 <span data-ttu-id="c6d49-107">時間のテストに耐えられる意味のある有用な抽象化は、設計が非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="c6d49-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="c6d49-108">主な難しさは、メンバーの適切なセットを取得することです。これは、それ以上ではありません。</span><span class="sxs-lookup"><span data-stu-id="c6d49-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="c6d49-109">抽象化に含まれるメンバーが多すぎると、の実装が困難になるか、または不可能になります。</span><span class="sxs-lookup"><span data-stu-id="c6d49-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="c6d49-110">約束された機能のメンバーが少なすぎると、多くの興味深いシナリオでは役に立たなくなります。</span><span class="sxs-lookup"><span data-stu-id="c6d49-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>

 <span data-ttu-id="c6d49-111">フレームワークの抽象化が多すぎると、フレームワークのユーザビリティにも悪影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="c6d49-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="c6d49-112">多くの場合、抽象化を理解することは、具象実装の大きな画像や、抽象化で動作する Api にどのように適合するかを理解することでは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="c6d49-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="c6d49-113">また、抽象化とそのメンバーの名前は必ずしも抽象的なものです。そのため、多くの場合、使用状況のより広範なコンテキストを理解する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="c6d49-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>

 <span data-ttu-id="c6d49-114">ただし、抽象化によって、他の拡張メカニズムが一致しないことが多い非常に強力な拡張性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="c6d49-115">これらは、プラグイン、制御の反転 (IoC)、パイプラインなど、さまざまなアーキテクチャパターンの中核になっています。</span><span class="sxs-lookup"><span data-stu-id="c6d49-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="c6d49-116">また、フレームワークのテスト性をテストするうえで非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="c6d49-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="c6d49-117">優れた抽象化によって、単体テストの目的で、高い依存関係をスタブ化できます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="c6d49-118">要約すると、抽象化は、最新のオブジェクト指向フレームワークによって検出された結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="c6d49-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>

 <span data-ttu-id="c6d49-119">❌ 抽象化を利用して、抽象化を使用するいくつかの具象実装と Api を開発することによって、抽象化を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="c6d49-119">❌ DO NOT provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>

 <span data-ttu-id="c6d49-120">抽象化を設計するときは、抽象クラスとインターフェイスの間で慎重に選択する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-120">✔️ DO choose carefully between an abstract class and an interface when designing an abstraction.</span></span>

 <span data-ttu-id="c6d49-121">✔️抽象化の具象実装の参照テストを提供することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c6d49-121">✔️ CONSIDER providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="c6d49-122">このようなテストでは、実装でコントラクトが正しく実装されているかどうかをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6d49-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>

 <span data-ttu-id="c6d49-123">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="c6d49-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c6d49-124">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="c6d49-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c6d49-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6d49-125">See also</span></span>

- [<span data-ttu-id="c6d49-126">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c6d49-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="c6d49-127">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="c6d49-127">Designing for Extensibility</span></span>](designing-for-extensibility.md)
