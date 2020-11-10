---
title: Windows ストア アプリの .NET ネイティブへの移行
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: ee17e50590a80d8973197b46910d5e22296c265f
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440895"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="978d6-102">Windows ストアアプリを .NET ネイティブに移行する</span><span class="sxs-lookup"><span data-stu-id="978d6-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="978d6-103">.NET ネイティブは、Windows ストアまたは開発者のコンピューターでアプリの静的なコンパイルを行います。</span><span class="sxs-lookup"><span data-stu-id="978d6-103">.NET Native provides static compilation of apps in the Windows Store or on the developer's computer.</span></span> <span data-ttu-id="978d6-104">これは、デバイス上で Just-In-Time (JIT) コンパイラまたは [ネイティブ イメージ ジェネレーター (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) によって Windows ストア アプリに対して実行される動的なコンパイルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="978d6-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="978d6-105">違いにかかわらず、.NET ネイティブは [Windows ストアアプリ用 .net](/previous-versions/windows/apps/br230302(v=vs.140))との互換性を維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="978d6-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](/previous-versions/windows/apps/br230302(v=vs.140)).</span></span> <span data-ttu-id="978d6-106">ほとんどの場合、Windows ストアアプリ用 .NET で動作するものは、.NET ネイティブでも動作します。</span><span class="sxs-lookup"><span data-stu-id="978d6-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="978d6-107">ただし、動作に違いがある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="978d6-108">このドキュメントでは、Windows ストアアプリ用の標準 .NET と、次の領域の .NET ネイティブにおけるこれらの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="978d6-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="978d6-109">全般的なランタイムの違い</span><span class="sxs-lookup"><span data-stu-id="978d6-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="978d6-110">動的プログラミングの違い</span><span class="sxs-lookup"><span data-stu-id="978d6-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="978d6-111">リフレクションに関するその他の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="978d6-112">サポートされていないシナリオと API</span><span class="sxs-lookup"><span data-stu-id="978d6-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="978d6-113">Visual Studio の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="978d6-114">全般的なランタイムの違い</span><span class="sxs-lookup"><span data-stu-id="978d6-114">General runtime differences</span></span>

- <span data-ttu-id="978d6-115"><xref:System.TypeLoadException>CLR (共通言語ランタイム) でアプリを実行するときに JIT コンパイラによってスローされる例外 (など) は、通常、.NET ネイティブによって処理されるときにコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="978d6-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="978d6-116">アプリの UI スレッドから <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> メソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="978d6-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="978d6-117">これにより、.NET ネイティブでデッドロックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="978d6-118">静的クラス コンストラクターの呼び出し順序に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="978d6-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="978d6-119">.NET ネイティブでは、呼び出し順序は標準ランタイムの順序とは異なります。</span><span class="sxs-lookup"><span data-stu-id="978d6-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="978d6-120">(標準ランタイムを使用する場合であっても、静的クラス コンストラクターの実行順序に依存しないでください。)</span><span class="sxs-lookup"><span data-stu-id="978d6-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="978d6-121">スレッドでの呼び出しを行わない無限ループ (たとえば、 `while(true);`) によって、アプリが停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="978d6-122">同様に、長時間または無限の待機によってもアプリが停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="978d6-123">特定の汎用初期化サイクルでは、.NET ネイティブで例外がスローされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="978d6-124">たとえば、次のコードは標準 CLR では <xref:System.TypeLoadException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="978d6-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="978d6-125">.NET ネイティブでは、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="978d6-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="978d6-126">場合によっては、.NET ネイティブは .NET Framework クラスライブラリのさまざまな実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="978d6-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="978d6-127">メソッドから返されるオブジェクトは、常に、返される型のメンバーを実装します。</span><span class="sxs-lookup"><span data-stu-id="978d6-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="978d6-128">ただし、その補助的な実装が異なるため、その他の .NET Framework プラットフォームの場合と同じ型セットへのオブジェクトのキャストを行うことができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="978d6-129">たとえば、 <xref:System.Collections.Generic.IEnumerable%601> や <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> などのメソッドにより返される <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> インターフェイス オブジェクトを `T[]`にキャストできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="978d6-130">WinInet キャッシュは、Windows ストアアプリ用 .NET では既定で有効になっていませんが、.NET ネイティブにあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="978d6-131">これによりパフォーマンスが向上しますが、作業セットへの影響があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="978d6-132">開発者のアクションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="978d6-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="978d6-133">動的プログラミングの違い</span><span class="sxs-lookup"><span data-stu-id="978d6-133">Dynamic programming differences</span></span>

