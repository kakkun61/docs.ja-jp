---
title: ICorProfilerInfo3::GetThreadStaticAddress2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: d8f2788d63f27aac30cf239b410eecea31f09212
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697884"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="04583-102">ICorProfilerInfo3::GetThreadStaticAddress2 メソッド</span><span class="sxs-lookup"><span data-stu-id="04583-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>

<span data-ttu-id="04583-103">指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="04583-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04583-104">構文</span><span class="sxs-lookup"><span data-stu-id="04583-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04583-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04583-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="04583-106">から要求されたスレッド静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="04583-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="04583-107">から要求されたスレッドの静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="04583-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="04583-108">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="04583-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="04583-109">から要求された静的フィールドのスコープであるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="04583-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="04583-110">入出力指定したスレッド内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="04583-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04583-111">注釈</span><span class="sxs-lookup"><span data-stu-id="04583-111">Remarks</span></span>  

 <span data-ttu-id="04583-112">`GetThreadStaticAddress2`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="04583-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="04583-113">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="04583-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="04583-114">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="04583-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="04583-115">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="04583-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="04583-116">では、クラスのクラスコンストラクターが完了する前に、 `GetThreadStaticAddress2` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="04583-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="04583-117">[ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md)メソッドはメソッドに似てい `GetThreadStaticAddress2` ますが、アプリケーションドメインの引数を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="04583-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04583-118">要件</span><span class="sxs-lookup"><span data-stu-id="04583-118">Requirements</span></span>  

 <span data-ttu-id="04583-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04583-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04583-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04583-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04583-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04583-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04583-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04583-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04583-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="04583-123">See also</span></span>

- [<span data-ttu-id="04583-124">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04583-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="04583-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="04583-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="04583-126">プロファイル</span><span class="sxs-lookup"><span data-stu-id="04583-126">Profiling</span></span>](index.md)
