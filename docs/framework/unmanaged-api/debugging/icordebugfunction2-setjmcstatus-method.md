---
title: ICorDebugFunction2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 55f219b5b834f365b87440e69bfa7d2c4e519235
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696094"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="d96d0-102">ICorDebugFunction2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="d96d0-102">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="d96d0-103">この ICorDebugFunction2 によって表される関数をステップ実行マイコードのみにマークします。</span><span class="sxs-lookup"><span data-stu-id="d96d0-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d96d0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d96d0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d96d0-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="d96d0-106">から関数を `true` ユーザーコードとしてマークする場合はに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="d96d0-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="d96d0-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d96d0-107">Return Values</span></span>  
  
|<span data-ttu-id="d96d0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d96d0-108">HRESULT</span></span>|<span data-ttu-id="d96d0-109">説明</span><span class="sxs-lookup"><span data-stu-id="d96d0-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d96d0-110">関数は正常にマークされました。</span><span class="sxs-lookup"><span data-stu-id="d96d0-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="d96d0-111">デバッグできないため、関数をユーザーコードとしてマークできませんでした。</span><span class="sxs-lookup"><span data-stu-id="d96d0-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d96d0-112">注釈</span><span class="sxs-lookup"><span data-stu-id="d96d0-112">Remarks</span></span>  

 <span data-ttu-id="d96d0-113">マイコードのみステッパは、非ユーザーコードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="d96d0-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="d96d0-114">ユーザーコードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d96d0-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96d0-115">要件</span><span class="sxs-lookup"><span data-stu-id="d96d0-115">Requirements</span></span>  

 <span data-ttu-id="d96d0-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d96d0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96d0-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d96d0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d96d0-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d96d0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d96d0-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96d0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
