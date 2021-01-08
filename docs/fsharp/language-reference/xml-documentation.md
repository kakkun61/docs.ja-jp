---
title: XML に関するドキュメント
description: 'コメントからドキュメントを生成するための F # のサポートについて説明します。'
ms.date: 09/15/2020
ms.openlocfilehash: 2f8788e79ea964143eecfaddbeb039474dd61f8e
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025017"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="62f1c-103">XML コメントを含むコードの文書化</span><span class="sxs-lookup"><span data-stu-id="62f1c-103">Document your code with XML comments</span></span>

<span data-ttu-id="62f1c-104">F # では、トリプルスラッシュ (///) コードコメントからドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-104">You can produce documentation from triple-slash (///) code comments in F#.</span></span> <span data-ttu-id="62f1c-105">XML コメントは、コードファイル (fs) ファイルまたは署名 (fsi.exe) ファイルの宣言の前に記述できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-105">XML comments can precede declarations in code files (.fs) or signature (.fsi) files.</span></span>

<span data-ttu-id="62f1c-106">XML 文書化コメントは、ユーザー定義型またはユーザー定義メンバーの定義の上に追加する特殊なコメントです。</span><span class="sxs-lookup"><span data-stu-id="62f1c-106">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="62f1c-107">このコメントが特殊な理由は、コンパイル時にコンパイラで処理して、XML 文書化ファイルを生成できることです。</span><span class="sxs-lookup"><span data-stu-id="62f1c-107">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="62f1c-108">コンパイラによって生成された XML ファイルは、.NET アセンブリと共に配布できます。これにより、Ide では、ツールヒントを使用して型またはメンバーに関する簡単な情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-108">The compiler-generated XML file can be distributed alongside your .NET assembly so that IDEs can use tooltips to show quick information about types or members.</span></span> <span data-ttu-id="62f1c-109">また、XML ファイルは、 [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) などのツールを使用して実行し、API 参照 web サイトを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-109">Additionally, the XML file can be run through tools like [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) to generate API reference websites.</span></span>

<span data-ttu-id="62f1c-110">XML ドキュメントコメントは、他のすべてのコメントと同様にコンパイラによって無視されます。ただし、コンパイル時にコメントの有効性と完全性を確認するために以下で説明するオプションを有効にする場合は除きます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-110">XML documentation comments, like all other comments, are ignored by the compiler, unless the options described below are enabled to check the validity and completeness of comments at compile time.</span></span>

<span data-ttu-id="62f1c-111">コンパイル時に XML ファイルを生成するには、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-111">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="62f1c-112">`GenerateDocumentationFile`プロジェクトファイルのセクションに要素を追加できます `<PropertyGroup>` `.fsproj` 。これにより、アセンブリと同じルートファイル名を持つ XML ファイルがプロジェクトディレクトリに生成されます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-112">You can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your `.fsproj` project file, which generates an XML file in the project directory with the same root filename as the assembly.</span></span> <span data-ttu-id="62f1c-113">例:</span><span class="sxs-lookup"><span data-stu-id="62f1c-113">For example:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- <span data-ttu-id="62f1c-114">Visual Studio を使用してアプリケーションを開発する場合は、プロジェクトを右クリックして、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="62f1c-115">プロパティ ダイアログ ボックスで、 **[ビルド]** タブをクリックし、 **[XML ドキュメント ファイル]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="62f1c-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="62f1c-116">コンパイラがファイルを書き込む場所を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-116">You can also change the location to which the compiler writes the file.</span></span>

<span data-ttu-id="62f1c-117">XML ドキュメントコメントを記述するには、XML タグの有無にかかわらず、2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-117">There are two ways to write XML documentation comments: with and without XML tags.</span></span> <span data-ttu-id="62f1c-118">どちらも、3つのスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-118">Both use triple-slash comments.</span></span>

## <a name="comments-without-xml-tags"></a><span data-ttu-id="62f1c-119">XML タグのないコメント</span><span class="sxs-lookup"><span data-stu-id="62f1c-119">Comments without XML tags</span></span>

