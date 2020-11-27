---
title: <TypeInstantiation> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: a1db497762b3dc8c135154086d72fb3ac92ff5a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250750"
---
# <a name="typeinstantiation-element-net-native"></a><span data-ttu-id="98e8c-102">\<TypeInstantiation> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="98e8c-102">\<TypeInstantiation> Element (.NET Native)</span></span>

<span data-ttu-id="98e8c-103">構築されたジェネリック型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-103">Applies runtime reflection policy to a constructed generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e8c-104">構文</span><span class="sxs-lookup"><span data-stu-id="98e8c-104">Syntax</span></span>  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98e8c-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="98e8c-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98e8c-107">属性</span><span class="sxs-lookup"><span data-stu-id="98e8c-107">Attributes</span></span>  
  
|<span data-ttu-id="98e8c-108">属性</span><span class="sxs-lookup"><span data-stu-id="98e8c-108">Attribute</span></span>|<span data-ttu-id="98e8c-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="98e8c-109">Attribute type</span></span>|<span data-ttu-id="98e8c-110">[説明]</span><span class="sxs-lookup"><span data-stu-id="98e8c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="98e8c-111">全般</span><span class="sxs-lookup"><span data-stu-id="98e8c-111">General</span></span>|<span data-ttu-id="98e8c-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-112">Required attribute.</span></span> <span data-ttu-id="98e8c-113">型名を指定します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-113">Specifies the type name.</span></span>|  
|`Arguments`|<span data-ttu-id="98e8c-114">全般</span><span class="sxs-lookup"><span data-stu-id="98e8c-114">General</span></span>|<span data-ttu-id="98e8c-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-115">Required attribute.</span></span> <span data-ttu-id="98e8c-116">ジェネリック型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-116">Specifies the generic type arguments.</span></span> <span data-ttu-id="98e8c-117">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="98e8c-117">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Activate`|<span data-ttu-id="98e8c-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="98e8c-118">Reflection</span></span>|<span data-ttu-id="98e8c-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-119">Optional attribute.</span></span> <span data-ttu-id="98e8c-120">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="98e8c-120">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="98e8c-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="98e8c-121">Reflection</span></span>|<span data-ttu-id="98e8c-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-122">Optional attribute.</span></span> <span data-ttu-id="98e8c-123">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="98e8c-123">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="98e8c-124">リフレクション</span><span class="sxs-lookup"><span data-stu-id="98e8c-124">Reflection</span></span>|<span data-ttu-id="98e8c-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-125">Optional attribute.</span></span> <span data-ttu-id="98e8c-126">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="98e8c-126">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="98e8c-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="98e8c-127">Serialization</span></span>|<span data-ttu-id="98e8c-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-128">Optional attribute.</span></span> <span data-ttu-id="98e8c-129">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="98e8c-129">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="98e8c-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="98e8c-130">Serialization</span></span>|<span data-ttu-id="98e8c-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-131">Optional attribute.</span></span> <span data-ttu-id="98e8c-132"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-132">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="98e8c-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="98e8c-133">Serialization</span></span>|<span data-ttu-id="98e8c-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-134">Optional attribute.</span></span> <span data-ttu-id="98e8c-135"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-135">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="98e8c-136">シリアル化</span><span class="sxs-lookup"><span data-stu-id="98e8c-136">Serialization</span></span>|<span data-ttu-id="98e8c-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-137">Optional attribute.</span></span> <span data-ttu-id="98e8c-138"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-138">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="98e8c-139">Interop</span><span class="sxs-lookup"><span data-stu-id="98e8c-139">Interop</span></span>|<span data-ttu-id="98e8c-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-140">Optional attribute.</span></span> <span data-ttu-id="98e8c-141">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-141">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="98e8c-142">Interop</span><span class="sxs-lookup"><span data-stu-id="98e8c-142">Interop</span></span>|<span data-ttu-id="98e8c-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-143">Optional attribute.</span></span> <span data-ttu-id="98e8c-144">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-144">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="98e8c-145">Interop</span><span class="sxs-lookup"><span data-stu-id="98e8c-145">Interop</span></span>|<span data-ttu-id="98e8c-146">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-146">Optional attribute.</span></span> <span data-ttu-id="98e8c-147">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-147">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="98e8c-148">Name 属性</span><span class="sxs-lookup"><span data-stu-id="98e8c-148">Name attribute</span></span>  
  
