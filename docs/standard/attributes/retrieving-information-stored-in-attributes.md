---
title: 属性に格納されている情報の取得
description: 属性インスタンスの場合など、属性に格納されている情報を取得する方法について説明します。属性には、同じスコープのものや、異なるスコープのものが多数あります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
ms.openlocfilehash: 6ba01fcd23e626354e5f9a2baa914815b61c8332
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701563"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="cb2c9-103">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="cb2c9-103">Retrieving Information Stored in Attributes</span></span>

<span data-ttu-id="cb2c9-104">カスタム属性の取得は簡単なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-104">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="cb2c9-105">まず、取得する属性のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-105">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="cb2c9-106">次に、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> メソッドを使用して、取得する属性の値に新しい属性を初期化します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-106">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="cb2c9-107">新しい属性が初期化されたら、そのプロパティを使用して値を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-107">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb2c9-108">このトピックでは、実行コンテキストに読み込まれるコードのカスタム属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-108">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="cb2c9-109">リフレクションのみのコンテキスト<xref:System.Reflection.CustomAttributeData> に読み込まれたコードの属性を取得するには、「[方法:リフレクションのみのコンテキストにアセンブリを読み込む](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-109">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="cb2c9-110">このセクションでは、以下の属性の取得方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-110">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="cb2c9-111">属性の単一のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-111">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="cb2c9-112">同じスコープに適用された属性の複数のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-112">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="cb2c9-113">異なるスコープに適用された属性の複数のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-113">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>

## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="cb2c9-114">属性の単一のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-114">Retrieving a Single Instance of an Attribute</span></span>  

 <span data-ttu-id="cb2c9-115">次の例では、(前のセクションで説明した) `DeveloperAttribute` がクラス レベルで `MainApp` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-115">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="cb2c9-116">`GetAttribute` メソッドは **GetCustomAttribute** を使用して、クラス レベルで `DeveloperAttribute` に格納されている値を取得してからコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-116">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="cb2c9-117">このプログラムを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-117">This program displays the following text when executed.</span></span>  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="cb2c9-118">属性が見つからない場合、**GetCustomAttribute** メソッドは `MyAttribute` を null 値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-118">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="cb2c9-119">この例では、そのようなインスタンスの `MyAttribute` を確認し、属性が見つからない場合はユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-119">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="cb2c9-120">クラス スコープ内に `DeveloperAttribute` 見つからない場合は、次のメッセージがコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-120">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```console  
The attribute was not found.
```  
  
 <span data-ttu-id="cb2c9-121">この例では、属性の定義が現在の名前空間にあると仮定しています。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-121">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="cb2c9-122">属性の定義が現在の名前空間にない場合は、その定義が存在する名前空間を忘れずにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-122">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="cb2c9-123">同じスコープに適用された属性の複数のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-123">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  

 <span data-ttu-id="cb2c9-124">前の例では、検査するクラスと検索する特定の属性が <xref:System.Attribute.GetCustomAttribute%2A> に渡されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-124">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="cb2c9-125">このコードは、クラス レベルで属性のインスタンスが 1 つのみ適用される場合に動作します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-125">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="cb2c9-126">ただし、属性のインスタンスが同じクラス レベルに複数適用されている場合、**GetCustomAttribute** メソッドはすべての情報を取得しません。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-126">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="cb2c9-127">同じ属性のインスタンスが同じスコープに複数適用されている場合、<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> を使用して、属性のすべてのインスタンスを配列に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-127">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="cb2c9-128">たとえば、同じクラスのクラス レベルで 2 インスタンスの `DeveloperAttribute` が適用された場合、両方の属性にある情報を表示するように `GetAttribute` メソッドを変更できます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-128">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="cb2c9-129">ただし、同じレベルで複数の属性を適用するには、<xref:System.AttributeUsageAttribute> で **AllowMultiple** プロパティを **true** に設定して属性を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-129">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="cb2c9-130">次のコード例は、**GetCustomAttributes** メソッドを使用して、指定されたクラスで `DeveloperAttribute` のすべてのインスタンスを参照する配列を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-130">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="cb2c9-131">すべての属性の値がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-131">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="cb2c9-132">このコードでは、属性が見つからない場合、ユーザーに警告されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-132">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="cb2c9-133">それ以外の場合は、`DeveloperAttribute` の両方のインスタンスに含まれる情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-133">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="cb2c9-134">異なるスコープに適用された属性の複数のインスタンスを取得する</span><span class="sxs-lookup"><span data-stu-id="cb2c9-134">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  

 <span data-ttu-id="cb2c9-135"><xref:System.Attribute.GetCustomAttributes%2A> メソッドと <xref:System.Attribute.GetCustomAttribute%2A> メソッドは、クラス全体を検索し、そのクラスに含まれる属性のすべてのインスタンスを返す処理を行いません。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-135">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="cb2c9-136">代わりに、指定されたメソッドまたはメンバーを一度に 1 つのみ検索します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-136">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="cb2c9-137">各メンバーに同じ属性が適用されているクラスがあり、それらのメンバーに適用されているすべての属性の値を取得する場合は、すべてのメソッドまたはメンバーを個別に **GetCustomAttributes** および **GetCustomAttribute** に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-137">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="cb2c9-138">次のコード例では、クラスをパラメーターとして受け取り、クラス レベルとそのクラスの個々のメソッドごとに `DeveloperAttribute` (以前に定義) を検索します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-138">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="cb2c9-139">メソッド レベルまたはクラス レベルで `DeveloperAttribute` のインスタンスが見つからない場合、`GetAttribute` メソッドは属性が見つからなかったことをユーザーに通知し、その属性を含まないメソッドまたはクラスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-139">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="cb2c9-140">属性が見つかると、`Name`、`Level`、および `Reviewed` フィールドがコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-140">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="cb2c9-141"><xref:System.Type> クラスのメンバーを使用して、渡されたクラスの個々のメソッドとメンバーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-141">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="cb2c9-142">この例では、まず **Type** オブジェクトに対してクエリを実行して、クラス レベルの属性情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-142">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="cb2c9-143">次に、<xref:System.Type.GetMethods%2A?displayProperty=nameWithType> を使用してすべてのメソッドのインスタンスを <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> オブジェクトの配列に配置し、メソッド レベルの属性情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-143">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="cb2c9-144"><xref:System.Type.GetProperties%2A?displayProperty=nameWithType> メソッドを使用して、プロパティ レベルまたは <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> で属性を確認したり、コンストラクター レベルで属性を確認したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cb2c9-144">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb2c9-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb2c9-145">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cb2c9-146">属性</span><span class="sxs-lookup"><span data-stu-id="cb2c9-146">Attributes</span></span>](index.md)
