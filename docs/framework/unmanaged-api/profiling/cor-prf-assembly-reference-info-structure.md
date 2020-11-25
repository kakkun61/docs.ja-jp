---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 7c7d447afcb5a8617aa92212f3325719d5f43bf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718619"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="1246a-102">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="1246a-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="1246a-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="1246a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1246a-104">アセンブリ参照クロージャのウォークを実行するときに考慮する必要があるアセンブリ参照の情報を、共通言語ランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="1246a-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1246a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1246a-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1246a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1246a-106">Members</span></span>  
  
|<span data-ttu-id="1246a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1246a-107">Member</span></span>|<span data-ttu-id="1246a-108">説明</span><span class="sxs-lookup"><span data-stu-id="1246a-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="1246a-109">公開キー、またはアセンブリのトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1246a-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="1246a-110">公開キーまたはトークンのバイト数。</span><span class="sxs-lookup"><span data-stu-id="1246a-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="1246a-111">参照されるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="1246a-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="1246a-112">アセンブリのメタデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1246a-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="1246a-113">ハッシュ バイナリ ラージ オブジェクト (BLOB) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1246a-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="1246a-114">ハッシュ BLOB のバイト数。</span><span class="sxs-lookup"><span data-stu-id="1246a-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="1246a-115">アセンブリのフラグ。</span><span class="sxs-lookup"><span data-stu-id="1246a-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1246a-116">注釈</span><span class="sxs-lookup"><span data-stu-id="1246a-116">Remarks</span></span>  

 <span data-ttu-id="1246a-117">`COR_PRF_EX_CLAUSE_INFO` 構造は、追加のアセンブリ参照を宣言するときに、プロファイラーによって値が設定されます。ここでの追加のアセンブリ参照は、アセンブリ参照クロージャのウォークを実行するときに共通言語ランタイムが考慮するものです。</span><span class="sxs-lookup"><span data-stu-id="1246a-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="1246a-118">プロファイラーが [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback メソッドを登録すると、ランタイムは、読み込まれるアセンブリのパスと名前、およびそのメソッドへの [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) インターフェイスオブジェクトへのポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="1246a-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="1246a-119">その後、プロファイラーは、 [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)コールバックで指定されたアセンブリから参照するターゲットアセンブリごとに、オブジェクトを使用して ICorProfilerAssemblyReferenceProvider:: addassemblyreference メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1246a-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1246a-120">要件</span><span class="sxs-lookup"><span data-stu-id="1246a-120">Requirements</span></span>  

 <span data-ttu-id="1246a-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1246a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1246a-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1246a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1246a-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1246a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1246a-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1246a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1246a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1246a-125">See also</span></span>

- [<span data-ttu-id="1246a-126">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1246a-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="1246a-127">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="1246a-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="1246a-128">AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="1246a-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
