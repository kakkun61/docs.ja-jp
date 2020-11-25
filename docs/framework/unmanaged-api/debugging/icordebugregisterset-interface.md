---
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712379"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="1b7a2-102">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b7a2-102">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="1b7a2-103">現在コードを実行しているコンピューターで使用できるレジスタのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b7a2-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-104">Methods</span></span>  
  
|<span data-ttu-id="1b7a2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-105">Method</span></span>|<span data-ttu-id="1b7a2-106">説明</span><span class="sxs-lookup"><span data-stu-id="1b7a2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b7a2-107">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="1b7a2-108">ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="1b7a2-109">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="1b7a2-110">現在使用できるレジスタを示すビットマスクを取得し `ICorDebugRegisterSet` ます。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="1b7a2-111">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="1b7a2-112">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="1b7a2-113">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="1b7a2-114">.NET Framework バージョン2.0 には実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="1b7a2-115">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="1b7a2-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="1b7a2-116">.NET Framework 2.0 には実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b7a2-117">注釈</span><span class="sxs-lookup"><span data-stu-id="1b7a2-117">Remarks</span></span>  

 <span data-ttu-id="1b7a2-118">インターフェイスでは、 `ICorDebugRegisterSet` 32 ビットレジスタのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="1b7a2-119">追加のレジスタを必要とする IA-64 などのプラットフォームで [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b7a2-120">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b7a2-121">要件</span><span class="sxs-lookup"><span data-stu-id="1b7a2-121">Requirements</span></span>  

 <span data-ttu-id="1b7a2-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b7a2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b7a2-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b7a2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b7a2-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b7a2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b7a2-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b7a2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7a2-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b7a2-126">See also</span></span>

- [<span data-ttu-id="1b7a2-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b7a2-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1b7a2-128">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b7a2-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
