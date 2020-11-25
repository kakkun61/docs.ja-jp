---
title: GetCachePath 関数
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724469"
---
# <a name="getcachepath-function"></a><span data-ttu-id="b5a56-102">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="b5a56-102">GetCachePath Function</span></span>

<span data-ttu-id="b5a56-103">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5a56-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a56-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5a56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5a56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5a56-105">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="b5a56-106">からキャッシュされたアセンブリのソースを示す [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 値。</span><span class="sxs-lookup"><span data-stu-id="b5a56-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="b5a56-107">入出力パスへの返されたポインター。</span><span class="sxs-lookup"><span data-stu-id="b5a56-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="b5a56-108">[入力、出力]要求された最大長 `pwzCachePath` 。戻り値は、の実際の長さ `pwzCachePath` 。</span><span class="sxs-lookup"><span data-stu-id="b5a56-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5a56-109">要件</span><span class="sxs-lookup"><span data-stu-id="b5a56-109">Requirements</span></span>  

 <span data-ttu-id="b5a56-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5a56-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a56-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b5a56-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b5a56-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a56-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a56-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5a56-113">See also</span></span>

- [<span data-ttu-id="b5a56-114">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="b5a56-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="b5a56-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b5a56-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
