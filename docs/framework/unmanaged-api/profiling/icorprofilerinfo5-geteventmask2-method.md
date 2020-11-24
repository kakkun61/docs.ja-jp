---
title: ICorProfilerInfo5::GetEventMask2 メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 81509db178b0ab1a524dcc4b00f39264e87a220d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682784"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="3c189-102">ICorProfilerInfo5::GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3c189-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>

<span data-ttu-id="3c189-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="3c189-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3c189-104">現在のイベント カテゴリを取得します。プロファイラーは、これに関する通知を共通言語ランタイム (CLR) から受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3c189-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="3c189-105">[ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md)メソッドで提供されていない機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c189-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c189-106">構文</span><span class="sxs-lookup"><span data-stu-id="3c189-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c189-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c189-107">Parameters</span></span>  

 `pdwEventsLow`  
 <span data-ttu-id="3c189-108">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c189-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="3c189-109">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="3c189-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="3c189-110">ビットは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="3c189-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="3c189-111">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c189-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="3c189-112">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="3c189-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="3c189-113">ビットは、 [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="3c189-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c189-114">注釈</span><span class="sxs-lookup"><span data-stu-id="3c189-114">Remarks</span></span>  

 <span data-ttu-id="3c189-115">`GetEventMask2` メソッドは、プロファイラーがサブスクライブしたコールバックを判断するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="3c189-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="3c189-116">通常は、値と値、および設定する新しいビットの論理 OR を実行 `pdwEventsLow` `pdwEventsHigh` し、次に [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c189-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="3c189-117">このメソッドは、 [Geteventmask](icorprofilerinfo-geteventmask-method.md) メソッドの代替手段として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="3c189-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c189-118">要件</span><span class="sxs-lookup"><span data-stu-id="3c189-118">Requirements</span></span>  

 <span data-ttu-id="3c189-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c189-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c189-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c189-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c189-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c189-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c189-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c189-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c189-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c189-123">See also</span></span>

- [<span data-ttu-id="3c189-124">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c189-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="3c189-125">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3c189-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