<span data-ttu-id="978d6-134">.NET Framework からコード内の静的なリンクを .NET ネイティブして、最大のパフォーマンスを実現するためにコードをアプリケーションローカルにします。</span><span class="sxs-lookup"><span data-stu-id="978d6-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="978d6-135">ただし、バイナリ サイズは小さいままである必要があるため、.NET Framework 全体を取り入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="978d6-136">.NET ネイティブコンパイラは、使用されていないコードへの参照を削除する依存関係 reducer を使用して、この制限を解決します。</span><span class="sxs-lookup"><span data-stu-id="978d6-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="978d6-137">ただし、コンパイル時にその情報を静的に推論できず、代わりに実行時に動的に取得される場合、.NET ネイティブは、型情報やコードを維持または生成しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="978d6-138">.NET ネイティブは、リフレクションと動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="978d6-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="978d6-139">ただし、すべての型をリフレクション対象としてマークできるわけではありません。そうすると、生成されるコード サイズが大きくなりすぎるため (特に、.NET Framework での パブリック API へのリフレクションがサポートされているため) です。</span><span class="sxs-lookup"><span data-stu-id="978d6-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="978d6-140">.NET ネイティブコンパイラは、リフレクションをサポートする型についての賢明な選択を行い、メタデータを保持し、それらの型に対してのみコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="978d6-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="978d6-141">たとえば、データ バインディングは、プロパティ名を関数にマップするためにアプリを必要とします。</span><span class="sxs-lookup"><span data-stu-id="978d6-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="978d6-142">Windows ストア アプリ用 .NET では、共通言語ランタイムが自動的にリフレクションを使用して、マネージド型および公開されているネイティブ型にこの機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="978d6-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="978d6-143">.NET ネイティブでは、データのバインド先となる型のメタデータがコンパイラによって自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="978d6-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="978d6-144">.NET ネイティブコンパイラでは、やなどの一般的に使用されるジェネリック型を処理することもできます <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602> 。これはヒントやディレクティブを必要とせずに機能します。</span><span class="sxs-lookup"><span data-stu-id="978d6-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="978d6-145">[dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) キーワードも、一定の制限の下でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="978d6-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="978d6-146">アプリを .NET ネイティブに移植するときは、すべての動的コードパスを十分にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="978d6-147">ほとんどの開発者には .NET ネイティブの既定の構成で十分ですが、ランタイムディレクティブ (.rd.xml) ファイルを使用して構成を微調整する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="978d6-148">また、場合によっては、.NET ネイティブコンパイラは、リフレクションで使用できる必要があるメタデータを判断できず、次の場合には特にヒントに依存します。</span><span class="sxs-lookup"><span data-stu-id="978d6-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="978d6-149"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> や <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> などの一部の構造体は、静的に決定できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="978d6-150">コンパイラでインスタンス化を決定できないため、リフレクション対象のジェネリック型をランタイム ディレクティブで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="978d6-151">これは、すべてのコードを含める必要があるだけではなく、ジェネリック型へのリフレクションによって無限サイクルが生じる可能性があるためです (たとえば、ジェネリック型でジェネリック メソッドが呼び出された場合)。</span><span class="sxs-lookup"><span data-stu-id="978d6-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="978d6-152">ランタイム ディレクティブは、ランタイム ディレクティブ (.rd.xml) ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="978d6-153">このファイルの使用方法に関する全般的な情報は、「[Getting Started with .NET Native](getting-started-with-net-native.md)」(.NET ネイティブの概要) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="978d6-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="978d6-154">ランタイム ディレクティブについては、「 [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="978d6-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="978d6-155">.NET ネイティブには、開発者が既定のセットの外部でリフレクションをサポートする必要のある型を判断するのに役立つプロファイリングツールも含まれています。</span><span class="sxs-lookup"><span data-stu-id="978d6-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="978d6-156">リフレクションに関するその他の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-156">Other reflection-related differences</span></span>

<span data-ttu-id="978d6-157">Windows ストアアプリ用 .NET と .NET ネイティブの動作には、リフレクションに関連するその他のさまざまな違いがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="978d6-158">.NET ネイティブ:</span><span class="sxs-lookup"><span data-stu-id="978d6-158">In .NET Native:</span></span>

