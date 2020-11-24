---
title: ICorDebugController::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679807"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="359b2-102">ICorDebugController::Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="359b2-102">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="359b2-103">指定された終了コードを使用してプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="359b2-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="359b2-104">このメソッドは、Win32 関数のラッパーです `TerminateProcess` 。</span><span class="sxs-lookup"><span data-stu-id="359b2-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="359b2-105">したがって、は、 `Terminate` Win32 関数が使用するのと同じ方法で終了コードを使用し `TerminateProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="359b2-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359b2-106">構文</span><span class="sxs-lookup"><span data-stu-id="359b2-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="359b2-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="359b2-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="359b2-108">から終了コードを表す数値。</span><span class="sxs-lookup"><span data-stu-id="359b2-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="359b2-109">有効な数値は、Winbase. h で定義されています。</span><span class="sxs-lookup"><span data-stu-id="359b2-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="359b2-110">注釈</span><span class="sxs-lookup"><span data-stu-id="359b2-110">Remarks</span></span>  

 <span data-ttu-id="359b2-111">が呼び出されたときにプロセスが停止された場合は、このプロセスを続行 `Terminate` する必要があります。これを行うに[は、](icordebugcontroller-continue-method.md)デバッガーが、"ExitProcess" または " [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) [managedcallback:: exitappdomain](icordebugmanagedcallback-exitappdomain-method.md) callback" を使用して終了の確認を受け取るようにします。</span><span class="sxs-lookup"><span data-stu-id="359b2-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="359b2-112">このメソッドは、アプリケーションドメインによって実装されていません。</span><span class="sxs-lookup"><span data-stu-id="359b2-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="359b2-113">つまり、レベルでは実装されていません <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="359b2-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359b2-114">要件</span><span class="sxs-lookup"><span data-stu-id="359b2-114">Requirements</span></span>  

 <span data-ttu-id="359b2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="359b2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359b2-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="359b2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="359b2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="359b2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="359b2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359b2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="359b2-119">See also</span></span>
