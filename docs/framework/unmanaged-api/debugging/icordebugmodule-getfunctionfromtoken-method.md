---
title: ICorDebugModule::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: bf2acd897c9c45e445b864f85550ed7ed6e00886
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710156"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="9c3d9-102">ICorDebugModule::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="9c3d9-102">ICorDebugModule::GetFunctionFromToken Method</span></span>

<span data-ttu-id="9c3d9-103">メタデータトークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9c3d9-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c3d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c3d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c3d9-105">Parameters</span></span>  

 `methodDef`  
 <span data-ttu-id="9c3d9-106">から `mdMethodDef` 関数のメタデータを参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="9c3d9-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="9c3d9-107">入出力関数を表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9c3d9-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c3d9-108">注釈</span><span class="sxs-lookup"><span data-stu-id="9c3d9-108">Remarks</span></span>  

 <span data-ttu-id="9c3d9-109">渡された `GetFunctionFromToken` 値 `methodDef` が Microsoft 中間言語 (MSIL) メソッドを参照していない場合、メソッドは CORDBG_E_FUNCTION_NOT_IL HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="9c3d9-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c3d9-110">要件</span><span class="sxs-lookup"><span data-stu-id="9c3d9-110">Requirements</span></span>  

 <span data-ttu-id="9c3d9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c3d9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c3d9-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c3d9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c3d9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c3d9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c3d9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c3d9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
