---
title: 新しいノードの作成時における XML 要素名および属性名の検証
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 5bad0faf8aec2f6f1d2395477867fbdaeea4a97a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733062"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="00496-102">新しいノードの作成時における XML 要素名および属性名の検証</span><span class="sxs-lookup"><span data-stu-id="00496-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>

<span data-ttu-id="00496-103">XML ドキュメント オブジェクト モデル (DOM) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。</span><span class="sxs-lookup"><span data-stu-id="00496-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="00496-104">名前に無効な文字が含まれていると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="00496-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="00496-105">名前が正しくエンコードされ、有効であることを保証するには、**XmlConvert** クラスを使用して名前をエンコードし、アプリケーション レベルで名前をデコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00496-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="00496-106">**XmlWriter** には、整形式の XML を生成するための追加の処理を行うメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="00496-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00496-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="00496-107">See also</span></span>

- [<span data-ttu-id="00496-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="00496-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
