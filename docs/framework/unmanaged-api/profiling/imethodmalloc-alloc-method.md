---
title: IMethodMalloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: 58809f12e4dd4419b754caafc3f8b883b8bc5089
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721167"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="d2b17-102">IMethodMalloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="d2b17-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="d2b17-103">新しい Microsoft 中間言語 (MSIL) 関数本体に対して、指定された量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="d2b17-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2b17-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2b17-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="d2b17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2b17-105">Parameters</span></span>

`cb`\
<span data-ttu-id="d2b17-106">からメソッド本体に割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="d2b17-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2b17-107">注釈</span><span class="sxs-lookup"><span data-stu-id="d2b17-107">Remarks</span></span>

 <span data-ttu-id="d2b17-108">割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベースアドレスよりも大きいアドレスから開始されます。</span><span class="sxs-lookup"><span data-stu-id="d2b17-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="d2b17-109">つまり、各アロケーターは特定のモジュールに対して作成され、そのベースアドレスからの正のオフセットでメモリの割り当てが試行されます。</span><span class="sxs-lookup"><span data-stu-id="d2b17-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="d2b17-110">が、 `Alloc` モジュールのベースアドレスよりも大きいアドレスで要求されたバイト数を割り当てられなかった場合は、使用可能な実際のメモリ容量に関係なく E_OUTOFMEMORY を返します。</span><span class="sxs-lookup"><span data-stu-id="d2b17-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="d2b17-111">メソッドは、 `Alloc` [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) メソッドと組み合わせて使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2b17-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2b17-112">要件</span><span class="sxs-lookup"><span data-stu-id="d2b17-112">Requirements</span></span>

 <span data-ttu-id="d2b17-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2b17-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="d2b17-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2b17-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="d2b17-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2b17-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="d2b17-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2b17-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d2b17-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2b17-117">See also</span></span>

- [<span data-ttu-id="d2b17-118">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2b17-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
