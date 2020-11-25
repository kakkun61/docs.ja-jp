---
title: 等値演算子
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 2331a852adb4dd254af85060a5077f454bcfe0eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734427"
---
# <a name="equality-operators"></a><span data-ttu-id="dd2b6-102">等値演算子</span><span class="sxs-lookup"><span data-stu-id="dd2b6-102">Equality Operators</span></span>

<span data-ttu-id="dd2b6-103">このセクションでは、等値演算子のオーバーロードについて説明し、 `operator==` 等値演算子としてとを参照し `operator!=` ます。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="dd2b6-104">❌ 等値演算子の1つをオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="dd2b6-105">✔️、 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 等値演算子のセマンティクスと同様のパフォーマンス特性がまったく同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="dd2b6-106">これは多くの場合 `Object.Equals` 、等値演算子がオーバーロードされるときにをオーバーライドする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="dd2b6-107">❌ 等値演算子から例外をスローしないようにします。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="dd2b6-108">たとえば、引数のいずれかがスローではなく null の場合は、false を返し `NullReferenceException` ます。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="dd2b6-109">値型の等値演算子</span><span class="sxs-lookup"><span data-stu-id="dd2b6-109">Equality Operators on Value Types</span></span>

 <span data-ttu-id="dd2b6-110">等しい場合は、値型に対して等値演算子をオーバーロード✔️ます。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="dd2b6-111">ほとんどのプログラミング言語では、値型にの既定の実装はありません `operator==` 。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="dd2b6-112">参照型の等値演算子</span><span class="sxs-lookup"><span data-stu-id="dd2b6-112">Equality Operators on Reference Types</span></span>

 <span data-ttu-id="dd2b6-113">❌ 変更可能な参照型に対する等値演算子のオーバーロードは避けてください。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="dd2b6-114">多くの言語には、参照型の等価演算子が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="dd2b6-115">これらの組み込み演算子は、通常、参照の等価性を実装します。多くの開発者は、既定の動作が値の等価性に変更されると驚かれます。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="dd2b6-116">不変性によって参照の等価性と値の等価性の違いが非常に困難になるため、この問題は変更できない参照型に対しては緩和されます。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="dd2b6-117">❌ 実装が参照の等価性よりも大幅に遅くなる場合は、参照型に対する等値演算子のオーバーロードを避けてください。</span><span class="sxs-lookup"><span data-stu-id="dd2b6-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="dd2b6-118">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="dd2b6-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dd2b6-119">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="dd2b6-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dd2b6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd2b6-120">See also</span></span>

- [<span data-ttu-id="dd2b6-121">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="dd2b6-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="dd2b6-122">使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="dd2b6-122">Usage Guidelines</span></span>](usage-guidelines.md)
