---
title: コンパイラ ディレクティブ
description: 'F # 言語のプリプロセッサディレクティブ、条件付きコンパイルディレクティブ、行ディレクティブ、およびコンパイラディレクティブについて説明します。'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: ff106339478c3413dc6458b12f12e1d3f9cd1fe5
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438176"
---
# <a name="compiler-directives"></a><span data-ttu-id="bb81c-103">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-103">Compiler Directives</span></span>

<span data-ttu-id="bb81c-104">このトピックでは、プロセッサ ディレクティブとコンパイラ ディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-104">This topic describes processor directives and compiler directives.</span></span>

## <a name="preprocessor-directives"></a><span data-ttu-id="bb81c-105">プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-105">Preprocessor Directives</span></span>

<span data-ttu-id="bb81c-106">プリプロセッサ ディレクティブは、# シンボルで始まり、独立した行に記述されます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-106">A preprocessor directive is prefixed with the # symbol and appears on a line by itself.</span></span> <span data-ttu-id="bb81c-107">プリプロセッサ ディレクティブは、コンパイラ自体の前に実行されるプリプロセッサにより解釈されます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-107">It is interpreted by the preprocessor, which runs before the compiler itself.</span></span>

<span data-ttu-id="bb81c-108">次の表に、F# で使用できるプリプロセッサ ディレクティブの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-108">The following table lists the preprocessor directives that are available in F#.</span></span>

|<span data-ttu-id="bb81c-109">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-109">Directive</span></span>|<span data-ttu-id="bb81c-110">説明</span><span class="sxs-lookup"><span data-stu-id="bb81c-110">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="bb81c-111">`#if`*シンボル*</span><span class="sxs-lookup"><span data-stu-id="bb81c-111">`#if` *symbol*</span></span>|<span data-ttu-id="bb81c-112">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-112">Supports conditional compilation.</span></span> <span data-ttu-id="bb81c-113">シンボルが定義されている場合、の後にあるセクションのコードが `#if` 含まれます。 *symbol*</span><span class="sxs-lookup"><span data-stu-id="bb81c-113">Code in the section after the `#if` is included if the *symbol* is defined.</span></span> <span data-ttu-id="bb81c-114">記号は、で否定することもでき `!` ます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-114">The symbol can also be negated with `!`.</span></span>|
|`#else`|<span data-ttu-id="bb81c-115">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-115">Supports conditional compilation.</span></span> <span data-ttu-id="bb81c-116">前の `#if` で使用したシンボルが定義されていない場合に含めるコードのセクションをマークします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-116">Marks a section of code to include if the symbol used with the previous `#if` is not defined.</span></span>|
|`#endif`|<span data-ttu-id="bb81c-117">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-117">Supports conditional compilation.</span></span> <span data-ttu-id="bb81c-118">コードの条件付きセクションの末尾をマークします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-118">Marks the end of a conditional section of code.</span></span>|
|<span data-ttu-id="bb81c-119">`#`直線 *int*、</span><span class="sxs-lookup"><span data-stu-id="bb81c-119">`#`[line] *int*,</span></span><br/><span data-ttu-id="bb81c-120">`#`直線 *int* *文字列*、</span><span class="sxs-lookup"><span data-stu-id="bb81c-120">`#`[line] *int* *string*,</span></span><br/><span data-ttu-id="bb81c-121">`#`直線 *int* *逐語的文字列*</span><span class="sxs-lookup"><span data-stu-id="bb81c-121">`#`[line] *int* *verbatim-string*</span></span>|<span data-ttu-id="bb81c-122">デバッグ用に、元のソース コードの行とファイル名を示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-122">Indicates the original source code line and file name, for debugging.</span></span> <span data-ttu-id="bb81c-123">この機能は、F# ソース コードを生成するツール用に用意されています。</span><span class="sxs-lookup"><span data-stu-id="bb81c-123">This feature is provided for tools that generate F# source code.</span></span>|
|<span data-ttu-id="bb81c-124">`#nowarn`*警告コード*</span><span class="sxs-lookup"><span data-stu-id="bb81c-124">`#nowarn` *warningcode*</span></span>|<span data-ttu-id="bb81c-125">コンパイラ警告を無効にします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-125">Disables a compiler warning or warnings.</span></span> <span data-ttu-id="bb81c-126">警告を無効にするには、コンパイラ出力で警告の番号を確認し、その番号を引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-126">To disable a warning, find its number from the compiler output and include it in quotation marks.</span></span> <span data-ttu-id="bb81c-127">"FS" プレフィックスを省略します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-127">Omit the "FS" prefix.</span></span> <span data-ttu-id="bb81c-128">1 つの行で複数の警告番号を無効にするには、それぞれの番号を引用符で囲んだうえで各文字列をスペースで区切ります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-128">To disable multiple warning numbers on the same line, include each number in quotation marks, and separate each string by a space.</span></span> <span data-ttu-id="bb81c-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-129">For example:</span></span>

`#nowarn "9" "40"`

