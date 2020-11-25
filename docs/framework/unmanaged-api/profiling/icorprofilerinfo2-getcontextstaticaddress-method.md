---
title: ICorProfilerInfo2::GetContextStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 067e5093cc3b141936eeec43e77e6e1a9475a8a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727121"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="3c306-102">ICorProfilerInfo2::GetContextStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="3c306-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="3c306-103">指定されたコンテキストのスコープ内にある、指定されたコンテキスト静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3c306-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c306-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c306-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c306-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c306-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="3c306-106">から要求されたコンテキスト静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="3c306-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="3c306-107">から要求されたコンテキスト静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="3c306-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="3c306-108">から要求されたコンテキスト静的フィールドのスコープであるコンテキストの ID。</span><span class="sxs-lookup"><span data-stu-id="3c306-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="3c306-109">入出力指定されたコンテキスト内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c306-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c306-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3c306-110">Remarks</span></span>  

 <span data-ttu-id="3c306-111">`GetContextStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c306-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="3c306-112">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3c306-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="3c306-113">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3c306-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="3c306-114">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="3c306-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="3c306-115">では、クラスのクラスコンストラクターが完了する前に、 `GetContextStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c306-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c306-116">要件</span><span class="sxs-lookup"><span data-stu-id="3c306-116">Requirements</span></span>  

 <span data-ttu-id="3c306-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c306-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c306-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c306-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c306-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c306-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c306-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c306-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c306-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c306-121">See also</span></span>

- [<span data-ttu-id="3c306-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c306-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3c306-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c306-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
