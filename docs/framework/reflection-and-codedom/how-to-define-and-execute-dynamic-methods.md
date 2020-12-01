---
title: '方法: 動的メソッドを定義および実行する'
description: .NET で動的メソッドを定義および実行する方法について確認します。 単純な動的メソッド、およびクラスのインスタンスにバインドされる動的メソッドの例について確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: 1ea15149ea72c3c422251abefb5a1008cc496f2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263452"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="d10be-104">方法: 動的メソッドを定義および実行する</span><span class="sxs-lookup"><span data-stu-id="d10be-104">How to: Define and Execute Dynamic Methods</span></span>

<span data-ttu-id="d10be-105">ここでは、単純な動的メソッドと、クラスのインスタンスにバインドされた動的メソッドを定義し、実行する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d10be-105">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="d10be-106">動的メソッドの詳細については、<xref:System.Reflection.Emit.DynamicMethod> クラスに関するトピックと「[Reflection Emit Dynamic Method Scenarios](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))」(リフレクション出力による動的メソッドのシナリオ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d10be-106">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="d10be-107">動的メソッドを定義および実行するには</span><span class="sxs-lookup"><span data-stu-id="d10be-107">To define and execute a dynamic method</span></span>  
  
1. <span data-ttu-id="d10be-108">メソッドを実行するために、デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d10be-108">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="d10be-109">汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。</span><span class="sxs-lookup"><span data-stu-id="d10be-109">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="d10be-110">次のコードでは、`SquareIt` メソッドで使用できる 2 つのデリゲート型 (1 つはジェネリック) を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d10be-110">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. <span data-ttu-id="d10be-111">動的メソッドのパラメーターの型を指定する配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-111">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="d10be-112">この例では、唯一のパラメーターが `int` (Visual Basic では `Integer`) であるため、配列には要素は 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="d10be-112">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. <span data-ttu-id="d10be-113"><xref:System.Reflection.Emit.DynamicMethod> を作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-113">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="d10be-114">この例では、メソッドの名前は `SquareIt` です。</span><span class="sxs-lookup"><span data-stu-id="d10be-114">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d10be-115">動的メソッドに名前を付ける必要はありません。動的メソッドは名前で呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="d10be-115">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="d10be-116">複数の動的メソッドに同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d10be-116">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="d10be-117">ただし、名前は呼び出し履歴に表示されるため、デバッグの際に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="d10be-117">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="d10be-118">戻り値の型は、`long` として指定します。</span><span class="sxs-lookup"><span data-stu-id="d10be-118">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="d10be-119">プログラム例を格納する `Example` クラスを含むモジュールにメソッドを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="d10be-119">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="d10be-120">読み込むモジュールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d10be-120">Any loaded module could be specified.</span></span> <span data-ttu-id="d10be-121">動的メソッドは、モジュール レベルの `static` メソッド (Visual Basic では `Shared`) と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="d10be-121">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. <span data-ttu-id="d10be-122">メソッド本体を出力します。</span><span class="sxs-lookup"><span data-stu-id="d10be-122">Emit the method body.</span></span> <span data-ttu-id="d10be-123">この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL (Microsoft Intermediate Language) を出力します。</span><span class="sxs-lookup"><span data-stu-id="d10be-123">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d10be-124">また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="d10be-124">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="d10be-125">この例の MSIL は、`int` である引数をスタックに読み込み、これを `long` に変換します。次に、`long` を複製し、2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="d10be-125">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="d10be-126">これにより、スタックには 2 乗された結果が残され、メソッドで実行する必要のあるすべてが返されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-126">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. <span data-ttu-id="d10be-127"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを呼び出して、動的メソッドを表す (手順 1 で宣言した) デリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-127">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="d10be-128">デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても (MSIL の追加など) 無視されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-128">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="d10be-129">次のコードでは、汎用デリゲートを使用して、デリゲートを作成し呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d10be-129">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="d10be-130">オブジェクトにバインドされた動的メソッドを定義および実行するには</span><span class="sxs-lookup"><span data-stu-id="d10be-130">To define and execute a dynamic method that is bound to an object</span></span>  
  
