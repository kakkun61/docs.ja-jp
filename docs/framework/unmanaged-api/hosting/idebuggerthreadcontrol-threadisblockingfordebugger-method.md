---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 8c2741d7db60781fef12293f3be0b515a55b7885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705513"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="ac4c2-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="ac4c2-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="ac4c2-103">このコールバックを送信しているスレッドがデバッグサービス内でブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="ac4c2-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac4c2-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="ac4c2-105">解説</span><span class="sxs-lookup"><span data-stu-id="ac4c2-105">Remarks</span></span>  

 <span data-ttu-id="ac4c2-106">`ThreadIsBlockingForDebugger`メソッドは常にランタイムスレッドで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ac4c2-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="ac4c2-107">メソッドは、 `ThreadIsBlockingForDebugger` スレッドがブロックされている間に、ホストに別のアクションを実行する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="ac4c2-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac4c2-108">要件</span><span class="sxs-lookup"><span data-stu-id="ac4c2-108">Requirements</span></span>  

 <span data-ttu-id="ac4c2-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac4c2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4c2-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ac4c2-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac4c2-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ac4c2-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac4c2-112">**.Net Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4c2-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4c2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac4c2-113">See also</span></span>

- [<span data-ttu-id="ac4c2-114">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac4c2-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
