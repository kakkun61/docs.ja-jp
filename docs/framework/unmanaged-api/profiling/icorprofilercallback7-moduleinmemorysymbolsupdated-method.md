---
title: 'ICorProfilerCallback7:: Moduleinmemory メソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 248d2f749ddcbd772313558af2b2721f4d1c0f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723091"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="a31bd-102">ICorProfilerCallback7:: Moduleinmemory メソッド</span><span class="sxs-lookup"><span data-stu-id="a31bd-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>

<span data-ttu-id="a31bd-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="a31bd-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a31bd-104">メモリ内モジュールに関連付けられているシンボルストリームが更新されるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a31bd-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="a31bd-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a31bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a31bd-106">Parameters</span></span>  

 <span data-ttu-id="a31bd-107">[入力] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="a31bd-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="a31bd-108">シンボルストリームが更新されるメモリ内モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="a31bd-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a31bd-109">注釈</span><span class="sxs-lookup"><span data-stu-id="a31bd-109">Remarks</span></span>  

 <span data-ttu-id="a31bd-110">このコールバックは、 [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドを呼び出すときに、 [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md)イベントマスクフラグを設定することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="a31bd-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a31bd-111">このイベントは、api を使用して暗黙的に作成または変更されたシンボルに対しては、現在発生していません <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="a31bd-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="a31bd-112">アセンブリのシンボルを指定する引数を含むマネージメソッドのオーバーロードのいずれかを呼び出すことによって、シンボルが事前に提供されていても <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` 、 [moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックが発生するまで、ランタイムはシンボリックデータをモジュールに実際に関連付けない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a31bd-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="a31bd-113">このイベントは、後でこのようなモジュールのシンボルを収集する機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="a31bd-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a31bd-114">要件</span><span class="sxs-lookup"><span data-stu-id="a31bd-114">Requirements</span></span>  

 <span data-ttu-id="a31bd-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a31bd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a31bd-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a31bd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a31bd-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a31bd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a31bd-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31bd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31bd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a31bd-119">See also</span></span>

- [<span data-ttu-id="a31bd-120">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a31bd-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="a31bd-121">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a31bd-121">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="a31bd-122">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a31bd-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
