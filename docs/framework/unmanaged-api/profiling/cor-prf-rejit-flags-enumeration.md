---
title: COR_PRF_REJIT_FLAGS 列挙型
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 09349674e0cf80649cc948e25a1c476c6f8097e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716370"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="89115-102">COR_PRF_REJIT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="89115-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="89115-103">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API の動作を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="89115-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89115-104">構文</span><span class="sxs-lookup"><span data-stu-id="89115-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="89115-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="89115-105">Members</span></span>  
  
|<span data-ttu-id="89115-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="89115-106">Member</span></span>|<span data-ttu-id="89115-107">説明</span><span class="sxs-lookup"><span data-stu-id="89115-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="89115-108">ReJITted メソッドは、他のメソッドでインライン化されないようにブロックされます。</span><span class="sxs-lookup"><span data-stu-id="89115-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="89115-109">メソッドをインラインで ReJITted するように `GetFunctionParameters` 要求されたメソッドに対してコールバックを受信します。</span><span class="sxs-lookup"><span data-stu-id="89115-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="89115-110">要件</span><span class="sxs-lookup"><span data-stu-id="89115-110">Requirements</span></span>  

 <span data-ttu-id="89115-111">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89115-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="89115-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89115-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89115-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89115-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89115-114">**.NET Framework のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89115-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89115-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="89115-115">See also</span></span>

- [<span data-ttu-id="89115-116">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="89115-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
