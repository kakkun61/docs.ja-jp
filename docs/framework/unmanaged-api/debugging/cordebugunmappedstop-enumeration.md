---
title: CorDebugUnmappedStop 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: e251bf67adcaf2bbd6565eda068d487eb0d70efd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725774"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="1f9e7-102">CorDebugUnmappedStop 列挙型</span><span class="sxs-lookup"><span data-stu-id="1f9e7-102">CorDebugUnmappedStop Enumeration</span></span>

<span data-ttu-id="1f9e7-103">ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f9e7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="1f9e7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1f9e7-105">Members</span></span>  
  
|<span data-ttu-id="1f9e7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1f9e7-106">Member</span></span>|<span data-ttu-id="1f9e7-107">説明</span><span class="sxs-lookup"><span data-stu-id="1f9e7-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="1f9e7-108">どの種類のマップされていないコードでも停止しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="1f9e7-109">プロローグコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="1f9e7-110">エピローグコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="1f9e7-111">マッピング情報のないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="1f9e7-112">プロローグ、エピローグ、非マッピング情報、またはアンマネージカテゴリに適合しない、マップされていないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="1f9e7-113">アンマネージコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-113">Stop in unmanaged code.</span></span> <span data-ttu-id="1f9e7-114">この値は、相互運用機能デバッグでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="1f9e7-115">すべての種類のマップされていないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f9e7-116">注釈</span><span class="sxs-lookup"><span data-stu-id="1f9e7-116">Remarks</span></span>  

 <span data-ttu-id="1f9e7-117">[ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)メソッドを使用して、ステッパが停止するマップされていないコードを指定するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9e7-118">要件</span><span class="sxs-lookup"><span data-stu-id="1f9e7-118">Requirements</span></span>  

 <span data-ttu-id="1f9e7-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f9e7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f9e7-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f9e7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f9e7-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f9e7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f9e7-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f9e7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9e7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f9e7-123">See also</span></span>

- [<span data-ttu-id="1f9e7-124">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="1f9e7-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
