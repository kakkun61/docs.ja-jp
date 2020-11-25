---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 028395b1c8677d07d4a6481740ecdc7ebb48c180
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718528"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="a1304-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="a1304-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>

<span data-ttu-id="a1304-103">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="a1304-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1304-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1304-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="a1304-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1304-105">Members</span></span>  
  
|<span data-ttu-id="a1304-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1304-106">Members</span></span>|<span data-ttu-id="a1304-107">説明</span><span class="sxs-lookup"><span data-stu-id="a1304-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="a1304-108">ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a1304-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="a1304-109">連続するブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="a1304-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1304-110">要件</span><span class="sxs-lookup"><span data-stu-id="a1304-110">Requirements</span></span>  

 <span data-ttu-id="a1304-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1304-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1304-112">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="a1304-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a1304-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1304-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1304-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1304-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1304-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1304-115">See also</span></span>

- [<span data-ttu-id="a1304-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a1304-116">Profiling Structures</span></span>](profiling-structures.md)
