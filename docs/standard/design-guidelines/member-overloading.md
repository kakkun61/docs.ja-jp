---
title: メンバーのオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: fe8bf23a04e6684564d3d7e287c2a009e0817732
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706633"
---
# <a name="member-overloading"></a><span data-ttu-id="264f5-102">メンバーのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="264f5-102">Member Overloading</span></span>

<span data-ttu-id="264f5-103">メンバーのオーバーロードとは、同じ型に複数のメンバーを作成し、パラメーターの数または型だけではなく、同じ名前を持つことを意味します。</span><span class="sxs-lookup"><span data-stu-id="264f5-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="264f5-104">たとえば、次の例では、 `WriteLine` メソッドはオーバーロードされています。</span><span class="sxs-lookup"><span data-stu-id="264f5-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="264f5-105">パラメーターを持つことができるのはメソッド、コンストラクター、およびインデックス付きプロパティだけなので、これらのメンバーのみをオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="264f5-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="264f5-106">オーバーロードは、再利用可能なライブラリのユーザビリティ、生産性、および読みやすさを向上させるための最も重要な手法の1つです。</span><span class="sxs-lookup"><span data-stu-id="264f5-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="264f5-107">パラメーターの数をオーバーロードすることで、コンストラクターとメソッドのより単純なバージョンを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="264f5-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="264f5-108">パラメーターの型をオーバーロードすると、選択した異なる型のセットに対して同じ操作を実行するメンバーに対して同じメンバー名を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="264f5-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="264f5-109">✔️は、記述的なパラメーター名を使用して、短いオーバーロードによって使用される既定値を示すようにします。</span><span class="sxs-lookup"><span data-stu-id="264f5-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="264f5-110">❌ オーバーロードでは、任意のパラメーター名を変更しないようにします。</span><span class="sxs-lookup"><span data-stu-id="264f5-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="264f5-111">1つのオーバーロード内のパラメーターが、別のオーバーロード内のパラメーターと同じ入力を表している場合、パラメーターの名前は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="264f5-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="264f5-112">❌ オーバーロードされたメンバーのパラメーターの順序が一致しないようにします。</span><span class="sxs-lookup"><span data-stu-id="264f5-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="264f5-113">同じ名前のパラメーターは、すべてのオーバーロードで同じ位置に出現します。</span><span class="sxs-lookup"><span data-stu-id="264f5-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="264f5-114">✔️は、最大のオーバーロード (拡張が必要な場合) のみにしてください。</span><span class="sxs-lookup"><span data-stu-id="264f5-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="264f5-115">より短いオーバーロードでは、より長いオーバーロードに対してを呼び出すだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="264f5-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="264f5-116">❌`ref` `out` メンバーをオーバーロードするためにまたは修飾子を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="264f5-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="264f5-117">一部の言語では、このようなオーバーロードの呼び出しを解決できません。</span><span class="sxs-lookup"><span data-stu-id="264f5-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="264f5-118">また、通常、このようなオーバーロードには完全に異なるセマンティクスがあり、オーバーロードは使用できませんが、2つの異なるメソッドを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="264f5-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="264f5-119">❌ 同じ位置にパラメーターを持つオーバーロードと、異なるセマンティクスを持つ同様の型を持つオーバーロードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="264f5-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="264f5-120">✔️ `null` 省略可能な引数に対してを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="264f5-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="264f5-121">✔️は、既定の引数を持つメンバーを定義するのではなく、メンバーのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="264f5-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="264f5-122">既定の引数は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="264f5-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="264f5-123">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="264f5-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="264f5-124">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="264f5-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="264f5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="264f5-125">See also</span></span>

- [<span data-ttu-id="264f5-126">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="264f5-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="264f5-127">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="264f5-127">Framework Design Guidelines</span></span>](index.md)
