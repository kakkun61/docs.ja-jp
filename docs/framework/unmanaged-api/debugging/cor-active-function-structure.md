---
title: COR_ACTIVE_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727420"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="584b9-102">COR_ACTIVE_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="584b9-102">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="584b9-103">スレッドのフレームで現在アクティブな機能に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="584b9-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="584b9-104">この構造体は、 [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="584b9-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="584b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="584b9-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="584b9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="584b9-106">Members</span></span>  
  
|<span data-ttu-id="584b9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="584b9-107">Member</span></span>|<span data-ttu-id="584b9-108">説明</span><span class="sxs-lookup"><span data-stu-id="584b9-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="584b9-109">フィールドのアプリケーションドメイン所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="584b9-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="584b9-110">フィールドのモジュール所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="584b9-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="584b9-111">フィールドの関数所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="584b9-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="584b9-112">フレームの MSIL (Microsoft 中間言語) オフセット。</span><span class="sxs-lookup"><span data-stu-id="584b9-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="584b9-113">将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="584b9-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="584b9-114">要件</span><span class="sxs-lookup"><span data-stu-id="584b9-114">Requirements</span></span>  

 <span data-ttu-id="584b9-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="584b9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="584b9-116">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="584b9-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="584b9-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="584b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="584b9-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="584b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584b9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="584b9-119">See also</span></span>

- [<span data-ttu-id="584b9-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="584b9-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="584b9-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="584b9-121">Debugging</span></span>](index.md)
