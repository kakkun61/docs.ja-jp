---
title: COR_PRF_RUNTIME_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: b599a97f414491ff80000f99551a727b86ae13de
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696753"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="59c1a-102">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="59c1a-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="59c1a-103">Silverlight で使用される共通言語ランタイム (CLR) のバージョンを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="59c1a-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c1a-104">構文</span><span class="sxs-lookup"><span data-stu-id="59c1a-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="59c1a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="59c1a-105">Members</span></span>  
  
|<span data-ttu-id="59c1a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="59c1a-106">Member</span></span>|<span data-ttu-id="59c1a-107">説明</span><span class="sxs-lookup"><span data-stu-id="59c1a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="59c1a-108">CLR のデスクトップバージョン。</span><span class="sxs-lookup"><span data-stu-id="59c1a-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="59c1a-109">Silverlight で使用される CLR のコアバージョン。</span><span class="sxs-lookup"><span data-stu-id="59c1a-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59c1a-110">解説</span><span class="sxs-lookup"><span data-stu-id="59c1a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c1a-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="59c1a-111">Requirements</span></span>  

 <span data-ttu-id="59c1a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59c1a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c1a-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59c1a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59c1a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59c1a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59c1a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c1a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c1a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="59c1a-116">See also</span></span>

- [<span data-ttu-id="59c1a-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="59c1a-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
