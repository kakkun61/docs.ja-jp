---
title: ICorProfilerInfo::GetAppDomainInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 62055a98197f5f8bd4cfc02e99891b83ef6341e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680299"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="ec5d3-102">ICorProfilerInfo::GetAppDomainInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="ec5d3-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>

<span data-ttu-id="ec5d3-103">アプリケーション ドメイン ID を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-103">Accepts an application domain ID.</span></span> <span data-ttu-id="ec5d3-104">アプリケーション ドメインの名前と、そのアプリケーション ドメインを含むプロセスの ID を返します。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5d3-105">構文</span><span class="sxs-lookup"><span data-stu-id="ec5d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec5d3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec5d3-106">Parameters</span></span>  

 `appDomainId`  
 <span data-ttu-id="ec5d3-107">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ec5d3-108">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ec5d3-109">[out] アプリケーション ドメイン名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ec5d3-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="ec5d3-111">このメソッドから制御が戻ると、`szName` にはアプリケーション ドメイン名の全部または一部が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="ec5d3-112">[out] アプリケーション ドメインを含むプロセスの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec5d3-113">注釈</span><span class="sxs-lookup"><span data-stu-id="ec5d3-113">Remarks</span></span>  

 <span data-ttu-id="ec5d3-114">このメソッドから制御が戻った後で、`szName` バッファーのサイズが十分で、アプリケーション ドメインの完全名を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="ec5d3-115">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ec5d3-116">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="ec5d3-117">別の方法として、最初に `GetAppDomainInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ec5d3-118">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec5d3-119">要件</span><span class="sxs-lookup"><span data-stu-id="ec5d3-119">Requirements</span></span>  

 <span data-ttu-id="ec5d3-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec5d3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec5d3-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec5d3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec5d3-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec5d3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec5d3-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec5d3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5d3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec5d3-124">See also</span></span>

- [<span data-ttu-id="ec5d3-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec5d3-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ec5d3-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec5d3-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ec5d3-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="ec5d3-127">Profiling</span></span>](index.md)
