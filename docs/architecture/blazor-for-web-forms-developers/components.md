---
title: を使用して再利用可能な UI コンポーネントを構築する Blazor
description: を使用して再利用可能な UI コンポーネントを構築する方法 Blazor と、それらを ASP.NET Web フォームコントロールと比較する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: fd560c84c095dffc3718a7709af904d9ba722a18
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512770"
---
# <a name="build-reusable-ui-components-with-no-locblazor"></a><span data-ttu-id="5d186-103">を使用して再利用可能な UI コンポーネントを構築する Blazor</span><span class="sxs-lookup"><span data-stu-id="5d186-103">Build reusable UI components with Blazor</span></span>

<span data-ttu-id="5d186-104">ASP.NET Web フォームに関するすばらしい点の1つは、再利用可能なユーザーインターフェイス (UI) コードを再利用可能な UI コントロールにカプセル化できるようにする方法です。</span><span class="sxs-lookup"><span data-stu-id="5d186-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="5d186-105">カスタムユーザーコントロールは、 *.ascx* ファイルを使用してマークアップで定義できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="5d186-106">デザイナーを完全にサポートするコードで、複雑なサーバーコントロールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="5d186-107">Blazor では、 *コンポーネント* による UI カプセル化もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5d186-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="5d186-108">コンポーネント:</span><span class="sxs-lookup"><span data-stu-id="5d186-108">A component:</span></span>

- <span data-ttu-id="5d186-109">は、UI の自己完結型のチャンクです。</span><span class="sxs-lookup"><span data-stu-id="5d186-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="5d186-110">は、独自の状態およびレンダリングロジックを保持します。</span><span class="sxs-lookup"><span data-stu-id="5d186-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="5d186-111">UI イベントハンドラーを定義し、入力データにバインドして、独自のライフサイクルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="5d186-112">は、通常、Razor 構文を使用する *razor* ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="5d186-113">Razor の概要</span><span class="sxs-lookup"><span data-stu-id="5d186-113">An introduction to Razor</span></span>

<span data-ttu-id="5d186-114">Razor は、HTML および C# に基づく軽量のマークアップテンプレート言語です。</span><span class="sxs-lookup"><span data-stu-id="5d186-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="5d186-115">Razor を使用すると、マークアップと C# のコードをシームレスに切り替えて、コンポーネントのレンダリングロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="5d186-116">*Razor* ファイルがコンパイルされると、レンダリングロジックは .net クラスで構造化された方法でキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="5d186-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="5d186-117">コンパイル済みクラスの名前は、 *razor* ファイル名から取得されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="5d186-118">名前空間は、プロジェクトの既定の名前空間およびフォルダーパスから取得されます。また、ディレクティブを使用して名前空間を明示的に指定することもでき `@namespace` ます (以下の Razor ディレクティブについてはこちらを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5d186-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="5d186-119">コンポーネントのレンダリングロジックは、C# を使用して動的なロジックが追加された通常の HTML マークアップを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="5d186-120">`@`文字は、C# に移行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="5d186-121">Razor は、通常、HTML に切り替えたときに理解することが賢明です。</span><span class="sxs-lookup"><span data-stu-id="5d186-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="5d186-122">たとえば、次のコンポーネントは、 `<p>` 現在の時刻を使用してタグをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="5d186-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="5d186-123">C# 式の開始と終了を明示的に指定するには、かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d186-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="5d186-124">Razor では、レンダリングロジックで C# の制御フローを簡単に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="5d186-125">たとえば、次のような HTML を条件付きでレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="5d186-126">または、次のような通常の C# ループを使用して項目の一覧を生成することもでき `foreach` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="5d186-127">Razor ディレクティブは、ASP.NET Web フォームのディレクティブと同様に、Razor コンポーネントのコンパイル方法の多くの側面を制御します。</span><span class="sxs-lookup"><span data-stu-id="5d186-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="5d186-128">コンポーネントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5d186-128">Examples include the component's:</span></span>

