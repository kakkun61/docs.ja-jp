---
title: '方法: リフレクションを使用してジェネリック型をチェックおよびインスタンス化する'
description: リフレクションを使用してジェネリック型をチェックおよびインスタンス化する方法について確認します。 IsGenericType プロパティ、IsGenericParameter プロパティ、GenericParameterPosition プロパティを使用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: 34efca4a26b0ab3739d19b793237532ec9f4f15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263439"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="d455d-104">方法: リフレクションを使用してジェネリック型をチェックおよびインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="d455d-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>

<span data-ttu-id="d455d-105">ジェネリック型の情報は、他の型の情報と同じ方法で取得します。つまり、ジェネリック型を表す <xref:System.Type> オブジェクトをチェックすることによって取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="d455d-106">根本的な違いとして、ジェネリック型には、そのジェネリック型パラメーターを表す <xref:System.Type> オブジェクトの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d455d-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="d455d-107">このセクションでは、まず、ジェネリック型をチェックする手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="d455d-108">ジェネリック型の定義の型パラメーターに型引数をバインドすることにより、構築された型を表す <xref:System.Type> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d455d-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="d455d-109">2 番目の手順でこの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="d455d-110">ジェネリック型とその型パラメーターを確認するには</span><span class="sxs-lookup"><span data-stu-id="d455d-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="d455d-111">ジェネリック型を表す <xref:System.Type> のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="d455d-112">次のコードでは、C# の `typeof` 演算子 (Visual Basic では `GetType`、Visual C++ では `typeid`) を使用して型を取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="d455d-113"><xref:System.Type> オブジェクトを取得する他の方法については、<xref:System.Type> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d455d-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="d455d-114">この手順では、これ以降、型は `t` という名前のメソッド パラメーターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d455d-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="d455d-115"><xref:System.Type.IsGenericType%2A> プロパティを使用して、型がジェネリックかどうかを確認し、<xref:System.Type.IsGenericTypeDefinition%2A> プロパティを使用して型がジェネリック型の定義かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d455d-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="d455d-116"><xref:System.Type.GetGenericArguments%2A> メソッドを使用して、ジェネリック型引数が格納された配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="d455d-117">各型引数について、<xref:System.Type.IsGenericParameter%2A> プロパティを使用して、その型引数が型パラメーター (ジェネリック型定義の型パラメーターなど) であるか、型パラメーターに指定された型 (構築された型の型パラメーターなど) であるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d455d-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="d455d-118">型システムでは、ジェネリック型パラメーターは、通常の型と同様に <xref:System.Type> のインスタンスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="d455d-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="d455d-119">次のコードでは、ジェネリック型パラメーターを表す <xref:System.Type> オブジェクトの名前とパラメーター位置を表示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="d455d-120">パラメーター位置はここでは重要な情報ではありませんが、別のジェネリック型の型引数として使用されている型パラメーターをチェックする場合に重要となります。</span><span class="sxs-lookup"><span data-stu-id="d455d-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="d455d-121"><xref:System.Type.GetGenericParameterConstraints%2A> メソッドを使用して、ジェネリック型パラメーターの基本型の制約とインターフェイスの制約を確認し、単一の配列内のすべての制約を取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="d455d-122">制約は、特定の順序であるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="d455d-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="d455d-123"><xref:System.Type.GenericParameterAttributes%2A> プロパティを使用して、型パラメーターの特殊な制約 (参照型であることが必要など) を確認します。</span><span class="sxs-lookup"><span data-stu-id="d455d-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="d455d-124">このプロパティには、分散を表す値も含まれています。次のコードに示すように、この値にはマスクを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d455d-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="d455d-125">特殊な制約の属性はフラグであり、特殊な制約がないことを表すフラグ (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) と同じフラグが、共変性や反変性がないことも表します。</span><span class="sxs-lookup"><span data-stu-id="d455d-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="d455d-126">したがって、これらの条件のいずれかを調べるには、適切なマスクを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d455d-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="d455d-127">ここでは、<xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> を使用して、特殊な制約のフラグを切り分けます。</span><span class="sxs-lookup"><span data-stu-id="d455d-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="d455d-128">ジェネリック型のインスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="d455d-128">Constructing an Instance of a Generic Type</span></span>  

 <span data-ttu-id="d455d-129">ジェネリック型はテンプレートに似ています。</span><span class="sxs-lookup"><span data-stu-id="d455d-129">A generic type is like a template.</span></span> <span data-ttu-id="d455d-130">ジェネリック型パラメーターの実際の型を指定しない限り、インスタンスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d455d-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="d455d-131">リフレクションを使用して実行時にこれを行うには、<xref:System.Type.MakeGenericType%2A> メソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="d455d-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="d455d-132">ジェネリック型のインスタンスを構築するには</span><span class="sxs-lookup"><span data-stu-id="d455d-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="d455d-133">ジェネリック型を表す <xref:System.Type> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d455d-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="d455d-134">次のコードでは、2 とおりの方法でジェネリック型 <xref:System.Collections.Generic.Dictionary%602> を取得します。型を示す文字列を指定して <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> メソッド オーバーロードを使用する方法と、構築された型 `Dictionary\<String, Example>` (Visual Basic では `Dictionary(Of String, Example)`) で <xref:System.Type.GetGenericTypeDefinition%2A> メソッドを呼び出す方法です。</span><span class="sxs-lookup"><span data-stu-id="d455d-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="d455d-135"><xref:System.Type.MakeGenericType%2A> メソッドには、ジェネリック型の定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="d455d-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="d455d-136">型引数の配列を構築して、型パラメーターと置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d455d-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="d455d-137">配列には、型パラメーター リストに表示される順序と同じ順序で、正確な数の <xref:System.Type> オブジェクトを格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d455d-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="d455d-138">この場合、キー (最初の型パラメーター) の型は <xref:System.String> であり、ディクショナリの値は `Example` というクラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="d455d-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="d455d-139"><xref:System.Type.MakeGenericType%2A> メソッドを呼び出して型引数を型パラメーターにバインドし、型を構築します。</span><span class="sxs-lookup"><span data-stu-id="d455d-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="d455d-140"><xref:System.Activator.CreateInstance%28System.Type%29> メソッド オーバーロードを使用して、構築された型のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d455d-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="d455d-141">次のコードでは、作成された `Dictionary<String, Example>` オブジェクトに、`Example` クラスの 2 つのインスタンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="d455d-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="d455d-142">例</span><span class="sxs-lookup"><span data-stu-id="d455d-142">Example</span></span>  

 <span data-ttu-id="d455d-143">`DisplayGenericType` メソッドを定義して、コードで使用されているジェネリック型の定義と構築された型をチェックし、この情報を表示するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="d455d-144">`DisplayGenericType` メソッドは、<xref:System.Type.IsGenericType%2A>、<xref:System.Type.IsGenericParameter%2A>、<xref:System.Type.GenericParameterPosition%2A> の各プロパティと <xref:System.Type.GetGenericArguments%2A> メソッドの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="d455d-145">この例では、`DisplayGenericParameter` メソッドも定義してジェネリック型パラメーターをチェックし、その制約を表示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="d455d-146">このコード例では、型パラメーターの制約を示すジェネリック型を含む一連のテスト用の型を定義し、これらの型の情報を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="d455d-147">この例では、型引数の配列を作成し、<xref:System.Type.MakeGenericType%2A> メソッドを呼び出して、<xref:System.Collections.Generic.Dictionary%602> クラスから型を構築します。</span><span class="sxs-lookup"><span data-stu-id="d455d-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="d455d-148">プログラムでは、<xref:System.Type.MakeGenericType%2A> を使用して構築された <xref:System.Type> オブジェクトと、`typeof` (Visual Basic では `GetType`) を使用して取得した <xref:System.Type> オブジェクトを比較し、これらが同じであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d455d-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="d455d-149">同様に、<xref:System.Type.GetGenericTypeDefinition%2A> メソッドを使用して構築された型のジェネリック型の定義を取得し、<xref:System.Collections.Generic.Dictionary%602> クラスを表す <xref:System.Type> オブジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="d455d-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d455d-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="d455d-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="d455d-151">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="d455d-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="d455d-152">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="d455d-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="d455d-153">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="d455d-153">Generics</span></span>](../../standard/generics/index.md)
