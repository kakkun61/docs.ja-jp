---
title: 'ICorProfilerInfo7:: ReadInMemorySymbols'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 6917900b7494550992dfa82f45ed0140f95e68cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733621"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="6527b-102">ICorProfilerInfo7:: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="6527b-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>

<span data-ttu-id="6527b-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="6527b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="6527b-104">メモリ内シンボルストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="6527b-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6527b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6527b-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6527b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6527b-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="6527b-107">からメモリ内ストリームを格納しているモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="6527b-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="6527b-108">からメモリ内ストリーム内でバイトの読み取りを開始する位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6527b-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="6527b-109">入出力データがコピーされるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6527b-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="6527b-110">バッファーには、 `countSymbolBytes` 使用可能な領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="6527b-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="6527b-111">からコピーするバイト数。</span><span class="sxs-lookup"><span data-stu-id="6527b-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="6527b-112">入出力メソッドから制御が戻るときに、実際に読み取られたバイト数を格納します。</span><span class="sxs-lookup"><span data-stu-id="6527b-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6527b-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="6527b-113">Return Value</span></span>  

 <span data-ttu-id="6527b-114">`S_OK`0以外のバイト数が読み取られた場合は。</span><span class="sxs-lookup"><span data-stu-id="6527b-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="6527b-115">`CORPROF_E_MODULE_IS_DYNAMIC`モジュールがを使用して作成された場合は <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="6527b-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6527b-116">注釈</span><span class="sxs-lookup"><span data-stu-id="6527b-116">Remarks</span></span>  

 <span data-ttu-id="6527b-117">メソッドは、 `ReadInMemorySymbols` `countSymbolBytes` インメモリストリーム内のオフセットを開始位置として、データの読み取りを試み      `symbolsReadOffset` ます。</span><span class="sxs-lookup"><span data-stu-id="6527b-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="6527b-118">データはにコピーされ `pSymbolBytes` ます。これには、使用可能な領域があることが予想され `countSymbolBytes` ます。</span><span class="sxs-lookup"><span data-stu-id="6527b-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="6527b-119">`pCountSymbolsBytesRead` 実際に読み取られたバイト数を格納し `countSymbolBytes` ます。ストリームの末尾に到達した場合よりも小さくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="6527b-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6527b-120">現在の実装では、リフレクションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6527b-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="6527b-121">モジュールがリフレクションを使用して作成された場合、メソッドは `CORPROF_E_MODULE_IS_DYNAMIC` を返します。</span><span class="sxs-lookup"><span data-stu-id="6527b-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6527b-122">要件</span><span class="sxs-lookup"><span data-stu-id="6527b-122">Requirements</span></span>  

 <span data-ttu-id="6527b-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6527b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6527b-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6527b-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6527b-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6527b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6527b-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6527b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6527b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6527b-127">See also</span></span>

- [<span data-ttu-id="6527b-128">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6527b-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
