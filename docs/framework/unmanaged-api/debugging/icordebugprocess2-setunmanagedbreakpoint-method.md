---
title: ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 1a883878107569145b97d5793f0628efefb13545
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675244"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="e8815-102">ICorDebugProcess2::SetUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="e8815-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="e8815-103">指定したネイティブイメージオフセットにアンマネージブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="e8815-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8815-104">構文</span><span class="sxs-lookup"><span data-stu-id="e8815-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8815-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8815-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e8815-106">から `CORDB_ADDRESS` ネイティブイメージオフセットを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e8815-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="e8815-107">から配列のサイズ (バイト単位) `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="e8815-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e8815-108">入出力ブレークポイントによって置き換えられるオペコードを格納している配列。</span><span class="sxs-lookup"><span data-stu-id="e8815-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="e8815-109">入出力配列で返されたバイト数へのポインター `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="e8815-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8815-110">注釈</span><span class="sxs-lookup"><span data-stu-id="e8815-110">Remarks</span></span>  

 <span data-ttu-id="e8815-111">ネイティブイメージオフセットが共通言語ランタイム (CLR) 内にある場合、ブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e8815-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="e8815-112">これにより、ブレークポイントがデバッガーによって設定されたときに、CLR は帯域外のブレークポイントのディスパッチを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e8815-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8815-113">要件</span><span class="sxs-lookup"><span data-stu-id="e8815-113">Requirements</span></span>  

 <span data-ttu-id="e8815-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8815-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8815-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8815-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8815-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8815-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8815-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8815-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
