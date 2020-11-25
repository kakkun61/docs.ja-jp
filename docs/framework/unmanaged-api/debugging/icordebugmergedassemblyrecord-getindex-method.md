---
title: ICorDebugMergedAssemblyRecord::GetCulture メソッド
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: 3056d22f5ddc1b11b79ee072aba68ce3ad40e8da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710637"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="9457d-102">ICorDebugMergedAssemblyRecord::GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="9457d-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>

<span data-ttu-id="9457d-103">アセンブリのプレフィックス インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9457d-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9457d-104">構文</span><span class="sxs-lookup"><span data-stu-id="9457d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9457d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9457d-105">Parameters</span></span>  

 `pIndex`  
 <span data-ttu-id="9457d-106">[out] プレフィックス インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9457d-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9457d-107">注釈</span><span class="sxs-lookup"><span data-stu-id="9457d-107">Remarks</span></span>  

 <span data-ttu-id="9457d-108">プレフィックス インデックスは、マージされたメタデータの型名での名前の競合を回避する目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="9457d-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9457d-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9457d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9457d-110">要件</span><span class="sxs-lookup"><span data-stu-id="9457d-110">Requirements</span></span>  

 <span data-ttu-id="9457d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9457d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9457d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9457d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9457d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9457d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9457d-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9457d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9457d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9457d-115">See also</span></span>

- [<span data-ttu-id="9457d-116">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9457d-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="9457d-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9457d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
