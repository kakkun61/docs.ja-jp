---
title: ICorDebugCode4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 8a373afdf41590ec44a7cbac7360719a12faa82e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720725"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="7c76a-102">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c76a-102">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="7c76a-103">デバッガーが関数のローカル変数と引数を列挙できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7c76a-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c76a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c76a-104">Methods</span></span>  
  
|<span data-ttu-id="7c76a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c76a-105">Method</span></span>|<span data-ttu-id="7c76a-106">説明</span><span class="sxs-lookup"><span data-stu-id="7c76a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c76a-107">EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="7c76a-107">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="7c76a-108">関数のローカル変数および引数に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c76a-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c76a-109">注釈</span><span class="sxs-lookup"><span data-stu-id="7c76a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c76a-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7c76a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c76a-111">要件</span><span class="sxs-lookup"><span data-stu-id="7c76a-111">Requirements</span></span>  

 <span data-ttu-id="7c76a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c76a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c76a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c76a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c76a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c76a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c76a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c76a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c76a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c76a-116">See also</span></span>

- [<span data-ttu-id="7c76a-117">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c76a-117">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="7c76a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c76a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