- <span data-ttu-id="978d6-159">.NET Framework クラス ライブラリでの型とメンバーに対するプライベート リフレクションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="978d6-160">ただし、独自のプライベート型とメンバー、およびサードパーティ ライブラリの型とメンバーに対するリフレクションは行うことができます。</span><span class="sxs-lookup"><span data-stu-id="978d6-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="978d6-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> プロパティは、戻り値を表す `false` オブジェクトに対し、正しく <xref:System.Reflection.ParameterInfo> を返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="978d6-162">Windows ストア アプリ用 .NET の場合、これは `true`を返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="978d6-163">中間言語 (IL) はこれを直接サポートしておらず、解釈は言語に残されています。</span><span class="sxs-lookup"><span data-stu-id="978d6-163">Intermediate language (IL) doesn't support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="978d6-164"><xref:System.RuntimeFieldHandle> 構造体と <xref:System.RuntimeMethodHandle> 構造体のパブリック メンバーはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="978d6-165">これらの型は、LINQ、式ツリー、および静的な配列の初期化でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="978d6-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="978d6-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> と <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> の基底クラスには隠ぺいされたメンバーが含まれるため、明示的なオーバーライドなしでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="978d6-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="978d6-167">これは、その他の [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) メソッドの場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="978d6-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="978d6-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> とは、 <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> 特定の組み合わせ (たとえば、オブジェクトの配列) を作成しようとしたときに失敗しません `byref` 。</span><span class="sxs-lookup"><span data-stu-id="978d6-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="978d6-169">リフレクションを使用して、ポインター パラメーターを持つメンバーを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="978d6-170">リフレクションを使用して、ポインター フィールドを取得または設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="978d6-171">引数の数が間違っていて、いずれかの引数の型が正しくない場合、.NET ネイティブはではなくをスロー <xref:System.ArgumentException> <xref:System.Reflection.TargetParameterCountException> します。</span><span class="sxs-lookup"><span data-stu-id="978d6-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="978d6-172">通常、例外のバイナリ シリアル化はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="978d6-173">そのため、シリアル化不可能なオブジェクトを <xref:System.Exception.Data%2A?displayProperty=nameWithType> ディクショナリに追加できます。</span><span class="sxs-lookup"><span data-stu-id="978d6-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="978d6-174">サポートされていないシナリオと API</span><span class="sxs-lookup"><span data-stu-id="978d6-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="978d6-175">次のセクションに、全般的な開発、相互運用、および HTTPClient や Windows Communication Foundation (WCF) などの技術でサポートされないシナリオと API を示します。</span><span class="sxs-lookup"><span data-stu-id="978d6-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="978d6-176">一般的な開発</span><span class="sxs-lookup"><span data-stu-id="978d6-176">General development</span></span>](#General)

- [<span data-ttu-id="978d6-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="978d6-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="978d6-178">相互運用</span><span class="sxs-lookup"><span data-stu-id="978d6-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="978d6-179">サポートされていない API</span><span class="sxs-lookup"><span data-stu-id="978d6-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="978d6-180">全般的な開発の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-180">General development differences</span></span>

<span data-ttu-id="978d6-181">**値型**</span><span class="sxs-lookup"><span data-stu-id="978d6-181">**Value types**</span></span>

- <span data-ttu-id="978d6-182">値型の <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> メソッドと <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> メソッドをオーバーライドする場合は、基底クラスの実装を呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="978d6-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="978d6-183">Windows ストア アプリ用 .NET では、これらのメソッドはリフレクションに依存します。</span><span class="sxs-lookup"><span data-stu-id="978d6-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="978d6-184">コンパイル時に、.NET ネイティブによって、ランタイムリフレクションに依存しない実装が生成されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="978d6-185">つまり、これらの2つのメソッドをオーバーライドしないと、コンパイル時に .NET ネイティブによって実装が生成されるため、これらのメソッドは想定どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="978d6-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="978d6-186">ただし、基底クラスの実装を呼び出さずにこれらのメソッドをオーバーライドすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="978d6-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="978d6-187">1 mb を超える値の型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-187">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="978d6-188">値型では、.NET ネイティブにパラメーターなしのコンストラクターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="978d6-189">(C# および Visual Basic 値型のパラメーターなしのコンストラクターを禁止します。</span><span class="sxs-lookup"><span data-stu-id="978d6-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="978d6-190">ただし、IL ではこれらを作成できます。)</span><span class="sxs-lookup"><span data-stu-id="978d6-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="978d6-191">**配列**</span><span class="sxs-lookup"><span data-stu-id="978d6-191">**Arrays**</span></span>

