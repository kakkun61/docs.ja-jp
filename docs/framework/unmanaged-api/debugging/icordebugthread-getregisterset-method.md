---
title: ICorDebugThread::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: 7d3575909f54c8d676c9fd4246e6eac4a8a0ea1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727979"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="c7e41-102">ICorDebugThread::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="c7e41-102">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="c7e41-103">このコンポーネントオブジェクトのアクティブな部分に関連付けられているレジスタセットへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c7e41-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e41-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7e41-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e41-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7e41-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="c7e41-106">入出力このスレッドのアクティブな部分のレジスタセットを [表す、の](icordebugregisterset-interface.md) オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c7e41-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e41-107">要件</span><span class="sxs-lookup"><span data-stu-id="c7e41-107">Requirements</span></span>  

 <span data-ttu-id="c7e41-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e41-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e41-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7e41-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7e41-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7e41-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7e41-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e41-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
