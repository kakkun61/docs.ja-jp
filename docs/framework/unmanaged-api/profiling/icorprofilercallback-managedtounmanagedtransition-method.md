---
title: ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: ef65ed908c71bcc2755aaf42070439fd7dab3f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733140"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="c2c9e-102">ICorProfilerCallback::ManagedToUnmanagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="c2c9e-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="c2c9e-103">マネージコードからアンマネージコードへの遷移が発生したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c9e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2c9e-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c9e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2c9e-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="c2c9e-106">から呼び出される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="c2c9e-107">からマネージコードからアンマネージコードへの呼び出しによって移行が発生したかどうか、またはアンマネージコードによって呼び出されたマネージ関数からの戻り値によって発生したものかどうかを示す [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2c9e-108">注釈</span><span class="sxs-lookup"><span data-stu-id="c2c9e-108">Remarks</span></span>  

 <span data-ttu-id="c2c9e-109">の値 `reason` が COR_PRF_TRANSITION_CALL の場合、関数 ID はアンマネージ関数の ID であり、just-in-time コンパイラを使用してコンパイルされることはありません。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="c2c9e-110">アンマネージ関数には、名前やメタデータなどの基本的な情報が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="c2c9e-111">アンマネージ関数が暗黙のプラットフォーム呼び出し (PInvoke) を使用して呼び出された場合、ランタイムは呼び出し先を特定できず、の値は null になり `functionId` ます。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="c2c9e-112">暗黙の PInvoke の詳細については、「 [C++ Interop の使用 (暗黙的な pinvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c9e-113">要件</span><span class="sxs-lookup"><span data-stu-id="c2c9e-113">Requirements</span></span>  

 <span data-ttu-id="c2c9e-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2c9e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c9e-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2c9e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2c9e-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2c9e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c9e-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c9e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c9e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2c9e-118">See also</span></span>

- [<span data-ttu-id="c2c9e-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2c9e-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c2c9e-120">UnmanagedToManagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="c2c9e-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="c2c9e-121">C++ での明示的な PInvoke の使用 (DllImport 属性)</span><span class="sxs-lookup"><span data-stu-id="c2c9e-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
