---
title: '方法: CodeDOM を使用してクラスを作成する'
description: Code Document Object Model (CodeDOM) を使用してクラスを作成する方法を説明した詳細な例について確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: 7c2cda2bb7cbdb93c27aef91c08f7c7227da7eed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235702"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="0e68f-103">方法: CodeDOM を使用してクラスを作成する</span><span class="sxs-lookup"><span data-stu-id="0e68f-103">How to: Create a Class Using CodeDOM</span></span>

<span data-ttu-id="0e68f-104">2 つのフィールド、3 つのプロパティ、1 つのメソッド、1 つのコンストラクター、1 つのエントリ ポイントを含むクラスを生成する CodeDOM グラフを作成し、コンパイルする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-104">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="0e68f-105">CodeDOM コードを使用するコンソール アプリケーションを作成し、クラスのソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-105">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="0e68f-106">この例では、生成元のクラスの名前が `Sample` で、生成されるコードが SampleCode という名前のファイルの `CodeDOMCreatedClass` という名前のクラスになります。</span><span class="sxs-lookup"><span data-stu-id="0e68f-106">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="0e68f-107">生成元のクラスでは、CodeDOM グラフを初期化し、CodeDOM メソッドを利用して生成されるクラスのメンバー、コンストラクター、エントリ ポイント (`Main` メソッド) を定義します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-107">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="0e68f-108">この例では、生成されるクラスに 2 つのフィールド、3 つのプロパティ、1 つのコンストラクター、1 つのメソッド、1 つの `Main` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="0e68f-108">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="0e68f-109">生成元のクラスで、言語固有のコード プロバイダーを作成し、その <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出してグラフからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-109">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="0e68f-110">アプリケーションをコンパイルして実行し、コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-110">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="0e68f-111">この例では、生成されたコードが SampleCode という名前のファイルに入っています。</span><span class="sxs-lookup"><span data-stu-id="0e68f-111">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="0e68f-112">そのコードをコンパイルして実行し、サンプル出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-112">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="0e68f-113">CodeDOM コードを実行するアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="0e68f-113">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="0e68f-114">CodeDOM コードを含むコンソール アプリケーション クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-114">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="0e68f-115">このクラスでアセンブリ (<xref:System.CodeDom.CodeCompileUnit>) とクラス (<xref:System.CodeDom.CodeTypeDeclaration>) を参照するためのグローバル フィールドを定義し、生成されるソース ファイルの名前を指定し、`Main` メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-115">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="0e68f-116">CodeDOM グラフを初期化するには</span><span class="sxs-lookup"><span data-stu-id="0e68f-116">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="0e68f-117">コンソール アプリケーション クラスのコンストラクターで、アセンブリとクラスを初期化し、適切な宣言を CodeDOM グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="0e68f-118">CodeDOM グラフにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="0e68f-118">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="0e68f-119">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberField> オブジェクトを追加することで CodeDOM グラフにフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-119">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="0e68f-120">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberProperty> オブジェクトを追加することで CodeDOM グラフにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-120">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="0e68f-121">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberMethod> オブジェクトを追加することで CodeDOM グラフにメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-121">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="0e68f-122">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeConstructor> オブジェクトを追加することで CodeDOM グラフにコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-122">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="0e68f-123">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeEntryPointMethod> オブジェクトを追加することで CodeDOM グラフにエントリ ポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-123">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="0e68f-124">CodeDOM グラフからコードを生成するには</span><span class="sxs-lookup"><span data-stu-id="0e68f-124">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="0e68f-125"><xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出すことで CodeDOM グラフからソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-125">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="0e68f-126">グラフを作成し、コードを生成するには</span><span class="sxs-lookup"><span data-stu-id="0e68f-126">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="0e68f-127">前の手順で作成したメソッドを最初の手順で定義した `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-127">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="0e68f-128">生成元のクラスをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-128">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e68f-129">例</span><span class="sxs-lookup"><span data-stu-id="0e68f-129">Example</span></span>  

 <span data-ttu-id="0e68f-130">次のコード サンプルは、前の手順のコードです。</span><span class="sxs-lookup"><span data-stu-id="0e68f-130">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="0e68f-131">前のサンプルをコンパイルし、実行すると、次のソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0e68f-131">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="0e68f-132">生成されたソース コードは、コンパイルされ、実行されると、次の内容を出力します。</span><span class="sxs-lookup"><span data-stu-id="0e68f-132">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e68f-133">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0e68f-133">Compiling the Code</span></span>  
  
- <span data-ttu-id="0e68f-134">このコード サンプルを正しく実行するには、`FullTrust` アクセス許可を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e68f-134">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e68f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e68f-135">See also</span></span>

- [<span data-ttu-id="0e68f-136">CodeDOM の使用方法</span><span class="sxs-lookup"><span data-stu-id="0e68f-136">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="0e68f-137">CodeDOM グラフからのソース コードの生成およびコンパイル</span><span class="sxs-lookup"><span data-stu-id="0e68f-137">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
