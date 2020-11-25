---
title: ICorDebugStringValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: cd6c5726b9a938d04cf4eb018ec9851c81d9c745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697052"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="c705f-102">ICorDebugStringValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c705f-102">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="c705f-103">文字列値に適用される、値のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="c705f-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c705f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c705f-104">Methods</span></span>  
  
|<span data-ttu-id="c705f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c705f-105">Method</span></span>|<span data-ttu-id="c705f-106">説明</span><span class="sxs-lookup"><span data-stu-id="c705f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c705f-107">GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="c705f-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="c705f-108">このによって参照される文字列の文字数を取得し `ICorDebugStringValue` ます。</span><span class="sxs-lookup"><span data-stu-id="c705f-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="c705f-109">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="c705f-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="c705f-110">このによって参照される文字列を取得し `ICorDebugStringValue` ます。</span><span class="sxs-lookup"><span data-stu-id="c705f-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c705f-111">注釈</span><span class="sxs-lookup"><span data-stu-id="c705f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c705f-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c705f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c705f-113">要件</span><span class="sxs-lookup"><span data-stu-id="c705f-113">Requirements</span></span>  

 <span data-ttu-id="c705f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c705f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c705f-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c705f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c705f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c705f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c705f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c705f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c705f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c705f-118">See also</span></span>

- [<span data-ttu-id="c705f-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c705f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
