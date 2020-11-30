---
title: <schemaImporterExtensions> 要素
description: <schemaImporterExtensions> 要素には、XSD の型を .NET の型にマッピングするために XmlSchemaImporter によって使用される型が含まれます。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 6b644ed1112b748be4dd301d6fa6f2a6416dc67e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722142"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="c5d7f-103">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-103">\<schemaImporterExtensions> element</span></span>

<span data-ttu-id="c5d7f-104">XSD の型を .NET の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5d7f-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span> <span data-ttu-id="c5d7f-105">構成ファイルの詳細については、「[構成ファイル スキーマ](../../framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5d7f-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d7f-106">構文</span><span class="sxs-lookup"><span data-stu-id="c5d7f-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="c5d7f-107">子要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-107">Child Elements</span></span>  
  
|<span data-ttu-id="c5d7f-108">要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-108">Element</span></span>|<span data-ttu-id="c5d7f-109">説明</span><span class="sxs-lookup"><span data-stu-id="c5d7f-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5d7f-110">\<schemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="c5d7f-111">マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="c5d7f-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="c5d7f-112">親要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c5d7f-113">要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-113">Element</span></span>|<span data-ttu-id="c5d7f-114">説明</span><span class="sxs-lookup"><span data-stu-id="c5d7f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5d7f-115">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="c5d7f-116">XML シリアル化を制御する最上位の要素です。</span><span class="sxs-lookup"><span data-stu-id="c5d7f-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5d7f-117">例</span><span class="sxs-lookup"><span data-stu-id="c5d7f-117">Example</span></span>  

 <span data-ttu-id="c5d7f-118">次のコード例では、XSD の型を .NET の型にマッピングするときに <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5d7f-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5d7f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5d7f-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c5d7f-120">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c5d7f-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c5d7f-121">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="c5d7f-122">\<schemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="c5d7f-123">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="c5d7f-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
