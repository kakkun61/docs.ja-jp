---
title: '方法: リフレクション出力を使用してジェネリック型を定義する'
description: リフレクション出力を使用してジェネリック型を定義する方法について確認します。 2 つの型パラメーターを持つジェネリック型を作成し、クラス制約、インターフェイス制約などを適用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
ms.openlocfilehash: 75076eb9ce1b9bfc6b3c8b5a48e200ca5e63cdff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263465"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a><span data-ttu-id="ce01a-104">方法: リフレクション出力を使用してジェネリック型を定義する</span><span class="sxs-lookup"><span data-stu-id="ce01a-104">How to: Define a Generic Type with Reflection Emit</span></span>

<span data-ttu-id="ce01a-105">このトピックでは、2 種類のパラメーターを持つ単純なジェネリック型を作成する方法、クラス制約、インターフェイス制約、特殊な制約をパラメーターに適用する方法、パラメーターの型や戻り値の型としてクラスの型パラメーターを使用するメンバーを作成する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-105">This topic shows how to create a simple generic type with two type parameters, how to apply class constraints, interface constraints, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce01a-106">メソッドはジェネリック型に属し、その型の型パラメーターを使用するだけであるため、ジェネリックではありません。</span><span class="sxs-lookup"><span data-stu-id="ce01a-106">A method is not generic just because it belongs to a generic type and uses the type parameters of that type.</span></span> <span data-ttu-id="ce01a-107">メソッドがジェネリックになるのは、そのメソッドが独自の型パラメーター リストを持つ場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ce01a-107">A method is generic only if it has its own type parameter list.</span></span> <span data-ttu-id="ce01a-108">ジェネリック型のほとんどのメソッドは、この例のように、ジェネリックではありません。</span><span class="sxs-lookup"><span data-stu-id="ce01a-108">Most methods on generic types are not generic, as in this example.</span></span> <span data-ttu-id="ce01a-109">ジェネリック メソッドの出力の例については、「[方法: リフレクション出力を使用してジェネリック メソッドを定義する](how-to-define-a-generic-method-with-reflection-emit.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce01a-109">For an example of emitting a generic method, see [How to: Define a Generic Method with Reflection Emit](how-to-define-a-generic-method-with-reflection-emit.md).</span></span>  
  
### <a name="to-define-a-generic-type"></a><span data-ttu-id="ce01a-110">ジェネリック型を定義するには</span><span class="sxs-lookup"><span data-stu-id="ce01a-110">To define a generic type</span></span>  
  
