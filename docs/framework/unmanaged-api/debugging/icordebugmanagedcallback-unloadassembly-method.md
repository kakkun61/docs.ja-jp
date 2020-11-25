---
title: ICorDebugManagedCallback::UnloadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: e89b425afb63de8ef496fe545873ce33e5ff828c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724014"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="c8939-102">ICorDebugManagedCallback::UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c8939-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>

<span data-ttu-id="c8939-103">共通言語ランタイムアセンブリがアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c8939-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8939-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8939-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8939-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8939-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="c8939-106">からアセンブリが格納されているアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8939-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="c8939-107">からアセンブリを表す、オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8939-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8939-108">注釈</span><span class="sxs-lookup"><span data-stu-id="c8939-108">Remarks</span></span>  

 <span data-ttu-id="c8939-109">このコールバックの後にアセンブリを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c8939-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8939-110">要件</span><span class="sxs-lookup"><span data-stu-id="c8939-110">Requirements</span></span>  

 <span data-ttu-id="c8939-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8939-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8939-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8939-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8939-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8939-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8939-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8939-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8939-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8939-115">See also</span></span>

- [<span data-ttu-id="c8939-116">LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c8939-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="c8939-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8939-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