- <span data-ttu-id="978d6-192">ゼロ以外の下限を持つ配列はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="978d6-193">通常、これらの配列は <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> オーバーロードを呼び出すことで作成されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="978d6-194">多次元配列の動的作成はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="978d6-195">そのような配列は通常、 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> パラメーターを含む `lengths` メソッドのオーバーロードを呼び出すか、 <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> メソッドを呼び出すことで作成されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="978d6-196">4 つ以上の次元を持つ多次元配列 (つまり、 <xref:System.Array.Rank%2A?displayProperty=nameWithType> プロパティ値が 4 以上のもの) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="978d6-197">代わりに [ジャグ配列](../../csharp/programming-guide/arrays/jagged-arrays.md) (配列の配列) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="978d6-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="978d6-198">たとえば、 `array[x,y,z]` は無効ですが、 `array[x][y][z]` は有効です。</span><span class="sxs-lookup"><span data-stu-id="978d6-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="978d6-199">多次元配列の共変性はサポートされず、実行時に <xref:System.InvalidCastException> 例外を発生させます。</span><span class="sxs-lookup"><span data-stu-id="978d6-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="978d6-200">**ジェネリック**</span><span class="sxs-lookup"><span data-stu-id="978d6-200">**Generics**</span></span>

- <span data-ttu-id="978d6-201">ジェネリック型の無限展開はコンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="978d6-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="978d6-202">たとえば、このコードはコンパイルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="978d6-203">**ポインター**</span><span class="sxs-lookup"><span data-stu-id="978d6-203">**Pointers**</span></span>

- <span data-ttu-id="978d6-204">ポインターの配列はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="978d6-205">リフレクションを使用して、ポインター フィールドを取得または設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="978d6-206">**シリアル化**</span><span class="sxs-lookup"><span data-stu-id="978d6-206">**Serialization**</span></span>

<span data-ttu-id="978d6-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 属性はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="978d6-208">代わりに <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 属性を使用してください。</span><span class="sxs-lookup"><span data-stu-id="978d6-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="978d6-209">**リソース**</span><span class="sxs-lookup"><span data-stu-id="978d6-209">**Resources**</span></span>

<span data-ttu-id="978d6-210"><xref:System.Diagnostics.Tracing.EventSource> クラスでのローカライズされたリソースの使用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="978d6-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> プロパティはローカライズされたリソースを定義しません。</span><span class="sxs-lookup"><span data-stu-id="978d6-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="978d6-212">**デリゲート**</span><span class="sxs-lookup"><span data-stu-id="978d6-212">**Delegates**</span></span>

<span data-ttu-id="978d6-213">`Delegate.BeginInvoke` と `Delegate.EndInvoke` はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="978d6-214">**その他の API**</span><span class="sxs-lookup"><span data-stu-id="978d6-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="978d6-215">[TypeInfo.GUID](xref:System.Type.GUID) <xref:System.PlatformNotSupportedException> <xref:System.Runtime.InteropServices.GuidAttribute> 属性が型に適用されていない場合、TypeInfo プロパティは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="978d6-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="978d6-216">GUID は主に COM サポートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="978d6-217">メソッドは、 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> .NET ネイティブの短い日付を含む文字列を正しく解析します。</span><span class="sxs-lookup"><span data-stu-id="978d6-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="978d6-218">ただし、Microsoft サポート技術情報の記事 [KB2803771](https://support.microsoft.com/kb/2803771) と [KB2803755](https://support.microsoft.com/kb/2803755)で説明されている日付と時刻の解析の変更に対する互換性は保持されません。</span><span class="sxs-lookup"><span data-stu-id="978d6-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="978d6-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`が .NET ネイティブで正しく丸められています。</span><span class="sxs-lookup"><span data-stu-id="978d6-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="978d6-220">CLR の一部のバージョンでは、結果の文字列が丸められるのではなく、切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="978d6-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="978d6-221">HttpClient の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-221">HttpClient differences</span></span>

<span data-ttu-id="978d6-222">.NET ネイティブでは、 <xref:System.Net.Http.HttpClientHandler> クラスは、 <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> 標準の <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> Windows ストアアプリ用 .net で使用されるクラスとクラスではなく、WinINet を内部で (クラスを通じて) 使用します。</span><span class="sxs-lookup"><span data-stu-id="978d6-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="978d6-223">WinINet では、 <xref:System.Net.Http.HttpClientHandler> クラスでサポートされる構成オプションがすべてサポートされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="978d6-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="978d6-224">その結果、次のような影響が出ています。</span><span class="sxs-lookup"><span data-stu-id="978d6-224">As a result:</span></span>

- <span data-ttu-id="978d6-225">の機能プロパティの一部は <xref:System.Net.Http.HttpClientHandler> `false` .NET ネイティブで返されますが、 `true` Windows ストアアプリ用の標準 .net ではを返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="978d6-226">一部の構成プロパティアクセサーは、 `get` Windows ストアアプリ用 .net の既定の構成可能な値とは異なる .NET ネイティブに、常に固定値を返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="978d6-227">次のサブセクションで、その他の動作の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="978d6-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="978d6-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="978d6-228">**Proxy**</span></span>

