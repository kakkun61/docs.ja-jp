---
title: IMethodMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 8eccdba75b59df505ae72d74cfcd2bc83de2b45a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688173"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="09e10-102">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09e10-102">IMethodMalloc Interface</span></span>

<span data-ttu-id="09e10-103">新しい Microsoft 中間言語 (MSIL) 関数の本体にメモリを割り当てる方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="09e10-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09e10-104">インターフェイスは、 `IMethodMalloc` 単純なメモリアロケーターです。</span><span class="sxs-lookup"><span data-stu-id="09e10-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="09e10-105">メモリを割り当てることはできますが、解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="09e10-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09e10-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="09e10-106">Methods</span></span>  
  
|<span data-ttu-id="09e10-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="09e10-107">Method</span></span>|<span data-ttu-id="09e10-108">説明</span><span class="sxs-lookup"><span data-stu-id="09e10-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09e10-109">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="09e10-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="09e10-110">新しい MSIL 関数本体に指定された量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="09e10-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e10-111">注釈</span><span class="sxs-lookup"><span data-stu-id="09e10-111">Remarks</span></span>  

 <span data-ttu-id="09e10-112">各アロケーターはモジュール固有であり、関数本体がモジュールのベースから正のオフセットになるようにします。</span><span class="sxs-lookup"><span data-stu-id="09e10-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="09e10-113">モジュールのベースを超えるメモリは貴重な場合があるため、アロケーターを使用して、関数本体にのみメモリを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e10-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e10-114">要件</span><span class="sxs-lookup"><span data-stu-id="09e10-114">Requirements</span></span>  

 <span data-ttu-id="09e10-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09e10-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09e10-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09e10-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09e10-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09e10-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09e10-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09e10-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e10-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="09e10-119">See also</span></span>

- [<span data-ttu-id="09e10-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="09e10-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
