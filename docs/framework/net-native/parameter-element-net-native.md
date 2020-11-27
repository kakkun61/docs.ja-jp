---
title: <Parameter> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 7e812ab60eb0a89eb868346733a8ea74e2f76d3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287866"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="3e954-102">\<Parameter> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="3e954-102">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="3e954-103">メソッドに渡された引数の型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="3e954-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e954-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e954-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e954-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3e954-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3e954-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e954-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e954-107">属性</span><span class="sxs-lookup"><span data-stu-id="3e954-107">Attributes</span></span>  
  
|<span data-ttu-id="3e954-108">属性</span><span class="sxs-lookup"><span data-stu-id="3e954-108">Attribute</span></span>|<span data-ttu-id="3e954-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="3e954-109">Attribute type</span></span>|<span data-ttu-id="3e954-110">[説明]</span><span class="sxs-lookup"><span data-stu-id="3e954-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3e954-111">全般</span><span class="sxs-lookup"><span data-stu-id="3e954-111">General</span></span>|<span data-ttu-id="3e954-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-112">Required attribute.</span></span> <span data-ttu-id="3e954-113">パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="3e954-113">The parameter name.</span></span> <span data-ttu-id="3e954-114">たとえば、メソッド シグネチャ `String.CompareTo(Object value)` の場合、`Name` 属性の値は "value" です。</span><span class="sxs-lookup"><span data-stu-id="3e954-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="3e954-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="3e954-115">Reflection</span></span>|<span data-ttu-id="3e954-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-116">Optional attribute.</span></span> <span data-ttu-id="3e954-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3e954-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="3e954-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="3e954-118">Reflection</span></span>|<span data-ttu-id="3e954-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-119">Optional attribute.</span></span> <span data-ttu-id="3e954-120">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="3e954-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="3e954-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="3e954-121">Reflection</span></span>|<span data-ttu-id="3e954-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-122">Optional attribute.</span></span> <span data-ttu-id="3e954-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="3e954-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="3e954-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="3e954-124">Serialization</span></span>|<span data-ttu-id="3e954-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-125">Optional attribute.</span></span> <span data-ttu-id="3e954-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e954-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="3e954-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="3e954-127">Serialization</span></span>|<span data-ttu-id="3e954-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-128">Optional attribute.</span></span> <span data-ttu-id="3e954-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="3e954-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="3e954-130">Serialization</span></span>|<span data-ttu-id="3e954-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-131">Optional attribute.</span></span> <span data-ttu-id="3e954-132"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="3e954-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="3e954-133">Serialization</span></span>|<span data-ttu-id="3e954-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-134">Optional attribute.</span></span> <span data-ttu-id="3e954-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="3e954-136">Interop</span><span class="sxs-lookup"><span data-stu-id="3e954-136">Interop</span></span>|<span data-ttu-id="3e954-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-137">Optional attribute.</span></span> <span data-ttu-id="3e954-138">WinRT と COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="3e954-139">Interop</span><span class="sxs-lookup"><span data-stu-id="3e954-139">Interop</span></span>|<span data-ttu-id="3e954-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-140">Optional attribute.</span></span> <span data-ttu-id="3e954-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="3e954-142">Interop</span><span class="sxs-lookup"><span data-stu-id="3e954-142">Interop</span></span>|<span data-ttu-id="3e954-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3e954-143">Optional attribute.</span></span> <span data-ttu-id="3e954-144">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e954-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3e954-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="3e954-145">Name attribute</span></span>  
  
|<span data-ttu-id="3e954-146">値</span><span class="sxs-lookup"><span data-stu-id="3e954-146">Value</span></span>|<span data-ttu-id="3e954-147">説明</span><span class="sxs-lookup"><span data-stu-id="3e954-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e954-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="3e954-148">*parameter_name*</span></span>|<span data-ttu-id="3e954-149">ポリシーが適用されるメソッド パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="3e954-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="3e954-150">たとえば、メソッド シグネチャ `String.CompareTo(Object value)` の場合、`Name` 属性の値は "value" です。</span><span class="sxs-lookup"><span data-stu-id="3e954-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3e954-151">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="3e954-151">All other attributes</span></span>  
  
|<span data-ttu-id="3e954-152">値</span><span class="sxs-lookup"><span data-stu-id="3e954-152">Value</span></span>|<span data-ttu-id="3e954-153">説明</span><span class="sxs-lookup"><span data-stu-id="3e954-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e954-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3e954-154">*policy_setting*</span></span>|<span data-ttu-id="3e954-155">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="3e954-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="3e954-156">指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="3e954-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3e954-157">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e954-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e954-158">子要素</span><span class="sxs-lookup"><span data-stu-id="3e954-158">Child Elements</span></span>  

 <span data-ttu-id="3e954-159">なし。</span><span class="sxs-lookup"><span data-stu-id="3e954-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e954-160">親要素</span><span class="sxs-lookup"><span data-stu-id="3e954-160">Parent Elements</span></span>  
  
|<span data-ttu-id="3e954-161">要素</span><span class="sxs-lookup"><span data-stu-id="3e954-161">Element</span></span>|<span data-ttu-id="3e954-162">説明</span><span class="sxs-lookup"><span data-stu-id="3e954-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="3e954-163">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="3e954-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e954-164">解説</span><span class="sxs-lookup"><span data-stu-id="3e954-164">Remarks</span></span>  

 <span data-ttu-id="3e954-165">`<Parameter>`要素は要素の子であり、特定の [\<Method>](method-element-net-native.md) メソッドパラメーターにポリシーを適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e954-165">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="3e954-166">特定のメソッド パラメーターは、型ではなく名前で指定されます。</span><span class="sxs-lookup"><span data-stu-id="3e954-166">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="3e954-167">`Activate` や `Dynamic` などのポリシーの種類を表す属性が 1 つ以上必要です。</span><span class="sxs-lookup"><span data-stu-id="3e954-167">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e954-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e954-168">See also</span></span>

- [<span data-ttu-id="3e954-169">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="3e954-169">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="3e954-170">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="3e954-170">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3e954-171">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="3e954-171">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="3e954-172">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="3e954-172">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
