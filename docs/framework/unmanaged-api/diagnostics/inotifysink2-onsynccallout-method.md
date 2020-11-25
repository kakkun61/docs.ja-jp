---
title: INotifySink2::OnSyncCallOut メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: 00f6032f41caf54d7366de30a449f1ae76e8bbd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719984"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="79f0e-102">INotifySink2::OnSyncCallOut メソッド</span><span class="sxs-lookup"><span data-stu-id="79f0e-102">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="79f0e-103">呼び出しがタイムアウトしたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="79f0e-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f0e-104">構文</span><span class="sxs-lookup"><span data-stu-id="79f0e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79f0e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79f0e-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="79f0e-106">から発信する呼び出しの ID。「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79f0e-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="79f0e-107">入出力呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="79f0e-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="79f0e-108">入出力呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="79f0e-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79f0e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="79f0e-109">Return Value</span></span>  

 <span data-ttu-id="79f0e-110">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="79f0e-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f0e-111">要件</span><span class="sxs-lookup"><span data-stu-id="79f0e-111">Requirements</span></span>  

 <span data-ttu-id="79f0e-112">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="79f0e-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f0e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="79f0e-113">See also</span></span>

- [<span data-ttu-id="79f0e-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79f0e-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="79f0e-115">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79f0e-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="79f0e-116">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79f0e-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
