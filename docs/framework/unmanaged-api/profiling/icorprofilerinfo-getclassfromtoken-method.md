---
title: ICorProfilerInfo::GetClassFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 7d9fe7d6d5c5af32be22ba19b52e7d40033a6eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706750"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="792c5-102">ICorProfilerInfo::GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="792c5-102">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="792c5-103">メタデータトークンを指定して、クラスの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="792c5-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="792c5-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="792c5-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="792c5-105">代わりに [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="792c5-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="792c5-106">構文</span><span class="sxs-lookup"><span data-stu-id="792c5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="792c5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="792c5-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="792c5-108">からクラスを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="792c5-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="792c5-109">から `mdTypeDef` クラスを参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="792c5-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="792c5-110">入出力クラス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="792c5-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="792c5-111">注釈</span><span class="sxs-lookup"><span data-stu-id="792c5-111">Remarks</span></span>  

 <span data-ttu-id="792c5-112">このメソッドは互換性のために残されています。代わりに、 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` すべての型に対してを使用します。</span><span class="sxs-lookup"><span data-stu-id="792c5-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="792c5-113">要件</span><span class="sxs-lookup"><span data-stu-id="792c5-113">Requirements</span></span>  

 <span data-ttu-id="792c5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="792c5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="792c5-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="792c5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="792c5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="792c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="792c5-117">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="792c5-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792c5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="792c5-118">See also</span></span>

- [<span data-ttu-id="792c5-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="792c5-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
