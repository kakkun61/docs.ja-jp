---
title: ICorDebugRegisterSet::SetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 4be5d2d9d891010e68cd6eb96cd4456e04d8c8b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712288"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="fe6a4-102">ICorDebugRegisterSet::SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="fe6a4-102">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="fe6a4-103">`SetRegisters` は .NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="fe6a4-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fe6a4-104">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="fe6a4-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe6a4-105">「いいね!: [: setip](icordebugilframe-setip-method.md) 」や「いいね!: [: setip](icordebugnativeframe-setip-method.md)」などの上位レベルの操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe6a4-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6a4-106">構文</span><span class="sxs-lookup"><span data-stu-id="fe6a4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fe6a4-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="fe6a4-107">Requirements</span></span>  

 <span data-ttu-id="fe6a4-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6a4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe6a4-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe6a4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe6a4-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe6a4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe6a4-111">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="fe6a4-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6a4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe6a4-112">See also</span></span>

- [<span data-ttu-id="fe6a4-113">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe6a4-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="fe6a4-114">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe6a4-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
