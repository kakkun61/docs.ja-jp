---
title: ICorDebugExceptionDebugEvent::GetStackPointer メソッド
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 46906e7d3ce7f257eb776e50dc6097946eb77d1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697403"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="1b6a6-102">ICorDebugExceptionDebugEvent::GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="1b6a6-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>

<span data-ttu-id="1b6a6-103">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b6a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b6a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b6a6-105">Parameters</span></span>  

 `pStackPointer`  
 <span data-ttu-id="1b6a6-106">[out] この例外デバッグ イベントのスタック ポインターのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="1b6a6-107">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b6a6-108">注釈</span><span class="sxs-lookup"><span data-stu-id="1b6a6-108">Remarks</span></span>  

 <span data-ttu-id="1b6a6-109">このスタック ポインターの意味は、次の表に示すように、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="1b6a6-110">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="1b6a6-110">Event type</span></span>|<span data-ttu-id="1b6a6-111">`pStackPointer` 値の意味</span><span class="sxs-lookup"><span data-stu-id="1b6a6-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="1b6a6-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1b6a6-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1b6a6-113">例外をスローしたフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="1b6a6-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1b6a6-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1b6a6-115">スローされた例外の位置に最も近いユーザー コード フレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="1b6a6-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="1b6a6-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1b6a6-117">catch ハンドラーを含むフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="1b6a6-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="1b6a6-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1b6a6-119">`pStackPointer` が **null** です。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1b6a6-120">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="1b6a6-121">イベントの種類は、[テキスト形式の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドから取得できます。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b6a6-122">要件</span><span class="sxs-lookup"><span data-stu-id="1b6a6-122">Requirements</span></span>  

 <span data-ttu-id="1b6a6-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6a6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b6a6-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b6a6-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b6a6-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b6a6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b6a6-126">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b6a6-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6a6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b6a6-127">See also</span></span>

- [<span data-ttu-id="1b6a6-128">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b6a6-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="1b6a6-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b6a6-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
