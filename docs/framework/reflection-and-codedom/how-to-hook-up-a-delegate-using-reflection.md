---
title: '方法: リフレクションを使用してデリゲートをフックする'
description: .NET のリフレクションを使用してデリゲートをフックする方法について確認します。 リフレクションを介して必要な型を取得することで、既存のメソッドをイベントに接続します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: 9a92afd1c2aeadeb0cf7bc1e626b5bd1fb3cecea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263426"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="2771c-104">方法: リフレクションを使用してデリゲートをフックする</span><span class="sxs-lookup"><span data-stu-id="2771c-104">How to: Hook Up a Delegate Using Reflection</span></span>

<span data-ttu-id="2771c-105">リフレクションを使用して、アセンブリを読み込んで実行する場合、C# の `+=` 演算子や Visual Basic の [AddHandler ステートメント](../../visual-basic/language-reference/statements/addhandler-statement.md)のような言語機能を使用してイベントをフックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2771c-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="2771c-106">次の手順では、必要なすべての型をリフレクションによって取得することで、既存のメソッドをイベントにフックする方法と、リフレクション出力を使用して動的メソッドを作成し、それをイベントにフックする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2771c-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2771c-107">イベント処理デリゲートをフックするもう 1 つの方法については、<xref:System.Reflection.EventInfo.AddEventHandler%2A> クラスの <xref:System.Reflection.EventInfo> メソッドのコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2771c-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="2771c-108">リフレクションを使用してデリゲートをフックするには</span><span class="sxs-lookup"><span data-stu-id="2771c-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="2771c-109">イベントを発生させる型を格納するアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2771c-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="2771c-110">通常、アセンブリは <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドで読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2771c-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2771c-111">この例を簡単にするために、現在のアセンブリの派生フォームを使用します。したがって、<xref:System.Reflection.Assembly.GetExecutingAssembly%2A> メソッドを使用して、現在のアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2771c-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="2771c-112">型を表す <xref:System.Type> オブジェクトを取得し、型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2771c-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="2771c-113">このフォームはパラメーターなしのコンストラクターを持つため、次のコードでは <xref:System.Activator.CreateInstance%28System.Type%29> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2771c-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="2771c-114">作成する型がパラメーターなしのコンストラクターを持たない場合に使用できる、<xref:System.Activator.CreateInstance%2A> メソッドのその他のオーバーロードがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="2771c-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="2771c-115">アセンブリについては何もわからないという架空の状態を保つために、新しいインスタンスは <xref:System.Object> 型として格納されます</span><span class="sxs-lookup"><span data-stu-id="2771c-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="2771c-116">(リフレクションを使用すると、事前に型名がわからなくてもアセンブリ内の型を取得できます)。</span><span class="sxs-lookup"><span data-stu-id="2771c-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="2771c-117">イベントを表す <xref:System.Reflection.EventInfo> オブジェクトを取得し、<xref:System.Reflection.EventInfo.EventHandlerType%2A> プロパティを使用して、イベントの処理に使用するデリゲートの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="2771c-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="2771c-118">次のコードでは、<xref:System.Reflection.EventInfo> イベントの <xref:System.Windows.Forms.Control.Click> が取得されます。</span><span class="sxs-lookup"><span data-stu-id="2771c-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="2771c-119">イベントを処理するメソッドを表す <xref:System.Reflection.MethodInfo> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="2771c-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="2771c-120">このトピックで後ほど示す「使用例」セクションの完全なプログラム コードには、<xref:System.EventHandler> イベントを処理する <xref:System.Windows.Forms.Control.Click> デリゲートのシグネチャと一致するメソッドが含まれていますが、実行時に動的メソッドを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2771c-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="2771c-121">詳細については、動的メソッドを使用して実行時にイベント ハンドラーを生成する場合の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2771c-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="2771c-122"><xref:System.Delegate.CreateDelegate%2A> メソッドを使用して、デリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2771c-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="2771c-123">このメソッドは static (Visual Basic では `Shared`) であるため、デリゲート型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2771c-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="2771c-124"><xref:System.Delegate.CreateDelegate%2A> を受け取る <xref:System.Reflection.MethodInfo> のオーバーロードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2771c-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="2771c-125">`add` アクセサー メソッドを取得し、このメソッドを呼び出してイベントをフックします。</span><span class="sxs-lookup"><span data-stu-id="2771c-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="2771c-126">すべてのイベントに、`add` アクセサーと `remove` アクセサーがあります。これらのアクセサーは高水準言語の構文によって隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="2771c-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="2771c-127">たとえば、C# では `+=` 演算子を使用してイベントをフックし、Visual Basic では [AddHandler ステートメント](../../visual-basic/language-reference/statements/addhandler-statement.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2771c-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="2771c-128">次のコードでは、`add` イベントの <xref:System.Windows.Forms.Control.Click> アクセサーを取得し、遅延バインディングによってこれを呼び出して、デリゲート インスタンスに渡します。</span><span class="sxs-lookup"><span data-stu-id="2771c-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="2771c-129">引数は配列として渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2771c-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="2771c-130">イベントをテストします。</span><span class="sxs-lookup"><span data-stu-id="2771c-130">Test the event.</span></span> <span data-ttu-id="2771c-131">次のコードで、このコード例で定義したフォームを表示します。</span><span class="sxs-lookup"><span data-stu-id="2771c-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="2771c-132">フォームをクリックすると、イベント ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2771c-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>

### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="2771c-133">動的メソッドを使用して実行時にイベント ハンドラーを生成するには</span><span class="sxs-lookup"><span data-stu-id="2771c-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="2771c-134">軽量の動的メソッドとリフレクション出力を使用して、イベント ハンドラーのメソッドを実行時に生成できます。</span><span class="sxs-lookup"><span data-stu-id="2771c-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="2771c-135">イベント ハンドラーを作成するには、デリゲートの戻り値の型とパラメーターの型が必要です。</span><span class="sxs-lookup"><span data-stu-id="2771c-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="2771c-136">これらは、デリゲートの `Invoke` メソッドを調べることによって入手できます。</span><span class="sxs-lookup"><span data-stu-id="2771c-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="2771c-137">次のコードでは、`GetDelegateReturnType` メソッドと `GetDelegateParameterTypes` メソッドを使用して、この情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2771c-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="2771c-138">これらのメソッドのコードは、このトピックで後ほど示す「使用例」セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="2771c-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="2771c-139"><xref:System.Reflection.Emit.DynamicMethod> に名前を付ける必要はないため、空の文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2771c-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="2771c-140">次のコードでは、最後の引数が動的メソッドを現在の型に関連付け、デリゲートが `Example` クラスのすべてのパブリック メンバーとプライベート メンバーにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2771c-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="2771c-141">メソッド本体を生成します。</span><span class="sxs-lookup"><span data-stu-id="2771c-141">Generate a method body.</span></span> <span data-ttu-id="2771c-142">このメソッドは文字列を読み込み、文字列を受け取る <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> メソッドのオーバーロードを呼び出します。次に、戻り値をスタックからポップし (ハンドラーには戻り値の型がないため)、返されます。</span><span class="sxs-lookup"><span data-stu-id="2771c-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="2771c-143">動的メソッドの出力の詳細については、「[方法: 動的メソッドを定義および実行する](how-to-define-and-execute-dynamic-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2771c-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="2771c-144"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを呼び出して、動的メソッドを完了します。</span><span class="sxs-lookup"><span data-stu-id="2771c-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="2771c-145">`add` アクセサーを使用して、イベントの呼び出しリストにデリゲートを追加します。</span><span class="sxs-lookup"><span data-stu-id="2771c-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="2771c-146">イベントをテストします。</span><span class="sxs-lookup"><span data-stu-id="2771c-146">Test the event.</span></span> <span data-ttu-id="2771c-147">次のコードでは、このコード例で定義したフォームを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2771c-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="2771c-148">フォームをクリックすると、定義済みイベント ハンドラーと出力されたイベント ハンドラーの両方が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2771c-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="2771c-149">例</span><span class="sxs-lookup"><span data-stu-id="2771c-149">Example</span></span>  

 <span data-ttu-id="2771c-150">リフレクションを使用して既存のメソッドをイベントにフックする方法、および <xref:System.Reflection.Emit.DynamicMethod> クラスを使用してメソッドを実行時に出力し、イベントにフックする方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2771c-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2771c-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="2771c-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="2771c-152">方法: 動的メソッドを定義および実行する</span><span class="sxs-lookup"><span data-stu-id="2771c-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="2771c-153">リフレクション</span><span class="sxs-lookup"><span data-stu-id="2771c-153">Reflection</span></span>](reflection.md)