- <span data-ttu-id="5d186-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="5d186-129">Namespace</span></span>
- <span data-ttu-id="5d186-130">基底クラス</span><span class="sxs-lookup"><span data-stu-id="5d186-130">Base class</span></span>
- <span data-ttu-id="5d186-131">実装されたインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d186-131">Implemented interfaces</span></span>
- <span data-ttu-id="5d186-132">ジェネリックパラメーター</span><span class="sxs-lookup"><span data-stu-id="5d186-132">Generic parameters</span></span>
- <span data-ttu-id="5d186-133">[インポートされた名前空間]</span><span class="sxs-lookup"><span data-stu-id="5d186-133">Imported namespaces</span></span>
- <span data-ttu-id="5d186-134">ルート</span><span class="sxs-lookup"><span data-stu-id="5d186-134">Routes</span></span>

<span data-ttu-id="5d186-135">Razor ディレクティブは、文字で始まり、 `@` 通常、ファイルの先頭にある新しい行の先頭で使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="5d186-136">たとえば、ディレクティブは `@namespace` コンポーネントの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="5d186-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="5d186-137">次の表は、で使用されるさまざまな Razor ディレクティブ Blazor と、それらが存在する場合の ASP.NET Web フォームに相当するものをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="5d186-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="5d186-138">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="5d186-138">Directive</span></span>    |<span data-ttu-id="5d186-139">説明</span><span class="sxs-lookup"><span data-stu-id="5d186-139">Description</span></span>|<span data-ttu-id="5d186-140">例</span><span class="sxs-lookup"><span data-stu-id="5d186-140">Example</span></span>|<span data-ttu-id="5d186-141">同等の Web フォーム</span><span class="sxs-lookup"><span data-stu-id="5d186-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="5d186-142">コンポーネントにクラスレベルの属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="5d186-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="5d186-143">なし</span><span class="sxs-lookup"><span data-stu-id="5d186-143">None</span></span>|
|`@code`      |<span data-ttu-id="5d186-144">コンポーネントにクラスメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d186-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="5d186-145">指定したインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5d186-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="5d186-146">コードビハインドを使用する</span><span class="sxs-lookup"><span data-stu-id="5d186-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="5d186-147">指定した基底クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="5d186-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="5d186-148">コンポーネントにサービスを挿入します。</span><span class="sxs-lookup"><span data-stu-id="5d186-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="5d186-149">なし</span><span class="sxs-lookup"><span data-stu-id="5d186-149">None</span></span>|
|`@layout`    |<span data-ttu-id="5d186-150">コンポーネントのレイアウトコンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="5d186-151">コンポーネントの名前空間を設定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="5d186-152">なし</span><span class="sxs-lookup"><span data-stu-id="5d186-152">None</span></span>|
|`@page`      |<span data-ttu-id="5d186-153">コンポーネントのルートを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="5d186-154">コンポーネントのジェネリック型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="5d186-155">コードビハインドを使用する</span><span class="sxs-lookup"><span data-stu-id="5d186-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="5d186-156">スコープに取り込む名前空間を指定します</span><span class="sxs-lookup"><span data-stu-id="5d186-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="5d186-157">*web.config* に名前空間を追加する</span><span class="sxs-lookup"><span data-stu-id="5d186-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="5d186-158">また、Razor コンポーネントでは、要素に対して *ディレクティブ属性* を広範に使用して、コンポーネントのコンパイル (イベント処理、データバインディング、コンポーネント & 要素参照など) のさまざまな側面を制御します。</span><span class="sxs-lookup"><span data-stu-id="5d186-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="5d186-159">ディレクティブ属性は、かっこ内の値が省略可能である一般的なジェネリック構文に従います。</span><span class="sxs-lookup"><span data-stu-id="5d186-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="5d186-160">次の表は、で使用される Razor ディレクティブのさまざまな属性をまとめたもの Blazor です。</span><span class="sxs-lookup"><span data-stu-id="5d186-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="5d186-161">属性</span><span class="sxs-lookup"><span data-stu-id="5d186-161">Attribute</span></span>    |<span data-ttu-id="5d186-162">説明</span><span class="sxs-lookup"><span data-stu-id="5d186-162">Description</span></span>|<span data-ttu-id="5d186-163">例</span><span class="sxs-lookup"><span data-stu-id="5d186-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="5d186-164">属性のディクショナリをレンダリングします</span><span class="sxs-lookup"><span data-stu-id="5d186-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="5d186-165">双方向のデータバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d186-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="5d186-166">指定したイベントのイベントハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d186-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="5d186-167">コレクション内の要素を保持するために比較アルゴリズムによって使用されるキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="5d186-168">コンポーネントまたは HTML 要素への参照をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="5d186-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="5d186-169">で使用されるさまざまなディレクティブ属性 Blazor ( `@onclick` 、 `@bind` 、 `@ref` など) については、以降の章で説明します。</span><span class="sxs-lookup"><span data-stu-id="5d186-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="5d186-170">*.Aspx* および *.ascx* ファイルで使用される構文の多くには、Razor の並列構文があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="5d186-171">次に、ASP.NET Web フォームと Razor の構文を簡単に比較します。</span><span class="sxs-lookup"><span data-stu-id="5d186-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="5d186-172">機能</span><span class="sxs-lookup"><span data-stu-id="5d186-172">Feature</span></span>                      |<span data-ttu-id="5d186-173">Web フォーム</span><span class="sxs-lookup"><span data-stu-id="5d186-173">Web Forms</span></span>           |<span data-ttu-id="5d186-174">構文</span><span class="sxs-lookup"><span data-stu-id="5d186-174">Syntax</span></span>               |<span data-ttu-id="5d186-175">Razor</span><span class="sxs-lookup"><span data-stu-id="5d186-175">Razor</span></span>         |<span data-ttu-id="5d186-176">構文</span><span class="sxs-lookup"><span data-stu-id="5d186-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="5d186-177">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="5d186-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="5d186-178">コード ブロック</span><span class="sxs-lookup"><span data-stu-id="5d186-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="5d186-179">式</span><span class="sxs-lookup"><span data-stu-id="5d186-179">Expressions</span></span><br><span data-ttu-id="5d186-180">(HTML エンコード)</span><span class="sxs-lookup"><span data-stu-id="5d186-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="5d186-181">順序 `@`</span><span class="sxs-lookup"><span data-stu-id="5d186-181">Implicit: `@`</span></span><br><span data-ttu-id="5d186-182">順序 `@()`</span><span class="sxs-lookup"><span data-stu-id="5d186-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="5d186-183">コメント</span><span class="sxs-lookup"><span data-stu-id="5d186-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="5d186-184">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="5d186-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="5d186-185">Razor コンポーネントクラスにメンバーを追加するには、ディレクティブを使用し `@code` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="5d186-186">この手法は、 `<script runat="server">...</script>` ASP.NET Web フォームのユーザーコントロールまたはページでブロックを使用するのと似ています。</span><span class="sxs-lookup"><span data-stu-id="5d186-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="5d186-187">Razor は c# に基づいているため、C# プロジェクト (*.csproj*) 内からコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="5d186-188">Visual Basic プロジェクト (*.vbproj*) から *razor* ファイルをコンパイルすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5d186-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="5d186-189">プロジェクトから Visual Basic プロジェクトを参照することもでき Blazor ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="5d186-190">逆も同様です。</span><span class="sxs-lookup"><span data-stu-id="5d186-190">The opposite is true too.</span></span>

