---
title: カスタム属性へのアクセス
description: .NET のカスタム属性にアクセスします。 属性がプログラム要素に関連付けられると、リフレクションを使用して、その存在と値をクエリすることができます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: d441bad7d4af3a88c4ede507d1bce7bdd1ab3215
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266819"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="6c570-104">カスタム属性へのアクセス</span><span class="sxs-lookup"><span data-stu-id="6c570-104">Accessing Custom Attributes</span></span>

<span data-ttu-id="6c570-105">属性がプログラム要素に関連付けられると、リフレクションを使用して、その存在と値をクエリすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c570-105">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="6c570-106">.NET Framework バージョン 1.0 および 1.1 では、カスタム属性は実行コンテキストで検証されます。</span><span class="sxs-lookup"><span data-stu-id="6c570-106">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="6c570-107">.NET Framework バージョン 2.0 では、新しい読み込みコンテキスト (リフレクションのみのコンテキスト) が提供されます。これを使用して、実行のために読み込むことができないコードを検証できます。</span><span class="sxs-lookup"><span data-stu-id="6c570-107">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="6c570-108">リフレクションのみのコンテキスト</span><span class="sxs-lookup"><span data-stu-id="6c570-108">The Reflection-Only Context</span></span>  

 <span data-ttu-id="6c570-109">リフレクションのみのコンテキストに読み込まれたコードは、実行することができません。</span><span class="sxs-lookup"><span data-stu-id="6c570-109">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="6c570-110">つまり、コンストラクターを実行する必要があるため、カスタム属性のインスタンスは作成できないということです。</span><span class="sxs-lookup"><span data-stu-id="6c570-110">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="6c570-111">リフレクションのみのコンテキストにカスタム属性を読み込み、検証するには、<xref:System.Reflection.CustomAttributeData> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6c570-111">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="6c570-112">静的な <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> メソッドの適切なオーバーロードを使用して、このクラスのインスタンスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="6c570-112">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6c570-113">「[方法:リフレクションのみのコンテキストにアセンブリを読み込む](how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c570-113">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="6c570-114">実行コンテキスト</span><span class="sxs-lookup"><span data-stu-id="6c570-114">The Execution Context</span></span>  

 <span data-ttu-id="6c570-115">実行コンテキストの属性をクエリする主なリフレクション メソッドは、<xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> と <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="6c570-115">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6c570-116">カスタム属性のアクセシビリティは、添付されているアセンブリに関してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="6c570-116">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="6c570-117">これは、カスタム属性が添付されているアセンブリの型のメソッドが、カスタム属性のコンストラクターを呼び出すことができるかどうかをチェックするのと同じです。</span><span class="sxs-lookup"><span data-stu-id="6c570-117">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="6c570-118"><xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> などのメソッドは、型引数の可視性とアクセシビリティをチェックします。</span><span class="sxs-lookup"><span data-stu-id="6c570-118">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="6c570-119">ユーザー定義型を含むアセンブリのコードのみが、**GetCustomAttributes** を使用する型のカスタム属性を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="6c570-119">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="6c570-120">次の C# の例は、一般的なカスタム属性の設計パターンです。</span><span class="sxs-lookup"><span data-stu-id="6c570-120">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="6c570-121">これは、ランタイムのカスタム属性のリフレクション モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="6c570-121">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="6c570-122">このランタイムで **GetLanguage** メソッドに添付されている公開のカスタム属性の型 <xref:System.ComponentModel.DescriptionAttribute> のカスタム属性を取得しようとしている場合、次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c570-122">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="6c570-123">ランタイムは、**Type.GetCustomAttributes**(Type *type*) の型引数 **DescriptionAttribute** が公開であることをチェックするため、表示およびアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c570-123">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="6c570-124">ランタイムは、**DescriptionAttribute** から派生するユーザー定義型 **MyDescriptionAttribute** が **System.Web.DLL** アセンブリ内で表示およびアクセスできることをチェックします。これは、メソッド **GetLanguage**() に添付されている場所です。</span><span class="sxs-lookup"><span data-stu-id="6c570-124">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="6c570-125">ランタイムは、**MyDescriptionAttribute** のコンストラクターが、**System.Web.DLL** アセンブリ内で表示およびアクセスできることをチェックします。</span><span class="sxs-lookup"><span data-stu-id="6c570-125">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="6c570-126">ランタイムは、カスタム属性のパラメーターを使って **MyDescriptionAttribute** のコンストラクターを呼び出し、呼び出し元に新しいオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6c570-126">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="6c570-127">カスタム属性のリフレクション モデルは、型が定義されているアセンブリの外にあるユーザー定義型のインスタンスをリークする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6c570-127">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="6c570-128">これは、**RuntimeMethodInfo** オブジェクトの配列を返す <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> など、ユーザー定義型のインスタンスを返すランタイム システム ライブラリのメンバーと同様です。</span><span class="sxs-lookup"><span data-stu-id="6c570-128">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="6c570-129">クライアントがユーザー定義のカスタム属性の型に関する情報を検出できないようにするには、型のメンバーを非公開に定義します。</span><span class="sxs-lookup"><span data-stu-id="6c570-129">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="6c570-130">次の例では、カスタム属性にアクセスできるリフレクションを使用する基本的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6c570-130">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6c570-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c570-131">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6c570-132">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="6c570-132">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="6c570-133">リフレクションに関するセキュリティ上の考慮事項</span><span class="sxs-lookup"><span data-stu-id="6c570-133">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
