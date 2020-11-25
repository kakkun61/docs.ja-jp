---
title: ICorDebugILCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type:
- apiref
ms.openlocfilehash: 980e97dd8ec4792e35bb8c7fbbc2091e9ced719a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728655"
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="99b7a-102">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99b7a-102">ICorDebugILCode Interface</span></span>

<span data-ttu-id="99b7a-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="99b7a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="99b7a-104">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="99b7a-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99b7a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="99b7a-105">Methods</span></span>  
  
|<span data-ttu-id="99b7a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="99b7a-106">Method</span></span>|<span data-ttu-id="99b7a-107">説明</span><span class="sxs-lookup"><span data-stu-id="99b7a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99b7a-108">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="99b7a-108">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)|<span data-ttu-id="99b7a-109">この IL のために定義された例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="99b7a-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99b7a-110">要件</span><span class="sxs-lookup"><span data-stu-id="99b7a-110">Requirements</span></span>  

 <span data-ttu-id="99b7a-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99b7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b7a-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99b7a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99b7a-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99b7a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99b7a-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b7a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="99b7a-115">See also</span></span>

- [<span data-ttu-id="99b7a-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="99b7a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="99b7a-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="99b7a-117">Debugging</span></span>](index.md)
