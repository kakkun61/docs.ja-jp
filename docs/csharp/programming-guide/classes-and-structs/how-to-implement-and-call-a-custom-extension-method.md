---
title: カスタム拡張メソッドを実装して呼び出す方法 - C# プログラミング ガイド
description: あらゆる .NET 型を対象に拡張メソッドを実装する方法について説明します。 クライアント コードでは、DLL に参照を追加し、ディレクティブの使用を追加することで、自分のメソッドを使用することができます。
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 4ae48a05d451a3276b3a0f2ee4d6c633ce7db306
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513012"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="0d7b1-104">カスタム拡張メソッドを実装して呼び出す方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0d7b1-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="0d7b1-105">このトピックでは、あらゆる .NET 型を対象に独自の拡張メソッドを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="0d7b1-106">クライアント コードで拡張メソッドを使用するには、拡張メソッドが格納されている DLL への参照を追加し、拡張メソッドが定義されている名前空間を指定する [using](../../language-reference/keywords/using-directive.md) ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="0d7b1-107">拡張メソッドを定義して呼び出すには</span><span class="sxs-lookup"><span data-stu-id="0d7b1-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="0d7b1-108">拡張メソッドを格納するための静的[クラス](./static-classes-and-static-class-members.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="0d7b1-109">このクラスは、クライアント コードから参照できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-109">The class must be visible to client code.</span></span> <span data-ttu-id="0d7b1-110">アクセシビリティの規則の詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="0d7b1-111">拡張メソッドを静的メソッドとして実装します。メソッドの可視性は、包含クラスと同レベル以上を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="0d7b1-112">メソッドの最初のパラメーターでは、メソッドが操作する型を指定します。型名の前には [this](../../language-reference/keywords/this.md) 修飾子を付加します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="0d7b1-113">呼び出し元のコードで、`using` ディレクティブを追加して、拡張メソッドのクラスを含む[名前空間](../../language-reference/keywords/namespace.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="0d7b1-114">型のインスタンス メソッドと同じようにメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="0d7b1-115">呼び出し元のコードでは最初のパラメーターを指定しません。これは演算子を適用する型を表すものであり、コンパイラはオブジェクトの型を既に認識しているためです。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="0d7b1-116">指定する必要があるのは、2 番目から `n` 番目のパラメーターの引数だけです。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d7b1-117">例</span><span class="sxs-lookup"><span data-stu-id="0d7b1-117">Example</span></span>  

 <span data-ttu-id="0d7b1-118">次の例では、`CustomExtensions.StringExtension` クラスの `WordCount` という名前の拡張メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="0d7b1-119">このメソッドは、最初のメソッド パラメーターとして指定された <xref:System.String> クラスを操作します。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="0d7b1-120">`CustomExtensions` 名前空間は、アプリケーション名前空間にインポートされ、メソッドは `Main` メソッド内で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="0d7b1-121">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d7b1-121">.NET Security</span></span>  

 <span data-ttu-id="0d7b1-122">拡張メソッドには、固有のセキュリティ上の脆弱性はありません。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="0d7b1-123">名前の衝突の解決では、型自体で定義されているインスタンス メソッドまたは静的メソッドが常に優先されるため、型の既存のメソッドを偽装するために拡張メソッドが使用されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="0d7b1-124">拡張メソッドは、拡張されたクラスのプライベート データにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="0d7b1-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7b1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d7b1-125">See also</span></span>

- [<span data-ttu-id="0d7b1-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0d7b1-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0d7b1-127">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="0d7b1-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="0d7b1-128">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0d7b1-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="0d7b1-129">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="0d7b1-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="0d7b1-130">protected</span><span class="sxs-lookup"><span data-stu-id="0d7b1-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="0d7b1-131">internal</span><span class="sxs-lookup"><span data-stu-id="0d7b1-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="0d7b1-132">public</span><span class="sxs-lookup"><span data-stu-id="0d7b1-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="0d7b1-133">this</span><span class="sxs-lookup"><span data-stu-id="0d7b1-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="0d7b1-134">namespace</span><span class="sxs-lookup"><span data-stu-id="0d7b1-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
