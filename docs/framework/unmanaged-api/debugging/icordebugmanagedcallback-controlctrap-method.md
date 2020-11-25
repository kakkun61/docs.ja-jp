---
title: ICorDebugManagedCallback::ControlCTrap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 0c38269ea4d730d8f3f9ba5d2c5d8f0edf6d7d45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731840"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="7b028-102">ICorDebugManagedCallback::ControlCTrap メソッド</span><span class="sxs-lookup"><span data-stu-id="7b028-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="7b028-103">デバッグ対象のプロセスで CTRL + C がトラップされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7b028-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b028-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b028-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b028-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b028-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="7b028-106">からCTRL + C キーがトラップされるプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b028-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b028-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="7b028-107">Return Value</span></span>  
  
|<span data-ttu-id="7b028-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b028-108">HRESULT</span></span>|<span data-ttu-id="7b028-109">説明</span><span class="sxs-lookup"><span data-stu-id="7b028-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b028-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b028-110">S_OK</span></span>|<span data-ttu-id="7b028-111">デバッガーは CTRL + C トラップを処理します。</span><span class="sxs-lookup"><span data-stu-id="7b028-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="7b028-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7b028-112">S_FALSE</span></span>|<span data-ttu-id="7b028-113">デバッガーは CTRL + C トラップを処理しません。</span><span class="sxs-lookup"><span data-stu-id="7b028-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b028-114">注釈</span><span class="sxs-lookup"><span data-stu-id="7b028-114">Remarks</span></span>  

 <span data-ttu-id="7b028-115">プロセス内のすべてのアプリケーションドメインがこのコールバックに対して停止されています。</span><span class="sxs-lookup"><span data-stu-id="7b028-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b028-116">要件</span><span class="sxs-lookup"><span data-stu-id="7b028-116">Requirements</span></span>  

 <span data-ttu-id="7b028-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b028-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b028-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b028-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b028-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b028-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b028-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b028-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b028-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b028-121">See also</span></span>

- [<span data-ttu-id="7b028-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b028-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
