---
title: 抽象プロパティを定義する方法 - C# プログラミング ガイド
description: C# で抽象プロパティを定義する方法について説明します。 抽象プロパティを宣言することは、クラスがプロパティをサポートしていることを意味します。 派生クラスによってアクセサーが実装されます。
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: e114e9349db9d6bcb18e15eb62532f48aa063339
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513030"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="c195b-105">抽象プロパティを定義する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c195b-105">How to define abstract properties (C# Programming Guide)</span></span>

<span data-ttu-id="c195b-106">次の例では、[抽象](../../language-reference/keywords/abstract.md)プロパティを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c195b-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="c195b-107">抽象プロパティの宣言では、プロパティ アクセサーは実装されません。クラスがプロパティをサポートしていることは宣言しますが、アクセサーの実装は派生クラスに委ねます。</span><span class="sxs-lookup"><span data-stu-id="c195b-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="c195b-108">基本クラスから継承された抽象プロパティを実装する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c195b-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="c195b-109">このサンプルは 3 つのファイルで構成され、それぞれ個別にコンパイルされ、生成されたアセンブリが次のコンパイルで参照されます。</span><span class="sxs-lookup"><span data-stu-id="c195b-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="c195b-110">abstractshape.cs: 抽象 `Shape` プロパティを含む `Area` クラス。</span><span class="sxs-lookup"><span data-stu-id="c195b-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="c195b-111">shapes.cs:`Shape` クラスのサブクラス。</span><span class="sxs-lookup"><span data-stu-id="c195b-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="c195b-112">shapetest.cs:`Shape` から派生したいくつかのオブジェクトの面積を表示するテスト プログラム。</span><span class="sxs-lookup"><span data-stu-id="c195b-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="c195b-113">この例をコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c195b-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="c195b-114">これで、実行可能ファイル shapetest.exe が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c195b-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c195b-115">例</span><span class="sxs-lookup"><span data-stu-id="c195b-115">Example</span></span>  

 <span data-ttu-id="c195b-116">このファイルは、`double` 型の `Shape` プロパティを含む `Area` クラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="c195b-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="c195b-117">プロパティの修飾子は、プロパティ宣言自体に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c195b-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="c195b-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c195b-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="c195b-119">抽象プロパティ (この例では `Area` など) を宣言する場合は、使用可能なアクセサーを示すだけで、実装はしません。</span><span class="sxs-lookup"><span data-stu-id="c195b-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="c195b-120">この例では、[get](../../language-reference/keywords/get.md) アクセサーのみが使用可能であるため、プロパティは読み取り専用となります。</span><span class="sxs-lookup"><span data-stu-id="c195b-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c195b-121">例</span><span class="sxs-lookup"><span data-stu-id="c195b-121">Example</span></span>  

 <span data-ttu-id="c195b-122">次のコードは、`Shape` の 3 つのサブクラスと、それらがどのように `Area` プロパティをオーバーライドして独自の実装を提供するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="c195b-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="c195b-123">例</span><span class="sxs-lookup"><span data-stu-id="c195b-123">Example</span></span>  

 <span data-ttu-id="c195b-124">次のコードは、`Shape` から派生するオブジェクトをいくつか作成し、それらの面積を出力するテスト プログラムを示しています。</span><span class="sxs-lookup"><span data-stu-id="c195b-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c195b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c195b-125">See also</span></span>

- [<span data-ttu-id="c195b-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c195b-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c195b-127">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="c195b-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="c195b-128">抽象クラスとシール クラス、およびクラス メンバー</span><span class="sxs-lookup"><span data-stu-id="c195b-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="c195b-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c195b-129">Properties</span></span>](./properties.md)
