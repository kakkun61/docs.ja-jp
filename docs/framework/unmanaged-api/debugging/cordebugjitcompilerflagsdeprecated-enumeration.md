---
title: CorDebugJITCompilerFlagsDeprecated 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: 8797f77388bf4992dfb69191ce8a844a9b7fdb8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696441"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="4dddb-102">CorDebugJITCompilerFlagsDeprecated 列挙型</span><span class="sxs-lookup"><span data-stu-id="4dddb-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>

<span data-ttu-id="4dddb-103">この列挙型は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="4dddb-103">This enumeration is obsolete.</span></span> <span data-ttu-id="4dddb-104">代わりに、 `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体のメンバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="4dddb-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dddb-105">構文</span><span class="sxs-lookup"><span data-stu-id="4dddb-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="4dddb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4dddb-106">Members</span></span>  
  
|<span data-ttu-id="4dddb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4dddb-107">Member</span></span>|<span data-ttu-id="4dddb-108">説明</span><span class="sxs-lookup"><span data-stu-id="4dddb-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="4dddb-109">代わりに、`CORDEBUG_JIT_DEFAULT` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4dddb-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4dddb-110">要件</span><span class="sxs-lookup"><span data-stu-id="4dddb-110">Requirements</span></span>  

 <span data-ttu-id="4dddb-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dddb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dddb-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dddb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dddb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dddb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dddb-114">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="4dddb-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dddb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dddb-115">See also</span></span>

- [<span data-ttu-id="4dddb-116">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4dddb-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
