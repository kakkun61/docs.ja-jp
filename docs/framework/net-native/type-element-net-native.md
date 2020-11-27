---
title: <Type> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: e71df41c4a37206910d835ee85dc3d68b4cbad4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287710"
---
# <a name="type-element-net-native"></a><span data-ttu-id="63f1b-102">\<Type> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="63f1b-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="63f1b-103">クラスや構造体などの特定の型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="63f1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="63f1b-104">Syntax</span></span>

```xml
<Type Name="type_name"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="63f1b-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-105">Attributes and Elements</span></span>

<span data-ttu-id="63f1b-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="63f1b-107">属性</span><span class="sxs-lookup"><span data-stu-id="63f1b-107">Attributes</span></span>

|<span data-ttu-id="63f1b-108">属性</span><span class="sxs-lookup"><span data-stu-id="63f1b-108">Attribute</span></span>|<span data-ttu-id="63f1b-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="63f1b-109">Attribute type</span></span>|<span data-ttu-id="63f1b-110">[説明]</span><span class="sxs-lookup"><span data-stu-id="63f1b-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="63f1b-111">全般</span><span class="sxs-lookup"><span data-stu-id="63f1b-111">General</span></span>|<span data-ttu-id="63f1b-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-112">Required attribute.</span></span> <span data-ttu-id="63f1b-113">型名を指定します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="63f1b-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="63f1b-114">Reflection</span></span>|<span data-ttu-id="63f1b-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-115">Optional attribute.</span></span> <span data-ttu-id="63f1b-116">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="63f1b-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="63f1b-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="63f1b-117">Reflection</span></span>|<span data-ttu-id="63f1b-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-118">Optional attribute.</span></span> <span data-ttu-id="63f1b-119">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="63f1b-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="63f1b-120">リフレクション</span><span class="sxs-lookup"><span data-stu-id="63f1b-120">Reflection</span></span>|<span data-ttu-id="63f1b-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-121">Optional attribute.</span></span> <span data-ttu-id="63f1b-122">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="63f1b-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="63f1b-123">シリアル化</span><span class="sxs-lookup"><span data-stu-id="63f1b-123">Serialization</span></span>|<span data-ttu-id="63f1b-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-124">Optional attribute.</span></span> <span data-ttu-id="63f1b-125">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="63f1b-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="63f1b-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="63f1b-126">Serialization</span></span>|<span data-ttu-id="63f1b-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-127">Optional attribute.</span></span> <span data-ttu-id="63f1b-128"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="63f1b-129">シリアル化</span><span class="sxs-lookup"><span data-stu-id="63f1b-129">Serialization</span></span>|<span data-ttu-id="63f1b-130">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-130">Optional attribute.</span></span> <span data-ttu-id="63f1b-131"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="63f1b-132">シリアル化</span><span class="sxs-lookup"><span data-stu-id="63f1b-132">Serialization</span></span>|<span data-ttu-id="63f1b-133">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-133">Optional attribute.</span></span> <span data-ttu-id="63f1b-134"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="63f1b-135">Interop</span><span class="sxs-lookup"><span data-stu-id="63f1b-135">Interop</span></span>|<span data-ttu-id="63f1b-136">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-136">Optional attribute.</span></span> <span data-ttu-id="63f1b-137">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="63f1b-138">Interop</span><span class="sxs-lookup"><span data-stu-id="63f1b-138">Interop</span></span>|<span data-ttu-id="63f1b-139">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-139">Optional attribute.</span></span> <span data-ttu-id="63f1b-140">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="63f1b-141">Interop</span><span class="sxs-lookup"><span data-stu-id="63f1b-141">Interop</span></span>|<span data-ttu-id="63f1b-142">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-142">Optional attribute.</span></span> <span data-ttu-id="63f1b-143">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="63f1b-144">Name 属性</span><span class="sxs-lookup"><span data-stu-id="63f1b-144">Name attribute</span></span>

|<span data-ttu-id="63f1b-145">値</span><span class="sxs-lookup"><span data-stu-id="63f1b-145">Value</span></span>|<span data-ttu-id="63f1b-146">説明</span><span class="sxs-lookup"><span data-stu-id="63f1b-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="63f1b-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="63f1b-147">*type_name*</span></span>|<span data-ttu-id="63f1b-148">型名。</span><span class="sxs-lookup"><span data-stu-id="63f1b-148">The type name.</span></span> <span data-ttu-id="63f1b-149">この `<Type>` 要素が要素または別の要素のいずれかの子である場合 [\<Namespace>](namespace-element-net-native.md) `<Type>` 、 *type_name* は名前空間なしで型の名前を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="63f1b-150">それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="63f1b-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="63f1b-151">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="63f1b-151">All other attributes</span></span>

|<span data-ttu-id="63f1b-152">値</span><span class="sxs-lookup"><span data-stu-id="63f1b-152">Value</span></span>|<span data-ttu-id="63f1b-153">説明</span><span class="sxs-lookup"><span data-stu-id="63f1b-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="63f1b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="63f1b-154">*policy_setting*</span></span>|<span data-ttu-id="63f1b-155">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="63f1b-156">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="63f1b-157">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f1b-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="63f1b-158">子要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-158">Child Elements</span></span>

|<span data-ttu-id="63f1b-159">要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-159">Element</span></span>|<span data-ttu-id="63f1b-160">説明</span><span class="sxs-lookup"><span data-stu-id="63f1b-160">Description</span></span>|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|<span data-ttu-id="63f1b-161">含んでいる型が属性の場合は、その属性が適用されるコード要素の実行時ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-161">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="63f1b-162">この型に属するイベントにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-162">Applies reflection policy to an event belonging to this type.</span></span>|
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="63f1b-163">この型に属するフィールドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-163">Applies reflection policy to a field belonging to this type.</span></span>|
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="63f1b-164">ジェネリック型のパラメーターの型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-164">Applies policy to the parameter type of a generic type.</span></span>|
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="63f1b-165">型にポリシーを適用します (それを含む `<Type>` 要素により表される型にそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="63f1b-165">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="63f1b-166">この型に属するメソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-166">Applies reflection policy to a method belonging to this type.</span></span>|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="63f1b-167">この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-167">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="63f1b-168">この型に属するプロパティにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-168">Applies reflection policy to a property belonging to this type.</span></span>|
|[\<Subtypes>](subtypes-element-net-native.md)|<span data-ttu-id="63f1b-169">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-169">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="63f1b-170">入れ子になった型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-170">Applies reflection policy to a nested type.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="63f1b-171">構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-171">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63f1b-172">親要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-172">Parent Elements</span></span>

|<span data-ttu-id="63f1b-173">要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-173">Element</span></span>|<span data-ttu-id="63f1b-174">説明</span><span class="sxs-lookup"><span data-stu-id="63f1b-174">Description</span></span>|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="63f1b-175">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-175">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="63f1b-176">指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-176">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="63f1b-177">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-177">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="63f1b-178">名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-178">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="63f1b-179">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-179">Applies reflection policy to a type and all its members.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="63f1b-180">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-180">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63f1b-181">解説</span><span class="sxs-lookup"><span data-stu-id="63f1b-181">Remarks</span></span>

<span data-ttu-id="63f1b-182">リフレクション、シリアル化、および相互運用属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="63f1b-182">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="63f1b-183">いずれも存在しない場合、`<Type>` 要素は、その子型が個々のメンバーのポリシーを定義するコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-183">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="63f1b-184">`<Type>`要素が、、、または要素の子である場合は、 [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) `<Type>` [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 親要素によって定義されたポリシー設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="63f1b-184">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="63f1b-185">ジェネリック型の `<Type>` 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-185">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="63f1b-186">構築されたジェネリック型のポリシーは、要素によって定義され [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-186">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="63f1b-187">型がジェネリック型の場合、アクサン グラーブ記号 (\`) の後ろにジェネリック パラメーターの数を付けたもので名前が修飾されます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-187">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="63f1b-188">たとえば、`Name` クラスの `<Type>` 要素の <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 属性は、``Name="System.Collections.Generic.List`1"`` と示されます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-188">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="63f1b-189">例</span><span class="sxs-lookup"><span data-stu-id="63f1b-189">Example</span></span>

