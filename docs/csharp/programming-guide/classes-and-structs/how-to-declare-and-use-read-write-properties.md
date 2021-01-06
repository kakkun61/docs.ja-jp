---
title: 読み取り/書き込みプロパティを宣言および使用する方法 - C# プログラミング ガイド
description: C# で読み取り/書き込みプロパティを使用する方法について説明します。 このサンプルには、読み取り/書き込みプロパティとなるように、get アクセサーと set アクセサーを持つ 2 つのプロパティが含まれています。
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 824ce8a8cd8f0ef94495a85726331cd6cd024891
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513011"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="f3af0-104">読み取り/書き込みプロパティを宣言および使用する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f3af0-104">How to declare and use read write properties (C# Programming Guide)</span></span>

<span data-ttu-id="f3af0-105">プロパティは、オブジェクトのデータへの保護されていない、制御されず未確認のアクセスに伴うリスクなしにパブリック データ メンバーの利便性を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3af0-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="f3af0-106">これは *アクセサー* を通じて行われます。アクセサーは、基になるデータ メンバーの値を割り当てたり、取得したりする特殊なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f3af0-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="f3af0-107">[set](../../language-reference/keywords/set.md) アクセサーはデータ メンバーの割り当てを可能にし、[get](../../language-reference/keywords/get.md) アクセサーはデータ メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f3af0-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="f3af0-108">このサンプルでは、`Name` (string) および `Age` (int) という 2 つのプロパティを持つ `Person` クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="f3af0-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="f3af0-109">両方のプロパティは `get` および `set` アクセサーを提供するため、読み取り/書き込みプロパティと見なされます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3af0-110">例</span><span class="sxs-lookup"><span data-stu-id="f3af0-110">Example</span></span>  

 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f3af0-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f3af0-111">Robust Programming</span></span>  

 <span data-ttu-id="f3af0-112">前述の例では、`Name` および `Age` プロパティは[パブリック](../../language-reference/keywords/public.md)であり、`get` および `set` アクセサーの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="f3af0-113">そのため、任意のオブジェクトがこれらのプロパティを読み書きできます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="f3af0-114">ただし、アクセサーのいずれかを除外することが望ましい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f3af0-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="f3af0-115">たとえば、次のように `set` アクセサーを省略すると、プロパティが読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="f3af0-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="f3af0-116">また、一方のアクセサーをパブリックに公開し、もう一方を private または protected にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="f3af0-117">詳細については、「[アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)](./restricting-accessor-accessibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3af0-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="f3af0-118">プロパティを宣言すると、プロパティをクラスのフィールドのように使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="f3af0-119">そのため、プロパティ値の取得と設定の両方で、次のように自然な構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="f3af0-120">プロパティの `set` メソッドでは、特殊な `value` 変数を使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3af0-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="f3af0-121">この変数には、ユーザーが指定した値が含まれます。たとえば、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f3af0-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="f3af0-122">`Person` オブジェクトの `Age` プロパティの値を増分する場合は、次のような簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f3af0-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="f3af0-123">`set` メソッドと `get` メソッドがそれぞれ使用されてプロパティがモデル化されている場合、上記と同じ内容のコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f3af0-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="f3af0-124">この例では、`ToString` メソッドが次のようにオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="f3af0-125">プログラムでは `ToString` が明示的に使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3af0-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="f3af0-126">既定では、`WriteLine` 呼び出しによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f3af0-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3af0-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3af0-127">See also</span></span>

- [<span data-ttu-id="f3af0-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f3af0-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f3af0-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3af0-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="f3af0-130">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="f3af0-130">Classes and Structs</span></span>](./index.md)
