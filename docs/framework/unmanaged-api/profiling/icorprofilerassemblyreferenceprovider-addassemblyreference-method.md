---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 56468fd38bc110318e04d9b1beda61e279f731d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685321"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="a297c-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="a297c-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>

<span data-ttu-id="a297c-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="a297c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a297c-104">プロファイラーが [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加することを計画しているアセンブリ参照の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="a297c-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a297c-105">構文</span><span class="sxs-lookup"><span data-stu-id="a297c-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a297c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a297c-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="a297c-107">アセンブリ参照クロージャウォークを実行するときに考慮する必要があるアセンブリ参照に関する情報を CLR に提供する、 [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a297c-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a297c-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a297c-108">Remarks</span></span>  

 <span data-ttu-id="a297c-109">プロファイラーは、 `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) コールバックの引数で指定されたアセンブリから参照するターゲットアセンブリごとに、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a297c-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="a297c-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)インターフェイスオブジェクトは、引数のアセンブリパスと名前と共に、プロファイラーの[ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)コールバックに渡され `wszAssemblyPath` ます。</span><span class="sxs-lookup"><span data-stu-id="a297c-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a297c-111">要件</span><span class="sxs-lookup"><span data-stu-id="a297c-111">Requirements</span></span>  

 <span data-ttu-id="a297c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a297c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a297c-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a297c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a297c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a297c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a297c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a297c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a297c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a297c-116">See also</span></span>

- [<span data-ttu-id="a297c-117">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a297c-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="a297c-118">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="a297c-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="a297c-119">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a297c-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
