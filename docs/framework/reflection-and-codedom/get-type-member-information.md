---
title: '方法: リフレクションを使用して型とメンバーの情報を取得する'
description: リフレクションを使用して型とメンバーの情報を取得する方法について説明します。ここでは、System.Reflection 名前空間を使用します。
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 771917bb2ae5cae56c775ae23119d5eda9701df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266325"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="bbb86-103">方法: リフレクションを使用して型とメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="bbb86-103">How to: Get type and member information by using reflection</span></span>

<span data-ttu-id="bbb86-104"><xref:System.Reflection> 名前空間には、型とそのメンバーに関する情報を取得するための多くのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="bbb86-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="bbb86-105">この記事では、これらのメソッドの 1 つである <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> を例として示します。</span><span class="sxs-lookup"><span data-stu-id="bbb86-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bbb86-106">詳細については、「[リフレクションの概要](reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbb86-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="bbb86-107">例</span><span class="sxs-lookup"><span data-stu-id="bbb86-107">Example</span></span>

<span data-ttu-id="bbb86-108">リフレクションを使用して型とメンバーの情報を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bbb86-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="bbb86-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbb86-109">See also</span></span>

- [<span data-ttu-id="bbb86-110">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="bbb86-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="bbb86-111">リフレクション</span><span class="sxs-lookup"><span data-stu-id="bbb86-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="bbb86-112">アプリケーション ドメインを使用する</span><span class="sxs-lookup"><span data-stu-id="bbb86-112">Use application domains</span></span>](../app-domains/use.md)