<span data-ttu-id="63f1b-190">次の例では、リフレクションを使用して、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> クラスのフィールド、プロパティ、およびメソッドに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-190">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="63f1b-191">この例の変数 `b` は、 <xref:Windows.UI.Xaml.Controls.TextBlock> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="63f1b-191">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="63f1b-192">この例は単に型情報を取得するのみであるため、メタデータの可用性は `Browse` ポリシー設定により制御されます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-192">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="63f1b-193">クラスのメタデータは <xref:System.Collections.Generic.List%601> .NET ネイティブツールチェーンによって自動的に含まれないため、この例では、要求されたメンバー情報を実行時に表示できません。</span><span class="sxs-lookup"><span data-stu-id="63f1b-193">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="63f1b-194">必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-194">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="63f1b-195">親要素 [<Namespace\>](namespace-element-net-native.md) を指定しているため、`<Type>` 要素で完全修飾型名を指定する必要はないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="63f1b-195">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="63f1b-196">例</span><span class="sxs-lookup"><span data-stu-id="63f1b-196">Example</span></span>

 <span data-ttu-id="63f1b-197">次の例では、リフレクションを使用して、<xref:System.Reflection.PropertyInfo> プロパティを表す <xref:System.String.Chars%2A?displayProperty=nameWithType> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-197">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="63f1b-198">続けて、<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> メソッドを使用して文字列の 7 番目の文字の値を取得し、文字列のすべての文字を表示します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-198">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="63f1b-199">この例の変数 `b` は、 <xref:Windows.UI.Xaml.Controls.TextBlock> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="63f1b-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="63f1b-200">オブジェクトのメタデータは <xref:System.String> 使用できないため、メソッドの呼び出しでは、 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.NullReferenceException> .NET ネイティブツールチェーンを使用してコンパイルしたときに、実行時に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="63f1b-200">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="63f1b-201">例外を排除し、必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="63f1b-201">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="63f1b-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f1b-202">See also</span></span>

- [<span data-ttu-id="63f1b-203">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="63f1b-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="63f1b-204">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="63f1b-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="63f1b-205">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="63f1b-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