<span data-ttu-id="978d6-229">クラスは、要求ごとの <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> プロキシの構成またはオーバーライドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="978d6-230">これは、プロパティの値に応じて、.NET ネイティブ上のすべての要求が、システム構成のプロキシサーバーを使用するか、プロキシサーバーを使用しないことを意味 <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> します。</span><span class="sxs-lookup"><span data-stu-id="978d6-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="978d6-231">Windows ストア アプリ用 .NET では、プロキシ サーバーは <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> プロパティにより定義されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="978d6-232">.NET ネイティブで、を <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> 以外の値に設定すると、 `null` 例外がスローさ <xref:System.PlatformNotSupportedException> れます。</span><span class="sxs-lookup"><span data-stu-id="978d6-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="978d6-233"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType>プロパティは .NET ネイティブ `false` でを返しますが、 `true` Windows ストアアプリの標準 .NET Framework ではを返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="978d6-234">**自動リダイレクト**</span><span class="sxs-lookup"><span data-stu-id="978d6-234">**Automatic redirection**</span></span>

<span data-ttu-id="978d6-235">クラスでは <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> 、自動リダイレクトの最大数を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="978d6-236">標準の Windows ストア アプリ用 .NET での <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> プロパティの値は既定で 50 で、変更できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="978d6-237">.NET ネイティブでは、このプロパティの値は10であり、変更しようとすると例外がスローさ <xref:System.PlatformNotSupportedException> れます。</span><span class="sxs-lookup"><span data-stu-id="978d6-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="978d6-238"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>プロパティは `false` .NET ネイティブでを返しますが、 `true` Windows ストアアプリの .net ではを返します。</span><span class="sxs-lookup"><span data-stu-id="978d6-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="978d6-239">**自動展開**</span><span class="sxs-lookup"><span data-stu-id="978d6-239">**Automatic decompression**</span></span>

<span data-ttu-id="978d6-240">Windows ストア アプリ用 .NET では、 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> プロパティを <xref:System.Net.DecompressionMethods.Deflate>、 <xref:System.Net.DecompressionMethods.GZip>、 <xref:System.Net.DecompressionMethods.Deflate> と <xref:System.Net.DecompressionMethods.GZip>の両方、または <xref:System.Net.DecompressionMethods.None>に設定できます。</span><span class="sxs-lookup"><span data-stu-id="978d6-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="978d6-241">.NET ネイティブ <xref:System.Net.DecompressionMethods.Deflate> は、、またはと共にのみサポートさ <xref:System.Net.DecompressionMethods.GZip> <xref:System.Net.DecompressionMethods.None> れます。</span><span class="sxs-lookup"><span data-stu-id="978d6-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="978d6-242"><xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> プロパティを <xref:System.Net.DecompressionMethods.Deflate> のみまたは <xref:System.Net.DecompressionMethods.GZip> のみに設定しようとすると、 <xref:System.Net.DecompressionMethods.Deflate> と <xref:System.Net.DecompressionMethods.GZip>の両方に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="978d6-243">**Cookie**</span><span class="sxs-lookup"><span data-stu-id="978d6-243">**Cookies**</span></span>

<span data-ttu-id="978d6-244">クッキーの処理は、 <xref:System.Net.Http.HttpClient> と WinINet により同時に行われます。</span><span class="sxs-lookup"><span data-stu-id="978d6-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="978d6-245"><xref:System.Net.CookieContainer> のクッキーは、WinINet クッキー キャッシュのクッキーと組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="978d6-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="978d6-246"><xref:System.Net.CookieContainer> のクッキーを削除すると <xref:System.Net.Http.HttpClient> からクッキーが送信されませんが、クッキーが既に WinINet に示されており、ユーザーによって削除されない場合、WinINet がクッキーを送信します。</span><span class="sxs-lookup"><span data-stu-id="978d6-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="978d6-247"><xref:System.Net.Http.HttpClient>、 <xref:System.Net.Http.HttpClientHandler>、または <xref:System.Net.CookieContainer> API を使用して、プログラムにより WinINet からクッキーを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="978d6-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="978d6-248"><xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> プロパティを `false` に設定しても、 <xref:System.Net.Http.HttpClient> からクッキーが送信されなくなるのみで、WinINet の要求にはまだそのクッキーが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="978d6-249">**資格情報**</span><span class="sxs-lookup"><span data-stu-id="978d6-249">**Credentials**</span></span>

