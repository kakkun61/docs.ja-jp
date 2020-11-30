---
title: XML スキーマ オブジェクト モデル (SOM)
ms.date: 03/30/2017
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: b2af024f9821401b1380347580cc0dc5aeb21c3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733023"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="dde76-102">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="dde76-102">XML Schema Object Model (SOM)</span></span>

<span data-ttu-id="dde76-103">XML スキーマは、XML ドキュメント準拠の構造を作成し検証する、強力な複合ツールです。</span><span class="sxs-lookup"><span data-stu-id="dde76-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="dde76-104">リレーショナル データベースのデータ モデリングと同様に、スキーマでは XML ドキュメントの構造を定義する方法を提供しています。これは、ドキュメントで使用する要素と、これらの要素に固有のスキーマを有効にするために準拠する構造や型を指定することによって実現します。</span><span class="sxs-lookup"><span data-stu-id="dde76-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="dde76-105">スキーマ オブジェクト モデル (SOM) は、クラスのセットを <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間に提供し、それによってファイルからスキーマを読み取ったり、プログラムを使用してスキーマをメモリ内に作成したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="dde76-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="dde76-106">その後、スキーマの走査、編集、コンパイル、検証、またはファイルへの書き込みが可能になります。</span><span class="sxs-lookup"><span data-stu-id="dde76-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dde76-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dde76-107">In This Section</span></span>  

 [<span data-ttu-id="dde76-108">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="dde76-108">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="dde76-109">スキーマ オブジェクト モデル (SOM) とその機能およびクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="dde76-110">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="dde76-110">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="dde76-111">ファイルまたは他のソースから XML スキーマの読み取りおよび書き込みを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="dde76-112">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="dde76-112">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="dde76-113"><xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のクラスを使用して、XML スキーマをメモリ内に作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="dde76-114">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="dde76-114">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="dde76-115">XML スキーマを走査して、SOM に格納されている要素、属性、および型にアクセスする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="dde76-116">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="dde76-116">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="dde76-117">XML スキーマを編集する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="dde76-118">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="dde76-118">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="dde76-119">他の XML スキーマをインクルードまたはインポートして、インクルードまたはインポートするスキーマの構造を補足する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dde76-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
