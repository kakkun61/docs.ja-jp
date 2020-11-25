---
title: ICorDebugFunction::GetNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: e34dff2ebdb6e1ea56c2682b351c3e17a44416f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726315"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="1b47e-102">ICorDebugFunction::GetNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="1b47e-102">ICorDebugFunction::GetNativeCode Method</span></span>

<span data-ttu-id="1b47e-103">このコード例で表される関数のネイティブコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b47e-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b47e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b47e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b47e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b47e-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="1b47e-106">入出力この関数のネイティブコードを表す、のコードインスタンスへのポインター。この関数が just-in-time (JIT) コンパイルされていない Microsoft 中間言語 (MSIL) コードの場合は null。</span><span class="sxs-lookup"><span data-stu-id="1b47e-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b47e-107">注釈</span><span class="sxs-lookup"><span data-stu-id="1b47e-107">Remarks</span></span>  

 <span data-ttu-id="1b47e-108">このインスタンスで表される関数が、 `ICorDebugFunction` ジェネリック型の場合と同じように JIT コンパイルされた場合、は、 `GetNativeCode` ランダムなネイティブコードオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1b47e-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b47e-109">要件</span><span class="sxs-lookup"><span data-stu-id="1b47e-109">Requirements</span></span>  

 <span data-ttu-id="1b47e-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b47e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b47e-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b47e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b47e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b47e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b47e-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b47e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