|<span data-ttu-id="98e8c-149">値</span><span class="sxs-lookup"><span data-stu-id="98e8c-149">Value</span></span>|<span data-ttu-id="98e8c-150">説明</span><span class="sxs-lookup"><span data-stu-id="98e8c-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98e8c-151">*type_name*</span><span class="sxs-lookup"><span data-stu-id="98e8c-151">*type_name*</span></span>|<span data-ttu-id="98e8c-152">型名。</span><span class="sxs-lookup"><span data-stu-id="98e8c-152">The type name.</span></span> <span data-ttu-id="98e8c-153">この `<TypeInstantiation>` 要素が [\<Namespace>](namespace-element-net-native.md) 要素、 [\<Type>](type-element-net-native.md) 要素、または別の要素の子である場合 `<TypeInstantiation>` 、 *type_name* は名前空間なしで型の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="98e8c-153">If this `<TypeInstantiation>` element is the child of a [\<Namespace>](namespace-element-net-native.md) element, a [\<Type>](type-element-net-native.md) element, or another `<TypeInstantiation>` element, *type_name* can specify the name of the type without its namespace.</span></span> <span data-ttu-id="98e8c-154">それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e8c-154">Otherwise, *type_name* must include the fully qualified type name.</span></span> <span data-ttu-id="98e8c-155">型名は修飾されません。</span><span class="sxs-lookup"><span data-stu-id="98e8c-155">The type name isn't decorated.</span></span> <span data-ttu-id="98e8c-156">たとえば、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> オブジェクトの場合、`<TypeInstantiation>` 要素は次のように示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="98e8c-156">For example, for a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> object, the `<TypeInstantiation>` element might appear as follows:</span></span><br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="98e8c-157">引数属性</span><span class="sxs-lookup"><span data-stu-id="98e8c-157">Arguments attribute</span></span>  
  
|<span data-ttu-id="98e8c-158">値</span><span class="sxs-lookup"><span data-stu-id="98e8c-158">Value</span></span>|<span data-ttu-id="98e8c-159">説明</span><span class="sxs-lookup"><span data-stu-id="98e8c-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98e8c-160">*type_argument*</span><span class="sxs-lookup"><span data-stu-id="98e8c-160">*type_argument*</span></span>|<span data-ttu-id="98e8c-161">ジェネリック型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-161">Specifies the generic type arguments.</span></span> <span data-ttu-id="98e8c-162">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="98e8c-162">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="98e8c-163">各引数は、完全修飾型名で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e8c-163">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="98e8c-164">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="98e8c-164">All other attributes</span></span>  
  
|<span data-ttu-id="98e8c-165">値</span><span class="sxs-lookup"><span data-stu-id="98e8c-165">Value</span></span>|<span data-ttu-id="98e8c-166">説明</span><span class="sxs-lookup"><span data-stu-id="98e8c-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98e8c-167">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="98e8c-167">*policy_setting*</span></span>|<span data-ttu-id="98e8c-168">構築されたジェネリック型のこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-168">The setting to apply to this policy type for the constructed generic type.</span></span> <span data-ttu-id="98e8c-169">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-169">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="98e8c-170">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98e8c-170">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98e8c-171">子要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-171">Child Elements</span></span>  
  
