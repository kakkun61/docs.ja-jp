---
title: ICorDebugDebugEvent::GetEventKind メソッド
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 7876dc6ec5ecee52b64e54e1c42533f8348e4dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713679"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="cd60f-102">ICorDebugDebugEvent::GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="cd60f-102">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="cd60f-103">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="cd60f-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd60f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd60f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd60f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd60f-105">Parameters</span></span>  

 <span data-ttu-id="cd60f-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="cd60f-106">pDebugEventKind</span></span>  
 <span data-ttu-id="cd60f-107">イベントの種類を示す [Cordebugdebugeventkind](cordebugdebugeventkind-enumeration.md) 列挙体メンバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd60f-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd60f-108">注釈</span><span class="sxs-lookup"><span data-stu-id="cd60f-108">Remarks</span></span>  

 <span data-ttu-id="cd60f-109">`pDebugEventKind` の値に基づいて、`QueryInterface` を呼び出して、追加データを含むより正確なデバッグ イベント インターフェイスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cd60f-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd60f-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd60f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd60f-111">要件</span><span class="sxs-lookup"><span data-stu-id="cd60f-111">Requirements</span></span>  

 <span data-ttu-id="cd60f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd60f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd60f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd60f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd60f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd60f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd60f-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd60f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd60f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd60f-116">See also</span></span>

- [<span data-ttu-id="cd60f-117">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd60f-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="cd60f-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd60f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
