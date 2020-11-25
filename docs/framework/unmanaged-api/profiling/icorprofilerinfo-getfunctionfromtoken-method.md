---
title: ICorProfilerInfo::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 9c7f01d2e462ad1cb0532be6f369c3118a4deb6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722493"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="bf4bb-102">ICorProfilerInfo::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="bf4bb-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="bf4bb-103">関数の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-103">Gets the ID of a function.</span></span> <span data-ttu-id="bf4bb-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bf4bb-105">代わりに [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4bb-106">構文</span><span class="sxs-lookup"><span data-stu-id="bf4bb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bf4bb-107">解説</span><span class="sxs-lookup"><span data-stu-id="bf4bb-107">Remarks</span></span>  

 <span data-ttu-id="bf4bb-108">メソッドは、ジェネリック `GetFunctionFromToken` 型のジェネリック関数または関数に対しては機能しません。現在は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="bf4bb-109">`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`すべての関数に使用します。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4bb-110">要件</span><span class="sxs-lookup"><span data-stu-id="bf4bb-110">Requirements</span></span>  

 <span data-ttu-id="bf4bb-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf4bb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4bb-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf4bb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf4bb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf4bb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf4bb-114">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="bf4bb-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4bb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf4bb-115">See also</span></span>

- [<span data-ttu-id="bf4bb-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf4bb-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
