---
title: <Event> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: b1cf2239e58839c5026bc375ba04568227881bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288100"
---
# <a name="event-element-net-native"></a><span data-ttu-id="2d393-102">\<Event> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="2d393-102">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="2d393-103">イベントにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="2d393-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d393-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d393-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d393-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d393-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2d393-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d393-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d393-107">属性</span><span class="sxs-lookup"><span data-stu-id="2d393-107">Attributes</span></span>  
  
|<span data-ttu-id="2d393-108">属性</span><span class="sxs-lookup"><span data-stu-id="2d393-108">Attribute</span></span>|<span data-ttu-id="2d393-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="2d393-109">Attribute type</span></span>|<span data-ttu-id="2d393-110">[説明]</span><span class="sxs-lookup"><span data-stu-id="2d393-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="2d393-111">全般</span><span class="sxs-lookup"><span data-stu-id="2d393-111">General</span></span>|<span data-ttu-id="2d393-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2d393-112">Required attribute.</span></span> <span data-ttu-id="2d393-113">イベントの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d393-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="2d393-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="2d393-114">Reflection</span></span>|<span data-ttu-id="2d393-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="2d393-115">Optional attribute.</span></span> <span data-ttu-id="2d393-116">イベントに関する情報の照会やイベントの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="2d393-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="2d393-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="2d393-117">Reflection</span></span>|<span data-ttu-id="2d393-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="2d393-118">Optional attribute.</span></span> <span data-ttu-id="2d393-119">イベントへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2d393-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="2d393-120">このポリシーにより、実行時にイベントを動的に処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2d393-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="2d393-121">Name 属性</span><span class="sxs-lookup"><span data-stu-id="2d393-121">Name attribute</span></span>  
  
|<span data-ttu-id="2d393-122">値</span><span class="sxs-lookup"><span data-stu-id="2d393-122">Value</span></span>|<span data-ttu-id="2d393-123">説明</span><span class="sxs-lookup"><span data-stu-id="2d393-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d393-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="2d393-124">*method_name*</span></span>|<span data-ttu-id="2d393-125">イベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="2d393-125">The event name.</span></span> <span data-ttu-id="2d393-126">イベントの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="2d393-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="2d393-127">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="2d393-127">All other attributes</span></span>  
  
|<span data-ttu-id="2d393-128">値</span><span class="sxs-lookup"><span data-stu-id="2d393-128">Value</span></span>|<span data-ttu-id="2d393-129">説明</span><span class="sxs-lookup"><span data-stu-id="2d393-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d393-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="2d393-130">*policy_setting*</span></span>|<span data-ttu-id="2d393-131">イベントのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="2d393-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="2d393-132">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="2d393-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="2d393-133">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d393-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d393-134">子要素</span><span class="sxs-lookup"><span data-stu-id="2d393-134">Child Elements</span></span>  

 <span data-ttu-id="2d393-135">なし。</span><span class="sxs-lookup"><span data-stu-id="2d393-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d393-136">親要素</span><span class="sxs-lookup"><span data-stu-id="2d393-136">Parent Elements</span></span>  
  
|<span data-ttu-id="2d393-137">要素</span><span class="sxs-lookup"><span data-stu-id="2d393-137">Element</span></span>|<span data-ttu-id="2d393-138">説明</span><span class="sxs-lookup"><span data-stu-id="2d393-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="2d393-139">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="2d393-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="2d393-140">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="2d393-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d393-141">解説</span><span class="sxs-lookup"><span data-stu-id="2d393-141">Remarks</span></span>  

 <span data-ttu-id="2d393-142">イベントのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="2d393-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d393-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d393-143">See also</span></span>

- [<span data-ttu-id="2d393-144">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="2d393-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="2d393-145">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="2d393-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="2d393-146">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="2d393-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