<span data-ttu-id="5d186-191">完全 Razor 構文リファレンスについては、「 [ASP.NET Core の Razor 構文リファレンス](/aspnet/core/mvc/views/razor)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d186-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="5d186-192">コンポーネントを使う</span><span class="sxs-lookup"><span data-stu-id="5d186-192">Use components</span></span>

<span data-ttu-id="5d186-193">通常の HTML とは別に、コンポーネントはレンダリングロジックの一部として他のコンポーネントを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="5d186-194">Razor でコンポーネントを使用するための構文は、ASP.NET Web フォームアプリでユーザーコントロールを使用する場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="5d186-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="5d186-195">コンポーネントは、コンポーネントの型名と一致する要素タグを使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="5d186-196">たとえば、次の `Counter` ようなコンポーネントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="5d186-197">ASP.NET Web フォームとは異なり、のコンポーネントは Blazor 次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5d186-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="5d186-198">要素のプレフィックスは使用しないでください (たとえば、 `asp:` )。</span><span class="sxs-lookup"><span data-stu-id="5d186-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="5d186-199">ページまたは *web.config* での登録は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5d186-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="5d186-200">.NET 型のような Razor コンポーネントについて考えてみましょう。これはまさにそのようなものです。</span><span class="sxs-lookup"><span data-stu-id="5d186-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="5d186-201">コンポーネントを含むアセンブリが参照されている場合は、コンポーネントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="5d186-202">コンポーネントの名前空間をスコープに入れるには、ディレクティブを適用し `@using` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="5d186-203">既定のプロジェクトに示されているように Blazor 、ディレクティブを _Imports の razor ファイルに配置するのが一般的です。 `@using` これにより、同じディレクトリおよび子ディレクトリ内のすべての *razor* ファイルにディレクティブがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="5d186-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="5d186-204">コンポーネントの名前空間がスコープ内にない場合は、C# の場合と同様に、完全な型名を使用してコンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="5d186-205">コンポーネントのパラメーター</span><span class="sxs-lookup"><span data-stu-id="5d186-205">Component parameters</span></span>

