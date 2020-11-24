---
title: ICorProfilerInfo::BeginInprocDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: 3f56c3faa10eb05896936a37b0094797b0b6e2b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669173"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="1079d-102">ICorProfilerInfo::BeginInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="1079d-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>

<span data-ttu-id="1079d-103">インプロセスデバッグサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="1079d-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="1079d-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="1079d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1079d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1079d-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1079d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1079d-106">Parameters</span></span>  

 `fThisThreadOnly`  
 <span data-ttu-id="1079d-107">から現在のスレッドのみのデバッグサポートを初期化するには、この値をに設定し `true` ます。 `false` すべてのスレッドのデバッグサポートを初期化するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="1079d-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="1079d-108">入出力デバッグセッションを識別する戻り値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1079d-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1079d-109">注釈</span><span class="sxs-lookup"><span data-stu-id="1079d-109">Remarks</span></span>  

 <span data-ttu-id="1079d-110">CLR デバッグサービスでは、.NET Framework バージョン1.0 および1.1 でサポートされているプロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="1079d-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="1079d-111">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="1079d-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="1079d-112">ただし、お客様からのフィードバックにより、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="1079d-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1079d-113">要件</span><span class="sxs-lookup"><span data-stu-id="1079d-113">Requirements</span></span>  

 <span data-ttu-id="1079d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1079d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1079d-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1079d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1079d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1079d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1079d-117">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="1079d-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1079d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1079d-118">See also</span></span>

- [<span data-ttu-id="1079d-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1079d-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