<span data-ttu-id="bb81c-130">警告を無効にした場合の影響は、ファイル全体 (ディレクティブの前にあるファイルの部分を含む) に適用されます |。</span><span class="sxs-lookup"><span data-stu-id="bb81c-130">The effect of disabling a warning applies to the entire file, including portions of the file that precede the directive.|</span></span>

## <a name="conditional-compilation-directives"></a><span data-ttu-id="bb81c-131">条件付きコンパイル ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-131">Conditional Compilation Directives</span></span>

<span data-ttu-id="bb81c-132">これらのディレクティブのいずれかによって非アクティブ化されたコードは、Visual Studio Code エディターでは淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-132">Code that is deactivated by one of these directives appears dimmed in the Visual Studio Code Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="bb81c-133">条件付きコンパイル ディレクティブの動作は、他の言語と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="bb81c-133">The behavior of the conditional compilation directives is not the same as it is in other languages.</span></span> <span data-ttu-id="bb81c-134">たとえば、シンボルを含むブール式を使用することはできません。また、`true` および `false` には特別な意味はありません。</span><span class="sxs-lookup"><span data-stu-id="bb81c-134">For example, you cannot use Boolean expressions involving symbols, and `true` and `false` have no special meaning.</span></span> <span data-ttu-id="bb81c-135">`if` ディレクティブで使用するシンボルは、コマンド ラインまたはプロジェクト設定で定義する必要があります。`define` プリプロセッサ ディレクティブは存在しません。</span><span class="sxs-lookup"><span data-stu-id="bb81c-135">Symbols that you use in the `if` directive must be defined by the command line or in the project settings; there is no `define` preprocessor directive.</span></span>

<span data-ttu-id="bb81c-136">次のコードは、`#if` ディレクティブ、`#else` ディレクティブ、および `#endif` ディレクティブの使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb81c-136">The following code illustrates the use of the `#if`, `#else`, and `#endif` directives.</span></span> <span data-ttu-id="bb81c-137">この例では、`function1` の定義の 2 つのバージョンがコードに含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb81c-137">In this example, the code contains two versions of the definition of `function1`.</span></span> <span data-ttu-id="bb81c-138">`VERSION1` [-Define コンパイラオプション](./compiler-options.md)を使用してを定義すると、ディレクティブとディレクティブの間のコード `#if` `#else` がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-138">When `VERSION1` is defined by using the [-define compiler option](./compiler-options.md), the code between the `#if` directive and the `#else` directive is activated.</span></span> <span data-ttu-id="bb81c-139">それ以外の場合、`#else` と `#endif` の間にあるコードがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-139">Otherwise, the code between `#else` and `#endif` is activated.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

<span data-ttu-id="bb81c-140">F# には、`#define` プリプロセッサ ディレクティブはありません。</span><span class="sxs-lookup"><span data-stu-id="bb81c-140">There is no `#define` preprocessor directive in F#.</span></span> <span data-ttu-id="bb81c-141">`#if` ディレクティブで使用するシンボルを定義するには、コンパイラ オプションまたはプロジェクト設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-141">You must use the compiler option or project settings to define the symbols used by the `#if` directive.</span></span>

<span data-ttu-id="bb81c-142">条件付きコンパイル ディレクティブは、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-142">Conditional compilation directives can be nested.</span></span> <span data-ttu-id="bb81c-143">プリプロセッサ ディレクティブでは、インデントに意味はありません。</span><span class="sxs-lookup"><span data-stu-id="bb81c-143">Indentation is not significant for preprocessor directives.</span></span>

<span data-ttu-id="bb81c-144">また、シンボルをで反転させることもでき `!` ます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-144">You can also negate a symbol with `!`.</span></span> <span data-ttu-id="bb81c-145">この例では、文字列の値は、デバッグ _されていない_ 場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-145">In this example, a string's value is something only when _not_ debugging:</span></span>

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a><span data-ttu-id="bb81c-146">行ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-146">Line Directives</span></span>

<span data-ttu-id="bb81c-147">ビルド時にコンパイラは、各エラーが発生した行番号を参照して、F# コード内のエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-147">When building, the compiler reports errors in F# code by referencing line numbers on which each error occurs.</span></span> <span data-ttu-id="bb81c-148">これらの行番号は、ファイル内の最初の行から 1 で始まります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-148">These line numbers start at 1 for the first line in a file.</span></span> <span data-ttu-id="bb81c-149">ただし、別のツールから F# ソース コードを生成している場合、生成されたコードの行番号は、通常、重要ではありません。これは、生成された F# コード内のエラーは、別のソースから発生する可能性が高いためです。</span><span class="sxs-lookup"><span data-stu-id="bb81c-149">However, if you are generating F# source code from another tool, the line numbers in the generated code are generally not of interest, because the errors in the generated F# code most likely arise from another source.</span></span> <span data-ttu-id="bb81c-150">`#line` ディレクティブを使用すると、F# ソース コードを生成するツールの作成者が、元の行番号およびソース ファイルに関する情報を、生成された F# コードに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-150">The `#line` directive provides a way for authors of tools that generate F# source code to pass information about the original line numbers and source files to the generated F# code.</span></span>