<span data-ttu-id="5d186-206">ASP.NET Web フォームでは、パブリックプロパティを使用して、パラメーターとデータをコントロールにフローできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="5d186-207">これらのプロパティは、属性を使用してマークアップで設定することも、コードで直接設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="5d186-208">Blazor コンポーネントのプロパティは、コンポーネントのパラメーターと見なされるように属性でマークする必要もありますが、同様の方法で動作し `[Parameter]` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="5d186-209">次のコンポーネントでは、 `Counter` `IncrementAmount` ボタンがクリックされるたびにがインクリメントされる量を指定するために使用できる、というコンポーネントパラメーターを定義して `Counter` います。</span><span class="sxs-lookup"><span data-stu-id="5d186-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="5d186-210">でコンポーネントパラメーターを指定するに Blazor は、ASP.NET Web フォームの場合と同じように属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="5d186-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="5d186-211">イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="5d186-211">Event handlers</span></span>

<span data-ttu-id="5d186-212">ASP.NET Web フォームとはどちらも、 Blazor UI イベントを処理するためのイベントベースのプログラミングモデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d186-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="5d186-213">このようなイベントの例としては、ボタンのクリックやテキスト入力などがあります。</span><span class="sxs-lookup"><span data-stu-id="5d186-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="5d186-214">ASP.NET Web フォームでは、HTML サーバーコントロールを使用して、DOM によって公開される UI イベントを処理したり、web サーバーコントロールによって公開されるイベントを処理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5d186-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="5d186-215">イベントは、ポストバック要求のフォームを使用してサーバー上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="5d186-216">次の Web フォームのボタンをクリックする例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="5d186-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="5d186-217">*カウンタ .ascx*</span><span class="sxs-lookup"><span data-stu-id="5d186-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="5d186-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="5d186-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="5d186-219">では Blazor 、フォームのディレクティブ属性を使用して、DOM UI イベントのハンドラーを直接登録でき `@on{event}` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="5d186-220">プレースホルダーは、 `{event}` イベントの名前を表します。</span><span class="sxs-lookup"><span data-stu-id="5d186-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="5d186-221">たとえば、次のようなボタンのクリックをリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="5d186-222">イベントハンドラーは、イベントに関する詳細情報を提供するために、省略可能なイベント固有の引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5d186-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="5d186-223">たとえば、マウスイベントは引数を受け取ることができますが、必須ではありません `MouseEventArgs` 。</span><span class="sxs-lookup"><span data-stu-id="5d186-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="5d186-224">イベントハンドラーのメソッドグループを参照する代わりに、ラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="5d186-225">ラムダ式を使用すると、他のスコープ内の値を閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="5d186-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="5d186-226">イベントハンドラーは、同期または非同期で実行できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="5d186-227">たとえば、次の `OnClick` イベントハンドラーは非同期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="5d186-228">イベントが処理されると、コンポーネントは、コンポーネントの状態の変更を考慮してレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5d186-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="5d186-229">非同期イベントハンドラーを使用すると、ハンドラーの実行が完了した直後にコンポーネントがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5d186-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="5d186-230">非同期の完了後に、コンポーネントが *再び* 表示され `Task` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="5d186-231">この非同期実行モードでは、非同期の処理中に適切な UI を表示することが `Task` できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="5d186-232">コンポーネントは、型のコンポーネントパラメーターを定義することで、独自のイベントを定義することもでき `EventCallback<TValue>` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="5d186-233">イベントコールバックは、省略可能な引数、同期または非同期、メソッドグループ、ラムダ式など、DOM UI イベントハンドラーのすべてのバリエーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5d186-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="5d186-234">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="5d186-234">Data binding</span></span>

