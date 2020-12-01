---
title: '方法: WebRequest に一致するプロトコル固有の WebResponse を取得する'
description: .NET Framework で WebRequest に一致するプロトコル固有の WebResponse を取得する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fd163c115dcd19c05f93f4c202b043440834ba9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266741"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="88bc0-103">方法: WebRequest に一致するプロトコル固有の WebResponse を取得する</span><span class="sxs-lookup"><span data-stu-id="88bc0-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="88bc0-104">この例では、WebRequest に一致するプロトコル固有の WebResponse を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="88bc0-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88bc0-105">例</span><span class="sxs-lookup"><span data-stu-id="88bc0-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88bc0-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="88bc0-106">Compiling the Code</span></span>  

 <span data-ttu-id="88bc0-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="88bc0-107">This example requires:</span></span>  
  
- <span data-ttu-id="88bc0-108">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="88bc0-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bc0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="88bc0-109">See also</span></span>

- [<span data-ttu-id="88bc0-110">データの要求</span><span class="sxs-lookup"><span data-stu-id="88bc0-110">Requesting Data</span></span>](requesting-data.md)
