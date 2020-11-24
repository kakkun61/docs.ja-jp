---
title: ICorDebugExceptionObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: 6a0c33799b2b2aaa48e3b18b7b4bb37643508bd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678884"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="00496-102">ICorDebugExceptionObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00496-102">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="00496-103">"は、マネージ例外オブジェクトからスタックトレース情報を提供するために、" は、"" のような "のインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="00496-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00496-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="00496-104">Methods</span></span>  
  
|<span data-ttu-id="00496-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="00496-105">Method</span></span>|<span data-ttu-id="00496-106">説明</span><span class="sxs-lookup"><span data-stu-id="00496-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00496-107">EnumerateExceptionCallStack メソッド</span><span class="sxs-lookup"><span data-stu-id="00496-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="00496-108">例外オブジェクトに埋め込まれている呼び出し履歴に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="00496-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00496-109">注釈</span><span class="sxs-lookup"><span data-stu-id="00496-109">Remarks</span></span>  

 <span data-ttu-id="00496-110">の呼び出しは、 `QueryInterface` から派生したマネージオブジェクトに対して成功し <xref:System.Exception?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="00496-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00496-111">要件</span><span class="sxs-lookup"><span data-stu-id="00496-111">Requirements</span></span>  

 <span data-ttu-id="00496-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00496-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00496-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00496-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00496-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00496-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00496-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00496-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00496-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="00496-116">See also</span></span>

- [<span data-ttu-id="00496-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="00496-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00496-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="00496-118">Debugging</span></span>](index.md)
