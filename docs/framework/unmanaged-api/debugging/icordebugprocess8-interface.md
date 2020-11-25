---
title: ICorDebugProcess8 インターフェイス
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 00c432374eeb82692492b8e6b10472f13bc44d6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732516"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="5f56f-102">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f56f-102">ICorDebugProcess8 Interface</span></span>

<span data-ttu-id="5f56f-103">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="5f56f-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="5f56f-104">ICorDebugManagedCallback2 Process インターフェイスを論理的に拡張して、特定の種類の[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f56f-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f56f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f56f-105">Methods</span></span>  
  
|<span data-ttu-id="5f56f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f56f-106">Method</span></span>|<span data-ttu-id="5f56f-107">説明</span><span class="sxs-lookup"><span data-stu-id="5f56f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f56f-108">EnableExceptionCallbacksOutsideOfMyCode メソッド</span><span class="sxs-lookup"><span data-stu-id="5f56f-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="5f56f-109">特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f56f-109">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f56f-110">解説</span><span class="sxs-lookup"><span data-stu-id="5f56f-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f56f-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="5f56f-111">Requirements</span></span>  

 <span data-ttu-id="5f56f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f56f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f56f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f56f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f56f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f56f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f56f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f56f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f56f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f56f-116">See also</span></span>

- [<span data-ttu-id="5f56f-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f56f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5f56f-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5f56f-118">Debugging</span></span>](index.md)
