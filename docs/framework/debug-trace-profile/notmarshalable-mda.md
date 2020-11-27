---
title: notMarshalable MDA
description: NotMarshalable マネージデバッグアシスタントを確認します。これは、呼び出しが処理されない場合、または COM インターフェイスポインターのコンテキストが間違っている場合にアクティブ化される可能性があります。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: 344c275d8645b16de3ecb06517297df06323ced4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254559"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="c8007-103">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="c8007-103">notMarshalable MDA</span></span>

<span data-ttu-id="c8007-104">共通言語ランタイム (CLR: Common Language Runtime) がコンテキスト間でインターフェイスをマーシャリングするときに、有効な登録済みのプロキシやスタブのない COM インターフェイス ポインター、または不正な `IMarshal` インターフェイスの実装を検出すると、`notMarshalable` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="c8007-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c8007-105">現象</span><span class="sxs-lookup"><span data-stu-id="c8007-105">Symptoms</span></span>  

 <span data-ttu-id="c8007-106">呼び出しが処理されないか、COM インターフェイス ポインターの不正なコンテキストで発生します。</span><span class="sxs-lookup"><span data-stu-id="c8007-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c8007-107">原因</span><span class="sxs-lookup"><span data-stu-id="c8007-107">Cause</span></span>  

 <span data-ttu-id="c8007-108">コンテキスト間でインターフェイスのマーシャリングを試みたときに、有効な登録済みのプロキシやスタブがないか、`IMarshal` が不正です。</span><span class="sxs-lookup"><span data-stu-id="c8007-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c8007-109">解像度</span><span class="sxs-lookup"><span data-stu-id="c8007-109">Resolution</span></span>  

 <span data-ttu-id="c8007-110">プロキシ スタブを登録済みであることと、`IMarshal` の実装が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8007-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8007-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="c8007-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="c8007-112">この MDA は、ランタイムに影響しません。</span><span class="sxs-lookup"><span data-stu-id="c8007-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c8007-113">出力</span><span class="sxs-lookup"><span data-stu-id="c8007-113">Output</span></span>  

 <span data-ttu-id="c8007-114">問題を説明するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="c8007-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c8007-115">構成</span><span class="sxs-lookup"><span data-stu-id="c8007-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8007-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8007-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c8007-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="c8007-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c8007-118">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="c8007-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
