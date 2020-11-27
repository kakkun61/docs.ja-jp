---
description: -nullable (C# コンパイラ オプション)
title: -nullable (C# コンパイラ オプション)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099225"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="b2107-103">-nullable (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="b2107-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="b2107-104">**-nullable** オプションを使用すると、Null 許容コンテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2107-104">The **-nullable** option lets you specify the nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2107-105">構文</span><span class="sxs-lookup"><span data-stu-id="b2107-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="b2107-106">引数</span><span class="sxs-lookup"><span data-stu-id="b2107-106">Arguments</span></span>

<span data-ttu-id="b2107-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b2107-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="b2107-108">`+` または **-nullable** を指定すると、コンパイラによって Null 許容コンテキストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="b2107-108">Specifying `+`, or **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="b2107-109">**-nullable** を指定しない場合に有効な `-` を指定すると、Null 許容コンテキストは無効になります。</span><span class="sxs-lookup"><span data-stu-id="b2107-109">Specifying `-`, which is in effect if you don't specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="b2107-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="b2107-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="b2107-111">Null 許容コンテキスト オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2107-111">Specifies the nullable context option.</span></span> <span data-ttu-id="b2107-112">有効または無効にする `+` または `-` に似ていますが、Null 許容のコンテキストをより細かく指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2107-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="b2107-113">`enable` 引数は、 **-nullable** の指定と同じですが、Null 許容のコンテキストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b2107-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="b2107-114">`disable` を指定すると、Null 許容コンテキストは無効になります。</span><span class="sxs-lookup"><span data-stu-id="b2107-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="b2107-115">**nullable: warning** のように `warnings` 引数を指定すると、Null 許容の警告コンテキストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="b2107-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="b2107-116">**-nullable:annotations** のように `annotations` 引数を指定すると、Null 許容の注釈コンテキストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="b2107-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2107-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2107-117">Remarks</span></span>

<span data-ttu-id="b2107-118">フロー分析は、実行可能コード内の変数に null 値が許容されるかどうかを推測するために使用します。</span><span class="sxs-lookup"><span data-stu-id="b2107-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="b2107-119">null 値が変数で許容されるかの推定は、変数の宣言されている null 許容とは無関係です。</span><span class="sxs-lookup"><span data-stu-id="b2107-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="b2107-120">メソッド呼び出しは、条件付きで省略される場合でも分析されます。</span><span class="sxs-lookup"><span data-stu-id="b2107-120">Method calls are analyzed even when they're conditionally omitted.</span></span> <span data-ttu-id="b2107-121">たとえば、リリース モードの <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="b2107-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="b2107-122">次の属性の注釈が付いたメソッド呼び出しも、フロー分析に影響します。</span><span class="sxs-lookup"><span data-stu-id="b2107-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="b2107-123">単純な実行前条件: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> と <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="b2107-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="b2107-124">単純な実行後条件: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> と <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="b2107-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="b2107-125">条件付きの実行後条件: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> および <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="b2107-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="b2107-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> の `DoesNotReturnIf(false)` など) と <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="b2107-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="b2107-127">メンバーの実行後条件: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> と <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="b2107-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2107-128">グローバルな Null 許容コンテキストは、生成されたコード ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="b2107-128">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="b2107-129">この設定でも、Null 許容のコンテキストは、生成済みとしてマークされているすべてのソース ファイルに対して "*無効になります*"。</span><span class="sxs-lookup"><span data-stu-id="b2107-129">Regardless of this setting, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="b2107-130">ファイルが生成済みとしてマークされる方法は 4 つあります。</span><span class="sxs-lookup"><span data-stu-id="b2107-130">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="b2107-131">.editorconfig で、そのファイルに適用されるセクションで `generated_code = true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2107-131">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="b2107-132">ファイルの先頭にあるコメントに `<auto-generated>` または `<auto-generated/>` を配置します。</span><span class="sxs-lookup"><span data-stu-id="b2107-132">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="b2107-133">これは、コメント内の任意の行に配置できますが、コメント ブロックはファイル内の最初の要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2107-133">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="b2107-134">ファイル名を *TemporaryGeneratedFile_* で開始します</span><span class="sxs-lookup"><span data-stu-id="b2107-134">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="b2107-135">ファイル名の末尾を *.designer.cs*、 *.generated.cs*、 *.g.cs*、または *.g.i.cs* にします。</span><span class="sxs-lookup"><span data-stu-id="b2107-135">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="b2107-136">ジェネレーターは、[`#nullable`](../preprocessor-directives/preprocessor-nullable.md) プリプロセッサ ディレクティブを使用してオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="b2107-136">Generators can opt-in using the [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="b2107-137">プロジェクトでこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="b2107-137">To set this compiler option in a project</span></span>

<span data-ttu-id="b2107-138">*.csproj* ファイルを編集して、`Project/PropertyGroup` 階層に `<Nullable>` タグを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2107-138">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="b2107-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2107-139">See also</span></span>

- [<span data-ttu-id="b2107-140">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="b2107-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b2107-141">`#nullable` プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b2107-141">`#nullable` preprocessor directive</span></span>](../preprocessor-directives/preprocessor-nullable.md)
- [<span data-ttu-id="b2107-142">Null 許容参照型</span><span class="sxs-lookup"><span data-stu-id="b2107-142">Nullable reference types</span></span>](../../nullable-references.md)
