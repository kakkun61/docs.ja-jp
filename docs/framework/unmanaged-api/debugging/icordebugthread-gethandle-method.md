---
title: ICorDebugThread::GetHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 5debd09f3ca0b4562f62913f9530cc4fa6f9110b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728031"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="bf953-102">ICorDebugThread::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="bf953-102">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="bf953-103">このスレッドのアクティブな部分の現在のハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf953-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf953-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf953-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf953-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf953-105">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="bf953-106">入出力このスレッドのアクティブな部分のハンドルである HTHREAD へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bf953-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf953-107">注釈</span><span class="sxs-lookup"><span data-stu-id="bf953-107">Remarks</span></span>  

 <span data-ttu-id="bf953-108">ハンドルは、プロセスが実行されると変化する場合があり、スレッドのさまざまな部分で異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf953-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="bf953-109">このハンドルは、デバッグ API によって所有されています。</span><span class="sxs-lookup"><span data-stu-id="bf953-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="bf953-110">使用する前に、デバッガーがそれを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf953-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf953-111">要件</span><span class="sxs-lookup"><span data-stu-id="bf953-111">Requirements</span></span>  

 <span data-ttu-id="bf953-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf953-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf953-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf953-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf953-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf953-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf953-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf953-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
