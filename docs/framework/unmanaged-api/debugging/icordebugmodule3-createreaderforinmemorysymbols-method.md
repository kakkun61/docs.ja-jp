---
title: ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 44f4c59f95c28f9982d67875584e2f9803c0ed3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709571"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="e3a92-102">ICorDebugModule3::CreateReaderForInMemorySymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="e3a92-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>

<span data-ttu-id="e3a92-103">動的モジュールのデバッグシンボルリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e3a92-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a92-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3a92-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3a92-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3a92-105">Parameters</span></span>  

 <span data-ttu-id="e3a92-106">riid</span><span class="sxs-lookup"><span data-stu-id="e3a92-106">riid</span></span>  
 <span data-ttu-id="e3a92-107">から返す COM インターフェイスの IID。</span><span class="sxs-lookup"><span data-stu-id="e3a92-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="e3a92-108">通常、これは [ISymUnmanagedReader インターフェイス](../diagnostics/isymunmanagedreader-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3a92-108">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="e3a92-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="e3a92-109">ppObj</span></span>  
 <span data-ttu-id="e3a92-110">入出力返されたインターフェイスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e3a92-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3a92-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="e3a92-111">Return Value</span></span>  

 <span data-ttu-id="e3a92-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3a92-112">S_OK</span></span>  
 <span data-ttu-id="e3a92-113">リーダーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="e3a92-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="e3a92-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="e3a92-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="e3a92-115">モジュールがメモリ内または動的モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="e3a92-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="e3a92-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3a92-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="e3a92-117">シンボルは、アプリケーションによって提供されていないか、まだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="e3a92-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="e3a92-118">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="e3a92-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e3a92-119">リーダーを作成できません。</span><span class="sxs-lookup"><span data-stu-id="e3a92-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3a92-120">注釈</span><span class="sxs-lookup"><span data-stu-id="e3a92-120">Remarks</span></span>  

 <span data-ttu-id="e3a92-121">このメソッドを使用して、インメモリ (非動的) モジュール用のシンボルリーダーオブジェクトを作成することもできますが、最初にシンボルを使用できるようになった後 ( [UpdateModuleSymbols メソッド](icordebugmanagedcallback-updatemodulesymbols-method.md) コールバックによって示されます) にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3a92-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="e3a92-122">このメソッドは、呼び出されるたびに新しいリーダーインスタンスを返します ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)など)。</span><span class="sxs-lookup"><span data-stu-id="e3a92-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="e3a92-123">したがって、デバッガーは、基になるデータが変更されている (つまり、 [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md) のコールバックが受信された) 場合にのみ、結果をキャッシュし、新しいインスタンスを要求します。</span><span class="sxs-lookup"><span data-stu-id="e3a92-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="e3a92-124">動的モジュールでは、最初の型が読み込まれるまで ( [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md) コールバックによって示されるように) シンボルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e3a92-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a92-125">要件</span><span class="sxs-lookup"><span data-stu-id="e3a92-125">Requirements</span></span>  

 <span data-ttu-id="e3a92-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3a92-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a92-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3a92-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3a92-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3a92-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3a92-129">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e3a92-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a92-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3a92-130">See also</span></span>

- [<span data-ttu-id="e3a92-131">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3a92-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="e3a92-132">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3a92-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e3a92-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3a92-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
