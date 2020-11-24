---
title: 'ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 46ffa5cb4fac6988240d32cb1939cc25bdf0a412
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686073"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="f1633-102">ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド</span><span class="sxs-lookup"><span data-stu-id="f1633-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="f1633-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="f1633-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="f1633-104">メモリ内シンボルストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="f1633-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1633-105">構文</span><span class="sxs-lookup"><span data-stu-id="f1633-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1633-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1633-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="f1633-107">からメモリ内ストリームを格納しているモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="f1633-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="f1633-108">Pcountシンボルバイト数</span><span class="sxs-lookup"><span data-stu-id="f1633-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="f1633-109">入出力 `DWORD` メソッドから制御が戻るときに、ストリーム長がバイト単位で格納されている値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f1633-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1633-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f1633-110">Return Value</span></span>  

 <span data-ttu-id="f1633-111">`S_OK`メモリストリームの長さがゼロ (0) であっても、このメソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="f1633-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="f1633-112">メソッドが `CORPROF_E_MODULE_IS_DYNAMIC` を使用して作成された場合、メソッドはを返し <xref:System.Reflection.Emit?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="f1633-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1633-113">注釈</span><span class="sxs-lookup"><span data-stu-id="f1633-113">Remarks</span></span>  

 <span data-ttu-id="f1633-114">モジュールにメモリ内シンボルがある場合は、ストリームの長さがに配置され `pCountSymbolBytes` ます。</span><span class="sxs-lookup"><span data-stu-id="f1633-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="f1633-115">モジュールにメモリ内シンボルがない場合は `*pCountSymbolBytes = 0` 。</span><span class="sxs-lookup"><span data-stu-id="f1633-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1633-116">現在の実装では、リフレクションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f1633-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="f1633-117">モジュールがリフレクションを使用して作成された場合、メソッドは `CORPROF_E_MODULE_IS_DYNAMIC` を返します。</span><span class="sxs-lookup"><span data-stu-id="f1633-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1633-118">要件</span><span class="sxs-lookup"><span data-stu-id="f1633-118">Requirements</span></span>  

 <span data-ttu-id="f1633-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1633-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1633-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1633-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1633-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1633-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1633-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1633-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1633-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1633-123">See also</span></span>

- [<span data-ttu-id="f1633-124">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1633-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
