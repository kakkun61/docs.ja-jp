---
title: ICorDebugThread::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: d3697bd8a3f32c802ab2e335f89c84efaf3e4db0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727992"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="9006b-102">ICorDebugThread::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="9006b-102">ICorDebugThread::GetProcess Method</span></span>

<span data-ttu-id="9006b-103">このコンポーネントがパートを形成するプロセスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9006b-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9006b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9006b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9006b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9006b-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="9006b-106">入出力プロセスを表す、のプロセスインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9006b-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9006b-107">要件</span><span class="sxs-lookup"><span data-stu-id="9006b-107">Requirements</span></span>  

 <span data-ttu-id="9006b-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9006b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9006b-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9006b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9006b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9006b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9006b-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9006b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
