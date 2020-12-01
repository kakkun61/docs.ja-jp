---
title: 型情報の表示
description: .NET でリフレクションの中心となる System.Type を使用した型情報について確認します。 ConstructorInfo、MemberInfo、MethodInfo、FieldInfo、PropertyInfo について確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
ms.openlocfilehash: 3baacbeca7f5cc50fbb720849aec273f996f86e7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259142"
---
# <a name="viewing-type-information"></a><span data-ttu-id="a3d56-104">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="a3d56-104">Viewing Type Information</span></span>

<span data-ttu-id="a3d56-105"><xref:System.Type?displayProperty=nameWithType> クラスは、リフレクションの中心です。</span><span class="sxs-lookup"><span data-stu-id="a3d56-105">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="a3d56-106">共通言語ランタイムは、リフレクションの要求時に読み込まれる型の **型** を作成します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-106">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="a3d56-107">**型** オブジェクトのメソッド、フィールド、プロパティ、および入れ子になったクラスから、その型に関することがすべてわかります。</span><span class="sxs-lookup"><span data-stu-id="a3d56-107">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="a3d56-108"><xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> または <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> を使用して、読み込まれていないアセンブリから **型** オブジェクトを取得します。これは、目的の型の名前で渡されます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-108">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="a3d56-109">既に読み込まれているアセンブリから **型** オブジェクトを取得するには、<xref:System.Type.GetType%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-109">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="a3d56-110"><xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> および <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> は、モジュール **型** オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-110">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3d56-111">ジェネリック型およびメソッドをチェックして操作したい場合は、「[リフレクションとジェネリック型](reflection-and-generic-types.md)」および「[方法:リフレクションを使用してジェネリック型をチェックおよびインスタンス化する](how-to-examine-and-instantiate-generic-types-with-reflection.md)」に記載された追加情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3d56-111">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="a3d56-112">次の例は、アセンブリの <xref:System.Reflection.Assembly> オブジェクトおよびモジュールの取得に必要な構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-112">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="a3d56-113">次の例は、読み込まれたアセンブリからの **型** オブジェクトの取得を示しています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-113">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="a3d56-114">**型** を取得すると、その型のメンバーに関する情報をさまざまな方法で確認できます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-114">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="a3d56-115">たとえば、その型の各メンバーについて説明した <xref:System.Reflection.MemberInfo> オブジェクトの配列を取得する <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> メソッドを呼び出すことで、すべての型のメンバーについて確認できます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-115">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="a3d56-116">**Type** クラスのメソッドを使用して、名前で指定した 1 つまたは複数のコンストラクター、メソッド、イベント、フィールド、プロパティに関する情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-116">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="a3d56-117">たとえば、<xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> は現在のクラスの特定のコンストラクターをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-117">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="a3d56-118">**型** がある場合、<xref:System.Type.Module%2A?displayProperty=nameWithType> プロパティを使用して、その型が含まれるモジュールをカプセル化するオブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-118">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="a3d56-119">モジュールが含まれるアセンブリをカプセル化するオブジェクトを見つけるには、<xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-119">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="a3d56-120"><xref:System.Type.Assembly%2A?displayProperty=nameWithType> プロパティを使用することで、型を直接カプセル化するアセンブリを取得できます。</span><span class="sxs-lookup"><span data-stu-id="a3d56-120">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="a3d56-121">System.Type および ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="a3d56-121">System.Type and ConstructorInfo</span></span>  

 <span data-ttu-id="a3d56-122">次の例は、クラス (この場合は <xref:System.String> クラス) のコンストラクターを一覧表示する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-122">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="a3d56-123">MemberInfo、MethodInfo、FieldInfo、および PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="a3d56-123">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  

 <span data-ttu-id="a3d56-124"><xref:System.Reflection.MemberInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.FieldInfo>、または <xref:System.Reflection.PropertyInfo> オブジェクトを使用して型のメソッド、プロパティ、イベント、およびフィールドに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3d56-124">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="a3d56-125">次の例では、**MemberInfo** を使用して **System.IO.File** クラスのメンバー数を一覧表示し、<xref:System.Type.IsPublic%2A> プロパティを使用してクラスの可視性を決定しています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-125">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="a3d56-126">次の例では、指定されたメンバーの型を調べています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-126">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="a3d56-127">**MemberInfo** クラスのメンバーにリフレクションを実行し、その型を一覧表示しています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-127">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="a3d56-128">次の例では、すべてのリフレクション **\*Info** クラスに <xref:System.Reflection.BindingFlags> を使用して、指定したクラスのすべてのメンバー (コンストラクター、フィールド、プロパティ、イベント、およびメソッド) を一覧表示しています。メンバーは静的およびインスタンスのカテゴリに分割されています。</span><span class="sxs-lookup"><span data-stu-id="a3d56-128">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a3d56-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3d56-129">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="a3d56-130">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="a3d56-130">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
