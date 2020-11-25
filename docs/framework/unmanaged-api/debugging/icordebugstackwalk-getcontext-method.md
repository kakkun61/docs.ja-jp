---
title: ICorDebugStackWalk::GetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 927f2077b4bb71177c24816774d06643ebdaa922
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711963"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="d6bdc-102">ICorDebugStackWalk::GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="d6bdc-102">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="d6bdc-103">[は、テキストオブジェクト内](icordebugstackwalk-interface.md)の現在のフレームのコンテキストを返します。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6bdc-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6bdc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6bdc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6bdc-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="d6bdc-106">からコンテキストバッファーの要求されたコンテンツを示すフラグ (Winnt.h で定義されています)。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="d6bdc-107">からコンテキストバッファーに割り当てられたサイズ。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d6bdc-108">入出力コンテキストの実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-108">[out] The actual size of the context.</span></span> <span data-ttu-id="d6bdc-109">この値は、コンテキストバッファーのサイズ以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="d6bdc-110">入出力コンテキストバッファー。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6bdc-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6bdc-111">Return Value</span></span>  

 <span data-ttu-id="d6bdc-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6bdc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6bdc-113">HRESULT</span></span>|<span data-ttu-id="d6bdc-114">説明</span><span class="sxs-lookup"><span data-stu-id="d6bdc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6bdc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6bdc-115">S_OK</span></span>|<span data-ttu-id="d6bdc-116">現在のフレームのコンテキストが正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="d6bdc-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6bdc-117">E_FAIL</span></span>|<span data-ttu-id="d6bdc-118">コンテキストを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="d6bdc-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT バッファー)</span><span class="sxs-lookup"><span data-stu-id="d6bdc-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="d6bdc-120">コンテキストバッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="d6bdc-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="d6bdc-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="d6bdc-122">フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d6bdc-123">例外</span><span class="sxs-lookup"><span data-stu-id="d6bdc-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6bdc-124">解説</span><span class="sxs-lookup"><span data-stu-id="d6bdc-124">Remarks</span></span>  

 <span data-ttu-id="d6bdc-125">アンワインドでは、非揮発性レジスタなどのレジスタのサブセットのみが復元されるため、呼び出し時にコンテキストがレジスタの状態と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6bdc-126">要件</span><span class="sxs-lookup"><span data-stu-id="d6bdc-126">Requirements</span></span>  

 <span data-ttu-id="d6bdc-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6bdc-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6bdc-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6bdc-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6bdc-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6bdc-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6bdc-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6bdc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bdc-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6bdc-131">See also</span></span>

- [<span data-ttu-id="d6bdc-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6bdc-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d6bdc-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d6bdc-133">Debugging</span></span>](index.md)
