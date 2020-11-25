---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 796c6aa4c42a037fe612b4b1ee5267a678cf5224
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729643"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="50d52-102">ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="50d52-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="50d52-103">コンストラクターメソッドを呼び出さずに、指定したクラスの新しいパラメーター化された型オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="50d52-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d52-104">構文</span><span class="sxs-lookup"><span data-stu-id="50d52-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50d52-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50d52-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="50d52-106">からインスタンス化するオブジェクトのクラスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50d52-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="50d52-107">から渡された型引数の数。</span><span class="sxs-lookup"><span data-stu-id="50d52-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="50d52-108">からポインターの配列。各ポインターは、インスタンス化されているオブジェクトの型引数を表す、テキスト型のオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="50d52-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50d52-109">注釈</span><span class="sxs-lookup"><span data-stu-id="50d52-109">Remarks</span></span>  

 <span data-ttu-id="50d52-110">`NewParameterizedObjectNoConstructor`型引数の数が正しくないか、型引数の型が正しくない場合、メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="50d52-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50d52-111">要件</span><span class="sxs-lookup"><span data-stu-id="50d52-111">Requirements</span></span>  

 <span data-ttu-id="50d52-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50d52-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50d52-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50d52-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50d52-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50d52-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50d52-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50d52-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
