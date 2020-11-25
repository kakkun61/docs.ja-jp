---
title: ICorProfilerInfo::IsArrayClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 2608f91a7c5baa935e48fbe58ad4d14aaaad1f0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722506"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="1d2a6-102">ICorProfilerInfo::IsArrayClass メソッド</span><span class="sxs-lookup"><span data-stu-id="1d2a6-102">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="1d2a6-103">指定したクラスが配列クラスであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d2a6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d2a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d2a6-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="1d2a6-106">から調べるクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="1d2a6-107">入出力配列要素の型を示す CorElementType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="1d2a6-108">入出力使用可能な場合は、配列要素のクラス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="1d2a6-109">入出力配列のランク (次元の数) を示す整数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2a6-110">注釈</span><span class="sxs-lookup"><span data-stu-id="1d2a6-110">Remarks</span></span>  

 <span data-ttu-id="1d2a6-111">指定したクラスが配列クラスの場合、 `IsArrayClass` メソッドは、null 以外の出力パラメーターの S_OK HRESULT と値を返します。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="1d2a6-112">それ以外の場合は S_FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2a6-113">要件</span><span class="sxs-lookup"><span data-stu-id="1d2a6-113">Requirements</span></span>  

 <span data-ttu-id="1d2a6-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d2a6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2a6-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d2a6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d2a6-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d2a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d2a6-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2a6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d2a6-118">See also</span></span>

- [<span data-ttu-id="1d2a6-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d2a6-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
