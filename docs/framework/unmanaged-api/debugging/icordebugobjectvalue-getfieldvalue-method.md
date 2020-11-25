---
title: ICorDebugObjectValue::GetFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 745be25183f6b94e7a807c4230961d72e2836fe5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695336"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="c8327-102">ICorDebugObjectValue::GetFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c8327-102">ICorDebugObjectValue::GetFieldValue Method</span></span>

<span data-ttu-id="c8327-103">このオブジェクト値について、指定したクラスの指定したフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8327-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8327-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8327-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8327-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8327-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="c8327-106">からフィールド値を取得する対象のクラスを表す "表示クラス" オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8327-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="c8327-107">から `mdFieldDef` フィールドを記述するメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="c8327-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c8327-108">入出力指定したフィールドの値を表す "ICorDebugValue" オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8327-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8327-109">注釈</span><span class="sxs-lookup"><span data-stu-id="c8327-109">Remarks</span></span>  

 <span data-ttu-id="c8327-110">パラメーターで指定されたクラスは、 `pClass` オブジェクト値のクラスの階層内に存在する必要があり、フィールドはそのクラスのフィールドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8327-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="c8327-111">`GetFieldValue`ジェネリックオブジェクトとジェネリッククラスでは、メソッドは引き続き成功します。</span><span class="sxs-lookup"><span data-stu-id="c8327-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="c8327-112">たとえば、MyDictionary が \<V> ディクショナリから継承 \<string,V> し、オブジェクト値が mydictionary 型の場合、 \<int32> ディクショナリのオブジェクトを渡すと `ICorDebugClass` \<K,V> ディクショナリのフィールドが正常に取得され \<string,int32> ます。</span><span class="sxs-lookup"><span data-stu-id="c8327-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8327-113">要件</span><span class="sxs-lookup"><span data-stu-id="c8327-113">Requirements</span></span>  

 <span data-ttu-id="c8327-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8327-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8327-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8327-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8327-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8327-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8327-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8327-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8327-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8327-118">See also</span></span>
