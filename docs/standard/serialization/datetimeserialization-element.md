---
title: <dateTimeSerialization> 要素
description: この記事では、DateTime オブジェクトのシリアル化モードを決定する <dateTimeSerialization> 要素について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 90ae911c8942fef7a9e8238921990b0a52a47ca0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281761"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="4c8a8-103">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="4c8a8-104"><xref:System.DateTime> オブジェクトのシリアル化モードを決定します。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="4c8a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c8a8-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c8a8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4c8a8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c8a8-108">属性</span><span class="sxs-lookup"><span data-stu-id="4c8a8-108">Attributes</span></span>  
  
|<span data-ttu-id="4c8a8-109">属性</span><span class="sxs-lookup"><span data-stu-id="4c8a8-109">Attributes</span></span>|<span data-ttu-id="4c8a8-110">説明</span><span class="sxs-lookup"><span data-stu-id="4c8a8-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="4c8a8-111">任意。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-111">Optional.</span></span> <span data-ttu-id="4c8a8-112">シリアル化モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-112">Specifies the serialization mode.</span></span> <span data-ttu-id="4c8a8-113"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 値のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="4c8a8-114">既定値は **RoundTrip** です。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c8a8-115">子要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-115">Child Elements</span></span>  
 <span data-ttu-id="4c8a8-116">なし。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c8a8-117">親要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4c8a8-118">要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-118">Element</span></span>|<span data-ttu-id="4c8a8-119">説明</span><span class="sxs-lookup"><span data-stu-id="4c8a8-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c8a8-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="4c8a8-120">system.xml.serialization</span></span>|<span data-ttu-id="4c8a8-121">XML シリアル化を制御する最上位の要素です。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c8a8-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c8a8-122">Remarks</span></span>  

<span data-ttu-id="4c8a8-123">このプロパティが **Local** に設定されている場合、<xref:System.DateTime> オブジェクトは常に現地時刻として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-123">When this property is set to **Local** , <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="4c8a8-124">つまり、ローカル タイム ゾーンの情報が、シリアル化されたデータに必ず組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="4c8a8-125">このプロパティが **Roundtrip** に設定されている場合は、<xref:System.DateTime> オブジェクトが調べられ、タイム ゾーンがローカル、UTC、または未指定のいずれであるかが特定されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-125">When this property is set to **Roundtrip** , <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="4c8a8-126">その後、この特定された情報を保持する形で、<xref:System.DateTime> オブジェクトがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="4c8a8-127">これは既定の動作であり、.NET Framework の以前のバージョンと通信を行わない、すべての新しいアプリケーションで推奨されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a8-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8a8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c8a8-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="4c8a8-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="4c8a8-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4c8a8-130">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="4c8a8-131">\<schemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="4c8a8-132">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="4c8a8-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
