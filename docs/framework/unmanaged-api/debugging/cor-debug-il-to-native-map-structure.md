---
title: COR_DEBUG_IL_TO_NATIVE_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: 61544d0dfe876f35fdfbe5afa945fad0620c0eb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726653"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="39bd3-102">COR_DEBUG_IL_TO_NATIVE_MAP 構造体</span><span class="sxs-lookup"><span data-stu-id="39bd3-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>

<span data-ttu-id="39bd3-103">Microsoft intermediate language (MSIL) コードをネイティブ コードにマップするために使用するオフセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="39bd3-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bd3-104">構文</span><span class="sxs-lookup"><span data-stu-id="39bd3-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="39bd3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="39bd3-105">Members</span></span>  
  
|<span data-ttu-id="39bd3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="39bd3-106">Member</span></span>|<span data-ttu-id="39bd3-107">説明</span><span class="sxs-lookup"><span data-stu-id="39bd3-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="39bd3-108">MSIL コードのオフセット。</span><span class="sxs-lookup"><span data-stu-id="39bd3-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="39bd3-109">ネイティブコードの開始位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="39bd3-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="39bd3-110">ネイティブコードの末尾のオフセット。</span><span class="sxs-lookup"><span data-stu-id="39bd3-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39bd3-111">要件</span><span class="sxs-lookup"><span data-stu-id="39bd3-111">Requirements</span></span>  

 <span data-ttu-id="39bd3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39bd3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bd3-113">**ヘッダー:** Corprof.idl、CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="39bd3-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="39bd3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39bd3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39bd3-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39bd3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bd3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="39bd3-116">See also</span></span>

- [<span data-ttu-id="39bd3-117">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="39bd3-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="39bd3-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="39bd3-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="39bd3-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="39bd3-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="39bd3-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="39bd3-120">Debugging</span></span>](index.md)
