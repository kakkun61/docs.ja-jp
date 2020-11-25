---
title: ICorDebugBoxValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: 6d58ae048382a78c422703d5c6caeb3bbc739849
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723169"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="734ca-102">ICorDebugBoxValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="734ca-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="734ca-103">ボックス化された値クラスオブジェクトを表す "" "のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="734ca-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="734ca-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="734ca-104">Methods</span></span>  
  
|<span data-ttu-id="734ca-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="734ca-105">Method</span></span>|<span data-ttu-id="734ca-106">説明</span><span class="sxs-lookup"><span data-stu-id="734ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="734ca-107">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="734ca-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="734ca-108">ボックス化された "の" のインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="734ca-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="734ca-109">注釈</span><span class="sxs-lookup"><span data-stu-id="734ca-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="734ca-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="734ca-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734ca-111">要件</span><span class="sxs-lookup"><span data-stu-id="734ca-111">Requirements</span></span>  

 <span data-ttu-id="734ca-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="734ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="734ca-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="734ca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="734ca-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="734ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="734ca-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="734ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734ca-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="734ca-116">See also</span></span>

- [<span data-ttu-id="734ca-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="734ca-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