1. <span data-ttu-id="ce01a-111">`GenericEmitExample1` という名前の動的アセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-111">Define a dynamic assembly named `GenericEmitExample1`.</span></span> <span data-ttu-id="ce01a-112">この例では、アセンブリが実行され、ディスクに保存されます。そのため、<xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> が指定されています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-112">In this example, the assembly is executed and saved to disk, so <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> is specified.</span></span>  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. <span data-ttu-id="ce01a-113">動的モジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-113">Define a dynamic module.</span></span> <span data-ttu-id="ce01a-114">アセンブリは実行可能モジュールで構成をされます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-114">An assembly is made up of executable modules.</span></span> <span data-ttu-id="ce01a-115">単一モジュールのアセンブリの場合、モジュール名はアセンブリ名と同じであり、ファイル名はモジュール名に拡張子が付いたものになります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-115">For a single-module assembly, the module name is the same as the assembly name, and the file name is the module name plus an extension.</span></span>  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. <span data-ttu-id="ce01a-116">クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-116">Define a class.</span></span> <span data-ttu-id="ce01a-117">この例では、クラスに `Sample` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-117">In this example, the class is named `Sample`.</span></span>  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. <span data-ttu-id="ce01a-118">パラメーターの名前を格納している文字列の配列を `Sample` メソッドに渡して、<xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> のジェネリック型パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-118">Define the generic type parameters of `Sample` by passing an array of strings containing the names of the parameters to the <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ce01a-119">これによりクラスがジェネリック型になります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-119">This makes the class a generic type.</span></span> <span data-ttu-id="ce01a-120">戻り値は、型パラメーターを表す <xref:System.Reflection.Emit.GenericTypeParameterBuilder> オブジェクトの配列になります。型パラメーターは出力されたコードで利用できます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-120">The return value is an array of <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objects representing the type parameters, which can be used in your emitted code.</span></span>  
  
     <span data-ttu-id="ce01a-121">次のコードでは、`Sample` が型パラメーターの `TFirst` と `TSecond` を持つジェネリック型になります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-121">In the following code, `Sample` becomes a generic type with type parameters `TFirst` and `TSecond`.</span></span> <span data-ttu-id="ce01a-122">コードを読みやすくするために、各 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> が型パラメーターと同じ名前の変数に入ります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-122">To make the code easier to read, each <xref:System.Reflection.Emit.GenericTypeParameterBuilder> is placed in a variable with the same name as the type parameter.</span></span>  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. <span data-ttu-id="ce01a-123">型パラメーターに特殊な制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-123">Add special constraints to the type parameters.</span></span> <span data-ttu-id="ce01a-124">この例では、型パラメーター `TFirst` が、パラメーターのないコンストラクターを持つ型と参照型に制約されています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-124">In this example, type parameter `TFirst` is constrained to types that have parameterless constructors, and to reference types.</span></span>  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. <span data-ttu-id="ce01a-125">オプションで、型パラメーターにクラスの制約とインターフェイスの制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-125">Optionally add class and interface constraints to the type parameters.</span></span> <span data-ttu-id="ce01a-126">この例では、型パラメーター `TFirst` が、変数 `baseType` に含まれる <xref:System.Type> オブジェクトで表される基底クラスから派生し、型が変数の `interfaceA` と `interfaceB` に含まれるインターフェイスを実装する型に制約されています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-126">In this example, type parameter `TFirst` is constrained to types that derive from the base class represented by the <xref:System.Type> object contained in the variable `baseType`, and that implement the interfaces whose types are contained in the variables `interfaceA` and `interfaceB`.</span></span> <span data-ttu-id="ce01a-127">これらの変数の宣言と割り当てについては、コード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce01a-127">See the code example for the declaration and assignment of these variables.</span></span>  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. <span data-ttu-id="ce01a-128">フィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-128">Define a field.</span></span> <span data-ttu-id="ce01a-129">この例では、フィールドの型は型パラメーター `TFirst` により指定されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-129">In this example, the type of the field is specified by type parameter `TFirst`.</span></span> <span data-ttu-id="ce01a-130"><xref:System.Reflection.Emit.GenericTypeParameterBuilder> は <xref:System.Type> から派生します。つまり、ジェネリック型パラメーターは、型を利用できるあらゆる場所で利用できます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-130"><xref:System.Reflection.Emit.GenericTypeParameterBuilder> derives from <xref:System.Type>, so you can use generic type parameters anywhere a type can be used.</span></span>  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. <span data-ttu-id="ce01a-131">ジェネリック型の型パラメーターを使用するメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-131">Define a method that uses the type parameters of the generic type.</span></span> <span data-ttu-id="ce01a-132">そのようなメソッドは、独自の型パラメーター リストが与えられない限り、ジェネリックにならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce01a-132">Note that such methods are not generic unless they have their own type parameter lists.</span></span> <span data-ttu-id="ce01a-133">次のコードでは、`TFirst` の配列を受け取り、その配列のすべての要素を含む `List<TFirst>` (Visual Basic の場合は `List(Of TFirst)`) を返す `static` メソッド (Visual Basic の場合は `Shared`) が定義されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-133">The following code defines a `static` method (`Shared` in Visual Basic) that takes an array of `TFirst` and returns a `List<TFirst>` (`List(Of TFirst)` in Visual Basic) containing all the elements of the array.</span></span> <span data-ttu-id="ce01a-134">このメソッドを定義するには、ジェネリック型定義の `List<T>` で <xref:System.Type.MakeGenericType%2A> を呼び出し、型 `List<TFirst>` を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-134">To define this method, it is necessary to create the type `List<TFirst>` by calling <xref:System.Type.MakeGenericType%2A> on the generic type definition, `List<T>`.</span></span> <span data-ttu-id="ce01a-135">(`typeof` 演算子 (Visual Basic の場合は `GetType`) を利用してジェネリック型の定義を取得するとき、`T` が省略されます。)パラメーター型は <xref:System.Type.MakeArrayType%2A> メソッドを利用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-135">(The `T` is omitted when you use the `typeof` operator (`GetType` in Visual Basic) to get the generic type definition.) The parameter type is created by using the <xref:System.Type.MakeArrayType%2A> method.</span></span>  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. <span data-ttu-id="ce01a-136">メソッド本体を出力します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-136">Emit the method body.</span></span> <span data-ttu-id="ce01a-137">メソッド本体は 3 つのオペコードで構成されます。それらのオペコードにより、入力配列をスタックにロードし、`IEnumerable<TFirst>` (入力要素をリストに入れるためのあらゆる作業を行う) を受け取る `List<TFirst>` コンストラクターを呼び出して戻る (スタックに新しい <xref:System.Collections.Generic.List%601> オブジェクトを残す) という動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-137">The method body consists of three opcodes that load the input array onto the stack, call the `List<TFirst>` constructor that takes `IEnumerable<TFirst>` (which does all the work of putting the input elements into the list), and return (leaving the new <xref:System.Collections.Generic.List%601> object on the stack).</span></span> <span data-ttu-id="ce01a-138">このコードの出力の難しい部分は、コンストラクターの取得です。</span><span class="sxs-lookup"><span data-stu-id="ce01a-138">The difficult part of emitting this code is getting the constructor.</span></span>  
  
     <span data-ttu-id="ce01a-139"><xref:System.Type.GetConstructor%2A> メソッドは <xref:System.Reflection.Emit.GenericTypeParameterBuilder> ではサポートされていません。そのため、`List<TFirst>` のコンストラクターを直接取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce01a-139">The <xref:System.Type.GetConstructor%2A> method is not supported on a <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, so it is not possible to get the constructor of `List<TFirst>` directly.</span></span> <span data-ttu-id="ce01a-140">最初に、ジェネリック型定義 `List<T>` のコンストラクターを取得し、`List<TFirst>` の該当コンストラクターにそれを変換するメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-140">First, it is necessary to get the constructor of the generic type definition `List<T>` and then to call a method that converts it to the corresponding constructor of `List<TFirst>`.</span></span>  
  
     <span data-ttu-id="ce01a-141">このコード例で使用されているコンストラクターでは `IEnumerable<T>` が受け取られています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-141">The constructor used for this code example takes an `IEnumerable<T>`.</span></span> <span data-ttu-id="ce01a-142">ただし、これは <xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスのジェネリック型定義ではありません。`IEnumerable<T>` の型パラメーター `T` に対して `List<T>` の型パラメーター `T` を代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-142">Note, however, that this is not the generic type definition of the <xref:System.Collections.Generic.IEnumerable%601> generic interface; instead, the type parameter `T` from `List<T>` must be substituted for the type parameter `T` of `IEnumerable<T>`.</span></span> <span data-ttu-id="ce01a-143">(これが紛らわしく見えるのは、いずれの型にも `T` という名前の型パラメーターが与えられているためです。</span><span class="sxs-lookup"><span data-stu-id="ce01a-143">(This seems confusing only because both types have type parameters named `T`.</span></span> <span data-ttu-id="ce01a-144">そのため、このコード例では `TFirst` と `TSecond` という名前が使用されています。)コンストラクター引数の型を取得するには、ジェネリック型定義 `IEnumerable<T>` で始め、<xref:System.Type.MakeGenericType%2A> を呼び出します (この呼び出しでは、最初のジェネリック型パラメーターを `List<T>` にします)。</span><span class="sxs-lookup"><span data-stu-id="ce01a-144">That is why this code example uses the names `TFirst` and `TSecond`.) To get the type of the constructor argument, start with the generic type definition `IEnumerable<T>` and call <xref:System.Type.MakeGenericType%2A> with the first generic type parameter of `List<T>`.</span></span> <span data-ttu-id="ce01a-145">コンストラクター引数リストは配列として渡す必要があります。この例では引数が 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="ce01a-145">The constructor argument list must be passed as an array, with just one argument in this case.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ce01a-146">C# で `typeof` 演算子を使用するときは `IEnumerable(Of )` として、または Visual Basic で `GetType` 演算子を使用するときは `IEnumerable<>` としてジェネリック型定義が表されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-146">The generic type definition is expressed as `IEnumerable<>` when you use the `typeof` operator in C#, or `IEnumerable(Of )` when you use the `GetType` operator in Visual Basic.</span></span>  
  
     <span data-ttu-id="ce01a-147">これで、ジェネリック型定義で <xref:System.Type.GetConstructor%2A> を呼び出し、`List<T>` のコンストラクターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-147">Now it is possible to get the constructor of `List<T>` by calling <xref:System.Type.GetConstructor%2A> on the generic type definition.</span></span> <span data-ttu-id="ce01a-148">このコンストラクターを `List<TFirst>` の該当コンストラクターに変換するために、`List<T>` から静的 <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> メソッドに `List<TFirst>` とコンストラクターを渡します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-148">To convert this constructor to the corresponding constructor of `List<TFirst>`, pass `List<TFirst>` and the constructor from `List<T>` to the static <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> method.</span></span>  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. <span data-ttu-id="ce01a-149">型を作成し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-149">Create the type and save the file.</span></span>  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. <span data-ttu-id="ce01a-150">メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-150">Invoke the method.</span></span> <span data-ttu-id="ce01a-151">`ExampleMethod` はジェネリックではありませんが、それが属する型がジェネリックです。そのため、呼び出しが可能な <xref:System.Reflection.MethodInfo> を取得するには、`Sample` の型定義から、構成された型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce01a-151">`ExampleMethod` is not generic, but the type it belongs to is generic, so in order to get a <xref:System.Reflection.MethodInfo> that can be invoked it is necessary to create a constructed type from the type definition for `Sample`.</span></span> <span data-ttu-id="ce01a-152">この構成された型は `TFirst` の制約を満たす `Example` クラスを使用します。それが参照型であり、既定のパラメーターなしのコンストラクターが与えられているためです。また、`TSecond` の制約を満たす `ExampleDerived` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ce01a-152">The constructed type uses the `Example` class, which satisfies the constraints on `TFirst` because it is a reference type and has a default parameterless constructor, and the `ExampleDerived` class which satisfies the constraints on `TSecond`.</span></span> <span data-ttu-id="ce01a-153">(`ExampleDerived` のコードはサンプル コード セクションで確認できます。)これら 2 つの型が <xref:System.Type.MakeGenericType%2A> に渡され、構成された型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-153">(The code for `ExampleDerived` can be found in the example code section.) These two types are passed to <xref:System.Type.MakeGenericType%2A> to create the constructed type.</span></span> <span data-ttu-id="ce01a-154">その後、<xref:System.Type.GetMethod%2A> メソッドを利用して <xref:System.Reflection.MethodInfo> が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-154">The <xref:System.Reflection.MethodInfo> is then obtained using the <xref:System.Type.GetMethod%2A> method.</span></span>  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. <span data-ttu-id="ce01a-155">次のコードでは、`Example` オブジェクトの配列が作成され、呼び出すメソッドの引数を表す型 <xref:System.Object> の配列にその配列が置かれ、<xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-155">The following code creates an array of `Example` objects, places that array in an array of type <xref:System.Object> representing the arguments of the method to be invoked, and passes them to the <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> method.</span></span> <span data-ttu-id="ce01a-156"><xref:System.Reflection.MethodBase.Invoke%2A> メソッドの最初の引数は null 参照です。メソッドが `static` であるためです。</span><span class="sxs-lookup"><span data-stu-id="ce01a-156">The first argument of the <xref:System.Reflection.MethodBase.Invoke%2A> method is a null reference because the method is `static`.</span></span>  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="ce01a-157">例</span><span class="sxs-lookup"><span data-stu-id="ce01a-157">Example</span></span>  

 <span data-ttu-id="ce01a-158">次のコード例では、`Sample` という名前のクラス、基底クラス、2 つのインターフェイスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="ce01a-158">The following code example defines a class named `Sample`, along with a base class and two interfaces.</span></span> <span data-ttu-id="ce01a-159">このプログラムでは、`Sample` の 2 つのジェネリック型パラメーターが定義され、ジェネリック型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-159">The program defines two generic type parameters for `Sample`, turning it into a generic type.</span></span> <span data-ttu-id="ce01a-160">型をジェネリックにするのは、型パラメーターだけです。</span><span class="sxs-lookup"><span data-stu-id="ce01a-160">Type parameters are the only thing that makes a type generic.</span></span> <span data-ttu-id="ce01a-161">このプログラムではそれを、型パラメーターの定義の前後にテスト メッセージが表示されていることで確認できます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-161">The program shows this by displaying a test message before and after the definition of the type parameters.</span></span>  
  
 <span data-ttu-id="ce01a-162">型パラメーター `TSecond` は、基底クラスとインターフェイスを利用し、クラスとインターフェイスの制約を示すために使用されます。型パラメーター `TFirst` は特殊な制約を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-162">The type parameter `TSecond` is used to demonstrate class and interface constraints, using the base class and interfaces, and the type parameter `TFirst` is used to demonstrate special constraints.</span></span>  
  
 <span data-ttu-id="ce01a-163">このコード例では、フィールド型とメソッドのパラメーター/戻り値の型に対し、クラスの型パラメーターを利用してフィールドとメソッドが定義されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-163">The code example defines a field and a method using the class's type parameters for the field type and for the parameter and return type of the method.</span></span>  
  
 <span data-ttu-id="ce01a-164">`Sample` クラスの作成後、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-164">After the `Sample` class has been created, the method is invoked.</span></span>  
  
 <span data-ttu-id="ce01a-165">このプログラムには、ジェネリック型に関する情報を一覧表示するメソッドと、ある型パラメーターに対する特殊な制約を一覧表示するメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-165">The program includes a method that lists information about a generic type, and a method that lists the special constraints on a type parameter.</span></span> <span data-ttu-id="ce01a-166">完成した `Sample` クラスに関する情報の表示にこれらのメソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-166">These methods are used to display information about the finished `Sample` class.</span></span>  
  
 <span data-ttu-id="ce01a-167">このプログラムでは、完成したモジュールが `GenericEmitExample1.dll` としてディスクに保存されます。そのため、[Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) で開き、`Sample` クラスの MSIL を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ce01a-167">The program saves the finished module to disk as `GenericEmitExample1.dll`, so you can open it with the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) and examine the MSIL for the `Sample` class.</span></span>  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ce01a-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce01a-168">See also</span></span>

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- <span data-ttu-id="ce01a-169">[リフレクション出力の使用](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce01a-169">[Using Reflection Emit](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span></span>
- <span data-ttu-id="ce01a-170">[リフレクション出力による動的アセンブリのシナリオ](/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce01a-170">[Reflection Emit Dynamic Assembly Scenarios](/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))</span></span>
