---
title: ICorDebugILFrame::GetLocalVariable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 54ecce830b928ded115233eb99932cc15a471033
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703136"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="25957-102">ICorDebugILFrame::GetLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="25957-102">ICorDebugILFrame::GetLocalVariable Method</span></span>

<span data-ttu-id="25957-103">この MSIL (Microsoft 中間言語) スタックフレーム内の指定されたローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="25957-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25957-104">構文</span><span class="sxs-lookup"><span data-stu-id="25957-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25957-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25957-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="25957-106">からこの MSIL スタックフレーム内のローカル変数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="25957-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="25957-107">[out] 取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25957-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25957-108">注釈</span><span class="sxs-lookup"><span data-stu-id="25957-108">Remarks</span></span>  

 <span data-ttu-id="25957-109">メソッドは、 `GetLocalVariable` MSIL スタックフレーム内または just-in-time (JIT) コンパイルフレームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="25957-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25957-110">要件</span><span class="sxs-lookup"><span data-stu-id="25957-110">Requirements</span></span>  

 <span data-ttu-id="25957-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25957-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25957-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25957-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25957-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25957-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25957-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25957-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
