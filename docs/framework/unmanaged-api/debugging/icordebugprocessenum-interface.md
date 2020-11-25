---
title: ICorDebugProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
ms.openlocfilehash: 31f26a40294857701b151cd2fce35b061da28238
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732529"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="c3a57-102">ICorDebugProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3a57-102">ICorDebugProcessEnum Interface</span></span>

<span data-ttu-id="c3a57-103">ICorDebugEnum メソッドを実装し、を処理する配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="c3a57-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3a57-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c3a57-104">Methods</span></span>  
  
|<span data-ttu-id="c3a57-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c3a57-105">Method</span></span>|<span data-ttu-id="c3a57-106">説明</span><span class="sxs-lookup"><span data-stu-id="c3a57-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3a57-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="c3a57-107">Next Method</span></span>](icordebugprocessenum-next-method.md)|<span data-ttu-id="c3a57-108">現在の位置から開始して、指定した数の `ICorDebugProcess` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="c3a57-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a57-109">注釈</span><span class="sxs-lookup"><span data-stu-id="c3a57-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3a57-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c3a57-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a57-111">要件</span><span class="sxs-lookup"><span data-stu-id="c3a57-111">Requirements</span></span>  

 <span data-ttu-id="c3a57-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3a57-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a57-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3a57-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3a57-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a57-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a57-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a57-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3a57-116">See also</span></span>

- [<span data-ttu-id="c3a57-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3a57-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
