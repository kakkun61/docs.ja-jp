---
title: 列挙体のプロファイリング
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 8956a09cf76aa54452e8c020239e650e55d8a0d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701615"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="5cfa7-102">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="5cfa7-102">Profiling Enumerations</span></span>

<span data-ttu-id="5cfa7-103">このセクションでは、プロファイル API が使用するアンマネージ列挙について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cfa7-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5cfa7-104">In This Section</span></span>  

 [<span data-ttu-id="5cfa7-105">COR_PRF_CLAUSE_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="5cfa7-106">コードが入った、または出た例外句のタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="5cfa7-107">COR_PRF_CODEGEN_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="5cfa7-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="5cfa7-108">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドで設定できるコード生成フラグを定義します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="5cfa7-109">COR_PRF_FINALIZER_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="5cfa7-110">オブジェクトのファイナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="5cfa7-111">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="5cfa7-112">ガベージ コレクションのジェネレーションを識別します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="5cfa7-113">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="5cfa7-114">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="5cfa7-115">COR_PRF_GC_ROOT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="5cfa7-116">ガベージ コレクターのルートのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="5cfa7-117">COR_PRF_GC_ROOT_KIND 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="5cfa7-118">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md)コールバックによって公開されるガベージコレクターのルートの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="5cfa7-119">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="5cfa7-120">プロファイラーが読み込み時に[ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドに対して指定できる、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙に含まれるフラグだけでなく、フラグも提供します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="5cfa7-121">COR_PRF_JIT_CACHE 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="5cfa7-122">キャッシュされている関数検索の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="5cfa7-123">COR_PRF_MISC 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="5cfa7-124">特殊な識別子を指定する定数値を含めます。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="5cfa7-125">COR_PRF_MODULE_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="5cfa7-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="5cfa7-126">モジュールのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="5cfa7-127">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="5cfa7-128">プロファイラーがサブスクライブしようとする動作、機能、またはイベントの指定で使用する値を含めます。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="5cfa7-129">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="5cfa7-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="5cfa7-130">共通言語ランタイムのバージョンを表す値を含めます。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="5cfa7-131">COR_PRF_SNAPSHOT_INFO 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="5cfa7-132">プロファイラーの `StackSnapshotCallback` 関数への各呼び出しにおいて、スタック スナップショットでどのくらいのデータが返されるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="5cfa7-133">COR_PRF_STATIC_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="5cfa7-134">フィールドが静的であるかどうかを示し、静的な場合は、フィールドに適用される静的なクオリティを示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="5cfa7-135">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="5cfa7-136">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="5cfa7-137">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="5cfa7-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="5cfa7-138">マネージド コードからアンマネージド コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="5cfa7-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cfa7-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cfa7-139">Related Sections</span></span>  

 [<span data-ttu-id="5cfa7-140">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="5cfa7-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="5cfa7-141">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cfa7-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="5cfa7-142">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="5cfa7-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="5cfa7-143">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="5cfa7-143">Profiling Structures</span></span>](profiling-structures.md)
