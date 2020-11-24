---
title: COR_PRF_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 1da8f414ccf0c1eed3ec7dde842dd381440a3fa9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674958"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="fc8c2-102">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="fc8c2-102">COR_PRF_FUNCTION Structure</span></span>

<span data-ttu-id="fc8c2-103">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="fc8c2-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc8c2-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="fc8c2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="fc8c2-105">Members</span></span>  
  
|<span data-ttu-id="fc8c2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fc8c2-106">Member</span></span>|<span data-ttu-id="fc8c2-107">説明</span><span class="sxs-lookup"><span data-stu-id="fc8c2-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="fc8c2-108">関数の ID。</span><span class="sxs-lookup"><span data-stu-id="fc8c2-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="fc8c2-109">再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="fc8c2-109">The ID of the recompiled function.</span></span> <span data-ttu-id="fc8c2-110">0 (ゼロ) の値は、関数の元のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="fc8c2-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc8c2-111">解説</span><span class="sxs-lookup"><span data-stu-id="fc8c2-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8c2-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="fc8c2-112">Requirements</span></span>  

 <span data-ttu-id="fc8c2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc8c2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8c2-114">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="fc8c2-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fc8c2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc8c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc8c2-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8c2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc8c2-117">See also</span></span>

- [<span data-ttu-id="fc8c2-118">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="fc8c2-118">Profiling Structures</span></span>](profiling-structures.md)