<span data-ttu-id="62f1c-120">コメントがで `///` 始まらない場合 `<` 、コメントテキスト全体が、直後に続くコードコンストラクターの概要ドキュメントとして取得されます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-120">If a `///` comment does not start with a `<`, then the entire comment text is taken as the summary documentation for the code construct that immediately follows.</span></span> <span data-ttu-id="62f1c-121">各コンストラクトの概要のみを記述する場合は、このメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-121">Use this method when you want to write only a brief summary for each construct.</span></span>

<span data-ttu-id="62f1c-122">コメントはドキュメントの準備中に XML にエンコードされるため、、、などの文字を `<` `>` `&` エスケープする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="62f1c-122">The comment is encoded to XML during documentation preparation, so characters such as `<`, `>`, and `&` need not be escaped.</span></span> <span data-ttu-id="62f1c-123">概要タグを明示的に指定しない場合は、 **param** や returns タグなど、他の **タグを** 指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="62f1c-123">If you don't specify a summary tag explicitly, you should not specify other tags, such as **param** or **returns** tags.</span></span>

<span data-ttu-id="62f1c-124">次の例は、XML タグのない代替メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="62f1c-124">The following example shows the alternative method, without XML tags.</span></span> <span data-ttu-id="62f1c-125">この例では、コメント内のテキスト全体が概要と見なされます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-125">In this example, the entire text in the comment is considered a summary.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a><span data-ttu-id="62f1c-126">XML タグの付いたコメント</span><span class="sxs-lookup"><span data-stu-id="62f1c-126">Comments with XML tags</span></span>

<span data-ttu-id="62f1c-127">コメントの本文が (通常は) で始まる場合 `<` `<summary>` 、xml タグを使用して xml 形式のコメント本文として扱われます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-127">If a comment body begins with `<` (normally `<summary>`), then it is treated as an XML formatted comment body using XML tags.</span></span> <span data-ttu-id="62f1c-128">この2番目の方法では、簡単な概要、追加の解説、各パラメーターのドキュメント、スローされる例外の種類、および戻り値の説明を個別に指定できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-128">This second enables you to specify separate notes for a short summary, additional remarks, documentation for each parameter and type parameter and exceptions thrown, and a description of the return value.</span></span>

<span data-ttu-id="62f1c-129">次に、シグネチャファイル内の一般的な XML ドキュメントコメントを示します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-129">The following is a typical XML documentation comment in a signature file:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a><span data-ttu-id="62f1c-130">推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="62f1c-130">Recommended Tags</span></span>

<span data-ttu-id="62f1c-131">XML タグを使用する場合、F # の XML コードコメントで認識される外側のタグについて、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-131">If you are using XML tags, the following table describes the outer tags recognized in F# XML code comments.</span></span>

