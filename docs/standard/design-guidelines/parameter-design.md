---
title: パラメーターのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 707ae48be3f45d82ed3819f943dc5ba3743172f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828804"
---
# <a name="parameter-design"></a><span data-ttu-id="b2e8c-102">パラメーターのデザイン</span><span class="sxs-lookup"><span data-stu-id="b2e8c-102">Parameter Design</span></span>

<span data-ttu-id="b2e8c-103">このセクションでは、引数をチェックするためのガイドラインを含むセクションなど、パラメーターの設計に関する広範なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="b2e8c-104">また、「 [パラメーターの名前付け](naming-parameters.md)」で説明されているガイドラインを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="b2e8c-105">✔️は、メンバーが必要とする機能を提供する最小の派生パラメーター型を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="b2e8c-106">たとえば、コレクションを列挙し、各項目をコンソールに出力するメソッドを設計するとします。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="b2e8c-107">このようなメソッドは、などで <xref:System.Collections.IEnumerable> はなく、パラメーターとしてを受け取る必要があり <xref:System.Collections.ArrayList> <xref:System.Collections.IList> ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="b2e8c-108">❌ 予約済みのパラメーターは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="b2e8c-109">将来のバージョンでメンバーへの入力が増えると、新しいオーバーロードを追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="b2e8c-110">❌ ポインター、ポインターの配列、または多次元配列をパラメーターとして受け取るメソッドを公開することはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="b2e8c-111">ポインターと多次元配列は、適切に使用するのが比較的困難です。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="b2e8c-112">ほとんどの場合、これらの型をパラメーターとして使用しないように、Api を再設計することができます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="b2e8c-113">`out` `ref` オーバーロード間のパラメーターの順序に矛盾が生じる場合でも、すべてのパラメーター (パラメーター配列を除く) の後にすべてのパラメーターを配置する✔️ます (「[メンバーのオーバーロード](member-overloading.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="b2e8c-114">これらのパラメーターは、 `out` 余分な戻り値として表示できます。また、これらをまとめてグループ化することで、メソッドのシグネチャがわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="b2e8c-115">メンバーをオーバーライドする場合や、インターフェイスメンバーを実装する場合は、名前付けパラメーターで✔️の一貫性を保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="b2e8c-116">これにより、メソッド間の関係がより適切に伝えられます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-116">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="b2e8c-117">列挙型パラメーターとブール型パラメーターの選択</span><span class="sxs-lookup"><span data-stu-id="b2e8c-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="b2e8c-118">メンバーに複数のブール型パラメーターが含まれている場合は、列挙型を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="b2e8c-119">❌ 2つ以上の値を必要としないことが確実である場合を除き、ブール値は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="b2e8c-120">列挙型を使用すると、後で値を追加できるようになりますが、列挙型に値を追加することによるすべての影響に注意する必要があります。これについては、「 [Enum Design](enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="b2e8c-121">ブール型のプロパティを初期化するために単純に使用されるコンストラクターパラメーターにはブール値を使用することを✔️してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="b2e8c-122">引数の検証</span><span class="sxs-lookup"><span data-stu-id="b2e8c-122">Validating Arguments</span></span>
 <span data-ttu-id="b2e8c-123">✔️は、public、protected、または明示的に実装されたメンバーに渡される引数を検証します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="b2e8c-124"><xref:System.ArgumentException?displayProperty=nameWithType>検証が失敗した場合、またはそのサブクラスの1つをスローします。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="b2e8c-125">実際の検証は、必ずしもパブリックメンバーまたはプロテクトメンバーに対して行われる必要がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="b2e8c-126">これは、一部のプライベートまたは内部ルーチンの下位レベルで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="b2e8c-127">主な点は、エンドユーザーに公開されているすべての領域が、引数をチェックすることです。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="b2e8c-128"><xref:System.ArgumentNullException>null 引数が渡され、メンバーが null 引数をサポートしていない場合は、✔️スローされます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="b2e8c-129">✔️列挙型パラメーターを検証します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="b2e8c-130">Enum 引数が列挙型によって定義された範囲内にあると仮定しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="b2e8c-131">CLR では、列挙型で値が定義されていない場合でも、任意の整数値を列挙値にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="b2e8c-132">❌<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>Enum 範囲チェックには使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="b2e8c-133">✔️は、変更可能な引数が検証後に変更された可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="b2e8c-134">メンバーがセキュリティに依存している場合は、コピーを作成して、引数を検証して処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="b2e8c-135">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="b2e8c-135">Parameter Passing</span></span>
 <span data-ttu-id="b2e8c-136">フレームワークデザイナーの観点からは、パラメーターの3つの主要なグループ (値渡しのパラメーター、 `ref` パラメーター、パラメーター) があり `out` ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="b2e8c-137">値渡しのパラメーターを通じて引数が渡されると、メンバーは渡された実際の引数のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="b2e8c-138">引数が値型の場合は、引数のコピーがスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="b2e8c-139">引数が参照型の場合は、参照のコピーがスタックに配置されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="b2e8c-140">C#、VB.NET、C++ など、最も一般的な CLR 言語は、既定で値渡しでパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="b2e8c-141">引数がパラメーターを通じて渡されると、 `ref` メンバーは渡された実際の引数への参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="b2e8c-142">引数が値型の場合は、引数への参照がスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="b2e8c-143">引数が参照型の場合は、参照への参照がスタックに配置されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="b2e8c-144">`Ref` パラメーターを使用して、呼び出し元によって渡された引数をメンバーが変更できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="b2e8c-145">`Out` パラメーターはパラメーターと似ていますが、若干の違いがあり `ref` ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="b2e8c-146">パラメーターは、最初は未割り当てと見なされ、何らかの値が割り当てられる前にメンバー本体で読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="b2e8c-147">また、メンバーがを返す前に、パラメーターに何らかの値が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="b2e8c-148">❌ またはパラメーターを使用しないように `out` `ref` してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="b2e8c-149">`out`パラメーターまたはパラメーターを使用するには `ref` 、ポインターの使用経験、値型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="b2e8c-150">また、 `out` パラメーターとパラメーターの違い `ref` は広く認識されていません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="b2e8c-151">一般ユーザー向けに設計されたフレームワークの設計者 `out` は、ユーザーがまたはパラメーターを使用して作業することを想定しないでください `ref` 。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="b2e8c-152">❌ 参照型を参照渡しで渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="b2e8c-153">ルールには、参照のスワップに使用できるメソッドなど、いくつかの例外があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="b2e8c-154">パラメーターの数が可変のメンバー</span><span class="sxs-lookup"><span data-stu-id="b2e8c-154">Members with Variable Number of Parameters</span></span>
 <span data-ttu-id="b2e8c-155">可変個の引数を受け取ることができるメンバーは、配列パラメーターを指定することによって表現されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="b2e8c-156">たとえば、に <xref:System.String> は次のメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="b2e8c-157">ユーザーは次のようにメソッドを呼び出すことができ <xref:System.String.Format%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="b2e8c-158">C# params キーワードを配列パラメーターに追加すると、パラメーターがいわゆる params array パラメーターに変更され、一時配列を作成するためのショートカットが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="b2e8c-159">これにより、ユーザーは配列要素を引数リストに直接渡すことによって、メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="b2e8c-160">Params キーワードは、パラメーターリストの最後のパラメーターにのみ追加できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="b2e8c-161">エンドユーザーが少数の要素を持つ配列を渡すことが予想される場合は、params キーワードを配列パラメーターに追加することを✔️します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="b2e8c-162">多くの要素が共通のシナリオで渡されることが予想される場合、ユーザーはこれらの要素をインラインで渡すことはないため、params キーワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-162">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="b2e8c-163">❌ 呼び出し元が配列に既に入力を格納している場合は、params 配列を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="b2e8c-164">たとえば、バイト配列パラメーターを持つメンバーは、個々のバイトを渡すことで呼び出されることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="b2e8c-165">このため、.NET Framework のバイト配列パラメーターでは、params キーワードは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="b2e8c-166">❌ Params 配列パラメーターを取得するメンバーによって配列が変更されている場合は、params 配列を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="b2e8c-167">多くのコンパイラがメンバーの引数を呼び出しサイトの一時配列に変換するので、配列は一時オブジェクトである可能性があるため、配列に対する変更はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="b2e8c-168">より複雑なオーバーロードで使用できない場合でも、単純なオーバーロードで params キーワードを使用することを検討してください✔️。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="b2e8c-169">ユーザーがすべてのオーバーロードに含まれていなくても、1つのオーバーロードで params 配列を持つことができるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-169">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="b2e8c-170">params キーワードを使用できるようにするには、パラメーターの順序を✔️してみてください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="b2e8c-171">✔️、非常にパフォーマンスが重要な Api では、少数の引数を使用した呼び出しに対して特別なオーバーロードとコードパスを提供することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="b2e8c-172">これにより、API が少数の引数で呼び出された場合に、配列オブジェクトを作成しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="b2e8c-173">配列パラメーターの単数形を取得し、数値のサフィックスを追加することによって、パラメーターの名前を形成します。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="b2e8c-174">これは、単に配列を作成してより一般的なメソッドを呼び出すだけでなく、コードパス全体を特殊なケースにする場合にのみ実行してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="b2e8c-175">✔️は、params 配列引数として null を渡すことができることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="b2e8c-176">処理する前に、配列が null でないことを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="b2e8c-177">❌`varargs`省略記号として知られていないメソッドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="b2e8c-178">C++ などの一部の CLR 言語では、メソッドと呼ばれる変数パラメーターリストを渡すための代替規則がサポートさ `varargs` れています。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="b2e8c-179">この規則は、CLS に準拠していないため、フレームワークでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="b2e8c-180">ポインター パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2e8c-180">Pointer Parameters</span></span>
 <span data-ttu-id="b2e8c-181">一般に、適切にデザインされたマネージコードフレームワークの公開領域にポインターを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="b2e8c-182">ほとんどの場合、ポインターはカプセル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="b2e8c-183">ただし、相互運用性の理由からポインターが必要になる場合もあれば、ポインターを使用することが適切な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="b2e8c-184">ポインターは CLS に準拠していないため、ポインター引数を受け取るメンバーに対して代替手段を提供する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="b2e8c-185">❌ ポインター引数の負荷の高い引数のチェックを行わないでください。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="b2e8c-186">ポインターを使用してメンバーをデザインするときは、一般的なポインターに関連する規則に従う✔️ます。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="b2e8c-187">たとえば、単純なポインター演算を使用して同じ結果を得ることができるため、開始インデックスを渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b2e8c-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="b2e8c-188">*部分 &copy; 2005、2009 Microsoft Corporation。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="b2e8c-188">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b2e8c-189">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="b2e8c-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b2e8c-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2e8c-190">See also</span></span>

- [<span data-ttu-id="b2e8c-191">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b2e8c-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="b2e8c-192">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b2e8c-192">Framework Design Guidelines</span></span>](index.md)
