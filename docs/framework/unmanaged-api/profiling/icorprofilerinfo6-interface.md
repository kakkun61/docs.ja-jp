---
title: ICorProfilerInfo6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: b3aed97e19694675fd5e0c1070dbbf6d9321eedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733842"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="89ce6-102">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89ce6-102">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="89ce6-103">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="89ce6-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="89ce6-104">特定の NGen モジュールで定義され、特定のメソッドにインラインで定義されているすべてのメソッドの列挙子を提供する [ICorProfilerInfo5](icorprofilerinfo5-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="89ce6-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89ce6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="89ce6-105">Methods</span></span>  
  
|<span data-ttu-id="89ce6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="89ce6-106">Method</span></span>|<span data-ttu-id="89ce6-107">説明</span><span class="sxs-lookup"><span data-stu-id="89ce6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89ce6-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="89ce6-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="89ce6-109">特定の NGen モジュールに属し、特定のメソッドの本体にインライン化されているすべてのメソッドの列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="89ce6-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89ce6-110">要件</span><span class="sxs-lookup"><span data-stu-id="89ce6-110">Requirements</span></span>  

 <span data-ttu-id="89ce6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89ce6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ce6-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89ce6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89ce6-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ce6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ce6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="89ce6-114">See also</span></span>

- [<span data-ttu-id="89ce6-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="89ce6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