<span data-ttu-id="5d186-235">Blazor UI コンポーネントのデータをコンポーネントの状態にバインドするための単純なメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d186-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="5d186-236">この方法は、データソースから UI コントロールにデータをバインドするための ASP.NET Web フォームの機能とは異なります。</span><span class="sxs-lookup"><span data-stu-id="5d186-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="5d186-237">データの処理に [関する](data.md) セクションでは、さまざまなデータソースからのデータの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d186-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="5d186-238">UI コンポーネントからコンポーネントの状態への双方向のデータバインディングを作成するには、ディレクティブ属性を使用し `@bind` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="5d186-239">次の例では、チェックボックスの値がフィールドにバインドされてい `isChecked` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="5d186-240">コンポーネントがレンダリングされると、チェックボックスの値がフィールドの値に設定され `isChecked` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="5d186-241">ユーザーがチェックボックスをオンにすると、 `onchange` イベントが発生し、 `isChecked` フィールドが新しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="5d186-242">`@bind`この場合の構文は、次のマークアップに相当します。</span><span class="sxs-lookup"><span data-stu-id="5d186-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="5d186-243">バインドに使用するイベントを変更するには、属性を使用し `@bind:event` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="5d186-244">コンポーネントは、パラメーターへのデータバインディングをサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="5d186-245">データバインドには、バインド可能なパラメーターと同じ名前のイベントコールバックパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="5d186-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="5d186-246">"Changed" サフィックスが名前に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="5d186-247">*PasswordBox。 razor*</span><span class="sxs-lookup"><span data-stu-id="5d186-247">*PasswordBox.razor*</span></span>

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="5d186-248">データバインディングを基になる UI 要素に連結するには、属性を使用するのではなく、値を設定し、UI 要素のイベントを直接処理し `@bind` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="5d186-249">コンポーネントパラメーターにバインドするには、属性を使用して、バインド先の `@bind-{Parameter}` パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d186-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="5d186-250">状態変更</span><span class="sxs-lookup"><span data-stu-id="5d186-250">State changes</span></span>

