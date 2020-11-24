---
title: ICLRGCManager2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: d2873b5e1f8229e8a16dfaacf1c9737ac47405bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672800"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="f94cf-102">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94cf-102">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="f94cf-103">ホストが共通言語ランタイムのガベージコレクションシステムと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f94cf-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f94cf-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f94cf-104">Methods</span></span>  
  
|<span data-ttu-id="f94cf-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f94cf-105">Method</span></span>|<span data-ttu-id="f94cf-106">説明</span><span class="sxs-lookup"><span data-stu-id="f94cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f94cf-107">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f94cf-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="f94cf-108">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="f94cf-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="f94cf-109">より大きいジェネレーション0およびセグメントサイズを有効に `DWORD` します。</span><span class="sxs-lookup"><span data-stu-id="f94cf-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f94cf-110">注釈</span><span class="sxs-lookup"><span data-stu-id="f94cf-110">Remarks</span></span>  

 <span data-ttu-id="f94cf-111">このインターフェイスは、 [ICLRGCManager インターフェイス](iclrgcmanager-interface.md)から継承されます。</span><span class="sxs-lookup"><span data-stu-id="f94cf-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="f94cf-112">共通言語ランタイム (CLR) は、マネージ型を使用してガベージコレクション機構を実装し <xref:System.GC> ます。</span><span class="sxs-lookup"><span data-stu-id="f94cf-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="f94cf-113">ガベージコレクションシステムの詳細については、「 [ガベージコレクション](../../../standard/garbage-collection/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f94cf-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f94cf-114">要件</span><span class="sxs-lookup"><span data-stu-id="f94cf-114">Requirements</span></span>  

 <span data-ttu-id="f94cf-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f94cf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94cf-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f94cf-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f94cf-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f94cf-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f94cf-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94cf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94cf-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f94cf-119">See also</span></span>

- [<span data-ttu-id="f94cf-120">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="f94cf-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="f94cf-121">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="f94cf-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="f94cf-122">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94cf-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f94cf-123">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94cf-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f94cf-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94cf-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f94cf-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f94cf-125">Hosting</span></span>](index.md)
