---
title: XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: d96386f8495685391203826fea85efba47c44951
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163260"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="75487-102">BC31200:XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません</span><span class="sxs-lookup"><span data-stu-id="75487-102">BC31200: XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="75487-103">XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="75487-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="75487-104">XML 機能を使用するには、コードをコードビハインドに移動します。</span><span class="sxs-lookup"><span data-stu-id="75487-104">To use XML features, move the code to code-behind.</span></span>

 <span data-ttu-id="75487-105">XML リテラルまたは XML 軸プロパティは、ASP.NET ファイルの埋め込みコード (`<%= =>`) 内で定義されます。</span><span class="sxs-lookup"><span data-stu-id="75487-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>

 <span data-ttu-id="75487-106">**エラー ID:** BC31200</span><span class="sxs-lookup"><span data-stu-id="75487-106">**Error ID:** BC31200</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="75487-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="75487-107">To correct this error</span></span>

- <span data-ttu-id="75487-108">XML リテラルまたは XML 軸プロパティが含まれているコードを、ASP.NET 分離コード ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="75487-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>

## <a name="see-also"></a><span data-ttu-id="75487-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="75487-109">See also</span></span>

- [<span data-ttu-id="75487-110">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="75487-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="75487-111">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="75487-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="75487-112">XML</span><span class="sxs-lookup"><span data-stu-id="75487-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
