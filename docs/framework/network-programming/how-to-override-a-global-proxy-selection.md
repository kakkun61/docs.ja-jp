---
title: '方法: グローバル プロキシの選択をオーバーライドする'
description: 次の例に従って、WebRequest を URL に送信することで、グローバル プロキシの選択をオーバーライドします。これにより、この選択がプロキシ サーバーでオーバーライドされます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 8931cdc471b957447277c333ba482a0cec0e6aa5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265740"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="a313e-103">方法: グローバル プロキシの選択をオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="a313e-103">How to: Override a Global Proxy Selection</span></span>

<span data-ttu-id="a313e-104">この例では、`www.contoso.com` に **WebRequest** を送信し、ポート 80 の `alternateproxy` という名前のプロキシ サーバーでグローバル プロキシの選択をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a313e-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a313e-105">例</span><span class="sxs-lookup"><span data-stu-id="a313e-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a313e-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a313e-106">Compiling the Code</span></span>  

 <span data-ttu-id="a313e-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a313e-107">This example requires:</span></span>  
  
- <span data-ttu-id="a313e-108">**System.Net** 名前空間の [`using` ディレクティブ](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="a313e-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a313e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="a313e-109">See also</span></span>

- [<span data-ttu-id="a313e-110">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="a313e-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="a313e-111">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a313e-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
