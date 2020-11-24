---
title: ICorProfilerCallback::AppDomainShutdownFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: ddb2d6eeb75a118a12f681b354f6feccd1231c64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685386"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="366a8-102">ICorProfilerCallback::AppDomainShutdownFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="366a8-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="366a8-103">アプリケーションドメインがプロセスからアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="366a8-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="366a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="366a8-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="366a8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="366a8-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="366a8-106">\[in] は、アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="366a8-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="366a8-107">\[in] アプリケーションドメインが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="366a8-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="366a8-108">注釈</span><span class="sxs-lookup"><span data-stu-id="366a8-108">Remarks</span></span>  

 <span data-ttu-id="366a8-109">`appDomainId` [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="366a8-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="366a8-110">アプリケーションドメインのアンロードの一部は、コールバック後に続行される場合があり `AppDomainCreationFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="366a8-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="366a8-111">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="366a8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="366a8-112">ただし、の成功 HRESULT は、 `hrStatus` アプリケーションドメインのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="366a8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="366a8-113">要件</span><span class="sxs-lookup"><span data-stu-id="366a8-113">Requirements</span></span>  

 <span data-ttu-id="366a8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="366a8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366a8-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="366a8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="366a8-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="366a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="366a8-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366a8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="366a8-118">See also</span></span>

- [<span data-ttu-id="366a8-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="366a8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
