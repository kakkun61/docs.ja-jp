---
title: ICorDebugStackWalk::GetFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 452635764794e01858baab10464a03c966a55271
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711938"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="f50e6-102">ICorDebugStackWalk::GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="f50e6-102">ICorDebugStackWalk::GetFrame Method</span></span>

<span data-ttu-id="f50e6-103">テキスト [オブジェクトの現在のフレーム](icordebugstackwalk-interface.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f50e6-103">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f50e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="f50e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f50e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f50e6-105">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="f50e6-106">からスタック内の現在のフレームを表す、作成されたフレームオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f50e6-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f50e6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f50e6-107">Return Value</span></span>  

 <span data-ttu-id="f50e6-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="f50e6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f50e6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f50e6-109">HRESULT</span></span>|<span data-ttu-id="f50e6-110">説明</span><span class="sxs-lookup"><span data-stu-id="f50e6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f50e6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f50e6-111">S_OK</span></span>|<span data-ttu-id="f50e6-112">ランタイムは、現在のフレームを正常に返しました。</span><span class="sxs-lookup"><span data-stu-id="f50e6-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="f50e6-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f50e6-113">E_FAIL</span></span>|<span data-ttu-id="f50e6-114">現在のフレームは返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f50e6-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="f50e6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f50e6-115">S_FALSE</span></span>|<span data-ttu-id="f50e6-116">現在のフレームはネイティブスタックフレームです。</span><span class="sxs-lookup"><span data-stu-id="f50e6-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="f50e6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f50e6-117">E_INVALIDARG</span></span>|<span data-ttu-id="f50e6-118">`pFrame` が null です。</span><span class="sxs-lookup"><span data-stu-id="f50e6-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="f50e6-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f50e6-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f50e6-120">フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f50e6-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f50e6-121">例外</span><span class="sxs-lookup"><span data-stu-id="f50e6-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f50e6-122">解説</span><span class="sxs-lookup"><span data-stu-id="f50e6-122">Remarks</span></span>  

 <span data-ttu-id="f50e6-123">`ICorDebugStackWalk` 実際のスタックフレームだけを返します。</span><span class="sxs-lookup"><span data-stu-id="f50e6-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="f50e6-124">内部フレームを返すには、 [ICorDebugThread3:: GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f50e6-124">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="f50e6-125">内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="f50e6-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f50e6-126">要件</span><span class="sxs-lookup"><span data-stu-id="f50e6-126">Requirements</span></span>  

 <span data-ttu-id="f50e6-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f50e6-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f50e6-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f50e6-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f50e6-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f50e6-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f50e6-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f50e6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50e6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f50e6-131">See also</span></span>

- [<span data-ttu-id="f50e6-132">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f50e6-132">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="f50e6-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f50e6-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f50e6-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f50e6-134">Debugging</span></span>](index.md)
