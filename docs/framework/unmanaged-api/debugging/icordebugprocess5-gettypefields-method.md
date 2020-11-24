---
title: ICorDebugProcess5::GetTypeFields メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: e4eba37487ca2ee0a88caf5a59f86949a6521e40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670941"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="52c0d-102">ICorDebugProcess5::GetTypeFields メソッド</span><span class="sxs-lookup"><span data-stu-id="52c0d-102">ICorDebugProcess5::GetTypeFields Method</span></span>

<span data-ttu-id="52c0d-103">型に属しているフィールドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="52c0d-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c0d-104">構文</span><span class="sxs-lookup"><span data-stu-id="52c0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52c0d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52c0d-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="52c0d-106">からフィールド情報を取得する型の識別子。</span><span class="sxs-lookup"><span data-stu-id="52c0d-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="52c0d-107">からフィールド情報を取得する [COR_FIELD](cor-field-structure.md) オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="52c0d-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="52c0d-108">入出力型に属するフィールドに関する情報を提供する [COR_FIELD](cor-field-structure.md) オブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="52c0d-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="52c0d-109">入出力に含まれている [COR_FIELD](cor-field-structure.md) オブジェクトの数へのポインター `fields` 。</span><span class="sxs-lookup"><span data-stu-id="52c0d-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52c0d-110">注釈</span><span class="sxs-lookup"><span data-stu-id="52c0d-110">Remarks</span></span>  

 <span data-ttu-id="52c0d-111">パラメーターは、 `celt` メソッドがデータを設定するために使用するフィールドの数を指定し `fields` ます。フィールドの値に対応する必要があり `COR_TYPE_LAYOUT::numFields` ます。</span><span class="sxs-lookup"><span data-stu-id="52c0d-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c0d-112">要件</span><span class="sxs-lookup"><span data-stu-id="52c0d-112">Requirements</span></span>  

 <span data-ttu-id="52c0d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52c0d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c0d-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52c0d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52c0d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52c0d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52c0d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c0d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c0d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="52c0d-117">See also</span></span>

- [<span data-ttu-id="52c0d-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52c0d-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="52c0d-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="52c0d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
