---
title: XML 名前空間 URI '<uri>' は 'xmlns' にのみバインドできます。
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 1aec6ac0a354bfe7e0378a2e46a70a7161bf6d36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163247"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a><span data-ttu-id="3dac4-102">BC31183:XML 名前空間 URI `http://www.w3.org/XML/1998/namespace` は 'xmlns' にのみバインドできます</span><span class="sxs-lookup"><span data-stu-id="3dac4-102">BC31183: XML namespace URI `http://www.w3.org/XML/1998/namespace`; can be bound only to 'xmlns'</span></span>

<span data-ttu-id="3dac4-103">URI `http://www.w3.org/XML/1998/namespace` は、XML 名前空間宣言で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3dac4-103">The URI `http://www.w3.org/XML/1998/namespace` is used in an XML namespace declaration.</span></span> <span data-ttu-id="3dac4-104">この URI は予約された名前空間であり、XML 名前空間宣言に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3dac4-104">This URI is a reserved namespace and cannot be included in an XML namespace declaration.</span></span>

 <span data-ttu-id="3dac4-105">**エラー ID:** BC31183</span><span class="sxs-lookup"><span data-stu-id="3dac4-105">**Error ID:** BC31183</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3dac4-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3dac4-106">To correct this error</span></span>

<span data-ttu-id="3dac4-107">XML 名前空間宣言を削除するか、URI `http://www.w3.org/XML/1998/namespace` を有効な名前空間 URI に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3dac4-107">Remove the XML namespace declaration or replace the URI `http://www.w3.org/XML/1998/namespace` with a valid namespace URI.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dac4-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dac4-108">See also</span></span>

- [<span data-ttu-id="3dac4-109">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="3dac4-109">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="3dac4-110">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="3dac4-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3dac4-111">XML</span><span class="sxs-lookup"><span data-stu-id="3dac4-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
