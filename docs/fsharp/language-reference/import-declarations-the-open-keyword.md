---
title: 'インポート宣言: open キーワード'
description: 'F # インポート宣言と、完全修飾名を使用せずに参照できる要素を持つモジュールまたは名前空間を指定する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 4d3fd159aa4b334e9db0d7f756047470ad9c0829
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739686"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="9ebdd-103">インポート宣言: `open` キーワード</span><span class="sxs-lookup"><span data-stu-id="9ebdd-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="9ebdd-104">*インポート宣言* は、完全修飾名を使用せずに参照できる要素を持つモジュールまたは名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ebdd-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ebdd-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
open type type-name
```

## <a name="remarks"></a><span data-ttu-id="9ebdd-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="9ebdd-106">Remarks</span></span>

<span data-ttu-id="9ebdd-107">常に完全修飾名前空間またはモジュールパスを使用してコードを参照すると、書き込み、読み取り、および保守が困難なコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="9ebdd-108">代わりに、 `open` 頻繁に使用されるモジュールと名前空間にキーワードを使用して、そのモジュールまたは名前空間のメンバーを参照するときに、完全修飾名の代わりに短い形式の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="9ebdd-109">このキーワードは、C# の `using` キーワード、 `using namespace` Visual C++、Visual Basic に似てい `Imports` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="9ebdd-110">指定されたモジュールまたは名前空間は、同じプロジェクトまたは参照されるプロジェクトまたはアセンブリ内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="9ebdd-111">そうでない場合は、プロジェクトへの参照を追加するか、 `-reference` コマンドラインオプション (またはその省略形) を使用することができ `-r` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="9ebdd-112">詳細については、「 [コンパイラオプション](compiler-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="9ebdd-113">インポート宣言は、外側の名前空間、モジュール、またはファイルの末尾まで、宣言の後のコードで名前を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="9ebdd-114">複数のインポート宣言を使用する場合は、別々の行に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="9ebdd-115">次のコードは、キーワードを使用して `open` コードを簡略化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="9ebdd-116">F # コンパイラは、同じ名前が複数の開いているモジュールまたは名前空間で発生した場合に、あいまいさが発生した場合にエラーまたは警告を生成しません。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="9ebdd-117">あいまいさが発生すると、F # は、最近開いたモジュールまたは名前空間を優先します。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="9ebdd-118">たとえば、次のコードでは、 `empty` `Seq.empty` との `empty` 両方のモジュールにがある場合でも、はを意味し `List` `Seq` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn %"{empty}"
```

<span data-ttu-id="9ebdd-119">したがって、同じ名前を持つメンバーが含まれているモジュールまたは名前空間を開く場合は注意が必要です。 `List` `Seq` 代わりに、修飾名の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="9ebdd-120">コードがインポート宣言の順序に依存している状況を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="9ebdd-121">オープン型の宣言</span><span class="sxs-lookup"><span data-stu-id="9ebdd-121">Open type declarations</span></span>

<span data-ttu-id="9ebdd-122">F # `open` は、次のような型でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-122">F# supports `open` on a type like so:</span></span>

```fsharp
open type System.Math
PI
```

<span data-ttu-id="9ebdd-123">これにより、型のアクセス可能なすべての静的フィールドとメンバーが公開されます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-123">This will expose all accessible static fields and members on the type.</span></span>

<span data-ttu-id="9ebdd-124">また、 `open` F # で定義された [レコード](records.md) と [判別共用体](discriminated-unions.md) の型を使用して、静的メンバーを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-124">You can also `open` F#-defined [record](records.md) and [discriminated union](discriminated-unions.md) types to expose static members.</span></span> <span data-ttu-id="9ebdd-125">判別共用体の場合は、共用体ケースを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-125">In the case of discriminated unions, you can also expose the union cases.</span></span> <span data-ttu-id="9ebdd-126">これは、次のように、モジュール内で宣言された型の共用体ケースにアクセスする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-126">This can be helpful for accessing union cases in a type declared inside of a module that you may not want to open, like so:</span></span>

```fsharp
module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="9ebdd-127">既定で開かれている名前空間</span><span class="sxs-lookup"><span data-stu-id="9ebdd-127">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="9ebdd-128">一部の名前空間は、明示的なインポート宣言がなくても暗黙的に開かれる F # コードでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-128">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="9ebdd-129">次の表は、既定で開かれている名前空間を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-129">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="9ebdd-130">名前空間</span><span class="sxs-lookup"><span data-stu-id="9ebdd-130">Namespace</span></span>|<span data-ttu-id="9ebdd-131">説明</span><span class="sxs-lookup"><span data-stu-id="9ebdd-131">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="9ebdd-132">やなどの組み込み型の基本的な F # 型定義が含まれてい `int` `float` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-132">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="9ebdd-133">やなどの基本的な算術演算が含まれてい `+` `*` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-133">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="9ebdd-134">やなどの変更できないコレクションクラスが含まれてい `List` `Array` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-134">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="9ebdd-135">レイジー評価や非同期ワークフローなどのコントロール構成要素の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-135">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="9ebdd-136">関数など、書式設定された IO 用の関数が含まれてい `printf` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-136">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="9ebdd-137">AutoOpen 属性</span><span class="sxs-lookup"><span data-stu-id="9ebdd-137">AutoOpen Attribute</span></span>

<span data-ttu-id="9ebdd-138">`AutoOpen`アセンブリが参照されたときに名前空間またはモジュールを自動的に開く場合は、アセンブリに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-138">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="9ebdd-139">また、属性をモジュールに適用して、 `AutoOpen` 親モジュールまたは名前空間を開いたときに自動的にそのモジュールを開くようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-139">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="9ebdd-140">詳細については、「 [Autoopenattribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-140">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="9ebdd-141">RequireQualifiedAccess 属性</span><span class="sxs-lookup"><span data-stu-id="9ebdd-141">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="9ebdd-142">一部のモジュール、レコード、または共用体型では、属性を指定でき `RequireQualifiedAccess` ます。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-142">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="9ebdd-143">これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-143">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="9ebdd-144">一般的に使用される名前を定義する型でこの属性を戦略的に使用すると、名前の競合を避けることができるため、ライブラリの変更に対するコードの回復性が向上します。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-144">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="9ebdd-145">詳細については、「 [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ebdd-145">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ebdd-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ebdd-146">See also</span></span>

- [<span data-ttu-id="9ebdd-147">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="9ebdd-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9ebdd-148">名前空間</span><span class="sxs-lookup"><span data-stu-id="9ebdd-148">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="9ebdd-149">モジュール</span><span class="sxs-lookup"><span data-stu-id="9ebdd-149">Modules</span></span>](modules.md)
