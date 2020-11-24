---
title: ICorDebugThread::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: dcaa5adc41a9e451b123b088dd900f01d9161689
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688277"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="e0303-102">ICorDebugThread::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="e0303-102">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="e0303-103">この ICorDebugStepper スレッドのアクティブなフレームをステップ実行できるようにする、オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0303-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0303-104">構文</span><span class="sxs-lookup"><span data-stu-id="e0303-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0303-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0303-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="e0303-106">入出力 `ICorDebugStepper` このスレッドのアクティブフレームのステップ実行を可能にするオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e0303-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0303-107">注釈</span><span class="sxs-lookup"><span data-stu-id="e0303-107">Remarks</span></span>  

 <span data-ttu-id="e0303-108">アクティブなフレームはアンマネージコードである場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0303-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="e0303-109">`ICorDebugStepper`実際のステップ実行には、インターフェイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0303-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0303-110">要件</span><span class="sxs-lookup"><span data-stu-id="e0303-110">Requirements</span></span>  

 <span data-ttu-id="e0303-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0303-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0303-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0303-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0303-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0303-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0303-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0303-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
