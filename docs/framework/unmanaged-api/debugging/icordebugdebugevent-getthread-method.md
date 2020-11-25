---
title: ICorDebugDebugEvent::GetThread メソッド
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: ca6aba7897d9e97743d29db49bd058e140f84e6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713588"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="ef6c6-102">ICorDebugDebugEvent::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="ef6c6-102">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="ef6c6-103">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="ef6c6-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef6c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef6c6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef6c6-105">Parameters</span></span>  

 <span data-ttu-id="ef6c6-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="ef6c6-106">ppThread</span></span>  
 <span data-ttu-id="ef6c6-107">[出力] イベントが発生したスレッドを表す ICorDebugThread オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef6c6-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef6c6-108">注釈</span><span class="sxs-lookup"><span data-stu-id="ef6c6-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef6c6-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef6c6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef6c6-110">要件</span><span class="sxs-lookup"><span data-stu-id="ef6c6-110">Requirements</span></span>  

 <span data-ttu-id="ef6c6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef6c6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef6c6-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef6c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef6c6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef6c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef6c6-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef6c6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6c6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef6c6-115">See also</span></span>

- [<span data-ttu-id="ef6c6-116">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef6c6-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="ef6c6-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef6c6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
