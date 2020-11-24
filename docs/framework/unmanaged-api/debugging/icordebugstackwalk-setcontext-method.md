---
title: ICorDebugStackWalk::SetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 1ae9fc1f1154866945d40cd63042fa8a43b88905
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677298"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="cfaac-102">ICorDebugStackWalk::SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="cfaac-102">ICorDebugStackWalk::SetContext Method</span></span>

<span data-ttu-id="cfaac-103">[オブジェクトの現在のコンテキスト](icordebugstackwalk-interface.md)をスレッドの有効なコンテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="cfaac-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfaac-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfaac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfaac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfaac-105">Parameters</span></span>  

 `flag`  
 <span data-ttu-id="cfaac-106">からコンテキストがスタックのアクティブなフレームからのものであるか、またはスタックのアンワインドによって取得されたコンテキストであるかを示す [Cordebugsetcontextflag](cordebugsetcontextflag-enumeration.md) フラグ。</span><span class="sxs-lookup"><span data-stu-id="cfaac-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cfaac-107">からバッファーに割り当てられたサイズ `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="cfaac-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="cfaac-108">から `CONTEXT` バッファー。</span><span class="sxs-lookup"><span data-stu-id="cfaac-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfaac-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="cfaac-109">Return Value</span></span>  

 <span data-ttu-id="cfaac-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="cfaac-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cfaac-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfaac-111">HRESULT</span></span>|<span data-ttu-id="cfaac-112">説明</span><span class="sxs-lookup"><span data-stu-id="cfaac-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfaac-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfaac-113">S_OK</span></span>|<span data-ttu-id="cfaac-114">`ICorDebugStackWalk`オブジェクトのコンテキストが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="cfaac-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="cfaac-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfaac-115">E_FAIL</span></span>|<span data-ttu-id="cfaac-116">`ICorDebugStackWalk`オブジェクトのコンテキストが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="cfaac-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="cfaac-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cfaac-117">E_INVALIDARG</span></span>|<span data-ttu-id="cfaac-118">コンテキストが null です。</span><span class="sxs-lookup"><span data-stu-id="cfaac-118">The context is null.</span></span>|  
|<span data-ttu-id="cfaac-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="cfaac-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="cfaac-120">コンテキストバッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="cfaac-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cfaac-121">例外</span><span class="sxs-lookup"><span data-stu-id="cfaac-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfaac-122">解説</span><span class="sxs-lookup"><span data-stu-id="cfaac-122">Remarks</span></span>  

 <span data-ttu-id="cfaac-123">このメソッドは、スレッドの現在のコンテキストを変更しません。</span><span class="sxs-lookup"><span data-stu-id="cfaac-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="cfaac-124">現在のコンテキストを無効なコンテキストに設定すると、スタックウォーカーから予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cfaac-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="cfaac-125">このコンテキストの完全なビットごとのコピーを取得するには、次のようにして、" [GetContext](icordebugstackwalk-getcontext-method.md) " メソッドを直ちに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cfaac-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfaac-126">要件</span><span class="sxs-lookup"><span data-stu-id="cfaac-126">Requirements</span></span>  

 <span data-ttu-id="cfaac-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfaac-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfaac-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfaac-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfaac-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfaac-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfaac-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfaac-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaac-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfaac-131">See also</span></span>

- [<span data-ttu-id="cfaac-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cfaac-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfaac-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="cfaac-133">Debugging</span></span>](index.md)
