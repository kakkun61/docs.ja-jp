---
title: ICorProfilerCallback::AppDomainCreationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 688b9975cc68463de066e5225c6ab1e04cbb5337
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685376"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="45b9a-102">ICorProfilerCallback::AppDomainCreationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="45b9a-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="45b9a-103">アプリケーションドメインが作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="45b9a-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b9a-104">構文</span><span class="sxs-lookup"><span data-stu-id="45b9a-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="45b9a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45b9a-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="45b9a-106">\[in] は、作成されたドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="45b9a-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="45b9a-107">\[in] アプリケーションドメインの作成が正常に完了したかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="45b9a-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="45b9a-108">注釈</span><span class="sxs-lookup"><span data-stu-id="45b9a-108">Remarks</span></span>  

 <span data-ttu-id="45b9a-109">アプリケーション ID は、メソッドが呼び出されるまで、情報要求に対して有効ではありません `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="45b9a-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="45b9a-110">アプリケーションドメインの読み込みの一部は、コールバック後も続行される場合があり `AppDomainCreationFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="45b9a-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="45b9a-111">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="45b9a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="45b9a-112">ただし、の成功 HRESULT は、 `hrStatus` アプリケーションドメインの作成の最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="45b9a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45b9a-113">要件</span><span class="sxs-lookup"><span data-stu-id="45b9a-113">Requirements</span></span>  

 <span data-ttu-id="45b9a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b9a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45b9a-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45b9a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45b9a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45b9a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45b9a-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45b9a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b9a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="45b9a-118">See also</span></span>

- [<span data-ttu-id="45b9a-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45b9a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
