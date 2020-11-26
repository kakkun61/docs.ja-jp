---
title: デバッガー表示属性によるデバッグ機能の拡張
description: .NET でのデバッガー表示属性の使用 .NET では、型の開発者は、デバッガーに表示されるときにどのような型を表示するかを指定することもできます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: 2e556358490409a0fa7b345c4454eb43cf607e32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244367"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="e13ce-103">デバッガー表示属性によるデバッグ機能の拡張</span><span class="sxs-lookup"><span data-stu-id="e13ce-103">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="e13ce-104">デバッガー表示属性は、型を指定し、その型の実行時の動作を最もよく理解している型の開発者が、デバッガーで表示されたときに、その型がどのように見えるかも指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e13ce-104">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="e13ce-105">さらに、`Target` プロパティを提供するデバッガー表示属性は、ソース コードの知識がなくても、ユーザーがアセンブリ レベルで適用することができます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-105">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="e13ce-106"><xref:System.Diagnostics.DebuggerDisplayAttribute> 属性は、デバッガーの変数ウィンドウで型やメンバーを表示する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-106">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="e13ce-107"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性は、デバッガーの変数ウィンドウにフィールドまたはプロパティを表示するかどうか、および表示方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-107">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="e13ce-108"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、型に対して代理の型 (プロキシ) を指定し、その型をデバッガー ウィンドウで表示する方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-108">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="e13ce-109">プロキシ (代理の型) を指定した変数を表示すると、元の型の代理としてプロキシがデバッガーの表示ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-109">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="e13ce-110">デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-110">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="e13ce-111">プライベート メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-111">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="e13ce-112">DebuggerDisplayAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="e13ce-112">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="e13ce-113"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> コンストラクターには引数が 1 つあり、それは、型のインスタンスの値列に表示される文字列です。</span><span class="sxs-lookup"><span data-stu-id="e13ce-113">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="e13ce-114">この文字列には、中かっこ ({ と }) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-114">This string can contain braces ({ and }).</span></span> <span data-ttu-id="e13ce-115">かっこ内のテキストは、式として評価されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-115">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="e13ce-116">たとえば、次の C# コードでは、`MyHashtable` のインスタンスのデバッガー表示を展開するプラス記号 (+) が選択された場合に、"Count = 4" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-116">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="e13ce-117">式で参照されるプロパティに適用される属性は処理されません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-117">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="e13ce-118">C# コンパイラでは、対象の型の現在のインスタンスへのこの参照に対し、暗黙的なアクセスのみを持つ一般的な式が許可されています。</span><span class="sxs-lookup"><span data-stu-id="e13ce-118">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="e13ce-119">この式は制限されており、エイリアス、ローカル、またはポインターに対するアクセスはありません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-119">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="e13ce-120">C# コードでは、対象となる型の現在のインスタンスのみの `this` ポインターに暗黙的にアクセスする一般的な式をかっこ内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-120">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="e13ce-121">たとえば、C# オブジェクトにオーバーライドされた `ToString()` がある場合、デバッガーはそのオーバーライドを呼び出し、標準の `{<typeName>}.` ではなく、その結果を表示します。したがって、オーバーライドされた `ToString()` がある場合、<xref:System.Diagnostics.DebuggerDisplayAttribute> を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-121">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="e13ce-122">両方を使用すると、<xref:System.Diagnostics.DebuggerDisplayAttribute> 属性が `ToString()` オーバーライドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-122">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="e13ce-123">DebuggerBrowsableAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="e13ce-123">Using the DebuggerBrowsableAttribute</span></span>

 <span data-ttu-id="e13ce-124"><xref:System.Diagnostics.DebuggerBrowsableAttribute> をフィールドまたはプロパティに適用して、デバッガー ウィンドウにフィールドまたはプロパティを表示する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-124">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="e13ce-125">この属性のコンストラクターは、次の状態のいずれかを指定する <xref:System.Diagnostics.DebuggerBrowsableState> 列挙値を 1 つ取得します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-125">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="e13ce-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> は、データ ウィンドウにメンバーが表示されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="e13ce-127">たとえば、この値をフィールドで <xref:System.Diagnostics.DebuggerBrowsableAttribute> に使用すると、そのフィールドが階層から削除され、型のインスタンスのプラス記号 (+) をクリックして囲む型を展開したときに、そのフィールドが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="e13ce-127">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="e13ce-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> は、メンバーが表示されますが、既定で展開されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="e13ce-129">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="e13ce-129">This is the default behavior.</span></span>

