---
title: CorDebugMDAFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: 1bb99503481d917d41ae00a5ef73c8fa59e2a999
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696454"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="50ef0-102">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="50ef0-102">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="50ef0-103">マネージド デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="50ef0-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ef0-104">構文</span><span class="sxs-lookup"><span data-stu-id="50ef0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="50ef0-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="50ef0-105">Members</span></span>  
  
|<span data-ttu-id="50ef0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="50ef0-106">Member</span></span>|<span data-ttu-id="50ef0-107">説明</span><span class="sxs-lookup"><span data-stu-id="50ef0-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="50ef0-108">Mda が起動されてから、MDA が起動されたスレッドが遅れています。</span><span class="sxs-lookup"><span data-stu-id="50ef0-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ef0-109">注釈</span><span class="sxs-lookup"><span data-stu-id="50ef0-109">Remarks</span></span>  

 <span data-ttu-id="50ef0-110">呼び出し履歴で、MDA が最初に発生した場所が記述されなくなった場合、スレッドは *遅れ* ていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="50ef0-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="50ef0-111">これは、スレッドが終了時に無効な操作を実行したことによって発生する異常な状況です。</span><span class="sxs-lookup"><span data-stu-id="50ef0-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ef0-112">要件</span><span class="sxs-lookup"><span data-stu-id="50ef0-112">Requirements</span></span>  

 <span data-ttu-id="50ef0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50ef0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ef0-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50ef0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50ef0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50ef0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50ef0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ef0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ef0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="50ef0-117">See also</span></span>

- [<span data-ttu-id="50ef0-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="50ef0-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
