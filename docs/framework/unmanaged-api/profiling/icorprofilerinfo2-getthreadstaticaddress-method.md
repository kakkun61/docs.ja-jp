---
title: ICorProfilerInfo2::GetThreadStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: 8b9b76fd58d8b3ec5c2d98156b7935051aff074b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731229"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="32034-102">ICorProfilerInfo2::GetThreadStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="32034-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>

<span data-ttu-id="32034-103">指定したスレッドのスコープ内にある、指定したスレッド静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="32034-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32034-104">構文</span><span class="sxs-lookup"><span data-stu-id="32034-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32034-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32034-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="32034-106">から要求されたスレッド静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="32034-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="32034-107">から要求されたスレッドの静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="32034-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="32034-108">から要求された静的フィールドのスコープであるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="32034-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="32034-109">入出力指定したスレッド内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="32034-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32034-110">注釈</span><span class="sxs-lookup"><span data-stu-id="32034-110">Remarks</span></span>  

 <span data-ttu-id="32034-111">`GetThreadStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="32034-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="32034-112">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="32034-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="32034-113">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="32034-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="32034-114">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションプロファイラーは、これらのアドレスが有効であると想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="32034-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="32034-115">では、クラスのクラスコンストラクターが完了する前に、 `GetThreadStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="32034-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32034-116">要件</span><span class="sxs-lookup"><span data-stu-id="32034-116">Requirements</span></span>  

 <span data-ttu-id="32034-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32034-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32034-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32034-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32034-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32034-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32034-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32034-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32034-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="32034-121">See also</span></span>

- [<span data-ttu-id="32034-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32034-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="32034-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32034-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
