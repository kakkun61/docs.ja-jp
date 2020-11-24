---
title: System.Xml の使用法
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 46282afa6548c731b04c40d8de91a1fed997c57c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677571"
---
# <a name="systemxml-usage"></a><span data-ttu-id="1061a-102">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="1061a-102">System.Xml Usage</span></span>

<span data-ttu-id="1061a-103">このセクションでは、 <xref:System.Xml?displayProperty=nameWithType> XML データを表すために使用できる名前空間に存在するいくつかの型の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1061a-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="1061a-104">❌<xref:System.Xml.XmlNode> <xref:System.Xml.XmlDocument> XML データを表すためにまたはを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1061a-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="1061a-105"><xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> 代わりにの、、、またはの各サブタイプのインスタンスの使用を優先し <xref:System.Xml.Linq.XNode> ます。</span><span class="sxs-lookup"><span data-stu-id="1061a-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="1061a-106">`XmlNode` と `XmlDocument` は、パブリック api で公開するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="1061a-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="1061a-107">✔️は `XmlReader` 、 `IXPathNavigable` XML を `XNode` 受け入れるか返すメンバーの入力または出力として、、、またはの各サブタイプを使用します。</span><span class="sxs-lookup"><span data-stu-id="1061a-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="1061a-108">、、またはではなく、これらの抽象化を使用し `XmlDocument` `XmlNode` <xref:System.Xml.XPath.XPathDocument> ます。これは、メモリ内の xml ドキュメントの特定の実装からメソッドを分離し、、、またはを公開する仮想 XML データソースとの連携を可能にするため `XNode` `XmlReader` <xref:System.Xml.XPath.XPathNavigator> です。</span><span class="sxs-lookup"><span data-stu-id="1061a-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="1061a-109">❌`XmlDocument`基になるオブジェクトモデルまたはデータソースの XML ビューを表す型を作成する場合は、サブクラス化しないでください。</span><span class="sxs-lookup"><span data-stu-id="1061a-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="1061a-110">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="1061a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1061a-111">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="1061a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1061a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1061a-112">See also</span></span>

- [<span data-ttu-id="1061a-113">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1061a-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1061a-114">使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="1061a-114">Usage Guidelines</span></span>](usage-guidelines.md)