| <span data-ttu-id="62f1c-132">タグ構文</span><span class="sxs-lookup"><span data-stu-id="62f1c-132">Tag syntax</span></span>                                  | <span data-ttu-id="62f1c-133">説明</span><span class="sxs-lookup"><span data-stu-id="62f1c-133">Description</span></span> |
|---------------------------------------------|-----------|
| <span data-ttu-id="62f1c-134">`<summary>`**_本文_**`</summary>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-134">`<summary>`**_text_**`</summary>`</span></span>           | <span data-ttu-id="62f1c-135">*テキスト* がプログラム要素の簡単な説明であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-135">Specifies that *text* is a brief description of the program element.</span></span> <span data-ttu-id="62f1c-136">説明は、通常、1つまたは2つの文です。</span><span class="sxs-lookup"><span data-stu-id="62f1c-136">The description is usually one or two sentences.</span></span>|
| <span data-ttu-id="62f1c-137">`<remarks>`**_本文_**`</remarks>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-137">`<remarks>`**_text_**`</remarks>`</span></span>           | <span data-ttu-id="62f1c-138">*Text* に program 要素に関する補足情報が含まれていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-138">Specifies that *text* contains supplementary information about the program element.</span></span>|
| <span data-ttu-id="62f1c-139">`<param name="`**_名前_** `">`**_説明_**`</param>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-139">`<param name="`**_name_**`">`**_description_**`</param>`</span></span> | <span data-ttu-id="62f1c-140">関数またはメソッドのパラメーターの名前と説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-140">Specifies the name and description for a function or method parameter.</span></span>|
| <span data-ttu-id="62f1c-141">`<typeparam name="`**_名前_** `">`**_説明_**`</typeparam>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-141">`<typeparam name="`**_name_**`">`**_description_**`</typeparam>`</span></span> | <span data-ttu-id="62f1c-142">型パラメーターの名前と説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-142">Specifies the name and description for a type parameter.</span></span>|
| <span data-ttu-id="62f1c-143">`<returns>`**_本文_**`</returns>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-143">`<returns>`**_text_**`</returns>`</span></span>           | <span data-ttu-id="62f1c-144">関数またはメソッドの戻り値を *テキスト* に記述するように指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-144">Specifies that *text* describes the return value of a function or method.</span></span>|
| <span data-ttu-id="62f1c-145">`<exception cref="`**_型_** `">`**_説明_**`</exception>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-145">`<exception cref="`**_type_**`">`**_description_**`</exception>`</span></span> |<span data-ttu-id="62f1c-146">生成できる例外の種類と、その例外がスローされる状況を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-146">Specifies the type of exception that can be generated and the circumstances under which it is thrown.</span></span>|
| <span data-ttu-id="62f1c-147">`<seealso cref="`**_「_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-147">`<seealso cref="`**_reference_**`"/>`</span></span>      | <span data-ttu-id="62f1c-148">別の種類のドキュメントへのリンクも参照してください。</span><span class="sxs-lookup"><span data-stu-id="62f1c-148">Specifies a See Also link to the documentation for another type.</span></span> <span data-ttu-id="62f1c-149">*参照* は、XML ドキュメントファイルに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="62f1c-149">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="62f1c-150">ドキュメントページの下部には、通常、リンクも表示されます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-150">See Also links usually appear at the bottom of a documentation page.</span></span>|

<span data-ttu-id="62f1c-151">次の表では、説明セクション内で使用するタグについて説明します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-151">The following table describes the tags for use inside description sections:</span></span>

| <span data-ttu-id="62f1c-152">タグ構文</span><span class="sxs-lookup"><span data-stu-id="62f1c-152">Tag syntax</span></span>                                | <span data-ttu-id="62f1c-153">説明</span><span class="sxs-lookup"><span data-stu-id="62f1c-153">Description</span></span> |
|-------------------------------------------|-------------|
| <span data-ttu-id="62f1c-154">`<para>`**_本文_**`</para>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-154">`<para>`**_text_**`</para>`</span></span>               | <span data-ttu-id="62f1c-155">テキストの段落を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-155">Specifies a paragraph of text.</span></span> <span data-ttu-id="62f1c-156">これは、 **コメント** タグ内のテキストを区切るために使用されます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-156">This is used to separate text inside the **remarks** tag.</span></span>|
| <span data-ttu-id="62f1c-157">`<code>`**_本文_**`</code>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-157">`<code>`**_text_**`</code>`</span></span>               | <span data-ttu-id="62f1c-158">*テキスト* が複数行のコードであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-158">Specifies that *text* is multiple lines of code.</span></span> <span data-ttu-id="62f1c-159">このタグは、ドキュメントジェネレーターがコードに適したフォントでテキストを表示するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-159">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="62f1c-160">`<paramref name="`**_指定_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-160">`<paramref name="`**_name_**`"/>`</span></span>         | <span data-ttu-id="62f1c-161">同じドキュメントコメント内のパラメーターへの参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-161">Specifies a reference to a parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="62f1c-162">`<typeparamref name="`**_指定_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-162">`<typeparamref name="`**_name_**`"/>`</span></span>     | <span data-ttu-id="62f1c-163">同じドキュメントコメント内の型パラメーターへの参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-163">Specifies a reference to a type parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="62f1c-164">`<c>`**_本文_**`</c>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-164">`<c>`**_text_**`</c>`</span></span>                     | <span data-ttu-id="62f1c-165">*テキスト* がインラインコードであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-165">Specifies that *text* is inline code.</span></span> <span data-ttu-id="62f1c-166">このタグは、ドキュメントジェネレーターがコードに適したフォントでテキストを表示するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-166">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="62f1c-167">`<see cref="`**_参照_** `">`**_テキスト_**`</see>`</span><span class="sxs-lookup"><span data-stu-id="62f1c-167">`<see cref="`**_reference_**`">`**_text_**`</see>`</span></span> | <span data-ttu-id="62f1c-168">別のプログラム要素へのインラインリンクを指定します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-168">Specifies an inline link to another program element.</span></span> <span data-ttu-id="62f1c-169">*参照* は、XML ドキュメントファイルに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="62f1c-169">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="62f1c-170">*テキスト* は、リンクに表示されるテキストです。</span><span class="sxs-lookup"><span data-stu-id="62f1c-170">The *text* is the text shown in the link.</span></span>|

