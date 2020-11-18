---
title: 抽象クラスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 6903e10c8695376d8ac5961461796c5413307f90
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821646"
---
# <a name="abstract-class-design"></a><span data-ttu-id="82543-102">抽象クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="82543-102">Abstract Class Design</span></span>

<span data-ttu-id="82543-103">❌ 抽象型では、パブリックまたはプロテクトの内部コンストラクターを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="82543-103">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="82543-104">コンストラクターは、ユーザーが型のインスタンスを作成する必要がある場合にのみ、パブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="82543-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="82543-105">抽象型のインスタンスを作成することはできないため、パブリックコンストラクターを持つ抽象型は誤って設計され、ユーザーに対して誤解が生じることになります。</span><span class="sxs-lookup"><span data-stu-id="82543-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="82543-106">✔️は、抽象クラスで protected コンストラクターまたは internal コンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="82543-106">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="82543-107">プロテクトコンストラクターはより一般的であり、サブタイプの作成時に基底クラスが独自の初期化を実行できるようにするだけです。</span><span class="sxs-lookup"><span data-stu-id="82543-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="82543-108">内部コンストラクターを使用すると、抽象クラスの具象実装を、クラスを定義するアセンブリに限定できます。</span><span class="sxs-lookup"><span data-stu-id="82543-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="82543-109">✔️は、出荷する各抽象クラスから継承される具象型を少なくとも1つ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82543-109">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="82543-110">これにより、抽象クラスの設計を検証できます。</span><span class="sxs-lookup"><span data-stu-id="82543-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="82543-111">たとえば、  <xref:System.IO.FileStream?displayProperty=nameWithType> は抽象クラスの実装です <xref:System.IO.Stream?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="82543-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="82543-112">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="82543-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="82543-113">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="82543-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="82543-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="82543-114">See also</span></span>

- [<span data-ttu-id="82543-115">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="82543-115">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="82543-116">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="82543-116">Framework Design Guidelines</span></span>](index.md)
