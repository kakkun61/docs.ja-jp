---
title: ICorDebugGenericValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: cfa0950ca2ef4e969258c147b762fa95e52a82e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705818"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="16d61-102">ICorDebugGenericValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16d61-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="16d61-103">すべての値に適用される "ICorDebugValue" のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="16d61-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="16d61-104">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="16d61-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16d61-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="16d61-105">Methods</span></span>  
  
|<span data-ttu-id="16d61-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="16d61-106">Method</span></span>|<span data-ttu-id="16d61-107">説明</span><span class="sxs-lookup"><span data-stu-id="16d61-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16d61-108">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="16d61-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="16d61-109">指定したバッファーに値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="16d61-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="16d61-110">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="16d61-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="16d61-111">指定したバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="16d61-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16d61-112">注釈</span><span class="sxs-lookup"><span data-stu-id="16d61-112">Remarks</span></span>  

 <span data-ttu-id="16d61-113">`ICorDebugGenericValue` は、リモート処理が不可能なため、サブインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="16d61-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="16d61-114">参照型の場合、値は参照の内容ではなく参照です。</span><span class="sxs-lookup"><span data-stu-id="16d61-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="16d61-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="16d61-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16d61-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="16d61-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d61-117">要件</span><span class="sxs-lookup"><span data-stu-id="16d61-117">Requirements</span></span>  

 <span data-ttu-id="16d61-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16d61-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d61-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16d61-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16d61-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16d61-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d61-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d61-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d61-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="16d61-122">See also</span></span>

- [<span data-ttu-id="16d61-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="16d61-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
