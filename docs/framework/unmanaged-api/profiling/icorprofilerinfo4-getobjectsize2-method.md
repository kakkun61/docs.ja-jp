---
title: ICorProfilerInfo4::GetObjectSize2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 960f8f1fe2315e068d599aa5a31e03f521b235a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733868"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="0c845-102">ICorProfilerInfo4::GetObjectSize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0c845-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>

<span data-ttu-id="0c845-103">指定したオブジェクトのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="0c845-103">Returns the size of a specified object.</span></span> <span data-ttu-id="0c845-104">で表現できる値よりも大きいオブジェクトのサイズをレポートすることによって、 [ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) メソッドを置き換え `ULONG` ます。</span><span class="sxs-lookup"><span data-stu-id="0c845-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c845-105">構文</span><span class="sxs-lookup"><span data-stu-id="0c845-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c845-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c845-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="0c845-107">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="0c845-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="0c845-108">入出力オブジェクトのサイズへのポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0c845-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c845-109">注釈</span><span class="sxs-lookup"><span data-stu-id="0c845-109">Remarks</span></span>  

 <span data-ttu-id="0c845-110">多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。</span><span class="sxs-lookup"><span data-stu-id="0c845-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="0c845-111">ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0c845-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c845-112">要件</span><span class="sxs-lookup"><span data-stu-id="0c845-112">Requirements</span></span>  

 <span data-ttu-id="0c845-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c845-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c845-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c845-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c845-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c845-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c845-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c845-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c845-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c845-117">See also</span></span>

- [<span data-ttu-id="0c845-118">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c845-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
