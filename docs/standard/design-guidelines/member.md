---
title: メンバーのデザインのガイドライン
description: .NET のメンバーデザインガイドラインについて説明します。 メンバーには、メソッド、プロパティ、イベント、コンストラクター、およびフィールドが含まれます。
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: 5070f45beccd89d6f051f1b1d8345390e915d471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706594"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="41550-104">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="41550-104">Member Design Guidelines</span></span>

<span data-ttu-id="41550-105">メソッド、プロパティ、イベント、コンストラクター、およびフィールドは、総称してメンバーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="41550-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="41550-106">フレームワークのエンドユーザーに公開されるフレームワークの機能は、最終的にメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="41550-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="41550-107">メンバーは、仮想または非仮想、具象または抽象、静的、またはインスタンスにすることができ、アクセシビリティの複数の異なるスコープを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="41550-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="41550-108">これらはすべて、非常に優れた表現力を提供しますが、同時にフレームワークデザイナーの一部に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41550-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="41550-109">この章では、任意の型のメンバーを設計する際に従う必要がある基本的なガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="41550-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41550-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="41550-110">In This Section</span></span>  

 [<span data-ttu-id="41550-111">メンバーのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="41550-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="41550-112">プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="41550-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="41550-113">コンストラクターのデザイン</span><span class="sxs-lookup"><span data-stu-id="41550-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="41550-114">イベントのデザイン</span><span class="sxs-lookup"><span data-stu-id="41550-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="41550-115">フィールドのデザイン</span><span class="sxs-lookup"><span data-stu-id="41550-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="41550-116">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="41550-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="41550-117">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="41550-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="41550-118">パラメーターのデザイン</span><span class="sxs-lookup"><span data-stu-id="41550-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="41550-119">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="41550-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="41550-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="41550-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41550-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="41550-121">See also</span></span>

- [<span data-ttu-id="41550-122">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="41550-122">Framework Design Guidelines</span></span>](index.md)
