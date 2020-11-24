---
title: ICorDebugThread2::GetActiveFunctions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
ms.openlocfilehash: 2d5674d6b5962ca539de02cda1e5658daed83622
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678754"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="3a328-102">ICorDebugThread2::GetActiveFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="3a328-102">ICorDebugThread2::GetActiveFunctions Method</span></span>

<span data-ttu-id="3a328-103">このスレッドの各フレームのアクティブな関数に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3a328-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a328-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a328-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a328-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a328-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="3a328-106">[in] `pFunctions` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3a328-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="3a328-107">入出力配列で返されたオブジェクトの数へのポインター `pFunctions` 。</span><span class="sxs-lookup"><span data-stu-id="3a328-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="3a328-108">返されるオブジェクトの数は、スタック上のマネージフレームの数と同じになります。</span><span class="sxs-lookup"><span data-stu-id="3a328-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="3a328-109">[入力、出力]COR_ACTIVE_FUNCTION オブジェクトの配列。各オブジェクトには、このスレッドのフレーム内のアクティブな関数に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a328-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="3a328-110">最初の要素はリーフフレームに使用され、その後スタックのルートに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3a328-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a328-111">注釈</span><span class="sxs-lookup"><span data-stu-id="3a328-111">Remarks</span></span>  

 <span data-ttu-id="3a328-112">`pFunctions`入力時にが null の場合、 `GetActiveFunctions` スタック上の関数の数だけを返します。</span><span class="sxs-lookup"><span data-stu-id="3a328-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="3a328-113">つまり、 `pFunctions` 入力時にが null の場合、は `GetActiveFunctions` でのみ値を返し `pcFunctions` ます。</span><span class="sxs-lookup"><span data-stu-id="3a328-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="3a328-114">この `GetActiveFunctions` メソッドは、スタックトレース内のフレームから同じ情報を取得することを目的とした最適化として使用されます。また、完全なスタックトレースでは、このメソッドに対しては、表示されないフレームオブジェクトを持つフレームだけを含みます。</span><span class="sxs-lookup"><span data-stu-id="3a328-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a328-115">要件</span><span class="sxs-lookup"><span data-stu-id="3a328-115">Requirements</span></span>  

 <span data-ttu-id="3a328-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a328-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a328-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a328-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a328-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a328-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a328-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a328-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