<span data-ttu-id="978d6-250">Windows ストア アプリ用 .NET では、 <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> プロパティと <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> プロパティは独立して動作します。</span><span class="sxs-lookup"><span data-stu-id="978d6-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="978d6-251">また、 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは <xref:System.Net.ICredentials> インターフェイスを実装するオブジェクトをすべて受け入れます。</span><span class="sxs-lookup"><span data-stu-id="978d6-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="978d6-252">.NET ネイティブでは、プロパティを <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> に設定する `true` と、プロパティがに <xref:System.Net.Http.HttpClientHandler.Credentials%2A> なり `null` ます。</span><span class="sxs-lookup"><span data-stu-id="978d6-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="978d6-253">さらに、 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは、 `null`、 <xref:System.Net.CredentialCache.DefaultCredentials%2A>、または <xref:System.Net.NetworkCredential>型のオブジェクトにしか設定できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="978d6-254">その他の <xref:System.Net.ICredentials> オブジェクト (最も一般的なものは <xref:System.Net.CredentialCache>) を <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティに割り当てると、 <xref:System.PlatformNotSupportedException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="978d6-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="978d6-255">**その他のサポートされていない機能または構成できない機能**</span><span class="sxs-lookup"><span data-stu-id="978d6-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="978d6-256">.NET ネイティブ:</span><span class="sxs-lookup"><span data-stu-id="978d6-256">In .NET Native:</span></span>

- <span data-ttu-id="978d6-257"><xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> プロパティの値は常に <xref:System.Net.Http.ClientCertificateOption.Automatic>です。</span><span class="sxs-lookup"><span data-stu-id="978d6-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="978d6-258">Windows ストア アプリ用 .NET での既定値は <xref:System.Net.Http.ClientCertificateOption.Manual>です。</span><span class="sxs-lookup"><span data-stu-id="978d6-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="978d6-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> プロパティは構成できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="978d6-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> プロパティは常に `true`です。</span><span class="sxs-lookup"><span data-stu-id="978d6-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="978d6-261">Windows ストア アプリ用 .NET での既定値は `false`です。</span><span class="sxs-lookup"><span data-stu-id="978d6-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="978d6-262">応答の `SetCookie2` ヘッダーは廃止されたものとして無視されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>

### <a name="interop-differences"></a><span data-ttu-id="978d6-263">相互運用の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-263">Interop differences</span></span>

 <span data-ttu-id="978d6-264">**非推奨の API**</span><span class="sxs-lookup"><span data-stu-id="978d6-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="978d6-265">マネージド コードで相互運用性のために使用される頻度が低い API のいくつかが、非推奨にされました。</span><span class="sxs-lookup"><span data-stu-id="978d6-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="978d6-266">これらの Api を .NET ネイティブと共に使用すると、または例外がスローされるか、コンパイラエラーが発生する可能性があり <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> ます。</span><span class="sxs-lookup"><span data-stu-id="978d6-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="978d6-267">Windows ストア アプリ用 .NET では、これらの API は廃止としてマークされていますが、これらの API を呼び出すとコンパイラ エラーではなくコンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="978d6-268">非推奨の `VARIANT` マーシャリング api には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="978d6-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> はサポートされていますが、 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) や variant で使用されている場合など、一部のシナリオでは例外をスロー `byref` します。</span><span class="sxs-lookup"><span data-stu-id="978d6-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="978d6-270">非推奨の [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) サポート用 api は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="978d6-270">Deprecated APIs for [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="978d6-271">クラシック COM イベントの非推奨の Api は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="978d6-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="978d6-272"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>.NET ネイティブでサポートされていない、インターフェイスの非推奨の api には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="978d6-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="978d6-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="978d6-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="978d6-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="978d6-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="978d6-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="978d6-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="978d6-276">その他のサポートされない相互運用機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="978d6-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="978d6-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="978d6-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="978d6-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="978d6-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="978d6-279">ほとんど使用されないマーシャリング Api:</span><span class="sxs-lookup"><span data-stu-id="978d6-279">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="978d6-280">**プラットフォーム呼び出しと COM 相互運用の互換性**</span><span class="sxs-lookup"><span data-stu-id="978d6-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="978d6-281">ほとんどのプラットフォーム呼び出しと COM 相互運用のシナリオは、.NET ネイティブでもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="978d6-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="978d6-282">特に、Windows ランタイム (WinRT) API とのすべての相互運用性と Windows ランタイムで必要なすべてのマーシャリングがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="978d6-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="978d6-283">これには、次のものに対するマーシャリング サポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="978d6-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="978d6-284">配列 ( <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>を含む)</span><span class="sxs-lookup"><span data-stu-id="978d6-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="978d6-285">代理人</span><span class="sxs-lookup"><span data-stu-id="978d6-285">Delegates</span></span>

