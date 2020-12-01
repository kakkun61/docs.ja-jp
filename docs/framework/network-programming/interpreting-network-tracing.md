---
title: ネットワークのトレースの解釈
description: .NET Framework のさまざまな System.Net クラス メンバーのアプリケーションによる呼び出しを、トレースを利用してキャプチャする方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 63d7e36bb95054303fc4f26b0fd14dc3d10dbb7d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241565"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="462a1-103">ネットワークのトレースの解釈</span><span class="sxs-lookup"><span data-stu-id="462a1-103">Interpreting Network Tracing</span></span>

<span data-ttu-id="462a1-104">ネットワークのトレースを有効にすると、トレースを使用して、アプリケーションからさまざまな <xref:System.Net> クラス メンバーへの呼び出しをキャプチャすることができます。</span><span class="sxs-lookup"><span data-stu-id="462a1-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="462a1-105">これらの呼び出しからの出力は、次の例のようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="462a1-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="462a1-106">上の例では、[588] は現在のスレッドの一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="462a1-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="462a1-107">(4357) と (4387) は、アプリケーションが起動してから経過したミリ秒数を示すタイムスタンプです。</span><span class="sxs-lookup"><span data-stu-id="462a1-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="462a1-108">タイムスタンプの後のデータは、メソッド **Socket.Send** を開始および終了するアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="462a1-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="462a1-109">**Send** メソッドを実行するオブジェクトは、一意の識別子として 33574638 を持っています。</span><span class="sxs-lookup"><span data-stu-id="462a1-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="462a1-110">メソッドの exit トレースには、戻り値 (上の例では 61) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="462a1-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="462a1-111">ネットワークのトレースは、ハイパーテキスト転送プロトコル (HTTP) などのアプリケーション レベルのプロトコルを使用して、アプリケーションから送信されるまたはアプリケーションで受信されるネットワーク トラフィックをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="462a1-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="462a1-112">このデータは、テキストとして、また任意で、16 進数データとしてキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="462a1-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="462a1-113">16 進数データは、**tracemode** 属性の値として **includehex** を指定した場合に使用できます</span><span class="sxs-lookup"><span data-stu-id="462a1-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="462a1-114">(この属性の詳細については、「[方法:ネットワークのトレースを構成する](how-to-configure-network-tracing.md)」を参照してください)。次のサンプル トレースは、**includehex** を使用して生成されました。</span><span class="sxs-lookup"><span data-stu-id="462a1-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="462a1-115">16 進数データを省略するには、**tracemode** 属性の値として **protocolonly** を指定します。</span><span class="sxs-lookup"><span data-stu-id="462a1-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="462a1-116">次の例は、**protocolonly** が指定されている場合のトレースを示しています。</span><span class="sxs-lookup"><span data-stu-id="462a1-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="462a1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="462a1-117">See also</span></span>

- [<span data-ttu-id="462a1-118">ネットワークのトレースの有効化</span><span class="sxs-lookup"><span data-stu-id="462a1-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="462a1-119">方法: ネットワークのトレースを構成する</span><span class="sxs-lookup"><span data-stu-id="462a1-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="462a1-120">.NET Framework のネットワークのトレース</span><span class="sxs-lookup"><span data-stu-id="462a1-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
