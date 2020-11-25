---
title: CorDebugJITCompilerFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 0c8398b9e423414f32a391edcd5ea1c709af37f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696558"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="d763b-102">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="d763b-102">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="d763b-103">マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d763b-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d763b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d763b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d763b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d763b-105">Members</span></span>  
  
|<span data-ttu-id="d763b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d763b-106">Member</span></span>|<span data-ttu-id="d763b-107">説明</span><span class="sxs-lookup"><span data-stu-id="d763b-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="d763b-108">コンパイラがコンパイルデータを追跡し、最適化を許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d763b-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="d763b-109">コンパイラがコンパイルデータを追跡する必要があるが、最適化を無効にすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d763b-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="d763b-110">コンパイラがコンパイルデータを追跡し、最適化を無効にして、エディットコンティニュテクノロジを有効にする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d763b-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d763b-111">要件</span><span class="sxs-lookup"><span data-stu-id="d763b-111">Requirements</span></span>  

 <span data-ttu-id="d763b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d763b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d763b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d763b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d763b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d763b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d763b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d763b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d763b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d763b-116">See also</span></span>

- [<span data-ttu-id="d763b-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="d763b-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
