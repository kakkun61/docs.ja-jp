---
title: ICorDebugTypeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum
helpviewer_keywords:
- ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: 159ccfcf-b37c-4ad9-8e0d-a9a443262472
topic_type:
- apiref
ms.openlocfilehash: 620dbace00afe004454457b2d502461b80359add
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725678"
---
# <a name="icordebugtypeenum-interface"></a><span data-ttu-id="b38d1-102">ICorDebugTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b38d1-102">ICorDebugTypeEnum Interface</span></span>

<span data-ttu-id="b38d1-103">"ICorDebugEnum" メソッドを実装し、"" 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="b38d1-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugType" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b38d1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b38d1-104">Methods</span></span>  
  
|<span data-ttu-id="b38d1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b38d1-105">Method</span></span>|<span data-ttu-id="b38d1-106">説明</span><span class="sxs-lookup"><span data-stu-id="b38d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b38d1-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="b38d1-107">Next Method</span></span>](icordebugtypeenum-next-method.md)|<span data-ttu-id="b38d1-108">現在の位置から開始して、指定した数の `ICorDebugType` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="b38d1-108">Gets the specified number of `ICorDebugType` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b38d1-109">注釈</span><span class="sxs-lookup"><span data-stu-id="b38d1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b38d1-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b38d1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38d1-111">要件</span><span class="sxs-lookup"><span data-stu-id="b38d1-111">Requirements</span></span>  

 <span data-ttu-id="b38d1-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b38d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38d1-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b38d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b38d1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b38d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b38d1-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b38d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b38d1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b38d1-116">See also</span></span>

- [<span data-ttu-id="b38d1-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b38d1-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