<span data-ttu-id="5d186-251">コンポーネントの状態が通常の UI イベントまたはイベントコールバックの外部で変更された場合、コンポーネントは、再レンダリングが必要であることを手動で通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="5d186-252">コンポーネントの状態が変更されたことを通知するには、 `StateHasChanged` コンポーネントでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d186-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="5d186-253">次の例では、コンポーネントに `AppState` よって、アプリの他の部分で更新可能なサービスからのメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="5d186-254">コンポーネントは、 `StateHasChanged` `AppState.OnChange` メッセージが更新されるたびにコンポーネントがレンダリングされるように、そのメソッドをイベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="5d186-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="5d186-255">コンポーネントのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="5d186-255">Component lifecycle</span></span>

<span data-ttu-id="5d186-256">ASP.NET Web Forms framework には、モジュール、ページ、およびコントロールに対して明確に定義されたライフサイクルメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="5d186-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="5d186-257">たとえば、次のコントロールは `Init` 、、、およびの各 `Load` ライフサイクルイベントのイベントハンドラーを実装し `UnLoad` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="5d186-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="5d186-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="5d186-259">Blazor コンポーネントには、明確に定義されたライフサイクルもあります。</span><span class="sxs-lookup"><span data-stu-id="5d186-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="5d186-260">コンポーネントのライフサイクルは、コンポーネントの状態を初期化し、高度なコンポーネントの動作を実装するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="5d186-261">のすべての Blazor コンポーネントライフサイクルメソッドには、同期バージョンと非同期バージョンの両方があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="5d186-262">コンポーネントのレンダリングは同期です。</span><span class="sxs-lookup"><span data-stu-id="5d186-262">Component rendering is synchronous.</span></span> <span data-ttu-id="5d186-263">コンポーネントレンダリングの一部として非同期ロジックを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="5d186-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="5d186-264">すべての非同期ロジックは、ライフサイクルメソッドの一部として実行する必要があり `async` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="5d186-265">OnInitialized 化</span><span class="sxs-lookup"><span data-stu-id="5d186-265">OnInitialized</span></span>

<span data-ttu-id="5d186-266">`OnInitialized`コンポーネントを `OnInitializedAsync` 初期化するには、メソッドとメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d186-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="5d186-267">コンポーネントは通常、最初のレンダリング後に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="5d186-268">コンポーネントが初期化されると、最終的に破棄される前に複数回レンダリングされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="5d186-269">`OnInitialized`メソッドは、 `Page_Load` ASP.NET Web フォームのページおよびコントロールのイベントに似ています。</span><span class="sxs-lookup"><span data-stu-id="5d186-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="5d186-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="5d186-270">OnParametersSet</span></span>

<span data-ttu-id="5d186-271">`OnParametersSet`コンポーネントが `OnParametersSetAsync` 親からパラメーターを受け取り、値がプロパティに割り当てられるときに、メソッドとメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="5d186-272">これらのメソッドは、コンポーネントの初期化の後、および *コンポーネントがレンダリング* されるたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="5d186-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="5d186-273">OnAfterRender</span></span>

<span data-ttu-id="5d186-274">`OnAfterRender`メソッドと `OnAfterRenderAsync` メソッドは、コンポーネントのレンダリングが完了した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="5d186-275">この時点で、要素参照とコンポーネント参照が設定されます (以下の概念を参照)。</span><span class="sxs-lookup"><span data-stu-id="5d186-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="5d186-276">この時点では、ブラウザーとの対話機能が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5d186-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="5d186-277">DOM および JavaScript の実行とのやり取りは、安全に実行できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="5d186-278">`OnAfterRender``OnAfterRenderAsync`*サーバーでのプリレンダリング時には呼び出されませ* ん。</span><span class="sxs-lookup"><span data-stu-id="5d186-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="5d186-279">`firstRender`パラメーターは、 `true` コンポーネントが初めてレンダリングされるときに指定します。それ以外の場合は、値はに `false` なります。</span><span class="sxs-lookup"><span data-stu-id="5d186-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="5d186-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="5d186-280">IDisposable</span></span>

