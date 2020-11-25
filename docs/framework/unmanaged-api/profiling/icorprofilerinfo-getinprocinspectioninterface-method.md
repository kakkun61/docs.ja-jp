---
title: ICorProfilerInfo::GetInprocInspectionInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: cc8bdfb1e46e5304227a40f869856f07e1f90bed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707491"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="8f20c-102">ICorProfilerInfo::GetInprocInspectionInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="8f20c-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>

<span data-ttu-id="8f20c-103">"いいプロセス" インターフェイスに対してクエリを実行できるオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="8f20c-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="8f20c-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="8f20c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f20c-105">構文</span><span class="sxs-lookup"><span data-stu-id="8f20c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f20c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f20c-106">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="8f20c-107">インターフェイスに対してクエリを実行できる[out](/cpp/atl/iunknown)オブジェクト `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="8f20c-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f20c-108">注釈</span><span class="sxs-lookup"><span data-stu-id="8f20c-108">Remarks</span></span>  

 <span data-ttu-id="8f20c-109">共通言語ランタイム (CLR) デバッグ API でサポートされている .NET Framework バージョン1.0 では、プロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="8f20c-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="8f20c-110">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="8f20c-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="8f20c-111">お客様からのフィードバックの結果として、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="8f20c-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f20c-112">要件</span><span class="sxs-lookup"><span data-stu-id="8f20c-112">Requirements</span></span>  

 <span data-ttu-id="8f20c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f20c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f20c-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f20c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f20c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f20c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f20c-116">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="8f20c-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f20c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f20c-117">See also</span></span>

- [<span data-ttu-id="8f20c-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f20c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
