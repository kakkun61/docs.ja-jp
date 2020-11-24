---
title: コレクション初期化子を使用してディクショナリを初期化する方法 - C# プログラミング ガイド
description: Add メソッドまたはインデックス初期化子のいずれかを使用して、C# でディクショナリを初期化する方法について説明します。 この例では、両方のオプションについて説明します。
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 667b39076f01ab59eb64cf31d7c1dbb921500135
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099344"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="5218e-104">コレクション初期化子を使用してディクショナリを初期化する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5218e-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="5218e-105"><xref:System.Collections.Generic.Dictionary%602> にはキーと値のペアのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5218e-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="5218e-106">その <xref:System.Collections.Generic.Dictionary%602.Add%2A> メソッドは、それぞれキーと値に対する 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5218e-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="5218e-107">`Add` メソッドが複数のパラメーターを受け取る <xref:System.Collections.Generic.Dictionary%602> またはコレクションを初期化する 1 つの方法は、次の例に示すように、各パラメーターのセットを中かっこで囲むことです。</span><span class="sxs-lookup"><span data-stu-id="5218e-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="5218e-108">もう 1 つのオプションは、インデックス初期化子を使用することです。これも次の例に示されています。</span><span class="sxs-lookup"><span data-stu-id="5218e-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="5218e-109">例</span><span class="sxs-lookup"><span data-stu-id="5218e-109">Example</span></span>

<span data-ttu-id="5218e-110">次のコード例では、<xref:System.Collections.Generic.Dictionary%602> が型 `StudentName` のインスタンスで初期化されています。</span><span class="sxs-lookup"><span data-stu-id="5218e-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="5218e-111">最初の初期化では、`Add` メソッドを 2 つの引数と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="5218e-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="5218e-112">コンパイラにより、`int` キーと `StudentName` 値の各ペアに対して、`Add` への呼び出しが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5218e-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="5218e-113">2 回目の初期化では、`Dictionary` クラスのパブリック読み取り/書き込みインデクサー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="5218e-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="5218e-114">最初の宣言のコレクションの各要素の中かっこの 2 つのペアに注目してください。</span><span class="sxs-lookup"><span data-stu-id="5218e-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="5218e-115">最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students` <xref:System.Collections.Generic.Dictionary%602> に追加されるキーと値のペアの初期化子を囲んでいます。</span><span class="sxs-lookup"><span data-stu-id="5218e-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="5218e-116">最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="5218e-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="5218e-117">2 回目の初期化では、代入の左辺はキーで、右辺は `StudentName` のオブジェクトの初期化子を使用する値です。</span><span class="sxs-lookup"><span data-stu-id="5218e-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5218e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5218e-118">See also</span></span>

- [<span data-ttu-id="5218e-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5218e-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5218e-120">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="5218e-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
