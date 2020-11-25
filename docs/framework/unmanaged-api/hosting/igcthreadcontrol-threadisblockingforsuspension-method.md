---
title: IGCThreadControl::ThreadIsBlockingForSuspension メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 39834ba868a21ead3113f2f0d9157cd210d9798c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721648"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="c913f-102">IGCThreadControl::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="c913f-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="c913f-103">呼び出しを行っているスレッドがブロックしようとしていることをホストに通知します。ガベージコレクションやその他の中断が考えられます。</span><span class="sxs-lookup"><span data-stu-id="c913f-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c913f-104">構文</span><span class="sxs-lookup"><span data-stu-id="c913f-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c913f-105">解説</span><span class="sxs-lookup"><span data-stu-id="c913f-105">Remarks</span></span>  

 <span data-ttu-id="c913f-106">ホストは、 `ThreadIsBlockingForSuspension` スレッドを再スケジュールするかどうかをコールバック内で選択できます。</span><span class="sxs-lookup"><span data-stu-id="c913f-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c913f-107">要件</span><span class="sxs-lookup"><span data-stu-id="c913f-107">Requirements</span></span>  

 <span data-ttu-id="c913f-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c913f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c913f-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c913f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c913f-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c913f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c913f-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c913f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c913f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c913f-112">See also</span></span>

- [<span data-ttu-id="c913f-113">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c913f-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
