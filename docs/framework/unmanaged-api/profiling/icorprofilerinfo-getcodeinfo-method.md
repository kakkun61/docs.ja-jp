---
title: ICorProfilerInfo::GetCodeInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: da3b0acefa68be3506567ad4742784943f4ec5ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722519"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="701d1-102">ICorProfilerInfo::GetCodeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="701d1-102">ICorProfilerInfo::GetCodeInfo Method</span></span>

<span data-ttu-id="701d1-103">指定した関数 ID に関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="701d1-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="701d1-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="701d1-104">This method is obsolete.</span></span> <span data-ttu-id="701d1-105">代わりに [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="701d1-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701d1-106">構文</span><span class="sxs-lookup"><span data-stu-id="701d1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="701d1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="701d1-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="701d1-108">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="701d1-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="701d1-109">[out] 関数のネイティブ コードを構成するバイトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="701d1-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="701d1-110">[out] ネイティブ コードのバイト単位のサイズを指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="701d1-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="701d1-111">注釈</span><span class="sxs-lookup"><span data-stu-id="701d1-111">Remarks</span></span>  

 <span data-ttu-id="701d1-112">パフォーマンスを最適化するために、.NET Framework Version 2.0 のランタイムは、関数のプリコンパイルされたネイティブ コードを複数の領域に分割します。</span><span class="sxs-lookup"><span data-stu-id="701d1-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="701d1-113">したがって、関数のネイティブ コードの範囲を処理できないため、.NET Framework 2.0 では `GetCodeInfo` メソッドは互換性のために残されているだけです。</span><span class="sxs-lookup"><span data-stu-id="701d1-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="701d1-114">プロファイラーは、より一般的な `ICorProfilerInfo2::GetCodeInfo2` メソッドを代わりに使用するように切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="701d1-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="701d1-115">この関数は、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="701d1-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701d1-116">要件</span><span class="sxs-lookup"><span data-stu-id="701d1-116">Requirements</span></span>  

 <span data-ttu-id="701d1-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701d1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701d1-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="701d1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="701d1-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="701d1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="701d1-120">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="701d1-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701d1-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="701d1-121">See also</span></span>

- [<span data-ttu-id="701d1-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="701d1-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="701d1-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="701d1-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="701d1-124">プロファイル</span><span class="sxs-lookup"><span data-stu-id="701d1-124">Profiling</span></span>](index.md)
