---
title: ICorProfilerCallback::AppDomainCreationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 901546c80c3bee32afddfa8e8cffbd2b679bc43b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685395"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="8a2da-102">ICorProfilerCallback::AppDomainCreationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="8a2da-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="8a2da-103">アプリケーションドメインが作成中であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8a2da-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a2da-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a2da-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a2da-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a2da-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="8a2da-106">\[in] 作成されるドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="8a2da-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8a2da-107">注釈</span><span class="sxs-lookup"><span data-stu-id="8a2da-107">Remarks</span></span>  

 <span data-ttu-id="8a2da-108">ID は、 [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="8a2da-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a2da-109">要件</span><span class="sxs-lookup"><span data-stu-id="8a2da-109">Requirements</span></span>  

 <span data-ttu-id="8a2da-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a2da-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a2da-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a2da-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a2da-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a2da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a2da-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a2da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a2da-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a2da-114">See also</span></span>

- [<span data-ttu-id="8a2da-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a2da-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