- <span data-ttu-id="978d6-286">文字列 (Unicode、ANSI、および HSTRING)</span><span class="sxs-lookup"><span data-stu-id="978d6-286">Strings (Unicode, ANSI, and HSTRING)</span></span>

- <span data-ttu-id="978d6-287">構造体 (`byref` と `byval`)</span><span class="sxs-lookup"><span data-stu-id="978d6-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="978d6-288">Unions</span><span class="sxs-lookup"><span data-stu-id="978d6-288">Unions</span></span>

- <span data-ttu-id="978d6-289">Win32 ハンドル</span><span class="sxs-lookup"><span data-stu-id="978d6-289">Win32 handles</span></span>

- <span data-ttu-id="978d6-290">すべての WinRT 構造体</span><span class="sxs-lookup"><span data-stu-id="978d6-290">All WinRT constructs</span></span>

- <span data-ttu-id="978d6-291">マーシャリング バリアント型の部分的なサポート。</span><span class="sxs-lookup"><span data-stu-id="978d6-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="978d6-292">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="978d6-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="978d6-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="978d6-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="978d6-294">ただし、.NET ネイティブは次の機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="978d6-295">クラシック COM イベントの使用</span><span class="sxs-lookup"><span data-stu-id="978d6-295">Using classic COM events</span></span>

- <span data-ttu-id="978d6-296">マネージド型での <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="978d6-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="978d6-297">[属性を使用したマネージド型での](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) IDispatch <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> インターフェイスの実装。</span><span class="sxs-lookup"><span data-stu-id="978d6-297">Implementing the [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="978d6-298">ただし、から COM オブジェクトを呼び出すことはできません `IDispatch` 。また、マネージオブジェクトでを実装することもできません `IDispatch` 。</span><span class="sxs-lookup"><span data-stu-id="978d6-298">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="978d6-299">リフレクションを使用したプラットフォーム呼び出しメソッドの呼び出しはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="978d6-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="978d6-300">この制限を回避するには、別のメソッドでメソッド呼び出しをラップし、リフレクションを使用してラッパーを代わりに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="978d6-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="978d6-301">その他の Windows ストア アプリ用 .NET API との違い</span><span class="sxs-lookup"><span data-stu-id="978d6-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="978d6-302">このセクションでは、.NET ネイティブでサポートされていないその他の Api の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="978d6-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="978d6-303">サポートされていない Api の最大セットは、Windows Communication Foundation (WCF) Api です。</span><span class="sxs-lookup"><span data-stu-id="978d6-303">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="978d6-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="978d6-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="978d6-305"><xref:System.ComponentModel.DataAnnotations>名前空間と名前空間の型は、 <xref:System.ComponentModel.DataAnnotations.Schema> .NET ネイティブではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="978d6-306">これには、Windows 8 用 Windows ストアアプリ用 .NET に存在する次の型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="978d6-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="978d6-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="978d6-307">**Visual Basic**</span></span>

<span data-ttu-id="978d6-308">Visual Basic は、現在 .NET ネイティブではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="978d6-309">名前空間と名前空間の次の型は、 <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> .NET ネイティブでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="978d6-310">**リフレクション コンテキスト (System.Reflection.Context 名前空間)**</span><span class="sxs-lookup"><span data-stu-id="978d6-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="978d6-311"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>クラスは .NET ネイティブではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="978d6-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="978d6-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="978d6-313">`System.Net.Http.RtcRequestFactory`クラスは .NET ネイティブではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="978d6-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="978d6-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="978d6-315">[System.servicemodel. \* 名前空間](xref:System.ServiceModel)の型は、.NET ネイティブではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="978d6-316">次のような型があります。</span><span class="sxs-lookup"><span data-stu-id="978d6-316">These include the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="978d6-317">シリアライザーの違い</span><span class="sxs-lookup"><span data-stu-id="978d6-317">Differences in serializers</span></span>

