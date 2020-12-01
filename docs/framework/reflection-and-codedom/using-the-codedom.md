---
title: CodeDOM の使用方法
description: オブジェクト グラフをアセンブルするために多くの一般的な種類のソース コード要素を表す型を提供する Code Document Object Model (CodeDOM) を使用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
ms.openlocfilehash: f2481aa0423615f5f5925bde7cae3ad170ca8533
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259181"
---
# <a name="using-the-codedom"></a><span data-ttu-id="a067c-103">CodeDOM の使用方法</span><span class="sxs-lookup"><span data-stu-id="a067c-103">Using the CodeDOM</span></span>

<span data-ttu-id="a067c-104">CodeDOM には一般的なさまざま種類のソース コード要素を表す型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a067c-104">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="a067c-105">オブジェクト グラフをアセンブルする CodeDOM 要素を使用すると、ソース コード モデルを構築するプログラムをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="a067c-105">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="a067c-106">このオブジェクト グラフは、サポートされているプログラミング言語用の CodeDOM コード ジェネレーターを使用して、ソース コードとしてレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="a067c-106">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="a067c-107">また、CodeDOM を使用して、ソース コードをバイナリ アセンブリにコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a067c-107">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="a067c-108">CodeDOM の一般的な使用方法の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a067c-108">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="a067c-109">テンプレートを使ったコード生成。ASP.NET、XML Web サービス クライアント プロキシ、コード ウィザード、デザイナー、またはその他のコード出力機構のためのコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="a067c-109">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="a067c-110">動的コンパイル。1 つ以上の言語でのコードのコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a067c-110">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="a067c-111">CodeDOM グラフの構築</span><span class="sxs-lookup"><span data-stu-id="a067c-111">Building a CodeDOM Graph</span></span>  

 <span data-ttu-id="a067c-112"><xref:System.CodeDom> 名前空間には、言語の構文に依存しない、ソース コードの論理構造を表すクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a067c-112">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="a067c-113">CodeDOM グラフの構造</span><span class="sxs-lookup"><span data-stu-id="a067c-113">The Structure of a CodeDOM Graph</span></span>  

 <span data-ttu-id="a067c-114">CodeDOM グラフの構造はコンテナーのツリーに似ています。</span><span class="sxs-lookup"><span data-stu-id="a067c-114">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="a067c-115">コンパイル可能な CodeDOM グラフの最上位のコンテナー、つまりルートのコンテナーは <xref:System.CodeDom.CodeCompileUnit> です。</span><span class="sxs-lookup"><span data-stu-id="a067c-115">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="a067c-116">ソース コード モデルの各要素は、CodeDOM グラフ内の <xref:System.CodeDom.CodeObject> のプロパティを通じて CodeDOM グラフにリンクされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a067c-116">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="a067c-117">サンプルの Hello World プログラム用ソース コード モデルの構築</span><span class="sxs-lookup"><span data-stu-id="a067c-117">Building a Source Code Model for a Sample Hello World Program</span></span>  

 <span data-ttu-id="a067c-118">単純な Hello World アプリケーションのコードを表す CodeDOM オブジェクト グラフを構築する手順の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-118">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="a067c-119">このコード サンプルのソース コード例全体については、「<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a067c-119">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="a067c-120">コンパイル単位の作成</span><span class="sxs-lookup"><span data-stu-id="a067c-120">Creating a compile unit</span></span>  

 <span data-ttu-id="a067c-121">CodeDOM は、<xref:System.CodeDom.CodeCompileUnit> と呼ばれるオブジェクトを定義します。このオブジェクトでは、コンパイルするソース コードをモデル化した CodeDOM オブジェクト グラフを参照できます。</span><span class="sxs-lookup"><span data-stu-id="a067c-121">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="a067c-122">**CodeCompileUnit** には、属性、名前空間、およびアセンブリへの参照を格納するためのプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a067c-122">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="a067c-123"><xref:System.CodeDom.Compiler.CodeDomProvider> クラスから派生する CodeDom プロバイダーには、**CodeCompileUnit** が参照するオブジェクト グラフを処理するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a067c-123">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="a067c-124">簡単なアプリケーション用のオブジェクト グラフを作成するには、ソース コード モデルをアセンブルし、生成されたオブジェクト グラフを **CodeCompileUnit** から参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a067c-124">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="a067c-125">新しいコンパイル単位を作成するには、次の例に示す構文を使います。</span><span class="sxs-lookup"><span data-stu-id="a067c-125">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="a067c-126"><xref:System.CodeDom.CodeSnippetCompileUnit> には、既に対象言語で記述されているソース コードのセクションを格納できますが、この単位は別の言語にはレンダリングできません。</span><span class="sxs-lookup"><span data-stu-id="a067c-126">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="a067c-127">名前空間の定義</span><span class="sxs-lookup"><span data-stu-id="a067c-127">Defining a namespace</span></span>  

 <span data-ttu-id="a067c-128">名前空間を定義するには、<xref:System.CodeDom.CodeNamespace> を作成してから、適切なコンストラクターを使用するか **Name** プロパティを設定することにより、定義する名前空間の名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a067c-128">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="a067c-129">名前空間のインポート</span><span class="sxs-lookup"><span data-stu-id="a067c-129">Importing a namespace</span></span>  

 <span data-ttu-id="a067c-130">名前空間のインポート ディレクティブを名前空間に追加するには、インポートする名前空間を示す <xref:System.CodeDom.CodeNamespaceImport> を **CodeNamespace.Imports** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a067c-130">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="a067c-131">**System** 名前空間のインポートを、`samples` という名前の **CodeNamespace** の **Imports** コレクションに追加するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-131">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="a067c-132">コード要素のオブジェクト グラフへのリンク</span><span class="sxs-lookup"><span data-stu-id="a067c-132">Linking code elements into the object graph</span></span>  

 <span data-ttu-id="a067c-133">CodeDOM グラフを形成するすべてのコード要素は、CodeDOM グラフのルート オブジェクトのプロパティから直接参照される要素間の一連の参照によって、ツリーのルート要素である <xref:System.CodeDom.CodeCompileUnit> にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a067c-133">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="a067c-134">オブジェクトをコンテナー オブジェクトのプロパティに設定し、コンテナー オブジェクトからの参照を確立します。</span><span class="sxs-lookup"><span data-stu-id="a067c-134">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="a067c-135">`samples` **CodeNamespace** をルートの **CodeCompileUnit** の **Namespaces** コレクション プロパティに追加するステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-135">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="a067c-136">型の定義</span><span class="sxs-lookup"><span data-stu-id="a067c-136">Defining a type</span></span>  

 <span data-ttu-id="a067c-137">CodeDOM を使ってクラス、構造体、インターフェイス、または列挙体を宣言するには、新しい <xref:System.CodeDom.CodeTypeDeclaration> を作成し、名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a067c-137">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="a067c-138">このために、**Name** プロパティを設定するコンストラクターのオーバーロードを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-138">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="a067c-139">名前空間に型を追加するには、名前空間に追加する型を表す <xref:System.CodeDom.CodeTypeDeclaration> を、**CodeNamespace** の **Types** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a067c-139">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="a067c-140">`class1` という名前のクラスを `samples` という名前の **CodeNamespace** に追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-140">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="a067c-141">クラスへのクラス メンバーの追加</span><span class="sxs-lookup"><span data-stu-id="a067c-141">Adding class members to a class</span></span>  

 <span data-ttu-id="a067c-142"><xref:System.CodeDom> 名前空間には、クラス メンバーを表すために使用できるさまざまな要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a067c-142">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="a067c-143">各クラス メンバーは、<xref:System.CodeDom.CodeTypeDeclaration> の **Members** コレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a067c-143">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="a067c-144">実行可能プログラムのコード エントリ ポイント メソッドの定義</span><span class="sxs-lookup"><span data-stu-id="a067c-144">Defining a code entry point method for an executable</span></span>  

 <span data-ttu-id="a067c-145">実行可能プログラムのコードを記述する場合は、プログラムの実行を開始するメソッドを表す <xref:System.CodeDom.CodeEntryPointMethod> を作成して、プログラムのエントリ ポイントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a067c-145">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="a067c-146">"Hello World!" と出力するための **System.Console.WriteLine** を呼び出す <xref:System.CodeDom.CodeMethodInvokeExpression> を格納しているエントリ ポイント メソッドを定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-146">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="a067c-147">`Start` という名前のエントリ ポイント メソッドを `class1` の **Members** コレクションに追加するステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a067c-147">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="a067c-148">これで、<xref:System.CodeDom.CodeCompileUnit> という名前の `compileUnit` に、簡単な Hello World プログラムの CodeDOM グラフが追加されました。</span><span class="sxs-lookup"><span data-stu-id="a067c-148">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="a067c-149">CodeDOM グラフからのコードの生成およびコンパイルについては、「[CodeDOM グラフからのソース コードの生成およびプログラムのコンパイル](generating-and-compiling-source-code-from-a-codedom-graph.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a067c-149">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="a067c-150">CodeDOM グラフの構築に関する詳細</span><span class="sxs-lookup"><span data-stu-id="a067c-150">More information on building a CodeDOM graph</span></span>  

 <span data-ttu-id="a067c-151">CodeDOM では、共通言語ランタイムをサポートするプログラミング言語の一般的なさまざまな種類のコード要素をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a067c-151">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="a067c-152">CodeDOM は、プログラミング言語のすべての機能を表す要素を提供するようにはデザインされていません。</span><span class="sxs-lookup"><span data-stu-id="a067c-152">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="a067c-153">CodeDOM 要素で簡単に表すことができないコードは、<xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember>、または <xref:System.CodeDom.CodeSnippetCompileUnit> にカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="a067c-153">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="a067c-154">ただし、CodeDOM ではコードを自動的に他の言語に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="a067c-154">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="a067c-155">CodeDOM のそれぞれの型については、<xref:System.CodeDom> 名前空間の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a067c-155">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="a067c-156">特定の種類のコード要素を表す CodeDOM 要素を探すための一覧については、「[CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))」(CodeDOM クイック リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a067c-156">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
