---
title: ICorDebugEval2::CreateValueForType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 0b17bd729733665fbc4645aecd2e588b7eba14bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729695"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="67374-102">ICorDebugEval2::CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="67374-102">ICorDebugEval2::CreateValueForType Method</span></span>

<span data-ttu-id="67374-103">初期値が0または null の、指定した型の新しい ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="67374-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67374-104">構文</span><span class="sxs-lookup"><span data-stu-id="67374-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67374-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67374-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="67374-106">から型を表す、の型のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="67374-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="67374-107">入出力値を表すオブジェクトのアドレスへのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="67374-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67374-108">注釈</span><span class="sxs-lookup"><span data-stu-id="67374-108">Remarks</span></span>  

 <span data-ttu-id="67374-109">`CreateValueForType` 一般化 [Okeval:: CreateValue](icordebugeval-createvalue-method.md) 。などの構築された型を含む任意のオブジェクトの種類を指定でき `List<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="67374-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="67374-110">このメソッドの唯一の目的は、関数の評価に渡すことができる値を生成することです。</span><span class="sxs-lookup"><span data-stu-id="67374-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="67374-111">型はクラスまたは値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="67374-111">The type must be a class or a value type.</span></span> <span data-ttu-id="67374-112">このメソッドを使用して配列値や文字列値を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="67374-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67374-113">要件</span><span class="sxs-lookup"><span data-stu-id="67374-113">Requirements</span></span>  

 <span data-ttu-id="67374-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67374-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67374-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67374-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67374-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67374-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67374-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67374-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
