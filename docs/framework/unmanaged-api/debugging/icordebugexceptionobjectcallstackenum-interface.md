---
title: ICorDebugExceptionObjectCallStackEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: 1c45faecdb8b95af8d9e981962151c2c5d071a4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731892"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="056a2-102">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="056a2-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>

<span data-ttu-id="056a2-103">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="056a2-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="056a2-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="056a2-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="056a2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="056a2-105">Methods</span></span>  
  
|<span data-ttu-id="056a2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="056a2-106">Method</span></span>|<span data-ttu-id="056a2-107">説明</span><span class="sxs-lookup"><span data-stu-id="056a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="056a2-108">いい Exceptionobjectcallstackenum:: Next</span><span class="sxs-lookup"><span data-stu-id="056a2-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="056a2-109">例外オブジェクトの呼び出し履歴に関する情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="056a2-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="056a2-110">注釈</span><span class="sxs-lookup"><span data-stu-id="056a2-110">Remarks</span></span>  

 <span data-ttu-id="056a2-111">`ICorDebugExceptionObjectCallStackEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="056a2-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="056a2-112">`ICorDebugExceptionObjectCallStackEnum` [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)オブジェクトを使用してインスタンスに値を設定するには、 [EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="056a2-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="056a2-113">コレクション内のコールスタック項目を列挙するには、 [次](icordebugexceptionobjectcallstackenum-next-method.md) のように指定します。</span><span class="sxs-lookup"><span data-stu-id="056a2-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="056a2-114">要件</span><span class="sxs-lookup"><span data-stu-id="056a2-114">Requirements</span></span>  

 <span data-ttu-id="056a2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="056a2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="056a2-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="056a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="056a2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="056a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="056a2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="056a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056a2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="056a2-119">See also</span></span>

- [<span data-ttu-id="056a2-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="056a2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="056a2-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="056a2-121">Debugging</span></span>](index.md)