<span data-ttu-id="978d6-318"><xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスによるシリアル化と逆シリアル化に関する違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="978d6-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="978d6-319">.NET ネイティブでは、とは、 <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 型がルートシリアル化型ではない基底クラスメンバーを持つ派生クラスのシリアル化または逆シリアル化に失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="978d6-320">たとえば、次のコードでは、 `Y` をシリアル化または逆シリアル化しようとするとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="978d6-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="978d6-321">基底クラスのメンバーはシリアル化時にスキャンされないため、 `InnerType` 型はシリアライザーに認識されていません。</span><span class="sxs-lookup"><span data-stu-id="978d6-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="978d6-322"><xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスまたは構造体のシリアル化に失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="978d6-323">たとえば、次の型ではシリアル化と逆シリアル化が失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="978d6-324"><xref:System.Xml.Serialization.XmlSerializer> は、シリアル化するオブジェクトの正確な型を認識していないため、次のオブジェクト値をシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="978d6-325"><xref:System.Xml.Serialization.XmlSerializer> は、シリアル化されるオブジェクトの型が <xref:System.Xml.XmlQualifiedName>の場合、シリアル化と逆シリアル化に失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="978d6-326">すべてのシリアライザー (<xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer>) は、 <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> 型または <xref:System.Xml.Linq.XElement>を含む型のシリアル化コードを生成できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="978d6-327">代わりに、ビルド時エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="978d6-328">次のシリアル化型のコンストラクターが、期待どおりに動作する保証はありません。</span><span class="sxs-lookup"><span data-stu-id="978d6-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="978d6-329"><xref:System.Xml.Serialization.XmlSerializer> は、次のいずれかの属性が設定されているメソッドを持つ型のコードを生成できません。</span><span class="sxs-lookup"><span data-stu-id="978d6-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="978d6-330"><xref:System.Xml.Serialization.XmlSerializer> は、 <xref:System.Xml.Serialization.IXmlSerializable> カスタム シリアル化インターフェイスを受け入れません。</span><span class="sxs-lookup"><span data-stu-id="978d6-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="978d6-331">このインターフェイスを実装するクラスがある場合、 <xref:System.Xml.Serialization.XmlSerializer> は型を Plain Old CLR Object (POCO) 型であると見なし、そのパブリック プロパティのみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="978d6-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="978d6-332">プレーンオブジェクトのシリアル化は <xref:System.Exception> 、とでは正しく機能しません <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="978d6-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="978d6-333">Visual Studio の違い</span><span class="sxs-lookup"><span data-stu-id="978d6-333">Visual Studio differences</span></span>

<span data-ttu-id="978d6-334">**例外とデバッグ**</span><span class="sxs-lookup"><span data-stu-id="978d6-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="978d6-335">デバッガーで .NET ネイティブを使用してコンパイルされたアプリを実行している場合は、次の例外の種類に対して初回例外が有効になります。</span><span class="sxs-lookup"><span data-stu-id="978d6-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="978d6-336">**アプリのビルド**</span><span class="sxs-lookup"><span data-stu-id="978d6-336">**Building apps**</span></span>

<span data-ttu-id="978d6-337">Visual Studio で既定で使用される x86 ビルド ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="978d6-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="978d6-338">C:\Program Files (x86)\MSBuild\12.0\bin\amd64 にある AMD64 MSBuild ツールは、ビルドの問題が発生する可能性があるため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="978d6-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="978d6-339">**プロファイラー**</span><span class="sxs-lookup"><span data-stu-id="978d6-339">**Profilers**</span></span>

- <span data-ttu-id="978d6-340">Visual Studio CPU プロファイラーと XAML メモリ プロファイラーでは、マイ コードのみは正しく表示されません。</span><span class="sxs-lookup"><span data-stu-id="978d6-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="978d6-341">XAML メモリ プロファイラーでは、マネージド ヒープ データが正しく表示されません。</span><span class="sxs-lookup"><span data-stu-id="978d6-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="978d6-342">CPU プロファイラーでは、モジュールが正しく識別されず、プレフィックス付きの関数名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="978d6-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="978d6-343">**単体テスト ライブラリ プロジェクト**</span><span class="sxs-lookup"><span data-stu-id="978d6-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="978d6-344">Windows ストアアプリプロジェクトの単体テストライブラリで .NET ネイティブを有効にすることはサポートされていないため、プロジェクトのビルドに失敗します。</span><span class="sxs-lookup"><span data-stu-id="978d6-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="978d6-345">関連項目</span><span class="sxs-lookup"><span data-stu-id="978d6-345">See also</span></span>

- [<span data-ttu-id="978d6-346">はじめに</span><span class="sxs-lookup"><span data-stu-id="978d6-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="978d6-347">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="978d6-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="978d6-348">[Windows ストアアプリ用 .NET の概要](/previous-versions/windows/apps/br230302(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="978d6-348">[.NET For Windows Store apps overview](/previous-versions/windows/apps/br230302(v=vs.140))</span></span>
- [<span data-ttu-id="978d6-349">Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート</span><span class="sxs-lookup"><span data-stu-id="978d6-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