|<span data-ttu-id="98e8c-172">要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-172">Element</span></span>|<span data-ttu-id="98e8c-173">説明</span><span class="sxs-lookup"><span data-stu-id="98e8c-173">Description</span></span>|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="98e8c-174">この型に属するイベントにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-174">Applies reflection policy to an event belonging to this type.</span></span>|  
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="98e8c-175">この型に属するフィールドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-175">Applies reflection policy to a field belonging to this type.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="98e8c-176">型にポリシーを適用します (それを含む `<TypeInstantiation>` 要素により表される型にそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="98e8c-176">Applies policy to a type, if that policy has been applied to the type represented by the containing `<TypeInstantiation>` element.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="98e8c-177">この型に属するメソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-177">Applies reflection policy to a method belonging to this type.</span></span>|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="98e8c-178">この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-178">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|  
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="98e8c-179">この型に属するプロパティにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-179">Applies reflection policy to a property belonging to this type.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="98e8c-180">入れ子になった型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-180">Applies reflection policy to a nested type.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="98e8c-181">入れ子になった構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-181">Applies reflection policy to a nested constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98e8c-182">親要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-182">Parent Elements</span></span>  
  
|<span data-ttu-id="98e8c-183">要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-183">Element</span></span>|<span data-ttu-id="98e8c-184">説明</span><span class="sxs-lookup"><span data-stu-id="98e8c-184">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="98e8c-185">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-185">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="98e8c-186">指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-186">Applies reflection policy to all the types in a specified assembly.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="98e8c-187">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-187">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="98e8c-188">名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-188">Applies reflection policy to all the types in a namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="98e8c-189">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-189">Applies reflection policy to a type and all its members.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="98e8c-190">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-190">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98e8c-191">解説</span><span class="sxs-lookup"><span data-stu-id="98e8c-191">Remarks</span></span>  

 <span data-ttu-id="98e8c-192">リフレクション、シリアル化、および相互運用属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="98e8c-192">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="98e8c-193">ただし、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e8c-193">However, at least one must be present.</span></span>  
  
 <span data-ttu-id="98e8c-194">`<TypeInstantiation>`要素が、、、またはの各要素の子である場合、 [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) 親要素によって定義されたポリシー設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="98e8c-194">If a `<TypeInstantiation>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), or [\<Type>](type-element-net-native.md), element, it overrides the policy settings defined by the parent element.</span></span> <span data-ttu-id="98e8c-195">要素が [\<Type>](type-element-net-native.md) 対応するジェネリック型定義を定義する場合、要素は、 `<TypeInstantiation>` 指定された構築ジェネリック型のインスタンス化に対してのみランタイムリフレクションポリシーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="98e8c-195">If a [\<Type>](type-element-net-native.md) element defines a corresponding generic type definition, the `<TypeInstantiation>` element overrides runtime reflection policy only for instantiations of the specified constructed generic type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98e8c-196">例</span><span class="sxs-lookup"><span data-stu-id="98e8c-196">Example</span></span>  

 <span data-ttu-id="98e8c-197">次の例では、リフレクションを使用して、構築された <xref:System.Collections.Generic.Dictionary%602> オブジェクトからジェネリック型定義を取得します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-197">The following example uses reflection to retrieve the generic type definition from a constructed <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="98e8c-198">また、リフレクションを使用して、構築されたジェネリック型とジェネリック型定義を表す <xref:System.Type> オブジェクトに関する情報も表示します。</span><span class="sxs-lookup"><span data-stu-id="98e8c-198">It also uses reflection to display information about <xref:System.Type> objects that represent constructed generic types and generic type definitions.</span></span> <span data-ttu-id="98e8c-199">この例の変数 `b` は、 <xref:Windows.UI.Xaml.Controls.TextBlock> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="98e8c-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 <span data-ttu-id="98e8c-200">.NET ネイティブツールチェーンを使用してコンパイルした後、この例では、メソッドを呼び出す行で [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外がスローされ <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="98e8c-200">After compilation with the .NET Native tool chain, the example throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception on the line that calls the <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="98e8c-201">次の `<TypeInstantiation>` 要素をランタイム ディレクティブ ファイルに追加すると、この例外を排除して、必要なメタデータを提供できます。</span><span class="sxs-lookup"><span data-stu-id="98e8c-201">You can eliminate the exception and provide the necessary metadata by adding the following `<TypeInstantiation>` element to the runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98e8c-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="98e8c-202">See also</span></span>

- [<span data-ttu-id="98e8c-203">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="98e8c-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="98e8c-204">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="98e8c-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="98e8c-205">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="98e8c-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
