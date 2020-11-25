---
title: ICorDebugProcess5::GetTypeLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 32277e8adcd4bb08c8d0480eb3b4e7e4b5949479
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723130"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="370df-102">ICorDebugProcess5::GetTypeLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="370df-102">ICorDebugProcess5::GetTypeLayout Method</span></span>

<span data-ttu-id="370df-103">型識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="370df-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370df-104">構文</span><span class="sxs-lookup"><span data-stu-id="370df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="370df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="370df-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="370df-106">からレイアウトが必要な型を指定する [COR_TYPEID](cor-typeid-structure.md) トークン。</span><span class="sxs-lookup"><span data-stu-id="370df-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="370df-107">入出力メモリ内のオブジェクトのレイアウトに関する情報を格納している [COR_TYPE_LAYOUT](cor-type-layout-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="370df-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="370df-108">注釈</span><span class="sxs-lookup"><span data-stu-id="370df-108">Remarks</span></span>  

 <span data-ttu-id="370df-109">メソッドは、その `ICorDebugProcess5::GetTypeLayout` [COR_TYPEID](cor-typeid-structure.md)に基づいてオブジェクトに関する情報を提供します。これは、他の多くの [ICorDebugProcess5](icordebugprocess5-interface.md) メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="370df-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="370df-110">この情報は、メソッドによって設定される [COR_TYPE_LAYOUT](cor-type-layout-structure.md) 構造体によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="370df-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="370df-111">要件</span><span class="sxs-lookup"><span data-stu-id="370df-111">Requirements</span></span>  

 <span data-ttu-id="370df-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="370df-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="370df-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="370df-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="370df-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="370df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="370df-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="370df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370df-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="370df-116">See also</span></span>

- [<span data-ttu-id="370df-117">COR_TYPE_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="370df-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="370df-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="370df-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="370df-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="370df-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
