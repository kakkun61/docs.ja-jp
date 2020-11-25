---
title: ICorDebugFunction3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 17eda7470e5f2e4b41d1f2ed164843eaeeedea93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695870"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="d796b-102">ICorDebugFunction3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d796b-102">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="d796b-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="d796b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d796b-104">ICorDebugFunction インターフェイスを論理的に拡張して、ReJIT 要求からコードへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d796b-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d796b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d796b-105">Methods</span></span>  
  
|<span data-ttu-id="d796b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d796b-106">Method</span></span>|<span data-ttu-id="d796b-107">説明</span><span class="sxs-lookup"><span data-stu-id="d796b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d796b-108">GetActiveReJitRequestILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="d796b-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="d796b-109">アクティブな ReJIT 要求から IL を含む、 [コード](icordebugilcode-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d796b-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d796b-110">解説</span><span class="sxs-lookup"><span data-stu-id="d796b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d796b-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="d796b-111">Requirements</span></span>  

 <span data-ttu-id="d796b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d796b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d796b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d796b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d796b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d796b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d796b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d796b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d796b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d796b-116">See also</span></span>

- [<span data-ttu-id="d796b-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d796b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d796b-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d796b-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="d796b-119">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="d796b-119">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