<span data-ttu-id="5d186-281">Blazor コンポーネント `IDisposable` が UI から削除されると、コンポーネントはを実装してリソースを破棄できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="5d186-282">Razor コンポーネントは、ディレクティブを使用してを実装でき `IDispose` `@implements` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="5d186-283">コンポーネント参照のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="5d186-283">Capture component references</span></span>

<span data-ttu-id="5d186-284">ASP.NET Web フォームでは、ID を参照することによって、コントロールインスタンスをコード内で直接操作するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="5d186-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="5d186-285">では Blazor 、コンポーネントへの参照をキャプチャして操作することもできますが、これはあまり一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="5d186-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="5d186-286">でコンポーネント参照をキャプチャするには Blazor 、 `@ref` ディレクティブ属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="5d186-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="5d186-287">属性の値は、参照されるコンポーネントと同じ型の設定可能フィールドの名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d186-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="5d186-288">親コンポーネントがレンダリングされると、そのフィールドに子コンポーネントインスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="5d186-289">その後、コンポーネントインスタンスのメソッドを呼び出したり、それ以外の操作を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5d186-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="5d186-290">コンポーネント参照を使用してコンポーネントの状態を直接操作することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="5d186-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="5d186-291">これにより、コンポーネントが適切な時刻に自動的にレンダリングされるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="5d186-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="5d186-292">要素参照のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="5d186-292">Capture element references</span></span>

<span data-ttu-id="5d186-293">Blazor コンポーネントは、要素への参照をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="5d186-294">ASP.NET Web フォームの HTML サーバーコントロールとは異なり、の要素参照を使用して DOM を直接操作することはできません Blazor 。</span><span class="sxs-lookup"><span data-stu-id="5d186-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="5d186-295">Blazor dom 比較アルゴリズムを使用して、ほとんどの DOM 対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="5d186-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="5d186-296">でキャプチャされた要素参照 Blazor は不透明です。</span><span class="sxs-lookup"><span data-stu-id="5d186-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="5d186-297">ただし、JavaScript の相互運用呼び出しで特定の要素参照を渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="5d186-298">JavaScript の相互運用機能の詳細については、「 [ASP.NET Core Blazor javascript interop](/aspnet/core/blazor/javascript-interop)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d186-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="5d186-299">テンプレート コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d186-299">Templated components</span></span>

<span data-ttu-id="5d186-300">ASP.NET Web フォームでは、テンプレート化された *コントロール* を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="5d186-301">開発者は、テンプレート化されたコントロールを使用して、コンテナーコントロールの表示に使用する HTML の一部を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="5d186-302">テンプレート化されたサーバーコントロールを構築するメカニズムは複雑ですが、ユーザーがカスタマイズ可能な方法でデータを表示するための強力なシナリオを実現します。</span><span class="sxs-lookup"><span data-stu-id="5d186-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="5d186-303">テンプレート化されたコントロールの例 `Repeater` として、やがあり `DataList` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="5d186-304">Blazor コンポーネントは、型または型のコンポーネントパラメーターを定義することによって、テンプレートを設定することもでき `RenderFragment` `RenderFragment<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="5d186-305">は、 `RenderFragment` コンポーネントによってレンダリングできる Razor マークアップのチャンクを表します。</span><span class="sxs-lookup"><span data-stu-id="5d186-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="5d186-306">は、 `RenderFragment<T>` レンダリングフラグメントのレンダリング時に指定できるパラメーターを受け取る Razor マークアップのチャンクです。</span><span class="sxs-lookup"><span data-stu-id="5d186-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="5d186-307">子コンテンツ</span><span class="sxs-lookup"><span data-stu-id="5d186-307">Child content</span></span>

