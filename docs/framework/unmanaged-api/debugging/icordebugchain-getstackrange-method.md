---
title: ICorDebugChain::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 841e3ca608d20a4b8618508e69195de0b1da1341
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724404"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="a5301-102">ICorDebugChain::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="a5301-102">ICorDebugChain::GetStackRange Method</span></span>

<span data-ttu-id="a5301-103">このチェーンのスタックセグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5301-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5301-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5301-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5301-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5301-105">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="a5301-106">入出力 `CORDB_ADDRESS` スタックセグメントの開始アドレスを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5301-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="a5301-107">入出力 `CORDB_ADDRESS` スタックセグメントの終了アドレスを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5301-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5301-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a5301-108">Remarks</span></span>  

 <span data-ttu-id="a5301-109">数値の範囲は、スタックフレームの位置を比較する場合にのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="a5301-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="a5301-110">実際にスタックに格納されている内容について、想定を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="a5301-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5301-111">要件</span><span class="sxs-lookup"><span data-stu-id="a5301-111">Requirements</span></span>  

 <span data-ttu-id="a5301-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5301-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5301-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5301-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5301-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5301-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5301-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5301-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
