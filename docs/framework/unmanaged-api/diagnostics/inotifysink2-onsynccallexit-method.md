---
title: INotifySink2::OnSyncCallExit メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 9049cd42e9c10cdcff62b005094b56c9df9ce975
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719997"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="d6ebd-102">INotifySink2::OnSyncCallExit メソッド</span><span class="sxs-lookup"><span data-stu-id="d6ebd-102">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="d6ebd-103">呼び出しを終了したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ebd-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6ebd-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ebd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6ebd-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="d6ebd-106">から終了する呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="d6ebd-107">「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="d6ebd-108">入出力呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="d6ebd-109">入出力呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6ebd-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6ebd-110">Return Value</span></span>  

 <span data-ttu-id="d6ebd-111">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="d6ebd-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ebd-112">要件</span><span class="sxs-lookup"><span data-stu-id="d6ebd-112">Requirements</span></span>  

 <span data-ttu-id="d6ebd-113">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="d6ebd-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ebd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6ebd-114">See also</span></span>

- [<span data-ttu-id="d6ebd-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ebd-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="d6ebd-116">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ebd-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="d6ebd-117">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ebd-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
