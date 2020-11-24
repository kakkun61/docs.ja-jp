---
title: DOM の要素に対する新しい属性の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 1cb37e47bedf955ea2c6f9faad628df2175fb703
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826028"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="50750-102">DOM の要素に対する新しい属性の作成</span><span class="sxs-lookup"><span data-stu-id="50750-102">Creating New Attributes for Elements in the DOM</span></span>

<span data-ttu-id="50750-103">属性はノードではなく、要素ノードのプロパティであり、要素に関連付けられた **XmlAttributeCollection** に格納されるため、新しい属性を作成する方法は、他のノード型を作成する方法と異なります。</span><span class="sxs-lookup"><span data-stu-id="50750-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="50750-104">属性を作成して要素に追加するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="50750-104">There are multiple ways to create an attribute and attach it to an element:</span></span>

- <span data-ttu-id="50750-105">要素ノードを取得し、**SetAttribute** を使用してその要素の属性コレクションに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="50750-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>

- <span data-ttu-id="50750-106">**CreateAttribute** メソッドを使用して **XmlAttribute** ノードを作成します。要素ノードを取得し、**SetAttributeNode** を使用してその要素の属性コレクションにノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="50750-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>

<span data-ttu-id="50750-107">**SetAttribute** メソッドを使用して属性を要素に追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="50750-107">The following example shows how to add an attribute to an element using the **SetAttribute** method:</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
    End Sub
End Class
```  
  
```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

<span data-ttu-id="50750-108">**CreateAttribute** メソッドを使用して新しい属性を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="50750-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="50750-109">属性の作成後、**SetAttributeNode** メソッドを使用して、その属性を **book** 要素の属性コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="50750-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>

<span data-ttu-id="50750-110">次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="50750-110">Given the following XML:</span></span>
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="50750-111">新しい属性を作成し、その属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="50750-111">create a new attribute and give it a value:</span></span>

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

<span data-ttu-id="50750-112">作成した属性を要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="50750-112">and attach it to the element:</span></span>

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

<span data-ttu-id="50750-113">**出力**</span><span class="sxs-lookup"><span data-stu-id="50750-113">**Output**</span></span>

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="50750-114">完全なコード サンプルは <xref:System.Xml.XmlDocument.CreateAttribute%2A> にあります。</span><span class="sxs-lookup"><span data-stu-id="50750-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>

<span data-ttu-id="50750-115">**XmlAttribute** ノードを作成した後、**InsertBefore** メソッドまたは **InsertAfter** メソッドを使用して、コレクション内の適切な位置にそのノードを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="50750-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="50750-116">同じ名前の属性が属性コレクションに既に含まれている場合、既存の **XmlAttribute** ノードはコレクションから削除され、新しい **XmlAttribute** ノードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="50750-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="50750-117">これは、**SetAttribute** メソッドで行われる処理と同じです。</span><span class="sxs-lookup"><span data-stu-id="50750-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="50750-118">これらのメソッドは、**InsertBefore** や **InsertAfter** を実行するときに、参照ポイントとなる既存のノードをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="50750-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="50750-119">新しいノードの挿入位置を示す参照ノードが指定されていないと、**InsertAfter** メソッドは、既定でコレクションの先頭に新しいノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="50750-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="50750-120">参照ノードが指定されなかった場合の **InsertBefore** の既定の挿入位置は、コレクションの末尾です。</span><span class="sxs-lookup"><span data-stu-id="50750-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>

<span data-ttu-id="50750-121">属性の **XmlNamedNodeMap** を作成し、<xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> メソッドを使用すると、名前を指定して属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="50750-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> method.</span></span> <span data-ttu-id="50750-122">詳細については、「[NamedNodeMaps と NodeLists のノード コレクション](node-collections-in-namednodemaps-and-nodelists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50750-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span></span>

## <a name="default-attributes"></a><span data-ttu-id="50750-123">既定の属性</span><span class="sxs-lookup"><span data-stu-id="50750-123">Default attributes</span></span>

<span data-ttu-id="50750-124">既定の属性を持つと宣言された要素を作成すると、既定値を持つ新しい既定の属性が XML ドキュメント オブジェクト モデル (DOM) によって作成され、その要素に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="50750-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="50750-125">既定の属性の子ノードも同時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="50750-125">The child nodes of the default attribute are also created at this time.</span></span>

## <a name="attribute-child-nodes"></a><span data-ttu-id="50750-126">属性の子ノード</span><span class="sxs-lookup"><span data-stu-id="50750-126">Attribute child nodes</span></span>

<span data-ttu-id="50750-127">属性ノードの値は、その属性の子ノードになります。</span><span class="sxs-lookup"><span data-stu-id="50750-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="50750-128">有効な子ノードの種類は 2 つだけです。**XmlText** ノード、および **XmlEntityReference** ノードです。</span><span class="sxs-lookup"><span data-stu-id="50750-128">There are only two types of valid child nodes: **XmlText** nodes and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="50750-129">これらのノードは、**FirstChild** や **LastChild** のようなメソッドが子ノードとして処理するという意味で、子ノードと見なされます。</span><span class="sxs-lookup"><span data-stu-id="50750-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="50750-130">属性が子ノードを持つという点は、属性または属性の子ノードを削除するときに重要になります。</span><span class="sxs-lookup"><span data-stu-id="50750-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="50750-131">詳細については、「[DOM の要素ノードからの属性の削除](removing-attributes-from-an-element-node-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50750-131">For more information, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50750-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="50750-132">See also</span></span>

- [<span data-ttu-id="50750-133">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="50750-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
