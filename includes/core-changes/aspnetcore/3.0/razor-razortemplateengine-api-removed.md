---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032631"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="45226-101">Razor: RazorTemplateEngine API が削除されました</span><span class="sxs-lookup"><span data-stu-id="45226-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="45226-102">[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API が削除され、<xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="45226-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="45226-103">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45226-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45226-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="45226-104">Version introduced</span></span>

<span data-ttu-id="45226-105">3.0</span><span class="sxs-lookup"><span data-stu-id="45226-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="45226-106">以前の動作</span><span class="sxs-lookup"><span data-stu-id="45226-106">Old behavior</span></span>

<span data-ttu-id="45226-107">Razor ファイルのコードを解析し、生成するためにテンプレート エンジンを作成し、使用できます。</span><span class="sxs-lookup"><span data-stu-id="45226-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="45226-108">新しい動作</span><span class="sxs-lookup"><span data-stu-id="45226-108">New behavior</span></span>

<span data-ttu-id="45226-109">Razor ファイルのコードを解析し、生成するために、`RazorProjectEngine` を作成し、`RazorTemplateEngine` と同じ種類の情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="45226-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="45226-110">`RazorProjectEngine` からは追加の構成レベルも与えられます。</span><span class="sxs-lookup"><span data-stu-id="45226-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="45226-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="45226-111">Reason for change</span></span>

<span data-ttu-id="45226-112">`RazorTemplateEngine` と既存の実装の結合密度が高すぎました。</span><span class="sxs-lookup"><span data-stu-id="45226-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="45226-113">Razor の解析および生成パイプラインを正しく構成しようとするとき、この密結合によって問題が増えました。</span><span class="sxs-lookup"><span data-stu-id="45226-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45226-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="45226-114">Recommended action</span></span>

<span data-ttu-id="45226-115">`RazorTemplateEngine` ではなく `RazorProjectEngine` を使用します。</span><span class="sxs-lookup"><span data-stu-id="45226-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="45226-116">次の例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="45226-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="45226-117">RazorProjectEngine の作成と構成</span><span class="sxs-lookup"><span data-stu-id="45226-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="45226-118">Razor ファイルのコードを生成する</span><span class="sxs-lookup"><span data-stu-id="45226-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="45226-119">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="45226-119">Category</span></span>

<span data-ttu-id="45226-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="45226-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45226-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="45226-121">Affected APIs</span></span>

- [<span data-ttu-id="45226-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="45226-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="45226-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="45226-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
