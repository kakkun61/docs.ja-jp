---
title: 例外のデザインのガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 776e559bb1629245c275cb4463531a8dd4b230ae
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821152"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="6446f-102">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="6446f-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="6446f-103">例外処理には、戻り値に基づくエラー報告よりも多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="6446f-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="6446f-104">優れたフレームワーク設計は、アプリケーション開発者が例外の利点を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6446f-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="6446f-105">このセクションでは、例外の利点について説明し、それらを効果的に使用するためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="6446f-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6446f-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6446f-106">In This Section</span></span>  
 [<span data-ttu-id="6446f-107">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="6446f-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="6446f-108">標準例外型の使用</span><span class="sxs-lookup"><span data-stu-id="6446f-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="6446f-109">例外とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="6446f-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="6446f-110">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="6446f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6446f-111">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="6446f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6446f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6446f-112">See also</span></span>

- [<span data-ttu-id="6446f-113">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="6446f-113">Framework Design Guidelines</span></span>](index.md)