<span data-ttu-id="5d186-308">Blazor コンポーネントは、子コンテンツをとしてキャプチャ `RenderFragment` し、コンポーネントレンダリングの一部としてそのコンテンツをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="5d186-309">子コンテンツをキャプチャするには、型のコンポーネントパラメーターを定義 `RenderFragment` し、という名前を指定し `ChildContent` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="5d186-310">*ChildContentComponent。 razor*</span><span class="sxs-lookup"><span data-stu-id="5d186-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="5d186-311">親コンポーネントは、通常の Razor 構文を使用して子コンテンツを提供できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="5d186-312">Template parameters</span><span class="sxs-lookup"><span data-stu-id="5d186-312">Template parameters</span></span>

<span data-ttu-id="5d186-313">また、テンプレート Blazor コンポーネントでは、型または型の複数のコンポーネントパラメーターを定義することもでき `RenderFragment` `RenderFragment<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="5d186-314">のパラメーターは、 `RenderFragment<T>` 呼び出されたときに指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="5d186-315">コンポーネントのジェネリック型パラメーターを指定するには、Razor ディレクティブを使用し `@typeparam` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="5d186-316">*SimpleListView。 razor*</span><span class="sxs-lookup"><span data-stu-id="5d186-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="5d186-317">テンプレート化されたコンポーネントを使用する場合、テンプレートパラメーターは、パラメーターの名前と一致する子要素を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="5d186-318">`RenderFragment<T>`要素として渡される型のコンポーネント引数には、という名前の暗黙的なパラメーターがあり `context` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="5d186-319">子要素の属性を使用して、この実装パラメーターの名前を変更でき `Context` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="5d186-320">ジェネリック型パラメーターは、型パラメーターの名前と一致する属性を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d186-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="5d186-321">可能な場合は、型パラメーターが推論されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="5d186-322">このコンポーネントの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5d186-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="5d186-323">分離コード</span><span class="sxs-lookup"><span data-stu-id="5d186-323">Code-behind</span></span>

<span data-ttu-id="5d186-324">Blazorコンポーネントは通常、単一の *razor* ファイルで作成されます。</span><span class="sxs-lookup"><span data-stu-id="5d186-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="5d186-325">ただし、分離コードファイルを使用して、コードとマークアップを分離することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d186-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="5d186-326">コンポーネントファイルを使用するには、コンポーネントファイルのファイル名と一致し、 *.cs* 拡張子を追加した C# ファイルを追加します (*Counter.razor.cs*)。</span><span class="sxs-lookup"><span data-stu-id="5d186-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="5d186-327">コンポーネントの基本クラスを定義するには、C# ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d186-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="5d186-328">基底クラスには任意の名前を指定できますが、クラスにはコンポーネントクラスと同じ名前を付けますが、 `Base` 拡張機能が追加され `CounterBase` ます ()。</span><span class="sxs-lookup"><span data-stu-id="5d186-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="5d186-329">コンポーネントベースのクラスも、から派生する必要があり `ComponentBase` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="5d186-330">次に、Razor コンポーネントファイルで、ディレクティブを追加して、 `@inherits` コンポーネントの基本クラスを指定し `@inherits CounterBase` ます ()。</span><span class="sxs-lookup"><span data-stu-id="5d186-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="5d186-331">*カウンタ。 razor*</span><span class="sxs-lookup"><span data-stu-id="5d186-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="5d186-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="5d186-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="5d186-333">基底クラスのコンポーネントのメンバーの可視性は、 `protected` コンポーネントクラスに表示される必要があり `public` ます。</span><span class="sxs-lookup"><span data-stu-id="5d186-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5d186-334">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="5d186-334">Additional resources</span></span>

<span data-ttu-id="5d186-335">前のは、コンポーネントのすべての側面を網羅するものではありません Blazor 。</span><span class="sxs-lookup"><span data-stu-id="5d186-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="5d186-336">[ASP.NET Core Razor コンポーネントを作成して使用](/aspnet/core/blazor/components)する方法の詳細については、のドキュメントを参照してください Blazor 。</span><span class="sxs-lookup"><span data-stu-id="5d186-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d186-337">[前へ](app-startup.md)
>[次へ](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="5d186-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
