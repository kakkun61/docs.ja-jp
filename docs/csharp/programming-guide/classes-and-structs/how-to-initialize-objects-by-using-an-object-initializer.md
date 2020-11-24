---
title: オブジェクト初期化子を使用してオブジェクトを初期化する方法 - C# プログラミング ガイド
description: コンストラクターを呼び出さずに、C# でオブジェクト初期化子を使用して、型オブジェクトを初期化する方法について説明します。 オブジェクト初期化子を使用して、匿名型を定義します。
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 032bbbff3ad356f9718053e8ba54a53559ef1ace
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098685"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="21379-104">オブジェクト初期化子を使用してオブジェクトを初期化する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="21379-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="21379-105">オブジェクト初期化子を使用すると、型のコンストラクターを明示的に呼び出さずに、宣言的な方法で型オブジェクトを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="21379-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="21379-106">次の例は、指定したオブジェクトでオブジェクト初期化子を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="21379-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="21379-107">コンパイラでは、最初にパラメーターなしのインスタンス コンストラクターにアクセスし、メンバーの初期化を処理することで、オブジェクト初期化子が処理されます。</span><span class="sxs-lookup"><span data-stu-id="21379-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="21379-108">そのため、クラスでパラメーターなしのコンストラクターが `private` として宣言されている場合、パブリック アクセスを必要とするオブジェクト初期化子は失敗します。</span><span class="sxs-lookup"><span data-stu-id="21379-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="21379-109">匿名型を定義する場合は、オブジェクト初期化子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21379-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="21379-110">詳細については、「[クエリで要素のプロパティのサブセットを返す方法](how-to-return-subsets-of-element-properties-in-a-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21379-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21379-111">例</span><span class="sxs-lookup"><span data-stu-id="21379-111">Example</span></span>  

<span data-ttu-id="21379-112">次の例は、オブジェクト初期化子を使用して、新しい `StudentName` 型を初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="21379-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="21379-113">この例では `StudentName` 型でプロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="21379-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="21379-114">オブジェクト初期化子を使用し、オブジェクトにインデクサーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="21379-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="21379-115">次の例では、インデクサーを使用する `BaseballTeam` クラスを定義し、選手を取得し、さまざまなポジションに据えます。</span><span class="sxs-lookup"><span data-stu-id="21379-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="21379-116">初期化子によって、ポジションの省略形 (野球のスコアカードに使用される各ポジションの番号) に基づき、選手を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="21379-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="21379-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="21379-117">See also</span></span>

- [<span data-ttu-id="21379-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="21379-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="21379-119">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="21379-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