### <a name="user-defined-tags"></a><span data-ttu-id="62f1c-171">ユーザー定義タグ</span><span class="sxs-lookup"><span data-stu-id="62f1c-171">User-defined tags</span></span>

<span data-ttu-id="62f1c-172">前のタグは、F # コンパイラおよび一般的な F # エディターツールによって認識されるタグを表します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-172">The previous tags represent those that are recognized by the F# compiler and typical F# editor tooling.</span></span> <span data-ttu-id="62f1c-173">ただし、ユーザー独自のタグも自由に定義できます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-173">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="62f1c-174">Fsdocs などのツールでは、のような余分なタグがサポート対象と [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) なります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-174">Tools like fsdocs bring support for extra tags like [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md).</span></span>
<span data-ttu-id="62f1c-175">カスタムまたは社内ドキュメント生成ツールを標準タグと共に使用して、HTML から PDF への複数の出力形式をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-175">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="compile-time-checking"></a><span data-ttu-id="62f1c-176">コンパイル時のチェック</span><span class="sxs-lookup"><span data-stu-id="62f1c-176">Compile-time checking</span></span>

<span data-ttu-id="62f1c-177">が有効になっている場合 `--warnon:3390` 、コンパイラは、XML の構文と、タグとタグで参照されるパラメーターを検証し `<param>` `<paramref>` ます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-177">When `--warnon:3390` is enabled, the compiler verifies the syntax of the XML and the parameters referred to in `<param>` and `<paramref>` tags.</span></span>

## <a name="documenting-f-constructs"></a><span data-ttu-id="62f1c-178">F # コンストラクトの文書化</span><span class="sxs-lookup"><span data-stu-id="62f1c-178">Documenting F# Constructs</span></span>

<span data-ttu-id="62f1c-179">モジュール、メンバー、共用体ケース、レコードフィールドなどの F # コンストラクトは、宣言の直前にコメントによって文書化され `///` ます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-179">F# constructs such as modules, members, union cases, and record fields are documented by a `///` comment immediately prior to their declaration.</span></span>
<span data-ttu-id="62f1c-180">必要に応じて、 `///` 引数リストの前にコメントを付けることによって、クラスの暗黙的なコンストラクターを記述します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-180">If needed, implicit constructors of classes are documented by giving a `///` comment prior to the argument list.</span></span> <span data-ttu-id="62f1c-181">例:</span><span class="sxs-lookup"><span data-stu-id="62f1c-181">For example:</span></span>

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a><span data-ttu-id="62f1c-182">制限事項</span><span class="sxs-lookup"><span data-stu-id="62f1c-182">Limitations</span></span>

<span data-ttu-id="62f1c-183">C# やその他の .NET 言語の XML ドキュメントの一部の機能は、F # ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="62f1c-183">Some features of XML documentation in C# and other .NET languages are not supported in F#.</span></span>

- <span data-ttu-id="62f1c-184">F # では、相互参照では、対応するシンボルの完全な XML シグネチャ (たとえば) を使用する必要があり `cref="T:System.Console"` ます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-184">In F#, cross-references must use the full XML signature of the corresponding symbol, for example `cref="T:System.Console"`.</span></span>
  <span data-ttu-id="62f1c-185">などの単純な C# スタイルの相互参照 `cref="Console"` は、完全な XML シグネチャには対応していません。これらの要素は、F # コンパイラによってチェックされません。</span><span class="sxs-lookup"><span data-stu-id="62f1c-185">Simple C#-style cross-references such as `cref="Console"` are not elaborated to full XML signatures and these elements are not checked by the F# compiler.</span></span> <span data-ttu-id="62f1c-186">一部のドキュメントツールでは、後続の処理でこれらの相互参照を使用できますが、完全なシグネチャを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-186">Some documentation tooling may allow the use of these cross-references by subsequent processing, but the full signatures should be used.</span></span>

