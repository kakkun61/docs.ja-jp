---
title: ICorDebugRegisterSet2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712324"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="4b3f0-102">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b3f0-102">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="4b3f0-103">64を超えるレジスタを持つハードウェアプラットフォームに対し [て、の](icordebugregisterset-interface.md) 機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b3f0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f0-104">Methods</span></span>  
  
|<span data-ttu-id="4b3f0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f0-105">Method</span></span>|<span data-ttu-id="4b3f0-106">説明</span><span class="sxs-lookup"><span data-stu-id="4b3f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b3f0-107">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f0-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="4b3f0-108">ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="4b3f0-109">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f0-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="4b3f0-110">使用できるレジスタのビットマップを提供するバイト配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="4b3f0-111">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f0-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="4b3f0-112">.NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b3f0-113">注釈</span><span class="sxs-lookup"><span data-stu-id="4b3f0-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b3f0-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3f0-115">要件</span><span class="sxs-lookup"><span data-stu-id="4b3f0-115">Requirements</span></span>  

 <span data-ttu-id="4b3f0-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b3f0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3f0-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b3f0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b3f0-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b3f0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b3f0-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3f0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3f0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b3f0-120">See also</span></span>

- [<span data-ttu-id="4b3f0-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b3f0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4b3f0-122">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b3f0-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
