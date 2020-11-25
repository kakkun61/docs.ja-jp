---
title: ICorDebugProcess5::GetTypeID メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 3a9ef06f312126319875544caf272903b9f7c716
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701030"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="36122-102">ICorDebugProcess5::GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="36122-102">ICorDebugProcess5::GetTypeID Method</span></span>

<span data-ttu-id="36122-103">オブジェクトのアドレスを [COR_TYPEID](cor-typeid-structure.md) 識別子に変換します。</span><span class="sxs-lookup"><span data-stu-id="36122-103">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36122-104">構文</span><span class="sxs-lookup"><span data-stu-id="36122-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36122-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36122-105">Parameters</span></span>  

 `obj`  
 <span data-ttu-id="36122-106">からオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="36122-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="36122-107">オブジェクトを識別する [COR_TYPEID](cor-typeid-structure.md) 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="36122-107">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36122-108">解説</span><span class="sxs-lookup"><span data-stu-id="36122-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36122-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="36122-109">Requirements</span></span>  

 <span data-ttu-id="36122-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36122-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36122-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36122-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36122-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36122-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36122-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36122-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36122-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="36122-114">See also</span></span>

- [<span data-ttu-id="36122-115">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36122-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="36122-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="36122-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
