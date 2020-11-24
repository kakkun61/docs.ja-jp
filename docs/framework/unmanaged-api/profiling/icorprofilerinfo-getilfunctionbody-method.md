---
title: ICorProfilerInfo::GetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 337c4fd091ebf7c39f7eee2358ca4f4df239cce3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687529"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="3a0c9-102">ICorProfilerInfo::GetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="3a0c9-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>

<span data-ttu-id="3a0c9-103">Microsoft 中間言語 (MSIL) コード内のメソッドの本文へのポインターを、ヘッダーを開始位置として取得します。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a0c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a0c9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a0c9-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="3a0c9-106">から関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="3a0c9-107">からメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="3a0c9-108">入出力メソッドのヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="3a0c9-109">入出力メソッドのサイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a0c9-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3a0c9-110">Remarks</span></span>  

 <span data-ttu-id="3a0c9-111">メソッドは、それが存在するモジュールによってスコープが設定されます。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="3a0c9-112">メソッドは、 `GetILFunctionBody` MSIL コードが共通言語ランタイム (CLR) によって読み込まれる前に、ツールにアクセスできるように設計されているため、メソッドのメタデータトークンを使用して目的のインスタンスを検索します。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="3a0c9-113">`GetILFunctionBody` は、が `methodId` MSIL コード (抽象メソッドやプラットフォーム呼び出し (PInvoke) メソッドなど) を持たないメソッドを指している場合、CORPROF_E_FUNCTION_NOT_IL HRESULT を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a0c9-114">要件</span><span class="sxs-lookup"><span data-stu-id="3a0c9-114">Requirements</span></span>  

 <span data-ttu-id="3a0c9-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a0c9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a0c9-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a0c9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a0c9-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a0c9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a0c9-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a0c9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0c9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a0c9-119">See also</span></span>

- [<span data-ttu-id="3a0c9-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a0c9-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
