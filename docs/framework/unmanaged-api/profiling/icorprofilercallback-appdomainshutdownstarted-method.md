---
title: ICorProfilerCallback::AppDomainShutdownStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: cb0b763059c787b8f3e93e6c46b0e7fb2f8f8b2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718463"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="52f5b-102">ICorProfilerCallback::AppDomainShutdownStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="52f5b-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="52f5b-103">アプリケーションドメインがプロセスからアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="52f5b-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="52f5b-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52f5b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52f5b-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="52f5b-106">\[in] は、アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="52f5b-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="52f5b-107">注釈</span><span class="sxs-lookup"><span data-stu-id="52f5b-107">Remarks</span></span>  

 <span data-ttu-id="52f5b-108">の値は、 `appDomainId` メソッドが返された後の情報要求に対して有効ではありません `AppDomainShutdownStarted` 。これは、このアプリケーションドメインに関する情報を取得する最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="52f5b-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f5b-109">要件</span><span class="sxs-lookup"><span data-stu-id="52f5b-109">Requirements</span></span>  

 <span data-ttu-id="52f5b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52f5b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f5b-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52f5b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52f5b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f5b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f5b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f5b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="52f5b-114">See also</span></span>

- [<span data-ttu-id="52f5b-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52f5b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
