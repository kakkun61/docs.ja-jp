---
title: ICorDebugAppDomain2::GetFunctionPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: be797b1b3f288fd367d7f624e9cf33015dd114ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698274"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="ac7a9-102">ICorDebugAppDomain2::GetFunctionPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="ac7a9-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="ac7a9-103">指定されたシグネチャを持つ関数へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac7a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac7a9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac7a9-105">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="ac7a9-106">から関数の型引数の数。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="ac7a9-107">からポインターの配列。各ポインターは、関数の型引数を表す、テキスト型のオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="ac7a9-108">最初の要素は戻り値の型です。その他の要素はそれぞれパラメーター型です。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="ac7a9-109">入出力関数へのポインターを表すオブジェクトのアドレスへのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac7a9-110">要件</span><span class="sxs-lookup"><span data-stu-id="ac7a9-110">Requirements</span></span>  

 <span data-ttu-id="ac7a9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac7a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac7a9-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac7a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac7a9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac7a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac7a9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac7a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