1. <span data-ttu-id="d10be-131">メソッドを実行するために、デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d10be-131">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="d10be-132">汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。</span><span class="sxs-lookup"><span data-stu-id="d10be-132">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="d10be-133">次のコードでは、1 つのパラメーターと戻り値を持つ任意のメソッド、またはデリゲートがオブジェクトにバインドされている場合は 2 つのパラメーターと戻り値を持つメソッドの実行に使用できる汎用デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d10be-133">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. <span data-ttu-id="d10be-134">動的メソッドのパラメーターの型を指定する配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-134">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="d10be-135">メソッドを表すデリゲートをオブジェクトにバインドする場合、1 つ目のパラメーターは、デリゲートのバインド先となる型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d10be-135">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="d10be-136">この例では、`Example` 型と `int` 型 (Visual Basic では `Integer`) の 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="d10be-136">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. <span data-ttu-id="d10be-137"><xref:System.Reflection.Emit.DynamicMethod> を作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-137">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="d10be-138">この例では、メソッドに名前はありません。</span><span class="sxs-lookup"><span data-stu-id="d10be-138">In this example the method has no name.</span></span> <span data-ttu-id="d10be-139">戻り値の型は、`int` (Visual Basic では `Integer`) として指定します。</span><span class="sxs-lookup"><span data-stu-id="d10be-139">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="d10be-140">このメソッドは、`Example` クラスのプライベート メンバーとプロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d10be-140">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. <span data-ttu-id="d10be-141">メソッド本体を出力します。</span><span class="sxs-lookup"><span data-stu-id="d10be-141">Emit the method body.</span></span> <span data-ttu-id="d10be-142">この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL (Microsoft Intermediate Language) を出力します。</span><span class="sxs-lookup"><span data-stu-id="d10be-142">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d10be-143">また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="d10be-143">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="d10be-144">この例の MSIL は、`Example` クラスのインスタンスである 1 つ目の引数を読み込み、この引数を使用して、`int` 型のプライベート インスタンス フィールドの値を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d10be-144">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="d10be-145">2 つ目の引数が読み込まれ、この 2 つの数値が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-145">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="d10be-146">この結果が `int` よりも大きい場合、値は切り捨てられ、最上位ビットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-146">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="d10be-147">戻り値がスタックに配置されて、メソッドが返されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-147">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. <span data-ttu-id="d10be-148"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> メソッド オーバーロードを呼び出して、動的メソッドを表す (手順 1 で宣言した) デリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d10be-148">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="d10be-149">デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても (MSIL の追加など) 無視されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-149">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d10be-150"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを複数回呼び出して、対象の型の他のインスタンスにバインドされたデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d10be-150">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="d10be-151">次のコードでは、プライベート テスト フィールドが 42 に設定された `Example` クラスの新しいインスタンスにメソッドをバインドします。</span><span class="sxs-lookup"><span data-stu-id="d10be-151">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="d10be-152">つまり、デリゲートが呼び出されるたびに、`Example` のインスタンスがメソッドの 1 つ目のパラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-152">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="d10be-153">メソッドの 1 つ目のパラメーターは、常に `Example` のインスタンスを受け取るため、`OneParameter` デリゲートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-153">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="d10be-154">デリゲートの呼び出し時には、2 つ目のパラメーターだけが必要となります。</span><span class="sxs-lookup"><span data-stu-id="d10be-154">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="d10be-155">例</span><span class="sxs-lookup"><span data-stu-id="d10be-155">Example</span></span>  

 <span data-ttu-id="d10be-156">単純な動的メソッドおよびクラスのインスタンスにバインドされた動的メソッドを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="d10be-156">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="d10be-157">この単純な動的メソッドは、32 ビット整数である引数を 1 つ受け取り、その整数の 2 乗を 64 ビットで返します。</span><span class="sxs-lookup"><span data-stu-id="d10be-157">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="d10be-158">汎用デリゲートを使用して、メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d10be-158">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="d10be-159">2 つ目の動的メソッドには、`Example` 型と `int` 型 (Visual Basic では `Integer`) の 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="d10be-159">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="d10be-160">動的メソッドが作成されると、`int` 型の引数を 1 つ持つ汎用デリゲートを使用して、`Example` のインスタンスにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="d10be-160">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="d10be-161">メソッドの 1 つ目のパラメーターは、常に `Example` のバインドされたインスタンスを受け取るため、デリゲートは `Example` 型の引数を持ちません。</span><span class="sxs-lookup"><span data-stu-id="d10be-161">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="d10be-162">デリゲートの呼び出し時には、`int` 型の引数だけが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d10be-162">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="d10be-163">動的メソッドは、`Example` クラスのプライベート フィールドにアクセスし、プライベート フィールドと `int` 型の引数の積を返します。</span><span class="sxs-lookup"><span data-stu-id="d10be-163">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="d10be-164">メソッドの実行に使用できるデリゲートを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d10be-164">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d10be-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="d10be-165">See also</span></span>

- <xref:System.Reflection.Emit.DynamicMethod>
- <span data-ttu-id="d10be-166">[リフレクション出力の使用](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d10be-166">[Using Reflection Emit](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span></span>
- <span data-ttu-id="d10be-167">[リフレクション出力による動的メソッドのシナリオ](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d10be-167">[Reflection Emit Dynamic Method Scenarios](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span></span>
