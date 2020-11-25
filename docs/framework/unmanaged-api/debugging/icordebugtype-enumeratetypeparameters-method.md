---
title: ICorDebugType::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: 3717497ab6e72f0ce67f688813ee7264206e8c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727953"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="c7677-102">ICorDebugType::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="c7677-102">ICorDebugType::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="c7677-103"><xref:System.Type>このテキストの型によって参照されるクラスのパラメーターを格納している、テキスト型へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c7677-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7677-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7677-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7677-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7677-105">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="c7677-106">入出力 `ICorDebugTypeEnum` 型のパラメーターを格納しているのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c7677-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7677-107">注釈</span><span class="sxs-lookup"><span data-stu-id="c7677-107">Remarks</span></span>  

 <span data-ttu-id="c7677-108">を使用することができます、 `EnumerateTypeParameters` [corelementtype:: GetType](icordebugtype-gettype-method.md) によって返される corelementtype 値が ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR、または ELEMENT_TYPE_FNPTR です。</span><span class="sxs-lookup"><span data-stu-id="c7677-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="c7677-109">パラメーターの数と順序は、型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c7677-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="c7677-110">ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE: このメソッドが返すに格納されている型パラメーターの数 `ICorDebugTypeEnum` は、対応するクラスの仮引数の型パラメーターの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c7677-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="c7677-111">たとえば、型がの場合、 `class Dict<String,int32>` はを `EnumerateTypeParameters` `ICorDebugTypeEnum` 表し、シーケンス内でを表すオブジェクトを含むを返し `String` `int32` ます。</span><span class="sxs-lookup"><span data-stu-id="c7677-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="c7677-112">ELEMENT_TYPE_FNPTR: に格納されている型パラメーターの数 `ICorDebugTypeEnum` が、関数で許容される引数の数を超えています。</span><span class="sxs-lookup"><span data-stu-id="c7677-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="c7677-113">に格納されている最初の型パラメーターは、関数の戻り値の型であり、 `ICorDebugTypeEnum` 後続の型パラメーターは関数のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="c7677-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="c7677-114">ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR: 1 つの型パラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="c7677-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="c7677-115">たとえば、型がなどの配列型である場合、 `int32[]` `EnumerateTypeParameters` はを `ICorDebugTypeEnum` 表すオブジェクトを含むを返し `int32` ます。</span><span class="sxs-lookup"><span data-stu-id="c7677-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7677-116">要件</span><span class="sxs-lookup"><span data-stu-id="c7677-116">Requirements</span></span>  

 <span data-ttu-id="c7677-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7677-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7677-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7677-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7677-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7677-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7677-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7677-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
