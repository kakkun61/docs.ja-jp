---
title: <Subtypes> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: 7484152c351f59ee84b601584bd84347186628a3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287814"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="527fc-102">\<Subtypes> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="527fc-102">\<Subtypes> Element (.NET Native)</span></span>

<span data-ttu-id="527fc-103">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="527fc-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="527fc-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="527fc-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="527fc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="527fc-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="527fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="527fc-107">属性</span><span class="sxs-lookup"><span data-stu-id="527fc-107">Attributes</span></span>  
  
|<span data-ttu-id="527fc-108">属性</span><span class="sxs-lookup"><span data-stu-id="527fc-108">Attribute</span></span>|<span data-ttu-id="527fc-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="527fc-109">Attribute type</span></span>|<span data-ttu-id="527fc-110">Description</span><span class="sxs-lookup"><span data-stu-id="527fc-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="527fc-111">リフレクション</span><span class="sxs-lookup"><span data-stu-id="527fc-111">Reflection</span></span>|<span data-ttu-id="527fc-112">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-112">Optional attribute.</span></span> <span data-ttu-id="527fc-113">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="527fc-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="527fc-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="527fc-114">Reflection</span></span>|<span data-ttu-id="527fc-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-115">Optional attribute.</span></span> <span data-ttu-id="527fc-116">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="527fc-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="527fc-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="527fc-117">Reflection</span></span>|<span data-ttu-id="527fc-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-118">Optional attribute.</span></span> <span data-ttu-id="527fc-119">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="527fc-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="527fc-120">シリアル化</span><span class="sxs-lookup"><span data-stu-id="527fc-120">Serialization</span></span>|<span data-ttu-id="527fc-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-121">Optional attribute.</span></span> <span data-ttu-id="527fc-122">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="527fc-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="527fc-123">シリアル化</span><span class="sxs-lookup"><span data-stu-id="527fc-123">Serialization</span></span>|<span data-ttu-id="527fc-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-124">Optional attribute.</span></span> <span data-ttu-id="527fc-125"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="527fc-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="527fc-126">Serialization</span></span>|<span data-ttu-id="527fc-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-127">Optional attribute.</span></span> <span data-ttu-id="527fc-128"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="527fc-129">シリアル化</span><span class="sxs-lookup"><span data-stu-id="527fc-129">Serialization</span></span>|<span data-ttu-id="527fc-130">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-130">Optional attribute.</span></span> <span data-ttu-id="527fc-131"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="527fc-132">Interop</span><span class="sxs-lookup"><span data-stu-id="527fc-132">Interop</span></span>|<span data-ttu-id="527fc-133">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-133">Optional attribute.</span></span> <span data-ttu-id="527fc-134">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="527fc-135">Interop</span><span class="sxs-lookup"><span data-stu-id="527fc-135">Interop</span></span>|<span data-ttu-id="527fc-136">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-136">Optional attribute.</span></span> <span data-ttu-id="527fc-137">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="527fc-138">Interop</span><span class="sxs-lookup"><span data-stu-id="527fc-138">Interop</span></span>|<span data-ttu-id="527fc-139">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="527fc-139">Optional attribute.</span></span> <span data-ttu-id="527fc-140">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="527fc-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="527fc-141">すべての属性</span><span class="sxs-lookup"><span data-stu-id="527fc-141">All attributes</span></span>  
  
|<span data-ttu-id="527fc-142">値</span><span class="sxs-lookup"><span data-stu-id="527fc-142">Value</span></span>|<span data-ttu-id="527fc-143">説明</span><span class="sxs-lookup"><span data-stu-id="527fc-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="527fc-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="527fc-144">*policy_setting*</span></span>|<span data-ttu-id="527fc-145">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="527fc-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="527fc-146">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="527fc-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="527fc-147">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="527fc-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="527fc-148">子要素</span><span class="sxs-lookup"><span data-stu-id="527fc-148">Child Elements</span></span>  

 <span data-ttu-id="527fc-149">なし。</span><span class="sxs-lookup"><span data-stu-id="527fc-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="527fc-150">親要素</span><span class="sxs-lookup"><span data-stu-id="527fc-150">Parent Elements</span></span>  
  
|<span data-ttu-id="527fc-151">要素</span><span class="sxs-lookup"><span data-stu-id="527fc-151">Element</span></span>|<span data-ttu-id="527fc-152">説明</span><span class="sxs-lookup"><span data-stu-id="527fc-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="527fc-153">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="527fc-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="527fc-154">解説</span><span class="sxs-lookup"><span data-stu-id="527fc-154">Remarks</span></span>  

 <span data-ttu-id="527fc-155">`<Subtypes>` 要素は、それを含む型のすべてのサブタイプにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="527fc-155">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="527fc-156">派生型および基底クラスに異なるポリシーを適用する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="527fc-156">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="527fc-157">リフレクション、シリアル化、および相互運用属性はいずれも省略可能ですが、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="527fc-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="527fc-158">例</span><span class="sxs-lookup"><span data-stu-id="527fc-158">Example</span></span>  

 <span data-ttu-id="527fc-159">次の例では、`BaseClass` という名前のクラスと `Derived1` という名前のサブクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="527fc-159">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="527fc-160">次のコードに示すように、ランタイム ディレクティブ ファイルは、`Dynamic` の `Activate` ポリシーと `BaseClass` ポリシーを明示的に `Excluded` に設定します。</span><span class="sxs-lookup"><span data-stu-id="527fc-160">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="527fc-161">このため、`BaseClass` 型のオブジェクトは動的に、または `BaseClass` クラス コンストラクターの呼び出しによってインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="527fc-161">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="527fc-162">ただし、`<Subtypes>` 要素では、`BaseClass` から派生されたクラスの動的なおよびクラス コンストラクターの呼び出しによるインスタンス化は行えません。</span><span class="sxs-lookup"><span data-stu-id="527fc-162">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="527fc-163">`<Subtypes>` ディレクティブによって、`Derived1` インスタンスを <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> メソッドを呼び出すことによって動的にインスタンス化する次のコードが正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="527fc-163">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="527fc-164">ここでブロック変数は、空の Windows ストア アプリの <xref:System.Windows.Controls.TextBlock> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="527fc-164">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="527fc-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="527fc-165">See also</span></span>

- [<span data-ttu-id="527fc-166">\<Type> 要素</span><span class="sxs-lookup"><span data-stu-id="527fc-166">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="527fc-167">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="527fc-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="527fc-168">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="527fc-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="527fc-169">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="527fc-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
