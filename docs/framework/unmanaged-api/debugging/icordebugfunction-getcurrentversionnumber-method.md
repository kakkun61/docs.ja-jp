---
title: ICorDebugFunction::GetCurrentVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 14579d4c84be9bb225e618715b3a7d45ccaac0a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728148"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="cbfe6-102">ICorDebugFunction::GetCurrentVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="cbfe6-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="cbfe6-103">このオブジェクトによって表される関数に対して行われた最新の編集のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="cbfe6-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbfe6-104">構文</span><span class="sxs-lookup"><span data-stu-id="cbfe6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbfe6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cbfe6-105">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="cbfe6-106">入出力この関数に対して行われた最新の編集のバージョン番号を表す整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cbfe6-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbfe6-107">注釈</span><span class="sxs-lookup"><span data-stu-id="cbfe6-107">Remarks</span></span>  

 <span data-ttu-id="cbfe6-108">この関数に対して行われた最新の編集のバージョン番号が、関数自体のバージョン番号よりも大きい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cbfe6-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="cbfe6-109">[ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md)メソッドまたは[Code:: GetVersionNumber](icordebugcode-getversionnumber-method.md)メソッドを使用して、関数のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="cbfe6-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbfe6-110">要件</span><span class="sxs-lookup"><span data-stu-id="cbfe6-110">Requirements</span></span>  

 <span data-ttu-id="cbfe6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbfe6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbfe6-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbfe6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbfe6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbfe6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbfe6-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbfe6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
