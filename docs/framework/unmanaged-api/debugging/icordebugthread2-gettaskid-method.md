---
title: ICorDebugThread2::GetTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 9b17a179745af65bde05527bd0157f3ce06c12c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678663"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="8e78c-102">ICorDebugThread2::GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="8e78c-102">ICorDebugThread2::GetTaskID Method</span></span>

<span data-ttu-id="8e78c-103">このスレッドで実行されているタスクの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8e78c-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e78c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8e78c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e78c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8e78c-105">Parameters</span></span>  

 `pTaskId`  
 <span data-ttu-id="8e78c-106">入出力この ICorDebugThread2 オブジェクトによって表されるスレッド上で実行されているタスクの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8e78c-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e78c-107">注釈</span><span class="sxs-lookup"><span data-stu-id="8e78c-107">Remarks</span></span>  

 <span data-ttu-id="8e78c-108">スレッドが接続に関連付けられている場合にのみ、スレッドでタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e78c-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="8e78c-109">`GetTaskID``pTaskId`スレッドが接続に関連付けられていない場合は、で0を返します。</span><span class="sxs-lookup"><span data-stu-id="8e78c-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e78c-110">要件</span><span class="sxs-lookup"><span data-stu-id="8e78c-110">Requirements</span></span>  

 <span data-ttu-id="8e78c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e78c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e78c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e78c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e78c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e78c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e78c-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e78c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
