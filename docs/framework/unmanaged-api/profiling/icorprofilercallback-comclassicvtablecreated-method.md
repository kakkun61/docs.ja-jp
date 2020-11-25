---
title: ICorProfilerCallback::COMClassicVTableCreated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: c4d1f2467927e64ae08c0e7d8067c2ce96b95522
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700211"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="f0814-102">ICorProfilerCallback::COMClassicVTableCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="f0814-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="f0814-103">指定した IID およびクラスの COM 相互運用機能の vtable が作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f0814-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0814-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0814-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0814-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0814-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="f0814-106">\[in] vtable が作成されたクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="f0814-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="f0814-107">\[in] クラスによって実装されるインターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="f0814-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="f0814-108">この値は、インターフェイスが内部でのみ使用されている場合は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="f0814-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="f0814-109">\[) vtable の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f0814-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="f0814-110">\[in] vtable 内のスロットの数。</span><span class="sxs-lookup"><span data-stu-id="f0814-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0814-111">注釈</span><span class="sxs-lookup"><span data-stu-id="f0814-111">Remarks</span></span>  

 <span data-ttu-id="f0814-112">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f0814-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f0814-113">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="f0814-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f0814-114">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="f0814-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0814-115">要件</span><span class="sxs-lookup"><span data-stu-id="f0814-115">Requirements</span></span>  

 <span data-ttu-id="f0814-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0814-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0814-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0814-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0814-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0814-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0814-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0814-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0814-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0814-120">See also</span></span>

- [<span data-ttu-id="f0814-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0814-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f0814-122">COMClassicVTableDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="f0814-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
