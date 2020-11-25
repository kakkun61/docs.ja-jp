---
title: ICorDebugMDA インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: c4ff28ff1019b5314902a4e71f6d02b5a2fd8d70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710845"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="a3f24-102">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3f24-102">ICorDebugMDA Interface</span></span>

<span data-ttu-id="a3f24-103">マネージド デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3f24-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-104">Methods</span></span>  
  
|<span data-ttu-id="a3f24-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-105">Method</span></span>|<span data-ttu-id="a3f24-106">説明</span><span class="sxs-lookup"><span data-stu-id="a3f24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3f24-107">GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="a3f24-108">この MDA の説明を格納している文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="a3f24-109">GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="a3f24-110">この MDA に関連付けられているフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="a3f24-111">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="a3f24-112">この MDA の名前を格納している文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="a3f24-113">GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="a3f24-114">この MDA が実行されているオペレーティングシステムのスレッド id を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="a3f24-115">GetXML メソッド</span><span class="sxs-lookup"><span data-stu-id="a3f24-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="a3f24-116">この MDA に関連付けられている XML の完全ストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="a3f24-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3f24-117">注釈</span><span class="sxs-lookup"><span data-stu-id="a3f24-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3f24-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a3f24-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f24-119">要件</span><span class="sxs-lookup"><span data-stu-id="a3f24-119">Requirements</span></span>  

 <span data-ttu-id="a3f24-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3f24-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f24-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3f24-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3f24-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3f24-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3f24-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3f24-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f24-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3f24-124">See also</span></span>

- [<span data-ttu-id="a3f24-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3f24-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a3f24-126">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a3f24-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
