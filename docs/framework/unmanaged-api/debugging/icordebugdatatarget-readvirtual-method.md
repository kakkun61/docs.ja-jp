---
title: ICorDebugDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 8fb0cfc72867653eaff65f3183dacf9191604290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679729"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="996fc-102">ICorDebugDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="996fc-102">ICorDebugDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="996fc-103">指定したアドレスを開始位置として連続したメモリのブロックを取得し、指定したバッファー内でそれを返します。</span><span class="sxs-lookup"><span data-stu-id="996fc-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="996fc-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="996fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="996fc-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="996fc-106">から要求されたメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="996fc-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="996fc-107">入出力メモリが格納されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="996fc-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="996fc-108">からターゲットアドレスから取得するバイト数。</span><span class="sxs-lookup"><span data-stu-id="996fc-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="996fc-109">入出力ターゲットアドレスから実際に読み取られたバイト数。</span><span class="sxs-lookup"><span data-stu-id="996fc-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="996fc-110">これはよりも小さくなる可能性があり `bytesRequested` ます。</span><span class="sxs-lookup"><span data-stu-id="996fc-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996fc-111">注釈</span><span class="sxs-lookup"><span data-stu-id="996fc-111">Remarks</span></span>  

 <span data-ttu-id="996fc-112">最初のバイト (指定した開始アドレス) を読み取ることができる場合、呼び出しは成功を返します (null で終わる文字列など、自己記述型の長さを持つデータ構造の効率的な読み取りをサポートするため)。</span><span class="sxs-lookup"><span data-stu-id="996fc-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996fc-113">要件</span><span class="sxs-lookup"><span data-stu-id="996fc-113">Requirements</span></span>  

 <span data-ttu-id="996fc-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="996fc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996fc-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996fc-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996fc-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996fc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="996fc-118">See also</span></span>

- [<span data-ttu-id="996fc-119">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="996fc-119">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="996fc-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="996fc-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="996fc-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="996fc-121">Debugging</span></span>](index.md)