<span data-ttu-id="bb81c-151">`#line` ディレクティブを使用する場合、ファイル名を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-151">When you use the `#line` directive, file names must be enclosed in quotation marks.</span></span> <span data-ttu-id="bb81c-152">パスでバックスラッシュ文字を使用するには、文字列の前に逐語的トークン (`@`) がある場合を除き、バックスラッシュ文字をエスケープする必要があります。エスケープするには、バックスラッシュ文字を 1 つではなく、2 つ使用します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-152">Unless the verbatim token (`@`) appears in front of the string, you must escape backslash characters by using two backslash characters instead of one in order to use them in the path.</span></span> <span data-ttu-id="bb81c-153">有効な行トークンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-153">The following are valid line tokens.</span></span> <span data-ttu-id="bb81c-154">これらの例では、ツールを使用して元のファイル `Script1` を実行したときに F# コード ファイルが自動生成され、これらのディレクティブがある位置のコードが `Script1` ファイルの 25 行目のトークンから生成されるものと仮定します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-154">In these examples, assume that the original file `Script1` results in an automatically generated F# code file when it is run through a tool, and that the code at the location of these directives is generated from some tokens at line 25 in file `Script1`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

<span data-ttu-id="bb81c-155">これらのトークンは、この場所で生成された F# コードが、`Script1` 内の行 `25` またはその近くにあるなんらかの構成要素から派生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-155">These tokens indicate that the F# code generated at this location is derived from some constructs at or near line `25` in `Script1`.</span></span>

## <a name="compiler-directives"></a><span data-ttu-id="bb81c-156">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-156">Compiler Directives</span></span>

<span data-ttu-id="bb81c-157">コンパイラ ディレクティブは、# 記号で始まるという点でプリプロセッサ ディレクティブに似ていますが、プリプロセッサが解釈するのではなく、コンパイラが解釈して対応できるように放置されます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-157">Compiler directives resemble preprocessor directives, because they are prefixed with a # sign, but instead of being interpreted by the preprocessor, they are left for the compiler to interpret and act on.</span></span>

<span data-ttu-id="bb81c-158">次の表に、F# で使用できるコンパイラ ディレクティブの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bb81c-158">The following table lists the compiler directive that is available in F#.</span></span>

|<span data-ttu-id="bb81c-159">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="bb81c-159">Directive</span></span>|<span data-ttu-id="bb81c-160">説明</span><span class="sxs-lookup"><span data-stu-id="bb81c-160">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="bb81c-161">`#light` ["on" &#124; "off"]</span><span class="sxs-lookup"><span data-stu-id="bb81c-161">`#light` ["on"&#124;"off"]</span></span>|<span data-ttu-id="bb81c-162">他のバージョンの ML との互換性を保つために、軽量構文を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="bb81c-162">Enables or disables lightweight syntax, for compatibility with other versions of ML.</span></span> <span data-ttu-id="bb81c-163">既定では、軽量構文は有効です。</span><span class="sxs-lookup"><span data-stu-id="bb81c-163">By default, lightweight syntax is enabled.</span></span> <span data-ttu-id="bb81c-164">冗語構文は常に有効です。</span><span class="sxs-lookup"><span data-stu-id="bb81c-164">Verbose syntax is always enabled.</span></span> <span data-ttu-id="bb81c-165">したがって、軽量構文と冗語構文の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb81c-165">Therefore, you can use both lightweight syntax and verbose syntax.</span></span> <span data-ttu-id="bb81c-166">ディレクティブ `#light` は `#light "on"` と同等です。</span><span class="sxs-lookup"><span data-stu-id="bb81c-166">The directive `#light` by itself is equivalent to `#light "on"`.</span></span> <span data-ttu-id="bb81c-167">`#light "off"` を指定した場合は、すべての言語構成要素に冗語構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb81c-167">If you specify `#light "off"`, you must use verbose syntax for all language constructs.</span></span> <span data-ttu-id="bb81c-168">F# のドキュメント内の構文は、軽量構文の使用を前提として記述されています。</span><span class="sxs-lookup"><span data-stu-id="bb81c-168">Syntax in the documentation for F# is presented with the assumption that you are using lightweight syntax.</span></span> <span data-ttu-id="bb81c-169">詳細については、「 [Verbose 構文](verbose-syntax.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb81c-169">For more information, see [Verbose Syntax](verbose-syntax.md).</span></span>|

<span data-ttu-id="bb81c-170">インタープリター (fsi.exe) のディレクティブについては、「 [F # を使用した対話型プログラミング](../tools/fsharp-interactive/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb81c-170">For interpreter (fsi.exe) directives, see [Interactive Programming with F#](../tools/fsharp-interactive/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb81c-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb81c-171">See also</span></span>

- [<span data-ttu-id="bb81c-172">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="bb81c-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="bb81c-173">コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="bb81c-173">Compiler Options</span></span>](compiler-options.md)
