---
title: 配列
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: c3545c609b6544e6528bbae08889d0ef20473802
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821607"
---
# <a name="arrays"></a><span data-ttu-id="a7a07-102">配列</span><span class="sxs-lookup"><span data-stu-id="a7a07-102">Arrays</span></span>
<span data-ttu-id="a7a07-103">✔️は、パブリック Api で配列に対してコレクションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a7a07-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="a7a07-104">コレクション [セクションで](guidelines-for-collections.md) は、コレクションと配列のどちらかを選択する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a7a07-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="a7a07-105">❌ 読み取り専用の配列フィールドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a7a07-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="a7a07-106">フィールド自体は読み取り専用であり、変更することはできませんが、配列内の要素は変更できます。</span><span class="sxs-lookup"><span data-stu-id="a7a07-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="a7a07-107">✔️多次元配列の代わりにジャグ配列を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a7a07-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="a7a07-108">ジャグ配列は、配列でもある要素を含む配列です。</span><span class="sxs-lookup"><span data-stu-id="a7a07-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="a7a07-109">要素を構成する配列は、さまざまなサイズになることがあり、一部のデータセット (スパースマトリックスなど) では、多次元配列と比較して無駄になる領域が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="a7a07-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="a7a07-110">さらに、CLR はジャグ配列に対するインデックス操作を最適化するため、一部のシナリオでは実行時のパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a7a07-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="a7a07-111">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="a7a07-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a7a07-112">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="a7a07-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a7a07-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7a07-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="a7a07-114">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a7a07-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a7a07-115">使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="a7a07-115">Usage Guidelines</span></span>](usage-guidelines.md)
