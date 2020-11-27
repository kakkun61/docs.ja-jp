---
title: <AttributeImplies> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 4171345bb5337436142128623abc7d183c4477ff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288113"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="8a90f-102">\<AttributeImplies> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="8a90f-102">\<AttributeImplies> Element (.NET Native)</span></span>

<span data-ttu-id="8a90f-103">それを含む属性が適用されるコード要素のポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a90f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a90f-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a90f-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8a90f-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a90f-107">属性</span><span class="sxs-lookup"><span data-stu-id="8a90f-107">Attributes</span></span>  
  
|<span data-ttu-id="8a90f-108">属性</span><span class="sxs-lookup"><span data-stu-id="8a90f-108">Attribute</span></span>|<span data-ttu-id="8a90f-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="8a90f-109">Attribute type</span></span>|<span data-ttu-id="8a90f-110">Description</span><span class="sxs-lookup"><span data-stu-id="8a90f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="8a90f-111">リフレクション</span><span class="sxs-lookup"><span data-stu-id="8a90f-111">Reflection</span></span>|<span data-ttu-id="8a90f-112">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-112">Optional attribute.</span></span> <span data-ttu-id="8a90f-113">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8a90f-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8a90f-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="8a90f-114">Reflection</span></span>|<span data-ttu-id="8a90f-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-115">Optional attribute.</span></span> <span data-ttu-id="8a90f-116">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="8a90f-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8a90f-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="8a90f-117">Reflection</span></span>|<span data-ttu-id="8a90f-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-118">Optional attribute.</span></span> <span data-ttu-id="8a90f-119">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8a90f-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8a90f-120">シリアル化</span><span class="sxs-lookup"><span data-stu-id="8a90f-120">Serialization</span></span>|<span data-ttu-id="8a90f-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-121">Optional attribute.</span></span> <span data-ttu-id="8a90f-122">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8a90f-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8a90f-123">シリアル化</span><span class="sxs-lookup"><span data-stu-id="8a90f-123">Serialization</span></span>|<span data-ttu-id="8a90f-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-124">Optional attribute.</span></span> <span data-ttu-id="8a90f-125"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8a90f-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="8a90f-126">Serialization</span></span>|<span data-ttu-id="8a90f-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-127">Optional attribute.</span></span> <span data-ttu-id="8a90f-128"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8a90f-129">シリアル化</span><span class="sxs-lookup"><span data-stu-id="8a90f-129">Serialization</span></span>|<span data-ttu-id="8a90f-130">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-130">Optional attribute.</span></span> <span data-ttu-id="8a90f-131"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8a90f-132">Interop</span><span class="sxs-lookup"><span data-stu-id="8a90f-132">Interop</span></span>|<span data-ttu-id="8a90f-133">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-133">Optional attribute.</span></span> <span data-ttu-id="8a90f-134">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8a90f-135">Interop</span><span class="sxs-lookup"><span data-stu-id="8a90f-135">Interop</span></span>|<span data-ttu-id="8a90f-136">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-136">Optional attribute.</span></span> <span data-ttu-id="8a90f-137">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8a90f-138">Interop</span><span class="sxs-lookup"><span data-stu-id="8a90f-138">Interop</span></span>|<span data-ttu-id="8a90f-139">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-139">Optional attribute.</span></span> <span data-ttu-id="8a90f-140">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="8a90f-141">すべての属性</span><span class="sxs-lookup"><span data-stu-id="8a90f-141">All attributes</span></span>  
  
|<span data-ttu-id="8a90f-142">値</span><span class="sxs-lookup"><span data-stu-id="8a90f-142">Value</span></span>|<span data-ttu-id="8a90f-143">説明</span><span class="sxs-lookup"><span data-stu-id="8a90f-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a90f-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8a90f-144">*policy_setting*</span></span>|<span data-ttu-id="8a90f-145">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="8a90f-146">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="8a90f-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8a90f-147">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a90f-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a90f-148">子要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-148">Child Elements</span></span>  

 <span data-ttu-id="8a90f-149">なし。</span><span class="sxs-lookup"><span data-stu-id="8a90f-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a90f-150">親要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-150">Parent Elements</span></span>  
  
|<span data-ttu-id="8a90f-151">要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-151">Element</span></span>|<span data-ttu-id="8a90f-152">説明</span><span class="sxs-lookup"><span data-stu-id="8a90f-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="8a90f-153">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8a90f-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a90f-154">解説</span><span class="sxs-lookup"><span data-stu-id="8a90f-154">Remarks</span></span>  

 <span data-ttu-id="8a90f-155">`<AttributeImplies>` 要素は、それを含む型が属性 (つまり、<xref:System.Attribute?displayProperty=nameWithType> から継承されるクラス) である場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a90f-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="8a90f-156">特定のプログラム要素に属性が適用される場合、`<AttributeImplies>` 要素によって定義されるポリシーがそのプログラム要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="8a90f-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="8a90f-157">リフレクション、シリアル化、および相互運用属性はいずれも省略可能ですが、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a90f-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a90f-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a90f-158">See also</span></span>

- [<span data-ttu-id="8a90f-159">\<Type> 要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="8a90f-160">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="8a90f-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8a90f-161">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="8a90f-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="8a90f-162">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="8a90f-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
