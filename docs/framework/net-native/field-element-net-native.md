---
title: <Field> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: e63dc293c42aa620b7f7ac15fc0454bc603b9dde
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251049"
---
# <a name="field-element-net-native"></a><span data-ttu-id="87383-102">\<Field> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="87383-102">\<Field> Element (.NET Native)</span></span>

<span data-ttu-id="87383-103">フィールドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="87383-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87383-104">構文</span><span class="sxs-lookup"><span data-stu-id="87383-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87383-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="87383-105">Attributes and Elements</span></span>  

 <span data-ttu-id="87383-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="87383-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87383-107">属性</span><span class="sxs-lookup"><span data-stu-id="87383-107">Attributes</span></span>  
  
|<span data-ttu-id="87383-108">属性</span><span class="sxs-lookup"><span data-stu-id="87383-108">Attribute</span></span>|<span data-ttu-id="87383-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="87383-109">Attribute type</span></span>|<span data-ttu-id="87383-110">[説明]</span><span class="sxs-lookup"><span data-stu-id="87383-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="87383-111">全般</span><span class="sxs-lookup"><span data-stu-id="87383-111">General</span></span>|<span data-ttu-id="87383-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="87383-112">Required attribute.</span></span> <span data-ttu-id="87383-113">フィールド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="87383-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="87383-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="87383-114">Reflection</span></span>|<span data-ttu-id="87383-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="87383-115">Optional attribute.</span></span> <span data-ttu-id="87383-116">フィールドに関する情報の照会やフィールドの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="87383-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="87383-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="87383-117">Reflection</span></span>|<span data-ttu-id="87383-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="87383-118">Optional attribute.</span></span> <span data-ttu-id="87383-119">フィールドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="87383-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="87383-120">このポリシーにより、実行時にフィールドを動的に設定または取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="87383-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="87383-121">シリアル化</span><span class="sxs-lookup"><span data-stu-id="87383-121">Serialization</span></span>|<span data-ttu-id="87383-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="87383-122">Optional attribute.</span></span> <span data-ttu-id="87383-123">フィールドへの実行時アクセスを制御して、型インスタンスを Newtonsoft の JSON シリアライザーなどのライブラリによってシリアル化できるようにしたり、データ バインディングで使用できるようにしたりします。</span><span class="sxs-lookup"><span data-stu-id="87383-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="87383-124">Name 属性</span><span class="sxs-lookup"><span data-stu-id="87383-124">Name attribute</span></span>  
  
|<span data-ttu-id="87383-125">値</span><span class="sxs-lookup"><span data-stu-id="87383-125">Value</span></span>|<span data-ttu-id="87383-126">説明</span><span class="sxs-lookup"><span data-stu-id="87383-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="87383-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="87383-127">*method_name*</span></span>|<span data-ttu-id="87383-128">フィールド名。</span><span class="sxs-lookup"><span data-stu-id="87383-128">The field name.</span></span> <span data-ttu-id="87383-129">フィールドの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="87383-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="87383-130">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="87383-130">All other attributes</span></span>  
  
|<span data-ttu-id="87383-131">値</span><span class="sxs-lookup"><span data-stu-id="87383-131">Value</span></span>|<span data-ttu-id="87383-132">説明</span><span class="sxs-lookup"><span data-stu-id="87383-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="87383-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="87383-133">*policy_setting*</span></span>|<span data-ttu-id="87383-134">フィールドのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="87383-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="87383-135">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="87383-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="87383-136">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87383-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87383-137">子要素</span><span class="sxs-lookup"><span data-stu-id="87383-137">Child Elements</span></span>  

 <span data-ttu-id="87383-138">なし。</span><span class="sxs-lookup"><span data-stu-id="87383-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87383-139">親要素</span><span class="sxs-lookup"><span data-stu-id="87383-139">Parent Elements</span></span>  
  
|<span data-ttu-id="87383-140">要素</span><span class="sxs-lookup"><span data-stu-id="87383-140">Element</span></span>|<span data-ttu-id="87383-141">説明</span><span class="sxs-lookup"><span data-stu-id="87383-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="87383-142">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="87383-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="87383-143">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="87383-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87383-144">解説</span><span class="sxs-lookup"><span data-stu-id="87383-144">Remarks</span></span>  

 <span data-ttu-id="87383-145">フィールドのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="87383-145">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87383-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="87383-146">See also</span></span>

- [<span data-ttu-id="87383-147">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="87383-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="87383-148">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="87383-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="87383-149">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="87383-149">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
