---
title: ICorProfilerInfo3::GetModuleInfo2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
ms.openlocfilehash: 2213b674cce27c77156b8de1bbf20d2975e3e55c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721596"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="af324-102">ICorProfilerInfo3::GetModuleInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="af324-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>

<span data-ttu-id="af324-103">モジュール ID を指定して、モジュールのファイル名、モジュールの親アセンブリの ID、およびモジュールのプロパティを示すビットマスクを返します。</span><span class="sxs-lookup"><span data-stu-id="af324-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af324-104">構文</span><span class="sxs-lookup"><span data-stu-id="af324-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af324-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af324-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="af324-106">[in] 情報が取得されるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="af324-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="af324-107">[out] モジュールが読み込まれるベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="af324-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="af324-108">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="af324-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="af324-109">[out] 返されるモジュールのファイル名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="af324-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="af324-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="af324-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="af324-111">メソッドから制御が戻るとき、このバッファーにモジュールのファイル名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="af324-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="af324-112">[out] モジュールの親アセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="af324-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="af324-113">入出力モジュールのプロパティを指定する [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) 列挙体の値のビットマスク。</span><span class="sxs-lookup"><span data-stu-id="af324-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af324-114">注釈</span><span class="sxs-lookup"><span data-stu-id="af324-114">Remarks</span></span>  

 <span data-ttu-id="af324-115">動的モジュールの場合、`szName` パラメーターはモジュールのメタデータ名になり、ベース アドレスは 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="af324-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="af324-116">メタデータ名は、メタデータ内の Module テーブルの Name 列の値です。</span><span class="sxs-lookup"><span data-stu-id="af324-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="af324-117">これは、マネージコードにプロパティとして公開され、 <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> `szName` [IMetaDataImport:: getscopeprops](../metadata/imetadataimport-getscopeprops-method.md) メソッドのパラメーターとしてアンマネージメタデータクライアントコードにも公開されます。</span><span class="sxs-lookup"><span data-stu-id="af324-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="af324-118">メソッドは、 `GetModuleInfo2` モジュールの id が存在するとすぐに呼び出される場合がありますが、プロファイラーが [ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) コールバックを受信するまで、親アセンブリの id は使用できません。</span><span class="sxs-lookup"><span data-stu-id="af324-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="af324-119">`GetModuleInfo2` から制御が戻ったら、`szName` バッファーのサイズが十分で、モジュールのファイル名全体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af324-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="af324-120">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="af324-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="af324-121">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetModuleInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="af324-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="af324-122">別の方法として、最初に `GetModuleInfo2` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="af324-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="af324-123">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetModuleInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="af324-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af324-124">要件</span><span class="sxs-lookup"><span data-stu-id="af324-124">Requirements</span></span>  

 <span data-ttu-id="af324-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af324-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af324-126">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af324-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af324-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af324-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af324-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af324-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af324-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="af324-129">See also</span></span>

- [<span data-ttu-id="af324-130">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af324-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="af324-131">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="af324-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="af324-132">プロファイル</span><span class="sxs-lookup"><span data-stu-id="af324-132">Profiling</span></span>](index.md)
