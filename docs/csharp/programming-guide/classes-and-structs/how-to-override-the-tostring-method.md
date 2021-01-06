---
title: ToString メソッドをオーバーライドする方法 - C# プログラミング ガイド
description: C# で ToString メソッドをオーバーライドする方法について説明します。 すべてのクラスまたは構造体がオブジェクトを継承し、ToString を取得して、そのオブジェクトの文字列表現を返します。
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 9573e6b97383d6f422c6a2802040fb9d6db709dd
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512744"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="89b7a-104">ToString メソッドをオーバーライドする方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="89b7a-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="89b7a-105">C# では、すべてのクラスまたは構造体が、暗黙的に <xref:System.Object> クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="89b7a-106">そのため、C# のすべてのオブジェクトが <xref:System.Object.ToString%2A> メソッドを取得し、そのオブジェクトの文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="89b7a-107">たとえば、`int` 型の変数はすべて `ToString` メソッドを持ち、次のようにその変数の内容を文字列として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="89b7a-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="89b7a-108">カスタムのクラスまたは構造体を作成するときは、クライアント コードにカスタム型の情報を提供するため、<xref:System.Object.ToString%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b7a-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="89b7a-109">`ToString` メソッドで書式設定文字列やその他のカスタム形式を使用する方法については、「[型の書式設定](../../../standard/base-types/formatting-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b7a-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="89b7a-110">このメソッドを使用して提供する情報を決定するときは、作成したクラスまたは構造体が信頼関係のないコードによって使用されるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="89b7a-111">悪意があるコードで利用される可能性がある情報を提供しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="89b7a-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="89b7a-112">クラスまたは構造体内の `ToString` メソッドをオーバーライドする手順</span><span class="sxs-lookup"><span data-stu-id="89b7a-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="89b7a-113">次の修飾子および戻り値の値を指定して、`ToString` メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="89b7a-114">文字列を返すように、メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="89b7a-115">次の例では、特定のクラス インスタンスに固有のデータに加えて、クラス名も返されます。</span><span class="sxs-lookup"><span data-stu-id="89b7a-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="89b7a-116">`ToString` メソッドをテストする方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="89b7a-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="89b7a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="89b7a-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="89b7a-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="89b7a-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="89b7a-119">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="89b7a-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="89b7a-120">文字列</span><span class="sxs-lookup"><span data-stu-id="89b7a-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="89b7a-121">string</span><span class="sxs-lookup"><span data-stu-id="89b7a-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="89b7a-122">override</span><span class="sxs-lookup"><span data-stu-id="89b7a-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="89b7a-123">virtual</span><span class="sxs-lookup"><span data-stu-id="89b7a-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="89b7a-124">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="89b7a-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
