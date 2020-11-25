---
title: ICorDebugDataTarget2::EnumerateThreadIDs メソッド
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 31a839076b34901ae1a8f3b43021f64f77629fc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713848"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="3b6d7-102">ICorDebugDataTarget2::EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6d7-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>

<span data-ttu-id="3b6d7-103">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="3b6d7-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b6d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="3b6d7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b6d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3b6d7-105">Parameters</span></span>  

 <span data-ttu-id="3b6d7-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="3b6d7-106">cThreadIDs</span></span>  
 <span data-ttu-id="3b6d7-107">[入力] ID を返すことのできるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="3b6d7-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="3b6d7-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="3b6d7-108">pcThreadIds</span></span>  
 <span data-ttu-id="3b6d7-109">[出力] `ULONG32` 配列に書き込まれたスレッド ID の実際の数を示す `pThreadIds` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3b6d7-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="3b6d7-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="3b6d7-110">pThreadIDs</span></span>  
 <span data-ttu-id="3b6d7-111">スレッド識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="3b6d7-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b6d7-112">注釈</span><span class="sxs-lookup"><span data-stu-id="3b6d7-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b6d7-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b6d7-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b6d7-114">要件</span><span class="sxs-lookup"><span data-stu-id="3b6d7-114">Requirements</span></span>  

 <span data-ttu-id="3b6d7-115">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。**ヘッダー:** CorDebug .idl、CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b6d7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b6d7-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b6d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b6d7-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b6d7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6d7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b6d7-118">See also</span></span>

- [<span data-ttu-id="3b6d7-119">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b6d7-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="3b6d7-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b6d7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
