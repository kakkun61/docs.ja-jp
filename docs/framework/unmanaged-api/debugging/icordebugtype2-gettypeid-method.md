---
title: 'ICorDebugType2:: GetTypeID メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 2a4a0bfae6f9a1970f0d4aca8b37f8fc68194462
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725691"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="1a81b-102">ICorDebugType2:: GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="1a81b-102">ICorDebugType2::GetTypeID Method</span></span>

<span data-ttu-id="1a81b-103">この型の [COR_TYPEID](cor-typeid-structure.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a81b-103">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a81b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1a81b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a81b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a81b-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="1a81b-106">入出力このテキスト型の [COR_TYPEID](cor-typeid-structure.md) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1a81b-106">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a81b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1a81b-107">Return Value</span></span>  

 <span data-ttu-id="1a81b-108">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="1a81b-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="1a81b-109">コードには `HRESULT` 次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1a81b-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="1a81b-110">リターン コード</span><span class="sxs-lookup"><span data-stu-id="1a81b-110">Return code</span></span>|<span data-ttu-id="1a81b-111">説明</span><span class="sxs-lookup"><span data-stu-id="1a81b-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="1a81b-112">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="1a81b-112">Method succeeded.</span></span> <span data-ttu-id="1a81b-113">メソッドが有効な [COR_TYPEID](cor-typeid-structure.md)を取得しました。</span><span class="sxs-lookup"><span data-stu-id="1a81b-113">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="1a81b-114">型が読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="1a81b-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="1a81b-115">この型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1a81b-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a81b-116">注釈</span><span class="sxs-lookup"><span data-stu-id="1a81b-116">Remarks</span></span>  

 <span data-ttu-id="1a81b-117">このメソッドは、ランタイムに読み込まれている可能性がある型を表す、または [COR_TYPEID](cor-typeid-structure.md)ランタイムに読み込まれていない可能性のある型を表す、、ランタイムに読み込まれた型を識別する不透明なハンドルとして機能する、の型からのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a81b-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="1a81b-118">によって表される型がまだ読み込まれていない場合、このメソッドはを返し `CORDBG_E_CLASS_NOT_LOADED` ます。</span><span class="sxs-lookup"><span data-stu-id="1a81b-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="1a81b-119">型がサポートされていない場合は、を返し `CORDBG_E_UNSUPPORTED` ます。</span><span class="sxs-lookup"><span data-stu-id="1a81b-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a81b-120">要件</span><span class="sxs-lookup"><span data-stu-id="1a81b-120">Requirements</span></span>  

 <span data-ttu-id="1a81b-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a81b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a81b-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a81b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a81b-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a81b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a81b-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a81b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a81b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a81b-125">See also</span></span>

- [<span data-ttu-id="1a81b-126">ICorDebugType2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a81b-126">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)
