---
title: 機能拡張のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 7b7b1bcfc907612be12e7f8ca7114183f7e830ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734453"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="dcc51-102">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="dcc51-102">Designing for Extensibility</span></span>

<span data-ttu-id="dcc51-103">フレームワークを設計する際の重要な要素の1つは、フレームワークの拡張性が慎重に考慮されていることです。</span><span class="sxs-lookup"><span data-stu-id="dcc51-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="dcc51-104">これには、さまざまな拡張メカニズムに関連するコストと利点を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcc51-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="dcc51-105">この章では、拡張メカニズム (サブクラス化、イベント、仮想メンバー、コールバックなど) を、フレームワークの要件を最もよく満たすことができるかどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dcc51-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="dcc51-106">フレームワークで拡張性を実現するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="dcc51-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="dcc51-107">これは、あまり強力ではなく、コストが非常に高く、非常にコストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="dcc51-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="dcc51-108">特定の拡張要件については、要件を満たす最もコストの低い拡張性メカニズムを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcc51-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="dcc51-109">通常は、後で拡張機能を追加できることに注意してくださいが、重大な変更を導入しなくても、この機能を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="dcc51-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcc51-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dcc51-110">In This Section</span></span>  

 [<span data-ttu-id="dcc51-111">シールされていないクラス</span><span class="sxs-lookup"><span data-stu-id="dcc51-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="dcc51-112">プロテクトメンバー</span><span class="sxs-lookup"><span data-stu-id="dcc51-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="dcc51-113">イベントとコールバック</span><span class="sxs-lookup"><span data-stu-id="dcc51-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="dcc51-114">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="dcc51-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="dcc51-115">抽象化 (抽象型とインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="dcc51-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="dcc51-116">抽象化を実装するための基本クラス</span><span class="sxs-lookup"><span data-stu-id="dcc51-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="dcc51-117">シール</span><span class="sxs-lookup"><span data-stu-id="dcc51-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="dcc51-118">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="dcc51-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dcc51-119">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="dcc51-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc51-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcc51-120">See also</span></span>

- [<span data-ttu-id="dcc51-121">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="dcc51-121">Framework Design Guidelines</span></span>](index.md)
