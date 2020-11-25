---
title: ICorDebugRegisterSet2::SetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: 53660a5b10858632dffc5b31c290e9cb98d634c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712301"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="297e3-102">ICorDebugRegisterSet2::SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="297e3-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>

<span data-ttu-id="297e3-103">`SetRegisters` は .NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="297e3-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="297e3-104">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="297e3-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="297e3-105">「いいね!: [: setip](icordebugilframe-setip-method.md) 」や「いいね!: [: setip](icordebugnativeframe-setip-method.md)」などの上位レベルの操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="297e3-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="297e3-106">構文</span><span class="sxs-lookup"><span data-stu-id="297e3-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="297e3-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="297e3-107">Requirements</span></span>  

 <span data-ttu-id="297e3-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="297e3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="297e3-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="297e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="297e3-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="297e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="297e3-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="297e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297e3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="297e3-112">See also</span></span>

- [<span data-ttu-id="297e3-113">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="297e3-113">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="297e3-114">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="297e3-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
