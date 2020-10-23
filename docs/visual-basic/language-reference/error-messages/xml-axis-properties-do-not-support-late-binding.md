---
title: XML 軸のプロパティは遅延バインディングをサポートしていません
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: 9eef245d6f83770ce26bc9e753711543241d57fb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163286"
---
# <a name="bc31168-xml-axis-properties-do-not-support-late-binding"></a><span data-ttu-id="51a82-102">BC31168:XML 軸のプロパティは遅延バインディングをサポートしていません</span><span class="sxs-lookup"><span data-stu-id="51a82-102">BC31168: XML axis properties do not support late binding</span></span>

<span data-ttu-id="51a82-103">型指定されていないオブジェクトに対して、XML 軸プロパティが参照されています。</span><span class="sxs-lookup"><span data-stu-id="51a82-103">An XML axis property has been referenced for an untyped object.</span></span>

 <span data-ttu-id="51a82-104">**エラー ID:** BC31168</span><span class="sxs-lookup"><span data-stu-id="51a82-104">**Error ID:** BC31168</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="51a82-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="51a82-105">To correct this error</span></span>

- <span data-ttu-id="51a82-106">XML 軸プロパティを参照する前に、オブジェクトが厳密に型指定された <xref:System.Xml.Linq.XElement> オブジェクトであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51a82-106">Ensure that the object is a strong-typed <xref:System.Xml.Linq.XElement> object before referencing the XML axis property.</span></span>

## <a name="see-also"></a><span data-ttu-id="51a82-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="51a82-107">See also</span></span>

- [<span data-ttu-id="51a82-108">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="51a82-108">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="51a82-109">XML</span><span class="sxs-lookup"><span data-stu-id="51a82-109">XML</span></span>](../../programming-guide/language-features/xml/index.md)