- <span data-ttu-id="62f1c-187">タグは `<include>` 、 `<inheritdoc>` F # コンパイラではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="62f1c-187">The tags `<include>`, `<inheritdoc>` are not supported by the F# compiler.</span></span> <span data-ttu-id="62f1c-188">これらが使用されている場合、エラーは発生しませんが、生成されたドキュメントに影響を与えることなく、単に生成されたドキュメントファイルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-188">No error is given if they are used, but they are simply copied to the generated documentation file without otherwise affecting the documentation generated.</span></span>

- <span data-ttu-id="62f1c-189">が使用されている場合でも、相互参照は F # コンパイラによってチェックされません `-warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="62f1c-189">Cross-references are not checked by the F# compiler, even when `-warnon:3390` is used.</span></span>

- <span data-ttu-id="62f1c-190">タグとで使用される名前は、 `<typeparam>` が使用されている `<typeparamref>` 場合でも、F # コンパイラによってチェックされません `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="62f1c-190">The names used in the tags `<typeparam>` and `<typeparamref>` are not checked by the F# compiler, even when `--warnon:3390` is used.</span></span>

- <span data-ttu-id="62f1c-191">が使用されている場合でも、ドキュメントが見つからない場合、警告は与えられません `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="62f1c-191">No warnings are given if documentation is missing, even when `--warnon:3390` is used.</span></span>

## <a name="recommendations"></a><span data-ttu-id="62f1c-192">推奨事項</span><span class="sxs-lookup"><span data-stu-id="62f1c-192">Recommendations</span></span>

<span data-ttu-id="62f1c-193">コードを文書化することをお勧めするのには、さまざまな理由があります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-193">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="62f1c-194">ここでは、F # コードで XML ドキュメントタグを使用するときに理解しておく必要があるベストプラクティス、一般的なユースケースシナリオ、および重要事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="62f1c-194">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your F# code.</span></span>

- <span data-ttu-id="62f1c-195">`--warnon:3390`Xml ドキュメントが有効な xml であることを確認するために、コードでオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="62f1c-195">Enable the option `--warnon:3390` in your code to help ensure your XML documentation is valid XML.</span></span>

- <span data-ttu-id="62f1c-196">実装から長い XML ドキュメントコメントを分離するために、署名ファイルを追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="62f1c-196">Consider adding signature files to separate long XML documentation comments from your implementation.</span></span>

- <span data-ttu-id="62f1c-197">整合性を保つため、一般に公開されているすべての型とそのメンバーを文書化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-197">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="62f1c-198">必要な文書化はすべて実行してください。</span><span class="sxs-lookup"><span data-stu-id="62f1c-198">If you must do it, do it all.</span></span>

- <span data-ttu-id="62f1c-199">最小限のモジュール、型、およびそれらのメンバーには、通常の `///` コメントまたは `<summary>` タグが必要です。</span><span class="sxs-lookup"><span data-stu-id="62f1c-199">At a bare minimum, modules, types, and their members should have a plain `///` comment or `<summary>` tag.</span></span> <span data-ttu-id="62f1c-200">これは、F # 編集ツールのオートコンプリートツールヒントウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="62f1c-200">This will show in an autocompletion tooltip window in F# editing tools.</span></span>

- <span data-ttu-id="62f1c-201">文書化のテキストは、句点で終わる完全な文を使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62f1c-201">Documentation text should be written using complete sentences ending with full stops.</span></span>

## <a name="see-also"></a><span data-ttu-id="62f1c-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="62f1c-202">See also</span></span>

- <span data-ttu-id="62f1c-203">[C# XML ドキュメントコメント &#40;C&#35; プログラミングガイド&#41;](../../csharp/programming-guide/xmldoc/index.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62f1c-203">[C# XML Documentation Comments &#40;C&#35; Programming Guide&#41;](../../csharp/programming-guide/xmldoc/index.md).</span></span>
- [<span data-ttu-id="62f1c-204">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="62f1c-204">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="62f1c-205">コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="62f1c-205">Compiler Options</span></span>](compiler-options.md)
