---
title: 要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 8ef86f05d2b39639ad5faae792eb9b2854ff0673
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830169"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="0376b-102">要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響</span><span class="sxs-lookup"><span data-stu-id="0376b-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="0376b-103">エンティティ宣言には、原則として任意のコンテンツを含めることができるため、`<!ENTITY aname "<elem>test</elem>">` のような要素が含まれている可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="0376b-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="0376b-104">`&aname;` の置換コンテンツへの展開は、XML の解析時に行われるのではありません。</span><span class="sxs-lookup"><span data-stu-id="0376b-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="0376b-105">ノードがドキュメントに配置されるまでは、要素に対する名前空間を解決できないため、XML の展開は実行されません。</span><span class="sxs-lookup"><span data-stu-id="0376b-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="0376b-106">スコープ内の名前空間が判明するのは、ノードが配置された後になります。</span><span class="sxs-lookup"><span data-stu-id="0376b-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="0376b-107">ノードがドキュメントに配置されると、名前空間の解決が行われ、結果として得られたエンティティ コンテンツが適切なノードに解析されます。</span><span class="sxs-lookup"><span data-stu-id="0376b-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0376b-108">新しく作成されたエンティティ参照ノードがいったん展開された後、再び展開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0376b-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="0376b-109">したがって、要素の置換テキストで使われる名前空間は、親ノードの設定時にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0376b-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="0376b-110">ただし、既存のエンティティ参照ノードを削除して別の場所に挿入すると、そのノードに対する名前空間が変更される可能性があります。また、**CloneNode** メソッドで複製されたエンティティ参照ノードにおいても、名前空間が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0376b-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0376b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0376b-111">See also</span></span>

- [<span data-ttu-id="0376b-112">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="0376b-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
