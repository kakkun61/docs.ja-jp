---
title: ICorDebugMutableDataTarget インターフェイス
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: cd22707832504ca2f08299872bc39bca2af782bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709350"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="c4e0e-102">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4e0e-102">ICorDebugMutableDataTarget Interface</span></span>

<span data-ttu-id="c4e0e-103">変更可能なデータターゲットをサポートするために、の機能を拡張[します。](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="c4e0e-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4e0e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4e0e-104">Methods</span></span>  
  
|<span data-ttu-id="c4e0e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4e0e-105">Method</span></span>|<span data-ttu-id="c4e0e-106">説明</span><span class="sxs-lookup"><span data-stu-id="c4e0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4e0e-107">ContinueStatusChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="c4e0e-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="c4e0e-108">指定されたスレッド上の未処理のデバッグ イベントの継続状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="c4e0e-109">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="c4e0e-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="c4e0e-110">スレッドのコンテキスト (レジスタの値) を設定します。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="c4e0e-111">WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="c4e0e-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="c4e0e-112">ターゲット プロセスのアドレス空間にメモリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e0e-113">注釈</span><span class="sxs-lookup"><span data-stu-id="c4e0e-113">Remarks</span></span>  

 <span data-ttu-id="c4e0e-114">このモジュール [へのこの](icordebugdatatarget-interface.md) 拡張機能は、ターゲットプロセスを変更する (たとえば、ライブによる干渉デバッグを実行する) デバッグツールで実装できます。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="c4e0e-115">これらのメソッドすべては省略可能です。つまり、このインターフェイスを実装しない場合や、これらのメソッドに対する呼び出しに失敗する場合にも、コア検査に基づくデバッグ機能は失われません。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="c4e0e-116">これらのメソッドからの失敗 `HRESULT` すべては、ICorDebug メソッドからの `HRESULT` として伝達されます。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="c4e0e-117">1 回の ICorDebug メソッド呼び出しによって複数の変更が行われる可能性があること、および関連する変更をトランザクションごとに適用するメカニズムがないこと (すべてに適用するか、まったく適用しないかのどちらか) に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="c4e0e-118">つまり、(同じ ICorDebug 呼び出しの) 他のユーザーが正常に完了した後に変更を失敗すると、ターゲット プロセスは一貫性のない状態のままになり、デバッグが信頼性に欠ける結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e0e-119">要件</span><span class="sxs-lookup"><span data-stu-id="c4e0e-119">Requirements</span></span>  

 <span data-ttu-id="c4e0e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e0e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e0e-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4e0e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4e0e-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4e0e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4e0e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e0e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e0e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4e0e-124">See also</span></span>

- [<span data-ttu-id="c4e0e-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4e0e-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c4e0e-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c4e0e-126">Debugging</span></span>](index.md)
