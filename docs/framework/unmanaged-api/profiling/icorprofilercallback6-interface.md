---
title: ICorProfilerCallback6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 2176b624a427994b9d2af4b5eba31a64c9288a0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725470"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="1bde8-102">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bde8-102">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="1bde8-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="1bde8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1bde8-104">アセンブリが読み込まれていることをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供する [ICorProfilerCallback5](icorprofilercallback5-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="1bde8-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bde8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1bde8-105">Methods</span></span>  
  
|<span data-ttu-id="1bde8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1bde8-106">Method</span></span>|<span data-ttu-id="1bde8-107">説明</span><span class="sxs-lookup"><span data-stu-id="1bde8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1bde8-108">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="1bde8-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="1bde8-109">共通言語ランタイムがアセンブリ参照クロージャのウォークを実行するときに、アセンブリがごく初期のローディング状態であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1bde8-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bde8-110">解説</span><span class="sxs-lookup"><span data-stu-id="1bde8-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bde8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="1bde8-111">Requirements</span></span>  

 <span data-ttu-id="1bde8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bde8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bde8-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bde8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bde8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bde8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bde8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bde8-115">See also</span></span>

- [<span data-ttu-id="1bde8-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bde8-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
