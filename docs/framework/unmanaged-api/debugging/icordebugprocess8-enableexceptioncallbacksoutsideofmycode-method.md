---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 750d2a2d69c74e147c34c9c496079ee48ac04b42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732542"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="37c4a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド</span><span class="sxs-lookup"><span data-stu-id="37c4a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="37c4a-103">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="37c4a-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="37c4a-104">特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="37c4a-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="37c4a-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37c4a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37c4a-106">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="37c4a-107">[入力]</span><span class="sxs-lookup"><span data-stu-id="37c4a-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37c4a-108">注釈</span><span class="sxs-lookup"><span data-stu-id="37c4a-108">Remarks</span></span>  

 <span data-ttu-id="37c4a-109">`enableExceptionsOutsideOfJMC` の値が `false` の場合:</span><span class="sxs-lookup"><span data-stu-id="37c4a-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="37c4a-110">デバッガーへのコールバックでは DEBUG_EXCEPTION_FIRST_CHANCE 例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="37c4a-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="37c4a-111">例外がユーザー コードにエスケープされることがない場合 (つまり、例外の発生から例外ハンドラーへのパスで、JustMyCode または JMC とマークされているメソッドがない場合)、DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="37c4a-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="37c4a-112">`enableExceptionsOutsideOfJMC` の既定値は `true`です。</span><span class="sxs-lookup"><span data-stu-id="37c4a-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c4a-113">要件</span><span class="sxs-lookup"><span data-stu-id="37c4a-113">Requirements</span></span>  

 <span data-ttu-id="37c4a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37c4a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c4a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37c4a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37c4a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37c4a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37c4a-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c4a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c4a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="37c4a-118">See also</span></span>

- [<span data-ttu-id="37c4a-119">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c4a-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="37c4a-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c4a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
