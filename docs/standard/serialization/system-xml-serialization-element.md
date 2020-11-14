---
title: <system.xml.serialization> 要素
description: この記事では、XML シリアル化を制御する最上位要素である <system.xml.serialization> 要素について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282386"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="60bd3-103">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="60bd3-104">XML シリアル化を制御する最上位の要素です。</span><span class="sxs-lookup"><span data-stu-id="60bd3-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="60bd3-105">構成ファイルの詳細については、「[構成ファイル スキーマ](../../framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60bd3-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="60bd3-106">構文</span><span class="sxs-lookup"><span data-stu-id="60bd3-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60bd3-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-107">Attributes and Elements</span></span>

<span data-ttu-id="60bd3-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="60bd3-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="60bd3-109">属性</span><span class="sxs-lookup"><span data-stu-id="60bd3-109">Attributes</span></span>

<span data-ttu-id="60bd3-110">なし。</span><span class="sxs-lookup"><span data-stu-id="60bd3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60bd3-111">子要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-111">Child Elements</span></span>

|<span data-ttu-id="60bd3-112">要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-112">Element</span></span>|<span data-ttu-id="60bd3-113">説明</span><span class="sxs-lookup"><span data-stu-id="60bd3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60bd3-114">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="60bd3-115"><xref:System.DateTime> オブジェクトのシリアル化モードを決定します。</span><span class="sxs-lookup"><span data-stu-id="60bd3-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="60bd3-116">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="60bd3-117">XSD の型を .NET の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60bd3-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="60bd3-118">親要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-118">Parent Elements</span></span>

|<span data-ttu-id="60bd3-119">要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-119">Element</span></span>|<span data-ttu-id="60bd3-120">説明</span><span class="sxs-lookup"><span data-stu-id="60bd3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60bd3-121">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="60bd3-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="60bd3-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="60bd3-123">例</span><span class="sxs-lookup"><span data-stu-id="60bd3-123">Example</span></span>

<span data-ttu-id="60bd3-124">次のコード例では、<xref:System.DateTime> オブジェクトのシリアル化モードを指定し、XSD の型を .NET の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="60bd3-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="60bd3-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="60bd3-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="60bd3-126">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="60bd3-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="60bd3-127">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="60bd3-128">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="60bd3-129">\<schemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="60bd3-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
