---
title: ICorDebugILFrame::GetArgument メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: d17179dbeb9564b16c0c95a43502a53a67d3b9b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703163"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="68719-102">ICorDebugILFrame::GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="68719-102">ICorDebugILFrame::GetArgument Method</span></span>

<span data-ttu-id="68719-103">この MSIL (Microsoft 中間言語) スタックフレーム内の指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="68719-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68719-104">構文</span><span class="sxs-lookup"><span data-stu-id="68719-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68719-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68719-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="68719-106">からこの MSIL スタックフレーム内の引数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="68719-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="68719-107">[out] 取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="68719-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68719-108">注釈</span><span class="sxs-lookup"><span data-stu-id="68719-108">Remarks</span></span>  

 <span data-ttu-id="68719-109">メソッドは、 `GetArgument` MSIL スタックフレーム内または just-in-time (JIT) コンパイルフレームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="68719-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68719-110">要件</span><span class="sxs-lookup"><span data-stu-id="68719-110">Requirements</span></span>  

 <span data-ttu-id="68719-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68719-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68719-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68719-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68719-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68719-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68719-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68719-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
