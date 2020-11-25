---
title: ICorDebugModuleEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: 08d16393a04888cd3f1a03fa209a1fceac28520b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724755"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="40044-102">ICorDebugModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40044-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="40044-103">ICorDebugEnum メソッドを実装し、モジュール配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="40044-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40044-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="40044-104">Methods</span></span>  
  
|<span data-ttu-id="40044-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="40044-105">Method</span></span>|<span data-ttu-id="40044-106">説明</span><span class="sxs-lookup"><span data-stu-id="40044-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40044-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="40044-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="40044-108">現在の位置から開始して、指定した数の `ICorDebugModule` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="40044-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40044-109">注釈</span><span class="sxs-lookup"><span data-stu-id="40044-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40044-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="40044-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40044-111">要件</span><span class="sxs-lookup"><span data-stu-id="40044-111">Requirements</span></span>  

 <span data-ttu-id="40044-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40044-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40044-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40044-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40044-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40044-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40044-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40044-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40044-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="40044-116">See also</span></span>

- [<span data-ttu-id="40044-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="40044-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
