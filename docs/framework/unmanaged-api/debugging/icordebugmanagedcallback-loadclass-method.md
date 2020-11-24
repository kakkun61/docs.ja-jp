---
title: ICorDebugManagedCallback::LoadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 6f1672d40cd495d3ec099abc703639cf52460703
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679664"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="49d92-102">ICorDebugManagedCallback::LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="49d92-102">ICorDebugManagedCallback::LoadClass Method</span></span>

<span data-ttu-id="49d92-103">クラスが読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="49d92-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d92-104">構文</span><span class="sxs-lookup"><span data-stu-id="49d92-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d92-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49d92-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="49d92-106">からクラスが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="49d92-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="49d92-107">からクラスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="49d92-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d92-108">注釈</span><span class="sxs-lookup"><span data-stu-id="49d92-108">Remarks</span></span>  

 <span data-ttu-id="49d92-109">このコールバックは、クラスを含むモジュールに対してクラスの読み込みが有効になっている場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="49d92-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="49d92-110">動的モジュールでは、クラスの読み込みが常に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="49d92-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="49d92-111">`LoadClass`コールバックは、動的モジュールで新しく生成されたクラスにブレークポイントをバインドするための適切な時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="49d92-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d92-112">要件</span><span class="sxs-lookup"><span data-stu-id="49d92-112">Requirements</span></span>  

 <span data-ttu-id="49d92-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49d92-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d92-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49d92-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49d92-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49d92-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49d92-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d92-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d92-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="49d92-117">See also</span></span>

- [<span data-ttu-id="49d92-118">UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="49d92-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="49d92-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49d92-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
