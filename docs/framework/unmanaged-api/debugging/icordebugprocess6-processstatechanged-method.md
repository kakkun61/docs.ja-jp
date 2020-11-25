---
title: ICorDebugProcess6::ProcessStateChanged メソッド
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 006c81e0339a00aac14fb4f83f2bc140990bd546
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732581"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="d2127-102">ICorDebugProcess6::ProcessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="d2127-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>

<span data-ttu-id="d2127-103">プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="d2127-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2127-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2127-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2127-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2127-105">Parameters</span></span>  

 `change`  
 <span data-ttu-id="d2127-106">から [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) 列挙型のメンバー</span><span class="sxs-lookup"><span data-stu-id="d2127-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2127-107">注釈</span><span class="sxs-lookup"><span data-stu-id="d2127-107">Remarks</span></span>  

 <span data-ttu-id="d2127-108">デバッガーはこのメソッドを呼び出して、プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="d2127-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2127-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2127-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2127-110">要件</span><span class="sxs-lookup"><span data-stu-id="d2127-110">Requirements</span></span>  

 <span data-ttu-id="d2127-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2127-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2127-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2127-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2127-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2127-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2127-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2127-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2127-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2127-115">See also</span></span>

- [<span data-ttu-id="d2127-116">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2127-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="d2127-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2127-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
