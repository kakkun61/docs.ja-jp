---
title: リフレクションに依存する API
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 2c361962f4570200d63037a68ef39b0c982bd5f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251140"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="e417a-102">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="e417a-102">APIs That Rely on Reflection</span></span>

<span data-ttu-id="e417a-103">場合によっては、コードでのリフレクションの使用は明確ではないため、.NET ネイティブツールチェーンは実行時に必要なメタデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="e417a-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="e417a-104">このトピックでは、リフレクション API の一部であるとは見なされないが、正常に実行するためにリフレクションを必要とする、一般的な API と一般的なプログラミング パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e417a-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="e417a-105">これらをソース コードで使用している場合、これらに関する情報をランタイム ディレクティブ (.rd.xml) ファイルに追加して、これらの API を呼び出しても [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外やその他の例外が実行時にスローされないようにできます。</span><span class="sxs-lookup"><span data-stu-id="e417a-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="e417a-106">Type.MakeGenericType メソッド</span><span class="sxs-lookup"><span data-stu-id="e417a-106">Type.MakeGenericType method</span></span>  

 <span data-ttu-id="e417a-107">ジェネリック型 `AppClass<T>` を動的にインスタンス化するには、次のようなコードを使用して <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e417a-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="e417a-108">このコードが実行時に成功するためには、いくつかのメタデータ項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="e417a-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="e417a-109">1 つ目は、インスタンス化されていないジェネリック型 `Browse` の `AppClass<T>` メタデータです。</span><span class="sxs-lookup"><span data-stu-id="e417a-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="e417a-110">これにより、<xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> メソッド呼び出しが成功し、有効な <xref:System.Type> オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="e417a-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="e417a-111">ただし、インスタンス化されていないジェネリック型のメタデータを追加した場合でも、<xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドを呼び出すと、次のような [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e417a-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="e417a-112">パフォーマンス上の理由から、次の種類のメタデータが削除されたため、この操作を実行できません:</span><span class="sxs-lookup"><span data-stu-id="e417a-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="e417a-113">`App1.AppClass`1<system.string>'。</span><span class="sxs-lookup"><span data-stu-id="e417a-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="e417a-114">次のランタイム ディレクティブをランタイム ディレクティブ ファイルに追加すると、`Activate` の `AppClass<T>` に対する特定のインスタンス化の <xref:System.Int32?displayProperty=nameWithType> メタデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="e417a-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="e417a-115">`AppClass<T>` に対するそれぞれ異なるインスタンス化は、<xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドにより作成され、静的に使用されていない場合、個別のディレクティブを必要とします。</span><span class="sxs-lookup"><span data-stu-id="e417a-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="e417a-116">MethodInfo.MakeGenericMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="e417a-116">MethodInfo.MakeGenericMethod method</span></span>  

 <span data-ttu-id="e417a-117">ジェネリック メソッド `Class1` を持つクラス `GetMethod<T>(T t)` があるとすると、`GetMethod` は、次のようなコードを使用してリフレクションにより呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e417a-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="e417a-118">このコードを正常に実行するには、次のようないくつかのメタデータ項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="e417a-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="e417a-119">呼び出すメソッドを持つ型の `Browse` メタデータ。</span><span class="sxs-lookup"><span data-stu-id="e417a-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="e417a-120">呼び出すメソッドの `Browse` メタデータ。</span><span class="sxs-lookup"><span data-stu-id="e417a-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="e417a-121">パブリック メソッドの場合、それを含む型のパブリック `Browse` メタデータを追加しても、メソッドが含められます。</span><span class="sxs-lookup"><span data-stu-id="e417a-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="e417a-122">リフレクション呼び出しデリゲートが .NET ネイティブツールチェーンによって削除されないようにするために、呼び出すメソッドの動的メタデータ。</span><span class="sxs-lookup"><span data-stu-id="e417a-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="e417a-123">メソッドの動的メタデータが欠落している場合、<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> メソッドを呼び出すと、次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e417a-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="e417a-124">次のランタイム ディレクティブは、必要なすべてのメタデータが必ず使用可能であるようにします。</span><span class="sxs-lookup"><span data-stu-id="e417a-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="e417a-125">`MethodInstantiation` ディレクティブは、動的に呼び出されるメソッドの異なるインスタンス化ごとに必要です。`Arguments` 要素は、それぞれ異なるインスタンス化引数を反映するために更新されます。</span><span class="sxs-lookup"><span data-stu-id="e417a-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="e417a-126">Array.CreateInstance メソッドと Type.MakeTypeArray メソッド</span><span class="sxs-lookup"><span data-stu-id="e417a-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  

 <span data-ttu-id="e417a-127">次の例は、<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 型で <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> メソッドと `Class1` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e417a-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="e417a-128">配列メタデータが存在しない場合、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e417a-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="e417a-129">配列型の `Browse` メタデータは、配列を動的にインスタンス化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="e417a-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="e417a-130">次のランタイム ディレクティブにより、`Class1[]` を動的にインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="e417a-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e417a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e417a-131">See also</span></span>

- [<span data-ttu-id="e417a-132">はじめに</span><span class="sxs-lookup"><span data-stu-id="e417a-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="e417a-133">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="e417a-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