- <span data-ttu-id="e13ce-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> は、メンバー自体は表示されませんが、メンバーが配列またはコレクションである場合は、その構成オブジェクトが表示されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="e13ce-131">.NET Framework version 2.0 では、<xref:System.Diagnostics.DebuggerBrowsableAttribute> は Visual Basic でサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-131">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="e13ce-132">次のコード例は、<xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、それに続くプロパティがクラスのデバッグ ウィンドウに表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="e13ce-132">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="e13ce-133">DebuggerTypeProxy の使用</span><span class="sxs-lookup"><span data-stu-id="e13ce-133">Using the DebuggerTypeProxy</span></span>

 <span data-ttu-id="e13ce-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、型のデバッグ ビューを大幅かつ根本的に変更する必要があるものの、型そのものは変えない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-134">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="e13ce-135"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、開発者が型の表示を調整できるように、型の表示プロキシを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-135">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="e13ce-136"><xref:System.Diagnostics.DebuggerDisplayAttribute> と同様に、この属性は、アセンブリ レベルで使用できます。この場合、<xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> プロパティは、プロキシが使用される型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-136">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="e13ce-137">推奨される使用法は、この属性が、属性が適用される型の中で発生するプライベートの入れ子にされた型を指定することです。</span><span class="sxs-lookup"><span data-stu-id="e13ce-137">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="e13ce-138">型ビューアーをサポートする式エバリュエーターが、型が表示されるときに、この属性をチェックします。</span><span class="sxs-lookup"><span data-stu-id="e13ce-138">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="e13ce-139">属性が見つかると、式エバリュエーターは、属性が適用される型の代わりに表示プロキシ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-139">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="e13ce-140"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> が存在する場合は、デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-140">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="e13ce-141">プライベート メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-141">Private members are not displayed.</span></span> <span data-ttu-id="e13ce-142">データ ウィンドウの動作は、属性拡張ビューでは変更されません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-142">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="e13ce-143">不要なパフォーマンスの低下を避けるため、データ ウィンドウでユーザーが型の横にあるプラス記号 (+) をクリックするか、<xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性の適用により、オブジェクトが展開されるまで、表示プロキシの属性は処理されません。</span><span class="sxs-lookup"><span data-stu-id="e13ce-143">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="e13ce-144">そのため、表示型に属性を適用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e13ce-144">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="e13ce-145">属性は、表示型の本体内で適用でき、また適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e13ce-145">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="e13ce-146">次のコード例は、<xref:System.Diagnostics.DebuggerTypeProxyAttribute> を使用してデバッガーの表示プロキシとして使用する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e13ce-146">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="e13ce-147">例</span><span class="sxs-lookup"><span data-stu-id="e13ce-147">Example</span></span>

### <a name="description"></a><span data-ttu-id="e13ce-148">説明</span><span class="sxs-lookup"><span data-stu-id="e13ce-148">Description</span></span>

<span data-ttu-id="e13ce-149">次のコード例を Visual Studio で表示する <xref:System.Diagnostics.DebuggerDisplayAttribute> と、、、およびの各属性を適用した結果を確認でき <xref:System.Diagnostics.DebuggerBrowsableAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="e13ce-149">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="e13ce-150">コード</span><span class="sxs-lookup"><span data-stu-id="e13ce-150">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e13ce-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="e13ce-151">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
